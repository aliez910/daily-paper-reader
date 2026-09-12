---
title: "SegDiff: Segmented Trajectory Diffusion for Consistent and Adaptive Robot Manipulation"
title_zh: "SegDiff:用于一致自适应机器人操作的分段轨迹扩散方法"
authors: "Haidong Cao, Wenjun Cao, Quanhao Li, Sicheng Xie, Zhiying Du, Jiaqi Leng, Zuxuan Wu, Yu-Gang Jiang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/3744.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 闭环视觉运动模仿学习策略
tldr: "模仿学习通过观测到动作的映射使机器人从示教中获取操作技能,但连续动作预测存在误差累积,关键姿态方法又依赖外部规划器。本文提出SegDiff,一种将示教分解为关键姿态间运动分段并从当前状态预测连续轨迹的闭环视觉运动策略。该方法融合两种范式优势,实现一致且自适应的机器人操作,显著提升复杂任务的端到端视觉运动模仿学习效果,推动操作策略的实时部署。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-001.webp\", \"caption\": \"\", \"page\": 5, \"index\": 1, \"width\": 451, \"height\": 441}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 552, \"height\": 259}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-003.webp\", \"caption\": \"\", \"page\": 5, \"index\": 3, \"width\": 603, \"height\": 259}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-004.webp\", \"caption\": \"\", \"page\": 7, \"index\": 4, \"width\": 371, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-005.webp\", \"caption\": \"\", \"page\": 7, \"index\": 5, \"width\": 1159, \"height\": 446}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-006.webp\", \"caption\": \"\", \"page\": 7, \"index\": 6, \"width\": 1102, \"height\": 403}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-007.webp\", \"caption\": \"\", \"page\": 7, \"index\": 7, \"width\": 515, \"height\": 387}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-008.webp\", \"caption\": \"\", \"page\": 7, \"index\": 8, \"width\": 1172, \"height\": 403}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-009.webp\", \"caption\": \"\", \"page\": 8, \"index\": 9, \"width\": 443, \"height\": 456}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-010.webp\", \"caption\": \"\", \"page\": 8, \"index\": 10, \"width\": 371, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-011.webp\", \"caption\": \"\", \"page\": 12, \"index\": 11, \"width\": 2000, \"height\": 1125}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-012.webp\", \"caption\": \"\", \"page\": 12, \"index\": 12, \"width\": 1264, \"height\": 344}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-013.webp\", \"caption\": \"\", \"page\": 12, \"index\": 13, \"width\": 1216, \"height\": 712}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-014.webp\", \"caption\": \"\", \"page\": 12, \"index\": 14, \"width\": 1272, \"height\": 880}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-015.webp\", \"caption\": \"\", \"page\": 12, \"index\": 15, \"width\": 1280, \"height\": 688}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-13e7bb849c599bb47b4c1b44/fig-016.webp\", \"caption\": \"\", \"page\": 12, \"index\": 16, \"width\": 1216, \"height\": 816}]"
motivation: "现有模仿学习方法在连续动作预测与关键姿态规划之间存在权衡,难以兼顾实时性与多模态建模。"
method: "提出SegDiff闭环视觉运动策略,将示教分解为关键姿态间的运动段,结合扩散模型预测连续轨迹。"
result: "在多个机器人操作基准上实现一致且自适应的控制性能,优于单一范式的基线方法。"
conclusion: "为复杂机器人操作任务提供统一的闭环视觉运动模仿学习框架,推动端到端策略实用化。"
---

## Abstract
Imitation learning enables robots to acquire manipulationskills from demonstrations by mapping observations to actions. Existingapproaches predict either short-horizon continuous action sequences ordiscrete keyposes. However, continuous prediction methods suffer fromcompounding errors due to short prediction horizons and struggle withmulti-modal action distributions, whereas keypose-based methods ne-cessitate an external planner, constraining real-time applicability. Toaddress these challenges, we introduce SegDiff, a closed-loop visuomo-tor policy that integrates the strengths of both paradigms. SegDiff de-composes demonstrations into motion segments between keyposes andlearns to predict the continuous trajectory from the current state tothe next keypose, enabling long-horizon prediction with real-time refine-ment. Furthermore, we leverage the capability of diffusion models andDDIM inversion to propose a Dynamic Temporal Ensembling mecha-nism, which allows the policy to efficiently respond to dynamic environ-ments and mitigate discontinuities caused by inconsistent multi-modalsampling. SegDiff demonstrates significant performance gains over exist-ing approaches across various simulated and real-world scenarios, indi-cating its strong ability to reason over extended temporal dependencieswhile maintaining real-time adaptability and control stability.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "SegDiff: Segmented Trajectory Diffusion for Consistent and Adaptive Robot Manipulation" organized by specific points. Let me analyze the paper carefully and structure the response according to the 8 requested points.

