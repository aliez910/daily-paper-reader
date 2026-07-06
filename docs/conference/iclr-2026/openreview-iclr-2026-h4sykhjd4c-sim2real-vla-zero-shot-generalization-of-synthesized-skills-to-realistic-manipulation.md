---
title: "Sim2Real VLA: Zero-Shot Generalization of Synthesized Skills to Realistic Manipulation"
title_zh: Sim2Real VLA：合成技能到真实操作的零样本泛化
authors: "Runyi Zhao, Sheng Xu, Ruixing Jin, Yueci Deng, Yunxin Tai, Kui Jia, Guiliang Liu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=H4SyKHjd4c"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操作的通用视觉-语言-动作模型，实现仿真到现实迁移
tldr: 针对视觉-语言-动作（VLA）模型在仿真训练后难以泛化到真实操作这一关键挑战，本文提出 Sim2Real-VLA，一种完全基于合成数据训练却能零样本迁移到真实世界操作的通用机器人控制模型。模型采用双系统架构：高层规划器推断以物体为中心的可供性链，底层控制器将动作落实到视觉观测。该工作显著缩小了 VLA 模型的仿真到现实差距，为通用机器人策略的发展提供了重要支撑。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: VLA 模型在仿真中训练后难以稳定泛化到真实环境，Sim2Real 差距严重制约其应用。
method: 提出 Sim2Real-VLA 双系统架构，结合以物体为中心的可供性链规划与视觉驱动控制。
result: 完全在合成数据上训练即可零样本迁移到真实世界操作任务。
conclusion: 为通用 VLA 模型跨越仿真到现实鸿沟提供了有效方案。
---

## Abstract
Vision-Language-Action (VLA) models represent a critical milestone toward embodied intelligence in robotic manipulation. To support their training, recent research has developed high-performance simulation engines for data synthesis. However, their effectiveness is still significantly limited by the simulation-to-reality (Sim2Real) gap, as policies trained on synthetic data often fail to generalize reliably to the real world. To address this challenge, we present Sim2Real-VLA, a generalist robot control model trained exclusively on synthetic data, yet capable of transferring seamlessly to real-world manipulation tasks. Sim2Real-VLA features a dual-system architecture: a high-level planner that infers object-centered chains-of-affordances, and a low-level actor that executes and validates these plans in real time via a tokenized action space. This design filters out manipulation-irrelevant features and prioritizes motion-critical dynamics, thereby enhancing Sim2Real domain transfer. Besides, a notable advantage of Sim2Real-VLA lies in its tight integration with automated data generation for manipulation skills, eliminating the need for manual fine-tuning and enabling scalable, hands-free training. Empirical evaluations across bimanual, dexterous, and long-horizon tasks show that Sim2Real-VLA consistently outperforms previous VLA baselines under diverse real-world environments and domain shifts.

---

## 论文详细总结（自动生成）

<think>
The user wants me to summarize a paper based on the provided metadata. Let me analyze what's available:

1. The PDF content is just a CAPTCHA verification page, not the actual paper content.
2. However, there's detailed metadata in Chinese about the paper "Sim2Real VLA: Zero-Shot Generalization of Synthesized Skills to Realistic Manipulation"

I need to be careful here - the actual paper PDF was not accessible (CAPTCHA blocked), but the metadata provides a good summary of the paper. I should base my summary on the metadata provided, while being clear about the limitations of my analysis.

Let me structure the response according to the 8 points requested:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources/compute
5. Number of experiments and adequacy
6. Main conclusions
7. Strengths
8. Limitations

I need to be honest that the actual paper content wasn't accessible, but I can still work from the metadata which provides substantial information.

Let me draft the response in Chinese as requested.
</think>
# Sim2Real-VLA 论文总结

> **说明**：原始 PDF 页面因 CAPTCHA 验证未能抓取到论文正文，以下总结主要基于提供的论文元数据（标题、摘要、TLDR 等）进行整理，部分细节（如具体超参数、实验数量、算力等）可能与论文实际内容存在偏差，建议以原文为准。

---

## 1. 核心问题与整体含义

- **研究领域**：机器人操作（robotic manipulation）中的视觉-语言-动作（Vision-Language-Action, VLA）模型。
- **核心问题**：现有 VLA 模型在仿真环境中利用合成数据训练后，难以可靠地泛化到真实世界（Sim2Real gap），严重制约通用机器人策略的落地。
- **研究目标**：构建一个**完全在合成数据上训练、却能零样本迁移到真实环境**的通用机器人控制模型，缩小乃至跨越 Sim2Real 鸿沟。

---

## 2. 方法论

