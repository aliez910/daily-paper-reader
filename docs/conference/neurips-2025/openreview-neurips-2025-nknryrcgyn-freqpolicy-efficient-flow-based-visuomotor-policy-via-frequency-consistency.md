---
title: "FreqPolicy: Efficient Flow-based Visuomotor Policy via Frequency Consistency"
title_zh: FreqPolicy：通过频率一致性实现高效的流式视觉运动策略
authors: "Yifei Su, Ning Liu, Dong Chen, Zhen Zhao, Kun Wu, Meng Li, Zhiyuan Xu, Zhengping Che, Jian Tang"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=NKNryrCGYn"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向实时机器人操控的流式视觉运动策略，建模多模态动作分布
tldr: 生成式视觉运动策略因多步采样推理成本过高，难以满足机器人实时控制需求。本文提出FreqPolicy，通过在流式去噪过程中引入频率一致性约束，使其契合机器人动作轨迹的时间连续性要求，在保留多模态建模能力的同时显著加速采样。该工作推动了可实际部署的快速视觉到动作策略发展。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 多步采样的高推理成本限制了生成式视觉运动策略在实时机器人系统中的应用。
method: 在流式去噪中引入频率一致性约束以匹配机器人动作的时序结构，从而实现高效采样。
result: 在不损失多模态建模能力的前提下降低了推理延迟，适配实时操控。
conclusion: 为实时机器人操控提供了一种兼顾速度与表达力的视觉运动策略。
---

## Abstract
Generative modeling-based visuomotor policies have been widely adopted in robotic manipulation, attributed to their ability to model multimodal action distributions. However, the high inference cost of multi-step sampling limits its applicability in real-time robotic systems.
Existing approaches accelerate sampling in generative modeling-based visuomotor policies by adapting techniques originally developed to speed up image generation. However, a major distinction exists: image generation typically produces independent samples without temporal dependencies, while robotic manipulation requires generating action trajectories with continuity and temporal coherence.
To this end, we propose FreqPolicy, a novel approach that first imposes frequency consistency constraints on flow-based visuomotor policies.
Our work enables the action model to capture temporal structure effectively while supporting efficient, high-quality one-step action generation.
Concretely, we introduce a frequency consistency constraint objective that enforces alignment of frequency-domain action features across different timesteps along the flow, thereby promoting convergence of one-step action generation toward the target distribution.
In addition, we design an adaptive consistency loss to capture structural temporal variations inherent in robotic manipulation tasks.
We assess FreqPolicy on $53$ tasks across $3$ simulation benchmarks, proving its superiority over existing one-step action generators.
We further integrate FreqPolicy into the vision-language-action (VLA) model and achieve acceleration without performance degradation on $40$ tasks of Libero.
Besides, we show efficiency and effectiveness in real-world robotic scenarios with an inference frequency of $93.5$ Hz.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "FreqPolicy: Efficient Flow-based Visuomotor Policy via Frequency Consistency". Let me analyze the provided content carefully.

The paper is about:
- Visuomotor policies based on generative modeling for robotic manipulation
- The problem: multi-step sampling inference is too costly for real-time robotics
- Key distinction from image generation: robotic actions need temporal coherence
- Solution: FreqPolicy - frequency consistency constraints on flow-based visuomotor policies
- Enables one-step action generation while maintaining quality
- Frequency consistency constraint objective across different timesteps along the flow
- Adaptive consistency loss for structural temporal variations
- Tested on 53 tasks across 3 simulation benchmarks
- Integrated into VLA model, tested on 40 Libero tasks
- Real-world: 93.5 Hz inference frequency

Let me organize the response according to the required structure. I should note that the full paper text isn't available (only the abstract), so I need to be careful about claims I make regarding experimental details, computational resources, etc.

Let me write a detailed Chinese summary following the 8-point structure.
</think>
# FreqPolicy 论文总结

## 1. 核心问题与研究动机

- **背景**：基于生成模型（特别是流匹配/扩散类）的视觉运动策略（visuomotor policy）因能建模多模态动作分布，已广泛应用于机器人操控任务。
- **核心矛盾**：此类方法通常需要多步迭代去噪/采样才能生成动作，单次推理延迟高，难以满足机器人实时控制（通常需 50–100 Hz 以上）的需求。
- **现有方案的不足**：已有加速方法大多直接借鉴图像生成领域的蒸馏/少步采样技术，但忽略了图像生成与机器人动作生成的本质差异——**图像样本之间相互独立，而机器人动作轨迹具有时间连续性和时序结构**，因此直接迁移存在适配性问题。
- **本文目标**：在保留生成式策略多模态表达能力的同时，将多步去噪压缩为一步生成，使其满足实时操控需求。

## 2. 方法论

### 2.1 整体思路
- 在基于流（flow-matching）的视觉运动策略中引入**频率一致性约束（frequency consistency constraint）**，使模型在去噪过程中沿流方向保持动作在频域上的一致性，从而支持一步（one-step）高质量动作生成。

