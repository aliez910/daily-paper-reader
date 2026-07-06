---
title: Enhancing LLM Planning for Robotics Manipulation through Hierarchical Procedural Knowledge Graphs
title_zh: 通过层次化程序性知识图谱增强机器人操控的LLM规划
authors: "Jiacong Zhou, Jiaxu Miao, Xianyun Wang, Jun Yu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=8LO0vLRXpz"
tags: ["query:rob-il"]
score: 4.0
evidence: 基于LLM的层次化知识图谱用于复杂机器人操控规划，非模仿学习
tldr: 大语言模型在简单抓放任务中表现出色，但在复杂操控规划中因程序性知识不准而受限，且部署大规模LLM能耗高。本文构建层次化程序性知识图谱(HP-KG)，以结构化知识增强小规模LLM的复杂机器人规划能力。该工作涉及机器人操控任务与控制，但并非基于模仿学习或视觉到动作映射。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有LLM在复杂机器人操控规划中存在程序性知识不准且模型规模过大的问题。
method: 提出层次化程序性知识图谱为小规模LLM提供结构化程序知识以完成复杂操控规划。
result: 提升了LLM在复杂操控任务中的规划准确性并降低了对大模型的依赖。
conclusion: 为LLM驱动的机器人操控规划提供了一种高效且结构化的知识增强途径。
---

## Abstract
Large Language Models (LLMs) have shown the promising planning capabilities for robotic manipulation, which advances the development of embodied intelligence significantly. However, existing LLM-driven robotic manipulation approaches excel at simple pick-and-place tasks but are insufficient for complex manipulation tasks due to inaccurate procedural knowledge. Besides, for embodied intelligence, equipping a large scale LLM is energy-consuming and inefficient, which affects its real-world application.
To address the above problems, we propose Hierarchical Procedural Knowledge Graphs (\textbf{HP-KG}) to enhance LLMs for complex robotic planning while significantly reducing the demand for LLM scale in robotic manipulation. 
Considering that the complex real-world tasks require multiple steps, and each step is composed of robotic-understandable atomic actions, we design a hierarchical knowledge graph structure to model the relationships between tasks, steps, and actions. This design bridges the gap between human instructions and robotic manipulation actions. To construct HP-KG, we develop an automatic knowledge graph construction framework powered by LLM-based multi-agents, which eliminates costly manual efforts while maintaining high-quality graph structures. 
The resulting HP-KG encompasses over 40k activity steps across more than 6k household tasks, spanning diverse everyday scenarios. Extensive experiments demonstrate that small scale LLMs (7B) enhanced by our HP-KG significantly improve the planning capabilities, which are stronger than 72B LLMs only. Encouragingly, our approach remains effective on the most powerful GPT-4o model.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper about "Enhancing LLM Planning for Robotics Manipulation through Hierarchical Procedural Knowledge Graphs". Let me analyze the provided content and structure my response according to the 8 points requested.

From the metadata and abstract, I can extract:
- Title: 通过层次化程序性知识图谱增强机器人操控的LLM规划
- Authors: Jiacong Zhou, Jiaxu Miao, Xianyun Wang, Jun Yu
- Date: 2025-09-18
- Conference: NeurIPS 2025
- Score: 4.0

Key information from abstract:
1. Problem: LLMs perform well at simple pick-and-place tasks but struggle with complex manipulation due to inaccurate procedural knowledge. Also, large-scale LLMs are energy-consuming for embodied intelligence.
2. Method: Proposes Hierarchical Procedural Knowledge Graphs (HP-KG) with hierarchical structure (tasks → steps → atomic actions). Automatic construction framework using LLM-based multi-agents. Contains 40k+ activity steps across 6k+ household tasks.
3. Results: 7B LLMs with HP-KG outperform 72B LLMs. Also effective on GPT-4o.

I need to note that the PDF content extraction failed (CAPTCHA page), so I need to base my summary on the metadata and abstract that was provided. I should be honest about what information is available and what is not.

Let me structure the response with detailed Chinese summary following the 8 requested points.
</think>
# 论文总结：通过层次化程序性知识图谱增强机器人操控的LLM规划

> **说明**：原始 PDF 文本因 OpenReview 的 CAPTCHA 验证未能成功提取，以下总结基于论文元数据（标题、摘要、标签等）综合整理而成，部分细节（具体数据集名称、消融实验细节、算力信息等）在现有材料中未明确给出，已在相应位置注明。

---

## 1. 核心问题与整体含义（研究动机和背景）

- **核心痛点**：现有 LLM 驱动的机器人操控方法在**简单 pick-and-place（抓取-放置）任务**上表现良好，但面对**复杂操控任务**时表现不足，根本原因是其**程序性知识（procedural knowledge）不够准确**。
- **现实约束**：将**大规模 LLM**（如 70B+ 级别）部署到机器人/具身智能平台上**能耗高、效率低**，不利于真实场景落地。
- **研究目标**：在小规模 LLM 基础上，通过引入**结构化、层次化的领域知识**，让模型在不依赖巨大参数量的前提下获得可靠的复杂任务规划能力。

---

## 2. 方法论：核心思想与关键技术

- **核心思想**：提出 **HP-KG（Hierarchical Procedural Knowledge Graphs，层次化程序性知识图谱）**，将人类指令与机器人可执行的原子动作通过三层结构桥接起来：
  - **任务层（Tasks）**：来自人类自然语言层面的高层目标。
  - **步骤层（Steps）**：完成任务所需的中粒度子流程。
  - **动作层（Atomic Actions）**：机器人可直接理解的低层原子操作。
