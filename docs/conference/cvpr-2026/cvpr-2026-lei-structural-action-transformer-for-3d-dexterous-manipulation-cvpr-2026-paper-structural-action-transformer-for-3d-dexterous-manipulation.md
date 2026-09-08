---
title: Structural Action Transformer for 3D Dexterous Manipulation
title_zh: 面向三维灵巧操作的结构化动作Transformer
authors: "Lei, Xiaohan, Wang, Min, Weng, Bohong, Zhou, Wengang, Li, Houqiang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Lei_Structural_Action_Transformer_for_3D_Dexterous_Manipulation_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向灵巧操作的模仿学习，解决跨本体技能迁移难题
tldr: 本文研究面向高自由度灵巧手的模仿学习，重点解决跨本体技能迁移中三维空间关系建模困难的问题。现有方法多依赖二维观测和以时序为中心的动作表示，难以应对本体异构性。为此，作者提出了结构化动作Transformer（SAT），将每个动作块重新表达为可变长度、无序的关节级轨迹序列。该结构化建模使Transformer能够原生处理异构本体，提升了灵巧操作中的策略学习与迁移效果。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1773, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 836, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 861, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 860, \"height\": 347, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 850, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1699, \"height\": 216, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1722, \"height\": 170, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1785, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 845, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 816, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 779, \"height\": 360, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 815, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lei-structural-action-transformer-for-3d-dexterous-manipulation-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 864, \"height\": 356, \"label\": \"Table\"}]"
motivation: 模仿学习中二维观测与时序动作表示难以建模三维空间关系及本体异构性。
method: 提出SAT，将动作块建模为可变长无序的关节级轨迹序列以原生支持异构本体。
result: 在灵巧手跨本体模仿学习上提升了策略对高自由度操作的建模能力。
conclusion: 结构化视角为灵巧机器人操作的模仿学习提供了更通用的动作表征。
---

## Abstract
Achieving human-level dexterity in robots via imitation learning from heterogeneous datasets is hindered by the challenge of cross-embodiment skill transfer, particularly for high-DoF robotic hands. Existing methods, often relying on 2D observations and temporal-centric action representation, struggle to capture 3D spatial relations and fail to handle embodiment heterogeneity. This paper proposes the Structural Action Transformer (SAT), a new 3D dexterous manipulation policy that challenges this paradigm by introducing a structural-centric perspective. We reframe each action chunk not as a temporal sequence, but as a variable-length, unordered sequence of joint-wise trajectories. This structural formulation allows a Transformer to natively handle heterogeneous embodiments, treating the joint count as a variable sequence length. To encode structural priors and resolve ambiguity, we introduce an Embodied Joint Codebook that embeds each joint's functional role and kinematic properties. Our model learns to generate these trajectories from 3D point clouds via a continuous-time flow matching objective. We validate our approach by pre-training on large-scale heterogeneous datasets and fine-tuning on simulation and real-world dexterous manipulation tasks. Our method consistently outperforms all baselines, demonstrating superior sample efficiency and effective cross-embodiment skill transfer. This structural-centric representation offers a new path toward scaling policies for high-DoF, heterogeneous manipulators.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Structural Action Transformer for 3D Dexterous Manipulation" following a specific structure. Let me carefully analyze the paper and produce a comprehensive summary.

Let me organize the response according to the 8 points requested:
1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions and findings
7. Strengths
8. Limitations

I need to be thorough and detailed while keeping it concise. Let me extract the key information from the paper.

Key points:
- Problem: Cross-embodiment skill transfer in high-DoF dexterous hands using imitation learning from heterogeneous datasets
- Limitation of existing methods: 2D observations + temporal-centric action representation
- Method: SAT - Structural-centric representation (Da, T) instead of (T, Da)
- Embodied Joint Codebook: triplet (e, f, r) - Embodiment ID, Functional Category, Rotation Axis
- Flow matching objective for continuous-time normalizing flow
- DiT backbone with causal masking
- 3D point cloud + language input
- Pre-training on heterogeneous datasets (human + robot + simulation)
- Fine-tuning on Adroit, DexArt, Bi-DexHands
- Real-world bimanual tasks with xArm + xHand

Let me write this out in Chinese.</think>

# 面向三维灵巧操作的结构化动作 Transformer（SAT）——论文总结

## 一、核心问题与研究动机

- **核心问题**：如何让机器人从跨本体（cross-embodiment）、异构形态的高自由度灵巧手演示数据中学习，实现类人级别的灵巧操作能力。
- **现有方法的瓶颈**：
  - **观测维度**：主流 VLA/模仿学习方法主要依赖 **2D 图像**，难以捕捉灵巧操作中关键的 **3D 空间几何关系**与接触细节。
  - **动作表示**：普遍采用 **时序中心（temporal-centric）** 视角，把动作块建模为 `(T, D_a)` 序列，即每个时间步输出一个整体动作向量。这种"单体向量"式表示在 `D_a` 增大（如 7-DoF 臂 → 24-DoF 灵巧手）时：
    - 需要隐式学习关节间耦合，建模低效；
    - 形态不同则维度不可对齐，跨本体迁移缺乏天然机制。
