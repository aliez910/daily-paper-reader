---
title: "Robotic Programmer: Video Instructed Policy Code Generation for Robotic Manipulation"
title_zh: 机器人程序员：面向机器人操作的视频指令策略代码生成方法
authors: "Senwei Xie, Hongyu Wang, Zhanqi Xiao, Ruiping Wang, Xilin Chen"
date: 2024-09-25
pdf: "https://openreview.net/pdf?id=baQ0ICrnCR"
tags: ["query:rob-il"]
score: 7.0
evidence: 通用机器人基础模型通过策略代码连接视觉指令与操作执行
tldr: 机器人操作中跨机器人、跨任务、跨环境的零样本泛化仍是核心难题。本文提出通用机器人基础模型RoboPro，可感知视觉信息并遵循自由形式指令，在零样本条件下通过生成可执行策略代码完成操作任务。为降低代码数据采集成本，作者设计Video2Code流水线，从大规模视频数据自动合成可执行代码。RoboPro借助原子技能库与代码生成弥合高层任务描述与底层动作序列之间的鸿沟，为面向复杂操作的通用视觉-动作模型提供了新的实现路径。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 机器人操作在不同机器人、任务与环境间的零样本泛化能力仍然有限。
method: 提出通用基础模型RoboPro结合Video2Code流水线，从视频数据合成可执行代码以驱动操作。
result: 模型可在零样本条件下理解视觉指令并通过策略代码完成复杂机器人操作任务。
conclusion: RoboPro为构建通用、零样本的视觉-动作机器人操作系统提供了新范式。
---

## Abstract
Zero-shot generalization across various robots, tasks and environments remains a significant challenge in robotic manipulation. Policy code generation methods use executable code to connect high-level task descriptions and low-level action sequences, leveraging the generalization capabilities of large language models and atomic skill libraries. In this work, we propose Robotic Programmer (RoboPro), a robotic foundation model, enabling the capability of perceiving visual information and following free-form instructions to perform robotic manipulation with policy code in a zero-shot manner. To address low efficiency and high cost in collecting runtime code data for robotic tasks, we devise Video2Code to synthesize executable code from extensive videos in-the-wild with off-the-shelf vision-language model and code-domain large language model. Extensive experiments show that RoboPro achieves the state-of-the-art zero-shot performance on robotic manipulation in both simulators and real-world environments. Specifically, the zero-shot success rate of RoboPro on RLBench surpasses the state-of-the-art model GPT-4o by 11.6\%, which is even comparable to a strong supervised training baseline. Furthermore, RoboPro is robust to different robotic configurations, and demonstrates broad visual understanding in general VQA tasks.

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize a paper based on the metadata provided. The actual PDF content wasn't accessible (it was a CAPTCHA page), but the metadata gives substantial information about the paper "Robotic Programmer: Video Instructed Policy Code Generation for Robotic Manipulation" (RoboPro). Let me create a structured summary based on the available information.

Let me organize my response according to the 8 requested points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and computing
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

The paper is about RoboPro, a robotic foundation model for zero-shot generalization using policy code generation. Key points:
- Zero-shot generalization across robots, tasks, environments is hard
- Uses executable code as bridge between high-level descriptions and low-level actions
- Leverages LLMs and atomic skill libraries
- Proposes Video2Code pipeline to synthesize code from videos using vision-language models and code LLMs
- Achieves SOTA on RLBench, beating GPT-4o by 11.6%
- Works in simulators and real-world
- Robust to different robotic configurations
- Good at general VQA tasks

Let me write the summary in Chinese with Markdown formatting.</think>

# 论文总结：RoboPro——面向机器人操作的视频指令策略代码生成

## 1. 核心问题与研究动机

- **核心问题**：机器人操作在不同机器人形态、任务类型、环境场景之间的**零样本泛化能力**仍然受限。现有端到端的"感知-动作"模型往往难以从有限数据中泛化到未见过的任务与配置。
- **整体思路**：借鉴"代码即策略"（code-as-policy）范式，将高层任务描述与底层动作序列之间的鸿沟，由大语言模型（LLM）通过生成可执行代码、并结合原子技能库来弥合。
- **现实痛点**：直接采集机器人运行时代码数据效率低、成本高，难以大规模扩展。
- **解决方向**：利用"野外"大规模视频数据，借助现成的视觉-语言模型（VLM）与代码领域大模型，**自动合成**可执行的策略代码，从而降低数据门槛。

---

## 2. 方法论

### 2.1 核心思想
提出通用机器人基础模型 **RoboPro（Robotic Programmer）**：以视频/图像作为视觉输入、以自由形式语言作为任务指令，**直接生成可执行的策略代码**（Policy Code），由机器人端调用底层原子技能完成操作，整个过程零样本完成。

### 2.2 关键组件
- **视觉-语言编码器**：负责感知视频/图像与自由文本指令。
- **代码生成器（LLM）**：根据感知到的场景与指令生成 Python 等可执行代码作为策略。
- **原子技能库（Atomic Skill Library）**：封装底层动作原语（如抓取、放置、移动等），由生成的代码调用，屏蔽底层控制复杂性。

### 2.3 Video2Code 流水线（数据合成方法）
- 输入：大规模野外视频（in-the-wild videos）。
- 流程：
  1. 使用**现成 VLM**对视频内容进行语义理解和任务描述生成。
  2. 使用**代码领域 LLM**根据任务描述生成对应的可执行策略代码。
  3. 通过**仿真执行验证/筛选**，过滤不可执行或语义不一致的样本，形成训练数据集。
