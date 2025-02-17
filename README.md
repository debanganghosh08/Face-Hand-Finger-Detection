# 🖐️ Face & Finger Detection using OpenCV and Mediapipe

## 🎯 Overview
This project implements real-time **Human Face Detection** and **Finger Count Detection** using **Python, OpenCV, and Mediapipe**. It captures video from a webcam, detects faces using Mediapipe’s Face Detection module, and counts the number of fingers raised using Mediapipe’s Hand Landmarks module. The output displays the detected face inside a **green bounding box**, while detected hands are marked with **blue bounding boxes** along with the counted number of fingers.

---

## 🧠 Face Detection Logic
Mediapipe’s **FaceDetection** model is used to detect faces. The following logic is implemented:

1. Convert the captured **BGR frame to RGB** as Mediapipe processes images in RGB format.
2. Apply **FaceDetection.process()** to detect faces.
3. If a face is detected, extract **bounding box coordinates** from the detection data.
4. Draw a **green rectangle** around the detected face.

### Code Implementation:
```python
# Convert to RGB for Mediapipe
rgb_frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)

# Face Detection
face_results = face_detection.process(rgb_frame)

# Draw bounding box for detected face
if face_results.detections:
    for detection in face_results.detections:
        bboxC = detection.location_data.relative_bounding_box
        ih, iw, _ = frame.shape
        x, y, w, h = int(bboxC.xmin * iw), int(bboxC.ymin * ih), int(bboxC.width * iw), int(bboxC.height * ih)
        cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 255, 0), 2)  # Green box
```

---

## ✋ Hand & Finger Detection Logic
For hand tracking and finger count:

1. Process the frame using **Mediapipe Hands** to detect hand landmarks.
2. Define **finger tip indices**: `[4, 8, 12, 16, 20]` for Thumb to Pinky.
3. Compare each **finger tip's Y-coordinate** with the second knuckle (to check if a finger is raised).
4. Use a special case for the **thumb**, comparing X-coordinates.
5. Display the detected **finger count** on the screen.

### Code Implementation:
```python
# Define Finger Tip Landmarks (Thumb to Pinky)
FINGER_TIPS = [4, 8, 12, 16, 20]

def count_fingers(hand_landmarks):
    count = 0
    if hand_landmarks:
        landmarks = hand_landmarks.landmark
        for tip in FINGER_TIPS[1:]:  # Exclude thumb (special case)
            if landmarks[tip].y < landmarks[tip - 2].y:
                count += 1
        
        # Thumb special case
        if landmarks[FINGER_TIPS[0]].x > landmarks[FINGER_TIPS[0] - 1].x:
            count += 1
    return count
```

---

## ⚙️ Code Breakdown (How it Works?)

1. **Import Required Libraries**:
   ```python
   import cv2
   import mediapipe as mp
   ```

2. **Initialize Mediapipe Modules**:
   ```python
   mp_hands = mp.solutions.hands
   mp_face = mp.solutions.face_detection
   mp_drawing = mp.solutions.drawing_utils
   ```

3. **Initialize Webcam**:
   ```python
   cap = cv2.VideoCapture(0)
   ```

4. **Define Detection Models**:
   ```python
   hands = mp_hands.Hands(min_detection_confidence=0.7, min_tracking_confidence=0.7)
   face_detection = mp_face.FaceDetection(min_detection_confidence=0.7)
   ```

5. **Process Frames in Real-Time**:
   - Convert **BGR to RGB**.
   - Detect **face & hand landmarks**.
   - Draw **bounding boxes & landmarks**.
   - Count and display **finger count**.

6. **Display the Output & Exit on 'q' Press**:
   ```python
   cv2.imshow("Face & Hand Detection", frame)
   if cv2.waitKey(1) & 0xFF == ord('q'):
       break
   ```

---

## 🛠️ Requirements & Installation

### **🔹 Prerequisites**
- Python 3.x
- OpenCV
- Mediapipe

### **📌 How to Install Dependencies?**
```bash
pip install opencv-python mediapipe
```

### **🚀 How to Run the Project?**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/face-finger-detection.git
   cd face-finger-detection
   ```
2. **Run the Python Script**:
   ```bash
   python face_finger_detection.py
   ```
3. **Press 'q' to Exit**.

---

## 📸 Project Demo (Screenshots)

![Git image README](https://github.com/user-attachments/assets/3229186a-9f14-49e3-8cad-0ba9bdaadc17)


---

## 🤝 Contributing
Contributions are welcome! Feel free to submit a pull request or open an issue.

---

## 📩 Contact
For any queries or collaborations, reach out via **primusvlog@gmail.com** or connect on **https://www.linkedin.com/in/debangan-ghosh/**.

