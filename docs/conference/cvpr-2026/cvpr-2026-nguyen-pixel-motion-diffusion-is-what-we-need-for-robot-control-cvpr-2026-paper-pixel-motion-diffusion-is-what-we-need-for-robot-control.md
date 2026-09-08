---
title: Pixel Motion Diffusion is What We Need for Robot Control
title_zh: 像素运动扩散：机器人控制所需的关键表示
authors: "Nguyen, E-Ro, Zhang, Yichi, Ranasinghe, Kanchana, Li, Xiang, Ryoo, Michael S."
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Nguyen_Pixel_Motion_Diffusion_is_What_We_Need_for_Robot_Control_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 在CALVIN基准上达到SOTA的扩散式视觉运动策略，验证语言条件操作
tldr: 针对语言条件机器人操作中高层意图与底层动作的衔接难题，本文提出基于像素运动的统一扩散框架DAWN，将高低层控制器均建模为扩散过程，实现端到端可训练系统。方法在CALVIN基准上取得多任务SOTA，并在MetaWorld上进一步验证。真实机器人实验表明其以极少的微调即可完成可靠的仿真到现实迁移。该工作显著推动了基于扩散模型的视觉运动模仿学习前沿。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1538, \"height\": 704, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 792, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 758, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 783, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1645, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1506, \"height\": 733, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1702, \"height\": 548, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 891, \"height\": 351, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1800, \"height\": 194, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 598, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nguyen-pixel-motion-diffusion-is-what-we-need-for-robot-control-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 493, \"height\": 554, \"label\": \"Table\"}]"
motivation: 语言条件机器人操作需要在高层意图与底层动作之间建立可解释桥梁。
method: 提出基于像素运动表示的统一扩散框架DAWN，端到端建模高层与低层控制器。
result: 在CALVIN基准上达到SOTA，并在MetaWorld和真实机器人上验证迁移能力。
conclusion: 该工作证明了扩散模型作为通用机器人操作策略骨干的潜力。
---

## Abstract
We present DAWN (Diffusion is All We Need for robot control), a unified diffusion-based framework for language-conditioned robotic manipulation that bridges high-level motion intent and low-level robot action via structured pixel motion representation. In DAWN, both the high-level and low-level controllers are modeled as diffusion processes, yielding a fully trainable, end-to-end system with interpretable intermediate motion abstractions. DAWN achieves state-of-the-art results on the challenging CALVIN benchmark, demonstrating strong multi-task performance, and further validates its effectiveness on MetaWorld. Despite the substantial domain gap between simulation and reality and limited real-world data, we demonstrate reliable real-world transfer with only minimal finetuning, illustrating the practical viability of diffusion-based motion abstractions for robotic control. Our results show the effectiveness of combining diffusion modeling with motion-centric representations as a strong baseline for scalable and robust robot learning.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Pixel Motion Diffusion is What We Need for Robot Control" (DAWN). Let me analyze the paper carefully and produce a structured summary covering all 8 required points.

Let me go through each section systematically:

1. **Core problem and motivation**: Language-conditioned robot manipulation needs to bridge high-level motion intent with low-level robot actions. Existing methods either use VLA (vision-language-action) models that directly map observations to actions, or use multi-stage pixel/point tracking, or predict future RGB frames. Each has limitations - VLA lacks interpretability, tracking methods need additional components, RGB prediction is overly complex.

2. **Method**: DAWN is a two-stage diffusion framework:
   - Motion Director: A latent diffusion model that generates dense pixel motion representations conditioned on visual observations and language
   - Action Expert: A diffusion-based policy that translates pixel motions to robot actions
   - Key technical details:
     - Pixel motion F_{t,k} = [u, v] is encoded as 3-channel image F' = [u, v, (u+v)/2]
     - Motion Director uses U-Net denoiser, text encoder, VAE encoder/decoder, vision encoder
     - Denoising happens in latent space
     - Action Expert uses transformer denoiser with ConvNeXt-S (DINOv3), T5-small encoders
     - Both trained with MSE noise estimation loss
     - Ground truth pixel motion from RAFT optical flow