Let me go through the paper content:

1. **Core problem and motivation**: 
- Imitation learning for robot manipulation
- Two existing paradigms: continuous action prediction (short horizon, compounding errors, struggles with multi-modal distributions) vs keypose prediction (discrete salient points, requires external planner, limited real-time adaptability)
- Need to combine advantages of both

2. **Methodology**:
- SegDiff: closed-loop visuomotor policy
- Segmented Trajectory Modeling (STM): decomposes demonstrations into motion segments between keyposes, learns to predict continuous trajectory from current state to next keypose
- Dynamic Temporal Ensembling (DTE) using DDIM inversion
- Training: uses diffusion model with sub-segments of fixed length L (interpolated using cubic spline for translation, SLERP for rotation)
- Keypose extraction follows PerAct: where gripper state changes or velocity approaches zero
- Inference follows Receding Horizon Control (RHC)
- Two candidates generated: τ_rand (from Gaussian noise) and τ_prior (from DDIM inversion of action buffer)
- Two RMSE metrics: d_valid (buffer validity) and d_mode (mode discrepancy)
- Threshold δ computed from training set DDIM inversion reconstruction error
- Three cases in DTE:
  - Buffer valid + mode consistent: η·τ_rand + (1-η)·b_t
  - Buffer valid + mode switch detected: η·τ_prior + (1-η)·b_t
  - Buffer invalid: τ_rand only

3. **Experiments**:
- Simulation: RLBench (10 representative tasks + full RLBench-60), RoboMimic (PH dataset, 3 tasks with varying demos 30-200)
- Real-world: 5 tasks (Cube, Flip Cup, Package, Banana, Screw Cap) on xArm7 with Intel RealSense D435i cameras
- Baselines: ACT, Diffusion Policy (DP), CoA, Octo, AWE
- Compared with/without temporal ensembling

4. **Resources**:
- GPU: RTX A6000 (single GPU mentioned)
- Real robot: xArm7 with gripper, 2 Intel RealSense D435i cameras
- Training duration: not explicitly mentioned
- Inference time: ~622ms (DP) vs ~656ms (SegDiff) on real robot

5. **Experiment quantity and sufficiency**:
- 10 RLBench tasks + 60 RLBench benchmark
- 3 RoboMimic tasks with 4 different demo counts
- 5 real-world tasks with 10 trials each
- Ablations: STM vs DP, DTE variants (RAND, INV, DTE), hyperparameter sensitivity (L, η, δ), efficiency analysis
- Results averaged over 3 random seeds

6. **Main conclusions**:
- SegDiff outperforms all baselines on RLBench (11.1% improvement, 30% over DP)
- Best on 9/10 tasks
- On RLBench-60: outperforms DP by 34%, CoA by 9%
- Better data efficiency on RoboMimic in low-demo regime
- Strong real-world performance especially in dynamic (Banana), multi-modal (Package), precise (Screw Cap) scenarios

7. **Strengths**:
- Novel combination of continuous and keypose paradigms
- DDIM inversion for buffer validation and refinement is elegant
- Comprehensive experiments across simulation and real-world
- Negligible computational overhead (~5.4%)
- Effective in handling multi-modal action distributions
- Robust to dynamic perturbations

8. **Limitations**:
- Dependency on pre-defined keyposes for segmenting demonstrations
- Keypose extraction follows PerAct's heuristic
- DTE shows no improvement in simulation (perturbation-free, monomodal trajectories)
- INV mode can hurt performance in deterministic tasks
- Limited to tasks where keyposes can be well-defined
- The paper mentions the limitation in conclusion: "incorporating automated or self-supervised keypose discovery would therefore be a promising direction"

