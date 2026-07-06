---
title: "From Language to Action Streams: Bridging LLM Autoregression for Long-Horizon Robot Action Prediction"
title_zh: 从语言到动作流：面向长时序机器人动作预测的LLM自回归桥接
authors: "Zijian Wang, Yunke Wang, Siyu Xu, Chang Xu"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=ztBF43TsTg"
tags: ["query:rob-il"]
score: 8.0
evidence: 视觉-语言-动作模型，将视觉与语言翻译为长时序机器人动作
tldr: 视觉-语言-动作模型借助预训练VLM直接将视觉与语言映射为底层动作，但现有方案多生成固定长度的单步动作序列，限制了策略的生成时域。本文提出动作流（Action Stream）范式，将LLM的自回归生成定制为可变长度、长时序的动作流预测，使策略在长视野任务中具备更强的规划与执行能力。该工作为通用视觉-动作模型处理复杂长时序机器人控制任务提供了新的生成框架与扩展路径。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有VLA模型将动作预测限制为固定长度的单步序列，难以应对长时序任务。
method: 提出Action Stream范式，定制LLM自回归生成可变长度长时序动作流。
result: 动作流生成机制有效扩展了VLA策略的规划时域，适配长视野任务。
conclusion: 将LLM自回归能力拓展为动作流可显著增强通用视觉-动作模型的时序规划能力。
---

## Abstract
Vision-Language-Action(VLA) models is a transformative paradigm for robotic control, leveraging pre-trained vision-language models(VLMs) to directly translate natural language instructions and visual observations into low-level actions. 
The prominent idea of ``Action-as-Language" discretizes action spaces into tokens for large language models(LLMs), reframing action prediction as a standard sequential language generation task. 
However, current implementations underutilize the LLM's full generation potential, confining action prediction to fixed-length, single-step token sequences and limiting the policy's generation horizon.
To overcome this limitation, we propose the \textbf{Action Stream} paradigm, which customizes LLM training and inference recipes to VLAs, enabling the generation of extended chains of action tokens and facilitating implicit long-horizon generation with task performance improvements.
For training action streams, we propose a two-phase approach: Long-horizon Behavior Cloning(L-BC) and Step-wise Action Alignment(S-AA). 
L-BC enables VLA models to generate coherent multi-step action sequences, while S-AA mitigates exposure bias during sequential inference, creating a framework that enables long-horizon generation while reducing error accumulation.
During deployment, decoding strategies from language generation can be successfully transferred to action streams, enabling efficient solution search and task performance improvements.
Through extensive evaluations on the simulation benchmark and real-world robotic setups, we demonstrate that the Action Stream paradigm achieves improved task performance when extending the generation horizon, representing a significant step toward unified vision-language-action modeling.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided abstract and metadata. Let me analyze the content:

The paper is titled "From Language to Action Streams: Bridging LLM Autoregression for Long-Horizon Robot Action Prediction" - it proposes an "Action Stream" paradigm for Vision-Language-Action (VLA) models.

Key points:
1. Problem: Current VLA models use "Action-as-Language" but limit action prediction to fixed-length, single-step token sequences, limiting the generation horizon
2. Method: Action Stream paradigm with two-phase training: L-BC (Long-horizon Behavior Cloning) and S-AA (Step-wise Action Alignment)
3. Experiments: Simulation benchmark and real-world robotic setups
4. Resources: Not mentioned in the abstract
5. Conclusions: Action Stream achieves improved task performance with extended generation horizon

Let me organize this into a structured Chinese summary following the requested 8 points.
</think>
# 《从语言到动作流：面向长时序机器人动作预测的LLM自回归桥接》论文总结

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（VLA）模型是机器人控制的新范式，借助预训练视觉-语言模型（VLM）将自然语言指令与视觉观测直接翻译为底层动作。
- **核心思路**："Action-as-Language" 即将动作空间离散化为 token，利用大语言模型（LLM）的自回归生成能力，将动作预测转化为标准的序列语言生成任务。
- **现有局限**：
  - 现有实现仅利用 LLM 的一小部分生成潜力；
  - 动作预测被限制为**固定长度、单步的 token 序列**；
  - 策略的**生成时域（horizon）受限**，难以应对复杂长时序任务。
- **研究目标**：打破固定长度限制，使 VLA 模型能够像语言模型生成长文本一样，自回归地生成长链动作序列（"动作流"），从而增强长视野规划与执行能力。

## 2. 方法论

