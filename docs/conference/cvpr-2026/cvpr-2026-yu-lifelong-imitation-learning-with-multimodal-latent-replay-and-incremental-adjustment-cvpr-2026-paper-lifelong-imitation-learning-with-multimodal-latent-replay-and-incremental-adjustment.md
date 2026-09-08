---
title: Lifelong Imitation Learning with Multimodal Latent Replay and Incremental Adjustment
title_zh: 基于多模态潜在回放与增量调整的终身模仿学习
authors: "Yu, Fanqi, Tiezzi, Matteo, Apicella, Tommaso, Beyan, Cigdem, Murino, Vittorio"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Yu_Lifelong_Imitation_Learning_with_Multimodal_Latent_Replay_and_Incremental_Adjustment_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向复杂任务的模仿学习，在LIBERO基准上取得SOTA
tldr: "本文针对顺序任务下的终身模仿学习难题，提出在多模态潜在空间中进行回放与增量特征调整的持续学习框架。通过紧凑存储视觉、语言与机器人状态表征，并结合角度裕度约束的任务嵌入正则化机制，方法在LIBERO基准上刷新了最先进水平，AUC提升10-17分，存储开销减少高达65%。该工作为复杂机器人任务的持续模仿学习提供了高可扩展、低内存的解决方案。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 805, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1727, \"height\": 829, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 341, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 427, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1809, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 323, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 257, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-yu-lifelong-imitation-learning-with-multimodal-latent-replay-and-incremental-adjustment-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 261, \"label\": \"Table\"}]"
motivation: 现有模仿学习方法难以在有限内存下持续学习多任务策略，任务间存在灾难性遗忘。
method: 在多模态潜在空间中进行紧凑回放，并利用角度裕度约束增量调整任务嵌入以稳定适应。
result: "在LIBERO基准上AUC提升10-17分，存储开销减少最高达65%。"
conclusion: 为复杂多任务场景下的终身模仿学习提供了一种内存高效、性能领先的新方案。
---

## Abstract
We introduce a lifelong imitation learning framework that enables continual policy refinement across sequential tasks under realistic memory and data constraints. Our approach departs from conventional experience replay by operating entirely in a multimodal latent space, where compact representations of visual, linguistic, and robot's state information are stored and reused to support future learning. To further stabilize adaptation, we introduce an incremental feature adjustment mechanism that regularizes the evolution of task embeddings through an angular margin constraint, preserving inter-task distinctiveness. Our method establishes a new state of the art in the LIBERO benchmarks, achieving 10-17 point gains in AUC and up to 65% less forgetting compared to previous leading methods. Ablation studies confirm the effectiveness of each component, showing consistent gains over alternative strategies. The code is available at: https://github.com/yfqi/lifelong_mlr_ifa.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper following the provided structure. Let me analyze the paper carefully:

**Paper Title:** Lifelong Imitation Learning with Multimodal Latent Replay and Incremental Adjustment
**Authors:** Fanqi Yu, Matteo Tiezzi, Tommaso Apicella, Cigdem Beyan, Vittorio Murino
**Venue:** CVPR 2026
**GitHub:** https://github.com/yfqi/lifelong_mlr_ifa

Let me extract the key points from the paper:

1. **Problem/Motivation:**
- Standard Imitation Learning assumes fixed task set; can't handle new tasks
- Lifelong Imitation Learning (LIL) aims to continuously acquire skills without catastrophic forgetting
- Memory constraints in real-world scenarios
- Many methods rely on task-ID at test time (not always available)
- Existing rehearsal-based methods store raw data which is memory-intensive

2. **Method:**
Two main components:
- **Multimodal Latent Replay (MLR):** Store compact latent representations (vision + language + state + actions) instead of raw trajectories
- **Incremental Feature Adjustment (IFA):** Loss function with angular margin to keep new task representations distinct from old tasks while maintaining alignment with their own reference

Key formulas:
- IFA loss: L_IFA = (1/|P|) Σ max(0, d(g_t(Tk), h^(r)(Tk)) - d(g_t(Tk), h^(r)(Tj)) + δ)
- δ = α · d(h^(r)(Tk), h^(r)(Tj)) - adaptive margin
- Uses angular distance: d(a,b) = arccos(a^T b / ||a||·||b||)
- Total loss: L = L_BC + λ_IFA · L_IFA

Architecture:
- Visual, language, state encoders (frozen CLIP for vision/language)
- FiLM modulation
- GPT-2 temporal decoder
- Policy head
- Reference: language embedding for each task

