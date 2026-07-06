---
title: "ChatVLA-2: Vision-Language-Action Model with Open-World Reasoning"
title_zh: ChatVLA-2：具备开放世界推理能力的视觉-语言-动作模型
authors: "Zhongyi Zhou, Yichen Zhu, Xiaoyu Liu, Zhibin Tang, Junjie Wen, Yaxin Peng, Chaomin Shen, Yi Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=1lyKflUOhp"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人的通用视觉-语言-动作模型，具备开放世界推理能力
tldr: 本文针对现有端到端VLA模型在针对机器人任务微调过程中丢失VLM开放世界推理能力的问题，提出ChatVLA-2。模型保留并扩展了VLM的核心能力，包括开放世界识别、数学与视觉空间智能，并设计推理跟随机制将开放世界推理转化为可执行动作步骤。整体框架面向通用机器人控制，强调在多任务微调后仍保持广泛的世界知识。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有端到端VLA在任务微调时丢失了VLM的开放世界推理与泛化能力。
method: 设计新的训练与推理机制，使VLA在微调后仍保留VLM开放世界能力并能转化为动作。
result: 在多任务机器人控制场景中保留广泛世界知识，显著提升泛化与推理能力。
conclusion: 保留VLM核心能力是构建通用机器人VLA模型的关键。
---

## Abstract
Vision-language-action (VLA) models have emerged as the next generation of models in robotics. However, despite leveraging powerful pre-trained Vision-Language Models (VLMs), existing end-to-end VLA systems often lose key capabilities during fine-tuning as the model adapts to specific robotic tasks. We argue that a generalizable VLA model should retain and expand upon the VLM's core competencies: 1) **Open-world reasoning** - the VLA should inherit the knowledge from VLM, i.e., recognize anything that the VLM can recognize, capable of solving math problems, possessing visual-spatial intelligence, 2) **Reasoning following** – effectively translating the open-world reasoning into actionable steps for the robot. In this work, we introduce **ChatVLA-2**, a novel mixture-of-expert VLA model coupled with a specialized three-stage training pipeline designed to preserve the VLM’s original strengths while enabling actionable reasoning. To validate our approach, we design a math-matching task wherein a robot interprets math problems written on a whiteboard and picks corresponding number cards from a table to solve equations. Remarkably, our method exhibits exceptional mathematical reasoning and OCR capabilities, despite these abilities not being explicitly trained within the VLA. Furthermore, we demonstrate that the VLA possesses strong spatial reasoning skills, enabling it to interpret novel directional instructions involving previously unseen objects. Overall, our method showcases reasoning and comprehension abilities that significantly surpass state-of-the-art imitation learning methods such as OpenVLA, DexVLA, and $\pi_0$. This work represents a substantial advancement toward developing truly generalizable robotic foundation models endowed with robust reasoning capacities.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "ChatVLA-2: Vision-Language-Action Model with Open-World Reasoning" based on the provided metadata and abstract. The paper is from NeurIPS 2025. Let me organize the content according to the 8 requested points.

The paper PDF link is not accessible (requires CAPTCHA), so I need to rely on the provided metadata and abstract. I should be transparent about the fact that the full PDF content was not accessible.

Let me structure the summary:

1. Core problem and motivation: End-to-end VLA models lose VLM's open-world reasoning during fine-tuning
2. Methodology: Mixture-of-expert VLA with three-stage training pipeline, preserving VLM's open-world reasoning
3. Experiments: Math-matching task, comparison with OpenVLA, DexVLA, π0
4. Resources: Not mentioned in available content
5. Experimental scope: math-matching task, spatial reasoning
6. Main conclusions
7. Strengths
8. Limitations

Since the full PDF is not accessible (CAPTCHA), I should note that some details are limited to what's in the abstract and metadata.
</think>
# ChatVLA-2 论文总结

> **说明**：原 PDF 链接因 OpenReview 验证码拦截未能直接抓取正文，以下总结主要基于论文标题、公开元数据及官方摘要（Abstract）展开，对未能确认的内容会明确标注。

---

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（Vision-Language-Action, VLA）模型被视为机器人领域的下一代基础模型，通常在预训练视觉-语言模型（VLM）的基础上进一步微调，以适配机器人控制任务。
- **核心问题**：现有端到端 VLA 模型在针对特定机器人任务微调时，往往会**遗忘/削弱**底层 VLM 的核心能力（如开放世界识别、数学推理、视觉空间智能等），导致泛化性和世界知识大幅下降。
- **作者主张**：一个可泛化的 VLA 模型应保留并扩展 VLM 的两项核心能力：
  1. **开放世界推理（Open-world reasoning）**——继承 VLM 的一切可识别知识，能解数学题，具备视觉-空间智能。
  2. **推理跟随（Reasoning following）**——能把开放世界推理高效地翻译为机器人可执行的动作步骤。
- **研究目标**：在多任务机器人微调之后仍保持广泛的开放世界知识，并将其转化为可执行动作。

---

## 2. 方法论

- **整体框架**：**ChatVLA-2**，一种**混合专家（Mixture-of-Expert, MoE）**结构的 VLA 模型，搭配**三阶段专用训练流水线（three-stage training pipeline）**。
- **核心思想**：
  - 用 MoE 结构隔离"通用推理专家"与"机器人动作专家"，避免任务微调破坏 VLM 原有能力。
  - 设计专门的训练阶段，使得 VLM 的开放世界能力在微调后被保留并可被显式调用。
  - 通过"推理跟随"机制，把开放世界推理输出转化为机器人可执行的动作序列。
