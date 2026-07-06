---
title: "FDVLA: A Flow-Diffusion Vision-Language-Action Framework with Dual Reasoning Modulation"
title_zh: FDVLA：具有双推理调制的流-扩散视觉-语言-动作框架
authors: "Maowei Jiang, Qi Wang, Ruiqi Li, Hongfeng Ai, Quangao Liu, Yifan WANG, Hongliang Niu, Pengyu Zeng, Moquan Cheng, Yusong Hu, Xiaoxin Deng, Zhiyong Dong, Peter Búš, Long ZENG"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=qQuca6fbFX"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向复杂操控的流-扩散视觉-语言-动作框架
tldr: 现有 VLA 框架中，自回归解码易产生不连续轨迹，纯扩散方法缺乏对推理语义的显式建模。本文提出 FDVLA 统一框架，将语义推理与基于流场的全局轨迹规划相结合，再通过扩散机制进行细粒度动作精炼。方法在多种复杂操控任务中生成物理上更连贯、更平滑的动作序列。该工作将高层推理与底层动作生成深度融合，推动了通用VLA模型在精细操控中的发展。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 自回归VLA轨迹不连续，纯扩散VLA缺乏对高层推理语义的显式注入。
method: 提出流-扩散机制，将流场全局轨迹规划与扩散细粒度动作生成相结合，并融入语义推理。
result: 在多种复杂操控任务中生成了更平滑、更物理连贯的动作序列。
conclusion: 将高层语义推理与底层动作生成深度融合，推动了通用VLA在精细操控中的发展。
---

## Abstract
Recent advances in vision-language models (VLMs) have empowered robots to interpret natural language and perform complex manipulation tasks. Existing vision-language-action (VLA) frameworks typically adopt autoregressive decoding or diffusion-based strategies. While the former may lead to fragmented or less smooth trajectories, the latter often lacks explicit injection of reasoning semantics into the action generation process, which can affect the quality of generated actions. In this paper, we propose FDVLA, a unified framework integrating semantic reasoning with smooth and physically coherent action generation. We introduce a flow-diffusion mechanism that unifies global trajectory planning (via flow fields) and fine-grained action refinement (via diffusion) in a dual-headed policy, enabling physically coherent and stable action generation. Additionally, we design DualMod, a lightweight module that injects semantic signals into both velocity and noise prediction branches, thus integrating high-level reasoning into action generation. Extensive experiments across diverse simulated and real-world robotic tasks, demonstrate that FDVLA achieves solid performance, efficient inference, and shows robust generalization under a variety of task conditions.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper titled "FDVLA: A Flow-Diffusion Vision-Language-Action Framework with Dual Reasoning Modulation" based on the provided abstract and metadata. I need to structure it according to the 8 specified points using Markdown format.

Let me organize the information:

1. Core problem and motivation: Existing VLA frameworks use autoregressive decoding (which leads to fragmented/less smooth trajectories) or diffusion-based strategies (which lack explicit injection of reasoning semantics).

2. Method: FDVLA framework with flow-diffusion mechanism, dual-headed policy, DualMod module for semantic injection into velocity and noise prediction branches.

3. Experiments: Diverse simulated and real-world robotic tasks, achieving solid performance, efficient inference, robust generalization.

4. Resources: Not mentioned in the abstract/metadata.

5. Experiment quantity: Not specified in detail, but extensive experiments across diverse tasks.

6. Conclusions: FDVLA achieves solid performance, efficient inference, and robust generalization.

7. Highlights: Unified framework, flow-diffusion mechanism, DualMod module.

8. Limitations: Not mentioned in detail.

I'll write this up in Chinese with clear Markdown formatting.
</think>
# FDVLA 论文总结

## 1. 核心问题与研究背景

- **问题定位**：随着视觉-语言模型（VLM）的发展，机器人能够通过自然语言完成复杂操控任务，但现有的视觉-语言-动作（VLA）框架在动作生成层面仍存在两大核心缺陷：
  - **自回归解码策略**：倾向于产生碎片化、不连续的运动轨迹，难以保证物理连贯性；
  - **纯扩散方法**：虽然能生成平滑动作，但缺乏对高层推理语义的显式注入，导致动作生成质量受限于语义-动作的脱节。
- **研究目标**：构建一个能同时保证动作平滑性、物理连贯性以及高层语义推理能力统一的VLA框架。

