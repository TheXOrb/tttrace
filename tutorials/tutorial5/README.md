## Tutorial 5
### Integrating Models and Calculating Metrics (Ball Speed, Player Movement):
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| 💤 | 💤 | TL5-1 | Combining the player detection, ball detection, and keypoint detection models |
| 💤 | 💤 | TL5-2 | Calculating ball speed and player movement using detected data |
| 💤 | 💤 | TL5-3 | Determining if the ball is "in" or "out" using keypoints |
| 💤 | 💤 | TL5-4 | Calculating player coverage  |

## Combining the Player Detection, Ball Detection, and Keypoint Detection Models

- Now we will combine the other tutorials to put everything together.
- We will first create a `main.py` file that will put everything together.
- We will create a `main` function:

```python
def main():
    print("Hello, world")

if __name__ == "__main__":
    main()
```

- We are going to process every frame individually rather than analyzing the whole video at once.
- We will create a new folder called `utils`.
- We will create a new file called `video_utils.py`.
- We will import OpenCV (`cv2`) in `video_utils.py` to handle video processing.

```python
import cv2

def read_video(video_path):
    cap = cv2.VideoCapture(video_path)
    frames = []
    while True:
        ret, frame = cap.read()
        if not ret:
            break
        frames.append(frame)
    cap.release()
    return frames

def save_video(output_video_frames, output_video_path):
    fourcc = cv2.VideoWriter_fourcc(*'MJPG')
    frame_size = (output_video_frames[0].shape[1], output_video_frames[0].shape[0])
    out = cv2.VideoWriter(output_video_path, fourcc, 24, frame_size)
    for frame in output_video_frames:
        out.write(frame)
    out.release()
```

- To expose the functions outside `utils`, we need to initialize a file called `__init__.py`:

```python
from .video_utils import save_video, read_video
```

- Then we can use these functions in `main.py`:

```python
from utils import read_video, save_video
```

- We can now read in the video and save the video, just to test the functions:

```python
import os

# Ensure output directory exists
os.makedirs("output_videos", exist_ok=True)

def main():
    input_video_path = "input_videos/image.mp4"
    video_frames = read_video(input_video_path)

    save_video(video_frames, "output_videos/output.avi")

if __name__ == "__main__":
    main()
```

- **Important:** Use `.avi` format for output files, otherwise OpenCV might return an error.

- Create a folder called `output_videos`.
- Run the script to verify that it correctly processes the video.
- If successful, we can now continue to add trackers.

## Implement trackers
- We now need to implement the trackers
- We start with the player tracker and create a new folder called /tracker/
- In the folder create a new file called player_tracker.py
- We create the file and the functions that are needed into this player_tracker.py
- We then need to expose it outside the function and then we need the __init__.py to fix this
```
from .player_tracker import PlayerTracker
```
- To use this tracker inside the main.py you need to import it
```
from trackers import PlayerTracker
``` 
- And in the main function you need to use the PlayerTreacker functions
```
# Detect the players
player_tracker = PlayerTracker(model_path='yolov8x')
player_detections = player_tracker.detect_frames(video_frames)
```
- Now we need to fix the player trackers on top of the original video.
- That is needed to be done in the player_tracker.py
- Add a function that are doing this
```
import cv2

def draw_bboxes(self, video_frames, player_detections):
    output_video_frames = []
    for frame, player_dict in zip(video_frames, player_detections):
        # Draw bounding boxes
        for track_id, bbox in player_dict.items[]:
            x1, y1, x2, y2 = bbox
            cv2.putText(frame, f"Player ID:" {track_id},(int(bbox[0], int(bbox[1] -10))),cv2.FONT_HERSHEY_SIMPLEX, 0.9, (0, 0, 255 ), 2)
``` 
            frame = cv2.rectangle(frame, (int(x1), int(y1), int(x2), int(y2)), (0, 0, 255), 2)
