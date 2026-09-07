---
title: "LEADER: Learning Reliable Local-to-Global Correspondences for LiDAR Relocalization"
title_zh: LEADER：学习可靠局部到全局对应以实现激光雷达重定位
authors: "Wu, Jianshi, Zhu, Minghang, Liu, Dunqiang, Li, Wen, Ao, Sheng, Shen, Siqi, Wen, Chenglu, Wang, Cheng"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Wu_LEADER_Learning_Reliable_Local-to-Global_Correspondences_for_LiDAR_Relocalization_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 5.0
evidence: 鲁棒激光雷达重定位结合6自由度位姿回归与可靠局部-全局对应学习，可用于基于激光雷达的位姿估计方法
tldr: 在复杂三维场景中，基于深度回归的激光雷达重定位常因对噪声和离群点一视同仁而精度有限。LEADER提出鲁棒投影式几何编码器，捕获多尺度几何特征以增强描述，并通过可靠局部到全局对应学习提升6自由度位姿预测。实验显示其在挑战性场景中较现有回归方法更稳健。该对应学习方法可用于基于点云模型的航天器相对位姿估计。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 793, \"height\": 522, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1632, \"height\": 805, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 795, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1804, \"height\": 381, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1794, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 621, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 827, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 829, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 837, \"height\": 419, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1813, \"height\": 457, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1757, \"height\": 456, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 304, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1744, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wu-leader-learning-reliable-local-to-global-correspondences-for-lidar-relocalization-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 851, \"height\": 304, \"label\": \"Table\"}]"
motivation: 激光雷达重定位回归方法在复杂场景中对噪声离群点敏感，等权处理所有点导致位姿预测不稳定。
method: 提出带鲁棒投影式几何编码器的LEADER框架，提取多尺度几何特征并学习可靠局部到全局对应来回归6自由度位姿。
result: 在挑战场景下比已有回归方法更准确稳健地估计激光雷达6自由度位姿。
conclusion: 验证了强几何描述与可靠对应学习对鲁棒激光雷达位姿回归的有效性，可迁移至点云目标位姿估计。
---

## Abstract
LiDAR relocalization has attracted increasing attention as it can deliver accurate 6-DoF pose estimation in complex 3D environments. Recent learning-based regression methods offer efficient solutions by directly predicting global poses without the need for explicit map storage. However, these methods often struggle in challenging scenes due to their equal treatment of all predicted points, which is vulnerable to noise and outliers. In this paper, we propose LEADER, a robust LiDAR-based relocalization framework enhanced by a simple, yet effective geometric encoder. Specifically, a Robust Projection-based Geometric Encoder architecture which captures multi-scale geometric features is first presented to enhance descriptiveness in geometric representation. A Truncated Relative Reliability loss is then formulated to model point-wise ambiguity and mitigate the influence of unreliable predictions. Extensive experiments on the Oxford RobotCar and NCLT datasets demonstrate that LEADER outperforms state-of-the-art methods, achieving 24.1% and 73.9% relative reductions in position error over existing techniques, respectively. The source code is released on https://github.com/JiansW/LEADER.

---

## 论文详细总结（自动生成）

# LEADER：学习可靠局部到全局对应以进行 LiDAR 重定位

## 1. 核心问题与整体含义

- **研究背景**：LiDAR 重定位任务旨在给定单帧激光雷达扫描时，估计传感器在世界坐标系中的 6 自由度位姿，特别应用于 GNSS 不可靠的自动驾驶与机器人场景。
- **现有方法不足**：传统“检索-配准”范式对存储和通信资源要求高，不利于城市场景实时部署；已有基于学习的“场景坐标回归”框架被一视同仁地处理所有点，导致：
  - 对偏航角变化（yaw rotation）鲁棒性差，网络在视角变化下预测不一致；
  - 对环境中不可靠的退化结构敏感，产生错误对应，而真实场景中只有部分几何区域能提供稳定重定位线索。
- **论文目标**：设计一种可靠的场景坐标回归新框架，同时解决两大挑战：①姿态变化下的表示鲁棒性；②对不可靠点的判别与抑制。实验在两个大规模数据集上实现了当前最优精度。

## 2. 论文提出的方法论

