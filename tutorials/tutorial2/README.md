# Tutorial 2: Fine-Tuning the Ball Detection Model

## Understanding the Need for Fine-Tuning
- In our initial detection attempts, the table tennis ball was not consistently detected in many frames.
- This happens because the default YOLO model is not specifically trained to detect small, fast-moving objects like a table tennis ball.
- To improve detection accuracy, we need a **fine-tuned dataset** specifically designed for table tennis ball recognition.

## Setting Up the Training Environment
### Create a Jupyter Notebook
1. Create a new directory for training:
    ```sh
    mkdir training
    ```
2. Navigate to the folder and create a Jupyter notebook:
    ```sh
    cd training
    nano table_tennis_ball_detector_training.ipynb
    ```
3. If you don’t have Jupyter installed, install it using pip:
    ```sh
    pip3 install jupyter
    ```
4. Run the notebook to ensure it works:
    ```sh
    jupyter nbconvert --to notebook --execute table_tennis_ball_detector_training.ipynb
    ```

## Finding or Creating a Table Tennis Ball Dataset
- A dataset is required to train the model for detecting table tennis balls.
- You can use **Roboflow** to find relevant datasets.
- A good dataset should contain **images from similar angles** to the video you are analyzing.
- **Recommended dataset**: [Table Tennis Ball Detection Dataset](https://universe.roboflow.com/madianou-kqrfk/table-tennis-ball-detection/dataset/1)
- We will use **YOLOv5** for training, as it provides the best detection accuracy for small objects like table tennis balls and rackets.

### Downloading the Dataset from Roboflow
1. Create an account on Roboflow.
2. Find a dataset with similar image perspectives.
3. Click on the dataset and select **YOLOv5 PyTorch** as the export format.
4. Click **Download Code** and copy the generated code.
5. Paste the code into a Jupyter notebook and execute it.
6. After downloading, a new folder will be created: `/imagenet-1k_tennis-table-ball/`.
7. Ensure the dataset is inside the correct folder structure:
    ```sh
    /imagenet-1k_tennis-table-ball/imagenet-1k_tennis-table-ball
    ```

## Preparing the Dataset for Training
- Once the dataset is downloaded, organize the files into **training**, **testing**, and **validation** sets.
- Move the dataset into the **training folder**.
- Verify that the dataset structure matches YOLO's expected format.

## Training a Custom YOLO Model (YOLOv5) on the Ball Dataset
- Using **Google Colab** is highly recommended for training, as it provides free GPU resources.
- YOLOv5 requires setting specific parameters like **image size**, **batch size**, and **epochs**.

### Training on Google Colab
```sh
!yolo task=detect mode=train model=yolov5l6u.pt data={dataset.location}/data.yaml epochs=100 imgsz=640
```
- This command trains the model with:
  - `100 epochs`
  - Image size of `640x640`
  - The `yolov5l6u.pt` model, which is a large version optimized for detection.
- Training time:
  - **20 epochs** took **0.335 hours**
  - **100 epochs** took **1.265 hours**

### Training Locally (For CPU Users)
```sh
!yolo task=detect mode=train model=yolov5su.pt data={dataset.location}/data.yaml epochs=1 imgsz=320 device=cpu batch=1 workers=0
```
- This method is significantly slower, taking around **10 minutes per epoch** and this is only for the image size of 320.

### Saving the Trained Model
- Once training is complete, the model weights will be saved inside:
  ```sh
  /runs/detect/weights/
  ```
- Copy the files `last.pt` and `best.pt` to the **models** directory for later use.
  ```sh
  cp runs/detect/weights/best.pt models/
  cp runs/detect/weights/last.pt models/
  ```

## Evaluating and Comparing the Fine-Tuned Model’s Performance
- After training, we will use the model to test its accuracy in detecting table tennis balls in images and videos.
- In the yolo_inference.py change the model
```
mode = YOLO('/models/best-100.pt')
```
- Run the inference script to analyze detection results:
  ```sh
  python3 yolo_inference.py
  ```
- **Results Analysis:**
  - **Detection Accuracy:** Check how many frames detect the ball correctly.
  - **False Positives:** Ensure no unwanted objects are classified as balls.
  - **Frame Consistency:** The ball should be detected across consecutive frames.

## Combining YOLOv5 and YOLOv8 for Comprehensive Analysis
- Since **YOLOv5** is optimized for **ball detection** and **YOLOv8** is better for **player detection**, we will use both models together.
- YOLOv5 will be used to **detect the ball**, while YOLOv8 will **track the players**.
- This combination ensures:
  - High accuracy in ball tracking.
  - Player identification with unique IDs.

## Next Steps
With our fine-tuned model ready, the next tutorial will cover:
- Integrating **YOLOv5 and YOLOv8** together.
- Using object tracking to **follow the ball’s motion**.
- Analyzing ball speed, player movement, and in-game statistics.

This fine-tuned model will significantly improve our table tennis analysis accuracy and consistency!

## My training set was maybe not sufficient good 
- Will need to train a new dataset and I will try to do this
- We will need the video .mp4
- We will need ffmpg to extract each frame from the video
- We will need labelme to finetune the dataset
- Run the command
```
ffmpeg -i din_video.mp4 -vf fps=25 bildruta_%04d.jpg
```
- Now you will have a lot of pictures in the folder
- Skapa en ny mapp med alla bilder
```
mkdir table_tennis_balls
```
- Start the labelme application
- Choose the directory where you placed all your pictures
- Choose to create a rectangle and mark the ball
- Create the label and mark the ball
- Annotate the ball
- Zip all the files
- Upload the Zip files to chatgpt and convert the file to yolo format
- 
- 
