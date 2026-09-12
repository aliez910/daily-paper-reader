---
title: "LaMP: Learning Vision-Language-Action Policies with 3D Scene Flow as Latent Motion Prior"
title_zh: LaMP：以三维场景流作为潜在运动先验的视觉语言动作策略学习
authors: "Xinkai Wang, Chenyi Wang, Yifu Xu, Mingzhe Ye, Fu-Cheng Zhang, Jialin Tian, Xinyu Zhan, Lifeng Zhu, Cewu Lu, Lixin Yang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/295.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操作的视觉语言动作框架，在LIBERO基准上评估
tldr: 现有VLA模型直接从二维语义视觉特征回归动作，难以隐式学习复杂的三维物理交互，在不熟悉的空间动态下性能下降。本文提出LaMP双专家框架，将稠密三维场景流作为潜在运动先验嵌入，通过门控交叉注意力对齐流匹配运动专家与策略预测动作专家。在LIBERO、LIBERO-Plus和SimplerEnv等复杂操作基准上的评估验证了该方法的有效性，为端到端视觉运动学习提供了更强的三维感知能力。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1691, \"height\": 634}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 679, \"height\": 405}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 682, \"height\": 402}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 428, \"height\": 381}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 591, \"height\": 381}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 671, \"height\": 380}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 518, \"height\": 381}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 671, \"height\": 380}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 671, \"height\": 380}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 791, \"height\": 376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 629, \"height\": 489}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-012.webp\", \"caption\": \"\", \"page\": 1, \"index\": 12, \"width\": 422, \"height\": 293}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-013.webp\", \"caption\": \"\", \"page\": 1, \"index\": 13, \"width\": 596, \"height\": 418}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-014.webp\", \"caption\": \"\", \"page\": 1, \"index\": 14, \"width\": 589, \"height\": 423}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-015.webp\", \"caption\": \"\", \"page\": 1, \"index\": 15, \"width\": 422, \"height\": 295}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-016.webp\", \"caption\": \"\", \"page\": 1, \"index\": 16, \"width\": 424, \"height\": 295}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-017.webp\", \"caption\": \"\", \"page\": 1, \"index\": 17, \"width\": 1465, \"height\": 633}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-018.webp\", \"caption\": \"\", \"page\": 1, \"index\": 18, \"width\": 762, \"height\": 538}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-019.webp\", \"caption\": \"\", \"page\": 1, \"index\": 19, \"width\": 760, \"height\": 550}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-020.webp\", \"caption\": \"\", \"page\": 5, \"index\": 20, \"width\": 946, \"height\": 531}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-021.webp\", \"caption\": \"\", \"page\": 5, \"index\": 21, \"width\": 536, \"height\": 402}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-022.webp\", \"caption\": \"\", \"page\": 5, \"index\": 22, \"width\": 536, \"height\": 402}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-023.webp\", \"caption\": \"\", \"page\": 5, \"index\": 23, \"width\": 536, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-024.webp\", \"caption\": \"\", \"page\": 5, \"index\": 24, \"width\": 712, \"height\": 536}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-025.webp\", \"caption\": \"\", \"page\": 5, \"index\": 25, \"width\": 655, \"height\": 492}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-026.webp\", \"caption\": \"\", \"page\": 5, \"index\": 26, \"width\": 401, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-027.webp\", \"caption\": \"\", \"page\": 5, \"index\": 27, \"width\": 402, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-028.webp\", \"caption\": \"\", \"page\": 5, \"index\": 28, \"width\": 401, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-029.webp\", \"caption\": \"\", \"page\": 5, \"index\": 29, \"width\": 480, \"height\": 596}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-030.webp\", \"caption\": \"\", \"page\": 5, \"index\": 30, \"width\": 453, \"height\": 685}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-031.webp\", \"caption\": \"\", \"page\": 5, \"index\": 31, \"width\": 858, \"height\": 488}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-032.webp\", \"caption\": \"\", \"page\": 5, \"index\": 32, \"width\": 711, \"height\": 536}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-033.webp\", \"caption\": \"\", \"page\": 5, \"index\": 33, \"width\": 711, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-034.webp\", \"caption\": \"\", \"page\": 5, \"index\": 34, \"width\": 1124, \"height\": 632}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-035.webp\", \"caption\": \"\", \"page\": 5, \"index\": 35, \"width\": 686, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-036.webp\", \"caption\": \"\", \"page\": 5, \"index\": 36, \"width\": 439, \"height\": 301}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-037.webp\", \"caption\": \"\", \"page\": 5, \"index\": 37, \"width\": 725, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-038.webp\", \"caption\": \"\", \"page\": 5, \"index\": 38, \"width\": 800, \"height\": 493}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-039.webp\", \"caption\": \"\", \"page\": 5, \"index\": 39, \"width\": 1200, \"height\": 805}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-040.webp\", \"caption\": \"\", \"page\": 5, \"index\": 40, \"width\": 792, \"height\": 449}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-041.webp\", \"caption\": \"\", \"page\": 5, \"index\": 41, \"width\": 536, \"height\": 398}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-042.webp\", \"caption\": \"\", \"page\": 11, \"index\": 42, \"width\": 1496, \"height\": 820}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-043.webp\", \"caption\": \"\", \"page\": 12, \"index\": 43, \"width\": 1490, \"height\": 816}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-044.webp\", \"caption\": \"\", \"page\": 12, \"index\": 44, \"width\": 1785, \"height\": 1385}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-045.webp\", \"caption\": \"\", \"page\": 12, \"index\": 45, \"width\": 1037, \"height\": 1088}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-046.webp\", \"caption\": \"\", \"page\": 12, \"index\": 46, \"width\": 548, \"height\": 386}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-047.webp\", \"caption\": \"\", \"page\": 12, \"index\": 47, \"width\": 546, \"height\": 386}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-048.webp\", \"caption\": \"\", \"page\": 12, \"index\": 48, \"width\": 553, \"height\": 385}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-049.webp\", \"caption\": \"\", \"page\": 12, \"index\": 49, \"width\": 439, \"height\": 302}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-050.webp\", \"caption\": \"\", \"page\": 12, \"index\": 50, \"width\": 685, \"height\": 460}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-051.webp\", \"caption\": \"\", \"page\": 12, \"index\": 51, \"width\": 438, \"height\": 302}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-052.webp\", \"caption\": \"\", \"page\": 12, \"index\": 52, \"width\": 685, \"height\": 460}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-053.webp\", \"caption\": \"\", \"page\": 12, \"index\": 53, \"width\": 685, \"height\": 460}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-054.webp\", \"caption\": \"\", \"page\": 12, \"index\": 54, \"width\": 440, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-055.webp\", \"caption\": \"\", \"page\": 12, \"index\": 55, \"width\": 947, \"height\": 366}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-056.webp\", \"caption\": \"\", \"page\": 12, \"index\": 56, \"width\": 947, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-057.webp\", \"caption\": \"\", \"page\": 12, \"index\": 57, \"width\": 945, \"height\": 371}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3e52d33d8b3797114c7a00d3/fig-058.webp\", \"caption\": \"\", \"page\": 14, \"index\": 58, \"width\": 1496, \"height\": 820}]"
motivation: 现有VLA模型直接从二维视觉特征回归动作，隐式学习三维物理交互，在陌生空间动态下性能下降。
method: 提出双专家LaMP框架，将三维场景流作为潜在运动先验，通过门控交叉注意力对齐运动专家与动作专家。
result: 在LIBERO、LIBERO-Plus和SimplerEnv等复杂操作基准上验证了三维感知对动作预测的提升效果。
conclusion: 为VLA模型引入显式三维运动先验，推动了端到端视觉运动机器人操作的性能上限。
---

