---
title: A Data-Centric Revisit of Pre-Trained Vision Models for Robot Learning
title_zh: 以数据为中心重新审视预训练视觉模型在机器人学习中的应用
authors: "Wen, Xin, Zhao, Bingchen, Chen, Yilun, Pang, Jiangmiao, Qi, Xiaojuan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wen_A_Data-Centric_Revisit_of_Pre-Trained_Vision_Models_for_Robot_Learning_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 系统评估预训练视觉模型在视觉运动控制中的表现
tldr: 预训练视觉模型在机器人领域应用广泛，但其最优配置尚不明确。论文通过系统评估发现，能否从非物体中心数据中学到物体中心表征是决定视觉运动控制性能的关键。基于此提出的SlotMIM方法通过语义瓶颈压缩原型数量来诱导物体中心表征。在视觉运动控制与感知任务上的实验表明，新方法在非物体中心数据上显著优于DINO、iBOT和MAE等基线，为机器人视觉预训练的数据选择提供了新视角。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1782, \"height\": 620, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 226, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1812, \"height\": 420, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 872, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 690, \"height\": 382, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 645, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1086, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1601, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1811, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 871, \"height\": 363, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 999, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 830, \"height\": 313, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wen-a-data-centric-revisit-of-pre-trained-vision-models-for-robot-learning-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 354, \"label\": \"Table\"}]"
motivation: 预训练视觉模型在机器人中的最优配置尚不清晰，尤其在非物体中心数据上表现欠佳。
method: 提出SlotMIM，通过语义瓶颈限制原型数来诱导物体中心表征。
result: 系统评估多个PVM并验证物体中心表征对视觉运动控制性能的关键作用。
conclusion: 物体中心表征能力是预训练视觉模型在机器人学习上成功的核心因素。
---

## Abstract
Pre-trained vision models (PVMs) are fundamental to modern robotics, yet their optimal configuration remains unclear. Through systematic evaluation, we find that while DINO and iBOT outperform MAE across visuomotor control and perception tasks, they struggle when trained on non-(single-)object-centric (NOC) data--a limitation strongly correlated with their diminished ability to learn object-centric representations. This investigation indicates that the ability to form object-centric representations from the non-object-centric robotics dataset is the key to success for PVMs. Motivated by this discovery, we designed SlotMIM, a method that induces object-centric representations by introducing a semantic bottleneck to reduce the number of prototypes to encourage the emergence of objectness as well as cross-view consistency regularization for encouraging multiview invariance. Our experiments encompass pre-training on object-centric, scene-centric, web-crawled, and ego-centric data. Across all settings, our approach learns transferrable representations and achieves significant improvements over prior work in image recognition, scene understanding, and robot learning evaluations. When scaled up with million-scale datasets, our method also demonstrates superior data efficiency and scalability. Our code and models are publicly available at https://github.com/CVMI-Lab/SlotMIM.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "A Data-Centric Revisit of Pre-Trained Vision Models for Robot Learning" organized into 8 specific sections. Let me carefully analyze the paper content provided and structure my response accordingly.

Let me go through the paper systematically:

1. Core problem: Pre-trained vision models (PVMs) optimal configuration for robot learning is unclear. Questions: Is MAE optimal? Is ego-centric data best?

2. Method: SlotMIM - introduces semantic bottleneck (reduce number of prototypes to encourage objectness emergence), cross-view consistency regularization for multiview invariance, combines MIM and contrastive learning on object-level slots.

3. Experiments: 
- Datasets: ImageNet (object-centric), COCO+ (scene-centric), CC12M (web-crawled), Ego4D (ego-centric)
- Benchmarks: Franka Kitchen, Meta-World (manipulation), Pascal VOC, ADE20K (segmentation), COCO (detection), ObjectNav, ImageNav (navigation)
- Compared methods: BEiT, SplitMask, MAE, DINO, iBOT, plus MVP, VC-1, V-Cond for scaling
- Backbone: ViT-B/16

4. Resources: Not explicitly mentioned GPU specs, but mentions 241K and 1.28M data scales, 800/400 epochs, mentions "extreme GPU demands" for navigation tasks

5. Experiments count: Multiple dataset × method combinations, ablation study (5 configurations), scaling experiments, 6+ downstream tasks

6. Conclusions: 
- DINO/iBOT outperform MAE across tasks
- Both struggle with NOC data
- Object-centric representation ability is key
- SlotMIM is more data efficient and scalable

7. Highlights: Systematic study across multiple dimensions, novel object-centric approach, surprising inverse-scaling findings

