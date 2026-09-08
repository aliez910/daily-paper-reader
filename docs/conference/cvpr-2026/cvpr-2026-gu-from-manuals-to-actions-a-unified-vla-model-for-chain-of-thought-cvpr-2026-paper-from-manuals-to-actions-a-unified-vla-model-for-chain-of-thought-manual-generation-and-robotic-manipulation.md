---
title: "From Manuals to Actions: A Unified VLA Model for Chain-of-Thought Manual Generation and Robotic Manipulation"
title_zh: 从手册到动作：面向思维链手册生成与机器人操作的统一 VLA 模型
authors: "Gu, Chenyang, Liu, Jiaming, Chen, Hao, Huang, Runzhong, Wuwu, Qingpo, Li, Xiaoqi, Liu, Zhuoyang, Li, Ying, Zhang, Renrui, Jia, Peng, Heng, Pheng-Ann, Zhang, Shanghang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Gu_From_Manuals_to_Actions_A_Unified_VLA_Model_for_Chain-of-Thought_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 统一 VLA 模型，通过思维链实现端到端机器人操作
tldr: 现有视觉-语言-动作模型在长时序规划与精确操作的协调上仍存不足，难以胜任乐高组装、物体重排等任务。本文提出 ManualVLA，一种基于混合 Transformer 架构的统一 VLA 框架，通过思维链推理实现多模态手册生成与动作执行的协同。实验表明该模型能更好地从目标状态推演执行过程，推动了面向端到端机器人控制的通用视觉-动作模型发展。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 1014, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1791, \"height\": 735, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 517, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 412, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1812, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 879, \"height\": 370, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-gu-from-manuals-to-actions-a-unified-vla-model-for-chain-of-thought-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1809, \"height\": 359, \"label\": \"Table\"}]"
motivation: 现有 VLA 模型在长时序任务中难以兼顾高层规划与精确操作。
method: 提出基于混合 Transformer 的统一 VLA 框架 ManualVLA，通过思维链连接手册生成与动作执行。
result: 在乐高组装等长时序任务中提升了从目标到可执行步骤的推理能力。
conclusion: 该工作推动了通用化视觉-动作模型在端到端机器人控制中的发展。
---

## Abstract
Vision-Language-Action (VLA) models have recently emerged, demonstrating strong generalization in robotic scene understanding and manipulation. However, when confronted with long-horizon tasks that require defined goal states, such as LEGO assembly or object rearrangement, existing VLA models still face challenges in coordinating long-horizon planning with precise manipulation.Therefore, we aim to endow a VLA model with the capability to infer the "how" process from the "what" outcomes, transforming goal states into executable procedures. In this paper, we introduce ManualVLA, a unified VLA framework built upon a Mixture-of-Transformers (MoT) architecture, enabling coherent collaboration between multimodal manual generation and action execution. Unlike prior VLA models that directly map sensory inputs to actions, we first equip ManualVLA with a planning expert that generates intermediate manuals consisting of images, visual prompts, and textual instructions. Building upon these multimodal manuals, we design a Manual Chain-of-Thought (ManualCoT) reasoning process that feeds them into the action expert, where each manual step provides explicit control conditions, while its latent representation offers implicit guidance for accurate manipulation. To alleviate the burden of data collection, we develop a high-fidelity digital-twin toolkit based on 3D Gaussian Splatting, which automatically generates manual data for planning expert training. ManualVLA demonstrates strong real-world performance, achieving an average success rate 32% higher than the previous hierarchical SOTA baseline on LEGO assembly and object rearrangement tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "From Manuals to Actions: A Unified VLA Model for Chain-of-Thought Manual Generation and Robotic Manipulation" (ManualVLA). I need to organize the summary according to 8 specific points using Markdown format with hierarchical headings and bullet points, ending with "(完)".

Let me analyze the paper carefully:

1. **Core Problem & Motivation**: The paper addresses the limitation of existing VLA models in handling long-horizon tasks with defined goal states (like LEGO assembly or object rearrangement). These tasks require both high-level planning and precise manipulation, which current VLA models struggle with because they directly map sensory inputs to actions.

