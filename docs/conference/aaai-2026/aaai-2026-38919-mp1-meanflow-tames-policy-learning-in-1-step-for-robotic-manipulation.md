---
title: "MP1: MeanFlow Tames Policy Learning in 1-step for Robotic Manipulation"
title_zh: MP1：MeanFlow在机器人操作中实现一步策略学习
authors: "Juyi Sheng, Ziyi Wang, Peiming Li, Mengyuan Liu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38919/42881"
tags: ["query:rob-il"]
score: 8.0
evidence: 提出从3D点云一步生成机器人操作动作轨迹的方法
tldr: 针对扩散模型迭代慢与流模型架构约束的问题，MP1采用MeanFlow范式直接从3D点云输入在一步网络评估中生成动作轨迹，无需额外一致性约束，消除了ODE求解误差，在机器人操作任务上提升了轨迹精度和效率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 755, \"height\": 772, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1710, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1832, \"height\": 545, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 738, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 661, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38919/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 789, \"height\": 565, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38919/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1830, \"height\": 352, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38919/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1834, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38919/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1836, \"height\": 223, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38919/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 884, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38919/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 881, \"height\": 175, \"label\": \"Table\"}]"
motivation: 现有生成式模型在机器人操作中面临扩散模型采样慢和流模型架构约束的权衡问题。
method: 提出MP1，结合3D点云输入与MeanFlow范式，直接学习区间平均速度，一步生成动作轨迹。
result: 在模拟和真实机器人操作任务上，MP1比扩散模型更快更精确。
conclusion: MP1为机器人操作提供了一种高效、精确的生成式策略学习方法。
---

## Abstract
In robot manipulation, robot learning has become a prevailing approach. However, generative models within this field face a fundamental trade-off between the slow, iterative sampling of diffusion models and the architectural constraints of faster Flow-based methods, which often rely on explicit consistency losses. To address these limitations, we introduce MP1, which pairs 3D point-cloud inputs with the MeanFlow paradigm to generate action trajectories in one network function evaluation (1-NFE). By directly learning the interval-averaged velocity via the "MeanFlow Identity", our policy avoids any additional consistency constraints. This formulation eliminates numerical ODE-solver errors during inference, yielding more precise trajectories. MP1 further incorporates CFG for improved trajectory controllability while retaining 1-NFE inference without reintroducing structural constraints. Because subtle scene-context variations are critical for robot learning, especially in few-shot learning, we introduce a lightweight Dispersive Loss that repels state embeddings during training, boosting generalization without slowing inference. We validate our method on the Adroit and Meta-World benchmarks, as well as in real-world scenarios. Experimental results show MP1 achieves superior average task success rates, outperforming DP3 by 10.2% and FlowPolicy by 7.3%. Its average inference time is only 6.8 ms—19 times faster than DP3 and nearly 2 times faster than FlowPolicy.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 机器人操作任务中，生成式策略学习（如行为克隆）已成为主流方法，但面临根本性权衡：
  - **扩散模型**：能有效处理多模态动作分布，生成质量高，但需要多步迭代采样（通常10步以上），推理延迟高，难以满足实时控制需求。
  - **流匹配模型**（Flow-based）：采样步数少，推理快，但需附加一致性损失（consistency loss）或架构约束，导致实现复杂且可能引入误差。
- 现有方法如DP3（扩散+3D点云）和FlowPolicy（流匹配+一致性）虽各有优势，却未能同时实现 **超快推理（一步采样）** 与 **高成功率**。
- **MP1目标**：在机器人操作中实现 **真正的1步采样（1-NFE）**，不依赖显式一致性损失或ODE数值求解器，同时保持对场景细节的高区分能力和少样本泛化能力。

## 2. 方法论
### 核心思想
- 将 **MeanFlow** 范式从图像生成引入机器人学习。MeanFlow通过 **“MeanFlow Identity”** 使模型直接学习 **区间平均速度场**，避免传统流匹配中需求解瞬时速度的积分过程，从而在单次前向传播中完成从噪声到动作轨迹的生成。

