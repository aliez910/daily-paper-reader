---
title: "VidBot: Learning Generalizable 3D Actions from In-the-Wild 2D Human Videos for Zero-Shot Robotic Manipulation"
title_zh: VidBot：从野外二维人类视频中学习可泛化三维动作以实现零样本机器人操作
authors: "Chen, Hanzhi, Sun, Boyang, Zhang, Anran, Pollefeys, Marc, Leutenegger, Stefan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_VidBot_Learning_Generalizable_3D_Actions_from_In-the-Wild_2D_Human_Videos_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 从人类视频中学习可泛化的机器人操作能力
tldr: 物理机器人学习难以规模化，而互联网中已存在海量相关人类视频数据。本文提出VidBot框架，通过从野外单目RGB人类视频中学习三维可供性表征，实现机器人零样本操作。该方法从视频中提取显式三维手部轨迹表示，将人类操作知识迁移到机器人。该工作为面向复杂任务的视觉模仿学习提供了可扩展的解决路径，对缩小机器人学习数据缺口具有重要意义。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1798, \"height\": 655, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 776, \"height\": 456, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1802, \"height\": 595, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 832, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1705, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 827, \"height\": 442, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-vidbot-learning-generalizable-3d-actions-from-in-the-wild-2d-human-videos-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 252, \"label\": \"Table\"}]"
motivation: 物理机器人学习难以规模化，亟需利用互联网中丰富的野外人类视频数据。
method: 从单目RGB人类视频中提取三维手部轨迹等可供性表征以指导机器人操作。
result: 实现了基于野外人类视频数据的机器人零样本操作能力。
conclusion: VidBot为视觉模仿学习提供了可扩展的视频数据利用方案。
---

## Abstract
Future robots are envisioned as versatile systems capable of performing a variety of household tasks. The big question remains, how can we bridge the embodiment gap while minimizing physical robot learning, which fundamentally does not scale well. We argue that learning from in-the-wild human videos offers a promising solution for robotic manipulation tasks, as vast amounts of relevant data already exist on the internet. In this work, we present VidBot, a framework enabling zero-shot robotic manipulation using learned 3D affordance from in-the-wild monocular RGB-only human videos. VidBot leverages a pipeline to extract explicit representations from them, namely 3D hand trajectories from videos, combining a depth foundation model with structure-from-motion techniques to reconstruct temporally consistent, metric-scale 3D affordance representations agnostic to embodiments. We introduce a coarse-to-fine affordance learning model that first identifies coarse actions from the pixel space and then generates fine-grained interaction trajectories with a diffusion model, conditioned on coarse actions and guided by test-time constraints for context-aware interaction planning, enabling substantial generalization to novel scenes and embodiments. Extensive experiments demonstrate the efficacy of VidBot, which significantly outperforms counterparts across 13 manipulation tasks in zero-shot settings and can be seamlessly deployed across robot systems in real-world environments. VidBot paves the way for leveraging everyday human videos to make robot learning more scalable.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "VidBot: Learning Generalizable 3D Actions from In-the-Wild 2D Human Videos for Zero-Shot Robotic Manipulation" following a specific structured outline. Let me analyze the paper carefully and produce a comprehensive summary.

Let me organize my thoughts on each section:

1. Core problem and motivation: The paper addresses the scalability challenge of physical robot learning. While robots need to perform diverse household tasks, collecting robot demonstrations is costly and doesn't scale well due to the combinatorial explosion of embodiments, tasks, and environments. The authors propose learning from in-the-wild human videos as a scalable alternative.

2. Method:
- 3D Affordance Acquisition pipeline: Uses SfM + metric depth foundation model to extract 3D hand trajectories from monocular RGB videos
- Consistent pose optimization with global scale correction
- Coarse-to-Fine Affordance Learning:
  - Coarse stage: Predicts goal points and contact points in pixel space using heatmaps
  - Fine stage: Uses diffusion model with 1D U-Net to generate fine-grained interaction trajectories
  - Test-time cost guidance: multi-goal, collision avoidance, contact normal guidance
- Loss functions for training

3. Experiments:
- IsaacGym simulator with 13 tasks from FrankaKitchen, PartManip, ManiSkill
- Baselines: GAPartNet, Where2Act, Octo, VRB, GFlow
- Ablation studies on 6 tasks
- Downstream applications: visual goal-reaching, exploration
- Real robot experiments on Hello Robot Stretch 3 and Boston Dynamics Spot

4. Resources/compute: The paper doesn't explicitly mention GPU models, quantities, or training time. I should note this.

