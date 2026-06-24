---
title: "Actor-Critic for Continuous Action Chunks: A Reinforcement Learning Framework for Long-Horizon Robotic Manipulation with Sparse Reward"
title_zh: 面向连续动作块的Actor-Critic：用于稀疏奖励长时域机器人操作的强化学习框架
authors: "Jiarui Yang, Bin Zhu, Jingjing Chen, Yu-Gang Jiang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38937/42899"
tags: ["query:rob-il"]
score: 4.0
evidence: 用于长时域操作的强化学习动作块方法
tldr: 现有强化学习方法难以处理长时域稀疏奖励操作任务。本文提出AC3框架，利用动作块范式并结合稳定的Actor-Critic机制，学习生成高维连续动作序列。实验证明在长时域操作任务中数据高效且稳定，为强化学习在复杂操作中的应用提供了新方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 879, \"height\": 680, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1679, \"height\": 839, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1679, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 849, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 853, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 852, \"height\": 366, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38937/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 851, \"height\": 368, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38937/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 854, \"height\": 265, \"label\": \"Table\"}]"
motivation: 解决强化学习在长时域稀疏奖励操作任务中的困难。
method: 提出AC3框架，采用动作块和稳定化机制。
result: 在长时域操作任务中实现数据高效的稳定学习。
conclusion: 提出了一种面向长时域操作的强化学习动作块框架。
---

## Abstract
Existing reinforcement learning (RL) methods struggle with long-horizon robotic manipulation tasks, particularly those involving sparse rewards. While action chunking is a promising paradigm for robotic manipulation, using RL to directly learn continuous action chunks in a stable and data-efficient manner remains a critical challenge. 
This paper introduces AC3 (Actor-Critic for Continuous Chunks), a novel RL framework that learns to generate high-dimensional, continuous action sequences. To make this learning process stable and data-efficient, AC3 incorporates targeted stabilization mechanisms for both the actor and the critic. First, to ensure reliable policy improvement, the actor is trained with an asymmetric update rule, learning exclusively from successful trajectories. Second, to enable effective value learning despite sparse rewards, the critic's update is stabilized using intra-chunk n-step returns and further enriched by a self-supervised module providing intrinsic rewards at anchor points aligned with each action chunk. We conducted extensive experiments on 25 tasks from the BiGym and RLBench benchmarks. 
Results show that by using only a few demonstrations and a simple model architecture, AC3 achieves superior success rates on most tasks, validating its effective design.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义
- **研究背景**：现有强化学习（RL）方法在短时域任务（如关门、关抽屉）上表现良好，但在长时域、稀疏奖励的机器人操作任务（如移动盘子、翻三明治）上探索空间巨大，且缺少中间反馈，导致学习极为困难。
- **现有局限**：模仿学习（IL）中的动作块（action chunking）范式（如ACT、Diffusion Policy）能生成连续动作序列，但其性能受限于专家数据上限，无法通过在线交互自我提升；将动作块引入RL时，离散化方法（如CQN-AS）牺牲精度，而复杂蒸馏管道（如Q-Chunking）计算成本高、依赖大规模离线数据。
- **本文目标**：提出一个直接、稳定、数据高效的RL框架，能够在**连续动作块**空间中进行学习，仅利用少量专家演示即可在长时域稀疏奖励任务中取得优异性能。

