---
title: "Demystifying Robot Diffusion Policies: Action Memorization and a Simple Lookup Table Alternative"
title_zh: 揭秘机器人扩散策略：动作记忆与一种简单的查表替代方案
authors: "Chengyang He, Xu Liu, Gadiel Mark Sznaier Camps, Joseph Bruno, Guillaume Adrien Sartoretti, Mac Schwager"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=PL0tJOfm7I"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过扩散策略实现视觉运动机器人操控
tldr: 扩散策略在视觉运动机器人操控中以极少量演示即可获得出色灵巧性，但原因不明。本文提出假设：扩散策略本质上记忆了一个动作查找表，运行时在潜在空间中检索与测试图像最相近的训练动作。作者进一步证明这种基于记忆的行为在数据稀疏场景下反而是有益的，并提出了一个简单的查表基线作为强对比。分析揭示了当前方法在少样本设置中的工作机制与局限，对未来策略设计具有重要指导意义。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 扩散策略在少样本操控任务中表现优异，但其工作机制缺乏清晰解释。
method: 提出假设认为扩散策略等价于潜在空间中的动作查表，并设计简单查表基线进行验证。
result: 实验表明在数据稀疏时查表行为有益，并揭示了现有扩散策略缺乏动作泛化的本质。
conclusion: 为理解与改进视觉运动操控策略提供了关于记忆与泛化机制的新视角。
---

