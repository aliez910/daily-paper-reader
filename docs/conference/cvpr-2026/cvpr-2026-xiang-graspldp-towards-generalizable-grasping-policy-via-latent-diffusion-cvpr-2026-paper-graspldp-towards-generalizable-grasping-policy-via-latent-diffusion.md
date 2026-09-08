---
title: "GraspLDP: Towards Generalizable Grasping Policy via Latent Diffusion"
title_zh: "GraspLDP:基于潜在扩散的可泛化抓取策略"
authors: "Xiang, Enda, Ma, Haoxiang, Ma, Xinzhu, Liu, Zicheng, Huang, Di"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Xiang_GraspLDP_Towards_Generalizable_Grasping_Policy_via_Latent_Diffusion_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过模仿学习提升抓取精度与泛化能力
tldr: "现有模仿学习抓取策略在执行精度、空间与物体泛化方面存在不足,本文提出GraspLDP方法。该方法将抓取先验知识融入潜在扩散策略框架,用于指导动作块解码。在复杂操纵任务中的实验表明,该方法显著提升了抓取精度与跨场景泛化能力,为面向复杂操作的模仿学习提供了有效的扩散式解决方案。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1754, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1610, \"height\": 611, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 708, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 843, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1715, \"height\": 645, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 858, \"height\": 313, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 800, \"height\": 376, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1606, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1736, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 802, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1681, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiang-graspldp-towards-generalizable-grasping-policy-via-latent-diffusion-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 859, \"height\": 308, \"label\": \"Table\"}]"
motivation: 模仿学习抓取策略在空间与物体泛化、执行精度上仍有较大提升空间。
method: "将抓取先验融入潜在扩散策略框架,以指导动作块解码并提升抓取质量。"
result: 在空间与物体泛化场景下抓取精度与成功率均显著提高。
conclusion: 为复杂操纵中的抓取子任务提供了一种可泛化的模仿学习新方案。
---

## Abstract
This paper focuses on enhancing the grasping precision and generalization of manipulation policies learned via imitation learning. Diffusion-based policy learning methods have recently become the mainstream approach for robotic manipulation tasks. As grasping is a critical subtask in manipulation, the ability of imitation-learned policies to execute precise and generalizable grasps merits particular attention. Existing imitation learning techniques for grasping often suffer from imprecise grasp executions, limited spatial generalization, and poor object generalization. To address these challenges, we incorporate grasp prior knowledge into the diffusion policy framework. In particular, we employ a latent diffusion policy to guide action chunk decoding with grasp pose prior, ensuring that generated motion trajectories adhere closely to feasible grasp configurations. Furthermore, we introduce a self-supervised reconstruction objective during diffusion to embed the graspness prior: at each reverse diffusion step, we reconstruct wrist-camera images back-projected the graspness from the intermediate representations. Both simulation and real robot experiments demonstrate that our approach significantly outperforms baseline methods and exhibits strong dynamic grasping capabilities.

---

## 论文详细总结（自动生成）

<think>The user is asking me to summarize a CVPR 2026 paper titled "GraspLDP: Towards Generalizable Grasping Policy via Latent Diffusion" in Chinese. I need to follow a specific structure with 8 points and use Markdown formatting. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is about enhancing grasping policies in robotic manipulation through latent diffusion models that incorporate grasp prior knowledge. Let me extract key information:

1. Core problem: Imitation learning-based grasping policies suffer from imprecise grasps, limited spatial generalization, and poor object generalization.

2. Method: 
   - Two-stage latent diffusion policy
   - Stage 1: Action Latent Learning - VAE encodes action chunks, grasp pose G is concatenated with latent Z to reconstruct action
   - Stage 2: Diffusion on Latent Action Space - Diffusion in compact latent space
   - Visual Graspness Cue - back-project graspness scores to wrist-view images
   - Self-supervised reconstruction loss
   - Heuristic Pose Selector (HPS) for inference

