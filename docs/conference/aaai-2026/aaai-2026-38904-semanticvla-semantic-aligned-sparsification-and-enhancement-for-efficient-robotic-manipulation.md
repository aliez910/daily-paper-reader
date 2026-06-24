---
title: "SemanticVLA: Semantic-Aligned Sparsification and Enhancement for Efficient Robotic Manipulation"
title_zh: SemanticVLA：面向高效机器人操作的语义对齐稀疏化与增强
authors: "Wei Li, Renshan Zhang, Rui Shao, Zhijian Fang, Kaiwen Zhou, Zhuotao Tian, Liqiang Nie"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38904/42866"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向操作的视觉-语言-动作模型的语义对齐稀疏化
tldr: 现有VLA模型存在感知冗余和指令-视觉对齐不足的问题。本文提出SemanticVLA框架，通过语义引导的双视觉剪枝器实现冗余感知的稀疏化，并增强语义对齐。实验表明在多个操作任务上效率显著提升，同时保持高精度，为VLA模型的实际部署提供了有利支持。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38904/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38904/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1647, \"height\": 1088, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38904/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1801, \"height\": 535, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38904/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1745, \"height\": 548, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38904/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1832, \"height\": 321, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1806, \"height\": 504, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 809, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 819, \"height\": 342, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1824, \"height\": 295, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38904/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 243, \"label\": \"Table\"}]"
motivation: 解决VLA模型在操作任务中的感知冗余和语义对齐不足。
method: 提出语义引导的双视觉剪枝器进行稀疏化和增强。
result: 在多个操作任务上实现高效且保持高精度。
conclusion: 提出了一种语义对齐的VLA稀疏化与增强框架，提升操作效率。
---

## Abstract
Vision-Language-Action (VLA) models have advanced in robotic manipulation, yet practical deployment remains hindered by two key limitations: **1) perceptual redundancy**, where irrelevant visual inputs are processed inefficiently, and **2) superficial instruction-vision alignment**, which hampers semantic grounding of actions.
In this paper, we propose **SemanticVLA**, a novel VLA framework that performs Semantic-Aligned Sparsification and Enhancement for Efficient Robotic Manipulation. Specifically:
**1)** To sparsify redundant perception while preserving semantic alignment, **Semantic-guided Dual Visual Pruner (SD-Pruner)** performs: Instruction-driven Pruner (ID-Pruner) extracts global action cues and local semantic anchors in SigLIP; Spatial-aggregation Pruner (SA-Pruner) compacts geometry-rich features into task-adaptive tokens in DINOv2.
**2)** To exploit sparsified features and integrate semantics with spatial geometry, **Semantic-complementary Hierarchical Fuser (SH-Fuser)** fuses dense patches and sparse tokens across SigLIP and DINOv2 for coherent representation.
**3)** To enhance the transformation from perception to action, **Semantic-conditioned Action Coupler (SA-Coupler)** replaces the conventional observation-to-DoF approach, yielding more efficient and interpretable behavior modeling for manipulation tasks.
Extensive experiments on simulation and real-world tasks show that SemanticVLA sets a new SOTA in both performance and efficiency. SemanticVLA surpasses OpenVLA on LIBERO benchmark by **21.1%** in success rate, while reducing training cost and inference latency by **3.0×** and **2.7×**.

---

## 论文详细总结（自动生成）

# 语义对齐稀疏化与增强的高效机器人操作框架 SemanticVLA 详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **研究对象**：视觉‑语言‑动作（Vision‑Language‑Action, VLA）模型在机器人操作任务中展现出端到端的能力，但在实际部署中仍面临两个关键瓶颈：
  - **感知冗余（Perceptual Redundancy）**：现有 VLA 框架采用与指令无关的通用视觉编码器（如 SigLIP、DINOv2），对所有像素等同处理，背景杂乱、任务无关干扰物被一同编码，导致计算冗余和关键线索被稀释。
  - **指令‑视觉语义对齐不足（Superficial Instruction‑Vision Alignment）**：大部分 VLA 模型仅通过大语言模型进行通用跨模态对齐，无法捕捉细粒度的语义关系（如动作动词与目标对象的关联），导致模型难以识别全局动作线索和局部语义锚点，影响语义接地（grounding）。
- **整体目标**：实现**语义对齐的稀疏化与增强**，在减少冗余计算的同时保持甚至提升任务性能，为 VLA 模型的高效部署提供新路径。

## 2. 方法论：核心思想与关键技术

