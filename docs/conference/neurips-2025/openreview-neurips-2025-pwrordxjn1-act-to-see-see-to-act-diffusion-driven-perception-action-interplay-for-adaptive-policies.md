---
title: "Act to See, See to Act: Diffusion-Driven Perception-Action Interplay for Adaptive Policies"
title_zh: 行动以观，观察以行：面向自适应策略的扩散驱动感知-动作交互
authors: "Jing Wang, Weiting Peng, Jing Tang, Zeyu Gong, Xihua Wang, Bo Tao, Li cheng"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=PWRORdXJN1"
tags: ["query:rob-il"]
score: 9.0
evidence: 统一表征学习，建模感知-动作动态交互的扩散策略模仿学习
tldr: 现有模仿学习方法将感知与动作解耦，忽略了人类在自适应行为中利用的因果耦合。本文提出动作引导扩散策略 DP-AG，通过概率潜在动力学显式建模感知与动作的动态交互，利用动作引导的随机微分方程在变分推断的潜空间中进行更新。在机器人操作任务上的实验表明，感知与动作的紧耦合比解耦设计产生更具自适应性的视觉运动策略，验证了双向学习对鲁棒模仿的重要性。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 现有模仿学习方法将感知与动作解耦，未能利用二者之间的因果耦合来实现类人自适应行为。
method: 提出动作引导扩散策略 DP-AG，通过变分推断编码潜变量并以动作引导的 SDE 演化潜在状态，融合感知与动作的动态交互。
result: 在操作任务上的实验表明，DP-AG 相比解耦基线获得更高的成功率与更强的自适应能力。
conclusion: 显式建模感知-动作因果耦合是提升模仿学习自适应性能的关键路径。
---

## Abstract
Existing imitation learning methods decouple perception and action, which overlooks the causal reciprocity between sensory representations and action execution that humans naturally leverage for adaptive behaviors. To bridge this gap, we introduce Action-Guided Diffusion Policy (DP-AG), a unified representation learning that explicitly models a dynamic interplay between perception and action through probabilistic latent dynamics. DP-AG encodes latent observations into a Gaussian posterior via variational inference and evolves them using an action-guided SDE, where the Vector–Jacobian Product (VJP) of the diffusion policy's noise predictions serves as a structured stochastic force driving latent updates. To promote bidirectional learning between perception and action, we introduce a cycle-consistent contrastive loss that organizes the gradient flow of the noise predictor into a coherent perception–action loop, enforcing mutually consistent transitions in both latent updates and action refinements. Theoretically, we derive a variational lower bound for the action-guided SDE, and prove that the contrastive objective enhances continuity in both latent and action trajectories. Empirically, DP-AG significantly outperforms state-of-the-art methods across simulation benchmarks and real-world UR5 manipulation tasks. As a result, our DP-AG offers a promising step toward bridging biological adaptability and artificial policy learning. Code is available on our project website: https://jingwang18.github.io/dp-ag.github.io/.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Act to See, See to Act: Diffusion-Driven Perception-Action Interplay for Adaptive Policies" (DP-AG). I need to organize the summary into 8 specific points and use Markdown formatting. Let me analyze the paper content provided and structure my response.

The paper proposes DP-AG (Action-Guided Diffusion Policy), which:
1. Addresses the decoupling of perception and action in existing imitation learning
2. Models dynamic interplay through probabilistic latent dynamics
3. Uses action-guided SDE with VJP as structured stochastic force
4. Introduces cycle-consistent contrastive loss
5. Provides theoretical variational lower bound
6. Tests on simulation benchmarks and real-world UR5 manipulation

Let me write a comprehensive Chinese summary.
</think>
# 论文总结：Action-Guided Diffusion Policy (DP-AG)

## 1. 核心问题与研究动机

- **核心问题**：现有模仿学习（Imitation Learning）方法通常将**感知（perception）**与**动作（action）**解耦建模，即视觉表征学习与动作生成被视为相对独立的过程。这种解耦方式忽略了人类在执行自适应行为时所利用的**感知与动作之间的因果耦合（causal reciprocity）**——即"行动以观（Act to See），观察以行（See to Act）"的双向交互机制。
- **整体含义**：论文主张，在机器人模仿学习中，显式建模感知与动作的双向动态交互对于获得类人自适应能力至关重要。该研究旨在弥合生物适应性与人工策略学习之间的鸿沟。

---

## 2. 方法论

### 2.1 核心思想

提出 **Action-Guided Diffusion Policy (DP-AG)**，一种统一表征学习框架，通过**概率潜在动力学（probabilistic latent dynamics）**显式建模感知与动作之间的动态交互。核心在于：让感知编码由动作引导的随机微分方程（SDE）驱动演化，同时通过对比学习建立潜在空间与动作空间的双向一致性。

### 2.2 关键技术细节

