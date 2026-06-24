---
title: "DiTEA: Mixture-of-Experts for Vision-Language-Action Model in Robotic Manipulation"
title_zh: DiTEA：机器人操作中视觉-语言-动作模型的混合专家方法
authors: "Chengxuan Li, Xingwan Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38902/42864"
tags: ["query:rob-il"]
score: 10.0
evidence: 基于混合专家模型的视觉-语言-动作模型用于机器人操作
tldr: 基于扩散的VLA模型存在指令跟随能力差和技能遗忘问题。该论文提出DiTEA，在动作头中引入混合专家模块（Action MoE），并通过任务指令约束缓解权重冲突。实验表明该方法在多任务设置下有效提升了指令遵循度并保持旧任务性能。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38902/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1831, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38902/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 883, \"height\": 826, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38902/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38902/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38902/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1855, \"height\": 591, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38902/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1735, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38902/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1735, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38902/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 898, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38902/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 884, \"height\": 395, \"label\": \"Table\"}]"
motivation: 现有扩散VLA模型多任务微调时易出现技能遗忘和指令跟随不佳。
method: 提出DiTEA，在动作头中使用混合专家模块，并设计任务指令约束保持权重稳定性。
result: 在多个操作任务上实现了更好的指令跟随和抗遗忘能力。
conclusion: 混合专家结构可有效缓解多任务学习中的冲突，提升VLA模型的通用性。
---

## Abstract
The current diffusion-based Vision-Language-Action (VLA) models have faster inference speed and the ability to solve the action muti-modality problem in robot manipulation tasks compared to traditional autoregressive models after large-scale pre-training and post-training. However, the diffusion-based VLA models were found to have poor instruction-following ability, and after fine-tuning training on multiple tasks, them often suffer from "skill forgetting" due to conflicting model weights on each task. To address this problem, we propose DiTEA, a Diffusion Transformer-based Mixture-of-Experts (MoE) VLA model. Specifically, it fuses the MoE module into the action head of VLA to form Action MoE, and in addition, we design the Task-Instruction Gate, which uses language instructions to select specific experts for tasks they specialize in, in order to improve the VLA's instruction-following ability. We conducted comprehensive experiments and ablation study to evaluate the efficacy of our model under different designs. Experimental results from simulation and real-world show that our DiTEA has excellent improvement in multi-task compared to baseline and other VLAs.

---

## 论文详细总结（自动生成）

# DiTEA 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机与背景）
- **核心问题**：当前的扩散式视觉-语言-动作（VLA）模型虽然在推理速度和多模态动作分布建模上优于自回归模型，但在多任务微调时出现两个主要缺陷：**指令跟随能力差**（poor instruction-following）以及**技能遗忘**（skill forgetting），后者源于不同任务对模型权重的冲突更新。
- **研究动机**：受大脑前额叶皮层动态门控机制以及皮层功能模块化组织的启发，作者认为混合专家（MoE）架构能够在多任务学习中隔离任务特定参数、缓解干扰，同时通过基于任务指令的动态路由提升指令执行精度。
- **整体含义**：本文提出 DiTEA——一个基于 Diffusion Transformer 的 MoE VLA 模型，旨在同时解决扩散 VLA 的多任务冲突和指令跟随瓶颈，实现更鲁棒、更通用的机器人操控策略。

## 2. 论文提出的方法论
### 2.1 核心思想
- 在 VLA 模型的 **动作解码头（action head）** 中引入 Mixture-of-Experts（MoE）结构，形成 **Action MoE** 模块。
- 设计一个 **Task-Instruction Gate**，它使用语言指令的表示作为门控输入，动态选择最适合当前任务的专家子网络。
- 引入**共享专家（shared expert）** 捕获任务间共性，并使用**负载均衡损失（load balancing loss）** 防止专家利用率失衡。

### 2.2 关键技术细节
- **模型总体架构**（约 7B 参数）：
  - **视觉模块**：DINOv2 + SigLIP 双编码器 → 合并特征 → 256 个视觉 token。
  - **语言模块**：LLAMA 2 7B 作为主干，融合视觉 token 与语言指令，输出一个认知特征（cognition feature）。
  - **动作模块（Action MoE）**：基于 DiT（Diffusion Transformer）将 MLP 层替换为 MoE 层，每个专家是一个 MLP，同时包含一个共享专家。
- **Task-Instruction Gate**：输入为指令 token 的表示 \( x_{\text{inst}} \)，通过线性变换 + softmax 得到专家权重：
  \[
  G(x_{\text{inst}}; \Theta) = \text{softmax}(W_g x_{\text{inst}} + b_g)
  \]
  最终输出为：
  \[
  F_{\text{MoE}}(x; \Theta, \{W_i\}) = \sum_{i=1}^{N} G(x_{\text{inst}}; \Theta)_i \cdot F_i(x; W_i)
  \]
- **共享专家**：在每个 MoE 层，共享专家始终被激活，提供通用知识，并与其他专家加权融合。
- **负载均衡损失**：鼓励各专家接收接近均匀的输入分布，以避免路由坍塌。公式为：
  \[
  L_{\text{balance}} = \beta \sum_{j=1}^{m} \left( \frac{m}{T} \sum_{t=1}^{T} I(t,j) \right) \cdot \left( \frac{1}{T} \sum_{t=1}^{T} P(t,j) \right)
  \]
- **训练目标**：最小化预测噪声与真实噪声的 MSE（扩散模型标准损失）。

