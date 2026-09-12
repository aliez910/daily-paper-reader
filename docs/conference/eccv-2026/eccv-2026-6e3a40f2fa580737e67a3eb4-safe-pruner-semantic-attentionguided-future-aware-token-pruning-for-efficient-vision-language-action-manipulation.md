---
title: "SAFE-Pruner: Semantic Attention–Guided Future-Aware Token Pruning for Efficient Vision-Language-Action Manipulation"
title_zh: "SAFE-Pruner:面向高效视觉-语言-动作操作的语义注意力引导未来感知令牌剪枝方法"
authors: "Shilin Ma, Chubin Zhang, Changyuan Wang, Yuji Wang, Yue Wu, Zixuan Wang, Jingqi Tian, Zheng Zhu, Yansong Tang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/8797.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向机器人控制的视觉-语言-动作模型加速推理
tldr: "视觉-语言-动作模型的实时推理对机器人控制至关重要,但现有视觉令牌剪枝方法依赖浅层线索,可能丢弃深层所需信息。本文提出SAFE-Pruner,即插即用框架,将未来层注意力线索融入剪枝决策。该方法通过识别跨控制时间步的语义注意力一致性,设计前瞻式剪枝策略。实验表明该方法在保持操作性能的同时显著加速VLA推理,推动通用视觉-动作策略的高效部署,对实时机器人控制具有重要价值。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-001.webp\", \"caption\": \"\", \"page\": 10, \"index\": 1, \"width\": 1440, \"height\": 1241}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-002.webp\", \"caption\": \"\", \"page\": 10, \"index\": 2, \"width\": 1024, \"height\": 768}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-003.webp\", \"caption\": \"\", \"page\": 11, \"index\": 3, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-004.webp\", \"caption\": \"\", \"page\": 11, \"index\": 4, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-005.webp\", \"caption\": \"\", \"page\": 11, \"index\": 5, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-006.webp\", \"caption\": \"\", \"page\": 11, \"index\": 6, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-007.webp\", \"caption\": \"\", \"page\": 11, \"index\": 7, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-008.webp\", \"caption\": \"\", \"page\": 11, \"index\": 8, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-009.webp\", \"caption\": \"\", \"page\": 11, \"index\": 9, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-010.webp\", \"caption\": \"\", \"page\": 11, \"index\": 10, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-011.webp\", \"caption\": \"\", \"page\": 11, \"index\": 11, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-012.webp\", \"caption\": \"\", \"page\": 11, \"index\": 12, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-013.webp\", \"caption\": \"\", \"page\": 11, \"index\": 13, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-014.webp\", \"caption\": \"\", \"page\": 11, \"index\": 14, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-015.webp\", \"caption\": \"\", \"page\": 11, \"index\": 15, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-016.webp\", \"caption\": \"\", \"page\": 11, \"index\": 16, \"width\": 477, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-017.webp\", \"caption\": \"\", \"page\": 11, \"index\": 17, \"width\": 476, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-018.webp\", \"caption\": \"\", \"page\": 11, \"index\": 18, \"width\": 476, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-019.webp\", \"caption\": \"\", \"page\": 11, \"index\": 19, \"width\": 476, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-020.webp\", \"caption\": \"\", \"page\": 11, \"index\": 20, \"width\": 476, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-021.webp\", \"caption\": \"\", \"page\": 11, \"index\": 21, \"width\": 476, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6e3a40f2fa580737e67a3eb4/fig-022.webp\", \"caption\": \"\", \"page\": 11, \"index\": 22, \"width\": 477, \"height\": 268}]"
motivation: "现有VLA模型的视觉令牌剪枝仅依赖浅层线索,容易丢弃深层所需的视觉信息,影响机器人实时控制的稳定性。"
method: "提出SAFE-Pruner插件式框架,将未来层语义注意力作为剪枝依据,通过语义注意力一致性实现前瞻式令牌选择。"
result: 在多个机器人操作任务上加速推理的同时保持甚至提升了原始VLA策略的任务成功率。
conclusion: "为VLA模型的高效部署提供了通用加速方案,推动通用视觉-动作策略走向实时机器人控制应用。"
---

## Abstract
Real-time inference of vision–language–action (VLA) models is essential for robotic control. While visual token pruning has shown strong potential for accelerating inference, most existing methods mainly base pruning decisions on shallow-layer cues and risk discarding visual information required by deep layers. To address this issue, we propose SAFE-Pruner, a plug-and-play pruning framework that incorporates attention cues of future layers into pruning decisions. Specifically, we identify semantic attention consistency, the tendency that VLA models concentrate their attention probability mass on the same semantic entity across control timesteps. Based on this observation, we design a forwardlooking strategy to forecast the token saliency in deep layers, which prevents the premature removal of critical tokens and leads to more stable acceleration. We further introduce a reference timestep refresh strategy that triggers updates upon attention shifts, thereby improving forecasting accuracy and pruning reliability. Extensive experiments across diverse evaluation settings demonstrate that our method achieves up to 1.89× speedup with a minimal degradation in success rate of less than 1.5%, while outperforming state-of-the-art methods by up to 1.9%.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "SAFE-Pruner: Semantic Attention–Guided Future-Aware Token Pruning for Efficient Vision-Language-Action Manipulation" following a specific structure. Let me analyze the paper carefully and produce a well-organized summary.

