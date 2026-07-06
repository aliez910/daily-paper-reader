---
title: "From Code to Action: Hierarchical Learning of Diffusion-VLM Policies"
title_zh: 从代码到动作：扩散-VLM策略的分层学习
authors: "Markus Peschl, Pietro Mazzaglia, Daniel Dijkman"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=S93SnUsO8c"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过分层代码生成VLM与扩散策略进行机器人操控模仿学习
tldr: 本文针对复杂长视野机器人操控任务中模仿学习泛化能力弱、数据稀缺的问题展开研究。作者提出一种分层框架，将代码生成视觉-语言模型与底层扩散策略相结合：VLM将任务描述分解为可执行子程序，扩散策略模仿并执行相应行为。其核心思想是将开源机器人API同时作为执行接口和结构化监督来源，把子任务函数作为模块化语义标签。该系统在复杂长视野操控任务中显著提升了模仿与泛化能力，将高层代码规划与低层扩散视觉运动控制有效连接。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 复杂长视野机器人操控任务中模仿学习泛化能力有限且数据稀缺。
method: 提出代码生成VLM与扩散策略结合的分层框架，VLM分解任务为子程序，扩散策略模仿执行。
result: 在复杂长视野操控任务中显著提升模仿与泛化能力，高层代码与低层视觉运动控制有效衔接。
conclusion: 将机器人API作为结构化监督源是解决长视野操控模仿学习难题的有效路径。
---

## Abstract
Imitation learning for robotic manipulation often suffers from limited generalization and data scarcity, especially in complex, long-horizon tasks. In this work, we introduce a hierarchical framework that leverages code-generating vision-language models (VLMs) in combination with low-level diffusion policies to effectively imitate and generalize robotic behavior. Our key insight is to treat open-source robotic APIs not only as execution interfaces but also as sources of structured supervision: the associated subtask functions - when exposed - can serve as modular, semantically meaningful labels. We train a VLM to decompose task descriptions into executable subroutines, which are then grounded through a diffusion policy trained to imitate the corresponding robot behavior. To handle the non-Markovian nature of both code execution and certain real-world tasks, such as object swapping, our architecture incorporates a memory mechanism that maintains subtask context across time. We find that this design enables interpretable policy decomposition, improves generalization when compared to flat policies and enables separate evaluation of high-level planning and low-level control.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper based on the provided content. Let me analyze what's available:

1. The paper is titled "From Code to Action: Hierarchical Learning of Diffusion-VLM Policies"
2. It's about imitation learning for robotic manipulation
3. Key idea: hierarchical framework with code-generating VLMs and diffusion policies
4. Memory mechanism for non-Markovian tasks
5. Authors: Markus Peschl, Pietro Mazzaglia, Daniel Dijkman
6. Date: 2025-09-19
7. Conference: ICLR-2026-Public
8. Score: 8.0

The abstract provides good information but doesn't give me detailed experimental setup, datasets, benchmarks, compute resources, etc. I'll need to be careful to note where information is not explicitly available.

Let me structure the summary according to the requested 8 points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Number of experiments and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I should note that the provided text is limited (mainly abstract), so for items like compute resources, specific datasets, and detailed experimental numbers, I should acknowledge what's not specified in the provided content.
</think>
# 论文总结：从代码到动作——扩散-VLM 策略的分层学习

## 1. 核心问题与整体含义（研究动机与背景）

- **研究领域**：机器人操控（robotic manipulation）中的模仿学习（imitation learning）。
- **核心痛点**：
  - 在复杂、**长视野（long-horizon）**任务中，模仿学习泛化能力有限。
  - 高质量、细粒度的机器人演示数据严重稀缺。
  - 传统端到端（flat）策略难以同时处理高层语义规划与低层精细运动控制。
- **论文主张**：将高层代码规划（语义/结构层）与低层扩散策略（运动控制层）解耦，是突破上述瓶颈的关键。

## 2. 方法论

- **整体框架**：分层（hierarchical）架构，由"高层代码生成 VLM"+"低层扩散策略"组成，并辅以记忆机制。
- **核心思想（Key Insight）**：
  - 将开源机器人 **API 不仅视为执行接口，更视为结构化监督来源**。
  - 暴露的**子任务函数（subtask functions）天然充当模块化、语义化的标签**，可作为分层监督信号。
- **关键技术细节**：
  - **高层 VLM**：基于代码生成的视觉-语言模型，将自然语言任务描述分解为可执行的**子程序（subroutines）**。
  - **低层 Diffusion Policy**：模仿对应子任务，输出具体的视觉运动控制信号。
  - **记忆机制（Memory Module）**：用以处理代码执行和部分现实任务（如物体交换 object swapping）所具有的**非马尔可夫（non-Markovian）特性**，跨时间步维持子任务上下文。
