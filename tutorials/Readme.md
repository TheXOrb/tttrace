# Tutorials directory
### Progress indication
💤 Not started  
🟡 In progress  
✅ Complete  

| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 🟡 | HL1 | The vertical slice can start without any more services running |

## Tutorial 1
### Setting up the Environment and Basic Object Detection (Table Tennis Players and Ball):
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 💤 | TL1-1 | Installing necessary libraries (Ultralytics) |
| ✅ | 💤 | TL1-2 | Understanding YOLO and its basic usage |
| ✅ | 💤 | TL1-3 | Running inference on a sample image and video |
| ✅ | 💤 | TL1-4 | Analyzing the output (bounding boxes, confidence scores, class names)  |
| ✅ | 💤 | TL1-5 | Adapting the model to table tennis |


## Tutorial 2
### Fine-Tuning the Ball Detection Model:
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| ✅ | 💤 | TL2-1 | Understanding the need for fine-tuning |
| ✅ | 💤 | TL2-2 | Finding or creating a table tennis ball dataset (Roboflow equivalent) |
| ✅ | 💤 | TL2-3 | Preparing the dataset for training |
| ✅ | 💤 | TL2-4 | Training a custom YOLO model (YOLOv5) on the ball dataset  |
| ✅ | 💤 | TL2-5 | Evaluating and comparing the fine-tuned model's performance |

## Tutorial 3
### Object Tracking and Player Identification:
| Writing | Video | Shortname | Requirement |
|---|---|---|---|
| 🟡 | 💤 | TL3-1 | Understanding the concept of object tracking |
| 🟡 | 💤 | TL3-2 | Using YOLO's tracking capabilities |
| 🟡 | 💤 | TL3-3 | Assigning unique IDs to players |
| 🟡 | 💤 | TL3-4 | Applying tracking to table tennis player movements  |
| 🟡 | 💤 | TL3-5 | Understanding the benifits of tracking for table tennis |

## Tutorial 4
### Court/Table Keypoint Detection (Using PyTorch):
- Understanding the importance of keypoint detection.
- Acquiring or creating a table keypoint dataset.
- Building a custom PyTorch dataset.
- Training a CNN (ResNet50) to detect keypoints.
- Understanding loss functions and optimizers.

## Tutorial 5
### Integrating Models and Calculating Metrics (Ball Speed, Player Movement):
- Combining the player detection, ball detection, and keypoint detection models.
- Calculating ball speed and player movement using detected data.
- Determining if the ball is "in" or "out" using keypoints.
- Calculating player coverage.

## Tutorial 6
### Advanced Analysis and Refinement:
- Analysing shot count, and shot speed.
- Refining the models for better accuracy.
- Visualizing the results.
- Exploring advanced analysis techniques (e.g., player positioning, shot patterns).

