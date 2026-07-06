---
title: "SpatialVLA-Mamba: Efficient State-Space Models with Self-Refinement for Spatially-Grounded Robotic Control"
title_zh: SpatialVLA-Mamba：面向空间感知机器人控制的高效状态空间模型与自 refinement 机制
authors: "Sifan Li, Hao Tang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=sTn4EqE49A"
tags: ["query:rob-il"]
score: 9.0
evidence: "具备空间感知能力的 VLA 模型,面向端到端机器人控制与操控"
tldr: "现有视觉-语言-动作模型在空间感知、长时序执行效率与分布偏移鲁棒性方面存在不足。本文提出 SpatialVLA-Mamba,通过三项创新应对上述挑战:其一,空间感知编码器将深度与几何基元融入 RGB 特征,实现厘米级精度;其二,基于 Mamba 状态空间的解码器提升长时序执行的高效性与稳定性;其三,自 refinement 机制增强分布偏移下的鲁棒性。框架支持机器人在多样化操控任务中按语言指令执行,并在精度与稳定性上均取得提升。该工作为面向复杂操控的端到端通用视觉-动作模型贡献了新的架构方案。"
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有 VLA 模型存在空间感知不足、长时序效率低及分布偏移鲁棒性差三大挑战。
method: "提出 SpatialVLA-Mamba,融合空间感知编码器、Mamba 状态空间解码器与自 refinement 机制。"
result: "在多类语言指令操控任务上,模型在空间精度、长时序稳定性与鲁棒性方面均获提升。"
conclusion: 该工作为复杂机器人操控任务中的端到端视觉-动作模型提供了高效且鲁棒的架构新方案。
---

## Abstract
Recent progress in vision-language-action (VLA) models has enabled robots to follow natural language instructions across diverse manipulation tasks. However, existing approaches struggle with three persistent challenges: limited spatial grounding, which hampers centimeter-level precision; inefficiency and instability in long-horizon execution due to transformer-based decoders; and brittleness under distribution shift, where minor visual or linguistic variations can cause failure. We present SpatialVLA-Mamba, a framework that addresses these challenges through three innovations. First, a spatial-aware encoder augments RGB features with depth and geometric primitives, providing explicit metric grounding. Second, a Mamba-based state-space decoder replaces transformers, offering linear-time complexity and stable long-sequence modeling for extended action horizons. Third, a Chain-of-Thought Reinforcement Learning (CoT-RL) loop introduces intrinsic self-refinement: the policy generates textual outcome summaries of candidate trajectories, evaluates them with CLIPScore against the goal instruction, and updates itself via PPO without reliance on external language models. Experiments in Webots show that SpatialVLA-Mamba reduces spatial error by over 35\% relative to strong baselines, improves unseen-task success to 67.3\%, and achieves higher robustness to sensor noise and linguistic paraphrasing, while requiring less GPU memory and runtime. These results highlight the importance of combining spatial grounding, efficient sequence modeling, and intrinsic reasoning for reliable embodied control, pointing toward embodied foundation models that are accurate, efficient, and self-correcting.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "SpatialVLA-Mamba: Efficient State-Space Models with Self-Refinement for Spatially-Grounded Robotic Control" based on the provided abstract and metadata. Let me organize the content according to the 8 requested sections.

Let me carefully analyze what's given:
- The paper is about VLA (Vision-Language-Action) models for robotic control
- Three challenges: spatial grounding, long-horizon efficiency, distribution shift robustness
- Three innovations: spatial-aware encoder (depth + geometric primitives), Mamba state-space decoder, CoT-RL self-refinement
- Experiments in Webots simulator
- Results: 35% spatial error reduction, 67.3% unseen-task success, robust to sensor noise and linguistic paraphrasing, less GPU memory

Let me write a comprehensive summary.
</think>
# SpatialVLA-Mamba 论文总结

## 1. 核心问题与研究动机

