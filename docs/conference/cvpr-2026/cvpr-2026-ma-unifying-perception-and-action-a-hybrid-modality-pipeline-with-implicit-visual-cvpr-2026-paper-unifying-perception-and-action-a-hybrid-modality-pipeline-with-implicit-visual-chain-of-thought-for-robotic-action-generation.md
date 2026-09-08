---
title: "Unifying Perception and Action: A Hybrid-Modality Pipeline with Implicit Visual Chain-of-Thought for Robotic Action Generation"
title_zh: "感知与动作的统一:基于隐式视觉思维链的混合模态机器人动作生成流水线"
authors: "Ma, Xiangkai, Xing, Lekai, Zhang, Han, Li, Wenzhong, Lu, Sanglu"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Ma_Unifying_Perception_and_Action_A_Hybrid-Modality_Pipeline_with_Implicit_Visual_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: VLA模型将视觉先验映射为机器人动作
tldr: "针对视觉思维链VLA模型在视觉观测与底层动作之间存在模态鸿沟、训练不稳定等难题,本文设计了混合模态流水线。该方法通过隐式视觉思维链与视觉-动作轨迹统一表征,将感知与动作生成紧密结合。实验表明在复杂空间环境下方法稳定性与动作质量均显著提升,为通用机器人的视觉到动作映射提供了新的统一框架。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1604, \"height\": 660, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1704, \"height\": 1108, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1644, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 794, \"height\": 364, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 846, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 847, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 846, \"height\": 214, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 235, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 847, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 849, \"height\": 204, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 844, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 840, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-ma-unifying-perception-and-action-a-hybrid-modality-pipeline-with-implicit-visual-cvpr-2026-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 848, \"height\": 172, \"label\": \"Table\"}]"
motivation: 现有视觉CoT VLA模型在视觉-动作模态间隙与训练稳定性方面存在不足。
method: "提出隐式视觉思维链混合模态流水线,通过视觉-动作统一轨迹表征联合生成。"
result: 在复杂空间环境下显著提升了动作生成稳定性与质量。
conclusion: 为通用机器人智能体提供了统一的视觉-动作协同生成框架。
---

## Abstract
Vision-Language-Action (VLA) models built upon Chain-of-Thought (CoT) have achieved remarkable success in advancing general-purpose robotic agents, owing to its significant perceptual comprehension. Recently, since text-only CoT struggles to adequately capture scene details in complex spatial environments, a highly promising strategy involves leveraging visual priors to guide robotic action generation. Nevertheless, these strategies face two inherent challenges: (i) a modality gap between visual observations and low-level actions, and (ii) unstable training due to competing objectives between visual prediction and action generation. To address these challenges, we propose a Vision-Integrated Trajectory Alignment (VITA) framework that learns a shared discrete latent space for vision and action, enabling joint modeling of perception and motor control. VITA introduces a implicit visual CoT: autoregressively generated tokens is simultaneously decoded into future frames predictions and robot actions, thereby internalizing visual dynamics as an inductive bias for motion planning. Extensive experiments on simulated and real-world environments demonstrate state-of-the-art performance. VITA improves 14.5%, 9.6% and 12.1% over existing baselines on CALVIN, LIBERO and SimplerEnv. Furthermore, VITA attains an average success rate of 80.5% across six real-world tasks, demonstrating its potential as a generalist robotic manipulation model.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper on VITA (Vision-Integrated Trajectory Alignment). I need to organize it according to 8 specific points using Markdown formatting with hierarchical headings and bullet points. Let me analyze the paper carefully.

The paper is about VITA, a VLA (Vision-Language-Action) framework that unifies perception and action through a shared discrete latent space. Let me extract the key information:

1. Core problem: Modality gap between visual observations and actions, training instability in visual CoT approaches
2. Method: Cross-modal vector quantization, shared codebook, implicit visual CoT, progressive training
3. Experiments: CALVIN, LIBERO, SimplerEnv (simulation), real-world UR-5e tasks
4. Compute: 16 NVIDIA A100 GPUs, 300K steps, ~5 days, 2.8B parameters
5. Number of experiments: Many ablations, multiple benchmarks
6. Conclusions: SOTA performance on multiple benchmarks
7. Strengths: Unified latent space, joint optimization, etc.
8. Limitations: Need to identify any

Let me write this up in Chinese with detailed structure.</think>

# 论文总结：VITA —— 感知与动作统一的混合模态机器人动作生成框架

## 1. 核心问题与研究动机

### 1.1 背景
- Vision-Language-Action (VLA) 模型借助 Vision-Language Model (VLM) 的感知先验，将视觉语义与机器人动作结合，是当前通用机器人研究的核心方向。
- 在复杂长时序任务中，**纯文本 Chain-of-Thought (Textual CoT)** 难以表达细粒度空间结构，描述存在歧义，因此研究者提出引入 **Visual CoT**，让模型先预测未来帧，再据此生成动作（即 "predict-then-act" 范式）。

