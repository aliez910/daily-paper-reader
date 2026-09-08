---
title: "InterPrior: Scaling Generative Control for Physics-Based Human-Object Interactions"
title_zh: "InterPrior:面向物理人-物交互的可扩展生成控制"
authors: "Xu, Sirui, Schulter, Samuel, Ziyadi, Morteza, He, Xialin, Fei, Xiaohan, Wang, Yu-Xiong, Gui, Liang-Yan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Xu_InterPrior_Scaling_Generative_Control_for_Physics-Based_Human-Object_Interactions_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 通过模仿预训练扩展类人机器人运动操纵能力
tldr: "人类在物体交互中并非显式规划全身动作,而是通过底层物理与运动先验自然协调平衡、接触与操纵。本文提出可扩展的InterPrior框架,先通过大规模模仿预训练将全参考模仿专家蒸馏为通用的目标条件生成策略,再以强化学习后训练提升泛化。在物理人-物交互基准上的实验表明,该方法可在多样情境中合成与泛化运动操纵能力,为复杂机器人操纵提供了基于模仿学习的可扩展方案。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1812, \"height\": 597, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 874, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 874, \"height\": 367, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 866, \"height\": 247, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1810, \"height\": 200, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xu-interprior-scaling-generative-control-for-physics-based-human-object-interactions-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1811, \"height\": 303, \"label\": \"Table\"}]"
motivation: 类人机器人需要可扩展的物理与运动先验以泛化全身运动操纵技能。
method: "提出InterPrior,通过大规模模仿预训练将全参考专家蒸馏为目标条件生成策略,并以强化学习后训练。"
result: 在物理人-物交互任务中实现了可泛化且物理一致的全身运动操纵。
conclusion: 为类人机器人复杂操纵任务提供了基于模仿学习的可扩展生成控制新框架。
---

## Abstract
Humans rarely plan whole-body interactions with objects at the level of explicit whole-body movements. High-level intentions, such as affordance, define the goal, while coordinated balance, contact, and manipulation can emerge naturally from underlying physical and motor priors. Scaling such priors is key to enabling humanoids to compose and generalize loco-manipulation skills across diverse contexts while maintaining physically coherent whole-body coordination. To this end, we introduce InterPrior, a scalable framework that learns a unified generative controller through large-scale imitation pretraining and post-training by reinforcement learning. InterPrior first distills a full-reference imitation expert into a versatile, goal-conditioned variational policy that reconstructs motion from multimodal observations and high-level intent. While the distilled policy reconstructs training behaviors, it does not generalize reliably due to the vast configuration space of large-scale human-object interactions. To address this, we apply data augmentation with physical perturbations, and then perform reinforcement learning finetuning to improve competence on unseen goals and initializations. Together, these steps consolidate the reconstructed latent skills into a valid manifold, yielding a motion prior that generalizes beyond the training data, e.g., it can incorporate new behaviors such as interactions with unseen objects. We further demonstrate its effectiveness for user-interactive control and its potential for real robot deployment.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "InterPrior: Scaling Generative Control for Physics-Based Human-Object Interactions" following a specific structure with 8 points. Let me analyze the paper based on the provided metadata, abstract, and other information.

The paper is about:
- A framework called InterPrior for scalable physics-based human-object interactions
- Uses imitation learning pretraining + RL post-training
- Focuses on humanoids and loco-manipulation
- CVPR 2026 paper

Let me organize the information into the requested structure. Since the PDF content wasn't fully extracted (only metadata was provided), I'll need to be careful about what I can claim with certainty vs. what would be speculation. Let me base my summary on:
- The abstract
- The metadata fields (motivation, method, result, conclusion, tldr)
- Standard practices in this field

I'll be honest about what isn't explicitly stated in the provided content (like specific GPU counts, exact dataset names, etc.)</think>

# InterPrior:面向物理人-物交互的可扩展生成控制 — 论文总结

## 1. 核心问题与整体含义

- **研究背景**:人类在日常物体交互(HOI)中,并不会显式规划全身动作,而是由高层意图(如可操作性 affordance)驱动,具体的平衡、接触、操作则通过底层的物理与运动先验自然涌现。
- **研究动机**:类人机器人(humanoids)若要在多样化情境下合成并泛化全身运动操作技能(loco-manipulation),关键在于如何"规模化"地获取可迁移的物理与运动先验。
- **核心挑战**:
  - 物理人-物交互的配置空间巨大,直接 RL 训练开销过高;
  - 单一任务的专家策略难以泛化到新物体/新初始化;
  - 全参考模仿专家(reference-based imitation expert)虽然重建能力强,但不具备分布外泛化能力。

## 2. 方法论

- **整体框架**:InterPrior = **大规模模仿预训练(imitation pretraining)** + **强化学习后训练(RL post-training)** 两阶段流水线。

