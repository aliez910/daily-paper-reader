---
title: "Beyond Success: Refining Elegant Robot Manipulation from Mixed-Quality Data via Just-in-Time Intervention"
title_zh: 超越成功：通过即时干预从混合质量数据中精炼优雅的机器人操作
authors: "Mao, Yanbo, Fu, Jianlong, Zhang, Ruoxuan, Xie, Hongxia, Yao, Meibao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Mao_Beyond_Success_Refining_Elegant_Robot_Manipulation_from_Mixed-Quality_Data_via_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: LIBERO-Elegant 基准用于评估 VLA 模型的机器人操作执行质量
tldr: 作者观察到用于通用机器人操作的视觉-语言-动作模型因演示数据质量参差，常出现执行质量不稳定的问题。本文超越单纯的成败评估，提出 LIBERO-Elegant 基准与显式的执行质量准则，并基于即时干预设计了去耦的精炼框架，以隐式任务约束形式化优雅执行。实验表明该方法无需重训基础 VLA 策略即可提升执行质量，既推动了模仿学习操作的基准评测，也丰富了 VLA 模型的优化方法。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1793, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 821, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1795, \"height\": 410, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 1060, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-mao-beyond-success-refining-elegant-robot-manipulation-from-mixed-quality-data-via-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 292, \"label\": \"Table\"}]"
motivation: VLA 模型因演示数据质量不一，常出现执行质量不稳定的问题。
method: 提出 LIBERO-Elegant 基准与基于即时干预的去耦精炼框架，以隐式任务约束形式化优雅执行。
result: 在不重训基础 VLA 策略的前提下提升了操作的执行质量与一致性。
conclusion: 该工作为模仿学习操作的执行质量评估与模型精炼提供了新基准与方法。
---

## Abstract
Vision-Language-Action (VLA) models have enabled notable progress in general-purpose robotic manipulation, yet their learned policies often exhibit variable execution quality. We attribute this variability to the mixed-quality nature of human demonstrations, where the implicit principles that govern how actions should be carried out are only partially satisfied. To address this challenge, we introduce the LIBERO-Elegant benchmark with explicit criteria for evaluating execution quality. Using these criteria, we develop a decoupled refinement framework that improves execution quality without modifying or retraining the base VLA policy. We formalize Elegant Execution as the satisfaction of Implicit Task Constraints (ITCs) and train an Elegance Critic via offline Calibrated Q-Learning to estimate the expected quality of candidate actions. At inference time, a Just-in-Time Intervention (JITI) mechanism monitors critic confidence and intervenes only at decision-critical moments, providing selective, on-demand refinement. Experiments on LIBERO-Elegant and real-world manipulation tasks show that the learned Elegance Critic substantially improves execution quality, even on unseen tasks. The proposed model enables robotic control that values not only whether tasks succeed, but also how they are performed.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Beyond Success: Refining Elegant Robot Manipulation from Mixed-Quality Data via Just-in-Time Intervention". I need to organize it according to the 8 points specified, using Markdown format with hierarchical headings and bullet points. Let me analyze the paper content carefully:

1. Core problem and motivation: VLA models have variable execution quality due to mixed-quality human demonstrations. The focus is on "how" actions are executed, not just success/failure.

2. Methodology:
- Formalize Elegant Execution via Implicit Task Constraints (ITCs)
- LIBERO-Elegant Benchmark with Success and Elegance criteria
- Elegance Critic trained via offline Calibrated Q-Learning (Cal-QL)
- Just-in-Time Intervention (JITI) mechanism based on Q-value fluctuation
- Three-stage framework: base VLA training, critic training, inference-time intervention

3. Experiments:
- LIBERO-Elegant benchmark (8 tasks, 327 episodes, ~52.7K frames)
- LIBERO-Object for generalization (seen vs unseen)
- 6 real-world tasks on SO-100 robot arm
- Compared with π0.5, Isaac GR00T N1, SmolVLA, Isaac GR00T N1.5

