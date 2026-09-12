---
title: "LARY: A Latent Action Representation Yielding Benchmark"
title_zh: LARY：潜在动作表示的产出基准
authors: "Dujun Nie, Fengjiao Chen, Jun Kuang, Qi Lv, Xiaoyu Li, Xuezhi Cao"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/8585.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 用于评估VLA潜在动作表示的机器人控制基准
tldr: 显式动作数据的匮乏限制了视觉-语言-动作模型的规模扩展，而海量人类视频提供了未标注数据源，但从中提取本体无关的潜在动作表示并验证其对视觉到控制映射能力的有效性仍是关键挑战。本文提出LARY基准，构建统一评估框架，同时衡量高层语义动作与低层机器人控制，覆盖超百万视频片段，并在多平台上系统比较潜在动作表示方法，从而推动基于人类视频的VLA模仿学习规模化评测。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 463, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 462, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 487, \"height\": 285}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 1062, \"height\": 537}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 612, \"height\": 247}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-012.webp\", \"caption\": \"\", \"page\": 1, \"index\": 12, \"width\": 480, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-013.webp\", \"caption\": \"\", \"page\": 1, \"index\": 13, \"width\": 480, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-014.webp\", \"caption\": \"\", \"page\": 1, \"index\": 14, \"width\": 480, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-015.webp\", \"caption\": \"\", \"page\": 1, \"index\": 15, \"width\": 480, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-016.webp\", \"caption\": \"\", \"page\": 5, \"index\": 16, \"width\": 480, \"height\": 288}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-017.webp\", \"caption\": \"\", \"page\": 5, \"index\": 17, \"width\": 1200, \"height\": 655}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-018.webp\", \"caption\": \"\", \"page\": 5, \"index\": 18, \"width\": 480, \"height\": 288}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-019.webp\", \"caption\": \"\", \"page\": 5, \"index\": 19, \"width\": 4161, \"height\": 1918}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-020.webp\", \"caption\": \"\", \"page\": 5, \"index\": 20, \"width\": 1200, \"height\": 655}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-021.webp\", \"caption\": \"\", \"page\": 6, \"index\": 21, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-022.webp\", \"caption\": \"\", \"page\": 6, \"index\": 22, \"width\": 500, \"height\": 500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-023.webp\", \"caption\": \"\", \"page\": 12, \"index\": 23, \"width\": 3520, \"height\": 1135}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-024.webp\", \"caption\": \"\", \"page\": 13, \"index\": 24, \"width\": 3577, \"height\": 1173}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7edb8300ea6d0f09ecaa10db/fig-025.webp\", \"caption\": \"\", \"page\": 14, \"index\": 25, \"width\": 1559, \"height\": 344}]"
motivation: 显式动作数据稀缺使VLA难以扩展，人类视频中的潜在动作表示亟需严格评测。
method: 构建统一基准框架，从百万级人类视频中评估高层语义与低层控制两类动作表示。
result: 提供大规模基准并系统比较潜在动作方法对机器人控制的迁移能力。
conclusion: 为基于潜在动作的VLA模仿学习建立了标准化评测基准。
---

## Abstract
While the shortage of explicit action data limits VisionLanguage-Action (VLA) models, human action videos offer a scalable yet unlabeled data source. A critical challenge in utilizing large-scale human video datasets lies in transforming visual signals into ontologyindependent representations, known as latent actions. However, the capacity of latent action representation to derive robust control from visual observations has yet to be rigorously evaluated. We introduce the Latent Action Representation Yielding (LARY) Benchmark, a unified framework for evaluating latent action representations on both highlevel semantic actions (what to do) and low-level robotic control (how to do). The comprehensively curated dataset encompasses over one million videos (1,000 hours) spanning 151 action categories, alongside 620K image pairs and 595K motion trajectories across diverse embodiments and environments. Our experiments reveal two crucial insights: (i) General visual foundation models, trained without any action supervision, consistently outperform specialized embodied latent action models. (ii) Latent-based visual space is fundamentally better aligned to physical action space than pixel-based space. These results suggest that general visual representations inherently encode action-relevant knowledge for physical control, and that semantic-level abstraction serves as a fundamentally more effective pathway from vision to action than pixel-level reconstruction.

