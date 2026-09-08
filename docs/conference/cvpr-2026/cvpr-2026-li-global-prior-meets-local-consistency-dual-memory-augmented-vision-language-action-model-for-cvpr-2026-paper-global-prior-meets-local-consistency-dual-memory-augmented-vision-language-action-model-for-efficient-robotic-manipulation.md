---
title: "Global Prior Meets Local Consistency: Dual-Memory Augmented Vision-Language-Action Model for Efficient Robotic Manipulation"
title_zh: "全局先验结合局部一致性:面向高效机器人操纵的双记忆增强视觉-语言-动作模型"
authors: "Li, Zaijing, Hu, Bing, Shao, Rui, Chen, Gongwei, Jiang, Dongmei, Xie, Pengwei, Hao, Jianye, Nie, Liqiang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Li_Global_Prior_Meets_Local_Consistency_Dual-Memory_Augmented_Vision-Language-Action_Model_for_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向通用机器人操纵的视觉-语言-动作模型
tldr: "针对现有层次化视觉-语言-动作模型在机器人操纵任务中推理效率低与鲁棒性差两大瓶颈,本文提出双记忆增强的VLA框架。该方法通过注入全局先验并强化动作生成的局部一致性,缓解分布失配与历史信息缺失问题。在复杂操纵基准上的实验表明,所提方法显著提升了推理效率与任务鲁棒性,推动了面向通用机器人的视觉-动作模型实用化。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 900, \"height\": 923, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1790, \"height\": 794, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1802, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 908, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1799, \"height\": 885, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 684, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 869, \"height\": 636, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1815, \"height\": 567, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 906, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-global-prior-meets-local-consistency-dual-memory-augmented-vision-language-action-model-for-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 183, \"label\": \"Table\"}]"
motivation: 现有VLA模型在动作生成阶段受限于噪声先验与目标分布差距大、推理效率低、鲁棒性差等问题。
method: "提出双记忆模块同时建模全局先验与局部一致性,改进层次化VLA的动作生成过程。"
result: 在操纵任务中显著降低去噪步数并提升策略鲁棒性与成功率。
conclusion: 为通用机器人操纵提供了更高效、更鲁棒的视觉-语言-动作生成方案。
---

## Abstract
Hierarchical Vision-Language-Action (VLA) models have rapidly become a dominant paradigm for robotic manipulation. It typically comprising a Vision-Language backbone for perception and understanding, together with a generative policy for action generation. However, its performance is increasingly bottlenecked by the action generation proceess. (i) Low inference efficiency. A pronounced distributional gap between isotropic noise priors and target action distributions, which increases denoising steps and the incidence of infeasible samples. (ii) Poor robustness. Existing policies condition solely on the current observation, neglecting the constraint of history sequence and thus lacking awareness of task progress and temporal consistency. To address these issues, we introduce OptimusVLA, a dual-memory VLA framework with Global Prior Memory (GPM) and Local Consistency Memory (LCM). GPM replaces Gaussian noise with task-level priors retrieved from semantically similar trajectories, thereby shortening the generative path and reducing the umber of function evaluations (NFE). LCM dynamically models executed action sequence to infer task progress and injects a learned consistency constraint that enforces temporal coherence and smoothness of trajectory. Across three simulation benchmarks, OptimusVLA consistently outperforms strong baselines: it achieves 98.6% average success rate on LIBERO, improves over pi_0 by 13.5% on CALVIN, and attains 38% average success rate on RoboTwin 2.0 Hard. In Real-World evaluation, OptimusVLA ranks best on Generalization and Long-horizon suites, surpassing pi_0 by 42.9% and 52.4%, respectively, while delivering 2.9x inference speedup.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze this paper about OptimusVLA (a dual-memory VLA framework for robotic manipulation) and produce a structured Chinese summary following specific guidelines. Let me organize my analysis according to the 8 requested points.

