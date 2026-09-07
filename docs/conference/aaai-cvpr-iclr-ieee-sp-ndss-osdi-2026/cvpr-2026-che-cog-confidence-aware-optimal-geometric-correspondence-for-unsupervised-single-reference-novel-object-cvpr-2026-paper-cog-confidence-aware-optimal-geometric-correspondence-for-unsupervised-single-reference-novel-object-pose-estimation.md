---
title: "COG: Confidence-aware Optimal Geometric Correspondence for Unsupervised Single-reference Novel Object Pose Estimation"
title_zh: COG：用于无监督单参考新型物体位姿估计的置信度感知最优几何对应
authors: "Che, Yuchen, Wu, Jingtu, Zheng, Hao, Kanezaki, Asako"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Che_COG_Confidence-aware_Optimal_Geometric_Correspondence_for_Unsupervised_Single-reference_Novel_Object_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 8.0
evidence: 基于置信度感知最优输运的单参考新型物体6D位姿估计；为遮挡条件下非合作航天器提供鲁棒匹配方法。
tldr: 单参考图像下的新型物体6D位姿估计常受遮挡、视角变化和离群点影响，而离散一对一匹配不可微且易坍塌到稀疏关键点。COG提出置信度感知的最优输运框架，将逐点置信度作为边际约束以生成平衡软对应关系，抑制非重叠区域，并利用语义先验进行引导。该无监督框架无需对每个参考图像重新优化参数，提升了泛化能力与计算效率。实验表明其在单参考物体位姿估计中对抗遮挡和离群点具有更强的鲁棒性，可为非合作航天器等弱纹理目标的位姿估计提供强对应范式。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1808, \"height\": 614, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1819, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1810, \"height\": 519, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1817, \"height\": 411, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 865, \"height\": 417, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 205, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1789, \"height\": 651, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 544, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-che-cog-confidence-aware-optimal-geometric-correspondence-for-unsupervised-single-reference-novel-object-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 309, \"label\": \"Table\"}]"
motivation: 单参考新型物体6D位姿估计容易受遮挡、视角变化和离群点影响，离散对应匹配不可微且易塌缩。
method: 提出将对应估计建模为置信度感知的最优输运问题，以逐点置信度约束生成平衡软对应并抑制非重叠区域。
result: 实验显示在遮挡和离群点存在时对应更鲁棒，单参考6D位姿估计精度显著提升。
conclusion: 置信度感知的最优输运为鲁棒几何对应提供了通用框架，可服务于非合作航天器的位姿估计。
---

## Abstract
Estimating the 6DoF pose of a novel object with a single reference view is challenging due to occlusions, view-point changes, and outliers. A core difficulty lies in finding robust cross-view correspondences, as existing methods often rely on discrete one-to-one matching that is non-differentiable and tends to collapse onto sparse keypoints. We propose Confidence-aware Optimal Geometric Correspondence (COG), an unsupervised framework that formulates correspondence estimation as a confidence-aware optimal transport problem. COG produces balanced soft correspondences by predicting point-wise confidences and injecting them as optimal transport marginals, suppressing non-overlapping regions. Semantic priors from vision foundation models further regularize the correspondences, leading to stable pose estimation. This design integrates confidence into the correspondence finding and pose estimation pipeline, enabling unsupervised learning. Experiments show unsupervised COG achieves comparable performance to supervised methods, and supervised COG outperforms them. Codes: https://github.com/YC-Che/COG

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- 论文关注**新型物体（novel object）6DoF 位姿估计**任务，即估计训练阶段从未见过的物体的旋转 R 与平移 t。
- 与传统方法不同，本文瞄准**更具挑战性的单参考图像（single-reference）设置**：仅给定一张参考 RGB-D 图像和一张查询图像，适合实际部署中无法获得 CAD 模型或多视角参考图的场景。
- 该设置面临三大核心困难：(1) 大视角变化导致两视角可见区域不一致；(2) 遮挡引入大量离群点/非重叠点；(3) 深度与外观的几何对应关系难以在全监督条件下稳定学习。
- 现有方法（如 UnoPose）通常使用 **离散一一匹配（argmax）** 来构建跨视角对应，存在两个严重缺陷：
  - **非可微** → 无法进行无监督端到端训练；
  - **易坍缩** → 对应关系集中在少数主导关键点上，大量有效点被浪费。