- **研究意义**：在异构演示数据上预训练 + 下游任务微调，是当前"通用机器人策略"的核心路线；如何让动作表示本身支持跨本体，是这一路线的关键瓶颈。

---

## 二、方法论

### 2.1 核心思想：结构化中心（Structural-centric）表示

- 将动作块从 `(T, D_a)` 重新定义为 **`(D_a, T)`**：
  - 序列长度 = 关节数 `D_a`（**可变**，因本体而异）；
  - 每个 token = 单个关节在未来 `T` 步的**完整轨迹**；
  - 序列**无序**，借助 Transformer 自注意力天然处理。
- 关键收益：
  - 异构本体以**序列长度变化**统一表达，无需专门的 alignment 模块；
  - 时间作为特征维度，便于压缩每个关节的运动基元；
  - 自注意力可在不同本体的关节之间直接学习**功能对应关系**。

### 2.2 模型架构（三大组件）

1. **观察编码器（Observation Tokenizer）**：
   - 输入：过去 `T_o` 帧 3D 点云 + 自然语言指令；
   - 点云用 **FPS** 选 `M` 个局部中心，每中心取 `K` 近邻构成局部组，经 **PointNet** 提取局部几何 token；
   - 全局点云再走一个 PointNet 编码得到单条全局场景 token；
   - 训练时对局部 token 做随机打乱作为数据增强；
   - 语言指令用 **T5** 编码；最终拼接为 `tok_obs`。
2. **结构化动作编码器（Structural Action Tokenizer）**：
   - 噪声动作 `A_t^τ ∈ R^{D_a×T}` 沿关节维切成 `D_a` 个 token；
   - 共享 MLP 将每条轨迹从 `T` 维压缩到 `d_feat` 维；
   - **Embodied Joint Codebook**：每个关节 `j` 由三元组 `(e, f, r)` 描述——
     - `e`：本体 ID（如 ShadowHand、xHand）；
     - `f`：功能类别（CMC、MCP、PIP、DIP 等，借鉴人手解剖学）；
     - `r`：旋转主轴（屈伸、外展内收、旋前旋后）；
   - 三组查表嵌入相加得到结构嵌入 `C_j`，与动作 token 相加；
   - 跨本体共享功能/旋转轴 ⇒ 嵌入相似 ⇒ 利于迁移。
3. **结构化动作 Transformer（SAT 主干）**：
   - 基于 **DiT**（Diffusion Transformer）；
   - 注意力掩码：观察 token 自注意力内聚，动作 token 既关注所有观察 token 也关注其他动作 token；
   - 输出经最终 MLP 预测动作**速度场**。

### 2.3 训练目标：连续时间流匹配（Flow Matching）

- 把策略建模为条件 CNF：学习速度场 `v(A_t^τ, τ, o_t)`，把 `N(0, I)` 输运到动作分布；
- 优化目标：
  $$\mathcal{L}(\theta)=\mathbb{E}_{\tau, A_t^0, A_t^1}\left\|\epsilon_\theta(A_t^\tau,\tau,o_t)-(A_t^1-A_t^0)\right\|^2$$
  其中 `A_t^τ = (1-τ)A_t^0 + τA_t^1`，`τ~U[0,1]`；
- 推理时从噪声 `A_t^0` 沿 ODE 积分得到动作 chunk，使用 Euler 积分（**1-NFE**）即可。

---

## 三、实验设计

### 3.1 预训练数据（异构、跨本体）

- **人类演示**：HOI4D、Ego-Exo4D、Aria Digital Twin（提取 MANO 手部姿态）；
- **机器人演示**：Fourier ActionNet、DexCap；
- **仿真演示**：Bi-DexHands（PPO）、DexArt（PPO）、Adroit（VRL3），保留成功轨迹。

### 3.2 下游基准与任务

- **仿真基准（11 个任务）**：
  - **Adroit**（Shadow Hand，3 任务）；
  - **DexArt**（铰接物体操作，4 任务）；
  - **Bi-DexHands**（双臂灵巧操作，4 任务）；
  - 物理引擎：MuJoCo、IsaacGym。
- **真实世界**：双 7-DoF xArm + 双 12-DoF xHand，顶部 L515 LiDAR 采集点云；Meta Quest 3 + AnyTele 遥操；6 个任务（拔笔帽、递玩具、推箱取箱、放块入盘、刷杯子、抓篮球），每个 50 条演示。

### 3.3 对比方法

- **2D 基线**：Diffusion Policy (DP)、HPT、UniAct；
- **3D 基线**：3D Diffusion Policy (3DDP)、3D ManiFlow Policy；
- 全部使用官方实现，公平对比。

---

## 四、资源与算力

