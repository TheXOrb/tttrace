# Tutorial 1: Setting Up and Basic Object Detection (Table Tennis)

## Introduction (2-3 minutes)
- The goal of this project is to analyze **table tennis matches** using computer vision.
- We will use **Ultralytics YOLO**, a state-of-the-art object detection model, to detect and track table tennis objects.
- Key object detection concepts:
  - **Bounding boxes**: Rectangles around detected objects.
  - **Class names**: The object category (e.g., player, ball, racket).
  - **Confidence scores**: A probability (0-1) indicating detection certainty.

## Environment Setup (5-7 minutes)
### Project Folder Structure
- Organize files for easier access:
  ```
  /input_videos/     # Video clips for testing and validation
  /output_videos/    # Processed videos with detections
  ```
- The `/input_videos/` folder contains sample clips for testing.

### Installing Dependencies
#### 1. Install a Python virtual environment:
```sh
sudo apt install python3-venv
```
#### 2. Create and activate the virtual environment:
```sh
python3 -m venv tttrace_env
source tttrace_env/bin/activate
```
#### 3. Install Ultralytics YOLO:
```sh
pip install ultralytics
```
#### 4. To exit the virtual environment:
```sh
deactivate
```
#### 5. Show sample images and videos of table tennis for reference.

## Handling Limited Storage Issues with PIP and Ultralytics
If you encounter **storage issues**, configure PIP to use a different cache location:
```sh
# Create a new cache directory:
sudo mkdir -p /mnt/sdb/pip-cache

# Set the new cache directory:
export PIP_CACHE_DIR=/mnt/sdb/pip-cache

# Make this change permanent:
echo 'export PIP_CACHE_DIR=/mnt/sdb/pip-cache' >> ~/.bashrc
source ~/.bashrc
```

## Basic YOLO Inference (10-12 minutes)
### 1. Create a YOLO inference script
```sh
nano yolo_inference.py
```
### 2. Write the following code:
```python
from ultralytics import YOLO

# Load the YOLOv8x model
model = YOLO('yolov8x')

# Run inference on an image and save the results
model.predict('input_videos/image.png', save=True)
```
- This will create a **new folder** containing the detected image:
  ```sh
  /runs/detect/predict/image.png
  ```

### 3. Running YOLO inference
```sh
python3 yolo_inference.py
```
- This command **downloads YOLOv8x** (if not already downloaded) and processes the image.
- The output will be saved in the `/runs/detect/predict/` folder.
- Open the image to view **bounding boxes** drawn around detected objects.

### 4. Extending the Inference Code
We can **extend** our script to print detection results:
```python
from ultralytics import YOLO

# Load the model
model = YOLO('yolov8x')

# Run inference on an image and store results
result = model.predict('input_videos/image.png', save=True)

# Print detected objects
print(result)

# Print bounding boxes for each detected object
print("Bounding boxes:")
for box in result[0].boxes:
    print(box)
```
- Running this script will create a **new prediction folder** (`predict2`).
- The **output** includes:
  - **Bounding boxes** around objects.
  - **Class names** (e.g., person, racket, ball).
  - **Confidence scores** indicating detection accuracy.

## Video Inference and Initial Observations (5-8 minutes)
### Running YOLO on a Table Tennis Video
Modify our script to **process a video** instead of an image:
```python
# Run inference on a video and save the results
result = model.predict('input_videos/image.mp4', save=True)
```
- The output video will be saved in:
  ```sh
  /runs/detect/predict3/image.avi
  ```
- Open the **output video** to observe YOLO's detection in action.

### Observations and Challenges
- **Detection Issues:**
  - The **table tennis ball** is **often missed** or not labeled as a "sports ball".
  - The **racket** may be classified as a **"baseball glove"**.
- **Challenges:**
  - The **ball moves too fast** for accurate detection.
  - Players and objects **overlap**, making tracking harder.

### Preparing for the Next Step
In the **next tutorial**, we will:
- **Fine-tune YOLOv5** to better detect **table tennis balls** and **rackets**.
- Train on a **custom dataset** to improve accuracy.
- Optimize detection for **fast-moving objects**.

Stay tuned for **Tutorial 2: Fine-Tuning the Ball Detection Model**!
