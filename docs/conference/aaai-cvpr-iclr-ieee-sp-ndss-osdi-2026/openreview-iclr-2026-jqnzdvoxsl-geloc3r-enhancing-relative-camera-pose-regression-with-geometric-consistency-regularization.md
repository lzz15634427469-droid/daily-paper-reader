---
title: "GeLoc3r: Enhancing Relative Camera Pose Regression with Geometric Consistency Regularization"
title_zh: GeLoc3r：利用几何一致性正则化增强相对相机位姿回归
authors: "Jingxing Li, Yongjae Lee, Deliang Fan"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=jQNzDvoXSL"
tags: ["query:pe"]
score: 4.0
evidence: 用几何一致性正则化提升相对相机位姿回归，可作为单目相对位姿估计的通用技术组件
tldr: 针对回归式相对相机位姿估计虽快但精度低于特征对应点方法的问题，提出GeLoc3r，在训练时用真值深度生成稠密三维几何约束，并施加几何一致性正则化，使网络输出几何一致的位姿且推理期无需额外几何计算。实验表明该方法在保持毫秒级推理速度的同时接近对应点法的精度。该思路可服务于航天器交会中基于单目图像的高效相对位姿回归与验证。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 相对相机位姿回归网络内部表示存在几何不一致，难以达到对应点方法的精度上限。
method: 提出GeLoc3r，通过训练阶段的几何一致性正则化和真值深度生成的稠密三维约束优化回归网络。
result: 在保持约25毫秒快速推理的同时使回归精度接近对应点类方法。
conclusion: 表明将几何一致性嵌入训练可有效缓解位姿回归的速度-精度两难问题。
---

## Abstract
Prior ReLoc3R achieves breakthrough performance with fast 25ms inference and state-of-the-art regression accuracy, yet our analysis reveals subtle geometric inconsistencies in its internal representations that prevent reaching the precision ceiling of correspondence-based methods like MASt3R (which require 300ms per pair).
In this work, we present GeLoc3r, a novel approach to relative camera pose estimation that enhances pose regression methods through Geometric Consistency Regularization (GCR). 
GeLoc3r overcomes the speed-accuracy dilemma by training regression networks to produce geometrically consistent poses without inference-time geometric computation. During training, GeLoc3r leverages ground-truth depth to generate dense 3D-2D correspondences, weights them using a FusionTransformer that learns correspondence importance, and computes geometrically-consistent poses via weighted RANSAC. This creates a consistency loss that transfers geometric knowledge into the regression network. Unlike FAR method which requires both regression and geometric solving at inference, GeLoc3r only uses the enhanced regression head at test time, maintaining ReLoc3R's fast speed and approaching MASt3R's high accuracy. On challenging benchmarks, GeLoc3r consistently outperforms ReLoc3R, achieving significant improvements including 40.45% vs. 34.85% AUC@5° on the CO3Dv2 dataset (16% relative improvement), 68.66% vs. 66.70% AUC@5° on RealEstate10K, and 50.45% vs. 49.60% on MegaDepth1500. By teaching geometric consistency during training rather than enforcing it at inference, GeLoc3r represents a paradigm shift in how neural networks learn camera geometry, achieving both the speed of regression and the geometric understanding of correspondence methods.

---

## 论文详细总结（自动生成）

# GeLoc3r 论文深度总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题焦点**：单目相对相机位姿估计（relative camera pose estimation）面临“速度-精度两难”（speed-accuracy dilemma）困境。
  - 传统基于特征对应点的方法（如 MASt3R）精度较高，但每对图像推理约需 **300ms**，无法满足实时应用；
  - 端到端回归方法（如 ReLoc3R）速度快（每对约 **25ms**），但精度低于对应点法。
- **深层原因**：作者通过对 ReLoc3R 的深入分析发现，回归网络的内部隐式表征存在**细微的几何不一致性（geometric inconsistency）**，导致其精度无法逼近对应点类方法的上限。
- **核心研究问题**：如何让回归式网络同时获得“回归的速度”和“对应点法级的几何理解”，且不牺牲推理效率？
- **整体含义**：Neural networks 可以在**训练阶段**被教会几何一致性，而不需要在**推理阶段**显式执行几何计算——这为神经网络的相机几何学习提供了新的范式，兼具实时性和高精度。

## 2. 方法论

### 2.1 核心思路

- 提出 **GeLoc3r**，其核心是 **Geometric Consistency Regularization (GCR, 几何一致性正则化)**：
  > 在训练过程中迫使回归网络输出与“显式几何求解结果”一致的位姿，从而将几何知识从几何求解器“蒸馏/迁移”回回归网络；推理时仅保留增强后的回归头，无需任何额外几何计算。

### 2.2 关键技术细节

- **训练阶段（在位的几何监督）**：
  1. 利用 **真值深度（ground-truth depth）**（还结合预测的深度或 RGB 信息）生成稠密的 **3D-2D 对应点（dense 3D-2D correspondences）**；
  2. 引入 **FusionTransformer**：学习每组对应点的重要程度/权重（correspondence importance）；
  3. 对稠密加权对应点执行 **加权 RANSAC（weighted RANSAC）** 求解，得到**几何一致（geometrically consistent）的相对位姿**。
- **一致性损失（consistency loss）**：将上述几何求解结果与回归网络直接输出的位姿作一致性约束，形成梯度信号，回传到回归网络。
- **与 FAR（同时需要回归+推理时几何求解）不同**：GeLoc3r 仅在训练阶段使用几何模块；推理时回归头直接输出位姿，保持 ReLoc3R 级的快速推理（约 25ms）。
- **“教任务而非做任务”**：把几何一致性嵌入训练目标（loss）而非推理流程中——这是方法在哲学上与传统“求解器”类方法的最大差异。

