---
title: Learning Surgical Robotic Manipulation with 3D Spatial Priors
title_zh: 基于三维空间先验的手术机器人操作学习
authors: "Sheng, Yu, Wang, Lidian, Chu, Xiaomeng, Deng, Jiajun, Cheng, Min, Zhang, Yanyong, Hua, Bei, Li, Houqiang, Ji, Jianmin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Sheng_Learning_Surgical_Robotic_Manipulation_with_3D_Spatial_Priors_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向手术机器人操作的端到端视觉运动策略与三维空间先验
tldr: 精确的三维空间感知能力对手术机器人操作至关重要。然而现有方法要么依赖多阶段场景重建导致误差累积，要么需要腕部摄像头辅助但干扰临床操作。为此，本文提出 Spatial Surgical Transformer（SST），一种面向手术机器人的端到端视觉运动策略，通过引入三维空间先验赋予机器人直接的空间感知能力。该方法避免了多阶段误差累积并支持端到端优化，为精细手术操作提供了新的可行技术路径。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1693, \"height\": 596, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1805, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1810, \"height\": 349, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1771, \"height\": 728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1815, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 822, \"height\": 355, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 173, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1796, \"height\": 300, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-sheng-learning-surgical-robotic-manipulation-with-3d-spatial-priors-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 229, \"label\": \"Table\"}]"
motivation: 手术机器人需要精确的三维空间感知，而现有方法存在误差累积或临床干扰问题。
method: 提出端到端视觉运动策略 SST，将三维空间先验融入网络以赋能手术机器人。
result: 在精细手术操作任务上实现了端到端优化并避免多阶段误差累积。
conclusion: 为三维空间感知驱动的手术机器人操作提供了新的端到端解决方案。
---

## Abstract
Achieving 3D spatial awareness is crucial for surgical robotic manipulation, where precise and delicate operations are required. Existing methods either explicitly reconstruct the surgical scene prior to manipulation, or enhance multi-view features by adding wrist-mounted cameras to supplement the default stereo endoscopes. However, both paradigms suffer from notable limitations: the former easily leads to error accumulation and prevents end-to-end optimization due to its multi-stage nature, while the latter is rarely adopted in clinical practice since wrist-mounted cameras can interfere with the motion of surgical robot arms. In this work, we introduce the Spatial Surgical Transformer (SST), an end-to-end visuomotor policy that empowers surgical robots with 3D spatial awareness by directly exploring 3D spatial cues embedded in endoscopic images. First, we build Surgical3D, a large-scale photorealistic dataset containing 30K stereo endoscopic image pairs with accurate 3D geometry, addressing the scarcity of 3D data in surgical scenes. Based on Surgical3D, we finetune a powerful geometric transformer to extract robust 3D latent representations from stereo endoscopes images. These representations are then seamlessly aligned with the robot's action space via a lightweight multi-level spatial feature connector (MSFC), all within an endoscope-centric coordinate frame. Extensive real-robot experiments demonstrate that SST achieves state-of-the-art performance and strong spatial generalization on complex surgical tasks such as knot tying and ex-vivo organ dissection, representing a significant step toward practical clinical deployment. The dataset and code will be released.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Learning Surgical Robotic Manipulation with 3D Spatial Priors" organized according to 8 specific points. Let me analyze the paper carefully and produce a structured Markdown summary.

Let me go through each section:

1. **Core problem and motivation**: The paper addresses 3D spatial awareness for surgical robotic manipulation. Existing methods either do explicit multi-stage reconstruction (error accumulation, no end-to-end optimization) or use wrist cameras (impractical due to trocar constraints). The goal is to enable millimeter-level precision surgical operations.

2. **Methodology**:
   - Spatial Surgical Transformer (SST) - end-to-end visuomotor policy
   - Surgical3D dataset - 30K synthetic stereo endoscopic image pairs with 3D ground truth, built with NVIDIA Omniverse
   - Geometry Transformer - MASt3R finetuned on Surgical3D for 3D latent embeddings
   - Multi-Level Spatial Feature Connector (MSFC) - aggregates embeddings from 4 decoder layers
   - Endoscope-centric action space - relative pose representation
   - Policy decoder - 12 transformer blocks with self/cross attention, uses ACT framework with action chunking (k=100) and exponential weighting (m=0.1)
   - Loss functions: regression loss with scale normalization, confidence-aware loss

