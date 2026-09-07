---
title: "HamiPose: Hamiltonian Optimization for Unsupervised Domain Adaptive Pose Estimation"
title_zh: HamiPose：用于无监督域自适应姿态估计的哈密顿优化
authors: "Li, Jiawen, Jiang, Fei, Zhu, Dandan, Zhou, Aimin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Li_HamiPose_Hamiltonian_Optimization_for_Unsupervised_Domain_Adaptive_Pose_Estimation_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 面向域自适应的姿态估计优化框架，可支撑航天器位姿估计合成数据向真实数据的稳健迁移
tldr: 无监督域自适应的姿态估计在从合成域迁移到真实域时，常因源监督与目标一致性梯度相互干扰而不稳定。为此本文提出HamiPose框架，将解耦并置信度校准的梯度在统一哈密顿几何中传输，并对关键点局部几何进行分解以细化梯度交互。实验显示该方法有效减轻域偏移引起的更新振荡，提升了跨域姿态估计的稳定性和精度。这项工作为含稀疏定位监督的位姿类任务提供了一种通用而稳健的训练范式。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 844, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 868, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 702, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 863, \"height\": 381, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 780, \"height\": 1098, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1716, \"height\": 1257, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1596, \"height\": 453, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 872, \"height\": 560, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1766, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-hamipose-hamiltonian-optimization-for-unsupervised-domain-adaptive-pose-estimation-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 747, \"height\": 422, \"label\": \"Table\"}]"
motivation: 无监督域自适应的位姿估计在合成到真实域迁移时，源监督和目标一致性梯度相互干扰，导致更新不稳定。
method: 提出HamiPose哈密顿优化框架，将解耦且置信度校准后的梯度在统一几何空间中传输，并通过关键点几何分解细化梯度交互。
result: 实验表明HamiPose能有效抑制域偏移下的梯度振荡，提升跨域位姿估计的精度与稳定性。
conclusion: 为关键点式位姿估计的域自适应提供了一种稳健的通用训练范式，可迁移到航天器合成数据训练等任务。
---

## Abstract
Unsupervised domain adaptation (UDA) for pose estimation promises transfer from synthetic to real domains but often suffers instability under domain shift. Prior work attributes this deterioration to gradient interference between source supervision and target consistency. This conflict is distinct in pose estimation, where sparse and heterogeneous supervision signals cause gradients to be highly sensitive to small localization errors and lead to unstable updates. To address these challenges, we propose HamiPose, a Hamiltonian optimization framework that transports decoupled and confidence-calibrated gradients within a unified geometry to mitigate instability. HamiPose first refines gradient interaction through keypointwise geometry decomposition, orthogonally projecting target gradients to preserve nonconflicting component. Channelwise gated alignment then calibrates the parallel component with confidence and alignment, producing decoupled, confidence-calibrated gradients. These gradients are advanced by a Hamiltonian optimizer with a symplectic integrator, providing controlled momentum that stabilizes updates. Extensive experiments demonstrate that HamiPose achieves state-of-the-art performance in UDA pose estimation while maintains strong performance under domain generalization settings.

---

## 论文详细总结（自动生成）

# HamiPose：用于无监督域自适应姿态估计的哈密顿优化 —— 论文详细总结

## 1. 核心问题与研究动机

- 无监督域自适应（UDA）姿态估计旨在利用带标注的合成数据（源域）训练模型，并使其能够适应无标注的真实数据（目标域），以降低真实数据标注成本。
- 论文指出现有方法的主要瓶颈并非单纯的特征或预测空间不对齐，而是**训练过程中多种监督信号之间的梯度冲突**。源域监督梯度与目标域一致性梯度在方向上不一致，导致参数更新振荡、收敛不稳定、跨域泛化差。
- 姿态估计中的梯度冲突具有两个显著特点：
  - **稀疏性**：监督信号为高斯热图，有效梯度只存在于狭窄的峰值邻域内，微小定位偏差即可使梯度方向翻转。
  - **异质性**：目标域伪标签质量随遮挡、截断和运动模糊波动，不同关键点的监督可靠性差异大，少数困难关节主导冲突，其余关节则较一致。
