---
title: SE(3)-Equivariance with Geometric and Topological Guidance for Category-Level Object Pose Estimation
title_zh: SEGPose：具有几何与拓扑引导的SE(3)等变类别级物体位姿估计
authors: "Yu, Sheng, Zhai, Di-Hua, Xia, Yuanqing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Yu_SE3-Equivariance_with_Geometric_and_Topological_Guidance_for_Category-Level_Object_Pose_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 7.0
evidence: 点云类别级6自由度位姿估计，融合SE(3)等变与几何拓扑约束，可支撑无纹理航天器目标的位姿估计
tldr: 针对纯点云类别级物体位姿估计难度大的问题，提出SEGPose，在特征提取与三维重建中引入几何与拓扑约束，并利用SE(3)等变性提高网络位姿预测精度。该方法通过有效的目标形状重建增强对未知物体的泛化。实验结果显示其精度优于仅使用点云的既有类别级位姿方法。这种不依赖纹理的等变几何建模对航天器这类无纹理目标相对位姿估计具有直接参考价值。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1633, \"height\": 843, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1773, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 841, \"height\": 294, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1719, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1530, \"height\": 492, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 361, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-se3-equivariance-with-geometric-and-topological-guidance-for-category-level-object-pose-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 649, \"height\": 201, \"label\": \"Table\"}]"
motivation: 仅凭点云估计类别级物体位姿具有挑战性，纹理缺失时尤其需要几何、拓扑与姿态等变约束。
method: 使用约束驱动特征提取与三维重建，并引入SE(3)等变网络结构，以几何拓扑信息辅助位姿预测。
result: 在点云类别级位姿估计任务上取得更优的位姿精度。
conclusion: 验证几何拓扑先验和旋转等变规则可有效提升点云目标位姿估计的泛化与准确性。
---

## Abstract
Object pose estimation is a key task for embodied robots, enabling them to interact with objects effectively. Category-level object pose estimation provides a way for robots to estimate the pose of unknown objects. However, estimating object pose from point clouds alone remains challenging. In this paper, we introduce SEGPose, a novel category-level object pose estimation method based on point clouds. Unlike previous methods, SEGPose leverages geometric, topological information, and SE(3)-equivariance, enhancing the network's accuracy in pose prediction. To utilize geometric and topological features, we propose a constraint-based feature extraction and 3D reconstruction method, enabling effective object shape reconstruction. We also design an SE(3)-equivariance feature prediction network to handle pose transformations consistently across viewpoints, improving pose accuracy. Experimental results on benchmark datasets show that SEGPose outperforms all current category-level pose estimation methods based on point clouds. Additionally, we apply the SEGPose to the robotic grasping tasks in real-world scenarios, and the results indicate that SEGPose exhibits excellent generalization capabilities.

---

## 论文详细总结（自动生成）

# SEGPose 论文详细中文总结

## 一、核心问题与研究动机

- **研究背景**：物体位姿估计是具身机器人实现有效交互的关键任务。类别级物体位姿估计旨在对已知类别中的**未见物体**进行位姿预测，无需特定 CAD 模型，具有重要实用价值。
- **核心问题**：仅凭点云数据（纯深度信息）进行类别级位姿估计仍面临较大挑战。现有基于深度的方法（如 GPV-Pose、HS-Pose）主要聚焦于几何特征，忽略了点云中蕴含的**拓扑/图结构信息**（同类别物体常共享拓扑结构，有助于点云重建与位姿估计）。
- **另一关键缺口**：大多数现有方法未利用点云的**SE(3)-等变性**。在机器人抓取等动态场景中，目标运动和相机视角变化使点云发生连续变换，理想情况下预测位姿应同步适配输入变换，这一性质即 SE(3)-等变性，对提升动态场景下的位姿精度至关重要。
- **本文主张**：首次将几何信息、拓扑信息和 SE(3)-等变性三类点云属性同时引入类别级位姿估计，以解决纯点云条件下位姿预测精度不足的问题。
- **应用价值**：在暗光或无纹理环境中，RGB 不可靠或缺失时，仅依靠深度信息实现对未知物体（如航天器这类无纹理目标）的位姿估计，是该方法的重要应用场景。

## 二、方法论

### 1. 总体框架（Pipeline）
- 输入 RGB + 深度图 → Mask-RCNN 实例分割获取目标 mask → 裁剪深度图得到目标点云 P(o) ∈ R^(N_o×3)。
- SEGPose 的训练流程包含四个主要环节：
  1. **几何与拓扑特征提取**（HS-encoder + 图模块）
  2. **拓扑引导的三维重建**
  3. **SE(3)-等变特征编码**
  4. **SE(3)-等变引导的位姿估计头**
- 最后通过将重建点云与 ground truth NOCS 点云对齐实现位姿精修。
- 预测量为旋转 R ∈ SO(3)、平移 t ∈ R³、尺寸 s ∈ R³。

