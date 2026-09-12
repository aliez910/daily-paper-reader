---
title: "RAGrasp: A Retrieval-Augmented Framework with Diversity-Aware Modeling for Dexterous Grasp Generation"
title_zh: RAGrasp：面向灵巧抓取生成的检索增强多样性感知框架
authors: "Zhuo Yang, Sanping Zhou, Sen Wang, Jingyi Tian, lijiayi lijiayi, Gang Hua, Le Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/1642.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向机器人操纵任务的灵巧抓取生成
tldr: 灵巧抓取是机器人完成复杂操纵任务的关键能力，但同时提升抓取成功率与抓取类型多样性仍是难题。本文提出检索增强框架RAGrasp，包含几何感知手部姿态初始化与多样性感知抓取类型选择两个核心模块。该方法通过检索高质量样本并显式建模抓取多样性，显著提升了复杂操纵场景下的抓取质量与类型丰富度。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1380, \"height\": 494}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 1391, \"height\": 757}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-003.webp\", \"caption\": \"\", \"page\": 10, \"index\": 3, \"width\": 1852, \"height\": 365}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-004.webp\", \"caption\": \"\", \"page\": 12, \"index\": 4, \"width\": 1868, \"height\": 730}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-005.webp\", \"caption\": \"\", \"page\": 13, \"index\": 5, \"width\": 1800, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2a136fe4429e93eee96ef36c/fig-006.webp\", \"caption\": \"\", \"page\": 14, \"index\": 6, \"width\": 1394, \"height\": 374}]"
motivation: 灵巧抓取生成需同时兼顾抓取成功率和抓取类型多样性，传统方法难以平衡。
method: 提出几何感知初始化与多样性感知选择网络的检索增强双头分类框架。
result: 在标准灵巧抓取基准上显著提升了抓取成功率并保持了抓取多样性。
conclusion: 为复杂操纵任务提供了高质量且多样化的灵巧抓取解决方案。
---

## Abstract
Dexterous grasping is a fundamental ability for robots toperform complex manipulation tasks. However, simultaneously maximiz-ing grasp success rates and maintaining grasp-type diversity remains asignificant challenge. In response, we introduce RAGrasp, a retrieval-augmented framework that comprises two core components: a Geometry-Aware hand pose Initialization strategy(GAI) and a Diversity-Awaregrasp-type Selection network(DAS). First, GAI constructs a distribution-aligned retrieval dataset and leverages object geometric similarity toretrieve high-quality initial samples, significantly improving grasp suc-cess rates. Second, DAS adopts a retrieval-augmented dual-head classi-fier that formulates grasp-type selection as a collaborative optimizationproblem of single-label and multi-label grasp-type classification, improv-ing diversity and allowing flexible diversity adjustment. Extensive experi-ments show that RAGrasp yields an 8.2% relative improvement in successrate on BODex, alongside average relative gains of 13.0% and 11.9% onDexonomy under type-unconditioned and type-conditioned settings.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "RAGrasp: A Retrieval-Augmented Framework with Diversity-Aware Modeling for Dexterous Grasp Generation" following a specific structured format. Let me analyze the paper carefully and produce the summary.

Key points from the paper:
1. Problem: Dexterous grasping needs both high success rate and grasp-type diversity - currently hard to balance
2. Method: RAGrasp with two components:
   - GAI (Geometry-Aware hand pose Initialization): Uses Möbius normalizing flow, retrieves model-generated successful grasps instead of ground truth
   - DAS (Diversity-Aware grasp-type Selection network): Dual-head classifier - multi-label for diversity, single-label for fallback
3. Experiments: BODex and Dexonomy datasets, Shadow Hand in MuJoCo
4. Resources: Single NVIDIA RTX 3090 GPU
5. Results: 8.2% relative improvement on BODex, 13.0% on Dexonomy type-unconditioned, 11.9% type-conditioned
6. Real-world: Leap hand on Franka Research 3, 70% success rate on 10 objects × 3 trials

Let me structure this properly in Chinese with Markdown formatting.</think>

# RAGrasp 论文总结

## 1. 核心问题与研究动机

- **背景**：灵巧抓取（Dexterous Grasping）是机器人执行复杂操纵任务的基础能力，需从单视角部分点云生成多指手（ShadowHand，22 DoF）的完整抓取姿态。
- **两大挑战**：
  1. **抓取成功率**：现有生成式与混合方法对**手部姿态初始化策略**关注不足，随机初始样本难以保证物理可行的抓取。
  2. **抓取类型多样性**：现有抓取类型分类器仅预测单一最可能类型，导致多模态可行抓取模式坍缩为单一模式，多样性受限。
