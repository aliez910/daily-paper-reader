---
title: Efficient Hybrid SE(3)-Equivariant Visuomotor Flow Policy via Spherical Harmonics for Robot Manipulation
title_zh: 基于球谐函数的高效混合 SE(3) 等变视觉运动流策略用于机器人操作
authors: "Zhang, Qinglun, Cheng, Shen, Dan, Tian, Fan, Haoqiang, Liu, Guanghui, Liu, Shuaicheng"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhang_Efficient_Hybrid_SE3-Equivariant_Visuomotor_Flow_Policy_via_Spherical_Harmonics_for_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向机器人操作的端到端等变视觉运动流策略
tldr: 现有等变方法虽提升机器人操作数据效率，但计算开销大、依赖单一模态输入且与快速采样结合时不稳定。为此，本文提出 E3Flow 框架，首次统一高效整流流与稳定的多模态等变学习，基于球谐表示确保严格的 SO(3) 等变性，并设计不变特征增强模块动态融合点云与图像两种视觉模态。该方法为机器人操作提供稳定高效的端到端视觉运动流策略，有助于推进复杂操作任务中的等变策略学习。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 756, \"height\": 693, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1704, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 824, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1689, \"height\": 909, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 821, \"height\": 701, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1715, \"height\": 502, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1701, \"height\": 520, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1707, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 835, \"height\": 301, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-efficient-hybrid-se3-equivariant-visuomotor-flow-policy-via-spherical-harmonics-for-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 830, \"height\": 432, \"label\": \"Table\"}]"
motivation: 现有等变策略方法计算昂贵、依赖单一模态且难以与快速采样结合。
method: 基于球谐表示构建 SO(3) 等变整流流，并融合点云与图像两种视觉模态进行策略学习。
result: 在机器人操作任务上实现稳定、高效且数据高效的等变策略训练。
conclusion: 为等变视觉运动策略在复杂机器人操作中的实用化提供了新方案。
---

## Abstract
While existing equivariant methods enhance data efficiency, they suffer from high computational intensity, reliance on single-modality inputs, and instability when combined with fast-sampling methods. In this work, we propose E3Flow, a novel framework that addresses the critical limitations of equivariant diffusion policies. E3Flow overcomes these challenges, successfully unifying efficient rectified flow with stable, multi-modal equivariant learning for the first time. Our framework is built upon spherical harmonic representations to ensure rigorous SO(3) equivariance. We introduce a novel invariant Feature Enhancement Module (FEM) that dynamically fuses hybrid visual modalities (point clouds and images), injecting rich visual cues into the spherical harmonic features. We evaluate E3Flow on 8 manipulation tasks from the MimicGen and further conduct 4 real-world experiments to validate its effectiveness in physical environments. Simulation results show that E3Flow achieves a 3.12% improvement in average success rate over the state-of-the-art Spherical Diffusion Policy (SDP) while simultaneously delivering a 7x inference speedup. E3Flow thus demonstrates a new and highly effective trade-off between performance, efficiency, and data efficiency for robotic policy learning. Code: https://github.com/zql-kk/E3Flow.

---

## 论文详细总结（自动生成）

<think>The user wants a structured Chinese summary of the paper based on the provided content. Let me analyze the paper carefully and generate a detailed summary covering all 8 requested points.

The paper is about E3Flow, an equivariant visuomotor flow policy for robot manipulation using spherical harmonics. Let me organize the content according to the requested structure.

Key points:
1. Problem: Equivariant methods enhance data efficiency but suffer from high computational cost, single-modality reliance, and instability with fast sampling
2. Method: E3Flow - spherical harmonic SO(3) equivariant + rectified flow + FEM for multi-modal fusion
3. Experiments: MimicGen 8 tasks, real-world 4 experiments, compared with multiple baselines
4. Resources: Single H20 GPU, 500 epochs
5. Experiments: Multiple ablation studies, comparisons
6. Results: 3.12% improvement over SDP, 7x speedup
7. Advantages: First flow matching equivariant policy, hybrid modal fusion
8. Limitations: limited to spherical harmonics, local SE(3) issues, etc.

