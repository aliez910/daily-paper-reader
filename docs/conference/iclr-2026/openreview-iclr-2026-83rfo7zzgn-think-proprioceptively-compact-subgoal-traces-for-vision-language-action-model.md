---
title: "Think Proprioceptively: Compact Subgoal Traces for Vision-Language-Action Model"
title_zh: 以本体感思考：面向视觉-语言-动作模型的紧凑子目标轨迹
authors: "Fangyuan Wang, Peng ZHOU, Shipeng Lyu, Gu Gong, Weiwei Lin, Anqing Duan, David Navarro-Alarcon, Guodong Guo"
date: 2025-09-10
pdf: "https://openreview.net/pdf?id=83RFO7Zzgn"
tags: ["query:rob-il"]
score: 8.0
evidence: 结合本体感推理的视觉-语言-动作模型
tldr: 现有VLA模型将本体感视为被动输入，多模态特征处理与机器人物理构型脱节，SubgoalVLA针对此问题提出思考本体感的范式。在该框架中，本体感状态作为交叉注意力查询以选择任务相关特征，子目标轨迹编码在本体感空间中以实现具身锚定。该工作将本体感推理融入VLA架构，为复杂操纵任务中更可靠的视觉-动作映射提供了新思路。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有VLA模型将本体感视为被动输入，多模态特征与机器人具身构型脱节。
method: 提出思考本体感范式，将本体感状态作为交叉注意力查询，子目标轨迹编码于本体感空间。
result: 实现更具身化的VLA模型，强化视觉到动作的映射与推理。
conclusion: 将本体感从被动输入提升为VLA模型中的主动推理组件。
---

## Abstract
Vision-language-action (VLA) models translate visual observations and language instructions to robot actions, yet current architectures regard proprioception as a passive input rather than an active reasoning component. Without proprioceptive guidance, VLA models process multimodal features in isolation from the robot’s physical configuration, and hierarchical approaches often encode subgoals in high-dimensional visual or textual spaces that are ungrounded in the robot’s embodiment. We present SubgoalVLA, a framework built on the \textit{think proprioceptively} paradigm that redefines how multimodal information is processed. SubgoalVLA leverages proprioception in two ways. First, proprioceptive states serve as cross-attention queries to select vision-language features, enabling configuration-aware feature extraction. Second, subgoals are encoded as compact sequences of joint configurations that eliminate the need for cross-modal translation. Through a two-stage training protocol that begins with supervised learning on ground-truth subgoals and then fine-tunes with self-predicted subgoals, we mitigate distribution shift between training and inference. On the CALVIN benchmark, SubgoalVLA achieves state-of-the-art performance with an average task completion length of 3.32, demonstrating that proprioceptive reasoning provides the critical bridge between high-level task understanding and embodied control.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Think Proprioceptively: Compact Subgoal Traces for Vision-Language-Action Model" (SubgoalVLA). I have the abstract and metadata, but the PDF couldn't be fully extracted due to CAPTCHA. I'll work with the available information: the abstract, metadata, and my knowledge of the VLA model field to provide a comprehensive summary while being honest about limitations.

Let me organize the summary according to the 8 requested points.
</think>
# 论文总结：SubgoalVLA —— 以本体感思考的紧凑子目标轨迹

## 1. 核心问题与研究动机

- **研究背景**：视觉-语言-动作（Vision-Language-Action, VLA）模型是当前机器人操控领域的重要范式，旨在将视觉观测与语言指令映射为机器人的动作输出，代表工作如 RT-2、OpenVLA 等。
- **现有方法的不足**：
  - 现有 VLA 模型通常将**本体感觉（proprioception，如关节角、末端位姿、速度等）仅作为被动输入**拼接进 token，未让其参与特征选择与推理过程。
  - 现有分层/层级方法通常将**子目标（subgoal）编码在高维视觉空间或语言空间**，与机器人的物理构型（embodiment）解耦，缺乏具身锚定（embodiment grounding）。
- **核心问题**：如何让本体感信息在 VLA 中发挥主动推理作用，使多模态特征处理与机器人构型紧密耦合，从而提升复杂操控任务中的视觉-动作映射可靠性。

## 2. 方法论

### 2.1 核心思想：Think Proprioceptively 范式
论文提出 **SubgoalVLA** 框架，主张在两个层面让本体感参与推理：
1. **本体感作为特征选择器**：以本体感状态为查询（query），通过交叉注意力从视觉-语言特征中选取任务相关信息。
2. **本体感空间中的子目标编码**：将子目标表示为紧凑的关节构型序列（joint configurations），而非高层视觉/语言描述。

### 2.2 关键技术细节
- **构型感知的特征提取（Configuration-Aware Feature Extraction）**：
  - 输入包含视觉观测、语言指令和本体感状态（关节角等）。
  - 本体感状态向量作为 cross-attention 的 query，视觉-语言特征作为 key/value，筛选与当前物理构型相关的多模态特征。
- **紧凑子目标轨迹（Compact Subgoal Traces）**：
  - 子目标由末端位姿或关键关节构型序列组成，可直接被机器人执行，无需跨模态翻译。
  - 与图像子目标或文本子目标相比，维度更低、与执行器天然对齐。
