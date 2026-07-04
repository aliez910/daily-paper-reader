---
title: Universal Actions for Enhanced Embodied Foundation Models
title_zh: UniAct：面向增强型具身基础模型的通用动作空间
authors: "Zheng, Jinliang, Li, Jianxiong, Liu, Dongxiu, Zheng, Yinan, Wang, Zhihao, Ou, Zhonghong, Liu, Yu, Liu, Jingjing, Zhang, Ya-Qin, Zhan, Xianyuan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zheng_Universal_Actions_for_Enhanced_Embodied_Foundation_Models_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向跨构型具身基础模型的通用动作空间
tldr: 不同机器人构型的动作空间异构，难以利用互联网级跨构型数据训练统一具身基础模型。本文提出 UniAct 框架，在通用动作空间中学习跨机器人的共享行为结构，使单一基础模型可处理多种构型数据。该工作直接支撑通用视觉-动作模型在机器人操纵和具身控制中的规模化训练。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 755, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1691, \"height\": 951, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1714, \"height\": 549, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1694, \"height\": 536, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 273, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1745, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1703, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1712, \"height\": 539, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 273, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zheng-universal-actions-for-enhanced-embodied-foundation-models-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 257, \"label\": \"Table\"}]"
motivation: 异构动作空间阻碍了跨构型数据用于训练统一具身基础模型。
method: 提出通用动作空间，学习跨机器人共享的结构化动作表征。
result: 实现了单一基础模型在多种机器人构型上的有效学习。
conclusion: 为通用视觉-动作基础模型提供了统一的动作抽象。
---

## Abstract
Training on diverse, internet-scale data is a key factor in the success of recent large foundation models. Yet, using the same recipe for building embodied agents has faced noticeable difficulties. Despite the availability of many crowd-sourced embodied datasets, their action spaces often exhibit significant heterogeneity due to distinct physical embodiment and control interfaces for different robots, causing substantial challenges in developing embodied foundation models using cross-embodiment data. In this paper, we introduce UniAct, a new embodied foundation modeling framework operating in the Universal Action Space. Our learned universal actions capture the generic behaviors across diverse robots by exploiting their shared structural features, and enable enhanced cross-domain data utilization and cross-embodiment generalizations by eliminating the notorious heterogeneity. Moreover, the universal actions can be efficiently translated back to heterogeneous actionable commands by simply adding embodiment-specific details, from which fast adaptation to new robots becomes simple and straightforward. Our 0.5B instantiation of UniAct outperforms 14X larger SOTA embodied foundation models in extensive evaluations on various real-world and simulation robots, showcasing exceptional cross-embodiment control and adaptation capability, highlighting the crucial benefit of adopting universal actions.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Universal Actions for Enhanced Embodied Foundation Models" (UniAct) following a specific structure. Let me organize the information from the paper carefully and create a comprehensive summary.

The paper is about creating a universal action space for embodied foundation models that can work across different robot embodiments. Let me extract the key information:

1. **Core problem**: Action heterogeneity across different robot embodiments (different DoF, control interfaces like EEF position/velocity, joint position/torque, navigation) makes it hard to build generalist embodied foundation models. Existing approaches either forcibly treat different action spaces as equivalent (causing conflicts) or naively aggregate them (failing to capture shared structures).

2. **Method**: 
- Universal Action Space: vector-quantized codebook U ∈ R^(N×D) where N=256, D=128
- Universal Action Extractor: fine-tuned VLM (LLaVA-OneVision-0.5B) that outputs likelihood p(u|o,g) of selecting universal action u given observation o and goal g
- Uses Gumbel-Softmax for differentiable argmax
- Heterogeneous Decoders: lightweight MLP heads for each embodiment, taking (u*, o) as input
- Training: behavior cloning loss on each domain's action labels

3. **Experiments**:
- Real-world WidowX robot (19 tasks, 190 rollouts)
- LIBERO simulation benchmark (130 tasks across 5 suites)
- New robot AIRBOT (fast adaptation test, 100 demos, 4 control interfaces)
- Comparison with Octo (0.1B), CrossFormer, OpenVLA (7B), LAPA (7B)

