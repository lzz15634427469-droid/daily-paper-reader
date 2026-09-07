---
title: "LiREC-Net: A Target-Free and Learning-Based Network for LiDAR, RGB, and Event Calibration"
title_zh: LiREC-Net：面向LiDAR、RGB与事件数据的无靶标学习标定网络
authors: "Dash, Aditya Ranjan, Battrawy, Ramy, Schuster, René, Stricker, Didier"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Dash_LiREC-Net_A_Target-Free_and_Learning-Based_Network_for_LiDAR_RGB_and_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 联合标定LiDAR与RGB传感器无需靶标，是激光雷达+相机融合位姿估计的关键前置能力
tldr: 多传感器融合的前提是精确标定，而现有学习方法一般只标定一对双模态传感器且依赖靶标。LiREC-Net提出免靶标、可学习的统一标定网络，能够在同一框架中对LiDAR、RGB和事件相机的多个传感器对进行联合标定。网络通过共享LiDAR表示降低冗余计算并提高特征效率，仅需自然驾驶场景即可完成精确多模态对齐。该工作可作为LiDAR与相机数据相对位姿估计系统的传感器配准步骤，支撑后续空间目标融合测量流程。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 906, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1808, \"height\": 852, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 872, \"height\": 1233, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 866, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 355, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 864, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 454, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-dash-lirec-net-a-target-free-and-learning-based-network-for-lidar-rgb-and-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 831, \"height\": 257, \"label\": \"Table\"}]"
motivation: 现有双模态标定方法难以扩展到多传感器系统，且靶标依赖限定了应用场景。
method: 在统一网络中用共享LiDAR表示联合标定多个LiDAR、RGB与事件传感器对，目标为免靶标的端到端相对外参回归。
result: 无需靶标即可高精度对齐自然场景中的多传感器对，并降低冗余计算，提升效率。
conclusion: 无靶标联合标定可简化多模态传感系统标定流程，是LiDAR与相机融合感知的重要组成部分。
---

## Abstract
Advanced autonomous systems rely on multi-sensor fusion for safer and more robust perception. To enable effective fusion, calibrating directly from natural driving scenes (i.e., target-free) with high accuracy is crucial for precise multi-sensor alignment. Existing learning-based calibration methods are typically designed for only a single pair of sensor modalities (i.e., a bi-modal setup). Unlike these methods, we propose LiREC-Net, a target-free, learning-based calibration network that jointly calibrates multiple sensor modality pairs, including LiDAR, RGB, and event data, within a unified framework. To reduce redundant computation and improve efficiency, we introduce a shared LiDAR representation that leverages features from both its 3D nature and projected depth map, ensuring better consistency across modalities. Trained and evaluated on established datasets, such as KITTI and DSEC, our LiREC-Net achieves competitive performance to bi-modal models and sets a new strong baseline for the tri-modal use case.

---

## 论文详细总结（自动生成）

## 1. 核心问题与研究动机

现代自动驾驶系统通常融合多种传感器（LiDAR、RGB 相机、事件相机）以提升感知的鲁棒性和安全性。多传感器融合的前提是传感器之间的精确空间对齐（即外参标定）。然而实际操作中，车辆振动、温度变化、碰撞或维护等因素都会导致传感器相对位姿发生漂移，需要定期重新标定。

现有标定方法存在以下主要痛点：
- **靶标依赖**：传统方法（棋盘格、ArUco 标记等）需要受控环境、反复采集，成本高、干扰正常运营；
- **双模态局限**：现有基于学习的无靶标方法（如 LCCNet、RegNet、MULiEv 等）大多只针对单个传感器对（LiDAR-RGB 或 LiDAR-Event）分别标定，当系统扩展到三类传感器时会带来冗余计算、效率低下以及跨模态校准不一致性的问题。

**核心研究问题**：能否设计一种统一的、无靶标的、基于学习的框架，在同一网络架构中联合标定 LiDAR、RGB 相机与事件相机之间的相对外参？

论文给出了肯定回答——提出 **LiREC-Net**，该网络端到端地从自然驾驶场景中学习预测 LiDAR-RGB 和 LiDAR-Event 两组外参，无需标定靶标，同时支持任意一种相机单独使用或两种相机同时使用的场景。

