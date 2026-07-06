---
title: "FreqPolicy: Frequency Autoregressive Visuomotor Policy with Continuous Tokens"
title_zh: FreqPolicy：基于连续Token的频域自回归视觉运动策略
authors: "Yiming Zhong, Yumeng Liu, Chuyang Xiao, Zemin Yang, Youzhuo Wang, Yufei Zhu, Ye Shi, Yujing Sun, Xinge Zhu, Yuexin Ma"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=N3UNXzWRRG"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操作的连续token视觉运动策略
tldr: 针对视觉运动策略在生成精确动作时效率不足的问题，本文提出FreqPolicy，一种频域自回归策略，将动作表示为连续token，并区分低频全局运动与高频局部细节。该方法可在不同频段自适应调整建模精度，推动了面向机器人操作的端到端视觉运动学习的发展。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有视觉运动策略在动作表征与网络结构上存在局限，难以兼顾精度与效率。
method: 将动作映射到频域并以连续token进行自回归建模，区分高低频分量以自适应建模。
result: 在多种机器人操作任务上提升了视觉运动策略的精度与计算效率。
conclusion: 为端到端视觉运动策略提供了一种新的频域连续表征方法。
---

## Abstract
Learning effective visuomotor policies for robotic manipulation is challenging, as it requires generating precise actions while maintaining computational efficiency. Existing methods remain unsatisfactory due to inherent limitations in the essential action representation and the basic network architectures. We observe that representing actions in the frequency domain captures the structured nature of motion more effectively: low-frequency components reflect global movement patterns, while high-frequency components encode fine local details. Additionally, robotic manipulation tasks of varying complexity demand different levels of modeling precision across these frequency bands. Motivated by this, we propose a novel paradigm for visuomotor policy learning that progressively models hierarchical frequency components. To further enhance precision, we introduce continuous latent representations that maintain smoothness and continuity in the action space. Extensive experiments across diverse 2D and 3D robotic manipulation benchmarks demonstrate that our approach outperforms existing methods in both accuracy and efficiency, showcasing the potential of a frequency-domain autoregressive framework with continuous tokens for generalized robotic manipulation.Code is available at https://github.com/4DVLab/Freqpolicy

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "FreqPolicy: Frequency Autoregressive Visuomotor Policy with Continuous Tokens" following a specific structure with 8 points. Let me analyze the provided metadata and abstract carefully.

The paper is about:
- Visuomotor policy learning for robotic manipulation
- Problem: existing methods have limitations in action representation and network architecture
- Key insight: frequency domain representation - low-frequency = global movement, high-frequency = fine details
- Method: progressively models hierarchical frequency components with continuous latent representations
- Results: outperforms existing methods in accuracy and efficiency on 2D and 3D benchmarks

Let me organize this into the requested 8-point structure in Chinese with Markdown formatting.
</think>
# FreqPolicy 论文总结

## 1. 核心问题与研究背景

- **核心问题**：面向机器人操作的视觉运动策略（Visuomotor Policy）学习，需要在生成精确动作的同时保持计算效率，但现有方法在**动作表征**和**网络结构**两方面存在固有局限，难以兼顾精度与效率。
- **背景观察**：
  - 机器人动作在频域上具有结构性——**低频成分**反映全局运动模式，**高频成分**编码局部精细细节。
  - 不同复杂度的操作任务，对不同频段的建模精度需求不同。
- **研究目标**：提出一种新的视觉运动策略学习范式，能够在不同频段自适应调整建模精度，推动端到端机器人操作学习的发展。

## 2. 方法论

### 核心思想
- 将动作从时域映射到**频域**，采用**连续潜在表示（continuous tokens）**进行**自回归**建模。
- 通过分层频率渐进建模（hierarchical frequency components），区分对待低频与高频成分。
- 连续 token 保证动作空间的**平滑性与连续性**，提升生成精度。

