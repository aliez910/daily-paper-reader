---
title: "Behavioral Exploration: Learning to Explore via In-Context Adaptation"
title_zh: 行为探索：通过上下文适应学习探索
authors: "Andrew Wagenmaker, Zhiyuan Zhou, Sergey Levine"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=tlLkY9E2bZ"
tags: ["query:rob-il"]
score: 6.0
evidence: 行为克隆用于机器人探索与适应
tldr: 当前机器人和强化学习中的探索依赖于随机采样和缓慢的梯度更新，无法像人类一样快速在线适应。本文提出行为探索（Behavioral Exploration），借鉴上下文学习和大规模行为克隆，训练代理在专家行为空间中内化探索和适应能力。实验表明该方法显著提升了代理在未知环境中的探索效率和适应性。该工作为构建快速适应的自主代理提供了新的范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有探索方法效率低，无法实现快速在线适应。
method: 利用上下文学习和行为克隆，训练代理内化探索和适应。
result: 在未知环境中探索效率和适应性显著提升。
conclusion: 为自主代理的快速适应提供新思路。
---

## Abstract
Developing autonomous agents that quickly explore an environment and adapt their behavior online is a canonical challenge in robotics and machine learning. While humans are able to achieve such fast online exploration and adaptation, often acquiring new information and skills in only a handful of interactions, existing algorithmic approaches tend to rely on random exploration and slow, gradient-based behavior updates. How can we endow autonomous agents with such capabilities on par with humans? Taking inspiration from recent progress on both in-context learning and large-scale behavioral cloning, in this work we propose behavioral exploration: training agents to internalize what it means to explore and adapt in-context over the space of ''expert'' behaviors. To achieve this, given access to a dataset of expert demonstrations, we train a long-context generative model to predict expert actions conditioned on a context of past observations and a measure of how ''exploratory'' the expert's behaviors are relative to this context. This enables the model to not only mimic the behavior of an expert, but also, by feeding its past history of interactions into its context, to select different expert behaviors than what have been previously selected, thereby allowing for fast online adaptation and targeted, ''expert-like'' exploration. We demonstrate the effectiveness of our method in both simulated locomotion and manipulation settings, as well as on real-world robotic manipulation tasks, illustrating its ability to learn adaptive, exploratory behavior.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：当前机器人和强化学习中的探索方法（如随机采样、缓慢的梯度更新）无法像人类那样在少量交互中快速在线适应新环境。
- **动机**：现有探索效率低，缺乏人类那样的快速在线探索和适应能力。
- **目标**：希望赋予自主代理快速、目标导向的探索与适应能力，构建全新的自主决策范式。
- **意义**：提出一种**行为探索**（Behavioral Exploration）方法，借鉴**上下文学习（in-context learning）** 与**大规模行为克隆**，使代理内化“如何探索和适应”的能力，从而在未知环境中显著提升效率和适应性。

> 来源：论文摘要、TLDR 与 motivation 字段。

## 2. 论文提出的方法论

- **核心思想**：通过大规模专家演示数据训练一个长上下文生成模型，使代理能够**在上下文中**（in-context）学会探索和适应，而非依赖随机扰动或梯度更新。
- **关键技术细节**：
  1. 利用一个**专家演示数据集**（expert demonstrations）作为训练来源。
  2. 训练一个**长上下文生成模型**，使其在给定**历史观察序列**和**“探索性”度量**（measure of how ‘exploratory’ the expert’s behaviors are relative to this context）的条件下，预测专家动作。
  3. 该模型不仅模仿专家行为，还能**利用自身过去的交互历史作为上下文**，主动选择与之前不同的专家行为，从而实现**快速在线适应**和**有目标的、类似专家的探索**。
- **算法流程**（文字描述）：
  1. 收集专家演示数据。
  2. 对每个时间步，构建上下文（历史观察 + 探索性度量）。
  3. 训练生成模型：上下文 → 预测专家动作。
  4. 在部署时，代理将自身实时交互历史馈入模型上下文，模型输出动作，实现自适应探索。
- **原理**：将探索与适应过程内化到一个生成模型中，消除了对显式随机探索或梯度更新的需求。

> 来源：论文摘要、method 字段。

## 3. 实验设计

- **使用场景**：
  - **模拟环境**：运动控制（locomotion）和操作任务（manipulation）。
  - **真实世界**：机器人操作任务（real-world robotic manipulation tasks）。
- **基准与对比方法**：摘要中**未明确列出**具体的对比算法或基准，但指出与“现有依赖随机探索和缓慢梯度更新的算法”进行比较，并声称显著提升。
- **数据集**：专家演示数据集（expert demonstrations），未说明规模或来源。
- **评估指标**：探索效率和适应性（在未知环境中的表现）。

> 来源：论文摘要、result 字段。

## 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。
- 仅可知是在模拟和真实机器人上实验，但具体计算资源未提及。

> 提示：若需补全，需查阅全文。

## 5. 实验数量与充分性

- **实验组数**：摘要仅概括性地提到在**模拟运动控制、模拟操作、真实机器人操作**三类任务上测试，未给出具体子实验数量或消融实验。
- **充分性评估**：
  - ✅ 涵盖模拟和真实场景，具有一定代表性。
  - ❌ 缺乏与主流基线（如随机探索、强化学习中的经典探索方法）的定量比较细节。
  - ❌ 未报告消融实验、超参数敏感性分析或统计显著性检验。
  - 总体而言，摘要层面的信息不足以判断实验的充分性和公平性；需要阅读全文确认。

> 来源：摘要与元数据中未提供详细实验设计，此处基于已有信息给出保守评价。

## 6. 论文的主要结论与发现

- **核心结论**：行为探索方法能**显著提升代理在未知环境中的探索效率和适应性**，实现了类似人类的快速在线适应。
- **发现**：
  - 通过上下文内化探索和适应是可行的，且不依赖传统随机探索或梯度更新。
  - 该方法在多种环境（模拟/真实）中均有效，为构建快速适应的自主代理提供了**新范式**。
  - 可以视为将**行为克隆**扩展为一种**上下文适应性探索策略**的成功实践。

> 来源：摘要、TLDR、conclusion 字段。

## 7. 优点

- **方法创新性**：融合**上下文学习**与**大规模行为克隆**，提出全新的探索范式，解决了传统探索方法适应性慢的问题。
- **实用性**：不仅局限于模拟，还在**真实机器人**上验证，具有实际应用价值。
- **理念简洁**：将探索能力内化为生成模型的上下文预测，避免了复杂的探索奖励设计或策略梯度计算。
- **效率提升**：声称在未知环境中显著优于现有方法，且能实现快速在线适应。

## 8. 不足与局限

- **依赖专家演示**：需要高质量、覆盖性强的专家数据集，数据获取成本可能较高。
- **上下文长度限制**：长上下文生成模型可能面临注意力窗口或计算开销问题，影响长时间任务。
- **基线对比不透明**：摘要中未给出与 SOTA 方法的定量比较，优势程度和通用性尚存疑问。
- **实验细节缺失**：未报告实验数量、消融、超参数等，难以判断结果的稳定性和可复现性。
- **应用范围限制**：是否适用于高维连续控制、多任务泛化、稀疏奖励等情况未提及。
- **理论保障不足**：未给出探索最优性或收敛性分析，偏向工程实证。

> 注意：部分局限是基于常识推断的，原文摘要与元数据中未直接言明。

（完）
