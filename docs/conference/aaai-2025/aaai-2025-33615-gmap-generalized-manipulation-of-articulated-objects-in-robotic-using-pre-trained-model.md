---
title: "GMAP: Generalized Manipulation of Articulated Objects in Robotic Using Pre-trained Model"
title_zh: 基于预训练模型的机器人关节物体通用操纵方法 GMAP
authors: "Hongliang Zeng, Ping Zhang, Fang Li, QinPeng Yi, Tingyu Ye, Jiahua Wang"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33615/35770"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向关节物体的机器人感知与操纵综合流程
tldr: 针对服务机器人在关节物体感知与操纵方面已有方法只解决孤立子任务、缺乏端到端综合策略的问题，本文提出 GMAP 框架，将指令理解、部件级分割、关节几何与运动学参数估计、点级可供性预测以及交互位姿选择整合为统一流程。方法利用预训练大模型对形状、关节与可供性进行联合推理，并据此规划机械臂抓取与操作动作。在多种关节物体上的实验表明，该流程显著提高了对复杂物体的操纵成功率与泛化能力。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33615/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 817, \"height\": 304, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33615/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 863, \"height\": 231, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33615/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1754, \"height\": 685, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33615/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1726, \"height\": 915, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33615/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1807, \"height\": 597, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33615/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 535, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33615/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1820, \"height\": 749, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33615/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 875, \"height\": 382, \"label\": \"Table\"}]"
motivation: 已有方法仅解决关节物体感知或操纵的单一环节，缺乏从指令到完整操作的综合策略。
method: GMAP 联合执行部件级分割、关节几何与运动学估计以及点级可供性推理，并据此确定机械臂交互位姿。
result: 在多种关节物体上实现更高的操纵成功率和更强的跨类别泛化能力。
conclusion: 为服务机器人在复杂日常场景中操纵关节物体提供了统一的预训练驱动方案。
---

## Abstract
Perception and interaction with articulated objects present a unique challenge for service robots. Although recent research has emphasized understanding articulated shapes and affordance proposals, existing methods only address isolated aspects, failing to develop comprehensive strategies for robotic perception and manipulation of articulated objects. To bridge this gap, we propose GMAP, which systematically integrates the entire process from command to perception and manipulation. Specifically, we first perform precise part-level segmentation of the object and identify the geometric and kinematic parameters of articulated joints. Then, by evaluating point-level affordance proposals, we determine the interaction poses for the robot's end-effector. Finally, the robot's execution trajectory is dynamically computed by combining commands with joint parameters and interaction points. Additionally, a key innovation of GMAP is addressing the scarcity of annotated data. We designed a multi-scale point cloud feature extraction module and introduced pre-training and fine-tuning techniques, significantly enhancing the generalization capability of the perception model. Extensive experiments demonstrate that GMAP achieves state-of-the-art (SOTA) performance in both the perception and manipulation of articulated objects and adapts to real-world scenarios.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "GMAP: Generalized Manipulation of Articulated Objects in Robotic Using Pre-trained Model" following a specific structure. Let me analyze the paper content carefully and organize the response according to the 8 requested points.

Let me extract key information from the paper:

1. **Core problem**: Service robots need to manipulate articulated objects (e.g., cabinets, fridges). Existing methods only address isolated aspects (joint parameter estimation, digital twin, affordance visualization) but lack comprehensive strategies from command to perception to manipulation. Also, high-quality annotated 3D data is scarce.

2. **Methodology (GMAP)**:
   - Multi-Scale Feature Extraction (MSFE) module
   - Three core perception modules: Seg-Net, Para-Net, Afford-Net
   - Pre-training using Point-MGE (VQ-VAE + masked modeling)
   - Multi-scale patching with FPS and KNN
   - ViT encoders
   - Point-wise feature extraction (PFE) with feature propagation
   - Segmentation with movability prediction
   - Joint parameter estimation (type, orientation, position, state)
   - Affordance with action proposal and action scoring
   - Trajectory planning using joint parameters and commands

