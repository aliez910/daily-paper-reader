---
title: Spatial-Aware VLA Pretraining through Visual-Physical Alignment from Human Videos
title_zh: 基于视觉-物理对齐的空间感知VLA预训练：来自人类视频
authors: "Feng, Yicheng, Zhang, Wanpeng, Wang, Ye, Luo, Hao, Yuan, Haoqi, Zheng, Sipeng, Lu, Zongqing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Feng_Spatial-Aware_VLA_Pretraining_through_Visual-Physical_Alignment_from_Human_Videos_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 利用人类视频预训练通用VLA模型，弥合二维感知与三维动作之间的鸿沟
tldr: 本文针对VLA模型依赖二维视觉输入却要在三维环境中执行机器人操作所导致的感知与动作衔接不足的问题，提出了空间感知的VLA预训练范式。作者利用大规模人类演示视频提取三维视觉与三维动作标注，使模型在机器人策略学习前先获得三维空间理解能力。实验表明该预训练显著提升了通用VLA模型在下游操作任务中的三维空间推理表现。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1432, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 819, \"height\": 264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 818, \"height\": 338, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 822, \"height\": 229, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 701, \"height\": 302, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 739, \"height\": 203, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1447, \"height\": 889, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 843, \"height\": 237, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 695, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-spatial-aware-vla-pretraining-through-visual-physical-alignment-from-human-videos-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 698, \"height\": 211, \"label\": \"Table\"}]"
motivation: 现有VLA模型依赖二维视觉输入，难以在三维环境中建立可靠的感知-动作衔接。
method: 利用人类视频提取三维标注，进行空间感知VLA预训练以对齐二维视觉与三维动作。
result: 预训练后的通用VLA模型在下游机器人操作中表现出更强的三维空间理解。
conclusion: 空间感知预训练有效提升了通用VLA在三维机器人操作中的视觉到动作映射能力。
---

## Abstract
Vision-Language-Action (VLA) models provide a promising paradigm for robot learning by integrating visual perception with language-guided policy learning. However, most existing approaches rely on 2D visual inputs to perform actions in 3D physical environments, creating a significant gap between perception and action grounding. To bridge this gap, we propose a Spatial-Aware VLA Pretraining paradigm that enables models to acquire 3D spatial understanding before robot policy learning. Starting from pretrained vision-language models, we leverage large-scale human demonstration videos to extract 3D visual and 3D action annotations, forming a new source of supervision that aligns 2D visual observations with 3D spatial reasoning. We instantiate this paradigm with VIPA-VLA, a dual-encoder architecture that incorporates a 3D visual encoder to augment semantic visual representations with 3D-aware features, and aligns the two through visual-physical alignment pretraining. When adapted to downstream robot tasks, VIPA-VLA achieves significantly improved grounding between 2D vision and 3D action, resulting in more robust and generalizable robotic policies.

---

## 论文详细总结（自动生成）

<think>The user wants a structured Chinese summary of the paper following 8 specific points. Let me organize the content carefully based on the paper provided.

Let me analyze the paper:

1. Core problem: VLA models use 2D visual inputs but operate in 3D physical environments, creating a gap between perception and action grounding.

2. Method: 
- Spatial-Aware VLA Pretraining paradigm
- VIPA-VLA dual-encoder architecture
- 3D visual encoder (Cut3R) + semantic visual encoder + cross-attention fusion
- Hand3D dataset with 3D visual and action annotations
- Two-stage pretraining: Stage 1 (3D visual annotations, fuse layer training) + Stage 2 (3D action annotations, motion tokens)
- Post-training with flow matching action head (DiT)
- Mathematical formulations for scale calibration, direction discretization

3. Experiments:
- LIBERO benchmark (4 task suites: Spatial, Object, Goal, Long)
- Real robot tasks (Put-Three-Obj, Wipe-Board, Water-Plant)
- Compared with many methods (TraceVLA, OpenVLA, SpatialVLA, DiT Policy, CoT-VLA, ThinkAct, TriVLA, 4D-VLA, GR00T N1.5, MaIL, π0-FAST, MolmoAct, GR00T N1, π0, UniVLA, π0.5, Being-H0, InternVL3.5)
- Ablation studies on architecture and pretraining
- Hand3D-test for spatial reasoning evaluation

4. Resources: 8 × A800 GPUs, learning rate 1e-5 for pretraining, 5e-5 for post-training. No specific training duration mentioned.

5. Number of experiments:
- LIBERO benchmark (500 trials per suite × 4 suites)
- Real robot tasks (50 teleoperated trajectories, 10 evaluation trials per task)
- Unseen environments
- Ablations: 4 configurations
- Hand3D-test: 2K VQA pairs
- Total multiple comparisons

6. Main findings:
- Strong performance on LIBERO benchmark (92.4% single-view, 96.8% two-view avg)
- Real robot tasks: best overall performance
- Robust in unseen environments
- Both pretraining and dual encoder contribute
- Visual-physical alignment effectively bridges 2D-3D gap

7. Strengths:
- Novel paradigm using human videos for pretraining
- Dual encoder architecture
- Comprehensive dataset construction
- Both simulation and real-world evaluation
- Unseen environment testing
- Detailed ablations

