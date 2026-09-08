---
title: "DynBridge: Bridging Imagination and Control through Interaction Dynamics for Robot Manipulation"
title_zh: "DynBridge:通过交互动力学桥接想象与控制的机器人操纵"
authors: "Wang, Alex, Dong, Zhiwei, Bai, Qicheng, Zhang, Chenshi, Yi, Yujie, Dai, Guang, Liu, Yong, Wang, Mengmeng"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Wang_DynBridge_Bridging_Imagination_and_Control_through_Interaction_Dynamics_for_Robot_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 端到端统一想象与控制的机器人操纵框架
tldr: "现有生成式机器人操纵方法将视觉想象与动作控制分开建模,导致视觉连贯但物理不一致的行为。本文将动作与环境变化的双向耦合形式化为交互动力学,并提出端到端DynBridge框架,通过共享动力学表征将想象与控制统一。在操纵基准上的实验显示,该方法获得了物理一致的轨迹推演与更优的控制性能,为端到端视觉运动学习提供了新的统一路径。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 753, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1790, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 334, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 881, \"height\": 303, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 285, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 867, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 858, \"height\": 227, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 473, \"height\": 358, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 330, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/fig-011.webp\", \"caption\": \"\", \"page\": 0, \"index\": 11, \"width\": 859, \"height\": 286, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-wang-dynbridge-bridging-imagination-and-control-through-interaction-dynamics-for-robot-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1816, \"height\": 359, \"label\": \"Table\"}]"
motivation: "现有方法将视觉想象与动作控制解耦,导致行为物理不一致。"
method: "形式化交互动力学并提出DynBridge,通过共享动力学表征端到端统一想象与控制。"
result: 在操纵任务中获得物理一致的轨迹预测与更优控制性能。
conclusion: 为机器人操纵提供了因果驱动的端到端视觉运动统一学习框架。
---

## Abstract
Recent generative models allow robots to generate future visual outcomes for action guidance, yet most still address imagination and control independently, resulting in visually coherent rollouts but physically inconsistent behaviors. While structural priors enhance spatial grounding, these methods remain visually correlation-driven rather than causally informed, overlooking the bidirectional coupling between robot actions and the evolving environment. We formalize the coupling as interaction dynamics, which specify where environmental changes occur and how actions cause them. Based on this formulation, we introduce DynBridge, an end-to-end framework that unifies imagination and control through the shared dynamics representation. Specifically, DynBridge realizes this via three components: (1) an Interaction Dynamics Generator that forecasts interaction dynamics via joint trajectory generation and action prediction; (2) an Action-Conditioned Dynamics Aggregator that integrates dynamics under control signals; and (3) a Dynamics-Guided Action Predictor that leverages the aggregated dynamics to produce executable, context-aware actions. Results demonstrate that DynBridge consistently outperforms prior methods on simulated and real-world benchmarks without external pretraining.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "DynBridge: Bridging Imagination and Control through Interaction Dynamics for Robot Manipulation" following a specific structure with 8 points. Let me analyze the paper carefully and produce a comprehensive summary.

Let me go through each section:

1. **Core problem and motivation**: The paper addresses the gap between visual imagination (generative models predicting future frames/trajectories) and action control in robot manipulation. Existing methods either decouple these processes (leading to visually coherent but physically inconsistent behaviors) or focus only on spatial structure (where) without modeling causal dynamics (how). The key insight is the bidirectional coupling between robot actions and environmental changes.

2. **Methodology**: DynBridge framework:
   - **Interaction Dynamics Generator**: Uses learnable dynamic tokens that attend across visual+language modalities. Jointly optimizes trajectory prediction (where) and action prediction (how). Uses CoTracker for frame-wise resampling with short-horizon tracking for supervision.
   - **Action-Conditioned Dynamics Aggregator**: Dual-path design - local path (action-query-driven attention scoring and weighted aggregation) + global path (linear compression). Uses shared action tokens with stop-gradient and adapters.
   - **Dynamics-Guided Action Predictor**: Action-Transformer decoder with masked self-attention, cross-attention, integrating action tokens, aggregated dynamics, visual embeddings, and language embeddings.
   
   Loss: L_total = L_act + β·L_traj

