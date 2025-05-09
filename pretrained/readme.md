# Taking on from where people have left and continue to contribute
## Build on google colab
- First add this to the row:
```
!git clone https://github.com/AugustRushG/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch.git
%cd TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch
```
- Then install the requirements
```
!pip install -r requirements.txt
```
- I need to change the requirement a lot -. because here are packages that are needed
```
!pip install easydict==1.13 opencv-python-headless==4.10.0.84 numpy==1.26.3 tensorboard==2.17.0 scikit-learn==1.5.1 tqdm==4.66.5 --extra-index-url https://download.pytorch.org/whl/cu121 torch==2.4.0
!pip install torch==2.3.0 torchvision==0.18.0 easydict==1.13 opencv-python==4.9.0.80 numpy==1.26.4 torchsummary==1.5.1 tensorboard==2.16.2 scikit-learn==1.5.0
```
- Create a new directory
```
!mkdir -p /content/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/checkpoints/ttnet_3rd_phase
!mkdir -p /content/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/dataset/test/videos

```
- Navigate to the directory
```
!ls -R /content/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/checkpoints
```
- Install gdown
```
!pip install gdown
```
- Download the pretrained weight
```
!gdown 1tt2yO83nhbzSUUSZZTHCH6Z4szsdyoJS
```
- Change the downloaded file to ttnet_3rd_phase_epoch_30.pth and it should be in the ttnet_3rd_phase directory
- Upload the video to the folder dataset/test/videos and rename the file to test_1.mp4 or test_6.mp4
- Now we should try to run this with the video and the trained dataset
```
!python /content/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/src/main.py --video_path ../dataset/test/videos/test_1.mp4 --resume_path ../checkpoints/ttnet_3rd_phase/ttnet_3rd_phase_epoch_30.pth
```


## Build on my computer with modification because I dont have any NVIDIA CUDA
- Will be based on this repo: https://github.com/AugustRushG/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch
- Will try to build it and see what happens
- Will create a virtual environment in anaconda on windows to try this out first
- To createa virtual environment in anaconda do this
```
conda create --name TTNet
```
- To activate the environment do
```
conda activate TTNet
```
- After this you will have a prompt that looks like (TTNet) first 
- To deactivate
```
conda deactivate
```
- To install git
```
conda install git
```
- To download the repo from August
```
git clone https://github.com/AugustRushG/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch.git
```
- Now you will have a folder with the TTNet go into it
```
cd folder_of_tt_net
```
- Now install the requirments first
```
pip install -U -r requirement.txt
```
- Install PyTurboJEPG also if it´s not already installed
```
pip install PyTurboJPEG
```
- To run a demo in anaconda do this, first go into the /src/ folder in the project
```
bash demo.sh
```
- When i run this in my anaconda environment i get missing cv2 module, if you get the same error you need to do this
```
conda install -c conda-forge opencv
```
- After this i run into the issue with torch,so installed
```
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```
- Think we got the demo running now
- Download the pretrained model in this path   --pretrained_path ../checkpoints/ttnet_3rd_phase/ttnet_3rd_phase_epoch_30.pth \
- If the directory doesnt exist go from the /src/ to the root folder and create the folder
```
mkdir checkpoints
cd checkpoints
mkdir ttnet_3rd_phase
cd ttnet_3rd_phase
```
- In this directory download the training set first install gdown
```
pip install gdown
```
- Now you can take the link from the dataset and download it in the folder
```
gdown 1tt2yO83nhbzSUUSZZTHCH6Z4szsdyoJS
```
- Rename the file from the downloaded to the right name like this
```
mv initial_file_name.pth ttnet_3rd_phase_epoch_30.pth
``` 
- Upload a video to the following path   --video_path ../dataset/test/videos/test_1.mp4 or test_6.mp4 \
- If the path doesnt exist - create it
```
mkdir dataset
cd dataset
mkdir test
cd test
mkdir videos
cd videos
```
- Download the video the following folder and you can use the following command
```
curl -O https://raw.githubusercontent.com/TheXOrb/tttrace/main/input_videos/videoplayback%20(online-video-cutter.com)%20(1).mp4
```
- Rename the file
```
mv initial_file_name.mp4 test_6.mp4
```
- I have a problem as I dont have GPU from GEFORCE 
- Cuda is not enabled
- I need to change in the demo.py to
```
model.to("cpu")
```
- I need to change the file in the /src/models
```
nano models_utils.py
```
- And change this row to this
```
checkpoint = torch.load(pretrained_path, map_location=torch.device('cpu'), weights_only=False)
```
- I have changed a lot of different files just to get it working on my machine without CUDA - it works - but the results is poor
- I will try to run the main.py and see how that works with just the cpu
```
python main.py --video_path ../dataset/test/videos/test_1.mp4 --resume_path ../checkpoints/ttnet_3rd_phase/ttnet_3rd_phase_epoch_30.pth --no_cuda
```


