---
title: "EmbodiedVAE: Disentangled Video VAE for Efficient and Controllable Embodied Manipulation"
title_zh: EmbodiedVAE：面向高效可控具身操纵的解耦视频VAE
authors: "Jiayi Luo, Hanxin Zhu, Chen Gao, Jiankun Wang, Cong Wang, Tianyu He, Jianxin Li, Zhibo Chen"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/2922.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向具身操纵世界模型的视频VAE，支持精确机器人控制
tldr: 潜在扩散模型在构建强大具身操纵世界模型方面取得了显著进展，但现有模型主要依赖针对自然场景优化的变分自编码器，未考虑具身操纵场景的独有特性，导致潜空间表示既不紧凑也不可控，阻碍了潜在扩散模型的高效训练和精确机器人控制。本文提出EmbodiedVAE，一种专为机器人操纵世界模型设计的视频VAE，提供紧凑且可控的潜空间表示。该工作虽然不直接涉及模仿学习或VLA模型，但作为使能方法，为基于视觉的机器人操纵控制与世界模型构建提供了关键基础组件。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-001.webp\", \"caption\": \"\", \"page\": 4, \"index\": 1, \"width\": 624, \"height\": 604}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-002.webp\", \"caption\": \"\", \"page\": 4, \"index\": 2, \"width\": 335, \"height\": 1118}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-003.webp\", \"caption\": \"\", \"page\": 4, \"index\": 3, \"width\": 335, \"height\": 1118}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-004.webp\", \"caption\": \"\", \"page\": 4, \"index\": 4, \"width\": 629, \"height\": 507}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-005.webp\", \"caption\": \"\", \"page\": 4, \"index\": 5, \"width\": 629, \"height\": 506}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-006.webp\", \"caption\": \"\", \"page\": 4, \"index\": 6, \"width\": 2727, \"height\": 366}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-007.webp\", \"caption\": \"\", \"page\": 4, \"index\": 7, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-008.webp\", \"caption\": \"\", \"page\": 4, \"index\": 8, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-009.webp\", \"caption\": \"\", \"page\": 4, \"index\": 9, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-90a9de29638094feae0a4b46/fig-010.webp\", \"caption\": \"\", \"page\": 4, \"index\": 10, \"width\": 624, \"height\": 604}]"
motivation: 现有面向自然场景优化的VAE在具身操纵场景中产生的潜表示既不紧凑也不可控，阻碍了世界模型的高效训练和精确机器人控制。
method: 提出EmbodiedVAE，一种专为机器人操纵世界模型设计的解耦视频VAE，提供紧凑且可控的潜表示。
result: 为潜在扩散模型在具身操纵世界模型训练中提供了更高效可控的表示。
conclusion: 为具身操纵中的世界模型构建与机器人控制提供了关键的使能组件。
---

## Abstract
Latent diffusion models (LDMs) have recently significantlyadvanced embodied learning in constructing powerful embodied manipu-lation world models. However, despite the remarkable performance, exist-ing LDMs predominantly rely on Variational Autoencoders (VAEs) opti-mized for natural scenes while failing to account for the unique character-istics of embodied manipulation scenarios, yielding latent representationsthat are neither compact nor controllable, thereby hindering efficienttraining of LDMs and precise robotic control. To solve this problem, wepresent EmbodiedVAE, a novel video VAE that provides compact yetcontrollable latent representations tailored for the robotic manipulationworld models. Specifically, EmbodiedVAE adopts a dual-encoder, single-decoder architecture with an asymmetric spatio-temporal compressionmodule, which automatically disentangles the robot arm’s motion frombackground environment, resulting in overall compactness while provid-ing explicit embodied latent to support fine-grained action control. Tofurther preserve the temporal consistency of learned robotic motion la-tent, we introduce an optimal-transport-based consistency module thatexplicitly enforces motion fidelity and inter-frame coherence. Extensiveexperiments demonstrate that our proposed EmbodiedVAE achieves su-perior reconstruction quality with high compression rate, while enablingmore precise action control in robotic manipulation scenarios with anaverage of 2dB PSNR improvement over state-of-the-art video VAEs.Code is available at: https://github.com/Mutual-Luo/EmbodiedVAE

---

## 论文详细总结（自动生成）

<think>The user wants a structured Chinese summary of the paper "EmbodiedVAE: Disentangled Video VAE for Efficient and Controllable Embodied Manipulation". Let me analyze the paper content carefully and produce a detailed summary following the 8 required points.

Let me extract key information from the paper:

1. **Core Problem**: Existing LDMs use VAEs optimized for natural scenes, not accounting for unique characteristics of embodied manipulation. The latents are neither compact nor controllable, hindering efficient LDM training and precise robotic control.

