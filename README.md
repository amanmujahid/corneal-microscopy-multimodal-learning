# Multimodal Deep Learning for Corneal Microscopy Analysis

This project explores a multimodal deep learning approach for analyzing confocal microscopy mosaic images in the context of diabetes-related classification. The pipeline combines image-based features with clinical data and evaluates several transformer-based architectures.

---

## Overview

Confocal microscopy images come as large, high-resolution mosaics, which makes them difficult to use directly for model training.  
To handle this, the pipeline focuses on breaking the images into smaller regions and selecting the most informative ones before training.

The workflow includes:
- Contrast enhancement using CLAHE
- Splitting mosaics into overlapping patches
- Selecting informative regions using gradient-based scoring
- Combining image patches with clinical features
- Training and evaluating transformer-based models

---

## Methodology

### Image Preprocessing
- Applied percentile-based normalization to standardize intensity values
- Used CLAHE to improve local contrast
- Converted each mosaic into overlapping 224×224 patches

### Patch Selection
- Removed low-information patches using variance thresholding
- Ranked patches based on Sobel gradient magnitude
- Selected the top K patches (K = 64) per image

### Multimodal Learning
- Combined image patches with clinical features such as BMI and blood pressure
- This allows the model to use both visual and non-visual signals

### Model Architectures
- Swin Transformer (Tiny)
- DeiT (Data-efficient Vision Transformer)
- MobileViT (XS)

All models were implemented and trained in PyTorch.

---

## Evaluation

Models were evaluated using:
- ROC-AUC  
- F1 Score  
- Precision-Recall AUC  

To avoid data leakage, splitting was done at the subject level rather than the image level.

---

## Tech Stack

- Python  
- PyTorch  
- NumPy  
- Pandas  
- OpenCV  
