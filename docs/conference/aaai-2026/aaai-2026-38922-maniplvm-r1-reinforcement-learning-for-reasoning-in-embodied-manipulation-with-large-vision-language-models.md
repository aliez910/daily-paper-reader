---
title: "ManipLVM-R1: Reinforcement Learning for Reasoning in Embodied Manipulation with Large Vision-Language Models"
title_zh: ManipLVM-R1：基于大型视觉语言模型的具身操纵推理强化学习
authors: "Zirui Song, Guangxian Ouyang, Mingzhe Li, Yuheng Ji, Chenxi Wang, Zixiang Xu, Zeyu Zhang, Xiaoqing Zhang, Qian Jiang, Fengxian Ji, Zhenhao Chen, Zhongzhi Li, Xiuying Chen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38922/42884"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于可验证奖励的强化学习用于大型视觉语言模型操纵
tldr: 现有基于大型视觉语言模型的机器人操纵方法依赖昂贵的人工标注数据，泛化能力受限。本文提出ManipLVM-R1，一种利用可验证奖励进行强化学习的新框架，直接优化任务对齐结果。该方法不仅消除了对标注数据的依赖，还通过物理推理增强泛化能力，在域外场景中表现出显著提升，为LVLMs在复杂操纵任务中的应用提供了可扩展的解决方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38922/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1851, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38922/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1458, \"height\": 780, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38922/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1633, \"height\": 986, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38922/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1351, \"height\": 716, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38922/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1833, \"height\": 688, \"label\": \"Table\"}]"
motivation: LVLMs在操纵中依赖昂贵标注且泛化差，尤其在域外场景中表现不佳。
method: 提出ManipLVM-R1，采用可验证奖励的强化学习框架，直接优化任务对齐结果，替代传统监督。
result: 在域外操纵任务上显著提升了泛化能力和物理推理准确性，且无需人类标注。
conclusion: RLVR能够有效训练LVLMs，减少标注成本并增强鲁棒性，是未来操纵学习的重要方向。
---

## Abstract
Large Vision-Language Models (LVLMs) have recently advanced robotic manipulation by leveraging vision for scene perception and language for instruction following.
However, existing methods rely heavily on costly human-annotated training datasets, which limits their generalization and causes them to struggle in out-of-domain (OOD) scenarios, reducing real-world adaptability. To address these challenges, we propose ManipLVM-R1, a novel reinforcement learning framework that replaces traditional supervision with Reinforcement Learning using Verifiable Rewards (RLVR). By directly optimizing for task-aligned outcomes, our method enhances generalization and physical reasoning while removing the dependence on costly annotations. Specifically, we design two rule-based reward functions targeting key robotic manipulation subtasks: an Affordance Perception Reward to enhance localization of interaction regions, and a Trajectory Match Reward to ensure the physical plausibility of action paths. These rewards provide immediate feedback and impose spatial-logical constraints, encouraging the model to go beyond shallow pattern matching and instead learn deeper, more systematic reasoning about physical interactions. Experimental results show that ManipLVM-R1 achieves substantial performance gains across multiple manipulation tasks, using only 50% of the training data while achieving strong generalization to OOD scenarios. We further analyze the benefits of our reward design and its impact on task success and efficiency.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有基于大型视觉语言模型（LVLMs）的机器人操纵方法严重依赖昂贵的人工标注数据集进行监督微调（SFT），导致模型泛化能力弱，在域外场景（OOD）中性能显著下降，限制了实际部署的适应性。
- **研究动机**：为替代SFT对标注的依赖，作者引入可验证奖励的强化学习（RLVR）范式，该方法在数学和编程领域已展示出消除人工反馈的优势，但在机器人操纵中面临奖励稀疏、延迟及缺乏空间‑逻辑约束的挑战。
- **整体含义**：提出一套名为**ManipLVM-R1**的RLVR框架，通过任务对齐的结构化奖励直接优化模型输出，从而激发LVLM在具身操纵中的深层物理推理能力，减少监督成本并提升泛化性。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：以RLVR为核心，将复杂操纵任务分解为**功能感知（Affordance Perception）** 和**轨迹预测（Trajectory Prediction）** 两个子任务，并分别设计基于规则的、可验证的奖励函数，为每个生成的响应提供即时、结构化的反馈，同时利用GRPO（基于组相对策略优化）进行稳定策略更新。

- **关键技术细节**：
  - **奖励函数设计**：
    - **功能感知奖励** \(R_{spatial} = R_{format} + R_{aff}\)
      - \(R_{format}\)：检查输出是否遵循 `<think>...</think>` 和 `<answer>...</answer>` 的格式。
      - \(R_{aff} = IoU(b^*, \hat{b})\)：预测框与真值的交并比，衡量空间定位精度。
    - **轨迹匹配奖励** \(R_{trajectory} = R_{format} + R_{path} + R_{end}\)
      - \(R_{format}\)：除格式约束外，还要求预测点数在 3–10 之间。
      - \(R_{path}\)：由离散Fr&#233;chet距离、Hausdorff距离和RMSE三个几何相似度指标归一化后加权求和，评估轨迹整体形状与局部偏差。
      - \(R_{end} = \exp(-k \| \hat{p}_N - p^*_M \|_2)\)：基于终点欧氏距离的指数衰减，鼓励精确到达目标。
  - **策略更新（类似GRPO）**：
    - 对每个输入，从当前策略 \(\pi_\theta\) 采样 \(G\) 个响应，分别计算奖励 \(\{r_1,\dots,r_G\}\)。
    - 归一化得到优势值 \(A_i = (r_i - \text{mean}) / \text{std}\)。
    - 最大化优势加权似然，同时通过 KL 散度约束新策略不过分偏离参考模型 \(\pi_{\text{ref}}\)。

