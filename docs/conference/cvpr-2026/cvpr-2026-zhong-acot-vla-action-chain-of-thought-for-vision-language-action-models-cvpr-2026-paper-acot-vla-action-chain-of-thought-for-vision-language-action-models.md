---
title: "ACoT-VLA: Action Chain-of-Thought for Vision-Language-Action Models"
title_zh: ACoT-VLA：面向视觉-语言-动作模型的思维链动作推理
authors: "Zhong, Linqing, Liu, Yi, Wei, Yifei, Xiong, Ziyu, Liu, Si, Ren, Guanghui"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhong_ACoT-VLA_Action_Chain-of-Thought_for_Vision-Language-Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向通用机器人操纵的VLA模型动作思维链推理
tldr: 本文针对现有VLA模型依赖间接中间推理导致动作粒度不足的问题，提出动作思维链ACoT范式。方法直接在动作空间进行显式推理，相比子任务预测或目标图像合成等间接方式能传递更精细的执行信息。该工作提升了通用机器人在多样化复杂操纵任务中的视觉-动作映射精度。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 804, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1797, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 841, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 601, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1627, \"height\": 1023, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1632, \"height\": 788, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1538, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 782, \"height\": 198, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 286, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhong-acot-vla-action-chain-of-thought-for-vision-language-action-models-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 768, \"height\": 220, \"label\": \"Table\"}]"
motivation: VLA模型依赖间接中间推理，难以传递精确执行所需的细粒度信息。
method: 提出直接在动作空间进行显式推理的Action Chain-of-Thought范式。
result: ACoT-VLA在多种通用机器人操纵任务中提升了动作生成的精度与可靠性。
conclusion: 为通用VLA模型的动作空间推理提供了新的高效范式。
---

## Abstract
Vision-Language-Action models have emerged as essential generalist robot policies for diverse manipulation tasks, conventionally relying on directly translating multimodal inputs into actions via Vision-Language Model embeddings. Recent advancements have introduced explicit intermediary reasoning--such as sub-task prediction (language) or goal image synthesis (vision)--to guide action generation. However, these intermediate reasoning are often indirect and inherently limited in their capacity to convey the full, granular information required for precise action execution. Instead, we posit that the most effective form of reasoning is one that deliberates directly in the action space. We introduce Action Chain-of-Thought (ACoT), a paradigm where the reasoning process itself is formulated as a structured sequence of coarse action intents that guide the final policy. In this paper, we propose ACoT-VLA, a novel architecture that materializes the ACoT paradigm. Specifically, we introduce two complementary components: an Explicit Action Reasoner (EAR) and Implicit Action Reasoner (IAR). The former proposes coarse reference trajectories as explicit action-level reasoning steps, while the latter extracts latent action priors from internal representations of multimodal input, co-forming an ACoT that conditions the downstream action head to enable grounded policy learning. Extensive experiments in real-world and simulation environments demonstrate the superiority of our proposed method. Code is available at: https://github.com/AgibotTech/ACoT-VLA.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "ACoT-VLA: Action Chain-of-Thought for Vision-Language-Action Models" organized in 8 specific points. Let me carefully analyze the paper and produce a structured summary.

Let me go through each requirement:

1. Core problem and overall meaning (research motivation and background)
2. Methodology: core ideas, key technical details, formulas or algorithm flow (explained in text)
3. Experimental design: datasets/scenarios used, benchmarks, comparison methods
4. Resources and computing: GPU models, quantities, training duration, etc.
5. Number and sufficiency of experiments
6. Main conclusions and findings
7. Advantages: highlights of the method or experimental design
8. Limitations and shortcomings

Let me write a comprehensive summary based on the paper content.</think>

# ACoT-VLA 论文总结

## 1. 核心问题与研究动机

- **背景**：Vision-Language-Action（VLA）模型已成为通用机器人操作策略的主流范式，通常以预训练 VLM 为骨干，将视觉与语言输入编码后直接映射到动作空间。
- **现有局限**：
  - **语言 CoT 路线**（如 TraceVLA、ThinkAct、π0.5）：让 VLM 生成子任务描述作为中间推理，但子任务本质上是抽象语言描述，与底层运动指令之间存在显著的"语义–运动鸿沟"（semantic-kinematic gap）。
  - **视觉/世界模型 CoT 路线**（如 CoT-VLA、WorldVLA、DreamVLA）：合成未来目标图像来指导动作生成，但视觉信息同样难以精确刻画运动学细节。
  - **根本问题**：上述两类中间推理本质上都是间接的，无法传递精确动作执行所需的细粒度运动学信息。
- **本文观点**：最有效的推理应当直接在"动作空间"中进行，而非在语言或视觉空间。

