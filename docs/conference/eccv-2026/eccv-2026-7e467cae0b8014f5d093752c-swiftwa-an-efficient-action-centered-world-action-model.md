---
title: "SwiftWA: An Efficient Action-Centered World-Action Model"
title_zh: SwiftWA：面向机器人策略学习的高效以动作为中心的WAM模型
authors: "Chaojun Ni, Xinyu Zhou, YuKun Zhou, Jingyu Liu, Xiaofeng Wang, Zheng Zhu, Yang Wang, Qiuping Deng, Yun Ye, Hao Li, Zhichao Liu, Jindi Lv, Boyuan Wang, Guosheng Zhao, Guan Huang, Min Cao, Wenjun Mei"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/7867.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 以动作为中心的WAM模型，基于当前观测预测动作序列用于端到端机器人控制
tldr: 针对现有世界-动作模型（WAM）在联合推理未来视觉动态与动作时推理开销巨大，以及联合建模将视觉与运动表征纠缠导致运动预测依赖视频预测的问题，本文提出了以动作为中心的WAM——GigaWorld-Policy（SwiftWA）。该方法学习二维像素-动作动态，支持高效动作解码并可选地进行视频生成；模型以当前观测为条件预测未来动作序列，训练阶段同时以预测为条件生成未来视频。该工作为端到端机器人控制提供了一种高效的视觉-动作建模方案。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-001.webp\", \"caption\": \"\", \"page\": 5, \"index\": 1, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-003.webp\", \"caption\": \"\", \"page\": 7, \"index\": 3, \"width\": 924, \"height\": 788}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-004.webp\", \"caption\": \"\", \"page\": 14, \"index\": 4, \"width\": 725, \"height\": 465}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-005.webp\", \"caption\": \"\", \"page\": 14, \"index\": 5, \"width\": 725, \"height\": 388}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-006.webp\", \"caption\": \"\", \"page\": 14, \"index\": 6, \"width\": 725, \"height\": 465}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-007.webp\", \"caption\": \"\", \"page\": 14, \"index\": 7, \"width\": 759, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-008.webp\", \"caption\": \"\", \"page\": 14, \"index\": 8, \"width\": 759, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-009.webp\", \"caption\": \"\", \"page\": 14, \"index\": 9, \"width\": 725, \"height\": 388}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-010.webp\", \"caption\": \"\", \"page\": 14, \"index\": 10, \"width\": 759, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-011.webp\", \"caption\": \"\", \"page\": 14, \"index\": 11, \"width\": 759, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-012.webp\", \"caption\": \"\", \"page\": 15, \"index\": 12, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-013.webp\", \"caption\": \"\", \"page\": 15, \"index\": 13, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-014.webp\", \"caption\": \"\", \"page\": 15, \"index\": 14, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-015.webp\", \"caption\": \"\", \"page\": 15, \"index\": 15, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-016.webp\", \"caption\": \"\", \"page\": 15, \"index\": 16, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-017.webp\", \"caption\": \"\", \"page\": 15, \"index\": 17, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-018.webp\", \"caption\": \"\", \"page\": 15, \"index\": 18, \"width\": 768, \"height\": 192}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7e467cae0b8014f5d093752c/fig-019.webp\", \"caption\": \"\", \"page\": 15, \"index\": 19, \"width\": 768, \"height\": 192}]"
motivation: 现有世界-动作模型推理开销大且视觉与运动表征纠缠，难以用于高效端到端机器人控制。
method: 提出以动作为中心的WAM，学习二维像素-动作动态并实现高效动作解码与可选视频生成。
result: 在显著降低推理开销的同时保持了动作预测与视频预测的质量。
conclusion: SwiftWA 提供了一种面向端到端机器人控制的高效视觉-动作模型新方案。
---

## Abstract
World–Action Models (WAMs) initialized from pre-trainedvideo generation backbones have demonstrated remarkable potential forrobot policy learning. However, existing approaches face two critical bot-tlenecks: joint reasoning over future visual dynamics and actions incurssubstantial inference overhead, and joint modeling entangles visual andmotion representations, making motion prediction dependent on videoforecasts. To address these issues, we introduce GigaWorld-Policy, anaction-centered WAM that learns 2D pixel–action dynamics while en-abling efficient action decoding with optional video generation. Specif-ically, the model predicts future action sequences conditioned on thecurrent observation and, during training, generates future videos condi-tioned on the predicted actions and the same observation. Supervisionfrom both action prediction and video generation provides richer learn-ing signals and encourages physically plausible actions through visual-dynamics constraints. With a causal design that prevents future-videotokens from influencing action tokens, explicit future-video generationis optional at inference time, enabling faster deployment. To supportthis paradigm, we curate a diverse, large-scale robot dataset to pre-train the model. Experiments on real-world robotic platforms show thatGigaWorld-Policy runs 9× faster than the WAM baseline Motus whileimproving task success rates by 7%; compared with π0.5 , it improvesperformance by 95% on RoboTwin 2.0.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "GigaWorld-Policy: An Efficient Action-Centered World–Action Model" following a specific structure. Let me analyze the paper carefully and produce a well-structured Markdown summary.