- **关键技术细节**：
  1. **层次化知识图谱结构建模**：在任务—步骤—动作三层间建立语义关系，使 LLM 检索时能获得**与当前上下文最相关的程序性知识**。
  2. **基于 LLM 多智能体（multi-agents）的自动构建框架**：用 LLM 充当多个角色协同完成知识图谱的抽取、校验与组织，从而**避免昂贵的人工标注**，同时保证图谱质量。
  3. **图谱规模**：覆盖 **6,000+ 家庭任务 / 40,000+ 活动步骤**，涵盖多样化的日常场景。
  4. **模型搭配方式**：将 HP-KG 作为外部知识增强模块，注入到小规模 LLM（如 7B）的规划流程中。

---

## 3. 实验设计

- **场景与覆盖范围**：
  - 主要面向**家庭日常操控任务**（household tasks），是具身操控中较为复杂、有代表性的设定。
  - 强调**多步骤复杂任务**而非单一抓放。
- **Benchmark**：
  - 摘要中未明确给出具体 benchmark 名称（推测可能涉及 ALFRED、RT-1/RT-2 评测协议或自建数据集，但**原文未在可用文本中说明**）。
  - 评测维度应包含**任务规划成功率、步骤合理性、动作可执行性**等。
- **对比方法**：
  - **小规模基线 LLM（7B）**：未增强版本。
  - **大规模 LLM（如 72B 量级）**：验证 HP-KG 增强后的小模型能否反超大模型。
  - **GPT-4o**：最强闭源模型作为上限参照，验证方法在**不同模型规模/类别上的通用性**。
- **对比基线的具体名单、prompt 模板、评估脚本等细节在提供的文本中未给出**。

---

## 4. 资源与算力

- 提供的论文文本中**未明确说明**：
  - 训练/推理所用 GPU 型号与数量。
  - 训练时长、token 数量、显存占用。
  - 微调 vs. 仅检索增强（in-context retrieval）的算力差异。
- **可推断信息**：
  - 由于强调的是**知识增强而非重训**，主流程应**无需大规模 GPU 集群**，仅需对 7B 模型做推理 + 向量化知识检索，整体算力门槛相对较低。
  - HP-KG 构建阶段使用了**多智能体 LLM 调用**（可能调用 GPT-4o 等模型），其 API 成本与 token 消耗在原文中未披露。

---

## 5. 实验数量与充分性

- **从摘要可推断的实验维度**：
  - 不同规模 LLM 对比：7B（增强） vs. 72B（无增强）。
  - 不同模型族对比：开源小模型 vs. GPT-4o（最强模型）。
  - 在 HP-KG 存在/不存在的消融思路（虽然摘要未直接写明 ablation，逻辑上应包含）。
- **可能存在的不足**：
  - **未在摘要中详细说明**消融实验数量、随机种子数、统计显著性检验。
  - **benchmark 的多样性**仅从"6k+ 任务"可推断任务规模，但**是否跨真实机器人平台、是否包含 sim-to-real 评估**等信息在提供的材料中不可知。
  - **公平性**：由于强调"7B + KG > 72B"，需关注 prompt 设计、知识检索质量、评测脚本是否对小模型更友好；这些细节需要查阅正文确认。

---

## 6. 主要结论与发现

- **核心结论**：
  1. 引入 HP-KG 后，**7B 小模型**的规划能力**显著超过 72B 大模型**，验证了"**结构化知识 > 盲目堆参数**"的思路。
  2. 该方法在 **GPT-4o 上依然有效**，说明 HP-KG 是一种**模型无关的通用增强手段**。
  3. 层次化结构有效弥合了**人类高层指令**与**机器人原子动作**之间的**语义鸿沟**。
- **实践意义**：为机器人操控场景提供了一条**低算力、可扩展**的 LLM 规划路径。

---

## 7. 优点与亮点

- **结构化层次建模**：任务—步骤—动作三层结构清晰，对应人类认知与机器人执行的双重粒度，**可解释性强**。
- **自动化构建**：基于 LLM 多智能体的图谱构建方式**降低人工成本**，易扩展到更多领域。
- **知识图谱规模可观**：6k+ 任务、40k+ 步骤，**覆盖广度**较好。
- **小模型反超大模型**：在能耗/效率敏感的具身智能场景下具有**重要实用价值**。
- **模型无关性**：在开源小模型与 GPT-4o 上均有效，**泛化潜力**较好。

---

## 8. 不足与局限

- **信息获取受限**：PDF 文本未成功提取，**无法确认**具体的实验细节、统计显著性、跨平台泛化能力等。
- **任务域偏单一**：当前以**家庭日常任务**为主，对工业、室外、非结构化场景的迁移性尚未在现有材料中说明。
- **知识图谱质量依赖 LLM**：多智能体构建流程本身**依赖大模型输出质量**，可能引入幻觉/错误传播风险。
- **更新与维护成本**：现实任务不断演变，**HP-KG 的持续更新机制**在摘要中未涉及。
- **真实机器人部署评估缺失**：是否在**真实物理机器人**上做了端到端执行验证，提供的材料中未明确说明。
- **能耗节省仅为定性论证**：虽强调"小模型更省能"，但**缺乏具体的能耗/时延/碳排放定量对比**。
- **检索增强而非真正"学习"**：本质上是外部知识检索，可能在**未见过的长尾任务**上仍存在知识覆盖不足的问题。

（完）
