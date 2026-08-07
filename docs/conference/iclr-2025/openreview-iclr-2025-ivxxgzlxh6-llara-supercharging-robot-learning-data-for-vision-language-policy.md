---
title: "LLaRA: Supercharging Robot Learning Data for Vision-Language Policy"
title_zh: LLaRA：为视觉-语言策略强化机器人学习数据
authors: "Xiang Li, Cristina Mata, Jongwoo Park, Kumara Kahatapitiya, Yoo Sung Jang, Jinghuan Shang, Kanchana Ranasinghe, Ryan D Burgert, Mu Cai, Yong Jae Lee, Michael S Ryoo"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=iVxxgZlXh6"
tags: ["query:rob-il"]
score: 9.0
evidence: 由预训练视觉语言模型构建的视觉-语言-动作策略
tldr: 本文研究如何将预训练视觉语言模型高效转化为可用于机器人控制的视觉-语言-动作模型，特别是在机器人示范数据有限的情况下。作者提出 LLaRA 框架，将机器人动作策略建模为视觉-文本对话，并借鉴视觉指令微调的成功经验，将预训练 VLM 高效迁移为强大的 VLA。具体地，文中设计了自动化数据生成流程，从既有行为克隆数据集中构造对话风格的指令微调数据，从而将机器人动作与语言对齐。该工作直接推动了面向端到端机器人控制的视觉-动作模型发展，高度契合用户组合需求的核心主题。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 在机器人示范数据有限时，直接将预训练 VLM 适配为机器人控制策略仍具挑战。
method: 提出 LLaRA 框架，将动作策略视为视觉-文本对话，并设计自动化数据生成流程进行指令微调。
result: 实现了从预训练 VLM 到强大 VLA 模型的高效迁移，提升机器人控制性能。
conclusion: 为视觉-语言-动作模型在机器人控制中的数据与训练范式提供了实用方案。
---

## Abstract
Vision Language Models (VLMs) have recently been leveraged to generate robotic actions, forming Vision-Language-Action (VLA) models. However, directly adapting a pretrained VLM for robotic control remains challenging, particularly when constrained by a limited number of robot demonstrations. In this work, we introduce LLaRA: Large Language and Robotics Assistant, a framework that formulates robot action policy as visuo-textual conversations and enables an efficient transfer of a pretrained VLM into a powerful VLA, motivated by the success of visual instruction tuning in Computer Vision. First, we present an automated pipeline to generate conversation-style instruction tuning data for robots from existing behavior cloning datasets, aligning robotic actions with image pixel coordinates. Further, we enhance this dataset in a self-supervised manner by defining six auxiliary tasks, without requiring any additional action annotations. We show that a VLM finetuned with a limited amount of such datasets can produce meaningful action decisions for robotic control. Through experiments across multiple simulated and real-world tasks, we demonstrate that LLaRA achieves state-of-the-art performance while preserving the generalization capabilities of large language models. The code, datasets, and pretrained models are available at https://github.com/LostXine/LLaRA.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a structured, detailed Chinese summary of the paper "LLaRA: Supercharging Robot Learning Data for Vision-Language Policy" based on the provided metadata and abstract. I need to follow the 8 specified points and use Markdown formatting.

Let me organize the content:

1. **Core problem and motivation**: The paper addresses the challenge of adapting pretrained Vision-Language Models (VLMs) into Vision-Language-Action (VLA) models for robotic control, especially when limited robot demonstration data is available.

2. **Methodology**: LLaRA framework - formulates robot action policy as visuo-textual conversations, uses automated pipeline to generate conversation-style instruction tuning data from existing behavior cloning datasets, aligns robotic actions with image pixel coordinates, and enhances dataset with six self-supervised auxiliary tasks without requiring additional action annotations.