3. **Experimental design**:
   - Datasets/benchmarks: LIBERO (5 subsets: Spatial, Object, Goal, Long, 90), Meta-World (4 handle manipulation tasks)
   - Baselines: BC, R3M-finetune, VPT, UniPi, ATM, GraphMimic, PlaySlot, MPI, ImAct
   - Real-world: Franka Research 3 arm with 5 tasks (pressing button, pulling tissue, picking up cup and pouring water, placing cherries and snack, folding towel)
   - Cross-robot transfer: Franka Panda to XArm7

4. **Resources/compute**: The paper doesn't explicitly mention specific GPU types, counts, or training duration. I should note this.

5. **Experiment quantity and sufficiency**: Multiple ablations (end-to-end optimization, trajectory loss, coordinate vs. latent representation, prediction horizon L, dynamic token capacity N_tok, conditioning strategies), generalization tests (spatial displacement, background changes, cross-robot transfer, error correction), plus trajectory visualization, real-world experiments.

6. **Main conclusions**: 
   - Interaction dynamics representation captures task-invariant features
   - End-to-end joint optimization bridges imagination-control gap
   - Where (trajectory) and how (action imitation) are complementary
   - Implicit latent representations outperform explicit coordinates
   - Moderate prediction horizons are best
   - Action-conditioned aggregation is most effective
   - Cross-embodiment transferability
   - Robust to suboptimal demonstrations
   - Better generalization to unseen positions and backgrounds
   - Error correction during execution

7. **Strengths**: 
   - Novel formulation of interaction dynamics unifying spatial and causal
   - End-to-end joint training
   - Dual-path aggregator with action-conditioned mechanism
   - No external pretraining needed but outperforms methods with it
   - Strong cross-embodiment transferability
   - Robust to suboptimal data

8. **Limitations**:
   - No compute resources disclosed
   - Limited real-world tasks (5 tasks on one robot)
   - Cross-robot experiment uses deliberately imperfect data which is hard to compare
   - Few-shot demonstration settings may not scale to industrial applications
   - Reliance on CoTracker for trajectory supervision adds external dependency
   - Limited to relatively short-horizon tasks in real world
   - No exploration of open-world settings mentioned as future work
   - Some figures/charts in the paper appear duplicated/garbled (this is from OCR issues)

Let me write this in Chinese, well-structured with Markdown.</think>

# DynBridge 论文总结

## 1. 核心问题与研究动机

- **核心矛盾**：现有面向机器人操纵的生成式方法将"视觉想象"(如未来帧预测、轨迹生成)与"动作控制"作为两个相对独立的子问题进行优化,导致模型能够生成视觉上合理但物理上不可执行的策略——即"想象—控制鸿沟"(imagination–control gap)。
- **关键缺陷**：
  - **解耦训练**：视频生成模型与策略网络分阶段训练,优先保证视觉真实感而非物理可行性。
  - **空间先验的局限**：结构化先验(如 ATM 的轨迹、GraphMimic 的图结构)虽然增强了空间定位(where),但仍停留在视觉相关性层面,缺乏对"动作如何引起环境变化"(how)的因果建模。
  - **缺乏双向耦合**：环境演化与智能体动作是双向耦合的,但现有方法未充分利用这一依赖关系。
- **核心动机**：将这种双向耦合显式形式化为 **交互动力学(Interaction Dynamics)**,既编码环境在何处改变,也编码动作如何物理地引起该改变,从而统一"想象"与"控制"。

## 2. 方法论

DynBridge 是一个端到端框架,由三个核心组件构成,共享一个交互动力学隐表示。

### 2.1 交互动力学生成器(Interaction Dynamics Generator)
- **轨迹监督构造**：采用**逐帧重采样+短时跟踪**策略,使用 CoTracker 对每帧均匀采样 $N_q$ 个点进行长度为 $L$ 的短轨迹跟踪,避免训练时锚定首帧导致的 train–test 不一致,并适应目标出现/消失的动态场景。
- **结构**：
  - 视觉编码器:ResNet-18 提取帧特征 $F_{t-h:t}$。
  - 语言编码器:冻结的 6 层 MiniLM 编码指令得到 $G_l$。
  - 可学习动态令牌 $Z_{dyn}\in\mathbb{R}^{N_{tok}\times d}$ 作为查询,通过跨模态交叉注意力构建交互表示:
    $$H_t = \text{CrossAttn}(Q=Z_{dyn},\ K=V=[F_{t-h:t};G_l])$$
