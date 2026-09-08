---
title: "Real2Edit2Real: Generating Robotic Demonstrations via a 3D Control Interface"
title_zh: Real2Edit2Real：通过三维控制接口生成机器人演示数据
authors: "Zhao, Yujie, Fan, Hongwei, Chen, Di, Chen, Shengcong, Chen, Liliang, Li, Xiaoqi, Ren, Guanghui, Dong, Hao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhao_Real2Edit2Real_Generating_Robotic_Demonstrations_via_a_3D_Control_Interface_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 生成多样化机器人操作演示数据，缓解模仿学习数据采集成本问题
tldr: 本文针对机器人操作中视觉运动策略依赖大量多样化演示、且空间泛化数据采集成本高昂的问题，提出了Real2Edit2Real演示生成框架。该方法首先从多视角RGB重建度量尺度的三维场景几何，再在点云上进行深度可信的三维编辑，从而合成与二维观测保持几何一致性的新操作轨迹。这一框架有效扩展了模仿学习训练数据规模，为提升操作策略的空间泛化能力提供了低成本支持。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1795, \"height\": 814, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1776, \"height\": 714, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 376, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 864, \"height\": 529, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 863, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 388, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1612, \"height\": 1319, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1804, \"height\": 445, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 884, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-real2edit2real-generating-robotic-demonstrations-via-a-3d-control-interface-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 237, \"label\": \"Table\"}]"
motivation: 机器人操作策略鲁棒性受限，但多样化演示数据采集成本极高。
method: 基于多视角三维重建与点云编辑生成几何一致的新操作演示轨迹。
result: 为视觉运动策略模仿学习提供了低成本且多样化的演示数据增强。
conclusion: 三维编辑桥接显著提升了机器人模仿学习中的数据多样性与空间泛化能力。
---

## Abstract
Recent progress in robot learning has been driven by large-scale datasets and powerful visuomotor policy architectures, yet policy robustness remains limited by the substantial cost of collecting diverse demonstrations, particularly for spatial generalization in manipulation tasks. To reduce repetitive data collection, we present Real2Edit2Real, a framework that generates new demonstrations by bridging 3D editability with 2D visual data through a 3D control interface. Our approach first reconstructs scene geometry from multi-view RGB observations with a metric-scale 3D reconstruction model. Based on the reconstructed geometry, we perform depth-reliable 3D editing on point clouds to generate new manipulation trajectories while geometrically correcting the robot poses to recover physically consistent depth, which serves as a reliable condition for synthesizing new demonstrations. Finally, we propose a multi-conditional video generation model guided by depth as the primary control signal, together with action, edge, and ray maps, to synthesize spatially augmented multi-view manipulation videos. Experiments on four real-world manipulation tasks demonstrate that policies trained on data generated from only 1-5 source demonstrations can match or outperform those trained on 50 real-world demonstrations, improving data efficiency by up to 10-50x. Moreover, experimental results on height and texture editing demonstrate the framework's flexibility and extensibility, indicating its potential to serve as a unified data generation framework.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Real2Edit2Real: Generating Robotic Demonstrations via a 3D Control Interface". I need to follow the structured template with 8 specific points, use Markdown formatting with hierarchical headings and bullet points, and end with "（完）".

Let me carefully analyze the paper content and organize my summary:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me extract the key details:

**Core Problem:**
- Visuomotor policy learning (Diffusion Policy, VLA models like π0, π0.5) needs diverse demonstrations
- Spatial generalization is a bottleneck - need lots of data to cover spatial configurations
- Data collection is expensive and repetitive
- Existing methods: MimicGen (simulation required, asset required), Real2Render2Real (rendering gap, asset required), DemoGen (point cloud based, not compatible with 2D RGB)

**Method:**
Three main components:
1. Metric-scale geometry reconstruction - hybrid training of VGGT with real + simulated data
2. Depth-reliable spatial editing - point cloud editing with motion planning + robot pose correction
3. 3D-controlled video generation - multi-view video diffusion conditioned on depth, edges, actions, ray maps

