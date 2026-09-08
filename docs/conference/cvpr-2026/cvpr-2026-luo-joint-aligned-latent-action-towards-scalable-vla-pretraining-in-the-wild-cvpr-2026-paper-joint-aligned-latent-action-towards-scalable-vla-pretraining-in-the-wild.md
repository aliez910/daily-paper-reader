---
title: "Joint-Aligned Latent Action: Towards Scalable VLA Pretraining in the Wild"
title_zh: 联合对齐潜在动作：迈向野外大规模VLA预训练
authors: "Luo, Hao, Wang, Ye, Zhang, Wanpeng, Yuan, Haoqi, Feng, Yicheng, Xu, Haiweng, Zheng, Sipeng, Lu, Zongqing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Luo_Joint-Aligned_Latent_Action_Towards_Scalable_VLA_Pretraining_in_the_Wild_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向VLA模型的预训练框架，从大规模人类操作视频中学习潜在动作表示
tldr: 现有的视觉-语言-动作（VLA）模型受限于机器人数据规模小且多样性不足的困境，而野外人类操作视频虽然体量庞大，却存在手部标签不可靠的问题。本文提出JALA框架，通过联合对齐潜在动作，避免对完整视觉动态进行重建，转而学习与逆动力学和真实动作对齐的预测性动作嵌入。作者构建了包含750万段视频、超过2000小时的UniHand-Mix数据集用于规模化训练，得到了一个具备迁移感知、以行为为中心的潜在空间。该工作显著推动了面向机器人通用任务的视觉-动作模型发展，为从异构人类数据中学习VLA奠定了基础。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1597, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1604, \"height\": 627, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 250, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 881, \"height\": 410, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 829, \"height\": 366, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 322, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 802, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-luo-joint-aligned-latent-action-towards-scalable-vla-pretraining-in-the-wild-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 310, \"label\": \"Table\"}]"
motivation: VLA模型缺乏大规模多样化的机器人数据，野外人类操作视频虽丰富但手部跟踪标签不可靠，难以直接利用。
method: 提出JALA框架，学习与逆动力学和真实动作联合对齐的潜在动作嵌入，构建可扩展的原子技能库用于预训练。
result: 在750万段视频的UniHand-Mix数据集上完成规模化预训练，得到行为中心、具备迁移感知能力的潜在动作空间。
conclusion: JALA为利用异构人类数据进行VLA预训练提供了有效途径，显著提升了通用视觉-动作模型的可扩展性。
---

## Abstract
Despite progress, Vision-Language-Action models (VLAs) are limited by a scarcity of large-scale, diverse robot data. While human manipulation videos offer a rich alternative, existing methods are forced to choose between small, precisely-labeled datasets and vast in-the-wild footage with unreliable hand tracking labels. We present JALA, a pretraining framework that learns Jointly-Aligned Latent Actions. JALA bypasses full visual dynamic reconstruction, instead learns a predictive action embedding aligned with both inverse dynamics and real actions. This yields a transition-aware, behavior-centric latent space for learning from heterogeneous human data. We scale this approach with UniHand-Mix, a 7.5M video corpus (>2,000 hours) blending laboratory and in-the-wild footage. Experiments demonstrate that JALA generates more realistic hand motions in both controlled and unconstrained scenarios, significantly improving downstream robot manipulation performance in both simulation and real-world tasks. These results indicate that jointly-aligned latent actions offer a scalable pathway for VLA pretraining from human data.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Joint-Aligned Latent Action: Towards Scalable VLA Pretraining in the Wild" following a specific structure. Let me carefully analyze the paper content and organize it according to the 8 requested points.

Let me extract key information:

1. **Core problem**: VLA models are limited by scarce robot data. Human manipulation videos offer an alternative, but there's a trade-off between small precisely-labeled datasets and vast in-the-wild footage with unreliable hand tracking labels.

