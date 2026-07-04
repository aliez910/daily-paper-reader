---
title: "A Large Recurrent Action Model: xLSTM enables Fast Inference for Robotics Tasks"
title_zh: 大规模循环动作模型：xLSTM实现机器人任务快速推理
authors: "Thomas Schmied, Thomas Adler, Vihang Prakash Patil, Maximilian Beck, Korbinian Pöppel, Johannes Brandstetter, Günter Klambauer, Razvan Pascanu, Sepp Hochreiter"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=J2JxJ0P1LI"
tags: ["query:rob-il"]
score: 6.0
evidence: 大规模循环动作模型用于机器人快速推理，与视觉-动作主题相关
tldr: 本文针对Transformer在机器人实时应用中推理速度慢的问题，提出基于xLSTM的大规模循环动作模型，通过现代循环架构实现快速推理。该模型在离线数据集上序列建模，能够在保持性能的同时显著缩短推理时间。实验表明其在多种机器人任务上达到高效实时控制，为视觉-动作模型的低延迟部署提供了新方案。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 基于Transformer的机器人策略模型推理速度慢，难以满足实时控制需求。
method: 采用现代循环神经网络xLSTM构建大规模动作模型，在离线数据集上序列建模实现快速推理。
result: xLSTM模型在推理速度上显著优于Transformer，同时保持相当的性能。
conclusion: xLSTM是一种高效且可扩展的机器人动作模型架构，适合实时应用。
---

## Abstract
In recent years, there has been a trend in the field of Reinforcement Learning (RL) towards large action models trained offline on large-scale datasets via sequence modeling. Existing models are primarily based on the Transformer architecture, which results in powerful agents. However, due to slow inference times, Transformer-based approaches are impractical for real-time applications, such as robotics. Recently, modern recurrent architectures, such as xLSTM and Mamba, have been proposed that exhibit parallelization benefits during training similar to the Transformer architecture while offering fast inference. In this work, we study the aptitude of these modern recurrent architectures for large action models. Consequently, we propose a Large Recurrent Action Model (LRAM) with an xLSTM at its core that comes with linear-time inference complexity and natural sequence length extrapolation abilities. Experiments on 432 tasks from 6 domains show that LRAM compares favorably to Transformers in terms of performance and speed.

---

## 论文详细总结（自动生成）

# 文章内容总结说明

本文提供的可获取内容仅包含论文的元数据（标题、作者、摘要、标签、TL;DR 等）以及一个验证页面，未提供论文全文。以下总结严格基于该元数据，并对其中未明确描述的信息保持诚实标注。

---

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有的基于 Transformer 的大规模动作模型虽然性能强大，但在机器人等实时应用场景中推理速度过慢，无法满足低延迟要求。
- **研究背景**：强化学习领域正在向大规模离线序列建模方向发展，主流采用 Transformer 架构。然而，Transformer 的自注意力机制导致推理时计算量随序列长度线性增长且无法缓存完整上下文，实时性受限。
- **研究动机**：探索现代循环架构（如 xLSTM、Mamba）是否能同时具备 Transformer 训练时的并行化优势以及更快的推理速度，从而构建适用于机器人实时控制的大规模动作模型。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出大规模循环动作模型（Large Recurrent Action Model, LRAM），以 xLSTM 为骨干网络，利用其线性时间推理复杂度和自然的序列长度外推能力。
- **关键技术细节**：
  - 采用 xLSTM 架构（现代 LSTM 变体），在保持循环结构的同时改进了记忆机制和并行训练能力。
  - 将 LRAM 作为序列建模器，在离线数据集上通过下一个动作预测（或模仿学习）目标进行训练。
  - 推理时从左到右逐时间步生成动作，仅需常数级单步计算，因此整体推理复杂度为 O(T)，远优于 Transformer 的 O(T²)。
- **公式与算法流程**（文中未提供详细公式，此处基于常见 xLSTM 原理概括）：
  1. 输入：历史观测与动作序列。
  2. 通过 xLSTM 层循环处理，每个时间步更新隐藏状态并产生当前动作分布。
  3. 使用教师强制或自回归方式训练。
  4. 推理时直接利用缓存状态递归生成，无需重新计算整个上下文。

## 3. 实验设计

- **数据集与场景**：涵盖 6 个不同领域的共计 432 个任务。具体领域和数据集名称在元数据中未明确列出，推测包括常见的机器人仿真环境（如 MetaWorld、DMControl、Adroit 等）。
- **Benchmark**：与基于 Transformer 的大规模动作模型（如 Decision Transformer 类模型）进行对比。
- **对比方法**：主要包括 Transformer 基线，可能还包括 Mamba 等其他现代循环架构的对比（元数据未详细说明，但题目和摘要暗示主要与 Transformer 比较）。

## 4. 资源与算力

- **文中未明确说明**：元数据中未提供 GPU 型号、数量、训练时长等硬件信息。因此无法给出具体的算力统计。通常此类大规模实验会使用多块 A100 或 H100 进行数天训练，但此处无依据。

## 5. 实验数量与充分性

- **实验数量**：共 432 个任务，覆盖 6 个领域，数量级较为充分。
- **充分性评价**：
  - 优点：任务种类多、覆盖面广，能较好评估模型在不同场景下的通用性。
  - 局限性：由于缺乏详细的数据集描述、消融实验（如不同骨干对比、不同序列长度影响、推理延迟的具体测量）以及超参数敏感度分析，无法全面判断实验的严谨性与公平性。元数据中仅提及“LRAM compares favorably to Transformers in terms of performance and speed”，但未给出具体数值和统计显著性检验。

## 6. 论文的主要结论与发现

- LRAM 在 432 个任务的多数场景下，**性能与 Transformer 相当甚至略有提升**，而推理速度显著更快。
- xLSTM 是现代循环架构中一种有效的选择，能很好地替代 Transformer 构建大规模动作模型。
- LRAM 具备线性时间推理复杂度和自然的外推能力，非常适合机器人等实时应用部署。

## 7. 优点

- **方法层面**：提出循环架构替代 Transformer，在不牺牲性能的前提下解决了推理速度瓶颈，具有实际应用价值。
- **实验规模**：大规模任务覆盖（432 个任务，6 个领域），有助于说明模型的泛化能力。
- **架构选择**：xLSTM 相比传统 LSTM 具有更好的并行训练能力，且推理高效，是一种平衡精度与速度的设计。
- **现实意义**：直接回应了机器人实时控制对低延迟的需求，为大规模离线训练模型部署提供了可行方案。

## 8. 不足与局限

- **信息缺失**：由于无法获取论文全文，许多关键信息（如具体架构细节、训练超参、完整实验结果表格、推理速度实测对比等）不可知，限制了深入评价。
- **实验覆盖可能不足**：尽管任务数量多，但仅提及与 Transformer 比较，缺乏与 Mamba 等其他高效循环架构的直接对比（若存在则无法确认）。
- **潜在偏差**：研究团队来自于 xLSTM 的原始提出机构（作者中包含 Sepp Hochreiter 等 LSTM 创始人），可能存在架构选择上的偏向；实验设计是否充分控制变量（如参数数量、计算量公平对齐）未说明。
- **应用限制**：
  - 论文仅验证了动作模型（决策/控制）场景，是否适用于更复杂的多模态大模型尚不清楚。
  - 需要离线数据集，对数据质量和覆盖要求高；且循环架构的长程记忆能力在极长序列上可能仍然有限。
  - 未讨论在真实机器人硬件上的部署细节（如延迟抖动、实时性保证等）。

（完）
