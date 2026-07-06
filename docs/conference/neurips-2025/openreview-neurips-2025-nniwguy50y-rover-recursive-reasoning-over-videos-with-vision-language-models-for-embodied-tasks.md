---
title: "ROVER: Recursive Reasoning Over Videos with Vision-Language Models for Embodied Tasks"
title_zh: ROVER：面向具身任务的视频递归视觉语言推理
authors: "Philip Schroeder, Ondrej Biza, Thomas Weng, Hongyin Luo, James R. Glass"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NNiwGUY50Y"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向具身任务的视频递归推理
tldr: 针对视觉语言模型在长视频序列推理上的不足，ROVER提出递归视频推理框架，将长时程任务轨迹递归分解为更短子任务对应的片段，使模型能够在连续视觉流中更精准地理解与执行具身任务。该方法增强了VLM在长时程机器人场景下的时序局部推理能力，为下游决策与动作规划提供了更强的视觉基础。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 视觉语言模型在长视频帧序列推理上能力不足，限制了其在具身任务中的应用。
method: 提出递归视频推理框架ROVER，将长时程轨迹递归分解为子任务片段。
result: 在长时程具身任务中实现了更聚焦、更准确的时序局部推理。
conclusion: 为基于VLM的具身智能体处理长视频流提供了新的递归分解范式。
---

## Abstract
Vision-language models (VLMs) have exhibited impressive capabilities across diverse image understanding tasks, but still struggle in settings that require reasoning over extended sequences of camera frames from a video. This limits their utility in embodied settings, which require reasoning over long frame sequences from a continuous stream of visual input at each moment of a task attempt. To address this limitation, we propose ROVER (Reasoning Over VidEo Recursively), a framework that enables the model to recursively decompose long-horizon video trajectories into segments corresponding to shorter subtasks within the trajectory. In doing so, ROVER facilitates more focused and accurate reasoning over temporally localized frame sequences without losing global context. We evaluate ROVER, implemented using an in-context learning approach, on diverse OpenX Embodiment videos and on a new dataset derived from RoboCasa that consists of 543 videos showing both expert and perturbed non-expert trajectories across 27 manipulation tasks. ROVER outperforms strong baselines across three video reasoning tasks: task progress estimation, frame-level natural language reasoning, and video question answering. We observe that, by reducing the number of frames the model reasons over at each timestep, ROVER mitigates model hallucinations, especially during unexpected or non-optimal moments of a trajectory. In addition, by enabling the implementation of a subtask-specific sliding context window, ROVER's time complexity scales linearly with video length, an asymptotic improvement over baselines.

---

## 论文详细总结（自动生成）

<think>
The user wants me to analyze a paper based on the provided metadata and abstract, and produce a structured Chinese summary. Let me carefully read through the content.

The paper is "ROVER: Recursive Reasoning Over Videos with Vision-Language Models for Embodied Tasks" by Philip Schroeder et al., dated 2025-09-18, from NeurIPS 2025 Accepted.

Key points from the abstract:
- VLMs struggle with reasoning over extended sequences of camera frames from video
- This limits their utility in embodied settings
- ROVER = Reasoning Over VidEo Recursively
- It recursively decomposes long-horizon video trajectories into segments corresponding to shorter subtasks
- Evaluated using in-context learning
- Datasets: diverse OpenX Embodiment videos and a new dataset from RoboCasa (543 videos, expert and perturbed non-expert trajectories, 27 manipulation tasks)
- Three video reasoning tasks: task progress estimation, frame-level natural language reasoning, video question answering
- Outperforms strong baselines
- Mitigates model hallucinations during unexpected/non-optimal moments
- Time complexity scales linearly with video length (asymptotic improvement)
- Enables subtask-specific sliding context window

Let me structure the response according to the requested outline. The PDF content was not accessible (CAPTCHA), so I need to base my analysis on the metadata and abstract provided. I should note where information is limited or unavailable due to the PDF being inaccessible.

Let me organize the summary:

1. 核心问题与背景
2. 方法论
3. 实验设计
4. 资源与算力
5. 实验数量与充分性
6. 主要结论
7. 优点
8. 不足与局限

Since the PDF was not accessible (only CAPTCHA page), I need to be careful and only report what's available in the abstract and metadata. I should be transparent about this limitation.
</think>
# ROVER 论文总结

> **说明**：本次分析仅依据论文摘要与提供的元数据，原 PDF 因 OpenReview 验证码保护未能解析到正文细节，部分章节（如具体公式、完整实验表格、算力配置）信息有限，下文将明确标注。

---

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：现有的视觉语言模型（VLM）在处理**长序列视频帧**时推理能力不足，表现为对长时程、连续视觉流的理解能力有限。
- **应用场景瓶颈**：该缺陷直接限制了 VLM 在**具身智能（embodied）任务**中的应用，因为机器人/智能体在任务执行的每一时刻都需要对连续的相机帧流进行推理。
- **延伸挑战**：
  - 长视频帧序列容易引发模型的**幻觉（hallucination）**，尤其在轨迹中出现异常或非最优动作时；
  - 若将整段长视频一次性输入模型，计算量随视频长度**超线性增长**，难以在实际系统中部署。

---

## 2. 方法论：核心思想与关键技术

