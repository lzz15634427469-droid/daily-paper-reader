---
title: "Rays as Pixels: Learning A Joint Distribution of Video and Camera Trajectories"
title_zh: 射线即像素：学习视频与相机轨迹的联合分布
authors: "Wonbong Jang, Shikun Liu, Soubhik Sanyal, Juan Camilo Perez, Kam Woh Ng, Sanskar Agrawal, Juan-Manuel Perez-Rua, Yiannis Douratsos, Tao Xiang"
date: 2026-04-30
pdf: "https://openreview.net/pdf/c0a4677a69a2b0522f6d321e1f3ee53bad83072c.pdf"
tags: ["query:pe"]
score: 4.0
evidence: 通过视频-轨迹联合分布从图像恢复相机参数与位姿
tldr: 论文针对从图像恢复相机参数与从新视角渲染场景这两个正逆问题长期割裂、在图像覆盖稀疏或相机位姿模糊时失效的问题，提出Rays as Pixels视频扩散模型，将相机表示为稠密射线像素并与视频帧联合去噪，采用解耦自交叉注意力实现联合建模。实验表明该联合框架在稀疏覆盖与位姿模糊情形下改善了相机位姿恢复与视角合成效果。其从图像估计相机位姿的思路可迁移至视觉位姿估计任务。
source: ICML-2026-Accepted
selection_source: conference_retrieval
motivation: 从图像恢复相机参数与从新视角渲染场景长期被割裂处理，在图像覆盖稀疏或相机位姿模糊时容易失败。
method: 提出Rays as Pixels视频扩散模型，将相机表示为稠密射线像素，与视频帧一同去噪，并用解耦自交叉注意力实现联合建模。
result: 实验表明该联合建模在稀疏覆盖与位姿模糊条件下提升了相机位姿恢复与视角渲染效果。
conclusion: 统一了相机位姿感知与场景渲染两类问题，为基于图像的位姿估计提供了可迁移思路。
---

## Abstract
Can we bridge the gap between perceiving camera trajectories and rendering novel views within a single generative framework? Recovering camera parameters from images and rendering scenes from novel viewpoints are considered the forward and inverse problems in the field of computer vision and graphics. Previous approaches treat these problems in isolation, often failing when image coverage is sparse or camera poses are ambiguous. In this work, we propose Rays as Pixels, a specialized Video Diffusion Model (VDM) that learns a joint distribution of videos and camera trajectories. We represent cameras as dense ray pixels (raxels) and simultaneously denoise them alongside video frames using a novel Decoupled Self-Cross Attention. This joint formulation enables us to: i) generate a video from multiple input images following a defined camera trajectory, ii) perform novel view synthesis from sparse views (without necessarily requiring camera poses), and iii) predict the camera trajectory from a raw video. We evaluate our model on pose estimation, camera-controlled video generation and validate its self-consistency. Please reference supplementary material for more qualitative results.

---

## 论文详细总结（自动生成）

# 论文总结：Rays as Pixels: Learning A Joint Distribution of Video and Camera Trajectories

> 说明：当前可获取的 PDF 文本仅为 OpenReview 的 CAPTCHA 验证页面，并非论文正文；以下总结主要依据论文摘要与提供的元数据。因此，涉及数据集、算力、实验数量、对比方法等细节，凡摘要未明确说明者，均只能标注为“未提供/无法确认”，不能视为论文实际缺失。

## 1. 核心问题与整体含义

- 论文关注计算机视觉与图形学中长期被割裂处理的两个正逆问题：
  - **从图像恢复相机参数/相机轨迹**：即相机位姿感知问题。
  - **从新视角渲染场景**：即新视角合成问题。
- 现有方法通常将二者分开处理，导致在以下情形中容易失败：
  - 输入图像覆盖稀疏；
  - 相机位姿模糊或不确定。
- 论文的整体含义是：尝试用**单一生成式框架**同时建模视频与相机轨迹，从而桥接“感知相机轨迹”与“渲染新视角”之间的鸿沟。
- 元数据进一步指出，该工作希望从图像估计相机位姿的思路迁移到视觉位姿估计任务中。

## 2. 方法论

- **核心思想**：
  - 提出名为 **Rays as Pixels** 的专用视频扩散模型（Video Diffusion Model, VDM）。
  - 学习**视频与相机轨迹的联合分布**，而不是分别建模视频生成和相机估计。
- **关键表示**：
  - 将相机表示为**稠密射线像素**，论文中称为 **raxels**。
  - 相机轨迹不再仅以低维参数表示，而是以类似像素/射线的稠密形式参与生成建模。
