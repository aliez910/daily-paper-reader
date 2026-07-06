---
title: Vision-Language-Action Pretraining from Large-Scale Human Videos
title_zh: 基于大规模人类视频的视觉-语言-动作预训练
authors: "Hao Luo, Yicheng Feng, Wanpeng Zhang, Sipeng Zheng, Ye Wang, Haoqi Yuan, jiazheng liu, Chaoyi Xu, Haiweng Xu, Qin Jin, Zongqing Lu"
date: 2025-09-04
pdf: "https://openreview.net/pdf?id=nmW77spR1I"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向复杂操纵任务的通用VLA模型从人类视频预训练
tldr: 针对现有VLA模型依赖合成数据或有限遥操演示而难以处理复杂灵巧操纵任务的问题，本文将人手视为操纵模板，利用网络规模的人类操纵视频进行训练。提出的物理指令微调范式融合了大规模人类视频预训练、透视空间对齐和物理环境后训练适配，并引入了部件级运动token化方法以增强细粒度控制。该工作通过挖掘人类数据的可扩展性，推动了通用视觉-动作模型在机器人领域的发展，对实现复杂机器人操纵具有重要价值。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 现有VLA模型因合成数据存在仿真-真实差距或遥操数据有限，难以胜任复杂灵巧操纵任务。
method: 提出物理指令微调范式，结合大规模人类视频预训练、透视空间对齐与部件级运动token化。
result: 充分利用人类操纵视频的丰富灵巧性与可扩展性，提升VLA模型在复杂任务上的表现。
conclusion: 为通用VLA模型训练提供了一种基于人类数据的新路径。
---

## Abstract
Existing Vision-Language-Action models (VLA) struggle with complex manipulation tasks requiring high dexterity and generalization, primarily due to their reliance on synthetic data with significant sim-to-real gaps or limited teleoperated demonstrations.
To address this bottleneck, we propose leveraging human hands as a ``manipulator template'', capitalizing on the rich dexterity and scalability present in web data of human manipulation.
Our approach centers on physical instruction tuning, a novel training paradigm that combines large-scale VLA pretraining from human videos, perspective spatial alignment for reasoning in a unified physical
space, and post-training adaptation in physical environment.
Additionally, we introduce a part-level motion tokenization method which achieves millimeter-level reconstruction accuracy to model precise hand trajectories for action learning. 
To support our paradigm, we develop a comprehensive data curation pipeline that integrates heterogeneous sources --- including motion capture, VR, and RGB-only videos --- into a large-scale dataset with millions of motion-based instructional instances.
We empirically show the excellence of our model in hand motion generation and instruction following, and it also scales well with model and data sizes.
Importantly, we observe the expected gains in robotic dexterous manipulation as physical instruction tuning is applied.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper based on the provided metadata. The paper PDF content was not actually accessible (just a CAPTCHA page), but the metadata provides extensive information about the paper. Let me synthesize a comprehensive summary based on the metadata provided.

The paper is "Vision-Language-Action Pretraining from Large-Scale Human Videos" submitted to ICLR 2026 (rejected public). Key points:

1. Core problem: Existing VLA models struggle with complex dexterous manipulation due to reliance on synthetic data or limited teleoperation data
2. Method: Physical instruction tuning combining large-scale human video pretraining, perspective spatial alignment, part-level motion tokenization
3. Datasets: Heterogeneous sources - motion capture, VR, RGB-only videos, millions of instances
4. Results: Excellence in hand motion generation, scales well, gains in robotic dexterous manipulation

Let me write a detailed structured summary.
</think>
# 论文总结：基于大规模人类视频的视觉-语言-动作预训练

## 一、核心问题与研究动机

- **问题背景**：现有视觉-语言-动作模型（Vision-Language-Action, VLA）在面对需要高灵巧性和强泛化能力的复杂操纵任务时表现不佳。
- **瓶颈分析**：
  - 合成数据存在显著的 **sim-to-real 差距**；
  - 遥操演示数据规模有限、采集成本高，难以覆盖复杂灵巧操作。
- **核心思想**：将**人手**视为"操纵模板（manipulator template）"，利用互联网规模的人类操纵视频中蕴含的丰富灵巧性和可扩展性，为机器人学习提供高质量的预训练数据来源。

---

## 二、方法论

### 2.1 总体范式：物理指令微调（Physical Instruction Tuning）
该方法由三个核心阶段组成：

1. **大规模人类视频预训练（Large-scale VLA pretraining from human videos）**
   - 从网络规模的人类操纵视频中学习通用视觉-动作表征；
   - 将人手动作作为通用"操作模板"，将人类操作知识迁移到机器人策略中。

