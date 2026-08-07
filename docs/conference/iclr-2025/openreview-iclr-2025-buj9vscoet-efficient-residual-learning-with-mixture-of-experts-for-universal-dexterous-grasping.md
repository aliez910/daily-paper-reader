---
title: Efficient Residual Learning with Mixture-of-Experts for Universal Dexterous Grasping
title_zh: 基于混合专家残差学习的通用灵巧抓取方法
authors: "Ziye Huang, Haoqi Yuan, Yuhui Fu, Zongqing Lu"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=BUj9VSCoET"
tags: ["query:rob-il"]
score: 4.0
evidence: 通过残差策略学习实现跨多种物体的通用灵巧抓取
tldr: 本文针对通用灵巧抓取中多任务课程设计复杂、对未见物体泛化能力有限的问题，提出了ResDex框架。该方法将残差策略学习与混合专家机制相结合，先在单个物体上高效习得几何无关的基策略，再通过MoE融合泛化到多种未见物体。实验表明该方法显著简化了多任务学习流程并提升了跨物体泛化能力。这项工作为大规模灵巧操作策略学习提供了一条可扩展路径。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 通用灵巧抓取面临多任务课程设计复杂与未见物体泛化受限的难题。
method: 结合残差策略学习与混合专家机制，融合多个几何无关的基策略。
result: 在多物体抓取任务上显著简化训练流程并提升泛化能力。
conclusion: 残差学习加MoE为可扩展的通用灵巧抓取提供了有效方案。
---

## Abstract
Universal dexterous grasping across diverse objects presents a fundamental yet formidable challenge in robot learning. Existing approaches using reinforcement learning (RL) to develop policies on extensive object datasets face critical limitations, including complex curriculum design for multi-task learning and limited generalization to unseen objects. 
To overcome these challenges, we introduce ResDex, a novel approach that integrates residual policy learning with a mixture-of-experts (MoE) framework. ResDex is distinguished by its use of geometry-agnostic base policies that are efficiently acquired on individual objects and capable of generalizing across a wide range of unseen objects. Our MoE framework incorporates several base policies to facilitate diverse grasping styles suitable for various objects. By learning residual actions alongside weights that combine these base policies, ResDex enables efficient multi-task RL for universal dexterous grasping.
ResDex achieves state-of-the-art performance on the DexGraspNet dataset comprising 3,200 objects with an 88.8% success rate. It exhibits no generalization gap with unseen objects and demonstrates superior training efficiency, mastering all tasks within only 12 hours on a single GPU. For further details and videos, visit our project page.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper based on the provided content. The paper is about "Efficient Residual Learning with Mixture-of-Experts for Universal Dexterous Grasping" (ResDex). Let me organize the information according to the requested points.

From the metadata and abstract, I can extract:
- Title: Efficient Residual Learning with Mixture-of-Experts for Universal Dexterous Grasping
- Authors: Ziye Huang, Haoqi Yuan, Yuhui Fu, Zongqing Lu
- Date: 2025-01-22
- Source: ICLR-2025-Accepted

The paper introduces ResDex, which combines residual policy learning with mixture-of-experts (MoE) for universal dexterous grasping.

Key points from abstract:
- Problem: Universal dexterous grasping across diverse objects is challenging
- Existing approaches using RL have limitations: complex curriculum design for multi-task learning, limited generalization to unseen objects
- Solution: ResDex integrates residual policy learning with MoE
- Uses geometry-agnostic base policies acquired on individual objects, generalizing to unseen objects
- MoE framework incorporates several base policies for diverse grasping styles
- Learns residual actions alongside weights that combine base policies
- Achieves SOTA on DexGraspNet dataset (3,200 objects) with 88.8% success rate
- No generalization gap with unseen objects
- Training efficiency: 12 hours on a single GPU

Let me write the summary in Chinese with the required structure.</think>

# 论文总结：基于混合专家残差学习的通用灵巧抓取方法（ResDex）

## 1. 核心问题与整体含义

- **研究背景**：通用灵巧抓取（universal dexterous grasping）是机器人学习中的基础且极具挑战性的问题，需要在多种形态各异的物体上实现稳定抓取。
- **现有方法的局限**：
  - 基于强化学习（RL）在大量物体数据集上训练策略时，存在**多任务课程设计复杂**的问题；
  - 对**未见物体的泛化能力有限**。
- **本文目标**：提出一种能高效扩展到大量物体、且对未见物体具有强泛化能力的通用灵巧抓取方法。

## 2. 方法论

