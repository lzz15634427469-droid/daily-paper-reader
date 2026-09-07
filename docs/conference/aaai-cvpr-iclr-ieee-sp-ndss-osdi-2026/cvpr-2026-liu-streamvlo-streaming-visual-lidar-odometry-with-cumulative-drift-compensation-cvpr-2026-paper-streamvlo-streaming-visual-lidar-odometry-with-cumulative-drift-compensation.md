---
title: "StreamVLO: Streaming Visual-LiDAR Odometry with Cumulative Drift Compensation"
title_zh: StreamVLO：流式视觉-激光雷达里程计与累积漂移补偿
authors: "Liu, Mengmeng, Liu, Jiuming, Yang, Michael Ying, Jiang, Chaokang, Li, Jiangtao, Zhang, Yunpeng, Wang, Hesheng, Nex, Francesco, Cheng, Hao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_StreamVLO_Streaming_Visual-LiDAR_Odometry_with_Cumulative_Drift_Compensation_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 5.0
evidence: 融合视觉与LiDAR进行流式位姿估计并抑制漂移，可作为航天器相对位姿估计中相机与激光雷达融合方法的借鉴
tldr: 视觉-激光雷达里程计常局限于成对帧时序建模，在4D动态环境中容易累积漂移。文章提出StreamVLO，以Mamba构建跨多帧的统一时空相关模块融合异构视觉与LiDAR特征，并通过因果式残差学习在线补偿累计漂移。实验表明该方法增强了动态环境下的定位稳定性，降低了长时漂移。该融合与补偿思路可迁移到航天器相对位姿估计中的相机与激光雷达联合任务。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 848, \"height\": 793, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1807, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 215, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 825, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 826, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 869, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 863, \"height\": 513, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 626, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1628, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1624, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 364, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 849, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 871, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 319, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 864, \"height\": 183, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-streamvlo-streaming-visual-lidar-odometry-with-cumulative-drift-compensation-cvpr-2026-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 861, \"height\": 176, \"label\": \"Table\"}]"
motivation: 现有视觉-激光雷达位姿估计方法时序探索有限，且长时定位存在累积漂移问题。
method: StreamVLO采用Mamba统一时空相关融合视觉与LiDAR多帧信息，并用在线累积漂移补偿迭代修正历史帧残差。
result: 动态4D环境中的定位漂移得到抑制，显著位置特征表示增强，里程计精度与鲁棒性提高。
conclusion: 为视觉与激光雷达联合位姿估计提供了新的流式框架，可为多传感器航天器相对导航提供方法参考。
---

## Abstract
We propose StreamVLO, a streaming visual-LiDAR odometry framework that performs unified spatio-temporal correlation with Mamba models and tackles the long-standing cumulative drift problem via an online Cumulative Drift Compensation scheme for localization in 4D dynamic environments. Specifically, StreamVLO introduces a unified spatio-temporal correlation module built on Mamba to fuse heterogeneous visual and LiDAR cues across multi-frame clips, overcoming the limited temporal exploration of prior pairwise methods. Furthermore, a Cumulative Drift Compensation module minimizes cumulative drift by iteratively learning residual corrections from multiple historical frames in a causal manner. To strengthen spatial feature representation on salient regions, we adopt a Keypoint-Aware Auxiliary Loss with a winner-takes-all strategy. StreamVLO achieves state-of-the-art performance on two commonly used autonomous driving datasets, reducing errors by 19% t_rel and 22% r_rel on KITTI, and by 18% ATE and 16% RPE on Argoverse, while remaining suitable for real-time deployment.

---

## 论文详细总结（自动生成）

# 论文总结：StreamVLO —— 流式视觉-激光雷达里程计与累积漂移补偿

## 1. 论文的核心问题与整体含义

