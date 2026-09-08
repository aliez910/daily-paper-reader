---
title: Language-Grounded Decoupled Action Representation for Robotic Manipulation
title_zh: 面向机器人操作的基于语言的解耦动作表示方法
authors: "Weng, Wuding, Wu, Tongshu, Chen, Liucheng, Xie, Siyu, Wang, Zheng, Xu, Xing, Song, Jingkuan, Shen, Heng Tao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Weng_Language-Grounded_Decoupled_Action_Representation_for_Robotic_Manipulation_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 以语言为语义桥梁连接视觉语言理解与底层动作控制
tldr: 高层视觉语言理解与底层动作控制之间的异质性是机器人操作中的核心挑战，限制了模型在新任务上的泛化能力。为此，本文提出 LaDA 框架，以自然语言作为语义桥梁，并引入平移、旋转、夹爪控制三个可解释动作原语作为中间层。该方法结合语义引导的软标签机制，为底层动作提供显式语义结构，提升了模型在语义相关新任务上的鲁棒性与泛化能力，为通用机器人操作提供了新的解耦表示方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1815, \"height\": 638, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 837, \"height\": 363, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 820, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 374, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 347, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 880, \"height\": 967, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1629, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-weng-language-grounded-decoupled-action-representation-for-robotic-manipulation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 850, \"height\": 240, \"label\": \"Table\"}]"
motivation: 高层视觉语言理解与底层动作控制之间的异质性限制了操作的鲁棒性与泛化能力。
method: 以语言为语义桥梁，引入平移、旋转、夹爪三个可解释动作原语并结合软标签机制。
result: 提升了模型在语义相关新任务上的动作预测精度与鲁棒性。
conclusion: 为机器人操作中的高层语义与底层控制解耦提供了有效的语言桥接表示。
---

## Abstract
The heterogeneity between high-level vision-language understanding and low-level action control remains a fundamental challenge in robotic manipulation. Although recent methods have advanced task-specific action alignment, they often struggle to generate robust and accurate actions for novel or semantically related tasks. To address this, we propose the Language-Grounded Decoupled Action Representation (LaDA) framework, which leverages natural language as a semantic bridge to connect perception and control. LaDA introduces a fine-grained intermediate layer of three interpretable action primitives--translation, rotation, and gripper control--providing explicit semantic structure for low-level actions. It further employs a semantic-guided soft-label contrastive learning objective to align similar action primitives across tasks, enhancing generalization and motion consistency. An adaptive weighting strategy, inspired by curriculum learning, dynamically balances contrastive and imitation objectives for stable and effective training. Extensive experiments on simulated benchmarks (LIBERO and MimicGen) and real-world demonstrations validate that LaDA achieves strong performance and generalizes effectively to unseen or related tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Language-Grounded Decoupled Action Representation for Robotic Manipulation" (LaDA). I need to organize the summary according to 8 specific points, using Markdown formatting with hierarchical headings and bullet points. Let me carefully extract information from the paper for each section.

Let me go through each requirement:

1. Core problem and motivation
2. Methodology details
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I need to be detailed, objective, and structured. Let me write this out.</think>

# LaDA：面向机器人操作的基于语言的解耦动作表示 —— 论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：机器人操作中存在"高层视觉-语言语义理解"与"底层连续动作控制"之间的**异质性鸿沟**。当前视觉-语言-动作（VLA）模型在任务特定动作对齐上有所进展，但在面对**新任务或语义相关任务**时，难以生成鲁棒且精确的动作。
- **现象观察**：例如"倒水"和"放置瓶子"在语义上不同，但共享"接近、抓取、旋转"等底层运动原语（motion primitives）。现有模型未能利用这种共享结构，导致**冗余学习**和**跨任务泛化能力差**。
- **现有范式的不足**（论文归纳为三类）：
  - **(a) 端到端 VLA 模型**（如 RT-2、OpenVLA、Octo）：将感知与控制耦合在统一 Transformer 中，缺乏可解释性和运动结构重用能力。
  - **(b) 潜在动作学习**（如 LAPO、LAPA、UniSkill）：通过观测差学习潜在动作，但缺乏显式语义，难以跨任务迁移。
  - **(c) 语言条件策略**（如 CLIP-RT、Phoenix、RT-H）：引入语言作为中间表示，但原语过于粗粒度、离散化，缺乏平移量、旋转角等**细粒度运动参数**。