- 这些特性使传统全局梯度对齐方法难以奏效，需要一种保持动态结构、能够抑制振荡并处理稀疏异质监督的优化框架。

## 2. 方法核心思想与关键细节

### 2.1 总体思路

- 将优化过程建模为**哈密顿系统**：损失对应势能，数据驱动的度量诱导动能，参数更新沿保结构流演化，通过辛积分器提供受控动量，平滑高频振荡，实现稳定收敛。
- 整体流程分三步：
  1. **关键点级几何分解**：将目标梯度按关键点分解为正交和并行分量，保留非冲突分量；
  2. **通道级门控对齐**：结合置信度和对齐程度对并行分量进行校准，得到解耦且置信度校准的梯度；
  3. **哈密顿优化**：通过辛欧拉格式对更新进行动量传输。

### 2.2 关键点级几何分解（Keypointwise Geometry Decomposition）

- 在输出热图层面上按通道（关键点）计算源域和目标域梯度。
- 为消除不同参数组的尺度差异，引入**块对角自适应度量**，基于历史更新幅度的 EMA 构建：
  - \(D^{(k)}_{t-1} = (\alpha^{(k)}_{t-1} + \epsilon)I\)
  - 每个关键点对应一组参数 \(\theta^{(k)}\)，包含该输出通道的权重和偏置。
- 将输出梯度通过雅可比回拉（pullback）到参数空间，在该度量下计算：
  - **对齐系数 \(\rho_k\)**（度量归一化余弦相似度）
  - **投影系数 \(a_k\)**（度量内积比值）
- 将目标梯度分解为并行部分 \(g^{(k)}_{t,\parallel} = a_k g^{(k)}_s\) 和正交部分 \(g^{(k)}_{t,\perp} = g^{(k)}_t - g^{(k)}_{t,\parallel}\)。
- 关键性质：正交部分在参数空间度量下与源梯度正交，不会破坏源域下降方向，可安全保留。

### 2.3 通道级门控对齐（Channelwise Gated Alignment）

- 并行部分仍可能因伪标签噪声与源梯度冲突，因此需要选择性过滤。
- 置信度提取：取教师热图在空间网格上的最大值 \(c_k\)，反映该关键点预测的可靠程度。
- 对齐锐度退火：为避免早期硬过滤，设置锐度参数 \(\gamma(t)\) 从 \(\gamma_{\min}\) 线性增加到 \(\gamma_{\max}\)，warmup 期间逐渐提高选择性。
- 门控系数：\(\phi_k = \max(0, \tanh(\gamma(t)\rho_k) \cdot c_k)\)，取值范围 [0,1]；负对齐时置零，正对齐时按与源梯度的相似程度和置信度加权。
- 过滤后的目标梯度为：
  - \(\tilde{g}^{(k)}_{t,pc} = g^{(k)}_{t,\perp} + \phi_k g^{(k)}_{t,\parallel}\)
- 总更新梯度为：
  - \(g^{out}_{total} = g^{out}_s + \lambda \tilde{g}^{out}_{t}\)
- 理论保证：该组合更新在参数空间度量下与源梯度方向非冲突（内积非负）。

### 2.4 哈密顿优化器（Hamiltonian Optimization）

- 建立哈密顿量：
  - \(H(\theta,p) = \frac{1}{2}p^\top D^{-1}p + L_s(\theta) + \lambda L_t(\theta)\)
- 使用自适应质量矩阵（全局）：
  - \(D_{t-1} = (\alpha_{t-1} + \epsilon)I\)
  - \(\alpha_t = \mu\alpha_{t-1} + (1-\mu)\mathrm{mean}((\Delta\theta_t)^2)\)
