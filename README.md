# Weld Length Prediction using YOLOv5 and Mask R-CNN

This repository contains implementations for predicting weld lengths using **YOLOv5** and **Mask R-CNN** models. The project involves image processing and deep learning to detect and measure welds in images with a scale reference.

---

## Table of Contents
- [Project Overview](#project-overview)
- [Dataset Preparation](#dataset-preparation)
- [Approach](#approach)
  - [YOLOv5-based Weld Detection](#yolov5-based-weld-detection)
  - [Mask R-CNN for Weld Segmentation](#mask-r-cnn-for-weld-segmentation)
- [Installation and Setup](#installation-and-setup)
- [Usage](#usage)
- [Results](#results)
- [Contributions](#contributions)
- [License](#license)

---

## Project Overview

### Goal
To detect welds and accurately predict their lengths in images using:
1. **YOLOv5** for object detection (welds and scale).
2. **Mask R-CNN** for segmentation-based measurements.

The predicted weld length is reported in centimeters, leveraging a 31.5 cm reference scale present in the images.

### Motivation
Manual weld length measurements are prone to human error and inefficiencies. Automating this process using computer vision can help improve accuracy and save time, especially in industrial applications.

---

## Dataset Preparation

The dataset consists of images containing welds and a **31.5 cm reference scale**:
1. Images are annotated for both **YOLOv5** (bounding boxes) and **Mask R-CNN** (segmentation masks).
2. Classes include:
   - **Welds**
   - **Scale**
3. Tools used for annotation:
   - **Label Studio**
   - **labelImg** (for YOLOv5 annotations)

### Preprocessing Steps:
1. Crop the region of interest (ROI) to focus on weld and scale.
2. Apply preprocessing techniques to clean the images before training.

---

## Approach

### 1. YOLOv5-based Weld Detection
- **YOLOv5** is used to:
   - Detect welds and scale in the images.
   - Output bounding boxes for both weld and scale classes.
- Using the scale as a reference, the weld length is calculated in centimeters.

### 2. Mask R-CNN for Weld Segmentation
- **Mask R-CNN** is implemented for:
   - Generating pixel-wise segmentation masks for welds and the reference scale.
   - Calculating weld length based on the segmented area.

---

## Installation and Setup

### Prerequisites:
- Python 3.8+
- PyTorch
- OpenCV
- YOLOv5 dependencies
- Mask R-CNN libraries (Detectron2 or equivalent)

### Steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/weld-length-prediction.git
   cd weld-length-prediction
