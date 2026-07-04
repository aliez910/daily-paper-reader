---
title: Mitigating the Human-Robot Domain Discrepancy in Visual Pre-training for Robotic Manipulation
title_zh: 缓解机器人操纵视觉预训练中的人-机器人域差异
authors: "Zhou, Jiaming, Ma, Teli, Lin, Kun-Yu, Wang, Zifan, Qiu, Ronghe, Liang, Junwei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhou_Mitigating_the_Human-Robot_Domain_Discrepancy_in_Visual_Pre-training_for_Robotic_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 通过人-机器人配对数据桥接视觉预训练以提升操纵泛化
tldr: 机器人示教数据规模有限，限制了视觉表征在真实操纵任务中的泛化。本文利用大规模人类活动数据进行预训练，并针对人-机器人形态差异导致的域差异，提出新的适配范式，结合人-机器人配对视频数据弥合鸿沟。该方法使下游操纵策略获得更强的视觉泛化能力，对基于演示的模仿学习具有重要支撑作用。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1723, \"height\": 712, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1620, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1799, \"height\": 626, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 780, \"height\": 426, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 689, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1809, \"height\": 553, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhou-mitigating-the-human-robot-domain-discrepancy-in-visual-pre-training-for-robotic-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 245, \"label\": \"Table\"}]"
motivation: 机器人示教数据稀缺且多样性不足，人类视频存在域差异。
method: 利用人-机器人配对视频数据，提出新的适配范式弥合形态差异。
result: 提升了视觉表征在下游操纵任务中的跨域泛化能力。
conclusion: 为利用大规模人类视频预训练操纵策略提供了可行方案。
---

## Abstract
Learning generalizable visual representations across different embodied environments is essential for effective robotic manipulation in real-world scenarios. However, the limited scale and diversity of robot demonstration data pose a significant challenge. Recent research has explored leveraging large-scale human activity data for pre-training, but the substantial morphological differences between humans and robots introduce a significant human-robot domain discrepancy, hindering the generalization of these models to downstream manipulation tasks. To overcome this, we propose a novel adaptation paradigm that leverages readily available paired human-robot video data to bridge the domain gap. Our method employs a human-robot contrastive alignment loss to align the semantics of human and robot videos, adapting pre-trained models to the robot domain in a parameter-efficient manner. Experiments on 20 simulated tasks across two different benchmarks and five real-world tasks demonstrate significant improvements. These results span both single-task and language-conditioned multi-task settings, evaluated using two different pre-trained models. Compared to existing pre-trained models, our adaptation method improves the average success rate by over 7% across multiple tasks on both simulated benchmarks and real-world evaluations.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Mitigating the Human-Robot Domain Discrepancy in Visual Pre-training for Robotic Manipulation" following a specific structured format. Let me carefully analyze the paper content and organize the summary according to the 8 requested points.

Let me extract key information:

1. **Core problem**: Human-robot domain discrepancy in visual pre-training for robotic manipulation. Limited robot demonstration data, large-scale human data exists but morphological differences cause domain gaps.

2. **Method**: HR-Align (Human-Robot Semantic Alignment)
- Uses paired human-robot video data (from RH20T dataset)
- Adapter modules (parameter-efficient) inserted into pre-trained models
- Human-robot contrastive alignment loss
- Task-aware feature modeling using BERT for task descriptions
- Adapts frozen pre-trained models (R3M and D4R)

3. **Experiments**:
- 20 simulated tasks across 2 benchmarks (Adroit and RLBench)
- 5 real-world tasks (xArm7 robot)
- Compared methods: D4R, R3M (baseline), R3M-PreT, R3M-ClS
- Settings: single-task and multi-task (language-conditioned)

4. **Resources**:
- 4 NVIDIA A6000 GPUs
- ~8k training steps
- Learning rate 1e-4, batch size 200
- Temperature τ = 0.1
- 56k human-robot video pairs from RH20T

5. **Experiment count**: 
- Adroit single-task (2 tasks)
- RLBench multi-task (18 tasks)
- Real-world (5 tasks)
- Ablation: adapter position, t-SNE visualization
- Baselines: R3M-PreT, R3M-ClS

6. **Conclusions**: 
- +7% average improvement on multiple tasks
- R3M-Align: +7.3% on Adroit, +8.9% on RLBench
- D4R-Align: +2.0% on Adroit, +4.6% on RLBench
- Real-world: +13% (D4R-Align), +11% (R3M-Align)

7. **Strengths**:
- Parameter-efficient (only 1.6M extra params for R3M)
- Maintains versatility of pre-trained models
- Works with different pre-trained backbones
- Comprehensive evaluation across simulated and real-world

8. **Limitations**:
- Doesn't measure domain discrepancies quantitatively
- Doesn't revisit pre-training stage
- Scale/diversity of paired data impact not fully understood
- Adapter position needs careful selection

