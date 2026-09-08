---
title: "EgoRoC: Towards Egocentric Robotic Control via Task-Agnostic Visual Alignment"
title_zh: "EgoRoC:基于任务无关视觉对齐的自我中心机器人控制"
authors: "Feng, Wei, Zhang, Chi, Li, Nan, Zhang, Qian, Zhang, Qi, Li, Mingyan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Feng_EgoRoC_Towards_Egocentric_Robotic_Control_via_Task-Agnostic_Visual_Alignment_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向VLA视觉-动作映射的任务无关视觉对齐
tldr: "现有视觉-语言-动作模型将视觉理解与任务特定动作耦合,导致硬件与任务间泛化能力受限。本文提出EgoRoC,即插即用的第一人称视觉对齐头,解耦机器人感知与动作,仅暴露6自由度位姿接口。该任务无关的腕部视角一致性表征提升了VLA的跨平台泛化能力,为通用视觉-动作模型与端到端视觉运动学习提供了新的模块化基础。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 659, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1782, \"height\": 652, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 423, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1808, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1784, \"height\": 356, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 209, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 219, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 877, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 684, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 679, \"height\": 201, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-feng-egoroc-towards-egocentric-robotic-control-via-task-agnostic-visual-alignment-cvpr-2026-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 870, \"height\": 203, \"label\": \"Table\"}]"
motivation: "现有VLA模型将视觉理解与任务特定动作耦合,导致跨硬件与跨任务泛化差。"
method: "提出可插拔的EgoRoC自我中心对齐头,解耦感知与动作并暴露6自由度位姿接口。"
result: 在不同硬件与任务上提升了VLA系统的视角一致性与泛化能力。
conclusion: 为通用视觉-动作机器人系统提供了一种任务无关的视觉对齐模块化方案。
---

## Abstract
Recent Vision-Language-Action (VLA) models map visual-textual inputs to robotic actions via end-to-end architectures, yet this approach entangles visual understanding with task-specific actions. This leads to an exhaustive collection of full operational sequences and parameter redundancy across tasks, while generic third-person camera setups require fine-tuning for different hardware due to implicit hand-eye assumptions. We argue that decoupling how robots see from how robots act is a missing primitive in VLA systems. We present EgoRoC, a plug-and-play egocentric alignment head that precedes any task policy and exposes only a thin 6-DoF pose interface. EgoRoC establishes task-agnostic viewpoint consistency from a wrist-mounted (first-person) camera and then alternates alignment with manipulation, while a diffusion-based online hand-eye module corrects the action in the end-effector frame for hardware-agnostic deployment. Trained once from static wrist-target image pairs with relative poses, rather than full manipulation trajectories, EgoRoC leaves downstream VLAs unchanged. By turning egocentric alignment into a reusable capability, EgoRoC reduces training redundancy, strengthens zero-shot cross-scene transfer, and scales across VLA backbones without manual calibration. Across simulation and real settings, attaching EgoRoC consistently boosts success rates, especially on long-horizon and out-of-distribution tasks, and improves data efficiency during fine-tuning.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "EgoRoC: Towards Egocentric Robotic Control via Task-Agnostic Visual Alignment" following a specific structure. Let me analyze the paper carefully and organize the content according to the 8 required points.

Let me go through the paper systematically:

1. **Core Problem & Motivation**: Current VLA models entangle visual understanding with task-specific actions, leading to:
   - Need for full operation sequences per task
   - Parameter redundancy across tasks
   - Third-person camera setups require fine-tuning for different hardware due to implicit hand-eye assumptions
   - Lack of decoupling between "how robots see" and "how robots act"

2. **Methodology**: 
   - EgoRoC: plug-and-play egocentric alignment head
   - Two main modules:
     - EVAM (Egocentric Visual Alignment Module): Predicts 6-DoF relative transform from wrist camera to align with target view
     - DHCM (Diffusion-based Hand-Eye Calibration Module): Corrects action in end-effector frame
   - Uses Qwen2.5-VL-7B as backbone with LoRA
   - Alternates ⟨alignment → manipulation⟩ per subgoal
   - Trained from static image pairs with relative poses