- 正则方程为：
  - \(\dot{\theta} = D^{-1}p\)
  - \(\dot{p} = -\nabla_\theta(L_s + \lambda L_t)\)
- 采用**单步辛欧拉格式**（kick-drift-kick）：
  - \(p \leftarrow p - \frac{\epsilon}{2}g_H\)
  - \(\theta \leftarrow \theta + \epsilon D^{-1}p\)
  - \(p \leftarrow p - \frac{\epsilon}{2}g_H\)
- 每个迭代只计算一次回拉梯度 \(g_H\)，动量缩放是逐参数操作，额外计算量几乎为零，保持一阶优化代价。
- 每一步更新动量并使用同一梯度的半大步两次，等效于具有动量作用的积分器，可平滑高梯度噪声，防止长期数值漂移。

## 3. 实验设计

### 3.1 数据集与 Benchmark

- 人体姿态估计：
  - 源域：SURREAL（合成人体）
  - 目标域：Leeds Sports Pose (LSP)、Human3.6M（真实人体）
- 手部姿态估计：
  - 源域：Rendered Hand Pose Dataset (RHD)
  - 目标域：Hand-3D-Studio (H3D)、FreiHand（真实手部）
- 评价指标：PCK@0.05（关键点落在图像尺寸 5% 范围的比例），并报告分区部位精度：
  - 人体：肩、肘、腕、髋、膝、踝
  - 手部：MCP、PIP、DIP、指尖
- 此外还进行**域泛化（DG）实验**：
  - SURREAL→LSP 训练后直接测试 Human3.6M（未见域）
  - RHD→H3D 训练后直接测试 FreiHand（未见域）
- 额外在 WBH（COCO 构建的在野手部数据集）上进行定性比较。

### 3.2 对比方法

- 姿态估计 UDA 基线：CC-SSL、MDAM、RegDA、UniFrame、SFHPE、DA-LLPose
- 梯度相关方法：CGDM、FGDA/GGF、PGDA
- 域泛化基线：Fishr、SAM、SAGM、GGA

### 3.3 实现细节

- 骨干网络：ResNet101 预训练 + Simple Baseline 检测头
- 训练：70 epochs，batch size 32，每 epoch 500 次迭代
- 数据增强：旋转（-30°~30°）、随机平移（-5%~5%）
- 损失权重 \(\lambda=1.0\)
- EMA 衰减 \(\tau=0.99\)，二阶矩衰减 \(\mu=0.99\)，\(\epsilon=10^{-8}\)
- 辛积分步长 \(\epsilon=10^{-3}\)，一 epoch warmup 后余弦衰减

## 4. 资源与算力

- 论文正文**未明确说明使用的 GPU 型号、数量或训练时长**。
- 仅在实现细节中说明训练总轮次（70 epochs）、每 epoch 迭代数和 batch size，但未报告整体 wall-clock 时间、显存占用或单卡/多卡配置。
- 因此无法从文中获取精确的算力需求信息，只能推断其额外计算开销很低（动量缩放为 O(|θ|)，每步梯度次数与普通反向传播一致）。

## 5. 实验数量与充分性

### 实验数量

- 人体 UDA：2 个迁移任务（SURREAL→LSP，SURREAL→Human3.6M）
- 手部 UDA：2 个迁移任务（RHD→H3D，RHD→FreiHand）
- 域泛化：2 个未见域评估（Human3.6M，FreiHand）
- 消融研究：2 个基准任务（SURREAL→Human3.6M，RHD→H3D），逐步加入三个核心模块
- 附加分析：关键点级 vs 统一门控的冲突比例曲线（图 4），哈密顿优化 vs SGD/Adam 的损失轨迹对比（图 5），超参数分析（γmin/γmax/warmup ratio，表 5）
- 定性比较：LSP、H3D、FreiHand、Human3.6M 可视化结果，以及 WBH 数据集上与 GGA/GASM 的定性对比

### 充分性评估

