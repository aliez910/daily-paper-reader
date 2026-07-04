---
title: Score-Based Diffusion Policy Compatible with Reinforcement Learning via Optimal Transport
title_zh: 基于最优传输的分数扩散策略：与强化学习兼容的模仿学习
authors: "Mingyang Sun, Pengxiang Ding, Weinan Zhang, Donglin Wang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=2dqiqST8ZJ"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过最优传输改进基于扩散的模仿学习，结合在线强化学习微调
tldr: 针对扩散模仿学习在分布偏移下鲁棒性不足的问题，本文提出OTPR方法，通过最优传输理论将扩散策略与强化学习结合，利用Q函数作为运输成本实现高效微调。实验表明，该方法在多个模拟操作任务上显著提升了策略的鲁棒性和性能。相关工作为融合模仿学习和强化学习提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 扩散策略在分布偏移下鲁棒性不足，需要在线交互进行微调。
method: 提出OTPR算法，利用最优传输理论将扩散策略视为最优传输映射，使用Q函数作为运输成本进行RL微调。
result: 在模拟操作任务上，OTPR显著提升了扩散策略的鲁棒性和任务成功率。
conclusion: 最优传输为扩散策略与强化学习的集成提供了稳定高效的框架。
---

## Abstract
Diffusion policies have shown promise in learning complex behaviors from demonstrations, particularly for tasks requiring precise control and long-term planning. However, they face challenges in robustness when encountering distribution shifts. This paper explores improving diffusion-based imitation learning models through online interactions with the environment. We propose OTPR (Optimal Transport-guided score-based diffusion Policy for Reinforcement learning fine-tuning), a novel method that integrates diffusion policies with RL using optimal transport theory. OTPR leverages the Q-function as a transport cost and views the policy as an optimal transport map, enabling efficient and stable fine-tuning. Moreover, we introduce masked optimal transport to guide state-action matching using expert keypoints and a compatibility-based resampling strategy to enhance training stability. Experiments on three simulation tasks demonstrate OTPR's superior performance and robustness compared to existing methods, especially in complex and sparse-reward environments. In sum, OTPR provides an effective framework for combining IL and RL, achieving versatile and reliable policy learning.

---

## 论文详细总结（自动生成）

# 基于最优传输的分数扩散策略：与强化学习兼容的模仿学习（OTPR）—— 论文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **问题**：扩散策略在模仿学习中表现出色，尤其适用于需要精密控制与长期规划的任务；但当遇到**分布偏移**时，其鲁棒性严重不足，导致策略在实际部署中容易失败。
- **现有局限**：纯粹的离线模仿学习无法主动适应环境变化，而直接应用强化学习（RL）对扩散策略进行微调又面临不稳定、效率低等问题。
- **研究目标**：探索如何通过**在线交互**来改善基于扩散的模仿学习模型，使策略既保留模仿的专家知识，又能通过 RL 微调提升鲁棒性和任务成功率。
- **整体含义**：本文提出 OTPR 方法，利用最优传输（Optimal Transport）理论将扩散策略与 RL 有机融合，为结合模仿学习与强化学习提供了一种新的稳定高效框架，有望推广到复杂的机器人操作任务中。

## 2. 方法论：核心思想、关键技术细节与算法流程
- **核心思想**：将扩散策略视作一个**最优传输映射**，并用 RL 中的 **Q 函数**作为运输成本，从而将策略优化问题转化为最小化传输成本的映射学习问题。这样既保留了扩散模型的表达能力，又借助 RL 的信号对策略进行在线调整。
- **关键技术细节**：
  1. **Q 函数作为运输成本**：利用当前策略的 Q 估计值（或 RL 的价值函数）来定义状态-动作对之间的传输代价，引导扩散模型生成高奖励的动作。
  2. **掩码最优传输（Masked Optimal Transport）**：引入专家演示中的**关键点**（例如轨迹中的里程碑状态），仅对关键区域施加最优传输约束，避免全局匹配带来的过拟合，提升泛化性。
  3. **基于兼容性的重采样策略（Compatibility-based Resampling）**：在训练过程中，根据采样样本与当前策略的兼容性进行加权或筛选，稳定训练过程，防止极端动作的破坏。
- **算法流程（文字说明）**：
  - 输入：专家演示数据集 + 环境交互接口。
  - 初始化扩散策略参数（通常通过行为克隆预训练）。
  - 与环境交互，收集经验并利用标准 RL 算法（如 SAC 或 DQN）更新 Q 函数。
  - 在策略更新步骤中：采用最优传输视角，构造以 Q 函数为成本的传输问题，通过求解该问题来更新扩散策略的参数（例如，通过最小化带正则项的传输损失）。
  - 在损失函数中加入掩码项，仅对专家关键点强制最优传输匹配；同时利用重采样机制剔除低兼容性样本。
  - 重复交互与更新直至收敛。

