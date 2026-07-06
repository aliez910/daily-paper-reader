---
title: "SpoilDICE: Safe and Performant Offline Imitation Learning from Dual Demonstrations"
title_zh: SpoilDICE：基于双演示的安全高性能离线模仿学习
authors: "Seokin Seo, Jongmin Lee, Sung Kuk Shyn, Hongseok Yang, Kee-Eung Kim"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=WksEmokwkb"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向安全-性能双演示的离线模仿学习
tldr: 本文针对模仿学习中难以同时保证高回报与严格安全约束的挑战展开研究。现有方法依赖人工设计的奖励/成本函数，难以刻画复杂安全约束。作者提出从安全-性能双演示进行模仿学习的问题设定，其中训练数据自然分为安全（次优）与高性能（可能违反安全）两类，并提出基于平稳分布修正估计的离线方法SpoilDICE。该框架虽具通用性，但为机器人操控策略的安全模仿学习提供了可迁移的方法基础，支持在复杂操控任务中兼顾性能与安全。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 模仿学习中难以同时保证高回报与严格安全约束，且人工设计奖励/成本函数困难。
method: 提出SpoilDICE离线方法，基于平稳分布修正估计从安全-性能双演示中学习策略。
result: 在离线设定下统一处理安全与性能权衡，为安全模仿学习提供了可迁移方法。
conclusion: 基于双演示的离线模仿学习为复杂安全约束下的策略学习提供了通用解决方案。
---

## Abstract
Ensuring both high returns and strict safety guarantees remains a fundamental challenge in imitation learning (IL). Existing approaches often rely on manually specified reward or cost functions, which are difficult to design and rarely capture complex safety constraints in real-world settings. We tackle this issue by introducing the problem of imitation learning from safety–performance dual demonstrations, where training data naturally divides into (i) safe demonstrations that respect safety requirements but may be suboptimal, and (ii) performant demonstrations that achieve high returns but may violate safety. To address the problem in the offline setting, we propose SpoilDICE (Safe–Performant Offline Imitation Learning via stationary DIstribution Correction Estimation). SpoilDICE integrates DICE-based distribution matching with support constraints derived from safe demonstrations, enabling agents to exploit high-return behaviors while remaining within safety-compliant regions of the state–action space. We validate our approach in both tabular gridworld and continuous safety-critical domains from the DSRL dataset and Safety Gymnasium benchmark. Empirical results demonstrate that SpoilDICE consistently produces policies that achieve strong performance without sacrificing safety, substantially outperforming prior offline IL baselines.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper based on the provided metadata and abstract. Let me analyze the content carefully.

The paper is "SpoilDICE: Safe and Performant Offline Imitation Learning from Dual Demonstrations" - it's about offline imitation learning with both safety and performance considerations.

Let me structure the summary according to the 8 points requested:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Computational resources
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Note that the PDF content was not actually accessible (CAPTCHA blocked it), so I only have the metadata and abstract. I should be honest about what information I have and don't have.
</think>
# SpoilDICE 论文总结

## 1. 核心问题与整体含义

- **研究背景**：模仿学习（Imitation Learning, IL）旨在让智能体从专家演示中学习策略，但在现实应用中同时保证**高回报（performance）**与**严格安全约束（safety）**仍是一个根本性挑战。
- **现有方法的不足**：传统方法依赖人工设计的奖励函数（reward function）和成本函数（cost function），这类手工设计存在两大缺陷——（1）难以设计；（2）难以刻画现实场景中复杂的安全约束。
- **本文提出新问题设定**：**安全–性能双演示模仿学习**（Imitation Learning from Safety–Performance Dual Demonstrations）。训练数据被自然地划分为两类：
  - **安全演示**（safe demonstrations）：满足安全要求但可能次优；
  - **高性能演示**（performant demonstrations）：回报高但可能违反安全约束。
- **整体含义**：该研究在离线（offline）设定下探索如何从这两类演示中学习一个兼顾安全与性能的策略，对安全攸关的机器人操控等场景具有重要实际意义。

## 2. 方法论

- **方法名称**：**SpoilDICE**（Safe–Performant Offline Imitation Learning via stationary DIstribution Correction Estimation）。
- **核心思想**：将 DICE（stationary Distribution Correction Estimation，平稳分布修正估计）族的分布匹配方法与来自安全演示的**支持约束（support constraints）**相结合。
- **关键技术细节**：
  - **分布匹配**：利用 DICE 系列方法，将学得的策略的（状态–动作）平稳分布匹配到高性能演示所暗示的目标分布上，以获得高性能。
  - **支持约束**：从安全演示中提取状态–动作空间中的安全区域，将策略的优化限定在这些安全区域之内，从而避免策略"越界"到不安全行为。
  - **双演示融合**：通过上述两个机制同时利用两类演示——高性能演示提供回报信号，安全演示提供安全边界。
