🚧 Real-Time Pothole Detection on Raspberry Pi using ONNX

An edge AI system that performs real-time pothole detection using a Raspberry Pi camera and an ONNX deep learning model. The system processes live video, performs inference on-device (CPU), and displays prediction results with FPS and confidence metrics.

📌 Project Overview

This project implements a real-time road anomaly detection pipeline using:

Raspberry Pi 4

Raspberry Pi Camera Module

ONNX Runtime (CPU)

OpenCV

GStreamer + libcamera pipeline

The system captures live video input, processes frames through a trained ONNX model, and detects potholes with performance metrics displayed on screen.

🧠 Features

✅ Live camera-based pothole detection

✅ ONNX Runtime (CPU inference)

✅ Real-time FPS display

✅ Inference time measurement

✅ Confidence score display

✅ Running average confidence metric

✅ Fully compatible with modern Raspberry Pi OS (Bookworm / Trixie)

🏗️ System Architecture
Raspberry Pi Camera
        ↓
libcamera (libcamerasrc)
        ↓
GStreamer Pipeline
        ↓
OpenCV
        ↓
ONNX Runtime (CPU)
        ↓
Live Detection Output (FPS + Confidence)
🛠️ Hardware Requirements

Raspberry Pi 4 Model B

Raspberry Pi Camera Module v2 or
Raspberry Pi Camera Module 3

MicroSD Card (16GB+)

Power Supply (5V 3A recommended)

💻 Software Requirements

Raspberry Pi OS (Debian 12 Bookworm or Debian 13 Trixie)

Python 3.9+

ONNX Runtime (CPU)

OpenCV

GStreamer

libcamera stack

⚙️ Installation
1️⃣ Update System
sudo apt update
sudo apt full-upgrade -y
sudo reboot
2️⃣ Install Required Packages
sudo apt install -y \
rpicam-apps \
libcamera-dev \
gstreamer1.0-tools \
gstreamer1.0-libcamera \
gstreamer1.0-plugins-base \
gstreamer1.0-plugins-good \
gstreamer1.0-plugins-bad \
python3-opencv \
python3-pip
3️⃣ Install Python Dependencies
pip3 install onnxruntime numpy

⚠️ Do NOT install onnxruntime-gpu on Raspberry Pi.

🎥 Verify Camera
rpicam-hello

Verify GStreamer plugin:

gst-inspect-1.0 libcamerasrc
🚀 Running the Project

Ensure your ONNX model file is placed in the project directory:

pothole_model.onnx

Run:

python3 pothole_detection.py

Press q to exit.

📊 Output Display

The system overlays the following metrics on the video feed:

Predicted Class (Pothole / Normal Road)

Confidence Score

FPS (Frames Per Second)

Inference Time (ms)

Running Average Confidence

📈 Performance (Raspberry Pi 4 - CPU)
Model Type	FPS	Inference Time
Lightweight CNN	10–15 FPS	70–100 ms
MobileNet-based	5–10 FPS	120–200 ms
Heavy CNN	<5 FPS	250+ ms

Performance depends on model size and optimization.

📦 Project Structure
├── pothole_detection.py
├── pothole_model.onnx
├── README.md
└── requirements.txt
🔬 Accuracy Considerations

Live camera mode does not provide true dataset accuracy.

For proper evaluation:

Run model on labeled dataset

Compute confusion matrix

Calculate precision, recall, F1-score

Future versions may include dataset evaluation scripts.

⚡ Optimization Tips

Use quantized ONNX model (INT8)

Reduce input resolution (e.g., 160x160)

Use lightweight backbone (MobileNetV2)

Close all background processes

Ensure only one camera process is running

🧯 Troubleshooting
Camera Not Opened

Ensure no other process is using camera

Run sudo killall rpicam-hello

Verify gst-inspect-1.0 libcamerasrc

Green Tint

Use proper tuning file

Adjust AWB settings

Verify correct camera module

Low FPS

Reduce input resolution

Use quantized model

Ensure CPU-only provider is used

🔮 Future Improvements

Object detection (bounding box model)

Edge TPU acceleration

Real-time logging system

Integration with ADAS system

Automatic braking trigger integration

📜 License

This project is intended for academic and research purposes.

👨‍💻 Author

Susanth V
B.Tech – Computer and Communication Engineering
Amrita Vishwa Vidyapeetham