### 2.1 核心思想：Action Stream（动作流）范式
- 定制 LLM 的训练与推理流程，使其适配 VLA 模型；
- 让模型生成**扩展的动作 token 链**，从而实现**隐式的长时序生成**；
- 语言生成领域的解码策略（如采样、束搜索等）可直接迁移到动作流，提升任务表现。

### 2.2 两阶段训练方案
- **阶段一：长时序行为克隆（Long-horizon Behavior Cloning, L-BC）**
  - 目标：使 VLA 模型能够生成**连贯的多步动作序列**；
  - 作用：扩展策略在时间维度上的生成能力。
- **阶段二：逐步动作对齐（Step-wise Action Alignment, S-AA）**
  - 目标：缓解自回归推理过程中的**曝光偏差（exposure bias）**；
  - 作用：在长序列生成时减少误差累积，使生成的轨迹更稳定。

### 2.3 推理阶段
- 将语言模型中成熟的解码策略直接复用到动作流生成中；
- 通过高效的解空间搜索（如采样策略调整）提升任务执行表现。

## 3. 实验设计

- **仿真基准**：使用仿真环境下的 benchmark 进行系统评估（具体 benchmark 名称在摘要中未明确列出，参考元数据推测可能涉及 rob-il 相关基准）。
- **真实机器人实验**：在真实机器人平台上进行部署验证，检验从仿真到真实的迁移效果。
- **对比方法**：摘要中未列出具体对比方法的名称，仅强调"extensive evaluations"。可能对比对象包括：
  - 固定长度单步动作预测的基线 VLA 方法；
  - 现有"Action-as-Language"实现的代表性工作。

## 4. 资源与算力

- 论文摘要与元数据中**未明确说明**所使用的 GPU 型号、数量、训练时长等算力细节；
- 仅能确认方法基于预训练 VLM/LLM 进行微调（具体基础模型未在摘要中给出）。

## 5. 实验数量与充分性

- **实验维度**：
  - 仿真 benchmark 测试；
  - 真实机器人部署测试；
  - 强调"extensive evaluations"，暗示包含多场景、多任务的对比；
- **是否充分**：从摘要来看，实验覆盖了仿真与真实两个层面，并针对"延长生成时域"这一核心论点展开；但摘要未披露具体的消融实验（如 L-BC 与 S-AA 各自贡献的消融、不同动作流长度的对比等）的细节，因此实验充分性需结合正文进一步评估。
- **客观性与公平性**：摘要未透露具体基线选择、随机种子、统计显著性检验等信息，无法从摘要层面判断公平性。

## 6. 主要结论与发现

- Action Stream 范式能够有效扩展 VLA 策略的**生成时域**；
- 在仿真与真实机器人平台上均验证了**任务性能随生成时域延长而提升**的现象；
- L-BC + S-AA 的两阶段训练框架可同时实现长序列生成与误差累积的抑制；
- 验证了语言生成领域的解码策略可成功迁移至动作流生成；
- 代表了向**统一视觉-语言-动作建模**方向迈出的重要一步。

## 7. 优点与亮点

- **范式创新**：将 LLM 的长文本自回归生成能力显式拓展到动作预测领域，提出"动作流"概念，突破了固定长度的限制；
- **方法组合巧妙**：L-BC 负责"学会生成长链"，S-AA 负责"解决误差累积"，二者形成互补的闭环；
- **跨域迁移性强**：自然语言领域的解码与推理技巧可直接迁移到动作流，工程上易于复用；
- **虚实结合验证**：同时在仿真和真实机器人上验证，提升了结论的实用价值；
- **面向统一建模**：为通用 VLA 模型处理复杂长时序任务提供了可扩展的生成框架。

## 8. 不足与局限

- **细节披露不足**：摘要中未说明基线模型、具体 benchmark 名称、动作空间离散化方案、所用基础 VLM/LLM 等关键信息，需查阅正文；
- **算力与可复现性**：未披露训练算力与超参设置，第三方复现存在一定门槛；
- **长时序生成的风险**：虽然 S-AA 旨在缓解曝光偏差，但长自回归序列仍可能产生误差累积与分布漂移，摘要未给出量化分析；
- **动作离散化的固有局限**：将动作离散化为 token 不可避免地带来量化误差，对高精度控制任务（如接触丰富、力控任务）的适用性存疑；
- **实验充分性存疑**：摘要未提及消融实验、不同动作流长度的对比、跨任务泛化等细节，实验覆盖广度有待正文确认；
- **应用范围限制**：当前主要面向已有大规模演示数据的模仿学习范式，对于无数据或低数据场景的扩展能力未涉及。

（完）