Key points to cover:
1. Core problem and motivation
2. Methodology
3. Experimental design (datasets, baselines)
4. Computational resources
5. Number of experiments and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me draft this based on the paper content.

Core problem:
- World-Action Models (WAMs) initialized from pretrained video generation backbones have potential but two bottlenecks:
  1. Joint reasoning over future visual dynamics and actions = substantial inference overhead
  2. Joint modeling entangles visual and motion representations, making motion prediction dependent on video forecasts

Method:
- GigaWorld-Policy: action-centered WAM
- Learns 2D pixel-action dynamics
- Predicts future action sequences conditioned on current observation
- During training, generates future videos conditioned on predicted actions + same observation
- Causal design prevents future-video tokens from influencing action tokens
- At inference, future-video generation is optional → low latency
- Built on Wan 2.2 5B diffusion Transformer
- Multi-view composition (left, front, right cameras combined)
- Action chunk length p=48, future-observation stride Δ=12
- Causal self-attention mask: states/observations attend to each other; actions attend to states+observations only; future video tokens attend to all
- Flow matching objective for both action and video prediction
- Pre-training: web video model → embodied data pre-training (~10,000 hours) → post-training on target robot
- Datasets: EgoDex (800h), AgiBot (2500h), Ego4D (3500h), RoboMind (300h), RDT (25h), Open X-Embodiment (3500h), DROID (350h), ATARA (10h), Something-Something V2 (200h)

Experiments:
- Simulation: RoboTwin 2.0, 50+ tasks, 100 episodes per task, clean + randomized settings
- Real-world: AgileX PiPER 6-DoF arm, 4 tasks (Clean the Desk, Scan QR Code, Sweep up Trash, Stack Bowls), 20 trials per task, 5 attempts each
- Baselines: π0.5, GigaBrain-0, X-VLA (VLAs); Motus, Cosmos-Policy (WAMs)
- Inference latency benchmark on NVIDIA A100

Results:
- 9× faster than Motus (3231ms → 360ms)
- 7% higher success rate than Motus on real-world
- 95% improvement over π0.5 on RoboTwin 2.0 (0.43→0.85 in clean)
- Best real-world SR: 0.83 vs Motus 0.76 vs π0.5 0.69
- OOD generalization: 0.72 average vs Motus 0.60, π0.5 0.50
- Challenging tasks: 0.68 average vs Motus 0.58
- Data efficiency: matches π0.5 with only 10% data

Ablations:
- Pre-training components: scratch (0.45), video init only (0.57), embodied only (0.73), both (0.83)
- Future-frame sampling interval: Δ=12 best (0.83)
- Causal self-attention vs self-attention

Resources:
- NVIDIA A100 GPU mentioned for benchmarking
- 5B parameter Wan 2.2 backbone
- ~10,000 hours of pre-training data
- No explicit training duration mentioned
- No GPU count mentioned

Let me write this up in Chinese Markdown format.</think>

# GigaWorld-Policy 论文结构化总结

## 1. 核心问题与研究动机

- **背景**：基于 VLM 的视觉-语言-动作模型（VLA）在机器人操控中表现优异，但仍存在 **监督稀疏** 的核心痛点——动作监督低维、单一，容易让模型依赖语境捷径，坍缩到少量动作原型，难以学到物理一致的动作分布。
- **现有改进路线及其瓶颈**：
  - **路线 a**：在 VLA 中加入未来视觉监督信号，但 VLM 本质是判别式模型，难以约束物理一致性。
  - **路线 b**：将视频生成的世界模型（WM）引入策略学习（WAM），联合预测动作与未来视频，但**推理开销巨大**（需迭代采样生成未来视频）。
  - **路线 c**：两阶段设计（先预测未来视频，再用 IDM 解码动作），视频预测误差会传播到动作，且增加推理延迟。
