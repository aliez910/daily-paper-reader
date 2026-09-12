---
title: Grasp-Oriented Non-Prehensile Manipulation via Learning a Graspability Field
title_zh: 面向抓取目标的非抓握式操控：通过学习可抓取性场实现闭环优化
authors: "Licheng Zhong, Gim Hee Lee"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/1648.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 基于可抓取性场的闭环非抓握式机器人操控与抓取准备
tldr: 针对现有非抓握式操控方法通常需要预定义目标物体位姿、而实际物体具有多种可抓取构型难以预先指定的局限，本文将该问题重新定义为面向以物体为中心的可抓取性目标优化。文章通过合成抓取构建可抓取集合，并定义衡量构型适合度的可抓取性场。该标量场为强化学习提供稠密学习信号，并决定操控何时终止，从而形成面向机器人抓取准备的闭环操控流程。该工作对机器人操控任务与控制具有方法贡献。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-010.webp\", \"caption\": \"\", \"page\": 2, \"index\": 10, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-011.webp\", \"caption\": \"\", \"page\": 2, \"index\": 11, \"width\": 453, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 395, \"height\": 312}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-013.webp\", \"caption\": \"\", \"page\": 5, \"index\": 13, \"width\": 563, \"height\": 563}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-014.webp\", \"caption\": \"\", \"page\": 5, \"index\": 14, \"width\": 348, \"height\": 348}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-015.webp\", \"caption\": \"\", \"page\": 10, \"index\": 15, \"width\": 1832, \"height\": 1207}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-016.webp\", \"caption\": \"\", \"page\": 10, \"index\": 16, \"width\": 1083, \"height\": 697}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-017.webp\", \"caption\": \"\", \"page\": 10, \"index\": 17, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-018.webp\", \"caption\": \"\", \"page\": 10, \"index\": 18, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-019.webp\", \"caption\": \"\", \"page\": 10, \"index\": 19, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-020.webp\", \"caption\": \"\", \"page\": 10, \"index\": 20, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-021.webp\", \"caption\": \"\", \"page\": 10, \"index\": 21, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-022.webp\", \"caption\": \"\", \"page\": 10, \"index\": 22, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-023.webp\", \"caption\": \"\", \"page\": 10, \"index\": 23, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-024.webp\", \"caption\": \"\", \"page\": 10, \"index\": 24, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-025.webp\", \"caption\": \"\", \"page\": 10, \"index\": 25, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-026.webp\", \"caption\": \"\", \"page\": 10, \"index\": 26, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-027.webp\", \"caption\": \"\", \"page\": 12, \"index\": 27, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-028.webp\", \"caption\": \"\", \"page\": 12, \"index\": 28, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-029.webp\", \"caption\": \"\", \"page\": 12, \"index\": 29, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-030.webp\", \"caption\": \"\", \"page\": 12, \"index\": 30, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-031.webp\", \"caption\": \"\", \"page\": 12, \"index\": 31, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-032.webp\", \"caption\": \"\", \"page\": 12, \"index\": 32, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-033.webp\", \"caption\": \"\", \"page\": 12, \"index\": 33, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-034.webp\", \"caption\": \"\", \"page\": 12, \"index\": 34, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-035.webp\", \"caption\": \"\", \"page\": 12, \"index\": 35, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-036.webp\", \"caption\": \"\", \"page\": 12, \"index\": 36, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-037.webp\", \"caption\": \"\", \"page\": 12, \"index\": 37, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-038.webp\", \"caption\": \"\", \"page\": 12, \"index\": 38, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-039.webp\", \"caption\": \"\", \"page\": 12, \"index\": 39, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-040.webp\", \"caption\": \"\", \"page\": 12, \"index\": 40, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-041.webp\", \"caption\": \"\", \"page\": 12, \"index\": 41, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-042.webp\", \"caption\": \"\", \"page\": 12, \"index\": 42, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-043.webp\", \"caption\": \"\", \"page\": 12, \"index\": 43, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-044.webp\", \"caption\": \"\", \"page\": 12, \"index\": 44, \"width\": 640, \"height\": 378}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-045.webp\", \"caption\": \"\", \"page\": 12, \"index\": 45, \"width\": 369, \"height\": 369}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-046.webp\", \"caption\": \"\", \"page\": 12, \"index\": 46, \"width\": 369, \"height\": 369}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-047.webp\", \"caption\": \"\", \"page\": 13, \"index\": 47, \"width\": 4269, \"height\": 3200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8c7e28e4951c07712b264a54/fig-048.webp\", \"caption\": \"\", \"page\": 13, \"index\": 48, \"width\": 2317, \"height\": 1752}]"
motivation: 现有非抓握式操控依赖预定义目标位姿，难以应对物体多构型的实际场景。
method: 将非抓握式操控重构为可抓取性目标优化，引入可抓取性场为强化学习提供稠密信号与终止条件。
result: 实现了无需预定义位姿的闭环非抓握式操控，可作为抓取的有效准备步骤。
conclusion: 该方法为面向抓取的非抓握式机器人操控提供了一种通用、闭环的优化框架。
---

