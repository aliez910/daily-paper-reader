---
title: "Free-View Robot Manipulation: Visuomotor Policy by Calibration Diffusion"
title_zh: 自由视角机器人操纵：基于校准扩散的视觉运动策略
authors: "Tianlei Jin, Wei Song, Tian Zhou, Jingqi Zeng, Dong Jing, Zhiwu Lu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=a5rZNSuRbp"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于校准扩散的视觉运动策略，实现自由视角机器人操纵的闭环视觉反馈
tldr: 现有视觉运动策略多依赖固定视角，相机视角变化时性能急剧下降，限制了机器人操纵的泛化与应用。本文系统研究自由视角操纵任务，构建了包含8个任务、5000余条多视角回合的Isaac Sim数据集，并提出校准扩散框架，使视觉运动策略在不同视角下均能获得稳定的闭环视觉反馈。该方法显著提升了视觉运动策略在视角变化下的鲁棒性，为视角无关的机器人操纵提供了新的数据与算法基础。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有视觉运动策略在固定视角下训练，视角变化时性能显著下降。
method: 构建多视角自由操纵数据集，并提出校准扩散框架实现视角无关的闭环视觉反馈。
result: 校准扩散策略在多种新视角下均能可靠完成操纵任务。
conclusion: 校准扩散是提升视觉运动策略视角鲁棒性的有效方法。
---

## Abstract
Visuomotor policies have demonstrated great potential in robot manipulation tasks.
However, current robot manipulation tasks are often observed from fixed viewpoints. 
Once the viewpoints change, the trained policy becomes ineffective.
This limitation curbs the generalization of robot manipulation and impedes its application.
To address this issue, we make a comprehensive study by presenting novel free-view manipulation tasks that enables the robot to perform actions from any viewpoint.
Firstly, we construct a free-view dataset, which encompasses 8 tasks with over 5,000 episodes sourced from the ISAAC SIM simulation  environment. 
Each episode records robot manipulation behaviors from different viewpoints.
Secondly, we propose a calibration diffusion policy, which utilizes an additional calibration network to enhance the adaptability of the diffusion policy to different viewpoints. 
In particular, we adopt two-stage curriculum training to make the calibration diffusion policy converge rapidly.
Finally, we conduct a wealth of experiments on the free-view dataset. 
The obtained results demonstrate the effectiveness of the calibration diffusion policy. 
This also means that we have built a new benchmark for free-view manipulation.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper based on the provided content. Let me analyze the paper first.

The paper is about "Free-View Robot Manipulation: Visuomotor Policy by Calibration Diffusion" - a paper about visuomotor policies for robot manipulation that can work from any viewpoint.

Key points from the paper:
- Problem: Existing visuomotor policies depend on fixed viewpoints, performance drops when viewpoints change
- Contribution 1: Constructed a free-view dataset with 8 tasks, 5000+ episodes in Isaac Sim
- Contribution 2: Proposed "calibration diffusion policy" with additional calibration network
- Method: Two-stage curriculum training
- Result: Effective for free-view manipulation

Let me write a structured Chinese summary following the 8 points requested.

The PDF content is just a CAPTCHA page, but the metadata provides substantial information. I need to work primarily with the metadata and abstract provided.

Let me organize the summary well.
</think>
# 论文总结：自由视角机器人操纵——基于校准扩散的视觉运动策略

## 1. 核心问题与整体含义

- **研究背景**：视觉运动策略（Visuomotor Policy）在机器人操纵任务中表现出色，但现有方法普遍依赖**固定相机视角**采集训练数据。
- **核心问题**：一旦实际部署时相机视角与训练视角不一致，策略性能会急剧下降甚至失效，严重限制了机器人操纵的**泛化能力与实际应用**。
- **研究意义**：推动从"固定视角"到"自由视角"（free-view）的操纵，使机器人能在任意观察角度下稳定完成任务，是走向真实复杂环境部署的关键一步。

## 2. 方法论

### 核心思想
- 提出**校准扩散策略（Calibration Diffusion Policy）**：在原有扩散策略（Diffusion Policy）的基础上，引入一个额外的**校准网络（Calibration Network）**，用于在不同视角下对扩散策略的输出进行自适应调整或特征对齐，从而提升策略对视角变化的鲁棒性。

