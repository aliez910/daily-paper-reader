---
title: "FASTer: Toward Powerful and Efficient Autoregressive Vision–Language–Action Models with Learnable Action Tokenizer and Block-wise Decoding"
title_zh: FASTer：基于可学习动作令牌器与分块解码的高效自回归视觉-语言-动作模型
authors: "Yicheng Liu, Shiduo Zhang, Zibin Dong, Baijun Ye, Tianyuan Yuan, Xiaopeng Yu, Linqi Yin, Chenhao Lu, Junhao Shi, Luca Jiang-Tao Yu, Liangtao Zheng, Jingjing Gong, Tao Jiang, Xipeng Qiu, Hang Zhao"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=k6nTUFoqeT"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操作的自回归视觉-语言-动作模型
tldr: 针对自回归视觉-语言-动作（VLA）模型在机器人操作中动作令牌化所面临的重建精度与推理效率之间的权衡问题，本文提出了统一的FASTer框架。其核心是FASTerVQ可学习令牌器，将动作块编码为单通道图像以捕获全局时空依赖并保持高压缩比；在此基础上构建FASTerVLA策略，采用分块自回归解码与轻量动作专家。实验表明该方法在保持高效推理的同时提升了对多样化机器人操作任务的泛化能力。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 自回归VLA模型在动作令牌化阶段存在重建精度与推理效率难以兼顾的瓶颈，制约其在机器人操作中的实际部署。
method: 提出FASTerVQ将动作块编码为单通道图像，并构建采用分块自回归解码与轻量动作专家的FASTerVLA策略框架。
result: 在机器人操作任务上实现了高压缩比与高保真动作重建的兼顾，并提升了推理效率与泛化性能。
conclusion: FASTer为通用高效的机器人学习提供了统一的VLA方案，验证了可学习令牌化与分块解码的协同价值。
---

## Abstract
Autoregressive vision-language-action (VLA) models have recently demonstrated strong capabilities in robotic manipulation. However, their core process of action tokenization often involves a trade-off between reconstruction fidelity and inference efficiency.
We introduce \textbf{FASTer}, a unified framework for efficient and generalizable robot learning that integrates a learnable tokenizer with an autoregressive policy built upon it.
FASTerVQ encodes action chunks as single-channel images, capturing global spatio-temporal dependencies while maintaining a high compression ratio. FASTerVLA builds on this tokenizer with block-wise autoregressive decoding and a lightweight action expert, achieving both faster inference and higher task performance.
Extensive experiments across simulated and real-world benchmarks show that FASTerVQ delivers superior reconstruction quality, high token utilization, and strong cross-task and cross-embodiment generalization, while FASTerVLA further improves overall capability, surpassing previous state-of-the-art VLA models in both inference speed and task performance.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "FASTer: Toward Powerful and Efficient Autoregressive Vision–Language–Action Models with Learnable Action Tokenizer and Block-wise Decoding". I have the abstract and metadata, but the full PDF content was blocked by a CAPTCHA. So I need to base my summary primarily on the abstract and the metadata provided.

Let me structure the response according to the 8 required points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Since I only have the abstract, I should be honest about what information is available and what isn't. I should note where information is limited due to access restrictions.

Let me write this out in Chinese, using Markdown formatting with hierarchical headings.
</think>
# FASTer 论文总结

## 1. 核心问题与研究动机

- **背景**：自回归视觉-语言-动作（VLA）模型在机器人操控任务中展现出强大能力，但其在部署时面临两大瓶颈。
- **核心矛盾**：动作令牌化（action tokenization）阶段在**重建保真度**（reconstruction fidelity）与**推理效率**（inference efficiency）之间存在难以兼顾的权衡。
- **研究意义**：该权衡限制了自回归 VLA 模型在真实机器人操控场景中的实际部署，亟需一个兼顾压缩比、生成质量与推理速度的统一框架。

## 2. 方法论

FASTer 框架包含两个核心组件：

### 2.1 FASTerVQ —— 可学习动作令牌器
- **核心思想**：将**动作块**（action chunk）编码为**单通道图像**（single-channel image），从而利用图像化表征捕捉动作序列中的**全局时空依赖关系**。
- **关键优势**：
  - 维持高压缩比（high compression ratio），降低序列长度；
  - 提高令牌利用率（high token utilization）；
  - 改善动作重建的保真度。

