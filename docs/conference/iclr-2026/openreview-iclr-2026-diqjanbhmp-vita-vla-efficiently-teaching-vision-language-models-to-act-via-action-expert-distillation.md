---
title: "VITA-VLA: Efficiently Teaching Vision-Language Models to Act via Action Expert Distillation"
title_zh: VITA-VLA：通过动作专家蒸馏高效训练视觉-语言-动作模型
authors: "Shaoqi Dong, Chaoyou Fu, Haihan Gao, YiFan Zhang, Chi Yan, Chu Wu, Xiaoyu Liu, Yunhang Shen, Jing Huo, Deqiang Jiang, Haoyu Cao, Yang Gao, Xing Sun, Ran He, Caifeng Shan"
date: 2025-09-05
pdf: "https://openreview.net/pdf?id=dIqJaNbHmP"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过动作专家蒸馏将VLM转化为VLA模型用于机器人操控
tldr: VLA模型通过整合动作模块有效提升机器人操控的泛化与鲁棒性，但端到端训练需大规模数据与高昂算力。本文提出VITA-VLA，通过蒸馏预训练小型动作模型的知识，高效地为VLM赋予动作执行能力。架构仅在原VLM上新增一个动作token与状态编码器，在显著降低训练成本的同时保留VLA的泛化优势。该工作为大规模VLA模型的高效训练提供了一条实用路径。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有VLA模型端到端训练成本高，依赖大规模数据与重计算资源。
method: 提出VITA-VLA蒸馏框架，将预训练小型动作模型的知识迁移至VLM，仅新增动作token与状态编码器。
result: 显著降低VLA训练成本，同时保持预训练VLM的泛化与鲁棒性优势。
conclusion: VITA-VLA为大规模VLA模型的高效训练提供了一种轻量化蒸馏方案。
---

## Abstract
Vision-Language Action (VLA) models significantly advance robotic manipulation by leveraging the strong perception capabilities of pretrained vision-language models (VLMs). By integrating action modules into these pretrained models, VLA methods exhibit improved generalization and robustness. However, training them end-to-end is costly, as modeling action distributions typically requires massive datasets and heavy computation. In this work, we propose a simple yet effective distillation-based framework that equips VLMs with action-execution capability by transferring knowledge from pretrained small action models. Our architecture retains the original VLM structure, adding only an action token and a state encoder to incorporate physical inputs, as illustrated in Figure 1. To distill action knowledge, we adopt a two-stage training strategy. First, we perform lightweight alignment by mapping VLM hidden states into the action space of the small action model, enabling effective reuse of its pretrained action decoder and avoiding expensive end-to-end pretraining. This also facilitates better transfer of action modeling capabilities to the VLM. Second, we selectively fine-tune the language model, state encoder, and action modules, enabling the system to integrate multimodal inputs with precise action generation. Specifically, the action token provides the VLM with a direct handle for predicting future actions, while the state encoder allows the model to incorporate robot dynamics not captured by vision alone (see Figure 2). This design yields substantial efficiency gains over training large VLA models from scratch. Compared with previous state-of-the-art methods, our method achieves 97.3\% average success rate on LIBERO (11.8\% improvement), 93.5\% on LIBERO-LONG (24.5\% improvement), 92.5\% first task success rate on CALVIN ABC-D (4.1\% improvement). In real-world experiments across five manipulation tasks, our method consistently outperforms the teacher model Seer, achieving 82.0\% average success rate (17\% improvement). These results demonstrate that action distillation effectively enables VLMs to generate precise, executable actions while substantially reducing training costs.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "VITA-VLA: Efficiently Teaching Vision-Language Models to Act via Action Expert Distillation" based on the provided metadata and abstract. Let me organize this into the requested structure.

The paper is about VLA (Vision-Language-Action) models for robotic manipulation. The key contributions are:
1. A distillation framework that transfers knowledge from small action models to VLMs
2. Minimal architecture changes (action token + state encoder)
3. Two-stage training strategy
4. Significant efficiency improvements
5. State-of-the-art results on LIBERO, LIBERO-LONG, CALVIN ABC-D, and real-world tasks

Let me structure the summary according to the requested points.
</think>
# VITA-VLA 论文总结

## 1. 核心问题与研究动机

- **研究背景**：视觉-语言-动作（Vision-Language Action, VLA）模型通过在预训练视觉-语言模型（VLM）中整合动作模块，显著提升了机器人操控的泛化能力与鲁棒性。
- **现有瓶颈**：端到端训练 VLA 模型成本极高，需要大规模机器人数据集和大量算力，限制了其广泛应用。
- **核心问题**：如何在保留 VLM 强大的感知与泛化能力的同时，以低成本方式赋予其精确动作执行能力。

## 2. 方法论

### 核心思想
提出 **VITA-VLA**——一种基于知识蒸馏的轻量化框架，通过将预训练的小型动作模型（教师模型）的知识迁移到 VLM（学生模型），实现高效训练。

### 架构设计（最小侵入式）
- 在原始 VLM 基础上**仅新增两个组件**：
  1. **Action Token（动作 token）**：为 VLM 提供直接预测未来动作的"把手"；
  2. **State Encoder（状态编码器）**：将机器人本体感知状态（关节角、速度等动力学信息）注入模型，弥补纯视觉无法捕捉的物理信息。
- 完整保留 VLM 原有的视觉-语言主干结构，避免破坏其预训练知识。