- 针对这些问题，论文提出 **COG（Confidence-aware Optimal Geometric Correspondence）**，一种将对应关系查找建模为**置信度感知的最优输运（Optimal Transport, OT）问题**的无监督框架：
  - 预测逐点置信度，并将其显式作为 OT 的**目标边际（marginals）**，从而抑制非重叠区域和外点，产生全局平衡的软对应；
  - 引入 DINO 等视觉基础模型的语义先验来约束对应关系，缓解纯几何匹配的歧义；
  - 将置信度、对应关系与位姿估计集成在**端到端可微的流水线**中，使无监督学习成为可能。
- **整体意义**：COG 在不使用 CAD 模型、真值位姿或重叠标签的条件下，取得了接近甚至超越有监督方法的性能，为通用、可扩展的无监督物体位姿估计提供了新方向。

## 2. 方法论：核心思想、关键技术细节、公式与算法流程

### 2.1 核心思想

- 将**点云配准/对应查找**视为一个最优输运问题，以**预测的逐点置信度**作为非均匀目标边际，以几何与语义特征相似度构成**亲和核**，利用 Sinkhorn 算法求解输运计划，再基于软对应矩阵通过加权 SVD 恢复刚体变换。
- 无监督训练信号由几何重建质量、位姿对齐质量和语义一致性的高斯 RBF 核**自行生成伪置信度标签**，形成闭环。

### 2.2 预处理流水线（Pipeline）

- 使用 CNOS 风格的 UnoSeg 分割模型获得对象掩膜。
- 将掩膜深度图反投影为 3D 点云 P、Q（各 n 点）。
- 使用 DINO 提取 per-pixel RGB 特征并上采样，作为逐点外观描述子 Fp、Fq。
- 该预处理的输入为 RGB-D 双模态，图为 Query 和 Reference。

### 2.3 COG 模型结构（粗到细架构）

- **粗阶段**：用最远点采样（FPS）将点云降至 256 点，输入几何 Transformer，得到粗位姿。
- **细阶段**：用完整 1024 点云及粗位姿对齐结果，加入位置嵌入模块，优化最终位姿。
- 每阶段包含：
  - SE(3) 不变几何特征编码器；
  - 语义去噪模块（基于 STEGO 的自标签精炼策略，将 DINO 特征投影为低维语义嵌入 S）；
  - 自注意力+交叉注意力几何解码器，输出逐点几何特征 G 与置信度 c。

### 2.4 置信度感知的最优输运（核心公式）

**置信度归一化边际：**
\[
w_p = \frac{c_p}{\bar{c}_p},\quad w_q = \frac{c_q}{\bar{c}_q}
\]
确保 \(\sum_i w_p[i] = \sum_j w_q[j] = n\)，保持全局平衡。

**亲和核：**
\[
K[i,j] = \exp\left( \frac{1}{\tau}\langle G_p[i], G_q[j]\rangle_{\cos} \left( 1 + \langle S_p[i],S_q[j]\rangle_{\cos} \right)^{\lambda/\tau} \right)
\]
其中 \(\tau\) 为温度、\(\lambda\) 为语义先验权重。

**Sinkhorn 求解：**
\[
\Pi = \mathcal{S}(K, w_p, w_q)
\]
满足行和≈wp、列和≈wq。传输计划经行归一化得到行随机对应矩阵 \(M_{pq}\) 和 \(M_{qp}\)。

### 2.5 位姿估计

- 基于软对应矩阵构造凸组合对应点 \(M_{pq}Q\) 与 \(M_{qp}P\)。
- 拼接两侧原始点云与对应点云，使用加权 Umeyama 算法（加权 SVD）求解位姿：
\[
(\hat{R}_{pq},\hat{t}_{pq}) = U\big([P | M_{qp}P],\ [M_{pq}Q | Q],\ [w_p|w_q]\big)
\]

### 2.6 损失函数（无监督训练）

