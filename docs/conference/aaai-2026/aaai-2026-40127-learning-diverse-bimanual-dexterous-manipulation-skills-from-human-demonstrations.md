---
title: Learning Diverse Bimanual Dexterous Manipulation Skills from Human Demonstrations
title_zh: 从人类演示中学习多样化双手灵巧操作技能
authors: "Bohan Zhou, Haoqi Yuan, Yuhui Fu, Zongqing Lu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40127/44088"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过人类演示的模仿学习实现双手灵巧操作
tldr: 该论文针对双手灵巧操作中高维动作空间和任务复杂性的挑战，提出BiDexHD框架，通过教师-学生策略从人类演示中高效学习多样化技能。框架统一了现有数据集的任务构建，并实现了有效的策略迁移。实验结果表明，该方法在多个双手操作任务上显著提升了技能多样性和学习效率，为通用双手操作能力的发展奠定了坚实基础。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40127/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1807, \"height\": 564, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40127/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1810, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40127/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 841, \"height\": 329, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40127/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 450, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40127/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1691, \"height\": 522, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40127/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 828, \"height\": 371, \"label\": \"Table\"}]"
motivation: 现有双手机器人操作面临高维动作空间和任务复杂性挑战，且缺乏多样化基准。
method: 提出BiDexHD框架，利用教师-学生策略学习，统一从现有数据集构建任务并迁移策略。
result: 在多种双手操作任务上展示了高效学习和技能多样性。
conclusion: 证明从人类演示学习双手操作技能的有效性，为通用技能发展奠定基础。
---

## Abstract
Bimanual dexterous manipulation is a critical yet underexplored area in robotics. Its high-dimensional action space and inherent task complexity present significant challenges for policy learning, and the limited task diversity in existing benchmarks hinders general-purpose skill development. Existing approaches largely depend on reinforcement learning, often constrained by intricately designed reward functions tailored to a narrow set of tasks. In this work, we present a novel approach for efficiently learning diverse bimanual dexterous skills from abundant human demonstrations. Specifically, we introduce BiDexHD, a framework that unifies task construction from existing bimanual datasets and employs teacher-student policy learning to address all tasks. The teacher learns state-based policies using a general two-stage reward function across tasks with shared behaviors, while the student distills the learned multi-task policies into a vision-based policy. With BiDexHD, scalable learning of numerous bimanual dexterous skills from auto-constructed tasks becomes feasible, offering promising advances toward universal bimanual dexterous manipulation. Experiments on TACO tool-using dataset spanning 141 tasks across 6 categories demonstrate a task fulfillment rate of 74.59% on trained tasks and 51.07% on unseen tasks. We further transfer BiDexHD to 11 ARCTIC collaborative tasks and achieve an average of 80.49% task fulfillment rate on trained tasks and 65.99% on unseen task. All empirical results demonstrate the effectiveness and competitive zero-shot generalization capabilities of BiDexHD.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 双手灵巧操作（bimanual dexterous manipulation）是机器人学中重要但尚未充分探索的领域。
- 核心挑战：动作空间高维、任务内在复杂性高，导致策略学习困难；现有基准（benchmark）任务多样性有限，阻碍通用技能的发展。
- 现有方法主要依赖强化学习（RL），但需要为每个任务精心设计特定的奖励函数，不仅扩展性差，也难以泛化到更多任务。
- 近年也有方法基于遥操作（teleoperation）收集数据，但需人工介入，难以规模化。
- 作者提问：能否以一种统一且可扩展的方式学习多样化的双手灵巧操作技能？
- 答案：利用人类演示（human demonstrations），这些数据更容易通过数据手套或动作捕捉设备收集，且行为更符合人类习惯。
- 为此提出 **BiDexHD** 框架，能自动将人类双手操作数据集转化为仿真中的一系列任务，并通过教师-学生（teacher-student）策略学习实现高效技能获取。

## 2. 方法论：核心思想、关键技术细节

### 核心思想
- 提出三阶段框架：从人类演示数据集自动构造任务 → 基于状态的教师策略多任务强化学习 → 基于视觉的学生策略蒸馏。
- 避免任务特定的奖励工程，设计通用两阶段奖励函数，覆盖所有自动构造的以物体为中心的任务。
- 采用教师-学生范式，教师在训练时利用先验信息（物体精确状态），学生仅依赖点云和多视角 RGB-D 信息，便于真实世界部署。

### 关键技术细节

