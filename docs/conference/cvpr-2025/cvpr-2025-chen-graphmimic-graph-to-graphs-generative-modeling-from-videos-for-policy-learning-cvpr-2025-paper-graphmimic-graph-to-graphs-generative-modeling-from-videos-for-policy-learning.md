---
title: "GraphMimic: Graph-to-Graphs Generative Modeling from Videos for Policy Learning"
title_zh: GraphMimic：基于图到图视频生成建模的机器人策略学习
authors: "Chen, Guangyan, Cui, Te, Wang, Meiling, Yang, Chengcai, Hu, Mengxiao, Lu, Haoyang, Mu, Yao, Peng, Zicai, Zhou, Tianxing, Jiang, Xinran, Yang, Yi, Yue, Yufeng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_GraphMimic_Graph-to-Graphs_Generative_Modeling_from_Videos_for_Policy_Learning_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过视频生成式建模实现机器人技能的模仿学习
tldr: 动作标注的机器人示教数据采集成本高，限制了模仿学习的扩展。本文提出 GraphMimic，将视频帧抽象为对象与动作顶点构成图结构，通过图到图的生成建模进行预训练，学习可供下游模仿学习使用的状态表征。该方法显著降低了对昂贵动作标注数据的依赖。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1636, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 867, \"height\": 541, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1788, \"height\": 358, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1775, \"height\": 897, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1789, \"height\": 307, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1773, \"height\": 802, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 883, \"height\": 455, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 861, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-graphmimic-graph-to-graphs-generative-modeling-from-videos-for-policy-learning-cvpr-2025-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 884, \"height\": 455, \"label\": \"Table\"}]"
motivation: 动作标注机器人数据稀缺，限制了模仿学习的规模化。
method: 将视频帧抽象为图结构，进行图到图的生成式预训练。
result: 获得了可迁移的机器人状态表征，支持下游模仿学习。
conclusion: 为利用大规模无标注视频进行模仿学习提供了新范式。
---

## Abstract
Learning from demonstration is a powerful method for robotic skill acquisition. However, the significant expense of collecting such action-labeled robot data presents a major bottleneck. Video data, a rich data source encompassing diverse behavioral and physical knowledge, emerges as a promising alternative. In this paper, we present GraphMimic, a novel paradigm that leverages video data via graph-to-graphs generative modeling, which pre-trains models to generate future graphs conditioned on the graph within a video frame. Specifically, GraphMimic abstracts video frames into object and visual action vertices, and constructs graphs for state representations. The graph generative modeling network then effectively models internal structures and spatial relationships within the constructed graphs, aiming to generate future graphs. The generated graphs serve as conditions for the control policy, mapping to robot actions. Our concise approach captures important spatial relations and enhances future graph generation accuracy, enabling the acquisition of robust policies from limited action-labeled data. Furthermore, the transferable graph representations facilitate the effective learning of manipulation skills from cross-embodiment videos. Our experiments exhibit that GraphMimic achieves superior performance using merely 20% action-labeled data. Moreover, our method outperforms the state-of-the-art method by over 17% and 23% in simulation and real-world experiments, and delivers improvements of over 33% in cross-embodiment transfer experiments.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "GraphMimic: Graph-to-Graphs Generative Modeling from Videos for Policy Learning" organized into 8 specific sections. Let me analyze the paper carefully and structure my response accordingly.

Let me go through each section:

1. Core problem and overall meaning - The paper addresses the bottleneck of action-labeled robot data for imitation learning, proposes using video data via graph-to-graphs generative modeling.

2. Methodology - GraphMimic constructs graphs from video frames with object vertices and visual action vertices, uses property-aware graph generative modeling with hierarchical architecture, predicts future graphs to guide policy learning.

3. Experimental design - LIBERO benchmark (130 tasks across 5 suites), real-world experiments (12 tasks), cross-embodiment transfers (robot-to-robot with Franka→UR, human-to-robot), compared with BC, R3M, UniPi, ATM.

