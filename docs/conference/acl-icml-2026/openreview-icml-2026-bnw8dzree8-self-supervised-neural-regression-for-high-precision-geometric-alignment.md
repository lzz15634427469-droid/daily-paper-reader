---
title: Self-Supervised Neural Regression for High-Precision Geometric Alignment
title_zh: 面向高精度几何对齐的自监督神经回归
authors: "Jaehyun Kim, Youngil Kwon"
date: 2026-01-22
pdf: "https://openreview.net/pdf/5129ff2f6d5a9f8c646031b69badfcc6c32c77f8.pdf"
tags: ["query:pe"]
score: 4.0
evidence: 六自由度几何对齐模型估计最优校正参数
tldr: 论文针对大型物理系统在机械失配下难以高精度几何对齐的问题，提出自监督机器学习框架。系统由大规模高粒度独立传感器阵列组成，每个传感器由六自由度几何对齐模型描述，通过同时训练大量可微轻量仿射变换模块求解最优校正参数，并构造源自物理一致性约束的可微物理信息卡方代价函数，无需数据标注。实验表明该框架可高效估计六自由度校正参数，其位姿参数估计与对齐思路可迁移至相对位姿确定任务。
source: ICML-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 大型物理系统存在机械失配，传统方法难以在无标注条件下高精度求解各传感器的几何对齐参数。
method: 提出自监督框架，为每个传感器建立六自由度几何对齐模型，同时训练大量可微仿射变换模块，并用物理信息卡方代价函数优化。
result: 实验表明该框架无需数据标注即可估计最优六自由度校正参数，实现大规模传感器阵列的高精度对齐。
conclusion: 将物理一致性约束引入自监督回归，为位姿与几何对齐参数估计提供了可迁移范式。
---

## Abstract
We propose a Self-Supervised Machine Learning framework for the high-precision geometric alignment of large-scale physical systems with mechanical misalignment. The system comprises a large-scale high-granularity array of independent sensors, each defined by a six-degree-of-freedom (6-DoF) geometric alignment model. To determine the optimal correction parameters for each sensor, we simultaneously train a substantial number of differentiable lightweight affine transformation modules. Our core contribution is the formulation of a differentiable Physics-Informed $\chi^2$ cost function, which is derived from the system's physical consistency constraints and real data. This framework operates without data labeling, using the physics principles themselves as a supervisory signal. We applied this approach to the Inner Tracking System of the ALICE experiment at CERN, training the models on a large sample of particle trajectories. Compared with the standard method, our proposed approach leads to a reduced systematic bias and an improved resolution in the Distance of Closest Approach (DCA), which is the primary metric determining the track pointing accuracy to the primary vertex, specifically in critical kinematic regions.

---

## 论文详细总结（自动生成）

> 注：提供的“PDF 提取文本”实际为 OpenReview 的 CAPTCHA 验证页，未包含论文正文。以下总结主要依据论文摘要与元数据；未披露的细节将明确标注为“未说明/无法确认”。

## 1. 核心问题与整体含义

- **研究背景**：大型物理系统在装配和运行中会存在机械失配，导致大规模传感器阵列的几何位置偏离理想状态，进而影响测量精度。
- **核心问题**：传统方法难以在无数据标注条件下，为每个传感器高精度求解几何对齐参数，尤其是六自由度（6-DoF）校正参数。
- **典型场景**：论文将该问题应用于 CERN 的 ALICE 实验内径迹系统（Inner Tracking System, ITS）。该系统中，粒子轨迹重建对传感器几何对齐精度要求极高。
- **关键指标**：DCA（Distance of Closest Approach，最近接近距离）是决定径迹指向主顶点精度的核心指标，尤其在某些关键运动学区域。
- **整体含义**：论文尝试把物理一致性约束引入自监督神经回归，用物理规律替代人工标注作为监督信号，为大规模几何对齐和位姿参数估计提供可迁移范式。

## 2. 方法论

- **核心思想**：采用自监督机器学习框架，不依赖数据标注，而是利用系统自身的物理一致性约束作为监督信号。
- **系统建模**：
  - 系统由大规模、高粒度、相互独立的传感器阵列组成。
  - 每个传感器由一个六自由度（6-DoF）几何对齐模型描述。