| 损失 | 作用 | 形式 |
|------|------|------|
| \(L_{\rm cycl}\) | 循环一致性 | 点投影到对侧再返回应能重建自身位置，Gaussian RBF 度量几何相似度 |
| \(L_{\rm pose}\) | 位姿对齐 | 加权 Chamfer 距离的 Gaussian RBF 核形式 |
| \(L_{\rm sem}\) | 语义一致 | 惩罚对应到语义差异大的点的匹配 |
| \(L_{\rm conf}\) | 置信度学习 | 将三类核响应的乘积作为伪标签，用 BCE 损失监督，梯度 detached |

### 2.7 无监督置信度学习机制

- 伪标签由三个高斯 RBF 核相乘构成：\(\phi_{\rm tot} = \phi_{\rm cycl}\cdot\phi_{\rm pose}\cdot\phi_{\rm sem}\)，即**几何重建、位姿对齐、语义一致性共同决定每点的可信度**。
- 该方法提供**渐进的软标签**（而非二值内点/外点信号），引导网络压低不确定点的权重而非完全丢弃，实现可解释、可训练的置信度预测。

## 3. 实验设计

### 3.1 数据集

| 用途 | 数据集 | 规模/内容 |
|------|--------|----------|
| 训练 | Google Scanned Objects + ShapeNet | ~2,000,000 张 RGB-D 图像、50,000+ 物体 |
| 评测 | BOP 基准：TUD-L | 600 张图像、3 个几何复杂物体 |
| 评测 | LM-O | 200 张图像、8 个物体、杂乱桌面 |
| 评测 | YCB-V | 900 张图像、21 个家庭物品、重度遮挡 |

### 3.2 对比方法

- **无监督方法**：Robust OT、Dustbin OT、FreeZe
- **有监督方法**：RPM-Net、FCGF+MAC/RANSAC、GeDi、SAM-6D、UnoPose
- **传统方法**：PPF、FPFH+RANSAC、PPF+ICP 等
- 评测指标：BOP 协议下的 **mAP**（VSD、MSSD、MSPD 三种误差度量）
- 实现了与 UnoPose 相同的骨干网络，保证公平对比

### 3.3 主要实验

| 实验 | 内容 | 结论 |
|------|------|------|
| 主实验（表 1） | 三个 BOP benchmark 上的位姿精度对比 | 无监督 COG 均优于所有无监督方法和多数有监督方法 |
| 重叠区域预测（表 2） | TUD-L 上 IoU 对比 | 无监督 COG 超过有监督 UnoPose 均值（72.3% vs 67.1%） |
| 模块消融（表 3） | 4 种对应策略 × 2 种损失组合 | 置信度边际 OT + 双损失的组合最优 |
| OT 参数消融（表 4) | Sinkhorn 迭代次数 × 语义先验有无 | 语义先验显著提升 mAP、使对应更聚焦 |
| 迭代精化分析（图 6） | 迭代次数 vs 推理时间 | 1 次迭代平衡性能与开销 |
| 定性可视化（图 4、5） | 位姿预测与置信度可视化 | 置信度对遮挡/外点区域能做出合理解释 |

## 4. 资源与算力

- 论文中**未明确说明训练所用 GPU 数量、型号或总训练时长**（逐字阅读原文确认无此信息）。
- 可推断的部分：训练使用 ADAM 优化器，初始学习率 1e-4，**3 个 epoch**，batch size 32；推理时间评估在单张 NVIDIA RTX 3090 上完成。
- COG 平均推理时间为 4.0 秒（含分割与 DINO 特征提取），与 UnoPose 相当。
- 无论文的 FLOPS、参数量或显存占用统计。

## 5. 实验数量与充分性

### 实验充分性评价

- **数量较多且结构完整**：包含 3 个 BOP 标准 benchmark 的主评测、重叠预测评估、对应策略消融（4 种）、损失组合消融（16 种组合）、OT 参数消融、迭代精化实验，以及定性可视化。
- **系统消融设计合理**：将 argmax、softmax、均匀边际 OT、置信度边际 OT 四层递进的对应策略逐一对比，验证了每个设计选择的有效性。
- **公平性较好**：与直接基线 UnoPose 使用相同分割掩膜、相同查询-参考配对和相同骨干网络；OT 基线在相同骨干上重实现。
- **局限性**：
  - 消融实验只在 **YCB-V 单一 benchmark** 上验证（表 3、4），没有跨 TUD-L/LM-O 交叉验证；
  - TUD-L 的重叠 IoU 只测了 3 个物体，样本量偏小
  - 没有与最新单参考方法的在更多场景（如真实机器人抓取）下的比较；
  - 无参数量对比或训练成本对比。