Let me write this up in Chinese with proper Markdown structure.</think>

# 论文总结：Mitigating the Human-Robot Domain Discrepancy in Visual Pre-training for Robotic Manipulation

## 1. 核心问题与研究背景

- **研究动机**：机器人操纵（Robotic Manipulation）需要可泛化的视觉表征，但高质量机器人示教数据规模有限、多样性不足，限制了策略学习效果。
- **现有方案**：近年来利用大规模人类活动视频（如 Ego4D、Kinetics）进行预训练，再将冻结的视觉编码器迁移到下游机器人任务。其假设是"人-物交互的动态语义"与机器人操作任务具有相似性。
- **关键瓶颈**：人类与机器人在**形态学上存在巨大差异**（人手 vs. 机械臂/夹爪），导致显著的**人-机器人域差异（Human-Robot Domain Discrepancy）**，使基于人类数据预训练的模型难以直接迁移到机器人下游任务。
- **已有方法的不足**：
  - 路线一（隐式代理任务微调）：未直接接触机器人数据，难以有效弥合域差异；
  - 路线二（插入可学习模块并下游微调）：需为每个下游环境定制模型，损害了预训练模型的通用性。

## 2. 方法论：Human-Robot Semantic Alignment (HR-Align)

### 2.1 核心思想
- 提出**新的适配范式**：利用现成的**人-机器人配对视频数据**（如 RH20T）作为"桥梁"，通过参数高效（Parameter-Efficient）的适配器，将人类数据预训练模型适配到机器人域。
- **关键洞察**：配对人-机器人视频具有语义对齐性；机器人结构同质性使得即使是异源机器人演示，其与下游机器人数据的域差异也相对较小。

### 2.2 技术细节
- **适配器模块（Adapter）**：插入到预训练模型中（默认在最后一层之后），结构为：
  - 下投影卷积 → 激活函数 g → 上投影卷积 + 残差连接
  - 公式：$\text{r}_{t,\text{next}} = r_{f,\text{inter}} + \text{Conv}_{\text{up}}(g(\text{Conv}_{\text{down}}(r_{f,\text{inter}})))$
- **三条流（Stream）**：
  1. **冻结人类流**：用原始预训练模型提取人类视频特征 $h_f$；
  2. **冻结机器人流**：用原始预训练模型提取机器人视频特征 $r_f$；
  3. **适配机器人流**：用插入适配器后的模型提取机器人特征 $r_t$。
- **任务感知特征建模**：
  - 用冻结的 DistilBERT + 可学习 FC 层编码任务描述 $L$ 得 $l \in \mathbb{R}^{\hat{C}}$；
  - 以 $l$ 为 query，视觉特征为 key/value，做 attention 聚合，得到 $\bar{h}_f, \bar{r}_f, \bar{r}_t$。

### 2.3 人-机器人对比对齐损失（核心损失）
对于 batch 内 $M$ 对配对数据：
$$
\mathcal{L} = \frac{1}{2M}\sum_{i=1}^{M}\left[-\log\frac{S(\bar{h}_{f}^{i},\bar{r}_{t}^{i})}{S(\bar{h}_{f}^{i},\bar{r}_{t}^{i})+S(\bar{h}_{f}^{i},\bar{r}_{f}^{i})+\sum_{j \neq i}S(\bar{h}_{f}^{i},\bar{r}_{t}^{j})} + (h \leftrightarrow r)\right]
$$
其中 $S(x,y)=\exp(x^T y/\tau)$。该损失要求：
1. 适配后的机器人特征 $\bar{r}_t^i$ 与配对人类特征 $\bar{h}_f^i$ 的语义一致性，**优于**未适配的 $\bar{r}_f^i$；
2. 跨 batch 内的负样本形成对比约束。

## 3. 实验设计

### 3.1 数据集与场景
- **配对数据**：RH20T 数据集中的子集，共 **56k** 人-机器人视频对（用于适配阶段）。
- **预训练模型**：两种主流人类数据预训练视觉编码器：
  - **R3M**（Ego4D，vision-language contrastive）；
  - **D4R**（data4robotics，Kinetics，MoCo）。
- **下游仿真基准**：
  - **Adroit**：2 个灵巧操作单任务（pen、relocate）；
  - **RLBench**：18 个语言条件多任务（如 put in drawer、stack blocks 等）。
- **真实世界**：使用 **xArm7** 机械臂 + Inspire 夹爪 + Orbbec Femto Bolt 第三视角相机，5 个任务（put fruit in plate、stack cups、put tennis in mug、hang mug、put item in box），每任务 40 个演示，评估 20 次。

### 3.2 对比方法
- **基线预训练模型**：未适配的 R3M、D4R；
- **强对比基线**：
  - **R3M-PreT**：在机器人视频上继续用 R3M 原预训练方式全参数微调；
  - **R3M-ClS**：在机器人视频上做动作类别分类的全参数微调；
