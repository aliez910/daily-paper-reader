---
title: "MA-VLA: Multi-Arm Vision-Language-Action Model for Collaboration and Compositional Generalization"
title_zh: MA-VLA：面向协作与组合泛化的多臂视觉-语言-动作模型
authors: "Zaibin Zhang, Junlan Xiao, Zhongbo Zhang, Yifan Wang, Li Kang, Yiran Qin, Changxing Xia, Heng Zhou, Talas Fu, Enshen Zhou, Ruimao Zhang, Zhenfei Yin, Huchuan Lu, Lijun Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4925.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 多臂具身操纵的VLA模型，视觉-语言-动作映射
tldr: 多臂协作正成为具身操纵的核心能力，但现有视觉-语言-动作模型通常将语言表示为单一全局指令，缺乏将臂特定行为分配和组合的显式机制。本文提出MA-VLA统一框架，通过原子动作分配实现多臂协作，将协作行为分解为中层原子提示并分配给单个机械臂，从而实现显式的子目标指定和跨任务组合复用。该工作直接服务于通用视觉-动作模型在复杂多臂机器人操纵任务中的应用，对基于模仿学习的可组合泛化操纵策略具有重要贡献。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 2020, \"height\": 1470}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-002.webp\", \"caption\": \"\", \"page\": 4, \"index\": 2, \"width\": 3936, \"height\": 1184}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-004.webp\", \"caption\": \"\", \"page\": 6, \"index\": 4, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-005.webp\", \"caption\": \"\", \"page\": 12, \"index\": 5, \"width\": 866, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-006.webp\", \"caption\": \"\", \"page\": 12, \"index\": 6, \"width\": 864, \"height\": 644}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-007.webp\", \"caption\": \"\", \"page\": 12, \"index\": 7, \"width\": 1280, \"height\": 954}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-008.webp\", \"caption\": \"\", \"page\": 12, \"index\": 8, \"width\": 866, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-009.webp\", \"caption\": \"\", \"page\": 12, \"index\": 9, \"width\": 859, \"height\": 640}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-010.webp\", \"caption\": \"\", \"page\": 12, \"index\": 10, \"width\": 1274, \"height\": 954}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-011.webp\", \"caption\": \"\", \"page\": 12, \"index\": 11, \"width\": 865, \"height\": 648}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-012.webp\", \"caption\": \"\", \"page\": 12, \"index\": 12, \"width\": 865, \"height\": 648}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-013.webp\", \"caption\": \"\", \"page\": 12, \"index\": 13, \"width\": 1280, \"height\": 954}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-014.webp\", \"caption\": \"\", \"page\": 12, \"index\": 14, \"width\": 864, \"height\": 644}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-015.webp\", \"caption\": \"\", \"page\": 12, \"index\": 15, \"width\": 866, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c906764ddd26f319323c4036/fig-016.webp\", \"caption\": \"\", \"page\": 12, \"index\": 16, \"width\": 1280, \"height\": 954}]"
motivation: 现有VLA模型用单一全局指令表示语言，缺乏显式的臂特定行为分配与组合机制，限制了对新协作模式的迁移能力。
method: 提出MA-VLA框架，将协作行为分解为中层原子提示并分配给单个机械臂。
result: 实现了显式子目标指定与跨任务的组合复用。
conclusion: 为多臂协作具身操纵提供了可组合泛化的VLA解决方案。
---

## Abstract
Multi-arm collaboration is becoming a core capability in embodied manipulation. Recent vision-language-action (VLA) models integrate perception, language, and control, but most represent language as a single global instruction and do not provide an explicit mechanism for assigning and composing arm-specific behaviors. This design limits transfer to collaboration patterns that differ from those observed during training. We present MA-VLA, a unified framework for multi-arm collaboration via atomic action assignment. MA-VLA decomposes cooperative behavior into mid-level atomic prompts and allocates them to individual arms, enabling explicit subgoal specification and compositional reuse across tasks. To reduce reliance on fixed execution roles, we introduce Arm Shuffle, a training-time permutation of the observation, state, and assigned atomic prompts for each arm. This permutation enforces role-agnostic instruction following and supports recomposition into unseen coordination patterns, which we term multi-arm compositional generalization. We also construct a benchmark in which test-time collaboration patterns are absent in training set. Across simulation and real-world evaluations, prior state-of-the-art VLAs largely fail under these unseen collaborations, while MA-VLA consistently succeeds. These results indicate that structured, per-arm atomic action assignment offers a practical route to scalable generalization in multi-arm embodied systems. Code, models, and data are available at https://github.com/zhangzaibin/future-robots

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize the paper "MA-VLA: Multi-Arm Vision-Language-Action Model for Collaboration and Compositional Generalization" in Chinese, following a structured format with 8 specific points. Let me carefully analyze the paper content and create a comprehensive summary.