### 关键技术细节
- **输入处理**：3D点云 P 经3D投影及视觉编码器得到视觉特征 fv；机器人状态 S 经状态编码器得到状态特征 fs；两者拼接为条件向量 c。
- **平均速度场学习**：
  - 定义平均速度 \( u(z_t, r, t) = \frac{1}{t-r} \int_r^t v(z_\tau,\tau) d\tau \)。
  - 通过“MeanFlow Identity”（局部微分方程）训练网络 uθ 预测该平均速度：
    \[
    u(z_t, r, t) = v(z_t, t) - (t-r)\frac{d}{dt}u(z_t, r, t)
    \]
  - 回归损失 \( L(\theta) = \mathbb{E} \| u_\theta(z_t, r, t | c) - \text{sg}(u_{\text{tgt}}) \|^2 \)，其中 target 由已知瞬时速度与网络自身估计组合得到（含 stop-gradient 保持稳定）。
- **Classifier-Free Guidance (CFG)**：引入引导速度 \( \tilde{v}_t = \omega v_t(\cdot|c) + (1-\omega)u_\theta(\cdot|\emptyset) \)，修改损失函数为 \( L_{\text{cfg}}(\theta) \)，使模型在保持1-NFE的同时提升轨迹可控性。
- **Dispersive Loss（分散性损失）**：
  - 针对回归目标对潜在特征的间接监督导致“特征坍塌”——不同环境的输入被映射到相似潜在空间，损害少样本泛化。
  - 定义基于 InfoNCE 的损失：
    \[
    L_{\text{disp}}(\theta) = \log \mathbb{E}_{i,j \in B} \left[ \exp\left( -\frac{\|z_{A,i} - z_{A,j}\|_2^2}{\tau} \right) \right]
    \]
    其中 zA 为UNet中间层特征，τ=1，负对数形式使不同样本的特征相互排斥。
  - 该损失 **仅在训练时计算**，推理时无额外开销。
- **总体损失**：\( L_{\text{total}} = L_{\text{cfg}} + \lambda L_{\text{disp}} \)，λ=0.5。
- **推理过程**：给定噪声 A1 ~ N(0,I) 和条件 c，一步生成完整 K 步动作轨迹：
  \[
  A_0 = A_1 - u_\theta^{\text{cfg}}(A_1, 0, 1 | c)
  \]

## 3. 实验设计
### 数据集/场景
- **模拟基准**：
  - **Adroit**：3 个高难度任务（Hammer、Door、Pen）。
  - **Meta-World**：34 个任务，按难度分为 Easy（21）、Medium（4）、Hard（4）、Very Hard（5）。
- **真实世界**：
  - 使用 ARX R5 双臂机器人，RealSense L515 深度相机；5 个操作任务（Hammer、Drawer Close、Heat Water、Stack Block、Spoon）。
- **训练数据**：每个任务提供 **10 个专家演示**（模拟）；真实任务使用 **20 个人类演示**。

### 对比方法
- **2D 输入方法**：DP（2023）、AdaFlow（2024）、CP（2024）。
- **3D 输入方法**：DP3（2024）、Simple DP3（2024）、FlowPolicy（2025）。
- 扩散类方法（DP3等）使用 10-NFE；流类方法（CP、FlowPolicy）使用 1-NFE；AdaFlow 使用可变 NFE。

## 4. 资源与算力
- **硬件**：单张 NVIDIA RTX 4090 GPU。
- **训练配置**：
  - 批量大小 128，优化器 AdamW，学习率 0.0001。
  - 观测窗口 2 步，历史状态长度 4，预测水平 4 步。
  - MeanFlow ratio = 0.5，CFG scale = 2.0。
  - Adroit 任务训练 **3000 epochs**，Meta-World 任务训练 **1000 epochs**，每 200 epochs 评估一次。