- **训练目标**：
  - 空间监督:轻量解码器 $f_{dyn}$ 将 $H_t$ 解码为未来 $L$ 步轨迹预测 $\hat{P}_{t:t+L}$,使用 L2 损失 $L_{traj}=\|\hat{P}_{t:t+L}-P_{t:t+L}\|_2^2$。
  - 动力学监督:通过与动作预测器联合优化,使 $H_t$ 隐式地编码因果动作模式(推理时解码器被丢弃)。

### 2.2 动作条件动力学聚合器(Action-Conditioned Dynamics Aggregator)
为解决动态令牌数量过少(表征瓶颈)或过多(模态失衡)的问题,设计了**双路径聚合**:
- **局部压缩路径**(action-aware aggregation):
  - 引入可学习动作令牌 $A_{act}\in\mathbb{R}^{M\times d}$($M<N_{tok}$),在聚合器内通过 **stop-gradient + bottleneck adapter** 进行稳定复用与适应。
  - 通过 Token Scorer 计算动作令牌与交互令牌的注意力得分矩阵 $S_t=\text{Softmax}(Q_AK_{H_t}^\top/\sqrt{d})$,进而加权聚合: $H_t^{local}=S_t(H_tW_v)$。
- **全局压缩路径**:线性投影得到 $H_t^{global}\in\mathbb{R}^{M\times d}$,与局部路径维度一致。
- **融合**: $H_t^{agg}=H_t^{local}+H_t^{global}$,形成兼顾细节与全局的紧凑动力学先验。

### 2.3 动力学引导动作预测器(Dynamics-Guided Action Predictor)
- 采用 **Action-Transformer 解码器**(含 masked 自注意力 + cross-attention + FFN)。
- 每步输入拼接四类令牌:动作令牌 $A_{act}$、聚合动力学 $H_t^{agg}$、视觉嵌入 $F_{t-h:t}$、语言嵌入 $G_l$。
- 训练采用 MSE 损失(连续控制): $L_{act}=\|\hat{a}_t-a_t^*\|_2^2$。

### 2.4 整体优化
- 总损失: $L_{total}=L_{act}+\beta L_{traj}$,整个框架端到端联合训练。

## 3. 实验设计

### 3.1 仿真基准与对比方法
- **LIBERO 基准**(5 个子集):
  - Libero-Spatial、Libero-Object、Libero-Goal、Libero-Long、Libero-90。
  - 训练数据:仅每任务 10 条带标签演示;对比方法中部分使用额外 50 条无标签视频(标注为 Ext. Data)。
- **Meta-World 基准**:4 个精细操作任务(handle press、handle press side、handle pull、handle pull side),仅用每任务 5 条演示,且评估时把手位置有空间变化。
- **真实世界**:Franka Research 3 机械臂,5 个任务:按按钮、抽纸巾、端杯倒水、把樱桃+小零食依次放入盘中、折叠毛巾(每任务 10 次试验)。
- **跨机器人迁移**:从 Franka Panda 训练后迁移到 XArm7,采用刻意含较多失败/噪声演示的数据集。

### 3.2 对比方法分类
| 类别 | 方法 |
|------|------|
| Vanilla Imitation | BC、R3M-finetune |
| Video Generation | UniPi |
| Where-focused Interaction | ATM、GraphMimic |
| How-focused Interaction | VPT、PlaySlot |
| Where+How 联合 | MPI、ImAct |

## 4. 资源与算力

- **论文未明确披露**所使用 GPU 型号、数量、训练时长等算力信息。
- 仅可推断:训练在 LIBERO 与 Meta-World 等中等规模数据集上进行,使用了 CoTracker 作为外部点轨迹跟踪器(预训练模型依赖),未使用额外的机器人数据预训练。

## 5. 实验数量与充分性

- **主实验**:LIBERO 5 个子集 + Meta-World 4 个任务 + 真实世界 5 个任务,共 14 组场景。
- **消融实验**(约 7 类):
  - Interaction Dynamics Generator 的端到端消融( w/o e2e )、轨迹监督消融( w/o traj )、显式坐标消融( ours-coord )。
  - 预测时域 $L\in\{0,1,5,10,15\}$ 扫描。
  - 动态令牌数量 $N_{tok}\in\{4,8,16,32\}$ 与聚合器消融。
  - 4 种条件聚合策略(动作/语言/视觉/可学习锚)对比。
