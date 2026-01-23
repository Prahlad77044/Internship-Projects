# Week 3: Deep Learning for Vision - From Scratch to Transfer Learning and Attribution

## Overview
This project focuses on building a robust deep learning pipeline for computer vision tasks using the CIFAR-10 dataset. The goal is to explore training engineering, augmentations, transfer learning, calibration, and attribution techniques. The project is structured as a 5-day plan, with each day focusing on specific tasks to ensure a comprehensive understanding of the concepts.

Additionally, a **side quest** was completed to develop a desktop app for labeling images, showcasing the ability to ship a functional prototype.

---

## Main Project: Deep Learning for Vision

### Dataset
- **CIFAR-10**: A dataset of 60,000 32x32 color images in 10 classes, with 6,000 images per class.
- **Source**: [CIFAR-10 Dataset](https://www.cs.toronto.edu/~kriz/cifar.html)

---

### 5-Day Plan

#### **Day 1: Data & Augmentations**
- Implemented `train`, `val`, and `test` dataloaders with baseline augmentations:
  - Random horizontal flip
  - Random crop
  - Normalization
- Added advanced augmentations:
  - **RandAugment**
  - **MixUp**
  - **CutMix**
- Conducted ablation studies to analyze the effects of these augmentations on model performance.

#### **Day 2: From-Scratch CNN**
- Designed and trained a small CNN from scratch.
- Used **cosine annealing** learning rate scheduler for smooth convergence.
- Enabled **AMP (Automatic Mixed Precision)** for faster training and reduced memory usage.

#### **Day 3: Transfer Learning**
- Fine-tuned a **ResNet-18** model on CIFAR-10.
- Explored different fine-tuning strategies:
  - Fully frozen backbone
  - Partial unfreeze (last layer, Layer4 + FC)
  - Fully unfrozen model
- Logged convergence metrics and wall-clock time for each strategy.

#### **Day 4: Diagnostics & Robustness**
- Performed misclassification analysis and reviewed Grad-CAM visualizations for 20 examples.
- Conducted adversarial noise sanity checks using FGSM (Fast Gradient Sign Method).
- Computed calibration metrics:
  - **Expected Calibration Error (ECE)**
  - Reliability diagrams to assess model confidence.

#### **Day 5: Reproducible Artifacts**
- Saved the best model weights and created an `inference.py` script for predictions.
- Documented the model's intended use, failure modes, and robustness in a **model card**.
- Delivered:
  - Training curves
  - Confusion matrices
  - Grad-CAM visualizations
  - Calibrated inference script
  - Model card

---

### Deliverables
1. **Baseline & Transfer Learning Notebooks**:
   - [Day 1-2 Notebook](week_3/notebooks/day1,2.ipynb)
   - [Day 3-5 Notebook](week_3/notebooks/day3,4,5.ipynb)
2. **Training Curves**:
   - Validation loss and accuracy comparisons across models.
3. **Confusion Matrices**:
   - Visualized for each model to analyze class-wise performance.
4. **Grad-CAM Gallery**:
   - Heatmaps for correctly classified and misclassified examples.
5. **Calibrated Inference Script**:
   - [API Script](week_3/app/api.py)
   - [Streamlit App](week_3/app/streamlit_cifar10.py)
6. **Model Card**:
   - [Model Card](week_3/model_card.md)

---

## Side Quest: Desktop Image Labeler

### Purpose
Developed a simple desktop app to label images into two classes, demonstrating the ability to ship a functional prototype.

### Features
- **Open Folder**: Select a folder containing images.
- **Label Images**: Assign labels using two buttons or keyboard shortcuts:
  - `A` for Class 0
  - `B` for Class 1
- **Autosave**: Labels are saved to `labels.csv` in real-time.
- **Export Splits**: Automatically generate `train`, `val`, and `test` splits with configurable ratios.

### Deliverables
1. **App Script**: [Image Labeler](week_3/side_quest/image_labeler.py)
2. **Labels File**: `labels.csv` (contains filename and label).
3. **Splits File**: `splits.csv` (contains filename and split).
4. **Demo Recording**: A 60-second screen recording showcasing the app's functionality.

### Usage
1. Run the app:
   ```bash
   python image_labeler.py
   ```
2. Label images using the GUI or keyboard shortcuts.
3. Export splits for training, validation, and testing.

---

## Assessment Criteria (100 pts)
1. **Training Engineering & Stability (35 pts)**:
   - Proper use of augmentations, learning rate schedules, and mixed precision.
2. **Transfer Learning & Regularization (25 pts)**:
   - Effective fine-tuning strategies and regularization techniques.
3. **Attribution & Error Analysis (20 pts)**:
   - Grad-CAM visualizations and adversarial robustness checks.
4. **Reproducibility & Documentation (20 pts)**:
   - Clear documentation, saved artifacts, and inference scripts.

### Stretch Goals
- Ablation studies: Cutout vs MixUp vs CutMix.
- Label smoothing.
- Temperature scaling for calibration.

---

## How to Run
1. Clone the repository and navigate to the project directory.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the notebooks for training and analysis.
4. Use the `api.py` or `streamlit_cifar10.py` for inference.

---

## Acknowledgments
- **Dataset**: CIFAR-10 by the University of Toronto.
- **Frameworks**: PyTorch, FastAPI, Streamlit, Tkinter.
