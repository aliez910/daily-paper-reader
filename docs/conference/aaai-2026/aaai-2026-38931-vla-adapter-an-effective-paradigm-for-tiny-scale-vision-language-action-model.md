---
title: "VLA-Adapter: An Effective Paradigm for Tiny-Scale Vision-Language-Action Model"
title_zh: VLA-Adapter：小规模视觉-语言-动作模型的有效范式
authors: "Yihao Wang, Pengxiang Ding, Lingxiao Li, Can Cui, Zirui Ge, Xinyang Tong, Wenxuan Song, Han Zhao, Wei Zhao, Pengxu Hou, Siteng Huang, Yifan Tang, Wenhui Wang, Ru Zhang, Jianyi Liu, Donglin Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38931/42893"
tags: ["query:rob-il"]
score: 8.0
evidence: 用于高效视觉-语言-动作模型的轻量适配器
tldr: 现有VLA模型依赖大规模VLM预训练，训练成本高昂。VLA-Adapter通过分析视觉-语言条件的作用，提出轻量级Pol模块高效桥接到动作空间，在仅百万级参数下达到与大规模模型可比的性能，大幅降低了训练开销。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 843, \"height\": 507, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1774, \"height\": 684, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 315, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1789, \"height\": 639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 856, \"height\": 600, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 842, \"height\": 331, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38931/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 863, \"height\": 336, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 172, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 861, \"height\": 206, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 136, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1582, \"height\": 721, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1588, \"height\": 590, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38931/table-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 865, \"height\": 250, \"label\": \"Table\"}]"
motivation: VLA模型训练成本高，依赖大规模VLM。
method: 系统性分析视觉-语言条件的作用，设计轻量级Pol桥接模块。
result: 在多个操作基准上，VLA-Adapter以小规模参数达到和大模型相当的性能。
conclusion: 轻量级桥接范式可以大幅降低VLA模型的训练成本而不牺牲性能。
---

## Abstract
Vision-Language-Action (VLA) models typically bridge the gap between perceptual and action spaces by pre-training a large-scale Vision-Language Model (VLM) on robotic data. While this approach greatly enhances performance, it also incurs significant training costs. In this paper, we investigate how to effectively bridge vision-language (VL) representations to action (A). We introduce VLA-Adapter, a novel paradigm designed to reduce the reliance of VLA models on large-scale VLMs and extensive pre-training. To this end, we first systematically analyze the effectiveness of various VL conditions and present key findings on which conditions are essential for bridging perception and action spaces. Based on these insights, we propose a lightweight Policy module with Bridge Attention, which autonomously injects the optimal condition into the action space. In this way, our method achieves high performance using only a 0.5B-parameter backbone, without any robotic data pre-training. Extensive experiments on both simulated and real-world robotic benchmarks show that VLA-Adapter not only achieves state-of-the-art level performance, but also offers the fast inference speed reported to date. Furthermore, thanks to the proposed advanced bridging paradigm, VLA-Adapter enables the training of a powerful VLA model on a single consumer-grade GPU, greatly lowering the barrier to deploying VLA model.

---

## 论文详细总结（自动生成）

# VLA-Adapter 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：如何更有效地将视觉-语言（VL）表示桥接到动作（A）空间，同时降低对大规模视觉-语言模型（VLM）和昂贵机器人数据预训练的依赖。
- **背景**：现有VLA模型通常先在大规模机器人数据集（如Open X-Embodiment）上预训练大尺寸VLM（如7B），然后再接策略网络解码动作。这带来了巨大的训练成本、高GPU内存消耗、低推理吞吐量，且门槛高。
- **研究目标**：探索何种VL条件对动作生成最关键，并基于此设计轻量级桥梁模块，使得仅用小尺寸骨干（0.5B）且无需机器人预训练即可达到与大规模模型相当的性能，从而降低VLA部署壁垒。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：通过对不同VL特征条件（原始特征 vs ActionQuery特征，单层 vs 多层）的系统分析，确定最优的桥接方式；然后设计轻量策略网络（Policy）配合**桥接注意力（Bridge Attention）**，自动将最优条件注入动作空间。
- **关键技术细节**：
  - **条件分析**：在Prismatic-VLM上，用四种条件模式（单层/全层原始特征、单层/全层ActionQuery特征）进行实验，得到三条关键发现：
    1. 原始特征的中层性能优于深层，深层偏语义，不利于动作生成；
    2. ActionQuery特征的深层性能更好，因其从头训练，聚合了更多多模态细节；
    3. 多层特征优于单层，且省去层选择时间。
  - **Policy模块**（以L1变体为主）：
    - 输入：原始特征 \(C^R_t\)、ActionQuery特征 \(C^{AQ}_t\)、零初始化的动作块 \(A^0_t\)、本体感觉 \(P_t\)。
    - 每层包含一个**Bridge Attention**（两个交叉注意力分别处理两种条件，再加一个自注意力）和前馈网络（FFN）。
    - 交叉注意力中，\(C^R_t\) 经MLP作K,V；\(C^{AQ}_t\) 与本体嵌入拼接后经MLP作K,V；动作潜变量作Q。
    - 引入可学习参数 \(g\)（初始化为0，通过tanh限制在[-1,1]）控制原始特征注入程度，实现自适应性。
  - **训练目标**：L1损失，端到端训练，Policy从头训练，VLM可微调也可冻结。
  - **框架整体**：输入图像（第三视角+腕部）、指令、ActionQuery，经VLM提取条件特征，送入Policy逐层解码输出H步动作块。