- **关键技术细节**：
  - 同时训练大量可微、轻量的仿射变换模块。
  - 这些模块用于为每个传感器估计最优校正参数。
  - 核心贡献是构造可微的 Physics-Informed \(\chi^2\) 代价函数。
  - 该代价函数来源于系统物理一致性约束与真实数据。
- **算法流程（文字说明）**：
  1. 为传感器阵列建立 6-DoF 几何对齐参数化模型。
  2. 使用粒子轨迹等真实数据前向计算物理一致性残差。
  3. 将残差组织为可微的物理信息 \(\chi^2\) 代价。
  4. 通过反向传播同时优化大量轻量仿射变换模块。
  5. 得到各传感器的最优几何校正参数，实现高精度对齐。
- **未说明内容**：具体公式、网络结构、优化器、损失权重、训练策略等均未在提供内容中给出。

## 3. 实验设计

- **数据集/场景**：CERN 的 ALICE 实验 Inner Tracking System，使用大量粒子轨迹样本进行训练。
- **Benchmark**：与标准方法进行对比。
- **评价指标**：
  - DCA 的系统偏差（systematic bias）。
  - DCA 的分辨率（resolution）。
  - 特别关注关键运动学区域。
- **对比方法**：仅明确提到“标准方法”，未列出其他基线或学习型方法。
- **任务范围**：主要聚焦于 6-DoF 几何对齐参数估计；摘要提到其位姿参数估计与对齐思路可迁移至相对位姿确定任务，但未说明是否实际开展相关实验。

## 4. 资源与算力

- 提供内容中**未说明**使用的 GPU 型号、数量、训练时长、显存、参数量或计算集群规模。
- 因此无法评估该方法的计算成本、训练效率和可复现性资源需求。

## 5. 实验数量与充分性

- 从摘要与元数据看，主要实验为一个真实大型物理实验场景：ALICE ITS。
- 对比对象为标准方法。
- 未提及多数据集实验、消融实验、不同传感器配置实验、敏感性分析、统计显著性检验或跨任务验证。
- 因此，**实验充分性无法确认**；实验覆盖范围可能有限，客观性与公平性需结合全文和评审意见判断。

## 6. 主要结论与发现

- 所提自监督框架无需数据标注，即可估计最优的 6-DoF 校正参数。
- 该方法能够支持大规模传感器阵列的高精度几何对齐。
- 与标准方法相比，摘要声称其降低了系统偏差，并改善了 DCA 分辨率。
- 改善在关键运动学区域尤为明显。
- 论文认为，将物理一致性约束引入自监督回归，可为位姿与几何对齐参数估计提供可迁移范式。

## 7. 优点

- **无需标注**：利用物理原理作为监督信号，降低对人工标注数据的依赖。
- **物理信息驱动**：可微 Physics-Informed \(\chi^2\) 代价函数将物理一致性直接纳入优化目标。
- **可扩展性**：通过同时训练大量轻量仿射变换模块，适配大规模传感器阵列。
- **真实场景验证**：应用于 CERN ALICE ITS，具有较强现实意义。
- **指标相关性强**：以 DCA 偏差和分辨率为核心指标，直接关联径迹指向主顶点的精度。
- **可迁移性**：思路可推广至相对位姿确定等几何参数估计任务。

## 8. 不足与局限

- **全文未获取**：提供的 PDF 文本是验证页，无法核实方法公式、实验细节和结论强度。
- **实验覆盖有限**：仅见一个主要应用场景，跨数据集、跨探测器、跨任务泛化能力未知。
- **缺少算力与复现信息**：未说明 GPU、训练时长、超参数和实现细节。
- **缺少消融与公平性分析**：未说明各模块贡献、基线调参情况、统计显著性。
- **依赖物理模型与数据质量**：物理一致性约束和真实数据质量会影响监督信号可靠性。
- **模型假设限制**：每个传感器由 6-DoF 几何模型和可微仿射变换描述，可能不适用于更复杂失配或非仿射形变。
- **评审状态提示**：元数据标注为 ICML-2026-Rejected-Public，score 为 4.0，说明该工作可能未获接收，需谨慎看待其结论与贡献。

（完）
