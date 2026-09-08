---
title: "HiF-VLA: Hindsight, Insight and Foresight through Motion Representation for Vision-Language-Action Models"
title_zh: HiF-VLA：通过运动表征实现视觉-语言-动作模型的后见、内省与前瞻
authors: "Lin, Minghui, Ding, Pengxiang, Wang, Shu, Zhuang, Zifeng, Liu, Yang, Tong, Xinyang, Song, Wenxuan, Lyu, Shangke, Huang, Siteng, Wang, Donglin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Lin_HiF-VLA_Hindsight_Insight_and_Foresight_through_Motion_Representation_for_Vision-Language-Action_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 引入运动表征作为时序世界模型，为VLA闭环控制提供前后关联信息
tldr: 本文针对现有VLA模型仅依赖当前观测、假设马尔可夫性而难以处理长时序任务的局限性，提出了基于运动表征的世界模型增强方案。HiF-VLA将运动视为比像素更紧凑的时序表征，并据此实现后见、内省与前瞻三层能力，使策略在动作生成过程中能够推理未来演化。实验表明该方法在长时序机器人操作中显著提升了时序一致性与闭环控制质量。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1786, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1770, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1693, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 344, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1773, \"height\": 556, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1823, \"height\": 727, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 887, \"height\": 945, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-lin-hif-vla-hindsight-insight-and-foresight-through-motion-representation-for-vision-language-action-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 334, \"label\": \"Table\"}]"
motivation: 现有VLA因马尔可夫假设仅依赖当前观测，在长时序操作中出现时序短视。
method: 构建以运动为中心的世界模型，为VLA注入后见、内省与前瞻的时序推理能力。
result: 在长时序机器人操作任务中显著提升了时序一致性与闭环控制表现。
conclusion: 运动世界模型有效缓解VLA的时序短视，推动视觉到动作的鲁棒闭环映射。
---

## Abstract
Vision-Language-Action (VLA) models have recently enabled robotic manipulation by grounding visual and linguistic cues into actions. However, most VLAs assume the Markov property, relying only on the current observation and thus suffering from temporal myopia that degrades long-horizon coherence. In this work, we view motion as a more compact and informative representation of temporal context and world dynamics, capturing inter-state changes while filtering static pixel-level noise. From this perspective, HiF-VLA equips a motion-centric world model for the VLA, enabling agents to reason about temporal dynamics for future evolution during action generation. Building on this idea, we propose HiF-VLA (Hindsight, Insight, and Foresight for VLAs), a unified framework that leverages motion for bidirectional temporal reasoning. HiF-VLA encodes past dynamics through hindsight priors, anticipates future motion via foresight reasoning, and integrates both through a hindsight-modulated joint expert to enable a "think-while-acting" paradigm for long-horizon manipulation. As a result, HiF-VLA surpasses strong baselines on LIBERO-Long and CALVIN ABC-D benchmarks, while incurring negligible additional inference latency. Furthermore, HiF-VLA achieves substantial improvements in real-world long-horizon manipulation tasks, demonstrating its broad effectiveness in practical robotic settings.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "HiF-VLA" following a specific structure with 8 points. Let me analyze the paper carefully and organize the content.

The paper is about Vision-Language-Action (VLA) models for robotic manipulation. The key issues:
1. Most VLAs assume Markov property - only use current observation
2. This causes "temporal myopia" in long-horizon tasks
3. Existing solutions stack multiple past frames - expensive, redundant
4. Some use pixel-level future prediction - redundant

Their solution:
- HiF-VLA: Hindsight, Insight, Foresight framework
- Use Motion Vectors (MVs) from video codecs as compact temporal representation
- Three components:
  1. Hindsight prior acquisition - encodes historical frames into motion vectors
  2. Foresight reasoning with insight - VLM interprets task and current obs to predict future motion
  3. Hindsight-modulated joint expert - fuses hindsight, foresight, action representations

Experiments:
- LIBERO-Long (10 tasks)
- CALVIN ABC-D benchmark
- Real-world tasks on AgileX Piper robot
- 8 NVIDIA A100 GPUs, batch size 64
- 150k steps for LIBERO, 80k for CALVIN
- Various baselines: OpenVLA, OpenVLA-OFT, Seer, π0, UniVLA, etc.

Key results:
- LIBERO-Long: 94.4% (third-view), 96.4% (multi-view)
- CALVIN ABC-D: 4.08 (third-view), 4.35 (multi-view)
- Inference latency: negligible additional cost
- Real-world: significantly outperforms baseline

Let me write a comprehensive summary in Chinese.</think>

# HiF-VLA 论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：现有视觉-语言-动作（VLA）模型通常假设马尔可夫性，仅依赖当前时刻观测来预测动作，难以处理长时序任务，存在"时序短视（temporal myopia）"问题，导致长时序任务中动作依赖性下降、轨迹碎片化。
- **现有方案的不足**：
  - **堆叠历史帧**（如 TraceVLA、RoboVLMs、GR-2 等）：存在像素级冗余，且计算开销随历史帧数线性增长甚至出现 OOM，难以实时控制。
  - **像素级未来子目标预测**（如 CoT-VLA、UP-VLA、Seer 等）：存在局部畸变和语义漂移，缺乏连续时序建模能力。
