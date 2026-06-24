---
title: "Balancing Signal and Variance: Adaptive Offline RL Post-Training for VLA Flow Models"
title_zh: 信号与方差平衡：面向VLA流模型的自适应离线强化学习后训练
authors: "Hongyin Zhang, Shiyuan Zhang, Junxi Jin, Qixin Zeng, Yifan Qiao, Hongchao Lu, Donglin Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38944/42906"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操纵的VLA流模型离线强化学习后训练
tldr: 基于流匹配的视觉-语言-动作模型在通用机器人操纵中表现出色，但在复杂下游任务中动作精度不足，原因是仅依赖模仿学习后训练。本文理论上提出面向VLA流模型的离线RL目标，并推导出高效可行的自适应强化流匹配算法ARFM。通过引入自适应调整机制，ARFM能感知数据质量分布，显著提升VLA模型在复杂任务上的动作准确性与泛化能力。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38944/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38944/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 878, \"height\": 464, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38944/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 879, \"height\": 730, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38944/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 738, \"height\": 675, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38944/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 836, \"height\": 728, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38944/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38944/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38944/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1856, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38944/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1829, \"height\": 330, \"label\": \"Table\"}]"
motivation: VLA流模型仅依赖模仿学习后训练，无法理解数据质量分布，导致复杂任务动作精度不高。
method: 提出ARFM算法，基于理论推导的离线强化学习目标，引入自适应调整以感知数据质量分布，优化VLA流模型。
result: 在复杂下游操纵任务上，ARFM显著提升了VLA模型的动作精度和泛化性能。
conclusion: 离线RL后训练能有效弥补模仿学习的不足，为VLA模型在复杂任务中的应用提供新范式。
---

## Abstract
Vision-Language-Action (VLA) models based on flow matching have shown excellent performance in general-purpose robotic manipulation tasks. However, the action accuracy of these models on complex downstream tasks is unsatisfactory. One important reason is that these models rely solely on the post-training paradigm of imitation learning, which makes it difficult to have a deeper understanding of the distribution properties of data quality, which is exactly what Reinforcement Learning (RL) excels at. In this paper, we theoretically propose an offline RL post-training objective for VLA flow models and induce an efficient and feasible offline RL fine-tuning algorithm −− Adaptive Reinforced Flow Matching (ARFM). By introducing an adaptively adjusted scaling factor in the VLA flow model loss, we construct a principled bias-variance trade-off objective function to optimally control the impact of RL signal on flow loss. ARFM adaptively balances RL advantage preservation and flow loss gradient variance control, resulting in a more stable and efficient fine-tuning process. Extensive simulation and real-world experimental results show that ARFM exhibits excellent generalization, robustness, few-shot learning, and continuous learning performance.

---

## 论文详细总结（自动生成）

# 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **背景**：基于流匹配（Flow Matching）的视觉‑语言‑动作（VLA）模型（如 π0）在通用机器人操纵任务上表现优异，但在复杂下游任务中动作精度不足。
- **问题根源**：现有 VLA 模型仅依赖模仿学习（行为克隆或流匹配）进行后训练，无法深入感知训练数据的质量分布特性，而强化学习（RL）擅长利用数据质量信息。
- **现有方法的不足**：已有的离线 RL 后训练方法（如 ReinboT）在 VLA 流模型上效果有限，原因是流模型通过向量场建模整个动作轨迹分布，最大化的回报只能间接且低效地引导动作预测。
- **研究目标**：提出一种面向 VLA 流模型的自适应离线 RL 后训练算法——**自适应强化流匹配（ARFM）**，通过自适应调控 RL 信号强度，在保留高优势样本信号的同时控制梯度方差，实现稳定且高效的微调。

## 2. 方法论：核心思想、关键技术细节、算法流程

- **核心思想**：在 VLA 流模型的损失函数中引入一个动态调整的缩放因子 α，构建一个偏差‑方差权衡的优化目标，使损失加权能根据当前 batch 的数据质量分布自适应变化，获得 RL 信号强度与梯度方差控制之间的平衡。

- **关键技术细节**：
  - **能量加权 VLA 流模型**：定义能量加权策略分布  
    \(\pi(A_t|o_t) \propto p(A_t|o_t)\exp(\alpha R^*(A_t,o_t))\)，其中 \(R^*\) 为标准化的 Leave‑One‑Out RL 优势估计。使用条件能量加权流匹配损失（CEFM）进行训练。
  - **实际损失函数**：对每个 batch 计算带 softmax 能量权重的加权 FM 损失：  
    \(L(\theta) = \sum_i w_i(\alpha) \|v_\theta(\{A_i^t\}_\tau, o_t) - u(\{A_i^t\}_\tau|A_i^t)\|^2\)，  
    其中 \(w_i(\alpha) = \exp(\alpha R^*(A_i^t,o_t)) / \sum_j \exp(\alpha R^*(A_j^t,o_t))\)。
  - **自适应 α 的优化目标**：构建目标函数  
    \(J(\alpha) = \text{Var}(\hat{g}(\alpha)) - \lambda S(\alpha)\)，  
    其中 \(\hat{g}(\alpha)\) 为加权梯度，\(S(\alpha)\) 为加权平均 RL 优势。最小化 \(J(\alpha)\) 同时追求低梯度方差和高 RL 信号。
  - **可解近似**：假设标准化优势 \(R^*\) 和流匹配损失均服从高斯分布，推导出 α 的解析优化目标（Corollary 1）和非线性方程（Corollary 2），并用二分法迭代求解（Algorithm 1）。
  - **算法流程（Algorithm 2）**：
    1. 对每个 batch：
       - 采样噪声，计算噪声动作、RL 优势 \(R_i\)、原始 FM 损失 \(L_i^{\text{FM}}\)；
       - 通过 Algorithm 1 根据当前 batch 计算最优 \(\alpha^*\)；
       - 计算能量权重 \(w_i(\alpha^*)\)；
       - 计算加权损失 \(L(\theta) = \sum_i w_i(\alpha^*) L_i^{\text{FM}}\)；
       - 梯度更新模型参数。

