---
title: "Noise-conditioned Energy-based Annealed Rewards (NEAR): A Generative Framework for Imitation Learning from Observation"
title_zh: NEAR：噪声条件能量退火奖励的观察模仿学习生成框架
authors: "Anish Abhijit Diwan, Julen Urain, Jens Kober, Jan Peters"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=DL9txImSzm"
tags: ["query:rob-il"]
score: 7.0
evidence: 基于生成式模型的复杂机器人运动模仿学习框架
tldr: 本文提出 NEAR，一种基于能量生成模型的模仿学习框架，能够仅依靠状态级专家轨迹学习复杂、物理依赖的机器人运动策略。其核心通过对专家数据分布进行多级扰动并利用去噪得分匹配学习能量函数，将其作为 RL 奖励进行模仿。实验表明该方法能稳定模仿多种复杂运动，且无需动作标签。该工作为复杂机器人行为的模仿提供了新的生成式学习路径。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 复杂机器人运动模仿通常需要动作标签，难以从纯状态轨迹中学习。
method: 提出基于能量生成模型的 NEAR 框架，通过多级扰动数据分布与得分匹配学习奖励。
result: 在多种复杂机器人运动任务上实现稳定的观察模仿学习。
conclusion: 为无动作标签条件下的复杂机器人运动模仿学习提供了有效生成式方案。
---

## Abstract
This paper introduces a new imitation learning framework based on energy-based generative models capable of learning complex, physics-dependent, robot motion policies through state-only expert motion trajectories. Our algorithm, called Noise-conditioned Energy-based Annealed Rewards (NEAR), constructs several perturbed versions of the expert's motion data distribution and learns smooth, and well-defined representations of the data distribution's energy function using denoising score matching. We propose to use these learnt energy functions as reward functions to learn imitation policies via reinforcement learning. We also present a strategy to gradually switch between the learnt energy functions, ensuring that the learnt rewards are always well-defined in the manifold of policy-generated samples. We evaluate our algorithm on complex humanoid tasks such as locomotion and martial arts and compare it with state-only adversarial imitation learning algorithms like Adversarial Motion Priors (AMP). Our framework sidesteps the optimisation challenges of adversarial imitation learning techniques and produces results comparable to AMP in several quantitative metrics across multiple imitation settings.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Noise-conditioned Energy-based Annealed Rewards (NEAR): A Generative Framework for Imitation Learning from Observation" based on the provided metadata and abstract. I need to follow the specific structure with 8 sections, use Markdown formatting, and end with "（完）".

Let me analyze what's available:
- The PDF content shows a CAPTCHA page, so I only have the metadata and abstract
- The paper is about imitation learning from observation (no action labels)
- Uses energy-based generative models with denoising score matching
- Compares with AMP (Adversarial Motion Priors)
- Tested on humanoid tasks: locomotion and martial arts
- ICLR 2025 accepted
- Score 7.0

Since the PDF is inaccessible (CAPTCHA), I should be honest about the limitations of my summary based only on the abstract and metadata. I'll extract what I can from the abstract and infer carefully where needed, making clear what is direct from the paper vs. inference.

Let me structure this properly in Chinese with Markdown.</think>

# NEAR 论文中文总结

## 1. 核心问题与整体含义

- **研究背景**：模仿学习（Imitation Learning, IL）是让智能体通过专家示范学习策略的重要范式。然而传统的模仿学习算法（如行为克隆、GAIL 等）通常需要"动作标签"（state-action 配对数据），而现实中很多运动捕捉数据（如 mocap、人类演示视频）仅有状态轨迹而无动作标签。
- **核心问题**：如何仅依赖**状态级专家轨迹**（Imitation from Observation, IfO）学习复杂、物理依赖的机器人运动策略？特别是复杂类人机器人运动（如行走、武术动作）。
- **现有方法的痛点**：以 Adversarial Motion Priors（AMP）为代表的状态级对抗模仿方法虽有效，但继承了对抗训练固有的训练不稳定、模式坍塌、奖励难以调试等优化难题。
- **研究目标**：提出一种基于**生成式模型**而非对抗训练的模仿学习框架，绕过对抗优化的不稳定性。

## 2. 方法论

- **整体框架**：噪声条件能量退火奖励（NEAR），将"学习专家数据分布的能量函数"作为强化学习奖励信号，从而把模仿问题转化为带奖励的 RL 问题。
- **核心思想**：
  - 构造**多级（多尺度）扰动版本的专家数据分布**——对专家轨迹添加不同强度的高斯噪声。
  - 利用**去噪得分匹配（Denoising Score Matching, DSM）** 学习每个噪声层级对应的能量函数（得分场/score function）。
  - 不同噪声层级产生不同"光滑度"的能量地形（高噪声 → 平滑但粗糙；低噪声 → 精细但可能定义不清）。
