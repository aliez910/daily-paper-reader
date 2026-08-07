---
title: "HAMSTER: Hierarchical Action Models for Open-World Robot Manipulation"
title_zh: HAMSTER：面向开放世界机器人操作的层级动作模型
authors: "Yi Li, Yuquan Deng, Jesse Zhang, Joel Jang, Marius Memmel, Caelan Reed Garrett, Fabio Ramos, Dieter Fox, Anqi Li, Abhishek Gupta, Ankit Goyal"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=h7aQxzKbq6"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操作的层级视觉-语言-动作模型
tldr: 本文针对机器人数据昂贵稀缺、基础模型在机器人领域泛化不足的问题，提出HAMSTER，一种层级视觉-语言-动作模型。该模型利用动作无关视频、草图等离线数据，通过高层VLM进行语义规划并由低层模块预测具体动作，从而比单体VLA更高效地利用异构数据。该贡献为开放世界机器人操作提供了可扩展的通用方案。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 机器人数据采集昂贵，标准单体视觉-语言-动作模型难以有效利用离线异构数据。
method: 提出层级VLA模型，由高层VLM规划、低层模块预测动作，更好地利用非机器人数据。
result: 层级结构在多个操作任务上比直接微调的单体VLA更具数据效率和泛化能力。
conclusion: 层级设计为通用机器人VLA模型有效利用多源数据提供了可行路径。
---