- **目标**：同时**最大化抓取成功率**与**保持抓取类型多样性**，并支持灵活调节多样性与成功率的权衡。

---

## 2. 方法论

### 整体框架（RAGrasp）

检索增强框架，包含两个核心组件：**GAI（几何感知手部姿态初始化策略）** 和 **DAS（多样性感知抓取类型选择网络）**。

### 关键技术一：GAI（Geometry-Aware hand pose Initialization）

- **核心思想**：用 Möbius Normalizing Flow 在 SO(3) 流形上建模手部全局旋转分布，并通过对齐检索分布的初始样本，提高生成质量。
- **关键步骤**：
  1. **点云补全**：用 SymmCompletion 网络从部分观测重建完整点云，提升检索稳健性。
  2. **姿态生成模型训练**：以 Sparse 3D Conv（MinkowskiEngine）+ Codebook 编码抓取类型，生成 squeeze pose 的旋转 $R_s \in SO(3)$、平移 $t_s \in \mathbb{R}^3$ 及关节角 $\theta_s$。
  3. **抓取数据收集（核心创新）**：用训练好的模型为每个训练对象生成候选抓取，再经物理仿真过滤，构造成功抓取集 $D_{succ}$。**关键点：使用模型生成的成功抓取而非数据集真值**，避免分布失配。
  4. **物体相似性检索**：对测试对象 $i$，计算其特征 $f_i^{test}$ 与所有训练对象特征的欧氏距离，按升序排序，取最相似的若干对象的成功抓作为检索集 $S_i^{retr}$。
  5. **检索增强初始化**：将检索到的 $(R_s^{succ}, t_s^{succ}, E_j, P_j^{pred})$ 通过反变换映射到流模型的潜空间：
     $$
     (z_s^{rot}, z_s^{trans}) = (f_K^{-1} \circ \cdots \circ f_1^{-1})(R_s^{succ}, t_s^{succ}; E_j; P_j^{pred})
     $$
     作为几何对齐的初始样本，再前向生成测试对象的最终姿态。
- **Möbius Normalizing Flow 公式**：
  - 球面上的 Möbius 变换：$f_\omega(c) = \frac{1-\|\omega\|^2}{\|c-\omega\|^2}(c-\omega) - \omega$
  - 四元数的仿射变换：$g(q) = \frac{Wq}{\|Wq\|}$

### 关键技术二：DAS（Diversity-Aware grasp-type Selection）

- **核心思想**：将抓取类型选择建模为**单标签与多标签分类的协同优化问题**。
- **双头架构**：
  - **多标签头**（BCE Loss）：预测每种抓取类型成功率是否超过阈值 $\tau$，超阈值则随机选取 → 提升多样性。
  - **单标签头**（CE Loss）：预测最可能抓取类型，作为**回退机制**——当多标签头所有概率均低于 $\tau$ 时启用，保证成功率。
- **多样性调节**：阈值 $\tau$ 越低，激活的抓取类型越多，多样性越高；阈值越高，成功率越高。
- **自适应特性**：几何简单对象激活多类型（多样性），困难对象回退到最可能模式（成功率）。

---

## 3. 实验设计

### 数据集
- **BODex**：240 万指抓取，2.4k 物体，单一抓取类型，单视角部分点云。
- **Dexonomy**：950 万抓取，10.7k 物体，31 种抓取类型（基于人类抓取分类法），多类型数据集。

### 仿真环境
- **MuJoCo** + **ShadowHand**（BODex）/ **Leap Hand**（真实实验）。

### 评估指标
- **GSR**：抓取成功率（6 个外力扰动下不穿透）。
- **OSR**：对象成功率。
- **PD**：穿透深度；**CDC**：接触距离一致性；**SPD**：自穿透深度。
- **D (Diversity)**：基于 PCA 第一主成分解释方差的比例。

### 对比方法
- **BODex**：ISAGrasp、GraspTTA、DP3、UniDexGrasp。
- **Dexonomy**：Dexonomy 提供的 Diffusion 与 nflow 基线。

---

## 4. 资源与算力

- **GPU**：单张 **NVIDIA RTX 3090**。
- **训练配置**：batch size = 256，初始学习率 0.001 → 0.0001，梯度裁剪阈值 10。
- **推理配置**：每对象采样 100 个候选抓取，按似然选取 Top 10。
- **真实机器人**：Leap Hand + Franka Research 3 机械臂 + Orbbec Femto Bolt 深度相机。
- **说明**：论文**未明确报告总训练时长**，仅给出训练迭代次数（图中显示 1 万–5 万次迭代区间）。算力描述较为粗略。

---

## 5. 实验数量与充分性

