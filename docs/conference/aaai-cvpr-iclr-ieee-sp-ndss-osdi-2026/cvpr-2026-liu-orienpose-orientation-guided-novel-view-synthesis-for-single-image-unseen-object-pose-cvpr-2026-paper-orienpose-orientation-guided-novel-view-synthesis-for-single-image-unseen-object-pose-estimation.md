---
title: "OrienPose: Orientation-Guided Novel View Synthesis for Single-Image Unseen Object Pose Estimation"
title_zh: OrienPose：面向单图未见物体位姿估计的朝向引导新视角合成
authors: "Liu, Yating, Qi, Zhaoshuai, Zou, Yang, Yang, Yongnan, Zhang, Shizhou, Zhang, Yanning"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_OrienPose_Orientation-Guided_Novel_View_Synthesis_for_Single-Image_Unseen_Object_Pose_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 8.0
evidence: 基于方向引导新视角合成的单图未见物体6D位姿估计；直接服务航天器单目位姿估计问题。
tldr: 在无CAD模型条件下从单张图像估计未见物体的3D位姿仍很困难，已有基于新视角合成的方法仅以像素级监督近似视角变换，因起始朝向未定义且缺少几何校验，容易合成结构畸变或模糊的视图。OrienPose提出以朝向信息引导新视角合成，显式加入几何约束来验证预测变换，从而避免几何失真。实验表明，在标准未见物体位姿估计基准上，该方法相比现有单图模板匹配方法取得了更准确的位姿估计。其贡献是为单目物体位姿估计提供了一种带几何监督的可泛化范式，可助力单目空间目标观测。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1709, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1703, \"height\": 757, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 332, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1715, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 745, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 665, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 823, \"height\": 296, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1704, \"height\": 909, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 850, \"height\": 426, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 847, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-orienpose-orientation-guided-novel-view-synthesis-for-single-image-unseen-object-pose-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 825, \"height\": 211, \"label\": \"Table\"}]"
motivation: 单图未见物体位姿估计在新视角模板匹配中缺少明确起始朝向和几何校验，导致生成几何畸变视图。
method: 提出朝向引导的新视角生成，以预测朝向约束目标视图合成并引入几何一致性验证变换合理性。
result: 在单帧未见物体位姿基准上减少了合成畸变并提升了3D位姿精度。
conclusion: 显式朝向与几何约束能提高单目未见物体位姿估计的可靠性，对空间非合作目标的单目观测有参考价值。
---

## Abstract
Estimating the 3D pose of unseen objects from a single image remains a fundamental yet challenging problem in computer vision, especially under a CAD model-free setting.Pioneering attempts address this issue by matching templates generated through Novel View Synthesis (NVS), which essentially aims to learn the geometric transformation from a reference to a target view. While promising, these methods can only approximate this transformation under pixel-level supervision, as the starting orientation remains undefined. In the absence of explicit geometric constraints to verify the correctness of the predicted transformation, existing methods often synthesize novel views with geometry-distorted structures or severely blurred local textures, leading to unreliable template matching and suboptimal pose estimation results. To this end, we propose OrienPose, a novel object pose estimation framework via orientation-aware NVS from a single image. Specifically, we introduce the Orientation-Aware Guidance, which explicitly injects object orientation cues into the reference latent embedding to enhance orientation awareness during viewpoint transformation. We also introduce an orientation consistency loss that supervises viewpoint transformation at the geometric level, establishing sufficient supervision for explicit and geometry-consistent transformation guidance beyond pixel-level similarity. This loss justifies estimating the reference orientation rather than using its ground-truth pose, thereby ensuring the alignment of coordinate domains between the injected and supervised priors. Extensive experiments demonstrate that OrienPose achieves state-of-the-art performance in single-view unseen object pose estimation and impressive robustness to image degradations. Our code is available at https://github.com/pubyLu/OrienPose.

---

## 论文详细总结（自动生成）

## 摘要
该论文提出了一种面向单图未见物体位姿估计的朝向引导新视角合成框架（OrienPose），该框架通过显式引入目标朝向的先验信息来引导新视角合成过程，并引入朝向一致性损失以提供几何层面的监督，从而解决传统新视角合成方法因缺少起始朝向定义与几何校验而导致的几何畸变和纹理模糊问题。实验表明，该方法在未见物体的位姿估计基准上取得了领先的性能，并对图像退化具有较好的鲁棒性。

---

## 1. 论文的核心问题与整体意义

- **研究问题**：在无 CAD 模型条件下，仅从单张参考图像估计未见物体（unseen object）的三维旋转姿态。
- **研究背景**：尽管现有的基于模板匹配的方法使用新视角合成（NVS）来生成模板，但 NVS 本质上是一个病态变换问题——它是学习参考视图到目标视图之间的几何变换，而这一变换缺乏明确的起始朝向（starting orientation）定义。
- **核心瓶颈**：
  - 现有方法仅依赖像素级 L2 损失进行监督，缺少显式几何约束来验证变换的正确性；
  - 因此生成的新视角常出现**几何结构畸变**或**局部纹理模糊**，导致模板匹配不可靠和位姿估计精度次优；
  - 即使已有方法（NOPE）引入旋转信息，仍然忽略了物体内在朝向这一关键几何线索。
