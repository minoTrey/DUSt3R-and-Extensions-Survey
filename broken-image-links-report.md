# Broken Image Links Report

## Summary

I analyzed 34 unique image URLs across the documentation files and found **11 broken links** (404 errors) out of 34 total images, representing a **32.4% failure rate**.

## Status Overview

- ✅ **Working Images**: 23 (67.6%)
- ❌ **Broken Images**: 11 (32.4%)

## Broken Image Links

### 1. ReLoc3R Architecture
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/pose/reloc3r.md`
**Broken URL**: `https://github.com/ffrivera0/reloc3r/raw/main/assets/architecture.png`
**Status**: 404 - Not Found

**Alternative Source**: The architecture diagram can be found in the ArXiv paper (2412.08376). The paper describes Figure 2 showing ReLoc3R's two modules: a relative camera pose regression network and a motion averaging module. The architecture consists of a ViT-Large encoder, ViT-Base decoder, and regression head built on DUSt3R's backbone.

### 2. Spann3R Architecture
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/spann3r.md`
**Broken URL**: `https://hengyiwang.github.io/projects/spanner/images/architecture.png`
**Status**: 404 - Not Found

**Alternative Source**: The project page (https://hengyiwang.github.io/projects/spanner) and GitHub repository (https://github.com/HengyiWang/spann3r) contain architecture details. Spann3R uses a transformer-based architecture with external spatial memory, ViT encoder, memory encoder, and dual decoders.

### 3. SLAM3R Architecture
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/slam3r.md`
**Broken URL**: `https://github.com/PKU-VCL-3DV/SLAM3R/raw/main/assets/architecture.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/PKU-VCL-3DV/SLAM3R) and ArXiv paper (2412.09401). SLAM3R uses a two-hierarchy framework with Images-to-Points (I2P) network and Local-to-World (L2W) network, both built on DUSt3R architecture.

### 4. LaRI Overview
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reasoning/lari.md`
**Broken URL**: `https://github.com/ruili3/lari/raw/main/assets/teaser.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/ruili3/lari) contains project information. LaRI (Layered Ray Intersections) is a single-feed-forward method for 3D geometric reasoning from single images using layered point maps.

### 5. SPARS3R Overview
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/spars3r.md`
**Broken URL**: `https://github.com/snldmt/SPARS3R/raw/main/assets/overview.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/snldmt/SPARS3R) and ArXiv paper (2411.12592). SPARS3R uses semantic prior alignment and regularization for sparse 3D reconstruction with global fusion alignment and semantic outlier alignment steps.

### 6. Pow3R Overview
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/pow3r.md`
**Broken URL**: `https://github.com/naver/pow3r/raw/main/assets/overview.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/naver/pow3r) and ArXiv paper (2503.17316). Pow3R is a multi-modal 3D vision regression model that incorporates camera and scene priors for unconstrained 3D reconstruction.

### 7. MUSt3R Architecture
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/must3r.md`
**Broken URL**: `https://github.com/naver/must3r/raw/main/assets/must3r_archi.jpg`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/naver/must3r) and ArXiv paper (2503.01661). MUSt3R uses a symmetric architecture extending DUSt3R with multi-layer memory mechanism for multi-view stereo reconstruction.

### 8. Fast3R Teaser
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/fast3r.md`
**Broken URL**: `https://github.com/facebookresearch/fast3r/raw/main/assets/fast3r_teaser.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/facebookresearch/fast3r), project page (https://fast3r-3d.github.io/), and ArXiv paper (2501.13928). Fast3R processes 1000+ images in one forward pass for 3D reconstruction.

### 9. MASt3R-SLAM Overview
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/reconstruction/mast3r-slam.md`
**Broken URL**: `https://github.com/rmurai0610/MASt3R-SLAM/raw/main/assets/overview.png`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/rmurai0610/MASt3R-SLAM) and project page (https://edexheim.github.io/mast3r-slam/). MASt3R-SLAM is a real-time dense SLAM system built on MASt3R priors.

### 10. MASt3R-SfM Pipeline
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/foundation/mast3r-sfm.md`
**Broken URL**: `https://github.com/naver/mast3r/raw/main/assets/mast3r_sfm.jpg`
**Status**: 404 - Not Found

**Alternative Source**: GitHub repository (https://github.com/naver/mast3r) with mast3r_sfm branch and ArXiv paper (2409.19152). MASt3R-SfM is a fully-integrated Structure-from-Motion pipeline.

### 11. CroCo v2 Predictions
**File**: `/home/mino/workspace/DUSt3R-and-Extensions-Survey/docs/foundation/croco-v2.md`
**Broken URL**: `https://raw.githubusercontent.com/naver/croco/main/assets/predictions.jpg`
**Status**: 404 - Not Found

**Alternative Source**: The correct path should be `https://raw.githubusercontent.com/naver/croco/master/assets/predictions.jpg` (using "master" instead of "main" branch). GitHub repository (https://github.com/naver/croco) contains the CroCo v2 implementation.

## Working Images (23 total)

All other images are accessible and working correctly, including:
- POMATO, ODHSR, InstantSplat, Easi3R, Test3R, Geo4D, Endo3R
- DAS3R (main, davis.gif, sintel.gif), CUT3R, AVAT3R, Align3R
- MonST3R, RaySt3R, D²USt3R, VGGT, CroCo, MV-DUSt3R+
- Light3R, DUSt3R, MASt3R, Stereo4D

## Recommendations

1. **Fix Broken Links**: Contact repository owners or update documentation to use correct URLs
2. **Use Alternative Sources**: Replace broken GitHub raw links with project pages or ArXiv figures
3. **Regular Monitoring**: Implement periodic checks for image link availability
4. **Local Backup**: Consider maintaining local copies of critical images
5. **Branch Correction**: Fix the CroCo v2 link to use "master" instead of "main" branch

## Files Affected

The broken images span across multiple documentation files:
- Foundation models: 3 broken images
- Reconstruction methods: 6 broken images  
- Pose estimation: 1 broken image
- Reasoning methods: 1 broken image

This represents a significant documentation maintenance issue that should be addressed to improve user experience and ensure proper visualization of the surveyed methods.