---

## 2. 方法论述

### 2.1 核心思想

LiREC-Net 采用**双路径共享 LiDAR 特征编码器**的设计：

- 一个共享的 LiDAR 特征分支同时服务于 LiDAR-RGB 和 LiDAR-Event 两条标定路径，避免对每个双模态对分别训练独立的 LiDAR 编码器；
- 将 LiDAR 点云特征与其投影深度图的特征进行融合，得到统一的 LiDAR 表示，同时保留 3D 结构信息和稠密的深度几何线索；
- 对标定问题建模为从带误标定的多模态输入回归两组相对变换（平移向量 ˆt ∈ R³ + 单位四元数 ˆq ∈ R⁴）。

### 2.2 输入预处理

| 模态 | 预处理方式 |
|------|-----------|
| LiDAR 点云 | 转换到相机坐标系，滤除负深度点，按最大距离截断，固定重采样到 N 个点 |
| LiDAR 深度图（SDP） | 将点云投影为单通道深度图，投影时使用**缩放内参矩阵**（scale matrix 缩放原始内参）而非原始内参投影后 resize，避免模糊伪影 |
| RGB 图像 | 按训练集统计做通道标准化，bilinear resize 到模型输入分辨率 |
| 事件数据 | 50ms 时间窗内累积正/负极性双通道事件帧，利用已知的 RGB-Event 外参变换到 RGB 坐标系后输入 |

### 2.3 架构关键组件

1. **共享 LiDAR 编码分支**
   - 基于点的编码器：**Point-Transformer-V3 (PTV3)**，通过空间填充曲线序列化点云实现高效局部注意力，捕获细粒度 3D 几何结构；
   - 基于深度的编码器：**MViTV2**，从深度图中提取空间上下文；
   - 逐点特征通过缩放内参投影到图像平面（**SFP**，Scaling Feature Projection），与深度特征在通道维度拼接融合。

2. **RGB / 事件编码器**
   - 两个独立的 MViTV2 编码器，分别提取各自的模态特征，利用卷积捕获局部纹理、Transformer 建模全局上下文。

3. **成对代价体（Pair-wise Cost Volume）**
   - 借鉴 PWC-Net 和 LCCNet 的思路，在 LiDAR 特征与相机特征之间用通道归一化内积构建相关性代价体：
   
   \[
   C(y,x,\Delta x,\Delta y) = \frac{1}{C}\sum_{c=1}^{C} F^c_{Li}(y,x) \cdot F^c_{Cam}(y+\Delta y, x+\Delta x)
   \]
   
   - 代价体维度为 H″ × W″ × M（M = (2d+1)²）。

4. **上下文模块**
   - 每路径 5 层卷积，参考 DenseNet 将每层输出与当前特征拼接，保留低层与高层信息。

5. **预测头**
   - 展平特征后经共享全连接层，再分叉为 translation head（2 层 FC + LeakyReLU）和 rotation head（输出归一化为合法四元数）。

### 2.4 迭代细化

采用与 LCCNet 类似的多阶段策略：

- 训练 S 个模型（stage），从最大的标定误差范围逐步训练到最小范围；
- 每个 stage 预测增量变换 ΔT̂⁽ᵏ⁾，通过矩阵乘法逐级修正：
  
  \[
  \hat{T}_{v}^{(k)} = \Delta\hat{T}_{v}^{(k)} \cdot \hat{T}_{v}^{(k-1)}, \quad k=1,\ldots,S
  \]

### 2.5 损失函数

每组模态对的总损失由三部分组成：

- **平移损失**：Smooth L1 损失 \( \mathcal{L}_{trans} \)；
- **旋转损失**：预测四元数与真值四元数之间的角度距离 \( \mathcal{L}_{rot} \)；
- **点云距离损失**：预测变换与真值变换作用下 LiDAR 点位置的欧氏距离 \( \mathcal{L}_{pcd} \)。

总损失：
\[
\mathcal{L}_v = (1-w)(\lambda_t \mathcal{L}_{trans}^v + \lambda_r \mathcal{L}_{rot}^v) + w\mathcal{L}_{pcd}^v
\]
\[
\mathcal{L}_{total} = \mathcal{L}_{Li-RGB} + \mathcal{L}_{Li-Ev}
\]

