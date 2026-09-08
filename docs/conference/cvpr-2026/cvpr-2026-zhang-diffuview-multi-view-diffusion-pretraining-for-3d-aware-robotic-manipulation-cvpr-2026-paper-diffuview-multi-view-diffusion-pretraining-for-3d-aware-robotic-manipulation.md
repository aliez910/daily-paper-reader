---
title: "DiffuView: Multi-View Diffusion Pretraining for 3D Aware Robotic Manipulation"
title_zh: DiffuView：面向3D感知机器人操纵的多视图扩散预训练
authors: "Zhang, Kaizhao, Niu, Tian, Liu, Tianyu, Guo, Chenen, Xu, Zijun, Hu, Qingda, Ding, Wenchao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhang_DiffuView_Multi-View_Diffusion_Pretraining_for_3D_Aware_Robotic_Manipulation_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过多视图扩散预训练实现3D感知的视觉运动模仿学习
tldr: 本文针对机器人操纵中缺乏跨视角一致3D表征的问题，提出DiffuView框架。该方法利用多视图扩散模型进行预训练以学习统一的3D感知表征，并将其部署到模仿学习中实现视角鲁棒的视觉运动控制。该工作为复杂操作任务中的端到端视觉运动学习提供了强大的3D感知基础表示。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 900, \"height\": 811, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1807, \"height\": 974, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 907, \"height\": 1176, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1812, \"height\": 471, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 862, \"height\": 688, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 862, \"height\": 419, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1810, \"height\": 441, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 193, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1816, \"height\": 259, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 914, \"height\": 139, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 914, \"height\": 177, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-diffuview-multi-view-diffusion-pretraining-for-3d-aware-robotic-manipulation-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 916, \"height\": 259, \"label\": \"Table\"}]"
motivation: 现有视觉表征方法难以捕捉跨视角一致性，限制了视角鲁棒的视觉运动控制。
method: 通过多视图扩散预训练学习统一的3D感知表征，并将其应用于模仿学习。
result: DiffuView在多种操纵任务中实现了更鲁棒的视觉运动策略学习。
conclusion: 为复杂机器人操纵中的3D感知模仿学习提供了新的预训练范式。
---

## Abstract
Robotic manipulation from visual observations remains challenging due to the lack of 3D consistent representations that can generalize across diverse viewpoints and sensor configurations. Existing approaches often rely on masked autoencoders or neural scene representations, which fail to capture cross view correspondences. Crucially, while multi-view diffusion models have recently shown tremendous success in 3D aware generative synthesis, their powerful representations offer a promising direction for achieving viewpoint robust visuomotor control. In this paper, we introduce DiffuView, a novel framework that learns unified 3D aware representations through multi-view diffusion pretraining and deploys them for imitation learning. Specifically, DiffuView models the conditional generation of target views given source observations within a diffusion framework, enabling the network to implicitly recover scene geometry and enforce view consistency. The pretrained diffusion network is then utilized as a powerful visual backbone for an action policy, allowing robust control under varying viewpoints and visual conditions. We evaluate DiffuView on two challenging benchmarks, MetaWorld and Libero. Extensive experiments in both simulation and realworld scenarios demonstrate that DiffuView achieves superior generalization, improving success rates under viewpoint shifts by nearly 20% compared with existing methods.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze a research paper about DiffuView, a multi-view diffusion pretraining framework for 3D-aware robotic manipulation. Let me carefully read through the paper content and provide a structured summary in Chinese covering all 8 requested points.

Let me analyze the paper systematically:

1. **Core problem/motivation**: Robotic manipulation from visual observations is challenging because existing methods lack 3D consistent representations that generalize across viewpoints. MAE-based methods and neural scene representations both have limitations - MAE lacks global 3D consistency, neural rendering requires scene-specific optimization.

