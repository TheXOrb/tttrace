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