4. Resources:
- SmolVLA trained 100k steps, batch size 64, on NVIDIA RTX 5090
- Isaac GR00T N1.5 finetuned 50k steps, batch size 16, on 4× NVIDIA A40
- Elegance Critics trained 20k steps, batch size 32, on RTX 5090, AdamW, lr=1e-5

5. Number and adequacy of experiments:
- 8 LIBERO-Elegant tasks
- Generalization experiments on seen/unseen subsets
- Ablation on JITI vs Full-Guidance
- Ablation on reward formulation (binary vs task-specific)
- Real-world validation on 6 tasks, 50 rollouts each

6. Main conclusions:
- JITI-guided Elegance Critic improves ESR significantly
- Average ESR improvement: SmolVLA +17.4 pts, GR00T +21.2 pts
- Generalizes to unseen tasks without retraining
- Reduces intervention count by 60%+ vs Full-Guidance

7. Strengths:
- Decoupled framework (non-invasive)
- Event-driven, plug-and-play
- Model-agnostic (works with SmolVLA and GR00T)
- Effective both in simulation and real-world
- Reduces computation by selective intervention

8. Limitations:
- Evaluation only on 8 LIBERO-Elegant tasks (small)
- Real-world experiments only on SO-100 arm
- May have threshold sensitivity for JITI
- Reward annotation requires human effort
- Limited comparison with other quality-aware methods

Let me write this up in proper Chinese with Markdown formatting.</think>

# 论文总结：Beyond Success — 通过即时干预从混合质量数据中精炼优雅的机器人操作

## 1. 核心问题与研究动机

- **研究对象**：面向通用机器人操作的视觉-语言-动作（VLA）模型（如 π0.5、Isaac GR00T、SmolVLA 等）。
- **核心问题**：尽管 VLA 模型在任务成功率上表现优异，但**执行质量不稳定**（variable execution quality）。
- **归因分析**：作者认为这种波动来自人类演示数据的**混合质量（mixed-quality）特性**——既有专家级示范，也包含犹豫修正、低效运动甚至失败轨迹；标准的模仿学习（BC）继承了这种行为分布，导致推理时表现参差。
- **关键洞察**：模型具备高质量执行的能力，但无法稳定表达。因此需要一个**解耦的精炼机制**，在不重训基础策略的前提下提升"如何做"（how）而非仅"是否完成"（whether）。
- **形式化定义**：提出 **Implicit Task Constraints（ITCs，隐式任务约束）** 概念，将同时满足任务目标和 ITC 的轨迹称为 **Elegant Execution（优雅执行）**。

## 2. 方法论

### 2.1 整体框架：三阶段去耦设计

- **Stage 1**：在混合质量数据上训练基础生成式 VLA 策略 πθ（建模整体行为分布）。
- **Stage 2**：利用 LIBERO-Elegant 标注，通过离线 Calibrated Q-Learning（Cal-QL）训练轻量化 Elegance Critic Qϕ。
- **Stage 3**：推理时通过 Just-in-Time Intervention（JITI）机制，在决策关键点选择性介入。

### 2.2 基础生成策略（Flow-Matching VLA）

- πθ 实现为基于 Transformer 的 **Flow Matching 生成模型**。
- 输入当前状态 $s_t$ 与噪声水平 τ 下的"含噪动作" $A_t^\tau = \tau A_t + (1-\tau)\epsilon$，网络 $v_\theta$ 预测指向干净动作的速度场。
- 训练损失：
  $$\mathcal{L}_{FM}(\theta) = \mathbb{E}_{\tau,(s_t,A_t),\epsilon}\left[\left\|v_\theta(A_t^\tau, s_t) - (A_t - \epsilon)\right\|_2^2\right]$$
- 推理时可从不同噪声初始化采样多个候选动作，为 JITI 提供多样性基础。

### 2.3 Elegance Critic（离线 Cal-QL 训练）

