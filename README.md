# 🔐 Face Recognition Laptop Lock

A Python-based **Face Recognition Laptop Security System** that automatically locks a Windows laptop when the registered user moves away from the camera.

The system uses **OpenCV Haar Cascade** for face detection and **LBPH Face Recognizer** for face recognition.

## ✨ Features

* 👤 Register your face using the laptop camera
* 🧠 Train a face recognition model automatically
* 📷 Continuously monitor the user's face
* 🔒 Automatically lock the Windows laptop when the user is away
* ⏱️ Configurable absence time
* 🪟 Designed for Windows

## 📁 Project Structure

```text
Face-Recognition-Laptop-Lock/
│
├── dataset/
│   └── YourName/
│       ├── 1.jpg
│       ├── 2.jpg
│       └── ...
│
├── register.py
├── LaptopLock.py
└── README.md
```

## 🛠️ Technologies Used

* Python
* OpenCV
* Haar Cascade Classifier
* LBPH Face Recognition
* NumPy
* Windows `LockWorkStation`

## 📦 Installation

Install Python and the required libraries:

```bash
pip install opencv-contrib-python numpy
```

> **Note:** `opencv-contrib-python` is required because the project uses `cv2.face.LBPHFaceRecognizer_create()`.

## 🚀 How to Use

### 1. Register Your Face

Run:

```bash
python register.py
```

Enter your name when prompted.

The webcam will capture **50 face images** and store them inside:

```text
dataset/YourName/
```

Press **ESC** to stop registration early.

### 2. Start Laptop Locking

Run:

```bash
python LaptopLock.py
```

The program will:

1. Access the webcam.
2. Detect faces.
3. Compare the detected face with the registered dataset.
4. Keep the laptop unlocked while the registered user is detected.
5. Lock the Windows laptop if the registered user is not detected for more than **5 seconds**.

The locking command used is:

```python
os.system("rundll32.exe user32.dll,LockWorkStation")
```

## ⚙️ Configuration

The default absence time is:

```python
away_time = 5
```

For example, to lock after 10 seconds:

```python
away_time = 10
```

## 🔄 Workflow

```text
Start
  ↓
Register Face
  ↓
Capture 50 Images
  ↓
Store Images in Dataset
  ↓
Start LaptopLock.py
  ↓
Detect Face
  ↓
Recognize Registered User
  ↓
User Present? ── Yes ──→ Continue Monitoring
  │
  No
  ↓
Wait 5 Seconds
  ↓
Lock Windows Laptop
```

## ⚠️ Important Notes

* This project is intended for **Windows** because `LockWorkStation` is a Windows-specific command.
* Good lighting improves recognition accuracy.
* The recognition threshold can be adjusted from:

```python
if confidence < 80:
```

* This is a demonstration/security project and should not be considered a replacement for Windows authentication or enterprise-grade biometric security.

## 👨‍💻 Project Purpose

This project demonstrates how **computer vision and face recognition** can be used to create an automatic laptop security mechanism that locks the system when the authorized user moves away.

## 📜 License

This project is open-source and can be modified for educational and personal use.
