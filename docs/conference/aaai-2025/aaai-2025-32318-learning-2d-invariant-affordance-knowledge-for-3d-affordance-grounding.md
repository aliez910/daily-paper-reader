---
title: Learning 2D Invariant Affordance Knowledge for 3D Affordance Grounding
title_zh: 基于二维不变可供性知识学习的三维可供性定位
authors: "Xianqiang Gao, Pingrui Zhang, Delin Qu, Dong Wang, Zhigang Wang, Yan Ding, Bin Zhao"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/32318/34473"
tags: ["query:rob-il"]
score: 4.0
evidence: 三维可供性定位为机器人操纵交互提供感知基础
tldr: 针对三维可供性定位中训练物体与人类交互图像几何结构不一致导致泛化能力差的问题，本文提出 MIFAG 框架，从同类可供性的多张人-物交互图像中学习二维不变的可供性知识，并迁移到三维物体上完成功能区域预测。该方法有效缓解了因视角与形状差异带来的过拟合问题。在多个三维物体可供性基准上的实验表明，其在新物体与新交互类别上的预测准确率显著优于单图像监督方法。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32318/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 879, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32318/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1839, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32318/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1835, \"height\": 929, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32318/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 825, \"height\": 787, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32318/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 880, \"height\": 917, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32318/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1841, \"height\": 435, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32318/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 873, \"height\": 404, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32318/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 870, \"height\": 488, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32318/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 430, \"label\": \"Table\"}]"
motivation: 单张人-物交互图像与三维物体几何不一致，限制了三维可供性定位的泛化能力。
method: MIFAG 从同类可供性的多张二维交互图像中学习不变特征，用于指导三维物体的功能区域预测。
result: 在新物体和新交互类别上的三维可供性预测准确率明显提升。
conclusion: 为机器人操纵中物体可供性感知提供了更鲁棒的跨视角泛化方案。
---

## Abstract
3D Object Affordance Grounding aims to predict the functional regions on a 3D object and has laid the foundation for a wide range of applications in robotics. Recent advances tackle this problem via learning a mapping between 3D regions and a single human-object interaction image. However, the geometric structure of the 3D object and the object in the human-object interaction image are not always consistent, leading to poor generalization. To address this issue, we propose to learn generalizable invariant affordance knowledge from multiple human-object interaction images within the same affordance category. Specifically, we introduce the Multi-Image Guided Invariant-Feature-Aware 3D Affordance Grounding (MIFAG) framework. It grounds 3D object affordance regions by identifying common interaction patterns across multiple human-object interaction images. First, the Invariant Affordance Knowledge Extraction Module (IAM) utilizes an iterative updating strategy to gradually extract aligned affordance knowledge from multiple images and integrate it into an affordance dictionary. Then, the Affordance Dictionary Adaptive Fusion Module (ADM) learns comprehensive point cloud representations that consider all affordance candidates in multiple images. Besides, the Multi-Image and Point Affordance (MIPA) benchmark is constructed and our method outperforms existing state-of-the-art methods on various experimental comparisons.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper following a specific structure. Let me analyze the paper carefully and produce the summary.

The paper is about "Learning 2D Invariant Affordance Knowledge for 3D Affordance Grounding" - it proposes MIFAG framework for 3D object affordance grounding using multiple human-object interaction images.

Let me organize the summary according to the 8 requested points.</think>

# 论文总结：基于二维不变可供性知识学习的三维可供性定位

## 1. 核心问题与研究背景

- **任务定义**：3D 物体可供性定位（3D Object Affordance Grounding）旨在预测 3D 物体点云上的功能交互区域，是连接视觉感知与物理操作的关键基础任务。
- **现有方法的局限**：当前主流方法（如 IAGNet、LASO）通常仅将 3D 区域与**单张**人-物交互图像进行映射，忽略了同类可供性下多张参考图像所蕴含的共性与不变知识。
- **核心痛点**：
  - 单张图像与 3D 物体在几何结构上常不一致（如不同品牌的烤箱尺寸、把手位置差异显著），导致模型易过拟合于特定视角/形状。
  - 单纯文本描述（如"打开烤箱"）信息量不足；多张图像外观差异大，直接拼接也难以利用。
- **论文动机**：同一可供性类别下的多张人-物交互图像虽然外观差异大，但共享不变的可供性知识与内部关联，可提供跨上下文的鲁棒指导。

