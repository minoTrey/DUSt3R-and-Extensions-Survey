# MEt3R: Measuring Multi-View Consistency in Generated Images

## Overview

MEt3R (Measuring Multi-View Consistency in Generated Images) is a metric designed to evaluate the geometric consistency of multi-view generated images. The paper was accepted at CVPR 2025 and introduces a novel approach to assess the quality of multi-view image generation models.

## Paper Information

- **Title**: MEt3R: Measuring Multi-View Consistency in Generated Images
- **Conference**: CVPR 2025
- **arXiv**: [2501.06336](https://arxiv.org/abs/2501.06336)
- **Project Page**: [https://geometric-rl.mpi-inf.mpg.de/met3r/](https://geometric-rl.mpi-inf.mpg.de/met3r/)
- **GitHub**: [https://github.com/mohammadasim98/met3r](https://github.com/mohammadasim98/met3r)

## Authors

- Mohammad Asim (Max Planck Institute for Informatics, Saarland Informatics Campus, Germany)
- Christopher Wewer (Max Planck Institute for Informatics, Saarland Informatics Campus, Germany)  
- Thomas Wimmer (Max Planck Institute for Informatics, Saarland Informatics Campus, Germany; ETH Zurich)
- Bernt Schiele (Max Planck Institute for Informatics, Saarland Informatics Campus, Germany)
- Jan Eric Lenssen (Max Planck Institute for Informatics, Saarland Informatics Campus, Germany)

## Key Contributions

1. **Novel Evaluation Metric**: MEt3R provides a pose-free metric for evaluating multi-view consistency in generated images, addressing a critical gap in assessing generative models for multi-view synthesis.

2. **DUSt3R Integration**: The method leverages DUSt3R to obtain dense 3D reconstructions from image pairs in a feed-forward manner, enabling geometry-aware consistency evaluation.

3. **View-Invariant Features**: Uses DINO + FeatUp to extract features that are robust to view-dependent effects like lighting changes.

4. **Comprehensive Evaluation**: Evaluates consistency across various state-of-the-art methods for novel view and video generation.

## Technical Approach

### Core Methodology

1. **3D Reconstruction**: Uses DUSt3R to obtain dense 3D point maps from image pairs
2. **Cross-View Warping**: Warps image contents from one view into another using the 3D geometry
3. **Feature Extraction**: Extracts features using DINO or other backbones with FeatUp for upsampling
4. **Similarity Computation**: Compares feature maps to obtain a consistency score invariant to view-dependent effects

### Key Features

- **Pose-Free**: Does not require camera poses
- **Resolution Robust**: Works with varying image resolutions
- **Plug-n-Play**: Easy integration into existing pipelines
- **Content Independent**: Works across different image content and quality levels

## Implementation Details

### Requirements

- Python >= 3.6
- PyTorch >= 2.1.0
- CUDA >= 11.3
- PyTorch3D >= 0.7.5
- FeatUp >= 0.1.1

### Installation

```bash
pip install git+https://github.com/mohammadasim98/met3r
```

### Usage Example

```python
from met3r import MEt3R
import torch

# Initialize the metric
metric = MEt3R(
    img_size=256,
    backbone="mast3r",          # Options: "mast3r", "dust3r", "raft"
    feature_backbone="dino16"    # Options: "dino16", "dinov2", "maskclip", etc.
).cuda()

# Prepare input images (batch_size, num_views, channels, height, width)
inputs = torch.randn((10, 2, 3, 256, 256)).cuda()
inputs = inputs.clip(-1, 1)

# Compute consistency score
score, *_ = metric(images=inputs)
print(f"Consistency score: {score.mean().item()}")  # Expected: 0.25-0.35
```

### Configuration Options

- **Backbones**: 
  - "mast3r" (default)
  - "dust3r"
  - "raft"

- **Feature Backbones**:
  - "dino16" (default)
  - "dinov2"
  - "maskclip"
  - Other supported options

- **Upsampling Methods**:
  - "featup" (default)
  - "nearest"
  - "bilinear"
  - "bicubic"

- **Distance Metrics**:
  - "cosine" (default)
  - "lpips"
  - "rmse"
  - "psnr"
  - Other supported metrics

## Evaluated Methods

MEt3R was used to evaluate consistency across two categories:

### Multi-View Generation
- GenWarp
- PhotoNVS
- MV-LDM
- DFM

### Video Generation
- I2VGen-XL
- Ruyi-Mini-7B
- SVD

## Significance

MEt3R addresses a crucial challenge in evaluating multi-view generative models. Traditional reconstruction metrics are not suitable for generated outputs due to the stochastic nature of generative modeling. MEt3R provides a metric that is:
- Independent of the sampling procedure
- Robust to view-dependent effects
- Easy to integrate into existing evaluation pipelines

This makes it an essential tool for researchers developing and evaluating multi-view generation models, particularly as the field advances with large-scale generative models for 3D inference from sparse observations.

## Related Work

MEt3R builds upon the DUSt3R foundation for 3D reconstruction and combines it with modern feature extraction methods (DINO, FeatUp) to create a robust evaluation metric for the growing field of multi-view image generation.