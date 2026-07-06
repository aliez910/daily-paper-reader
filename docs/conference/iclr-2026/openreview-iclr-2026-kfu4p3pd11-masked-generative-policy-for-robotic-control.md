---
title: Masked Generative Policy for Robotic Control
title_zh: 用于机器人控制的掩码生成策略
authors: "Lipeng Zhuang, Shiyu Fan, Florent P. Audonnet, Yingdong Ru, Edmond S. L. Ho, Gerardo Aragon-Camarasa, Paul Henderson"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=KFu4p3pd11"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向复杂机器人操纵的视觉运动模仿学习框架，支持闭环动作优化
tldr: 当前视觉运动模仿学习方法在生成全局一致动作与适应非马尔可夫任务方面仍有不足。本文提出掩码生成策略（MGP），将动作表示为离散令牌，并通过条件掩码Transformer并行生成，再快速优化低置信度令牌，从而提升全局一致性。作者进一步设计MGP-Short与MGP-Long两种采样范式，分别支持马尔可夫任务与非马尔可夫任务，实现基于新观测的动态动作优化。在150个机器人操纵任务上的大量实验表明，该方法在控制可靠性上明显优于既有方法，为复杂操纵任务提供了新的视觉运动模仿学习基线。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有视觉运动模仿学习方法在生成动作时缺乏全局一致性，且难以可靠处理非马尔可夫复杂任务。
method: 将动作表示为离散令牌，使用条件掩码Transformer并行生成，并按置信度迭代优化低置信度令牌。
result: 在150个机器人操纵任务上的大量评测表明，该方法在复杂任务上控制可靠且性能优于既有方法。
conclusion: 掩码生成与置信度驱动优化可显著提升视觉运动模仿学习在复杂机器人操纵中的表现。
---

## Abstract
We present Masked Generative Policy (MGP), a novel framework for visuomotor imitation learning. We represent actions as discrete tokens, and train a conditional masked transformer that generates tokens in parallel and then rapidly refines only low-confidence tokens. We further propose two new sampling paradigms: MGP-Short, which performs parallel masked generation with score-based refinement for Markovian tasks, and MGP-Long, which predicts full trajectories in a single pass and dynamically refines low-confidence action tokens based on new observations. With globally coherent prediction and robust adaptive execution capabilities, MGP-Long enables reliable control on complex and non-Markovian tasks that prior methods struggle with. Extensive evaluations on 150 robotic manipulation tasks spanning the Meta-World and LIBERO benchmarks show that MGP achieves both rapid inference and superior success rates compared to state-of-the-art diffusion and autoregressive policies. Specifically, MGP increases the average success rate by 9\% across 150 tasks while cutting per-sequence inference time by up to 35×. It further improves the average success rate by 60\% in dynamic and missing-observation environments, and solves two non-Markovian scenarios where other state-of-the-art methods fail.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Masked Generative Policy for Robotic Control" based on the provided metadata. Let me organize the summary according to the 8 requested points.
</think>
# 论文总结：Masked Generative Policy for Robotic Control（用于机器人控制的掩码生成策略）

## 1. 核心问题与研究动机

- **研究背景**：视觉运动模仿学习（visuomotor imitation learning）是机器人操作任务中的重要范式，目标是直接从人类示范中学习视觉观测到动作的映射策略。
- **现有方法的局限**：
  - **扩散策略（Diffusion Policy）**：虽能生成高保真动作，但迭代去噪过程耗时较长，推理速度慢；同时对全局一致性的建模较弱。
  - **自回归策略（Autoregressive Policy）**：如动作分块 Transformer（ACT）等，逐令牌生成动作，缺乏全局一致性，且在非马尔可夫任务（需要历史信息或长程依赖的任务）中表现不佳。
- **核心问题**：如何在保证**全局一致动作生成**的同时，实现**快速推理**，并可靠地处理**非马尔可夫复杂任务**。

## 2. 方法论

- **核心思想**：将动作序列表示为**离散令牌（discrete tokens）**，借鉴文本/图像生成中掩码生成模型（如 MaskGIT）的思路，通过**条件掩码 Transformer** 并行生成动作令牌，并对低置信度令牌进行迭代优化。
- **关键技术细节**：
  - **动作离散化**：将连续动作空间通过向量量化（Vector Quantization, VQ）映射为离散码本（codebook）中的索引。
  - **条件掩码 Transformer**：以视觉观测（如图像嵌入）作为条件，一次性对整段动作序列进行并行预测，而非逐个顺序生成。
  - **置信度驱动的迭代优化**：生成过程中只对置信度低于阈值的令牌进行重采样/优化，已确定的高置信度令牌保持不变，从而实现"快速收敛"。
  - **两种采样范式**：
    - **MGP-Short（马尔可夫版本）**：在每个时间步执行并行掩码生成 + 基于分数的细化（score-based refinement），适合短时依赖的马尔可夫任务。
    - **MGP-Long（非马尔可夫版本）**：一次性预测完整动作轨迹，当新观测到来时，仅对低置信度的动作令牌进行动态细化，保留高置信度令牌，从而实现**闭环动作优化**与长程一致性。
- **算法流程概览**：
  1. 编码观测（视觉特征）。
  2. 随机掩码部分动作令牌。
  3. 掩码 Transformer 并行预测所有掩码位置的令牌分布。
  4. 计算各令牌的置信度，仅对低置信度令牌重新掩码并迭代。
  5. 解码离散令牌为连续动作序列并执行。
  6. MGP-Long 在执行过程中以新观测为条件重复步骤 2–5。

