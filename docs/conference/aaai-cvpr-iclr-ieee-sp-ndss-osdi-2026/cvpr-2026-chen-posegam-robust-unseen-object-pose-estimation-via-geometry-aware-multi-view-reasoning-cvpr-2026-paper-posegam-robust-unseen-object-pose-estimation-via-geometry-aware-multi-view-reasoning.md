---
title: "PoseGAM: Robust Unseen Object Pose Estimation via Geometry-Aware Multi-View Reasoning"
title_zh: PoseGAM：通过几何感知多视图推理实现鲁棒的未见物体姿态估计
authors: "Chen, Jianqi, Zhang, Biao, Tang, Xiangjun, Wonka, Peter"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Chen_PoseGAM_Robust_Unseen_Object_Pose_Estimation_via_Geometry-Aware_Multi-View_Reasoning_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 7.0
evidence: 面向未见物体的鲁棒6D位姿估计，几何感知多视图推理，适用于基于模板图像的非合作航天器位姿估计
tldr: 对未见过的物体进行6自由度位姿估计仍困难，已有方法常需显式建立查询图与目标模型或模板图之间的特征对应。PoseGAM基于多视图基础模型直接回归姿态，并通过显式点几何与几何表征网络特征两种机制融入物体几何约束，避免显式匹配。实验表明该方法在未见物体上具有更强的鲁棒性。该框架有助于不依赖精细外观先验的非合作航天器位姿估计。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1800, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1809, \"height\": 920, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1803, \"height\": 820, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1449, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 883, \"height\": 271, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 885, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 886, \"height\": 233, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-chen-posegam-robust-unseen-object-pose-estimation-via-geometry-aware-multi-view-reasoning-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 877, \"height\": 217, \"label\": \"Table\"}]"
motivation: 未见物体的6D位姿估计仍需显式特征对应，易受外观与遮挡影响，难以适应非合作目标。
method: 提出PoseGAM，结合多视图基础模型、显式点云几何和几何表征特征，直接从查询图与模板图预测位姿。
result: 在未见物体基准上取得了比显式匹配方法更鲁棒和准确的位姿估计效果。
conclusion: 验证了几何感知多视图推理可显著提升模型无关物体的位姿估计泛化能力。
---

## Abstract
6D object pose estimation, which predicts the transformation of an object relative to the camera, remains challenging for unseen objects. Existing approaches typically rely on explicitly constructing feature correspondences between the query image and either the object model or template images. In this work, we propose PoseGAM, a geometry-aware multi-view framework that directly predicts object pose from a query image and multiple template images, eliminating the need for explicit matching. Built upon recent multi-view-based foundation model architectures, the method integrates object geometry information through two complementary mechanisms: explicit point-based geometry and learned features from geometry representation networks. In addition, we construct a large-scale synthetic dataset containing more than 190k objects under diverse environmental conditions to enhance robustness and generalization. Extensive evaluations across multiple benchmarks demonstrate our state-of-the-art performance, yielding an average AR improvement of 5.1% over prior methods and achieving up to 17.6% gains on individual datasets, indicating strong generalization to unseen objects.

---

## 论文详细总结（自动生成）

### 一、论文的核心问题与整体含义

- **研究背景**：6D物体姿态估计旨在预测物体相对于相机坐标系的旋转与平移变换，是机器人操作、增强现实、自动驾驶等领域的基础性问题。
- **核心问题**：对于**未见过的物体（unseen objects）**，即训练阶段从未出现过的物体类别或实例，现有的姿态估计方法仍然面临巨大挑战。传统方法通常依赖在查询图像与物体三维模型或模板图像之间**显式构建特征对应关系**，这一过程极易受到外观变化、纹理缺失、遮挡以及环境光照差异的干扰，鲁棒性不足。
- **研究动机**：作者提出，是否可以直接从查询图像与多张模板图像中回归物体姿态，而**绕过显式的特征匹配步骤**，从而从根本上增强对未见物体的泛化能力。该思路对无法预先获得精细外观模型或三维 CAD 模型的**非合作目标**（例如在轨服务中的非合作航天器）姿态估计尤其具有潜在价值。
- **整体意义**：PoseGAM 探索了一条不同于传统对应关系匹配范式的技术路径，证明了基于多视图几何感知推理的方法能够在不显式匹配特征的情况下，取得优于显式匹配方法的姿态估计精度与鲁棒性。

---

### 二、论文提出的方法论

#### 1. 核心思想

- 将未见物体的姿态估计问题建模为：给定一张查询图像和若干张已知姿态的模板图像，直接**回归查询图像中物体的 6D 姿态**，省略查询图与模板图之间的显式特征对应建立过程。
- 方法建立在**多视图基础模型架构**之上，利用大规模预训练获得的多视图几何与外观先验能力，实现对与训练类别不同的新物体的姿态推理。

#### 2. 两类几何信息融合机制

PoseGAM 通过两种互补的途径将物体几何信息注入网络：

- **显式点级几何（Explicit point-based geometry）**：引入点云或稀疏三维点等显式几何表示，使网络能直接感知物体的三维结构与空间关系。
- **几何表征网络的隐式特征（Learned features from geometry representation networks）**：利用几何表征网络编码物体形状，并将其学到的特征与多视图图像特征进行融合，弥补纯图像特征对三维结构表达能力不足的问题。

两种机制形成互补：显式几何提供了确定性的三维空间约束，隐式几何特征则提供了可学习的形状语义抽象，两者共同帮助网络在物体外观未知的情况下聚焦于结构信息。

#### 3. 框架流程（文字描述）

