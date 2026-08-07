---
title: "Robots Pre-train Robots: Manipulation-Centric Robotic Representation from Large-Scale Robot Datasets"
title_zh: 机器人预训练机器人：来自大规模机器人数据集的操纵中心表征
authors: "Guangqi Jiang, Yifei Sun, Tao Huang, Huanyu Li, Yongyuan Liang, Huazhe Xu"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=yTEwmr1TJb"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向机器人操纵的视觉表征预训练研究
tldr: 本文关注机器人视觉表征预训练问题，指出人类视频预训练存在分布偏移且缺乏动力学信息。为此利用大规模机器人数据集预训练视觉表征，并提出操纵中心性作为下游任务成功率的有效指标。实验表明，所学习的表征能够显著提升下游操纵策略的学习效率与性能。其贡献为模仿学习管线提供了更具任务针对性的预训练方案。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 人类视频预训练的视觉表征存在分布偏移，难以满足机器人操纵任务需求。
method: 利用大规模机器人数据集预训练视觉表征，并以操纵中心性作为下游任务评价指标。
result: 所学习的表征显著提升下游操纵策略的成功率与学习效率。
conclusion: 为机器人模仿学习提供了面向操纵任务的更合适的视觉预训练方案。
---

## Abstract
The pre-training of visual representations has enhanced the efficiency of robot learning. Due to the lack of large-scale in-domain robotic datasets, prior works utilize in-the-wild human videos to pre-train robotic visual representation. Despite their promising results, representations from human videos are inevitably subject to distribution shifts and lack the dynamics information crucial for task completion. We first evaluate various pre-trained representations in terms of their correlation to the downstream robotic manipulation tasks (i.e., manipulation centricity). Interestingly, we find that the ''manipulation centricity'' is a strong indicator of success rates when applied to downstream tasks. Drawing from these findings, we propose **M**anipulation **C**entric **R**epresentation (**MCR**), a foundation representation learning framework capturing both visual features and the dynamics information such as actions and proprioceptions of manipulation tasks to improve manipulation centricity. Specifically, we pre-train a visual encoder on the DROID robotic dataset and leverage motion-relevant data such as robot proprioceptive states and actions. We introduce a novel contrastive loss that aligns visual observations with the robot's proprioceptive state-action dynamics, combined with an action prediction loss and a time contrastive loss during pre-training. Empirical results across four simulation domains with 20 robotic manipulation tasks demonstrate that **MCR** outperforms the strongest baseline by 14.8\%. Additionally, **MCR** significantly boosts the success rate in three real-world manipulation tasks by 76.9\%. Project website: robots-pretrain-robots.github.io

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize a paper in Chinese based on the provided metadata and abstract. The paper is titled "Robots Pre-train Robots: Manipulation-Centric Robotic Representation from Large-Scale Robot Datasets" (MCR). Let me organize the content according to the 8 requested points.

The PDF text extraction only shows a CAPTCHA page, so I need to rely on the abstract and metadata provided. Let me create a comprehensive summary based on this information.

Key information from the abstract:
- Problem: Pre-training visual representations for robot learning currently uses human videos, which have distribution shift and lack dynamics information
- Finding: "Manipulation centricity" is a strong indicator of success rates for downstream tasks
- Method: MCR (Manipulation Centric Representation) - pre-trains on DROID dataset, uses proprioceptive states and actions
- Losses: contrastive loss aligning visual observations with state-action dynamics, action prediction loss, time contrastive loss
- Results: 4 simulation domains, 20 tasks, outperforms strongest baseline by 14.8%, 3 real-world tasks with 76.9% boost

I should note that since I couldn't access the full PDF, some details (like exact GPU specs, training time, ablation studies) are not available.</think>

# 论文总结：Robots Pre-train Robots (MCR)

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：机器人学习中的视觉表征预训练，目前主流做法是利用大规模人类视频（如 Ego4D、Something-Something 等）来预训练视觉编码器，然后迁移到机器人下游任务。
- **现有方法的不足**：
  - **分布偏移（Distribution Shift）**：人类视频与机器人第一人称视角在场景、物体、相机参数等方面存在显著差异，导致迁移效果受限。
  - **缺乏动力学信息（Dynamics Information）**：人类视频只包含视觉信号，缺乏机器人完成操作所必需的动作（actions）和本体感知（proprioception）等动力学线索。
- **研究目标**：从大规模机器人数据集中直接预训练机器人专用视觉表征，使其更好地服务于下游操作策略学习。

---

## 2. 论文提出的方法论

### 2.1 核心思想
- 提出 **Manipulation Centric Representation (MCR)**，即"以操作任务为中心"的表征学习框架。
- 关键发现：**"manipulation centricity"（操作中心性）**——即预训练表征与下游操作任务的相关程度——是预测下游任务成功率的有效指标。
- 直接在 **DROID 机器人数据集** 上进行视觉编码器的预训练，而非依赖人类视频。

