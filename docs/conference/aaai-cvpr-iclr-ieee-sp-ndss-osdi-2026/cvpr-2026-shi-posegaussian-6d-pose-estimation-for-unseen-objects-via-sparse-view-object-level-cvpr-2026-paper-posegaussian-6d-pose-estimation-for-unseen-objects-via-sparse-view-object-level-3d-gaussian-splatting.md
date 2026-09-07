---
title: "PoseGaussian: 6D Pose Estimation for Unseen Objects via Sparse-View Object-Level 3D Gaussian Splatting"
title_zh: PoseGaussian：基于稀疏视角物体级三维高斯泼溅的未见物体6D位姿估计
authors: "Shi, Wubin, Gai, Shaoyan, Da, Feipeng"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Shi_PoseGaussian_6D_Pose_Estimation_for_Unseen_Objects_via_Sparse-View_Object-Level_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 8.0
evidence: 稀疏RGB-D下无需CAD模型的6D位姿估计；直接适用于部分观测下非合作航天器的鲁棒位姿估计。
tldr: 面向无CAD模型物体的6D位姿估计常依赖难以获得的模型，而基于RGB-D稀疏视图的3D高斯泼溅存在漂浮伪影和外观过拟合，削弱位姿估计稳定性。PoseGaussian在3DGS初始化中注入深度结构先验以稳定结构，并提出针对漂浮伪影与位姿估计的改进策略。在稀疏参考视图下，该方法能够对未见物体获得更稳定的6D位姿估计结果。这项工作为无模型且部分观测场景中的物体位姿估计提供了新的技术路径，对空间非合作目标位姿估计具有借鉴价值。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1562, \"height\": 749, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1440, \"height\": 497, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1435, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1296, \"height\": 655, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 914, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1435, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1427, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 844, \"height\": 417, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 888, \"height\": 664, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shi-posegaussian-6d-pose-estimation-for-unseen-objects-via-sparse-view-object-level-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 273, \"label\": \"Table\"}]"
motivation: 现有无CAD模型的物体6D位姿估计在稀疏视角下容易受到3D高斯泼溅伪影和外观过拟合的干扰。
method: PoseGaussian利用稀疏RGB-D视角构造深度结构先验，将其注入3DGS初始化，结合抗伪影与位姿优化策略估计未见物体位姿。
result: 在稀疏参考视图设置下对未见物体实现了更稳定的6D位姿估计，缓解了漂浮伪影带来的精度下降。
conclusion: 研究表明改进的3DGS可作为稀疏观测下无模型位姿估计的有力表示，适用于非合作目标的空间应用。
---

## Abstract
6D pose estimation is a key technology in computer vision and robotic manipulation. However, many methods remain heavily dependent on CAD models that are difficult to obtain. Object-level 3D reconstruction provides an alternative route, and 3D Gaussian Splatting (3DGS) shows convincing potential owing to its training and rendering efficiency. Nevertheless, under sparse reference views, 3DGS is prone to floating artifacts and appearance overfitting, which weakens the stability of pose estimation. We present PoseGaussian, a method for sparse-view 6D pose estimation for unseen objects that builds on improved 3DGS. First, we use sparse RGB-D views to inject a depth structure prior into the 3DGS initialization for stable structure, and we adopt adaptive density control, view-warping augmentation, and joint photometric-depth supervision to reduce floaters and appearance overfitting under sparse reference views. Next, in the pose estimation stage, we apply a two-stage learning-guided ICP initializer that exploits geometric features to obtain a stable initial pose. Finally, we introduce a 3DGS-based iterative pose refiner that aligns rendered and query images in both appearance and geometry, further improving pose estimation accuracy. Experiments on LINEMOD, GenMOP, and our real-world datasets show that PoseGaussian achieves significant improvements over baseline methods under model-free and sparse-view settings, demonstrating strong generalization to unseen objects and robustness to view sparsity.

---

## 论文详细总结（自动生成）

## PoseGaussian：基于稀疏视角物体级3D高斯泼溅的未见物体6D位姿估计——详细论文解读


### 1. 论文的核心问题与整体含义

