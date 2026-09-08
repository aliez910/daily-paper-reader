---
title: Bootstrap Dynamic-Aware 3D Visual Representation for Scalable Robot Learning
title_zh: AFRO：面向可扩展机器人学习的三维动力学感知视觉表示
authors: "Liang, Qiwei, Cai, Boyang, Lai, Minghao, Zhuang, Sitong, Lin, Tao, Qin, Yan, Ye, Yixuan, Liang, Jiaming, Xu, Renjing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liang_Bootstrap_Dynamic-Aware_3D_Visual_Representation_for_Scalable_Robot_Learning_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 自监督三维动力学感知表示，面向可扩展的机器人视觉运动学习
tldr: 现有三维视觉预训练方法在识别与分割任务上表现良好，却在机器人操作中表现欠佳。本文认为原因在于缺乏状态-动作-状态动力学建模以及显式几何重建的冗余。AFRO以自监督方式将状态预测建模为生成扩散过程，并在共享潜空间中联合建模前向与逆向动力学。该方法显著提升了可扩展机器人视觉运动学习的表示质量与稳定性。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1814, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1807, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 833, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 827, \"height\": 604, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1815, \"height\": 454, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 876, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 872, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 867, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 867, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 858, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 861, \"height\": 650, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1789, \"height\": 576, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1814, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liang-bootstrap-dynamic-aware-3d-visual-representation-for-scalable-robot-learning-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 459, \"label\": \"Table\"}]"
motivation: 现有3D视觉预训练方法因缺乏动力学建模而在机器人操作中表现受限。
method: 提出自监督框架AFRO，以扩散过程联合建模前向与逆向动力学并抑制特征泄露。
result: 在多种机器人操作任务上提升了表示质量与策略学习稳定性。
conclusion: 该工作为可扩展的机器人视觉运动学习提供了新的表示预训练范式。
---

## Abstract
Despite strong results on recognition and segmentation, current 3D visual pre-training methods often underperform on robotic manipulation. We attribute this gap to two factors: the lack of state-action-state dynamics modeling and the unnecessary redundancy of explicit geometric reconstruction. We introduce AFRO, a self-supervised framework that learns dynamics-aware 3D representations without action or reconstruction supervision. AFRO casts state prediction as a generative diffusion process and jointly models forward and inverse dynamics in a shared latent space to capture causal transition structure. To prevent feature leakage in action learning, we employ feature differencing and inverse-consistency supervision, improving the quality and stability of visual features. When combined with Diffusion Policy, AFRO substantially increases manipulation success rates across 16 simulated and 4 real-world tasks, outperforming existing pre-training approaches. The framework also scales favorably with data volume and task complexity. Qualitative visualizations indicate that AFRO learns semantically rich, discriminative features, offering an effective pre-training solution for 3D representation learning in robotics. Project page: https://kolakivy.github.io/AFRO/

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "AFRO: Bootstrap Dynamic-Aware 3D Visual Representation for Scalable Robot Learning" following 8 specific points. Let me organize the content from the paper into a structured Markdown format.

Let me analyze the paper carefully:

1. Core problem: 3D visual pre-training methods work well on recognition/segmentation but underperform on robotic manipulation. Two issues identified:
   - Lack of state-action-state dynamics modeling
   - Redundancy of explicit geometric reconstruction

2. Method (AFRO):
   - Self-supervised framework
   - No action labels or reconstruction supervision
   - State prediction as generative diffusion process
   - Joint forward and inverse dynamics in shared latent space
   - Feature differencing to prevent feature leakage in IDM
   - Inverse-consistency supervision
   - Components: online encoder f_φ, IDM g_ψ, FDM h_θ, EMA target encoder f_ξ
   - FDM implemented as Diffusion Transformer (DiT) with AdaLN-Zero conditioning
   - VICReg loss for self-supervised learning
   - Latent action dimension = 16
   - Frame interval k = 4
   - 300 epochs, AdamW, lr=1e-4
   - VICReg weights λ_I = λ_V = 25, λ_C = 1, variance threshold γ=1
   - EMA momentum starting at 0.996

