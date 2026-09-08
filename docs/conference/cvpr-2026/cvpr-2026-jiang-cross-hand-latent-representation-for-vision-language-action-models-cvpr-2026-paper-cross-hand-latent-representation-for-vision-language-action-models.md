---
title: Cross-Hand Latent Representation for Vision-Language-Action Models
title_zh: 面向视觉-语言-动作模型的跨手统一潜在表征
authors: "Jiang, Guangqi, Liang, Yutong, Ye, Jianglong, Huang, Jia-Yang, Jing, Changwei, Duan, Rocky, Abbeel, Pieter, Wang, Xiaolong, Zou, Xueyan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Jiang_Cross-Hand_Latent_Representation_for_Vision-Language-Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向灵巧操纵的跨具身VLA统一潜在动作空间
tldr: 本文针对灵巧操纵中为每种机器人手收集大规模演示数据成本高昂的问题，提出跨手统一潜在动作空间VLA框架。该方法通过统一潜在表示实现跨具身知识迁移，使不同机器人手之间的数据可共享。该工作推动了通用视觉-动作模型在多样化灵巧操纵任务中的规模化训练。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1697, \"height\": 965, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1365, \"height\": 379, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 813, \"height\": 295, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1370, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 820, \"height\": 391, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 731, \"height\": 418, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1718, \"height\": 536, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1724, \"height\": 553, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 699, \"height\": 156, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1716, \"height\": 297, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jiang-cross-hand-latent-representation-for-vision-language-action-models-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1711, \"height\": 875, \"label\": \"Table\"}]"
motivation: 为每种灵巧机器人手单独收集大规模演示成本过高，限制VLA模型的扩展。
method: 构建跨手统一潜在动作空间，实现跨具身知识迁移的VLA框架。
result: 在多种灵巧机器人手上实现了高效可扩展的视觉-动作策略学习。
conclusion: 为通用VLA模型在灵巧操纵中的跨具身训练提供了有效途径。
---

## Abstract
Dexterous manipulation is essential for real-world robot autonomy, mirroring the central role of human hand coordination in daily activity. Humans rely on rich multimodal perception--vision, sound, and language-guided intent--to perform dexterous actions, motivating vision-based, language-conditioned manipulation systems for robots. However, training reliable vision-language-action (VLA) models for dexterous manipulation requires large-scale demonstrations across many robotic hands. In addition, as new dexterous embodiments appear rapidly, collecting data for each becomes costly and impractical, creating a need for scalable cross-embodiment learning. We introduce \ourmethod, a vision-language-action framework integrated with a unified latent action space shared across diverse dexterous hands. This embodiment-invariant latent space is directly pluggable into standard VLA architectures, enabling seamless cross-embodiment training and efficient reuse of both existing and newly collected data. Experimental results demonstrate that \ourmethod consistently outperforms baseline VLA models operating in raw joint spaces, establishing it as an effective solution for scalable cross-embodiment dexterous manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper "Cross-Hand Latent Representation for Vision-Language-Action Models" (XL-VLA) based on the provided content. I need to follow a specific structure with 8 sections and end with "（完）".

Let me analyze the paper carefully:

1. Core problem: Cross-embodiment dexterous manipulation - training VLA models for multiple dexterous hands is expensive because each hand has different action spaces. Need a unified representation.

2. Method: XL-VLA - a VLA framework with a shared latent action space across dexterous hands. Uses multi-headed VAE-style autoencoder with three losses: reconstruction (L1), retargeting via FK (L2), and KL regularization (L3). The latent space is plugged into π0 architecture, replacing state tokens with latent tokens.

3. Experiments: 
- 4 dexterous hands (Ability, Inspire, X-Hand1, Paxini DexH13)
- 10 manipulation tasks
- 50 demos per task per hand, 2000 total
- Compared with π0 baseline, LAD latent action diffusion
- xArm and G1 humanoid platforms
- Real-world evaluation

4. Resources: 8 NVIDIA H100 GPUs, 80GB each, 60K training steps, batch size 128

5. Experiments: Multiple comparisons - cross-hand scaling, cross-robot scaling, zero-shot task generalization, latent replay comparison, ablations on loss components and architecture

6. Main findings: XL-VLA outperforms π0 (0.72 vs 0.32 mean success rate), achieves +40% improvement, outperforms LAD in latent replay, supports zero-shot transfer

7. Highlights: Unsupervised latent space learning (no paired data needed), plug-and-play, real-world evaluation, multiple dexterous hands

8. Limitations: Only 4 hands tested, latent size matters, evaluation mainly on real-world tasks with limited samples (10 trials per task)

Let me structure this properly in Chinese.</think>

# 论文总结：XL-VLA — 面向视觉-语言-动作模型的跨手统一潜在表征

## 1. 核心问题与研究动机

