---
title: Learning Scene Coordinate Reconstruction from Unposed Images via Pose Graph Optimization
title_zh: 通过位姿图优化从无位姿图像学习场景坐标重建
authors: "Tse, Tze Ho Elden, Peng, Jizong, Yao, Angela"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Tse_Learning_Scene_Coordinate_Reconstruction_from_Unposed_Images_via_Pose_Graph_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 5.0
evidence: 无位姿图像的场景坐标重建与位姿图优化修正相机位姿；可支持基于三维模型的目标相对定位。
tldr: 无监督学习框架ACE-Zero在估计相机位姿与场景坐标时缺少全局和多视图一致性约束，容易产生漂移和误校正。本文将位姿图优化引入ACE-Zero，从预测场景坐标中提取相对位姿约束构建位姿图，并设计不确定性感知的优化策略以抑制错误修正。实验表明混合框架能在复杂场景下改进相机位姿精度并降低累积漂移。由此显示位姿图正则化可直接服务于图像地图构建和面向目标的相机定位，对航天器相对位姿估计有借鉴意义。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 246, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1802, \"height\": 268, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 744, \"height\": 453, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 872, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1664, \"height\": 1055, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 346, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tse-learning-scene-coordinate-reconstruction-from-unposed-images-via-pose-graph-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 686, \"label\": \"Table\"}]"
motivation: 现有无监督场景坐标重建与相机位姿估计缺乏全局一致约束，复杂场景下易出现漂移和误校正。
method: 提出将位姿图优化与ACE-Zero结合，由预测场景坐标提取相对位姿约束，并采用不确定性加权优化来修正相机位姿。
result: 在场景坐标重建实验中，相机位姿精度提升，误校正与漂移得到抑制。
conclusion: 证明基于场景坐标的位姿图优化能提升无监督SfM的稳健性，可迁移到基于地图的目标相对定位。
---

## Abstract
Learning-based structure-from-motion methods such as ACE-Zero have demonstrated strong performance in estimating camera poses and scene coordinates from unordered image collections without requiring ground truth supervision. However, the lack of global and multi-view consistency constraints in ACE-Zero can lead to pose drift and misalignment, particularly in complex or ambiguous scenes. In this work, we propose a hybrid framework that integrates pose graph optimization (PGO) into ACE-Zero to refine camera poses and suppress incorrect refinements. We construct pose graphs directly from ACE-Zero outputs by extracting relative pose constraints from predicted scene coordinates. Furthermore, we introduce an uncertainty-aware optimization strategy by estimating confidence scores using geometric priors, including epipolar and optical flow consistencies across views. Our approach improves the robustness and accuracy of pose estimation, demonstrating that global geometric reasoning can effectively complement learning-based inference in structure-from-motion.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与研究动机

- **背景**：基于学习的运动恢复结构（SfM）方法（如 ACE-Zero）能够从无序图像集合中直接估计相机位姿和场景坐标，且无需地面真值监督，在视觉定位与重建中展现出较强性能。
- **核心问题**：ACE-Zero 的位姿细化完全基于局部神经优化，缺少**全局一致性与多视图一致性约束**，在复杂、大规模或具有模糊性的场景中容易产生**位姿漂移（pose drift）和误对齐（misalignment）**；此外，其场景坐标预测存在噪声且缺乏不确定性估计，进一步影响位姿精度。
- **研究意义**：论文旨在解决“纯粹学习式 SfM 缺乏全局几何推理”的问题，探索如何将经典的**位姿图优化（PGO）**嵌入到 ACE-Zero 流程中，以全局几何约束弥补局部神经推理的不足，从而提升无监督 SfM 的鲁棒性和准确性。

## 2. 方法论

### 2.1 总体思路

提出一个**混合框架**：在 ACE-Zero 的每次迭代中执行 PGO，利用从预测场景坐标中提取的相对位姿约束构建位姿图，并引入**不确定性感知的加权优化**，抑制不可靠约束的影响，最终实现全局一致的相机位姿估计。

