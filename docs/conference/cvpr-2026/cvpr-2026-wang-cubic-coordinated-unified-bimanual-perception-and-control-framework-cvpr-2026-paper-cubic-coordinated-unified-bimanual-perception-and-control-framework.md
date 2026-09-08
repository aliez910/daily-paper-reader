---
title: "CUBic: Coordinated Unified Bimanual Perception and Control Framework"
title_zh: CUBic：面向双臂感知与控制的协调统一框架
authors: "Wang, Xingyu, Ding, Pengxiang, Xu, Jingkai, Wang, Donglin, Fan, Zhaoxin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Wang_CUBic_Coordinated_Unified_Bimanual_Perception_and_Control_Framework_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 直接从视觉输入学习端到端视觉运动策略以实现双臂操作
tldr: 现有视觉运动策略在从单臂扩展到双臂操作时面临困难，难以同时兼顾各臂独立感知与双臂协调。本文提出统一框架 CUBic，将双臂协同重新建模为统一感知问题，学习一种共享的 token 化表征以桥接感知与控制，从而在保持独立性的同时强化跨臂耦合。该方法在双臂操作任务上验证了端到端视觉控制的有效性，为通用化双臂策略提供了可扩展的方案，推动了复杂机器人操作中视觉运动学习的发展。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1786, \"height\": 670, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1613, \"height\": 782, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1801, \"height\": 713, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1250, \"height\": 662, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 385, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 287, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 549, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wang-cubic-coordinated-unified-bimanual-perception-and-control-framework-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 813, \"height\": 241, \"label\": \"Table\"}]"
motivation: 将端到端视觉运动策略从单臂操作扩展到双臂操作时，需要兼顾独立感知与跨臂协调。
method: 提出统一框架 CUBic，将双臂协同建模为统一感知问题，学习共享的 token 化表征以连接感知与控制。
result: 在双臂操作任务中实现了独立性与协调性的平衡，验证了端到端视觉控制的有效性。
conclusion: 该框架为复杂双臂操作提供了可扩展的通用视觉运动策略方案。
---

## Abstract
Recent advances in visuomotor policy learning have enabled robots to perform control directly from visual inputs. Yet, extending such end-to-end learning from single-arm to bimanual manipulation remains challenging due to the need for both independent perception and coordinated interaction between arms. Existing methods typically favor one side--either decoupling the two arms to avoid interference or enforcing strong cross-arm coupling for coordination--thus lacking a unified treatment. We propose CUBic, a Coordinated and Unified framework for Bimanual perception and control that reformulates bimanual coordination as a unified perceptual modeling problem. CUBic learns a shared tokenized representation bridging perception and control, where independence and coordination emerge intrinsically from structure rather than from hand-crafted coupling. Our approach integrates three components: unidirectional perception aggregation, bidirectional perception coordination through two codebooks with shared mapping, and a unified perception-to-control diffusion policy. Extensive experiments on the RoboTwin benchmark show that CUBic consistently surpasses standard baselines, achieving marked improvements in coordination accuracy and task success rates over state-of-the-art visuomotor baselines.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze a paper called "CUBic: Coordinated Unified Bimanual Perception and Control Framework" and provide a structured Chinese summary. Let me carefully read through the paper and organize my response according to the requested sections.

Let me analyze the paper:

1. **Core Problem**: Extending visuomotor policy learning from single-arm to bimanual manipulation. The challenge is balancing independence (avoiding interference) with coordination (enabling collaboration between arms). Existing methods favor one side over the other.

2. **Method**: CUBic - a framework with three components:
   - Unidirectional Perception Aggregation: uses masked attention to encode multi-view inputs (left, right, top views) into arm-specific perceptual tokens
   - Bidirectional Perception Coordination: uses two codebooks with shared mapping to enable cross-arm awareness while preserving autonomy
   - Unified Perception-to-Control Diffusion Policy: uses DiT with two-stage training

