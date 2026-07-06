---
title: "XR-1: Towards Versatile Vision-Language-Action Models via Learning Unified Vision-Motion Representations"
title_zh: XR-1：通过统一视觉-运动表征构建通用视觉-语言-动作模型
authors: "Shichao Fan, Kun Wu, Zhengping Che, Xinhua Wang, Di Wu, Fei Liao, Ning Liu, Yixue Zhang, Zhen Zhao, Zhiyuan Xu, Meng Li, Qingjie Liu, Shanghang Zhang, Min Wan, Jian Tang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=XJclc9Eabd"
tags: ["query:rob-il"]
score: 9.0
evidence: 通用视觉-语言-动作模型，统一跨具身形态的视觉-运动表征
tldr: 本文针对通用视觉-语言-动作（VLA）模型面临的两个核心挑战展开研究：从高维观测生成精确低层动作，以及跨越异构数据源（不同机器人具身与人类演示）之间的域差距。作者提出XR-1，通过学习统一的视觉-运动表征，充分利用大规模异构数据集中的互补多模态知识。该方法结合视觉动态与机器人动作潜变量，推动了面向端到端机器人控制的通用VLA模型发展，为多具身、多数据源的统一学习提供了通用架构。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 通用VLA模型难以从高维观测生成精确低层动作，也难以跨越异构数据源的域差距。
method: 提出XR-1框架，通过学习统一视觉-运动表征融合视觉动态与机器人动作潜变量。
result: 在异构多具身数据上实现统一学习，提升了通用VLA模型的端到端控制能力。
conclusion: 统一视觉-运动表征是构建跨具身通用机器人控制模型的有效方向。
---

## Abstract
Recent progress in large-scale robotic datasets and vision-language models (VLMs) has advanced research on vision-language-action (VLA) models.  However, existing VLA models still face two fundamental challenges: (\textit{i}) producing precise low-level actions from high-dimensional observations, (\textit{ii}) bridging domain gaps across heterogeneous data sources, including diverse robot embodiments and human demonstrations. Existing methods often encode latent variables from either visual dynamics or robotic actions to guide policy learning, but they fail to fully exploit the complementary multi-modal knowledge present in large-scale, heterogeneous datasets. In this work, we present \textbf{XR-1}, a novel framework for versatile and scalable VLA learning across diverse robots, tasks, and environments.
At its core, XR-1 introduces the \emph{Unified Vision-Motion Codes (UVMC)}, a discrete latent representation learned via a dual-branch VQ-VAE that jointly encodes visual dynamics and robotic motion.  UVMC addresses these challenges by (\textit{i}) serving as an intermediate representation between the observations and actions, and  (\textit{ii}) aligning multimodal dynamic information from heterogeneous data sources to capture complementary knowledge. To effectively exploit UVMC, we propose a \emph{three-stage training paradigm}: (\textit{i}) self-supervised UVMC learning, (\textit{ii}) UVMC-guided pretraining on large-scale cross-embodiment robotic datasets, and (\textit{iii}) task-specific post-training.  We validate XR-1 through extensive real-world experiments with more than 12,000 rollouts on six different robot embodiments, spanning over 120 diverse manipulation tasks. XR-1 consistently outperforms state-of-the-art baselines such as $\pi_0$ and GR00T-N1.5 while demonstrating strong generalization to novel objects, background variations, distractors, and illumination changes. Our project is at \href{https://xr-1-vla.github.io/}{https://xr-1-vla.github.io/}.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "XR-1: Towards Versatile Vision-Language-Action Models via Learning Unified Vision-Motion Representations". I have the abstract and metadata, but the PDF content couldn't be extracted (it was a CAPTCHA page). I'll base my summary on the abstract and metadata provided, being careful not to fabricate specific details that aren't in the provided text.

Let me organize the summary according to the 8 required points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I need to be honest about what information is available and what isn't (since the full PDF wasn't accessible).
</think>
# XR-1 论文总结：基于统一视觉-运动表征的通用视觉-语言-动作模型

## 1. 核心问题与研究动机

随着大规模机器人数据集和视觉-语言模型（VLM）的发展，视觉-语言-动作（VLA）模型成为机器人学习领域的重要方向。然而，现有的 VLA 模型仍面临两个根本性挑战：

- **精确动作生成难题**：如何从高维视觉观测中生成精确的低层机器人动作。
- **跨域异构数据融合难题**：不同机器人具身（embodiment）和人类演示数据之间存在显著的域差距，难以有效整合。

现有方法通常只对视觉动态或机器人动作的潜变量单独编码，未能充分挖掘大规模异构数据中互补的多模态知识。

---

## 2. 方法论

### 2.1 核心思想