- **核心思想**：将**残差策略学习（Residual Policy Learning）**与**混合专家机制（Mixture-of-Experts, MoE）**相结合，提出 ResDex 框架。
- **关键技术细节**：
  - **几何无关的基策略（Geometry-agnostic base policies）**：在单个物体上高效习得，能够跨多种未见物体进行泛化。
  - **MoE 融合**：多个基策略对应不同的抓取风格（grasping styles），通过混合专家框架进行加权融合，以适配不同物体。
  - **残差动作学习**：在基策略之上学习残差动作（residual actions），并同时学习组合各基策略的权重（mixing weights）。
  - **高效多任务强化学习**：通过上述机制实现对通用灵巧抓取的高效多任务 RL 训练。
- **算法流程概述**：
  1. 在少量代表性物体上分别训练多个基策略；
  2. 冻结基策略并训练 MoE 路由器，学习组合权重；
  3. 同时学习残差动作以修正基策略输出；
  4. 端到端优化以适应大规模多样化物体集合。

## 3. 实验设计

- **数据集**：DexGraspNet 数据集，包含 **3,200 个物体**。
- **Benchmark**：DexGraspNet 上的通用灵巧抓取成功率。
- **对比方法**：论文称达到了 **state-of-the-art (SOTA)** 性能，但具体对比的方法基线在所提供文本中未详尽列出（需要查阅正文）。
- **评估维度**：
  - 在训练物体上的抓取成功率；
  - 在未见物体上的泛化表现（"no generalization gap"）。

## 4. 资源与算力

- **训练效率**：在**单块 GPU 上仅用 12 小时**即可掌握全部任务。
- **GPU 型号**：所提供文本中**未明确说明 GPU 型号与具体硬件配置**。
- **训练时长对比**：摘要中提及该方法相比其他方法具有显著的训练效率优势（"superior training efficiency"），但具体对比数据未在所提供文本中给出。

## 5. 实验数量与充分性

- **实验规模**：在 3,200 个物体的大规模数据集上进行评估，具有较强的统计意义。
- **泛化性验证**：不仅评估训练集内物体，还专门测试了**未见物体的泛化能力**，这是该类研究的关键。
- **充分性评估**：
  - 优点：数据集规模大、涵盖训练与未见物体验证，体现出较强的实验充分性。
  - 不足：所提供的元数据中**未详述消融实验（ablation study）数量与内容**，以及与其他主流方法（如 DexGraspNet 原方法、UniDexGrasp 等）的具体定量对比，因此对实验充分性的全面评价需要查阅论文正文。

## 6. 主要结论与发现

- **性能结论**：ResDex 在 DexGraspNet 数据集上以 **88.8% 的成功率**达到 SOTA。
- **泛化结论**：在未见物体上**无明显泛化差距（no generalization gap）**，证明残差学习 + MoE 能有效促进跨物体迁移。
- **效率结论**：单 GPU、12 小时即可完成全部任务训练，显著简化了多任务 RL 的训练流程。
- **方法论结论**：残差策略学习与 MoE 的结合为大规模灵巧操作策略学习提供了一条**可扩展（scalable）的路径**。

## 7. 优点

- **方法创新性**：
  - 将残差学习与 MoE 融合用于抓取策略，思路新颖；
  - 使用几何无关的基策略，简化了对物体几何先验的依赖。
- **训练高效**：相比传统多任务课程学习，显著降低了课程设计复杂度，且训练耗时极短（12h / 单 GPU）。
- **强泛化能力**：对未见物体具有零泛化差距，实用价值高。
- **可扩展性强**：为大规模式灵巧操作策略学习提供了清晰、可复用的范式。
- **代码与项目页**：作者提供了项目页面（project page）与视频，便于复现与可视化验证。

## 8. 不足与局限

- **实验对比细节有限**：所提供的元数据中未列出具体基线方法的对比数字，对 SOTA 结论的客观评估需查阅正文表格。
- **消融实验不明**：未明确说明针对残差学习、MoE 融合、几何无关基策略各组件的消融分析是否充分。
- **硬件细节缺失**：GPU 型号未明确，可能影响复现性评估。
- **物体类别多样性**：虽然 DexGraspNet 包含 3,200 个物体，但主要集中在刚性规则物体上，对**柔性物体、铰接物体**或**极端形状**的适用性尚不明确。
- **真实世界部署**：摘要未明确提及真实机器人平台上的实验，**仿真到真实的迁移（sim-to-real gap）** 仍是该类方法潜在的局限。
- **依赖基策略质量**：基策略的覆盖度与多样性直接决定了 MoE 融合的最终性能上限，若基策略训练不充分，可能限制整体表现。

（完）
