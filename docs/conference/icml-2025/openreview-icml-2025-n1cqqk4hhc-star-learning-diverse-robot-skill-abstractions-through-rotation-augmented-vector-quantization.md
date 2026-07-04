---
title: "STAR: Learning Diverse Robot Skill Abstractions through Rotation-Augmented Vector Quantization"
title_zh: STAR：通过旋转增强向量量化学习多样机器人技能抽象
authors: "Hao Li, Qi Lv, Rui Shao, Xiang Deng, Yinchuan Li, Jianye HAO, Liqiang Nie"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=n1cqQK4hhC"
tags: ["query:rob-il"]
score: 6.0
evidence: 通过旋转增强VQ-VAE学习机器人操纵技能抽象
tldr: 现有基于VQ-VAE的技能抽象方法面临码本折叠和技能因果建模困难。本文提出STAR框架，通过旋转增强残差量化防止码本折叠，并改进技能组合。在机器人操作任务中，STAR学习到更丰富、可组合的技能，提升了复杂行为的表现。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有技能抽象方法存在码本折叠和技能因果关系建模不足。
method: 引入旋转增强残差量化，利用编码器输出的相对角度信息改善码本学习。
result: 在多个操作基准上表现出更优的技能多样性和任务完成率。
conclusion: STAR促进了技能抽象的可扩展性和下游任务的可组合性。
---

## Abstract
Transforming complex actions into discrete skill abstractions has demonstrated strong potential for robotic manipulation.Existing approaches mainly leverage latent variable models, e.g., VQ-VAE, to learn skill abstractions through learned vectors (codebooks), while they suffer from codebook collapse and modeling the causal relationship between learned skills. To address these limitations, we present **S**kill **T**raining with **A**ugmented **R**otation (**STAR**), a framework that advances both skill learning and composition to complete complex behaviors. Specifically, to prevent codebook collapse, we devise rotation-augmented residual skill quantization (RaRSQ).It encodes relative angles between encoder outputs into the gradient flow by rotation-based gradient mechanism. Points within the same skill code are forced to be either pushed apart or pulled closer together depending on gradient directions.Further, to capture the casual relationship between skills, we present causal skill transformer (CST) which explicitly models dependencies between skill representations through an autoregressive mechanism for coherent action generation.Extensive experiments demonstrate the superiority of STAR on both LIBERO benchmark and realworld tasks, with around 12% improvement over the baselines.

---

## 论文详细总结（自动生成）

# STAR：通过旋转增强向量量化学习多样机器人技能抽象 —— 论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **背景**：将连续动作离散化为技能抽象（skill abstraction）是机器人操作领域的一种有效范式，现有方法多依赖隐变量模型（如 VQ-VAE）通过学习码本（codebook）来获得技能表示。
- **核心问题**：
  - **码本折叠（codebook collapse）**：部分码本向量得不到更新或利用，导致学习到的技能多样性降低。
  - **技能因果建模不足**：生成的技能序列缺乏对技能之间因果依赖关系的显式建模，影响长程任务的连贯性。
- **本文目标**：提出 **STAR（Skill Training with Augmented Rotation）** 框架，同时改进技能学习和技能组合，以完成更复杂的操作行为。

## 2. 论文提出的方法论：核心思想、关键技术细节与流程
- **整体框架**：STAR 包含两个主要组件：旋转增强残差技能量化（RaRSQ）和因果技能 Transformer（CST）。
- **旋转增强残差技能量化（RaRSQ）**：
  - 核心思想：利用编码器输出向量间的**相对角度**来引导码本学习，从而防止码本折叠。
  - 关键机制：在梯度流中引入基于旋转的梯度机制（rotation-based gradient mechanism），对于落入同一技能码本内的数据点，根据梯度方向使它们**相互推开或拉近**，从而保持码本内样本的区分度与紧凑性。
  - 具体实现：通过旋转操作将角度信息注入损失函数的梯度中，使得码本学习不仅依赖向量范数，还依赖方向信息。
- **因果技能 Transformer（CST）**：
  - 核心思想：采用自回归机制显式建模技能表示之间的**因果依赖关系**，保证生成的技能序列在时序上具有连贯性。
  - 实现方式：以已生成的技能序列为条件，预测下一个技能，从而优化技能组合的任务完成能力。

（注：公式或算法流程在现有资料中未提供详细数学推导，上述描述基于摘要和元数据中的方法摘要。）

## 3. 实验设计
- **基准（Benchmark）**：
  - **LIBERO benchmark**：一个广泛使用的机器人操作任务集合，包含多种日常操作场景。
  - **真实世界任务（real-world tasks）**：在物理机器人上进行的实际操纵实验。
- **对比方法**：未具体列出基线模型名称，但指出相比基线方法（可能包括标准 VQ-VAE 等技能抽象方法）平均提升约 **12%**。
- **评估指标**：任务完成率（success rate）等。

## 4. 资源与算力
- **未明确说明**：论文中未提及使用的 GPU 型号、数量或训练时长等信息。现有内容无法评估计算资源消耗情况。

## 5. 实验数量与充分性
- **已有实验**：
  - 在 LIBERO 基准上多个任务场景的评估；在真实机器人上进行实物验证。
  - 可能包含消融研究：但摘要未详细列出消融数量，元数据中未提及具体消融结果。
- **充分性评价**：
  - 实验覆盖了模拟环境和真实场景，具有一定**客观性**。
  - 但与典型顶会论文相比，实验细节（如任务数量、基线具体结果、统计显著性等）缺乏详尽说明，**无法全面判断**实验的完整性和公平性。这可能是由于本文基于摘要提供的信息有限。

## 6. 论文的主要结论与发现
- STAR 框架成功缓解了码本折叠问题，学习到的技能抽象更加**多样化**且**可组合**。
- CST 因果建模有效提升了长程操作任务的连贯性和成功率。
- 在 LIBERO 和真实任务上均取得显著提升，平均约 **12%** 的优势证明了方法的有效性。
- 结论指出 STAR 促进了技能抽象的可扩展性与下游任务的可组合性。

## 7. 优点
- **方法创新**：
  - 提出旋转增强梯度机制解决码本折叠，思想新颖，可迁移至其他量化模型。
  - 将因果 Transformer 集成到技能组合中，强化了时域依赖建模。
- **实验验证**：既包含标准模拟基准，又有真实机器人实验，增强了结果的说服力。
- **性能提升**：相对基线有明显改进（约12%），效果较为突出。

## 8. 不足与局限
- **资源开销未知**：旋转梯度计算和因果 Transformer 可能带来额外计算负担，但未提供训练或推理时间分析。
- **实验报告不够充分**：
  - 未给出具体消融实验设置和结果，难以判断各组件贡献。
  - 基线方法仅为概括性描述，未展示多个对比算法的得分。
  - 未报告不同复杂度任务下的性能差异，缺乏对泛化能力的深入分析。
- **应用限制**：方法可能假设技能码本规模固定，且旋转机制对低维动作空间是否依然有效未讨论。
- **潜在偏差风险**：真实世界任务的具体设置（如机器人型号、任务数量、演示来源）未公开，可能影响复现性。

（完）
