---
title: "TRM-VLA: Temporal-Aware Chain-of-Thought Reasoning and Memorization for Vision-Language-Action Models"
title_zh: TRM-VLA：面向视觉-语言-动作模型的时序感知思维链推理与记忆机制
authors: "Li, Xiang, Li, Ya-Li, Wang, Yuan, Wang, Shengjin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Li_TRM-VLA_Temporal-Aware_Chain-of-Thought_Reasoning_and_Memorization_for_Vision-Language-Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用机器人操作的视觉-语言-动作通用模型
tldr: 现有视觉-语言-动作模型直接回归动作而缺乏中间推理步骤，限制了其可解释性与长时程任务表现。为此，本文提出 TRM-VLA，将时序感知的思维链推理与记忆机制引入 VLA 模型，避免每步生成完整推理造成的冗余，同时保证跨步骤的时序一致性。整体框架面向通用机器人操作，提升了模型的可解释性与组合任务的执行效果，为通用 VLA 模型在复杂操纵中的应用提供了有效方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 885, \"height\": 746, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1705, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 881, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 883, \"height\": 545, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 398, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1829, \"height\": 603, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1848, \"height\": 357, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-trm-vla-temporal-aware-chain-of-thought-reasoning-and-memorization-for-vision-language-action-models-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 846, \"height\": 670, \"label\": \"Table\"}]"
motivation: 现有 VLA 模型直接回归动作，缺乏中间推理，难以处理长时程组合任务且缺乏可解释性。
method: 提出时序感知思维链推理与记忆机制，避免每步推理冗余并保证时间一致性。
result: 在通用机器人操作任务上提升了推理可解释性与长时程组合任务的执行性能。
conclusion: 为通用 VLA 模型在复杂操纵任务中引入高效推理与记忆机制提供了新方案。
---

## Abstract
Vision-Language-Action (VLA) models have emerged as a powerful paradigm for general robotic manipulation. However, existing approaches typically omit intermediate reasoning steps and directly regress actions, limiting reasoning interpretability and performance in long-horizon or compositional tasks. Although recent studies introduce Chain-of-Thought (CoT) reasoning into VLA models, their effectiveness remains suboptimal due to two key issues: (1) generating a full reasoning trajectory at every timestep introduces substantial redundancy, thereby hinders real-time deployment and (2) reasoning is performed independently, neglecting temporal consistency, which leads to planning conflicts.We propose TRM-VLA, a temporal-aware reasoning and memorization framework that integrates explicit temporal modeling into the VLA reasoning process. TRM-VLA consists of two core components: (1) Keyframe-Triggered Reasoning (KTR), which identifies task progress and performs hierarchical CoT reasoning only at key decision points to reduce redundant inference; and (2) Granularity-adaptable Context Memory (GCM), which dynamically stores and retrieves historical reasoning trajectories to maintain inter-frame coherence and global context. Built upon a dual-system architecture--combining a multimodal foundation model for slow reasoning (System 2) with a diffusion-based policy for fast execution (System 1)--TRM-VLA learns to plan and act efficiently in a unified manner. Extensive experiments on LIBERO-90, SIMPLER, and four real-world robotic tasks demonstrate that TRM-VLA achieves state-of-the-art performance while improving reasoning efficiency.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "TRM-VLA: Temporal-Aware Chain-of-Thought Reasoning and Memorization for Vision-Language-Action Models" following a specific structure with 8 points. Let me analyze the paper content carefully and produce a comprehensive summary.

Let me organize my analysis:

1. **Core Problem & Motivation**:
   - VLA models directly regress actions, missing intermediate reasoning
   - Existing CoT-augmented VLAs have two key issues:
     - Generating full CoT at every timestep causes redundancy
     - Frame-wise independent reasoning lacks temporal consistency, leading to planning conflicts
   - This is non-Markovian dependency that frame-wise reasoning can't resolve