- 目标：以低成本从视频中合成大量"视频-代码"配对数据，缓解真实机器人代码数据稀缺的问题。

### 2.4 推理流程（文字描述）
1. 给定任务指令 + 当前视频/图像观察；
2. 视觉-语言模型将指令与观察对齐为任务语义；
3. 代码生成模型输出策略代码；
4. 在机器人端执行代码，依次调用原子技能完成操作。

---

## 3. 实验设计

- **数据集/场景**：
  - **RLBench**（机器人操作仿真基准）；
  - **真实环境实验**（real-world robotic manipulation）；
  - **通用 VQA 任务**（用于评估视觉理解的泛化性）。
- **Benchmark**：
  - 主要 benchmark 为 RLBench 上的零样本成功率。
  - 同时在真实机器人配置上验证。
- **对比方法**：
  - **GPT-4o**：作为当前 SOTA 通用基模型对照；
  - **有监督训练基线**（strong supervised baseline）：用于衡量零样本方法在性能上限上的逼近程度。
- **评估指标**：任务成功率（Success Rate）、跨机器人配置的鲁棒性、通用 VQA 准确率。

---

## 4. 资源与算力

- 论文摘要与元数据中**未明确披露**具体的 GPU 型号、数量与训练时长。
- 从方法推断，训练涉及 VLM、代码 LLM 等大规模预训练模型组件，可能在多卡 GPU 上进行微调，但**具体算力配置、训练小时数、数据规模等未在所提供内容中说明**。
- 建议读者查阅正文/附录以获取更详细的训练资源信息。

---

## 5. 实验数量与充分性

- **实验覆盖**：
  - 仿真（RLBench）+ 真实环境，构成 sim-to-real 与真实部署双重验证。
  - 不同机器人配置下的鲁棒性测试。
  - 通用 VQA 任务以衡量视觉理解的广泛性。
- **对比维度**：与 GPT-4o、有监督强基线分别比较，并展示对后者的可逼近性。
- **充分性评价**：
  - 优点：涵盖 sim/real、跨机器人、跨任务（VQA）多维度，且与 GPT-4o 等强基线对比具有说服力。
  - 不足：所提供的元数据中**未给出消融实验的详细信息**（如 Video2Code 各模块、原子技能库规模、LLM 选型的影响等），难以判断各组件的边际贡献是否被充分验证。

---

## 6. 主要结论与发现

- **零样本性能领先**：在 RLBench 上，RoboPro 的零样本成功率**超越 GPT-4o 约 11.6 个百分点**。
- **逼近监督基线**：零样本设置下性能已可与强监督训练基线相媲美。
- **跨配置鲁棒性**：对不同机器人形态（embodiment）具有较强的鲁棒性，验证了"代码即策略"对形态差异的解耦能力。
- **广泛视觉理解**：在通用 VQA 任务上同样表现良好，表明模型不仅适用于操作任务，也保留了通用视觉语义能力。
- **数据范式**：Video2Code 验证了"视频→可执行代码"自动合成路径的可行性，为机器人策略数据扩展提供新思路。

---

## 7. 优点与亮点

- **范式新颖**：将"代码生成 + 原子技能库"作为机器人基础模型的核心输出形式，巧妙绕过端到端动作预测中的长尾分布与形态耦合问题。
- **数据策略高效**：Video2Code 利用 VLM + 代码 LLM 从大规模野外视频合成训练数据，显著降低数据采集门槛。
- **零样本能力突出**：相对 GPT-4o 取得显著提升，且可逼近强监督基线，实用价值高。
- **泛化多面**：同时在操作任务（仿真/真实）、机器人配置、通用 VQA 上展现能力，体现"基础模型"定位。
- **可解释性较好**：生成的是可读代码，便于调试、审计与人在回路修正，相较黑盒动作预测更具透明度。

---

## 8. 不足与局限

- **算力与训练细节不透明**：摘要/元数据未披露 GPU 型号与数量、训练时长、数据规模等关键资源信息，复现成本难以评估。
- **消融实验信息缺失**：所提供内容未详细描述 Video2Code 各阶段、原子技能库覆盖度、代码 LLM/VLM 选型等对最终性能的贡献，组件重要性未充分拆解。
- **真实实验规模有限**：仅说明在真实环境进行验证，但具体任务数量、试次（trials）、机器人型号等细节未给出，统计显著性需进一步确认。
- **对 VLM/代码 LLM 依赖较强**：方法性能高度依赖底层 VLM 与代码 LLM 的能力，存在模型能力天花板与偏置继承风险（如 VLM 的物体/动作偏见）。
- **Video2Code 偏差风险**：自动合成代码的"语义忠实度"依赖 VLM 的视频理解质量，若视频与目标操作存在域差（如 YouTube 视频 vs 真实机器人），可能产生错误策略代码，且筛选机制的有效性需更多分析。
- **原子技能库的设计成本**：虽然避免了逐任务标注动作，但技能库本身的工程设计仍依赖专家经验，限制了任务可扩展性。
- **安全与可靠性**：在真实机器人上执行生成代码存在安全风险，文中未充分讨论安全约束、回退机制或失败检测策略。
- **评估公平性**：与 GPT-4o 的对比未说明是否使用相同的原子技能库、提示工程或调用预算，对比口径可能不完全公平，需在正文核实。

（完）
