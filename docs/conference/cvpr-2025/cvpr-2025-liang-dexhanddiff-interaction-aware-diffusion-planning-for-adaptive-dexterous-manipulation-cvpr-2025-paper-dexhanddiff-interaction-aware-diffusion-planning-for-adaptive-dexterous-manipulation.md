---
title: "DexHandDiff: Interaction-aware Diffusion Planning for Adaptive Dexterous Manipulation"
title_zh: DexHandDiff：面向自适应灵巧操纵的交互感知扩散规划
authors: "Liang, Zhixuan, Mu, Yao, Wang, Yixiao, Chen, Tianxing, Shao, Wenqi, Zhan, Wei, Tomizuka, Masayoshi, Luo, Ping, Ding, Mingyu"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Liang_DexHandDiff_Interaction-aware_Diffusion_Planning_for_Adaptive_Dexterous_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向灵巧操纵的扩散规划方法，建模状态-动作动力学
tldr: 现有扩散规划方法在接触密集的灵巧操纵任务中常出现物体自动移动等不真实的鬼态现象，且难以处理复杂序列交互。本文提出DexHandDiff框架，通过双阶段扩散过程将交互前接触对齐与接触后目标导向控制解耦。该方法可建模联合状态-动作动力学，从而实现目标自适应且物理合理的灵巧操纵。在多个灵巧手序列任务基准上的实验表明，新方法显著优于现有扩散规划方法。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 973, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 859, \"height\": 275, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1708, \"height\": 656, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1788, \"height\": 512, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1667, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1790, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1618, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 140, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 192, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 872, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-liang-dexhanddiff-interaction-aware-diffusion-planning-for-adaptive-dexterous-manipulation-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 694, \"height\": 117, \"label\": \"Table\"}]"
motivation: 现有扩散规划方法在接触密集灵巧操纵中存在不真实鬼态与适应性不足的问题。
method: 提出DexHandDiff双阶段扩散规划，分别建模交互前接触对齐与接触后目标控制。
result: 在灵巧手序列操纵基准上显著优于现有方法，生成物理合理的接触动态。
conclusion: 接触感知与目标自适应机制对灵巧操纵中的扩散规划至关重要。
---

## Abstract
Dexterous manipulation with contact-rich interactions is crucial for advanced robotics. While recent diffusion-based planning approaches show promise for simple manipulation tasks, they often produce unrealistic ghost states (e.g., the object automatically moves without hand contact) or lack adaptability when handling complex sequential interactions. In this work, we introduce DexHandDiff, an interaction-aware diffusion planning framework for adaptive dexterous manipulation. DexHandDiff models joint state-action dynamics through a dual-phase diffusion process which consists of pre-interaction contact alignment and post-contact goal-directed control, enabling goal-adaptive generalizable dexterous manipulation. Additionally, we incorporate dynamics model-based dual guidance and leverage large language models for automated guidance function generation, enhancing generalizability for physical interactions and facilitating diverse goal adaptation through language cues. Experiments on physical interaction tasks such as door opening, pen and block re-orientation, object relocation, and hammer striking demonstrate DexHandDiff's effectiveness on goals outside training distributions, achieving over twice the average success rate (59.2% vs. 29.5%) compared to existing methods. Our framework achieves an average of 70.7% success rate on goal adaptive dexterous tasks, highlighting its robustness and flexibility in contact-rich manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper "DexHandDiff: Interaction-aware Diffusion Planning for Adaptive Dexterous Manipulation" based on the provided content. I need to follow a specific structure with 8 points, use Markdown formatting, and end with "（完）".

Let me analyze the paper carefully:

1. Core problem: Existing diffusion-based planning methods for dexterous manipulation have issues with "ghost states" (objects moving without hand contact) and lack adaptability to new goals in contact-rich sequential tasks.

2. Method: DexHandDiff proposes:
- Joint state-action diffusion (not just state or just action)
- Dual-phase diffusion: pre-contact alignment + post-contact goal-directed control
- Dynamics model-based dual guidance
- LLM-based automatic guidance function generation