## Abstract
Non-prehensile manipulation is often used as a preparatory step for robotic grasping, yet existing approaches typically require a predefined target object pose. In practice, however, objects admit multiple graspable configurations and the desired pose is not known in advance. We reformulate non-prehensile manipulation for grasping as optimizing an object centric graspability objective rather than reaching a specific pose. We construct a graspable set from synthesized grasps and define a graspability field that measures how suitable an object configuration is for successful grasp execution. The scalar measure provides a dense learning signal for reinforcement learning and determines when to terminate manipulation. This yields a closed-loop manipulation-to-grasp pipeline driven by a single policy. Experiments in simulation and on a real robot show that the policy reliably reconfigures objects into graspable states and transitions to grasping without external planners or manually specified stopping conditions. The predicted graspability distance correlates with real world grasp success, which indicates that the learned representation captures grasp feasibility of object configurations.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper following a specific structure. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is "Grasp-Oriented Non-Prehensile Manipulation via Learning a Graspability Field" by Licheng Zhong and Gim Hee Lee from NUS, accepted at ECCV 2026.

Let me organize the summary according to the 8 required points.</think>

# 论文总结：面向抓取目标的非抓握式操控（GOMP）

## 1. 核心问题与研究动机

- **问题定位**：非抓握式操控（如推、滑动、重定向）常被用作机器人抓取前的准备步骤，但现有方法（如 CORN、DyWA）通常要求预先定义目标物体位姿，将操控问题形式化为"目标位姿到达"任务。
- **关键局限**：
  - 实际物体通常存在多种可抓取构型，单一目标位姿不能完整表征可抓取性；
  - 可抓取性在构型空间中具有多局部极大值，预定义目标可能远离最近的"可抓取盆地"，导致策略被迫将物体移开本已易于抓取的状态；
  - 位姿到达目标与"为抓取做准备"目标之间存在本质错配——前者优化几何相似性，后者优化抓取成功率。
- **核心论点**：抓取准备不是位姿调节任务，而是构型改善过程，策略应由"当前构型的可抓取程度"驱动，而非"距预定义位姿的距离"驱动。

## 2. 方法论

### 2.1 整体思路
将非抓握式操控重构为**以物体为中心的可抓取性目标优化**问题，学习一个**可抓取性场（Graspability Field）**，用同一信号同时驱动强化学习训练与操控—抓取切换决策。

### 2.2 可抓取集合构建（Sec. 4.1）
- 使用现成的抓取合成模型（如 SE(3)-DiffusionFields）从物体完整几何生成多个候选抓取；
- 通过固定垂直顶抓姿态并求逆变换，将每个抓取转换为参考物体位姿；
- 收集 G 个参考位姿，构成可抓取集合 **S_g = {ŝ_i^o}**；
- 注意：这些参考位姿仅用于训练阶段构造监督信号，不作为目标位姿输入策略。

### 2.3 可抓取性场定义（Sec. 4.2）
- **几何距离 D(s_o, ŝ_i^o)**：通过 K 个关键点变换后的平均欧氏距离衡量两个构型的几何差异（与机器人末端无关）；
- **锚定距离**：d_anchor(s_o) = min_i D(s_o, ŝ_i^o)，但硬最小导致不连续；
- **软聚合**：d_soft(s_o) = -τ · log Σ exp(-D/τ)，使距离光滑可微，τ→0 时逼近硬最小；
- **锚定项**：加入对前一步所选参考构型的距离惩罚 d̃ = d_soft + λ·D(s_o, ŝ_{i*}^o)，以稳定轨迹、避免在多个抓取模式间振荡；
- **解释**：该标量场定义在构型空间上，刻画物体当前状态对抓取的"适合度"，可视为潜在函数。

