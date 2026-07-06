---
title: "Compose Your Policies! Improving Diffusion-based or Flow-based Robot Policies via Test-time Distribution-level Composition"
title_zh: 组合你的策略：基于测试时分布级组合改进扩散/流式机器人策略
authors: "Jiahang Cao, Yize Huang, Hanzhong Guo, Qiang Zhang, Rui Zhang, Weijian Mai, Mu Nan, Jiaxu Wang, Hao Cheng, Jingkai SUN, Gang Han, Wen Zhao, Yijie Guo, Qihao Zheng, Xiao Li, Chunfeng Song, Ping Luo, Andrew Luo"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=TnLFRhLuZ6"
tags: ["query:rob-il"]
score: 8.0
evidence: 测试时组合VLA/VA扩散策略以提升机器人控制性能
tldr: 扩散与流匹配策略在机器人控制中表现强大，但进展受限于大规模交互数据的高昂成本。本文提出无需额外训练的测试时分布级策略组合方法，并从理论上证明多个扩散模型分布得分的凸组合可产生更优的单步目标函数。实验表明组合策略性能可超越任一父策略。该方法为VLA/VA操控策略的部署与性能增强提供了一条轻量化新路径。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 扩散与流式机器人策略受限于大规模交互数据成本高，进一步训练代价大。
method: 提出测试时分布级组合方法，从理论上证明分布得分凸组合可形成更优目标。
result: 实验显示组合后的VLA/VA策略可超越任一父策略，且无需额外训练。
conclusion: 该工作为机器人操控策略的性能增强提供了一种无需重训的轻量化组合范式。
---

## Abstract
Diffusion-based models for robotic control, including vision-language-action (VLA) and vision-action (VA) policies, have demonstrated significant capabilities. Yet their advancement is constrained by the high cost of acquiring large-scale interaction datasets. This work introduces an alternative paradigm for enhancing policy performance ***without additional model training***. Perhaps surprisingly, we demonstrate that the composed policies can exceed the performance of either parent policy. Our contribution is threefold. First, we establish a theoretical foundation showing that the convex composition of distributional scores from multiple diffusion models can yield a superior one-step functional objective compared to any individual score. A Grönwall-type bound is then used to show that this single-step improvement propagates through entire generation trajectories, leading to systemic performance gains. Second, motivated by these results, we propose General Policy Composition (GPC), a training-free method that enhances performance by combining the distributional scores of multiple pre-trained policies via a convex combination and test-time search. GPC is versatile, allowing for the plug-and-play composition of heterogeneous policies, including VA and VLA models, as well as those based on diffusion or flow-matching, irrespective of their input visual modalities. Third, we provide extensive empirical validation. Experiments on Robomimic, PushT, and RoboTwin benchmarks, alongside real-world robotic evaluations, confirm that GPC consistently improves performance and adaptability across a diverse set of tasks. Further analysis of alternative composition operators and weighting strategies offers insights into the mechanisms underlying the success of GPC. These results establish GPC as a simple yet effective method for improving control performance by leveraging existing policies.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Compose Your Policies! Improving Diffusion-based or Flow-based Robot Policies via Test-time Distribution-level Composition" based on the provided metadata and abstract. Let me organize the response according to the 8 requested points.
</think>
# 论文总结：Compose Your Policies!

## 1. 核心问题与研究动机

- **背景**：基于扩散模型（Diffusion-based）和流匹配（Flow-matching）的机器人控制策略，包括视觉-语言-动作（VLA）和视觉-动作（VA）策略，近年来表现出强大能力。
- **瓶颈**：此类策略的进一步发展受限于大规模交互数据集采集的高昂成本；继续训练代价大、扩展性差。
- **核心问题**：能否在 **不进行额外训练** 的前提下，仅利用已有的多个预训练策略，通过组合（composition）的方式获得性能更优的策略？
- **整体含义**：提出一种"测试时分布级组合"范式，绕开数据与训练成本问题，为机器人操控策略的部署与增强提供轻量化路径。

## 2. 方法论

### 核心思想
- 对多个预训练策略所对应的**分布分数（distributional score）**做**凸组合（convex combination）**，再通过测试时搜索（test-time search）调整权重，得到一个性能优于任一父策略的组合策略。
- 强调 **Training-free**（无需训练）、**Plug-and-play**（即插即用）、**异构兼容**（可组合不同类型策略）。

