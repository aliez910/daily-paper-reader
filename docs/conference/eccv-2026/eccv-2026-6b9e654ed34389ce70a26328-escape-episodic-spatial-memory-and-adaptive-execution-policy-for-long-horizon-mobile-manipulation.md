---
title: "ESCAPE: Episodic Spatial Memory and Adaptive Execution Policy for Long-Horizon Mobile Manipulation"
title_zh: ESCAPE：面向长视野移动操纵的情景空间记忆与自适应执行策略
authors: "Jingjing Qian, Zeyuan He, Chen Shi, Lei Xiao, Li Jiang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4955.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向长视野移动操纵的自适应执行策略
tldr: 在复杂室内环境中协调导航与操纵的鲁棒性能对具身AI至关重要，但现有方法在任务视野延长时常因灾难性遗忘、空间不一致和僵硬执行而失效。本文提出ESCAPE，通过紧密耦合的感知-定位-执行工作流解决这些问题。在感知层面，ESCAPE具备时空融合建图模块以自回归构建无需深度估计的持久三维空间记忆，以及记忆驱动的目标定位模块以生成精确交互掩码。该工作虽然侧重移动操纵的导航-操作协调而非直接模仿学习，但仍属于机器人操纵任务与控制范畴，对复杂环境下的视觉反馈执行策略具有方法贡献。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 404, \"height\": 404}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 404, \"height\": 404}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-003.webp\", \"caption\": \"\", \"page\": 5, \"index\": 3, \"width\": 536, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-004.webp\", \"caption\": \"\", \"page\": 7, \"index\": 4, \"width\": 888, \"height\": 610}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-005.webp\", \"caption\": \"\", \"page\": 9, \"index\": 5, \"width\": 438, \"height\": 448}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-006.webp\", \"caption\": \"\", \"page\": 13, \"index\": 6, \"width\": 761, \"height\": 1097}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-007.webp\", \"caption\": \"\", \"page\": 13, \"index\": 7, \"width\": 761, \"height\": 1097}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-008.webp\", \"caption\": \"\", \"page\": 14, \"index\": 8, \"width\": 760, \"height\": 1096}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6b9e654ed34389ce70a26328/fig-009.webp\", \"caption\": \"\", \"page\": 14, \"index\": 9, \"width\": 760, \"height\": 1096}]"
motivation: 长视野移动操纵面临灾难性遗忘、空间不一致和僵硬执行等挑战。
method: 提出ESCAPE框架，结合时空融合建图、记忆驱动目标定位与自适应执行策略。
result: 实现了长视野复杂室内环境中导航与操纵的鲁棒协调。
conclusion: 为长视野移动操纵提供了一种紧密耦合的感知-定位-执行一体化方案。
---

## Abstract
Coordinating navigation and manipulation with robust per-formance is essential for embodied AI in complex indoor environments.However, as tasks extend over long horizons, existing methods oftenstruggle due to catastrophic forgetting, spatial inconsistency, and rigidexecution. To address these issues, we propose ESCAPE (EpisodicSpatial memory Coupled with an Adaptive Policy for Execution), op-erating through a tightly coupled perception-grounding-execution work-flow. For robust perception, ESCAPE features a Spatio-Temporal FusionMapping module to autoregressively construct a depth-estimation-free,persistent 3D spatial memory, and a Memory-Driven Target Groundingmodule for precise interaction mask generation. To achieve flexible ac-tion, our Adaptive Execution Policy dynamically orchestrates proactiveglobal navigation and reactive local manipulation to seize opportunis-tic targets. ESCAPE achieves state-of-the-art performance on the AL-FRED benchmark, reaching 65.09% and 60.79% success rates in test seenand unseen environments with step-by-step instructions. By reducing re-dundant exploration, our ESCAPE substantially improves path-length-weighted metrics and remains robust (61.24%/56.04%) even without de-tailed guidance for long-horizon tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "ESCAPE: Episodic Spatial Memory and Adaptive Execution Policy for Long-Horizon Mobile Manipulation" organized in a specific structure. Let me carefully read through the paper content and create a comprehensive summary covering all 8 required points.

Let me organize my thoughts:

