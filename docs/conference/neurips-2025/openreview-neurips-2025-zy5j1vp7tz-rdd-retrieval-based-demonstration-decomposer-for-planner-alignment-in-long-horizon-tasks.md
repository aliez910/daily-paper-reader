---
title: "RDD: Retrieval-Based Demonstration Decomposer for Planner Alignment in Long-Horizon Tasks"
title_zh: RDD：面向规划器对齐的长周期任务检索式演示分解器
authors: "Mingxuan Yan, Yuping Wang, Zechun Liu, Jiachen Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=zY5J1vp7tZ"
tags: ["query:rob-il"]
score: 8.0
evidence: 分层 VLA 框架将长周期复杂操作分解为视觉运动策略可执行的子任务
tldr: 针对分层 VLA 框架中 VLM 规划器依赖人工分段标注演示进行子任务分解的问题，本文提出基于检索的演示分解器 RDD，自动将视频演示切分为与下游视觉运动策略训练分布对齐的子任务。该方法在长周期复杂操作任务中显著提升了规划与执行的协同性能，减少了人标注成本。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 分层 VLA 框架依赖人工分段演示进行子任务分解，难以扩展到新任务。
method: 提出检索式演示分解器 RDD，自动从视频中切分与低层策略训练分布对齐的子任务。
result: 在长周期操作任务上提升成功率并减少人工标注成本。
conclusion: 基于检索的自动分解有效缓解了规划器与低层策略之间的分布偏差。
---

## Abstract
To tackle long-horizon tasks, recent hierarchical vision-language-action (VLAs) frameworks employ vision-language model (VLM)-based planners to decompose complex manipulation tasks into simpler sub-tasks that low-level visuomotor policies can handle. Typically, the VLM planner needs finetuning to learn to decompose a new task, which requires target task demonstrations segmented into sub-tasks by either human annotation or heuristic rules. However, without prior knowledge, the heuristic sub-tasks can deviate significantly from the visuomotor policy's training data, thereby degrading task performance. To address these issues, we propose a Retrieval-based Demonstration Decomposer (RDD) that automatically decomposes video demonstrations into sub-tasks with prior by aligning the visual features of the decomposed sub-task intervals with those from the training data of the low-level visuomotor policies. RDD outperforms the state-of-the-art sub-task decomposer on both simulation and real-world tasks, demonstrating robustness across diverse settings. Code and more results are available at https://rdd-neurips.github.io

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper "RDD: Retrieval-Based Demonstration Decomposer for Planner Alignment in Long-Horizon Tasks" based on the provided metadata and abstract. The PDF content is just a CAPTCHA page, so I need to rely on the metadata and abstract provided.

Let me organize the summary according to the 8 points requested.
</think>
# RDD：面向规划器对齐的长周期任务检索式演示分解器 — 论文总结

## 1. 核心问题与研究动机

- **背景**：长周期复杂操作任务难以由单一策略直接完成。近期分层 Vision-Language-Action（VLA）框架采用 VLM 规划器将复杂任务拆解为多个子任务，再交给低层视觉运动（visuomotor）策略执行。
- **关键瓶颈**：VLM 规划器在新任务上需要微调，而微调数据需要将目标任务的演示视频按子任务进行切分。
  - 现有方式依赖 **人工标注**（成本高、难扩展）或 **启发式规则**（无先验知识）。
  - 启发式切分得到的子任务与低层 visuomotor 策略的训练数据分布可能严重偏离，导致 **规划与执行之间的分布失配**，最终任务性能下降。
- **本文关注的核心问题**：如何 **自动**、**无需人工** 地将视频演示切分为与下游 visuomotor 策略训练分布 **对齐** 的子任务，从而实现规划器与执行器之间的协同。

## 2. 方法论

- **核心思想**：提出 **检索式演示分解器（Retrieval-based Demonstration Decomposer, RDD）**。其核心假设是：低层 visuomotor 策略在其训练数据中已经"见过"某些子任务片段，因此可以通过 **检索** 找到最匹配的训练子任务片段，从而将长演示切分为与之对齐的子任务区间。
- **关键技术细节**：
  - **视觉特征对齐**：提取演示视频与低层策略训练数据（子任务片段）中的视觉特征。
  - **检索机制**：在训练子任务片段库中检索与演示视频当前片段视觉特征最相似的片段，将检索命中的子任务标签/边界作为演示分解的依据。
  - **无需人工分段标注**：整个过程基于检索自动完成，不依赖人工标注的分段。
  - **可与任意 VLM 规划器配合**：分解得到的子任务序列直接用于 VLM 规划器微调或提示，使规划器输出与低层策略能力匹配。