### 实验数量（共约 8 组主要实验）
1. **BODex 定量对比**（Tab. 1）：4 个基线 + 本方法。
2. **Dexonomy 类型条件设定**（Tab. 2）：2 种模式（diversity / success）。
3. **Dexonomy 类型非条件设定**（Tab. 3）：31 种抓取类型细分对比。
4. **GAI 消融实验**（Tab. 4）：4 种配置（Base / +Comp / +Comp+Ret / +Comp+Data+Ret），验证补全、检索、数据收集模块的贡献。
5. **训练过程曲线**（Fig. 5）：10 种代表性抓取类型训练迭代过程对比。
6. **DAS 阈值消融**（Fig. 6）：分析阈值对成功率和多样性的影响。
7. **可视化结果**（Fig. 3, Fig. 4）：BODex 与 Dexonomy 上的生成抓取姿态可视化。
8. **真实机器人实验**：10 个物体 × 3 次试验，整体成功率 70%。

### 充分性评估
- **优点**：覆盖了两个主流大规模基准，多项指标，消融完整，含真实机器人验证。
- **不足**：
  - **真实实验样本量小**（仅 10 物体 × 3 次 = 30 次抓取），统计意义有限。
  - **未报告训练时长与完整超参搜索细节**。
  - **DAS 仅基于阈值消融**，未做更细粒度的多标签/单标签 head 单独消融。
  - **未在更复杂场景（如遮挡、杂乱、动态物体）下验证**。

---

## 6. 主要结论与发现

- **BODex**：GSR 达 **86.7%**，相对次优方法（UniDexGrasp 80.1%）提升 **8.2% 相对 / 6.6% 绝对**，PD 最低，SPD 与最佳持平。
- **Dexonomy 类型非条件**：平均成功率 **39.1%**，相对提升 **13.0% 相对 / 4.5% 绝对**，在 Large Diameter、Prismatic 4 Finger、Precision Sphere 等代表性抓取上提升显著。
- **Dexonomy 类型条件**：success 模式下 GSR 达 **71.5%**，相对提升 **11.9% 相对 / 7.6% 绝对**；diversity 模式下 D 指标最佳（25.5）。
- **GAI 消融**：使用真值数据集进行检索（Base+Comp+Ret）反而性能下降，验证了**模型生成抓取构建检索库**对消除分布失配的必要性。
- **DAS 阈值**：$\tau = 1.0$ 时实现成功率与多样性的最佳平衡。
- **真实机器人**：10 物体 × 3 次试验达到 70% 成功率，证明迁移可行性。

---

## 7. 优点

- **方法新颖性**：
  - 首次将**检索增强生成（RAG）** 引入基于 Normalizing Flow 的灵巧抓取生成。
  - 提出**分布对齐的检索库构建**策略（用模型生成的成功抓取而非数据集真值），有效消除训练-推理分布失配。
- **多样性可控**：DAS 通过双头 + 阈值机制实现**灵活性强、可解释的多样性调节**。
- **模块化设计**：GAI 与 DAS 各自独立，可单独使用或组合。
- **充分消融**：对 GAI 各组件（补全、检索、数据收集）进行细致拆解，验证各部分贡献。
- **跨数据集验证**：BODex（单类型）与 Dexonomy（31 类型）两种截然不同的设定均验证有效。
- **真实实验**：补充物理机器人验证，增强可信度。

---

## 8. 不足与局限

- **真实实验规模小**：仅 10 物体 × 3 次试验，统计意义有限，未涵盖多样物体类型与复杂场景。
- **计算资源报告不充分**：未提供训练时长、收敛迭代数、能耗等详细指标，仅给出单卡 3090 配置。
- **依赖点云补全网络**：GAI 性能部分依赖于补全网络质量，若补全失败将影响检索。
- **检索库静态**：检索集在训练时构建，**无法随新物体/新场景在线更新**，限制了在线部署能力。
- **桌面场景适配需后处理**：真实实验中需手动滤除与桌面/物体的碰撞，运动规划辅助降低自动化程度。
- **跨手型泛化未充分验证**：仿真用 ShadowHand，真实用 Leap Hand，**未在同一设定下系统对比不同手型泛化能力**。
- **多样性评估维度单一**：D 指标仅基于 PCA 第一主成分方差解释比例，未涵盖抓取类型分布熵、接触点多样性等多维度度量。
- **基线范围有限**：未与最新的基于 3D 基础模型或大规模预训练的抓取方法（如 DexVLG、UniGraspTransformer 等）对比。
- **失败案例分析缺失**：未系统展示失败抓取的典型模式（如指节干涉、特定物体类型失败等），影响后续改进方向的指导性。

（完）
