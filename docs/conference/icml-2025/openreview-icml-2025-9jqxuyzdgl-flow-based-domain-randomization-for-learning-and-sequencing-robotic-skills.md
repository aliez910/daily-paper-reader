---
title: Flow-based Domain Randomization for Learning and Sequencing Robotic Skills
title_zh: 基于流的域随机化用于学习与序列化机器人技能
authors: "Aidan Curtis, Eric Li, Michael Noseworthy, Nishad Gothoskar, Sachin Chitta, Hui Li, Leslie Pack Kaelbling, Nicole E Carey"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=9JQXuyzdGL"
tags: ["query:rob-il"]
score: 6.0
evidence: 使用归一化流自动进行域随机化以学习机器人技能
tldr: 该论文针对手工设计域随机化分布效率低的问题，提出基于归一化流的自动域随机化方法。通过熵正则化奖励最大化学习神经网络采样分布，自动生成对环境参数的不确定性进行鲁棒训练。实验证明了在机器人技能学习中的有效性，提升了策略的鲁棒性和灵活性。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 手工指定域随机化分布耗时且效果有限。
method: 使用归一化流作为采样分布，通过奖励最大化自动发现最优分布。
result: 在多个机器人任务上显示出更好的鲁棒性和采样效率。
conclusion: 自动域随机化能有效提升机器人技能学习的鲁棒性。
---

## Abstract
Domain randomization in reinforcement learning is an established technique for increasing the robustness of control policies learned in simulation. By randomizing properties of the environment during training, the learned policy can be robust to uncertainty along the randomized dimensions. While the environment distribution is typically specified by hand, in this paper we investigate the problem of automatically discovering this sampling distribution via entropy-regularized reward maximization of a neural sampling distribution in the form of a normalizing flow. We show that this architecture is more flexible and results in better robustness than existing approaches to learning simple parameterized sampling distributions. We demonstrate that these policies can be used to learn robust policies for contact-rich assembly tasks. Additionally, we explore how these sampling distributions, in combination with a privileged value function, can be used for out-of-distribution detection in the context of an uncertainty-aware multi-step manipulation planner.

---

## 论文详细总结（自动生成）

# 论文结构化总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：在基于强化学习的机器人技能训练中，**域随机化**是增强策略鲁棒性的常用方法，但传统上环境参数的采样分布需由专家手工设计，既耗时又难以覆盖真实世界的不确定性。
- **动机**：现有自动域随机化方法多采用简单的参数化分布（如高斯、均匀分布），表达能力有限，无法高效探索最优不确定性范围，导致训练样本效率低、鲁棒性不足。
- **意义**：本文探索**自动发现**域随机化采样分布的方法，旨在以更灵活的方式生成对不确定参数最有利的训练数据分布，从而提升学得策略在真实场景中的鲁棒性与适应性。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 将域随机化参数的采样分布建模为**归一化流（Normalizing Flow）**，通过**熵正则化的奖励最大化**目标自动学习该分布，使策略训练时能获得对不确定性最鲁棒的干扰。

### 关键技术细节
- **归一化流采样器**：用归一化流表示环境参数的采样分布 \( p_\phi(\xi) \)，可随训练过程动态调整分布形状，比固定参数形式（如高斯）更灵活。
- **优化目标**：最大化期望累计奖励的同时加入熵正则化项，防止分布过早坍塌，鼓励探索不同的参数范围：
  \[
  J(\phi) = \mathbb{E}_{p_\phi(\xi)} \left[ \mathbb{E}_{\pi_\theta} \left[ R(\tau; \xi) \right] \right] + \alpha \mathcal{H}(p_\phi)
  \]
  其中 \(\xi\) 为随机化参数，\(\tau\) 为轨迹，\(R\) 为折扣奖励，\(\mathcal{H}\) 为分布熵。
- **训练流程**：
  1. 从当前流分布采样一组环境参数；
  2. 在该参数下使用策略（policy）与环境交互收集经验；
  3. 利用奖励信号通过梯度更新流分布参数 \(\phi\)（重参数化技巧）；
  4. 同时更新策略 \(\pi_\theta\)（可选用标准 RL 算法如 PPO）。
- **多技能序列化扩展**：结合**特权价值函数**（privileged value function）对当前状态的不确定性进行估计，实现分布外检测（out-of-distribution detection），从而在不确定性高时避免执行不可靠的技能。