3. Experiments:
   - LIBERO benchmark
   - ~12K demonstrations over 20 objects
   - Baselines: Diffusion Policy, OpenVLA, GraspVLA, Ours Baseline (conditioning)
   - Real-world: Franka Research 3, RealSense cameras
   - 10 training objects + 13 test objects, 500 demos total
   - 4 cluttered scenarios
   - Dynamic grasp evaluation

4. Resources: No specific GPU information mentioned in the paper (except mentioning RTX 4090 in inference latency comparison)

5. Experimental coverage:
   - 4 evaluation splits: In Domain, Spatial, Object, Visual generalization
   - 6 tables of results
   - Ablation studies
   - Cluttered scenarios
   - Dynamic grasping
   - Real-world experiments

6. Conclusions: GraspLDP achieves 17.5% higher SR in-domain over Diffusion Policy, with 22.2%, 46.8%, 48.3% gains in spatial, object, visual generalization. Strong performance in cluttered and dynamic scenarios.

7. Strengths:
   - Two-stage latent design effectively incorporates grasp priors
   - HPS balances grasp quality and kinematic proximity
   - Self-supervised reconstruction enhances graspness attention
   - Lower inference latency than GraspVLA
   - Strong generalization across multiple axes

8. Limitations:
   - Difficulty with highly deformable or fragile objects (egg, beaker)
   - Mentioned in conclusion
   - Future work to incorporate tactile/force signals

Let me write the summary in Chinese with proper Markdown formatting.</think>

# GraspLDP 论文总结

## 1. 核心问题与研究动机

- **研究背景**：抓取（grasping）是机器人操纵（manipulation）的关键前置子任务。基于扩散的模仿学习策略（Diffusion Policy）已成为主流范式，但在抓取任务上仍面临三大瓶颈：
  - 抓取执行精度不足（imprecise grasp execution）；
  - 空间泛化能力有限（limited spatial generalization）；
  - 物体泛化能力差（poor object generalization）。
- **现有方案的不足**：
  - **数据驱动路线**（如 GraspVLA）：依赖亿级仿真数据（Syngrasp-1b 需 160 块 RTX 4090 跑 10 天），且大 VLA 模型推理延迟高、动作频率低，难以处理动态场景；
  - **先验注入路线**（如 Robograsp、Spatial Robograsp、GPA-RAM）：仅将抓取位姿作为附加条件输入，存在两个问题——输入位姿与输出动作序列相关性弱、且低语义位姿与视觉输入之间存在模态错配，模型难以充分提取抓取空间分布信息。
- **本文目标**：将成熟的抓取检测器（grasp detector）所蕴含的先验知识，更深入地融入扩散策略框架，从而同时提升抓取精度与多维度泛化能力。

## 2. 方法论

### 2.1 整体框架
- 提出 **GraspLDP**，一种**两阶段训练的潜在扩散策略**（latent diffusion policy）：
  - **阶段一：动作潜在空间学习（Action Latent Learning）**——利用 VAE 将动作块（action chunk）压缩到紧凑潜在空间，并注入抓取位姿先验；
  - **阶段二：潜在动作空间扩散（Diffusion on Latent Action Space）**——在紧凑潜在空间上做条件扩散，并以视觉抓取性线索（visual graspness cue）作为额外条件。

### 2.2 潜在空间中的抓取位姿引导
- 用轻量级 VAE 编码器将 $A$ 映射为紧凑潜变量 $Z = E(A)$；
- 将**目标抓取位姿 $G$** 与潜变量拼接后，由非对称解码器还原动作块：$\hat{A} = D(Z \oplus G)$；
- 训练损失：$L_{VAE} = \text{MSE}(A, \hat{A}) + \lambda L_{KL}$；
- 关键洞察：将抓取位姿引导放在**紧凑潜空间**中而非原始动作空间，避免了"位姿条件被其他观测稀释"以及"顺序推理增加延迟"的问题。

