---
title: Learning to Act Robustly with View-Invariant Latent Actions
title_zh: 基于视角不变潜在动作的鲁棒行为学习
authors: "Jeong, Youngjoon, Chun, Junha, Kim, Taesup"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Jeong_Learning_to_Act_Robustly_with_View-Invariant_Latent_Actions_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: "面向视觉策略的潜在动作学习,提升鲁棒性"
tldr: "针对视觉机器人策略对视角变化敏感的问题,本文提出视角不变的潜在动作方法VILA。该方法建模跨轨迹的转移动态潜在动作,将视觉表征锚定于物理动力学而非外观特征,通过对齐不同视角下的潜在动作实现鲁棒泛化。实验表明在真实场景的视角变化下策略性能显著提升,为视角鲁棒的视觉运动学习提供了动力学驱动的新路径。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1580, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 805, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 808, \"height\": 322, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 753, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1809, \"height\": 760, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 725, \"height\": 412, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 655, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 743, \"height\": 332, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 732, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 877, \"height\": 913, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-to-act-robustly-with-view-invariant-latent-actions-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 746, \"height\": 613, \"label\": \"Table\"}]"
motivation: "视觉机器人策略在视角轻微变化下即出现性能下降,现有方法依赖外观多视角对齐而忽略物理动态。"
method: "提出VILA,学习刻画轨迹转移模式的潜在动作,并在不同视角间对齐该潜在动作以获得动力学驱动的视角不变表征。"
result: "在真实环境视角变化下显著提升策略鲁棒性与泛化能力,验证了物理动态对齐的有效性。"
conclusion: 为视觉运动策略提供了一种以物理动力学为基础的视角不变表征学习新范式。
---

## Abstract
Vision-based robotic policies often struggle with even minor viewpoint changes, underscoring the need for view-invariant visual representations. This challenge becomes more pronounced in real-world settings, where viewpoint variability is unavoidable and can significantly disrupt policy performance. Existing methods typically learn invariance from multi-view observations at the scene level, but such approaches rely on visual appearance and fail to incorporate the physical dynamics essential for robust generalization. We propose View-Invariant Latent Action (VILA), which models a latent action capturing transition patterns across trajectories to learn view-invariant representations grounded in physical dynamics. VILA aligns these latent actions across viewpoints using an action-guided objective based on ground-truth action sequences. Experiments in both simulation and the real world show that VILA-based policies generalize effectively to unseen viewpoints and transfer well to new tasks, establishing VILA as a strong pretraining framework that improves resilience to viewpoint shifts and downstream learning performance.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper "Learning to Act Robustly with View-Invariant Latent Actions" (VILA) following a specific structure with 8 points. Let me carefully analyze the paper content and organize the summary.

The paper is about:
1. VILA - a framework that learns view-invariant latent actions for robust visuomotor policies
2. Two-stage training: latent action learning + latent behavior cloning
3. Uses IDM (Inverse Dynamics Model) + FDM (Forward Dynamics Model) based on LAOM framework
4. Adds action-guided contrastive learning for view invariance
5. Tests on 5 RoboSuite tasks + real-world SO-ARM pick-and-place

Let me structure my response according to the 8 required points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I should provide a thorough, well-organized analysis in Markdown format.</think>

# 论文总结：基于视角不变潜在动作的鲁棒行为学习（VILA）

## 1. 核心问题与整体含义

### 1.1 研究背景
- 视觉机器人策略在部署时对相机视角变化极为脆弱，即便是微小的视角扰动也会显著降低策略性能，这成为真实场景落地的关键瓶颈。
- 真实场景下，相机位置、朝向变化不可避免，视角多样性是制约视觉运动策略（visuomotor policy）泛化的核心挑战。

### 1.2 现有方法的局限
- **观测层面方法**（如 NVS 视角合成、几何条件输入）：依赖多相机大规模数据集，数据获取成本高昂，且扩展性差。
- **表征层面方法**（如场景级不变特征学习）：要求单一紧凑特征向量整张图像的布局与背景信息，同时承载任务相关的运动信息。这种"全场景级"不变性要求过于宽泛，未能显式区分静态场景与动力学动作。

### 1.3 研究动机
- 论文的核心洞察：**视角不变性应当施加于动力学层面（场景变化）而非整个场景级视觉表征**，因为表征变化比表征场景本身更紧凑，且更聚焦于智能体与物体的运动。
- 因此提出 VILA（View-Invariant Latent Action），将潜在动作作为视角鲁棒性的接口。

---

## 2. 方法论

### 2.1 整体框架
VILA 包含两阶段训练：
1. **潜在动作学习阶段**：学习紧凑的、由动作引导的、视角不变的动态表征。
2. **潜在行为克隆阶段**：训练一个潜在策略 π_z（输入当前观测，预测潜在动作），将其用作视角不变的视觉编码器，去条件化下游的视觉运动策略。

### 2.2 基座潜在动作学习（基于 LAOM）
- 使用逆动力学模型（IDM）从连续观测推断潜在动作：
  - $z_t^v = \text{IDM}(s_t^v, s_{t+k}^v)$
