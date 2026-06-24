---
title: "LatentVLA: Taming Latent Space for Generalizable and Long-Horizon Bimanual Manipulation"
title_zh: LatentVLA：驯服潜在空间实现通用长时域双手操作
authors: Junming Wang
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38926/42888"
tags: ["query:rob-il"]
score: 10.0
evidence: 通过潜在空间VLA框架进行双手操作的模仿学习
tldr: 当前机器人模仿学习在扩散模型的动作保真度和逆动力学模型的数据可扩展性之间存在权衡。逆动力学模型学习的潜在动作空间与物理现实脱节，导致时间纠缠等问题。为此提出LatentVLA，通过学习连续潜在空间，解耦视觉相似但动作不同的状态，实现鲁棒的长时域双手操作。在多个基准上验证了其有效性，为通用机器人操作提供了新范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38926/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38926/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1107, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38926/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1839, \"height\": 1123, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38926/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1848, \"height\": 651, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38926/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 661, \"height\": 417, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38926/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 884, \"height\": 565, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38926/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 384, \"height\": 459, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38926/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 344, \"height\": 451, \"label\": \"Table\"}]"
motivation: 现有模仿学习模型在动作保真度和数据可扩展性之间存在矛盾，且潜在空间与物理现实脱节导致计划不可靠。
method: 提出LatentVLA框架，学习连续的视觉-语言-行动潜在表示，避免时间纠缠和离散化伪影。
result: 在多种双手操作任务上表现优于基线，验证了潜在空间设计的有效性。
conclusion: 证明了通过合适的潜在空间设计可以兼顾保真度和可扩展性，推动通用机器人操作发展。
---

## Abstract
Current paradigms for robotic imitation learning face a stark trade-off between the motion fidelity of diffusion models and the data scalability of inverse dynamics models. The latter, while scalable, often learns a latent action space disconnected from physical reality. This flaw leads to critical failures: temporal entanglement, where the model cannot distinguish between visually similar states requiring distinct actions, e.g., a gripper approaching versus receding from an object. This ambiguity, compounded by discretization artifacts and sensitivity to task-irrelevant dynamics, renders robust planning infeasible. We introduce LatentVLA, a vision-language-action framework designed to overcome these limitations by learning a continuous and spatiotemporally grounded latent action representation. Its progressive three-stage architecture first employs a Temporal-Attentive Latent Action Model (TA-LAM) to resolve ambiguities using language-guided attention and explicit temporal encoding. Subsequently, a Latent Action Diffusion Transformer (LADT) performs planning via diffusion directly within this continuous latent space, preserving motion fidelity without tokenization. Finally, an expert policy head translates these latent plans into precise robot actions. Experiments show LatentVLA sets a new state-of-the-art across a suite of real-world bimanual tasks, outperforming prior methods and demonstrating superior zero-shot generalization and few-shot efficiency.

---

## 论文详细总结（自动生成）

# 1. 论文的核心问题与整体含义（研究动机和背景）

- 机器人模仿学习面临两类主流方法之间的根本性矛盾：**扩散模型**具有高动作保真度，但依赖大量精心标注的专家数据，可扩展性差；**逆动力学模型（IDM）**可以利用大量无标签视频，数据效率高，但所学到的潜在动作空间与物理现实脱节，导致多种严重失效模式。
- 具体失效模式包括：
  - **时间纠缠（Temporal Entanglement）**：模型无法区分视觉相似但动作要求截然不同的状态（例如夹爪靠近物体与远离物体），导致状态‑动作映射病态。
  - **离散化伪影（Discretization Artifacts）**：使用 VQ‑VAE 等离散化方法使表示丧失连续性，产生不连贯的物理轨迹。
  - **对任务无关动态的敏感性（Task‑irrelevant Dynamics）**：光照、背景等无关视觉变化污染潜在空间，误导策略。
- 本文提出 **LatentVLA**，旨在通过学习**连续且具有时空锚定性的潜在动作表示**，同时解决保真度与可扩展性的权衡，实现通用、鲁棒的长时域双手操作。

# 2. 论文提出的方法论

## 2.1 核心思想

- 解耦**表示学习**与**规划**：首先从异构数据（含标签与无标签）中学习一个鲁棒的、连续的潜在动作空间，随后在该高质量空间内进行规划，避免直接对离散 token 或原始动作建模的缺陷。
- 采用渐进式三阶段流水线：**TA‑LAM** 用于构建语义丰富且时间解耦的潜在空间；**LADT** 在该连续空间内进行扩散规划；**专家策略头部**（Expert Policy Head）将潜在计划映射为精确的机器人动作。

