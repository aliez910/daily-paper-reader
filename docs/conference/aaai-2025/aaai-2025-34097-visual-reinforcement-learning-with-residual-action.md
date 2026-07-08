---
title: Visual Reinforcement Learning with Residual Action
title_zh: 基于残差动作的视觉强化学习
authors: "Zhenxian Liu, Peixi Peng, Yonghong Tian"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34097/36252"
tags: ["query:rob-il"]
score: 5.0
evidence: 通过残差动作建模将高维图像映射到连续控制动作
tldr: 本文针对将高维视觉图像准确映射到连续控制动作的核心难题，指出传统决策模块仅依赖当前观测输出动作，分布具有任务依赖性且难以学习。作者提出ResAct方法，一种视觉强化学习框架，通过显式建模相邻观测差异对应的动作调整而非直接从原始观测学习动作。该残差动作范式在视觉连续控制任务上提升了学习效率与性能。尽管该方法基于强化学习而非模仿学习，但直接解决了机器人控制中的视觉到动作映射问题。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34097/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 794, \"height\": 1018, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34097/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 880, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34097/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1670, \"height\": 554, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34097/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 795, \"height\": 1059, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34097/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 650, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34097/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1740, \"height\": 645, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34097/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1830, \"height\": 683, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34097/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1831, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34097/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1825, \"height\": 539, \"label\": \"Table\"}]"
motivation: 视觉观测到连续动作的映射受任务分布依赖影响，传统策略网络难以直接学习。
method: 提出ResAct方法，通过建模相邻观测差异对应的动作调整来简化视觉到动作的学习。
result: 在视觉连续控制任务上提升学习效率与最终策略性能。
conclusion: 残差动作建模为视觉到连续控制动作映射提供了一种更易学习的范式。
---

## Abstract
Learning control policy from continuous action space by visual observations is a fundamental and challenging task in reinforcement learning (RL). An essential problem is how to accurately map the high-dimensional images to the optimal actions by the policy network. Traditional decision-making modules output actions solely based on the current observation, while the distributions of optimal actions are dependent on specific tasks and cannot be known priorly, which increases the learning difficulty. To make the learning easier, we analyze the action characteristics in several control tasks, and propose Reinforcement Learning with Residual Action (ResAct) to explicitly model the adjustments of actions based on the differences between adjacent observations, rather than learning actions directly from observations. The method just redefines the output of the policy network, and doesn’t introduce any prior assumption to constrain or simplify the vanilla control problem. Extensive experiments on DeepMind Control Suite and CARLA demonstrate that the method could improve different RL baselines significantly, and achieve state-of-the-art performance.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Visual Reinforcement Learning with Residual Action" (ResAct), organized according to 8 specific points. Let me analyze the paper carefully and produce a comprehensive summary.

Let me extract key information from the paper:

1. Core problem: Mapping high-dimensional images to continuous actions in visual RL is difficult because action distributions are task-dependent and unknown.

2. Method: ResAct has two components:
   - RAL (Residual Action Learning): Policy network outputs residual action δa instead of action a, then a = tanh(a_{t-1} + δa_t)
   - ODL (Observation Difference Learning): Two structurally identical but independently parameterized CNNs encode adjacent observations, subtract feature maps, then compress via FC + LayerNorm

3. Experiments: DMControl (6 common tasks + 5 hard tasks from Flare), CARLA driving

4. Resources: Not explicitly mentioned in the paper text I have

5. Number of experiments: Many - DMControl 6 tasks at 100K and 500K, DMControl 5 hard tasks at 500K and 1M, CARLA, ablations on RAL/ODL, feature dimension compression, attention maps, 5 seeds

6. Conclusions: ResAct achieves SOTA, improves different baselines, improves sample efficiency and stability

7. Strengths: Novel perspective, simplicity (no new hyperparameters), modular, general, SOTA performance

8. Weaknesses: Doesn't mention computational resources, methods like momentum contrast were tried but worse - might want more analysis, limited to off-policy SAC

Let me write a comprehensive summary in Chinese.</think>

# 论文总结：基于残差动作的视觉强化学习（ResAct）

## 1. 核心问题与研究动机

- **问题**：在视觉强化学习（vision-based RL）中，策略网络需要将高维图像观测映射到连续动作空间中的最优动作。由于最优动作分布具有任务依赖性，无法预先获知，传统"基于当前观测直接输出动作"的决策模式显著增加了学习难度，导致基于像素的 RL 在样本效率和最终性能上仍与基于状态（state-based）的 RL 存在明显差距。
- **核心观察（动机依据）**：
  - **动作平滑性**：作者定义 *Mean Action Distance (MAD)*（相邻动作的欧氏距离均值）作为度量。通过在 CARLA 和 DMControl 上统计发现，**MAD 越低的算法性能越好**，说明平滑的相邻动作调整对学习有利。
  - **残差动作分布简单**：以 state-based SAC 训练的策略近似最优策略，比较动作与残差动作的分布。动作分布零散、范围广；而**残差动作近似服从以零为中心的正态分布**，结构简单，更易探索。
  - **观测差异与残差动作的关联性**：通过 t-SNE 可视化潜空间，从"相邻观测的表示差"映射到"残差动作"比从"单帧观测"映射到"动作"更直接、紧凑。

