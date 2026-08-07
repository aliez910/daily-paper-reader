---
title: Zero-Shot Offline Imitation Learning via Optimal Transport
title_zh: 基于最优传输的零样本离线模仿学习
authors: "Thomas Rupf, Marco Bagatella, Nico Gürtler, Jonas Frey, Georg Martius"
date: 2024-09-27
pdf: "https://openreview.net/pdf?id=vDecbmWf6w"
tags: ["query:rob-il"]
score: 4.0
evidence: 基于目标条件策略的零样本模仿学习
tldr: 现有零样本模仿学习方法通常将专家示范视为目标序列，由高层目标选择器与底层目标条件策略组合执行，容易出现短视行为——即对每个子目标的即时追逐会损害长期目标。本文提出一种直接优化模仿学习占据匹配目标的方法，通过将目标条件值函数提升为占据之间的距离度量，并借助学习到的世界模型进行近似。该方法缓解了短视行为问题。该工作为模仿学习提供了一种可迁移的理论与方法工具，但摘要中并未明确聚焦于基于视觉的机器人操作。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 将示范视为目标序列的零样本模仿学习容易产生短视行为，损害长期目标。
method: 将目标条件值函数提升为占据度量间的距离，并借助学习到的世界模型近似求解。
result: 缓解了逐目标追逐导致的短视问题，但未明确报告视觉机器人操作结果。
conclusion: 为占据匹配视角下的模仿学习提供了一种更原则化的方法路径。
---

## Abstract
Zero-shot imitation learning algorithms hold the promise of reproducing unseen behavior from as little as a single demonstration at test time.
Existing practical approaches view the expert demonstration as a sequence of goals, enabling imitation with a high-level goal selector, and a low-level goal-conditioned policy. 
However, this framework can suffer from myopic behavior: the agent's immediate actions towards achieving individual goals may undermine long-term objectives.
We introduce a novel method that mitigates this issue by directly optimizing the occupancy matching objective that is intrinsic to imitation learning. 
We propose to lift a goal-conditioned value function to a distance between occupancies, which are in turn approximated via a learned world model.
The resulting method can learn from offline, suboptimal data, and is capable of non-myopic, zero-shot imitation, as we demonstrate in complex, continuous benchmarks.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of a paper based on the provided metadata. Let me analyze the content carefully.

The paper is "Zero-Shot Offline Imitation Learning via Optimal Transport" (基于最优传输的零样本离线模仿学习). However, I notice that the PDF content extraction failed (just a CAPTCHA page), so I need to rely on the metadata provided.

Let me organize my response according to the 8 requested points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Advantages
8. Limitations

I should be honest about what information is available and what is not. The actual PDF content is not accessible (only CAPTCHA page), so I'll need to work from the metadata and abstract provided.

Let me draft a comprehensive summary in Chinese Markdown format.</think>

# 论文总结：基于最优传输的零样本离线模仿学习

> 注：本论文 PDF 抓取页面为 OpenReview 的浏览器验证（CAPTCHA）页面，未能获取正文具体内容。以下总结主要依据论文元数据、摘要及元信息中的方法/结论描述展开，凡涉及正文细节之处均明确标注为"未明确披露"。

---

## 1. 核心问题与研究动机

- **研究主题**：零样本离线模仿学习（Zero-Shot Offline Imitation Learning），即在测试时仅凭少量（甚至单条）未见过的专家示范即可复现专家行为。
- **现有方法的范式**：将专家示范视作一串目标序列（goal sequence），通过"高层目标选择器 + 底层目标条件策略"的组合执行模仿。
- **核心痛点**：该范式容易产生**短视（myopic）行为**——底层策略为追求每一个即时子目标，可能与长期目标相冲突，从而损害整体任务完成质量。
- **作者主张**：应当直接优化模仿学习**本质上蕴含的占据匹配（occupancy matching）目标**，而不是仅仅在目标序列层面做事后组合。

## 2. 方法论

- **总体思路**：把模仿学习重新放到占据匹配的视角下，给出更原则化的优化路径。
- **关键技术点**：
  - **目标条件值函数的提升**：将通常用作"单步目标达成度"的目标条件值函数（goal-conditioned value function）**提升为占据之间的距离度量**。也就是说，把值函数当作衡量两个状态–动作占据分布（occupancy）相似度的工具，而不仅仅是一个奖励/进度信号。
  - **借助学习世界模型进行近似**：实际占据难以直接枚举或计算，作者借助**学习到的世界模型（learned world model）**对占据进行近似估计，从而让上述距离度量在实践中可计算、可求优。
  - **与最优传输的关联**：题目中的"Optimal Transport"暗示占据间的距离度量借鉴了最优传输/分布匹配的思想，将模仿学习与 OT 框架进行连接。