### 2.2 FASTerVLA —— 自回归策略模型
- 在 FASTerVQ 之上构建，采用**分块自回归解码**（block-wise autoregressive decoding）。
- 引入**轻量级动作专家**（lightweight action expert）模块，提高推理速度并增强任务性能。
- 整体形成"统一令牌器 + 高效策略"的可端到端训练的 VLA 框架。

> 注：具体公式、损失函数与网络架构细节需参考正文图表，受当前可访问性限制未能完整提取。

## 3. 实验设计

- **实验场景**：涵盖**模拟环境与真实世界**两类基准测试（simulated and real-world benchmarks）。
- **核心评估维度**：
  - 动作重建质量（reconstruction quality）；
  - 令牌利用率（token utilization）；
  - 跨任务与跨具身（cross-task & cross-embodiment）泛化能力；
  - 任务成功率与推理速度。
- **对比基线**：与之前的**最先进 VLA 模型**（previous SOTA VLA models）进行对比，在推理速度与任务性能两个维度上同时进行比较。

> 注：具体基准名称（如 LIBERO、RLBench、MetaWorld 等）以及各方法名称未在摘要中明确列出，需进一步查阅正文。

## 4. 资源与算力

- **摘要与元数据中未明确披露**具体的 GPU 型号、训练时长或算力消耗。
- 仅可推测：作为 VLA 类模型，训练应涉及大规模多模态预训练 + 机器人操控微调，可能需要多卡 GPU 集群。
- 这一点属于论文信息的缺失，建议读者参阅正文或附录。

## 5. 实验数量与充分性

- 从摘要可知，实验覆盖了**模拟与真实双场景**，并对**重建质量、泛化、推理速度、任务性能**四个维度进行了评估，形式上较为全面。
- **但仅凭摘要无法判断**：
  - 具体做了多少组实验（数据集数量、任务数量）；
  - 是否包含充分的消融实验（如各模块对最终性能的贡献）；
  - 跨具身实验的具身类型覆盖范围；
  - 实验的随机种子次数与统计显著性检验。
- 建议进一步阅读正文以评估实验的客观性与公平性。

## 6. 主要结论与发现

- FASTerVQ 在**重建质量、令牌利用率、跨任务与跨具身泛化**方面均表现优异。
- FASTerVLA 在**推理速度与任务性能**两个指标上同时超越了之前的 SOTA VLA 模型。
- 验证了**可学习令牌化 + 分块解码**的协同设计对于通用高效机器人学习的有效性。

## 7. 优点与亮点

- **问题定位精准**：聚焦于 VLA 落地部署中最核心的动作令牌化效率-质量权衡问题。
- **方法设计新颖**：
  - 将动作块表示为单通道图像是一种简洁而有效的范式转换；
  - 分块自回归解码 + 轻量动作专家在保持生成能力的同时显著提升推理速度。
- **统一框架**：将令牌器与策略整合为端到端训练系统，避免了两阶段训练可能带来的表征不一致问题。
- **泛化能力突出**：明确强调跨任务与跨具身的泛化能力，这是实用化的关键指标。
- **双重场景验证**：模拟 + 真实世界双重验证，提升结论可信度。

## 8. 不足与局限

- **信息可得性限制**：当前仅能依据摘要与元数据评估，正文细节（数据集、算力、消融等）未能获取，可能导致总结不完整。
- **单通道图像化表征的局限**：
  - 是否能很好捕捉**高频、非平稳**的动作变化尚不明确；
  - 动作块大小（chunk size）对精度与延迟的影响需要更系统的消融分析。
- **真实世界实验规模**：摘要未说明真实机器人实验的任务数量、试次与统计方法，泛化结论的统计强度有待确认。
- **安全与可靠性**：VLA 模型直接输出连续控制量，在真实部署中的**失败模式与安全约束**讨论应进一步补充。
- **可复现性**：算力与训练超参数未在摘要中披露，可能影响社区复现。
- **下游任务范围**：摘要所列的"机器人操控"任务是否覆盖长时序、接触密集型操作等高难度场景，仍需正文确认。

---

**（完）**
