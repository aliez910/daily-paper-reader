---
title: "Learning to See and Act: Task-Aware Virtual View Exploration for Robotic Manipulation"
title_zh: 学看与学动：面向机器人操纵的任务感知虚拟视角探索
authors: "Bai, Yongjie, Wang, Zhouxia, Liu, Yang, Luo, Kaijun, Wen, Yifan, Dai, Mingtong, Chen, Weixing, Chen, Ziliang, Liu, Lingbo, Li, Guanbin, Lin, Liang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Bai_Learning_to_See_and_Act_Task-Aware_Virtual_View_Exploration_for_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向多任务机器人操纵的VLA模型任务感知虚拟视角探索
tldr: 本文针对现有VLA模型依赖固定相机与共享视觉编码器在遮挡和跨任务迁移下性能受限的问题，提出任务感知虚拟视角探索框架TVVE。该方法从重建场景中动态选择任务相关虚拟视角进行重渲染，并引入任务感知混合专家视觉编码器缓解任务间干扰。该工作提升了多任务机器人操纵中视觉到动作映射的鲁棒性与泛化能力。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 834, \"height\": 384, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1532, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 783, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1708, \"height\": 630, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1815, \"height\": 739, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1808, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1804, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 870, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 750, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 907, \"height\": 175, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-bai-learning-to-see-and-act-task-aware-virtual-view-exploration-for-cvpr-2026-paper/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 909, \"height\": 233, \"label\": \"Table\"}]"
motivation: 固定相机与共享视觉编码器限制了VLA模型在遮挡和跨任务场景下的性能。
method: 提出TVVE动态选择任务相关虚拟视角进行重渲染，并设计任务感知混合专家视觉编码器。
result: 在多任务操纵中显著提升了VLA模型的鲁棒性与跨任务迁移能力。
conclusion: 为通用视觉-动作模型在复杂多任务操纵中的视觉表征提供了新思路。
---

## Abstract
Recent vision-language-action (VLA) models for multi-task robot manipulation often rely on fixed camera setups and shared visual encoders, which limit their performance under occlusions and during cross-task transfer. To address these challenges, we propose Task-aware Virtual View Exploration (TVVE), a framework that learns to select task-relevant virtual camera viewpoints and dynamically re-render observations from a reconstructed scene representation using the selected viewpoints. To enable efficient view selection, we train an exploration policy in a pseudo-environment. In addition, we introduce a Task-aware Mixture-of-Experts (TaskMoE) visual encoder that routes visual features to task-specialized experts, mitigating interference in multi-task learning. To evaluate robustness under distribution shifts, we construct RLBench-OG, an out-of-distribution benchmark with visual perturbations and camera pose variations. Experiments on RLBench and RLBench-OG demonstrate that TVVE achieves higher success rates than strong baselines, while real-robot experiments further confirm its robustness to visual disturbances and unseen instructions. Code and visualizations are available at: https://hcplab-sysu.github.io/TAVP.

---

## 论文详细总结（自动生成）

<think>The user wants a structured Chinese summary of the paper "Learning to See and Act: Task-Aware Virtual View Exploration for Robotic Manipulation". I need to organize the response according to 8 specific points, using Markdown formatting with hierarchical headers and bullet points. Let me carefully analyze the paper content and produce a comprehensive summary.

Let me go through each point:

1. **Core problem and motivation**: The paper addresses limitations of VLA models in multi-task robot manipulation - fixed camera setups and shared visual encoders lead to issues with occlusions and cross-task transfer.

2. **Methodology**: TVVE framework with two main components:
   - MVEP (Multi-Viewpoint Exploration Policy): Uses RL with PPO in a pseudo-environment to learn viewpoint selection from point clouds
   - TaskMoE (Task-aware Mixture-of-Experts): Routes features using instruction+vision cues via FiLM, with decoupled gating (NG gates for NJ tasks)
   - Training strategy: 3 stages (fixed-view training, MVEP refinement via PPO, end-to-end fine-tuning)
   - Uses Gaussian distribution sampling for camera poses with reparameterization trick
   - Camera pose parameterized as 5D vectors using look-at model

3. **Experiments**: 
   - RLBench (multi-view 18 tasks, single-view 10 tasks)
   - RLBench-OG (new OOD benchmark with occlusion and generalization suites)
   - Real robots: Franka Research 3 and Dobot Nova 2 (5 tasks)
   - Compared with: C2F-ARM-BC, PerAct, HiveFormer, PolarNet, RVT, Act3D, 3D Diffuser Actor, RVT-2, ARP, GNFactor, Diffusion Policy

