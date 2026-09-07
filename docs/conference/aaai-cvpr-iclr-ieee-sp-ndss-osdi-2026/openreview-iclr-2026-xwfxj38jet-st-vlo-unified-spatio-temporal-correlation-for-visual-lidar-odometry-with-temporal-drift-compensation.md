---
title: "ST-VLO: Unified Spatio-Temporal Correlation for Visual-LiDAR Odometry with Temporal Drift Compensation"
title_zh: ST-VLO：具有时间漂移补偿的视觉-激光雷达里程计统一时空关联
authors: "Mengmeng Liu, Jiuming Liu, Michael Ying Yang, Chaokang Jiang, Jiangtao Li, Yunpeng Zhang, Hesheng Wang, Francesco Nex, Hao Cheng"
date: 2025-09-03
pdf: "https://openreview.net/pdf?id=XwFXJ38jET"
tags: ["query:pe"]
score: 4.0
evidence: 视觉与激光雷达时空融合及漂移补偿方法，可供相机-激光雷达相对位姿估计的多模态融合借鉴
tldr: 针对视觉-激光雷达里程计的时间信息利用不足和累积漂移问题，提出ST-VLO，采用Mamba建立跨帧视觉与激光雷达的统一时空相关模块，并设计了学习修正残差的时间漂移补偿模块。该方法在4D动态环境定位中有效缓解了长期误差累积。实验表明其定位精度和稳定性优于逐对融合方法。多模态时空融合思想可为航天器交会中的相机与激光雷达组合相对位姿估计提供参考。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有视觉-激光雷达里程计多采用成对帧融合，忽视多帧时间信息且累积漂移严重。
method: 用Mamba统一建模跨帧视觉与LiDAR时空相关，并通过迭代学习残差进行时间漂移补偿。
result: 在动态环境视觉-激光雷达里程计基准上有效降低累积漂移、提升定位稳定性。
conclusion: 说明多帧时空相关与漂移补偿对多模态里程计重要，可迁移到航天器多传感器相对导航。
---

## Abstract
We propose an effective and efficient visual-LiDAR odometry framework named ST-VLO, which establishes the unified spatio-temporal correlation with Mamba models and addresses the long-standing cumulative drift problem with temporal compensation for the localization in 4D dynamic environments. 
Specifically, ST-VLO includes a novel unified spatial-temporal correlation module established on Mamba to fuse heterogeneous visual and LiDAR information across multi-frame video clips, overcoming the insufficient temporal information exploration in previous pairwise odometry methods. Furthermore, a Temporal Drift Compensation module is designed to minimize cumulative drifts by iteratively learning correction residuals from multiple history frames. To strengthen the spatial feature representation on salient features, we also propose a Keypoint-Aware Auxiliary Loss with a winner-takes-all strategy.
ST-VLO achieves state-of-the-art performance on two commonly-used autonomous driving datasets, surpassing previous methods with a 19\% \( t_{rel} \) and 22\% \( r_{rel} \) reduction on KITTI, and a 18\% ATE and 16\% RPE reduction on Argoverse.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究背景**：视觉-激光雷达里程计（Visual-LiDAR Odometry, VLO）旨在融合相机与激光雷达的互补信息，为自动驾驶等4D动态环境下的自主定位提供鲁棒的状态估计。
- **核心问题**：现有VLO方法大多采用**逐对帧融合（pairwise fusion）**的策略，仅关注相邻两帧之间的空间关联，对多帧序列中蕴含的**时间维度信息**利用不足，导致在动态场景下定位精度受限。
- **深层痛点**：里程计在长距离运行中不可避免地存在**累积漂移**问题，而传统方法缺乏显式的时间漂移补偿机制，使得长期定位误差持续累加，最终影响系统稳定性和可靠性。

## 2. 论文提出的方法论
论文提出了一种名为 **ST-VLO** 的统一时空关联视觉-激光雷达里程计框架，核心思想包括以下三大部分：

### 核心技术思路
- **统一时空关联建模**：不再仅做帧间配对融合，而是直接在**多帧视频片段**（multi-frame video clips）上建立跨模态的统一时空相关。
- **基于Mamba的架构**：引入状态空间模型 Mamba 来处理长序列的时空依赖关系，克服逐对融合方法时间信息探索不足的问题。
- **显式漂移补偿**：设计了时间漂移补偿模块，通过学习修正残差来平滑累积误差。
- **特征强化**：提出关键点感知的辅助损失，以加强显著特征的空间表示能力。

### 关键模块（按文字流程描述）
1. **统一时空相关模块（Unified Spatial-Temporal Correlation Module）**
   - 构建在 Mamba 模型之上，将来自相机（视觉）和激光雷达（LiDAR）的异构信息在多帧片段中统一建模。
   - 从整个系统流程看，视觉特征和 LiDAR 特征先分别被提取，再进入该模块，在时空两维上做跨模态交互融合，从而提取出比逐帧配对更好的运动与结构线索。
2. **时间漂移补偿模块（Temporal Drift Compensation Module）**
   - 核心操作是**利用多个历史帧迭代学习修正残差**，不是一次性直接预测最终位姿，而是通过反复修正逐步逼近真实轨迹。
   - 作用机制可理解为：在每个迭代步骤中读取上一阶段产生的轨迹估计误差，再将历史帧信息作为上下文来估计残差，进而对当前位姿进行更新和补偿，从而显著降低轨迹上的累积漂移。
