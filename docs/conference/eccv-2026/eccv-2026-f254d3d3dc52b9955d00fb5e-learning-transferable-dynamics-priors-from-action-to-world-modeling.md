---
title: Learning Transferable Dynamics Priors from Action to World Modeling
title_zh: 从动作到世界建模：学习可迁移的动态先验
authors: "Ze Huang, Zhang Jiahui, Hairuo Liu, Chenxi Zhang, Ran Cheng, Li Zhang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/2406.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向机器人操纵的动作条件世界建模与动态先验
tldr: 本文研究动作条件世界建模以学习可迁移的机器人动态先验。在大规模真实动作标注的机器人操纵数据上预训练多视角交互扩散世界模型A2World，并据此构建场景专用模拟器A2World-sim。该动态先验支持长时序推演与策略评估，可替代真实机器人回放用于策略分析，为视觉-动作映射与模仿学习提供可扩展的仿真训练环境。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 738, \"height\": 230}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-002.webp\", \"caption\": \"\", \"page\": 9, \"index\": 2, \"width\": 1263, \"height\": 780}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-003.webp\", \"caption\": \"\", \"page\": 10, \"index\": 3, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-004.webp\", \"caption\": \"\", \"page\": 10, \"index\": 4, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-005.webp\", \"caption\": \"\", \"page\": 10, \"index\": 5, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-006.webp\", \"caption\": \"\", \"page\": 10, \"index\": 6, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-007.webp\", \"caption\": \"\", \"page\": 10, \"index\": 7, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-008.webp\", \"caption\": \"\", \"page\": 10, \"index\": 8, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-009.webp\", \"caption\": \"\", \"page\": 10, \"index\": 9, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-010.webp\", \"caption\": \"\", \"page\": 10, \"index\": 10, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-011.webp\", \"caption\": \"\", \"page\": 10, \"index\": 11, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-012.webp\", \"caption\": \"\", \"page\": 10, \"index\": 12, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-013.webp\", \"caption\": \"\", \"page\": 10, \"index\": 13, \"width\": 512, \"height\": 256}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-014.webp\", \"caption\": \"\", \"page\": 10, \"index\": 14, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-015.webp\", \"caption\": \"\", \"page\": 10, \"index\": 15, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-016.webp\", \"caption\": \"\", \"page\": 10, \"index\": 16, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-017.webp\", \"caption\": \"\", \"page\": 10, \"index\": 17, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-018.webp\", \"caption\": \"\", \"page\": 10, \"index\": 18, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-019.webp\", \"caption\": \"\", \"page\": 11, \"index\": 19, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-020.webp\", \"caption\": \"\", \"page\": 11, \"index\": 20, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-021.webp\", \"caption\": \"\", \"page\": 11, \"index\": 21, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-022.webp\", \"caption\": \"\", \"page\": 11, \"index\": 22, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-023.webp\", \"caption\": \"\", \"page\": 11, \"index\": 23, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-024.webp\", \"caption\": \"\", \"page\": 11, \"index\": 24, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-025.webp\", \"caption\": \"\", \"page\": 11, \"index\": 25, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-026.webp\", \"caption\": \"\", \"page\": 11, \"index\": 26, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-027.webp\", \"caption\": \"\", \"page\": 11, \"index\": 27, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-028.webp\", \"caption\": \"\", \"page\": 11, \"index\": 28, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-029.webp\", \"caption\": \"\", \"page\": 11, \"index\": 29, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-030.webp\", \"caption\": \"\", \"page\": 11, \"index\": 30, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-031.webp\", \"caption\": \"\", \"page\": 11, \"index\": 31, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-032.webp\", \"caption\": \"\", \"page\": 11, \"index\": 32, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-033.webp\", \"caption\": \"\", \"page\": 11, \"index\": 33, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-034.webp\", \"caption\": \"\", \"page\": 11, \"index\": 34, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-035.webp\", \"caption\": \"\", \"page\": 11, \"index\": 35, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-036.webp\", \"caption\": \"\", \"page\": 11, \"index\": 36, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-037.webp\", \"caption\": \"\", \"page\": 11, \"index\": 37, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-038.webp\", \"caption\": \"\", \"page\": 11, \"index\": 38, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-039.webp\", \"caption\": \"\", \"page\": 11, \"index\": 39, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-040.webp\", \"caption\": \"\", \"page\": 11, \"index\": 40, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-041.webp\", \"caption\": \"\", \"page\": 11, \"index\": 41, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-042.webp\", \"caption\": \"\", \"page\": 11, \"index\": 42, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-043.webp\", \"caption\": \"\", \"page\": 11, \"index\": 43, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-044.webp\", \"caption\": \"\", \"page\": 11, \"index\": 44, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-045.webp\", \"caption\": \"\", \"page\": 11, \"index\": 45, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-046.webp\", \"caption\": \"\", \"page\": 11, \"index\": 46, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-047.webp\", \"caption\": \"\", \"page\": 11, \"index\": 47, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-048.webp\", \"caption\": \"\", \"page\": 11, \"index\": 48, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-049.webp\", \"caption\": \"\", \"page\": 11, \"index\": 49, \"width\": 960, \"height\": 240}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f254d3d3dc52b9955d00fb5e/fig-050.webp\", \"caption\": \"\", \"page\": 11, \"index\": 50, \"width\": 960, \"height\": 240}]"
motivation: 机器人学习需要可复用的交互动态先验，纯外观视频生成无法满足策略评估需求。
method: 在真实动作标注的大规模操纵数据上预训练多视角交互扩散世界模型A2World。
result: 所学动态先验支持长时序策略回放与可扩展的反事实分析。
conclusion: 为视觉-动作策略训练与评估提供了通用的世界模型基础工具。
---

