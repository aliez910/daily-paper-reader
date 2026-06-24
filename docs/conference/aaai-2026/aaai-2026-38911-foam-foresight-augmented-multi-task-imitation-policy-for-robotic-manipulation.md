---
title: "FoAM: Foresight-Augmented Multi-Task Imitation Policy for Robotic Manipulation"
title_zh: 预见增强的多任务模仿策略用于机器人操控
authors: "Litao Liu, Wentao Wang, Yifan Han, Zhuoli Xie, Pengfei Yi, Junyan Li, Wenzhao Lian"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38911/42873"
tags: ["query:rob-il"]
score: 9.0
evidence: 多任务模仿学习用于机器人操控，带有预见增强
tldr: 针对多任务模仿学习在机器人操控中动作可靠性不足和泛化困难的问题，提出了FoAM策略，通过引入多模态目标条件和预见增强模块，在动作重建的同时预测未来状态，有效避免了异常动作序列。实验表明，FoAM在多个操控基准上显著提升了动作的稳定性和对新任务的泛化能力，为多任务模仿学习提供了新的高效范式。该框架简洁易扩展，有望推动机器人技能学习研究。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38911/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 885, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38911/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 892, \"height\": 151, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38911/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 887, \"height\": 669, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38911/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 888, \"height\": 671, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38911/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1805, \"height\": 314, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38911/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38911/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 882, \"height\": 171, \"label\": \"Table\"}]"
motivation: 现有模仿学习策略在机器人操控中动作不可靠且难以泛化到新任务。
method: 提出FoAM策略，利用多模态目标输入和预见增强模块进行动作预测和未来状态建模。
result: 在仿真和真实机器人任务中，FoAM在动作可靠性和泛化性能上均优于基线方法。
conclusion: FoAM通过预见增强有效解决了多任务模仿学习中的关键挑战。
---

## Abstract
Multi-task imitation learning (MTIL) has shown significant potential in robotic manipulation by enabling agents to perform various tasks using a single policy. It simplifies the policy deployment and enhances the agent's adaptability across different scenarios. However, key challenges remain, such as maintaining action reliability (e.g., avoiding abnormal action sequences that deviate from nominal task trajectories) and generalizing to unseen tasks with a few expert demonstrations. To address these challenges, we introduce the Foresight-Augmented Manipulation (FoAM) policy, a novel MTIL policy that pioneers the use of multi-modal goal conditions as input and introduces a foresight augmentation in addition to the general action reconstruction. FoAM enables the agent to reason about its actions' visual consequences (foresight) and to be guided by these more expressive representations during task execution. Extensive experiments on over 100 tasks in simulation and real-world settings demonstrate that FoAM significantly enhances MTIL policy performance, outperforming state-of-the-art baselines by up to 41% in success rate. We released our simulation suites that include over 80 challenging tasks across more than 10 scenarios designed for manipulation policy training and evaluation.

---

## 论文详细总结（自动生成）

# 论文《FoAM: Foresight-Augmented Multi-Task Imitation Policy for Robotic Manipulation》详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究背景**：多任务模仿学习（Multi-Task Imitation Learning, MTIL）旨在通过单一策略使机器人完成多种操控任务，以简化部署并增强适应性。然而，现有 MTIL 策略存在两大关键挑战：
  1. **动作可靠性不足**：容易产生偏离名义任务轨迹的异常动作序列。
  2. **泛化能力受限**：在仅有少量专家演示时难以泛化到未见任务。
- **现有方法的局限**：
  - **单模态目标条件**：仅使用语言指令的策略（如 MT‑ACT、BAKU）在未见任务上很难泛化；仅使用目标图像的策略（如 Gimg‑ACT）虽然泛化较强，但存在**场景歧义**（同一目标图像可能对应不同任务，导致执行与意图不符）。
  - 收集目标图像往往需要人工参与（手绘草图或采集真实图像），降低了自动化程度。
- **论文动机**：受人类执行任务时能够预想完成状态并指导行动的能力启发，提出一种**预见增强**的 MTIL 策略，利用多模态目标条件（语言指令 + 目标图像）并结合动作后果的推理，以同时提升执行可靠性和泛化能力。

## 2. 方法论：核心思想与关键技术

### 2.1 整体思路
- 提出 **FoAM (Foresight‑Augmented Manipulation) 策略**，基于 Transformer 架构，采用条件变分自编码器（CVAE）框架。
- 在训练时，除了重建专家动作，还增加**预见分支**：让策略同时预测未来若干步的视觉帧（foresight），并与目标图像进行对齐损失，从而将动作与其视觉后果耦合。
- 在推理时，丢弃预见分支，只利用动作预测和指数时间平滑来生成轨迹。