## 2. 方法论

### 2.1 核心思想
提出 **Action Chain-of-Thought（ACoT）** 范式，将推理过程定义为一系列粗粒度的动作意图（coarse action intents），作为最终动作策略的引导。具体实现为 **ACoT-VLA** 框架，包含两个互补模块：**显式动作推理器（EAR）** 和 **隐式动作推理器（IAR）**。

### 2.2 形式化定义
- 标准 VLA：$\pi_\theta(a_{t:t+H-1} \mid o_t, l)$
- 加入中间引导 $g$：$\pi_\theta(a,g \mid o_t,l) = \pi_\theta(a \mid o_t,l,g) \cdot \pi_\theta(g \mid o_t,l)$，其中 $g \in \{g_{lang}, g_{vis}, g_{action}\}$
- 本文将 $g$ 分解为显式 $g^{ex}_{action}$（参考动作轨迹）和隐式 $g^{im}_{action}$（动作分布先验）。

### 2.3 显式动作推理器（EAR）
- **结构**：轻量级 Transformer（18 层），与 VLM 的 18 层一一对应。
- **输入**：含噪动作序列 $\tilde{a}^{ref}_{t:t+H_{ref}-1}$。
- **机制**：
  - 每层先做自注意力（捕捉动作时间依赖）；
  - 再做交叉注意力，注入对应 VLM 层的 KV 缓存（注入多模态上下文先验）；
  - 通过 FFN + 残差更新表征。
- **训练**：用 flow matching 目标学习动作轨迹分布，输出粗粒度参考动作序列 $a^{ref}_{t:t+H_{ref}-1}$。
- **输出**：经 MLP 投影得到动作嵌入 $Z_{ex}$，作为显式动作空间引导。

### 2.4 隐式动作推理器（IAR）
- **目标**：从 VLM 的 KV 缓存中提取隐含的"动作分布先验"。
- **机制**：
  - 初始化可学习的查询矩阵 $Q_i \in \mathbb{R}^{M \times d}$（$M=1$）；
  - 先将 KV 缓存下采样到低维空间（$d'=128$）；
  - 再用查询对降采样后的 KV 做交叉注意力，池化后经 MLP 得到每层的隐式特征 $z^i_{im}$；
  - 跨层聚合得到 $Z_{im}$，作为隐式动作空间引导。
- **意义**：捕捉语言中的动作语义（如"reach out"、"grasp"）以及视觉中的可交互性（affordance）。

### 2.5 动作引导预测（AGP）
- **输入**：含噪动作序列先编码为查询 $Q_{action}$。
- **机制**：
  - $Q_{action}$ 分别与 $Z_{ex}$、$Z_{im}$ 做交叉注意力，得到 $S_{ex}$、$S_{im}$；
  - 拼接后经自注意力融合模块得到 $\bar{h}$；
  - $\bar{h}$ 输入动作头 $\pi^{head}_\theta$，由去噪过程生成最终动作序列。
- **损失函数**：$\mathcal{L}_{total} = \lambda_1 \mathcal{L}_{\pi^{ref}_\theta} + \lambda_2 \mathcal{L}_{\pi^{head}_\theta}$，$\lambda_1=\lambda_2=0.5$。
- **Teacher Forcing**：训练时 EAR 用真实参考轨迹（而非自身预测），以稳定优化；推理时切换到完全自条件模式。

## 3. 实验设计

### 3.1 数据集与基准
- **LIBERO**：四类能力（空间、物体、目标、长时序），每类 10 个任务 × 50 演示，每任务 50 次评估，共 2000 次 rollout。
- **LIBERO-Plus**：在 LIBERO 基础上引入 7 种分布偏移（相机、机器人、语言、光照、背景、噪声、布局），共 10030 个评估回合。
- **VLABench**（基于 ManiSkill3）：含 5 个公开赛道（分布内、跨类别、常识、语义指令、未见纹理），使用 IS（意图分数）和 PS（进度分数）。
- **真实环境**：AgiBot G1 与 AgileX 两个机器人平台，3 个任务（Wipe Stain、Pour Water、Open-set Pick）。

### 3.2 实现细节
- 骨干：π0.5 架构（SigLIP 视觉编码器 + Gemma 2B LLM，18 层，隐藏维度 2048）。
- EAR：18 层 Transformer；IAR：$M=1$，$d'=128$。
- 参考动作 horizon $H_{ref}=15$，策略 horizon $H=10$，动作步移 2 和 1。
- 帧分辨率 $224\times224$。