Key technical details:
- Metric-VGGT: fine-tunes VGGT using 40K sim frames + 100K real robot data, hybrid loss
- Camera pose from sim only (precise), depth from both
- Algorithm 1: spatial editing pipeline with motion segments and skill segments
- Robot pose correction: separate arm from end-effector, use FK to re-render
- Smooth object relocation: interpolate translation and rotation
- Dual attention: intra-view + cross-view
- Training: GE-Sim based on Cosmos-Predict-2B, 7K episodes, 64 tasks from AgiBot-World

**Experiments:**
- 4 real-world tasks: Mug to Basket, Pour Water, Lift Box, Scan Barcode
- 2 VLA policies: Go-1 and π0.5
- Hardware: AgiBot Genie G1 robot, 3 RGB cameras (head, left wrist, right wrist)
- Workspace: 50cm × 40cm rectangular area
- Comparison: Real data (10, 20, 50 demos) vs Generated data (from 1, 2, 5 source demos → 200 generated)

**Compute:**
- 8 H100 GPUs
- Metric-VGGT: 150K iterations, 20 hours
- Video generation: 20K iterations, 60 hours
- Policy training: 2-4 hours
- Generation time: 48.6s for 20s, 30-FPS episode (with 8 H100 parallelization)

**Results:**
- 1 source demo + 200 gen: matches 50 real demos
- 5 source demos + 200 gen: 78.8% (Go-1), 81.3% (π0.5) vs 61.3% with 50 real
- Height editing: 80% success on unseen platform height
- Texture editing: 68% with multi-texture generated data vs 52% single texture

**Ablations:**
- Geometry reconstruction (VGGT vs Metric-VGGT)
- Robot pose correction
- Smooth object relocation

**Limitations:**
- Requires depth sensors for real data
- Limited tasks (4 only)
- Limited spatial configurations tested
- Fixed robot embodiment
- Quality depends on first frame editing for texture

Now let me write this in a clean, structured Chinese summary.
</think>
# Real2Edit2Real 论文总结

## 1. 核心问题与研究动机

- **研究背景**：近年来基于大规模数据集与 Diffusion Policy、VLA（Vision-Language-Action）等视觉运动策略架构，机器人学习取得显著进展，但策略鲁棒性严重受限于演示数据的多样性。
- **关键瓶颈**：在操作任务中，物体在空间中的随机摆放（spatial generalization）需要大量演示数据来覆盖；真实演示采集成本高、效率低。
- **现有方法的不足**：
  - MimicGen 系列依赖仿真引擎与物体资产，无法直接扩展真实演示；
  - Real2Render2Real 基于 3D Gaussian Splatting 渲染合成视频，存在视觉与物理 gap；
  - DemoGen 基于点云编辑，但仅支持 3D 策略，不能用于 2D 多视角 RGB 视频；
- **研究目标**：在不使用仿真/数字资产的前提下，从少量真实 RGB 演示出发，生成空间增强的多视角操作视频，提升下游 VLA 策略的空间泛化能力与数据效率。

## 2. 方法论

### 2.1 整体框架
Real2Edit2Real 由三个核心模块串联而成：

1. **度量尺度几何重建（Metric-VGGT）**；
2. **深度可信的空间编辑（Depth-reliable Spatial Editing）**；
3. **3D 条件控制的视频生成（3D-Controlled Video Generation）**。

整体流程公式化为：$\mathcal{O} = \{\mathcal{O}_i\}_{i=1}^{N} = \text{Real2Edit2Real}(\mathcal{O}, \mathcal{K})$，即给定源演示 $\mathcal{O}=(I, q, a)$（多视角视频、关节角、动作）与机器人运动学/相机参数 $\mathcal{K}$，输出新演示集。

### 2.2 关键技术细节

