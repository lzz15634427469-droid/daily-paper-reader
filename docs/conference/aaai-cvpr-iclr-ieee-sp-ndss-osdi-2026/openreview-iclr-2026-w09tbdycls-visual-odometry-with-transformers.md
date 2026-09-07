---
title: Visual Odometry with Transformers
title_zh: 基于Transformer的视觉里程计
authors: "Vladimir Yugay, Duy Kien Nguyen, Theo Gevers, Cees G. M. Snoek, Martin R. Oswald"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=w09tBdYcls"
tags: ["query:pe"]
score: 5.0
evidence: 端到端单目视觉里程计逐帧预测相机位姿；可为航天器单目相对运动估计提供基线方法。
tldr: 传统单目视觉里程计依赖复杂的标定与优化模块，难以在未知真实场景中推广。本文提出基于Transformer的端到端单目视觉里程计方法，直接预测逐帧相机位姿，省去BA等人工设计组件。在标准视觉里程计基准上，该方法匹配或超越复杂流水线的精度，同时简化了标定依赖。研究展示了长序列与逐帧估计的可行性，可为航天器单目导航中的相对运动估计提供端到端方案。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 传统单目视觉里程计流水线复杂、依赖相机标定和超参数，泛化到未知场景困难。
method: 提出基于Transformer的端到端视觉里程计，直接由单目视频预测逐帧相机位姿，消除BA等手工优化模块。
result: 在基准上证明了端到端方法能够保持良好精度并简化流程，支持长时间序列估计。
conclusion: 该工作说明单目视觉里程计可被端到端建模，为基于图像序列的航天器相对运动估计提供了可借鉴途径。
---

## Abstract
Modern monocular visual odometry methods typically combine pre-trained deep learning components with optimization modules, resulting in complex pipelines that rely heavily on camera calibration and hyperparameter tuning, and often struggle in unseen real-world scenarios. Recent large-scale 3D models trained on massive amounts of multi-modal data have partially alleviated these challenges, providing generalizable dense reconstruction and camera pose estimation. Still, they remain limited in handling long videos and providing accurate per-frame estimates, which are required for visual odometry. In this work, we demonstrate that monocular visual odometry can be addressed effectively in an end-to-end manner, thereby eliminating the need for handcrafted components such as bundle adjustment, feature matching, camera calibration, or dense 3D reconstruction. We introduce VoT, short for **V**isual **o**dometry **T**ransformer, which processes sequences of monocular frames by extracting features and modeling global relationships through temporal and spatial attention. Unlike prior methods, VoT directly predicts camera motion without estimating dense geometry and relies solely on camera poses for supervision. The framework is modular and flexible, allowing seamless integration of various pre-trained encoders as feature extractors. Experimental results demonstrate that \ours scales effectively with larger datasets, benefits substantially from stronger pre-trained backbones, generalizes across diverse camera motions and calibration settings, and outperforms traditional methods while running more than $3\times$ faster. The code will be released.

---

## 论文详细总结（自动生成）

> **说明**：所提供的网页正文其实是一个浏览器验证拦截页（CAPTCHA），并非论文全文。以下总结主要基于嵌入在页面 Markdown 元数据中的标题、作者、摘要以及摘录信息整理而成；由于缺少正文、图表与实验表格，凡涉及实验明细之处将据实指出信息缺口，不作无依据的推断。

### 1. 核心问题与整体含义

- 传统单目视觉里程计（VO）通常由预训练深度模块与 Bundle Adjustment（BA）、特征匹配、相机标定等优化模块组合而成，形成复杂流水线，对相机内参、超参数高度敏感，在未知真实场景中泛化能力有限。
- 虽然近期大规模 3D 基础模型可提供一定的密集重建与姿态估计能力，但仍存在**难以处理长视频**、**不能提供逐帧精确位姿**的问题，而这正是视觉里程计的核心需求。
- 本文核心论点是：**单目 VO 可以作为端到端任务直接建模**，无需手工设计的 BA、特征匹配、相机标定或密集三维重建模块，从而以更简洁的流程获得与传统复杂流水线匹敌或更优的性能。

### 2. 方法论（核心思想与关键技术）

- **核心思想**：将单目视觉里程计重构为一个序列级位姿回归问题，由单个深度模型直接输出相机运动，规避传统几何优化。
- **模型架构（VoT, Visual odometry Transformer）**：
  - 输入为连续单目帧序列；
  - 通过特征提取器提取图像特征；
  - 利用 Transformer 的**时间注意力**建模帧间运动关系、**空间注意力**建模场景结构关系，以捕捉全局依赖；
  - 直接预测逐帧相机位姿。
- **关键机制与去手工化**：
  - 不需要稠密深度估计或三维几何重建；
  - 训练监督信号**仅来自相机位姿真值**，无需光度一致性、深度等辅助损失；
  - 网络端到端可微，消除 Bundle Adjustment、特征匹配、相机内参显式标定等人工组件。