2. **Method**: JALA (Jointly-Aligned Latent Actions) framework that:
   - Bypasses full visual dynamic reconstruction
   - Learns predictive action embeddings aligned with both inverse dynamics and real actions
   - Uses MCP (Masked Chunk Prediction) for motion label supervision
   - Uses LAP (Latent Action Perceiver) as inverse dynamics model
   - Uses LSP (Latent State Perceiver) to pair with LAP
   - Decoupled EMA updates for stability
   - Hybrid training loss: L = 1_labeled · L_MCP + λL_Align
   - Post-training with flow matching head (DiT-based)

3. **Experiments**:
   - Datasets: UniHand-Mix (7.5M videos, 2000+ hours), LIBERO, RoboCasa, GR1 tabletop, real-world tasks
   - Baselines: Being-H0, GR00T N1.5, LAPA, UniVLA, π0, π0-FAST, OpenVLA, etc.
   - Tasks: Hand motion generation, LIBERO (4 suites), RoboCasa, real-world manipulation

4. **Resources**: 
   - 8×A100-80G GPUs mentioned
   - LAPA†: 29h+57h (two-stage), JALA: 68h
   - JALA uses <80% time of LAPA†

5. **Experiments count**: Multiple ablations, 5-seed mean ± std on LIBERO, scalability studies, layer ablations, real-world tasks with 10 rollouts each

6. **Conclusions**: JALA outperforms baselines, especially on wild data; joint-aligned latent actions are critical; robust to visual backbone choice

7. **Strengths**: 
   - Novel paradigm avoiding reconstruction
   - Scales to wild data without labels
   - Efficient compared to reconstruction-based
   - Robust to visual backbone choice
   - Strong real-world performance

8. **Limitations**: 
   - Limited to 2D video input
   - Real-world only 3 tasks, 10 rollouts
   - Relies on MANO parameters which require preprocessing
   - Ego4D data quality varies
   - No mention of safety considerations

Let me write this in Markdown format in Chinese.</think>

# 论文总结：Joint-Aligned Latent Action (JALA)

## 1. 核心问题与研究背景

- **VLA 模型的数据瓶颈**：视觉-语言-动作（VLA）模型在机器人操控任务上具有潜力，但其性能受限于大规模、多样化机器人数据的稀缺（相比视觉/语言领域数据量差几个数量级）。
- **人类视频的"质量-多样性"权衡**：
  - 实验室采集的人类操作视频（如 ARCTIC、Hot3D、EgoDex 等）提供精确的 3D 手部追踪标签，但场景受限于桌面式受控环境。
  - 野外视频（如 Ego4D、Epic-Kitchens）规模庞大、行为自然，但缺乏可靠的关节/动作标签。
- **现有方法的不足**：以 LAPA 为代表的"重建式"潜在动作方法依赖前向动力学模型（FDM）从像素重建未来帧，但对细粒度手部动作而言，建模难度高、噪声大，导致潜在动作质量下降。
- **核心问题**：如何有效融合互补的人类数据源（带标签与无标签），实现可扩展的 VLA 预训练？

---

## 2. 方法论

### 2.1 核心思想：联合对齐的潜在动作

- JALA **不重建像素级视觉动态**，而是学习与**逆动力学（IDM）输出**和**真实动作标签**都保持对齐的**预测性动作嵌入（predictive embedding）**。
- 类比人类学习：人类通过"可迁移的动作模式"学习操控，而非记忆每个视觉细节。

### 2.2 框架组件

| 组件 | 作用 |
|------|------|
| **MCP（Masked Chunk Prediction）** | 基于手部追踪标签的块级掩码建模，捕捉块内动作的联合模式 |
| **LAP（Latent Action Perceiver）** | 基于 Perceiver 的逆动力学模块，从起止帧特征生成 K 个潜在动作向量 |
| **LSP（Latent State Perceiver）** | 将 VLM 上下文映射到同一潜在动作空间，减轻 VLA 的预测负担 |
| **Decoupled EMA Update** | LAP/LSP 的 backbone 与查询向量使用不对称 EMA 更新，保证训练稳定性 |

### 2.3 关键公式