## 3. 实验设计：数据集 / 场景、benchmark、对比方法

- **模拟环境**：**LIBERO** 基准，包含 4 个任务套件（Object、Long、Spatial、Goal），每套 10 个语言引导的机器人操纵任务，用于评估多任务学习、动作扰动鲁棒性、少样本学习和持续学习。
- **真实世界**：**UR5** 机械臂平台，设计 3 种不同的抓取放置任务，并在任务中引入外部扰动（如物体移动）。
- **对比方法**：
  - **非流匹配模型**：Octo、OpenVLA、Dita、Diffusion Policy、MDT、QueST。
  - **流匹配模型**：π0（基线）、ReinboT（基于 π0 的流模型版）、RWR（Reward‑Weighted Regression，流模型版）、ARFM（所提方法）。

## 4. 资源与算力

- 文中 **未明确说明** 所使用的 GPU 型号、数量、训练时长等算力信息。仅可推断实验是在标准深度学习集群上完成（如使用 NVIDIA 系列 GPU），但具体细节缺失，可能影响实验可重复性。

## 5. 实验数量与充分性

- **实验种类**：
  - 多任务学习（4 套件，每套 10 任务，报告平均成功率）。
  - 动作扰动（4 套件，5 种噪声等级 0.1‑0.3，报告平均成功率）。
  - 少样本学习（LIBERO‑Long 上 30‑shot、20‑shot、10‑shot，组合 3 种噪声等级）。
  - 持续学习（3 种训练序列，报告 NBT 和平均成功率）。
  - 消融实验（在 LIBERO‑Goal 上改变 λ 和二分迭代次数 M，分析敏感性）。
  - 真实世界实验（3 类任务，对比 π0、ReinboT、RWR、ARFM，含外部扰动）。
- **数量与充分性**：
  - 实验覆盖全面（多任务、鲁棒性、数据效率、持续学习、真实场景），对比基线多样。
  - 但未提供多次独立重复实验的标准差或置信区间，且每个实验仅报告平均成功率，统计稳健性略显不足。
  - 总体上实验设计较为充分，但仍缺乏对超参数尤其是 α 更新机制鲁棒性的深入分析。

## 6. 主要结论与发现

- **多任务学习**：ARFM 在 LIBERO 上平均成功率 **92.1%**，比 π0 高 4.5%，优于 ReinboT（91.2%）和 RWR（90.8%）。
- **动作扰动鲁棒性**：ARFM 平均成功率 48.2%，比 π0 高 **11.4%**，显著优于其他流匹配方法。
- **少样本学习**：ARFM 在 LIBERO‑Long 上平均成功率 36.5%，比 π0 高 12.2%，证明其数据利用效率更高。
- **持续学习**：ARFM 获得最高平均成功率（61.0%）和最低负后向迁移（NBT=4.7），比 π0 的 NBT（7.5）降低 **38.0%**，有效缓解灾难性遗忘。
- **消融**：ARFM 对超参数 λ 不敏感，二分迭代在 10 步后性能稳定。
- **真实世界**：ARFM 在扰动任务下成功率最高，证明其在实际复杂场景中更鲁棒。

## 7. 优点（方法与实验设计亮点）

- **方法论创新**：
  - 首次将能量加权流匹配与自适应缩放因子相结合，用于 VLA 流模型的离线 RL 后训练，既有理论推导又有实用算法。
  - 构建了可求解的方差‑信号权衡优化目标，并提出二分迭代实时更新 α，确保自适应能力。
- **实验设计亮点**：
  - 评估维度全面：涵盖多任务、鲁棒性、数据效率、持续学习和真实世界，验证了方法的通用性。
  - 对比基线覆盖多种近期 SOTA 模型（非流匹配和流匹配），比较公平。
  - 持续学习实验使用 NBT 指标，能有效衡量遗忘程度。
  - 真实世界引入外部扰动增加了评估难度，更具实际意义。

## 8. 不足与局限

- **实验统计**：未提供多次重复的标准差或置信区间，结论的统计显著性不够明确。
- **算力信息缺失**：未说明 GPU 型号、数量、训练时长，影响可重复性。
- **假设依赖**：推导中假设优势值和流匹配损失服从高斯分布，在复杂真实分布下可能不完全成立。
- **泛化范围有限**：仅在一个模拟基准（LIBERO）和一个真实平台（UR5）上验证，且任务类型相对单一（操纵），尚未测试到更多机器人系统或任务场景。
- **仅离线设置**：未探索在线 RL 后训练，而在线方法可能在交互中进一步优化。
- **奖励设计**：依赖稠密奖励和 RTG 设计，在某些任务中可能不易获得。
- **超参数 λ**：虽不敏感但仍需设置，缺乏自动调优机制。

（完）