## Abstract
We introduce LaMP, a dual-expert Vision-Language-Actionframework that embeds dense 3D scene flow as a latent motion prior forrobotic manipulation. Existing VLA models regress actions directly from2D semantic visual features, forcing them to learn complex 3D physicalinteractions implicitly. This implicit learning strategy degrades underunfamiliar spatial dynamics. LaMP addresses this limitation by aligninga flow-matching Motion Expert with a policy-predicting Action Expertthrough gated cross-attention. Specifically, the Motion Expert generatesa one-step partially denoised 3D scene flow, and its hidden states condi-tion the Action Expert without full multi-step reconstruction. We eval-uate LaMP on the LIBERO, LIBERO-Plus, and SimplerEnv-WidowXsimulation benchmarks as well as real-world experiments. LaMP consis-tently outperforms evaluated VLA baselines across LIBERO, LIBERO-Plus, and SimplerEnv-WidowX benchmarks, achieving the highest re-ported average success rates under the same training budgets. On LIBERO-Plus OOD perturbations, LaMP shows improved robustness with an av-erage 9.7% gain over the strongest prior baseline. Our project page isavailable at https://summerwxk.github.io/lamp-project-page/.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "LaMP: Learning Vision-Language-Action Policy with 3D Scene Flow as Latent Motion Prior". I need to organize it according to the 8 points specified, using Markdown formatting with hierarchical headings and bullet points.