## 2. 方法论

### 2.1 整体框架 MIFAG
由两大模块串联组成：
1. **不变可供性知识提取模块（IAM）**：从多张图像中渐进提取不变知识。
2. **可供性字典自适应融合模块（ADM）**：将不变知识融入点云表征，预测功能区域。

### 2.2 不变可供性知识提取模块（IAM）
- **核心思想**：采用**多层迭代 + 双分支结构**，使可供性查询 token 与图像特征在迭代中相互促进、逐步对齐。
- **双分支构成**：
  - **Affordance Knowledge Branch（可供性知识分支）**：维护 M 个可学习的可供性查询 token $Q$。
  - **Image Feature Branch（图像特征分支）**：基于 ResNet 编码的图像特征 $F$。
- **关键流程**（逐层迭代）：
  - 知识分支：通过多头交叉注意力（MCA）将查询与图像特征交互，更新 $Q_i^{(l)}$（公式 1）。
  - 知识聚合：用 MLP 对多张图像的查询进行对齐聚合，得到统一查询 $Q_f^{(l)}$（公式 2）。
  - 图像分支：用多头自注意力（MSA）更新图像特征 $\bar{F}^{(l-1)}$（公式 3），再以 $Q_f^{(l)}$ 为 KV，通过 MCA 注入可供性信息得到 $F_i^{(l)}$（公式 4）。
- **约束**：每层计算多张图像特征间的**余弦相似度损失**，强制不同图像在同一可供性类别下保持一致。
- **输出**：最后一层知识分支的输出构成**不变可供性知识字典**（Invariant Affordance Knowledge Dictionary）。

### 2.3 可供性字典自适应融合模块（ADM）
- **核心思想**：以点云特征为查询、以不变可供性字典为键值，通过**自适应跨注意力**实现 2D 知识向 3D 表征的迁移。
- **关键算子 IQDCA（Invariant-aware Query Dictionary Cross-Attention）**：
  - 点云特征 $P_{in}$ 经投影得到查询 $Q_P$（公式 5）。
  - 字典中每个 token 经 $W_k$、$W_v$ 投影生成多组 $K_{ID}$、$V_{ID}$（公式 6-7）。
  - 通过**余弦相似度**计算字典注意力矩阵 $A = \text{Softmax}(\text{SimCos}(Q_P, K_{ID}))$（公式 8），加权得到 $P_q$（公式 9）。
- **自加权注意力（SWA）**：在多张图像的加权结果上应用 SWA，丢弃不相关 token，得到 $P_{mix}$（公式 10），与原始点云特征拼接后送入解码器。

### 2.4 损失函数
- 总损失：$L_{total} = \lambda_1 L_{CE} + \lambda_2 L_{Sim} + \lambda_3 L_{HM}$
  - $L_{CE}$：图像级可供性分类的交叉熵损失。
  - $L_{Sim}$：各层图像特征间的余弦相似度损失。
  - $L_{HM}$：点云热图损失（Focal Loss + Dice Loss），监督点级可供性预测。

## 3. 实验设计

### 3.1 新构建的数据集 MIPA
- **数据来源**：点云与标注取自 3D AffordanceNet；多张配对图像来自 IAGNet、HICO、AGD20K。
- **规模**：5,162 张图像 + 7,012 个点云，涵盖 23 个物体类别和 17 个可供性类别。
- **评测划分**：seen（训练/测试类别相同）与 unseen（类别不同）两种设置。

### 3.2 对比方法
- 跨模态/3D 分割基线：PMF、XMF、MBDF、FRCNN、ILN、PFusion。
- 可供性领域 SOTA：IAGNet（单图像监督）、LASO（语言引导）。
- 复现时将这些方法的多图像/文本输入对齐到 MIPA 设定，便于公平比较。

### 3.3 评测指标
AUC、aIOU、SIM、MAE（沿用 IAGNet/LASO 标准）。

### 3.4 消融实验
- IAM 与 ADM 的组合消融。
- 输入图像数量（1–5）的消融。
- IAM 迭代层数（1–6）的消融。

### 3.5 真实场景验证
使用 iPhone 15 Pro + LiDAR 扫描真实物体点云，输入训练好的模型测试零样本泛化能力（包含 seen 与 unseen 物体，如训练集中没有的"沙发"）。

