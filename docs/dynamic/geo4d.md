# Geo4D: Leveraging Video Generators for Geometric 4D Scene Reconstruction

## Overview

**Paper Title**: Geo4D: Leveraging Video Generators for Geometric 4D Scene Reconstruction  
**Conference**: ICCV 2025  
**arXiv**: [2504.07961](https://arxiv.org/abs/2504.07961)  
**Project Page**: [https://geo4d.github.io/](https://geo4d.github.io/)  
**GitHub**: [https://github.com/jzr99/Geo4D](https://github.com/jzr99/Geo4D)

## Authors and Affiliations

- **Zeren Jiang** - Visual Geometry Group (VGG), University of Oxford
  - First-year DPhil student supervised by Prof. Andrea Vedaldi and Dr. Iro Laina
- **Chuanxia Zheng** - Visual Geometry Group (VGG), University of Oxford
  - Marie Skłodowska-Curie Actions (MSCA) Fellow working with Prof. Andrea Vedaldi
- **Iro Laina** - Visual Geometry Group (VGG), University of Oxford
- **Diane Larlus** - Naver Labs Europe
- **Andrea Vedaldi** - Visual Geometry Group (VGG), University of Oxford

## Key Contributions

Geo4D introduces a novel approach to 4D scene reconstruction that repurposes video diffusion models for dynamic scene understanding. The key innovation is leveraging the strong dynamic priors captured by video generation models to achieve robust geometric reconstruction.

### Main Features

1. **Video Diffusion Foundation**: Built on top of DynamiCrafter, a foundation video diffusion model
2. **Multi-Modal Predictions**: Predicts complementary geometric modalities:
   - Point maps (viewpoint-invariant 3D coordinates)
   - Depth maps
   - Ray maps
3. **Zero-Shot Generalization**: Trained only on synthetic data but generalizes well to real data
4. **Multi-Modal Alignment**: Novel algorithm to align and fuse different geometric modalities
5. **Sliding Window Processing**: Handles long videos through multiple sliding windows

## Technical Approach

### Foundation Model
Geo4D builds upon DynamiCrafter, a latent diffusion model that uses a variational autoencoder (VAE) to reduce computational complexity by working in a compressed latent space.

### Point Map Representation
Following DUSt3R's approach, Geo4D adopts viewpoint-invariant point maps where each pixel is associated with 3D coordinates relative to the first frame. This representation:
- Implicitly encodes camera motion and intrinsics
- Can be easily predicted by neural networks
- Extends DUSt3R's static representation to dynamic scenes

### Multi-Modal Geometric Prediction
The method predicts three complementary modalities:
1. **Point Maps**: 3D coordinates for each pixel
2. **Depth Maps**: Traditional depth information
3. **Ray Maps**: Ray direction information

### Fusion and Alignment
A novel multi-modal alignment algorithm combines:
- Different geometric modalities
- Multiple sliding windows across time
- Robust fusion for accurate 4D reconstruction

## Relationship to DUSt3R

Geo4D directly builds upon DUSt3R's innovations while addressing its key limitation:

### DUSt3R Foundation
- Introduced viewpoint-invariant point map representation
- Enabled holistic end-to-end 3D reconstruction
- Eliminated need for camera poses and intrinsics
- **Limitation**: Focuses only on static scenes

### Geo4D Extensions
- Extends point maps to handle dynamic scenes
- Incorporates temporal understanding through video diffusion
- Adds complementary geometric modalities
- Achieves state-of-the-art dynamic scene reconstruction

## Performance

### Benchmarks
Extensive experiments show Geo4D significantly outperforms:
- State-of-the-art video depth estimation methods
- MonST3R (designed for dynamic scenes)
- DepthCrafter (based on same DynamiCrafter model)
  - 17.3% improvement in Abs Rel on KITTI dataset

### Key Advantages
- Handles extreme object and camera motion
- Robust long video reconstruction
- Zero-shot transfer from synthetic to real data
- No need for per-video bundle adjustment

## Implementation Details

### Training
- Trained exclusively on synthetic data
- Leverages video diffusion model priors
- Achieves strong zero-shot generalization

### Inference
- Feed-forward framework (no optimization loops)
- Multi-window processing for long videos
- Real-time applicability potential

## Related Work

### Dynamic Extensions of DUSt3R
- **MonST3R**: Extends DUSt3R for dynamic scenes
- **Easi3R**: Training-free 4D reconstruction using attention adaptation
- **Geo4D**: Most advanced extension using video diffusion models

### Video Depth Estimation
Geo4D outperforms traditional video depth estimation by incorporating:
- Multi-modal geometric understanding
- Video generation model priors
- Robust temporal alignment

## Applications

Geo4D enables:
- Monocular video to 4D reconstruction
- Dynamic scene understanding
- Robust geometry estimation in challenging scenarios
- Zero-shot application to diverse real-world videos

## Code and Resources

- **GitHub Repository**: [https://github.com/jzr99/Geo4D](https://github.com/jzr99/Geo4D)
- **Project Website**: [https://geo4d.github.io/](https://geo4d.github.io/)
- **Paper**: [arXiv:2504.07961](https://arxiv.org/abs/2504.07961)
- **Acknowledgments**: Uses code from DUSt3R

## Summary

Geo4D represents a significant advancement in dynamic 3D reconstruction by successfully repurposing video generation models for geometric understanding. It extends DUSt3R's static reconstruction capabilities to handle complex dynamic scenes, achieving state-of-the-art performance through innovative multi-modal fusion and video diffusion priors.