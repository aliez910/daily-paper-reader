---
title: "ManiLong-Shot: Interaction-Aware One-Shot Imitation Learning for Long-Horizon Manipulation"
title_zh: ManiLong-Shot：面向长时域操作任务的交互感知单次模仿学习
authors: "Zixuan Chen, Chongkai Gao, Lin Shao, Jieqi Shi, Jing Huo, Yang Gao"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38881/42843"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向长时域操作的单次模仿学习
tldr: 当前单次模仿学习方法主要局限于短时域任务，难以应用于复杂长时域操作。本文提出ManiLong-Shot框架，通过将长时域任务分解为基于物理交互事件的原语序列，利用视觉语言模型进行高层推理或规则启发式驱动，实现从单一演示中学习复杂操作。实验证明在长时域操作任务上显著优于现有方法，为单次模仿学习在复杂场景的应用提供了有效途径。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 489, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1839, \"height\": 1041, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 880, \"height\": 244, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 774, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38881/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 611, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38881/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1657, \"height\": 588, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38881/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1792, \"height\": 285, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38881/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 621, \"height\": 296, \"label\": \"Table\"}]"
motivation: 解决现有单次模仿学习无法应用于长时域复杂操作任务的问题。
method: 将长时域任务分解为交互感知原语序列，通过VLM或规则驱动。
result: 在长时域操作任务上表现优异，超越现有方法。
conclusion: 提出了一种有效的长时域单次模仿学习框架。
---

## Abstract
One-shot imitation learning (OSIL) offers a promising way to teach robots new skills without large-scale data collection. However, current OSIL methods are primarily limited to short-horizon tasks, thus limiting their applicability to complex, long-horizon manipulations. To address this limitation, we propose ManiLong-Shot, a novel framework that enables effective OSIL for long-horizon prehensile manipulation tasks. ManiLong-Shot structures long-horizon tasks around physical interaction events, reframing the problem as sequencing interaction-aware primitives instead of directly imitating continuous trajectories. This primitive decomposition can be driven by high-level reasoning from a vision-language model (VLM) or by rule-based heuristics derived from robot state changes. For each primitive, ManiLong-Shot predicts invariant regions critical to the interaction, establishes correspondences between the demonstration and the current observation, and computes the target end-effector pose, enabling effective task execution. Extensive simulation experiments show that ManiLong-Shot, trained on only 10 short-horizon tasks, generalizes to 20 unseen long-horizon tasks across three difficulty levels via one-shot imitation, achieving a 22.8% relative improvement over the SOTA. Additionally, real-robot experiments validate ManiLong-Shot’s ability to robustly execute three long-horizon manipulation tasks via OSIL, confirming its practical applicability.

---

## 论文详细总结（自动生成）

## 论文的核心问题与整体含义（研究动机和背景）

论文聚焦于机器人单次模仿学习（One-Shot Imitation Learning，OSIL）的一项核心挑战：现有方法大多局限于短时域操作任务（如简单的抓取、放置），难以推广到包含多个子任务、多种物体交互的长时域操作场景（如摆桌子、整理厨房）。尽管 OSIL 在数据效率和快速适应新任务方面有巨大潜力，但当前技术在面对需要多步协调、长时间序列的任务时表现不佳。为此，作者提出 **ManiLong-Shot** 框架，通过将长时域任务划分为基于物理交互事件的原语序列，并利用交互感知的不变区域预测与匹配，实现从单次演示到未曾见过的复杂长时域任务的有效泛化。

## 论文提出的方法论

### 核心思想
ManiLong-Shot 的核心是将长时域操作任务分解为一系列**交互感知原语**，每个原语对应机器人末端执行器与环境之间的一个物理交互阶段：预接触（pre‑contact）、抓取（grasping）和接触后（post‑contact）。模仿学习不再直接拟合连续轨迹，而是通过识别每个原语中功能不变的关键区域（invariant region），在演示和当前场景之间建立对应关系，从而估计目标末端位姿，实现稳健的原语级执行。

