---
title: "ChronoFlow Policy: Unifying Past-Future Interaction Flow in Visuomotor Policy Learning"
title_zh: ChronoFlow Policy：统一过去与未来交互流的视觉运动策略学习
authors: "Bokai Lin, Yifu Xu, Xinyu Zhan, Hongjie Fang, Jialin Tian, Fu-Cheng Zhang, Yong-Lu Li, Cewu Lu, Lixin Yang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/577.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于扩散模型的视觉运动策略，统一历史与未来交互动态的端到端学习
tldr: 针对现有视觉运动策略往往单独建模历史上下文或未来动态，缺乏统一时间表征刻画交互动态的问题，本文提出了ChronoFlow。该方法通过物体与夹爪的稀疏三维关键点捕捉过去、现在与未来的交互动态，并据此设计了基于扩散模型的ChronoFlow-Policy视觉运动策略。该工作将端到端视觉运动学习与未来预测相结合，使策略能像人一样基于经验与预期结果进行推理。在操控任务上的实验表明所提统一时序表征对策略学习具有显著增益。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 987, \"height\": 655}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 771, \"height\": 631}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 681, \"height\": 222}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 903, \"height\": 652}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 903, \"height\": 652}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 426, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 426, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 433, \"height\": 326}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 433, \"height\": 326}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 385, \"height\": 328}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 385, \"height\": 328}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-012.webp\", \"caption\": \"\", \"page\": 1, \"index\": 12, \"width\": 395, \"height\": 341}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-013.webp\", \"caption\": \"\", \"page\": 1, \"index\": 13, \"width\": 395, \"height\": 341}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-014.webp\", \"caption\": \"\", \"page\": 1, \"index\": 14, \"width\": 391, \"height\": 335}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-015.webp\", \"caption\": \"\", \"page\": 1, \"index\": 15, \"width\": 391, \"height\": 335}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-016.webp\", \"caption\": \"\", \"page\": 1, \"index\": 16, \"width\": 1077, \"height\": 212}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-017.webp\", \"caption\": \"\", \"page\": 1, \"index\": 17, \"width\": 449, \"height\": 325}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-018.webp\", \"caption\": \"\", \"page\": 1, \"index\": 18, \"width\": 385, \"height\": 328}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-019.webp\", \"caption\": \"\", \"page\": 1, \"index\": 19, \"width\": 391, \"height\": 335}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-020.webp\", \"caption\": \"\", \"page\": 1, \"index\": 20, \"width\": 568, \"height\": 562}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-021.webp\", \"caption\": \"\", \"page\": 1, \"index\": 21, \"width\": 584, \"height\": 402}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-022.webp\", \"caption\": \"\", \"page\": 1, \"index\": 22, \"width\": 644, \"height\": 698}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-023.webp\", \"caption\": \"\", \"page\": 1, \"index\": 23, \"width\": 800, \"height\": 544}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-024.webp\", \"caption\": \"\", \"page\": 1, \"index\": 24, \"width\": 566, \"height\": 485}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-025.webp\", \"caption\": \"\", \"page\": 1, \"index\": 25, \"width\": 682, \"height\": 222}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-026.webp\", \"caption\": \"\", \"page\": 1, \"index\": 26, \"width\": 644, \"height\": 342}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-027.webp\", \"caption\": \"\", \"page\": 1, \"index\": 27, \"width\": 389, \"height\": 345}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-028.webp\", \"caption\": \"\", \"page\": 6, \"index\": 28, \"width\": 771, \"height\": 528}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-029.webp\", \"caption\": \"\", \"page\": 6, \"index\": 29, \"width\": 772, \"height\": 528}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-030.webp\", \"caption\": \"\", \"page\": 6, \"index\": 30, \"width\": 711, \"height\": 599}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-031.webp\", \"caption\": \"\", \"page\": 6, \"index\": 31, \"width\": 706, \"height\": 598}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-032.webp\", \"caption\": \"\", \"page\": 6, \"index\": 32, \"width\": 715, \"height\": 605}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-033.webp\", \"caption\": \"\", \"page\": 6, \"index\": 33, \"width\": 723, \"height\": 607}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-034.webp\", \"caption\": \"\", \"page\": 6, \"index\": 34, \"width\": 736, \"height\": 610}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-035.webp\", \"caption\": \"\", \"page\": 12, \"index\": 35, \"width\": 455, \"height\": 325}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-036.webp\", \"caption\": \"\", \"page\": 12, \"index\": 36, \"width\": 452, \"height\": 326}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-037.webp\", \"caption\": \"\", \"page\": 12, \"index\": 37, \"width\": 426, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-038.webp\", \"caption\": \"\", \"page\": 12, \"index\": 38, \"width\": 433, \"height\": 326}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-039.webp\", \"caption\": \"\", \"page\": 12, \"index\": 39, \"width\": 987, \"height\": 655}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-040.webp\", \"caption\": \"\", \"page\": 12, \"index\": 40, \"width\": 389, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-041.webp\", \"caption\": \"\", \"page\": 12, \"index\": 41, \"width\": 385, \"height\": 325}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-042.webp\", \"caption\": \"\", \"page\": 12, \"index\": 42, \"width\": 385, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-043.webp\", \"caption\": \"\", \"page\": 12, \"index\": 43, \"width\": 397, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-044.webp\", \"caption\": \"\", \"page\": 12, \"index\": 44, \"width\": 395, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-045.webp\", \"caption\": \"\", \"page\": 12, \"index\": 45, \"width\": 835, \"height\": 648}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-046.webp\", \"caption\": \"\", \"page\": 12, \"index\": 46, \"width\": 385, \"height\": 328}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-047.webp\", \"caption\": \"\", \"page\": 12, \"index\": 47, \"width\": 395, \"height\": 341}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-048.webp\", \"caption\": \"\", \"page\": 12, \"index\": 48, \"width\": 391, \"height\": 335}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-049.webp\", \"caption\": \"\", \"page\": 12, \"index\": 49, \"width\": 771, \"height\": 631}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-050.webp\", \"caption\": \"\", \"page\": 12, \"index\": 50, \"width\": 728, \"height\": 593}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-051.webp\", \"caption\": \"\", \"page\": 12, \"index\": 51, \"width\": 720, \"height\": 560}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-052.webp\", \"caption\": \"\", \"page\": 12, \"index\": 52, \"width\": 726, \"height\": 563}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-053.webp\", \"caption\": \"\", \"page\": 12, \"index\": 53, \"width\": 1536, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-054.webp\", \"caption\": \"\", \"page\": 15, \"index\": 54, \"width\": 471, \"height\": 454}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-04744093a5871fb61a639365/fig-055.webp\", \"caption\": \"\", \"page\": 15, \"index\": 55, \"width\": 670, \"height\": 636}]"
motivation: 现有视觉运动策略单独建模历史或未来，缺少统一的交互动态时序表征。
method: 提出ChronoFlow统一时序表征及基于扩散模型的ChronoFlow-Policy，端到端融合过去经验与未来预测。
result: 在需要历史与未来推理的操控任务上取得优于单时序建模基线的策略性能。
conclusion: ChronoFlow 为端到端视觉运动操控提供了融合过去与未来的统一时序表征框架。
---