### 1.2 现有视觉 CoT 方法的两大瓶颈
- **模态鸿沟（Modality Gap）**：高维像素级视觉观测与低维底层动作之间存在本质差异，预测未来帧中的大量像素细节对动作执行而言是冗余的，难以直接用于精确动作生成。
- **训练不稳定**：视觉预测任务与动作生成任务之间存在**优化目标竞争**，导致预训练知识被快速遗忘；同时 "predict-then-act" 范式推理延迟高，无法满足高频操控需求。

### 1.3 生物学类比
- 人类无需在脑中完整模拟未来视觉状态再执行动作，而是基于任务需求与视觉感知形成"**运动直觉（motor intuition）**"，直接驱动小脑输出精确运动指令。

---

## 2. 方法论：VITA 框架

### 2.1 整体思想
- 提出 **Vision-Integrated Trajectory Alignment (VITA)** 框架，通过构建**视觉-动作共享的离散潜空间（shared codebook）**，将感知与控制统一在同一表征中。
- 引入 **隐式视觉思维链（Implicit Visual CoT）**：VLM 主干自回归生成的同一序列 token 被同时解码为未来帧预测与机器人动作，将视觉预测内化为动作生成的**归纳偏置（inductive bias）**。

### 2.2 关键技术细节

#### 2.2.1 跨模态向量量化框架
- 共享 codebook $C = \{c_k\}_{k=1}^K \subset \mathbb{R}^d$，通过最近邻查找完成量化 $Q(z) = c_k$，$k = \arg\min_j \|z - c_j\|_2$。
- 视觉与动作两个分支独立训练，**不需要跨模态配对数据**，靠共享 codebook 实现结构对齐。

#### 2.2.2 视觉自编码与量化
- 输入连续两帧 $(I_t, I_{t+1})$，用冻结的 DINOv2 提取空间特征，再经 M-Former 得到时空运动嵌入 $z_v$。
- 量化后通过视觉解码器重构未来帧 $I_{t+1}$，损失为 L1 + SSIM：
  $$\mathcal{L}_v = \lambda_{L1}\|I_{t+1} - \hat{I}_{t+1}\|_1 + \lambda_{SSIM}(1 - SSIM(I_{t+1}, \hat{I}_{t+1}))$$

#### 2.2.3 动作自编码与量化（FAST 风格）
- 对动作段 $a_{t:t+H}$ 先做 DCT 变换压缩时序，再用 MLP 编码到潜空间 $z_a$，量化后经逆 DCT 解码回连续轨迹。
- 采用 MSE 损失重建动作序列，并按位置/旋转/夹爪力分维度归一化。

#### 2.2.4 VLM 主干 + 渐进式注意力
- 两阶段推理：先做 **Textual CoT**（将高层指令分解为符号子任务 GRASP/LIFT/MOVE/PLACE 等），再做 **Internal CoT**（自回归生成共享 token）。
- 渐进式混合注意力：input token 之间双向 → textual token 之间双向 → input → textual → cross-modal 之间因果，建立有向信息流。

#### 2.2.5 双解码输出
- 同一组 token $\{c_{\tau_i}\}$ 同时送入视觉解码器 $D_v$ 预测未来帧和动作解码器 $D_a$ 预测动作轨迹。

### 2.3 三阶段渐进训练
1. **Warmup（热身）**：分别训练视觉分支、动作分支、共享 codebook，无需配对数据。
2. **Co-train（联合训练）**：冻结 codebook，联合训练 VLM 主干 + 视觉解码器 + 动作解码器。混合两类数据——纯视频数据和视频-动作配对数据，损失为：
   $$\mathcal{L}_{co} = \lambda_v \|I_{1:T} - \hat{I}_{1:T}\|_1 + \lambda_a \|a_{1:H} - \hat{a}_{1:H}\|_2^2$$
3. **Fine-tune（微调）**：仅微调解码器用于具体任务部署。

---

## 3. 实验设计

### 3.1 数据集
- 训练阶段使用 13 个数据集混合，包括：
  - 人体示范视频：SSv2、Ego4D
  - 真实机器人数据：OXE、RoboMIND
  - 仿真机器人数据：CALVIN-ABC、LIBERO

### 3.2 仿真 Benchmark
- **CALVIN ABC-D**：长时序、多步骤家庭任务
- **LIBERO**：GOAL/SPATIAL/OBJECT/LONG 四套测试
- **SimplerEnv**：Google Robot 与 WidowX 两个分支

### 3.3 真实世界 Benchmark
- 基于 UR-5e 机械臂，6 个桌面任务（4 个 ID + 2 个 OOD），每个任务 100 次 rollout。
- OOD 任务包括 "Inverse Execution"、"Conditional Decision" 等需要抽象推理与上下文理解的场景。

### 3.4 基线对比
- 仿真：GR-1、OpenVLA、Octo、CogACT、UP-VLA、CoT-VLA、TraceVLA、SpatialVLA、UniVLA、DeFI、Pi0-FAST。
- 真实：Pi0、OpenVLA、GR00T N1.5、Octo。

---

## 4. 资源与算力

