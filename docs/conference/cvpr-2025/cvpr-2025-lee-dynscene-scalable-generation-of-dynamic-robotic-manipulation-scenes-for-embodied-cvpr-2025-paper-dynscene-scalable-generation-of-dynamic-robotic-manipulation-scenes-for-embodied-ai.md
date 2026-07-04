---
title: "DynScene: Scalable Generation of Dynamic Robotic Manipulation Scenes for Embodied AI"
title_zh: "DynScene:面向具身 AI 的大规模动态机器人操控场景生成"
authors: "Lee, Sangmin, Park, Sungyong, Kim, Heewon"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Lee_DynScene_Scalable_Generation_of_Dynamic_Robotic_Manipulation_Scenes_for_Embodied_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向具身 AI 基准的大规模动态机器人操控场景生成
tldr: "具身智能中的机器人操控研究高度依赖大规模、高质量且能反映真实物理动态的数据集,但现有数据采集流程成本高、效率低。本文提出 DynScene,一种基于扩散模型的框架,可以从文本指令直接生成动态机器人操控场景。该方法将生成过程解耦为静态场景合成与动作轨迹生成两个阶段,从而实现细粒度控制与多样化输出。通过引入场景精炼与物理可行性约束,所生成数据在结构多样性与物理合理性方面均有所提升。该工作为复杂操控任务下模仿学习与策略评估提供了可扩展的数据生成工具。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1793, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1812, \"height\": 589, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1806, \"height\": 859, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1786, \"height\": 805, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 392, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 799, \"height\": 471, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1804, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lee-dynscene-scalable-generation-of-dynamic-robotic-manipulation-scenes-for-embodied-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 872, \"height\": 162, \"label\": \"Table\"}]"
motivation: "现有机器人操控数据采集成本高、效率低,难以满足大规模具身智能研究需求。"
method: "提出基于扩散模型的 DynScene,将生成过程分解为静态场景合成与动作轨迹生成两阶段,并加入物理可行性约束。"
result: 所生成场景在结构多样性、动作物理合理性与可控性方面均优于已有方法。
conclusion: 为复杂操控基准下模仿学习与策略评估提供了可扩展的合成数据生成方案。
---

## Abstract
Robotic manipulation in embodied AI critically depends on large-scale, high-quality datasets that reflect realistic object interactions and physical dynamics. However, existing data collection pipelines are often slow, expensive, and heavily reliant on manual efforts. We present DynScene, a diffusion-based framework for generating dynamic robotic manipulation scenes directly from textual instructions. Unlike prior methods that focus solely on static environments or isolated robot actions, DynScene decomposes the generation into two phases static scene synthesis and action trajectory generation allowing fine-grained control and diversity. Our model enhances realism and physical feasibility through scene refinement (layout sampling, quaternion quantization) and leverages residual action representation to enable action augmentation, generating multiple diverse trajectories from a single static configuration. Experiments show DynScene achieves 26.8x faster generation, 1.84x higher accuracy, and 28% greater action diversity than human-crafted data. Furthermore, agents trained with DynScene exhibit up to 19.4% higher success rates across complex manipulation tasks. Our approach paves the way for scalable, automated dataset generation in robot learning.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "DynScene: Scalable Generation of Dynamic Robotic Manipulation Scenes for Embodied AI" based on the provided content. I need to organize it according to the 8 specified points using Markdown formatting with hierarchical headings and bullet points. Let me carefully extract information from the paper.

Key information from the paper:
- Title: DynScene - diffusion-based framework for generating dynamic robotic manipulation scenes from text
- Authors: Sangmin Lee, Sungyong Park, Heewon Kim from Soongsil University
- Conference: CVPR 2025
- Core problem: Data collection for robotic manipulation is slow, expensive, manual
- Method: Two-phase diffusion - static scene synthesis + action trajectory generation
- Key techniques: layout sampling, quaternion quantization, residual action representation, action augmentation
- Dataset: ARNOLD benchmark (8 tasks, 3571 training, 773 test)
- Metrics: FD, DTW, SC for diversity; SR for success rate
- Results: 26.8× faster, 1.84× higher accuracy, 28% more diverse actions, up to 19.4% higher SR for agents
- GPUs: RTX4090 for DynScene training, A6000 for agent training
- Training: 100K epochs for DynScene, 200K steps for agents
- Limitations: Only evaluated on ARNOLD, generalization to OOD states is challenging

Let me write a comprehensive summary following the 8 required points.</think>

# DynScene 论文详细总结

## 1. 核心问题与研究动机

- **领域背景**：具身 AI（Embodied AI）中的机器人操控任务高度依赖大规模、高质量的数据集，数据需反映真实物体交互与物理动态。
- **现有瓶颈**：
  - 真实数据采集成本高、耗时长、依赖人工，且对试错式学习存在安全风险。
  - 仿真平台（AI2-THOR、Habitat 2.0、Isaac Sim）和操控数据集（RLBench、ALFRED、ARNOLD）虽缓解了部分问题，但规模化构建依然困难。