3. **Experiments**:
   - Datasets: BridgeData, DROID (from Open X-Embodiment), 2.3M image pairs from 60k episodes
   - Baselines: OpenVLA, TinyVLA, SpatialVLA, Pi-0, OpenVLA-OFT
   - Tasks: Task-L (Lift), Task-Po (Put onto), Task-PA (Put all), Task-PD (Put in drawer)
   - Short and long-horizon tasks
   - Simulation: NVIDIA Isaac Sim with Franka Emika Panda
   - Real world: UMS Eco-bot with MOKOSE 4K third-view and US858 wrist-mounted camera

4. **Resources/Compute**: 
   - Used DeepSpeed ZeRO-2 optimization
   - EVAM: AdamW, lr 10^-5, LoRA rank 64, 17 epochs
   - DHCM: Adam, lr 10^-4, batch size 1024, 50000 steps, diffusion steps 10
   - No specific GPU count mentioned

5. **Experiment Volume**: Multiple experiments including:
   - Out-of-domain generalization (simulation + real)
   - Data-efficient fine-tuning
   - Ablation studies (hand-eye calibration, grid matching, Rank-N-Contrast, diffusion process, Geo-MLP)
   - Adaptable plug-and-play evaluation

6. **Conclusions**: Consistent gains, especially in long-horizon and OOD tasks, better zero-shot transfer, more data-efficient fine-tuning

7. **Strengths**:
   - Novel decoupling of perception and action
   - Plug-and-play with no architectural changes
   - Data-efficient training from static image pairs
   - Online hand-eye calibration without CAD/markers
   - Hardware-agnostic deployment

8. **Limitations**:
   - Reliance on static image pairs may limit handling of highly dynamic environments
   - No temporal alignment
   - Latency concerns in real-time applications
   - Only uses third-person camera rendering for target views

Let me now compose a comprehensive Chinese summary.</think>

# EgoRoC 论文总结

## 一、核心问题与研究动机

**核心问题**：现有 Vision-Language-Action（VLA）模型（如 OpenVLA、RT-2、π0）以端到端方式将视觉-语言输入直接映射到机器人动作，导致以下关键缺陷：

- **感知-动作耦合**：视觉理解与任务特定的动作策略深度耦合，新任务需同时重训练感知与控制模块，参数与数据存在大量跨任务冗余。
- **数据成本高**：需要为每个任务采集完整的操作轨迹（如 RT-2 需 560K、OpenVLA 需 970K 数据）。
- **硬件依赖强**：第三人称相机-机械臂之间的隐式手眼关系使模型在迁移到不同硬件时必须重新微调。
- **缺乏可复用原语**：VLA 缺少"先看后做"的视觉对齐模块，泛化与零样本迁移能力受限。

**整体含义**：论文主张应将"机器人如何看（视觉对齐）"与"机器人如何做（任务执行）"解耦，使视觉对齐成为可复用的前置模块。

---

## 二、方法论

### 核心思想
提出 **EgoRoC**，一个即插即用（plug-and-play）的自我中心（egocentric）视觉对齐头，通过薄 6-DoF 位姿接口接入任何 VLA，不改变下游策略架构。

### 关键技术组成（两个模块）

**1. 自我中心视觉对齐模块（EVAM）**
- **输入**：语言指令、腕部相机当前图像 I_cur、任务相关目标图像 I_tar
- **目标**：输出 6-DoF 相对变换 A ∈ SE(3) 与对齐状态 token（aligning / aligned / searching）
- **目标图像生成**：利用 LMM（Qwen2.5-VL-7B）解析任务子目标序列，使用 VGGT 构建点云图并从第三人称视角渲染顶视图序列（pix2pix-turbo + Gemini 2.5 Flash Image 蒸馏）
- **动作离散化**：按百分位分桶（1%-99%）将连续位姿离散为 256 个 token/维度
- **训练**：仅微调 LoRA 适配器（视觉编码器、多模态投影层、部分 Transformer 层），主干冻结

