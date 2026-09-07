---
title: "EgoXtreme: A Dataset for Robust Object Pose Estimation in Egocentric Views under Extreme Conditions"
title_zh: EgoXtreme：极端条件下自视角鲁棒物体位姿估计数据集
authors: "Yoon, Taegyoon, Han, Yegyu, Ji, Seojin, Park, Jaewoo, Kim, Sojeong, Kwon, Taein, Kim, Hyung-Sin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Yoon_EgoXtreme_A_Dataset_for_Robust_Object_Pose_Estimation_in_Egocentric_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 构建了含极端视觉条件的自视角6D位姿数据集，可为航天器位姿估计算法训练与评估提供数据集设计参考
tldr: 现有6D物体位姿估计基准多在受控条件下采集，不能覆盖真实应用中常见的严重运动模糊、动态光照和遮挡，导致模型泛化受限。为此作者提出EgoXtreme，这是一个完全从自视角采集的大规模6D位姿数据集，包含三类挑战性场景。该数据集用于训练和评测鲁棒位姿模型，能更好地体现真实应用与实验室数据的差距。这项工作可为构建航天器位姿估计的复杂场景数据集提供借鉴。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1440, \"height\": 788, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1800, \"height\": 911, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 805, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1809, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 872, \"height\": 434, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1626, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1630, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1807, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 621, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yoon-egoxtreme-a-dataset-for-robust-object-pose-estimation-in-egocentric-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 723, \"height\": 1011, \"label\": \"Table\"}]"
motivation: 现有6D位姿数据集无法体现自视角应用中的运动模糊、动态光照与遮挡，制约了鲁棒位姿估计的真实应用。
method: 从自视角大规模采集构造EgoXtreme数据集，覆盖多种挑战性成像条件以支撑6D位姿估计训练与基准测试。
result: 该数据集能呈现真实应用与受控实验室数据间的显著差距，为鲁棒模型评估提供更有难度的测试平台。
conclusion: 通过推进真实复杂条件下的位姿估计评测，本数据集对航天器等高价值目标的鲁棒位姿算法研究有参考意义。
---

## Abstract
Smart glass is emerging as an useful device since it provides plenty of insights under hands-busy, eyes-on-task situations. To understand the context of the wearer, 6D object pose estimation in egocentric view is becoming essential. However, existing 6D object pose estimation benchmarks fail to capture the challenges of real-world egocentric applications, which are often dominated by severe motion blur, dynamic illumination, and visual obstructions. This discrepancy creates a significant gap between controlled lab data and chaotic real-world application. To bridge this gap, we introduce EgoXtreme, a new large-scale 6D pose estimation dataset captured entirely from an egocentric perspective. EgoXtreme features three challenging scenarios--industrial maintenance, sports, and emergency rescue--designed to introduce severe perceptual ambiguities through extreme lighting, heavy motion blur, and smoke. Evaluations of state-of-the-art generalizable pose estimators on EgoXtreme indicate that their generalization fails to hold in extreme conditions, especially under low light. We further demonstrate that simply applying image restoration (e.g., deblurring) offers no positive improvement for extreme conditions. While performance gain has appeared in tracking-based approach, implying using temporal information in fast-motion scenarios is meaningful. We conclude that EgoXtreme is an essential resource for developing and evaluating the next generation of pose estimation models robust enough for real-world egocentric vision. The dataset and code are available at https://taegyoun88.github.io/EgoXtreme/

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究背景**：智能眼镜在“双手忙碌、视线专注”的应用场景中提供了大量有效信息；要理解佩戴者的环境上下文，**自视角中的 6D 物体位姿估计**变得越来越关键。
- **现有问题**：已有的 6D 位姿估计基准大多在**受控条件下**采集，无法反映真实自视角应用中普遍存在的**严重运动模糊、动态光照和视觉遮挡**等复杂情况，导致受控实验室数据与真实混沌应用之间存在显著差异（gap）。
- **核心目标**：论文引入 **EgoXtreme**——一个大规模、完全从自视角采集的 6D 位姿估计数据集，专门覆盖真实应用中最具挑战性的极端场景，以此支撑鲁棒位姿估计模型的开发与评测。

## 2. 方法论：核心思想与关键技术细节

- 论文的核心**方法论贡献**不在于设计新的位姿估计算法，而在于构建一个新的**基准数据集**，用于暴露现有模型在极端条件下的泛化瓶颈，并推动鲁棒模型的研究。
- 数据集设计要点：
  - **数据来源**：完全从**自视角（egocentric perspective）** 采集，不采用第三方视角模拟。
  - **场景设计**：包含三个具有真实任务背景的挑战性场景：
    - 工业维护（industrial maintenance）
    - 体育运动（sports）
    - 应急救援（emergency rescue）
  - **退化因素注入**：通过**极端光照**、**重度运动模糊**和**烟雾**等物理条件，主动引入严重的感知模糊性和视觉干扰，以此模拟真实世界的设备佩戴者在“低头作业、快速移动、环境混乱”状态下的视觉输入。
  - 该数据集可用于**训练**和**基准测试**两类用途，服务于新的模型研究周期。

## 3. 实验设计

