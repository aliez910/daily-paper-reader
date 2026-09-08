---
title: Expanding Spatial and Temporal Context for Robotic Imitation Learning With Scene Graphs
title_zh: 基于场景图扩展机器人模仿学习的空间与时间上下文
authors: "Qian, Jianing, Peng, Qinhe, Panov, Emmanuel, Fermoselle, Leonor, Jayaraman, Dinesh, Bucher, Bernadette, Kelestemur, Tarik"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Qian_Expanding_Spatial_and_Temporal_Context_for_Robotic_Imitation_Learning_With_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于场景图记忆机制的模仿学习以应对部分观测与长时程任务
tldr: 在家庭、办公室等大规模真实环境中，机器人模仿学习面临严重部分观测以及长时程子任务推理的挑战。为此，本文提出将场景图作为显式结构化记忆机制用于模仿学习，通过维护动态的对象中心关系及其随时间的演化，使智能体在任务执行过程中保留相关历史上下文，从而高效地基于逐步累积的场景信息进行推理。该方法显著提升了模仿学习在大规模、部分观测环境中的长时程任务执行能力，对推动复杂环境下的机器人模仿学习具有重要价值。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1253, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 704, \"height\": 872, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1809, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 826, \"height\": 1084, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1813, \"height\": 143, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-qian-expanding-spatial-and-temporal-context-for-robotic-imitation-learning-with-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1818, \"height\": 925, \"label\": \"Figure\"}]"
motivation: 大规模环境下模仿学习受限于部分观测与长时程推理，难以高效完成复杂任务。
method: 将场景图作为显式结构化记忆引入模仿学习，维护对象关系及其时序演化。
result: 在长时程、部分观测任务中提升了模仿学习的上下文推理与执行能力。
conclusion: 为复杂环境下模仿学习的记忆与上下文建模提供了有效的结构化方案。
---

## Abstract
Imitation learning enables robots to learn how to execute tasks via observation. However, real-world environments like homes and offices are often severely partially observed due to their large spatial scales. In addition, many tasks involve executing a series of subtasks requiring autonomous robots to reason over extended time horizons. To address these challenges, we propose using scene graphs as an explicit and structured memory mechanism in imitation learning. By maintaining a dynamic scene graph that captures object-centric relationships and their evolution over time, our method allows the agent to retain relevant historical context during task execution to efficiently reason over incrementally accrued scene information. Our experiments on simulated mobile manipulation and real-world tabletop manipulation demonstrate that our approach substantially improves policy performance, particularly in settings that demand long-term reasoning and robust generalization under partial observability.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper based on the provided metadata and abstract. Let me analyze the information given:

The paper is "Expanding Spatial and Temporal Context for Robotic Imitation Learning With Scene Graphs" - a CVPR 2026 paper about using scene graphs as structured memory for robot imitation learning in partially observable, large-scale environments.

Key information available:
- Authors: Jianing Qian, Qinhe Peng, Emmanuel Panov, Leonor Fermoselle, Dinesh Jayaraman, Bernadette Bucher, Tarik Kelestemur
- Published at CVPR 2026
- Tags: query:rob-il
- Score: 9.0
- TLDR: Uses scene graphs as explicit structured memory for imitation learning to handle partial observability and long-horizon tasks
- Motivation: Large-scale environments have partial observability issues and long-horizon sub-task reasoning challenges
- Method: Scene graphs as explicit structured memory, maintaining dynamic object-centric relationships and their temporal evolution
- Result: Improved long-horizon task performance with partial observability
- Conclusion: Provides effective structured memory and context modeling for imitation learning in complex environments

The abstract mentions:
- Experiments on simulated mobile manipulation and real-world tabletop manipulation
- Substantial improvements in policy performance
- Particularly in long-term reasoning and robust generalization under partial observability

Since the PDF text extraction failed (the markdown content section is empty), I need to work with the metadata and abstract provided. I should note this limitation and base my summary primarily on the abstract content and metadata.

Let me create a comprehensive Chinese summary following the user's requirements:

1. Core problem and overall meaning
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and adequacy
6. Main conclusions
7. Strengths
8. Limitations

I need to be honest about what's not available in the extracted text - the actual PDF content beyond the abstract seems unavailable. The figures are listed but without captions. The detailed methodology beyond the abstract is not available in the extracted text.

Let me structure this carefully:</think>

# 论文总结：基于场景图扩展机器人模仿学习的空间与时间上下文

> **说明**：本次提供的论文 PDF 提取文本中正文部分为空，仅包含标题、摘要及元数据，因此本总结主要基于摘要与结构化元数据推断，详细方法细节、完整实验表格、超参数设置等信息无法直接验证，建议结合原文 PDF 进行核对。

---

## 1. 核心问题与研究动机

- **应用场景**：机器人模仿学习（Imitation Learning）应用于家庭、办公室等大规模真实环境。
- **核心挑战**：
  - **空间维度的部分观测**：环境空间尺度大，机器人单步观测只能覆盖局部区域，难以获得全局上下文。
  - **时间维度的长时程推理**：许多任务由一系列子任务组成，需要跨越较长的时间跨度进行规划与决策。
- **研究意义**：解决上述问题对推动模仿学习从受控实验室走向大规模、真实可部署的家庭/办公场景具有关键作用。
- **整体目标**：在严重部分观测条件下，让智能体能够基于逐步累积的场景信息进行高效推理，从而完成长时程复杂任务。