3. **Experiments**:
   - Datasets: PartNet-Mobility, Shape2Motion
   - Pre-training: ShapeNet
   - Simulator: Sapien
   - Baselines: RPM-Net, ANCSH, Ditto, Cart, MARS, Where2Act, AdaAfford
   - Real-world: RealSense2 RGB-D camera, 3 types of articulated objects
   - Evaluation: IoU for segmentation, errors for joint parameters, success rate for manipulation

4. **Resources**: Not explicitly mentioned in the text I have

5. **Experiment count**: Multiple tables covering segmentation, joint parameters, generalization, manipulation - seems comprehensive

6. **Main conclusions**: SOTA performance in segmentation and joint parameter estimation, better generalization, dynamic manipulation planning, real-world adaptability

7. **Strengths**: Multi-scale feature extraction, pre-training strategy, integrated pipeline, dynamic trajectory planning

8. **Limitations**: Acknowledged need to improve affordance proposal accuracy; segmentation edges may have jaggedness for closed parts

Let me now write this up in Chinese with proper Markdown formatting.</think>

# GMAP 论文总结

## 一、核心问题与研究背景

- **核心问题**：服务机器人在日常生活中需要对大量关节物体（如柜门、冰箱、抽屉、桌椅等）进行自主操纵。当前研究往往只解决孤立子任务——有的只做关节参数估计，有的只做数字孪生重建，有的只做可供性（affordance）热图可视化——缺乏从"自然语言指令 → 感知 → 操纵"的端到端完整策略。
- **关键矛盾**：关节物体感知模型对泛化性和精度要求很高，但高质量的 3D 标注数据极度稀缺；为缓解数据不足而采用的"类别级"模型又削弱了模型在真实场景中的部署适应性。
- **研究目标**：构建一个通用的"小脑"模块，能够根据指令完成部件级分割、关节几何/运动学估计、可供性推理和动态轨迹规划，使机器人能够将抽象意图（如"打开冰箱门 50%"）转化为具体的执行轨迹。

## 二、方法论

### 2.1 整体框架（GMAP）

GMAP 由四个核心组件构成：多尺度特征提取（MSFE）、逐点特征提取（PFE）、三个感知子网络（Seg-Net、Para-Net、Afford-Net）以及轨迹规划模块。

### 2.2 多尺度特征提取（MSFE）

- **归一化**：将点云平移到中心，并对最大距离做缩放，使其适应不同尺度的物体：
  
  $X' = \frac{X - \frac{1}{N}\sum x_i}{\max_i \|x_i - \frac{1}{N}\sum x_j\|}$

- **多尺度切片**：在不同尺度上使用 Farthest Point Sampling（FPS）选取中心点，再用 KNN 聚成 patch。文中设定三档尺度：$M = \{512, 256, 64\}$，每 patch 点数 $K = \{32, 8, 8\}$。

- **ViT 编码**：第一尺度使用 mini-PointNet 提取初步特征并加上位置编码，后续尺度将上一层 patch 特征通过最大池化融合后再送入下一个 ViT 编码器。

### 2.3 逐点特征提取（PFE）

- 借鉴 PointNet++ 的特征传播机制，将多个尺度的 patch 特征插值回原始点云，再通过最大池化和平均池化拼接融合，最后用一维卷积降维。
- 这一设计允许 Seg-Net 在稀疏点 $X$（$N$ 点）上提取特征，却在稠密点 $Y$（$N'$ 点）上完成分割，节省计算开销。

### 2.4 预训练策略

- 采用 Point-MGE 的两阶段范式：先训练 VQ-VAE 将点块特征映射为离散码本，再对 patch 进行可变掩码并要求 MSFE 从可见部分重建 3D 形状。
- 在 ShapeNet（5 万余模型、55 类）上预训练 300 个 epoch，再在关节物体数据集上做 100 个 epoch 的后训练/微调。

### 2.5 Seg-Net（部件分割与可动性预测）