- 使用前向动力学模型（FDM）预测未来特征：
  - $\hat{s}_{t+k}^v = \text{FDM}(s_t^v, z_t^v)$
- 时序一致性损失 $L_{LA}$ 为预测特征与目标编码器（EMA 权重）特征的 MSE。
- 上标 $v$ 表示视角，下标 $t$ 表示时间，$k \in \{1,...,K\}$ 为时间偏移。

### 2.3 动作引导的潜在动作不变性（核心创新）
**训练批次构造**：
- 采样偏移 $k$，采样 $N$ 个基准时间索引 $\{t_i\}_{i=1}^N$，每个索引采样 $V$ 个视角，得到 $B = N \cdot V$ 个潜在动作样本。
- 关键创新：**利用真实动作（GT action）序列作为监督信号**（多视角机器人学习场景下天然可获取）。

**加权 InfoNCE 对比损失（$L_{W\text{-}NCE}$）**：
- 首先定义两个 GT 动作序列的归一化 Frobenius 距离：
  - $d_{ij} = \|A_i^{GT} - A_j^{GT}\|_F^2 / (kD)$
- 将距离转换为软权重（$w_{ij}$），即基于相似度做 softmax，温度参数为 $\beta$。
- 应用监督对比学习损失（Weighted InfoNCE），使潜在动作在 GT 动作相似时彼此接近。

**结构对齐损失（$L_{struct}$）**：
- 将 GT 动作序列展开为向量，与潜在动作各自做 L2 归一化。
- 构造两者的余弦相似度矩阵 $S_z = \hat{Z}\hat{Z}^\top$ 与 $S_{GT} = \hat{A}\hat{A}^\top$。
- 最小化两个相似度矩阵之间的 Frobenius 距离，对齐全局结构。

**总损失**：
$$L_{VILA} = L_{LA} + \lambda_1 L_{W\text{-}NCE} + \lambda_2 L_{struct}$$

### 2.4 潜在行为克隆
- 冻结 IDM，训练潜在策略 $\pi_z$ 使其从当前观测预测潜在动作：
  - $L_{BC} = \|\pi_z(s_t^v) - \text{IDM}(s_t^v, s_{t+k}^v)\|_2^2$
- 由于 $\pi_z$ 在预训练的潜在动作空间中运行，自然继承了视角不变、结构化的特性。
- 在下游微调时，$\pi_z$ 的输出作为下游扩散策略（Diffusion Policy）的条件。

---

## 3. 实验设计

### 3.1 数据集与场景
**仿真环境**（基于 RoboSuite）：
- Lift：简单方块抓举（RoboMimic）
- Square：精准抓取放置（RoboMimic）
- Stack Three：多块堆叠（MimicGen）
- Coffee：咖啡胶囊入机并关闭（MimicGen）
- Mug Cleanup：打开柜子、放杯子入柜并关闭（MimicGen）

**多视角构造**：
- 在 agentview 基础上定义 5×5 网格，覆盖方位角偏移 $[-90°,+90°]$ 与俯仰角偏移 $[-15°,+15°]$。
- 25 个视角中，10 个用于训练，15 个用于评估。
- 还测试了外推视角（超出训练网格 ±2°）。

**真实环境**：
- SO-ARM101 机器人执行抓块放入杯子的任务。
- 采用 ZeroNVS 对单视角视频做视角增强，组合得到 27 个视角（方位 ±5°、垂直 ±5cm、光轴 ±5cm）。
- 4 个视角训练，3 个视角测试。

### 3.2 基线方法
- **Vanilla**：直接使用 ImageNet 预训练 ResNet-18 编码器。
- **Vanilla + 数据增强**（3 种）：Crop、Aug-Str、Aug-Wk。
- **CLASS**：基于 GT 动作序列距离的加权 InfoNCE 场景级编码器。
- **ReViWo**：通过分解多视角观测学习视角不变场景表征。
- **KYC（Know Your Camera）**：将相机内参与外参作为策略条件输入。
- **VLA 模型**（仅真实实验）：π0.5、SmolVLA，从官方 LeRobot checkpoint 微调。

### 3.3 评估协议
- 所有基线共享相同的下游 Diffusion Policy、超参数与训练流程，仅编码器预训练策略不同。
- 仿真每视角评估 20 个 episode，真实环境每视角评估 10 个 episode。
- 两种下游设置：
  - **冻结设置**：编码器固定，仅训练策略。
  - **微调设置**：编码器与策略联合更新。
- 报告指标：训练视角成功率、未见视角成功率、二者之比 Rel.。

---

## 4. 资源与算力

- 论文**未明确说明** GPU 型号、数量、训练时长等算力信息。
- 仅提到图像分辨率 64×64、潜在特征维度 128 等模型规模参数。
- 训练流程使用相同的下游策略（Diffusion Policy）超参数。

---

## 5. 实验数量与充分性