- **阶段一：任务构造（Task Construction）**
  - 从人类双手操作数据集（如 TACO、ARCTIC）中提取轨迹，包含工具和物体的位姿序列、双手 MANO 参数等。
  - 预处理：利用 MANO 模型获取手的关节点和指尖位置（只保留 LEAP Hand 的 4 根手指），形成统一轨迹表示。
  - 在 Isaac Gym 中并行构造任务：初始化双臂+双手+工具/物体，固定初始关节角，通过正向运动学计算手腕和指尖位置，并利用 AnyTeleop 和逆运动学优化手/臂关节角度，使之与人类姿态对齐；最终筛选出有效任务。

- **阶段二：基于状态的多任务策略学习（Multi-Task State-Based Policy Learning）**
  - 任务分为两个子阶段（Stage 1 & Stage 2），共享一套通用的两阶段奖励函数。
  - **Stage 1：仿真对齐（Simulation Alignment）**
    - 目标：将仿真中工具和物体的初始位姿移动并调整到演示轨迹第一步的参考位姿。
    - 奖励函数组成：
      - 接近奖励（r_appro）：激励双手手掌和指尖靠近预计算的抓取中心（基于演示数据中最近的物体表面点）。
      - 提升奖励（r_lift）：在手掌和指尖足够接近抓取中心的前提下，激励物体提升到参考位姿（位置项 + 四元数距离惩罚项）。
      - 奖励（r_bonus）：当物体位置与参考位的距离小于阈值 ε_succ 时给予正向奖励，且连续保持 u 步才算成功。
    - 总奖励 r_align = w1*r_appro + w2*r_lift + w3*r_bonus。

  - **Stage 2：轨迹跟踪（Trajectory Tracking）**
    - 对齐成功后，双手需保持抓握并精确跟踪演示的后续轨迹。
    - 跟踪奖励 r_track = exp(-w_t * ‖x_t_i - x_hat_i‖₂)，其中 x_hat_i 为演示轨迹第 i 步的物体位置，x_t_i 为仿真中对应步的位置（通过跟踪频率 f 映射）。
    - 总奖励 r_total = r_align + w4*r_track。

  - **算法**：采用独立 PPO（IPPO）训练每个手的策略，两个智能体独立观测并行动。对比了集中式 PPO（单个策略输出两个手动作）。

- **阶段三：基于视觉的策略蒸馏（Vision-Based Policy Distillation）**
  - 使用 DAgger（on-policy 模仿学习）将一组教师策略蒸馏为一个视觉策略。
  - 学生策略输入：机器人本体感觉（关节角度/速度、手腕位姿、指尖位置）+ 物体点云（从物体表面预采4096点，并根据当前位姿变换并加噪）+ 可选的 K 步未来物体位姿。
  - 将学生策略做成轨迹条件化的上下文策略 π(aside_t | oside_t, pside_t, aside_{t-1})，有利于泛化到新物体和新任务。
  - K=0 时可屏蔽未来信息，仅依赖点云和本体感觉。

## 3. 实验设计

### 数据集
- **TACO 工具使用数据集**：141 个任务，覆盖 6 个类别（Dust, Empty, Pour in some, Put out, Skim off, Smear），均为双手使用工具操作目标物体的演示。
  - 将任务按语义分组为 16 个语义子任务，每个子任务对应一种动作+同类工具+同类物体。
  - 80% 训练/20% 测试。测试集分为组合任务（Test Comb：物体和工具均在训练集中见过）和新任务（Test New：物体或工具有未见过的实例）。
- **ARCTIC 协作数据集**：11 个双手协作任务（单一物体），其中 8 个用于多任务训练，3 个用于测试。

### 评估指标
- **m1**：Stage 1 平均成功率（物体连续 u 步保持参考位姿，距离/四元数误差 < ε_succ）。
- **m2**：Stage 2 平均跟踪率（整个轨迹中物体每步跟踪误差 < ε_track 的比例），作为任务完成度主要指标。
- 默认 ε_succ = ε_track = 0.1。

### 对比方法
- **教师阶段对比**：
  - BiDexHD-IPPO（独立 PPO）
  - BiDexHD-PPO（集中式 PPO）
  - 消融变体：无 Stage 1（w/o stage-1）、无功能性抓取中心（w/o gc）、无奖励（w/o bonus）
- **学生阶段对比**：
  - BiDexHD-IPPO+DAgger（本文完整方法）
  - BiDexHD-PPO+DAgger
  - 行为克隆（BC）：使用 DexPilot 将人手运动重定向到机器人关节角度形成静态数据集直接模仿。
- **不同 K 值消融**：K = 0, 1, 2, 5。
- **跨数据集迁移**：在 ARCTIC 上验证 BiDexHD-IPPO 和 BiDexHD-IPPO+DAgger。

## 4. 资源与算力