2. **Methodology**: 
   - ManualVLA based on Mixture-of-Transformers (MoT) architecture
   - Two experts: planning expert (generates multimodal manuals) and action expert (generates actions)
   - Manual Chain-of-Thought (ManualCoT) reasoning - both explicit and implicit CoT
   - Built on Janus-Pro foundation model
   - Uses DeepSeek-LLM 1.5B as base
   - VQ-based vision tokenizer for manual generation
   - SigLIP-Large for action generation visual features
   - Diffusion-based action modeling
   - 3D Gaussian Splatting digital-twin toolkit for manual data generation
   - Three-stage training strategy

3. **Experiments**:
   - Three long-horizon tasks: 2D LEGO Assembly, 3D LEGO Assembly, Object Rearrangement
   - Franka dual-arm robotic platform
   - Baselines: π0, π0.5, FAST, CoT-VLA, VLM+π0.5 (hierarchical)
   - Evaluation: PSNR, FID, MAE for manual generation; Success Rate for manipulation
   - 20 unseen test goal states
   - 300 unseen test samples for manual generation

4. **Resources & Compute**: The paper doesn't explicitly mention specific GPU models or training duration. I should note this.

5. **Experiment Quantity & Sufficiency**: 
   - Manual generation evaluation on 300 samples
   - Manipulation on 20 unseen goal states per task
   - 3 task types
   - Multiple baselines compared
   - Ablation studies: (a) information in manuals, (b) explicit/implicit CoT, (c) MoT vs MoE architecture, (d) action generation paradigm
   - Generalization tests

7. **Main Findings**:
   - 32% average improvement over hierarchical SOTA baseline
   - ManualCoT with both explicit and implicit reasoning is essential
   - MoT outperforms MoE
   - Diffusion-based action generation is superior

8. **Strengths**:
   - Unified architecture addressing long-horizon tasks
   - Novel ManualCoT concept
   - Digital-twin toolkit for data generation
   - Strong experimental results

9. **Limitations**:
   - Small evaluation set (20 rollouts)
   - Limited task diversity (only 3 tasks)
   - Manual generation may still have minor inaccuracies
   - No mention of computational costs
   - Real-world deployment challenges

Let me write a comprehensive summary in Chinese following the specified format.</think>

# 论文总结：ManualVLA —— 面向长时序任务的统一 VLA 模型

## 1. 核心问题与研究动机

- **核心问题**：现有视觉-语言-动作（VLA）模型在面对**具有明确定义目标状态的长时序任务**（如 LEGO 拼装、物体重排）时表现不佳。这类任务需要同时具备：
  - **精确的操纵能力**：动作必须严格对齐最终的物体配置；
  - **长时序规划能力**：需要在高层推理和细粒度控制之间协调；
  - **泛化能力**：能够处理多种未见的真实世界场景。
- **现有方法的局限**：
  - 现有 VLA 模型直接将感知输入映射为动作，缺乏对中间步骤的推理；
  - 分层方法（如 CheckManual、Vid2Robot 等）依赖人工编写的说明书或人类演示视频，泛化性差且人力成本高；
  - 视觉世界建模方法（如 Dreamitate、RoboDreamer）虽能生成子目标，但难以关联子目标与细粒度控制。
- **研究动机**：赋予 VLA 模型**"从'什么'目标推演'如何'执行"**的能力，即从最终目标状态自动推理出可执行的多模态过程手册，并据此生成精确动作。

---

## 2. 方法论

### 2.1 核心思想
- 提出 **ManualVLA**：一个基于**混合 Transformer（Mixture-of-Transformers, MoT）**架构的统一 VLA 框架，将**多模态手册生成**与**动作执行**协同整合在同一模型中。
- 引入 **Manual Chain-of-Thought (ManualCoT)** 推理过程，包含**显式 CoT**（视觉提示）和**隐式 CoT**（跨任务共享注意力）两部分。

### 2.2 关键技术细节

