---
title: Multi-fingered Hand Grasps with Visuo-Tactile Fusion via Multi-Agent Deep Reinforcement Learning
title_zh: 基于多智能体深度强化学习与视觉-触觉融合的多指手抓取
authors: "Peida Jia, Xuanheng Li, Tianqiang Zhu, Rina Wu, Xiangbo Lin, Yi Sun"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33599/35754"
tags: ["query:rob-il"]
score: 5.0
evidence: 多指手视觉-触觉融合的深度强化学习抓取
tldr: 针对高自由度多指手在接触丰富抓取任务中动作空间维度高、难以控制的问题，本文将手腕、手臂和每根手指建模为独立智能体，提出基于手指级的多智能体深度强化学习方法。方法先利用单智能体强化学习引导整手到达可行的接近方向与距离，再通过视觉-触觉融合与神经科学启发的奖励机制完成多指精细抓取。实验表明该策略在多种物体上实现了更稳定、更具泛化性的灵巧抓取。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33599/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 836, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33599/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1747, \"height\": 447, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33599/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1649, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33599/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1659, \"height\": 838, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33599/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 877, \"height\": 98, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33599/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1588, \"height\": 607, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33599/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1658, \"height\": 393, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33599/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 812, \"height\": 98, \"label\": \"Table\"}]"
motivation: 多指手自由度极高，传统整体控制难以完成接触丰富的灵巧抓取任务。
method: 将手腕、手臂和每根手指视为独立智能体，融合视觉与触觉信息分阶段完成接近与精细抓取。
result: 在多种物体上实现了更稳定和更具泛化性的多指灵巧抓取。
conclusion: 为高自由度灵巧手的接触丰富操作提供了一种可扩展的强化学习控制方案。
---

## Abstract
Humans achieve contact-rich dexterous grasping through the synergy of visual and tactile information. However, the high-dimensional action space of high DoF multi-fingered hands poses significant challenges to this operation. In this study, we address this complexity by controlling the robotic hand at the reduced dimensional level of individual fingers instead of the entire hand, and develop a finger-based multi-agent deep reinforcement learning strategy by regarding the wrist, arm, and each finger of the hand as intelligent agents. We commence by applying a single-agent reinforcement learning algorithm to guide the whole hand to reach the feasible approaching direction and distance to the object. Then, we develop neuroscience-inspired visuo-tactile fusion networks to train multiple agents to control their assigned fingers by effectively leveraging visual and tactile feedback. This enables dynamic and collaborative adjustments of finger-object interactions, ultimately achieving precise contact with specific areas of the objects. The grasping results on 8 objects show that our approach can achieve stable and compliant grasps. To the best of our knowledge, this is the first work that employs a finger-based multi-agent reinforcement learning approach to control the dexterous grasping process under the guidance of both visual and tactile feedback.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Multi-fingered Hand Grasps with Visuo-Tactile Fusion via Multi-Agent Deep Reinforcement Learning" following a specific structure with 8 points. Let me carefully analyze the paper and organize the content.

The paper is from AAAI-25, proposes VT-MAGIC scheme for dexterous grasping with visuo-tactile fusion using multi-agent DRL. Let me extract the key details:

1. Core problem: High-DoF multi-fingered hand grasping with contact-rich manipulation is challenging due to high-dimensional action space
2. Method: Two-phase approach (approaching + grasping), 7 agents (arm, wrist, 5 fingers), MADDPG with neuroscience-inspired visuo-tactile fusion network using self-attention and cross-attention
3. Experiments: MuJoCo simulator, 8 objects (ball, watch, rubber duck, elephant toy, light bulb, water bottle, flashlight, hammer)
4. Baselines: SAPG, SAPPO, VT-SAPG, VT-SAPPO
5. Hardware: Intel i9-10920 CPU, NVIDIA RTX 3090
6. Metrics: Success rate, stability (max relative displacement under shaking)
7. Ablation: VT-MAGIC-NF (no tactile), VT-MAGIC-MLP (conventional MLP fusion)
8. Results: 86% success rate vs 70-75% for baselines

Let me write a detailed Chinese summary.
</think>
# 论文总结：基于多智能体深度强化学习与视觉-触觉融合的多指手抓取

## 1. 核心问题与研究背景

- **核心问题**：高自由度（24 个手部关节 + 6 自由度机械臂）多指灵巧手的接触丰富型抓取任务，动作空间维度极高、接触点复杂，难以实现稳定且柔顺的抓取规划。
- **两大挑战**：
  - 手-物交互的复杂度随关节数和接触点数量指数级增长，传统的运动规划与基于模型的方法难以适应环境变化和新任务；
  - 触觉反馈稀疏而视觉信息稠密，二者模态差异大，难以有效融合。现有基于深度强化学习（DRL）的多指抓取方案多依赖序列示教数据（VR/视频采集成本高），且大多只针对二指夹爪。