Let me carefully review the paper:

1. **Core problem/motivation**: The paper addresses two bottlenecks in hierarchical VLA models:
   - Low inference efficiency due to large gap between isotropic Gaussian noise prior and target action distribution
   - Poor robustness due to Markovian assumption - only conditioning on current observation, ignoring history

2. **Methodology**: 
   - OptimusVLA framework with two memory modules:
     - **GPM (Global Prior Memory)**: 
       - Prior Head: MLP projects multimodal embedding to retrieval token z_re
       - Memory Bank: stores M key-value pairs of task embeddings and trajectories, retrieves k nearest via cosine similarity
       - Prior-Aware Sampler: samples with adaptive noise scale λ and adaptive NFE N
       - Equations: λ = λmax - (s̄+1)/2 * (λmax - λmin), N = Nmin + (1 - (s̄+1)/2) * (Nmax - Nmin), X̂_t = μ + λ(ε ⊙ √Var)
     - **LCM (Local Consistency Memory)**:
       - Consistency Layer: self-attention on action chunk
       - Dynamic Awareness Module: Mamba-based structure
       - Injects consistency bias B_t as additive constraint

3. **Experiments**:
   - Datasets/benchmarks: LIBERO, CALVIN, RoboTwin 2.0, real-world (GALAXEA R1 Lite)
   - Baselines: DP, Octo, SpatialVLA, π0-FAST, CogACT, MemoryVLA, OpenVLA-OFT, OpenVLA, UniVLA, π0, π0.5, RDT, ACT, DP3, RoboVLM, ReconVLA, UP-VLA, RoboDual, Seer, VPP

4. **Resources**:
   - 8× NVIDIA A800 GPUs
   - Global batch size 512
   - 30,000 training steps
   - Learning rate 5e-5
   - 3.6B parameters

5. **Experiment count/sufficiency**:
   - Three simulation benchmarks + real-world
   - LIBERO with 4 suites, 500 rollouts each
   - CALVIN ABC→D
   - RoboTwin 2.0 with 7 tasks under Hard setting, 100 rollouts
   - Ablation studies on GPM and LCM
   - Memory size ablation
   - Training efficiency comparison
   - Inference efficiency comparison
   - Qualitative analysis

6. **Main conclusions**:
   - 98.6% SR on LIBERO
   - 13.5% improvement over π0 on CALVIN (4.45 avg length)
   - 38% SR on RoboTwin 2.0 Hard
   - 42.9% improvement on real-world generalization, 52.4% on long-horizon
   - 2.9× inference speedup
   - 6.5× faster inference time and 3.1× fewer NFEs on LIBERO

7. **Strengths**:
   - Dual memory design addresses both efficiency and robustness
   - Memory bank is interpretable and adaptive
   - Adaptive NFE based on similarity
   - LCM is lightweight (Mamba-based linear complexity)
   - Comprehensive evaluation across simulators and real-world
   - Fast training convergence

8. **Limitations**:
   - Memory bank size matters (need to store many trajectories)
   - Single retrieval seed per query
   - Limited to hierarchical VLA architecture
   - Real-world evaluation only on one robot platform (GALAXEA R1 Lite)
   - Dependence on good task embeddings for retrieval
   - Memory bank needs to be maintained/updated

Let me write this up in Chinese Markdown format.</think>

# OptimusVLA 论文结构化总结

## 一、核心问题与研究动机

### 1. 研究背景
- 层次化 **Vision-Language-Action (VLA)** 模型已成为机器人操纵的主流范式，由 **Vision-Language 骨干**（负责感知与理解）与 **生成式策略**（负责动作生成，通常基于扩散/流匹配）组成。
- 尽管视觉-语言预训练模型和生成式策略近年来发展迅速，**动作生成阶段**已成为整个 VLA 流水线的瓶颈。

