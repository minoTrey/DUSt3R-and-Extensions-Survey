# Dens3R: A Foundation Model for 3D Geometry Prediction (arXiv 2025)

![Dens3R Teaser](https://g-1nonly.github.io/Dens3R/static/images/Teaser.png)
*Dens3R provides unified geometric dense prediction for high-quality 3D reconstruction from unposed images through joint modeling of multiple geometric quantities*

## 📋 Overview
- **Authors**: Xianze Fang, Jingnan Gao, Zhe Wang, Zhuo Chen, Xingyu Ren, Jiangjing Lyu, Qiaomu Ren, Zhonglei Yang, Xiaokang Yang, Yichao Yan, Chengfei Lyu
- **Institution**: Alibaba Group, Shanghai Jiao Tong University
- **Venue**: arXiv preprint (2025)
- **Links**: [Paper](https://arxiv.org/abs/2507.16290) | [Project Page](https://g-1nonly.github.io/Dens3R/) | [Code](https://github.com/G-1nOnly/Dens3R)
- **TL;DR**: Foundation model for unified 3D geometry prediction that jointly models depth, surface normals, and point maps with explicit structural coupling.

## 🎯 Key Contributions

1. **Unified Framework**: Joint geometric dense prediction for multiple quantities
2. **Structural Coupling**: Explicitly models relationships between geometric properties
3. **Intrinsic Invariance**: Achieves invariance in pointmap representation
4. **High-Resolution Support**: Handles 2K inputs with quality geometric predictions
5. **Versatile Foundation Model**: Adaptable to various downstream 3D reconstruction tasks

## 🔧 Technical Details

### Core Innovation: Unified Dense Prediction
```
Traditional: Separate models for depth, normals, point maps → Inconsistent geometry
Dens3R: Joint geometric prediction → Consistent, coupled geometric understanding
```

### Technical Approach

#### 1. Two-Stage Training Framework
- **Stage 1**: Foundation geometric understanding
- **Stage 2**: Multi-view consistency and refinement
- Progressive training for optimal convergence
- Joint optimization across geometric quantities

#### 2. Unified Architecture
```
Input: Unposed images {I₁, I₂, ..., Iₙ}
Encoder: Lightweight shared backbone
Decoder: Multi-head geometric prediction
Output: {Depth, Normals, Point maps} with structural coupling
```

#### 3. Key Components
- **Shared Encoder-Decoder**: Lightweight backbone architecture
- **Position-Interpolated RoPE**: Rotary positional encoding for spatial awareness
- **Multi-Head Prediction**: Joint geometric quantity regression
- **Image-Pair Matching**: Integrates matching features for improved geometry

### Geometric Coupling Strategy
- **Cross-Property Learning**: Depth and normals inform each other
- **Consistency Constraints**: Geometric relationships maintained
- **Joint Optimization**: Single loss function for all quantities
- **Multi-Scale Processing**: Handles various input resolutions

## 📊 Results

### Surface Normal Prediction Results

#### Quantitative Comparison (Angular Error)
| Dataset | Method | Mean ↓ | Median ↓ | δ<11.25° ↑ |
|---------|--------|--------|----------|------------|
| **NYUv2** | DSINE | 18.6 | 9.9 | 56.1% |
| | Lotus-G | 17.5 | 8.6 | 58.7% |
| | GeoWizard | 20.4 | 11.9 | 47.0% |
| | StableNormal | 19.7 | 10.5 | 53.0% |
| | **Ours** | **16.1** | **7.4** | **62.5%** |
| **ScanNet** | DSINE | 18.6 | 9.9 | 56.1% |
| | Lotus-G | 18.1 | 8.8 | 58.2% |
| | GeoWizard | 21.4 | 13.9 | 37.1% |
| | StableNormal | 18.1 | 10.1 | 56.0% |
| | **Ours** | **16.9** | **7.1** | **64.0%** |
| **iBims-1** | DSINE | 18.8 | 8.3 | 64.1% |
| | Lotus-G | 19.2 | 5.6 | 66.2% |
| | GeoWizard | 19.7 | 9.7 | 58.4% |
| | StableNormal | 17.2 | 8.1 | 66.7% |
| | **Ours** | **16.0** | **4.3** | **72.2%** |
| **Sintel** | DSINE | 34.9 | 28.1 | 21.5% |
| | Lotus-G | 35.7 | 28.0 | 20.5% |
| | GeoWizard | 41.6 | 34.3 | 11.8% |
| | StableNormal | 35.0 | 27.0 | 19.5% |
| | **Ours** | **30.7** | **21.4** | **28.9%** |
| **DIODE-outdoor** | DSINE | 22.0 | 14.5 | 39.6% |
| | Lotus-G | 24.7 | 15.9 | 32.9% |
| | GeoWizard | 27.0 | 19.8 | 24.0% |
| | StableNormal | 26.9 | 16.1 | 36.1% |
| | **Ours** | **20.8** | **12.8** | **43.0%** |

*Note: Lower is better for Mean/Median errors, higher is better for δ<11.25°*

### Camera Pose Estimation Results

#### Map-free Dataset
| Method | Reproj. Error ↓ | Precision ↑ | AUC ↑ | Median Error (m) ↓ | Median Error (°) ↓ | Pose Precision ↑ | Pose AUC ↑ |
|--------|----------------|-------------|--------|-------------------|-------------------|------------------|------------|
| DUSt3R | 125.8 px | 45.2% | 0.704 | 1.10 m | 9.4° | 17.0% | 0.344 |
| MASt3R | 57.2 px | 75.9% | 0.934 | 0.46 m | 3.0° | 51.7% | 0.746 |
| VGGT | 48.8 px | 78.9% | 0.789 | 0.36 m | 3.6° | 57.7% | 0.577 |
| **Ours** | **30.4 px** | **82.1%** | **0.944** | **0.24 m** | **3.4°** | **65.5%** | **0.852** |

### Two-view Matching Results

#### ScanNet-1500 Dataset
| Method | AUC@5° ↑ | AUC@10° ↑ | AUC@20° ↑ |
|--------|----------|-----------|-----------|
| ROMA | 31.8 | 53.4 | 70.9 |
| VGGT | 33.9 | 55.2 | 73.4 |
| MASt3R | 62.4 | 77.4 | 86.9 |
| **Ours** | **65.6** | **80.3** | **89.2** |

#### MegaDepth-1500 Dataset
| Method | AUC@5° ↑ | AUC@10° ↑ | AUC@20° ↑ |
|--------|----------|-----------|-----------|
| SP+SG | 42.2 | 61.2 | 76.0 |
| SP+LG | 49.9 | 67.0 | 80.1 |
| LoFTR | 52.8 | 69.2 | 81.2 |
| MASt3R | 73.3 | 84.1 | 90.9 |
| **Ours** | **73.9** | **84.4** | **91.2** |

### Model Efficiency
| Setting | Compute Cost | Memory Cost | Network Params |
|---------|--------------|-------------|----------------|
| w/o Shared | 1.362 TFlops | 4.6 GB | 737.591 M |
| **w/ Shared** | **1.362 TFlops** | **4.1 GB** | **624.152 M** |

*Experiments conducted on image pairs with 512 resolution*

### Resolution Support
| Resolution | Processing | Quality | Speed |
|------------|------------|---------|-------|
| 512×512 | Standard | Good | Fast |
| 1024×1024 | Enhanced | Better | Medium |
| **2048×2048** | **High-quality** | **Excellent** | **Practical** |

### Key Achievements
- ✅ **Best normal prediction** across all benchmarks (16.1° mean error on NYUv2)
- ✅ **72.2% accuracy** on iBims-1 (δ<11.25°), highest among all methods
- ✅ **State-of-the-art pose estimation**: 30.4px reprojection error (76% better than DUSt3R)
- ✅ **Superior two-view matching**: 65.6% AUC@5° on ScanNet (best performance)
- ✅ **Efficient architecture**: 11% less memory (4.1GB vs 4.6GB) with shared encoder-decoder
- ✅ **High-resolution support** up to 2K resolution with unified framework

## 💡 Insights & Impact

### Paradigm Shift in Geometric Prediction

**Traditional Approach**:
1. Separate models for each geometric quantity
2. Inconsistent predictions across properties
3. Limited cross-property understanding
4. Manual post-processing for consistency

**Dens3R Approach**:
1. Unified model for all geometric quantities
2. Structurally coupled predictions
3. Deep geometric understanding
4. Automatic consistency maintenance

### Why Unified Prediction Works
1. **Structural Coupling**: Geometric properties are inherently related
2. **Shared Learning**: Common features benefit all predictions
3. **Consistency**: Joint optimization ensures coherent geometry
4. **Efficiency**: Single model reduces computational overhead

### Applications
- **3D Reconstruction**: High-quality scene reconstruction
- **Robot Navigation**: Comprehensive scene understanding
- **AR/VR**: Robust geometry for immersive experiences
- **Autonomous Driving**: Multi-modal geometric perception
- **Digital Twins**: Detailed geometric modeling

### Technical Advantages
- **Unified**: Single model for multiple tasks
- **Consistent**: Geometrically coherent predictions
- **Scalable**: Handles high-resolution inputs
- **Efficient**: Lightweight shared architecture

## 🔗 Related Work

### Comparison with Foundation Models
| Model | Geometric Quantities | Coupling | Resolution | Multi-view |
|-------|---------------------|----------|------------|------------|
| DUSt3R | Point maps | None | 512 | Limited |
| MASt3R | Points + Matching | Basic | 512 | Good |
| MoGe | Depth + Normals | Limited | 1024 | Medium |
| **Dens3R** | **All + Unified** | **Explicit** | **2048** | **Excellent** |

### Builds On
- **DUSt3R**: Foundation model architecture and point map prediction
- **Multi-Task Learning**: Joint optimization strategies
- **Geometric Processing**: 3D geometric understanding
- **Dense Prediction**: High-resolution geometric estimation

### Relationship to DUSt3R Ecosystem
- **Extension**: Builds upon DUSt3R's foundation model approach
- **Enhancement**: Adds unified geometric prediction capabilities
- **Consistency**: Addresses geometric coherence limitations
- **Scalability**: Extends to higher resolutions and multi-task scenarios

## 📚 Key Takeaways

Dens3R demonstrates that:
1. **Unified prediction superior**: Joint geometric modeling outperforms separate approaches
2. **Structural coupling matters**: Explicitly modeling geometric relationships improves consistency
3. **High-resolution achievable**: Foundation models can scale to 2K+ resolutions
4. **Multi-view consistency**: Unified approach enables consistent cross-view geometry

The success of Dens3R in achieving unified, consistent geometric prediction represents a significant advancement toward comprehensive 3D understanding from unposed images.