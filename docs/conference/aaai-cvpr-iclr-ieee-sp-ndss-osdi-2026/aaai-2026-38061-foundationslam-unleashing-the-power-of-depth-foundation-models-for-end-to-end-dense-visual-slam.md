---
title: "FoundationSLAM: Unleashing the Power of Depth Foundation Models for End-to-End Dense Visual SLAM"
title_zh: FoundationSLAM：利用深度基础模型实现端到端稠密单目SLAM
authors: "Yuchen Wu, Jiahe Li, Fabio Tosi, Matteo Poggi, Jin Zheng, Xiao Bai"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38061/42023"
tags: ["query:pe"]
score: 5.0
evidence: 基于单目图像的稠密SLAM同时估计位姿与深度，可作为单目航天器相对位姿估计的技术参考
tldr: 基于光流的单目稠密SLAM缺少几何一致性，导致位姿与深度估计在跨关键帧时不够稳定。FoundationSLAM利用深度基础模型引导混合光流网络产生几何感知对应，并提出双一致束调整层联合优化关键帧位姿与深度，同时引入可靠性感知精化模块。实验显示其在单目跟踪与稠密建图上的几何一致性与鲁棒性相比先前方法显著提升。该框架为单目相机在空间环境中的位姿估计提供了可借鉴的深度-几何结合范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 单目稠密SLAM中纯光流方法缺乏几何一致性，跟踪与建图精度和鲁棒性受限。
method: 提出以深度基础模型引导混合光流网络，并用双一致束调整层联合优化关键帧位姿与深度，附可靠性感知精化。
result: 跨关键帧的深度与位姿估计更具一致性，单目稠密SLAM的准确性和鲁棒性得到增强。
conclusion: 探索基础深度模型结合几何优化进行单目定位与建图，可为空间目标单目位姿估计提供重要支撑。
---

## Abstract
We present FoundationSLAM, a learning-based monocular dense SLAM system that addresses the absence of geometric consistency in previous flow-based approaches for accurate and robust tracking and mapping.
Our core idea is to bridge flow estimation with geometric reasoning by leveraging the guidance from foundation depth models. 
To this end, we first develop a Hybrid Flow Network that produces geometry-aware correspondences, enabling consistent depth and pose inference across diverse keyframes. 
To enforce global consistency, we propose a Bi-Consistent Bundle Adjustment Layer that jointly optimizes keyframe pose and depth under multi-view constraints. Furthermore, we introduce a Reliability-Aware Refinement mechanism that dynamically adapts the flow update process by distinguishing between reliable and uncertain regions, forming a closed feedback loop between matching and optimization.
Extensive experiments demonstrate that FoundationSLAM achieves superior trajectory accuracy and dense reconstruction quality across multiple challenging datasets, while running in real-time at 18 FPS, demonstrating strong generalization to various scenarios and practical applicability of our method.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
基于单目图像的稠密SLAM同时估计位姿与深度，可作为单目航天器相对位姿估计的技术参考。

### 2. 核心内容
基于光流的单目稠密SLAM缺少几何一致性，导致位姿与深度估计在跨关键帧时不够稳定。FoundationSLAM利用深度基础模型引导混合光流网络产生几何感知对应，并提出双一致束调整层联合优化关键帧位姿与深度，同时引入可靠性感知精化模块。实验显示其在单目跟踪与稠密建图上的几何一致性与鲁棒性相比先前方法显著提升。该框架为单目相机在空间环境中的位姿估计提供了可借鉴的深度-几何结合范式。

### 3. 对应检索需求
How to perform spacecraft pose estimation from monocular imagery?

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/38061](https://ojs.aaai.org/index.php/AAAI/article/view/38061)
