---
title: "DecomPose: Disentangling Cross-Category Optimization Contention for Category-Level 6D Object Pose Estimation"
title_zh: DecomPose：解耦跨类别优化竞争的类别级6D物体位姿估计
authors: "Yifan Gao, Lu Zou, Zhangjin Huang, Guoping Wang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/d0ff03e0aefdeaaa9eadc179f387d5c86789cfce.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 类别级6D物体位姿估计
tldr: 针对类别级6D物体位姿估计在多类别联合训练时，类别间几何差异导致梯度冲突与负迁移的问题，提出DecomPose难度感知分解框架。方法先用梯度诊断量化模块级跨类别竞争，再按数据驱动难度代理分组并解耦梯度以缓解优化冲突。实验显示该方法能提升位姿估计精度，为多类别6D位姿估计提供可迁移的优化解耦思路。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 类别级6D物体位姿估计多类别联合训练时，类别间几何差异导致梯度冲突与负迁移。
method: 提出DecomPose，基于梯度诊断的难度感知分解框架，按难度分组并解耦梯度。
result: 实验显示该方法能缓解跨类别优化竞争，提升位姿估计精度。
conclusion: 为多类别6D位姿估计提供了可迁移的优化解耦思路。
---

## Abstract
Category-level 6D object pose estimation is typically formulated as a multi-category joint learning problem with fully shared model parameters. However, pronounced geometric heterogeneity across categories entangles incompatible optimization signals in shared modules, resulting in gradient conflicts and negative transfer during training. To address this challenge, we first introduce gradient-based diagnostics to quantify module-level cross-category contention. Building on results of diagnostics, we propose DecomPose, a difficulty-aware decomposition framework that mitigates optimization contention via: (1) difficulty-aware gradient decoupling, which groups categories using a data-driven difficulty proxy and routes each instance to a group-specific correspondence branch to isolate incompatible updates; and (2) stability-driven asymmetric branching, which assigns higher-capacity branches to structurally simple categories as stable optimization anchors while constraining complex categories with lightweight branches to suppress noisy updates and alleviate negative transfer. Extensive experiments on REAL275, CAMERA25, and HouseCat6D demonstrate that DecomPose effectively reduces cross-category optimization contention and delivers superior pose estimation performance across multiple benchmarks.

---

## 论文详细总结（自动生成）

# DecomPose 论文总结

> 说明：可获取的 PDF 提取文本实际为 OpenReview 的浏览器验证页面，未包含论文正文。以下总结主要依据论文摘要与提供的元数据；摘要未覆盖之处会明确标注为“未说明/无法判断”。

## 1. 核心问题与整体含义
- 类别级 6D 物体位姿估计通常被建模为多类别联合学习问题，并采用完全共享的模型参数。
- 问题在于：不同类别之间存在显著几何异质性，导致共享模块中混入不相容的优化信号，产生梯度冲突和负迁移。
- 整体含义：论文试图从“跨类别优化竞争”角度解决多类别联合训练难题，而不是仅依赖网络结构改进；其目标是在多类别共享训练下提升位姿估计精度与稳定性。

## 2. 方法论
- 核心思想：提出 **DecomPose**，一个难度感知分解框架，用于缓解跨类别优化竞争。
- 关键技术细节：
  - **梯度诊断**：先使用基于梯度的诊断方法，量化模块级的跨类别竞争程度。
  - **难度感知梯度解耦**：利用数据驱动的难度代理对类别进行分组，并将每个实例路由到“组特定的对应关系分支”，以隔离不相容的更新。
  - **稳定性驱动的非对称分支**：给结构简单的类别分配更高容量分支，作为稳定优化锚点；对复杂类别使用轻量分支，以抑制噪声更新并缓解负迁移。
- 公式与算法流程：摘要未给出具体公式。可概括为“梯度诊断 → 难度代理分组 → 实例路由到组特定分支 → 非对称容量分配 → 联合优化”。

## 3. 实验设计
- 数据集：在 **REAL275、CAMERA25、HouseCat6D** 上进行实验。
- Benchmark：类别级 6D 物体位姿估计。
- 对比方法：可获取文本未列出具体基线方法名称，仅声称在多个 benchmark 上取得更优位姿估计性能。
- 评价指标：未说明，无法判断是否使用 ADD/ADD-S、IoU 或其他常用指标。

## 4. 资源与算力
- 可获取文本未提及 GPU 型号、数量、训练时长、显存消耗或总计算量。
- 因此无法总结具体算力配置，也无法评估训练成本与可复现性。

## 5. 实验数量与充分性
- 明确提到在三个数据集上进行了“extensive experiments”。
- 但未说明具体实验组数、消融实验数量、是否包含跨数据集泛化、鲁棒性实验或统计显著性分析。
- 公平性方面：若确实在标准 benchmark 上与常规基线比较，则具备一定客观性；但由于缺少对比方法清单、训练协议和超参数细节，无法验证实验是否完全公平。

## 6. 主要结论与发现
- DecomPose 能有效减少跨类别优化竞争。
- 在多个 benchmark 上取得更优的位姿估计性能。
- 为多类别 6D 位姿估计提供了可迁移的“优化解耦”思路。

## 7. 优点
- 问题切入新颖：关注多类别联合训练中的梯度冲突与负迁移，而非仅改进网络模块。
- 诊断驱动：先量化模块级跨类别竞争，再据此设计解耦策略。
- 数据驱动难度分组：避免纯手工类别划分，更具适应性。
- 非对称分支设计有针对性：简单类别用高容量分支稳定优化，复杂类别用轻量分支抑制噪声。
- 在三个常用数据集上验证，具备一定泛化性。

## 8. 不足与局限
- 全文不可得，导致方法细节、公式、实现和实验设置大量缺失。
- 实验报告不完整：未给出具体对比方法、评价指标、消融组数、统计显著性和训练协议，充分性与公平性难以判断。
- 方法超参数不明确：难度代理定义、分组数量、分支容量、路由规则、损失函数等均未说明。
- 可能引入额外分支与调参开销，训练和推理成本未知。
- 应用限制：方法依赖类别间几何异质性；若类别同质、类别数少或单类别场景，收益可能有限；对新类别、类别不平衡和开放世界的泛化能力未知。
- 未报告算力资源，影响可复现性与实际部署评估。

（完）
