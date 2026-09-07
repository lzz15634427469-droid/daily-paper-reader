---
title: "ReCAP: Recursive Prompting for Self-Supervised Category-Level Articulated Pose Estimation from an Image"
title_zh: ReCAP：通过递归提示实现单目图像自监督类别级关节物体姿态估计
authors: "Linlian Jiang, Zhixiang Chi, Ye Wang, Ziqiang Wang, Rui Ma, Yang Wang, Xinxin Zuo"
date: 2025-09-15
pdf: "https://openreview.net/pdf?id=NXaw2SRUzd"
tags: ["query:pe"]
score: 5.0
evidence: 基于单张RGB图像的自监督类别级关节物体位姿估计，其方法思路适用于单目位姿估计
tldr: "关节物体位姿估计常依赖昂贵标注或RGB-D等辅助信息，单目RGB图像下仍未很好解决。ReCAP通过递归提示生成器与残差注入适配预训练基础模型，仅增加不到1%参数即可完成自监督类别级关节物体位姿估计。该方法避免稠密标注和深度几何约束，具有较强的可扩展性。其从单张图像估计物体的思路可迁移至航天器部件位姿估计场景。"
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 单目RGB图像下的关节物体位姿估计仍受限于标注成本或对深度等辅助信号的依赖，缺乏可扩展性。
method: 提出ReCAP，用递归提示生成器结合残差注入微调预训练基础模型，以极低参数开销实现单目自监督位姿估计。
result: 仅用少量额外参数即可完成自监督类别级关节位姿估计，减少了对标注与RGB-D依赖。
conclusion: 展示递归提示策略可高效泛化基础模型到新位姿任务，适用图像级物体位姿估计。
---

## Abstract
Estimating category-level articulated object poses is crucial for robotics and virtual reality. 
Prior works either rely on costly annotations, limiting scalability, or depend on auxiliary signals such as dense RGB-D sensing and geometric constraints that are rarely available in practice. 
As a result, articulated pose estimation from a single RGB image remains largely unsolved.
We propose ReCAP, a Recursive prompting for self-supervised Category-level Articulated object Pose estimation from an image. 
ReCAP adapts a pre-trained foundation model using a Recursive Prompt Generator with residual injection, introducing less than 1\% additional parameters.
This mechanism enables parameter-efficient scaling through recursive refinement, while residual injection preserves token alignment under dynamic reconfiguration, yielding robust articulated-object adaptation.
To further resolve structural ambiguities, we introduce $\mathcal{X}$-SGP, a multi-scale fusion module that adaptively integrates semantic and geometric cues, an aspect often overlooked by geometry-centric approaches. 
Experiments on synthetic and real benchmarks demonstrate state-of-the-art monocular articulated pose estimation without requiring 3D supervision or auxiliary depth input. 
To the best of our knowledge, ReCAP is the first self-supervised framework to accomplish this task from a single image.

---

## 论文详细总结（自动生成）

# 中文总结：ReCAP 论文分析

## 1. 论文的核心问题与整体含义

- **研究动机**：类别级关节物体（articulated object，如抽屉、柜门等）的位姿估计对机器人操作和虚拟现实至关重要。
- **背景痛点**：
  - 传统方法依赖昂贵的三维标注，可扩展性差；
  - 或依赖 RGB-D 深度信息与几何约束，而这些辅助信号在实际场景中很少可得；
  - 因此，仅凭单张 RGB 图像实现自监督的关节物体位姿估计仍是一个很大的挑战。
- **整体含义**：论文试图用最小的参数开销，把预训练基础模型迁移到“单目图像 → 关节物体位姿”这一任务上，并避免稠密标注和深度输入，以提升方法的可扩展性与实用性。

## 2. 论文提出的方法论

- **核心思想**：使用“递归提示生成器”（Recursive Prompt Generator）加上“残差注入”（Residual Injection）来适配预训练基础模型，仅引入不到 1% 的额外参数即可完成自监督训练。
- **模块与机制**：
  1. **递归提示生成器**：通过多次递归迭代逐步精炼提示参数，让模型以参数高效的方式在任务上进行渐进式优化。
  2. **残差注入**：在模型动态重配置（递归中改变结构或提示）时，通过残差连接保持 token 的语义对齐，从而保证适配过程稳定。
  3. **X-SGP 多尺度融合模块**：自适应整合语义特征与几何特征，用于解决关节物体的结构歧义；论文指出此前以几何为中心的方法多忽略语义与几何的融合。
