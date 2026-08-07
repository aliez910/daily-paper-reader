---
title: Building Generalist Robot Policy from Pre-trained Visual Representations
title_zh: 基于预训练视觉表征构建通用机器人策略
authors: "Yunshi Wen, Zhengye Yang, Richard Radke, Anak Agung Julius"
date: 2024-09-27
pdf: "https://openreview.net/pdf?id=9GKMCecZ7c"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于预训练视觉表征构建通用机器人操作策略
tldr: 本文研究如何利用预训练视觉模型来构建能够执行多任务并跨越域差异的通用机器人操作策略。作者发现，常用预训练模型的全局特征不足以支撑多任务操作，而保留局部特征则能显著提升域内性能与跨域泛化能力；其中在传统视觉数据上训练的 DINOv2 反而优于专门为机器人设计的模型。此外，论文还提出了进一步弥合域差距的方法。该工作通过厘清哪些预训练特征最易迁移，直接推动了通用视觉-动作机器人策略的发展。
source: ICLR-2025-Public
selection_source: conference_retrieval
motivation: 现有通用机器人操作策略难以兼顾多任务能力与跨域泛化，需要合适的视觉预训练表征支撑。
method: 系统评估多种视觉预训练模型，保留局部特征并提出域差距弥合技术以构建通用策略。
result: 局部特征显著提升多任务表现，DINOv2 等通用视觉模型优于机器人专用模型。
conclusion: 为通用视觉-动作机器人策略的表征选择与迁移提供了明确指引。
---

## Abstract
In this paper, we investigate the use of vision pre-trained models (PTMs) for developing generalist robot manipulation policies. We study whether embodied policies trained with representations from vision and language PTMs are capable of multi-tasking and overcoming domain gaps. Evaluating a set of off-the-shelf vision PTMs, our first finding is that the commonly used global features are generally inadequate for building multi-task robot manipulation policies, while keeping local features significantly improves in-domain performance and out-of-domain generalizibility. Experiment results show that DINOv2, a model trained on conventional vision datasets, outperforms models explicitly designed for robot learning. To bridge the domain gaps, we further experiment on the effect of augmentation methods on embodied robot policies and few-shot adaptation. On the later case, we propose a novel objective by introducing self-distillation to the objectives of few-shot adaptation. Experiment results show that our approach is compatible with multiple PTMs, improving performance on novel domains when the number of demonstration available is limited.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Building Generalist Robot Policy from Pre-trained Visual Representations" based on the provided metadata and abstract. Let me organize my response according to the 8 requested sections.

I need to:
1. Use Markdown format with hierarchical headings and bullet points
2. Cover all 8 points requested
3. Be concise but informationally complete
4. End with "（完）" marker
5. Use Chinese language

Let me draft a comprehensive summary based on the metadata and abstract provided.</think>

# 论文总结：基于预训练视觉表征构建通用机器人策略

## 1. 核心问题与整体含义

- **研究背景**：通用机器人操作策略（generalist robot manipulation policies）需要在多任务、多场景下同时具备良好的任务执行能力与跨域泛化能力。然而现有方法往往难以兼顾"多任务能力"与"跨域迁移"。
- **核心问题**：
  - 现有通用机器人策略在视觉表征层面缺少系统性指导——哪些预训练视觉模型（PTM）更适合用于具身操作？
  - 常用的全局特征（global features）是否足以支撑多任务学习？
  - 如何弥合预训练视觉数据与机器人真实部署场景之间的域差距（domain gap）？
- **研究意义**：明确"哪些视觉预训练特征最适合迁移到机器人策略"这一基础问题，为通用视觉-动作（vision-action）机器人策略的设计提供可操作的指引。

## 2. 方法论

- **核心思想**：系统评估多种开源视觉预训练模型（包括通用视觉模型与机器人专用模型），分析"全局特征 vs. 局部特征"对机器人操作策略的影响，并提出域差距弥合方法。
- **关键技术细节**：
  - **表征层级对比**：保留视觉 PTM 的局部特征（local features / patch-level tokens），而非仅使用 CLS token 等全局特征。
  - **预训练模型选择**：覆盖 DINOv2（在传统视觉数据集上训练）以及若干专门为机器人学习设计的视觉模型。
  - **域差距弥合**：
    - **数据增强（augmentation）**：研究增强方法对具身策略鲁棒性的影响。
    - **少样本适应（few-shot adaptation）**：提出一种新目标函数，将 **自蒸馏（self-distillation）** 引入到少样本适应目标中，以在有限演示样本条件下提升对新颖域的迁移能力。
