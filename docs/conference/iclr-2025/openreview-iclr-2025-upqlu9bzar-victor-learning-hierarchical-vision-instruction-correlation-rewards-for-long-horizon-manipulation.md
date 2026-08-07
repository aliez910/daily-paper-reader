---
title: "VICtoR: Learning Hierarchical Vision-Instruction Correlation Rewards for Long-horizon Manipulation"
title_zh: VICtoR：面向长时序操纵的分层视觉-指令相关性奖励学习
authors: "Kuo-Han Hung, Pang-Chi Lo, Jia-Fong Yeh, Han-Yuan Hsu, Yi-Ting Chen, Winston H. Hsu"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=UpQLu9bzAR"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向长时序机器人操纵任务的分层奖励模型
tldr: 本文针对长时序机器人操纵中奖励建模困难的问题，提出分层视觉-指令相关性奖励模型 VICtoR，仅利用基础动作示范即可训练。该方法通过分阶段评估任务进度，克服了现有 VIC 方法在子阶段感知、任务复杂度建模与物体状态估计方面的不足。实验表明，VICtoR 能够在多阶段任务中提供精确的奖励信号，有效支持复杂操纵策略的学习。其贡献为长时序操纵任务的奖励学习提供了更具结构感的新思路。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有 VIC 奖励方法在长时序操纵任务中缺乏子阶段感知和物体状态估计能力。
method: 提出分层视觉-指令相关性奖励模型 VICtoR，分阶段评估任务进度并提供精确奖励信号。
result: 在长时序操纵任务上能够给出精准的进度奖励，验证了分层结构对复杂任务的有效性。
conclusion: 为长时序机器人操纵的奖励学习提供了一种结构化、可分阶段建模的新方法。
---

## Abstract
We study reward models for long-horizon manipulation by learning from action-free videos and language instructions, which we term the visual-instruction correlation (VIC) problem. Existing VIC methods face challenges in learning rewards for long-horizon tasks due to their lack of sub-stage awareness, difficulty in modeling task complexities, and inadequate object state estimation. To address these challenges,
we introduce VICtoR, a novel hierarchical VIC reward model capable of providing effective reward signals for long-horizon manipulation tasks. Trained solely on primitive motion demonstrations, VICtoR effectively provides precise reward signals for long-horizon tasks by assessing task progress at various stages using a novel stage detector and motion progress evaluator. We conducted extensive experiments in both simulated and real-world datasets. The results suggest that VICtoR outperformed the best existing methods, achieving a 43% improvement in success rates for long-horizon tasks. Our project page can be found at https://cmlab-victor.github.io/cmlab-vicotor.github.io/.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "VICtoR: Learning Hierarchical Vision-Instruction Correlation Rewards for Long-horizon Manipulation" based on the provided abstract and metadata. Let me analyze the content carefully.

The paper is about:
- Long-horizon manipulation reward learning
- Learning from action-free videos and language instructions (VIC problem)
- Existing VIC methods have limitations: lack of sub-stage awareness, difficulty modeling task complexity, inadequate object state estimation
- Proposes VICtoR: hierarchical VIC reward model
- Trained on primitive motion demonstrations
- Uses stage detector and motion progress evaluator
- 43% improvement in success rates for long-horizon tasks
- Both simulated and real-world experiments
- ICLR 2025 accepted

I need to organize the summary according to the 8 points requested. Since the full PDF content is just a verification page, I'll rely on the abstract and metadata provided. I should be clear about what information is available and what isn't (e.g., specific compute resources, detailed experimental numbers).

Let me structure the response carefully in Markdown.</think>

# VICtoR 论文总结

## 1. 核心问题与研究动机

- **研究背景**：在机器人长时序操纵（long-horizon manipulation）任务中，如何设计有效的奖励信号是强化学习与模仿学习中的核心难题。
- **具体问题**：作者将其定义为**视觉-指令相关性（Visual-Instruction Correlation, VIC）问题**——即仅利用**不含动作的视频**与**语言指令**来学习奖励模型。
- **现有方法的不足**：
  - 缺乏**子阶段感知（sub-stage awareness）**能力，无法判断任务进行到哪一步；
  - 对**任务复杂度**建模困难，难以处理多阶段任务；
  - **物体状态估计**能力不足，导致奖励信号不精确。

## 2. 方法论

