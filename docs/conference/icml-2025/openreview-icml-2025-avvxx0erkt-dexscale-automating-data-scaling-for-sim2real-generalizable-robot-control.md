---
title: "DexScale: Automating Data Scaling for Sim2Real Generalizable Robot Control"
title_zh: DexScale：自动化数据扩展以实现仿真到现实的通用机器人控制
authors: "Guiliang Liu, Yueci Deng, Runyi Zhao, Huayi Zhou, Jian Chen, Jietao Chen, Ruiyan Xu, Yunxin Tai, Kui Jia"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=AVVXX0erKT"
tags: ["query:rob-il"]
score: 7.0
evidence: 自动化数据扩展以增强机器人操纵策略的仿真到现实泛化
tldr: 该论文针对真实机器人数据昂贵、仿真数据泛化性差的问题，提出了DexScale数据引擎。它自动在仿真环境中生成并扩展机器人操纵技能，并通过集成技术确保技能的真实可用性。实验证明DexScale可以训练出在真实世界中泛化的操纵策略，降低了数据收集成本，提升了sim2real迁移效果。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 机器人训练数据昂贵，仿真数据与真实环境存在差距。
method: 构建自动化的数据引擎，在仿真中生成和扩展可用的机器人操纵技能。
result: 生成的策略在真实世界中表现良好，泛化性强。
conclusion: 自动化的sim2real数据扩展是降低数据需求的有效途径。
---

## Abstract
A critical prerequisite for achieving generalizable robot control is the availability of a large-scale robot training dataset. Due to the expense of collecting realistic robotic data, recent studies explored simulating and recording robot skills in virtual environments. While simulated data can be generated at higher speeds, lower costs, and larger scales, the applicability of such simulated data remains questionable due to the gap between simulated and realistic environments. To advance the Sim2Real generalization, in this study, we present DexScale, a data engine designed to perform automatic skills simulation and scaling for learning deployable robot manipulation policies. Specifically, DexScale ensures the usability of simulated skills by integrating diverse forms of realistic data into the simulated environment, preserving semantic alignment with the target tasks. For each simulated skill in the environment, DexScale facilitates effective Sim2Real data scaling by automating the process of domain randomization and adaptation. Tuned by the scaled dataset, the control policy achieves zero-shot Sim2Real generalization across diverse tasks, multiple robot embodiments, and widely studied policy model architectures, highlighting its importance in advancing Sim2Real embodied intelligence.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究动机**：机器人训练依赖大规模真实数据，但真实数据采集成本高昂、效率低。仿真数据虽可快速、廉价地大规模生成，但由于仿真环境与真实环境之间的差异（Sim2Real gap），直接使用仿真数据训练的策略在真实环境中泛化性差、可用性低。
- **核心问题**：如何自动化地在仿真环境中生成并扩展高质量、真实可用的机器人操作技能数据，从而降低对真实数据的依赖，提升Sim2Real迁移的泛化能力。
- **整体含义**：论文提出DexScale数据引擎，通过自动化仿真技能生成、数据扩展和域随机化适应，使训练出的控制策略能够零样本（zero-shot）地从仿真迁移到真实世界，为低成本、大规模获取机器人训练数据提供有效途径。

### 2. 论文提出的方法论

- **核心思想**：构建一个自动化数据引擎DexScale，在仿真环境中集成多种类型的真实数据以保持语义对齐，并自动进行域随机化和适应，从而在仿真中生成可直接用于真实世界的技能数据。
- **关键技术细节**（基于摘要推断）：
  - 将多种形式的真实数据融入仿真环境，确保生成技能与目标任务语义一致。
  - 自动化域随机化与适应过程，针对每个仿真技能调整仿真参数，使数据分布更接近真实。
  - 利用扩展后的数据集训练控制策略，实现零样本Sim2Real泛化。
- **公式或算法流程**：摘要未提供具体算法描述，仅从概念层面说明了数据引擎的工作流程（集成真实数据 → 自动化扩展示例 → 域随机化与适应 → 策略训练）。

### 3. 实验设计

- **使用的数据集/场景**：摘要提及实验覆盖“different tasks”（不同任务）、“multiple robot embodiments”（多种机器人形态）以及“widely studied policy model architectures”（广泛研究的策略模型架构），但未具体列出任务名称、环境或数据集来源。
- **Benchmark**：未明确提及具体的基准测试集。推测其可能基于常用Sim2Real基准（如RLBench、MetaWorld等），但原文未交代。
- **对比方法**：摘要未提及与其他方法的定量对比。仅声称DexScale可以在多种设定下实现零样本泛化，但未列出基线方法。

### 4. 资源与算力

- **摘要与元数据中未提及**使用的GPU型号、数量、训练时长等信息。本文未专门说明算力资源。

### 5. 实验数量与充分性

- **实验组数**：摘要提到实验覆盖多种任务、多种机器人形态和多种模型架构，但未给出具体实验数量或消融实验细节。从文本推断，可能包含多组对比实验（如不同策略架构、不同域随机化策略等），但信息不足。
- **充分性与公平性**：仅从摘要无法判断实验是否充分、对比是否公平。缺乏基线方法、定量结果和统计信息，故难以评估。

### 6. 论文的主要结论与发现

- DexScale能自动化生成和扩展仿真操作技能，且通过集成真实数据与域随机化适应，解决了仿真数据可用性低的问题。
- 训练后的控制策略在不同任务、不同机器人形态以及多种流行策略架构上均能实现零样本Sim2Real泛化。
- 该方法显著降低了真实数据收集成本，提升了Sim2Real迁移效果，对推动具身智能具有重要价值。

### 7. 优点

- **自动化程度高**：DexScale实现了技能仿真、数据扩展和域适应的全自动化，无需人工干预。
- **泛化性广**：在多种任务、多种机器人形态和多种策略架构上验证了零样本迁移能力，说明方法具有较强的通用性。
- **实际应用意义强**：通过降低对昂贵真实数据的依赖，为低成本部署机器人策略提供了可行方案。
- **数据引擎思路新颖**：将真实数据融入仿真环境以保持语义对齐，同时利用域随机化自动调整，是提升仿真数据实用性的有效设计。

### 8. 不足与局限

- **实验细节缺失**：未报告具体任务、环境、机器人型号、策略架构名称及定量结果，导致无法直接复现或判断性能水平。
- **对比基线不明**：未列出与现有Sim2Real方法（如Domain Randomization、Adaptation等）的对比，削弱了说服力。
- **计算资源未公开**：未说明训练所需算力，难以评估方法的实用性成本。
- **应用限制**：仅聚焦于机器人操控任务，其他类型技能（移动、导航等）尚未验证；且零样本泛化的鲁棒性（如环境扰动、光照变化等）未提及。
- **消融研究缺失**：未明确指出是否分析了不同组件（如真实数据融合、域随机化策略、数据扩展量）的贡献，实验充分性存疑。

（完）