### 2. 现存两大瓶颈
- **瓶颈一：推理效率低。** 当前主流方法从**各向同性高斯噪声**出发，经过多步去噪才能到达结构化目标动作分布，先验–目标分布差距（prior–target gap）大，导致：
  - 函数评估次数（NFE）居高不下；
  - 随机起点常落在运动学不可行的区域。
- **瓶颈二：时间依赖性差（鲁棒性差）。** 现有策略通常基于**马尔可夫假设**，仅以当前观测为条件，忽略了历史轨迹约束，导致：
  - 难以区分视觉相似但任务阶段不同的状态（如"未打开的抽屉"与"刚关闭的抽屉"）；
  - 控制抖动、轨迹不连贯；
  - 简单地拼接历史观测又会引入较大推理开销，并破坏 VLA 单帧预训练分布。

---

## 二、方法论：OptimusVLA 框架

### 1. 总体架构
OptimusVLA 在标准层次化 VLA（π0.5 风格）基础上引入**双记忆模块**：
- **Global Prior Memory (GPM)**：解决先验–目标差距，提升生成效率；
- **Local Consistency Memory (LCM)**：注入局部一致性与进度感知，提升鲁棒性。

### 2. Global Prior Memory (GPM)
将"先验初始化"重新定义为**基于记忆的检索问题**，从语义相似轨迹中检索任务级先验，替代高斯噪声。

**关键组件：**
- **Prior Head**：轻量 MLP，将多模态嵌入 $E_{emb}$ 映射为检索 token $z_{re}$。
- **Memory Bank**：存储 $M$ 组 (任务嵌入 $z_m$, 完整轨迹 $J_m$) 键值对，基于余弦相似度检索 top-$k$ 个最近邻 $\{J_i, s_i\}_{i=1}^k$，得到 softmax 权重 $\alpha_i = \text{softmax}(s_i/\tau_s)$。
- **任务级先验构造**：以滑动窗口从检索轨迹中抽取动作块 $C_i \in \mathbb{R}^{H \times A}$，通过加权平均得到高斯分布 $\mathcal{N}(\mu, \text{diag}(\text{Var}))$：
  $$\mu = \sum_{i=1}^k \alpha_i C_i, \quad \text{Var} = \sum_{i=1}^k \alpha_i (C_i - \mu)^2$$
- **Prior-Aware Sampler**：根据全局相似度 $\bar{s}$ 自适应调整噪声尺度 $\lambda$ 和 NFE $N$：
  $$\lambda = \lambda_{\max} - \frac{\bar{s}+1}{2}(\lambda_{\max} - \lambda_{\min}),\quad N = N_{\min} + \left(1 - \frac{\bar{s}+1}{2}\right)(N_{\max} - N_{\min})$$
  $$\hat{X}_t = \mu + \lambda(\varepsilon \odot \sqrt{\text{Var}}),\ \varepsilon \sim \mathcal{N}(0, I)$$

**作用**：将生成起点拉到目标流形附近，大幅减少 NFE 与不可行采样，同时通过自适应噪声保留多样性。

### 3. Local Consistency Memory (LCM)
作为轻量级工作记忆，为策略提供进度感知与时间一致性，**无需修改 VLA 预训练范式**。

**关键组件：**
- **Consistency Layer**：对最近一个动作块 $A_{t-1} = [a_{t-H+1}, \ldots, a_t]$ 使用 **Self-Attention** 捕获块内动作间依赖，输出 $\hat{B}_{t-1}$。
- **Dynamic Awareness Module**：采用 **Mamba 结构**（线性复杂度）建模跨块长期时序依赖，输出下一时刻一致性偏置 $B_t$。
- **注入方式**：将 $B_t$ 以加性偏置形式叠加到 GPM 采样的初始化上：
  $$X_t = \hat{X}_t + B_t$$
  再交给 flow policy $p_\theta$ 生成最终动作块 $a_{t+1:t+H}$。

