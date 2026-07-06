---
title: "PRISM: Performer RS-IMLE for Single-pass Multisensory Imitation Learning"
title_zh: PRISM：基于Performer RS-IMLE的单次前向多感官模仿学习
authors: "Amisha Bhaskar, Pratap Tokekar, Stefano Di Cairano, Alexander Schperberg"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=icnIadBCoR"
tags: ["query:rob-il"]
score: 8.0
evidence: 单次前向多模态模仿学习策略，在多个操控基准上验证
tldr: 针对现有生成式模仿学习方法难以同时满足多模态动作建模、实时控制与多传感融合的问题，本文提出PRISM，基于批全局拒绝采样IMLE与时间多感官编码器，结合Performer线性注意力生成器构成单次前向策略。该方法可建模多模态动作分布，融合RGB、深度、触觉、声音与本体感知，并在MetaWorld、CALVIN、Robomimic等操控基准上完成验证。PRISM为复杂操控任务提供了一种高效且统一的多感官模仿学习框架。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有模仿学习方法难以同时兼顾多模态动作建模、实时控制速率与多传感融合的需求。
method: 提出PRISM，使用批全局拒绝采样IMLE结合时间多感官编码器与Performer线性注意力生成器。
result: 在MetaWorld、CALVIN、Robomimic等操控基准上完成验证，兼顾多模态动作分布与实时控制。
conclusion: PRISM为复杂机器人操控任务提供了一种高效统一的多感官模仿学习解决方案。
---

## Abstract
Robotic imitation learning typically requires models that capture multimodal action distributions while operating in real-time control rates and accommodating multiple sensing modalities. Although recent generative approaches such as diffusion models, flow matching, and Implicit Maximum Likelihood Estimation (IMLE) have achieved promising results in this domain, they satisfy only a subset of these requirements. To satisfy these requirements, we introduce PRISM, based on a batch-global rejection-sampling variant of IMLE. PRISM is a single-pass policy that couples a temporal multisensory encoder (e.g, RGB, Depth, tactile, audio, proprioception) with a linear-attention generator using a Performer architecture. We validate on MetaWorld, CALVIN, Robomimic, and a real hardware suite using a Unitree Go2 with a 7-DoF arm, wrist and shoulder RGB, tactile, audio, and proprioception sensors. PRISM matches or outperforms diffusion, flow-matching, and prior IMLE policies in terms of task success rates, robustness, and sample efficiency. In CALVIN with 10\% of the data, PRISM improves the success rate by $\sim$ 10\% over IMLE, $\sim$ 20\% over flow matching, and $\sim$ 25\% over diffusion, while reducing the jerk by about $20\times$. On MetaWorld, PRISM is 5-12\% on Hard/Very-Hard splits over diffusion and flow baselines. Real-world loco-manipulation shows 10--25\% higher success and maintains faster inference diffusion policy. These results position PRISM as a fast, accurate, and multisensory imitation policy that retains multimodal action coverage without iterative sampling.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "PRISM: Performer RS-IMLE for Single-pass Multisensory Imitation Learning" based on the provided metadata and abstract. Let me organize the content according to the 8 requested points.

The paper is about imitation learning for robotics. Key points:
- Single-pass policy (single forward pass)
- Combines batch-global rejection-sampling IMLE with Performer linear attention
- Multisensory encoder (RGB, Depth, tactile, audio, proprioception)
- Validated on MetaWorld, CALVIN, Robomimic, and real hardware (Unitree Go2 with 7-DoF arm)
- Outperforms diffusion, flow-matching, and prior IMLE in success rates, robustness, sample efficiency
- In CALVIN with 10% data, improves ~10% over IMLE, ~20% over flow matching, ~25% over diffusion
- Reduces jerk by ~20x
- On MetaWorld Hard/Very-Hard splits, 5-12% improvement
- Real-world loco-manipulation: 10-25% higher success

Let me write a structured summary.
</think>
# PRISM 论文总结

## 1. 核心问题与研究动机

- **核心问题**：机器人模仿学习（Imitation Learning）需要同时满足三项相互冲突的需求：
  1. 对**多模态动作分布**（multimodal action distributions）的精确建模；
  2. **实时控制频率**（real-time control rates）的推理速度；
  3. 对**多传感模态**（RGB、深度、触觉、声音、本体感知等）的融合。
- **现有方法局限**：当前主流的生成式方法（Diffusion、Flow Matching、IMLE）只能满足上述需求的子集。例如：
  - 扩散模型与 Flow Matching 需要**多步迭代采样**，延迟较高；
  - 传统 IMLE 虽能单次前向，但难以同时融合多传感器与建模多模态动作。
- **整体目标**：提出一种**单次前向（single-pass）**的策略，能够在保持高控制频率的同时，融合多种传感模态并准确建模多模态动作分布。

---

## 2. 方法论

### 核心思想
- 提出 **PRISM（Performer RS-IMLE）**：将 **批全局拒绝采样 IMLE（Batch-Global Rejection-Sampling IMLE）** 与 **Performer 线性注意力生成器** 相结合，构建单次前向模仿学习策略。

### 关键技术细节
1. **批全局拒绝采样 IMLE（RS-IMLE）**：
   - 传统 IMLE 通过从噪声中采样候选动作并选择与专家最接近的样本来隐式建模多模态分布。
   - PRISM 在 **整个 batch 层面**进行拒绝采样，使得采样过程更加全局化，能更好地覆盖多模态动作模式。
2. **时间多感官编码器（Temporal Multisensory Encoder）**：
   - 接收并融合时间序列上的多种传感信号：RGB、深度、触觉、声音、本体感知。
   - 对时间维度上的多模态信息进行联合编码。