- **对齐损失**：$\mathcal{L}_{\text{Align}} = \sum_{i=1}^{N} \sum_{k=1}^{K} \|h_{i,k} - z_{i,k}\|_1$
- **混合训练目标**：$\mathcal{L} = \mathbf{1}_{\text{labeled}} \cdot \mathcal{L}_{\text{MCP}} + \lambda \mathcal{L}_{\text{Align}}$
  - 标注数据：MCP + Align 同时启用；
  - 无标签数据：仅启用 Align，从 IDM 中获得学习信号。
- **流匹配后训练**：$\mathcal{L}_{\text{FM}} = \mathbb{E}_{\varepsilon,\xi,A_t} \left[ \| V_\theta(\{h_{i,k}\}, A^\varepsilon_t, q_t) - (\xi - A_t) \|^2 \right]$

### 2.4 算法流程

1. **预训练**：VLA 预测嵌入 $h_{i,k}$（取自 Transformer 第 19 层隐藏状态，维度 d），与 LAP 生成的潜在动作 $z_{i,k}$ 对齐；用 MANO 参数序列 token 化（GRQ-VAE，codebook=8192，15 帧 → 128 token）。
2. **后训练**：固定 VLA backbone，将预测嵌入馈入基于 DiT 的 flow-matching 头（自-交叉注意力交替），通过去噪生成机器人动作块。
3. **架构选择**：以 InternVL3-2B 为 VLM 主干，可选 DINOv3 或 V-JEPA2 作为 LAP/LSP 视觉编码器。

---

## 3. 实验设计

### 3.1 数据集

- **UniHand-Mix**（自建，7.5M 视频，>2000 小时）：
  - 实验室子集：~1000 小时，约 5M 样本，含 MANO 标签。
  - 野外子集：从 Ego4D 中筛选 ~1123 小时，约 2.5M 样本（10% 含 HaWoR 估计的手部姿态）。
- **下游基准**：LIBERO（4 套任务：Spatial/Object/Goal/Long）、RoboCasa（Synthetic & Human）、GR1 Tabletop（跨形态）。
- **真机任务**：Franka Research 3（7-DoF）+ Inspire 灵巧手（6-DoF），3 个多步任务（Put-Three-Obj、Wipe-Board、Water-Plant），每任务仅 50 条遥操作示范。

### 3.2 对比方法

- **手部动作生成**：Being-H0、Being-H0+dino、JALA w/o align、JALA w/o latent。
- **VLA 操控**：π0、π0-FAST、GR00T N1.5、OpenVLA、Octo、UniVLA、LAPA、4D-VLA、TriVLA、SpatialVLA、MolmoAct、ThinkAct、DiT Policy、Diffusion Policy、UniACT 等。
- **特殊对比**：LAPA†（用 JALA 同一 backbone + 数据重训）、JALA-act（只用有标签子集）、JALA w/o dec.（去除解耦 EMA）。

### 3.3 评估指标

- **手部动作**：MPJPE、PAJPE、MWTE、MDE（Lab/Wild 两个 split）。
- **操控**：成功率（SR），LIBERO 上使用 5-seed mean±std。

---

## 4. 资源与算力

- **明确提及**：使用 **8 块 NVIDIA A100-80G GPU** 进行预训练。
- **训练时长**：
  - LAPA†：两阶段预训练共 29h + 57h = 86h。
  - JALA：单一流程 **68h**，比 LAPA† 节省 **>20%** 时间。
- **其他细节**：batch size 128，学习率 1e-4，余弦调度；后训练仅解冻 LM 参数，冻结视觉编码器。
- **未明确说明**：真机实验的算力、后训练的 GPU 数量、UniHand-Mix 各阶段的具体算力分配。

---

## 5. 实验数量与充分性