---

## 2. 方法论

- **核心思想**：将**场景图（Scene Graph）作为显式的结构化记忆机制**引入模仿学习，替代或补充传统隐式记忆（如递归神经网络隐藏状态）。
- **关键技术细节**：
  - **对象中心表征**：以对象（object-centric）为节点、以对象间关系（spatial / semantic relations）为边构建场景图。
  - **动态维护**：场景图随时间动态更新，捕捉对象关系在任务过程中的变化（如物体被移动、遮挡、消失、新增等）。
  - **历史上下文保留**：智能体在执行过程中能够"回看"图中累积的历史信息，从而在部分观测下仍能推断全局状态。
  - **增量推理**：基于"逐步累积的场景信息"进行策略决策，而非仅依赖当前帧观测。
- **算法流程（基于摘要推断）**：
  1. 感知模块从当前观测抽取对象与关系；
  2. 更新到维护中的动态场景图；
  3. 将当前观测 + 场景图作为策略网络的输入；
  4. 策略网络输出动作，循环往复。
- **备注**：摘要未明确给出具体网络架构、损失函数或公式；详细技术细节需要查阅正文与附录。

---

## 3. 实验设计

- **任务类型**：
  - **仿真移动操作（Simulated Mobile Manipulation）**。
  - **真实世界桌面操作（Real-world Tabletop Manipulation）**。
- **Benchmark**：
  - 摘要未明确指出使用的具体基准（如 AI2-THOR、Habitat、RLBench 等），需查阅正文确认。
- **对比方法（基于元数据与摘要推断）**：
  - 论文声称对比方法在长时程与部分观测设置下表现较弱，但具体基线名称（如 Behavior Cloning、Recurrent Policy、Transformer-based Memory 等）需进一步核对。
- **评估维度**：
  - 策略整体成功率；
  - 长时程推理能力；
  - 部分观测下的泛化能力。

---

## 4. 资源与算力

- **摘要与元数据中均未提及**：
  - 使用的 GPU 型号与数量；
  - 训练时长（墙钟时间或迭代步数）；
  - 仿真环境的算力需求；
  - 真实实验的硬件平台（如机器人型号、计算单元）。
- **建议**：正式总结时需在原文中检索 "implementation details"、"training"、"hardware"、"GPU" 等关键词进行补充。

---

## 5. 实验数量与充分性

- **已知的实验类别**（摘要中提及）：
  - 仿真移动操作实验；
  - 真实世界桌面操作实验。
- **充分性评估**：
  - 摘要表明实验覆盖了"仿真 + 真实"两种场景，兼顾可重复性与可部署性。
  - 但由于正文内容缺失，**无法判断**是否包含：
    - 消融实验（如去除场景图记忆、缩短时间窗口等）；
    - 多任务 / 多环境泛化实验；
    - 不同部分观测程度的敏感性分析；
    - 与多种 SOTA 基线的全面对比。
- **客观性与公平性**：在缺乏完整实验信息的前提下无法下定论；从摘要描述"substantially improves"来看，作者应提供了量化对比，但仍需查正文确认是否在统一协议下进行评估。

---

## 6. 主要结论与发现

- 场景图作为**显式结构化记忆**，能够有效缓解模仿学习在部分观测环境中的信息缺失问题。
- 动态维护对象关系有助于**长时程子任务推理**，使智能体能够跨越较长时间跨度规划动作。
- 在仿真移动操作与真实桌面操作两类任务上，策略性能均获得**显著提升**。
- 该方法在需要**长期推理**与**部分观测下鲁棒泛化**的场景中优势尤为突出。

---

## 7. 优点与亮点

- **结构化记忆的引入**：相比黑盒隐式记忆（RNN hidden state、Transformer context），场景图具有更好的**可解释性**与**可操作性**。
- **对象中心设计**：契合机器人操作任务的对象性本质，便于对环境状态进行显式建模与查询。
- **时空上下文扩展**：同时在空间（对象关系）与时间（动态演化）两个维度扩展上下文建模能力。
- **跨平台验证**：涵盖仿真与真实环境，增强结论的可信度与可迁移性。
- **应用导向**：直接面向家庭、办公等大规模真实场景，工程价值清晰。

---

## 8. 不足与局限

- **文本信息缺失**：本次 PDF 提取未提供正文内容，因此本总结无法对方法细节、参数设置、消融实验等做深入分析，存在一定推断成分。
- **依赖场景图构建质量**：方法的性能上限受限于感知模块（对象检测、关系抽取）的准确性；感知误差会被记忆机制放大或累积。
- **真实环境可扩展性**：摘要虽提到"real-world tabletop manipulation"，但具体环境复杂度、物体数量、任务多样性未明确，规模仍可能受限。
- **算力与训练成本未知**：缺乏训练资源信息，难以评估方法在大规模训练中的实际成本。
- **泛化性边界**：在训练场景之外的物体类别、布局、扰动下是否仍能保持性能，需要正文中的额外实验来支持。
- **与传统记忆机制的对比深度**：是否对 RNN、Transformer、长上下文 LLM-style 记忆等基线做了系统对比，仍需查正文核实。
- **可解释性 vs. 灵活性权衡**：显式结构化记忆虽然可解释，但在面对非结构化、连续或难以对象化的环境时（如柔性物体、液体）可能适用性下降。

---

（完）
