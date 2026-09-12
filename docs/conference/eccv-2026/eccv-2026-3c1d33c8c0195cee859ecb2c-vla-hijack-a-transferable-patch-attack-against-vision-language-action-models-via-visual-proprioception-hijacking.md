---
title: "VLA-Hijack: A Transferable Patch Attack against Vision-Language-Action Models via Visual Proprioception Hijacking"
title_zh: "VLA-Hijack:通过视觉本体感知劫持实现针对视觉-语言-动作模型的可迁移补丁攻击"
authors: "Jiyuan Fu, Kaixun Jiang, Jingkai Jia, Zhaoyu Chen, Xueyao Chen, Lingyi Hong, Shuyong Gao, Chenzhi Tan, Dingkang Yang, Wenqiang Zhang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4661.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 针对通用VLA策略的对抗补丁攻击研究
tldr: "视觉-语言-动作模型作为通用机器人策略存在严重对抗补丁漏洞,阻碍其在安全关键领域的部署。现有攻击多为白盒设定,过拟合于特定模型的动作输出空间,导致跨架构迁移性差。本文提出VLA-Hijack统一对抗框架,利用VLA模型必须先在视觉上定位自身机械臂这一根本性漏洞,设计可跨架构迁移的补丁攻击。该工作揭示了通用VLA模型的安全风险,为未来防御研究奠定基础。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 687, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 1024, \"height\": 559}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 718, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-004.webp\", \"caption\": \"\", \"page\": 5, \"index\": 4, \"width\": 656, \"height\": 658}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-005.webp\", \"caption\": \"\", \"page\": 5, \"index\": 5, \"width\": 656, \"height\": 656}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-006.webp\", \"caption\": \"\", \"page\": 5, \"index\": 6, \"width\": 658, \"height\": 656}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-007.webp\", \"caption\": \"\", \"page\": 5, \"index\": 7, \"width\": 656, \"height\": 656}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-008.webp\", \"caption\": \"\", \"page\": 5, \"index\": 8, \"width\": 870, \"height\": 872}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-009.webp\", \"caption\": \"\", \"page\": 5, \"index\": 9, \"width\": 870, \"height\": 868}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-010.webp\", \"caption\": \"\", \"page\": 5, \"index\": 10, \"width\": 872, \"height\": 872}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 870, \"height\": 872}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-012.webp\", \"caption\": \"\", \"page\": 6, \"index\": 12, \"width\": 562, \"height\": 560}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-013.webp\", \"caption\": \"\", \"page\": 6, \"index\": 13, \"width\": 646, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-014.webp\", \"caption\": \"\", \"page\": 6, \"index\": 14, \"width\": 1274, \"height\": 1180}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-015.webp\", \"caption\": \"\", \"page\": 6, \"index\": 15, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-016.webp\", \"caption\": \"\", \"page\": 6, \"index\": 16, \"width\": 646, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-017.webp\", \"caption\": \"\", \"page\": 6, \"index\": 17, \"width\": 646, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-018.webp\", \"caption\": \"\", \"page\": 6, \"index\": 18, \"width\": 562, \"height\": 560}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-019.webp\", \"caption\": \"\", \"page\": 13, \"index\": 19, \"width\": 3568, \"height\": 1767}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-020.webp\", \"caption\": \"\", \"page\": 13, \"index\": 20, \"width\": 3568, \"height\": 1767}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-021.webp\", \"caption\": \"\", \"page\": 13, \"index\": 21, \"width\": 3568, \"height\": 1767}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-022.webp\", \"caption\": \"\", \"page\": 13, \"index\": 22, \"width\": 3568, \"height\": 1767}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-023.webp\", \"caption\": \"\", \"page\": 14, \"index\": 23, \"width\": 1410, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-024.webp\", \"caption\": \"\", \"page\": 14, \"index\": 24, \"width\": 1410, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-025.webp\", \"caption\": \"\", \"page\": 14, \"index\": 25, \"width\": 1410, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-026.webp\", \"caption\": \"\", \"page\": 14, \"index\": 26, \"width\": 1410, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-027.webp\", \"caption\": \"\", \"page\": 14, \"index\": 27, \"width\": 1410, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-028.webp\", \"caption\": \"\", \"page\": 15, \"index\": 28, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-029.webp\", \"caption\": \"\", \"page\": 15, \"index\": 29, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-030.webp\", \"caption\": \"\", \"page\": 15, \"index\": 30, \"width\": 790, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-031.webp\", \"caption\": \"\", \"page\": 15, \"index\": 31, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-032.webp\", \"caption\": \"\", \"page\": 15, \"index\": 32, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-033.webp\", \"caption\": \"\", \"page\": 15, \"index\": 33, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-034.webp\", \"caption\": \"\", \"page\": 15, \"index\": 34, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-035.webp\", \"caption\": \"\", \"page\": 15, \"index\": 35, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-036.webp\", \"caption\": \"\", \"page\": 15, \"index\": 36, \"width\": 1092, \"height\": 932}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-037.webp\", \"caption\": \"\", \"page\": 15, \"index\": 37, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-038.webp\", \"caption\": \"\", \"page\": 15, \"index\": 38, \"width\": 960, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3c1d33c8c0195cee859ecb2c/fig-039.webp\", \"caption\": \"\", \"page\": 15, \"index\": 39, \"width\": 960, \"height\": 540}]"
motivation: "通用VLA模型对对抗补丁高度脆弱,现有攻击跨架构迁移能力差,威胁安全部署。"
method: "提出VLA-Hijack统一对抗框架,通过视觉本体感知劫持机制实现跨架构可迁移的补丁攻击。"
result: "显著提升对抗补丁在不同VLA架构间的迁移成功率,有效暴露通用策略的安全缺陷。"
conclusion: "揭示了VLA模型在部署前的安全风险,为后续防御机制研究提供重要参考与启示。"
---

