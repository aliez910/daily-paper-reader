---
title: "Chain-of-Action: Trajectory Autoregressive Modeling for Robotic Manipulation"
title_zh: 动作链：面向机器人操纵的轨迹自回归建模
authors: "Wenbo Zhang, Tianrun Hu, Hanbo Zhang, Yanyuan Qiao, Yuchu Qin, Yang Li, Jiajun Liu, Tao Kong, Lingqiao Liu, Xiao Ma"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=hiiaHn3pWd"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操纵的视觉运动策略新范式，轨迹自回归建模
tldr: 本文针对现有视觉运动策略仅做前向逐步动作预测、缺乏全局任务一致性约束的局限，提出Chain-of-Action（CoA）轨迹自回归范式，将整条轨迹的生成建模为以任务目标为关键帧的动作级Chain-of-Thought过程。该方法先输出编码任务目标的稳定关键帧动作，再以自回归方式生成后续动作，从而实现从全局到局部结构的强约束。实验表明，CoA在多个机器人操纵基准上相比前向逐步预测基线获得更优的精度和长时序表现。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有视觉运动策略采用逐步前向预测方式，难以在长时序任务中保持全局目标一致性。
method: 提出Chain-of-Action，将整条轨迹生成统一在自回归结构中，先输出关键帧动作再逐token生成后续动作，实现动作级思维链。
result: 在机器人操纵基准上优于逐步前向预测基线，表现出更强的长时序规划与执行一致性。
conclusion: 全局到局部的反向推理为视觉运动策略提供了更稳定的目标约束范式。
---

## Abstract
We present Chain-of-Action (CoA), a novel visuomotor policy paradigm built upon Trajectory Autoregressive Modeling. Unlike conventional approaches that predict next step action(s) forward, CoA generates an entire trajectory by explicit backward reasoning with task-specific goals through an action-level Chain-of-Thought (CoT) process. This process is unified within a single autoregressive structure: (1) the first token corresponds to a stable keyframe action that encodes the task-specific goals;  and (2) subsequent action tokens are generated autoregressively, conditioned on the initial keyframe and previously predicted actions. This backward action reasoning enforces a global-to-local structure, allowing each local action to be tightly constrained by the final goal. To further realize the action reasoning structure, CoA incorporates four complementary designs: continuous action token representation; dynamic stopping for variable-length trajectory generation; reverse temporal ensemble; and multi-token prediction to balance action chunk modeling  with global structure. As a result, CoA gives strong spatial generalization capabilities while preserving the flexibility and simplicity of a visuomotor policy. Empirically, we observe that CoA outperforms representative imitation learning algorithms such as ACT and Diffusion Policy across 60 RLBench tasks and 8 real-world tasks.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Chain-of-Action: Trajectory Autoregressive Modeling for Robotic Manipulation" based on the provided metadata and abstract. Let me organize the response according to the 8 required sections.
</think>
# 论文总结：Chain-of-Action（动作链）

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有视觉运动策略（visuomotor policy）通常采用"逐步前向预测"的方式，即在每个时间步基于当前观测预测下一动作。这种方式在长时序任务中容易出现**全局目标不一致**的问题——模型容易"走到一半"丢失任务目标，难以维持从初始状态到目标状态的稳定轨迹。
- **研究动机**：受大语言模型中 Chain-of-Thought（思维链）推理范式的启发，作者希望将"先明确目标、再逐步推理"的思想迁移到机器人动作生成中，从而在长时序操控任务中同时获得**全局目标一致性**与**局部动作灵活性**。
- **整体含义**：提出一种"轨迹自回归"（Trajectory Autoregressive）的新范式 Chain-of-Action（CoA），让策略先生成"目标级关键帧动作"，再以自回归方式反向生成完整轨迹，从根本上将动作规划约束在最终目标之下。

## 2. 方法论：核心思想与关键技术细节

### 核心思想
- 将**整条动作轨迹的生成**视为一个自回归过程，第一步先输出编码任务目标的"关键帧动作"，之后逐步生成后续动作 token。
- 形成"**全局 → 局部**"的反向推理结构（backward reasoning），让每个局部动作都被最终目标强约束。

### 关键技术组件（四大设计）
1. **连续动作 token 表示（Continuous action token representation）**：
   - 不同于语言模型中离散的词 token，CoA 直接在连续空间中表示动作 token，使模型可端到端回归连续控制信号。
2. **动态停止（Dynamic stopping）**：
   - 支持**变长轨迹**生成，模型可自主决定何时结束轨迹生成，提升对不同任务时长/复杂度的适应性。
3. **反向时间集成（Reverse temporal ensemble）**：
   - 在推理时对多次反向生成的轨迹进行时间维度上的集成，提升鲁棒性。