2. **Method**: EmbodiedVAE with:
   - Dual-encoder, single-decoder architecture
   - Asymmetric spatio-temporal compression (Robotic arm: 4× temporal, 16×16 spatial; Environment: 8× temporal, 8×8 spatial)
   - Two-stage training (first stage: train two encoders with masks; second stage: train unified decoder without masks)
   - OT-based motion consistency loss using Sinkhorn-Knopp algorithm
   - Disentanglement of robot motion from background
   - Compression rate of 0.39%

3. **Experiments**:
   - Datasets: Training on ~1M videos aggregated from RobNet, RobSet, BC-Z, RH20T, DROID
   - Evaluation: Agibot-2025, Bridge for VAE reconstruction; RT-1, Bridge for action-conditioned generation
   - Baselines: OpenSoraPlan, Cosmos, iVideoGPT, MAGVIT-v2, VidTwin, EMU-3, CV-VAE, CMD, Wan-VAE, Cog-VAE, SDXL
   - Metrics: PSNR, SSIM, LPIPS, FVD, compression rate

4. **Resources**:
   - Trained on 8 NVIDIA A800 GPUs (one section says 16 A800 GPUs in appendix)
   - 8 fps, 16-frame, 256×256 videos
   - Training duration not explicitly stated

5. **Experiment quantity**:
   - Table 1: Reconstruction comparison on 2 datasets with 4 metrics
   - Table 2: Action-controlled generation comparison
   - Table 3: Ablation studies (w/o Mask, w/o Lmotion)
   - Disentanglement analysis (Figure 5)
   - Efficiency analysis (Figure 6)
   - Multiple qualitative comparisons

6. **Main conclusions**:
   - Superior reconstruction quality with high compression
   - More accurate action control
   - ~2dB PSNR improvement over SOTA

7. **Strengths**: 
   - Novel disentanglement approach
   - OT-based motion consistency with theoretical foundation (Proposition 1)
   - Asymmetric compression tailored to embodied scenarios
   - Two-stage training with mask-free inference

8. **Limitations**:
   - Relies on pre-trained SAM2 + Grounding DINO for mask generation during training
   - OT module computational overhead (though acceptable)
   - Limited to robotic arm manipulation scenarios
   - Trained on limited datasets

Let me write this in Chinese, organized by the 8 required points.</think>

# EmbodiedVAE 论文总结

## 1. 核心问题与研究背景

- **研究对象**：基于潜在扩散模型（LDM）的具身操纵世界模型（embodied manipulation world models），用于预测机器人在给定动作条件下的未来交互。
- **核心问题**：现有 LDM 主要依赖面向自然场景优化的 VAE（无论是 2D 图像 VAE 还是通用视频 VAE），无法兼顾具身操纵场景的两个关键特性：
  - **紧凑性不足**：2D 图像 VAE 逐帧压缩，未利用帧间冗余，导致潜空间过大、训练效率低；
  - **可控性不足**：现有视频 VAE 通过时空压缩获得紧凑潜空间，但时序压缩往往**损失了机器人动作语义**，难以进行精确动作控制。
- **研究意义**：为具身操纵世界模型提供既紧凑又可控的潜表示，是实现高效训练与精确机器人控制的关键使能组件。

## 2. 方法论

### 2.1 整体架构

- **双编码器、单解码器（Dual-Encoder, Single-Decoder）**：将输入视频自动解耦为机器人手臂运动潜表示和环境上下文潜表示。
- **非对称时空压缩**：
  - **机器人手臂编码器**（前景）：由于手臂在画面中占比小但关键，采用较强空间压缩——时间下采样 4×、空间下采样 16×16、潜通道 4；
  - **环境上下文编码器**（背景）：利用第一人称视角下背景的高时间冗余，采用较强时间压缩——时间下采样 8×、空间下采样 8×8、潜通道 4；
  - 两个潜表示共同输入统一解码器重建完整视频，总压缩率约 **0.39%**。

### 2.2 两阶段训练策略

- **第一阶段**：训练两个独立 VAE（机器人分支 + 环境分支），使用 SAM2 + Grounding DINO 生成的机械臂掩码作为辅助监督，使两个分支分别专注于运动信息与环境信息。
  - 机器人分支损失：`L_arm = L_rec + α·L_motion + β·L_KL + λ·L_aux`，其中 `L_rec` 仅在掩码区域计算；
  - 环境分支损失：`L_env = L_rec + β·L_KL + λ·L_aux`，其中 `L_rec` 仅在掩码外区域计算。
