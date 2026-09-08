---
title: "CycleManip: Enabling Cycle-based Manipulation via Effective History Perception and Understanding"
title_zh: CycleManip：通过有效历史感知与理解实现周期性操作
authors: "Wei, Yi-Lin, Liao, Haoran, Lin, Yuhao, Wang, Pengyue, Liang, Zhizhao, Liu, Guiliang, Zheng, Wei-Shi"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Wei_CycleManip_Enabling_Cycle-based_Manipulation_via_Effective_History_Perception_and_Understanding_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向周期性机器人操作的模仿学习基准及自动评测工具
tldr: 本文关注一类被忽视的机器人操作任务——周期性操作，要求机器人在规定时间内完成循环或重复动作（如摇瓶、敲钉）。现有模仿学习方法因未充分利用历史信息而难以胜任。为此，作者提出 CycleManip 框架以强化历史感知与理解，并构建了包含充足数据和自动评测工具的基准。实验表明该方法在多种周期性任务上取得提升，推动了复杂时间结构操作任务中模仿学习的研究，并提供了可复用的测试平台。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1755, \"height\": 898, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1761, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1759, \"height\": 941, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1736, \"height\": 479, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1388, \"height\": 465, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1566, \"height\": 469, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1274, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1472, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 840, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wei-cyclemanip-enabling-cycle-based-manipulation-via-effective-history-perception-and-understanding-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 861, \"height\": 187, \"label\": \"Table\"}]"
motivation: 周期性操作任务常要求规定时长内的循环动作，现有模仿学习难以利用历史信息完成。
method: 提出 CycleManip 框架以增强历史感知与理解，并构建含自动评测的基准。
result: 在摇瓶、敲钉等周期性任务中显著提升了完成率与时间控制精度。
conclusion: 该工作为复杂时间结构操作中的模仿学习提供了新框架与基准。
---

## Abstract
In this paper, we explore an important yet underexplored task in robot manipulation: cycle-based manipulation, where robots need to perform cyclic or repetitive actions with an expected terminal time. These tasks are crucial in daily life, such as shaking a bottle or knocking a nail. However, few prior works have explored this task, leading to two main challenges: 1) the imitation methods often fail to complete these tasks within the expected terminal time due to the ineffective utilization of history; 2) the absence of a benchmark with sufficient data and automatic evaluation tools hinders development of effective solutions in this area. To address these challenges, we first propose the CycleManip framework to achieve cycle-based task manipulation in an end-to-end imitation manner without requiring any extra models, hierarchical structure or significant computational overhead. The core insight is to enhance effective history perception by a cost-aware sampling strategy and to improve historical understanding by multi-task learning. Second, we introduce a cycle-based task manipulation benchmark, which provides diverse cycle-based tasks, and an automatic evaluation method. Extensive experiments conducted in both simulation and real-world settings demonstrate that our method achieves high success rates in cycle-based task manipulation. The results further show strong adaptability performance in general manipulation, and the plug-and-play ability on imitation policies such as Vision-Language-Action (VLA) models. Moreover, the results show that our approach can be applied across diverse robotic platforms, including bi-arm grippers, dexterous hands, and humanoid robots.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "CycleManip: Enabling Cycle-based Manipulation via Effective History Perception and Understanding" following specific structure. Let me carefully analyze the paper and organize my response according to the 8 requested points.

Key points from the paper:
1. Problem: Cycle-based manipulation tasks (e.g., shaking bottle, hammering nail) - robots need to perform cyclic actions and stop at expected terminal time
2. Method: CycleManip framework with two components:
   - Effective Historical Perception: cost-aware sampling strategy (dense sampling for low-overhead observations like proprioception, heuristic sparse sampling for high-overhead observations like RGB/point clouds)
   - Effective Historical Understanding: multi-task learning with auxiliary task of predicting current cycle progress (10-way classification)