Let me now write this in a structured Chinese summary following the requested format.</think>

# SegDiff 论文总结

## 一、论文核心问题与研究动机

- **背景**：模仿学习（Imitation Learning, IL）是机器人获取操作技能的主流范式，其中离线模仿学习（OIL）通过行为克隆（BC）从专家示教中直接学习视觉运动策略。
- **现有两大范式的局限**：
  - **连续动作预测方法**（如 Diffusion Policy, ACT）：采用滑动窗口预测短时动作序列，但因预测时域短容易产生**复合误差（compounding errors）**，且难以处理**多模态动作分布**（同一观测对应多个合法动作模式，模式平均会产生模糊/不安全动作）。
  - **关键姿态（Keypose）预测方法**（如 PerAct, RVT）：聚焦离散关键点（如抓取位姿），但**依赖外部路径规划器**、采用开环控制，限制实时适应性。
- **已有混合方法**（如 ChainedDiffuser, CoA）多采用多阶段架构，存在推理延迟高、模块间误差传递、难以处理多模态等问题。
- **本文目标**：设计一个闭环视觉运动策略，融合连续预测与关键姿态约束的优势，实现长时域推理、实时适应性与动作模式一致性。

---

## 二、方法论

### 2.1 整体框架（SegDiff）

- 端到端的闭环视觉运动策略，基于扩散模型。
- 两大核心组件：
  1. **分段轨迹建模（Segmented Trajectory Modeling, STM）**：以关键姿态为预测锚点。
  2. **动态时间集成（Dynamic Temporal Ensembling, DTE）**：利用 DDIM 反演实时校验与修正动作缓存。

### 2.2 分段轨迹建模（STM）

- **关键姿态提取**（沿用 PerAct 启发式）：定义为夹爪开/闭状态变化或末端执行器速度趋于零的位姿，并将末端动作 $a_T$ 强制纳入关键姿态集合。
- **轨迹分段**：给定示教轨迹 $\{a_1, a_2, ..., a_T\}$ 与关键姿态 $\{a_{k_1}, ..., a_{k_n}\}$，在任意时刻 $t$（$k_{m-1} \le t < k_m$）构造子轨迹 $a_{t:k_m}$，从当前状态延伸到下一个关键姿态。
- **变长处理**：所有子轨迹通过**三次样条插值（平移）+ 球面线性插值 SLERP（旋转）** 归一化为固定长度 $L$。
- **训练目标**：标准扩散策略损失：
  $$L_{\text{SegDiff}} = \mathbb{E}_{\tilde{a}^{(t,k_m)}, \epsilon, k}\left[\left\|\epsilon - \epsilon_\theta(\tilde{a}^{(t,k_m)}, k, o_{t-h:t}, s_t)\right\|^2\right]$$
- **核心优势**：训练目标引导模型聚焦任务关键状态，同时保持对中间连续动作的理解，从根本上缓解复合误差。

### 2.3 动态时间集成（DTE）推理机制

- **推理范式**：采用 Receding Horizon Control (RHC)，每步执行前 $n_{exec}$ 个动作，剩余存入动作缓存 $b_t$。
- **关键性质**：由于 STM 设计，缓存 $b_t$ 与新预测轨迹 $\tau_{t+1}$ 共享同一起点并终止于同一关键姿态，便于比对与集成。
- **生成两个候选**：
  - $\tau_{\text{rand}}$：从标准高斯噪声采样（响应性最强）。
  - $\tau_{\text{prior}}$：先对缓存 $b_t$ 进行 **DDIM 反演** 得到噪声 $\epsilon_{\text{prior}}$，再在新观测条件下去噪生成（保持动作模式一致性）。
- **两个 RMSE 度量**：
  - $d_{\text{valid}} = \text{RMSE}(b_t, \tau_{\text{prior}})$：衡量缓存是否仍可行。
  - $d_{\text{mode}} = \text{RMSE}(\tau_{\text{rand}}, \tau_{\text{prior}})$：衡量新预测是否与缓存模式一致。
