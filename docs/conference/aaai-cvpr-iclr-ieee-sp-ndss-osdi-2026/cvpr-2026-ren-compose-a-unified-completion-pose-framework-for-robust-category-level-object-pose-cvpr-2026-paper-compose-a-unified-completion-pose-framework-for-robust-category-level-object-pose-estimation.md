---
title: "ComPose: A Unified Completion-Pose Framework for Robust Category-Level Object Pose Estimation"
title_zh: ComPose：面向鲁棒类别级物体位姿估计的统一补全-位姿框架
authors: "Ren, Huan, Chen, Yihan, Wang, Chuxin, Liu, Nailong, Yang, Wenfei, Zhang, Tianzhu"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Ren_ComPose_A_Unified_Completion-Pose_Framework_for_Robust_Category-Level_Object_Pose_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 7.0
evidence: 从残缺点云估计6自由度物体位姿，可迁移用于非合作航天器目标的鲁棒位姿估计
tldr: 针对残缺点云导致类别级物体位姿估计不准、独立补全带来误差累积的问题，提出ComPose统一框架，将形状补全与位姿回归紧耦合，以完整几何线索增强部分观测下的位姿推理。在通用物体位姿基准上验证了该框架能提升鲁棒性与效率。其非合作目标场景下的点云补全与位姿联合建模思路可直接用于航天器相对位姿估计。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 839, \"height\": 415, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1788, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 846, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 846, \"height\": 413, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 884, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 646, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 867, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ren-compose-a-unified-completion-pose-framework-for-robust-category-level-object-pose-cvpr-2026-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 185, \"label\": \"Table\"}]"
motivation: 观测点云常不完整，独立形状补全会引入复合误差并增加开销，限制位姿估计的鲁棒性。
method: 提出紧耦合形状补全与类别级位姿估计的统一框架，利用完整几何线索辅助鲁棒位姿回归。
result: 在类别级物体位姿基准上，精度与效率优于采用独立补全预处理的方法。
conclusion: 证明补全与位姿联合学习能有效缓解部分观测造成的估计退化，适用于目标点云缺失场景。
---

## Abstract
Category-level object pose estimation aims to predict the pose and size of arbitrary objects in specific categories. Existing methods struggle with the inherent incompleteness of observed point clouds, which limits their ability to capture complete object shapes for robust pose reasoning. While point cloud completion offers a promising solution, naively treating it as a separate preprocessing step for partial observations introduces compounding errors and additional computational overhead, ultimately hindering both accuracy and efficiency. To address these challenges, we propose ComPose, a novel unified framework that tightly integrates shape completion to provide complete geometric cues for enhanced pose estimation. At the core of ComPose is a keypoint-based progressive completion module, which recovers full shape representations by progressively predicting a sparse set of keypoints and their surrounding dense point sets, empowering the keypoints to capture holistic object geometries. A geometric relation encoding module further enriches keypoint features with both local and global geometric context. In addition, we introduce a novel geometric relation consistency loss to enforce structural alignment between observed keypoints and their predicted NOCS coordinates, ensuring globally coherent coordinate transformations. Extensive experiments on standard benchmarks demonstrate that our method outperforms state-of-the-art approaches without relying on category-level shape priors.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **任务背景**：类别级物体位姿估计（Category-level Object Pose Estimation）旨在预测某一预定义类别中任意物体的 6D 位姿（旋转矩阵 R、平移向量 t）和 3D 尺寸 s，是 3D 计算机视觉中的基础任务，广泛应用于机器人操控、增强现实、自动驾驶等领域。与实例级方法不同，类别级方法在推理时不需要实例专属 CAD 模型，更具泛化性。
- **核心问题**：真实深度传感器因目标物体自遮挡（self-occlusion）只能拍摄到部分点云（partial point cloud），这类天然不完整的几何输入严重限制了网络对完整物体结构的理解和位姿推理能力。现有大多数方法从部分点云直接编码几何结构，无法有效捕获完整形状。
- **已有解决思路的不足**：
  - 一些方法引入类别级形状先验（Shape Prior），在特征级别增强完整形状上下文，但仍基于本质上不完整的观测空间形状，根本的几何不完整问题未被解决；此外，收集 CAD 模型并训练额外的自编码器成本高昂。
  - 直接使用点云补全网络作为前置预处理步骤，构成两阶段串联流水线，存在误差累积和额外计算开销，损害精度与效率。