---

## 论文详细总结（自动生成）

<think>The user wants a structured, detailed Chinese summary of the paper "LARY: A Latent Action Representation Yielding Benchmark" following specific outline points. Let me analyze the paper carefully and produce a comprehensive summary.

Let me go through each section:

1. Core problem and motivation: VLA models limited by explicit action data scarcity; need to evaluate latent action representations from human videos.

2. Methodology: LARYBench framework, two evaluation dimensions (semantic classification + control regression), data engine for curation.

3. Experiments: 11 models, datasets, tasks.

4. Resources: Not explicitly mentioned.

5. Experiment count and adequacy: Many ablations, comparisons.

6. Main conclusions: General vision encoders outperform embodied LAMs; latent space aligns with action space better than pixel space.

7. Strengths: Decoupling evaluation, large-scale dataset, comprehensive comparison.

8. Limitations: Limited robot action data for General LAMs, etc.

Let me write this out in Markdown format in Chinese.</think>

# LARY：潜在动作表示的产出基准 — 论文总结

## 1. 核心问题与研究动机

- **VLA 模型的"数据孤岛"困境**：Vision-Language-Action 模型依赖大规模带标签的机器人遥操作数据，但此类数据采集成本高、规模有限，难以支撑通用基础模型的训练。
- **人类视频的潜力与挑战**：海量未标注的人类动作视频是潜在的数据源，核心难题在于如何将视觉信号转化为"本体无关（ontology-agnostic）"的**潜在动作（latent action）**表示。
- **评测缺位**：现有的潜在动作模型（LAPA、Moto、UniVLA、IGOR 等）大多依赖下游操控任务表现或聚类可视化来间接评估，无法剥离 VLA 其他组件的干扰，缺少跨实体、跨任务、跨粒度的统一评测框架。
- **关键疑问未解**：不同训练架构与策略对潜在动作表示质量的影响，以及"从视觉到控制"的有效路径（高层语义抽象 vs. 像素级重建）仍缺乏系统比较。

## 2. 方法论

### 2.1 整体框架 LARYBench

- **形式化定义**：给定观测序列 $o_{1:T}$，潜在动作模型提取 $z \in \mathcal{Z}$，通过两个任务评估：
  - 语义解码 $f_{\text{sem}}: \mathcal{Z} \to \mathcal{C}$（动作分类）
  - 物理控制 $f_{\text{dyn}}: \mathcal{Z} \to \mathcal{A}$（轨迹回归）

### 2.2 双维度评估

- **高层语义理解**（what to do）：
  - **运动学原子基元**（Kinematic-Level Atomic Primitives）：基于 LIBERO 套件，通过阈值化末端执行器运动，提取 28 个原子动作类，生成约 25,940 张图像对+轨迹。
  - **任务级复合行为**（Task-Level Composite Behaviors）：145 个复合类，覆盖 692,297 段人类片段与 538,423 段机器人片段。
- **低层物理控制**（how to do）：在 CALVIN、VLABench（Franka 7-DoF）、RoboCOIN（10 平台，12-DoF）、AgiBotWorld-Beta（16-DoF）等 4 个机器人数据集上回归末端执行器轨迹。

### 2.3 自动化数据引擎

- 基于 **Doubao-1.5-pro-vision API** 的 VLM 进行时空视频理解和语义对齐。
- 流程：动作分割 → 视频–动词一致性检查 → 视频–描述匹配 → 手动采样检验 → 对机器人数据额外进行轨迹分析与运动标签提取。
- 支持未来数据流的持续扩展。

### 2.4 四类表示范式（被评测对象）