### 2.1 核心思想
LEADER 将场景坐标回归与可靠性建模结合，通过一种**鲁棒投影式几何编码器**获得对偏航不敏感的多尺度特征，并用新设计的**截断相对可靠性损失**估计逐点可靠性，从而在推理时只保留高质量对应点，交由 RANSAC 位姿估计。

### 2.2 总体架构
| 模块 | 作用 |
|---|---|
| 空间变换模块（Spatial Transformation） | 先通过 Patchwork++ 估计地面并校正点云至水平面；再做柱面投影（voxelization，分槽大小为 1024），将柱面坐标视作笛卡尔坐标进行特征提取，构成对偏航角一致的场景结构 |
| 鲁棒投影式几何编码器（RPGE） | 采用多维特征编码：每点特征由 [y, z, 强度] 构成，回避对偏航敏感的 x 分量；引入循环填充式稀疏卷积以处理柱面投影中 yaw 边界处的不连续性；使用 U-Net 架构，五步下采样与单步上采样，将末层与下采样第四层特征拼接得到 512 维特征 |
| 多头最大回归器 | 多层全连接配合多分辨率头(取 k=4 头中的最大激活)，先回归 3D 场景坐标与 1D 可靠性分数；再通过逆柱面投影恢复笛卡尔坐标以保持几何一致 |
| 位姿估计（推理阶段） | 利用可靠性分数选出 top-k 点，通过 RANSAC / 鲁棒最小二乘 (如 SC2-PCR 等) 求解 6-DoF 变换，并补偿地面校正得到最终世界系位姿 |

### 2.3 关键损失函数：truncated Relative Reliability Loss（TRR）
- 先计算逐点预测坐标与真值坐标的欧式距离： `L_raw, i = ||gt_i − c_hat_i||`。
- 对预测可靠性分数应用 arctan 缩放与 clamp，限定其数值边界。
- 通过指数归一化形成权重，对区域内所有逐点误差做加权求和：
  `L_TRR = Σ_i w_i · L_raw,i`，权重对确定性高的点增大、对模糊样本减少。
- 设计效果：促使网络自适应地“牺牲”难以学习（动态物体、弱纹理等）点以集中资源拟合可靠的几何结构，实现自调节的权重分配机制。

## 3. 实验设计

### 3.1 数据集 / Benchmark
- **Oxford RobotCar（质量增强版）**：城市场景，10 km 路径，4 条轨迹用于训练、4 条用于测试（含光照与天气变化）；
- **NCLT（North Campus）**：校园场景，约 5.5 km，覆盖季节变化、植被稀疏和有意的人为 LiDAR 振动，也使用 4 条训练/4 条测试轨迹。

### 3.2 对比方法
- **APR 法**：PointLoc、PosePN++（论文表中同时包括 PosePN++）、HypLiLoc、DiffLoc；
- **SCR 法**：SGLoc、LiSA、RALoc、LightLoc。
- 另提供帧误差累积分布、99% 误差阈值（critical coverage）等对比。

## 4. 资源与算力

文中提及**训练与硬件配置**，但**并未明确给出总训练时长或总计算量**。

- **硬件**：单张 NVIDIA RTX 3090，Intel i9-14900K CPU，128 GB RAM；
- **软件框架**：PyTorch 与 MinkowskiEngine（稀疏卷积）；
- **训练参数**：Adam 优化器，初始学习率 0.001，衰减因子 γ=0.9，体素大小 0.2m，柱面圆周分辨率 Lx=1024，共训练 50 epochs。

整体训练耗时未在方法与实验段落内报告。

## 5. 实验数量与充分性

实验总体上较为详实：

- **主实验**：在两个公开主流自动驾驶/校园域基准（质量增强版 Oxford RobotCar 与 NCLT）上与 **4 类 APR + 4 类 SCR** 共 8 种基线进行了逐轨迹与平均精度比较，属于当前领域内的标准测试设置；
- **消融研究**：完成 RPGE 与 TRR 消融，对固定配置做了开启/关闭组合，共 6 种变体，分别报告正常点云与方位扰动下误差、耗时、参数量；
- **鲁棒性评估**：测试 180° FOV 遮挡、随机点丢弃0–50%、高斯噪声、俯仰/翻滚各 ±10° 扰动等退化条件；
- **补充机制验证**：绘制 TRR 启用前后的误差分布变化，以及可靠性分数区间与平均场景点误差之间的趋势，以验证 TRR 权重机制有效性。