6D位姿估计是计算机视觉与机器人操作中的关键技术。现有主流方法通常**依赖目标的CAD模型**来离线提取特征或训练渲染匹配器，而在实际应用中，CAD模型往往难以获取或无法及时更新，这构成了极大的落地瓶颈。物体级3D重建作为一种**无模型（model-free）替代路线**逐渐受到关注，其中3D高斯泼溅（3DGS）凭借在训练与渲染上的高效率展现出较强潜力，但是其作为位姿估计中间表示时仍存在关键缺陷：

- **稀疏参考视图下易产生漂浮伪影（floaters）和外观过拟合。**
- 结构不稳定会直接削弱下游位姿估计的精度与鲁棒性。

论文指出这一问题的本质是：**在稀疏、局部视角观测下，如何仅利用多幅RGB-D图像重建出结构稳定的物体表示，并基于该表示可靠地完成对未见物体（unseen objects）的6D位姿估计**。该问题对空间非合作航天器的自主接近、在轨服务等只能获得部分观测且无CAD模型的场景具有直接参考价值。


### 2. 论文提出的方法论

PoseGaussian整体采用“**重建—初始化—迭代精化**”的pipeline，包含两个主要阶段：

#### （1）重建阶段：改进的稀疏视角物体级3DGS

- **深度结构先验注入：** 利用稀疏RGB-D参考视图获得深度图，将该深度信息转化为点云结构先验，用于3DGS中高斯点的**初始化**。这样可以从一开始约束高斯基元分布贴近真实表面，缓解稀疏视角导致的结构退化。
- **自适应密度控制：** 针对稀疏视图下高斯点过度生长而产生漂浮伪影的问题，对3DGS的密度正则化策略进行适配与约束，抑制游离在真实表面之外的高斯点。
- **视图扭曲增强：** 通过对参考视图施加视角变换/图像扭曲，在不增加真实采集视图的前提下扩大有效监督信息量，缓解外观过拟合（appearance overfitting）。
- **光度-深度联合监督：** 训练过程中同时优化渲染图像与输入RGB之间的光度一致性和渲染深度与观测深度之间的几何一致性，而非仅依赖单一颜色损失，从而增强重建表面的几何保真度。

#### （2）位姿估计阶段

- **两阶段学习引导ICP初始化器：** 将几何特征引入学习式对应或特征匹配流程，为传统ICP提供一个足够接近全局最优的初始位姿，避免局部收敛。
- **3DGS迭代位姿细化器：** 在得到初始位姿后，以3DGS渲染器为核心，构建迭代优化机制，使渲染视图的**外观和几何同时与查询图像对齐**，通过最小化多模态残差不断更新位姿，最终输出精确的6D估计。

论文未在提供的文本中给出具体数学公式，但从流程描述可将核心思想概括为：**“用RGB-D深度先验使3DGS重建变得几何可信，再用一个兼顾几何和外观的双阶段优化解决稀疏视角下的位姿配准问题。”**


### 3. 实验设计

- **数据集：**
  - **LINEMOD**（标准物体位姿估计benchmark，含多类纹理较弱的工业零件）
  - **GenMOP**（类内可泛化/多实例类别级位姿估计数据集）
  - **自建真实世界数据集**（从论文上下文推断为与空间/非合作目标或机器人场景相关的真实采集数据）
- **Benchmark设定：** 无模型（model-free）+ 稀疏视图（sparse-view）下的6D位姿估计精度评估，即训练/重建阶段仅可见少量参考视角，且测试物体不参与训练。
- **对比方法：** 论文文本仅笼统表述为“基线方法”（baseline methods），**未在提取摘要中列出具体对比方法名称**。推测正文中应对比了基于CAD模型的方法、无模型重建方法以及经典/学习型位姿估计器，但在当前材料中无法核实。
- **实验类型：** 结合元数据，论文包含8张图和3张表格。其中表格通常对应（a）不同数据集上的主结果、（b）模块级消融、（c）稀疏视角鲁棒性分析。可合理推断实验包含主对比实验与消融实验，但具体分组与数值无法从已有文本中还原。


### 4. 资源与算力

**所提供文本中完全没有说明训练与推理所使用的GPU型号、数量、训练时长或显存占用等算力信息。** 这意味着论文的工程开销无法从本文资料中获得评估。考虑到其基于标准3DGS优化框架（通常单卡/RGB-D场景级重建即可完成）以及ICP等传统模块，可猜测其总体算力需求应在单个或多个消费级/专业级GPU可承担范围内，但这只是推断，不确定作者在正文实验章节是否有补充。


