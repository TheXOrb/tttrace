# Object Tracking and Player Identification:
## Understanding the concept of object tracking
- The object tracking will look at each bounding boxes for each object in each frames and correlate them
- We can still use Ultralytics but instead of predict we will use the function track like this
```
result = model.track('input_file.mpg', conf=0.2, save=True)
```
## Using YOLO's tracking capabilities
## Assigning unique IDs to players
## Applying tracking to table tennis player movements
## Understanding the benifits of tracking for table tennis