- **领域背景**：灵巧操作（dexterous manipulation）是机器人实现真实世界自主性的核心能力之一，但当前视觉-语言-动作（VLA）模型主要针对带平行夹爪的机械臂，缺乏针对多指灵巧手的可扩展方案。
- **核心痛点**：不同灵巧手在关节构型、自由度、驱动方式上差异显著，其动作空间（如关节位置 q-pos）是手型专属的，无法像语言那样具有通用词汇表。
- **关键挑战**：
  - 如何在多种机器人手之间定义一个统一的动作表征？
  - 当新硬件形态不断出现时，如何低成本地将其接入已有 VLA 框架？
- **现实瓶颈**：为每种灵巧手单独收集大规模遥操作数据成本极高，制约了 VLA 模型在灵巧操作方向的规模化训练与数据复用。

## 2. 方法论

### 2.1 整体框架

- **名称**：XL-VLA（Cross-Hand Latent VLA）。
- **核心思想**：为多种灵巧手学习一个共享的、与具身无关的潜在动作空间，作为不同手之间沟通的"通用语言"。该潜在空间作为即插即用模块，可直接替换标准 VLA（如 π0）中的状态/动作 token。
- **整体流程**：每只手 h 配备专属的编码器 Eₕ 与解码器 Dₕ，将关节位置动作块映射到统一的潜在向量 z；VLA 骨干网络在冻结的编码-解码器之上预测潜在动作；预测结果再经 Dₕ 解码为该手可执行的关节指令。

### 2.2 关键技术细节

**（1）问题形式化**
- 动作以"块"（action chunk）形式处理：每个块包含 64 帧、采样率 20 Hz（约 3.2 s）。
- 输入：关节状态历史 q_t、图像观测 V、语言指令 T；输出：下一动作块 q_{t+1}。
- 模型 F 本身与具身无关，手型身份 h 只用于选择对应的编码器/解码器。

**（2）多头 VAE 风格的潜在空间自编码器**
- 每个手型 h 有专属 MLP 编码器 Eₕ 与解码器 Dₕ。
- 编码器输出高斯后验 (μ, σ)，通过重参数化技巧采样潜在向量 z。
- 训练数据：仅在各手硬件关节限位内随机采样的关节构型（无需示教轨迹或 IK 数据）。

**（3）三项损失函数共同塑造跨具身潜在空间**
- **L₁（重建损失）**：MSE 重建每个手的自身关节构型，保证各手型信息不丢失。
- **L₂（重定向损失）**：基于可微正向运动学（FK），对齐不同手之间的指尖捏取距离与方向。包含 L_dist²（拇指-四指捏取距离）和 L_dir²（捏取方向余弦相似度），并通过 w_ij = exp(-λ_dis·‖δ‖²) 强调紧凑捏取。
- **L₃（KL 正则）**：让潜在分布逼近标准高斯 N(0, I)，便于采样与插值。
- **总目标**：L_latent = L₁ + L₂ + βL₃，超参固定为 β=1e-5、λ_dis=2000、λ_dir=5、λ_exp_dis=12。

**（4）VLA 集成（基于 π0 改造）**
- 用 PaliGemma 初始化 VLM 主干。
- 将原 π0 中的"状态 token"替换为"潜在动作 token"：每个块的关节历史先经 Eₕ 编码为潜在向量，再作为 token 输入。
- VLA 预测下一潜在动作块 z_{t+1}，再由 Dₕ 解码为关节指令。
- 训练时 Eₕ、Dₕ 全程冻结，只微调动作专家。

## 3. 实验设计

### 3.1 数据集与场景

- **数据集**：自建大规模遥操作数据集（每任务每手 50 条示教，共约 2000 条）。
- **任务**：10 个真实世界桌面操作任务，包括准备水果（PF）、堆叠罐头（SC）、分拣罐头（SoC）、递水瓶（HB）、整理柠檬（RL）、倒酱汁（PS）、重排盒子（RB）、推糖盒（PuS）、倒糖（PoS）、推罐头（PC）。
- **硬件平台**：
  - 双手 7-DoF xArm 桌面系统 + Unitree G1 人形机器人。
  - 4 种灵巧手：Ability Hand、Inspire Hand、X-Hand1、Paxini DexH13（手指数 4–5，自由度 12–16，含 mimic 自由度）。

### 3.2 对比方法（Baseline）

- **π0 [Black et al., 2024]**：原始 VLA 直接在原始关节空间训练，通过调整序列长度兼容不同具身，是本文的主基线。
- **LAD [Bauer et al., 2025]**：监督式潜在动作扩散方法，用于跨具身重定向。
- **π0 + RT（Retargeting）**：用 XHand 训练，再用运动学重定向算法映射到其他手型。
- **CETransfer** 等（仅在 Table 1 相关工作中提及，未做直接对比）。

### 3.3 评估指标

- **成功率（SR）** 和 **部分成功率（PSR）**：每个任务测试 10 次。
- **潜在空间评估指标**：重建关节/指尖 RMSE、Pinch/Random Tip 方向与距离误差、潜在连续性（加噪声后的位移）、插值平滑性（加速度/急动度均值）。

## 4. 资源与算力