- **算法能力**：
  - 支持**离线（offline）**且可使用**次优（suboptimal）**数据进行训练，摆脱对在线交互或高质量专家数据的依赖。
  - 具备**非短视（non-myopic）**、**零样本（zero-shot）**模仿能力，无需对每个子目标进行即时贪心追逐。

## 3. 实验设计

- **任务与基准**：摘要中提到在 **复杂的、连续控制（complex, continuous）** 的基准测试上验证，强调对"非短视零样本模仿"的检验。
- **具体数据集/场景**：正文未抓取到，因此**未明确披露**使用了哪些具体 benchmark（可能包括连续控制类的 locomotion 或 manipulation 等标准模仿学习环境）。
- **对比方法**：正文未抓取到，因此**未明确披露**对比了哪些基线方法；通常此类工作会与基于目标序列的零样本模仿方法（如 GOAL-GAIL、SAIL 等思路）以及 GAIL/BC 等经典模仿学习方法比较。
- **评估指标**：未明确披露，但根据领域惯例应包含任务成功率、累积回报、占据匹配距离等。

## 4. 资源与算力

- 论文 PDF 未能抓取到正文，**未明确披露**：
  - 使用的 GPU 型号与数量；
  - 总训练时长或单个任务的训练耗时；
  - 是否涉及分布式训练或大规模超参搜索。
- 这是该论文总结的一个**信息缺口**，无法基于现有材料进一步评价其算力代价。

## 5. 实验数量与充分性

- 在可获得的信息中，摘要仅描述"在复杂的连续基准上验证"，**没有具体列出实验组数、消融实验数量或不同数据集/任务的覆盖**。
- 因此，从**实验充分性、客观性与公平性**的角度，目前**无法做出有依据的判断**：
  - 是否做了对短视行为的专门消融？
  - 是否对比了不同质量的次优数据？
  - 是否在不同随机种子下统计了方差？
  - 是否报告了视觉/操作类任务？
- 元数据明确指出："摘要中并未明确聚焦于基于视觉的机器人操作"，说明其在视觉机器人操作这一重要应用场景上的实验覆盖存在不确定性。

## 6. 主要结论与发现

- **方法层面**：
  - 把目标条件值函数提升为占据距离度量是可行且有效的；
  - 用学习到的世界模型近似占据，使得离线次优数据上的占据匹配优化成为可能。
- **行为层面**：
  - 缓解了既有"目标序列 + 即时追逐"范式带来的**短视问题**；
  - 实现了**非短视的零样本模仿**。
- **理论/工具层面**：为占据匹配视角下的模仿学习提供了一种更原则化的方法路径，具有**可迁移的理论与方法价值**。
- **数据利用层面**：能够从**离线、次优**数据中学习，扩大了模仿学习可用的数据来源。

## 7. 优点与亮点

- **视角新颖**：不再把示范当作"目标序列"来做事后拼接，而是直接回到模仿学习最根本的占据匹配目标。
- **概念桥梁**：把"目标条件值函数"重新解释为"占据距离"，为连接 RL 值函数与分布匹配（最优传输）提供了优雅的桥梁。
- **数据友好**：支持**离线 + 次优数据**训练，对实际数据采集具有重要意义。
- **应用价值**：在复杂连续控制任务上验证了**非短视、零样本**模仿能力，覆盖了既有方法的一个明显弱点。
- **方法论通用性**：元数据评注指出该工作"为模仿学习提供了一种可迁移的理论与方法工具"。

## 8. 不足与局限

- **信息可获取性**：本文为 ICLR-2025 **Rejected-Public** 投稿（根据元数据），且本次抓取仅获得 CAPTCHA 页面，正文细节缺失，上述总结不可避免存在不确定性。
- **实验覆盖不明**：未明确说明是否包含**视觉机器人操作（vision-based robotic manipulation）**实验——这恰恰是模仿学习最受关注的应用场景之一。
- **基线对比不充分披露**：从现有信息无法判断对比方法的覆盖是否公平、是否包含当前 SOTA。
- **算力与可复现性**：未披露 GPU 数量、训练时长、随机种子数等关键信息，影响**复现与可比性评估**。
- **方法依赖项**：依赖**学习到的世界模型**进行占据近似，这意味着方法性能受世界模型质量影响；世界模型误差如何传播到模仿学习目标，在现有材料中没有讨论。
- **零样本承诺与代价**：所谓"零样本"依赖测试时的目标条件值/世界模型泛化能力，但缺乏对**分布外（OOD）目标**鲁棒性的明确分析。
- **应用限制**：从描述看偏向连续控制类任务，是否能扩展到**高维视觉输入、长视野语言指令任务**仍有待进一步验证。
- **应用偏差风险**：缺乏对失败案例、对错误占据匹配的敏感度分析，存在**未充分讨论的失败模式与偏差风险**。

（完）