3. **Experiments**:
   - Torin surgical robot deployed
   - Three tasks: Peg pickup, knot tying, ex-vivo gallbladder dissection
   - 180 trajectories for peg pickup, 200 for knot tying, 200 for gallbladder
   - Compared with SRT (with wrist cameras), ACT, Diffusion Policy (without wrist cameras)
   - 10 trials per task
   - Training: 100 epochs

4. **Resources**:
   - RTX-4090 mentioned for latency testing
   - MASt3R: 56.2ms latency
   - VGGT: 140.4ms latency
   - No specific training time, GPU count, or other compute details mentioned

5. **Experiment count and adequacy**:
   - Main results table (3 tasks, multiple methods)
   - Spatial generalization analysis
   - Robustness of 3D latent embeddings analysis
   - Ablation: Finetuning on Surgical3D (Table 2)
   - Ablation: Efficiency (MASt3R vs VGGT)
   - Ablation: MSFC variants (LFC, MSC, MSFC) - Table 3
   - 10 trials per task - relatively limited but standard for real-robot experiments
   - Evaluation in two test regions for peg pickup

6. **Conclusions**:
   - SST achieves SOTA without wrist cameras
   - Strong spatial generalization
   - Robust 3D embeddings transfer across unseen scenes
   - Validates importance of 3D priors for surgical robots

7. **Strengths**:
   - First large-scale 3D surgical dataset (Surgical3D)
   - End-to-end design without extra hardware
   - MASt3R selected over VGGT for real-time deployment
   - MSFC effective for fusing multi-level features
   - Hybrid training (synthetic + pseudo-labeled real data) addresses domain gap
   - Tested on real organs (ex-vivo) - high practical relevance
   - Multiple ablation studies

8. **Limitations**:
   - 10 trials per evaluation is relatively limited
   - No public benchmark exists, comparison may not be fully standardized
   - Synthetic data only - some domain gap remains
   - Three tasks, although diverse, may not cover all surgical scenarios
   - Reliance on specific robot platform (Torin)
   - Comparison with SRT in gallbladder task was excluded (wrist camera damage)
   - Limited failure mode analysis
   - No statistical significance testing
   - Action space limited to 7 DOF per arm
   - Pseudo-labels for real data may introduce noise

Let me now write the structured summary in Chinese.</think>

# 论文总结：基于三维空间先验的手术机器人操作学习

## 1. 核心问题与研究背景

手术机器人（如达芬奇系统）的自主操作要求毫米级精度，必须具备可靠的 **3D 空间感知能力**。现有方法存在两大瓶颈：

- **显式多阶段重建路线**：先通过 SfM/NeRF/3DGS 等方法重建 3D 场景，再在其上学习操控策略。该管线存在误差累积，且难以端到端优化。
- **腕部摄像头补充方案**（如 SRT 系列）：在患者侧机械臂（PSM）末端加装相机以提供多视角信息。然而套管针（Trocar）对 PSM 插入路径施加严格空间约束，腕部摄像头会干扰实际临床操作；且无 3D 监督时多视图特征难以捕获有意义的几何线索。

**研究目标**：构建一种仅依赖手术机器人原有立体内窥镜（ECM）、端到端可训练、并能为机器人提供稳健 3D 空间先验的视觉运动策略。

---

## 2. 方法论

### 2.1 整体框架（Spatial Surgical Transformer, SST）

SST 包含三个核心组件：
1. **几何 Transformer（Geometry Transformer）**：从立体内窥镜图像中提取 3D 潜空间嵌入。
2. **多层级空间特征连接器（MSFC）**：聚合多层级 3D 特征并对齐到动作空间。
3. **内窥镜中心策略解码器（Endoscope-Centric Policy Decoder）**：在内窥镜坐标系下预测相对动作。

### 2.2 Surgical3D 数据集