3. **Experiments**:
   - CALVIN (ABC→D setting) - language-conditioned long-horizon manipulation
   - MetaWorld - 11 challenging tasks
   - Real-world: xArm7 single-arm (1000 episodes, 6 toys, 12 tasks)
   - Bimanual: Galaxea R1-Lite (100+ hours, 9 bimanual tasks)
   - Baselines: Diffusion Policy, Robo-Flamingo, Moto, MoDE, RoboUniview, Seer, VPP, Enhanced DP, π0, Gen2Act, AVDC, LTM, etc.

4. **Compute**: Not explicitly mentioned in the paper text I have. I should note this.

5. **Number of experiments and sufficiency**: 
   - Multiple benchmarks (CALVIN, MetaWorld, real-world, bimanual)
   - Ablation studies on: pixel motion vs RGB goal, gripper view, diffusion steps
   - Fair comparison following standard protocols

6. **Main conclusions**:
   - SOTA on CALVIN
   - Best performance on MetaWorld (65.4% overall vs 57.7% for LTM)
   - Best real-world single-arm performance
   - Lower MSE on bimanual task
   - Pixel motion is a structured, interpretable intermediate representation

7. **Highlights**:
   - Two-stage fully diffusion-based architecture
   - Leverages pretrained models effectively
   - Data-efficient
   - Modular and interpretable
   - Bridges hierarchical motion and end-to-end agents