## Abstract
Visual signals play a crucial role in policy learning by en-abling models to capture object motion and interaction dynamics. Just ashumans reason about actions using both past experience and anticipatedoutcomes, effective policies should integrate past interactions with futurepredictions. However, existing visuomotor policies typically model eitherhistorical context or future dynamics in isolation, lacking a unified tem-poral representation of interaction dynamics. In this work, we introduceChronoFlow, a temporally unified representation that captures past,current, and future interaction dynamics through sparse 3D keypointsof both objects and the gripper. Based on this representation, we proposeChronoFlow-Policy, a diffusion-based visuomotor policy that jointlylearns ChronoFlow and action sequences through a co-training objective.Experiments on 14 simulated tasks and 5 real-world manipulation tasksdemonstrate that ChronoFlow-Policy consistently outperforms strongdiffusion-policy baselines and improves robustness in long-horizon andnon-Markovian manipulation scenarios. Code and models will be releasedat https://github.com/The-kamisato-Sii/ChronoFlow-Policy.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze an academic paper about ChronoFlow-Policy, which is about unifying past-current-future interaction flow in visuomotor policy learning. Let me carefully read through the paper content and generate a structured summary in Chinese following the specified outline.

Let me organize my analysis:

1. **Core Problem & Motivation**: The paper addresses the limitation of existing visuomotor policies that model either historical context or future dynamics in isolation, lacking a unified temporal representation of interaction dynamics.