## 2. 方法论

ResAct 由两个轻量、即插即用的模块组成，**不引入任何额外超参数**，仅重新定义了策略网络的输出和编码器结构。

### 2.1 残差动作学习（Residual Action Learning, RAL）

- **核心思想**：不再让策略网络直接输出动作 $a_t$，而是联合输入当前观测的表示 $z_t$ 与上一时刻动作 $a_{t-1}$，输出 **残差动作** $\delta a_t$。最终动作由 $a_t = \tanh(a_{t-1} + \delta a_t)$ 给出。
- **关键含义**：
  - 网络初始化权重小 → 输出 $\delta a_t \approx 0$ → 与"残差动作集中分布在零附近"的先验高度一致 → 训练初期获得更平滑的梯度。
  - 不强制约束动作分布：在需要剧烈变化的场景，仍可学习到大残差 → **不损害理论上最优性**（区别于对策略做正则化或奖励工程的方法）。

### 2.2 观测差异学习（Observation Difference Learning, ODL）

- **结构**：两个**结构相同但参数独立**的 CNN 分别对 $o_t$ 与 $o_{t-1}$ 编码，得到 $c \times h \times w$ 特征图，做差后送入 FC + LayerNorm，压缩为定长特征向量 $z_t$。
- **目的**：去除相邻观测间的冗余信息、保留动态变化信息，为 RAL 提供更紧凑的表征。
- **消融过的设计选择**：作者实验过共享参数或 MoCo 风格的动量更新，效果均不如双独立 CNN（差异在附录 B）。

### 2.3 算法流程（推断阶段伪代码）

1. $F_{\text{obs}} = f_{\text{convs}}(o_t)$， $F_{\text{prev}} = f_{\text{prev\_convs}}(o_{t-1})$（ODL）
2. $z_t = \text{LayerNorm}(f_{\text{FC}}(F_{\text{obs}} - F_{\text{prev}}))$
3. $\delta a_t \sim \pi_\theta(\cdot | z_t, a_{t-1})$（RAL）
4. $a_t = \tanh(a_{t-1} + \delta a_t)$
5. 与环境交互得到 $o_{t+1}$。

### 2.4 与已有工作的差异

- 与 Shen 等 (2020)、Mysore 等 (2021) 等通过**正则化或奖励塑造**强加平滑约束的方法不同：ResAct 改变学习范式而非约束策略。
- 与 Johannink 等 (2019)、Zeng 等 (2020) 的"残差 RL"不同：后者残差是相对于一个**基础控制策略**（来自物理先验或示教）；而 ResAct 的残差是相对于**时间维度的前一时刻动作**。
- 与 Shang 等 (2021) Flare 的差异：Flare 在单帧上做差以提取时序信息；ODL 用堆叠帧做差以适配残差动作学习。

## 3. 实验设计

### 数据集 / 场景

- **DMControl（DeepMind Control Suite）**：
  - 6 个常用任务（Cartpole Swingup、Reacher Easy、Cheetah Run、Walker Walk、Finger Spin、Ball-in-cup Catch），分别在 **100K 与 500K 环境步**下评估。
  - **5 个困难任务**（取自 Flare 设定：Quadruped Walk、Pendulum Swingup、Hopper Hop、Finger Turn Hard、Walker Run），在 **500K 与 1M 环境步**下评估。
- **CARLA 自动驾驶**：Town04 数字 8 形公路，1000 步内尽量行驶且不碰撞，**100K 训练步**评测。

### 对比方法（baselines / SOTA）

- 作为基线验证通用性的：**Pixel SAC、DeepMDP、RAD、DeepRAD**（作者自组的最强基线 = DeepMDP + RAD）。
- DMControl 比较对象：**CURL、SVEA、PlayVirtual、MLR、PSRL、TACO、MaDi** 等。
- CARLA 比较对象：**Pixel SAC、CURL、RAD、DrQ、SVEA、Flare、ISO-Dream、DeepMDP、TACO、MaDi、DeepRAD**。
- 每个实验使用 **5 个随机种子**，报告均值 ± 标准差。

## 4. 资源与算力

- **论文正文中没有给出具体算力信息**（GPU 型号、数量、单次训练耗时等均未注明）。
- 在致谢中仅提到计算支持来自"鹏城云脑"（Pengcheng Cloudbrain）这一超算平台，**未列出具体硬件规模或训练时长**。
- 代码开源地址：https://github.com/LiuZhenxian123/ResAct。

## 5. 实验数量与充分性