- 两个 MLP 头分别预测每点所属部件 $\gamma$ 与部件可动性 $\tau \in \{0, 1\}$。
- 损失函数：$L_{seg} = L_{bce}(\tau, \hat{\tau}) + L_{ce}(\gamma, \hat{\gamma})$。

### 2.6 Para-Net（关节参数估计）

- 根据指令选择某个可动部件 $\kappa$ 后，用特征分离器将属于该部件的特征与不属于该部件的特征分别聚合，再拼接送入 MLP 头。
- 预测关节四个属性：类型 $\rho$（旋转/平移，0/1）、方向 $o$、位置 $u$、当前状态 $s \in [0,1]$。
- 位置损失利用估计点到真实轴线的**投影距离**；方向损失用两向量夹角的 $\arccos$；状态用 L1 loss。
- 综合目标：$L_{para} = L_{type} + (1-\rho)L_{pos} + L_{ori} + L_{state}$，仅对旋转关节计入位置损失。

### 2.7 Afford-Net（可供性估计）

- 两个 MLP 头：
  - **Action Proposal (AP)**：以点特征 + 高斯噪声 + 动作类型 $a_t$（push/pull）为输入，预测末端执行器在 SO(3) 空间中的 3-DoF 朝向 $R_z$，用 Min-of-N 损失优化，保证高召回率。
  - **Action Scoring (AS)**：以点特征、AP 给出的 $R$ 以及动作类型为输入，预测该交互点是否可行的二分类得分，用 BCE 训练。
- 训练数据通过在仿真器内执行交互收集 $(S, p, R, a_t, r)$ 五元组。

### 2.8 轨迹规划

- 根据指令中的目标状态 $s'$ 与当前状态 $s$ 之差计算所需运动位移 $l = (s' - s) \cdot L$（$L$ 为状态满量程对应的物理极限）。
- **平移关节**：$p(t) = p + t \cdot (l \cdot o)$
- **旋转关节**：$p(t) = R(o, l \cdot t)(p - u) + u$（Rodrigues 公式）
- 通过插值得到末端执行器在 SE(3) 空间中的完整执行轨迹。

## 三、实验设计

### 3.1 数据集

- **PartNet-Mobility**：选用 14 个关节物体类别。
- **Shape2Motion**：选用 4 个类别。
- 每个实例导入仿真器后，随机调整可动关节状态 20 次，用深度相机采样点云，按 9 : 1 : 1 划分训练/验证/测试集。
- **ShapeNet**：用于 MSFE 预训练。
- **Sapien 仿真器**：用于进行推/拉操纵规划评估。
- **真实环境**：配备 RealSense2 RGB-D 相机，对 3 类真实关节物体进行测试。

### 3.2 对比方法

- **分割与关节参数基线**：RPM-Net、ANCSH、Ditto、Cart、MARS，以及一个去掉预训练的 GMAP 消融版（w/o Pre-training）。
- **可供性/操纵基线**：Where2Act、AdaAfford，加上仅用 Afford-Net 而不带动态规划的 "Our-Afford" 消融版，以及三种手工动作基线 B-Random、B-Normal、B-PCPNet。

### 3.3 评估指标

- 部件分割 mIoU（%）。
- 旋转/平移关节的方向误差（角度）、位置投影误差、状态误差。
- 操纵任务的成功率（Push/Pull Succ %）。
- 跨类别泛化测试：在 cabinet 上训练，在 5 个未见类别上测试。

## 四、资源与算力

- **未明确披露**：论文正文与附录中未具体说明 GPU 型号、数量、内存、训练总耗时等算力信息。仅提到使用 AdamW 优化器在 ShapeNet 上预训练 300 epoch + 微调 100 epoch。
- 这一缺失使读者难以评估其工程成本与可复现性。

## 五、实验数量与充分性

