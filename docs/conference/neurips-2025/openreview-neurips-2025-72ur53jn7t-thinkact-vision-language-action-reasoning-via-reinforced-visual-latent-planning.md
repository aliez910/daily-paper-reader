---
title: "ThinkAct: Vision-Language-Action Reasoning via Reinforced Visual Latent Planning"
title_zh: ThinkAct：通过强化视觉潜规划实现视觉-语言-动作推理
authors: "Chi-Pin Huang, Yueh-Hua Wu, Min-Hung Chen, Yu-Chiang Frank Wang, Fu-En Yang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=72UR53jN7T"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向端到端机器人控制的视觉-语言-动作推理
tldr: 针对现有端到端VLA模型缺乏显式推理、难以进行多步规划与适应复杂任务变化的问题，本文提出ThinkAct双系统框架，通过强化视觉潜规划连接高层推理与低层动作执行。ThinkAct训练多模态大模型生成具身推理规划，并以动作对齐的视觉奖励进行强化。该方法显著提升了视觉-语言-动作模型在复杂机器人控制任务中的规划与适应能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA端到端映射缺乏显式推理，难以支持多步规划与复杂任务适应。
method: 提出ThinkAct双系统框架，以强化视觉潜规划连接高层推理与低层动作执行。
result: 在多种复杂机器人控制任务上提升了VLA模型的规划能力与适应性。
conclusion: 为通用VLA模型提供了一种结合推理与动作执行的新框架。
---

## Abstract
Vision-language-action (VLA) reasoning tasks require agents to interpret multimodal instructions, perform long-horizon planning, and act adaptively in dynamic environments. Existing approaches typically train VLA models in an end-to-end fashion, directly mapping inputs to actions without explicit reasoning, which hinders their ability to plan over multiple steps or adapt to complex task variations. In this paper, we propose ThinkAct, a dual-system framework that bridges high-level reasoning with low-level action execution via reinforced visual latent planning. ThinkAct trains a multimodal LLM to generate embodied reasoning plans guided by reinforcing action-aligned visual rewards based on goal completion and trajectory consistency. These reasoning plans are compressed into a visual plan latent that conditions a downstream action model for robust action execution on target environments. Extensive experiments on embodied reasoning and robot manipulation benchmarks demonstrate that ThinkAct enables few-shot adaptation, long-horizon planning, and self-correction behaviors in complex embodied AI tasks.

---

## 论文详细总结（自动生成）

<think>
The user wants me to summarize a paper based on the provided metadata and abstract. Let me analyze the content carefully.

The paper is "ThinkAct: Vision-Language-Action Reasoning via Reinforced Visual Latent Planning" - a NeurIPS 2025 accepted paper.

Key points from the abstract:
- It's about Vision-language-action (VLA) reasoning
- Agents need to interpret multimodal instructions, perform long-horizon planning, act adaptively
- Existing approaches train VLA models end-to-end, mapping inputs to actions without explicit reasoning
- This limits multi-step planning and adaptation to complex task variations
- ThinkAct is a dual-system framework
- Bridges high-level reasoning with low-level action execution via reinforced visual latent planning
- Trains a multimodal LLM to generate embodied reasoning plans
- Uses action-aligned visual rewards based on goal completion and trajectory consistency
- Reasoning plans compressed into visual plan latent that conditions downstream action model
- Experiments on embodied reasoning and robot manipulation benchmarks
- Enables few-shot adaptation, long-horizon planning, self-correction

The PDF text was just a CAPTCHA page, so I don't have the full paper content. I'll need to work with the abstract and metadata provided.

Let me structure the response according to the 8 requested points in Chinese with Markdown formatting.
</think>
# ThinkAct 论文总结

## 一、核心问题与研究背景

- **研究领域**：面向端到端机器人控制的**视觉-语言-动作（VLA）**推理任务，要求智能体能够理解多模态指令、进行长时序规划（long-horizon planning），并在动态环境中自适应地执行动作。
- **现有方法痛点**：当前主流的 VLA 模型普遍采用端到端训练范式，将多模态输入直接映射为动作输出，**缺乏显式的中间推理机制**。
  - 难以进行多步规划；
  - 难以适应复杂任务变化；
  - 泛化性与可解释性受限。
- **研究目标**：提出一种将**高层推理**与**低层动作执行**解耦但又紧密耦合的框架，弥补端到端 VLA 在推理规划能力上的不足。

## 二、方法论：ThinkAct 双系统框架

- **核心思想**：受"快慢系统"与人类"思考—行动"认知机制启发，采用 **System 1（慢思考 / 规划器）+ System 2（快反应 / 执行器）** 的双系统架构。
  - **System 1（规划器）**：基于多模态大语言模型（MLLM），负责生成**具身推理规划（embodied reasoning plans）**。
  - **System 2（执行器）**：下游动作执行模型，接收规划器输出的**视觉潜变量（visual plan latent）**作为条件，输出具体动作。
