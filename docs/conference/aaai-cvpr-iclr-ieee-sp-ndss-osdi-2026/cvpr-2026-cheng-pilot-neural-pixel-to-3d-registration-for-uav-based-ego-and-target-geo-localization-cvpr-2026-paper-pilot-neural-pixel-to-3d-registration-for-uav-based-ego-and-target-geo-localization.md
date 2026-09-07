---
title: "PiLoT: Neural Pixel-to-3D Registration for UAV-based Ego and Target Geo-localization"
title_zh: PiLoT：面向无人机自身与目标地理定位的神经像素到三维注册
authors: "Cheng, Xiaoya, Wang, Long, Liu, Yan, Liu, Xinyi, Tan, Hanlin, Liu, Yu, Zhang, Maojun, Yan, Shen"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Cheng_PiLoT_Neural_Pixel-to-3D_Registration_for_UAV-based_Ego_and_Target_Geo-localization_CVPR_2026_paper.pdf"
tags: ["query:pe"]
score: 6.0
evidence: 单目视频到三维地图的像素注册实现自身与目标定位，类比航天器与目标的相对位姿确定。
tldr: 面向无人机自身与目标地理定位的已有方法常依赖GNSS与视觉惯性里程计等分离式流程，在GNSS缺失环境中易失效。PiLoT提出将实时视频流直接与地理参考三维地图进行神经像素到3D注册，同时估计自身位置姿态与目标位置，并采用双线程引擎分离地图渲染与定位计算以降低延迟。实验显示该方法能够在保持实时性的同时取得鲁棒和准确的定位结果，为视觉相对定位问题提供了一种可迁移的单目注册方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1799, \"height\": 732, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1806, \"height\": 528, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1793, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1794, \"height\": 456, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 337, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1822, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 881, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-cheng-pilot-neural-pixel-to-3d-registration-for-uav-based-ego-and-target-geo-localization-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 894, \"height\": 413, \"label\": \"Table\"}]"
motivation: 现有无人机自身与目标地理定位依赖GNSS和视觉惯性里程计解耦流水线，易在GNSS拒止环境失效且硬件成本高。
method: 提出PiLoT，将实时视频流直接与地理参考三维地图做像素到三维注册，同时估计自身与目标定位，并用双线程引擎加速。
result: 在保持实时定位能力的同时获得鲁棒准确的地理定位结果，表明不依赖GNSS的像素到三维注册可行。
conclusion: PiLoT为无人机目标定位提供了GNSS拒止环境下的统一单目注册范式，其思路可延伸至航天器相对位姿估计。
---

## Abstract
We present PiLoT, a unified framework that tackles UAV-based ego and target geo-localization. Conventional approaches rely on decoupled pipelines that fuse GNSS and Visual-Inertial Odometry (VIO) for ego-pose estimation, and active sensors like laser rangefinders for target localization. However, these methods are susceptible to failure in GNSS-denied environments and incur substantial hardware costs and complexity. PiLoT breaks this paradigm by directly registering live video stream against a geo-referenced 3D map. To achieve robust, accurate, and real-time performance, we introduce three key contributions: 1) a Dual-Thread Engine that decouples map rendering from core localization thread, ensuring both low latency while maintaining drift-free accuracy; 2) a large-scale synthetic dataset with precise geometric annotations (camera pose, depth maps). This dataset enables the training of a lightweight network that generalizes in a zero-shot manner from simulation to real data; and 3) a Joint Neural-Guided Stochastic-Gradient Optimizer (JNGO) that achieves robust convergence even under aggressive motion.Evaluations on a comprehensive set of public and newly collected benchmarks show that PiLoT outperforms state-of-the-art methods while running over 25 FPS on NVIDIA Jetson Orin platform. Our code and dataset are available at: https://github.com/Choyaa/PiLoT.

---

## 论文详细总结（自动生成）

## 1. 核心问题与研究动机

无人机自身与目标的地理定位（geo-localization）是实现数字孪生、增强现实、自主导航和具身智能等应用的基础能力。传统主流方法采用**解耦流程**：

- **自身定位（Ego-localization）**：依赖 GNSS 与视觉惯性里程计（VIO）融合；
- **目标定位（Target geo-localization）**：依赖激光测距仪等主动传感器。

该范式存在两个关键缺陷：

1. **GNSS 拒止环境下易失效**：地下、城市峡谷、电子干扰等场景无法使用；
2. **硬件成本高、系统复杂**：激光等主动传感器昂贵且笨重，且只能定位单一目标点。

论文主张根本性的范式转变：将自身的 6-DoF 位姿估计与任意像素的目标地理坐标定位，统一建模为**将实时视频流对地理参考三维地图的逐像素到三维（pixel-to-3D）注册问题**。

该问题面临所谓“不可能三角”的挑战：同时兼顾精度（漂移自由）、鲁棒性（环境与运动变化）和实时性（嵌入式平台可运行）。