4. **Resources**: 64 A100 GPUs, 10 days of training, 1 million demonstrations from 28 embodiments

5. **Conclusions**: 
- 0.5B model outperforms 14x larger models
- Universal actions encode semantically meaningful behaviors
- Fast adaptation to new robots with minimal parameters (4M/500M = 0.8%)

6. **Strengths**:
- Novel approach to action heterogeneity
- Information bottleneck forces shared representation
- Strong empirical results with smaller model
- Fast adaptation capability

7. **Limitations**:
- Limited to single-arm robots primarily
- Resource constraints on larger models
- Coverage of embodiments

Let me write this up in a structured Chinese summary.</think>

# UniAct 论文总结：面向增强型具身基础模型的通用动作空间

## 1. 核心问题与研究动机

具身智能领域期望借助"互联网规模"的多源数据训练通用基础模型（VLA），但存在严重阻碍：

- **动作空间异构性**：不同机器人因机械结构（机械臂、四足、车等）、自由度（DoF）、控制接口（末端位姿 EEF 位置/速度、关节位置/力矩、导航速度等）的差异，动作空间分布在物理空间中近乎不相交的流形上；
- **现有方案的缺陷**：
  - **粗暴对齐**：直接对所有动作做相同的离散化或归一化（Octo、OpenVLA、RT-X），导致相同动作编码可能对应完全不同的物理含义；
  - **朴素聚合**：把不同动作空间拼接为一个统一空间（CrossFormer、RDT、π0、Yang et al.），依赖大量人工工程且难以挖掘跨构型的共享结构；
- **多模态人类操作**：即便同一平台，由不同操作员演示也会进一步加剧动作分布的多模态。

本文认为跨构型数据难以利用的根本原因是**没有解决动作异构性**，因此提出 UniAct：在**通用动作空间**中学习跨机器人共享的"原子行为"，从根本上消除异构性。

---

## 2. 方法论

### 2.1 核心思想
将不同机器人的异构控制信号统一抽象为**通用动作（universal action）**——一种与具体构型和控制接口无关的"原子行为"语义；下游通过轻量级解码器补全构型细节，即可还原为各平台可执行的控制指令。

### 2.2 关键技术细节

**（1）通用动作空间**
- 表示为向量量化码本 $U = (u_1, u_2, ..., u_N)$，其中 $U \in \mathbb{R}^{N \times D}$，本文实例化为 $N=256, D=128$；
- 每个码字 $u_i$ 表示一个跨机器人通用的原子行为。

**（2）通用动作提取器（Universal Action Extractor）**
- 基于预训练 VLM（LLaVA-OneVision-0.5B）进行微调；
- 输入：观察 $o$ + 任务目标 $g$（语言指令）；
- 输出：在码本上的选择概率 $p(u|o, g)$；
- 最优通用动作 $u^* = \arg\max_{u \in U} p(u|o, g)$；
- **关键设计**：相比 LAPA/IGOR/LAPO 等仅通过帧间视觉变化推断 latent action，本文结合**目标驱动的任务进展**（条件于语言指令）进行推断，避免把"场景中无关视觉变化"误编码进动作；
- **离散采样训练**：因 $\arg\max$ 不可微，采用 Gumbel-Softmax：
  $$u^* = \sum_{i=1}^{N} w_i u_i,\quad w_i = \frac{\exp((\log p(u_i|o,g) + \epsilon_i)/\tau)}{\sum_k \exp((\log p(u_k|o,g) + \epsilon_k)/\tau)}$$
- 训练中温度 $\tau$ 逐渐衰减，平衡探索与收敛。

**（3）异构解码器（Heterogeneous Decoders）**
- 每种构型配备一个轻量 MLP 解码头 $h_k$：
  $$\hat{a}^{(k)} = h_k(u^*, o)$$
- 共享视觉骨干（来自 VLM）抽取特征 $+ u^*$ 共同作为输入；
- 保持解码头小参数量，确保大部分学习发生在通用动作层。

**（4）训练目标**
- 在 $K$ 个异构数据集 $D = (D_1, ..., D_K)$ 上联合优化：
  $$\min_{U, \theta} \sum_{k=1}^{K} \mathbb{E}_{a_i \in \tau_i, \tau_i \in D_k} \mathcal{L}_k(\hat{a}^{(k)}, a_i^{(k)})$$
