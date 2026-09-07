---
title: "RCP-LO: A Relative Coordinate Prediction Framework for Generalizable Deep LiDAR Odometry"
title_zh: RCP-LO：面向可泛化深度激光雷达里程计的相对坐标预测框架
authors: "Chen Liu, Wen Li, Yongshu Huang, Minghang Zhu, Yuyang Yang, Dunqiang Liu, Sheng Ao, Cheng Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37643/41605"
tags: ["query:pe"]
score: 4.0
evidence: 深度激光雷达里程计估计传感器间的相对位姿，方法可迁移至航天器与目标相对位姿求定，但并非航天应用
tldr: 基于深度学习的激光雷达里程计在不同场景间泛化困难，在KITTI上训练的模型应用到新环境时精度明显下降。RCP-LO将相对位姿建模为相对坐标，并通过几何验证来求解，降低了简化姿态表征所带来的过拟合。实验显示该方法能显著提升跨场景相对位姿估计的泛化性能，减少性能衰退。该工作对基于点云的相对导航与定位提供了一种简单有效的方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
motivation: 现有端到端深度学习激光雷达里程计在跨场景迁移时泛化性能下降明显，位姿表征过于简化是关键原因。
method: RCP-LO将相对位姿重新表示为相对坐标，用几何验证求解，设计简单有效的回归框架避免单一过度简化表示。
result: 跨数据集和跨场景实验表明，其泛化性显著优于现有方法，性能下降幅度更小。
conclusion: 为点云相对位姿估计提供了可泛化表示与几何验证手段，可作为激光雷达相对导航任务的参考。
---

## Abstract
LiDAR odometry is a critical component of SLAM in autonomous driving and robotics. Learning-based methods have shown remarkable performance by regressing relative poses in an end-to-end manner. However, when applying these trained models, originally developed on the widely used KITTI dataset, to other scenes, performance often drops significantly. In other words, existing methods struggle to generalize well to new environments. To address this challenge, we propose RCP-LO, a simple yet effective LiDAR odometry framework. 
We introduce a novel representation for relative poses, reformulating them as relative coordinates, which can then be solved using geometrical verification. This approach avoids overly simplified pose representations and makes better use of scene geometry, thereby improving generalization.
Moreover, to capture the inherent uncertainties in relative pose estimation from occluded LiDAR point clouds from dynamic environments, we adapt our framework to learn a denoising diffusion model, allowing for sampling plausible relative coordinates while improving robustness. We also introduce a differentiable geometric weighted singular value decomposition module, enabling efficient pose estimation through a single forward pass. 
Extensive experiments demonstrate that RCP-LO, trained exclusively on the KITTI dataset, achieves competitive performance compared to SOTA learning-based methods and generalizes effectively to the KITTI-360, Ford, and Oxford datasets.

---

## 论文详细总结（自动生成）

### 1. 检索相关性
深度激光雷达里程计估计传感器间的相对位姿，方法可迁移至航天器与目标相对位姿求定，但并非航天应用。

### 2. 核心内容
基于深度学习的激光雷达里程计在不同场景间泛化困难，在KITTI上训练的模型应用到新环境时精度明显下降。RCP-LO将相对位姿建模为相对坐标，并通过几何验证来求解，降低了简化姿态表征所带来的过拟合。实验显示该方法能显著提升跨场景相对位姿估计的泛化性能，减少性能衰退。该工作对基于点云的相对导航与定位提供了一种简单有效的方案。

### 3. 对应检索需求
determination of relative position and orientation between two spacecraft or a spacecraft and target。

### 4. 来源与原文
- Source：AAAI-2026-Accepted
- OpenReview：[https://ojs.aaai.org/index.php/AAAI/article/view/37643](https://ojs.aaai.org/index.php/AAAI/article/view/37643)
