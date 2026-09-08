---
title: "Action-Sketcher: From Reasoning to Action via Visual Sketches for Robotic Manipulation"
title_zh: Action-Sketcher：通过视觉草图实现机器人操作中从推理到动作的桥接
authors: "Tan, Huajie, Co, Peterson, Xu, Yijie, Rong, Shanyu, Ji, Yuheng, Chi, Cheng, Chen, Xiansheng, Zhao, Zhongxia, Wang, Pengwei, Wang, Zhongyuan, Zhang, Shanghang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Tan_Action-Sketcher_From_Reasoning_to_Action_via_Visual_Sketches_for_Robotic_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向长时序机器人操作的端到端VLA策略，强调闭环交互
tldr: 本文针对现有端到端与分层VLA策略在长时序机器人操作中过度依赖文本线索、难以在杂乱场景中实现指代落地的问题，提出了视觉草图作为新的中间表征。该方法可在机器人视角上渲染点、框、箭头及类型化关系，从而支持任务分解与因果解释。Action-Sketcher框架通过视觉草图桥接推理与动作，提升了在动态交互下的闭环适应性与时序鲁棒性，为复杂操作任务提供了更可解释的视觉到动作方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 1004, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 1134, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1791, \"height\": 761, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 850, \"height\": 414, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 879, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1818, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tan-action-sketcher-from-reasoning-to-action-via-visual-sketches-for-robotic-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 875, \"height\": 597, \"label\": \"Table\"}]"
motivation: 现有VLA策略依赖文本线索，在杂乱长时序任务中指代落地与因果解释能力不足。
method: 提出视觉草图作为中间表征，构建Action-Sketcher框架将推理转化为可执行的视觉动作。
result: 在长时序复杂操作任务中实现了更强的指代落地、任务分解与闭环鲁棒性。
conclusion: 视觉草图为VLA策略提供了更可解释、更鲁棒的视觉到动作映射。
---

## Abstract
Long-horizon robotic manipulation is increasingly important for real-world deployment, requiring spatial disambiguation in complex layouts and temporal resilience under dynamic interaction. However, existing end-to-end and hierarchical Vision-Language-Action (VLA) policies often rely on text-only cues while keeping plan intent latent, which undermines referential grounding in cluttered or underspecified scenes, impedes effective task decomposition of long-horizon goals with close-loop interaction, and limits causal explanation by obscuring the rationale behind action choices. To address these issues, we first introduce Visual Sketch, an implausible visual intermediate that renders points, boxes, arrows, and typed relations in the robot's current views to externalize spatial intent, connect language to scene geometry, and provide a human-verifiable bridge between high-level reasoning and low-level control. Building on Visual Sketch, we present Action-Sketcher, a VLA framework that operates in a cyclic See -> Think -> Sketch -> Act workflow coordinated by adaptive token-gated strategy for reasoning triggers, sketch revision, and action issuance, thereby supporting reactive corrections and human interaction while preserving real-time action prediction. To enable scalable training and evaluation, we curate diverse corpus with interleaved images, text, Visual Sketch supervision, and action sequences, and train Action-Sketcher with a multi-stage curriculum recipe that combines interleaved sequence alignment for modality unification, language-to-sketch consistency for precise linguistic grounding, and imitation learning augmented with sketch-to-action reinforcement for robustness. Extensive experiments on cluttered scenes and multi-object tasks, in simulation and on real-world tasks, show improved long-horizon success, stronger robustness to dynamic scene changes, and enhanced interpretability via editable sketches and step-wise plans.

---

## 论文详细总结（自动生成）

<think>The user wants me to provide a detailed Chinese summary of the paper "Action-Sketcher: From Reasoning to Action via Visual Sketches for Robotic Manipulation" following the specified structure with 8 points. Let me analyze the paper carefully.

The paper is about:
1. Problem: Long-horizon robotic manipulation challenges in VLA models, specifically:
   - Spatial disambiguation issues in cluttered scenes
   - Temporal brittleness in long-horizon tasks
   - Existing VLAs rely on text-only cues keeping plan intent latent
   - Lacks referential grounding, task decomposition, and causal explanation

