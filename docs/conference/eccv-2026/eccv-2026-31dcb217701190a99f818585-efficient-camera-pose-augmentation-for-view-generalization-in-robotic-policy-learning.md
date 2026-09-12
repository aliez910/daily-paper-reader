---
title: Efficient Camera Pose Augmentation for View Generalization in Robotic Policy Learning
title_zh: GenSplat：面向机器人策略学习视角泛化的高效相机位姿增强
authors: "Sen Wang, Huaiyi Dong, Jingyi Tian, lijiayi lijiayi, Zhuo Yang, Tongtong Cao, Anlin Chen, Shuang Wu, Sanping Zhou, Le Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4971.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向机器人操纵的视运动策略学习，提升视角泛化能力
tldr: 当前主流的二维视运动策略在新视角泛化方面存在明显缺陷，因为其依赖静态观测阻碍了在未见视角下的一致动作映射。本文提出GenSplat，一种前馈三维高斯溅射框架，通过新视角渲染促进视角泛化的策略学习。该方法采用置换等变架构从稀疏未标定输入中单次重建高保真三维场景，并通过三维先验蒸馏策略防止几何坍塌。该工作直接服务于端到端视运动学习对机器人操纵的支撑，通过视角增强提升视觉-动作映射在真实部署中的鲁棒性。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 757, \"height\": 426}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 757, \"height\": 426}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 660, \"height\": 463}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-010.webp\", \"caption\": \"\", \"page\": 2, \"index\": 10, \"width\": 354, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-011.webp\", \"caption\": \"\", \"page\": 2, \"index\": 11, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-012.webp\", \"caption\": \"\", \"page\": 2, \"index\": 12, \"width\": 371, \"height\": 371}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-013.webp\", \"caption\": \"\", \"page\": 2, \"index\": 13, \"width\": 530, \"height\": 336}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-014.webp\", \"caption\": \"\", \"page\": 6, \"index\": 14, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-015.webp\", \"caption\": \"\", \"page\": 6, \"index\": 15, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-016.webp\", \"caption\": \"\", \"page\": 6, \"index\": 16, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-017.webp\", \"caption\": \"\", \"page\": 6, \"index\": 17, \"width\": 528, \"height\": 608}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-018.webp\", \"caption\": \"\", \"page\": 6, \"index\": 18, \"width\": 528, \"height\": 608}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-019.webp\", \"caption\": \"\", \"page\": 6, \"index\": 19, \"width\": 528, \"height\": 608}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-020.webp\", \"caption\": \"\", \"page\": 6, \"index\": 20, \"width\": 528, \"height\": 608}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-021.webp\", \"caption\": \"\", \"page\": 6, \"index\": 21, \"width\": 528, \"height\": 608}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-022.webp\", \"caption\": \"\", \"page\": 6, \"index\": 22, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-023.webp\", \"caption\": \"\", \"page\": 6, \"index\": 23, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-024.webp\", \"caption\": \"\", \"page\": 6, \"index\": 24, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-025.webp\", \"caption\": \"\", \"page\": 6, \"index\": 25, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-026.webp\", \"caption\": \"\", \"page\": 6, \"index\": 26, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-027.webp\", \"caption\": \"\", \"page\": 6, \"index\": 27, \"width\": 1024, \"height\": 572}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-028.webp\", \"caption\": \"\", \"page\": 6, \"index\": 28, \"width\": 1024, \"height\": 572}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-029.webp\", \"caption\": \"\", \"page\": 6, \"index\": 29, \"width\": 1131, \"height\": 1026}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-030.webp\", \"caption\": \"\", \"page\": 9, \"index\": 30, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-031.webp\", \"caption\": \"\", \"page\": 9, \"index\": 31, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-032.webp\", \"caption\": \"\", \"page\": 9, \"index\": 32, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-033.webp\", \"caption\": \"\", \"page\": 9, \"index\": 33, \"width\": 1122, \"height\": 1122}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-034.webp\", \"caption\": \"\", \"page\": 9, \"index\": 34, \"width\": 1122, \"height\": 1122}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-035.webp\", \"caption\": \"\", \"page\": 9, \"index\": 35, \"width\": 1122, \"height\": 1122}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-036.webp\", \"caption\": \"\", \"page\": 9, \"index\": 36, \"width\": 2000, \"height\": 1500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-037.webp\", \"caption\": \"\", \"page\": 11, \"index\": 37, \"width\": 1837, \"height\": 301}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-038.webp\", \"caption\": \"\", \"page\": 11, \"index\": 38, \"width\": 1837, \"height\": 305}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-039.webp\", \"caption\": \"\", \"page\": 11, \"index\": 39, \"width\": 462, \"height\": 462}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-040.webp\", \"caption\": \"\", \"page\": 11, \"index\": 40, \"width\": 462, \"height\": 462}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-041.webp\", \"caption\": \"\", \"page\": 11, \"index\": 41, \"width\": 1024, \"height\": 576}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-042.webp\", \"caption\": \"\", \"page\": 11, \"index\": 42, \"width\": 448, \"height\": 448}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-043.webp\", \"caption\": \"\", \"page\": 11, \"index\": 43, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-044.webp\", \"caption\": \"\", \"page\": 11, \"index\": 44, \"width\": 980, \"height\": 982}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-045.webp\", \"caption\": \"\", \"page\": 13, \"index\": 45, \"width\": 1848, \"height\": 870}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-046.webp\", \"caption\": \"\", \"page\": 13, \"index\": 46, \"width\": 1848, \"height\": 870}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-31dcb217701190a99f818585/fig-047.webp\", \"caption\": \"\", \"page\": 14, \"index\": 47, \"width\": 3000, \"height\": 3000}]"
motivation: 二维视运动策略在新视角泛化方面存在缺陷，依赖静态观测阻碍了一致的动作映射。
method: 提出GenSplat前馈三维高斯溅射框架，通过新视角渲染促进策略学习的视角泛化。
result: 实现了稀疏未标定输入下高保真三维场景重建与多样化合成视图生成。
conclusion: 为视运动策略在新视角下的鲁棒部署提供了有效的视角增强方案。
---

