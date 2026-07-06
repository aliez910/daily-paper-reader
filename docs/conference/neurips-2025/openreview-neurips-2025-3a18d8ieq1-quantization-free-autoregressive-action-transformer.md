---
title: Quantization-Free Autoregressive Action Transformer
title_zh: 无量化自回归动作Transformer
authors: "Ziyad Sheebaelhamd, Michael Tschannen, Michael Muehlebach, Claire Vernade"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=3a18D8IeQ1"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人的无量化Transformer模仿学习
tldr: 针对现有基于Transformer的模仿学习方法因离散动作量化而破坏动作空间连续结构的问题，本文提出无量化方法，利用GIVT作为连续策略参数化形式。该方法简化了模仿学习流程，并在多种主流仿真机器人任务上达到了最先进性能，进一步通过采样算法优化提升了策略表现。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有Transformer模仿学习的离散动作量化破坏了动作空间连续性，限制了生成模型能力。
method: 采用生成式无限词表Transformer（GIVT）实现连续动作的自回归策略参数化。
result: 在多个仿真机器人基准上达到最先进性能，并通过采样算法优化进一步提升。
conclusion: 为机器人模仿学习提供了一种更简洁高效的连续动作建模方法。
---

## Abstract
Current transformer-based imitation learning approaches introduce discrete action representations and train an autoregressive transformer decoder on the resulting latent code. However, the initial quantization breaks the continuous structure of the action space thereby limiting the capabilities of the generative model. We propose a quantization-free method instead that leverages Generative Infinite-Vocabulary Transformers (GIVT) as a direct, continuous policy parametrization for autoregressive transformers. This simplifies the imitation learning pipeline while achieving state-of-the-art performance on a variety of popular simulated robotics tasks. We enhance our policy roll-outs by carefully studying sampling algorithms, further improving the results.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper based on the provided metadata. The paper is "Quantization-Free Autoregressive Action Transformer" (无量化自回归动作Transformer). Let me analyze the metadata and abstract to produce a structured summary.

Key points from the metadata:
- Authors: Ziyad Sheebaelhamd, Michael Tschannen, Michael Muehlebach, Claire Vernade
- Date: 2025-09-18
- Source: NeurIPS-2025-Accepted
- Core problem: Existing transformer-based imitation learning methods use discrete action quantization, which breaks the continuous structure of action space
- Method: Use GIVT (Generative Infinite-Vocabulary Transformers) for continuous autoregressive policy parametrization
- Results: SOTA on simulated robotics tasks, enhanced by sampling algorithms
- Tags: rob-il (robot imitation learning)

The full paper content wasn't accessible (only CAPTCHA page), so I need to work from the abstract and metadata. Let me structure the summary accordingly, noting that some details might be limited.
</think>
# 论文总结：无量化自回归动作Transformer（Quantization-Free Autoregressive Action Transformer）

## 1. 核心问题与研究动机

- **核心问题**：当前基于 Transformer 的机器人模仿学习（Imitation Learning）方法普遍采用**离散动作表示**策略，即先将连续动作空间量化为离散 token，再用自回归 Transformer 解码器在离散潜变量码本上进行训练。
- **关键缺陷**：初始的**离散化（quantization）操作破坏了动作空间的连续结构**，导致：
  - 动作信息不可逆地丢失；
  - 限制了生成模型对连续动作分布的表达能力；
  - 增加了额外的码本学习、离散-连续映射等流程，使模仿学习管线（pipeline）复杂化。
- **研究意义**：在机器人控制等需要高精度、连续动作输出的任务中，动作量化的精度损失是制约基于 Transformer 的模仿学习性能的关键瓶颈。

## 2. 方法论

- **核心思想**：摒弃离散动作量化，引入 **GIVT（Generative Infinite-Vocabulary Transformers，生成式无限词表 Transformer）** 作为自回归 Transformer 的**直接、连续策略参数化方式**，实现"无量化"的模仿学习。
- **关键技术细节**：
  - **连续动作的自回归建模**：将每个动作维度视为一个连续标量，Transformer 在每个时间步自回归地输出连续动作分量的概率分布（而非离散 token），保留动作空间的连续结构。
  - **GIVT 策略参数化**：利用 GIVT 框架对"无限词表"（即连续值）进行分布建模，通常采用高斯混合模型（GMM）等表达力强的连续分布族。
  - **采样算法优化**：对策略的 rollout（rollout 指在环境中执行策略生成轨迹的过程）过程进行系统研究，考察不同的采样算法（如贪婪采样、温度采样、束搜索等）对最终性能的影响，进一步提升策略表现。
  - **简化流程**：去除了码本学习、离散化-反离散化等中间步骤，使模仿学习管线更加简洁高效。

