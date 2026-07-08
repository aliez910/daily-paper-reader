---
title: When Should We Prefer State-to-Visual DAgger over Visual Reinforcement Learning?
title_zh: 何时应优先选择状态到视觉DAgger而非视觉强化学习
authors: "Tongzhou Mu, Zhaoyang Li, Stanisław Wiktor Strzelecki, Xiu Yuan, Yunchao Yao, Litian Liang, Hao Su"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33604/35759"
tags: ["query:rob-il"]
score: 8.0
evidence: 在三个基准16个任务上对比模仿学习（DAgger）与视觉强化学习的端到端视觉策略学习
tldr: 本文在三个基准共16个任务上对State-to-Visual DAgger（先训练状态策略再通过在线模仿学习视觉策略的两阶段框架）与视觉强化学习进行系统性实证对比。研究从渐近性能、样本效率和计算成本三个维度评估，发现模仿学习方法在多个任务上优于视觉强化学习的反直觉结果。该工作直接对应模仿学习在视觉运动任务上的基准评估问题，对视觉到动作方法在机器人控制中的选择具有重要指导意义，为视觉策略学习中选择模仿学习还是视觉强化学习提供了可操作的指导。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33604/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1841, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33604/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1831, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33604/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1833, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33604/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1826, \"height\": 1275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33604/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1827, \"height\": 1273, \"label\": \"Figure\"}]"
motivation: 从高维视觉输入学习策略时，视觉强化学习面临样本效率与计算成本挑战，需系统比较基于模仿的替代方案。
method: 对比State-to-Visual DAgger两阶段框架与视觉强化学习在多个基准任务上的表现。
result: 在16个任务三个基准上发现模仿学习方法在某些场景下优于视觉强化学习。
conclusion: 为视觉策略学习中模仿学习与视觉强化学习的选用提供了实证依据与指导。
---

## Abstract
Learning policies from high-dimensional visual inputs, such as pixels and point clouds, is crucial in various applications. Visual reinforcement learning is a promising approach that directly trains policies from visual observations, although it faces challenges in sample efficiency and computational costs. This study conducts an empirical comparison of State-to-Visual DAgger — a two-stage framework that initially trains a state policy before adopting online imitation to learn a visual policy — and Visual RL across a diverse set of tasks. We evaluate both methods across 16 tasks from three benchmarks, focusing on their asymptotic performance, sample efficiency, and computational costs. Surprisingly, our findings reveal that State-to-Visual DAgger does not universally outperform Visual RL but shows significant advantages in challenging tasks, offering more consistent performance. In contrast, its benefits in sample efficiency are less pronounced, although it often reduces the overall wall-clock time required for training. Based on our findings, we provide recommendations for practitioners and hope that our results contribute valuable perspectives for future research in visual policy learning.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper following a specific structure with 8 points. Let me analyze the paper carefully and produce a comprehensive, well-organized summary.

The paper is "When Should We Prefer State-to-Visual DAgger over Visual Reinforcement Learning?" - an AAAI 2025 paper that empirically compares two paradigms for learning visual policies.

Let me organize my thoughts:

1. Core problem: When to use State-to-Visual DAgger vs Visual RL for visual policy learning
2. Method: Two-stage framework vs single-stage visual RL with Asymmetric Actor-Critic
3. Experiments: 16 tasks from 3 benchmarks (ManiSkill, DMControl, Adroit)
4. Resources: 32 CPU cores (Intel Xeon 2.1GHz), 1 GPU (NVIDIA RTX 2080 Ti 11GB)
5. Experimental sufficiency: 16 tasks × 3 seeds = 48+ runs, multiple metrics
6. Main findings: S2V DAgger excels at hard tasks, more consistent, better wall-clock time but not always better sample efficiency
7. Advantages: Standardized implementation, critical design decisions analysis
8. Limitations: Task difficulty classification not rigorous, checkpoint selection not studied

Let me write this up in Chinese with proper Markdown formatting.</think>

# 论文总结：何时应优先选择 State-to-Visual DAgger 而非视觉强化学习

## 1. 论文的核心问题与整体含义