Let me carefully analyze the paper content and structure my response.

Key points from the paper:
1. Core problem: VLA models regress actions from 2D semantic features, implicitly learning 3D physical interactions, which degrades under unfamiliar spatial dynamics
2. Method: LaMP dual-expert framework with Motion Expert (flow-matching 3D scene flow) and Action Expert connected via gated cross-attention
3. Experiments: LIBERO, LIBERO-Plus, SimplerEnv-WidowX, real-world tasks
4. Compute: 16 NVIDIA H100 GPUs
5. Conclusions: LaMP achieves highest success rates across benchmarks

Let me write a detailed, structured summary in Chinese.</think>

# LaMP 论文总结：以 3D 场景流作为潜在运动先验的视觉语言动作策略

## 1. 核心问题与研究动机

- **根本矛盾**：现有 Vision-Language-Action (VLA) 模型（如 π0、π0.5、GR00T、UniVLA、FlowVLA 等）直接从 2D 语义视觉特征回归机器人动作，缺少对 3D 物理动态的显式建模。
- **能力瓶颈**：VLM 的视觉特征本质上是 2D 且语义导向的，而机器人操控需要推理显式的 3D 几何与接触关系；这种"2D–3D 鸿沟"迫使模型仅凭动作监督隐式学习 3D 物理交互，导致在相机视角、物体位置变化等陌生空间动态下鲁棒性下降。
- **典型失败模式**：纯 2D 策略在需要精确深度控制的任务（如插孔、紧公差堆叠）以及 OOD 视觉扰动下表现尤其脆弱（LIBERO-Plus 已揭示此问题）。
- **核心假设**：稠密 3D 场景流不仅是动作的可观测副产物，更应作为"潜在运动先验"，主动引导策略学习。

## 2. 方法论

### 2.1 整体框架

- **双专家（Dual-Expert）架构**：
  - **Motion Expert**（≈300M 参数，CogVideoX 风格 3D Transformer）：通过条件流匹配（Flow Matching）建模稠密 3D 场景流，作为运动先验。
  - **Action Expert**（≈300M 参数）：通过流匹配预测连续动作块。
  - **门控跨注意力（Gated Cross-Attention）**（≈30M 参数）：连接两者，将单步部分去噪的运动隐藏状态注入到 VLM 最后一层特征中。
- **预训练 VLM**：Qwen3-VL-4B-Instruct 作为感知主干（冻结）。
- **概率分解**：
  $$P(A_{t:t+H}, M_t \mid z_t) = \underbrace{P(A_{t:t+H} \mid z_t, M_t)}_{\text{Action Expert}} \cdot \underbrace{P(M_t \mid z_t)}_{\text{Motion Expert}}$$

### 2.2 关键技术细节

- **3D 场景流表示**：在图像平面采样 20×20 = 400 个关键点，每个点跟踪未来 T=32 步的位移增量 (Δu, Δv, Δd)，轨迹经统一参考相机帧 (camref) 校准，对相机运动鲁棒。
- **流匹配训练**（运动）：
  - 噪声插值 $M^\tau = (1-\tau)\epsilon + \tau M_t$，训练 Motion Expert 预测速度场 $M_t - \epsilon$。
  - 损失：$\mathcal{L}_{\text{motion}} = \mathbb{E}_{\tau, M_t, \epsilon} \| v_\theta(M^\tau, \tau, z_t) - (M_t - \epsilon) \|_2^2$。
- **单步部分去噪（One-Step Partial Denoising）**：推理时从纯噪声出发，仅走 N=10 步 ODE 中的第 1 步（τ=0→0.1），提取中间隐藏状态 $z_m \in \mathbb{R}^{B \times N \times d_m}$，避免完整多步重建的高延迟。
- **门控跨注意力融合**：
  $$z_{\text{guided}} = z + \sigma(g) \cdot \mathrm{CA}(Q = \mathrm{LN}(z), K = V = \tilde{h}_{\text{motion}})$$
  其中 $g$ 为零初始化的可学习标量门控（经 sigmoid 约束），训练中自适应放大以保留预训练 VLM 表达。
