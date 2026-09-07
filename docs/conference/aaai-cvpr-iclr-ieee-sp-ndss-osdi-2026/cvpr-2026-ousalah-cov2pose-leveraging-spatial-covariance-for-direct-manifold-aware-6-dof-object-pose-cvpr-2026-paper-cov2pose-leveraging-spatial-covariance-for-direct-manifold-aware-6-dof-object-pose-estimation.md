---
title: "Cov2Pose: Leveraging Spatial Covariance for Direct Manifold-aware 6-DoF Object Pose Estimation"
title_zh: Cov2Pose：利用空间协方差进行流形感知的直接6自由度物体姿态估计
authors: "Ousalah, Nassim Ali, Rostami, Peyman, Gaudillière, Vincent, Koumandakis, Emmanuel, Kacem, Anis, Ghorbel, Enjie, Aouada, Djamila"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Ousalah_Cov2Pose_Leveraging_Spatial_Covariance_for_Direct_Manifold-aware_6-DoF_Object_Pose_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 8.0
evidence: 从单张RGB图像直接估计6D物体位姿，协方差池化加流形感知回归可直接迁移至单目航天器位姿估计
tldr: 单张RGB图像的6自由度物体位姿估计中，直接回归方法速度快但常忽略特征二阶统计量并输出不连续姿态表示。Cov2Pose提出协方差池化表征卷积特征的空间分布，并结合流形感知回归以更稳健地预测姿态。实验表明直接位姿回归精度有所提升且保持计算高效。该方法面向通用物体，是单目航天器位姿估计的重要技术基座。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 821, \"height\": 490, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 348, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 736, \"height\": 746, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 873, \"height\": 438, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1784, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 877, \"height\": 166, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 793, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ousalah-cov2pose-leveraging-spatial-covariance-for-direct-manifold-aware-6-dof-object-pose-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 398, \"label\": \"Table\"}]"
motivation: 现有直接位姿回归使用全局池化特征，忽略空间二阶统计量且输出不连续位姿表示，导致精度和鲁棒性不足。
method: 提出协方差池化与流形感知的直接回归头，在单个RGB图像上端到端预测6自由度物体位姿。
result: 在保持端到端效率的同时提升直接回归的位姿精度与鲁棒性，可与间接PnP方法互补。
conclusion: 为单目6D位姿直接回归提供了更有效的特征与表示方案，可应用于航天器对目标位姿估计。
---

## Abstract
In this paper, we address the problem of 6-DoF object pose estimation from a single RGB image. Indirect methods that typically predict intermediate 2D keypoints, followed by a Perspective-n-Point solver, have shown great performance. Direct approaches, which regress the pose in an end-to-end manner, are usually computationally more efficient but less accurate. However, direct pose regression heads rely on globally pooled features, ignoring spatial second-order statistics despite their informativeness in pose prediction. They also predict, in most cases, discontinuous pose representations that lack robustness. Herein, we therefore propose a covariance-pooled representation that encodes convolutional feature distributions as a symmetric positive definite (SPD) matrix. Moreover, we propose a novel pose encoding in the form of an SPD matrix via its Cholesky decomposition. Pose is then regressed in an end-to-end manner with a manifold-aware network head, taking into account the Riemannian geometry of SPD matrices. Experiments and ablations consistently demonstrate the relevance of second-order pooling and continuous representations for direct pose regression, including under partial occlusion.

---

## 论文详细总结（自动生成）

# Cov2Pose 论文深度分析

## 1. 核心问题与研究动机

- **任务背景**：从单张 RGB 图像估计物体的 6 自由度（6-DoF）位姿（旋转 + 平移，P ∈ SE(3)），是机器人操作、AR/VR、自主导航、工业检测等领域的核心视觉问题。
- **现有方法的两大阵营**：
  - **间接方法**（如 PnP-based、render-and-compare）：先预测 2D 关键点或稠密对应关系，再通过 PnP 等几何求解器解算位姿，精度高但**计算开销大**、含迭代过程。
  - **直接回归方法**（end-to-end）：从图像直接回归位姿参数，速度快但**精度显著偏低**。