2. Method:
   - Visual Sketch: explicit visual intermediate using points, boxes, arrows, relations
   - Action-Sketcher framework: See → Think → Sketch → Act loop
   - Token-gated strategy with `<BOR>` (begin-of-reasoning) and `<BOA>` (begin-of-action)
   - Two modes: Reasoning Mode and Action Mode
   - Three-stage training curriculum:
     - Stage 1: Foundational Spatiotemporal Learning (3.4M samples + 870k sequences)
     - Stage 2: Reasoning-to-Sketch Enhancement (21k samples)
     - Stage 3: Sketch-to-Action and Mode Adaptation
   - Backbone: π0 with flow-matching action expert
   - Visual Sketch elements:
     - Boxes (Bt): bounding boxes for object regions
     - Points (Pt): keypoints for precise locations
     - Arrows (At): translation arrows and rotation arrows

3. Experiments:
   - LIBERO benchmark (Spatial, Object, Goal, Long, Avg)
   - RoboTwin 2.0 (enhanced version with clutter)
   - Real-world: 3 tasks on Agilex and Galaxea dual-arm platforms
   - Tasks: Tidy Table, Pour Tea, Pick and Place
   - Baselines: DP, Octo, OpenVLA, SpatialVLA, π0, π0.5, OpenVLA-OFT, TraceVLA, Molmo-ACT, PixelVLA

4. Resources/Compute:
   - The paper doesn't explicitly mention GPU types, count, or training duration. I need to note this.

5. Experiments & Sufficiency:
   - LIBERO: 5 subcategories (Spatial, Object, Goal, Long, Avg)
   - RoboTwin 2.0: 5 tasks (Stack Blocks, Hang Mugs, Empty Cups, Place A2B Left, Place A2B Right)
   - Real-world: 3 tasks
   - Ablation: 3 dimensions (Framework Components, Visual Primitives, Training Stages)
   - Human-in-the-loop study
   - Failure analysis

6. Main conclusions:
   - Action-Sketcher outperforms SOTA baselines
   - Particularly strong on long-horizon and spatially complex tasks
   - Visual Sketch is critical (key for grounding)
   - Human-in-the-loop correction significantly improves success rates
   - Most failures are in spatial reasoning/Visual Sketch generation

7. Strengths:
   - Novel explicit visual intermediate representation
   - Three-stage curriculum learning
   - Human-in-the-loop capability
   - Comprehensive ablations
   - Both simulation and real-world validation
   - Token-gated adaptive switching mechanism

8. Limitations:
   - Compute resources not specified
   - Failure analysis shows 61% of errors are in Visual Sketch generation
   - Limited to ego-view reference frame
   - Data imbalance between modes requires special sampling
   - 12% failure rate due to incorrect mode switching
   - Limited tasks in real-world evaluation

Let me structure this into the requested format. I need to use Markdown headers and bullet points, be concise but comprehensive, and end with "（完）".</think>

# Action-Sketcher 论文总结

## 1. 核心问题与研究动机

- **应用背景**：长时序、开放世界的机器人操作任务需要处理复杂的空间布局和动态交互，要求智能体在语言指代存在歧义、目标未充分定义时仍能可靠执行。
- **现有方法的不足**：
  - 端到端 VLA（如 OpenVLA、π0、Diffusion Policy 等）将规划意图隐式编码在潜空间中，难以解释。
  - 分层 VLA（如 Hi Robot、Helix）缺乏对全局意图（如目标演化、错误状态、历史信息）的持续建模。
  - "Think before Act" 类方法（如 EO-1、OneTwoVLA、THINK_ACT）的中间推理多为纯文本，无法显式表达接触点、接近方向、物体间空间关系等几何信息。
- **关键瓶颈**：
  - 空间维度：自然语言指代在多物体场景中存在歧义（如多杯场景下的"将茶倒入杯中"），难以转化为可执行的几何约束。
  - 时间维度：人类难以介入纠正，错误易累积而缺乏可解释的规划结构。
- **本文立场**：将"空间意图"通过**可视化草图**显式外化，作为高层推理与低层控制之间的可验证"桥梁"。

## 2. 方法论

### 2.1 核心思想