Let me write this in Chinese Markdown format.</think>

# 论文总结：E3Flow — 基于球谐函数的高效混合 SE(3) 等变视觉运动流策略

## 1. 核心问题与研究动机

- **背景**：基于扩散模型的机器人策略（如 DP、DP3）虽擅长建模多模态动作分布，但严重依赖大量高质量专家数据，数据采集成本高、泛化能力受限。
- **现有等变方法的痛点**：
  - 计算开销大（EquiBot、ET-SEED、SDP 等需数百步去噪，且等变网络本身参数重）；
  - 多依赖单一视觉模态（点云或图像），缺乏细粒度语义信息；
  - 与快速采样方法（如 FlowPolicy、Consistency Policy、MeanFlow）结合不稳定，复杂任务性能显著下降。
- **核心问题**：能否在保持数据效率（等变性）的同时，获得快速采样与多模态融合的优势？E3Flow 旨在填补"等变性 + 快速流匹配 + 多模态融合"三者之间的空白。

## 2. 方法论：E3Flow

### 2.1 整体框架
- 输入：手眼相机 RGB-D 图像 + 单视角点云 + 机器人本体感受状态；
- 编码：ResNet 提取图像不变特征，EquiformerV2 提取点云球谐等变特征；
- 融合：通过**特征增强模块（Feature Enhancement Module, FEM）**将图像语义注入点云球谐表示的 Type-0 分量；
- 生成：在球谐等变空间中以**整流流（Rectified Flow）**进行动作生成，端到端 SE(3) 等变。

### 2.2 关键技术细节
- **球谐表示**：将特征表示为连续球谐系数 $Y_l^m(\theta,\phi)$，自然保证 SO(3) 等变性，避免 EquiDiff 的离散化误差；
- **FEM**：用交叉注意力 $A(f_{pcd}^{(0)}, f_{img})$ + 门控 $\Lambda$ 动态调节图像贡献，最后投影回球谐空间 $f_{fused} = \Pi(\Lambda(f_{pcd}^{(0)}, f_{img}), f_{pcd}^{(0)} \| f_{pcd}^{(>0)})$；
- **状态嵌入**：3D 位置与 6D 旋转按等变量嵌入，夹爪状态按平凡表示 $ρ_0$ 嵌入；
- **整流流目标**：通过线性插值 $x_t = (1-t)x_0 + t a$ 与速度场 $v_t^* = a - x_0$ 的最小二乘回归学习 ODE；因其参数网络等变、目标函数在群作用下不变，**端到端满足等变性**。
- **流程（Fig.2）**：视觉编码 → FEM 融合 → 球谐等变特征 → Equi-Flow U-Net → 多步流匹配 → 等变动作。

## 3. 实验设计

