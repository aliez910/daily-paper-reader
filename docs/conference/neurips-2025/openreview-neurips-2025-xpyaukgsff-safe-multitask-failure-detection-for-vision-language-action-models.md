---
title: "SAFE: Multitask Failure Detection for Vision-Language-Action Models"
title_zh: SAFE：面向视觉-语言-动作模型的多任务故障检测
authors: "Qiao Gu, Yuanliang Ju, Shengxiang Sun, Igor Gilitschenski, Haruki Nishimura, Masha Itkina, Florian Shkurti"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=XPyAukgsFf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向通用视觉-语言-动作模型的故障检测
tldr: 针对视觉-语言-动作模型在新任务上成功率有限的问题，本文提出多任务故障检测任务，并设计了SAFE故障检测器。该检测器面向VLAs等通用机器人策略，可泛化到未见过的任务与环境中。实验表明SAFE能为机器人提供及时的安全警报以停止、回退或求助，提升通用VLA策略的安全部署能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 通用VLA模型在新任务部署时成功率有限，需要可靠的故障检测机制保障安全。
method: 提出多任务故障检测问题并设计SAFE检测器，使其能泛化到未见任务与环境。
result: 实验表明SAFE可在多种任务和环境中为VLA策略提供及时有效的故障警报。
conclusion: 为通用视觉-语言-动作模型的安全部署提供了关键的故障检测支撑。
---

## Abstract
While vision-language-action models (VLAs) have shown promising robotic behaviors across a diverse set of manipulation tasks, they achieve limited success rates when deployed on novel tasks out of the box. To allow these policies to safely interact with their environments, we need a failure detector that gives a timely alert such that the robot can stop, backtrack, or ask for help. However, existing failure detectors are trained and tested only on one or a few specific tasks, while generalist VLAs require the detector to generalize and detect failures also in unseen tasks and novel environments. In this paper, we introduce the multitask failure detection problem and propose SAFE, a failure detector for generalist robot policies such as VLAs. We analyze the VLA feature space and find that VLAs have sufficient high-level knowledge about task success and failure, which is generic across different tasks. Based on this insight, we design SAFE to learn from VLA internal features and predict a single scalar indicating the likelihood of task failure. SAFE is trained on both successful and failed rollouts and is evaluated on unseen tasks. SAFE is compatible with different policy architectures. We test it on OpenVLA, $\pi_0$, and $\pi_0$-FAST in both simulated and real-world environments extensively. We compare SAFE with diverse baselines and show that SAFE achieves state-of-the-art failure detection performance and the best trade-off between accuracy and detection time using conformal prediction. More qualitative results and code can be found at the project webpage: https://vla-safe.github.io/

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "SAFE: Multitask Failure Detection for Vision-Language-Action Models" based on the provided abstract and metadata. Let me organize the content according to the specified points.

The paper is about failure detection for VLA (Vision-Language-Action) models in robotics. Let me extract key information:

1. Core problem: VLA models have limited success on novel tasks, need failure detection for safety
2. Method: SAFE - a failure detector that learns from VLA internal features, predicts scalar failure likelihood, uses conformal prediction
3. Experiments: Tested on OpenVLA, π0, π0-FAST in simulation and real-world, compared with diverse baselines
4. Resources: Not mentioned in the provided text
5. Experimental volume: Tested in multiple tasks and environments, both sim and real
6. Conclusions: SOTA failure detection, best trade-off between accuracy and detection time
7. Strengths: Generalizes to unseen tasks, compatible with different policy architectures, uses conformal prediction
8. Limitations: Not explicitly mentioned in the provided text, but I can infer some limitations

Let me write a detailed Chinese summary following the structure requested.
</think>
# SAFE：面向视觉-语言-动作模型的多任务故障检测 —— 论文总结

## 1. 核心问题与研究动机

- **研究背景**：近年来，视觉-语言-动作模型（Vision-Language-Action Models, VLAs）作为通用机器人策略，在多种操作任务上展现出良好的行为泛化能力，但在直接部署到新任务（novel tasks）时仍存在成功率有限的问题。
- **核心问题**：当 VLA 策略在新任务或新环境中出现失误时，机器人需要一种**及时、可靠的故障检测机制**，以便在执行过程中能够触发**停止、回退或请求人工协助**等安全行为。
- **现有方法的不足**：已有故障检测器通常只在单一或少数任务上训练与测试，缺乏对**未见任务与新环境**的泛化能力，难以满足通用 VLA 策略在多种任务上安全部署的需求。
- **整体目标**：提出一种面向通用机器人策略（如 VLA）的多任务故障检测方法，使其在未见任务中也能给出及时、准确的失败预警。

## 2. 方法论

- **核心思想**：通过对 VLA 内部特征空间的分析，发现 VLA 模型中已包含关于任务成败的**高层语义信息**，且该信息在不同任务间具有通用性。据此，可以直接从 VLA 内部特征中学习故障检测器，而无需从零训练。
- **关键技术——SAFE 检测器**：
  - **输入**：VLA 模型执行 rollout 过程中的**内部特征**。
  - **输出**：一个标量值，表示任务**失败的概率**。
  - **训练数据**：同时使用**成功**与**失败**的 rollout 轨迹进行训练。
  - **泛化能力**：在训练中未见过的任务与新环境中进行评估。