### 关键技术细节
- **理论基础**：
  - 证明对多个扩散模型分布分数的凸组合，可构造出比任一单模型更优的单步目标函数（one-step functional objective）。
  - 通过 **Grönwall 型不等式**（Gronwall-type bound）证明单步改进会在整个生成轨迹中传播，从而带来系统性性能提升。
- **算法名称**：General Policy Composition（**GPC**）。
- **算法流程**（文字描述）：
  1. 准备多个预训练策略（可为 VA/VLA、扩散/流匹配，输入视觉模态可不同）。
  2. 在测试时，对每个策略计算其分布分数。
  3. 通过凸组合公式融合多个分数，并结合测试时搜索寻找最优权重 λ。
  4. 使用组合分数进行去噪/生成，得到组合后的动作。
- **可组合对象**：异构策略（diffusion 与 flow-matching；VA 与 VLA），输入模态可不同，权重 α 通过搜索确定。

## 3. 实验设计

- **数据集/Benchmark**：
  - **仿真**：Robomimic、PushT、RoboTwin。
  - **真实世界**：真实机器人实验（real-world robotic evaluations）。
- **对比方法**：
  - 与各父策略（即参与组合的预训练策略）单独执行进行对比。
  - 还分析了 **替代的组合算子（alternative composition operators）** 与 **加权策略（weighting strategies）** 的消融。
- **评测维度**：任务成功率、跨任务适应性、不同异构策略组合的泛化表现。

## 4. 资源与算力

- 摘要与元数据 **未明确说明** 所使用的 GPU 型号、数量或训练时长。
- 由于方法本身是 **training-free**，主要计算开销来自 **测试时搜索权重 λ** 的过程，但具体算力规模未在可见文本中披露。
- 这一点是论文的一个**信息披露缺口**。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 3 个仿真 benchmark（Robomimic、PushT、RoboTwin）+ 真实世界实验。
  - 包含对组合算子与加权策略的消融分析。
  - 涉及异构策略（VA/VLA、diffusion/flow-matching）组合测试。
- **充分性评估**：
  - ✅ 跨仿真到真实的迁移验证，方法泛化性较强。
  - ✅ 包含消融实验，揭示了 GPC 成功背后的机制。
  - ⚠️ 由于具体实验配置（每数据集任务数、随机种子数、每组重复次数等）未在元数据中详尽列出，难以判断统计显著性是否充分。
  - ⚠️ 测试时搜索的权重空间大小、搜索开销与稳定性需在论文正文中进一步核实。

## 6. 主要结论与发现

- **理论层面**：分布分数的凸组合在单步目标上严格更优，且改进会通过 Grönwall 界传递到整条生成轨迹。
- **经验层面**：
  - GPC 组合策略在 Robomimic、PushT、RoboTwin 及真实机器人上**一致地提升**任务表现。
  - 组合后的策略可**超越任一父策略**。
  - 方法对**异构策略**（不同架构、模态、范式）具有兼容性与即插即用性。
- **方法论意义**：GPC 提供了一种**轻量化、零训练**的策略性能增强路径，避免了大规模数据与训练成本。

## 7. 优点

- **理论支撑扎实**：给出严格的单步目标改进证明与 Grönwall 型轨迹传播界，区别于纯经验性的模型融合方法。
- **实用性强**：
  - Training-free，部署成本低。
  - Plug-and-play，兼容 VA/VLA、diffusion/flow-matching。
  - 输入视觉模态不敏感。
- **验证维度多元**：仿真多 benchmark + 真实机器人 + 算子/加权消融。
- **范式创新**：将"测试时计算"思路从 LLM 领域延伸至机器人扩散/流匹配策略，开辟新研究方向。

## 8. 不足与局限

- **算力信息披露不全**：未提供测试时搜索的具体算力开销与可扩展性分析。
- **测试时搜索成本**：尽管无需训练，但权重搜索可能带来显著的推理时延迟，实际部署的实时性保障需进一步评估。
- **任务范围**：仿真 benchmark 数量有限（3 个），且在更复杂、长时间跨度、含接触丰富操作的任务上泛化性尚需验证。
- **统计显著性**：元数据中未提及多次随机种子下的均值/方差报告，结果稳定性需查正文。
- **理论假设的适用边界**：Grönwall 型证明依赖特定 ODE 动力学假设，跨任务、跨策略的实际满足程度未充分讨论。
- **真实世界实验规模**：真实机器人评估的规模（任务数、试验次数）未在元数据中披露，限制了对真实落地可靠性的判断。
- **潜在偏差风险**：父策略的选择空间、初始化分布可能影响组合上限，存在"选择偏倚"风险。

（完）
