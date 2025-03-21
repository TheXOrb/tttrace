# Taking on from where people have left and continue to contribute
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
pip3 install -U -r requirement.txt
```
- Install PyTurboJEPG also if it´s not already installed
```
pip3 install PyTurboJPEG
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
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```
- Think we got the demo running now
- Will try to use the pretrained models
- 


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
