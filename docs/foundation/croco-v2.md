# CroCo v2: Improved Cross-view Completion Pre-training for Stereo Matching and Optical Flow (2023)

## 📋 Overview
- **Authors**: Philippe Weinzaepfel, Thomas Lucas, Vincent Leroy, Yohann Cabon, Vaibhav Arora, Romain Brégier, Gabriela Csurka, Leonid Antsfeld, Boris Chidlovskii, Jérôme Revaud
- **Institution**: NAVER LABS Europe
- **Venue**: ICCV 2023 (arXiv:2211.10408v3)
- **Links**: [Paper](https://arxiv.org/abs/2211.10408) | [Code](https://github.com/naver/croco) | [Project Page](https://croco.europe.naverlabs.com/)
- **TL;DR**: Enhanced CroCo with real-world data, relative position embeddings, and larger models, achieving SOTA on stereo and optical flow without task-specific components.

## 🎯 Key Contributions

1. **Real-world Data Collection**: Introduces methodology to collect 5.3M real image pairs from ARKitScenes, MegaDepth, 3DStreetView, and IndoorVL
2. **Relative Position Embeddings**: Replaces absolute cosine embeddings with RoPE for better resolution flexibility
3. **Model Scaling**: Upgrades to ViT-Large encoder and Base decoder for improved capacity
4. **SOTA Performance**: First transformer-based method to achieve state-of-the-art on stereo and flow without correlation volumes
5. **Unified Architecture**: Single model excels at both stereo matching and optical flow

## 🔧 Technical Details

### Architecture Improvements
- **Input**: Image pairs with varying resolutions
- **Output**: Dense predictions (disparity/flow) via DPT head
- **Key Changes from v1**:
  - Encoder: ViT-Base → ViT-Large (24 blocks, 1024 dims, 16 heads)
  - Decoder: Small → Base (12 blocks, 768 dims, 12 heads)
  - Positional: Absolute cosine → RoPE (relative embeddings)
  - Head: Simple projection → DPT for dense predictions

### Training Data Collection
**Real-world datasets (5.3M pairs)**:
| Dataset | Pairs | Domain | Selection Method |
|---------|--------|---------|------------------|
| ARKitScenes | 1.07M | Indoor | Relative pose + co-visibility |
| MegaDepth | 2.01M | Landmarks | SfM reconstruction |
| 3DStreetView | 0.66M | Street views | GPS + visual overlap |
| IndoorVL | 1.59M | Indoor public | Frame sampling |

**Total**: 7.1M pairs (5.3M real + 1.82M synthetic)

### Training Strategy
- **Pre-training**: 100 epochs on 7.1M pairs
- **Masking**: 90% of first image patches
- **Batch size**: 512 (64 per GPU × 8 GPUs)
- **Learning rate**: 3×10⁻⁴ with cosine decay
- **Augmentations**: Random crops, color jittering

## 📊 Results

### Stereo Matching Performance

| Dataset | Metric | CroCo v1 | CroCo v2 | Previous SOTA |
|---------|--------|----------|----------|---------------|
| Middlebury | bad@1.0 ↓ | 5.0 | **1.82** | 2.31 (RAFT) |
| ETH3D | bad@1.0 ↓ | - | **0.38** | 0.47 (CRAFT) |
| KITTI 2012 | bad@3.0 ↓ | - | **1.38** | 1.27 (CRAFT) |
| SceneFlow | EPE ↓ | - | **5.3** | 6.3 (GMFlow) |

### Optical Flow Performance

| Dataset | Split | CroCo v2 | Previous SOTA |
|---------|-------|----------|---------------|
| Sintel | Clean | **1.25** | 1.43 (FlowFormer) |
| Sintel | Final | **2.26** | 2.51 (GMFlow) |
| KITTI 2015 | Fl-all | **5.8%** | 6.4% (CRAFT) |

### Key Achievement
First pure transformer method to achieve SOTA without:
- Correlation volumes
- Iterative refinement
- Multi-scale processing
- Task-specific architectures

## 💡 Insights & Impact

### Advantages over CroCo v1
1. **Generalization**: Real-world training data dramatically improves performance
2. **Flexibility**: RoPE enables handling arbitrary resolutions and aspect ratios
3. **Scalability**: Larger models yield substantial performance gains
4. **Simplicity**: Achieves SOTA without complex task-specific components

### Limitations
1. **Data Requirements**: Needs geometric metadata (poses/depth) for pair selection
2. **Computational Cost**: Larger transformer models increase inference time
3. **Training Resources**: Requires significant GPU resources for pre-training

### Impact on DUSt3R Development
- **Architectural Foundation**: DUSt3R adopts the scaled encoder-decoder design
- **Data Strategy**: Validates using diverse real-world data for 3D tasks
- **Unified Approach**: Reinforces viability of general architectures for geometric vision
- **Pre-training Benefits**: Shows strong representations transfer to various 3D tasks

## 🔗 Related Work

### Evolution Path
- **CroCo** (NeurIPS 2022): Original cross-view completion
- **CroCo v2** (ICCV 2023): This work
- **DUSt3R** (CVPR 2024): Extends to uncalibrated 3D reconstruction
- **MASt3R** (ECCV 2024): Further unification of 3D tasks

### Contemporary Methods
- **RAFT-Stereo**: Correlation-based stereo matching
- **GMFlow**: Global matching for optical flow
- **CRAFT**: Cross-attention for stereo and flow

## 📚 Key Takeaways

CroCo v2 significantly advances the cross-view completion paradigm by:
1. Demonstrating that real-world data collection at scale is crucial
2. Proving transformers can match/exceed specialized architectures
3. Showing relative position embeddings improve geometric understanding
4. Validating that unified models can excel at multiple dense prediction tasks

The transition from synthetic-only (v1) to real-world training (v2) and the architectural improvements directly influenced DUSt3R's design, particularly in handling uncalibrated images and producing dense 3D predictions.