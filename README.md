# TensorFlow - 3D GAN for Volumetric data synthesis
Python 3.12, TensorFlow 2.16.2, 
Final Major Project (FMP) – Undergraduate-Bournemouth University, 2025

Link to the breakdown and results video - 
https://www.youtube.com/watch?v=fsqkFNdqEkw

This project implements a 3D Generative Adversarial Network (GAN) to synthesise a volumetric computed-tomography (CT) scans from 2D X-ray Projections. Aim to explore deep-learning methods for reconstructing 3D medical imagery, which has potential implications in medical imaging.

<img width="688" alt="Screenshot 2025-05-15 at 18 57 32" src="https://github.com/user-attachments/assets/ce95744b-f0b7-4916-8842-3ac0d7cc10fb" />

## Overview 
- Input: Two 2D X-ray projections (posterior-anterior, lateral views)
- Ouput: A synthesised 3D volumetric representation
- Objective: Providing a cheap, less-ionising alternative to CT scanning

## Model Features
- Dynamic loading and memory-efficient batching of large nii.gz CT scans
- Preprocessing and normalising of 3D volumes
- Projection for synthetic X-ray generation
- Loss components - adversarial, reconstruction & projection-based

## Model Architecture 
The model is based on a dual-path encoder-decoder GAN framework with 3D convolutional layers. Key features include:
- Feature fusion layers to integrate multi-scale information
- Skip connections to preserve spatial consistency
- PatchGAN discriminator adapted for volumetric data
  
<img width="738" alt="Screenshot 2025-05-15 at 18 44 47" src="https://github.com/user-attachments/assets/97eddc5e-887f-4806-9005-94d07a253ea2" />

## Techniques and Features 
- 3D Convolutions for volumetric learning
- Loss Functions: Combination of L1 loss and adversarial loss to balance realism and accuracy
- Data Normalisation and Augmentation to mitigate overfitting
- Custom training loop for improved control over generator-discriminator balance

## Dataset
Link to the dataset I used for this project-
(https://faspex.cancerimagingarchive.net/aspera/faspex/public/package?context=eyJyZXNvdXJjZSI6InBhY2thZ2VzIiwidHlwZSI6ImV4dGVybmFsX2Rvd25sb2FkX3BhY2thZ2UiLCJpZCI6IjU5MiIsInBhc3Njb2RlIjoiMDNkOWZmMzE2ZmE3NmQ3YzlmZmEyZWFhZDg2ZjkxNTJjZTFhY2FhNSIsInBhY2thZ2VfaWQiOiI1OTIiLCJlbWFpbCI6ImhlbHBAY2FuY2VyaW1hZ2luZ2FyY2hpdmUubmV0In0=&redirected=true&authenticated=true) 

## Future Work 
While the results demonstrate promising progress, several limitations provide avenues for future enhancement.

Hardware Constraints-
The model was trained on a local machine with an Apple M2 chip and 8GB RAM, which significantly constrained batch sizes, input resolution, and training time. Future iterations could benefit from training on dedicated GPUs or cloud-based platforms (e.g., Google Cloud, AWS) to enable higher-resolution volumes, deeper architectures, and more robust training cycles.

Dataset Limitations-
The training dataset was limited in both size and diversity, which may have impacted the model’s generalisation ability across varied patient anatomies and imaging conditions. Incorporating larger, publicly available datasets (e.g., LIDC-IDRI, BraTS) and applying data augmentation or synthetic data generation could improve robustness and model fidelity.

Architectural Enhancements-
In this project, I explored many different architectures but due to hardware constraints a lot were not feasible at the time. However, for future development I can consider:
Adding attention mechanisms for enhanced feature localisation
Exploring transformer-based models to capture global 3D context