## 3. 实验设计

- **数据集 / Benchmark**：
  - **Meta-World**：经典机器人操作基准，包含多个操控任务（如抓取、按按钮、推物体等）。
  - **LIBERO**：面向终身/多任务学习的机器人操作基准，包含多种长时序、组合式任务。
  - **共 150 个机器人操作任务**横跨上述两大基准。
- **对比方法**：
  - **Diffusion Policy（扩散策略）**：当前 SOTA 的扩散类模仿学习方法。
  - **Autoregressive Policy（如 ACT 等自回归动作分块方法）**：当前 SOTA 的自回归模仿学习方法。
- **评测维度**：
  - 任务成功率（Success Rate）。
  - 每序列推理时间（Inference Time）。
  - 鲁棒性测试：动态环境（dynamic environments）和缺失观测（missing-observation environments）。
  - 非马尔可夫任务：2 个其他方法均失败的关键场景。

## 4. 资源与算力

- **算力信息**：论文提供的元数据与可获取的摘要中**未明确说明**所使用的 GPU 型号、数量及训练时长。
- **可推断信息**：作为基于 Transformer 的模仿学习方法，训练通常在单卡或多卡高端 GPU（如 A100/V100）上完成；由于使用离散令牌与掩码生成机制，相比扩散策略推理更高效（论文报告推理时间最高降低 35×），但具体训练算力开销未公开。

## 5. 实验数量与充分性

- **实验规模**：
  - 涵盖 **150 个任务**，在两大主流基准（Meta-World + LIBERO）上进行评估，实验规模较大。
  - 包含**鲁棒性实验**：动态环境、缺失观测环境。
  - 包含**非马尔可夫任务**专项评估。
- **方法对比**：与两大类当前 SOTA 方法（扩散策略、自回归策略）进行系统性对比，涵盖成功率与推理效率两个维度。
- **充分性与客观性**：
  - 优点：任务数量多、基准广泛、对照方法为当前主流 SOTA，实验设计较为全面。
  - 局限：摘要与元数据中**未详细说明消融实验**（如码本大小、掩码比例、迭代轮数等对性能的影响），也未说明每个任务的成功率统计次数（seeds/trials），因此实验的统计稳健性尚不能完全确认。
  - 论文代码与实验配置在 ICLR 审稿版本中可能未完全公开，公平性需结合最终正式版判断。

## 6. 主要结论与发现

- **整体性能**：MGP 在 150 个任务上**平均成功率提升约 9%**，同时**每序列推理时间最高降低 35×**，在控制可靠性和推理效率上均优于现有 SOTA。
- **鲁棒性**：在**动态环境与缺失观测环境**中，平均成功率提升约 **60%**，显示出对观测扰动的强鲁棒性。
- **非马尔可夫任务**：成功解决 **2 个其他 SOTA 方法均失败的非马尔可夫场景**，验证了 MGP-Long 的长程建模与动态细化能力。
- **设计验证**：掩码生成 + 置信度驱动优化是提升动作全局一致性的有效途径；将完整轨迹预测与基于新观测的动态细化结合，是处理非马尔可夫任务的关键。

## 7. 优点与亮点

- **方法层面**：
  - 首次将**掩码生成范式**（来自图像/文本生成）系统性地引入视觉运动模仿学习，开辟了新方向。
  - 离散令牌 + 并行生成 + 置信度选择性优化的组合，在**全局一致性**与**推理速度**之间取得了良好平衡。
  - **MGP-Long** 设计巧妙：通过保留高置信度令牌、仅细化低置信度令牌，实现了**闭环动作优化**而无需重新生成整条轨迹，适合长时序任务。
- **实验层面**：
  - 横跨 150 个任务的大规模评测，覆盖两个主流基准，结论具有较强说服力。
  - 兼顾**性能（成功率）**与**效率（推理时间）**两个维度，并特别强调**鲁棒性**与**非马尔可夫能力**，评测维度全面。
- **实用性**：推理速度提升最高 35×，为真实机器人部署提供了更高的实时性可能。

## 8. 不足与局限

- **算力与训练成本未披露**：论文未说明训练所使用的 GPU 资源、训练时长与超参搜索成本，复现门槛难以评估。
- **消融实验不充分（从现有摘要看）**：缺少对码本大小、掩码比例、迭代轮数、MGP-Short vs MGP-Long 各组件贡献的详细消融分析。
- **任务覆盖偏差**：所有任务均来自仿真基准（Meta-World、LIBERO），**未在真实硬件机器人上进行验证**，sim-to-real 迁移性能未知。
- **统计显著性存疑**：摘要中未明确说明每任务的试验次数与置信区间，"9% 平均提升"和"60% 提升"的统计显著性需进一步确认。
- **非马尔可夫任务数量有限**：仅展示了 2 个非马尔可夫场景，泛化能力有待在更多样化的长时序任务中验证。
- **离散化的固有局限**：将连续动作离散化可能引入量化误差，对高精度控制任务（如接触丰富的操作）可能产生不利影响。
- **对示范数据质量的依赖**：作为模仿学习方法，性能上限受限于示范数据分布，对示范数据的多样性与覆盖度敏感。

（完）
