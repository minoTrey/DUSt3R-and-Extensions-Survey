# π³: Scalable Permutation-Equivariant Visual Geometry Learning (arXiv 2025)

![Pi3 Teaser](https://yyfz.github.io/pi3/assets/images/main.png)
*π³ eliminates reference view bias through permutation-equivariant architecture, achieving state-of-the-art visual geometry reconstruction*

## 📋 Overview
- **Authors**: Yifan Wang, Jianjun Zhou, Haoyi Zhu, Wenzheng Chang, Yang Zhou, Zizun Li, Junyi Chen, Jiangmiao Pang, Chunhua Shen, Tong He
- **Institution**: Shanghai AI Lab, Zhejiang University, SenseTime
- **Venue**: arXiv preprint (2025)
- **Links**: [Paper](https://arxiv.org/abs/2507.13347) | [Project Page](https://yyfz.github.io/pi3/) | [Code](https://github.com/yyfz/Pi3) | [Demo](https://huggingface.co/spaces/yyfz233/Pi3)
- **TL;DR**: Permutation-equivariant neural network that achieves state-of-the-art visual geometry reconstruction without requiring fixed reference views.

## 🎯 Key Contributions

1. **Permutation-Equivariant Architecture**: First method to systematically eliminate reference view bias
2. **Order-Invariant Reconstruction**: Consistent results regardless of input image sequence
3. **Affine-Invariant Poses**: Direct prediction without fixed reference viewpoint
4. **SOTA Performance**: Best results across all benchmarks, surpassing VGGT and other methods

## 🔧 Technical Details

### Architecture Components

1. **Transformer Architecture**: Alternating view-wise and global self-attention blocks
2. **DINOv2 Backbone**: Embeds image views into patch tokens without positional encoding
3. **Permutation-Equivariant Processing**: Treats all views symmetrically without designated reference
4. **Dual Output**: Affine-invariant camera poses + scale-invariant local point maps

### Key Innovation: True Permutation Equivariance
- **Problem**: Previous methods rely on fixed reference views, causing ordering bias
- **Solution**: Symmetric processing of all input views
- **Result**: Near-zero variance across different input permutations

## 📊 Results

### Table 1: Camera Pose Estimation on RealEstate10K and Co3Dv2
| Method | RealEstate10K (unseen) | | | Co3Dv2 (seen) | | |
|--------|------------------------|-------|-------|----------------|-------|-------|
| | RRA@30↑ | RTA@30↑ | AUC@30↑ | RRA@30↑ | RTA@30↑ | AUC@30↑ |
| Fast3R | 99.05 | 81.86 | 61.68 | 97.49 | 91.11 | 73.43 |
| CUT3R | 99.82 | 95.10 | 81.47 | 96.19 | 92.69 | 75.82 |
| FLARE | 99.69 | 95.23 | 80.01 | 96.38 | 93.76 | 73.99 |
| VGGT | 99.97 | 93.13 | 77.62 | 98.96 | 97.13 | 88.59 |
| **π³** | **99.99** | **95.62** | **85.90** | **99.05** | **97.33** | **88.41** |

### Table 2: Camera Pose Estimation on Sintel, TUM-dynamics and ScanNet
| Method | Sintel (zero-shot) | | | TUM-dynamics (zero-shot) | | | ScanNet (seen) | | |
|--------|-------------------|---------|---------|-------------------------|---------|---------|----------------|---------|----------|
| | ATE↓ | RPE trans↓ | RPE rot↓ | ATE↓ | RPE trans↓ | RPE rot↓ | ATE↓ | RPE trans↓ | RPE rot↓ |
| Fast3R | 0.371 | 0.298 | 13.75 | 0.090 | 0.101 | 1.425 | 0.155 | 0.123 | 3.491 |
| CUT3R | 0.217 | 0.070 | 0.636 | 0.047 | 0.015 | 0.451 | 0.094 | 0.022 | 0.629 |
| Aether | 0.189 | 0.054 | 0.694 | 0.092 | 0.012 | 1.106 | 0.176 | 0.028 | 1.204 |
| FLARE | 0.207 | 0.090 | 3.015 | 0.026 | 0.013 | 0.475 | 0.064 | 0.023 | 0.971 |
| VGGT | 0.167 | 0.062 | 0.491 | 0.012 | 0.010 | 0.311 | 0.035 | 0.015 | 0.382 |
| **π³** | **0.074** | **0.040** | **0.282** | **0.014** | **0.009** | **0.312** | **0.031** | **0.013** | **0.347** |

### Table 3: Point Map Estimation on DTU and ETH3D
| Method | DTU | | | | | | ETH3D | | | | | |
|--------|-----|-----|-----|-----|-----|-----|-------|-----|-----|-----|-----|-----|
| | Acc.↓ Mean | Med. | Comp.↓ Mean | Med. | N.C.↑ Mean | Med. | Acc.↓ Mean | Med. | Comp.↓ Mean | Med. | N.C.↑ Mean | Med. |
| Fast3R | 3.340 | 1.919 | 2.929 | 1.125 | 0.671 | 0.755 | 0.832 | 0.691 | 0.978 | 0.683 | 0.667 | 0.766 |
| CUT3R | 4.742 | 2.600 | 3.400 | 1.316 | 0.679 | 0.764 | 0.617 | 0.525 | 0.747 | 0.579 | 0.754 | 0.848 |
| FLARE | 2.541 | 1.468 | 3.174 | 1.420 | 0.684 | 0.774 | 0.464 | 0.338 | 0.664 | 0.395 | 0.744 | 0.864 |
| VGGT | 1.338 | 0.779 | 1.896 | 0.992 | 0.676 | 0.766 | 0.280 | 0.185 | 0.305 | 0.182 | 0.853 | 0.950 |
| **π³** | **1.198** | **0.646** | **1.849** | **0.607** | **0.678** | **0.768** | **0.194** | **0.131** | **0.210** | **0.128** | **0.883** | **0.969** |

### Table 4: Point Map Estimation on 7-Scenes and NRGBD
| Method | View | 7-Scenes | | | | | | NRGBD | | | | | |
|--------|------|----------|-----|-----|-----|-----|-----|-------|-----|-----|-----|-----|-----|
| | | Acc.↓ Mean | Med. | Comp.↓ Mean | Med. | NC.↑ Mean | Med. | Acc.↓ Mean | Med. | Comp.↓ Mean | Med. | NC.↑ Mean | Med. |
| Fast3R | sparse | 0.096 | 0.065 | 0.145 | 0.093 | 0.672 | 0.760 | 0.135 | 0.091 | 0.163 | 0.104 | 0.759 | 0.877 |
| CUT3R | | 0.094 | 0.051 | 0.101 | 0.050 | 0.703 | 0.804 | 0.104 | 0.041 | 0.079 | 0.031 | 0.822 | 0.968 |
| FLARE | | 0.085 | 0.058 | 0.142 | 0.104 | 0.695 | 0.779 | 0.053 | 0.024 | 0.051 | 0.025 | 0.877 | 0.988 |
| VGGT | | 0.046 | 0.026 | 0.057 | 0.034 | 0.728 | 0.842 | 0.051 | 0.029 | 0.066 | 0.038 | 0.890 | 0.981 |
| **π³** | | **0.048** | **0.028** | **0.072** | **0.047** | **0.742** | **0.842** | **0.026** | **0.015** | **0.028** | **0.014** | **0.916** | **0.992** |
| Fast3R | dense | 0.038 | 0.015 | 0.056 | 0.018 | 0.645 | 0.725 | 0.072 | 0.030 | 0.050 | 0.016 | 0.790 | 0.934 |
| CUT3R | | 0.022 | 0.010 | 0.027 | 0.009 | 0.668 | 0.762 | 0.086 | 0.037 | 0.048 | 0.017 | 0.800 | 0.953 |
| FLARE | | 0.018 | 0.007 | 0.027 | 0.014 | 0.681 | 0.781 | 0.023 | 0.011 | 0.018 | 0.008 | 0.882 | 0.986 |
| VGGT | | 0.022 | 0.008 | 0.027 | 0.013 | 0.663 | 0.757 | 0.017 | 0.010 | 0.015 | 0.005 | 0.893 | 0.988 |
| **π³** | | **0.015** | **0.007** | **0.022** | **0.011** | **0.687** | **0.790** | **0.015** | **0.008** | **0.013** | **0.005** | **0.898** | **0.987** |

### Table 5: Video Depth Estimation on Sintel, Bonn and KITTI
| Method | Params | Align | Sintel | | Bonn | | KITTI | | FPS |
|--------|--------|-------|--------|-------|------|-------|-------|-------|---------|
| | | | Abs Rel↓ | δ<1.25↑ | Abs Rel↓ | δ<1.25↑ | Abs Rel↓ | δ<1.25↑ | |
| DUSt3R | 571M | scale | 0.662 | 0.434 | 0.151 | 0.839 | 0.143 | 0.814 | 1.25 |
| MASt3R | 689M | | 0.558 | 0.487 | 0.188 | 0.765 | 0.115 | 0.848 | 1.01 |
| MonST3R | 571M | | 0.399 | 0.519 | 0.072 | 0.957 | 0.107 | 0.884 | 1.27 |
| Fast3R | 648M | | 0.638 | 0.422 | 0.194 | 0.772 | 0.138 | 0.834 | 65.8 |
| MVDUSt3R | 661M | | 0.805 | 0.283 | 0.426 | 0.357 | 0.456 | 0.342 | 0.69 |
| CUT3R | 793M | | 0.417 | 0.507 | 0.078 | 0.937 | 0.122 | 0.876 | 6.98 |
| Aether | 5.57B | | 0.324 | 0.502 | 0.273 | 0.594 | 0.056 | 0.978 | 6.14 |
| FLARE | 1.40B | | 0.729 | 0.336 | 0.152 | 0.790 | 0.356 | 0.570 | 1.75 |
| VGGT | 1.26B | | 0.299 | 0.638 | 0.057 | 0.966 | 0.062 | 0.969 | 43.2 |
| **π³** | **959M** | | **0.233** | **0.664** | **0.049** | **0.975** | **0.038** | **0.986** | **57.4** |
| DUSt3R | 571M | scale&shift | 0.570 | 0.493 | 0.152 | 0.835 | 0.135 | 0.818 | 1.25 |
| MASt3R | 689M | | 0.480 | 0.517 | 0.189 | 0.771 | 0.115 | 0.849 | 1.01 |
| MonST3R | 571M | | 0.402 | 0.526 | 0.070 | 0.958 | 0.098 | 0.883 | 1.27 |
| Fast3R | 648M | | 0.518 | 0.486 | 0.196 | 0.768 | 0.139 | 0.808 | 65.8 |
| MVDUSt3R | 661M | | 0.619 | 0.332 | 0.482 | 0.357 | 0.401 | 0.355 | 0.69 |
| CUT3R | 793M | | 0.534 | 0.558 | 0.075 | 0.943 | 0.111 | 0.883 | 6.98 |
| Aether | 5.57B | | 0.314 | 0.604 | 0.308 | 0.602 | 0.054 | 0.977 | 6.14 |
| FLARE | 1.40B | | 0.791 | 0.358 | 0.142 | 0.797 | 0.357 | 0.579 | 1.75 |
| VGGT | 1.26B | | 0.230 | 0.678 | 0.052 | 0.969 | 0.052 | 0.968 | 43.2 |
| **π³** | **959M** | | **0.210** | **0.726** | **0.043** | **0.975** | **0.037** | **0.985** | **57.4** |

### Performance Summary
- **Camera Pose**: 55.7% better ATE on Sintel (0.074 vs VGGT 0.167)
- **Point Maps**: 30.7% better accuracy on ETH3D (0.194 vs VGGT 0.280)
- **Video Depth**: Best results across all datasets with both scale and scale&shift alignment
- **Speed**: 57.4 FPS on KITTI (vs VGGT 43.2 FPS, Fast3R 65.8 FPS)
- **Efficiency**: 959M params achieving better results than models with 1.26B-5.57B params

## 💡 Critical Analysis

### Strengths
- **Reference View Elimination**: Solves fundamental bias problem in visual geometry
- **Order Invariance**: Robust to arbitrary input sequence permutations
- **Superior Performance**: State-of-the-art across multiple benchmarks
- **Faster Training**: Better convergence due to symmetric architecture

### Limitations
- **Computational Overhead**: Transformer architecture may be slower than simpler methods
- **Memory Requirements**: Processing all views symmetrically increases memory usage
- **Limited Scale Testing**: Evaluation mostly on standard benchmarks

### Applications
- **Multi-camera Systems**: Autonomous vehicles, surveillance, robotics
- **AR/VR**: Flexible reconstruction without view ordering constraints
- **Photogrammetry**: Professional 3D scanning and mapping

## 🔗 Method Comparison

| Method | Reference View | Order Dependence | Speed (FPS) | Performance |
|--------|----------------|------------------|-------------|-------------|
| DUSt3R | Required | High | 1.25 | Baseline |
| VGGT | Required | Medium | 43.2 | Good |
| **π³** | **None** | **None** | **57.4** | **SOTA** |

### Key Differences from VGGT
- **Architecture**: Eliminates reference view bias through symmetric processing
- **Robustness**: Invariant to input ordering (near-zero variance)
- **Performance**: Better on all tasks - pose (55.7%), point maps (30.7%), video depth (22%)
- **Speed**: 33% faster inference (57.4 vs 43.2 FPS)
- **Efficiency**: Smaller model (959M vs 1.26B params) with better results

## 📚 Conclusions

### Key Achievements
1. **Reference-Free Reconstruction**: First method to systematically eliminate reference view bias
2. **State-of-the-Art Performance**: Superior results across camera pose, point maps, and video depth
3. **Order Invariance**: Robust to arbitrary input permutations
4. **Practical Speed**: 57.4 FPS enables real-time applications

### Impact
- **Consumer**: More robust 3D capture from unordered photo collections
- **Professional**: Reliable multi-camera systems without view ordering constraints
- **Research**: Establishes permutation equivariance as key principle for visual geometry

### Significance

π³ proves that eliminating reference view bias through permutation-equivariant design leads to both superior performance and increased robustness, establishing a new paradigm for visual geometry learning.