---
title: Learning Object-Centric Motion Priors from Human for Robotic Dexterous Manipulation
title_zh: 从人类学习中学习面向对象的运动先验用于机器人灵巧操作
authors: "Zhengdong Hong, Guofeng Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38892/42854"
tags: ["query:rob-il"]
score: 7.0
evidence: 从人类演示中学习运动先验用于灵巧操作
tldr: 灵巧操作因高维性和复杂性而困难。本文利用人类-物体交互数据集，学习面向对象的运动先验，预测未来手-物状态，作为强化学习的通用奖励项。实验在仿真和真实世界任务中超越现有方法，展示了从人类数据中提取可迁移知识的有效性。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38892/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1845, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38892/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1850, \"height\": 608, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38892/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1840, \"height\": 1050, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38892/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 547, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38892/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 828, \"height\": 630, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 485, \"height\": 334, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 850, \"height\": 303, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 302, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1609, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38892/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1613, \"height\": 300, \"label\": \"Table\"}]"
motivation: 解决灵巧操作中奖励工程繁琐且泛化难的问题。
method: 从人类-物体交互数据学习面向对象的运动先验，预测未来状态作为奖励。
result: 在多个操作任务中超越现有方法。
conclusion: 提出利用人类数据学习运动先验增强灵巧操作。
---

## Abstract
Manipulating diverse objects with multi-fingered dexterous hands is challenging due to the high dimensionality and complex dynamics. Human-Object Interaction (HOI) datasets provide rich knowledge about task information and embodied interactions. Instead of solely imitating the human demonstrations, our method learns to holistically predict future hand-object states by leveraging these datasets. The predicted future states of the object can serve as a general-purpose reward term for reinforcement learning, reducing reliance on task-specific reward engineering and enhancing generalization across tasks. We conduct extensive experiments on three manipulation tasks in simulation and the real world. Our approach outperforms existing SOTA methods in both success rate and generalizability on novel objects. Furthermore, we validate the cross-embodiment compatibility of our methods by successfully deploying the skills on different robot hands.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：多指灵巧手的灵巧操作面临高维动作空间和复杂接触动力学的挑战。现有方法（如基于模型的轨迹优化、无模型强化学习、模仿学习）各有局限：强化学习需要大量探索和繁琐的任务特定奖励工程设计，模仿学习需要昂贵的机器人示范数据，而传统方法难以泛化到新物体和新场景。
- **利用人类数据的动机**：互联网规模的人类视频和人类-物体交互（HOI）数据集（如Dex-YCB、ARCTIC）蕴含丰富的操作经验，且容易获取。但以往工作往往只关注单纯模仿人类手臂运动或设计任务特定奖励，忽视了人类在操作过程中同时在做“状态预测”这一关键认知能力。
- **整体含义**：本文提出从人类数据中学习**面向对象的运动先验（object-centric motion priors）**，通过整体预测未来手-物体状态，将物体状态的预测作为强化学习的通用奖励项，从而减少对任务特定奖励的依赖，提高跨任务和跨本体的泛化能力，并实现零样本仿真到真实世界的迁移。

