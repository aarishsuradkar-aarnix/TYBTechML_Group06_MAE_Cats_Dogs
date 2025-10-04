# Masked Autoencoder (MAE) Reproduction

## Project Overview
This repository contains the **reproduction of the Masked Autoencoder (MAE)** for image reconstruction. The original research paper introduces a self-supervised learning method where a large portion of input image patches is masked and the model learns to reconstruct the original image from the visible patches.

**Original Paper:** [Masked Autoencoders Are Scalable Vision Learners (CVPR 2022)](https://openaccess.thecvf.com/content/CVPR2022/html/He_Masked_Autoencoders_Are_Scalable_Vision_Learners_CVPR_2022_paper.html)

---

## Problem Statement
The goal is to **reproduce the MAE model** as described in the original paper and validate its performance on **image reconstruction tasks**. The model is evaluated by how accurately it can reconstruct images from masked patches.

---

## Datasets
### Original Dataset
- The original paper used **ImageNet** for training MAEs.
- High-resolution images of diverse classes for generalizable feature learning.

### Reproduction Dataset
- For this reproduction, a smaller dataset of **Cats & Dogs** images is used.
- Dataset contains **two classes (cats and dogs)** with ~2,500 images per class (for faster training and demonstration).

---

## Methodology / Implementation Steps
1. **Data Preprocessing**
   - Resize images to `48x48`.
   - Random cropping, horizontal flipping for data augmentation.
   - Split into training and validation sets (80:20).

2. **Patch Extraction**
   - Images are divided into non-overlapping patches of size `6x6`.
   - Each patch is flattened and fed into the encoder.

3. **MAE Architecture**
   - **Encoder:** 3-layer MLP (linear + ReLU) to encode visible patches.
   - **Decoder:** Lightweight MLP to reconstruct original patches.
   - Mask **75% of patches** randomly during training.

4. **Training**
   - Loss function: Mean Squared Error (MSE) between original and reconstructed images.
   - Optimizer: AdamW with learning rate `0.005`.
   - Trained for **50 epochs** on GPU (if available).

5. **Evaluation**
   - Reconstruct images from the validation set.
   - Visual comparison of **original vs reconstructed images**.

---

## Results
- The MAE successfully learns to reconstruct masked images with reasonable quality.
- Reconstruction quality is lower than the original ImageNet results (due to smaller dataset and lower resolution), but the pipeline reproduces the methodology accurately.

**Example Visualization:**