### 2.2 多模态目标条件
- 使用**任务指令**（语言）和**目标图像**同时作为输入：
  - 语言指令通过预训练文本编码器（Gadre et al. 2023）得到 384 维特征，再投影至 512 维。
  - 目标图像通过预训练 ResNet18 编码为 300×512 的特征。
- 目标图像来源：可由**目标想象模块**（微调的 InstructPix2Pix）根据初始观察和指令自动生成，也可由人工采集。

### 2.3 目标想象模块
- 采用 InstructPix2Pix 并微调，训练数据包含：
  - RT‑1 数据集中的首帧与末帧对（约 16,000 对），对应任务名称作为指令。
  - 自采集的模拟与现实数据（约 4,000 对）。
- 训练：单个 NVIDIA H100 GPU，约 3 天，500 epoch。
- 推理：生成一张 480×640×3 目标图像平均约 4 秒。

### 2.4 预见增强（Foresight Augmentation）
- 将 CVAE 的 decoder 扩展为同时输出动作块 \(\hat{a}_{t:t+k}\) 和预见的视觉序列 \(\hat{f}_{t:t+k}\)（形状为 k×300×512）。
- 从预见序列中选取与目标图像时间对齐的一帧 \(\hat{g}_i = \hat{f}_{t:t+k}[k-t]\)。
- **损失函数**：
  \[
  L = \alpha L_{\text{action}} + \beta L_{\text{foresight}} + \gamma L_{\text{reg}}
  \]
  - \(L_{\text{action}}\)：动作 L1 损失。
  - \(L_{\text{foresight}}\)：\(\hat{g}_i\) 与目标图像 \(g_i\) 的 Huber 损失。
  - \(L_{\text{reg}}\)：KL 散度正则项。
  - 超参数：\(\alpha=1,\beta=2,\gamma=10\)，chunk size \(k\approx T\)（最大回合步长）。

### 2.5 训练与推理流程
- **训练**（Algorithm 1）：
  1. 从专家演示中采样动作、本体感知、观察、语言指令、目标图像。
  2. 编码潜变量 \(z \sim q_\phi(z|a_{t:t+k}, j_t)\)。
  3. 解码预测动作和预见序列。
  4. 计算总损失并更新参数。
- **推理**（Algorithm 2）：
  1. 设置潜变量 \(z=0\)。
  2. 依据当前观测和目标条件预测动作块 \(\hat{a}_{t:t+k}\)。
  3. 使用**指数时间聚合**（引入超参数 \(r\) 作为实际聚合范围，允许灵活调整）输出平滑动作 \(a_t\)。

### 2.6 网络架构
- 视觉编码：ResNet18 + FiLM 条件层，用于嵌入任务指令到图像特征。
- 语言编码：预训练文本编码器 → MLP 至 512 维。
- 目标图像编码：固定 ResNet18（不更新参数），输出 300×512。
- CVAE encoder：4 层 Transformer encoder。
- CVAE decoder：4 层 Transformer encoder + 7 层 Transformer decoder。
- 总参数量：训练约 160M，推理约 80M。

## 3. 实验设计

### 3.1 仿真环境与数据集
- **FoAM Benchmark**：基于 MuJoCo 构建的双臂 UR3e 系统，含 10 个多任务套件，共 **86 个仿真任务**，涵盖拾取、推、放置、插入、开门、滑动、转移等技能。
- 每个任务生成了 **50 个专家演示**（物体位置随机初始化）。
- 数据集频率 50 Hz，统一动作空间 14 维（双臂）。
- 相机为头戴式单目（480×640）。

### 3.2 真实世界环境
- 机器人：UFACTORY xArm 7 + 平行夹爪 + 静态 Orbbec Femto Bolt 相机 + 腕装 Intel RealSense D435。
- 共 **4 个多任务场景**（14 个任务）：试管拾取、插入孔位、水果入碗、苦瓜放入分层柜。
- 每个任务采集 50 个演示，物体在 50×60 cm 区域内随机初始化，频率 30 Hz。

### 3.3 对比方法
- **MT‑ACT**（语言条件）
- **BAKU**（语言条件）
- **Gimg‑ACT**（仅目标图像条件）
- **FoAM w/o FA**（多模态条件但无预见损失，作为消融）
- **FoAM**（完整方法）

### 3.4 评估协议
- 仿真：5 个任务类别（Dual‑Arm 12 任务、Block‑based 40 任务、Cabinet‑based 14 任务、Locker‑based 8 任务、Others 8 任务） + 4 个未见任务（修改颜色）。每个任务 **50 次测试**，报告平均成功率。
- 真实世界：每个场景依次执行所有子任务，每场景测试 10 个不同初始化位置，记录成功次数（如 Scenario I: 40 次）。
- 额外实验：**VLM‑FoAM 联合推理**（使用生成目标图像 vs 真实目标图像）、**鲁棒性分析**（外部干扰、物体被移除后反应）。