### 主要技术模块
1. **交互感知任务分解（Interaction‑aware Task Decomposition）**  
   - 支持两种分解方式：
     - **规则驱动**：基于关节速度与夹爪状态（开/闭）自动识别阶段边界。
     - **VLM 驱动**：利用 GPT‑4o 等视觉语言模型，通过结构化提示（demonstration steps + 物理交互描述）进行语义分解。
   - 两种方式可互换，规则驱动更稳定，VLM 驱动更具灵活性。

2. **交互感知区域预测网络（Interaction‑aware Region Prediction Network）**  
   - 仅在短时域任务（SH）上训练，充分利用数据效率。  
   - 使用 Point Cloud Transformer V3（PTV3）处理 RGB‑D 点云，通过跨场景和场景内的注意力机制提取特征。  
   - 针对预接触/抓取与接触后阶段分别训练：预接触/抓取阶段共享网络，接触后阶段额外使用定位网络（Positioning Network）来精确对齐目标区域。  
   - 输出一个概率图，指示每个点属于不变区域的概率，从而得到预测的区域点云。

3. **交互感知区域匹配网络（Interaction‑aware Region Matching Network）**  
   - 在测试时，从演示中提取预测的不变区域，与当前场景的点云进行匹配。  
   - 采用双重 softmax（DualSoftmax）算法计算对应矩阵，然后通过 SE(3) 优化求解目标末端位姿。  
   - 位姿计算完成后，使用 RRT‑Connect 运动规划器执行，迭代进行直至任务完成。

### 整体流程
- 训练阶段：仅使用 10 个短时域任务的离线演示数据（共 100 条轨迹），训练区域预测网络和区域匹配网络。
- 测试阶段：对于未见过的长时域任务，提供一条单次成功演示 → 通过任务分解提取原语 → 对每个原语预测不变区域 → 在执行时使用匹配网络对齐当前观测 → 估计位姿并规划运动 → 重复直到任务结束。

## 实验设计

### 数据集与 Benchmark
- **RLBench‑Oneshot**：从 RLBench 中精选 30 个任务构建的专用 benchmark。
  - **短时域（SH）任务**：10 个，每个包含 100 条成功演示（来自前、左右肩、手腕摄像头）。
  - **长时域（LH）任务**：20 个，按交互次数分为三个难度级别：
    - Level 1：6 次物理交互（13 个任务）
    - Level 2：9 次物理交互（4 个任务）
    - Level 3：12 次物理交互（3 个任务）
- 每个 LH 任务仅提供一条成功演示作为单次学习输入。

### 对比方法
- 短时域任务对比：**RVT2**, **3DDA**, **ARP**, **IMOP**（均为 SOTA 方法）。
- 长时域任务对比：以上方法的微调版本（+FT，使用 5 条演示微调）以及 IMOP 作为 OSIL 基线。

### 评价指标
- 平均成功率（Average Success Rate）与平均排名（Average Rank）。
- 每个任务在 5 个随机种子下各运行 25 次（共 125 次评估），取平均值和标准差。

### 真实机器人实验
- 使用 UFactory xArm7 机器人，RealSense D435 和 D415 摄像头，MoveIt 进行运动规划。
- 设置 3 个长时域操作任务：Stack Blocks、Stack Cups、Place Cups，每个任务进行 5 次 OSIL 测试（物体位置稍有扰动）。

## 资源与算力
论文正文中**未明确提及**训练所使用的 GPU 型号、数量及训练时长。实验部分仅说明运行环境为模拟器与真实机器人，未提供硬件加速细节。

## 实验数量与充分性

- **短时域训练任务**：10 个，每个 100 条轨迹，共 1000 条演示数据。
- **长时域评估**：20 个场景 × 5 种子 × 25 次 = 2500 次评估（原文表述为 5 随机种子各 25 次，因此每个任务 125 次，但表 2 中每个任务的平均值和标准差基于 25 trials with 5 random seeds，即 25 次？可能存在歧义，但整体样本量足够）。
- **消融实验**：
  - 比较 VLM 驱动与规则驱动的任务分解效果。
  - 比较是否使用接触后阶段的定位网络。
