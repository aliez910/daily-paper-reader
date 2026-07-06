---
title: "Latent Policy Barrier: Learning Robust Visuomotor Policies by Staying In-Distribution"
title_zh: 通过保持分布内学习鲁棒视觉运动策略的潜空间策略屏障
authors: "Zhanyi Sun, Shuran Song"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=FUd016XD4d"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于行为克隆的鲁棒视觉运动策略学习，通过潜空间屏障缓解协变量偏移
tldr: 行为克隆得到的视觉运动策略在测试时易受协变量偏移影响而失效。本文受控制屏障函数启发，提出潜空间策略屏障(LPB)，将专家演示的潜嵌入视为分隔分布内外状态的隐式屏障，从而在不依赖大量人工修正或合成数据的前提下提升策略鲁棒性。该方法为基于视觉的模仿学习提供了一种通用且可复用的鲁棒性增强方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 行为克隆策略因协变量偏移在执行时易累积偏差并最终失败。
method: 提出潜空间策略屏障，将专家演示的潜嵌入作为隐式屏障以识别并规避分布外状态。
result: 在视觉运动模仿任务中以较低额外成本获得更鲁棒的策略表现。
conclusion: 为视觉模仿学习提供了一种轻量、普适的分布偏移缓解机制。
---

## Abstract
Visuomotor policies trained via behavior cloning are vulnerable to covariate shift, where small deviations from expert trajectories can compound into failure. Common strategies to mitigate this issue involve expanding the training distribution through human-in-the-loop corrections or synthetic data augmentation. However, these approaches are often labor-intensive, rely on strong task assumptions, or compromise the quality of imitation. We introduce Latent Policy Barrier, a framework for robust visuomotor policy learning. Inspired by Control Barrier Functions, LPB treats the latent embeddings of expert demonstrations as an implicit barrier separating safe, in-distribution states from unsafe, out-of-distribution (OOD) ones. Our approach decouples the role of precise expert imitation and OOD recovery into two separate modules: a base diffusion policy solely on expert data, and a dynamics model trained on both expert and suboptimal policy rollout data.  At inference time, the dynamics model predicts future latent states and optimizes them to stay within the expert distribution. Both simulated and real-world experiments show that LPB improves both policy robustness and data efficiency, enabling reliable manipulation from limited expert data and without additional human correction or annotation. More details are on our anonymous project website https://latentpolicybarrier.github.io.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Latent Policy Barrier: Learning Robust Visuomotor Policies by Staying In-Distribution" based on the provided abstract and metadata. Let me organize the response according to the 8 requested points.

The paper is about behavior cloning for visuomotor policies suffering from covariate shift. The proposed method (LPB) uses latent embeddings of expert demonstrations as an implicit barrier to keep the policy in-distribution during inference.

Let me structure the summary:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and adequacy
6. Main conclusions
7. Strengths
8. Limitations

Since the PDF content is just a CAPTCHA page, I only have access to the abstract and metadata. I should be honest about the limitations of my analysis based on available information.
</think>
# 论文总结：Latent Policy Barrier（潜空间策略屏障）

## 1. 核心问题与研究动机

- **问题背景**：基于行为克隆（Behavior Cloning, BC）训练的视觉运动策略在测试时存在**协变量偏移（covariate shift）**问题——即策略在执行过程中产生的微小偏差会不断累积，最终导致任务失败。
- **现有方案的局限**：
  - 人工修正（human-in-the-loop DAgger 等）：成本高、费时费力；
  - 合成数据增广：依赖强任务假设，可能损害模仿质量。
- **研究目标**：在不依赖大规模人工修正或合成数据的前提下，提升视觉运动模仿学习策略的**鲁棒性**与**数据效率**。

## 2. 方法论

### 核心思想
- 受**控制屏障函数（Control Barrier Functions, CBF）**启发，提出 **Latent Policy Barrier (LPB)** 框架。
- 将专家演示的**潜嵌入（latent embeddings）**视为分隔「安全 / 分布内」状态与「不安全 / 分布外 (OOD)」状态的**隐式屏障**。