- **研究背景**：从像素、点云等高维视觉观测中学习策略是机器人操作、导航与自动驾驶等领域的关键问题。**视觉强化学习（Visual RL）**作为主流范式，需要同时解决两个难题：(1) 通过试错找到完成任务的方法；(2) 建立从高维视觉到高奖励动作的映射（通常需训练大型视觉编码器），因此面临**样本效率低、计算成本高**的固有问题。
- **替代思路**：将上述两个挑战**解耦**，先以低维状态（含特权信息）训练教师策略，再通过在线模仿学习（DAgger）将其蒸馏为视觉策略。该两阶段框架被称为 **State-to-Visual DAgger**（S2V DAgger），已广泛应用于灵巧操作、四足运动、无人机控制、自动驾驶等任务。
- **核心问题**：S2V DAgger 增加了训练阶段，**并不一定更便宜**。因此本文聚焦的核心问题是——**"在什么情况下应优先选择 S2V DAgger 而非 Visual RL？"** 这是现有文献中尚未系统回答的问题。

## 2. 方法论

### 2.1 State-to-Visual DAgger（两阶段框架）

- **前提**：训练环境需同时提供低维状态观测 $o_t^S$ 与高维视觉观测 $o_t^V$。最终部署的视觉策略不依赖任何仿真器特权信息。
- **Stage 1（状态策略学习）**：使用 **SAC（Soft Actor-Critic）** 算法在低维状态空间上训练教师策略 $\pi_S$。状态通常含机器人本体感知与仿真器才能提供的特权信息（如物体的真实位姿）。训练至收敛后保存最终检查点。
- **Stage 2（视觉策略模仿学习）**：以 $\pi_S$ 为教师，使用 **DAgger（在线模仿学习）** 训练视觉策略 $\pi_V$，最小化动作 MSE 损失：
$$\pi_V = \arg\min_{\pi_V} \|\pi_V(o_t^V) - \pi_S(o_t^S)\|^2$$
- **两个关键设计决策**（本文贡献）：
  1. **Off-policy vs On-policy**：经验表明 off-policy（使用回放缓冲池保留多样轨迹）显著优于 on-policy。
  2. **早停机制**：每轮训练以预设的模仿损失阈值触发早停，再启动新数据采集周期，避免过拟合并提升训练效率。

### 2.2 Visual RL（对比基线）

- 为保证公平比较，选择 **Asymmetric Actor-Critic** 作为 Visual RL 代表——其 critic 使用含特权信息的低维状态作为输入，actor 仍以视觉观测为输入，可与 S2V DAgger 同样利用特权信息。
- 将原始 DDPG 替换为 **SAC** 以提升性能。
- 实证表明 Asymmetric SAC 在所测任务上达到 SOTA 视觉 RL 水平，因此作为代表性对比方法。

## 3. 实验设计

- **Benchmark（3 套，共 16 个任务）**：
  - **ManiSkill**（8 个任务）：固定基座机械臂操作、移动操作、双臂协作等；状态含本体感知+物体真实位姿；视觉为 64×64 双目 RGBD 相机。
  - **DMControl**（5 个任务）：不同机器人形态的运动控制与经典控制；状态主要为本体感知；视觉为 84×84 RGB 三帧堆叠。
  - **Adroit**（3 个任务）：灵巧手操作；状态含所有关节信息与手掌/物体位姿；视觉为 128×128 RGB。
- **对比方法**：仅对比 S2V DAgger 与 Visual RL（Asymmetric SAC）。
- **任务难度分类**：将"状态 RL 在 4M 环境步内能否收敛"作为"易/难"任务的划分依据。
- **评价指标**：
  - **渐近性能**：取学习曲线末端 3% 步数窗口的均值。
  - **样本效率**：以环境步数衡量。
  - **计算成本**：以墙钟时间（wall-clock time）衡量，并对 S2V DAgger 累加两个阶段的成本。

## 4. 资源与算力

- 文中明确给出的硬件配置：
  - **CPU**：32 核 Intel Xeon 2.1 GHz
  - **GPU**：1 块 NVIDIA GeForce RTX 2080 Ti（11 GB 显存）
- 所有实验均**统一在同一硬件**上以保证墙钟时间比较的公平性。
- 训练时长因任务而异：短任务（如 Acrobot-Swingup）约 2–4 小时；长任务（如 ManiSkill MoveBucket、Adroit Relocate）可达 60–100 小时以上（从图 5 的横轴推断）。

## 5. 实验数量与充分性

