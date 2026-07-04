---
title: "G3Flow: Generative 3D Semantic Flow for Pose-aware and Generalizable Object Manipulation"
title_zh: G3Flow：面向位姿感知与可泛化物体操作的三维语义流生成
authors: "Chen, Tianxing, Mu, Yao, Liang, Zhixuan, Chen, Zanxin, Peng, Shijia, Chen, Qiangyu, Xu, Mingkun, Hu, Ruizhen, Zhang, Hongyuan, Li, Xuelong, Luo, Ping"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Chen_G3Flow_Generative_3D_Semantic_Flow_for_Pose-aware_and_Generalizable_Object_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向三维机器人操作的扩散策略模仿学习
tldr: 三维机器人操作需要同时具备几何精度与语义理解能力，而现有方法难以兼顾。本文提出G3Flow框架，结合三维生成模型、视觉基础模型与鲁棒位姿跟踪，实时构建以物体为中心的三维语义流表征。该方法在遮挡情况下仍能提供完整语义信息，且无需人工标注。该研究为基于扩散策略的模仿学习提供了更强的视觉表征基础，对提升复杂操作任务的泛化能力具有重要意义。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 801, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1721, \"height\": 1063, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 658, \"height\": 394, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 743, \"height\": 457, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 788, \"height\": 578, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 835, \"height\": 515, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 792, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 790, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1701, \"height\": 320, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 1795, \"height\": 214, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1452, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 178, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 189, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-chen-g3flow-generative-3d-semantic-flow-for-pose-aware-and-generalizable-object-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 867, \"height\": 124, \"label\": \"Table\"}]"
motivation: 现有模仿学习方法难以在三维操作中同时融合几何精度与语义理解。
method: 结合三维生成模型、视觉基础模型与位姿跟踪构建实时三维语义流。
result: 实现了遮挡下完整语义理解且无需人工标注的可泛化视觉表征。
conclusion: G3Flow为扩散策略模仿学习提供了更强的视觉表征支持。
---

## Abstract
Recent advances in imitation learning for 3D robotic manipulation have shown promising results with diffusion-based policies. However, achieving human-level dexterity requires seamless integration of geometric precision and semantic understanding. We present G3Flow, a novel framework that constructs real-time semantic flow, a dynamic, object-centric 3D semantic representation by leveraging foundation models. Our approach uniquely combines 3D generative models for digital twin creation, vision foundation models for semantic feature extraction, and robust pose tracking for continuous semantic flow updates. This integration enables complete semantic understanding even under occlusions while eliminating manual annotation requirements. By incorporating semantic flow into diffusion policies, we demonstrate significant improvements in both terminal-constrained manipulation and cross-object generalization. Extensive experiments across five simulation tasks show that G3Flow consistently outperforms existing approaches, achieving up to 68.3% and 50.1% average success rates on terminal-constrained manipulation and cross-object generalization tasks respectively. Our results demonstrate the effectiveness of G3Flow in enhancing real-time dynamic semantic feature understanding for robotic manipulation policies.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the G3Flow paper, structured according to 8 specific points. Let me carefully analyze the paper content and organize my response.

Key points to cover:
1. Core problem and motivation
2. Methodology (core idea, key technical details, formulas/algorithm flow)
3. Experimental design (datasets/scenarios, benchmarks, comparison methods)
4. Resources and compute (GPU models, count, training time)
5. Number and sufficiency of experiments
6. Main conclusions and findings
7. Strengths
8. Limitations and shortcomings

Let me organize the paper content:

**Problem**: 
- Imitation learning for 3D robotic manipulation needs both geometric precision and semantic understanding
- Image-based methods lack geometric precision
- 3D methods (point clouds, voxels) lack semantic understanding
- Existing semantic field methods (D3 Fields, GenDP) require manual keypoint selection, multi-view setup, struggle with occlusion, and lack real-time performance
- Need: dynamic, object-centric, occlusion-robust, single-view, no manual annotation

