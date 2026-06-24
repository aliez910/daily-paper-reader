---
title: "MoLe-VLA: Dynamic Layer-skipping Vision Language Action Model via Mixture-of-Layers for Efficient Robot Manipulation"
title_zh: MoLe-VLA：通过层混合实现的动态跳层视觉-语言-动作模型用于高效机器人操作
authors: "Rongyu Zhang, Menghang Dong, Yuan Zhang, Liang Heng, Xiaowei Chi, Gaole Dai, Li Du, Dan Wang, Yuan Du, Shanghang Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38945/42907"
tags: ["query:rob-il"]
score: 9.0
evidence: 用于高效操作的动态跳层VLA模型
tldr: 现有VLA模型因密集LLM计算庞大难以部署，而早期退出方法忽视最终层语义角色。受浅脑假说启发，本文提出MoLe-VLA，将每层视为专家，通过时空感知路由器动态激活子集，实现高效推理。实验证明在保持任务性能的同时大幅降低计算成本，为VLA模型的实际部署提供了有效方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38945/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1759, \"height\": 690, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38945/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1826, \"height\": 702, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38945/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1642, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38945/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1558, \"height\": 658, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38945/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1839, \"height\": 870, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38945/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 878, \"height\": 353, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38945/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38945/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 878, \"height\": 273, \"label\": \"Table\"}]"
motivation: 解决VLA模型计算量大、部署困难的问题。
method: 提出MoLe-VLA架构，通过层混合和时空路由动态激活LLM层。
result: 在保持性能的同时显著降低计算成本。
conclusion: 提出了一种动态跳层的VLA模型实现高效操作。
---

## Abstract
Vision-Language-Action (VLA) models enable robotic systems to perform embodied tasks but face deployment challenges due to the high computational demands of the dense Large Language Models (LLMs), with existing early-exit-based sparsification methods often overlooking the critical semantic role of final layers in downstream tasks. Aligning with the recent breakthrough of the Shallow Brain Hypothesis (SBH) in neuroscience and the mixture of experts in model sparsification, we conceptualize each LLM layer as an expert and propose a Mixture-of-LayEr Vision Language Action model (MoLe-VLA or simply MoLe) architecture for dynamic LLM layer activation. Specifically, we introduce a Spatial-Temporal Aware Router (STAR) for MoLe to selectively activate only parts of the layers based on the robot’s current state, mimicking the brain's distinct signal pathways specialized for cognition and causal reasoning. Additionally, to compensate for the cognition ability of LLM lost during the layer-skipping, we devise a Cognitive self-Knowledge Distillation (CogKD) to enhance the understanding of task demands and generate task-relevant action sequences by leveraging cognition features. Extensive experiments in RLBench simulations and real-world environments demonstrate the superiority of MoLe-VLA in both efficiency and performance, improving the mean success rate by 9.7% across ten simulation tasks while accelerating inference by 36.8% over OpenVLA.

---

## 论文详细总结（自动生成）

以下是根据论文内容生成的结构化中文总结。

---

## 1. 核心问题与整体含义（研究动机和背景）

- **问题**：视觉‑语言‑动作（VLA）模型在机器人操作任务中展现出强大能力，但其底层的大语言模型（LLM）计算量极大，导致推理速度远低于实际机械臂所需的控制频率（如 Franka 机械臂需 50–1000 Hz，而 7B VLA 在 RTX 4090 上仅 5–10 Hz）。这使得 VLA 模型在商业级 GPU 上的部署困难重重。
- **现有方法不足**：已有的基于早期退出（early‑exit）的精简方法往往忽略最后层在语义理解中的关键作用，导致性能损失。
- **启发来源**：神经科学的**浅脑假说（Shallow Brain Hypothesis, SBH）** 指出，生物大脑通过深度分层与并行皮层‑皮层下回路（shortcut）的平衡实现高效推理，而非单纯依赖逐层传递。同时，混合专家（MoE）的思路在模型稀疏化中取得进展。
- **核心目标**：提出一种动态的层激活机制，在减少计算开销的同时保持甚至提升任务性能，使得 VLA 模型能在资源受限的机器人平台上高效运行。

