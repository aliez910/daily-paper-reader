---
title: Behavior Cloning from Suboptimal Demonstrations with Robust World Models
title_zh: 基于鲁棒世界模型的次优演示行为克隆
authors: "Krishnan Srinivasan, Bhavna Sud, Animesh Garg, Jeannette Bohg"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=PZwpFrNNYn"
tags: ["query:rob-il"]
score: 7.0
evidence: 通过世界模型正则化实现次优演示下的机器人操纵行为克隆
tldr: 行为克隆在演示数据质量不高时性能受限，现有方法往往需要对失败或噪声样本进行过滤或重加权。本文提出RIC（基于评论家的鲁棒模仿）离线强化学习框架，利用隐式世界模型对未来回报进行预测，并据此对行为克隆策略进行正则化。该方法无需显式过滤次优数据即可获得鲁棒的策略，为复杂机器人操纵中数据质量参差不齐的实际场景提供了实用的模仿学习解决方案。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 行为克隆在演示数据质量较低时性能受限，现有方法需显式过滤或重加权。
method: 提出RIC框架，用隐式世界模型预测未来回报并正则化行为克隆策略。
result: 方法可在不显式过滤次优数据的情况下学习到鲁棒操纵策略。
conclusion: 世界模型正则化为次优数据下的行为克隆提供了新路径。
---

## Abstract
Recent advances in behavior cloning and generative modeling of manipulation behaviors have shown promising results in learning complex multi-modal behavior distributions. However, a common limitation for all behavior cloning methods has been the challenge of acquiring high-quality training data. Existing state-of-the-art methods for policy learning face significant limitations when expert demonstrations are low quality, and often require the filtering or reweighting of failed or noisy demonstrations. To address this challenge, we propose an efficient offline reinforcement learning framework which utilizes an implicit world model to regularize a behavior cloning policy via predicted future returns. Our approach, Robust Imitation with a Critic (RIC), utilizes a critic-regularized imitation learning objective to incorporate both successful and failed demonstrations, steering imitation learning towards better trajectories via a conservative critic. Our method improves on prior works by accelerating the quality of learned policies by as much as 20% in the presence of suboptimal expert training data. Our simulated experiments consider different types of data suboptimality, including rollouts from a poor demonstrator policy and biased action perturbations from controller error.  We empirically evaluate different algorithmic choices for RIC, including comparisons of (1) offline reinforcement learning and behavior cloning, (2) critic guidance via an implicit world-model and a conservative critic estimate, and (3) different behavior cloning methods, including token and diffusion-based architectures.

---

## 论文详细总结（自动生成）

<think>
The user wants a structured, detailed Chinese summary of the paper based on the provided abstract and metadata. Let me analyze the content carefully and organize it according to the 8 required points.

Key information from the metadata and abstract:
- Title: Behavior Cloning from Suboptimal Demonstrations with Robust World Models
- Authors: Krishnan Srinivasan, Bhavna Sud, Animesh Garg, Jeannette Bohg
- Date: 2025-09-20
- Conference: ICLR-2026-Public
- Method: RIC (Robust Imitation with a Critic) - offline RL framework using implicit world model
- Key claim: 20% improvement in policy quality with suboptimal data
- Tests different suboptimality types: poor demonstrator rollouts, biased action perturbations
- Compares: offline RL vs behavior cloning, implicit world-model vs conservative critic, token/diffusion-based BC architectures

Let me structure the summary properly.
</think>
# 论文总结：基于鲁棒世界模型的次优演示行为克隆

## 1. 核心问题与研究动机

- **核心问题**：行为克隆（Behavior Cloning, BC）方法的性能高度依赖训练数据质量。当专家演示数据质量较差（存在失败样本或噪声扰动）时，现有方法性能受限。
- **现有方法的局限**：当前主流策略学习方法在面对低质量专家演示时表现不佳，往往需要**显式过滤**或**重加权**失败/噪声样本，过程繁琐且依赖人工经验。
- **研究目标**：在不需要显式过滤次优数据的前提下，让模仿学习算法能够直接从包含成功与失败样本的混合演示数据中学习到鲁棒的策略。

## 2. 方法论