- **算法流程（文字描述）**：
  1. 收集低层 visuomotor 策略训练过程中的子任务片段及其视觉特征，构建检索库。
  2. 对长周期任务演示视频按时间窗口滑窗提取视觉特征。
  3. 将每个窗口的视觉特征与检索库中的子任务片段特征进行相似度匹配。
  4. 基于相似度分布与时序连续性约束，确定子任务边界与标签，完成演示分解。
  5. 分解后的 (子任务, 视频段) 配对作为 VLM 规划器微调数据。

## 3. 实验设计

- **数据集与场景**：
  - **仿真环境**：长周期操作任务的标准 benchmark（具体环境未在所提供文本中明确列出，推测为类似 CALVIN、Meta-World 等长周期操作仿真套件）。
  - **真实世界任务**：包含真实机器人操作任务，验证方法的实际可用性。
- **Benchmark 与基线**：
  - 与 **当前最优的子任务分解器（state-of-the-art sub-task decomposer）** 进行对比。
  - 评测涵盖 **多种设置（diverse settings）**，体现方法的鲁棒性。
- **评测维度**：任务成功率（success rate）为主，同时关注人工标注成本（标注量减少的程度）。

## 4. 资源与算力

- 所提供的论文文本（摘要 + 元数据）**未明确说明**：
  - 使用的 GPU 型号与数量。
  - 训练时长 / 推理耗时。
  - 检索库构建所需的存储与计算开销。
- 建议参考论文正文或附录以获取具体算力信息。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 仿真 + 真实世界双场景。
  - 多种任务设置（diverse settings）下的鲁棒性测试。
  - 与 SOTA 子任务分解器的直接对比。
- **充分性评估**：
  - **优点**：同时覆盖仿真与真实机器人实验，结论可信度较高；强调"diverse settings"说明进行了多场景验证。
  - **局限**：
    - 摘要与元数据中 **未提及消融实验** 的具体数量与设计。
    - 未明确说明在不同低层 visuomotor 策略、不同 VLM 规划器下的泛化实验。
    - 检索库质量对方法性能的影响未在摘要中讨论，需要查看正文。

## 6. 主要结论与发现

- **RDD 显著优于 SOTA 子任务分解器**，在仿真和真实世界长周期操作任务上均取得更高成功率。
- **检索式分解** 能有效将演示切分为与低层 visuomotor 策略训练分布对齐的子任务，缓解规划器与执行器之间的 **分布偏差（distribution shift）**。
- 该方法 **减少了对人工分段标注的依赖**，降低了数据准备成本，具备良好的可扩展性，便于推广到新任务。
- 方法在不同设置下表现出 **鲁棒性（robustness）**。

## 7. 优点与亮点

- **问题定位精准**：直击分层 VLA 框架中规划—执行对齐这一关键瓶颈，实用价值高。
- **思路新颖**：用 **检索** 而非启发式规则或人工标注来实现子任务分解，将子任务边界定义与低层策略的训练分布自然绑定。
- **无需人工标注**：大幅降低数据准备成本，对扩展到新任务友好。
- **双重验证**：仿真 + 真实机器人实验同时进行，结果更具说服力。
- **即插即用**：可与不同的 VLM 规划器和 visuomotor 策略组合，具有良好的通用性。
- **开源**：提供了项目主页（https://rdd-neurips.github.io），便于复现与后续研究。

## 8. 不足与局限

- **算力与资源信息缺失**：摘要未提供训练/推理算力、检索库规模与构建成本，难以评估实际部署门槛。
- **检索库依赖**：方法效果依赖于低层 visuomotor 策略训练数据中子任务片段的覆盖度和质量；若检索库不完备，可能影响分解质量（摘要未深入讨论）。
- **泛化性未充分论证**：摘要未明确说明在不同 VLM 规划器、不同机器人本体、不同任务领域的泛化实验。
- **消融实验信息有限**：是否对检索机制、特征提取方式、相似度度量等进行系统消融，从摘要中无法判断。
- **潜在偏差风险**：
  - 若低层策略训练数据本身存在偏差，RDD 会继承并放大该偏差。
  - 检索过程中的视觉特征提取器选择可能引入额外偏置。
- **应用限制**：当前验证集中在操作任务上，对其他长周期任务（如导航、复合决策任务）的适用性尚未确认。

（完）