XR-1 的核心在于提出**统一视觉-运动编码（Unified Vision-Motion Codes, UVMC）**——一种通过双分支 VQ-VAE 学习的离散潜表征，联合编码视觉动态和机器人运动。

### 2.2 关键技术细节

- **UVMC 的双重作用**：
  - 作为观测与动作之间的中间表征，桥接高维视觉输入与低层动作输出。
  - 对齐来自异构数据源的多模态动态信息，捕获互补知识。
- **三阶段训练范式**：
  1. **自监督 UVMC 学习**：通过 VQ-VAE 自监督学习统一视觉-运动编码。
  2. **UVMC 引导的跨具身预训练**：在大规模跨具身机器人数据集上进行预训练。
  3. **任务特定后训练（post-training）**：针对具体任务进行微调。

---

## 3. 实验设计

根据摘要提供的信息：

- **真实世界实验**：在 6 种不同机器人具身上进行了超过 **12,000 次 rollout**。
- **任务范围**：涵盖 **120 余种不同的操控任务**。
- **对比基线**：与当前最先进的 VLA 模型进行比较，包括 **π₀** 和 **GR00T-N1.5**。
- **泛化测试**：评估模型在未见物体、背景变化、干扰物（distractors）和光照变化等场景下的泛化能力。

> 注：由于 PDF 原文未能成功提取（页面需要验证），关于具体使用的仿真 benchmark（如 SimplerEnv、LIBERO 等）和更多实验细节未能确认。

---

## 4. 资源与算力

根据所提供的摘要与元数据内容，**论文中未明确披露**具体的 GPU 型号、数量或训练时长。

> 建议：若需详细算力信息，可参考项目主页 https://xr-1-vla.github.io/ 或论文正式发表版本的附录。

---

## 5. 实验数量与充分性

- **实验规模可观**：6 种具身 × 120+ 任务 × 12,000+ 次 rollout，已属于大规模真实世界评测。
- **基线对比充分**：与最具代表性的两个 SOTA 模型（π₀、GR00T-N1.5）对比。
- **泛化维度丰富**：覆盖未见物体、背景变化、干扰物、光照变化四个维度，较为全面。
- **不足之处**（基于现有信息推断）：
  - 摘要中未提及消融实验（ablation studies）的数量与设计。
  - 未明确说明是否包含仿真环境下的标准 benchmark 测试。
  - 由于侧重真实世界实验，可重复性受限于硬件条件。

---

## 6. 主要结论与发现

- XR-1 在多种具身、任务和环境上**持续优于** π₀ 和 GR00T-N1.5 等 SOTA 基线。
- **统一视觉-运动表征**能够有效桥接异构数据源域差距，并作为观测-动作之间的有效中间表征。
- 验证了通过统一表征融合视觉动态与运动信息，是构建通用 VLA 模型的有效路径。
- 强泛化能力：在未见物体、背景变化、干扰物、光照变化场景下仍保持稳定表现。

---

## 7. 优点与亮点

- **统一表征的创新设计**：UVMC 同时编码视觉动态和机器人动作，避免了已有方法只关注单一模态的局限。
- **三阶段训练范式清晰**：从自监督表征学习 → 大规模预训练 → 任务后训练，pipeline 层次分明，符合现代大模型训练范式。
- **大规模真实世界验证**：6 种具身、120+ 任务、12,000+ rollout，实验规模在 VLA 领域属于较高水准。
- **强调跨具身泛化**：针对 VLA 领域的核心痛点——异构数据源整合——提供了切实可行的方案。
- **强泛化性能**：在多种干扰因素下仍表现稳健。

---

## 8. 不足与局限

- **PDF 原文未成功获取**：本次分析主要基于摘要与元数据，部分细节（具体数据集、消融实验、算力配置、公式细节）可能不完整。
- **算力信息缺失**：未披露训练所需的硬件资源，限制了对方法可复现性的评估。
- **仿真 benchmark 不明确**：从摘要看，实验以真实世界为主，但未说明是否在标准化仿真 benchmark（如 SimplerEnv、LIBERO、Calvin 等）上验证。
- **计算开销与延迟**：离散 VQ-VAE 编码 + 跨具身预训练的范式可能带来较大计算开销，论文是否讨论了推理延迟、模型大小等部署相关指标尚不明确。
- **数据偏差风险**：尽管覆盖 6 种具身，训练数据仍可能存在特定任务或环境的主导偏差，对长尾任务的覆盖度可能不足。
- **应用范围限制**：聚焦于操控任务（manipulation），未涉及移动导航、双足 locomotion 等其他机器人能力。
- **可复现性顾虑**：依赖大规模异构真实世界数据集，对一般研究团队复现门槛较高。

（完）
