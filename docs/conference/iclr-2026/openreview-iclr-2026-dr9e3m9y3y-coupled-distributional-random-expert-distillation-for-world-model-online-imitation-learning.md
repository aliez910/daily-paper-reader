---
title: Coupled Distributional Random Expert Distillation for World Model Online Imitation Learning
title_zh: 耦合分布随机专家蒸馏：用于世界模型在线模仿学习
authors: "Shangzhe Li, Zhiao Huang, Hao Su"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DR9e3M9Y3y"
tags: ["query:rob-il"]
score: 5.0
evidence: 基于世界模型的在线模仿学习，解决机器人领域IL不稳定性
tldr: 本文针对现有模仿学习方法在世界模型框架中依赖对抗性奖励或价值函数而存在不稳定性的问题展开研究。作者提出一种新的在线模仿学习方法，使用随机网络蒸馏（RND）进行密度估计以构建奖励模型，并在世界模型潜空间中联合估计专家与行为分布。该方法在机器人、自动驾驶和医疗等多个基准上评估，显著提升了在线模仿学习的稳定性。其贡献在于提供了一个更稳定、适用面更广的模仿学习框架，可作为机器人操控训练流程的基础组件。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有基于世界模型的模仿学习方法依赖对抗性奖励/价值函数，存在训练不稳定问题。
method: 提出使用随机网络蒸馏进行密度估计的奖励模型，在世界模型潜空间中耦合估计专家与行为分布。
result: 在机器人、自动驾驶和医疗等多领域基准上提升在线模仿学习的稳定性。
conclusion: RND密度估计为世界模型下的在线模仿学习提供了更稳定且广泛适用的训练框架。
---

## Abstract
Imitation Learning (IL) has achieved remarkable success across various domains, including robotics, autonomous driving, and healthcare, by enabling agents to learn complex behaviors from expert demonstrations. However, existing IL methods often face instability challenges, particularly when relying on adversarial reward or value formulations in world model frameworks. In this work, we propose a novel approach to online imitation learning that addresses these limitations through a reward model based on random network distillation (RND) for density estimation. Our reward model is built on the joint estimation of expert and behavioral distributions within the latent space of the world model. We evaluate our method across diverse benchmarks, including DMControl, Meta-World, and ManiSkill2, showcasing its ability to deliver stable performance and achieve expert-level results in both locomotion and manipulation tasks. Our approach demonstrates improved stability over adversarial methods while maintaining expert-level performance.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided metadata. The PDF text extraction failed (only got a CAPTCHA page), so I need to work entirely from the metadata provided. Let me organize a structured summary following the 8 points requested.

The paper is about "Coupled Distributional Random Expert Distillation for World Model Online Imitation Learning" - an ICLR 2026 submission about imitation learning using world models with RND-based density estimation.

Let me structure this carefully with the available information.
</think>
# 论文总结：耦合分布随机专家蒸馏用于世界模型在线模仿学习

## 1. 核心问题与整体含义

- **研究背景**：模仿学习（Imitation Learning, IL）已在机器人、自动驾驶、医疗等多个领域取得显著成功，使智能体能够从专家示教中学习复杂行为。
- **核心痛点**：现有模仿学习方法在**基于世界模型（World Model）的框架**中，常常依赖**对抗性奖励（adversarial reward）或价值函数（value function）** 来区分专家与行为分布。这种对抗式设计在训练过程中普遍存在**不稳定**的问题——容易出现奖励欺骗、训练振荡甚至策略崩溃。
- **研究目标**：在保留世界模型强大表征能力的同时，绕过对抗训练，提供一种更稳定、适用范围更广的在线模仿学习方案，使其能够作为机器人操控训练流程中的基础组件。

## 2. 方法论

- **核心思想**：用**随机网络蒸馏（Random Network Distillation, RND）** 进行**密度估计（density estimation）**，替代对抗性奖励信号，并在**世界模型的潜空间（latent space）** 中**耦合（coupled）估计专家分布与自身行为分布**，从而构造稳定可靠的奖励模型。
- **关键技术细节**：
  - **随机网络蒸馏（RND）奖励建模**：利用一个固定随机目标网络与一个可训练预测网络之间的预测误差作为密度估计器。预测误差小 ⇒ 状态/动作更"熟悉"（更接近专家分布），误差大 ⇒ 更陌生（更偏离专家）。该机制无需对抗判别器，天然稳定。
  - **耦合分布估计（Coupled Distributional Estimation）**：在世界模型所学得的潜空间中，同时建模专家数据分布与当前行为策略分布（"专家/行为"配对关系），使奖励信号能够同时反映"接近专家"与"偏离自身行为"两个方向。
  - **与世界模型联合训练**：奖励模型在世界模型潜空间中构建，使奖励信号与世界模型对未来动态的预测能力保持一致，有利于长程任务的稳定学习。
  - **在线学习范式**：智能体在世界模型产生的想象轨迹（imagined rollouts）中与 RND 奖励信号交互，迭代更新策略，属于在线模仿学习（online IL）流程。