5. Experimental thoroughness:
- 13 manipulation tasks in simulator (3 viewpoints × 5 trajectories = 15 trials per task per model)
- 6 tasks for ablation
- Downstream applications studies
- 55 real-world trials
- Quite thorough but real-world trials could be more extensive

6. Main conclusions: Outperforms baselines by ~20% success rate, achieves 88.2% average success, 80% on real robots

7. Strengths:
- Only uses RGB-only in-the-wild videos
- Embodiment-agnostic representation
- Cost-guided diffusion for test-time flexibility
- Coarse-to-fine design
- Cross-embodiment deployment

8. Limitations:
- Data quality depends on depth foundation model and SfM accuracy
- Cannot handle precise tasks like unscrewing caps
- Real-world experiments limited

Now I'll write this in Chinese with proper Markdown formatting.</think>

# VidBot 论文总结

## 一、核心问题与研究背景

- **机器人学习规模化难题**：现代机器人执行多样化家务任务（如开关柜门、推抽屉、拿物品）的能力受限于物理演示数据的高昂采集成本。模仿学习（IL）范式严重依赖专家遥操演示，但随着任务、物体、环境、机器人形态的组合爆炸，数据扩展困难。
- **野外人类视频的潜力**：互联网已存在海量第一人称人类视频，涵盖丰富场景和任务，理论上可作为机器人学习的可扩展数据源。但现有方法存在局限：
  - 需要静态相机、深度传感器或动作捕捉系统，限制在实验室环境；
  - 仅学习视觉表征或2D像素级动作，无法直接部署到机器人；
  - 依赖新环境下的人工遥操演示做微调。
- **关键科学问题**：(1) 如何从原始RGB人类视频中提取三维可操作知识？(2) 如何将提取的知识零样本迁移到新场景与新机器人形态？
- **研究目标**：提出 VidBot 框架，从野外单目RGB视频中学习**与具体形态无关**（embodiment-agnostic）的三维可供性（3D affordance）表示，实现机器人零样本操作。

## 二、方法论

### 2.1 三维可供性获取管线（从视频到3D轨迹）

- **数据准备**：输入单目RGB视频序列 $\{\hat{I}_0,...,\hat{I}_T\}$ 与语言描述 $l$。
  - 利用 COLMAP/SfM 估计相机内参 $K$、逐帧尺度未知位姿 $\{T^{WC}_i\}$ 与稀疏路标点 $\{W^l_j\}$；
  - 使用 Metric3D v2 等**度量深度基础模型**预测稠密深度 $\{\hat{D}_i\}$；
  - 用 100DOH/手-物检测器 + SAM 分割模型获取手部掩膜 $\{M^h_i\}$ 与接触物体掩膜 $\{M^o_i\}$；
  - 用视频修复模型去除手部，得到"无手"帧 $\{\tilde{I}_i\}$。
- **全局尺度校正**：通过将 SfM 稀疏路标反投影到图像平面与度量深度对齐，优化全局尺度因子 $s_g$，公式为：
  $$\min_{s_g} \sum_{i,j} \tilde{M}_i[u_{ij}] \|\hat{D}_i[u_{ij}] - s_g \, d(T^{-1}_{WC_i} W^l_j)\|_2^2$$
- **逐帧位姿与尺度精修**：选取共视度最高的参考帧 $k$，最小化跨视角三维点重投影误差，确保深度一致性。
- **可供性提取**：在精修后的相机坐标下，取每帧手部中心点 → 第一帧坐标系下得到交互轨迹 $\hat{\tau}$；从第一帧手部点均匀下采样得**接触点** $\hat{c}$，从最后一帧手部点采样得**目标点** $\hat{g}$。
- **数据来源**：Epic-Kitchens-100 + EpicFields 提供的 SfM 结果。

### 2.2 粗到细可供性学习模型

模型分为两个阶段，整体架构如图3所示。

#### 粗粒度阶段（Coarse Affordance Prediction）

- 由两个 Hourglass 网络组成：$\pi^{goal}_c$ 预测目标点，$\pi^{cont}_c$ 预测接触点。
- 输入：经开放集检测器裁剪后的物体 RGB-D 图像、全局上下文图像、语言指令。
- $\pi^{goal}_c$：
  - 目标点图像用物体中位深度填充（因目标点通常处于自由空间）；
  - 通过 ViT 提取视觉特征，RoI Pooling 获得物体中心特征 $z^o_{goal}$，MLP 编码 bbox 位置特征 $z^b_{goal}$，冻结 CLIP 提取语言特征 $z_l$；
  - Perceiver 模块做 cross-attention 融合全局上下文与条件特征；
  - 同时回归目标深度 $\hat{D}_g$ 与逐像素目标概率热图。