## Abstract
While Vision-Language-Action (VLA) models have emergedas powerful generalist policies, their severe vulnerability to adversarialpatches significantly hinders their deployment in safety-critical domains.Moreover, existing patch attacks primarily focus on white-box settings,heavily overfitting to the specific action output space of the target model,which results in poor cross-architecture transferability. To overcome thislimitation, we propose VLA-Hijack, a unified adversarial framework thatbreaks the transferability bottleneck by exploiting a fundamental vulner-ability identified in this work: before planning any motion, a VLA modelmust first use visual information to locate its own robotic arm withinthe environment. Targeting this shared visual self-localization process,our approach concurrently optimizes Attention-Guided ProprioceptiveSuppression to inhibit the real robotic arm’s features, and MultimodalProprioceptive Injection to establish the patch as a surrogate "phantomembodiment". By alternating between semantic concept anchoring andvisual prototype projection, VLA-Hijack effectively severs the semanticrelationship between the agent’s true embodiment and its control pol-icy. Extensive experiments across diverse architectures (OpenVLA, Uni-VLA, and CronusVLA) demonstrate that VLA-Hijack achieves superioroptimization efficiency in white-box settings and sets a new SOTA forcross-architecture and cross-domain black-box transferability.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the academic paper "VLA-Hijack: A Transferable Patch Attack against Vision-Language-Action Models via Visual Proprioception Hijacking". I need to organize the summary according to the 8 specified points, using Markdown formatting with hierarchical headings and bullet points. Let me carefully analyze the paper content and structure my response.

Let me go through each section:

1. **Core problem and overall meaning**: The paper addresses the vulnerability of VLA models to adversarial patch attacks, particularly the poor cross-architecture transferability of existing attacks that overfit to specific action output spaces.

2. **Methodology**: VLA-Hijack framework with two main components:
   - Attention-Guided Proprioceptive Suppression (Phase I)
   - Multimodal Proprioceptive Injection (Phase II) with alternating schedule between semantic concept anchoring and visual prototype projection

3. **Experimental design**: 
   - Datasets: LIBERO (Spatial, Object, Goal, Long suites), BridgeData V2
   - Victim models: OpenVLA, UniVLA, CronusVLA (12 variants total)
   - Baselines: UADA, UPA, TMA (varying DoFs), Random Noise, Arm Image
   - Physical world experiments on OpenVLA and π0

4. **Resources/compute**: The paper doesn't explicitly mention GPU types or training duration in the extracted text.

5. **Experiment quantity and sufficiency**: 
   - Main results across 12 victim models
   - Cross-domain Real-to-Sim evaluation
   - Surrogate architecture robustness tests (4 UniVLA variants)
   - Ablation studies on components, optimization strategy
   - Physical world evaluation
   - Pretty comprehensive