### 4. 训练策略（三阶段）
1. 按 π0.5 的流程预训练层次化 VLA；
2. 用 **InfoNCE** 损失训练 Prior Head 学习任务判别性表示：
   $$\mathcal{L}_{\text{GPM}} = -\mathbb{E}_q\left[\log \frac{\exp(\text{sim}(z_{re}, z^+)/\tau_c)}{\sum_{j \in N(q)} \exp(\text{sim}(z_{re}, z_j)/\tau_c)}\right]$$
3. 冻结 GPM，训练 LCM 预测残差 $B_t^* = A_t^* - \mu_t$（真实动作与全局先验均值的差），采用 MSE 损失。

---

## 三、实验设计

### 1. 仿真基准（3 个）
- **LIBERO**：包含 Spatial / Object / Goal / Long 四套任务，每套 10 个任务，500 次 rollout/套；
- **CALVIN**：ABC→D 跨环境泛化测试，500 次 rollout，记录 5 个子任务成功率与平均完成长度；
- **RoboTwin 2.0 Hard**：随机选 7 个任务、100 次 rollout，包含双臂操作测试。

### 2. 真实世界
- **平台**：GALAXEA R1 Lite（14-DoF 双臂），腕部 + 第三视角相机，224×224 分辨率；
- **Generalization Tasks**：每任务 100–150 条专家演示，50 次 rollout（含光照、场景扰动）；
- **Long-horizon Tasks**：每任务 200–300 条演示，25 次 rollout。

### 3. 主要对比方法
DP、Octo、SpatialVLA、π0-FAST、CogACT、MemoryVLA、OpenVLA-OFT、OpenVLA、UniVLA、π0、π0.5、RDT、ACT、DP3、RoboVLM、ReconVLA、UP-VLA、RoboDual、Seer、VPP 等近 20 种当前 SOTA 方法。

---

## 四、资源与算力

- **GPU**：8 × **NVIDIA A800**；
- **总参数量**：约 **3.6B**（基于 π0.5 初始化 + GPM + LCM）；
- **全局 Batch Size**：512；
- **训练步数**：30,000 步；
- **学习率**：在 LIBERO、CALVIN、RoboTwin 上均为 $5\times10^{-5}$；
- **推理效率**：在 LIBERO 上达到 **6.5× 推理时间加速**、**3.1× NFE 减少**；在真实世界达到 **2.9× 推理加速**。

> 注：论文未明确披露每步训练时长、单 GPU 利用率、单次完整训练耗时及能耗等细节。

---

## 五、实验数量与充分性

### 1. 实验覆盖
- **3 个仿真基准 + 1 个真实世界平台**；
- **主结果表**：LIBERO（4 套任务）、CALVIN（5 子任务）、RoboTwin 2.0（7 任务）；
- **真实世界**：Generalization 与 Long-horizon 两类任务，多种扰动；
- **消融实验**：
  - GPM / LCM 各组件单独移除的消融（Table 4）；
  - Memory Bank 大小 $N_{um}$ 与检索数 $k$ 的影响（Table 5）；
- **效率分析**：
  - 训练效率对比（图 4）；
  - 推理效率对比（时间、NFE，图 5）；
- **定性分析**（图 6）：仿真任务展示 $\bar{s}$、$\lambda$、$N$ 的自适应变化；真实世界任务展示 LCM 对视觉相似阶段差异的区分能力。

### 2. 客观性评估
- **优点**：覆盖了仿真 + 真实世界；baseline 数量多且包含近期 SOTA（π0/π0.5、MemoryVLA、OpenVLA-OFT 等）；消融较为系统；同时给出任务级细节与综合指标。
- **不足**：真实世界仅在单一平台（GALAXEA R1 Lite）评估，未覆盖其他机器人形态；某些 baseline 结果来自论文复现（带 † 标记），可能存在复现偏差；rollout 次数（尤其真实世界 25–50 次）统计显著性有限。