1. Core problem and motivation: Long-horizon mobile manipulation in embodied AI, three challenges - catastrophic forgetting, spatial inconsistency, rigid execution.

2. Methodology: ESCAPE framework with three components:
   - Spatio-Temporal Fusion Mapping (OME + MRU)
   - Memory-Driven Target Grounding
   - Adaptive Execution Policy (proactive global planner + reactive local monitor)

3. Experiments: ALFRED benchmark, compared with multiple baselines (Seq2Seq, MOCA, E.T., HLSM, ABP, FILM, LGS-RPA, Prompter, CAPEAM, DISCO, ThinkBot)

4. Resources: 8 RTX 4090 GPUs, 24 hours for main training, 2 hours for reactive local monitor

5. Experiment count and adequacy: Multiple ablations, comparison tables, qualitative results

6. Conclusions: SOTA on ALFRED, significant improvements in PLW metrics

7. Strengths: depth-estimation-free memory, adaptive execution, strong quantitative results

8. Limitations: Sim2Real gap, reliance on simulator supervision

Let me write this out in proper Chinese Markdown format.</think>

# ESCAPE 论文总结：面向长视野移动操纵的情景空间记忆与自适应执行策略

## 1. 核心问题与整体含义（研究动机与背景）

- **研究主题**：在复杂室内环境中，具身智能体需要同时完成**长视野导航**与**精细物体操纵**，这是具身 AI 走向日常家务任务的关键能力。
- **应用场景**：以 ALFRED benchmark 为代表的**长视野家庭任务**，要求智能体根据自然语言指令完成"移动到 A、拿起 B、放置到 C"等多步组合任务。
- **现有方法三大瓶颈**：
  - **灾难性遗忘（Catastrophic Forgetting）**：端到端方法（Seq2Seq、MOCA、E.T.）直接将当前观测映射为动作，缺乏持久空间记忆，导致在已访问区域反复探索。
  - **空间不一致（Spatial Inconsistency）**：模块化方法（FILM、CAPEAM、DISCO、ThinkBot）依赖不准确的深度估计将 2D 语义反投影到 3D 空间，误差在长视野任务中累积。
  - **僵硬执行（Rigid Execution）**：基于手工策略的方法（FILM、Prompter、CAPEAM）无法对状态变化或近距离目标的出现做出即时反应，只能按既定长路径执行。
- **论文目标**：构建一个**以记忆为中心**的框架，紧密耦合"感知 → 定位 → 执行"工作流，从根本上同时解决以上三个问题。

## 2. 方法论

### 2.1 整体框架
- **两大支柱**：
  - **情景空间记忆（Episodic Spatial Memory）**：负责鲁棒感知与精确交互定位。
  - **自适应执行策略（Adaptive Execution Policy, AEP）**：负责灵活行动，动态切换长期规划与即时操作。
- **工作流**：观测 → 时空融合建图（更新 3D 记忆）→ 记忆驱动目标定位（生成交互掩码与场景语义图）→ 自适应执行（全局规划 + 局部监视器）。

### 2.2 时空融合建图（Spatio-Temporal Fusion Mapping）
- **空间划分**：将 25m × 25m 的房间划分为 100 × 100 的栅格（每格 25 cm），每个栅格单元维护一个 C=256 维的可学习查询 $Q_p$。
- **OME（Observation-to-Memory Encoding）机制**：
  - 将每个 2D 栅格 $p=(x,y)$ 沿高度采样 $N_{ref}$ 个 3D 参考点 $(x,y,z_i)$；
  - 利用相机投影矩阵 $P$ 将 3D 点投影到 2D 图像平面：
  
    $$z'_i \cdot [x'_i, y'_i, 1]^T = P \cdot [x, y, z_i, 1]^T$$
  - 通过**可变形注意力（Deformable Attention）**在投影点附近采样图像特征，从而避免深度估计误差。
- **MRU（Memory Retrieval and Update）机制**：
  - 当前时刻查询 $Q$ 与上一时刻记忆 $M_{t-1}$ 通过可变形注意力融合：
    
    $$\text{MRU}(Q_p, \{Q, M_{t-1}\}) = \sum_{V \in \{Q, M_{t-1}\}} \text{DeformAttn}(Q_p, p, V)$$
  - 同时聚合**时间信息**（防止遗忘）与**空间邻域信息**（增强空间推理）。
