---
title: "SAM2Act: Integrating Visual Foundation Model with A Memory Architecture for Robotic Manipulation"
title_zh: SAM2Act：集成视觉基础模型与记忆架构的机器人操纵
authors: "Haoquan Fang, Markus Grotz, Wilbert Pumacay, Yi Ru Wang, Dieter Fox, Ranjay Krishna, Jiafei Duan"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=anSWDvJm8v"
tags: ["query:rob-il"]
score: 9.0
evidence: 集成视觉基础模型与记忆架构实现端到端机器人操纵
tldr: "该论文针对机器人在复杂动态环境中的操作需求，提出了SAM2Act，一种多视角Transformer策略。它集成了SAM2视觉基础模型和多分辨率上采样，并引入记忆架构以处理空间记忆任务。在RLBench的18个任务上达到86.8%的平均成功率，显著优于现有方法，展示了强大的泛化能力。这项工作突出了视觉基础模型结合记忆在机器人操作中的潜力。"
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有机器人操纵方法在泛化和记忆依赖任务上表现不足。
method: 多视角Transformer策略，利用SAM2视觉基础模型及多分辨率上采样，并加入记忆模块。
result: "在RLBench 18个任务中达到86.8%的成功率，泛化性优异。"
conclusion: 视觉基础模型与记忆架构结合显著提升机器人操纵性能。
---

## Abstract
Robotic manipulation systems operating in diverse, dynamic environments must exhibit three critical abilities: multitask interaction, generalization to unseen scenarios, and spatial memory. While significant progress has been made in robotic manipulation, existing approaches often fall short in generalization to complex environmental variations and addressing memory-dependent tasks. To bridge this gap, we introduce **SAM2Act**, a multi-view robotic transformer-based policy that leverages multi-resolution upsampling with visual representations from large-scale foundation model. SAM2Act achieves a state-of-the-art average success rate of **86.8% across 18 tasks** in the RLBench benchmark, and demonstrates robust generalization on *The Colosseum* benchmark, with only a **4.3% performance gap** under diverse environmental perturbations. Building on this foundation, we propose **SAM2Act+**, a memory-based architecture inspired by SAM2, which incorporates a memory bank, an encoder, and an attention mechanism to enhance spatial memory. To address the need for evaluating memory-dependent tasks, we introduce ***MemoryBench***, a novel benchmark designed to assess spatial memory and action recall in robotic manipulation. SAM2Act+ achieves an average success rate of **94.3% on memory-based tasks** in *MemoryBench*, significantly outperforming existing approaches and pushing the boundaries of memory-based robotic systems.
Project page: [sam2act.github.io](https://sam2act.github.io/).

---

## 论文详细总结（自动生成）

# 论文结构总结

## 1. 核心问题与整体含义

- **研究动机**：现有机器人操纵方法在动态、复杂环境中的泛化能力不足，尤其对依赖空间记忆的任务表现薄弱。  
- **整体含义**：作者试图证明，将大规模视觉基础模型（SAM2）与显式记忆架构相结合，能够同时提升机器人在多任务学习、零样本泛化和记忆依赖任务上的性能，为构建更通用的操纵系统提供新思路。

## 2. 方法论

- **核心思想**：利用 SAM2 的视觉特征（多分辨率上采样）作为骨干，构建多视角 Transformer 策略，并进一步设计记忆模块以处理需要空间记忆的任务。  
- **关键技术细节**：
  - **SAM2Act**：基础版本，采用多视角输入，通过 Transformer 架构融合来自 SAM2 的多分辨率视觉表示，输出动作。
  - **SAM2Act+**：扩展版本，受 SAM2 的记忆机制启发，引入 **memory bank**（存储历史观测/特征的缓存）、**encoder**（对当前与历史信息进行编码）和 **attention 机制**（在记忆与当前特征之间建立关联），使模型能够主动回忆与利用过去状态。
- **算法流程**（文字说明）：
  1. 多视角图像经 SAM2 提取多分辨率特征；
  2. 特征经 Transformer 编码为联合表示；
  3. （SAM2Act+）联合表示与 memory bank 中的历史嵌入通过 attention 交互，更新记忆并输出增强后的特征；
  4. 最后通过策略头（如 MLP）生成动作。
- **公式或伪代码**：摘要中未提供具体公式。

## 3. 实验设计

- **数据集 / 场景**：
  - **RLBench**：18 个机器人操纵任务（涵盖多步操作、物体抓取、放置等）。
  - **The Colosseum**：包含多种环境扰动（光照、纹理、物体形状等）的泛化 benchmark。
  - **MemoryBench**：作者新提出的 benchmark，专门评估空间记忆与动作回忆能力（例如需要记住之前物体的位置或状态才能继续执行的任务）。
- **对比方法**：摘要未列出具体基线名称，仅提及“显著优于现有方法”。元数据中注明与“现有方法”对比，在 RLBench 达到 SOTA。
- **评估指标**：任务成功率（%）。

## 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量及训练时长。此信息在摘要与元数据中均未提及。

## 5. 实验数量与充分性

- **实验数量**：
  - RLBench 上评估 18 个任务（平均成功率）；
  - The Colosseum 上测试泛化性（报告性能差距）；
  - MemoryBench 上评估记忆任务（多个任务取平均）。
- **充分性判断**：
  - 覆盖了多任务、泛化、记忆三个核心能力，广度较好；
  - 但缺乏消融实验（例如移除记忆模块、不使用 SAM2 特征等）的详细结果，也未提供复现误差或多次运行的统计；
  - 仅在仿真环境中验证，未涉及真实机器人实验；
  - 对比方法的数量与具体结果未列出，难以评估比较的公平性。

## 6. 主要结论与发现

- **核心结论**：SAM2Act 在 RLBench 上达到 86.8% 平均成功率，在 The Colosseum 上仅下降 4.3%，说明 SAM2 视觉基础模型能显著提升泛化能力。
- **记忆增强有效性**：SAM2Act+ 在 MemoryBench 上达到 94.3% 平均成功率，大幅超越现有方法，表明显式记忆架构对空间记忆类任务至关重要。
- **总体发现**：大规模视觉基础模型与记忆机制集成是一种有效的机器人操纵范式，尤其适用于复杂、动态及需要历史信息的环境。

## 7. 优点

1. **方法创新**：结合 SAM2 的强视觉表征与多分辨率上采样，无需额外训练视觉部分，提升了零样本泛化性。
2. **记忆设计**：借鉴 SAM2 的 memory 机制，采用 attention 与 memory bank，增强了策略对时序/空间信息的利用。
3. **基准贡献**：提出 MemoryBench，填补了机器人记忆任务评估的空缺。
4. **实验结果**：在多个 benchmark 上达到 SOTA，且泛化差距小，体现了方法的鲁棒性。

## 8. 不足与局限

1. **计算资源缺失**：未报告训练效率与硬件成本，难以评估实际部署可行性。
2. **消融不充分**：未明确分析各组件（SAM2、记忆模块、多分辨率）的单独贡献。
3. **实验范围有限**：仅在仿真环境（RLBench 等）测试，缺乏真实机器人实验；MemoryBench 的任务设计覆盖面可能存在偏颇。
4. **对比不透明**：未列出详细对比方法及各自的成功率，不利于直接复现与验证。
5. **偏差风险**：评价指标可能未考虑任务难度差异；记忆任务的定义可能偏向于论文提出的方法。
6. **开放性**：SAM2Act+ 的记忆架构更新策略与注意力机制细节模糊，可能难以复现。

（完）