- **表格覆盖**：
  - 表 1：在 PartNet-Mobility 与 Shape2Motion 上对分割和关节参数的多维比较（共 7 类指标 × 2 数据集）。
  - 表 2：跨类别泛化实验（5 个未见类别 + 1 个训练类别）。
  - 表 3：5 类的推/拉操纵成功率对比（7 个方法）。
  - 图 4：8 个实例的可视化（4 类 × 2 实例）。
  - 图 5：真实环境 3 类物体的关键帧可视化。
- **充分性判断**：
  - 感知层面有分割、关节、跨类别、可视化多角度验证，相对充分。
  - 操纵层面仅给出 Sapien 仿真中的成功率与少量真实场景例证，缺少消融对动态轨迹规划子模块独立贡献的细粒度分析。
  - 真实实验未给出多次重复的平均成功率与方差统计，可能影响对鲁棒性结论的客观判断。

## 六、主要结论

- GMAP 在 PartNet-Mobility 与 Shape2Motion 上分别取得 **79.6%** 与 **81.4%** 的部件分割 mIoU，全面超越现有方法。
- 旋转关节方向估计误差低至 **0.45° / 0.39°**，在多类指标上超过 SOTA（MARS）。
- 旋转关节状态估计比 MARS 在两个数据集上分别低 **3.53°** 和 **2.68°**。
- 指令驱动的推/拉操纵成功率达 **36.94% / 21.72%**，显著优于 AdaAfford（27.71% / 10.45%）等最强基线。
- 跨类别泛化：在仅用 cabinet 训练后对 5 类未见物体的方向估计平均误差仅约 2.41°，表现出强泛化。
- 直接将仿真训练模型部署到真实环境，配合柔顺控制可成功操纵 3 类真实物体。

## 七、优点与亮点

- **统一的"指令 → 感知 → 操纵"管线**：不再将各子任务割裂开，而是融合到同一个特征主干（MSFE + PFE）联合训练，使各模块互相受益。
- **多尺度 + 预训练策略**：ViT 编码器在多尺度 patch 上运行，并通过 Point-MGE 风格的自监督预训练大幅缓解 3D 标注稀缺问题；消融实验明确证实预训练几乎在所有指标上都带来显著提升。
- **动态轨迹规划**：不同于 Where2Act/AdaAfford 等仅预测固定 push/pull 的方法，GMAP 根据指令目标状态与当前状态之差实时计算 SE(3) 轨迹，能处理"打开 100%"之类的精确指令。
- **跨类别泛化验证**：在 cabinet 训练、其他 5 类上测试的设计直接回应了"类别级模型泛化性差"的问题。
- **真实环境部署**：使用消费级 RealSense2 相机即可工作，且仅依赖柔顺控制吸收估计误差，工程门槛较低。

## 八、不足与局限

- **算力与实现细节缺失**：未给出 GPU 型号/数量、训练时长、每个 epoch 的耗时，不便于复现。
- **分割边缘精度有限**：作者自述对处于闭合状态且与其他部件紧贴的部分，分割边缘存在锯齿；虽不影响关节参数估计，但可能影响需要精细接触点的下游任务。
- **可供性仍是瓶颈**：作者在结论中明确承认"进一步提升交互可供性提议的精度仍是开放问题"，并指出 Our-Afford 仍略弱于经过 few-shot 交互微调的 AdaAfford。
- **仿真到真实的桥接较简单**：真实环境实验仅展示了 3 类物体的成功案例，缺乏对失败案例的统计分析与系统误差归因，也未给出 sim-to-real gap 的量化指标。
- **操纵评估维度有限**：成功率的对比集中在指令驱动的推/拉任务，未涉及多步复合任务（如"开门→取出物品"）、复杂接触动力学场景或多机器人协同。
- **指令理解依赖上游**：框架本身只接受结构化指令（如目标部件 + 目标状态），将 LLM 的"指令到原子动作"部分留给上游；与真正的端到端自然语言驱动机器人仍有差距。
- **数据规模仍受仿真器限制**：训练数据来自 Sapien 和 ShapeNet，与真实家庭环境中的物体多样性、长尾分布差距较大。

（完）
