---
title: "Two by Two: Learning Multi-Task Pairwise Objects Assembly for Generalizable Robot Manipulation"
title_zh: 2BY2：面向可泛化机器人操作的多任务两物体装配学习
authors: "Qi, Yu, Ju, Yuanchen, Wei, Tianming, Chu, Chi, Wong, Lawson L.S., Xu, Huazhe"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Qi_Two_by_Two_Learning_Multi-Task_Pairwise_Objects_Assembly_for_Generalizable_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向日常物体装配的大规模操作基准
tldr: 3D 装配是家用机器人的关键能力，但现有数据集多聚焦几何碎片或工业零件，缺乏日常装配的复杂性。本文构建 2BY2 大规模日常两物体装配数据集，覆盖插拔、插花与放面包等 18 类细粒度任务，包含一千余实例和五百余对带位姿与对称性标注的物体。该数据集填补了日常装配基准的空缺，为可泛化机器人操作研究提供重要支撑。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1805, \"height\": 761, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 856, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 857, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1782, \"height\": 984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 873, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1786, \"height\": 1220, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1806, \"height\": 345, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1808, \"height\": 897, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 731, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qi-two-by-two-learning-multi-task-pairwise-objects-assembly-for-generalizable-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1810, \"height\": 267, \"label\": \"Table\"}]"
motivation: 现有装配数据集过于简单，难以反映真实日常装配的复杂度，限制了可泛化操作策略的发展。
method: 构建大规模带位姿与对称性标注的日常两物体装配数据集，涵盖 18 类细粒度日常装配任务。
result: 提供了包含 1034 个实例与 517 对物体的可泛化装配基准，弥补了日常装配数据集的空白。
conclusion: 2BY2 为可泛化机器人装配操作研究提供了贴近真实生活的大规模基准资源。
---

## Abstract
3D assembly tasks, such as furniture assembly and component fitting, play a crucial role in daily life and represent essential capabilities for future home robots. Existing benchmarks and datasets predominantly focus on assembling geometric fragments or factory parts, which fall short in addressing the complexities of everyday object interactions and assemblies. To bridge this gap, we present 2BY2, a large-scale annotated dataset for daily pairwise objects assembly, covering 18 fine-grained tasks that reflect real-life scenarios, such as plugging into sockets, arranging flowers in vases, and inserting bread into toasters. 2BY2 dataset includes 1,034 instances and 517 pairwise objects with pose and symmetry annotations, requiring approaches that align geometric shapes while accounting for functional and spatial relationships between objects. Leveraging the 2BY2 dataset, we propose a two-step SE(3) pose estimation method with equivariant features for assembly constraints. Compared to previous shape assembly methods, our approach achieves state-of-the-art performance across all 18 tasks in the 2BY2 dataset. Additionally, robot experiments further validate the reliability and generalization ability of our method for complex 3D assembly tasks. More details and demonstrations can be found at https://tea-lab.github.io/TwoByTwo/.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Two by Two: Learning Multi-Task Pairwise Objects Assembly for Generalizable Robot Manipulation" following a specific structure with 8 points. Let me carefully analyze the paper and produce a comprehensive summary.

Let me go through each section:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and computing
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I need to use Markdown formatting with hierarchical headings and bullet points, in Chinese. Let me draft this carefully based on the paper content.
</think>
# 2BY2：面向可泛化机器人操作的多任务两物体装配学习

## 1. 核心问题与研究动机

- **核心问题**：3D 装配任务（如家具组装、零件插装）是家用机器人必须掌握的关键能力。然而现有装配基准和数据集主要聚焦于"几何碎片拼合"（如 Breaking Bad、Neural Shape Mating）或"工业零件装配"（如 Factory、RLBench），缺乏对**日常物体两两装配**这一更贴近真实生活场景的复杂任务的覆盖。
- **研究动机**：
  - 日常两物体装配不仅要求几何形状对齐，还涉及**语义关系**（如花要放进花瓶而非茶杯）和**空间功能关系**（如面包需水平插入烤面包机），单纯的局部几何匹配方法表现次优。
  - 现有数据集普遍存在规模小、任务单一、无对称性标注、未考虑真实应用场景等局限。
  - 本文通过构建一个**大规模、带位姿与对称性标注、覆盖日常装配场景**的新基准，并配套提出一种有效的 SE(3) 位姿估计方法，推动可泛化机器人装配操作研究。

## 2. 方法论

### 2.1 核心思想

- 模仿人类的装配逻辑（先放底座再插零件，例如先放花瓶再插花），提出**两步式（Two-Step）成对网络架构**：
  - 第一步（Branch B, $B_B$）：预测**基座物体** $O_B$（如花瓶、邮箱、螺母）的位姿。
  - 第二步（Branch A, $B_A$）：利用 $O_B$ 变换后的点云与 $O_A$（如花、信件、螺栓）联合预测 $O_A$ 的位姿。