## 2. 方法论：核心思想、关键技术细节

### 整体架构：MoLe-VLA
- 将 **LLM 的每一层视为一个“专家”**，通过一个轻量级路由器自适应地选择激活哪些层，从而实现垂直的层稀疏化。
- 与 Mixture‑of‑Depth (MoD) 不同，MoLe 对整体输入特征进行统一选择，避免了 token 级别的感知不一致。

### 关键技术 1：Spatial‑Temporal Aware Router (STAR)
- **功能**：根据机器人当前状态（视觉和语言指令）动态为每一层生成激活权重，只让 **top‑k** 层参与计算。
- **设计**：分别处理视觉特征（空间路由权重 S）和语言指令（时序路由权重 T），通过可学习的锐度控制器 α 自适应融合，得到最终的选通向量 G。
- **优势**：仅增加 **<0.1%** 的额外参数，计算复杂度为 O(Ne·(d² + N_text²))，远低于传统 MoE 的 O(Ne·d)。

### 关键技术 2：Cognitive self‑Knowledge Distillation (CogKD)
- **动机**：跳层会造成模型认知表达能力下降，需通过蒸馏恢复。
- **方法**：以原始全层模型为教师、MoLe 稀疏模型为学生，进行自蒸馏。
- **创新点**：利用 LLM 输出的**认知令牌（cognition token）** 识别与任务最相关的“兴趣令牌（ToIs）”，仅对这些令牌施加 Mimic 损失和 Reverse‑KL 损失，避免对所有 tokens 做无差别对齐，从而降低计算开销并提升关键语义传递。
- **损失函数**：L_cog = (1‑λ₁)L_cog‑mimic + λ₁L_cog‑reversekl，λ₁=0.5。

### 整体目标
L_MoLe = L_task + λ₂L_cog + λ₃L_lb，其中 L_task 是任务损失（如扩散头噪声预测 MSE），λ₂=0.5，λ₃=0.1。

## 3. 实验设计

### 模拟环境：RLBench
- **场景**：10 种桌面操作任务，包括 Close box、Close laptop lid、Toilet seat down、Put rubbish in bin、Sweep to dustpan、Close fridge、Phone on base、Take umbrella out of stand、Frame off hanger、Change clock。
- **数据**：每个任务 100 条训练轨迹，评估 25 次/任务。
- **评价指标**：成功率（Mean Acc.%）、推理速度（Hz）。

### 真实世界部署
- **机器人**：Franka Research 3，配备 UMI 夹爪、GoPro 9 腕部摄像头。
- **任务**：Detach charger、Pull drawer、Pour water。
- **数据**：共 50 条演示，每任务评估 10 次。

### 基线方法对比
- **VLA 模型**：OpenVLA（自回归）、π0（扩散）、CogAct（扩散）。
- **效率基线（基于 CogAct 骨干）**：DeeR（早期退出）、MoD（动态令牌分配）、Random‑skip（随机跳层）；另与 RoboMamba 对比效率。
- **变体**：MoLe‑OpenVLA、MoLe‑π0、MoLe‑CogAct。

## 4. 资源与算力

- **训练**：8 块 NVIDIA A800 GPU，使用 FSDP 框架，以 2×10⁻⁵ 学习率端到端微调 **1,000 迭代**，耗时约 **1.5 小时**。
- **推理评估**：在单块 **GeForce RTX 4090D** 上测量频率。
- 文中未明确说明批量大小及完整训练的总参数量，但路由器增加参数 <0.1%。

## 5. 实验数量与充分性

