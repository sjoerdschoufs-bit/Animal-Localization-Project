# Single-Object Localization with ResNet18 

This repository contains a Deep Learning project for localizing animals in images using a Convolutional Neural Network (CNN). The model is built with **PyTorch** and utilizes Transfer Learning to predict bounding boxes around animals.

This project was developed as part of the *Engineering with AI* minor (Deep Learning course) at TU Delft.

## Key Results
On the independent Test Set (15% of data), the model achieved:
* **Mean IoU:** 62.72%
* **Accuracy (IoU > 0.5):** 71.13%

*The model demonstrates strong localization capabilities, with many predictions achieving a high overlap (0.7-0.9 IoU) with the ground truth.*

## Methodology
### 1. Data Processing
* **Dataset:** 3,179 images across 5 classes (Dog, Cat, Bird, Cow, Horse).
* **Preprocessing:** Images resized to 256x256 and normalized using ImageNet statistics.
* **Augmentation:** Random Horizontal Flip and Color Jitter applied to the training set to prevent overfitting.

### 2. Model Architecture
* **Backbone:** **ResNet18** (Pretrained on ImageNet).
* **Head:** The classification layer was replaced with a regression head (Dropout + Linear Layer) to output 4 continuous coordinates (`xmin`, `ymin`, `xmax`, `ymax`).

### 3. Training Configuration
* **Loss Function:** `SmoothL1Loss` (chosen for robustness against outliers).
* **Optimizer:** `AdamW` (LR: 1e-3, Weight Decay: 1e-4).
* **Scheduler:** `ReduceLROnPlateau` to adjust the learning rate dynamically.

## Visuals
<img width="421" height="207" alt="Training and validation loss curves" src="https://github.com/user-attachments/assets/0e7aeb58-0fb0-4cf8-b52c-d4438672f682" />
<img width="209" height="207" alt="distribution of IoU" src="https://github.com/user-attachments/assets/872c8145-6cbf-4717-b50a-30768ff251c4" />
<img width="630" height="126" alt="inference samples" src="https://github.com/user-attachments/assets/78f1d3ea-9d8a-43bd-9ef1-bef77d88a7e1" />



## 🛠️ Getting Started

Follow these steps to set up and run the project locally.

### 1. Installation
Clone the repository and install the required dependencies:

```bash
git clone [https://github.com/JOUW_GEBRUIKERSNAAM/Animal-Localization-Project.git](https://github.com/JOUW_GEBRUIKERSNAAM/Animal-Localization-Project.git)
cd Animal-Localization-Project
pip install -r requirements.txt
