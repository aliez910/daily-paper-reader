---
title: "MobileH2R: Learning Generalizable Human to Mobile Robot Handover Exclusively from Scalable and Diverse Synthetic Data"
title_zh: MobileH2R：仅基于可扩展多样化合成数据学习通用移动机器人人-机交接技能
authors: "Wang, Zifan, Chen, Ziqing, Chen, Junyu, Wang, Jilong, Yang, Yuxin, Liu, Yunze, Liu, Xueyi, Wang, He, Yi, Li"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_MobileH2R_Learning_Generalizable_Human_to_Mobile_Robot_Handover_Exclusively_from_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于合成数据的机器人交接操作模仿学习
tldr: 移动机器人需要在广阔工作空间内可靠接收物体，通用交接能力难以通过真实演示获得。本文提出MobileH2R框架，完全依赖可扩展的合成数据学习通用视觉交接技能，包括合成人体运动生成流水线、自动演示生成与高效4D模仿学习。该方法为基于模仿学习的机器人操作控制提供了重要技术参考，对减少对真实数据依赖具有显著价值。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1724, \"height\": 426, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1726, \"height\": 972, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 742, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1255, \"height\": 220, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1258, \"height\": 223, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1258, \"height\": 208, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1257, \"height\": 207, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 882, \"height\": 267, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 894, \"height\": 270, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 838, \"height\": 225, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-mobileh2r-learning-generalizable-human-to-mobile-robot-handover-exclusively-from-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 872, \"height\": 145, \"label\": \"Table\"}]"
motivation: 移动机器人在大工作空间内的通用人-机交接能力难以通过真实演示获得。
method: 构建合成数据生成流水线并采用4D模仿学习从合成数据中蒸馏交接策略。
result: 实现了完全基于合成数据训练的通用视觉交接技能。
conclusion: MobileH2R展示了合成数据加模仿学习实现通用机器人操作的可行性。
---

## Abstract
This paper introduces MobileH2R, a framework for learning generalizable vision-based human-to-mobile-robot (H2MR) handover skills. Unlike traditional fixed-base handovers, this task requires a mobile robot to reliably receive objects in a large workspace enabled by its mobility. Our key insight is that generalizable handover skills can be developed in simulators using high-quality synthetic data, without the need for real-world demonstrations. To achieve this, we propose a scalable pipeline for generating diverse synthetic full-body human motion data, an automated method for creating safe and imitation-friendly demonstrations, and an efficient 4D imitation learning method for distilling large-scale demonstrations into closed-loop policies with base-arm coordination. Experimental evaluations in both simulators and the real world show significant improvements (at least +15% success rate) over baseline methods in all cases. Experiments also validate that large-scale and diverse synthetic data greatly enhances robot learning, highlighting our scalable framework.

---

## 论文详细总结（自动生成）

<think>Let me analyze this paper carefully and create a structured summary in Chinese.

The paper is about MobileH2R, a framework for learning generalizable vision-based human-to-mobile-robot (H2MR) handover skills using only synthetic data. Let me extract the key information:

1. **Core Problem**: Mobile robots need to reliably receive objects handed over by humans across large workspaces. Real-world training is dangerous and expensive, so they need to develop these skills in simulators.

2. **Methodology**: 
- Scalable pipeline for diverse full-body human motion synthesis
- Automated method for safe, imitation-friendly demonstrations
- 4D imitation learning with base-arm coordination
- Uses CHOMP planner with future obstacle avoidance
- Vision neural loss for imitation-friendly demonstrations
- Modified PointNet++ for processing human body and hand-object point clouds separately

3. **Experiments**:
- Three test sets: m0 (simple), n0 (complex), s0 (real mocap)
- 100k training scenes, 1k testing scenes per setup
- 6 objects in real-world user study
- Baselines: Grasp Selection + Trajectory Planning, GenH2R, GenH2R(reprod.)

4. **Resources**: 
- RTX 3090 with 32 CPU cores for timing standardization
- Galbot G1 mobile robot for real-world experiments
- 10k and 100k demonstrations compared

5. **Experiments**:
- Comparison with baselines
- Data scaling evaluation
- Demonstration strategies evaluation
- Ablations on policy designs
- Real-world user study

6. **Conclusions**: 
- +15% improvement over baselines
- Reduces collisions by about 1/3
- Demonstrates viability of synthetic data + imitation learning

Let me write a comprehensive Chinese summary now.</think>

# MobileH2R 论文详细总结

## 1. 核心问题与研究动机

- **任务定义**：研究"人-移动机器人交接"（Human-to-Mobile-Robot, H2MR）问题，即移动机器人需要在大工作空间内可靠接收人类递交的物体。相比传统固定基座机器人，移动机器人依赖其移动性扩展作业范围。
- **核心挑战**：
  - 真实训练成本高、安全风险大、不可规模化。
  - 现有仿真数据集（如 HandoverSim 仅 1000 条序列）规模与复杂度不足。
  - 现有方法（GenH2R 等）通常只针对固定基座机械臂，且仅建模手部手势，缺乏全身运动建模。
  - 移动机器人需同时协调底盘与机械臂动作，难度更高。