4. Resources/compute - The paper doesn't explicitly mention GPU models or training time. I'll note this.

5. Number of experiments and adequacy - Quite extensive: 140+ tasks total, multiple ablations (state representations, visual action representations, object representations, hierarchical modeling, object property estimation), 3 seeds.

6. Main conclusions - Method outperforms SOTA by 17%+ in simulation, 23%+ in real-world, 33%+ in cross-embodiment transfer, works with only 20% labeled data.

7. Strengths - Novel graph-based approach, cross-embodiment transferability, sparse data efficiency.

8. Limitations - Tracking models struggle with low-texture objects during large motions; appendix reference.

Let me write this in detailed Chinese with Markdown structure.</think>

# 论文总结：GraphMimic——基于图到图视频生成建模的机器人策略学习

---

## 1. 核心问题与整体含义（研究动机与背景）

- **核心瓶颈**：机器人模仿学习（Learning from Demonstration）的规模化受限于**动作标注机器人数据**的高昂采集成本，演示收集需要大量人力投入。
- **替代数据源**：视频数据（尤其是人类视频或异构机器人视频）含有丰富的行为与物理知识，是一种低成本、易获取的替代方案。
- **现有方法的不足**：
  - 视觉表征预训练（R3M、MVP 等）仅描述当前状态、**忽略过渡动力学**；
  - 视频生成或轨迹流生成方法（UniPi、ATM）在像素空间直接建模，**忽略了物体内部结构、物体间空间关系以及物体-执行器之间的关系**；
  - 强化学习奖励学习方法面临显著的 sim-to-real 差距。
- **核心问题**：能否将视频预训练形式化建模为 **graph-to-graphs 生成式建模**，从而在有限的动作标注数据下学习到鲁棒的机器人策略，并支持**跨本体迁移**？

---

## 2. 方法论

### 2.1 总体框架（GraphMimic）
两步流程：
1. **预训练阶段**：在大量无标注视频上预训练一个 graph-to-graphs 生成模型，预测未来图序列；
2. **模仿学习阶段**：将预测得到的未来图作为条件，与当前观测、本体感受信号一起输入策略网络，预测机器人动作。

### 2.2 关键技术模块

#### (1) Action-informed Transferable Graph（动作感知可迁移图）
- **物体顶点**：由 VLM 根据任务描述和初始图像解析出任务相关物体集合 Ω，再用 Grounded-SAM 分割并在掩膜内均匀采样得到。
- **视觉动作顶点（Visual Action Vertices）**：将本体抽象为**关键交互点**——人体视频中即**指尖位置**（fingertips），既编码功能交互又弱化本体特异性。
- **图构建**：按预设距离阈值 d 在顶点对之间建立**双向边**，仅保留距离小于 d 的连通关系，得到当前帧的图表示 $G_t = (V_t, E_t)$。

#### (2) Property-aware Graph Generative Modeling（属性感知图生成建模）

**目标**：给定当前观测 $o_t$、历史观测 $o_{t-H:t}$ 与语言指令 $\ell$，预测未来 $F_G$ 步图序列 $G_{t:t+F_G}$。

- **物体属性估计**：从历史图序列中抽取物体子图，使用在线跟踪算法（如 TAPIR/Cotracker）建立顶点对应；用 GNN 提取物体级特征 $\bar{Z}_{\Omega_i}^t$，再通过 **LSTM** 建模长时依赖，得到属性特征 $\phi_{\Omega_i}^t = \text{MLP}(h_t)$。该属性特征将作为额外输入融合到图中。
- **层级图建模（Hierarchical Graph）**：在原始图 $G_t$ 基础上，对动作与物体顶点集分别做 K-means 聚类，为每个簇添加一个**全局顶点**（root global vertex，位置为簇内顶点均值的质心），并构建三类边：
  - $E_{L2R}$：叶子→根（自底向上信息聚合）；
  - $E_{R2L}$：根→叶子（自顶向下信息传播）；
  - $E_{R2R}$：根与根之间的全连接有向边。
  最终层级图为 $G_t^h = \{V_t \cup V_t^g,\; E_t \cup E_t^{L2R} \cup E_t^{R2L} \cup E_t^{R2R}\}$。