- **动作流匹配**：与运动专家同构，$\mathcal{L}_{\text{action}} = \mathbb{E} \| v_\phi(a^\tau, \tau, z_{\text{guided}}) - (a - \epsilon^a) \|_2^2$。

### 2.3 两阶段训练流程

- **Stage I（Motion 预训练）**：用 TraceForge 标注器从 LIBERO / BridgeV2 / DROID / InternData-A1 构建 1.6M (观测-语言-运动) 三元组，训练 Motion Expert。
- **Stage II（动作后训练）**：冻结 VLM 与 Motion Expert，仅训练 Motion Guidance + Action Expert（仍以单步去噪方式提供条件）。
- **推理流程**：VLM 编码 → Motion Expert 单步去噪 → 门控融合 → Action Expert 去噪采样动作。

## 3. 实验设计

### 3.1 仿真基准与数据集

- **LIBERO**（4 个子套件）：Spatial / Object / Goal / Long，每套件 10 任务，每任务 500 条专家演示，单策略跨套件联合训练，每任务评估 50 episodes。
- **LIBERO-Plus**（零样本 OOD）：7 类扰动维度（Camera / Robot / Language / Light / Background / Noise / Layout），不进行任何额外训练。
- **SimplerEnv-WidowX**：基于 BridgeV2 真实数据训练，零样本迁移到 WidowX 仿真，4 个任务（Stack Block / Put Spoon / Put Carrot / Put Eggplant）。
- **RoboTwin 2.0**（补充）：10 个双臂任务，clean/randomized 设置。
- **真实世界**：Flexiv Rizon 4 (7-DoF) + Robotiq 2F-85 + Intel RealSense D415；160 条专家演示（约 1 小时遥操作）。

### 3.2 真实任务设计

- **域内任务**（三类）：
  - Pick-and-Place（堆杯）：6-DoF 刚体操控；
  - Fold Towel（叠毛巾）：4 阶段可形变体操控；
  - Making Bread（做早餐）：3 阶段长视野多步任务。
- **OOD 条件**：未见过布局 / 未见过物体（替换颜色或容器） / 未见过背景。

### 3.3 对比方法

- **General VLA**：OpenVLA、OpenVLA-OFT、π0、π0.5、GR00T N1。
- **Latent-Action VLA**：UniVLA、villa-X。
- **Video-Based VLA**：mimic-video、WorldVLA、F1。
- **2D Flow/Trace-Guided VLA**：FlowVLA、TraceVLA。
- **3D-Aware VLA**：GeoVLA、SpatialVLA、RoboVLMs。
- **真实世界对比**：π0、3D FDP（作者重新实现）。

### 3.4 消融实验

- **变体**：No-Motion / 2D-Flow Prior / Add（直接相加） / Concat+MLP。
- **对比维度**：几何先验的有无（Q1）、3D vs 2D（Q2）、OOD 鲁棒性（Q3）、融合策略（Q4）。

## 4. 资源与算力

- **GPU**：16 × NVIDIA H100。
- **代码框架**：基于 starVLA 构建。
- **推理开销**：Motion Expert 仅增加 1.35× 延迟和 1.15× 显存，可保持实时控制。
- **真实世界推理**：单卡 NVIDIA RTX 4090 工作站。
- **训练预算声明**：在相同训练预算（same training budgets）下对比，未给出具体训练时长或总 epoch。

## 5. 实验数量与充分性

- **仿真实验**：覆盖 3 个公开基准（LIBERO 4 子套件、LIBERO-Plus 7 维度、SimplerEnv-WidowX 4 任务）+ RoboTwin 2.0 双臂扩展，规模充足。
- **真实世界实验**：3 类任务 ×（域内 10 trials + OOD 3 条件 × 5 trials），对比 3 种方法（LaMP / π0 / 3D FDP）。
- **消融维度**：4 个变体（No-Motion / 2D-Flow / Add / Concat+MLP）× SimplerEnv 4 任务。
- **公平性**：
  - 仿真中明确说明"相同训练预算"对比；
  - 真实世界中 π0 与 LaMP 使用相同数据集与训练协议；
  - 3D FDP 由于无官方实现，作者基于原论文重实现，可能引入实现偏差；
  - LIBERO 与 SimplerEnv 上的每任务评估 episodes 数固定（50），统计稳定性较好，但真实世界实验每条件 5 trials 样本量较小。