3. Benchmark: Built on RoboTwin 2.0 with 8 cyclic tasks, includes automatic evaluation system
4. Experiments: Comparison with DP, DP3, RDT, Pi-0; real-world experiments on diverse platforms
5. Computing: Single RTX 4090 for training, RTX 4070 for real-world inference; Pi-0 and RDT trained on H100
6. Results: Significantly outperforms baselines in success rate and cycle count deviation
7. Plug-and-play: Can be integrated with Pi-0 VLA model
8. Generalization: Works on general manipulation tasks too

Let me write a detailed summary following the requested format.</think>

# CycleManip 论文总结

## 1. 核心问题与研究背景

- **问题定义**：本文关注的是机器人操作中一类被忽视但极为重要的任务——**周期性操作（Cycle-based Manipulation）**，即机器人需要执行循环/重复动作并在规定的终止时刻准确停止（如"摇瓶五次"、"敲钉八次"、"搅拌食材"等）。
- **现有方法的不足**：
  - **历史信息利用低效**：现有模仿学习方法（如 DP、DP3、Pi-0、RDT）通常仅依赖短时间窗口的观测进行动作预测。在周期性任务中，每个周期的当前观测往往看起来几乎相同，模型无法判断当前处于周期的哪一阶段，导致陷入死循环或提前终止。
  - **缺少专用基准**：现有机器人操作基准（如 RLBench、Libero 等）针对通用长程任务设计，缺乏专门用于周期性任务的数据集与自动评测工具。
- **研究意义**：周期性任务广泛存在于家庭、工业与实验室场景中（如分装、混合、敲击、清洁、切割等），是机器人自主化部署的关键能力之一。

## 2. 方法论

整体框架采用**端到端模仿学习**方式，无需额外辅助模型、分层结构或显著的算力开销。

### 2.1 问题形式化
- 策略基于历史观测和语言指令预测动作：
  $$a_t = \pi(l_{an}, \{o_i\}_{i=1}^{t})$$
- 其中 $l_{an}$ 为用户语言指令，$o_i$ 为机器人观测。

### 2.2 核心组件一：有效历史感知（Effective Historical Perception）
- **关键思想**：直接扩展观测视野会带来高计算开销（编码/融合高维视觉代价大），因此提出**成本感知采样策略（Cost-Aware Sampling）**，对不同模态采用不同采样密度：
  - **低开销观测**（如本体感知 proprioception，尤其是末端执行器位姿差）：使用**密集且宽范围采样** $H_l(\{o_i^{low}\}_{i=1}^t)$，因其编码成本低，可以完整保留所有历史信息，凸显周期性运动特征。
  - **高开销观测**（如 RGB 图像、点云）：使用**启发式稀疏采样** $H_h(\{o_i^{high}\}_{i=1}^t)$：
    - 以当前帧为 $t$，从最近帧开始按指数规则 $t - 2^k$ 采样后半部分（$0.5 \cdot K_{high}$ 帧）；
    - 对前半部分做右侧二值采样（$0.5 \cdot K_{high}$ 帧），以兼顾早期上下文。
- 策略更新为：
  $$a_t = \pi(H_h(\{o_i^{high}\}), H_l(\{o_i^{low}\}))$$

### 2.3 核心组件二：有效历史理解（Effective Historical Understanding）
- **关键思想**：仅靠扩展观测不够——监督信号（如"敲一下"）在每个周期都相同，会让模型学到退化的特征。为此引入**多任务学习（Multi-Task Learning）**：
  - 增加一个辅助任务：预测当前所处的进度 $b_t$（即当前帧数 / 最大帧数）。
  - 将 $[0, 1]$ 区间离散化为 10 个区间，做 10 分类任务。
  - 用 MLP 融合特征，先通过多层 MLP 用于扩散决策，再通过单层 MLP 预测进度，避免辅助任务主导优化。
- 总损失：
  $$\mathcal{L} = \alpha \cdot \text{MSE}(a_t, a_t^*) + \beta \cdot \text{CE}(b_t, b_t^*)$$
  其中 $\alpha = 1$，$\beta = 0.1$。

