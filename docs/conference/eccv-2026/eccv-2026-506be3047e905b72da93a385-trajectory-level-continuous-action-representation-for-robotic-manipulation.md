---
title: Trajectory-Level Continuous Action Representation for Robotic Manipulation
title_zh: CAT：面向机器人操控的轨迹级连续动作表征
authors: "Tong Yang, Jingkai Jia, Yuecheng Xu, Xueyao Chen, Chi Zhang, Wenqiang Zhang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/5247.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向端到端视觉运动操控的轨迹级连续动作表征
tldr: 针对现有视觉运动系统将动作表征与控制频率耦合、依赖固定时间参数化从而在高采样率下产生表征冗余的问题，本文提出了 CAT 轨迹级连续动作表征框架。该方法在固定实时区间内将动作轨迹编码为一组连续潜变量令牌，并引入频率感知位置编码以建立跨控制频率的统一时间坐标系，再通过轨迹级正则化稳定表征。该设计有效避免了表征粒度问题，提升了面向机器人操控的视觉运动策略学习效果。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-506be3047e905b72da93a385/fig-001.webp\", \"caption\": \"\", \"page\": 12, \"index\": 1, \"width\": 927, \"height\": 696}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-506be3047e905b72da93a385/fig-002.webp\", \"caption\": \"\", \"page\": 12, \"index\": 2, \"width\": 927, \"height\": 696}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-506be3047e905b72da93a385/fig-003.webp\", \"caption\": \"\", \"page\": 12, \"index\": 3, \"width\": 927, \"height\": 696}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-506be3047e905b72da93a385/fig-004.webp\", \"caption\": \"\", \"page\": 12, \"index\": 4, \"width\": 927, \"height\": 696}]"
motivation: 现有视觉运动系统的动作表征与控制频率耦合，高采样率下存在表征冗余与粒度问题。
method: 提出轨迹级连续动作表征CAT，将固定实时区间内动作编码为连续潜变量，并引入频率感知位置编码与正则化。
result: 在不同控制频率下显著提升视觉运动策略的稳定性与表征质量。
conclusion: CAT 为端到端视觉运动操控提供了一种统一、稳定的连续动作表征方案。
---

## Abstract
We propose CAT, a trajectory-level continuous action representation framework for robotic manipulation. Existing visuomotor systems often entangle action representation with control frequency or rely on fixed temporal parameterizations. This leads to representational redundancy at high sampling rates and limits the modeling of critical motion. CAT instead encodes action trajectories within a fixed realtime interval into a set of continuous latent tokens. To ensure temporal consistency across varying control frequencies, we further incorporate a frequency-aware positional encoding that establishs a shared temporal coordinate system. Trajectory-level regularization further stabilizes the latent representation. This approach prevents representation growth with timestep density and avoids reliance on predefined temporal parameterizations. Extensive system-level evaluations on LIBERO, MimicGen, and real-world long-horizon manipulation tasks demonstrate that CATbased policies consistently outperform both competitive VQ-based and continuous visuomotor baselines under matched training settings. Across various model backbones and control frequencies, CAT consistently improves success rates. These results highlight the advantages of trajectorylevel continuous action modeling for scalable robotic manipulation across varying control rates.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "CAT: Trajectory-Level Continuous Action Representation for Robotic Manipulation" following 8 specific points. Let me organize the content carefully based on the paper provided.

Let me analyze each section:

1. **Core Problem**: Existing visuomotor systems couple action representation with control frequency or rely on fixed temporal parameterizations (DCT, B-spline, VQ), leading to representational redundancy at high sampling rates and inability to model critical motion.

2. **Method**: CAT encodes action trajectories within fixed real-time interval (T=1s) into K continuous latent tokens. Key components:
   - Frequency-aware Transformer encoder with F-RoPE
   - Asymmetric causal decoder
   - Reconstruction loss + contrastive regularization
   - Integrated with flow matching diffusion VLA

3. **Experiments**:
   - LIBERO (Spatial, Object, Goal, Long)
   - MimicGen (8 tasks)
   - RoboTwin 2.0 (frequency evaluation, 8 tasks, 10/16.7/25/50Hz)
   - Real-world: 4 long-horizon tasks (Stack-5, Drawer, Rope, Flower)
   - Baselines: Octo, OpenVLA, SmolVLA variants, FAST, VQ-VLA, π0, Diffusion Policy, 4D-VLA, CogACT, OmniSAT, TCD, SDP, CARP

4. **Resources**: Not explicitly mentioned in paper

5. **Experiment quantity**: Multiple benchmarks, ablation studies (PE type, K, λreg, attention type), controlled comparisons

6. **Conclusions**: CAT consistently improves policy performance across simulation and real-world, robust to varying control frequencies

7. **Strengths**: Decoupling from timestep grid, fixed token budget across frequencies, frequency-aware positional encoding, contrastive regularization

8. **Limitations**: Limited frequency range tested, only SmolVLA and π0 backbones, real-world only 100 demos per task, single robot arm (ARX R5)

Let me write a comprehensive structured summary in Chinese.</think>

# CAT：面向机器人操控的轨迹级连续动作表征 — 论文总结

