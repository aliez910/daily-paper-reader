---
title: "CogVLA: Cognition-Aligned Vision-Language-Action Models via Instruction-Driven Routing & Sparsification"
title_zh: CogVLA：通过指令驱动路由与稀疏化实现的认知对齐视觉-语言-动作模型
authors: "Wei Li, Renshan Zhang, Rui Shao, Jie He, Liqiang Nie"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=Fg9HufTI0K"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向端到端感知到控制的视觉-语言-动作框架
tldr: 现有VLA模型依赖大量后训练，计算开销高且难以扩展。CogVLA提出认知对齐的视觉-语言-动作框架，通过指令驱动的路由与稀疏化在三种模态间协同剪枝，提升了从感知到控制的端到端一致性。该方法在机器人操作任务中显著降低计算成本并保持性能，为可扩展的通用VLA部署提供了有效方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型后训练开销大、跨模态语义耦合被忽视，难以高效部署。
method: 提出认知对齐的VLA框架，采用指令驱动的路由与稀疏化策略。
result: 在保持性能的同时显著降低计算开销并提升端到端一致性。
conclusion: 为高效可扩展的视觉-语言-动作模型部署提供了统一方案。
---

## Abstract
Recent Vision-Language-Action (VLA) models built on pre-trained Vision-Language Models (VLMs) require extensive post-training, resulting in high computational overhead that limits scalability and deployment. Existing sparsification strategies—such as Mixture-of-Depths, layer skipping, and early exit—fall short by neglecting the semantic coupling across vision-language-action modalities, and focusing narrowly on intra-LLM computation while overlooking end-to-end coherence from perception to control. To address these challenges, we propose **CogVLA**, a Cognition-Aligned Vision-Language-Action framework that leverages instruction-driven routing and sparsification to improve both efficiency and performance. CogVLA draws inspiration from human multimodal coordination and introduces a 3-stage progressive architecture. 1) **Encoder-FiLM based Aggregation Routing (EFA-Routing)** injects instruction information into the vision encoder to selectively aggregate and compress dual-stream visual tokens, forming a instruction-aware latent representation. 2) Building upon this compact visual encoding, **LLM-FiLM based Pruning Routing (LFP-Routing)** introduces action intent into the language model by pruning instruction-irrelevant visually grounded tokens, thereby achieving token-level sparsity. 3) To ensure that compressed perception inputs can still support accurate and coherent action generation, we introduce **V‑L‑A Coupled Attention (CAtten)**, which combines causal vision-language attention with bidirectional action parallel decoding.
Extensive experiments on the LIBERO benchmark and real-world robotic tasks demonstrate that CogVLA achieves state-of-the-art performance with success rates of 97.4\% and 70.0\%, respectively, while reducing training costs by 2.5$\times$ and decreasing inference latency by 2.8$\times$ compared to OpenVLA.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "CogVLA: Cognition-Aligned Vision-Language-Action Models via Instruction-Driven Routing & Sparsification". The PDF couldn't be extracted due to CAPTCHA, but I have the metadata and abstract which provides substantial information. Let me organize the summary based on the available information from the metadata and abstract, while being honest about what is and isn't directly accessible from the full paper.

Let me structure this according to the 8 requested points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I need to note that the full PDF wasn't accessible, so some details (especially around specific compute resources) may need to be inferred or noted as unclear.
</think>
# CogVLA 论文总结

> **说明**：由于原 PDF 链接在抓取时触发了 Cloudflare 验证（"Verifying your browser"），未能获取论文正文细节。以下总结基于元数据中提供的标题、摘要（Abstract）、以及结构化标签信息综合整理。涉及具体算力、训练细节、消融设置等正文内容可能与最终发表版本存在差异。

---

## 1. 核心问题与整体含义（研究动机与背景）

- **背景**：近年来，视觉-语言-动作模型（Vision-Language-Action, VLA）依托大规模预训练的视觉-语言模型（VLM），在机器人操控任务中表现突出。然而，这类模型需要大量后训练，计算开销极高，限制了可扩展性与实际部署。
- **现有方案的不足**：
  - 现有稀疏化方法（如 **Mixture-of-Depths**、**层跳过（Layer Skipping）**、**提前退出（Early Exit）**）大多只关注 LLM 内部的计算压缩，**忽视了视觉-语言-动作三种模态之间的语义耦合**。
  - 缺乏从感知到控制的**端到端一致性**设计。
- **核心问题**：如何在跨模态协同的前提下，同时降低训练与推理成本并保持/提升任务性能？

---

## 2. 方法论：核心思想与关键技术

### 2.1 总体框架：CogVLA
- **CogVLA（Cognition-Aligned VLA）**：受人类多模态协同机制启发，提出**认知对齐**的 VLA 框架，核心手段是**指令驱动的路由与稀疏化（Instruction-Driven Routing & Sparsification）**。
- 采用 **3 阶段渐进式架构**：

#### 阶段 1：Encoder-FiLM based Aggregation Routing（EFA-Routing）
- **位置**：视觉编码器端。
- **做法**：通过 **FiLM（Feature-wise Linear Modulation）** 将语言指令信息注入到视觉编码器。
- **效果**：选择性聚合并压缩**双流视觉 token**（dual-stream visual tokens），生成**指令感知的潜在表征**。
- **目的**：从源头减少冗余视觉信息。