4. **Resources**: 
   - 4 NVIDIA RTX A800 GPUs for training
   - Single A800 for testing
   - K=3 viewpoints, NG=8 gates, NE=16 experts, top-2 selected

5. **Experiment count and sufficiency**:
   - Main results on RLBench multi-view (18 tasks), single-view (10 tasks)
   - RLBench-OG with 8 perturbation settings
   - Real robot experiments (2 platforms, 5 tasks)
   - Ablation studies: TaskMoE effectiveness, MVEP effectiveness (fixed/random viewpoints), K and r hyperparameters
   - Very comprehensive

6. **Main conclusions**:
   - TVVE achieves 86.6% avg success rate on RLBench multi-view (5% improvement over ARP)
   - 67.0% on RLBench-OG
   - 88.0% on Dobot, 78.0% on Franka in real world
   - Dynamic viewpoint exploration and task-aware MoE both contribute

7. **Strengths**:
   - Novel combination of dynamic view planning + task-aware MoE
   - Pseudo-environment for RL training without expensive physical interaction
   - Comprehensive benchmark (RLBench-OG)
   - Multi-platform real-world validation
   - Extensive ablations

8. **Limitations**:
   - Multi-view re-rendering increases inference latency
   - Reliance on accurate global point clouds - struggles with reflective/transparent objects
   - Limited to RGB-D inputs
   - Future work: multi-sensor integration and domain adaptation

Let me also note specific results:
- RLBench multi-view: TVVE 86.6% vs ARP 81.6% vs RVT-2 81.4%
- RLBench single-view: TVVE 83.2% vs RVT-2 82.7%
- RLBench-OG: TVVE 67.0% vs RVT-2 64.5% vs ARP 63.7% vs DP 23.8%
- Dobot: TVVE 88.0% vs DP 68.0%
- Franka: TVVE 78.0% vs ARP 72.0% vs DP 58.0%

Let me write this out in Chinese now with proper Markdown structure.</think>

# 论文总结：Task-Aware Virtual View Exploration (TVVE) for Robotic Manipulation

## 1. 核心问题与研究动机

- **关键痛点**：现有 Vision-Language-Action (VLA) 模型（如 OpenVLA、π0、RVT-2 等）在多任务机器人操纵中存在两大固有缺陷：
  - **固定视角受限**：依赖单视角或若干固定相机（front / shoulder / wrist），在杂乱、动态或末端执行器运动场景下，目标物体或夹爪易被遮挡，导致观测不完整、动作预测失效。
  - **共享编码器的任务干扰**：RVT、RVT-2 等基于语言条件的 Transformer 使用共享 Multi-View Transformer (MVT) 编码视觉特征，对视觉与语义差异较大的任务（如 "pick apple" 与 "open drawer"）会出现严重的特征纠缠，限制跨任务泛化能力。
- **核心目标**：让机器人既"会看"（主动选择信息量最大的视角）又"会动"（在不同任务中提取任务专属特征），提升遮挡鲁棒性与多任务迁移能力。

---

## 2. 方法论

### 2.1 整体框架 (TVVE)
- **输入**：语言指令 + 多视角 RGB-D + 末端本体感知 (joints + gripper) + Task ID。
- **流程**：
  1. 将 RGB-D 图像融合为**全局点云**（世界坐标系）。
  2. 一条**橙色分支**做 Coarse Grounding（沿用 RVT-2 思路），预测区域中心并对点云做裁剪/缩放。
  3. 一条**绿色分支**：将点云送入 **MVEP** 预测 K 个最优相机姿态参数，并据此**重渲染 2D 观测**。
  4. 重渲染图像经 TaskMoE-MVT 处理后进入 **Fine Grounding**，最终由升级版 ARP 自回归动作策略产生 7-DoF 动作 (位置 / 四元数旋转 / 夹爪开合 / 碰撞标志)。