- **真实实验**：3 个任务 × 5 次 OSIL 测试。

实验设计较为全面，覆盖了从训练到测试、从模拟到真实、从全量比较到部件消融的不同角度。评估指标采用多次重复的平均值与方差，保证了结果的统计意义。对比方法包括了当前最强的多任务策略和 OSIL 基线，且长时域任务对基线进行了 5 次演示的微调，条件对基线更有利，但仍不如 ManiLong‑Shot，说明比较公平。

## 论文的主要结论与发现

- **短时域任务**：ManiLong‑Shot 在 10 个训练 SH 任务上达到 90.4% 的平均成功率，比最佳基线 3DDA（85.0%）提升 3.8%，并在 6/10 个任务中取得最高分。
- **长时域任务（OSIL）**：在 20 个未见过的 LH 任务上，ManiLong‑Shot 以 30.2% 的平均成功率大幅超越 IMOP（7.4%），**绝对提升 22.8 个百分点**，且在所有难度级别均显著优于基线。某些复杂任务（如 Stack Blocks、Block Pyramid）上，基线成功率几乎为零，而 ManiLong‑Shot 仍可获得有限但非零的成功率。
- **真实机器人**：通过 sim‑to‑real 迁移，ManiLong‑Shot 在三个真实 LH 任务上平均成功率达 60.0%，比 IMOP 的 33.3% 提升 26.7%。
- **消融实验**：规则驱动分解优于 VLM 驱动，且接触后阶段的定位网络对性能至关重要（去除后成功率下降较多）。

这些结果验证了：**交互感知的任务分解 + 不变区域预测与匹配**能够有效将短时域训练的知识泛化到长时域 OSIL 场景中。

## 优点

- **新颖的问题视角**：将 OSIL 从短时域扩展到长时域，并基于物理交互事件进行原语级分解，降低了长序列模仿的难度。
- **数据高效**：只利用 10 个短时域任务的演示进行训练，即可泛化到 20 个长时域任务，不需要为每个新任务重新训练。
- **模块化设计**：分解、区域预测、匹配三模块可独立改进或替换（如 VLM vs 规则），便于未来扩展。
- **双重分解策略**：同时提供规则驱动和 VLM 驱动两种分解方法，兼顾稳定性与语义灵活性。
- **从模拟到真实的迁移能力**：真实实验验证了方法在实际环境中的可行性。
- **实验全面性**：在精心设计的 benchmark（RLBench‑Oneshot）上进行大量统计测试，对比多种 SOTA 方法，并附带消融和真实实验。

## 不足与局限

- **任务范围有限**：论文核心假设是操作可分解为 pre‑contact, grasping, post‑contact 三个离散阶段。这主要适用于**prehensile（夹持）操作**，对于需要持续接触的工具使用（如擦拭、倾倒、搅拌）或非夹持式操作（如推动、滑动）不适用。
- **长时域成功率仍较低**：尽管 30.2% 远超基线，但绝对数字不高，说明长时域 OSIL 仍然困难，尤其是在高难度级别（Level 3 成功率约 6%‑11%）。
- **VLM 驱动的不稳定性**：VLM 分解在当前模型下不如规则驱动可靠，且需要额外提示工程；VLM 的推理延迟和成本也未讨论。
- **对仿真环境的依赖**：区域预测网络的训练使用了仿真中的 ground truth 实例分割掩码，在真实环境下需要额外处理（论文中使用 sim‑to‑real，但训练仍基于仿真，实际部署时可能需要域适应）。
- **实验未报告训练开销**：未公开 GPU 型号、训练时间、模型参数量等资源消耗信息，不利于复现与公平比较。
- **固定场景假设**：所有任务均为桌面环境，未验证更复杂场景（如移动操作、拥挤空间）。

（完）
