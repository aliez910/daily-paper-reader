---
title: "StaMo: Unsupervised Learning of Generalizable Robot Motion from Compact State Representation"
title_zh: "StaMo:基于紧凑状态表征的可泛化机器人运动无监督学习"
authors: "Liu, Mingyu, Shu, Jiuhe, Chen, Hui, Li, Zeju, Zhao, Canyu, Yang, Jiange, Gao, Shenyuan, Chen, Hao, Shen, Chunhua"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_StaMo_Unsupervised_Learning_of_Generalizable_Robot_Motion_from_Compact_State_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 为VLA模型提供压缩状态表征以提升操纵性能
tldr: "针对机器人状态表征在表达性与紧凑性之间难以平衡的问题,本文提出无监督的StaMo方法。该方法结合轻量编码器与预训练扩散Transformer解码器,学习高度压缩的双标记状态表征。集成到现有VLA模型后,在LIBERO基准上提升11.6%,真实任务成功率提升31%,为通用视觉-动作机器人系统提供了有效的表征学习工具。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1534, \"height\": 1256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 867, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 531, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 336, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 728, \"height\": 576, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 825, \"height\": 114, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 869, \"height\": 578, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 656, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 841, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 873, \"height\": 268, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 769, \"height\": 147, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1681, \"height\": 381, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 839, \"height\": 260, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-stamo-unsupervised-learning-of-generalizable-robot-motion-from-compact-state-cvpr-2026-paper/table-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 800, \"height\": 145, \"label\": \"Table\"}]"
motivation: "机器人状态表征常在表达性与紧凑性之间失衡,影响世界建模与决策效率。"
method: "采用轻量编码器与预训练DiT解码器,无监督地学习双标记的紧凑状态表征。"
result: "在LIBERO基准提升11.6%,真实任务成功率提升31%,且可无缝集成进VLA模型。"
conclusion: 为通用机器人系统提供了一种高效且可解释的状态表征新方案。
---

## Abstract
A fundamental challenge in embodied intelligence is developing expressive and compact state representations for efficient world modeling and decision making. However, existing methods often fail to achieve this balance, yielding representations that are either overly redundant or lacking in task-critical information. We propose an unsupervised approach that learns a highly compressed two-token state representation using a lightweight encoder and a pre-trained Diffusion Transformer (DiT) decoder, capitalizing on its strong generative prior. Our representation is efficient, interpretable, and integrates seamlessly into existing VLA-based models, improving performance by 11.6% on LIBERO and 31% in real-world task success with minimal inference overhead. More importantly, we find that the difference between these tokens, obtained via latent interpolation, naturally serves as a highly effective latent action, which can be further decoded into executable robot actions. This emergent capability reveals that our representation captures structured dynamics without explicit supervision. We name our method StaMo for its ability to learn generalizable robotic Motion from compact State representation, which is encoded from static images, challenging the prevalent dependence to learning latent action on complex architectures and video data. The resulting latent actions also enhance policy co-training, outperforming prior methods by 10.4% with improved interpretability. Moreover, our approach scales effectively across diverse data sources, including real-world robot data, simulation, and human egocentric video.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "StaMo: Unsupervised Learning of Generalizable Robot Motion from Compact State Representation" following a specific structured format with 8 points. Let me analyze the paper carefully and produce a comprehensive, well-organized summary.

Let me go through each section of the paper systematically:

1. **Core problem and motivation**: The paper addresses the challenge of learning state representations that are both compact and expressive for world modeling and decision making in robotics. Existing methods tend to be either redundant (high-dimensional features) or lack task-critical information (low-dimensional motion representations).

2. **Methodology**: 
- StaMo framework using a Diffusion Autoencoder
- Encoder: DINOv2 (frozen) + transformer-based compressor
- Decoder: Pre-trained DiT (Diffusion Transformer) from Stable Diffusion 3
- Compresses images to as few as 2 tokens of 1024 dimensions
- Uses Flow Matching loss
- Key discovery: motion emerges as the difference between two state tokens (Δz = E(In+k) - E(In))
- Three applications: world modeling for VLA, latent motion co-training, goal-conditioned planning

3. **Experiments**:
- Datasets: LIBERO, DROID, OXE, Ego-centric data, ManiSkill (OOD)
- Benchmarks: LIBERO (Spatial, Object, Goal, Long), ManiSkill, real-world tasks
- Comparisons: DP, Octo-Base, Spatial-VLA, CoT-VLA, π0-FAST, WorldVLA, UniVLA, OpenVLA, OpenVLA-OFT, LAPA, ATM, DINO-WM

4. **Resources**: Only mentions RTX 4090 GPU for inference speed benchmarks. No training compute details.