8. Limitations:
- Scale calibration may still have issues
- Embodiment gap with human videos
- Limited real-world tasks (only 3 tasks)
- No robot data used in pretraining
- Single embodiment real robot
- Dependency on external models (Cut3R, Gemini-2.5-flash)

Let me write this in Chinese with proper Markdown formatting.</think>

# 论文总结：Spatial-Aware VLA Pretraining through Visual-Physical Alignment from Human Videos

## 1. 核心问题与研究动机

- **核心问题**：现有 Vision-Language-Action (VLA) 模型普遍依赖 **2D 视觉输入** 来感知世界，却在 **3D 物理环境** 中执行操作，导致 **2D 视觉感知与 3D 物理动作之间存在显著鸿沟**，制约了策略的空间落地能力与跨场景泛化性。
- **研究动机**：
  - 虽然人类能从 2D 视觉信号中自然推断 3D 空间，但当前 VLA 模型缺乏这种能力；
  - 大规模人类演示视频天然蕴含丰富的"2D 视觉—3D 动作"对应，且比机器人数据更易获取、场景更多样；
  - 现有 3D VLM 偏重"感知"而非"动作"，与机器人策略学习的衔接有限；
  - 已有的人体视频学习方法多停留在 2D 表征或隐式特征，未显式建立 3D 感知–3D 动作的桥接。

## 2. 方法论

### 2.1 整体思路
提出 **Spatial-Aware VLA Pretraining 范式**：在机器人策略学习之前，先用大规模人类演示视频教会模型 **2D 视觉 → 3D 空间** 的对齐能力（即所谓 "Visual-Physical Alignment"），再通过 Post-Training 适配到机器人任务。

### 2.2 数据集 Hand3D
- **数据来源**：聚合 9 个异构人类操作视频源（Arctic、HOI4D、FPHA、H2O、OAKINK2、TACO、Dex-YCB、EgoDex、Taste-Rob），统一到 MANO 手部参数化表示；
- **3D 视觉标注（Hand3D-visual，约 300K VQA 对）**：
  - 用 Cut3R 估计逐帧稠密点云 P；
  - 用 Gemini-2.5-flash + GroundingDINO 生成物体 2D 框并结合深度反投影到 3D；
  - 将 MANO 手部参数通过相机内外参投影到 2D，并过滤手部不可见帧；
  - **尺度校正**：用绝对空间的手腕深度 $J^h_z$ 与点云相对深度 $\tilde{J}^h_z$ 计算比例因子 $s = \text{median}_{k\in\Omega}(J^h_{z,k}/\tilde{J}^h_{z,k})$，统一到真实物理尺度 $sP$；
  - 由 Gemini-2.5-flash 生成四类 QA：空间关系 / 任务完成 / 手部运动 / 相机运动，3D 位移以 (方向, 距离) 离散化：$D=\{right/left, up/down, forward/backward\}$，阈值 $\gamma$ 过滤；
- **3D 动作标注（Hand3D-action，约 1M 对）**：从手腕轨迹 $(x_t,y_t,z_t)$ 离散化为运动 token，配以视频-指令对，过滤无效运动样本。

### 2.3 模型架构 VIPA-VLA（双编码器）
- **语义视觉编码器**（InternVL3.5 自带 ViT）→ $V_{sem}$；
- **3D 视觉编码器**（Cut3R）→ $V_{spa}$；
- **融合层**：以 $V_{sem}$ 为 Query、$V_{spa}$ 为 Key/Value 的 Cross-Attention，得到融合特征 $V_f$；
- 扩展词表加入 **运动 token**，将 3D 物理空间离散化；
- 初始化自 InternVL3.5-2B。

### 2.4 两阶段预训练
- **Stage 1（3D 视觉对齐）**：冻结两个视觉编码器，仅训练融合层；输入 1–4 帧，预测空间 QA，强化 3D 空间关系推理；
- **Stage 2（3D 动作对齐）**：冻结视觉编码器，训练 LLM 预测运动 token，学习视觉到细粒度物理运动的映射。

### 2.5 Post-Training（机器人适配）
- 附加 **DiT (Diffusion Transformer) 动作头**，使用 Flow Matching 目标：
  - 噪声插值：$\tilde{a}^{(\tau)}_t = (1-\tau)\epsilon + \tau a_t$，$\tau \sim U(0,1)$
  - 损失：$\mathcal{L}_{FM} = \mathbb{E}[\|v_\theta - (a_t - \epsilon)\|^2_2]$
- 条件由 VLM 主干对 action queries 的隐藏状态 $h_{cond}$ 提供，结合机器人状态 $s_t$ 一起输入 DiT；只更新 LLM 与动作头。

## 3. 实验设计

### 3.1 仿真 Benchmark
- **LIBERO**：四套任务（Spatial / Object / Goal / Long），每套 500 次试验；
- 对比方法涵盖单视图与双视图设置：
  - 单视图：TraceVLA、OpenVLA、SpatialVLA、DiT Policy、CoT-VLA、ThinkAct、TriVLA、4D-VLA、GR00T N1.5；
  - 双视图：MaIL、π0-FAST、MolmoAct、GR00T N1、π0、UniVLA、π0.5。

