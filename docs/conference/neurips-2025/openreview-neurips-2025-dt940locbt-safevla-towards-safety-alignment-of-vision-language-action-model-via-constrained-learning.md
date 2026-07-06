---
title: "SafeVLA: Towards Safety Alignment of Vision-Language-Action Model via Constrained Learning"
title_zh: SafeVLA：基于约束学习的视觉-语言-动作模型安全对齐
authors: "Borong Zhang, Yuhao Zhang, Jiaming Ji, Yingshan Lei, Josef Dai, Yuanpei Chen, Yaodong Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dt940loCBT"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用视觉-语言-动作机器人策略的安全对齐框架
tldr: VLA 模型有望成为通用机器人策略，但实际部署中存在严重安全风险。SafeVLA 提出一体化安全方法，建模安全约束、主动激发不安全行为，并基于 CMDP 通过安全强化学习约束 VLA 训练。专项评估表明，该方法在不显著牺牲任务性能的情况下大幅提升安全性，是可部署通用机器人的重要组件。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 通用 VLA 策略在真实部署中可能对环境、机器与人造成危害。
method: 提出集成安全方法，建模约束、激发不安全行为并通过 CMDP 下的安全 RL 约束策略。
result: 在保持任务性能的同时显著提升 VLA 策略的安全性。
conclusion: SafeVLA 为通用 VLA 机器人的安全部署提供系统化解决方案。
---

## Abstract
Vision-language-action models (VLAs) show potential as generalist robot policies. However, these models pose extreme safety challenges during real-world deployment, including the risk of harm to the environment, the robot itself, and humans. *How can safety constraints be explicitly integrated into VLAs?* We address this by exploring an integrated safety approach (ISA), systematically **modeling** safety requirements, then actively **eliciting** diverse unsafe behaviors, effectively **constraining** VLA policies via safe reinforcement learning, and rigorously **assuring** their safety through targeted evaluations. Leveraging the constrained Markov decision process (CMDP) paradigm, ISA optimizes VLAs from a min-max perspective against elicited safety risks. Thus, policies aligned through this comprehensive approach achieve the following key features: (I) effective **safety-performance trade-offs**, reducing the cumulative cost of safety violations by 83.58\% compared to the state-of-the-art method, while also maintaining task success rate (+3.85\%). (II) strong **safety assurance**, with the ability to mitigate long-tail risks and handle extreme failure scenarios. (III) robust **generalization** of learned safety behaviors to various out-of-distribution perturbations. The effectiveness is evaluated on long-horizon mobile manipulation tasks.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "SafeVLA: Towards Safety Alignment of Vision-Language-Action Model via Constrained Learning" based on the provided abstract and metadata. Let me structure this according to the 8 required points.

The paper is about:
- Vision-Language-Action models (VLAs) for generalist robot policies
- Safety alignment for VLAs
- Integrated Safety Approach (ISA) with modeling, eliciting, constraining, and assuring
- Uses Constrained Markov Decision Process (CMDP) paradigm
- Min-max optimization against elicited safety risks
- 83.58% reduction in cumulative cost of safety violations vs SOTA
- +3.85% task success rate
- Long-horizon mobile manipulation tasks

Let me write a comprehensive summary in Chinese using Markdown format.
</think>
# SafeVLA：基于约束学习的视觉-语言-动作模型安全对齐

## 1. 论文核心问题与整体含义

**研究背景**：视觉-语言-动作模型（VLA）作为通用机器人策略，展现出强大的跨任务泛化潜力，被视为通用机器人的基础模型。然而，VLA 在真实环境部署中存在严重的安全风险，可能对环境、机器人自身以及人类造成物理伤害。

**核心问题**：如何将安全约束显式、有效地整合进 VLA 策略中，确保其在保持任务能力的同时具备安全保障？

**研究动机**：当前 VLA 的研究主要聚焦于任务性能（如成功率），对安全对齐缺乏系统性解决方案，制约了其在真实场景中的可部署性。

## 2. 方法论

**核心思想**：提出 **ISA（Integrated Safety Approach，集成安全方法）** 框架，将安全对齐分解为四个关键步骤：

- **建模（Modeling）**：系统化地定义和形式化安全需求。
- **激发（Eliciting）**：主动诱导多样化的不安全行为，构建安全风险数据集。
- **约束（Constraining）**：基于 **约束马尔可夫决策过程（CMDP）** 范式，通过安全强化学习对 VLA 策略进行约束训练。
- **验证（Assuring）**：通过专项评估严格验证安全性能。

**关键技术细节**：