- **整体意义**：通过显式引入朝向先验来定义几何变换，使 NVS 从病态问题转化为有明确约束的变换问题，从而提出了一种可泛化的单目未见物体位姿估计范式，对单目空间目标观测等应用具有参考价值。

---

## 2. 方法论述

### 2.1 总体范式

采用与 NOPE 相似的“Generate-and-Compare”范式：从参考图像出发，对一组预设视角进行新视角合成得到模板，再通过模板匹配确定查询图像的姿态。

### 2.2 核心设计 1：Orientation-Aware Guidance（OAG）

- **核心思想**：解决“给定参考图像但没有朝向信息”的问题，在参考图像编码和解码之前显式注入目标朝向信息到参考图的潜在嵌入中，使 NVS 过程具备朝向感知能力。
- **朝向估计模块（OEM）**：以 Orient-Anything 为基础，在训练数据上重训。它输出方位角 α、平面内旋转角 θ和仰角 ω的离散概率分布：
  - α 和 θ：基于冯·米塞斯分布（von Mises distribution）建模；
  - ω：基于高斯分布建模；
  - 这些角度定义在规范坐标系（CCS）中。
- **融合机制**：朝向分布经 MLP 嵌入得到 E_orient，通过交叉注意力机制注入参考图像嵌入 E_ref，得到朝向感知嵌入 E′_ref，再输入变换网络。整个过程在潜在空间中完成，避免纹理畸变和生成伪影。

### 2.3 核心设计 2：Orientation Consistency Loss（OCL）

- **总损失**：L = λ1·L2 + λ2·L_OC（L2 为像素级损失；L_OC 为朝向一致性损失）。
- **L_OC 的构成**：预测和真实朝向分布（通过 OEM 提取）之间在三个角度上的 KL 散度加权和：L_OC = μ1·D_KL(P_α_gt, P_α_ref) + μ2·D_KL(P_θ_gt, P_θ_ref) + μ3·D_KL(P_ω_gt, P_ω_ref)
- **为何不用交叉熵？** 
  - KL 散度对分布学习更优；
  - 使得在 NVS 起始处注入朝向（Oref + ΔR = Osyn）与末尾朝向监督形成几何一致的完整学习闭环；
  - 因为只用分布的相对差异，这种方法保证了参考朝向的估计值与监督所用坐标系（OEM 的规范坐标系）的一致性。
- **为什么不用朝向估计器直接做位姿？** 
  - 朝向估计器产生的是规范坐标系下的朝向分布，不能直接转化为以物体规范坐标系为准的绝对位姿；
  - 故更适合做 NVS 指导的中间表达。

### 2.4 推理阶段的两步流程

- **模板生成**：将参考图输入 NVS 网络，以二十面体二次细分采样生成 N = 342 个视角，并转换成相对参考图的视角变换 ΔRk，生成 N 个目标视图模板。
- **模板匹配**：构建“朝向感知相似度”度量 S_OA，结合特征的 L2 距离和朝向分布的 KL 散度：S_OA^k = −||E_tmp^k − E_qry||² − D_KL(O_qry ‖ O_tmp^k)
  - 选择 S_OA 最高的模板，其对应的视角变换即为最终的相对位姿估计值。

---

## 3. 实验设计

### 3.1 数据集与评估设置

- **训练集**：ShapeNet 渲染图像，与 NOPE 相同；
- **测试集 1**：ShapeNet 中 10 个未见类别（bottle、clock、bus、mug、washer、pistol、guitar、train、dishwasher、skateboard）；
- **测试集 2**：真实数据集 NAVI 中 5 个实例（bull、bunny、sink、shark、schoolBus）；
- **测试集划分规则**：85% 参考图与查询图的方位角差 ≤45°，15% 超出此范围；
- **评估指标**：
  - ACC 30（姿态误差在 30° 以内占比，越高越好）
  - Median pose error（中位位姿误差，越低越好）

### 3.2 对比方法

| 类别 | 方法 |
|---|---|
| G&C（生成-比较） | NOPE |
| 回归法 | PIZZA |
| 关键点法 | MicKey |
| 概率法 | RelPose、RelPose++ |
| 扩散式 NVS 基线 | Free3D（替换 NOPE 的 NVS 骨干） |
| 多视角法 | OnePose++（48 视角）、BoxDreamer（5 视角） |
| CAD 模型法（不计排名） | GigaPose |

---

## 4. 资源与算力

- 原论文没有明确说明所使用的 GPU 型号、数量、训练时长、参数量或 FLOPs 等信息。
- 目前仅可确认在 ShapeNet 渲染数据上训练（与 NOPE 同源），无具体算力数据可总结。