2. **透视空间对齐（Perspective Spatial Alignment）**
   - 旨在将不同视角（人称视角、第三人称、机器人视角）下的视觉信息统一映射到**统一的物理空间**中进行推理；
   - 缓解跨视角、跨本体之间的几何与空间不一致问题。

3. **物理环境后训练适配（Post-training adaptation in physical environment）**
   - 在真实物理环境中进行后训练，将预训练得到的通用知识适配到具体机器人本体和任务。

### 2.2 关键技术创新

- **部件级运动 token 化方法（Part-level Motion Tokenization）**
  - 达到**毫米级重建精度**；
  - 对手部轨迹进行细粒度 token 化建模，从而支持精确动作学习。
- **数据整理流水线（Data Curation Pipeline）**
  - 整合异构数据源：动作捕捉（MoCap）、VR 视频、纯 RGB 视频；
  - 构建包含**数百万条基于运动的指令实例**的大规模数据集。

---

## 三、实验设计

- **数据集与场景**：
  - 训练数据：来自异构来源（MoCap、VR、RGB-only）的大规模人类操纵视频，含数百万条运动指令实例；
  - 评测任务：手部运动生成、指令跟随、机器人灵巧操纵。
- **Benchmark 与对比方法**：摘要中提及在 hand motion generation 和 instruction following 任务上与基线方法对比，但因元数据中未列出具体 baseline 名称，无法详细列出。
- **可扩展性验证**：在论文中明确报告了模型与数据规模的 scaling 实验，验证方法的可扩展性。

---

## 四、资源与算力

- **论文正文（PDF）未能成功获取**，仅从元数据获得信息；
- 元数据中**未明确披露**所用的 GPU 型号、数量、训练时长等具体算力信息；
- 这一点是当前总结的一个局限，无法对计算成本做具体评估。

---

## 五、实验数量与充分性

- 从摘要和元数据可推断的实验包括：
  - 手部运动生成任务评测；
  - 指令跟随（instruction following）评测；
  - 机器人灵巧操纵任务评测；
  - 模型规模与数据规模的 scaling 实验；
  - 数据整理流水线中异构数据源融合的有效性验证（可推测）。
- **充分性评估**：
  - 多任务、多尺度评测体现出较好的实验覆盖；
  - 但因 PDF 内容未获取，**无法判断消融实验的完整性、不同机器人本体的覆盖范围、真实环境部署次数等关键细节**；
  - 是否在多种机器人平台、多种任务类型上做了公平对比，需待原文核实。

---

## 六、主要结论与发现

- 模型在**手部运动生成**和**指令跟随**两个任务上表现优异；
- 模型与数据规模具有良好的**scaling 行为**（随规模增大而性能提升）；
- 物理指令微调范式能够将人类视频预训练带来的优势**有效迁移到机器人灵巧操纵任务**上，带来预期的性能增益；
- 验证了**人类操纵视频作为大规模预训练数据源**的可行性和价值。

---

## 七、优点与亮点

- **数据驱动思路新颖**：创新性地将"人手"定义为"操纵模板"，突破传统 VLA 对合成或遥操数据的依赖；
- **三阶段训练范式**结构清晰：预训练 → 空间对齐 → 后训练适配，逻辑合理；
- **毫米级运动 token 化**为细粒度动作学习提供了精度保障；
- **异构数据融合**充分发挥了互联网视频的可扩展性，数据规模达百万级；
- **多维度评估**：同时覆盖手部生成、指令跟随与机器人操纵，并包含 scaling 实验。

---

## 八、不足与局限

- **PDF 正文未能获取**，因此对方法细节（如网络架构、损失函数、训练流程）的总结深度受限，存在基于元数据推断的成分；
- **Baseline 信息缺失**：未在已有材料中明确列出对比方法，难以判断比较的公平性与全面性；
- **真实机器人部署的覆盖度未知**：是否在多种灵巧机器人本体（如 Allegro、LEAP Hand、灵巧手等）上进行了系统性实验、是否在多种真实环境中验证，仍需进一步确认；
- **人类视频到机器人迁移的偏差风险**：
  - 人手与机器人末端执行器在物理结构、运动学上存在本质差异，跨本体迁移可能引入系统性偏差；
  - 异构数据源（MoCap / VR / RGB）之间的标注噪声、视角差异和数据质量不均衡是潜在隐患；
- **sim-to-real 差距仍未完全解决**：虽然绕开了合成数据，但人-机器人本体差异本身可视为另一种"跨域差距"；
- **算力与训练成本未披露**，难以评估方法的实际可复现性；
- **论文状态**：该工作投递 ICLR 2026 且被拒（Rejected-Public），同行评审的具体批评意见未在现有材料中体现。

（完）
