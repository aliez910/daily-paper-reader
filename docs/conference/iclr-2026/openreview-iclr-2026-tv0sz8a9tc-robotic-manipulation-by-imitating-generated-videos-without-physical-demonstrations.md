---
title: Robotic Manipulation by Imitating Generated Videos Without Physical Demonstrations
title_zh: 无需物理演示的机器人视频模仿操作
authors: "Shivansh Patel, Shraddhaa Mohan, Hanlin Mai, Unnat Jain, Svetlana Lazebnik, Yunzhu Li"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=tv0Sz8A9Tc"
tags: ["query:rob-il"]
score: 9.0
evidence: 机器人通过模仿生成视频来学习复杂操作任务，属于视觉模仿学习
tldr: 针对模仿学习依赖大量物理演示这一瓶颈，本文提出 RIGVid 系统，使机器人能够仅通过模仿 AI 生成的视频完成倒水、擦拭、搅拌等复杂操作任务，无需任何物理演示或机器人专属训练。系统由视频扩散模型根据语言指令生成候选演示视频，视觉语言模型自动过滤不符合指令的结果，6D 位姿跟踪器提取物体轨迹并以与具体形态无关的方式重定向到机器人。真实环境评估表明，筛选后的生成视频可达到与真实演示相当的效果，大幅降低了对物理演示数据的依赖。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 模仿学习通常需要大量难以获取的物理机器人演示数据，限制了其规模化应用。
method: 利用视频扩散模型生成演示，结合 VLM 过滤与 6D 位姿跟踪实现跨形态轨迹重定向。
result: 在真实机器人上完成倒水、擦拭、搅拌等复杂任务，效果与真实演示相当。
conclusion: 为模仿学习摆脱物理演示依赖、利用生成式视频提供数据源开辟了新路径。
---

## Abstract
This work introduces Robots Imitating Generated Videos (RIGVid), a system that enables robots to perform complex manipulation tasks—such as pouring, wiping, and mixing—purely by imitating AI-generated videos, without requiring any physical demonstrations or robot-specific training. Given a language command and an initial scene image, a video diffusion model generates potential demonstration videos, and a vision-language model (VLM) automatically filters out results that do not follow the command. A 6D pose tracker then extracts object trajectories from the video, and the trajectories are retargeted to the robot in an embodiment-agnostic fashion. Through extensive realworld evaluations, we show that filtered generated videos are as effective as real demonstrations, and that performance improves with generation quality. We also show that relying on generated videos outperforms more compact alternatives such as keypoint prediction using VLMs, and that strong 6D pose tracking outperforms other ways to extract trajectories, such as dense feature point tracking. These findings suggest that videos produced by a state-of-the-art off-the-shelf model can offer an effective source of supervision for robotic manipulation.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper "Robotic Manipulation by Imitating Generated Videos Without Physical Demonstrations" (RIGVid) based on the provided content. I need to follow a specific structure with 8 points and output in Markdown format with hierarchical headings and bullet points.

Let me organize the information from the abstract and metadata:

1. Core problem: Imitation learning requires large amounts of physical robot demonstrations, which are hard to obtain
2. Method: RIGVid system - video diffusion model + VLM filtering + 6D pose tracking + embodiment-agnostic retargeting
3. Experiments: Real-world tasks like pouring, wiping, mixing; compared with real demos, VLM keypoint prediction, dense feature tracking
4. Resources: Not mentioned in the text provided
5. Experiment volume: Not entirely clear from the abstract, but mentions "extensive real-world evaluations"
6. Conclusions: Generated videos can be as effective as real demonstrations; performance correlates with generation quality
7. Advantages: No physical demos needed, off-the-shelf models can work
8. Limitations: Not explicitly stated in abstract

Let me write this out properly.
</think>
# 论文总结：RIGVid — 无需物理演示的机器人视频模仿操作

## 1. 核心问题与研究动机

- **核心瓶颈**：模仿学习（Imitation Learning）通常需要大量物理机器人演示数据，而这类数据采集成本高、耗时长，且对硬件与人力的依赖严重，限制了机器人技能学习的规模化推广。
- **研究目标**：探索能否绕开物理演示，利用现成的 AI 生成视频作为监督信号，使机器人直接完成复杂操作任务（如倒水、擦拭、搅拌）。
- **整体含义**：本文将"生成式视频模型"与"机器人操作"打通，提出一种数据来源几乎零成本的范式，对模仿学习的数据飞轮具有重要启发意义。

## 2. 方法论：RIGVid 系统

- **整体流程**（四阶段流水线）：
  1. **视频生成**：给定自然语言指令与初始场景图像，利用**视频扩散模型**生成若干候选演示视频。
  2. **视频过滤**：使用**视觉-语言模型（VLM）**对生成视频进行自动评估，过滤掉不符合指令或质量不达标的结果。
  3. **轨迹提取**：采用 **6D 位姿跟踪器**从筛选后的视频中提取物体（以及交互关系）的 6D 位姿轨迹。
  4. **形态无关重定向（Retargeting）**：将提取出的物体级轨迹以**与具体机器人本体无关（embodiment-agnostic）**的方式映射到目标机器人上执行。