## 4. 资源与算力

- **GPU**：单卡 NVIDIA **A100**。
- **Batch size**：64。
- **优化器与学习率**：Adam，lr = 4e-5。
- **其他**：使用 PointNet++ 作为 3D backbone，ResNet-18 作为 2D backbone。
- **训练时长**等更细节设置未在正文给出，被指引至补充材料（arXiv:2408.13024）。

## 5. 实验数量与充分性

- **主表实验** 1 组：MIPA 数据集 seen + unseen 两类设置下的 8 种方法对比。
- **消融实验** 3 组：IAM/ADM 组合、图像数量、迭代层数。
- **定性分析** 2 组：3D 可供性可视化 + t-SNE 查询 token 聚类可视化。
- **真实场景实验** 1 组：iPhone LiDAR 扫描的 seen/unseen 物体测试。
- **总体评价**：
  - 优点：覆盖了定量、定性、消融、真实场景四个维度，比较全面。
  - 不足：未见对训练时长、收敛曲线、显著性检验等的报告；未见在其它公开数据集（如 LASO 用的 PIAD 等）上的交叉验证，泛化结论可能受限于 MIPA 自建数据集；基线复现细节描述较为简略。

## 6. 主要结论与发现

- **SOTA 性能**：在 MIPA 上，seen AUC 85.10、aIOU 20.50；unseen AUC 71.13、aIOU 5.23，均超越 IAGNet 和 LASO。
- **多图像有效性**：图像数量从 1 增加到 5 时，seen 设置下 AUC 从 83.33 提升到 85.47；但 unseen 设置下过多图像反而可能引入干扰（aIOU 从 4.72 降至 4.49）。
- **迭代层数**：seen 最佳为 4 层，unseen 最佳为 6 层，过多层数会因相似度损失放大导致训练不稳定。
- **t-SNE 验证**：不同物体上相同操作（如"打开门/微波炉/包"）的查询 token 会在特征空间中聚类，证明 IAM 有效提取了类别级不变知识。
- **真实场景**：扫描的 seen/unseen 物体均能给出合理预测，展示零样本泛化潜力。

## 7. 优点与亮点

- **问题切入精准**：针对"单图像监督带来的过拟合与几何不一致"这一明确痛点，提出从多图像提取不变知识的新视角。
- **双分支 + 迭代更新设计**：通过 MLP 聚合 + 跨分支交叉注意力实现知识与图像特征的协同进化，避免简单拼接带来的外观干扰。
- **字典化融合 IQDCA**：将提取的不变知识组织为可查询字典，配合余弦相似度与自加权注意力，提升了知识到点云的迁移效率。
- **新基准 MIPA**：填补了"多图像 + 点云"可供性数据集的空白，对后续研究有参考价值。
- **真实场景验证**：用消费级 LiDAR 设备实测，增强了方法的实用可信度。
- **可视化充分**：t-SNE 聚类与 3D 可供性热图直观展示了模块效果。

## 8. 不足与局限

- **数据集规模与多样性有限**：5,162 张图像和 7,012 个点云虽具规模，但 23 个物体类别仍相对单薄；3D 物体多为简单几何，难以代表真实复杂场景。
- **缺乏任务扩展**：方法聚焦于视觉可供性理解，未考虑操作维度（机械手尺寸、操作方向、力反馈等），离真实机器人操作尚有距离。
- **超参数敏感**：图像数量、迭代层数在 seen 与 unseen 上最优值不一致，需要根据场景挑选；超参数 $\lambda_1, \lambda_2, \lambda_3$ 的选择与敏感性未充分讨论。
- **算力与时长信息缺失**：未公布训练时长、收敛曲线、显存占用等，对复现者不够友好。
- **公平性顾虑**：将原方法的单图像输入"强行替换为多图像"作为对比基线，可能未触及这些方法的最佳配置，对结论的公平性存在一定风险。
- **评测全面性不足**：未在 3D AffordanceNet 原始 split 或其它公开基准上做交叉验证，难以判断在 MIPA 上的提升是否可迁移到其它数据划分。
- **类别不平衡与失败案例**：未对失败案例做系统分析，也未对 17 类可供性分别报告指标，难以识别方法的薄弱子类别。

（完）
