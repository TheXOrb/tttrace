# TTTrace - Table Tennis Trace: Video Analysis for Performance Metrics
Welcome to the TTTrace repository. TTTrace, short for Table Tennis Trace, is a project dedicated to analyzing table tennis player performance through video analysis. We're developing a system that uses computer vision and machine learning to trace and extract key performance metrics, such as player speed, ball shot speed, and shot counts.

This is a hands-on project aimed at exploring and advancing sports analytics in table tennis. I initiated TTTrace to deepen my understanding of machine learning and computer vision, and I welcome contributions from anyone interested in expanding its capabilities. We've integrated YOLO for robust object detection, and I'm developing custom Convolutional Neural Networks (CNNs) for precise table keypoint extraction. If you're interested in contributing, please feel free to reach out!

One challenge we have already stumbled across is detecting the ball due to the high speed and also the small size. There are recommended way to use approches like sequential model. To predict the ball path or getting higher fps.

## Objective 
Detect and track players and table tennis balls in a video.

## Software that maybe needed also 
- LabelMe - https://github.com/wkentaro/labelme
- OpenCV - https://github.com/opencv/opencv

## Features
- Detect table tennis table key points
- Measure player positions, distances, and speed
- Determine if the ball is in or out
- Count player shots and measure shot speed
- Train two convolutional neural networks (YOLO and custom CNN)

## Tutorials
- In the folder /tutorial/ there are walk trough to do the same things that we have done in the repo


# CC Attribution 4.0 International
Shield: [![CC BY 4.0][cc-by-shield]][cc-by]

This work is licensed under a
[Creative Commons Attribution 4.0 International License][cc-by].

[![CC BY 4.0][cc-by-image]][cc-by]

[cc-by]: http://creativecommons.org/licenses/by/4.0/
[cc-by-image]: https://i.creativecommons.org/l/by/4.0/88x31.png
[cc-by-shield]: https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg
