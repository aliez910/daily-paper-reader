---
title: "Conditioning Matters:  Training Diffusion Policies is Faster Than You Think"
title_zh: 条件很重要：训练扩散策略比你想的更快
authors: "Zibin Dong, Yicheng Liu, Yinchuan Li, Hang Zhao, Jianye HAO"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=pKQcmLHoGG"
tags: ["query:rob-il"]
score: 8.0
evidence: 改进基于扩散的视觉-语言-动作策略训练效率
tldr: 本文发现条件扩散策略训练中因条件难以区分而出现的损失坍缩问题，导致目标退化为边缘动作分布建模。提出 Cocos 方法，将条件流匹配中的源分布改造为条件依赖型，围绕条件语义进行锚定。该方法显著加速了 VLA 扩散策略在端到端机器人控制中的训练收敛。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 条件扩散策略训练存在损失坍缩，条件难以区分时退化为对边缘动作分布建模。
method: 提出 Cocos，将条件流匹配的源分布改造为条件依赖并围绕语义进行锚定。
result: 在 VLA 训练基准上获得更快的收敛速度与更强的条件敏感性。
conclusion: 源分布的条件化设计是提升扩散策略训练效率的关键。
---

## Abstract
Diffusion policies have emerged as a mainstream paradigm for building vision-language-action (VLA) models. Although they demonstrate strong robot control capabilities, their training efficiency remains suboptimal. In this work, we identify a fundamental challenge in conditional diffusion policy training: when generative conditions are hard to distinguish, the training objective degenerates into modeling the marginal action distribution, a phenomenon we term loss collapse. To overcome this, we propose Cocos, a simple yet general solution that modifies the source distribution in the conditional flow matching to be condition-dependent. By anchoring the source distribution around semantics extracted from condition inputs, Cocos encourages stronger condition integration and prevents the loss collapse. We provide theoretical justification and extensive empirical results across simulation and real-world benchmarks. Our method achieves faster convergence and higher success rates than existing approaches, matching the performance of large-scale pre-trained VLAs using significantly fewer gradient steps and parameters. Cocos is lightweight, easy to implement, and compatible with diverse policy architectures, offering a general-purpose improvement to diffusion policy training.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Conditioning Matters: Training Diffusion Policies is Faster Than You Think" based on the provided metadata. Let me organize the response according to the 8 requested points.

Key information from the paper:
- Problem: Diffusion policies for VLA models have suboptimal training efficiency
- Issue identified: "loss collapse" - when conditions are hard to distinguish, the training objective degenerates into modeling marginal action distribution
- Solution: Cocos - modifies source distribution in conditional flow matching to be condition-dependent
- Method: Anchors source distribution around semantics from condition inputs
- Theoretical justification provided
- Experiments on simulation and real-world benchmarks
- Result: Faster convergence, higher success rates, matches large-scale pre-trained VLAs with fewer gradient steps and parameters
- Lightweight, easy to implement, compatible with diverse policy architectures
- Source: NeurIPS 2025 Accepted

Let me write a comprehensive Chinese summary.
</think>
# 论文总结：Conditioning Matters: Training Diffusion Policies is Faster Than You Think

## 1. 核心问题与研究动机

- **背景**：扩散策略（Diffusion Policies）已成为构建视觉-语言-动作（VLA）模型的主流范式，在机器人控制中表现出色，但其训练效率仍然欠佳。
- **核心问题**：作者识别出条件扩散策略训练中一个根本性挑战——**损失坍缩（loss collapse）**。当生成条件（如语言指令、视觉上下文等）难以区分时，训练目标会退化为对边缘动作分布（marginal action distribution）的建模，导致条件信号无法有效引导动作生成。
- **研究意义**：揭示了扩散策略训练效率低下的本质原因，并提出一个轻量、通用的解决方案，有望在显著减少计算开销的前提下提升 VLA 模型的性能。

## 2. 方法论：Cocos

- **核心思想**：不改变扩散/流匹配框架的整体结构，仅将条件流匹配（Conditional Flow Matching, CFM）中的源分布（source distribution）改造为**条件依赖型**，并围绕条件语义进行锚定。
- **关键技术细节**：
  - **源分布条件化**：传统 CFM 使用与条件无关的简单源分布（如标准高斯）。Cocos 让源分布的参数（如均值）由条件编码器提取的语义特征决定。
  - **语义锚定**：通过将源分布的中心锚定到条件语义空间中的对应位置，使模型在生成过程中从一开始就处于与目标更接近的流形上，从而加速收敛。
  - **条件敏感性增强**：通过源分布的条件化设计，强化了模型对不同条件之间的区分能力，缓解了条件难以区分时退化为边缘分布建模的问题。
  - **理论支撑**：作者提供了理论分析，说明该方法在何种条件下能避免损失坍缩，并保证流匹配目标的有效性。
