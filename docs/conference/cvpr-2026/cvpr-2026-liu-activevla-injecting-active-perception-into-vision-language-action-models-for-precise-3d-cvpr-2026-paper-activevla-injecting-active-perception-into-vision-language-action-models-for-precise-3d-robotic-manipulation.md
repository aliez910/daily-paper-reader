---
title: "ActiveVLA: Injecting Active Perception into Vision-Language-Action Models for Precise 3D Robotic Manipulation"
title_zh: ActiveVLA：为精确三维机器人操作注入主动感知的视觉语言动作模型
authors: "Liu, Zhenyang, Gu, Yongchong, Wang, Yikai, Xue, Xiangyang, Fu, Yanwei"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_ActiveVLA_Injecting_Active_Perception_into_Vision-Language-Action_Models_for_Precise_3D_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: VLA模型引入主动感知，支持闭环3D操作中的自适应视点控制
tldr: 现有VLA方法多依赖静态腕部相机，无法在任务执行中自适应选择最优视点。本文提出ActiveVLA，将主动感知注入VLA范式，使机器人能在长时程与细粒度操作中动态调整视觉输入。该方法将视觉与动作预测在闭环中紧密耦合，显著提升了三维机器人操作的精度与鲁棒性。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1735, \"height\": 1104, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1766, \"height\": 696, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1769, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 822, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 664, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1806, \"height\": 967, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 586, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-activevla-injecting-active-perception-into-vision-language-action-models-for-precise-3d-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 856, \"height\": 285, \"label\": \"Table\"}]"
motivation: 静态腕部相机限制了VLA模型在长时程和细粒度操作中的视点自适应能力。
method: 提出ActiveVLA，将主动感知集成到VLA中，实现任务执行中的动态视点选择。
result: 在精确三维机器人操作任务中显著提升性能与鲁棒性。
conclusion: 该工作推动了闭环视觉反馈与VLA策略的深度融合。
---

## Abstract
Recent advances in robot manipulation have leveraged pre-trained vision-language models (VLMs) and explored integrating 3D spatial signals into these models for effective action prediction, giving rise to the promising vision-language-action (VLA) paradigm. However, most existing approaches overlook the importance of active perception: they typically rely on static, wrist-mounted cameras that provide an end-effector-centric viewpoint. As a result, these models are unable to adaptively select optimal viewpoints or resolutions during task execution, which significantly limits their performance in long-horizon tasks and fine-grained manipulation scenarios. To address these limitations, we propose ActiveVLA, a novel vision-language-action framework that empowers robots with active perception capabilities for high-precision, fine-grained manipulation. ActiveVLA adopts a coarse-to-fine paradigm, dividing the process into two stages:(1) Critical region localization. ActiveVLA projects 3D inputs onto multi-view 2D projections, identifies critical 3D regions, and supports dynamic spatial awareness.(2) Active perception optimization. Drawing on the localized critical regions, ActiveVLA uses an active view selection strategy to choose optimal viewpoints. These viewpoints aim to maximize amodal relevance and diversity while minimizing occlusions. Additionally, ActiveVLA applies a 3D zoom-in to improve resolution in key areas. Together, these steps enable finer-grained active perception for precise manipulation.Extensive experiments demonstrate that ActiveVLA achieves precise 3D manipulation and outperforms state-of-the-art baselines on three simulation benchmarks. Moreover, ActiveVLA transfers seamlessly to real-world scenarios, enabling robots to learn high-precision tasks in complex environments.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "ActiveVLA: Injecting Active Perception into Vision-Language-Action Models for Precise 3D Robotic Manipulation". Let me organize my response according to the requested structure.

The paper is about:
1. VLA models for robotic manipulation
2. Limitation: static wrist-mounted cameras
3. Proposed: ActiveVLA with active perception
4. Two stages: critical region localization + active perception optimization
5. Experiments on 3 simulation benchmarks + real-world transfer

Let me write a comprehensive Chinese summary following the requested structure.

Key points from abstract:
- VLA paradigm uses pre-trained VLMs + 3D spatial signals for action prediction
- Problem: most rely on static wrist-mounted cameras with end-effector-centric viewpoint
- Limitation: can't adaptively select optimal viewpoints/resolutions
- ActiveVLA: coarse-to-fine paradigm
  - Stage 1: Critical region localization - projects 3D inputs onto multi-view 2D projections, identifies critical 3D regions
  - Stage 2: Active perception optimization - active view selection strategy to choose optimal viewpoints (maximize amodal relevance and diversity, minimize occlusions) + 3D zoom-in for resolution
- Experiments: 3 simulation benchmarks + real-world transfer

I'll structure this carefully with all 8 required sections.</think>

# ActiveVLA 论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：近年来，机器人操作领域兴起"视觉-语言-动作"（Vision-Language-Action, VLA）范式，即利用预训练的视觉语言模型（VLM）并融合 3D 空间信号进行动作预测。
- **关键瓶颈**：现有 VLA 方法大多依赖**静态腕部相机**（wrist-mounted camera），只能提供以末端执行器为中心的固定视角，无法在任务执行过程中**自适应地选择最优视点或分辨率**。
- **实际影响**：这一限制导致模型在**长时程任务（long-horizon tasks）**和**细粒度操作（fine-grained manipulation）**场景中表现受限，例如需要多角度观察的精密装配、对细小物体的精准抓取等。
- **核心动机**：将"主动感知（Active Perception）"能力引入 VLA 框架，使机器人能在闭环执行中**动态调整视觉输入**，从而实现高精度 3D 操作。