- **关键设计点**：
  - **数据来源完全来自生成视频**，无需任何物理示教或机器人专属训练数据。
  - **6D 位姿作为通用接口**：将视频中的"人/物体运动"抽象为 6D 轨迹，从而屏蔽人与机器人的形态差异。
  - **VLM 充当自动质量门控**：避免扩散模型低质量或不合指令的输出污染下游训练与执行。

## 3. 实验设计

- **任务场景**：真实环境中的复杂操作任务，包括 **倒水（pouring）、擦拭（wiping）、搅拌（mixing）** 等。
- **Benchmark / 数据集**：未在所提供文本中明确指出使用哪个公开 benchmark，主要为作者自建的真实机器人评估场景。
- **对比方法**（来自消融与对比实验）：
  - **真实物理演示**（作为性能上界基线）。
  - **更紧凑的替代方案**：使用 VLM 直接进行**关键点预测**。
  - **其他轨迹提取方式**：使用**密集特征点跟踪**（dense feature tracking），而非 6D 位姿跟踪。
- **评估维度**：任务成功率、生成视频质量与下游操控性能的关系。

## 4. 资源与算力

- 论文文本中**未明确披露**所使用 GPU 型号、数量、训练时长等算力细节。
- 可推测使用了现成的视频扩散模型、VLM 以及 6D 跟踪器作为"开箱即用"组件，但具体的推理硬件和模型规模未在所给摘要中说明。

## 5. 实验数量与充分性

- 摘要中提到开展了 **"extensive real-world evaluations"**（广泛的真实世界评估），但具体实验组数、任务数、试验次数（trials）在所提供的文本中**没有详细说明**。
- 充分性方面：
  - **优势**：涵盖了多类任务（倒水、擦拭、搅拌），并设计了多个有意义的对比（真实演示 vs. 生成视频；6D 位姿 vs. 密集特征点 vs. 关键点预测），从多角度验证了关键设计选择的必要性。
  - **不足**：仅凭摘要无法判断统计显著性、任务难度梯度、扰动鲁棒性测试等是否充分；评估对象的形态多样性（不同机器人平台）也尚不明确。

## 6. 主要结论与发现

- **生成视频可作为有效监督源**：经 VLM 过滤后的生成视频，在真实机器人任务上能达到与**真实人类演示相当**的效果。
- **生成质量与性能正相关**：生成视频的质量越高，下游机器人任务表现越好。
- **6D 位姿跟踪是关键**：相比 VLM 关键点预测、密集特征点跟踪，**6D 位姿跟踪**是更有效的轨迹提取方式。
- **范式意义**：表明使用**现成最先进模型（SOTA off-the-shelf）**即可为机器人操作提供有效监督，显著降低数据门槛。

## 7. 优点与亮点

- **数据零成本范式**：彻底摆脱对物理机器人演示的依赖，大幅降低模仿学习的部署门槛。
- **模块化、可替换的流水线**：视频扩散模型、VLM 过滤、6D 跟踪、形态重定向均为独立模块，可随底层模型升级而持续受益。
- **形态无关设计**：6D 位姿作为通用中间表征，使方法可迁移到不同机器人平台。
- **消融设计合理**：从"视频来源（生成 vs. 真实）"和"轨迹提取方式（6D 位姿 vs. 关键点 vs. 特征跟踪）"两个维度交叉对比，说服力较强。
- **任务具实际价值**：所选任务（倒水、擦拭、搅拌）属于日常生活级接触式操作，对应用落地具有直接意义。

## 8. 不足与局限

- **算力与可复现性披露不足**：所用模型规模、推理硬件、过滤与跟踪模块的具体配置未在所提供文本中明确，影响复现。
- **生成模型的固有偏差风险**：视频扩散模型可能存在训练数据偏差（动作分布、文化背景、物体类别偏差），导致在长尾任务或非典型场景下生成的演示偏离真实物理规律。
- **物理可行性问题**：生成视频可能在视觉上合理但**物理上不可执行**（如接触、力、摩擦等难以建模），摘要未深入讨论对接触密集型任务的鲁棒性。
- **任务覆盖与统计充分性存疑**：摘要层面的"extensive evaluation"未给出具体 trial 数、成功率置信区间，难以判断结论的统计稳健性。
- **6D 跟踪器的依赖**：该方法对**6D 位姿跟踪**质量依赖较高，在遮挡、严重遮挡、相似物体或透明物体场景下可能退化。
- **VLM 过滤的可靠性**：VLM 自动判别可能存在错误接受/拒绝，论文未充分讨论过滤错误对下游性能的影响。
- **应用边界**：主要验证短时程、单一物体的操作，对于**长时序、多步骤、多物体协同**等更复杂任务的适用性尚待验证。

（完）