4. **多 token 预测（Multi-token prediction）**：
   - 在自回归过程中同时预测多个未来 token，以**平衡"动作块建模"（action chunk）与"全局结构"**——既保证轨迹整体性，又保留 chunk 级的执行效率。

### 流程概述
1. 编码任务目标与当前观测，生成初始**关键帧动作 token**（编码任务最终目标）。
2. 以关键帧为锚点，自回归生成后续动作 token，每步条件依赖于：初始关键帧 + 历史已生成动作。
3. 训练目标：让模型学会同时预测关键帧 + 后续序列。
4. 推理时：可结合反向时间集成与多 token 预测提升稳定性与执行效率。

## 3. 实验设计

### 数据集 / 场景
- **仿真基准**：**RLBench**（共 **60 个任务**），是机器人模仿学习中常用的仿真 benchmark。
- **真实世界任务**：**8 个真实机器人操控任务**（real-world tasks）。

### 对比方法
- 主要对比的代表性模仿学习算法：
  - **ACT**（Action Chunking Transformer）
  - **Diffusion Policy**（扩散策略）
- 评价方向侧重：**空间泛化能力**、**长时序表现**、**精度**。

### 实验维度
- 仿真 RLBench 60 任务上的整体精度对比。
- 真实世界 8 任务上的迁移与执行表现。
- 由于摘要中未详细列出消融细节，推测还包含针对四大设计（连续 token、动态停止、反向时间集成、多 token 预测）的消融实验。

## 4. 资源与算力

- **论文提供的元数据与摘要中未明确说明**所使用的 GPU 型号、数量、训练时长或算力消耗。
- 这是一项不足之处：算力透明度缺失，使读者难以评估方法的**训练成本与可复现性**。

## 5. 实验数量与充分性

- **实验规模**：
  - 仿真：**60 个 RLBench 任务**，覆盖较广。
  - 真实：**8 个真实世界任务**，具备一定的现实迁移验证。
- **对比基线**：覆盖当前两类主流模仿学习方法（Transformer-based ACT、Diffusion-based Diffusion Policy），具有代表性。
- **充分性评估**：
  - 优点：任务数量多，对比基线强，覆盖仿真+真实两层验证。
  - 不足：摘要与元数据中未充分披露**消融实验数量**、**每个任务的试验次数/seed 数**、**统计显著性检验**等信息；真实任务仅 8 个，样本规模相对有限。

## 6. 主要结论与发现

- CoA **在 60 个 RLBench 仿真任务和 8 个真实世界任务上均优于 ACT 与 Diffusion Policy**。
- "**全局到局部的反向推理**"为视觉运动策略提供了**更稳定的目标约束**，尤其在**长时序任务**中优势更明显。
- 同时具备较强的**空间泛化能力**，且不牺牲 visuomotor policy 的**灵活性与简洁性**。
- 验证了"动作级 Chain-of-Thought"在机器人操控中的可行性——从大模型推理范式迁移到连续控制生成是有效的。

## 7. 优点（亮点）

- **范式创新**：首次系统性地将 Chain-of-Thought 思想引入机器人动作轨迹生成，提出"轨迹自回归"这一新范式，思路新颖、概念清晰。
- **统一的自回归结构**：将关键帧与后续动作统一在单一自回归框架下，避免了多阶段 pipeline 的复杂设计。
- **四大互补设计**：连续 token、动态停止、反向时间集成、多 token 预测，形成从表示、长度、集成、块建模的完整闭环。
- **实验覆盖面较广**：60 仿真 + 8 真实任务，基线选择具有代表性。
- **兼顾全局与局部**：通过关键帧锚定全局目标，又通过动作 chunk 保留局部执行效率。

## 8. 不足与局限

- **算力信息缺失**：未公开训练资源（GPU 型号/数量/时长），影响可复现性评估。
- **消融与统计细节不足**：从摘要层级无法判断消融实验的完整度、是否做了显著性检验、每个任务跑了多少 episode。
- **真实实验规模有限**：仅 8 个真实任务，相对仿真规模较小，真实世界泛化结论需更广泛验证。
- **依赖任务目标信息**：CoA 的关键帧生成需要任务级目标（goal）信息，在目标获取困难或完全无目标设定的场景下适用性受限。
- **与扩散模型的深度对比不足**：仅与 Diffusion Policy 对比，未与近期的更多先进策略（如基于视频预测的策略、3D 扩散策略等）进行对比。
- **失败模式与安全性分析缺失**：未讨论在动态环境、干扰、物体位姿大偏移等场景下的鲁棒性边界。
- **"动作级 CoT"与"语言级 CoT"的本质差异未深入讨论**：连续控制信号与离散语言推理之间的可类比性需要更深入的理论分析。

（完）