## Abstract
We study action-conditioned world modeling as a scalableway to learn transferable dynamics priors for robot learning. By pre-training a model to predict how actions drive visual scene evolution,the resulting world model captures reusable interaction dynamics be-yond appearance-level video generation. Concretely, we pretrain a multi-view interactive base diffusion world model, A2World, on large-scalerobot manipulation data with real action annotations. We validate thelearned dynamics priors from two complementary perspectives. First,we adapt A2World into a task- or scene-specialized real-world simula-tor, A2World-sim, whose long-horizon rollouts support simulator-basedpolicy evaluation and scalable what-if analysis by replacing real-robotrollouts with world model rollouts. Second, starting from the same pre-trained weights, we adapt A2World into a video-action joint predictionmodel, A2World-policy, that predicts actions under visual and instruc-tion conditioning. Experiments across simulation benchmarks and real-robot settings demonstrate that action-conditioned world model pre-training yields transferable dynamics priors that benefit both simulator-centric and policy-centric robot learning.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Learning Transferable Dynamics Priors from Action to World Modeling" following a specific 8-point structure. Let me carefully analyze the paper content and organize my summary.

Key points from the paper:
1. Core problem: Learning transferable dynamics priors for robot learning through action-conditioned world modeling
2. Method: A2World (base), A2World-sim (long-horizon simulator), A2World-policy (action prediction)
3. Experiments: Pretraining on 2156k trajectories from 8 datasets, evaluation on LIBERO, RoboNet, real-robot platform
4. Resources: 64 H200 GPUs for pretraining, 8 H200 for A2World-sim, 32 H200 for A2World-policy
5. Experiments: Many ablations and comparisons
6. Conclusions: Action-conditioned pretraining yields stronger priors than text-conditioned
7. Strengths: Multi-view, dual-use prior for both simulation and policy
8. Limitations: Need to discuss carefully

Let me write a comprehensive summary in Chinese with markdown formatting.</think>

# 论文总结：从动作到世界建模——学习可迁移的动态先验（A2World）

## 1. 核心问题与研究动机