## 3. 实验设计：数据集、基准与对比方法

- **数据集**：
  - **域内训练**：使用 **ShareRobot**（源于 Open X-Embodiment），包含 >1M 规划QA对、6.5k 带密集功能标注的图像、6.8k 带轨迹标签的帧，覆盖 102 个真实场景和 12 种机器人。
  - **域外测试**：
    - 功能感知：**UMD Part Affordance**，选取 grasp、cut、pound、scoop 四类，随机采样 1200 张图片。
    - 轨迹预测：**VAIT** 的验证子集（经人工校对），共 500 对样本。

- **基准 (Benchmark)**：分别评估功能感知和轨迹预测的性能，主要指标：
  - 功能感知：任务成功率（IoU > 0.5）及平均 IoU。
  - 轨迹预测：任务成功率（终点距离 < 20 像素），以及平均 DFD、HD、RMSE。

- **对比方法**：
  - **开源零/少样本模型**：Phi-4-multimodal-Instruct、Gemma-3（4B/12B/27B）、Qwen2.5-VL（3B/7B/32B）、LLARVA、VILA1.5-13B。
  - **监督微调模型**：LLaVA-1.6-7B、InternVL2-2B、Qwen2.5-VL-3B-SFT、RoboBrain-7B。
  - **本模型**：ManipLVM-R1-3B（仅使用 50% 训练数据）。

## 4. 资源与算力

- **明确说明**：论文正文及实验部分**未提及**所用的 GPU 型号、数量、训练时长或总计算量。仅指出模型基于 Qwen2.5-VL-3B 进行 RLVR 训练，未给出具体硬件配置与训练成本。

## 5. 实验数量与充分性

- **实验数量**：
  - 域内实验：两个子任务的定量对比（表1），涵盖 16 个模型/变体。
  - 域外实验：同样结构（表2），对比 14 个模型/变体，并对 UMD 数据集按类别详细报告 IoU。
  - 消融与效率分析：图1（右）展示了仅用 50% 数据时，RLVR 相比 SFT 在 IoU 和轨迹距离上的优势；图1（左）提供了空域可视化对比。
  - 定性分析：呈现了“惊喜时刻”推理成功案例与典型失败案例（图3）。

- **充分性与公平性**：
  - **充分**：覆盖了主要开源基线与监督微调基线，且本模型参数规模较小（3B），对比了更大模型（如32B、7B），使结果有说服力。
  - **公平**：所有基线在完整训练集下训练/评估，而本模型只用半数数据，性能仍领先，凸显样本效率。域外测试采用其他数据集，避免数据泄露。
  - **可改进**：缺少对奖励函数各组件重要性（如去掉 R_path 或 R_end）的系统消融，以及不同超参数（β、G）的敏感性分析。但总体实验设计较为完整。

## 6. 论文的主要结论与发现

- 在**域内**设置下，ManipLVM-R1-3B 在功能感知任务上达到 **31.0 IoU**（远超 RoboBrain-7B 的 11.79），在轨迹预测上平均误差仅 110.87，性能与更大规模监督模型持平甚至胜出。
- 在**域外**设置下，模型在 Grasp-IoU（34.65）和 VAIT 平均轨迹误差（131.99）上取得最优，全面超过 Qwen2.5-VL-32B-Instruct 和 RoboBrain-7B。
- 仅使用 **50%** 训练数据即可实现上述提升，证明 RLVR 在机器人操纵中可大幅降低监督成本。
- 定性分析发现模型能产生**隐式多步推理**（“aha moments”），但也在常识知识（如门把手 vs. 锁孔）和空间误判场景下暴露不足，说明仍需引入自验证机制。

## 7. 优点

- **方法论创新**：率先将 RLVR 应用于具身操纵，设计专门的结构化奖励，使模型学习物理推理而非模式匹配。
- **监督成本大幅降低**：仅需50%数据便超越完全监督方法，展示出高样本效率。
- **强泛化能力**：在分布外任务上一致优于多种开源和监督基线，验证了方法的鲁棒性。
- **奖励设计合理**：结合格式奖励与多指标几何奖励，提供即时且富有物理意义的反馈，避免奖励稀疏问题。
- **可解释性**：模型输出的 `<think>` 推理过程可作为决策解释窗口，有助于分析失败原因。

## 8. 不足与局限

- **缺乏对算力的明确报告**：未说明 GPU 型号、训练时间，难以全面评估方法的计算效率与复现成本。
- **实验覆盖范围有限**：域外测试仅选取了有限类别（4 种 affordance 和纯视觉轨迹），未涉及真实机器人硬件部署或动态环境；未与经典 RL‑based 操纵方法（如 RLafford、RGB‑based 策略）对比。
- **奖励设计依赖人工先验**：规则形式的奖励虽免除标注，但仍需专家手工设定阈值与度量组合，且未对奖励权重与任务性能的关系进行消融。
- **模型规模单一**：仅验证了 3B 模型，未探讨在更大 VLM（如 7B、32B）上的效果与扩展性。
- **失败模式的分析不深入**：定性指出常识与空间错误，但未定量统计各类失败占比或提出针对性缓解策略。
- **仅限于离线的视觉推理**：方法只输出坐标/轨迹，未与物理执行同步或处理闭环反馈，实用性受限于仿真与静态设定。

（完）