3. Experiments: 5 dexterous manipulation tasks (Door, Pen, Hammer, Relocate from Adroit Hand; Block from Shadow Hand), compared with Diffuser, Decision Diffuser, Diffusion Policy baselines.

4. Resources: RTX 3090 GPU mentioned, model is lightweight (3.96M params, 3.27 GFLOPS).

5. Experimental count: Multiple ablations, goal-adaptability tests, ghost state validation, etc.

6. Conclusions: 59.2% vs 29.5% success rate, 70.7% on goal-adaptive tasks.

7. Strengths: First interaction-aware diffusion planner, joint state-action modeling, dual-phase mechanism, LLM-based guidance.

8. Limitations: Training on simulation, possible issues with bias toward training distributions (observed in 70° task), computation frequency needs further acceleration.

Let me write this in a well-structured Markdown format.</think>

# DexHandDiff 论文总结

## 1. 核心问题与研究动机

- **背景**：灵巧操纵（dexterous manipulation）是高级机器人技术的关键，涉及多指手在接触密集、序列化的物理交互任务（如开门、敲钉、物体重定位等）中的精确控制。
- **现有方法的局限**：
  - **Action-only 扩散方法**（如 Diffusion Policy）依赖训练数据分布，无法对中间状态进行显式引导，缺乏目标适应性。
  - **State-only 扩散方法**（如 Diffuser、Decision Diffuser）会出现"鬼态"（ghost states）现象——物体在灵巧手尚未接触时就自行移动到目标状态，这在物理上是不可能的，导致任务失败。
  - **Classifier-free 方法**对训练分布外的目标角度适应性差。
- **核心矛盾**：在接触密集任务中，物体状态不能被直接控制，必须通过灵巧手状态先建立接触才能影响物体，这要求扩散模型必须显式建模"手-物体-环境"的耦合动力学。

## 2. 方法论

### 2.1 核心思想
DexHandDiff 提出**交互感知的扩散规划框架**，通过联合状态-动作扩散（joint state-action diffusion）和**双阶段扩散过程**（dual-phase diffusion）实现物理一致且目标自适应的灵巧操纵。

### 2.2 关键技术细节

- **联合状态-动作扩散**：
  - 在拼接的状态-动作空间 $\tau = [(a_0, s_0), (a_1, s_1), ..., (a_T, s_T)]$ 上进行扩散。
  - 状态 $s$ 包含灵巧手 24 个关节角度 + 3 个位置偏移，以及任务特定物体状态；动作 $a$ 仅包含可控的手部关节与位置变化。

- **双阶段扩散机制**：
  - **Pre-contact 阶段（接触前）**：通过接触点对齐引导（$\epsilon_{\text{align}}$）和动力学一致性引导（$\epsilon_{\text{dyn}}$）引导手稳定接近物体接触点，防止物体提前移动。触发条件：$|s_{\text{hand}} - s_{\text{contact}}| > \delta_1$。
  - **Post-contact 阶段（接触后）**：引入目标导向引导（$\epsilon_{\text{succ}}$）、物理约束引导（$\epsilon_{\text{penalty}}$，限制每步状态变化幅度）和持续动力学引导。触发条件：距离小于阈值 $\delta_1$。

- **动力学模型引导（dynamics-aware generation）**：
  - 通过 $\epsilon_{\text{dyn}}(\tau) = |s_{t+1} - T(s_t, a_t)|^2$ 惩罚违反演示数据中观测动力学的状态-动作对。
  - 动力学模型 $T(s, a)$ 单独训练，确保物理可行性。

- **扩展行为模型与乘积专家框架（Product of Experts）**：
  - 将多个引导函数组合为 $\tilde{p}_\theta(\tau) \propto p_\theta(\tau) \prod_{i=1}^{n} h_i(\tau)$。
  - 总引导梯度为各专家梯度之和：$g = -\sum_{i=1}^{n} \nabla_\tau \epsilon_i(\tau, c)$。