- **研究目标**：仅依靠**单帧静态参考抓取**，通过视觉-触觉融合的多智能体强化学习，实现稳定、柔顺、泛化性强的五指灵巧抓取。

## 2. 方法论：VT-MAGIC 方案

### 2.1 整体框架
提出 **VT-MAGIC（Visuo-Tactile based Multi-Agent Grasp with Intra-Collaboration）** 层级化方案，将抓取过程分为两个阶段：
- **接近阶段（Approaching Phase）**：用单智能体强化学习（NPG）引导整手到达参考抓取位姿上方约 5 cm 的预抓取位姿，规避碰撞。
- **抓取阶段（Grasping Phase）**：将 **5 根手指、手腕、手臂** 视为 7 个独立智能体，采用 **MADDPG** 进行多智能体协作训练。

### 2.2 状态、动作、奖励设计
- **接近阶段**：
  - 状态：6 臂关节 + 24 手关节角度、掌心"抓取点"到预抓取位姿距离、5 指指尖到目标位姿距离；
  - 动作：6 臂关节 + 24 手关节力矩（臂仅平移，不旋转）；
  - 奖励：$R_{all} = R_{position} + R_{pose}$，其中 $R_{position} = -\alpha_1 d_{palm} + \alpha_2 T_t$（$T_t$ 为保持时间步数累积项），$R_{pose} = -\sum_{i=1}^{5}\beta_i d_i$；
  - 终止条件：步数上限或 $T_t > 30$。
- **抓取阶段**：
  - 状态：手指智能体含自身+邻指关节角、触觉接触力大小、指尖到参考点距离；手腕/臂仅含关节角与"抓取点"距离；
  - 动作：按部位分解，臂 6 维、手腕 2 维、拇指 5 维、食/中/无名指各 4 维、小指 5 维；
  - 奖励：每根手指独立奖励 $R_{thumb}=R_{index}=\dots=R_{little}=f_i(d_i)$（距离二次函数），手腕/臂奖励 $R_{arm}=R_{wrist}=-\alpha_3 d_6 + R_l$，$R_l=-\alpha_5 h^2 + \alpha_6 h + \alpha_7$ 鼓励将物体抬升至目标高度。

### 2.3 神经科学启发的视觉-触觉融合网络
- 设计灵感：模拟人类大脑 **双层加工机制**（初级皮层 + 次级皮层）。
- **自注意力机制**：对视觉和触觉原始输入分别提取特征（类似初级皮层处理）；
- **跨注意力机制**：融合两种模态特征（类似次级皮层多感觉整合）；
- 输出经全连接层映射为各智能体的动作；手腕/臂智能体无触觉输入，仅用全连接层。
- 训练时每个智能体配备 **Main-Actor + Target-Actor** 与 **Main-Critic + Target-Critic**，Critic 接收全局状态和所有智能体动作，输出 Q 值，通过软更新（$\tau$ 平滑）同步目标网络。

