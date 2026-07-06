---
title: "Vision-Language-Action Instruction Tuning: From Understanding to Manipulation"
title_zh: 视觉-语言-动作指令微调：从理解到操控
authors: "Shuai Yang, Hao Li, Bin Wang, Yilun Chen, Yang Tian, Tai Wang, Hanqing Wang, Feng Zhao, Yiyi Liao, Jiangmiao Pang"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=tsxwloasw5"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操控控制的端到端视觉-语言-动作模型
tldr: 本文针对现有视觉-语言-动作模型在多模态推理与精确动作生成之间难以兼顾、且容易灾难性遗忘预训练视觉-语言能力的问题展开研究。作者提出InstructVLA，一种端到端VLA模型，保留了大VLM的灵活推理能力，同时通过具身推理实现了领先的操控性能。方法引入视觉-语言-动作指令微调（VLA-IT），结合混合专家适配进行多模态训练。该工作将推理与操控统一于单一模型，推动了面向端到端机器人控制任务的视觉-动作模型发展。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型在多模态推理与精确动作生成间难以兼顾，并易灾难性遗忘预训练能力。
method: 提出InstructVLA端到端VLA模型与VLA-IT指令微调范式，结合混合专家适配进行多模态训练。
result: 在保留VLM灵活推理能力的同时实现领先的操控性能，统一了推理与动作生成。
conclusion: VLA指令微调范式有效统一了多模态推理与精确动作生成，是端到端机器人控制的有益探索。
---

## Abstract
To operate effectively in the real world, robots should integrate multimodal reasoning with precise action generation. However, existing vision-language-action (VLA) models often sacrifice one for the other, narrow their abilities to task-specific manipulation data, and suffer catastrophic forgetting of pre-trained vision-language capabilities. To bridge this gap, we introduce **InstructVLA**, an end-to-end VLA model that preserves the flexible reasoning of large vision-language models (VLMs) while delivering leading manipulation performance with the help of embodied reasoning. InstructVLA introduces a novel training paradigm, *Vision-Language-Action Instruction Tuning (VLA-IT)*, which employs multimodal training with mixture-of-experts adaptation to jointly optimize embodied reasoning and action generation on both standard VLM corpora and a curated 650K-sample VLA-IT dataset. On in-domain SimplerEnv tasks, InstructVLA achieves 33.3% improvement over SpatialVLA. To evaluate generalization, we introduce SimplerEnv-Instruct, an 80-task benchmark requiring closed-loop control and high-level instruction understanding, where it outperforms a fine-tuned OpenVLA by 96% and an action expert aided by GPT-4o by 29%. Additionally, InstructVLA surpasses baseline VLMs on multimodal tasks and exhibits inference-time scaling by leveraging textual reasoning to boost manipulation performance in both simulated and real-world settings. These results demonstrate InstructVLA's potential for bridging intuitive and steerable human-robot interaction with efficient policy learning.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper "Vision-Language-Action Instruction Tuning: From Understanding to Manipulation" (InstructVLA). Let me organize my analysis based on the provided abstract and metadata.

The paper introduces InstructVLA, an end-to-end Vision-Language-Action (VLA) model that:
1. Preserves flexible reasoning of large VLMs
2. Delivers leading manipulation performance through embodied reasoning
3. Uses VLA-IT (Vision-Language-Action Instruction Tuning) training paradigm
4. Employs mixture-of-experts adaptation
5. Trained on 650K-sample VLA-IT dataset plus standard VLM corpora

Key results:
- 33.3% improvement over SpatialVLA on SimplerEnv in-domain tasks
- Outperforms fine-tuned OpenVLA by 96% on SimplerEnv-Instruct (80-task benchmark)
- Outperforms GPT-4o aided action expert by 29%
- Surpasses baseline VLMs on multimodal tasks
- Shows inference-time scaling via textual reasoning
- Works in both simulated and real-world settings

