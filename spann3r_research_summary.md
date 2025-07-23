# Spann3R: 3D Reconstruction with Spatial Memory - Research Summary

## Paper Details

**Title**: 3D Reconstruction with Spatial Memory  
**Conference**: 3DV 2025 (International Conference on 3D Vision)  
**Authors**: Hengyi Wang, Lourdes Agapito  
**Affiliation**: Department of Computer Science, University College London  
**Paper**: arXiv:2408.16061 (2024)  

## Key Contributions

### 1. External Spatial Memory Mechanism

Spann3R introduces a novel external spatial memory system that fundamentally differs from previous approaches:

- **Dense Working Memory**: Stores features from the most recent 5 frames with similarity checks to discard redundant features
- **Sparse Long-Term Memory**: Accumulates features over time with sparsification for memory efficiency
- **Memory Query Mechanism**: Uses cross-attention where query features retrieve information from memory keys and values

The memory encoding process involves:
- Memory key features: `f^{t-1}_K = head_{key}^{ref}(f^{t-1}_H, f^{t-1}_I)`
- Memory value features: `f^{t-1}_V = Encoder_V(X^{t-1}) + f^{t-1}_K`
- Attention mechanism: `f_G^{t-1} = A^{t-1}f_V + f_Q^{t-1}`

### 2. Technical Approach for Globally Aligned Pointmaps

The core innovation is generating pointmaps directly in a global coordinate system:

1. **Sequential Processing**: For each time step, Spann3R takes a new frame and previous query feature
2. **Memory Reading**: Query feature reads from spatial memory to generate fused features
3. **Dual Decoder Architecture**: Fused feature and visual feature feed into reference and target decoders
4. **Memory Update**: Reference decoder outputs are encoded into spatial memory
5. **Query Propagation**: Target decoder features become query features for next timestep

This eliminates the need for optimization-based global alignment required by DUSt3R.

### 3. Architecture Components

- **ViT Encoder**: Following DUSt3R architecture with two intertwined decoders
- **Lightweight Memory Encoder**: Additional transformer-based encoder for previous 3D information
- **MLP Heads**: Project geometric features into query features and memory keys
- **No Camera Information Required**: Works without any prior knowledge of scene or camera parameters

## How It Differs from MUSt3R's Memory Approach

### Spann3R vs MUSt3R Key Differences:

1. **Memory Structure**:
   - **Spann3R**: Uses external spatial memory with dense working + sparse long-term components
   - **MUSt3R**: Implements multi-layer memory with layerwise token storage across all transformer layers

2. **Coordinate System**:
   - **Spann3R**: Predicts pointmaps directly in global coordinates from the start
   - **MUSt3R**: Also uses unified coordinate system but with different memory integration

3. **Architecture**:
   - **Spann3R**: Retains pairwise structure with memory augmentation
   - **MUSt3R**: Extends beyond pairwise limitations with symmetric architecture

4. **Performance Trade-offs**:
   - **Spann3R**: Optimizes for speed (>50 FPS) with some accuracy trade-off
   - **MUSt3R**: Better accuracy but more computationally intensive

## Performance Metrics and Scalability

### Speed Performance
- **Real-time capability**: Over 50 FPS for online reconstruction
- **GPU Memory**: ~11GB usage
- **Memory capacity**: Handles up to 4000 memory tokens effectively

### Accuracy Benchmarks

**7Scenes Dataset**:
- Mean Accuracy: 0.0342 (vs DUSt3R: 0.0286)
- Median Accuracy: 0.0148
- Normal Consistency: 0.6635

**NRGBD Dataset**:
- Mean Accuracy: 0.0691
- Normal Consistency: 0.7775

### Scalability Features
- No test-time optimization required
- Single forward pass per image
- Supports both ordered and unordered image collections
- Dynamic scene reconstruction capability (v1.01)

### Training Data (v1.01)
Trained on 10-frame sequences from 15 datasets:
- ScanNet, ScanNetpp, WildRGBD, Co3D, Aria
- ArkitScene, BlendMVS, Waymo, Tartanair
- OmniObject3d, Megadepth, Vkitti2, Unreal, Spring, Pointodyssey

## Code Availability

The implementation is fully open-source:

- **GitHub Repository**: https://github.com/HengyiWang/spann3r
- **Project Page**: https://hengyiwang.github.io/projects/spanner
- **Installation**: 
  ```bash
  conda create -n spann3r python=3.9 cmake=3.14.0
  conda install pytorch==2.3.0 torchvision==0.18.0 torchaudio==2.3.0 pytorch-cuda=11.8 -c pytorch -c nvidia
  ```
- **Features**:
  - Gradio interface for easy interaction
  - Demo scripts and evaluation tools
  - Support for static/dynamic scenes

## Key Advantages

1. **No Camera Information Required**: Works without any scene or camera priors
2. **Real-time Performance**: Achieves >50 FPS for online reconstruction
3. **Global Alignment**: Direct prediction in global coordinates without post-processing
4. **Generalization**: Strong performance on unseen datasets
5. **Memory Efficiency**: Intelligent memory management with working/long-term split

## Limitations

- Struggles with large-scale multi-room scene reconstruction
- Limited by training data resolution and sequence length
- Potential drift in complex scenarios without bundle adjustment
- Memory constraints for very long sequences

## Citation

```bibtex
@article{wang20243d,
  title={3D Reconstruction with Spatial Memory},
  author={Wang, Hengyi and Agapito, Lourdes},
  journal={arXiv preprint arXiv:2408.16061},
  year={2024}
}
```

## Summary

Spann3R represents a significant advancement in 3D reconstruction by introducing an external spatial memory mechanism that enables real-time, incremental reconstruction without requiring camera information or optimization-based alignment. While it trades some accuracy for speed compared to methods like MUSt3R, its ability to process sequences at >50 FPS while maintaining competitive accuracy makes it particularly suitable for real-time applications and online reconstruction scenarios.