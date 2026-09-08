---
title: "PointWorld: Scaling 3D World Models for In-The-Wild Robotic Manipulation"
title_zh: PointWorld：面向野外机器人操作的大规模三维世界模型
authors: "Huang, Wenlong, Chao, Yu-Wei, Mousavian, Arsalan, Liu, Ming-Yu, Fox, Dieter, Mo, Kaichun, Fei-Fei, Li"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Huang_PointWorld_Scaling_3D_World_Models_for_In-The-Wild_Robotic_Manipulation_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 大规模三维世界模型，统一动作表示以支持跨本体机器人操作
tldr: 机器人在执行前需要预测3D世界如何响应动作，这种能力对野外机器人操作至关重要。本文提出PointWorld，将动作表示为3D点流，使状态与动作在同一3D空间中统一。该模型基于RGB-D观测与底层动作命令预测逐像素三维位移，从而跨本体学习并支持野外操作策略的扩展。论文为机器人操作提供了几何接地的世界模型新范式。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1791, \"height\": 798, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 769, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 787, \"height\": 965, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1096, \"height\": 606, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 661, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 637, \"height\": 482, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-huang-pointworld-scaling-3d-world-models-for-in-the-wild-robotic-manipulation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1137, \"height\": 300, \"label\": \"Table\"}]"
motivation: 现有方法以本体特定空间表示动作，限制了跨本体学习与野外泛化能力。
method: 提出3D点流表示，将状态与动作统一在共享三维空间中预训练大规模世界模型。
result: 模型能够跨机器人本体预测物理一致的3D动态响应。
conclusion: 该工作为跨本体机器人操作策略提供了可扩展的几何接地世界模型。
---

## Abstract
Humans anticipate, from a glance and a contemplated action of their bodies, how the 3D world will respond, a capability that is equally vital for robotic manipulation. We introduce PointWorld, a large pre-trained 3D world model that unifies state and action in a shared 3D space as 3D point flows: given one or few RGB-D images and a sequence of low-level robot action commands, PointWorld forecasts per-pixel displacements in 3D that respond to the given actions. By representing actions as 3D point flows instead of embodiment-specific action spaces (e.g., joint positions), this formulation directly conditions on physical geometries of robots while seamlessly integrating learning across embodiments. To train our 3D world model, we curate a large-scale dataset spanning real and simulated robotic manipulation in open-world environments, enabled by recent advances in 3D vision and simulated environments, totaling about 2M trajectories and 500 hours across a single-arm Franka and a bimanual humanoid. Through rigorous, large-scale empirical studies of backbones, action representations, learning objectives, partial observability, data mixtures, domain transfers, and scaling, we distill design principles for large-scale 3D world modeling. With a real-time (0.1s) inference speed, PointWorld can be efficiently integrated in the model-predictive control (MPC) framework for manipulation. We demonstrate that a single pre-trained checkpoint enables a real-world Franka robot to perform rigid-body pushing, deformable and articulated object manipulation, and tool use, without requiring any demonstrations or post-training and all from a single image captured in-the-wild.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "PointWorld: Scaling 3D World Models for In-The-Wild Robotic Manipulation" based on the provided PDF extraction and metadata. I need to organize the summary according to 8 specific points, use Markdown formatting with hierarchical headings and bullet points, and end with "（完）".

Let me carefully analyze the paper content:

1. **Core problem**: World modeling for robotic manipulation in unstructured environments. Existing methods use embodiment-specific action spaces limiting cross-embodiment learning. Need to predict how 3D world responds to actions.

2. **Method**: 
   - POINT WORLD - 3D point flows as unified state-action representation
   - State: scene point cloud from RGB-D
   - Action: robot point flows from forward kinematics using URDF
   - Backbone: PTv3 (Point Transformer v3) with frozen DINOv3 features
   - Multi-step (chunked) prediction, H=10 steps
   - Training: movement weighting, uncertainty regularization, Huber loss
   - MPC integration with MPPI planner
   - Real-time inference (0.1s)

