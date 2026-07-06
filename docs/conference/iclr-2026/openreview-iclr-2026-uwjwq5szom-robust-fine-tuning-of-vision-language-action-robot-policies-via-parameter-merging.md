---
title: Robust Fine-tuning of Vision-Language-Action Robot Policies via Parameter Merging
title_zh: 通过参数合并实现视觉-语言-动作机器人策略的鲁棒微调
authors: "Yajat Yadav, Zhiyuan Zhou, Andrew Wagenmaker, Karl Pertsch, Sergey Levine"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=uWJwQ5SZoM"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过参数合并实现通用VLA机器人策略的鲁棒微调
tldr: 通用机器人VLA策略在大规模数据上训练后具备广泛泛化能力，但针对新任务的少量示教微调常导致过拟合，丧失原有通用能力并在新任务内也难以泛化。为此，本文提出基于参数合并的微调方法，在保留通用策略原有泛化能力的同时将新技能稳健整合到单一策略中。实验表明该方法在吸收新技能的同时维持了对多样化任务的广泛覆盖能力，对构建持续可扩展的通用操作策略具有重要意义。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 通用VLA策略在新任务少量示教微调时易过拟合，丧失原有泛化能力。
method: 提出参数合并的微调方法，将新任务参数与原通用策略参数融合以保留泛化能力。
result: 该方法能在学习新技能的同时维持对多样化通用任务的鲁棒执行能力。
conclusion: 工作为通用机器人策略在新任务上的持续学习与稳健扩展提供了有效方案。
---

## Abstract
Generalist robot policies, trained on large and diverse datasets, have demonstrated the ability to generalize across a wide spectrum of behaviors, enabling a single policy to act in varied real-world environments. However, they still fall short on new tasks not covered in the training data. When finetuned on limited demonstrations of a new task, these policies often overfit to the specific demonstrations---not only losing their prior abilities to solve a wide variety of generalist tasks but also failing to generalize within the new task itself. In this work, we aim to develop a method that preserves the generalization capabilities of the generalist policy during finetuning, allowing a single policy to robustly incorporate a new skill into its repertoire. Our goal is a single policy that both learns to generalize to variations of the new task and retains the broad competencies gained from pretraining. We show that this can be achieved through a simple yet effective strategy: interpolating the weights of a finetuned model with that of the pretrained model. We show, across extensive simulated and real-world experiments, that such model merging produces a single model that inherits the generalist abilities of the base model and learns to solve the new task robustly, outperforming both the pretrained and finetuned model on out-of-distribution variations of the new task. Moreover, we show that model merging enables continual acquisition of new skills in a lifelong learning setting, without sacrificing previously learned generalist abilities.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Robust Fine-tuning of Vision-Language-Action Robot Policies via Parameter Merging" based on the provided metadata and abstract. Let me analyze the content and structure the response according to the 8 requested points.

Key information from the paper:
- Problem: Generalist VLA (Vision-Language-Action) robot policies overfit when fine-tuned on limited new task demonstrations, losing prior generalization
- Method: Simple weight interpolation between fine-tuned and pretrained model parameters
- Experiments: Simulated and real-world experiments
- Result: Merged model inherits generalist abilities + learns new task robustly, outperforms both pretrained and finetuned models on OOD variations
- Also enables continual/lifelong learning of new skills
- Conference: ICLR 2026
- Authors: Yajat Yadav, Zhiyuan Zhou, Andrew Wagenmaker, Karl Pertsch, Sergey Levine
- Date: 2026-01-26

Since the actual PDF content wasn't accessible (only the abstract and metadata were provided), I should note this limitation where appropriate, especially for resource/compute details and specific experimental numbers.
</think>
# 论文总结：通过参数合并实现视觉-语言-动作机器人策略的鲁棒微调

## 1. 核心问题与研究动机

- **背景**：在大规模、多样化数据上训练的通用机器人 VLA（Vision-Language-Action）策略，已展现出在多种真实环境与任务上的广泛泛化能力。
- **核心问题**：此类通用策略在面对训练数据未覆盖的新任务时，性能仍存在明显不足；通常的解决方案是使用少量新任务示教数据进行微调，但微调过程会带来以下两类显著的副作用：
  1. **灾难性遗忘（Catastrophic Forgetting）**：策略丧失原有在大量通用任务上的泛化能力。
  2. **新任务内过拟合**：在少量示教数据上过度拟合，导致在新任务本身的分布外（OOD）变体上表现不佳。
- **研究目标**：在微调过程中同时实现"学习新技能 + 保留通用泛化能力"，最终得到一个既能解决新任务变体、又能执行原有广泛任务的统一单一策略。

## 2. 方法论

- **核心思想**：采用**模型参数合并（Model Merging / Weight Interpolation）** 的极简策略——将微调后模型的参数与原始预训练模型的参数进行线性插值（加权平均）。
- **关键技术细节**：
  - 给定预训练模型权重 $\theta_{\text{pretrained}}$ 与针对新任务微调后的模型权重 $\theta_{\text{finetuned}}$，合并后模型参数为：
  
    $$\theta_{\text{merged}} = \alpha \cdot \theta_{\text{pretrained}} + (1 - \alpha) \cdot \theta_{\text{finetuned}}$$
    
    其中 $\alpha$ 为插值系数，控制"保留原通用能力"与"融入新技能"之间的权衡。
  - 整个流程无需额外训练过程，仅在参数空间进行一次插值，是典型的**训练后（post-hoc）模型融合**思路。
  - 同样可推广至**终身学习（Lifelong / Continual Learning）** 场景：依次将多个新技能与基础模型参数合并，使单一模型可持续累积新能力而不遗忘旧能力。