- **不确定性量化与决策阈值**：采用 **conformal prediction（共形预测）** 来对故障检测器输出进行校准，从而在**检测准确率与检测时间**之间获得最佳折中。
- **架构兼容性**：SAFE 是一种**与具体策略架构解耦**的检测器，已在多种主流 VLA 模型上验证可用性。
- **算法流程概述**（文字版）：
  1. 收集 VLA 策略在多种任务上的成功与失败 rollout。
  2. 提取每个时间步的 VLA 内部特征。
  3. 训练一个轻量级故障检测器，输入 VLA 内部特征，输出失败概率标量。
  4. 推理时，利用 conformal prediction 在保持用户指定的错误率约束下，选择合适的阈值触发安全警报。

## 3. 实验设计

- **被测策略（Backbone VLAs）**：
  - **OpenVLA**
  - **π₀**
  - **π₀-FAST**
- **实验场景**：
  - **仿真环境**（多种任务）
  - **真实世界环境**（real-world）
- **Benchmark**：在**未见任务（unseen tasks）**和**新环境**下进行测试，构成多任务故障检测基准。
- **对比方法**：与**多种基线方法（diverse baselines）**进行比较，包含但不限于已有故障检测思路（具体基线名称在摘要中未列出，详见论文正文与附录）。
- **评估指标**：
  - **故障检测准确率**（Accuracy）
  - **检测时间**（Detection Time / 告警及时性）
  - 通过 conformal prediction 衡量**准确率与检测时间的权衡曲线**。

## 4. 资源与算力

- **未明确说明**：所提供的摘要与元数据中**未提及**具体的 GPU 型号、数量或训练时长。
- 建议：如需详细算力信息（例如训练所用 GPU 数量、训练 epoch、单次实验耗时等），需查阅论文正文及附录中的实验设置章节。

## 5. 实验数量与充分性

- **策略覆盖**：横跨 3 种不同的 VLA 架构（OpenVLA、π₀、π₀-FAST）。
- **环境覆盖**：同时覆盖**仿真**与**真实机器人**环境。
- **任务覆盖**：包含训练中**已见任务**与**未见任务（unseen tasks）**的评估。
- **基线比较**：与多种 baseline 进行对比，并使用 conformal prediction 对性能-时间权衡进行系统评估。
- **充分性评价**：
  - **优点**：跨架构、跨仿真-真实、跨已见-未见任务的实验设置较为全面，且关注了检测时间这一实际部署中至关重要的指标。
  - **不足（基于现有信息）**：摘要中未提供具体的任务数量、每种策略下实验的运行次数（seeds/trials）等定量信息，难以独立判断统计显著性。

## 6. 主要结论与发现

- **核心发现**：VLA 模型的内部特征空间已经蕴含了关于任务成败的**通用高层知识**，该信息在任务间可迁移。
- **方法效果**：
  - SAFE 在多种 VLA 策略（OpenVLA、π₀、π₀-FAST）上均取得**最优（state-of-the-art）** 的故障检测性能。
  - 在 **conformal prediction 框架下**，SAFE 提供了**检测准确率与检测时间之间的最佳权衡**。
- **应用价值**：SAFE 为通用 VLA 策略的安全部署提供了**及时且有效的安全警报**，使机器人能够及时停止、回退或寻求人工协助。

## 7. 优点

- **任务无关的故障检测能力**：基于 VLA 内部通用高层特征，可泛化到**未见任务**与**新环境**，解决了现有检测器只能用于特定任务的局限。
- **架构无关性**：与具体 VLA 架构解耦，兼容多种主流通用机器人策略。
- **理论保障**：引入 **conformal prediction**，为故障检测提供统计意义上的覆盖率/错误率保证。
- **双重验证**：同时在**仿真与真实环境**下进行实验，结果更具说服力。
- **时序维度考虑**：在评估中显式关注**检测时间**，而不仅看最终检测准确率，更贴近真实部署需求。

## 8. 不足与局限

- **算力信息缺失**：摘要中未提供训练与评估所用的计算资源信息，**复现成本难以评估**。
- **实验细节有限**：摘要未提供具体的任务数量、每种任务的 rollout 数量、统计显著性检验等信息，**实验的统计强度不透明**。
- **基线选择不透明**：虽提到与“多种 baseline”对比，但具体对比方法未在摘要中列出，**公平性需结合正文验证**。
- **失败模式分析不足**：摘要未讨论 SAFE 在哪些类型的失败（例如灾难性失败 vs. 长期偏移失败、可恢复失败 vs. 不可恢复失败）下表现如何。
- **VLA 性能上限依赖**：SAFE 是 VLA 策略的**伴随检测器**，其效果依赖于 VLA 自身特征的可分性；若 VLA 在某些任务上几乎完全失效（例如从一开始就输出无意义动作），故障检测的有效性可能受限。
- **真实环境实验规模**：摘要中未明确真实世界实验的任务数量与试验次数，**真实场景的泛化结论需要更细致的报告**。

---

（完）