- 论文**未明确给出** GPU 型号、数量、训练时长等具体算力信息。
- 致谢中提及"USTC GPU 集群"与"MCC Lab + 超算中心"，但未公开具体规模或训练 wall-clock 时间。
- 仅给出模型规模：SAT 仅 **19.36 M** 参数（不含 T5），远小于 DP (266.8M)、UniAct (1053M)、3DDP (255.2M)、3D ManiFlow (218.9M)。

---

## 五、实验数量与充分性

- **基准对比**：11 个仿真任务 + 6 个真实任务，与 5 个强基线对比。
- **消融实验**（4 组）：
  1. 时序压缩维度 `d_feat` ∈ {16, 32, 64, 128, 256} 的参数/性能权衡；
  2. 预训练数据组合（仅人类 / 仅机器人 / 仅仿真 / 全量 + 数据规模 100% vs 10%）；
  3. 模型组件消融（去全局 token / 去局部 token / 去因果掩码 / 去关节嵌入 / 退回时序中心）；
  4. Embodied Joint Codebook 三元组各分量消融。
- **效率分析**：与 UniAct 在 10/50/100/500 条演示下对比少样本收敛速度。
- **可视化分析**：10 种常见灵巧手关节类型频次统计 + t-SNE 嵌入聚类图。
- **整体评价**：实验覆盖了**性能、效率、消融、可视化**四大维度，较为系统；但**缺少统计显著性检验**和**多随机种子方差**的更细致报告（仅给出 ±标准差），且真实世界每个任务仅 50 条演示且无重复次数说明。

---

## 六、主要结论与发现

- **核心结论**：将动作表示从时序中心切换为结构化中心，能显著提升高自由度灵巧操作策略的**跨本体迁移**能力与**样本效率**。
- **仿真性能**：SAT 在 11 个任务平均成功率 **0.71**，优于最强 3D 基线 3D ManiFlow (0.66) 与 2D 基线 UniAct (0.50)。
- **真实世界性能**：6 个任务均超过 HPT 与 3DDP，最显著提升在"推箱取箱"（0.05→0.35）与"刷杯子"（0.10→0.45）。
- **少样本优势**：10 条演示下已明显优于 UniAct，500 条演示下领先更多。
- **关键消融发现**：
  - **关节嵌入不可缺**：去掉后成功率从 0.71 → 0.01，因动作序列本身无序，无此嵌入 Transformer 无法辨识关节身份；
  - **功能类别**比本体 ID 与旋转轴更关键（去掉即崩）；
  - **仿真数据**预训练效果优于人类或机器人单独预训练，但**全混合**最优；
  - **人类数据**单独预训练反而**优于**机器人单独预训练，说明 Codebook 成功把人手功能映射到机器人。
- **压缩鲁棒性**：`d_feat=32` 即可保留几乎全部性能（0.71），证实轨迹存在高度冗余。
- **频率统计**：MCP/CMC/PIP 的屈伸关节在 10 种灵巧手中出现频次最高，是灵巧操作硬件设计的"核心功能集"。
- **嵌入可视化**：按本体 ID 和旋转轴聚类明显，按功能类别聚类较松散——表明迁移力来自 Codebook 的**组合结构**，而非单一嵌入相似。

---

## 七、优点与亮点

- **视角创新**：首次明确提出并实现**沿结构维度 token 化动作**的策略，把"跨本体"从输入侧对齐模块问题转化为 Transformer 序列长度自适应问题。
- **Embodied Joint Codebook 设计**：用 (本体, 功能, 主轴) 三元组构成可组合的结构先验，既显式编码异构先验，又支持解耦迁移。
- **效率显著**：参数量比主流 3D 基线小一个数量级，1-NFE 推理，部署友好。
- **数据多样性强**：人类 + 机器人 + 仿真三源预训练，验证异构数据互补性。
- **实验覆盖完整**：基准对比 + 多角度消融 + 少样本曲线 + 嵌入可视化 + 真实硬件部署。
- **少样本与可解释性兼顾**：通过 t-SNE 与频次统计提供直观的可解释性分析。

---

## 八、不足与局限

- **算力透明度低**：未公开 GPU 型号/数量/训练时长，复现成本难以估算。
- **真实世界评估规模小**：每任务仅 50 条演示、6 个任务，且未明确报告每轮试验次数，结果可信度受限。
- **传感器单一**：单 LiDAR 顶视点云，双臂/手物严重遮挡时缺乏多视角补偿，作者自承这是"失败模式"主因。
- **缺乏显著性检验**：标准差均基于少数随机种子，未提供统计显著性或多次独立运行的更严格方差。
- **动力学/触觉缺失**：异构本体间运动学/接触几何差异大时仍出现"动作分配错误"；缺乏力/触觉闭环。
- **任务类型偏窄**：仿真多为桌面灵巧任务，真实任务以桌面双臂为主；缺少移动、长序列、多刚体强接触等场景。
- **人类数据利用待深入**：仅作为预训练补充，未探索人类视频预训练 + 跨本体在线适配等更前沿范式。
- **码本依赖手工定义**：功能类别与旋转轴依赖人手解剖学的离散化标注，新本体需要人工注册，未给出自动发现机制。

（完）