- **Metric-VGGT（混合训练）**：
  - 在 VGGT 基础上，使用 40K 仿真帧（AgiBot-DigitalWorld）+ 100K 真实带深度数据联合微调；
  - 相机位姿监督**只用仿真数据**（真实手眼标定存在机械误差），采用 L1 损失；
  - 深度监督同时使用真实（带噪声掩码过滤）与仿真（精确无噪声）数据，损失形式为 $\mathcal{L}_{\text{conf}}$；
  - 仿真数据额外提供 point map 损失；
  - 总损失：$\mathcal{L} = \lambda \mathcal{L}_{\text{camera}} + \mathcal{L}_{\text{depth}} + \mathcal{L}_{\text{pointmap}}$（$\lambda=10$）。

- **空间编辑（Algorithm 1）**：
  - 将演示分解为 motion segment（自由运动）与 skill segment（物体交互）两类；
  - 目标点云变换 $T$ 作用于物体及对应 skill 段中的机械臂末端；
  - motion 段通过 cuRobo 运动规划生成新轨迹；
  - **关键创新：机器人姿态修正（Robot Pose Correction, RPC）**——之前的编辑将整臂视为刚体，导致姿态不一致；本文用 URDF + FK 重新分割手臂/末端，仅对末端施加变换后再渲染深度，得到运动学一致的深度图。

- **3D 控制视频生成**：
  - 基于 GE-Sim（基于 Cosmos-Predict-2B）微调的 Transformer 视频生成模型；
  - **双注意力机制**：intra-view（单视角内自注意力）+ cross-view（跨视角自注意力），兼顾多视角一致性与计算效率；
  - **深度作为 3D 控制接口**：将深度图与图像 latent 拼接输入 Transformer；
  - 辅助条件：Canny 边缘（清晰边界）、动作图（动作 grounding）、光线图（多视角一致性）；
  - **Smooth Object Relocation (SOR)**：对物体位移/旋转做插值生成平滑运动轨迹，将图像编辑转化为视频生成问题。

## 3. 实验设计

- **硬件平台**：AgiBot Genie G1 人形机器人，搭载 3 个 RGB 相机（头部 + 左右手腕），工作空间为 50cm × 40cm 桌面。
- **任务设置**（4 个真实操作任务，涵盖单/双臂）：
  - Mug to Basket：单臂将杯子放入篮子；
  - Pour Water：单臂拿起水壶倒入纸杯；
  - Lift Box：双臂抬起盒子；
  - Scan Barcode：单手抓取零食 + 单手扫码器扫描。
- **基线策略**：两个 VLA 模型——Go-1（仅微调 action expert）与 π0.5（因 embodiment 不匹配需全微调）。
- **数据对比**：
  - 真实数据：10/20/50 条人工遥操作演示；
  - 生成数据：1/2/5 条源演示 → 随机物体位姿变换 → 生成 200 条扩展演示。
- **评估方式**：物体在桌面均匀随机放置，统计 20 次试验的成功率，衡量空间泛化能力。
- **扩展实验**：高度编辑（桌面 → 平台）、纹理编辑（5 种桌面颜色），以及三项消融实验（几何重建、RPC、SOR）。

## 4. 资源与算力

- **Metric-VGGT 训练**：8 张 H100 GPU，150K 次迭代，约 20 小时，学习率 2e-4（backbone 2e-5）。
- **视频生成模型训练**：8 张 H100 GPU，20K 次迭代，约 60 小时，batch size 16，学习率 1e-4。
- **策略训练**：8 张 H100 GPU，10K 迭代，2-4 小时。
- **数据生成速度**：在 8 张 H100 并行下，生成一段 20 秒、30 FPS 的视频平均耗时 48.6 秒。
- **数据来源**：AgiBot-World 数据集 7K episodes（覆盖 64 个任务）+ 内部真实数据 100K 帧。

## 5. 实验数量与充分性