3. Experiments:
   - Simulation: MetaWorld (14 tasks) + Adroit (Door, Pen) = 16 simulated tasks
   - Real-world: 4 tasks on Franka Emika arm with RealSense L515 camera
   - Baselines: CLIP, DINOv2, PointNet, PointMAE, PointDif, DynaMo (2D/3D), FVP, DP3
   - Diffusion Policy architecture for downstream tasks
   - 100 epochs policy training, AdamW, lr=1e-4, batch size 128
   - 25 rollouts every 10 epochs
   - Real-world: 40 demonstrations per task, 20 trials for evaluation
   - RH20T for out-of-domain pre-training

4. Resources:
   - Single NVIDIA RTX 4090 GPU
   - No explicit training time mentioned

5. Experiment count and sufficiency:
   - Quantitative results on simulation benchmarks (Table 1)
   - Scaling across task domains (Fig 5)
   - Scaling with data (Fig 6)
   - t-SNE visualization (Fig 7)
   - Real-world performance with in-domain and out-of-domain pretraining (Table 2)
   - Object generalization (Table 3)
   - Cluttered scene generalization (Table 4)
   - Ablation studies (Table 5)
   - 5 categories of baselines

6. Main conclusions:
   - AFRO outperforms baselines in simulation and real-world
   - 76.0% on MetaWorld (+6.3 over DP3), 83.0% on Adroit
   - Real-world: 70% in-domain, 84% with out-of-domain pretraining
   - Better generalization to unseen objects and cluttered scenes
   - Scales favorably with data and task diversity
   - Stable training without collapse

7. Strengths:
   - First to introduce latent actions into 3D visual learning
   - Feature differencing prevents feature leakage
   - Inverse-consistency supervision
   - Diffusion-based forward dynamics captures multimodal futures
   - No action labels or reconstruction needed
   - Scales with data and domain diversity

8. Limitations:
   - Limited real-world tasks (only 4)
   - Limited robot type (only Franka)
   - Only single GPU
   - Latent action dimension needs tuning
   - Doesn't incorporate semantic priors from foundation models
   - Diffusion FDM slower than deterministic
   - Real-world experiments only on single environment

Let me write this in a structured Chinese Markdown format.</think>

# AFRO：面向可扩展机器人学习的三维动力学感知视觉表示

## 1. 论文核心问题与研究动机

- **背景**：视觉预训练在机器人操控中扮演关键角色，已涌现出 MVP、R3M、VIP 等 2D 视觉预训练方法以及 PointMAE、PointDif、SUGAR 等 3D 预训练方法。
- **核心问题**：现有 3D 视觉预训练方法在物体识别与分割任务上表现优秀，却在机器人操控任务上表现欠佳，甚至可能逊于 2D 基础模型。
- **作者归因的两大关键缺陷**：
  - **缺乏动力学感知**：操控任务本质是序列化的状态—动作—状态过程，但多数 3D 预训练框架只对单帧施加监督，忽略时间连续性与因果依赖。
  - **缺乏操控相关的抽象**：许多 3D 方法专注于全场景重建，会保留与控制无关的背景细节，可能分散策略网络对任务关键区域的注意力。
- **核心追问**：如何在不使用显式动作标签或重建的前提下，让模型在潜空间中捕获到因果状态转移结构？

## 2. 论文方法论

### 2.1 整体框架
- 名称 **AFRO**（Action-Free 3D visual pretraining），三模块结构：
  - **在线编码器** $f_\phi$：将点云 $P_t$ 映射为特征 $z_t$。
  - **逆向动力学模型 IDM** $g_\psi$：从相邻状态推断潜动作 $\alpha_{t\to t+k}$。
  - **前向动力学模型 FDM** $h_\theta$：由当前特征与潜动作预测未来特征 $\hat{z}_{t+k}$。
  - **目标编码器** $f_\xi$：以 EMA 方式更新，提供稳定监督目标 $\tilde{z}_{t+k}$。

### 2.2 关键技术细节
- **特征差分代替原始堆叠（防止特征泄露）**
  - 传统做法：$\alpha_{t\to t+k} = g_\psi(z_t, z_{t+k})$ 容易让 IDM 通过"复制" $z_{t+k}$ 的信息走捷径。
  - AFRO 做法：$\alpha_{t\to t+k} = g_\psi(z_{t+k} - z_t)$，强调"变化"而非"状态本身"，过滤静态背景。
