# Tutorials directory
### Progress indication
💤 Not started  
🟡 In progress  
✅ Complete  

| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 🟡 | HL1 | The vertical slice can start without any more services running |

## Tutorial to setup TT Net - from https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/
### Setting up the Environment and Basic Object Detection (Table Tennis Players and Ball):
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 💤 | TL1-1 | Installing necessary libraries (Ultralytics) |
| ✅ | 💤 | TL1-2 | Understanding YOLO and its basic usage |
| ✅ | 💤 | TL1-3 | Running inference on a sample image and video |
| ✅ | 💤 | TL1-4 | Analyzing the output (bounding boxes, confidence scores, class names)  |
| ✅ | 💤 | TL1-5 | Adapting the model to table tennis |

## Instructions
- First go to the repo TTNet Real time
- Follow the tutorial to setup a virtual environment for Python - https://github.com/maudzung/virtual_environment_python3
- First run the comman
```
git clone https://github.com/maudzung/virtual_environment_python3.git
```
- Then follow the guide from the link above
- Trying to simplify
```
python3 -m venv ttnet_env
```
- Then activate the environment
```
source ttnet_env/bin/activate
```
- Download the TTNet repo
```
git clone https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch.git
```
- Go into the repo TTNet
- When trying to install the Pytorch is outdated and is not possible to install
- In the requirements.txt there is a need to update the file with the following: 
```
torch==2.1.0
torchvision==0.16.0
easydict==1.10
opencv-python==4.8.0.76
numpy==1.26.0
torchsummary==1.5.1
tensorboard==2.14.1
scikit-learn==1.3.1
```
- In the virtual environment install the following
```
sudo apt-get install libturbojpeg0
pip install PyTurboJPEG
```


## Files
https://drive.google.com/file/d/1y-qtMazXLqJ0UryNlICTgGIQ4z0ZhbMh/view?usp=sharing  
https://drive.google.com/file/d/14NEW-Rgz6XlVlcVOkWlL7Io6jeeS4SeU/view?usp=sharing  
https://drive.google.com/file/d/1tt2yO83nhbzSUUSZZTHCH6Z4szsdyoJS/view?usp=sharing  
  
run file - https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/blob/master/src/demo.sh