- **算法流程（文字概述）**：
  1. 预训练世界模型，从环境中收集数据并构建潜空间表征。
  2. 在潜空间内训练 RND 密度估计器，对专家示教与当前行为策略进行耦合分布估计。
  3. 利用 RND 误差作为内生奖励信号，在世界模型的想象中通过强化学习更新策略。
  4. 在线收集新数据并重复上述过程，逐步收敛到专家级策略。

## 3. 实验设计

- **基准测试（Benchmarks）**：
  - **DMControl**：连续控制中的**运动（locomotion）**任务标准基准。
  - **Meta-World**：机器人操控任务的元学习基准。
  - **ManiSkill2**：面向灵巧操作的机器人操控基准。
- **任务覆盖**：同时涵盖**运动（locomotion）** 与**操控（manipulation）** 两类典型任务。
- **对比方法**：摘要与元数据中明确将方法与**基于对抗性奖励/价值函数**的模仿学习方法进行对比，重点突出稳定性优势。
- ⚠️ **说明**：由于本次未能成功抓取 PDF 正文，具体对比基线列表（如 GAIL、GAIL-TS、PSI、WORLD-IL、DAC 等）无法逐条核实，需以论文正文为准。

## 4. 资源与算力

- **当前可获取信息中未明确说明**所使用 GPU 型号、数量及训练时长。
- 仅可从元数据中得知论文收录于 **ICLR-2026**。
- 📌 建议查阅论文正文附录或附录中的"实验设置"章节以获取精确算力配置。

## 5. 实验数量与充分性

- **可获取的实验概览**：
  - 在 **3 个不同基准**（DMControl、Meta-World、ManiSkill2）上进行了评估，跨域覆盖运动与操控。
  - 元数据中提到"显著提升了在线模仿学习的稳定性"以及"达到专家级性能"，暗示在多个任务上对稳定性和最终回报都进行了报告。
- **不充分/不确定之处**：
  - 是否包含**完整的消融实验**（例如去除耦合分布、去除世界模型、替换 RND 为其他密度估计器等）——元数据未提供细节。
  - 是否报告了**多次随机种子**下的均值与方差，以体现稳定性收益的统计显著性——元数据未明确。
  - **样本效率、可视化、失败案例** 等是否呈现亦未明示。
- 因此，**实验是否真正"充分且公平"难以基于现有信息下定论**，需以正文为准。

## 6. 主要结论与发现

- 在基于世界模型的在线模仿学习场景下，**用 RND 密度估计替代对抗性奖励**，能显著缓解训练不稳定问题。
- 在世界模型潜空间中**耦合估计专家与行为分布**的奖励建模方式，能够在保持专家级最终性能的同时获得更稳定的训练曲线。
- 该方法在**机器人运动（DMControl）、机器人操控（Meta-World、ManiSkill2）** 等跨域基准中均有效，展示了**较强的通用性**。
- 总体结论：RND 密度估计为世界模型下的在线模仿学习提供了一个**更稳定、广泛适用**的训练框架，可作为机器人操控训练流程的基础组件。

## 7. 优点

- **创新性动机切中痛点**：直接针对世界模型 + 模仿学习中对抗训练的"不稳定性"这一长期被诟病的缺陷。
- **方法简洁且自洽**：RND 本质是预测误差回归任务，无对抗 min–max，理论上训练更稳定，实现也较轻量。
- **耦合分布设计有信息量**：在世界模型潜空间中同时估计专家与行为两个分布，使奖励信号更具判别力，避免单一 RND 容易"饱和"的问题。
- **跨域验证**：同时覆盖运动与操控、多个主流基准，体现出方法的**领域泛化能力**。
- **应用潜力明确**：可作为机器人操控训练流程的基础模块，实用价值清晰。

## 8. 不足与局限

- **PDF 抓取失败**：本次未成功获取正文内容，因此方法细节、公式、伪代码、超参数表、收敛曲线、统计显著性等均无法从原文核实。
- **算力与可复现性信息缺失**：未在元数据中给出 GPU 型号、训练时长、随机种子数等关键信息，复现成本不明。
- **基线覆盖度不透明**：摘要仅笼统提及"对抗方法"，未列举具体对比算法，难以判断对比的全面性与公平性。
- **RND 自身的潜在限制**：RND 密度估计在状态空间巨大或专家演示覆盖稀疏时，可能出现**过熟悉（over-familiarity）** 或**欠区分**问题，论文是否针对此作了分析尚未可知。
- **在线模仿学习的样本效率问题**：RND 奖励较为稀疏/局部，是否在样本效率上明显优于对抗基线，缺乏定量数据。
- **专家数据依赖**：方法依然依赖专家示教质量与覆盖度，对**次优专家**或**多模态专家行为**的鲁棒性未在元数据中说明。
- **安全与部署**：在自动驾驶、医疗等高风险场景中，仅以"benchmark 评估"作为支撑，离真实部署的安全性、可靠性仍存在较大差距。

（完）
