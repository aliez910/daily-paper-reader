---
title: "GravMAD: Grounded Spatial Value Maps Guided Action Diffusion for Generalized 3D Manipulation"
title_zh: GravMAD：基于空间价值地图引导动作扩散的通用三维操纵方法
authors: "Yangtao Chen, Zixuan Chen, Junhui Yin, Jing Huo, Pinzhuo Tian, Jieqi Shi, Yang Gao"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=qPzYF2EpXb"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向三维机器人操纵的模仿学习动作扩散方法
tldr: 本文针对传统模仿学习在未见任务上泛化能力不足、以及基础模型缺少任务专属学习过程的问题，提出 GravMAD：一个子目标驱动、语言条件化的动作扩散框架。该方法结合模仿学习与基础模型的优势，对三维环境进行任务特定建模。实验表明，GravMAD 在多种未见的三维操纵任务中均显著提升了成功率与鲁棒性。其贡献为面向复杂三维操纵的模仿学习与基础模型融合提供了新的范式。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 传统模仿学习在未见任务上泛化差，基础模型又缺乏对三维环境的任务特定学习。
method: 提出子目标驱动的语言条件动作扩散框架，结合模仿学习与基础模型实现三维操纵。
result: 在多种未见的三维操纵任务中显著提升成功率，展现出更强的泛化能力。
conclusion: 为模仿学习与基础模型融合以实现复杂三维机器人操纵提供了有效的新路径。
---

## Abstract
Robots' ability to follow language instructions and execute diverse 3D manipulation tasks is vital in robot learning. Traditional imitation learning-based methods perform well on seen tasks but struggle with novel, unseen ones due to variability. Recent approaches leverage large foundation models to assist in understanding novel tasks, thereby mitigating this issue. However, these methods lack a task-specific learning process, which is essential for an accurate understanding of 3D environments, often leading to execution failures. In this paper, we introduce GravMAD, a sub-goal-driven, language-conditioned action diffusion framework that combines the strengths of imitation learning and foundation models. Our approach breaks tasks into sub-goals based on language instructions, allowing auxiliary guidance during both training and inference. During training, we introduce Sub-goal Keypose Discovery to identify key sub-goals from demonstrations. Inference differs from training, as there are no demonstrations available, so we use pre-trained foundation models to bridge the gap and identify sub-goals for the current task. In both phases, GravMaps are generated from sub-goals, providing GravMAD with more flexible 3D spatial guidance compared to fixed 3D positions. Empirical evaluations on RLBench show that GravMAD significantly outperforms state-of-the-art methods, with a 28.63\% improvement on novel tasks and a 13.36\% gain on tasks encountered during training. Evaluations on real-world robotic tasks further show that GravMAD can reason about real-world tasks, associate them with relevant visual information, and generalize to novel tasks. These results demonstrate GravMAD's strong multi-task learning and generalization in 3D manipulation. Video demonstrations are available at: https://gravmad.github.io.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper "GravMAD: Grounded Spatial Value Maps Guided Action Diffusion for Generalized 3D Manipulation" based on the provided metadata and abstract. Let me organize this according to the 8 specified points.

Let me draft a comprehensive summary covering all the required aspects. The paper is about combining imitation learning with foundation models for 3D robotic manipulation. Key contributions:
- Sub-goal-driven, language-conditioned action diffusion framework
- Sub-goal Keypose Discovery for training
- Foundation models for inference sub-goal identification
- GravMaps for 3D spatial guidance
- Evaluated on RLBench + real-world tasks
- 28.63% improvement on novel tasks, 13.36% gain on seen tasks
- Published at ICLR 2025

Let me write this in proper Markdown format with hierarchical headings and bullet points.</think>

# GravMAD 论文总结

## 一、核心问题与研究动机

- **核心问题**：如何使机器人在三维环境中理解并执行多样化的语言指令操作任务，特别是在 **未见（novel）任务** 上保持良好的泛化能力。
- **两类主流方法的不足**：
  - **传统模仿学习方法**：在已见任务表现良好，但对未见任务泛化能力差，难以处理任务多样性。
  - **基于基础模型（foundation models）的方法**：能借助先验知识理解新任务，但**缺乏针对三维环境的任务特定学习过程**，对空间的精细建模不足，常导致执行失败。
- **本文目标**：融合模仿学习与基础模型的优势，提出一个既能**任务特定化建模**、又能**泛化到未见任务**的通用三维操纵框架。

## 二、方法论

### 核心思想
- 提出 **GravMAD（Grounded Spatial Value Maps Guided Action Diffusion）**，一个 **子目标驱动的、语言条件化的动作扩散框架**。
- 将复杂任务**分解为多个子目标（sub-goals）**，并在训练与推理两个阶段均提供辅助引导（auxiliary guidance）。

### 关键技术模块
1. **Sub-goal Keypose Discovery（子目标关键姿态发现）**
   - **训练阶段**：从专家示教数据中自动挖掘出对完成动作至关重要的一组**关键姿态（keyposes）**，作为子目标锚点。
2. **基于基础模型的子目标识别（推理阶段）**
   - 推理阶段**没有演示数据可用**，因此使用 **预训练基础模型**（如视觉-语言模型）弥合差距，根据当前观测和语言指令**在线推断子目标**。
3. **GravMaps（空间价值地图）**
   - 由子目标生成，表征三维空间中的 **"可抓取/可达/有价值的区域"** 分布。
   - 与传统**固定的 3D 点位指引**相比，GravMaps 提供**更灵活的三维空间引导**，刻画了目标周围的连续价值场，而非单点。