- **模拟实验**：10 个任务 × 每个任务 25 次评估，重复 4 次（论文注明“four repetitions”），结果给出均值与方差。
- **真实实验**：3 个任务 × 10 次评估，给出成功率。
- **消融实验**：3 组（表 3），分别验证 STAR 路由器、CogKD 不同损失组合的有效性，对比了线性路由器、纯 STAR、不同损失函数组合等。
- **效率分析**：测试不同跳层比例（图 3）、量化后性能（表 2，FP16 vs INT8）、FLOPs 与推理时间对比。
- **公平性**：所有基线使用相同任务配置，预训练权重加载后按各自设定训练；MoLe 与基线的骨干、动作头保持一致，仅在 LLM 层跳层策略上不同。随机跳层作为无智能对比，证实了路由器的必要性。

**评估充分性**：覆盖面较全面——多种 VLA 骨干、多种效率基线、模拟+真实、跳层比例分析、量化分析、消融。统计上使用了多次重复和方差，可信度较高。但真实任务数量（3 个）较少，可能会限制泛化结论。

## 6. 主要结论与发现

1. **性能提升**：MoLe‑OpenVLA 在 RLBench 平均成功率提升 **9.7%**（46.7% → 56.4%），推理加速 **36.8%**（6.8 Hz → 9.3 Hz）。
2. **跨骨干有效性**：MoLe‑π0 提升成功率 5.4%，加速至 18.4 Hz；MoLe‑CogAct 达到 60.2% 平均成功率，超越所有效率基线。
3. **比早期退出更优**：MoLe 比 DeeR 和 MoD 获得更高成功率且更低方差，证明跳层优于固定退出点。
4. **量化友好**：INT8 量化后保持 58.8% 成功率，推理速度达 15.7 Hz，显存降低 45%。
5. **路由器关键**：随机跳层比 MoLe 快但成功率低 9.0%；STAR 相比线性路由器提升 3.0% 成功率。
6. **蒸馏有效**：同时使用 MSE 和 Reverse‑KL 的 CogKD 达到最优（56.4%），优于单独使用任一损失。

## 7. 优点

- **理论新颖**：结合神经科学的浅脑假说，将层选择类比于脑内回路，提出垂直 MoE 视角，思路具有跨学科启发性。
- **工程实用**：额外参数极少（<0.1%），即插即用于多种 VLA 骨干（OpenVLA、π0、CogAct），可直接降低推理成本。
- **设计巧妙**：STAR 同时利用空间和时序信息，且通过单一的融合步骤高效计算；CogKD 利用认知令牌自动聚焦关键 token，避免全 token 蒸馏开销。
- **实验完整**：包含模拟、真实、多种骨干、多种效率基线、跳层比例分析、量化分析、消融验证，统计扎实，对比公平。

## 8. 不足与局限

- **任务多样性**：真实世界仅 3 个任务，且均为简单交互（推、倒水等），对长时序、高精度或重物的任务未验证。
- **硬件依赖**：效率数据仅在 RTX 4090D 上评估，未在更低端 GPU 或嵌入式设备（如 Jetson）上测试，实际边缘部署能力不明。
- **假设对齐**：SBH 的引入是类比性说明，未提供神经科学层面的定量验证或生物学合理性证明。
- **泛化风险**：路由器基于视觉和语言特征，可能在训练分布外的场景（如从未见过的物体或光照剧烈变化）中做出次优层选择。
- **跳层比例固定**：默认 50% 跳层，未讨论自适应根据任务复杂度动态调节跳层数的方案（尽管路由器输出是动态的，但 top‑k 的 k 是预设超参数）。
- **蒸馏目标局限**：蒸馏依赖原教师模型，若教师本身存在偏差（如对某些物体成功率低），学生可能继承该偏差。
- **计算公平性**：MoLe 的加速主要来自 LLM 层减少，但文中未详细对比加上路由器和蒸馏训练的额外开销对总训练时间的实际影响。

（完）