### 2.2 位姿图构建

- 给定迭代 `t` 中 ACE-Zero 预测的图像 `Ii` 的稠密场景坐标 `Xti`，对于图像对 `(i,j)`，将 `Xti` 通过相机 j 的逆位姿投影到图像 j：
  - `x̂tj = π(Tj⁻¹ Xti)`
- 检索该投影位置的预测场景坐标 `Xtj`，计算 3D 一致性误差：
  - `e_t_match = ||Xtj - Xti||`
- 若误差小于阈值 `τ`，则视为一致匹配；可选做双向对称检查。
- 利用 RANSAC + PnP 估计图像对之间的相对变换 `Zij ∈ SE(3)`，以最小化重投影误差。
- 以每个相机位姿为节点、相对变换为边，构建位姿图。

### 2.3 不确定性感知的置信度估计

ACE-Zero 不提供显式不确定性，因此提出基于几何先验的两种无监督置信度指标：

- **基于对极几何的误差**：
  - 计算本质矩阵 `Eij = [tij]× Rij`，得到对应极线 `ltj`；
  - 计算投影点 `x̂tj` 到极线的欧氏距离作为误差 `e_epi`。
- **基于光流的误差**：
  - 使用 RAFT 获取图像间稠密光流 `Fi→j`；
  - 光流预测对应点为 `x̃tj = xti + Fi→j(xti)`；
  - 计算投影点与光流对应点间的欧氏距离作为误差 `e_flow`。
- **组合置信度**：
  - `σij = α1 e_epi + α2 e_flow`（取 α1=0.4，α2=0.6）
  - 聚合图像对中所有有效匹配的置信度得到边级不确定性，并构造信息矩阵：
    - `Ωij = 1/(σij² + ε) · I`

### 2.4 全局优化

- 在 ACE-Zero 的每次迭代中执行 PGO，目标函数为最小化各边相对变换残差的加权范数：
  - `min Σ || Log(Zij⁻¹ Ti⁻¹ Tj) ||²_Ωij`
- 使用 Levenberg–Marquardt 优化器，配合 Huber 损失、首帧紧先验、未连通节点松先验等手段增强鲁棒性。

## 3. 实验设计

### 3.1 数据集与评测基准

论文在三个公开基准上评估，并以新视图合成质量（PSNR）作为位姿质量的间接度量：

- **7-Scenes**：室内 relocalization 数据集（含 Chess、Fire、Heads、Office、Pumpkin、RedKitchen、Stairs），使用 COLMAP 位姿作为伪地面真值。
- **Mip-NeRF 360**：室内外小规模场景（Bicycle、Bonsai、Counter、Garden、Kitchen、Room、Stump），用于视图合成评测。
- **Tanks and Temples**：大规模多样化场景，分为 **Training / Intermediate / Advanced** 三个子集，并包含 **短版本（~150–500 帧）和长版本（~4k–22k 帧）** 两种规模。

### 3.2 对比方法

- COLMAP（默认参数和快速模式，作为伪地面真值）
- ACE-Zero（最相关工作，基线与自复现结果）
- DROID-SLAM（神经 SLAM）
- VGGT-SLAM（神经 SLAM）

### 3.3 评测指标

- 采用 **PSNR（峰值信噪比）**：用估计位姿训练 Nerfacto 模型并渲染测试视角，与真实图像比较；
- 同时记录**重建时间**。

## 4. 资源与算力

- 文中明确说明：所有实验在**单张 NVIDIA 3090 GPU** 上执行，初始化使用 ZoeDepth。
- 具体训练总时长、GPU 数量等细节未以统一表格列出；仅在 7-Scenes 中给出平均运行时间：COLMAP 默认约 38 小时、COLMAP fast 约 13 小时、ACE-Zero 约 1 小时、本文方法约 30 分钟至 1.5 小时不等。
- 作者提到额外 PGO 步骤每次约 30 秒，而原生 ACE-Zero 每次约 150 秒；但 PGO 可将总迭代次数减少约一半。
- 论文未说明多卡并行、显存占用或具体能耗等更细粒度的算力资源信息。

