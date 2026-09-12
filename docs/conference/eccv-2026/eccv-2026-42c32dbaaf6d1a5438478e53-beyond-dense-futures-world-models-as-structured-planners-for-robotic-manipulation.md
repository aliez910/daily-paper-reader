---
title: "Beyond Dense Futures: World Models as Structured Planners for Robotic Manipulation"
title_zh: 超越密集未来：将世界模型作为结构化规划器用于机器人操纵
authors: "Minghao Jin, Mozheng Liao, Mingfei Han, Zhihui Li, Xiaojun Chang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/264.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 将世界模型重构为结构化规划器的VLA用于复杂机器人操纵
tldr: 基于世界模型的视觉-语言-动作架构虽通过视觉前瞻提升了机器人操纵能力，但密集未来预测引入视觉冗余并累积误差，易导致长视距规划漂移；而稀疏方法多以高层语义子目标或隐式潜状态表达，缺乏显式运动学约束，使规划与底层执行难以对齐。本文提出StructVLA，将生成式世界模型重构为显式结构化规划器，预测稀疏且物理上有意义的关键状态作为规划锚点，弥补密集与稀疏两类方案的不足，从而在长视距复杂机器人操纵任务中实现更可靠的端到端视觉运动控制与模仿学习表现。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 480, \"height\": 426}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 480, \"height\": 426}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 486, \"height\": 432}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-004.webp\", \"caption\": \"\", \"page\": 9, \"index\": 4, \"width\": 1400, \"height\": 234}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-005.webp\", \"caption\": \"\", \"page\": 9, \"index\": 5, \"width\": 1400, \"height\": 234}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-006.webp\", \"caption\": \"\", \"page\": 9, \"index\": 6, \"width\": 1400, \"height\": 234}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-007.webp\", \"caption\": \"\", \"page\": 9, \"index\": 7, \"width\": 1400, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-008.webp\", \"caption\": \"\", \"page\": 9, \"index\": 8, \"width\": 585, \"height\": 441}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-009.webp\", \"caption\": \"\", \"page\": 9, \"index\": 9, \"width\": 511, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-010.webp\", \"caption\": \"\", \"page\": 9, \"index\": 10, \"width\": 511, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-011.webp\", \"caption\": \"\", \"page\": 13, \"index\": 11, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-012.webp\", \"caption\": \"\", \"page\": 13, \"index\": 12, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-013.webp\", \"caption\": \"\", \"page\": 13, \"index\": 13, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-014.webp\", \"caption\": \"\", \"page\": 13, \"index\": 14, \"width\": 540, \"height\": 304}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-015.webp\", \"caption\": \"\", \"page\": 13, \"index\": 15, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-016.webp\", \"caption\": \"\", \"page\": 13, \"index\": 16, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-017.webp\", \"caption\": \"\", \"page\": 13, \"index\": 17, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-018.webp\", \"caption\": \"\", \"page\": 13, \"index\": 18, \"width\": 540, \"height\": 304}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-019.webp\", \"caption\": \"\", \"page\": 13, \"index\": 19, \"width\": 540, \"height\": 304}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-020.webp\", \"caption\": \"\", \"page\": 13, \"index\": 20, \"width\": 540, \"height\": 304}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-021.webp\", \"caption\": \"\", \"page\": 13, \"index\": 21, \"width\": 538, \"height\": 303}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-42c32dbaaf6d1a5438478e53/fig-022.webp\", \"caption\": \"\", \"page\": 13, \"index\": 22, \"width\": 538, \"height\": 303}]"
motivation: 密集未来预测带来冗余与误差累积，稀疏方法又缺乏运动学约束，难以对齐长视距操纵执行。
method: 将生成式世界模型重构为显式结构化规划器，预测稀疏且物理一致的关键状态锚点。
result: 在长视距复杂机器人操纵任务中实现更可靠的端到端VLA控制表现。
conclusion: 结构化稀疏前瞻使VLA在长视距操纵中兼具稳定性与运动学一致性。
---