3. **Experiments**:
   - RoboTwin benchmark (simulation)
   - Real-world experiments on 6 tasks with Agibot
   - Compared with DP, DP3, GR-MG
   - Ablation studies on shared mapping, two-stage training, latent tokens/codebook size

4. **Resources**: 
   - 4 NVIDIA 4090 GPUs
   - Batch size 32 per GPU, total 128
   - 900 epochs per training stage

5. **Experimental quantity**:
   - 7 simulation tasks
   - 6 real-world tasks
   - Multiple ablations
   - 3 random seeds, 50 executions per seed

6. **Conclusions**: CUBic achieves 51.8% avg success rate, 12% over DP3, 13.3% over DP

7. **Strengths**: 
   - Unified framework addressing both independence and coordination
   - Shared codebook design
   - Two-stage training paradigm
   - No need for 3D perception

8. **Limitations**:
   - Limited real-world task diversity
   - Standard deviations not reported for some metrics
   - Only compared against a few baselines
   - Reliance on expert demonstrations

Let me organize this into a clean Chinese summary.</think>

# CUBic：面向双臂感知与控制的协调统一框架 — 论文总结

## 1. 核心问题与研究背景

- **研究主线**：端到端视觉运动策略（visuomotor policy learning）近年来发展迅速，但大多数工作仍聚焦于**单臂操作**，将其扩展到**双臂协调操作**仍面临挑战。
- **核心矛盾**：双臂操作需要在两个层面同时满足——
  - **独立性**：每个机械臂需独立感知、决策，避免相互干扰；
  - **协调性**：双臂之间需要空间与时间一致性，例如交接、协同搬运等任务。
- **现有方案的局限**：
  - 一类方法（如 AnyBimanual、TwinVLA）通过**解耦双臂感知与控制流**来保证稳定性，但牺牲了跨臂一致性；
  - 另一类方法（如 Mobile ALOHA、PerAct2、InterAct）通过**交叉注意力或消息传递**增强双臂通信，但可能削弱可分性与鲁棒性。
  - 两者目标（独立 vs. 交互）相互矛盾，缺乏**统一处理**。
- **本文主张**：将双臂协调重新建模为**统一的感知问题**，通过共享的 token 化表征，使独立性与协调性从结构中自然涌现，而非依赖手工设计的耦合机制。

---

## 2. 方法论

CUBic 框架包含**三个核心组件**，整体流程为：多视图感知 → arm-specific token 化 → 共享码本协调 → 扩散策略生成双臂动作。

### 2.1 单向感知聚合（Unidirectional Perception Aggregation）

- **输入**：左腕、右腕、顶部三个 RGB 相机 + 双臂关节状态（proprioception）。
- **编码**：
  - 视觉特征使用**独立的 ResNet-18** 提取；
  - 关节状态通过轻量 **MLP** 映射到相同维度；
  - 为每个手臂初始化 **N=4 个可学习 latent token** $a_q^{left}, a_q^{right} \in \mathbb{R}^{N \times d}$。
- **关键设计**：采用**带掩码的单向自注意力 Transformer**：
  - 腕部相机与关节状态被视为 arm-specific 局部信息；
  - 头部相机作为共享全局上下文；
  - **注意力掩码**保证两臂 latent token 仅能通过各自腕部相机 + 关节状态关注顶部相机特征，避免信息泄露。
- **目的**：在保留各臂自主性的同时，锚定到共享的全局上下文。

### 2.2 双向感知协调（Bidirectional Perception Coordination）

- **结构**：两个码本（codebook）$Z_{left}, Z_{right} \in \mathbb{R}^{K \times d_z}$，**共享映射空间**。
- **量化方式**（联合最小化）：
  $$d_{left,i} = \|a_q^{left} - a_{z,i}^{left}\|_2^2, \quad d_{right,i} = \|a_q^{right} - a_{z,i}^{right}\|_2^2$$
  $$i^* = \arg\min_i (d_{left,i} + d_{right,i})$$