- $\pi^{cont}_c$：类似结构，但接触点深度无需预测（位于物体表面）。
- 利用相机内参、热图采样像素与对应深度，将接触点 $c$ 与目标点 $g$ 提升到三维。

#### 细粒度阶段（Fine Affordance Prediction）

- 基于条件扩散模型（DDPM），参数化为 1D U-Net（仿 Trace and Pace）。
- 条件嵌入 $o = \{PE(g), PE(c), Proj(z_l), z^o_{fine}\}$，$PE$ 为位置编码。
- 输入含 TSDF 体素特征：3D U-Net 编码体素化 TSDF $U$，用三线性插值得到轨迹每个 waypoint 的空间特征 $f_k$，与噪声化轨迹 $\tau^k$ 拼接为 $x^k = \{\tau^k, f^k\}$。
- 网络直接预测去噪轨迹 $\bar{\tau}^0$（而非噪声预测）：
  $$\bar{\tau}^0 = \pi_f(x^k, PE(k), o)$$

#### 测试时代价引导（Cost-Guided Trajectory Generation）

为提高对新形态/新场景的泛化，引入三类可微代价函数，在反向去噪过程中通过梯度扰动输出：

- **多目标代价** $J_{goal} = \min_{g_n \in g} \|g_n - \bar{\tau}^0_H\|_2^2$：避免单一目标点偏移导致错误；
- **碰撞避免代价** $J_{collide}$：对手部和物体表面采样 $N_p$ 个点，查询 TSDF 图 $U$ 的截断有符号距离，鼓励轨迹点位于自由空间（TSDF 截断距离取负值时累加）；
- **接触法向代价** $J_{normal}$：使轨迹切向对齐于接触点的法向量（正向或反向）。

总代价 $J = \lambda_g J_{goal} + \lambda_c J_{collide} + \lambda_n J_{normal}$，在每步去噪时更新：
$$\tau^0 = \bar{\tau}^0 - \Sigma_k \nabla_{\tau^k} J$$
最终代价 $J$ 可作为启发式用于最优轨迹选择。

### 2.3 训练损失

- 粗粒度阶段：将提取的真值 $\hat{g}, \hat{c}$ 投影到图像，拟合高斯混合模型生成真值热图 $\hat{H}_g, \hat{H}_c$。
  - $L_g = \text{BCE}(\hat{H}_g, H_g) + \lambda_d \|\hat{D}_g - D_g\|_2^2 + \lambda_v L_v$
  - $L_c = \text{BCE}(\hat{H}_c, H_c) + \lambda_v L_v$
  - $L_v$ 为辅助向量场回归损失。
- 细粒度阶段：$L_f = \mathbb{E}_{\epsilon,k}[\|\hat{\tau} - \bar{\tau}^0\|_2^2]$

## 三、实验设计

### 3.1 数据集与场景

- **数据集**：Epic-Kitchens-100 + EpicFields（用作可供性训练监督）。
- **模拟器**：NVIDIA IsaacGym。
- **基准任务**：13 个家务任务，源自 FrankaKitchen、PartManip、ManiSkill 三个基准，涵盖开合柜门、微波炉、洗碗机、抽屉滑动、拾取水壶/罐头/纸箱、揭盖等动作原语。
- **评估协议**：每个任务3个视角，每视角5条轨迹，共15次/任务；成功标准为物体自由度超过阈值且不与场景碰撞。

### 3.2 对比方法

| 基线 | 训练数据来源 | 特点 |
|------|------|------|
| GAPartNet | 模拟器交互 | 部件级可操作预测 |
| Where2Act | 模拟器交互 | 像素到动作的铰接物体交互 |
| Octo | 大规模遥操数据集+本文数据微调 | 通用机器人策略基础模型 |
| VRB | 人类视频（同本文数据源）| 2D像素级动作，作者用[42]策略提升到3D |
| GFlow | 人类视频（带真值深度、相机参数、物体位姿）| 通用流作为可供性 |
| **Ours** | 野外RGB-only人类视频 | 三维可供性 + 扩散 + 测试时引导 |

### 3.3 下游机器人学习任务

- **视觉目标到达**：智能体可访问物体目标配置图像，结合成功轨迹 buffer 替换目标点。
- **探索**：最大化环境变化的巧合成功率（coincidental success）。

### 3.4 真实机器人

- **机器人平台**：Hello Robot Stretch 3（移动操作机器人）与 Boston Dynamics Spot（四足机器人），均搭载 RGB-D 相机。
- **测试任务**：推抽屉、开柜门、取纸巾等家务任务。
- **环境**：3种不同的家居环境，共 **55 次试验**。

## 四、资源与算力