3. **Experiments**:
   - Datasets: DROID (real-world), BEHAVIOR-1K (simulation)
   - About 2M trajectories, 500 hours
   - Evaluated on DROID test set, BEHAVIOR-1K
   - Compared backbones: GBND, PointNet, PointNet++, SparseConv, Transformer, PTv3
   - Compared action representations: gripper point flows, full body, EEF pose, joint positions
   - Scaling experiments: model size 50M-1B, data 5%-100%
   - Generalization: in-domain, cross-domain, held-out real environments
   - Real robot tasks: pushing, deformable, articulated, tool use

4. **Resources/Compute**: Not explicitly mentioned in the paper. Need to note this.

5. **Number of experiments**: 
   - 5.1: Roadmap with backbones, objectives, features, model size
   - 5.2: Ablations on action representations, scaling
   - 5.3: Generalization and transfer (in-domain, cross-domain, held-out)
   - 5.4: Real robot experiments (8 tasks)
   - Multiple ablations mentioned
   - 40,000 robot trajectories with 10,000 point flows each for evaluation

6. **Main conclusions**:
   - PTv3 is effective and scalable backbone
   - Movement weighting, uncertainty regularization, Huber loss stabilize training
   - DINOv3 pretrained features help
   - Model and data scaling follow log-linear patterns
   - Gripper point flow actions balance effectiveness and efficiency
   - Generalizes well, transfers across domains
   - Single pre-trained checkpoint enables diverse manipulation tasks

7. **Strengths**:
   - Unified representation for state and action
   - Large-scale dataset curation with 3D annotations
   - Thorough empirical study of scaling
   - Real-time inference
   - Cross-embodiment transfer
   - Real robot demonstrations without finetuning

8. **Limitations**:
   - Real-to-sim and sim-to-real zero-shot transfer still challenging
   - Limited to 1-second prediction horizons
   - Compute resources not specified
   - Only Franka tested on real hardware (though bimanual humanoid in simulation)
   - Static scene assumption during forward pass
   - Task specification still requires manual GUI/clicking
   - Performance drop on noisy real-world data

Let me write this in a structured, comprehensive way in Chinese.
</think>
# PointWorld 论文总结

## 1. 核心问题与研究动机

- **研究背景**：人类能够从一瞥与一个"想象中的动作"出发，预见三维世界如何响应。这种"空间智能"对通用机器人操作同样关键。野外、非结构化环境下的世界建模（world modeling）是实现通用机器人操作的核心。
- **现有方法不足**：
  - 物理仿真器（如 MuJoCo）依赖手工建模，难以迁移到野外场景且 sim-to-real 差距大；
  - 学习型动力学模型常需对象性（objectness）、材料等先验，或要求完全可观测；
  - 大规模视频生成模型缺乏显式的动作条件化，物理一致性不足；
  - 已有动力学模型多以本体特定空间（如关节位置、末端位姿）表示动作，**难以跨本体学习与泛化**。
- **核心问题**：能否用一个统一的、与本体无关的表征，同时表达**状态**与**动作**，从而在野外、仅依靠少量 RGB-D 输入的条件下，预训练一个可扩展、可迁移的三维世界模型？

## 2. 方法论

### 2.1 核心思想
- **统一表征**：将"状态"和"动作"都表示为 **3D 点流（3D point flows）**。
  - 状态 = 由 RGB-D 反投影得到的全场景 3D 点云（去除机器人自身像素）；
  - 动作 = 由机器人 URDF 与关节配置经正向运动学采样得到夹爪（gripper）表面点随时间演化的点流序列。
- 这样的表征具有：
  - 强调几何交互（physical geometry）而非外观纹理；
  - 适用于部分可观测场景，无需场景重建、对象性或材料先验；
  - 可用稳定的 L2/Huber 回归损失训练，无需置换匹配；
  - 自然地实现跨本体（异构机械臂、双手、整体操作）学习。

### 2.2 关键技术细节
- **分块预测（chunked prediction）**：单次前向预测未来 H=10 步（每步 0.1s）的逐点位移：$F_\theta^H:(s_t,a_{t:t+H-1}) \to s_{t+1:t+H}$，减少推理次数、提高时序一致性。
- **网络结构**：
  - 场景点用冻结的 **DINOv3**（多层特征）投影到 2D 视图后提取特征；
  - 机器人点用时序 embedding 表征；
  - 两者拼接后送入 **PointTransformerV3 (PTv3)** 点云骨干网络；
  - 共享 MLP 头输出每个点在每一步的 3D 位移。