## 2.2 关键技术细节

### 阶段1：时间注意力潜在动作模型（TA‑LAM）

- **注意力驱动的逆动力学模型（IDM）**：融合两个机制
  - **语言引导的空间注意力**：利用冻结的 SigLIP 模型，将语言指令与多视图图像特征通过点积相似度计算注意力掩码，聚焦任务相关视觉元素，过滤环境干扰。
  - **时间解缠**：将历史（h=4）空间特征、语言嵌入、本体感受、**绝对时间编码**（指示任务阶段）拼接，并加入相对位置编码，由 Transformer 编码器输出潜在动作 \(Z_t \in \mathbb{R}^{512}\)。
- **潜在前向动力学模型（FDM）**：通过预测下一帧观测 \(\hat{O}_{t+1}\) 确保 \(Z_t\) 包含足够信息，实现无标签视频的无监督学习。
- **动作解码器**：轻量 MLP 将 \(Z_t\) 映射为连续机器人动作 \(\hat{a}_t \in \mathbb{R}^{14}\)，仅在有标签数据上训练。
- **联合优化目标**：重建损失（所有数据） + 动作损失（有标签数据），通过权重 \(\lambda_\text{act}\) 平衡。

### 阶段2：潜在动作扩散Transformer（LADT）

- 冻结 TA‑LAM 的 IDM，用其对有标签子集编码得到连续潜在动作序列。
- 训练一个扩散模型，以历史观测、历史潜在动作、本体感受和语言指令为条件，生成未来 H=16 步的潜在动作序列。
- 直接在连续空间扩散，避免离散化伪影；采用标准的噪声预测损失。
- 通过交替注入视觉与语言特征，确保语言指令鲁棒引导规划。

### 阶段3：真实世界微调

- 冻结整个 TA‑LAM（IDM + 动作解码器），仅更新 LADT 规划器。
- 在 1600 小时新演示数据上，最小化解码动作序列与真实动作之间的 MSE，实现高效任务适配。

## 2.3 公式/算法流程（文字说明）

- 空间注意力：\(\mathbf{A}_t^{(v)} = \text{softmax}\left( E_\text{img}(I_t^{(v)}) \cdot E_\text{text}(\ell)^T / \sqrt{d_\text{feat}} \right)\)，然后加权视觉特征 \(f_t^\text{visual} = \text{Concat}_v \left[ E_\text{vis}\big( I_t^{(v)} \odot \text{Upsample}(\mathbf{A}_t^{(v)}) \big) \right]\)。
- 时间上下文：\(C_{t-k} = \text{Concat}( f_{t-k}^\text{visual}, E_\ell(\ell), s_{t-k}, \gamma(t-k) ) + \text{PE}(k)\)，经 \(T_\text{enc}\) 输出 \(Z_t\)。
- 重建损失：\(\mathcal{L}_\text{recon} = \| \hat{O}_{t+1} - O_{t+1} \|_2^2\)。
- 动作损失：\(\mathcal{L}_\text{action} = \| \hat{a}_t - a_t \|_2^2\)。
- 扩散损失：\(\mathcal{L}_\text{LADT} = \mathbb{E}_{k,\epsilon,c_t} \left[ \| \epsilon - \epsilon_\theta(Z_\text{noisy}, k, c_t) \|_2^2 \right]\)。
- 微调：\(\mathcal{L}_\text{finetune} = \mathbb{E}\left[ \| D_\text{act}^\text{frozen}(\text{LADT}_\theta(c_t)) - A_\text{gt} \|_2^2 \right]\)。

# 3. 实验设计

## 3.1 数据集

- **预训练数据集 \(D_\text{pretrain}\)**：超过 250 万序列，来自 52 个来源，包括：
  - 无标签人类视频
  - 带标签的多本体机器人轨迹（RDT‑1B 语料库）
  - 仿真数据
  - 自行收集的大规模真实世界演示：AgiBot World Beta 和 LatentVLA‑Dexterous（约 50 万序列）。
- **微调数据集 \(D_\text{finetune}\)**：1600 小时新演示，涵盖 8 个具体双手任务，仅用于目标平台适配。

## 3.2 场景与Benchmark

- **真实世界**：8 个挑战性双手任务（如折毛巾、叠布等）以及针对性的分布外（OOD）探测（光照、背景、新物体干扰）。
- **仿真基准**：
  - **RoboTwin 1.0**：复杂双手协调（8 个子任务）。
  - **SIMPLER**：长时域操作（成功率）。
  - **CALVIN**（ABC→D 设置）：组合泛化（平均任务长度）。

