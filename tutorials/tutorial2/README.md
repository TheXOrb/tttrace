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
- If you dont have jupyter installed on the machine you need to install it
```
pip3 install jupyter
```
- Try to run the file
```
jupyter nbconvert --to notebook --execute table_tennis_ball_detector_training.ipynb

```
- We need to find a dataset to fill the notebook that we can utilise

## Finding or creating a table tennis ball dataset (Roboflow equivalent).
- For this part you need an account on Roboflow - where you can download the dataset
- Looking for a dataset in Roboflow from similar angles as in the video and I found this one
- we will use the model YoloV5 as this seems to be the best model for detecting table tennis balls and table tennis rackets
- Click on the model for example YoloV5 - and then look that you have download dataset
- Then you can choose click download code and YoloV5 Pytorch is fine and press continue
- In a Jupyter notebook copy and paste the code from the dataset
- - In the file create the following code 
```
{
 "cells": [
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "!pip install roboflow\n",
    "!pip install ultralytics"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": [
    "# Get Dataset\n",
    "\n",
    "from roboflow import Roboflow\n",
    "rf = Roboflow(api_key=\"API_KEY\")\n",
    "project = rf.workspace(\"datasets-dl\").project(\"imagenet-1k_tennis-table-ball\")\n",
    "version = project.version(6)\n",
    "dataset = version.download(\"yolov5\")"
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.10.12"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}```
- 
- https://universe.roboflow.com/madianou-kqrfk/table-tennis-ball-detection/dataset/1
- 
## Preparing the dataset for training.
## Training a custom YOLO model (YOLOv5) on the ball dataset.
## Evaluating and comparing the fine-tuned model's performance.