- 论文中未明确说明具体使用的 GPU 型号、数量、训练时长等算力资源。
- 提及使用 Isaac Gym 进行 GPU 加速仿真和并行任务训练，但未给出详细配置。
- 从方法描述（并行处理 141 个任务、多任务 IPPO 训练）推断需要较强的 GPU 算力，但无法获取精确数据。

## 5. 实验数量与充分性

- **主实验（TACO）**：完整对比了不同教师策略以及学生策略在训练集、组合测试集、新物体测试集上的 m1 和 m2，覆盖 6 个大类。
- **消融实验**：
  - 教师阶段：对比 w/o stage-1, w/o gc, w/o bonus 三个变体，每个均报告 m1 和 m2，验证了每个组件的必要性。
  - 学生阶段：对比 DAgger 与 BC，并消融 K 值（0,1,2,5）考察未来步信息的影响。
- **跨数据集泛化**：在 ARCTIC 数据集上重复类似实验，证明框架的可迁移性。
- **实验充分性评价**：
  - 实验设计较为充分，覆盖多个维度（不同方法、关键组件消融、不同数据集、零样本泛化）。
  - 指标 m1 和 m2 合理反映任务完成质量，且对阈值敏感性在附录讨论。
  - 实验公平：所有方法在相同的任务构造、仿真环境和评估协议下比较，对比基线（BC）也做了相应处理。
  - 但缺少真实机器人上的部署验证，全部在仿真中进行。

## 6. 主要结论与发现

- BiDexHD 框架能够从人类演示中有效学习多样化的双手灵巧操作技能，自动构造任务并统一训练。
- **教师阶段**：
  - BiDexHD-IPPO 显著优于 BiDexHD-PPO（IPPO 更易学到鲁棒技能，独立策略适应类似任务更好）。
  - 两阶段奖励设计（含对齐阶段）至关重要：无 stage-1 导致大多数任务失败。
  - 功能性抓取中心优于几何中心，尤其对带手柄/ flat 物体。
  - 奖励（r_bonus）能提升阶段转换感知和跟踪精度。
- **学生阶段**：
  - BiDexHD-IPPO+DAgger 在训练任务上达到 m2=74.59%，在所有未见任务上平均 m2=51.07%，证明良好零样本泛化能力。
  - 视觉学生策略对点云特征更敏感，而非特定 one-hot 标识符，因此在新物体上泛化显著优于状态基策略。
  - BC 完全失败，表明静态模仿无法应对仿真动力学和观测漂移。
  - 未来步条件（K）影响不大，即使 K=0 也能达到接近最优性能，但 K>0 提供额外运动线索。
- 跨数据集（ARCTIC）同样有效，证明框架的通用性和迁移性。

## 7. 优点

- **统一性**：提出一个通用框架，可从任意双手操作轨迹自动构造任务并训练，无需人工设计任务集或奖励函数。
- **可扩展性**：任务构造和数据驱动流程支持大量任务并行学习，易于扩展。
- **无任务特定奖励设计**：两阶段奖励函数适用于所有以物体为中心的操作任务，避免繁琐的手动调参。
- **教师-学生范式**：教师利用先验信息高效学习，学生蒸馏为纯视觉策略（点云+本体感觉），解决高维观察空间挑战，并具备零样本泛化能力。
- **功能性抓取中心**：基于演示数据准确确定抓取目标点，使学习更加稳定、类人。
- **多数据集验证**：在 TACO（6类141任务）和 ARCTIC（11任务）上均取得显著效果，证明方法通用性。
- **消融全面**：对每个重要设计选择（stage-1、抓取中心、奖励、K 值）进行实验分析，结论可靠。

## 8. 不足与局限

- **实验场景局限**：所有实验在仿真（Isaac Gym）中进行，未在真实机器人上部署验证，从仿真到现实的迁移效果未知。
- **依赖演示数据质量**：任务构造和教师学习高度依赖人类演示的准确性和完整性，对于演示中存在的错误（如抓取不稳定、轨迹不流畅）可能会导致学习失败。
- **新物体泛化仍有瓶颈**：在状态基策略上，新物体泛化显著下降（Test New 的 m2 仅 21.34%），即使视觉蒸馏后提升到 53.71%，仍有较大提升空间。
- **跟踪精度不够精细**：作者自己也指出需要更精准的空间和时间跟踪策略，未来工作是更好的跟踪方法。
- **未处理动态交互**：目前任务集中于工具-物体的静态/半动态操作，未涉及形变物体操作、双手交接（handover）等复杂动态场景。
- **未讨论算力需求**：论文未提供训练所需的 GPU 资源、时间等信息，不利于复现和实际部署评估。
- **奖励函数虽然通用但仍需调整权重**：两阶段奖励函数中的权重（w1-w4）可能在不同类别任务间需要微调，论文未讨论权重敏感性。

（完）