2. **Methodology**: 
   - Two-stage framework
   - Stage 1: Multi-view diffusion pretraining
     - Uses Plücker ray embeddings, depth, warped RGB-D pairs
     - Conditional generation of target views given source observations
     - VAE encoding, multi-view attention (2D intra-view, 3D cross-view)
     - 1-3 source views, M target views, no fixed positional encoding
   - Stage 2: Policy learning
     - Pretrained diffusion UNet as 3D-aware vision encoder
     - FiLM-conditioned Q-Former with CLIP text guidance
     - Mixture of Denoising Experts (MoDE) diffusion policy
     - Causal self-attention for action sequences
     - Noise-conditioned MoE with Top-2 activation
     - DDIM solver, 10 denoising steps

3. **Experiments**:
   - Datasets: RH20T (real-world), Objaverse, Co3Dv2, ScanNet, Real10k (pretraining), RoboSuite + CoppeliaSim (simulation pretraining), Libero (10/90/Spatial), MetaWorld (50 tasks)
   - Benchmarks: Libero, MetaWorld, Mv-Bench (custom)
   - Compared with: DP, MT-ACT, MDT, OpenVLA, Dita, VQVLA, π0.5-ki, RT-1, SuSIE, GR-1, Baku, VPP
   - Real-world: Franka Research 3 with RealSense D435/D455, 8 tasks

4. **Resources**: 8 NVIDIA A100 GPUs, about 2 days for pretraining fine-tuning

5. **Experiments count**: 
   - Libero benchmark (3 subsets)
   - MetaWorld benchmark (50 tasks)
   - Mv-Bench (view generalization)
   - Real-world (4 reported tasks out of 8)
   - Ablation studies (5 ablations)
   - Plus qualitative analyses

6. **Conclusions**: 
   - State-of-the-art on multiple benchmarks
   - Robust to viewpoint shifts (~20% improvement)
   - Effective view-adaptive module

7. **Strengths**: 
   - Novel application of multi-view diffusion to robotic representation learning
   - Two-stage framework
   - Comprehensive experiments including real-world
   - Strong performance on viewpoint generalization

8. **Limitations**:
   - No explicit dynamic temporal information
   - Performance degrades with very large viewpoint shifts due to geometric occlusions
   - Limited real-world task diversity (only 4 tasks reported quantitatively out of 8)
   - Reliance on depth estimation for RGB-only setups
   - High computational requirements

Let me write this in Chinese with proper Markdown structure.</think>

# DiffuView 论文总结

## 1. 核心问题与研究动机

- **核心痛点**：基于视觉观测的机器人操控面临**缺乏跨视角一致的 3D 表征**这一根本挑战，导致策略难以在多变视角与不同传感器配置下泛化。
- **现有方法的不足**：
  - **MAE 类方法**（如 MVP、3D-MVP、Lift3D、Embodied-MAE、CL3R）：依赖掩码重建，缺乏全局 3D 一致性。
  - **神经渲染类方法**（如 GNFactor、SPA、PDFactor）：通过三平面/体素/高斯场将 2D 特征提升到 3D 潜空间，但需要**场景特定优化**，且难以学到跨视角统一的表征。
- **研究洞察**：多视图扩散模型（MVDM）在 3D 感知生成任务上取得巨大成功（如 Free3D、Cat3D、ViewCrafter、Gen3C、Bolt3D），其强大的跨视角对应能力可被迁移到机器人操控领域。
- **研究目标**：提出一个统一框架，将多视图扩散预训练与模仿学习结合，实现**视角鲁棒的视觉运动（visuomotor）控制**。

## 2. 方法论

### 2.1 整体框架（两阶段）
- **阶段一：多视图扩散预训练** —— 学习跨视角几何一致的潜空间表征。
- **阶段二：策略学习** —— 将预训练扩散模型作为 3D 感知视觉编码器，下游用于动作生成。

### 2.2 关键模块与技术细节

- **几何信息编码**：
  - 利用源观测的 RGB-D 与相机内外参计算 3D 点云，并重投影到目标相机帧，得到**扭曲的 RGB 与深度图**（$\tilde{I}_{i\rightarrow j}, \tilde{D}_{i\rightarrow j}$）。
  - RGB-only 场景下使用 **MapAnything 估计度量深度**作为替代。
  - 采用 **Plücker 射线嵌入**：每条射线的方向 $d$ 与矩向量 $m = o \times d$ 拼接成 6 维向量，为每个像素注入相机几何上下文 $E_i \in \mathbb{R}^{6 \times H \times W}$。

