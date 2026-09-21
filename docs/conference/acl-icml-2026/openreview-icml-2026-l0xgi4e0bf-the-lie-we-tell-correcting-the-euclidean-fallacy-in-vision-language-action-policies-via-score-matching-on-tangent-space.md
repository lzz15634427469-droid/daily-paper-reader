---
title: "The Lie We Tell: Correcting the Euclidean Fallacy in Vision Language Action Policies via Score Matching on Tangent Space"
title_zh: 我们所说的谎言：通过切空间分数匹配纠正视觉语言动作策略中的欧氏谬误
authors: "Bing-Cheng Chuang, I-Hsuan Chu, Bor-Jiun Lin, YuanFu Yang, Min Sun, Chun-Yi Lee"
date: 2026-04-30
pdf: "https://openreview.net/pdf/22509e96de59cf250907a416e0836565f4c7edcc.pdf"
tags: ["query:pe"]
score: 4.0
evidence: 在SE(3)上做切空间分数匹配的位姿表示
tldr: 该文指出扩散式视觉语言动作策略将SE(3)位姿当作平坦R^12向量表示，导致流形漂移、等变性破坏和非测地轨迹。为此提出Lie Diffuser Actor（LDA），在SE(3)上以内蕴方式注入左不变SDE噪声、在切空间预测分数并用指数映射收缩样本。方法消除了流形漂移并保持几何一致性，对机器人位姿表示有参考价值，但与航天器位姿估计仅为方法层面关联。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 扩散式VLA策略将SE(3)位姿当作平坦向量表示，造成流形漂移、等变性破坏和运动学代价过高。
method: 提出LDA框架，在SE(3)上以内蕴方式通过左不变SDE注入噪声，在切空间预测分数并用指数映射收缩样本。
result: 消除流形漂移并保持几何一致性，生成更符合测地性的动作轨迹。
conclusion: 为机器人位姿的几何一致表示提供新思路，可与位姿估计任务间接结合。
---

## Abstract
Diffusion-based Vision-Language-Action policies achieve remarkable success in robotic manipulation, yet commit a fundamental geometric error we term the **Euclidean Fallacy**: representing SE(3) poses as flat $\mathbb{R}^{12}$ vectors. This approximation induces (1) manifold drift violating SO(3) constraints, (2) broken equivariance under coordinate transformations, and (3) non-geodesic trajectories with excessive kinematic cost. We introduce **Lie Diffuser Actor (LDA)**, a diffusion framework operating intrinsically on SE(3). Our method injects noise through left-invariant SDEs, predicts scores in the tangent space, and retracts samples via the exponential map. This formulation eliminates manifold drift by construction while guaranteeing coordinate-frame equivariance and geodesic optimality. On CALVIN ABC$\rightarrow$D, LDA improves average task length from  $3.27$ to $3.51$ ($+7.3\%$). We further validate our method on real robot and the results show that our methodology outperforms the baseline on majority tasks.

---

## 论文详细总结（自动生成）

# 论文总结

> 说明：给定 PDF 提取文本实际为 OpenReview 的 CAPTCHA 验证页面，未能获取论文正文。以下总结主要依据摘要与元数据，因此涉及公式、实验细节、算力等内容可能不完整。

## 1. 核心问题与整体含义
- 论文关注扩散式视觉语言动作策略（Diffusion-based Vision-Language-Action, VLA）在机器人操作中的几何表示问题。
- 作者将现有方法把 SE(3) 位姿表示为平坦 \(\mathbb{R}^{12}\) 向量的做法称为 **Euclidean Fallacy（欧氏谬误）**。
- 这种近似带来三类问题：
  - 流形漂移，违反 SO(3) 约束；
  - 坐标变换下等变性被破坏；
  - 生成轨迹非测地，导致额外运动学代价。
- 整体含义：机器人位姿动作生成应在 SE(3) 流形上内蕴建模，而非在欧氏空间中粗暴展开。

## 2. 方法论
- 核心思想：提出 **Lie Diffuser Actor（LDA）**，一个直接在 SE(3) 上运行的扩散框架。
- 关键技术细节：
  - 通过 **左不变 SDE** 在 SE(3) 上注入噪声；
  - 在 **切空间** 中预测 score；
  - 通过 **指数映射** 将样本 retract 回 SE(3) 流形。
- 算法流程可概括为：
  - 前向过程在 Lie 群上以左不变方式加噪；
  - 去噪网络学习切空间中的 score；
  - 反向去噪时在切空间更新，再用指数映射映射回 SE(3)。
- 摘要声称该形式化可“构造性地”消除流形漂移，并保证坐标框架等变性与测地最优性。
- 可见内容未给出具体公式、网络结构、损失函数或训练算法细节。

## 3. 实验设计
- 数据集 / 场景：
  - 仿真 benchmark：**CALVIN ABC→D**；
  - 真实机器人实验。
- Benchmark 指标：
  - CALVIN ABC→D 上使用平均任务长度（average task length）；
  - 真实机器人上比较多数任务的表现。
- 对比方法：
  - 摘要仅提到与 **baseline** 对比，未说明 baseline 的具体名称或配置。
- 主要结果：
  - CALVIN ABC→D 上平均任务长度从 **3.27 提升到 3.51**，相对提升 **+7.3%**；
  - 真实机器人实验中，方法在多数任务上优于 baseline。

## 4. 资源与算力
- 摘要与元数据均未提及 GPU 型号、数量、训练时长、参数量或计算资源规模。
- 因此无法总结其算力使用情况，需要查阅论文全文确认。

## 5. 实验数量与充分性
- 从可见信息看，至少包含两类实验：
  - CALVIN ABC→D 仿真 benchmark；
  - 真实机器人验证。
- 未提及消融实验、不同数据集、不同随机种子、统计显著性检验等。
- 真实机器人部分仅表述为“多数任务优于 baseline”，未给出任务数量、指标定义和失败案例分析。
- 由于 baseline 名称、训练配置、评价协议均不明确，实验的充分性、客观性与公平性无法仅凭摘要判断。

## 6. 主要结论与发现
- 将 SE(3) 位姿当作平坦向量会引入几何错误，而 LDA 在 SE(3) 上内蕴建模可消除流形漂移。
- LDA 能保持几何一致性，并生成更符合测地性的动作轨迹。
- 在 CALVIN ABC→D 上，平均任务长度提升 **+7.3%**。
- 在真实机器人上，LDA 在多数任务中优于 baseline。
- 该工作为机器人位姿的几何一致表示提供了新思路。

## 7. 优点
- 问题定义清晰：将扩散式 VLA 中的位姿表示问题形式化为“欧氏谬误”。
- 方法具有理论吸引力：在 SE(3) 上使用左不变 SDE、切空间 score matching 和指数映射，理论上可消除流形漂移并保持等变性。
- 结合了扩散策略、Lie 群几何与切空间分数匹配，思路较新颖。
- 同时进行仿真 benchmark 和真实机器人验证，初步显示方法有效性。

## 8. 不足与局限
- 给定 PDF 正文未成功提取，无法核实公式、算法流程、网络结构和实验细节。
- 实验覆盖有限：仅提及 CALVIN ABC→D 与真实机器人，未说明其他 benchmark 或数据集。
- 缺少消融实验、随机种子、统计显著性和失败案例分析。
- baseline 具体信息不明确，难以评估对比是否公平。
- 真实机器人任务数量、评价指标、部署开销与实时性均未说明。
- 元数据指出该工作与航天器位姿估计仅为方法层面关联，直接迁移到其他位姿估计任务仍需验证。

（完）