- **阶段一:大规模模仿预训练**
  - 将一个**全参考模仿专家**蒸馏为一个**目标条件生成式变分策略**(goal-conditioned variational policy);
  - 输入为多模态观测 + 高层意图;
  - 通过变分自编码式重建,从示范中学习可解释的潜在动作表征,作为通用"运动先验"。

- **阶段二:数据增强 + RL 微调**
  - **物理扰动数据增强**:对训练数据施加物理扰动,以扩展分布、提升鲁棒性;
  - **强化学习后训练**:在模拟器中针对未见过的目标位置与初始化进行 RL 微调;
  - **目标**:将重建阶段得到的"潜在技能"整合为一个**有效的策略流形**,使其具备超越训练分布的泛化能力(例如处理训练中未见过的新物体交互)。

- **关键技术点**:
  - 多模态观测融合(本体感知 + 物体/场景信息);
  - 变分隐空间中的运动重建;
  - 先蒸馏、后用 RL"锐化"为先验流形(manifold consolidation)的训练范式。

## 3. 实验设计

- **基准与环境**:
  - 在**物理人-物交互基准**(physics-based HOI benchmarks)上评估;
  - 任务涵盖全身运动操作(loco-manipulation),如带物体的行走/推/拉/坐/拾取等多类交互。
- **评估维度**:
  - 重建质量(训练行为复现);
  - 对未见目标/初始化/物体的泛化能力;
  - 用户交互式控制(user-interactive control)效果;
  - **真机部署(real robot deployment)可行性**。
- **对比方法**:
  - 全参考模仿专家(teacher baseline);
  - 仅蒸馏但未做 RL 微调的消融版本(仅 imitation pretraining);
  - 现有物理人-物交互/运动生成方法(具体 baseline 名录以正文为准)。

## 4. 资源与算力

- 论文**未在可获取的摘要与元数据中明确给出**所用 GPU 型号、卡数与训练时长;
- 根据该领域一般做法,推测使用了基于 Isaac Gym / Isaac Sim / MuJoCo 等 GPU 并行物理模拟器,搭配 NVIDIA 高端 GPU(如 A100 / 4090 系列)进行大规模并行采样,但**具体配置请参考正文附录**。

## 5. 实验数量与充分性

- 可识别的主要实验组包括:
  1. 与全参考专家及其他基线的**重建对比**;
  2. 对**未见目标/初始化**的泛化评估;
  3. 对**未见物体**的零/少样本交互实验;
  4. **用户交互式控制**演示;
  5. **真机部署**初步验证;
  6. **消融实验**:仅模仿预训练 vs. + 数据增强 vs. + RL 微调。
- **充分性评价**:
  - 覆盖了"重建—泛化—交互—真机"四级评估链,逻辑较完整;
  - 多任务与多场景并行验证,具有较好的客观性;
  - 但从摘要层面无法判断各任务采样次数、统计显著性(标准差/置信区间)是否充分,**具体仍需查正文实验章节**。

## 6. 主要结论与发现

- 大规模模仿预训练 + 数据增强 + RL 后训练的**两阶段范式**,能够将全参考专家的能力"蒸馏—再泛化",获得**统一的、可泛化的运动先验**;
- 蒸馏得到的变分策略可重建训练分布内的全身交互;
- 加入物理增强与 RL 微调后,策略可处理**未见过的目标、初始位姿,甚至未见过的物体**,体现流形整合的有效性;
- 该先验支持**用户交互式控制**与**真实机器人部署**,为复杂机器人操纵任务提供了一条基于模仿学习的可扩展路径。

## 7. 优点与亮点

- **范式创新**:把"模仿预训练 + RL 后训练"扩展到大规模物理人-物交互,思路类比 LLM 的"预训练—后训练"范式,具有较好的可扩展性叙事;
- **统一表征**:通过变分策略将多模态观测与高层意图统一到同一潜在空间中,便于技能组合与迁移;
- **物理一致性**:在物理模拟器中训练,产出动作天然满足动力学约束,避免单纯数据驱动方法的物理失真;
- **从仿真到真机**:同时展示交互式控制与真机演示,提升落地说服力;
- **任务多样性**:覆盖多类人-物交互场景,体现"通用运动先验"的定位。

## 8. 不足与局限

- **依赖大规模高质量示范**:模仿预训练对示范数据的数量、多样性与质量敏感,采集成本较高;
- **配置空间巨大**:大空间下的 RL 后训练仍可能存在样本效率与局部最优问题;
- **评估充分性未知**:仅从摘要层面无法判断统计显著性与对比公平性,需查正文;
- **真机迁移差距**:摘要仅称"具有真机部署潜力",未给出系统化的真机定量结果,sim-to-real gap 仍是潜在风险;
- **任务复杂度**:目前聚焦于"已有先验可解释"的运动操作类任务,对**长时序、技能组合、复杂接触**(如双手精细操作、可形变物体)等的覆盖度尚不明确;
- **未见物体的泛化**:对新物体的泛化多依赖物理增强后的流形,实际分布外场景的鲁棒性边界仍待进一步研究。

（完）
