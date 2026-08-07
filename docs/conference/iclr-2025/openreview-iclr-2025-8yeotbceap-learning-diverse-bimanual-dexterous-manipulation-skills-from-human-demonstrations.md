---
title: Learning Diverse Bimanual Dexterous Manipulation Skills from Human Demonstrations
title_zh: 从人类示中学习多样化双手灵巧操作技能
authors: "Bohan Zhou, Haoqi Yuan, Yuhui Fu, Zongqing Lu"
date: 2024-09-17
pdf: "https://openreview.net/pdf?id=8yEoTBceap"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过模仿学习从人类示中学习多样化双手灵巧操作
tldr: 本文针对双手灵巧操作中高维动作空间与任务多样性受限的问题，提出了BiDexHD框架。该框架整合多个现有双手数据集进行统一任务构建，并采用教师-学生策略学习从丰富的人类示中高效提取多样技能。相比依赖精心设计奖励函数的强化学习方法，该方法显著降低了任务工程成本。实验表明BiDexHD在多种复杂双手操作任务上均取得了优于现有方法的性能。该工作推动了通用双手灵巧操作技能的规模化学习。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 双手灵巧操作动作空间高维且任务复杂，现有RL方法奖励工程代价大。
method: 整合多个双手数据集并采用教师-学生模仿学习策略框架。
result: 在多种复杂双手操作任务上取得优于现有强化学习方法的效果。
conclusion: 基于人类示的模仿学习是规模化学习通用双手操作技能的有效路径。
---

## Abstract
Bimanual dexterous manipulation is a critical yet underexplored area in robotics. Its high-dimensional action space and inherent task complexity present significant challenges for policy learning, and the limited task diversity in existing benchmarks hinders general-purpose skill development. Existing approaches largely depend on reinforcement learning, often constrained by intricately designed reward functions tailored to a narrow set of tasks. In this work, we present a novel approach for efficiently learning diverse bimanual dexterous skills from abundant human demonstrations. Specifically, we introduce BiDexHD, a framework that unifies task construction from existing bimanual datasets and employs teacher-student policy learning to address all tasks. The teacher learns state-based policies using a general two-stage reward function across tasks with shared behaviors, while the student distills the learned multi-task policies into a vision-based policy. With BiDexHD, scalable learning of numerous bimanual dexterous skills from auto-constructed tasks becomes feasible, offering promising advances toward universal bimanual dexterous manipulation. Our empirical evaluation on the TACO dataset, spanning 141 tasks across six categories, demonstrates a task fulfillment rate of 74.59% on trained tasks and 51.07% on unseen tasks, showcasing the effectiveness and competitive zero-shot generalization capabilities of BiDexHD. For videos and more information, visit our project page.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of a paper about "Learning Diverse Bimanual Dexterous Manipulation Skills from Human Demonstrations" (BiDexHD). Let me organize a structured summary based on the abstract and metadata provided.

The paper is about bimanual dexterous manipulation, which is challenging due to high-dimensional action space and task complexity. The authors propose BiDexHD framework that:
1. Unifies task construction from existing bimanual datasets
2. Uses teacher-student policy learning
3. Teacher learns state-based policies using a general two-stage reward function
4. Student distills into vision-based policy
5. Evaluation on TACO dataset with 141 tasks across 6 categories
6. Achieves 74.59% on trained tasks and 51.07% on unseen tasks

Let me write a comprehensive summary in Chinese following the user's outline.</think>

# 论文总结：从人类示教中学习多样化双手灵巧操作技能（BiDexHD）

## 1. 核心问题与研究动机

- **研究领域**：双手灵巧操作（Bimanual Dexterous Manipulation）是机器人学中关键但尚未充分探索的方向。
- **核心挑战**：
  - 动作空间高维，双手灵巧手通常具有 20+ 个自由度；
  - 任务本身复杂度高，任务多样性受限；
  - 现有基准（benchmark）任务种类有限，阻碍通用技能的获取。
- **现有方法局限**：多数工作依赖强化学习（RL），但 RL 高度依赖为窄范围任务精心设计的奖励函数，工程代价巨大。
- **本文目标**：探索如何高效利用大规模人类示教数据，学习多样化的双手灵巧操作技能，绕开奖励工程难题。

## 2. 方法论：BiDexHD 框架