### 充分性综合评价
- 两个互补的真实场景数据集、多个轨迹、足够多 SOTA 基线、多种组合消融与鲁棒性测试，均在一个较高的科学性标准上完成，实验设计总体**公平、充分且客观**；
- 但是，消融与额外机制分析主要集中在 NCLT 数据集，牛津数据集上未包括完整的同维度消融与鲁棒性检查，可能会使某些结论略有局限；此外不同方法误差虽有大幅下降，但在公平性上应进一步检查各方法的超参数（RANSAC 阈值、top-k 策略等）是否调至最优。

## 6. 主要结论与发现

- LEADER 在 Oxford RobotCar 上平均位置误差降到 **0.63 m**(平均角度 1.11°)，相对最优 SCR 基线 (LightLoc)提升 **24.1%**；
- 在 NCLT 上位置误差降至 **0.31 m**、角度误差 1.81°；相对 DiffLoc 误差下降 **73.9%**，相对 LiSA 高 **79.5%**，是**首个在 NCLT 上达到亚 0.5 m 精度的隐式重定位方法**；
- 达到非常高的定位一致性：**90.0% 的 NCLT 帧误差小于 0.5 m**，98.3% 帧误差小于 1 m，仅在 1.23 m 阈值内即达到 99% 覆盖率，远超其他基线在 4.98–8.70 m 的表现；
- 运行时满足实时要求：Oxford 上 20 Hz、NCLT 上 10 Hz，单帧处理 46–48 ms；
- 消融与鲁棒性验证证明 RPGE 显著吸收偏航扰动，TRR 使网络能自适应地聚焦高可靠点并抑制退化区域，所预测可靠性分数与真实场景坐标误差有强烈单调相关性；
- 消融结论部分提到，RPGE 在正常点云与偏航扰动点云下几乎位置与角度各自完全一致，但对俯仰/翻滚仍依靠地面点校正，因此目前框架只能稳定处理高偏航变化，其他旋转轴还需改进。

## 7. 优点

1. **创新性的几何表示**：柱面投影 + 循环稀疏卷积方案在保持特征提取不变性的同时，自然解决了环形方向角坐标的分界不连续问题；
2. **端到端可学习的可靠性机制**：TRR 损失不需要额外的标注（如语义、置信度标签），让网络在训练过程中动态地分配容量，只在回归与推理中加入一种自加权机制，在无增加模型参数（新增 <0.001M）的前提下显著提升精度；
3. **广泛的泛化性与实时性**：在两个差异明显（城区稠密与校园植被稀疏干扰）的数据集上获得一致提升，且保持计算高效；
4. **优秀的鲁棒性表现**：在入站干扰条件下（遮挡、丢点、噪声、俯仰颤动）仍超过部分 SOTA 在正常条件下的结果，且有丰富的可视化与分析支撑；
5. 论文透明度较好，提供源码地址，公开了比较全面的实现细节。

## 8. 不足与局限

1. **旋转范围有限**：框架依赖地面/平面检测来进行俯仰和翻滚校正，本质只能有效补偿**偏航**的旋转变化，论文中多次明确说明此点，作者也指出未来要扩展到完整 SE(3) 而无地面先验；
2. **实验类别相对理想**：训练和测试轨迹邻近（但非精确重叠），事实上未涉及真正差异大的跨场景长期重定位（如相隔数月/数公里的远路径外推）或极端天气下强度分布变化；
3. **可靠性机制的特例性**：消融中 TRR 能降低位置误差，但角度误差改善微弱，作者注意到远处点的稀疏分布可能增强角度回归的困难，这需要未来考虑更高分辨率的远程结构纳入建模，但对于全自动导航而言角度精度同样非常关键；
4. **消融报告较为集中**：所有消融与机制分析均在NCLT数据集完成，牛津数据集上的针对性消融未完全呈现；
5. **缺少对失败案例的详细分析**（如哪类路段和结构仍然失败），论文整体技术写作合理，但讨论中可以更充分地说明误差来源；
6. 硬件实验仅用单张消费卡 RTX 3090 训练，部分条件下 50 轮的训练时长待定，报告对算力细节披露可以更加完整。

（完）
