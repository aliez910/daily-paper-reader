---
title: "Bridge Policy: Visuomotor Policy Learning via Stochastic Optimal Control"
title_zh: Bridge Policy：基于随机最优控制的视觉运动策略学习
authors: "Zhaoyang Liu, Mokai Pan, Zhongyi Wang, Kaizhen Zhu, Haotao Lu, Jingya Wang, Ye Shi"
date: 2025-09-14
pdf: "https://openreview.net/pdf?id=jDkKquWRgd"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于扩散桥的端到端视觉运动策略学习用于模仿学习
tldr: 模仿学习中现有基于条件扩散的视觉运动策略在正向与反向过程中存在流形偏离和估计误差，BridgePolicy针对此问题提出基于随机最优控制的扩散桥方法。该方法将观测显式纳入正向过程，从观测分布中采样动作而无需条件注入，避免了流形偏差并提升了多模态动作分布的建模能力。实验验证了该方法在端到端视觉运动模仿学习中的有效性，对机器人操纵策略学习有直接贡献。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 基于条件扩散的视觉运动策略存在流形偏离与估计误差问题。
method: 提出基于随机最优控制的无条件生成式扩散桥策略，将观测嵌入正向过程。
result: 避免流形偏差，提升多模态动作分布建模与时序依赖捕获能力。
conclusion: 为端到端视觉运动模仿学习提供了一种新的扩散桥方法。
---

## Abstract
Imitation learning has been widely used in robotic learning, where policies are derived from expert demonstrations. Recent advances leverage generative models, such as diffusion and flow-based methods, to better capture multi-modal action distributions and temporal dependencies. However, these approaches typically impose conditioning during the forward and reverse process, which inevitably introduces manifold deviation and estimation error. In this work, we propose BridgePolicy, a condition-free generative visuomotor policy that explicitly incorporates observations into the forward process through a diffusion bridge formulation grounded in stochastic optimal control. By sampling actions from observation distributions instead of random noise, BridgePolicy reduces stochasticity and achieves more controllable policy behaviors. However, directly bridging observations to actions poses new challenges, as the action distribution may exhibit mismatched data shape, and the robot observations are inherently multi-modal. In contrast, the diffusion bridge can only connect one-to-one distributions with the same shape.  To address the challenges of aligning distributional endpoints and handling multi-modal robot observations, we design a semantic aligner for distribution shape alignment, and a modality fusion module for unifying robot states and visual inputs. Experiments across 52 tasks on 3 benchmarks and 4 real-world tasks demonstrate that BridgePolicy consistently outperforms state-of-the-art generative policies.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Bridge Policy: Visuomotor Policy Learning via Stochastic Optimal Control" based on the provided abstract and metadata. Let me organize the content according to the 8 required points.

Let me analyze what I have:
- Title: Bridge Policy: Visuomotor Policy Learning via Stochastic Optimal Control
- Authors: Zhaoyang Liu, Mokai Pan, Zhongyi Wang, Kaizhen Zhu, Haotao Lu, Jingya Wang, Ye Shi
- Date: 2025-09-14
- Source: ICLR-2026-Public
- Key idea: Diffusion bridge based visuomotor policy learning for imitation learning
- Motivation: Existing conditional diffusion-based visuomotor policies have manifold deviation and estimation errors in forward and reverse processes
- Method: Stochastic optimal control based unconditional generative diffusion bridge policy, embedding observations into forward process
- Results: Avoids manifold bias, improves multimodal action distribution modeling and temporal dependency capture
- Experiments: 52 tasks on 3 benchmarks and 4 real-world tasks, outperforms SOTA generative policies

Let me write a comprehensive summary in Chinese following the 8-point structure.
</think>
# Bridge Policy 论文总结

## 1. 核心问题与研究动机

- **背景**：模仿学习（Imitation Learning）是机器人学习中的主流范式，策略通常从专家示教中学习。近期工作广泛采用扩散模型（diffusion）和流模型（flow-based methods）等生成式方法来更好地捕捉多模态动作分布与时序依赖。
- **核心问题**：现有基于条件扩散（conditional diffusion）的视觉运动策略需要在正向与反向过程中施加条件（conditioning），这不可避免地带来两类问题：
  - **流形偏离（manifold deviation）**：条件注入导致生成过程偏离数据流形；
  - **估计误差（estimation error）**：在条件生成链路中累积，影响策略精度。
- **整体含义**：论文针对模仿学习中条件生成式策略的结构性缺陷，提出一种新的无条 件生成式策略框架，旨在从根源上避免流形偏离问题，提高多模态动作分布与时序依赖的建模能力。

## 2. 方法论

- **核心思想**：提出 **BridgePolicy**，一种**无条件的（condition-free）生成式视觉运动策略**。该方法将观测信息显式嵌入正向过程，借助**扩散桥（diffusion bridge）**构建从观测分布到动作分布的直接桥梁，从观测分布中采样动作而非从随机噪声生成。
  - 数学基础：**随机最优控制（Stochastic Optimal Control, SOC）**，为扩散桥提供理论支撑。
  - 关键优势：减少了采样随机性，实现更可控的策略行为。

