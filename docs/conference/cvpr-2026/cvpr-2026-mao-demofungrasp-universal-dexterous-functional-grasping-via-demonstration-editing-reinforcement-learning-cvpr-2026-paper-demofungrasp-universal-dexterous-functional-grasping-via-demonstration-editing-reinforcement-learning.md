---
title: "DemoFunGrasp: Universal Dexterous Functional Grasping via Demonstration-Editing Reinforcement Learning"
title_zh: DemoFunGrasp：通过演示编辑与强化学习实现通用灵巧功能抓取
authors: "Mao, Chuan, Yuan, Haoqi, Huang, Ziye, Xu, Chaoyi, Ma, Kai, Lu, Zongqing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Mao_DemoFunGrasp_Universal_Dexterous_Functional_Grasping_via_Demonstration-Editing_Reinforcement_Learning_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 灵巧功能抓取，将演示编辑与强化学习相结合以服务下游操作
tldr: 针对下游操作所需但研究不足的精细功能抓取问题，本文提出 DemoFunGrasp，将功能抓取分解为抓取风格与可供性两个分量，并将演示编辑与强化学习相结合以应对奖励设计与探索难题。实验表明该方法在多种物体上实现通用灵巧功能抓取，并提升了仿真到真实的迁移能力。该工作为操作流水线提供了可复用的桥接方法，但其核心聚焦于抓取而非完整任务模仿。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1599, \"height\": 921, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1806, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 543, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 423, \"height\": 278, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 653, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1559, \"height\": 909, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 791, \"height\": 196, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 785, \"height\": 318, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 831, \"height\": 412, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-demofungrasp-universal-dexterous-functional-grasping-via-demonstration-editing-reinforcement-learning-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1613, \"height\": 267, \"label\": \"Table\"}]"
motivation: 精细功能抓取对下游操作至关重要，但奖励设计与多任务探索困难。
method: 将功能抓取分解为抓取风格与可供性，结合演示编辑与强化学习进行训练。
result: 在多种物体上实现了通用灵巧功能抓取，并改善了仿真到真实的迁移效果。
conclusion: 为操作前置的灵巧功能抓取提供了一种融合演示与强化学习的解决方案。
---

## Abstract
Reinforcement learning (RL) has achieved great success in dexterous grasping, significantly improving grasp performance and generalization from simulation to the real world. However, fine-grained functional grasping, which is essential for downstream manipulation tasks, remains underexplored and faces several challenges: the complexity of specifying goals and reward functions for functional grasps across diverse objects, the difficulty of multi-task RL exploration, and the challenge of sim-to-real transfer. In this work, we propose DemoFunGrasp for universal dexterous functional grasping. We factorize functional grasping conditions into two complementary components -- grasping style and affordance -- and integrate them into an RL framework that can learn to grasp any object with any functional grasping condition. To address the multi-task optimization challenge, we leverage a single grasping demonstration and reformulate the RL problem as one-step demonstration editing, substantially enhancing sample efficiency and performance.Experimental results in both simulation and the real world show that DemoFunGrasp generalizes to unseen combinations of objects, affordances, and grasping styles, outperforming baselines in both success rate and functional grasping accuracy. In addition to strong sim-to-real capability, by incorporating a vision-language model (VLM) for planning, our system achieves autonomous instruction-following grasp execution.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze this paper "DemoFunGrasp: Universal Dexterous Functional Grasping via Demonstration-Editing Reinforcement Learning" and produce a structured Chinese summary following the 8 specified points. Let me carefully read through the paper and extract the relevant information for each section.

1. Core problem: Fine-grained functional grasping for downstream manipulation - challenges in reward design, multi-task RL exploration, sim-to-real transfer
2. Method: Factorize functional grasping into affordance + grasping style, integrate into one-step demonstration editing RL
3. Experiments: DexGraspNet + YCB, comparison with DemoGrasp, UniDexGrasp, Dexonomy
4. Resources/compute: IsaacGym mentioned, but no specific GPU count/duration
5. Experiment scope: Multiple ablation studies, sim-to-real, VLM integration
6. Conclusions: Strong generalization, sim-to-real capability, 71% success rate
7. Strengths: One-step RL reformulation, style+affordance conditioning, VLM integration
8. Limitations: Centimeter-scale accuracy, no dynamic pre-grasp, no in-hand adjustment, no tactile sensing

Let me organize this into a comprehensive Chinese summary.</think>

# DemoFunGrasp 论文总结

## 1. 核心问题与研究动机