- **阈值 $\delta$**：基于训练集 DDIM 反演重建误差的最大 RMSE，以数据驱动方式设定。
- **集成规则**：
  $$
  \tau_{\text{DTE}} = \begin{cases}
  \eta \cdot \tau_{\text{rand}} + (1-\eta) \cdot b_t, & d_{\text{valid}} \le \delta \text{ 且 } d_{\text{mode}} \le \delta \\
  \eta \cdot \tau_{\text{prior}} + (1-\eta) \cdot b_t, & d_{\text{valid}} \le \delta \text{ 且 } d_{\text{mode}} > \delta \\
  \tau_{\text{rand}}, & d_{\text{valid}} > \delta
  \end{cases}
  $$
  - **模式一致**：用最新观测下的 $\tau_{\text{rand}}$ 集成。
  - **模式切换**：用 $\tau_{\text{prior}}$ 抑制切换，保持一致。
  - **缓存失效**：丢弃缓存，全量采用最新预测以快速响应环境变化。
- **效率**：DDIM 反演步数与采样步数解耦，$\tau_{\text{rand}}$ 与 $\tau_{\text{prior}}$ 可并行采样，对实时性影响小。

### 2.4 网络架构

- 视觉编码：每个相机视角单独使用 ResNet18（无预训练），BatchNorm 替换为 GroupNorm，全局平均池化替换为空间 softmax 池化。
- 去噪骨干：标准 Transformer ×N。
- 输入：历史 $h$ 帧多视角观测 + 机器人状态 + 噪声化的子轨迹。

---

## 三、实验设计

### 3.1 模拟实验

- **RLBench 基准**（基于 CoppeliaSim + Franka Panda）：
  - 10 个代表性任务（覆盖堆叠、按压、抓取、开抽屉等）。
  - 完整 RLBench-60 基准。
  - 每个任务 100 条训练示教 + 25 条评估示教。
- **RoboMimic 基准**（PH 人体示教数据集）：
  - 3 个任务，示教数量 30 / 50 / 100 / 200 变化，测试数据效率。

### 3.2 真实世界实验

- **机器人平台**：xArm7 机械臂 + 夹爪，配备 2 个 Intel RealSense D435i 相机（第三人称 + 腕部）。
- **图像分辨率**：240×240，示教通过人工遥操作采集。
- **5 个真实任务**（图 7）：
  1. **Cube**：位置泛化能力。
  2. **Flip Cup**：复杂 6-DoF 操作（随机化杯柄朝向）。
  3. **Package**：多模态动作分布（左/右两种抓取示教）。
  4. **Banana**：执行中主动扰动香蕉位姿，测试动态适应能力。
  5. **Screw Cap**：随机化瓶盖位置，测试高精度操作。

### 3.3 对比方法

- **RLBench**：ACT、Diffusion Policy (DP)、DP*（本文复现）、Chain-of-Action (CoA)、Octo（微调版）。
- **RoboMimic**：DP、AWE（在 DP 基础上加入关键路径点过滤）。
- **真实世界**：DP (w/ TE)、DP (w/o TE)、ACT。

---

## 四、资源与算力

- **GPU**：实验在单卡 **NVIDIA RTX A6000** 上进行（仅在效率分析部分明确提及）。
- **真实机器人**：xArm7 + 2× Intel RealSense D435i。
- **训练时长**：**论文未明确给出训练时长或总计算资源消耗**。
- **推理延迟**（真实机器人系统，反演 10 步 + 采样 50 步）：
  - DP：约 622.17 ms
  - SegDiff：约 655.83 ms（额外开销 ~33.7 ms，约 5.4%）
- **显存占用**：DP 与 SegDiff 均为 1.07 GB。

---

## 五、实验数量与充分性

- **模拟实验规模**：
  - RLBench 10 任务，每任务 25 次评估。
  - RLBench-60 全基准。
  - RoboMimic 3 任务 × 4 种示教规模（30/50/100/200）。
