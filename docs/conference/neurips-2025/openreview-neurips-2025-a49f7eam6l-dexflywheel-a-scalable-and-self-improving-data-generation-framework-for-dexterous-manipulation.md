---
title: "DexFlyWheel: A Scalable and Self-improving Data Generation Framework for Dexterous Manipulation"
title_zh: DexFlyWheel：面向灵巧操作的可扩展自改进数据生成框架
authors: "Kefei Zhu, Fengshuo Bai, YuanHao Xiang, Yishuai Cai, Xinglin Chen, Ruochong Li, Xingtao Wang, Hao Dong, Yaodong Yang, Xiaopeng Fan, Yuanpei Chen"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=a49F7EAm6l"
tags: ["query:rob-il"]
score: 7.0
evidence: 灵巧操作中模仿学习驱动的闭环数据生成
tldr: 针对灵巧操作中高质量多样化数据集稀缺的问题，本文提出DexFlyWheel可扩展自改进数据生成框架。该框架以少量种子演示为起点，将模仿学习与残差强化学习集成于闭环流水线中，通过迭代循环不断丰富数据多样性，为灵巧操作策略训练提供了可持续扩展的数据基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 灵巧操作缺乏多样化与高质量的数据集，限制了策略的可扩展性与泛化能力。
method: 提出DexFlyWheel自改进数据生成框架，将模仿学习与残差强化学习集成于闭环流水线。
result: 通过迭代循环持续丰富数据多样性，提升了灵巧操作策略的可扩展性。
conclusion: 为灵巧操作的大规模数据生成与策略学习提供了一种闭环自改进新机制。
---

## Abstract
Dexterous manipulation is critical for advancing robot capabilities in real-world applications, yet diverse and high-quality datasets remain scarce. Existing data collection methods either rely on human teleoperation or require significant human engineering, or generate data with limited diversity, which restricts their scalability and generalization. In this paper, we introduce DexFlyWheel, a scalable data generation framework that employs a self-improving cycle to continuously enrich data diversity. Starting from efficient seed demonstrations warmup, DexFlyWheel expands the dataset through iterative cycles. Each cycle follows a closed-loop pipeline that integrates Imitation Learning (IL), residual Reinforcement Learning (RL), rollout trajectory collection, and data augmentation. Specifically, IL extracts human-like behaviors from demonstrations, and residual RL enhances policy generalization. The learned policy is then used to generate trajectories in simulation, which are further augmented across diverse environments and spatial configurations before being fed back into the next cycle. Over successive iterations, a self-improving data flywheel effect emerges, producing datasets that cover diverse scenarios and thereby scaling policy performance. Experimental results demonstrate that DexFlyWheel generates over 2,000 diverse demonstrations across four challenging tasks. Policies trained on our dataset achieve an average success rate of 81.9\% on the challenge test sets and successfully transfer to the real world through digital twin, achieving a 78.3\% success rate on dual-arm lift tasks.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "DexFlyWheel: A Scalable and Self-improving Data Generation Framework for Dexterous Manipulation" based on the provided abstract and metadata. I need to organize the summary according to the 8 specified points, using Markdown formatting with hierarchical headers and bullet points. The language should be concise but information-complete, ending with "（完）".

Let me carefully analyze the content:

1. Core problem: Dexterous manipulation lacks diverse and high-quality datasets. Existing methods rely on human teleoperation or significant human engineering, or produce data with limited diversity.

2. Methodology: DexFlyWheel framework with self-improving cycle. Closed-loop pipeline integrating:
   - Imitation Learning (IL) - extracts human-like behaviors
   - Residual Reinforcement Learning (RL) - enhances policy generalization
   - Rollout trajectory collection
   - Data augmentation across diverse environments and spatial configurations
   Starting from seed demonstrations warmup, then iterative cycles.

3. Experiments: Four challenging tasks, generating over 2,000 diverse demonstrations. 81.9% average success rate on challenge test sets. 78.3% success rate on real-world dual-arm lift via digital twin.

4. Resources: The abstract doesn't mention specific GPU models, training time, etc. I should note this.

5. Experimental quantity: The abstract mentions 4 tasks, 2000+ demonstrations, real-world transfer. But specific ablation details aren't in the abstract.

6. Main conclusions: Self-improving data flywheel effect, scalable, transferable to real world.

7. Strengths: Self-improving loop, IL+residual RL combination, data augmentation diversity, real-world transfer.

8. Limitations: Not mentioned in abstract, but I can infer some from context.

Let me write a comprehensive summary based on the available information. I should be careful to note when information is not provided in the abstract.
</think>
# DexFlyWheel 论文总结

## 1. 核心问题与研究动机

- **关键瓶颈**：灵巧操作（dexterous manipulation）是机器人迈向真实应用的关键能力，但**多样化、高质量的数据集严重匮乏**，制约了策略的规模化训练与泛化能力。
- **现有方法的不足**：
  - 人类遥操（teleoperation）成本高昂、可扩展性差；
  - 人工工程（hand-engineering）投入大；
  - 现有自动数据生成方法产出数据的多样性有限。
- **研究目标**：构建一个**可持续扩展、闭环自改进**的数据生成框架，以最少的人工投入获得越来越丰富的数据。