- **核心洞察**：只要合成数据质量足够高（包含人体运动、物体资产、机器人演示），通用交接技能可完全在仿真中习得，无需任何真实演示。

## 2. 方法论

### 2.1 整体框架
框架包含三大模块：
1. **MobileH2R-Sim**：可扩展的全身人体运动合成流水线。
2. **安全且利于模仿的演示自动生成**：基于 CHOMP 的轨迹规划。
3. **4D 模仿学习**：融合时空点云的基-臂协调策略学习。

### 2.2 MobileH2R-Sim（人体运动合成）
- **两阶段生成**：
  - **预交接阶段**：使用 Guided Motion Diffusion（GMD，训练于 AMASS）生成多样化的全身运动（走、坐、跑、跳舞等）。
  - **交接阶段**：采用任务特定的局部合成法，分三步生成手臂运动：(1) 在可行空间随机采样最终交接位置；(2) 通过运动学优化器求解满足人体关节约束的末端构型；(3) 在初始与目标位置间插值生成平滑轨迹。
- **交互式设计**：当机器人距离小于 1m 或预交接阶段超时，触发阶段转换；人会对机器人靠近做出反应，模拟真实交互。
- **资产生成**：使用 ShapeNet（8836 个物体）、Acronym（抓取姿态）、DexGraspNet（手部姿态）；并使用 LLM（如 GPT-4）生成与物体语义属性对齐的运动提示。

### 2.3 安全且利于模仿的演示生成
- **底层规划器**：基于 CHOMP（梯度优化运动规划），结合物体 6D 位姿、人手与人体位姿、候选抓取点等特权信息。
- **安全性损失**：
  - **未来障碍物规避**：不仅考虑当前时刻，而是对时间窗内未来时刻计算碰撞损失，预判并平滑避让。
  - **最终姿态约束**：强制机器人停在人体前方进行面对面接交，避免从背后绕过等不安全动作。
- **利于模仿损失（视觉神经损失）**：
  - 核心思想：若视觉能从状态恢复出关键信息（如物体位姿），则视觉-动作关联更易学习。
  - 训练一个位姿预测网络 P，根据视觉输入预测物体位姿。
  - 训练一个状态-视觉恢复估计器 E，根据状态估计 P 的视觉神经损失。
  - 在轨迹优化时使用 E 估计的损失替代 P（因仿真渲染不可微），使梯度可回传以优化轨迹，从而保证生成的演示在视觉上易于学习和模仿。
  - 实验发现：相比手工设计"相机始终朝向物体"等启发式损失，神经视觉损失更稳定且泛化更好。

### 2.4 4D 模仿学习策略
- **输入**：头相机与腕相机点云，分割为物体、手、人体三部分，统一对齐到末端执行器坐标系。
- **4D 信息**：在每个时间戳重建点云，利用 ICP 配准计算相邻帧点云间的流信息（flow），注入时序信息。
- **特征提取**：针对人体与手-物体点云的空间尺度差异，采用不同采样半径的 Set Abstraction 层分别提取特征，最后用 PointNet 层拼接为全局表示。
- **输出**：使用 MLP 同时解码底盘 SE(2) 动作、机械臂 SE(3) 动作以及抓取姿态 SE(3) 预测。
- **损失函数**：
$$L = \lambda_1 L_{base} + \lambda_2 L_{arm} + \lambda_3 L_{pred}$$
  - $L_{base}$：底盘动作监督损失
  - $L_{arm}$：机械臂动作监督损失
  - $L_{pred}$：抓取姿态预测辅助损失

## 3. 实验设计

### 3.1 数据集
- **m0**：简单场景，人直线接近递交；100k 训练 + 1k 测试。
- **n0**：复杂场景，含坐、下楼梯、跑步、跳舞等；100k 训练 + 1k 测试。
- **s0**：基于 DexYCB 真实 mocap 数据（含 1000 个真实场景，20 个物体），补上人体模型；720 训练 + 144 测试。
- **预交接阶段 6 秒 + 交接阶段 1.05 秒**，触发阈值为 1m 距离或预交接超时。

### 3.2 评估指标
- **成功率**（无碰撞、抓住物体、未超时 Tmax=15s）。
- **时间**：推理时间 + 执行时间（区别于 GenH2R 仅考虑推理时间）。
- **AS（Average Success）**：类似 AP，对成功时间累积的成功率。

### 3.3 对比方法
- **Grasp Selection + Trajectory Planning**：非端到端，使用 GraspNet 或真值匹配获取抓取位姿，再做运动规划。
- **GenH2R**：端到端，仅输出 6D 机械臂动作。
- **GenH2R (reprod.)**：在 n0 数据上重新训练，扩展到基-臂动作（底盘通过逆运动学计算）。