- **研究背景**：视觉-语言-动作（VLA）模型近年来推动机器人依据自然语言指令完成多样化操控任务，但现有方法在落地中仍面临三类顽疾：
  - **空间感知能力不足**：缺乏对深度与几何结构的显式建模，难以达到厘米级操作精度。
  - **长时序执行效率低且不稳定**：主流 Transformer 解码器对长动作序列呈二次复杂度，容易出现误差累积。
  - **分布偏移下的鲁棒性差**：视觉外观或语言表述的细微变化即可导致策略失效。
- **整体目标**：构建一个同时具备**空间精度、长时序稳定性与分布鲁棒性**的端到端 VLA 框架，为通用具身操控提供"准、稳、健"的基础模型范式。

## 2. 方法论

### 2.1 总体框架
SpatialVLA-Mamba 由三个核心模块组成：空间感知编码器、Mamba 状态空间解码器、CoT-RL 自 refinement 机制，三者形成"感知—预测—反思"的闭环。

### 2.2 关键技术细节
- **空间感知编码器（Spatial-Aware Encoder）**
  - 在 RGB 视觉特征之上，**融合深度图与几何基元**（如表面法向量、边缘、关键点等），向特征空间注入显式的度量与几何先验。
  - 目的：将"看起来像"提升为"几何上对齐"，为下游动作预测提供可量化的空间锚点。
- **Mamba 状态空间解码器**
  - 用**选择性状态空间模型（SSM / Mamba）** 替换传统 Transformer 解码器。
  - 关键优势：复杂度由 **O(L²) 降至 O(L)**，便于长动作序列建模，并显著降低显存与运行时开销。
  - 行为上对长 horizon 任务更稳定，缓解误差累积。
- **CoT-RL 自 refinement 机制**
  - 借鉴 Chain-of-Thought 思路，让策略在执行后**生成候选轨迹的文本化结果摘要**。
  - 用 **CLIPScore** 衡量该摘要与目标语言指令的语义一致性，形成内部奖励信号。
  - 通过 **PPO** 在无需外部语言模型（LLM）参与的前提下进行策略自更新。
  - 强调 "intrinsic self-refinement"：反思与纠错由模型自身完成，不依赖外部监督。

### 2.3 算法流程（文字描述）
1. 视觉编码阶段：RGB + 深度 + 几何基元 → 空间感知特征。
2. 语言指令与空间特征共同输入 Mamba 解码器 → 长序列动作输出。
3. 执行后生成轨迹摘要 → CLIPScore 评估 → PPO 自更新策略。
4. 上述三步在训练与部署过程中循环迭代，实现精度、效率与鲁棒性的协同提升。

## 3. 实验设计

- **仿真平台**：使用 **Webots** 机器人仿真器进行实验验证。
- **任务类型**：包含多样化语言指令操控任务，覆盖训练中见过的任务（seen tasks）与未见过的新任务（unseen tasks），用于评估泛化能力。
- **基准指标**：
  - **空间误差**（Spatial error）：衡量厘米级精度。
  - **未见过任务成功率**（Unseen-task success rate）。
  - **鲁棒性指标**：对传感器噪声与语言复述（paraphrasing）的敏感度。
  - **资源消耗**：GPU 显存占用与运行时间。
- **对比方法（Baselines）**：摘要中未一一列出具体方法名，但明确表述对比了"strong baselines"，推断可能涵盖 OpenVLA、RT-2 类 Transformer-VLA 及其他空间感知或鲁棒性 VLA 改进版本。
- **具体实验数据点**：
  - 空间误差相对强基线**降低超过 35%**。
  - 未见过任务成功率提升至 **67.3%**。
  - 在传感器噪声与语言复述下表现更稳健。
  - GPU 显存与运行时间均低于对比方法。

## 4. 资源与算力

- **文中未明确披露**：
  - 使用的 **GPU 型号与数量**（如 A100/H100 数量、节点规模）未在所提供的摘要片段中给出。
  - **训练时长**、批大小、参数量等也未明确说明。
