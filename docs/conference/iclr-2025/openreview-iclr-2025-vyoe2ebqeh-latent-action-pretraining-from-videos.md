---
title: Latent Action Pretraining from Videos
title_zh: LAPA：基于视频的潜在动作预训练
authors: "Seonghyeon Ye, Joel Jang, Byeongguk Jeon, Se June Joo, Jianwei Yang, Baolin Peng, Ajay Mandlekar, Reuben Tan, Yu-Wei Chao, Bill Yuchen Lin, Lars Liden, Kimin Lee, Jianfeng Gao, Luke Zettlemoyer, Dieter Fox, Minjoon Seo"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=VYOe2eBQeh"
tags: ["query:rob-il"]
score: 9.0
evidence: 从视频中无监督预训练通用视觉-语言-动作模型
tldr: 本文针对现有视觉-语言-动作模型依赖昂贵人工遥控动作标签、限制数据规模的问题，提出了LAPA无监督预训练方法。该方法先利用VQ-VAE从视频帧间学习离散潜在动作，再预训练VLA模型预测这些潜在动作，最后在小规模机器人操作数据上微调。这一流程首次实现了无需真实动作标签的VLA预训练，可利用互联网规模的视频数据。该工作大幅扩展了通用机器人视觉-动作模型的训练数据来源。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型依赖昂贵人工遥控的动作标签，严重限制了训练数据规模。
method: 用VQ-VAE从视频帧间学习离散潜在动作，并据此无监督预训练VLA模型。
result: 首次实现无需真实动作标签的VLA预训练，并可在小数据上微调。
conclusion: 解锁了互联网规模视频数据用于通用机器人策略训练的潜力。
---

## Abstract
We introduce Latent Action Pretraining for general Action models (LAPA), the first unsupervised method for pretraining Vision-Language-Action (VLA) models without ground-truth robot action labels. Existing Vision-Language-Action models require action labels typically collected by human teleoperators during pretraining, which significantly limits possible data sources and scale. In this work, we propose a method to learn from internet-scale videos that do not have robot action labels. We first train an action quantization model leveraging VQ-VAE-based objective to learn discrete latent actions between image frames, then pretrain a latent VLA model to predict these latent actions from observations and task descriptions, and finally finetune the VLA on small-scale robot manipulation data to map from latent to robot actions. Experimental results demonstrate that our method significantly outperforms existing techniques that train robot manipulation policies from large-scale videos. Furthermore, it outperforms the state-of-the-art VLA model trained with robotic action labels on real-world manipulation tasks that require language conditioning, generalization to unseen objects, and semantic generalization to unseen instructions. Training only on human manipulation videos also shows positive transfer, opening up the potential for leveraging web-scale data for robotics foundation models.

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize the paper "Latent Action Pretraining from Videos" (LAPA) in Chinese, following a specific structure with 8 points. Let me analyze the available information carefully.

From the metadata and abstract, I can extract:
- Title: Latent Action Pretraining from Videos (LAPA)
- Authors: Many researchers from what appears to be Microsoft Research and University of Washington teams
- Conference: ICLR 2025 (Accepted)
- Core problem: Existing VLA models require expensive human-collected action labels, limiting data scale
- Method: 
  1. Train VQ-VAE to learn discrete latent actions between video frames
  2. Pretrain latent VLA model to predict these latent actions from observations and task descriptions
  3. Finetune VLA on small-scale robot manipulation data to map latent to robot actions
- Key results: 
  - First unsupervised VLA pretraining without ground-truth action labels
  - Outperforms existing methods that train from large-scale videos
  - Outperforms SOTA VLA model trained with action labels on real-world tasks
  - Positive transfer from human manipulation videos

The paper PDF content is just a CAPTCHA verification page, so I can only use the abstract and metadata. I should note this limitation in my summary where appropriate, especially for sections requiring computational resources and detailed experimental settings.

Let me write a comprehensive Chinese summary following the 8-point structure requested.</think>

# LAPA：基于视频的潜在动作预训练 —— 论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：当前主流的 **视觉-语言-动作（Vision-Language-Action, VLA）模型** 在预训练阶段依赖由人类遥控操作采集的真实机器人动作标签（action labels），这种数据采集方式成本高昂、规模受限，阻碍了训练数据的扩展。
- **研究意义**：机器人操作策略的训练极度缺乏可扩展的大规模数据，而互联网中存在海量的、未标注动作信息的视频（包括人类操作视频和跨形态机器人视频）。如果能绕过对真实动作标签的依赖，将这些"免费"的视频数据利用起来，将极大推动**通用机器人基础模型**的发展。
- **整体目标**：提出首个**无需真实机器人动作标签**的 VLA 无监督预训练方法 LAPA（Latent Action Pretraining for general Action models），从互联网规模的视频中学习通用的视觉-动作表征。

## 2. 方法论：核心思想、关键技术与流程