## Abstract
Prevailing 2D-centric visuomotor policies exhibit a pronounceddeficiency in novel view generalization, as their reliance on static observa-tions hinders consistent action mapping across unseen views. In response,we introduce GenSplat, a feed-forward 3D Gaussian Splatting frameworkthat facilitates view-generalized policy learning through novel view ren-dering. GenSplat employs a permutation-equivariant architecture to re-construct high-fidelity 3D scenes from sparse, uncalibrated inputs in asingle forward pass. To ensure structural integrity, we design a 3D-priordistillation strategy that regularizes the 3DGS optimization, preventingthe geometric collapse typical of purely photometric supervision. By ren-dering diverse synthetic views from these stable 3D representations, wesystematically augment the observational manifold during training. Thisaugmentation forces the policy to ground its decisions in underlying 3Dstructures, thereby ensuring robust execution under severe spatial per-turbations where baselines severely degrade.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "GenSplat: Efficient Camera Pose Augmentation for View Generalization in Robotic Policy Learning" following a specific 8-point structure. Let me analyze the paper carefully and produce a well-structured, comprehensive summary.

Let me organize my understanding:

1. **Core problem & motivation**: 2D visuomotor policies fail to generalize to novel camera viewpoints because they're trained on static viewpoints. Even small SE(3) perturbations disrupt action mapping. Re-collecting demonstrations is expensive.

2. **Method**: GenSplat - a feed-forward 3DGS framework that:
   - Uses permutation-equivariant architecture
   - Uses DINOv2 for patch tokens
   - Aggregates via alternating intra-frame and global self-attention
   - Predicts camera poses and dense point maps
   - Uses 3D-prior distillation from a pretrained foundation model (π3 from ref 57)
   - Distills point map loss L3D and camera pose loss Lcam
   - Total loss: L = Lrgb + λdepth Ldepth + L3D-prior
   - Generates novel views via rendering from sampled camera transforms
   - Trains policy (π0 or Diffusion Policy) on expanded manifold

3. **Experiments**: 
   - Real-world Franka Research 3 + Robotiq 2F-85 gripper
   - 3 RGB cameras (2 external + 1 wrist)
   - 6 manipulation tasks: Stack Block, Pick up the Banana, Insert Ring onto Pole, Stack three Cups together, Put Blocks into the Plate, Place Can on Second Shelf
   - 100 expert demonstrations per task
   - Comparison with: ZeroNVS, VISTA, SEVA, InstantSplat, NoPoSplat, AnySplat
   - Both π0 and Diffusion Policy

4. **Resources**: 
   - Pretrained on DROID dataset (271k training images, 1 fps subsampling)
   - 30k iterations, batch size 16
   - Learning rate 2e-4 with cosine annealing, 1k warmup
   - Uses FlashAttention, gradient checkpointing, bfloat16
   - Doesn't specify GPU type/number explicitly in extracted text
   - Synthesis speed: 0.14s/frame

5. **Experimental thoroughness**:
   - RQ1: Robustness to camera perturbations (small/medium/large)
   - RQ2: Comparison with SOTA (rendering quality, policy performance, efficiency)
   - RQ3: Ablation of 3D-prior distillation and P.E. architecture
   - RQ4: Impact of number of rendered views (N=1,2,3,4)
   - Each task evaluated 30 episodes (some 50)
   - Multiple tasks, multiple perturbations, multiple baselines - reasonably comprehensive