### 2.3 视觉抓取性线索（Visual Graspness Cue）
- 利用预训练 graspness 网络在腕视深度点云上计算逐点抓取性分数 $s_i \in [0,1]$；
- 将分数反投影到像素空间生成 graspness 映射 $M(j,k) = s_{\pi(j,k)}$；
- 阈值化后在腕视 RGB 图像上叠加掩码，得到条件图像 $O_{cue}$；
- **自监督重建损失**：在反扩散每一步从中间表示重建腕视图像：
  - $L_{Recon.} = \text{MSE}(O_{cue}, \hat{O}_{cue})$；
  - 总扩散损失：$L_{LDP} = L_{Diff.} + \lambda_{Recon.} L_{Recon.}$；
- 该设计鼓励策略**关注几何驱动的、亮度不变的抓取区域**，增强对光照变化等视觉干扰的鲁棒性。

### 2.4 启发式位姿选择器（HPS）
- 推理时需从候选集 $\mathcal{G}=\{G_0,\dots,G_m\}$ 中选出最合理的 $G^*$；
- 先做碰撞检测与非极大抑制（NMS），再保留 top-k 候选；
- 综合两个准则打分：抓取检测器的**质量分数** + 当前末端执行器位姿 $P$ 与候选 $G_j$ 的 **SE(3) 测地距离**；
- 使用加权矩阵 $W=\text{diag}(w_t,w_t,w_t,w_r,w_r,w_r)$ 使平移与旋转可比；
- 选取目标：$G^* = \arg\min_{G_j \in \mathcal{G}} d(G_j)$，从而保证运动学可行且轨迹平滑。

## 3. 实验设计

### 3.1 仿真环境
- **Benchmark**：LIBERO；
- **数据集**：从 LIBERO 中筛选并整理 **约 12K 高质量演示**，覆盖 **20 个物体** 的多种位姿与抓取姿态；
- **测试用未集划分**：
  - In Domain（ID）；
  - Spatial Generalization（SG）；
  - Object Generalization（OG）：取自 Graspnet-1Billion 的 similar/novel 划分，且对 GraspLDP 和预训练 grasp 检测器均未见过（公平对比）；
  - Visual Generalization（VG）：光照等视觉扰动。

### 3.2 真实机器人
- **平台**：Franka Research 3；
- **相机**：腕视 Intel RealSense D405、Agent 视 L515，GraspVLA 额外配备侧视 D405；
- **工作空间**：$50\times50\times20$ cm³；
- **物体集**：10 个训练 + 13 个测试日常物品（含刚体与少量铰接/可形变物体）；
- **演示采集**：每个训练物体 50 次，共 **500 次演示**；
- **测试协议**：每个物体在不同位姿下做 10 次试验，并设计 **4 个杂乱场景**（含堆叠物体）评估 SCR。

### 3.3 对比方法
- Diffusion Policy（基线）；
- OpenVLA（zero-shot 及在本数据集微调版）；
- GraspVLA（SOTA 通用抓取大模型）；
- AnyGrasp（专用于真实机器人对比）；
- **Ours Baseline**：仅将抓取位姿作为条件拼接，不使用两阶段潜空间设计（验证潜空间设计的必要性）；
- 评估指标：SR（成功率）、SCR（场景完成率）、**新指标 GFE（Grasp Frame Error）**量化策略遵循目标位姿引导的程度。

## 4. 资源与算力
- 论文**未明确说明训练所用的 GPU 型号、数量与训练时长**；
- 文中提到：
  - GraspVLA 训练 Syngrasp-1b 消耗 **160 块 RTX 4090 × 10 天**（用作对比，本文未沿用该路径）；
  - 推理延迟分析在单块 **RTX 4090** 上测量；
  - GraspLDP 相对 Diffusion Policy 仅增加约 **36 ms** 的 graspness 推理耗时与 **<1 ms** 的潜变量解码，总延迟仅高约 **15%**；比 torch.compile 加速后的 GraspVLA 低 **154 ms**。

## 5. 实验数量与充分性