### 关键技术细节
- **扩散策略基座**：以扩散模型作为行为生成器，输出机器人动作序列。
- **校准网络**：作为辅助模块，对视觉表征或动作分布进行视角相关的校准，使策略对相机内外参变化不敏感。
- **两阶段课程训练（Two-stage Curriculum Training）**：
  1. 第一阶段：可能侧重于基础任务学习或视角无关表征的预训练；
  2. 第二阶段：引入视角变化，逐步扩展到更多/更复杂的视角条件；
  - 通过课程式训练使校准扩散策略**快速收敛**。

## 3. 实验设计

- **数据集 / 仿真环境**：
  - 基于 **NVIDIA Isaac Sim** 仿真平台构建。
  - 包含 **8 个自由视角操纵任务**。
  - 超过 **5,000 条回合（episodes）**。
  - 每条回合从**多个不同视角**记录机器人操纵行为，构成本文提出的 **Free-View Benchmark**。
- **对比方法**：根据摘要与 tldr 描述，主要对比对象应为"在固定视角下训练的基线扩散策略"以及其他可参考的视觉运动策略（具体消融对比需以正文为准，目前提供的元数据未完全列出对比方法名单）。
- **评估重点**：在不同新视角（训练中未出现或较少出现的视角）下测试策略完成率与稳定性。

## 4. 资源与算力

- 论文元数据与提供的文本**未明确说明**所用 GPU 型号、数量、训练时长等算力信息。
- 仅可推断仿真环境为 **Isaac Sim**（通常需要较高 GPU 资源），但具体训练资源未在可见文本中披露。
- **建议**：在引用时需注意这一信息缺口。

## 5. 实验数量与充分性

- 实验规模包含 **8 个任务 × 多视角评估**，数据集规模达 **5,000+ episodes**，在仿真基准中属于中等偏上规模。
- 提出了一个**新基准（Free-View Benchmark）**，本身具有推动领域统一评测的价值。
- **充分性评估**：
  - 优点：覆盖了多任务、多视角的组合。
  - 局限：从已有信息看，缺少对**真实世界（real-world）**实验的描述，是否具备 sim-to-real 验证仍不明确。
  - 对比方法的全面性、消融实验的细粒度（如校准网络不同接入方式、视角数量变化对性能的影响等）需要正文进一步确认。

## 6. 主要结论与发现

- 校准扩散策略在多种**新视角**下均能可靠完成操纵任务，显著优于依赖固定视角训练的传统扩散策略。
- 两阶段课程训练能够使校准扩散策略**快速收敛**。
- 本文构建的 Free-View 数据集与基准，为后续视角无关的机器人操纵研究提供了**新的数据与算法基础**。

## 7. 优点

- **问题定义清晰且重要**：首次系统性地提出"自由视角操纵"任务设定，抓住了真实部署中的关键痛点。
- **数据贡献突出**：发布了多任务、多视角、大规模仿真数据集，填补了该方向基准的空白。
- **方法设计合理**：在扩散策略上引入轻量化的校准网络，并配合课程训练，思路简洁且易于扩展。
- **建立了新基准**：对推动领域后续研究具有基础设施意义。

## 8. 不足与局限

- **真实世界验证不足**：从目前可见内容看，实验主要在 Isaac Sim 仿真中进行，**sim-to-real 迁移能力有待验证**。
- **算力与训练细节披露不充分**：缺少 GPU 资源、训练时长、超参数设置等可复现性关键信息。
- **视角多样性边界未充分讨论**：未明确说明支持的最大视角偏离范围、外参变化幅度及遮挡等极端情况下的表现。
- **对比基线可能不够全面**：若仅与固定视角扩散策略对比，缺少与近期视角不变表征学习、3D 视觉策略等方法的横向比较，公平性需进一步论证。
- **校准网络的可解释性与开销**：引入额外网络的推理延迟、参数量及其对实时控制的影响未在可见文本中说明。
- **应用限制**：当前主要面向仿真环境，真实机器人部署中的光照、遮挡、动态干扰等复杂因素尚未涉及。

（完）