2. **Methodology**:
   - TRM-VLA framework with two core components:
     - KTR (Keyframe-Triggered Reasoning): Hierarchical CoT only at key decision points
     - GCM (Granularity-adaptable Context Memory): Dynamic memory buffer of past reasoning
   - Dual-system architecture (System 2: VLM for reasoning, System 1: Diffusion Transformer for action)
   - Backbone: Prismatic VLM + DINOv2 + SigLIP + LLaMA-2 + CogACT + DiT
   - Mathematical formulations:
     - Standard VLA: at ~ Pθ(at|ot, lt)
     - Reasoning-augmented: at ~ Pθ(at|rt, ot, lt), rt ~ Pθ(rt|ot, lt)
     - TRM-VLA: at ~ Pθ(at|mt, ot, lt), mt ~ Pφ(mt|rh_1,...,rh_t)
   - Embodied Reasoning Annotation with tags: task, plan, perception, subtask reasoning, subtask, move reasoning, move, gripper position
   - Keyframe-Based Annotation with binary flags for three granularities (perception, subtask, move)
   - Stage-Wise Temporal Structuring (early/middle/late stages)
   - Training: Next-token prediction with causal attention
   - GCM uses cross-attention with thinking query to retrieve from memory buffer
   - FiLM fusion of current cognition feature and retrieved memory feature
   - Diffusion policy training with MSE loss

3. **Experimental Design**:
   - Datasets/Benchmarks:
     - SIMPLER (SimplerEnv-Bridge) - WidowX robot
     - LIBERO-90 - Franka robot, 90 tasks across 10 domains
     - Real-world: AIRBOT Player robot with 4 tasks (Scoop Washers, Clean Table, Push Buttons in Order, Place Toy Bear into Box)
   - Training data: BridgeData V2, ECoT annotations, ECoT-Lite, Open X-Embodiment
   - Compared methods: RT-1-X, OpenVLA, SpatialVLA, Magma, π0-Fast, Octo-Base, TraceVLA, RoboVLM, CogACT-Base, π0, UniACT, CogACT-ECoT, ECoT

4. **Resources & Compute**:
   - The paper does NOT mention specific GPU types, counts, or training duration

5. **Experiment Quantity & Sufficiency**:
   - Multiple benchmarks (3 simulated + 4 real-world tasks)
   - Ablation studies on KTR and GCM (with sub-components like STS, KBA, DRC, TRI)
   - OOD evaluation with various perturbations
   - Comparison with extensive SOTA methods

6. **Main Conclusions**:
   - 72.9% average SR on SIMPLER (+21.6% over CogACT-Base)
   - 94.8% SR on LIBERO-90 (+6.4% over CogACT-Base)
   - Real-world: 67% on Push Buttons, 72% on Clean Table
   - Only 4.3 CoT tokens per step vs 26.8 for ECoT (4× reduction)
   - Better robustness under distribution shifts

7. **Strengths**:
   - Keyframe-triggered reasoning reduces computation
   - Hierarchical CoT with multi-granularity
   - Dynamic memory buffer for temporal coherence
   - Strong results on both simulated and real-world
   - Good efficiency-performance trade-off

8. **Limitations**:
   - Limited to AIRBOT Player robot for real-world
   - Only 4 real-world tasks
   - Reliance on annotation quality
   - No mention of compute resources
   - Real-world experiments only 20 trials per task (small sample)
   - Limited diversity of objects/scenes

Let me write the summary in Chinese, with proper Markdown formatting.</think>

# TRM-VLA 论文总结

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（VLA）模型已成为通用机器人操作的主流范式，通过在机器人交互数据上微调预训练视觉-语言模型（VLM），将开放世界推理能力迁移到实体控制中。
- **现有不足**：
  - 多数 VLA 模型直接由观测回归动作，**省略中间推理步骤**，导致可解释性差，难以处理长时程、组合任务；
  - 近期引入 CoT（思维链）推理的工作存在两大核心问题：
    1. **冗余推理**：在每个时间步都生成完整的 CoT 轨迹，相邻帧视觉/语言上下文几乎相同时仍重复生成，导致大量冗余 CoT token，阻碍实时部署；
    2. **帧间独立推理**：CoT 在每个时间步独立生成，缺乏时序依赖和历史记忆，造成行动计划冲突（如连续按钮按下任务中重复操作），违背非马尔可夫决策特性。
