## Tutorial 5
### Integrating Models and Calculating Metrics (Ball Speed, Player Movement):
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| 💤 | 💤 | TL5-1 | Combining the player detection, ball detection, and keypoint detection models |
| 💤 | 💤 | TL5-2 | Calculating ball speed and player movement using detected data |
| 💤 | 💤 | TL5-3 | Determining if the ball is "in" or "out" using keypoints |
| 💤 | 💤 | TL5-4 | Calculating player coverage  |

## Combining the player detection, ball detection, and keypoint detection models 
- Now we will combine the other tutorials to put everything together
- We will first create a main.py file that will put everything together
- We will create a main function
```
def main():
    print("Hello, world")

if __name__ == __main__:
    main()
```
- We are going to take care of every frame and not take the whole video
- We will create a new folder called utils
- We will create a new file called video_utils.py
- We will import cv2 in the video utils to take care of the video
```
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
    out = cv2.VideoWriter(output_video_path, fourcc, 24, (output_video_frames[0>
    for frame in output_video_frames:
        out.write(frame)
    out.release()
```
- To expose the functions outside the utils we need to initalise a file called __init__.py
```
from .video_utils import save_video, read_video
```
- Then we can use the functions in main
```
from utils import (read_video,
                   save_video)
``` 
- We can now read in the video and save the video - just to try the functions and see if this works
- Important to use avi in the output folder else you will get error
```
def main():
    input_video_path = "input_videos/image.mp4"
    video_frames= read_video(input_video_path)

    save_video(video_frames, "output_videos/output.avi")
```
- Create a folder called output_video
