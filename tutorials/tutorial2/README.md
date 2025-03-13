# Tutorial 2
Fine-Tuning the Ball Detection Model

## Understanding the need for fine-tuning.
- As we saw in the video the table tennis ball was not detected in so many frames
- To get a higher sensitivity in the recognition we need to have a finetuned dataset especially for the table tennis ball
## Create a jupyter notebook
- We create a new folder called /training/
```
mkdir training
```
- We create a notebook inside here called table_tennis_ball_detector_training.ipnyb
```
nano table_tennis_ball_detector_training.ipynb
```
- We need to find a dataset to fill the notebook that we can utilise
## Finding or creating a table tennis ball dataset (Roboflow equivalent).
- For this part you need an account on Roboflow - where you can download the dataset
- Looking for a dataset in Roboflow from similar angles as in the video and I found this one
- we will use the model YoloV5 as this seems to be the best model for detecting table tennis balls and table tennis rackets
- Click on the model for example YoloV5 - and then look that you have download dataset
- Then you can choose click download code and YoloV5 Pytorch is fine and press continue
- In a Jupyter notebook copy and paste the code from the dataset
```
!pip install roboflow

from roboflow import Roboflow
rf = Roboflow(api_key="API_KEY")
project = rf.workspace("datasets-dl").project("imagenet-1k_tennis-table-ball")
version = project.version(6)
dataset = version.download("yolov5")
```
- 
- https://universe.roboflow.com/madianou-kqrfk/table-tennis-ball-detection/dataset/1
- 
## Preparing the dataset for training.
## Training a custom YOLO model (YOLOv5) on the ball dataset.
## Evaluating and comparing the fine-tuned model's performance.