- **算法流程（文字描述）**：
  1. 选定预训练视觉模型并提取中间层局部 token；
  2. 将局部特征作为策略网络的视觉输入，训练多任务操作策略；
  3. 在新域上进行少样本微调，并以自蒸馏损失约束表征稳定；
  4. 对比不同 PTM、不同特征层级、不同适应策略下的最终性能。

## 3. 实验设计

- **数据集 / 场景**：
  - 主要为机器人操作（manipulation）相关 benchmark，具体数据集名称在所提供的文本片段中未完全列出，但从 ICLR 论文与"具身操作"语境来看，应包含多任务操作基准（如可能涉及 Meta-World、RoboSuite / Bridge / LIBERO 等常见具身操作 benchmark）。
- **Benchmark 与评估维度**：
  - **域内性能（in-domain performance）**：多任务操作的成功率。
  - **跨域泛化（out-of-domain generalization）**：在未见过的环境/外观/物体配置下的表现。
- **对比方法**：
  - 多种开箱即用（off-the-shelf）视觉预训练模型横向对比；
  - 全局特征 vs. 局部特征的消融；
  - 通用视觉模型（DINOv2）vs. 机器人专用视觉模型；
  - 多种增强方法的对比；
  - 少样本适应中是否引入自蒸馏损失的对比。

## 4. 资源与算力

- 所提供的 PDF 提取文本仅为 OpenReview 的验证码页面，**论文正文中关于 GPU 型号、数量、训练时长等算力细节无法从当前材料中确认**。
- 需要查阅论文正文中的"Experimental Setup"或"Implementation Details"章节以获取完整信息。
- 在当前可见摘要与元数据范围内，**未提及任何具体算力或训练时长信息**。

## 5. 实验数量与充分性

- **实验类型覆盖**：
  - 不同视觉 PTM 的对比实验；
  - 全局特征 vs. 局部特征的消融；
  - 增强方法对策略影响的实验；
  - 少样本适应 + 自蒸馏的消融/对比实验；
  - 域内与跨域两组评估维度。
- **充分性评估**：
  - 实验设计在"表征选择"这一中心问题上较为系统，结论方向清晰（局部特征 > 全局特征；通用 DINOv2 > 机器人专用模型）。
  - 但所提供的摘要级别信息**不足以判断**实验在 benchmark 数量、随机种子、统计显著性检验等方面是否足够严谨与公平。
  - 部分关键细节（如是否对所有 PTM 使用相同下游结构、训练步数、超参搜索策略等）需要查阅正文确认。

## 6. 主要结论与发现

- **关键发现 1**：常用的 **全局特征** 在多任务机器人操作中普遍不足；
- **关键发现 2**：**保留局部特征** 能够显著提升域内性能与跨域泛化能力；
- **关键发现 3**：在传统视觉数据上训练的 **DINOv2** 反而优于专门为机器人学习设计的视觉模型；
- **关键发现 4**：通过增强方法与少样本适应（结合自蒸馏目标），可以进一步弥合域差距；
- **关键发现 5**：所提出的少样本自蒸馏方法兼容多种 PTM，在演示样本有限的情况下仍能改善新域性能。

## 7. 优点

- **问题定位精准**：聚焦"视觉表征选择"这一常被忽视但基础性极强的问题，结论具有普遍指导意义。
- **反直觉发现**：揭示了"通用视觉模型 > 机器人专用模型"的有趣结论，为社区重新审视专用数据集/专用模型的价值提供依据。
- **方法兼容性强**：自蒸馏少样本适应目标可与多种 PTM 组合，具有较好可迁移性。
- **同时考虑域内与跨域**：评估维度全面，兼顾"多任务能力"与"泛化能力"。

## 8. 不足与局限

- **数据来源限制**：本总结所依据的 PDF 文本仅为验证码页面，**论文正文细节（特别是实验规模、统计检验、失败案例分析）均无法确认**。
- **真实部署信息有限**：摘要未提及真实硬件机器人实验，结果是否完全适用于 sim-to-real 场景需进一步验证。
- **PTM 覆盖面**：摘要提到"一组（a set）"PTM，但具体覆盖范围不明确，可能未涵盖最新的大规模视觉-语言模型（如更大的 VLM）。
- **少样本评估依赖演示质量**：few-shot adaptation 的性能受限于演示样本质量与数量，对实际应用中存在偏差风险。
- **潜在偏差风险**：若不同 PTM 在微调时使用了不同的训练预算或超参，可能对"哪个 PTM 更优"的结论产生偏差，需在正文中确认实验是否公平。
- **应用限制**：聚焦于 manipulation 任务，对 locomotion、长时序任务或包含更复杂语义指令的任务是否同样适用，仍待进一步研究。

（完）