- **关键定量观察**：作者用 AG-Pose 网络进行了 oracle 实验，将输入部分点云替换为 GT 完整点云后，10°2cm 精度从 68.5% 提升至 91.7%，说明完整形状信息有巨大潜力；而简单端到端两阶段方案仅带来边际提升（71.0%）且推理速度从 33.5 FPS 降至 21.5 FPS，表明需要更紧密的统一架构设计。

## 2. 论文提出的方法论（ComPose 框架）

ComPose 是一个将形状补全与位姿估计无缝统一在单一网络中的框架，核心思想是**不以独立预处理步骤处理补全，而是将其作为任务驱动的内部组件**。

整体框架由四个部分组成：

1. **部分特征提取（Partial Feature Extraction）**
   - 用 PointNet++ 从部分点云 \( P_{part} \) 提取逐点几何特征；
   - RGB-D 设置中额外使用 DINOv2 提取与位姿一致的语义特征并与几何特征融合；
   - 通过自注意力层（Self-Attention）捕捉全局上下文，得到精细的部分表示 \( F_{part} \)。
2. **基于关键点的渐进补全（Keypoint-based Progressive Completion）**
   - **粗关键点生成**：由全局特征 MLP 预测可能缺失区域的关键点 \( C_{miss} \)，同时用最远点采样从可见部分获得 \( C_{vis} \)；二者组成候选集后经评分 MLP 自适应挑选 top-\( N_{kpt} \) 个关键点 \( C_{kpt} \)；
   - **渐进补全**：以粗关键点的位置编码和全局特征构造关键点查询 \( Q_{kpt} \)，在 Transformer 解码器中通过交叉注意力与部分特征交互，逐步细化得到精炼关键点 \( P_{kpt} \) 及其特征 \( F_{kpt} \)；每个关键点再扩展出 \( N_{fold} \) 个局部稠密点，最终形成完整稠密点云 \( P_{com} \)，共 1024 点；
   - 训练时用 Chamfer Distance 约束 \( C_{miss} \)、\( P_{kpt} \)、\( P_{com} \) 与 GT 变换模型 \( M_{obs} \) 对齐（损失 \( L_{com} \)）；对关键点选择施加 MSE 分数回归损失 \( L_{score} \)。
3. **几何关系编码（Geometric Relation Encoding）**
   - 借鉴 AG-Pose，为每个关键点在其 \( N_{knn} \) 个最近邻上计算局部几何关系嵌入 \( E_l \)，并计算关键点间的全局几何关系嵌入 \( E_g \)；
   - 通过交叉注意力与交替增强过程获得几何感知关键点特征 \( F_{geo} \)，兼顾局部细节与全局结构上下文。
4. **基于对应的位姿估计（Correspondence-based Pose Estimation）**
   - 用 MLP 从 \( F_{geo} \) 预测每个关键点的 NOCS 坐标 \( O_{kpt} \)；
   - 通过 Umeyama 算法直接拟合旋转、平移和尺寸。
   - **损失函数**：
     - 逐点对应损失 \( L_{corr} \)（预测 NOCS 与 GT NOCS 的 L2/Smooth-L1 距离）；
     - 本文新提出的**几何关系一致性损失 \( L_{geo} \)**：构建观测空间按尺度归一化的关键点两两距离矩阵 \( G_{kpt} \) 与预测 NOCS 空间中同构的两两距离矩阵 \( G_{nocs} \)，约束二者一致，从而保持从观测空间到规范空间坐标变换的结构一致性，捕获高阶结构线索。总损失为各项加权求和：\( L_{all} = \lambda_{com}L_{com} + \lambda_{score}L_{score} + \lambda_{corr}L_{corr} + \lambda_{geo}L_{geo} \)。