- **算法流程（文字描述）**：
  1. 输入条件（如语言指令、视觉观测）经过编码器提取语义嵌入。
  2. 源分布的均值由该语义嵌入调制（而非固定为 0）。
  3. 在训练时，从条件依赖的源分布中采样噪声，与真实动作构造配对，训练流匹配模型。
  4. 推理时，同样根据条件生成对应的源分布样本，再沿学习到的流场积分得到最终动作。

## 3. 实验设计

- **数据集 / 场景**：
  - 仿真基准：涉及多个机器人操作任务（具体任务集合需查阅论文正文，涵盖了标准机器人模仿学习基准）。
  - 真实世界基准：在真实机器人平台上进行了实验验证。
- **Benchmark**：以视觉-语言-动作（VLA）扩散策略训练为评测场景。
- **对比方法**：
  - 标准条件扩散策略 / 条件流匹配基线。
  - 大规模预训练 VLA 模型（作为强对比对象）。
  - 可能在文中还与多种条件处理变体进行对比。

## 4. 资源与算力

- 论文元数据中**未明确提供** GPU 型号、数量、训练时长等具体算力信息。
- 从结论描述推断：Cocos 能以**显著更少的梯度步数和参数量**匹配大规模预训练 VLA 的性能，间接说明其计算开销大幅低于预训练 VLA 方案。

## 5. 实验数量与充分性

- 实验覆盖**仿真和真实世界**两个层面，具备一定的泛化性验证。
- 包含**收敛速度对比**、**成功率对比**以及**与大规模预训练 VLA 的性能匹配**等多维度评测。
- 提供了**理论分析**支撑方法设计，并声称进行了**广泛的经验验证**（extensive empirical results）。
- 是否包含充分的消融实验（如源分布条件化程度、不同条件编码方式等）需查阅正文，但从摘要描述来看较为系统。**由于仅基于摘要信息，实验的完整细节（消融数量、统计显著性、多次随机种子等）无法完全确认。**

## 6. 主要结论与发现

- 条件扩散策略训练中确实存在**损失坍缩**现象，这是训练效率低下的重要原因。
- 将源分布条件化（围绕条件语义锚定）能够**有效避免损失坍缩**，加速收敛并提升最终性能。
- Cocos 能以**显著更少的梯度步数和参数**匹配大规模预训练 VLA 的成功率，证明了"以巧取胜"的可能。
- 该方法**轻量、易实现、与多种策略架构兼容**，具有较强的通用性。

## 7. 优点与亮点

- **问题洞察深刻**：从训练目标的退化（损失坍缩）这一根本原因出发，而非在工程层面堆叠技巧，学术贡献明确。
- **方法简洁优雅**：仅修改源分布的构造方式，无需改变扩散/流匹配的总体框架，实现成本低、兼容性好。
- **理论 + 实证结合**：提供了理论分析与经验验证双重支撑。
- **实用价值高**：在大幅降低算力需求的前提下匹配大规模预训练 VLA 性能，对资源受限的研究团队尤其友好。
- **通用性强**：声称可与多种策略架构结合，具备"即插即用"潜力。

## 8. 不足与局限

- **实验细节不透明**：基于现有摘要，无法判断实验是否包含充分的消融实验、统计显著性检验、多次随机种子等严谨要素。
- **数据集覆盖范围有限**：仿真与真实世界实验的具体规模、任务多样性、动作空间维度等关键信息缺失，可能存在评测广度不足的风险。
- **"匹配大规模预训练 VLA"的可比性**：预训练 VLA 通常在更广泛数据上预训练，性能提升是否仅来自训练效率还是隐含数据优势，需进一步分析。
- **方法适用边界**：Cocos 的效果可能依赖于条件编码器的语义提取质量，当条件本身极度模糊或噪声较大时，其增益尚不明确。
- **应用范围限制**：论文聚焦于机器人控制领域的 VLA 训练，方法在其他扩散生成任务（如图像、音频生成）中是否同样有效，文中未作说明。

（完）
