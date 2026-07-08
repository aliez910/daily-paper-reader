---
title: Markov Balance Satisfaction Improves Performance in Strictly Batch Offline Imitation Learning
title_zh: 马尔可夫平衡满足提升严格批量离线模仿学习性能
authors: "Rishabh Agrawal, Nathan Dahlin, Rahul Jain, Ashutosh Nayyar"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33680/35835"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向机器人任务的模仿学习离线批处理方法
tldr: 本文针对严格批量离线场景下的模仿学习问题，研究者无法与环境交互且缺乏转移动力学信息，这种设定在实际机器人部署中十分常见。作者提出了一种基于马尔可夫平衡方程的条件密度估计框架，避免了传统模仿学习方法依赖补充数据或环境访问的局限。实验在受约束的批量离线条件下验证了所提方法相对于现有方法的性能提升。该工作为在线交互不可行的机器人操纵部署提供了一种可推广的模仿学习方法。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33680/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1823, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33680/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1825, \"height\": 617, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33680/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1826, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33680/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1830, \"height\": 477, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33680/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 798, \"height\": 642, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33680/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 894, \"height\": 484, \"label\": \"Table\"}]"
motivation: 机器人任务中模仿学习常需在线交互或额外数据集，这在真实部署中难以满足。
method: 基于马尔可夫平衡方程与条件密度估计构建新型批量离线模仿学习框架。
result: 在严格批量离线设置下相对现有方法取得性能改进，无需环境交互。
conclusion: 为现实机器人场景下的离线模仿学习提供了一种可推广且更鲁棒的解决方案。
---

## Abstract
Imitation learning (IL) is notably effective for robotic tasks where directly programming behaviors or defining optimal control costs is challenging. In this work, we address a scenario where the imitator relies solely on observed behavior and cannot make environmental interactions during learning. It does not have additional supplementary datasets beyond the expert's dataset nor any information about the transition dynamics. Unlike state-of-the-art (SOTA) IL methods, this approach tackles the limitations of conventional IL by operating in a more constrained and realistic setting. Our method uses the Markov balance equation and introduces a novel conditional density estimation-based imitation learning framework. It employs conditional normalizing flows for transition dynamics estimation and aims at satisfying a balance equation for the environment. Through a series of numerical experiments on Classic Control and MuJoCo environments, we demonstrate consistently superior empirical performance compared to many SOTA IL algorithms.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper following a specific structure. Let me analyze the paper carefully and produce a well-organized response.

The paper is about "Markov Balance Satisfaction Improves Performance in Strictly Batch Offline Imitation Learning" (MBIL). Let me go through each required section:

1. Core problem and motivation: Strictly batch offline imitation learning - no environment interaction, no supplementary data, no transition dynamics knowledge
2. Methodology: Markov Balance Equation + Conditional Normalizing Flows for density estimation
3. Experimental design: Classic Control (Acrobot, CartPole, LunarLander) and MuJoCo (Hopper, Ant, HalfCheetah, Walker2d)
4. Resources: No explicit GPU/compute info mentioned
5. Experiment quantity and adequacy
6. Main conclusions
7. Strengths
8. Limitations

Let me write this up in Chinese, using Markdown formatting.
</think>
# 论文总结：马尔可夫平衡满足提升严格批量离线模仿学习性能（MBIL）

## 1. 核心问题与研究动机

- **问题定位**：在模仿学习（Imitation Learning, IL）领域，许多实际场景（如自动驾驶、医疗）出于安全性或成本考虑，**无法与环境进行在线交互**，也往往**没有除专家数据集外的补充数据**，且**事先不知道环境转移动力学**。论文将这种最严苛的设定称为 **"strictly batch offline IL"**。
- **现有方法的不足**：
  - 行为克隆（BC）只做状态-动作的监督学习，**不利用轨迹数据满足的马尔可夫平衡方程（Markov Balance Equation, MBE）**，因此存在误差传播和协变量偏移问题。
  - 逆强化学习（IRL）需先估计奖励函数，**奖励估计本身是病态问题**，且计算代价高。
  - 对抗模仿学习（AIL，如 GAIL）需要 on-policy 样本估计密度比，**无法在纯离线场景使用**。
  - DICE 系方法（ValueDICE、SoftDICE、ODICE 等）依赖平稳分布匹配，需假设马尔可夫链遍历性与平稳性，且在终止状态上存在**终止偏差**和**奖励偏差**。