1. **Embodied LAM**：LAPA、UniVLA、villa-X（专为机器人操控设计）。
2. **通用语义编码器**：DINOv3、V-JEPA 2 / 2.1（对比学习/潜在级重建）。
3. **生成式像素编码器**：Wan2.2 VAE、FLUX.2-dev VAE（像素级重建）。
4. **通用潜在动作模型（General LAM，本文新提出）**：将 LAPA 的 VQ-VAE 框架嫁接到冻结的通用视觉骨干上，包括 LAPA-DINOv2、DINOv3、SigLIP2、MAGVIT2。

### 2.5 评测协议细节

- **采样策略**：复合任务使用 Motion-Guided Sampler（MGSampler）选取动态显著的帧序列；原子与回归任务使用固定间隔的图像对。
- **分类探针**：4 层 attentive probe + projector 对齐，统一输入 9 帧 224×224，bfloat16 训练 20 epoch，使用多 head 学习率（3e-4 ~ 5e-3）与权重衰减（0.01~0.8）。
- **回归专家**：2 个残差块、隐藏维度 4096 的 MLP，输入图像对间隔 s=5，输出 7/12/16-DoF 的 action chunk。

## 3. 实验设计

### 3.1 数据集

| 数据来源 | 用途 | 规模 |
|---|---|---|
| LIBERO | 原子动作分类 | 25,940 图像对 |
| Ego4D、HoloAssist、SSv2、TACO、EPIC-KITCHENS、EgoDex | 复合人类动作 | 692,297 视频 |
| AgiBotWorld-Beta | 复合机器人动作 | 538,423 视频 |
| CALVIN、VLABench | 单臂控制回归（Franka 7-DoF） | — |
| RoboCOIN | 双臂控制回归（10 平台，12-DoF） | 273K+ 图像对&轨迹 |
| AgiBotWorld-Beta | 双臂控制回归（16-DoF） | 321K+ 图像对&轨迹 |

总计 **120 万+ 视频片段、620K 图像对、595K 轨迹**，覆盖 11 种机器人平台 + 人类，跨越家庭、工厂、商店、厨房等多场景。

### 3.2 对比方法（共 11 个模型）

- **Embodied LAM**：LAPA、UniVLA、villa-X
- **通用语义编码器**：V-JEPA 2、V-JEPA 2.1、DINOv3、SigLIP2
- **生成式像素编码器**：Wan2.2 VAE、FLUX.2-dev VAE
- **General LAM（本文）**：LAPA-MAGVIT2、LAPA-SigLIP2、LAPA-DINOv2、LAPA-DINOv3

### 3.3 评估指标

- **分类**：Top-1 准确率（按类别平均）。
- **回归**：归一化 MSE；附录中另报告 `phys_vector_mse`、`phys_se3_mse`、`phys_balanced_mse`。
- 回归分**绝对（Absolute）** 与 **相对增量（Delta）** 两种动作形式。

## 4. 资源与算力

- **论文中未明确披露**训练与评测所用的 GPU 型号、数量及训练时长。
- 仅提到 General LAM 训练时"编码器权重保持冻结，潜在动作在内部视频数据集上从头学习"，并表示"详细训练配置见附录"，但本文提供的 PDF 文本中未见附录中的算力信息。
- 评测阶段提到 bfloat16 精度训练 20 epoch，未给出硬件配置。

## 5. 实验数量与充分性

- **分类任务**：1 张主表覆盖 4 个子任务（原子、复合人类、复合机器人、平均）×11 个模型。
- **回归任务**：1 张主表覆盖 4 个数据集 × 2 种动作形式 ×11 个模型。
- **消融实验**（Table 3）：码本大小（80/64/256）、序列长度（16/49/64）、潜在维度（32/64/256/512/1024）共 10+ 组配置。
- **步长消融**（Table 4）：VLABench 上 stride ∈ {5, 15, 30}，共 11 个模型对比。
- **错误分析**（Figure 5）：长尾分布的逐类 F1 散点。
- **可视化分析**（Figure 6）：跨注意力热力图对比 7+ 种模型。
- **充分性评价**：
  - 跨范式、跨数据集、跨粒度的横向比较较为全面。
  - 多头超参搜索与不同归一化指标提升了评测稳健性。
  - 但 Embodied LAM 的训练数据与测试分布存在差距，**对其不利**；General LAM 仅与单一 LAPA 框架嫁接，**对架构多样性的覆盖有限**。
  - 所有回归指标均为单一 MSE，缺少多维度的物理一致性度量（如成功率仿真回放）。