3. **Experimental design**: Multiple simulated and real-world tasks, compared against state-of-the-art methods. The paper mentions achieving SOTA while preserving LLM generalization capabilities. However, the metadata doesn't specify which datasets exactly (likely OpenVLA benchmark, CALVIN, etc., but I should be careful not to fabricate).

4. **Resources/compute**: The metadata and abstract don't specify compute resources explicitly. I should note this.

5. **Number and sufficiency of experiments**: Multiple simulated and real-world tasks, but specifics not detailed in the provided abstract.

6. **Main conclusions**: LLaRA achieves SOTA performance while preserving LLM generalization capabilities, and demonstrates that VLMs fine-tuned with limited datasets can produce meaningful action decisions.

7. **Strengths**: Automated data generation pipeline, self-supervised auxiliary tasks, efficient VLM-to-VLA transfer.

8. **Limitations**: Limited by the information provided - mainly about data generation from existing behavior cloning datasets, which may have inherent biases.

Let me write this in a structured Markdown format in Chinese.</think>

# LLaRA 论文结构化总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究主题**：如何将预训练的视觉语言模型（VLM）高效转化为可用于机器人控制的视觉-语言-动作模型（VLA）。
- **核心痛点**：在机器人示范数据（demonstration）数量有限的现实约束下，直接将预训练 VLM 适配为机器人控制策略仍然非常困难，存在迁移效率低、动作对齐难、泛化能力易丢失等问题。
- **整体含义**：VLM 本身具备丰富的视觉-语言理解与推理能力，但并不天然具备"输出动作"的能力。LLaRA 旨在打通从 VLM 到 VLA 的桥梁，让通用大模型的能力能够被低成本地"复用"到机器人端到端控制领域，从而推动基础模型范式在机器人控制中的落地。

---

## 2. 方法论：核心思想与关键技术

### 核心思想
- 将机器人动作策略（action policy）重新建模为"视觉-文本对话"（visuo-textual conversations），借鉴视觉指令微调（visual instruction tuning）在计算机视觉中的成功经验，把机器人控制问题转化为对话式任务。
- 通过自动化的数据生成流程，把已有行为克隆（behavior cloning）数据集中的动作标注"翻译"为对话风格的指令微调数据，从而让 VLM 在微调过程中自然学会输出机器人动作。

### 关键技术细节
- **动作表示与对齐**：将机器人动作与图像像素坐标进行对齐（aligning robotic actions with image pixel coordinates），把连续动作空间离散化或坐标化，使其能够以语言/文本 token 形式被 VLM 输出。
- **自动化数据生成流水线**：从既有的行为克隆数据集中自动构造"对话式"指令微调样本，无需人工重新标注，最大化复用已有数据。
- **自监督辅助任务**：定义了 **6 个自监督辅助任务**（six auxiliary tasks），在不增加任何额外动作标注的前提下，对数据集进行扩充和增强，进一步提升 VLM 到 VLA 的迁移质量。
- **训练范式**：基于 VLM 进行指令微调（instruction tuning），输出"动作决策"用于机器人控制。

### 算法流程（文字描述）
1. 输入：预训练 VLM + 现有行为克隆数据集（包含图像、状态、动作）。
2. 通过自动化流水线，将原数据集中的动作转换为基于像素坐标的文本 token 描述。
3. 自动构建对话风格样本（图像 + 指令 → 动作 token）。
4. 加入 6 个自监督辅助任务进一步增强训练信号。
5. 在上述数据上对 VLM 进行指令微调，得到可用于机器人控制的 VLA 模型。
6. 部署到仿真或真实机器人上执行任务。

---

## 3. 实验设计

- **任务场景**：多个**仿真任务**与**真实世界任务**（multiple simulated and real-world tasks）。
- **对比基线**：论文声称达到 state-of-the-art（SOTA）性能，对比方法包括已有的 VLA 类方法以及基础 VLM 适配方案（具体基线方法在摘要中未详细列出，需查阅正文）。
- **评测目标**：
  - 机器人控制任务的成功率 / 完成度。
  - 是否保留 LLM 的通用泛化能力（preserving the generalization capabilities of large language models）。