- **模块化设计**：整体框架对特征提取器不敏感，可无缝替换/集成不同预训练编码器（pre-trained backbones），便于在多种视觉基座上扩展。
- 摘要中未提供显式数学公式；可理解为一种基于 Transformer 编码器 + 位姿回归头的监督学习流水线。

### 3. 实验设计

- **数据集与场景**：摘要并未列出具体数据集名称；仅提及在“标准视觉里程计基准”上进行验证，并考察了多样相机运动模式以及不同相机标定设置下的泛化。
- **对比方法**：摘要指明与**传统视觉里程计方法**进行了对比；从其“仍不擅长长视频和逐帧估计”的表述可推测，相关工作可能与大规模 3D 基础模型相关，但摘要未明确列出具体基线模型名称。
- **验证维度**（从摘要可提取四类实验方向）：
  - 更大训练数据规模是否带来增益；
  - 更强预训练 backbone 的影响；
  - 在不同相机运动与标定条件下的泛化能力；
  - 与传统方法在精度和推理速度上的比较。

### 4. 资源与算力

- **文中未提供任何 GPU 型号、数量、训练时长、参数量或 FLOPs 等算力信息**。
- 仅有一点运行时相对效率：VoT 的推理速度比传统方法快 **3 倍以上**；但“快 3 倍”是相对速度，不含训练侧的硬件说明。
- 完整算力细节需查看全文或发布代码后的版本来补充。

### 5. 实验数量与充分性评估

- 摘要所体现的实验组数量大约为 4–5 组方向（规模消融、backbone 消融、泛化测试、精度对比、速度对比），呈现一定梯度设计，符合“端到端 VO”的验证逻辑。
- 由于正文未获取，以下不可验证：
  - 各基准上的具体数值指标（ATE、RPE 等）缺失；
  - 缺少与最新神经 SLAM / 大规模 3D 基础模型的定量比较；
  - 长序列轨迹的可视化、漂移累积随序列长度的变化未展示；
  - 消融细节（如去掉时间或空间注意力的效果）未知。
- 因此，对**充分性、公平性**暂难作出最终判断。以摘要披露的口径而言，实验设计思路合理；但仍需要阅读全文核对数据才能给出可靠结论。

### 6. 主要结论与发现

1. 单目视觉里程计可以被端到端系统有效解决，无需复杂传统几何优化。
2. 模型能有效利用更大数据集带来的规模红利，且从更强的预训练特征提取器中显著受益。
3. 面对不同相机运动类型与标定条件时具有一定的跨域泛化表现。
4. 在精度上达到或超过传统复杂 VO 流水线，同时推理速度快 3 倍以上，简化了流程与标定负担。
5. 端到端方案在长序列视频上的逐帧位姿估计是可行的，为单目 VO 提供了一种更简洁、可扩展的建模范式。

### 7. 优点

- **端到端简化**：从几何优化复合流水线跳转至“视频进、位姿出”，直接降低对相机标定和超参调优的依赖。
- **归纳偏置清晰**：时空注意力的组合天然适配 VO 中的运动连续性与场景几何约束。
- **无密集重建依赖**：避免对 3D 几何监督、深度真值的需求，显著降低标注/数据构造门槛。
- **框架模块化**：可灵活更换不同预训练视觉骨干，容易从模型库进步中获益。
- **应用潜力强**：对太空探索、机器人导航、移动设备 AR 等受算力/标定约束较大的场景，这种无标定、快 3 倍以上的方案有一定吸引力。
- 社区贡献角度上作者明确说明代码将开源，有利于复现与后续推进。

### 8. 不足与局限

- **信息可得性局限**：本次分析被 CAPTCHA 页面阻断，无法获取论文正文、实验定量表格和可视化结果；任何更进一步的细节评估都有赖于完整论文。
- **方法本身可能存在的隐患（未在摘要中被讨论）**：单目视觉里程计普遍存在尺度漂移问题、长序列累加漂移问题；摘要未提及在这些方面的专项设计或崩溃案例。
- **适用范围有待验证**：视频中出现严重运动模糊、动态物体、光照突变等现实情形时，模型表现未知。
- **监督依赖**：虽然去掉了几何监督，但仍需要大量有精确位姿真值的训练数据；这类数据在室外、大尺度场景中的采集成本较高。
- **复杂度与实时性描述有限**：文中仅给出相对“快 3 倍”的宣传结论，未披露模型参数量、内存占用、具体帧率/图像分辨率等工程指标。
- 如果面向航天器单目相对运动估计等新应用，需要考虑在轨嵌入式硬件、光照极端、无先验纹理等场景的适配性——这些问题在本论文的摘要中尚无对应实验证据。

（完）