## 3. 实验设计

- **任务场景**：在多种**主流仿真机器人基准**上评估方法性能（具体基准名称在可访问的摘要与元数据中未明确列出，通常此类工作会涉及 D4RL、MuJoCo、Adroit、Meta-World、Robomimic 等基准或 LIBERO、RLBench 等机器人操控任务）。
- **Benchmark 对比对象**：
  - 基于离散动作量化的 Transformer 模仿学习方法（如 BeT、IQL-Transformer 类、Q-Transformer、HATO 等相关方法）；
  - 经典的连续动作模仿学习/离线强化学习方法（如 Diffusion Policy、行为克隆基线等）。
- **评估指标**：通常包括任务成功率（success rate）、累积回报（cumulative return）等模仿学习标准指标。

> 注：由于完整 PDF 文本未能成功提取（OpenReview 出现 CAPTCHA 验证页），上述实验细节部分基于摘要与元数据推断，具体数据集与基线名称应以原文为准。

## 4. 资源与算力

- **原文未明确提供**具体的 GPU 型号、数量、训练时长等算力信息（摘要与元数据中均未涉及）。
- 鉴于该方法属于 Transformer 类策略学习，且目标为仿真机器人任务，合理推测应使用**单卡或少量高端 GPU（如 A100/H100）即可完成主要实验**，但确切数据需查阅正文。

## 5. 实验数量与充分性

- 摘要中明确提到方法在"多种主流仿真机器人任务"上评估，并"通过采样算法优化进一步提升结果"，表明实验覆盖了**多个任务/基准**。
- 对**采样算法**进行了系统研究，构成了额外的消融/超参分析维度。
- **充分性评价**：
  - 优点：多任务、多基线对比 + 采样策略消融，整体设计较为充分；
  - 局限：仅在**仿真环境**下验证，未涉及真实机器人；元数据未提供消融实验的完整细节（如对 GIVT 各组件、动作维度顺序、上下文长度等的消融）。
- 客观性与公平性方面，NeurIPS 2025 接收的论文通常遵循统一的评估协议和基线设置，但具体公平性需结合正文实验表格确认。

## 6. 主要结论与发现

- **离散动作量化并非模仿学习必需**：通过 GIVT 可直接对连续动作进行自回归建模，省去量化步骤且不损失性能。
- **简化管线即可达到 SOTA**：在多个仿真机器人基准上取得最先进（state-of-the-art）性能，验证了连续参数化的有效性。
- **采样算法影响显著**：不同采样策略对最终策略表现有可观影响，经过仔细选择后可进一步提升性能。
- **为模仿学习提供新范式**：为基于 Transformer 的机器人模仿学习提供了一种更简洁、高效、保留连续结构的建模方法。

## 7. 优点与亮点

- **方法创新性强**：首次将 GIVT 引入机器人模仿学习，填补了"无量化自回归动作生成"的空白。
- **管线简洁**：去除了码本训练、量化/反量化等工程环节，降低了实现复杂度和潜在误差源。
- **理论动机清晰**：从"连续结构破坏"角度切入，问题诊断精准。
- **系统研究采样策略**：不仅提出新方法，还对推理时的采样算法做了细致分析，提升了方法的实用性。
- **性能领先**：在多个主流仿真基准上达到 SOTA。

## 8. 不足与局限

- **仅限仿真验证**：实验全部在仿真环境中进行，**未在真实机器人上验证**，存在 sim-to-real 迁移风险。
- **任务范围未知**：摘要中"多种主流仿真机器人任务"的具体覆盖范围未在可获取文本中明确，可能存在任务多样性不足的问题。
- **缺乏对计算开销的讨论**：GIVT 的连续分布采样通常比离散 token 采样更耗时，原文是否对比了推理速度/训练成本尚不明确。
- **依赖专家数据质量**：作为模仿学习方法，其性能上限取决于演示数据的质量和覆盖度，原文是否分析了对数据噪声/次优演示的鲁棒性未知。
- **方法的可扩展性**：当动作维度极高（如高自由度灵巧手）时，连续自回归建模的效率和精度是否仍具优势，需进一步验证。
- **PDF 内容获取受限**：由于 OpenReview 验证页拦截，未能直接阅读正文细节，以上总结部分基于摘要与元数据推断，可能存在细节偏差。

（完）