- 引入**Visual Sketch** 作为显式视觉中间表征，在机器人当前视角上渲染稀疏的几何基元（点、框、箭头、类型化关系），以消除指代歧义、提供人可验证/可编辑的规划接口。
- 构建 **Action-Sketcher** 框架，运行 **See → Think → Sketch → Act** 闭环循环，由自适应 **Token-Gated 策略**协调推理触发、草图修订与动作生成。

### 2.2 关键技术细节

- **Visual Sketch 三类基元**：
  - **Boxes (B_t)**：目标区域的物体级边界框，参数化为左上/右下像素坐标，用于消除指代歧义。
  - **Points (P_t)**：关键接触/目标像素点，可表示部位级可供性、运动路径点或几何参考点（如茶壶把手 phandle、壶嘴 pspout、杯心 pcup）。
  - **Arrows (A_t)**：由 A_trans（平移轨迹箭头 (p_start, p_end)）与 A_rot（绕 x/y/z 轴的旋转箭头 (p_i, axis, dir)）构成，将 SE(3) 操作分解到 2D 图像平面。
- **形式化定义**：S_t = {B_t, P_t, A_t}，所有基元定义于自视图像平面上（统一参考系）。
- **双模态推理与切换**：
  - **Reasoning Mode**：生成 `<BOR>` 触发，先做时序推理（分解下一个子任务），再做空间推理（生成草图文本描述），以 `<EOR>` 结束；草图文本随后被渲染为图像。
  - **Action Mode**：生成 `<BOA>` 触发，调用基于 Flow-Matching 的 Action Expert 输出一段 action chunk。
  - **Token-Gated 自适应切换**：依据状态、预测风险、用户反馈在两种模式间切换，支持实时中断处理。
- **模型结构**：以 π0 为骨干，LLM 头负责文本推理/草图生成，Action Head（Flow-Matching）输出连续动作；模型架构与 VLA 无关，可替换。
- **多阶段课程训练**：
  - **Stage 1 基础时空预训练**：约 340 万样本（含 Visual Grounding、Spatial Pointing、Scene Understanding、VQA），以及 EgoPlan/ShareRobot/AgiBot-World 整合的 87 万时序序列，其中 20% 标注 GPT-4o 文本推理。
  - **Stage 2 推理-草图增强**：自采 2.6k 长时序真实回合 + 1.7k LIBERO/RoboTwin 2.0 标注轨迹，共 21k 样本用于 Reasoning Mode 训练。
  - **Stage 3 草图-动作与模式自适应**：对草图引入扰动增强（boxes 保持 IoU≥0.8，points 在半径 c 圆内采样），并采用**模式均衡采样**（等概率从 Reasoning/Action 数据集各取一半）缓解数据不平衡。

### 2.3 算法流程概述

1. 输入多视角图像、任务指令、历史子任务；
2. 若需推理 → 进入 Reasoning Mode，输出子任务文本 + 草图文本 → 渲染为草图图像并更新上下文；
3. 否则进入 Action Mode → 由 Flow-Matching Action Expert 输出 action chunk；
4. 实时评估状态变化、风险、用户反馈，决定是否再次切换。

## 3. 实验设计

### 3.1 基准与场景

- **仿真**：
  - **LIBERO**：含 Spatial / Object / Goal / Long / Avg 共 5 类子集。
  - **RoboTwin 2.0 增强版**：提高物体杂乱度与空间复杂度，包含 Stack Blocks、Hang Mugs、Empty Cups、Place A2B Left、Place A2B Right。
- **真实世界**：在 Agilex 与 Galaxea 双臂机器人平台执行 3 项长时序任务：
  - Tidying a cluttered tabletop（长时序）
  - Pouring tea（长时序 + 空间复杂度）
  - General pick-and-place（带歧义指令的空间任务）

### 3.2 对比方法

- **端到端 VLA**：Diffusion Policy (DP)、Octo、OpenVLA。
- **架构型 VLA**：SpatialVLA、π0、π0+FAST、π0.5、OpenVLA-OFT。
- **视觉提示/中间表征型 VLA**：TraceVLA、Molmo-ACT、PixelVLA。

## 4. 资源与算力

- 论文正文及附录**未明确披露**所使用 GPU 型号、数量、训练时长、显存占用等算力细节。
- 仅可推断：Stage 1 数据量约 340 万 + 87 万样本；Stage 2 含 21k 草图-推理样本；Stage 3 动作专家训练使用带扰动的草图增强数据。
- 未能找到算力相关说明属于**披露缺失**。

