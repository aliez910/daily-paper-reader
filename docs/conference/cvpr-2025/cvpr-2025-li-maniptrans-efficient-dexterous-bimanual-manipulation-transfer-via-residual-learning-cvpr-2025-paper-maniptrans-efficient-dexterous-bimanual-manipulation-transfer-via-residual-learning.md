---
title: "ManipTrans: Efficient Dexterous Bimanual Manipulation Transfer via Residual Learning"
title_zh: "ManipTrans:基于残差学习的灵巧双手操控高效迁移"
authors: "Li, Kailin, Li, Puhao, Liu, Tengyu, Li, Yuyang, Huang, Siyuan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_ManipTrans_Efficient_Dexterous_Bimanual_Manipulation_Transfer_via_Residual_Learning_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 用于灵巧双手操控的模仿学习轨迹模仿器
tldr: "在灵巧机器人操控研究中,获取精确、大规模、类人化的双手操作序列数据十分困难。本文提出 ManipTrans,一种两阶段方法,用于将人类双手技能高效迁移到灵巧机器人手。该方法先预训练一个通用的轨迹模仿器来模仿人手运动,再在交互约束下微调一个残差模块,从而实现高效学习与复杂双手任务的准确执行。实验结果表明,ManipTrans 在多项复杂操控任务上优于已有基线。该工作为基于模仿学习的灵巧操控技能迁移提供了一条可扩展的路径。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1803, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1689, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1694, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 319, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 858, \"height\": 362, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 868, \"height\": 361, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 864, \"height\": 294, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 847, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-maniptrans-efficient-dexterous-bimanual-manipulation-transfer-via-residual-learning-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 847, \"height\": 113, \"label\": \"Table\"}]"
motivation: "灵巧双手操控任务缺乏精确且大规模的人类操作数据,传统方法难以高效迁移人类技能。"
method: "提出两阶段方法 ManipTrans,先预训练通用轨迹模仿器,再微调残差模块以适应交互约束。"
result: "实验显示该方法在多种复杂双手操控任务上超越已有基线,实现了更准确的执行效果。"
conclusion: 为基于模仿学习的灵巧操控技能跨平台迁移提供了一种高效且可扩展的解决方案。
---

## Abstract
Human hands play a central role in interacting, motivating increasing research in dexterous robotic manipulation. Data-driven embodied AI algorithms demand precise, large-scale, human-like manipulation sequences, which are challenging to obtain with conventional reinforcement learning or real-world teleoperation. To address this, we introduce ManipTrans, a novel two-stage method for efficiently transferring human bimanual skills to dexterous robotic hands in simulation. ManipTrans first pre-trains a generalist trajectory imitator to mimic hand motion, then fine-tunes a specific residual module under interaction constraints, enabling efficient learning and accurate execution of complex bimanual tasks. Experiments show that ManipTrans surpasses state-of-the-art methods in success rate, fidelity, and efficiency. Leveraging ManipTrans, we transfer multiple hand-object datasets to robotic hands, creating DexManipNet, a large-scale dataset featuring previously unexplored tasks like pen capping and bottle unscrewing. DexManipNet comprises 3.3K episodes of robotic manipulation and is easily extensible, facilitating further policy training for dexterous hands and enabling real-world deployments.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "ManipTrans: Efficient Dexterous Bimanual Manipulation Transfer via Residual Learning" organized by specific points. Let me analyze the paper content carefully and structure the response.

Key points to cover:
1. Core problem and motivation
2. Methodology - core ideas, technical details, formulas/algorithm flow
3. Experimental design - datasets, benchmarks, comparison methods
4. Resources and compute
5. Experiment count and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me extract relevant information from the paper:

**Core Problem:**
- Dexterous robotic manipulation research needs precise, large-scale, human-like manipulation data
- Traditional RL requires task-specific reward functions, limiting scalability
- Teleoperation is labor-intensive and embodiment-specific
- MoCap data has noise accumulation issues
- Morphological differences between human and robot hands make direct pose retargeting suboptimal
- Bimanual manipulation has high-dimensional action space
- Most prior work stops at single-hand grasping/lifting tasks

