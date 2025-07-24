# DUSt3R Paper Collection: Curated Research with In-Depth Analysis

[![GitHub Stars](https://img.shields.io/github/stars/minoTrey/DUSt3R-Paper-Collection?style=social)](https://github.com/minoTrey/DUSt3R-Paper-Collection)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Papers](https://img.shields.io/badge/Papers-55-green.svg)](#papers-database)
[![Last Updated](https://img.shields.io/badge/Last%20Updated-July%202025-orange.svg)](#)

> **A curated collection of 55+ research papers on DUSt3R and feed-forward 3D reconstruction**

## 🌟 What is DUSt3R?

[DUSt3R](docs/foundation/dust3r.md) (Dense Uncalibrated Stereo 3D Reconstruction) revolutionized 3D computer vision by enabling **instant 3D reconstruction from uncalibrated images**. Unlike traditional methods requiring camera calibration and iterative optimization, DUSt3R uses a feed-forward neural network to directly predict 3D geometry.

This paper collection tracks the explosive growth of the DUSt3R ecosystem, documenting **55 papers** with in-depth analysis that extend, improve, or apply this groundbreaking technology across diverse domains.

## 🚀 Quick Start

- **New to DUSt3R?** → Start with [📚 Foundation Papers](docs/foundation/README.md)
- **Looking for specific applications?** → Browse by [🏷️ Categories](#research-categories)
- **Want full list?** → See [📄 Complete Papers List](docs/papers-list.md)

## 📈 Research Landscape

DUSt3R has catalyzed a paradigm shift in 3D reconstruction, moving from traditional iterative pipelines to **end-to-end feed-forward models**. This survey tracks the explosive growth of this field:

```
2022 ██ 1 paper   (CroCo)
2023 ██ 1 paper   (CroCo v2)  
2024 ████████████████████ 17 papers
2025 ████████████████████████████████████████████████████████████████ 35 papers
```

## 🏷️ Research Categories

### 🔬 [Foundation Models](docs/foundation/) (5 papers)
The seminal works that established the feed-forward 3D reconstruction paradigm.

| Paper | Venue | Key Innovation | Best Performance |
|-------|-------|----------------|-----------------|
| [CroCo](docs/foundation/croco.md) | ICCV 2023 | Cross-view completion pretraining | 85.6% on NYUv2 depth |
| [CroCo v2](docs/foundation/croco-v2.md) | CVPR 2024 | Enhanced stereo & optical flow | 1.25 EPE on Sintel (SOTA) |
| **[DUSt3R](docs/foundation/dust3r.md)** ⭐ | CVPR 2024 | **End-to-end 3D reconstruction** | **No calibration needed** |
| [MASt3R](docs/foundation/mast3r.md) | ECCV 2024 | 3D-aware feature matching | 91.4% MMA@10px (SOTA) |
| [MASt3R-SfM](docs/foundation/mast3r-sfm.md) | arXiv 2024 | Complete SfM pipeline | 100% registration T&T |

### 🏗️ [3D Reconstruction](docs/reconstruction/) (18 papers)
Core advances in static scene reconstruction, multi-view consistency, and large-scale scenarios.

<details>
<summary>View papers in this category</summary>

- **🏆 State-of-the-Art**: [π³ (Pi3)](docs/reconstruction/pi3.md) - Permutation-equivariant architecture beats VGGT
- **⚡ Real-time Systems**: [SLAM3R](docs/reconstruction/slam3r.md), [Fast3R](docs/reconstruction/fast3r.md), [MASt3R-SLAM](docs/reconstruction/mast3r-slam.md), [Spann3R](docs/reconstruction/spann3r.md)
- **👁️ Multi-view**: [MUSt3R](docs/reconstruction/must3r.md), [MV-DUSt3R+](docs/reconstruction/mv-dust3r-plus.md), [Light3R-SfM](docs/reconstruction/light3r-sfm.md)  
- **🤖 Foundation Models**: [MoGe](docs/reconstruction/moge.md), [LoRA3D](docs/reconstruction/lora3d.md), [Test3R](docs/reconstruction/test3r.md), [Pow3R](docs/reconstruction/pow3r.md), [Dens3R](docs/reconstruction/dens3r.md)
- **🌍 Large-scale**: [REGIST3R](docs/reconstruction/regist3r.md), [Spurfies](docs/reconstruction/spurfies.md), [ReconX](docs/reconstruction/reconx.md)
- **🎯 Specialized**: [SPARS3R](docs/reconstruction/spars3r.md)

</details>

### 🎬 [Dynamic Scene Reconstruction](docs/dynamic/) (11 papers)
Extending DUSt3R to handle motion, temporal consistency, and 4D understanding.

<details>
<summary>View papers in this category</summary>

- **🏃 Motion Modeling**: [POMATO](docs/dynamic/pomato.md) (ICCV'25), [MonST3R](docs/dynamic/monst3r.md) (ICLR'25), [Easi3R](docs/dynamic/easi3r.md), [D²USt3R](docs/dynamic/d2ust3r.md)
- **⏱️ Temporal Consistency**: [CUT3R](docs/dynamic/cut3r.md), [Align3R](docs/dynamic/align3r.md), [Dynamic Point Maps](docs/dynamic/dynamic-point-maps.md)
- **🎯 4D Reconstruction**: [Geo4D](docs/dynamic/geo4d.md), [Stereo4D](docs/dynamic/stereo4d.md)
- **👥 Specialized**: [ODHSR](docs/dynamic/odhsr.md) (human-scene), [Adapt3R](docs/dynamic/adapt3r.md) (domain adaptation)

</details>

### ✨ [Gaussian Splatting](docs/gaussian-splatting/) (10 papers)
Revolutionizing neural rendering by combining DUSt3R with 3D Gaussian Splatting.

<details>
<summary>View papers in this category</summary>

- **🚀 Core Methods**: [Splatt3R](docs/gaussian-splatting/splatt3r.md) (instant 3DGS), [PreF3R](docs/gaussian-splatting/pref3r.md), [InstantSplat](docs/gaussian-splatting/instantsplat.md) (40s reconstruction)
- **🎨 Quality Enhancement**: [LM-Gaussian](docs/gaussian-splatting/lm-gaussian.md) (foundation model priors), [Dust-GS](docs/gaussian-splatting/dust-gs.md), [Dust to Tower](docs/gaussian-splatting/dust-to-tower.md)
- **🌊 Advanced**: [FlowR](docs/gaussian-splatting/flowr.md) (flow-based), [DAS3R](docs/gaussian-splatting/das3r.md) (dynamic filtering)
- **🎭 Creative**: [Styl3R](docs/gaussian-splatting/styl3r.md) (style transfer), [Avat3R](docs/gaussian-splatting/avat3r.md) (animatable avatars)

</details>

### 🧠 [Scene Understanding](docs/understanding/) (3 papers)
Bridging 3D geometry with semantic understanding and perception.
- **Key Papers**: [PE3R](docs/understanding/pe3r.md) (9× speedup), [MEt3R](docs/understanding/met3r.md) (consistency metric), [LargeSpatialModel](docs/understanding/largespatialmodel.md)

### 🔍 [Scene Reasoning](docs/reasoning/) (3 papers)
Advanced geometric reasoning beyond visible surfaces.
- **Key Papers**: [LaRI](docs/reasoning/lari.md) (layered reasoning), [RaySt3R](docs/reasoning/rayst3r.md) (zero-shot completion), [Amodal3R](docs/reasoning/amodal3r.md) (ICCV'25)

### 🤖 [Robotics](docs/robotics/) (2 papers)
Enabling robotic perception and manipulation.
- **Key Papers**: [RIG3R](docs/robotics/rig3r.md) (grasping), [GraphSeg](docs/robotics/graphseg.md) (segmentation)

### 🏥 [Medical Applications](docs/medical/) (1 paper)
Adapting to challenging medical imaging domains.
- **Key Paper**: [Endo3R](docs/medical/endo3r.md) (dynamic endoscopy)

### 📍 [Pose Estimation](docs/pose/) (2 papers)
Efficient pose regression from DUSt3R's foundation.
- **Key Papers**: [Reloc3R](docs/pose/reloc3r.md) (40 FPS camera pose), [Pos3R](docs/pose/pos3r.md) (zero-shot 6D pose)

## 📊 Key Comparisons & Benchmarks

### 🏆 Performance Overview

#### DTU Dataset (Traditional Metrics)
| Model | Type | Accuracy ↓ | Completeness ↓ | Overall ↓ | Speed | Year |
|-------|------|------------|-----------------|-----------|--------|------|
| [DUSt3R](docs/foundation/dust3r.md) | Feed-forward | 2.667 | 0.805 | 1.741 | ~10s | 2024 |
| **[MASt3R](docs/foundation/mast3r.md)** | **Enhanced** | **0.403** | **0.344** | **0.374** | ~7s | 2024 |
| [Fast3R](docs/reconstruction/fast3r.md) | Speed-optimized | - | - | 1.98 | 0.03s | 2025 |

*Note: Lower is better for all metrics. MASt3R shows 78% improvement over DUSt3R.*

#### Point Map Reconstruction (DTU & ETH3D)
| Model | DTU Acc. ↓ | DTU Comp. ↓ | ETH3D Acc. ↓ | ETH3D Comp. ↓ | Year |
|-------|------------|--------------|---------------|----------------|------|
| [Fast3R](docs/reconstruction/fast3r.md) | 3.340 | 2.929 | 0.832 | 0.978 | 2025 |
| [VGGT](docs/reconstruction/vggt.md) | 1.338 | 1.896 | 0.280 | 0.305 | 2025 |
| **[π³ (Pi3)](docs/reconstruction/pi3.md)** ⭐ | **1.198** | **1.849** | **0.194** | **0.210** | **2025** |

*Note: Lower is better. Pi3 achieves state-of-the-art on both DTU and ETH3D datasets.*

#### Camera Pose Estimation (Zero-shot)
| Model | Sintel ATE ↓ | TUM-dyn ATE ↓ | Co3Dv2 RRA@30 ↑ | Speed | Year |
|-------|--------------|-----------------|-------------------|--------|------|
| [VGGT](docs/reconstruction/vggt.md) | 0.167 | 0.012 | 98.96 | 43.2 FPS | 2025 |
| **[π³ (Pi3)](docs/reconstruction/pi3.md)** ⭐ | **0.074** | **0.014** | **99.05** | **57.4 FPS** | **2025** |

*Pi3: 55% better on Sintel, 33% faster than VGGT, with permutation-equivariant design.*

#### Foundation Models Evolution
| Model | Stereo (Middlebury) | Optical Flow (Sintel) | Feature Matching | 3D Recon (DTU) |
|-------|---------------------|----------------------|------------------|----------------|
| [CroCo](docs/foundation/croco.md) | 5.0 bad@1.0 | 3.00 EPE | - | - |
| [CroCo v2](docs/foundation/croco-v2.md) | **1.82** bad@1.0 | **1.25** EPE | - | - |
| [DUSt3R](docs/foundation/dust3r.md) | - | - | - | 1.741 overall |
| [MASt3R](docs/foundation/mast3r.md) | - | - | **91.4%** MMA@10px | **0.374** overall |

*Foundation models show dramatic improvements: CroCo v2 achieved SOTA on stereo/flow, MASt3R improved 3D reconstruction by 78%.*

### 🔄 Paradigm Comparison
| Aspect | Traditional (COLMAP) | DUSt3R Family | Latest ([Pi3](docs/reconstruction/pi3.md)/[VGGT](docs/reconstruction/vggt.md)) | Benefits |
|--------|---------------------|---------------|-------------------|----------|
| **Workflow** | Multi-stage pipeline | End-to-end | Single forward pass | 100-300× faster |
| **Robustness** | Fails on textureless | Learned priors | Universal | Works everywhere |
| **Speed** | Minutes-hours | 5-10 seconds | 0.03-0.2 seconds | Real-time ready |
| **Calibration** | Required | Not needed | Not needed | Zero setup |
| **Min Images** | 10+ optimal | 2+ sufficient | 2+ sufficient | Flexible input |
| **Accuracy** | High (given texture) | Good | State-of-the-art | Best quality |

## 🛠️ Implementation Resources

### 🌟 Official Implementations
- **[DUSt3R](docs/foundation/dust3r.md)**: [`naver/dust3r`](https://github.com/naver/dust3r) - The original
- **[MASt3R](docs/foundation/mast3r.md)**: [`naver/mast3r`](https://github.com/naver/mast3r) - Enhanced matching
- **[MonST3R](docs/dynamic/monst3r.md)**: [`Junyi42/MonST3R`](https://github.com/Junyi42/MonST3R) - Dynamic scenes
- **[Splatt3R](docs/gaussian-splatting/splatt3r.md)**: [`splatt3r/splatt3r`](https://github.com/splatt3r/splatt3r) - Instant 3DGS
- **[π³ (Pi3)](docs/reconstruction/pi3.md)**: [`yyfz/Pi3`](https://github.com/yyfz/Pi3) - Current SOTA (57.4 FPS)

### 🚀 Quick Start Guide
```bash
# Install DUSt3R
pip install dust3r

# Basic 3D reconstruction
from dust3r.inference import inference
from dust3r.model import AsymmetricCroCo3DStereo
from dust3r.utils.image import load_images

# Load model
model = AsymmetricCroCo3DStereo.from_pretrained("naver/DUSt3R_ViTLarge_BaseDecoder_512_dpt")

# Load images and reconstruct
images = load_images(['img1.jpg', 'img2.jpg'], size=512)
output = inference(pairs=[(images[0], images[1])], model=model)
pts3d = output['pts3d']  # Your 3D points!
```


## 📋 Papers Database

### By Publication Year
- **2025**: 35 papers (CVPR, ICCV, ICLR, 3DV, arXiv)
- **2024**: 17 papers (CVPR, ECCV, NeurIPS, RAL, arXiv)
- **2023**: 1 paper (ICCV)
- **2022**: 1 paper (NeurIPS)

### By Application Domain
- **3D Reconstruction**: 18 papers
- **Dynamic Scenes**: 11 papers  
- **Gaussian Splatting**: 10 papers
- **Scene Understanding/Reasoning**: 6 papers
- **Foundation Models**: 5 papers
- **Pose Estimation**: 2 papers
- **Robotics**: 2 papers
- **Medical Applications**: 1 paper


## 🌟 Featured Research Highlights

### 🏆 Most Influential Papers
1. **[DUSt3R](docs/foundation/dust3r.md)** (CVPR 2024) - The foundation that started the revolution
2. **[MASt3R](docs/foundation/mast3r.md)** (ECCV 2024) - Brought 3D understanding to feature matching
3. **[Splatt3R](docs/gaussian-splatting/splatt3r.md)** (arXiv 2024) - Enabled instant Gaussian Splatting

### 🚀 Latest Breakthroughs (2025)
| Paper | Innovation | Impact |
|-------|------------|--------|
| **[π³ (Pi3)](docs/reconstruction/pi3.md)** | Permutation-equivariant architecture | SOTA on DTU/ETH3D/Sintel |
| **[POMATO](docs/dynamic/pomato.md)** | Pointmap matching + temporal motion | Solves dynamic scenes |
| **[Dens3R](docs/reconstruction/dens3r.md)** | Unified dense geometric prediction | High-quality reconstruction |
| **[VGGT](docs/reconstruction/vggt.md)** | 45× faster processing | Real-time performance |
| **[MonST3R](docs/dynamic/monst3r.md)** | Monocular video tracking | Robust dynamic 3D |

### 💡 Emerging Research Directions
1. **4D Understanding**: Extending to spatiotemporal ([D²USt3R](docs/dynamic/d2ust3r.md), [Geo4D](docs/dynamic/geo4d.md))
2. **Language Integration**: Text-guided 3D reconstruction
3. **Mobile Deployment**: On-device processing ([Fast3R](docs/reconstruction/fast3r.md))
4. **Generative 3D**: Creating new content, not just reconstructing
5. **Unified Models**: One model for all 3D tasks

## 📚 Learning Path & Resources

### 🎓 Recommended Learning Path
1. **Start Here**: [DUSt3R paper](docs/foundation/dust3r.md) - Understand the core innovation
2. **Deep Dive**: [Foundation Models](docs/foundation/) - Learn the fundamentals
3. **Pick Your Interest**:
   - **Neural Rendering** → [Gaussian Splatting](docs/gaussian-splatting/)
   - **Video/Motion** → [Dynamic Scenes](docs/dynamic/)
   - **Applications** → [Robotics](docs/robotics/) or [Medical](docs/medical/)
4. **Latest SOTA**: [π³ (Pi3)](docs/reconstruction/pi3.md) - See cutting edge

### 📖 Additional Resources
- [📊 Complete Papers List](docs/papers-list.md) - All 55 papers with summaries
- [🔍 Search by Topic](#research-categories) - Find specific applications
- [💻 Code Examples](https://github.com/naver/dust3r) - Official tutorials

## 🤝 Contributing

We welcome contributions from the research community! Help us keep this survey comprehensive and up-to-date.

### 📝 How to Contribute

1. **Add New Papers**:
   - Create a markdown file in the appropriate category folder
   - Include: paper summary, key innovations, results, and links
   - Add teaser image/video if available

2. **Update Information**:
   - Fix errors or outdated information
   - Add new benchmark results
   - Update implementation links

3. **Improve Content**:
   - Enhance existing documentation
   - Add tutorials or guides
   - Create comparison tables

### 🎯 Contribution Guidelines
- Use the existing paper template format
- Verify all links work correctly
- Include proper citations
- Be objective and accurate

### 🙏 Acknowledgments
Special thanks to all researchers advancing this field and contributors maintaining this collection!

## 📞 Contact & Citation

### Citation
If you find this survey useful for your research, please cite:
```bibtex
@misc{dust3r_papers_2025,
  title={DUSt3R Paper Collection: Curated Research with In-Depth Analysis},
  author={Min-Ho Lee},
  year={2025},
  url={https://github.com/minoTrey/DUSt3R-Paper-Collection}
}
```

### Connect
- 💬 **Discussions**: [GitHub Discussions](../../discussions)
- 🐛 **Issues**: [GitHub Issues](../../issues)

## 📄 License

This survey is released under the [MIT License](LICENSE). Individual papers retain their original licenses.

## 🔮 Future of DUSt3R

The DUSt3R ecosystem continues to evolve rapidly:

- **Near Term** (2025): Real-time 4D reconstruction, mobile deployment, language integration
- **Medium Term** (2026): Unified 3D-language-video models, generative 3D content
- **Long Term**: Complete spatial AI systems, AR/VR metaverse infrastructure

---

<div align="center">

### **⭐ Star this repo to stay updated with the latest advances! ⭐**

[![GitHub Stars](https://img.shields.io/github/stars/minoTrey/DUSt3R-Paper-Collection?style=social)](https://github.com/minoTrey/DUSt3R-Paper-Collection)
[![Watchers](https://img.shields.io/github/watchers/minoTrey/DUSt3R-Paper-Collection?style=social)](https://github.com/minoTrey/DUSt3R-Paper-Collection)

*Tracking 55 papers and growing | Last updated: July 2025*

**[Submit a Paper](../../issues/new)** | **[Report an Issue](../../issues)** | **[Join Discussion](../../discussions)**

</div>