- **GPU**：8 块 NVIDIA H100，每块 80 GB 显存。
- **训练规模**：60K 步，批量大小 128。
- **训练数据规模**：约 2M state-action pairs（10 任务 × 50 demos × 4 手 × 约 100 帧/段）。
- **说明**：论文未明确给出每块 GPU 的精确训练小时数，也未报告推理时的实时性指标。

## 5. 实验数量与充分性

- **跨手数据扩展实验**（Table 2）：与 π0 在 4 种手 × 10 任务上系统对比。
- **跨机器人数据扩展**（Figure 5）：在 xArm 与 G1 上联合训练，对比原始动作空间 vs 潜在空间。
- **零样本任务泛化**（Figure 4）：每只手留出若干未见任务，训练时剔除，对比 π0 + RT。
- **潜在重放对比**（Table 4）：与 LAD 在两种手配对（Ability+Inspire、Paxini+XHand）上进行 10 任务对比。
- **消融实验**（Table 5）：分别移除 L₁、L_dist²、L_dir²、L₂ 全部；并系统扫描隐藏层配置（H=128/256、64/128×2、64/64、64）与潜在维度（L=8/16/64/96/128）。
- **可视化**（Figure 6）：定性展示同一潜在码在多手上的解码结果。
- **充分性评价**：实验覆盖了跨手、跨机器人、零样本、重定向、消融五大维度，结构较完整；但每个任务的试验次数仅 10 次，统计显著性有限；与监督式 LAD 的对比仅依赖"潜在重放"指标，未在 VLA 联合训练下对比。

## 6. 主要结论与发现

- **跨手训练性能**：XL-VLA 在所有 4 只手上均显著优于 π0；平均成功率从 0.32 提升到 0.72（+0.40，相对提升约 125%）。其中 Ability 手 0.37→0.73、Paxini 手 0.35→0.78、XHand 0.29→0.70、Inspire 0.27→0.68。
- **任务级提升**：在 Sort Cans、Hand over Bottle、Re-arrange Boxes 等精细灵巧任务上提升尤为明显。
- **零样本任务泛化**：在未见过的任务-手组合上，XL-VLA 在所有手上所有任务均不弱于 π0+RT 基线。
- **跨机器人迁移**：xArm 与 G1 联合训练时，统一潜在空间带来约 +57% 的性能提升。
- **潜在空间质量**：在重放任务中，XL-VLA 取得 0.81–0.82 平均成功率，远高于 LAD 的 0.60–0.61，且完全无监督（不需要成对跨手数据）。
- **消融发现**：
  - L₂（尤其 L_dir²）对跨具身一致性至关重要，去掉后跨手方向/距离误差显著恶化；
  - 隐藏层容量和潜在维度存在适度区间（H=128→64，L=32 表现良好），L=128 反而因过于松散而性能下降；
  - L₁、L₃ 也对重建稳定性有贡献。

## 7. 优点与亮点

- **即插即用的统一潜在空间**：在标准 VLA（如 π0）上替换 token 即可，无需改动主架构。
- **完全无监督的跨手对齐**：仅靠随机采样关节构型 + 可微 FK，无需成对跨手示教或人工标注，大幅降低数据成本。
- **三维损失协同设计**：重建 + 重定向 + KL 三者结合，既保留手型特异性又获得跨手几何一致性。
- **面向真实硬件的真实实验**：4 种异构灵巧手 + 10 个真实任务 + 双手平台，而非纯仿真。
- **跨机器人平台的额外验证**：进一步在 xArm 与 G1 人形机器人上展示方法的可推广性。
- **大规模数据集与基线公开**：2000 条示教 + 2M state-action pairs 是面向灵巧 VLA 的有价值的资源。

## 8. 不足与局限

- **手型覆盖有限**：仅在 4 种灵巧手（且都是 4–5 指、近似人手形态）上验证，对于差异更大的形态（如欠驱动手、专用工具手、人形整臂）的扩展性未充分验证。
- **单任务试验次数偏少**：每个任务仅 10 次试验，统计置信度有限；缺少置信区间或显著性检验。
- **无监督的代价**：潜在空间完全靠自监督建立，没有利用任何人类视频或示教先验，可能在非常精细的语义动作上对齐有限。
- **潜在维度与架构依赖消融不彻底**：仅扫描到 L=128，但未解释为何 L=32 是最佳点；不同手型之间的拓扑差异（如 Paxini 缺小指）只是简单丢弃对应指对，缺乏更系统的拓扑处理。
- **效率与可扩展性未量化**：未报告训练时长、推理延迟、是否支持在线新增手型的快速再训练等关键工程指标。
- **缺少与 π0 之外的强 VLA 基线对比**：未与 OpenVLA、RT-2、UniVLA 等代表性 VLA 在同等数据下的对比，难以判断收益来自"潜在空间"还是"数据规模"。
- **潜在空间可解释性与安全性**：未讨论潜在空间是否会产生不安全动作（如自碰撞、关节越界），实际部署中潜在解码仍可能越限。
- **场景单一**：全部任务为桌面双手机构化操作，未覆盖移动操作、长序列任务或非结构化环境。

（完）
