---
title: Evolutionary Reinforcement Learning with Parameterized Action Primitives for Diverse Manipulation Tasks
title_zh: 面向多样化操控任务的参数化动作基元进化强化学习
authors: "Xianxu Qiu, Haiming Huang, Weiwei Chen, Qiuzhen Lin, Wei-Neng Chen, Fuchun Sun"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33606/35761"
tags: ["query:rob-il"]
score: 4.0
evidence: 针对多样化机器人操控任务的强化学习方法，并采用分层动作基元
tldr: 本文针对需要学习长序列动作的机器人操控任务，指出传统强化学习算法面临动作空间巨大导致的探索效率低下以及采样不足引发的灾难性遗忘问题。为此，作者提出进化强化学习方法 ERLAP，将进化算法与分层强化学习相结合，并维护一组参数化的异构动作基元库，从而在不同操控任务上获得更高效的策略学习。该工作直接涉及机器人操控与控制，但采用的是强化学习而非模仿学习范式。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 731, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 894, \"height\": 896, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 788, \"height\": 525, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1831, \"height\": 1005, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 842, \"height\": 357, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1843, \"height\": 400, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33606/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1848, \"height\": 401, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33606/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1780, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33606/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 897, \"height\": 228, \"label\": \"Table\"}]"
motivation: 解决机器人操控任务中动作空间大导致的探索效率低和灾难性遗忘问题。
method: 提出 ERLAP，将进化算法与分层强化学习结合并使用参数化动作基元库。
result: 在多样化机器人操控任务上提升了学习效率与策略性能。
conclusion: 为复杂机器人操控提供一种高效的分层强化学习框架。
---

## Abstract
Reinforcement learning (RL) has shown promising performance in tackling robotic manipulation tasks (RMTs), which require learning a prolonged sequence of manipulation actions to control robots efficiently. However, most RL algorithms often suffer from two problems when solving RMTs: inefficient exploration due to the extremely large action space and catastrophic forgetting due to the poor sampling efficiency. To alleviate these problems, this paper introduces an Evolutionary Reinforcement Learning algorithm with parameterized Action Primitives, called ERLAP, which combines the advantages of an evolutionary algorithm (EA) and hierarchical RL (HRL) to solve diverse RMTs. A library of heterogeneous action primitives is constructed in HRL to enhance the exploration efficiency of robots and dual populations with new evolutionary operators are run in EA to optimize these primitive sequences, which can  diversify the distribution of replay buffer and avoid catastrophic forgetting. The experiments show that ERLAP outperforms four state-of-the-art RL algorithms in simulated RMTs with dense rewards and can effectively avoid catastrophic forgetting in a set of more challenging simulated RMTs with sparse rewards.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper following a specific structure with 8 points. Let me carefully analyze the paper and produce a comprehensive summary.

The paper is about ERLAP (Evolutionary Reinforcement Learning with Parameterized Action Primitives) for robotic manipulation tasks. Let me organize the information for each section.

1. Core problem and motivation: RMTs have large action spaces leading to inefficient exploration and catastrophic forgetting due to poor sampling efficiency.

2. Methodology: Combines EA with HRL, uses parameterized action primitives library, dual-population evolutionary mechanism, specific evolutionary operators (crossover + 4 mutations).

3. Experiments: Two sets - dense reward on Robosuite (6 tasks) and sparse reward on Unity (4 tasks). Compared with TD3, SAC, MAPLE, TRAPs, MAPLE+PER.

4. Resources: Not explicitly mentioned in the paper.

5. Experiment count: 6 dense reward tasks + 4 sparse reward tasks = 10 tasks total, 3 random seeds each.

6. Conclusions: ERLAP outperforms baselines, effectively avoids catastrophic forgetting.

7. Strengths: Novel combination of EA and HRL, dual-population mechanism, better sampling efficiency.

8. Limitations: Limited primitive library (handcrafted), computational cost of EA, evaluation only in simulation.

Let me write this up in Chinese with Markdown formatting.</think>

# 论文总结：ERLAP —— 面向多样化机器人操控任务的参数化动作基元进化强化学习

## 1. 核心问题与研究动机

- **研究背景**：机器人操控任务（RMTs）通常需要学习一条较长的动作序列以高效控制机器人。深度强化学习（DRL）在该领域表现出较强能力，但仍存在明显瓶颈。
- **两大核心问题**：
  - **探索效率低下**：操控任务的原始动作空间（力、力矩、关节技能等）维度极高，DRL 难以在其中高效搜索可行策略。
  - **灾难性遗忘**：由于采样效率不足，RL 智能体容易遗忘先前学到的优质经验，导致训练不稳定或策略退化。