### 两阶段训练策略
- **第一阶段——轻量对齐（Alignment）**：
  - 将 VLM 的隐藏状态映射到小型动作模型的动作空间，复用其预训练好的动作解码器；
  - 避免从头进行昂贵的端到端预训练；
  - 有效将动作建模能力迁移至 VLM。
- **第二阶段——选择性微调（Fine-tuning）**：
  - 选择性微调语言模型、状态编码器与动作模块；
  - 实现多模态输入融合与精确动作生成的协同。

### 关键技术亮点
- **解耦式蒸馏**：将"动作分布建模"从 VLM 主干中剥离，由小型专家模型承担，VLM 仅需学习"如何调用"该能力。
- **多模态融合**：视觉 + 语言 + 状态（本体感知）三者协同，弥补视觉盲区。

## 3. 实验设计

### 数据集 / 评测场景
| 评测基准 | 性质 |
|---------|------|
| **LIBERO** | 仿真机器人操控基准，多任务场景 |
| **LIBERO-LONG** | LIBERO 的长时序/复杂任务扩展 |
| **CALVIN ABC→D** | 仿真长视野操控基准（零样本泛化） |
| **真实机器人实验** | 5 项操控任务（与教师模型 Seer 对比） |

### 对比方法
- 多种现有 SOTA VLA 方法（论文中以"previous state-of-the-art methods"统称）。
- 真实实验中特别与**教师模型 Seer** 进行对比（蒸馏后的学生是否能超越教师）。

### 主要结果
- **LIBERO**：平均成功率 **97.3%**（提升 11.8%）；
- **LIBERO-LONG**：平均成功率 **93.5%**（提升 24.5%）；
- **CALVIN ABC→D**：首任务成功率 **92.5%**（提升 4.1%）；
- **真实机器人 5 项任务**：平均成功率 **82.0%**（较教师 Seer 提升 17%），验证了"学生超越教师"的蒸馏效果。

## 4. 资源与算力

- **明确披露的信息**：摘要中强调"substantial efficiency gains over training large VLA models from scratch"，但**未在所提供内容中给出具体的 GPU 型号、数量、训练时长、参数量等细节**。
- 需查阅论文正文/附录以获取完整的算力配置（建议读者进一步核实）。

## 5. 实验数量与充分性

- **仿真实验**：覆盖 LIBERO、LIBERO-LONG、CALVIN 三大主流 benchmark，具备较强可比性。
- **真实实验**：5 项操控任务，跨仿真与真实两个维度。
- **可观察的对比维度**：
  - 与多个 SOTA 横向对比（LIBERO / LIBERO-LONG / CALVIN）；
  - 蒸馏学生 vs. 教师模型对比（真实环境）；
  - 公开了多个量化提升指标。
- **潜在不充分之处**（从摘要层面判断）：
  - 摘要未明确说明消融实验（ablation）的数量与结论；
  - 真实实验仅 5 项任务，任务多样性有限；
  - 未提及是否在不同机器人本体（embodiment）上验证泛化性。

## 6. 主要结论与发现

- **结论 1**：通过动作专家蒸馏，VLM 能够以极低的训练成本获得精确动作执行能力。
- **结论 2**：仅引入 action token + state encoder 的最小架构修改，即可高效融合多模态信息。
- **结论 3**：在 LIBERO / LIBERO-LONG / CALVIN 三大基准以及真实机器人任务上均取得 SOTA 或显著提升。
- **结论 4**：蒸馏后的学生模型在真实任务中**显著超越教师模型**（Seer），证明该框架的实用性与可扩展性。
- **结论 5**：为大规模 VLA 模型的高效训练提供了一条实用且可推广的技术路径。

## 7. 优点

- **架构极简**：相比传统端到端 VLA 训练，仅新增两个模块，保留了 VLM 全部预训练知识。
- **训练高效**：两阶段策略（对齐 + 选择性微调）避免了大规模端到端预训练。
- **效果显著**：在多个仿真 benchmark 与真实任务上均取得大幅提升，尤其在 LIBERO-LONG 上提升 24.5%。
- **学生超越教师**：在真实实验中蒸馏模型优于原教师 Seer，体现蒸馏策略的优越性。
- **多模态融合设计合理**：通过 state encoder 显式建模本体感知，弥补纯视觉盲区。
- **实用价值高**：为业界提供了一条低成本部署 VLA 模型的可行方案。

## 8. 不足与局限

- **算力信息不透明**：摘要中未提供 GPU 型号、训练时长、参数量等关键信息，难以客观评估"高效"的具体程度。
- **消融实验不充分**：摘要未明确说明针对 action token、state encoder、两阶段策略等的消融验证。
- **真实实验规模有限**：仅 5 项真实任务，任务种类与场景复杂度有待扩展。
- **泛化性验证不足**：未提及在不同机器人本体、不同视觉配置下的跨平台泛化能力。
- **对教师模型依赖**：蒸馏效果受限于教师模型（Seer）的质量上限，若教师存在偏差，学生可能继承该偏差。
- **任务分布偏差风险**：LIBERO/CALVIN 等仿真 benchmark 与真实任务之间存在 sim-to-real gap，真实实验仅 5 项可能不足以全面反映该差距。
- **应用限制**：当前方法针对操控任务（manipulation），尚未验证在 locomotion、navigation 等其他机器人任务上的适用性。

（完）
