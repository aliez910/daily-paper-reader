---
title: Closed-Loop Long-Horizon Robotic Planning via Equilibrium Sequence Modeling
title_zh: 通过均衡序列建模实现闭环长期机器人规划
authors: "Jinghan Li, Zhicheng Sun, Yadong MU"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=MCqlamfhAy"
tags: ["query:rob-il"]
score: 8.0
evidence: 提出通过均衡序列建模实现闭环机器人规划，包含自我修正机制
tldr: 该论文针对长时间跨度任务规划中语言模型容易出错的问题，提出了一种自修正的闭环规划方法。通过均衡序列建模，规划器可以在监督学习下迭代优化草案计划直至收敛，无需额外验证器或奖励模型。实验表明该方法在长程任务规划中显著提高了成功率，为实现鲁棒的机器人自主规划提供了新框架。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 语言模型在长程规划中容易出错，且缺乏自我修正能力。
method: 提出自修正规划框架，利用均衡序列建模迭代优化计划，端到端训练。
result: 在长程规划任务上成功率显著提升。
conclusion: 自我修正和均衡序列建模是实现可靠长期规划的关键。
---

## Abstract
In the endeavor to make autonomous robots take actions, task planning is a major challenge that requires translating high-level task descriptions to long-horizon action sequences. Despite recent advances in language model agents, they remain prone to planning errors and limited in their ability to plan ahead. To address these limitations in robotic planning, we advocate a self-refining scheme that iteratively refines a draft plan until an equilibrium is reached. Remarkably, this process can be optimized end-to-end from an analytical perspective without the need to curate additional verifiers or reward models, allowing us to train self-refining planners in a simple supervised learning fashion. Meanwhile, a nested equilibrium sequence modeling procedure is devised for efficient closed-loop planning that incorporates useful feedback from the environment (or an internal world model). Our method is evaluated on the VirtualHome-Env benchmark, showing advanced performance with improved scaling w.r.t. inference-time computation. Code is available at https://github.com/anonymous-icml-2025/equilibrium-planner.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- **研究动机**：语言模型在长时域机器人任务规划中容易产生错误，且缺乏自我修正能力，导致规划结果可靠性低。
- **背景挑战**：自主机器人需将高层任务描述转换为长时间跨度的动作序列，现有方法受限于模型的前瞻能力与错误累积问题。
- **核心意义**：本文提出一种闭环、自修正的规划框架，旨在不依赖额外验证器或奖励模型的前提下提升长期规划的鲁棒性与成功率。

## 2. 提出的方法论
- **核心思想**：采用自精炼（self-refining）机制，迭代优化一个初始草案计划，直至计划达到均衡状态（equilibrium），从而收敛到合理方案。该过程可以从解析角度进行端到端优化，仅需监督学习范式，无需专门设计验证器或奖励模型。
- **关键技术细节**：
  - **均衡序列建模（Equilibrium Sequence Modeling）**：将规划视为一个迭代序列修正过程，模型重复输入当前计划草案并输出改进版本，直到相邻两次迭代的输出不再显著变化（均衡）。这允许模型在推断时利用更多计算来提升性能（scaling w.r.t. inference-time computation）。
  - **闭环规划（Closed‑Loop Planning）**：嵌套一种均衡序列建模过程，使计划能够吸收来自环境（或内部世界模型）的反馈，实现动态调整而非一次性生成。
- **算法流程（文字说明）**：
  1. 给定高层任务描述，生成初始长的动作序列（草案）。
  2. 将当前草案与任务提示输入模型中，模型输出修正后的计划。
  3. 重复上一步，直至计划变化收敛（达到均衡点）。
  4. 若环境中观察到新反馈（如状态变化），则将反馈信息融入计划，继续迭代修正，形成闭环。
- **训练方式**：整个框架通过标准的监督学习端到端训练，优化目标是使模型学会从任意草案逐步迭代到正确计划，无需额外的训练信号。

## 3. 实验设计
- **基准环境**：VirtualHome‑Env，一个用于模拟家庭环境中机器人执行长任务的标准仿真平台。
- **任务与评价指标**：面向长时域任务规划（long‑horizon task planning），主要评价指标为任务**成功率**。
- **对比方法**：论文摘要中提到“showing advanced performance with improved scaling w.r.t. inference‑time computation”，但未明确列举所对比的基线模型。元数据结果描述为“在长程规划任务上成功率显著提升”，因此可以推断至少与标准语言模型规划基线进行了比较。
- **说明**：由于缺乏全文，无法获取更详细的对比方法列表、任务数量或配置；仅能确认使用了单个模拟环境。

## 4. 资源与算力
- **未明确说明**：论文正文中（包括摘要和元数据）未提及训练所使用 GPU 型号、数量、训练时长或任何其他算力资源信息。无法评估计算成本与可复现性。

## 5. 实验数量与充分性
- **实验规模**：从现有信息看，实验集中在 VirtualHome‑Env 一个基准上。虽可能在多种任务长度或条件下进行了测试，但具体组数（如不同任务数、消融实验分支）未公布。
- **充分性评估**：受限于信息透明度，难以判断实验的全面性。
  - 优点：专注长时域任务，成功率的提升有明确陈述，并展示了推理时计算规模扩展的正向作用。
  - 不足：缺少与多种基线（特别是强化学习、分层规划等方法）的系统对比；缺乏对均衡策略收敛性、推理迭代次数的详细消融；未提及零样本泛化或迁移实验。
  - 总体而言，实验设计在单一基准上初步验证了方法有效性，但充分性和公平性因缺乏细节而无法准确判断。

## 6. 主要结论与发现
- **结论**：本文提出的闭环均衡序列规划方法（自修正、监督训练）在长时域机器人规划任务上取得了显著的成功率提升，并且在推理时计算越多（更多迭代）性能越高。
- **发现**：
  - 自我修正与均衡收敛机制是实现可靠长期规划的关键。
  - 不需要额外的验证器或奖励模型，仅通过端到端监督学习即可学会自修正。
  - 闭环规划通过融入环境反馈进一步提高了鲁棒性。

## 7. 优点
- **方法层面**：
  - **自我修正能力**：模型自动迭代优化计划，无需外部验证器，简化训练流程。
  - **闭环整合**：将环境反馈纳入迭代过程，提升规划对动态变化的适应性。
  - **推理时计算可扩展**：通过调整迭代次数，实现性能与计算灵活权衡。
  - **训练简便**：仅需标准监督学习，不依赖强化学习或复杂奖励设计，降低了训练门槛。
- **实验层面**：
  - 在长时域规划这一关键问题上给出了正面结果，并提供开源代码，便于复现与扩展。

## 8. 不足与局限
- **实验覆盖不足**：只评测了一个模拟环境（VirtualHome‑Env），缺乏真实机器人平台验证；与最新的语言模型规划专家或分层方法的全面对比未公开。
- **评估指标单一**：仅使用成功率，未提供场景多样性、规划长度、执行时间或安全性等指标的详细分析。
- **可解释性欠缺**：均衡迭代的具体停止条件、收敛保证未在摘要中讨论；更深入的理论分析（如均衡存在性）缺失。
- **依赖环境反馈**：闭环部分需要来自环境（或世界模型）的反馈信号，若环境模型有偏或难以获取真实反馈，可能影响性能。
- **资源成本未知**：未报告训练或推理的计算消耗，难以评估实际部署成本。
- **泛化能力未讨论**：未说明对未见任务或新环境领域是否同样有效。

（完）