- **可视化分析**：提供运动先验轨迹预测可视化（图 5c），定性验证运动专家学习的物理意义。

## 6. 主要结论与发现

- **LIBERO**：LaMP 平均成功率 **98.3%**，超过最强基线 π0.5（96.9%），Long 子套件 **96.7%**（π0.5 仅 92.4%）。
- **LIBERO-Plus OOD**：平均 **79.3%**，超过最强基线 OpenVLA-OFT（69.6%）**+9.7 pp**；Camera 和 Robot 维度上提升尤为显著（Camera +8.1、Robot +37.7 over π0-Fast）。
- **SimplerEnv-WidowX**：平均 **79.2%**，超 FlowVLA（74.0%）+5.2 pp，Stack Block 单任务 75.0%（次优 FlowVLA 仅 62.5%）。
- **消融结论**：
  - 移除 Motion Expert：LIBERO 平均 −5.9%（Long −18.5%），SimplerEnv −22.9%（Stack Block −50.0%）；
  - 2D Flow → 3D Scene Flow：Stack Block +16.7%，Put Spoon +8.3%；
  - Add / Concat+MLP 融合在 Stack Block 上崩塌（33.3% / 45.8% vs 75.0%）。
- **真实世界**：LaMP 在 Pick-and-Place / Deformable / Long-Horizon / OOD 上分别为 80% / 50% / 80% / 62.5%，全面优于 π0（70/40/70/52.5%）和 3D FDP（53/40/60/26.8%）；OOD 下 3D FDP 崩塌 26.2 pp，LaMP 仅降 17.5 pp。
- **RoboTwin 2.0**：clean / randomized 设置下分别为 83.9% / 81.8%。

## 7. 方法与实验设计的亮点

- **概念创新**：将稠密 3D 场景流定位为"潜在运动先验"而非可观测输出，论证其作为显式中间表示的必要性。
- **单步部分去噪策略**：避免完整多步 ODE 重建的高延迟，同时保留任务相关动力学，兼顾精度与效率。
- **零初始化门控机制**：从近零注入出发，自适应放大运动引导，缓解预训练 VLM 表示崩塌（论文指出朴素融合会引起表征崩塌）。
- **跨本体一致性**：运动表示采用参考相机帧 (Δu, Δv, Δd)，与具体机器人无关；使其可在 BridgeV2 / DROID / InternData-A1 / LIBERO 等异质数据上联合训练，并零样本迁移到新本体。
- **系统消融严谨**：围绕 4 个 Research Question 设计对应消融，逐项验证几何先验、3D vs 2D、OOD 鲁棒性、融合策略的必要性。
- **真实世界证据完整**：覆盖刚体 / 可形变 / 长视野三类任务 + 三类 OOD 条件，含可视化证据（运动先验轨迹预测）。

## 8. 不足与局限

- **运动表征固定**：Motion Expert 空间分辨率（20×20）与时间长度（T=32）固定，缺乏自适应分辨率与更长视野建模能力。
- **标注依赖**：依赖 TraceForge 离线生成的 3D 场景流作为监督，未尝试直接从无标注 in-the-wild 视频中学习运动先验；Depth 标注源在不同数据集间不一致（TraceForge 估计 vs 传感器深度）。
- **融合深度受限**：仅在 VLM 最后一层注入运动信息，多层融合会引发表征崩塌，多层消融与改进路径仍属未来工作。
- **真实世界样本量小**：每 OOD 条件仅 5 trials，统计显著性可能不足；缺少多次随机种子的置信区间报告。
- **3D FDP 实现偏差**：由于无官方代码，作者自实现可能引入不公平因素；3D FDP 在真实世界需逐任务训练，天然处于劣势，未充分控制这一变量。
- **消融维度不完整**：未对单步去噪步数 τ=0.1、运动空间网格大小 K、轨迹长度 T 等超参数进行系统性消融。
- **任务覆盖偏差**：真实世界仅一种硬件平台（Flexiv Rizon 4），双臂 / 移动机器人的真实部署仅在 RoboTwin 仿真中给出，泛化性结论尚需扩展。
- **依赖深度信息**：训练标注阶段使用深度（TraceForge 估计或传感器），虽然推理时无需深度传感器，但训练管线对深度质量敏感，可能限制其在缺乏合适单目深度估计器的场景中的可扩展性。

（完）