### 2.1 核心思想
- 提出三个层次互补的语义：**指令级语义**（任务提示意图）、**视觉级语义**（物体与空间布局）、**控制级语义**（平移、旋转、夹爪状态）。
- 通过三个模块实现语义对齐的稀疏化和增强：
  1. **语义引导的双视觉剪枝器（SD‑Pruner）**：对 SigLIP 和 DINOv2 分别进行指令感知剪枝和空间聚合剪枝。
  2. **语义互补的分层融合器（SH‑Fuser）**：在密集层级和稀疏层级融合两个编码器的特征。
  3. **语义条件动作耦合器（SA‑Coupler）**：将感知映射到结构化的动作类型，提升解码效率与可解释性。

### 2.2 关键技术细节

#### (1) SD‑Pruner
- **ID‑Pruner（用于 SigLIP）**：
  - 构建指令令牌与视觉令牌的余弦相似度矩阵 S∈R^(N×M)。
  - **Vision‑to‑Language Mapping**：筛选与指令最相关的 k 个指令令牌，聚合对应视觉令牌作为全局动作线索特征。
  - **Language‑to‑Vision Filtering**：筛选与指令整体最相关的 h 个视觉令牌，形成局部语义锚点令牌。
  - 输出为两部分并集：V_VL ∪ V_LV，保留任务关键信息，过滤背景噪声。
- **SA‑Pruner（用于 DINOv2）**：
  - 在 DINOv2 的观测令牌后添加零初始化的聚合令牌（数量为 N/8）。
  - 通过 FiLM 层用指令表示对令牌进行调制（缩放 + 偏移），使空间特征根据任务上下文动态调整。
  - 聚合令牌最后输出紧凑的几何特征，补全 ID‑Pruner 的语义信息。

#### (2) SH‑Fuser
- **Dense‑Fuser**：在 SigLIP 和 DINOv2 的多个 Transformer 块之间（表层、中层、深层）插入融合模块，交换密集补丁特征，实现语义与几何的逐级增强：
  \( V_{Fusion}^b = \text{MLP}(\text{Concat}(V_{Sig}^b, V_{Din}^b)) \)
- **Sparse‑Fuser**：最终阶段，将 ID‑Pruner 的 V_LV 与 SA‑Pruner 的 V_Agg 拼接并投影，形成紧凑表示：
  \( Z_{Fusion} = \text{MLP}(\text{Concat}(V_{LV}, V_{Agg})) \)
- 整体效果：视觉令牌减少 8～16×，同时保持判别性。

#### (3) SA‑Coupler
- 替代传统的将 7‑DoF 动作离散化为 7 个独立令牌的做法。
- 将每个未来动作分解为三个令牌：平移（t）、旋转（r）、夹爪（g），每个令牌统一编码对应 DoF。
- 在解码阶段使用三个专用预测头分别回归连续运动参数：
  \( d_{i,u} = W_u h_i + b_u, \quad u \in \{\text{trans}, \text{rot}, \text{grip}\} \)
- 使得模型能够并行解码所有未来动作，提升效率与可解释性。

#### (4) 整体流程
- 输入：观察图像 V、本体状态 q、自然语言指令 ℓ。
- 路径：SigLIP + ID‑Pruner 和 DINOv2 + SA‑Pruner 分别提取语义/空间特征，经 SH‑Fuser 得到统一表示 Z。
- 构建 LLM 输入序列：`[Z, q, ℓ, 0_0, 0_1, ..., 0_{K-1}]`，其中 0_i 为 SA‑Coupler 初始化的动作占位令牌。
- 通过双向解码一次前向生成所有 K 个动作。

## 3. 实验设计

### 3.1 模拟环境
- **基准**：LIBERO 基准，包含四个任务套件：**Spatial**、**Object**、**Goal**、**Long**，每套 500 个人类遥操作演示。
- **评估指标**：任务成功率（SR）及在对比方法中的排名（RK）。
- **对比方法**：50+ SOTA 基线，包括 Octo、π₀、OpenVLA、OpenVLA‑OFT、PD‑VLA、STAR、CoT‑VLA、SpatialVLA 等。
- **效率比较**：在相同设置下与 OpenVLA、OpenVLA‑OFT、PD‑VLA 对比训练 FLOPs、训练时长、推理延迟、吞吐量。

### 3.2 真实世界环境
- **平台**：AgileX Cobot Magic 平台。
- **任务**：物体放置（Bear→Plate + Raccoon→Bowl）、抽屉操作（Open + Place + Close）、T 恤折叠（3 个子步骤），以及另外两个场景（共 45+105 个演示）。
- **评估**：子任务成功率和总体成功率。
- **对比方法**：VQ‑BeT、QueST、STAR、PD‑VLA、OpenVLA‑OFT。

## 4. 资源与算力

- **GPU 配置**：8× NVIDIA A800 (80GB) GPU。
- **训练成本**（见 Table 2）：
  - SemanticVLA‑Lite：3.6 小时
  - SemanticVLA：3.9 小时