**Method - G3Flow**:
- Two phases:
  1. Initial semantic flow construction (offline):
     - Object-centric exploration: use Grounded-SAM for detection, then wrist camera multi-view observation
     - 3D model generation: use Rodin (3D generative model) to create digital twins from multi-view RGB
     - Virtual semantic flow generation: render digital twins in virtual space from multiple viewpoints, extract DINOv2 features, apply PCA to reduce dimensions (D_feat), sample K points with FPS
  2. Dynamic semantic flow maintenance (online):
     - Spatial alignment via FoundationPose
     - Transform initial semantic flow using: P^T_update = [(M_c2w · M_update)(M_c2w · M_init)^{-1}] P^T_init
- G3Flow-enhanced Diffusion Policy:
  - Three encoders: semantic features f_s, scene features f_r (real point cloud), robot state features f_p
  - Conditional denoising: a_{k-1} = ... (DDIM-like)
  - Training: MSE noise prediction loss

**Experiments**:
- 5 tasks from RoboTwin benchmark
- Single-arm: Shoe Place, Bottle Adjust, Tool Adjust
- Dual-arm: Dual Shoes Place, Diverse Bottles Pick
- 100 expert demonstrations per task
- 3 random seeds × 100 test episodes per seed
- Baselines: DP, 3D DP, 3D DP w/ color
- PCA reduces DINOv2 to 5 dimensions
- Downsample to 1024 points
- Training: 3000 epochs for G3Flow and DP3, 300 epochs for DP, batch size 256/128

**Resources**:
- Single NVIDIA GeForce RTX 4090
- G3Flow runs at 42.92 Hz field gen, 34.04 Hz decision
- Field gen freq: G3Flow 42.92 Hz vs Scene-Level DINOv2 10.52 Hz vs D3Fields 8.14 Hz
- Decision freq: G3Flow 34.04 Hz vs Scene-Level DINOv2 9.52 Hz vs D3Fields 6.89 Hz

**Results**:
- Terminal constraint tasks: G3Flow 68.3% vs 3D DP 46.2%
- Cross-object generalization: G3Flow 50.1% vs 3D DP 31.7%
- Specific gains: Shoe Place (T) 83.0% (vs 58%), Bottle Adjust (T) 82.0% (vs 74.3%)
- Dual Shoes Place (T): 24.0% (vs 13.0%)

**Ablations**:
- Quality of semantic field: scene-level features vs D3Fields vs G3Flow
- VFM replacement: CLIP, SAM, DINOv2 (DINOv2 best at 83.0%)
- Efficiency comparison

**Strengths**:
- Single-view, no manual annotation
- Occlusion-robust
- Real-time (34 Hz)
- Significant performance improvement
- Combines 3D generation + VFM + pose tracking
- Comprehensive evaluation on RoboTwin

**Limitations**:
- Only simulation (RoboTwin)
- Only 5 tasks
- 3D generative model quality may limit performance
- DINOv2 feature dimension fixed
- No real-world experiments
- Heavy dependence on foundation models
- PCA dimension choice is a hyperparameter
- The Dual Shoes Place task has relatively low success rate (24.0%)
- Doesn't handle articulated objects or multi-object interactions (mentioned as future work)

Let me write a comprehensive summary in Chinese.
</think>
# G3Flow 论文总结

## 1. 核心问题与研究动机

- **关键痛点**：三维机器人模仿学习需要同时具备**几何精度**与**语义理解**能力，但现有方法难以兼顾：
  - 二维图像方法（DP）：缺乏几何信息，精确操控和样本效率差。
  - 三维点云/体素方法（3D DP、3D Diffuser Actor）：几何信息丰富但**缺乏语义理解**，难以识别语义关键部位（如鞋头、工具手柄）。
  - 已有语义场方法（D³ Fields、GenDP）：需要**人工标注关键点**、依赖**多视角**、**遮挡下难以维持语义一致性**，且计算开销大、难以实时。
