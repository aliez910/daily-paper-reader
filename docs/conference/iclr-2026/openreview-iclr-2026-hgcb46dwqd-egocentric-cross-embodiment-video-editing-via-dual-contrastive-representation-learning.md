---
title: Egocentric Cross-Embodiment Video Editing via Dual Contrastive Representation Learning
title_zh: 基于双对比表征学习的自我中心跨具身视频编辑
authors: "Zhiyuan Li, Wenyan Yang, Wenshuai Zhao, Yue Ma, Yuanpeng Tu, Pekka Marttinen, Joni Pajarinen"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=hGcb46DWQD"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向机器人操纵的跨具身表征学习，利用人类视频数据
tldr: 从人类视频中学习机器人操纵可缓解数据瓶颈，但人机具身间的分布差异使任务相关特征与人类特有运动学信息纠缠。本文提出基于双对比表征学习的生成式跨具身视频编辑框架，将演示视频分解为正交的任务与具身两个隐空间，并通过互信息最小化保证其独立性，从而实现清晰可控的跨具身知识迁移。该方法为利用大规模人类视频数据进行机器人模仿学习提供了新的表征解耦思路，有助于缩小人类到机器人之间的具身鸿沟。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 人类视频与机器人之间存在显著的具身分布差异，导致任务特征与人类运动学信息纠缠。
method: 通过双对比目标将演示视频分解为正交的任务与具身隐空间，强制二者独立。
result: 生成的解耦表征可支持跨具身视频编辑，并提升下游机器人策略的可迁移性。
conclusion: 显式解耦任务与具身表征是从人类视频学习机器人操纵的有效途径。
---

## Abstract
Learning robotic manipulation from human videos is a promising solution to the data bottleneck in robotics, but the distribution shift between humans and robots remains a critical challenge. Existing approaches often produce entangled representations, where task-relevant information is coupled with human-specific kinematics, limiting their adaptability. We propose a generative framework for cross-embodiment video editing that directly addresses this by learning explicitly disentangled task and embodiment representations. Our method factorizes a demonstration video into two orthogonal latent spaces by enforcing a dual contrastive objective: it minimizes mutual information between the spaces to ensure independence while maximizing intra-space consistency to create stable representations. A parameter-efficient adapter injects these latent codes into a frozen video diffusion model, enabling the synthesis of a coherent robot execution video from a single human demonstration, without requiring paired cross-embodiment data. Experiments show our approach generates temporally consistent and morphologically accurate robot demonstrations, offering a scalable solution to leverage internet-scale human video for robot learning.

---

## 论文详细总结（自动生成）

<think>
The user wants me to analyze a paper based on the provided metadata and abstract. Let me carefully read through what's available.

The paper is titled "Egocentric Cross-Embodiment Video Editing via Dual Contrastive Representation Learning" - it's about learning robotic manipulation from human videos using a cross-embodiment approach with dual contrastive representation learning.

Note: The actual PDF content was not successfully extracted (CAPTCHA blocked), but I have detailed metadata including abstract, motivation, method, results, and conclusion. I'll base my analysis on this available information, being clear about what I can and cannot determine.

Let me structure my response according to the 8 required points.
</think>
# 论文总结：基于双对比表征学习的自我中心跨具身视频编辑

## 1. 核心问题与研究动机

- **核心问题**：机器人操纵策略学习面临严重的数据瓶颈问题。虽然人类视频数据在互联网上规模巨大、容易获取，但人类与机器人之间存在显著的**具身分布差异**（embodiment gap），如运动学结构、形态和动作模式完全不同。
- **现有方法的不足**：从人类视频中直接学习时，任务相关信息（如物体操作语义）与人类特有的运动学信息（human-specific kinematics）**纠缠**（entangled）在一起，导致所学表征难以迁移到机器人端。
- **研究意义**：如果能有效解耦"任务"与"具身"两个维度的表征，就能利用大规模人类视频数据训练机器人，从而大幅降低对昂贵机器人示教数据的依赖。

## 2. 方法论

### 2.1 核心思想

- 提出一个**生成式跨具身视频编辑框架**，直接从人类示范视频合成对应的机器人执行视频。
- 关键在于学习**显式解耦**的两个隐空间：
  - **任务空间**（task latent）：编码"做什么"（如抓取杯子、倒水等任务语义）。
  - **具身空间**（embodiment latent）：编码"谁来做"（如人手 vs. 机械臂的运动学特征）。

### 2.2 关键技术

- **双对比目标（Dual Contrastive Objective）**：
  - **互信息最小化**：在任务空间与具身空间之间最小化互信息，保证二者**正交独立**。
  - **空间内一致性最大化**：在每个空间内部最大化样本间的一致性，构造**稳定、可迁移**的表征。