- **架构**：冻结 VLA 的 VLM 主干 + 基于 VLM 的精炼头，输出与动作、奖励拼接后的 Q 值。
- **目标**：估计满足 ITC 的累积优雅回报。
- **核心挑战**：既要对细粒度优雅奖励保持敏感，又要避免 OOD 动作的过估计 → 采用 Cal-QL。
- **校准正则项**：
  $$\mathcal{R}_{cal}(\phi) = \mathbb{E}_{s\sim D}\left[\max\left(\mathbb{E}_{a\sim\pi(\cdot|s)}Q_\phi(s,a), V^\mu(s)\right) - \mathbb{E}_{a\sim D(\cdot|s)}Q_\phi(s,a)\right]$$
- **完整目标**：$\mathcal{L}_{Cal-QL}(\phi) = \mathcal{L}_{Bellman}(\phi) + \lambda_{cal}\mathcal{R}_{cal}(\phi)$，其中 Bellman 损失使用目标网络 $Q_{\phi'}$。

### 2.4 Just-in-Time Intervention（JITI）算法

- **核心思想**：轨迹整体优雅性由少量**决策关键点**决定，多数时刻局部决策是明确的。
- **关键指标 — Q 值波动**：
  $$\Delta q_t = |q_t - \bar{q}_t|$$
  其中 $q_t = Q_\phi(s_t, A_t^0)$ 为默认动作的 Q 值，$\bar{q}_t$ 为短窗口均值。
- **触发逻辑**：
  - 若 $\Delta q_t \leq \tau$（非关键点）→ 直接执行默认动作，单次 critic 评估即可。
  - 若 $\Delta q_t > \tau$（关键点）→ 采样 N 个候选动作，逐一用 critic 打分，执行 $\arg\max_a Q_\phi(s_t, a)$。
- **波动来源**：稀疏优雅奖励产生的 Bellman 尖峰 + Cal-QL 对 OOD 动作的保守惩罚。

## 3. 实验设计

### 3.1 基准与数据集

- **LIBERO-Elegant（自建）**：8 个对执行质量敏感的操作任务，327 个演示回合，约 52.7K 帧 RGB-D + 本体感知数据；其中 148 个回合具有高质量优雅执行，并在关键的 25 帧窗口上做了优雅标注。
- **优雅评估四维度**：
  1. Task Sequence Integrity（任务序列完整性）
  2. Target Pose Accuracy（目标位姿精度）
  3. Pose Alignment（姿态对齐）
  4. Collision-Free Execution（无碰撞执行）
- **泛化测试**：LIBERO-Object 中的 Pick-and-Place 任务，已见（milk、ketchup 等）vs 未见（salad dressing、BBQ sauce、tomato sauce、orange juice 等）。

### 3.2 对比方法

- **基线 VLA**：SmolVLA（450M，基础策略）、Isaac GR00T N1.5（3B，基础策略）。
- **其他参考**：π0.5、Isaac GR00T N1（表 1 列出但不直接叠 JITI）。
- **消融对照**：
  - 无指导的基础策略
  - Full-Guidance：每个时间步都做 N 样本评估
  - JITI（本文方法）
  - 二元奖励 vs 任务特定优雅奖励

### 3.3 评估指标

- **Elegant Success Rate（ESR）**：必须同时达成任务目标且满足所有优雅约束；每个任务平均 50 次 rollout。

### 3.4 真实世界验证

- 平台：SO-100 机械臂，基础策略为 SmolVLA。
- 6 个真实任务（关抽屉、摆放、多物体堆叠等），每个任务 50 次 rollout。

## 4. 资源与算力

| 组件 | 训练步数 / Batch Size | 硬件 |
|---|---|---|
| SmolVLA 基础策略 | 100k 步 / BS=64 | 1× NVIDIA RTX 5090 |
| Isaac GR00T N1.5 基础策略 | 50k 步 / BS=16 | 4× NVIDIA A40 |
| Elegance Critic | 20k 步 / BS=32 | 1× RTX 5090 |

- 优化器：AdamW，学习率 $1\times 10^{-5}$。
- Critic VLM 精炼头：SmolVLM2-256M-Video-Instruct（SmolVLA 版）、Eagle2-1B（GR00T 版）。
- **未明确说明**：单次实验总墙钟时间、推理延迟、阈值 τ 与窗口大小 k 的取值细节（仅在 Supp. 中给出）。

## 5. 实验数量与充分性

- **主实验**：8 个 LIBERO-Elegant 任务 × 2 个 VLA 主干 × 50 rollouts → 约 800 次仿真回合/配置。
- **消融实验**：
  - JITI vs Full-Guidance vs 无指导（8 任务对照 + 平均干预次数对比）。
  - 优雅奖励消融（二元 vs 任务特定，8 任务对照）。
- **泛化实验**：3 个已见任务 + 4 个未见任务，各 50 rollouts。
- **真实世界**：6 任务 × 50 rollouts = 300 次实操回合。
- **充分性评估**：
  - 涵盖仿真消融、跨模型迁移、跨任务泛化、真实世界四个维度，较为系统。
  - 对照方法数量适中，但缺少与近同期质量感知方法（如 Phoenix、HUME、Value Guidance 等）的直接同条件对比。
  - 任务数仍偏少（8 个），统计显著性未在文中显式检验。

## 6. 主要结论与发现

- **效果显著且跨模型一致**：
  - SmolVLA 平均 ESR：49.8% → **67.2%**（+17.4 pts）。
  - GR00T N1.5 平均 ESR：46.0% → **67.2%**（+21.2 pts）。
  - 多个单项任务提升 10–30+ pts。
- **JITI 比 Full-Guidance 更高效**：在 ESR 更高的同时，**平均干预次数减少超过 60%**。
- **奖励形式化是关键**：任务特定优雅奖励（67.2%）显著优于二元奖励（56.8%），说明细粒度 ITC 监督不可或缺。
- **优雅概念可迁移**：在未见但语义相似的 Pick-and-Place 任务上，ESR 从 53.0% 提升至 68.6%，证明 critic 学到的是可迁移的行为先验而非任务记忆。
- **真实世界有效**：6 任务平均 ESR 从 34.3% 提升至 58.0%（+23.7 pts），在堆叠、摆放等精度敏感任务上提升尤为明显。
- **结论**：模仿学习操作不仅要关注"是否成功"，更要关注"如何执行"；隐式执行质量可被学习并在推理时显式利用。

## 7. 优点与亮点

- **概念创新**——首次将"优雅执行"形式化为 ITC 的满足，并显式构建基准。
- **非侵入、即插即用**——无需重训基础 VLA，可叠加在任意生成式 VLA 之上（模型无关）。
- **事件驱动高效机制**——Q 值波动作为低开销不确定性信号，仅在关键点触发多采样评估。
- **离线 RL 选型合理**——Cal-QL 同时兼顾对细粒度优雅奖励的敏感性和 OOD 保守性。
- **实验跨层级**——仿真+真实世界、跨模型、跨任务（已见/未见）四重验证，逻辑闭环。
- **类人决策视角**——模仿人"在少量关键瞬间调整动作"的运动学习机理。

## 8. 不足与局限

- **基准规模偏小**：LIBERO-Elegant 仅 8 个任务、327 个回合、约 52.7K 帧；可能限制结论的泛化可信度。
- **优雅标注依赖人工**：25 帧关键窗口需多名标注者交叉验证，标注成本与一致性是落地瓶颈。
- **超参依赖**：JITI 阈值 τ 与窗口 k 需手工设定，文中未系统分析敏感性。
- **对比基线不够丰富**：缺少与 Phoenix、HUME、Value Guidance 等同期"解耦指导"类工作的对比。
- **真实世界范围有限**：仅在 SO-100 单臂、6 个相对简单的家庭任务上验证；未覆盖双臂、长 horizon、动态环境等更复杂场景。
- **干预次数仍非零**：平均每回合仍有约 6 次干预，延迟敏感场景下的实时性需进一步评估。
- **优雅维度固定**：四类 ITC 准则较为通用，但对某些任务可能不够完整（如力度控制、人类安全距离等）。
- **基础策略质量的隐性依赖**：若基础 VLA 在某任务上完全失败（成功率接近 0），critic 也难以挽救；方法对基础模型的最低能力存在隐含要求。

（完）