## 5. 实验数量与充分性

- **主要实验**：在三大数据集上进行了与 COLMAP、ACE-Zero、DROID-SLAM、VGGT-SLAM 的定量比较，每组均包含多场景平均结果。
- **消融实验**：
  1. 对 PGO 设计组件消融（vanilla PGO、无不确定性、完整版、是否渐进式集成）；
  2. 对几何一致性阈值 τ（0.05m/0.1m/0.2m）和对称检查的敏感性分析；
  3. 对稀疏训练数据（不同数量帧）的鲁棒性测试。
- **定性比较**：提供 Mip-NeRF 360 与 Tanks and Temples 场景的可视化渲染结果对比。
- **总体评价**：实验覆盖场景类型广（室内/室外、小规模/大规模、中低纹理/复杂模糊），对比方法包含传统优化式与神经 SLAM，消融较为系统。但所有位姿质量均为**间接通过 PSNR 衡量**，没有直接使用真实位姿（ground truth）做误差统计；且 VGGT-SLAM 在 Tanks and Temples 长版本中因 GPU 显存限制未作完整对比。整体充分但存在一定的评测间接性风险。

## 6. 主要结论与发现

- 将 PGO 嵌入 ACE-Zero 可以显著改善相机位姿的全局一致性和重建质量，在 7-Scenes、Mip-NeRF 360 和 Tanks and Temples 上均超过或追平 ACE-Zero，且接近或超过 COLMAP。
- 不确定性感知的信息矩阵加权（基于对极几何+光流）比朴素 PGO 更鲁棒，能有效抑制错误相对约束的影响。
- **渐进式、每迭代执行 PGO** 比仅在训练结束后一次性优化效果更好。
- 额外计算开销换取约一半的迭代次数减少，总体重建时间仍显著低于 COLMAP。
- 全局几何推理（PGO）能够有效补充学习式 SfM 的局部神经推理，带来更可靠和一致的位姿估计。

## 7. 优点

- **方法贡献清晰**：首次将经典 PGO 系统地融入无监督场景坐标回归框架（ACE-Zero），而不是简单替换其子模块。
- **工程可行性高**：位姿图直接从 ACE-Zero 输出中构造，不依赖任何外部位姿监督；相对约束由 RANSAC+PnP 估计，接口简单。
- **不确定性设计合理**：对极几何与光流互补，提供全局几何校验与局部图像证据，能提高优化对噪声和异常值的鲁棒性。
- **效率优势明显**：虽增加每次迭代计算，但全局约束使整体迭代次数减半，实际总时间仍远少于 COLMAP。
- **实验范围较广**：覆盖多类数据集与多种对比方法，且提供了详尽的消融与敏感性分析。

## 8. 不足与局限

- **不确定性为启发式**：基于对极和光流的置信度度量并非严格概率模型，在高度动态或极低纹理场景中可能不通用、不准确。
- **超参数依赖人工调节**：τ、α1、α2、Huber 尺度等需要较多手动调参，泛化时可能需重新调整。
- **未联合优化场景结构**：PGO 只优化位姿，不同时优化 3D 结构，仍缺乏端到端联合束调整（BA）能力。
- **评测间接性**：由于缺乏真实位姿，PSNR 并非直接衡量位姿精度，可能会受 NeRF 渲染质量、模型能力等因素干扰，导致偏差。
- **对 COLMAP 的依赖**：在实验中把 COLMAP 作为伪地面真值，而 COLMAP 自身在大规模或弱纹理场景也可能存在误差。
- **对比完整性受限**：VGGT-SLAM 在长版本 Tanks and Temples 因显存原因无法完整运行，DROID-SLAM 也只在部分场景给出结果，公平性略受影响。
- **运行资源未充分细化**：未报告显存占用、多卡可扩展性以及各子步骤精确耗时分解。

（完）