---

## 2. 方法论：核心思想与关键技术细节

### 2.1 整体范式：粗到精（Coarse-to-Fine）

ActiveVLA 采用两阶段流程，将 3D 主动感知与动作预测紧密耦合：

#### 阶段一：关键区域定位（Critical Region Localization）
- 将 **3D 输入投影到多视角 2D 投影图**（multi-view 2D projections），既保留 3D 几何信息，又能复用 VLM 的 2D 视觉编码能力。
- 在多视图表征上识别与任务相关的**关键 3D 区域**，实现动态空间感知。

#### 阶段二：主动感知优化（Active Perception Optimization）
基于定位到的关键区域，进一步做：
- **主动视点选择（Active View Selection）**：在多个候选视点中选出**最优视角**，优化准则为同时提升**无模态相关性（amodal relevance）**与**视点多样性（diversity）**，并尽量**最小化遮挡**。
- **3D 放大（3D Zoom-in）**：对关键区域进行分辨率提升（zoom-in），使模型获得更精细的视觉特征。

### 2.2 关键技术贡献
- 视点选择本质上是一个**多目标优化**：最大化信息量（相关性 + 多样性）、最小化遮挡。
- 将"看哪里"和"怎么做"在**闭环**中耦合，而非先感知后动作的串行范式。
- 通过多视图 2D 投影，弥合 3D 点云与 VLM 之间的表示鸿沟。

---

## 3. 实验设计

### 3.1 数据集 / 场景
- **仿真基准**：在 **3 个仿真 benchmark** 上进行评估（具体名称在论文正文中给出，常见为 RLBench 类桌面操作套件，但本提取文本未明确列出名称）。
- **真实世界**：在真实机器人平台上进行迁移验证，涵盖复杂环境下的高精度任务。

### 3.2 对比方法
- 与**当前 SOTA 基线**（state-of-the-art baselines）进行比较，涵盖典型 VLA 类方法及依赖静态腕部相机的 3D 操作方法。

### 3.3 评估指标
（文中摘要未详述，正文应包括任务成功率、视点合理性等指标。）

---

## 4. 资源与算力

- 摘要与提供的元数据中**未明确披露** GPU 型号、数量、训练时长、参数量等算力信息。
- 建议参考论文正文中的"Implementation Details"或附录部分以获取具体配置。

---

## 5. 实验数量与充分性

- **实验规模**：覆盖 3 个仿真基准 + 真实机器人迁移实验。
- **充分性评估**：
  - 既有仿真也有真机迁移，**跨域验证较充分**。
  - 但仅依据摘要无法判断是否包含：
    - 不同 VLM backbone 的消融（如不同规模 / 不同预训练数据）
    - 视点选择各目标（相关性 / 多样性 / 遮挡）的独立消融
    - 噪声、扰动下的鲁棒性测试
  - 真实世界任务的具体数量与多样性需要参考正文实验章节。

---

## 6. 主要结论与发现

- ActiveVLA 实现了**精确的 3D 操作**，在 3 个仿真基准上**超越 SOTA**。
- 提出的**粗到精主动感知范式**有效提升了模型在长时程与细粒度任务中的表现。
- 框架可**无缝迁移至真实场景**，使机器人学习复杂环境中的高精度任务成为可能。
- 验证了**闭环视觉反馈与 VLA 策略深度融合**的可行性与有效性。

---

## 7. 优点

- **问题切入精准**：直击 VLA 中静态视角这一被忽视但关键的痛点。
- **方法新颖**：将"主动感知"显式注入 VLA，提出 coarse-to-fine 的两阶段流程。
- **多目标视点选择**：同时考虑相关性、多样性、遮挡，比单一指标更贴近真实需求。
- **多视图 2D 投影**：巧妙利用成熟 VLM 的 2D 编码能力，避免直接处理 3D 点云带来的算力开销与训练不稳定。
- **3D zoom-in**：在关键区域提升分辨率，针对细粒度操作十分有效。
- **仿真 + 真机迁移**：实验设置完整，验证了实用价值。

---

## 8. 不足与局限

- **算力 / 训练细节缺失**：摘要未披露训练成本，复现难度较大。
- **基准与任务多样性受限**：仅 3 个仿真基准，真实世界任务数量、物体类别与扰动条件的覆盖度需进一步了解正文。
- **视点选择策略的可解释性**：虽提出多目标优化，但选择过程是否依赖大量预计算候选视图、若场景动态变化是否仍能实时响应，需要正文验证。
- **主动感知与动作预测的耦合机制**：摘要未细说"闭环耦合"的具体实现（例如是否引入反馈延迟、视点变化如何影响下一时刻动作），存在信息不充分的风险。
- **VLM 依赖性**：方法依赖预训练 VLM，对 VLM 的视觉能力（特别是 3D 几何理解）有较高要求，可能存在**领域偏差风险**。
- **真机验证规模**：未给出真实实验中任务数与尝试次数，难以判断统计显著性。

（完）