- **核心思想**：提出 **RIC（Robust Imitation with a Critic）** 框架——一种高效的离线强化学习框架，利用**隐式世界模型（implicit world model）**对未来回报进行预测，并据此对行为克隆策略进行正则化。
- **关键组件**：
  - **隐式世界模型**：用于预测未来回报（future returns），为策略学习提供奖励信号或正则化依据。
  - **保守评论家（conservative critic）**：引导模仿学习偏向更优的轨迹，避免被次优数据误导。
  - **评论家正则化的模仿学习目标（critic-regularized imitation learning objective）**：同时利用成功与失败的演示数据，将评论家的价值估计融入到行为克隆损失中。
- **算法流程概述**：
  1. 收集包含成功与失败的次优演示数据；
  2. 训练一个隐式世界模型，预测未来回报；
  3. 基于该回报预测训练一个保守评论家；
  4. 用评论家对行为克隆策略进行正则化，使得策略倾向于产生高回报轨迹；
  5. 最终输出在次优数据上训练得到的鲁棒策略。

## 3. 实验设计

- **任务场景**：机器人操纵（robotic manipulation）任务，具体场景未在摘要中完全展开。
- **次优数据类型**（模拟不同次优性来源）：
  - 较差演示策略产生的 rollout 数据；
  - 控制器误差引入的偏置动作扰动（biased action perturbations）。
- **Benchmark 与对比方法**：
  - 对比 **离线强化学习** vs **行为克隆** 两种范式；
  - 对比 **隐式世界模型引导** vs **保守评论家估计引导** 两种评论家信号来源；
  - 对比 **基于 Token 的行为克隆架构** vs **基于扩散模型（diffusion-based）的行为克隆架构**。
- **评测指标**：隐含为策略质量提升幅度，论文称在次优数据下策略质量提升达 **20%**。

## 4. 资源与算力

- **论文摘要中未明确提及**所使用的 GPU 型号、数量或训练时长等算力信息。
- 这一点在所提供的文本中无法确认，需要查阅正文补充材料才能获知。

## 5. 实验数量与充分性

- **消融实验维度**：摘要中明确提到了三组对比维度（离线 RL vs BC、世界模型 vs 保守评论家、Token-based vs Diffusion-based BC），说明进行了较为系统的消融。
- **次优性覆盖**：考虑了两种典型次优来源（差策略 rollout 和控制器偏置扰动），覆盖了数据次优性的常见情形。
- **充分性评估**：
  - **优点**：从三个不同维度对比，覆盖了算法选择、评论家信号类型和基础 BC 架构，实验设计较为全面。
  - **局限**：摘要未说明在多少个具体任务/环境上进行了测试，benchmark 的多样性和统计显著性无法从摘要中判断；是否在真实机器人上验证也不明确。

## 6. 主要结论与发现

- **主要结论**：提出的 RIC 框架能够在**不显式过滤次优数据**的情况下，从混合质量的演示中学习到鲁棒的操作策略。
- **量化结果**：在存在次优专家训练数据时，所学策略的质量比已有方法**提升约 20%**。
- **核心洞见**：通过隐式世界模型对未来回报的预测来正则化行为克隆，可以有效解决次优演示下的模仿学习问题，为世界模型正则化提供了一条新路径。

## 7. 优点

- **方法新颖性**：将隐式世界模型与保守评论家结合，为行为克隆提供正则化信号，避免了显式数据过滤/重加权的复杂流程。
- **实用性强**：直接处理包含成功与失败样本的混合数据，更贴近真实机器人学习场景中数据质量参差不齐的实际情况。
- **加速效果显著**：在次优数据下可加速策略质量提升达 20%，训练效率较高。
- **模块化对比充分**：同时从 RL 范式、评论家信号源、BC 架构三个维度进行了算法选择对比，验证了各模块的有效性。
- **次优性建模全面**：覆盖了策略次优和控制器偏置两种次优来源。

## 8. 不足与局限

- **实验环境信息有限**：摘要未明确具体任务名称（如 Meta-World、Robomimic 等）和任务数量，难以判断泛化性。
- **真实世界验证缺失**：从摘要看实验主要在仿真中进行，未提及真实机器人部署，实用性仍需进一步验证。
- **算力信息缺失**：训练成本和计算资源未在摘要中披露，方法的可复现性和经济性难以评估。
- **20% 提升的统计显著性未说明**：摘要中给出的提升幅度缺乏置信区间或多次实验取平均的说明。
- **依赖次优数据中的成功样本比例**：方法效果可能受成功/失败样本比例影响，但摘要中未对这一敏感性进行分析。
- **理论分析薄弱**：未提供关于保守评论家偏差、隐式世界模型误差对策略影响的理论分析。

（完）