- **推理速度**：平均 6.8ms / 步（含编码器）。
- 论文 **未明确给出** 总训练时长（小时数），但可从 epochs 与 batch size 大致推断。

## 5. 实验数量与充分性
- **模拟实验**：
  - 37 个任务 × 3 个随机种子，每个种子取 5 个最高成功率平均，计算总体均值与标准差。
  - 对比包括成功率（表1）和推理时间（表2）。
  - **消融实验**：
    - Dispersive Loss 影响（表3）：移除后平均成功率下降 4~5%。
    - MeanFlow Ratio 影响（表4）：0.5 附近最优，极值 (1.0) 性能骤降。
    - 演示数量影响（图5）：随演示数增加成功率提升，MP1 在少样本（0/2/5）下显著优于 FlowPolicy。
  - **训练曲线对比**（图4）：MP1 收敛更快、方差更低。
- **真实实验**：5 个任务，各方法比较成功率和完成时间（表5）。
- **充分性评价**：
  - 任务覆盖广泛（模拟+真实），难度分级合理。
  - 对比基准均为近年 SOTA，公平性有保证（相同种子、相同环境配置）。
  - 消融实验多维，揭示了各组件贡献。
  - **不足**：未与更多对比学习方法（如 SimCLR、Triplet loss）比较；未在多视角或动态光照下测试泛化性。

## 6. 主要结论与发现
- MP1 在所有 37 个模拟任务上的 **平均成功率** 达 **78.9%±2.1%**，比 DP3 高 **10.2%**，比 FlowPolicy 高 **7.3%**。
- **推理时间仅 6.8ms**，是 FlowPolicy 的近 **2 倍**、DP3 的 **19 倍**；且标准差小（±0.1ms），稳定性强。
- 在 **真实机器人** 上，MP1 平均成功率 90%（FlowPolicy 70%，DP3 70%），完成时间最短（20.1s vs 25.1s / 30.7s）。
- **Dispersive Loss** 一致提升目标，尤其在复杂/少样本任务中表现明显。
- MP1 的 1-NFE 避免了 ODE 求解误差，轨迹更加平滑准确。
- 证实 MeanFlow 范式可有效迁移至机器人策略学习，解决扩散/流匹配的长期痛点。

## 7. 优点
- **真正的一步采样（1-NFE）**：推理极快（6.8ms），适合实时控制。
- **无额外一致性约束**：利用 MeanFlow Identity 直接学习平均速度，无需 ODE 积分器，实现简单且数值稳定。
- **Dispersive Loss 设计巧妙**：仅训练时生效，不增加推理负担，有效提升特征判别力与少样本泛化。
- **联合 CFG**：在保持 1-NFE 的前提下提升轨迹可控性。
- **实验严谨**：多种难度任务、多随机种子、多维度评估（成功率+速度+消融），代码开源利于复现。
- **真实场景验证**：在现有硬件上达到 SOTA，证明可迁移性。

## 8. 不足与局限
- **输入模态单一**：仅使用点云+机器人状态，未探索 RGB 图像、语言指令等；点云依赖深度传感器，适用场景受限。
- **观测视角固定**：实验相机位置固定，未测试多视角或动态移动下的鲁棒性。
- **真实任务数量有限**：仅 5 个，且均为单一双臂设置，硬件通用性未验证。
- **零样本能力未评估**：训练需至少几个演示（实验最少 0 个演示时成功率很低），论文未做严格零样本测试。
- **Flow Ratio 极值时性能下降（1.0）**：未深入分析原因，仅作现象描述。
- **消融不全面**：未与其他正则化方法（如对比学习、信息瓶颈）比较；Dispersive Loss 的超参数 τ 未调优分析；λ 固定为 0.5，缺少敏感性测试。
- **训练资源表述不详**：未提供总训练时间，潜在影响可复现性。

（完）
