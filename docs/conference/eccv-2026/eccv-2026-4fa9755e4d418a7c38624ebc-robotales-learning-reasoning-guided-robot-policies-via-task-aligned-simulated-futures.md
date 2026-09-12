---
title: "RoboTALES: Learning Reasoning-Guided Robot Policies via Task-Aligned Simulated Futures"
title_zh: RoboTALES：通过任务对齐仿真未来学习推理引导的机器人策略
authors: "Hanan Gani, Tejal Kulkarni, Madhoolika Chodavarapu, Nicklas Hansen, Manmohan Chandraker"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/11562.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 通过任务对齐的未来仿真进行视觉运动机器人策略学习
tldr: 预训练视频生成模型为视觉运动控制提供了富有想象力的未来预测，但其生成的未来常偏离任务意图且对动作条件不敏感，难以直接用于规划与策略提取。本文提出RoboTALES单阶段框架，通过分层LLM规划器将复杂任务分解为子目标以引导模型想象，并由VLM评价器依据奖励反馈评估所生成的未来，确保内部表征持续聚焦任务意图，进而训练出可靠的视觉运动机器人策略，展示了视频生成模型在复杂机器人操纵任务中的可用性。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 768, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 768, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 768, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 558, \"height\": 447}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-005.webp\", \"caption\": \"\", \"page\": 6, \"index\": 5, \"width\": 578, \"height\": 350}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-006.webp\", \"caption\": \"\", \"page\": 6, \"index\": 6, \"width\": 1280, \"height\": 1279}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-007.webp\", \"caption\": \"\", \"page\": 12, \"index\": 7, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-008.webp\", \"caption\": \"\", \"page\": 12, \"index\": 8, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-009.webp\", \"caption\": \"\", \"page\": 12, \"index\": 9, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-010.webp\", \"caption\": \"\", \"page\": 12, \"index\": 10, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-011.webp\", \"caption\": \"\", \"page\": 12, \"index\": 11, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-012.webp\", \"caption\": \"\", \"page\": 12, \"index\": 12, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-013.webp\", \"caption\": \"\", \"page\": 12, \"index\": 13, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-014.webp\", \"caption\": \"\", \"page\": 12, \"index\": 14, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-015.webp\", \"caption\": \"\", \"page\": 12, \"index\": 15, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-016.webp\", \"caption\": \"\", \"page\": 12, \"index\": 16, \"width\": 1376, \"height\": 1376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-017.webp\", \"caption\": \"\", \"page\": 13, \"index\": 17, \"width\": 1900, \"height\": 1180}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-018.webp\", \"caption\": \"\", \"page\": 13, \"index\": 18, \"width\": 1457, \"height\": 846}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-019.webp\", \"caption\": \"\", \"page\": 13, \"index\": 19, \"width\": 2068, \"height\": 1469}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-020.webp\", \"caption\": \"\", \"page\": 13, \"index\": 20, \"width\": 1473, \"height\": 1033}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-021.webp\", \"caption\": \"\", \"page\": 13, \"index\": 21, \"width\": 1781, \"height\": 1062}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-4fa9755e4d418a7c38624ebc/fig-022.webp\", \"caption\": \"\", \"page\": 13, \"index\": 22, \"width\": 2793, \"height\": 1737}]"
motivation: 视频生成模型的想象未来偏离任务意图且对动作不敏感，难以直接用于策略学习。
method: 结合分层LLM规划器与VLM评价器，引导视频模型生成任务对齐的未来并据此训练策略。
result: 在多种视觉运动机器人操纵任务中获得了更可靠的策略表现。
conclusion: 证明任务对齐的视频未来可用于提取面向复杂任务的机器人策略。
---