- **关键技术细节**：
  - 在扩散去噪过程中，**视频帧与相机射线像素被同时去噪**。
  - 使用一种新的 **Decoupled Self-Cross Attention**（解耦自交叉注意力）实现联合建模。
    - 该机制意图在视频表示与相机射线表示之间建立交互；
    - 同时保持二者各自的结构与建模特性。
- **算法流程概述**：
  - 输入可为多张图像或原始视频；
  - 模型在联合扩散框架中对视频帧和 raxels 进行迭代去噪；
  - 最终可得到视频内容与相机轨迹的联合结果。
- **公式与伪代码**：
  - 当前提供的摘要与元数据未给出具体公式、损失函数或算法伪代码，无法进一步展开。

## 3. 实验设计

- **评估任务**：
  - 摘要明确提到在三类任务上评估：
    1. **位姿估计**（pose estimation）；
    2. **相机控制视频生成**（camera-controlled video generation）；
    3. **自一致性验证**（self-consistency）。
- **模型能力展示**：
  - 从多张输入图像按指定相机轨迹生成视频；
  - 从稀疏视角进行新视角合成，且不必然要求相机位姿；
  - 从原始视频预测相机轨迹。
- **数据集 / 场景**：
  - 摘要未列出具体数据集、场景类型或数据规模。
- **Benchmark 与对比方法**：
  - 摘要未说明使用何种 benchmark；
  - 未列出对比方法、基线模型或评价指标。
- **元数据补充**：
  - 元数据称实验表明，在稀疏覆盖与位姿模糊条件下，该联合框架改善了相机位姿恢复与视角合成效果。

## 4. 资源与算力

- 当前可获取文本**未提及**以下信息：
  - GPU 型号；
  - GPU 数量；
  - 训练时长；
  - 参数量、训练步数、batch size 等算力相关细节。
- 因此，无法判断该工作的实际计算开销与可复现成本。

## 5. 实验数量与充分性

- 从摘要可知，论文至少围绕三类任务进行了评估：
  - 位姿估计；
  - 相机控制视频生成；
  - 自一致性验证。
- 但当前文本未说明：
  - 使用了多少个数据集；
  - 做了多少组消融实验；
  - 是否包含跨数据集泛化实验；
  - 是否与多种基线方法公平比较；
  - 定量指标与统计显著性如何。
- 因此，**无法评估实验数量是否充分、设计是否客观公平**。
- 摘要提到补充材料中有更多定性结果，但当前未提供补充材料内容。

## 6. 主要结论与发现

- 通过联合建模视频与相机轨迹，可以统一处理：
  - 相机位姿感知；
  - 新视角合成；
  - 相机控制视频生成；
  - 从视频预测相机轨迹。
- 在图像覆盖稀疏或相机位姿模糊时，联合框架相比孤立处理方式表现更好。
- 模型具备一定的自一致性，即视频生成与相机轨迹建模之间能够相互验证。
- 整体上，该工作为基于图像的位姿估计与场景渲染提供了一种可迁移的统一生成式思路。

## 7. 优点

- **统一框架**：将计算机视觉与图形学中的正逆问题放入同一扩散模型中建模。
- **表示创新**：用稠密射线像素（raxels）表示相机，使相机轨迹可与视频帧在同一像素/射线空间中联合去噪。
- **注意力机制设计**：提出 Decoupled Self-Cross Attention，兼顾视频与相机表示的交互与解耦。
- **多任务能力**：同一模型支持视频生成、新视角合成、相机轨迹预测等多种任务。
- **稀疏与模糊场景潜力**：针对传统方法容易失败的稀疏覆盖和位姿模糊情形，提供了联合建模的解决思路。
- **可迁移性**：从图像估计相机位姿的机制可被迁移至视觉位姿估计相关任务。

## 8. 不足与局限

- **全文信息不足**：当前仅能获取摘要和元数据，无法验证方法细节、实验设置与结论强度。
- **实验细节缺失**：
  - 未提供数据集、benchmark、对比方法和评价指标；
  - 无法判断实验是否充分、公平、可复现。
- **算力与效率未知**：
  - 未说明训练资源与推理成本；
  - 扩散模型通常可能带来较高计算开销，但论文未在可获取文本中讨论。
- **应用限制未展开**：
  - 对动态场景、长视频、极端稀疏视角、相机模型假设、域外泛化等问题的表现尚不明确。
- **潜在偏差风险**：
  - 若评估主要依赖特定合成数据或有限场景，结论的外推性需要谨慎看待；
  - 位姿模糊的定义、度量方式与失败边界在摘要中未说明。

（完）
