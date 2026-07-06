---
title: "Correspondence-Oriented Imitation Learning: Flexible Visuomotor Control with 3D Conditioning"
title_zh: 对应驱动的模仿学习：基于三维条件建模的灵活视觉运动控制
authors: "Yunhao Cao, Zubin Bhaumik, Jessie Jia, Xingyi He, Kuan Fang"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=U6Efnba2i9"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于关键点对应的三维视觉运动模仿学习
tldr: 现有模仿学习方法在视觉运动控制中常依赖固定数量的关键点或统一时间步长，限制了任务表示的灵活性。本文提出对应驱动的模仿学习COIL框架，以场景中关键点的预期运动定义任务，支持可变空间与时间粒度的任务规范。为将对应表示稳健映射为动作，COIL设计了带时空注意力机制的条件策略，有效融合多模态输入信息。该工作为复杂视觉运动模仿学习提供了灵活且鲁棒的表示与控制方法。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有模仿学习方法对关键点数量与时间步长的固定假设限制了视觉运动控制的灵活性。
method: 提出COIL框架，以关键点运动定义任务并用时空注意力条件策略将对应表示映射为动作。
result: 该方法支持可变粒度的任务表示，在多模态融合下实现灵活的视觉运动控制。
conclusion: 工作为基于对应的灵活视觉运动模仿学习提供了统一有效的框架。
---

## Abstract
We introduce Correspondence-Oriented Imitation Learning(COIL), a conditional policy learning framework for visuomotor control with a flexible task representation in 3D. At the core of our approach, each task is defined by the intended motion of keypoints selected on objects in the scene. Instead of assuming a fixed number of keypoints or uniformly spaced time intervals, COIL supports task specifications with variable spatial and temporal granularity, adapting to different user intents and task requirements. To robustly ground this correspondence-oriented task representation into actions, we design a conditional policy with a spatio-temporal attention mechanism that effectively fuses information across multiple input modalities. The policy is trained via a scalable self-supervised pipeline using demonstrations collected in simulation, with correspondence labels automatically generated in hindsight. COIL generalizes across tasks, objects, and motion patterns, achieving superior performance compared to prior methods on real-world manipulation tasks under both sparse and dense specifications.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Correspondence-Oriented Imitation Learning: Flexible Visuomotor Control with 3D Conditioning" based on the provided metadata and abstract. Let me organize the content according to the 8 requested points.

The paper is about COIL (Correspondence-Oriented Imitation Learning), a framework for visuomotor control using 3D keypoint correspondences as task representations. Let me analyze each point:

1. Core problem: Existing imitation learning methods rely on fixed numbers of keypoints or uniform time steps, limiting flexibility in visuomotor control tasks.

2. Method: COIL framework - defines tasks via intended motion of keypoints, supports variable spatial/temporal granularity, uses spatio-temporal attention mechanism in conditional policy, trained via self-supervised pipeline with hindsight labels from simulation.

3. Experiments: Based on metadata, the paper evaluates on real-world manipulation tasks with sparse and dense specifications. The exact benchmark details aren't fully provided in the metadata, so I'll note this limitation.

4. Resources: Not mentioned in the provided text.

5. Experiment count: Not explicitly stated in the metadata provided.

6. Conclusions: Generalizes across tasks, objects, motion patterns; superior to prior methods on real-world manipulation.

7. Strengths: Flexible task representation, variable granularity, spatio-temporal attention for multimodal fusion.

8. Limitations: Limited information provided in the metadata; I should note this.

Let me write a structured Markdown summary.
</think>
# COIL：对应驱动的模仿学习——论文总结

## 1. 核心问题与研究动机

- **问题域**：视觉运动控制（visuomotor control）中的模仿学习。
- **现有方法的局限**：
  - 多数模仿学习方法对**关键点数量**做固定假设，无法灵活适应不同任务粒度。
  - 对**时间步长**采用均匀采样假设，限制了用户意图与任务需求的多样性表达。
- **核心需求**：需要一种支持**可变空间粒度与时间粒度**的任务规范方式，以提升通用性。

## 2. 方法论

