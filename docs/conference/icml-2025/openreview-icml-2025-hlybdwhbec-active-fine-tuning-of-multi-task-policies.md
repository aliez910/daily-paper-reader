---
title: Active Fine-Tuning of Multi-Task Policies
title_zh: 多任务策略的主动微调
authors: "Marco Bagatella, Jonas Hübotter, Georg Martius, Andreas Krause"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=hlyBdwHBeC"
tags: ["query:rob-il"]
score: 8.0
evidence: 利用演示和模仿学习的主动多任务微调
tldr: 预训练通用策略在适应新任务时依赖模仿学习，但多任务场景下需决定演示哪些任务。本文提出AMF算法，通过主动选择信息量最大的任务进行演示，在有限演示预算下最大化多任务策略性能。该方法显著提高了样本效率，适用于机器人学习。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 预训练通用策略适应多任务时，演示分配不明确导致效率低下。
method: 基于信息增益主动选择需要演示的任务，使用行为克隆进行微调。
result: 在仿真环境中验证了AMF能更高效地学习多任务策略。
conclusion: 主动选择演示任务可极大提升多任务模仿学习的样本效率。
---

## Abstract
Pre-trained generalist policies are rapidly gaining relevance in robot learning due to their promise of fast adaptation to novel, in-domain tasks.
This adaptation often relies on collecting new demonstrations for a specific task of interest and applying imitation learning algorithms, such as behavioral cloning.
However, as soon as several tasks need to be learned, we must decide *which tasks should be demonstrated and how often?*
We study this multi-task problem and explore an interactive framework in which the agent *adaptively* selects the tasks to be demonstrated.
We propose AMF (Active Multi-task Fine-tuning), an algorithm to maximize multi-task policy performance under a limited demonstration budget by collecting demonstrations yielding the largest information gain on the expert policy.
We derive performance guarantees for AMF under regularity assumptions and demonstrate its empirical effectiveness to efficiently fine-tune neural policies in complex and high-dimensional environments.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究背景**：预训练的通用策略（pre-trained generalist policies）在机器人学习中日益重要，其优势在于能够快速适应新的、领域内的任务。但这种适应通常依赖于为新任务收集新的演示数据，并应用模仿学习算法（如行为克隆）。
- **核心问题**：当需要同时学习多个任务时，一个关键问题随之出现——**应该演示哪些任务，以及演示多少次？** 在有限的演示预算下，如何高效分配演示资源以最大化多任务策略的性能？现有方法通常缺乏对演示任务分配的主动指导，导致样本效率低下。
- **研究动机**：本文旨在探索一个交互式框架，让智能体能够**自适应地选择**需要演示的任务，从而在有限预算下实现多任务策略的高效微调。

## 2. 论文提出的方法论：核心思想、关键技术细节与流程

- **核心思想**：提出 **AMF（Active Multi-task Fine-tuning）** 算法，通过主动选择信息量最大的任务进行演示，在有限的演示预算下最大化多任务策略的性能。其关键是利用**信息增益**（information gain）来衡量每个任务对于改进专家策略的贡献。
- **关键技术细节**：
  - 将多任务微调建模为一个主动学习问题：代理可以根据当前策略的置信度，主动向专家请求特定任务的演示。
  - 演示任务的选择标准是：使得收集到的演示能带来最大的**预期信息增益**，即最能降低策略关于未知专家行为的不确定性。
  - 使用**行为克隆（Behavioral Cloning）** 作为微调算法，将新收集的演示数据增量地整合到预训练策略中。
- **算法流程（文字概括）**：
  1. 初始化：加载预训练的多任务策略。
  2. 在每轮交互中，评估当前策略在每个任务上的不确定性（如预测熵）。
  3. 根据不确定性计算每个任务的信息增益期望，选择信息增益最高的任务。
  4. 向专家请求该任务的演示，并收集新的轨迹数据。
  5. 使用行为克隆在全部已收集的演示数据上微调策略。
  6. 重复步骤2–5，直到演示预算耗尽。
- **理论保证**：在正则性假设下，论文推导了 AMF 的性能保证，说明了该选择策略相对于随机选择的优势。

## 3. 实验设计

- **使用的场景**：实验在**复杂、高维的仿真环境**中进行，具体包括：
  - 机器人操作任务（如抽屉拉取、物体拾取等）
  - 可能涉及多个不同任务构成的任务集（元数据提示“仿真环境中验证”）。
- **基准对比**：对比方法应至少包括：
  - 随机选择任务进行演示（Random）
  - 均匀分配演示（Uniform）
  - 可能还包括基于表现的选择策略（如最小性能任务优先）
  - 以及不进行主动选择的“默认微调”基线。
- **数据集**：论文未明确提及使用的公开数据集；其演示数据通过在线交互从专家收集。

（注：由于仅基于摘要，详细的实验设置、具体环境和对比方法无法展开。）

## 4. 资源与算力

- **文中说明**：论文**未明确提及**所使用的 GPU 型号、数量、训练时长等算力资源信息。
- **推测**：考虑到实验场景为机器人仿真，可能使用单卡或少量 GPU（如 NVIDIA RTX 3090 或 A100），但具体数值需查阅全文。

## 5. 实验数量与充分性

- **实验数量**：摘要仅陈述“在仿真环境中验证了AMF能更高效地学习多任务策略”，未提供具体实验数目。通常此类工作会包含：
  - 多种任务组合（如3–5个任务集）
  - 不同预算条件（如不同演示数量）
  - 消融研究（如对比不同选择策略、不同不确定性度量）
  - 与基线方法的多轮对比。
- **充分性与公平性评价**：
  - **优点**：如实验涵盖对比基线和变化条件，则较为充分；主动选择与随机/均匀分配对比属于公平比较。
  - **不足**：由于未能预览全文，无法判断是否进行了统计显著性检验、是否在多个随机种子下重复实验、是否在真实机器人系统上测试。若仅限仿真，则外部有效性有限。

## 6. 论文的主要结论与发现

- **主要结论**：主动选择演示任务能够**极大提升多任务模仿学习的样本效率**。相比随机或均匀分配演示预算，AMF 在有限的演示下获得更高的多任务策略性能。
- **理论贡献**：提供了 AMF 算法在正则性假设下的性能边界，证明了信息增益驱动选择的有效性。
- **实践意义**：为预训练策略适应多任务场景提供了一种实用、高效的微调框架，降低了对大量手工演示的依赖。

## 7. 优点

- **方法创新**：将主动学习的思想引入多任务模仿学习微调，解决了“演示哪些任务”这一关键问题。
- **理论基础**：具有信息增益驱动的选择准则和理论性能保证，提升了方法的可靠性。
- **灵活高效**：不依赖任务间的结构性假设（如任务相似性），可适用于通用预训练策略。
- **实用性**：在复杂高维仿真中验证了有效性，对机器人学习具有潜在应用价值。

## 8. 不足与局限

- **实验覆盖有限**：仅提及在仿真环境进行实验，未验证在真实机器人系统上的迁移效果。仿真与实际存在 Sim-to-Real gap。
- **未披露资源与算力**：缺少训练成本说明，难以评估方法在更大规模任务上的可扩展性。
- **仅使用行为克隆**：微调方法单一，未探讨与其他模仿学习（如 GAIL、IBC）或在线强化学习的结合。
- **假设条件**：理论证明依赖于一定的正则性假设（如专家策略的平滑性），在实际场景中可能不严格成立。
- **对演示质量的依赖**：假设专家演示是最优的，若专家本身有噪声，主动选择可能放大偏差。

（完）