### 2. 拓扑标签的构造（Topological Label）
- 使用**持久同调算法**提取点云的拓扑特征，以持久图（persistence diagrams）表示，包含 1D（D1）和 2D（D2）拓扑特征。
- 由于持久图由不连续的“出生-死亡”点构成，难以端到端训练：
  - 先通过线性变换 T(x,y) = (x, y−x) 得到“出生-持续”坐标；
  - 利用**正则化高斯核**将离散点转换为连续分布 N(p|p̄, σ²)；
  - 设计权重 w = (y−x)/t（t 为图中最大持续值），突出长持续特征；
  - 计算持久表面 S_D*(p)，划分 M×M 块并做双重积分，得到持久图像 I1 和 I2，作为网络训练的拓扑标签。

### 3. 几何与拓扑特征提取与重建
- 使用 HS-encoder 提取点云几何特征 F。
- 采用 CatFormer 中提出的 transformer 图模块构建多重拓扑图，提取拓扑特征 F_topo。
- 通过拓扑信息引导头（基于 adaptive max pooling + MLP）预测点云的 1D 和 2D 持久图像。
- **双重拓扑约束**：
  - 点云拓扑约束（L_pt）：预测的持久图像逼近目标物体实测拓扑标签。
  - 类别级拓扑约束（L_ct）：利用平衡因子 α = e^(−2L_pt⁎) 使预测结果对齐类别级拓扑先验（对噪声/离群点导致的错误标签保持鲁棒）。
- 结合几何与拓扑特征完成三维重建 P_recon，使重建既保持几何精度又符合真实拓扑结构。

### 4. SE(3)-等变特征提取与位姿估计
- 以 **Vector Neuron Networks (VNNs)** 为骨干：采用 VNN-DGCNN 层提取等变特征，利用向量表示捕捉空间信息。
- 融合各 VNN 层输出 → F_fuse；经 VNN-Linear 调整后与 F_fuse 做逐元素乘积 → F_se。
- 用 F_fuse 通过 MLP 预测形状权重，调整点云形状得到 P_adj；拼接 P_adj 与 F_se，经 MLP 得到最终 SE(3)-等变特征 F_SE。
- 提出 **SE(3)-等变引导的位姿估计头**：将 SE(3)-等变特征与点云特征（经 1D 卷积 / VNN-Linear 处理）拼接融合，经 Sigmoid 生成权重调整点云特征，最终预测旋转分量 R_r、R_b（合成 R）与平移 t、尺寸 s。

### 5. 损失函数
- 总损失：L = L_basic + λ3·L_pt + L_ct + L_alig + λ4·(L_F + L_rec) + λ5·L_sdf
- **L_basic**：位姿损失 + 对称重建损失（与 GPV-Pose/HS-Pose 相同），λ1=8, λ2=1。
- **L_pt / L_ct**：分别用 MAE 衡量点云拓扑持久图像和类别级持久图像的预测误差（L_ct 带自适应权重 α）。
- **L_alig**：Density Chamfer Distance，将重建点云变换到 NOCS 空间与类别级 NOCS 点云对齐，用于位姿纠偏（无需特定 CAD 模型），β1=0.5, β2=1。
- **L_F**：余弦相似度，约束增强点云与原始点云特征的一致性。
- **L_rec**：重建损失（沿用 GPV-Pose）。
- **L_sdf**：基于 SDF 的包围盒-位姿一致性损失，将物体按包围盒分为内/外/表面三区域，以 L1 度量预测误差，保证包围盒预测与位姿估计协同（SE(3)-等变的强一致性约束）。

## 三、实验设计

### 1. 数据集与 Benchmark
- **CAMERA25 数据集**（合成）：约 30 万张训练图像、2.5 万张评估图像，虚拟合成物体叠加到真实场景。
- **REAL275 数据集**（真实）：7 个场景 4300 张真实训练图像，6 个场景 2750 张评估图像。
- 共含 6 个类别：bottle、bowl、camera、can、laptop、mug。
- **Wild6D 数据集**（跨域泛化）：含 5 个类别的真实世界多样场景。

### 2. 评估指标
- 3D IoU（阈值 0.5 / 0.75）
- 5°2cm、5°5cm、10°2cm、10°5cm（旋转角度 + 平移距离联合判定）
- 机器人抓取成功率和 mAP。

### 3. 对比方法
- **纯深度方法（D）**：SAR-Net、GPV-Pose、SSP-Pose、DR-Pose、RBP-Pose、HS-Pose、TG-Pose、HRC-Pose。
- **RGB-D 方法**：NOCS、DualPoseNet、SPD、SGPA、CatFormer、VI-Net、AG-Pose、SpotPose。

## 四、资源与算力

- 论文明确提到：所有实验在**单张 NVIDIA RTX 3090 GPU** 上完成。
- 相关超参数：batch size = 24，初始学习率 = 1e−4，使用余弦退火学习率调度。
- 输入点云点数 No=1024。
- **未在文中披露**：训练总时长、GPU 数量、模型参数规模等细节。

## 五、实验数量与充分性分析