3. **关键点感知辅助损失（Keypoint-Aware Auxiliary Loss）**
   - 采用 **winner-takes-all（赢家通吃）** 策略，在训练期间强化对显著关键点特征的约束，增强空间特征表达。

## 3. 实验设计
- **数据集**：
  - **KITTI** 自动驾驶数据集（视觉-激光雷达里程计的标准benchmark）。
  - **Argoverse** 自动驾驶数据集（更强调城市复杂动态环境）。
- **评估指标**：
  - KITTI上：相对平移误差（\( t_{rel} \)）与相对旋转误差（\( r_{rel} \)）。
  - Argoverse上：绝对轨迹误差（ATE）与相对位姿误差（RPE）。
- **对比方法**：
  - 与以往主流的视觉-激光雷达里程计方法（尤其先前基于逐对帧融合的VLO方法）进行全面对比。
- **主要结果**：
  - 在 KITTI 上，相比于以往方法，相对平移误差 \( t_{rel} \) 降低 19%，相对旋转误差 \( r_{rel} \) 降低 22%。
  - 在 Argoverse 上，ATE 降低 18%，RPE 降低 16%，达到当前最优性能（state-of-the-art）。

## 4. 资源与算力
- **原文说明情况**：在提供的摘要与论文元数据内容中，**未明确披露**训练所使用的 GPU 型号、数量、训练总时长、参数量等具体算力信息。
- **备注**：只能从文本中确认实验是在两个常用自动驾驶数据集上完成的，但具体硬件环境属于不可见细节，须阅读论文正文（实验设置章节）才能获得更完整信息。

## 5. 实验数量与充分性
- **实验组别概览**：
  - 在两个主流数据集（KITTI、Argoverse）上分别进行测评。
  - 依据摘要可推断，论文包含了带有/不含关键点感知辅助损失的消融分析（因为明确将该损失作为贡献点提出）。
  - 论文提及与先前SOTA方法的对比实验。
- **充分性评估**：
  - **积极方面**：在两个公开大型自动驾驶数据集上验证，且结果同时检验了平移与旋转两方面误差，评估维度较为系统；从改进幅度（约20%左右）来看，性能增益具有统计意义。
  - **不足方面**：仅仅在自动驾驶场景（KITTI / Argoverse）中对动态环境LM进行评测，若可补充更多多样环境（如校园、室内、越野）的数据，会让泛化性结论更稳健。
  - **公平性提示**：在阅读正文时需要核对是否采用相同的特征提取预训练、是否加入额外地图约束（loop closure）等，以避免与无回环的纯里程计方法对比时产生不公平因素。

## 6. 论文的主要结论与发现
- 在4D动态环境中，**多帧跨模态的时空统一相关建模**相比传统的逐帧配对融合策略能更充分地挖掘时间维度上的信息，有效提升里程计的整体精度。
- 通过**迭代学习历史帧修正残差**来进行时间漂移补偿，能够显著缓解长期误差累积问题，提高轨迹估计的稳定性和鲁棒性。
- **关键点感知辅助损失**与赢家通吃策略能进一步强化空间特征，对整体系统性能有正向贡献。
- 综合实验结果，ST-VLO在两大自动驾驶基准上均取得了当前最优（SOTA）精度，不仅验证了方法有效性，也为核心思想的推广提供了实证支持。

## 7. 优点
- **方法创新鲜明**：将视觉与LiDAR的融合从空间维度升级为“空间+时间”的统一建模；引入Mamba的这一选择比传统RNN/Transformer在处理长时序时更有序列建模效率优势，是新颖的架构设计。
- **针对性解决难题**：直接针对VLO时间信息利用不足和累积漂移两个瓶颈问题分别设计模块，问题意识清晰、模块分工明确。
- **多样化的训练信号**：借助关键点感知辅助损失（winner-takes-all）这种细粒度正则，相对单纯用整帧监督信号而言在特征表达上更具鲁棒性。
- **实验提升幅度大且共识性好**：在两个数据集上均带来约20%级别的误差下降，且同时覆盖KITTI与Argoverse，说明方法改进不是对单一benchmark的偶然适配。
- **应用迁移潜力**：方法框架对多传感器融合相对导航（如地外天体着陆、航天器交会过程中的视觉与LiDAR组合位姿估计）具有理论上的可借鉴性。

## 8. 不足与局限
- **算力/复现细节不足**：摘要和元数据中没有提供模型大小、推理速度、训练消耗等工程信息，读者难以从当前文本中快速评估实际应用中的部署可行性，须在正文中补查。
- **基准场景维度偏窄**：实验只在自动驾驶道路场景上评测；对建筑遮挡严重、植被环绕或近距交会等非结构化场景的适应力尚不明确。
- **漂移补偿的“无界”问题**：时间漂移补偿依赖历史帧迭代修正，如果外推至极长轨迹（数百公里以上）或GPS信号拒止环境，其收敛性和误差上界尚需进一步考核。
- **时间代价风险**：实现更强的时序关联通常需要同时缓存多帧点云与图像，内存占用和计算时延在小型移动平台（无人机等）上可能成为瓶颈。
- **没有提供相对评估细节**：摘要只描述“相比先前方法提升x%”，但若缺少基线设置、后处理细节、测试分割说明，便无法完全排除对比口径差异风险，须谨慎阅读正文章节。
- **辅助损失的适用范围**：关键点感知损失依赖提取器对显著特征的响应，若场景纹理稀少或点云稀疏，则该思路是否依旧有效缺乏明确证据。

（完）