## 3. 实验设计（数据集 / 基准 / 对比方法）

- **数据集**：
  - **CAMERA25**：合成数据集，来自 REAL275 基准，6 个物体类别，275K 训练 / 25K 测试，混合现实渲染；
  - **REAL275**：真实数据集，4.3K 训练（7 个场景）/ 2.75K 测试（6 个场景），6 类日常物体；
  - **HouseCat6D**：更全面的新兴真实世界基准，含 10 类家庭物体、20K 训练（34 场景）/ 3K 测试（5 场景），包含强遮挡与视角多样的光照挑战物体。
- **评估指标**：
  - 6D 位姿：\( n°mcm \) mAP（旋转误差 < n°、平移误差 < m cm 的预测比例），重点为 5°2cm、5°5cm、10°2cm、10°5cm；
  - 位姿+尺寸联合评估：3D IoU（阈值 x%）mAP。
- **对比方法**（REAL275 表 1）：
  - RGB-D 设置：SPD、SGPA、DPDN、GCE-Pose、VI-Net、SecondPose、AG-Pose、SpherePose、SpotPose、CleanPose；
  - 仅深度设置：SAR-Net、RBP-Pose、DR-Pose、GPV-Pose、HS-Pose、Query6DoF、AG-Pose*（复现），并标明了哪些方法采用形状先验。
  - RGB-D 下无先验方法对比；作者另对 AG-Pose 做了复现（标 *），保证公平性。
- **补全性能比较**：与 SPD、SGPA、DR-Pose 在**部分点云补全或形状重建任务**上比较（表 3）。这是论文首次在任意姿态下于观测空间做补全，而非在规范空间重建。用单位缩放 CD（CD unit）和观测空间 CD 两个指标衡量。作者在文末附上了“camera”类别部分形状补全示例的可视化结果。
- **遮挡鲁棒性评估**：在 REAL275 上对分割掩码加 25% 遮挡噪声对比 AG-Pose。

## 4. 资源与算力

- **硬件**：单张 RTX3090Ti GPU（推理 FPS 实验均在此 GPU 测量）；作者在显式说明部分（4.3节、图2）以 RTX3090Ti 测速，并在实验设置部分明确“All experiments are conducted on a single RTX3090Ti GPU”。
- **训练配置**：batch size = 24，训练 200K 次迭代，Adam 优化器，初始学习率 0.001，余弦退火调度；RTX3090Ti 的显存容量为 24 GB。
- **未明确信息**：论文未明确说明 GPU 数量、总训练时长、能源消耗与训练代价；只给出了单卡与迭代次数，无法判断总算力开销。

## 5. 实验数量与充分性

- **主实验**：
  - REAL275 上同时报告 RGB-D 与仅深度两种设置（表 1）；
  - HouseCat6D 上同样两种设置（表 2）；
- **形状补全性能专门实验**（表 3），与 SPD / SGPA / DR-Pose 对比；在 camera 类别上报告 CD。
- **遮挡增强测试**（表 4），与 AG-Pose 对比并量化性能下降幅度。
- **消融实验**：
  - 形状补全策略消融：部分实例重建 vs 完整形状重建，以及是否补全稠密点云 \( P_{com} \)（表 5）；
  - 统一框架 vs 两阶段流水线的精度与效率对比（图 2）；
  - 渐进补全过程消融：静态查询 vs PoinTr 式 vs AdaPoinTr 式 vs 本文渐进式，以及有无监督、是否自适应关键点选择（Nmiss/Nvis 不同组合）（表 6）；
  - 几何关系建模消融：编码模块和一致性损失分别开/关（表 7）。
