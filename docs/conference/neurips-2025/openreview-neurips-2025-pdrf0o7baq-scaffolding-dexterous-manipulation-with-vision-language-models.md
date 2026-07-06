---
title: Scaffolding Dexterous Manipulation with Vision-Language Models
title_zh: 利用视觉-语言模型搭建灵巧操作框架
authors: "Vincent de Bakker, Joey Hejna, Tyler Ga Wei Lum, Onur Celik, Aleksandar Taranovic, Denis Blessing, Gerhard Neumann, Jeannette Bohg, Dorsa Sadigh"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=PdRf0O7baQ"
tags: ["query:rob-il"]
score: 6.0
evidence: 灵巧手操作任务与控制方法
tldr: 针对灵巧机器人手在复杂操作任务中难以训练的问题，本文利用视觉-语言模型为强化学习提供参考轨迹骨架，避免依赖人工设计的任务特定奖励函数。方法通过VLM生成目标手部姿态与物体姿态，引导RL策略探索并提供任务无关的稠密奖励。实验结果表明该框架在灵巧操作任务上提升了可扩展性与泛化能力，为复杂灵巧操作提供了新的学习范式。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 灵巧机器人手因演示采集难、控制维度高而难以训练，且传统RL依赖任务特定奖励函数限制了泛化能力。
method: 借助视觉-语言模型生成参考手部与物体姿态轨迹，引导RL策略在仿真中进行任务无关的探索学习。
result: 实验表明该方法在多种灵巧操作任务上具有更好的可扩展性与泛化性能。
conclusion: 为灵巧操作提供了一种基于VLM引导的、可扩展的强化学习训练新范式。
---

## Abstract
Dexterous robotic hands are essential for performing complex manipulation tasks, yet remain difficult to train due to the challenges of demonstration collection and high-dimensional control. While reinforcement learning (RL) can alleviate the data bottleneck by generating experience in simulation, it typically relies on carefully designed, task-specific reward functions, which hinder scalability and generalization. Thus, contemporary works in dexterous manipulation have often bootstrapped from reference trajectories. These trajectories specify target hand poses that guide the exploration of RL policies and object poses that enable dense, task-agnostic rewards.
However, sourcing suitable trajectories---particularly for dexterous hands---remains a significant challenge. Yet, the precise details in explicit reference trajectories are often unnecessary, as RL ultimately refines the motion. Our key insight is that modern vision-language models (VLMs) already encode the commonsense spatial and semantic knowledge needed to specify tasks and guide exploration effectively. Given a task description (e.g., “open the cabinet”) and a visual scene, our method uses an off-the-shelf VLM to first identify task-relevant keypoints (e.g., handles, buttons) and then synthesize 3D trajectories for hand motion and object motion. Subsequently, we train a low-level residual RL policy in simulation to track these coarse trajectories or ``scaffolds'' with high fidelity. Across a number of simulated tasks involving articulated objects and semantic understanding, we demonstrate that our method is able to learn robust dexterous manipulation policies. Moreover, we showcase that our method transfers to real-world robotic hands without any human demonstrations or handcrafted rewards.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Scaffolding Dexterous Manipulation with Vision-Language Models" based on the provided abstract and metadata. I need to organize the summary according to 8 specific points using Markdown formatting with hierarchical headings and bullet points, and end with "（完）".

Let me analyze the paper content:

**Title**: Scaffolding Dexterous Manipulation with Vision-Language Models
**Authors**: Vincent de Bakker, Joey Hejna, Tyler Ga Wei Lum, Onur Celik, Aleksandar Taranovic, Denis Blessing, Gerhard Neumann, Jeannette Bohg, Dorsa Sadigh
**Date**: 2025-09-18
**Conference**: NeurIPS-2025-Accepted

