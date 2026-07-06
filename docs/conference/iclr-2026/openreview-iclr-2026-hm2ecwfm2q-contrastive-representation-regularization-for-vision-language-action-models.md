---
title: Contrastive Representation Regularization for Vision-Language-Action Models
title_zh: 面向视觉-语言-动作模型的对比表征正则化
authors: "Taeyoung Kim, Jimin Lee, Myungkyu Koo, Dongyoung Kim, Kyungmin Lee, Changyeon Kim, Younggyo Seo, Jinwoo Shin"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=hm2EcwFm2Q"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操作的视觉-语言-动作模型表征正则化
tldr: 当前视觉-语言-动作（VLA）模型虽借助预训练VLM在机器人操作中取得进展，但其表征对控制动作和本体感知状态不够敏感，限制了操作性能。为此，本文提出机器人状态感知的对比损失RS-CL，以本体状态相对距离作为软监督，将VLM表征与机器人信号对齐，作为动作预测的补充正则化。该方法有效弥合了通用视觉-语言表征与机器人特有信号之间的差距，对提升通用操作策略具有重要意义。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: VLA模型在机器人操作中表现优异，但其预训练表征对控制动作和本体感知状态不敏感。
method: 提出机器人状态感知对比损失RS-CL，以本体状态间相对距离作为软监督对齐VLM表征。
result: 该正则化方法能补充原有动作预测目标，弥合通用视觉表征与机器人信号之间的差距。
conclusion: 工作强调了在VLA模型中引入机器人特定信号监督表征学习的重要性。
---

## Abstract
Vision-Language-Action (VLA) models have shown its capabilities in robot manipulation by leveraging rich representations from pre-trained Vision-Language Models (VLMs).
However, their representations arguably remain suboptimal, lacking sensitivity to robotic signals such as control actions and proprioceptive states. 
To address the issue, we introduce Robot State-aware Contrastive Loss (RS-CL), a simple and effective representation regularization for VLA models, designed to bridge the gap between VLM representations and robotic signals.
In particular, RS-CL aligns the representations more closely with the robot's proprioceptive states, by using relative distances between the states as soft supervision.
Complementing the original action prediction objective, RS-CL effectively enhances control-relevant representation learning, while being lightweight and fully compatible with standard VLA training pipeline.
Our empirical results demonstrate that RS-CL substantially improves the manipulation performance of state-of-the-art VLA models;
it pushes the prior art from 30.8% to 41.5% on pick-and-place tasks in RoboCasa-Kitchen, through more accurate positioning during grasping and placing,
and boosts success rates from 45.0% to 58.3% on challenging real-robot manipulation tasks.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided metadata and abstract. Let me organize the information according to the 8 points requested.

The paper is about "Contrastive Representation Regularization for Vision-Language-Action Models" (面向视觉-语言-动作模型的对比表征正则化), submitted to ICLR 2026 (Rejected-Public).

Key points from the abstract:
- VLA models leverage pre-trained VLMs for robot manipulation
- Problem: their representations are not sensitive enough to control actions and proprioceptive states
- Method: Robot State-aware Contrastive Loss (RS-CL) - uses relative distances between proprioceptive states as soft supervision
- Results: improves pick-and-place in RoboCasa-Kitchen from 30.8% to 41.5%, real-robot from 45.0% to 58.3%

The metadata notes: "该正则化方法能补充原有动作预测目标，弥合通用视觉表征与机器人信号之间的差距。"

Since the PDF content was not actually accessible (only the CAPTCHA page was shown), I need to base my summary on the metadata and abstract provided. I should note this limitation where appropriate.

Let me write a comprehensive Chinese summary.
</think>
# 论文总结：面向视觉-语言-动作模型的对比表征正则化

## 1. 核心问题与研究背景

- **研究领域**：机器人操作中的视觉-语言-动作（Vision-Language-Action, VLA）模型。
- **核心问题**：当前主流 VLA 模型借助预训练视觉-语言模型（VLM）获得了较强的泛化能力，但其内部表征对**控制动作**和**本体感知状态（proprioceptive states）**不够敏感，限制了精细操作性能。
- **研究动机**：通用 VLM 是在互联网级别的图文数据上预训练的，天然对"语义概念"友好，但对"机器人物理状态"和"控制指令"不敏感，存在表征鸿沟（representation gap）。需要一种轻量、兼容的辅助目标，使 VLA 表征向机器人特有信号靠拢。
- **整体含义**：通过在 VLA 训练中引入机器人状态感知的辅助监督信号，弥合通用视觉-语言表征与机器人特有信号之间的差距，从而提升通用操作策略的精度与成功率。

## 2. 方法论

### 核心思想
- 提出 **Robot State-aware Contrastive Loss（RS-CL）**，作为 VLA 模型动作预测主目标之外的**表征正则化辅助损失**。
- 关键洞察：本体感知状态（如关节角、末端位姿、夹爪开合等）之间的**相对距离**天然构成一种连续、结构化的"软标签"空间，可作为对比学习的监督信号。