### 核心思想
提出 **VICtoR（Vision-Instruction Correlation Rewards）**，一种**分层（hierarchical）VIC 奖励模型**，通过对任务进度的分阶段评估，为长时序操纵提供精确的奖励信号。

### 关键组件
- **Stage Detector（阶段检测器）**：判断当前任务处于哪个子阶段（sub-stage），提供粗粒度的任务进度估计。
- **Motion Progress Evaluator（运动进度评估器）**：在子阶段内部进一步评估动作完成的精细程度，提供细粒度的奖励。
- **训练数据**：仅使用**原始动作示范（primitive motion demonstrations）**，无需动作标签的视频或专家奖励。

### 流程概述
1. 输入为当前视觉观察 + 语言指令；
2. Stage Detector 输出任务所处的阶段；
3. Motion Progress Evaluator 在该阶段内估计完成度；
4. 综合两者输出最终奖励信号，用于策略学习。

## 3. 实验设计

- **数据集/场景**：
  - **仿真环境**（具体仿真器名称在提供的文本中未明确提及）；
  - **真实世界数据集**（real-world datasets），验证从仿真到真实的迁移能力。
- **Benchmark**：论文聚焦**长时序操纵任务**（multi-stage tasks），这是核心评测场景。
- **对比方法**：与**现有最佳 VIC 方法（best existing methods）**进行对比，但具体对比方法名称在摘要中未列出。
- **核心指标**：任务成功率（success rate）。

## 4. 资源与算力

- 论文摘要及所提供的元数据中**未明确提及** GPU 型号、数量、训练时长等算力信息。
- 仅提供项目主页：https://cmlab-victor.github.io/cmlab-vicotor.github.io/，详细资源信息可能需要查阅正文或附录。

## 5. 实验数量与充分性

- 从已有信息看：
  - 进行了**仿真 + 真实世界**两类实验，覆盖较广；
  - 主结果报告 **43% 的成功率提升**（相对于最强基线），表明在长时序任务上提升显著。
- **不足之处**：
  - 摘要中**未提及消融实验（ablation study）**的具体数量；
  - 未说明实验涉及多少任务种类、多少随机种子、统计显著性检验等细节；
  - 公平性方面，仅声明与"最佳现有方法"对比，但具体基线数量与多样性未知，客观性需要进一步核实。

## 6. 主要结论与发现

- VICtoR 在长时序操纵任务上**显著优于现有 VIC 方法**，成功率提升 **43%**；
- **分层结构**（stage detector + motion progress evaluator）的设计能有效解决子阶段感知与物体状态估计问题；
- 仅凭**基础动作示范**即可训练，无需昂贵的动作标签或专家奖励；
- 该方法为长时序操纵奖励学习提供了一种**结构化、可分阶段建模**的新范式。

## 7. 优点

- **问题定义清晰**：将"动作无关视频 + 语言指令 → 奖励"抽象为 VIC 问题，定位明确。
- **分层设计新颖**：将奖励分解为"阶段判断 + 进度评估"两层，分别处理粗粒度与细粒度信号，逻辑合理。
- **训练数据要求低**：仅需 primitive motion demonstrations，降低了数据获取成本。
- **仿真 + 真实世界双验证**：兼顾算法验证与实用迁移性。
- **提升幅度显著**：43% 的成功率提升在长时序任务中是非常可观的结果。

## 8. 不足与局限

- **信息有限**：摘要较短，缺少对方法细节、理论分析、超参数影响的描述。
- **对比基线不充分**：仅与"最佳现有方法"对比，未说明是否涵盖多种类型（如基于偏好、基于语言、基于视频预测等不同范式）。
- **泛化性未验证**：是否对未见过的物体、指令、任务结构具备鲁棒性，摘要中未给出。
- **物体状态估计仍可能受限**：尽管作者声称解决了该问题，但在遮挡、视角变化、相似物体等复杂视觉场景下的表现未知。
- **应用限制**：方法依赖语言指令描述，对语言歧义或任务描述模糊场景的适用性需进一步研究。
- **算力与可复现性信息缺失**：GPU 资源、训练时间、代码开源情况（项目主页是否提供代码）未在摘要中明确。
- **潜在的偏差风险**：未明确指出实验是否在多种随机种子下进行统计检验，可能存在过拟合或单一场景下的偶然优势。

（完）
