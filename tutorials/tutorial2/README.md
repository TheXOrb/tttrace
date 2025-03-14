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
- After the file hase been runned - there will be a new folder create called /imagenet-1k_tennis-table-ball/
- If we want to train the dataset we need to have the exact same folder inside the folder in this case /imagenet-1k_tennis-table-ball/imagenet-1k_tennis-table-ball
- 
- https://universe.roboflow.com/madianou-kqrfk/table-tennis-ball-detection/dataset/1
- 
## Preparing the dataset for training.
## Training a custom YOLO model (YOLOv5) on the ball dataset.
- If you want to train the dataset, a strong advice is to use colab.research.google.com where you have free GPU resources.
- With colab you can also use larger models - this will take some times - for me it took around 40 seconds per each epoch
```
!yolo task=detect mode=train model=yolov5l6u.pt data={dataset.location}/data.yaml epochs=100 imgsz=640
```
- If you want to run it locally and if you not have GPU you can use the below code for the training
```
!yolo task=detect mode=train model=yolov5su.pt data={dataset.location}/data.yaml epochs=1 imgsz=320 device=cpu batch=1 workers=0
```
- This took me 10 minutes - with only 1 epoch and low image size
- 20 epochs completed in 0.335 hours.
- Now we have got files inside /runs/detect/weights that we will use
- Copy the files last.pt and best.pt to models
- 
## Evaluating and comparing the fine-tuned model's performance.
- now we can use this in the inferior file that we created from the beginning in the first tutorial
- 