- **图生成**：将图嵌入 $Z_t^h$、图像嵌入 $Z_t^o$、BERT 文本嵌入 $Z_\ell$ 一起送入 Transformer 生成器，再通过两层 MLP 头预测顶点位置 $x_{t:t+F_G}$（边的集合按距离阈值 d 由位置关系隐式确定）；损失为预测位置与 Cotracker 跟踪得到的真值位置之间的 MSE。

#### (3) Graph-guided Policy Learning（图引导的策略学习）
- **状态编码器**：将未来图 $G_{t:t+F_G}$、当前观测 $o_t$、本体感受 $\rho_t$ 通过各自的编码器（GNN、ResNet、MLP）映射到共享嵌入空间，加上可学习的位置嵌入与 CLS token，经 Transformer 块自注意力聚合成状态表示 $s_t$。
- **动作头**：将 CLS token $s_t$ 与图 token 拼接得到策略条件 $Z_t^c$，通过 MLP 输出未来 $F_a$ 步动作序列 $a_{t:t+F_a}$，使用 MSE 损失训练。

---

## 3. 实验设计

### 3.1 数据集与场景
- **LIBERO Benchmark（仿真）**：包含 130 个语言条件操作任务，分为 5 个子套件——Spatial、Object、Goal、Long、90。每任务收集 50 条无标注机器人视频 + 10 条动作标注演示用于训练。
- **真实世界**：12 个真实任务（开关抽屉、堆叠方块、开烤箱、水果放盘、按键、杯子互倒、扫桌、推箱、叠布、折布放好、捋绳……），每任务 50 条无标注视频 + 10 条动作标注演示。
- **跨本体迁移**：
  - **Robot-to-Robot**：Franka → UR（不同形态机械臂）；
  - **Human-to-Robot**：人手 → Franka 机械臂。

### 3.2 对比方法
- **BC（Behavior Cloning）**：纯动作标注数据训练，作为基线（包括 Full-Trainset 与 10-demos 版本）；
- **R3M**：对比式视频-语言视觉预训练（Ego4D 权重在 LIBERO 视频上微调）；
- **UniPi**：文本条件视频扩散 + 逆动力学模型；
- **ATM**：轨迹点跟踪生成 + 轨迹引导策略；
- **Diffusion Policy、Im2Flow2Act**：附录中补充对比。

---

## 4. 资源与算力

- 论文**正文未明确披露**所使用的 GPU 型号、数量或训练时长等算力细节。
- 仅在附录中讨论了跟踪模型在低纹理物体大运动下的局限，间接提示其依赖较先进的点跟踪器（如 CoTracker3）。
- 关于算法复杂度、各模块训练开销的具体数值（如小时数、显存占用等）**未给出**。

---

## 5. 实验数量与充分性

- **任务规模**：合计跨越 140+ 个任务（仿真 130 + 真实世界 12）。
- **多次随机种子**：仿真实验以 3 个种子取均值，减小随机性。
- **消融实验**：5 项系统性消融（详见下表）：

| 消融维度 | 关键发现 |
| --- | --- |
| 状态表示（State representations） | 网格采样+图 < 关键点+流 < 关键点+图（本文方式最优） |
| 视觉动作表示 | 无动作 < 末端执行器采样 < 交互关键点（本文方式最优） |
| 物体表示 | 仅操作物（空间关系不足） < 全部物体（动静不平衡） < 任务相关（本文方式最优） |
| 层级建模 | 局部连接 < 全局连接 < 层级架构（本文方式最优） |
| 物体属性估计 | 无估计 < 仅图无 LSTM < Graph+LSTM（本文方式最优） |