- **关键技术**：
  1. **噪声条件得分估计**：训练一个得分网络 $s_\theta(x, \sigma)$，在不同噪声尺度 $\sigma$ 下估计 $\nabla_x \log p_{\sigma}(x)$。
  2. **能量作为奖励**：将学到的能量（或负得分）作为奖励信号 $r(x) \approx -\nabla_x \log p_{\sigma}(x) \cdot \text{something}$，提供给下游 RL 算法（如 PPO）。
  3. **退火（Annealing）策略**：在训练过程中**渐进式切换不同噪声层级的能量函数**，保证策略生成的样本始终落在能量函数良好定义的流形区域，避免低噪声能量函数在策略分布偏离专家时出现未定义/极端值。
- **算法流程（文字概述）**：
  1. 收集或加载专家状态轨迹数据集。
  2. 在多个噪声水平下扰动数据，训练条件得分/能量模型。
  3. 在 RL 训练循环中，先使用粗粒度（高噪声）能量作为引导，待策略靠近专家分布后再切换到细粒度（低噪声）能量。
  4. 用所得奖励信号驱动 RL 学习（通常为 PPO），得到模仿策略。

## 3. 实验设计

- **任务/场景**：复杂类人机器人任务，包含：
  - **运动（locomotion）**：如行走、跑动等基础运动。
  - **武术动作（martial arts）**：复杂的物理依赖动作序列。
- **数据集**：使用 mocap 类专家运动数据集（论文中应为人形机器人仿真中的 motion clips，例如参考 DeepMimic/AMP 常用数据集）。
- **基准对比（Benchmark & Baselines）**：
  - 主要对比方法：**Adversarial Motion Priors（AMP）**——当前 IfO 领域事实标准。
  - 其他可能的消融或对比（根据元信息推断可能包含随机策略、行为克隆变体等）。
- **评价指标**：量化指标（quantitative metrics），可能包括模仿相似度（如 pose error / pose match）、任务完成度、奖励曲线稳定性等（具体细节由于 PDF 受限无法完全确认）。

## 4. 资源与算力

- ⚠️ **未明确说明**：当前可获得的文本（仅摘要与元数据）**未提供**具体的 GPU 型号、数量、训练时长等算力信息。
- 由于论文属于 ICLR 2025 接收的基于 Isaac Gym / MuJoCo 类人机器人模仿学习工作，可推断训练**通常需要多 GPU（如 1–4 块 NVIDIA RTX/4090/A100）进行数小时至一天的仿真交互 + 训练**，但**此为领域惯例推断，非论文明确披露**。

## 5. 实验数量与充分性

- **任务数量**：至少覆盖两类不同性质的任务（locomotion + martial arts），并以多种具体运动设置（multiple imitation settings）进行评估。
- **对比维度**：
  - 与 AMP 的**多指标横向对比**；
  - 跨多种模仿设定（不同专家片段 / 不同难度）的泛化测试。
- **充分性评价**：
  - **优点**：覆盖了运动模仿领域的多样任务，并明确与领域 SOTA 对比，指标量化。
  - **局限**：当前摘要未提及**严格的消融实验**（如去除退火策略的影响、噪声层级数的影响），亦未说明是否在**真实机器人**上验证；实验主要在仿真环境中进行。

## 6. 主要结论与发现

- NEAR 能够在**无动作标签**条件下稳定学习复杂的、物理依赖的类人机器人运动策略。
- 基于能量生成模型的奖励设计**绕开了对抗模仿学习的优化困境**，训练更稳定。
- 在多项量化指标上**与 AMP 表现相当**，但在训练稳定性方面具有优势。
- **退火策略**对保证奖励函数始终良定义（well-defined）于策略分布流形上具有关键作用。

## 7. 优点（亮点）

- **生成式 vs 对抗式范式转变**：将模仿学习的核心难题从"对抗训练不稳定"转移到"得分匹配 + 退火策略"，为该领域开辟了新方向。
- **理论上的优雅性**：用噪声条件得分匹配自然地获得多尺度能量表示，无需额外判别器网络。
- **退火机制**：渐进式切换噪声层级的设计是该方法的关键工程贡献，提升了奖励的可用性。
- **广泛适用性**：理论上可应用于任何能获取状态级专家轨迹的机器人模仿场景。

## 8. 不足与局限

- **真实世界迁移性未验证**：实验似乎仅在仿真环境（physics simulator）中进行，**未提及真实机器人部署**。
- **依赖高斯扰动假设**：噪声条件得分匹配假设扰动分布为高斯，对高度多模态或离散动作分布的适用性可能受限。
- **算力与可复现性**：未明确披露算力与超参数细节，复现门槛较高。
- **实验广度有限**：仅与 AMP 对比，缺少与近年其他 IfO 方法（如 LILO、OPAL、Diffusion Policy 类等）的全面对比。
- **奖励设计依赖专家数据覆盖度**：若专家轨迹分布稀疏或具极端长尾，能量函数在策略附近的良定义性仍可能出现问题。
- **任务规模**：仅在类人机器人任务上验证，向其他形态（机械臂、四足等）以及多任务/语言条件模仿下的泛化未在摘要中提及。

（完）