### 5.1 实验规模
- **仿真主实验**：5 个任务 × 2 种设置（冻结/微调）× 25 个视角（10 seen + 15 unseen）× 20 episodes，覆盖 seen / unseen 成功率及 Rel. 比值。
- **外推视角实验**：4 个任务 × 8 个外推视角 × 20 episodes。
- **真实环境实验**：3 个未见视角 × 10 episodes 对比 5 个基线（含 VLA 模型）。
- **跨任务适应实验**：将 Stack Three 编码器迁移到 Coffee 任务，对比不同标注数据预算下的表现。
- **消融实验**（Lift 任务）：
  - 损失函数消融（5 种组合）。
  - 动作序列距离度量（DTW vs L2）。
  - 偏移采样策略（4 种）。
  - 潜在动作维度（4 种：32/64/256/512）。

### 5.2 分析性实验
- **表示质量分析**：基于 k=50 近邻的视角熵与动作熵，对比各方法在 25 视角上的混合度与动力学聚类程度。
- **动作-结果失配分析**：在 Square 任务上对比 VILA 与 CLASS 在卡住-运动配对上的潜在空间分离度。

### 5.3 充分性评价
- 实验设计**较为充分**，覆盖仿真与真实环境、多种任务、可见/未见/外推视角，并提供了多个分析维度。
- 控制变量严格：所有基线共享相同的下游策略与训练流程，确保对比公平。
- 评估指标丰富，包含 Rel. 比值和外推视角，对泛化能力评估较为严格。

---

## 6. 主要结论与发现

### 6.1 主要结论
- VILA 在所有 5 个仿真任务的未见视角上均取得最佳成功率；在冻结设置中，VILA 是少数能在未见视角保持非平凡性能的方法。
- 在外推视角（超出训练范围）下，VILA 仍能保持有意义的成功率，而基线方法基本失败。
- 真实环境中 VILA 平均成功率 63.33%，显著优于所有基线（含 π0.5 与 SmolVLA 等 VLA）。
- 跨任务适应：在 Stack Three → Coffee 迁移中，VILA 在所有数据预算下均提供比 Vanilla 更强的先验，而其他场景级不变性方法往往不如从头训练。

### 6.2 关键发现
- **动力学中心的不变性优于场景级不变性**：仅对动力学变化（潜在动作）施加不变性，可同时实现视角鲁棒性与任务适应性。
- **GT 动作作为软对齐信号比作为回归目标更有效**：直接回归动作反而损害未见视角性能。
- **结构对齐与加权对比损失互补**：单独使用任一组件均不足以达到完整性能。
- **潜在动作维度 128 是最佳平衡点**：过小或过大都会降低性能。
- **偏移采样范围 1–10 最佳**：固定偏移或过大偏移均会降低性能。
- **VILA 在动作-结果失配场景下分离度更高**：相比 CLASS 的场景级方法，VILA 能更好地区分"相似动作导致不同结果"的情形。

---

## 7. 优点

- **方法论创新点突出**：将视角不变性从场景级推向动力学级（潜在动作），思路清晰且有理论支撑。
- **GT 动作监督的引入贴合实际**：多视角机器人数据天然包含动作日志，利用其为对比学习提供软监督信号。
- **结构对齐 + 加权对比的双损失设计**：兼顾局部对比（Weighted InfoNCE）与全局结构（相似度矩阵对齐）。
- **实验设计全面且公平**：统一下游策略、严格控制变量、覆盖仿真与真实、可见与未见及外推视角，并对比 VLA 基线。
- **分析实验深入**：视角熵、动作熵、动作-结果失配分析等超越单纯性能指标。
- **消融充分**：损失函数、距离度量、采样策略、潜在维度等多维度均做了验证。

---

## 8. 不足与局限

### 8.1 方法层面
- **依赖多视角观测**：仿真实验假设可同时获得多视角数据；真实场景下需借助 ZeroNVS 做视角增强，这意味着部分性能可能依赖于底层 NVS 模型的可靠性。
- **依赖 GT 动作日志**：对比学习权重依赖真实动作序列；若动作空间不可用或动作噪声较大，方法可能受限。
- **限定于相机位姿变化**：未覆盖光照、背景、物体外观等其他视觉分布变化。

### 8.2 实验层面
- **真实实验任务单一**：仅在 SO-ARM101 抓块入杯任务上做验证，缺少更多真实任务与机器人平台的迁移性验证。
- **训练视角相对较少**：仿真中 25 视角但训练仅 10 个，作者声称比以往基线更具挑战性，但实际是否能扩展到更大规模数据集（如真实机器人大规模数据）尚不清楚。
- **VLA 基线对比局限**：仅与 π0.5、SmolVLA 在单任务上对比，未涵盖更多 VLA 模型。
- **算力信息缺失**：未报告 GPU 型号、数量、训练时长，限制了对计算成本与可复现性的评估。
- **与无监督潜在动作方法的对比**：未与 LAOM（基座方法）、LAPA、VideoWorld 等无动作日志设置下的方法进行系统对比，可能无法清晰划分 VILA 的增益中"GT 动作监督"与"多视角对齐"的贡献。

### 8.3 应用层面
- 当前方法主要针对固定桌面操作任务，对长时序、移动机器人、动态环境等场景的适用性未验证。
- 多视角数据获取仍是推广瓶颈，尤其在工业或野外场景中部署难度较大。

（完）