8. Limitations: 
- Mainly ViT-B/16 backbone
- Navigation limited due to GPU constraints
- Doesn't cover all PVM paradigms (language, 3D)

Let me write this up in Chinese with clear Markdown structure.</think>

# 论文总结：《A Data-Centric Revisit of Pre-Trained Vision Models for Robot Learning》

## 1. 核心问题与研究动机

- **核心问题**：预训练视觉模型（PVM）在机器人学习中的最优配置尚未明确，特别是两个广泛被接受的假设被质疑：
  - **MAE 是否是最优预训练方法？** 主流机器人 PVM 方案（R3M、MVP、VC-1、V-Cond 等）几乎都默认采用 MAE。
  - **第一人称（ego-centric）数据是否最佳？** 业界普遍认为 Ego4D 等第一人称视频因与操控任务场景相似而最有价值。
- **研究背景**：现有工作存在两个缺口——①评估主要局限于 ego-centric 数据 + MAE；②评估多集中在操控任务，缺乏对导航、感知等任务的多维比较。
- **本文意图**：从数据中心的视角，系统比较不同（预训练方法 × 数据源 × 任务）组合下的 PVM 表现，并据此提出新方法。

## 2. 方法论：SlotMIM

- **核心思想**：将 NOC（非单一物体中心）数据下的自监督学习拆解为两个子任务：①将图像 patch 分组为"物体"；②在物体层级做对比学习。
- **关键技术细节**：
  - **语义瓶颈（Semantic Bottleneck）**：将 iBOT 的原型数从默认 8192 大幅减少（如 COCO+ 上用 512），迫使其从细粒度纹理聚类退化为语义级"物体性"涌现。
  - **跨视图一致性正则化** $L_{\text{cross patch}}$：在两个增强视图间，用 RoIAlign 匹配 patch，对学生预测的聚类分配与教师 patch 的聚类分配做交叉熵，鼓励视图不变语义学习。
  - **物体级槽位对比学习** $L_{\text{slot}}$：先用原型作为 query、patch embedding 作为 key 做 attentive pooling，将同一聚类内的 patch 聚合成"slot"（物体特征），再用 MoCo 风格对比损失在 slot 之间进行实例判别。
  - **总损失**：$L = \lambda_1 L_{\text{within patch}} + \lambda_1 L_{\text{cross patch}} + \lambda_2 L_{\text{slot}}$，其中 $\lambda_1=0.5,\ \lambda_2=1$。
- **算法流程概述**：
  1. 用 mask token 处理掩码 patch；
  2. 学生/教师分支分别产生 patch embedding 与聚类分配；
  3. 视图内 patch 重建（iBOT-style）+ 跨视图语义对齐（新增）；
  4. 通过原型引导的注意力池化聚合为 slot；
  5. 在 slot 空间做对比学习。

## 3. 实验设计

- **预训练数据**（统一控制为 241K 图像）：
  - **物体中心**：ImageNet（INet-241K，平均 1.7 物体/图）
  - **场景中心**：COCO+（241K，平均 7.3 物体/图）
  - **网络爬取**：CC12M（CC-241K）
  - **第一人称**：Ego4D（Ego-241K，0.2 fps 采帧）
  - 扩展数据集：DetSoup（4M，由 ImageNet + COCO+ + OpenImages + Objects365 + LVIS 组成），用于百万级实验。
- **下游基准**：
  - **操控**：Franka Kitchen（5 任务）、Meta-World（8 任务），均用 25 条演示、行为克隆 + attentive pooling、不使用本体感知；
  - **导航**：ObjectNav、ImageNav（设置沿用 VC-1）；
  - **感知**：Pascal VOC 2012 分割、ADE20K 语义分割（UperNet, 160K iter, bs=16）、COCO 检测/实例分割（Cascade Mask R-CNN, 1× schedule）。
- **对比方法**：
  - 主对比：BEiT、SplitMask、MAE、DINO、iBOT；
  - 扩展对比：MVP（ViT-B/L, EgoSoup 4.6M）、VC-1（ViT-B/L, 5.6M）、V-Cond、iBOT-12M（ImageNet-21K）；
  - 骨干网络：ViT-B/16，241K 数据训练 800 epoch，1.28M 数据训练 400 epoch。

## 4. 资源与算力

- 文中**未明确披露**具体的 GPU 型号、数量、训练总时长。
- 仅有的相关线索：
  - 提到导航任务"extreme GPU demands"，因此在导航评测中只选了 2 个 SlotMIM 模型（Ego-241K 1.28M 与 DetSoup 4M）；
  - 4M 规模场景中心数据（DetSoup）预训练消耗显著，但具体卡数未给出；
  - 800/400 epoch 的训练规模与 ViT-B/16 的标准算力大体吻合。