3. **Experiments:**
- LIBERO benchmark: LIBERO-OBJECT (10 tasks), LIBERO-GOAL (10 tasks), LIBERO-50 (50 tasks)
- Metrics: FWT (Forward Transfer), NBT (Negative Backward Transfer), AUC
- Compared with: Sequential, ER, BUDS, LOTUS, ISCIL, M2Distill, TAIL
- Pretraining: 6 tasks for OBJECT/GOAL, 25 for LIBERO-50, 50 demos each
- Lifelong: 4 stages for OBJECT/GOAL, 5 stages for LIBERO-50, 10 demos per new task

4. **Resources:**
- Single NVIDIA A100 GPU
- Batch size 10, 100 epochs
- AdamW optimizer, lr=1e-4 with linear scheduler
- λ_IFA = 0.1
- α: 0.3, 0.7, 0.1 for the three benchmarks
- Buffer size: equivalent to 5 demonstrations per task
- 3 random seeds, 20 trials per seed

5. **Experimental thoroughness:**
- Multiple ablations:
  - Modality similarity (Tab 2)
  - Task pair selection proportion (Tab 3)
  - Reference choice (Tab 4)
  - Storage ratio (Tab 5)
  - Angle vs cosine distance (Fig 3)
  - UMAP visualization (Fig 4)
  - Cosine similarity analysis (Tab 6)
- Comparison with many SOTA methods

6. **Results:**
- New SOTA on LIBERO benchmarks
- AUC gains of 10-17 points
- Up to 65% less forgetting
- For example: LIBERO-GOAL AUC from 60.5 (ISCIL) to 77.2, NBT from 19.4 to 6.9

7. **Strengths:**
- No PEFT needed - frozen backbone
- Task-ID agnostic
- Memory efficient (compact latent)
- Simpler than distillation or generative approaches
- Comprehensive ablations
- UMAP visualization to confirm feature separation

8. **Limitations:**
- Limited benchmark (only LIBERO)
- Need language description for reference
- Real-world not tested (only simulation)
- Limited discussion of integration with RL
- Computational efficiency comparisons not detailed

Let me write a comprehensive Chinese summary now.</think>

# 论文总结：基于多模态潜在回放与增量调整的终身模仿学习

## 1. 核心问题与研究背景

- **根本矛盾**：传统模仿学习（Imitation Learning, IL）通常假设任务集合固定，难以应对真实环境中不断出现的新任务、物体或场景（例如家用机器人面对新厨具、重排家具、未知任务）。
- **终身模仿学习（Life-long Imitation Learning, LIL）的核心难题**：如何在持续获得新技能的同时，避免对旧任务的**灾难性遗忘**（catastrophic forgetting），且**测试时不依赖任务 ID**（task-ID agnostic）。
- **现有方法的局限**：
  - **回放类方法**（如 ER、CRIL）通常存储**原始观测与轨迹**，内存开销大；
  - **PEFT/Adapter 类方法**（如 TAIL、ISCIL）需要任务 ID，且通常微调视觉编码器；
  - **蒸馏类方法**（M2Distill）依赖多阶段蒸馏，结构复杂；
  - 现有方法在**新任务与旧任务表征高度相似**时容易出现**表征漂移**（representation drift）。

## 2. 方法论

### 2.1 整体框架（两阶段）
- **多任务预训练阶段**：在固定任务集 $T'$ 上对策略 $\pi_\theta$ 进行行为克隆（BC）。
- **终身学习阶段**：依次到达新任务 $T_1, T_2, \dots, T_K$（与预训练任务不相交），结合当前任务数据与回放缓冲区训练，公式化目标为：
  $$\min_\theta \mathbb{E}_{(o_{\le t}, a_t)\sim(D_k \cup B)} \mathcal{L}_{BC}(\pi_\theta(\hat a_t|o_{\le t}), a_t)$$

### 2.2 网络架构
- **编码器**：视觉与语言编码器均使用**冻结的 CLIP**；状态编码器为两层 MLP；通过 **FiLM 层**用语言特征调制视觉与状态特征。
- **时间解码器**：GPT-2 decoder。
- **策略头**：将全局潜在表示 $g_t$ 解码为动作 $\hat a_t$。
- **关键设计**：在终身学习阶段**只有时间解码器和策略头可训练**，其余骨干完全冻结。