- **算法流程（文字描述）**：
  1. 分别收集安全演示数据集 $\mathcal{D}_{\text{safe}}$ 与高性能演示数据集 $\mathcal{D}_{\text{perf}}$；
  2. 利用安全演示估计安全状态–动作区域（支持约束）；
  3. 在该支持约束下，通过 DICE 风格的分布修正估计，将策略分布推向高性能演示所对应的分布；
  4. 输出一个既在安全区域内、又能逼近高性能分布的策略。
- **适用范围**：在论文层面，方法被定位为通用框架；在机器人操控场景中可作为可迁移的方法基础。

## 3. 实验设计

- **实验场景 / 数据集**：
  - **表格环境（tabular gridworld）**：用于在简化、可控环境中验证方法行为；
  - **连续安全关键域（continuous safety-critical domains）**：
    - **DSRL 数据集**（离线安全强化学习基准）；
    - **Safety Gymnasium 基准**（安全强化学习的标准仿真平台）。
- **对比基线**：论文声称与"先前的离线模仿学习基线（prior offline IL baselines）"进行了对比，**具体基线方法名称在所提供的摘要与元数据中未详细列出**。
- **评测指标**：从摘要可推断，主要关注两个维度——**回报（performance）**与**安全违反程度（safety violation）**，目标是取得两者的良好权衡。

## 4. 资源与算力

- **在所提供的论文内容（摘要 + 元数据）中未明确提及**：
  - GPU 型号与数量；
  - 训练时长（wall-clock time）；
  - 硬件配置或算力消耗。
- 因此，关于计算资源的细节**无法从现有材料中总结**，需查阅论文正文或附录以获取。

## 5. 实验数量与充分性

- **从已有信息看**：
  - 实验覆盖了**离散（gridworld）**与**连续（DSRL、Safety Gymnasium）**两类环境；
  - 包含**多种任务**（DSRL 与 Safety Gymnasium 通常包含多个安全关键任务），实验规模具有一定广度。
- **不充分 / 不确定之处**：
  - 由于无法获取正文，**具体的实验组数、是否包含消融实验（ablation）、对超参数的敏感性分析、不同演示数据比例的影响等均未知**；
  - 公平性方面也未能核实：是否在所有方法上使用相同的演示数据划分、相同的随机种子数、相同的训练步数等。
  - 总体来看，**实验是否充分且客观需要阅读正文与附录后判断**。

## 6. 主要结论与发现

- SpoilDICE 能够在**离线设定**下，**统一处理安全与性能的权衡问题**；
- 在表格 gridworld 与多个连续安全关键任务上，方法**始终能够在不显著牺牲安全性的前提下获得较强的回报**；
- 相较于先前的离线模仿学习基线，SpoilDICE 在性能–安全权衡上**取得了实质性提升（substantially outperforming）**；
- 结论：基于"安全–性能双演示"的离线模仿学习设定与基于 DICE 的解决框架，为复杂安全约束下的策略学习提供了一种**通用、可迁移的方案**。

## 7. 优点

- **问题设定新颖**：将模仿学习中的安全与性能问题统一为"双演示"学习问题，避免了手工设计成本函数的困难，贴合实际部署场景。
- **方法框架通用**：基于 DICE 的分布匹配 + 支持约束的设计是模块化的，可与多种 DICE 变体兼容，具有较好扩展性。
- **同时覆盖离散与连续环境**：在简化环境与高维连续控制基准上均得到验证，说明方法具备从理论验证到实际应用的迁移潜力。
- **离线设定贴合现实**：无需在线交互，可在历史数据上完成学习，对安全攸关场景尤为关键。

## 8. 不足与局限

- **依赖演示数据的自然划分**：该方法隐含假设数据已明确分为"安全"与"高性能"两类；现实中**演示的来源、标签与混杂（confounding）**可能不明确，存在数据划分偏差风险。
- **安全演示的质量影响上限**：若安全演示仅覆盖状态–动作空间中的部分安全区域，支持约束可能过严，导致策略性能受限。
- **缺乏对错误标注/混合演示的鲁棒性分析**：摘要与元数据中未提及对演示标签噪声、演示比例变化等的鲁棒性。
- **未提供计算资源细节**：无法评估方法的实际部署成本与可复现性。
- **应用限制**：
  - 在**多智能体、高维感知输入（如图像）**等更复杂场景下尚未验证；
  - 方法的**理论收敛性保证**与**安全性的形式化保证**（如最坏情况安全违反上界）在现有材料中未提及；
  - 对**演示分布偏移（distribution shift）**的严重程度是否敏感，也需进一步实验验证。
- **论文状态**：根据元数据，本文目前为 **ICLR-2026 拒稿公开版本**，评审意见可能揭示了本文未充分覆盖的问题，建议结合公开评审了解更深层不足。

---

（完）