6. **Conclusions**: GenSplat enables view generalization for visuomotor policies via NVS-based data augmentation, achieving 62.2% average success rate, +6.7-13.3% relative improvement across perturbation levels.

7. **Highlights**: 
   - Feed-forward (no per-scene optimization)
   - No calibration required
   - Pose-free
   - 3D-prior distillation prevents geometric collapse
   - High efficiency (0.14s/frame)
   - Architecture-agnostic (works with π0 and DP)
   - Point maps rather than depth for better topology

8. **Limitations**:
   - Real-world only, no simulation benchmarks
   - Limited to 6 tasks
   - 100 demos per task
   - Doesn't address dynamic wrist-camera fully
   - Limited view angle range (max 60° in extreme)
   - Only tested on Franka arm
   - No discussion of generalization to different embodiments

Let me write this up in Chinese.</think>

# GenSplat 论文总结

## 1. 核心问题与研究动机

- **核心问题**：当前主流的二维视觉-运动策略（如 π0、Diffusion Policy）在**新视角泛化（Novel View Generalization）**方面存在严重缺陷。由于这些策略学习的是"从静态观测到动作"的映射，对相机外参高度敏感——即使轻微的 SE(3) 扰动（旋转/平移）也会破坏动作相关线索的空间对齐，导致策略部署失败。
- **数据瓶颈**：通过重新采集人类示教来覆盖未见视角的方式边际成本极高（需重复远程操控演示），难以规模化扩展至真实部署。
- **科学问题**：如何在不增加人工数据采集成本的前提下，**扩展观测流形（observational manifold）**，从而诱导策略获得视角泛化能力？

## 2. 方法论

### 2.1 整体框架
- 提出 **GenSplat**：一种前馈式 3D 高斯溅射（Feed-forward 3DGS）框架，从**稀疏、未标定**的输入中单次前向重建高保真 3D 场景，并基于此渲染几何一致的新视角。
- 通过将原始数据集 $D$ 与合成增强集 $\tilde{D}$ 合并，得到 $\mathcal{D}_{\text{train}} = D \cup \tilde{D}$，在 π0 与 Diffusion Policy 上训练视角泛化的策略。

### 2.2 关键技术细节
- **置换等变架构（Permutation-Equivariant）**：使用 DINOv2 提取 patch tokens $\{h_i\}$，通过**交替的帧内与全局自注意力**层聚合多视角上下文，确保输入顺序不敏感；同时预测相机姿态 $p_i = (R_i, T_i) \in SE(3)$ 与稠密 3D 点图 $P_i$。
- **高斯参数解耦预测**：
  - 空间中心：$\mu_g = R_i P_i + T_i$（基于点图而非深度图，保留局部度量结构）
  - 渲染属性（不透明度 $\sigma_g$、旋转四元数 $r_g$、各向异性尺度 $s_g$、球谐系数 $c_g$）：通过 DPT 头融合深部等变 token 与浅层 RGB 特征回归。
- **3D 先验蒸馏（核心创新）**：从预训练 3D 视觉几何基础模型 π3 [57] 中蒸馏几何知识，避免纯光度监督导致的浮游物（floater）和边界撕裂。
  - 点图损失：$\mathcal{L}_{3D} = \frac{1}{HW}\sum_{u,v}\|\hat{P}(u,v) - P(u,v)\|_2^2$
  - 相机姿态损失：旋转用 SO(3) 测地距离 $\ell_{\text{rot}}$，平移用 Huber 损失 $\mathcal{H}_\delta$
  - 总蒸馏损失：$\mathcal{L}_{\text{3D-prior}} = \lambda_{3D}\mathcal{L}_{3D} + \lambda_{\text{cam}}\mathcal{L}_{\text{cam}}$
- **总训练目标**：$\mathcal{L} = \mathcal{L}_{\text{rgb}} + \lambda_{\text{depth}}\mathcal{L}_{\text{depth}} + \mathcal{L}_{\text{3D-prior}}$，其中 $\mathcal{L}_{\text{rgb}}$ 包含 ℓ1 + LPIPS 项，$\mathcal{L}_{\text{depth}}$ 强制渲染深度与点图 z 分量对齐。

## 3. 实验设计

### 3.1 实验平台
- **硬件**：7 自由度 Franka Research 3 机械臂 + Robotiq 2F-85 夹爪；3 个 RGB 摄像头（2 个外部 + 1 个腕部）。
- **任务**：6 个真实操作任务——Stack Block、Pick up the Banana、Insert Ring onto Pole、Stack three Cups together、Put Blocks into the Plate、Place Can on Second Shelf。
- **数据**：每任务通过远程操作采集 100 条专家示教，物体位置与颜色系统变化以保证多样性。