- **整体思路**：三阶段流程，将"动作标签缺失"问题转化为"潜在动作预测"问题。
- **关键技术与流程**：
  1. **第一阶段：潜在动作量化（Action Quantization）**
     - 使用 **VQ-VAE** 目标函数训练一个动作量化模型。
     - 输入视频中连续两帧图像（$o_t, o_{t+1}$），模型在二者之间学习一组**离散的潜在动作（latent actions）** codebook，相当于无监督地从视频帧间变化中"提取"出动作语义。
  2. **第二阶段：潜在动作 VLA 预训练（Latent VLA Pretraining）**
     - 训练一个 VLA 模型，输入当前观测 $o_t$ 和任务语言描述 $\ell$，输出**预测的潜在动作**（而非真实物理动作）。
     - 由于潜在动作是从视频中无监督得到的，因此该阶段可以使用大量无标签的互联网视频。
  3. **第三阶段：下游微调（Finetuning）**
     - 在**小规模真实机器人操作数据**上对 VLA 进行微调。
     - 微调过程中将模型预测的潜在动作**映射到真实机器人动作空间**，从而得到可执行的机器人策略。
- **核心创新点**：用"潜在动作"作为代理任务（surrogate task）替代真实动作标签，使无动作标签的视频也能用于 VLA 预训练。

## 3. 实验设计：数据集、Benchmark 与对比方法

- **训练数据**：
  - 互联网规模视频（用于第一、二阶段无监督预训练）；
  - 小规模真实机器人操作数据（用于第三阶段微调）；
  - 同时验证了仅使用**人类操作视频**进行训练也能带来正向迁移。
- **下游 Benchmark**：
  - **真实机器人操作任务**：重点评测**语言条件操控**、**未见物体泛化**、**未见指令的语义泛化**三类能力。
- **对比方法**：
  - 现有从大规模视频中训练机器人操作策略的方法（如其他视频预训练基线）；
  - **使用真实动作标签训练的 SOTA VLA 模型**（作为强基线）。

> 注：因 PDF 内容未能完整提取（仅有摘要），关于具体数据集名称（如 OpenX-Embodiment、RT-1 等）与具体任务清单，需进一步查阅正文确认。

## 4. 资源与算力

- 摘要与可获取的元数据中**未明确披露**所使用的 GPU 型号、数量及训练时长。
- 由作者署名（Microsoft Research 等机构）和方法规模推断，预期使用了较大规模的多卡 GPU 集群进行预训练，但**具体算力细节需参考正文或附录**。

## 5. 实验数量与充分性

- 摘要中明确报告了三类评估维度：
  1. 与"从视频训练"基线的对比；
  2. 与"使用真实动作标签"的 SOTA VLA 的对比；
  3. 仅用人类操作视频训练的迁移效果。
- **公开层面**：摘要强调了在语言条件、物体泛化、指令泛化上的显著提升，论据较为清晰。
- **局限性**：由于 PDF 文本未能成功解析（仅返回 OpenReview 的 CAPTCHA 验证页），无法完整评估其消融实验、随机种子次数、统计显著性检验等充分性指标，需查阅正文判断。

## 6. 主要结论与发现

- **首次实现无需真实动作标签的 VLA 预训练**，大幅降低了机器人策略对昂贵人工标注数据的依赖。
- LAPA 显著优于现有的"从大规模视频训练机器人操作策略"的方法。
- 在真实机器人操控任务上，LAPA **超过了使用真实动作标签训练的 SOTA VLA 模型**，特别是在语言条件操控、对未见物体与未见指令的泛化能力上。
- 仅使用**人类操作视频**也能带来正向迁移，表明互联网规模的非机器人视频具备用于构建机器人基础模型的潜力。

## 7. 优点与亮点

- **方法创新性强**：用 VQ-VAE 提取离散潜在动作作为代理任务，思路简洁优雅，且首次实现无标签 VLA 预训练。
- **数据可用范围广**：解锁了互联网规模视频（含人类视频、跨形态机器人视频）作为训练源的可行性。
- **下游性能出色**：在真实机器人任务中击败了带标签训练的强基线，体现了方法的实用价值。
- **范式突破**：为构建"机器人基础模型"提供了新的数据驱动路径。

## 8. 不足与局限

- **数据分布偏差风险**：互联网视频与真实机器人操作场景之间存在显著的视觉、动力学和形态差异，潜在动作能否稳定跨形态迁移仍待进一步验证。
- **潜在动作的可解释性**：VQ-VAE 学到的离散 codebook 是否真正对应可解释的物理动作（如抓取、推动）仍不明确，可能限制后续分析和安全部署。
- **微调阶段仍需少量真实机器人数据**：并未完全摆脱对真实机器人数据的依赖，规模化部署时仍存在采集成本。
- **可复现性受限**：PDF 文本未能解析，算力、训练时长、消融细节、超参数等关键复现信息暂未可知。
- **评测规模与多样性**：摘要强调的是真实机器人任务，但具体的任务数量、试验次数、统计显著性等客观性指标仍需正文核实。

（完）