- **任务数量**：16 个任务，覆盖三类基准（操作、运动+经典控制、灵巧操作），任务类型多样。
- **随机种子**：每个任务、每种方法均使用 **3 个随机种子**，并报告 95% 置信区间。
- **实验维度**：
  - 渐近性能对比（按基准、按难度分类统计）
  - 样本效率学习曲线（按环境步）
  - 墙钟时间学习曲线（按小时）
- **消融/设计分析**：在 S2V DAgger 实现中分析了 off-policy vs on-policy、早停机制两个关键设计选择的影响。
- **公平性考量**：
  - 选用 Asymmetric SAC 作为 Visual RL 基线，使其也能利用特权信息，与 S2V DAgger 站在"同等信息"基础上比较。
  - 所有实验统一硬件、统一指标。
- **充分性评价**：整体较为充分，但作者自己也承认未研究**检查点选择策略**对 S2V DAgger 效率与性能的影响。

## 6. 主要结论与发现

- **渐近性能**：
  - **难任务上**，S2V DAgger **显著优于** Visual RL（归一化分数 66 vs 21）。
  - **易任务上**，S2V DAgger 与 Visual RL **相当或略差**（67 vs 68）。
  - 跨基准看，S2V DAgger 在 ManiSkill（74 vs 49）和 Adroit（77 vs 29）大幅领先；DMControl 上 Visual RL 略优（475 vs 459）。
- **稳定性**：S2V DAgger 收敛后**置信区间更窄、性能更稳定**；Visual RL 在部分任务上出现波动甚至"遗忘"现象（如 Adroit Pen）。
- **样本效率**：S2V DAgger 在难任务上表现更优主要**源于更高的渐近性能**，而非真正的样本效率优势；在易任务上**没有明显优势**。
- **计算成本**：S2V DAgger 在**绝大多数任务上墙钟时间更短**，因为 Stage 1 的状态 RL 无需渲染视觉与训练大型 CNN，速度快得多。
- **机制解释**：难任务的性能差距来源于状态 RL（MLP+稠密奖励）能稳健解决任务，而 Visual RL 在 CNN 训练中受探索噪声梯度影响难以学习。

## 7. 优点与亮点

- **系统性强**：在 16 个任务、3 套基准上做统一、可复现的实证比较，弥补了既有文献缺乏标准化对比的空白。
- **提供了 S2V DAgger 的标准化开源实现**，并明确指出 off-policy + 早停两个关键设计选择，避免后续研究者重复踩坑。
- **公平对比方法选择得当**：选用 Asymmetric SAC 作为 Visual RL 基线，使两者在特权信息使用上对等。
- **多维度评价**：同时考察渐近性能、样本效率、墙钟时间与稳定性，避免单一指标的片面结论。
- **面向实践的指导**：基于实验结果明确给出"何时用 S2V DAgger / 何时用 Visual RL"的可操作建议，对工程落地有直接价值。
- **跨任务类型**：覆盖操作、运动、灵巧操作三大场景，结论适用范围更广。

## 8. 不足与局限

- **任务难度分类方法不严谨**：以"状态 RL 是否在 4M 步内收敛"作为易/难划分，缺乏理论依据，带有主观性。
- **未研究检查点选择的影响**：S2V DAgger 在何时停止 Stage 1、如何选择教师检查点，可能显著影响最终效率与性能，本文未做系统分析。
- **未引入更先进的视觉 RL 增强技术**：为保证对比公平，未加入先进的图像特征提取或数据增强（如 RAD、DrQ、CURL 等），可能使 Visual RL 的代表性能被低估。
- **依赖仿真器特权信息**：S2V DAgger 要求训练环境同时提供低维状态，这在真实机器人上往往不可行，限制其应用场景。
- **方法选择局限**：仅对比 Asymmetric SAC 一种 Visual RL 范式，未涵盖基于世界模型（如 Dreamer、TD-MPC）的方法，可能遗漏某些场景下的相对优势。
- **硬件规模较小**：仅使用单卡 RTX 2080 Ti，未在大规模分布式训练下验证，可能影响墙钟时间结论的泛化性。
- **行为克隆的固有风险**：S2V DAgger 第二阶段本质上是有监督模仿，难以超越教师策略上限；若状态教师策略本身存在偏差或过拟合，会传递到视觉学生策略。

（完）