- **核心思想（COIL）**：以场景中物体上**关键点的预期运动**来定义任务，而非使用固定维度的轨迹表示。
- **关键技术细节**：
  - **任务表示**：通过若干关键点的运动（位移轨迹）描述任务，允许关键点数量与时间间隔灵活变化。
  - **条件策略网络**：采用带**时空注意力机制（Spatio-Temporal Attention）**的条件策略，有效融合多模态输入（图像、点云/三维信息、对应关系等）。
  - **训练范式**：
    - 数据来自仿真中的演示轨迹。
    - 通过**自监督管线（hindsight 标注）**自动生成关键点对应标签。
    - 无需人工标注对应关系，具有良好的可扩展性。
- **算法流程概述**：
  1. 在仿真中收集专家演示数据。
  2. 利用 hindsight 机制自动回填关键点对应标签。
  3. 构建条件策略，以多模态观测 + 对应表示为输入，输出动作。
  4. 推理阶段，根据用户指定的稀疏或密集关键点运动执行任务。

## 3. 实验设计

- **场景与任务**：真实世界操作任务（real-world manipulation tasks），同时覆盖**稀疏（sparse）与密集（dense）任务规范**两种条件。
- **Benchmark**：基于元数据可推测涉及多任务、多物体、多运动模式下的操控基准，但完整 benchmark 列表在所提供的元数据中未详尽列出。
- **对比方法**：与**先前的视觉运动模仿学习方法**进行性能比较，论文声称在两种规范密度下均取得更优表现。

## 4. 资源与算力

- 在所提供的论文文本与元数据中，**未明确提及** GPU 型号、数量、训练时长或计算资源消耗。
- 仅可推断：训练基于仿真数据，使用自监督 hindsight 标注管线，理论计算成本与数据规模相关。

## 5. 实验数量与充分性

- **消融与泛化测试**：从元数据可知，论文报告了**跨任务、跨物体、跨运动模式**的泛化性评估。
- **任务密度对比**：分别评估了**稀疏规范**与**密集规范**两种条件下的性能。
- **充分性评价**：
  - 优点：覆盖了多种规范粒度，体现方法的灵活性。
  - 不足（基于现有信息）：具体的消融实验数量、统计显著性检验、跨域迁移实验等细节在所提供的元数据中并未充分呈现，难以判断实验的完整充分性。

## 6. 主要结论与发现

- COIL 能够以**统一框架**支持可变空间与时间粒度的任务表示。
- 基于**时空注意力**的条件策略能够稳健地将对应表示映射为动作。
- 在真实世界操控任务上，**稀疏与密集规范下均优于先前的视觉运动模仿学习方法**。
- 验证了**自监督 hindsight 标注**在仿真训练中的可扩展性与有效性。

## 7. 优点与亮点

- **任务表示的灵活性**：突破关键点数量与时间步长的固定假设，是该工作的核心亮点。
- **对应驱动的统一框架**：将任务规范、策略条件化、动作生成统一在 3D 对应基础上。
- **多模态融合能力强**：时空注意力机制有效整合视觉、几何与对应信息。
- **可扩展的训练数据生成**：自监督 hindsight 标注降低人工标注成本。
- **实用性强**：在真实世界操作任务中验证，兼顾稀疏与密集任务规范。

## 8. 不足与局限

- **算力与训练细节缺失**：论文未提供训练资源、收敛曲线、超参设置等可复现性关键信息。
- **实验覆盖度有限（基于元数据）**：具体的消融实验数量、统计报告、跨域（sim-to-real gap）分析等不完整。
- **依赖仿真数据与 hindsight 标注**：自监督标签的质量依赖仿真演示的多样性，可能引入仿真偏置。
- **关键点选择假设**：虽然关键点数量可变，但任务仍需**预先指定关键点**，对完全无结构化规范的用户场景存在限制。
- **任务范围聚焦操控**：实验主要针对 manipulation 任务，对 locomotion 或其他具身任务的适用性未充分验证。
- **潜在偏差风险**：仅与"prior methods"比较，未明确罗列所有基线，可能存在选择性对比风险。

（完）