The paper is about accelerating Vision-Language-Action (VLA) models through a novel token pruning framework. Let me organize my thoughts:

1. Core problem: VLA models have heavy computational overhead and high inference latency, hindering real-time robotic control. Existing token pruning methods rely on shallow-layer cues and may discard tokens critical for deep layers.

2. Method: SAFE-Pruner, a plug-and-play framework that:
- Identifies "semantic attention consistency" - VLA models attend to the same semantic entities across control timesteps
- Future-aware token pruning: predicts late-stage token saliency using historical keyframe information
- Adaptive key timestep selection: refreshes reference when attention shifts are detected
- Uses cosine similarity to match visual tokens between current frame and reference keyframe
- Fusion formula: s_t = (1-λ) * S^ℓs_t + λ * Ŝ^Ld_t

3. Experiments:
- Models: OpenVLA, OpenVLA-OFT, CogACT, π0.5
- Benchmarks: LIBERO (4 suites, 2000 episodes), SIMPLER (Visual Matching and Variant Aggregation), real robot on Astribot S1
- Comparisons: FastV, SparseVLM, DivPrune, VLA-Cache, VLA-Pruner
- Metrics: Success rate, FLOPs, latency

4. Resources: 
- Latency measured on NVIDIA RTX 4090 (for simulation) and RTX 3090 (for real robot)
- No explicit training compute mentioned

5. Experiment thoroughness:
- Main results on 3 different VLAs across 4 LIBERO suites
- SIMPLER benchmark with CogACT
- Real robot experiments with 3 tasks, 200 trials each
- Ablation study (4 configurations)
- Compatibility test with HiF8 quantization
- Quite comprehensive

6. Conclusions:
- Achieves up to 1.89× speedup with <1.5% success rate drop
- Outperforms SOTA by up to 1.9%
- Compatible with quantization methods
- Identifies new attention dynamics insight

7. Strengths:
- Novel observation about semantic attention consistency
- Forward-looking pruning strategy
- Adaptive reference selection
- Cross-architecture generalization
- Comprehensive experiments including real-world

8. Limitations:
- Real robot only on one platform (Astribot S1)
- Limited to specific VLA backbones (though 4 are tested)
- Semantic consistency may break down in complex multi-stage tasks
- Latency overhead from saliency computation not deeply analyzed
- Only tested on manipulation tasks, not other robotic applications

Let me write this in Chinese following the requested structure.</think>

# SAFE-Pruner 论文总结

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（VLA）模型通过统一视觉感知、语言理解和动作生成，已成为通用机器人操作的热门范式，但其庞大的计算开销与高推理延迟严重制约了实时机器人控制（尤其在动态场景中）。
- **现有方法的局限**：传统加速手段（蒸馏、量化、层剪枝等）通常需要重新训练或修改架构，泛化能力受限；而视觉令牌剪枝虽是无训练的轻量化方案，却普遍存在 **"短视剪枝"问题**：
  - 大多数方法仅依赖浅层（早期）的注意力或相似度信号做剪枝决策；
  - 由于 VLA 单次动作生成涉及多层 Transformer 由浅入深的特征精炼，在浅层看似不重要的视觉令牌可能在深层变得关键，过早丢弃会显著损害性能；
  - 部分改进方法尝试从已被剪枝的子集估计深层显著性，但关键令牌可能已被不可逆地移除。
- **本文关注的核心问题**：如何在不重新训练的前提下，利用未来层（深层）的推理线索指导剪枝决策，避免过早丢弃对后续推理至关重要的视觉令牌？

## 2. 方法论

### 2.1 预备：基于注意力的令牌显著性

- 在浅层 ℓs 计算 query→key（query 设为 action token）的缩放点积注意力：
$$A^{\ell_s} = \text{Softmax}\left(\frac{Q^{\ell_s}(K^{\ell_s})^\top}{\sqrt{d}}\right) \in \mathbb{R}^{N_h \times L_{query} \times L_{vis}}$$
- 对所有注意力头与 query token 求平均，得到每个视觉令牌的显著性分数 $S^{\ell_s} \in \mathbb{R}^{L_{vis}}$；
- 保留 top-K 显著性令牌，其余丢弃。**该剪枝操作不可逆**，因此如何选对至关重要。