**2. 扩散式在线手眼标定模块（DHCM）**
- **目标**：将 EVAM 输出转换并校正到末端执行器坐标系
- **标定表示 X ∈ SE(3) 用 4 个点 P={p1,p2,p3,p4} 编码**：
  - p1, p2, p3 在单位球上且两两正交（编码旋转 RX）
  - p4 编码平移 tX（分米级归一化）
- **条件特征 CondFeature 构建**：
  - 视觉-几何特征：COTR 做 4×4 网格跨图匹配 → 双 Image-MLP 在 t 与 t+1 步去噪 → f_img
  - 动作感知特征：6D 动作向量通过 Text-MLP → f_txt
  - 跨模态融合：受 Q-Former 启发，将 [f_txt; f_img] 作为 KV，K=8 个可学习查询做交叉注意力
- **扩散生成器 D_θ**：Concatsquash MLPs 实现，从条件分布生成点集
- **多任务损失**：
  - L_rank：Rank-N-Contrast 对比学习（温度 τ=2）
  - L_diff：扩散去噪损失
  - L_sphere + L_ortho + L_dist：球面、正交、最小距离几何正则项

### 部署工作流
每个子目标交替执行 ⟨EVAM 视觉对齐 → DHCM 标定运动 → VLA 操作⟩，对齐后切回 VLA；若物体离开视野（searching），EVAM 重新初始化。

### 多阶段训练策略
- **第一阶段（80% 数据）**：分别独立训练 EVAM 与 DHCM
- **第二阶段（20% 数据）**：冻结 EVAM 与 Geo-MLP，端到端精调跨模态融合与扩散生成器

---

## 三、实验设计

### 数据集
- **训练数据**：从 Open X-Embodiment 中的 **BridgeData** 与 **DROID** 中选取 60K 操作片段，提取 **2.3M 自我中心-目标图像对**（带相对位姿标注）
- **目标图像生成辅助**：Gemini 2.5 Flash Image（蒸馏监督）

### Benchmark 与任务设置
四类操作任务：
- **Task-L**：Lift（短程，抓取精度）
- **Task-Po**：Put onto（短程，序列推理）
- **Task-PA**：Put all into（长程，多轮）
- **Task-PD**：Put into drawer（长程，时空约束）

### 实验平台
- **仿真**：NVIDIA Isaac Sim + Franka Emika Panda
- **真实**：UMS Eco-bot + MOKOSE 4K 第三人称相机 + US858 腕部相机

### 对比基线（5 种 SOTA VLA）
- OpenVLA
- TinyVLA
- SpatialVLA
- Pi-0
- OpenVLA-OFT

每个基线在有/无 EgoRoC 条件下分别测试 100 次/任务。

---

## 四、资源与算力

论文明确提及的算力相关信息：
- **优化框架**：DeepSpeed ZeRO-2，无量化
- **EVAM 训练**：AdamW，lr=10⁻⁵，LoRA rank=64，17 个 epoch，余弦退火
- **DHCM 训练**：Adam 优化器，lr=10⁻⁴，weight decay=5×10⁻⁵，batch size=1024，50,000 步，扩散步数=10
- **第二阶段**：SGD，lr=10⁻⁵，batch size=256，1 epoch

**未明确披露**：GPU 型号、数量、训练总时长、显存占用等具体算力细节（这是论文的不足之处）。

---

## 五、实验数量与充分性

