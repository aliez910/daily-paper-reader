---
title: "Think Small, Act Big: Primitive-level Skill Prompt Learning for Lifelong Robot Manipulation"
title_zh: 小思大行：面向终身机器人操作的基本级技能提示学习
authors: "Yuanqi Yao, Siao Liu, Haoming Song, Yan Ding, Bin Zhao, Zhigang Wang, Dong Wang, Xuelong Li"
date: 2024-09-23
pdf: "https://openreview.net/pdf?id=tpUEqmjZiS"
tags: ["query:rob-il"]
score: 4.0
evidence: 免排练的终身机器人操作技能获取
tldr: 本文针对通用机器人需在不回访历史数据的情况下持续学习新技能这一终身学习难题，提出PSPL方法。该方法通过两阶段学习方案，在多技能预训练阶段利用前缀技能提示与运动感知模块提取共享知识，并构建可复用、可扩展的基本技能库。实验表明该方法能有效避免灾难性遗忘并支持终身技能扩展，为通用机器人持续学习提供了实用方案。
source: ICLR-2025-Public
selection_source: conference_retrieval
motivation: 通用机器人需在终身过程中免排练地持续获取新技能，且需避免灾难性遗忘。
method: 提出PSPL两阶段方案，通过前缀技能提示与运动感知模块学习可扩展的基本技能。
result: 方法在多技能顺序学习场景中有效保留旧知识并习得新技能。
conclusion: PSPL为终身机器人操作提供了一种免排练的可持续学习框架。
---

## Abstract
The general-purpose robots need to continuously acquire new skills in lifelong spans without revisiting past experiences, known as Rehearsal-free Lifelong Learning, which remains significantly challenging.  Recent advances learn a separate adapter along pretrained policy for each new skill to address catastrophic forgetting problem, ignoring the shared knowledge between old skills and new ones. To tackle these issues, we propose Primitive-level Skill Prompt Learning (PSPL), to achieve lifelong robot manipulation via reusable and extensible primitives.  Within our two stage learning scheme, we first learn a set of prefix skill prompts to extract shared knowledge through multi-skills pre-training stage, where motion-aware skill prompts are learned to capture semantic and motion shared primitives across different skills.  Secondly, when acquiring new skills in lifelong span, new prefix skill prompts are added and learned via cross-attention between prefix prompts of old skills, boosting the new skills learning via shared knowledge transfer. For evaluation, we construct a large-scale skill dataset and conduct extensive experiments in both simulation and real-world tasks, demonstrating PSPL's superior performance over state-of-the-art methods. Code and dataset will be released upon acceptance.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper "Think Small, Act Big: Primitive-level Skill Prompt Learning for Lifelong Robot Manipulation" based on the provided content. The PDF content was just a CAPTCHA verification page, but I have detailed metadata including abstract, title, authors, etc. Let me analyze what I have:

1. The paper is about lifelong robot manipulation learning without rehearsal
2. They propose PSPL (Primitive-level Skill Prompt Learning)
3. Two-stage learning: multi-skill pre-training with prefix skill prompts and motion-aware modules, then lifelong extension
4. They construct a large-scale skill dataset
5. Experiments in simulation and real-world
6. Authors include Yuanqi Yao, Siao Liu, Haoming Song, etc.
7. Published at ICLR 2025

Let me organize the summary according to the 8 requested points. Since the actual PDF content was not accessible (CAPTCHA blocked), I should base the summary on the abstract and metadata provided. I'll need to be honest about what can be inferred vs. what's detailed.

Let me write a thorough Chinese summary based on the available information.</think>

# 《Think Small, Act Big: Primitive-level Skill Prompt Learning for Lifelong Robot Manipulation》论文总结

## 1. 核心问题与研究动机

- **研究背景**：通用机器人（general-purpose robots）需要在真实环境的长时间跨度（lifelong span）中持续学习新技能。
- **核心挑战**：终身学习（Lifelong Learning）面临两大难题：
  - **灾难性遗忘**（Catastrophic Forgetting）：学习新任务后旧任务能力退化。
  - **免排练约束**（Rehearsal-free）：由于存储、隐私或计算限制，不能回访历史数据（rehearsal buffer）。
- **现有方法的不足**：近期方法通常为每个新技能在预训练策略上添加独立的 adapter（适配器），但这种做法**忽略了新旧技能之间的共享知识**，导致知识迁移效率低、参数膨胀。
- **研究目标**：让机器人能够以"组合复用"的方式学习可扩展的基本技能，实现终身且高效的操作能力增长。

## 2. 方法论：Primitive-level Skill Prompt Learning（PSPL）

### 2.1 核心思想
- 将复杂操作技能**分解为可复用、可扩展的"基本技能"（primitive skills）**。
- 通过 **前缀技能提示（Prefix Skill Prompts）** + **运动感知模块（Motion-aware Skill Prompts）** 学习并存储这些基本技能。
- 终身阶段通过新旧提示的**交叉注意力**实现共享知识迁移。

### 2.2 两阶段学习方案

#### 阶段一：多技能预训练（Multi-skill Pre-training）
- 学习一组前缀技能提示（prefix skill prompts）作为技能库的"槽位"。
- 引入 **运动感知技能提示（motion-aware skill prompts）**，捕获跨技能的：
  - **语义共享基本动作**（semantic primitives）
  - **运动共享基本动作**（motion primitives）
- 预训练完成后得到一个可扩展的基础技能库。

