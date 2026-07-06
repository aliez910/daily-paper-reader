---
title: "Cortical Policy: A Dual-Stream View Transformer for Robotic Manipulation"
title_zh: Cortical Policy：用于机器人操控的双流视图Transformer
authors: "Xuening Zhang, Qi Lv, Xiang Deng, Miao Zhang, Xingbo Liu, Liqiang Nie"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=eWe8zqGvs5"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过视觉到动作映射的视图Transformer预测机器人操控动作
tldr: 本文针对机器人操控中视图Transformer三维空间推理不足、动态适应性差的问题展开研究。借鉴人脑整合静态与动态视图的机制，作者提出Cortical Policy，一种双流视图Transformer。静态流通过预训练3D基础模型提取几何一致关键点增强空间理解，动态流支持操控过程中的动态适应。该双流设计将互补信息流融合，显著提升了视觉到动作映射的质量，为操控策略提供了更鲁棒的空间感知与动态适应能力。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有视图Transformer在机器人操控中三维空间推理不足且缺乏动态适应性。
method: 提出双流视图Transformer，静态流基于3D基础模型关键点增强空间理解，动态流支持动态适应。
result: 通过双流互补信息融合，显著提升了操控策略的视觉到动作映射质量与鲁棒性。
conclusion: 仿生双流架构能有效提升机器人操控中视图Transformer的空间与动态建模能力。
---

## Abstract
View transformers process multi-view observations to predict actions and have shown impressive performance in robotic manipulation. Existing methods typically extract static visual representations in a view-specific manner, leading to inadequate 3D spatial reasoning ability and a lack of dynamic adaptation. Taking inspiration from how the human brain integrates static and dynamic views to address these challenges, we propose Cortical Policy, a novel dual-stream view transformer for robotic manipulation that jointly reasons from static-view and dynamic-view streams. The static-view stream enhances spatial understanding by aligning features of geometrically consistent keypoints extracted from a pretrained 3D foundation model. The dynamic-view stream achieves adaptive adjustment through position-aware pretraining of an egocentric gaze estimation model, computationally replicating the human cortical dorsal pathway. Subsequently, the complementary view representations of both streams are integrated to determine the final actions, enabling the model to handle spatially-complex and dynamically-changing tasks under language conditions. Empirical evaluations on RLBench, the challenging COLOSSEUM benchmark, and real-world tasks demonstrate that Cortical Policy outperforms state-of-the-art baselines substantially, validating the superiority of dual-stream design for visuomotor control. Our cortex-inspired framework offers a fresh perspective for robotic manipulation and holds potential for broader application in vision-based robot control.

---

## 论文详细总结（自动生成）

<think>
The user wants me to write a detailed Chinese summary of the paper "Cortical Policy: A Dual-Stream View Transformer for Robotic Manipulation" based on the abstract and metadata provided. Let me organize my response according to the 8 requested points.

Let me analyze what I have:
- The paper is about a dual-stream view transformer for robotic manipulation
- It's inspired by how human brain integrates static and dynamic views
- It has two streams: static-view and dynamic-view
- Static stream uses pretrained 3D foundation model for geometrically consistent keypoints
- Dynamic stream uses egocentric gaze estimation model
- Tested on RLBench, COLOSSEUM benchmark, and real-world tasks
- ICLR 2026 accepted
- The PDF couldn't be fully extracted (CAPTCHA), so I have limited details

I need to be careful to only use information from the abstract and metadata provided, and clearly note limitations when info is not available.
</think>
# Cortical Policy 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有用于机器人操控的视图 Transformer（view transformer）在处理多视角观测以预测动作时，存在两个关键不足：
  - **三维空间推理能力不足**：现有方法多以"视图特定"（view-specific）方式提取静态视觉表征，难以建立跨视角一致的三维几何理解。
  - **动态适应性差**：方法缺乏对操控过程中视角和场景动态变化的适应能力，难以处理空间复杂且任务动态变化的场景。
- **整体含义**：作者受人类大脑"静/动态视图整合"机制的启发，提出了一种仿生双流架构，将静态空间推理与动态自适应能力结合，旨在提升机器人在语言指令条件下的视运动控制（visuomotor control）质量与鲁棒性。
- **研究意义**：为视觉驱动的机器人操控提供新的架构思路（cortex-inspired framework），并具备向更广泛的基于视觉的机器人控制场景扩展的潜力。

## 2. 方法论

### 2.1 核心思想
- 提出 **Cortical Policy**，一种**双流（dual-stream）视图 Transformer**：
  - **静态视图流（static-view stream）**：增强对三维空间的理解。
  - **动态视图流（dynamic-view stream）**：增强操控过程中的动态适应性。
- 二者在语言条件（language condition）下进行融合，共同预测最终动作。

### 2.2 关键技术细节
- **静态视图流**：
  - 利用**预训练的 3D 基础模型（pretrained 3D foundation model）**提取**几何一致的关键点（geometrically consistent keypoints）**。
  - 通过对齐这些关键点对应的特征来构建跨视图一致的空间表征，从而弥补现有方法三维推理不足的问题。