- **自对比消融**：不同位置插入适配器（Early / Middle / Late / All）。

### 3.3 训练配置
- 单任务 Adroit：行为克隆（Behavior Cloning），3 个种子平均报告；
- 多任务 RLBench：单层 self-attention 融合冻结特征 + 语言，1800 演示，5 epoch，3 次测试取均值与标准差；
- 真实世界：ACT 框架预测末端关键位姿。

## 4. 资源与算力

- **GPU**：4 张 **NVIDIA A6000**；
- **训练步数**：约 **8k 步**；
- **优化器**：Adam，学习率 $1 \times 10^{-4}$，batch size = 200；
- **温度**：$\tau = 0.1$；
- **采样**：每视频随机采样 5 帧（$T=5$）；
- **相对成本**：作者强调适配阶段额外成本远小于人类数据预训练本身；
- 论文**未明确说明**总训练时长（小时数）、显存占用或与下游策略学习的算力消耗。

## 5. 实验数量与充分性

### 5.1 实验规模
- **仿真任务**：Adroit 2 单任务 + RLBench 18 多任务，共 **20 个任务**；
- **真实世界任务**：5 个真实操作任务；
- **消融实验**：
  - 适配器插入位置（Early/Middle/Late/All）；
  - 与两种全参数微调强基线对比；
  - t-SNE 可视化对比 R3M 与 R3M-Align 的下游特征分布；
  - 任务感知特征增强模块的消融（附录中提及）。

### 5.2 充分性评估
- **优点**：
  - 覆盖两种主流预训练骨干（R3M、D4R），结论具有迁移性；
  - 跨越仿真单任务、仿真多任务、真实世界三类场景；
  - 报告均值与标准差（RLBench 上 3 次测试），具备统计意义；
  - 与"全参数微调"对比，突出了**参数高效（仅 1.6M 可学习参数，约 6.4%）** 的优势。
- **可能的不足**：
  - Adroit 仅 2 任务，难度与多样性有限；
  - 真实世界每任务仅 20 次评估，统计置信度有限；
  - 仅适配了一种形态学差距场景（xArm7），未在多种机械臂/夹爪上验证。

## 6. 主要结论与发现

- **仿真单任务（Adroit）**：
  - R3M-Align 相比 R3M 平均提升 **+7.3%**；
  - D4R-Align 相比 D4R 提升 **+2.0%**。
- **仿真多任务（RLBench 18 任务）**：
  - R3M-Align 平均提升 **+8.9%**（50.3 → 59.2）；
  - D4R-Align 平均提升 **+4.6%**（55.3 → 59.9）；
  - 在"put in drawer"上 R3M-Align 提升高达 **+56.0%**（14.7 → 70.7）。
- **真实世界 5 任务**：
  - D4R-Align 提升 **+13%**；R3M-Align 提升 **+11%**。
- **消融发现**：
  - 适配器仅插入最后位置（Late）效果最佳，仅用 1.6M 参数即可获得最大增益；
  - 在多处插入反而降低性能，说明多位置协同适配不利于语义对齐；
  - t-SNE 显示 R3M-Align 的下游特征聚类更紧凑、更有判别性。

## 7. 方法与实验的亮点

- **新范式视角**：首次明确提出"利用配对人-机器人数据 + 参数高效适配器"作为弥合域差异的统一方案；
- **参数高效**：仅需调节约 1.6M 参数（R3M 总参数 25M 的 6.4%），即可达到或超越全参数微调效果；
- **通用性强**：保持预训练模型的通用性，无需为每个下游环境定制；同一适配流程适用于 R3M 和 D4R 两种异质预训练方法；
- **损失设计精巧**：对比损失同时实现"正样本拉近 + 未适配负样本对比"双重约束，兼顾了语义对齐与判别性；
- **实验覆盖广**：仿真+真实、单任务+多任务、两套预训练骨干均验证。

## 8. 不足与局限

- **域差异的度量缺失**：作者承认未提供定量方法来衡量人类数据预训练与下游机器人任务之间的域差异，难以精准指导适配过程；
- **未触及预训练阶段**：仅在预训练后做适配，未探索将配对人-机器人数据融入大规模预训练以得到更强的原生模型；
- **配对数据规模与多样性的影响未充分研究**：未系统分析配对数据量、任务多样性对最终性能的影响曲线；
- **真实世界评估规模较小**：每任务 20 次评估、5 个任务，可能未覆盖复杂干扰、跨场景等真实挑战；
- **适配器位置选择依赖经验**：缺少自动选择适配器插入位置的策略（论文中"在多处同时插入反而下降"反映了这一点）；
- **任务特征增强非核心**：BERT-based 任务感知的贡献相对较小，且依赖语言标注质量；
- **计算细节披露不全**：总训练时长、显存消耗、与下游策略学习的总算力未明确说明。

（完）