### 2.2 Task-aware Mixture-of-Experts (TaskMoE)
- **路由输入**：Task ID + 指令 + 视觉特征。
- **跨模态融合**：指令与视觉特征经 cross-attention 得到上下文特征，再与 Task ID 通过 **FiLM 层** 自适应融合。
- **解耦门控**：设计 $N_G$ 个门共享给 $N_J$ 个任务 ($N_G < N_J$)——相似任务（如 "Task 1/2" 都涉及开抽屉）共用同一门、激活不同专家；语义差异大的任务（如 "Task 3"）走独立门。
- **专家池**：$N_E$ 个共享专家，每次只激活 top-k（论文中 $N_G=8, N_E=16$，top-2）。

### 2.3 Multi-Viewpoint Exploration Policy (MVEP)
- **输入**：聚合的全局点云 $P \in \mathbb{R}^{N \times 3}$ 与对应 RGB 特征 $F_{img} \in \mathbb{R}^{N \times 3}$，拼接为 $X \in \mathbb{R}^{N \times 6}$。
- **相机姿态参数化**（look-at 模型）：每个视角 $p_i = (\theta_i, \phi_i, r_i, \theta_i^{up}, \phi_i^{up}) \in \mathbb{R}^5$，相机始终指向原点。
- **可微采样**：MVEP 输出每个视角的均值 $\mu_i$ 与 log 标准差 $\log \sigma_i$，通过重参数化技巧 $\tilde{p}_i = \mu_i + \sigma_i \odot \epsilon_i$ 采样；用 sigmoid 约束到合法球坐标范围（$\theta, \theta^{up} \in [0,\pi]$，$\phi, \phi^{up} \in [0,2\pi]$，$r \in [r_{min}, r_{max}]$）。
- **奖励设计**（PPO）：
  - $r_0$：任务损失差（参考模型 $L_{ref}$ 与 TVVE $L_{TVVE}$ 之差）作为性能下界信号；
  - $r_1$：Fine Grounding 热力图熵的负均值（鼓励高置信度预测）；
  - $r_2$：相机位置之间的平均成对余弦距离（鼓励视角多样性）；
  - 加权聚合时使用 Welford 在线归一化 + 裁剪到 $[-10, 10]$ 保证稳定性。

### 2.4 三阶段训练策略
- **Stage 1**：以 front / left / top 三固定视角训练 TVVE，损失 $L_{s1} = L_{hc} + L_{hf} + L_{rot} + L_{gri} + L_{col}$（热力图 / 旋转 / 夹爪 / 碰撞）。
- **Stage 2**：冻结其他模块，仅用 PPO 在**伪环境**（无需真实仿真交互）中优化 MVEP，伪环境用 Stage 1 模型提供奖励信号。
- **Stage 3**：冻结 MVEP，对整体网络进行监督微调以协调"see-and-act"能力。

---

## 3. 实验设计

### 3.1 数据集 / 场景
- **RLBench**（CoppeliaSim 仿真，Franka Panda 7-DoF）：
  - 多视角设定：18 个任务，每个任务 2–60 个变体，使用全部 4 个相机（front / left-shoulder / right-shoulder / wrist）。
  - 单视角设定：10 个任务，仅用 front RGB-D 相机。
- **RLBench-OG（本文新构建的 OOD 基准）**：
  - **Occlusion Suite**：模拟遮挡（添加遮挡物或旋转物体），分"训练+测试都遮挡"与"仅训练时无遮挡、零样本测试遮挡"两种配置；
  - **Generalization Suite**：零样本评估在灯光、桌面颜色 / 纹理、背景颜色 / 纹理、干扰物、相机姿态变化下的表现；10 个任务，每任务 50 条训练轨迹，每任务 25 条评估轨迹。
- **真实机器人**：
  - **Franka Research 3**：单一第三人称 RGB-D 相机（ORBBEC Femto Bolt）；
  - **Dobot Nova 2**：三个 Intel RealSense（overhead D435i、front D455、wrist D405）；
  - 5 个任务：Pick Grape、Stack Bowls、Push Buttons、Collect Fruits、Put Item In Drawer，每任务 50 条专家演示，仅保留关键帧。

### 3.2 对比方法
- 涵盖 **10+ 基线**：Diffusion Policy、C2F-ARM-BC、PerAct、HiveFormer、PolarNet、GNFactor、RVT、Act3D、3D Diffuser Actor、RVT-2、ARP 等。

---

## 4. 资源与算力

- **训练硬件**：4 块 NVIDIA RTX A800 GPU。
- **测试硬件**：单块 NVIDIA RTX A800 GPU。
- **超参**：$K=3$ 视角、$N_G=8$ 门、$N_E=16$ 专家、top-2 激活。
- **未明确披露**：训练时长（epoch 数 / wall-clock time）、数据规模、伪环境实现细节（仅称在补充材料中）。