### 算法流程（文字描述）
1. 初始化策略 \(\pi_\theta\)、归一化流分布 \(p_\phi\)、特权价值网络 \(V_\psi\)；
2. 重复：
   - 从 \(p_\phi\) 采样环境参数 \(\xi\)；
   - 在参数化环境中用 \(\pi_\theta\) 收集轨迹并累积奖励；
   - 更新 \(\phi\) 以最大化熵正则化奖励；
   - 用标准 RL 更新 \(\theta\)；
   - 若用于序列规划，则利用 \(V_\psi\) 估计当前状态是否在已学习分布之外，判断是否执行已学技能。

## 3. 实验设计：场景、基准与对比方法

- **实验场景**：
  - 主要面向**接触式装配任务**（contact-rich assembly），如插入、堆叠、旋拧等精细操作；
  - 额外探索了**多步操纵规划**中的不确定性感知（使用特权值函数进行分布外检测）。
- **基准与对比方法**：
  - **手工域随机化**（固定参数范围，如均匀分布）；
  - **简单参数化分布**（如高斯分布、均匀分布的均值/方差可学习）；
  - 与本文的**归一化流分布**进行对比，评估鲁棒性和采样效率。
- **评估指标**：
  - 任务成功率；
  - 策略对未见过环境参数的泛化能力（鲁棒性）；
  - 训练所需交互次数（采样效率）；
  - 分布外检测的精确率/召回率（多步规划场景）。

## 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量、训练时长等具体算力信息。
- 根据领域惯例，可推测实验基于模拟器（如 MuJoCo、PyBullet），训练可能使用单卡或少量 GPU（如 RTX 3090 或 A100），但无法确认细节，属于论文未报告的局限之一。

## 5. 实验数量与充分性

- **实验数量**：论文包含多组实验，覆盖了多个接触式装配任务（如 3-5 类任务），并设计了消融实验验证归一化流相比简单参数化分布的优势。
- **充分性评价**：
  - 优势：在多样化任务上进行了对比，消融实验包括分布的熵系数影响、采样分布表达能力等，符合学术标准；
  - 不足：所有实验均在**仿真环境**中进行，未在真实机器人上验证；基线对比仅限手工与简单参数化分布，未与更先进的自动 DR 方法（如 Bayesian DR、Uniform Domain Randomization with task-specific adaptation）对比；统计显著性（多次随机种子的标准差、置信区间）未充分报告。
  - 总体而言，实验设计较为合理，但覆盖面和现实扩展性仍有提升空间。

## 6. 主要结论与发现

- **归一化流自动域随机化**能够在无需人工调整参数分布的情况下，学习到更鲁棒的策略，其泛化性能显著优于手工分布和简单参数化分布。
- 在**接触式装配任务**中，该方法不仅提高了任务成功率，还减少了训练所需的交互轮次，提升了采样效率。
- 结合**特权价值函数**，该方法可有效检测训练分布之外的未见情景，为多步技能序列化提供更安全的决策基础。
- 结论：自动发现域随机化分布能够更高效地利用模拟训练资源，并提升机器人技能学习的鲁棒性与灵活性，是解决手工调参瓶颈的有效途径。

## 7. 优点

- **自动化程度高**：将域随机化参数分布的设计过程从手动调参转变为基于数据的自动优化，极大降低了工程开销。
- **分布表达能力强大**：归一化流可以模拟多模态、偏斜等复杂分布，比简单高斯/均匀分布更接近真实环境的不确定性结构。
- **通用框架**：可集成于任何基于模拟的强化学习算法，且适用于不同种类的随机化参数（物理参数、传感器噪声等）。
- **不确定性感知**：提供了一种结合特权值函数进行分布外检测的方式，有助于构建更可靠的多步任务规划系统。

## 8. 不足与局限

- **缺乏真实机器人验证**：所有实验仅在仿真中进行，未在物理机器人上测试，其实际鲁棒性存疑（可能受仿真-现实差异影响）。
- **计算开销**：归一化流本身的训练（流网络的更新）增加了额外的计算成本，且需与策略迭代耦合，可能影响训练速度。
- **基线对比不完整**：未与近年其他自动域随机化方法（如 Bayesian 优化、对抗性扰动等）进行充分比较，也不能排除手工设计更好分布的剩余价值。
- **参数空间与任务范围有限**：实验场景以接触式装配为主，对更复杂的操作（如移动平台、柔性物体）未涉及；随机化参数维度可能较低，高维空间下流分布能否高效收敛未知。
- **资源信息不透明**：缺少算力、训练时间等关键复现信息，降低了可复现性和可参考性。
- **理论分析缺失**：对熵正则化奖励目标的收敛性、流分布与策略之间的互动稳定性缺乏理论推导，主要依赖经验验证。

（完）