## Abstract
Recent world-model-based Vision-Language-Action (VLA)architectures have improved robotic manipulation through predictive vi-sual foresight. However, dense future prediction introduces visual redun-dancy and accumulates errors, causing long-horizon plan drift. Mean-while, recent sparse methods typically represent visual foresight usinghigh-level semantic subtasks or implicit latent states. These representa-tions often lack explicit kinematic grounding, weakening the alignmentbetween planning and low-level execution. To address this, we proposeStructVLA, which reformulates a generative world model into an explicitstructured planner for reliable control. Instead of dense rollouts or seman-tic goals, StructVLA predicts sparse, physically meaningful structuredframes. Derived from intrinsic kinematic cues (e.g., gripper transitionsand kinematic turning points), these frames capture spatiotemporal mile-stones closely aligned with task progress. We implement this approachthrough a two-stage training paradigm with a unified discrete token vo-cabulary: the world model is first trained to predict structured frames andsubsequently optimized to map the structured foresight into low-level ac-tions. This approach provides clear physical guidance and bridges visualplanning and motion control. In our experiments, StructVLA achievesstrong average success rates of 75.0% on SimplerEnv-WidowX and 94.8%on LIBERO. Real-world deployments further demonstrate reliable taskcompletion and robust generalization across both basic pick-and-placeand complex long-horizon tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Beyond Dense Futures: World Models as Structured Planners for Robotic Manipulation" (StructVLA). I need to organize the summary according to the 8 specified points, using Markdown formatting with hierarchical headings and bullet points.

Let me analyze the paper carefully:

1. **Core problem**: World-model-based VLA architectures have issues - dense future prediction causes redundancy and error accumulation (plan drift), while sparse methods using semantic subtasks or implicit latent states lack kinematic grounding. The paper aims to bridge visual planning and motion control.

2. **Methodology**: 
- StructVLA reformulates generative world model into explicit structured planner
- Predicts sparse structured frames from kinematic cues (gripper transitions, kinematic turning points)
- Two-stage training paradigm with unified discrete token vocabulary
- Stage 1: World model predicts structured frames (using Emu3 tokenizer, VQ)
- Stage 2: Maps structured foresight into low-level actions (using FAST tokenizer for actions)
- Unified token space for vision, language, action

3. **Experiments**: 
- SimplerEnv-WidowX benchmark
- LIBERO benchmark (Spatial, Object, Goal, Long suites)
- Real-world Franka robot arm deployment
- Compared with many baselines (OpenVLA, SpatialVLA, VideoVLA, UniVLA, FlowVLA, DreamVLA, etc.)

4. **Resources/compute**: Not explicitly mentioned - I need to note this

5. **Number of experiments**: 
- Multiple benchmarks (3 main)
- Real-world with generalization tests
- Ablations (history context, training efficiency)
- Qualitative analyses (attention maps, OOD predictions)

6. **Conclusions**: 75.0% on SimplerEnv-WidowX, 94.8% on LIBERO, strong real-world generalization

7. **Strengths**: 
- Novel sparse structured planning approach
- Physically grounded kinematic cues
- Two-stage training with unified token space
- Strong empirical results across multiple benchmarks
- Real-world validation

8. **Limitations**: 
- Limited experimental scale due to computational constraints
- Need larger multi-domain evaluation
- Could explore online RL
- Acknowledged in paper

Let me write this up in Chinese.</think>

# StructVLA 论文总结：超越密集未来——将世界模型作为结构化规划器用于机器人操纵

## 1. 核心问题与研究动机

- **研究背景**：近年来，将生成式世界模型集成到视觉-语言-动作（VLA）架构中已成为长视距机器人操纵的重要范式，通过预测性视觉前瞻（visual foresight）为策略提供超出瞬时感知的时空上下文。
- **现存两类方案的缺陷**：
  - **密集未来预测**（如连续像素/潜在空间 rollout）：存在大量视觉冗余，且随着时间步累积误差，在长视距任务中容易产生"规划漂移（plan drift）"。
  - **稀疏规划**（高层语义子目标或隐式潜在状态）：虽然压缩了预测范围，但缺乏显式的运动学（kinematic）约束，难以与底层执行精确对齐。
- **核心矛盾**：现有方法在"密集 vs 稀疏"两个极端之间摇摆，缺少一种兼具**物理可解释性**与**控制有效性**的中间层视觉子目标表达。

## 2. 方法论

### 2.1 核心思想
- 将生成式世界模型重构为**显式结构化规划器（structured planner）**，预测**稀疏、物理上有意义的"结构化帧"（structured frames）**作为中间层视觉子目标。
- 结构化帧源自机器人本体的**内禀运动学线索**，包括：
  - **抓取器状态转换**（gripper state transitions）：反映接触状态变化；
  - **运动学转折点**（kinematic turning points）：反映运动模式的切换。