- **直接回归方法的两大缺陷（本文核心问题）**：
  1. **特征信息不足**：现有直接回归头依赖全局平均/最大池化后的特征，仅利用了一阶统计量，忽略了**空间二阶统计量**（即协方差信息）。作者通过实验（图 1）证明：特征空间协方差之间的距离与真实位姿间的 SE(3) 测地距离呈显著正相关，而展平特征的余弦距离几乎不随位姿变化——说明协方差是更具判别力的位姿表征。
  2. **位姿表示不连续**：大多数直接方法使用四元数或欧拉角回归旋转，这些表示在 SO(3) 上存在**不连续性**，导致训练不稳定、精度受限。
- **研究目标**：构建一种**兼顾直接回归效率与精度**的框架，通过引入二阶统计量和连续位姿表示来弥合直接法与间接法之间的精度差距。

## 2. 方法论

### 2.1 核心思想

提出 **Cov2Pose**——首个基于协方差池化（covariance pooling）的端到端 6-DoF 位姿回归框架。核心设计遵循一条原则：**特征编码和位姿解码都应尊重数据所在的几何结构**——即特征协方差矩阵所在的空间是对称正定（SPD）矩阵的黎曼流形。

整个流程可分解为两个映射的复合：

- 特征提取 Γ: I → S₊₊ⁿ（空间协方差 + SPD 流形上的降维层）
- 位姿解码 Ψ: S₊₊ⁿ → P（Cholesky 分解 + Gram-Schmidt → SO(3)×R³）

### 2.2 协方差特征提取（Γ）

- 使用 CNN 骨干（EfficientNet-B6）提取特征图 F ∈ R^(C×H×W)，输出空间分辨率 H=W=17。
- 将特征图展平为 X ∈ R^(C×N)（N=H×W），计算**空间协方差矩阵**（像素位置间的协变关系）：

  Σ̂ = (1/(C−1)) Σᵢ (Xᵢ − μ_X)ᵀ(Xᵢ − μ_X) ∈ S₊₊²⁸⁹

- 由于协方差矩阵维度高（289×289），需要使用 SPD 流形上的专用降维层：
  - **BiMap 层**（Bilinear Mapping）：通过列正交权重 W 做共轭变换 Y = WᵀXW，使维度从 n 压缩至 m（m<n），同时保持 SPD 结构；训练中通过 QR retraction 将权重约束在 Stiefel 流形上。
  - **ReEig 层**：类似于 ReLU，通过谱分解将过小的特征值抬升到阈值 ε=10⁻⁴，保证输出严格正定。
- 经过 L=4 组 BiMap+ReEig 层后，得到紧凑 SPD 矩阵 Σ_L ∈ S₊₊⁴。

### 2.3 从 SPD 到位姿的连续映射（Ψ）

- **关键设计**：使用 **Cholesky 分解** Σ_L = LLᵀ 将 SPD 矩阵编码为下三角矩阵 L ∈ R^{4×4}（10 个非零元素），其非零元素恰好编码 9 个位姿自由度（6D 旋转 + 3D 平移）+ 1 个归一化约束：

  L = [e^{tₓ}, 0, 0, 0; u₁, e^{t_y}, 0, 0; u₂, v₁, e^{t_z}, 0; u₃, v₂, v₃, e^{−(tₓ+t_y+t_z)}]

- 从 L 中提取：
  - 平移向量 t̂ = (log L₁₁, log L₂₂, log L₃₃)
  - 两个 3D 向量 û = (L₂₁, L₃₁, L₄₁) 和 v̂ = (L₃₂, L₄₂, L₄₃)，构成 **6D 旋转表示**（Stiefel 流形 V₂(R³)），再经**可微 Gram-Schmidt 正交化** + 叉积补齐第三维，得到 R ∈ SO(3)。
- **完整性保证**：L 对角线取指数形式确保正定性；L₄₄ = e^{−(tₓ+t_y+t_z)} 使 det(Σ_L) = 1（几何平均归一化）。
- Cholesky 分解具有**单射性、连续性和可微性**，满足端到端训练的要求。

### 2.4 训练损失

总损失 = SO(3) 上的**测地距离损失**（arccos[(tr(R̂ᵀR_gt)−1)/2]）+ R³ 上的 ℓ2 平移损失 + 正交性正则化项（⟨û, v̂⟩→0 和 ∥û∥=∥v̂∥=1），其中 λ=10⁻³。

### 2.5 优化策略

使用**混合几何优化器**：Stiefel 约束的 BiMap 权重采用黎曼梯度步（投影 + QR retraction，学习率 10⁻²），骨干网络参数使用 Adam（学习率 10⁻⁴），配合 ReduceLROnPlateau 调度器。

