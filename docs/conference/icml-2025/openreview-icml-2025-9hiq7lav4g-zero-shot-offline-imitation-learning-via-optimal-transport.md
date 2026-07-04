---
title: Zero-Shot Offline Imitation Learning via Optimal Transport
title_zh: 基于最优传输的零样本离线模仿学习
authors: "Thomas Rupf, Marco Bagatella, Nico Gürtler, Jonas Frey, Georg Martius"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9hiq7LaV4G"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过最优传输和占用匹配实现零样本模仿学习
tldr: 现有零样本模仿学习将演示分解为目标序列，容易导致短视行为。本文提出基于最优传输的方法，直接优化占用匹配目标，并利用学习的世界模型估计占用距离。该方法在多个控制任务上实现了更好的长期模仿效果。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 基于目标的模仿学习容易产生短视行为，忽视长期目标。
method: 使用最优传输提升目标条件值函数到占用距离，并通过世界模型近似。
result: 在模拟环境中实现了高效且可靠的零样本模仿。
conclusion: 全局占用匹配可有效改善零样本模仿的长周期性能。
---

## Abstract
Zero-shot imitation learning algorithms hold the promise of reproducing unseen behavior from as little as a single demonstration at test time. Existing practical approaches view the expert demonstration as a sequence of goals, enabling imitation with a high-level goal selector, and a low-level goal-conditioned policy. However, this framework can suffer from myopic behavior: the agent's immediate actions towards achieving individual goals may undermine long-term objectives. We introduce a novel method that mitigates this issue by directly optimizing the occupancy matching objective that is intrinsic to imitation learning. We propose to lift a goal-conditioned value function to a distance between occupancies, which are in turn approximated via a learned world model. The resulting method can learn from offline, suboptimal data, and is capable of non-myopic, zero-shot imitation, as we demonstrate in complex, continuous benchmarks. The code is available at https://github.com/martius-lab/zilot.

---

## 论文详细总结（自动生成）

基于提供的论文摘要与元数据，我按照要求对内容进行结构化总结。需说明的是，原文信息有限，部分要点无法详细展开，将如实指出。

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：现有的零样本模仿学习算法（zero-shot imitation learning）通常将专家演示分解为一系列目标（goal sequence），通过高层目标选择器与底层目标条件策略来实现模仿。但这种框架容易导致**短视行为（myopic behavior）**：智能体为达成单个目标而采取的行动可能损害长期目标。
- **整体含义**：如何在不依赖大量演示或在线交互的情况下，实现既能跟随任务目标又具备长期眼光的行为复制，是当前离线模仿学习面临的关键挑战。

## 2. 方法论：核心思想、关键技术细节、算法流程
- **核心思想**：直接优化模仿学习内在的**占用匹配目标（occupancy matching objective）**，而非通过目标序列分解来近似模仿。
- **关键步骤**：
  1. **提升目标条件值函数**：将原有的目标条件值函数（goal-conditioned value function）扩展为**占用距离（distance between occupancies）**，从而更好地衡量当前行为与专家行为在状态-动作分布上的差异。
  2. **占用距离的近似**：利用**学习的世界模型（learned world model）**来估计占用距离，使得该距离可以在不依赖真实环境过渡的情况下计算。
  3. **零样本离线模仿**：最终的算法（命名为 ZILOT）可以直接从**离线、次优数据（offline, suboptimal data）**中学习，并在测试时仅需一条专家演示实现零样本模仿。
- **算法流程**（文字说明）：
  - 预训练世界模型，使其能够预测状态转移和奖励。
  - 基于世界模型学习目标条件值函数，并将其提升为占用距离度量。
  - 在给定单一专家演示后，通过最小化占用距离来调整策略输出，完成零样本模仿。

## 3. 实验设计
- **数据集/场景**：论文在**复杂连续控制基准（complex, continuous benchmarks）**上评估，具体环境名称未在摘要或元数据中列出。
- **Benchmark**：未明确提及具体基准（如 D4RL、Meta-World、DMControl 等）。
- **对比方法**：未在提供内容中说明与哪些方法进行了对比，可能包括其他零样本模仿学习和离线模仿学习方法。

## 4. 资源与算力
- **文中未提及**摘要和元数据中均未涉及 GPU 型号、数量、训练时长等计算资源信息。

## 5. 实验数量与充分性
- **实验数量**：未明确报告实验组数或消融实验数量。根据摘要描述的“在复杂连续基准上演示”推测可能进行了多个任务上的评估，但缺乏具体数据。
- **充分性与公平性**：无法从现有信息判断实验的统计严谨性、对比是否公平或消融设计的完整性。摘要仅声称方法有效，未提供实验细节。

## 6. 主要结论与发现
- **全局占用匹配**可有效改善零样本模仿的**长周期性能**。
- 从离线、次优数据中学习的方法能够实现**非短视（non-myopic）**的零样本模仿，在连续控制任务中取得高效、可靠的结果。

## 7. 优点
- **方法论创新**：将零样本模仿问题重新定义为占用匹配优化，突破了基于目标序列分解的框架，避免短视行为。
- **技术亮点**：
  - 利用学习的世界模型估计占用距离，降低了在线交互需求。
  - 能从**次优离线数据**中学习，拓宽了数据来源，增强了实用性。
- **理论价值**：建立了目标条件值函数与占用距离之间的桥梁，为占用匹配优化提供了可计算的形式。

## 8. 不足与局限
- **实验覆盖不全**：原文未提供实验环境、数据集、对比方法、性能指标等关键细节，难以评估方法在实际场景中的泛化能力和与现有工作的优劣关系。
- **潜在偏差风险**：世界模型的准确性可能影响占用距离估计，若模型泛化不佳，可能导致模仿失败。
- **应用限制**：零样本能力依赖于单条演示，对于复杂长期任务（如长视域或稀疏奖励场景）的有效性未得到验证。
- **算力与复现**：未说明 GPU 需求，增加了复现门槛。

（完）