- 通过**分离训练**（Branch A 训练时使用 $P_B$ 的真值位姿）减少两物体位姿误差的相互干扰；测试时再级联使用。

### 2.2 关键技术细节

- **编码器：两尺度（Two-Scale）SE(3) 等变 + SO(3) 不变 Vector Neuron DGCNN**
  - 基础组件是 Vector Neuron Network (VNN)，将传统神经元从标量扩展为 3D 向量，保证 SO(3) 旋转等变性。
  - **平移等变性**：通过减去点云质心 $\bar{x} = (\sum_{i=1}^n p_i)/n$ 实现 $f(P+T) = f(P) + T$。
  - **两尺度机制**：采用两个不同 K 值的 KNN 分支分别提取局部与全局特征，再拼接融合，形成"金字塔"结构。
- **跨物体特征融合模块（Cross-Object Fusion）**
  - 在 $B_A$ 中对 $I_B$（$O_B$ 的 SO(3) 不变特征）与 $E_A$（$O_A$ 的等变特征）做**逐点乘法**：
  $$f(R \cdot (I_B * E_A)) = R \cdot f(I_B * E_A), \quad R \in \mathbb{R}^{3\times3}$$
  - 在保留 $O_A$ 旋转等变性的同时，将 $O_B$ 的几何信息融入每个 $O_A$ 点特征。
- **位姿预测头**：对 $B_A$ 与 $B_B$ 分别采用**独立 MLP** 头预测平移 $T \in \mathbb{R}^3$ 与旋转 $R \in \mathbb{R}^{3\times3}$，缓解两者收敛速度差异。
- **损失函数**：
  - 平移：L1 损失 $L_{trans} = L_1(T_{pred}, T_{gt})$。
  - 旋转：测地距离（Geodesic Distance）：
  $$L_{rot} = \arccos\left(\frac{\text{tr}(R_{gt} R_{pred}^T) - 1}{2}\right)$$
  - 总损失 $L = \lambda_{rot} L_{rot} + \lambda_{trans} L_{trans}$。

### 2.3 算法流程

1. 输入两片点云 $P_A, P_B \in \mathbb{R}^{1024 \times 3}$（去质心后）。
2. $B_B$ 通过两尺度 VN-DGCNN 提取 $E_B$，经 MLP 头输出 $\hat{T}_B, \hat{R}_B$。
3. 将 $\hat{T}_B, \hat{R}_B$ 作用于 $P_B$ 得到变换后的 $\hat{P}_B$。
4. $B_A$ 同时接收 $\hat{P}_B$ 与 $P_A$，提取 $E_A$、$I_B$ 并融合，输出 $\hat{T}_A, \hat{R}_A$。

## 3. 实验设计

### 3.1 数据集：2BY2

- **规模**：1,034 个实例、517 对独特物体；36 个类别；18 个细粒度装配任务。
- **任务层次（3 大类 18 子类）**：
  - **Lid Covering（盖合类，5 子类）**：Kitchenport、Bottle、Kettle、Coffeemachine、Cup。
  - **Inserting（插入类，6 子类）**：Plug、Childrentoy、Letter、Bread、Nut、Coin、Key、Usb。
  - **High Precision Placing（高精度放置类，5 子类）**：Box、Tissue、Flower、Teaport、Position。
- **数据来源**：3D Warehouse、SAPIEN PartNet-Mobility、Google SketchUp 3D Challenge、Objaverse。
- **标注**：人工配对与清洁、均匀缩放、定义**规范位姿**（物体稳定放置于 XY 平面，最低点对齐 Z=0）；采用蓝噪声采样生成 (1024, 3) 点云；标注 Z 轴旋转对称（如瓶子、螺丝）与 X 轴镜像对称（如面包、字母）。
- **训练/测试划分**：测试集包含**未见过的新几何形状**，并通过 Chamfer Distance 量化训练-测试几何差异（Figure 2）。
- **跨类基准**：Lid Covering、Inserting、High Precision Placing 三大类以及 All（全任务）联合训练/测试，评估跨任务泛化能力。

### 3.2 评估指标

- **平移 RMSE** 与**旋转 RMSE**（考虑对称性，使用 Euler 角表示）。
- 真实机器人实验采用**成功率**（10 次初始位姿下成功次数）。

### 3.3 对比方法

