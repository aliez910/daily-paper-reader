---
title: Imitation Learning from a Single Temporally Misaligned Video
title_zh: 从单个时间错位的视频中进行模仿学习
authors: "William Huey, Huaxiaoyue Wang, Anne Wu, Yoav Artzi, Sanjiban Choudhury"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=YV05KZt7v2"
tags: ["query:rob-il"]
score: 8.0
evidence: 提出ORCA方法，从单个视频中进行模仿学习，处理时间错位
tldr: 该论文针对单一视觉演示中时间错位导致模仿学习失败的问题，提出了ORCA（有序覆盖对齐）方法。该方法在序列级别进行匹配，确保子目标按序覆盖，从而在时间变化、不同具身或执行不一致的情况下仍能有效学习。实验表明ORCA能够从单个错位视频中成功学习顺序任务，提升了模仿学习的鲁棒性。这项工作为降低演示数据质量要求提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有帧级匹配方法无法保证时序顺序，需要序列级匹配来处理时间错位问题。
method: 提出ORCA（有序覆盖对齐），在序列级别进行子目标覆盖对齐，强制保持时序顺序。
result: 实验表明ORCA能从单个时间错位视频中有效学习顺序任务，优于帧级匹配方法。
conclusion: 序列级匹配是处理时间错位的关键，ORCA为降低演示数据要求提供了有效方案。
---

## Abstract
We examine the problem of learning sequential tasks from a single visual demonstration.
A key challenge arises when demonstrations are temporally misaligned due to variations in timing, differences in embodiment, or inconsistencies in execution. Existing approaches treat imitation as a distribution-matching problem, aligning individual frames between the agent and the demonstration. However, we show that such frame-level matching fails to enforce temporal ordering or ensure consistent progress.
Our key insight is that matching should instead be defined at the level of sequences. 
We propose that perfect matching occurs when one sequence successfully covers all the subgoals in the same order as the other sequence. 
We present ORCA (ORdered Coverage Alignment), a dense per-timestep reward function that measures the probability of the agent covering demonstration frames in the correct order. 
On temporally misaligned demonstrations, we show that agents trained with the ORCA reward achieve $4.5$x improvement ($0.11 \rightarrow 0.50$ average normalized returns) for Meta-world tasks and $6.6$x improvement ($6.55 \rightarrow 43.3$ average returns) for Humanoid-v4 tasks compared to the best frame-level matching algorithms. 
We also provide empirical analysis showing that ORCA is robust to varying levels of temporal misalignment. The project website is at https://portal-cornell.github.io/orca/

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义

- **研究动机**：在机器人模仿学习中，从单个视觉演示学习顺序任务时，演示视频常因执行速度、不同机器人形态或一致性差异而出现**时间错位**（temporally misaligned）。现有方法将模仿视为分布匹配问题，逐帧对齐智能体与演示，但这类**帧级匹配**无法强制保持时间顺序或保证一致的任务进展。
- **核心问题**：如何从单个时间错位的演示视频中有效学习顺序任务，避免帧级对齐的局限。
- **整体意义**：提出一种基于**序列级匹配**的新思路，降低对演示数据质量（特别是时序一致性）的要求，拓宽模仿学习在真实场景中的适用性。

## 2. 方法论

- **核心思想**：匹配应在**序列级别**定义。完美匹配应要求“一个序列以与另一序列相同的顺序成功覆盖所有子目标”。
- **关键技术**：  
  - **ORCA（Ordered Coverage Alignment，有序覆盖对齐）**：一种密集的每时间步奖励函数。  
  - 该奖励函数衡量智能体状态序列以**正确顺序**覆盖演示帧（视为子目标）的概率。  
  - 不再逐帧独立匹配，而是评估整个序列的覆盖顺序一致性。
- **算法流程简述**：
  1. 给定演示视频帧序列和智能体执行轨迹。
  2. 构建一个概率模型，为每个智能体状态分配一个与演示帧覆盖相关的分数。
  3. 通过强制覆盖必须按演示顺序进行，定义奖励：如果智能体按序覆盖越来越多演示帧，则奖励递增。
  4. 使用该奖励信号（可结合强化学习或行为克隆）训练策略。

## 3. 实验设计

- **数据集／场景**：
  - **Meta-world**：多种机器人操作任务。
  - **Humanoid-v4**：高维人形机器人控制任务。
- **基准对比**：与**最佳的帧级匹配算法**（best frame-level matching algorithms）进行比较。
- **评价指标**：
  - Meta-world：平均归一化回报（average normalized returns）。
  - Humanoid-v4：平均回报（average returns）。
- **鲁棒性分析**：测试ORCA对**不同程度时间错位**（varied levels of temporal misalignment）的表现。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量或训练时长等具体算力信息。仅提及在模拟环境（Meta-world、Humanoid-v4）中进行实验，未提供训练基础设施细节。

## 5. 实验数量与充分性

- **实验数量**：基于摘要，主要报告了两个任务套件（Meta-world和Humanoid-v4）的对比结果，并包含对不同错位等级的分析。未提及其他数据集或额外的消融实验（如不同超参数、网络结构等）。
- **充分性与客观性**：
  - 实验对比了当前最好帧级方法，且绩效提升显著（4.5x和6.6x），结果具有说服力。
  - 鲁棒性实验增加了对方法适用边界的理解。
  - **局限性**：由于提供文本信息有限，无法判断是否进行了充分的消融、跨领域泛化或真实机器人实验；实验覆盖范围相对单一（仅两个模拟环境），公平性和全面性需在正式论文中确认。

## 6. 论文的主要结论与发现

- **帧级匹配无法保证时序顺序是模仿失败的关键原因**。
- **序列级匹配（ORCA）可有效从单个时间错位演示中学习顺序任务**。
- ORCA在Meta-world上平均归一化回报提升4.5倍（0.11→0.50），在Humanoid-v4上平均回报提升6.6倍（6.55→43.3），显著优于帧级方法。
- ORCA对不同程度的时间错位具有良好的鲁棒性。

## 7. 优点

- **创新性**：将模仿学习中的匹配粒度从帧级提升到序列级，明确引入**顺序约束**，解决了长期存在的时序错位问题。
- **方法简洁有效**：奖励函数设计直观，基于覆盖顺序的概率，易于结合现有强化学习框架。
- **实验表现突出**：在两类不同难度的连续控制任务上均取得数倍提升，验证了方法的普适性。
- **鲁棒性分析**：针对关键变量（错位程度）进行了系统测试，增强了结论的可信度。

## 8. 不足与局限

- **实验覆盖范围有限**：仅报道了两个模拟环境的结果，缺乏真实机器人平台验证，也未与其他序列级方法（如选项学习、时间抽象）进行比较。
- **数据要求**：仅从“单个”演示学习，虽然降低了对数据量的需求，但对演示长度、子目标定义等仍有潜在假设，复杂任务中可能不充分。
- **算力与复现细节缺失**：未提供训练资源、超参数设置等关键复现信息，影响可复现性评估。
- **潜在偏差风险**：演示错位类型可能仅限于文中模拟的几种变化（速度、形态等），未覆盖更复杂的时间变形（如部分倒序、缺失子目标等）。
- **应用限制**：方法假设子目标与演示帧近似对应，对于高度抽象或非视觉子目标的任务可能需要调整。

（完）