- **论文核心观点**：运动（Motion）是比像素更紧凑、更有效的时序表征，能捕捉状态间变化、过滤静态噪声，是连接历史与未来的天然桥梁。因此提出基于运动的"双向时序推理"框架。

---

## 2. 方法论

### 2.1 整体框架：HiF-VLA（Hindsight、Insight、Foresight）

模型由三个核心模块组成，目标函数定义为：

$$(\tilde{a}_{t:t+n}, \tilde{m}_{t:t+n}) \sim P'_\theta(a_{t:t+n}, m_{t:t+n} \mid o_t, l, m^{his}_{t-h:t})$$

即同时预测未来 n 步的动作和运动向量，条件于当前观测、文本指令和历史运动先验。

### 2.2 模块一：后见先验获取（Hindsight Prior Acquisition）

- **关键技术**：借鉴视频编码标准（H.264 / MPEG-4），将历史帧序列压缩为**运动向量（Motion Vectors, MVs）**。
- **运动向量定义**：对于 16×16 宏块，$MV_{t-1:t}(x,y) = (x_t - x_{t-1}, y_t - y_{t-1})$。
- **数据结构**：形成 GOP（Group of Pictures）单元：$[MV_{t-m:t-m+1}, ..., MV_{t-1:t}, o_t]$，尺寸为 $h \times (H/16) \times (W/16) \times 2$。
- **编码器**：轻量级 ViT + 浅层 3D 卷积，将后见运动编码为 token $M_h \in \mathbb{R}^{K_h \times d}$。
- **优势**：相比原始帧（H×W×3），表征维度大幅降低（$H/16 \times W/16 \times 2$），去除静态冗余。

### 2.3 模块二：内省驱动的前瞻推理（Foresight Reasoning with Insight）

- **核心技术**：在 VLM 输入中引入 $K_f$ 个可学习的**前瞻运动查询 token** $\{q^f_1, ..., q^f_{K_f}\}$ 与 $K_a$ 个空**动作 token** $\{q^a_1, ..., q^a_{K_a}\}$。
- **推理过程**：$(M_f, A_f) = F_\theta(o_t, l)$，VLM 并行预测前瞻运动 token $M_f$ 与动作潜在 token $A_f$。
- **创新点**：相比预测像素级未来帧，预测结构化的运动向量，避免语义漂移与局部畸变。

### 2.4 模块三：后见调制联合专家（Hindsight-Modulated Joint Expert）

- **架构设计**：前瞻运动 token 与动作 token 形成两条并行流，通过**跨流联合注意力（Joint Attention）**交互，但保留各自独立的 FFN 以保证表示解耦。
- **后见条件注入**：历史运动 token $M_h$ 经线性层映射为条件向量 $h_c$，通过**自适应层归一化（AdaLN）**对联合专家模块进行调制：
$$\text{AdaLN}(z; h_c) = \gamma(h_c) \cdot \frac{z - \mu(z)}{\sigma(z)} + \beta(h_c)$$
- **设计哲学**：将后见信息作为顶层约束注入解码器，而非直接塞入 VLM，避免破坏预训练的视觉-语言对齐。
- **训练损失**：
$$L_{all} = L_A + \lambda \cdot L_{MV}, \quad \lambda = 0.01$$
其中 $L_A$ 与 $L_{MV}$ 均为 L1 损失，分别作用于动作与运动预测。

### 2.5 输入表示与并行解码

- 视觉编码使用 DINOv2 + SigLIP 混合嵌入（沿用 OpenVLA-OFT）。
- VLM 采用**非因果注意力掩码**，支持运动与动作的并行预测。
- 推理阶段运动解码可选（根据下游需求）。

---

## 3. 实验设计

### 3.1 数据集 / Benchmark

- **LIBERO-Long**：10 个多子目标长时序操作任务，覆盖不同场景。
- **CALVIN ABC-D**：4 个室内环境（A-D），在 A-C 上训练，D 上测试泛化能力，5 条连续指令的平均完成长度。
- **真实世界**：AgileX Piper 机械臂 + RealSense D435 + USB 腕部摄像头，3 个长时序任务（Place blocks on the plates、Cover block and stack bowls、Press buttons in order），每个任务 100 条示范。

### 3.2 对比方法

- **LIBERO-Long**：OpenVLA、UniVLA、MemoryVLA、OpenVLA-OFT、Seer 等。
- **CALVIN ABC-D**：SuSIE、OpenVLA、CLOVER、VPP、π0、UniVLA、GR-1、Vidman、UP-VLA、RoboVLMs、Seer 等。
- **消融对比**：Baseline、+ Subgoal、+ Foresight、+ History frames、+ Hindsight、+ Hindsight+Foresight。