- **关键研究问题**：如何构建一种**既语义可解释、又跨任务可迁移**的动作表示？

## 2. 方法论：核心思想与关键技术细节

### 2.1 整体框架（LaDA）

LaDA（Language-Grounded Decoupled Action Representation）以**自然语言作为语义桥梁**，在高层视觉-语言理解与底层连续控制之间引入一个**细粒度、可解释的中间层**。

整体流程：
1. **动作分解**：将 7-DoF 末端执行器连续动作分解为三个语言锚定的原语。
2. **多模态编码**：使用 CLIP 视觉/文本编码器，并通过 FiLM + MLP 适配器融合得到统一潜在嵌入。
3. **软标签对比学习**：在嵌入空间中按原语级语义亲和度对齐动作与动作、动作与原语描述。
4. **自适应损失加权**：动态平衡模仿损失与对比损失。
5. **微调与推理**：用轻量 MLP 动作头配合 L1 回归损失微调，推理时直接输出连续动作。

### 2.2 语言锚定的动作分解（Language-Grounded Action Decomposition）

- 通过投影 $\Pi: a_t \in \mathbb{R}^7 \rightarrow p_t$ 将连续动作分解为三类正交原语：
  - **平移原语 $\Delta T$**：模板为 "Move [dist] meters along [dir]"。
  - **旋转原语 $\Delta R$**：模板为 "Rotate [mag] degrees around [axis]"。
  - **夹爪原语 $G$**：离散为 "Open" / "Close"。
- 每一个原语都被**离散化为符号化、语言对齐的 bin**，从而把连续控制轨迹映射为可解释的语义类别。

### 2.3 语义引导的软标签对比学习（Semantic-Guided Soft-Label Contrastive Learning）

#### (1) 软标签相似度矩阵构造
对 $N$ 个动作构建软标签相似度矩阵 $S \in [0,1]^{N \times N}$：
$$
S = \frac{w_t M_t + w_r M_r + w_g M_g}{w_t + w_r + w_g}
$$
其中 $M_t, M_r, M_g$ 分别为平移、旋转、夹爪维度上的二值匹配矩阵，$w_t, w_r, w_g$ 是控制各类原语贡献的超参数。$S_{ij}$ 量化动作 $i$ 与动作 $j$ 在原语级别的**连续语义相似度**。

#### (2) 双路径软标签对比损失
使用 CLIP 预训练编码器获得视觉 token $v_i = f_v(V_i)$ 与指令 token $l_i = f_l(L_i)$，并通过 FiLM 融合：
$$
A_i = \text{MLP}(\text{FiLM}(v_i, l_i))
$$
两种对齐路径：
- **动作-动作对齐** $L_a$：在嵌入空间中按 $S_{ij}$ 加权拉近语义相似的动作。
- **动作-原语对齐** $L_m$：将动作嵌入锚定到原语的文本描述 token $P_j = f_l(D(p_j))$。

两者均采用**软标签 InfoNCE**：
$$
L_a = -\sum_{i=1}^{N}\sum_{j=1}^{N} S_{ij} \log \frac{\exp(\text{sim}(A_i,A_j)/\tau)}{\sum_{k=1}^{N}\exp(\text{sim}(A_i,A_k)/\tau)}
$$
$$
L_m = -\sum_{i=1}^{N}\sum_{j=1}^{N} S_{ij} \log \frac{\exp(\text{sim}(A_i,P_j)/\tau)}{\sum_{k=1}^{N}\exp(\text{sim}(A_i,P_k)/\tau)}
$$
总对比损失：$L_{CL} = L_a + \lambda L_m$，其中 $\lambda$ 控制两类对齐的权重。