2. **Methodology**: 
   - ChronoFlow: temporally unified representation using sparse 3D keypoints of objects and gripper
   - ChronoFlow-Policy: diffusion-based policy with co-training objective
   - Key components: ChronoFlow Encoder, Joint Diffusion Denoising, ChronoFlow Decoder, Action Decoder
   - Loss function: L = Laction + λCF * LCF

3. **Experiments**:
   - Simulation: MetaWorld (7 tasks), RoboTwin 2.0 (7 tasks)
   - Real-world: 5 tasks (Prepare Breakfast, Fold Towel, Pour Ball, Swap-Easy, Swap-Hard)
   - Baselines: DP3, RISE, HistRISE, 3D-FDP, MBA
   - 50 expert demonstrations per real-world task
   - 15-18 trials per real-world task evaluation

4. **Resources**:
   - Real-world: NVIDIA RTX 3090 workstation
   - Single Flexiv Rizon robotic arm with Robotiq 2F-85 gripper
   - Intel RealSense D415 RGB-D camera
   - TAPIP3D for tracking
   - Asynchronous inference at 5.82 Hz

5. **Experimental Sufficiency**:
   - Multiple ablation studies on Fold Towel
   - Various baseline comparisons
   - Analysis of historical vs future contributions

6. **Conclusions**:
   - ChronoFlow effectively models past-current-future interactions
   - Significant improvements in non-Markovian, long-horizon, deformable tasks
   - Outperforms DP3, RISE, HistRISE, 3D-FDP, MBA

7. **Highlights**:
   - Unified temporal representation
   - Interaction-centric keypoints
   - Asynchronous tracking for real-time performance

8. **Limitations**:
   - Reliance on 3D tracking which can have noise, drift, missing keypoints
   - Severe occlusion can degrade performance
   - Need for uncertainty-aware tracking

Let me write this out in Chinese Markdown format.</think>

# ChronoFlow-Policy 论文深度总结

## 1. 核心问题与研究动机

- **核心问题**：现有视觉运动策略（visuomotor policy）在处理机器人操控任务时，要么单独建模历史上下文（如 HistRISE、TraceVLA），要么单独建模未来动力学（如 MBA、3D-FDP），**缺乏统一的时序表征**来刻画"过去—现在—未来"三阶段的交互动态。
- **仿生动机**：人类在操控任务中会同时调用三类信息——过去做过什么（Q1）、当前应如何行动（Q2）、未来物体将如何变化（Q3）。当前策略无法同时建模这三者，导致在非马尔可夫、长时序、形变物体等场景下表现受限。
- **关键洞察**：将历史经验与未来预期结合，形成"世界—动作模型"（world-action model）的统一学习框架，是提升策略泛化与鲁棒性的关键。

## 2. 方法论

### 2.1 ChronoFlow 表征
- **定义**：在每个时刻 t，使用**稀疏 3D 关键点**同时表示夹爪与任务相关物体：
  - 夹爪关键点 $P_t^g \in \mathbb{R}^{N_g \times 3}$：预先定义在夹爪几何上，通过 TCP 位姿刚体变换获得，保证时间一致性。
  - 物体关键点 $P_t^o \in \mathbb{R}^{N_o \times 3}$：先用 SAM-2 进行 3D 分割，再通过最远点采样（FPS）获取候选点，最后用 TAPIP3D 进行 3D 点跟踪，得到时序一致的物体轨迹。
- **统一性**：将夹爪流与物体流在共享空间坐标系下联合表示，既能反映接触动态，也能保留任务相关的几何结构，过滤冗余场景运动。

### 2.2 ChronoFlow-Policy 框架
- **整体架构**：基于扩散模型（DiT 或 Unet1D）的视觉运动策略，将策略分解为：
  $$\pi(a_{t:t+H} | o_t, \mathcal{P}_{:t}) = \pi_\phi(a_{t:t+H} | P_{t:t+H}) \, \pi_\theta(P_{t:t+H} | o_t, \mathcal{P}_{:t})$$
  即先预测未来交互轨迹，再解码动作。