- **算法流程（文字版）**：
  1. 输入：自然语言任务描述 + 视觉观测。
  2. VLM 生成代码，将任务分解为多个子程序。
  3. 每一步根据当前状态选择执行某个子程序。
  4. 扩散策略接收子任务语义标签，输出连续动作。
  5. 记忆模块跟踪已执行/正在执行的子任务，以应对状态依赖。

## 3. 实验设计

- **场景**：复杂、长视野的机器人操控任务（论文 evidence 提到"复杂长视野操控任务"），可能涉及多阶段、含物体交换等非马尔可夫操作。
- **Benchmark**：原 PDF 文本仅提供摘要，**未在所给内容中明确指出具体数据集（如 LIBERO、Meta-World、RLBench 等）**——需查阅正文。
- **对比方法**：
  - 与**端到端/扁平策略（flat policies）**对比（如纯扩散策略、纯 VLM 端到端方案等），以验证分层结构的优势。
  - 可能包含对单独 VLM 规划、单独扩散策略等组件的消融对比（推测，需正文确认）。
- **评估方式**：摘要提到"可分别评估高层规划与低层控制"——即**分模块评估**是该框架的特色之一。

## 4. 资源与算力

- **所给文本中未明确说明**：
  - 论文 PDF 仅提取到摘要部分，**未涉及使用的 GPU 型号/数量、训练时长、参数量等算力信息**。
  - 元数据 metadata 也未提供相关数据。
  - 实际使用资源需查阅正文与附录。

## 5. 实验数量与充分性

- **依据所给信息**：
  - 摘要层面**只声明了方向性结论**（如"显著提升""优于扁平策略"），未给出具体实验组数。
  - 消融设计（高层 vs 低层、有无记忆模块、不同 VLM backbone 等）的具体规模未在摘要中披露。
- **可推断的实验维度**（基于元数据 + 摘要）：
  - 至少包含：分层框架 vs 扁平基线（1 组主对比）。
  - 可能涉及：模块消融（记忆机制、代码生成接口）；泛化测试（未见过的任务/物体）。
- **充分性评价**：信息不足，需正文数据；摘要表明评估了"模仿与泛化能力"以及"高层/低层独立评估"，形式上较为系统，但具体组数与统计显著性未呈现。

## 6. 主要结论与发现

- 论文核心结论可归纳为：
  1. **将机器人 API 作为结构化监督源**能有效解决长视野操控模仿学习的数据稀缺与泛化难题。
  2. 高层代码规划 + 低层扩散视觉运动控制的**分层衔接**显著优于扁平策略。
  3. 记忆机制对**非马尔可夫子任务**（如 object swapping）至关重要。
  4. 框架天然支持**可解释的策略分解**（interpretable policy decomposition），且可对高层规划与低层控制进行**独立评估**。
  5. 子任务函数可作为**模块化、语义化的标签**，降低对密集演示数据的依赖。

## 7. 优点（亮点）

- **思路新颖**：把 API 同时作为"执行接口"和"结构化监督源"，将"代码即标签"（code-as-labels）思想引入机器人模仿学习。
- **层次解耦清晰**：高层语义规划（VLM/代码）与低层连续控制（Diffusion）各司其职，便于调试与评估。
- **可解释性**：子任务以代码形式呈现，策略行为可追溯、可分析。
- **模块化评估能力**：可分别评估高层规划器与低层控制器，定位瓶颈更方便。
- **针对非马尔可夫任务的记忆机制设计**：契合真实长视野场景的时序依赖。
- **缓解数据稀缺**：用 API 的结构化语义替代部分密集示范数据需求。

## 8. 不足与局限

- **数据/算力透明度不足**：摘要未提供数据集、计算资源、训练时长等关键信息，难以复现与横向比较。
- **依赖开源 API 的可获得性**：方法的有效性以"机器人 API 暴露子任务函数"为前提——若 API 不开放或子任务粒度不合适，方法可能失效，存在**应用前置假设**。
- **VLM 能力上限**：高层规划依赖代码生成 VLM 的能力，VLM 的幻觉（hallucination）、编译/语法错误可能级联导致执行失败。
- **错误传播风险**：高层规划若出错，下层扩散策略难以纠正；分层架构虽然模块化，但也带来**误差累积**。
- **任务覆盖与泛化边界**：摘要仅泛泛提及"复杂长视野任务"，未具体说明任务多样性、物体/场景分布外（OOD）泛化范围，结论的**外部效度**有待正文实验佐证。
- **公平性考量**：与扁平策略的对比是否在同一演示数据量、同一 VLM 条件下进行，仅凭摘要难以判断。
- **仿真 vs 真实差距**：未在所给文本中确认是否在真实机器人上验证，存在**Sim-to-Real 风险**未充分披露的可能。

（完）