- **逆向一致性监督（双向时间一致性）**
  - 对称地学 $\alpha_{t+k \to t} = g_\psi(z_t - z_{t+k})$。
  - FDM 反向预测 $\hat{z}_t = h_\theta(z_{t+k}, \alpha_{t+k \to t})$，与 $\tilde{z}_t$ 对齐。
  - 强制潜动作可逆且物理合理，避免退化解。
- **基于扩散 Transformer 的前向动力学**
  - 将状态预测视为条件去噪过程。
  - FDM 由 DiT + **AdaLN-Zero** 调节构成，条件变量为 $c = \text{cond}(z_t, \alpha_{t\to t+k}, \tau)$。
  - 前向加噪：$z^{(\tau)}_{t+k} = \sqrt{\bar\alpha_\tau} z_{t+k} + \sqrt{1-\bar\alpha_\tau}\epsilon$。
  - 单步去噪：$\hat{z}_{t+k} = h_\theta(z^{(\tau)}_{t+k}, z_t, \alpha_{t\to t+k}, \tau)$。
  - AdaLN-Zero 初始为零，使残差路径近似恒等，逐步注入时间步与动作信息。
- **VICReg 匹配损失**
  - 防止自监督潜在学习发生坍缩，包含不变项 $L_\text{inv}$、方差项 $L_\text{var}$、协方差项 $L_\text{cov}$。
  - 损失权重 $\lambda_I = \lambda_V = 25$，$\lambda_C = 1$，方差阈值 $\gamma = 1$。
- **预训练超参数**
  - IDM 为 3 层 MLP + GeLU，输出 16 维潜动作。
  - FDM 为 4 层 Transformer（自适应调节）。
  - 帧间隔 $k = 4$，共训练 300 轮，使用 AdamW，lr=1e-4。
  - 目标编码器 EMA 动量从 0.996 起步。

## 3. 实验设计

### 3.1 数据集与基准
- **仿真**：
  - **MetaWorld**（14 个任务，7-DoF Sawyer 机械臂，MuJoCo），每任务 25 条专家轨迹。
  - **Adroit**（2 个任务：Door 与 Pen，多指灵巧手），每任务 100 条专家轨迹（VRL3 生成）。
- **真实机器人**
  - 7-DoF Franka Emika + 平行夹爪 + RealSense L515 顶视深度相机。
  - 4 个任务：块对齐（Block-to-Block Alignment）、按铃（Bell Pressing）、水果抓放（Fruit Pick-and-Place）、杯子覆盖方块（Cover Block）。
  - 每任务 40 条演示，20 次试验评估。
- **大规模跨域预训练数据集**：RH20T 真实机器人数据集（构造 Franka Simple 子集，去前 30 帧静态，每 20 帧采样一次）。

### 3.2 对比方法
- **端到端基线**：DP3（3D Diffusion Policy）。
- **大规模数据集预训练**：CLIP、DINOv2（2D 图像）、PointNet（3D）。
- **静态 3D 预训练**：PointMAE、PointDif。
- **动力学感知预训练**：FVP、DynaMo（2D 与 3D 版本，本文的 DynaMo-3D 是对原始 DynaMo 的 3D 扩展）。

### 3.3 评估协议
- 视觉编码器预训练后冻结，配套使用 **Diffusion Policy**。
- 策略训练 100 轮，AdamW（$\beta_1=0.9, \beta_2=0.999$），lr=1e-4（余弦退火），batch size 128。
- 每 10 轮评估 25 次 rollouts，取前三名最高成功率。

## 4. 资源与算力
- **GPU**：全部实验在 **单块 NVIDIA RTX 4090** 上完成。
- **预训练规模**：300 轮，AdamW，lr=1e-4（具体单轮时长与总训练时长未在文中披露）。
- **评估规模**：单 GPU 完成仿真 16 任务与真实 4 任务的策略训练与评估。
- **算力说明**：未提供总机时、显存占用或预训练耗时细节。

## 5. 实验数量与充分性