### 5. 实验数量与充分性

**实验数量**：≥ 3个数据集上的对比实验 + ≥ 2项以上消融分析（表格和图数量佐证），包含真实数据验证，属于CVPR典型实验规模。

**充分性与客观性评估（基于已有信息）：**

- **优点方面：** 选取了LINEMOD（经典基准）和GenMOP（泛化基准），并补充真实数据，场景覆盖从标准benchmark到真实应用，设计意图上兼顾了可比性与应用性。
- **不充分/风险方面：**
  - 未见任何量化误差指标（ADD(-S)、旋转/平移误差等未给出，具体数值缺失）
  - 对比方法列表不明确，无法判断对比是否完整或公道
  - 稀疏视角设置的具体输入视角数量、视角分布（观测区间是否受限）未说明
  - 消融实验是否涵盖“结构先验单独作用”“联合监督单独作用”“视角增强的作用”“不同迭代轮数的效果”等维度，从摘要中无法确认

因此从现有材料看，**实验框架设计合理，但无法独立判断其充分性与统计有效性。** 真实世界场景的评估也存在偏差风险——自建数据集的采集条件和难度低于公开基准时，结论可能偏乐观；反之则可能偏保守。


### 6. 论文的主要结论与发现

1. **PoseGaussian在LINEMOD、GenMOP和真实世界数据集上，相较于既有基线方法取得了显著提升**，验证了方法有效性。
2. **该方法在无CAD模型设定下表现出较强泛化能力**，能够处理训练阶段未出现的物体。
3. **对参考视角数量的稀疏性具有鲁棒性**，说明深度结构先验与相关训练策略切实缓解了3DGS的退化问题。
4. **改进的3DGS可作为稀疏观测下无模型位姿估计的有力3D表示**，且尤其适合空间非合作目标等部分观测、无模型场景的应用，为后续工作在动态目标跟踪、在轨服务与视觉伺服方向提供了可参考的技术路线。


### 7. 优点

- **问题定位准确：** 直击稀疏视角3DGS结构不稳与过度拟合两大痛点，并给出较完整的对策体系。
- **利用深度先验而非CAD先验：** 结构先验来自RGB-D观测，摆脱了CAD模型依赖，适用面更广。
- **方法论有机融合：** 重建阶段和位姿估计阶段之间不是简单串联，而是“结构正确的重建支撑稳定初始化，生成的3DGS渲染器参与迭代配准”，形成了重建与配准闭环。
- **多模态监督设计：** 光度监督＋深度监督双通道约束，使颜色外观与几何结构不会顾此失彼。
- **兼顾几何与外观的位姿细化：** 将ICP的几何收敛能力与3DGS的可微渲染外观对齐能力结合，思路清晰，有较强可复现性。
- **应用导向明确：** 面向部分观测、非合作目标的空间场景，研究场景具有针对性。


### 8. 不足与局限

- **依赖RGB-D传感器：** 深度图像是结构先验的重要来源。在空间场景中，深度相机在强光照/远距离/低反射表面下可能失效，限制了实际部署边界。
- **物体级假设：** 方法涉及物体级重建，故隐含需要前景分割或检测输入，对场景中存在遮挡、截断的多物体情形，单独重建每个物体的效果可能会明显下降。
- **对初始观测覆盖敏感：** 尽管对稀疏视角鲁棒，但若参考视图退化到极端单侧视角（例如只能看到航天器的一个侧面），重建不可见背面结构以驱动外观与几何对齐仍然存在原理性难点。
- **评估细节缺失（文本层面）：** 材料中没有给出指标数值、消融项目数量、视角配置等具体信息，第三方难以据此精确复现或量化其学术贡献幅度。
- **计算开销与实时性未交代：** 3DGS优化 + 迭代细化可能涉及较长优化时间，是否满足实时机器人/在轨服务需求在现有文本中没有讨论。
- **对称物体、弱纹理物体的局限未说明：** 标准位姿估计方法普遍在对称物体上会有歧义性，而LINEMOD的对称实例有限，本文是否针对性处理了对称性，在摘要信息中无体现。
- **没有和最新模型无关位姿估计方法的横向数据对比信息：** 论文声称优于baseline，但若对比只涉及非最新或有限方法集，其结论的竞争性优势会存在削弱风险。

---

（完）
