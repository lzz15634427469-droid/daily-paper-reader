---
title: "ConceptPose: Training-Free Zero-Shot Object Pose Estimation using Concept Vectors"
title_zh: ConceptPose：使用概念向量的免训练零样本目标位姿估计
authors: "Kuang, Liming, Velikova, Yordanka, Saleh, Mahdi, Zaech, Jan-Nico, Paudel, Danda Pani, Busam, Benjamin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Kuang_ConceptPose_Training-Free_Zero-Shot_Object_Pose_Estimation_using_Concept_Vectors_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 7.0
evidence: 免训练零样本6DoF目标位姿估计，能处理未知目标，对非合作航天器尤其适用
tldr: 大多数目标位姿估计方法需要数据集专属训练，面对非合作航天器等未知目标时适应性差。ConceptPose利用大型视觉语言模型生成开放性词汇的3D概念图，每个三维点由显著图导出的概念向量标注；通过跨概念图的鲁棒3D-3D对应，可直接估计6DoF相对位姿，全流程无需训练和目标专属模型。实验证明其零样本条件下也能准确估计6DoF位姿，为未知空间目标的即时位姿感知提供了新范式。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 402, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1802, \"height\": 1130, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 660, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1815, \"height\": 433, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1813, \"height\": 422, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1813, \"height\": 424, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-kuang-conceptpose-training-free-zero-shot-object-pose-estimation-using-concept-vectors-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 876, \"height\": 250, \"label\": \"Table\"}]"
motivation: 现有目标位姿估计需数据集专属训练，无法处理训练中未见过的新目标。
method: 以视觉语言模型构建开放词汇3D概念图，用概念向量建立3D-3D匹配，进而恢复6DoF相对位姿。
result: 无需任何对象或数据集专属训练即实现精确的6DoF相对位姿估计，验证零样本能力。
conclusion: 概念向量结合3D概念图为训练无关的通用物体位姿估计提供了有效解决途径，可用于非合作目标。
---

## Abstract
Object pose estimation is a fundamental task in computer vision and robotics, yet most methods require extensive, dataset-specific training. Concurrently, large-scale vision language models show remarkable zero-shot capabilities. In this work, we bridge these two worlds by introducing ConceptPose, a framework for object pose estimation that is both training-free and model-free. ConceptPose leverages a vision-language-model (VLM) to create open-vocabulary 3D concept maps, where each point is tagged with a concept vector derived from saliency maps. By establishing robust 3D-3D correspondences across concept maps, our approach allows precise estimation of 6DoF relative pose. Without any object or dataset-specific training, our approach achieves state-of-the-art results on common zero shot relative pose estimation benchmarks, outperforming the strongest baseline by a relative 62% in average ADD(-S) score, including methods that utilize extensive dataset-specific training.

---

## 论文详细总结（自动生成）

# ConceptPose：使用概念向量的免训练零样本目标位姿估计（CVPR 2026）论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心痛点**：主流 6DoF 目标位姿估计方法高度依赖数据集专属训练和精确的 3D CAD 模型。这种范式在真实场景中面临严重瓶颈——面对新类别、未见过的物体或动态环境时，无法快速适应。
- **研究背景**：大型视觉语言模型（VLM）展示出前所未有的零样本语义理解能力；同时位姿估计领域的近期工作（如 Oryon、Horyon）虽引入了基础模型（如 DINO），但仍需在冻结特征之上训练额外的 Correspondence 网络头，本质上仍未摆脱训练依赖。
- **关键洞察**：作者类比人类认知机制——人类判断未见物体的位姿时会先感知物体特性（如“刃口”“指环”“金属”），再从新视角中寻找这些被语言表达的特征并建立跨视角对应。因此，若能用语言（概念）驱动视觉模型完成空间推理，即可实现真正与训练无关、与物体无关的通用位姿估计。
- **论文定位**：首次提出**完全训练无关（training-free）** 且**模型无关（model-free，即不需要 CAD 模型）**的零样本相对位姿估计管线，不需任何数据集训练、不需 CAD、不需微调。

## 2. 论文提出的方法论

### 学习思想：从语言概念到 6D 位姿

ConceptPose 通过将**语言驱动的开放词汇概念**与**VLM 可解释性（saliency map）** 结合，构建携带语义信息的 3D 概念点云，并通过跨视图的概念向量匹配求取相对位姿，整体流程包含四个环节：

### 流程与关键技术

- **① 类别级概念提取（LLM 生成概念标签）**
  - 输入类别名称（如 “cup”），调用通用大语言模型（Gemini 2.5 Pro）生成 L 个概念标签集合 L = {l₁, ..., l_L}。
  - 概念不限于语义部件，还可涵盖：几何属性（“curved surface”）、功能可供性（“graspable region”）、外观属性（“metal”）等。
  - 通过**结构化 Prompt** 约束概念须满足：跨实例可泛化、至少从一个视点外部可见、语义正交以减少冗余。