---

## 3. 实验设计

### 3.1 数据集

| 数据集 | 用途 | 关键细节 |
|--------|------|----------|
| **KITTI Odometry** | LiDAR-RGB 标定 benchmark | LiDAR-RGB 无事件数据，使用 **V2E** 框架从 RGB 视频合成事件；每帧取 N=20,000 前向点 |
| **DSEC** | 三模态联合标定 | 真实 LiDAR（VLP-16）+ RGB（FLIR）+ 事件相机（Prophesee Gen3.1），点云更稀疏（N=5,000），光照天气多样，更具挑战性 |

### 3.2 仿真误标定设置

对比实验采用两组扰动范围：
- 五阶段：±{20°/150cm, 10°/100cm, 5°/50cm, 2°/20cm, 1°/10cm}（与 RegNet、LCCNet 对齐）；
- 两阶段：±{10°/100cm, 1°/10cm}（与 MULiEv 对齐）。

训练/测试时对 LiDAR-RGB 和 LiDAR-Event 分别施加**两个独立的误标定扰动**，模拟两组外参各自偏差的真实场景。

### 3.3 对比方法与基准

- **LiDAR-RGB 对比方法**：RegNet、CalibNet、LCCNet、PseudoCal、LCCRAFT（补充材料）；
- **LiDAR-Event 对比方法**：MULiEv（唯一已有方法）；
- 由于已有方法多为双模态模型，DSEC 上 LiDAR-RGB 标定此前无人报告结果，LiREC-Net 建立了该基准。

### 3.4 评估指标

- 平移误差 \(e_t\)：预测与真值平移向量的平均欧氏距离；
- 旋转误差 \(e_r\)：预测与真值四元数的平均角度差。

---

## 4. 资源与算力

论文**未明确报告总训练时间**。文中仅交代关键训练配置：

- 优化器：Adam，学习率 3×10⁻⁴，按验证损失饱和以 0.5 衰减；
- 训练轮数：DSEC 第一阶段 150 epochs + 后续每阶段 70 epochs；KITTI 第一阶段 120 epochs + 后续每阶段 50 epochs；
- 硬件：4× NVIDIA RTX A6000 / L40S GPU，batch size 64；
- 推理效率评测统一使用 NVIDIA H200 GPU。

此外，tri-modal 模式的推理指标可量化：KITTI 上推理时间约 0.33s，参数量 1.7×10⁹，GPU 显存 11.1 GiB。

---

## 5. 实验数量与充分性

### 实验数量

论文共包含以下实验：

1. **KITTI benchmark 实验**（五阶段扰动，±20°/150cm）— 对比 RegNet、CalibNet、LCCNet、PseudoCal；
2. **DSEC benchmark 实验** — 五种阶段设置下的 LiDAR-RGB 与 LiDAR-Event 结果，对比 MULiEv；
3. **Bi-modal vs. Tri-modal 对比实验** — KITTI 和 DSEC 上分别比较分开训练/联合训练的性能、时延、参数量、显存；
4. **消融实验 1**：point features 与 depth features 的有无（3 组）；
5. **消融实验 2**：SDP/SFP 四种组合（4 组）；
6. **消融实验 3**：MViTV2 vs. ResNet backbone（2 组）；
7. **定性可视化结果**：KITTI 与 DSEC 的校准前后叠加对比图。

### 充分性评估

**充分之处**：
- 在 KITTI 与 DSEC 两个不同密度、不同环境的真实/半真实驾驶数据集上验证，覆盖面较广；
- 消融从特征融合、投影策略、骨干网络三个维度展开，逻辑完整；
- 与多个代表性 SOTA 方法在相同扰动范围的公平对比，设置细节表述明确；
- 额外对 bi-modal vs. tri-modal 的效率-精度权衡做了系统对比，反映设计的实际工程价值。

