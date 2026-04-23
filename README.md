# Awesome LiDAR-Camera Calibration (2023–2026)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
[![Awesome](https://cdn.rawgit.com/sindresorhus/awesome/d7305f38d29fed78fa85652e3a63e154dd8e8829/media/badge.svg)](https://github.com/sindresorhus/awesome)
[![PR's Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat)](http://makeapullrequest.com)


A curated list of **recent (2023 – 2026) LiDAR–Camera extrinsic calibration** papers, toolboxes, and resources.

> Inspired by and complementary to [Deephome/Awesome-LiDAR-Camera-Calibration](https://github.com/Deephome/Awesome-LiDAR-Camera-Calibration) — this repo focuses on the newest works (roughly 2023 → 2026) that are not yet indexed there, including foundation-model / SAM / NeRF / 3D Gaussian Splatting based calibration, BEV-based methods, and joint Camera–LiDAR–Radar / Event camera calibration.

---

## Table of Contents

- [Surveys & Reviews](#surveys--reviews)
- [Target-based Methods](#target-based-methods)
- [Targetless Methods](#targetless-methods)
    - [Motion-based](#motion-based)
    - [Scene / Edge / Intensity-based](#scene--edge--intensity-based)
    - [Deep Learning-based](#deep-learning-based)
    - [Foundation Models / SAM / NeRF / 3D Gaussian Splatting](#foundation-models--sam--nerf--3d-gaussian-splatting)
- [Online / Continuous Calibration](#online--continuous-calibration)
- [Multi-sensor Joint Calibration](#multi-sensor-joint-calibration)
    - [LiDAR–Camera–IMU](#lidarcameraimu)
    - [LiDAR–Camera–Radar](#lidarcameraradar)
    - [LiDAR–Camera–Event](#lidarcameraevent)
- [Toolboxes](#toolboxes)
- [Contributing](#contributing)

---

## Surveys & Reviews

| Year | Title | Venue | Links |
|------|-------|-------|-------|
| 2024 | **Survey of Extrinsic Calibration on LiDAR-Camera System for Intelligent Vehicle: Challenges, Approaches, and Trends** | IEEE T-ITS | [paper](https://doi.org/10.1109/TITS.2024.3419758) |
| 2024 | **A Review of Deep Learning-Based LiDAR and Camera Extrinsic Calibration** | Sensors (MDPI) | [paper](https://www.mdpi.com/1424-8220/24/12/3878) |
| 2025 | **Camera, LiDAR, and IMU Spatiotemporal Calibration: Methodological Review and Research Perspectives** | Sensors (MDPI) | [paper](https://pmc.ncbi.nlm.nih.gov/articles/PMC12431046/) |
| 2023 | **Deep Learning for Camera Calibration and Beyond: A Survey** | arXiv:2303.10559 | [paper](https://arxiv.org/abs/2303.10559) |

---

## Target-based Methods

Calibration using dedicated targets (checkerboards, ArUco, custom 3D objects).

- **Extrinsic Calibration of Camera and LiDAR Systems With Three-Dimensional Towered Checkerboards** (2024, Int. J. Intelligent Systems), Ren et al. [paper](https://onlinelibrary.wiley.com/doi/full/10.1155/2024/2478715)
  - 3D towered checkerboard (3TC) target designed for robust camera–LiDAR extrinsic estimation.

- **One target to align them all: LiDAR, RGB and event cameras extrinsic calibration for Autonomous Driving** (2026, arXiv:2511.12291), [paper](https://arxiv.org/abs/2511.12291)
  - Single multi-modal target that jointly calibrates event camera + RGB + LiDAR rigs.

- **A long-range LiDAR–camera extrinsic calibration method for rail transit** (2025, Scientific Reports), [paper](https://www.nature.com/articles/s41598-025-34547-6)
  - Custom long-range calibration target / workflow tailored to railway environments.

- **P2O-Calib: Camera-LiDAR Calibration Using Point-Pair Spatial Occlusion Relationship** (2023, arXiv:2311.02062), Zhu et al. [paper](https://arxiv.org/abs/2311.02062)
  - Uses point-pair occlusion cues around target boundaries for accurate 6-DoF extrinsics.

---

## Targetless Methods

Methods that do **not** require any physical calibration target. Grouped by the core cue they rely on.

### Motion-based

Hand-eye style calibration from ego-motion / odometry.

- **MDPCalib: Automatic Target-Less Camera-LiDAR Calibration From Motion and Deep Point Correspondences** (2024, arXiv:2404.17298), Petek et al. [paper](https://arxiv.org/abs/2404.17298)
  - Combines visual + LiDAR odometry with learned 2D-pixel ↔ 3D-point correspondences in a single optimization; generalizes across car / quadruped / UAV platforms.

- **OA-LICalib: Observability-Aware Intrinsic and Extrinsic Calibration of the Rolling-Shutter Camera and LiDAR-IMU Sensor Suite** (2023, IEEE T-RO), Lv et al. [paper](https://arxiv.org/abs/2201.10346) [code](https://github.com/APRIL-ZJU/OA-LICalib)
  - Continuous-time B-spline trajectory model with observability-aware degeneracy handling.

- **Targetless Intrinsics and Extrinsic Calibration of Multiple LiDARs and Cameras with IMU using Continuous-Time Estimation** (2025, arXiv:2501.02821), [paper](https://arxiv.org/abs/2501.02821)
  - Continuous-time joint calibration of multiple LiDARs + cameras + IMU without targets.

---

### Scene / Edge / Intensity-based

Classical targetless methods based on edge alignment, mutual information, or intensity/reflectance cues.

- **SensorX2car: Sensors-to-Car Calibration for Autonomous Driving in Road Scenarios** (2023, arXiv:2301.07279), Yan et al. [paper](https://arxiv.org/abs/2301.07279) [code](https://github.com/OpenCalib/SensorX2car)
  - Uses road-scene structure (lanes, vanishing points, ground plane) to calibrate LiDAR / camera / radar to the vehicle frame.

- **General, Single-shot, Target-less, and Automatic LiDAR-Camera Extrinsic Calibration Toolbox** (2023, ICRA / arXiv:2302.05094), Koide et al. [paper](https://arxiv.org/abs/2302.05094) [code](https://github.com/koide3/direct_visual_lidar_calibration)
  - Widely-used ROS1/ROS2 toolbox — direct, single-shot, targetless calibration from a single scan + image pair.

- **Pixel-Level Extrinsic Self-Calibration of High-Resolution LiDAR and Camera in Targetless Environments** (IEEE RAL, baseline; arXiv:2103.01627), Yuan et al. [paper](https://arxiv.org/abs/2103.01627) [code](https://github.com/hku-mars/livox_camera_calib)
  - Edge-alignment based targetless calibration (`livox_camera_calib`) — the canonical baseline widely used in 2023–2025 work.

---

### Deep Learning-based

End-to-end / regression / flow-based learning approaches.

- **CalibFormer: A Transformer-based Automatic LiDAR-Camera Calibration Network** (2024, ICRA / arXiv:2311.15241), Xiao et al. [paper](https://arxiv.org/abs/2311.15241)
  - Transformer with multi-layer cross-modal correlation; reports ~0.88 cm / 0.056° on KITTI.

- **UniCalib: Targetless LiDAR-Camera Calibration via Probabilistic Flow on Unified Depth Representations** (2025, arXiv:2504.01416), [paper](https://arxiv.org/abs/2504.01416)
  - Projects both modalities into unified dense depth; learns a probabilistic flow field with uncertainty.

- **BEVCalib: LiDAR-Camera Calibration via Geometry-Guided Bird's-Eye View Representations** (2025, arXiv:2506.02587), [paper](https://arxiv.org/abs/2506.02587)
  - First calibration method operating directly on BEV features from raw data.

- **What Really Matters for Learning-based LiDAR-Camera Calibration** (2025, arXiv:2501.16969), [paper](https://arxiv.org/abs/2501.16969)
  - Systematic ablation revisiting what actually drives accuracy in learning-based LCC.

- **RobustCalib: Robust LiDAR-Camera Extrinsic Calibration with Consistency Learning** (2023, arXiv:2312.01085), [paper](https://arxiv.org/abs/2312.01085)
  - Self-supervised consistency learning for robust extrinsics under sensor noise.

- **Online, Target-Free LiDAR-Camera Extrinsic Calibration via Cross-Modal Mask Matching** (2024, IEEE T-IV / arXiv:2404.18083), Huang et al. [paper](https://arxiv.org/abs/2404.18083)
  - Uses large vision-model masks as cross-modal correspondences for online calibration.

---

### Foundation Models / SAM / NeRF / 3D Gaussian Splatting

Recent wave of calibration methods that leverage foundation models or neural scene representations.

- **Calib-Anything: Zero-training LiDAR-Camera Extrinsic Calibration Method Using Segment Anything** (2024, China Automation Congress / arXiv:2306.02656), Luo et al. [paper](https://arxiv.org/abs/2306.02656) [code](https://github.com/OpenCalib/CalibAnything)
  - SAM masks gate 3D–2D correspondences; **zero extra training**, works on arbitrary scenes.

- **SAM4D: Segment Anything in Camera and LiDAR Streams** (2025, ICCV / arXiv:2506.21547), Xu et al. [paper](https://arxiv.org/abs/2506.21547) [project](https://sam4d-project.github.io/) [code](https://github.com/CN-ADLab/SAM4D)
  - Cross-modal promptable segmentation over camera + LiDAR streams — foundation for cross-modal correspondence / calibration.

- **3DGS-Calib: 3D Gaussian Splatting for Multimodal SpatioTemporal Calibration** (2024, arXiv:2403.11577), Herau et al. [paper](https://arxiv.org/abs/2403.11577)
  - Uses LiDAR points as Gaussian anchors; orders of magnitude faster than NeRF-based calibration with better accuracy.

- **Targetless LiDAR-Camera Calibration with Anchored 3D Gaussians** (a.k.a. *TLC-Calib*) (2025, arXiv:2504.04597), [paper](https://arxiv.org/abs/2504.04597)
  - Jointly optimizes sensor poses + neural-Gaussian scene, using reliable LiDAR points as anchor Gaussians.

- **Robust LiDAR-Camera Calibration with 2D Gaussian Splatting** (2025, arXiv:2504.00525), [paper](https://arxiv.org/abs/2504.00525)
  - 2DGS reconstruction from LiDAR with photometric refinement of extrinsics.

- **MOISST: Multi-modal Optimization of Implicit Scene for SpatioTemporal Calibration** (2023, IROS / arXiv:2303.03056), Herau et al. [paper](https://arxiv.org/abs/2303.03056)
  - NeRF-based joint optimization of poses, LiDAR–camera extrinsics, and time offset.

- **SOAC: Spatio-temporal Overlap-Aware Multi-Sensor Calibration using Neural Radiance Fields** (2024, CVPR / arXiv:2311.15803), Herau et al. [paper](https://arxiv.org/abs/2311.15803)
  - NeRF-based multi-camera + LiDAR calibration exploiting overlapping FoVs.

- **INF: Implicit Neural Fusion for LiDAR and Camera** (2023, IROS / arXiv:2308.14414), Zhou et al. [paper](https://arxiv.org/abs/2308.14414)
  - Implicit neural field for joint LiDAR–camera representation and extrinsic refinement.

---

## Online / Continuous Calibration

Methods that maintain valid extrinsics at runtime / detect miscalibration.

- **CalibRefine: Deep Learning-Based Online Automatic Targetless LiDAR–Camera Calibration with Iterative and Attention-Driven Post-Refinement** (2025, arXiv:2502.17648), [paper](https://arxiv.org/abs/2502.17648)
  - Common-feature discriminator + coarse homography + iterative attention refinement, fully online.

- **EdO-LCEC: Environment-Driven Online LiDAR-Camera Extrinsic Calibration** (2025, arXiv:2502.00801), [paper](https://arxiv.org/abs/2502.00801)
  - First *environment-driven* online calibration — a scene discriminator estimates feature density and adapts extraction.

---

## Multi-sensor Joint Calibration

Calibration methods that go beyond a single LiDAR ↔ Camera pair, jointly handling additional modalities.

### LiDAR–Camera–IMU

- **OA-LICalib** (2023, IEEE T-RO) — see [Motion-based](#motion-based).

- **Targetless Intrinsics and Extrinsic Calibration of Multiple LiDARs and Cameras with IMU using Continuous-Time Estimation** (2025, arXiv:2501.02821), [paper](https://arxiv.org/abs/2501.02821)
  - Continuous-time joint calibration of multi-LiDAR + multi-camera + IMU without targets.

### LiDAR–Camera–Radar

- **CLRNet: Targetless Extrinsic Calibration for Camera, Lidar and 4D Radar Using Deep Learning** (2026, arXiv:2603.15767), [paper](https://arxiv.org/abs/2603.15767)
  - End-to-end joint / pairwise calibration across camera + LiDAR + 4D radar.

- **RLCNet: An end-to-end deep learning framework for simultaneous online calibration of LiDAR, RADAR, and Camera** (2025, arXiv:2512.08262), [paper](https://arxiv.org/abs/2512.08262)
  - Joint LiDAR + RADAR + camera calibration with minimal supervision, real-time capable.

### LiDAR–Camera–Event

- **One target to align them all: LiDAR, RGB and event cameras extrinsic calibration for Autonomous Driving** (2026, arXiv:2511.12291), [paper](https://arxiv.org/abs/2511.12291)
  - Unified multi-modal target for event + RGB + LiDAR calibration.

---

## Toolboxes

| Toolbox | Description | Link |
|---------|-------------|------|
| **OpenCalib / SensorsCalibration** | Full multi-sensor calibration toolbox (targeted & targetless). | [github](https://github.com/PJLab-ADG/SensorsCalibration) / [paper](https://arxiv.org/abs/2205.14087) |
| **CalibAnything** | SAM-based zero-training targetless LiDAR-camera calibration. | [github](https://github.com/OpenCalib/CalibAnything) |
| **SensorX2car** | Road-scene targetless sensor-to-car calibration. | [github](https://github.com/OpenCalib/SensorX2car) |
| **direct_visual_lidar_calibration** | General single-shot targetless LiDAR-camera calibration (ROS1/ROS2). | [github](https://github.com/koide3/direct_visual_lidar_calibration) |
| **livox_camera_calib** | Pixel-level targetless self-calibration (HKU-MARS). | [github](https://github.com/hku-mars/livox_camera_calib) |
| **OA-LICalib** | Observability-aware LiDAR–IMU–Camera continuous-time calibration. | [github](https://github.com/APRIL-ZJU/OA-LICalib) |
| **velo2cam_calibration** | Circular-hole + ArUco target toolbox — long-standing baseline. | [github](https://github.com/beltransen/velo2cam_calibration) |

---

## Contributing

Pull requests are very welcome! Please follow this entry template:

```md
- **Title** (Year, Venue / arXiv:xxxx.xxxxx), Authors. [paper](URL) [code](URL)
  - One-line summary of the contribution.
```

When adding a paper, place it in the most appropriate section (or suggest a new one). If a paper spans categories (e.g., SAM + online), pick the section that best captures its primary contribution and cross-link from the other section.

---

## License

This list is released under [CC0-1.0](https://creativecommons.org/publicdomain/zero/1.0/) — feel free to reuse, remix, and redistribute.