- **泛化性测试**:
  - LIBERO-Goal 目标位置低/高偏移泛化。
  - 推理阶段背景替换的视觉泛化。
  - 跨机器人(Franka Panda→XArm7)迁移。
  - 末端执行器轨迹可视化对比 ATM。
- **充分性评价**:
  - 消融维度较为系统,覆盖了组件级设计选择与超参扫描。
  - 仿真与真实世界双重验证,增强了结论可信度。
  - **不足**:真实世界任务数量偏少(5 个)、每任务仅 10 次试验,统计显著性可能有限;跨机器人实验中基线对比的样本量与公平性需进一步考量(基线在该刻意不完美数据集上表现都很低)。

## 6. 主要结论与发现

1. **端到端联合优化显著缩小想象—控制鸿沟**:解耦训练( w/o e2e )性能明显下降,验证了联合优化的必要性。
2. **空间监督(where)与动作模仿(how)互补**:移除轨迹分支( w/o traj )会降低控制精度;两者共同塑造因果一致的交互动力学。
3. **隐式表示优于显式坐标**:隐式交互表示能编码多模态可行轨迹,比单条确定性坐标更鲁棒。
4. **适中的预测时域最优**:$L>0$ 显著提升性能;但 $L$ 过大(>10)会因误差累积而降低稳定性。
5. **聚合器缓解令牌容量权衡**:无论 $N_{tok}$ 多寡,聚合器均提升性能,避免了表征瓶颈与模态失衡。
6. **动作条件聚合最有效**:相比语言/视觉/可学习锚条件,以动作令牌为查询的聚合带来最大增益。
7. **任务不变的交互特征**:在 LIBERO-90(90 个不同任务)上仍保持优势,证明学到的是可迁移的交互因果模式而非任务特定特征。
8. **跨机器人可迁移**:Franka Panda 上预训练的交互动力学可迁移到 XArm7。
9. **对次优演示鲁棒**:即使演示中含大量失败/噪声样本,因果结构仍能稳定控制,而 ATM 等易被失败轨迹干扰。
10. **零样本泛化能力强**:在目标位置偏移与背景替换设置下性能稳定,具备纠错能力。

## 7. 优点与亮点

- **概念创新**:首次将"动作—环境"双向耦合显式形式化为交互动力学,跳出了传统"先想象后控制"的范式。
- **架构统一**:三个组件通过共享的交互动力学隐表示端到端耦合,避免了两阶段管线常见的视觉—物理不一致。
- **无需外部预训练**即超越多个使用 50 条无标签视频的方法(如 GraphMimic、ATM),数据效率高。
- **双路径聚合器**与 stop-gradient 共享动作令牌的设计兼顾了稳定性与适应性。
- **跨具身迁移能力**与对**次优数据**的鲁棒性,展示了因果导向表示的实用价值。
- **轨迹逐帧重采样**策略解决了 train–test 不一致问题,提升了跟踪监督质量。

## 8. 不足与局限

- **算力披露缺失**:未报告 GPU 型号/数量、训练时长等关键资源信息,复现门槛不透明。
- **真实世界覆盖有限**:仅 5 个任务、每任务 10 次试验,且局限于单一机器人平台(Franka Research 3),长时域与多平台验证仍不足。
- **跨机器人实验的公平性**:在刻意设计的低质量数据集上,基线性能整体较低(20%–45%),基线间的相对比较可能受数据集偏差影响;且未说明迁移机制(权重共享程度、是否微调)。
- **轨迹监督依赖外部跟踪器**:依赖 CoTracker 提供监督信号,引入了额外的预训练模型依赖,且跟踪误差会向上游传播。
- **短时轨迹假设**:L 的有效范围受限于短视域,论文自身承认长时域预测会放大误差,如何扩展到更长任务仍待解决。
- **模态限制**:仅依赖 RGB + 语言指令,未探索深度/触觉等更直接的物理信号,而论文自身强调物理动力学的重要性。
- **未涉及开放世界与安全/失败恢复**:作者将其列为未来工作,但在当前实验中未提供任何初步验证。
- **图表质量问题**:原文 Figure 7、Figure 8 在 PDF OCR 后存在图表重复显示与部分文字乱码,可能影响读者对部分实验细节(如跨机器人具体任务列表)的理解。

（完）