---

## 2. 方法论

### 2.1 总体框架：PiLoT

输入为：地理参考三维地图、单目视频流、相机内参、首帧的粗略位姿先验。输出为：每帧的 6-DoF 无人机位姿、任意目标像素的经纬高坐标。

### 2.2 三大核心技术创新

#### ① 双线程引擎（Dual-Thread Engine）

将地图渲染与核心定位流程解耦为两个并行线程，避免传统的“渲染-定位”线性依赖造成的延迟瓶颈：

- **渲染线程（Render Thread）**：基于恒速 Kalman 滤波预测参考位姿，从该视角渲染参考图像与深度图，并反投影 N 个像素形成 3D **geo-anchors**（地理锚点）。仅渲染单一参考视图。
- **定位线程（Localization Thread）**：将实时视频帧与共享的参考视图进行特征级注册，采用**一对多（one-to-many）** 策略——多个位姿假设同时针对同一渲染视图优化，从而在无需多个参考视点的前提下扩展搜索范围。

#### ② 大规模合成数据集（百万级规模）

现有无人机数据集（University-1652、UAVD4L 等）存在规模小、缺少完整几何标注等问题。作者搭建了**AirSim-Cesium-Unreal Engine 模拟器**流程，自动生成百万级图像对：

- 覆盖 82 个区域、飞行总距离 650.3 km、RGB-D 对超过 110 万；
- 包含逐像素绝对深度、经重投影验证的精确 6-DoF 相机位姿；
- 涵盖多样化视觉条件（不同场景、天气、光照）和动态视角变化。

**关键论点**：通过精确的几何监督（深度+位姿），网络学习到的特征以稳定的 3D 几何为锚点，不依赖视角或光照的颜色外观，从而对真实数据实现零样本泛化。

#### ③ JNGO：联合神经引导随机-梯度优化器

针对无人机剧烈运动导致的标准优化器收敛失败问题，JNGO 分三个关键步骤：

- **旋转感知的假设生成**：针对无人机图像中旋转引起的像素位移远大于平移的特点，在俯仰角/偏航角方向采用各向异性均匀采样、在平移方向采用高斯扰动，生成 M=144 个初始位姿假设。
- **神经引导的并行精化**：使用 Levenberg-Marquardt（LM）优化器，在**粗-中-细三级特征金字塔**上并行优化每个假设，最小化特征级光度误差。

核心残差公式：

**r(j,ℓ) = f_q^ℓ(π(Kℓ, T̃⁻¹, P_Wj)) − f_r^ℓ(p_rj)**

即参考 3D 锚点投影到查询帧后所采样的查询特征与参考特征之间的差异。

更新规则：**(JᵀWJ + λI) Δξ = −JᵀWr**，经指数映射更新 SE(3) 位姿。

- **运动约束的假设选取**：将最终的基于特征的光度代价与 KF 预测位姿的 SE(3) 测地距离正则项相加，选取得分最低的假设作为最终位姿。

训练采用端到端方式，以参考锚点重投影误差作为几何监督（Barron 鲁棒损失，N=500 锚点）。

---

## 3. 实验设计

### 3.1 评估数据集

| 数据集 | 类型 | 场景内容 |
|---|---|---|
| SynthCity-6 | 合成 | 6 个 2km×2km 区域，60 条轨迹（54k 帧），覆盖多种天气和光照 |
| UAVScenes | 真实 | 51.6k 帧，AMtown、AM-valley、HKairport、HKisland 四个场景，含跨场景变化 |
| UAVD4L-2yr | 真实 | 8 条新轨迹（7.2k 帧），参考地图与实际场景相隔两年的季节/光照差异，提供厘米级 RTK-GPS 真值 |
| UAVD4L-SynTarget | 合成 | 基于 UAVD4L 场景，6 条轨迹（6k 帧），100+ 动态目标（车辆、行人），含 3D 地理坐标真值 |

### 3.2 对比方法

分为两大类：

- **混合方法**：结合帧间 VO 与绝对位姿修正。如 Render2ORB（ORB-SLAM3 + 1Hz Render-and-Compare 修正）、Render2RAFT（光流 + LoFTR + PnP）。
- **绝对定位方法**：逐帧进行绝对定位。如 PixLoc（特征直接对齐）、Render2Loc（渲染-比较 + PnP），并配备 LoFTR、ELoFTR、Aerial-MASt3R、RoMaV2 等特征匹配器。

### 3.3 评估指标

- 平移与旋转误差的中位数
- Recall@1/3/5（m, °）
- 完整率（Completeness）
- 定位频率（FPS）

---

## 4. 资源与算力

- **训练硬件**：8 块 NVIDIA RTX 4090 GPU
- **训练轮数**：30 epochs
- 训练数据规模：百万级；优化器：Adam，学习率 1e-3
- **文中未明确给出**：

  - 总训练时长（多少小时/天）；
  - 合成数据集的渲染耗时；
  - 推理时 Jetson Orin 的功耗与具体型号规格未提及。