### 2.4 整体网络架构
- 语言指令经 **CLIP** 编码为 $f_{lan}$；
- 高维视觉观测经 **Point Encoder** 编码为 $f_h$；
- 低维本体感知经 **Transformer**（全局 CLS + 局部 MLP）编码为 $f_l$；
- 通过 MLP 融合后，作为扩散模型条件（采用 FiLM 调制），输出动作预测（动作视野 8，DDIM 采样，训练 100 步，测试 10 步）。

## 3. 实验设计

### 3.1 数据集/场景
- **仿真基准（CycleManip Benchmark）**：基于 **RoboTwin 2.0** 平台构建，包含 **8 个周期性任务**：
  - 双刀切菜板、敲钉子、摇瓶、擀面杖擀面、切萝卜、打蛋、化学混合、Morse 敲击。
  - 每个任务采集 **200 条专家演示**，循环次数范围 1–8，并标注目标循环次数、每步完成数和物体 6D 位姿。
- **通用任务基准**：同时在 RoboTwin 2.0 通用操作基准上验证（4 个任务）。
- **真实世界**：6 个真实任务（敲钉、摇瓶、击鼓、打气、切菜、擦桌），覆盖单臂、双臂夹爪、双灵巧手、人形机器人（Unitree G1）等多种平台。

### 3.2 对比方法
- **DP**（Diffusion Policy）
- **DP3**（3D Diffusion Policy）
- **RDT-1B**
- **Pi-0**（VLA 模型）
- 以及自身的消融版本（去掉历史感知/去掉历史理解）。

### 3.3 评测指标
- **成功率（Success Rate, Suc. %）**：完成操作且循环次数正确的比例。
- **循环次数偏差（Cycle Count Deviation, Cyc.）**：执行次数与真实要求次数的平均绝对偏差。
- 仿真每任务 100 次试验；真实世界每任务 16 次试验。

### 3.4 自动评测系统
- 针对接触类任务（敲钉、切菜）：基于**状态机的碰撞检测**计数；
- 针对非接触类任务（摇瓶、搅拌）：基于**峰值检测算法**分析物体位姿轨迹；
- 经人工复核 100 次结果确认可靠。

## 4. 资源与算力

- **训练硬件**：
  - 框架自身（DP/DP3 类）：单块 **RTX 4090** GPU；
  - Pi-0 与 RDT 基线：单块 **H100** GPU。
- **推理硬件**：
  - 仿真：单块 **RTX 4090**；
  - 真实世界：单块 **RTX 4070** GPU。
- **训练时长/批次**：训练 300 epochs，batch size = 128，初始学习率 $2.0 \times 10^{-4}$，余弦调度。
- **效率分析（Table 5）**：相比 DP3，单步训练时间仅从 0.073s 增至 0.102s，GPU 显存从 16796 MB 增至 17342 MB，测试时间从 0.0893s 增至 0.0953s，显存从 5801 MB 增至 6003 MB——开销增加很小。
- **未明确披露**：训练总时长（wall-clock time）和能耗数据未在文中给出。

## 5. 实验数量与充分性

- **任务数量**：仿真 8 个周期性任务 + 4 个通用任务；真实世界 6 个任务，覆盖多种机器人形态。
- **消融实验**：Table 2 中分别测试了"无历史理解（w/o Task）"与完整版本（Ours），验证两个核心模块的独立贡献。
- **对比方法**：4 个 SOTA 基线（DP、DP3、RDT、Pi-0）。
- **额外实验**：
  - **Plug-and-Play 实验**（Table 4）：将 CycleManip 嵌入 Pi-0，验证可插拔性；
  - **跨形态实验**（Table 2）：在单臂夹爪、双臂夹爪、双灵巧手、人形机器人上验证；
  - **效率分析**（Table 5）：训练/推理时间与显存对比。
