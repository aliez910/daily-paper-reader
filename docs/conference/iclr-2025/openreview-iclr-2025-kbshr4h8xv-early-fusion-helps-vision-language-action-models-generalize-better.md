---
title: Early Fusion Helps Vision Language Action Models Generalize Better
title_zh: 早期融合助力视觉-语言-动作模型更好泛化
authors: "Huang Huang, Fangchen Liu, Letian Fu, Tingfan Wu, Mustafa Mukadam, Jitendra Malik, Ken Goldberg, Pieter Abbeel"
date: 2024-09-27
pdf: "https://openreview.net/pdf?id=KBSHR4h8XV"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向端到端闭环控制的视觉-语言-动作模型
tldr: 现有视觉-语言-动作模型通常将文本与图像编码为分离的 token，在执行精确闭环控制时泛化到新环境的能力受限。本文提出 EF-VLA，利用 CLIP 对比预训练所具备的视觉-语言对齐能力，通过早期融合构建新型 VLA 架构。该方法在同时执行视觉-语言理解与精确闭环控制方面取得改进，显著提升了在机器人操作新环境中的泛化能力，为端到端机器人控制提供了更有效的 VLA 建模方案。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 现有 VLA 模型在同时进行视觉-语言理解与精确控制时难以泛化到新环境。
method: 提出早期融合 VLA 架构，充分利用 CLIP 的视觉-语言对齐能力。
result: 在机器人操作的闭环控制与跨环境泛化上取得了显著提升。
conclusion: 验证了早期融合对端到端机器人控制 VLA 模型泛化的关键作用。
---

## Abstract
Recent advances in Vision-Language-Action (VLA) models can enable robots to perform a wide range of tasks based on language or goal-based instructions. These VLA models typically encode text and images into disjoint tokens, generating actions that align with the given instructions. This requires the VLA models to simultaneously perform vision-language understanding and precise closed-loop control, resulting in significant challenges for them to generalize to new environments. However, contrastive pre-trained VLMs, such as CLIP, already possess vision-language alignment capabilities, which are underutilized by current VLA models. In this paper, we propose Early Fusion VLA (EF-VLA), a novel VLA architecture that exploits CLIP’s vision-language understanding by performing early fusion, extracting fine-grained vision-language tokens relevant to the task instructions before passing them to the transformer policy. EF-VLA keeps the
VLM frozen, allowing it to effectively perform unseen tasks without requiring fine-tuning, which often reduces generalization capabilities. Simulation and real-world experiments suggest that EF-VLA outperforms state-of-the-art VLA models on diverse tasks, with significant generalization capabilities in unseen environments.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper based on the provided metadata. Let me organize this systematically following the 8 required points.</think>

# 论文总结：早期融合助力视觉-语言-动作模型更好泛化（EF-VLA）

## 1. 核心问题与整体含义

- **研究背景**：近年来，视觉-语言-动作（Vision-Language-Action, VLA）模型使机器人能够根据语言指令或目标图像完成多种任务。但现有 VLA 模型通常将文本与图像分别编码为**分离的 token**，再由策略网络生成动作。
- **关键挑战**：VLA 模型需要**同时**完成视觉-语言理解与精确的闭环控制，这对模型跨环境泛化能力提出了极高要求。当部署到训练中未见过的新环境时，这类模型往往表现不佳。
- **核心洞察**：CLIP 等对比预训练的视觉-语言模型（VLM）天然具备视觉-语言对齐能力，但当前的 VLA 架构**未能充分利用**这一已有能力。
- **研究目标**：提出一种更有效融合视觉与语言信息的 VLA 架构，使机器人既能完成高层语义理解，又能保证底层闭环控制的精度，并显著提升在未见环境中的泛化能力。

## 2. 方法论：核心思想与关键技术

- **核心思想**：**早期融合（Early Fusion）** —— 在将 token 输入 Transformer 策略网络之前，先利用 CLIP 进行视觉-语言早期融合，提取与任务指令相关的细粒度视觉-语言 token。
- **关键技术细节**：
  - **保持 VLM 冻结（VLM frozen）**：EF-VLA 在训练与推理时保持 CLIP 等视觉-语言编码器参数固定，仅训练后续的策略网络。这一设计的动机是：微调 VLM 往往会削弱其在预训练阶段获得的通用视觉-语言对齐能力，从而损害泛化能力。
  - **细粒度 token 提取**：通过早期融合机制，从 CLIP 中提取与文本指令最相关的视觉特征 token，避免将所有图像 token 全部输入策略网络。
  - **Transformer 策略**：融合后的视觉-语言 token 送入 Transformer 策略网络，输出机器人动作（如末端位姿、关节角等），实现闭环控制。
