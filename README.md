# Campus Energy Oracle Model + UI

**Intelligent Classroom Occupancy Detection & Energy Management System**

A comprehensive Flask-based web application that uses advanced YOLO object detection to monitor classroom occupancy in real-time. This system enables smart campus energy management by providing accurate occupancy data for automated HVAC, lighting, and energy distribution.

![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Flask](https://img.shields.io/badge/Flask-3.0.0-green)
![License](https://img.shields.io/badge/License-MIT-blue)

---

## 🎯 Project Overview

Campus Energy Oracle is an intelligent occupancy detection system designed to optimize energy consumption in educational institutions. By accurately detecting the number of people in classrooms using AI-powered computer vision, the system enables:

- **Real-time occupancy monitoring** across multiple classrooms
- **Smart energy management** with automated HVAC and lighting control
- **Historical analytics** for occupancy patterns and energy optimization
- **Web-based dashboard** for intuitive monitoring and configuration

### Key Statistics
- **Detection Accuracy**: High precision with YOLO-based detection
- **Processing Speed**: Real-time frame analysis with GPU acceleration
- **Support**: Image, Video, and Live Webcam streams
- **Scalability**: Designed for multi-room campus deployment

---

## ✨ Features

### Core Detection Capabilities
- ✅ **Image-based Detection**: Analyze single images for classroom occupancy
- ✅ **Video Analysis**: Process video files with frame-by-frame detection and statistics
- ✅ **Live Webcam**: Real-time monitoring with streaming capability
- ✅ **Confidence Threshold**: Adjustable detection confidence (10% - 100%)
- ✅ **Batch Processing**: Efficient handling of multiple files

### Intelligence Features
- 📊 **Occupancy Analytics**: Track occupancy patterns over time
- 📈 **Statistical Reports**: Min, max, and average occupancy metrics
- 🎨 **Visual Annotations**: Bounding boxes and confidence labels on output
- ⚡ **GPU Acceleration**: CUDA support for faster processing
- 🔍 **Debug Information**: Detailed logging for troubleshooting

### User Interface
- 🎨 **Modern Dashboard**: Clean, responsive web interface
- 📱 **Mobile Responsive**: Works on desktop, tablet, and mobile devices
- ⌨️ **Intuitive Controls**: Easy-to-use buttons for all operations
- 📋 **Real-time Status**: Model status, device information, and processing metrics
- 🎨 **Dark Theme**: Eye-friendly modern design with animations

### API Features
- 🔌 **RESTful API**: Standard HTTP endpoints for all operations
- 📡 **CORS Enabled**: Support for cross-origin requests
- 🛡️ **Error Handling**: Comprehensive error messages and validation
- 📝 **Health Check**: Endpoint to verify system status

---

## 📋 Prerequisites

### System Requirements
- **Python**: 3.10 or higher
- **GPU**: NVIDIA GPU with CUDA support (optional, but recommended)
  - CUDA Toolkit 12.4
  - cuDNN compatible with PyTorch 2.4.1
- **CPU**: If GPU unavailable, CPU processing is supported (slower)
- **Storage**: Minimum 2GB free space (model + dependencies)
- **RAM**: 8GB+ recommended (16GB+ for video processing)

### Supported Operating Systems
- Windows 10/11
- Ubuntu 20.04+ / Debian
- macOS (Intel/Apple Silicon)

---

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/campus-energy-oracle.git
cd campus-energy-oracle
```

### 2. Create Virtual Environment
```bash
# Windows
python -m venv env
env\Scripts\activate

# Linux/macOS
python3 -m venv env
source env/bin/activate
```

### 3. Install Dependencies
```bash
# Upgrade pip
pip install --upgrade pip

# Install all dependencies
pip install -r requirements.txt

# For NVIDIA GPU support (CUDA 12.4)
pip install torch==2.4.1 torchvision==0.19.1 torchaudio==2.4.1 --index-url https://download.pytorch.org/whl/cu124
```

### 4. Download Pre-trained Model
The YOLO model file `SMFA_Yolo26x.pt` should be placed in the `Models/` directory:
```
Campus Energy Oracle/
├── Models/
│   └── SMFA_Yolo26x.pt  (Download and place here)
├── app.py
├── requirements.txt
└── ...
```

### 5. Verify Installation
```bash
# Run the test endpoint
python app.py

# In another terminal, test the API
curl http://localhost:5000/debug/test
```

---

## 📁 Project Structure

```
Campus Energy Oracle/
│
├── app.py                          # Main Flask application
├── requirements.txt                # Python dependencies
├── README.md                       # This file
│
├── Models/                         # Machine Learning Models
│   └── SMFA_Yolo26x.pt            # YOLO11x detection model
│
├── templates/                      # HTML Templates
│   └── index.html                 # Main dashboard interface
│
├── static/                        # Static Assets
│   ├── css/
│   │   ├── styles.css            # Main stylesheet
│   │   ├── components.css        # Component-specific styles
│   │   └── animations.css        # UI animations
│   └── js/
│       ├── app.js                # Main application logic
│       ├── api.js                # API communication
│       ├── charts.js             # Chart/graph utilities
│       ├── config.js             # Configuration
│       └── ui.js                 # UI interaction handlers
│
├── uploads/                       # Temporary file storage
│   ├── input_*                   # Uploaded input files
│   └── output_*                  # Processed output files
│
└── env/                          # Virtual environment (created after setup)
```

---

## 🎮 Quick Start

### 1. Start the Application
```bash
# Activate virtual environment (if not already activated)
# Windows: env\Scripts\activate
# Linux/macOS: source env/bin/activate

# Run the Flask app
python app.py
```

Expected output:
```
INFO:__main__:Device selected: cuda
INFO:__main__:Loading YOLO model from: .../Models/SMFA_Yolo26x.pt
INFO:__main__:✓ Model loaded successfully on cuda
WARNING in flask.app: This is a development server...
Running on http://127.0.0.1:5000
```

### 2. Open Web Dashboard
Navigate to: **http://localhost:5000**

### 3. Use Detection Features
- **Upload Image**: Click "Upload Image" → Select JPG/PNG → View results with bounding boxes
- **Upload Video**: Click "Upload Video" → Select MP4/AVI → Download annotated video
- **Live Webcam**: Click "Start Webcam" → Allow camera access → Real-time detection
- **Adjust Threshold**: Use confidence slider in settings (10%-100%)

---

## 📡 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Endpoints

#### 1. Health Check
```http
GET /api/health
```

**Response:**
```json
{
  "status": "healthy",
  "model_loaded": true,
  "device": "cuda",
  "timestamp": "2024-04-29T10:30:45.123456"
}
```

#### 2. Model Information
```http
GET /api/model/info
```

**Response:**
```json
{
  "model_path": ".../Models/SMFA_Yolo26x.pt",
  "device": "cuda",
  "framework": "PyTorch + YOLOv11",
  "task": "Object Detection (Person)",
  "input_size": "640x640",
  "confidence_threshold": 0.5,
  "timestamp": "2024-04-29T10:30:45.123456"
}
```

#### 3. Image Detection
```http
POST /api/detect/image
Content-Type: multipart/form-data

Parameters:
  - file (required): Image file (PNG, JPG, JPEG, GIF, BMP)
  - confidence (optional): Detection threshold (0.1-1.0, default: 0.5)
```

**Response:**
```json
{
  "success": true,
  "occupancy_count": 12,
  "confidence_threshold": 0.5,
  "detections": [
    {
      "x1": 150.5,
      "y1": 200.3,
      "x2": 350.2,
      "y2": 400.8,
      "width": 199.7,
      "height": 200.5,
      "confidence": 0.98,
      "person_id": 0
    }
  ],
  "annotated_image": "data:image/jpeg;base64,/9j/4AAQSkZJRg...",
  "timestamp": "2024-04-29T10:30:45.123456"
}
```

#### 4. Video Detection
```http
POST /api/detect/video
Content-Type: multipart/form-data

Parameters:
  - file (required): Video file (MP4, AVI, MOV, MKV)
  - confidence (optional): Detection threshold (0.1-1.0, default: 0.5)
```

**Response:**
```json
{
  "success": true,
  "frames_processed": 300,
  "avg_occupancy": 8.5,
  "max_occupancy": 15,
  "min_occupancy": 2,
  "output_video": "/api/download/video/output_20240429_103045_video.mp4",
  "occupancy_data": [5, 6, 8, 12, 15, 14, ...],
  "timestamp": "2024-04-29T10:30:45.123456"
}
```

#### 5. Webcam/Real-time Detection
```http
POST /api/detect/webcam
Content-Type: application/json

Body:
{
  "image": "data:image/jpeg;base64,...",
  "confidence": 0.5
}
```

**Response:**
```json
{
  "success": true,
  "occupancy_count": 10,
  "detections": [...],
  "frame": "data:image/jpeg;base64,...",
  "timestamp": "2024-04-29T10:30:45.123456"
}
```

#### 6. Download Processed Video
```http
GET /api/download/video/{filename}
```

---

## ⚙️ Configuration

### Model Configuration
Edit the following variables in `app.py`:

```python
# Detection Confidence Threshold (0.0 - 1.0)
CONFIDENCE_THRESHOLD = 0.5

# Maximum file size for uploads (bytes)
MAX_FILE_SIZE = 100 * 1024 * 1024  # 100MB

# Allowed file extensions
ALLOWED_IMAGE_EXTENSIONS = {'png', 'jpg', 'jpeg', 'gif', 'bmp'}
ALLOWED_VIDEO_EXTENSIONS = {'mp4', 'avi', 'mov', 'mkv'}

# Model path (ensure model file exists)
MODEL_PATH = os.path.join(BASE_DIR, 'models', 'SMFA_Yolo26x.pt')
```

### Flask Configuration
```python
# Auto-reload templates during development
app.jinja_env.auto_reload = True
app.config['TEMPLATES_AUTO_RELOAD'] = True

# CORS settings for cross-origin requests
CORS(app, resources={
    r"/api/*": {
        "origins": "*",
        "methods": ["GET", "POST", "OPTIONS"],
        "allow_headers": ["Content-Type"]
    }
})
```

### GPU/Device Configuration
The application automatically selects the best available device:
- **CUDA GPU** (if NVIDIA GPU with CUDA support is available)
- **CPU** (fallback for systems without GPU)

To force CPU mode:
```python
device = 'cpu'  # In app.py, line ~86
```

---

## 🤖 Model Information

### YOLO Detection Model
- **Model Name**: SMFA_Yolo26x
- **Framework**: PyTorch + YOLOv11
- **Task**: Object Detection (Person Detection)
- **Input Size**: 640×640 pixels
- **Output**: Bounding boxes with confidence scores
- **Classes**: Person (single class detection)

### Model Performance
- **Inference Speed**: ~10-30ms per frame (GPU)
- **Detection Classes**: Person
- **Confidence Range**: 0.0 - 1.0 (recommended: 0.5+)
- **Supported Devices**: CUDA GPU, CPU

### Loading Model
The model is automatically loaded when the Flask app starts:
```
Device selected: cuda
Loading YOLO model from: .../Models/SMFA_Yolo26x.pt
✓ Model loaded successfully on cuda
```

---

## 📊 Usage Examples

### Using cURL
```bash
# Health check
curl http://localhost:5000/api/health

# Detect people in image
curl -X POST -F "file=@classroom.jpg" \
  http://localhost:5000/api/detect/image

# Detect with custom confidence
curl -X POST -F "file=@classroom.jpg" \
  -F "confidence=0.7" \
  http://localhost:5000/api/detect/image
```

### Using Python
```python
import requests
import json

# Image detection
url = 'http://localhost:5000/api/detect/image'
files = {'file': open('classroom.jpg', 'rb')}
data = {'confidence': 0.5}

response = requests.post(url, files=files, data=data)
result = response.json()

print(f"People detected: {result['occupancy_count']}")
print(f"Detections: {result['detections']}")
```

### Using JavaScript (Fetch API)
```javascript
// Image detection
const formData = new FormData();
formData.append('file', imageFile);
formData.append('confidence', 0.5);

fetch('/api/detect/image', {
  method: 'POST',
  body: formData
})
.then(response => response.json())
.then(data => {
  console.log(`Occupancy: ${data.occupancy_count}`);
  console.log(`Detections: ${data.detections.length}`);
})
.catch(error => console.error('Error:', error));
```

---

## 🔧 Troubleshooting

### Common Issues

#### 1. Model Not Loading
**Error**: `Model file not found at: .../Models/SMFA_Yolo26x.pt`

**Solution**:
- Verify the model file exists in `Models/` directory
- Check file permissions
- Ensure correct file name (case-sensitive on Linux/macOS)

#### 2. CUDA Not Available
**Error**: `No CUDA GPUs detected, using CPU`

**Solution**:
- Install NVIDIA GPU drivers: https://www.nvidia.com/Download/driverDetails.aspx
- Install CUDA Toolkit 12.4: https://developer.nvidia.com/cuda-12-4-0-download-archive
- Verify installation: `nvidia-smi`

#### 3. Port Already in Use
**Error**: `Address already in use`

**Solution**:
```bash
# Kill process using port 5000
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Linux/macOS
lsof -ti:5000 | xargs kill -9
```

#### 4. Out of Memory
**Error**: `CUDA out of memory`

**Solution**:
- Reduce input image size
- Process smaller video chunks
- Enable CPU fallback:
  ```python
  device = 'cpu'
  ```

#### 5. File Upload Issues
**Error**: `File too large` or `Invalid file type`

**Solution**:
- Check `MAX_FILE_SIZE` configuration (default: 100MB)
- Verify file format is supported (JPG, PNG for images; MP4, AVI for videos)
- Ensure file extension is correct

### Debug Mode
Enable detailed logging:
```python
# In app.py
logging.basicConfig(level=logging.DEBUG)
```

Access debug endpoints:
```bash
# System information
curl http://localhost:5000/debug/info

# API test
curl http://localhost:5000/debug/test
```

---

## 📈 Performance Tips

### Optimization Strategies
1. **GPU Acceleration**: Ensure CUDA is properly installed for 5-10x faster processing
2. **Batch Processing**: Process multiple files without restarting the server
3. **Confidence Threshold**: Increase threshold to reduce false positives and speed up processing
4. **Input Size**: Resize large images to 640×640 for optimal performance
5. **Memory Management**: Clear old upload files regularly

### Monitoring
```bash
# Monitor system resources during processing
# Windows
tasklist /FI "IMAGENAME eq python.exe"

# Linux
top -p $(pgrep -f app.py)
```

---

## 🤝 Contributing

Contributions are welcome! To contribute:

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/your-feature`
3. **Commit** your changes: `git commit -m 'Add your feature'`
4. **Push** to the branch: `git push origin feature/your-feature`
5. **Submit** a Pull Request

### Development Setup
```bash
# Install development dependencies
pip install -r requirements.txt

# Run tests
pytest tests/

# Code style (optional)
black app.py
flake8 app.py
```

---

## 📝 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Author & Contact

**Campus Energy Oracle Development Team**

- 📧 Email: your.email@university.edu
- 🐙 GitHub: [@yourusername](https://github.com/yourusername)
- 📍 Institution: [Your University Name]

### Project Links
- 📖 [Documentation](./docs/README.md)
- 🐛 [Report Issues](https://github.com/yourusername/campus-energy-oracle/issues)
- 💡 [Feature Requests](https://github.com/yourusername/campus-energy-oracle/discussions)

---

## 📚 Additional Resources

- **YOLO Documentation**: https://docs.ultralytics.com/
- **Flask Documentation**: https://flask.palletsprojects.com/
- **PyTorch Documentation**: https://pytorch.org/docs/stable/index.html
- **OpenCV Documentation**: https://docs.opencv.org/

---

## 🙏 Acknowledgments

- YOLO team for the outstanding object detection framework
- Flask team for the lightweight web framework
- PyTorch team for deep learning infrastructure
- Campus Energy Management initiative

---

## ⭐ Show Your Support

If you find this project useful, please consider:
- ⭐ Starring the repository
- 🐛 Reporting bugs and issues
- 💡 Suggesting improvements
- 📤 Sharing with the community

---

**Last Updated**: April 29, 2024
**Version**: 1.0.0
**Status**: Active & Maintained