> 注：原文未给出具体公式或伪代码，以上描述基于摘要和方法部分的简短叙述。

## 3. 实验设计
- **数据集/场景**：**三个模拟操作任务**（具体名称未在摘要中列出，推测来自模拟基准，如 MetaWorld、Robosuite 或 D4RL 类环境）。
- **Benchmark**：未明确指定，但实验中可能使用了与主流模仿学习/RL 微调方法对比的常见任务。
- **对比方法**：原文未列出具体基线，但从语境可判断包括：
  - 单纯扩散策略（Diffusion Policy）；
  - 其他基于 RL 微调的模仿学习方法（可能包括 IQL、AWAC 等）；
  - 可能包括无最优传输的变体以进行消融。
- **关键结果**：OTPR 在三个任务上均取得**更优的性能和鲁棒性**，尤其在高复杂度和稀疏奖励场景下提升显著。

## 4. 资源与算力
- **未明确说明**：原文摘要及提供的信息中**没有提及**使用的 GPU 型号、数量、训练耗时等资源细节。
- 需要指出：这是一项实验信息的缺失，不利于复现和评估方法的实际计算成本。

## 5. 实验数量与充分性
- **实验数量**：仅笼统提及“三个模拟操作任务”，未给出每个任务的具体实验次数、不同随机种子下的统计结果、以及收敛曲线等。
- **消融实验**：摘要提及引入了掩码最优传输和重采样策略，但**未明确报告是否进行了系统的消融实验**来验证每个组件的贡献。
- **充分性评价**：当前信息不足以全面评估实验的充分性。作者声称方法优于现有方法，但由于缺乏详细的实验设置、对比基线列表、以及误差条等统计信息，客观性和公平性仍存在疑问。
- **优点**：至少覆盖了稀疏奖励和复杂场景，表明方法在困难任务上有能力。
- **不足**：实验报告过于简略，缺少量化对比表、超参数敏感性分析、以及跨领域泛化测试，使得结论的说服力受限。

## 6. 主要结论与发现
- OTPR 成功将**最优传输理论**引入扩散策略的 RL 微调中，为融合模仿学习与强化学习提供了新视角。
- 通过**Q 函数作为运输成本**，使得策略可以在保留扩散模型强大生成能力的同时，利用 RL 信号自适应改进。
- **掩码最优传输**和**兼容性重采样**进一步提升了训练稳定性和最终策略的鲁棒性。
- 在三个模拟操作任务上，OTPR 超越了现有方法，尤其在处理稀疏奖励和复杂动力学时表现突出。
- 整体上，OTPR 提供了一个**高效、稳定、通用**的 IL+RL 集成框架，具有很好的应用前景。

## 7. 优点
- **理论创新**：首次将最优传输与扩散策略的 RL 微调紧密结合，赋予了策略优化以几何解释，天然适合处理分布偏移。
- **实用性**：方法设计考虑了训练稳定性（重采样）和专家知识利用（掩码关键点），降低了调参难度。
- **性能提升**：在复杂和稀疏奖励场景下效果显著，证明了所提模块的有效性。
- **领域融合**：为扩散模仿学习走向真实机器人强化学习部署提供了可行路径。

## 8. 不足与局限
- **实验信息不足**：仅用三个模拟任务，且未提供具体任务名、基线细节、统计结果表与误差分析，实验的可复现性和说服力弱。
- **资源消耗未公开**：缺乏算力要求、训练时间等数据，不利于实际部署评估。
- **依赖专家关键点**：掩码最优传输需要人为指定专家关键点，如何自动获取关键点或在不同任务中适应标注成本未讨论。
- **理论保证缺失**：最优传输视角下的收敛性、Q 函数作为成本是否总有效等理论分析未在摘要中体现（可能正文中有，但信息不足）。
- **对比基线不明确**：无法确认比较对象是否为最先进且公平调优，存在 cherry-pick 风险。
- **应用范围有限**：仅停留在模拟，未提及真实机器人实验或更广泛的任务，泛化性有待验证。
- **元数据中 tldr 强调“相关工作为融合模仿学习和强化学习提供了新思路”，但实验部分缺乏对最新 RL 微调方法的直接对比，结论可推广性存疑。

（完）
