# DUSt3R and Extensions: A Comprehensive Survey

[![GitHub Stars](https://img.shields.io/github/stars/minoTrey/DUSt3R-and-Extensions-Survey?style=social)](https://github.com/minoTrey/DUSt3R-and-Extensions-Survey)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Papers](https://img.shields.io/badge/Papers-42-green.svg)](#papers-database)
[![Last Updated](https://img.shields.io/badge/Last%20Updated-July%202025-orange.svg)](#)

> **A systematic survey of DUSt3R and its extensions for feed-forward 3D reconstruction**

This repository provides a comprehensive overview of DUSt3R (Geometric 3D Vision Made Easy) and its rapidly growing ecosystem of extensions and applications. From the pioneering work that introduced feed-forward 3D reconstruction to the latest advances in dynamic scenes and neural rendering.

## 🚀 Quick Start

- **New to DUSt3R?** → Start with [📚 Foundation Papers](docs/foundation/README.md)
- **Looking for specific applications?** → Browse by [🏷️ Categories](#research-categories)
- **Want full list?** → See [📄 Complete Papers List](docs/papers-complete.md)

## 📈 Research Landscape

DUSt3R has catalyzed a paradigm shift in 3D reconstruction, moving from traditional iterative pipelines to **end-to-end feed-forward models**. This survey tracks the explosive growth of this field:

```
2022 ████ 1 paper  (CroCo)
2023 ████ 1 paper  (CroCo v2)
2024 ████████████████████████████████████████ 10 papers
2025 ████████████████████████████████████████████████████████████████████████████████ 30 papers
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

### 🏗️ [3D Reconstruction](docs/reconstruction/) (14 papers)
Core advances in static scene reconstruction, multi-view consistency, and large-scale scenarios.

<details>
<summary>View papers in this category</summary>

- **Real-time Systems**: SLAM3R, Fast3R, MASt3R-SLAM, Spann3R
- **Multi-view**: MUSt3R, MV-DUSt3R+, Light3R-SfM
- **Quality Enhancement**: VGGT, Test3R, Pow3R
- **Specialized**: Mono3R, SPARS3R, Rig3R, Regist3R

</details>

### 🎬 [Dynamic Scene Reconstruction](docs/dynamic/) (9 papers)
Handling motion, temporal consistency, and dynamic objects.

<details>
<summary>View papers in this category</summary>

- **Motion Modeling**: Easi3R, MonST3R, POMATO, D²USt3R
- **Temporal Consistency**: CUT3R, Align3R
- **4D Reconstruction**: Geo4D, Stereo4D
- **Human/Scene**: ODHSR

</details>

### ✨ [Gaussian Splatting](docs/gaussian-splatting/) (7 papers)
Integration with 3D Gaussian Splatting for neural rendering and novel view synthesis.

<details>
<summary>View papers in this category</summary>

- **Core Integration**: Splatt3R, EasySplat, PreF3R
- **Fast Reconstruction**: InstantSplat
- **Dynamic Filtering**: DAS3R
- **Avatars**: Avat3R

</details>

### 🧠 [Scene Understanding](docs/understanding/) (2 papers)
Semantic integration and multi-view consistency evaluation.

### 🔍 [Scene Reasoning](docs/reasoning/) (2 papers)
Advanced geometric reasoning and amodal completion.

### 🏥 [Medical Applications](docs/medical/) (1 paper)
Specialized applications in medical imaging.

### 📍 [Pose Estimation](docs/pose/) (2 papers)
Camera relocalization and 6D object pose estimation.

## 📊 Key Comparisons

### Performance Overview (DTU Dataset)
| Model | Type | Accuracy ↓ | Completeness ↓ | F-Score ↑ | Speed |
|-------|------|------------|-----------------|-----------|--------|
| COLMAP | Traditional | 0.812 | 0.94 | 0.721 | Minutes |
| DUSt3R | Feed-forward | 0.923 | 0.96 | 0.689 | ~10s |
| MASt3R | Feed-forward | 0.760 | 0.88 | 0.714 | ~7s |
| **VGGT** | **Unified** | **0.677** | **0.72** | **0.798** | **0.2s** |
| MV-DUSt3R+ | Single-stage | 0.640 | 0.72 | 0.798 | ~2s |

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
- **DUSt3R**: [`naver/dust3r`](https://github.com/naver/dust3r)
- **MASt3R**: [`naver/mast3r`](https://github.com/naver/mast3r)
- **MonST3R**: [`Junyi42/MonST3R`](https://github.com/Junyi42/MonST3R)
- **VGGT**: [`facebookresearch/vggt`](https://github.com/facebookresearch/vggt)

### Getting Started
```bash
# Quick installation
pip install dust3r

# Basic usage
from dust3r import DUSt3R
model = DUSt3R.from_pretrained("naver/DUSt3R_ViTLarge_BaseDecoder_512_dpt")
```


## 📋 Papers Database

### By Publication Year
- **2025**: 30 papers (CVPR, ICCV, ICLR, 3DV, arXiv)
- **2024**: 10 papers (CVPR, ECCV, NeurIPS, RAL, arXiv)
- **2023**: 1 paper (ICCV)
- **2022**: 1 paper (NeurIPS)

### By Application Domain
- **General 3D Reconstruction**: 14 papers
- **Dynamic Scenes**: 9 papers  
- **Gaussian Splatting**: 7 papers
- **Scene Understanding/Reasoning**: 4 papers
- **Pose Estimation**: 2 papers
- **Medical Applications**: 1 paper

[📄 Complete Papers List](docs/papers-complete.md)

## 🌟 Featured Research Highlights

### 🏆 Most Influential
**DUSt3R** (CVPR 2024) - The paper that started it all, enabling end-to-end 3D reconstruction from uncalibrated images.

### 🎯 Dynamic Scene Breakthrough
**POMATO** (arXiv 2025) - Marries pointmap matching with temporal motion, addressing DUSt3R's limitations in dynamic scenes through explicit matching relationships and temporal consistency.

### 🚀 Latest Breakthroughs
- **VGGT** (CVPR 2025 Best Paper) - 45× faster unified 3D vision
- **MV-DUSt3R+** (CVPR 2025) - 2-second reconstruction from sparse views
- **Light3R-SfM** (CVPR 2025) - 49× speedup over traditional SfM
- **PreF3R** (arXiv 2024) - Real-time feed-forward Gaussian Splatting

### 💡 Most Promising Directions
- **Temporal Consistency** in dynamic scenes
- **Large-scale** city-level reconstruction  
- **Integration** with language models

## 📚 Learning Resources

### Key Resources
- [🔬 Foundation Papers](docs/foundation/) - Start with DUSt3R and MASt3R
- [📊 Complete Papers List](docs/papers-complete.md) - All 42 documented papers
- [🏷️ Browse by Category](#research-categories) - Find papers by application

## 🤝 Contributing

We welcome contributions from the research community! 

### How to Contribute
1. **Add new papers**: Submit a pull request with documentation
2. **Update benchmarks**: Share new experimental results
3. **Fix errors**: Report issues or submit corrections
4. **Improve documentation**: Enhance existing content

### Recent Contributors
Thanks to all researchers who have contributed to this survey! 🙏

## 📞 Contact & Citation

### Citation
If you find this survey useful for your research, please cite:
```bibtex
@misc{dust3r_survey_2025,
  title={DUSt3R and Extensions: A Comprehensive Survey},
  author={minoTrey},
  year={2025},
  url={https://github.com/minoTrey/DUSt3R-and-Extensions-Survey}
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