- **第二阶段**：冻结两个编码器，丢弃各自的解码器，仅训练统一解码器，损失为完整视频上的重建损失（无掩码）。
- **关键特性**：推理阶段**不需要任何掩码输入**，可自动完成解耦。

### 2.3 OT-based 运动一致性模块

- **核心思想**：稳定运动在帧间应保持视觉对应一致性，利用**最优传输（Optimal Transport, OT）** 显式约束潜空间中的时序稳定性。
- **数学表述**：
  - 用离散概率分布 `μ_p = Σ a_i δ_{x_i}`、`μ_q = Σ b_j δ_{y_j}` 表示第 `t_p` 和 `t_q` 帧的潜表示分布；
  - 传输代价定义为负余弦相似度：`c(i,j) = -S_{i,j} = ⟨Z_p[i], Z_q[j]⟩/√d`；
  - 使用 Sinkhorn-Knopp 算法求解**熵正则化 OT**（`ε` 控制正则化强度）；
  - **运动一致性损失**：`L_motion = (1/N) Σ_{p, q=p..p+Δ} ‖Z_q - T_{p→q} Z_p‖ + γ·‖T T^T - I‖`，其中第二项约束 T 接近置换矩阵（一一对应）。
- **理论支撑**：命题 1（Proposition 1）证明：当潜特征跨帧可分且运动平滑时，OT 传输矩阵 T 会收敛为近似置换结构，反映强时序一致性。
- **应用范围**：仅作用于机器人手臂潜空间（其解码器在第二阶段被丢弃，因此可专注于时序一致性建模）。

### 2.4 与下游 LDM 的集成

- 以 IRASim-L（461M DiT）为例，将机器人手臂潜 `Z_arm` 与环境潜 `Z_env` 转为同维度 token 序列，共享 DiT 参数与扩散过程；
- 每 `k=2` 个 transformer block 插入一次交叉注意力层，实现两路潜之间的信息交换（机器人运动受周围物体调整，环境表征考虑光照、阴影等运动引起的变化）；
- 动作条件注入策略：对齐到不同压缩率下的潜空间维度（如手臂 4× 时间下采样对应 `T/4` 个动作 token，环境 8× 对应 `T/8` 个）。

## 3. 实验设计

### 3.1 数据集

| 用途 | 数据集 |
|---|---|
| 训练 | 自建约 100 万条机械臂操纵视频，聚合自 RobNet、RobSet、BC-Z、RH20T、DROID |
| 重建评估 | Agibot-2025、Bridge (BridgeData V2) |
| 动作条件视频生成评估 | RT-1、Bridge |

- 训练视频为 3 fps、16 帧、256×256；评估视频为 16 fps、16 帧、256×256；
- 机械臂掩码由 SAM2 + Grounding DINO 自动生成（文本提示 "robotic arm"）。

### 3.2 评估指标

- **重建质量**：PSNR、SSIM、LPIPS、FVD；
- **效率**：压缩率（latent 维度 / 原始视频维度）；
- **下游生成**：固定 LDM backbone（IRASim-L 461M），仅替换 VAE 进行公平比较。

### 3.3 对比方法

- **重建任务（8 个基线）**：OpenSoraPlan、Cosmos、iVideoGPT、MAGVIT-v2、VidTwin、EMU-3、CV-VAE、CMD；
- **下游动作条件生成（7 个基线 + SDXL 图像 VAE）**：Wan-VAE、Cog-VAE、OpenSoraPlan、EMU-3、CV-VAE、VidTwin、CMD、SDXL（无时序压缩的强基线）。

## 4. 资源与算力

- **GPU**：训练使用 **NVIDIA A800** GPU，正文称 "8 张"，附录 C 中训练配置表提到 8 张 A800（40 GB），但在附录实验细节部分提及 **16 张 A800**，存在轻微不一致；
- **训练配置**：8 fps（正文）vs 3 fps（附录）、16 帧、256×256 分辨率；
- **训练时长**：**论文未明确报告总训练时长**；
- **OT 模块开销**：每 100 样本训练时间从 49.23s 增至 52.76s（增加约 7%），作者声称"可接受"。

## 5. 实验数量与充分性