- **关键技术与模块设计**：
  1. **分布端点对齐挑战**：扩散桥只能连接形状相同的"一对一"分布，但动作分布与观测分布存在形状不匹配问题。
     - 解决：设计 **语义对齐器（Semantic Aligner）**，用于分布形状对齐。
  2. **多模态观测融合挑战**：机器人观测天然具有多模态性（视觉 + 状态）。
     - 解决：设计 **模态融合模块（Modality Fusion Module）**，统一处理机器人状态与视觉输入。
  3. **正向过程**：将观测作为扩散桥的端点，动作作为另一端点，正向过程显式依赖于观测。
  4. **反向过程**：直接从观测分布中采样动作，无需额外条件注入。

- **算法流程（文字概述）**：
  1. 输入机器人多模态观测（视觉 + 状态）；
  2. 通过模态融合模块统一表征；
  3. 语义对齐器将动作分布与观测分布形状对齐；
  4. 基于 SOC 框架构建扩散桥，前向过程由观测驱动；
  5. 训练完成后，推理阶段直接从观测分布中采样得到动作。

## 3. 实验设计

- **Benchmark 与数据集**：
  - 涵盖 **3 个仿真基准**，共 **52 个任务**；
  - 额外包含 **4 个真实世界任务**（real-world tasks）。
- **对比方法**：与当前最优的**生成式策略（state-of-the-art generative policies）** 进行对比，覆盖扩散类与流模型类基线。
- **实验维度**：任务数量多（52 + 4），跨越仿真与真实世界，验证了方法的泛化能力与实用性。

## 4. 资源与算力

- **现状**：根据所提供的论文内容（摘要与元数据），**未明确提及**所使用的 GPU 型号、数量、训练时长等算力信息。
- 仅能推断为通用深度学习训练流程，具体算力配置需查阅正文与附录。

## 5. 实验数量与充分性

- **实验规模**：
  - 仿真：3 个基准、52 个任务；
  - 真实世界：4 个任务；
  - 总计 56 个任务场景。
- **对比维度**：与多种 SOTA 生成式策略进行对比。
- **充分性评估**：
  - 优点：任务数量丰富，仿真+真实结合，benchmark 覆盖较广，结论具有较强说服力；
  - 局限：仅从摘要层面无法判断是否包含**消融实验（ablation study）**、**不同噪声调度对比**、**超参数敏感性分析**等细分实验；摘要未详细说明实验公平性控制（如统一随机种子、硬件条件等）。

## 6. 主要结论与发现

- BridgePolicy 通过**无条件生成式扩散桥**避免了传统条件扩散策略的流形偏离与估计误差问题。
- 将观测显式纳入正向过程，**从观测分布采样动作**而非从随机噪声生成，显著**降低随机性、提升可控性**。
- 语义对齐器与模态融合模块有效解决了分布端点对齐与多模态融合两大核心挑战。
- 在 52 个仿真任务与 4 个真实任务上**一致优于**当前 SOTA 生成式策略，验证了方法的有效性与泛化性。
- 为端到端视觉运动模仿学习提供了一种**新的扩散桥范式**。

## 7. 优点与亮点

- **方法创新**：
  - 首次将**扩散桥**与**随机最优控制**引入视觉运动策略学习，提出 condition-free 生成式框架，从根源上规避条件注入带来的偏差问题；
  - 区别于主流"噪声→动作"的条件扩散范式，采用"观测→动作"的桥式生成，物理直觉更清晰。
- **模块设计**：
  - 语义对齐器针对性解决分布形状不匹配；
  - 模态融合模块统一处理视觉与状态信息，便于多模态融合。
- **实验规模**：56 个任务（含真实世界），覆盖广，对比充分。
- **应用价值**：对机器人操纵策略学习具有直接贡献，方法具有较好的可推广性。

## 8. 不足与局限

- **信息不足**：
  - 摘要未给出**算力与训练成本**信息，难以评估方法的实际部署门槛；
  - 摘要未提及**消融实验**，无法判断各模块（语义对齐器、模态融合、扩散桥）的具体贡献度。
- **方法局限**：
  - 扩散桥要求端点分布形状一致，依赖语义对齐器进行形状匹配；若观测与动作空间差异极大，对齐器设计难度增加；
  - 推理阶段仍依赖迭代采样过程，相对于直接回归策略可能在**推理延迟**上存在劣势，未在摘要中讨论实时性表现。
- **实验偏差风险**：
  - 仅在 3 个 benchmark + 4 个真实任务上验证，未涵盖更多样化的机器人形态与任务类型；
  - 真实任务数量偏少（仅 4 个），可能存在过拟合或环境特定性风险；
- **应用限制**：
  - 方法依赖于 SOC 框架的扩散桥假设，对观测噪声、延迟与缺失模态的鲁棒性尚未在摘要中讨论；
  - 多模态融合模块在视觉退化、遮挡等极端条件下的表现未知。

（完）