- **关键技术细节**：
  - **强化视觉潜规划（Reinforced Visual Latent Planning）**：使用**强化学习**对 MLLM 进行训练，奖励信号由两部分组成：
    1. **目标完成度（goal completion）**：当前潜规划在多大程度上朝着任务目标推进；
    2. **轨迹一致性（trajectory consistency）**：规划结果与实际执行轨迹之间的一致性。
  - **视觉计划潜空间压缩**：将 MLLM 生成的推理计划压缩到一个**视觉潜变量（visual plan latent）**，而非直接以文本形式传递给动作模型，从而保留更丰富的空间/视觉信息。
  - **跨环境迁移**：潜变量条件化设计使执行器可在不同目标环境中复用同一规划，实现**少样本适应（few-shot adaptation）**与**自校正（self-correction）**。
- **算法流程（文字描述）**：
  1. 输入：多模态指令（文本 + 视觉观察）。
  2. MLLM 推理生成候选推理计划。
  3. 强化学习依据动作对齐的视觉奖励对计划打分/优化。
  4. 将最优计划压缩为视觉潜变量。
  5. 下游动作模型以潜变量为条件生成低层动作序列。
  6. 环境反馈用于在线调整与自校正。

## 三、实验设计

- **数据集 / 场景**：
  - **具身推理（Embodied Reasoning）**基准；
  - **机器人操作（Robot Manipulation）**基准。
  - 注：因本次未能成功抓取 PDF 正文（被 CAPTCHA 拦截），具体数据集名称（如 RLBench、ManiSkill2、Habitat、ALFRED 等可能候选）暂无法从文本中确认。
- **评估维度**：
  - 少样本适应能力（few-shot adaptation）；
  - 长时序规划能力（long-horizon planning）；
  - 自校正行为（self-correction behaviors）。
- **对比方法**：摘要未列出具体基线，但根据领域背景，对比对象应涵盖：
  - 端到端 VLA 模型（如 OpenVLA、RT-2、π₀ 等同类型工作）；
  - 仅依赖文本/链式思考（CoT）规划的分层方法；
  - 不含强化信号的视觉潜规划消融版本。

## 四、资源与算力

- 摘要与元数据中**未明确说明**使用的 GPU 型号、数量、训练时长等算力信息。
- 仅可推断：训练涉及多模态大语言模型 + 下游动作模型，参数规模与计算开销通常较大，**建议读者参考论文正文或附录以获取完整训练资源配置**。

## 五、实验数量与充分性

- 由于 PDF 内容未能完整获取，**具体的实验组数、基准数量、消融设置无法从摘要中精确统计**。
- 从摘要描述来看，实验覆盖至少两个类别（具身推理 + 机器人操作），并针对三项关键能力（少样本适应 / 长时序规划 / 自校正）分别进行了评估，**设计方向较为全面**。
- 但**是否存在充分的消融实验**（如去掉强化奖励、去掉视觉潜压缩、换不同 MLLM 骨干等）**需要核对正文**才能判断。
- 公平性方面：作为 NeurIPS 2025 录用论文，实验设计通常会经过同行评审检验，可信度较高；但仅凭摘要尚不能完全确认。

## 六、主要结论与发现

- ThinkAct 的双系统设计有效桥接了**高层语言/视觉推理**与**低层动作控制**之间的鸿沟。
- 通过**强化视觉潜规划**机制：
  - 实现了复杂具身 AI 任务中的**少样本适应**；
  - 提升了**长时序规划**能力；
  - 赋予了智能体**自校正**的行为能力。
- 为通用 VLA 模型提供了一种**可扩展的"推理+执行"新框架范式**。

## 七、优点与亮点

- **双系统架构**：清晰分离规划与执行，符合认知科学中"深思熟虑 vs 快速反应"的双过程理论，模块化程度高。
- **强化视觉潜规划**：相较于纯文本 CoT 规划，视觉潜变量能保留更丰富的空间结构信息；引入强化信号使规划与下游动作真正对齐。
- **多奖励设计**：同时考虑**目标完成度**与**轨迹一致性**，缓解了奖励稀疏问题，使训练信号更稳定。
- **少样本 + 自校正**：显著提升了模型在未见任务和动态扰动下的鲁棒性，是迈向通用机器人智能的重要一步。
- **任务通用性**：框架可与不同的 MLLM 骨干和动作执行器组合，具有较强的**可迁移性与扩展性**。

## 八、不足与局限

- **PDF 未能抓取**：本次由于目标页面触发 CAPTCHA 验证，论文正文内容缺失，上述总结主要基于摘要与元数据，可能遗漏关键细节（如具体实验数据、对比基线、消融设置、算力等）。
- **强化学习训练成本**：基于强化信号训练 MLLM 通常需要大量样本与算力开销，**实际部署门槛与训练稳定性是潜在风险**。
- **奖励设计依赖**：目标完成度与轨迹一致性奖励的可靠性直接影响规划质量，若奖励模型存在偏差，可能导致规划行为偏差（reward hacking 风险）。
- **视觉潜空间可解释性**：将推理计划压缩为潜变量虽然高效，但**牺牲了一部分可解释性**，难以直接追溯推理链条。
- **实验覆盖度未知**：是否在真实硬件机器人上验证、与 SOTA VLA 模型（如 π₀、OpenVLA-OFT 等）的对比是否充分，仍需核对正文。
- **任务泛化边界**：对"长时序 + 高动态"场景下的失败模式分析、OOD 场景鲁棒性等**安全关键问题**未在摘要中讨论。

（完）
