# Dynamic Scene Reconstruction

This category covers papers that extend DUSt3R to handle dynamic scenes, temporal consistency, and moving objects.

## Overview

While DUSt3R excels at static scene reconstruction, dynamic scenes present unique challenges:
- **Temporal consistency** across frames
- **Motion estimation** for moving objects
- **Disentangling** camera motion from object motion
- **Scale consistency** throughout sequences

## Key Papers

### Motion Modeling
- **[POMATO](pomato.md)** (arXiv 2025) - Marries pointmap matching with temporal motion
- **[MonST3R](monst3r.md)** (ICLR 2025) - Separate pointmap per timestep
- **[Easi3R](easi3r.md)** (ICCV 2025) - Training-free motion extraction from attention
- **[D²USt3R](d2ust3r.md)** (arXiv 2025) - 4D pointmap regression framework

### Temporal Consistency
- **[CUT3R](cut3r.md)** (CVPR 2025) - Continuous 3D perception with persistent state
- **[Align3R](align3r.md)** (CVPR 2025) - Aligned monocular depth for videos
- **[Dynamic Point Maps](dynamic-point-maps.md)** (arXiv 2025) - Versatile 4D representation

### Human & Object Reconstruction
- **[ODHSR](odhsr.md)** (CVPR 2025) - Joint human and scene reconstruction
- **[Endo3R](endo3r.md)** (arXiv 2025) - Dynamic endoscopic video reconstruction

### 4D Scene Understanding
- **[Geo4D](geo4d.md)** (ICCV 2025) - Video generators for 4D reconstruction
- **[Stereo4D](stereo4d.md)** (CVPR 2025) - Learning motion from internet videos
- **[Adapt3R](adapt3r.md)** (arXiv 2025) - Adaptive scene representation

## Technical Approaches

### 1. Temporal Extension
Methods that extend DUSt3R's architecture to handle time:
- Adding temporal attention modules
- Recurrent processing of frames
- 4D pointmap representations

### 2. Motion Disentanglement
Separating different types of motion:
- Camera motion estimation
- Object motion tracking
- Scene flow computation

### 3. Consistency Enforcement
Ensuring temporal coherence:
- Cross-frame constraints
- Temporal smoothness losses
- Scale-consistent representations

## Challenges & Open Problems

1. **Real-time Performance**: Most methods sacrifice speed for accuracy
2. **Long Sequences**: Memory limitations for extended videos
3. **Complex Motion**: Handling non-rigid deformations
4. **Occlusion Handling**: Maintaining tracks through occlusions

## Benchmarks

Common evaluation datasets:
- **Dynamic Replica**: Synthetic dynamic scenes
- **TartanAir**: Dynamic outdoor environments
- **KITTI**: Real-world driving sequences
- **Sintel**: Synthetic scenes with ground truth flow

## Future Directions

- **Unified 4D Models**: Single model for all spatiotemporal tasks
- **Real-time Systems**: Efficient architectures for online processing
- **Language Integration**: Dynamic scene understanding with language
- **Physics-aware**: Incorporating physical constraints