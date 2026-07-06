---
title: Unified Latent Steering and Residual Refinement for Online Improvement of Diffusion Policy Models
title_zh: 扩散策略模型的统一隐空间引导与残差精炼在线改进
authors: "Zhengbang Zhu, Ziyan Li, Xiu Yuan, Hanbo Zhang, Yuxiao Liu, Chongjie Zhang, Yong Yu, Weinan Zhang, Minghuan Liu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=DbBD2aT1OG"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于扩散模型的视觉运动模仿策略在线改进，面向机器人操纵
tldr: 基于扩散模型的视觉运动模仿策略在机器人操纵中取得显著进展，但在分布偏移与新场景下仍显脆弱，亟需在线改进能力。本文提出USR框架，融合隐空间引导与残差精炼，无需微调策略参数即可在在线部署中高效提升扩散策略表现。该方法在保留预训练多模态分布能力的同时拓展了对演示分布之外的适应能力，为复杂机器人操纵的视觉-动作模仿学习策略提供了实用的在线改进方案。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 模仿学习扩散策略在新场景下表现脆弱，且直接微调代价高昂。
method: 提出USR框架，通过轻量级actor实现隐空间引导与残差精炼的免微调在线改进。
result: 在保留多模态分布的同时显著提升策略在新场景下的鲁棒性与适应能力。
conclusion: 隐空间引导与残差精炼的结合是扩散模仿策略在线改进的有效途径。
---

## Abstract
Imitation learning has driven major advances in robotic manipulation by exploiting large and diverse demonstrations, yet policies trained purely by imitation remain brittle under distribution shift and novel scenarios, making online improvement essential. 
Directly finetuning the parameters of modern large policies is prohibitively sample inefficient and computationally expensive,
while recent finetuning-free adaptation methods either fail to exploit the multimodal distributions learned by pretrained policies or remain confined to the coverage of demonstrations.
We propose USR, a Unified framework for latent Steering and residual Refinement that enables efficient online improvement of diffusion policy models. A lightweight actor jointly outputs latent noise to steer the diffusion process toward promising modes and residual corrections to adapt beyond the diffusion policy's support, combining stable mode selection with flexible refinement. This unified design stabilizes training and fully leverages both components. Experiments on standard benchmarks and our MultiModalBench demonstrate USR's state-of-the-art performance. Furthermore, we validate its real-world applicability by improving a Vision-Language-Action (VLA) model on a physical robot, setting a new paradigm for sample-efficient adaptation of diffusion-based policies.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of a paper based on the provided metadata. The paper is about "USR: Unified Latent Steering and Residual Refinement for Online Improvement of Diffusion Policy Models" - a framework for improving diffusion policy models in robotic imitation learning.

Let me organize the summary according to the 8 requested points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I need to be careful - the actual PDF text shows only a CAPTCHA page, but the metadata provides substantial information about the paper. I should base my summary primarily on the metadata provided, while noting that I couldn't access the full PDF.

Let me structure this well in Chinese Markdown format.
</think>
# 论文总结：USR —— 扩散策略模型的统一隐空间引导与残差精炼在线改进

> 注：原 PDF 链接需通过 CAPTCHA 验证，本总结主要基于论文元数据（标题、摘要、TLDR 等）整理而成。

## 1. 核心问题与研究动机

- **研究背景**：模仿学习（Imitation Learning）借助大规模、多样化的示教数据，在机器人操纵任务中取得显著进展。基于扩散模型（Diffusion Models）的视觉-运动策略（如 Diffusion Policy）能够建模多模态动作分布，性能突出。
- **关键痛点**：
  - 纯模仿训练得到的策略在**分布偏移**和**新场景**下表现脆弱，泛化能力不足。
  - 在线部署阶段迫切需要**在线改进（online improvement）**能力。
  - 直接对大规模预训练策略进行**参数微调**代价高昂（样本效率低、计算开销大）。
  - 现有的**免微调（finetuning-free）自适应**方法存在两类不足：① 无法充分利用预训练策略学到的多模态分布；② 改进范围被限制在示教分布的覆盖范围内。
- **核心问题**：如何在大模型时代实现**免微调、样本高效**的扩散策略在线改进，使其既能利用预训练多模态能力，又能泛化到示教分布之外？

## 2. 方法论：USR 框架

- **核心思想**：提出 **USR（Unified latent Steering and residual Refinement）** 统一框架，将"隐空间引导"与"残差精炼"融合在一个轻量级 actor 中，在**不修改预训练扩散策略参数**的前提下实现高效的在线策略改进。
- **关键技术细节**：
  - **隐空间引导（Latent Steering）**：在扩散去噪过程中，向隐变量注入由轻量 actor 预测的**隐空间噪声（latent noise）**，引导采样过程偏向更优的多模态分支，实现稳定的**多模态选择**。
  - **残差精炼（Residual Refinement）**：在扩散策略输出基础上叠加一个**残差修正项（residual correction）**，使最终动作能够突破预训练策略的支持集，扩展到**示教分布之外**的动作区域。
  - **统一联合输出**：同一个轻量 actor 同时输出 latent noise 和 residual correction，**端到端联合训练**，使两个组件相互协同——既保留稳定的多模态选择能力，又具备灵活的动作精炼能力。
  - **免微调特性**：预训练扩散策略参数冻结，仅训练该轻量 actor，计算与样本效率显著提升。