- **核心动机**：轨迹数据唯一已知且可信赖的数学结构就是 **马尔可夫平衡方程**，因此应直接利用该方程约束模仿策略学习，避免奖励估计和分布匹配带来的偏差。

## 2. 方法论

### 2.1 核心思想

提出 **MBIL（Markov Balance-based Imitation Learning）** 框架：
- 不估计奖励，不做分布匹配；
- 通过 **条件密度估计** 学得两个转移动力学：诱导马尔可夫链的转移密度 $P^{\pi_D}(s',a'|s,a)$ 和 MDP 转移动力学 $T(s'|s,a)$；
- 优化一个组合损失，使学得策略 $\pi_\theta$ 在数据上**满足马尔可夫平衡方程**，同时保留对专家动作的拟合（行为克隆正则）。

### 2.2 关键公式与算法

- **马尔可夫平衡方程**（状态-动作空间形式，规避连续动作求和）：

$$
P^{\pi_D}(s', a' \mid s, a) = \pi_D(a' \mid s')\, T(s' \mid s, a)
$$

- **优化目标**（双损失加权组合）：

$$
J_{\text{MBIL}}(\pi_\theta) = \alpha\,\underbrace{\mathbb{E}_{(s,a,s',a')\sim D}\!\Big[\big(\log \hat P - \log \pi_\theta(a'|s') - \log \hat T\big)^2\Big]}_{\text{动力学损失}}
+ \beta\,\underbrace{\mathbb{E}_{(s,a)\sim D}\!\big[L(\pi_D(\cdot|s), \pi_\theta(\cdot|s))\big]}_{\text{策略损失}}
$$

其中 $L$ 可为 KL/对数似然（离散动作任务）或 MSE（连续动作任务）。

- **密度估计**：用 **条件 Normalizing Flow（CNF）** 估计 $P^{\pi_D}$ 和 $T$；具体实现采用 **RealNVP**（GLOWCouplingBlocks）+ FrEIA 框架，条件输入 $c$ 先经一个共享网络 $NN_c$ 映射到潜空间，再注入每个耦合块（Coupling Block）。

### 2.3 算法流程（Algorithm 1 摘要）

1. 初始化策略参数 $\theta$、专家 MC 参数 $\eta$、MDP 转移参数 $\psi$；
2. 将专家数据 $\mathcal{D}$ 重组为 $(s,a,s',a')$ 元组存入 buffer $B$；
3. **先**用对数似然最大化训练 $\hat P_\eta$ 和 $\hat T_\psi$（并在训练时加高斯噪声正则以应对低数据场景）；
4. 循环：从 $B$ 采样 batch，按式 (5) 计算 MBIL 损失，梯度更新 $\theta$；
5. 返回 $\theta^*$。

> **注**：训练流程是**单阶段优化**，没有 DICE 类方法的交替最大-最小过程，且无需折扣因子 $\gamma$。

## 3. 实验设计

- **任务/数据集**：
  - **Classic Control**（OpenAI Gym）：Acrobot-v1、CartPole-v1、LunarLander-v2（离散动作）；
  - **MuJoCo 运动任务**：Hopper、Ant、HalfCheetah、Walker2d（连续动作）。
  - 专家数据来自 Kostrikov 等 (2020) 在 MuJoCo 上用 GAIL 收集的轨迹，Classic Control 上则用 RL Baselines3 Zoo 中 PPO/DQN/A2C 预训练的最优代理采样得到。
- **数据规模（强调低数据）**：
  - Classic Control：1、3、7、10、15 条专家轨迹；
  - MuJoCo：**仅 1 条专家轨迹**。
- **对比方法**：
  - Classic Control：BC、ValueDICE、RCAL、EDM、AVRIL、DSFN、IQ-Learn；
  - MuJoCo：BC、ValueDICE、SoftDICE、ODICE（排除 IQ-Learn/EDM/AVRIL，因其在高维连续任务上不适用或在严格离线设定下 Q 函数爆炸）。
  - **明确排除** 依赖补充数据或在线交互的方法（CLARE、DemoDICE、MILO、OPOLO 等），以保证公平。
- **评估协议**：
  - Classic Control：300 个 episode 评估，10 个不同随机初始化与轨迹采样；
  - MuJoCo：每 500 次梯度更新在 10 个 episode 上评估，5 个随机种子报告均值±标准差。

## 4. 资源与算力

- 论文**未明确说明**所用 GPU 型号、数量或总训练时长；
- 仅给出模型结构与超参数：策略网络为 2 隐藏层 ReLU MLP；Normalizing Flow 使用 16 个 Flow Block，$NN_c$ 与耦合块均为 2 层 64 节点 LeakyReLU MLP，$NN_i$ 为 1 层 32 节点；
- 训练用 Adam 优化器，附录中给出超参数表。
- → **信息缺失**点：算力开销、可复现的 wall-clock 时间均未报告。

## 5. 实验数量与充分性

- **实验组数**：
  - 3 个 Classic Control 环境 × 5 个数据规模 × 10 次重复 ≈ 150 组；
  - 4 个 MuJoCo 环境 × 5 个种子；
  - 1 个 Walker2d 消融实验（4 种 $\alpha,\beta$ 组合）。
- **消融**：在 Walker2d 上对比了 $\alpha=1,\beta=0$（仅动力学损失）、$\alpha=0,\beta=1$（仅策略损失/BC）以及两种不同加权组合，结论是"**两项都重要，策略损失权重略高时效果最佳**"。
- **充分性评价**：
  - ✅ 覆盖离散/连续、低维/高维、不同数据量；
  - ✅ 与多个 SOTA 基线对比，且排除需在线交互/补充数据的方法，设定公平；
  - ⚠️ 仅在标准 benchmark 上做实验，未在真实机器人任务上验证；
  - ⚠️ 消融只在一个任务上进行，结论的泛化性有限。

## 6. 主要结论与发现

- **核心结论**：在严格批量离线 IL 设定下，MBIL 在 Classic Control 和 MuJoCo 上**一致优于**多种 SOTA IL/IRL/AIL 方法；
- **低数据高效性**：CartPole 上**仅需 1 条轨迹**即可接近专家性能，Acrobot/LunarLander 最多 3 条轨迹达到近专家水平；MuJoCo 上**单轨迹**就能在所有任务上达到近专家性能；
- **动力学损失的价值**：单纯策略损失（BC）和单纯动力学损失性能接近，但**两者结合**（且策略损失权重更高）才能稳定达到近专家水平；
- **规避偏差**：MBE 不依赖折扣因子、避免终止/奖励偏差、无需交替优化，因此对分布偏移更鲁棒。

## 7. 优点与亮点

- **新视角**：跳出"奖励估计 / 分布匹配"的范式，直接利用**轨迹数据唯一普适的数学结构（MBE）**进行学习；
- **方法简洁**：目标函数为单一监督损失，避免 DICE 类方法的 min-max 交替训练；
- **密度估计工具新颖**：首次将**条件 Normalizing Flow**用于模仿学习中的转移动力学估计，并通过噪声正则解决低数据问题；
- **实验设定严谨**：明确排除需要补充数据/在线交互的算法，对比公平；
- **低数据强鲁棒性**：在 1 条轨迹条件下仍能在多任务上达到近专家性能，对实际部署场景（数据稀缺）有现实意义。

## 8. 不足与局限

- **理论分析不足**：作者明确承认尚未给出**渐近与非渐近样本复杂度界**，缺少对方法收敛性的理论保证；
- **子优数据处理能力有限**：方法在专家演示假设下设计，未像 DemoDICE/SMODICE 那样处理**次优、混合质量**的演示数据；
- **算力与可复现性**：未报告 GPU 型号、训练时长、收敛所需的 epoch 数等，复现成本难以评估；
- **消融有限**：消融实验仅在 Walker2d 一个任务上完成，缺少对 Normalizing Flow 架构选择、噪声正则强度等关键组件的系统性分析；
- **实验域有限**：所有实验在仿真环境（MuJoCo、Classic Control）中进行，**未在真实机器人系统**上验证，部署鲁棒性未知；
- **密度估计误差传播**：当数据极少时，$P^{\pi_D}$ 和 $T$ 的估计误差会直接进入 MBE 损失，方法对这种误差的敏感性缺乏深入讨论；
- **依赖 RealNVP/FrEIA**：条件 Normalizing Flow 的实现细节（如耦合层结构、$NN_c$ 设计）会显著影响结果，但论文未对其选择做充分论证。

（完）