6. **Main conclusions**: SOTA transferability, 63.68% average failure rate, 42.66%-45.41% improvement over baselines

7. **Strengths**: Novel insight into visual proprioception loop, multimodal approach, alternating optimization, comprehensive evaluation across architectures and domains

8. **Limitations**: The paper doesn't extensively discuss limitations. Some potential ones: single surrogate model assumption, universal untargeted attack scope, patch placement constraints, etc.

Let me write this up in Chinese with proper Markdown formatting.</think>

# VLA-Hijack 论文总结

## 1. 核心问题与研究背景

- **研究对象**：视觉-语言-动作（Vision-Language-Action, VLA）模型作为新兴的通用机器人策略（如 OpenVLA、UniVLA、CronusVLA、π0 等），通过将大模型的视觉-语言推理能力迁移到物理控制中，已广泛应用于医疗辅助、家庭服务等安全关键领域。
- **核心问题**：VLA 模型对对抗补丁（adversarial patch）攻击具有严重脆弱性，阻碍其在安全敏感场景的实际部署。
- **现有方法的瓶颈**：现有针对 VLA 的补丁攻击（如 UADA、UPA、TMA）大多仅在白盒设定下有效，且普遍通过最大化动作偏差来优化扰动。这种策略严重过拟合于源模型的特定"动作头"（Action Head）和动作空间分布，导致**跨架构（cross-architecture）、跨域（cross-domain）的迁移能力极差**。
- **关键观察**：作者发现，即使仅以"动作误差"为优化目标，生成的对抗补丁也会自发地呈现出类似机械臂关节的视觉模式，由此推断 VLA 决策存在一个**根本性依赖——视觉本体感知回路（Visual Proprioception Loop）**：模型必须先从观测图像中视觉定位自身的机械臂，再定位目标物体，最后规划相对运动。

## 2. 方法论

### 2.1 核心思想——"本体感知身份重写"（Proprioceptive Identity Rewiring）

- 与现有方法攻击"动作输出空间"不同，VLA-Hijack 攻击的是 VLA 模型共享的**视觉自我定位过程**。
- 通过同步执行两个互补目标实现身份替换：
  1. **抑制原始机械臂特征**（"感知真空"）
  2. **将对抗补丁注入为"幻象具身"（phantom embodiment）**——使模型将补丁误识别为真正的机械臂。

### 2.2 威胁模型与优化目标

- **攻击类型**：通用（universal）无目标（untargeted）补丁攻击，一个补丁对多任务、多场景有效。
- **形式化**：给定观测图像 $I$、指令 $T$ 与 VLA 模型 $f_\theta$，生成补丁 $P$，优化如下目标：
$$\min_{P} \mathbb{E}_{(I,T)\sim\mathcal{D}}\left[\mathcal{L}_{total}(f_\theta(I_{adv}, T))\right] \quad \text{s.t.} \quad P \in [0,1]^{H\times W}$$
- **迁移攻击设置**：仅对一个替代模型（surrogate）白盒优化补丁，再在未知架构的黑盒受害者模型上测试。

### 2.3 阶段一：注意力引导的本体感知抑制（Phase I）

- **显著性引导加权**：提取视觉编码器最后一层的多头自注意力图，聚合得到原始显著性图 $S$，归一化后转换为权重图 $W$：
$$W = \mathbf{1} + \alpha \cdot \frac{S - S_{min}}{S_{max} - S_{min} + \epsilon}$$
- **加权特征抑制**：在原始机械臂特征响应强烈的区域，强制对抗特征 $Z_{adv}$ 与清洁特征 $Z_{clean}$ 余弦相似度最小化，制造"感知真空"。

### 2.4 阶段二：多模态本体感知注入（Phase II）

- **语义概念锚定（Semantic Concept Anchoring）**：
  - 定义语义锚点文本集 $T_{sem}$（如 {"robot", "arm", "hand", "claw", "end-effector"}），通过文本编码器获得嵌入 $E_{sem}$。
  - 采用 Top-K 聚合策略，使对抗补丁特征与最相关的 K 个语义锚点保持高余弦相似度，避免机械臂特征的多义性问题（如"claw"与"arm"的纹理差异）。