### 3.3 对比方法（涵盖三类引导范式）
- **基线/扩散策略**：Diffusion Policy、Octo。
- **视觉 CoT**：CoT-VLA、WorldVLA（256/512）、DreamVLA、UniVLA、F1、GE-Act。
- **语言 CoT**：TraceVLA、OpenVLA、UniAct、SpatialVLA、ThinkAct、π0-FAST、FPC-VLA、SmolVLA、GR00T-N1、π0、GO-1、DD-VLA、MemoryVLA、π0.5、OpenVLA-OFT、VLA-Adapter。

## 4. 资源与算力
- 训练硬件：**单节点 8 卡 NVIDIA H100 GPU**，bfloat16 精度。
- 推理硬件：单张 **NVIDIA RTX 4090**。
- 优化器：AdamW，梯度裁剪 1.0，EMA 衰减 0.999。
- 学习率：cosine decay，warm-up 10K 步，峰值 $5\times10^{-5}$，衰减 $5\times10^{-6}$ 持续 10K 步。
- **未明确说明**：具体训练时长、训练数据量级、模型参数量等细节未在正文中给出。

## 5. 实验数量与充分性

- **主对比实验**：3 个仿真基准（LIBERO、LIBERO-Plus 含零样本迁移与监督微调两种协议、VLABench）。
- **消融实验**：
  - 模块消融：EAR、IAR 单独/联合使用（4 组）。
  - EAR 超参数消融：动作步移（1/2/3）× 动作 horizon（5/10/15/30/60/90），共 7 组配置。
  - IAR KV 缓存交互策略：Query、Attention Pooling、Downsample 三种。
- **真实环境**：3 个任务 × 2 个机器人平台。
- **充分性评价**：实验覆盖了仿真/真实、长/短时序、多类引导范式对比、消融维度较完整；公平性较好——均严格遵循官方训练与评估协议，未引入额外数据。但缺少对失败案例、可解释性的深入分析。

## 6. 主要结论与发现

- **LIBERO**：ACoT-VLA 平均成功率 **98.5%**（最佳），比 π0.5 高 1.6%；其中 Long-horizon 任务提升尤为显著（92.4% → 96.0%）。
- **LIBERO-Plus**：
  - 零样本迁移：平均 **86.6%**，优于所有先前方法；
  - 监督微调：平均 **88.0%**，在机器人初始状态偏移（+3.2%）和语言变体（+4.2%）上鲁棒性突出。
- **VLABench**：平均 IS **63.5%** / PS **47.4%**，均优于 π0.5；未见纹理赛道 IS 提升 12.6%、PS 提升 7.2%。
- **真实环境**：平均成功率 **66.7%**，相比 π0.5（61.0%）和 π0（33.8%）显著领先；跨具身（AgiBot G1 与 AgileX）均验证有效。
- **消融结论**：EAR 与 IAR 各自独立带来提升，组合时产生互补效应；EAR 中"短参考 horizon + 中等步移"配置最佳；IAR 中 KV 缓存下采样策略优于直接查询与注意力池化。

## 7. 优点

- **范式创新**：首次明确提出"动作空间推理"的概念，从根本上解决 VLA 的语义–运动鸿沟问题。
- **架构设计巧妙**：显式 + 隐式双轨推理既保留运动学直接性，又利用 VLM 内部的隐含动作语义。
- **Teacher Forcing 策略**：训练时用真值参考轨迹稳定优化，推理时切换自条件，避免训练-推理不一致。
- **训练稳定**：仅冻结 LLM 骨干亦能取得 SOTA（表中 † 标记的 98.5%）。
- **跨域泛化强**：在仿真、真实环境、跨具身平台上均验证有效。
- **开源**：代码已公开在 AgiBotTech/ACoT-VLA。

## 8. 不足与局限

- **真实世界实验规模有限**：仅 3 个任务、2 个平台，未涵盖更复杂的具身与场景多样性。
- **算力与训练细节不透明**：未报告总训练时长、单 epoch 时间、参数量级及训练数据规模。
- **对失败案例缺乏分析**：未提供失败模式、可解释性或对极端分布偏移的深入诊断。
- **潜在偏差风险**：
  - 教师强制训练策略依赖高质量参考轨迹，可能在演示数据稀缺或噪声场景下退化；
  - EAR 参考轨迹质量直接受 VLM 编码质量影响，对 VLM backbone 选型敏感。
- **应用限制**：
  - 框架依赖 π0.5 作为骨干，是否适用于其他 VLA 架构（如 OpenVLA、π0）尚未充分验证；
  - 双模块设计带来额外计算开销，对实时控制的延迟影响未在论文中讨论；
  - 主要在桌面级机械臂任务上验证，对移动机器人或灵巧手等场景的迁移性未知。

（完）
