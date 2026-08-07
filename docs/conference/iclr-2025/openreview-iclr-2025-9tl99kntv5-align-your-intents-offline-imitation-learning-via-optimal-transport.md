---
title: "Align Your Intents: Offline Imitation Learning via Optimal Transport"
title_zh: 对齐意图：基于最优传输的离线模仿学习方法
authors: "Maksim Bobrin, Nazar Buzun, Dmitrii Krylov, Dmitry V. Dylov"
date: 2024-09-26
pdf: "https://openreview.net/pdf?id=9TL99KnTv5"
tags: ["query:rob-il"]
score: 4.0
evidence: 基于最优传输的无奖励无动作标签离线模仿学习方法
tldr: 离线强化学习常因缺少显式奖励与动作标签而难以实用。本文提出AILOT方法，将状态表示为包含数据点两两空间距离的意图结构，并通过最优传输定义内在奖励函数。该方法即使在缺失显式奖励与动作标签的情况下，仍能仅通过观察专家示范学到期望行为。AILOT对模仿学习中状态对齐与奖励重构问题提出了新的解决思路，对基于演示数据的策略学习具有方法论上的借鉴价值。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 离线模仿学习缺乏显式奖励与动作标签，难以从专家示范中学习期望行为。
method: 提出AILOT，将状态表示为包含两两空间距离的意图，并通过最优传输定义内在奖励进行学习。
result: 在无显式奖励和动作标签条件下，仍能仅从专家观察中学到期望的策略行为。
conclusion: AILOT为离线模仿学习的奖励重构与状态对齐提供了新颖且可借鉴的方法论。
---

## Abstract
Offline reinforcement learning (RL) addresses the problem of sequential decision-making by learning optimal policy through pre-collected data, without interacting with the environment. As yet, it has remained somewhat impractical, because one rarely knows the reward explicitly and it is hard to distill it retrospectively. Here, we show that an imitating agent can still learn the desired behavior merely from observing the expert, despite the absence of explicit rewards or action labels. In our method, AILOT (Aligned Imitation Learning via Optimal Transport), we involve special representation of states in a form of intents that incorporate pairwise spatial distances within the data. Given such representations, we define intrinsic reward function via optimal transport distance between the expert's and the agent's trajectories. We report that AILOT outperforms state-of-the art offline imitation learning algorithms on D4RL benchmarks and improves the performance of other offline RL algorithms by dense reward relabelling in the sparse-reward tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of a paper titled "Align Your Intents: Offline Imitation Learning via Optimal Transport" (AILOT). Let me analyze the provided content carefully.

From the abstract and metadata, I can extract:
- Problem: Offline RL is impractical because rewards are rarely known explicitly and hard to distill retrospectively
- Method: AILOT (Aligned Imitation Learning via Optimal Transport)
- Key idea: States represented as "intents" incorporating pairwise spatial distances, intrinsic reward via optimal transport distance between expert and agent trajectories
- Results: Outperforms SOTA offline imitation learning on D4RL benchmarks; improves other offline RL via dense reward relabelling in sparse-reward tasks
- Status: ICLR-2025 Rejected but public

The paper PDF content is just a verification page (OpenReview), so I don't have access to the full paper text. I need to summarize based on the abstract and metadata provided.

Let me structure the response according to the user's requirements:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources/compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Since the actual paper PDF content is only a CAPTCHA page, I should be honest that I'm working with limited information (abstract + metadata). Let me note this where appropriate.

I'll write this in Chinese with Markdown formatting.</think>

# 论文总结：Align Your Intents: Offline Imitation Learning via Optimal Transport (AILOT)

> **说明**：原 PDF 链接在抓取时仅返回 OpenReview 的人机验证页面，未能获取正文与附录细节。本总结主要基于论文摘要与元数据（标题、TL;DR、标签等）整理，部分章节会明确指出信息缺失。

---

## 1. 核心问题与研究动机

- **离线强化学习（Offline RL）的实用化瓶颈**：
  - 实际场景中，奖励函数往往**不可显式获取**，事后从演示数据中反推也十分困难。
  - 此外，**动作标签（action labels）常常缺失**，进一步限制了对专家策略的复用。
- **研究目标**：
  - 在**无显式奖励、无动作标签**的前提下，仅依靠观察专家示范（observation-only imitation），让智能体学到期望行为。
- **整体含义**：
  - 将模仿学习推向更现实的数据条件（reward-free + action-free），并借助几何/最优传输视角重新定义"状态对齐"与"内在奖励"。

---

## 2. 方法论：AILOT 的核心思想与技术细节