## 3. 实验设计

### 3.1 数据集与 Benchmark

| 数据集 | 内容 | 训练/测试协议 |
|--------|------|---------------|
| **LineMOD (LM)** | 13 类物体，16k 张图像，重度杂乱场景 | 默认 BOP split，85% RGB 图像测试 |
| **LineMOD Occlusion (LM-O)** | 8 类物体，1214 张标注图像，重度遮挡 | 使用公开 pbr 合成图像训练 |
| **YCB-Video (YCB-V)** | 21 类物体，约 100k 张真实图像 | YCB-V 真实图像 + pbr 合成图像训练 |

### 3.2 评估指标

- **ADD / ADD-S**：模型点经 GT 位姿与预测位姿变换后的平均距离，低于模型直径 10% 判定为正确，报告正确率。
- **AUC of ADD-S / ADD(-S)**：在 YCB-V 上以 10 cm 为最大阈值计算曲线下面积。

### 3.3 对比方法

- **间接方法**：PVNet、ZebraPose、CheckerPose、VAPO、6D-Diff（对应点 + PnP/RANSAC）
- **直接/端到端方法**：PoseCNN、Pix2Pose、DeepIM、Single-Stage、GDR-Net、Self6D++、EPro-PnP（可微 PnP）、BPnP

### 3.4 主要实验结果

- **LM**：Cov2Pose 平均 ADD(-S) 达 **97.2%**，超越所有端到端方法（含 DeepIM 88.6%），并**超过所有 PnP 方法**（EPro-PnP 95.8%），在多个物体类别（Eggbox、Glue、Phone 等）上取得 100%。
- **LM-O**：平均 ADD(-S) 达 **76.8%**，大幅超越所有端到端方法（GDR-Net 为 62.2%），与最佳间接方法 ZebraPose（76.9%）仅差 0.1%。
- **YCB-V**：ADD(-S) 达 **69.7%**（端到端方法中最佳），AUC of ADD-S 达 90.0%，但与最佳 PnP 方法（VAPO 为 84.9% ADD(-S)）间仍存在约 15 个百分点的差距。

### 3.5 消融实验

1. **旋转表示对比**：6D + Gram-Schmidt 连续表示（76.8%）显著优于欧拉角（70.9%），验证了连续表示的有效性。
2. **SPD 头 vs. 欧氏 MLP 头**：用全连接层替代 SPD 头后精度骤降至 31.0%，证实了流形感知降维的必要性（欧氏层不匹配 SPD 几何，破坏正定性）。
3. **空间协方差 vs. 通道协方差**：空间协方差（76.8%）优于通道协方差（70.9%），说明像素间协变信息对位姿更关键。
4. **Cholesky 位姿解码 vs. log-tangent 空间监督**：直接对 SO(3)×R³ 监督（76.8%）优于在 SPD 对数切空间上训练（72.3%）。

## 4. 资源与算力

文中明确说明：

- **GPU**：4 × NVIDIA A100（40 GB）
- **Batch size**：8
- **训练轮数**：LM/LM-O 上 30 epochs，YCB-V 上 20 epochs
- **训练集划分**：90% 训练 / 10% 验证，基于验证集最优 checkpoint 测试
- **模型参数量**：41.4M
- **推理时间**：46.9 ms（骨干 22.6ms + 协方差池化 0.5ms + 位姿头 23.8ms），在 A100 上测量
- 文中未提及具体训练总时长（小时数），也未说明能源消耗。

## 5. 实验数量与充分性评估

### 实验数量

论文共包含：
- **3 个标准数据集的系统性评测**（LM、LM-O、YCB-V），覆盖面较广。
- **2 组消融实验**（旋转表示对比 + 三个框架变体对比），外加图 1 的动机验证实验和图 4 的定性结果。
- 推理时间对比实验。

### 充分性评估

**充分之处**：
- 在三个 BOP 基准上与当前 SOTA（含间接和直接方法）进行了全面对比，表格完整、指标标准。
- 消融实验设计针对性强，逐一验证了三大核心贡献（协方差池化、SPD 头、Cholesky 连续解码），实验结论与主张一致。

**不足之处**：
- 表 4 的消融仅给出平均指标，未报告逐类别细粒度结果，统计显著性（方差/多次运行）未讨论。
- 未在类别级/实例级位姿估计（如 Category-level NOCS 数据集）或非 BOP 基准上验证。
- 表 1 中 LM 数据集 13 个类别上与 GDR-Net 等近期方法的逐类别对比部分缺失（"—"），对比完整性受限。
- 文中未报告不同遮挡程度下的分层性能拆分，对 LM-O 的"重度遮挡"具体场景分析不够细致。

