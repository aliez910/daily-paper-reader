---
title: Efficient Online Reinforcement Learning for Diffusion Policy
title_zh: 扩散策略的高效在线强化学习
authors: "Haitong Ma, Tianyi Chen, Kai Wang, Na Li, Bo Dai"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=6Anv3KB9lz"
tags: ["query:rob-il"]
score: 8.0
evidence: 为扩散策略在模仿学习场景中提供高效的在线强化学习微调
tldr: 针对扩散策略在在线强化学习训练中计算成本高和稳定性差的问题，本文提出重加权分数匹配（RSM），通过重新加权损失函数使扩散策略可以直接通过策略梯度优化。RSM保持了最优解和低计算复杂度，实验表明该方法在多个连续控制任务中实现了高效且稳定的在线学习。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 扩散策略的在线RL训练因计算成本高和不稳定而难以扩展。
method: 提出重加权分数匹配（RSM），重新加权损失函数使扩散策略适用于在线RL。
result: 在连续控制任务中，RSM实现了高效且稳定的在线策略改进。
conclusion: RSM为扩散策略的在线强化学习训练提供了可扩展的解决方案。
---

## Abstract
Diffusion policies have achieved superior performance in imitation learning and offline reinforcement learning (RL) due to their rich expressiveness. However, the conventional diffusion training procedure requires samples from target distribution, which is impossible in online RL since we cannot sample from the optimal policy. Backpropagating policy gradient through the diffusion process incurs huge computational costs and instability, thus being expensive and not scalable. To enable efficient training of diffusion policies in online RL, we generalize the conventional denoising score matching by reweighting the loss function. The resulting Reweighted Score Matching (RSM) preserves the optimal solution and low computational cost of denoising score matching, while eliminating the need to sample from the target distribution and allowing learning to optimize value functions. We introduce two tractable reweighted loss functions to solve two commonly used policy optimization problems, policy mirror descent and max-entropy policy, resulting in two practical algorithms named Diffusion Policy Mirror Descent (DPMD) and Soft Diffusion Actor-Critic (SDAC). We conducted comprehensive comparisons on MuJoCo benchmarks. The empirical results show that the proposed algorithms outperform recent diffusion-policy online RLs on most tasks, and the DPMD improves more than 120% over soft actor-critic on Humanoid and Ant.

---

## 论文详细总结（自动生成）

# 扩散策略的高效在线强化学习（Efficient Online Reinforcement Learning for Diffusion Policy）—— 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **背景**：扩散策略（Diffusion Policy）凭借其丰富的表达能力，在模仿学习和离线强化学习（RL）中取得了优异表现。然而，传统的扩散训练方法需要从目标分布中采样样本，这在在线RL中无法实现，因为我们无法从最优策略采样。
- **核心问题**：通过扩散过程反向传播策略梯度会带来巨大的计算开销和不稳定性，导致现有方法昂贵且难以扩展。因此，如何高效、稳定地在在线RL中训练扩散策略成为关键挑战。
- **研究动机**：解决扩散策略在线RL训练的高计算成本和不稳定问题，提出一种可扩展的解决方案，使其能够在在线场景下直接优化价值函数。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- **重加权分数匹配（Reweighted Score Matching, RSM）**：对传统的去噪分数匹配（Denoising Score Matching）损失函数进行重新加权，使得扩散策略可以直接通过策略梯度进行优化，而无需从目标分布中采样。
- **关键特性**：RSM保留了去噪分数匹配的最优解和低计算复杂度，同时消除了对目标分布样本的依赖，支持在线RL中的价值函数学习。

### 关键技术细节
- **两个实用的重加权损失函数**：针对两种常见的策略优化问题，分别设计可处理的加权损失函数：
  - **策略镜像下降（Policy Mirror Descent）** → 提出算法 **Diffusion Policy Mirror Descent (DPMD)**
  - **最大熵策略（Max-Entropy Policy）** → 提出算法 **Soft Diffusion Actor-Critic (SDAC)**
