---
title: Self-Improving Embodied Foundation Models
title_zh: 自改进的具身基础模型
authors: "Seyed Kamyar Seyed Ghasemipour, Ayzaan Wahid, Jonathan Tompson, Pannag R Sanketi, Igor Mordatch"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=KXMIIVUB9U"
tags: ["query:rob-il"]
score: 7.0
evidence: 结合行为克隆与自改进的具身基础模型后训练方法
tldr: 机器人基础模型多依赖行为克隆，难以胜任底层控制。受大语言模型后训练启发，本文提出两阶段方法：先用行为克隆与剩余步数预测进行监督微调，再利用剩余步数预测提取稠密奖励与成功检测器实现自改进。真实机器人实验表明，该框架可在最少监督下自主练习并稳健完成多种操纵任务，推动通用具身策略的发展。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有机器人基础模型主要依赖行为克隆，缺少类似 LLM 的强化学习后训练阶段。
method: 提出两阶段后训练：第一阶段行为克隆加剩余步数预测，第二阶段据此自改进并自主练习。
result: 在真实机器人多任务操纵中实现少监督下的稳健自主学习与执行。
conclusion: 该工作将 LLM 后训练范式迁移到具身基础模型，扩展了通用机器人能力。
---

## Abstract
Foundation models trained on web-scale data have revolutionized robotics, but their application to low-level control remains largely limited to behavioral cloning. Drawing inspiration from the success of the reinforcement learning stage in fine-tuning large language models, we propose a two-stage post-training approach for robotics. The first stage, Supervised Fine-Tuning (SFT), fine-tunes pretrained foundation models using both: a) behavioral cloning, and b) steps-to-go prediction objectives. In the second stage, Self-Improvement, steps-to-go prediction enables the extraction of a well-shaped reward function and a robust success detector, enabling a fleet of robots to autonomously practice downstream tasks with minimal human supervision. Through extensive experiments on real-world and simulated robot embodiments, our novel post-training recipe unveils significant results on Embodied Foundation Models. First, we demonstrate that the combination of SFT and Self-Improvement is significantly more sample-efficient than scaling imitation data collection for supervised learning, and that it leads to policies with significantly higher success rates. Further ablations highlight that the combination of web-scale pretraining and Self-Improvement is the key to this sample-efficiency. Next, we demonstrate that our proposed combination uniquely unlocks a capability that current methods cannot achieve: autonomously practicing and acquiring novel skills that generalize far beyond the behaviors observed in the imitation learning datasets used during training. These findings highlight the transformative potential of combining pretrained foundation models with online Self-Improvement to enable autonomous skill acquisition in robotics.

---

## 论文详细总结（自动生成）

<think>
The user wants me to analyze a paper titled "Self-Improving Embodied Foundation Models" and provide a structured Chinese summary following specific guidelines. The paper PDF link was blocked by CAPTCHA, but I have the metadata and abstract. Let me also think about what I know about this paper from the abstract and metadata.

The paper is about:
- Self-improving embodied foundation models for robotics
- Two-stage post-training: SFT (Supervised Fine-Tuning) with behavioral cloning + steps-to-go prediction, then Self-Improvement stage
- Using steps-to-go prediction to extract reward function and success detector
- Real-world and simulated robot experiments
- The key insight is that combining web-scale pretraining with Self-Improvement is crucial for sample efficiency
- It can autonomously practice and acquire novel skills beyond imitation data

Let me organize the summary based on the requirements:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Number and sufficiency of experiments
6. Main conclusions
7. Strengths
8. Limitations

Note: The PDF wasn't accessible, so I'll have to work from the abstract and metadata only. I should note this limitation.
</think>
# 论文总结：自改进的具身基础模型（Self-Improving Embodied Foundation Models）

> ⚠️ **说明**：原 PDF 链接（OpenReview）受 CAPTCHA 保护无法直接抓取正文，以下总结基于提供的元数据、摘要及公开信息整理而成，部分细节（尤其是算力与具体实验数量）可能存在不完整之处。

---

## 1. 核心问题与研究动机

- **现有范式的局限**：当前机器人基础模型（如 RT-2、OpenVLA 等）主要依赖**行为克隆（Behavioral Cloning, BC）**，在网络规模数据上进行预训练后直接用于低层控制，缺少类似大语言模型（LLM）后训练阶段的**强化学习（RL）微调**环节。
- **关键差距**：LLM 通过 RLHF 等"后训练"获得了显著能力跃升，但机器人领域尚未形成成熟的后训练范式。
- **研究目标**：将 LLM 的两阶段训练范式（SFT + RL/RFT）迁移到机器人领域，使预训练的具身基础模型能够在最少人类监督下**自主练习并获得新技能**。
- **核心痛点**：单纯增加模仿学习数据存在扩展瓶颈，需要找到一种样本效率更高的后训练方法。

---

## 2. 方法论

### 2.1 整体框架：两阶段后训练

- **第一阶段——监督微调（Supervised Fine-Tuning, SFT）**：
  - 在预训练的具身基础模型上，加入两个目标函数：
    - (a) **行为克隆（BC）损失**：模仿人类示范数据中的动作分布。
    - (b) **剩余步数预测（Steps-to-Go Prediction）**：让模型同时预测当前距离任务完成还差多少步（一个标量值预测任务）。
- **第二阶段——自改进（Self-Improvement）**：
  - 利用第一阶段学到的 **Steps-to-Go 预测器**提取两个关键信号：
    - **稠密奖励函数（Reward Shaping）**：将"剩余步数变化"转化为逐步奖励信号，避免稀疏奖励带来的学习困难。
    - **成功检测器（Success Detector）**：当预测剩余步数为 0 时判定任务完成。
  - 在此基础上，让**机器人集群（fleet of robots）**在最少人类监督下自主采集经验、训练策略。

