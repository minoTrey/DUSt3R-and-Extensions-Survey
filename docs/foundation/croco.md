# CroCo: Self-Supervised Pre-training for 3D Vision Tasks by Cross-View Completion (NeurIPS 2022)

![CroCo Overview](https://ar5iv.labs.arxiv.org/html/2210.10716/assets/x1.png)
*Figure 1: CroCo cross-view completion task*

![CroCo Architecture](https://ar5iv.labs.arxiv.org/html/2210.10716/assets/x2.png)
*Figure 2: CroCo reconstruction examples*

![CroCo Architecture](https://ar5iv.labs.arxiv.org/html/2210.10716/assets/x3.png)
*Figure 3: CroCo architecture*

## 📋 Overview
- **Authors**: Philippe Weinzaepfel, Vincent Leroy, Thomas Lucas, Romain Brégier, Yohann Cabon, Vaibhav Arora, Leonid Antsfeld, Boris Chidlovskii, Gabriela Csurka, Jérôme Revaud
- **Institution**: NAVER LABS Europe
- **Venue**: NeurIPS 2022
- **Links**: [Paper](https://arxiv.org/abs/2210.10716) | [Code](https://github.com/naver/croco) | [Project Page](https://croco.europe.naverlabs.com/)
- **TL;DR**: Self-supervised pre-training method that learns 3D-aware representations by reconstructing masked image regions using cross-view information.

## 🎯 Key Contributions

1. **Cross-View Completion Pretext Task**: Novel self-supervised approach that masks one image and reconstructs it using both visible parts and a second view
2. **3D Vision-Oriented Pre-training**: Unlike semantic-focused methods (MAE), specifically designed for geometric understanding
3. **Unified Architecture**: Single model handles both monocular (encoder only) and binocular tasks (full encoder-decoder)
4. **State-of-the-art 3D Performance**: Achieves 85.6% δ₁ accuracy on NYUv2 depth estimation, surpassing all previous self-supervised methods
5. **Synthetic Pre-training Success**: Demonstrates effectiveness of simulator-based training on 1.8M image pairs

## 🔧 Technical Details

### Architecture
- **Input**: Two images of the same scene (different viewpoints)
- **Output**: Reconstructed RGB patches for masked regions
- **Components**:
  - Encoder: ViT-Base/16 (12 blocks, 768 dims, 12 heads) - processes each image independently
  - Decoder: 8 transformer blocks (512 dims, 16 heads) - reconstructs masked patches
  - Two decoder variants tested:
    - **CrossBlock**: Uses cross-attention between views (better performance)
    - **CatBlock**: Simple concatenation of features

### Key Design Choices
- **High masking ratio**: 90% (much higher than typical MIM)
- **Patch size**: 16×16 on 224×224 images
- **Loss**: Simple MSE on RGB values
- **Optimal co-visibility**: ~50% overlap between views

### Training
- **Dataset**: 1.82M synthetic indoor image pairs from Habitat simulator
- **Sources**: 
  - HM3D: ~1M pairs
  - Gibson: ~400K pairs  
  - Replica: ~200K pairs
  - Other datasets: ~200K pairs
- **Epochs**: 400 with cosine LR schedule
- **Hardware**: 8 V100 GPUs
- **Batch size**: 256
- **Augmentations**: Homography and color jittering

## 📊 Results

**Model Details**: All results use CroCo pre-trained on synthetic data (400 epochs) then fine-tuned on target datasets.

### Quantitative Performance

#### Monocular Depth Estimation (NYUv2)
| Method | δ₁ ↑ | δ₂ ↑ | δ₃ ↑ | REL ↓ | RMS ↓ | log₁₀ ↓ |
|--------|-------|-------|-------|--------|--------|----------|
| MAE | 0.796 | 0.954 | 0.989 | 0.129 | 0.497 | 0.055 |
| MultiMAE | 0.830 | 0.964 | 0.991 | 0.116 | 0.455 | 0.050 |
| **CroCo** | **0.856** | **0.972** | **0.994** | **0.106** | **0.424** | **0.046** |

*Note: δᵢ represents accuracy at threshold 1.25ⁱ*

#### Other Monocular Tasks  
| Task | Dataset | Metric | CroCo | Baseline |
|------|---------|--------|--------|-----------|
| 3D Tasks | Taskonomy | Avg Rank | **1st** | - |
| Segmentation | ADE20k | mIoU | 40.6 | 41.8 (MAE) |
| Classification | ImageNet | Top-1 | 37.0% | 65.5% (MAE) |

#### Binocular Tasks
| Task | Dataset | Split | CroCo | Supervised |
|------|---------|-------|--------|------------|
| Optical Flow | MPI-Sintel | Clean | 3.00 EPE | ~1.4 EPE |
| Optical Flow | MPI-Sintel | Final | 3.60 EPE | ~2.5 EPE |
| Stereo Matching | Middlebury | - | 5.0 bad@1.0 | - |

*Note: CroCo achieves competitive results without task-specific design*

### Qualitative Results
- Sharp depth predictions with fine details
- Accurate optical flow estimation
- Robust cross-view matching capabilities
- Effective on both synthetic and real images

## 💡 Insights & Impact

### Strengths
1. **Geometric Understanding**: Forces model to reason about 3D structure through cross-view constraint
2. **Versatility**: Single pre-trained model for diverse 3D tasks
3. **Efficiency**: Fast convergence on downstream tasks (200 vs 1500 epochs)
4. **Simplicity**: No task-specific components needed

### Limitations
1. **Semantic Performance**: Lower on high-level tasks (ImageNet)
2. **Indoor Bias**: Pre-training limited to indoor scenes
3. **Reconstruction Quality**: MSE loss leads to blurry outputs
4. **Computational Cost**: Decoder adds overhead for single-view tasks

### Impact on the Field
- **Foundation for DUSt3R**: Cross-view understanding → uncalibrated 3D reconstruction
- **Inspired Follow-ups**: CroCo v2, CroCo-Man, and numerous 3D vision models
- **Paradigm Shift**: From semantic to geometric pre-training objectives
- **Synthetic Data Validation**: Proved viability of simulator-based training

## 🔗 Related Work

### Building on CroCo
- **CroCo v2** (ICCV 2023): Enhanced version for stereo and optical flow
- **DUSt3R** (CVPR 2024): Extended to end-to-end 3D reconstruction
- **MASt3R** (ECCV 2024): Unified 3D-aware matching and reconstruction

### Contemporary Approaches
- **MAE**: Masked autoencoding for semantic understanding
- **MultiMAE**: Multi-modal masked autoencoding
- **PixelPlayer**: Cross-modal completion

## 📚 Key Takeaways

CroCo established the foundation for modern feed-forward 3D reconstruction by:
1. Demonstrating that cross-view constraints induce strong 3D representations
2. Creating a unified architecture for diverse 3D vision tasks
3. Proving synthetic pre-training can transfer to real-world applications
4. Inspiring the entire DUSt3R family of models

The progression from CroCo's feature learning to DUSt3R's direct 3D prediction represents a natural evolution in geometric deep learning.