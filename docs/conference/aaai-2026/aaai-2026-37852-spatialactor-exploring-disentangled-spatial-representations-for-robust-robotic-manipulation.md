---
title: "SpatialActor: Exploring Disentangled Spatial Representations for Robust Robotic Manipulation"
title_zh: SpatialActor：探索解耦空间表示以实现鲁棒机器人操纵
authors: "Hao Shi, Bin Xie, Yingfei Liu, Yang Yue, Tiancai Wang, Haoqiang Fan, Xiangyu Zhang, Gao Huang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37852/41814"
tags: ["query:rob-il"]
score: 9.0
evidence: 解耦空间表示用于操纵中的视觉到动作映射
tldr: 机器人操纵需要精确的空间理解，但现有方法往往混淆语义与几何信息，易受深度噪声影响。本文提出SpatialActor，一个解耦框架，显式分离语义与几何表示。通过语义引导的几何模块自适应调整多模态特征，该方法在保留丰富语义的同时增强了低层空间定位的鲁棒性。实验证明，SpatialActor在多个操纵基准上对深度噪声和场景变化具有更强的鲁棒性。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37852/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1830, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37852/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1824, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37852/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1812, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37852/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 806, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37852/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 869, \"height\": 463, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1844, \"height\": 900, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1574, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1845, \"height\": 579, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 316, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 878, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37852/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 867, \"height\": 417, \"label\": \"Table\"}]"
motivation: 现有方法将语义与几何信息混在一起，易受深度噪声影响，且忽略了精细空间线索。
method: 提出SpatialActor，通过解耦的语义引导几何模块显式分离语义和几何表示，并自适应融合多模态特征。
result: 在多个操纵任务上对深度噪声和场景变化表现出更强的鲁棒性，提升了任务成功率。
conclusion: 解耦语义与几何能够增强空间表示的鲁棒性，是提高操纵系统泛化能力的有效途径。
---

## Abstract
Robotic manipulation requires precise spatial understanding to interact with objects in the real world. Point-based methods suffer from sparse sampling, leading to the loss of fine-grained semantics. Image-based methods typically feed RGB and depth into 2D backbones pre-trained on 3D auxiliary tasks, but their entangled semantics and geometry are sensitive to inherent depth noise in real-world that disrupts semantic understanding. Moreover, these methods focus on high-level geometry while overlooking low-level spatial cues essential for precise interaction. We propose SpatialActor, a disentangled framework for robust robotic manipulation that explicitly decouples semantics and geometry. The Semantic-guided Geometric Module adaptively fuses two complementary geometry from noisy depth and semantic-guided expert priors. Also, a Spatial Transformer leverages low-level spatial cues for accurate 2D-3D mapping and enables interaction among spatial features. We evaluate SpatialActor on multiple simulation and real-world scenarios across  50+ tasks. It achieves state-of-the-art performance with 87.4% on RLBench and improves by 13.9% to 19.4% under varying noisy conditions, showing strong robustness. Moreover, it significantly enhances few-shot generalization to new tasks and maintains robustness under various spatial perturbations.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **背景**：机器人操纵任务需要精确的空间理解来与真实世界的物体交互。现有方法主要分为两类：
  - **点云方法**：显式表示3D几何，但采样稀疏导致细粒度语义丢失，且3D标注成本高限制了预训练规模。
  - **图像方法**（如RVT-2）：利用RGB-D图像在共享特征空间中联合建模语义和几何，能获得密集语义并受益于2D预训练，但语义和几何的纠缠使其对真实世界的深度噪声非常敏感，深度噪声会污染语义理解。此外，这些方法主要关注高级几何，忽略了低级空间线索（如精确的2D-3D对应关系），这对于精确交互至关重要。
- **问题**：如何构建一种鲁棒的空间表示，既具备细粒度的空间理解能力，又能抵抗传感器噪声，同时保留低级空间线索？
- **核心意义**：提出解耦的框架，显式分离语义和几何，通过融合互补的几何信息（鲁棒的专家先验与细粒度的原始深度）并利用低级空间位置编码，提升操纵的鲁棒性和精确性。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：  
  将输入（多视图RGB-D、语言指令、机器人状态）中的语义和几何解耦，分别处理后再融合。几何分支进一步分解为高级几何表示（通过SGM融合互补信息）和低级空间线索（通过SPT编码位置关系）。
- **整体架构**：
  - 使用CLIP作为视觉语言编码器提取语义特征（`F_sem`）和文本特征（`F_text`）。
  - 使用单独的深度编码器（ResNet-50）提取深度特征（`F_geo`）。
  - **Semantic-guided Geometric Module (SGM)**：
    - 利用冻结的、大规模预训练的深度估计专家（Depth Anything v2）从RGB中生成鲁棒但粗糙的几何先验（`hat{F}_geo`）。
    - 采用多尺度门控融合机制：`G = sigmoid(MLP(Concat(hat{F}_geo, F_geo)))`，然后融合：`F_fuse-geo = G ⊙ F_geo + (1-G) ⊙ hat{F}_geo`。这样自适应地保留深度细节同时抑制噪声。
  - **Spatial Transformer (SPT)**：
    - 利用相机内参和外参将每个像素的深度转换为机器人基坐标系下的3D坐标。
    - 采用旋转位置编码（RoPE）为每个空间token编码3D位置（公式9-11），建立精确的2D-3D映射。
    - 先后进行 **view-level interaction**（视图内自注意力+FFN）和 **scene-level interaction**（跨视图+语言特征的自注意力）来精炼token表示。
  - **动作预测**：使用轻量级解码器（ConvexUp）生成每视图2D热图，通过argmax得到目标2D位置并提升到3D；用MLP从局部特征回归旋转（欧拉角）和夹爪状态。
