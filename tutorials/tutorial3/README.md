# Object Tracking and Player Identification:
## Understanding the concept of object tracking
- The object tracking will look at each bounding boxes for each object in each frames and correlate them

## Using YOLO's tracking capabilities
- We can still use Ultralytics but instead of predict we will use the function track like this, and also use Yolov8x instead of the newly finetuned training
```
model = YOLO(yolov8x)

result = model.track('input_file.mpg', conf=0.2, save=True)
```
## Assigning unique IDs to players
- If you now look into the video you will se that each player will have a bounding box with an id correlated to the right player
## Applying tracking to table tennis player movements
## Understanding the benifits of tracking for table tennis