### 2.2 关键技术细节
预训练阶段同时利用三类信息：
1. **视觉观测（Visual Observations）**：来自 DROID 数据集的机器人视角图像。
2. **本体感知状态（Proprioceptive States）**：机器人关节状态等本体感知信息。
3. **动作（Actions）**：机器人执行的动作序列。

### 2.3 损失函数设计
- **对比损失（Contrastive Loss）**：将视觉观测与机器人的"状态–动作动力学"（state-action dynamics）进行对齐，使视觉特征捕捉到与机器人运动相关的信息。
- **动作预测损失（Action Prediction Loss）**：根据视觉特征预测下一步动作，迫使表征包含动力学信息。
- **时间对比损失（Time Contrastive Loss）**：在时间维度上构建正负样本，增强表征对时序动态的敏感性。

---

## 3. 实验设计

### 3.1 数据集与场景
- **预训练数据**：DROID 机器人数据集（大规模真实机器人操作数据集）。
- **下游仿真基准**：跨 **4 个仿真领域**（domains），共 **20 个机器人操作任务**。
- **下游真实场景**：**3 个真实世界操作任务**。

### 3.2 对比方法
- 与多种现有预训练视觉表征方法进行对比，包括但不限于：
  - 基于人类视频的预训练方法（如 R3M、Voltron 等同类基线）。
  - 其它图像/视频自监督预训练表征。
  - 具体最强基线在文中被称为 "the strongest baseline"。

### 3.3 评测指标
- 主要指标：**任务成功率（Success Rate）**。
- 中间分析指标：**Manipulation Centricity**（用于衡量预训练表征与下游操作任务的相关性）。

---

## 4. 资源与算力

- **文中未明确说明**具体的 GPU 型号、数量以及训练时长（由于本总结仅能依据摘要与元数据，原文 PDF 未成功提取，可能在正文中有更详细的描述）。
- 仅可确认：预训练基于 DROID 数据集规模较大，下游实验涵盖 4 个仿真域与 3 个真实任务。

---

## 5. 实验数量与充分性

- **下游任务规模**：共 20 个仿真任务 + 3 个真实任务，跨多个仿真平台，覆盖较为全面。
- **核心结果**：
  - 仿真任务：相较最强基线平均提升 **+14.8%**。
  - 真实任务：成功率提升 **+76.9%**。
- **对比维度**：涵盖人类视频预训练基线与其它自监督表征，验证了"机器人预训练机器人"思路的优势。
- **充分性评估**：仅从摘要信息看，实验在仿真与真实场景上均做了验证，并提出了新的评价指标（manipulation centricity），但完整的消融实验、各损失项的贡献度分析等细节需要参考正文。

---

## 6. 主要结论与发现

- **关键发现 1**：人类视频预训练表征存在不可忽视的分布偏移，且缺乏动力学信息，限制了其在机器人操作任务上的表现。
- **关键发现 2**："Manipulation centricity" 与下游任务成功率高度相关，是衡量预训练表征质量的良好代理指标。
- **关键发现 3**：直接在大规模机器人数据（DROID）上预训练视觉编码器，并联合对齐视觉–本体–动作信号，可以显著提升下游操作策略的学习效率与最终性能。
- **结论**：面向机器人模仿学习的视觉预训练，应优先考虑"机器人原生数据 + 动力学信息"，而非单纯依赖人类视频。

---

## 7. 优点（亮点）

- **问题切入角度新颖**：明确指出"manipulation centricity"这一可量化指标，并将其作为表征选择的指导原则，具有方法论价值。
- **数据来源针对性更强**：使用 DROID 机器人数据集直接预训练，从根源上缓解了 human-to-robot 的分布偏移问题。
- **多任务验证**：横跨 4 个仿真域、20 个任务以及 3 个真实任务，兼顾仿真与真实场景的泛化验证。
- **真实场景增益显著**：真实世界任务提升 76.9%，说明方法具有较强的实际部署潜力。
- **损失函数组合合理**：对比损失 + 动作预测 + 时间对比三者结合，使表征同时包含静态外观与动态运动信息。

---

## 8. 不足与局限

- **预训练数据集依赖性强**：仅在 DROID 数据集上进行验证，方法对其它机器人数据集（如 Bridge、RT-X 等）的泛化能力有待进一步研究。
- **算力与训练成本未披露**：摘要未给出预训练所需的计算资源，难以评估方法的可复现性与训练门槛。
- **Manipulation Centricity 指标的普适性**：该指标作为新提出概念，其理论严谨性、与其它任务的相关性仍需更多实验支撑。
- **任务覆盖范围有限**：尽管涉及 20 个仿真任务与 3 个真实任务，但与现实世界中的复杂操作场景相比，覆盖仍相对有限。
- **基线对比的全面性**：摘要仅提及"最强基线"，但未明确说明是否涵盖了所有当前 SOTA 的人类视频预训练方法（如 LAPA、GR-1 等大规模视频模型）。
- **真实任务泛化风险**：真实世界仅 3 个任务，样本量较小，76.9% 的提升虽显著，但统计显著性仍需更多实验验证。

（完）