- 基于 **NVIDIA Omniverse** 构建的大规模合成手术场景数据集。
- **3 万对**（30K）高分辨率（1920×1080）立体内窥镜图像，含精确深度图、点云、相机内外参标注。
- 资产组成：开源人体器官模型（8 类）+ 手术器械 + 利用 iPad 扫描的真实器官网格（10 种）。
- 通过 **域随机化**（基线、内参、外参、光照、组织纹理变化）增强多样性。
- 为弥合合成—真实差距，对无标注真实数据利用在合成数据上微调的 VGGT 点预测头推理伪标签，仅保留高置信度区域，形成 **合成 + 伪标注真实数据** 的混合训练集。

### 2.3 手术几何 Transformer

- 选用 **MASt3R**（基于 ViT 的前馈 3D 重建模型）作为基础结构。
- 输入立体图像 → Patch 化 → 共享编码器 → ViT 解码器（跨视图跨注意力）→ DPT 头回归稠密点图。
- **损失函数**：使用尺度归一化回归损失 + 置信度感知损失。
  - 回归损失：$\mathcal{L}_{reg}(v,i) = \sum_{i \in D_v} \| \frac{1}{z}\mathbf{X}_{v,1}^i - \frac{1}{\hat{z}}\hat{\mathbf{X}}_{v,1}^i \|$
  - 置信度损失：$\mathcal{L}_{conf} = \sum C_{v,1}^i \mathcal{L}_{reg}(v,i) - \alpha \log C_{v,1}$
- **为何选 MASt3R 而非 VGGT**：MASt3R 更轻量（56.2 ms vs 140.4 ms），可实时部署；VGGT 推理低于 10 Hz 会引起运动抖动。
- ViT-Large，patch size = 16，使用 MASt3R 预训练权重初始化。

### 2.4 多层级空间特征连接器（MSFC）

- 提取解码器中 **4 个层级**（与 DPT 头对应的层）的潜空间嵌入。
- 各层嵌入先降维 → 沿特征维度拼接 → 通过轻量 MLP 对齐到动作空间 → 与位置编码进行跨注意力。
- 设计动机：低层编码细粒度局部细节，高层编码全局上下文，对精密手术操控同时需要两者。

### 2.5 内窥镜中心策略解码器

- **动作空间**：相对位姿表示 $\mathbf{a}_t = \{\mathbf{E}_{t+1} \ominus \mathbf{E}_t\}$，旋转差用欧拉角表示；夹爪用绝对角度。每臂 7 维（3 平移 + 3 旋转 + 1 夹爪）。
- 全部动作在内窥镜坐标系下表示，避免正运动学不准的问题。
- 解码器为 **12 层 Transformer 块**，含自注意力和跨注意力。
- 采用 **ACT（Action Chunk Transformer）框架**：预测未来 k=100 个动作，执行时通过指数加权 $w_i = \exp(-m \cdot i)$（m=0.1）平滑平均，减少抖动。
- 损失函数为 MSE：$\mathcal{L}_{MSE} = \text{MSE}(\hat{a}_t, \pi_\theta(o_t, x_t))$。

---

## 3. 实验设计

### 3.1 硬件平台
- **Torin 手术机器人**（Tuodao Medical），配置：1 个立体 ECM + 2 个 PSM。
- 推理延迟测试在 **RTX 4090** 单卡上完成。

### 3.2 任务设置（三个真实手术场景）
| 任务 | 数据量 | 场景特点 |
|------|--------|----------|
| Peg Pickup（取钉） | 180 条轨迹 | 硅胶肝模型，分绿色训练区 + 蓝色测试区 |
| Knot Tying（打结） | 200 条轨迹 | 圆顶模拟腹腔，分抓取 + 环绕两个子任务 |
| Ex-vivo Gallbladder Dissection（胆囊剥离） | 200 条轨迹 | 真实离体器官，需抓取+切割 |

### 3.3 对比方法
- **SRT**（带腕部摄像头）
- **ACT**（无腕部摄像头）
- **Diffusion Policy (DP)**（无腕部摄像头）
- **SST（本文，无腕部摄像头）**

### 3.4 评估协议
- 每种方法训练 100 epoch，最终 checkpoint 评估。
- 每任务 **10 次独立试验**。

---

## 4. 资源与算力