- **现有方案的不足**：
  - HRL（分层强化学习）通过参数化动作基元（Parameterized Action Primitives）部分缓解探索负担，但高度依赖信息密集的奖励，并仍存在灾难性遗忘。
  - ERL（进化强化学习）通过种群机制缓解遗忘，但容易出现网络崩溃或缺乏语义，且并未真正缩小动作搜索空间。
- **研究空白**：尚无研究将 HRL 与 ERL 结合起来同时解决"探索效率低"和"灾难性遗忘"两个问题。

## 2. 方法论：ERLAP 框架

### 2.1 整体架构
ERLAP 由两个核心模块组成：
- **RL 模块**：采用 HRL 框架，将原始动作空间替换为"基元类型 + 参数"的参数化动作空间，并基于 SAC（Soft Actor-Critic）进行训练。
- **EA 模块**：维护**双种群**（Success Population $P_s$ 与 Development Population $P_d$），对完整的基元序列进行进化操作。

### 2.2 参数化动作基元库（5 种基元）
| 基元类型 | 参数维度 | 含义 |
|---------|---------|------|
| Reach | 4-D | 末端执行器到达目标位姿 (x,y,z,ψ) |
| Release | 4-D | 到达位姿并张开夹爪 |
| Open | 1-D | 张开夹爪（仅调整 ψ） |
| Grasp | 4-D | 到达位姿并闭合夹爪 |
| Micro-move | 4-D | 微小位移/角度调整 |

每个基元带有固定执行步数（$l_{reach}=l_{release}=l_{grasp}=20$, $l_{open}=1$, $l_{micro}=2$），整个序列累计步数超过阈值 $L$ 时停止生成。

### 2.3 RL 模块：基元序列生成
- 决策建模为 MDP，动作空间定义为：
  $$A = \bigcup_{a \in A_d} \{(a, x) \mid x \in X^a\}$$
  其中 $a$ 为基元类型，$x \in \mathbb{R}^{d_a}$ 为对应参数，组合成基元 $\xi = (a, x)$。
- **任务网络** $\pi_a(a_t | s_t)$：高层策略，采样基元类型。
- **参数网络** $\pi_a^p(x_t | s_t)$：低层策略集合，为所选基元生成参数。
- 基于 SAC 的损失函数（含双最大熵 $\alpha_t, \alpha_p$）：
  - 价值网络损失 $J_Q(\theta)$（式 2）
  - 任务网络损失 $J_{\pi_a}(\phi)$（式 3）
  - 参数网络损失 $J_{\pi^p}(\psi)$（式 4）

### 2.4 EA 模块：双种群进化机制
- **成功种群 $P_s$**：存储并保留高奖励基元序列；通过权重因子更新适应度：
  $$f_i \leftarrow \alpha \cdot f_i + \beta \cdot f \quad (\alpha=0.9, \beta=0.1)$$
- **开发种群 $P_d$**：规模更大，采用 UCB 策略选择个体：
  $$U_i = f_i + C \cdot \sqrt{\log(N)/n_i} \quad (C=4)$$
  适应度更新采用增量平均（式 7）。
- **种群间交互**：$P_d$ 中最优个体若优于 $P_s$ 中最弱者，则替换之，保证收敛。
- **关键设计**：当 $P_s$ 中最弱个体差于 RL 生成的序列 $S_{RL}$ 时，直接替换为 $S_{RL}$，以保留 RL 的优质经验。

### 2.5 序列进化算子（1 交叉 + 4 变异）
- **Crossover**：从 $P_s$ 选最优 2 个体，随机交换 1/4–1/2 长度的片段。
- **Replacement Mutation**：随机生成片段替换父代片段。
- **Deletion Mutation**：随机删除父代某一片段。
- **Addition Mutation**：在父代中插入新片段。
- **Gaussian Disturbance Mutation**：对所有基元参数加高斯噪声，不改变基元分布。

> 注意：前三类变异会改变基元分布，需要重新经参数网络处理后与环境交互；高斯扰动变异则可直接交互。

## 3. 实验设计

### 3.1 基准与场景
- **密集奖励实验**：Robosuite 仿真平台，6 个不同复杂度操控任务
  - Lift（LIF）、Pick-and-Place（PAP）、Nut-Assembly（NAS）、Peg-Insert（PIN）、Clean-Up（CUP）、Stack（STA）