- **推理延迟**：SemanticVLA 为 0.089 s（Latency），吞吐量 89.9 Hz。
- 对比：OpenVLA 训练需 11.7 h，推理延迟 0.240 s；OpenVLA‑OFT 延迟 0.134 s。SemanticVLA 训练加速约 3.0×，推理加速约 2.7×。
- **说明**：算力信息在文中明确给出，实验均在同一硬件条件下完成。

## 5. 实验数量与充分性

- **模拟实验**：
  - 主表（Table 1）：9 个方法在 4 个套件上的成功率与排名，充分展示性能。
  - 效率表（Table 2）：5 个方法的 FLOPs、训练时间、延迟、吞吐量及成功率对比。
  - 消融实验（Table 4）：SD‑Pruner 中 ID‑Pruner 与 SA‑Pruner 的交叉组合。
  - 稀疏率消融（Table 5）：4×/8×/16×/32× 压缩率对比，并与 FastV、SliME 比较。
  - 融合器与动作耦合器消融（Table 6）：HF‑Fuser 与 SA‑Coupler 的单独/组合贡献。
  - 定性分析：注意力图可视化（Fig．5）展示剪枝与融合效果。
- **真实世界实验**（Table 3）：4 个方法（含两个变体）在 3 个长时程任务子步骤上的成功率，总体 77.8%（比第二名 OpenVLA‑OFT 高 22.2%）。
- **充分性评价**：实验覆盖多个模拟套件与多种真实物理场景，消融全面（剪枝器、融合器、动作耦合器、稀疏率），对比基线丰富（超过 10 个），且进行了效率与性能的联合评价。实验设计客观、公平，在相同环境下与复现的基线对比（标记 †）。整体充分且具说服力。

## 6. 主要结论与发现

1. **性能领先**：SemanticVLA 在 LIBERO 上达到 **97.7%** 平均成功率，排名第一，超出第二名 OpenVLA‑OFT 0.6 个百分点；超越原始 OpenVLA 约 21.1%。
2. **效率大幅提升**：训练成本仅 3.9 h（相比 OpenVLA 的 11.7 h），推理延迟 0.089 s（相比 0.240 s），吞吐量 89.9 Hz（相比 4.2 Hz）。视觉令牌减少 8×，动作令牌从 7 个减至 3 个。
3. **真实世界泛化**：在复杂长时程任务（折叠 T‑shirt、抽屉操作等）上总体成功率 77.8%，明显优于最强基线 OpenVLA‑OFT（55.6%）。
4. **消融验证**：ID‑Pruner 与 SA‑Pruner 的组合最优；8× 稀疏率达到最佳权衡；HF‑Fuser 和 SA‑Coupler 均提供互补性提升，尤其对长时程任务。
5. **可解释性**：注意力图表明模型能同时关注全局动作线索与局部语义锚点，并有效利用空间几何信息。

## 7. 优点

- **方法创新**：
  - 首次在 VLA 框架中显式解耦指令级、视觉级、控制级语义，并针对不同编码器特性设计专用剪枝策略（ID‑Pruner 基于指令相似度，SA‑Pruner 基于聚合令牌 + FiLM）。
  - 分层融合器在多个层级整合语义与空间特征，而非简单后期拼接，利于早期信息互补。
  - 动作耦合器将 7‑DoF 分解为三个语义原子类型，减少令牌数并支持并行解码，提升效率且易于理解。
- **实验全面**：模拟 + 真实世界，多项消融，与多个高效 VLA 变体公平对比，并复现基线以保证公平性。
- **开源贡献**：提供代码（GitHub），便于复现与进一步研究。

## 8. 不足与局限

- **固定编码器依赖**：依赖 SigLIP 和 DINOv2 两个预训练模型，增加了模型内存和加载复杂度；若未来出现更强或更高效的编码器，框架可能需要适配。
- **真实世界任务范围有限**：仅测试单臂固定平台（AgileX Cobot Magic），未涉及移动操作、双臂协作或人形机器人；泛化到其他平台有待验证。
- **稀疏率选择依赖调参**：8× 最优通过经验选择，但不同环境可能需要不同稀疏比，缺乏自适应调整机制。
- **未讨论失败案例与鲁棒性**：虽然报道了成功率，但没有深入分析失败情况（如遮挡极端、指令歧义、动作精度不够等）及模型敏感性。
- **实时性验证不足**：推理延迟虽低，但未在真实机器人控制循环中测试实际响应时间（包括图像采集、前处理、通信延迟），可能影响超实时控制。
- **消融实验未覆盖全部组合**：例如未单独消融 Dense‑Fuser 与 Sparse‑Fuser 的内部设计，或 ID‑Pruner 内部两个映射路径的贡献拆分，留有部分未探索空间。

（完）