- **LLM 引导函数自动生成**：
  - 采用 text-to-reward 范式，通过 6 部分提示模板（功能目的、引导结构、环境描述、函数原型、任务指令、few-shot 提示）让 LLM（Claude Sonnet 3.5）自动生成引导函数代码。
  - 将人工设计耗时从约 20 次试错减少到约 5 次。

- **In-hand 操纵简化机制**：对于笔旋转、块重定向等已在手中的任务，采用单阶段引导（$\epsilon_{\text{goal}} + \epsilon_{\text{finger}} + \epsilon_{\text{dyn}} + \epsilon_{\text{penalty}}$），其中 $\epsilon_{\text{finger}}$ 用 Heaviside 函数强制手指关节有真实运动。

## 3. 实验设计

### 3.1 数据集与环境
- **Adroit Hand 环境**（4 个任务）：Door、Pen、Hammer、Relocate，使用 D4RL 中通过遥操作收集的专家演示数据。
- **Shadow Hand 环境**（1 个任务）：Block Rotate-Z，使用 TQC+HER 算法收集 5000 条专家轨迹（因 Shadow Hand 不提供演示数据）。
- **仿真平台**：24 关节 Shadow Hand 仿真器，最多 30 自由度，与硬件设置匹配。

### 3.2 Benchmark 任务
- 5 个灵巧操纵任务：开门、笔重定向、敲钉、物体重定位、方块旋转。
- 每个任务包含**分布内（in-domain）**目标与**分布外（goal-adaptive / 半侧）**目标，例如：
  - 训练数据仅包含 90° 开门，测试 30°、50°、70°、110° 和关门（反向任务）。
  - 笔任务训练右半球朝向，测试左半球朝向。

### 3.3 对比方法
- **Classifier-guided 基线**：Diffuser（含 Goal Inpainting 和 Guided Sampling 两种变体）。
- **Classifier-free 基线**：Decision Diffuser、Diffusion Policy（Conditional DP）。
- **本文变体**：DexHandDiff-disc（使用 Goal Inpainting 替代引导采样）。

## 4. 资源与算力

- **GPU 型号**：测试阶段使用单块 **RTX 3090**。
- **模型规模**：3.96M 参数，3.27 GFLOPS，属于轻量级模型。
- **推理频率**：
  - Door 任务约 5.04 Hz；Pen 5.88 Hz；Hammer 5.86 Hz；Relocate 5.78 Hz；Block 6.92 Hz。
  - 通过 DPM Solver++ 可获 4× 加速，命令插值后可达到 36 Hz，满足真实机器人控制需求。
- **训练时长**：**论文中未明确报告训练时长、GPU 数量等训练资源信息**。
- **滚动预测视野（receding horizon）**：8（Door 任务为 32）。

## 5. 实验数量与充分性

### 5.1 实验覆盖
- **主对比实验**：Door 任务 6 种目标角度 × 3 次 × 10 随机种子（表 2）。
- **跨任务泛化实验**：5 个环境 × 2 种目标变体 × 3 次 × 10 种子（表 3）。
- **鬼态验证实验**：5 个自适应任务的预测/仿真状态 L2 距离对比（表 4）。
- **消融实验**：
  - LLM 引导生成 vs 人工设计 vs 朴素引导（表 5，3 个任务）。
  - 框架组件消融（表 6）：无引导 / Diffuser / Dyn-guide / Joint S&A / Dyn+Joint / DexHandDiff 完整版。
- **效率测试**：5 个任务的控制频率（表 7）。
- **可视化**：4 类任务的训练/推理结果对比（图 4）。

### 5.2 充分性与客观性
- **优点**：
  - 实验数量较为丰富，覆盖 5 个任务、多种目标变体和多个随机种子，结果含标准差。
  - 与三类基线方法（state-only、action-only、classifier-free、classifier-guided）全面对比。
  - 通过 L2 距离直接量化鬼态现象，并做组件级消融。