- **输出**：更新后的 3D 记忆 $M_t \in \mathbb{R}^{H \times W \times C}$，再通过 3D 语义分割头生成网格化的语义场景图，损失为 BCE 损失 $L_{map}$。

### 2.3 记忆驱动目标定位（Memory-Driven Target Grounding）
- **核心思想**：利用已存储的 3D 记忆特征生成对象查询，避免传统静态查询的局限性。
- **算法流程**：
  1. 在语义场景图中取出目标对象通道为 1 的栅格集合 $G_{object}$；
  2. 对这些栅格的记忆特征进行**平均池化**得到 3D 对象特征 $F_{object}$；
  3. 通过 MLP 编码为对象查询 $Q_{object}$；
  4. 与当前帧经过卷积映射的 2D 视觉特征做相似度计算，生成**精确交互掩码**。
- **训练损失**：$L = L_{map} + \lambda L_{img}$，其中 $\lambda = 1.0$，联合监督 3D 地图分割与 2D 图像分割。

### 2.4 自适应执行策略（Adaptive Execution Policy）
- **三个子模块**：
  - **随机探索**：未检测到目标时，基于"仅地面为 1 的可导航图"用 BFS 随机选点。
  - **主动全局规划器（Proactive Global Planner）**：检测到目标后，在记忆中找到目标最高概率栅格，扩展 1 m 可达邻域，用 BFS 生成长期导航路径（基于规则，无训练）。
  - **反应式局部监视器（Reactive Local Monitor）**：ResNet50 + 线性分类器，输出"对象是否可操纵"的二值向量；通过具有完整场景知识的专家规划器收集的 332,432 张训练图监督训练。
- **动态切换机制**：在执行全局路径时，监视器持续检测近距离机会目标，一旦发现可操纵目标即**抢占**全局规划，直接执行即时抓取动作；多实例目标（如土豆）靠监视器机会主义发现，大型唯一目标（如冰箱）靠记忆精确定位；存在**分层回退策略**处理监视器失效的情形。

## 3. 实验设计

- **数据集 / Benchmark**：ALFRED（25,726 episodes；训练 21,023、验证 1,641、测试 3,062）。
- **场景**：模拟家庭室内环境（AI2-THOR 仿真），任务包含分步指令与高层目标描述两种模式。
- **评估指标**：Success Rate（SR）、Goal Condition（GC）、Path Length Weighted SR（PLWSR）、PLWGC。
- **对比方法**：
  - 端到端类：Seq2Seq、MOCA、E.T.、HLSM、ABP。
  - 模块化记忆类：FILM、LGS-RPA、Prompter、CAPEAM、DISCO、ThinkBot。
- **对比设置**：在"使用分步指令"与"不使用分步指令"两种设定下分别对比，并对 Test Seen 与 Test Unseen 两个测试集均做评估。

## 4. 资源与算力

- **GPU 型号与数量**：8 块 RTX 4090。
- **训练时长**：
  - 主模型（Spatio-Temporal Fusion + Target Grounding）：约 **24 小时**（25 epochs，batch size 64，学习率 2e-4，AdamW）。
  - 反应式局部监视器：约 **2 小时**（40 epochs，batch size 128，学习率 5e-5）。
- **其他实现细节**：使用 ResNet50 backbone，记忆查询为可学习参数并联合优化，输入为 RGB 与语言指令。

## 5. 实验数量与充分性

- **主对比实验**：1 张大表覆盖 12 种方法 × 4 项指标 × 2 种指令模式 × 2 种测试场景，共 **64 个数据点**。
- **消融实验**（验证集 seen/unseen）：
  - 移除 OME、移除 MRU、移除 AEP；
  - 替换为 GT 掩码、静态查询；
  - 不同栅格分辨率（80×80、100×100、120×120）。
