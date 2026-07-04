---
title: "3D-MVP: 3D Multiview Pretraining for Manipulation"
title_zh: 3D-MVP：面向操纵的3D多视图预训练
authors: "Qian, Shengyi, Mo, Kaichun, Blukis, Valts, Fouhey, David F., Fox, Dieter, Goyal, Ankit"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Qian_3D-MVP_3D_Multiview_Pretraining_for_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向操纵任务的3D多视图预训练并预测抓取位姿动作
tldr: 现有机器人视觉预训练多基于2D图像，而操纵任务需要3D场景理解。本文提出3D-MVP，在Objaverse等大规模3D数据集上对多视图Transformer视觉编码器进行掩码自编码预训练。该编码器被集成到RVT框架中用于预测抓取位姿动作。实验表明，3D多视图预训练显著提升了策略在虚拟机器人操纵任务上的泛化能力，为3D视觉预训练在机器人中的落地提供了新范式。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1694, \"height\": 834, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1799, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 824, \"height\": 622, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1802, \"height\": 533, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1802, \"height\": 703, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-qian-3d-mvp-3d-multiview-pretraining-for-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1283, \"height\": 453, \"label\": \"Table\"}]"
motivation: 现有机器人视觉预训练仅基于2D图像，缺少对3D场景结构的建模。
method: 在Objaverse等3D数据上对多视图Transformer进行掩码自编码预训练，并用于RVT动作预测。
result: 在虚拟机器人操纵任务上显著提升泛化性能，验证3D多视图预训练的有效性。
conclusion: 3D多视图预训练可为视觉运动策略提供更丰富的几何表征，提升操纵性能。
---

## Abstract
Recent works have shown that visual pretraining on egocentric datasets using masked autoencoders (MAE) can improve generalization for downstream robotics tasks. However, these approaches pretrain only on 2D images, while many robotics applications require 3D scene understanding. In this work, we propose 3D-MVP, a novel approach for 3D Multi-View Pretraining using masked autoencoders. We leverage Robotic View Transformer (RVT), which uses a multi-view transformer to understand the 3D scene and predict gripper pose actions. We split RVT's multi-view transformer into visual encoder and action decoder, and pretrain its visual encoder using masked autoencoding on large-scale 3D datasets such as Objaverse. We evaluate 3D-MVP on a suite of virtual robot manipulation tasks and demonstrate improved performance over baselines. Our results suggest that 3D-aware pretraining is a promising approach to improve generalization of vision-based robotic manipulation policies.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "3D-MVP: 3D Multiview Pretraining for Manipulation" following a specific structure with 8 points. Let me analyze the paper carefully and provide a comprehensive summary.

Let me organize my thoughts on each section:

1. Core problem and motivation: The paper addresses the limitation of existing visual pretraining methods for robotics that only work on 2D images, while many manipulation tasks require 3D scene understanding.

2. Methodology: 3D-MVP uses masked autoencoding on multi-view 3D scenes. They split RVT's multi-view transformer into visual encoder and action decoder. Pretrain encoder E on Objaverse with MAE. Then finetune on downstream tasks.

3. Experimental setup: RLBench benchmark (18 tasks), COLOSSEUM benchmark (12 perturbations). Compared with Image-BC, C2F-ARM-BC, PerAct, RVT, MVP, R3M.

4. Resources: 8 NVIDIA V100 (32GB) GPUs for pretraining and finetuning, single V100 for evaluation. Pretrained for 15 epochs, finetuned for 15 epochs.

5. Experiments: Multiple ablations - architecture, masking strategy (RGB vs All), dataset choice (Objaverse small/full, 3D-FRONT, RLBench), pretraining on RLBench vs external data. RLBench results (18 tasks), COLOSSEUM results.

6. Main conclusions: 3D-aware pretraining improves performance and robustness significantly.

7. Strengths: Novel approach combining 3D pretraining with manipulation, comprehensive evaluation, clear ablation studies.

8. Limitations: Fixed camera viewpoints, no explicit occlusion reasoning, assumes quasi-static dynamics, requires labeled data per task, no real robot experiments.

Let me write a structured Chinese summary now.</think>

# 3D-MVP 论文总结

## 1. 核心问题与研究动机

