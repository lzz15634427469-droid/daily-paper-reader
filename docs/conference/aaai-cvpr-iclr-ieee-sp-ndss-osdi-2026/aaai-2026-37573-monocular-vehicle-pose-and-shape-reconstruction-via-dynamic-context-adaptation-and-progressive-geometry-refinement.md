---
title: Monocular Vehicle Pose and Shape Reconstruction via Dynamic Context Adaptation and Progressive Geometry Refinement
title_zh: 基于动态上下文自适应与渐进几何精化的单目车辆姿态与形状重建
authors: "Wei Li, Long Ji, Ying Wang, Xiao Wu, Zhaoquan Yuan, Penglin Dai"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37573/41535"
tags: ["query:pe"]
score: 7.0
evidence: 单目图像车辆姿态与形状重建，其技术路线可迁移至单目航天器位姿估计
tldr: 单目车辆三维姿态与形状重建在远距离和深度歧义下存在几何结构不完整等问题。MonoVPR设计了层级双上下文注意力，通过门控交叉注意力融合多尺度特征，并结合渐进式几何精化逐步恢复精确位姿与形状。实验表明该方法能改善远景车辆的重建质量。该框架面向单目图像，其动态上下文与渐进精化策略可借鉴到单目航天器相对位姿估计。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有单目车辆位姿形状重建存在深度估计几何歧义与结构空洞，尤其远距离目标准确度不足。
method: 提出MonoVPR，用层级双上下文注意力融合多尺度特征，并结合渐进几何精化框架逐步优化位姿与形状。
result: 在远处、复杂尺度场景中相比已有方法更准确地恢复车辆位姿与三维形状。
conclusion: 验证了动态上下文融合与渐进式几何精化对单目位姿重建的有效性，可推广至其他刚性目标位姿估计。
---

## Abstract
Accurate reconstruction of 3D vehicle pose and shape from monocular images is challenging, particularly for distant objects in autonomous driving. Existing methods often suffer from geometric ambiguity in depth estimation and structural hollowness in shape recovery, primarily due to inadequate multi-scale feature aggregation and unflexible prior modeling. To overcome these limitations, MonoVPR is proposed, a novel framework integrating dynamic context adaptation and progressive geometry refinement. Specifically, a Hierarchical Dual-Context Attention (HDCA) module is introduced to resolve scale-dependent degradation through gated cross-attention across multi-resolution feature maps, dynamically fusing object-centric geometric cues with scene-centric semantics. For shape refinement, the Bounded Iterative Mesh Refiner (BIMR) progressively optimizes template-guided deformations via multi-head attention and a tanh-bounded correction loop, ensuring physically plausible reconstructions.Extensive experiments on the ApolloCar3D benchmark demonstrate MonoVPR achieves state-of-the-art performance, showing exceptional capability in reconstructing geometrically consistent shapes and precise poses for challenging long-range scenarios.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
单目图像车辆姿态与形状重建，其技术路线可迁移至单目航天器位姿估计。

### 2. 核心内容
单目车辆三维姿态与形状重建在远距离和深度歧义下存在几何结构不完整等问题。MonoVPR设计了层级双上下文注意力，通过门控交叉注意力融合多尺度特征，并结合渐进式几何精化逐步恢复精确位姿与形状。实验表明该方法能改善远景车辆的重建质量。该框架面向单目图像，其动态上下文与渐进精化策略可借鉴到单目航天器相对位姿估计。

### 3. 对应检索需求
How to perform spacecraft pose estimation from monocular imagery?

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37573](https://ojs.aaai.org/index.php/AAAI/article/view/37573)