- **② Saliency Map 提取（VLM 定位概念）**
  - 对每个概念标签使用 **GradCAM** 在 Vision Transformer（SigLIP2-giant）上对文本 prompt 求梯度，合成该概念对应的空间显著性热图。
  - 将 RGB 裁剪到物体 bbox、resize 到 VLM 输入尺寸；saliency map 最终 resize 回原图尺寸并填充，得到 (L, H, W) 的 saliency 张量。
- **③ 3D 概念向量与对应关系构建**
  - 将 saliency maps 与深度图结合，反投影为稠密 3D 点云 P_a、P_q，每个点 p 关联一条 L 维概念向量。
  - 概念向量经**带温度 τ 的 Softmax** 归一化为概率分布：

    $$c(p) = \mathrm{softmax}(s(p)/\tau)$$
  - 使用**前向 KL 散度**构建查询—锚点相似度矩阵，取最小 KL 散度作为匹配点：

    $$S_{ij} = -D_{KL}\big(c(p_i^q)\,\|\,c(p_j^a)\big)$$
- **④ 位姿估计**
  - 使用 **RANSAC** 鲁棒估计：迭代采样最小点集，用 Umeyama 闭合解求相似变换，统计内点数并选最优变换。
  - 最后施加 **ICP refinement**（几何近邻匹配）做局部优化，获得最终相对变换 T_rel = (R_rel, t_rel)。
  - 使用 Ground Truth anchor 位姿合成绝对位姿用于评测。

### 其他细节

- 两阶段统计滤波：先基于 KNN 局部去外点，再基于到质心距离的全局去外点（μ±2.5σ）。
- 可选**体素化**模块：将点云归一化到单位立方体，64³ 体素网格内做 mean pooling 聚合概念向量成稀疏表示，加速推理。
- 文本 embeddings 跨帧缓存以加速。

## 3. 实验设计

### 评测数据集（4 个真实世界 RGB-D 基准）

- **NOCS REAL275**：室内桌面场景，18 个实例、6 个类别。
- **Toyota-Light (TYOL)**：21 类日用品，含光照变化、杂乱和遮挡。
- **YCB-Video (YCB-V)**：21 个 YCB 物体，密集杂乱、遮挡严重。
- **LINEMOD (LM)**：15 个经典物体，含对称物体。

### Benchmark 协议

- 采样 **2000 对 anchor-query 图像对/数据集**，沿用 Oryon 的评估协议。REAL275/TYOL 采用 Oryon 公开固定 split（跨场景）；YCB-V 与 LM 使用固定随机种子生成配对。
- 物体 mask 使用 GT 以隔离目标物体（遵循标准的零样本相对位姿评估协议）。

### 对比方法

- 经典方法：SIFT、ObjectMatch。
- 训练式方法：Oryon、Horyon、Any6D、One2Any。
- 指标：ADD(-S) recall、BOP AR（含 VSD/MSSD/MSPD），另有 ADD-AUC、ADD-S-AUC 等。

### 主要结果

- **ADD(-S)**：全部四个数据集取得 SOTA——REAL275 71.5（超越 Any6D 53.5）、TYOL 55.0（超越 One2Any 34.6）、YCB-V 41.2（超越 Horyon 22.6）、LM 38.6（超越 Horyon 27.6），平均超越最强基线 **62.8%**。
- **BOP AR**：REAL275/TYOL/YCB-V 均超越所有基线，平均提升 14.3%；仅 LM 略低于 Horyon（31.0 vs 34.4），作者归因于该数据集遮挡严重。

### 额外实验

- **Few-shot 位姿跟踪**（YCB-Video 测试集，4068 对）：以 2 个静态参考帧构建实例级概念模型。ADD-AUC 90.1%、ADD-S-AUC 95.4%，超越 FoundationPose（87.4%/94.3%），仅次于在线 shape completion 的 UA-Pose。

## 4. 资源与算力

- 论文中未提供大规模训练算力信息——因为该方法**不需要训练阶段**。
- 推理硬件明确为消费级配置：AMD Ryzen 7 5800X（8 核 CPU）+ NVIDIA GeForce RTX 4060 Ti 16GB + 48GB RAM；所有操作以 FP16 精度运行。
- 推理时长：每张图像对约 **7.27~8.82 秒**（不含体素化），体素化后降至约 **6.75~6.87 秒**（平均约 11% 加速）。
- 作者指出推理时延主要源于 VLM/GradCAM 的推理开销，并预测随 VLM 架构进步会成比例改善。

## 5. 实验数量与充分性评估

### 实验覆盖