- **核心问题**：现有面向机器人操控的视觉预训练方法（如 MAE）主要基于 2D 图像（如 Ego4D、Epic-Kitchens 等以自我为中心的视频数据集），而机器人操控任务通常需要 3D 场景理解能力。2D 预训练得到的表示难以直接迁移到具有显式 3D 表征的操控策略（如 RVT、PerAct、Act3D）中。
- **研究背景**：基于显式 3D 表示（如体素、点云、多视角 RGB-D）的操控策略相比 2D 视觉策略在样本效率和泛化性上更优；但这些方法目前都只能从零开始在有限的任务演示上训练，缺乏大规模 3D 数据上的预训练。
- **整体含义**：填补"3D 预训练"在操控策略中的空白，利用大规模 3D 物体数据集（如 Objaverse）对多视图 Transformer 进行掩码自编码预训练，从而提升下游操控策略的泛化性与鲁棒性。

## 2. 方法论

### 2.1 核心思想
- 基于 Robotic View Transformer (RVT) 框架，将多视图 Transformer 拆分为"渲染器 R + 视觉编码器 E + 动作解码器 D"。
- 在大规模 3D 数据集（Objaverse）上对视觉编码器 E 进行掩码自编码（MAE）预训练，学习 3D 感知的多视图表示。
- 预训练完成后丢弃轻量级 MAE 解码器 D_MAE，再将 E 与动作解码器 D 在下游操控演示数据上进行微调。

### 2.2 关键技术细节
- **多视图虚拟相机**：RVT 在点云上渲染 5 个正交虚拟视图（顶部、左、右、前、后），每张图含 10 通道：RGB(3) + Depth(1) + 世界坐标(3) + 相机坐标(3)。
- **网络结构**：
  - 编码器 E：8 层多视图 Transformer，8 个注意力头，隐藏维度 1024。
  - MAE 解码器：2 层多视图 Transformer，8 个注意力头（轻量化设计）。
  - 动作解码器 D：复用 RVT 的多视图 Transformer。
- **预训练任务**：对 5 张虚拟 RGB-D 图随机掩码 75% 的 patch，通过编码器得到潜在嵌入 z，再由 MAE 解码器重建所有视图。
- **损失函数**：
  $$L_{recon} = \frac{1}{5WH}\sum_{i=1}^{5}\sum_{p=1}^{W\cdot H}\|[I_i](p) - [\tilde{I}_i](p)\|_2^2$$
- **算法流程**（两阶段）：
  1. **预训练阶段**：从 Objaverse 采样点云 → 5 虚拟视图 → 掩码 → 编码器 E → MAE 解码器重建。
  2. **微调阶段**：丢弃 MAE 解码器 → 在操控演示数据上联合训练 E 与动作解码器 D → 预测末端 6-DoF 位姿 + 抓取开合状态。

## 3. 实验设计

### 3.1 评测基准
- **RLBench**：18 个虚拟操控任务（基于 CoppeliaSim 仿真，Franka Panda 机械臂 + 平行夹爪，4 个 RGB-D 相机观察，分辨率 128×128）。
- **COLOSSEUM**：20 个任务 × 12 种环境扰动（物体颜色、纹理、大小、光照等），用于系统评估鲁棒性。

### 3.2 对比方法
- **RLBench 基线**：Image-BC (CNN)、Image-BC (ViT)、C2F-ARM-BC、PerAct、RVT。
- **COLOSSEUM 基线**：RVT、MVP（2D MAE 预训练）、R3M（2D 重建+对比预训练）。

### 3.3 数据集
- **预训练数据**：Objaverse（采样 200K 高质量 3D 模型 + 1000 验证）；消融实验中用到 Objaverse-small (18K)、3D-FRONT、RLBench 点云。
- **下游数据**：RLBench 演示数据（标准设定）、COLOSSEUM 训练演示数据（每个任务 100 个演示）。

## 4. 资源与算力

- **预训练**：8 块 NVIDIA V100 GPU（PyTorch 实现）；训练 15 个 epoch，使用 AdamW 优化器，学习率 1e-4，权重衰减 0.01，batch size = 3，掩码率 0.75。
- **微调**：8 块 NVIDIA V100 (32GB)；学习率 1e-4，2000 warmup 步，cosine 衰减至 1e-6；LAMB 优化器，batch size = 3，训练 15 个 epoch（RLBench 和 COLOSSEUM）。
- **评估**：单块 V100。
- **未明确说明**：单次实验的具体运行时间（如多少小时/天）、总实验耗时。

