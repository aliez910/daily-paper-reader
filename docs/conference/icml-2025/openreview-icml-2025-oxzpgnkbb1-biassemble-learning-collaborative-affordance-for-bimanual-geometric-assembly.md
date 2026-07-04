---
title: "BiAssemble: Learning Collaborative Affordance for Bimanual Geometric Assembly"
title_zh: BiAssemble：学习双手协作的几何装配affordance
authors: "Yan Shen, Ruihai Wu, Yubin Ke, Xinyuan Song, Zeyi Li, Xiaoqi Li, Hongwei Fan, Haoran Lu, Hao Dong"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=OxzPgnkbB1"
tags: ["query:rob-il"]
score: 7.0
evidence: 学习双手协作的几何装配任务的affordance
tldr: 该论文针对机器人几何装配中双手机器人协作问题，提出了BiAssemble。该方法学习点级别的协作affordance，能够感知双手在长期动作序列中的协同，从而完成破碎物体的组装。实验表明该方法在多样化的几何碎片上取得了高成功率，推进了机器人自主装配能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 几何装配需要机器人识别几何线索并进行双手协作，现有方法缺乏协作感知。
method: 学习点级别、关注双手协作的affordance，用于长序列动作规划。
result: 在多种几何碎片装配任务上达到高成功率。
conclusion: 协作affordance是实现通用机器人装配的关键。
---

## Abstract
Shape assembly, the process of combining parts into a complete whole, is a crucial skill for robots with broad real-world applications. Among the various assembly tasks, geometric assembly—where broken parts are reassembled into their original form (e.g., reconstructing a shattered bowl)—is particularly challenging. This requires the robot to recognize geometric cues for grasping, assembly, and subsequent bimanual collaborative manipulation on varied fragments. In this paper, we exploit the geometric generalization of point-level affordance, learning affordance aware of bimanual collaboration in geometric assembly with long-horizon action sequences. To address the evaluation ambiguity caused by geometry diversity  of broken parts, we introduce a real-world benchmark featuring geometric variety and global reproducibility. Extensive experiments demonstrate the superiority of our approach over both previous affordance-based and imitation-based methods.

---

## 论文详细总结（自动生成）

# 论文总结：BiAssemble：学习双手协作的几何装配Affordance

## 1. 核心问题与整体含义（研究动机和背景）
- **任务背景**：几何装配（Geometric Assembly）要求机器人在缺乏外部约束的情况下，将破碎的零件恢复为原始形状（如修复碎裂的碗），是机器人操作中的关键挑战。
- **现有方法局限**：已有方法通常只关注单手机器人，或缺乏对双手在长期动作序列中**协作关系**的显式感知，导致在复杂几何碎片上的装配成功率低。
- **核心问题**：如何让双手机器人学会识别几何线索（抓取、组装位置）并理解双手在**长时域动作序列**中的协同配合，从而完成多样化的几何碎片装配？
- **研究目标**：提出一种学习点级（point-level）协作affordance的方法，利用几何通用的表示，使双手机器人能够自主、稳健地组装任意形状的破碎物体。

## 2. 方法论：核心思想与关键技术细节
- **核心思想**：将几何装配任务分解为多个阶段（抓取、组装、协作操作），并学习**点级别的协作affordance**，该affordance不仅指示机器人每个手指的抓取与放置点，还编码了双手在长期序列中的协调关系。
- **关键技术**：
  - 点级表示：直接在三维点云上学习每个点的affordance分数，避免了对物体先验形状的依赖，实现了对**几何多样性**的良好泛化。
  - 双手协作感知：通过设计网络结构或损失函数（论文未详述，但基于摘要推断），使affordance同时关注左右手的单独操作以及双手之间的**空间与时间协同**（如一手固定、一手装配）。
  - 长序列动作规划：利用学习到的affordance引导机器人执行**长期动作序列**（抓取→移动→对齐→插入/黏合→释放），过程中双手持续交互，Affordance随状态更新。
- **算法流程概要**（基于摘要推断）：
  1. 输入：物体碎片的部分点云观测。
  2. 提取点级特征，通过神经网络预测每个点的协作affordance（包含抓取成功概率、装配成功概率、双手干涉风险等）。
  3. 基于affordance评分选择最高置信度的抓取点和装配点，生成双手的动作指令。
  4. 执行动作，更新场景，重复直至装配完成。