### 2. 方法论
- **核心思想**：基于DDPG框架，将Actor输出扩展为连续动作块（\(C\)步连续动作），并在稀疏奖励下通过两项关键稳定机制实现稳定训练。
- **关键技术细节**：
  - **Actor设计**：采用MLP+GRU架构预测长度为\(C\)的连续动作块\(A_t = \pi_\theta(s_t)\)，利用GRU捕捉时序依赖，输出为连续值，避免离散化损失。
  - **Critic设计**：评估状态-动作块对的价值\(Q_\phi(s_t, A_t)\)，同样采用MLP+GRU架构。
  - **异步Actor更新规则**：Actor**仅从成功轨迹**（包括专家演示和在线探索中的成功轨迹）中学习，避免被不可靠的Q值梯度误导。损失函数由BC损失（模仿成功动作）和Q损失（最大化价值）加权组合：
    \[
    \mathcal{L}_\theta = \lambda_{\text{BC}} \mathbb{E}_{(s_t, A_t^{\text{exp}})\sim\mathcal{B}_{\text{succ}}}[\|\pi_\theta(s_t)-A_t^{\text{exp}}\|^2] - \lambda_Q \mathbb{E}_{s_t\sim\mathcal{B}_{\text{succ}}}[\min_{i=1,2} Q_{\phi_i}(s_t, \pi_\theta(s_t))]
    \]
  - **Critic稳定更新**：
    - 使用**chunk内n步回报**（\(n < C\)）作为TD目标，平衡宏观规划与微观控制，降低噪声：
      \[
      y_t = \sum_{k=0}^{n-1} \gamma^k r_{t+k} + \gamma^n \min_{i=1,2} Q_{\phi'_i}(s_{t+n}, \pi_\theta(s_{t+n}) + \epsilon)
      \]
    - 采用clipped double-Q机制抑制过估计。
  - **自监督内在奖励**：
    - 先用专家演示通过对比学习预训练一个目标网络\(G_\omega\)（triplet loss），将状态嵌入低维空间。
    - 在线交互时，每隔\(K\)步（与动作块对齐）计算当前状态与演示状态的最小嵌入距离\(d(s_t)\)，若距离小于阈值则提供固定正奖励（如0.1）作为锚点信号，引导探索。
- **算法流程简述**（对应Algorithm 1）：
  1. 初始化Actor、双Critic及目标网络，将专家演示填充至回放池\(\mathcal{B}\)。
  2. 预训练目标网络\(G_\omega\)。
  3. 每\(C\)步用Actor生成带噪声的动作块，逐步执行其中单步动作，并根据锚点注入内在奖励。
  4. 采样mini-batch，计算n步目标更新Critic。
  5. 从mini-batch中筛选成功轨迹，用BC+Q损失更新Actor（仅成功轨迹）。

### 3. 实验设计
- **数据集与场景**：
  - **BiGym**（15个任务）：双手机器人移动操作，专注多子任务与精细操作。使用3个视角的84×84 RGB图像（头、左腕、右腕），**每任务仅10条人类演示**作为离线数据。
  - **RLBench**（10个任务）：桌面操作任务，使用4个视角的84×84 RGB图像（前、腕、左肩、右肩），**每任务100条合成演示**。
- **Benchmark**：上述两个基准下的**25个任务**，奖励均为稀疏二元（成功=1，否则=0）。
- **对比方法**：
  - **CQN-AS**：基于离散动作块的层次化Q学习方法。
  - **DrQ-v2**：单步动作的actor-critic基线，辅以BC损失帮助探索。
  - **Chunk-wise BC**：使用与AC3 Actor相同架构，仅用离线数据做行为克隆。
- **评估**：每任务训练50k步，每隔一定步数在25个episode上测试成功率，报告3个种子的均值与标准差。

### 4. 资源与算力
- **文中明确说明**：所有实验在**单张RTX 3090 GPU**上完成。
- **未明确信息**：没有给出每任务的具体训练耗时或总GPU小时数，仅提及训练步数为50k步。

### 5. 实验数量与充分性
- **主要实验**：覆盖25个多样化任务（15个BiGym + 10个RLBench），每个任务运行3个随机种子，对比4种方法，结果用曲线图展示性能趋势，**数量足够**。
- **消融实验**（代表性子集）：
  - 动作块长度 \(C\) 的影响（BiGym的move plate和RLBench的open oven）。
  - intra-chunk n步回报的不同\(n\)值（1,4,8,16）。
  - 自监督奖励设计（无奖励、线性递增、与成功奖励相同等）。
  - 异步更新规则（仅成功轨迹 vs 所有轨迹）。
  - 模型复杂度与推理速度对比表（参数量、推理延迟）。
- **公平性与客观性**：所有RL基线均配同等的BC辅助损失（DrQ-v2和CQN-AS均有辅助），且使用方法间一致的观测和奖励设定；但对比方法中缺少Q-Chunking（作者指出其复杂度高、依赖大规模数据），且所有实验仅在仿真环境进行，无真实机器人验证，**存在一定选择性偏差**。

### 6. 主要结论与发现
- **AC3在25个任务中多数取得最高成功率**，尤其在长时域、高维动作空间任务上提升显著（如BiGym的move plate，AC3曲线快速上升）。
- **关键机制有效性**：
  - 动作块长度需适中：任务复杂度高时，大块（C=16）提供时序一致性；任务简单时，小块更利于精确探索。
  - intra-chunk n步回报（\(n=4,8\)）优于全块（\(n=C\)）或单步（\(n=1\)），能平衡规划与修正。
  - 自监督内在奖励明显提升复杂任务性能，但若奖励设置不当（如线性递增）会导致Q值爆炸。
  - 异步更新（仅成功轨迹）是训练稳定的核心，否则策略完全退化。
- **效率优势**：AC3的Actor仅6.56M参数，推理2.9ms，是CQN-AS（28.58M, 9.5ms）的**3倍以上**，适合高频率控制。

### 7. 优点
- **直接连续动作块**：避免离散化精度损失，DDPG风格框架简单直接，易于实现。
- **双重稳定机制**：
  - 异步Actor更新创造了“可信区域”，避免稀疏奖励下Q值噪声影响策略。
  - n步回报与自监督锚点结合，使Critic学习更平稳。
- **数据高效**：仅需少量演示（BiGym仅10条）即可启动在线改进，并快速超越纯模仿。
- **消融实验全面**：验证了各设计组件的必要性，结论可信。
- **推理速度快**：低参数量+简单架构，适合实时部署。

### 8. 不足与局限
- **实验覆盖**：
  - 仅包含仿真Benchmark，缺乏真实机器人平台验证，结论在真实环境下的泛化性未知。
  - 未与同期的连续动作块RL方法Q-Chunking直接比较（虽然作者说明了方法复杂度差异，但仍缺少量化对比）。
  - 种子数只有3个，统计显著性较弱（尤其对于任务间方差大的情况）。
- **方法依赖**：
  - 异步更新依赖成功轨迹筛选，在初期成功轨迹极少时可能回退到纯BC，限制了探索效率的初始相位。
  - 动作块长度\(C\)需手动调整，任务间最优值差异大（简单任务要求小块，复杂任务要求大块），缺乏自适应机制。
  - 自监督内在奖励依赖于对比学习预训练和手工设定的阈值/步长，对演示质量敏感，且可能在某些任务上导致Suboptimal exploitation。
- **应用限制**：
  - 论文未讨论多任务或大任务族（Task Family）的泛化性，仅展示单任务学习。
  - 模型假设动作块长度固定，无法适应变时域细粒度控制需求。
  - 推理速度虽快，但离线预训练（目标网络）需要额外数据和计算，虽非主要开销但增加部署步骤。

（完）