- **基础模型**：基于 Janus-Pro（解耦视觉编码的统一多模态模型），LLM 使用 DeepSeek-LLM 1.5B。
- **双专家设计（MoT 架构）**：
  - **规划专家（Planning Expert）**：生成子目标手册，包含文本描述、像素级 (U,V) 坐标、子目标图像；
  - **动作专家（Action Expert）**：基于扩散过程生成动作序列。
  - 每个专家在 MoT 层拥有独立的 FFN、注意力投影、LayerNorm，但共享全局注意力权重矩阵，实现跨任务信息交互。
- **视觉模块**：
  - 规划专家使用 VQ-GAN 风格的 VQ 视觉 tokenizer（码本大小 16,384×8，下采样因子 16）；
  - 动作专家使用 SigLIP-Large（384 分辨率）作为连续视觉编码器。
- **动作建模**：基于 Diffusion Policy 框架，加入噪声编码器（2 层 MLP）和噪声解码器，机器人状态通过 2 层 MLP 编码注入。
- **ManualCoT 推理**：
  - **显式 CoT**：将预测的 (U,V) 坐标以掩码叠加到当前图像上，作为动作专家的视觉提示输入；
  - **隐式 CoT**：通过**跨任务共享注意力**机制，让动作专家在潜在空间中关注手册生成特征，实现"操作什么→放在哪里→期望的视觉结果"的链式推理。
- **数字孪生工具包**：基于 **3D Gaussian Splatting** 重建真实场景资产，通过迭代放置算法自动生成大量中间状态、位置、文本标注数据，用于训练规划专家。

### 2.3 算法流程
1. 输入：语言指令 $l$、当前图像 $I_t^{current}$、目标图像 $I^{goal}$；
2. 规划专家生成子目标手册：$(\hat{l}_t, p_t, I_t^{subgoal}) \sim \pi_\theta(\cdot | I^{goal}, I_t^{current}, l)$；
3. 构造提示图像 $I_t^{prompt}$（叠加位置掩码）；
4. 动作专家结合状态 $s_t$、提示图像和手册特征 $F_{subgoal}, F_p, F_{\hat{l}}$，生成动作序列：$a_{t:t+h} \sim \pi_\theta(\cdot | s_t, I_t^{prompt}, F_{subgoal}, F_p, F_{\hat{l}})$；
5. 只有当前子目标完成（生成文本描述变化）时才生成新手册，避免冗余。

### 2.4 三阶段训练策略
- **Stage 1**：在大规模跨本体数据集（DROID、Open X-Embodiment、RoboMind 等共 40 万+ 轨迹）上预训练动作专家 5 个 epoch；
- **Stage 2**：在数字孪生生成的数据（每任务 1 万+ 帧）上预训练规划专家，采用交叉熵损失监督手册生成；
- **Stage 3**：在每个下游任务收集约 100 条人工示教数据，联合微调所有组件，损失为 $L_{final} = L_{manual} + L_{action}$。

---

## 3. 实验设计

### 3.1 任务设置
- **平台**：双臂 Franka 机器人；
- **三个长时序任务**：
  - **2D LEGO 拼装**：在平面板上按目标图像拼接不同颜色的积木；
  - **3D LEGO 拼装**：从 2D 布局扩展到 3D 结构，考验空间推理；
  - **物体重排**：将不同形状/尺寸物体放置到盒子内指定位置，需双手交替控制避免碰撞。

### 3.2 对比方法
- **第一类**（强动作生成基线）：π0、π0.5、FAST，均加载官方预训练权重；
- **第二类**（含子目标推理）：CoT-VLA，加入目标图像作为条件并预测子目标图像；
- **第三类**（分层基线）：VLM + π0.5，VLM 负责生成手册，π0.5 负责执行。

### 3.3 评估指标
- **手册生成**：PSNR（↑）、FID（↓）、MAE（↓）；
- **动作执行**：完整任务成功率及关键中间步骤成功率（每步 2 bricks/2 objects）；
- **泛化测试**：背景、物体形状、光照变化下的性能下降率。

---

## 4. 资源与算力

- **论文中未明确说明**：
  - 未提及具体的 GPU 型号、数量；
  - 未报告训练时长、推理延迟等算力开销；
  - 仅有"约 100 条下游任务示教数据"和"40 万+ 轨迹预训练数据"的描述。