- **算法流程（文字描述）**：
  1. 输入单张 RGB 图像，提取图像特征；
  2. 初始化提示参数，送入基础模型；
  3. 递归迭代：每轮生成新提示，并通过残差注入更新模型行为；
  4. 在 X-SGP 中融合多尺度语义与几何线索，输出类别级关节位姿估计；
  5. 在无 3D 监督、无深度输入的条件下，通过自监督信号进行训练。

## 3. 实验设计

- **Benchmark**：
  - 使用了**合成基准**与**真实基准**进行评测（论文摘要中明确提到 synthetic and real benchmarks）。
  - 具体数据集名称（如 Articulated Object Dataset、PartNet-Mobility 等）在可获取的文本中未具体列出。
- **对比方法**：
  - 与方法相关的对比对象包括：依赖稠密标注的监督方法、依赖 RGB-D/几何约束的方法，以及可适配基础模型的其他提示/微调策略。
  - 结论声称达到目前单目关节位姿估计的最优水平（state-of-the-art）。
- **评测目标**：在无 3D 监督、无辅助深度输入条件下验证单目 RGB 关节物体位姿估计的效果。

## 4. 资源与算力

- 论文文本中**未明确说明**训练使用的 GPU 型号、数量、训练时长、参数量级等具体算力信息。
- 唯一可量化指标是“额外参数 < 1%”，但未给出基础模型本身的参数量或实际运行开销。
- 因此，无法从当前内容中评估该方法的计算资源需求和训练成本。

## 5. 实验数量与充分性

- **已提及的实验**：
  - 合成数据集上的评测；
  - 真实数据集上的评测；
  - 对比实验（相对既有方法）；
  - 并声称达到 SOTA 效果。
- **缺席描述**：
  - 未给出具体的消融实验数量（如递归轮数、X-SGP 有无、不同基础模型选择等）；
  - 未给出每项实验的量化结果（误差指标、与基线的差距等）；
  - 实验的详细设置、实现细节、数据划分均未在本提取文本中呈现。
- **总体判断**：从摘要看，实验覆盖了合成与真实场景，方向合理；但可获取信息不足，无法判断其消融是否全面、统计是否显著、对比设置是否完全公平。需要阅读全文才能评估其充分性。

## 6. 论文的主要结论与发现

- **核心结论**：仅仅通过不到 1% 的参数开销，递归提示 + 残差注入即可有效将预训练基础模型迁移到单目关节物体位姿估计任务。
- **关键技术发现**：
  - 递归提示能带来参数高效的扩展与跨任务泛化；
  - 残差注入能解决动态重配置下的 token 对齐问题；
  - 语义-几何多尺度融合（X-SGP）能克服单纯几何方法的歧义。
- **任务成果**：论文声称是**第一个不依赖 3D 监督或辅助深度输入**、单张 RGB 图像下完成自监督类别级关节物体位姿估计的框架。

## 7. 优点

- **任务创新性强**：目标设定为“单 RGB 图像 + 自监督 + 类别级关节物体位姿”，难度高且有应用价值。
- **参数高效**：仅 <1% 额外参数，有利于在边缘设备或算力受限场景应用。
- **方法论组合巧妙**：递归提示与残差注入结合控制基础模型的适配，比全微调更经济；X-SGP 模块兼顾语义与几何，弥补几何中心路线的不足。
- **数据依赖低**：不依赖稠密标注与 RGB-D 深度，降低数据采集成本，提升可扩展性。
- **评估覆盖双路径**：合成与真实基准双验证，增强了一定说服力。

## 8. 不足与局限

- **实验细节缺失**：具体数据集、指标、结果数值、对比方法版本等均未在可获取文本中出现，难以进行独立复现或深入评价。
- **算力/效率分析缺失**：未报告训练时长、显存消耗、推理速度等，虽参数少，但实际运行成本未知。
- **自监督的信号设计未展开**：摘要未说明自监督损失或伪标签从何而来，这往往是该类方法成败的关键。
- **应用范围限制**：实验主要面向关节物体，对更广的物体类别或极端外观/遮挡场景的泛化未说明。
- **风险与偏差**：若自监督依赖类别先验或合成数据，则存在域偏移风险；真实场景表现可能有偏差。
- **论文状态**：该文被 ICLR-2026 拒绝（来源显示 Rejected），需谨慎对待其宣称的 SOTA，应结合审稿意见与公开代码进一步验证。

（完）