## Abstract
Pretrained video generative models are promising backbonesfor visuomotor control, but their imagined futures often drift from taskintent and are not reliably action-conditional. As a result, these mod-els can be difficult to use for planning or policy extraction. To addressthese limitations, we propose RoboTALES, a single-stage framework thatlearns task-aligned simulated futures and uses them to train robot poli-cies. Our approach introduces two key innovations: (1) a hierarchicalLLM-based planner that breaks complex tasks into a sequence of sub-goals to guide the model’s imagination; and (2) a VLM-based critic thatevaluates these “imagined” futures and uses reward-based feedback tokeep the model’s internal representations focused on the goal. By an-choring the video generator in abstract reasoning, we produce temporallyconsistent rollouts and more coherent actions. We evaluate RoboTALESon diverse manipulation tasks from RoboCasa and LIBERO10, and showthat our method consistently outperforms existing methods, especiallyin long-horizon tasks. Our code and models are publicly available athttps://github.com/hananshafi/RoboTALES.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze a research paper and produce a structured Chinese summary. Let me carefully read through the paper content and extract the key information for each section requested.

The paper is "RoboTALES: Learning Reasoning-Guided Robot Policies via Task-Aligned Simulated Futures" - an ECCV 2026 paper about using pretrained video generative models for robot visuomotor control, with hierarchical LLM planning and VLM critic feedback.

Let me organize the summary according to the 8 requested points.</think>

# RoboTALES 论文总结

## 1. 核心问题与研究动机

- **核心问题**：预训练的视频生成模型（如 Stable Video Diffusion）虽然可作为视觉运动控制的有力主干，但其"想象"的未来帧往往**偏离任务意图**（drift from task intent），并且**对动作条件的响应不敏感**，导致难以直接用于规划或策略提取。
- **背景与动机**：
  - 人类在执行任务前会进行**分层目标分解 + 心理模拟 + 拒绝式决策**，而现有自主智能体缺乏这种"先想象再行动"的推理基底。
  - 现有基于视频生成的机器人策略方法（如 Video-Policy、Gen2Act、ViPRA）大多把语言与预测解耦：语言只决定执行哪个动作，却不塑造世界模型内部的预测表征，导致"想象"与"行动"之间没有闭环对齐。
  - 现有 LLM/VLM 规划方法仅把语言作为外部指令，不能进入视频生成模型的潜在表征，从而无法保证想象未来的语义忠实性。
- **核心论点**：需要一种机制（i）在想象过程中施加**层次化结构**，（ii）强制想象未来的**语义忠实性**，以使视频模型真正成为面向控制的世界模型。

## 2. 方法论

### 2.1 整体框架

- **名称**：RoboTALES（Learning Reasoning-Guided RoboT Policies via Task-ALigned SimulatEd FutureS）
- **核心思想**：**单阶段（single-stage）联合训练**，将分层 LLM 规划器与 VLM 评价器嵌入到基于扩散的视频世界模型中，使视频模型学会"为行动而想象"。
- **四大组件**：
  1. **LLM Planner $F_P$**：以 Gemini-2.5-Pro 为后端，将自然语言指令 $\tau$ 分解为 K∈[2,5] 个语义子目标 $c^{(1:K)}$，与原指令拼接为增强计划 $C^* = \{\tau; c^{(1)}; c^{(2)}; \dots; c^{(K)}\}$。
  2. **视频生成器 $G_\theta$**：以预训练 SVD 为骨架，条件于当前观测 $s_t$ 与增强计划 $C^*$，预测未来 Δ 帧 $\hat{s}_{t+1:t+\Delta}$。
  3. **VLM Critic $F_R$**：冻结的视觉-语言模型，对解码出的关键帧评估与任务指令的语义对齐程度，给出标量奖励 $r \in \mathbb{R}$。
  4. **动作生成器 $\pi_\phi$**：1D 扩散 UNet（Diffusion Policy），以视频解码器中间特征 $f^{G_\theta^*}_{l}$ 为条件，输出可执行动作序列 $a_{t:t+H}$。

### 2.2 关键创新点

- **Planner-Conditioned Video Generation**：将 LLM 规划结果通过 **cross-attention 模块**（注入 CLIP 嵌入）引入视频扩散模型的潜空间，使生成过程具备里程碑式层次结构。
- **Critic-Guided Representational Steering**：在去噪轨迹上施加 **DDPO（Denoising Diffusion Policy Optimization）**——将去噪过程视为多步 MDP，每一步去噪为动作，VLM 奖励为最终回报，用 REINFORCE 风格目标优化 VideoUNet 的选定参数 $\theta^*$。
- **Reasoning-Aligned Policy Learning**：动作 UNet 与视频 UNet **共享梯度通路**（不设 stop-gradient），动作扩散损失反传回视频解码器，使解码器特征同时优化视觉保真度、语义对齐与下游控制。