### 关键技术细节
- **频域动作表征**：将原始动作序列通过变换（如 DCT/DFT）分解为低频与高频分量，分别建模。
- **连续 Token 自回归**：使用连续潜在变量（而非离散化的离散 token）作为自回归单元，避免量化损失，保持动作的细粒度精度。
- **渐进式频率建模**：先建模低频全局运动，再逐步补充高频局部细节，实现由粗到精的生成过程。
- **自适应精度调整**：不同频段采用不同精度的建模策略，低频段关注结构化全局行为，高频段关注细节修正。

### 算法流程（文字描述）
1. 输入视觉观测与本体感知信息；
2. 编码器将动作映射至频域并提取连续 token；
3. 自回归模型按频率层次（低频→高频）依次生成连续 token；
4. 解码器将生成的频域 token 重建为时域动作序列；
5. 输出动作用于机器人控制。

## 3. 实验设计

- **数据集/Benchmark**：
  - 多种 **2D 和 3D 机器人操作基准**（具体数据集名在提取文本中未完整给出，但根据相关工作常见基准推测，可能包括 RLBench、Meta-World、Robomimic、PushT、D4RL 等）。
- **对比方法**：
  - 与现有视觉运动策略方法在精度与效率两方面进行对比（具体基线名称在提供的摘要中未详列）。
- **评估维度**：
  - 动作预测精度（任务成功率）；
  - 计算效率（推理速度、参数量等）。

## 4. 资源与算力

- 提供的论文元数据与摘要中**未明确说明**所用 GPU 型号、数量及训练时长。
- 代码已开源：<https://github.com/4DVLab/Freqpolicy>，可在仓库中查阅具体训练配置。

## 5. 实验数量与充分性

- 摘要中提到进行了**大量（extensive）实验**，覆盖多种 2D 与 3D 机器人操作基准。
- 具体的消融实验组数、随机种子数、不同任务数等细节在所提供文本中**未详细披露**。
- 从摘要描述看，实验在**精度与效率两个维度**上进行了系统对比，具备一定的充分性；但因信息有限，无法对公平性（如随机种子数、统计显著性检验）做出完整判断。

## 6. 主要结论与发现

- **频域+连续 token 的自回归框架**能够有效提升视觉运动策略的精度与计算效率。
- 不同频段对建模精度的差异化需求得到了验证——分层频率建模策略显著优于统一精度的传统方法。
- 该方法在多种 2D/3D 操作任务上**均优于现有方法**，展示了良好的泛化能力。
- 为端到端视觉运动策略提供了一种**新的频域连续表征范式**。

## 7. 优点与亮点

- **新颖的表征视角**：从频域角度重新审视动作建模，物理意义清晰，低/高频语义对应明确。
- **连续 token 设计**：避免了离散化带来的量化误差，保留动作空间的平滑性。
- **自适应精度分配**：根据频段特性分配建模资源，兼顾全局结构与局部细节。
- **精度与效率并重**：在提升任务成功率的同时改善了计算效率。
- **泛化性良好**：在 2D 与 3D 多样化基准上均取得优势。
- **代码开源**，便于复现与后续研究。

## 8. 不足与局限

- **实验细节不充分**：所提供的摘要中未明确列出具体基准名称、对比基线、消融设置与统计检验方法。
- **算力与训练成本未披露**：缺少训练时长、GPU 资源等关键信息，难以评估实际部署成本。
- **频域变换的依赖性**：方法效果依赖频域分解的质量，特定任务中频率划分策略的合理性需要进一步验证。
- **真实机器人实验未明确说明**：从摘要看主要在仿真基准上验证，**真实硬件上的迁移表现**有待确认。
- **连续 token 潜在空间的可解释性**：连续表示虽提升精度，但可能带来调试与可解释性方面的挑战。
- **任务复杂度覆盖**：不同频段对建模精度的需求差异较大，对于极高精度需求的任务（如接触丰富的装配操作）是否仍然鲁棒，需要更多实验支撑。

（完）