- **真实实验规模**：5 任务，每任务 10 次试验。
- **随机种子**：模拟结果在 3 个随机种子上取均值并报告标准差。
- **消融实验**：
  - STM 消融（对比 DP 基线，4 个任务的学习曲线对比）。
  - DTE 消融：RAND / INV / DTE 三种策略。
  - 超参敏感度：插值长度 $L \in \{10, 25, 50, 100\}$、更新因子 $\eta \in \{0, 0.25, 0.5, 1\}$、阈值 $\delta$（max / p99 / p95）。
  - 效率分析：采样步数与反演步数的不同组合。
- **总体评价**：实验覆盖模拟+真实、多个基准、多种示教规模，消融维度较全；每个核心组件都进行了独立验证。**结果在 3 个随机种子上做了统计，方差有报告，公平性较好**。但缺少与更多最新方法（如 π0、RDT-1B、3D Diffusion Policy）的直接对比。

---

## 六、主要结论与发现

- **RLBench-10 任务**：SegDiff 平均成功率 **86.7%**，相比 CoA（75.6%）、Octo（64.4%）、DP*（54.4%）、ACT（48.8%）均有显著提升，在 9/10 任务上取得最佳；高精度任务（如 Turn Tap）提升超 30%。
- **RLBench-60**：相对 DP 提升 **+34%**，相对 CoA 提升 **+9%**。
- **RoboMimic**：在低示教规模（30/50 demos）下数据效率明显优于 DP 和 AWE。
- **真实世界**：在 Flip Cup（0.9）、Package（1.0）、Banana（0.9）、Screw Cap（0.6）上均显著优于基线；Package 任务中 DP(w/TE) 与 ACT 因模式震荡失败，Screw Cap 上 SegDiff 是唯一取得部分成功的方法。
- **学习曲线**：STM 加速收敛，所需训练步数更少即可达到更高性能。
- **DTE 价值**：在模拟环境中提升有限（仿真无扰动、单模态），但在真实多模态/动态场景下价值显著。
- **效率**：DDIM 反演 + 并行采样对实时性影响微小（+5.4% 延迟）。

---

## 七、优点与亮点

- **范式融合思路新颖**：将关键姿态作为预测锚点而非终点，统一了"离散关键点"与"连续轨迹"两种范式，结构上比多阶段方案（如 ChainedDiffuser、CoA）更简洁。
- **DDIM 反演应用于动作缓存校验**：利用扩散模型的确定性反演估计缓存的有效性与模式一致性，是首个将 DDIM inversion 用于在线时间集成的策略，设计优雅。
- **延迟可接受**：额外 5.4% 的推理开销对实时控制影响极小。
- **实验充分**：模拟与真实兼顾，覆盖多模态、动态扰动、高精度、位置泛化等多种挑战场景。
- **消融严谨**：DTE 三种策略（RAND/INV/DTE）的对比清晰展示了各模块的实际贡献，并对阈值选择、反演步数进行了敏感性分析。
- **数据驱动阈值 $\delta$**：避免手工调参，方法自洽。

---

## 八、不足与局限

- **关键姿态依赖人工启发式**：沿用 PerAct 的定义（夹爪状态变化 + 速度趋于零），对不符合该模式的任务（如连续速度操作的非抓取任务）可能不适用。论文在结论中也明确承认：未来应引入**自动或自监督关键姿态发现**。
- **DTE 在仿真中几乎无收益**：在单模态、无扰动的仿真环境下 DTE 提升微弱，甚至 INV 模式在确定性任务上反而**损害性能**（因为反演引入的旧观测信息会削弱响应性），表明方法对**任务特性敏感**。
- **资源与算力信息不完整**：未报告训练时长、整体 GPU 时长、收敛所需的 epoch 数等，**复现性受限**。
- **真实实验样本量较小**：每任务仅 10 次试验，可能存在随机性偏差；未报告方差或显著性检验。
- **缺乏与最新强基线对比**：未与 π0、RDT-1B、3D Diffusion Policy、Consistency Policy 等 2024–2025 年提出的方法直接比较。
- **泛化性验证有限**：真实任务多在固定桌面环境下，未测试光照变化、物体类别泛化、跨机器人平台迁移等。
- **关键姿态间距离可变**：通过插值归一化到固定长度 $L$ 可能掩盖了真实轨迹的动态特征，对速度敏感的精细操作可能受影响（作者承认但未深入分析）。

（完）