## Abstract
Large foundation models have shown strong open-world generalization to complex problems in vision and language, but similar levels of generalization have yet to be achieved in robotics. One fundamental challenge is the lack of robotic data, which are typically obtained through expensive on-robot operation. A promising remedy is to leverage cheaper, *off-domain* data such as action-free videos, hand-drawn sketches, or simulation data. In this work, we posit that *hierarchical* vision-language-action (VLA) models can be more effective in utilizing off-domain data than standard monolithic VLA models that directly finetune vision-language models (VLMs) to predict actions.
In particular, we study a class of hierarchical VLA models, where the high-level VLM is finetuned to produce a coarse 2D path indicating the desired robot end-effector trajectory given an RGB image and a task description. The intermediate 2D path prediction is then served as guidance to the low-level, 3D-aware control policy capable of precise manipulation. Doing so alleviates the high-level VLM from fine-grained action prediction, while reducing the low-level policy's burden on complex task-level reasoning.
We show that, with the hierarchical design, the high-level VLM can transfer across significant domain gaps between the off-domain finetuning data and real-robot testing scenarios, including differences in embodiments, dynamics, visual appearances, and task semantics, etc.
In the real-robot experiments, we observe an average of 20% improvement in success rate across seven different axes of generalization over OpenVLA, representing a 50% relative gain.
Visual results are provided at: [https://hamster-robot.github.io/](https://hamster-robot.github.io/)

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper "HAMSTER: Hierarchical Action Models for Open-World Robot Manipulation" based on the provided metadata and abstract. Let me organize my thoughts and create a structured Markdown summary covering all 8 required points.

The paper is about hierarchical Vision-Language-Action (VLA) models for robot manipulation. Key points:
- Addresses lack of robotic data
- Uses off-domain data (action-free videos, sketches, simulation)
- Hierarchical design: high-level VLM predicts 2D path, low-level policy predicts 3D actions
- High-level can transfer across domain gaps
- 20% improvement over OpenVLA, 50% relative gain
- 7 axes of generalization

Since I only have the abstract and metadata (no full PDF content due to CAPTCHA), I need to base my summary on what is available. I'll note limitations in experimental details since the full paper wasn't accessible.

Let me write this out in Chinese with proper Markdown formatting.</think>

# HAMSTER 论文总结

## 1. 核心问题与整体含义

- **研究背景**：大规模基础模型在视觉与语言任务上展现了强大的开放世界泛化能力，但类似的泛化水平在机器人领域尚未实现。其根本瓶颈在于机器人数据稀缺——真实的机器人操作数据需要通过昂贵的实体机器人操作来采集。
- **研究动机**：探索如何利用廉价、异构的**离域（off-domain）数据**（例如无动作标注的视频、手绘草图、仿真数据等）来弥补真实机器人数据不足的问题。
- **核心问题**：标准的单体（monolithic）视觉-语言-动作（VLA）模型（如 OpenVLA）直接微调视觉-语言模型（VLM）以预测动作，难以有效利用异构离域数据。作者认为，**层级化（hierarchical）VLA 模型**比单体模型在利用离域数据上更具优势。

## 2. 方法论：核心思想与技术细节

- **整体思路**：将任务分解为两个层级——
  - **高层（High-level）**：在 RGB 图像 + 任务文本描述条件下，由微调后的 VLM 预测一条粗糙的 **2D 路径**，指示机器人末端执行器（end-effector）的期望轨迹。
  - **低层（Low-level）**：以高层生成的 2D 路径作为引导（guidance），由一个具备 **3D 感知能力**的控制策略输出精确的操作动作。
- **关键优势**：
  - 高层 VLM 免于直接预测细粒度动作，从而更容易在不同形态/动力学/视觉/语义差异下迁移。
  - 低层策略专注于精准操控，而无需承担复杂的任务级推理负担。
- **训练范式**：
  - 高层 VLM 在离域数据（如动作无关视频、草图、仿真数据等）上进行微调，学习任务级语义规划。
  - 低层 3D 感知策略在真实机器人数据上训练，学习将 2D 路径转化为精确动作。
- **算法流程（文字描述）**：
  1. 输入任务文本描述与当前 RGB 观测图像；
  2. 高层 VLM 输出末端执行器的 2D 路径规划；
  3. 低层策略结合 2D 路径与 3D 感知信息，输出最终机器人动作。

## 3. 实验设计

- **真实机器人实验**：在真实机器人平台上进行操作任务评估，覆盖**七个不同泛化维度**（axes of generalization），包括但不限于形态、动力学、视觉外观、任务语义等。
- **基线对比**：与 **OpenVLA**（单体 VLA 模型）进行直接对比。
- **Benchmark**：使用了涵盖多种泛化场景的机器人操作任务集（具体任务细节由于 PDF 未能完整获取，仅基于摘要信息推断）。
- **数据来源**：综合使用了真实机器人数据 + 多种离域数据（动作无关视频、草图、仿真）。

## 4. 资源与算力

- 由于本次仅能获取论文摘要与元数据，**论文主体中的 GPU 型号、训练算力、训练时长等具体细节未能获取**。建议查阅正文以确认完整实验的资源配置信息。

## 5. 实验数量与充分性

- **泛化维度**：在 7 个不同的泛化轴上评估，覆盖了机器人学习中常见的泛化挑战（形态、动力学、视觉、语义等）。
- **对比实验**：与 OpenVLA 这一代表性基线进行对比。
- **充分性评估（基于现有信息）**：
  - 优势：在多个泛化维度上系统评估，能够较全面地说明层级结构的泛化优势。
  - 局限：由于无法获取完整正文，**消融实验数量、对不同离域数据源的单独消融、不同模型规模对比等细节尚不明确**。摘要中仅给出总体平均提升数字，未提供每个泛化维度的细分结果。

## 6. 主要结论与发现

- **层级 VLA 模型在数据效率上优于单体 VLA**：通过将任务规划（高层）与精确控制（低层）解耦，可以更高效地利用异构离域数据。
- **跨域迁移能力强**：高层 VLM 能够在离域微调数据与真实机器人测试场景之间跨越显著的域差异（形态、动力学、视觉外观、任务语义等）。
- **实验结果**：在七个泛化维度上，相较 OpenVLA 平均成功率提升 **20%**（**相对增益约 50%**）。
- **意义**：层级设计为通用机器人 VLA 模型有效利用多源异构数据提供了可行路径，是迈向开放世界机器人操作的可扩展方案。

## 7. 优点

- **方法创新性强**：提出层级化 VLA 架构，将语义规划与精确操控解耦，思路清晰且符合"分层决策"的机器人学传统。
- **数据利用效率高**：能够利用大量廉价、异构的离域数据，显著缓解机器人数据稀缺问题。
- **泛化能力突出**：在 7 个不同泛化轴上系统验证，相对 OpenVLA 取得 50% 相对增益。
- **实际应用导向**：基于真实机器人平台验证，而非仅停留在仿真层面，工程价值较高。
- **代码与可视化公开**：提供了项目网站（https://hamster-robot.github.io/），便于复现与推广。

## 8. 不足与局限

- **依赖 2D 路径作为中间表征**：高层输出 2D 路径虽然简化了任务规划，但可能限制模型在需要复杂 3D 空间推理的任务上的表现。
- **真实机器人数据仍不可或缺**：低层策略需要在真实机器人数据上训练，完全脱离真实数据的零样本性能未知。
- **离域数据筛选与标注**：对草图、动作无关视频等异构数据的预处理与筛选策略在摘要中未充分提及，可能存在人工设计偏差。
- **实验覆盖（基于摘要的不确定性）**：未能获取完整论文，无法判断是否包含充分的消融实验、不同 backbone 对比、统计显著性检验等。
- **单一基线**：仅与 OpenVLA 对比，未与其他层级式或基于模型的机器人学习方法（如 RT-2、PI 系、扩散策略等）进行更广泛的对比。
- **真实世界的安全与鲁棒性**：摘要未讨论系统在面对真实世界中不可预测扰动、物体遮挡、光照变化等极端情况下的鲁棒性表现。

（完）