- **已有方法的局限**：
  - 静态场景生成（如 DiffuScene、PhyScene）和机器人动作生成（如 SynthER、MTDIFF）两条研究路径**相互独立**，无法保证场景布局与机器人动作在物理层面的协同一致性。
  - 静态场景中常出现不合理的物体放置（碰撞、不可达）或姿态（重力倾倒），导致动作执行失败。
- **研究意义**：首次提出联合生成静态场景与机器人动作的"动态场景"概念，填补了物理一致性数据合成的空白。

## 2. 方法论：核心思想与技术细节

### 2.1 整体框架（两阶段扩散生成）

- **输入**：自然语言指令 y（如"将抽屉关上 50%"）。
- **输出**：动态场景 (s, a)，其中 s 为静态场景，a 为动作序列。
- **阶段一**：条件扩散模型生成静态场景数据 s。
- **阶段二**：另一条件扩散模型以静态场景 s 为条件生成动作序列 a。
- **后处理**：在 Isaac Sim 仿真器中验证生成结果，仅保留成功样本用于训练。

### 2.2 数据表示

- **静态场景 s**（绝对坐标）：
  - 目标物体 o：位置 pobj、四元数 qobj、类别 c、尺寸 v、形状编码 f（32 维点云嵌入）、初始状态 sinit、目标状态 sgoal。
  - 机器人 r：基座位置 pbase 与姿态 qbase、末端执行器初始位置 pee0 与姿态 qee0、夹爪状态 g0。
  - 房间布局 z：干扰物与结构元素。
- **动作 a**（**残差坐标**）：第 k 步动作 ak = [Δpeek, Δqeek, gk]，其中 Δpeek = peek − peek−1，Δqeek = qeek − qeek−1。
  - 残差表示使动作学习与具体静态场景解耦，便于跨场景泛化和动作增广。

### 2.3 静态场景生成与精炼

- **条件扩散过程**：前向加噪 q(st|s0) = N(st; √ᾱt·s0, (1−ᾱt)I)；反向去噪 pθ(st−1|st, y) 借助 U-Net [35] 和预训练语言模型 BERT [11] 进行条件生成。
- **损失函数**：L(θ)text = E[‖ε − εθ(st, t; y)‖²]。
- **布局采样（Layout Sampling）**：
  - 从候选布局数据集中选取与扩散预测位姿最接近的布局 ẑ = zr̂，其中 r̂ = arg minr(‖pobjr − p̃obj‖² + ‖pbaser − p̃base‖²)。
  - 解决机器人物理碰撞或目标不可达问题。
- **四元数量化（Quaternion Quantization）**：
  - 公式：q̂obj = round(q̃obj / δ) · δ，以固定间隔 δ 对物体姿态进行离散化。
  - 防止微小姿态误差导致铰接物体（柜门、抽屉）因重力倾倒。

### 2.4 动作生成与增广

- **条件扩散过程**：以静态场景 s 为条件生成动作 a0，反向过程 pφ(at−1|at, s)，损失 L(φ)scene。
- **动作增广机制**：
  - 静态场景与动作解耦后，可对 N 个静态场景各生成 M 个动作，形成 N×M 的多样化数据集。
  - 可在已见状态间插值（如 10cm 场景中学到的动作可用于生成 20cm、30cm 的动作）。
- **无效场景过滤**：使用 Isaac Sim [20] 按 ARNOLD [7] 的成功阈值验证，仅保留成功样本。

### 2.5 阶段感知智能体训练（PerAct-PSA）

- 基于 PerAct [31]，将抓取阶段与操控阶段使用**独立网络**训练，使各网络专注于特定阶段特征。

## 3. 实验设计

### 3.1 数据集与基准

- **ARNOLD 基准** [7]：
  - 8 项操控任务（拾取物体、调整姿态、开关柜门、开关抽屉、倒水、转移水等）。
  - 3,571 训练样本 + 773 测试样本。
  - 支持**连续状态**变化（如"打开抽屉 75%"），区别于离散状态基准。

### 3.2 评价指标

- **多样性指标**：Fréchet Distance（FD）、Dynamic Time Warping（DTW）、Spatial Coverage（SC）。
- **成功率（SR）**：动态场景生成阶段每个任务取 100 次试验的平均；智能体阶段取 3 次试验的平均。

### 3.3 对比方法

- **人类专家数据**（ARNOLD 原始数据，使用 Xbox 手柄采集）。
- **DiffuScene** [35]：专门的静态场景生成扩散模型，配以 ARNOLD 动作数据。
- **SynthER** [18]、**MTDIFF** [8]：仅生成机器人动作。
- **ROSIE** [45]、**GenAug** [3]：基于文本引导图像合成增强静态场景。
- **PhyScene** [43]：物理交互感知的静态场景生成。

### 3.4 智能体对比

- BC-Lang-CNN、BC-Lang-ViT、PerAct、PerAct-PSA，分别在仅 ARNOLD 数据和 ARNOLD+DynScene 数据上训练。