**Methodology:**
- Two-stage framework: 
  1. Pre-trained hand trajectory imitation model
  2. Residual module for interaction refinement
- Stage 1: Hand Trajectory Imitation
  - State includes τ^h and proprioception
  - Rewards: wrist tracking, finger imitation (with keypoint correspondence), smoothness
  - Training with RSI, early termination, curriculum learning
- Stage 2: Residual Learning
  - State expansion: object position, velocity, mass, gravity, BPS representation, distance, contact force
  - Residual actions: a = a^I + Δa^R
  - Rewards: object following, contact force
  - Training: relaxation mechanism (gravity, friction), curriculum learning
- MDP formulation with PPO

**Experiments:**
- Datasets: OakInk-V2 validation (~80 episodes), GRAB, FAOVR, ARCTIC for qualitative
- Metrics: Er, Et, Ej, Eft, SR
- Compared with: RL-Only, Retarget + Residual, Retarget-Only
- Qualitative comparison with QuasiSim
- Cross-embodiment: Shadow Hand, MANO, Inspire Hand, Allegro Hand
- Real-world deployment: 2 7-DoF Realman arms + Inspire Hands
- Ablations: tactile info (obs, reward, term), training strategy (gravity, friction, thresholds)
- Benchmark for DexManipNet with IBC, BET, DP-UNet, DP-Trans