- **结论与评估**：
  - 实验总体上较充分：数据集覆盖合成与真实（含更难的 HouseCat6D）、设置覆盖有 RGB 与无 RGB、并行了大量消融和可视化（补全过程和位姿对比），公平性方面也较好（复现 AG-Pose、标注是否使用先验、统一遮挡模拟条件、对补全性能报告两种指标以公平对比）。然而，仍缺乏跨数据集泛化实验（如在 REAL275 训练后直接测试在其他数据上），并且消融全部在仅深度 REAL275 上完成，未覆盖 RGB-D 场景下的消融验证。

## 6. 论文的主要结论与发现

- **完整的几何线索对类别级位姿估计具有决定性作用**：将部分点云换成 GT 完整点云可使 10°2cm 从 68.5% 提升至 91.7%（oracle 实验）。
- **独立的两阶段补全-位姿流水线效率与精度都不理想**（71.0% 精度 / 21.5 FPS），说明简单串联不能释放形状补全的潜力。
- **ComPose 统一框架实现精度-效率双赢**（77.8% / 38.4 FPS），在仅深度和 RGB-D 设置下均超越现有方法且无需类别级形状先验。
- **渐进补全模块 + 稠密点补全有效增强关键点对完整形状的感知**（表 5：完整形状比部分重建提升约 6% 的 5°2cm 精度）。
- **几何关系编码和几何关系一致性损失**分别提升 4.3% 和 1.8%（5°2cm），对鲁棒坐标变换起着关键保证作用。
- 在苛刻的遮挡条件下（25% 掩码遮挡），ComPose 性能下降幅度小于基线，体现更强鲁棒性。

## 7. 优点（方法与实验亮点）

- **范式创新**：明确将 point cloud completion 嵌入位姿估计任务内部，完成“补全增强推理”的统一范式；实验中给出了支撑该范式的 oracle 证据。
- **任务驱动的补全设计**：不是为目标单独优化补全质量，而是用关键点沟通“补全”和“位姿”，使几何特征直接为位姿推理服务。
- **无需外部形状先验**：避开先验需要 CAD 模型和额外自编码器的问题，降低了数据与训练成本；表 3 说明其补全质量还超过有先验的方法。
- **自适应关键点选择**：同时考虑可见与缺失区域关键点，加上可学习的评分与筛选机制，比静态方案（如 PoinTr/AdaPoinTr）更适合真实场景严重不完整的情形。
- **结构性约束**：几何关系一致性损失直接约束观测空间与 NOCS 空间的相对结构而非绝对坐标，避免“平凡坐标误差掩盖结构性错误”的问题。
- **实验设计细致**：包含 oracle 上界分析、效率（FPS）对比、遮挡压力测试、每层次模块消融，并复现基线，评估公平性和透明性较好。
- **兼顾实用效率**：通过模块复用和网络剪枝达到比原始 AG-Pose 更快的推理速度。

## 8. 不足与局限

- **算力细节不完备**：未报告 GPU 数量/总训练时间/模型的完整参数量与内存占用，不利于复现和对比工程代价。
- **遮挡实验局限**：仅做 25% 一种遮挡比例的模拟测试，未覆盖不同程度、不同方向遮挡的连续分析。
- **数据集与类别有限**：REAL275 和 HouseCat6D 均以室内物体为主，缺少自动驾驶/工业场景；未做跨域（合成到真实、不同传感器）的泛化测试。
- **补全真实性有限**：利用 CAD 模型变换作为补全的监督与真值，在观测空间直接对齐，需要背景干净的可见部分（仅关注物体本体），对于多物体相互遮挡的实际复杂场景，说明不够。
- **仅深度消融集中在单一数据集**：消融实验仅在 REAL275 depth-only 设置上完成，未展示 RGB-D 上的消融表现。
- **对 DINOv2 的依赖**：RGB-D 下依赖 DINOv2 的语义特征，该特征是在自然图像上预训练的，对某些非自然物体可能不匹配；论文未探讨这一外部预训练模型的失效边界。
- **定位与贡献边界**：该方法为“紧耦合内嵌补全”，对特别严重的点云缺失（如完全遮挡）仍可能失效；论文未充分讨论此极端场景。

（完）