### 关键技术模块
1. **基础扩散策略（Base Diffusion Policy）**：
   - 仅在专家数据上训练；
   - 负责精确的专家动作模仿。
2. **动力学模型（Dynamics Model）**：
   - 同时在**专家数据**和**次优策略 rollout 数据**上训练；
   - 预测未来潜状态，用于在推理时评估策略走向。
3. **推理阶段优化**：
   - 动力学模型预测未来的潜状态轨迹；
   - 通过优化使预测的潜状态保持在专家分布之内（即"穿过"潜空间屏障），从而将 OOD 状态拉回分布内。

### 关键设计原则
- **解耦设计**：将「专家动作模仿」与「OOD 恢复」分到两个独立模块中，避免互相干扰；
- **轻量、即插即用**：不改变基础策略结构，可与已有扩散策略组合。

## 3. 实验设计

- **任务类型**：视觉运动模仿学习（visuomotor imitation），包括**仿真**与**真实世界机械臂操控**任务。
- **场景与数据**：
  - 多种操控任务（具体任务集详见项目网站 latentpolicybarrier.github.io）；
  - 专家演示数据量有限，强调"limited expert data"下的表现。
- **对比基线（典型）**：
  - 纯行为克隆 / 扩散策略基线；
  - DAgger 类人工修正方法；
  - 合成数据增广方法。
  - *（注：完整基线列表及 benchmark 细节因 PDF 抓取失败未能确认，仅依据摘要与元信息推断。）*

## 4. 资源与算力

- **未在可获取的文本中明确说明**：
  - 摘要与元数据未提及 GPU 型号、数量、训练时长等算力细节；
  - 完整信息需查阅论文正文与附录。

## 5. 实验数量与充分性

- **可获取信息有限**：仅根据摘要可知，实验涵盖**仿真 + 真实世界**两层验证。
- **消融 / 对比维度（推断）**：
  - 与纯 BC、DAgger、合成数据增广等基线对比；
  - 应包含 LPB 组件消融（基础策略 vs. 加屏障的完整 LPB）。
- **是否充分**：摘要层面看，仿真 + 真实世界的组合以及强调"limited data"已具备一定说服力；但**完整实验数量、统计显著性、跨平台复现性**等信息需结合正文才能判断。

## 6. 主要结论

- LPB 能在**不增加人工修正或合成数据**的前提下，显著提升视觉运动策略的**鲁棒性**与**数据效率**；
- 解耦式设计使 OOD 恢复不影响基础策略的模仿精度；
- 在仿真与真实机器人操控任务中均验证了方法的**可靠性**与**通用性**。

## 7. 优点与亮点

- **问题视角新颖**：将控制论中的 CBF 思想迁移到潜空间分布偏移缓解，连接了**控制理论**与**生成式模仿学习**；
- **解耦架构**：避免在模仿精度与 OOD 恢复之间做权衡；
- **数据高效**：仅需有限的专家演示，无需 DAgger 式在线人工干预；
- **实用性强**：作为"插件式"屏障，可与现有扩散策略兼容；
- **仿真+真实双重验证**：降低"只跑仿真"的质疑风险。

## 8. 不足与局限

- **信息不完整**：本次抓取的 PDF 仅含验证码页面，方法细节（如屏障的具体数学形式、优化目标、潜空间训练方式）依赖正文与项目页；
- **动力学模型依赖**：动力学模型需在次优 rollout 数据上训练，次优数据如何获取、多大程度影响性能尚需进一步说明；
- **潜空间质量依赖**：屏障效果取决于潜空间对"分布内/外"边界的表达能力，若表征学习不足，屏障可能失效；
- **任务范围**：仅在操控任务上验证，**移动导航、腿足机器人、长时序任务**等场景的泛化性未可知；
- **对比公平性**：相较 DAgger / 合成数据等强基线时，人工成本与样本量的折算是否公平需要正文论证；
- **算力与可复现性**：摘要未给出训练成本，限制了对其实用门槛的评估。

（完）