5. **Experiment count and sufficiency**:
- Multiple ablations: token dimension, training data sources, pretrained vs from-scratch decoder
- Reconstruction quality on multiple datasets
- World modeling experiments on LIBERO
- Zero-shot transfer to ManiSkill
- Inference speed comparison
- Policy co-training with RDT
- Linear probing
- Goal-conditioned planning
- Real-world experiments with 6 tasks

6. **Main conclusions**:
- StaMo representation is both compact and expressive
- Motion emerges naturally from state differences
- +11.6% on LIBERO, +31% real-world success rate
- 10.4% improvement in policy co-training
- Scales with more data including human egocentric videos
- Strong generalization and zero-shot transfer

7. **Highlights**:
- Novel approach of learning motion from static images (not video)
- Extremely compact representation (2 tokens)
- Pre-trained DiT decoder provides strong generative prior
- Seamless integration with existing VLA models
- No need to decode full images during inference
- Motion emerges without explicit motion supervision

8. **Limitations**:
- Real-world experiments limited to 50 demonstrations per task, 20 trials
- OpenVLA-OFT* removed wrist camera input (modification)
- Limited comparison of training data sources
- No detailed computational resource reporting
- The "emergent" nature of motion may have boundary conditions not fully explored
- Limited evaluation on more complex/long-horizon tasks

Let me write this up in a detailed, structured manner in Chinese.</think>

# StaMo 论文总结

## 1. 核心问题与研究动机

**核心问题**：在具身智能领域，学习既**紧凑**又**富有表达力**的状态表征是一个根本性挑战。现有方法存在明显失衡：
- **高维视觉特征**（如 DINOv2 完整特征图 256×1024）：过于冗余，无法通过简单差分表示运动
- **低维运动表征**（如轨迹、光流、潜动作）：缺乏足够的语义丰富度，无法编码目标状态、交互动力学与结构化空间关系

**研究动机**：作者提出一个颠覆性问题——既然目标是从帧间变化中捕捉潜动作，为何必须依赖复杂视频模型从次优的状态表征中学习运动？是否可以**从单帧图像中学习足够表达性的状态表征**，使得两个状态之间的简单差分自然蕴含有意义的潜动作？

---

## 2. 方法论

### 2.1 整体框架：扩散自编码器（Diffusion Autoencoder）

StaMo 基于 Stable Diffusion 3 构建，由两部分组成：

- **编码器 E**：冻结的 DINOv2 视觉特征提取器 + Transformer 压缩器，将图像压缩为仅 **2 个 1024 维 token** 的紧凑潜态
- **解码器 D**：预训练的 Diffusion Transformer (DiT)，以紧凑 token 为条件重建原始图像

### 2.2 训练目标（Flow Matching）

$$\mathcal{L}_{DAE} = \mathbb{E}_{z_0, t} \| D(z_t, E(x_0), t) - u(z_t) \|_2^2$$

其中 $z_0 = \tau(x_0)$ 为 VAE 编码的图像潜变量，$z_t = (1-\sigma_t)z_0 + \sigma_t \epsilon$ 为线性插值噪声，$u$ 为目标速度。仅训练压缩器和 DiT 解码器，DINOv2 保持冻结。

### 2.3 核心发现：运动从状态中"涌现"

通过在潜态空间对两个状态的紧凑 token 做**线性差分**，即可得到运动表示：

$$a_t = s_{t+1} - s_t, \quad m_t = E(o_{t+1}) - E(o_t)$$

即潜动作 = 状态差，无需任何显式运动监督。

### 2.4 三大下游应用

1. **高效世界建模**：将 StaMo 表征集成到 OpenVLA/OpenVLA-OFT，附加轻量 MLP 头预测未来状态，损失函数为：
   $$\mathcal{L}_{total} = \lambda_{action} \mathcal{L}_{action} + \lambda_{future} (\mathcal{L}_{MSE} + \mathcal{L}_1)$$
   
2. **潜动作协同训练**：在无动作标签的视频数据上自动生成伪动作标签，与少量带标签的机器人数据联合训练策略模型

3. **目标图像规划**：通过线性头将状态差解码为可执行动作序列

---

## 3. 实验设计

### 3.1 数据集与场景

| 用途 | 数据集 |
|------|--------|
| 训练 | LIBERO、DROID、OXE、Ego-centric（人称视角视频）、ManiSkill (OOD) |
| 评估基准 | LIBERO（4 个子集）、ManiSkill、6 个自建真实任务 |

### 3.2 对比方法

- **VLA 基线**：DP、Octo-Base、Spatial-VLA、CoT-VLA、π0-FAST、WorldVLA、UniVLA、OpenVLA、OpenVLA-OFT
- **潜动作方法**：LAPA、ATM
- **世界模型**：DINO-WM

### 3.3 评估维度

- 重建质量（PSNR、SSIM）
- 任务成功率（仿真与真实）
- 推理速度（Hz）
- 零样本迁移能力
- 潜动作线性探测 MSE