**Compute Resources:**
- Personal computer with NVIDIA RTX 4090 GPU
- Intel i9-13900KF CPU
- 4096 simulated environments in Isaac Gym
- 60 fps time step
- ~15 minutes training for 60 frames (compared to QuasiSim's 40 hours)

**Main Conclusions:**
- Outperforms SOTA in success rate, fidelity, efficiency
- Generalizes across embodiments
- Feasible for real-world deployment
- DexManipNet has 3.3K episodes, 1.34M frames
- 600+ bimanual task sequences

**Strengths:**
- Two-stage decoupling improves efficiency
- No task-specific reward engineering needed
- Cross-embodiment generalizability
- Real-world deployment demonstration
- Large-scale dataset contribution

**Limitations:**
- Some MoCap sequences cannot be transferred due to:
  1. Excessive noise in interaction poses
  2. Insufficiently accurate object models (especially articulated)
- Insufficient future direction discussion

Let me write this in Chinese with proper markdown formatting.
</think>
# ManipTrans 论文总结

## 1. 核心问题与研究动机

- **数据匮乏问题**：数据驱动的具身智能算法需要**精确、大规模、类人化**的灵巧双手操作序列数据，而传统方法难以高效获取：
  - **强化学习（RL）** 依赖精心设计的任务特定奖励函数，可扩展性差，任务复杂度受限。
  - **远程遥操作** 劳动密集、成本高，且只能产出与特定硬件绑定的数据，缺少跨硬件泛化能力。
- **形态差异问题**：人-机器人手部形态差异巨大，**直接姿态重定位（pose retargeting）** 难以生成物理合理的动作。
- **MoCap 噪声问题**：动作捕捉数据在长序列、接触密集任务中误差累积严重，导致高精任务失败。
- **动作空间高维**：双手操控动作空间维度极高，使策略学习效率低下。
- **任务覆盖局限**：现有工作多停留在**单手抓取/举起**任务上，复杂双手任务（如拧瓶盖、套笔帽、装酒精灯）几乎未被探索。
- **核心目标**：将人类双手操作技能高效迁移到灵巧机器人手，在仿真中精确跟踪参考运动。

---

## 2. 方法论

### 2.1 整体框架：两阶段残差学习
将迁移过程解耦为**两个阶段**：
- **阶段一**：预训练**通用手部轨迹模仿器** πI，专注于手指运动模仿。
- **阶段二**：训练**残差模块** πR，在物理交互约束下对粗动作进行细化修正。

最终动作： **a_t = a_t^I + Δa_t^R**

### 2.2 问题形式化
- **MDP** 定义：S, A, T, R, γ；策略使用 PPO 训练。
- **参考轨迹**：人手 τ^h（腕部 6-DoF 姿态 + 速度 + MANO 关节位置）与物体 τ^o（6-DoF 姿态 + 速度）。
- **机器人动作**：PD 控制的目标关节位置 a^q ∈ R^K + 腕部 6-DoF 力 a^w ∈ R^6。

### 2.3 阶段一：手部轨迹模仿（Hand Trajectory Imitating）
- **状态**：s_t^I = {τ_t^h, s_t^prop}，含参考手轨迹 + 灵巧手本体感知（关节角、腕部位姿及其速度）。
- **奖励函数** r_t^I 由三部分组成：
  1. **腕部跟踪奖励** r^wrist：SE(3) 空间位姿差与速度差。
  2. **手指模仿奖励** r^finger（公式 1）：
     - $$r_t^{finger} = \sum_{f=1}^{F} w_f \cdot \exp(-\lambda_f \| j_t^{d_f} - j_t^{h_f} \|_2^2)$$
     - 手动选取 F=21 个机器人关键点对应 MANO 模型；**对拇指、食指、中指指腹赋予更高权重**，以缓解形态差异。
  3. **平滑性奖励** r^smooth：惩罚关节速度与力矩的乘积（能量项）。
- **训练策略**：
  - **参考状态初始化（RSI）+ 早停**：若 j^d 偏离阈值 ε_finger 则终止。
  - **课程学习**：ε_finger 从 6cm 衰减至 4cm。
  - 训练数据包括手部运动数据集 [14, 36, 60, 105, 131, 134, 141] 与插值合成数据；左右手镜像平衡。

### 2.4 阶段二：残差学习交互（Residual Learning for Interaction）
- **状态扩展** s_t^interact：
  - 物体位姿 p^o（相对腕部）、速度、质量 m^o、重力向量 G^o。
  - **BPS 表示**编码物体形状 [89]。
  - 关键点-物体距离 D(j^d, p^o)。
  - **接触力 C**（来自仿真器，作为触觉反馈）。
- **残差动作结合策略**：
  - 初始化为零均值高斯分布，**warm-up 策略**逐渐激活。
  - 输出被裁剪到机器人关节限位。
- **奖励函数** r_t^R = r_t^I + w_object · r^object + w_contact · r^contact：
  1. **物体跟踪奖励** r^object：仿真物体与参考轨迹的位置/速度差。
  2. **接触力奖励**（公式 2）：
     - $$r_t^{contact} = w_c \cdot \exp\left(-\lambda_c \sum_{f=1}^{F} C_t^{d_f} \cdot \mathbb{1}\left(D(j_t^{h_f}, p_t^{o \cdot o}) < \xi_c\right)\right)$$
     - 当 MoCap 中手-物距离小于阈值 ξ_c 时，鼓励产生接触力。
- **训练策略**：
  - **物理约束松弛机制**：早期设 G=0、Friction=高值，逐步恢复真实值。
  - **课程学习**：ε_object 从 90°/6cm 衰减至 30°/2cm。
  - **接触早停条件**：若 MoCap 显示稳定抓取但接触力为零，则终止 episode。

### 2.5 DexManipNet 数据集
- 基于 FAVOR [60] 与 OakInk-V2 [131] 转移生成。
- 使用 **Inspire Hand** 的 12-DoF 仿真配置。
- 包含 **61 个任务、3.3K episodes、1.34M 帧**，其中约 600 段双手任务。

---

## 3. 实验设计

### 3.1 数据集与场景
- **定量评估**：OakInk-V2 验证集（~80 episodes，4-20 秒，降采样 60fps；排除可变形或过大物体）；约一半为双手任务。
- **定性评估**：GRAB [105]、FAOVR [60]、ARCTIC [32]。
- **仿真环境**：Isaac Gym，4096 并行环境。

### 3.2 评估指标
- **Er**：平均每帧物体旋转误差（度）。
- **Et**：平均每帧物体平移误差（cm）。
- **Ej**：平均每关节位置误差（cm）。
- **Eft**：平均每指腹位置误差（cm）。
- **SR**：成功率（阈值 Er<30°, Et<3cm, Ej<8cm, Eft<6cm，双手任务更严格）。

### 3.3 对比方法
- **RL-Combined 类**（重新实现）：
  1. **Retarget-Only**：仅关键点对齐重定位，无学习。
  2. **RL-Only**：基于 PPO 从零训练 [27]。
  3. **Retarget + Residual**：在重定位动作上施加残差 [92]。
- **Optimization-Based 类**：
  4. **QuasiSim [70]**：基于定制准物理仿真器优化（仅定性比较，代码未开源）。

### 3.4 消融实验
- **触觉信息消融**（w/o C obs, w/o C reward, w/o C term）：在关灯等接触密集任务上。
- **训练策略消融**（w/o relax-gravity, w/o increased friction, w/o relax-thresholds）：在套笔帽等复杂任务上。

### 3.5 跨硬件泛化
- **Shadow Hand** (K=22)、**MANO** (K=22)、**Inspire Hand** (K=12)、**Allegro Hand** (K=16)；不调整超参数或奖励权重。

### 3.6 真实世界部署
- 2 × 7-DoF Realman 机械臂 + 升级版 Inspire Hand（带触觉传感器）。
- 通过指尖对齐拟合将 12-DoF 仿真动作映射到 6-DoF 真实硬件。

### 3.7 DexManipNet 基准
- 在**瓶子重排任务**上测试四种模仿学习方法：IBC [33]、BET [99]、DP-UNet [25]、DP-Trans [25]。

---

## 4. 资源与算力

- **硬件**：单台个人电脑，配备 **NVIDIA RTX 4090 GPU** + **Intel i9-13900KF CPU**。
- **仿真**：Isaac Gym 中并行 **4096 个环境**，时间步长 1/60s。
- **训练效率**：
  - 60 帧未见过的单手轨迹仅需 **~15 分钟** 训练即可获得鲁棒结果。
  - 对比 QuasiSim 需 **~40 小时** 优化。
- **未明确说明**：
  - 两阶段训练的总耗时（小时数或迭代数）。
  - DexManipNet 全量生成所需时间。
  - 真实世界部署实验的总训练 / 调参时长。

---

## 5. 实验数量与充分性

- **定量对比**：4 个评估指标 × 4 个方法 × 单/双手分组（Table 1）——多维度对比充分。
- **消融实验**：6 个消融变体（3 触觉 + 3 训练策略），覆盖关键设计选择。
- **跨硬件**：4 种不同 DoF（K=12, 16, 22）的灵巧手。
- **数据集验证**：4 个公开手-物交互数据集（OakInk-V2、GRAB、FAOVR、ARCTIC）进行定性测试。
- **下游基准**：4 种模仿学习方法在 DexManipNet 上的基准（Table 2）。
- **真实世界部署**：包括牙膏盖开启等多任务真实机器人测试。
- **客观性评价**：
  - **优点**：对比维度丰富、指标严格化（双手任务 SR 更严格）、包含 SOTA 与基线。
  - **不足**：
    - 真实世界部署缺少系统性定量评估（如成功率、错误率），主要是定性展示。
    - 触觉传感器在真实实验中虽安装但作用未充分量化。
    - RL-Combined 对比方法均为重新实现，可能与原作者结果有差异。
    - QuasiSim 因代码未开源无法直接定量比较。

---

## 6. 主要结论与发现

- **精度领先**：在所有评估指标上优于基线，单手 SR 58.1%、双手 SR 39.5%，显著高于 Retarget+Residual（47.8%/13.9%）。
- **效率大幅提升**：训练速度比 QuasiSim 快 **~160 倍**（15 分钟 vs 40 小时）。
- **跨硬件泛化**：在不修改超参数情况下，可适配 4 种不同 DoF 灵巧手。
- **真实可行性**：成功在真实机器人上演示"挤牙膏""装酒精灯"等复杂双手任务。
- **触觉与训练策略关键**：触觉信息（作为奖励/观测/终止条件）以及物理约束松弛（重力、摩擦、阈值课程学习）均对收敛速度和最终 SR 有显著贡献。
- **DexManipNet 价值**：3.3K episodes、1.34M 帧的双手操作数据为下游模仿学习提供了新基准；当前 SOTA 模仿学习方法在瓶重排任务上 SR 最高仅 18.44%，表明该领域仍有挑战。
- **任务覆盖广**：首次实现笔帽套合、瓶盖拧开、化学实验等**先前未探索**的双手任务。

---

## 7. 优点

- **解耦设计思想清晰**：将"手部形态差异"和"物体物理交互"分两阶段解决，避免传统方法中"既要形态对齐又要物理合规"的冲突。
- **数据效率高**：阶段一利用大规模手部运动数据预训练，无需昂贵任务数据；阶段二残差学习从接近零初始化开始，加速收敛。
- **无任务特定奖励工程**：奖励设计通用（腕部跟踪 + 手指模仿 + 物体跟踪 + 接触力），跨任务泛化能力强。
- **跨硬件、即插即用**：仅需建立人-机器人关键点对应关系，奖励权重和网络结构不需调整。
- **物理松弛课程学习**：在 Isaac Gym 中直接调节 G 与摩擦，避免了 QuasiSim 所需的自定义准物理仿真器。
- **触觉信息多用途利用**：接触力同时作为观测、奖励和早停条件，多方面促进稳定抓取。
- **大规模数据集贡献**：DexManipNet 在任务数量、bimanual 覆盖上明显超过 DexMimicGen [50]（60 演示 / 9 任务）。
- **真实世界部署验证**：从仿真到真实机械臂的整套链路完整。
- **公开网站** maniptrans.github.io 提供视频与代码。

---

## 8. 不足与局限

- **失败案例**：
  1. MoCap 数据噪声过大（交互位姿不准）时无法迁移。
  2. 物体模型（特别是铰接物体）不够准确，导致物理仿真失败。
- **数据筛选偏差**：验证集仅 ~80 episodes，从原始 OakInk-V2 人工筛选并排除可变形 / 过大物体，可能不反映完整任务分布。
- **真实世界评估不充分**：
  - 缺乏真实机器人上的定量成功率统计。
  - 12-DoF 仿真到 6-DoF 真实硬件的拟合依赖指尖对齐优化，未必能保持复杂抓取姿态。
  - 触觉传感器虽安装但其作用未量化。
- **方法对比局限**：
  - QuasiSim 缺少直接定量对比（代码未开源）。
  - RL 基线为作者重实现，可能与原作者结果有偏差。
  - 缺少与最新 RL 双手操控方法（如 [66, 68]）的直接比较。
- **形态差异处理有限**：仍依赖人工选择 21 个关键点对应，泛化到差异更大的手部（如四指 Allegro）时可能需要额外调整。
- **DexManipNet 下游表现不佳**：4 种模仿学习算法在瓶重排上 SR 均低于 20%，反映数据集生成质量与下游学习之间仍有差距，但论文未深入分析原因。
- **应用场景限制**：
  - 依赖 MoCap 数据的质量和可用性。
  - 仿真中物体模型依赖凸包 / BPS 近似，难以处理强非凸物体。
  - 主要针对静态桌面操作，未探索移动 / 全身操控。
- **安全与可靠性**：未讨论在真实世界中错误执行（如手-物碰撞、关节过载）的安全机制。

（完）