- **评测数据集**：以 EgoXtreme 自身作为测试平台，分别评估不同方法在极端自视角条件下的表现。
- **Benchmark 构成**：三个场景维度形成自然的分组式评测，同一方法可在不同退化条件下分别考核。
- **对比与分析的方法类型**：
  - **通用/可泛化 6D 位姿估计器**（state-of-the-art, SOTA）：考察现有泛化方法在不同于其训练分布的数据上的迁移能力；
  - **图像复原预处理方法**（如图像去模糊 deblurring）：考察“先复原再位姿估计”这一直观手段是否能够恢复性能；
  - **基于时序/追踪的位姿估计方法**（tracking-based）：考察利用视频帧间时间关联对缓解快速运动场景中单帧歧义的有效性。
- 对比结论为：SOTA 泛化模型普遍**无法在极端条件下保持泛化性能**，尤其在低光照下表现最差。

## 4. 资源与算力

- **论文文本中（仅摘要被提供）未明确说明** GPU 型号、数量、训练时长、数据标注的算力消耗等具体资源信息。
- 由于这是一篇数据集论文，缺少标注设备、人工标注规模、渲染/采集硬件等资源细节；不过，核心内容以数据采集与线下评测为主，其算力负担不体现在模型训练过程。

## 5. 实验数量与充分性

- **实验分组数量有限但目标明确**，从提供的摘要层面可识别出至少三组关键实验：
  1. SOTA 泛化位姿估计器的整体基准评测；
  2. 基于图像复原（去模糊）预处理前后对比的消融式实验；
  3. tracking-based 方法的额外性能验证。
- **覆盖率**：在原始采样数据范围内实验设计较为充分，在场景划分上能覆盖三类独立任务且都反映真实自视角使用环境，有助于说明普遍性；
- **公平性**：将三个不同挑战场景分开考察，便于定位模型的失败模式（例如低光最为明显），对比结论较为可信；
- **充分性的注意事项**：摘要限于展示存在的性能差距和方向性判断，缺乏大量量化表格与分场景分类数值，无法借此对统计差异的显著度、指标分布离散程度、各类目标间的难度平衡做更深层的检验。

## 6. 主要结论与发现

- **主要结论**：EgoXtreme 揭示了 SOTA 位姿估计器在真实自视角极端条件下的**泛化失败**，表明当前模型距真实世界应用仍有明显差距。
- **性能发现**：
  - 普遍情况：现有模型的泛化能力在极端光照、运动模糊和烟雾下失效；
  - 特定情境：**低光条件下失败最为严重**；
  - 复原手段无效：简单加在流水线前端的图像复原（例如去模糊）对极端条件下的位姿估计**没有正向收益**；
  - 时间线索可行：tracking-based 方法的引入带来了性能提升，说明在快速运动场景中**利用帧间时序信息**是解决极端自视角位姿退化的有效方向。
- **综合定位**：EgoXtreme 可作为下一代面向真实世界自视角视觉的鲁棒位姿估计模型开发与评测的基础资源。

## 7. 优点

- **真实数据优于合成再退化**：完全从真实自视角中采集，而非后期在受控图像上注入噪声，确保退化模式与真实设备实际成像特征相符。
- **非典型数据集选题**：关注此前 6D pose 基准很少覆盖的“极端环境”，有效补足了自视角与常规受控场景之间的数据集断层。
- **任务场景选择具有现实价值**：工业维护、运动、应急救援均是智能眼镜的核心使用场景，具有较强的应用指向性。
- **清晰的失败分析结论**：不仅给出性能下降现象，还通过复原算法对比识别出“语义信息丢失而非噪声干扰是主要障碍”这一重要判定。
- **提供研究方向信号**：明确指出 time-domain information（基于时序方法）是当前条件下最有希望的提升路径，给后续算法研究提供直接线索。

## 8. 不足与局限

- **模型覆盖线有限**：方法对比集中于 baseline 的 benchmark，未在摘要中体现更多别的领域的先进方法（如基于基础模型、扩散模型、新范式方法）的对比。
- **单个视觉域的主导**：光照、运动模糊、烟雾被有意设计在三个离散的脚本场景中，未充分探讨它们**联合发生**（如低光+浓烟同时存在）的组合空间；真实情况往往多种退化并存。
- **缺少数据量详细信息**：论文摘要未提供具体帧数、对象类别数、标注帧比例以及不同场景难度之间的量化差异，限制对数据集规模的充分判断。
- **评测指标与差异显著性**：文本层面缺少公开量化指标（如 ADD/S）与标准误差，未充分说明模型差距的稳健性与类别间偏差。
- **标签机制的可扩展性问题**：自视角画幅小、运动剧烈、遮挡重，手工标注高质量位姿标签的难度较大，需更多说明标注协议、质量控制以及验证集互评标准，否则用户使用过程中可能引入标注偏差。
- **应用覆盖有限**：仅涉及穿戴设备向的短距离场景，未能覆盖高价值目标（如航天器）的长距离、多变光照、星上资源受限的双目/单目跨度等更专的领域；该数据集可用作方法论参考，而非直接的航天器位姿数据集。

---

（完）