## 3. 实验设计：数据集、基准与对比方法

- **模拟基准**：
  - **LIBERO**（Spatial, Object, Goal, Long四套），主要指标为成功率（每子任务50次重复）。
  - **CALVIN ABC→D**（零样本泛化），指标为连续完成任务数（最多5个）和平均长度。
- **真实世界**：自搭建6-DOF机械臂系统，含四大类任务（简单抓取、横向移动、堆叠、长时序列），随机化物体位置，每任务重复10次取平均。
- **对比方法**：
  - 大型：UnifiedVLA、OpenVLA、OpenVLA-OFT、UniVLA、CoT-VLA、WorldVLA（7B-8.5B）。
  - 小型：SpatialVLA、π0、π0-FAST、SmolVLA、GR00T N1（2B-4B）。
  - 极小：Seer、VLA-OS、Diffusion Policy（0.5B或非VLM方法）。
  - 真实世界：ACT + OFT。
- **消融实验**：在LIBERO-Long上考察ActionQuery数量（1~512）、条件类型（四种范式各代表一种组合）、注入程度（固定/可学习）。

## 4. 资源与算力

- **硬件**：所有模拟实验在配备4块NVIDIA H100 GPU的服务器上运行。未报告每个实验的具体训练时长。
- **内存与效率**：
  - 0.5B骨干 + Policy（97M参数）时，训练显存仅24.7 GB（batch size 8），远低于7B模型（62 GB）。
  - 推理吞吐量：219.2 Hz（8维动作块），是OpenVLA-OFT（71.4 Hz）的3倍。
- **可部署性**：由于较低显存需求，作者声称可在单张消费级GPU（如RTX 4090 24GB）上完成训练。

## 5. 实验数量与充分性

- **实验数量**：包含大量对比和消融：
  - 骨干尺度分析（表2、表3，不同骨干和冻结设置）。
  - LIBERO整体对比（表5，10余个方法，4套子任务）。
  - CALVIN泛化对比（表6，10余个方法）。
  - 真实世界实验（图7，4类任务）。
  - 三组消融实验（ActionQuery数量、条件类型、注入程度，图8、表7、表8）。
- **充分性**：
  - 模拟实验均采用50次重复，统计可靠。
  - 对比方法结果来自原论文或公开复现，保证了客观性（但部分大模型结果可能来自不同环境，存在一定偏差风险）。
  - 消融仅在LIBERO-Long上进行，代表性有限，但覆盖了关键设计要素。
  - 未在更多样场景（如灵巧手、移动操作）上验证。

## 6. 论文的主要结论与发现

- **桥接条件的关键发现**：
  1. 中层原始特征优于深层；深层ActionQuery特征优于其他层。
  2. 多层特征优于单层。
  3. ActionQuery作为接口整体优于直接使用原始特征。
- **VLA-Adapter性能**：
  - 在LIBERO平均成功率97.3%（0.5B骨干），与7B的OpenVLA-OFT（97.1%）相当，显著优于其他小模型。
  - 在CALVIN ABC→D平均完成任务长度4.42，优于所有比较方法。
  - 真实世界任务平均成功率显著高于ACT+OFT基线。
- **效率优势**：推理速度提升3倍，训练显存减少约3/5，且无需机器人数据预训练。
- **泛化性**：即使冻结骨干（不微调VLM），仍达到86.4%成功率，超过SmolVLA 9.4%。

## 7. 优点：方法与实验设计的亮点

- **方法创新**：
  - 首次系统分析VL桥接范式对动作生成的影响，提供可操作的设计指南。
  - 提出Bridge Attention模块，自适应融合两种条件，注入程度可学习，提高鲁棒性。
  - 采用轻量Policy（仅97M）配合极小骨干（0.5B），避免对大规模VLM和机器人预训练的依赖。
- **实验设计**：
  - 跨多个尺度骨干（0.5B, 7B）进行比较，验证方法普遍性。
  - 同时包含模拟和真实任务，评估泛化能力。
  - 消融实验针对关键超参数（ActionQuery数量、条件类型、注入程度）逐一分析，结论新颖。
- **实用价值**：大幅降低VLA训练的计算门槛，使消费级GPU训练成为可能。

## 8. 不足与局限

- **消融范围局限**：所有消融实验仅在LIBERO-Long上进行，其他数据集未做同等分析，可能影响结论泛化性。
- **对比公平性**：部分基线结果来自原论文，实验环境、重复次数、采样策略可能与本文不完全一致，尤其大型模型（如UnifiedVLA）的结果可能难以在小设备上验证。
- **真实任务规模较小**：真实世界实验仅使用特定六轴机械臂、有限物体和场景，任务种类和复杂度有限，未涉及移动操作或灵巧手等更复杂场景。
- **未包含最新小模型**：未与同期某些极简模型（如Pi0.5、MoDE增强版本等）进行全面比较，时间差可能导致对比不完整。
- **骨干基础**：虽然宣称无需机器人预训练，但基座VLM（Prismatic）已在通用图像-文本数据上预训练，并非完全“从零开始”。
- **Policy设计**：仅尝试L1和DiT两种Policy，未探索更多架构（如扩散Policy变体），可能错过更优方案。

（完）
