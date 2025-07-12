# Object-recognition-from-video-with-opencv
Running a YOLOv8-ready model to detect multiple objects within a video using OpenCV.
## Overview:
This project uses the YOLOv8 Nano model integrated with OpenCV to detect multiple objects in real-time from video files. It's lightweight, fast, and easy to run.

## Requirements
1. From anaconda>>base>>open terminal install these packages:
pip install opencv-python
pip install ultralytics opencv-python

2. After that open vs code from terminal by typing: code .
3. Open your project folder which contains the model code and video that will be tested.
4. In same folder, create python file or download it (yolo_detect.py).
5. Running your code, the output will appear as a video after recognizing the elements, you will notice that there is a box around each element with its name whose elements have been recognized by the model.

## The structure of the code and how it works:
1. Import libraries:
   - cv2 library from opencv to read video, view images and draw boxes.
   - Ultralytics.YOLO to download and run the YOLOv8 prototype.
```pyton
     import cv2
     from ultralytics import YOLO

2. Download the model: There are several versions of the YOLO model, multiple speeds and resolutions, I chose Nano, the lightweight version of the model, supporting more than 80 types of objects (people, cars, bicycles, etc.)

3. Open the video file: Cap is an object that represents the video.
4. Read the video frame by frame
5: Play the model on each Frame
6. Extract objects, draw rectangle and text
7. Displaying the Frame to the user
8. Exit when pressing q
9. Cleaning the memory after the video ends