- **问题定位**：灵巧手功能抓取（functional grasping）是下游操作任务（如工具使用）的基础，但现有 RL 抓取研究多仅关注**机械稳定性**（即物体不掉落），忽略了"抓哪里"与"怎么抓"的功能性语义。
- **三大挑战**：
  1. **奖励与目标难以统一**：跨物体、跨抓取风格（grip style）的功能抓取奖励函数设计复杂。
  2. **多任务 RL 探索困难**：高 DoF 灵巧手 + 多任务组合导致策略搜索空间巨大，优化不稳定。
  3. **仿真到真实迁移**：功能抓取需闭环控制，仿真训练难以直接落地实物。
- **研究意义**：填补精细功能抓取这一空白，作为操作流水线的桥接组件，为 VLM 等高层规划器提供可靠的低层执行器。

## 2. 方法论

### 2.1 核心思想：功能条件分解
- 将功能抓取条件分解为两个互补分量：
  - **Affordance（可供性）**：3D 空间点 `p_afford ∈ ℝ³`，指示"抓哪里"（如杯把、盖沿）。
  - **Grasping Style（抓取风格）**：用 one-hot 向量 `l_style` 编码的参考手型，指示"怎么抓"（如 palmar pinch、lateral、small diameter 等）。
- 两者共同完整定义一个功能抓取。

### 2.2 关键技术：一步演示编辑 RL
- **问题重塑**：将传统多步灵巧操作 RL 转化为**单步（MDP）演示编辑问题**——只采集**一条**遥操作抓取演示，策略输出残差动作 `(ΔT, Δq, k)`：
  - `ΔT`：末端执行器位姿修正；
  - `k`：关节缩放系数；
  - `Δq`：关节角度残差。
- **状态空间**：`o = (s_r, s_o, x_o, p_afford, l_style)`，即机器人本体位姿、物体位姿、完整点云、affordance 点、抓取风格。
- **动作空间**：基于物体几何自适应编辑参考轨迹，编辑后的演示执行一次即得到奖励信号。

### 2.3 风格感知的演示编辑
- **风格选择**：基于 Feix 等人的人类抓取分类，并经大规模仿真实验去重，保留 **Shadow Hand 9 种**风格、**Inspire Hand 4 种**风格。
- **几何条件手型编辑**：目标关节配置 `q*_pos = k · q_pos + Δq`，并通过分数系数沿参考轨迹插值，保证时序连贯性。
- **运动插值公式**：`q_i = q_ref^0 + f · (q_ref^i - q_ref^0)`，其中 `f = (q*_pos - q_ref^0) / (q_ref^Tl - q_ref^0)`，无需碰撞检查即可生成平滑轨迹。

### 2.4 Affordance 采样与奖励设计
- **采样策略**：基于物体表面法向对齐与规范化位姿估计 affordance 似然分布，每回合随机采样一个候选点。
- **分层奖励**：
  - `r_afford`：稀疏接近项，结合 `obj_bb`（包围盒最长边）做物体尺度归一化；
  - `r_close`：密集对齐项，沿轨迹计算 affordance 点与手接触点的最小距离；
  - `r_qpos`：风格一致性项 `exp(-∥q_pos - q*_pos∥²)`；
  - `r_success`：成功奖励。
- 总奖励：`r = λ_afford · r_afford + λ_close · r_close + λ_qpos · r_qpos + r_success`。

### 2.5 视觉化 sim-to-real
- 训练收敛后采集 **30k 成功轨迹**，通过模仿学习蒸馏为 RGB-based 策略。
- 评估三种网络架构：ACT+ViT、ViT 扩散策略、**DiT + VLM 编码器**（GR00T N1），最终 VLM+DiT 表现最佳。
- 域随机化：物体/桌面纹理、光照方向与强度、相机外参、初始位姿等。
- Affordance 通过相机内/外参投影到图像平面，作为视觉编码器的显式空间线索。

## 3. 实验设计

- **仿真平台**：IsaacGym（GPU 物理仿真），RL 算法使用 **PPO**。
- **数据集/物体**：
  - 训练集：YCB + DexGraspNet（**3,200 个物体**），姿态随机化于 50×50 cm 区域；
  - 测试集：3 类仿真物体 + 3 类真实物体；
  - 真实世界扩展测试：33 个额外物体（包含高度不规则、部分可形变物体）。
- **真实机器人平台**：7-DoF Franka 3 + 6-DoF **Inspire Hand**（6 主动 + 6 被动关节），两台 RealSense D435i 相机对角放置。
- **评估指标**：
  - **GSR**（抓取成功率）：抓起 ≥10 cm 并稳定 20 步；
  - **SAD**（Success Affordance Distance）：抓取接触点与目标 affordance 点的欧氏距离；
  - **SD**（Style Diversity）：成功抓取手型配置的平均成对欧氏距离；
  - **SA**（Style Accuracy）：成功抓取中风格匹配的比例；
  - **IAS / ISS**：真实世界 intended affordance/style score。