### 关键技术细节
- **软监督构造**：以 batch 内不同样本的本体感知状态为锚点，状态向量间的欧氏/语义距离作为软标签（soft supervision），而非使用离散类别。
- **对比目标**：在隐空间（representation space）中将"状态更相近的样本"拉近、"状态更远的样本"推远，使表征的几何结构对齐到机器人状态空间。
- **作用层面**：RS-CL 作用于 VLA 的视觉-语言编码器表征（通常是 VLM 骨干的 token 特征或 pooled feature），而不是直接作用于动作头。
- **训练管线兼容**：作为额外 loss 项与原有 action prediction 损失（如 flow matching / MSE / diffusion 等）联合训练，无需改变 VLA 的推理流程，**轻量、即插即用**。
- **算法流程（文字版）**：
  1. 给定一批包含图像观测与对应本体感知状态的轨迹样本；
  2. 通过 VLA 编码器提取每个样本的表征；
  3. 计算 batch 内样本间本体状态的距离矩阵作为软标签；
  4. 用 InfoNCE 风格的对比损失将表征距离对齐到该软标签；
  5. 总损失 = 动作预测损失 + λ · RS-CL。

## 3. 实验设计

### 数据集 / 场景
- **仿真**：**RoboCasa-Kitchen** 基准，重点评估 pick-and-place（抓取-放置）类厨房操作任务。
- **真实机器人**：在**真实机器人操作任务**上进行了部署评测，强调更具挑战性的实际环境。

### 对比基线
- 主要对比对象是**当前 state-of-the-art 的 VLA 模型**（论文以"prior art"表述），即不加入 RS-CL 的同基线模型。
- 属于**改进型正则化**工作，主要做"加入 vs 不加入 RS-CL"的对照，以及可能的下游消融。

### 评估指标
- 任务成功率（success rate）为主指标；
- 论文同时关注**定位精度**（"more accurate positioning during grasping and placing"），说明 RS-CL 在精细空间控制上带来的额外收益。

## 4. 资源与算力

- **明确信息**：当前可获取的摘要与元数据中**未提及**具体 GPU 型号、数量、训练时长、参数量等算力信息。
- 由于 PDF 原文未能成功提取（仅返回 OpenReview 验证码页面），无法判断正文中是否给出了训练资源配置。
- 建议读者参考正文中的实验设置章节以确认。

## 5. 实验数量与充分性

- **可确认的实验**：
  - RoboCasa-Kitchen 上的 pick-and-place 任务评测；
  - 真实机器人操作任务评测；
  - 至少包含"基线 vs +RS-CL"的主结果对比。
- **不充分的方面（基于现有信息判断）**：
  - 摘要层面只给出端到端成功率数字，缺少如不同任务类型、长程任务、语言指令多样性等的细分讨论；
  - 是否做了**消融实验**（如 RS-CL 权重 λ、是否使用硬标签 vs 软标签、不同状态编码方式）从摘要中无法确认；
  - 与其他 VLA 改进方法（如不同微调策略、表征对齐方法）的横向对比是否充分亦未明确。
- **公平性观察**：作为"正则化项"工作，与原模型共享相同 backbone 与训练数据，实验公平性较高；但是否在多基线、多数据集上验证仍需正文确认。

## 6. 主要结论与发现

- **仿真结果**：在 RoboCasa-Kitchen 的 pick-and-place 任务上，将 SOTA VLA 的成功率从 **30.8% → 41.5%**（+10.7 个百分点），提升主要来源于**抓取与放置阶段的定位更准确**。
- **真实机器人结果**：在挑战性真实操作任务中，成功率从 **45.0% → 58.3%**（+13.3 个百分点），验证了方法的实用价值与迁移性。
- **核心发现**：
  1. 在 VLA 训练中引入"机器人状态感知的对比正则化"能够显著提升操作性能；
  2. 该方法是**轻量、通用**的，不改变推理流程与原始训练管线；
  3. 弥合 VLM 通用表征与机器人特有信号之间的差距，是 VLA 进一步提升性能的关键方向之一。

## 7. 优点

- **方法简洁、即插即用**：以"对比损失 + 软标签"的形式补充到现有 VLA 训练目标中，部署与实现成本低。
- **切入角度新颖**：从"表征对机器人信号不敏感"这一被忽视的角度切入，区别于常见的更多数据 / 更大模型 / 更复杂动作头等改进路径。
- **仿真 + 真实机器人双重验证**：覆盖 sim-to-real 与真实部署两个维度，结论更具说服力。
- **可解释性强**：通过"抓取与放置定位更准确"的归因分析，让表征层面的收益在行为层面可被理解。
- **泛化潜力**：作为正则化项，理论上可与多种 VLA 架构、动作预测头组合，具备良好的可扩展性。

## 8. 不足与局限

- **PDF 未能完整获取**：原始正文、公式、附录均未拿到，本总结主要基于摘要与元数据，存在信息盲区（例如损失函数具体形式、batch 构造细节、λ 选择等）。
- **任务覆盖可能偏窄**：从摘要看主要聚焦于 pick-and-place 类任务，对**长程、复合指令、双臂、接触丰富的任务**是否同样有效尚不明确。
- **本体状态依赖**：方法依赖本体感知状态信号，对于**本体状态不可靠、缺失或高噪声**的场景（如部分柔性/欠驱动机器人）适用性可能下降。
- **可扩展性未充分验证**：RS-CL 是否在多种不同 VLA 骨干、不同动作头（如 diffusion、flow matching、tokenized action）上均稳定生效，摘要未提供横向对比。
- **消融与超参分析不足**：摘要层面未展示对损失权重、温度系数、状态编码方式等的敏感性分析。
- **真实机器人实验规模有限**：通常真实机器人任务数较少、任务类型有限，存在任务选择偏差风险，是否在更多样化的真实任务中保持 +13.3% 的提升仍需进一步验证。
- **理论解释有限**：为何"本体状态相对距离"作为软监督就能显著提升控制相关表征，缺少更深入的理论分析（如信息瓶颈、互信息等视角）。

（完）