- **GPU**：16 块 NVIDIA A100。
- **训练规模**：300K 步，**2.8B 可训练参数**。
- **训练时长**：约 **5 天**。
- **模型组成**：SigLIP (400M, 视觉 tokenizer) + Gemma 2B (VLM 主干) + ViT 12 层 (96M, 视觉解码器) + Transformer (228M, 动作解码器)。
- 推理延迟（RTX 4090 24GB）：平均 **60 Hz** 动作吞吐，端到端延迟约 60–71 ms（Len=12–48）。

---

## 5. 实验数量与充分性

### 5.1 实验规模
- **主实验**：CALVIN、LIBERO（4 子集）、SimplerEnv（2 分支）、真实世界（6 任务）共 7+ 个独立评估场景。
- **消融实验**：
  - 表 6：6 种 CoT 范式对比（无 CoT / Textual / Visual / Textual-Visual / Internal / Textual-Internal）。
  - 表 7：5 种训练策略逐步消融（无量化 / 仅动作解码 / + codebook / + 视觉解码器 / + 人体视频）。
  - 表 8：数据效率（10% 数据 few-shot）与训练效率。
  - 表 9：推理延迟对比。
- **可视化**：图 3-4 展示真实世界和仿真环境的执行轨迹。

### 5.2 充分性与公平性评估
- 优点：
  - 实验覆盖广，仿真 + 真实双验证，ID/OOD 分层评估。
  - 提供 100 次 rollout 统计，比单次实验更具统计意义。
  - 与 10+ 主流基线横向对比，包含近一年最新 SOTA 方法。
  - 消融完整，从 CoT 形式、训练策略、数据来源、效率多维度切入。
- 局限性：
  - 真实世界任务仅 6 个且偏桌面操控，**任务复杂度有限**。
  - 主要与已发表结果对比，部分 baseline 直接引用原论文，可能存在评测细节差异。
  - 真实实验未报告重复次数与方差，仅给出单次均值。

---

## 6. 主要结论与发现

### 6.1 性能提升
- **CALVIN ABC-D**：平均任务完成数 4.73，较 UniVLA 提升 7.3%、较 UP-VLA 提升 16.0%。
- **LIBERO**：四套子集均 SOTA，Long 子集达 96.8%（较 CoT-VLA 提升 36.2%）。
- **SimplerEnv**：Google Robot 57.4%、WidowX 71.5%，均超过 DeFI、UniVLA 等方法。
- **真实世界**：6 任务平均成功率 **80.5%**，显著优于 Pi0（53.5%）、GR00T N1.5（44.6%）等。

### 6.2 关键发现
- **Internal CoT（隐式视觉 CoT）显著优于显式 Visual CoT**：验证了将视觉预测作为归纳偏置优于 "predict-then-act" 串行范式。
- **共享离散潜空间有效缓解模态鸿沟**：无需像素级配对监督即可让视觉先验指导动作。
- **人体视频数据有显著增益**：提供跨域运动先验，进一步提升长时序任务表现。
- **数据/训练效率高**：仅 10% 数据 fine-tune 即可超越 OpenVLA 全量训练结果；收敛速度显著快于消融变体。

---

## 7. 方法亮点

- **统一表征视角新颖**：用共享离散 codebook 将视觉与动作嵌入同一潜空间，避免像素级配对标注需求。
- **Internal CoT 巧妙设计**：单 token 流双解码，兼顾视觉感知与动作生成，无额外推理开销。
- **渐进式训练策略稳健**：warmup → co-train → fine-tune 三阶段解耦，避免优化目标竞争。
- **推理高效**：相比 CoT-VLA 的 168–244 ms，VITA 仅 60–71 ms，**降低约 3-4 倍延迟**。
- **跨域知识迁移能力强**：融合人体视频、真实机器人、仿真数据，模型可扩展为通用操控基础模型。
- **泛化能力强**：在 OOD 真实任务上保持 66–71% 成功率，远超基线（Octo 在 OOD 上下降 48%）。

---

## 8. 不足与局限

- **真实世界评估规模有限**：仅 6 个桌面任务，缺少移动操作、双臂协作、柔性物体等复杂场景。
- **缺少失败案例分析**：未系统报告模型失败的分布与原因（如物体遮挡、指令歧义等）。
- **OOD 任务定义有限**：所谓 OOD 仍是同一桌面设置内的变体，未涉及跨环境、跨形态（embodiment）泛化。
- **推理延迟优化空间**：60 Hz 对低频任务足够，但对高动态操作（如抓取运动物体）仍可能受限。
- **与其他方法的延迟/算力可比性**：未提供统一硬件下全部 baseline 的延迟对比。
- **理论分析不足**：对共享 codebook 学到的语义、对齐机制缺乏可视化或定量分析（如 token 激活频率、跨模态检索召回率等）。
- **训练数据规模/计算成本较高**：5 天 × 16 卡 A100 的算力门槛可能限制复现性，对中小实验室不友好。
- **Codebook 大小 $K$ 与训练稳定性关系**：未深入讨论 codebook 容量对最终性能的影响。
- **安全与可解释性**：在真实机器人部署中缺乏安全约束、失败恢复机制的讨论。

（完）