- **核心问题**：现有的机器人学习方法（基于视频生成模型）主要沿着两条路径发展：① 将视频模型适配为视觉-语言-动作（VLA）策略；② 构建动作条件世界模型用于数据增强与策略评估。然而，这些工作普遍**未充分利用机器人数据预训练所蕴含的可迁移动态先验**，存在以下问题：
  - 直接从通用视频生成检查点微调，未在大规模动作标注的机器人数据上进行专门预训练；
  - 仅在单一数据集上预训练，限制了可吸收的本体形态、相机配置和运动模式；
  - 优化目标往往只针对单一下游任务，未设计为可跨"模拟器中心"与"策略中心"管线复用。
- **整体含义**：论文提出**以动作条件世界建模作为学习可迁移机器人动态先验的可扩展路径**。其核心直觉是：尽管物体、场景、视角各异，但操控任务中动作如何引起状态变化（接触、抓取、推动、释放）的交互规则是普适的；通过让模型预测由动作驱动的视觉演化，可学到超越外观级视频生成的可控、可复用的动作—动力学先验。

## 2. 方法论

### 2.1 整体框架

论文提出 **A2World 系列模型**，共享同一套预训练权重，分别衍生出两个下游变体：
- **A2World（基础世界模型）**：动作条件的多视角交互扩散世界模型；
- **A2World-sim**：长时序自回归模拟器，用于策略评估与反事实分析；
- **A2World-policy**：视觉—动作联合预测策略。

### 2.2 A2World 基础世界模型

- **建模目标**：给定条件帧 $o_t$ 与未来动作块 $a_{t+1:t+k}$，预测未来观测 $o_{t+1:t+k}$，即 $p(o_{t+1:t+k} \mid o_t, a_{t+1:t+k})$。
- **架构**：DiT 扩散 Transformer（在 WAN2.1 潜空间），采用 EDM 去噪分数匹配目标 $\mathcal{L}_{\text{A2World}}(\sigma) = \mathbb{E}_{z,n}\left[\|A2World(z+n;\sigma,c=0,a)-z\|_2^2\right]$。
- **动作条件注入**：将动作块经 MLP 编码为 $e = \text{MLP}(a)$，并加到扩散时间步嵌入上 $\tilde{\tau}(\sigma) = \tau(\sigma) + e$，用于自适应层归一化（AdaLN）的调制。
- **多视角生成**：将 $V$ 个视角打包到时间维度统一处理；为每个相机引入可学习视角嵌入，并通过 **跨视角注意力模块**（插入到每个 DiT 块中）强制视角间时空一致性。
- **预训练数据**：将所有动作统一为双臂格式（每臂 7 维：末端位姿 + 夹爪状态），单臂零填充；采用**数据集一致的小批量采样策略**，避免不同数据集的相机配置冲突。

### 2.3 A2World-sim 长时序模拟器

- **建模目标**：$p(o_{t+1:t+k} \mid o_t, a_{t+1:t+k}, \mathcal{H}_{t-1})$，其中 $\mathcal{H}_{t-1} = o_{1:t-1}$。
- **位姿引导的历史采样（Alg. 1）**：基于相对动作的加权弧长（位置变化权重 $w_t=1.0$，旋转变化权重 $w_r=0.3$）沿轨迹均匀采样 $m$ 帧，保留关键转折点。
- **历史注入**：① 通过交叉注意力（替换预训练中置零的条件）；② 将历史 token 投影为 K/V 拼接进自注意力记忆路径。
- **自回归生成**：分块自回归方式生成，生成的帧追加到历史缓冲。
- **Self-forcing 训练**：训练中周期性以自身生成帧作为条件（而非真实帧），使模型接触并从自身的累积误差中恢复，无需独立教师模型。

### 2.4 A2World-policy 策略模型