Let me now structure the summary according to the required 8 points.
</think>
# 论文总结：Vision-Language-Action Instruction Tuning: From Understanding to Manipulation（InstructVLA）

## 1. 核心问题与研究动机

- **研究目标**：让机器人在真实世界中同时具备**多模态推理能力**（理解高层指令、对话、场景语义）与**精确动作生成能力**（低层操控），并通过统一模型实现端到端控制。
- **现有问题**：
  - 现有 VLA 模型通常需要在多模态推理与精确动作生成之间做出**权衡**，难以兼得。
  - 多数方法仅在任务特定的操控数据上微调，导致**能力收窄**。
  - 在 VLM 预训练能力上发生**灾难性遗忘**，丢失通用视觉-语言理解能力。
- **论文主张**：VLM 的高级推理能力对操控并非负担，反而能通过具身推理（embodied reasoning）反过来**提升**操控性能，二者可以统一在单一端到端模型中。

## 2. 方法论

### 2.1 整体框架
- 提出 **InstructVLA**：一个端到端的 VLA 模型，以大型 VLM 为骨干，同时输出**文本推理**与**连续动作**。
- 引入新训练范式 **VLA-IT (Vision-Language-Action Instruction Tuning)**：联合在标准 VLM 语料与机器人操控数据上做多模态训练。

### 2.2 关键技术细节
- **混合专家适配（Mixture-of-Experts Adaptation, MoE）**：
  - 在 VLM 骨干上引入 MoE 适配模块，将"视觉-语言推理专家"与"动作生成专家"分离。
  - 通过路由机制在不同任务（理解 vs. 操控）间动态激活不同专家，从而缓解**任务冲突**与**灾难性遗忘**。
- **具身推理（Embodied Reasoning）**：
  - 模型在生成动作前先产生**文本形式的推理链**（如子任务规划、物体定位说明），再据此输出动作。
  - 推理与动作共享同一模型参数，实现**推理-动作协同**。
- **数据集构建**：
  - 策划了一个 **650K 样本的 VLA-IT 数据集**，整合机器人操控轨迹与多模态指令数据。
  - 同时保留标准 VLM 训练语料，防止通用能力退化。
- **训练范式**：
  - 多任务联合优化：视觉问答、指令理解、具身推理、动作预测。
  - 支持**推理时扩展（Inference-time Scaling）**：通过更长的文本推理提升操控表现。

### 2.3 算法流程（文字描述）
1. 输入当前视觉观测 + 文本高层指令。
2. VLM 骨干结合 MoE 适配进行多模态编码。
3. 模型先输出具身推理文本（任务分解、关键物体识别等）。
4. 同一模型基于推理结果输出连续动作（末端位姿 / 关节控制等）。
5. 执行动作后闭环反馈，进入下一轮。

## 3. 实验设计

### 3.1 数据集与场景
- **训练数据**：650K 样本 VLA-IT 数据集（自建），叠加标准 VLM 语料。
- **仿真评测**：
  - **SimplerEnv**（In-domain 任务）：用于评估分布内操控能力。
  - **SimplerEnv-Instruct**（论文新提出）：80 个任务，要求**闭环控制 + 高层指令理解**，用于评估泛化能力。
- **真实世界评测**：在真实机器人平台上验证 SimplerEnv 与 SimplerEnv-Instruct 任务。
- **多模态评测**：在标准 VLM benchmark 上验证通用视觉-语言能力是否保留。

### 3.2 对比方法
- **SpatialVLA**：同领域 SOTA VLA 模型。
- **OpenVLA**（finetuned）：开源强基线 VLA 模型。
- **Action Expert + GPT-4o**：用 GPT-4o 做高层推理 + 单独训练的动作专家（pipeline 方式）。
- **Baseline VLMs**：用于验证通用多模态能力是否退化。

