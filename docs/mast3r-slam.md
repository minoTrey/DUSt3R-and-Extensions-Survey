# MASt3R-SLAM: Real-Time Dense SLAM with 3D Reconstruction Priors

## Paper Details

**Title:** MASt3R-SLAM: Real-Time Dense SLAM with 3D Reconstruction Priors

**Authors:**
- Riku Murai
- Eric Dexheimer
- Andrew J. Davison

**Affiliations:** All authors are affiliated with Imperial College London

**Publication:** CVPR 2025 (Accepted as Highlight)

**Links:**
- Paper: [https://arxiv.org/abs/2412.12392](https://arxiv.org/abs/2412.12392)
- Project Page: [https://edexheim.github.io/mast3r-slam/](https://edexheim.github.io/mast3r-slam/)
- GitHub: [https://github.com/rmurai0610/MASt3R-SLAM](https://github.com/rmurai0610/MASt3R-SLAM)

## Key Contributions

MASt3R-SLAM combines the MASt3R two-view 3D reconstruction prior with SLAM to create a real-time monocular dense SLAM system with several key innovations:

1. **First Real-Time Integration:** First pipeline to fully integrate a two-view 3D prior into a realtime incremental SLAM system
2. **Camera Model Flexibility:** Operates without assuming a fixed camera model, supporting time-varying camera models (e.g., dynamic zooming)
3. **Robust Performance:** Achieves robust performance on in-the-wild video sequences
4. **Global Consistency:** Produces globally-consistent poses and dense geometry at 15 FPS
5. **Plug-and-Play System:** Functions as a plug-and-play monocular SLAM system requiring only a unique camera center

## Technical Approach

### Core Architecture

MASt3R-SLAM is built "bottom-up from MASt3R" and introduces efficient methods for:

1. **Pointmap Matching:**
   - Massively parallel matching by minimizing angular error between camera rays
   - Achieves matching time of just 2ms with GPU-accelerated CUDA kernels
   - ~40x faster than standard MASt3R matching (2ms vs 2 seconds)

2. **Camera Tracking and Local Fusion:**
   - Generic central camera model by normalizing pointmaps into rays
   - Enables SLAM with time-varying camera models
   - Removes reliance on predefined intrinsic calibration

3. **Graph Construction and Loop Closure:**
   - Standard graph construction similar to DUSt3R or MASt3R-SfM
   - Efficient loop closure detection and optimization

4. **Second-Order Global Optimization:**
   - Uses Gauss-Newton optimization for efficient large-scale updates
   - Pose Graph optimization adjusts only camera poses (unlike Bundle Adjustment)

### How MASt3R Enhances SLAM

1. **Strong 3D Priors:** Leverages MASt3R's pointmap predictions and per-pixel feature confidences
2. **Robustness:** The two-view 3D reconstruction prior enables robust performance on challenging sequences
3. **Dense Reconstruction:** Produces high-quality dense geometry alongside accurate poses
4. **Feature Quality:** MASt3R's matching capabilities provide reliable correspondences for tracking

## Differences from SLAM3R

### MASt3R-SLAM vs SLAM3R Comparison

| Aspect | MASt3R-SLAM | SLAM3R |
|--------|-------------|---------|
| **Core Approach** | Built on MASt3R priors with optimization | End-to-end neural networks |
| **Frame Rate** | 15 FPS | 20+ FPS |
| **Camera Model** | Highly flexible, supports time-varying models | Standard monocular RGB |
| **Optimization** | Gauss-Newton with pose graph optimization | Avoids explicit parameter solving |
| **Architecture** | Two-view 3D prior integration | Feed-forward networks with sliding window |
| **Drift Handling** | Traditional optimization-based | Neural network-based drift control |

### Key Distinctions

1. **Philosophy:** MASt3R-SLAM leverages strong 3D reconstruction priors with efficient optimization, while SLAM3R takes a direct neural approach
2. **Flexibility:** MASt3R-SLAM offers exceptional camera model flexibility
3. **Speed:** SLAM3R achieves slightly higher frame rates but MASt3R-SLAM provides more flexibility

## Performance Metrics

### Real-Time Capabilities
- **Frame Rate:** 15 FPS on RTX 4090
- **Tracking Speed:** >20 FPS for frame tracking
- **Matching Time:** 2ms (GPU-accelerated)
- **Network Runtime:** Encoder/decoder consume ~64% of total runtime

### Benchmark Results

#### 7-Scenes Dataset
- State-of-the-art trajectory accuracy
- Superior dense geometry reconstruction
- Handles varying trajectory complexities effectively

#### EuRoC Dataset
- Competitive performance despite dataset challenges (aggressive motion, large-scale trajectories)
- Without calibration: weighted fusion improves ATE by 1.3cm
- **Dense Reconstruction:** Produces more coherent geometry with better RMSE Chamfer distance than DROID-SLAM
- Fewer outliers compared to DROID-SLAM

### Performance Advantages
1. Outperforms ORB-SLAM iterations and DROID-SLAM
2. Nearly 40x faster matching than standard MASt3R
3. Superior reconstruction quality with fewer outliers
4. Robust performance in uncalibrated scenarios

## Advantages of Using MASt3R Priors

1. **Robustness:** Strong two-view 3D reconstruction prior enables handling of challenging sequences
2. **Dense Geometry:** High-quality dense reconstruction alongside pose estimation
3. **Feature Quality:** MASt3R's advanced matching provides reliable correspondences
4. **Generalization:** Works on in-the-wild video sequences without scene-specific training
5. **Camera Flexibility:** No fixed camera model assumptions enable diverse applications

## Code Availability

### Repository Information
- **GitHub:** [https://github.com/rmurai0610/MASt3R-SLAM](https://github.com/rmurai0610/MASt3R-SLAM)
- **License:** Open-source
- **Status:** Publicly available

### Requirements
- Python 3.11
- CUDA-compatible GPU (tested on RTX 4090)
- PyTorch 2.5.1
- CUDA 11.8, 12.1, or 12.4

### Key Dependencies
- MASt3R
- MASt3R-SfM
- DROID-SLAM
- ModernGL

### Supported Datasets
- TUM-RGBD
- 7-Scenes
- EuRoC
- ETH3D SLAM
- Custom videos and image sequences
- Live camera feeds (e.g., RealSense)

### Installation
```bash
conda create -n mast3r-slam python=3.11
conda activate mast3r-slam
git clone https://github.com/rmurai0610/MASt3R-SLAM.git --recursive
pip install -e thirdparty/mast3r
pip install -e thirdparty/in3d
pip install --no-build-isolation -e .
```

### Usage Examples
```bash
# Run on TUM-RGBD dataset
python main.py --dataset datasets/tum/rgbd_dataset_freiburg1_room/ --config config/calib.yaml

# Live demo with RealSense
python main.py --dataset realsense --config config/base.yaml

# Process video
python main.py --dataset path/to/video.mp4 --config config/base.yaml
```

## Summary

MASt3R-SLAM represents a significant advancement in real-time dense SLAM by successfully integrating MASt3R's powerful two-view 3D reconstruction priors into a real-time system. The combination enables robust performance on challenging sequences while maintaining competitive speed (15 FPS) and producing high-quality dense reconstructions. Its flexibility with camera models and strong performance on standard benchmarks make it a valuable contribution to the SLAM community.