#### (3) 自适应损失加权（Adaptive Weighting）
模仿损失 $L_{IL}$ 与对比损失 $L_{CL}$ 语义粒度不同、收敛行为不同。采用**移动平均（MA）** 自适应加权：
$$
w_{IL} = \frac{\text{MA}(L_{IL})}{\text{MA}(L_{IL}) + \text{MA}(L_{CL})},\quad w_{CL} = \frac{\text{MA}(L_{CL})}{\text{MA}(L_{IL}) + \text{MA}(L_{CL})}
$$
$$
L_{total} = w_{CL} L_{CL} + w_{IL} L_{IL}
$$
这一策略受**课程学习（curriculum learning）** 启发，动态平衡两类目标，避免任一方主导优化。

### 2.4 微调与推理

- 在软标签对比预训练后，使用**轻量 MLP 动作头** + **L1 轨迹回归损失**进行微调；
- 推理时无需显式原语标签，直接根据 $(V_t, L_t)$ 输出连续 7-DoF 动作，端到端执行。

## 3. 实验设计

### 3.1 预训练数据集

- **Open X-Embodiment (OXE)**：超过 100 万条真实轨迹、22 种机器人本体。
- 使用约 **2250 万视觉帧** 的精选子集，每个动作表示为 7-DoF 控制向量（3D 平移 + 3D 旋转 + 二值夹爪）。
- 自动生成与控制向量对齐的结构化语言描述（例如"沿 z 轴正方向移动 0.5 米并闭合夹爪"），作为软标签对比预训练的辅助监督。

### 3.2 仿真基准与对比方法

- **LIBERO 基准**：包含 Spatial、Object、Goal、Long 四个任务套件，每套 10 个任务，每个任务 50 条人类遥操作演示。报告 50 次随机试验的平均成功率。
- **MimicGen 基准**：9 个接触丰富的操作任务（如 StackThree、Threading、ThreePieceAssembly 等），每个任务约 1000 条演示。
- 对比方法覆盖三大类：
  - 端到端 VLA：OpenVLA、Octo、π-FAST、GR00T-N1.5、MolmoAct、FlowVLA、CoT-VLA、SpatialVLA、WorldVLA、Dita、ThinkAct 等。
  - 潜在动作 VLA：LAPA、UniACT。
  - 语言原语策略：CLIP-RT（含论文复现版本 CLIP-RT*）、Phoenix、Task/Subgoal/Motion-conditioned 等。
  - 传统策略：Diffusion Policy、MDT。

### 3.3 真实世界实验

- **平台**：7-DoF Franka Emika Panda 机械臂 + 静态第三人称 RealSense D435i 相机。
- **任务**：抓取方块并放入盒子（pick-and-place）。
- **训练数据**：100 条人类演示 + OXE 预训练。
- 在光照、物体位姿、颜色、盒子放置等变化下评估鲁棒性。

## 4. 资源与算力

- **论文未明确披露**所使用 GPU 型号、数量、训练时长等算力细节，也未给出预训练或微调的具体训练成本。
- 仅可推断：模型参数规模约 **0.6B**（CLIP-RT* 同规模）；CLIP-RT 原版为 1.3B，论文表述 LaDA 以**约为 CLIP-RT 一半的参数**取得更好结果。
- 附录（论文中提到"see the appendix"）可能包含更多实现细节，但本次提供的文本中未给出。

## 5. 实验数量与充分性

### 5.1 实验规模

- **仿真基准实验**：在 LIBERO 4 套件、MimicGen 9 任务上系统对比，约 **15 个基线方法**。
- **泛化评估**：在 LIBERO-Goal 上进行两类设置——**跨任务泛化**（全新任务指令）与**相似任务泛化**（保留运动语义但改变目标）。
- **多任务迁移**：在 MimicGen 的 Stack/StackThree/Threading 上比较单任务与多任务训练。
- **嵌入可视化**：通过 t-SNE 展示 LaDA 学习到的动作嵌入结构。
- **消融实验**：在 LIBERO 上对比去掉 SCL（软标签对比学习）与去掉 AW（自适应加权）的影响。
- **真实世界实验**：1 个任务（pick-and-place），使用 100 条演示。

### 5.2 充分性与公平性评价