### 2.3 联合训练目标

$$\mathcal{L}_{\text{total}}(\theta^*, \phi) = \mathcal{L}_{\text{video}}(\theta^*) + \beta \mathcal{L}_{\text{DDPO}}(\theta^*) + \gamma \mathcal{L}_{\text{action}}(\phi, \theta^*)$$

- **$\mathcal{L}_{\text{video}}$**：标准噪声预测 MSE 损失，仅作用于 cross-attention 与部分解码器层。
- **$\mathcal{L}_{\text{DDPO}}$**：DDPO 目标，其中每步去噪转移的对数似然为
  $$\ell_\theta(x_{t-1}|x_t, C^*) = -\frac{\|x_{t-1} - \mu_\theta(x_t, \sigma_t, C^*)\|_2^2}{2(\sigma_t^{\text{ker}})^2} - \frac{d}{2}\log[2\pi(\sigma_t^{\text{ker}})^2]$$
  优势 $A = r - b(\tau)$，$b(\tau)$ 为按指令维护的奖励运行均值。
- **$\mathcal{L}_{\text{action}}$**：动作扩散的噪声预测损失，动作 UNet 接收来自视频解码器的隐藏嵌入。

### 2.4 训练策略

- **冻结范围**：除视频 UNet 的（i）cross-attention 模块、（ii）向动作 UNet 提供条件的部分解码器层外，其余参数冻结。
- **目的**：保留预训练视觉先验，仅在"语义进入"与"任务抽象涌现"的接口处适配。

## 3. 实验设计

### 3.1 数据集与基准

- **RoboCasa**：大规模日常任务仿真基准，涵盖 24 个操纵任务（取放、开门/关单双门、抽屉开/关、旋钮开关、水龙头、按钮按压、咖啡机插入等），每任务 50 条人类演示。
- **LIBERO10**：知识迁移基准，10 个任务，共 50 条演示。
- **总任务数**：34 个长视野操纵任务。

### 3.2 对比方法

- **RoboCasa 上**：3DA、DP3、DP-ResNet、DP-CLIP（Diffusion Policy 变体）、GR00T、FPV、DP-VLA、UVA、Video-Policy（最强基线）。
- **LIBERO10 上**：DP-C、DP-T、OpenVLA、π0、π0-FAST、UVA、VideoPolicy。

### 3.3 评估协议

- 每任务 50 次 rollout × 5 个不同场景。
- 动作空间 $\mathbb{R}^7$（6-DoF 夹爪位姿 + 抓取开闭标量）。
- 演示分辨率统一为 256×256。

## 4. 资源与算力

- **硬件**：2 块 **NVIDIA A100 80GB** GPU。
- **训练时长**：联合训练约 **6–7 天**，batch size = 1/GPU。
- **其他资源**：
  - 视频 UNet 与 Action UNet 用 Video-Policy（[35]）官方 Stage 2 权重初始化。
  - Planner：Gemini-2.5-Pro（闭源 API）。
  - VLM Critic：复用 [7]、[5]、[37] 中的奖励设置，每 4 步对解码关键帧计算奖励，全程冻结。

## 5. 实验数量与充分性

### 5.1 主结果
- **RoboCasa（24 任务）表 1**：完整列表展示各类任务的成功率，平均成功率 **64%**，Video-Policy 为 57.5%，UVA 为 57%。
- **LIBERO10（10 任务）表 2**：平均成功率 **97%**，VideoPolicy 为 94%，UVA 为 90%。

### 5.2 消融与补充实验
- **Planner 消融（图 4）**：3 个变体（仅 inference 注入 Planner、训练时 Planner conditioning 但无 Critic、完整模型）在 3 个 RoboCasa 任务上的对比。
- **策略优化效果（图 5）**：
  - 轨迹质量：物体-末端执行器距离随时间的方差对比。
  - 鲁棒性：观测加噪 σ ∈ {0, 0.03, 0.06} 下的成功率。
  - 平滑性：末端执行器 jerk 对比。