- $\mathcal{L}_k$ 可根据动作类型灵活选用 Cross-Entropy、MSE、Huber 或 Diffusion Loss；
- 共享参数（码本 $U$ + 提取器 $\theta$）跨域同步更新，解码头仅基于本域批次更新，类比元学习思想。

### 2.3 算法流程
1. VLM 编码图像与语言指令 → 抽取多模态特征；
2. 特征经 Tokenizer + Gumbel-Softmax 选择离散码字 $u^*$；
3. $u^*$ + 视觉特征输入对应构型的 MLP 解码头 → 输出该平台的连续/离散控制信号；
4. 对该构型真实动作做行为克隆损失，反向传播更新码本、提取器与解码头。

---

## 3. 实验设计

### 3.1 数据集
- 训练数据：来自 **Open-X Embodiment、LIBERO、Droid** 等开源集合，**约 100 万条演示**、**28 种不同构型**；
- 不做统一动作预处理（如将绝对 EEF 转相对、去除关节位置），保留原始动作异构性。

### 3.2 Benchmark 与对比方法

**（1）真实 WidowX 机器人（"开箱即用"评测）**
- 19 个任务 × 10 次试验 = 共 **190 次 rollout**；
- 评估维度：视觉、运动、物理、语义、语言接地（language grounding）泛化能力。

**（2）LIBERO 仿真基准（Franka 机器人）**
- 5 个任务套件：Spatial、Object、Goal、Long、-90；
- 共 **130 个任务**，每个任务 20 次试验。

**（3）新构型快速适应实验**
- 未在训练数据中出现的 **AIRBOT 真实机器人**；
- 测试 **4 种不同控制接口**（相对/绝对 EEF 位置、相对/绝对关节位置）；
- 仅使用 100 条演示进行微调。

**（4）新解码器扩展实验**
- 在 UniAct 冻结后接入 **ACT 解码器**，适配双手机械臂 AIRBOT（顶视 + 双腕视 + 本体感受）。

### 3.3 对比基线
- **Octo**（0.1B，主流开源通用策略）；
- **CrossFormer**（跨构型）；
- **OpenVLA**（7B，自回归离散动作）；
- **LAPA**（7B，基于无动作视频构造 latent action）；
- **LLaVA-OV-0.5B**（作为 VLM 基线，验证预训练有效性）；
- 注：基线均经过数据清洗去除异构性（如全部转相对 EEF），而 UniAct 不做此处理。

---

## 4. 资源与算力

- **GPU**：64 张 NVIDIA **A100**；
- **训练时长**：**10 天**（使用 DeepSpeed 加速）；
- **训练数据规模**：约 100 万条演示 / 28 种构型；
- **模型规模**：UniAct-0.5B（0.5B 参数）；
- **算力用途**：64 卡规模在 10 天内完成 100 万条异构数据的联合训练，资源消耗在大型 VLM/VLA 训练中属常规水平；
- 注：实验部分关于推理侧算力、单机部署成本未给出细节。

---

## 5. 实验数量与充分性

- **主实验**：3 大类（真实 WidowX、LIBERO 仿真、快速适应）+ 4 个 LIBERO 套件细分；
- **快速适应**：跨 4 种控制接口分别在"简单"和"困难"（带干扰物）两版任务上评估；
- **解码器扩展**：4 个双手机械臂任务对比 LLaVA-OV；
- **分析实验**：
  - 人工逐条检查 256 个码字在不同机器人上的解码行为，发现至少 **40% 完全一致**；
  - 通过可视化证明可"用通用动作 ID 直接操控机器人"（图 7）；
  - 统计不同任务/不同机器人的通用动作使用分布，计算 **JS 散度**：相同任务在不同机器人上的分布相近（0.34~0.60），不同任务在同机器人上的分布差异更大（0.44~0.58），验证通用动作确实抓住了"任务进展"而非构型细节；