---

## 六、主要结论与发现

1. **性能领先**
   - **LIBERO**：平均成功率 **98.6%**，超过 π0.5（96.9%）与 MemoryVLA（96.7%）；
   - **CALVIN (ABC→D)**：平均完成长度 **4.45**，较 π0 提升 **13.5%**；
   - **RoboTwin 2.0 Hard**：平均成功率 **38%**，在 Stack Bowls Two 任务达 58%，较 RDT 提升 +28%；
   - **真实世界 Generalization**：85.0%，较 π0 提升 **42.9%**；
   - **真实世界 Long-horizon**：64.0%，较 π0 提升 **52.4%**。

2. **效率显著提升**
   - LIBERO 上推理时间 **6.5× 加速**，NFE **3.1× 减少**（3.2 vs. 10.0）；
   - 真实世界 **2.9× 推理加速**；
   - 训练收敛更快：LIBERO-Goal 在 18,000 步即达 97.6%，而 π0.5 需 26,000 步。

3. **组件贡献明确**
   - GPM 主要带来泛化与效率增益（CALVIN -3.8%、真实世界泛化 -9.4%）；
   - LCM 主要带来长时序一致性增益（LIBERO-Long -1.7%）。

4. **记忆库设计经验**
   - 库容量与检索数 $k$ 都对性能有显著影响：$k=8$、充足库容量下表现最佳，过小 $k$ 易过拟合于单条轨迹。

---

## 七、优点 / 方法与实验亮点

- **问题定义清晰**：准确识别出当前 VLA 在动作生成阶段的两个核心瓶颈（效率与时序依赖），并给出定量与定性证据；
- **双记忆设计新颖**：将"先验初始化"重定义为记忆检索问题，避免了直接用动作先验导致的"模式坍缩"，同时保留噪声注入的探索性；
- **自适应机制**：根据检索相似度动态调整噪声尺度 $\lambda$ 和 NFE $N$，在高相似度任务上大幅加速；
- **LCM 轻量化**：采用 Self-Attention（块内）+ Mamba（块间）组合，以线性复杂度建模时序，避免了每次更新都触发 VLM 前向；
- **不破坏预训练范式**：GPM/LCM 以附加模块形式注入，不修改 VLA 原始输入分布，便于复用现有预训练权重；
- **实验较全面**：3 仿真 + 1 真实世界、近 20 个 baseline、含消融、效率分析、定性可视化；
- **可视化说服力强**：图 6 同时展示了 GPM 自适应参数变化与 LCM 区分相似视觉状态的能力。

---

## 八、不足与局限

### 1. 方法层面
- **依赖记忆库质量**：性能与 Memory Bank 容量、覆盖度强相关；任务分布变化时需更新记忆库；
- **检索粒度有限**：仅基于检索 token $z_{re}$ 的余弦相似度进行 top-$k$ 检索，缺乏更细粒度的语义匹配；
- **LCM 仅用最近一个动作块**：窗口长度固定，对更长历史信息利用有限；
- **仅适用于层次化 VLA**：依赖 flow policy 生成动作块，对自回归式 VLA 直接迁移性未验证。

### 2. 实验层面
- **真实世界规模有限**：仅在 GALAXEA R1 Lite 一个平台评估，未涵盖不同机器人形态；
- **真实世界 rollout 数量偏少**：每任务 25–50 次，统计置信度有限；
- **部分 baseline 为复现结果**（带 † 标记），可能存在复现偏差；
- **缺乏失败案例系统分析**：未对失败模式进行细分（如长尾任务、对抗扰动等）；
- **未明确报告训练时长/能耗**，也未充分分析在极端边缘设备上的部署可行性。

### 3. 应用层面
- 对**未见任务语义分布外**的泛化能力仍可能受限于记忆库的覆盖范围；
- 在**动态环境或多人协作场景**下的表现尚待验证。

（完）