- **研究背景**：里程计（Odometry）任务旨在估计传感器在相邻帧之间的相对位姿变换，是自动驾驶、SLAM 系统等下游应用的基础。视觉与 LiDAR 传感器各具优势：视觉提供丰富的 2D 纹理信息，LiDAR 提供精确的 3D 几何结构，二者互补，因此视觉-激光雷达融合里程计（Visual-LiDAR Odometry）受到广泛关注。
- **核心问题**：现有大多数里程计方法存在以下两大局限：
  - **时序建模不足**：主流方法通常采用**成对帧输入**（如相邻两帧），仅依靠 Deformable Mamba 或相似模块做空间建图，忽略了多帧序列中丰富的时间上下文信息，导致定位鲁棒性不足；
  - **累积漂移严重**：长序列运行过程中，帧间位姿估计的微小误差逐步累积，造成显著的长时轨迹漂移，而传统 SLAM 依赖全局优化或回环检测来消除累积误差，但这不适用于流式在线场景。
- **整体意义**：论文提出一种**流式的、因果的**视觉-LiDAR 融合里程计框架 StreamVLO，通过统一时空相关建模与在线累积漂移补偿，在不依赖全局优化或回环检测的前提下，实现对长序列的精确、低漂移的实时位姿估计。

## 2. 论文提出的方法论

### 2.1 总体架构
StreamVLO 的整体流程为：分别使用图像编码器和点云编码器提取多尺度特征，再经过三个核心模块处理，逐步生成位姿估计并修正：

1. **Unified Spatio-Temporal Correlation（统一时空相关）**——对视觉和 LiDAR 特征进行跨帧融合；
2. **Cumulative Drift Compensation (CDC，累积漂移补偿)**——利用历史累积位姿信息对当前帧位姿进行残差修正；
3. **Keypoint-Aware Auxiliary Loss（关键点感知辅助损失）**——强化空间特征表示中显著区域的学习。

### 2.2 统一时空相关模块（MMG 架构）
论文提出了一个由 **MaxPooling、Mamba、gMLP** 组成的统一架构（MMG），其核心逻辑如下：

- **gMLP**：将不同模态、不同时间维度的输入序列编码到统一特征空间；
- **Mamba**：在序列内建立时间交互（状态空间模型，SSM），捕获长时依赖；
- **MaxPooling**：将序列压缩为统一、紧凑的特征向量。

在 MMG 框架下，论文设计了两个实例化模块：

- **Deformable Mamba（空间融合）**：以 LiDAR 特征为 query，通过相机内外参将 LiDAR 点云投影到图像平面获取参考点，再围绕参考点进行可变形偏移后的双线性插值采样视觉特征，通过 MMG 模块与 LiDAR 特征融合，公式为：
  - F_fused = MaxPool(Mamba(G_f(F_sample ⊕ F_P)))
  - 融合后经过 Cost Volume 模块产生跨帧运动特征 E_ego。

- **Temporal Mamba（时序记忆）**：设计了隐式特征记忆库（MFB）和显式位姿记忆库（MPB），存储历史帧的自我运动特征和位姿序列（四元数平移向量）。MMG 对历史特征序列进行编码，得到时间增强的嵌入 E_ego、Q_enc、P_enc。初始位姿由 MLP 从融合特征中预测，并级联迭代细化。

### 2.3 累积漂移补偿（CDC）
这是本文解决长时漂移问题的核心模块，关键思想是：**从历史帧出发回溯（backtrack），利用累积位姿将历史帧点云变换到当前帧，再与当前目标点云计算残差位姿，以此修正当前帧的位姿预测**，以直接惩罚累积误差。

核心流程如下：
1. 计算最近 T_g 帧的**累积位姿**（通过依次相乘相邻帧的位姿变换获得）；
2. 利用该累积位姿将历史源点云（PC 在 T_t-T_g 时刻）Warp 到当前时刻 T_t；
3. 通过 PWC 结构计算 Warp 所得点云与当前时刻目标点云之间的**残差位姿误差** (Δq^(2), Δp^(2))；
4. 将残差位姿与初始位姿组合得到最终位姿：(q^(3), p^(3)) = (Δq^(2), Δp^(2)) ∘ (q^(2), p^(2))。

该漂移补偿机制是**可微分的、在线端到端训练的**，避免了 SLAM 中的全局优化或回环闭合需求。

### 2.4 损失函数
总体损失分为三部分：

