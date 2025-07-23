# MoGe: Unlocking Accurate Monocular Geometry Estimation for Open-Domain Images (CVPR 2025)

![MoGe Overview](https://wangrc.site/MoGePage/static/images/overview.png)
*MoGe enables accurate monocular geometry estimation on diverse open-domain images through robust foundation model training*

## 📋 Overview
- **Authors**: Ruicheng Wang, Sicheng Xu, Cassie Dai, Jianfeng Xiang, Yu Deng, Xin Tong, Jiaolong Yang
- **Institution**: Microsoft Research, University of Washington
- **Venue**: CVPR 2025
- **Links**: [Paper](https://arxiv.org/abs/2410.19115) | [Project Page](https://wangrc.site/MoGePage/) | [Code](https://github.com/microsoft/MoGe)
- **TL;DR**: Foundation model for accurate monocular geometry estimation that works across diverse open-domain images with superior generalization capabilities.

## 🎯 Key Contributions

1. **Open-Domain Generalization**: Works on diverse real-world images
2. **Robust Foundation Model**: Large-scale training for geometry estimation
3. **Accurate Depth Prediction**: Superior monocular depth estimation
4. **Normal Estimation**: Joint depth and surface normal prediction
5. **Broad Applicability**: Handles various scene types and conditions

## 🔧 Technical Details

### Core Innovation: Foundation-Scale Geometry
```
Traditional: Task-specific depth models → Limited generalization
MoGe: Foundation model training → Open-domain geometry estimation
```

### Technical Approach

#### 1. Foundation Model Architecture
- Large-scale transformer-based architecture
- Multi-task learning for depth and normals
- Robust feature representations
- Cross-domain training strategy

#### 2. Training Strategy
```
Data: Diverse multi-domain datasets
Scale: Foundation model size training
Tasks: Joint depth + normal estimation
Target: Open-domain generalization
```

#### 3. Key Components
- **Geometry Encoder**: Multi-scale feature extraction
- **Multi-Task Decoder**: Joint depth and normal prediction
- **Domain Adaptation**: Cross-domain robustness
- **Quality Assessment**: Uncertainty estimation

### Architecture Design
- **Transformer Backbone**: Scalable attention mechanism
- **Multi-Resolution**: Handles different image scales
- **Robust Training**: Domain adaptation techniques
- **Efficient Inference**: Optimized for practical use

## 📊 Results

### Quantitative Performance
| Dataset | Metric | Previous SOTA | MoGe | Improvement |
|---------|--------|---------------|------|-------------|
| NYU-v2 | δ₁↑ | 0.925 | **0.952** | +2.7% |
| KITTI | AbsRel↓ | 0.062 | **0.055** | -11.3% |
| ETH3D | δ₁↑ | 0.887 | **0.921** | +3.4% |
| ScanNet | δ₁↑ | 0.847 | **0.889** | +4.2% |

### Cross-Domain Generalization
| Domain | Previous | MoGe | Zero-Shot |
|--------|----------|------|-----------|
| Indoor | Good | **Excellent** | ✅ |
| Outdoor | Good | **Excellent** | ✅ |
| Natural | Poor | **Good** | ✅ |
| Medical | Poor | **Good** | ✅ |

### Key Achievements
- ✅ SOTA performance across multiple benchmarks
- ✅ Superior zero-shot generalization
- ✅ Joint depth and normal estimation
- ✅ Robust to domain shifts
- ✅ Efficient inference speed

## 💡 Insights & Impact

### Paradigm Shift in Monocular Geometry

**Traditional Approach**:
1. Task-specific models
2. Limited domain coverage
3. Poor generalization
4. Separate depth/normal models

**MoGe Approach**:
1. Foundation model scale
2. Multi-domain training
3. Excellent generalization
4. Joint multi-task learning

### Why Foundation Scale Works
1. **Data Diversity**: Massive multi-domain training
2. **Model Capacity**: Large-scale architecture
3. **Robust Features**: Domain-invariant representations
4. **Multi-Task Learning**: Joint optimization benefits

### Applications
- **Robotics**: Scene understanding and navigation
- **AR/VR**: Real-time geometry estimation
- **Autonomous Driving**: Road surface reconstruction
- **Photography**: Depth-aware effects
- **Medical Imaging**: Surface analysis

### Limitations
- Computational requirements for large model
- Still struggles with transparent/reflective surfaces
- Limited by training data distribution
- May hallucinate geometry in ambiguous regions

## 🔗 Related Work

### Comparison with Depth Methods
| Method | Domain | Accuracy | Generalization | Speed |
|--------|--------|----------|----------------|-------|
| MiDaS | Mixed | Good | Medium | Fast |
| DPT | Indoor | Good | Poor | Medium |
| ZoeDepth | Mixed | Better | Good | Fast |
| **MoGe** | **All** | **Best** | **Excellent** | **Good** |

### Builds On
- **Foundation Models**: Large-scale training paradigms
- **Multi-Task Learning**: Joint depth and normal estimation
- **Domain Adaptation**: Cross-domain robustness techniques
- **Transformer Architecture**: Scalable attention mechanisms

### Relationship to DUSt3R Ecosystem
- **Complementary**: Provides monocular geometry for single images
- **Input Provider**: Can provide initial geometry estimates
- **Quality Enhancement**: Better single-view understanding
- **Foundation**: Shares foundation model philosophy

## 📚 Key Takeaways

MoGe demonstrates that:
1. **Scale matters**: Foundation model size improves generalization
2. **Multi-domain training works**: Diverse data enables robustness
3. **Joint learning helps**: Multi-task optimization improves both tasks
4. **Open-domain is achievable**: Foundation models can generalize broadly

The success of MoGe in achieving accurate monocular geometry estimation across diverse domains represents a significant step toward universal geometry understanding from single images.