- **DMControl 6 任务 × 2 时间点 × 多基线（SAC/DeepMDP/RAD/DeepRAD）**：验证通用性。
- **DMControl 6 任务 × 100K/500K × 8 个 SOTA 方法**：验证 SOTA 性能。
- **DMControl 5 困难任务 × 2 时间点 × 5 个方法**：在仍有像素–状态性能差距的更难任务上验证提升。
- **CARLA 全驾驶实验 × 11 个方法对比**：含 episode reward、行驶距离、碰撞强度、平均转向/制动幅度等多个指标。
- **消融实验**：
  - 在 CARLA 上逐步叠加 RAL 与 ODL，验证各模块贡献（Fig.4(a)）。
  - **ODL 表征压缩极限实验**：逐级压缩特征维度，比较 ResAct 与 DeepRAD 的鲁棒性（Fig.4(b)）。
  - **空间注意力可视化**：DMControl 4 任务 + CARLA，对比 DeepRAD 与 ResAct 的注意力是否聚焦于运动区域（Fig.5）。
- **附录中还有**：人类行为模式相关性、t-SNE 可视化、动作分布对比、超参数/实验设置等。
- **充分性评价**：实验覆盖较广（3 个 benchmark × 多种基线 × 多时间点 × 多种子实验），并辅以注意力可视化、定量统计量（MAD、动作/残差分布）从多个角度支撑结论。**唯一明显不足**：缺少消融仅"去掉 RAL 但保留 ODL"或"去掉 ODL 但保留 RAL"的拆分报告（附录有但正文叙述较少）；以及缺少与最新更复杂方法（如 Dreamer 系列、基于 Transformer 的方法）的对比。

## 6. 主要结论与发现

- ResAct 在 **DMControl 6 个常用任务**的 100K / 500K 步设置中，**5/6 任务样本效率 SOTA、4/6 任务最终性能 SOTA**，且**收敛稳定性显著优于基线**（标准差更低）。
- 在 **DMControl 5 个困难任务**的 1M 步设置中，4/5 任务第一，且平均得分超过 Flare、TACO、MaDi、DeepRAD 等。
- 在 **CARLA 驾驶**任务中，奖励提升 ~43%，行驶距离提升 ~54%，平均转向和制动幅度大幅下降，验证了"动作更平滑"的实际效益。
- **关键洞察**：相邻观测的差异比单帧观测更适合预测残差动作；残差动作的先验分布（接近零）天然契合网络初始化，从而降低学习难度。
- 提出未来工作：将 ResAct 拓展到基于模型的框架，以及从该新视角进一步探索策略学习。

## 7. 优点与亮点

- **方法简洁优雅**：仅重新定义策略输出（动作→残差）和编码器（拼接→差分），**不引入任何超参数**，对 SAC 等主流算法可"即插即用"。
- **理论与直觉统一**：没有施加显式约束，因此 **不损害 RL 理论最优性**，避免了正则化类方法在突发场景下的失效风险。
- **通用性强**：在 Pixel SAC、DeepMDP、RAD、DeepRAD 四个差异较大的基线上一致提升，体现了方法对底层算法的兼容性。
- **稳定且高效的收敛**：在多个 benchmark 上**标准差显著降低**，对训练稳定性敏感的实际部署具有吸引力。
- **完整的实证支撑**：不仅有 SOTA 数字，还有 MAD、动作分布、t-SNE、注意力图等多维度定量/定性证据。
- **连接人类行为模式**：附录中将残差动作学习与人类连续操控行为的相似性进行了讨论，提升可解释性。

## 8. 不足与局限

- **算力/训练细节缺失**：未披露具体 GPU 型号、数量和单次训练时长，**复现成本难以评估**。
- **算法局限性**：
  - 仅在 off-policy SAC 上验证，未在 PPO、模型类方法（如 Dreamer）或基于 Transformer 的策略上检验。
  - 依赖"上一时刻动作"作为输入 → 在 **多智能体或异步执行等场景下时间步对齐要求更严**，可能限制适用性。
  - RAL 将前一步动作送入网络，会使策略对动作历史产生依赖，**对通信延迟、动作截断（clipped action）** 等鲁棒性问题未深入讨论。
- **实验覆盖不足**：
  - 与最新 SOTA（如 DreamerV3、TD-MPC、SAC-X 系列）的直接对比缺失。
  - 困难任务上 Walker Run 仍非最佳，说明在极端动态场景下仍有失败案例。
  - CARLA 仅一个场景（Town04 figure-8），其他城市场景、恶劣天气、行人交互等未覆盖。
- **先验假设的边界**：作者承认"残差动作均值为零的正态分布"在极端突发场景下会失效（此时退化到与原始 RL 类似），但未提供检测或量化这种"灾难性失败"概率的实验。
- **潜在偏差风险**：
  - 基线 DeepRAD 由作者自行组合（DeepMDP + RAD），可能在调参中对齐有利。
  - 注意力图仅展示少量示例，缺乏定量统计（如 IoU、显著性指标）。
  - 标准差较小可能也来自 5 个种子的样本量有限。

（完）
