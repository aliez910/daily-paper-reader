---
title: "Overcoming Knowledge Barriers: Online Imitation Learning from Visual Observation with Pretrained World Models"
title_zh: 克服知识屏障：基于预训练世界模型的在线视觉观察模仿学习
authors: "Xingyuan Zhang, Philip Becker-Ehmck, Patrick van der Smagt, Maximilian Karl"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=EbOhZyxIzQ"
tags: ["query:rob-il"]
score: 7.0
evidence: 基于预训练世界模型的在线视觉模仿学习
tldr: 本文研究基于预训练模型的模仿学习，观察到两个关键障碍：本体知识屏障与示范知识屏障。为此分别提出针对性解决方案，并将其集成到 AIME 框架中。实验表明，所提方法能够在未见本体与有限示范条件下实现更准确的视觉动作推断。该工作推动了基于视觉观察的模仿学习发展，对机器人任务具有直接应用价值。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 现有 ILfO 在预训练模型下面临本体知识与示范知识的双重障碍。
method: 分别针对两种屏障提出解法并集成进 AIME 框架，实现更准确的视觉动作推断。
result: 在多种本体与有限示范设置下显著提升了模仿学习的动作推断精度。
conclusion: 为基于视觉观察的在线模仿学习提供了可迁移至机器人任务的实用方案。
---

## Abstract
Pretraining and finetuning models has become increasingly popular in decision-making. But there are still serious impediments in Imitation Learning from Observation (ILfO) with pretrained models. This study identifies two primary obstacles: the Embodiment Knowledge Barrier (EKB) and the Demonstration Knowledge Barrier (DKB). The EKB emerges due to the pretrained models' limitations in handling novel observations, which leads to inaccurate action inference. Conversely, the DKB stems from the reliance on limited demonstration datasets, restricting the model's adaptability across diverse scenarios. 
We propose separate solutions to overcome each barrier and apply them to Action Inference by Maximising Evidence (AIME), a state-of-the-art algorithm.
This new algorithm, AIME-NoB, integrates online interactions and a data-driven regulariser to mitigate the EKB. Additionally, it uses a surrogate reward function to broaden the policy's supported states, addressing the DKB. Our experiments on vision-based control tasks from the DeepMind Control Suite and MetaWorld benchmarks show that AIME-NoB significantly improves sample efficiency and converged performance, presenting a robust framework for overcoming the challenges in ILfO with pretrained models.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of a paper based on provided metadata. The paper is about imitation learning from observation with pretrained world models, identifying two barriers (EKB and DKB) and proposing AIME-NoB as a solution. Let me organize this according to the 8 required points.

The paper PDF text couldn't be extracted (CAPTCHA), but I have rich metadata including title, abstract, motivation, method, results, conclusion, tags, etc. I'll use these to construct the summary, being careful to only state what's supported by the metadata and clearly note where information is unavailable.</think>

# 论文总结：克服知识屏障——基于预训练世界模型的在线视觉观察模仿学习

## 1. 核心问题与研究动机

- **核心问题**：在视觉观察模仿学习（Imitation Learning from Observation, ILfO）场景下，使用预训练世界模型面临两大知识屏障。
  - **本体知识屏障（Embodiment Knowledge Barrier, EKB）**：预训练模型在面对训练时未见过的观测（即新本体/新视角）时，无法准确推断动作。
  - **示范知识屏障（Demonstration Knowledge Barrier, DKB）**：依赖有限的专家示范数据，限制模型在不同场景下的泛化与适应能力。
- **整体含义**：随着"预训练 + 微调"在决策任务中的流行，如何借助已在大规模数据上训练好的世界模型完成视觉模仿学习，并突破上述双重屏障，是将 ILfO 推向真实机器人任务的关键问题。

## 2. 方法论

- **基线算法**：以现有最优算法 **AIME（Action Inference by Maximising Evidence）** 为基础，在其框架上扩展。
- **整体思想**：分别针对 EKB 和 DKB 提出独立解法，并集成得到新算法 **AIME-NoB**。
- **针对 EKB 的解决方案**：
  - 引入**在线交互（online interactions）**，让智能体主动与环境交互以补充视觉信息。
  - 使用**数据驱动的正则化项（data-driven regulariser）**，缓解预训练模型在新本体观测下的不准确性，从而改善动作推断。
- **针对 DKB 的解决方案**：
  - 设计**替代奖励函数（surrogate reward function）**，在不依赖更多专家示范的前提下，扩大策略所支持的状态空间分布，提升策略在不同场景中的适配性。