- **仿真主对比**（表 1）：在 MetaWorld（Easy/Medium/Hard/Very Hard 分档）与 Adroit（Door、Pen）上与 8 类基线比较。
- **域可扩展性**（图 5）：单任务 vs. 多任务联合预训练在 Bin Picking、Peg Unplug Side、Push Wall、Pen 上的对比。
- **数据可扩展性**（图 6）：在 Door、Pen 上对 10/20/50/100/200/500 条专家轨迹下的策略成功率扫描。
- **表示分析**（图 7）：8 个 MetaWorld 任务的 t-SNE 可视化。
- **真实机器人**（表 2）：
  - 蓝块：域内预训练下 4 个任务的成功率。
  - 红块：使用 RH20T Franka Simple 跨域预训练再微调后的成功率。
- **泛化评估**（表 3、表 4）：物体外观泛化（更重、更软、更小）与场景杂乱泛化。
- **消融实验**（表 5）：FDM 类型（Transformer vs. Diffusion）、是否使用特征差分输入、是否使用逆向一致性、VICReg vs. MSE、潜动作维度（Dact=16/64/128）、帧间隔（k=1/4/16）。
- **充分性评估**：覆盖主结果、跨域、跨数据规模、可视化、泛化、消融共 7 类实验，对照 8 类基线，比较系统；但仿真任务数与真实机器人任务数有限。

## 6. 主要结论与发现
- AFRO 在 MetaWorld 上达到 **76.0%** 平均成功率（较 DP3 提升 +6.3），Adroit 上达到 **83.0%**。
- 真实机器人上 AFRO 平均成功率为 **70%**（域内预训练）与 **84%**（RH20T 跨域预训练），明显优于所有基线。
- AFRO 在多任务联合预训练下表现更佳（平均从 68.0% → 82.8%，Bin Picking 从 20% → 58%，Peg Unplug Side 达到 100%）。
- AFRO 在不同数据规模下均领先基线，Door 上 50 条样本即达 74%，500 条达 90%；Pen 上 20→50 样本即从 60% 提升至 81%，500 条达 98%。
- t-SNE 可视化显示 AFRO 表征聚类更紧致、轨迹更平滑。
- 物体外观与杂乱场景泛化测试中，AFRO 的成功率下降幅度最小（如 BP 上 75%→60%，B2BA 上 70%→65%）。
- 消融显示：FDM 扩散化、特征差分、逆向一致性、VICReg 均不可缺；潜动作维度 16 与帧间隔 k=4 表现最佳。

## 7. 优点
- **首次将潜动作引入 3D 视觉学习**，避免了显式动作标签与几何重建依赖。
- **特征差分 + 逆向一致性** 两个轻量技巧显著抑制 IDM 的特征泄露与退化解。
- **扩散 Transformer 前向动力学** 能更好地刻画未来多模态不确定性。
- **完全自监督、无动作标签**，天然适配大规模无标签 3D 机器人交互数据（含仿真生成数据）。
- 在仿真与真机、域内与跨域、不同数据量、不同任务复杂度上均展现良好的可扩展性。
- 实验设计涵盖性能、可扩展性、表示可视化、泛化与消融五大维度，论证较完整。

## 8. 不足与局限
- **真实机器人任务数较少**（仅 4 个任务），单一平台（Franka + RealSense L515）评估，难以推断在异构机器人本体上的可迁移性。
- **算力披露不充分**：未给出总机时、显存占用或每次预训练/微调时长，难以评估实际训练成本。
- **扩散前向模型推理开销**：DiT 扩散动力学相较确定性 Transformer 推理代价更高，可能限制实时部署或大规模策略 rollouts 场景。
- **基线 3D-DynaMo 系自建**：作者自扩展的 DynaMo-3D 缺少与原 DynaMo 的严格等价性证明，可能引入对比偏差。
- **潜动作维度与帧间隔敏感**：消融显示 Dact 与 k 选择影响明显，最优值是否随任务域自适应仍不明确。
- **尚未融合语义先验**：作者在结论中明确指出，未来可结合视觉基础模型的语义先验，当前 AFRO 完全依赖几何—动力学监督，对语义敏感的操控子任务可能受限。
- **数据偏差风险**：RH20T 子集仅采样前两场景的 140+ 任务，未评估在更大跨域、跨本体数据上的稳定性。
- **任务多样性局限**：MetaWorld 与 Adroit 的任务类型偏桌面级，AFRO 对长序列、双臂、移动操作等复杂场景的适用性未经验证。

（完）
