# 📥 Installation Guide for Face & Hand Finger Detection

## 🔹 Clone the Repository
To get started, clone this repository from GitHub using the following command:
```bash
git clone https://github.com/debanganghosh08/Face-Hand-Finger-Detection.git
cd Face-Hand-Finger-Detection
```

---

## 🛠️ System Requirements
Before running the project, ensure you have the following:
- **Operating System**: Windows, macOS, or Linux
- **Python Version**: Python 3.7 or later
- **Webcam**: Required for real-time detection

---

## 📌 Install Dependencies
This project requires **OpenCV** and **Mediapipe**. You can install all dependencies using:
```bash
pip install opencv-python mediapipe
```

If you face any issues, try installing them separately:
```bash
pip install opencv-python
pip install mediapipe
```

For Jupyter Notebook users, install OpenCV and Mediapipe inside the notebook environment:
```python
!pip install opencv-python mediapipe
```

---

## 🚀 Running the Project
Once the dependencies are installed, you can run the project using:
```bash
python face_finger_detection.py
```

### **Instructions:**
1. Make sure your **webcam** is connected and enabled.
2. The script will **detect faces** and **count fingers** in real-time.
3. Press **'q'** to exit the application.

---

## 🛠️ Troubleshooting
**1. Import Errors?**
   - Ensure you have installed all required libraries (`pip list` to check).
   - Try running Python in a **virtual environment**.
   
**2. Webcam Not Opening?**
   - Restart your system and try again.
   - Check if another application is using the webcam.
   
**3. Slow Performance?**
   - Reduce video resolution in the script.
   - Close background applications to free up RAM.

---

## 📞 Need Help?
For any issues, open an **[issue on GitHub](https://github.com/debanganghosh08/Face-Hand-Finger-Detection/issues)** or reach out via email.

---

Enjoy real-time **Face & Finger Detection!** 🚀