### 3.2 对比方法
- **基于扩散的 NVS**：ZeroNVS、VISTA、SEVA
- **基于高斯的 NVS**：InstantSplat、NoPoSplat、AnySplat
- **策略架构**：π0 与 Diffusion Policy

### 3.3 评估维度（4 个研究问题）
- **RQ1**：抗相机扰动鲁棒性（Small/Medium/Large 三档扰动）
- **RQ2**：渲染质量、策略性能与合成效率综合对比
- **RQ3**：3D 先验蒸馏与置换等变架构的消融
- **RQ4**：合成视角数 $N \in \{1,2,3,4\}$ 对泛化的影响

## 4. 资源与算力

- **预训练数据集**：DROID（公开大规模机器人数据集），按 1 帧/秒时间下采样得 271k 训练图像。
- **训练配置**：30k 迭代，batch size 16，余弦退火学习率（峰值 2e−4，1k 步 warmup），启用 FlashAttention、梯度检查点、bfloat16 精度；π3 初始化部分采用基础学习率的 0.1×。
- **合成速度**：0.14 秒/帧（在统一硬件上对比），SEVA 为 50.00 秒、InstantSplat 为 85.20 秒。
- **未明确说明**：具体的 GPU 型号与数量、每张显卡的显存占用、真实硬件采集阶段的工时等。

## 5. 实验数量与充分性

- **真实实验量**：每任务在每档扰动下评估 30 条回合（部分实验 50 条），6 个任务 × 3 档扰动 × 多种方法，实验量较为充实。
- **消融**：分别去除置换等变架构与 3D 先验蒸馏，验证各组件贡献。
- **视角数扫描**：$N = 1 \sim 4$，得到饱和曲线与几何解释。
- **充分性评价**：实验覆盖多视角扰动、多基线、多策略架构，结论具备一定普适性。但**所有评估均在单一真实平台、单一机械臂型号上进行**，且未在仿真基准（如 RLBench、ManiSkill2、Colosseum 等）做交叉验证，外部效度有限。

## 6. 主要结论与发现

- 在 Large 扰动下，GenSplat 使 π0 平均成功率从基线 48.9% 提升至 **62.2%**，绝对增益 +13.3%。
- 跨 6 任务聚合，相对提升为：**Small +6.7%、Medium +8.9%、Large +13.3%**；DP 在 Large 扰动下相对提升高达 **56.0%**（27.78% → 43.33%）。
- 与最近的 AnySplat 相比，绝对增益 +6.1%；且合成速度（0.14s）远快于 SEVA/InstantSplat。
- 仅添加 1 个增强视角即可带来最大性能跃升，$N = 3$ 后收益趋于饱和。
- **关键发现**：低质量 NVS 数据增强可能**损害**策略学习（如 VISTA 37.8% < Baseline 48.9%、NoPoSplat 36.7% < Baseline 48.9%）；几何一致性是增强有效性的前提。

## 7. 优点与亮点

- **架构无关性**：可即插即用地应用于 π0 与 Diffusion Policy，无需修改策略本身。
- **免标定、稀疏输入适用**：适配真实机器人数据的稀疏与未标定特性，规避传统 3DGS 的密集视角与精确外参依赖。
- **3D 先验蒸馏设计精巧**：用点图（而非深度图）作为监督信号，缓解边界撕裂与平面重建崩塌。
- **置换等变架构**：从根本上避免参考视角选择带来的顺序敏感性。
- **效率与质量兼顾**：0.14s/帧的合成速度与 SOTA 几何一致性同时达成。
- **视角增强的可解释性**：图 9 直观展示流形从稀疏到球面密集的扩展过程。

## 8. 不足与局限

- **平台单一性**：仅在 Franka Research 3 + 3 个 RGB 摄像头的单一设置下验证，跨平台泛化未知。
- **任务规模有限**：仅 6 个桌面级操作任务，未涉及移动操作、长序列任务或动态场景。
- **缺失仿真基准**：未在 RLBench、SimplerEnv、Colosseum 等仿真 benchmark 上做受控对比，无法隔离真实世界噪声影响。
- **算力信息不全**：GPU 型号、数量、训练总时长、推理硬件均未明确披露，复现成本难以估算。
- **腕部相机利用不足**：当前主要依赖两个外部相机，腕部视角在主动操作中的细粒度遮挡几何尚未充分探索（作者在结论中列为未来工作）。
- **扰动范围受限**：极端扰动仅达 60°/12cm，对真实部署中可能出现的剧烈视角变化覆盖不够。
- **数据规模**：每任务仅 100 条示教，在更大规模数据集（如 Open X-Embodiment）下的可扩展性未验证。
- **生成视角的单一性**：每条原始演示仅采样一组扰动 $(\theta, \mu)$，未考虑更复杂的多样化轨迹增强策略。

（完）