### 2.3 核心模块一：多模态潜在回放（Multimodal Latent Replay, MLR）
- 缓冲区存储的是**冻结编码器输出的紧凑多模态潜在表征**：
  $$B = \{(H_n, a_n)\}_{n=1}^{N_B}$$
  其中 $H_n$ 是视觉、语言、状态多模态的拼接特征（无需原始图像）。
- 优势：相比存储原始轨迹（如 ER），存储开销大幅降低，且对原始高维图像访问被回避。

### 2.4 核心模块二：增量特征调整（Incremental Feature Adjustment, IFA）
- **动机**：当新任务的潜在表征漂移到旧任务参考附近时，会引发干扰。
- **核心损失**：对每个任务对 $(j,k)$（$j<k$），约束当前任务全局潜在 $g_t(T_k)$ 到其自身参考的距离比到旧任务参考的距离小一个裕度：
  $$\mathcal{L}_{IFA} = \frac{1}{|P|}\sum_{(j,k)\in P,\, j<k}\max\left(0,\ d(g_t(T_k), h^{(r)}(T_k)) - d(g_t(T_k), h^{(r)}(T_j)) + \delta\right)$$
- **自适应裕度**：固定 $\delta$ 会忽略任务间语义差异，因此令 $\delta = \alpha \cdot d(h^{(r)}(T_k), h^{(r)}(T_j))$。
- **距离度量采用 angular distance**：$d(a,b) = \arccos\left(\frac{a^\top b}{\|a\|_2\|b\|_2}\right)$，相比余弦距离对小差异更敏感。
- **总损失**：$\mathcal{L} = \mathcal{L}_{BC} + \lambda_{IFA} \mathcal{L}_{IFA}$。

### 2.5 任务对选择与参考选择
- **任务对筛选**：仅对在两种模态（语言 + agent-view）相似度排序中**同时进入前 50%** 的任务对施加 IFA，且必为新旧任务配对。
- **参考选择**：选取每个任务的**语言嵌入** $h^{(l)}$ 作为参考 $h^{(r)}(T_i)$（稳定、富含任务语义）。
- **超参设置**：$\lambda_{IFA}=0.1$；$\alpha$ 在三个基准上分别为 0.3/0.7/0.1。

## 3. 实验设计

### 3.1 数据集与基准
- 采用 **LIBERO 终身机器人操作基准**（[Liu et al., NeurIPS 2023]），包含：
  - **LIBERO-OBJECT**（10 任务，多样物体操作）
  - **LIBERO-GOAL**（10 任务，复杂目标条件）
  - **LIBERO-50**（50 任务，长序列、长跨度）
- 输入模态：agent-view、eye-in-hand 图像、语言指令、机器人本体状态、控制动作。

### 3.2 训练流程
- **预训练**：OBJECT/GOAL 用 6 任务，每任务 50 条演示；LIBERO-50 用 25 任务，每任务 50 条演示。
- **终身学习**：OBJECT/GOAL 分 4 阶段，每阶段新增 1 任务；LIBERO-50 分 5 阶段，每阶段新增 5 任务，每任务 10 条演示。

### 3.3 评价指标
- **FWT（Forward Transfer）**：适应新任务的能力；
- **NBT（Negative Backward Transfer）**：对旧任务的遗忘程度；
- **AUC**：综合所有任务的曲线下面积（成功率）。

### 3.4 对比方法
- **Sequential**：朴素顺序微调；
- **ER [Chaudhry et al.]**：原始轨迹回放；
- **BUDS / LOTUS [Wan et al.]**：基于技能发现的层次化方法；
- **ISCIL [Lee et al.]**：基于可检索技能的增量方法；
- **M2Distill [Roy et al.]**：多模态蒸馏；
- **TAIL [Liu et al.]**：PEFT/Adapter 方法（被适配为 LIL 设置）。

## 4. 资源与算力
- **GPU**：单卡 **NVIDIA A100**；
- **训练设置**：batch size 10、100 epoch、AdamW（lr=1e⁻⁴，linear scheduler）；
- **缓冲区规模**：每个任务约等效 5 条演示的潜在特征（其中 OBJECT 约 188 MB、GOAL 约 121.2 MB、LIBERO-50 约 30.3–37.6 MB 数量级）；
- **实验重复性**：3 个随机种子 × 每种子 20 次试验；
- 论文**未明确报告训练总时长**（小时数/收敛步数等），仅说明 epoch 数。

## 5. 实验数量与充分性