- **演示效率（图 6a）**：10/25/50 演示下的成功率，与 VideoPolicy、Planner-augmented 变体对比（4 个任务平均）。
- **推理时间（图 6b）**：Planner 仅用于推理，引入的额外开销约 1 秒/episode（3 任务 × 50 demos × 30 episodes 测量）。
- **定性对比（图 3）**：与 VideoPolicy 在同一任务上的视频轨迹对比，展示基线出现物理失真与语义漂移，本文方法保持结构一致性。

### 5.3 公平性说明
- 论文在脚注中说明与 Video-Policy 作者通信确认基线复现数差异，并在本文中**采用与基线完全一致的实验设置**以确保公平对比。
- 此外，注意到部分基线（GR-1、VidMan 等）使用了 300 条演示，而本文仅用 50 条即取得更优成绩，强调了样本效率。

总体而言，实验涵盖 34 任务 + 多个对比方法 + 4 类消融，**充分性较高**，但绝大部分评测集中于仿真环境（RoboCasa、LIBERO），缺乏真实机器人实验。

## 6. 主要结论与发现

- **核心结论**：将"想象"与"层次化推理"显式对齐，可获得更可靠的视频 rollout 与更连贯的下游动作；RoboTALES 在长视野与接触密集任务上显著优于 Video-Policy 等强基线。
- **关键数据点**：
  - RoboCasa 平均成功率 64%（VideoPolicy 57.5%）。
  - LIBERO10 平均成功率 97%（VideoPolicy 94%）。
  - Pick-and-Place 类任务均值 48%，开门/抽屉类结构敏感任务提升尤为显著。
  - 在加噪 σ=0.06 观测下仍保持较高成功率，基线几乎归零。
- **示范效率**：仅 10 条演示即可获得约 43% 成功率，与 VideoPolicy（50 演示）相当。
- **推理效率**：Planner 仅在推理时使用，每回合增量仅约 1 秒。
- **设计启示**：联合训练（不切断动作到视频的梯度通路）显著优于解耦训练，前者能让视频模型学到"对控制有用的"潜在表征。

## 7. 优点

- **问题切入精准**：明确指出现有视频世界模型在"任务对齐"与"动作条件化"两方面的根本缺陷。
- **架构创新**：
  - 将 LLM 规划 token 通过 cross-attention 注入 SVD 潜空间，把高层语义"翻译"为视频生成条件。
  - DDPO + VLM Critic 将语义奖励嵌入扩散采样过程，使表征主动对齐任务。
  - 去除 stop-gradient，实现视频-动作的端到端共适应。
- **理论分析扎实**：给出了 DDPO 的对数似然、转移分布、优势函数等完整数学推导。
- **实验广度大**：34 任务、9+ 基线、消融、鲁棒性、平滑性、效率、推理延迟皆有覆盖。
- **工程考虑周全**：Planner 仅在推理时启用，额外开销小；冻结大部分预训练参数以保持视觉先验。

## 8. 不足与局限

- **奖励信号粗糙**：依赖冻结的 VLM Critic 提供粗粒度的语义奖励，缺乏对子目标完成度、物理合理性等细粒度进度的建模。
- **算力门槛**：联合训练需 2×A100 80GB 跑 6–7 天，且依赖闭源 Gemini-2.5-Pro API 与 SVD Stage 2 权重，复现成本较高。
- **未见真实机器人实验**：所有评测均在 RoboCasa 与 LIBERO10 仿真环境，未给出 sim-to-real 的迁移证据。
- **任务范围有限**：虽然覆盖 34 个任务，但均为桌面/厨房级日常操纵，未涉及移动操作、双手机器人、复杂工具使用等更广场景。
- **超参数敏感**：DDPO 系数 β、η、奖励计算频率（每 4 步）等敏感超参未做系统消融。
- **规划静态性**：LLM Planner 在每次 episode 开始时生成一次子目标序列，**未与环境反馈闭环再规划**，遇到意外扰动时缺乏在线重规划机制。
- **奖励黑客风险**：VLM 奖励可能在分布偏移下被"刷高"而产生不真实但被高分的 rollout，作者未讨论此风险。
- **样本效率提升幅度有限**：50 演示下 64% 的成功率虽优于基线，但距离可实际部署仍存在差距，特别是 TurnOnStove/TurnOffStove/TurnSinkSpout 等任务甚至低于强基线。

（完）