- **关键模块**：
  1. **Observation Encoder**：用 PointNet（仿真）/稀疏 3D 编码器（真实）处理点云，可融合本体感知 MLP。
  2. **ChronoFlow Encoder**：通过多头交叉注意力（MCA），将历史 ChronoFlow $P_{:t}$ 与加噪的未来 ChronoFlow $P^k_{t:t+H}$ 编码为 ChronoFlow tokens $Z^k_t$，每个 token 对应一个夹爪或物体关键点。
  3. **Joint Diffusion Denoising**：在 ChronoFlow token 空间进行条件去噪，逐步得到干净交互 tokens $Z^0_t$，作为共享隐式表征。
  4. **ChronoFlow Decoder**：轻量 Transformer 解码器，从 $Z^0_t$ 解码未来 ChronoFlow 轨迹 $\hat{P}_{t:t+H}$。
  5. **Action Decoder**：将 $Z^0_t$ 与近似轨迹 $\tilde{P}_{t:t+H}$ 拼接，输入动作解码器预测动作序列 $\hat{a}_{t:t+H}$。

- **训练目标**：
  $$\mathcal{L} = \mathcal{L}_{\text{action}} + \lambda_{CF} \mathcal{L}_{CF}$$
  其中 $\mathcal{L}_{CF}$ 为标准扩散去噪损失（监督 ChronoFlow 轨迹），$\mathcal{L}_{\text{action}}$ 为动作 MSE 损失（在中间加噪状态上计算，避免完整去噪开销）。

- **推理流程**：使用 TAPIP3D **异步**追踪历史 ChronoFlow，避免 3D 跟踪成为运行时瓶颈（同步 0.93 Hz → 异步 5.82 Hz）。

## 3. 实验设计

### 3.1 仿真基准
- **MetaWorld**：单臂 MuJoCo 操控基准，7 个任务（Shelf Place、Bin Picking、Box Close、Peg Insert Side、Hand Insert、Soccer、Sweep Into）。
- **RoboTwin 2.0**：双臂仿真框架，7 个任务（Beat Block Hammer、Handover Microphone、Click Bell、Move Playingcard Away、Place Empty Cup、Click Alarmclock、Place Dual Bottles）。
- **协议**：动作预测窗口 H=8，观测窗口=1，执行前 4 步（receding horizon）；MetaWorld 用 3 个 seed 评估取前 5 均值，RoboTwin 用 100 episodes 取前 3 均值。

### 3.2 真实世界任务
- **5 个任务**（Flexiv Rizon 机械臂 + Robotiq 2F-85 夹爪 + Intel RealSense D415 顶视 RGB-D 相机）：
  - Prepare Breakfast（长时序）
  - Fold Towel（软体形变）
  - Pour Ball（非马尔可夫，双阶段）
  - Swap-Easy（非马尔可夫，三阶段）
  - Swap-Hard（非马尔可夫，三阶段，最具挑战）
- **数据采集**：每任务 50 条触觉遥操作示教。
- **评估指标**：单次执行成功率（one-attempt success rate），按阶段（Stage I/II/III）细分；Swap-Hard 评估 18 次，其余任务 15 次。

### 3.3 对比方法
- **基线策略**：DP3、RISE（动作监督，3D 点云编码）
- **历史增强**：HistDP3、HistRISE
- **未来预测**：3D-FDP（稠密场景流）、MBA（物体位姿轨迹）
- **消融变体**：CFP w/o past（移除历史 ChronoFlow，仅用未来监督）

## 4. 资源与算力

- **真实实验平台**：NVIDIA RTX 3090 工作站进行训练与评估；单 RGB-D 相机，无额外 2D 视觉输入。
- **推理频率**：异步追踪下 5.82 Hz，同步追踪仅 0.93 Hz。
- **论文未明确披露**：训练总时长、GPU 数量（仅单卡 RTX 3090）、各任务的训练 epoch 数、仿真与真实实验分别的总训练时间。
- **3D 追踪依赖**：使用 TAPIP3D（异步）+ D4RT（训练时提取历史轨迹）。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 14 个仿真任务（MetaWorld 7 + RoboTwin 2.0 7）
  - 5 个真实任务，每任务 2-3 个阶段细分评估
  - Fold Towel 上 5 项消融实验（w/o ChronoFlow、w/o ObjPoints、w/o GriPoints、w/o CF-Sampling、w/o CF-Aug）
  - 推理频率对比表（TAPIP3D 同步/异步）