Let me extract the key information:

1. **Core Problem & Motivation**: Multi-arm collaboration is a core capability in embodied manipulation. Existing VLA models treat language as a single global instruction without explicit mechanism for assigning/composing arm-specific behaviors, limiting transfer to unseen collaboration patterns.

2. **Methodology**: 
   - MA-VLA framework with two components: VLM-based Planner and VLA Executor
   - Decomposes high-level instruction into atomic prompts for each arm
   - Uses flow-matching expert for action generation
   - Arm Shuffle: training-time permutation of observation/state/atomic prompts
   - View Dropout: random masking of visual inputs
   - Planner uses GPT-4.1 (or similar VLM)
   - Backbone: Pi0 with pi0_base checkpoint

3. **Experimental Design**:
   - Benchmarks: RoboFactory, RoboTwin 2.0 (Hard), Real-world SO101 dual-arm
   - Tasks: 2-arm, 3-arm, 4-arm tasks in RoboFactory; bimanual tasks in RoboTwin 2.0
   - Real-world: Stack Bowls, Place Cubes, Pass Toys, Stack Cubes
   - Baselines: ACT, DP, DP3, Pi0-FAST, Pi0
   - Evaluation: in-domain and out-of-domain compositional generalization

4. **Resources & Compute**:
   - 2 NVIDIA A800 GPUs
   - Batch size 32
   - RoboFactory 2-arm: 10,000 steps; 3-4 arm: 15,000 steps
   - RoboTwin 2.0 (Hard): 30,000 steps
   - SO101: 15,000 gradient steps
   - Horizon 50 for all tasks

5. **Experimental Quantity & Sufficiency**:
   - Tables 1-6 with multiple benchmarks
   - Ablation studies: components, shuffle probability, separate model comparison
   - 100 rollouts per configuration in simulation
   - 20 episodes in real-world
   - Visualization figures

6. **Main Conclusions**:
   - MA-VLA outperforms SOTA in both in-domain and OOD
   - Prior VLAs largely fail on unseen collaboration patterns
   - Atomic action assignment offers practical route to scalable generalization

7. **Strengths**:
   - Novel decomposition framework
   - Arm Shuffle is elegant regularization
   - Comprehensive evaluation including real-world
   - Clear motivation

8. **Limitations**:
   - Limited real-world tasks
   - Only 4 real-world tasks
   - Limited OOD scenarios
   - Dependence on VLM planner (GPT-4.1)
   - Demonstrations collected only 50 per real-world task

Let me write this in Chinese, structured format.</think>

# MA-VLA 论文总结

## 1. 核心问题与研究动机

- **研究背景**：多臂协作已成为具身智能操作的核心能力。与单臂任务相比，多臂场景涉及并行执行与协调控制，可解决单臂无法完成的复杂任务。
- **现有 VLA 的不足**：现有视觉-语言-动作（VLA）模型（如 RT-2、Octo、OpenVLA、π0）通常将语言视为单一静态全局指令，直接映射到连续控制信号，缺乏：
  - 显式的任务分解机制；
  - 跨机械臂的子任务分配机制；
  - 对角色（哪个臂做什么）的灵活泛化能力。
- **核心瓶颈**：这种设计导致协作模式严重依赖于训练中见过的"分工组合"，对测试阶段出现的新协作模式（如角色互换、堆叠顺序变化）泛化能力极差。
- **本文目标**：探索一种新的能力——**多臂组合泛化（multi-arm compositional generalization）**：利用训练时见过的原子动作重新组合成未见过的协作模式执行多臂任务。

## 2. 方法论

### 2.1 整体框架
MA-VLA 采用"分层语言接口"的两阶段架构：
1. **VLM Planner（任务规划器）**：将高层指令分解为按时间排序的、面向每个机械臂的原子子目标（atomic prompts）；
2. **VLA Executor（动作执行器）**：基于当前场景与原子提示为每个机械臂生成连续动作。