- **仿真基准**：MimicGen 上 8 个操作任务（Coffee D2、Coffee Preparation D1、Hammer Cleanup D1、Mug Cleanup D1、Nut Assembly D0、Square D2、Stack D1、Stack Three D1），每个任务 100 条专家演示；
- **真实环境**：4 个真实机器人实验（细节在补充材料）；
- **零样本 SE(3) 测试**：训练在水平桌面场景，测试时桌面与物体沿 y 轴倾斜 10°；
- **对比基线**：
  - 等变方法：EquiBot（SIM(3)）、EquiDiff (img/voxel, SO(2)）、SDP (DDiM/DDPM, SE(3))；
  - 非等变方法：BC-RNN、ACT、DP（图像）、DP3（点云）；
- **评估指标**：最大成功率（3 个随机种子，每 20 epoch 评估 50 回合取最大）+ 平均推理时间；
- **消融**：模态组合（PCD / PCD+Img）、融合方式（concat / FEM）、生成范式（Diffusion / RF）、流匹配方法（MeanFlow / αFlow / RF-1/5/10）、数据规模（20/50/100/200 条）。

## 4. 资源与算力

- **GPU**：单张 **NVIDIA H20** GPU；
- **训练时长**：每个任务 500 epoch，批量大小 64，AdamW 学习率 $1\times10^{-4}$，使用 EMA（衰减率 0.95）；
- **其他**：图像分辨率 84×84，点云经最远点采样到 1024 点并保留颜色，体素网格 $84^3$；
- **明确缺失**：未报告每任务具体训练小时数、单次训练能耗或多次消融实验的累计算力。

## 5. 实验数量与充分性

- **数量**：
  - 5 张主要结果表（成功率、推理时间、SE(3) 扰动、消融、流匹配对比）+ 1 张数据效率图 + 5 张示意图；
  - 8 任务 × 3 种子 × 多基线 + 4 个真实任务 + 5 类消融 + 5 种流匹配变体 + 4 种数据规模；
- **充分性评估**：
  - **优点**：基线覆盖了 SO(2)/SIM(3)/SE(3)/非等变多种等变粒度与多种视觉模态；消融覆盖输入模态、融合方式、生成范式、流匹配变体、数据规模五个维度；
  - **不足**：
    - 每任务只用 100 条演示（部分任务规模较小），未在更大数据集上验证；
    - SE(3) 扰动只测了 10°（受重力限制），未覆盖更大幅度或平移扰动；
    - 真实实验仅 4 个场景，缺少失败案例统计与跨平台迁移数据；
    - 随机种子数为 3，统计显著性检验未充分报告。

## 6. 主要结论与发现

- **性能**：E3Flow 在 8 个 MimicGen 任务上的平均成功率达 **79.00%**，较 SDP (DDPM) 提升 **3.12%**，较 DP3 提升 **53.5%**，较 EquiDiff (voxel) 提升 **10.5%**；
- **效率**：平均推理时间 **0.51 s**，较 SDP (DDPM, 3.73 s) **快 7×**，较 EquiDiff (img) 快 5×，较 EquiDiff (voxel) 快 2×；
- **泛化性**：在 10° SE(3) 倾斜场景下，E3Flow 全面优于 SDP、EquiDiff、DP、EquiBot（如 Nut Assembly 0°→10° 仅从 94% 降至 52%，仍为最优）；
- **数据效率**：用 100 条演示即可达到其他方法 200 条演示的水平；
- **流匹配优势**：现有一步采样（MeanFlow / αFlow / RF-1）在复杂任务上不稳定；RF-10 在效率与性能之间取得最佳折衷；
- **FEM 作用**：相比简单 concat 融合，FEM 在 PCD+Img 输入下提升 ~6.6% 成功率（79.00% vs 72.36%）。

## 7. 优点与亮点

- **首次将 Rectified Flow 引入等变策略**，在保留等变性的同时实现快速多模态动作生成；
- **球谐表示 + 高阶系数**，避免了离散化等变方法（如 EquiDiff）误差，并能捕获更细的方向信息；
- **FEM 动态门控机制**，将图像语义选择性注入 Type-0 标量分量，比硬拼接更适合等变空间；
- **单一前向传播**，相比 ET-SEED 的多尺度采样大幅加速；
- **混合输入（点云 + 图像）** 缓解 SDP 在遮挡场景下点云信息不足的问题；
- **理论与实现结合紧密**：显式证明损失与参数化的群不变性 → 等变最优解存在。

## 8. 不足与局限

- **角度扰动有限**：仅在 10° 倾斜下测试，更大角度因重力不可行；未测试纯平移 SE(3) 扰动；
- **演示规模偏小**：主实验固定 100 条演示，缺少大尺度（>1k）演示下的可扩展性验证；
- **真实实验披露不足**：仅提及"4 个真实机器人实验"，细节在补充材料，正文中无失败统计；
- **未探讨非平凡等变特征的作用**：作者明确将未来工作方向定为"系统研究不变/等变视觉特征对动作精度的影响"，说明本文未触及该问题；
- **统计严谨性**：仅 3 个随机种子，未提供置信区间或显著性检验；
- **算力报告单薄**：缺少训练时长、能耗、显存峰值等信息，难以复现成本评估；
- **方法依赖**：FEM 与 EquiformerV2 等较大骨干限制了端侧实时部署；球谐阶数与系数通道数对性能/效率的敏感度未充分分析。

（完）