### 2.4 强化学习奖励设计（Sec. 4.3）
- 使用基于势函数的奖励塑形（potential-based shaping），保证最优策略不变；
- 势函数 Φ(s_o) = φ(d̃)，φ(d) = k₁·β^(k₂·d)；
- 即时奖励 r_t = γ·Φ(s_{t+1}) - Φ(s_t)，对构型向可抓取集合靠近的动作给予正奖励；
- 优势：稠密监督信号，无需在训练阶段实际执行抓取。

### 2.5 策略架构（GOMP，Sec. 4.4）
- 感知—控制架构，使用 CORN 的物体中心编码器（冻结前层，仅微调最后一层注意力层）；
- 学生策略通过 GRU 聚合时序信息以应对部分观测与遮挡；
- 同时输出三类预测：(a) 非抓握操控动作；(b) 可抓取性距离 d̂_t；(c) 终止时的抓取位姿；
- 训练采用**教师—学生框架**：先用 RL 训练教师策略，再在线蒸馏给学生；教师仅在训练中使用；
- 关键设计哲学：策略架构本身非方法核心，任何感知—动作网络均可嵌入；**贡献在于基于可抓取性的目标函数**。

### 2.6 操控—抓取切换准则（Sec. 4.5）
- 用归一化可抓取性距离 d̄_t = d̂_t / L（L 为包围盒对角线长度）实现尺度无关；
- 切换条件：当连续 K 步窗口内 d̄_{t:t+K} < ε 时，判定物体已处于可抓取区域，输出抓取位姿并执行抓取；
- 该准则无需外部规划器或手工停止条件，由策略自身决定。

## 3. 实验设计

### 3.1 仿真环境
- **平台**：NVIDIA IsaacSim + IsaacLab，Franka Emika Panda 平行爪；
- **数据集/物体**：从 DexGraspNet、GraspFactory、YCB 数据集手工挑选任务适配物体；
- **观测**：教师接收完整点云，学生接收部分点云（nvdiffrast 渲染）。

### 3.2 真实环境
- **硬件**：Franka Research 3 + 平行爪；
- **感知**：3 个 Intel RealSense D435IF RGB-D 相机，多视角深度融合为部分点云，去除工作空间框外与机器人点；
- **评估物体**：10 个几何、摩擦、刚度各异的目标物体（图 4），不使用任何标记或外部追踪；
- **基准**：每个物体 5 次挑战性初始构型，使固定轨迹直接抓取成功率仅 8%。

### 3.3 对比方法
仿真阶段对比：
1. **Pretrained Baseline**：CORN/DyWA 发布的预训练权重；
2. **Retrained Baseline**：在相同观测与动作空间下复现并重新训练；
3. **Multi-reference Oracle**：使用所有候选参考位姿，取最优结果（上限）；
4. **Nearest-reference Oracle**：每步使用最近参考位姿作为目标（公平上限）；
5. **GOMP（Teacher / Student）**：本文方法。

真实世界主要展示 GOMP 的操控—抓取全流程，无外部基准对比，但有"直接抓取基线"（8% 成功率）作为对照。

### 3.4 评估指标
- 仿真成功：位置误差 < 0.05 m、姿态误差 < 15°、线速度 < 0.01 m/s、角速度 < 0.1 rad/s；同时报告忽略速度阈值（仅几何）的结果；
- 真实世界：操控成功率（Manip.）、抓取成功率（Grasp）、总体成功率（Total）。

## 4. 资源与算力

- 文中明确提到：**教师策略 RL 训练在单块 NVIDIA RTX A6000 GPU 上进行**，15k 次迭代约 10 小时；之后又继续训练 10k 次迭代（带动作尺度课程）；
- 真实机器人部署使用 Franka Research 3 + 3 个 RealSense 相机；
- 仿真平台：IsaacSim / IsaacLab（GPU 加速并行训练，但未给出具体并行环境数与总算力规模）；
- **未明确给出**学生蒸馏阶段的总训练时长、批量大小、采样环境数等细节。