- **建模目标**：$p(o_{t+1:t+k}, a_{t+1:t+k} \mid o_t, l)$，指令 $l$ 经 T5 编码后作为交叉注意力条件。
- **联合扩散**：视频与动作潜变量独立加噪，采用共享基础噪声 $\sigma_{\text{base}}$，按模态缩放 $\sigma_v = \alpha_v \sigma_{\text{base}}$, $\sigma_a = \alpha_a \sigma_{\text{base}}$。
- **MoE 式视频—动作块**：跨模态共享自注意力（"注意力专家"），各模态保留专属 AdaLN 与 MLP 分支。
- **训练目标**：加权联合去噪损失 $\mathcal{L}_{\text{A2World-policy}} = \mathbb{E}[w(\sigma_v)\|\hat{z}_v-z_v\|_2^2 + \lambda_a w(\sigma_a)\|\hat{z}_a-z_a\|_2^2]$。
- **推理引导**：模态独立的 classifier-free guidance，可分别调节视觉保真度与动作精度。

## 3. 实验设计

### 3.1 数据集

| 用途 | 数据集 | 轨迹数 |
|------|--------|--------|
| 预训练 | AgiBot、DROID、OPEN-X、InternData-A1、InternData-M1-Agilex、RoboCoin、Galaxea | 合计 2156k 轨迹 |
| 微调/评估 | LIBERO（6k）、LIBERO-Plus Spatial（3.7k）、RoboNet（100k）、自定义真实机器人数据（2k） | — |

**真实机器人平台**：基于 Flexiv Rizon 4S 双臂 + Robotiq-2F-85 夹爪的类似 TRI 风格平台，含 5 个任务（插入 RAM 模块、翻转小盒、拨动电源开关、高举盒子、把链条放入盒子），覆盖富接触、铰接物体、可形变物体等挑战场景。

### 3.2 Benchmark 与对比方法

- **世界模型评估**：LIBERO、RoboNet、自定义真实机器人数据上的视频预测（FVD、PSNR、SSIM、tSSIM、EPE、cos）；
- **模拟器评估**：LIBERO-Plus Spatial（OOD）；
- **策略评估**：LIBERO（4 套件）、LIBERO-Plus Spatial（OOD）、真实机器人 5 个任务；
- **对比方法**：Cosmos-Predict2、Ctrl-World、Prophet、DreamDojo、Cosmos Policy、π0、π0.5、UniVLA、4D-VLA、Dita、OpenVLA-OFT、CogVLA、FastWAM、X-VLA、GE-Act、LingBot-VA 等近 20 种基线。

## 4. 资源与算力

- **A2World 预训练**：64 块 H200 GPU，每卡 batch size 12，梯度累积 4，训练 2 个 epoch。
- **A2World-sim 微调**：8 块 H200 GPU，每卡 batch size 24。
- **A2World-policy 训练**：32 块 H200 GPU，全局 batch size 256，2 万步（LIBERO 与真实机器人微调）；OOD 评估时微调 2.4 万步。
- **优化器**：融合 Adam，学习率 $1\times 10^{-4}$，权重衰减 0.1。
- **模型规模**：A2World 约 2.5B 参数（基于 Cosmos-Predict2-2B-Video2World 初始化），A2World-policy 约 3.0B 参数。

## 5. 实验数量与充分性

- **基线对比**：覆盖通用视频生成（Cosmos-Predict2）、单数据集机器人世界模型（Ctrl-World）、单视角动作条件世界模型（Prophet）、通用机器人世界模型（DreamDojo）等。
- **消融实验**：
  - 历史采样策略消融（无历史 / 滑动窗口 / 位姿引导）；
  - 预训练变体消融（C-init / T-pre / A-pre / P-pre）；
  - 视频—动作联合学习消融（冻结视频分支 vs 完整联合训练）；
  - 动作保真度（光流 EPE/cos）与视频生成质量（PSNR/SSIM）多维指标对比。
- **OOD 评估**：LIBERO-Plus Spatial 涵盖背景、相机、语言、光照、布局、初始位姿、噪声 7 类扰动。
- **真实机器人评估**：第三方盲评，~25 次真实回放 vs 64 次模拟器回放。
- **充分性**：实验覆盖模拟到真实、单视角到多视角、域内到 OOD、消融到对比，**整体设计较为充分**；但真实机器人任务仅 5 个且为新采集平台，存在一定评估覆盖局限。

