# Face Recognition System

## Overview
This project is a real-time face recognition and attendance system built with Python. It uses deep learning for face detection and recognition, and includes basic anti-spoofing by detecting mobile phones in the frame. The system can be integrated with a Django backend for attendance management.

## Features
- Real-time face detection and recognition using facenet-pytorch (MTCNN + FaceNet)
- Anti-spoofing: Detects mobile phones using YOLO and flags possible spoofing attempts
- Attendance marking via Django backend
- Modular code for training and recognition

## Project Structure
```
face_recognition/
├── classifier.py
├── detect_face.py
├── facenet.py
├── face_recognition.py         # Main recognition script
├── piped.py                    # Real-time recognition with anti-spoofing
├── preprocess.py
├── requirements.txt            # Python dependencies
├── rtsp.py
├── train.py                    # Training script for classifier
├── model/                      # Pre-trained FaceNet model
├── object_detection/           # YOLO and related files
├── image_feed/                 # Input images or video
```

## Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/Lalithag-19/face_recognition.git
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## Usage
### 1. Train the Classifier
- Prepare a dataset of aligned face images in `aligned_images/` (one folder per person).
- Run:
  ```bash
  python train.py
  ```
- This will generate `classifier.pkl` for recognition.

### 2. Run Real-Time Recognition
- For webcam or video stream:
  ```bash
  python piped.py
  ```
- The system will display recognized faces and flag spoofing attempts.

## Key Libraries Used
- **facenet-pytorch**: Face detection (MTCNN) and embeddings (FaceNet)
- **OpenCV**: Image/video processing
- **TensorFlow**: Deep learning backend for FaceNet
- **scikit-learn**: SVM classifier and label encoding
- **ultralytics (YOLO)**: Object detection for anti-spoofing
- **Django**: Backend integration for attendance

## Anti-Spoofing
- The system uses YOLO to detect mobile phones. If a phone overlaps with a detected face, it flags a possible spoofing attempt (e.g., someone showing a photo on a phone).

## Extending the Project
- Add more faces by updating the dataset and retraining.
- Integrate advanced liveness detection for stronger anti-spoofing.
- Connect to other backends or databases as needed.

## License
This project is for educational and research purposes.