- **3D 感知多视图扩散模型**：
  - VAE 编码图像到 $\frac{H}{8} \times \frac{W}{8}$ 潜空间；将 RGB、深度、相机嵌入通过轻量 CNN 叠加到 VAE 潜变量上。
  - **2D 空间注意力**捕捉视图内空间依赖，**3D 全注意力**推理跨视图几何关系。
  - 训练时 $N+M=8$ 视图（$N$ 源、$M$ 目标），$N$ 在 $\{1,2,3\}$ 中**随机采样**。
  - **不使用时间/位置编码**，使模型可自然外推到任意数量的源/目标视图。

- **视觉特征提取器**（阶段二）：
  - 复用预训练 UNet 作为编码器，提取其上采样层的多尺度特征。
  - 通过 **FiLM 条件 Q-Former** + **CLIP 文本嵌入**生成任务相关的紧凑视觉 token $z_{obs}$。
  - 推理时**仅做一次前向扩散**（类似 VPP），不做完整去噪。

- **扩散策略网络**：
  - 标准 DDPM 训练：$\mathcal{L}_{policy} = \mathbb{E}\|\epsilon - \epsilon_\psi(a^{(t)}, t, z_{obs}, l_{emb})\|^2$。
  - **RMSNorm** 替代 LayerNorm，提高稳定性。
  - **因果自注意力**：动作 token 间使用因果掩码，保证时序一致性。
  - **Mixture of Denoising Experts (MoDE)**：每层 4 个专家，根据噪声水平 token $\eta(\sigma_t)$ 通过路由器**稀疏激活 Top-2** 专家。
  - 推理采用 **DDIM-solver**，10 步去噪，输出 10 步动作块（action chunk）。

## 3. 实验设计

### 3.1 数据集与场景
- **预训练数据**：
  - 通用：Objaverse、Co3Dv2、ScanNet、Real10k（来自 MVGenMaster）。
  - **机器人中心微调数据**：RH20T 约 100 个任务子集（用 MapAnything 补深度）；RoboSuite + CoppeliaSim 仿真渲染 5000+ 相机视角，覆盖 200+ 任务。
- **下游评测基准**：
  - **LIBERO**：10 / 90 / Spatial 子集，每任务 50 条 Franka Panda 演示。
  - **MetaWorld**（MuJoCo）：50 个任务，按难度分 Easy(28) / Medium(11) / Hard & Very Hard(11)，每任务 50 条轨迹。
  - **Mv-Bench（自建）**：在 LIBERO Spatial 中绕机器人基坐标 z 轴旋转视角（-30°~60°），评测跨视角泛化。
- **真实世界**：Franka Research 3 机械臂 + RealSense D435/D455，共 8 个任务（报告其中 4 个的量化结果）。

### 3.2 对比方法
- **Transformer 类**：RT-1、MT-ACT、Baku。
- **扩散策略类**：DP、Dita、MDT。
- **VLA 类**：OpenVLA、VQ-VLA、π0.5-ki。
- **基于视觉生成的策略**：SuSIE（图像编辑扩散条件化）、GR-1（自回归视频+动作）、VPP（视频扩散预测表征）。

## 4. 资源与算力

- **硬件**：所有实验使用 **8 块 NVIDIA A100 GPU**。
- **预训练微调耗时**：约 **2 天**完成多视图扩散模型在机器人中心数据集上的微调。
- **其他细节**：所有 RGB-D 图像统一 resize 到 512×512；策略网络为 8 层 Transformer block，潜维度 768。
- **未明确披露**：未报告具体显存占用、训练 token 总数或碳排放等细节。

## 5. 实验数量与充分性

- **主结果**：
  - LIBERO 三个子集（Tab. 1，6 个对比方法）。
  - MetaWorld 50 个任务，三档难度（Tab. 2，6 个对比方法）。
