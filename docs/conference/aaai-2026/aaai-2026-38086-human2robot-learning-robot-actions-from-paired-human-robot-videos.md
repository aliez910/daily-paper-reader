---
title: "Human2Robot: Learning Robot Actions from Paired Human-Robot Videos"
title_zh: "Human2Robot: 从配对的人-机器人视频学习机器人动作"
authors: "Sicheng Xie, Haidong Cao, Zejia Weng, Zhen Xing, Haoran Chen, Shiwei Shen, Jiaqi Leng, Zuxuan Wu, Yu-Gang Jiang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38086/42048"
tags: ["query:rob-il"]
score: 9.0
evidence: 从配对的人-机器人视频学习机器人动作，解决精细对齐问题
tldr: "本文提出Human2Robot，将精细人机对齐视为条件视频生成问题，并构建了包含2600段精确同步人-机器人视频的H&R数据集。通过该数据集学习机器人动作，克服了已有方法忽略帧级动态的局限。实验表明该方法在复杂操作任务上性能优越且泛化能力强，精细对齐的数据集与生成范式推动了机器人从演示学习的研究。"
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38086/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 746, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38086/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 260, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38086/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1796, \"height\": 1033, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38086/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1830, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38086/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1830, \"height\": 327, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38086/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1105, \"height\": 343, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38086/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 704, \"height\": 328, \"label\": \"Table\"}]"
motivation: 现有方法忽略了帧级动态，限制复杂操作和泛化。
method: 将人-机器人对齐作为条件视频生成问题，构建精确同步数据集。
result: 在复杂操作任务上表现出改进的性能和泛化能力。
conclusion: 精细对齐的数据集和生成范式推动了机器人从演示学习。
---

## Abstract
Distilling knowledge from human demonstrations is a promising way for robots to learn and act. Existing methods, which often rely on coarsely-aligned video pairs, are typically constrained to learning global or task-level features. As a result, they tend to neglect the fine-grained frame-level dynamics required for complex manipulation and generalization to novel tasks. We posit that this limitation stems from a vicious circle of inadequate datasets and the methods they inspire. To break this cycle, we propose a paradigm shift that treats fine-grained human-robot alignment as a conditional video generation problem. To this end, we first introduce H&R, a novel third-person dataset containing 2,600 episodes of precisely synchronized human and robot motions, collected using a VR teleoperation system. We then present Human2Robot, a framework designed to leverage this data. Human2Robot employs a Video Prediction Model to learn a rich and implicit representation of robot dynamics by generating robot videos from human input, which in turn guides a decoupled action decoder. Our real-world experiments demonstrate that this approach not only achieves high performance on seen tasks but also exhibits significant one-shot generalization to novel positions, objects, instances, and even new task categories.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有从人类演示中学习机器人动作的方法通常依赖**粗略对齐**的人-机器人视频对，只能学习全局或任务级特征，忽略了**帧级精细动态**，导致在复杂操作和新任务上的泛化能力严重不足。
- **根源分析**：作者指出，当前领域存在一个**恶性循环**——缺乏精细对齐的数据集使得方法局限于粗粒度学习，而粗粒度方法的流行又抑制了精细数据集的构建。
- **整体含义**：本文旨在打破这一循环，提出将**精细人-机器人对齐**重新定义为**条件视频生成**问题，通过生成机器人视频来隐式学习帧级的运动对应关系，从而获得更强的泛化能力。

### 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：以人类演示视频为条件，训练一个**视频预测模型（VPM）** 生成对应的机器人臂运动视频，从而让模型内化操纵的动态过程；再将VPM中蕴含的预测特征作为先验，训练一个**动作解码器**来输出具体动作指令。
- **关键技术与流程**：
  - **H&R数据集收集**：使用VR遥操作系统，通过坐标系统一映射将人手运动精确映射至机器人臂，实现两者在第三视角视频中的精细同步，获取2600段人-机器人配对视频。
  - **第一阶段：视频预测模型（VPM）**：
    - 基于预训练**Stable Diffusion**构建。
    - 包含 **Spatial UNet（S-UNet）** 提取机器人臂特征、**Behavior Extractor** 提取人类视频中的位置和运动线索、**Spatial-Temporal UNet（ST-UNet）** 进行时序建模。
    - 分两小阶段训练：首先训练单帧图像生成能力（冻结时序层），然后训练30帧视频生成能力（激活时序层）。
    - 优化目标：噪声预测损失 \( \mathcal{L}_G = \mathbb{E}_{z_{t_s},c,\epsilon,t_s} \| \epsilon - \epsilon_\theta(z_{t_s}, c, t_s) \|^2_2 \)。
  - **第二阶段：动作解码器**：
    - 冻结VPM参数，将其视为**视觉编码器**：对输入的人类视频加噪至强度 \(t=K\)，仅做一步去噪，取第一个上采样层的输出特征 \(F^{VPM}\)。
    - 动作解码器由 **Video Former**（用可学习token聚合视频特征）和 **Diffusion Policy**（对动作进行扩散去噪）组成。
    - 优化目标：动作噪声预测损失 \( \mathcal{L}_A = \mathbb{E}_{a_k, F^{VF}, \epsilon, k} \| \epsilon - \epsilon_\phi(a_k, F^{VF}, k) \|^2_2 \)。
  - **KNN + Human2Robot**：为在测试时无需提供人类视频，使用DINOv2和CLIP对当前场景第一帧提取特征，在训练集中检索最相似的人类视频作为条件。

### 3. 实验设计：数据集、场景、基准、对比方法