- **框架名称**：**ROVER**（**R**easoning **O**ver **VidE**o **R**ecursively）。
- **核心思想**：将**长时程视频轨迹递归地分解**为对应于较**短子任务**的视频片段，使模型在每一时刻只对**时序局部聚焦的帧序列**进行推理，同时保留全局上下文。
- **关键技术点**：
  1. **递归分解（recursive decomposition）**：长轨迹被切分为多个子任务级视频片段，形成层级化结构；
  2. **子任务级滑动上下文窗口（subtask-specific sliding context window）**：在递归分解的基础上，对每个子任务维护局部上下文；
  3. **In-context Learning 实现**：采用上下文学习（无需微调）方式实现 ROVER，便于即插即用；
  4. **保持全局上下文**：在聚焦局部推理的同时，不丢失对整体任务进度的感知。
- **复杂度优势**：通过减少每个时间步需要推理的帧数，时间复杂度相对视频长度**线性扩展**，相较基线在渐近意义上有所改进。
- **算法流程（文字描述）**：
  - 输入：长时程任务视频轨迹；
  - 步骤1：使用 VLM 递归地将长轨迹切分为若干子任务片段；
  - 步骤2：对每个子任务片段，调用 VLM 完成相应的视频推理任务（进度估计 / 帧级自然语言推理 / 视频问答）；
  - 步骤3：在子任务级别维护滑动上下文窗口，从而实现线性时间复杂度。

---

## 3. 实验设计

- **使用数据集**：
  1. **OpenX Embodiment 视频集**（多源、多样化的具身操作视频）；
  2. **基于 RoboCasa 构造的新数据集**：
     - 共 **543 段视频**；
     - 涵盖 **27 个操作任务**；
     - 同时包含**专家轨迹**和**受扰动的非专家轨迹**，便于评估模型在异常情况下的鲁棒性。
- **Benchmark 任务**（共 3 类视频推理任务）：
  1. **任务进度估计（task progress estimation）**；
  2. **帧级自然语言推理（frame-level natural language reasoning）**；
  3. **视频问答（video question answering）**。
- **对比方法**：摘要提及"strong baselines"，但未在可访问文本中列出具体基线名称（很可能包含一次性（one-shot）长视频推理、滑动窗口等常见方法，但需正文确认）。

---

## 4. 资源与算力

- **可获取信息**：摘要与元数据中**未明确说明**所使用的 GPU 型号、数量、训练时长或推理成本等算力信息。
- **间接线索**：
  - ROVER 采用 **in-context learning** 方式实现，**不需要对 VLM 进行训练**（即无微调阶段），因此主要算力消耗集中在**推理**上；
  - 由于时间复杂度相对视频长度线性扩展，理论上具备较好的推理效率。
- **结论**：算力相关细节**需查阅正文/附录**进一步确认。

---

## 5. 实验数量与充分性

- **可确认的实验规模**：
  - 涉及 **2 个数据集**（OpenX Embodiment + 新建 RoboCasa 数据集）；
  - 涵盖 **3 类下游视频推理任务**；
  - 新数据集规模适中（543 段视频 / 27 个任务），并区分**专家 vs. 非专家**轨迹，覆盖了正常与受干扰两类情形。
- **充分性评价**（基于现有信息）：
  - 优点：在多个任务、数据集和轨迹质量维度上进行了评估，并特别关注**非最优/异常时刻**的鲁棒性，实验设计具有一定的针对性；
  - 不足：
    - 仅依据摘要，**无法判断**消融实验、参数敏感性、不同 VLM backbone 替换等横向对比的覆盖程度；
    - 未见明确的统计显著性检验或多次随机种子平均结果的信息。

---

## 6. 主要结论与发现

- ROVER 在 **3 个视频推理任务**上均**优于强基线**；
- 通过减少每个时间步的输入帧数，**有效缓解了模型在意外/非最优时刻的幻觉**问题；
- 借助子任务级滑动窗口，**时间复杂度对视频长度为线性**（相对基线具备渐近优势）；
- 证明**递归分解**是在长视频具身任务中释放 VLM 推理能力的有效范式。

---

## 7. 优点

- **问题切入精准**：直接针对 VLM 在长视频具身任务中的核心痛点；
- **方法简洁可复用**：递归分解 + 子任务滑动窗口的思路清晰，in-context learning 实现方式便于扩展到不同 VLM；
- **效率优势明显**：线性时间复杂度在大规模长视频场景中具有实际部署价值；
- **评估维度全面**：同时考察任务进度、帧级语言推理、视频问答三类任务，并区分专家/非专家轨迹；
- **新建数据集贡献**：基于 RoboCasa 构建的 543 段视频数据集，涵盖 27 个任务，对社区有数据贡献价值。

---

## 8. 不足与局限

- **PDF 不可访问限制**：因 OpenReview 验证码拦截，**正文细节、完整实验配置、算力信息未能在本次分析中确认**，相关结论需以最终论文为准；
- **依赖 in-context learning**：基于上下文学习实现，对底层 VLM 的上下文窗口长度与指令遵循能力存在依赖，超长视频或极细粒度子任务可能仍受限制；
- **数据集规模与覆盖**：新建数据集仅 543 段视频，跨任务的样本量与场景多样性可能不足以覆盖全部具身场景；
- **缺乏（可确认的）消融与统计分析**：现有信息未提及消融实验、不同 VLM backbone 之间的对比、随机种子方差等内容，实验充分性需正文佐证；
- **应用范围限制**：当前主要在视频理解/推理层面验证，与**真实机器人闭环控制**的对接效果（如动作规划成功率、真实环境部署）未在摘要中体现；
- **潜在偏差风险**：摘要提到使用了"perturbed non-expert"轨迹，但具体的扰动类型与分布是否充分代表真实失败模式，仍需在原文中考察。

---

（完）