- **对比方法**：
  - **DemoGrasp**：单演示编辑 RL 的 SOTA（基线/对比）；
  - **UniDexGrasp**：无风格条件的 RL 抓取生成；
  - **Dexonomy**：抓取合成方法（用作风格多样性可视化对比）；
  - VLM 规划：使用 **Embodied-R1** 自动生成 affordance 点。

## 4. 资源与算力

- 文中**未明确披露** GPU 型号、数量及训练时长等具体算力信息。
- 仅提到训练环境为 **NVIDIA IsaacGym**（基于 GPU 的物理仿真平台），并采集 **30k 条成功轨迹**用于模仿学习蒸馏。

## 5. 实验数量与充分性

- **主要定量实验**：
  - Affordance-conditioned grasping：对比 DemoGrasp（seen/unseen 类别）；
  - Grasping style diversity：对比 UniDexGrasp（seen/unseen 类别，含 best-style 变体）；
  - 消融实验：5 项组件消融（afford reward、object size clipping、close reward、qpos reward、style disturbance）；
  - RGB-based 仿真评估；
  - 真实世界评估：人类标注 vs VLM 预测（9 + 33 个物体 ×3 次试验）；
  - 跨形态（cross-embodiment）评估：Shadow Hand 与 Inspire Hand。
- **充分性**：实验覆盖面较广（仿真+真实、seen/unseen 类别、风格多样性、多网络架构对比），消融较为系统；但对比方法种类仍较有限，且未与多个最新 VLM 或功能抓取方法做直接同条件对比。

## 6. 主要结论与发现

- **整体性能**：在 3,200 个 DexGraspNet 物体上达到 SOTA；affordance 距离相比 DemoGrasp 降低 >3 cm（从约 6.2 → 3.0 cm）。
- **风格多样性**：相比 UniDexGrasp 提升约 **1.5×**，且风格经 RL 后仍保持良好区分度（t-SNE 可视化验证）。
- **泛化能力**：seen 类别 GSR 76.26%，unseen 类别 71.65%（完整模型）；best-style 变体分别可达 81.74% / 78.68%。
- **sim-to-real**：RGB 策略零样本迁移至真实机器人，**9 个日常物体 71% 成功率**；33 个扩展物体 70.7% 成功率。
- **VLM 集成**：结合 Embodied-R1 后，语言引导功能抓取真实平均成功率 **64.4%**。
- **跨形态**：无需超参调优即可在 Shadow Hand（22 DoF）与 Inspire Hand（12 DoF）上分别训练**均取得 ≥77% 成功率**。

## 7. 优点与亮点

- **问题重塑新颖**：将多步高维灵巧 RL 简化为**单步演示编辑**，显著降低探索难度，提升样本效率。
- **结构化条件设计**：将 affordance 与 style 同时融入**观测、奖励、动作空间**，三者协同提供稠密且语义一致的训练信号。
- **尺度自适应的 affordance 奖励**：通过 `obj_bb` 归一化，缓解大/小物体训练不稳定问题。
- **完整的 VLA 闭环**：高层 VLM + 低层 RL 策略，实现语言到功能抓取的端到端执行。
- **风格可插拔**：演示编辑机制使得风格条件易于拓展，无需重新训练底层策略。
- **跨形态鲁棒性**：同一框架适配不同 DoF 的灵巧手，体现方法的通用性。

## 8. 不足与局限

- **精度仍为厘米级**：作者自述准确度仅在厘米尺度（≈3 cm），距人类水平仍有差距。
- **缺少动态调整**：当前策略仅做单步编辑，无 pre-grasp 操作或 in-hand adjustment，难以应对需要先调整物体再抓取的任务。
- **缺乏触觉感知**：未引入触觉反馈，对接触丰富或形变物体的鲁棒性受限。
- **计算资源未披露**：GPU 类型/数量/训练时长等关键可复现性信息缺失。
- **失败模式明确但未根治**：(i) affordance 区域过小无法精抓；(ii) 训练分布外物体泛化不足；(iii) VLM 在挑战性姿态下预测失准。
- **对比基线有限**：主要与 DemoGrasp、UniDexGrasp、Dexonomy 等少量方法对比，未涵盖更广泛的功能抓取或 affordance 方法。
- **真实世界评估规模有限**：扩展测试虽达 33 个物体，但每个 3 次试验，统计波动较大；未见长期、不同光照/杂乱场景的鲁棒性测试。
- **依赖单一演示**：风格空间受演示覆盖范围限制，极端新颖抓取类型可能无法通过编辑得到。

（完）