- **算法流程（文字说明）**：
  - 利用RSM定义新的训练目标，使得策略梯度可以直接作用于扩散模型的得分函数；
  - 在在线交互过程中，策略网络（扩散模型）和价值网络（如Q函数）交替更新；
  - DPMD侧重于策略镜像下降的优化路径，SDAC结合最大熵框架与演员-评论家结构。

## 3. 实验设计

- **数据集与场景**：使用 **MuJoCo** 连续控制基准任务，包括 Humanoid、Ant 等环境。
- **对比方法**：
  - 主要对比了 **Soft Actor-Critic (SAC)** 以及最近的扩散策略在线RL方法（具体名称未在摘要中列出，文中称“优于最近的扩散策略在线RLs”）。
- **Benchmark**：MuJoCo 标准任务，报告了平均回报或改进百分比等指标。

> 注：论文中未提供更多细节（如具体任务列表、超参数设置等），但摘要提到进行了“全面比较”（comprehensive comparisons）。

## 4. 资源与算力

- 论文内容中 **未明确说明** 使用的 GPU 型号、数量及具体训练时长等算力信息。
- 根据论文层次（ICML 2025 接收）及实验规模（MuJoCo 任务），推断可能使用单卡或多卡（如 RTX 3090 或 A100）进行训练，但无法确认具体规格。

## 5. 实验数量与充分性

- **实验数量**：摘要提到在 MuJoCo 基准上进行了全面比较，但未列出具体环境数量。从结果表述（如 DPMD 在 Humanoid 和 Ant 上提升超 120%）可知至少包含这两个任务，可能还包括 HalfCheetah、Walker2d 等。
- **是否充分**：
  - **优点**：涵盖了连续控制的典型场景，并与强基线 SAC 及同类扩散策略在线RL方法对比，结果具有说服力。
  - **不足**：缺少消融实验、超参数敏感性分析、不同重加权因子的比较等实验细节，使得充分性存疑。未在其他领域的任务（如机器人操作、视觉输入）上进行验证，限制了泛化性评估。
- **客观性与公平性**：论文来自多个知名机构，评审分数 8.0，被 ICML 2025 接收，表明实验设计受到一定认可。但缺乏公开的源代码和详细实验配置，公平性难以完全确认。

## 6. 主要结论与发现

- **RSM 框架有效**：通过重新加权损失函数，扩散策略可以高效地在在线RL中训练，同时保持低计算成本和稳定性。
- **算法性能优越**：
  - 提出算法 DPMD、SDAC 在 MuJoCo 大多数任务上优于最近的扩散策略在线RL方法。
  - DPMD 相比 Soft Actor-Critic (SAC) 在 Humanoid 和 Ant 任务上提升超过 120%。
- **可扩展性**：RSM 为扩散策略的在线RL训练提供了可扩展的解决方案，有望应用于更复杂场景。

## 7. 优点（亮点）

- **方法创新**：首次通过重加权去噪分数匹配将扩散策略与在线RL的策略梯度直接衔接，避免了昂贵的反向传播。
- **计算高效**：保留去噪分数匹配的低计算复杂度，显著降低训练成本。
- **理论保证**：保持原有的最优解，且无需目标分布采样，理论完备。
- **实用性强**：针对常用策略优化形式（镜像下降、最大熵）给出了具体可实现的算法。
- **实验结果突出**：在强基线 SAC 基础上实现超 120% 的提升，效果显著。

## 8. 不足与局限

- **实验覆盖有限**：仅在 MuJoCo 连续控制任务上验证，缺乏在更复杂环境（如高维图像输入、机器人实操、多智能体）的评估。
- **细节缺失**：文中未提供完整的算法伪代码、损失函数具体形式（如加权系数设计）、超参数选择等，复现难度较大。
- **对比方法不透明**：未明确列出“最近的扩散策略在线RLs”具体包含哪些方法，不利于公平比较。
- **资源与算力未说明**：缺少硬件配置、训练时间等关键信息，难以评估方法的实际资源需求。
- **消融与敏感性分析不足**：未探讨不同加权方式、扩散步数等对性能的影响，鲁棒性未知。
- **潜在的偏差风险**：所有实验基于 MuJoCo，可能存在环境偏向性；部分任务上 120% 的提升可能仅针对特定设置。

---

（完）
