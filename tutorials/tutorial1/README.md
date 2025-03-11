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
- Demonstrate how to load a pre-trained YOLO model (YOLOv8).
- Run inference on a sample table tennis image.
- Explain the output: bounding boxes, class names, confidence scores.
- Show how to save the detection results.
## Video Inference and Initial Observations (5-8 minutes):
- Run YOLO inference on a sample table tennis video.
- Discuss the initial detection results.
- Highlight potential challenges (e.g., fast-moving ball, overlapping players).
- Adaptation to table tennis, explain the difference in court size, ball size, and player movement compared to tennis.