- **手部动作生成实验**：Lab + Wild 两个 split × 4 指标 × 8 个模型变体 = 64 个数据点（Tab. 1）。
- **LIBERO 双视角实验**：4 任务套件 × 9 个模型（Tab. 2）。
- **LIBERO 消融**：5-seed mean±std（Tab. 3），包含 8 种 JALA 变体。
- **LIBERO 单视角实验**：4 套件 × 19 个模型，分 >3B 和 ≈3B 两组（Tab. 4）。
- **RoboCasa + GR1**：2 子集 + GR1 = 8 模型对比（Tab. 5）。
- **超参消融**：野生数据比例（0/25/50/100%）、对齐层位置（14/19/24/28 层）。
- **真机实验**：3 任务 × 10 rollouts × 6 个模型对比，含 Seen/Unseen 泛化（Tab. 6）。
- **充分性评价**：
  - **优点**：覆盖仿真+真机、消融充分、多 seed 统计、跨形态测试。
  - **局限**：真机仅 3 任务、每任务 10 次 rollout 统计效力有限；RoboCasa/GR1 缺误差棒（作者称因评测成本 24×50=1200 次运行）。

---

## 6. 主要结论与发现

- **手部动作生成**：JALA 在 Lab/Wild 上均优于 Being-H0 系列，Wild split 提升尤为显著（如 MPJPE 从 16.91 降至 11.02），证明对齐式潜在动作能有效迁移到野外。
- **LIBERO 操控**：双视角平均 SR 96.9%（JALA-dino）；单视角 <3B 模型中 SoTA（92.3%），Long-horizon 套件提升最大（87.2%）。
- **RoboCasa/GR1**：合成数据 + 真实数据均提升，跨形态（人手→GR1）优势最明显。
- **真机**：JALA-dino 在所有任务（seen/unseen）上均显著领先，Put-Three-Obj unseen 提升约 30 pp（58% vs GR00T 28%）。
- **关键洞察**：
  1. 单纯增加无标签视频（w/o latent）反而**有害**；需有合适的结构化监督。
  2. 预测范式（next-token vs masked-chunk）影响小，**联合对齐是关键驱动**。
  3. 对视觉 backbone（DINOv3 vs V-JEPA2）选择**鲁棒**。
  4. 第 19 层隐藏状态最适合做预测嵌入，更深层会过拟合数据集细节。
  5. **去耦 EMA 更新至关重要**（w/o dec. 在 LIBERO 上 SR 从 96.9% 暴跌至 56.6%）。

---

## 7. 优点 / 亮点

- **范式创新**：突破"重建式潜在动作"范式，避免像素重建带来的噪声问题。
- **统一潜在空间**：可同时利用标注和无标注异构数据，实现真正的可扩展 VLA 预训练。
- **数据规模化**：UniHand-Mix（7.5M 视频）比 LAPA 等使用的人类数据集大 1-2 个数量级。
- **工程效率**：相比重建式方法训练时间节省 20%+，仅用人类视频预训练即超越部分含机器人数据的模型。
- **真实世界泛化**：在未见过场景（桌布、马克笔颜色变化）下鲁棒性强。
- **理论动机清晰**："人类通过可迁移动作模式而非视觉细节学习操控"这一直觉贯穿全篇。

---

## 8. 不足与局限

- **真机评估有限**：仅 3 个任务，每任务仅 10 次 rollout；任务均为短中期多步任务，缺少长时序、复杂接触（如软体、流体）任务。
- **无安全/失败分析**：未涉及机器人操控安全、失败恢复等现实关切。
- **数据预处理依赖**：依赖 MANO 参数、GRQ-VAE 量化、WiLoR+HaWoR 估计等复杂管线，端到端能力受限。
- **训练时长仍较长**：68h on 8×A100 仍非轻量；无法说明推理延迟（real-time 是否可部署）。
- **视觉形态限制**：仅使用第三视角（部分双视角），缺少深度信息、触觉等多模态输入。
- **缺乏错误模式分析**：未深入讨论失败案例、归因。
- **数据集偏差风险**：Ego4D 主要来自西方文化背景、欧美厨房场景，对其他文化/任务的可迁移性未验证。
- **缺乏与最新 SOTA 对比**：与 π0.5 等 2025 年新模型未直接对比。

（完）