## 2. 论文提出的方法论
- **核心思想**：将人类-物体交互视为整体，训练一个**自回归运动预测器**来预测未来的手部和物体姿态。这些预测轨迹（尤其是物体轨迹）作为强化学习的引导信号，让机器人学习如何像数据中描述的那样操作物体，而非仅模仿手部形态。
- **关键技术细节**：
  1. **手-物体姿态预测（HOI Motion Predictor）**：
     - 使用 Dex-YCB 和 ARCTIC 数据集的6自由度手-物体姿态序列。
     - 物体形状通过最远点采样（FPS）提取100个点的点云，经PointNet编码为特征。
     - 历史手-物体姿态（10步）与物体特征拼接，送入6层GPT-2 transformer模型，以自回归方式预测后续姿态。
     - 训练损失：`L = α∥̂s_h - s_h∥² + β∥̂s_o - s_o∥²`，其中α=1，β=2。
  2. **机器人-物体轨迹提取**：
     - 将预测的人手姿态通过优化重定向（retargeting）映射到机器人手关节，优化目标为最小化指尖位置差，并包含关节限制和时域平滑。
  3. **轨迹引导的强化学习**：
     - 采用PPO算法，状态包含机器人关节位置和物体6D位姿，动作包含末端执行器delta位姿和手部delta关节位置。
     - 奖励函数包含四项：
       - **跟随奖励** R_f：鼓励机器人手跟随参考手部运动（关节位置、末端位置、末端方向）。
       - **物体跟随奖励** R_o：鼓励机器人使物体姿态接近预测的物体姿态（使用指数函数计算位姿差异）。
       - **接触奖励** R_contact：鼓励拇指和至少另一手指接触物体。
       - **成功奖励** R_success：任务成功时给予大奖励（障碍物任务中增加碰撞惩罚）。
     - 奖励权重经过精心调参，但所有任务共享相同的奖励结构（除障碍物任务修改接触惩罚）。
  4. **Sim-to-Real 迁移**：
     - 通过系统辨识调整仿真机器人参数（PID、力矩限）以匹配真实机器人。
     - 采用域随机化（摩擦、物体尺度、重量、观测噪声等）增强鲁棒性。

## 3. 实验设计
- **数据集与场景**：
  - 训练HOI预测器的数据集：Dex-YCB（单手机器人手，部分物体）、ARCTIC（双臂铰接物体操作）。
  - 测试任务：
    1. **YCB物体抓取**：抓取并提升10cm，包括5个Dex-YCB物体、5个非Dex-YCB物体、5种随机初始位姿。
    2. **铰接物体操作**：旋转铰接物体超过30度，包括ARCTIC中的laptop/box/mixer以及日常物体（real laptop, larger box, toy coffee machine）。
    3. **障碍物抓取**：在路径上放置已知但位置变化的障碍物，要求过程中任何部分不得触碰障碍物。
    4. **跨本体测试**：替换为不同型号的灵巧手（PSYONIC Ability Hand、ROBOTERA XHand1、Inspire hand）。
- **对比方法**：
  - ViviDex、AdaDexGrasp、ManipTrans、HOP（使用RL微调）、PPO w/o following（用到达奖励代替跟随奖励）、Obj-Dex（仅铰接物体任务）。
- **评估指标**：任务成功率（success rate）。

## 4. 资源与算力
- **硬件**：单张 NVIDIA RTX 4090 GPU（24GB）和 i7-14700K CPU。
- **并行环境**：1024个环境并行运行（GPU并行训练和渲染）。
- **训练速度**：平均每秒约10000步（steps per second）。
- **训练步数**：PPO策略训练1百万步（1M steps）后收敛。
- **说明**：文中**未明确给出总训练时长**（可大致估算：1M步 / 10000步/秒 ≈ 100秒，但考虑到环境交互和网络更新，实际可能更长，但原文未提供具体小时数）。HOI运动预测器的训练时间未提及。

## 5. 实验数量与充分性
- **仿真实验**：每种条件使用5个随机种子，每个种子训练后评估100次，取平均成功率。
- **真实机器人实验**：每个条件重复20次，计算成功率。
- **实验组数**：
  - YCB抓取：仿真和真实世界各6行数据（Dex-YCB物体、非Dex-YCB物体、新位姿）共3个设置，包含5个物体或5种位姿，每个方法比较。
  - 铰接物体：仿真和真实世界各2个设置（ARCTIC物体、日常物体），共3个方法对比。
  - 障碍物抓取：仿真和真实世界各2个设置（Dex-YCB障碍物、3D打印障碍物），5个物体变化。
  - 跨本体测试：3种机械手，在YCB抓取和铰接物体任务上各测试一次。
  - 消融实验：移除R_o和R_contact，在YCB抓取上（5个种子）显示学习曲线。