### 2.2 VLM-based Planner
- 输入：高层指令 $l$、视觉观测 $I$、预定义的有限原子提示集合 $\mathcal{A}$；
- 输出：$T$ 个时间阶段的原子提示序列 $(p^1, \dots, p^T)$，其中 $p^t = (p_1^t, \dots, p_N^t)$，$p_i^t \in \mathcal{A}$ 表示阶段 $t$ 时第 $i$ 个臂的子指令；
- 单次前向推理完成分解：$(p^1,\dots,p^T) = P_\phi(I, l, \mathcal{A})$；
- 实际采用 GPT-4.1 作为规划器，仅生成语言提示，不参与梯度微调。

### 2.3 VLA Executor
- 将每帧的所有臂原子提示拼成统一指令字符串：$u_t =$ `"Arm0: p_0^t, Arm1: p_1^t, …, ArmN: p_N^t"`；
- 输入：多视角观测 $I_t$（含全局与腕部相机）、所有臂的本体感知 $s_t = [s_t^1,\dots,s_t^N]$、统一指令 $u_t$；
- 输出：所有臂的动作 $[a_t^1,\dots,a_t^N] = \pi_\theta(I_t, s_t, u_t)$；
- **动作生成**：基于 π0 的轻量级 flow-matching，预测从噪声潜变量到真实动作的去噪向量场；推理时通过积分从噪声恢复到动作；
- 多头投影层将共享潜变量分离为各臂的动作头。

### 2.4 训练时的两个正则化策略
- **Arm Shuffle**：每步以概率 $p_{shuffle}$ 随机置换每个臂的状态、视角、提示与动作的对应关系：$(s_i^t, v_i^t, p_i^t, a_i^t) \to (s_{\sigma(i)}^t, v_{\sigma(i)}^t, p_{\sigma(i)}^t, a_{\sigma(i)}^t)$；
  - 目的：防止模型将行为绑定到固定臂身份，强制按语义而非结构解释原子提示；
- **View Dropout**：以概率 $p_{drop}$ 随机将部分相机视角置零，强化多视角冗余感知；
- **训练目标**：与标准行为克隆（BC）一致，仅在数据层面做扰动：$L_t(\theta) = \mathbb{E}\big[\sum_i \ell(\pi_\theta(\tilde{I}_t, s_i^t, p_i^t), a_i^t)\big]$。

## 3. 实验设计

### 3.1 Benchmark 与数据集
- **RoboFactory**：含 2、3、4 臂的协作任务，每任务 150 条专家示范；
  - 2 臂任务：Lift Barrier、Place Food、Two Arms Stack Cube、Pass Shoe；
  - 3 臂任务：Three Arms Stack Cube；
  - 4 臂任务：Camera Alignment、Long Pipeline Delivery、Take Photo。
- **RoboTwin 2.0 (Hard)**：双臂协作任务，强调视觉干扰（散乱物、背景变化、光照变化），含 Place Dual Shoes、Handover Block、Stack Bowls、Grab Roller、Place Object (Cabinet)、Place Bread (Skillet)、Stamp Seal；
- **真实机器人平台**：SO101 双臂（12 自由度，每臂 6 DoF），每臂 1 个腕部相机 + 1 个全局相机，30 Hz；
  - 任务：Stack Bowls、Place Cubes、Pass Toys、Stack Cubes；
  - 每个任务 50 条遥操作示范（用 LeRobot 收集）。

### 3.2 对比方法
- 模仿学习方法：ACT、Diffusion Policy (DP)、DP3；
- VLA 方法：π0-FAST、π0；
- 所有基线针对多臂输入/输出接口做了适配，使用相同示范与训练预算。

### 3.3 评测协议
- **In-domain Collaboration**：与训练同分布的任务，含随机物体位姿、视角、环境扰动；
- **Out-of-domain Compositional Generalization**：原子动作集合相同，但重新组合为未见过的协作模式（新角色分配、新顺序、新交互模式）；
- 仿真每组 100 次 rollout，真实机器人每任务 20 次；
- 报告成功率。

## 4. 资源与算力

- **GPU**：2 块 NVIDIA A800；
- **Batch size**：32；
- **训练步数**：
  - RoboFactory 2 臂任务：10,000 步；
  - RoboFactory 3–4 臂任务：15,000 步；
  - RoboTwin 2.0 (Hard)：30,000 步；
  - SO101 真实机器人：15,000 梯度步；
- **动作 horizon**：所有任务统一为 50；
- **超参设置**：
  - 不同 OOD 任务设置不同的 $p_{shuffle}$（0.6 / 0.8 / 1.0）与 $p_{drop}$（0.2 / 0.4）；
  - SO101：$p_{shuffle}=1.0$，$p_{drop}=0.4$；