- **本文定位**：提出一种 **以动作为中心（action-centered）的 WAM**，将未来视频动态作为训练阶段的密集监督与推理信号，但在推理阶段 **可选生成视频**，从而兼顾物理一致性约束与低延迟部署。

---

## 2. 方法论

### 2.1 整体框架
- 基于 **Wan 2.2 5B 扩散 Transformer**（视频生成骨干）构建。
- 模型同时参数化两个条件分布：
  - 动作建模：\( a_{t:t+p-1} \sim g_\Theta(\cdot | o_t, s_t, l) \)
  - 视觉前向动力学：\( o_{t+k\Delta} \sim g_\Theta(\cdot | o_t, s_t, l, c_t) \)，其中 \(\Delta\) 为时间步长，\(K=\lfloor p/\Delta \rfloor\)。

### 2.2 关键设计
- **多视图输入融合**：将 left/front/right 三视角图像拼接为一张合成图像，保持分辨率一致，利于跨视角一致性推理。
- **稀疏未来帧预测**：仅沿动作时域每 \(\Delta\) 步预测一帧，减少冗余监督。
- **共享 Transformer + 分模态位置编码**：所有 token（观测、状态、动作、未来视频）共用 Q/K/V 投影；视觉 token 用 2D 位置编码，状态/动作 token 用 1D 时间位置编码。
- **因果自注意力掩码**（核心创新）：
  - 状态 \(T_s\) 与观测 \(T_o\) 互相可见，但不能看动作/未来视频；
  - 动作 token \(T_a\) 仅能看到 \(\{T_s, T_o\}\)，看不到未来视频；
  - 未来视频 token \(T_f\) 可看到 \(\{T_s, T_o, T_a\}\)，用于动作条件下的视觉前向预测。
  - 语言指令通过 cross-attention 注入，不参与因果序列。
- **流匹配目标**：对动作 token 和未来视频 token 分别施加 flow matching 损失；后训练阶段联合优化 \(L_{all} = \lambda_{video} L_{video} + \lambda_{action} L_{action}\)，其中 \(\lambda_{action}=5, \lambda_{video}=1\)，更强调动作预测。

### 2.3 训练流程
- **预训练阶段 1**：用 Wan 2.2 的通用视频生成权重初始化。
- **预训练阶段 2**：在约 **10,000 小时** 的具身数据（含真实机器人视频 + 第一视角人类视频）上继续预训练，学习具身相关视觉动力学。
- **后训练阶段**：在目标机器人（AgileX PiPER）数据上对齐图像-语言-动作。
- 动作块长度 \(p=48\)，未来观测间隔 \(\Delta=12\)。

### 2.4 推理流程
- 仅解码动作 token，不实例化未来视频 token；如需视频，可通过 KV 缓存复用已有上下文，条件式生成。
- 控制闭环延迟可低至 **0.36 s/step**。

---

## 3. 实验设计

### 3.1 数据集
- **具身预训练数据**（合计约 10,000 h）：
  - EgoDex（800h）、Ego4D（3500h）、Something-Something V2（200h）
  - AgiBot（2500h）、Open X-Embodiment（3500h）、RDT（25h）、RoboMind（300h）、DROID（350h）、ATARA（10h）
- **仿真训练数据**：RoboTwin 2.0 混合数据集，2,500 条 clean（每任务 50）+ 25,000 条重随机化（每任务 500）。

### 3.2 Benchmark
- **仿真**：RoboTwin 2.0，50+ 操控任务，覆盖 clean 与随机化两种设置。
- **真实世界**：AgileX PiPER 6-DoF 机械臂，4 个任务（Clean the Desk、Scan a QR Code、Sweep up Trash、Stack Bowls）。
- **鲁棒性测试**：OOD 任务（未知环境、新物体、光照变化、新桌布）与高难度任务（高灵巧 Fold Clothes、长时序 Stack Boxes）。
- **指标**：Success Rate（SR），真实任务采用分级评分（如抓取 0.5 + 放置 0.5）。

### 3.3 对比方法
- **VLA 类**：π0.5、GigaBrain-0、X-VLA。
- **WAM 类**：Motus（最强基线）、Cosmos-Policy。

---

## 4. 资源与算力

- **GPU**：报告推理延迟时使用 **单张 NVIDIA A100**。
- **骨干规模**：Wan 2.2 5B 参数扩散 Transformer。
- **数据规模**：具身预训练约 10,000 小时视频数据。
- **未明确披露**：训练使用的 GPU 数量、训练时长、显存占用、训练阶段总算力等关键信息，**算力细节明显不足**。