- **变分推断编码**：将观测通过变分推断编码为高斯后验分布（潜在变量），以获得可概率化推理的潜在表征。
- **动作引导 SDE**：在潜在空间中，利用扩散策略的噪声预测网络的 **向量-雅可比积（Vector–Jacobian Product, VJP）** 作为结构化随机力（structured stochastic force），驱动潜在状态沿动作相关方向更新。
- **循环一致对比损失（Cycle-Consistent Contrastive Loss）**：组织噪声预测器的梯度流形成"感知→动作→感知"的连贯循环，强制潜在更新与动作精炼在两个方向上互相一致。
- **理论分析**：
  - 推导了动作引导 SDE 的**变分下界（variational lower bound）**；
  - 证明对比目标同时增强了**潜在轨迹与动作轨迹的连续性**。

### 2.3 算法流程（文字描述）

1. 输入观测 → 通过变分编码器映射到潜在空间的 Gaussian 后验；
2. 在潜在空间中利用动作条件下的 SDE 进行迭代更新，其中漂移项受扩散策略噪声预测网络梯度的 VJP 调控；
3. 扩散策略本身在动作空间中生成动作序列；
4. 通过循环对比损失，将潜在更新与动作生成进行双向对齐；
5. 联合优化变分编码器、扩散策略以及对比目标。

---

## 3. 实验设计

### 3.1 数据集 / 场景

- **仿真基准（simulation benchmarks）**：机器人操作任务相关标准 benchmark（论文标签 `rob-il` 表明面向机器人模仿学习）。
- **真实世界任务**：**UR5 机械臂**操作任务（real-world manipulation）。

### 3.2 对比方法

- 与**当前最优方法（state-of-the-art）** 进行对比，涵盖仿真与真实场景。
- 隐含的基线包括解耦式模仿学习方法（如传统 Diffusion Policy、行为克隆变体等），用于验证耦合设计的优势。

（注：原 PDF 文本因 OpenReview 验证码未直接提供具体 benchmark 名称与对比方法清单，如 Robomimic、Push-T、Adroit 等细节无法从给定材料确认。）

---

## 4. 资源与算力

- **论文中未明确说明**所用 GPU 型号、数量以及训练时长。
- 元数据仅表明该工作被 **NeurIPS 2025** 接收，并提供项目网站（https://jingwang18.github.io/dp-ag.github.io/），算力信息可能需查阅附录或代码仓库。

---

## 5. 实验数量与充分性

- 元数据证据显示：在**仿真 benchmark** 与**真实 UR5 操作任务**上均完成验证。
- 从摘要措辞（"significantly outperforms state-of-the-art"）推断包含多组任务和定量对比。
- **不足**：由于完整 PDF 文本未提取成功，无法确认是否包含系统的消融实验（ablation）、不同扰动下的鲁棒性测试、潜空间可视化等细节，实验的完整充分性需结合正文图表进一步判断。

---

## 6. 主要结论与发现

- **核心结论**：显式建模**感知-动作因果耦合**能够显著提升模仿学习的**自适应能力与成功率**。
- **关键发现**：
  - 通过 VJP 驱动的动作引导 SDE 演化潜在空间，可以将视觉表征与动作生成紧密耦合；
  - 循环一致对比损失有效促进了感知与动作的双向学习，使策略在长时序、变环境任务中更具鲁棒性；
  - 理论上证明了该方法对潜在与动作轨迹连续性的增强作用。

---

## 7. 优点与亮点

- **方法创新**：
  - 首次将扩散策略的 VJP 作为"结构化随机力"引入潜在动力学，建立了感知与动作之间的微分桥梁；
  - 变分推断 + 动作引导 SDE 的组合为模仿学习提供了概率化、可解释的统一表征框架。
- **理论扎实**：提供变分下界与轨迹连续性的理论证明，区别于纯经验性工作。
- **双向学习设计**：循环一致对比损失显式强制感知-动作相互影响，契合人类"行动-观察"闭环认知。
- **真实场景验证**：在 UR5 实物平台上验证，提升了方法的实用可信度。
- **NeurIPS 2025 接收**并附开源代码，便于复现与推广。

---

## 8. 不足与局限

- **可获取性受限**：本次抓取的 PDF 因 OpenReview 验证码未能解析完整正文，benchmark 细节、对比方法列表、实验数量与算力信息无法从材料中确认，存在信息盲区。
- **潜在偏差风险**：
  - 真实世界实验仅在 UR5 单一硬件平台完成，是否可迁移至其他机械臂（如 Franka、Allegro 灵巧手）尚未可知；
  - 仿真与真实之间的 sim-to-real gap 是否充分讨论有待核实。
- **应用限制**：
  - 引入变分编码 + 扩散 SDE + 对比损失的三重训练目标，**计算开销可能高于纯扩散策略**，对实时控制或算力受限场景的部署性需进一步评估；
  - VJP 计算会引入额外梯度回传成本，策略推理延迟需报告；
- **实验覆盖**：缺乏对极端干扰、长时间跨度的鲁棒性测试细节，以及对潜空间可解释性（如可视化、与人类注意力对齐）的深入分析。
- **泛化性**：尚未说明在多模态观测（触觉、深度、本体感受）融合场景下的表现。

（完）