## Abstract
Diffusion policies for visuomotor robot manipulation tasks achieve remarkable dexterity and robustness while only training on a small number of task demonstrations.  However, the reason for this performance remains a mystery. In this paper, we offer a surprising hypothesis: diffusion policies essentially memorize an action lookup table---\emph{and this is beneficial}. We posit that, at runtime, diffusion policies find the closest training image to the test image in a latent space, and recall the associated training action  (i.e. action chunk), offering reactivity without the need for action generalization. This is effective in the sparse data regime, where there is not enough data density for the model to learn action generalization. We support this claim with systematic empirical evidence, showing that even when conditioned on highly out of distribution (OOD) images, Diffusion Policy still outputs an action chunk from the training data. We evaluate and compare three representative policy families on the same data set: Diffusion Policy, Action Chunking with Transformers (ACT), and GR00T, a pre-trained generalist Vision-Language-Action (VLA) model.  We show that Diffusion Policy gives strong action memorization giving surprising robustness in OOD regimes, ACT shows action interpolation with poor robustness in OOD regimes, and GR00T (benefiting from substantial pre-training) shows both action interpolation and OOD robustness. As a simple alternative to Diffusion Policy, we introduce the Action Lookup Table (ALT) policy, showing that an explicit lookup table policy can perform comparably in this low data regime. Despite its simplicity, ALT attains Diffusion Policy–level performance while also providing faster inference and explicit OOD detection via latent-distance thresholds. These results reframe diffusion policies for robot manipulation as reactive memory retrieval under data sparsity, and provide practical tools for interpreting, evaluating, and monitoring such policies. More information can be found at: \url{https://stanfordmsl.github.io/alt/}.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of a paper based on the provided metadata and abstract. Let me analyze the content carefully:

The paper is titled "Demystifying Robot Diffusion Policies: Action Memorization and a Simple Lookup Table Alternative" - a Chinese paper from ICLR 2026 about robot diffusion policies.

Key points from the abstract:
1. Diffusion policies for visuomotor robot manipulation achieve good performance with few task demonstrations
2. The authors propose a hypothesis: diffusion policies essentially memorize an action lookup table
3. At runtime, they find closest training image to test image in latent space and recall associated action
4. This is effective in sparse data regime where there's not enough data for action generalization
5. They provide systematic empirical evidence - even with OOD images, Diffusion Policy outputs action chunks from training data
6. They evaluate three policy families: Diffusion Policy, ACT, and GR00T (VLA model)
7. Diffusion Policy: strong action memorization, surprising robustness in OOD
8. ACT: action interpolation with poor OOD robustness
9. GR00T: both action interpolation and OOD robustness
10. They introduce Action Lookup Table (ALT) as simple alternative
11. ALT performs comparably to Diffusion Policy in low data regime with faster inference and explicit OOD detection

Let me create a detailed structured summary in Chinese following the requested format.
</think>
# 论文总结：揭秘机器人扩散策略：动作记忆与一种简单的查表替代方案

## 一、核心问题与研究动机

- **核心问题**：扩散策略（Diffusion Policy）在视觉运动机器人操控任务中表现出了卓越的灵巧性与鲁棒性，但所需训练演示数量极少——其卓越性能背后的机理尚不清楚。
- **研究背景**：尽管扩散策略在少样本（low-data）操控任务中效果突出，但目前缺乏对"为什么少量数据就能训练出高性能策略"这一现象的深入解释。
- **核心假设**：作者提出一个反直觉的假设——**扩散策略本质上记忆了一个"动作查找表"**，而这种记忆行为在少样本场景下反而是有益的。
- **现实意义**：理解扩散策略的工作机制有助于设计更可解释、可监控的操控策略，对策略在真实部署中的安全性与可靠性具有重要意义。

## 二、方法论

### 2.1 核心思想
- **动作记忆假说**：在推理阶段，扩散策略在潜在空间中找到与测试图像最接近的训练图像，并"回忆"（recall）其对应的训练动作块（action chunk）。即模型并未真正"泛化"出新动作，而是执行检索式的动作重现。
- **适用条件**：在数据稀疏（sparse data regime）场景下，训练数据密度不足以让模型学习到真正的"动作泛化"，因此基于记忆的检索行为反而是最优策略。

### 2.2 关键技术细节
- **ALT（Action Lookup Table）策略**：作为扩散策略的简单替代方案，ALT 构建一个显式的"图像-动作"查找表：
  - 训练阶段：存储所有训练样本的潜在表示与对应动作块。
  - 推理阶段：在潜在空间中检索与测试样本最接近的 k 个训练样本，取其动作块作为输出。
  - 优势：
    - **显式 OOD 检测**：通过潜在空间距离阈值判断测试样本是否分布外（out-of-distribution）。
    - **更快的推理速度**：省去了扩散模型的多次去噪迭代过程。
    - **更好的可解释性**：输出动作可追溯到具体训练样本。

### 2.3 评估方法
- 在相同数据集上系统比较三类代表性策略家族，验证记忆假说：
  - **Diffusion Policy**：扩散基策略
  - **ACT（Action Chunking with Transformers）**：基于 Transformer 的动作分块策略
  - **GR00T**：预训练的通用视觉-语言-动作（VLA）基础模型
- 设计 OOD 图像输入实验，检验各策略在分布外条件下的行为模式。

## 三、实验设计

- **数据集/场景**：基于视觉运动的机器人操控任务数据集（具体细节受限于 PDF 提取不完整，但属于 rob-il 类别）。
- **Benchmark**：在相同数据集上对比 Diffusion Policy、ACT、GR00T 三种方法，并加入 ALT 作为基线。
- **对比方法**：
  - Diffusion Policy（扩散基）
  - ACT（Transformer 基）
  - GR00T（预训练 VLA 大模型）
  - ALT（作者提出的查表基线）
- **评估维度**：
  - 操控任务的成功率
  - 在 OOD 图像条件下的输出行为分析
  - 推理速度
  - OOD 检测能力

## 四、资源与算力

- **说明**：由于 PDF 文本提取不完整（仅获取到 OpenReview 的验证页面），论文中关于具体 GPU 型号、数量、训练时长等算力细节**未能从提供的文本中确认**。
- 推断：考虑到涉及 GR00T（大规模预训练 VLA 模型）以及多种策略的对比实验，算力消耗应较为可观，但具体数字缺失。

## 五、实验数量与充分性

- **实验覆盖**：
  - 三类策略（Diffusion Policy、ACT、GR00T）× OOD/ID 条件的系统性对比。
  - ALT 与 Diffusion Policy 的直接对标。
  - 跨策略的"动作记忆 vs 动作插值"行为模式分析。
- **充分性评价**：
  - **优点**：实验设计聚焦核心假设（记忆假说），三类策略的对比具有代表性，结论层次清晰。
  - **局限**：受限于 PDF 提取内容，无法判断是否包含消融实验、不同数据规模实验、不同任务类型实验等更细粒度的验证。
  - 总体上，实验逻辑自洽，对假说的验证具备一定的说服力。

## 六、主要结论与发现

- **Diffusion Policy**：表现为强动作记忆，输出动作主要来自训练数据；在 OOD 条件下表现出令人惊讶的鲁棒性。
- **ACT**：表现为动作插值（action interpolation），但对 OOD 图像的鲁棒性较差。
- **GR00T**：得益于大规模预训练，同时具备动作插值能力与 OOD 鲁棒性。
- **ALT**：在少样本设置下，简单的查表策略即可达到与 Diffusion Policy 相当的性能，同时具备更快的推理速度和显式 OOD 检测能力。
- **核心洞察**：当前扩散策略在少样本操控中的成功，可能主要归功于"反应式记忆检索"机制，而非真正的动作泛化能力。

## 七、优点

- **新颖的视角**：对"扩散策略为何在小数据下表现优异"这一长期未解之谜，给出了一个简洁且可验证的解释。
- **方法论简洁优雅**：ALT 作为一个"奥卡姆剃刀"式的基线，挑战了"必须使用复杂生成模型"的固有认知。
- **实用价值强**：提供 OOD 检测能力与可追溯的决策路径，对真实机器人部署中的安全性监控具有重要意义。
- **跨方法对比的系统性**：在同一数据集下对三类代表性策略家族进行横向对比，结论具有较强的可推广性。
- **理论意义**：重新定义了机器人操控策略的设计思路，提示研究者关注"记忆 vs 泛化"的权衡。

## 八、不足与局限

- **结论的普适性**：假说主要在少样本设置下成立，未必能解释数据充足时扩散策略的行为；缺乏对不同数据规模下策略行为模式的完整分析。
- **动作插值与泛化的界限模糊**：ACT 表现为"插值"但缺乏 OOD 鲁棒性，作者未深入解释这种插值机制失败的具体原因。
- **GR00T 预训练的影响**：GR00T 的双重能力（插值+鲁棒）高度依赖大规模预训练，作者未深入探讨预训练数据规模与策略行为模式之间的量化关系。
- **ALT 的局限性**：作为查表方法，ALT 在数据量增大后可能面临存储与检索效率问题，论文未充分讨论其可扩展性。
- **缺乏失败案例分析**：未系统讨论 ALT 与扩散策略在哪些具体任务或条件下会出现显著性能差异。
- **PDF 提取受限**：部分实验细节、数据集名称、算力配置等关键信息无法从提取内容中获取，影响了对其完整性的判断。
- **应用限制**：目前聚焦于低数据、视觉运动操控场景，对于需要长期规划或复杂推理的任务尚不明确。

（完）