## 3. 实验设计
### 3.1 使用的数据集与场景
- **仿真实验**：使用 **BridgeData V2** 数据集（60,096 条轨迹，24 个环境），基于 **SIMPLER** 框架的 **WidowX 机器人 Visual Matching** 设定。评估四个任务：Put spoon on towel, Put carrot on plate, Stack green block on yellow block, Put eggplant in yellow basket。
- **真实世界实验**：
  - 预训练：使用 **DROID** 数据集（76k 演示，564 个场景，86 个任务）。
  - 微调：使用 GELLO 遥操作收集的 **Franka Research 3 机器人** 数据，每个任务 60-100 条轨迹。
  - 评估三类任务（共 8 个子任务）：Pick and Place（玉米、土豆、卷心菜）、Stack（方块、碗）、Open and Close（抽屉、箱子）。

### 3.2 Benchmark
- 仿真：SIMPLER 标准协议，以成功率作为指标。
- 真实：自建任务集，包含多任务、泛化（未见过的颜色、形状、类别）、指令跟随三个维度。

### 3.3 对比方法
- **仿真**：RoboVLMs、Octo-Small、OpenVLA、CogACT。
- **真实**：OpenVLA、CogACT。
- **消融实验**：基线（Ex 0）与逐步添加负载均衡损失、Task-Instruction Gate、共享专家、参数匹配对照。

## 4. 资源与算力
- 使用 **8 张 NVIDIA A100 GPU**。
- 框架：PyTorch Fully Shared Data Parallel（FSDP）。
- 超参数：
  - 批大小：256
  - 扩散步数：8
  - 学习率：2×10⁻⁵（常数）
  - 仿真微调：约 20K 训练步
  - 真实实验：先 DROID 全参数预训练，再冻结 VLM 只训练 DiT 进行微调（具体步数未明确说明，但基于数据量推算合理）
- **未明确说明训练总时间或能耗**。

## 5. 实验数量与充分性
### 实验数量
- **仿真主实验**：表1，4 个任务 × 5 种方法。
- **真实主实验**：表2，8 个子任务 × 3 种方法。
- **泛化实验**：表3，3 种泛化类型（颜色、形状、类别）× 3 种方法。
- **指令跟随实验**：图5，3 种任务难度 × 3 种方法（含中间步骤评分）。
- **消融实验**：表4，共 9 种配置（含参数匹配基线），覆盖三个组件的所有组合。
- 总计超过 30 组不同条件下的成功率对比。

### 充分性与公平性
- 仿真和实物双验证，覆盖多种机器人平台（WidowX、Franka）。
- 对比方法均为公开最强基线（OpenVLA、CogACT 等），超参数保持一致。
- 消融实验系统性地验证了每个模块的贡献。
- 额外引入参数匹配基线（Ex 3‑1）排除参数增加带来的混淆。
- **结论**：实验设计充分、客观、公平，能够有力支撑核心观点。

## 6. 论文的主要结论与发现
- DiTEA 在仿真多任务上的平均成功率达到 **40.8%**，高于所有对比方法（CogACT 35.2%，OpenVLA 1.0%）。
- 在真实世界 8 个任务中，DiTEA 平均成功率为 **40.2%**，显著优于 CogACT（34.0%）和 OpenVLA（6.2%）。
- 泛化实验中，DiTEA 在未见颜色（53.5%）、形状（71.3%）、类别（15.0%）上均优于对比方法。
- 指令跟随能力：**优于扩散模型 CogACT，但仍逊于自回归模型 OpenVLA**（说明指令跟随仍是开放问题但已获改进）。
- 消融实验表明，Task-Instruction Gate、共享专家、负载均衡损失三组件同时使用可使成功率从 40.2% 提升至 51.5%（+11.3%），且性能增益源于 MoE 架构而非单纯参数增长。
- **核心发现**：在动作头中融入 MoE 结构并利用语言指令路由专家，是缓解多任务技能干扰、提升指令跟随的有效方法。

## 7. 优点
- **方法创新性**：首次将 MoE 深度集成到扩散 VLA 的动作解码阶段，并提出指令感知的门控机制。
- **生物学启发**：从前额叶皮层动态门控获得设计灵感，增强了可解释性和合理性。
- **架构设计**：共享专家 + 负载均衡损失考虑周全，兼顾任务特异性和共性，并通过辅助损失防止路由崩溃。
- **实验全面**：覆盖仿真、实物、泛化和指令跟随，并设置了参数匹配对照，消融实验完备。
- **开源性趋势**：论文提及使用公开数据集和开源代码（OpenVLA、DROID 等），便于复现与后续研究。

## 8. 不足与局限
- **计算资源需求高**：8×A100 GPU 训练成本大，限制了更大规模预训练，零样本泛化能力不足，仍需任务特定微调。
- **指令跟随仍有差距**：与自回归模型 OpenVLA 相比仍有明显不足（图5），说明扩散架构在语言条件化上仍有改进空间。
- **实验覆盖范围有限**：仅测试单一机器人平台（Franka）和有限任务数（8 个真实任务），缺乏多机器人、多场景的广泛验证。
- **未见高难度任务**：如长时间序列任务、碰撞避免等复杂操控未涉及。
- **潜在偏差风险**：真实世界数据由作者自行采集，虽然采用标准遥操作框架，但与公开数据集分布可能存在差异。
- **部分超参数未充分讨论**：如专家数量、门控网络结构、负载均衡系数 β 的选择未做深入分析。
- **未与最新 MoE VLA 模型（如 MoRE、DriveMoE）直接对比**，仅在论文提及但实验未纳入。

（完）