- **核心思想**：将多个已有双手数据集统一为任务集合，并以教师—学生模仿学习策略完成跨任务学习与视觉策略蒸馏。
- **关键技术细节**：
  1. **统一任务构建（Unified Task Construction）**
     - 整合多个现成双手数据集（如 TACO 等），将其中的轨迹、状态、动作等信息标注统一化；
     - 基于共享行为类型将任务自然划分，为跨任务策略学习提供结构化基础。
  2. **教师—学生策略学习（Teacher-Student Policy Learning）**
     - **教师策略（Teacher）**：基于状态（state-based）输入进行学习，使用一个**通用的两阶段奖励函数（general two-stage reward function）**覆盖具有共享行为模式的多个任务。两阶段设计通常对应任务的接近—执行等典型阶段，避免为每个任务单独设计奖励。
     - **学生策略（Student）**：将教师学到的多任务状态策略蒸馏为**基于视觉（vision-based）的策略**，通过观测输入实现可用于真实环境的端到端控制。
  3. **算法流程**（文字概述）：
     - 数据收集与统一 → 任务划分 → 教师策略多任务 RL（两阶段奖励）→ 教师策略生成伪标签 → 学生策略模仿蒸馏 → 视觉策略部署。
- **核心优势**：消除任务级奖励工程的成本，使规模化学习成为可能。

## 3. 实验设计与数据集

- **数据集 / 场景**：使用 **TACO 数据集**进行实证评估。
- **Benchmark 规模**：覆盖 **141 个任务**，分为 **6 个类别**。
- **评估设置**：
  - 已见任务（trained tasks）；
  - 未见任务（unseen tasks）——用于检验零样本泛化能力。
- **对比方法**：文章摘要中明确与依赖 RL 的现有方法进行比较（具体对比基线需参考正文，此处基于可得信息说明）。主要对比目标为当前基于 RL 的双手灵巧操作方法。

## 4. 资源与算力

- **本文摘要中未明确说明**所使用 GPU 型号、数量、训练时长等算力相关信息。
- 若需补充应进一步检索正文 / 附录。

## 5. 实验数量与充分性

- **实验规模**：实验覆盖 **141 个任务 × 2 种评估场景**（已见/未见），任务数量较为可观。
- **评估指标**：报告 **任务完成率（Task Fulfillment Rate）**，数值如下：
  - 已见任务：**74.59%**；
  - 未见任务：**51.07%**（零样本）。
- **充分性评估**：
  - 优点：任务规模大、覆盖类别丰富，验证了通用双手操作的可扩展性；
  - 不足：从摘要信息看，未明确给出消融实验（如去掉教师—学生蒸馏、去掉两阶段奖励等）的对比结果，亦未给出与具体方法的逐项数值对比，因此实验充分性需结合正文才能充分评估。

## 6. 主要结论与发现

- BiDexHD 能够在仅使用人类示教与统一任务构建的条件下，对大量双手任务进行高效学习；
- 教师—学生框架 + 通用两阶段奖励显著降低奖励工程成本；
- 在已见任务上取得 **74.59%** 的完成率，说明大规模任务学习可行；
- 在未见任务上达到 **51.07%**，展现具有竞争力的零样本泛化能力；
- 表明基于人类示教的模仿学习是规模化学习通用双手灵巧操作技能的有效路径。

## 7. 优点与亮点

- **范式新颖**：以模仿学习替代奖励工程密集型的 RL，降低工程成本；
- **数据复用**：通过统一多个数据集，大幅扩展任务空间；
- **两阶段通用奖励**：巧妙利用任务结构相似性，缓解奖励设计难题；
- **教师—学生架构**：充分利用状态策略的训练效率与视觉策略的可部署性；
- **泛化能力**：在 141 个任务的训练范围之外仍能完成约 51% 的任务，体现零样本能力。

## 8. 不足与局限

- **算力信息缺失**：摘要未给出 GPU 类型、数量、训练时长等关键资源信息，难以评估方法的实际部署成本；
- **实验细节有限**：在摘要信息中未明确列出消融实验、基线对比的具体数值；
- **依赖人类示教**：方法性能上限受数据集规模与质量限制，可能继承示教数据中的偏差（selection bias、demonstrator bias）；
- **任务空间覆盖**：虽然有 141 个任务，但仍未涵盖更广泛的真实世界双手操作场景（如工具使用、柔性物体操作等）；
- **零样本泛化局限**：未见任务完成率（51.07%）相较已见任务（74.59%）仍有约 23 个百分点的下降，说明任务间共享模式仍有提升空间；
- **视觉策略鲁棒性**：未在摘要中讨论视觉策略对噪声、光照、相机位姿变化的鲁棒性评估。

（完）