## 6. 主要结论与发现

- **动作条件预训练优于文本条件预训练**：A-pre（动作—视频）显著优于 T-pre（文本—视频）和 C-init（Cosmos 直接初始化），原因是动作对未来视觉演化的歧义性更低，能学到更确定的动作—动力学先验。
- **世界模型可作为真实机器人策略评估器**：A2World-sim 的闭环回放成功率与真实成功率呈强相关（Spearman ρ=0.916, Pearson r=0.965, R²=0.930），可替代真实机器人回放进行 what-if 分析。
- **动态先验的双重用途**：同一套预训练权重既可适配为长时序模拟器（A2World-sim），也可适配为指令条件策略（A2World-policy），无需单独的动作专用预训练阶段。
- **视频—动作学习正耦合**：视频预测质量的提升与动作生成质量的提升在训练过程中同步出现；冻结视频分支会导致策略性能大幅下降（98.6% → 86.2%）。
- **动作条件 OOD 模拟器**：在 LIBERO-Plus Spatial 上，A2World-sim 的动作保真度（EPE 0.13）显著优于 DreamDojo（0.27）。
- **策略性能领先**：在 LIBERO 4 套件上平均成功率 98.6%，超过 Cosmos Policy 等强基线；在真实机器人 5 个任务上超越 π0.5 和 LingBot-VA，长时序富接触任务上提升尤为显著。

## 7. 方法与实验设计亮点

- **统一的"动作—动力学先验"视角**：将原本分散在世界模型与策略学习两条路径上的目标统一为同一预训练目标，使预训练权重可"一鱼两吃"。
- **真实动作标注直接监督**：不使用辅助潜动作模型生成伪标签，避免了间接监督带来的迁移损失。
- **数据集一致的小批量采样**：巧妙缓解了跨数据集相机配置冲突，无需对数据集做进一步对齐。
- **位姿引导的弧长历史采样**：基于动作加权弧长选取历史帧，比滑动窗口更能保留关键交互状态。
- **Self-forcing 训练**：无需独立教师模型，直接让模型暴露在自身误差分布下，简化了长时序自回归训练流程。
- **MoE 式视频—动作块**：通过共享自注意力 + 模态专属 AdaLN/MLP 的设计，在最小修改下将视频动力学先验迁移到策略学习。
- **真实机器人平台的第三方盲评**：增强了对真实部署表现的客观性。

## 8. 不足与局限

- **算力投入门槛高**：64 块 H200 预训练 + 32/8 块 H200 微调，对中小研究机构不友好，复现门槛较高。
- **真实机器人任务数量与多样性有限**：仅 5 个任务，集中在双臂对称布置，对更复杂的非对称双臂、移动操作等场景未涉及。
- **评估协议细节未完全披露**：例如 LIBERO 评估的试验次数、真实机器人"进度"的定义被推迟到附录，可能影响跨论文对比的公平性。
- **数据集相机设置差异的处理方式**：仅采用"同批次同数据集"策略缓解冲突，并未从根本上解决跨数据集视觉风格差异，理论上可能限制模型对相机切换的鲁棒性。
- **模拟器与真实之间的残余差距**：尽管 Spearman ρ 较高，论文未给出每任务的逐项误差分解，对失败模式的分析有限。
- **历史采样依赖相对动作**：当真实动作信号缺失或噪声大时（如纯观察数据），位姿引导采样不可用，限制了方法向纯视频数据的延伸。
- **T5 指令编码的依赖**：策略变体依赖固定 T5 编码器，对长或复杂指令的表征能力可能成为瓶颈。
- **未明确讨论安全与部署**：动作条件世界模型理论上可被用于危险动作的反事实评估，但论文未深入讨论其安全应用与潜在滥用风险。

（完）