## 5. 实验数量与充分性

- **仿真非抓握操控评估**：Seen / Unseen 两组物体，使用 10 个参考构型；
- **真实世界操控—抓取**：10 个物体 × 5 次试验 = 50 次回合（表 2），区分操控成功与抓取成功；
- **可抓取性距离验证**：跨多个真实构型统计预测距离分布（图 6），验证单一阈值可有效分离可抓取/不可抓取状态；
- **消融实验（表 3）**：
  - 参考构型数量：1、3、5、8、10、15、20 个；
  - 距离公式：hard-min、soft-min 去掉锚定项；
- **总体充分性评价**：
  - 优点：覆盖仿真+真实、seen+unseen、消融多维度；
  - 局限：真实世界每个物体仅 5 次试验，统计置信度有限；未与多个真实世界 SOTA 操控方法做头对头对比；未提供大规模物体数据集结果。

## 6. 主要结论与发现

- **仿真定量结果（表 1）**：GOMP Teacher 在已见物体上成功率达 84.0%（4.6s），未见物体 77.9%（4.8s）；Student 分别为 75.5% / 68.1%，显著优于所有目标位姿基线（包括最近参考 oracle 上限 52.0%）；
- **真实世界结果（表 2）**：操控成功率 64%（32/50），抓取成功率 97%（31/32），总成功率 62%；唯一持续失败的物体是高度变形且光滑的 Snack；
- **可抓取性距离的有效性**：预测距离在真实构型上明显分离可抓取与不可抓取状态（图 6），支持单一阈值的切换准则；
- **消融发现**：
  - 10 个参考位姿是性能/效率的最佳平衡点，过多反而导致下降；
  - 即便仅 1 个参考位姿也具合理性能，说明方法并非简单退化为目标位姿到达；
  - 软聚合 + 锚定项优于 hard-min 与无锚定版本；
- **核心论断**：预测的可抓取性距离既能作为强化学习奖励，又能作为切换信号，且与真实抓取成功相关——表明该表征捕捉到了物体构型的"抓取可行性"。

## 7. 优点

- **问题重新形式化**：将"位姿到达"替换为"可抓取性优化"，解决了多构型物体与未知目标的关键错配；
- **统一信号设计**：单一标量同时承担奖励、终止准则与可抓取性度量三重角色，工程简洁且闭环；
- **不依赖外部规划器**：操控—抓取切换由策略自主决定，无需手工阈值或外部抓取规划；
- **软聚合 + 锚定项**：解决硬最小不连续问题，并防止多模式振荡；
- **教师—学生 + 在线蒸馏**：兼顾性能（教师见全状态）与可部署性（学生仅见部分点云）；
- **仿真 + 真实结合验证**：从定量对比到真实物体全流程都给出明确数据；
- **泛化证据**：在未见物体上仍保持显著优势，且可抓取性距离在真实构型上具良好判别力。

## 8. 不足与局限

- **真实试验规模有限**：每物体仅 5 次，难以做统计显著性分析；
- **缺少与多种真实世界 SOTA 操控方法的头对头对比**，仅与"直接抓取基线（8%）"对照；
- **物体多样性有限**：真实实验中高度变形（如 Snack）和极薄/光滑物体持续失败，方法在强变形物体上的适用性存疑；
- **参考构型依赖外部抓取合成模型**：合成质量直接决定可抓取集合的合理性；若合成器对某类物体失效，方法会受影响；
- **算力细节披露不全**：学生蒸馏时长、批量大小、并行环境数等未给出，复现成本难以估算；
- **安全机制简单**：依靠预设安全力限制终止，对强接触场景可能过早放弃；
- **抓取位姿生成仍较朴素**：依赖策略单独预测头，未与专门抓取网络集成，可能限制精细抓取质量；
- **速度阈值作为成功判据**带有一定主观性，不同阈值会改变对比公平性（论文同时报告了含/不含阈值的版本，但未深入分析敏感性）；
- **可抓取集合静态生成**：未考虑不同初始姿态下接触动力学对可达可抓取盆地的影响，存在"几何可抓取但动力学不可达"的隐性偏差。

（完）