- **优化范式**：基于 CMDP，将任务奖励与安全代价联合建模；从 **min-max 视角** 进行优化，在最坏情况（最激烈诱发的不安全风险）下仍保证策略安全。
- **不安全行为激发**：通过对抗式或主动探索方法，生成多样化的不安全轨迹，丰富训练中的"风险样本"。
- **约束 RL**：在策略训练中引入安全约束（例如拉格朗日方法或类似约束优化），使 VLA 在最大化任务回报的同时，控制安全代价在阈值之下。
- **端到端对齐**：方法作用于完整的 VLA 流程，而非仅限后处理。

**算法流程**（概述）：
1. 形式化安全约束 → 2. 主动采集不安全行为样本 → 3. 构建 CMDP 训练环境 → 4. 使用安全 RL（约束优化）微调 VLA → 5. 在专项安全基准上评估。

## 3. 实验设计

**任务场景**：长时序（long-horizon）**移动操作（mobile manipulation）** 任务。

**基准与评估维度**：

- **任务性能**：任务成功率（Task Success Rate）。
- **安全性能**：累积安全违规代价（Cumulative Cost of Safety Violations）、长尾风险处理能力、极端失败场景下的安全保障。
- **泛化性**：对 **分布外（OOD）扰动** 的鲁棒性。

**对比方法**：与"当前最优方法（state-of-the-art method）"对比（摘要中未点名具体基线，但声明 SafeVLA 在安全违规代价上较 SOTA 降低 83.58%，同时任务成功率反而提升 3.85%）。

## 4. 资源与算力

- **未明确披露**：所提供的元数据与摘要中均**未提及**所使用的 GPU 型号、数量、训练时长、显存占用或算力成本等具体信息。

## 5. 实验数量与充分性

- **实验规模**：摘要中仅给出两个量化指标（-83.58% 安全代价，+3.85% 任务成功率）以及三方面的定性结论（安全-性能权衡、安全保障、泛化性）。
- **充分性评估**：
  - 评估维度覆盖较广（任务成功、安全代价、OOD 鲁棒性、长尾与极端场景），**评估设计较为全面**。
  - 但仅凭摘要信息难以判断具体实验组数、是否包含消融实验、不同安全阈值下的灵敏度分析、不同 VLA 骨干（如 OpenVLA、RT-2 等）的对比。
  - **基线对比略显模糊**：未明确指明对比的 SOTA 方法名称。
  - 在长时序移动操作任务上，**未透露**真实机器人实验还是仅仿真实验。

## 6. 主要结论与发现

- SafeVLA 通过 CMDP 框架下的 min-max 优化，在 **任务性能几乎不退化**（成功率 +3.85%）的同时，将 **累积安全违规代价降低 83.58%**。
- 所得策略具备**长尾风险缓解能力**，并能处理**极端失败场景**。
- 学到的安全行为对 **OOD 扰动具有良好泛化性**。
- 验证了将安全对齐显式集成到 VLA 训练中是可行且有效的。

## 7. 优点（亮点）

- **方法系统性**：将"建模-激发-约束-验证"四阶段整合为一套端到端安全对齐流水线，思路清晰完整。
- **min-max 视角**：在最坏情况（最严重诱发风险）下进行优化，理论上对安全保证更稳健。
- **性能-安全双赢**：在安全大幅提升的同时任务性能不降反升，避免了常见的安全-性能 trade-off 困境。
- **关注 OOD 泛化与极端场景**：契合真实部署对鲁棒性的核心需求。
- **可作为通用机器人安全组件**：框架具备良好的可扩展性，可适配不同的 VLA 骨干。

## 8. 不足与局限

- **算力信息缺失**：未公开训练资源、训练时长和超参，**复现性受限**。
- **基线不明确**：摘要中未指明对比的 SOTA 具体为何方法，第三方难以判断提升幅度的含金量。
- **任务与平台单一**：评估集中于"长时序移动操作"任务，**尚未在多种机器人形态**（如桌面机械臂、双臂、人形等）和更广泛任务上验证。
- **仿真 vs 真实**：未说明是仿真还是真实机器人实验，**真实世界的 Sim-to-Real 差距** 是该类工作的关键风险。
- **安全约束形式化**：摘要未深入说明"安全需求"如何形式化（如何定义代价函数、约束阈值），**依赖人工设计的代价函数可能引入偏差**。
- **可扩展性疑问**：对极大规模 VLA（如 7B/13B 参数级别）进行 CMDP 安全 RL 微调，**训练稳定性与算力成本** 是潜在挑战。
- **缺乏消融细节**：未提供 4 个阶段（建模/激发/约束/验证）中各模块的消融贡献，模块必要性存疑。
- **统计显著性未明示**：仅给出一个数值（83.58%、3.85%），**是否经过多随机种子平均**尚不可知。

（完）