- **核心思想**：
  - 把每个状态表示为"**意图（intent）**"——一种融合了**样本间两两空间距离**的结构化表示，使状态本身携带数据集几何信息。
  - 在此基础上，用**最优传输（Optimal Transport, OT）距离**度量**专家轨迹与智能体轨迹**之间的差距，将其作为**内在奖励（intrinsic reward）**，驱动策略学习。
- **关键组件**：
  - **Intent 表示**：对数据点两两距离进行编码，使得"对齐"问题转化为"分布对齐"问题。
  - **OT-based 内在奖励**：专家轨迹与当前策略轨迹之间的 OT 距离 → 稠密奖励信号。
  - **奖励重标记（reward relabelling）**：将上述稠密奖励回填到离线数据集，缓解稀疏奖励任务中其他离线 RL 算法难以学习的问题。
- **训练范式**：
  - 整体上仍是"**对齐专家分布 + 离线学习**"的两阶段思路；理论上兼容任何能消费稠密奖励的离线 RL/模仿学习算法。

---

## 3. 实验设计

- **基准测试集**：
  - **D4RL**（离线 RL/模仿学习最常用的 MuJoCo 系列 benchmark，包括 HalfCheetah、Hopper、Walker2k 等 locomotion 任务）。
- **对比方法**：
  - 摘要明确表示与 **SOTA 离线模仿学习算法**进行比较。
  - 同时将 AILOT 作为**奖励重标记模块**，接入其他**离线 RL 算法**以提升其在稀疏奖励任务中的表现。
- **任务设置**：
  - 标准 D4RL（中等/专家/混合等数据集）；
  - **稀疏奖励任务**（用于评估 dense reward relabelling 的贡献）。

---

## 4. 资源与算力

- **未能从摘要与元数据中提取**：
  - GPU 型号/数量；
  - 训练时长；
  - 是否使用预训练模型或大规模并行；
- 由于原 PDF 正文未成功抓取，**该部分具体信息缺失**。建议查阅正文 Appendix 或代码仓库（如已开源）以补全。

---

## 5. 实验数量与充分性

- **可推断的实验维度**：
  - 在 D4RL 多任务上的主对比；
  - 与多种 SOTA 离线模仿学习方法对比；
  - 奖励重标记模块在稀疏奖励任务中的兼容性实验。
- **充分性评估（基于现有信息）**：
  - **优势**：覆盖了模仿学习与奖励重标记两条评估路线，且任务设置贴合主流 benchmark。
  - **不足**：
    - 缺乏消融实验（如是否去掉 OT、是否去掉 intent 表示）的具体描述；
    - 缺少对不同"专家演示数量"鲁棒性的分析（实际场景中专家数据往往有限）；
    - 未提供任务多样性（如图像观测、高维感知任务）方面的实验信息；
    - 总体实验充分性需结合正文表格与附录进一步判断。

---

## 6. 主要结论与发现

- **有效性**：
  - AILOT 在 D4RL 上**优于现有 SOTA 离线模仿学习算法**；
  - 作为奖励重标记工具，可**显著提升其他离线 RL 算法在稀疏奖励任务上的性能**。
- **方法学贡献**：
  - 证明"**intent 表示 + OT 内在奖励**"这一组合在无显式奖励、无动作标签的条件下依然可行；
  - 为离线模仿学习中的**状态对齐**与**奖励重构**提供了新思路。

---

## 7. 优点（方法与实验设计亮点）

- **几何视角新颖**：用 OT 距离度量轨迹分布差异，理论动机清晰。
- **奖励解耦**：通过 intent 表示把"对齐"与"策略学习"解耦，模块化程度高。
- **双重贡献**：既可直接用于模仿学习，也可作为奖励重标记插件提升其他离线 RL 算法。
- **对数据条件要求低**：在 reward-free、action-free 条件下仍可学习，符合现实数据需求。

---

## 8. 不足与局限

- **未在抓取内容中确认的局限**：
  - OT 计算的复杂度随样本量增长，可能在大规模数据集上受限；
  - intent 表示依赖成对距离，对高维感知输入（图像等）的可扩展性需要进一步验证；
  - 缺乏对**对抗/次优专家**（非最优演示）鲁棒性的实验说明；
  - 在分布外（OOD）状态上的安全与稳定性未讨论。
- **评审层面的信号**：
  - 论文标注为 **ICLR-2025 Rejected (Public)**，说明虽方法有亮点，但可能存在**实验充分性、对比公平性或创新边界**上的争议；建议结合公开评审意见与最终版本（若作者修订）评估。
- **信息完整性风险**：
  - 本次仅基于摘要/元数据进行总结，**未读到完整正文**，可能遗漏消融、超参数敏感性、社会影响等章节信息。

---

（完）