---

## 5. 实验数量与充分性

- **仿真实验**：RoboTwin 2.0 上 50+ 任务 × 2 设置（clean / Rand.）× 100 episodes，覆盖较广。
- **真实世界实验**：每个任务 20 次 × 最多 5 次尝试，相对样本量较小。
- **OOD 与高难度任务**：3 个 OOD 任务 + 2 个高难度任务，初步验证泛化能力。
- **消融实验**：
  - 预训练组合（scratch / 视频初始化 / 具身预训练 / 两者结合）
  - 未来帧采样间隔（Δ=4, 8, 12, 24, 48 + No pred.）
  - 因果 vs. 全连接自注意力（含 PSNR/SSIM 视频质量）
  - 数据效率曲线（不同数据比例 vs π0.5）
- **充分性评价**：
  - 优点：仿真覆盖任务多、含 clean/随机化双设置、消融维度合理。
  - 局限：真实世界任务数与样本量偏少；未在多机器人形态、多控制接口上验证；缺乏与更多近期 WAM/VLA（如 DreamVLA、GR-3）的直接对比。

---

## 6. 主要结论与发现

- **效率-性能权衡**：相比 Motus，推理 **快 9×**（3.231s → 0.36s），真实世界成功率提升 7%（0.76 → 0.83）。
- **vs π0.5**：仿真平均成功率提升 44+ 百分点（0.43 → 0.85），真实任务提升 14%（0.69 → 0.83），延迟接近。
- **vs Cosmos-Policy**：快 3.9×，成功率大幅领先（0.58 → 0.83）。
- **OOD / 难任务**：平均 SR 分别 0.72 / 0.68，显著高于所有基线。
- **数据效率**：用 π0.5 训练数据量的 **10%** 即可达到其最佳成功率。
- **关键消融**：
  - 视频初始化 + 具身预训练互补，组合最佳（SR 0.83）。
  - 未来帧间隔 \(\Delta=12\)（K=4）最优，过密或过疏都会退化。
  - 因果掩码在动作 SR 上与全连接自注意力相近，但视频生成质量更高（PSNR/SSIM 提升），且推理时可省略视频。

---

## 7. 优点

- **范式创新**：把 WAM 的"视频必生成"解耦为"训练必监督、推理可选"，兼顾物理一致性与低延迟。
- **因果掩码设计**：简洁而有效，既保证动作预测不被未来视频污染，又允许视频以动作为条件。
- **多源大规模预训练**：10,000 h 数据融合真实机器人视频与人类第一视角视频，提供强具身先验。
- **效率-性能兼顾**：9× 加速同时 7% 成功率提升，对实际部署友好。
- **实验较全面**：仿真任务多、含随机化、消融维度（预训练、未来帧密度、注意力机制）合理。
- **数据效率突出**：10% 数据即可追平全量 π0.5，对小数据场景友好。

---

## 8. 不足与局限

- **真实世界样本量偏小**：每任务仅 20 次试验，统计稳定性有限，且任务数仅 4 个，泛化结论需谨慎。
- **缺乏多样化机器人平台验证**：仅在 AgileX PiPER 上测试，未覆盖双臂、移动机器人、其他灵巧手等。
- **缺少与最新方法的对比**：未与 WorldVLA、DreamVLA、GR-3、GR-3 tech report 等同期工作直接比较。
- **资源与训练细节披露不完整**：未给出 GPU 数量、训练总时长、超参搜索过程、后训练数据规模与采样细节。
- **因果掩码收益解释有限**：消融显示 SR 与全连接自注意力相近，主要靠视频质量提升；但缺少更细致的归因分析（如单独关闭未来帧预测的影响）。
- **任务类型偏窄**：均为桌面级抓取/放置类任务，缺乏接触丰富、力控、长时间语言条件任务。
- **超参敏感性**：动作块长度 48、未来帧间隔 12 等关键超参的鲁棒性未做大规模扫描。
- **潜在偏差风险**：真实任务评分采用分级制（0.5 + 0.5），可能掩盖中间过程失败；不同基线是否完全公平部署（含 KV cache、采样步数等）未充分说明。
- **应用限制**：依赖 Wan 2.2 这一相对较大的视频骨干（5B），对边缘部署仍具挑战；多视角拼接方式可能限制泛化到其他相机配置。

（完）
