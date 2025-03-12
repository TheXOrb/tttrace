# Tutorial 1
Setting Up and Basic Object Detection (Table Tennis)

## Introduction (2-3 minutes):
- Briefly explain the project's goal: analyzing table tennis matches using computer vision.
- Introduce the tools we'll be using: Python, Ultralytics YOLO.
- Explain the basic concepts of object detection (bounding boxes, confidence scores).
## Environment Setup (5-7 minutes):
- Explain the project folder structure (input videos, output folders).
  - /input_video/ - here is the material that we will use to validate and test the development we are doing
  - /output_video/ - here is the output material that are tested and have gone trough the development
- In the root folder /input_video/ is two clips where we can test the code against
- Install a virtual environment for python3 first 
```
sudo apt install python3-venv
```
- Create a virtual environment after that
```
python3 -m venv tttrace_env
```
- Activate the environment
```
source tttrace_env/bin/activate
```
- Now install ultralytics
```
pip install ultralytics
```
- To exit from the virtual environment
```
deactivate
```
- Show sample images and videos of table tennis.
## Basic YOLO Inference (10-12 minutes):
- Create a new file in the folder called yolo_inference.py
```
nano yolo_inference.py
```
- Now we will create some code and import the ultralytics that we earlier installed
```
from ultralytics import YOLO
# To import a YOLO model and which model
model = YOLO('yolov8x')
# To run it on an image - give it the image path, we also want to save it
model.predict('input_videos/image.png', save=True)
# After this code is runned - it will create a new folder called /runs/detect/predict/image.png
```
- If you looked at the picture that is created you will find rectangles with the detections that are found in the images with the Yolo model
- We will now extend the code and improve it - complete code from the above and extended
```
from ultralytics import YOLO
# To import a YOLO model and which model
model = YOLO('yolov8x')
# To run it on an image - give it the image path, we also want to save it
# Store the output in a varible 
result = model.predict('input_videos/image.png', save=True)
# After this code is runned - it will create a new folder called /runs/detect/predict2/image.png
# We can print the result
print(result)
# We also print out the bounding boxes
print("boxes:")
for box in result[0].boxes:
  print(box)
```
- After you run this the second time you will have a new folder called /predict2/

- Demonstrate how to load a pre-trained YOLO model (YOLOv8).
- Run inference on a sample table tennis image.
- Explain the output: bounding boxes, class names, confidence scores.
  - Around each object that is detected there is a bounding box
  - Each bouding box have a class name
  - Each bounding box also have the confidence score that ranges from 0-1 where higher number is more specific to the trained subject 
- Show how to save the detection results.
## Video Inference and Initial Observations (5-8 minutes):
- Run YOLO inference on a sample table tennis video.
- Now we can use this little snippet to change the .png to the .mp4 to run it on the video like this
```
# To run it on an image - give it the image path, we also want to save it
# Store the output in a varible 
result = model.predict('input_videos/image.mp4', save=True)
# After this code is runned - it will create a new folder called /runs/detect/predict3/image.mp4
``` 
- Discuss the initial detection results.
- We will see that the table tennis ball is not recognised as a sports ball many times
- Highlight potential challenges (e.g., fast-moving ball, overlapping players).
- What we will need now is to finetune the model so it can detect the small table tennis ball
- Adaptation to table tennis, explain the difference in court size, ball size, and player movement compared to tennis.
