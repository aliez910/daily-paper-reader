---
title: "Falcon: Fast Visuomotor Policies via Partial Denoising"
title_zh: Falcon：通过部分去噪实现快速视觉运动策略
authors: "Haojun Chen, Minghao Liu, Chengdong Ma, Xiaojian Ma, Zailin Ma, Huimin Wu, Yuanpei Chen, Yifan Zhong, Mingzhi Wang, Qing Li, Yaodong Yang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=fiv2M4P5vk"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过部分去噪加速视觉运动策略，实现实时决策
tldr: 针对扩散策略在视觉运动任务中采样步骤多、实时性差的问题，本文提出Falcon，利用动作序列的时序依赖性，复用历史部分去噪的动作而非从高斯噪声开始采样。该方法无需重新训练即可显著加速推理，在保持性能的同时实现了实时决策。实验证明了在模拟和真实机器人操作任务中的有效性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 扩散策略的多次采样步骤严重阻碍实时推理。
method: 提出部分去噪方法，重用历史部分去噪的动作以加速推断。
result: 在多种视觉运动任务中，Falcon在保持策略性能的前提下大幅提升推理速度。
conclusion: 动作间的时序依赖可用于加速扩散策略，适合实时控制场景。
---

## Abstract
Diffusion policies are widely adopted in complex visuomotor tasks for their ability to capture multimodal action distributions. However, the multiple sampling steps required for action generation significantly harm real-time inference efficiency, which limits their applicability in real-time decision-making scenarios. Existing acceleration techniques either require retraining or degrade performance under low sampling steps. Here we propose Falcon, which mitigates this speed-performance trade-off and achieves further acceleration. The core insight is that visuomotor tasks exhibit sequential dependencies between actions. Falcon leverages this by reusing partially denoised actions from historical information rather than sampling from Gaussian noise at each step. By integrating current observations, Falcon reduces sampling steps while preserving performance. Importantly, Falcon is a training-free algorithm that can be applied as a plug-in to further improve decision efficiency on top of existing acceleration techniques. We validated Falcon in 48 simulated environments and 2 real-world robot experiments. demonstrating a 2-7x speedup with negligible performance degradation, offering a promising direction for efficient visuomotor policy design.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：扩散策略（Diffusion Policy）在复杂视觉运动任务中因能捕获多峰动作分布而被广泛采用，但其动作生成需要多次采样步骤，导致推理延迟高，难以满足实时决策需求。
- **现有局限**：已有的加速方法要么需要重新训练模型（如蒸馏），要么在减少采样步数时性能明显下降，无法兼顾速度与性能。
- **本文目标**：设计一种无需重新训练、即插即用的加速方案，在保持策略性能的前提下大幅提升推理速度，使扩散策略能应用于实时控制场景。

## 2. 方法论：核心思想与关键技术细节

- **核心洞察**：视觉运动任务中的动作序列存在时序依赖性，即相邻时间步的动作高度相关，因此无需每次从纯高斯噪声开始完整去噪。
- **关键方法**：提出**部分去噪（Partial Denoising）** 技术，在每一步复用**历史信息中已部分去噪的动作**，而放弃从随机噪声重新采样；同时结合当前观测，只需执行较少的去噪步骤即可获得高质量动作。
- **算法流程**（文字说明）：
  1. 在初始时间步，从高斯噪声开始执行完整的多步去噪，生成初始动作序列。
  2. 从第二步开始，不再重新采样初始噪声，而是将上一步生成的**部分去噪后的动作**直接作为当前步去噪过程的初始状态。
  3. 利用当前观测对上一步的部分去噪动作进行条件调整，继续执行剩余的去噪步骤（步数远少于完整采样）。
  4. 输出当前动作，进入下一时间步，重复步骤2–3。
- **技术特点**：
  - **无训练**：不需要额外训练或修改原扩散策略模型，可直接作为插件使用。
  - **兼容性强**：可与现有采样加速技术（如DDIM、DPM-Solver等）叠加，进一步提升效率。

## 3. 实验设计

- **数据集与场景**：
  - **模拟环境**：共 **48 个模拟环境**，覆盖多种视觉运动任务（具体环境名称未在摘要中列出，但涵盖典型机器人操作场景）。
  - **真实机器人实验**：**2 个真实机器人操作任务**，验证方法在真实物理环境中的有效性。
- **基准（Benchmark）**：未明确指定单一标准基准，但通过对比不同采样步数下的性能与速度，以及与其他加速技术的组合来评估。
- **对比方法**：
  - 原始扩散策略（多步采样基线）。
  - 现有加速技术（如需要重新训练的方法或低步数采样方法，论文中提到“Existing acceleration techniques either require retraining or degrade performance under low sampling steps”）。
  - 同时将Falcon作为插件叠加于其他加速器之上进行对比。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量及具体训练/推理时长等算力信息。
- 仅可推断：由于方法无训练，推理时依赖预训练的扩散策略模型，对算力需求可能与原模型相当；但加速后推理所需采样步数大幅减少，因此实际运行时算力消耗更低。

## 5. 实验数量与充分性

- **实验数量**：
  - 模拟：48 个环境，涵盖面较广，具有较好的多样性。
  - 真实：2 个真实机器人实验，提供物理世界验证。
  - 此外，论文还评估了Falcon与多种加速方法的组合，隐含进行了消融与对比实验。
- **充分性与公平性**：
  - 实验数量在模拟环境上较为充分，真实环境偏少但常见于该领域工作。
  - 无训练插件模式使得对比公平（其他方法无需额外训练，直接比较推理速度与性能）。
  - 未提及超参数敏感性分析或统计显著性检验，客观性尚可但细节不足。

## 6. 主要结论与发现

- Falcon 在**保持原有策略性能（性能下降可忽略）** 的前提下，实现了 **2–7 倍的推理速度提升**。
- 通过复用历史部分去噪动作并利用时序依赖，成功打破了速度与性能的权衡。
- 作为无训练插件，Falcon 可以灵活地与现有加速技术结合，进一步提升效率。
- 验证了动作序列时序依赖性可用于加速扩散策略，为实时视觉运动策略设计提供了新方向。

## 7. 优点

- **概念简单有效**：核心思想直观，仅利用时序依赖性进行部分去噪，实现无需重新训练的推理加速。
- **即插即用**：可直接应用于预训练好的扩散策略模型，无需修改训练流程。
- **兼容性强**：可与多种现有加速方法叠加，进一步提升效率。
- **速度提升显著**：在大量模拟和真实任务中获得2–7倍加速，且性能几乎无损。
- **实验覆盖较广**：48个模拟环境加真实机器人验证，增强结果可信度。

## 8. 不足与局限

- **实验细节缺失**：未提供具体任务列表、超参数设置、消融实验设计细节及统计量，复现与深入分析较困难。
- **真实实验较少**：仅2个真实任务，可能不足以推广至各种真实操作场景；物理世界中的噪声与累积误差未充分讨论。
- **依赖动作序列长度**：部分去噪的有效性依赖动作间的时序相关性，若动作序列极短或动作变化剧烈，复用历史信息可能引入偏差。
- **无训练特性对模型可能有前提条件**：假设扩散策略已经很好且动作序列平滑，若模型本身无法捕获充分时序依赖，加速效果可能受限。
- **没有与最先进蒸馏方法直接对比**：仅提到现有方法需重新训练，但未定量对比蒸馏后的模型性能与速度。
- **算力资源未报告**：不利于评估实际部署成本。

（完）