- **主实验**：4 个任务 × 2 个 VLA 策略 × 3 种真实数据规模 + 3 种生成数据规模 ≈ 48 组主结果对比；
- **扩展实验**：高度泛化（1 个任务 2 种数据规模）+ 纹理泛化（5 种纹理 × 3 种数据规模）；
- **消融实验**：3 项（Metric-VGGT、RPC、SOR），均有定性可视化（图 5/6/7）；
- **生成可视化**：4 个任务的视频示例（图 8）；
- **充分性评价**：
  - **优点**：横跨多个任务与两种主流 VLA 策略，泛化能力评估较全面；
  - **不足**：每个任务仅 20 次评估试验，统计置信区间有限；物体姿态变化范围受限于桌面大小；缺少与 DemoGen、Real2Render2Real 等基线方法的同条件直接对比；扩展实验样本量较小（高度实验 5 次评估、纹理实验 10 次评估）。

## 6. 主要结论与发现

- **数据效率**：使用仅 1 条源演示生成的 200 条数据训练出的策略，其性能可与 50 条真实演示训练出的策略相当；当源演示增至 5 条时，Go-1 与 π0.5 平均成功率分别达到 78.8% 与 81.3%，比 50 条真实数据训练的 61.3% 高出 17.5% 与 20 个百分点，**数据效率提升 10-50×**。
- **空间泛化能力**：编辑生成的数据显著改善策略对新颖物体位姿的鲁棒性，且更多源演示带来更丰富的交互模式与更广的空间覆盖。
- **框架可扩展性**：
  - 高度编辑：在桌面训练、平台测试场景下，混合生成数据可将成功率从 0% 提升到 80%；
  - 纹理编辑：生成包含多纹理数据时，在 5 种桌面颜色上的平均成功率从 52%（单纹理生成）提升到 68%。
- **消融结论**：Metric-VGGT 比原始 VGGT 生成更干净、姿态更准确的点云；RPC 与 SOR 对生成视频的物理一致性与物体定位精度至关重要。

## 7. 优点与亮点

- **方法论创新**：提出以**深度作为 3D 控制接口**的桥接思路，巧妙连接 3D 可编辑性与 2D 视觉数据，避开了 Sim2Real 与 Render2Real 双重 gap；
- **机器人姿态修正（RPC）**：解决了点云编辑中将整臂视为刚体导致的运动学不一致问题，对基于视频生成的策略训练尤为关键；
- **多条件视频生成设计**：以深度为主、Canny 边缘/动作/光线图为辅的组合条件，配合 intra+cross 双注意力机制，在保证多视角一致性的同时提升计算效率；
- **VLA 兼容性强**：方法不依赖任何数字资产或仿真环境，可直接对接主流 VLA 训练流程；
- **应用场景丰富**：除物体空间位姿编辑外，框架天然支持高度、纹理等扩展编辑，具备作为统一数据生成引擎的潜力。

## 8. 不足与局限

- **任务覆盖有限**：仅 4 个桌面级操作任务，缺少长时序、移动操作、复杂接触等更具挑战性的任务；
- **评估统计强度不足**：每个测试条件仅 10-20 次试验，未给出置信区间或显著性检验，结论可能受随机性影响；
- **基线对比缺失**：未与 DemoGen、Real2Render2Real、MimicGen 等已有方法在相同硬件与任务下做 head-to-head 对比，难以判断相对优势；
- **依赖源演示质量**：生成数据的多样性受限于源演示数量与质量；当源演示较少时，交互模式可能仍不够丰富；
- **相机视角受限**：方法仅针对头/左右腕三个固定视角，未验证在更多相机或移动视角下的多视角一致性；
- **Sim2Real 训练数据偏差**：Metric-VGGT 的度量尺度精度依赖仿真数据分布，若真实场景与仿真分布差距大，性能可能下降；
- **生成视频的物理真实性**：尽管做了 RPC 和 SOR，深度可控的视频生成仍可能产生与真实物理不符的细节（如物体抓取瞬间的微小偏差），对精细接触操作可能不适用；
- **生成计算成本**：单条 20 秒演示需约 48.6 秒生成时间与 8 张 H100 算力，对大规模数据合成的成本仍不低。

（完）