1. 输入：查询图像 + 一组模板图像（模板含已知标注的位姿）。
2. 多视图特征提取：由多视图基础模型分别提取查询图与各模板图的图像特征。
3. 几何编码：利用显式点几何分支与几何表征网络分支分别提取物体几何描述。
4. 跨视图推理与融合：在 Transformer 式架构中进行跨图像、跨几何信息的交互推理，隐式学习查询图与模板图之间的相对位姿关系。
5. 姿态回归：直接输出查询物体的 6D 姿态（旋转矩阵 R 与平移向量 t）。

---

### 三、实验设计

#### 1. 训练数据集

- 作者构建了一个**大规模合成数据集**，包含**超过 19 万个物体**，覆盖多样的环境条件（如不同光照、背景、相机视角等），用于增强模型的鲁棒性和泛化能力。

#### 2. Benchmark与评估场景

- 论文在**多个公开基准数据集**上进行了广泛评估（具体数据集名称未在摘要中出现，需结合正文确认，涉及多种未见物体测试协议）。
- 评估任务涵盖：
  - 查询图像与模板图像间的姿态回归精度；
  - 对训练中未见过物体的零样本泛化能力；
  - 不同环境干扰条件下（光照、遮挡等）的鲁棒性。

#### 3. 对比方法

- 与近期主流的**未见物体姿态估计方法**进行了比较，特别是与依赖**显式特征匹配**的基线方法进行了对比，包括基于物体模型匹配和基于模板图像匹配的类别代表方法。
- 评估指标方面使用了姿态估计中常用的 **AR（Average Recall）** 指标。

---

### 四、资源与算力

- 论文原文（摘要与给定元数据）**未明确说明**具体使用的 GPU 型号、GPU 数量、训练总时长或计算资源规模。
- 构建 19 万以上物体的合成数据集本身对渲染和存储有一定资源需求，但原摘要未提供相关硬件配置信息。
- **需在正文或附录中进一步确认**训练所用算力细节。

---

### 五、实验数量与充分性

#### 1. 实验规模

- 根据表格元数据，论文包含至少 **5 张结果表格** 与 **4 张图表**，结合“多基准评测”的描述，可推断实验工作量较大。
- 主要实验类型可能包括：
  - 多个数据集上的**主实验对比**；
  - **与显式匹配方法的对比**（验证核心假设）；
  - 涉及点几何机制与几何表征网络特征的**消融实验**（验证两类几何信息的贡献）；
  - 不同环境条件（光照、遮挡等）下的**鲁棒性分析**。

#### 2. 充分性与客观性分析

- **优点**：多数据集评测和与多种 SOTA 方法对比增强了说服力；大规模合成数据训练有助于评估跨类别泛化。
- **潜在不足**：
  - 若仅依赖合成数据训练，真实场景中的 **sim-to-real 域差**需要额外的实验验证（如真实图像上的测试、实时性分析）；
  - 未见物体的定义与测试协议是否严格（例如类别不可见 vs. 实例不可见）需要正文明确，以避免评估口径引起的偏差；
  - 缺乏关于**失败案例**和姿态歧义场景下的详细分析。
- **总体评价**：实验布局覆盖面较广，方法设计上具备清晰的消融逻辑，但其在真实世界中的泛化能力仍有待进一步验证。

---

### 六、论文的主要结论与发现

- 所提出的 PoseGAM 框架在多个未见物体姿态估计基准上达到了**最先进的性能**。
- 相比此前最先进的方法，在 **AR 指标上平均提升 5.1%**，在个别数据集上的最高提升达到 **17.6%**。
- 实验结果揭示：**显式特征匹配并非未见物体姿态估计的必需环节**，几何感知的多视图推理可以更有效地组织空间信息，对未见物体表现出更强的泛化稳定性。
- 证明显式点几何与隐式几何表征特征具有**互补效应**，二者联合使用可获得最佳效果。
- 验证了大规模、多环境条件的合成数据对于学习鲁棒的几何推理能力具有重要的工程价值。

---

### 七、优点

1. **范式新颖**：跳过显式匹配，将姿态估计统一转化为多视图几何推理问题，为未见物体位姿估计提供了新的解决思路。
2. **几何信息建模充分**：同时引入显式点级几何和隐式特征两种互补机制，较单一模态更加完备，也与“几何感知”的方法名呼应。
3. **数据规模大**：超过 19 万个物体的合成数据集在规模上具有优势，有助于提升模型的泛化能力。
4. **实验结果突出**：平均 5.1%、最高 17.6% 的 AR 提升幅度具有明显的实际意义。
5. **应用前景广阔**：可以拓展到非合作航天器姿态估计等缺乏高质量三维模型的领域，因为这些场景下几何结构和多视图模板通常比纹理外观更容易获得。

---

### 八、不足与局限

1. **真实场景验证有限**：训练数据全部来自合成环境，缺少在真实物理图像上的大量评测细节，实际部署中的 sim-to-real 差距与噪声鲁棒性需进一步验证。
2. **缺乏算力信息**：正文未提供训练硬件与时间等信息，不利于社区评估复现成本和方法的可及性。
3. **对模板质量的依赖**：方法假设模板图像的位姿已知（可能在训练时构建），若模板本身存在噪声或数量不足，对推理效果的影响需进一步分析。
4. **细粒度姿态歧义**：对于高度对称或结构极度相似的物体，仅依赖几何推理是否足以区分姿态歧义，仍需更详细的边界分析。
5. **对称性问题**：未见物体中常见的对称性会导致位姿标注存在多解性，目前摘要中未明确描述如何处理对称对象的监督信号。
6. **运行实时性**：多视图推理和几何编码通常会带来较高的计算开销，摘要未涉及推理速度，限制了其在实时机器人场景中的适用性说明。

---

（完）