- **优点**：对比基线覆盖广泛、规模差异大（从 93M 到 8.5B 参数）；包含定性与定量（成功率 + t-SNE 可视化）。
- **改进空间**：
  - 真实世界实验仅 1 个任务，**任务多样性有限**；
  - 消融仅围绕 SCL 与 AW 两项，对 $\lambda$、$w_t/w_r/w_g$、温度 $\tau$ 等**超参数敏感性**未做充分分析；
  - 跨任务泛化仅在 LIBERO-Goal 上测试，未覆盖其他套件；
  - 与最强基（如 FlowVLA 8.5B、GR00T-N1.5 3B）比较时未控制训练数据规模的一致性。

## 6. 主要结论与发现

- **LIBERO 性能**：LaDA 平均成功率 **93.6%**，超越所有基线；在 LIBERO-Long（长时序任务）上达到 **86.4%**，显著优于次优的 MolmoAct（77.2%）。
- **MimicGen 性能**：平均成功率 **67%**，相比 Phoenix（58%）提升约 **9%**，相比 CLIP-RT*（51%）提升约 **16%**；在多步、接触丰富任务上增益尤为明显。
- **跨任务与相似任务泛化**：LaDA 在"push"等全新指令上获得 **12.3%** 成功率（CLIP-RT* 为 0%），在相似任务上也持续优于基线。
- **多任务训练增益**：MimicGen 多任务训练下 LaDA 收益显著大于 CLIP-RT，验证语义结构促进运动模式共享。
- **t-SNE 可视化**：LaDA 学习到的嵌入形成更紧凑、语义结构更清晰的聚类；不同任务的平移与旋转原语呈现重叠区域，说明其捕获了**可重用的跨任务运动语义**。
- **真实世界**：在光照、姿态、颜色、盒子位置变化下，LaDA 仍能稳定抓取与放置。

## 7. 优点与亮点

- **方法学创新**：
  - 首次将 7-DoF 连续动作**显式分解为三个语言锚定、可解释原语**，为低层控制提供显式语义监督。
  - 提出**软标签对比学习**机制（区别于传统 hard positive/negative），通过连续语义亲和度实现部分相关动作的细粒度对齐。
  - 引入**移动平均自适应损失加权**，借鉴课程学习思想稳定训练。
- **参数效率高**：仅 0.6B 参数即可达到甚至超过 1.3B（CLIP-RT）、8.5B（FlowVLA）等更大模型。
- **可解释性强**：每个动作都附带自然语言描述与对应原语，便于人机交互、调试与错误诊断。
- **跨任务泛化能力显著**：在完全未见任务上取得 12.3% 成功率（基线为 0%），证明语义桥梁对分布外迁移的有效性。
- **理论动机清晰**：明确指出"语义接地层缺失"是异质性根源，并系统对比了现有三类范式的不足。

## 8. 不足与局限

- **真实世界实验单一**：仅在 pick-and-place 一种任务上验证，缺乏长时序、接触丰富、双臂等更复杂场景的评估。
- **演示数据规模较小**：真实任务仅使用 100 条演示，对真实世界泛化性的论证仍显单薄。
- **超参数与组件分析不足**：除 SCL 与 AW 之外的组件（如 $\lambda$、原语离散 bin 数量、各原语权重 $w_t/w_r/w_g$）缺乏敏感性分析；也未与硬标签对比学习、InfoNCE 温度变化等做细致对照。
- **数据规模与公平性问题**：与 FlowVLA、GR00T-N1.5 等大规模模型比较时未明确控制预训练数据规模，存在**规模偏差风险**。
- **离散化误差**：将连续平移/旋转离散为有限 bin 不可避免地引入量化误差，可能影响高精度任务（如 Threading）的极限性能（LaDA 在 Threading_D0 上仅 48%，仍有较大提升空间）。
- **语言模板固定**：原语描述模板是手工设计的，难以覆盖全部可能的动作语义（如组合动作、非刚体操作），存在**模板覆盖偏差**。
- **可解释性 vs. 灵活性**：语言锚定在带来可解释性的同时，也可能限制模型表达超出模板范围的复杂动作。
- **算力与训练细节披露不完整**：训练资源、时长、batch size 等关键信息缺失，影响复现性评估。
- **跨本体迁移未充分验证**：虽然使用 OXE 预训练，但未见对未见本体的零样本迁移评估。

（完）