- **核心思想**：双系统（dual-system）架构，模仿"高层推理 + 低层控制"的认知分工。
- **高层规划器（Planner）**：
  - 推理"以物体为中心的可供性链"（object-centered chains-of-affordances）。
  - 关注"做什么"以及操作对象之间的语义和物理可供性。
- **底层执行器（Actor）**：
  - 在实时视觉观测下，将高层规划落实为具体动作。
  - 采用**离散化（tokenized）的动作空间**，便于与语言/视觉 token 联合建模。
- **关键设计理念**：
  - **过滤与操作无关的视觉特征**，优先保留运动关键的动力学信息；
  - 与**自动化数据生成流程紧耦合**，无需人工微调即可完成规模化训练。
- **算法流程（文字描述）**：
  1. 仿真器自动生成多样化操作任务的数据；
  2. 高层模型基于视觉-语言输入输出可供性链；
  3. 底层模型结合当前观测将可供性链转化为动作 token；
  4. 推理时直接部署到真实机器人，零样本执行。

---

## 3. 实验设计

- **任务类型**（基于元数据推断）：
  - 双手操作（bimanual）
  - 灵巧操作（dexterous）
  - 长视野任务（long-horizon）
- **Benchmark**：未在元数据中明确指出，文中以"diverse real-world environments and domain shifts"描述评估条件。
- **对比方法**：文中与"previous VLA baselines"进行比较，但具体方法列表未在可获取内容中列出，可能包括 RT-2、OpenVLA、Octo 等主流 VLA 基线。
- **评估维度**：真实环境、多样化领域偏移下的零样本泛化能力。

---

## 4. 资源与算力

- 元数据中**未提供** GPU 型号、数量、训练时长、参数量等具体算力信息。
- 仅可推断：训练完全在合成数据上进行，因此理论上不涉及大规模真实机器人数据采集成本。
- 建议查阅论文正文与附录以获取完整算力与训练开销信息。

---

## 5. 实验数量与充分性

- **元数据层面**的信息：覆盖双手、灵巧、长视野三类典型操作任务。
- **充分性判断**：
  - 优点：任务种类涵盖了机器人操作中的多种难点（双手协调、灵巧性、长视野规划）；
  - 局限：缺乏具体消融实验数量、统计显著性、跨平台/跨机器人迁移等细节，仅凭现有信息难以全面评判实验充分性。
- **公平性**：
  - 由于强调"零样本"且无人工微调，与依赖真实数据微调的基线方法相比，实验设计本身对所提方法略有"严格"约束；
  - 但具体的随机种子、试验次数、成功率统计标准等需以正文为准。

---

## 6. 主要结论与发现

- 完全在合成数据上训练的 Sim2Real-VLA 能够**零样本迁移**到真实世界操作任务。
- 双系统架构 + 物体级可供性链 + token 化动作空间是缩小 Sim2Real 差距的有效设计。
- 与自动化数据生成深度集成，使得训练过程**无需人工微调、可扩展**。
- 在双手、灵巧、长视野任务上**一致优于**已有 VLA 基线，表现出较强的领域鲁棒性。

---

## 7. 优点

- **架构创新**：双系统分工（语义规划 + 实时控制）符合认知分层思想，解释性强。
- **可供性链建模**：以物体为中心的中间表征提升了跨场景泛化能力。
- **动作离散化**：token 化动作空间便于与 VLM 联合训练与推理。
- **数据管线自动化**：摆脱对人工遥操数据的依赖，具规模化潜力。
- **任务覆盖广**：双手、灵巧、长视野三种典型设置具有代表性。
- **零样本承诺**：无需真实数据微调即可部署，应用门槛低。

---

## 8. 不足与局限

- **信息不完整风险**：因 PDF 未能抓取正文，技术细节、实验规模、消融设置等均需谨慎对待。
- **仿真器偏差**：方法依赖仿真器生成质量，若仿真器建模不准（如接触动力学、材质光学），仍会引入新的 Sim2Real 鸿沟。
- **领域偏移覆盖度未知**：摘要提及"diverse domain shifts"，但具体涵盖哪些偏移（光照、背景、物体外观、相机视角等）未在元数据中说明。
- **缺乏真实数据微调对比**：在真实世界任务中，若允许少量真实数据微调，对比是否仍保持优势尚不明确。
- **安全性与可重复性**：长视野、灵巧操作的失败率与安全指标（如碰撞率）未提及。
- **可扩展性边界**：可供性链的复杂度随任务增长，是否仍可高效推理，缺乏理论或实验分析。
- **社会与伦理风险**：大规模自动化合成数据可能放大仿真器中的偏差，需关注其向真实世界的传导。

（完）
