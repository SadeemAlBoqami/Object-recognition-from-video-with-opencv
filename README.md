# Object-recognition-from-video-with-opencv
Running a YOLOv8-ready model to detect multiple objects within a video using OpenCV.
## Overview:
This project uses the YOLOv8 Nano model integrated with OpenCV to detect multiple objects in real-time from video files. It's lightweight, fast, and easy to run.

## Requirements
1. From anaconda>>base>>open terminal install these packages:
```python pip install opencv-python
pip install ultralytics opencv-python 
```
2. After that open vs code from terminal by typing: ```python code .
   ```
3. Open your project folder which contains the model code and video that will be tested.
4. In same folder, create python file or download it (yolo_detect.py).
5. Running your code, the output will appear as a video after recognizing the elements, you will notice that there is a box around each element with its name whose elements have been recognized by the model.

## The structure of the code and how it works:
1. Import libraries:
   - cv2 library from opencv to read video, view images and draw boxes.
   - Ultralytics.YOLO to download and run the YOLOv8 prototype.
```python
     import cv2
     from ultralytics import YOLO
```

2. Download the model: There are several versions of the YOLO model, multiple speeds and resolutions, I chose Nano, the lightweight version of the model, supporting more than 80 types of objects (people, cars, bicycles, etc.)
```python
model = YOLO('yolov8n.pt') #It loads automatically the first time
   ```
3. Open the video file and edit the video frame measurements:  Cap is an object that represents the video.
```python
cap = cv2.VideoCapture('test6.mp4')
cv2.namedWindow("YOLOv8 Detection", cv2.WINDOW_NORMAL)
cv2.resizeWindow("YOLOv8 Detection", 1280, 720)
   ```
4. Read the video frame by frame
```python
while True:
    ret, frame = cap.read()
    if not ret:
        break
   ```
5. Play the model on each Frame
```python
results = model(frame)
   ```
6. Extract objects, draw rectangle and text
```python
    for result in results:
        boxes = result.boxes
        for box in boxes:
            x1, y1, x2, y2 = map(int, box.xyxy[0])
            conf = box.conf[0]
            cls = int(box.cls[0])
            label = model.names[cls]
            cv2.rectangle(frame, (x1, y1), (x2, y2), (0, 255, 0), 2)
            text = f"{label} {conf:.2f}"
            cv2.putText(frame, text, (x1, y1 - 10), cv2.FONT_HERSHEY_SIMPLEX,
                        0.6, (0, 255, 0), 2)
   ```
7. Displaying the Frame to the user
```python
    cv2.imshow("YOLOv8 Detection", frame)
   ```
8. Exit when pressing q
```python
 if cv2.waitKey(25) & 0xFF == ord('q'):
        break
   ```
9. Cleaning the memory after the video ends
```python
cap.release()
cv2.destroyAllWindows()
   ```