- **关键技术**：
  - 采用**残差向量量化（RVQ）** 提升码本表达力与训练稳定性；
  - VQ 训练采用 **straight-through estimator** + **commitment loss**（式 12）；
  - 通过联合索引选择，使两臂 latent 表征**收敛到一致的语义空间**，实现隐式跨臂耦合。
- **目的**：在统一潜在流形上保持双臂语义对齐，同时保留功能独立性。

### 2.3 统一感知→控制（Unified Perception-to-Control）

- **策略网络**：基于 **DiT（Diffusion Transformer）**，通过交叉注意力融合感知嵌入 $Q_{left}, Q_{right}$。
- **扩散过程**：训练 100 步 cosine 噪声调度，推理时使用 **DDIM** 降为 10 步。
- **两阶段训练范式**（图 3）：
  1. **Stage 1 - 单臂预训练**：双臂各用独立的 DiT 分支（含 self-attn / cross-attn / FFN），动作沿运动维度切分，分别学习各自的扩散损失 $\mathcal{L}_{left}^{diff} + \mathcal{L}_{right}^{diff} + \mathcal{L}_{VQ}$；
  2. **Stage 2 - 双臂协调后训练**：**冻结感知模块**，将两臂 DiT 中的 **self-attention 层合并**（共享），而 **cross-attention 路径独立**，从而在控制层引入显式跨臂交互，同时保持感知解耦。
- **核心思想**：先在感知层学会协同表征，再在控制层引入交互，避免端到端联合训练的不稳定性。

---

## 3. 实验设计

### 3.1 仿真实验

- **基准**：**RoboTwin**[37]（基于 ManiSkill2，包含 7 个双臂任务，每个任务 100 条专家演示，250–850 步）。
- **任务列表**（Table 1）：
  - Pick Apple（Messy）、Dual Bottles Pick (Easy)、Blocks Stack (Easy)、Dual Bottles Pick (Hard)、Dual Shoes Place、Handover Cabinet、Put Apple。
- **对比基线**：
  - **Diffusion Policy (DP)** [6] — 2D 扩散策略；
  - **3D Diffusion Policy (DP3)** [58] — 基于稀疏点云的 3D 扩散策略；
  - **GR-MG** [29] — 多模态目标条件视频生成策略。
- **评估指标**：3 个随机种子、每种子 50 次执行的成功率均值 ± 标准差。

### 3.2 真实世界实验

- **硬件**：Agibot 双臂平台 + 3 个 Intel RealSense D435 相机（头部 + 双腕）。
- **任务**（6 个，分单臂/双臂同时/双臂顺序）：Apple to Plate、Bowl to Plate、Dual Banana Grasp、Dual Bottle Grasp、Banana Handover to Plate、Apple to Drawer。
- **数据**：每任务 100 条专家轨迹；50 次评估，分 In-Domain 与 Out-of-Domain。
- **基线**：仅对比 **Diffusion Policy (DP)**。
- **评分**：分步打分（抓取、放置、交接、开抽屉等子任务）。

### 3.3 消融实验（RoboTwin）

- 共享映射 vs. 独立码本；
- 两阶段训练 vs. 端到端单阶段训练；
- 潜在 token 数量 N 与码本大小 K 的影响（N=0/4/8，K=256/512）。

---

## 4. 资源与算力

- **GPU**：4 张 **NVIDIA RTX 4090**。
- **批大小**：每 GPU 32，总计 **128**。
- **训练量**：每阶段 **900 epochs**，共两阶段（即 1800 epochs 总训练）。
- **关键超参**：观测视野 O=1、预测视野 H=8、latent token N=4、码本容量 K=256、潜在维度 d=32。
- **缺失信息**：论文**未明确报告**总训练时长（小时/天）；未报告推理延迟与显存占用；未提供 FLOPs 或模型参数量。

---

## 5. 实验数量与充分性