## 1. 核心问题与研究动机

- **问题定义**：在视觉运动策略（visuomotor policy）学习中，动作轨迹对任务成败的影响在时间维度上分布不均——只有接触过渡、空闲-接触切换、关键纠错等"局部关键段"对任务结果至关重要，其余多为平滑重复运动。
- **现有方法的局限**：
  - **时间步级离散化**（如 RT-1/RT-2、Octo）：表征单元数量与时间网格绑定，高采样率下轨迹长度膨胀，引入表征冗余；
  - **固定时间重参数化**（如 FAST 的 DCT 系数、B-spline 控制点）：表征规模虽然不随频率增长，但结构被预先选定的基函数约束，限制了建模灵活性；
  - **VQ 离散化**（如 FAST、VQ-VLA、CARP）：依赖离散码本，损失了连续动作中的精细结构信息；
  - **频域方法**（如 FreqPolicy）：仍依赖预定义的频谱基。
- **核心诉求**：希望动作表征既能保持固定规模的表征预算（不随采样频率膨胀），又摆脱对预定义时间基的依赖，从而在不同控制频率下保持稳定一致。

## 2. 方法论

### 2.1 核心思想
CAT（Continuous Action Trajectory）将固定实时窗口（T = 1 s）内的动作轨迹编码为 **K 个连续的潜在令牌（latent tokens）**，K 固定且不随控制频率变化，并通过频率感知位置编码（F-RoPE）在不同采样率之间建立统一的时间坐标系。

### 2.2 关键模块
- **结构解耦（Structural Decoupling）**：
  - 输入动作序列 $\{a_t\}_{t=1}^{N}$（其中 $N = f_s T$），编码为 $K \ll N$ 个 register token $\{z_i\}_{i=1}^{K}$；
  - Transformer 编码器通过 register token 聚合整条轨迹信息；
  - 解码器采用 **不对称因果掩码**：所有 action embedding 可看到全部 register token，但 action embedding 之间仅因果注意力，保证时序因果性。

- **频率对齐（Frequency Alignment）—— F-RoPE**：
  - 对时间索引 $t$ 按控制频率 $f_s$ 归一化为 $t/f_s$；
  - 旋转位置编码定义为 $\text{F-RoPE}(t/f_s) = [\sin(\omega_i t/f_s), \cos(\omega_i t/f_s)]_{i=1}^{d/2}$；
  - 注入到 Transformer 的 query/key 中，使不同控制频率下的轨迹在共享时间空间中可比。

- **潜在稳定性（Latent Stability）**：
  - **重建损失**：$L_{\text{rec}} = \frac{1}{N}\sum_t \|a_t - \hat{a}_t\|_2^2$
  - **轨迹级对比正则化**：将所有 register token 拼接得到轨迹嵌入 $\bar{z}$，通过负样本对的指数距离惩罚推动不同语义轨迹在潜空间中分离：
    $$L_{\text{reg}} = \frac{1}{B}\sum_i \log\sum_{j \ne i}\exp\left(\frac{-D(\bar{z}_i, \bar{z}_j)}{\eta}\right)$$
  - **总损失**：$L_{\text{CAT}} = L_{\text{rec}} + \lambda_{\text{reg}} L_{\text{reg}}$

### 2.3 与扩散式 VLA 集成
- CAT 输出替换原始 timestep 级动作参数化，作为紧凑潜空间供 flow-matching 策略使用；
- 扩散模型在潜空间 $\{Z_\tau\}$ 上学习连续流：$Z_\tau = (1-\tau)Z_0 + \tau Z_1$，预测速度场 $v_\psi(Z_\tau, \tau, c)$；
- 推理时由扩散模型生成潜轨迹，解码回连续动作，控制频率作为条件信号保留。

## 3. 实验设计

### 3.1 数据集 / Benchmark
- **LIBERO**：4 个子任务集（Spatial / Object / Goal / Long），用于标准视觉运动策略评估。
- **MimicGen**：基于 Robomimic 的 8 个多任务操控任务，用于多任务模仿学习。
- **RoboTwin 2.0（Easy split）**：被重用作多频率评估平台，覆盖 8 个任务、4 个控制频率（10 / 16.7 / 25 / 50 Hz）。
- **真实机器人**：ARX R5 机械臂 + 1 个第三人称相机 + 1 个腕部相机，4 个长时任务（Stack-5、Drawer、Rope、Flower），每任务 100 条遥操作演示。

### 3.2 对比方法
- **LIBERO**（同类对比）：SmolVLA、SmolVLA-FAST、SmolVLA-VQ-VLA、π0、π0-FAST、Octo、OpenVLA、Diffusion Policy、4D-VLA、CogACT、OmniSAT；
- **MimicGen**：TCD、SDP、CARP、Diffusion Policy（flow-matching 变体 DP）、DP-CAT；
- **RoboTwin 2.0**：仅与同骨干 SmolVLA 基线对比（控制变量）；
- **真实世界**：仅与 SmolVLA 基线对比。

## 4. 资源与算力

