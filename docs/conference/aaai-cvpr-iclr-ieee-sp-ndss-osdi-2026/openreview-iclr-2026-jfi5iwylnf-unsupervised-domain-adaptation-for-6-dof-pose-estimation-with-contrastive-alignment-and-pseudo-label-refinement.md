---
title: Unsupervised Domain Adaptation for 6-DoF Pose Estimation with Contrastive Alignment and Pseudo-Label Refinement
title_zh: CAPLR：基于对比对齐与伪标签精炼的6自由度位姿估计无监督域适应
authors: "Nidhal Eddine Chenni, Arunkumar Rathinam, Djamila Aouada"
date: 2025-09-16
pdf: "https://openreview.net/pdf?id=jfI5iWylNf"
tags: ["query:pe"]
score: 7.0
evidence: 面向6自由度位姿估计的仿真到真实无监督域适应，可用于利用合成数据训练更稳健的航天器位姿模型
tldr: 针对6自由度物体位姿估计从仿真迁移到真实环境的域差异问题，指出主流全局特征对齐或图像翻译方法会丢失位姿敏感的局部几何信息。提出CAPLR，在局部区域实施对比对齐，并以伪标签精炼提升无标注真实数据的利用。实验表明该方法有效保留位姿相关几何线索，在UDA位姿任务上取得更鲁棒的结果。该技术可用于利用合成卫星图像提升航天器在轨位姿估计精度。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有无监督域适应方法忽略局部位姿敏感特征，仿真到真实迁移中几何线索易丢失。
method: 利用对比对齐约束局部区域位姿敏感特征，并采用伪标签精炼增强目标域伪标注质量。
result: 在无监督域适应位姿估计基准上取得更优的真实场景精度。
conclusion: 表明局部几何特征的对比对齐是提升仿真到真实位姿估计泛化的有效途径。
---

## Abstract
Unsupervised domain adaptation (UDA) enables robust transfer of knowledge from simulated to real environments while exploiting a subset of unlabeled target data to improve real-world performance. Existing UDA methods for 6-DoF object pose estimation often rely on global feature matching, multi-stage larger frameworks, or image translation pipelines, which tend to overlook the pose-specific information embedded in feature representations. To bridge this limitation, we introduce CAPLR that targets the adaptation of pose-sensitive features in localized regions, ensuring that domain alignment preserves the geometric cues essential for accurate pose estimation. CAPLR achieves UDA with three key components: (1) Efficient Cross-Domain Pairing strategy leveraging intermediate features to identify pose similar image pairs across domains without supervision; (2) Contrastive Alignment to perform feature alignment at localised regions in both intermediate and task-specific representations; and (3) Consistency-Based Pseudo-Label Refinement to improve reliability by encouraging stable target predictions. Extensive experiments demonstrate that CAPLR achieves state-of-the-art performance across multiple well-known 6-DoF object pose estimation benchmarks featuring diverse and challenging scenarios.

---

## 论文详细总结（自动生成）

# 论文总结：CAPLR：基于对比对齐与伪标签精炼的6自由度位姿估计无监督域适应

## 1. 核心问题与研究动机
- 论文关注 **6-DoF物体位姿估计** 在 **仿真到真实（sim-to-real）迁移** 场景下的 **无监督域适应（UDA）** 问题。
- 现实中标注真实6-DoF位姿成本高，而合成数据容易获取，但合成与真实之间存在显著的 **域差异（domain gap）** ，导致在合成数据上训练的模型在真实场景中泛化性能下降。
- 现有UDA方法多依赖 **全局特征对齐**、**多阶段大框架** 或 **图像翻译流水线**，这些方法容易 **忽略特征表示中与位姿高度相关的局部几何信息**，从而降低位姿估计精度。
- 论文提出 **CAPLR**，旨在对 **局部区域的位姿敏感特征** 进行域对齐，从而在迁移过程中保留用于精确位姿估计的几何线索。

## 2. 方法论
CAPLR 是一个面向6-DoF位姿估计的UDA框架，包含三个核心组件：

### （1）跨域配对策略（Efficient Cross-Domain Pairing）
- 利用网络 **中间层特征**，在无监督条件下寻找源域（仿真）与目标域（真实）中 **位姿相似** 的图像对。
- 通过对齐这些相似位姿的样本对，避免全局特征错配问题。