## Progress Indication
- 💤 Not started  
- 🟡 In progress  
- ✅ Complete  

## Tutorials Overview
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 🟡 | HL1 | The vertical slice can start without any more services running |

---

## Tutorial: Setup TT Net
**Source:** [TTNet Real-time Analysis System for Table Tennis (Pytorch)](https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/)

### Setting up the Environment and Basic Object Detection (Table Tennis Players and Ball)
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 💤 | TL1-1 | Installing necessary libraries (Ultralytics) |
| ✅ | 💤 | TL1-2 | Understanding YOLO and its basic usage |
| ✅ | 💤 | TL1-3 | Running inference on a sample image and video |
| ✅ | 💤 | TL1-4 | Analyzing the output (bounding boxes, confidence scores, class names)  |
| ✅ | 💤 | TL1-5 | Adapting the model to table tennis |

---

## Instructions
### Step 1: Clone and Setup Virtual Environment
1. Clone the Python virtual environment repository:
   ```sh
   git clone https://github.com/maudzung/virtual_environment_python3.git
   ```
2. Follow the guide from the repository.
3. Simplified virtual environment setup:
   ```sh
   python3 -m venv ttnet_env
   source ttnet_env/bin/activate
   ```

### Step 2: Download TTNet Repository
```sh
 git clone https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch.git
```

### Step 3: Update Dependencies
1. Open `requirements.txt` and update the dependencies:
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
2. Install the updated requirements:
   ```sh
   pip install -U -r requirements.txt
   ```

### Step 4: Install Additional Libraries
```sh
sudo apt-get install libturbojpeg0
pip install PyTurboJPEG
```

### Step 5: Download Required Datasets
- [Dataset 1](https://drive.google.com/file/d/1y-qtMazXLqJ0UryNlICTgGIQ4z0ZhbMh/view?usp=sharing)  
- [Dataset 2](https://drive.google.com/file/d/14NEW-Rgz6XlVlcVOkWlL7Io6jeeS4SeU/view?usp=sharing)  
- [Dataset 3](https://drive.google.com/file/d/1tt2yO83nhbzSUUSZZTHCH6Z4szsdyoJS/view?usp=sharing)  

---

## Running the Demo
### Step 1: Modify `demo.sh` if Necessary
Example `demo.sh` content:
```sh
python demo.py \
  --working-dir '../' \
  --saved_fn 'demo' \
  --arch 'ttnet' \
  --gpu_idx 0 \
  --pretrained_path ../checkpoints/ttnet_3rd_phase/ttnet_3rd_phase_epoch_30.pth \
  --seg_thresh 0.5 \
  --event_thresh 0.5 \
  --thresh_ball_pos_mask 0.05 \
  --video_path ../dataset/test/videos/test_6.mp4 \
  --show_image \
  --save_demo_output
```

### Step 2: Navigate to the `/src/` Folder and Run the Demo
```sh
cd src
./demo.sh
```

---

## Additional Resources
- **Run File:** [demo.sh](https://github.com/maudzung/TTNet-Real-time-Analysis-System-for-Table-Tennis-Pytorch/blob/master/src/demo.sh)
- **Dataset Links:**
  - [Dataset 1](https://drive.google.com/file/d/1y-qtMazXLqJ0UryNlICTgGIQ4z0ZhbMh/view?usp=sharing)
  - [Dataset 2](https://drive.google.com/file/d/14NEW-Rgz6XlVlcVOkWlL7Io6jeeS4SeU/view?usp=sharing)
  - [Dataset 3](https://drive.google.com/file/d/1tt2yO83nhbzSUUSZZTHCH6Z4szsdyoJS/view?usp=sharing)
