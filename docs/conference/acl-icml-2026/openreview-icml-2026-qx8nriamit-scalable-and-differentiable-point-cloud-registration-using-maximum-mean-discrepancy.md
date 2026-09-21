---
title: Scalable and Differentiable Point-Cloud Registration Using Maximum Mean Discrepancy
title_zh: 基于最大均值差异的可扩展可微点云配准
authors: "Rixon Crane, Fahira Afzal Maken, Nicholas Lawrance, Stanislav Funiak, Kasra Khosoussi, Ming Xu, Russell Tsuchida"
date: 2026-04-30
pdf: "https://openreview.net/pdf/db3fbe77df278b027f742dd0b2c2c6c49deb9a02.pdf"
tags: ["query:pe"]
score: 5.0
evidence: 可微点云配准用于相对位姿
tldr: 针对点云配准在初始对齐差、部分重叠等困难条件下难以兼顾精度与可扩展性的问题，提出MMD-Reg，将配准建模为基于最大均值差异的非线性最小二乘，用随机傅里叶特征近似并借助隐函数定理实现可微。实验表明其具有线性复杂度，可在差初始对齐和部分重叠下有效配准，并能作为端到端模型中的可微优化层支撑相对位姿估计。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 点云配准在初始对齐差、部分重叠等困难条件下难以兼顾精度与可扩展性。
method: 提出MMD-Reg，基于最大均值差异的免对应配准，用随机傅里叶特征近似并可微。
result: 实验表明其具有线性复杂度，在差初始对齐和部分重叠下仍能有效配准。
conclusion: 为可微分、可扩展的点云配准提供新思路，可支撑相对位姿估计。
---

## Abstract
We present MMD-Reg, a novel correspondence-free approach to point-cloud registration that is differentiable and has linear computational complexity in the number of points. We model registration as a nonlinear least-squares problem based on the Maximum Mean Discrepancy, approximated using random Fourier features. The resulting objective can be solved efficiently with standard methods such as Levenberg–Marquardt, and the solution is differentiable via the implicit function theorem. This allows MMD-Reg to be used as a differentiable optimization layer within end-to-end trainable models, supporting registration under challenging conditions such as poor initial alignment and partial overlap. We demonstrate this Neural MMD-Reg formulation by integrating the layer with a set transformer, training the resulting model in supervised and unsupervised settings, and comparing its performance against recent learning-based methods. We also evaluate standalone MMD-Reg, comparing its accuracy and scalability against widely used non-learning-based registration methods.

---

## 论文详细总结（自动生成）

> **重要说明**：提供的 PDF 提取文本仅为 OpenReview 的浏览器验证/CAPTCHA 页面，未包含论文正文。因此以下总结主要依据论文元数据与摘要。凡摘要未明确说明的实验细节、数据集、算力、对比方法和数值结果，均标注为“未说明/无法确认”，不作臆测。

# 论文总结：基于最大均值差异的可扩展可微点云配准

## 1. 核心问题与整体含义
- **研究背景**：点云配准是 3D 视觉、机器人、SLAM、自动驾驶和相对位姿估计中的基础问题。
- **核心问题**：在**初始对齐较差、点云仅部分重叠**等困难条件下，现有方法难以同时兼顾配准精度与可扩展性。
- **整体含义**：论文提出 **MMD-Reg**，一种**免对应（correspondence-free）**、**可微**且对点数具有**线性计算复杂度**的点云配准方法，并可作为端到端模型中的可微优化层，支撑相对位姿估计。

## 2. 方法论
- **核心思想**：将点云配准建模为基于**最大均值差异（Maximum Mean Discrepancy, MMD）** 的非线性最小二乘问题，避免显式建立点对点对应关系。
- **关键技术细节**：
  - 使用**随机傅里叶特征（Random Fourier Features, RFF）** 近似 MMD，使目标函数可高效计算，并带来对点数的线性复杂度。
  - 配准目标可通过标准优化方法求解，摘要中明确提到 **Levenberg–Marquardt**。
  - 最优解通过**隐函数定理（implicit function theorem）** 实现可微，从而支持反向传播。