## 3. 实验设计

- **基准与数据集（3 类主流大规模位姿估计基准）**：
  - **CO3Dv2**（常见物体 3D 数据集，挑战性强）；
  - **RealEstate10K**（大规模室内外场景序列）；
  - **MegaDepth1500**（MegaDepth 的 1500 对子集，常用相对位姿评测基准）。
- **评估指标**：AUC@5°（位姿误差在 5° 内的累计分布面积），也应当含 AUC@10°/20°（摘要未给出，通常此类 benchmark 会报告）。
- **对比方法**：
  - ReLoc3R（自身基线，同为回归方法，SOTA 回归精度 + 25ms 快速推理）；
  - MASt3R（对应点类方法的代表，高精度、推理慢）；
  - FAR（也属于“回归+几何求解”混合路线）。

## 4. 资源与算力

- **文中有提及的部分**：未在摘要和元数据中明确列出具体的 GPU 型号、卡数、训练时长等落地资源信息。
- **结论**：这篇论文在提供的信息中没有报告训练配置（如 A100/H100 数量、训练天数等）。若需要完整资源信息，仍需查阅全文（实验设置/附录）。这是一个信息缺口。

## 5. 实验数量与充分性

- **主实验规模**：在 **3 个数据集**（CO3Dv2、RealEstate10K、MegaDepth1500）上进行了系统性评测；
- **对照/消融内容**（根据摘要可推断，至少包含）：
  - 与同源回归基线 ReLoc3R 对比（同一头、同一设置）；
  - 与高精度对应点法 MASt3R 对比（验证“速度-精度”新型边界）；
  - 与混合推理方法 FAR 对比（证明纯回归也可以在推理时无需几何求解）；
  - 从中可以看出作者内部还进行了“w/ vs w/o 几何一致性正则化”的消融分析（通过对比 GeLoc3r 与 ReLoc3R 的结果来体现），很可能在全文中有更多细节（如 FusionTransformer 的消融、不同权重方案等），但在摘要中有限。
- **充分性评价**：
  - **优点**：三组基准涵盖了室内外场景与物体中心数据，覆盖面较广；对比方法具有代表性（快vs准 vs 混合三种路线），能够有力支撑“接近 MASt3R 精度、同时保持约 25ms 速度”的主结论。
  - **局限**：摘要给出的消融细节较少；在论文正文中若没有额外测试，则缺少关于分辨率、相机内参、真实深度噪声鲁棒性的充分讨论；若训练数据依赖真值深度，泛化性实验的充分性需全文确认。

## 6. 主要结论与发现

- **回归基线的不一致性被证实**：ReLoc3R 虽然准确率高，但内部表示存在“几何不一致的误差”，制约其逼近对应点法精度。
- **GeLoc3r 全面超过 ReLoc3R，大幅在 CO3Dv2 上提升**：
  | 数据集 | ReLoc3R AUC@5° | GeLoc3r AUC@5° | 相对改进 |
  |---|---|---|---|
  | CO3Dv2 | 34.85% | **40.45%** | **+16%（相对）** |
  | RealEstate10K | 66.70% | **68.66%** | ~ +2.9%（相对） |
  | MegaDepth1500 | 49.60% | **50.45%** | ~ +1.7%（相对） |
- **速度与精度的新边界**：GeLoc3r 在约 25ms 的推断速度下，将回归精度提升至接近 MASt3R（对应点法）的水平，显著缓解了速度-精度两难。
- **范式论断**：通过“在训练中教学几何一致性，而非在推理中强化几何一致性” (teaching during training vs enforcing at inference)，可以同时获得回归网络的效率与对应点法的几何理解能力。

## 7. 优点

- **概念清晰、视角新颖**：不再同时用“回归+几何”两条腿走路，而是用几何求解器作为训练期教师，用回归网络作推理期唯一执行者——范式边界清晰。
- **效率与精度的兼顾**：co-design 了“训练期 RANSAC + 推理期零开销”的流程，在真实部署时没有引入额外 latency。
- **对应点加权设计的针对性**：使用 FusionTransformer 自适应地学习稠密对应的权重，有利于处理遮挡、弱纹理区域，比均匀采样式 RANSAC 更稳。
- **一致性的“知识传递”思想**：将显式几何求解作为正则化项（而不是推理流程）的做法，具有较好的通用性/可迁移性，可应用到其他回归式几何任务中。
- **效果好且趋势一致**：在 3 个不同数据集均取得提升，特别是 CO3Dv2 上的 +16% 相对提升比较显著，说明在难数据、物体级场景下收益更高。

## 8. 不足与局限

- **依赖真值深度**：训练时需要 ground-truth depth 生成 3D-2D 对应。在无深度标注的大规模真实场景上训练受限，限制了方法在“百亿级无标注互联网图像”场景下的可扩展性。
- **缺少完整资源/训练设置的说明**：摘要中未提供 GPU 数量、训练时间、参数量对比等，给复现和工程评估造成不便。
- **消融呈现范围的限制**：从摘要来看，实验虽覆盖 3 个标准基准且纵向对比清晰，但关于 FusionTransformer、加权 RANSAC 阈值、深度噪声、未见过的类别/场景泛化等消融是否充分，尚需全文评估。
- **精度仍与最优对应点法存在差距**：虽然 GeLoc3r 逼近 MASt3R，但并未明确宣称完全追平——GeLoc3r 只是“接近（approaching）” MASt3R 的精度，表明几何一致性正则化依然受限于回归式表征容量。
- **应用约束**：
  - 该方法针对“相对位姿”设置，无法直接覆盖绝对位姿估计或多视角全局一致的场景；
  - 推理时若回归头内部表示退化，没有运行时几何校验，安全性要求高的任务中存在风险。

---

（完）