- **数据集**：自建 **H&R 数据集**，包含2600段episode，帧数300~600，覆盖4种基本任务（推、拉、抓取、放置等）和6种长程任务。重点在**pick-and-place**类任务上进行训练和测试。
- **测试场景**：
  - **Seen tasks**：训练集中出现的基本任务（推/拉、抓取、旋转）。
  - **泛化测试**（各20次试验）：外观变化、位置变化、实例变化（从未见过的物体，如乒乓球、香蕉）、背景变化、任务组合（如先拉盘子再放方块）、**全新任务**（如写字母“H”“R”）。
- **对比方法**：
  - Diffusion Policy (DP) – 语言条件
  - XSkill – 人类视频条件，自监督
  - Video Prediction Policy (VPP) – 语言条件，视频生成预训练
  - Action Decoder w. Human – 直接用人类视频特征训练动作解码器
  - Human2Robot w/o Pretrain – 跳过硬件事前预训练
  - Human2Robot w. KNN – 本文KNN变体
  - **Human2Robot (Ours)** – 完整模型

### 4. 资源与算力

- **第一阶段（VPM训练）**：4张 NVIDIA A100 GPU，训练 **3天**（在2600个任务视频上）。
- **第二阶段（动作解码器训练）**：8张 NVIDIA A100 GPU，训练 **约6小时**（在简单task上，以及写作任务的play data上单独6小时）。
- 论文未提供单卡模型参数量或推理开销的具体数据，但明确指出VPM在推理时只做一次特征提取，不会带来显著计算负担。

### 5. 实验数量与充分性

- **实验数量**：
  - 在基本任务上报告了**Push & Pull、Pick & Place、Rotation**三类成功率，每组20次试验。
  - 进行了**6种泛化设置**实验（外观、位置、实例、背景、组合、全新任务），各20次试验。
  - 消融研究：对比了Action Decoder w. Human和Human2Robot w/o Pretrain，各任务下报告成功率。
  - 可视化：展示了VPM一步去噪和完整去噪结果与GT的对比。
- **充分性与公平性**：
  - 与多种代表性基线（DP、XSkill、VPP）直接对比，控制变量合理。
  - 消融实验清晰验证了VPM和视频预训练的必要性。
  - 统计试验次数（20次）在机器人操作论文中属常规设置，但未提供标准差或置信区间，略显不足。
  - 未在公开基准数据集（如RLBench、MetaWorld等）上进行评估，所有评测均基于自建场景，外部泛化证据稍弱。

### 6. 论文的主要结论与发现

- 在**seen tasks**上，Human2Robot取得**95%平均成功率**，显著高于DP（28%）、XSkill（53%）、VPP（80%）；甚至KNN变体也达到82%。
- 在**六个泛化设置**中，Human2Robot在几乎所有设置上都优于基线（例如实例泛化70%而基线为0%），展现了**强泛化能力**，尤其在其他方法完全失效的组合与全新任务上仍有效。
- **消融实验**证明：移除VPM或视频预训练都会导致成功率大幅下降（分别降至23%和10%），验证了生成式对齐和预训练的关键作用。
- **KNN+Human2Robot**可在无需人类视频输入时完成已见任务（平均82%），增强了系统实用性。
- **可视化**表明：VPM的一步去噪特征已包含足够运动信息，多步去噪结果与GT高度接近，验证了生成模型在机器人特征学习中的潜力。

### 7. 优点：方法或实验设计上的亮点

- **数据集创新**：首次构建**像素级精细同步**的人-机器人配对视频数据集（H&R），打破了数据瓶颈。
- **方法新颖**：将人-机器人对齐重定义为**条件视频生成**问题，通过生成过程隐式学习帧级动态，避免手动标注对应关系。
- **两阶段解耦设计**：先学视觉动态（生成），后学行为映射（动作），使得动作解码器能够直接利用生成模型中的运动先验，计算高效（一步去噪即可）。
- **强泛化验证**：不仅测试了常见变体（颜色、位置），还设计了任务组合和全新类别（写作），覆盖了实际部署中的多种挑战。
- **KNN扩展**：将历史演示作为条件库，实现了无需实时人类输入的闭环执行模式，增加部署灵活性。

### 8. 不足与局限

- **数据局限**：受限于遥操作系统的**具身差距**（手与夹爪形态不同），目前只能收集**pick-and-place**类数据，无法应对拧螺丝等灵巧操作；H&R数据集规模（2600段）相对较小，且长程任务比例不高（6%）。
- **实验局限**：所有评测均基于**自建场景**，未在独立第三方基准（如RLBench、CALVIN、ManiSkill等）上进行验证，可能高估方法的通用性；未报告成功率的标准差或多次运行统计分析。
- **写作任务证据不足**：写作训练数据是“随机运动”而非实际字符，虽然展示了泛化潜力，但仅演示了“H”“R”两个字母，缺乏对更复杂字符或笔画的系统评测。
- **泛化边界模糊**：论文未分析在背景杂乱或物体不出现时的失败案例，也未讨论光照、视角变化的影响；全新任务泛化（写作）是单独实验，未与其他方法在同一设置下严格对比。
- **推理时需人类视频**：完整的Human2Robot在测试时仍需提供对应人类视频，虽然KNN提供替代方案，但KNN的检索依赖训练集，对完全未见过任务不适用。
- **算力需求**：第一阶段训练需4×A100持续3天，对资源常规实验室可能门槛较高；第二阶段虽快，但整体成本不低。

（完）