### 3.4 真实世界实验
- **机器人**：Galbot G1，全向轮底盘 + 7-DOF 机械臂 + 头部深度相机 + 腕部深度相机。
- **分割**：使用 SAM2 对点云进行实例分割。
- **用户研究**：6 个物体，2 种场景（简单/复杂，含坐、下楼、对抗动作），每种 30 次试验。

## 4. 资源与算力

- **标准化测试平台**：空闲 RTX 3090 + 32 CPU 核（用于统一时间测量）。
- **训练规模**：对比 1k、10k、100k 不同规模的演示数据。
- **未明确说明**：训练总时长、GPU 数量、具体训练超参数设置等细节论文未详细披露（这些信息缺失）。

## 5. 实验数量与充分性

- **方法对比实验**（表 1）：在 m0、n0、s0 三个测试集上与三种基线对比。
- **数据规模化实验**（表 2）：演示数量（1k vs 10k vs 100k）× 资产类型（n0/m0/s0）共 5 组组合。
- **演示策略消融**（表 3）：5 种策略对比（去除未来避障、去除终态约束、去除模仿损失、相机朝向损失、完整方法）。
- **策略设计消融**（表 4）：4 组（无 flow、无人体信息、无协调动作、完整）。
- **真实世界实验**（表 5）：2 场景 × 2 方法 × 30 次试验，共 120 次试验。
- **充分性评估**：
  - 多维度评估较为全面，涵盖仿真与真实、多个数据集、多种策略消融。
  - 但每个真实场景试验数（30 次）相对有限，且未给出方差或置信区间，统计显著性证据略显不足。
  - 真实世界实验仅与 GenH2R(reprod.) 一个基线比较，缺乏与其他方法的对比。

## 6. 主要结论与发现

- **性能提升**：相比基线方法，在所有测试场景中至少提升 +15% 成功率。
- **m0/n0/s0 三个测试集**：成功率分别为 63.8% / 53.4% / 77.8%，明显优于 GenH2R(reprod.) 的 46.8% / 32.9% / 61.1%。
- **数据规模化效应**：100k 比 10k 提升约 3.3%，1k 则下降 13.9%；mocap 数据集 s0 平均下降 34.6%，表明仿真可扩展资产对泛化的重要性。
- **演示策略影响**：未来障碍物规避降低 4% 成功率影响，最终姿态约束影响 8%，模仿损失影响 11.6%（影响最大）。
- **策略设计影响**：去除 flow 损失下降 12.1%，去除人体信息下降 12.5%，去除基-臂协调下降 17.8%（影响最大）。
- **真实世界实验**：简单场景 80.0% vs 40.0%，复杂场景 63.3% vs 30.0%，相比 GenH2R(reprod.) 提升约 33-40 个百分点。
- **安全性**：自动生成的可扩展演示使碰撞率降低约 1/3，成功率提升 11.6%。

## 7. 优点与亮点

- **完全零真实演示**：仅依赖合成数据即可获得通用交接能力，对数据获取昂贵的机器人任务意义重大。
- **可扩展的人体运动合成**：结合扩散模型与任务特定合成，覆盖多样化全身运动。
- **创新的视觉神经损失**：通过可微的状态-视觉恢复估计器 E 解决仿真渲染不可微问题，使轨迹优化可考虑视觉可学性，这是相对巧妙的设计。
- **全身点云融合**：将人体点云纳入策略输入，提升安全性与上下文建模能力。
- **基-臂协调联合解码**：通过统一 MLP 同时解码基座与机械臂动作，相比分离解码（下降 17.8%）显著更优。
- **不同尺度点云的差异化处理**：为人体与手-物体点云使用不同采样半径的 Set Abstraction，解决尺度不平衡问题。
- **未来时窗避障**：相比仅考虑当前时刻的避障，更平滑自然。

## 8. 不足与局限

- **真实世界实验规模有限**：仅与 GenH2R(reprod.) 一个基线对比，每场景 30 次试验，未报告方差或显著性检验。
- **数据多样性局限**：人体模型为单一 SMPL 类骨架，对不同年龄、身高、体型的泛化性未验证。
- **物体集合有限**：虽然 ShapeNet 提供 8836 个物体，但真实场景物体种类、形状、表面材质的多样性远超仿真。
- **训练时长与算力未披露**：缺乏计算资源消耗的明确信息，难以评估实际部署成本。
- **依赖 LLM 与外部资产**：使用 GPT-4 等商业模型生成运动提示，存在可复现性与版权风险。
- **简单相机朝向损失反而降低性能**：表明手工启发式设计较为脆弱，但作者未深入分析其失败模式。
- **Sim-to-Real gap 未量化**：缺乏对仿真与真实世界差异的系统性分析（如域随机化、域适应策略）。
- **应用场景限制**：仅验证桌面尺寸物体的递交，未涉及大型、重型或柔性物体的复杂交接。
- **CHOMP 依赖特权信息**：规划阶段需要完整 6D 位姿、人手与人体位姿，仿真中易获取，但真实部署时需解决感知问题（论文仅依赖 SAM2 分割，未深入讨论）。

（完）