1. **回归损失（Regression Loss）**：对三阶段输出位姿——初始 (q^(1), p^(1))、细化位姿 (q^(2), p^(2))、漂移补偿后的 (q^(3), p^(3))——分别计算回归误差（平移用 L1、旋转用 L2），总损失为三阶段的加权和 L_reg = α₁L^(1) + α₂L^(2) + α₃L^(3)；
2. **关键点感知辅助损失（Keypoint-Aware Auxiliary Loss）**：对特征图上的 N 个查询点（query）分别预测位姿，然后采用**胜者通吃（winner-takes-all）**策略，只对与真值误差最小的 top-k 个查询点计算回归损失，引导模型关注静态、高显著性区域；
3. **集体平均损失（Collective Average Loss, CAL）**：在整个子片段（sub-clip）的各帧间进行平均聚合——受到 MOTR 的启发，适用于流式多帧场景。

## 3. 实验设计

### 3.1 数据集

| 数据集 | 用途 | 划分方式 |
|--------|------|---------|
| KITTI Odometry（22 个序列） | 主实验 | 序列 00–06 训练，07–10 测试 |
| Argoverse（113 个序列） | 泛化性验证 | 官方划分：65/24/24（训练/验证/测试） |

### 3.2 评估指标
- **平移 RMSE（t_rel，%）**和**旋转 RMSE（r_rel，°/100m）**（在 100–800m 长度区间内计算）；
- **ATE（绝对轨迹误差）**和 **RPE（相对位姿误差）**——在跨数据集与 SLAM 对比中使用。

### 3.3 对比方法
- **深度学习视觉里程计（VO）**：SfMLearner、DFVO、Cho et al.；
- **LiDAR 里程计（LO）**：LO-Net、PWCLO、DELO、TransLO、EfficientLO、DSLO、LAGLO 等；
- **多模态视觉-LiDAR 里程计**：An et al.、H-VLO、DVLO、DVLO4D；
- **传统 SLAM（带回环闭合）**：ORB-SLAM2/3、LDSO、DROID-SLAM、DPV-SLAM、MambaVO++、DVL-SLAM、TVL-SLAM 等；
- **几何方法**：LeGO-LOAM、SUMA、PyLiDAR。

### 3.4 主要应用与实验场景
论文在若干方面做了对比，包括：KITTI/Argoverse 主测评、与传统 SLAM 的 ATE 对比（尽管它们通常有回环闭合与全局优化，而本文是用流式前端直接对比）、视频中 trajectory 可视化、动态/高旋转运动场景评估等，从多个维度对比了方法的性能表现。

## 4. 资源与算力

- 论文提到使用了 **NVIDIA 4090 GPU**（单卡）进行推理延迟评估，未提及具体训练硬件配置（是否多卡、数量、型号等），但给出的整体推理延迟约 74ms。
- 原文未明确给出**训练时长、GPU 数量等具体训练资源信息**，只提到延迟测试使用英伟达 4090 GPU。若要复现模型，需要从论文其他细节（如 batch size、模型结构）推断所需的大致算力，但无法精确得知。

## 5. 实验数量与充分性

- **总体实验组数**较多，论文至少报告了以下 8 类实验结果：
  1. KITTI 主实验——多模态/SLAM/传统方法的对比（表 1、2、3）；
  2. Argoverse 测试集上的性能评估与对比（表 4）；
  3. 定性分析（trajectory visualization、图 5–8）；
  4. 消融实验（表 6，包括 unified MMG、CDC、关键点辅助损失）；
  5. 替代融合策略的比较（表 7，CNN、聚类、注意力、可变形注意力 vs 可变形 Mamba）；
  6. 延迟效率对比分析（表 5）；
  7. 跨数据集泛化实验（KITTI→Argoverse，表 8）；
  8. 复杂运动（高动态、高旋转）场景评估（表 9）。