## 4. 资源与算力

- **DynScene 训练**：NVIDIA **RTX 4090** GPU；每任务 100,000 个 epoch；Adam 优化器，学习率 2e-4。
- **智能体训练**：NVIDIA **A6000** GPU；200,000 训练步，batch size = 4；LAMB 优化器，学习率 1e-4。
- 论文致谢中提到 **Corca AI 赞助了部分算力**。
- 国家层面资助：MSIT 韩国国家 SW 卓越计划、NRF 基金项目等。

## 5. 实验数量与充分性

- **实验数量**：
  - 8 个操控任务的逐项多样性对比（Table 2，含 3 个指标）。
  - 任务级生成时间与成功率对比（Table 3，8 任务）。
  - 与 DiffuScene 的静态场景对比（Table 4）。
  - 智能体训练对比（Table 5，4 种方法 × 8 任务 × 2 数据条件）。
  - 目标状态估计精度（Table 6，4 类文本指令）。
  - 泛化能力测试（Table 7，新物体/新场景/新状态）。
  - 动作多样性可视化分析（Figure 4，3 个坐标轴）。
  - 文本条件生成定性展示（Figure 5，3 类任务）。
- **公平性考量**：
  - 在相同数量的有效动态场景下与 ARNOLD 进行公平对比。
  - 使用 ARNOLD 官方阈值过滤生成场景。
  - 同时报告无条件与文本条件两种设置。
- **消融与超参研究**：论文本身**未提供完整的消融实验**（如各模块的独立贡献），仅在框架中描述了每个组件的功能；这一点在充分性上略有不足。

## 6. 主要结论与发现

- **生成效率**：DynScene 平均生成时间 2.52 秒/场景，比人类专家的 67.50 秒/场景**快 26.8 倍**。
- **生成质量**：平均成功率 69.50%，超过人类专家的 37.50%（**1.84 倍**）。
- **动作多样性**：FD 30.32 vs 28.39、DTW 55.25 vs 47.58、SC 3.62 vs 2.83，**平均提升 28%**。
- **物理一致性**：相比 DiffuScene，速度快 10 倍，成功率高 3.5 倍（69.50% vs 20.04%）。
- **智能体性能提升**：
  - PerAct 平均成功率从 29.14% → 34.79%（+5.65%）。
  - PerAct-PSA 从 41.46% → 45.62%（+4.16%）。
  - 在复杂任务（如 open cabinet、transfer water）上提升尤为显著，最高**提升 19.4%**。
- **数值指令遵循**：能精确生成指定目标状态（如 9.99cm、179.94°、80.09%）。
- **泛化能力**：在新物体、新场景、any state 条件下均优于基线，但在 novel state（分布外）上略有下降。

## 7. 优点与亮点

- **方法创新性**：
  - 首次将静态场景生成与机器人动作生成在扩散框架下**统一**，保证物理一致性。
  - 残差动作表示实现了场景-动作解耦，是**支持动作增广**的关键设计。
- **物理可行性保障**：布局采样解决碰撞/不可达问题，四元数量化解决铰接物体倾倒问题，仿真器验证保证数据质量。
- **显著的实际效益**：数量级地提升数据生成效率（26.8×），大幅缓解人工采集瓶颈。
- **文本可控性强**：支持连续数值指令（如"50%"、"10cm"），并能精确生成对应目标状态。
- **对训练下游智能体具有直接价值**：在多个基线和任务上稳定提升成功率。
- **工程贡献完整**：代码、数据、训练流程公开可复现，并提供了阶段感知训练变体 PerAct-PSA。

## 8. 不足与局限

- **数据集单一**：仅在 ARNOLD 基准上评估，未在 RLBench、Habitat、Behavior-1K 等其他基准验证，**泛化到其他领域仍是开放问题**。
- **分布外状态能力不足**：Table 7 显示 novel state（如训练时 25-75%，测试时 100%）成功率下降，作者明确指出这是未来工作方向。
- **消融实验不足**：缺少对布局采样、四元数量化、残差表示、动作增广等模块的**独立消融研究**，各组件贡献难以量化。
- **任务覆盖有限**：仅涉及 8 种操控任务，未涵盖可形变物体操控、移动操作、长时序任务等更复杂场景。
- **物理现实性局限**：依赖 Isaac Sim 仿真验证，仿真与真实世界之间的"sim-to-real"差距未被讨论；动作多样性受限于残差表示的局部性。
- **动作多样性分析粒度**：仅对"pour water"任务做了详细的 3D 坐标分布可视化（Figure 4），其他任务仅给出标量指标，缺乏深入分析。
- **公平性边界**：Table 3 中"人类专家"数据来自 ARNOLD 原数据集，操作员使用 Xbox 手柄；与完全真实世界操控数据可能仍有差异，文中未做跨采集方式比较。
- **计算成本未充分披露**：仅给出 GPU 型号与训练步数，**未报告具体训练总时长、显存占用、单次推理延迟等更细粒度指标**。

（完）