- **重建对比实验**：表 1 在 2 个数据集（Agibot-2025、Bridge）× 4 个指标（PSNR、LPIPS、SSIM、FVD）下与 8 个基线对比，并附加图 3 的定性可视化；
- **下游生成对比实验**：表 2 在 2 个数据集（RT-1、Bridge）× 4 个指标下与 8 个基线对比，附加图 4 的定性可视化；
- **消融实验**：表 3 在 2 个重建数据集 + 2 个下游数据集上对比 "完整方法 / w/o Mask / w/o L_motion"；
- **解耦分析**：图 5 可视化两个分支独立解码结果，证明潜空间解耦；
- **效率分析**：图 6 对比下游 LDM 训练时间（每 1000 步），含 SDXL/Cog-VAE/Wan-VAE/OpenSoraPlan/CMD 等多个基线；
- **补充材料**：附录提供 Bridge、Agibot-2025 的额外重建样例（图 1、图 2）、Bridge/RT-1 的额外生成样例（图 5、图 6）、OT 模块计算时间分析、大机械臂占比场景下的鲁棒性分析。
- **充分性评价**：实验较为系统，覆盖了重建、下游任务、消融、效率、可视化等多个维度；但**训练集和评估集存在领域差异**（训练集来自 RobNet/RobSet/BC-Z/RH20T/DROID，评估集为 Agibot-2025、RT-1、Bridge），且未做跨域泛化的专项评估。

## 6. 主要结论与发现

- **重建质量**：EmbodiedVAE 在 Agibot-2025 上取得最佳 PSNR（31.6745）、LPIPS（0.0723）、SSIM（0.9345）、FVD（368.55），压缩率 0.39%，仅为次优基线 CMD（6.85%）的约 1/20；
- **下游动作控制**：在 RT-1 和 Bridge 上均显著优于 Wan-VAE、Cog-VAE 等强基线，**比 runner-up Wan-VAE 平均提升约 2 dB PSNR**；且**超越了无时序压缩的 SDXL 图像 VAE**，验证了解耦设计 + 时序一致性约束的有效性；
- **OT 一致性损失的作用**：消融实验显示其对下游操纵任务的提升尤为显著；
- **掩码监督的作用**：训练时使用掩码显著提升解耦质量（消融 "w/o Mask" 性能下降），但推理时无需掩码；
- **效率优势**：紧凑潜空间有效降低下游 LDM 训练时间和显存消耗（图 6）。

## 7. 方法与实验设计的亮点

- **场景驱动的非对称压缩**：根据前景/背景在具身场景中的不同特性（机器人占比小但关键、背景时间冗余高）设计差异化压缩率，是本文最核心的设计思路；
- **OT-based 时序一致性**：相比简单的相似度损失，OT 通过全局最优传输建立多对多对应关系，并附带理论分析（Proposition 1）解释为何 T 会收敛为置换结构；
- **训练-推理解耦的掩码策略**：训练时用 SAM2 + Grounding DINO 自动生成的掩码引导，推理时无需任何额外输入即可完成解耦，工程化考虑周到；
- **公平对比设计**：固定 LDM backbone（IRASim-L 461M），仅替换 VAE 进行下游评估，并针对每个 VAE 设计相应的动作注入策略（附录 C.2 详细列出），增强了结论可信度；
- **下游训练效率实证**：图 6 直接量化了紧凑潜空间对 LDM 训练时间和显存的影响。

## 8. 不足与局限

- **训练掩码依赖**：依赖 SAM2 + Grounding DINO 自动生成掩码，掩码质量直接影响解耦效果，若目标场景与训练集差距大可能带来偏差风险；
- **任务与场景覆盖有限**：仅聚焦于桌面级机械臂操纵（first-person 操作视角），未涉及移动机器人、双臂协同、户外场景等；附录 E 提到大占比机械臂场景的鲁棒性，但仅展示定性样例，缺乏定量评估；
- **跨域泛化未充分验证**：训练集（RobNet/RobSet/BC-Z/RH20T/DROID）与评估集（Agibot-2025、RT-1、Bridge）领域分布差异较大，未做系统性的跨域泛化实验；
- **训练时长与数据规模报告不充分**：未明确报告总训练时长、收敛曲线，且正文与附录对 GPU 数量（8 vs 16）和训练 fps（8 vs 3）的描述存在不一致；
- **OT 模块的理论-实践 gap**：Proposition 1 给出的是渐近性结论，未提供定量实验（如不同 ε、Δ、γ 下的敏感性分析）；
- **计算开销声明偏弱**：OT 模块 `O(ΔT N² d)` 复杂度在 N 较大时仍可能成为瓶颈，附录 D 仅给出单 GPU、单分辨率下的对比，缺乏规模化分析；
- **应用局限**：目前仅在 IRASim 一个 LDM backbone 上验证，未展示与多种主流视频生成 LDM（如 CogVideoX、Wan 系列、SVD）的兼容性；
- **潜在偏差**：作者团队与 IRASim 团队有部分重叠（来自 Microsoft Research Asia、USTC 等），存在一定的方法对比选择性偏差风险。

（完）