#### 阶段二：终身技能获取（Lifelong Skill Acquisition）
- 每当遇到新技能时，**新增一条新的前缀提示**（不改动旧提示）。
- 通过**新旧前缀提示之间的交叉注意力**（cross-attention between prefix prompts）：
  - 让新提示"参考"旧提示，从而复用已有知识。
  - 避免对旧提示参数的修改，从机制上缓解遗忘。
- 实现参数与知识层面的**可扩展性**（extensibility）。

### 2.3 关键技术细节
- **Prefix Prompt 机制**：源自自然语言处理中的 prefix tuning 思想，将其适配到机器人策略网络。
- **Motion-aware 设计**：不仅建模高层语义，还显式编码运动（动作序列）层面的共性。
- **Cross-Attention 知识迁移**：新技能学习时查询旧技能提示，实现"小提示—大动作"（Think Small, Act Big）的思想。

## 3. 实验设计

### 3.1 数据集与场景
- 作者**自行构建了一个大规模技能数据集**（large-scale skill dataset），用于多技能预训练和终身学习评测。
- 实验涵盖：
  - **仿真任务**（simulation tasks）
  - **真实世界任务**（real-world tasks）

### 3.2 Benchmark 与对比方法
- 对照任务为**多技能顺序学习场景**（sequential multi-skill learning）。
- 对比对象为 **state-of-the-art** 的终身机器人操作方法（具体名称未在摘要中给出，但属于基于预训练策略 + adapter 的 SOTA 类方法）。
- 评测维度应包含：最终技能成功率、旧技能保留率、参数/存储开销等。

### 3.3 注：
- 由于 PDF 原文未能成功提取（仅返回 OpenReview 的验证码页面），具体任务清单、对比方法名称、量化指标的细节**无法从摘要外的文本确认**。

## 4. 资源与算力

- 摘要与元数据中**未明确说明**使用的 GPU 型号、数量、训练时长或算力开销。
- 由于论文声明 "Code and dataset will be released upon acceptance"，可推测其代码与训练流程在论文接收后将公开，但**目前没有公开的算力信息**。
- 这是一个明显的报告缺失，建议读者关注正式发表版本的附录。

## 5. 实验数量与充分性

- 从元数据看，实验至少包括：
  - 多技能顺序学习主实验（仿真 + 真实）。
  - 终身学习典型场景（新旧技能保留率）。
- 由于原文不可访问，**消融实验（Ablation Study）、超参敏感性、不同顺序敏感性等是否充分**无法从摘要确认。
- 一般而言，ICLR-2025 接收论文通常会包含较充分的消融与可视化分析，但具体实验数量需以正文为准。
- **客观性与公平性**：所有方法在相同数据集、相同顺序下对比是终身学习评测的常规做法；但摘要未披露是否对每个方法做了多次随机种子运行。

## 6. 主要结论与发现

- PSPL 在仿真与真实世界的多技能顺序学习任务上**优于现有 SOTA**。
- **有效避免灾难性遗忘**：旧技能性能得到较好保留。
- **支持终身技能扩展**：新技能可在不重训旧模型的情况下学习。
- **共享知识迁移有效**：通过 prefix prompt + cross-attention，新技能学习效率提升。
- 为通用机器人的**免排练、可持续学习**提供了一种实用框架。

## 7. 优点与亮点

- **思路新颖**：将"基本技能（primitive）"作为终身学习的"积木"，而非为每个任务训练独立 adapter，更符合人类技能组合的认知。
- **机制优雅**：prefix + 冻结旧提示的设计，从机制层面（而非仅靠正则化）缓解遗忘。
- **运动感知**：同时建模语义与运动共享原语，比纯高层语义 prompt 更贴合机器人控制。
- **可扩展性强**：新增技能只需新增一条提示，理论上支持任意数量技能。
- **仿真 + 真实双验证**：方法不仅在仿真上有效，也迁移到了真实机器人。
- **数据集贡献**：自行构建的大规模技能数据集对社区有价值。

## 8. 不足与局限

- **PDF 原文未能获取**：本次总结仅基于摘要与元数据，方法细节（网络结构、训练损失、提示维度、cross-attention 形式等）无法深入评估。
- **算力信息缺失**：训练成本、可复现性难以评估。
- **依赖多技能预训练阶段**：方法的有效性高度依赖第一阶段是否能学到足够通用、可迁移的基本技能；若预训练覆盖不足，后续终身阶段仍可能受限。
- **prefix 数量增长问题**：虽然新增提示轻量，但随着技能数量累积，提示库会越来越大，cross-attention 的计算/存储成本是否仍可控需进一步验证。
- **真实世界任务规模未知**：摘要提到 real-world tasks，但具体任务数量与难度梯度未披露，可能存在评测覆盖不足的风险。
- **与基于 rehearsal/buffer 的方法对比缺失**：摘要仅与免排练类方法比较，未讨论在允许 rehearsal 场景下 PSPL 是否仍具优势。
- **作者列表与机构信息不完整**：摘要未列出作者所属机构，难以判断研究背景与潜在的应用偏向。

---

> **总体评价**：PSPL 提出了一种以"基本技能 + 前缀提示 + 运动感知 + 交叉注意力"为核心的终身机器人操作学习框架，思路清晰、机制优雅，命中了当前具身智能中"持续学习"的关键痛点。但受限于本次仅能获取摘要级信息，方法细节、消融完整性与算力可复现性仍需查阅正文与附录进一步评估。

（完）
