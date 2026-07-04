---
title: "DiffusionVLA: Scaling Robot Foundation Models via Unified Diffusion and Autoregression"
title_zh: DiffusionVLA：通过统一扩散与自回归扩展机器人基础模型
authors: "Junjie Wen, Yichen Zhu, Minjie Zhu, Zhibin Tang, Jinming Li, Zhongyi Zhou, Xiaoyu Liu, Chaomin Shen, Yaxin Peng, Feifei Feng"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=VdwdU81Uzy"
tags: ["query:rob-il"]
score: 9.0
evidence: 统一扩散与自回归的视觉-语言-动作机器人模型框架
tldr: 自回归视觉-语言-动作模型缺乏精确动作生成，而扩散策略缺乏推理能力。本文提出DiffusionVLA，通过将自回归推理注入扩散策略，实现推理与动作生成的紧耦合。该方法简单灵活，实验表明其性能和鲁棒性均有提升，为机器人基础模型提供了新范式。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有方法中，VLAs动作精度不足，扩散策略缺乏推理能力，需要统一框架。
method: 预训练VLM产生自回归推理短语，通过推理注入模块嵌入扩散策略学习过程。
result: 在多个任务上验证了该方法的有效性和效率提升。
conclusion: DiffusionVLA实现了推理与动作生成的协同，促进了机器人基础模型的发展。
---

## Abstract
In this paper, we present DiffusionVLA, a novel framework that integrates autoregressive reasoning with diffusion policies to address the limitations of existing methods: while autoregressive Vision-Language-Action (VLA) models lack precise and robust action generation, diffusion-based policies inherently lack reasoning capabilities. Central to our approach is autoregressive reasoning — a task decomposition and explanation process enabled by a pre-trained VLM — to guide diffusion-based action policies. To tightly couple reasoning with action generation, we introduce a reasoning injection module that directly embeds self-generated reasoning phrases into the policy learning process. The framework is simple, flexible, and efficient, enabling seamless deployment across diverse robotic platforms.

We conduct extensive experiments using multiple real robots to validate the effectiveness of DiVLA. Our tests include a challenging factory sorting task, where DiVLA successfully categorizes objects, including those not seen during training. The reasoning injection module enhances interpretability, enabling explicit failure diagnosis by visualizing the model’s decision process. Additionally, we test DiVLA on a zero-shot bin-picking task, achieving \textbf{63.7\% accuracy on 102 previously unseen objects}. Our method demonstrates robustness to visual changes, such as distractors and new backgrounds, and easily adapts to new embodiments. Furthermore, DiVLA can follow novel instructions and retain conversational ability. Notably, DiVLA is data-efficient and fast at inference; our smallest DiVLA-2B runs 82Hz on a single A6000 GPU. Finally, we scale the model from 2B to 72B parameters, showcasing improved generalization capabilities with increased model size.

---

## 论文详细总结（自动生成）

# 论文总结：DiffusionVLA

## 1. 核心问题与整体含义（研究动机和背景）
- **研究动机**：现有的视觉-语言-动作（VLA）模型（基于自回归）在动作生成上缺乏精确性和鲁棒性；而基于扩散的策略则缺少推理能力（如任务分解、解释、故障诊断）。两者的优势不能兼得。
- **核心问题**：如何将自回归推理与扩散动作策略紧密结合，使机器人基础模型既能高效推理又能生成精细、稳健的动作。
- **整体含义**：本文提出**DiffusionVLA（DiVLA）**，通过将自回归推理注入扩散策略，实现推理与动作的紧耦合，为构建可扩展的机器人基础模型提供新范式。

## 2. 论文提出的方法论
- **核心思想**：利用预训练视觉语言模型（VLM）生成自回归推理短语（任务分解与解释），再通过一个**推理注入模块**将这些推理信息直接嵌入扩散策略的学习过程，使动作生成受推理指导。
- **关键技术细节**：
  - **自回归推理**：VLM对当前任务进行分解和自主解释，输出推理短语。
  - **推理注入模块**：将推理短语作为条件信号，嵌入到扩散模型的去噪过程中，从而紧密耦合推理与动作生成。
  - **整体框架**：简单、灵活、高效，可直接部署于不同机器人平台。