- **客观性**：所有方法在相同 3D 点云观测、相同训练设置下对比；真实任务使用相同的固定测试初始化。
- **充分性评估**：仿真任务覆盖单/双臂、马尔可夫/非马尔可夫多种场景；真实任务针对三大挑战（非马尔可夫、长时序、形变）专门设计；消融实验覆盖了关键模块；但真实任务每任务仅 15-18 次 trial，统计稳定性可能有限。

## 6. 主要结论与发现

- **Q1（历史 ChronoFlow 改善非马尔可夫任务）**：在 Swap-Easy、Swap-Hard 上，CFP 保持各阶段稳定性能（如 Swap-Easy 三阶段均为 93%），而无历史建模的基线（RISE、3D-FDP、CFP w/o past）在后期阶段性能骤降。
- **Q2（未来交互建模改善长时序任务）**：Prepare Breakfast 上 CFP 两阶段均达 93%/80%，优于 RISE（73%/53%）和 MBA（87%/73%）。
- **Q3（ChronoFlow 处理形变物体）**：Fold Towel Stage II 维持 87%，显著优于 RISE（40%）和 MBA（依赖位姿，对形变不鲁棒）。
- **整体增益**：相比基线 DP3/RISE，仿真提升 +32.5%，真实提升 +35.3%。
- **消融发现**：
  - 物体流对形变跟踪贡献最大（移除后 87% → 47%）
  - 随机关键点采样对空间覆盖至关重要（移除后 87% → 27%）
  - 空间抖动增强是真实部署稳定的**关键**（移除后 Stage II 暴跌至 6%）

## 7. 方法与实验设计亮点

- **统一时序表征**：首次将过去/现在/未来三阶段统一为单一稀疏关键点流表示，避免双流/三流分离建模的冗余与不一致。
- **交互中心设计**：聚焦夹爪—物体关键点，过滤场景冗余运动，更适合接触密集的操控任务。
- **稀疏 + 紧凑**：相比稠密场景流，ChronoFlow 紧凑、可解释且与 3D 点跟踪技术栈兼容。
- **异步追踪流水线**：通过异步 TAPIP3D 跟踪避免运行时瓶颈，提升真实部署效率约 6 倍。
- **架构通用性**：兼容 Unet1D 与 DiT 两种扩散骨干，仿真与真实均可应用。
- **任务设计精心**：将每个真实任务分解为多阶段进行细粒度评估，便于诊断历史与未来建模的具体贡献。

## 8. 不足与局限

- **3D 跟踪的脆弱性**：方法依赖 SAM-2 分割与 TAPIP3D 点跟踪，论文明确承认存在噪声、漂移、关键点缺失等问题；在严重遮挡或长时间跟踪失败时性能可能下降。
- **真实实验统计规模有限**：每任务 15-18 次 trial，Swap-Hard 等高难度任务的指标稳定性可能受偶然性影响。
- **算力信息不完整**：未公布训练时长、GPU 数量（仅提到单卡 RTX 3090）、各任务的 epoch 总数；仿真与真实实验的总计算开销不透明。
- **历史建模的边界**：CFP w/o past 在某些任务（如 Swap-Hard Stage III）仍优于部分基线，但整体仍依赖历史，存在历史长度敏感性，但未系统分析。
- **形变任务的物体依赖**：ChronoFlow 对 Fold Towel 的优势来源于物体关键点跟踪，但若物体初始分割失败或形变超出跟踪能力（如多物体交互、严重自遮挡），表示可能失效。
- **基线覆盖**：缺少与最新的基于 VLA（如 TraceVLA、CronusVLA）的对比，以及缺少与世界动作模型（如 UWM、DreamZero）的直接基准；这些方法在标题中被提及但未纳入实验。
- **应用范围**：当前实验仅使用单 RGB-D 相机与单一机械臂，对多视角、多臂协作等场景的扩展性未验证。

（完）