## 5. 实验数量与充分性

- **基准对比**：LIBERO（5 类指标）+ RoboTwin 2.0（5 个任务）+ 真实世界（3 个任务），共 13 项主要任务指标。
- **人工介入研究**：对比 3 个真实任务在 "Original" 与 "+ Human-in-Loop" 下的子任务完成率（Tab. 3）。
- **失败分析**：统计了错误模式切换（12%）、Reasoning Mode 错误（66%）、Action Mode 错误（19%），并细化到 61% 的失败源于 Visual Sketch 空间推理错误。
- **消融实验**（Tab. 4）覆盖三个维度：
  - 框架组件（去除空间推理或视觉草图）；
  - 视觉基元（分别去除 bbox、keypoint、arrow）；
  - 训练阶段（分别去除 Stage 1/2/3）。
- **客观性评估**：包含仿真 + 真实双重验证、ablation、对照基线丰富；真实世界采用子任务完成率作为更细粒度指标。
- **充分性局限**：真实任务种类偏少（仅 3 个）、每个任务的回合数未在摘录中明确、对照人类干预下的成功率提升未说明基线是否同样可介入。

## 6. 主要结论与发现

- **总体性能**：Action-Sketcher 在 LIBERO、RoboTwin 2.0、真实世界任务上均达到 SOTA 或近 SOTA 水平，在 "Long" 类长时序测试上提升最为显著。
- **关键瓶颈定位**：失败主要由 **Visual Sketch 空间推理不准确**造成（占 61%），说明空间落地的显式化是性能上限的关键。
- **草图即接口**：通过"草图修正"实现的人机协同显著提升真实任务完成率（如 Tidy Table +23.0%、Pick & Place +18.5%、Pour Tea +16.4%）。
- **组件必要性**：Stage 3（草图-动作联合训练）不可或缺，缺失后性能归零；Keypoint 是草图最关键基元；Stage 2（推理-草图一致性）对正确草图生成至关重要。
- **模式均衡采样**：有效缓解 Action Mode 样本远多于 Reasoning Mode 所致的偏置问题。

## 7. 优点

- **新颖的显式中间表征**：将空间意图以几何基元可视化、可编辑，是相对"潜在规划"的差异化贡献。
- **闭环自适应切换**：`<BOR>` / `<BOA>` 触发机制兼顾实时性与可中断性，支持人介入修正。
- **多阶段课程训练**：从通用时空 → 推理-草图一致性 → 草图-动作鲁棒性，层次清晰且经消融验证。
- **数据增强设计**：草图扰动增强提高 Action Expert 对草图小误差的鲁棒性。
- **双重评估维度**：仿真基准 + 真实双臂平台，含失败分析与 HIL 实验，证据较完整。
- **可解释性与可协作性**：草图天然支持人机协作（Tab. 3 显著提升）。

## 8. 不足与局限

- **算力披露缺失**：未给出 GPU 型号/数量、训练时长、超参数细节，**复现成本不透明**。
- **基线公平性存疑**：TraceVLA、Molmo-ACT、PixelVLA 等视觉提示型基线在论文中的对照较弱（如 TraceVLA 在 LIBERO Long 仅 54.1%，与本文 96.0% 差距悬殊），可能存在**实现细节差异**导致对比不公平。
- **真实任务规模有限**：仅 3 个真实任务，每个任务的评估回合数、统计显著性检验未明确，可能存在**方差未报告**问题。
- **失败模式集中**：61% 失败集中在 Sketch 生成，说明 Reasoning Mode 仍是性能瓶颈；当前缓解依赖人类干预而非模型自身修复。
- **参考系单一**：草图定义于自视图像平面，未充分讨论跨视角对齐、相机标定误差对箭头/框投影的影响。
- **HIL 实验设计**：仅展示"草图修正"的平均收益，未给出误修正、过度修正、人为延迟等**鲁棒性子分析**。
- **应用范围限制**：当前仅在桌面杂乱、双臂结构化场景验证，对**移动操作、柔性物体、可变形目标**等场景未涉及。

（完）