- **视角泛化**：Mv-Bench 覆盖 7 个角度（-30° 到 +60°，Tab. 3）+ 定性可视化（Fig. 4）。
- **真实世界**：8 个任务，但仅 4 个（Wipe table、Return bowl、Open drawer、Pull out tissue）给出量化结果（Tab. 4）。
- **消融研究**（Tab. 5，Libero-10 上）：
  1. 移除机器人中心数据预训练；
  2. 移除 Plücker 嵌入；
  3. 移除 Q-Former 的 FiLM 语言条件；
  4. MoE 仅激活 Top-1 专家；
  5. 腕部视角（wrist view）外推能力（Fig. 6）。
- **定性展示**：真实世界多视图扩散生成结果（Fig. 7）。
- **充分性评价**：
  - **优点**：覆盖仿真 + 真实世界、多基准、消融较系统。
  - **不足**：真实世界任务量化覆盖仅 4/8；Mv-Bench 仅在 LIBERO Spatial 上构建；缺少对不同 3D 表征骨干的可视化对比（如与 SPA、3D-MVP 的直接对比）。

## 6. 主要结论与发现

- **核心结论**：
  - 在 LIBERO 与 MetaWorld 上均达到 SOTA，平均成功率分别达到 **92.2%** 与 **70.6%**。
  - 在视角偏移下相对 OpenVLA 提升近 **20%**（Mv-Bench 平均 59.2% vs 39.3%）。
  - 真实世界 4 任务平均 0.65，高于 DP (0.51) 与 OpenVLA (0.63)。
- **关键发现**：
  - **机器人中心数据微调**对策略性能至关重要（移除后从 89.2% 跌至 63.3%）。
  - **Plücker 射线**显著提升空间表征（移除后跌至 76.2%）。
  - **FiLM 语言条件**对任务相关特征聚合有效（移除后跌至 73.3%）。
  - **Top-2 MoE 专家**在效率与性能间取得最佳平衡（Top-1 时 87.7%）。
  - 模型具备良好的 **OOD 视角泛化能力**（未训练的腕部视角仍能生成有效视图）。

## 7. 优点与亮点

- **方法创新**：
  - 首次系统地将多视图扩散预训练迁移到机器人操控领域，提供新的表征学习范式。
  - **不固定视图数训练** + **无位置编码**设计，使模型对源/目标视图数具备外推灵活性。
- **工程设计**：
  - FiLM 条件 Q-Former 有效桥接预训练视觉表征与下游策略。
  - MoDE（Mixture of Denoising Experts）+ 因果自注意力兼顾推理速度与时序一致性。
  - 同一预训练模型在训练时作为特征提取器、推理时可作为视角自适应模块（dual-role 设计）。
- **实验视角**：
  - 视角泛化评测（Mv-Bench）针对既有方法的薄弱环节。
  - 仿真 + 真实世界双轨验证，并展示在未见视角（腕部）下的零样本迁移。

## 8. 不足与局限

- **方法层面**：
  - 缺乏对**动态时间信息**的显式建模，限制了对运动连续性的推理能力。
  - **视角偏移过大**时（如 ±60°）性能显著下降，源于几何遮挡（论文 Fig. 4 与 Tab. 3 中已观察到）。
  - 依赖深度信息（RGB-only 需借助 MapAnything 补深度），引入额外误差源。
- **实验层面**：
  - 真实世界仅 4/8 任务给出量化结果，覆盖面不足。
  - Mv-Bench 仅在 LIBERO Spatial 构建，未在 MetaWorld 或真实场景验证视角泛化。
  - 缺乏与最直接的 3D 感知基线（如 SPA、Lift3D、PDFactor）的**同条件对比**。
  - 未报告推理延迟、显存占用与训练总耗时等部署相关指标。
- **应用与偏差风险**：
  - 预训练微调集中在 Franka + 特定相机配置，向其他机器人本体迁移能力未验证。
  - 仿真训练的视角分布与真实世界存在差异（sim-to-real 偏差），虽有真实实验但样本量较小。
  - 大规模多视图扩散微调需 8×A100×2 天，对中小研究团队门槛较高。

（完）
