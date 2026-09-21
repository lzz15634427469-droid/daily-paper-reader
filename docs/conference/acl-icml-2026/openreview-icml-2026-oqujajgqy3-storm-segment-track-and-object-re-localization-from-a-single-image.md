---
title: "STORM: Segment, Track, and Object Re-Localization from a Single Image"
title_zh: STORM：从单张图像进行分割、跟踪与目标重定位
authors: "Yu Deng, Teng Cao, Hikaru Shindo, Quentin Delfosse, Jiahong Xue, Kristian Kersting"
date: 2026-04-30
pdf: "https://openreview.net/pdf/0b57251c7c1196fb54e8341058884f842426693e.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 无需CAD模型、从单张参考图像进行六自由度位姿估计与跟踪
tldr: 针对现有六自由度位姿估计与跟踪依赖CAD模型、人工掩码且遮挡或快速运动下易失败的问题，本文提出STORM统一框架。方法以单张参考图像为条件，结合层次化空间融合注意力实现单或多参考融合，并可选用视觉语言语义条件。该框架在遮挡和快速运动下提升了位姿跟踪的鲁棒性，并能识别失败情形。其单图六自由度位姿估计思路对航天器单目位姿估计具有方法借鉴价值。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 现有6D位姿估计与跟踪依赖CAD模型与人工标注，在遮挡和快速运动下鲁棒性差且难以识别失败。
method: 提出参考条件式6D跟踪框架STORM，采用层次化空间融合注意力支持单或多参考与语义条件。
result: 框架可在单张参考图像下运行，减少人工输入并在遮挡与快速运动下提升鲁棒性。
conclusion: 该工作为无CAD、单图条件下的鲁棒6D位姿估计与跟踪提供了统一方案。
---

## Abstract
Accurate 6D pose estimation and tracking are core capabilities for physical AI systems, yet real-world deployment remains brittle and labor-intensive. 
Many pipelines rely on CAD models, manual masking, or per-object adaptation, and still fail under occlusion or fast motion without a principled way to recognize failure. 
We propose STORM, a unified framework for reference-conditioned 6D tracking that can operate from a single reference image, with minimal manual input and improved robustness. 
STORM combines: (i) Hierarchical Spatial Fusion Attention (HSFA), a task-driven reference-query fusion architecture that supports both single-reference and multi-reference conditioning and can optionally use vision-language semantic conditioning to resolve instance ambiguities; and (ii) a BCE-trained tracking verifier whose continuous compatibility logit is used as an energy-like score to detect drift and trigger automatic re-initialization. 
Experiments on LM-O and YCB-Video show that STORM improves annotation-free pose tracking accuracy over strong baselines and recovers reliably from severe occlusions and rapid viewpoint changes with minimal overhead.

---

## 论文详细总结（自动生成）

> 说明：提供的 PDF 文本实际为 OpenReview 验证页面，并非论文全文。以下总结主要依据给出的摘要、标题与元数据，部分实验细节无法核实。

## 1. 核心问题与整体含义
- 研究动机：6D 位姿估计与跟踪是物理 AI 系统的核心能力，但真实部署仍脆弱且劳动密集。
- 现有问题：许多流程依赖 CAD 模型、人工掩码或逐物体适配；在遮挡或快速运动下容易失败，且缺乏有原则的失败识别机制。
- 整体含义：STORM 试图提供一种“参考条件式 6D 跟踪”统一框架，仅用单张参考图像即可运行，减少人工输入，并提升遮挡与快速运动下的鲁棒性。
- 标题还涉及 Segment、Track、Object Re-Localization，但摘要重点落在 6D 位姿估计与跟踪。

## 2. 方法论：核心思想与关键技术
- 核心思想：以参考图像为条件进行 6D 跟踪，支持单参考与多参考融合，并可选使用视觉语言语义条件解决实例歧义。
- 关键技术一：Hierarchical Spatial Fusion Attention（HSFA）
  - 任务驱动的 reference-query 融合架构。
  - 支持单参考和多参考条件。
  - 可选用视觉语言语义条件，帮助区分相似或歧义实例。