- **损失函数**：
  - 2D热图的交叉熵损失（平移）。
  - 离散化欧拉角的交叉熵损失（旋转）。
  - 夹爪状态的二分类损失。

## 3. 实验设计

- **仿真实验**：
  - **RLBench**（18个任务，249个变体）：CoppeliaSim模拟器，Franka机器人，4个固定RGB-D相机（128×128）。每个任务100个演示训练，25个未见场景测试。对比方法：C2F-ARM-BC, HiveFormer, PolarNet, PerAct, RVT, Act3D, SAM-E, 3D Diffuser Actor, RVT-2。
  - **ColosseumBench**（20个任务）：评估空间扰动（无变化、操作对象尺寸变化、接收对象尺寸变化、相机姿态扰动）。对比方法：R3M, MVP, VoxPoser, PerAct, RVT。
- **真实世界实验**：
  - WidowX机器人 + Intel RealSense D435i相机，8个任务共15个变体（如Pick Glue to Box, Stack Cup等）。每个任务收集25个演示，测试次数因任务而异（单变体20次，多变体各10次）。对比RVT-2。
- **鲁棒性实验**：在RLBench上对点云注入高斯噪声，三个等级（Light:20%点, std=0.05; Middle:50%点, std=0.1; Heavy:80%点, std=0.1）。
- **少样本泛化**：预训练模型微调到19个新任务，每任务仅10个演示（1/10数据）。
- **消融实验**：逐步添加“解耦”、“SGM”、“SPT”，在无噪声和重噪声下评估。

## 4. 资源与算力

- **文中说明**：训练约40k次迭代，余弦学习率调度（2k次预热）。使用**8块GPU**，总批量大小为192（每GPU 24），初始学习率2.4e-3。数据增强包括随机平移和旋转。
- **未明确说明**：GPU的具体型号、训练耗时（小时数）、以及基线方法的资源消耗对比。

## 5. 实验数量与充分性

- **实验数量**：覆盖模拟器（RLBench 18任务、ColosseumBench 20任务）、真实世界（8任务15变体）、噪声（3级）、少样本（19新任务）、空间扰动（4种）以及消融研究，总计超过50个任务场景。
- **充分性**：
  - 在RLBench上对比了9种主流基线，报告了平均值和标准差，结果具有统计意义。
  - 消融实验清晰证明了每个组件的有效性。
  - 真实实验设置了多种环境变化（操纵对象、接收对象、亮度、背景）验证泛化。
  - 与基线在相同条件下比较，代码开源保证可复现。
- **公平性**：采用相同的数据划分和评估协议（如RLBench标准设置）。噪声和扰动实验设计合理。

## 6. 论文的主要结论与发现

- **性能优越**：SpatialActor在RLBench上平均成功率**87.4%**，比之前最好方法RVT-2（81.4%）高6.0%；在高精度任务如Insert Peg上提升**53.3%**，Sort Shape提升38.3%。
- **强鲁棒性**：在三种噪声水平下分别提升13.9%、16.9%、19.4%；在ColosseumBench的空间扰动下也优于所有基线。
- **少样本泛化**：仅用10个演示适应新任务，成功率**79.2%**，远超RVT-2的46.9%（提升32.3%）。
- **真实世界有效**：在8个任务15个变体上平均成功率63%（RVT-2为43%），并在多种分布偏移下保持稳定。
- **解耦设计的价值**：消融证实解耦+ SGM + SPT每一步均带来增益，尤其在噪声环境下提升显著（重噪声下57.0%→76.4%）。

## 7. 优点（方法/实验亮点）

- **方法创新**：
  - 首次在操纵中显式解耦语义与几何，避免相互干扰。
  - SGM的设计巧妙结合了深度估计专家（鲁棒、粗粒度）和原始深度（细粒度、噪声大），通过门控自适应融合。
  - SPT利用旋转位置编码提供精确的2D-3D对应，为动作头提供低层空间线索。
- **实验充分**：
  - 涵盖模拟和真实，多种噪声和扰动设置，少样本和全量训练。
  - 与多个SOTA方法在统一基准上对比，结果有重复性统计。
  - 真实环境不仅评估成功率，还评估了分布偏移（对象、光照、背景）下的泛化。
- **开放贡献**：提供项目页面和代码，便于复现和扩展。

## 8. 不足与局限

- **计算开销**：使用冻结的Depth Anything v2视觉专家，虽然提供鲁棒先验，但可能增加推理延迟，文中未量化额外开销或与基线对比效率。
- **场景限制**：所有实验均在桌面操控场景（RLBench、简单真实桌面）中展开，未涉及移动操纵、复杂非结构化环境或动态物体。
- **真实世界规模**：仅8个任务，机器人硬件简单（WidowX），任务种类有限（主要集中在抓取、放置、堆叠等），未验证力控或灵巧操作。
- **消融深度不足**：只对比了解耦、SGM、SPT三个大模块，未深入探讨例如门控机制变体、不同位置编码方式、深度专家选择等消融。
- **训练资源**：需要8 GPU训练，但未与基线模型（如RVT-2）比较训练成本，读者难以评估性价比。
- **偏差风险**：深度专家基于互联网数据预训练，其泛化可能受限于训练域，在某些特殊材质或光照条件下的表现未知。

（完）