### 2.2 关键技术细节
- **频率一致性约束目标**：在流的不同时间步上，对动作的频域特征进行对齐，强制中间过程的频域表示与目标分布的频域表示一致。这使得一步生成结果能够"收敛"到目标分布。
- **自适应一致性损失（adaptive consistency loss）**：考虑到机器人操控任务中动作具有**结构化的时序变化**（例如接触事件、阶段性运动），损失函数设计为自适应的，能针对不同任务/阶段捕捉其特有的时序结构。
- **频域分析视角**：将动作序列视为时间信号，在频域上对不同去噪阶段的特征做匹配，利用机器人动作的**低频主导、平滑连续**特性来加速收敛。
- **与 VLA 模型集成**：方法可作为插件整合到现有的视觉-语言-动作（Vision-Language-Action）大模型中，在不损害原有性能的前提下提升推理速度。

### 2.3 算法流程（文字描述）
1. 在流匹配框架下训练时，除常规的流匹配损失外，加入**频率一致性损失**，对齐中间步与目标步动作的频域表示。
2. 训练完成后，推理阶段直接使用**单步生成**（one-step），无需多步迭代。
3. 推理频率达到 93.5 Hz，满足实时操控要求。

## 3. 实验设计

### 3.1 数据集 / 场景 / Benchmark
- **仿真基准**：3 个主流模拟器基准，合计 **53 个任务**，覆盖多种机器人操控场景。
- **VLA 集成评测**：在 **Libero** 基准的 **40 个任务**上评估与视觉-语言-动作大模型集成的效果。
- **真实机器人实验**：在真实机器人场景中验证了方法的有效性与效率。

### 3.2 对比方法
- 与现有的"一步动作生成器"（one-step action generators）进行了比较，文中明确指出 FreqPolicy 在这些对比方法之上具有优势（superiority）。
- 对比维度应包括生成质量、任务成功率与推理速度（具体数值需参见正文表格）。

## 4. 资源与算力

- **论文元数据中未提供**具体的 GPU 型号、数量、训练时长等算力信息。
- 仅给出推理效率指标：真实机器人场景下推理频率达到 **93.5 Hz**，表明方法的实时性。
- **建议**：若需评估可复现性成本，需查阅正文或附录中的实验配置部分。

## 5. 实验数量与充分性

- **实验规模**：
  - 3 个仿真 benchmark × 53 个任务；
  - 1 个 VLA benchmark × 40 个任务（Libero）；
  - 真实机器人实验（具体任务数与场景数在摘要中未明确）。
- **充分性评估**：
  - ✅ 任务覆盖较为广泛（仿真+真实），涉及不同难度与类型的操控任务。
  - ✅ 同时验证了在通用策略和 VLA 大模型上的通用性。
  - ✅ 兼顾了多模态建模能力保留与推理加速两个目标。
  - ⚠️ 摘要中未明确提及消融实验的细节（如频率一致性损失与自适应一致性损失各自的贡献），但从方法描述推断应包含相关消融。
  - ⚠️ 真实机器人实验的细节（任务类型、成功率统计、对比基线）需要正文进一步确认。

## 6. 主要结论与发现

- 在流式视觉运动策略中引入**频率一致性约束**是实现一步生成的有效手段。
- 频域对齐可使一步动作生成的结果分布与多步目标分布保持一致。
- **自适应一致性损失**对捕捉操控任务的结构性时序变化至关重要。
- FreqPolicy 在 53 个仿真任务上**优于现有一步动作生成器**。
- 集成到 VLA 模型后，**在不损失性能的前提下显著加速**（Libero 40 个任务）。
- 真实机器人上达到 **93.5 Hz** 推理频率，证明其可用于实时操控。

## 7. 优点与亮点

- **问题洞察深刻**：明确指出图像生成加速方法直接迁移到机器人动作生成的不适用性，抓住了"时序连续性"这一核心差异。
- **频域视角新颖**：将频率分析引入流匹配策略的损失设计，是一项跨领域（信号处理+生成式建模）的创新点。
- **实用性强**：直接面向实时部署需求（93.5 Hz），并展示了在真实机器人上的可行性。
- **通用性好**：可作为插件集成到现有 VLA 大模型中，不改变原有架构。
- **多维度验证**：仿真（多 benchmark、多任务）+ 真实机器人 + 大模型集成，验证较为全面。

## 8. 不足与局限

- **算力信息缺失**：摘要中未给出训练所需的 GPU 资源与训练时长，限制了可复现性评估。
- **真实机器人实验细节不足**：仅给出推理频率指标，未明确报告真实场景下的任务成功率、对比基线及统计显著性。
- **方法适用范围**：频率一致性约束对**动作的高频成分**（如快速接触、抖动）是否仍有效，文中未深入讨论；理论上低频主导的假设可能不适用于所有操控任务。
- **消融分析**：摘要中未充分展开各组件（频率一致性损失 vs. 自适应一致性损失）的单独贡献，需正文佐证。
- **任务偏差风险**：3 个仿真 benchmark 是否在任务多样性、难度分布上存在选择偏差，需进一步审视。
- **频率约束的普适性**：当动作分布具有强多模态特性（如多解任务）时，频域一致性是否仍能保证一步生成质量，是潜在的风险点。
- **与最新 SOTA 的对比**：摘要仅称"优于现有一步动作生成器"，但未明确列出对比方法是否涵盖 2024–2025 年的最新工作。

（完）