### 1. 实验组数概览
论文共包含四大组实验：
- **主 Benchmark 对比**（CAMERA25 + REAL275，两种模态方法横向对比）
- **Ablation 消融研究**（表 2，含 A–E 五大细分模块的逐步消融，覆盖拓扑、SE(3)、重建、位姿头、增广等约十余个子实验）
- **跨域泛化测试**（Wild6D 数据集）
- **真实机器人抓取实验**（6 类任务）

### 2. 消融实验的充分性
消融设计较全面：
- 整模块移除（拓扑/SE(3) 各自与联合移除）；
- 拓扑重建消融（(B)）、SE(3)-位姿头消融（(C)）、数据增广消融（(D)）；
- 损失函数逐项消融（(E)：L_pt、L_ct、L_alig、L_F、L_rec、L_sdf）。

### 3. 客观性与公平性评价
- **优点**：与深度方法在同类输入（纯点云）下对齐；消融组间排除了上位模块干扰，逻辑清晰。
- **不足**：与 RGB-D 方法对比时，未将方法改为 RGB-D 输入进行同条件对比（引用模态差异解释与 SpotPose 的差距），公平性存疑；部分已发表方法在特定指标上未报告完整数值（如表 1 中部分方法仅报告部分指标），直接比较不同方法间缺失项时需谨慎。

## 六、主要结论与发现

- 在 CAMERA25 数据集上，SEGPose 在深度方法中达到最优：IoU50=93.7、IoU75=90.5、5°2cm=76.3、5°5cm=82.9。
- 在 REAL275 数据集上，SEGPose 在大部分核心指标上超越此前深度方法 SOTA（HRC-Pose），如 IoU75=78.3、5°5cm=61.1、10°5cm=87.1，但 IoU50（83.1）低于 HRC-Pose（83.4），整体优于后者。
- SEGPose 还超越多数 RGB-D 方法，但仍不及 RGB-D 的 SOTA SpotPose；论文将其归因于 SpotPose 使用了 RGB-D 双模态信息以获得更高精度。
- 消融研究表明：拓扑引导对性能增益高于 SE(3)-等变模块；两者结合效果最佳；各损失项均对性能有正向贡献；拓扑点云损失 L_pt 优于单纯类别级拓扑损失 L_ct。
- Wild6D 跨域实验：SEGPose 在深度方法中全面领先（IoU50=72.2），表明其泛化能力优于对比方法。
- 真实机器人实验：SEGPose 在 6 类抓取任务中均取得最高成功率（64.4%–88.9%），显著超越 6-DOF GraspNet（26.7%–68.9%）、GPV-Pose（26.7%–71.1%）和 HS-Pose（55.6%–75.6%）。

## 七、主要优点

- **首创性**：首次同时将几何信息、拓扑信息和 SE(3)-等变性整合到类别级物体位姿估计网络中。
- **纯深度（点云）路线**：在暗光、纹理缺失环境下仍然可用，不依赖 RGB 纹理，有较高实用价值。
- **拓扑建模完善**：从持久同调到持久图像、再到类别级拓扑约束的完整技术链条，设计合理且可微、可训练。
- **方法互补性**：拓扑引导改善重建质量 → 几何与拓扑双约束提升点云重建 & NOCS 对齐 → SE(3)-等变增强网络对视角/位姿变化的适应力，各模块逻辑上相互增益。
- **算法效率较好**：在提升精度的同时维持约 45.8 FPS 的推理速度，优于多数 SOTA 对比方法。
- **验证充分有层次**：合成数据 + 真实数据 + 跨域泛化 + 物理机器人 6 类真实抓取任务验证，整体使结论具有说服力。
- **对无纹理目标相对位姿估计有直接参考价值**（如航天器这类纹理缺失目标）。

## 八、不足与局限性

- **与 RGB-D SOTA 仍存在差距**：尽管文本上优于大多数 RGB-D 方法，但性能仍不及 SpotPose；论文将此归因于模态差异，却未做同等输入条件下的控制实验来充分证明纯深度方法的优势或缩小差距。
- **部分深度对比方法数据不完整**：某些方法（如 GPV-Pose、SSP-Pose、HRC-Pose）在表格中只报告了部分指标，影响全方位的公平比较；SSP-Pose 在 REAL275 集上无 IoU50 数据，HRC-Pose 的 FPS 未报告，削弱了比较的系统性。
- **类别范围有限**：REAL275 → 6 类、Wild6D → 5 类，未覆盖更广泛的物体类别（如碗、瓶盖等对称或无结构物体之外的类别）；对称物体、多实例场景的处理未具体探讨。
- **依赖实例分割**：使用 Mask-RCNN 获取目标点云，若分割错误会影响后续整体精度（如遮挡严重场景），论文未单独讨论分割错误带来的级联影响。
- **算力披露不足**：未给出训练时长、参数量或能耗等；复现成本不透明。
- **拓扑标签计算约束**：点云质量差、噪声大时，持久同调结果的稳定性与有效性仍面临挑战；类别级拓扑约束虽可缓解，但不同形状实例间差异大时的鲁棒性未深入验证。
- **仅限类别级**：依赖类别级先验信息，无法支持 未知类别的物体和大型结构的位姿估计，在一定程度上限制了方法在开放世界中的应用。

（完）