### 3.2 真机任务（7-DoF Franka + 6-DoF Inspire 手 + 2 个 RealSense L515）
- **Put-Three-Obj**：依次将三个水果放入抽屉（5 个子任务）；
- **Wipe-Board**：用布擦除白板笔迹（3 个子任务）；
- **Water-Plant**：拿起水壶浇花（3 个子任务）；
- 每任务 50 条遥操作演示，10 次评估；同时报告 **子任务成功率** 与 **整体成功率**；
- 额外测试 **未见环境**（unseen settings）的泛化能力；
- 基线：GR00T N1.5、Being-H0、InternVL3.5。

### 3.3 空间推理评估
- **Hand3D-test**：2K 未见视频的 VQA 对，评估距离误差（米）与方向得分（3 个主轴各 0/1 分）。

### 3.4 消融
- LIBERO 上验证：去掉预训练 / 去掉双编码器 / 同时去掉两者。

## 4. 资源与算力

- 文末明确：**8 × A800 GPU**；
- 学习率：预训练 1e-5，Post-Training 5e-5；
- **未明确说明**：训练总时长、单阶段耗时、数据处理时间、显存峰值等细节均未给出。

## 5. 实验数量与充分性

- **仿真**：4 个 LIBERO 子基准 × 500 trial，对比 15+ 基线；
- **真机**：3 个任务 × 2 种环境（seen / unseen）× 2 种指标（子任务 / 整体），3 个基线；
- **空间推理**：Hand3D-test 上 3 个模型对比，辅以直方图可视化；
- **消融**：4 组配置，量化了双编码器与预训练各自的贡献；
- **可视化**：第二阶段运动轨迹预测 vs 真值对比；
- **充分性评价**：
  - 优点：覆盖仿真 + 真机、seen + unseen、整体 + 子任务指标，并提供定量与定性两类证据；
  - 局限：真机任务仅 3 类且单一机械臂平台；每任务评估 10 次 trial，统计置信区间有限；未能与 π0.5、GR00T N1 等强基线在真机上直接比较；未见环境下仅覆盖 Put-Three-Obj 和 Wipe-Board 两个任务。

## 6. 主要结论与发现

- **LIBERO 仿真**：单视图平均 92.4%（与 GR00T N1.5 92.1% 相当，超越多数先前方法）；双视图 96.8%，与 π0.5（96.9%）、UniVLA（95.5%）相当；
- **真机**：在全部 3 个任务上子任务 / 整体成功率均高于 GR00T N1.5、Being-H0 和 InternVL3.5；未见环境下提升尤为显著；
- **空间推理**：在 Hand3D-test 上距离误差从 0.18m → 0.12m，方向得分从 1.22/3 → 1.82/3；
- **消融**：去掉预训练平均降 1.2%，去掉双编码器降 2.0%，同时去掉降 3.7%，证明两者互补；
- **核心结论**：从人类视频中学到的 2D–3D 视觉-物理对齐，可作为机器人策略学习的有效预训练先验，无需机器人预训练数据即能在多个基准上与使用大规模机器人数据的强基线匹敌。

## 7. 优点

- **范式创新**：首次系统提出"先 2D–3D 对齐预训练、再机器人 Post-Training"的两阶段范式，不依赖机器人预训练数据；
- **数据构建精细**：尺度校正解决了相对深度与绝对物理尺度不一致的问题，方向–距离离散化将 3D 几何压缩为可监督的语言 token；
- **架构清晰**：双编码器 + 跨注意力融合保持语义表征完整性，同时注入 3D 几何；
- **评估多维度**：仿真 + 真机 + 空间推理 + 消融 + 可视化结合，子任务粒度的细粒度评估；
- **泛化性强**：未见环境显著优于基线，体现所学空间先验的可迁移性。

## 8. 不足与局限

- **真机规模有限**：仅单一 Franka + Inspire 平台、3 个任务，单任务 10 次 trial 统计意义偏弱；未在双臂 / 灵巧手 / 移动机器人上验证；
- **数据规模与多样性**：Hand3D-visual 仅约 4K 片段、300K QA 对，相比 π0、GR00T 等使用的万级机器人轨迹规模较小；
- **依赖外部模型**：Cut3R、Gemini-2.5-flash、GroundingDINO 的错误会逐级传递，可能引入标注噪声与系统偏差；
- **人体–机器人 embodiment gap**：人类手部动作与机器人执行器差异显著，论文未显式讨论如何缓解这种分布漂移；
- **手工先验**：方向离散阈值 $\gamma$、MANO 投影–点云匹配滤波等均为手工设计，缺乏对超参数敏感性的分析；
- **缺失对比**：真机部分未与 π0、π0.5、GR00T N1、UniVLA 等强基线同台比较；
- **算力报告不全**：未提供训练时长、token 数量、显存占用等细节，难以复现成本评估；
- **安全与失败模式**：未见环境下整体成功率仍较低（如 Put-Three-Obj-Unseen 仅 20%），未深入分析失败原因。

（完）