- **充分性与公平性评价**：
  - 对比方法覆盖了该领域最新SOTA（ViviDex、AdaDexGrasp、ManipTrans、HOP等）。
  - 测试任务多样（抓取、铰接操作、障碍物规避、不同机器人本体），涵盖“seen/unseen”物体和位姿。
  - 报告了仿真和真实世界结果，减少过拟合风险。
  - 消融实验证明了关键奖励项的重要性。
  - **潜在偏差**：未专门讨论超参数敏感性，但奖励权重在多任务上保持一致，减轻了过调风险。障碍物类型仅5+5种，泛化性有限。所有实验在同一硬件平台完成，公平性有保障。

## 6. 论文的主要结论与发现
- 利用HOI数据集的运动先验进行整体状态预测，可以为强化学习提供**通用且任务无关的奖励引导**，显著减少任务特定奖励工程设计。
- 在YCB物体抓取、铰接物体操作、障碍物抓取三个任务中，所提方法在**成功率和泛化性能（新物体、新位姿）上均超越现有SOTA方法**（如ViviDex、AdaDexGrasp、ManipTrans、HOP等）。
- 物体跟随奖励（R_o）对稳定和高效策略学习**至关重要**（去除后样本效率骤降）；接触奖励（R_contact）有助于稳定的训练。
- 方法支持**零样本Sim-to-Real迁移**，且能**跨本体泛化**到不同型号的灵巧手（性能一致且良好）。

## 7. 优点（方法或实验设计的亮点）
- **整体预测思路新颖**：不是单纯模仿人手，而是同时预测手和物体的未来状态，将物体状态作为reward信号，使奖励更具通用性和任务适应性。
- **奖励设计简洁且任务无关**：统一奖励形式（R_f + R_o + R_contact + R_success）适用于多种任务（仅障碍物惩罚调整），极大降低了针对每个任务重新设计奖励的成本。
- **跨本体兼容性**：通过运动重定向和适应性优化，在多种机械手上取得一致好成绩，证明了方法的可迁移性。
- **高效的Sim-to-Real**：系统辨识+域随机化实现零样本迁移，真实机器人成功率接近仿真表现。
- **实验充分**：仿真和真实对比多个SOTA，涵盖不同物体、不同位姿、不同本体，并包含消融研究，实验设计公平且覆盖全面。

## 8. 不足与局限
- **对HOI数据集依赖**：方法依赖具有3D手-物体姿态标注的数据集（如Dex-YCB、ARCTIC），此类数据获取成本仍较高。对于未标注数据域需要额外标注或适应。
- **物体模型需求**：点云提取需要物体网格模型，且使用FoundationPose进行6D跟踪，对新物体或不可见物体需要在线重建或模板匹配，可能带来感知误差。
- **任务范围有限**：测试的任务集中在抓取、铰接操作和简单避障，未涉及更复杂的动态操作（如物体重组、工具使用、多步任务）。动力学丰富的任务可能还需更精细的奖励。
- **障碍物规避策略**：在障碍物任务中，对参考轨迹中与障碍物碰撞的帧做了过滤（disable following reward），这一手动预处理限制了自动化的可能。
- **计算资源描述简略**：未提供HOI运动预测器的训练成本，仅提及强化学习在单卡RTX 4090上运行，训练1M步。整体的计算效率和可扩展性讨论不足。
- **泛化性边界**：尽管在新型物体和位姿上显著优于基线，但成功率仍有提升空间（如现实世界novel pose仅65%），鲁棒性未见极限测试（如极端光照、遮挡、物体形变）。
- **跨任务一致的奖励权重**：虽然避免了过度调参，但不同任务的最优权重可能有差异，统一权重可能不是最优，文中未做灵敏度分析。

（完）