## 2. 方法论

- **核心思想**：提出 **DexFlyWheel**——一个"数据飞轮"式自改进数据生成框架，通过**迭代闭环**不断丰富数据多样性。
- **整体流程（按周期循环）**：
  1. **种子演示热启动（Seed Demonstrations Warmup）**：从少量高效的种子演示出发，提供初始行为先验。
  2. **模仿学习（IL）**：从演示中提取类人行为模式。
  3. **残差强化学习（Residual RL）**：在 IL 策略基础上进行 RL 训练，**增强策略的泛化能力**（残差形式便于在保持类人动作的同时进行探索）。
  4. **Rollout 轨迹收集**：用学到的策略在仿真中自动 rollout，批量生成新轨迹。
  5. **数据增强（Data Augmentation）**：在不同环境、不同空间配置下对轨迹做增强，进一步扩展多样性。
  6. **回到下一轮循环**，形成**自改进飞轮（self-improving flywheel）**。
- **关键设计点**：
  - **IL + 残差 RL 的组合**：既保留人类行为先验，又允许策略超越演示进行探索；
  - **闭环迭代**：每一轮的新数据反哺下一轮训练，实现"数据-策略"协同进化；
  - **数据增强在仿真层面**进行而非简单的图像增强，覆盖场景与空间构型变化。

## 3. 实验设计

- **任务规模**：在 **4 个具有挑战性的灵巧操作任务**上验证。
- **数据规模**：生成超过 **2,000 条多样化演示**。
- **Benchmark 表现**：
  - 挑战测试集上平均成功率 **81.9%**；
  - 通过 **数字孪生（digital twin）**迁移到真实世界，在双臂提升（dual-arm lift）任务上取得 **78.3%** 成功率。
- **对比方法**：摘要未明确列出对比基线的名称与数量，需结合正文查看（仅有上述总体结果）。
- **真实世界验证**：通过数字孪生进行 sim-to-real 迁移，验证策略在真实环境中的可部署性。

## 4. 资源与算力

- 摘要与元数据中**未明确披露**所用 GPU 型号、数量、训练时长或计算开销等细节。
- 建议进一步阅读正文"Experimental Setup"或"Implementation Details"章节以获取完整算力信息。

## 5. 实验数量与充分性

- **任务维度**：覆盖 4 个不同灵巧操作任务，具备一定的任务多样性。
- **数据维度**：2,000+ 条轨迹且强调"多样化"，说明在数据规模上较为可观。
- **迁移验证**：包含从仿真到真实世界的迁移实验，是灵巧操作研究的重要检验环节。
- **局限性（基于现有信息）**：
  - 摘要中**未提供消融实验**的描述（如去掉残差 RL、去掉数据增强等的影响），充分性需结合正文判断；
  - **未列出基线对比**的具体对象与对比维度，难以判断公平性与客观性；
  - 仅以**双臂提升**作为真实世界任务，真实场景覆盖较为有限。

## 6. 主要结论与发现

- DexFlyWheel 通过闭环自改进机制，能够**持续扩大数据多样性与规模**，形成"数据飞轮"效应。
- 组合使用 IL 与残差 RL，可在保留人类行为先验的同时获得**更强的泛化策略**。
- 仿真训练的策略能够通过数字孪生**有效迁移到真实世界**（78.3% 成功率）。
- 提供了**超过 2,000 条多样化演示**的灵巧操作数据集，为下游研究提供数据基础。

## 7. 优点与亮点

- **自改进飞轮机制**：数据-策略协同进化的设计思路新颖，符合规模化数据生成的发展方向。
- **IL + 残差 RL 的协同**：兼顾"类人"先验与"超演示"探索，缓解了纯 IL 泛化差与纯 RL 探索难的双重问题。
- **闭环流程整合度强**：将 IL、RL、rollout、增广统一在一个流水线中，工程化程度高。
- **覆盖仿真到真实**：通过数字孪生完成 sim-to-real 验证，落地性强。
- **任务具挑战性**：所选任务对灵巧操作能力要求较高，结果具有说服力（81.9% / 78.3%）。

## 8. 不足与局限

- **算力与训练细节不透明**：摘要中未给出硬件、训练时长、超参数等信息，复现难度较高。
- **对比基线信息不足**：未在摘要中明确对比方法，难以判断相对于 SOTA 的实际优势。
- **消融实验信息缺失**：IL、残差 RL、数据增强各组件的独立贡献未在摘要中体现。
- **真实世界验证范围有限**：仅在"双臂提升"一个任务上做了真实世界测试，sim-to-real 的鲁棒性结论尚需更多场景支撑。
- **数据多样性度量不明确**："多样化"的具体定义、评估指标（如任务构型、物体类别、初始位姿等）未在摘要中说明。
- **种子演示依赖**：框架仍需少量"高效种子演示"作为起点，**并非完全无人工干预**，存在种子质量对最终性能的影响风险。
- **应用边界**：聚焦于 4 个特定任务，对更广泛灵巧操作任务（如双手精细装配、工具使用、柔性物体操作等）的可扩展性尚待验证。

（完）