- **仿真**：1 个 benchmark × 7 个任务 × 3 个基线 × 3 seeds × 50 trials = 较充分的统计样本。
- **真实世界**：6 个任务，但**仅 1 个基线**（DP），且未与其他双臂专用方法（如 AnyBimanual、InterAct、RDT-1B）对比。
- **消融**：覆盖共享映射、两阶段训练、token 数量与码本大小四个维度，但每组仅给出代表性配置（如 N=0/4/8），**未做更细的扫参**。
- **客观性**：
  - 仿真部分使用 3 seeds + 标准差，统计较为规范；
  - 真实世界缺少多次重复实验的标准差，结果稳定性评估不足；
  - 真实世界任务选择偏向简单 pick-and-place / handover，对**长时序强耦合**任务（如装配、柔性物体操作）的验证有限。

---

## 6. 主要结论与发现

- **仿真性能**（Table 1）：CUBic 平均成功率 **51.8%**，相比 DP3（39.8%）、DP（38.5%）、GR-MG（8.0%）分别提升 **+12.0%、+13.3%、+43.8%**。
- **关键优势任务**：复杂长时序协调任务（如 Pick Apple Messy 40.0%、Blocks Stack Easy 16.0%）。
- **真实世界**：平均得分 43.1（In-Domain）/ 34.7（Out-of-Domain），相比 DP（19.5/12.7）分别提升 +23.6、+22.0。
- **消融发现**：
  - 共享码本映射 → +9.5%；
  - 两阶段训练 → +7.5%；
  - 二者结合 → +19.2%（强烈协同效应）；
  - 缺少 latent token（N=0）→ 性能崩溃至 0%；
  - 过大的 N=8/K=512 → 性能反而下降（40.2%），说明表征容量需匹配任务复杂度。

---

## 7. 优点

- **问题视角新颖**：将"独立 vs. 协调"的对立转化为**统一感知建模问题**，从结构层面化解矛盾，而非通过手工约束平衡。
- **共享码本设计**：通过联合索引选择实现隐式跨臂耦合，避免显式注意力带来的纠缠问题。
- **两阶段训练**：先感知协同、再控制协同，降低了端到端训练的不稳定性，是工程上非常实用的设计。
- **无需 3D 感知**：仅用 2D 多视图 + 关节状态即可超越 DP3，节省了 3D 表征的预处理开销。
- **定性结果直观**：图 4 显示 CUBic 在物体定位、抓取精度与双臂同步性上明显优于 DP。
- **架构对称且模块化**：两臂对称结构便于扩展到 N 臂场景。

---

## 8. 不足与局限

- **真实世界实验基线单一**：仅与 DP 对比，缺少与 AnyBimanual、InterAct、RDT-1B、H-RDT 等**双臂专用 SOTA** 的对比，难以判断在真实场景中的相对位次。
- **真实世界统计不足**：未见多次重复实验的标准差或显著性检验，泛化性结论的可靠性有限。
- **任务多样性受限**：
  - 仿真 7 个任务集中在 pick / handover / stack 类；
  - 真实任务以短时序、单一物体为主，**未涉及装配、柔性物体、长时序规划**等更具挑战的场景。
- **缺失细节**：
  - 未报告训练时长、模型参数量、推理延迟；
  - 未提供超参敏感性、码本使用率（codebook perplexity）等关键 VQ 诊断信息。
- **对专家演示的依赖**：与所有模仿学习方法一样，**性能上限受限于示范质量与多样性**，未讨论主动学习或数据增强。
- **两阶段训练的工程开销**：需要两阶段独立训练与模块冻结，部署与调优流程较复杂。
- **码本维度选择经验化**：N=4、K=256 是经验最优，缺乏理论解释或自适应机制。
- **偏差风险**：仿真评测基于 RoboTwin 自带 3D 生成 + LLM 生成的演示，可能与真实数据分布存在差距，仿真→真实的迁移表现仍是关键风险点。

（完）