## 6. 主要结论与发现

1. **空间协方差是位姿估计的有效特征**：特征图的空间协方差与位姿变化高度相关（图 1），而一阶统计量（展平特征）几乎不含位姿判别信息。
2. **二阶统计量 + 流形感知学习可显著提升直接回归精度**：Cov2Pose 在三个数据集的端到端方法中均取得 SOTA；在 LM 上甚至超越了基于 PnP 的间接方法。
3. **连续旋转表示优于非连续表示**：6D 表示 + 可微 Gram-Schmidt 比欧拉角高出约 6 个百分点的 ADD(-S)。
4. **几何约束不可忽视**：对 SPD 特征使用欧氏降维层会导致精度崩溃（从 76.8%降至 31.0%），证明流形感知的深度结构至关重要。
5. **精度-速度平衡好**：46.9ms 的推理时间优于大多数间接方法，同时在端到端方法中精度最高，适合实时应用。
6. 在 LM-O（遮挡场景）上，Cov2Pose 仍保持较强性能（76.8%），说明协方差表征对局部遮挡具有一定鲁棒性。

## 7. 优点与亮点

- **问题定位准确**：通过数据驱动的可视化实验（图 1）有力论证了二阶统计量与位姿的关联，动机扎实、说服力强。
- **方法设计新颖且自洽**：第一个将 SPD 流形深度学习引入位姿回归的工作；从协方差池化 → BiMap 降维 → Cholesky 解码 → 6D 连续旋转的整个链路在数学上紧密衔接，每个环节都有明确的几何依据。
- **完整的理论性质论证**：明确分析了 Cholesky 解码的**单射性、连续性、可微性**，以及 6D 表示相对四元数/欧拉角的优势，理论严谨。
- **工程细节到位**：
  - 混合几何优化器的设计尊重了不同参数空间的几何结构；
  - 对角线指数化 + det=1 归一化的技巧兼顾正定性与表达能力；
  - 正则化项设计防止了 Gram-Schmidt 过程中的退化。
- **消融实验具有判别力**：特别是欧氏 MLP 头的巨大性能下降（31.0%），强有力地证明了流形感知设计不可替代。
- **结果在当前端到端方法中达到最优**，且与 PnP 方法（尤其是 LM 上）的精度差距已基本消除。

## 8. 不足与局限

- **与顶级 PnP 方法仍有差距**：在 YCB-V 上，与 VAPO（84.9%）等间接方法相比仍落后约 15 个百分点（ADD(-S)），表明在复杂场景下直接回归的精度上限仍受限于特征提取能力。
- **未显式处理物体对称性**：作者在结论中坦承 Cov2Pose 不处理对称物体（如 LM 中的 Eggbox、Glue 等），尽管这些物体的 ADD-S 指标显示结果良好，但对称性导致的位姿歧义可能使训练信号不稳定，文中仅将对称性分析置于补充材料。
- **骨干网络分辨率限制**：EfficientNet-B6 输出 17×17 特征图，协方差矩阵仅为 289×289，对高分辨率细粒度纹理信息的捕捉可能受限。
- **可扩展性问题未充分讨论**：当物体类别数增加或多物体场景出现时，当前架构需要逐物体训练（per-object），缺乏多实例/多类别的扩展验证。
- **对遮挡的处理机制不够明确**：虽然 LM-O 结果良好，但方法本身没有显式的遮挡感知模块，鲁棒性的来源更多依赖协方差的整体统计特性，缺乏对不同程度遮挡的系统性分析。
- **评估偏差风险**：未报告多次重复实验的方差，在训练-验证划分和 checkpoint 选择上可能存在一定偏差；与间接方法的对比在部分数据集上缺少逐类别数据（"—"项），且未与其他方法共享相同的训练数据量（部分方法使用不同的训练集协议）。
- **新增的超参数**（ReEig 的 ε、正则化系数 λ、BiMap 层数等）对结果的影响缺乏敏感性分析。
- **实际应用广度有限**：该方法为物体级位姿估计设计，是否可迁移至航天器位姿估计等场景需要进一步验证——这关系到本文在航天应用背景中的直接可迁移性。

（完）