## 2. 方法论

- **整体框架**：提出 **FDVLA**（Flow-Diffusion Vision-Language-Action），将语义推理与基于物理感知的动作生成统一在同一个框架内。
- **核心机制——流-扩散机制（Flow-Diffusion Mechanism）**：
  - **流场（Flow Fields）**：负责**全局轨迹规划**，在动作空间上学习速度场（velocity field），提供长程、平滑的运动趋势；
  - **扩散（Diffusion）**：负责**细粒度动作精炼**，在流场预测的基础上对动作进行迭代去噪与优化。
  - 两者以**双头策略（dual-headed policy）**形式融合，兼顾全局一致性与局部细节。
- **关键模块——DualMod**：
  - 一种轻量级模块，作用是将**高层语义信号**显式注入到策略的两个分支中：
    - 注入到**速度预测分支**（流场端），使轨迹规划具有任务语义引导；
    - 注入到**噪声预测分支**（扩散端），使动作精炼过程受语义约束。
  - 通过该模块实现"高层推理"与"底层动作生成"的深度耦合。

## 3. 实验设计

- **任务场景**：覆盖**多种仿真任务**与**真实世界机器人操控任务**，体现跨域泛化能力。
- **Benchmark**：从摘要与元数据看，文中涉及多样化任务条件下的综合评测，但具体数据集/benchmark名称未在提供材料中详细列出。
- **对比方法**：未在摘要中明确点名对比基线（typical 候选可能包括自回归 VLA、纯扩散 VLA、其它 flow-based 或 diffusion-based 策略），需进一步从正文确认。
- **评测维度**：性能（任务成功率）、**推理效率**、**泛化能力**（在不同任务条件下的鲁棒性）。

## 4. 资源与算力

- 在提供的摘要与元数据中**未明确披露**所用 GPU 型号、数量、训练时长等算力细节。
- 仅可推断 DualMod 被设计为"轻量级（lightweight）"模块，暗示对额外算力开销进行了控制。

## 5. 实验数量与充分性

- 摘要中提到"**Extensive experiments across diverse simulated and real-world robotic tasks**"，但具体实验组数、是否包含完整消融、跨平台/跨机器人形态的对比等细节**未在当前文本中给出**。
- 由于覆盖了**仿真 + 真实机器人**双场景，并测试了**性能、效率、泛化**三方面指标，从外部表述上实验设计相对全面，但具体充分性需结合正文中的消融实验、超参数分析、跨具身迁移等进一步评估。

## 6. 主要结论与发现

- FDVLA 在多样化仿真与真实机器人任务中均取得**稳健（solid）的性能表现**；
- 具备**高效的推理速度**，满足实时操控需求；
- 在多种任务条件下表现出**鲁棒的泛化能力**；
- 验证了"**流场全局规划 + 扩散局部精炼 + 语义注入**"这一组合在VLA范式中的有效性。

## 7. 优点与亮点

- **统一框架设计**：将"高层语义推理"与"底层物理动作生成"在同一模型中显式耦合，弥补了既有方法语义-动作脱节的不足；
- **双头策略创新**：流场 + 扩散的组合既保证了轨迹的全局平滑性，又保留了扩散模型在细粒度动作生成上的优势；
- **轻量级语义注入模块 DualMod**：避免引入过重结构即可在两个分支中实现语义引导；
- **跨域验证**：同时覆盖仿真与真实机器人，结论可信度较高；
- **关注推理效率**：在追求性能的同时兼顾实时性，对实际部署友好。

## 8. 不足与局限

- **信息有限**：当前材料仅含摘要与元数据，缺乏正文中关于：
  - 具体对比基线、benchmark 名称的细节；
  - 消融实验是否充分拆解流场、扩散、DualMod 各部分贡献；
  - 失败案例分析；
- **泛化范围未细化**：未明确说明是否在多机器人形态（不同机械臂、灵巧手、底盘等）上验证，泛化性结论的边界尚不清晰；
- **真实世界实验规模**：是否包含多次重复试验、不同光照/物体摆放等扰动下的鲁棒性测试，需进一步从正文确认；
- **算力与可复现性**：未披露训练算力与超参数细节，可能影响复现；
- **应用范围限制**：主要面向"复杂操控"任务，对于长时序、跨多步推理的任务，方法是否同样有效仍待验证。

（完）
