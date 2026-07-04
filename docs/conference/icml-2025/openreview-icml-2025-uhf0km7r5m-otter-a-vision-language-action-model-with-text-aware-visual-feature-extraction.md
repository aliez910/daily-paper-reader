---
title: "OTTER: A Vision-Language-Action Model with Text-Aware Visual Feature Extraction"
title_zh: "OTTER: 具有文本感知视觉特征提取的视觉-语言-动作模型"
authors: "Huang Huang, Fangchen Liu, Letian Fu, Tingfan Wu, Mustafa Mukadam, Jitendra Malik, Ken Goldberg, Pieter Abbeel"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=UHF0km7R5M"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人动作预测的VLA模型，具有文本感知特征提取
tldr: 针对现有VLA模型需要微调预训练视觉-语言模型导致语义对齐退化的问题，提出OTTER架构。它通过文本感知视觉特征提取，仅将任务相关的视觉特征传递给策略网络，从而保持预训练编码器冻结。实验表明OTTER在多个机器人操作基准上取得了优异性能，且更高效。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型需微调预训练模型，破坏了原有的语义对齐。
method: 设计文本感知特征提取模块，选择性传递与指令语义对齐的视觉特征。
result: 在多个机器人操作任务上超越基线，同时保持预训练模型参数不变。
conclusion: 语义对齐的特征提取能有效提升VLA模型性能与训练效率。
---

## Abstract
Vision-Language-Action (VLA) models aim to predict robotic actions based on visual observations and language instructions. Existing approaches require fine-tuning pre-trained vision-language models (VLMs) as visual and language features are independently fed into downstream policies, degrading the pre-trained semantic alignments. We propose OTTER, a novel VLA architecture that leverages these existing alignments through explicit, text-aware visual feature extraction. Instead of processing all visual features, OTTER selectively extracts and passes only task-relevant visual features that are semantically aligned with the language instruction to the policy transformer. This allows OTTER to keep the pre-trained vision-language encoders frozen. Thereby, OTTER preserves and utilizes the rich semantic understanding learned from large-scale pre-training, enabling strong zero-shot generalization capabilities. In simulation and real-world experiments, OTTER significantly outperforms existing VLA models, demonstrating strong zero-shot generalization to novel objects and environments. Video, code, checkpoints, and dataset: https://ottervla.github.io/.

---

## 论文详细总结（自动生成）

# 论文总结：OTTER: 具有文本感知视觉特征提取的视觉-语言-动作模型

## 1. 核心问题与整体含义（研究动机和背景）

- **研究动机**：现有视觉-语言-动作（VLA）模型通常需要微调预训练的视觉-语言模型（VLM），这使得视觉和语言特征被独立送入下游策略网络，从而破坏了预训练阶段学习到的语义对齐。微调过程代价高且可能导致语义理解退化。
- **背景**：机器人操作任务需要根据视觉观测和语言指令预测动作；VLA模型期望利用大规模预训练VLM的丰富语义，但直接微调会损害其原有对齐能力。
- **核心问题**：如何在不破坏预训练语义对齐的前提下，将视觉和语言特征有效结合用于机器人动作预测，并保持高效训练与强泛化能力。

## 2. 方法论：核心思想、关键技术细节

- **核心思想**：通过**文本感知的视觉特征提取**，仅将与语言指令语义对齐的任务相关视觉特征选择性地传递给策略变换器（policy transformer），从而保持预训练编码器冻结，保留并利用大规模预训练的语义理解。
- **关键技术细节**：
  - 明确利用预训练VLM中已存在的语义对齐关系；
  - 设计文本感知特征提取模块（Text-Aware Visual Feature Extraction），根据语言指令动态筛选视觉特征；
  - 预训练的视觉编码器和语言编码器保持冻结，只训练策略网络部分，减少微调带来的退化；
  - 避免了将所有视觉特征不加区分地输入下游策略，提升了特征效率与语义一致性。
- **公式或算法流程**：原论文未提供具体公式或伪代码（基于给定摘要），文字上可概括为：输入图像和语言指令 → 冻结的视觉编码器提取全图特征 → 文本感知模块根据指令特征筛选相关视觉区域 → 仅将筛选后的视觉特征与语言特征送入策略变换器 → 输出动作。

## 3. 实验设计

- **数据集与场景**：摘要提及在仿真环境（Simulation）和真实世界（Real-World）机器人操作任务上进行实验，包括对新颖物体和新环境的零样本泛化测试。具体数据集名称和环境细节未在给定文本中说明。
- **Benchmark**：未明确指定基准测试，但或许采用机器人操作领域常用的模拟器（如RLBench、MetaWorld等）或自建真实场景。元数据标签显示属于 `query:rob-il`（机器人模仿学习）范畴，可能使用标准VLA评估协议。
- **对比方法**：摘要声明“显著优于现有VLA模型”，但对比的具体方法（如RT-2、MOO、或其他VLA架构）未列出。元数据在 `result` 中提到“在多个机器人操作任务上超越基线”，但未提基线名称。

## 4. 资源与算力

- **文中未明确说明**使用的GPU型号、数量、训练时长、参数量等信息。仅能从方法特征推断：冻结VLM仅训练策略部分，算力需求可能低于全模型微调方案，但具体数据缺失。

## 5. 实验数量与充分性

- **实验数量**：给定摘要和元数据未提供具体实验组数，只提到模拟和真实实验，以及零样本泛化测试。消融实验、不同任务数量等细节未知。
- **充分性评估**：由于信息有限，无法直接判断实验充分性。但该论文已被ICML 2025接收（元数据标明 `source: ICML-2025-Accepted`，且评分9.0），表明审稿人认为实验设计较为充分。然而，从公开摘要无法评估其统计有效性和偏差风险，可能还需要关注原始论文中更详细的实验设置。

## 6. 论文的主要结论与发现

- **主要结论**：语义对齐的特征提取能有效提升VLA模型性能与训练效率。
- **关键发现**：
  - OTTER显著优于现有VLA模型，在多个机器人操作任务上超越基线。
  - 通过保持预训练视觉-语言编码器冻结，将任务相关的语义对齐特征传递给策略网络，实现了**强零样本泛化**能力（对新物体和新环境）。
  - 该方法更高效（可能因只更新策略网络），且保留了预训练阶段的丰富语义理解。

## 7. 优点

- **方法创新**：提出文本感知视觉特征提取，巧妙利用预训练VLM的语义对齐，避免了微调带来的退化问题。
- **训练效率**：冻结预训练编码器仅训练策略网络，减少了计算开销和过拟合风险。
- **泛化能力**：在零样本场景（新物体、新环境）上表现出色，说明方法真正利用了预训练模型的语义知识。
- **实验验证**：涵盖了模拟和真实世界两种场景，增强了方法的实用性。
- **代码与数据开源**：论文提供视频、代码、检查点和数据集链接（见末尾URL），有利于复现和后续研究。

## 8. 不足与局限

- **信息不足**：基于给定摘要和元数据，无法评估实验的完整性和具体细节，如缺少数据集名称、对比方法、消融实验、错误分析等。
- **依赖预训练VLM质量**：方法效果可能受限于所选VLM的语义对齐程度，若预训练模型在特定领域能力不足，可能影响性能。
- **潜在偏差风险**：零样本泛化测试可能仅在特定任务和场景上证明有效性，通用性尚需更多证据。
- **算力和部署细节缺失**：没有报告训练资源、推理速度或模型规模，难以与其他方法公平比较效率。
- **应用限制**：未讨论复杂长指令、多步任务或高动态环境下的表现；真实实验可能限于特定机械臂或物体集合。

（完）