- **核心矛盾**：在位姿感知任务（如鞋子摆放、工具使用）和跨物体泛化任务中，语义信息是必要条件，但传统几何表征无法提供。

## 2. 方法论

### 2.1 整体框架（两阶段）
- **阶段一：初始语义流构建（离线）**
  - **物体中心主动探索**：用 Grounded-SAM 检测物体并获取掩码；机械臂腕部相机主动绕物体多视角采集 RGB 观测。
  - **三维数字孪生生成**：调用 Rodin 等三维生成模型从多视角 RGB 重建高质量数字孪生（可补全遮挡区域）。
  - **虚拟语义流生成**：在虚拟空间多视角渲染数字孪生 → DINOv2 提取语义特征 → PCA 降维至 D_feat（实验取 5）→ 用 FPS 采样 K=1024 个语义点云 P_init。
- **阶段二：动态语义流维护（在线/实时）**
  - **空间对齐**：用 FoundationPose 进行 6D 位姿跟踪。
  - **位姿变换公式**（核心公式）：
    - P^T_update = [(M_c2w · M_update)(M_c2w · M_init)^{-1}] · P^T_init
    - 即将虚拟空间中的语义点云通过相机到世界的变换和当前/初始位姿的相对关系，映射回真实世界物理坐标系。
  - **优势**：无需每帧重新检测、分割、提取特征，避免误差累积；位姿跟踪在遮挡下仍稳健。

### 2.2 G3Flow 增强的扩散策略
- **三种特征输入**（分别经 MLP 编码）：
  - 语义流特征 f_s：来自对齐后的语义点云 (K, 3+D_feat)。
  - 真实点云特征 f_r：(K, 3)，提供即时几何反馈。
  - 机器人状态特征 f_p：关节状态编码。
- **条件去噪过程**（DDIM 调度器）：
  - a_{k-1} = α_k(a_k − γ_k·ε_θ(a_k, k, f_s, f_r, f_p)) + σ_k·N(0, I)
- **训练损失**：标准的噪声预测 MSE 损失 L = MSE(ε, ε_θ(...))。

## 3. 实验设计

- **基准平台**：RoboTwin 仿真平台 [Mu et al., 2024]。
- **5 个任务**（图 6）：
  - 单臂：Shoe Place、Bottle Adjust、Tool Adjust。
  - 双臂：Dual Shoes Place、Diverse Bottles Pick。
- **数据规模**：每任务 100 条专家示范，3 个随机种子 × 每种子 100 条测试回合。
- **任务设置**：
  - 终端约束任务（T）：训练与测试物体几何相似，关注位姿精度。
  - 跨物体泛化任务（G）：测试集选用与训练集**几何差异大**的物体，关注泛化能力。
- **基线方法**：
  - DP（二维扩散策略）
  - 3D DP（3D Diffusion Policy）
  - 3D DP w/ color（带 RGB 颜色的 3D DP）
- **训练配置**：G3Flow 与 DP3 训练 3000 epoch，batch size 256；DP 训练 300 epoch，batch size 128。
- **数据预处理**：DINOv2 特征经 PCA 降维至 5 维；语义点云与真实点云均下采样至 1024 点。

## 4. 资源与算力

- **GPU**：单张 NVIDIA GeForce RTX 4090（用于测速）。
- **运行频率**（Table 3）：
  - G3Flow：场生成 42.92 Hz，决策 34.04 Hz。
  - Scene-Level DINOv2：10.52 Hz / 9.52 Hz。
  - D³ Fields (GenDP)：8.14 Hz / 6.89 Hz。
  - G3Flow 决策频率约为 GenDP 的 **6 倍**。
- **算力披露**：未明确给出总训练时长、GPU 小时数等细节；仅说明了推理频率与单 GPU 型号。

## 5. 实验数量与充分性