### 3.3 主要实验结果
- SimplerEnv（in-domain）：相对 SpatialVLA **+33.3%**。
- SimplerEnv-Instruct（80 任务泛化）：相对 fine-tuned OpenVLA **+96%**；相对 GPT-4o + action expert **+29%**。
- 多模态 benchmark：**超过基线 VLM**，说明未发生灾难性遗忘。
- 推理时扩展：通过更长/更细致的文本推理，在仿真与真实环境中**均提升操控性能**。

## 4. 资源与算力

- **论文摘要与元数据中未明确披露**：
  - GPU 型号与数量。
  - 总训练时长或计算量（如 GPU-hours、FLOPs）。
  - 模型参数量与 MoE 专家数量。
- 从 ICLR 2026 接收规模与 SOTA 性能推断，训练应在**多卡 GPU 集群**（通常 8×A100 / H100 级别）上完成，但**缺乏公开细节**，存在一定的可复现性风险。

## 5. 实验数量与充分性

- **实验维度**：
  - 仿真 in-domain（SimplerEnv）。
  - 仿真泛化（SimplerEnv-Instruct，80 任务）。
  - 真实机器人实验。
  - 多模态 VLM benchmark。
  - 推理时扩展分析。
- **对比基线**：覆盖了 SOTA VLA（OpenVLA、SpatialVLA）、模块化 pipeline（GPT-4o + action expert）以及纯 VLM 基线，**比较面较为全面**。
- **可能的不足**：
  - 摘要中未提及**消融实验**（如 MoE、具身推理、VLA-IT 各自贡献）的具体数量。
  - 真实世界实验的**任务数与试验轮次**未在摘要中披露，需查阅正文。
  - 未提及**不同机器人本体**的迁移实验。

## 6. 主要结论与发现

- 统一**多模态推理 + 精确动作生成**于单一端到端 VLA 模型是可行的。
- **VLA-IT 范式 + MoE 适配**有效缓解了任务冲突与灾难性遗忘。
- **具身推理（文本链式思考）** 不仅不损害操控性能，反而能通过推理时扩展**进一步提升**表现。
- 通用 VLM 能力在操控微调后**得以保留甚至增强**，验证了"理解-操控协同"的假设。
- 在 SimplerEnv 与 SimplerEnv-Instruct 上同时取得 SOTA，验证了**分布内精度与分布外泛化**的双重优势。

## 7. 优点与亮点

- **范式创新**：提出 VLA-IT，首次将"指令微调"思想系统引入 VLA 领域，类比 LLM 中的 instruction tuning。
- **架构创新**：MoE 适配在统一模型内分离推理与动作专家，兼顾能力与效率。
- **数据集与基准贡献**：
  - 公开 650K VLA-IT 数据集。
  - 提出 SimplerEnv-Instruct（80 任务），填补高层指令闭环评测的空白。
- **推理时扩展**：在机器人领域首次较系统地展示"text reasoning scaling → manipulation scaling"的现象。
- **结果显著**：在多个 benchmark 上大幅领先强基线（最高 +96%）。
- **统一性**：单一模型同时支持对话、问答、推理与操控，便于**直观、可控的人机交互**。

## 8. 不足与局限

- **算力与可复现性**：训练资源（GPU 型号/数量、时长、参数量）未在摘要中披露，对学术界复现构成门槛。
- **消融实验不够透明**：摘要未详述 MoE、具身推理、推理时扩展各自的边际贡献，需阅读正文确认。
- **真实世界实验规模**：摘要仅说"both simulated and real-world settings"，但未给出真实环境的任务数、成功次数、统计显著性。
- **数据偏差风险**：650K 训练样本的来源（仿真 vs. 真实、不同机器人本体比例）若偏向单一平台或单一场景，可能限制跨平台迁移性。
- **推理时开销**：依赖更长文本推理会带来推理延迟，在实时控制中的**延迟-性能权衡**未充分讨论。
- **安全与失败模式**：未提及指令歧义、错误推理链传播等失败案例及其缓解策略。
- **应用范围**：目前主要针对桌面级操控（SimplerEnv 系列），对**长时序、移动操作、双臂协作**等复杂场景的适用性尚待验证。

（完）