### 2.4 算法流程简述
1. 接近阶段训练整手到达预抓取位姿；
2. 以预抓取位姿为起点进入抓取阶段；
3. 各智能体观测局部状态 + 邻指状态，Actor 输出关节力矩；
4. 与环境交互后，将 $(s_i, a_i, R_i, s_i')$ 存入回放池；
5. 采样批次用 MADDPG 更新 Critic（最小化 Q 预测与目标 $Q_T$ 的 MSE）和 Actor（最大化 Q 值）；
6. 软更新 Target 网络：$\theta_T = (1-\tau)\theta_T + \tau \theta$。

## 3. 实验设计

- **仿真平台**：MuJoCo 物理仿真器；手为 24 关节灵巧手，臂为 6-DoF 机械臂。
- **测试物体**：8 种代表性物体——球、手表、橡皮鸭、大象玩具、灯泡、水瓶、手电筒、锤子。
- **基线方法**（5 个，全部基于单智能体 DRL，与 VT-MAGIC 在相同奖励与静态参考抓取下公平对比）：
  - **SAPG**：DAPG 改写版（去序列示教，使用单帧参考抓取 + 自定义奖励）；
  - **SAPPO**：单智能体 PPO；
  - **VT-SAPG / VT-SAPPO**：在 SAPG/SAPPO 基础上加入视觉+触觉信息（无 MADRL 结构）；
  - **VT-MAGIC**（本文）。
- **消融实验**：
  - **VT-MAGIC-NF**：去掉触觉反馈（无 Force）；
  - **VT-MAGIC-MLP**：用传统 MLP 替代神经科学启发的融合网络。
- **评估指标**：
  - **成功率**：能否将物体提升 10 cm 并保持 5 s，每物 50 次试验求平均；
  - **稳定性检测**：抓稳后沿 x/y/z 轴正反施加外力引发晃动，测量物体与手之间最大相对位移；水瓶因重量体积特殊，记录晃动次数作为稳定性指标。

## 4. 资源与算力

- 文中明确给出的硬件配置：
  - **CPU**：Intel Core i9-10920 @ 3.50 GHz × 24 核；
  - **GPU**：NVIDIA GeForce RTX 3090；
  - 仅 1 张 GPU，未给出训练时长、迭代次数的具体数值。
- **未明确说明**：单次训练总耗时、各阶段训练步数、模型参数量等。

## 5. 实验数量与充分性

- **对比实验**：5 个方法 × 8 个物体 × 50 次试验/物体 = 2000 次抓取评估，覆盖率高；
- **稳定性测试**：5 个方法 × 8 物体 × 3 方向（x/y/z）扰动；
- **消融实验**：2 个变体（VT-MAGIC-NF、VT-MAGIC-MLP）× 8 物体 × 3 方向 + 成功率对比；
- **充分性评价**：
  - 物体形状、质量、尺寸具有多样性（球/手表/不规则玩具/细长手电筒/重水瓶/异形锤等），能反映方法泛化能力；
  - 消融实验从"模态贡献"和"融合网络结构"两个维度展开，论证较充分；
  - 局限：仅在 MuJoCo 仿真中验证，未涉及真实机器人实验；未给出统计显著性检验（如多次随机种子下的均值±方差）；触觉建模为简化"力大小标量"，未涉及真实触觉传感器的空间分布信息。

## 6. 主要结论与发现

- **整体性能**：VT-MAGIC 平均成功率 **86%**，显著优于 VT-SAPG（75%）、VT-SAPPO（74%）、SAPG（70%）、SAPPO（72%）。
- **稳定性**：在 x/y/z 三方向扰动下，VT-MAGIC 几乎不发生物体跌落，相对位移普遍小于所有基线；水瓶在 VT-MAGIC 下可承受 6 次晃动（z 轴），远超其他方法的 0-1 次。
- **抓取姿态**：定性结果显示 VT-MAGIC 手指能"包裹"物体（如手指环抱鸭子），而基线方法往往只有指尖接触，姿态不够自然。
- **触觉贡献**：去掉触觉（VT-MAGIC-NF）后成功率降至 82%，稳定性显著下降，说明触觉对防止"过度施力撞倒物体"至关重要。
- **融合网络贡献**：将自+跨注意力融合网络替换为简单 MLP（VT-MAGIC-MLP）后，成功率降至 77%，稳定性也下降，说明精细的多模态融合结构是必要的。
- **机制有效性**：手指级多智能体分解有效降低了单智能体需控制的关节数，提升了内部协作与可探索性。

## 7. 优点与亮点

- **首创性**：第一个将基于手指的多智能体强化学习与视觉-触觉融合结合用于五指灵巧抓取的工作；
- **结构化分解**：将 24 关节+6 臂的高维动作空间按解剖学分解为 7 个智能体，显著降低探索复杂度，且符合人手协同运动模式；
- **仿生融合网络**：自注意力+跨注意力的双层设计在原理上具备可解释性（对应大脑初级/次级皮层），且实验验证优于 MLP；
- **去示教依赖**：仅需一张静态参考抓取图，避免昂贵的 VR/视频示教采集；
- **基线设计完整**：对比了 DRL 算法（PG vs PPO）、是否融合触觉、是否多智能体，多维度验证每个组件的贡献；
- **奖励设计层次化**：手指奖励强调指尖定位，臂/腕奖励强调"抓取点对齐 + 抬升高度"，与任务目标契合。

## 8. 不足与局限

- **仅仿真验证**：未在真实机器人平台上做 sim-to-real 迁移，触觉与视觉的真实噪声、延迟、传感器漂移均未涉及；
- **触觉建模简化**：将触觉处理为"标量接触力大小"，未利用真实触觉传感器（如 GelSight/DIGIT）的空间图像信息，与"neuroscience-inspired"宣称的细粒度多模态融合存在差距；
- **视觉信息粒度有限**：未明确视觉输入是 RGB 图像、深度图还是物体位姿/语义特征；输入维度信息缺失，复现性受影响；
- **参考抓取依赖**：仍需一张静态参考抓取作为先验，对完全未知物体的零样本泛化能力未评估；
- **稳定性测试场景简单**：扰动仅为沿坐标轴正反方向施加的"震荡"，未涉及更复杂的外力模式（如扭矩、连续轨迹扰动、协作干扰）；
- **统计充分性不足**：未报告多次随机种子下的均值与标准差，缺少显著性检验；
- **计算开销未量化**：未报告训练总时长、收敛步数、单次推理延迟等，难以评估实际部署成本；
- **物体集合有限**：8 个物体虽形状多样但数量仍偏少，未覆盖易碎/可变形/铰接物体等更具挑战性的场景；
- **应用限制**：方法针对单手抓取静态桌面物体，未涉及动态目标抓取、双手协作、复杂工具使用等更高级灵巧操作任务；作者在结论中也明确将 sim-to-real 列为下一步工作。

（完）
