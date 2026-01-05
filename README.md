# 😊 Smart Face, Eye & Smile Detection using OpenCV

A real-time computer vision application that detects **faces, eyes, and smiles** from a live webcam feed using OpenCV’s Haar Cascade classifiers.

---

## 🤔 Project Overview

This project demonstrates how classical computer vision techniques can be used to detect human facial features in real time. It uses **pre-trained Haar Cascade XML models** provided by OpenCV to identify:

* Human faces
* Eyes inside detected faces
* Smiles inside detected faces

Detected features are highlighted with bounding boxes and text labels.

---

## ✨ Features

* Real-time webcam-based detection
* Face detection using Haar Cascade
* Eye detection within detected faces
* Smile detection with status label
* Lightweight and beginner-friendly
* Press **Q** to exit the application

---

## 🛠️ Tech Stack

* **Language:** Python
* **Library:** OpenCV (cv2)
* **Models:** Haar Cascade XML classifiers
* **Input Device:** Webcam

---

## 📂 Project Structure

```
Smart-Face-Detector/
│-- smart_face_detector.py
│-- haarcascade_frontalface_default.xml
│-- haarcascade_eye.xml
│-- haarcascade_smile.xml
│-- README.md
```

---

## ⚙️ How It Works

### 1️⃣ Webcam Frame Capture

The webcam continuously captures frames using OpenCV.

```python
cap = cv2.VideoCapture(0)
```

---

### 2️⃣ Convert Frame to Grayscale

Haar Cascades work best on grayscale images.

```python
gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
```

---

### 3️⃣ Face Detection

The face cascade scans the frame and returns bounding box coordinates.

```python
faces = face_cascade.detectMultiScale(gray, 1.1, 5)
```

---

### 4️⃣ Region of Interest (ROI)

Eyes and smiles are detected **only inside the face area** for better accuracy.

```python
roi_gray = gray[y:y+h, x:x+w]
roi_color = frame[y:y+h, x:x+w]
```

---

### 5️⃣ Eye Detection

If eyes are detected, a label is displayed.

```python
eyes = eye_cascade.detectMultiScale(roi_gray, 1.1, 1)
```

---

### 6️⃣ Smile Detection

Smiles are detected using a stricter classifier configuration.

```python
smiles = smile_cascade.detectMultiScale(roi_gray, 1.7, 20)
```

---

### 7️⃣ Display Output

Bounding boxes and labels are drawn on the live feed.

```python
cv2.imshow("Smart Face Detector", frame)
```

---

### 8️⃣ Exit & Cleanup

Press **Q** to exit safely.

```python
cap.release()
cv2.destroyAllWindows()
```

---

## 📦 Installation

### 1️⃣ Install OpenCV

```bash
pip install opencv-python
```

### 2️⃣ Download Haar Cascade Files

Ensure the following files are present in your project directory:

* `haarcascade_frontalface_default.xml`
* `haarcascade_eye.xml`
* `haarcascade_smile.xml`

(Available from OpenCV’s official GitHub repository)

---

## ▶️ Run the Project

```bash
python smart_face_detector.py
```

---

## ⚠️ Notes

* Good lighting improves detection accuracy
* Smile detection may take a moment to trigger
* Works best with a front-facing camera
* Haar Cascades are fast but less accurate than modern deep learning models

---

## 🤝 Contributing

Contributions, improvements, and feature suggestions are welcome.
Feel free to open an issue or submit a pull request.

---

## 📜 License

This project is licensed under the **MIT License**.
You are free to use, modify, and distribute it.
