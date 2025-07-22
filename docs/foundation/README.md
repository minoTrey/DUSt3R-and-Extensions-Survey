# Foundation Models

## 🔬 Overview

The foundation models category represents the seminal works that established the feed-forward 3D reconstruction paradigm. These papers introduced key innovations that moved the field from traditional iterative methods (SfM + MVS) to end-to-end learnable approaches.

## 📈 Research Timeline

```
2022: CroCo     - Cross-view completion pretraining
2023: CroCo v2  - Enhanced stereo and optical flow
2024: DUSt3R    - End-to-end 3D reconstruction ⭐
2024: MASt3R    - 3D-aware feature matching
2024: MASt3R-SfM - Complete SfM pipeline
```

## 🎯 Key Innovations

1. **Self-supervised Pretraining** (CroCo, CroCo v2)
   - Cross-view completion as pretext task
   - No need for 3D ground truth annotations
   - Effective representation learning for downstream tasks

2. **Feed-forward 3D Reconstruction** (DUSt3R)
   - Direct regression of 3D pointmaps
   - Confidence-aware predictions
   - Works with uncalibrated images

3. **3D-aware Feature Matching** (MASt3R)
   - Integrates geometric understanding into matching
   - Improved accuracy over traditional feature matching
   - Enables robust multi-view reconstruction

4. **Complete SfM Pipeline** (MASt3R-SfM)
   - End-to-end trainable structure from motion
   - Handles unordered image collections
   - Competitive with traditional pipelines

## 📊 Performance Comparison

### DTU Dataset (3D Reconstruction Quality)
| Model | Accuracy ↓ | Completeness ↓ | Overall ↓ | Speed |
|-------|------------|----------------|-----------|--------|
| COLMAP | 0.70 | 0.96 | 0.83 | ⭐⭐ |
| DUSt3R | 2.67 | 0.81 | 1.74 | ⭐⭐⭐⭐⭐ |
| MASt3R | 0.40 | 0.34 | 0.37 | ⭐⭐⭐⭐ |

### HPatches (Feature Matching)
| Model | MMA@3px | MMA@5px | MMA@10px |
|-------|---------|---------|----------|
| SuperPoint + SuperGlue | 52.4 | 68.1 | 82.7 |
| MASt3R | 68.2 | 81.3 | 91.4 |

## 🔗 Paper Links

1. [CroCo: Self-Supervised Pre-training for 3D Vision Tasks by Cross-View Completion](croco.md)
2. [CroCo v2: Improved Cross-view Completion Pre-training for Stereo Matching and Optical Flow](croco-v2.md)
3. [DUSt3R: Geometric 3D Vision Made Easy](dust3r.md)
4. [MASt3R: Matching And Stereo 3D Reconstruction](mast3r.md)
5. [MASt3R-SfM: A Fully-Integrated Solution for Uncalibrated Multi-View 3D Reconstruction](mast3r-sfm.md)

## 💡 Impact on the Field

These foundation models have:
- **Democratized 3D reconstruction** by removing the need for calibration
- **Accelerated research** with readily available pretrained models
- **Enabled new applications** in robotics, AR/VR, and content creation
- **Inspired 50+ follow-up papers** in just 2 years

## 🚀 Getting Started

```python
# Quick start with DUSt3R
from dust3r.inference import inference
from dust3r.model import AsymmetricCroCo3DStereo

# Load pretrained model
model = AsymmetricCroCo3DStereo.from_pretrained("naver/DUSt3R_ViTLarge_BaseDecoder_512_dpt")

# Run inference on image pairs
output = inference([(img1, img2)], model)
```

See individual paper pages for detailed implementation guides and usage examples.