---

## 4. 资源与算力

- **推理基准**：仅在 **单卡 RTX 4090 GPU** 上测试了推理频率
- **训练算力**：论文**未明确说明**训练所用的 GPU 型号、数量及训练时长
- **数据规模**：真实任务每项 50 条人类示范，每项任务评估 20 次

> **算力信息披露不充分**，这是论文的一个明显缺憾。

---

## 5. 实验数量与充分性

论文共进行了 **约 9 组主要实验**，覆盖面较广：

1. **重建质量实验**：7 个数据集的 PSNR/SSIM 评估
2. **LIBERO 世界建模**：在 OpenVLA 与 OpenVLA-OFT 两个基线上对比 state/motion 两种表征
3. **推理速度对比**：7 种方法的频率测试
4. **ManiSkill 零样本迁移**：4 个任务 × 100 次试验
5. **RDT 协同训练**：5 种数据配置
6. **线性探测**：4 种基线、4 种时间跨度的 MSE
7. **目标条件规划**：ManiSkill 上 4 个任务
8. **真实世界实验**：6 个任务（3 短视野 + 3 长视野）
9. **消融研究**：
   - Token 维度（256/512/1024）
   - 训练数据组合（S / S+D / S+D+O / S+D+O+Ego）
   - 预训练 vs 从头训练解码器

**充分性评价**：
- ✅ 多数据集、多任务、多方法对比，涵盖仿真与真实场景
- ✅ 消融较完整，覆盖表征维度、数据规模、关键组件
- ⚠️ 真实任务评估次数偏少（20 次/任务），统计显著性有待加强
- ⚠️ OpenVLA-OFT* 移除了腕部相机输入，修改了原架构，可能影响公平性

---

## 6. 主要结论与发现

1. **状态表征兼具紧凑性与表达力**：仅 2 个 1024 维 token 即可在多个数据集上达到 25+ dB PSNR 与 0.89+ SSIM
2. **LIBERO 基准**：OpenVLA* + StaMo 平均成功率从 76.5% → 88.1%（**+11.6%**）；OpenVLA-OFT* 从 92.2% → 96.8%
3. **真实任务**：相比 OpenVLA 基线，成功率从 25% 提升至 56%–64%（**+31%**）
4. **协同训练**：RDT 配合 4 份 StaMo 伪动作视频 + 1 份真值，达到 84.6%（接近全真值 86.2%），超越 LAPA（74.2%）和 ATM（73.4%）
5. **零样本迁移**：在 ManiSkill 上显著优于 WorldVLA、UniVLA
6. **潜动作线性探测**：在所有时间跨度（1/2/4/8 步）下 MSE 均最低
7. **目标条件规划**：在 ManiSkill 上优于 DINO-WM
8. **可扩展性**：随数据规模与多样性增加（仿真 + DROID + OXE + 人称视频），性能持续提升
9. **架构选择**：短视野策略适合 motion 表征；长视野策略适合 state 表征

---

## 7. 优点与亮点

- **范式创新**：打破"必须从视频学潜动作"的固有思维，从静态图像出发获得运动表征
- **极致紧凑**：2 个 token 同时实现重建与世界建模，计算开销极小
- **预训练先验利用**：DiT 预训练生成能力为表征学习提供强先验，消融证明从头训练解码器性能显著下降
- **零推理开销**：不需解码完整图像，仅预测 token 即可，推理速度近原模型
- **广泛适用**：可无缝集成进 OpenVLA、OpenVLA-OFT、RDT 等多种框架
- **强泛化性**：sim2sim、sim2real、real2sim 的运动迁移均验证通过
- **数据扩展性强**：仿真、真实机器人、人称视频均可利用

---

## 8. 不足与局限

1. **算力信息披露不全**：训练 GPU 型号、数量、训练时长均未报告，难以复现
2. **架构修改公平性**：OpenVLA-OFT* 移除了腕部相机输入，对比时可能引入变量偏差
3. **真实实验规模有限**：每任务 50 条示范、20 次评估，对长视野任务的统计可靠性不足
4. **理论机制未充分阐释**：为何状态差分能"涌现"运动的内在机制缺乏理论分析，更多是经验性发现
5. **OOD 测试有限**：仅在 ManiSkill 上做零样本迁移，未覆盖更多 OOD 场景（如光照变化、杂乱背景、复杂物体）
6. **"涌现"边界条件未明**：在哪些情况下状态差分不再代表有效运动，论文未做失败案例分析
7. **对比方法版本可能不一致**：OpenVLA-OFT 的"*"变体实际是简化版本，对比公平性需谨慎解读
8. **依赖强预训练**：严重依赖 DiT 的生成先验，对于没有大规模图像预训练资源的团队可能难以复现

（完）