## 3.3 对比方法

- 主要对比了 **RDT‑1B**（扩散基础模型）和 **LAPA**（离散潜在动作方法），均从零重新训练以保证公平。
- 在仿真中另对比了 DP、DP3、Octo、OpenVLA、RT‑2、Moto、RoboFlamingo、GR‑1 等。

# 4. 资源与算力

- 预训练阶段（Stage 1 & 2）使用 **112 块 NVIDIA A100‑80G GPU**，耗时约 **一个月**。
- 微调阶段（Stage 3）在 1 块 A100 GPU 上不到 **1 小时**（20 次示范条件下）。
- 论文明确报告了上述算力信息。

# 5. 实验数量与充分性

- 实验覆盖**多种任务维度**：
  - 真实世界 8 个双手任务（图4：成功率柱状图）；
  - 仿真三个基准（RoboTwin 1.0、SIMPLER、CALVIN），每个含多个子任务或指标（表1）；
  - 零样本泛化测试（光照、背景、动态干扰）；
  - 少样本适配（20 次演示）；
  - 数据规模对比（在原始 1.3M 数据集上重新训练）；
  - 消融实验（表2：5 种变体，加基线对比）。
- **充分性评价**：实验设计较为全面，涵盖了性能、泛化、效率、消融等多个方面，对比方法均在同一条件下重新训练，消融有定量结果，结论有数据支撑。但真实世界任务局限于 8 个，且未提供方差或统计显著性检验，实验可复现性信息有限。
- **客观性与公平性**：明确说明所有基线均重新训练，采用相同的训练数据；消融控制变量合理。但未提及随机种子或多次重复实验的误差条。

# 6. 论文的主要结论与发现

- **高性能**：在三个仿真基准上达到 SOTA；在真实世界双手任务中平均成功率 63.8%，比 RDT‑1B 高 12.8%，比 LAPA 高 48.5%。
- **零样本泛化**：在多项干扰下（光照变化等）仍保持 56% 成功率，优于基线。
- **少样本高效性**：仅用 20 次演示即可在新任务上达到 61% 成功率，比 RDT‑1B 高 27%。
- **架构有效性**：消融显示连续扩散规划与绝对时间编码是关键，语言注意力与联合训练同样重要，所有组件相互配合。
- 证实了解耦表示学习与规划、使用连续潜在空间兼顾保真度与可扩展性的可行性。

# 7. 优点

- **思路创新**：首次系统性解决现有潜在动作方法的时间纠缠、离散化伪影、任务无关动态三大失败模式。
- **架构设计**：三阶段流水线（TA‑LAM + LADT + 微调）逻辑清晰，各阶段目标明确，能够充分利用大规模无标签与有标签数据。
- **技术亮点**：
  - 语言引导的空间注意力与绝对时间编码相结合，实现时空解耦。
  - 在连续潜在空间进行扩散规划，避免了离散化的信息损失。
  - 微调时冻结表示层，仅更新规划器，实现高效迁移。
- **实验验证充分**：涵盖真机、仿真、泛化、少样本、消融等多方面，对比基准最新且重新训练，结果有说服力。
- **开源数据贡献**：大规模预训练数据集（>250 万）与长时间双手操作演示数据（1600 小时）公开，推动社区研究。

# 8. 不足与局限

- **剩余失误模式**：对物体完全遮挡和反射表面造成的视觉模糊仍敏感，说明表示学习在极端情况下的鲁棒性不足。
- **真实世界任务数量有限**：8 个任务虽具代表性，但可能未能覆盖所有复杂场景（如高动态碰撞、稠密接触等）。
- **计算资源需求大**：预训练需要 112 块 A100 跑一个月，成本极高，对一般研究组不易复现。
- **实验报告细节不足**：未提供成功率的标准差或置信区间，未说明重复次数，降低了统计可靠性。
- **消融实验仅涉及单一任务（折毛巾）**：结论的泛化性可能受任务特性影响，若能跨任务验证会更稳健。
- **微调阶段依赖大量目标平台数据（1600 小时，尽管是混合）**：对于全新机器人平台仍需可观数据，并非完全零样本。
- **未探讨潜在动作维度（512）的敏感性**、扩散步数等超参数影响。
- **伦理与安全**：论文未讨论部署时的安全风险或失败后果。

（完）