- 仅可确认结论性陈述：模型"requires less GPU memory and runtime"（相比基线更省显存与时间），但**具体数值缺失**。
- 局限：摘要层级信息有限，算力细节需进一步阅读正文或附录确认。

## 5. 实验数量与充分性

- **已有信息**：
  - 包含**主实验**（seen / unseen 任务成功率）、**空间精度实验**、**鲁棒性实验**（传感器噪声 + 语言复述）以及**效率实验**（显存 + 运行时间）。
  - 摘要中提及对比"strong baselines"，覆盖精度、泛化、鲁棒、效率四个维度。
- **可能的不充分之处**：
  - **仅在 Webots 仿真中验证**，未提及真实机器人实验，外推到现实世界的有效性存疑。
  - 缺少关于**消融实验**（ablation）的明确描述：三个模块（空间编码器、Mamba 解码器、CoT-RL）各自的独立贡献未在摘要中量化。
  - **基线数量与多样性**未完全披露，公平性难以独立判断。
  - **任务规模**（任务数量、指令数量、物体种类）未在摘要中给出，统计显著性尚不明确。
- **整体评价**：摘要呈现的实验覆盖"精度+泛化+鲁棒+效率"较为全面，但深度与可复现性细节需依赖正文。

## 6. 主要结论与发现

- **空间精度**：通过深度 + 几何基元融合，空间误差相对强基线**降低 35%+**。
- **泛化能力**：未见过任务的成功率达到 **67.3%**，表明语言与视觉变化下仍具较强泛化。
- **长时序稳定性**：Mamba 状态空间模型在长 horizon 上表现更稳定、显存更低。
- **鲁棒性**：对传感器噪声与语言复述具有更高抗干扰能力，验证 CoT-RL 自 refinement 的有效性。
- **总体定位**：将"空间锚定 + 高效序列建模 + 内省式推理"三者结合，是迈向**准确、高效、可自纠错的具身基础模型**的有益探索。

## 7. 优点

- **问题切中要害**：一次性针对 VLA 模型在精度、效率、鲁棒三方面的核心痛点，定位精准。
- **架构创新性强**：
  - 显式几何基元注入，弥补纯 RGB 视觉对空间的"近视"问题。
  - 用 Mamba 替代 Transformer，兼顾效率与长时序建模。
  - CoT-RL 形成内省式闭环，**摆脱对外部 LLM 的依赖**，工程独立性更高。
- **多维评价体系**：在精度、泛化、鲁棒、效率四个维度均有定量比较，结果说服力较强。
- **资源友好**：相比 Transformer 基线显存与运行时间更少，具有部署潜力。

## 8. 不足与局限

- **仅仿真验证**：实验在 Webots 中完成，**未涉及真实机器人迁移**，sim-to-real 鸿沟仍是开放问题。
- **算力与训练细节缺失**：GPU 型号、数量、训练时长、超参数等未在摘要中披露，影响可复现性。
- **基线透明度不足**：所对比的 "strong baselines" 具体名单未在摘要中给出，公平性难以独立评估。
- **缺少明确消融实验**：三个核心模块各自贡献未被摘要量化，组件级有效性证据不充分。
- **CLIPScore 评估的偏差风险**：依赖 CLIP 对"轨迹摘要 vs. 目标指令"的语义匹配，可能引入视觉-语言预训练模型的固有偏差，对细粒度操控目标的奖励信号可能不够精确。
- **任务与语言多样性有限**：未说明任务规模、指令分布与物体类别覆盖度，**分布偏移的代表性**可能不够全面。
- **自 refinement 机制的稳定性风险**：PPO 训练中的奖励稀疏或奖励黑客（reward hacking）问题在摘要中未讨论，闭环自更新可能带来训练不稳定的隐患。
- **应用范围限制**：当前以仿真语言指令操控为主，向**多模态指令、接触丰富的复杂操作**（如装配、柔性物体）扩展的能力未在文中体现。

（完）