- **公平性**：所有方法均使用相同的标注数据量（除 BC-Full-Trainset 用作上限参考）；同时比较了**仅用 20% 数据（2 条/任务）** 的 Ours 版本以验证数据效率。
- **客观性**：消融在 robot-to-robot 转移场景上评估，避免在同域内过拟合。
- 总体而言，**实验设计较为充分**，覆盖了仿真、真实、跨本体三大场景，并给出 5 项系统性消融；但缺少对**物体类别分布、显著性差异统计检验**等的报告。

---

## 6. 主要结论与发现

- **数据高效**：仅用 20% 的动作标注数据（2 条/任务）即可超过使用 5 倍数据训练的 ATM/UniPi 等基线；
- **仿真提升**：在 LIBERO 全部 5 个子套件上均超过 SOTA，10-demos 设置下平均提升 **>17%**；
- **真实世界提升**：12 个真实任务总体成功率 0.76 vs ATM 的 0.53，相对提升 **>23%**；
- **跨本体提升**：
  - Robot-to-Robot：UR 臂（用 Franka 视频预训练）整体成功率显著高于基线，**提升 >33%**；
  - Human-to-Robot：人手视频预训练下真实任务总体成功率 0.64 vs ATM 的 0.27。
- **关键设计要点**：
  - **图表示的层级结构** + **属性估计**对捕获不同物体的不同动力学（刚体、布料、流体等）至关重要；
  - **可迁移图表示**通过"物体动力学 + 关键交互点"的解耦，使跨本体迁移成为可能。

---

## 7. 优点（亮点）

- **范式新颖**：首次将视频预训练形式化为 graph-to-graphs 生成式建模，统一了物体动力学建模与策略条件的供给。
- **稀疏性归纳偏置**：图结构天然编码空间关系，相比像素/光流更具结构化、可解释性强。
- **跨本体能力强**：通过"功能交互点（fingertips）"抽象本体，使人类视频可被机械臂直接复用。
- **数据效率极高**：仅 2 条/任务的标注即可超过 50 条的全量 BC，可见预训练价值显著。
- **公平基线对比**：与 4 个有代表性的视频预训练方法（BC、R3M、UniPi、ATM）在同等数据设置下对比；附录进一步加入 DP、Im2Flow2Act。
- **实验规模大**：140+ 任务、3 个随机种子、5 类系统性消融。
- **训练开销可承受**：相较于 UniPi 的视频扩散模型，GraphMimic 的图预测规模小很多，更易部署。

---

## 8. 不足与局限

- **依赖跟踪器质量**：作者在 Limitations 中明确指出，"low-texture"（低纹理）物体在大运动场景下，当前 SOTA 跟踪器（如 CoTracker3）仍会失效，**直接影响训练数据质量与图预测精度**。
- **图构建误差传播**：基于阈值的边构建（距离 d 的设定）较为朴素，缺少自适应机制；阈值选择对结果敏感性未做充分讨论。
- **属性估计依赖历史长度 H、预测步数 F_G、F_a 等超参的调参细节**：未在正文给出充分讨论或敏感性分析。
- **仿真到真实差距**：尽管在真实实验中表现良好，但**真实任务数（12）** 相对仿真（130）仍较少，且实验复杂度有限（未见多个机器人、复杂长时序任务的深入评测）。
- **人类视频场景受限**：人类视频中指尖检测依赖手部姿态估计模型，对**遮挡、域外视角**的鲁棒性未做实验评估。
- **缺乏统计显著性检验**：仅报告均值与标准差，未使用配对 t 检验或置信区间分析，难以判断若干数据集上提升是否稳定（如 Libero-Long 的 ±0.03 与 ATM 的 ±0.15 区间重叠）。
- **未给出算力/能耗信息**：复现成本难估计，对工业落地参考价值有限。
- **未与最新大规模视频预训练方法**（例如大规模 V-JEPA 类视频自监督表征）**进行直接比较**，对"图建模相对于大规模视频表征是否真的更优"的边界讨论略显单薄。

---

（完）