### 3.3 实验设置

- VLM 主干：Prismatic-7B，OpenVLA 预训练权重初始化（OXE 预训练）。
- 评估设置：第三视角 vs. 第三视角 + 腕部多视角。
- LIBERO 每个任务 500 次试验，CALVIN 报告 5 条连续指令的平均长度。

---

## 4. 资源与算力

- **GPU**：8 块 NVIDIA A100。
- **全局 batch size**：64。
- **训练步数**：LIBERO 150k 步；CALVIN 80k 步。
- **动作 / 前瞻块长度**：n = 8；后见窗口默认 8（消融中测试 4、8、16、32）。
- **微调初始化**：基于 OpenVLA 预训练权重，其余模块随机初始化。
- 推理延迟测试在 NVIDIA A100 上进行，每变体 100 次推理取平均。

---

## 5. 实验数量与充分性

- **主实验**：
  - LIBERO-Long 第三视角 + 多视角共 2 个设置，每个 10 个子任务；
  - CALVIN ABC-D 第三视角 + 多视角共 2 个设置。
- **消融实验**：
  - 后见长度扫描（4 / 8 / 16 / 32）；
  - 后见信息嵌入位置对比（VLM 内注入 vs. 专家模块条件注入）；
  - 多模块消融（Baseline / + Subgoal / + Foresight / + History frames / + Hindsight / + H+F）。
- **效率分析**：峰值 GPU 内存、推理延迟、随历史长度的延迟增长曲线。
- **真实世界实验**：3 个长时序任务，每个 20 次试验，与 OpenVLA-OFT 对比。
- **充分性评价**：覆盖了仿真基准、消融、效率、可扩展性、真实部署多个维度，较为全面。但真实世界任务数量较少（仅 3 个任务），可能存在任务多样性不足的问题。

---

## 6. 主要结论与发现

- **LIBERO-Long**：第三视角设置下达到 94.4%（+3.4% 相对基线），多视角设置下达到 96.4%（SOTA），且第三视角单版本即可媲美其他多视角基线。
- **CALVIN ABC-D**：第三视角平均任务长度 4.08，多视角达到 4.35（SOTA），泛化能力优于 OpenVLA-OFT、Seer、VPP 等。
- **效率**：相比堆叠 4 帧历史（229.5 ms，3.15×），HiF-VLA 推理延迟几乎无额外开销（121.6 ms，1.67× 仅来自后见模块本身；纯前瞻模块仅 1.13×）。
- **后见长度最优**：8 帧时性能最佳（94.4% / 96.4%），过长会引入冗余。
- **嵌入位置**：条件注入专家模块（94.4%）优于直接拼接到 VLM 输入（92.8%），表明不破坏视觉-语言对齐的重要性。
- **真实世界**：相比 OpenVLA-OFT（17.4%-34.2%），HiF-VLA 显著提升至 57.9%-65%，尤其在按钮顺序任务上提升近 4 倍。

---

## 7. 优点与亮点

- **核心创新点**：将视频编码领域的运动向量（MVs）引入 VLA 时序建模，是一个跨领域借鉴的巧妙思路。
- **表征效率高**：运动向量相比原始帧压缩比极高（$H/16 \times W/16 \times 2$ vs. $H \times W \times 3$），保留动态信息、过滤静态冗余。
- **双向时序推理**：统一框架内同时建模后见与前瞻，理论上更契合长时序决策的因果结构。
- **计算开销可控**：前瞻模块仅增加 13% 延迟，几乎不增加显存，可扩展性好。
- **"边思考边行动"范式**：联合专家 + AdaLN 条件注入的设计体现了将世界模型与 VLA 融合的清晰路径。
- **实证充分**：仿真 + 真实世界、效果 + 效率 + 消融三层验证结合较好。

---

## 8. 不足与局限

- **运动表征依赖估计精度**：在高度动态或快速运动的场景中，运动向量估计可能不准确或含噪，影响性能。
- **真实世界任务有限**：仅 3 个长时序任务，每任务 20 次试验，统计意义与任务多样性有限。
- **未在大规模互联网视频上预训练**：作者在 Limitations 中明确指出，留待未来工作探索。
- **后见窗口选择缺乏自适应机制**：固定长度 8 在不同任务 / 不同运动速度下未必最优，缺乏动态调整策略。
- **与扩散策略的对比不足**：基线主要是 OpenVLA 系列与 Seer、UniVLA 等，未充分对比 RDT-1B、CogACT、DexVLA 等扩散式 VLA 在长时序任务上的差异。
- **运动向量作为输入对 VLM 预训练的对齐干扰未充分量化**：虽然通过消融证明条件注入优于 VLM 内注入，但缺乏更细粒度的可视化分析（如注意力分布）。
- **跨平台泛化未验证**：真实世界实验仅在 AgileX Piper 上完成，未展示在 Franka、ALOHA 等其他机器人平台上的可迁移性。

（完）