### 5.1 实验覆盖维度
- **主对比实验（表 1）**：在 3 个 LIBERO 基准、3 个指标、3 个种子下与 7 个对比方法全面比较；
- **模态相似度消融（表 2）**：AV、Lan、EIH、Act、Sta 单模态 + 4 种与 Lan 的组合，验证任务对筛选的模态选择；
- **任务对筛选比例消融（表 3）**：33.3% / 50% / 66.6%；
- **参考选择消融（表 4）**：语言参考 vs 全局潜在均值；
- **存储比例消融（表 5）**：0.10 / 0.20 / 0.50 概率；
- **距离度量消融（图 3）**：angular vs cosine；
- **表征空间可视化（图 4）**：UMAP 可视化有无 IFA 的特征分布；
- **任务间相似度量化（表 6）**：具体分析任务 8 与其他参考的余弦相似度变化。

### 5.2 充分性与公平性评估
- 优点：消融维度齐全（任务对选择、参考、距离度量、存储比例、模态组合），并辅以可视化与定量分析；与 SOTA 方法对比充分。
- 局限：消融多在 OBJECT 与 GOAL 上进行，LIBERO-50 上的细粒度消融较少；未在更大规模或跨域数据上验证。

## 6. 主要结论与发现

- **新 SOTA**：在 LIBERO-OBJECT、LIBERO-GOAL、LIBERO-50 三个基准的 FWT、NBT、AUC 上均取得最佳或并列最佳表现。
- **关键提升**（论文摘要级指标）：
  - AUC 提升 **10–17 分**；
  - 遗忘（NBT）最高减少 **65%**；
  - 例如 LIBERO-GOAL：AUC 由 60.5（ISCIL）提升到 **77.2**，NBT 由 19.4 降至 **6.9**；LIBERO-OBJECT：AUC 由 69.0（M2Distill）提升到 **79.4**。
- **结构层面发现**：
  - 仅 MLR（无 IFA）即可超过 LOTUS、ISCIL、M2Distill 等强基线；
  - IFA 在所有基准上稳定带来增量收益，尤其在高相似任务对上；
  - 角度距离在低相似度区域比余弦距离更敏感，效果更好；
  - UMAP 显示 IFA 后任务特征聚类更紧密、跨任务分离更明显；
  - 语言嵌入作为参考显著优于全局均值参考；
  - Lan + agent-view 是最佳任务对筛选模态组合；
  - 50% 的任务对筛选比例是甜点。

## 7. 优点与亮点

- **简洁性高**：不需要 PEFT、不需要知识蒸馏、不需要生成模型、不需要开放词汇视觉模型；
- **骨干冻结**：CLIP 完全冻结，省去了视觉 adapter 的管理负担；
- **真正 task-ID agnostic**：测试时不需要任务 ID；
- **内存高效**：存储多模态潜在而非原始图像，文中报告较 SOTA 节省最高约 65%；
- **正则化设计精巧**：自适应角度裕度避免了固定裕度对相似度不敏感的问题；
- **消融充分**：从模块、模态、参考、距离、存储比例等多维度系统验证；
- **可视化直观**：UMAP 与余弦相似度量化从几何层面佐证 IFA 的作用。

## 8. 不足与局限

- **基准单一**：仅在 LIBERO 上验证，缺少对真实机器人、跨域（不同视觉/动力学环境）的实验；
- **依赖语言描述**：参考嵌入 $h^{(r)}$ 来自语言指令，对没有清晰文本描述的任务需要额外设计；
- **缓冲区设计敏感**：表现随存储概率提升而提升，意味着极小内存下性能会下降（Tab 5）；
- **对 LIBERO-50 的消融有限**：复杂的消融（任务对筛选、模态组合等）多在 OBJECT/GOAL 上完成，LIBERO-50 上只跑了主对比；
- **未报告训练时长与计算开销对比**：缺乏与 M2Distill、LOTUS 等方法的 FLOPs/时间成本对比；
- **场景假设**：目前依赖预训练阶段有充足数据，真实环境下预训练任务可能不足；
- **任务对筛选规则较经验化**：top-50% + 两种模态同时选中的设计并非全局最优，需进一步理论分析；
- **未涉及与强化学习结合或在线持续学习**：仅讨论了离线模仿学习设定；
- **角度裕度对极端相似任务的处理仍有提升空间**：Tab 6 与 Fig. 4 显示部分非常相似的任务在 IFA 后仍然高度重叠。

（完）