## 5. 实验数量与充分性

### 5.1 实验规模
- **主实验**：18 个 RLBench 任务（详细成功率表）、COLOSSEUM 上 12 种扰动的对比。
- **消融研究**（Table 2）：共 7 组配置
  - 架构贡献：拆分后从零训练 vs. RVT 原始架构。
  - 预训练数据：Objaverse-full、Objaverse-small、3D-FRONT、RLBench、无预训练。
  - 掩码策略：仅 RGB 通道 vs. 所有 10 通道。
- **定性验证**：未见过 Objaverse 物体的重建可视化（Figure 3）；RLBench 预训练的过拟合分析（Figure 5）。

### 5.2 充分性与公平性
- **优点**：消融维度较多（数据集、规模、掩码策略、架构），并在两个互补的 benchmark 上验证（性能 + 鲁棒性）。
- **不足**：
  - 未报告每个消融的方差/置信区间（多次随机种子统计）。
  - RLBench 评测设定中提到"未与 2D 预训练方法对比，因为它们在 RLBench 上表现不佳"，使得 2D vs 3D 预训练的直接对比不够充分。
  - COLOSSEUM 中由于部分扰动参数难生成（如"empty dishwasher"），只报告了能生成的设置，可能引入选择偏差。

## 6. 主要结论与发现

- **性能提升**：3D-MVP 在 RLBench 上平均成功率 67.5%，优于 RVT (62.9%)、PerAct (49.4%)、C2F-ARM-BC (20.1%) 等。
- **提升来源**：拆解架构后从零训练仅得 62.9%，证明增益来自 3D 预训练本身，而非架构改动。
- **鲁棒性**：在 COLOSSEUM 上对物体大小、纹理、光照、桌面颜色等扰动均优于 RVT 与 2D 预训练方法（MVP、R3M）。
- **数据规模**：预训练数据越多越好（Objaverse-full > Objaverse-small > 3D-FRONT）。
- **数据集选择**：物体级数据（Objaverse）比场景级数据（3D-FRONT）更利于桌面操控任务。
- **预训练源选择**：可在 RLBench 点云上自监督预训练并取得相近性能（67.5%），但会过拟合到 RLBench 场景，难以泛化到 COLOSSEUM。
- **掩码策略**：仅掩码 RGB 通道优于掩码所有 10 通道（预训练任务过难会损害表示质量）。

## 7. 方法亮点

- **首个面向 3D 操控策略的预训练方案**：填补了 2D MAE 预训练与显式 3D 表示操控策略之间的空白。
- **架构解耦设计**：将渲染器、视觉编码器、动作解码器分离，使预训练可以无需机器人标注，纯粹利用 3D 模型数据。
- **大规模 3D 数据利用**：充分利用了 Objaverse 这类高质量、规模化的 3D 资产库，是 2D 视频预训练难以达到的 3D 信息密度。
- **跨视角推理**：通过多视图联合掩码重建任务，迫使模型学习跨视角的 3D 空间推理能力，而非单图像重建。
- **完整的两阶段范式**：预训练 + 微调流程清晰，便于迁移到其他 3D 表征的操控策略中。

## 8. 不足与局限

- **固定视角假设**：当前方案使用固定的 5 个正交虚拟相机视角，未处理任意视角或遮挡关系。
- **静态场景假设**：假设场景、机器人、物体遵循准静态动力学，不建模动态交互。
- **每任务仍需标注数据**：未能实现零样本泛化到全新任务，仍需每个下游任务的少量演示数据进行微调。
- **缺乏真机实验**：仅在仿真（CoppeliaSim）中验证，未给出真实机器人上的结果。
- **过拟合风险**：在 RLBench 自监督预训练虽在原任务上效果好，但泛化性下降，说明数据集多样性与规模对预训练至关重要。
- **潜在偏差**：Objaverse 等数据集的内容偏差（场景、物体类别、文化背景）可能传递到下游策略中。
- **可扩展性疑问**：作者认为可扩展到 Objaverse-XL（10M+ 物体）但未在文中实验验证，且当前算力消耗（8×V100、batch size=3）较大。
- **COLOSSEUM 评测的不完整性**：部分扰动无法生成，限制了与基线的全维度比较。

（完）