---

## 5. 实验数量与充分性

论文的实验整体数量偏少，可概括如下：

| 实验类别 | 内容 | 数量 |
|---|---|---|
| 标准基准（合成数据） | ShapeNet 未见类别的跨类泛化 | 1 组（含 10 个类别） |
| 标准基准（真实数据） | NAVI 模拟到真实的零样本迁移 | 1 组（含 5 个实例） |
| 消融实验 1 | OAG 与 L_OC 的有效性，仅 bus 类别 | 1 组（含 3 个变体） |
| 鲁棒性实验 | bus 类别上的模糊和遮挡各 4 级 | 2 组 |
| 局限性实验 | NAVI 上大视角变化（45°–90°） | 1 组（定性为主） |

- **优点**：消融实验设计能清晰区分各组件贡献（w/o OAG、w/o LOC、w/ OAG & LOC）；鲁棒性实验覆盖了不同退化等级；对比方法较为全面（9 种以上方法）。
- **不足**：
  - 消融和鲁棒性实验只在 bus 单类别上进行，缺乏跨类别的验证；
  - 大视角变化的实验以定性展示为主，缺少定量对比表；
  - 评估中是否有置信度过滤、类别不平衡等偏差控制，仍需进一步说明。

---

## 6. 论文的主要结论与发现

- **核心结论**：OAG 与 L_OC 均能有效提升性能，且二者联合使用时增益最大，证明朝向先验注入和几何层面的监督对 NVS 至关重要。
- **ShapeNet 上的结果**：相比 NOPE，ACC 30 平均提升 +7.3%，Median 误差降低 7.3°（OrienPose 46.6% → 59.6%（ACC 30）；27.7° → 20.4°（Median）），取得了 SOTA。
- **针对旧方法**：NOPE 在几何各向同性物体上容易产生翻转姿态、缺乏细节，而 OrienPose 可保持几何细节一致；
- **对 NAVI 的迁移**：所有方法都存在 sim-to-real 性能下降，但 OrienPose 在 ACC 30 上仍优于其他方法（50.9%），仍显著高于 NOPE（36.8%）。
- **鲁棒性**：
  - 对模糊的鲁棒性较强：40% 强度模糊时 ACC 30 仅下降不到 3%；
  - 重度遮挡下性能下降更为明显，但仍然与 NOPE 的未退化性能相当，彰显了较强的鲁棒性。
- **局限性**：在参考-查询视角差 45°–90° 的大视角变化下仍会出现明显的位姿误差。

---

## 7. 优点

围绕模型设计和实验方法的亮点主要有：

- **问题剖析准确**：明确指出 NVS 的病态性来自“起始朝向未定义”，并以清晰的几何视角对问题进行公式化，具有较好的理论解释力。
- **设计闭环性强**：朝向注入（起始）与朝向一致性监督（结束）共同形成 O_ref + ΔR = O_syn 的闭环，使 NVS 的变换具备了双向几何约束，思路新颖。
- **姿态推理与绝对位姿估计解耦**：朝向估计器只提供规范坐标下的相对一致性分布，不直接预测绝对位姿，可有效规避坐标域不匹配带来的估计偏差，逻辑巧妙。
- **模块可替换性高**：OAG 和 OCL 都是模块化组件，可以嵌入到其他基于 NVS 的 G&C 方法中。
- **实验设置相对严谨**：训练与测试的类别/实例不重叠，能较好体现“未见物体”的泛化性；对比方法数量较多，在 NO CAD 设定下对比基本公平。
- **鲁棒性验证充分**；且给出了可视化失效案例和可视化差异图，有助于直观理解。

---

## 8. 不足与局限

主要不足如下：

- **缺少算力信息**：没有 GPU 型号、数量、训练时长、推理耗时等关键工程信息，难以客观评估实际成本和部署可行性。
- **消融实验覆盖不足**：消融实验只在 bus 一个类别上进行，无法判断 OAG 和 OCL 的增益是否在所有类别上都稳定存在。
- **单目场景的**三维旋转 vs. 6D 位姿的定位缺失**：文中只估计了三维旋转，没有估计平移，对于机器人抓取等实际应用限制较大。
- **NAVI 的绝对性能**较低，sim-to-real 迁移问题仍是未解难题。
- **对照公平性有限**：
  - OnePose++ 和 BoxDreamer 使用了不同的视角数（48 和 5），虽说明是为了适配单视角设定，却未必可比较，但仍会在一定程度上影响对比的公平性；
  - Free3D 使用扩散模型做 NVS 骨干，与 NOPE 训练的细节差异没有得到完全控制。
- **大视角变化性能欠佳**：当参考-查询视角差在 45°–90° 之间时，OrienPose 的性能会出现明显下降，泛化能力仍有提升空间。
- **受限于无 CAD 设定**：对于结构对称或视觉上模糊不清的物体，仅靠外观模板匹配，依然会存在方位歧义的隐患。

---

（完）