- 覆盖了人体和手部两类姿态估计任务，包含合成到真实、不同目标域和未见域设置，比较对象包括了领域内主流 UDA 和梯度相关 DG 方法，整体较为全面。
- 消融实验能清晰验证每个模块的贡献；梯度冲突比例曲线和损失轨迹分析进一步支持哈密顿优化的稳定性声明。
- 超参数分析对门控参数进行了网格搜索，显示了方法对超参数的基本敏感性。
- 可能的不足：
  - 所有 UDA 实验均采用**合成源到真实目标的单方向设置**，未涉及真实到真实或逆方向迁移。
  - 未报告多次随机种子的方差或统计显著性，无法判断差异是否稳健。
  - 方法依赖伪标签质量；在极端低估伪标签噪声情况下（如严重遮挡）的鲁棒性缺少专门实验。
  - 未与其他新近的优化器（如 RAdam、LAMB、SAM 的变体）在相同网络下做系统比较，仅对比了 SGD/Adam。
  - 部分表格中“Source Only”的基线数值与正文描述存在不一致（如手部表），可能存在排版或统计口径问题。

## 6. 主要结论与发现

- HamiPose 在四个 UDA 姿态估计任务上均取得最优总体精度：
  - SURREAL→LSP：All 83.9%
  - SURREAL→Human3.6M：All 79.8%
  - RHD→H3D：All 83.1%
  - RHD→FreiHand：All 59.9%
- 在域泛化设置中同样取得最佳结果：
  - 未见域 Human3.6M：All 77.5%
  - 未见域 FreiHand：All 52.2%
- 在困难部位（如髋、指尖等）上性能提升尤为显著，说明方法能缓解由异质监督导致的局部梯度冲突。
- 关键点级门控比统一门控更快降低冲突比例（最终稳定在约 6% vs 8~9%）。
- 哈密顿优化相较 SGD 和 Adam，损失曲线更平稳、步间波动更小，能在保持一阶代价的同时抑制高频振荡。

## 7. 优点与亮点

- 将哈密顿动力学与辛积分引入 UDA 姿态估计的优化过程，视角新颖且有物理直觉支撑。
- 采用关键点级别的梯度分解，区别于以往全局梯度对齐，更贴合姿态估计中伪标签异质性的特点。
- 门控机制中同时引入**几何对齐**（ρk）和**教师置信度**（ck），并配合锐度退火，避免训练初期强制过滤导致的误拒。
- 理论上有保障：组合更新与源梯度在指定度量下内积非负，能确保不干扰源域下降方向。
- 实际计算开销小：无需额外的对抗网络或二阶信息，每步仅额外做一次动量缩放，适合大规模训练。
- 在 UDA 和域泛化两种协议下均取得领先性能，说明方法不只针对特定适配场景，还具备一定泛化能力。

## 8. 不足与局限

- 方法主要在热图回归的监督信号下设计，**适用于基于热图的姿态估计头**；对直接回归坐标或以 Transformer 为输出头的模型需要重新推导或适配。
- 训练仍然需要源域数据可用且每个目标 batch 需要同时计算源/目标损失，**不适用于 source-free 或完全测试时自适应**场景。
- 门控和哈密顿优化引入了多个超参数（γmin、γmax、warmup 比例、ε、μ、辛步长 ε 等），实际应用中需要较多调参成本。
- 所有实验都在公开合成-真实人体/手部姿态数据集上进行，且模型规模相对固定（ResNet101 + Simple Baseline），**未验证在更大模型或视频/3D 姿态估计上的可扩展性**。
- 论文中未给出严谨的收敛性证明，仅提供非冲突性质和动力学上的直觉，理论完备性有待加强。
- 未报告实验随机种子、多次重复的标准差，也未披露计算资源，无法精确评估结果的可复现性和方法稳定性。
- 使用教师热图最大值作为置信度可能偏向空间峰值明显的简单样本，对多峰或低响应情形可能估计不准。

（完）