- **算法流程（文字版）**：
  1. 输入源点云与目标点云；
  2. 用 RFF 近似两个点云分布之间的 MMD；
  3. 构造关于位姿/变换参数的非线性最小二乘目标；
  4. 使用 Levenberg–Marquardt 等标准方法优化求解；
  5. 利用隐函数定理对最优解求导，使该配准过程可作为可微优化层；
  6. 将该层嵌入端到端模型，例如与 **set transformer** 结合形成 **Neural MMD-Reg**，并支持监督与无监督训练。

## 3. 实验设计
- **评估形式**：
  - **Neural MMD-Reg**：将 MMD-Reg 层与 set transformer 集成，在监督和无监督设置下训练，并与近期基于学习的方法比较。
  - **Standalone MMD-Reg**：单独评估 MMD-Reg，与广泛使用的非学习方法比较精度和可扩展性。
- **场景/困难条件**：摘要明确提到**差初始对齐**和**部分重叠**。
- **数据集 / Benchmark / 对比方法 / 指标**：摘要和元数据均**未说明**具体数据集名称、benchmark、评价指标以及对比方法的名称。
- **结论性数值**：摘要未给出具体精度、速度或复杂度常数结果。

## 4. 资源与算力
- 摘要与元数据中**未说明** GPU 型号、数量、训练时长、参数量或计算资源。
- 因此无法评估其训练成本和可复现性。

## 5. 实验数量与充分性
- 从摘要可推断，论文至少包含以下实验维度：
  - Neural MMD-Reg 的监督学习与无监督学习；
  - 与近期学习型方法的对比；
  - Standalone MMD-Reg 与非学习方法的精度和可扩展性对比；
  - 差初始对齐、部分重叠等困难条件评估。
- 但具体做了多少数据集、多少组实验、是否包含消融实验、统计显著性检验等，均**无法确认**。
- 由于缺少正文，**无法客观判断实验充分性与公平性**；只能确认摘要声称进行了多类对比。

## 6. 主要结论与发现
- MMD-Reg 是一种**可微、免对应**的点云配准方法。
- 其计算复杂度对点数呈**线性**，具备可扩展性。
- 在**差初始对齐**和**部分重叠**条件下仍能有效配准。
- 可作为**可微优化层**嵌入端到端模型，支持相对位姿估计。
- 摘要声称与近期学习型方法和常用非学习方法进行了比较，但未给出具体数值结论。

## 7. 优点
- **免对应配准**：避免显式对应搜索，有望减少对应错误和局部最优问题。
- **可扩展性**：基于 RFF 近似 MMD，实现线性复杂度，适合较大规模点云。
- **可微性**：通过隐函数定理使优化解可反向传播，可作为端到端模型中的优化层。
- **优化成熟**：采用 Levenberg–Marquardt 等标准非线性最小二乘方法，工程实现路径清晰。
- **适应困难条件**：面向差初始对齐和部分重叠，具有实际应用潜力。
- **训练灵活**：支持监督和无监督两种端到端训练设置。

## 8. 不足与局限
- **信息不完整**：提供的 PDF 正文缺失，无法全面验证方法、实验和结论。
- **实验细节缺失**：未说明数据集、benchmark、指标、对比方法和具体数值，难以判断是否达到 SOTA。
- **算力未报告**：未提供 GPU 型号、数量、训练时长等，影响可复现性评估。
- **消融未知**：无法判断 RFF、MMD 目标、隐函数定理可微层、set transformer 集成等组件的贡献。
- **潜在方法敏感性**：MMD 核带宽、RFF 特征数、优化初始化等超参数的影响未说明。
- **大规模表现未知**：虽然声称线性复杂度，但常数项、内存占用和超大规模点云表现未说明。
- **鲁棒性未知**：对噪声、离群点、不同部分重叠比例、对称性等情况的鲁棒性未说明。
- **应用限制**：摘要强调“差初始对齐”和“部分重叠”，但未说明是否仍需要一定初始信息，也未讨论完全无重叠或极端退化场景。

（完）