## 6. 主要结论与发现

- **置信度作为 OT 边际有效**：相比均匀边际 OT，置信度感知的边际约束显著提升了位姿精度，因为其抑制了非重叠点的输运、避免对应过度集中于少数关键点。
- **无监督 COG 性能可比有监督方法**：总体 mAP 与 SOTA 有监督方法 UnoPose 的差距仅 2.1%（68.8 vs 70.9），在物体形状较复杂的 TUD-L 上甚至超过了 UnoPose 的有监督版本（73.8 vs 71.0）。
- **语义先验能聚焦对应**：将 DINO 特征经 STEGO 式去噪后与几何核结合，对应关系流更紧凑（ENT 降低），mAP 明显提升。
- **伪标签置信度学习具备可解释性**：在遮挡、视点差异下，模型能学会对不可靠点给出低置信度，无需任何重叠率标签。
- **有监督版 COG 达到 SOTA**：在三个基准上的平均 mAP 为 73.8，验证了该框架不仅适合无监督，也适合有监督训练迁移。

## 7. 优点

1. **创新性强**：首次将**置信度作为 OT 边际而非后验过滤**纳入位姿估计框架，从方法论上克服了先前 OT 配准方法（如 Robust OT、Dustbin OT）"先对应后加权" 的局部性缺陷，实现了置信度与相应的联合端到端优化。
2. **无监督且完整**：无需任何真值（无 CAD、无位姿、无重叠率标签），能从自身几何-语义一致性中产生伪标签，降低了对人工标注的依赖。
3. **可微和全局最优视角**：Sinkhorn + 软对应 + 加权 SVD 全链路可微，为端到端无监督训练奠定基础。
4. **语义+几何融合机制设计优雅**：DINO 语义先验以核的乘性因子形式嵌入亲和矩阵，辅以独立语义一致性损失，实现几何与语义的柔性平衡。
5. **消融实验清晰**：对对应求解方式（argmax → softmax → 均匀 OT → 置信度 OT）的递进对比有力地支撑了论文主张。
6. **推理高效**：与 UnoPose 耗时相当（4.0s vs 3.7s）但精度更高；迭代精化能灵活进行精度-速度权衡。

## 8. 不足与局限

- **未报告算力消耗**：论文未给出训练硬件（GPU 型号、数量）和训练总时长，使其实际部署门槛难以评估，也降低了可复现性评价的能力。
- **训练-评测分布差异**：在大规模合成数据（GSO/ShapeNet 组成）上训练后在真实场景（LINEMOD/YCB-V）评测，存在域差距风险，但论文未分析是否需要域适应。
- **在最难遮挡的子集性能仍有明显差距**：虽然整体 mAP 已接近有监督方法，LM-O 上无监督与有监督 UnoPose 差距为 2.0%（56.7 vs 58.7）、YCB-V 上差 7.2%（75.9 vs 83.1），语义弱纹理遮挡场景下的鲁棒性仍有限。
- **消融仅在单一数据集上进行**：表 3、表 4 的结果局限于 YCB-V；在 TUD-L 与 LM-O 上各损失/参数的贡献没有得到验证，可能掩盖数据依赖性（例如 TUD-L 对循环一致性权重更敏感）。
- **语义特征依赖 DINO 的固有缺陷**：DINO 对弱纹理、非语义明确物体（如遮挡物）识别不稳定，STEGO 式去噪的效果没有得到定量对比（没有消融"去噪模块 vs 原始 DINO"的实验）。
- **TUD-L 重叠评估样本过少**：只有 3 个物体（Dragon、Frog、Watering Can），统计置信度较低。
- **缺少应用于真实机器人系统的验证**：虽然动机上指向机器人和空间应用，但没有端到端（抓取率、操作成功率）的物理实验。
- **无监督变体在 YCB-V 的置信度质量仍然低于有监督变体**：相关表格（表 2）显示在部分类别（如 Frog）上仍有较大差距，可见完全无监督仍有提升空间。

（完）
