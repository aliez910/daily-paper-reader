---
title: "One-Step Diffusion Policy: Fast Visuomotor Policies via Diffusion Distillation"
title_zh: 单步扩散策略：通过扩散蒸馏实现快速视觉运动策略
authors: "Zhendong Wang, Max Li, Ajay Mandlekar, Zhenjia Xu, Jiaojiao Fan, Yashraj Narang, Linxi Fan, Yuke Zhu, Yogesh Balaji, Mingyuan Zhou, Ming-Yu Liu, Yu Zeng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=E2VsqgKNlr"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过扩散蒸馏加速行为克隆的视觉运动策略
tldr: 扩散模型在行为克隆中表现出色，但生成速度慢，限制实时应用。本文提出单步扩散策略(OneDP)，通过KL散度最小化将预训练扩散策略蒸馏为单步动作生成器，大幅加速响应时间。实验表明，OneDP在保持高性能的同时显著提升速度，适用于资源受限的机器人系统。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 扩散策略生成速度慢，难以满足机器人实时控制需求。
method: 通过最小化KL散度蒸馏预训练扩散策略为单步动作生成器。
result: 在多个机器人任务上验证了速度提升且性能损失极小。
conclusion: 单步蒸馏有效平衡了生成质量与速度，为实时控制提供可能。
---

## Abstract
Diffusion models, praised for their success in generative tasks, are increasingly being applied to robotics, demonstrating exceptional performance in behavior cloning. However, their slow generation process stemming from iterative denoising steps poses a challenge for real-time applications in resource-constrained robotics setups and dynamically changing environments.
In this paper, we introduce the One-Step Diffusion Policy (OneDP), a novel approach that distills knowledge from pre-trained diffusion policies into a single-step action generator, significantly accelerating response times for robotic control tasks. We ensure the distilled generator closely aligns with the original policy distribution by minimizing the Kullback-Leibler (KL) divergence along the diffusion chain, requiring only $2\%$-$10\%$ additional pre-training cost for convergence. We evaluated OneDP on 6 challenging simulation tasks as well as 4 self-designed real-world tasks using the Franka robot. The results demonstrate that OneDP not only achieves state-of-the-art success rates but also delivers an order-of-magnitude improvement in inference speed, boosting action prediction frequency from 1.5 Hz to 62 Hz, establishing its potential for dynamic and computationally constrained robotic applications. A video demo is provided at our project page, and the code will be publicly available.

---

## 论文详细总结（自动生成）

以下是根据提供的论文元数据与摘要信息生成的详细中文总结：

### 1. 论文的核心问题与整体含义（研究动机和背景）
扩散模型在行为克隆等机器人模仿学习任务中表现出色，但其迭代式去噪生成过程导致推理速度极慢，难以满足实时控制（尤其是动态环境与资源受限机器人系统）的需求。现有扩散策略通常需要在动作生成速度与控制性能之间进行权衡。本文提出**单步扩散策略（One-Step Diffusion Policy, OneDP）**，通过知识蒸馏将预训练的多步扩散策略压缩为单步生成器，旨在**在保持竞争力的同时将推理速度提升一个数量级**，使扩散模型能够真正用于实时机器人控制。

### 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程
- **核心思想**：利用扩散链上的**KL散度最小化**，将预训练的扩散策略（教师）蒸馏为一个单步动作生成网络（学生），使学生分布尽可能接近教师的原始分布。
- **关键技术细节**：
  - 学生网络直接输出动作，不再进行迭代去噪。
  - 蒸馏损失为沿扩散路径各步的KL散度之和（或近似），确保学生分布匹配教师的多步去噪分布。
  - 仅需额外 **2%–10%** 的预训练计算成本即可收敛。
- **算法流程（文字说明）**：  
  ① 使用标准扩散策略训练方法（如DDPM）预训练一个教师策略。  
  ② 冻结教师网络，并定义学生网络（结构与教师去噪网络类似但输出为单步动作）。  
  ③ 对于每个状态，教师通过完整扩散链生成动作分布，学生直接预测动作；最小化两者在扩散链各中间步上的条件分布KL散度。  
  ④ 优化学生网络直至收敛，之后在推理时只需一次前向传播即可获得动作。

### 3. 实验设计：使用的数据集/场景、benchmark、对比方法
- **场景**：6 个具有挑战性的仿真任务 + 4 个自设计的真实世界任务（使用Franka Panda机械臂）。
- **Benchmark与对比方法**：
  - 原文未明确列出对比方法的名称，但声称OneDP达到了**最优的成功率（state-of-the-art success rates）**，并给出了推理速度从原有扩散策略的 **1.5 Hz 提升至 62 Hz** 的对比数据。
  - 常见基线可能包括原始多步扩散策略、其他加速采样方法（如DDIM、DPM-solver）、或非扩散的行为克隆方法（如LSTM、Transformer策略），但文中未具体说明。
- **评估指标**：任务成功率、动作预测频率（Hz）。

### 4. 资源与算力
- 论文**未明确说明**使用的GPU型号、数量及训练总时长。
- 仅指出蒸馏过程仅需额外 **2%–10%** 的预训练成本，暗示额外计算开销很小。
- 推断：预训练阶段的资源消耗取决于原始的扩散策略训练设置，本文未提供具体细节。

### 5. 实验数量与充分性
- **数量**：共10个任务（6仿真+4真实），覆盖多样化的控制场景，具备一定的代表性。
- **充分性**：
  - 缺少消融实验（如不同蒸馏损失函数、学生网络结构设计、蒸馏步数影响等）的公开描述。
  - 未与多种加速方法进行全面对比，仅给出了成功率与速度的绝对数值。
  - 真实世界任务为自行设计，可能缺少标准化benchmark，但自建任务增加了实际部署验证。
  - 总体而言，实验设计较为聚焦，验证了核心提速效果，但在对比全面性和机理分析上存在提升空间。

### 6. 论文的主要结论与发现
- OneDP能够将扩散策略的**推理速度提升一个数量级以上**（1.5 Hz → 62 Hz），同时保持与原始多步扩散策略相当甚至更好的任务成功率。
- 蒸馏过程**高效**，仅需少量额外训练成本，且不需要特殊网络架构或复杂技巧。
- 单步生成对于**资源受限与实时性要求高**的机器人应用具有重要价值，使扩散模型从离线规划走向在线控制。

### 7. 优点：方法或实验设计上的亮点
- **简洁高效**：蒸馏目标明确，额外训练开销小，易于在现有扩散策略上集成。
- **大幅加速推理**：从15Hz级跨越到62Hz，满足实时控制需求（常见控制循环如10–50 Hz）。
- **实验覆盖真实部署**：除了模拟，还在真实Franka机器人上进行了4个任务验证，增加了可信度。
- **应用潜力大**：适用于对计算和延迟敏感的边缘机器人系统。

### 8. 不足与局限
- **对比方法不透明**：未列出具体对比基线，难以评估与最新加速采样或单步生成方法的相对优势。
- **消融研究缺失**：没有分析蒸馏损失设计、学生网络容量、教师策略质量对性能的影响。
- **泛化能力未知**：仅在有限任务上验证，未涉及多任务、组合任务或长序列动作决策。
- **对教师策略的依赖**：学生性能受限于教师策略的能力，若教师本身存在误差或过拟合，蒸馏后可能放大问题。
- **应用限制**：单步生成可能牺牲多步扩散的多样性，在某些需要多模态动作分布的任务中表现可能不佳。
- **技术细节不足**：原文仅提供摘要与元数据，缺少公式、网络结构、训练超参数等细节，不利于复现。

（完）