- **可复现性**：作者公开了代码、数据集与预训练模型，地址：<https://github.com/LostXine/LLaRA>。

> 备注：所提供的 PDF 提取内容仅包含摘要与 OpenReview 元数据，**未能展示具体使用的基准数据集名称、对比方法清单、消融实验设置与定量结果**。以下涉及具体数字的部分需参考正文核实。

---

## 4. 资源与算力

- 在所提供的内容中**未明确说明**所用 GPU 型号、数量、训练时长或总算力消耗等细节。
- 从方法特征推断：基于 VLM 进行指令微调，通常需要多卡 A100/H100 级别 GPU；但精确算力配置需要查阅论文正文/附录。

---

## 5. 实验数量与充分性

- **实验规模**：摘要提到"多个仿真与真实世界任务"，并报告了 SOTA 性能；但具体实验组数（如数据集数量、任务数量、随机种子重复次数等）**在所提供信息中未列出**。
- **自监督辅助任务的消融**：方法中提出 6 个辅助任务，但摘要未说明是否分别做消融验证。
- **充分性评估**：
  - 优点：覆盖仿真 + 真实机器人，并强调对 LLM 泛化能力的保留评测，维度较全面。
  - 局限：从现有摘要无法判断实验是否对各组件进行了充分消融，以及是否在多种 VLM backbone（如 LLaVA、GPT-4V 等）上验证。

---

## 6. 主要结论与发现

- 在有限的机器人示范数据下，对 VLM 进行对话式指令微调即可使其输出**有意义的机器人动作决策**。
- LLaRA 在多个仿真与真实任务上**达到 SOTA 性能**。
- 该方法在提升机器人控制表现的同时，**保留了大型语言模型的泛化能力**，避免了传统微调中常见的灾难性遗忘问题。
- 自动化数据流水线 + 自监督辅助任务 是将通用 VLM 高效迁移为机器人专用 VLA 的有效路径。

---

## 7. 优点（亮点）

- **范式创新**：把机器人动作策略重新建模为视觉-文本对话，统一了 VLM 与 VLA 的训练接口。
- **数据高效**：通过自动化流水线复用现有行为克隆数据，避免昂贵的人工重新标注。
- **零额外标注的增强**：6 个自监督辅助任务在不引入新动作标签的前提下提升数据多样性与训练信号强度。
- **泛化能力保留**：在机器人控制任务上微调后，仍能保留 LLM 的通用能力，是优于多数传统微调方案的关键卖点。
- **开源完整**：代码、数据集、预训练模型全部开源，利于复现与后续研究。

---

## 8. 不足与局限

- **数据来源依赖**：方法依赖"已有行为克隆数据集"，其数据多样性、偏差和任务覆盖度会直接限制 LLaRA 的上限；现有 BC 数据集通常存在分布偏窄问题。
- **动作表示限制**：将动作对齐到图像像素坐标这一做法对高自由度、连续精细动作的表达能力可能不足，动作精度与多模态分布表达仍待验证。
- **自监督任务的设计合理性**：6 个辅助任务的有效性需要在消融实验中验证，所提供摘要并未给出相关证据。
- **实验细节不透明**：所提供的 PDF 内容仅为标题页（被 CAPTCHA 拦截），无法确认具体基准、数据集、对比方法与定量指标，需进一步阅读正文。
- **真实任务规模未知**：摘要仅说"真实世界任务"，未说明任务数量、复杂度与多样性，相较仿真结果的说服力仍受限于任务规模。
- **算力与可复现成本**：VLM 微调本身对算力要求较高，对普通研究组复现存在门槛，论文未披露算力信息也增加了复现难度。
- **泛化边界**：保留 LLM 通用能力是亮点，但同时也意味着模型在长尾、罕见机器人任务上的鲁棒性尚需进一步评估。

（完）