- **主实验**：5 个任务 × 2 类设置（终端约束/泛化）= 10 组对比。
- **消融实验**（3 组）：
  1. **计算效率对比**：与 Scene-Level DINOv2、D³ Fields 在场生成与决策频率上的对比。
  2. **语义场质量**：在 Shoe Place (T) 和 Dual Shoes Place (T) 上对比场景级特征、D³ Fields、G3Flow。
  3. **VFM 选择**：在 Shoe Place (T) 上替换为 CLIP、SAM、DINOv2。
- **可视化分析**：特征质量对比图（图 9）、5 任务语义流可视化（图 10）、见过的/未见过物体集（图 7、图 8）。
- **客观性评估**：
  - 每个任务均报告 3 个种子的均值与标准差，**统计意义较好**。
  - 泛化设置上明确区分 seen / unseen 物体集，避免"记忆训练物体"造成的虚高结果。
  - 不足：所有任务均在仿真环境完成，**未在真实机器人上验证**；任务数量有限（仅 5 个）；Dual Shoes Place (T) 上的绝对成功率仍偏低（24.0%）。

## 6. 主要结论与发现

- **总体性能**：
  - 终端约束任务平均成功率：**G3Flow 68.3% vs. 次优基线 46.2%**（提升约 22%）。
  - 跨物体泛化任务平均成功率：**G3Flow 50.1% vs. 次优基线 31.7%**（提升约 18.4%）。
- **关键发现**：
  - 在要求精确朝向的 Shoe Place (T) 和 Bottle Adjust (T) 上 G3Flow 提升最显著（>25%）。
  - Dual Shoes Place (T) 任务上，G3Flow 成功率近乎翻倍（24.0% vs. 13.0%）。
  - 跨类泛化（Tool Adjust G）：G3Flow 在未见过的工具类上达 70.7%，比最佳基线高 13.4%。
  - 语义流在机械臂遮挡下仍保持**完整与稳定**。
  - DINOv2 比 CLIP、SAM 更适合该任务（CLIP 偏图文对齐，SAM 关注细节而非部件级语义）。
- **结论**：基础模型驱动的实时语义流可显著提升模仿学习的位姿精度与跨物体泛化能力。

## 7. 优点 / 亮点

- **无需人工标注**：完全由基础模型自动构建，部署门槛低。
- **单视角输入即可工作**：区别于 D³ Fields、GenDP 等需要多视角的方法。
- **遮挡鲁棒**：基于位姿跟踪变换语义流，避免重复检测造成的误差累积。
- **实时性强**：决策频率 34 Hz，满足真实机器人控制需求。
- **方法设计新颖**：将 3D 生成模型（Rodin）+ 视觉基础模型（DINOv2）+ 位姿跟踪（FoundationPose）有机结合，开辟"语义流"新思路。
- **消融充分**：从计算效率、语义场质量、VFM 替换三个维度验证了设计选择的合理性。
- **可视化直观**：通过特征着色可视化清晰展示语义一致性。

## 8. 不足与局限

- **仅仿真验证**：缺乏真实机器人实验，实际传感器噪声、延迟、深度不准确等因素可能影响效果。
- **依赖基础模型质量**：3D 生成模型（Rodin）的几何/纹理重建精度是性能上限；DINOv2 特征对极端姿态变化可能不鲁棒。
- **任务范围有限**：仅 5 个任务，未涵盖铰接物体、多物体交互、长时序复杂任务（作者在结论中明确列为未来工作）。
- **绝对成功率仍偏低**：Dual Shoes Place 任务 G3Flow 也仅 24.0%，远未达到实用水平。
- **超参数依赖**：PCA 降维维度（5 维）依赖经验选择，未做敏感性分析。
- **数字孪生一次性生成**：对每个新物体需重新调用 3D 生成模型（虽然仅一次），但限制了在线快速适应能力。
- **评估场景单一**：未在仿真其他基准（如 RLBench、ManiSkill2）或不同仿真器上验证，泛化结论可能受限。
- **未给出训练时长与算力开销**：可重复性略受影响。

（完）