- **算法流程（文字描述）**：
  1. 输入：当前观测图像 + 任务语言指令。
  2. 冻结的 CLIP 编码器对图像与文本进行早期融合，提取任务相关的视觉-语言 token。
  3. 将融合 token 送入可训练的 Transformer 策略网络。
  4. 策略网络输出连续动作，机器人执行并进入下一时间步，循环形成闭环。

## 3. 实验设计

- **数据集与场景**：
  - 仿真环境与真实世界机器人操作任务（具体 benchmark 名称在 PDF 受限情况下未完全呈现，需参见正文）。
  - 涵盖多种机器人操作任务，且包含**未见环境（unseen environments）**用于评估泛化能力。
- **Benchmark**：以机器人操作任务的成功率（success rate）作为主要评估指标，并区分训练中见过的环境与未见过的环境。
- **对比方法**：与现有 **state-of-the-art（SOTA）VLA 模型**进行比较，但具体基线名称（如 RT-2、OpenVLA、Octo 等）在所提供摘要中未一一列出，需参阅正文。
- **实验维度**：同时考察**视觉-语言理解任务**与**精确闭环控制任务**，强调二者协同能力。

## 4. 资源与算力

- **算力说明**：所提供的 PDF 抽取内容（仅含摘要页）中**未明确提及**使用的 GPU 型号、数量以及训练时长等算力细节。
- 建议读者参考正文或附录以获取实验硬件配置。

## 5. 实验数量与充分性

- **实验覆盖**：摘要提及“仿真与真实世界实验”，并在多种任务与未见环境下进行对比，验证 EF-VLA 的泛化能力。
- **充分性评估**：
  - 优点：同时覆盖仿真与真实机器人、并区分 seen/unseen 环境，实验设计较为全面。
  - 局限：仅基于摘要信息无法判断具体的消融实验数量、统计显著性检验、不同任务数量等细节，需进一步阅读正文确认实验是否充分、客观与公平。

## 6. 主要结论与发现

- EF-VLA 通过早期融合机制显著提升了 VLA 模型在**机器人操作任务**上的表现。
- 在**未见环境中**展现出显著的泛化能力提升，验证了冻结 VLM、早期融合策略的有效性。
- 表明 CLIP 等对比预训练 VLM 蕴含的视觉-语言对齐能力对机器人控制具有重要价值，可被有效迁移到动作生成中。
- 为端到端、可泛化的机器人 VLA 模型提供了一种简洁且有效的架构方案。

## 7. 优点

- **方法新颖**：早期融合思路清晰，直接利用 CLIP 已有的跨模态对齐能力，避免重新学习。
- **冻结 VLM**：保持预训练视觉-语言模型的通用能力不被破坏，提升跨环境泛化性。
- **细粒度 token**：通过提取任务相关 token，降低策略网络的输入负担，可能提升控制精度与效率。
- **兼顾高层理解与底层控制**：在同一框架中同时支持语义理解与精确闭环动作输出。
- **实验较全面**：覆盖仿真与真实世界，并设置未见环境以验证泛化。

## 8. 不足与局限

- **PDF 受限**：当前仅可获得摘要，正文细节（如基线、消融、任务细节）无法完全核实。
- **算力信息缺失**：摘要未提供训练资源细节，复现成本与可扩展性难以评估。
- **对 CLIP 依赖**：方法性能依赖于 CLIP 等对比预训练 VLM 的对齐质量；若 VLM 在某些领域对齐能力不足，可能限制 EF-VLA 的适用性。
- **冻结 VLM 的双刃剑**：虽然避免破坏通用能力，但也意味着无法通过微调适配任务特定特征，可能在某些高度专业化任务中表现欠佳。
- **泛化性验证范围有限**：仅摘要中提到“unseen environments”，但未见环境的多样性、复杂度是否充分覆盖，尚需正文证据。
- **应用限制**：当前评估主要聚焦机器人操作，是否适用于 locomotion（运动控制）、导航等其他机器人领域未在摘要中体现。
- **偏差风险**：真实世界实验数量若较少，可能存在选择偏差与统计噪声。

（完）