---

## 5. 实验数量与充分性

实验矩阵可总结为：

- **自身定位任务**：3 个数据集（SynthCity-6、UAVScenes、UAVD4L-2yr）× 2 类方法中共 7 种基线；
- **目标地理定位任务**：2 个数据集（Multi-Target-Syn 和 Single-Target-Real），对比 4 种代表性方法；
- **消融实验**：两个维度共 6 组配置——**系统组件消融** 验证了领域特定训练、旋转感知假设生成、运动正则化各自的贡献，**训练数据消融** 则对比了本文数据集与 MegaDepth、无光照变化合成数据的差异。

### 充分性评估

**充分之处**：

- 覆盖合成与真实场景、不同季节光照差异，体现零样本泛化能力；
- 消融设计逻辑递进，每项组件单独验证增量贡献；
- 包含嵌入式平台（Jetson Orin）的测速，证明计算效率在边缘设备上可行。

**可进一步改进**：

- 未与现有基于 GNSS+VIO 的工业级方法做对比；
- 对动态目标的评估仅限单个或少数目标的简单场景，缺乏多目标、遮挡交互的场景验证；
- 对极端天气（浓雾、暴雨）的实测未见。

**总体评价**：实验设计相对完整、层次清晰，对比方法多样，但仍存在极端条件下验证不足等问题。

---

## 6. 主要结论与发现

1. 提出的 PiLoT 在三个数据集上的表现优于所有对比方法。在真实数据集 UAVD4L-2yr 上取得了 0.92m/0.89° 的最低中位误差，比最强的匹配型基线方法有可观的优势（如 Render2Loc 在此数据集上的 LoFTR 为 1.08m/0.95°，RoMaV2 为 1.05m/0.97°）。
2. 领域特定的合成数据训练至关重要：直接使用现成骨干网络加载到本文任务时，召回率不到 5%，而完成领域特定训练后，在 10m/10° 的大扰动条件下召回率提升至 84.3%，说明大幅度的初始扰动具有极强的破坏力。
3. 旋转感知假设生成与运动正则化显著增强了优化器在剧烈运动下的鲁棒性；
4. PiLoT 在 NVIDIA Jetson Orin 上运行速度超过 25 FPS（桌面 GPU 上可达 28 FPS），而像素级匹配方法通常不到 5 FPS，具有实时性优势。

---

## 7. 优点

以下几方面值得肯定：

1. **统一范式**：首次将 UAV 的自身定位与目标地理定位统一到同一 pixel-to-3D 注册框架，摆脱 GNSS/IMU 依赖，同时省去激光测距等硬件，降低系统复杂度。
2. **双线程架构设计巧妙**：通过渲染与定位的并行化打破了“渲染制约定位”的时序瓶颈；一对多策略以单参考视图支撑多假设并行优化，有效节省计算量。
3. **合成数据规模与质量并存**：百万级图像对加精确几何标注是模型零样本迁移成功的基础；数据的多光照、多天气、多视角设计充分覆盖了现实中的变化因素。
4. **工程完成度高**：CUDA 并行化的 LM 优化器已实际部署在 Jetson Orin 嵌入式平台上，验证了从学术研究到工程落地的可行性。
5. **零样本泛化能力强**：模型在合成数据训练后直接迁移到真实场景，无需微调，体现特征学习对几何结构的依赖优于对视角/光照外观的依赖。

---

## 8. 不足与局限

### 8.1 环境极端的退化
论文自述在浓雾等极端视觉条件下性能会下降。对暴雨、雪、沙尘等恶劣天气，以及夜间光线极弱的情况，未做系统性验证。

### 8.2 地图依赖（最大的适用性瓶颈）
系统需要预先存在高保真的地理参考 3D 地图（mesh/模型）。对尚未有此类数据的偏远地区或非城市环境，部署受限。论文提出未来向 DOM+DEM 扩展的方向，但本文尚未覆盖。

### 8.3 初始先验的依赖
系统假定已知首帧的粗略位姿先验。若该先验在无 GNSS 环境中也无法获得（误差超过 10m/10°），模型性能会显著下降，鲁棒性不足。

### 8.4 目标注册方式较为简化
目标地理定位实验以像素级点目标为主，未考虑目标存在 2D 包围框面积、高度估计误差、非刚性目标等情况，实际中需要结合目标检测的完整流程。

### 8.5 基线的可扩展性
PixLoc、Render2ORB 等基线仅在单一地图上完成微调，未系统评估其在不同地图类型上的泛化差异对公平性的影响；部分高效匹配器（ELoFTR、RoMaV2）在复杂真实场景下精度虽高，耗时却居于劣势，定位精度与运行效率在各类对比中优势不完全一致。

---

（完）
