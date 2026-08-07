---
title: Learning View-invariant World Models for Visual Robotic Manipulation
title_zh: 面向视觉机器人操作的视角不变世界模型学习
authors: "Jing-Cheng Pang, Nan Tang, Kaiyuan Li, Yuting Tang, Xin-Qiang Cai, Zhen-Yu Zhang, Gang Niu, Masashi Sugiyama, Yang Yu"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=vJwjWyt4Ed"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向闭环操作的视角不变视觉表征
tldr: 本文针对机器人视觉操作在相机视角变化下性能显著下降的问题，提出ReViWo方法。该框架通过自编码器结构将表征分解为视角不变与视角相关两部分，并联合利用多视角仿真数据与Open X-Embodiment数据进行训练，从而提升视角扰动下控制策略的鲁棒性。在多种操作任务上的实验验证了其泛化能力。该贡献为视觉机器人操作在真实部署中的视角鲁棒性提供了实用方案。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 机器人视觉操作在相机视角变化时性能显著下降，缺乏鲁棒的视角不变表征。
method: 提出ReViWo自编码器框架，将表征分解为视角不变部分与视角相关部分并联合训练。
result: 方法在多视角仿真数据与Open X-Embodiment数据集上提升了视角扰动下的鲁棒性。
conclusion: ReViWo为视觉机器人操作的视角鲁棒控制提供了一种有效的表征学习方案。
---

## Abstract
Robotic manipulation tasks often rely on visual inputs from cameras to perceive the environment. However, previous approaches still suffer from performance degradation when the camera’s viewpoint changes during manipulation. In this paper, we propose ReViWo (Representation learning for View-invariant World model), leveraging multi-view data to learn robust representations for control under viewpoint disturbance. ReViWo utilizes an autoencoder framework to reconstruct target images by an architecture that combines view-invariant representation (VIR) and view-dependent representation. To train ReViWo, we collect multi-view data in simulators with known view labels, meanwhile, ReViWo is simutaneously trained on Open X-Embodiment datasets without view labels. The VIR is then used to train a world model on pre-collected manipulation data and a policy through interaction with the world model. We evaluate the effectiveness of ReViWo in various viewpoint disturbance scenarios, including control under novel camera positions and frequent camera shaking, using the Meta-world & PandaGym environments. Besides, we also conduct experiments on real world ALOHA robot. The results demonstrate that ReViWo maintains robust performance under viewpoint disturbance, while baseline methods suffer from significant performance degradation. Furthermore, we show that the VIR captures task-relevant state information and remains stable for observations from novel viewpoints, validating the efficacy of the ReViWo approach.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper based on the provided metadata and abstract. Let me analyze the content and create a structured Markdown summary following the 8 points specified.

The paper is about "Learning View-invariant World Models for Visual Robotic Manipulation" (ReViWo). Let me organize the information:

1. Core problem: Visual robotic manipulation degrades when camera viewpoint changes
2. Method: ReViWo autoencoder with view-invariant and view-dependent representations, trained on multi-view simulation data and Open X-Embodiment
3. Experiments: Meta-world & PandaGym environments, real-world ALOHA robot
4. Resources: Not mentioned in the provided text
5. Experimental completeness: Various viewpoint disturbance scenarios
6. Conclusions: Robust performance under viewpoint disturbance
7. Strengths: Novel representation decomposition approach
8. Limitations: Would need to infer from context

Let me write a comprehensive summary in Chinese.</think>

# 论文总结：面向视觉机器人操作的视角不变世界模型学习（ReViWo）

## 1. 核心问题与研究动机
- **背景**：机器人操作任务通常依赖摄像头提供的视觉输入进行环境感知；当前主流的视觉操控方法在训练与测试视角一致时表现良好，但一旦部署时摄像头视角发生变化（位移、抖动等），策略性能会显著下降。
- **核心问题**：缺乏对**视角扰动（viewpoint disturbance）**鲁棒的视觉表征，使得基于学习的控制策略难以在真实场景中可靠部署。
- **整体含义**：本文聚焦于在相机视角变化（包含**新视角位置**与**频繁抖动**两种典型扰动）下，保持操控策略的稳定性和泛化能力。

## 2. 方法论：ReViWo 框架
- **核心思想**：将视觉表征分解为两部分：
  - **视角不变表征（View-Invariant Representation, VIR）**：仅编码与任务相关的状态信息，对视角变化保持稳定。
  - **视角相关表征（View-Dependent Representation）**：编码与视角相关的信息（如光照、几何投影等）。