- **本文目标**：在 VLA 模型中引入显式的时序建模，使推理与记忆机制协同，提升长时程任务性能和推理效率。

## 2. 方法论

### 2.1 整体架构

- 基于 **CogACT** 的双系统设计：
  - **System 2（慢思考）**：Prismatic VLM 负责 CoT 推理；
  - **System 1（快执行）**：Diffusion Transformer（DiT）负责动作生成；
- 视觉编码器采用 **DINOv2**（空间特征）+ **SigLIP**（语义特征）；语言编码器采用 **LLaMA-2**。
- 预训练于 **Open X-Embodiment** 数据集，再在任务特定数据上微调。

### 2.2 形式化定义

- 标准 VLA：$a_t \sim P_\theta(a_t|o_t, l_t)$
- 推理增强 VLA：$a_t \sim P_\theta(a_t|r_t, o_t, l_t),\ r_t \sim P_\theta(r_t|o_t, l_t)$
- **TRM-VLA**：$a_t \sim P_\theta(a_t|m_t, o_t, l_t)$，其中 $m_t \sim P_\phi(m_t|r_1^h, ..., r_t^h)$，$r_t^h$ 为关键帧触发的层级推理。

### 2.3 核心模块一：关键帧触发推理（KTR）

- **嵌入式推理标注**：沿用 ECoT 协议，将 CoT 分解为 8 个语义标签：`task, plan, perception, subtask reasoning, subtask, move reasoning, move, gripper position`；
- **关键帧标注**：定义三个粒度的二元指示器 $b_t^\tau$（$\tau \in \{perception, subtask, move\}$），仅在标签发生变化时激活对应关键帧；
- **阶段化时序结构**：将任务分为
  - 早期（高层规划：task、plan、perception、subtask/move reasoning）
  - 中期（仅在 perception 关键帧激活）
  - 后期（低层执行：subtask/move/gripper，由 subtask 或 move 关键帧触发）
- **训练目标**：使用因果注意力的 next-token 预测，$L_{KTR} = -\sum_{S \in D}\sum_t \log p(T_t|o_t, l_t;\theta)$。

### 2.4 核心模块二：粒度自适应上下文记忆（GCM）

- **动态推理上下文**：维护一个字典式记忆缓冲 $C_{k_c}$，按层级存储关键帧推理 token；高层（task、plan）寿命长，低层（subtask、move、gripper）寿命短，按粒度更新；
- **时序推理整合**：通过可学习的 **thinking query** 与记忆条目做 Cross-Attention 检索：$f^{att} = \text{CrossAttn}(q, K=f_r^c, V=f_r^c)$；
- **FiLM 融合**：$f_t = \text{FiLM}(f_c, f^{att})$，将当前认知特征与历史记忆融合，作为扩散动作策略的条件信号；
- **动作扩散损失**：$L_{MSE} = \mathbb{E}_{\epsilon \sim \mathcal{N}(0,1),i}\|\hat{\epsilon}_i - \epsilon\|^2$。

## 3. 实验设计

### 3.1 数据集与基准

- **SIMPLER（SimplerEnv-Bridge）**：高保真仿真环境，real-to-sim 评估协议；
- **LIBERO-90**：长时程基准，10 个家庭场景的 90 个任务；
- **真实世界**：AIRBOT Player 机器人，410 条专家演示，覆盖 4 个任务：
  - Place Toy Bear into Box（精确抓取）
  - Push Buttons in Order（时序记忆）
  - Clean Table（长时程规划）
  - Scoop Washers using Shovel（工具使用）
- **训练数据标注**：BridgeData V2 + ECoT 标注、ECoT-Lite、Qwen3-VL 自动标注真实世界数据。

### 3.2 对比方法