- **公式/算法流程**（文字说明）：
  1. 输入视觉观测和语言指令。
  2. 预训练VLM生成自回归推理短语（例如：“首先抓住红色方块，然后放入左侧槽中”）。
  3. 推理注入模块将推理短语编码为特征，与视觉/语言特征一起作为扩散策略的条件。
  4. 扩散策略以条件信息逐步去噪，输出精确的动作序列。

## 3. 实验设计
- **数据集/场景**：
  - 挑战性**工厂分类任务**：包括训练中未见过的物体，考验泛化。
  - **零样本拣选任务**：在102个全新物体上进行，报告**63.7%准确率**。
  - **视觉鲁棒性测试**：引入干扰物、改变背景。
  - **新指令遵循与对话能力**：验证模型对新颖指令的响应和保持对话连贯性的能力。
  - **多形态适应**：测试在不同机器人本体上的易适配性。
- **Benchmark**：未明确提及统一基准，但通过多个真实机器人任务进行综合评估。
- **对比方法**：abstract未列出具体对比方法，但基于问题背景应对比自回归VLA模型与纯扩散策略模型（如RT-2、扩散策略等）；消融实验应包含有无推理注入模块的对比。

## 4. 资源与算力
- **推理算力**：最小的DiVLA-2B模型在单张A6000 GPU上达到**82Hz**，推理效率高。
- **训练算力**：论文正文（未提供）中可能涉及训练时间及GPU数量，但根据现有abstract信息**未明确说明**训练所使用的具体算力规模（例如GPU数量、训练时长等）。

## 5. 实验数量与充分性
- **实验数量与多样性**：涵盖：
  - 多任务（工厂分类、零样本拣选、视觉鲁棒性、新指令、对话）。
  - 多机器人（多个真实机器人平台）。
  - 多规模（模型参数从2B扩展到72B）。
- **充分性**：实验覆盖面较广，验证了泛化性、鲁棒性、可解释性、数据效率与扩展性，具备一定的综合性。但由于缺少全文细节，无法判断消融实验的完整性和对比方法的全面性。
- **公平性**：在真实机器人上进行的实验条件较为客观；未提及与SOTA方法的数值比较细节，需正文补充。

## 6. 主要结论与发现
- **推理与动作的协同**：将自回归推理注入扩散策略后，模型动作精度和鲁棒性显著提升，同时保留了推理能力。
- **可解释性**：推理注入模块使得模型能够显式输出决策过程，支持故障诊断。
- **数据高效**：在有限数据下仍能取得良好性能（推理短语带来额外监督）。
- **快速推理**：2B模型可达82Hz，满足实时控制需求。
- **规模扩展有效**：参数从2B增至72B，泛化能力持续提升，验证了scaling law在机器人基础模型中的适用性。

## 7. 优点
- **方法设计**：简单、灵活、即插即用，易于迁移到不同机器人平台。
- **融合优势**：集VLM的推理能力与扩散策略的动作精确性于一身，弥补了各自短板。
- **可解释性**：通过自回归推理短语显式展示模型决策过程，为错误诊断和调试提供依据。
- **数据效率与推理速度**：在较低计算开销下实现高性能，适合实际部署。
- **扩展性良好**：模型规模增大时性能持续提升，具备成为基础模型的潜力。

## 8. 不足与局限
- **实验细节缺失**：由于只提供了摘要，无法评估对比方法是否全面、消融实验是否严谨、各模块的贡献量化等。
- **VLM依赖**：方法依赖预训练VLM的推理质量，若VLM产生错误推理，可能误导动作策略；VLM的规模和部署开销未充分讨论。
- **场景覆盖有限**：目前验证于桌面操作任务，尚未在更复杂或动态环境（如移动操作、长时家庭任务）中测试。
- **鲁棒性测试**：虽然测试了视觉变化，但对对抗性干扰或传感器噪声的鲁棒性未见分析。
- **训练算力未公开**：缺乏训练成本数据，难以评估其可复现性和资源门槛。

（完）