- **视觉原型投影（Visual Prototype Projection）**：
  - 利用 SAM 3 分割得到机械臂掩码 $M_{arm}$，从清洁特征中全局平均池化得到视觉原型 $v_{proto}$。
  - 将补丁特征与原型对齐，克隆真实机械臂的纹理、结构细节。
- **交替注入调度（Alternating Schedule）**：
  - 同时优化语义与视觉目标会产生梯度冲突，因此定义：
$$\mathcal{L}_{inject}^{(t)} = \begin{cases} \mathcal{L}_{sem}(Z_{adv}, E_{sem}), & \text{if } \lfloor t/\tau \rfloor \text{ is even} \\ \mathcal{L}_{vis}(Z_{adv}, v_{proto}), & \text{if } \lfloor t/\tau \rfloor \text{ is odd} \end{cases}$$
  - 通过周期 $\tau$ 交替优化两种模态损失（实验中 $\tau=5$ 最优）。

### 2.5 总体目标函数

$$\min_P \mathcal{L}_{total} = \mathcal{L}_{suppress} + \lambda \cdot \mathcal{L}_{inject}^{(t)}$$
- 抑制项 $\mathcal{L}_{suppress}$ 始终开启；注入项 $\lambda \cdot \mathcal{L}_{inject}^{(t)}$ 按调度切换；$\lambda=0.2$ 时性能最优。

## 3. 实验设计

### 3.1 数据集与场景
- **仿真域**：包含 LIBERO 的四个任务套件——Spatial、Object、Goal、Long，每个套件含 10 个操作任务，用于评估高层推理与多步序列决策。
- **真实域**：BridgeData V2 数据集，包含 60,096 条轨迹、24 种环境、13 项基础操作技能，用于评估非结构化物理场景。
- **真实世界评估**：自采真实数据集，覆盖两类任务（T1：把纸放进抽屉；T2：垃圾分类）。

### 3.2 受害者 VLA 模型（共 12 个）
- **OpenVLA**（离散动作 Token 化）× 4 个任务变体
- **UniVLA**（统一潜在动作表示）× 4 个任务变体
- **CronusVLA**（多帧连续动作）× 4 个任务变体
- **额外真实世界测试**：π0（基于流匹配的多视角架构）

### 3.3 替代模型与基准方法
- **替代模型**：以 OpenVLA-Spatial（白盒基准）和 UniVLA 各任务变体（跨架构验证）作为替代。
- **对比基线**（共 8 类攻击目标）：
  - **UADA**（1-DoF、1-3-DoF 动作）
  - **UPA**（1-DoF、1-3-DoF 动作）
  - **TMA**（1、7、1-3、1-7 DoF 动作）
  - **Random Noise**：随机噪声基准
  - **Arm Image**：直接将真实机械臂图像作为补丁（朴素视觉先验）
- **评价指标**：Failure Rate (FR) = 1 − Success Rate (SR)，每任务 50 次 rollout（主实验），每任务 10 次 rollout（消融实验）。

### 3.4 攻击配置
- 补丁大小：图像面积的 5%
- 机械臂掩码工具：SAM 3
- 优化参数：batch size = 4，总步数 $N=500$，每步内层 $K=50$ 次，$\alpha=2$

## 4. 资源与算力

- **论文未明确披露**所使用 GPU 型号、数量、训练时长等具体算力信息。
- 仅可推断：实验涉及多个大规模 VLA 模型（如 OpenVLA-7B、UniVLA、CronusVLA），并包含真实世界机器人实验，表明研究需投入较多算力与机器人硬件资源；但具体资源消耗未在文中说明。

## 5. 实验数量与充分性

### 5.1 实验规模
- **主实验（仿真域）**：12 个受害者模型 × 多任务套件 × 多基线对比。
- **跨域实验（Real-to-Sim）**：在 BridgeData V2 上训练补丁，在 LIBERO 12 个模型上测试。
- **替代架构鲁棒性**：分别以 4 个 UniVLA 变体作为替代进行实验。
- **消融实验**：
  - 攻击步数与收敛效率（4 个图）
  - 各损失项贡献（语义注入、视觉注入、抑制项，5 个图）
  - 注入权重 $\lambda$ 敏感性（5 组）
  - 交替周期 $\tau$ 敏感性（5 组）