- **公平性说明**：所有基线使用 RoboTwin 默认设置；DP/DP3 在其框架中复用了相同的语言编码器以保证公平。
- **充分性评估**：
  - 仿真任务数量、循环次数多样性（1–8 次）、评测指标（成功率+循环偏差）较为充分；
  - 真实世界试验次数偏少（16 次/任务），统计置信度有限；
  - 每个任务的循环次数由训练数据中已见范围决定，对**分布外循环次数（如 9 次以上）的泛化能力**未充分验证。

## 6. 主要结论与发现

- **周期性任务上的显著优势**：CycleManip 在所有 8 个仿真周期性任务上均大幅超越 DP、DP3、RDT、Pi-0（如 block hammering Suc. 从 23% 提升至 86%；bottle shaking 从 16% 提升至 95%）；循环次数偏差（Cyc.）同样显著降低。
- **真实世界验证**：在 6 个真实任务、不同机器人形态下，CycleManip 相比最强基线 DP3 提升显著（如敲钉 62.5% → 93.75%，擦桌 40% → 100%）。
- **通用任务上的泛化**：在 RoboTwin 2.0 通用任务上仍达到最优，证明了方法并非仅适用于周期性任务。
- **可插拔性**：仅采样当前帧视觉 + 历史本体感知，嵌入 Pi-0 后性能显著提升（如 bottle shaking Suc. 从 19% → 72%）。
- **算力开销可接受**：相对基线仅引入边际级计算与显存增加。
- **核心消融结论**：单独加入"成本感知采样"即可显著提升；再加入"多任务进度预测"可进一步提升，说明**感知 + 理解**两个组件缺一不可。

## 7. 优点与亮点

- **问题新颖且实用**：首次系统性地提出"周期性操作"任务定义，并构建专用基准，填补了该方向研究空白。
- **方法简洁实用**：不引入额外辅助模型、不分层设计、不显著增加计算开销，端到端可训练，便于部署到现有模仿学习策略中。
- **成本感知采样设计巧妙**：低维信息密集采、高维信息稀疏采，平衡了历史视野与计算代价。
- **多任务进度预测动机明确**：有效避免了"同监督信号导致特征退化"问题。
- **基准设计完整**：含 8 个任务、可配置循环次数、自动数据生成、自动评测系统，且经过人工复核保证可靠性。
- **跨平台验证充分**：覆盖单臂/双臂夹爪、灵巧手、人形机器人，展示了强异构适应性。
- **可插拔性强**：可与 VLA 模型（Pi-0）结合，体现了方法的通用性。

## 8. 不足与局限

- **真实世界试验规模偏小**：每任务仅 16 次试验，可能受随机性影响显著，统计置信度有限。
- **循环次数泛化未充分验证**：训练数据循环次数为 1–8，对训练分布外循环次数的鲁棒性未明确评估。
- **依赖低维本体感知**：成本感知策略的"低开销密集采样"依赖于机器人本体感知信号，对本体感知质量差或缺失的形态（如部分欠驱动平台）可能受影响。
- **进度标签的获取**：辅助任务需要"当前帧数 / 总帧数"作为监督信号，这在真实部署中需要预先知道总任务长度，可能限制了在**开放式/非预定义循环次数**场景下的直接应用。
- **基线公平性的潜在偏差**：Pi-0 与 RDT 在 H100 上训练而 CycleManip 在 RTX 4090 上训练，作者未明确说明这一算力差异是否会对结果产生潜在影响（虽然推理资源差异已说明）。
- **缺乏失败案例分析**：未对失败案例做深入归因（如哪些任务在哪些循环次数最易失败）。
- **语言指令多样性**：评测中循环次数通过指令传达，但指令模板相对简单（如"shaking five times"），对更复杂自然语言指令（如带条件分支的循环）的处理能力未验证。
- **安全与可重复性**：周期性操作涉及多次接触（如敲钉、切菜），但论文未讨论碰撞安全与失败恢复机制。

（完）