#### 阶段 2：LLM-FiLM based Pruning Routing（LFP-Routing）
- **位置**：语言模型（LLM 主干）内部。
- **做法**：通过 FiLM 将**动作意图（action intent）**注入 LLM。
- **效果**：**剪枝（pruning）与指令无关的视觉基础 token**，实现**token 级稀疏化**。
- **目的**：在 LLM 推理阶段进一步降低计算量。

#### 阶段 3：V-L-A Coupled Attention（CAtten）
- **位置**：跨模态注意力层。
- **做法**：
  - 视觉-语言部分使用**因果注意力（causal attention）**。
  - 动作部分使用**双向并行解码（bidirectional parallel decoding）**。
- **目的**：在感知被压缩的情况下，确保**动作生成的准确性、连贯性与端到端一致性**。

### 2.2 方法核心创新点总结
- **跨模态协同稀疏化**：不同于传统只关注 LLM 内部的方法，CogVLA 在视觉编码、LLM 推理、跨模态注意力三个层面同时引入指令与动作意图。
- **认知对齐设计灵感**：模拟人类多模态认知协调过程。
- **两阶段 FiLM 路由机制**：EFA-Routing + LFP-Routing 形成"视觉压缩 → 语言稀疏"链路。

---

## 3. 实验设计

### 3.1 Benchmark 与场景
- **仿真基准**：**LIBERO**（机器人操控的标准 benchmark）。
- **真实场景**：**真实机器人任务（real-world robotic tasks）**。
- **任务类型**：机器人操作（robotic manipulation）。

### 3.2 对比方法
- 主要基线：**OpenVLA**（代表性 VLA 模型）。
- 隐含对比对象：隐含引用现有稀疏化方法（Mixture-of-Depths、Layer Skipping、Early Exit）作为动机对比，但未明确列出全部消融对比对象（需查正文确认）。

### 3.3 主要结果（来自摘要）
- **LIBERO**：成功率 **97.4%**。
- **真实机器人任务**：成功率 **70.0%**。
- **效率提升**：
  - 训练成本降低 **2.5×**。
  - 推理时延降低 **2.8×**。
  - 相对基线均为 **OpenVLA**。

---

## 4. 资源与算力

- 摘要中**未明确说明**所用 GPU 型号、数量、训练时长等具体算力信息。
- 仅给出相对的效率提升指标：训练成本 -2.5×、推理时延 -2.8×（vs. OpenVLA）。
- 实际硬件配置、训练 epoch 数、参数量等需查阅正文或附录（当前不可获取）。

---

## 5. 实验数量与充分性

- 现有可获取信息显示包含至少两组主实验：
  1. **LIBERO 仿真基准实验**。
  2. **真实机器人任务实验**。
- 通常此类 VLA 论文还会包含：
  - 各阶段（EFA-Routing、LFP-Routing、CAtten）的**消融实验**；
  - 跨多个 LIBERO 子集（LIBERO-Spatial、LIBERO-Object、LIBERO-Goal、LIBERO-Long 等）的评估；
  - 推理时延 / FLOPs / 吞吐量分析。
  - 但**这些细节未能从摘要中确认**，充分性需待正文验证。
- 总体来看，仿真 + 真实机器人的组合使评估场景具备一定说服力，但**是否覆盖多任务、多物体、多干扰**等场景，仍需进一步确认。

---

## 6. 主要结论与发现

- **性能领先**：在 LIBERO 和真实机器人任务上达到 SOTA，成功率分别达 97.4% 和 70.0%。
- **效率显著提升**：相比 OpenVLA，训练成本降低 2.5×，推理时延降低 2.8×。
- **验证认知对齐思路有效**：跨模态协同的稀疏化（视觉编码 + LLM 内部 + 跨模态注意力）比纯 LLM 内部稀疏化更有效。
- **为可扩展 VLA 部署提供统一方案**：在不牺牲性能的前提下显著降低计算开销。

---

## 7. 优点 / 亮点

- **问题定位精准**：明确指出"跨模态语义耦合被忽视"这一关键缺口。
- **方法论系统性强**：3 阶段渐进式架构覆盖了从感知压缩到动作解码的全链路。
- **认知可解释性**：以"人类多模态协调"为隐喻，增强方法可解释性。
- **效率与性能兼得**：在 SOTA 性能下实现 2.5× 训练加速和 2.8× 推理加速，工程价值高。
- **仿真 + 真实双验证**：评估场景较为全面，提升结论可信度。
- **模块化设计**：EFA-Routing、LFP-Routing、CAtten 三个模块各自独立，便于后续消融与扩展。

---

## 8. 不足与局限

- **可获取信息有限**：由于 PDF 未能成功解析，以下判断均基于摘要，存在不完整风险。
- **算力信息不透明**：未在摘要中说明硬件规模与训练时长，**复现成本**难以直接评估。
- **真实任务细节不足**：70.0% 的真实机器人成功率与具体任务数、物体数、尝试次数等未给出，可能存在**评估范围偏小**的风险。
- **对比基线单一**：摘要中仅明确对比 OpenVLA，**未明确是否对比了其他近期 VLA（如 RT-2、Pi0、Octo 等）**。
- **泛化性待验证**：在分布外（OOD）任务、复杂长序列任务中的表现是否仍保持 SOTA，未在摘要中说明。
- **安全与可解释性**：作为机器人操控模型，未讨论指令歧义、错误动作恢复等安全相关问题。
- **潜在偏差风险**：真实机器人实验通常任务数有限，可能存在**实验选择偏差**，需谨慎解读结果。

---

（完）