- 关键技术二：跟踪验证器
  - 使用 BCE 训练。
  - 其连续兼容性 logit 被用作类似能量的分数。
  - 用于检测跟踪漂移，并触发自动重初始化。
- 算法流程文字描述：
  - 输入：单张或多张参考图像，以及当前帧/查询。
  - 特征融合：通过 HSFA 在层次化空间上融合参考与查询特征，可选加入语义条件。
  - 位姿跟踪：输出目标 6D 位姿或跟踪结果。
  - 失败检测：验证器计算兼容性分数，低分表示漂移或失败。
  - 恢复机制：触发自动重初始化，以从严重遮挡或快速视角变化中恢复。

## 3. 实验设计
- 数据集/场景：
  - LM-O，即 LineMOD Occlusion，常用于遮挡场景下的 6D 位姿估计。
  - YCB-Video，常用于 6D 位姿估计与跟踪。
- Benchmark：
  - 主要是 6D 位姿估计/跟踪基准。
  - 摘要提到评估“annotation-free pose tracking accuracy”，即无标注或减少标注条件下的位姿跟踪精度。
- 对比方法：
  - 摘要称与“strong baselines”对比，但未在可见内容中列出具体基线名称。
- 鲁棒性场景：
  - 严重遮挡。
  - 快速视角变化。
  - 强调以最小额外开销可靠恢复。

## 4. 资源与算力
- 提供的摘要与元数据未说明 GPU 型号、数量、训练时长、显存或总计算量。
- 因此无法总结具体算力配置；这一点属于信息缺失。

## 5. 实验数量与充分性
- 从可见内容看，实验至少覆盖 LM-O 与 YCB-Video 两个数据集。
- 摘要提到与强基线比较，并验证严重遮挡与快速视角变化下的恢复能力。
- 是否包含消融实验、跨数据集实验、真实机器人实验、失败检测阈值分析等，未在可见内容中说明。
- 因此无法判断实验组数是否充分，也无法评估对比是否完全公平；仅能确认使用了两个常用 6D 位姿 benchmark。

## 6. 主要结论与发现
- STORM 可在单张参考图像条件下运行，减少对 CAD 模型、人工掩码和逐物体适配的依赖。
- 在 LM-O 和 YCB-Video 上，STORM 提升了 annotation-free 位姿跟踪精度，优于强基线。
- 在严重遮挡和快速视角变化下，STORM 能够可靠恢复，且额外开销较小。
- 跟踪验证器可通过兼容性分数检测漂移，并触发自动重初始化，从而提供失败识别与恢复能力。
- 该工作为无 CAD、单图条件下的鲁棒 6D 位姿估计与跟踪提供了统一方案，对航天器单目位姿估计等方向有方法借鉴价值。

## 7. 优点
- 减少人工输入：不依赖 CAD 模型、人工掩码或逐物体适配。
- 单图参考条件：仅需单张参考图像即可运行，部署门槛较低。
- 融合机制灵活：HSFA 支持单参考与多参考，并可选用视觉语言语义条件。
- 具备失败检测：验证器用连续兼容性分数检测漂移，并触发自动重初始化。
- 鲁棒性导向：针对遮挡和快速运动这两个实际难点设计恢复机制。
- 统一框架：将参考条件融合、跟踪与重定位/重初始化整合在一个框架中。

## 8. 不足与局限
- 全文不可得：当前 PDF 提取为验证页面，无法核实公式、网络结构、训练细节与完整实验。
- 实验覆盖有限：可见信息仅涉及 LM-O 和 YCB-Video，缺少更多跨域、真实场景或机器人平台验证。
- 算力未报告：无法评估训练成本、推理速度和实际部署可行性。
- 依赖参考图像：单图参考可能受参考视角、光照、遮挡和域差异影响。
- 验证器标定问题：能量式兼容性分数如何设阈值、是否跨场景稳定，未在可见内容中说明。
- 实时性与长期跟踪：快速运动下的恢复能力虽被强调，但推理延迟和长期漂移抑制效果未知。
- 元数据可能存在偏差：标题、摘要与自动生成元数据之间范围不完全一致，部分结论需以论文全文为准。

（完）