- **仿真主表（Table 1）**：在 ID / SG / OG / VG 四个评估划分上对比 5 种方法，每划分 325 次试验，统计充分；
- **消融实验（Table 2）**：对 Graspness Cue（GC）与 Latent Guidance（LG）进行 5 种组合消融，含 Ours Baseline（CG）对照，同时报告 SR 与 GFE；
- **位姿选择策略消融（Table 3）**：对比 Random / Highest Score / Nearest / **HPS** 四种策略；
- **推理延迟分析（Figure 4）**：在相同动作 horizon 下量化对比；
- **真实机器人 SR（Table 4）**：合并 ID&SG，含 OG 与 VG；
- **杂乱场景（Table 5）**：4 个递进难度场景，含堆叠；
- **动态抓取（Table 6）**：3 类动态任务（运动中的香蕉 / 西瓜 / 交接水杯）；
- **定性可视化（Figure 5）**：仿真 + 真实世界对比；
- **总体评估**：覆盖仿真/真实两个域、多种泛化维度、消融、效率与定性分析，**实验设计较为充分与公平**（例如 OG 物体对检测器与策略均未见过、相同演示数据训练 DP 与 GraspLDP）。

## 6. 主要结论与发现

- **仿真（Table 1）**：相对 Diffusion Policy，ID 提升 **+17.5%**（62.8→80.3），SG **+22.2%**、OG **+46.8%**、VG **+48.3%**，平均 SR 从 34.9 提升到 **68.6**；
- **真实机器人（Table 4）**：ID&SG 取得 **84.0%** SR（最佳），OG 75.0%，VG 77.0%，综合 **78.7%**，与 AnyGrasp（79.7%）相当，远超 Diffusion Policy（43.0%）与 GraspVLA（26.0%）；
- **杂乱场景（Table 5）**：与 AnyGrasp 并列最高 SCR 92.3%，SR 高 12.7%，且能处理堆叠场景；
- **动态抓取（Table 6）**：GraspLDP 是唯一在三类动态任务中均成功的策略；
- **消融结论**：
  - 去除 LG（改用 CG 条件）时 GFE 显著上升，说明**潜空间引导**比条件拼接更精确；
  - 去除 GC 后 VG 性能下降最明显，验证**几何驱动的 graspness 对光照鲁棒**；
  - HPS 在 ID/SG/OG/VG 上均显著优于 Random/Highest/Nearest 单准则选择。

## 7. 优点与亮点

- **方法创新**：
  - 将抓取位姿引导**置于潜空间**而非原始动作空间，兼顾引导强度与推理效率；
  - 首次将 **graspness（几何抓取性）** 与 **grasp pose** 两种异质先验系统性地融入 latent diffusion policy；
  - 自监督重建目标迫使网络真正利用 graspness 视觉提示，而非仅作条件旁路；
  - HPS 同时考虑**抓取质量与运动学邻近度**，生成更平滑可行的轨迹，特别有利于动态抓取。
- **实验亮点**：
  - 设计 GFE 新指标，量化"策略遵循目标位姿的程度"；
  - 同时覆盖仿真与真实机器人、静态/杂乱/动态场景；
  - 推理延迟分析显示方法**接近 Diffusion Policy 的实时性**，远超 GraspVLA；
  - 与 AnyGrasp 在单物体演示训练下在杂乱场景中表现相当，说明闭环策略有效继承了开环检测器的泛化能力。

## 8. 不足与局限

- **应用范围局限**：作者明确指出，对**高度可形变或易碎物体**（如鸡蛋、烧杯）仍存在挑战，未来计划融合高频触觉与力/力矩信号；
- **实验覆盖局限**：
  - 仿真训练数据仅 12K 演示、20 个物体，规模相对有限；
  - 真实机器人演示仅 500 次，且仅在单一 Franka 平台、单一工作空间大小下验证；
  - 杂乱场景仅 4 个，动态抓取任务仅 3 类，覆盖广度有限；
- **算力信息缺失**：训练资源、收敛时间等关键复现信息未在文中给出；
- **方法可解释性与失败分析有限**：未对失败案例做系统性分类分析；
- **潜在偏差风险**：
  - HPS 中权重矩阵 $W$ 的取值对结果影响较大，但文中未充分讨论其敏感性；
  - Graspness 阈值 $\tau$ 等超参数缺少消融；
  - 与 GraspVLA 在真实机器人上未做相机/数据完全对齐的公平性说明。

（完）