8. **Limitations**:
   - Higher inference time due to two-stage design (319.82ms vs VPP's 190.55ms)
   - Limited to 1000 episodes in real-world
   - Only tested on specific camera configurations
   - Pixel motion assumes access to ground-truth optical flow during training (RAFT)
   - Tested on relatively small set of real-world tasks

Let me write this in Chinese, organized with Markdown.</think>

# DAWN：像素运动扩散驱动的机器人控制框架

## 1. 核心问题与研究动机

- **研究背景**：语言条件下的机器人操作需要建立高层语义意图（如"整理沙发靠垫"）与底层连续动作之间的桥梁。
- **现有方法的不足**：
  - **VLA（视觉-语言-动作）模型**（RT-2、OpenVLA、π0 等）：直接由观测映射到动作，缺乏可解释的中间表征；
  - **多阶段点轨迹/光流跟踪方法**（Gen2Act、Track2Act、Im2Flow2Act 等）：通常依赖稀疏轨迹，依赖额外的目标检测器或关键点选择机制；
  - **未来 RGB 帧预测方法**（UniPi、SuSIE、VidMan、VPP 等）：在 RGB 空间中操作，问题复杂且冗余。
- **核心问题**：能否在不依赖 RGB 视频生成的条件下，直接预测稠密像素运动作为高层意图与底层动作之间的结构化接口？

## 2. 方法论

### 2.1 整体框架（DAWN）

DAWN（Diffusion is All We Need for robot control）是一种两级全扩散（fully diffusion）的视觉运动框架：

- **高层——Motion Director（运动导演）**：基于潜空间扩散模型，根据多视角图像与语言指令直接生成稠密像素运动场；
- **低层——Action Expert（动作专家）**：基于 Transformer 的扩散策略，将像素运动转化为可执行机器人动作序列。

### 2.2 像素运动表示

- 定义从 $I_t$ 到 $I_{t+k}$ 的像素运动 $F_{t,k} = [u, v]$，其中 $u, v \in \mathbb{R}^{H\times W}$ 分别表示像素在水平/垂直方向的位移；
- 为利用预训练图像扩散模型，将其编码为三通道图像 $F'_{t,k} = [u, v, (u+v)/2]$；
- 训练时使用 **RAFT** 光流模型从 $I_t$ 与 $I_{t+k}$ 提取真实像素运动。

### 2.3 Motion Director

- 初始化自预训练潜空间扩散模型（Stable Diffusion v1.5 系列），包含 U-Net 去噪器 $U_M$、文本编码器 $T_M$、VAE 编解码器 $(V_M^E, V_M^D)$；
- 引入额外视觉编码器 $E_M$ 处理另一相机视角；
- 推理时流程：
  1. 采样高斯噪声 $N_{M,n}$，与 $V_M^E(I_t)$ 在通道维度拼接形成 $O_{M,n} = [N_{M,n}, V_M^E(I_t)]$；
  2. 条件向量 $C_M = [E_M(G_t), T_M(L), k]$ 经交叉注意力注入 U-Net；
  3. 经 $n$ 步去噪后由 VAE 解码为三通道像素运动图像；
- 训练时仅微调 U-Net，其余模块冻结。

### 2.4 Action Expert

- 四模块组成：
  1. **视觉编码器 $V_A$**：基于 DINOv3 的 ConvNeXt-S，冻结；
  2. **文本编码器 $T_A$**：T5-small，冻结；
  3. **状态编码器 $S_A$**：两层 MLP，从零训练；
  4. **去噪 Transformer $U_A$**：从零训练，用于生成动作序列；
- 多模态 token 经拼接后通过交叉注意力注入每个 Transformer 块；
- 从高斯先验出发迭代去噪，输出长度为 $h$ 的动作块。

### 2.5 训练与推理

- 两模块均使用 **MSE 噪声估计损失**；
- 两模块可**并行训练**，且可独立升级；Action Expert 可在 Motion Director 真实输出上做可选微调；
- 推理时形成**闭环控制**：执行完动作后重新观测，循环往复。

## 3. 实验设计

### 3.1 数据集与基准

- **CALVIN**（ABC→D 零样本长时序设置）：A/B/C 环境训练，D 环境评估；
- **MetaWorld**（11 个挑战性任务：开关门、投篮、装配等，使用 AVDC/LTM 数据划分）；
- **真实单臂平台**：xArm7 7-DoF + 两路 RGB 相机（静态 + 腕部），1000 条示教，6 类玩具/容器，12 个任务；
- **真实双臂平台**：Galaxea R1-Lite（双臂 + 头部相机 + 双腕相机），来自 Galaxea Open-World Dataset 的 100+ 小时数据，9 种双臂任务。

### 3.2 对比方法

- **CALVIN 无外部数据**：Diffusion Policy、Robo-Flamingo、Moto、MoDE、RoboUniview、Seer/Seer-Large、VPP；
- **CALVIN 有外部数据**：GR-1、VidMan、LTM、Seer、MoDE、VPP、DreamVLA；
- **MetaWorld**：BC-Scratch、BC-R3M、Diffusion Policy、UniPi、Im2Flow2Act、ATM、AVDC、LTM；
- **真实单臂**：Enhanced DP（无 Motion Director 的 Action Expert 变体）、π0（LoRA 微调）、VPP；
- **双臂**：Enhanced Diffusion Policy 基线。

### 3.3 主要结果

| 设置 | 关键结果 |
|------|---------|
| CALVIN（无外部数据） | DAWN Avg.Len = **4.00**，超过 VPP（3.93）和 Seer-Large（3.83），任务1成功率 0.98 |
| CALVIN（含 DROID 数据） | DAWN Avg.Len = 4.10，与 VPP（4.33）、DreamVLA（4.44）相当，但用数据更少 |
| MetaWorld | 总体成功率 **65.4%** vs LTM 57.7%，对"开门 vs 关门"等语义相似任务区分能力显著提升 |
| 真实单臂 | 6 种水果平均成功率高，每类"错误抓取"几乎为 0，显著优于 π0、VPP |
| 双臂 Galaxea | 动作预测 MSE = **0.117** vs Enhanced DP 0.128 |

### 3.4 消融实验

- **像素运动 vs RGB 目标 vs 无中间表征**：像素运动最优（4.00 vs 3.21 vs 2.78）；从零训练 U-Net 也降至 3.42，证明预训练价值；
- **腕部视角条件**：加入后 4.00，去除后 3.74；VPP 同样去腕部时为 3.58；
- **去噪步数**：2 步即可达 3.88，25 步最优（4.00），40 步反而略降（3.95）。

## 4. 资源与算力

- 论文正文中**未明确披露**所用 GPU 型号、数量及训练时长。
- 仅可推断的工程信息：
  - 推理时 Motion Director 使用 **25 步去噪**生成像素运动；
  - 真实单臂实验中所有方法统一微调 **100k 步**；
  - 推理延迟：Enhanced DP 112.77 ms、VPP 190.55 ms、DAWN 319.82 ms（每动作块）。
- **建议**：复现时需参考附录或代码仓库才能获取完整硬件配置。

## 5. 实验数量与充分性

- **多基准验证**：覆盖仿真（CALVIN + MetaWorld）、真实单臂、真实双臂四个场景；
- **消融维度齐全**：表征形式（像素运动/RGB/无）、条件输入（腕部视角）、去噪步数均有对比；
- **公平性**：
  - CALVIN 严格按 [16, 29] 协议评估，基线结果直接引用；
  - MetaWorld 采用 AVDC/LTM 公开数据划分；
  - 真实单臂统一 100k 步微调、20 episode/任务的随机初始化；
- **充分性**：实验覆盖较完整，但部分表格（特别是 CALVIN 含外部数据）DAWN 仅与 SOTA 接近而非全面超越，且真实世界仅 1000 episode（12 任务），数据规模较小。

## 6. 主要结论与发现

1. **像素运动可作为高效中间表征**：相比 RGB 帧预测，更简洁、更易学习，且具备可解释性；
2. **两级全扩散架构可行**：高层（Motion Director）与低层（Action Expert）均建模为扩散过程，可端到端训练；
3. **强数据效率**：在数据量远少于 VPP/DreamVLA 的情况下仍达到 CALVIN 上的 SOTA；
4. **预训练模型价值显著**：将预训练图像扩散模型改造为像素运动生成器比从零训练效果更好；
5. **具备仿真到真实迁移能力**：仅用 1000 条真实 episode + 100k 步微调即可在多类抓放任务上稳定超越 π0、VPP。

## 7. 优点与亮点

- **结构化中间表征**：稠密像素运动既是高层意图的具体化，又直接对接 Action Expert，避免 RGB 空间中的高复杂度；
- **可解释性**：像素运动可视化便于分析失败原因（论文展示了"lift the apple"的中间结果）；
- **模块化与可升级**：Motion Director 与 Action Expert 可独立训练/替换；
- **充分利用预训练**：继承 Stable Diffusion、DINOv3、T5、CLIP 等大模型先验，避免从零训练；
- **跨域泛化**：在仿真、单臂、双臂、跨 sim-to-real 均验证有效；
- **语义区分能力增强**：在视觉相似但语义相反的任务（开门/关门）上大幅领先；
- **闭环频率仍实用**：319.82 ms 的推理时延在闭环控制中仍可接受。

## 8. 不足与局限

- **算力信息不透明**：未披露 GPU 型号/数量/总训练时长，影响复现成本评估；
- **推理延迟较高**：相比 Enhanced DP（112.77 ms）与 VPP（190.55 ms），DAWN 接近 320 ms 的两阶段串行推理开销明显；
- **真实世界数据规模有限**：单臂仅 1000 episode/12 任务，双臂仅以 MSE 评估未做实机成功率；
- **训练依赖光流真值**：需用 RAFT 离线生成像素运动，限制了在缺乏前后帧对的场景的扩展；
- **任务多样性偏窄**：CALVIN 与 MetaWorld 均为桌面级操作；未覆盖移动操作、柔性物体、长时序导航等场景；
- **双臂评估不充分**：仅报告测试集 MSE，未提供实机成功率与定性 rollout 的系统分析；
- **跨数据集偏差风险**：不同基准的 baseline 来源不同，公平性受限于第三方报告数据；
- **失败模式分析较简略**：仅展示代表性失败案例，缺乏对错误抓取/语义混淆的系统性诊断。

（完）