- **算法流程（文字描述）**：
  1. 输入当前观测；
  2. 预训练扩散策略按常规去噪过程生成动作；
  3. 轻量 actor 输出隐空间噪声和残差修正；
  4. 隐空间噪声用于在采样过程中引导扩散过程选择更优模式；
  5. 残差修正叠加到最终动作上以适应新场景；
  6. 通过在线交互数据联合训练 actor。

## 3. 实验设计

- **基准与场景**：
  - 在**标准机器人模仿学习基准**（如 Push-T、Robomimic、MetaWorld 等同类基准，文中提及 "standard benchmarks"）上进行系统评估。
  - 提出并使用自建的 **MultiModalBench**，专门用于评估多模态分布场景下的策略表现。
  - **真实机器人实验**：在一台物理机器人上对 **VLA（Vision-Language-Action）模型**进行在线改进，验证方法的实用价值。
- **对比方法**：
  - 隐式对比对象包括：直接微调（finetuning）、现有免微调自适应方法、以及 Diffusion Policy 基线。
  - 论文宣称在上述场景下取得 **SOTA 性能**。
- **评估指标**（基于模仿学习/RL 常见指标推断）：任务成功率、累积回报，可能还包括对多模态分布保留度的分析。

## 4. 资源与算力

- **说明**：原文 PDF 未能在本次访问中获取（仅显示 CAPTCHA 页面），因此**论文中关于 GPU 型号、数量、训练时长等具体算力信息无法直接确认**。
- 唯一可推断的算力信息：
  - 方法本身被定性为"轻量级 actor"，暗示对算力需求较低；
  - 框架"免微调"，仅需训练小规模 actor 网络，理论上训练成本远低于全参数微调；
  - 在真实机器人上完成部署实验。
- **建议**：若需精确算力信息，应进一步查阅论文正文及附录。

## 5. 实验数量与充分性

- **实验类型覆盖**（基于元数据推断）：
  - 仿真基准实验（standard benchmarks）；
  - 多模态专项评估（MultiModalBench）；
  - 真实机器人 VLA 模型在线改进实验；
  - 推测包含消融实验以验证"隐空间引导"和"残差精炼"各自贡献及其联合作用。
- **充分性评估**：
  - 优点：覆盖了**仿真 + 真实机器人**两个层级，且包含专门构造的多模态基准，并扩展到当前的 **VLA 大模型**场景，实验设计的层次感和前沿性较好。
  - 局限：仅凭元数据无法判断具体的消融维度数量、随机种子数量、统计显著性检验等细节；MultiModalBench 是否被同行广泛接受还需观察。

## 6. 主要结论与发现

- **核心结论**：将"隐空间引导"与"残差精炼"统一在同一轻量 actor 中，是**扩散模仿策略在线改进的有效途径**。
- **关键发现**：
  - 隐空间引导能稳定实现多模态模式选择，避免策略退化为单一模式；
  - 残差精炼使策略能突破示教分布支持集，泛化到新场景；
  - 二者联合训练互相促进，带来"稳定 + 灵活"的双重收益；
  - 在仿真与真实机器人上均显著优于现有免微调自适应方法；
  - 可成功用于改进 VLA 大模型，提出了一种**样本高效的大模型策略自适应新范式**。

## 7. 优点与亮点

- **方法层面**：
  - **"免微调 + 在线改进"** 切中大模型时代机器人策略部署的核心痛点；
  - 统一框架同时解决"多模态保留"和"分布外适应"两个问题，思路优雅；
  - 轻量 actor 训练成本低，**样本效率高**，适合真实机器人在线交互场景。
- **实验层面**：
  - 涵盖仿真基准、自建多模态基准和真实机器人 VLA 实验，**层层递进**；
  - 把方法推广到当前最热门的 VLA 模型上，**应用价值显著**；
  - 提出了 MultiModalBench，对社区多模态策略评估有贡献。

## 8. 不足与局限

- **信息获取限制**：原 PDF 未能成功解析，无法对方法细节、实验规模、消融设计做充分核实。
- **方法局限**（基于元数据的合理推测）：
  - 残差精炼虽然能扩展到分布外，但若 actor 学到的残差方向不当，可能引入不稳定行为；
  - 隐空间引导的强度需精细调节，过强可能破坏预训练策略的多模态结构；
  - 依赖在线交互数据，在线采集成本与安全性仍是真实部署挑战。
- **实验局限**：
  - MultiModalBench 为自建基准，**尚需社区广泛验证**；
  - 真实机器人实验规模（任务数、试验次数）未在元数据中披露，可能存在统计显著性不足风险；
  - 与各类 SOTA 免微调方法的具体差距、计算开销对比的细节不够透明。
- **应用范围**：主要针对扩散类策略，对其他类型策略（如 flow matching、transformer-based 策略）的迁移性仍待验证。

（完）