### 2.2 自动化数据筛选流程（Physics-Grounded Data Curation）
- **候选帧提取**：
  - 计算末端执行器运动幅度的自适应阈值 ∥vₜ∥，结合 EMA 平滑；
  - 在抓取器翻转时间 t_c 后增加稳定窗口 δ_settle，选择恢复主运动前的最后一个准静态观测；
  - 对滑动窗口内平滑速度始终低于 τ_low 的时刻作为转折点候选。
- **时间覆盖与填充**：引入最小时间间隔约束，避免冗余；对长低速段，使用动作命令 L2 变化量最小的帧进行补样。
- **离线 VLM 过滤**：仅在数据构建阶段使用 GPT-5.2 对候选帧做任务相关性与冗余性筛选；训练时仅使用精选数据，推理时不依赖任何 VLM。

### 2.3 两阶段训练范式（统一离散词表）
- **统一离散词表**：使用 Emu3 VQ 编码器（空间压缩 8×）将图像与语言离散化；使用 FAST tokenizer（1024 词表）将动作离散化，并映射到语言词表末尾的 1024 个 ID，实现视觉/语言/动作的统一。
- **Stage 1 — 结构化规划器（视觉前瞻）**：
  - 给定指令 l 与视觉上下文 O_t，自回归预测下一结构化帧 s；
  - 损失函数仅作用于视觉 token：
  
  $$\mathcal{L}_{\text{planner}} = -\sum_{k=1}^{K} \log P_\theta(z_k | z_{<k}, T_l, T_{O_t})$$

  - 采用 LoRA（rank=32）参数高效微调，保留预训练先验；并通过滑动窗口目标时间步增强监督密度。
- **Stage 2 — 动作策略（Plan-to-Act 迁移）**：
  - 输入由语言指令 + 交错（视觉, 动作）token 构成；
  - 仅对动作 token 计算交叉熵：
  
  $$\mathcal{L}_{\text{act}} = -\sum_{m=1}^{M} \log P_\theta(a_m | a_{<m}, T_l, H_t)$$

  - 在统一词表内将规划器直接转化为可执行动作策略。

### 2.4 关键技术细节
- 模型规模：**8.5B 参数**纯自回归 Transformer，初始化自 UniVLA 的世界模型；
- 不同场景的视觉设置：
  - SimplerEnv：单视图 256×256；
  - LIBERO：Stage 1 使用第三人称 200×200，Stage 2 额外加入腕视图 200×200；
  - 真实环境：Stage 1 使用前置 256×144，Stage 2 加入腕视图 240×135；
- 不同阶段的训练配置（批大小 / 步数）：
  - 结构化规划器：SimplerEnv 30K（bs=32）/ LIBERO 10K（bs=32）/ 真实 2K（bs=32）；
  - 动作策略：SimplerEnv 20K（bs=128）/ LIBERO 4K（bs=192）/ 真实 2K（bs=32）。

## 3. 实验设计

### 3.1 仿真基准
- **SimplerEnv-WidowX**：评估从 BridgeData V2 训练的策略在光照、纹理、相机视角扰动下的迁移泛化能力；
- **LIBERO**：Franka 仿真臂四套任务集（Spatial / Object / Goal / Long），每套 10 个任务×50 条专家演示，联合训练统一模型。

### 3.2 真实世界部署
- 硬件：**Franka 机械臂** + 前置/腕部相机；
- 任务设置：
  - 4 个基础 pick-and-place 任务（黄碗、饼干盒、玩具、茄子），共 1152 条轨迹（每任务 288 条）；
  - 1 个长视距 "Tidy Up" 任务，648 条轨迹；
- 评估维度：基础成功率、零样本 OOD 泛化（未见颜色与几何形状）、动态人为干预下的鲁棒性。

### 3.3 对比方法
- 主流 VLA 基线：RT-1-X、Octo-Base/Small、OpenVLA、RoboVLMs、SpatialVLA、VideoVLA、mimic-video、UniVLA、π0-FAST、FlowVLA、DreamVLA、CoT-VLA、Diffusion Policy 等；
- 真实世界重点对比 UniVLA 与 SpatialVLA；
- 任务规划相关工作：Track2Act、LDP、ATM、ForeAct、VISTA、BagelVLA、LatentPilot 等。