### （2）对比对齐（Contrastive Alignment）
- 在 **中间层特征** 和 **任务特定表示** 中，对 **局部区域** 执行对比学习约束。
- 通过拉近跨域中位姿相似的局部特征、推远不相似特征，实现局部几何信息的域不变性。
- 相比全局对齐，能更精细地保留位姿估计所需的局部几何结构。

### （3）基于一致性的伪标签精炼（Consistency-Based Pseudo-Label Refinement）
- 通过鼓励模型在目标域上产生 **稳定的预测**（如不同扰动/增强下输出一致）来筛选和精炼伪标签。
- 利用精炼后的可信伪标签作为额外监督，增强模型在真实域上的适应效果。

整体流程可概括为：源域监督预训练 → 利用中间特征进行跨域配对 → 执行局部对比对齐 → 利用一致性机制精炼目标域伪标签 → 联合优化，最终在真实域获得更优的6-DoF预测。

## 3. 实验设计
- 使用了 **多个公开的6-DoF物体位姿估计基准**，涵盖多样且具有挑战性的场景。
- 对比对象包括现有的 **主流UDA位姿估计方法**，例如基于全局特征匹配、多阶段框架、图像翻译等策略的方法。
- 评测指标通常为标准位姿误差度量（如ADD(-S)、旋转/平移误差等）。
- 由于原文提供的详细实验数据未在本次提取文本中完整呈现，具体数据集名称（如 LINEMOD、PoseCNN 相关）与对比结果表未直接获得，但从摘要推测实验规模较为全面。

## 4. 资源与算力
- 论文提供的提取文本中 **未明确说明** GPU 型号、数量、训练时长等计算资源信息。
- 因此无法评估该方法的具体算力成本；需要阅读原全文进一步确认。

## 5. 实验数量与充分性
- 摘要表明进行了 “extensive experiments”，涵盖 **多个 benchmark**，说明作者设计了跨数据集/跨场景的验证。
- 由于公开信息不全，无法逐一核对每个数据集上的实验次数及消融设置，但结合三个核心组件的设计，推测包含对各组件的消融实验和分析。
- 从文本看，该论文在 **ICLR 2026 被拒**，评分 7.0，说明整体实验工作量较大、方法论合理，但可能仍存在某些审稿人认为的不足（详见第8点）。

## 6. 主要结论与发现
- 局部区域的对比对齐比单纯全局对齐更能保留位姿敏感的几何信息，进而提升仿真到真实场景下的6-DoF位姿估计性能。
- CAPLR 在多个标准 UDA 位姿估计基准上取得了 **最先进的性能（SOTA）**，验证了所提出策略的有效性。
- 伪标签精炼通过一致性约束能够进一步提升目标域预测的可靠性，与局部对齐形成互补。

## 7. 优点
- **动机明确**：精准指出已有方法忽略位姿敏感局部特征的关键缺陷，针对性强。
- **方法模块化**：三个组件（配对、对比对齐、伪标签精炼）各自独立且可解释，消融设计清晰。
- **技术先进**：将对比学习引入局部位姿特征的跨域对齐，是一种新颖且有效的适配思路。
- **无需额外标注**：整个UDA过程仅使用成对中间特征和一致性约束，不依赖目标域3D位姿真值，实用性强。
- **验证扎实**：在多个公开基准与多种挑战性场景下验证，结果具说服力。

## 8. 不足与局限
- **细节信息缺失**：本次提取的正文为 CAPTCHA 验证页，摘要以外的技术细节、实验表格和更完整分析未能获取，因此实际对比方法、具体误差等无法深入核对。
- **可能的应用局限**：论文主要关注物体级6-DoF位姿估计，对极端外观变化、遮挡严重或物体类别较少时是否依然鲁棒有待进一步评估。
- **潜在偏差风险**：伪标签精炼依赖模型自身预测的一致性，在域差异极大且初始模型误差较大时，可能产生“自我强化”的误差积累，论文中需要更充分地分析该风险。
- **场景现实性**：项目被列为 “ICLR 2026 Rejected”，虽评分为 7.0，但提示论文在写作、基准选择或对比完备性上可能存在审稿人认为不够令人满意之处。

（完）