- **物理世界实验**：两个任务 × 两个模型（OpenVLA、π0）× 20 次试验。

### 5.2 充分性与公平性评价
- 实验在 **架构异质性**（离散 Token / 潜在表示 / 连续动作）和 **域差异**（仿真 / 真实）两个维度上覆盖较广。
- 每个任务使用 50 次 rollout（总计每套件 500 次），统计可靠性较强。
- 同时报告白盒与黑盒迁移结果，对比 8 类基线，公平性较好。
- 唯一不足：物理世界实验任务数量较少（仅 2 个任务），可能未完全覆盖实际部署的多样性。

## 6. 主要结论与发现

- **白盒性能**：在替代模型 OpenVLA-Spatial 上达到 100% 失败率，且仅需 30 步即可收敛（优于需更长步数的基线）。
- **跨架构迁移（仿真域）**：Transfer Avg. 达 61.64%，显著优于最强基线 UADA₁₋₃ 的 37.53%，绝对提升超过 24 个百分点（论文摘要提及整体提升幅度为 42.66%–45.41%，对应 Real-to-Sim 设定）。
- **跨域迁移（Real-to-Sim）**：Transfer Avg. 达 63.68%，约为现有 SOTA 基线（18%–21%）的 3 倍；甚至远超朴素"Arm Image"基准（23.45%）。
- **核心发现**：VLA 模型的视觉自我定位回路是其决策的"阿喀琉斯之踵"，针对此机制的补丁攻击在跨架构、跨域设定下具有强普适性。
- **物理世界验证**：在 OpenVLA 和 π0 上分别达到 100% 和 92.5% 的平均失败率，证明真实威胁性。
- **补丁可视化**：所有训练得到的补丁均呈现机械臂结构（关节、金属纹理、夹爪），可视化为"幻象具身"假设提供了直观证据。

## 7. 优点与亮点

- **洞察新颖**：揭示了 VLA 模型的"视觉本体感知回路"这一根本性脆弱性，将对抗攻击视角从动作空间转向共享的感知空间，从根源上解决了迁移性瓶颈。
- **机制设计精巧**：
  - "抑制 + 注入"双向操作的"感知真空-幻象具身"框架具有清晰的直觉解释力；
  - 引入注意力显著性图作为加权抑制先验，避免对背景无关 Token 的无效优化；
  - 多模态注入（语义锚点 + 视觉原型）+ 交替调度有效缓解梯度冲突。
- **评估全面**：覆盖 12 个异构 VLA 模型、仿真+真实双域、白盒+黑盒+物理实验，并对比 8 类基线，是目前 VLA 对抗攻击领域较为系统的评估。
- **可视化充分**：注意力图、补丁结构、3D 轨迹可视化帮助理解攻击机理。

## 8. 不足与局限

- **物理世界实验规模有限**：仅 2 个任务（T1、T2）和 2 个模型（OpenVLA、π0），每任务 20 次试验，难以充分反映真实场景的多样性。
- **算力披露缺失**：未报告所用 GPU 型号/数量与训练时长，限制可复现性评估。
- **补丁先验依赖**：方法依赖 SAM 3 精确分割机械臂掩码以提取视觉原型；若分割失败，可能影响攻击效果，泛化至其他机器人形态（不同机械臂外观）的鲁棒性未详细讨论。
- **白盒替代假设过强**：要求攻击者能完全访问替代模型的参数与梯度；实际部署中，若目标模型封闭且无开源替代模型可用，迁移性可能下降。
- **补丁尺寸与位置固定**：实验固定使用 5% 图像面积的补丁，未讨论不同尺寸/位置对成功率的影响。
- **未深入分析防御**：论文聚焦攻击端，未提出针对性防御方法或评估对抗训练、输入预处理等防御手段下的攻击衰减情况。
- **基准对比范围**：尽管对比了 8 类攻击目标，但基本集中在"动作空间扰动"路线；未与针对 VLM 的多模态对抗攻击（如协作式多模态攻击、扩散净化攻击等）直接比较。
- **解释性尚浅**：虽然通过注意力可视化佐证"视觉本体感知回路"，但缺乏更严格的因果分析（如注意力消融、控制变量实验定量证明该机制的存在）。

（完）