- **GPU 型号**：RTX 4090（仅在几何 Transformer 延迟测试时明确提及）。
- **延迟数据**：
  - MASt3R：56.2 ms（≈17.8 Hz）
  - VGGT：140.4 ms（≈7.1 Hz）
- **未明确说明**：训练时长、GPU 数量、显存占用、数据预处理耗时等。论文在算力披露上较为有限。

---

## 5. 实验数量与充分性

- **主要结果**（表 1）：4 种方法 × 3 个任务（含子任务）共约 11 列指标对比。
- **空间泛化分析**：Peg Pickup 设置 Test1（绿色区）和 Test2（蓝色区，含深度变化）。
- **3D 嵌入鲁棒性分析**：跨未见场景定性可视化（图 5）。
- **消融实验**：
  - 几何 Transformer 是否在 Surgical3D 上微调（表 2）。
  - 几何 Transformer 选型对比（MASt3R vs VGGT 的延迟）。
  - 空间连接器变体对比（表 3）：LFC（最后一层） / MSC（多层独立） / MSFC（多层融合）。
- **充分性评价**：消融维度较完整（数据集、连接器、模型选型），但每任务仅 10 次试验，样本量较小；缺乏统计显著性检验（如置信区间、显著性 p 值）。

---

## 6. 主要结论与发现

1. SST 在所有任务上达到与 SRT（带腕部摄像头）相当甚至更优的性能，且**仅依赖立体内窥镜**，临床实用性更强。
2. 在复杂任务（Ex-vivo 胆囊剥离）上，SST 是唯一成功的方法（6/10），ACT 和 DP 全部失败（0/10）。
3. SST 表现出**优秀的空间泛化能力**：在 Test2 大范围+深度变化区域仍能定位目标（8/10），而 ACT（2/10）和 DP（1/10）显著退化。
4. 在 Surgical3D 上微调几何 Transformer **显著提升**真实场景的 3D 重建精度（Acc 0.0048 vs 0.0111；Comp 0.0064 vs 0.0140）。
5. **MASt3R 比 VGGT 更适合实时部署**：推理速度快约 2.5×，避免运动抖动。
6. **MSFC 优于 LFC 和 MSC**：融合多层 3D 嵌入比仅用最后一层或独立处理各层更有效。

---

## 7. 优点与亮点

- **首个大规模手术场景 3D 数据集**（Surgical3D，30K），填补了手术 3D 标注数据空白。
- **端到端架构**：消除多阶段误差累积，简化部署流程。
- **临床实用性**：不依赖腕部摄像头，符合真实手术场景硬件约束。
- **混合训练策略**：合成数据 + 伪标注真实数据，有效缩小域差距。
- **几何 Transformer 选型基于实际指标**：延迟数据明确支撑了 MASt3R 而非 VGGT 的选择。
- **多层特征融合设计**：MSFC 兼顾细粒度几何与全局上下文。
- **跨域泛化能力**：在未见过的真实器官上仍能保持稳定表现。
- **包含 Ex-vivo 真实器官实验**：比纯硅胶模型更接近临床。

---

## 8. 不足与局限

1. **试验样本量较小**：每任务仅 10 次试验，缺乏统计显著性检验和置信区间，结果波动性可能未充分体现。
2. **缺乏公开 benchmark**：自定义任务设置使得与文献方法对比难以完全标准化。
3. **数据集为合成**：尽管有伪标注真实数据补充，但合成—真实差距不可能完全消除。
4. **任务覆盖有限**：仅 3 类任务，未覆盖缝合、超声刀切割、软组织形变等更具挑战性的操作。
5. **平台依赖性强**：仅在 Torin 机器人上验证，迁移到其他系统（如达芬奇）的可行性未知。
6. **SRT 在胆囊任务上被排除**（腕部摄像头易被液体损坏），导致该任务缺少直接对比。
7. **缺乏失败案例分析**：未深入讨论失败模式与边界条件。
9. **算力披露不完整**：训练时长、GPU 数量等关键信息缺失。
10. **数据集与代码虽承诺开源，但截至发表尚未公开**，影响复现性。
11. **未探索动作空间扩展**：仅 7 维/臂，未涵盖力反馈、阻抗控制等临床常用模式。

（完）