- 这是论文的一个**信息披露缺口**，影响了方法可复现性的评估。

---

## 5. 实验数量与充分性

- **主要实验**：
  - 手册生成评估：300 个未见测试样本；
  - 动作执行评估：每个任务 20 个未见测试目标状态；
  - 泛化实验：背景、形状、光照各 20 次 rollout。
- **消融实验**（4 组）：
  - (a) 手册包含的信息类型（位置/位置+图像/完整多模态）；
  - (b) 显式 CoT 与隐式 CoT 的贡献；
  - (c) MoT 架构 vs 标准 MoE 架构；
  - (d) 动作生成范式（扩散 vs 自回归）。
- **充分性评估**：
  - **优点**：任务设计多样（2D/3D 拼装、重排），基线覆盖三类方法，包含消融与泛化测试；
  - **不足**：
    - 每个任务仅 20 个测试目标，样本量较小，可能存在统计波动；
    - 缺少与其他大规模 VLA 模型（如 RT-2、OpenVLA 等）的直接对比；
    - 缺乏在更复杂真实环境（动态干扰、多任务组合）下的测试；
    - 无用户研究或人类评估主观维度。

---

## 6. 主要结论与发现

- ManualVLA 在三个长时序任务上**全面超越所有基线**，平均成功率比之前分层 SOTA 提升 **32%**；
- 手册生成质量高：PSNR 28-29、FID 24-36、MAE 3-6，文本描述在未见样本上 100% 正确；
- **关键发现**：
  - **MoT 架构**优于标准 MoE（仅复制 FFN）；
  - **扩散式动作生成**优于自回归；
  - **显式 + 隐式 CoT 联合使用**缺一不可；
  - 多模态手册（文本+图像+位置）逐步增加信息能持续提升操纵性能；
  - 即便手册存在轻微误差，MoT + ManualCoT 仍能产生可靠动作，具有鲁棒性；
  - 在背景/形状/光照变化下性能下降有限（-17% ~ -29%），体现良好泛化能力。

---

## 7. 优点与方法亮点

- **架构创新**：首次提出基于 MoT 的统一 VLA 架构，将规划与执行在同一模型内协同，避免了分层方法的信息损失和工程复杂度；
- **ManualCoT 设计**：将子目标手册同时作为**显式条件**（视觉提示图像）和**隐式条件**（共享注意力特征）传递给动作专家，模仿人类"看图说话+心算"的双重推理；
- **数据效率高**：仅需约 100 条下游示教即可达到强性能，主要依赖规划专家的世界知识；
- **数字孪生工具包**：基于 3D Gaussian Splatting 自动生成手册数据，缓解了长时序任务数据收集的瓶颈，可推广到其他任务；
- **稀疏手册生成**：仅在状态变化关键帧生成新手册，避免冗余规划，提升效率；
- **实验完整**：包含主结果、消融、泛化、可视化多维度评估。

---

## 8. 不足与局限

- **算力与可复现性**：未披露 GPU 型号/数量/训练时长等算力信息，给复现带来困难；
- **测试规模较小**：每任务仅 20 个测试目标，可能高估真实场景性能；
- **任务范围有限**：仅测试 LEGO 拼装与简单重排，未涉及工具使用、柔性物体操作、动态环境等更复杂场景；
- **依赖基础模型能力**：性能受限于 Janus-Pro 和 DeepSeek-LLM 的生成能力，对未见物体/极端组合可能失效；
- **泛化边界未充分探究**：未测试极端遮挡、密集堆叠、新物体类别等场景；
- **手工规划逻辑**：稀疏手册生成的判断逻辑（文本变化触发）是手工设计的，可能不适用于所有任务类型；
- **真实世界部署风险**：3D Gaussian Splatting 重建需要精确的多视图采集，限制了工具包在快速新场景下的应用；
- **失败案例分析不充分**：附录 D 中提及但论文主体未详细分析失败模式；
- **社会/伦理维度缺失**：未讨论大规模机器人部署可能带来的安全、劳动力影响等问题。

（完）