- **消融实验**：未明确给出码本大小 N、维度 D、温度衰减策略等的独立消融，主要靠对比基线展示整体有效性；
- **公平性**：在 LIBERO 上，UniAct 与基线在任务、数据量、图像质量上完全对齐；基线为新构型收集 100 条专门演示并保证 OpenVLA 收敛到 95% 预测准确率；
- **充分性评价**：覆盖跨域（真实+仿真）、跨构型（含未见过机器人）、跨控制接口、多任务规模（130+19+4），整体较为充分；但消融维度和统计显著性检验（如多次种子）未充分呈现。

---

## 6. 主要结论与发现

1. **以小博大**：0.5B 的 UniAct-0.5B 在 WidowX 真实机器人和 LIBERO 仿真基准上**全面超越 14 倍参数量的 OpenVLA-7B 与 LAPA-7B**；
2. **通用动作空间有效**：相同通用动作在不同机器人上可解码为语义一致的行为（人工检查 256 个码字中至少 40% 完全一致）；
3. **任务进展驱动**：JS 散度分析表明通用动作使用分布对"任务"敏感、对"构型"不敏感，证明其编码的是任务级原子行为而非构型细节；
4. **快速适应新构型**：在新 AIRBOT 上，仅需 100 条演示、冻结主模型 + 训练 4 个 MLP 头（**仅 4M / 500M = 0.8%** 参数量）即可达到对比基线水平；
5. **可作为动作 Tokenizer**：通用动作空间是离散且语义对齐的，可直接用于规划、控制或下游更大基础模型的"动作词表"；
6. **统一抽象**：为大规模跨构型 VLA 训练提供了统一抽象层，避免数据清洗的工程负担。

---

## 7. 优点

- **问题切入精准**：聚焦动作异构性这一具身基础模型训练的核心瓶颈，而非停留在视觉/语言模态对齐层面；
- **信息瓶颈设计巧妙**：通过离散小码本强制不同机器人共享有限原子行为，天然促进跨构型泛化；
- **训练目标合理**：条件于语言目标 $g$，避免 latent action 路线（LAPA/IGOR/LAPO）将"场景视觉变化"误编码进动作；
- **部署友好**：解码头为轻量 MLP，新构型仅需训练极小参数即可适配，便于快速迁移；
- **与多种解码器兼容**：可灵活替换解码器（如接入 ACT），证明框架通用性；
- **实验维度全面**：同时覆盖真实+仿真、已知+未知构型、多种控制接口；
- **可视化强**：直接展示"用通用动作 ID 操控机器人"的可玩性，提供直观的语义可解释证据；
- **不依赖数据清洗**：相较基线需做大量动作归一化，UniAct 直接处理原始异构数据，更贴合真实多源数据场景。

---

## 8. 不足与局限

- **构型覆盖有限**：受算力与数据所限，主要在**单臂机器人**（WidowX、Franka、AIRBOT）上评估；论文中提到未来将扩展至双臂、导航与自动驾驶，但当前结果对该方向的支撑较弱；
- **消融不够充分**：缺少对码本大小 $N$、维度 $D$、Gumbel 温度衰减策略、不同 VLM 骨干等关键超参的单独消融，难以判断各组件贡献；
- **人工检查的可重复性问题**："至少 40% 码字完全一致"的判断依赖人工逐条核对，缺乏定量指标（如可重复执行成功率）与跨评估者一致性检验；
- **数据集选择偏差**：所有训练数据均来自英语世界的开源集合，对低资源语言或非标准演示风格（如 VR 遥操作 vs. 触觉示教）的覆盖不足；
- **统计显著性未明确**：未报告多次随机种子下的标准差或显著性检验，0.5B vs 7B 的胜出是否稳健需要进一步验证；
- **快速适应评测规模较小**：新构型实验仅 100 条演示、单一任务（堆叠方块）和 4 种控制接口，结论泛化到更复杂任务仍需验证；
- **Diffusion Loss 应用不深入**：训练目标中提及可用 Diffusion Loss，但实际实现细节和消融未充分展开；
- **缺乏安全性/失败分析**：未讨论模型在失败任务上的错误模式、对分布外指令的鲁棒性及安全约束；
- **算力信息不完整**：仅给出训练端 A100×64×10 天，推理延迟、单卡部署门槛、对实时控制的影响未涉及。

---

（完）