- **训练目标**（公式 1）：
  - 运动加权（movement weighting）$w_{k,i}$：使用基于真实位移范数的 sigmoid 软权重 $m_{k,i} = \sigma(\kappa(\delta_{k,i}-\tau))$ 放大运动点信号；
  - 不确定性正则化（aleatoric uncertainty）：对每个点预测 log-variance $s_{k,i}$，并用 Huber loss $\rho_\delta$ 拟合残差 $\hat P_{t+k,i} - P_{t+k,i}$；
  - 综合目标：$\sum_{k,i} w_{k,i}\left(\rho_\delta(\cdot)e^{-s_{k,i}} + s_{k,i}\right)$。
- **推理与控制**：单次 0.1s 实时推理，结合 **MPPI**（Model Predictive Path Integral）采样式规划器，对末端执行器 SE(3) 目标序列加 cubic-spline 噪声采样，累积任务代价 $c_{\text{task}}$（点级 L2 到目标）和控制代价 $c_{\text{ctrl}}$ 后指数加权更新。
- **任务目标指定**：通过 GUI 工具手动绘制目标点集（亦可由 VLM 提供），适用于刚性、可形变、铰接物体的统一表达。

## 3. 实验设计

### 3.1 数据集
- **DROID**（真实世界）：约 200 小时、约 60% 标注恢复率；用 FoundationStereo 重估计深度、VGGT+机器人网格对齐优化相机外参、CoTracker3 提供 2D 跟踪并升维 3D。
- **BEHAVIOR-1K (B1K)**（仿真）：约 1100 小时原始、过滤后仅保留有接触/有物体运动的轨迹，直接用仿真真值 3D 流。
- **合计**：~2M 条轨迹，约 500 小时，跨单臂 Franka、双手人形、整体/移动操作。
- **基准评测**：
  - 主指标：1 秒预测时域内运动点的逐点 L2 距离 `l2_mover`，辅以 `l2_static`；
  - 评测集约 40,000 条机器人轨迹、每条约 10,000 个点流，标准误 ≤ 1e-5 m；
  - 真实数据通过在测试集上单独训练的"专家"模型按置信度过滤掉 20% 不可靠点。

### 3.2 对比方法
- **骨干网络对比**：GBND（基线）、PointNet、PointNet++、SparseConv、Transformer、PTv3（50M/132M/411M/1B）；
- **动作表示对比**：仅夹爪点流（300–500 点/夹爪，论文方法）、全身 3000 点、全身 500 点、6-DoF 末端位姿、关节位置；
- **泛化对比**：域内（held-out split）、跨域 D↔B、保留 CLVR 实验室作为 unseen held-out H 域；
- **基线**：从头训练的"专家"模型（specialist）作为 held-out 场景的对照。

## 4. 资源与算力

- **论文正文及附录均未明确报告**所用的 GPU 型号/数量、单次训练时长或总计算量。仅给出"推理延迟 ≈0.1s/前向传播"（PTv3-1B ≈123.65ms）这一粗略指标。
- 训练数据量（2M 轨迹、500 小时）以及模型最大规模（1B 参数）暗示需要较大算力，但具体硬件配置缺失，可视为该工作透明度的一处不足。

## 5. 实验数量与充分性

- **实验维度充分**：覆盖
  - 骨干网络选型（6 种）、动作表示（5 种）、训练目标（运动加权/不确定性/Huber 损失）、预训练特征（DINOv2/3 多层）、模型规模（4 个量级）、数据规模（5 个比例）；
  - 数据混合（仅 DROID、仅 B1K、D+B 共训）；
  - 跨域与保留场景的 zero-shot 与 1/20 微调对比；
  - 真实机器人 8 类任务（纸巾盒、书本、围巾、枕头、微波炉、抽屉、掸子、扫帚）的成功率评测。