## 4. 资源与算力
- **论文未明确披露**具体使用的 GPU 型号、数量与训练总时长；
- 仅给出与训练相关的批大小、训练步数、LoRA rank 等超参；并承认"实验规模受限于计算资源"（见 Limitations）。
- 推断使用大规模 GPU 集群（8.5B 参数 Transformer + 多数据集训练），但具体规模未公开。

## 5. 实验数量与充分性

### 5.1 实验覆盖范围
- **仿真基准**：3 个（SimplerEnv + LIBERO 四子套件 + 真实世界）；
- **真实世界任务**：4 个基础 + 1 个长视距；
- **消融与分析**：
  - 训练效率对比（Tab.3，与 RoboVLMs、UniVLA 比较达到峰值性能所需步数）；
  - 历史上下文长度消融（Tab.4，H=2/3/4 对比 StructVLA vs UniVLA）；
  - 抓取成功率 vs 任务成功率分解（Fig.6）；
  - 注意力图可视化分析（Fig.4a）；
  - OOD 场景泛化预测（Fig.4b）；
  - 真实世界零样本泛化与干预鲁棒性（Fig.7）。

### 5.2 充分性与公平性评价
- 优点：基准多样（仿真+真实）、对比方法覆盖面广（涵盖稠密/稀疏/隐式潜在等不同流派）；
- 局限：每个真实任务仅 10 次试验，统计置信度受限；未与最新的扩散式 VLA（如 GR-1、3D-VLA 等）充分比较；消融主要集中于历史长度与训练步数，未对结构化帧定义本身（运动学线索 vs 语义子目标）做完整对照实验。

## 6. 主要结论与发现

- **仿真结果**：
  - SimplerEnv-WidowX 平均成功率 **75.0%**（超过此前最佳 UniVLA 69.8%）；
  - LIBERO 平均成功率 **94.8%**（超过 DreamVLA 92.6%、UniVLA 93.7%），其中 LIBERO-Long 达 92.2%。
- **真实世界结果**：
  - 基础 pick-and-place 平均成功率 87.5%，比 UniVLA 高 20.0%；
  - 长视距 Tidy Up：StructVLA 8/10 vs UniVLA 4/10 vs SpatialVLA 2/10；
  - OOD 泛化（未见物体）：80.0% vs UniVLA 30.0%；
  - 干预鲁棒性：80.0% vs UniVLA 40.0%。
- **核心发现**：
  - 结构化帧监督显著提升长视距稳定性，减少误差累积；
  - 抓取-任务转化率高于基线，表明规划阶段改进带来执行阶段一致性提升；
  - 注意力图显示模型更聚焦于抓取器-物体接触区域，验证运动学锚点的有效性；
  - 训练效率优于 RoboVLMs 与 UniVLA（更少步数达峰）；
  - 历史上下文更长时性能单调上升（70.8%→75.0%），与 UniVLA 相反，验证规划对长期时序信息的有效利用。

## 7. 优点与亮点

- **方法层面**：
  - 提出介于"密集像素 rollout"与"语义子目标"之间的**第三种稀疏规划表示**，并赋予其显式运动学意义；
  - 设计了**自动化、可扩展**的结构化帧筛选管线，无需昂贵的人工标注；
  - 两阶段 + 统一离散词表，使规划与控制在同一生成式框架内无缝衔接；
  - 利用 LoRA 实现参数高效适配，保留预训练世界模型的视觉动态先验。
- **实验层面**：
  - 同时覆盖 SimplerEnv、LIBERO、真实 Franka 三类环境；
  - 包含 OOD 泛化、动态干预、抓取-任务分解等多维度分析；
  - 提供注意力图与 OOD 预测可视化，增强可解释性。

## 8. 不足与局限

- **实验规模受限**：作者明确指出受计算资源约束，未在更大规模、跨域数据集上验证泛化性；
- **真实世界样本量小**：每任务 10 次试验的统计置信度有限；
- **运动学线索的依赖性**：当前结构化帧定义依赖末端执行器速度与抓取器信号，对非标准末端或软体操作器的迁移性未评估；
- **离线 VLM 依赖**：数据筛选阶段使用 GPT-5.2，可能引入筛选偏差与外部模型成本；
- **基线覆盖不完全**：与一些最新的扩散/3D VLA（如 GR-1、3D-VLA、CogACT 等）的对比有限；
- **理论分析缺失**：缺乏对结构化帧数量、密度与下游策略性能之间关系的系统消融；
- **未来方向**：作者建议引入在线强化学习以进一步提升真实部署鲁棒性。

（完）