## 6. 主要结论与发现

1. **结论一**：通用视觉基础模型（V-JEPA 2.1、DINOv3 等）即使未经显式动作监督，也**一致优于**专用 Embodied LAM。
   - 复合任务平均分类：V-JEPA 2.1 达 **76.29%**，而 LAPA 仅 19.13%、UniVLA 18.82%、villa-X 23.85%。
2. **结论二**：**潜在特征空间比像素空间更对齐物理动作空间**。
   - 绝对回归：V-JEPA 2.1（0.19）远低于 Wan2.2（0.31）和 FLUX.2-dev（0.50）。
   - 长步长下，LAM 范式（特别是 General LAM）展现出对动态轨迹的稳定性，而像素编码器（如 FLUX.2-dev）从 stride=5 的 0.04 MSE 退化到 stride=30 的 0.62。
3. **范式层级**：通用视觉编码器 > General LAM > Embodied LAM，提示当前"具身特化"训练反而可能损害表示质量。
4. **动作形式的影响**：绝对定位由语义特征主导；相对增量下 General LAM 与最强基线的差距显著缩小（V-JEPA 2.1: 0.50 vs LAPA-DINOv3: 0.57）。
5. **设计准则**：自监督视觉先验 + 严格正则化的量化瓶颈（码本大小、序列长度、潜在维度）共同决定有效潜在动作空间。

## 7. 优点与亮点

- **首次将潜在动作表示的评估与下游策略解耦**，专注于表征本身质量的标准化测量。
- **数据规模庞大、覆盖维度广**：1.2M 视频 / 151 类 / 11 种机器人形态 / 4 种环境大类。
- **统一了语义与物理两个互补维度**，构建出"什么要做"与"如何做"的双轴评估体系。
- **提出 General LAM 这一新范式**，系统性验证了通用视觉先验嫁接至 LAM 训练的价值。
- **自动化数据引擎**可扩展处理未来数据流，避免依赖人工标注。
- **多角度诊断分析**：长尾 F1 散点 + 跨注意力热力图 + 步长消融，揭示了模型失败模式（注意力扩散、量化崩溃）。
- **细粒度消融**（码本大小、序列长度、潜在维度）提供了具体的超参设计指引。

## 8. 不足与局限

- **算力信息缺失**：未披露 GPU 型号、数量与训练时长，复现成本难以估算。
- **General LAM 仅基于 LAPA 框架**：对其他 LAM 范式（如连续动作 CoMo、IGOR）的嫁接未做对比，结论的普适性受限。
- **Embodied LAM 的评测公平性存疑**：LAPA 等的训练数据与 LARYBench 测试数据存在分布差异，可能导致其表现被低估，但论文未对此进行补偿分析。
- **复合人类 vs. 复合机器人之间数据/形态不平衡**：复合人类约 692K 视频，复合机器人约 538K，且机器人形态、动作空间差异较大，可能引入偏差。
- **回归指标单一**：仅用 MSE 评估物理对齐，缺乏仿真回放、成功率、轨迹平滑度等多维度量；附录虽提到 phys_*_mse 但未在主表中呈现。
- **动作形式与数据集对应不完整**：Table 2 中 AgiBotWorld-Beta、VLABench 等数据集在绝对与 delta 回归下指标存在缺失或统一空间问题，影响横向对比的直观性。
- **长尾性能仍受数据驱动**：即便强模型在长尾类上优势扩大，但绝对准确率仍较低，且未给出针对性的改进方案。
- **应用边界**：聚焦视觉到动作的潜在表示评测，**未涉及语言条件、触觉/力觉等多模态融合**，对 VLA 整体系统设计的指导仍有距离。

（完）
