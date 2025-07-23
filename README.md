# DUSt3R and Extensions: A Comprehensive Survey

[![GitHub Stars](https://img.shields.io/github/stars/[YOUR_USERNAME]/[REPO_NAME]?style=social)](https://github.com/[YOUR_USERNAME]/[REPO_NAME])
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Papers](https://img.shields.io/badge/Papers-57-green.svg)](#papers-database)
[![Last Updated](https://img.shields.io/badge/Last%20Updated-July%202025-orange.svg)](#)

> **A systematic survey of DUSt3R and its extensions for feed-forward 3D reconstruction**

This repository provides a comprehensive overview of DUSt3R (Geometric 3D Vision Made Easy) and its rapidly growing ecosystem of extensions and applications. From the pioneering work that introduced feed-forward 3D reconstruction to the latest advances in dynamic scenes and neural rendering.

## 🚀 Quick Start

- **New to DUSt3R?** → Start with [📚 Foundation Papers](docs/foundation/README.md)
- **Looking for specific applications?** → Browse by [🏷️ Categories](#research-categories)
- **Want to implement?** → Check [💻 Implementation Guides](docs/implementation/README.md)
- **Need comparisons?** → See [📊 Performance Tables](docs/benchmarks/README.md)

## 📈 Research Landscape

DUSt3R has catalyzed a paradigm shift in 3D reconstruction, moving from traditional iterative pipelines to **end-to-end feed-forward models**. This survey tracks the explosive growth of this field:

```
2022 ████ 1 paper  (CroCo)
2023 ████ 1 paper  (CroCo v2)
2024 ████████████████████████████████████████ 16 papers
2025 ████████████████████████████████████████████████████████████████████████████████ 39 papers
```

## 🏷️ Research Categories

### 🔬 [Foundation Models](docs/foundation/) (5 papers)
The seminal works that established the feed-forward 3D reconstruction paradigm.

| Paper | Venue | Key Innovation |
|-------|-------|----------------|
| [CroCo](docs/foundation/croco.md) | NeurIPS 2022 | Cross-view completion pretraining |
| [CroCo v2](docs/foundation/croco-v2.md) | ICCV 2023 | Improved stereo & optical flow |
| **[DUSt3R](docs/foundation/dust3r.md)** | CVPR 2024 | **End-to-end 3D reconstruction** |
| [MASt3R](docs/foundation/mast3r.md) | ECCV 2024 | 3D geometry-aware matching |
| [MASt3R-SfM](docs/foundation/mast3r-sfm.md) | arXiv 2024 | Integrated SfM pipeline |

### 🏗️ [3D Reconstruction](docs/reconstruction/) (15 papers)
Core advances in static scene reconstruction, multi-view consistency, and large-scale scenarios.

<details>
<summary>View papers in this category</summary>

- **Real-time Systems**: SLAM3R, Fast3R, MASt3R-SLAM
- **Large-scale**: Pow3R, Align3R, REGIST3R  
- **Quality Enhancement**: VGGT, Test3R, PE3R
- **Efficiency**: SPANN3R, CUT3R, MonST3R

</details>

### 🎬 [Dynamic Scene Reconstruction](docs/dynamic/) (12 papers)
Handling motion, temporal consistency, and dynamic objects.

<details>
<summary>View papers in this category</summary>

- **Motion Modeling**: Easi3R, MonST3R, POMATO, D²USt3R
- **Human Reconstruction**: ODHSR, Endo3R
- **Temporal Consistency**: CUT3R, Align3R, Dynamic Point Maps
- **4D Reconstruction**: Geo4D, Stereo4D, Adapt3R

</details>

### ✨ [Gaussian Splatting](docs/gaussian-splatting/) (12 papers)
Integration with 3D Gaussian Splatting for neural rendering and novel view synthesis.

<details>
<summary>View papers in this category</summary>

- **Core Integration**: EasySplat, MVSplat, PreF3R
- **Style Transfer**: Styl3R, ArtSplat3R, StyleGS
- **Quality Enhancement**: FlowR, SplatSt3R, GauSt3R

</details>

### 🧠 [Scene Understanding](docs/understanding/) (5 papers)
Semantic integration, object reasoning, and spatial relationships.

### 🔍 [Scene Reasoning](docs/reasoning/) (4 papers)
Advanced geometric reasoning and amodal completion.

### 🤖 [Robotics Applications](docs/robotics/) (2 papers)
Hand-eye calibration and object pose estimation for manipulation.

### 📍 [Pose Estimation](docs/pose/) (2 papers)
Camera relocalization and 6D object pose estimation.

## 📊 Key Comparisons

### Performance Overview (DTU Dataset)
| Model | Type | Accuracy ↓ | Completeness ↓ | Overall ↓ | Speed |
|-------|------|------------|-----------------|-----------|--------|
| COLMAP | Traditional | 0.70 | 96.5 | ~3 min | ⭐⭐ |
| MVSNet | Learning+GT | 0.396 | 0.527 | 0.462 | ⭐⭐⭐ |
| **DUSt3R** | **Feed-forward** | **2.667** | **0.805** | **1.741** | **⭐⭐⭐⭐⭐** |
| MASt3R | Feed-forward | 0.403 | 0.344 | 0.374 | ⭐⭐⭐⭐ |
| VGGT | Feed-forward | 0.389 | 0.374 | 0.382 | ⭐⭐⭐⭐ |

*Note: Lower is better for accuracy/completeness metrics*

### Paradigm Comparison
| Aspect | Traditional (SfM+MVS) | Feed-forward (DUSt3R+) |
|--------|----------------------|------------------------|
| **Workflow** | Multi-stage, Sequential | End-to-end, Parallel |
| **Robustness** | Sensitive to texture/lighting | Robust via learned priors |
| **Speed** | Minutes to hours | Seconds |
| **Scalability** | Good for large scenes | Limited by GPU memory |
| **Ease of Use** | Requires expertise | "Black box" inference |

## 🛠️ Implementation Resources

### Official Implementations
- **DUSt3R**: [`facebook/dust3r`](https://github.com/naver/dust3r) ⭐ 1.5k
- **MASt3R**: [`facebook/mast3r`](https://github.com/naver/mast3r) ⭐ 800+
- **SLAM3R**: [`pengsongyou/slam3r`](https://github.com/WangYueFt/slam3r) ⭐ 400+

### Getting Started
```bash
# Quick installation
pip install dust3r

# Basic usage
from dust3r import DUSt3R
model = DUSt3R.from_pretrained("naver/DUSt3R_ViTLarge_BaseDecoder_512_dpt")
```

See our [💻 Implementation Guide](docs/implementation/README.md) for detailed tutorials.

## 📋 Papers Database

### By Publication Year
- **2025**: 39 papers ([CVPR 2025](docs/venues/cvpr2025.md), [ICCV 2025](docs/venues/iccv2025.md), [arXiv](docs/venues/arxiv2025.md))
- **2024**: 16 papers ([CVPR 2024](docs/venues/cvpr2024.md), [ECCV 2024](docs/venues/eccv2024.md))
- **2023**: 1 paper ([ICCV 2023](docs/venues/iccv2023.md))
- **2022**: 1 paper ([NeurIPS 2022](docs/venues/neurips2022.md))

### By Application Domain
- **General 3D Reconstruction**: 20 papers
- **Dynamic Scenes**: 12 papers  
- **Neural Rendering**: 12 papers
- **Robotics & AR/VR**: 7 papers
- **Scene Understanding**: 6 papers

[📄 Complete Papers List](docs/papers-complete.md) | [🔍 Search by Keywords](docs/search.md)

## 🌟 Featured Research Highlights

### 🏆 Most Influential
**DUSt3R** (CVPR 2024) - The paper that started it all, enabling end-to-end 3D reconstruction from uncalibrated images.

### 🎯 Dynamic Scene Breakthrough
**POMATO** (arXiv 2025) - Marries pointmap matching with temporal motion, addressing DUSt3R's limitations in dynamic scenes through explicit matching relationships and temporal consistency.

### 🚀 Latest Breakthroughs
- **Fast3R** (CVPR 2025) - 1000+ images in one forward pass
- **POMATO** (arXiv 2025) - Unified pointmap matching with temporal motion
- **EasySplat** (arXiv 2025) - View-adaptive 3D Gaussian Splatting
- **SLAM3R** (CVPR 2025) - Real-time dense SLAM

### 💡 Most Promising Directions
- **Temporal Consistency** in dynamic scenes
- **Large-scale** city-level reconstruction  
- **Integration** with language models

## 📚 Learning Resources

### Tutorials & Guides
- [🎓 From SfM to Feed-forward: A Paradigm Shift](docs/tutorials/paradigm-shift.md)
- [🔧 Implementing Your First DUSt3R Model](docs/tutorials/first-model.md)
- [📊 Evaluation Metrics and Benchmarks](docs/tutorials/evaluation.md)
- [🚀 Scaling to Large Scenes](docs/tutorials/scaling.md)

### Research Papers Analysis
- [📖 Technical Deep Dives](docs/analysis/) - In-depth analysis of key papers
- [🔄 Evolution Timeline](docs/timeline.md) - How the field developed
- [🔗 Research Graph](docs/connections.md) - Connections between papers

## 🤝 Contributing

We welcome contributions from the research community! 

### How to Contribute
1. **Add new papers**: Use our [paper template](docs/templates/paper-template.md)
2. **Update benchmarks**: Submit new experimental results
3. **Fix errors**: Report issues or submit corrections
4. **Improve documentation**: Enhance explanations and tutorials

See our [Contributing Guide](CONTRIBUTING.md) for detailed instructions.

### Recent Contributors
Thanks to all researchers who have contributed to this survey! 🙏

## 📞 Contact & Citation

### Citation
If you find this survey useful for your research, please cite:
```bibtex
@misc{dust3r_survey_2025,
  title={DUSt3R and Extensions: A Comprehensive Survey},
  author={[Your Name]},
  year={2025},
  url={https://github.com/[YOUR_USERNAME]/[REPO_NAME]}
}
```

### Connect
- 💬 **Discussions**: [GitHub Discussions](../../discussions)
- 🐛 **Issues**: [GitHub Issues](../../issues)

## 📄 License

This survey is released under the [MIT License](LICENSE). Individual papers retain their original licenses.

---

<div align="center">

**⭐ Star this repo if you find it useful! ⭐**

*Last updated: July 2025 | Next update: August 2025*

</div>