- **算法流程（AIME-NoB）概述**：
  1. 利用预训练世界模型对观测进行编码与未来预测。
  2. 在 AIME 的证据最大化框架下同时优化动作推断与正则化项。
  3. 通过在线交互采集到的轨迹驱动正则化学习，缓解 EKB。
  4. 通过替代奖励塑造策略的状态覆盖，缓解 DKB。
- 注：原文 PDF 因访问受限未能完整抓取，公式层面的细节（例如正则化项的具体形式、替代奖励的构造方式）以摘要与元数据为准，未做进一步臆测。

## 3. 实验设计

- **任务 / 数据集 / Benchmark**：
  - **DeepMind Control Suite**：基于视觉的控制任务。
  - **MetaWorld**：机器人操作类视觉控制任务。
- **对比方法**：
  - 以 AIME 作为主要基线（在原文元数据中明确为 state-of-the-art baseline）。
  - 由于原文 PDF 未能完整解析，其他具体对比基线（如 DDPG、BC、SQUIRL、OPEL 等常见 ILfO 方法）无法核实，故此处不罗列未确认项。
- **评估指标**：摘要中明确强调 **样本效率（sample efficiency）** 与 **最终收敛性能（converged performance）**。
- **关键实验设定**：覆盖"未见本体"与"有限示范"两种典型挑战场景，用于验证两种屏障的应对效果。

## 4. 资源与算力

- 原文 PDF 由于 OpenReview 反爬/CAPTCHA 限制未能获取，**未能从原文中确认具体的 GPU 型号、数量与训练时长**。
- 元数据中也未提供计算资源相关字段。
- 因此本节如实标注：算力信息缺失，无法评估训练成本与可复现性细节。

## 5. 实验数量与充分性

- **可确认的实验范围**：
  - 至少包含 **两个基准**（DM Control + MetaWorld）的视觉控制任务。
  - 实验设计明确区分"未见本体"与"有限示范"两个维度，与论文提出的两种屏障一一对应，具有较强的针对性。
- **充分性评估**：
  - **优点**：在样本效率与收敛性能两个指标上同时评估，兼顾训练过程与最终效果；任务横跨运动控制与操作两类，具一定多样性。
  - **局限（因信息缺失无法完全评估）**：是否包含消融实验（如分别去掉在线交互、正则化项、替代奖励以验证各模块贡献）、是否覆盖多种本体差异程度、是否做了随机种子统计显著性检验——这些在可获取的摘要与元数据中未明确说明，需结合正文进一步核实。

## 6. 主要结论与发现

- 提出的 **AIME-NoB** 在基于视觉的模仿学习任务上，**显著提升了样本效率与最终收敛性能**。
- 通过分别处理 EKB 与 DKB，**有效缓解了预训练世界模型在新本体和有限示范下的动作推断偏差**。
- 表明结合在线交互与替代奖励的方式，**能够弥补预训练模型在下游 ILfO 任务中的知识缺口**，为机器人视觉模仿学习提供更鲁棒的框架。

## 7. 优点与亮点

- **问题分解清晰**：将阻碍 ILfO 的因素拆解为 EKB 与 DKB 两个相互独立但可叠加的瓶颈，针对性强，便于诊断与扩展。
- **方法组合合理**：把 AIME 的证据最大化优势、在线交互的探索能力、数据驱动正则化与替代奖励巧妙结合，体现"模块化解决屏障"的设计思路。
- **任务适配性好**：同时覆盖 DeepMind Control Suite（连续控制）与 MetaWorld（机器人操作），对真实机器人迁移有直接意义。
- **实用价值高**：以预训练世界模型为基础降低对示范数据量的依赖，契合当前大规模预训练 + 下游微调的研究范式。

## 8. 不足与局限

- **信息获取受限**：本次分析仅依赖摘要与元数据，**完整方法细节、公式推导与完整实验设置未能从原文中核验**，结论的细节严谨性有待进一步比对正文。
- **算力与可复现性信息缺失**：未提供 GPU 配置、训练时长、超参搜索范围与随机种子统计，难以独立评估复现成本与结果的统计显著性。
- **对比基线完整性存疑**：摘要主要提及与 AIME 的对比，是否包含更广泛的 ILfO/RL baseline、是否做了跨算法公平调参，未在已有材料中得到确认。
- **应用风险**：
  - 在线交互引入额外环境探索成本，在真实机器人上可能带来安全与磨损问题；
  - 替代奖励的构造依赖特定任务设计，其泛化性尚需在更多样化的环境中验证；
  - 预训练世界模型本身的偏差会传导至下游策略，"知识屏障"的边界条件与失败模式仍值得进一步研究。
- **潜在偏差**：摘要未明确说明实验是否在多种随机种子下取平均，评价结论时需注意是否可能存在单次实验带来的过拟合风险。

（完）