- **关键技术细节**：
  - 采用**自编码器（Autoencoder）**结构，通过结合 VIR 与视角相关表征重建目标图像。
  - **多源数据联合训练**：
    - 来自仿真器的**多视角数据**（具有已知的视角标签，用于显式监督）；
    - 来自 **Open X-Embodiment** 的大规模机器人数据（无视角标签，作为辅助训练信号）。
  - 训练完成后，将 **VIR** 输入世界模型（World Model），并基于预收集的操作数据与世界模型交互训练策略（policy）。
- **算法流程**（文字说明）：
  1. 收集多视角仿真数据（带视角标签）；
  2. 自编码器同时在多视角数据与 Open X-Embodiment 上进行联合训练，分离 VIR 与视角相关表征；
  3. 利用 VIR 在预收集的操作数据上训练世界模型；
  4. 通过与世界模型交互训练控制策略；
  5. 在新视角/抖动条件下执行策略。

## 3. 实验设计
- **仿真环境 / Benchmark**：
  - **Meta-world**：标准机器人操控仿真基准；
  - **PandaGym**：基于 Franka Panda 的操控仿真环境；
- **真实机器人**：**ALOHA** 双手机器人平台；
- **视角扰动场景**：
  - **新摄像头位置（novel camera positions）**；
  - **频繁摄像头抖动（camera shaking）**；
- **对比方法**：未在摘要中列出具体基线，但论文提到 "baseline methods suffer from significant performance degradation"，暗示对比了多种主流视觉操控/世界模型方法。

## 4. 资源与算力
- **说明**：在所提供的论文文本（标题、摘要、元数据）中**未明确提及**具体的 GPU 型号、数量、训练时长或算力消耗。
- 需要查阅正文才能获取这部分细节，本文现有信息**无法覆盖**。

## 5. 实验数量与充分性
- **实验覆盖**：覆盖了多个仿真环境（Meta-world + PandaGym）、多种视角扰动场景（新视角 + 抖动）、以及真实机器人验证。
- **充分性评估**：
  - **优点**：仿真→真实的迁移验证较为完整；同时验证了 VIR 对新视角的稳定性与任务相关性。
  - **可能不足**：
    - 摘要未给出消融实验细节（如去掉 VIR、去掉 Open X-Embodiment 数据、去掉多视角监督的具体影响）；
    - 真实机器人实验规模与任务数量在摘要中未具体说明；
    - 公平性方面需要查看正文是否对所有基线使用一致的视角扰动设置与训练数据量。

## 6. 主要结论与发现
- ReViWo 在多种视角扰动（**新视角位置**与**频繁抖动**）下均能维持稳定操控性能，而基线方法出现显著退化。
- 学到的 **VIR 编码了任务相关的状态信息**，并对来自未见过的视角的观测保持稳定。
- 验证了视角不变表征 + 世界模型框架在真实部署场景中的可行性。

## 7. 优点
- **问题导向明确**：直接解决真实部署中的视角鲁棒性问题，实用价值高。
- **表征分解思路清晰**：将视角不变与视角相关信息显式解耦，可解释性好。
- **数据来源多样**：结合仿真多视角（带标签）与 Open X-Embodiment（无标签）的大规模数据，提升泛化潜力。
- **跨平台验证**：同时在仿真（Meta-world、PandaGym）与真实机器人（ALOHA）上验证，证据链较完整。
- **结合世界模型**：通过与世界模型交互训练策略，有利于在数据有限条件下提升样本效率。

## 8. 不足与局限
- **算力信息缺失**：摘要未提供计算资源与训练成本信息，难以评估实际部署门槛。
- **基线对比细节不全**：摘要未列举具体对比方法及其实现细节，公平性需依赖正文进一步核实。
- **真实实验规模有限**：仅提到 ALOHA 平台，未说明任务数量、试验次数与统计显著性。
- **对 Open X-Embodiment 的依赖**：依赖大规模多源数据来弥补无视角标签的不足，可能引入分布偏移（不同机器人形态、场景差异）。
- **视角变化的范围**：实验集中在摄像机位置变化与抖动，是否覆盖更复杂的视角变化（如大幅旋转、遮挡、尺度变化）尚不明确。
- **应用限制**：方法需要预收集操作数据训练世界模型，对于在线快速适配新任务的能力未在摘要中讨论。

（完）