- **实验充分性评价**：
  - 优点：实验覆盖面较广，涵盖了传统/学习两类基线、单模态/多模态融合类型的对比，各类实验设计完整，尤其是消融和跨数据集泛化、复杂运动场景的实验，具有较强的说服力；
  - 局限：主要在两个自动驾驶数据集（KITTI、Argoverse）上进行验证，**缺乏在其他类型场景（室内、非结构化地形或恶劣天气）上的实验**；对同一传感器在不同时间、不同天气条件下的泛化能力也未提供验证。另外，文中虽与几何法（SUMA 等）进行对比，但部分对比对象（如传统 SLAM）的存在配置差异（有无回环等）也可能带来不公的因素，值得关注。

## 6. 论文的主要结论

1. **统一的 MMG 时空相关建模**确实优于单独、分离的空间和时间建模方式，能有效利用多帧上下文信息，结果呈现 19% 平移误差和 22% 旋转误差的相对降低；
2. **累积漂移补偿（CDC）** 在多帧历史上进行差分学习，能有效抑制长序列的漂移累积，并与传统的全局优化/回环检测思路形成互补；
3. **关键点感知辅助损失**有效引导模型关注静态显著性区域，增强特征鲁棒性，削除了动态物体的不利影响，使得模型的准确性和稳定性增强；
4. **实时性**符合要求，推理延迟约 74ms，适用于自动驾驶场景的流式部署；
5. StreamVLO 在**KITTI 与 Argoverse** 数据集上均取得了领先性能，并在 KITTI 序列 07–10 上的平移和旋转误差大幅低于主流方法，且跨数据集泛化性明显优于 DVLO（误差增大幅度从 81.6%→32.9%）。

## 7. 优点

### 方法层面
- **新颖性**：首次将 Mamba（状态空间模型）用于视觉-LiDAR 融合里程计的统一时空相关建模中，设计 Deformable Mamba 和 Temporal Mamba，具有线性复杂度和长序列建模能力；
- **漂移控制思路先进**：通过可微分的 CDC 模块在线上因果地修正累积漂移，避免了 SLAM 中全局优化/回环闭合的强假设，更适应长序列无界行驶场景；
- **架构轻巧**：统一 MMG 结构避免了传统跨模态方法的复杂处理流程，牺牲较少精度而提升效率，融合方案综合性能优，准确度与延迟较优。

### 实验与工程层面
- 在多个主流 benchmark（KITTI、Argoverse）上进行了充分的对比实验，并在性能指标上均有提升；
- 消融实验覆盖到位，验证了每个模块的贡献；
- 提供了含实时性、跨数据集泛化性、复杂运动等不同维度的风险评估。

## 8. 不足与局限

### 实验层面的局限
- **场景多样性不足**：实验仅在 KITTI 和 Argoverse（自动驾驶室外场景）上进行，未在室内 / 山地 / 雨雪 / 夜间 / 地下等环境中验证，结果可能过度依赖结构化道路环境；
- **跨数据集泛化实验虽有但形式单一**：只做了 KITTI→Argoverse 方向的迁移，并未检验 Argoverse→KITTI 的反向迁移效果；
- **未包含长时间大尺度测试**：对更大规模的真实路网是否存在记忆库费用 / 记忆库溢出问题未提供任何分析或验证；
- **与传统 SLAM 方法的对比公平性可以再进一步说明**：传统 SLAM（ORB、DROID 等）在一般条件下存在回环闭合或全局优化配置，与纯流式前端对比的条件并不完全一致，表 2 中的误差对比无法完全反映其算法差距。

### 方法层面的潜在问题
- **记忆库和超参数规模**依赖较多（如 T_h=30、T_g=20 等），当场景变化较大或序列非常长（需要记忆的历史数量非常庞大时）时未必能保持有效或及时响应；
- **对融合的标定误差比较敏感**：Deformable Mamba 依赖 LiDAR 点云投影到图像平面并采样视觉特征的精确投影关系，在标定误差或时间同步误差较大的情况下，采样分支可能会失效；
- **点云稀疏与图像高分辨率不匹配**时，融合特征在语义细节与稀疏三维结构的交互上可能仍有信息丢失。

### 算力报告的缺失
- 论文虽报告了推理延迟时间，但**未报告训练时长、总计算资源（GPU 卡数、型号与训练策略）**，对后续复现性有一定影响。

---

（完）