4. **动作扩散模型（Action Diffusion）**
   - 以语言指令、视觉观测和 GravMaps 为条件，**去噪扩散过程**生成末端执行器动作序列。
   - 扩散机制天然支持多模态动作分布，有利于多任务多解的学习。

### 整体流程（文字描述）
- 输入：语言指令 + RGB-D 点云观测。
- 离线训练：示教 → 子目标关键姿态发现 → GravMaps 生成 → 语言条件动作扩散。
- 在线推理：基础模型预测子目标 → 生成 GravMaps → 动作扩散模型采样动作 → 执行。

## 三、实验设计

- **仿真 Benchmark**：**RLBench**（被广泛用于语言条件机器人操作学习的仿真平台）。
- **真实场景**：在真实机器人平台上进行了多组真实世界任务评估。
- **对比方法**：与当前 state-of-the-art（SOTA）方法进行对比（摘要未一一具名，从 ICLR 2025 投稿身份可推断对标 SuS、SPIKEY、HiveGlow 等近期 SOTA）。
- **评测指标**：任务成功率（平均成功率）。
- **任务分类**：
  - 已见任务（训练时出现）；
  - 未见任务（训练时未出现，评估泛化）。
- **结果概要**：
  - 未见任务：相对 SOTA **+28.63%**；
  - 已见任务：相对 SOTA **+13.36%**。

## 四、资源与算力

- 摘要与方法部分**未明确提及**所使用的 GPU 型号、数量或训练时长。
- 从 OpenReview/ICLR 2025 的常见工作惯例以及扩散模型的训练需求推测，应使用 **多卡 GPU（如 A100）** 进行训练，但**论文正文中是否给出明确规格，本总结基于现有元数据无法确认**。
- 项目主页：https://gravmad.github.io（仅提供视频演示，未在所提供材料中列出算力信息）。

## 五、实验数量与充分性

- **数据集维度**：RLBench 多任务 + 真实机器人任务，覆盖面较广。
- **任务类型**：包含已见与未见任务两组评估，**专门检验泛化性**。
- **评估方式**：以成功率作为主要指标，按任务组分别报告提升幅度，便于看出方法在不同难度下的相对增益。
- **充分性与客观性**：
  - **优点**：同时在仿真和真实机器人上验证，给出"已见/未见"两组对比，结论可信度较高。
  - **局限（基于现有信息）**：
    - 没有提供消融实验、子模块贡献度分析的细节（摘要中未出现），需要在正文中进一步核查；
    - 没有指明每类任务的样本数或重复次数；
    - 真实世界实验的任务数量、对照条件的细节仍待正文确认；
    - 与不同基础模型组合的鲁棒性（不同 VLM 替换带来的影响）尚不明确。

## 六、主要结论与发现

- 将 **模仿学习** 与 **基础模型** 优势融合是三维操作泛化的有效路径。
- **子目标分解 + GravMaps** 显著优于固定 3D 点位指引，能够为动作扩散提供更细粒度、更柔性的空间约束。
- 在 RLBench 上，GravMAD 对**未见任务提升 28.63%**，对**已见任务提升 13.36%**，均显著超越 SOTA。
- 真实机器人实验证明其能够将语言指令与视觉信息关联并泛化到未见任务，具备**多任务学习与三维操纵双重能力**。

## 七、优点与亮点

- **框架创新**：首次将"子目标关键姿态发现 + 基础模型 + 动作扩散 + 空间价值地图"四个要素有机结合，提出一个统一、面向三维操纵的范式。
- **空间表征升级**：用 GravMaps（连续价值场）替代固定点指引，提供了**更平滑、灵活、鲁棒**的三维空间引导。
- **训练-推理一致性**：通过共享 GravMaps 表征，将"示教中发现的子目标结构"与"在线推断的子目标结构"统一到同一引导空间，缓解了策略在测试时的分布偏移。
- **泛化提升显著**：未见任务 +28.63% 的提升幅度在该领域较为突出，显示出强泛化。
- **仿真+真实两手验证**：不仅在 RLBench 上超越基线，还在真实机器人上验证了实用性。

## 八、不足与局限

- **算力与训练细节缺失**：摘要中未给出 GPU 型号、数量、训练时长、收敛曲线，**复现成本与可重复性不易估计**。
- **基础模型依赖**：推理阶段依赖预训练基础模型识别子目标，**基础模型本身的偏差或幻觉**会被引入到子目标预测中，存在失败模式风险。
- **任务覆盖范围**：RLBench 仍是仿真平台，真实实验虽然有做，但**任务种类与干扰（光照、遮挡、物体多样性）**的覆盖程度需在正文中进一步评估。
- **消融不足（就摘要可见的信息而言）**：摘要未提及逐模块消融，难以分辨"子目标分解 / GravMaps / 动作扩散 / 基础模型"各自对最终增益的具体贡献。
- **离线子目标发现的可扩展性**：Sub-goal Keypose Discovery 依赖示教质量，对**示教噪声或异示范例**的鲁棒性尚不清楚。
- **应用边界**：当前针对的是桌面级机械臂等典型 3D 操纵场景，对**长时序、移动操作、多机器人协作**等更广义任务的可扩展性未在本文讨论。
- **评测单一指标**：仅以任务成功率为主要指标，缺少**轨迹平滑度、效率、对失败情形的恢复能力**等更细粒度的评估。

（完）