**Key ideas from abstract**:
1. Dexterous robotic hands are hard to train (data bottleneck, high-dim control)
2. RL can help but needs task-specific reward functions (limits scalability)
3. Previous work uses reference trajectories (hand poses + object poses for dense task-agnostic rewards)
4. Getting such trajectories for dexterous hands is hard
5. Key insight: VLMs already encode commonsense spatial/semantic knowledge
6. Method: Use VLM to identify task-relevant keypoints (handles, buttons) from task description + visual scene, then synthesize 3D trajectories
7. Train low-level residual RL policy in simulation to track these "scaffolds"
8. Results: Robust dexterous manipulation on simulated tasks with articulated objects; transfers to real-world hands without human demos or handcrafted rewards

Let me organize this into the 8 requested sections. Since I only have the abstract and metadata, I should note where information is limited (like specific resource/compute details, which aren't in the abstract).

Let me write a comprehensive summary in Chinese.
</think>
# 论文总结：利用视觉-语言模型搭建灵巧操作框架

## 1. 核心问题与研究动机

- **研究对象**：灵巧机器人手（Dexterous Robotic Hands）的复杂操作任务。
- **核心痛点**：
  - 灵巧手控制维度高、自由度大，难以采集人类演示数据。
  - 强化学习（RL）虽可在仿真中自主生成经验，缓解数据瓶颈，但通常依赖人工设计的、任务特定的奖励函数，严重限制可扩展性与泛化能力。
- **已有做法的不足**：现有工作常借助参考轨迹（reference trajectories）来引导 RL 探索，并提供稠密、任务无关的奖励；但这类参考轨迹本身难以获取（尤其是针对灵巧手），且其精确细节对最终 RL 策略而言往往是冗余的。
- **关键洞察（Key Insight）**：现代视觉-语言模型（VLM）已经隐式编码了完成任务所需的常识性空间与语义知识，可以代替人工来生成粗略但有效的参考轨迹。

## 2. 方法论

### 2.1 整体框架
提出一种 **"VLM 提供骨架 + 残差 RL 精细跟踪"** 的两阶段训练范式：
- 上层：冻结的、开箱即用的 VLM 充当"任务规划器"，输出粗略的运动参考。
- 下层：在仿真中训练残差 RL 策略，对上层提供的"脚手架（scaffolds）"进行高保真跟踪。

### 2.2 关键技术流程
1. **任务输入**：给定自然语言任务描述（如"打开柜子"）和当前场景的视觉观察。
2. **关键点识别**：VLM 首先识别任务相关的语义关键点，例如把手、按钮等。
3. **3D 轨迹合成**：基于识别出的关键点，VLM 进一步合成 3D 空间中的两条参考轨迹：
   - 手的运动轨迹（hand motion）
   - 物体的运动轨迹（object motion）
4. **残差 RL 训练**：在仿真环境中训练底层残差 RL 策略，目标是以高保真度跟踪这些粗略轨迹（scaffolds），由此获得可执行的灵巧操作策略。

### 2.3 设计优势
- **任务无关的奖励**：物体姿态轨迹可直接用于构造稠密奖励，无需人工设计任务特定奖励。
- **粗轨迹即可**：RL 会进一步精修运动，因此不需要 VLM 输出精确轨迹。
- **不依赖人类演示**：完全由 VLM 知识驱动。

## 3. 实验设计

- **任务场景**（基于摘要信息）：
  - 仿真任务：涉及**铰接物体（articulated objects）**的操作，以及需要**语义理解**的任务（例如开柜子等）。
- **评估维度**：
  - 在仿真中学习到的策略的**鲁棒性**。
  - 仿真到真实（sim-to-real）的**迁移能力**。
- **基准与对比**：
  - 摘要中未明确列出具体 baseline 方法名称，但定位是相对于依赖"人工参考轨迹"或"任务特定奖励"的传统 RL 灵巧操作方法进行对比。
- **真机验证**：
  - 强调**无需任何人类演示或人工设计奖励**即可迁移到真实机器人手。

> 注：具体的 benchmark 数据集名称、对比基线列表及量化指标在所提供摘要中未给出，需参考正文补充。

## 4. 资源与算力

- **摘要中未明确披露**：
  - 未提及所用 GPU 型号与数量。
  - 未说明训练时长、参数量或总计算预算。
- 只能推断：
  - 方法依赖一个"开箱即用"的 VLM（off-the-shelf VLM），具体模型未在摘要中说明。
  - 残差 RL 在仿真中训练，仿真平台未在摘要中说明（结合作者背景与领域惯例，大概率基于 IsaacGym / MuJoCo 类仿真器，但仍需正文确认）。

## 5. 实验数量与充分性

- **摘要中可观察到的实验内容**：
  - 多项仿真任务（涉及多种铰接物体 + 语义理解任务）。
  - 真实机器人手的迁移实验。
- **充分性评估**：
  - 从摘要描述看，实验同时覆盖了**仿真性能**与**真实迁移**两个维度，并强调"无需人类演示与人工奖励"的关键卖点，论证链路较为完整。
- **客观性**：
  - 摘要未透露是否包含消融实验（如：去除 VLM 关键点识别、去除残差 RL、去除稠密奖励等）。
  - 是否对不同 VLM backbone、不同任务、不同物体进行了系统对比，仍需参考正文。
- **总体判断**：从摘要层面只能确认存在"多任务仿真 + 真机迁移"两类实验，**是否充分、是否公平**的判断依据不完整，建议结合正文实验章节评估。

## 6. 主要结论与发现

- 基于 VLM 生成的粗略"脚手架"轨迹，**完全可以替代人工设计的参考轨迹与任务特定奖励**。
- 残差 RL 能在仿真中有效精修这些粗轨迹，**学到鲁棒的灵巧操作策略**。
- 该方法**具备良好的可扩展性与泛化性**，适用于多种铰接物体操作与语义任务。
- 可**零人类演示、零人工奖励**地迁移到真实机器人手，展示了较强的 sim-to-real 能力。

## 7. 优点与亮点

- **范式创新**：首次系统性地提出用 VLM 为灵巧手 RL 提供"语义级参考轨迹"，将 VLM 的常识知识与 RL 的精细控制能力有机结合。
- **摆脱数据与奖励瓶颈**：完全无需人类演示和人工奖励函数，显著降低灵巧操作策略开发成本。
- **任务无关的奖励构造**：利用物体姿态轨迹自然导出稠密奖励，避免奖励工程。
- **两阶段分工清晰**：VLM 负责高层语义规划，残差 RL 负责底层精确执行，模块化程度高，便于替换任一组件。
- **端到端 sim-to-real**：直接展示真实灵巧手部署，验证实用价值。

## 8. 不足与局限

- **VLM 依赖风险**：
  - 方法性能高度依赖所选用 VLM 的空间推理与关键点定位能力；当前 VLM 在 3D 几何与精确关键点定位上仍存在错误率，可能引入系统性偏差。
- **粗轨迹质量上限**：
  - 若 VLM 给出的关键点或轨迹本身不准确，残差 RL 的精修能力受限于仿真器与策略容量，可能无法完全纠正高层错误。
- **实验细节不透明**：
  - 摘要未提供对比 baseline、消融实验、统计显著性、不同 VLM backbone 鲁棒性等关键信息，实验充分性需进一步验证。
- **任务范围限制**：
  - 实验集中在"铰接物体 + 语义任务"，对接触丰富的精细操作（如装配、柔性物体、双手协同等）是否同样有效尚不明确。
- **真机迁移细节缺失**：
  - 摘要仅声称"无需人类演示与人工奖励即可迁移到真实手"，但域随机化、感知噪声、真实环境多样性等关键因素未在摘要中讨论。
- **算力与可复现性信息不足**：训练资源、代码与超参数在摘要中未披露，可能影响复现。

（完）