- **结论**：算力信息不充分，读者难以复现完整对比开销。

## 5. 实验数量与充分性

- **实验规模**：
  - 4 数据源 × 6 预训练方法 ≈ 24 组主对比，外加 SlotMIM；
  - 百万级 scaling 实验覆盖 MAE / DINO / iBOT / SlotMIM 在 ego、object、scene 三类数据上的曲线（Fig. 6）；
  - 5 组消融实验（Tab. 3）覆盖 mask、$L_{\text{cross patch}}$、$L_{\text{within patch}}$、$L_{\text{slot}}$ 开关；
  - 6 个下游任务（Franka Kitchen、Meta-World、ObjectNav、ImageNav、COCO 检测/分割、ADE20K）。
- **公平性考量**：
  - 数据规模、骨干、训练 epoch 数严格对齐；
  - 操控任务采用 attentive probing（避免 [CLS] token 偏置），3 个种子取平均，遵循 [45, 33] 设置；
  - 感知任务沿用 iBOT/MAE 官方评估协议。
- **总体评价**：实验维度较广，控制变量较严；但仍存在少量维度未覆盖（如 BEiT/SplitMask 仅有 241K 扩展、未给出更多骨干规模）。

## 6. 主要结论与发现

- **MAE 不是最优**：在 241K 尺度下，DINO/iBOT 在所有任务上显著优于 MAE，特别是在物体中心数据上。
- **ego-centric 不是最优数据**：场景中心、物体中心数据在多个任务上反而更优。
- **物体中心能力是关键**：DINO/iBOT 在 NOC 数据上表现骤降，与其注意图学到的"objectness"下降强相关（相关系数 0.72）。
- **反向 scaling 现象**：MAE 随数据量增大而提升，但 DINO/iBOT 在百万级数据上反而下降（被解释为"过压缩"，丢失低层视觉信息）。
- **SlotMIM 的优势**：
  - 在 241K 规模即可超过使用 1M+ 数据的 MVP、VC-1；
  - 在 NOC 数据（场景/网络爬取）上仍能持续提升；
  - 跨任务、跨数据源均稳定领先；
  - 在 ADE20K、COCO 上以 1/3 数据量超过 ImageNet-21K（12M）训练的 iBOT；
  - 导航任务（ObjectNav）用 DetSoup 提升 6.6%、ImageNav 提升 1.9% 相对 MVP/VC-1。

## 7. 优点与亮点

- **数据中心视角的系统性研究**：首次以网格化方式扫描（方法 × 数据 × 任务），打破"MAE + Ego4D"单一范式。
- **新颖的物体中心学习机制**：通过减少原型数量制造语义瓶颈，并结合跨视图一致性 + slot 级对比，显式注入 objectness 监督。
- **令人惊讶的反向 scaling 发现**：揭示了 DINO/iBOT 在大规模 NOC 数据上的过压缩问题，对 PVM 扩展实践有警示意义。
- **跨任务通用性强**：同时在操控、导航、检测、分割上验证，而非局限于某一类任务。
- **数据效率突出**：仅 241K 即可达到甚至超过百万级 PVM，下游训练成本大幅降低。
- **代码与模型开源**：便于复现和后续工作对比。

## 8. 不足与局限

- **算力与规模信息缺失**：未给出 GPU 型号、卡数、训练时长，无法评估复现成本。
- **骨干规模有限**：主要以 ViT-B/16 为主，仅在导航任务中与 ViT-L 的 MVP/VC-1 做了粗对比；缺少对 ViT-L、ViT-H 的全面扫描。
- **导航实验覆盖不足**：仅评估 2 个 SlotMIM 模型，未与其他 ego-centric 方法在同尺度下充分对照。
- **百万级实验中部分方法数据规模不对齐**：MAE 用 5M ego-centric（EgoSoup），iBOT 用 12M ImageNet-21K，SlotMIM 用 4M DetSoup，三者横向比较时数据分布差异较大，可能影响结论的客观性。
- **缺少语言/3D PVM 范式对比**：未与 CLIP、LIV、SUGAR 等基于语言或 3D 的 PVM 直接比较。
- **objectness 量化方法依赖特定度量**：用注意力图聚类度量物体性，相关性结论（0.72）可能受度量方式影响。
- **应用限制**：方法主要在静态 RGB 图像上预训练，未涉及时序、视频帧间监督或触觉等多模态信号；并且对真实机器人在闭环、动态环境中的鲁棒性尚未评估。

（完）