- **两阶段训练协议（Two-Stage Training）**：
  1. **阶段一（监督学习）**：使用真实标注的子目标（ground-truth subgoals）进行监督训练，使模型学会生成具身锚定的子目标。
  2. **阶段二（自预测微调）**：使用模型自身预测的子目标进行微调，缩小训练-推理分布偏移（distribution shift），提升鲁棒性。
- **算法流程（文字描述）**：
  视觉+语言 → 多模态编码 → 以本体感为 query 做 cross-attention 筛选 → 构型感知特征 → 子目标解码器输出关节构型序列 → 动作解码器生成具体动作。

## 3. 实验设计

- **基准测试**：**CALVIN** benchmark（用于长视野、语言条件下的桌面操控任务，是 VLA 分层方法常用评测基准）。
- **评测指标**：**平均任务完成长度（Average Task Completion Length）**，数值越高表示连续成功完成的任务数越多。
- **主要结果**：在 CALVIN 上达到 **SOTA，平均任务完成长度 3.32**。
- **对比基线**：依据摘要和领域常规，文中应与 RT-1、RT-2、HULC、GR-1、Pi-0、OpenVLA 等通用 VLA 模型，以及 HIERARCHICAL/HiP 等分层 VLA 方法进行比较（具体基线以论文正文为准，PDF 提取受 CAPTCHA 限制未能获取完整正文）。

> 注：由于原始 PDF 文本受 OpenReview 验证码保护未能完整提取，上述对比基线来自摘要与领域常识，具体细节以原论文为准。

## 4. 资源与算力

- 原 PDF 受 OpenReview CAPTCHA 限制，**未能从提取文本中获取 GPU 型号、数量、训练时长等具体算力信息**。
- 依据领域经验，CALVIN 基准上的 VLA 训练通常需要 4–8 张 A100/H100 级别 GPU、数小时到数天不等，但**具体数值需以论文正文或附录为准**。

## 5. 实验数量与充分性

- **已知实验**：CALVIN 基准上的主要结果，以及 SOTA 对比。
- **可推测实验**（基于方法设计）：
  - 消融实验：是否使用 proprioception-as-query、是否使用本体感空间子目标、两阶段训练各组件的贡献。
  - 跨场景/跨机器人迁移实验（若涉及）。
- **充分性评估**：
  - 优点：在 CALVIN 单一基准上达到 SOTA，并提出明确的两阶段训练策略缓解分布偏移。
  - 局限：单一基准可能不足以全面验证泛化能力；缺乏真实机器人实机实验的覆盖度（需以论文正文确认）。

## 6. 主要结论与发现

- **结论一**：将本体感从被动输入提升为**主动推理组件**（作为 cross-attention 查询），可显著提升 VLA 对多模态特征的构型相关性筛选能力。
- **结论二**：将子目标编码在**本体感空间**（紧凑关节构型序列）比高维视觉/语言子目标更具具身一致性，无需跨模态翻译即可直接执行。
- **结论三**：**两阶段训练**（真实子目标监督 + 自预测子目标微调）能有效缓解训练-推理分布偏移。
- **总体发现**：本体感推理是从高层任务理解到具身控制之间的**关键桥梁**，在 CALVIN 上达到 3.32 的平均任务完成长度，验证了"think proprioceptively"范式的有效性。

## 7. 优点

- **范式创新**：明确提出"think proprioceptively"理念，将本体感从被动输入升级为主动推理组件，思路清晰、动机充分。
- **设计简洁**：子目标采用紧凑的关节构型序列，避免高维视觉/语言子目标带来的歧义和翻译开销。
- **缓解分布偏移**：两阶段训练协议（监督 + 自预测微调）是对分层 RL/VLA 经典痛点的针对性解决方案。
- **实验结果强**：在广泛使用的 CALVIN 基准上取得 SOTA，证据有力。
- **可解释性**：本体感查询使得特征选择过程更易追溯和理解。

## 8. 不足与局限

- **PDF 提取受限**：受 OpenReview CAPTCHA 限制，未能获取完整正文细节（如完整基线对比、消融实验设置、算力配置等），上述部分内容基于摘要与领域知识推断，存在不确定性。
- **基准单一**：主要在 CALVIN 仿真基准上验证，**未明确提及真实机器人实机实验**（若有需以正文为准），泛化到真实世界的可靠性有待进一步验证。
- **构型依赖性**：方法高度依赖本体感空间作为子目标表示，**对不同机器人构型的迁移性**（如从单臂到双臂、从固定基座到移动基座）需要额外验证。
- **子目标粒度选择**：紧凑子目标序列的步长与粒度选择可能对性能有较大影响，文中未必给出系统性分析。
- **与最新 SOTA 对比的充分性**：摘要中未明确列出全部对比方法，需查阅正文以确认比较的公平性与全面性。
- **应用范围限制**：论文聚焦桌面操控类任务，对更复杂的长视野任务（如移动操作、多阶段装配）的扩展性未在摘要中体现。

（完）