- 论文**未明确披露**训练所用 GPU 型号、数量、训练时长等算力信息；
- 仅给出训练步数：仿真中 LIBERO 训练按标准流程，真实世界任务中 SmolVLA 训练 180k 步，CAT 在 Open X-Embodiment 上预训练后再针对目标任务微调 1k 步；
- 这一信息缺口使得复现成本难以评估。

## 5. 实验数量与充分性

- **实验规模**：
  - LIBERO 上 3 个对比族 × 4 子任务集；
  - MimicGen 上 8 个任务 × 5 种方法对比；
  - RoboTwin 2.0 上 8 任务 × 4 频率 × 2 方法 = 64 个 (任务-频率) 单元；
  - 真实世界 4 个长时任务 × 10 次评估；
- **消融实验**（均基于 LIBERO）：
  - 位置编码类型（F-RoPE vs Learned PE，含 RoboTwin 2.0 验证）；
  - register 数量 $K \in \{2,4,6,8\}$；
  - 正则化权重 $\lambda_{\text{reg}} \in \{0,0.1,0.2,0.3\}$；
  - 解码器注意力类型（Causal vs Full）。
- **公平性**：
  - LIBERO 与 MimicGen 严格控制骨干、数据集、预处理、训练流程，仅改变动作表征；
  - RoboTwin 2.0 采用统一数据集训练，频率作为唯一变量；
  - 提供了 controlled comparison（SmolVLA-CAT）与 reference comparison（其他系统）两层证据。
- **充分性评价**：
  - 多频率鲁棒性实验覆盖了较广范围（10–50 Hz），但未涉及更极端设置（>50 Hz 或 <10 Hz）；
  - 真实世界任务数量有限（4 个），每任务演示仅 100 条，泛化性证据相对薄弱；
  - 真实世界仅与单一基线（SmolVLA）对比，缺少更多基线的对比。

## 6. 主要结论与发现

- **整体提升**：CAT 在 LIBERO、MimicGen、RoboTwin 2.0、真实世界任务上一致优于时间步级连续基线与 VQ 基线；
- **跨模型泛化**：将 π0 的动作表征替换为 CAT 后，LIBERO 平均成功率由 94.2% → 96.5%；
- **跨骨干一致**：SmolVLA-CAT 在 SmolVLA 上实现 +3.5 平均增益，且优于 FAST/VQ-VLA 变体；
- **频率鲁棒**：在 10/16.7/25/50 Hz 四个频率下，SmolVLA-CAT 在 24/32 个 (任务-频率) 对上胜出，平均提升 +5.3 ~ +10.3 点；
- **任务特性关联**：提升在涉及短促关键交互转换的任务上更显著（Grab Roller +18.5、Press Stapler +16.0、Stack 3 +9），平滑任务增益较小；
- **真实世界**：长时任务平均得分由 45.0 → 60.5，四个任务全部正向提升（Flower +28 尤为突出）；
- **消融结论**：
  - F-RoPE 优于 Learned PE，多频率场景优势更明显；
  - $K=4$ 为最佳（增加 $K$ 至 6/8 反而下降）；
  - $\lambda_{\text{reg}}=0.1$ 最优；
  - 解码器因果注意力优于全注意力（+2.25 平均）。

## 7. 优点与亮点

- **思路清晰**：从"动作表征与控制频率耦合"这一具体问题出发，给出"结构解耦 + 频率对齐 + 潜在稳定性"的层次化设计；
- **无预定义时间基**：相比 FAST（依赖 DCT）、FreqPolicy（依赖频谱基），CAT 完全数据驱动，灵活度更高；
- **跨骨干兼容**：作为表征模块可即插即用到 π0、SmolVLA 等不同 VLA；
- **多频率鲁棒性**：在 4 个不同采样率上系统验证，提供实证支撑；
- **真实世界验证**：包含长时序、铰接物体、可形变物体的真实任务，而非纯仿真；
- **消融较为完整**：从位置编码、容量、正则化、注意力四个维度逐项验证。

## 8. 不足与局限

- **算力与训练成本未披露**：GPU 型号、数量、训练时长等关键信息缺失，影响复现性评估；
- **真实世界规模有限**：仅 4 个任务、每任务 100 条演示、单一机器人平台（ARX R5），对结论的泛化性支撑不够充分；
- **频率范围有限**：仅测试 10–50 Hz，未覆盖更低（如 5 Hz）或更高（如 100+ Hz）的极端控制频率；
- **基线覆盖不均**：
  - LIBERO 提供了广基线对比，但仅 SmolVLA 与 π0 做了严格 controlled comparison；
  - 真实世界仅与 SmolVLA 单基线对比，缺少与 FAST、π0 等的同条件对比；
- **应用范围限制**：
  - 论文评估限定在桌面级单臂操控，未涉及双臂、移动操作等场景；
  - 真实世界均为视觉简单背景下的实验室环境，复杂视觉干扰未测试；
- **方法假设**：固定实时窗口 T=1 s 是手工设定，未探讨不同 T 对效果的影响；
- **潜在偏差风险**：消融均基于 LIBERO 单一基准，可能未完全揭示在其他基准上的最优配置（如 $K$、$\lambda_{\text{reg}}$ 是否需重新调参）。

（完）