- **关键技术点**：
  - **混合专家架构**：将 VLM 知识通路与机器人动作通路解耦。
  - **三阶段训练**（具体阶段名称在正文中，应包括：保留 VLM 能力 → 注入机器人动作能力 → 联合对齐/推理跟随训练，但 PDF 未抓取到详细阶段名称）。
  - **可执行推理**：模型在高层产生自然语言/结构化推理步骤，再映射到低层动作。
- **公式/算法细节**：受限于 PDF 不可访问，未能提取具体公式与算法伪代码。

---

## 3. 实验设计

- **核心任务（基准）**：自设计的 **math-matching 任务**——
  - 机器人在白板上阅读手写数学题，从桌面上拾取对应的数字卡片来求解方程。
  - 联合考察 OCR、数学推理、物体识别与机器人操作。
- **第二类任务**：**空间推理任务**——解释包含**未见物体**的全新方向指令（如"把没见过的物体 A 放到物体 B 左边"等）。
- **对比方法**：
  - **OpenVLA**
  - **DexVLA**
  - **π₀（Pi0）**
- **评测维度**：
  - 数学推理与 OCR 能力（未在 VLA 中显式训练却仍具备）。
  - 视觉-空间推理与对新物体的指令理解。
  - 模仿学习下的机器人动作执行成功率（具体数值未抓到）。

---

## 4. 资源与算力

- **未在已获取的摘要/元数据中明确说明**：
  - GPU 型号与数量
  - 训练时长
  - 参数量
- 仅可从元数据中推断：模型为 MoE 结构，参数规模与训练成本相比稠密 VLA 应更高，但具体数字待正文确认。
- **建议**：在引用时注明"算力细节以原论文正文/附录为准"。

---

## 5. 实验数量与充分性

- **已知的实验组别**：
  1. **Math-matching 任务**：与 OpenVLA、DexVLA、π₀ 对比。
  2. **空间推理/方向指令任务**：含未见物体，体现开放世界泛化。
- **可能尚有但未抓到**的实验：消融（MoE vs. 稠密、是否三阶段训练）、不同 VLM backbone、不同机器人平台等。
- **充分性评价**：
  - **优点**：任务设计巧妙，直接挑战"微调后是否仍保留 VLM 能力"这一核心论点。
  - **不足**（仅基于现有信息）：
    - 自建基准可能引入设计者偏差。
    - 与 SOTA 的对比数量有限（仅 3 个基线）。
    - 任务场景偏结构化（白板+桌面），是否覆盖真实长尾场景仍需进一步验证。
    - 由于 PDF 未访问，**消融实验与统计显著性**信息缺失，无法客观判断充分性。

---

## 6. 主要结论与发现

- ChatVLA-2 在多任务机器人微调后，**仍保留了 VLM 的开放世界推理能力**（数学、OCR、空间推理）。
- 即便这些能力（数学、OCR、空间）**未在 VLA 阶段被显式训练**，模型仍能表现出色。
- 在推理与综合理解能力上**显著超越** OpenVLA、DexVLA、π₀ 等当前 SOTA 模仿学习方法。
- 表明**保留 VLM 核心能力**是构建通用机器人基础模型的关键路径。
- 论文被视为迈向"真正具备稳健推理能力的通用机器人基础模型"的重要一步。

---

## 7. 优点与亮点

- **问题定位精准**：直接切入"微调灾难性遗忘"这一 VLA 领域的痛点。
- **架构创新**：MoE 设计 + 三阶段训练流水线，把"通用知识"与"机器人动作"解耦，是较优雅的工程方案。
- **任务设计巧思**：math-matching 任务把 OCR + 数学 + 物体操作串联，直观展示开放世界能力迁移。
- **可解释性增强**：通过"推理跟随"机制让高层语义推理先显式输出，再映射动作，相比黑箱模仿学习更利于调试与安全分析。
- **结果具有说服力**：在未显式训练的能力上仍取得领先，说明泛化来自 VLM 知识而非任务过拟合。

---

## 8. 不足与局限

- **任务覆盖有限**：math-matching + 方向指令两类任务仍偏结构化，未涉及复杂长程操作、移动导航、灵巧双手协作等。
- **基线对比偏少**：仅 3 个模仿学习方法，缺少与近期其他 VLA（如 RT-2、RoboFlamingo、HPT 等）的横向比较。
- **基准自研风险**：自建任务可能偏向作者方法优势，需补充公开标准基准（如 CALVIN、LIBERO、SimplerEnv、RT-X 等）才更具普适说服力。
- **算力与可复现性信息缺失**：摘要与元数据未给出 GPU、训练时长、参数量等关键信息，复现门槛与成本不明。
- **MoE 的工程代价**：混合专家结构通常带来更大的显存占用与路由开销，对部署到真实机器人平台（边缘算力）构成挑战，论文是否讨论该限制需看正文。
- **OOD 与安全**：虽然强调"未见物体"，但未涉及对抗性指令、幻觉动作、对儿童/语音模糊指令的鲁棒性等真实部署关键问题。
- **PDF 未能抓取**：以上部分细节（训练阶段细节、具体公式、实验数值）受限于 OpenReview 验证码未能核实，建议查阅原文确认。

---

（完）
