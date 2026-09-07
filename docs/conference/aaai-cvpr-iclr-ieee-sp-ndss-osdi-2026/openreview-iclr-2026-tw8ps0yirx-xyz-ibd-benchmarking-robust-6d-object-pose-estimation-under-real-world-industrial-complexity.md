---
title: "XYZ-IBD: Benchmarking Robust 6D Object Pose Estimation under Real-World Industrial Complexity"
title_zh: XYZ-IBD：面向真实工业复杂性的鲁棒6D目标位姿估计基准
authors: "Junwen Huang, Jiaqi Hu, Jizhong Liang, Nassir Navab, Peter KT Yu, Slobodan Ilic, Martin Sundermeyer, Benjamin Busam"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=TW8ps0YirX"
tags: ["query:pe"]
score: 6.0
evidence: 提出了工业分拣6D位姿评测基准，其强遮挡、金属对称目标等设计可作为航天器深度学习位姿精度评估方法参考
tldr: 现有6D位姿估计基准多集中于接近饱和的家用物体，难以反映复杂工业场景中的真实难点。XYZ-IBD构建了面向抓取场景的6D位姿基准，包含金属、强反光及多对称物体，并具有毫米级标注和很强遮挡与堆叠。该基准用于评测现有深度学习位姿算法在真实复杂性下的表现，暴露工业应用中尚未解决的目标。其评测思路可迁移到航天器位姿估计精度评估，特别是在纹理弱、对称性强等场景中。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有6D位姿基准在家用物体上接近饱和，缺少工业级反射、遮挡和杂乱堆叠的真实挑战。
method: 构建XYZ-IBD数据集，采集金属多对称物体的高密度遮挡分拣场景并提供毫米级精确标注，建立6D鲁棒位姿评测基准。
result: 该基准暴露出复杂工业视觉下尚未解决的位姿估计问题，可有效区分现有方法的真实性能。
conclusion: 通过复杂条件下的标准评测推动6D位姿估计落地应用，亦可为航天器位姿评估基准设计提供借鉴。
---

## Abstract
We introduce XYZ-IBD, a bin-picking benchmark for 6D pose estimation that captures real-world industrial complexity, including challenging object geometries, reflective materials, severe occlusions, and dense clutter. The dataset reflects authentic robotic manipulation scenarios with millimeter-accurate annotations. Unlike existing datasets that primarily focus on household objects, which approach saturation, XYZ-IBD represents the unsolved vision problems in the real-world application. The dataset features metallic and mostly symmetrical objects of varying shapes and sizes. These objects are heavily occluded and randomly arranged in bins with high density, replicating the challenges of industrial bin-picking.
XYZ-IBD was collected using two high-precision industrial cameras and one commercially available camera, providing RGB, grayscale, and depth images. It contains 75 multi-view real-world scenes with around 273k annotated object instances, along with a large-scale synthetic dataset rendered under simulated bin-picking conditions. We employ a meticulous annotation pipeline that includes anti-reflection spray, multi-view depth fusion, and semi-automatic annotation, achieving millimeter-level pose labeling accuracy required for industrial manipulation. Quantification in simulated environments confirms the reliability of the ground-truth annotations.
We benchmark state-of-the-art methods on 2D detection and 6D pose estimation tasks on our dataset, revealing significant performance degradation in our setups compared to current academic household benchmarks. By capturing the complexity of real-world bin-picking scenarios, XYZ-IBD introduces more realistic and challenging vision problems for future research.

---

## 论文详细总结（自动生成）

# 中文总结：XYZ-IBD：面向真实工业复杂性的鲁棒 6D 目标位姿估计基准

## 1. 论文的核心问题与整体含义（研究动机和背景）
- 6D 目标位姿估计对机器人抓取、工业自动化等应用至关重要。
- 现有主流基准多基于家用物体（household objects），且在这些基准上算法性能已接近饱和，难以反映真实工业场景中仍未解决的视觉挑战。
- 工业分拣场景中普遍存在**金属反光**、**目标对称性强**、**严重遮挡**和**密集堆叠杂乱**等问题，现有基准无法为算法提供足够真实的评测环境。
- 论文提出 **XYZ-IBD**，一个面向真实工业 bin-picking（料箱抓取）场景的 6D 位姿估计基准，以还原实际应用中的复杂视觉条件，推动 6D 位姿估计从学术 benchmark 走向落地。