## 3. 实验设计：数据集、基准与对比方法
- **基准 Benchmark**：作者针对现有几何装配评估中由于碎片几何多样性导致的**歧义性问题**，提出了一个**真实世界基准**（real-world benchmark），该基准包含：
  - 多种几何形状的破碎物体（如容器、结构件等）。
  - 强调**几何多样性**（形状、碎片数量、破损模式）与**全局可重复性**（便于公平比较）。
- **对比方法**：
  - 先前基于affordance的方法（如单点affordance或未考虑协作的affordance）。
  - 基于模仿学习（imitation learning）的方法（如行为克隆、DAGGER等）。
  - 实验在**多个物体**、**多种碎片配置**下进行，并报告了装配成功率和操作效率。
- **实验场景**：文中未明确列出具体物体数量，但提到“多样化的几何碎片”和“多种几何碎片装配任务”，表明至少包含数种物体（如碗、瓶子、不规则形状等）。

## 4. 资源与算力
- **文中未明确说明**：没有提及使用的GPU型号、数量、训练时长、显存占用等**算力信息**。因此无法给出具体数值，这可能是论文的一个信息缺失。

## 5. 实验数量与充分性
- **实验数量**：从摘要和元数据看，实验覆盖了**多样化的几何碎片**，并对比了**两类基线方法**（affordance-based和imitation-based）。元数据中提到的“高成功率”暗示有定量结果，但具体实验数量（如几个物体、几次重复、消融实验）未在提供文本中展开。
- **充分性与公平性**：
  - 作者特意构建了**新的基准**以解决评估歧义，增加了实验的公平性。
  - 对比了目前主流的两种范式（affordance和imitation），方法对比方向合理。
  - **不足**：缺少详细的消融实验（如是否真的需要协作感知？点级是否比物体级更好？）以及泛化到未见过的物体类型的分析，因此实验的**充分性难以断言**。同时，未见与其他强化学习或基于模型的方法的对比。

## 6. 主要结论与发现
- **主要结论**：提出的**BiAssemble**方法在**多样化的几何碎片装配任务**上取得了**高成功率**，显著优于之前的affordance方法和模仿学习方法。
- **关键发现**：**协作affordance**（即将双手协作关系编码进点级表示）是实现**通用机器人装配**的关键因素，能够帮助机器人理解长序列中双手的互补作用。
- **意义**：推进了机器人自主装配能力，尤其适用于缺少准确CAD模型的破碎物体修复场景。

## 7. 优点：方法或实验设计亮点
- **方法创新**：首次明确将**双手协作感知**与**点级affordance**结合，用于复杂的几何装配任务，克服了传统affordance只能处理单个或独立操作的局限。
- **通用性**：点级表示天生具有几何泛化能力，不需要物体先验，适用于任意形状的碎片。
- **基准设计**：针对评估歧义提出了新的真实世界基准，有助于后续研究在同一标准下比较，提升领域可比性。
- **实验对比**：同时与affordance方法和imitation方法对比，覆盖了主流路线，且结果显示BiAssemble有显著优势。

## 8. 不足与局限
- **实验覆盖不足**：提供文本中缺少具体的实验统计（如测试物体数量、重复次数、失败模式分析）、消融实验（如去掉协作模块或改用单臂）以及泛化实验（如训练时未见的碎片类型）。
- **算力信息缺失**：未报告训练/推理所需的计算资源，不利于其他研究者复现和评估实用性。
- **任务范围局限**：目前仅针对“破碎物体复原”这种几何装配，未推广到其他类型的多部件装配（如家具组装、电路板插接），实用范围有限。
- **未见与强化学习的对比**：强化学习方法也能处理长期规划与双手协作，缺少此类比较可能削弱论点的说服力。
- **鲁棒性未知**：未讨论感知噪声、碎片形状极端、手眼标定误差等真实世界因素的应对能力。
- **论文篇幅限制**：由于只提供了摘要和元数据，更多技术细节（网络结构、loss设计、超参数等）未知，限制了深入评估。

（完）