- **稀疏奖励实验**：Unity 仿真平台，4 个更具挑战性的任务
  - Lift（LIF）、Pick-and-Place（PAP）、Stack（STA）、Put-into-Drawer（PID）

### 3.2 对比方法
- **密集奖励对比**：TD3、SAC、MAPLE（基元方法）、TRAPs（LTL+基元，SOTA）
- **稀疏奖励对比**：MAPLE、TRAPs、MAPLE+PER（在 MAPLE 中加入优先经验回放）

### 3.3 公平性设置
- 由于 ERLAP 引入双种群机制，为公平起见，将 ERLAP 网络侧采样步数设为基线的一半。

## 4. 资源与算力

- **论文中未明确说明**所使用的 GPU 型号、数量、训练时长或计算资源等具体细节。
- 仅可从实验规模推断：每组实验使用 **3 个随机种子**，实验覆盖 6 + 4 = 10 个任务场景。

## 5. 实验数量与充分性

- **实验总数**：
  - 密集奖励 6 任务 × 3 种子 = 18 组
  - 稀疏奖励 4 任务 × 3 种子 = 12 组
  - 加上奖励曲线、成功率统计、回放缓冲经验分布可视化等内容
- **公平性考量**：
  - 多个随机种子取平均并报告标准差（图中阴影区）。
  - 在采样公平性上做了调整（ERLAP 网络采样减半）。
- **充分性评估**：
  - 优势：覆盖了从密集到稀疏奖励、从简单到复杂的多种任务；与 4 个强基线对比，包含 SOTA（TRAPs）。
  - 不足：**未提供消融实验**（例如剥离双种群机制、剥离某种变异算子、剥离参数化基元等），难以判断各组件的独立贡献；只在仿真中验证，未涉及真实机器人实验。

## 6. 主要结论与发现

- **密集奖励实验**（表 1）：ERLAP 在 4 个任务上达到 100% 成功率，6 任务平均成功率 99.27%，超过 TRAPs（98.55%）、MAPLE（97.25%）、SAC（21.00%）、TD3（12.50%）。
- **采样效率**：相较 TRAPs 减少 18.8% 采样步数，相较 MAPLE 减少 30.1%。
- **稀疏奖励实验**（表 2）：在 4 个任务中均取得最佳结果，特别是 PID 任务中其他算法全部失败，ERLAP 仍达 77.6%；STA 任务中 81.8% vs MAPLE+PER 74.6%。
- **经验分布分析**（图 7）：ERLAP 双种群机制使回放缓冲中成功/失败经验比例显著优于其他算法，避免长尾效应导致的高质量经验难以采样。
- **核心结论**：将 HRL 与 EA 结合在统一框架内，可同时缓解探索效率低和灾难性遗忘两大难题。

## 7. 优点与亮点

- **首个将 HRL 与 ERL 联合的通用框架**：填补研究空白，且具备清晰的设计逻辑（基元解决探索、种群解决遗忘）。
- **双种群进化机制设计巧妙**：成功种群保留经验，开发种群通过 UCB 平衡 exploration-exploitation，UCB 系数 $C=4$ 设置合理。
- **面向序列而非单步动作的进化算子**：设计了 1 交叉 + 4 变异算子直接对完整基元序列操作，能捕获动作间的时序关联。
- **效率与性能并重**：在保持甚至提升成功率的同时显著减少采样步数。
- **基元库语义清晰**：5 种基元涵盖操控任务的常见子任务，便于扩展。

## 8. 不足与局限

- **缺乏消融实验**：未能定量分析双种群、各变异算子、参数化基元库等组件的独立贡献。
- **基元库依赖人工设计**：5 种基元为手工构造，难以泛化到任务差异较大的新场景；论文在结论中也承认这是未来工作方向（自动发现基元）。
- **仅在仿真环境验证**：未涉及真实机器人迁移，仿真到现实的 gap 未讨论。
- **算力与时间成本未披露**：双种群机制会带来额外环境交互开销（虽然以网络侧步数减半作为补偿），但总训练时长对比不明。
- **稀疏奖励下部分任务成功率仍有限**：STA 81.8% 和 PID 77.6% 表明算法在极高稀疏度任务上仍有提升空间。
- **基线代表性**：TRAPs 在密集奖励实验中已是 SOTA，但其与 ERLAP 的差距主要在"更稳定"而非"绝对性能"，优势幅度有限（< 1%）。
- **可扩展性未充分验证**：仅在 6+4 个任务上测试，未讨论基元组合爆炸或长序列场景的可扩展性。

（完）