- **附加定量分析**：地图 / 图像 mIOU 与效率因子 EF（EF = PLWSR / SR）。
- **定性分析**：图 5 展示时空融合建图对包含关系（CD 在箱中）的处理能力；图 6 展示 AEP 在"取勺子"任务中将步数从 5 步缩减到 2 步。
- **充分性评价**：
  - 实验覆盖了组件级消融、超参数（栅格尺寸）、对比方法（最新 SOTA ThinkBot）、指令模式（带/不带分步指令）、未见场景泛化等多个维度，**较为充分**。
  - 标准差数据放在附录 E 中（声称 3 次随机种子运行），具备一定的统计可靠性。
  - 但仅在 ALFRED 单个 benchmark 上验证，未在其他长视野任务（如 HomeRobot、行为基准 BEHAVIOR、EmbodiedBench）上评测，**泛化广度有限**。

## 6. 主要结论与发现

- **SOTA 性能**：在 ALFRED 上取得**当前最优**，分步指令下 Test Seen / Unseen 成功率分别为 **65.09% / 60.79%**，比此前的 ThinkBot 分别提升 2.40% 和 2.97%。
- **效率显著提升**：路径加权指标 PLWSR 在 Seen 上达到 52.42%、Unseen 上达到 46.82%，相比 DISCO 提升约 10+ 个百分点，说明冗余探索大幅减少。
- **无指令鲁棒**：在仅高层目标的设定下仍达到 61.24%/56.04% 的成功率，证明自适应执行策略对"无详细指导"的真实场景更鲁棒。
- **消融关键发现**：
  - **MRU 是最关键模块**（移除后 SR 暴跌 19.52%/34.11%），表明时空记忆对长视野任务至关重要。
  - **OME 中等重要**（移除后 SR 下降 8.78%/8.53%）。
  - **AEP 主要贡献于效率**：移除后 SR 降 4.73%/4.14%，但 PLW 指标下降更大。
  - **栅格分辨率 100×100 最优**，过粗或过细都会显著掉点。
- **交互精度**：图像分割 mIOU 0.869/0.779，使用生成的掩码与 GT 掩码仅差 0.24%/2.55%，说明目标定位模块已**接近感知上限**，任务瓶颈不在交互精度而在导航策略。

## 7. 优点

- **方法新颖性**：
  - 提出**无需深度估计**的 3D 记忆构建（3D→2D 投影取代传统 2D→3D 反投影），从根本上切断深度误差积累。
  - **时空融合建图 + 自适应执行**的紧耦合设计同时解决三个长期痛点。
- **工程完整度**：OME 与 MRU 均采用可变形注意力以控制计算量，框架在 100×100 栅格、256 维特征下仍可实时推理。
- **执行策略灵活性**：通过"主动规划 + 反应式监视器"的层次化机制，把传统单一长视野规划升级为"随时可中断 + 机会主义抓取"，将"取土豆"类任务步数从 5 步压缩到 2 步，效果直观。
- **实验数据扎实**：组件级消融完整，含 mIOU 与 EF 等附加定量指标，含定性可视化与失败案例分析。

## 8. 不足与局限

- **监督依赖**：所有训练信号（语义地图、图像掩码、可操纵性标签）均**来自仿真器**，限制了在真实场景的应用。论文在 Limitations 中承认这一点，并提出未来可用基础模型生成伪标签或真实机器人自训练来缓解。
- **单一基准**：仅在 ALFRED 上验证，未在 HomeRobot、BEHAVIOR、EmbodiedBench 等其他长视野基准上评测，难以判断方法对其他任务/场景的迁移性。
- **缺乏真实机器人实验**：方法是否能在真实噪声、动态干扰下保持性能未知，**Sim-to-Real 差距未评估**。
- **反应式监视器数据量**：训练样本来自"专家规划器 + 全场景知识"，实际部署时可能存在分布偏移。
- **规则化回退策略**：自适应执行策略中"分层回退"仍以规则形式给出，对复杂组合情形（如多个潜在目标同时出现）的最优行为缺乏学习式方案。
- **效率指标的解释性**：EF = PLWSR / SR 是作者自定义指标，未必与实际部署时间/能耗直接对应。
- **任务设定假设**：ALFRED 任务只要求"放置任一目标到任一容器"，方法通过语义类别而非实例区分解决，多实例/同类别细分任务下的能力未被验证。

（完）