- 论文未明确披露具体的 GPU 型号、数量、训练时长或计算资源消耗。
- 仅可推断使用的关键预训练模型：Metric3D v2 / ZoeDepth（深度估计）、DINO/GroundingDINO（开放集检测）、SAM/EfficientSAM（分割）、CLIP（语言编码）、DINOv2（ViT 特征提取）。
- 模拟器使用 IsaacGym（GPU 加速物理仿真）。

## 五、实验数量与充分性

- **主对比实验**：13 任务 × 15 次试验 = 195 次/方法，6 种方法共约 1170 次模拟试验。
- **消融实验**：6 任务 × 5 个变体（粗粒度目标预测、多目标引导、法向引导、碰撞避免、代价启发式选择），含完整模型共 6 组配置 × 6 任务 × 15 次 ≈ 540 次。
- **下游应用**：6 任务的视觉目标到达与探索曲线对比。
- **真实机器人**：55 次试验，2 种机器人平台。
- **充分性评估**：
  - 任务覆盖面较广（开/关、推/拉、抓取），覆盖多种物体；
  - 与同样使用人类视频的 VRB、GFlow 直接对比，验证三维化的必要性；
  - 与模拟器训练（Where2Act、GAPartNet）和大规模遥操数据训练（Octo）对比，公平性较好；
  - 但**真实世界试验样本数（55 次）偏少**，统计显著性论证有限；
  - VRB 等基线使用本文模型预测接触点来标准化，**评测焦点偏向轨迹预测**而非完整端到端能力，可能对部分基线略不公平。

## 六、主要结论与发现

- 在 13 个模拟任务上取得 **88.2% 平均成功率**，比第二名（Octo，69.2%）高出近 20%。
- 相比同样用 Epic-Kitchens 训练的 VRB（2D），本文通过三维先验将成功率提升约 30%（88.2% vs 59.0%）。
- 真实机器人任务上达到 **80.0%** 成功率（55 次试验），在 Stretch 3 和 Spot 两类异构平台上均可部署，验证了形态无关特性。
- 消融研究的关键发现：
  - 粗粒度目标预测贡献最大（去掉后从 85.6% → 57.8%）；
  - 多目标引导贡献 12.3%；
  - 碰撞避免对抓取类便携物体贡献达 26.7%；
  - 代价启发式选择贡献 11.1%。
- 在视觉目标到达与探索两类下游 RL/IL 任务中均显著加速收敛并提高最终性能。

## 七、优点与亮点

- **数据源极简**：仅需野外单目 RGB 视频，无需深度相机、动作捕捉或遥操演示，是真正的"零样本、跨形态"迁移。
- **三维可供性显式建模**：通过 SfM + 度量深度的全局优化获得时间一致的米制尺度3D轨迹，相比 VRB 的2D像素动作更适合直接驱动机器人。
- **粗到细的分解**：高层语义（接触点/目标点）与低层轨迹分阶段预测，降低了直接生成高维动作的难度。
- **测试时代价引导**：将多目标、碰撞、法向等几何约束融入扩散采样过程，既保留数据先验又允许新形态适配，且代价值本身可作为轨迹排序启发式，是工程上很巧妙的设计。
- **跨平台部署**：同一模型在 Stretch 3 与 Spot 上均工作良好，展示了 embodiment-agnostic 表征的实用价值。
- **任务范围广**：涵盖开/关/推/拉/抓取等异构操作原语。

## 八、不足与局限

- **数据质量瓶颈**：作者明确指出，提取精度受限于深度基础模型与 SfM 管线的误差；当前管线对低纹理、快速运动、严重遮挡视频鲁棒性未知。
- **能力上限**：无法处理需要精细手指操作的任务（如拧瓶盖、按钮按压），目前主要面向抓取级（grasping-level）操作。
- **真实试验规模**：仅 55 次真实试验，且任务集中于抓取/开合抽屉类，未覆盖更复杂的多步骤长视域任务。
- **基线公平性争议**：为公平对比，作者用自身模型代替 VRB/GFlow 预测接触区域，使对比焦点窄化为"轨迹预测"而非完整可供性预测，可能掩盖基线在接触区域检测上的劣势。
- **管线工程复杂度高**：依赖 SfM、Metric3D、SAM、GroundingDINO、CLIP、DINOv2 等多个独立组件，端到端训练困难，任何上游模块失效都会传播。
- **缺乏算力披露**：未公开 GPU 类型/数量、训练时长、推理延迟等关键信息，**复现成本不可评估**。
- **伦理与安全考量**：真实机器人试验过程中潜在安全风险未讨论；人类视频数据集 Epic-Kitchens 涉及隐私，已通过既有数据许可使用，但本文未做专门讨论。

（完）