## 2. 论文提出的方法论：核心思想与关键技术
- 论文并未提出新的位姿估计算法，而是通过**数据采集与标注体系构建一个高难度基准**。
- 核心设计思路：在真实工业抓取环境中，用多台相机采集高密度堆叠、强遮挡的金属/对称物体场景，并获取**毫米级精确**的 6D 位姿标注，从而形成可量化评测的 ground-truth。
- 传感器配置：采用**两台高精度工业相机 + 一台商业可用相机**，同时采集 RGB、灰度图和深度图像。
- 数据规模与构成：
  - **75 个多视角真实场景**；
  - 约 **273,000 个标注物体实例**；
  - 同时包含大规模**合成数据集**（模拟 bin-picking 条件），用于辅助训练与扩展。
- 标注流程的关键技术细节：
  - **抗反射喷涂（anti-reflection spray）**：减少金属表面反射对重建和标注的干扰；
  - **多视角深度融合**：提高深度完整性和几何精度；
  - **半自动标注**：结合人工校验，降低全手工标注的误差；
  - 在**模拟环境中量化验证**标注精度，保证真实场景标注达到 mm 级。
- 基准中的物体多为金属材质且大多数具有对称性，形状和尺寸多样，且被随机、高密度地放入料箱中，能够模拟真实工业分拣中机器人视觉系统面临的最棘手情况。

## 3. 实验设计
- 评测任务：**2D 检测**与 **6D 位姿估计**。
- 使用场景：XYZ-IBD 真实料箱场景 + 大规模合成数据；专门面向复杂工业分拣场景。
- 对比对象：论文声称对当前 **state-of-the-art 方法**进行了 Benchmark（但提取的文本中未列出具体算法名称或每个实验的数值）。
- 主要结果模式：现有 SOTA 方法在 XYZ-IBD 上的性能相比在现有学术/家用物体基准上有**显著下降**，表明该基准更能暴露真实工业环境下的未解难题。
- 标注可靠性验证：在模拟环境中进行量化，验证 ground-truth 的毫米级精度。

## 4. 资源与算力
- 所给文本中**没有明确说明**训练或评测时使用的算力情况（如 GPU 型号、数量、训练时长等）。
- 仅交代了数据采集的硬件设备（两台高精度工业相机、一台商用相机），未提及计算平台配置。

## 5. 实验数量与充分性
- 虽然论文称对 2D 检测和 6D 位姿估计进行了 benchmark，并对比了多种 SOTA 方法，但就本次提供的文本来看，**缺少具体实验次数、数据集划分、评价指标数值和对比方法列表**。
- 作为数据集/基准类论文，其核心实验不是模型消融，而是通过基准检验现有方法在不同难度下的表现；因此“实验充分性”主要取决于评测协议是否覆盖典型位姿误差指标、对称性处理和遮挡等级。
- 就该摘要而言，实验设计在理念上是合理的：用模拟环境验证标注精度，再对多任务做算法评测；
- 但若只看摘要，**无法客观核实评估公平性与区分度**，需要阅读论文正文中的指标与误差定义才能判断。

## 6. 论文的主要结论与发现
- XYZ-IBD 能够反映**真实工业 bin-picking 场景中的复杂视觉问题**，比当前家用物体基准更具挑战性。
- 现有 SOTA 方法在真实反光、强遮挡、密集堆叠、对称物体条件下性能显著退化，说明该方向仍远未解决。
- 该基准可成为未来研究、算法对比与验证的重要平台，推动 6D 位姿估计技术在实际工业视觉任务中的应用落地。

## 7. 优点
- **真实工业场景**：直接采集于料箱抓取环境，包含金属反光、密集堆叠、强遮挡和高密度排列等实际难题，比合成或简单桌面场景更贴近应用。
- **对象与任务设计合理**：专注于“金属+多对称”物体，正是工业视觉中典型的挑战组合，能有效形成性能差异。
- **毫米级标注**：结合抗反射喷涂、多视图深度融合和半自动标注，并利用模拟环境验证精度，提升了 ground truth 的可信度。
- **多模态数据支持**：同时提供 RGB、灰度、深度，且包含多视角真实场景和大规模合成数据，兼顾训练素材与评测需求。
- **填补空白**：直接面向工业级反射/遮挡场景，避免了既有家用数据集接近饱和导致的评测区分度不足问题。

## 8. 不足与局限
- 提取到的内容缺少**定量结果**和评测细节，无法直接评估该基准的实际难度分布、误差指标定义及不同方法的提升空间。
- 数据集规模有限（仅 75 个真实场景），物体多为金属对称类，**泛化到其他工业对象（如透明件、非金属、复杂装配环节）的能力尚不明确**。
- 合成数据与真实数据之间可能存在 domain gap，但文本中未说明其训练与评测的迁移程度。
- 半自动标注虽然达到毫米级，但极端遮挡或镜面反射下仍可能引入标注偏差。
- 未给出算力与评测协议细节，外部复现、扩展和公平比较的门槛仍较高。

（完）