### 2.2 关键观察：VLA 的注意力动态

作者通过分析 OpenVLA-OFT 的注意力演化得到三点洞见：

1. **层内注意力的"由粗到细"**：浅层注意力分散、覆盖广；深层注意力更局部、聚焦。在 70% 以上的激进剪枝率下，"仅靠浅层显著性"会令核心令牌（深层 top-10%）丢失率急剧上升。
2. **跨控制步的语义一致性**：执行同一任务时，即便目标空间位置变化（如夹爪移动），同一推理阶段的注意力几乎稳定地锚定在相同的语义实体上（待抓取物体等）。这构成了"未来注意力预测"的理论基础。
3. **子任务边界处注意力突变**：当子任务切换（如"pick up"→"place"）时，注意力会从一种语义实体突然转移到另一种（如物体→目标盒），此时历史显著性会失效甚至有害。

### 2.3 Future-Aware Token Pruning（前瞻式剪枝）

- **关键时间步（Key Timestep）**：在某些控制步 τ 上不做剪枝，完整运行前向，缓存所有层的全令牌显著性 $\{S^\ell_\tau, \ell=0..L-1\}$；
- **非关键步**：在浅层 ℓs 处计算当前步的浅层显著性 $S^{\ell_s}_t$；
- **预测深层显著性**：以最近的关键步 $\tau_{ref}=\max\{\tau\in T_{key}:\tau<t\}$ 为参考，通过视觉令牌之间的余弦相似度建立"语义对应关系"，将参考步的全层显著性 $\{S^\ell_{\tau_{ref}}\}$ 转移到当前步，记为 $\{\hat{S}^\ell_t\}$；
- **聚合深层预测**：对一组深层集合 $\mathcal{L}_D$ 取均值：$\hat{S}^{\mathcal{L}_D}_t = \frac{1}{|\mathcal{L}_D|}\sum_{\ell\in\mathcal{L}_D}\hat{S}^\ell_t$；
- **分数融合**：$s_t = (1-\lambda)S^{\ell_s}_t + \lambda \hat{S}^{\mathcal{L}_D}_t$，并基于 $s_t$ 选 top-K 令牌。该策略兼顾当前与未来阶段的显著性，避免过早丢失关键令牌。

### 2.4 Adaptive Key Timestep Selection（自适应关键步选择）

- 用浅层显著性 $S^{\ell_s}_t$ 作为当前注意力模式的轻量代理；
- 计算其与预测显著性 $\hat{S}^{\ell_s}_t$ 的余弦相似度 $\kappa_t$；
- 当 $\kappa_t < \gamma$（阈值）时判定发生了注意力漂移/突变，将当前步升级为关键步，跳过剪枝并刷新参考缓存；
- 否则继续使用 $\tau_{ref}$ 复用以最大化加速。
- 该机制可减少不必要的全令牌推理，并保证预测只在"语义一致"的窗口内有效。

## 3. 实验设计

### 3.1 基础模型（覆盖主流架构族）

- **OpenVLA**：token-based、离散动作的自回归 VLA；
- **OpenVLA-OFT**：并行解码 + 动作块 + 连续动作回归；
- **CogACT**：视觉/语言与扩散式动作头解耦的组合化 VLA；
- **π0.5**：VLM 骨干 + flow-matching 动作专家。

### 3.2 基准与场景

| 基准 | 模型 | 说明 |
|---|---|---|
| **LIBERO** | OpenVLA / OpenVLA-OFT / π0.5 | 4 个子套件（Space / Object / Goal / Long），每套 10 任务×50 episode，共 2000 episode |
| **SIMPLER** | CogACT | Google 机器人臂，Visual Matching 与 Variant Aggregation 两个域偏移设定 |
| **真实机器人** | π0.5 | Astribot S1 双 7-DoF 臂平台 + 头/腕 RGB 相机，3 任务：Pick-and-Place（10 物体）、Throw Basketball（精细抓取）、Pack Doll（长时序多阶段），每任务 200 次试验 |

### 3.3 对比方法

- VLM 加速类：**FastV、SparseVLM、DivPrune**；
- VLA 专用加速类：**VLA-Cache、VLA-Pruner**；
- 基线：未加速的 vanilla 模型；
- 所有基线均经过同环境下超参调优以保证公平性。

### 3.4 评估指标

- 任务成功率（SR%）、FLOPs（T）、VLM 骨干延迟（ms）。

## 4. 资源与算力

- **未提及训练算力**：SAFE-Pruner 是训练无关（training-free）的即插即用方案，论文未说明基础模型训练所用的 GPU 类型/数量/时长；
- **推理延迟测量**：
  - 仿真/基准：NVIDIA **RTX 4090**；
  - 真实机器人：NVIDIA **RTX 3090**；