- **动态视图流**：
  - 采用**自我中心（egocentric）注视估计模型**，并通过**位置感知的预训练（position-aware pretraining）** 进行自适应调整。
  - 在计算层面模拟人类大脑的**皮层背侧通路（cortical dorsal pathway）**，实现对动态视角的适应。
- **融合与决策**：
  - 双流输出的**互补视图表征（complementary view representations）**被融合后用于最终动作预测，使模型可同时应对"空间复杂"和"动态变化"两类任务。

### 2.3 算法流程（文字描述）
1. 输入多视角观测与语言指令；
2. 静态流：3D 基础模型 → 几何关键点 → 关键点特征对齐 → 静态空间表征；
3. 动态流：自我中心注视估计模型 + 位置感知预训练 → 动态自适应表征；
4. 双流互补融合 → 动作预测。

> 注：因 PDF 文本未能完整提取（受 CAPTCHA 限制），上述流程依据摘要与元数据重建，具体公式与架构细节以官方论文为准。

## 3. 实验设计

- **数据集 / 场景**：
  - **RLBench**：常用机器人操控基准仿真平台。
  - **COLOSSEUM benchmark**：作者明确标注为"具有挑战性的基准"，主要测试策略在不同扰动/泛化条件下的鲁棒性。
  - **真实世界任务（real-world tasks）**：用于验证 sim-to-real 性能。
- **对比方法**：与多个**当前最优基线（state-of-the-art baselines）**进行对比（具体基线名称未在可获取的摘要片段中列出）。
- **评测条件**：在语言指令条件下进行，对模型处理"空间复杂 + 动态变化"任务的能力进行评估。

## 4. 资源与算力

- 可获取的摘要与元数据中**未明确披露**所使用的 GPU 型号、数量、训练时长等算力信息。
- 唯一与算力相关的提示是：动态流使用"位置感知预训练"的注视估计模型、静态流使用"预训练 3D 基础模型"，说明其依赖了**预训练模型权重**，但具体计算开销未给出。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 仿真层面：RLBench + COLOSSEUM 两个基准。
  - 真实世界：real-world tasks 验证。
  - 从摘要描述推断，作者应至少报告了**主结果对比**与**真实世界泛化**两类实验。
- **充分性评估**：
  - 优点：实验同时覆盖**仿真基准（RLBench）**、**扰动泛化基准（COLOSSEUM）**与**真实场景**，三维验证较为全面，符合机器人操控论文的常规标准。
  - 局限（基于现有信息）：是否包含**消融实验（ablation）**、**双流各组件贡献分析**、**语言条件消融**、**不同预训练模型替换对比**等，**在可获取的文本中未明确说明**，因此尚无法判断消融充分性。
  - 公平性方面：摘要中未提及随机种子数、试验次数、统计显著性检验等元信息，因此**客观性与公平性细节有待查阅正文确认**。

## 6. 主要结论与发现

- **性能优势**：Cortical Policy 在 RLBench、COLOSSEUM 以及真实世界任务上**显著优于现有 SOTA 基线**，验证了双流设计的优越性。
- **架构有效性**：
  - 静态流（3D 关键点对齐）有效增强空间推理。
  - 动态流（注视估计 + 位置感知预训练）有效增强动态适应性。
  - 双流融合对"空间复杂 + 动态变化"任务具有显著增益。
- **范式贡献**：仿生（cortex-inspired）双流框架为机器人操控与基于视觉的机器人控制提供了新视角。

## 7. 优点

- **仿生设计动机清晰**：将人类大脑的"静态/动态视图整合"机制显式映射到双流网络架构，故事性强、解释性好。
- **结构合理**：静态流 + 动态流分别针对"空间"与"动态"两类挑战，**职责清晰、信息互补**。
- **依赖成熟预训练模型**：复用 3D 基础模型与注视估计模型，**减少从零训练成本**、提升特征质量。
- **实验三维验证**：仿真（RLBench）+ 鲁棒性（COLOSSEUM）+ 真实世界三类评测，**整体验证较为充分**。
- **应用前景**：作者明确指出该框架具备向**更广泛的视觉机器人控制**扩展的潜力。

## 8. 不足与局限

- **算力与可复现性信息缺失**：摘要未披露 GPU、训练时长、超参等关键信息，**复现成本难以估计**。
- **对预训练模型的强依赖**：性能受益于外部 3D 基础模型与注视估计模型，可能引入**领域偏差（domain bias）**；在操控场景与预训练数据分布差异大时，性能可能受影响。
- **实验细节不充分**：是否包含完整消融、显著性检验、不同语言指令复杂度分析等，**在可见文本中未说明**。
- **双流计算开销**：双流架构相比单流会**增加推理延迟与显存占用**，对实时性要求高的真实场景部署可能存在挑战，论文未就此展开讨论。
- **应用范围局限**：尽管作者声称可推广到更广泛的视觉机器人控制，但摘要中**仅在操控（manipulation）**任务上验证，泛化到导航、移动操作等其他任务的可行性**有待进一步验证**。
- **偏差风险**：实验基线与场景可能存在选择性报告风险（仅可看到摘要层面声称"显著优于 SOTA"），**具体提升幅度**与统计显著性需查阅正文。

（完）