### 实验组成（共 6 大类）
1. **跨域泛化实验**：仿真 + 真实，5 个 VLA 基线 × 4 任务 × 100 次测试
2. **数据高效微调实验**：OpenVLA & Pi-0 × 4 数据集规模 {75, 150, 225, 300} × In/Out-of-Distribution 任务
3. **可插拔适配性实验**：共享 OpenVLA 的 LMM 作为 EVAM backbone（Table 1）
4. **消融实验**（5 项）：
   - 手眼标定策略 vs Tsai-Lenz（Table 2）
   - 网格匹配策略：无网格 / 2×2 / 4×4 / 8×8 COTR（Table 3）
   - Rank-N-Contrast 对比学习（Table 4）
   - 扩散过程 vs 直接 MLP 回归（Table 5）
   - Geo-MLP 几何约束模块（Table 6）

### 充分性评估
- ✅ 覆盖了仿真 + 真实环境、5 种主流 VLA、长/短程任务、域内/域外分布
- ✅ 消融实验较为系统，覆盖 DHCM 各关键组件
- ✅ 与经典方法（Tsai-Lenz）做了对比
- ⚠️ 评测任务数量有限（4 类），缺少更细粒度的失败模式分析
- ⚠️ 未公开代码或随机种子敏感性分析，可复现性受限

---

## 六、主要结论与发现

1. **一致性提升**：所有 5 个 VLA 基线在附加 EgoRoC 后任务成功率均稳定提升，尤其在长程与域外任务上。
2. **数据高效**：相同演示数量下，加入 EgoRoC 后微调成功率更高，数据效率显著改善。
3. **零样本迁移**：跨场景、跨硬件部署无需手工标定，可直接迁移。
4. **在线手眼标定优势**：完整训练的 DHCM 在所有任务上均超过经典 Tsai-Lenz 方法。
5. **关键设计验证**：
   - 网格匹配在 4×4 时取得精度/速度平衡
   - Rank-N-Contrast 显著降低旋转角误差（RAE 从 12.78° 降至 2.03°）
   - 扩散生成器优于直接 MLP 回归（RAE 2.03° vs 6.27°）
   - Geo-MLP 提供稳定但温和的提升

---

## 七、优点与亮点

- **范式创新**：首次系统化地将"视觉对齐"从任务策略中解耦，提出可复用前置模块的思路
- **即插即用**：通过 6-DoF 薄接口接入任何 VLA，零架构改动
- **数据高效**：训练仅需静态图像对（带相对位姿），无需完整操作轨迹
- **硬件无关**：扩散式在线手眼标定替代传统 AX=XB 求解，无需 CAD、标定板或外部标记
- **多模态融合设计**：Q-Former 风格的跨模态交叉注意力有效融合视觉几何与运动语义
- **优雅的 4 点位姿表示**：用单位球正交点编码旋转，简化几何约束
- **Rank-N-Contrast 适配连续旋转回归**：避免传统正负样本构造的脆弱性
- **实验设计系统**：覆盖基线、消融、对比、跨域四个维度

---

## 八、不足与局限

1. **依赖静态图像对**：对高度动态环境（运动模糊、快速变化光照）处理能力有限
2. **无时间建模**：未考虑时序信息融合，未利用视频或时序上下文
3. **目标图像生成依赖第三人称相机**：仍需外部第三人称视角渲染顶视图，并非完全自包含
4. **实时性顾虑**：扩散过程（即使 10 步）加上跨图像匹配仍带来约 0.19s/步延迟，论文承认未来需进一步降低
5. **算力披露不全**：GPU 型号/数量/总训练时长未给出，难复现性受影响
6. **任务覆盖有限**：仅 4 类操作任务，缺少对杂乱场景、多物体干扰、柔性物体等的测试
7. **基线公平性**：不同 VLA 的提示词模板与微调设置可能不完全一致，存在潜在比较偏差
8. **失败分析不足**：缺少典型失败案例的可视化（如 searching 状态卡死、扩散标定发散等）
9. **代码未开源声明**：论文未明确承诺代码/模型开源，影响后续研究复用

（完）