---

## 5. 实验数量与充分性

- **仿真主结果**：RLBench 多视角 18 任务 + 单视角 10 任务（每任务三独立运行报告 mean ± std），共 ~28 任务对比。
- **鲁棒性测试**：RLBench-OG 含 8 类扰动设定（Occlusion 1/2 + 5 种泛化条件）。
- **真实机器人**：2 个平台 × 5 个任务 × 每任务 10 次试验。
- **消融实验**（表 5-7）：
  - TaskMoE 开关（w/o TaskMoE）；
  - MVEP 替换为 Fixed viewpoints / Random viewpoints；
  - 视角数量 $K \in \{2,3,4\}$ 与径向范围 $r$ 的搜索；
  - TaskMoE 在已见 / 未见任务上的迁移能力。
- **充分性评价**：实验覆盖较全面（仿真 + 真实 + OOD + 消融），多次独立重复，使用标准差反映稳定性；但真实机器人试验数偏少（每任务仅 10 次），可能存在统计噪声。

---

## 6. 主要结论与发现

- **RLBench 多视角**：TVVE 平均成功率 **86.6%**，平均排名 2.17，超过此前最佳 ARP (81.6%)、RVT-2 (81.4%)；Insert Peg 任务从 65.6% → 98.0%，Sort Shape 从 36.0% → 62.0%。
- **RLBench 单视角**：TVVE 达 **83.2%**，超过 RVT-2 (82.7%)。
- **RLBench-OG**：TVVE 平均 **67.0%**（rank 1.4），优于 RVT-2 (64.5%)、ARP (63.7%)；遮挡 1/2 分别领先 ARP +2.0 / +5.4，背景纹理变化 +6.2，相机姿态变化 +3.5。
- **真实机器人**：
  - Dobot：TVVE **88.0%** vs Diffusion Policy 68.0%（Push Buttons +30%，Stack Bowls +20%）；
  - Franka：TVVE **78.0%** vs ARP 72.0%、DP 58.0%。
- **关键发现**：
  1. 动态视角规划能有效缓解遮挡并减少碰撞；
  2. 解耦的 task-aware MoE 显著减轻多任务干扰，对已见 / 未见任务均带来正向迁移；
  3. 视角数 $K$ 与径向范围 $r$ 对性能敏感，过大范围反而略降表现（48.8%）。

---

## 7. 优点 / 亮点

- **方法新颖**：首次将"动态虚拟视角探索"与"任务感知 MoE 视觉编码"系统整合到 VLA 框架中，呼应 "Learning to See and Act" 主题。
- **伪环境 RL 设计**：MVEP 用 Stage-1 固定视角模型作为奖励源，避免真实环境交互，训练更高效。
- **解耦门控 (NG < NJ)**：使相似任务共享门、异质任务分离门，有利于发现潜在任务聚类，提升对未见任务的迁移能力。
- **新基准 RLBench-OG**：覆盖遮挡 + 5 类视觉扰动，对未来鲁棒性研究有参考意义。
- **跨平台验证**：同时在 Franka 与 Dobot 两种硬件上测试，验证泛化性。
- **消融充分**：TaskMoE、MVEP、$K$、$r$ 多维度实验，论证各组件贡献。

---

## 8. 不足与局限

- **推理延迟**：多视角重渲染会增加计算开销，作者明确承认。
- **依赖全局点云质量**：对反射、透明物体（如玻璃、镜面）重建失败的情形表现受限。
- **真实机器人样本量较小**：每任务仅 10 次试验，统计显著性有限，且未见对真实环境下的 OOD 鲁棒性系统评测（仅给出补充材料提及）。
- **伪环境依赖**：MVEP 的奖励信号完全由 Stage-1 模型提供，可能继承其偏差；若 Stage-1 失败模式集中，MVEP 会强化同样的盲区。
- **专家路由可解释性**：FiLM 融合 + top-k 路由虽然有效，但对路由决策缺乏诊断分析（例如未可视化门激活矩阵、专家功能分布）。
- **未涉及**：跨 embodiment 迁移、与 LLM/VLM 预训练结合、长时序任务规划等延伸方向。
- **算力披露不足**：训练时长、伪环境实现细节未在正文给出。

（完）