- **主干网络**：基于 π0 官方 pi0_base 初始化；VLM Planner 使用 GPT-4.1；
- 论文未明确报告单次训练总时长。

## 5. 实验数量与充分性

- **主要对比表格**：表 1（RoboFactory，2/3/4 臂共 8 个任务）、表 2（RoboTwin 2.0 Hard，7 个任务）、表 3（5 个 OOD 任务）、表 4（真实机器人 4 任务 × ID/OOD 共 8 项）；
- **消融实验**：
  - 表 5：原子动作、Arm Shuffle、View Dropout 三组件消融；
  - 图 5：Arm Shuffle 概率 $0\%\sim100\%$ 扫描；
  - 表 6：与"每臂独立 VLA"基线对比；
- **定性分析**：图 6 展示仿真与真实机器人在 ID/OOD 下的 rollout；
- **充分性评估**：
  - 覆盖仿真+真实机器人两层级证据，2/3/4 臂均有评测；
  - 评测了 ID 与 OOD 两类泛化；
  - 多组消融研究关键设计选择；
  - 总体较为充分；但每个基准的 OOD 任务数量较少（如 RoboFactory 仅 5 个 OOD 任务），统计显著性可能受限。

## 6. 主要结论与发现

- **In-domain 表现**：
  - RoboFactory 2 臂平均 83.5%（π0 为 80.3%），3-4 臂平均 83.3%（π0 为 76.5%），优势随臂数增加更明显；
  - RoboTwin 2.0 (Hard) 平均 49.0%（π0 为 41.1%），ACT/DP/DP3/π0-FAST 远低于此；
- **OOD 组合泛化**：
  - 所有基线在未见过的协作模式下成功率均为 0；
  - MA-VLA 在 RoboFactory OOD 平均 13.0%，最大单项提升达 13 个百分点；
  - 真实机器人 OOD：π0 全为 0/20，MA-VLA 在 Stack Bowls OOD 达 10/20，其他任务也有非零成功率；
- **消融结论**：
  - 原子动作显著提升 ID 性能；
  - Arm Shuffle 是 OOD 突破的关键（0% → 7.3%）；
  - View Dropout 进一步提升 OOD 至 15.3%；
  - Arm Shuffle 概率越高，OOD 越稳健，ID 仅有轻微下降；
- **整体结论**：结构化的"按臂原子动作分配"为多臂具身系统的可扩展泛化提供了可行路径。

## 7. 方法与实验的亮点

- **将"分工"显式化**：从单一高层指令到逐臂原子提示的分解，使协作结构可解释、可干预；
- **Arm Shuffle 设计精巧**：用简单的数据层置换打破模型对臂身份的过拟合，无需改模型结构；
- **组合泛化视角新颖**：提出"多臂组合泛化"这一未被充分定义的问题，并配套构造 OOD benchmark；
- **统一模型 vs 独立模型**：表 6 证明单模型联合推理比 N 个独立 VLA 更利于协作；
- **跨仿真与真实机器人验证**：避免仅在模拟器中"刷榜"的局限；
- **完备的消融研究**：组件、消融、概率扫描、独立基线对比均齐全。

## 8. 不足与局限

- **真实机器人实验规模较小**：每个真实任务仅 50 条示范、20 次测试，且仅 4 个任务；
- **OOD 任务数量有限**：每个基准的 OOD 测试场景较少，统计显著性难以保证；
- **依赖外部大模型**：Planner 使用闭源 GPT-4.1，可复现性与部署成本受限；若换开源 VLM 性能如何未知；
- **原子动作库依赖人工定义**：需要为每个任务手工设计 $\mathcal{A}$ 与规则解析器，泛化到新任务时需要重新定义；
- **未充分讨论失败模式**：在某些任务上 ID 性能并未显著超越 π0（如 RoboFactory Place Food 59% vs 58%），论文未深入剖析；
- **对比方法局限**：仅与模仿学习与 VLA 基线对比，未与专门的双臂 VLA（如 GR-3、Hi Robot、TwinVLA）做全面比较；
- **未涉及长时序与容错恢复**：原子提示依赖任务依赖的终止条件，但鲁棒性与失败恢复能力未充分评测；
- **未量化算力/推理成本**：未报告 wall-clock 时间、显存占用、推理延迟等实用指标，部署可行性难评估；
- **数据偏差风险**：所有训练数据均来自单一仿真器或单一实验室的遥操作，跨平台迁移能力仍待验证。

（完）
