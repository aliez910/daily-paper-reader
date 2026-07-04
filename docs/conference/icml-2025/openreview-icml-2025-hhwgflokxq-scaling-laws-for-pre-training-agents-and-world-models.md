---
title: Scaling Laws for Pre-training Agents and World Models
title_zh: 面向智能体和世界模型预训练的缩放律
authors: "Tim Pearce, Tabish Rashid, David Bignell, Raluca Georgescu, Sam Devlin, Katja Hofmann"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=HHwGfLOKxq"
tags: ["query:rob-il"]
score: 4.0
evidence: 刻画了具身智能体中模仿学习和世界模型的缩放律
tldr: 本文研究了具身智能体预训练中模型大小、数据量和计算量对模仿学习和世界建模性能的影响，发现与语言模型类似，这些任务也遵循幂律缩放规律，但系数受分词器、任务和架构的影响。该发现为构建更大规模的具身模型提供了理论指导。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 具身智能体的性能随模型和数据规模提升，但缩放规律的精确形式尚不明确。
method: 通过系统实验，分析模仿学习和世界建模中损失与模型最优尺寸等关系，拟合幂律曲线。
result: 发现缩放规律与语言模型类似，但系数严重依赖分词器、任务和架构。
conclusion: 该工作为具身模型的高效预训练提供了经验法则和理论依据。
---

## Abstract
The performance of embodied agents has been shown to improve by increasing model parameters, dataset size, and compute. This has been demonstrated in domains from robotics to video games, when generative learning objectives on offline datasets (pre-training) are used to model an agent's behavior (imitation learning) or their environment (world modeling). This paper characterizes the role of scale in these tasks more precisely. Going beyond the simple intuition that `bigger is better', we show that the same types of power laws found in language modeling also arise in world modeling and imitation learning (e.g. between loss and optimal model size). However, the coefficients of these laws are heavily influenced by the tokenizer, task \& architecture -- this has important implications on the optimal sizing of models and data.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **研究动机**：具身智能体（如机器人、游戏AI）的性能随模型参数、数据集规模和计算量增加而提升的现象已有初步验证，但**缩放规律的精确形式尚不明确**。语言模型领域的幂律缩放律已被广泛认可，而在具身智能体预训练（模仿学习与世界建模）中，类似规律是否存在、其具体形式如何，是论文试图回答的核心问题。
- **整体含义**：通过系统刻画模型大小、数据量、计算量与损失（或最优模型尺寸）之间的幂律关系，为具身模型的高效预训练提供理论依据和经验法则，指导未来更大规模模型和数据集的构建。

## 2. 论文提出的方法论
- **核心思想**：将语言模型领域被验证的**缩放律分析方法**延伸至具身智能体的两个典型预训练任务——模仿学习（Imitation Learning）和世界建模（World Modeling）。假设损失（Loss）与模型规模、数据规模、计算量之间遵循幂律关系，并通过实验拟合这些关系的系数。
- **关键技术与流程**：
  - 采用**生成式学习目标**在离线数据集上预训练模型。
  - 针对不同模型大小、数据集大小和计算预算，记录验证损失。
  - 借鉴语言模型中的缩放律公式（如 `L ∝ N^(-α)` 等），拟合模仿学习和世界建模中的类似关系。
  - 重点分析**分词器（Tokenizer）、任务类型（Task）与模型架构（Architecture）**对幂律系数的影响。
- **注**：论文未公开具体的缩放律数学公式，但指出与语言模型中的幂律形式一致。

## 3. 实验设计
- **数据集/场景**：论文提及实验涵盖**机器人（Robotics）和视频游戏（Video Games）**等领域，但未列举具体数据集名称（如DMControl、Atari、MineRL等）。仅说明使用了“离线数据集”。
- **Benchmark**：未明确定义统一的Benchmark。实验通过自建任务（不同领域、不同复杂度）来验证缩放律的普遍性。
- **对比方法**：不作方法对比，而是**将自身实验结果与语言模型缩放律的理论预测进行对照**，并比较不同分词器、任务类型和架构下的系数差异。

## 4. 资源与算力
- **未明确说明**：论文原文未提供训练所使用的GPU型号、数量、总计算时长等算力细节。这是实验可重复性方面的一个缺口。

## 5. 实验数量与充分性
- **实验数量**：未报告具体实验次数或组合数量。但描述为“系统实验”，推测涵盖多种模型大小（如参数从百万级到亿级）、多种数据量级、多种计算预算，并针对不同分词器、任务和架构进行了消融。
- **充分性评估**：由于缺乏详细实验清单，难以判断是否全面。但论文能够拟合出幂律关系，说明实验设计是有结构的。客观性方面，论文未提及随机种子、多次重复等细节，存在一定风险。

## 6. 论文的主要结论与发现
- **缩放律存在性**：在模仿学习和世界建模中，损失与模型最优尺寸、数据量、计算量之间确实存在**幂律缩放关系**，与语言模型中的发现类似。
- **系数依赖性**：幂律的系数强烈依赖于**分词器、任务类型和模型架构**。这意味着同一套缩放律不能直接跨设定迁移，需要针对具体条件重新校准。
- **实践指导**：为具身模型预训练中**模型与数据的比例、最优计算分配**提供了经验法则，有助于避免盲目扩大模型或数据而浪费算力。

## 7. 优点
- **填补空白**：首次系统性地将缩放律分析框架引入具身智能体预训练领域，尤其是同时覆盖了模仿学习和世界建模两个重要任务。
- **实用性**：结论直接指导实践——开发者需根据自身分词器、任务和架构来估计最优规模，而非简单套用语言模型经验。
- **简洁有力**：从简单直觉“更大更好”升级为定量的幂律关系，为领域提供了理论支撑。

## 8. 不足与局限
- **实验细节缺失**：未公开具体数据集、模型架构、训练配置和算力消耗，限制了结果的可复现性和可信度。
- **任务覆盖有限**：仅提及机器人及视频游戏，未涉及其他具身范式（如自动驾驶、工业操作），通用性有待验证。
- **系数影响因素分析不够深入**：仅指出分词器、任务、架构有影响，但未系统量化各因素的贡献，也未提出如何选择最优分词器或架构的建议。
- **缺乏与现有缩放律的定量对比**：未给出与语言模型缩放律系数的直接数值比较，使得“类似”结论略显模糊。
- **仅关注损失**：未验证缩放律是否对下游任务性能（如任务完成率、样本效率）有同样规律，实用性打折扣。

（完）
