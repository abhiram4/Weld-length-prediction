# Weld-length-prediction
Weld Length Prediction using Yolov5 and Mask R-CNN

This repository contains implementations for predicting weld lengths using YOLOv5 and Mask R-CNN models. The project involves image processing and deep learning to detect and measure welds in images with a scale reference.

Table of Contents

Project Overview

Dataset Preparation

Approach

YOLOv5-based Weld Detection

Mask R-CNN for Weld Segmentation

Installation and Setup

Usage

Results

Contributions

License

Project Overview

Goal

To detect welds and accurately predict their lengths in images using:

YOLOv5 for object detection (welds and scale).

Mask R-CNN for segmentation-based measurements.

The predicted weld length is reported in centimeters, leveraging a 31.5 cm reference scale present in the images.

Motivation

Manual weld length measurements are prone to human error and inefficiencies. Automating this process using computer vision can help improve accuracy and save time, especially in industrial applications.

Dataset Preparation

The dataset consists of images containing welds and a 31.5 cm reference scale:

Images are annotated for both YOLOv5 (bounding boxes) and Mask R-CNN (segmentation masks).

Classes include:

Welds

Scale

Tools used for annotation:

Label Studio

labelImg (for YOLOv5 annotations)

Preprocessing Steps:

Crop the region of interest (ROI) to focus on weld and scale.

Apply preprocessing techniques to clean the images before training.

Approach

1. YOLOv5-based Weld Detection

YOLOv5 is used to:

Detect welds and scale in the images.

Output bounding boxes for both weld and scale classes.

Using the scale as a reference, the weld length is calculated in centimeters.

2. Mask R-CNN for Weld Segmentation

Mask R-CNN is implemented for:

Generating pixel-wise segmentation masks for welds and the reference scale.

Calculating weld length based on the segmented area.

Installation and Setup

Prerequisites:

Python 3.8+

PyTorch

OpenCV

YOLOv5 dependencies

Mask R-CNN libraries (Detectron2 or equivalent)

Steps:

Clone the repository:

git clone https://github.com/yourusername/weld-length-prediction.git
cd weld-length-prediction

Set up the virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`

Install dependencies:

pip install -r requirements.txt

Prepare the dataset:

Place YOLOv5 annotations in data/yolo/.

Place Mask R-CNN masks in data/maskrcnn/.

Usage

YOLOv5

Train the YOLOv5 model:

python train.py --data data/weld_data.yaml --weights yolov5s.pt --epochs 50

Run inference on test images:

python detect.py --weights runs/train/exp/weights/best.pt --source data/test_images/

Mask R-CNN

Train the Mask R-CNN model:

python train_mask_rcnn.py --data data/maskrcnn/

Run inference for segmentation:

python predict_mask_rcnn.py --model-path models/mask_rcnn.pth --image-path data/test_images/

Results

Model

Metric

Accuracy

YOLOv5

Detection mAP

92%

Mask R-CNN

Segmentation mAP

88%

Weld length prediction errors were found to be less than 2% when using the scale reference.

Contributions

Abhiram Sugesh: Project implementation, data preparation, and model development.
