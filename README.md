# Blood Cell Detection using YOLO26

A deep learning project for automated blood cell detection and classification using YOLO26s object detection model. This project leverages state-of-the-art computer vision techniques to identify and localize blood cells in medical images with high accuracy.

## 🎯 Project Overview

This project implements a blood cell detection system using YOLO26s, a cutting-edge real-time object detection framework. The model can detect and classify blood cells in microscopy images, making it useful for medical diagnostics, research, and automated analysis.

**Key Features:**
- Real-time blood cell detection in images and videos
- Support for multiple input sources (images, image folders, videos, webcam)
- Configurable confidence thresholds for flexible detection sensitivity
- GPU acceleration support (CUDA)
- Video recording capability for detection results
- Multiple model variants for different accuracy/speed tradeoffs

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- CUDA 11.0+ (for GPU acceleration, optional)
- pip or conda package manager

### Installation

1. **Clone or navigate to the project directory:**
   ```bash
   cd yolo
   ```

2. **Create a virtual environment (recommended):**
   ```bash
   python -m venv venv
   ```

3. **Activate the virtual environment:**
   - **Windows:**
     ```bash
     .\venv\Scripts\activate
     ```
   - **Linux/Mac:**
     ```bash
     source venv/bin/activate
     ```

4. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

   **Or manually install required packages:**
   ```bash
   pip install ultralytics opencv-python numpy torch torchvision
   ```

## 💻 Usage

### 1. Basic Blood Cell Detection on Images

Detect blood cells in a single image:

```bash
python yolo_detect.py --model blood_model.pt --source test_image.jpg
```

**Parameters:**
- `--model`: Path to the trained model file (required)
- `--source`: Input image file path (required)
- `--thresh`: Confidence threshold (default: 0.5, range: 0-1)
- `--resolution`: Display resolution in WxH format (e.g., "640x480")
- `--record`: Record video output as "demo1.avi"

### 2. Batch Detection on Image Folder

Process multiple images at once:

```bash
python yolo_detect.py --model blood_model.pt --source ./test_images/
```

### 3. Video Detection

Detect blood cells in a video file:

```bash
python yolo_detect.py --model blood_model.pt --source test.mp4 --record --resolution 640x480
```

### 4. Real-time Webcam Detection

Run detection on webcam stream:

```bash
python yolo_detect.py --model blood_model.pt --source usb0
```

### 5. Adjusting Confidence Threshold

Use a different confidence threshold (lower = more detections, higher = fewer but more confident):

```bash
python yolo_detect.py --model blood_model.pt --source t1.jpg --thresh 0.6
```

## 🔍 Model Information

### Blood Cell Detection Model

- **Architecture:** YOLO26 (Small variant - yolo26s)
- **Input Size:** 640x640 pixels
- **Framework:** PyTorch via Ultralytics
- **Model File:** `blood_model.pt`

### Training Configuration

- **Epochs:** 60
- **Batch Size:** 16
- **Optimizer:** SGD with momentum
- **Image Size:** 640x640
- **Device:** CUDA GPU (if available)

**Training Arguments:** See `train/args.yaml`

### Performance Metrics

Training results and metrics are logged in `train/results.csv`. Key metrics include:
- Precision
- Recall
- mAP@50
- mAP@50-95
- Training/Validation loss

## 🖥️ GPU Support

The project automatically detects and uses CUDA GPU if available.

## 📊 Input Sources Supported

The detection script supports multiple input types:

| Source Type | Example | Notes |
|-------------|---------|-------|
| Single Image | `test.jpg` or `./images/cell.png` | JPG, JPEG, PNG, BMP formats supported |
| Image Folder | `./test_images/` | Processes all images in directory |
| Video File | `test.mp4` | MP4, AVI, MOV, MKV, WMV formats |
| USB Webcam | `usb0` | Use index starting from 0 |
| Raspberry Pi Camera | `picamera0` | For RPI deployments |

## 🎓 Jupyter Notebook

For interactive exploration and experimentation:

```bash
jupyter notebook yolo.ipynb
```

## 🔧 Advanced Options

### Custom Resolution Output

Display results at a specific resolution:

```bash
python yolo_detect.py --model blood_model.pt --source test.mp4 --resolution 1280x720
```

### Confidence Threshold Tuning

- **High threshold (0.8-0.95):** More conservative, only high-confidence detections
- **Medium threshold (0.5-0.7):** Balanced detection rate
- **Low threshold (0.2-0.4):** Detects more cells, may include false positives

## 📦 Requirements

```
ultralytics>=8.0.0
opencv-python>=4.6.0
numpy>=1.21.0
torch>=1.9.0
torchvision>=0.10.0
```

Install all requirements:
```bash
pip install -r requirements.txt
```

## 🎯 Use Cases

- **Medical Diagnosis:** Automated blood cell analysis for disease detection
- **Research:** Quantitative analysis of blood cell morphology
- **Quality Control:** Batch processing of medical samples
- **Education:** Teaching computer vision and object detection concepts

## 📝 Output

The detection system produces:

1. **Visual Output:** Bounding boxes around detected blood cells with confidence scores
2. **Console Logs:** Detection statistics and processing time
3. **Video Output (optional):** Recorded detection results saved as `.avi` file

## 🐛 Troubleshooting

### Model Not Found Error
```
ERROR: Model path is invalid or model was not found.
```
**Solution:** Verify the model file path and ensure `blood_model.pt` exists in the directory.

### CUDA/GPU Issues
If you encounter GPU-related errors, the script will automatically fall back to CPU processing.

### No Detections Found
- Try lowering the `--thresh` parameter (e.g., 0.3 instead of 0.5)
- Ensure image quality is sufficient for detection
- Verify the model is trained on similar data

## 📄 License

This project is open source and available under appropriate licensing terms.

## 🤝 Contributing

Contributions, improvements, and suggestions are welcome! Please feel free to:
- Report bugs and issues
- Suggest improvements
- Submit pull requests

**Last Updated:** May 2026  
**Status:** ✅ Production Ready