## 4. 资源与算力
- **目标想象模块微调**：单张 NVIDIA H100 GPU，约 3 天，500 epoch。
- **策略训练与评估**：
  - 服务器：8×NVIDIA RTX 4090D GPU（24 GB each）。
  - 推理端：笔记本单张 NVIDIA RTX 3060 GPU。
- 文中未详细说明各基线及 FoAM 的具体训练时长，但可推断使用了多卡并行。

## 5. 实验数量与充分性
- **总体实验量**：仿真中 **86 个任务** × 50 次测试 = 约 4300 次测试；真实世界 **14 个任务** × 10 次 = 140 次测试。加上消融、VLM 对比、鲁棒性实验，样本量较大。
- **消融实验**：通过 FoAM w/o FA 对比，验证了预见增强的有效性；通过多模态与单模态对比，验证了多模态条件优于单模态。
- **泛化测试**：设计了 4 个颜色修改的未见任务，评估了不同方法的零样本迁移能力。
- **公平性**：所有方法在同一硬件、同一数据集（专家演示相同）上训练和测试，对比方法均为公开的 SOTA。
- **充分性**：覆盖了多种任务类型（单臂、双臂、精细插入、歧义场景等）、仿真到真实、有干扰情况，实验设计较为全面。但真实任务数量（14 个）相对仿真偏少，且未包含长时间跨度任务。

## 6. 主要结论与发现
1. **多模态目标条件的优势**：同时使用语言+目标图像解决了单模态策略的泛化困难（语言）与场景歧义（图像）问题。
2. **预见增强的有效性**：FoAM 在所有任务类别上均优于 FoAM w/o FA（最高提升 41% 在双臂任务），表明对齐动作后果可学习更鲁棒的表示。
3. **泛化能力**：FoAM 在未见任务上成功率 66%，远超单语言条件方法（0%）和单图像方法（45%），而 FoAM w/o FA 仅 11%，说明预见增强能抵消语言条件对泛化的负面影响。
4. **VLM 生成目标图像**：VLM‑FoAM 在实际部署中表现可与使用真实目标图像相当，甚至略优（可能因生成图像风格一致，减少过拟合）。
5. **鲁棒性**：FoAM 能抵抗外部干扰并在物体脱落时尝试重抓取。
6. **性能总结**：FoAM 在仿真和真实世界多数场景中达到最高成功率，证明了其作为 MTIL 策略的有效性。

## 7. 优点
- **方法创新**：
  - 首次在多任务模仿学习中引入**预见损失**，将动作与未来视觉后果耦合。
  - 多模态目标条件设计灵活，可适配不同来源的目标图像（真实或生成）。
  - 将 VLM 无缝嵌入训练和推理，提高自动化程度。
- **实验严谨**：
  - 构建了大规模、多样化的仿真 benchmark（86 任务、10 场景），并开源。
  - 消融实验清晰，验证了各组件贡献。
  - 同时进行仿真和真实世界评估，考虑了歧义场景和鲁棒性。
- **实用贡献**：
  - 开源了首套基于 MuJoCo 的 UR3e 双臂系统及丰富任务套件，便于后续 MTIL 和 Sim2Real 研究。
  - 推理时通过可调聚合范围 \(r\) 灵活平衡效率与反应性。

## 8. 不足与局限
- **高精度任务表现有限**：在真实场景 I（试管拾取）和 II（插入孔位）中，FoAM 的成功率仍然不高（11/40 和 11/40），说明对细粒度操作仍需改进。
- **VLM 生成的不稳定性**：在复杂场景或操控对象较小时（如试管孔位），生成的目标图像可能出现语义错误（如插错孔），影响训练和推理质量。这受限于微调数据集规模及当前 VLM 的细粒度理解能力。
- **未见任务泛化仍有上升空间**：尽管 FoAM 较基线有提升，但在真实未见任务中仅 3/10（30%），离真正通用仍远。
- **数据依赖**：方法依赖较高质量的专家演示（每任务 50 个），收集成本高。且 VLM 微调需要大量带指令的编辑数据对。
- **实验覆盖**：
  - 仿真任务虽多，但全部在 MuJoCo 中，未在 RLBench 或 LIBERO 等标准库上验证，外部可比性有限。
  - 真实世界仅 4 场景，且未涉及长时序或复杂移动操控。
  - 未在公开的 MTIL 数据集（如 Open X‑Embodiment）上测试。
- **潜在偏差与公平性**：基线方法可能未针对该 benchmark 进行充分调优；超参数（如损失权重 \(\alpha,\beta,\gamma\) 和聚合范围 \(r\)）是在特定任务上选择的，可能影响公平对比。

（完）