**不足之处**：
- 消融实验仅在 DSEC 上进行，KITTI 上缺少相应的消融验证以确认结论的跨数据集一致性；
- 对合成事件（KITTI-V2E）与真实事件（DSEC）域差异的定量分析不深入；
- LCCRAFT 的对比放在补充材料且评价标准不同，主表读起来对比不够一目了然。

---

## 6. 主要结论与发现

1. LiREC-Net 是第一个统一的 tri-modal LiDAR-RGB-Event 无靶标学习标定框架，可以直接在自然场景中联合预测两组外参。
2. 在 KITTI 上达到 LiDAR-RGB **1.80cm / 0.11°**，同时实现 LiDAR-Event **1.82cm / 0.12°**，精度与专门设计的双模态方法相当，显著优于 RegNet 和 CalibNet，旋转精度上超过 LCCNet，翻译上仅落后 21mm。
3. 在 DSEC 真实事件数据上实现 LiDAR-RGB **2.51cm / 0.14°**，并于 LiDAR-Event 达到旋转误差 **0.07°**，优于 MULiEv（0.10°）；平移误差（1.18cm）略逊于 MULiEv（0.81cm）。
4. 共享 LiDAR 表示带来显著的效率收益：tri-modal 模式下 KITTI 推理时间降低约 35%（0.51s → 0.33s），显存节省约 24%（14.6 → 11.1 GiB），且精度基本不降、部分指标反升。
5. 消融实验证明：
   - 点特征与深度特征**缺一不可**——只用点特征时 LiDAR-RGB 平移误差从 2.51cm 恶化到 14.43cm；
   - SDP 与 SFP 两个缩放投影策略互为补充，同时去除时误差大幅上升；
   - 基于 Transformer 的 MViTV2 相比 ResNet 更有利于跨模态特征对齐。

---

## 7. 优点与亮点

1. **问题选择前沿**：事件相机是新兴传感器，三模态统一标定少有先例，填补了研究空白。
2. **共享特征的设计高度工程实用**：不只追求精度，也重点权衡了推理时间、显存、参数量，比纯性能导向的 SOTA 更贴近实际部署。
3. **SDP 与 SFP 的缩放投影细节**是一个原创的技术贡献，可有效避免投影后缩放带来的图像退化，对精度有明显提升。
4. **双扰动训练策略设计巧妙**：在同一网络中让两条路径分别带不同误标定输入，既能联合训练又不会让网络只学会拟合单一偏差。
5. **实验设置规范**：与已有方法在相同扰动水平和评价指标下进行比较，并公开多维度效率数据。
6. 在 DSEC LiDAR-RGB 上建立了全新的 benchmark，为后续研究提供基准参照。
7. 论文写作结构清晰、图文并茂，可视化定性地证明了校准的实际效果。

---

## 8. 不足与局限

1. **沿用逐点/逐变换独立监督方式**，分支间缺少跨模态约束或一致性损失；虽然共享了 LiDAR 特征（一定程度缓解），但 RGB 与事件分支的预测在统一框架内未获得显式联合优化的协同收益验证。

2. **重要假设限制了泛化能力**：假设 RGB 与事件相机之间存在已知外参（预标定）。尽管仿真中两张相机相对 LiDAR 各自有不同扰动，这一前提在真实系统中仍需另一次标定过程保证。

3. **合成事件域差异**：KITTI 上的事件数据由 V2E 生成，与真实事件相机的噪声特性、动态范围均有差异；以此评估 LiDAR-Event 标定性能存在一定的仿真-真实 gap。KITTI 上首次建立 LiDAR-Event 基线，但其参考价值有待真实事件数据验证。

4. **无靶标精度与传统方法的差距**：实验主要与学习方法对比，未在真实物理环境中间接验证其精度极限或与传统 target-based 方法精度的差距。

5. **消融实验局限在 DSEC**，低线数 LiDAR（VLP-16）上的结论是否在 64 线 KITTI 同样成立未知。

6. **扰动范围有限**：最大误差设定为 ±20°/150cm，更大范围的初始化误差在真实安装偏差较大的场景下可能失效。

7. **实时性不足**：虽然 tri-modal 效率有所改善（0.33s，即约 3 FPS），事件相机本身通常用于高速场景，要达到实时在线在线标定还需进一步压缩推理时间。

---

（完）