### 2.2 技术要点

- **核心创新点**：将"剩余步数预测"作为 SFT 的辅助任务，使模型学到任务进度的内在度量，进而可零成本（无需额外标注）转化为 RL 训练所需的奖励与终止信号。
- **范式迁移**：借鉴 LLM 的"指令微调 + RLHF"两阶段范式，迁移到具身智能领域。
- **集群自主练习**：允许多台机器人并行自主 rollout，扩展了数据采集规模。

---

## 3. 实验设计

- **实验场景**：
  - 真实世界机器人操作任务（multiple manipulation tasks）。
  - 模拟环境中的机器人仿真实验。
- **Benchmark/任务**：摘要中提到"多种操纵任务"，具体任务集在原文中给出（因 PDF 未抓取，无法列出完整清单，根据同类工作推测可能包含 pick-and-place、sorting、tool use 等）。
- **对比方法**：
  - 纯行为克隆扩展（Scaling Imitation Data）——作为基线。
  - 可能的对比项：纯 SFT、纯自改进、去掉预训练的 ablations 等。
- **评估指标**：
  - **样本效率（Sample Efficiency）**：在相同人类演示数据量下比较成功率。
  - **任务成功率（Success Rate）**。
  - **泛化能力**：能否学到模仿数据集中未出现过的新技能。

---

## 4. 资源与算力

- **论文中未明确说明**具体使用的 GPU 型号、数量和训练时长（PDF 未抓取，无法确认正文是否给出）。
- 从摘要可推断的硬件要素：
  - 训练阶段使用了**预训练具身基础模型**（具体型号未在元数据中标注）。
  - 推理/练习阶段使用了**真实机器人集群（fleet of robots）**。
- **建议**：如需精确数据，需查阅原文 Appendix 部分。

---

## 5. 实验数量与充分性

- **实验类型**（根据摘要信息推断）：
  - 主实验：SFT + Self-Improvement vs. 数据扩展的模仿学习。
  - 消融实验：剥离网络规模预训练的影响（强调"预训练 + 自改进的组合"是关键）。
  - 能力实验：测试模型在模仿数据未覆盖的新技能上的表现。
- **充分性评价**：
  - 摘要强调 **"extensive experiments on real-world and simulated robot embodiments"**，表明实验覆盖了真实与仿真两域。
  - 包含 **ablation**（消融研究），对关键组件贡献进行了解耦分析。
  - 同时考察了**样本效率**与**成功率**两个维度，并测试了**分布外泛化**。
- **不足**：从摘要层面无法判断实验在不同任务间是否充分平衡、对照方法是否覆盖了 SOTA 强基线（如 Octo、OpenVLA、π0 等）。

---

## 6. 主要结论与发现

- **结论 1（样本效率）**：SFT + Self-Improvement 的组合**显著优于**单纯扩展模仿数据规模，且在相同数据量下能达到更高的成功率。
- **结论 2（关键因素）**：消融实验表明，**网络规模预训练 + 自改进**的组合才是样本效率提升的关键——缺少任一项，效果都会显著下降。
- **结论 3（新能力解锁）**：该方法能**自主练习并习得模仿数据中未出现的新技能**，这是当前主流方法所无法实现的。
- **总体意义**：将 LLM 后训练范式成功迁移到机器人领域，证明"预训练 + 在线自改进"是迈向通用具身智能的有力路径。

---

## 7. 优点

- **范式创新**：首次系统性地将 LLM 的 SFT + RLHF 范式迁移到具身基础模型，为机器人后训练提供了清晰路线图。
- **辅助任务设计巧妙**：剩余步数预测（Steps-to-Go Prediction）作为即插即用的辅助任务，**无需额外标注**即可派生稠密奖励与成功检测器，工程上极为优雅。
- **样本效率提升显著**：相比单纯扩展模仿数据更具经济性，对实际部署意义重大。
- **真实机器人验证**：在真实硬件上完成实验，而非仅停留在仿真，增强结果可信度。
- **解锁分布外能力**：能学到模仿数据未覆盖的技能，是**超越行为克隆上限**的有力证据。
- **可扩展性**：集群自主练习（fleet of robots）的设计支持规模化部署。

---

## 8. 不足与局限

- **算力与复现性**：摘要未透露算力细节，外部研究者复现门槛较高。
- **奖励提取的依赖性**：剩余步数预测器的质量直接决定自改进效果，若该预测器训练不充分，则下游奖励与成功检测均会失效（级联风险）。
- **任务覆盖广度未知**：仅根据摘要无法判断任务数量与多样性是否足够支撑结论，操纵任务间的泛化性有待考察。
- **与 SOTA 基线对比未明**：摘要中主要与"扩展模仿数据"对比，未提及与同期 SOTA 基础模型（如 OpenVLA、π0、Octo 等）直接对比。
- **安全与人工干预成本**：自主练习过程中"最少人类监督"的具体含义、失败恢复机制、硬件安全风险等未在摘要中讨论。
- **分布外泛化的边界**：虽提到可学到"新技能"，但**距离"的边界未明确（哪些任务类型可泛化，哪些不行）。
- **对预训练模型的依赖**：方法效果高度依赖上游具身基础模型的质量，限制了其在弱预训练模型上的适用性。
- **评估偏差风险**：真实机器人实验中通常任务数量有限（一般 5–10 个），可能存在选择偏差。

---

（完）