- 仿真：RT-1-X、OpenVLA、SpatialVLA、Magma、π0-Fast、Octo-Base、TraceVLA、RoboVLM、CogACT-Base、π0、UniACT、CogACT-ECoT；
- 真实世界：OpenVLA、CogACT-Base、ECoT、CogACT-ECoT。

## 4. 资源与算力

- **论文中未明确提及**所使用 GPU 型号、数量或训练时长；
- 仅提到训练数据来源（Open X-Embodiment、BridgeData V2、LIBERO）和真实世界 410 条专家演示。

## 5. 实验数量与充分性

- **仿真实验**：SIMPLER 上 4 个子任务 × 11 个对比方法 + LIBERO-90 上 7 个对比方法；
- **真实世界**：4 个任务，每任务 20 次试验；
- **消融实验**：SIMPLER 与真实世界各一组，分析 KTR（含 STS、KBA 子模块）与 GCM（含 DRC、TRI 子模块）的贡献；
- **泛化实验**：在光照、背景、干扰物、空间布局、相机位姿等 5 种分布偏移下评估鲁棒性；
- **效率评估**：以 CoT token/步数为代理，对比推理效率；
- **充分性评价**：覆盖仿真+真实、消融+泛化、效率+性能，较为全面；但真实世界每任务仅 20 次试验，统计置信度有限；缺乏对失败模式的细粒度分析。

## 6. 主要结论与发现

- **SIMPLER**：平均成功率 72.9%，较 CogACT-Base（51.3%）提升 **+21.6%**，全面超越现有 SOTA；
- **LIBERO-90**：成功率 **94.8%**，较 CogACT-Base（88.4%）提升 **+6.4%**，超过 CogACT-ECoT（92.1%）、π0-Fast（83.1%）等；
- **真实世界**：平均成功率 69.0%，Push Buttons in Order 67%（vs CogACT-ECoT 45%）、Clean Table 72%（vs 41%）；
- **推理效率**：平均仅 **4.3 CoT tokens/步**，相比 ECoT（26.8）减少约 **4 倍**；
- **泛化性**：在多种分布偏移下均优于 CogACT，drop 更小；
- **消融结论**：KTR 和 GCM 均不可或缺；Stage-wise Structuring 与 Keyframe Annotation 各贡献约 +5~6% SR；Dynamic Context 与 Temporal Integration 各贡献 +4~5% SR。

## 7. 优点与亮点

- **关键帧触发机制**：打破"每帧必推理"的隐式假设，将推理算力与任务动态对齐；
- **层级 CoT 设计**：从 task→plan→perception→subtask→move→gripper 形成"粗到细"的推理链，符合人类认知；
- **动态记忆缓冲**：通过跨粒度寿命管理解决非马尔可夫依赖问题；
- **效率-性能权衡优秀**：token 数量大幅下降的同时性能反而提升；
- **架构灵活**：KTR 与 GCM 可独立拆解，便于在其他 VLA 框架中集成；
- **跨平台验证**：在 WidowX、Franka、AIRBOT 三类机器人上验证，跨具身泛化性强；
- **消融设计细致**：对 KTR 的 STS/KBA 与 GCM 的 DRC/TRI 子组件分别评估。

## 8. 不足与局限

- **算力信息缺失**：未报告 GPU 类型、数量、训练时长等关键资源信息，复现难度较高；
- **真实世界规模有限**：仅 4 个任务、每任务 20 次试验，统计显著性较弱；
- **机器人平台单一**：真实世界仅在 AIRBOT Player 上验证，未涉及更复杂的多指手或双臂系统；
- **依赖标注质量**：方法效果依赖于 CoT 标注质量（ECoT/Qwen3-VL 自动生成），标注偏差可能传递；
- **泛化边界未明**：在训练数据分布外的极端场景（如新物体类别、未见过的工具）表现未充分讨论；
- **缺少失败案例分析**：未对错误决策进行系统性归因，难以判断模型局限性；
- **实时性未量化**：尽管 token 减少明显，但未报告端到端推理延迟（ms/步）；
- **跨具身迁移未测**：未明确验证方法在 Open X-Embodiment 跨具身数据上的迁移能力。

（完）