- **不足**：
  - 每个任务仅在单一训练配置下评估，缺少对多种训练数据规模/质量的鲁棒性分析。
  - 基线方法的超参选择与训练数据增强策略可能未充分优化，影响公平性。
  - 鬼态指标仅用 L2 距离衡量，未涵盖物理可行性等更广义指标。
  - 实验仅在仿真环境进行，真实机器人验证未呈现。

## 6. 主要结论与发现

- **目标自适应能力显著提升**：在 Door 任务中，训练数据仅含 90° 开门，测试 30° 时 DexHandDiff 成功率达 70.0%（对比 Diffusion Policy 16.7%），平均 59.2% vs 次优 29.5%，超过两倍。
- **跨任务性能优越**：在 5 个灵巧操纵任务（含分布内与自适应变体）上平均成功率 70.7%，全面优于 Diffuser（34.0%）和 Conditional DP（58.0%）。
- **鬼态现象有效缓解**：DexHandDiff 在自适应任务中预测/仿真状态 L2 距离约为基线的一半（如 Door 30°：2.92 vs 4.19）。
- **双阶段引导机制关键**：消融实验中，完整 DexHandDiff 平均成功率 67.5%，远超仅使用目标引导（27.5%）、仅添加动力学引导（27.5%）或仅联合状态-动作去噪（30.8%）的版本。
- **LLM 生成引导可行**：LLM 生成引导在 Door 30° 任务上达到 40%，证明自动引导设计的实用价值，但与人工设计（70%）仍有差距。
- **训练偏差现象**：70° 任务失败案例中有 8/14 次实际打开到 90°，说明训练动力学偏差对接近训练分布的目标影响更大，难以被引导信号纠正。

## 7. 论文亮点

- **首创交互感知扩散规划器**：首次系统解决灵巧操纵中扩散模型的鬼态问题，填补了 state-only 与 action-only 方法之间的空白。
- **双阶段扩散机制**：通过接触前/接触后两阶段分别采用不同引导函数，模拟人类操作中的"先对齐再操作"策略，符合运动学直觉。
- **乘积专家框架整合多引导**：理论优雅地将目标对齐、动力学一致性、物理约束等多个目标统一为单一优化目标。
- **LLM 自动引导生成**：首次将 text-to-reward 范式扩展到扩散策略的引导函数设计，降低人工调参成本。
- **轻量高效**：3.96M 参数模型 + 6 Hz 控制频率 + DPM Solver++ 加速 + 命令插值，可达 36 Hz，部署门槛低。
- **可视化解释性强**：图 4 清晰展示模型在新目标下能够正确保持物体物理接触并调整到目标状态。

## 8. 不足与局限

- **仿真到真实的迁移未验证**：所有实验仅在仿真器（Adroit / Shadow Hand MuJoCo）中进行，真实硬件上的性能未报告，未来工作提到可结合视觉感知。
- **训练资源未披露**：训练时长、GPU 数量、训练样本量等关键细节缺失，影响复现性评估。
- **训练偏差风险**：在接近训练分布的目标角度上（如 Door 70°）反而失败率更高，说明所学动力学对引导信号存在覆盖效应，可能限制细粒度控制。
- **基线公平性存疑**：如 Conditional DP 在 Pen/Block 任务上使用 action diffusion 而其他任务使用 state diffusion，作者承认是为适配任务特性而调整，这种选择对最终比较的公平性影响未深入讨论。
- **任务覆盖有限**：仅 5 个任务，且均为仿真环境中的刚性体操作，未覆盖软体操作、双手协作、长序列复杂任务等更广泛场景。
- **推理频率偏低**：Door 任务仅 5 Hz，对于需要快速反应的接触动态控制可能存在延迟风险。
- **LLM 生成引导的不确定性**：仅在 3 个任务上做消融，且 LLM 生成结果依赖提示工程，泛化到更复杂任务的稳定性未充分验证。
- **鬼态指标单一**：仅使用 L2 距离量化，未引入物理可行性、运动连贯性等更全面的评估维度。

（完）