- 主实验覆盖 4 个不同难度的权威基准，对比方法类型较全（经典、训练式零样本、多视角等）。
- 消融实验数量有限但定位关键：
  - **Prompt 类型消融**（REAL275）：比较 default、geometric、affordance、adjective 四种概念生成策略，以及是否对 LLM 提供渲染图。
  - **概念数量消融**（TYOL 上进行贪心前向选择）：发现 L=4~6 时性能即趋于饱和。
  - **体素化消融**：全部四个数据集，报告性能损失约 0.3~1.8 pp，时间缩短约 11%。
- 另有 Few-shot 跟踪任务作为泛化性延伸验证。

### 充分性与公平性评估

- **优点**：评估协议与 Oryon 保持一致（固定 splits），结果具有可比性；RANSAC 固定随机种子、确定性设置保证可复现。
- **不足/偏差风险**：
  - Any6D 与 One2Any 未在 YCB-V 和 LM 上评测，比较不完整。
  - YCB-V/LM 配对由作者生成而非固定公共 split，与基线比较存在**抽样方差风险**，但性能差距较大（如 YCB-V 上 41.2 vs 22.6）使结论较可信。
  - 消融评估仅集中在 REAL275/TYOL，未覆盖全部数据集。
  - GPT/LLM 概念生成具非确定性，实验虽有固定 seed 但概念生成环节仍可能存在潜在波动（作者以 L=15 做“保障覆盖”的折中）。
  - 概念数量选取更多为了规避 VRAM 约束而非严格最优（贪心分析建议 L≈4~6 即饱和，但实际用 15），可能造成计算冗余。

## 6. 论文的主要结论与发现

- **概念向量可传递语义对应**：概念向量驱动的 3D-3D 匹配能够在不训练、无 CAD 条件下获得精确的 6DoF 相对位姿。
- **语义推理可超越学习式几何特征**：在同一基准上，ConceptPose 以远超第二名的差距（平均 +62.8% ADD(-S)）超过了所有需训练的基线，实证了“语言驱动的语义推理在姿态任务上可以优于学习式几何特征”。
- **训练瓶颈可以被消除**：概念生成（LLM）与空间定位（VLM）均由预训练通用模型完成，下游无需任何梯度更新——这使位姿估计真正成为“零训练成本”的任务。
- **跨任务泛化性好**：除零样本相对位姿外，方法在 Few-shot 跟踪场景也达到 SOTA 水平（超越 FoundationPose 2.7 pp ADD-AUC）。

## 7. 优点

- **训练/模型双重免费**：无需数据集训练、无需 CAD、无需任何微调，直接使用开箱即用的通用 LLM+VLM 完成位姿推理。
- **概念定义高度灵活**：概念不止语义部件，可涵盖几何、材质、可供性等抽象描述，对不同种类物体自适应能力强（对无纹理对称物体也能有效）。
- **出色的实验战绩**：在 4 个公开基准上全面超越需训练的强基线，结果显著（最高涨幅 82.3%），在 YCB-V（高度遮挡）上依旧有 41.2% ADD(-S)。
- **可扩展性与模块化**：核心模块（LLM/VLM）可无痛替换为更强的新模型，适配新架构成本低，不需重训 pose head。
- **硬件门槛低**：消费级单 GPU（RTX 4060 Ti 16G）即可运行，使用 FP16 消减内存开销。
- **体素化策略巧妙**：加速的同时通过 mean pooling 抑制噪声，几乎不损精度（部分指标甚至提升）。

## 8. 不足与局限

- **推理延迟偏高**：每对图像 6.8~8.8 秒，实时性不足以支撑在线/动态应用，仍受 VLM 前向开销制约。
- **遮挡与视角大跨度仍是瓶颈**：在 LINEMOD（重遮挡）BOP AR 上不及 Horyon（31.0 vs 34.4）；极端视角变化下高度不对称物体表现会退化。
- **依赖额外 sensor 与 mask**：需要 RGB-D 深度图以及测试时的 GT 物体 mask（虽为通用零样本评估惯例），其“可用性”在实际开放场景中仍有限。
- **超参较多**：概念数量、softmax 温度 τ、RANSAC 迭代次数阈值/t、滤波阈值等需人工设定，部分超参选择受硬显存限制影响而非完全最优。
- **LLM 生成概念的非确定性**：虽对 prompt 稳健，但仍有随机性，且不同实例类别间可能覆盖不均。
- **评测仍以相对位姿为主**：论文主要评估 anchor→query 的相对变换后再合并 GT anchor pose，真实“端到端”开放物体的绝对姿态评估未完全覆盖；few-shot 实验也仅有一个数据集。
- **缺少对“概念质量”的量化分析**：saliency map 正确性缺乏独立评估，概念失败模式（如无法定位）未被显式分析和处理。

---

（完）