- **算法流程（文字描述）**：
  1. 在大规模数据集上预训练通用 VLA 策略；
  2. 使用少量新任务示教数据对预训练策略进行微调，得到任务专用模型；
  3. 在参数空间对预训练模型与微调模型进行加权插值，得到合并后的统一策略；
  4. 推理阶段直接使用合并后的单一模型。

## 3. 实验设计

- **数据集与场景**：
  - 同时包含**仿真环境**与**真实世界（real-world）** 机器人操作实验。
  - 涉及**新任务**及其**分布外（OOD）变体**（例如背景、物体外观、摆放位置等扰动），用以评估在新任务内的鲁棒泛化能力。
  - 评估通用能力时覆盖**多样化任务集合**，以验证对原始通用能力的保持。
- **Benchmark**：论文依托通用 VLA 机器人策略的设定，对比的"基准"既包括原预训练模型（在 OOD 新任务上的表现），也包括直接微调后的模型（在通用任务上的遗忘程度）。
- **对比方法**：
  - 预训练基线模型（Pre-trained model）；
  - 直接在新任务数据上微调的模型（Fine-tuned model）；
  - 本文提出的**参数合并模型（Merged model）**。
- **评估维度**：
  - 新任务 OOD 变体上的成功率；
  - 原通用任务集合上的成功率（衡量是否发生遗忘）；
  - 终身学习场景下顺序学习多个新技能时各任务的保持与学习情况。

## 4. 资源与算力

- 在所提供的论文元数据与可访问的摘要内容中，**未明确披露**具体的 GPU 型号、数量、训练时长或总算力消耗。
- 鉴于本文方法的核心步骤仅为"参数插值"（不涉及额外大规模训练），其相对额外算力开销极低；主要的算力消耗集中在预训练与微调阶段，而这两阶段的资源使用情况在可获得的文本中未被详细说明。
- 建议在引用时参考正文中的实验设置章节以获取更精确信息。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 同时覆盖**仿真**与**真实世界**两类场景；
  - 既包含**单任务新技能学习**，也包含**终身/持续学习多任务**的设置；
  - 既评估了**新任务内的 OOD 鲁棒性**，也评估了**通用任务上的能力保持**。
- **充分性**：
  - 总体而言，实验设计在"新任务学习"与"通用能力保持"两个维度上形成了较完整的对照，方法评估较为全面。
  - 不足之处（可从可获取内容中推断）：缺少对**不同插值系数 $\alpha$** 系统性的消融讨论细节、缺少与**其他正则化/抗遗忘方法**（如 EWC、LoRA、Adapter 等）的直接对比（仅从摘要层面无法确认正文是否补充）。
  - 由于 PDF 全文未能成功抓取，实验的具体数量（任务数、试验次数、成功率数值等）无法逐项核实，需以正文表格为准。

## 6. 主要结论与发现

- **参数合并简单有效**：仅通过对预训练模型与微调模型参数进行线性插值，就能得到一个同时具备"新任务鲁棒泛化"与"原通用能力保持"的单一策略。
- **同时超越两侧基线**：合并模型在新任务的 OOD 变体上**同时优于**预训练模型（提升新任务能力）和纯微调模型（保留泛化能力）。
- **终身学习可行**：在顺序学习多个新技能的持续学习场景下，模型合并可有效**避免灾难性遗忘**，使单一模型能够不断扩展技能库。
- **实践意义**：为构建可扩展、持续可增长的通用机器人操作策略提供了一条**低开销、易部署**的技术路径。

## 7. 优点

- **方法极简**：核心仅为一次参数加权平均，无需额外训练过程，易于实现，工程开销低。
- **双目标兼顾**：在单一模型中同时解决"学习新技能"与"保留通用能力"两个目标，避免维护多个模型副本。
- **可扩展至持续学习**：自然支持终身/持续学习场景中技能的逐步累积。
- **实验覆盖较全面**：仿真+真实世界、新任务 OOD+通用任务保持、单技能+多技能顺序学习多维度评估。
- **实用性高**：对部署阶段非常友好，合并后的单一模型可直接替代原有策略，无需复杂的运行时调度。

## 8. 不足与局限

- **超参数依赖**：合并性能对插值系数 $\alpha$ 较为敏感，不同任务或模型可能需要不同的最优 $\alpha$；摘要与元数据未明确说明如何自动选择或调优。
- **缺乏方法对比**：在可获取内容中未充分呈现与其他抗遗忘/参数高效微调方法（如 LoRA、Adapter、EWC、Knowledge Distillation 等）的对比，难以判断相对优势。
- **理论解释不足**：摘要未讨论为何简单的线性插值能在如此复杂的 VLA 策略上同时避免过拟合与遗忘，缺乏理论或经验性机理分析。
- **实验可复现性信息有限**：所提供材料中未包含训练数据规模、任务数、试验次数、成功率等关键定量指标，需结合正文核实。
- **任务与模态的泛化边界**：仅在 VLA 机器人策略上验证，方法是否可推广到其他类型的大模型（如纯视觉-语言模型）仍未知。
- **数据偏差风险**：新任务的少量示教数据可能存在演示者偏差（demonstrator bias），合并策略虽缓解过拟合，但无法完全消除数据本身带来的偏差。
- **应用限制**：对于与原预训练数据分布**差异极大**的新任务，简单的线性插值可能不足以融合新能力，方法的适用边界有待进一步研究。

（完）