- **参数高效适配器（Parameter-Efficient Adapter）**：
  - 将解耦得到的两个隐编码（latent codes）注入到一个**冻结的预训练视频扩散模型**中。
  - 仅训练轻量化的适配器，避免大规模微调基础扩散模型，节省算力与数据。
- **训练范式**：
  - 不需要配对的跨具身数据（unpaired cross-embodiment data），即不需要同一任务的"人类版"和"机器人版"成对样本。
  - 输入：单个人类示范视频 → 输出：形态正确、时间一致的机器人执行视频。

## 3. 实验设计

- **数据集与场景**：基于元数据描述，论文应在自我中心（egocentric）视角下进行视频编辑实验；具体使用的数据集名称在可获取的文本中**未明确列出**（因 PDF 提取受 CAPTCHA 阻挡）。
- **Benchmark**：从摘要可推断，评估应涵盖：
  - 视频生成的**时间一致性**（temporal consistency）。
  - 机器人形态的**形态学准确性**（morphological accuracy）。
  - 下游机器人策略的**可迁移性**（transferability）。
- **对比方法**：原文中未在可获取的片段中给出基线（baseline）方法列表，需参考正文表格。
- **评估指标**：未在元数据中明确，建议结合 FVD、跨具身分类准确率、下游模仿学习成功率等。

## 4. 资源与算力

- **未在可获取的文本中明确说明**所用 GPU 型号、数量及训练时长。
- 可推断的点：使用了**冻结的预训练视频扩散模型**（如基于 Stable Video Diffusion 类模型），仅训练轻量化 adapter，理论上算力需求相比全量微调大幅降低。
- 具体硬件配置与训练耗时需查阅正文实验章节。

## 5. 实验数量与充分性

- **消融实验**：方法依赖多个关键组件（双对比目标、互信息最小化、空间内一致性、adapter 注入等），合理的论文应包含针对各组件的消融研究。
- **公平性评估**：是否在统一设置下与多种跨具身/视频编辑基线方法对比，是否报告多次随机种子平均结果、统计显著性等，在可获取片段中**未能确认**。
- **总体判断**：从摘要描述看，实验覆盖"表征解耦质量 + 视频编辑质量 + 下游策略迁移"三个层面，框架较为完整，但具体实验组数与充分性需结合正文判断。

## 6. 主要结论与发现

- **核心结论**：通过双对比目标显式解耦任务与具身表征，是**从人类视频学习机器人操纵**的一条有效路径。
- **具体发现**：
  - 解耦后的表征可支持高质量、形态准确、时间一致的跨具身视频生成。
  - 无需配对跨具身数据，方法可扩展到互联网规模的人类视频。
  - 显式正交化设计有助于缓解人-机器人之间的具身鸿沟（embodiment gap），提升下游模仿学习的迁移效果。

## 7. 方法与实验的亮点

- **表征解耦视角新颖**：将"跨具身"问题转化为表征解耦问题，比直接做视频到视频翻译（video-to-video translation）的传统思路更可控、可解释。
- **双对比目标设计巧妙**：同时进行"空间间互信息最小化"与"空间内一致性最大化"，与对比学习的现代范式契合。
- **参数高效迁移**：冻结大规模视频扩散模型 + 轻量化 adapter，兼顾生成质量与训练成本。
- **无需配对数据**：降低了数据采集门槛，具有明显的可扩展性优势。
- **端到端可生成**：单个人类示范即可合成完整机器人执行视频，便于直接喂入下游模仿学习。

## 8. 不足与局限

- **数据与场景覆盖未知**：因 PDF 提取受限，论文使用的数据集规模、任务多样性和机器人形态覆盖范围无法评估；若仅在有限场景下验证，泛化性存疑。
- **人类视频偏差风险**：互联网人类视频本身存在视角、背景、动作风格偏差，可能被错误编码到具身空间中，影响解耦纯度。
- **下游策略评估的间接性**：评估生成视频质量（FID/FVD 等）并不能完全代表其对真实机器人策略学习的贡献，仍需在真实机器人上进行闭环验证。
- **互信息估计的精度问题**：深度学习中互信息的精确估计本身是一个开放问题，所用估计器（如 MINE、InfoNCE 类）的选择可能影响解耦效果。
- **基线对比与可复现性**：在可获取信息中未列出明确基线，复现所需的预训练扩散模型权重、adapter 实现细节、训练超参等需结合附录确认。
- **Sim2Real 鸿沟**：合成视频即便形态准确，与真实机器人执行视频仍可能存在差距，从合成数据到真实部署的迁移风险需关注。

（完）