3. **Performer 线性注意力生成器**：
   - 使用 Performer 架构（一种基于随机特征近似的线性注意力 Transformer）作为动作生成器。
   - 避免标准自注意力的二次复杂度，实现**线性时间推理**，满足实时控制需求。
4. **整体流程**：
   - 输入：多模态时间序列传感器数据；
   - 编码：时间多感官编码器 → 融合特征；
   - 生成：Performer 生成器单次前向输出动作；
   - 训练目标：基于批全局拒绝采样的 IMLE 损失。

---

## 3. 实验设计

### 数据集 / 仿真基准
- **MetaWorld**：机器人操控基准，特别是 Hard / Very-Hard 难度划分。
- **CALVIN**：长时序语言条件操控基准，使用 **仅 10% 数据**的低数据量设置。
- **Robomimic**：单任务与多任务模仿学习基准。
- **真实硬件**：Unitree Go2 四足机器人 + 7-DoF 机械臂，配备腕部/肩部 RGB、触觉、声音与本体感知传感器，测试**足式操控（loco-manipulation）**。

### 对比方法
- Diffusion policy
- Flow Matching policy
- Prior IMLE policy（即传统 IMLE 基线）
- 还包含与自身在**推理速度**上的对比。

### 评估指标
- 任务成功率（Success Rate）
- 鲁棒性（Robustness）
- 样本效率（Sample Efficiency）
- 动作平滑度（Jerk，越小越平滑）
- 推理延迟（Inference Speed）

---

## 4. 资源与算力

- 论文元数据与摘要中**未明确说明**所使用的 GPU 型号、数量以及训练时长等具体算力信息。
- 仅可推断：方法强调 **Performer 线性注意力** 带来的低推理复杂度，暗示其对算力需求较低，适合实时部署。

---

## 5. 实验数量与充分性

- **基准覆盖**：覆盖 3 个主流仿真基准（MetaWorld、CALVIN、Robomimic）+ 1 个真实硬件平台，**sim-to-real 验证较为充分**。
- **数据量变化**：在 CALVIN 上特别测试了 10% 低数据量场景，验证了样本效率。
- **多难度划分**：MetaWorld 上区分 Hard / Very-Hard 难度。
- **未明确提及**：从已有摘要中**未见详尽的消融实验**（例如单独验证 Performer、RS-IMLE、时间多感官编码器各自贡献的 ablation）。这是潜在的充分性缺口。
- **公平性**：在统一基准、统一指标下与 diffusion、flow matching、IMLE 横向对比，方法学上较为公平；但摘要中未提及是否控制了随机种子数、试验次数等。

---

## 6. 主要结论与发现

- **任务成功率**：在 MetaWorld Hard / Very-Hard 划分上，PRISM 较 diffusion 和 flow matching 基线提升 **5–12%**。
- **低数据量优势**：在 CALVIN 仅 10% 数据下，PRISM 相比 IMLE 提升 **~10%**，相比 Flow Matching 提升 **~20%**，相比 Diffusion 提升 **~25%**。
- **动作平滑性**：Jerk 降低约 **20 倍**，说明生成的动作轨迹更加平滑，更适合实际机器人执行。
- **实时性**：单次前向推理速度优于 diffusion policy。
- **真实硬件**：足式操控任务成功率比基线高 **10–25%**。
- **总体定位**：PRISM 是一种**快速、准确、多感官融合**的模仿学习策略，且**无需迭代采样**即可保持多模态动作覆盖能力。

---

## 7. 优点 / 亮点

- **单次前向 + 多模态动作建模**：克服了扩散 / Flow Matching 需多步迭代采样的延迟问题，同时保留多模态分布建模能力。
- **多传感融合的统一框架**：在同一策略中同时支持 RGB、深度、触觉、声音、本体感知，适用范围广。
- **样本效率突出**：在 10% 数据量下仍能大幅超越基线，对数据稀缺场景尤为重要。
- **动作平滑度显著提升**：~20× 的 Jerk 降低对于实际机器人执行（减少机械磨损、提升稳定性）具有实际价值。
- **Sim-to-Real 验证完整**：仿真 + 真实硬件（Unitree Go2 + 7-DoF 臂）双重验证，提升了结论的可信度。
- **Performer 架构的引入**：线性注意力降低了计算复杂度，便于嵌入式或实时部署。

---

## 8. 不足与局限

- **消融实验不足**：从摘要与元数据中未看到对各个组件（Performer、批全局拒绝采样、时间多感官编码器）的独立消融，难以判断各部分的边际贡献。
- **算力与可复现性信息缺失**：未公布 GPU 型号、训练时长、随机种子等关键信息，可能影响复现。
- **多传感模态的贡献未拆分**：未明确说明去掉某一传感模态（如触觉或声音）后性能下降多少，难以评估各模态的相对重要性。
- **真实硬件实验规模有限**：仅在一种机器人平台（Unitree Go2 + 7-DoF 臂）上验证，跨平台泛化能力有待进一步验证。
- **"批全局拒绝采样" 的理论分析薄弱**：摘要未深入解释该变体为何优于原始 IMLE，缺乏理论收敛性或偏差-方差分析。
- **长时序任务挑战**：CALVIN 是长时序任务，但摘要主要关注成功率与 Jerk，对**长时序预测误差累积**等问题未深入讨论。
- **对比基线版本不明**：未指明所对比的 diffusion / flow matching / IMLE 基线是哪个具体版本或实现，可能存在实现差异带来的偏差。

（完）