- 报告的延迟已对所有附加开销（含关键步全令牌推理与显著性预测）取平均，比较客观。

## 5. 实验数量与充分性

- **主结果**：
  - LIBERO 上 3 个模型 × 4 子套件 × 5 个加速方法 + vanilla = 大量对比；
  - SIMPLER 上 CogACT 在 2 种域偏移下与 4 个加速方法比较；
  - 真实机器人 3 个任务 ×（vanilla / FastV / Ours）× 200 次试验。
- **消融实验**：4 组配置（vanilla / w/o forecast / w/o adaptivity / Ours），验证前瞻预测与自适应关键步两个组件的各自贡献。
- **兼容性实验**：与 HiF8 量化联合，验证方法可叠加。
- **可视化分析**：注意力模式差异（粗到细）、核心令牌丢失曲线、跨帧语义一致性可视化、子任务边界突变示意。
- **充分性评价**：实验覆盖了 4 种 VLA 架构、3 类基准（仿真 + 真实）、多个加速基线，并做了消融与可视化，从结构上看较为充分；不过仍存在一些可补充的方向（详见第 8 节）。

## 6. 主要结论与发现

- **新观察**：VLA 模型在连续操控过程中具有跨控制步的**语义注意力一致性**（同一任务锚定同一语义实体），为用历史帧预测当前帧深层显著性提供了依据；
- **性能-效率权衡领先**：在 LIBERO、SIMPLER、真实机器人三类基准上一致优于 SOTA；
  - 最高 **1.89×** 加速；
  - 平均成功率下降不超过 **1.5%**，部分场景甚至略超 vanilla（作者解释为过滤掉无关令牌使模型更聚焦）；
  - 在 OpenVLA-OFT 上相比最佳基线提升 **1.9%** 成功率，同时 FLOPs 从 2.126T 降到 1.722T、延迟从 50.24ms 降到 37.22ms；
- **架构无关**：在自回归、并行+chunk、扩散头、flow-matching 四类 VLA 上均稳定生效；
- **可叠加**：与 HiF8 量化联合可同时获得计算效率与显存节省（FLOPs↓56.4%、GPU 内存↓38.1%）；
- **子任务边界鲁棒**：自适应关键步策略能识别注意力漂移并刷新参考，避免过时显著性带来的累积漂移。

## 7. 优点与亮点

- **问题切入精准**：首次明确提出 VLA 视觉令牌剪枝的"短视性"问题，并给出系统化的分析与可视化证据；
- **方法优雅轻量**：基于语义对应（余弦相似度）跨帧迁移显著性，无需任何训练或额外监督信号；
- **双组件协同**：前瞻预测 + 自适应关键步刷新形成闭环，既保留性能又最大化加速比；
- **跨架构泛化**：覆盖 4 种主流 VLA 架构，验证了方法的通用性；
- **实验链条完整**：基准测试 + 真实机器人 + 消融 + 量化兼容性 + 可视化分析；
- **实用价值高**：训练无关、即插即用，对延迟敏感的实时机器人部署意义显著。

## 8. 不足与局限

- **真实机器人覆盖有限**：仅在 Astribot S1 一个平台上验证 3 个任务，未覆盖移动机器人、四足/人形平台，或光照/遮挡更强的野外场景；
- **任务多样性受限**：评测任务集中于桌面级操作（抓取、放置、装箱），未验证在长时序导航、双臂精细装配、柔性物体操作等更复杂场景下的稳定性；
- **方法假设的边界**：依赖"语义注意力一致性"假设；当任务存在大幅度场景切换、相机视角骤变或多目标竞争注意力时，跨帧语义对应可能退化，作者虽用自适应刷新缓解，但未给出理论或量化分析该假设的失效条件；
- **显著性计算开销**：浅层显著性预测、跨帧余弦匹配、关键步全令牌推理均带来额外开销；论文虽说明延迟测量包含这些成本，但未对其单项开销做分解，未来更激进的剪枝率下该开销可能成为瓶颈；
- **基线公平性风险**：所有基线在同环境下重新调优，但不同方法在"同一延迟预算"下的对照（latency-vs-SR 帕累托曲线）未完整呈现；
- **可解释性与可控性**：阈值 γ、融合权重 λ、关键步集合的判定规则均为经验设定，缺乏对超参数敏感度的系统分析（论文未给出充分的超参扫描）；
- **安全性与失败模式**：未讨论剪枝失败时（如误删核心令牌）模型的行为是否会产生不安全动作，这在真实机器人部署中是关键风险；
- **与其他正交优化的兼容性**：除量化外，未探索与 KV-cache 优化、混合精度、投机解码等的协同效应；
- **开源与复现**：论文未明确给出代码与权重的可获取情况，影响第三方复现和推广。

（完）