- 选取 4 个装配/形状匹配领域 SOTA 基线：
  - **Jigsaw**[NeurIPS'24]：基于分层全局/局部特征的拼合方法。
  - **Puzzlefusion++**[2024]：基于扩散模型的 6-DoF 对齐 + Transformer 验证。
  - **Neural Shape Mating (NSM)**[CVPR'22]：PointNet + Transformer 联合预测。
  - **SE(3)-Assembly**[ICCV'23]：利用 SE(3) 等变性联合预测多位姿。
- 真实机器人实验中以 **SE(3)-Assembly** 为基线。

## 4. 资源与算力

- 论文**未明确说明**所使用的 GPU 型号、数量、训练时长与计算预算。
- 仅披露超参数：batch size = 4，Adam 优化器初始学习率 1e-4，训练 1000 个 epoch 以完全收敛。
- 真实机器人平台：UR5 机械臂 + Robotiq 2F-85 夹爪。

## 5. 实验数量与充分性

- **主实验（Table 3）**：在 18 个细粒度任务上对比 5 种方法 × 2 项指标 = 约 180 个数据点；另包含 4 个跨类/全任务汇总。
- **真实机器人实验（Table 4）**：4 个任务（Cup、Flower、Bread、Plug）× 10 次随机初始位姿 = 40 次试验，对比基线。
- **消融实验（Table 5）**：在三跨类任务与 All 上对比：
  - 编码器：VN-DGCNN、DGCNN、PointNet、两尺度 VN-DGCNN（4 种）。
  - 训练策略：端到端联合训练 vs. 两步分离训练。
- **可视化对比（Figure 6）**：在 7 个任务上提供定性结果展示。
- **充分性评估**：
  - 优点：基线覆盖匹配式、图网络式、扩散式三大类装配方法；包含单任务细粒度评估与跨任务/全任务泛化评估，并辅以消融与真机验证。
  - 局限：未提供统计显著性检验（如多次运行的均值/方差）；未报告每个任务的训练-测试样本数与计算成本。

## 6. 主要结论与发现

- 在 2BY2 全部 18 个细粒度任务上均取得 SOTA，**平均**平移 RMSE 降低 0.046、旋转 RMSE 降低 8.97。
- 在 All 任务上以 0.110 平移 RMSE 与 41.44 旋转 RMSE 显著优于最强基线（SE(3)-Assembly: 0.233/52.34）。
- 在 Plug、Key 等高难度任务上提升尤为明显（Plug 旋转 RMSE 从 18.58 降至 9.74）。
- **关键发现**：
  1. **分离预测两物体位姿**比联合预测能有效避免误差互相干扰。
  2. **SE(3) 等变特征**显著提升样本效率与对细微旋转/平移变化的敏感性。
  3. **两尺度 VN-DGCNN** 优于单尺度 VN-DGCNN、DGCNN、PointNet。
- **真机泛化**：在 4 个未见过真实物体的任务上总成功率 77.5%（SE(3)-Assembly 仅 22.5%）。

## 7. 优点

- **数据集贡献突出**：
  - 首个大规模日常两物体装配基准，填补了日常装配与现有碎片拼合数据集之间的空白。
  - 包含规范位姿、对称性、语义功能等丰富标注；测试集刻意包含未见过的新几何形状。
  - 与 6 个现有数据集（PartNet、AutoMate、JoinABLe、NSM、Breaking Bad、Factory）对比维度全面（类别数、形状数、任务数、对称性、实际意义等）。
- **方法设计新颖且符合直觉**：
  - "先放底座再插零件"的两步式设计高度契合人类装配认知。
  - 两尺度 VN-DGCNN 兼顾局部与全局几何信息。
  - 跨物体逐点乘法融合兼顾等变性与信息融合。
  - 独立 MLP 头分别预测平移与旋转，考虑了二者收敛速度差异。
- **实验较为充分**：
  - 同时包含单任务、跨任务、全任务、定量、定性、真机实验。
  - 消融研究覆盖编码器与训练策略两个核心组件。
- **真机验证**提升了工作的实际应用价值与可信度。

## 8. 不足与局限

- **数据集层面**：
  - 仅包含**成对（pairwise）**装配，不支持多部件（multi-part）装配任务。
  - 仅使用**仿真/合成 3D 网格**，未包含真实扫描点云，对真实传感器噪声、遮挡、背景的鲁棒性仍需更多验证。
  - 测试集虽包含未见过形状，但类别内分布差异有限（Figure 3 仅展示 4 个任务），跨域（如不同品牌、风格）泛化能力未知。
- **方法层面**：
  - 测试阶段依赖 Branch B 的位姿预测精度；若 $O_B$ 预测偏差大，会直接级联影响 $O_A$，两步设计虽缓解但未消除此误差传播问题。
  - 对称性信息仅作为后处理评估指标，未显式编码进网络结构以利用对称性先验。
  - 对**严重遮挡**或**部分点云**（如物体被部分遮挡）情况未作评估。
- **实验层面**：
  - 缺少**统计显著性分析**（多次随机种子运行的均值±方差）。
  - 未报告计算资源、训练时长等可复现性信息。
  - 真机实验仅 4 个任务、每任务 10 次试验，样本量偏小，且仅以 SE(3)-Assembly 为单一基线。
  - 未与近期 6D 位姿估计领域（如 FoundationPose、GSPose 等）做对比。
- **应用层面**：
  - 假设物体已被分割为独立点云，未解决从杂乱场景中检测、分割与位姿估计的**端到端**流程。
  - 真实机器人使用人工设计的抓取姿态，并非完全自主的抓取-装配一体化方案。

（完）