- **公平性**：每组消融都仅改变单一变量，遵循 controlled setup；评测指标基于同套专家过滤的测试集，避免了不同基线在不一致数据上评测。
- **充分性评价**：实验体系较完整、规模大、统计可靠；但缺乏对**单张图像以外更稀疏观测**、**光照/背景剧烈变化**、**人类示范 vs. 自主数据**的细粒度拆解，可能限制部分结论的普适性。
- **附录实验**：A.2/A.3 中还包含分块预测和部分可观测性的额外消融。

## 6. 主要结论与发现

- **骨干网络**：PTv3 在内存可控的前提下，参数可扩展到 GBND 的 **957×**（1B），且推理时延仅约 0.12s；
- **训练目标三件套**：运动加权 + 不确定性正则化 + Huber 损失，对真实噪声数据具有稳定化作用，比朴素 L2 基线显著提升；
- **预训练 2D 特征**：DINOv3 多层特征带来显著增益，提供隐式对象性先验；
- **Scaling Laws**：模型规模（50M→1B）和数据规模（5%→100%）在 DROID 上均呈现近似**对数线性**的精度提升；
- **动作表示**：仅夹爪的点流在仿真与真实两侧均优于末端位姿/关节位置等低维表示，并支持跨本体（Franka ↔ 双手机器人）正向迁移；
- **泛化性**：域内零样本迁移表现良好；sim↔real 零样本仍困难，但**仅用 1/20 训练步数的微调**即可追平甚至超过从零训练的专家模型；
- **真实机器人**：单一预训练 checkpoint + 同一 MPC 框架，即可在野外单张 RGB-D 下完成刚性推动、可形变操作、铰接物体操作、工具使用等 8 类任务，无需任何示范或后训练。

## 7. 优点

- **统一的、与本体无关的 3D 点流表征**，优雅地把状态和动作放在同一空间，是本工作最核心的概念性贡献；
- **大规模高质量 3D 交互数据集**（约 2M 轨迹、500 小时）开源，附完整的 3D 标注流水线（深度/外参/跟踪），填补了社区空白；
- **系统的"scaling recipe"研究**：从骨干、目标、特征到模型/数据规模的 5 维 scaling roadmap 完整、可复现；
- **跨本体能力**：Franka + 双手机器人同训，验证了真正的异构迁移；
- **实时性与实用性**：0.1s 推理可直接与 MPPI 闭环，结合真实机器人 8 类任务成功率的端到端验证；
- **零样本部署**：无需后训练或额外示范即可在野外完成多种操作任务，工程友好度高。

## 8. 不足与局限

- **算力与训练细节不透明**：未报告 GPU 型号/数量、训练时长、电能等资源消耗，限制可复现性；
- **sim↔real 零样本差距仍大**：尽管微调可快速收敛，但纯零样本跨域泛化（特别是 sim→real）尚不理想；
- **预测时域受限**：仅展示 1 秒（10 步 × 0.1s）的短时交互，**对长时序规划（>1s）** 与长程任务的支撑未充分验证；
- **真实硬件平台单一**：仅在 Franka + 单个 RealSense 上做实验；双手机器人、整体/移动操作的真实部署仍未展示；
- **任务目标仍需人工指定**：依赖 GUI 画目标点或 VLM，无法完全"开箱即用"，任务自动化与抽象层次有限；
- **静态场景假设**：模型假设前向传播中场景点集保持固定（对应关系仅在"想象"中保持），对动态多体交互场景的鲁棒性未深入研究；
- **评测指标偏连续**：以 L2 mover 为核心，对任务级长尾失败模式（接触错位、卡死、恢复）的刻画可能不足；附录虽提到任务成功率，但样本量与可重复性细节有限；
- **数据偏差风险**：DROID/B1K 偏单台/特定操作模式，背景、光照、物体分布的多样性仍可能限制对真正"in-the-wild"的覆盖；
- **与生成式世界模型的对比缺失**：与 Cosmos、Genie、V-JEPA 2 等视频/潜空间世界模型未做直接基准比较，难以判断点流表征在"长期想象"上的相对优势与劣势。

（完）
