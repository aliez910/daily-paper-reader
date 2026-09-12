---
title: "RoMan-4D: Learning Robot Arm Manipulation from 4D World Models"
title_zh: RoMan-4D：从4D世界模型学习机械臂操控
authors: "Kaichen Zhou, Yuzhen Chen, Fangneng Zhan, Hang Hua, Grace Chen, Xinhai Chang, Ao Qu, Yilun Du, Zhuang Liu, Paul Pu Liang, Mengyu Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/757.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 通过视频世界模型与逆动力学实现机械臂操控学习
tldr: 针对视频世界模型生成结果缺乏物理一致性的问题，本文提出几何对齐的4D世界模型GEM-4D。该方法将密集4D对应关系作为监督注入生成主干，并结合逆动力学模型实现机械臂操控。生成视频具备外观与几何结构的一致性。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 778, \"height\": 574}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 467, \"height\": 372}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 460, \"height\": 372}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 427, \"height\": 302}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-005.webp\", \"caption\": \"\", \"page\": 8, \"index\": 5, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-006.webp\", \"caption\": \"\", \"page\": 8, \"index\": 6, \"width\": 570, \"height\": 257}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-007.webp\", \"caption\": \"\", \"page\": 8, \"index\": 7, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-008.webp\", \"caption\": \"\", \"page\": 8, \"index\": 8, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-009.webp\", \"caption\": \"\", \"page\": 8, \"index\": 9, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-010.webp\", \"caption\": \"\", \"page\": 8, \"index\": 10, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-011.webp\", \"caption\": \"\", \"page\": 8, \"index\": 11, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-012.webp\", \"caption\": \"\", \"page\": 8, \"index\": 12, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-013.webp\", \"caption\": \"\", \"page\": 8, \"index\": 13, \"width\": 554, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-014.webp\", \"caption\": \"\", \"page\": 9, \"index\": 14, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-015.webp\", \"caption\": \"\", \"page\": 9, \"index\": 15, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-016.webp\", \"caption\": \"\", \"page\": 9, \"index\": 16, \"width\": 493, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-017.webp\", \"caption\": \"\", \"page\": 9, \"index\": 17, \"width\": 798, \"height\": 247}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-018.webp\", \"caption\": \"\", \"page\": 9, \"index\": 18, \"width\": 798, \"height\": 247}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-019.webp\", \"caption\": \"\", \"page\": 9, \"index\": 19, \"width\": 493, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-020.webp\", \"caption\": \"\", \"page\": 9, \"index\": 20, \"width\": 493, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-021.webp\", \"caption\": \"\", \"page\": 9, \"index\": 21, \"width\": 493, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-022.webp\", \"caption\": \"\", \"page\": 9, \"index\": 22, \"width\": 493, \"height\": 368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-023.webp\", \"caption\": \"\", \"page\": 11, \"index\": 23, \"width\": 1976, \"height\": 1258}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-024.webp\", \"caption\": \"\", \"page\": 13, \"index\": 24, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-025.webp\", \"caption\": \"\", \"page\": 13, \"index\": 25, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-026.webp\", \"caption\": \"\", \"page\": 13, \"index\": 26, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-027.webp\", \"caption\": \"\", \"page\": 13, \"index\": 27, \"width\": 828, \"height\": 623}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-028.webp\", \"caption\": \"\", \"page\": 13, \"index\": 28, \"width\": 828, \"height\": 623}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-029.webp\", \"caption\": \"\", \"page\": 13, \"index\": 29, \"width\": 828, \"height\": 623}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-030.webp\", \"caption\": \"\", \"page\": 13, \"index\": 30, \"width\": 582, \"height\": 437}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-031.webp\", \"caption\": \"\", \"page\": 13, \"index\": 31, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-032.webp\", \"caption\": \"\", \"page\": 13, \"index\": 32, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-033.webp\", \"caption\": \"\", \"page\": 13, \"index\": 33, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-034.webp\", \"caption\": \"\", \"page\": 13, \"index\": 34, \"width\": 582, \"height\": 436}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-035.webp\", \"caption\": \"\", \"page\": 13, \"index\": 35, \"width\": 755, \"height\": 571}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-036.webp\", \"caption\": \"\", \"page\": 13, \"index\": 36, \"width\": 748, \"height\": 565}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c2203ce6dc5edf043cb980d6/fig-037.webp\", \"caption\": \"\", \"page\": 13, \"index\": 37, \"width\": 789, \"height\": 597}]"
motivation: 视频世界模型生成结果缺乏物理一致性，难以支持可靠的机器人操控动作执行。
method: 引入几何基础模型的4D对应监督，构建几何对齐的视频世界模型并结合逆动力学。
result: 生成视频具备时空一致的物理结构，可用于机械臂操控策略学习。
conclusion: 几何对齐的世界模型为机器人操控提供了更可靠的视觉到动作桥梁。
---

## Abstract
Video world models can generate realistic futures from a sin-gle instruction, but they often fail to track the same physical pointsconsistently across time. As a result, the generated videos appear plausi-ble, yet lack the physical grounding required for reliable action execution,such as robot manipulation. We present GEM-4D, a geometry-groundedvideo world model that resolves this limitation by injecting dense 4Dcorrespondence supervision distilled from a pretrained geometry foun-dation model into the video generative backbone during training. Thissupervision enables the video world model to jointly capture appearanceand geometric structure while retaining a single-stream architecture withno additional inference cost. We further introduce an inverse dynam-ics module that converts correspondence-consistent video rollouts intoexecutable robot trajectories, enabling direct deployment in both real-world and simulated manipulation. GEM-4D achieves state-of-the-artperformance on both video prediction and geometric consistency acrossboth simulation and realistic scenarios and improves real-world manipu-lation success from 61% to 81%. Additional results are available at thehttps://gem-4d.github.io/.

---

## 论文详细总结（自动生成）

<think>The user wants a comprehensive Chinese summary of the GEM-4D paper following specific structure. Let me carefully analyze the paper and organize the summary according to the 8 requested points.

The paper is about GEM-4D: Geometry-Enhanced Video World Models for Robot Manipulation. Let me extract key information:

1. Core problem: Video world models lack physical consistency / correspondence consistency across frames, making action extraction unreliable for robot manipulation.

2. Method: 
- Geometry-Enhanced Velocity Alignment (GEVA) - distills 4D geometry foundation model features into video DiT
- Dual flow-matching framework with Video DiT and Geometry DiT
- Asymmetric conditioning: Geometry DiT receives video features as conditioning, no direct access to pixels
- Inference uses only video branch - zero additional cost
- Adaptive Inverse Dynamic System (AIDS) for converting rollouts to actions

3. Experiments:
- Datasets: ManiSkill3, RLBench, Bridge, RT-1, Droid (real-world)
- 400 unseen samples from Droid for real-world evaluation
- 780 unseen samples from RLBench for synthetic evaluation
- Baselines: CogVideoX, WAN 2.2-14B, TesserAct, Geometry Forcing
- Metrics: FVD, SSIM, PSNR, AbsRel, δ1, δ2, Chamfer Distance, δvis avg, task success rate
- 7 RLBench tasks, 3 Droid tasks (AUTOLab, CLVR, RAIL)

4. Resources: No explicit GPU/compute info provided

5. Experimental scale: Multiple ablations, comparisons on real and synthetic, but limited task diversity

6. Conclusions: GEM-4D achieves SOTA on video prediction and geometric consistency, improves real-world manipulation from 61% to 81%

7. Strengths:
- Novel use of geometry foundation models as correspondence teachers
- Single-stream architecture, zero inference overhead
- Comprehensive evaluation across real and synthetic
- Significant improvement over baselines

8. Limitations:
- Single-view RGB-only setting
- Limited number of tasks (7 RLBench, 3 Droid)
- No compute info disclosed
- Limited embodiment coverage
- Reliance on multiple foundation models (Qwen3.5-VL, SAM 2, CoTracker3, FoundationPose, GraspGen) for AIDS

Let me write this up in a structured Chinese Markdown format.</think>

# GEM-4D 论文总结

## 1. 核心问题与研究动机

- **核心问题**：现有视频世界模型（Video World Models）在生成任务条件下的未来帧时，往往只能产生视觉逼真的视频，但**缺乏跨帧的物理一致性（correspondence consistency）**。即同一个 3D 表面上的像素在不同帧间无法保持一致的轨迹。
- **后果**：从生成视频中提取可执行机器人动作时会出现问题——刚性物体发生非刚性形变、接触点漂移、深度不一致等"视觉上微妙但物理上致命"的错误。
- **现有方法的不足**：
  - 像素/潜空间重建损失无法保证对应关系一致（many-to-one 映射问题）。
  - 显式 4D 监督方法（如 TesserAct）需预测深度、法线等几何量，扩大输出空间且需要大规模几何标注。
- **核心洞察**：4D 几何基础模型（如 PAGE-4D、VGGT）的中间表征已经编码了影响帧间对应关系的关键因素（深度 D、相机位姿 R/T、场景流 ΔX）。可以将这些几何基础模型作为**对应关系教师**，通过特征级蒸馏注入视频生成主干，而无需修改输出空间。

## 2. 方法论

### 2.1 整体框架
GEM-4D 是一个**双流匹配（Dual Flow-Matching）框架**，包含：
- **Video DiT（视频分支）**：基于流匹配的视频潜在生成。
- **Geometry DiT（几何分支）**：以视频中间特征为条件，预测几何特征的流。

### 2.2 关键技术细节

**（1）帧间对应关系的形式化**
- 像素投影公式（Eq.1）：$p_{t+1} \sim K[R_{t \to t+1} D(p_t) K^{-1} p_t + T_{t \to t+1} + \Delta X_t]$
- 指出只要模型内部表征正确编码 (D, R, T, ΔX)，对应关系即可自动正确。

**（2）流匹配视频生成**
- 使用 VAE 编码视频潜变量 $z_0$，通过流匹配 ODE 过程生成视频。
- 训练目标：$L_{vid}^{FM} = \mathbb{E}_{z_0, z_1, t} \| v_{\theta}^{vid}(z_t, t, c) - v^*(z_t, t) \|_2^2$
- 中间特征 $m_t = E_\theta^{vid}(z_t, t, c)$，$v_\theta^{vid} = U_\theta^{vid}(m_t)$

**（3）几何流分支（Geometry Flow Branch）—— 核心创新**
- 冻结几何基础模型 G 提取密集几何表征 $g_0 = G(\{I_t\}_{t=0}^T)$。
- 几何分支 $v_\psi^{geo}$ **仅以视频中间特征 $m_t$ 作为场景级条件**，没有直接访问像素、相机参数或深度。
- 几何流匹配损失：$L_{geo}^{FM} = \mathbb{E}_{g_0, g_1, t} \| M(v_\psi^{geo}(g_t, t, m_t)) - v^*(g_t, t) \|_2^2$

**（4）联合优化与几何接地（Geometric Grounding）**
- 总损失：$L = L_{vid}^{FM} + \alpha L_{geo}^{FM}$
- 梯度分解（Eq.7）：外观项驱动 $m_t$ 编码像素运动，几何项驱动 $m_t$ 编码"为什么这么运动"的深度/位姿/场景流结构。
- **关键设计**：几何分支是"只读"的——读取视频特征但不写回；推理时丢弃几何分支，**实现零额外推理开销的单流生成架构**。

**（5）自适应逆动力学系统（AIDS）**
- **3D 场景接地**：使用 Qwen3.5-VL + SAM 2 生成分割掩码；FoundationPose 对齐 EE CAD 模型恢复初始 6DoF 位姿。
- **双准则置信门控跟踪器**：
  - 监控锚点保留率 $s_t$ 和帧间变化 $\Delta s_t$。
  - 渐变漂移（$s_t < \tau$）：重新采样锚点。
  - 突然崩溃（$\Delta s_t < -\delta$）：调用 VLM 重新接地掩码。
- **几何-运动学位姿回退**：当 FoundationPose 置信度 $\kappa_t < \kappa^*$ 时，用深度反投影的 3D 质心替换平移，SE(3) 上球面线性插值替换旋转。
- **抓取插入**：用 GraspGen 在目标点云上预测候选抓取，按加权位姿偏差选取最优抓取，逆运动学转换为可执行动作。

## 3. 实验设计

### 3.1 数据集与场景
- **训练集**：ManiSkill3、RLBench、Bridge、RT-1。
- **真实世界评估**：Droid 数据集（400 个未见样本），深度由 Depth Anything V3 估计，点跟踪由 CoTracker3 完成。
- **仿真评估**：RLBench（780 个未见样本），有真值深度。
- **额外真实机器人**：UF Robot Arm 实物部署。

### 3.2 评测指标
- **视频质量**：FVD、SSIM、PSNR。
- **深度质量**：AbsRel、δ1、δ2。
- **3D 重建**：L1 Chamfer Distance。
- **对应质量**：δvis_avg（TAP-Vid 协议）。
- **下游任务**：任务成功率（真实数据集人工评估 15 人；仿真回放执行）。

### 3.3 对比方法
- **CogVideoX**：大规模图像到视频扩散 Transformer（~35M 视频微调）。
- **WAN 2.2-14B**：基于时空 VAE 的 I2V 模型。
- **TesserAct**：基于 CogVideoX 的 4D 具身世界模型（联合 RGB+深度+法线）。
- **Geometry Forcing**：基于表示对齐的几何先验方法。
- **未对比**（因输入模态不同）：RoboTransfer（多视角）、3DFlowAction（输出流而非 RGB）、Liu et al.（立体 RGB-D）。

### 3.4 任务范围
- **RLBench 7 个任务**：Lift、Numbered Block、Put Rubbish InBin、Reach Target、Lamp On、Pick Up Cup、Slide Block ToTarget、Solve Puzzle 等。
- **Droid 3 个场景**：AUTOLab、CLVR、RAIL。

## 4. 资源与算力

- **论文中未明确披露**任何训练算力信息（GPU 型号、数量、训练时长、参数量等）。
- 间接可推断信息：使用视频 DiT + 几何分支联合训练，包含冻结的几何基础模型（PAGE-4D、VGGT 等）和多个推理期使用的 VLM（Qwen3.5-VL）、分割模型（SAM 2）、跟踪器（CoTracker3）、位姿估计（FoundationPose）、抓取生成（GraspGen）。
- 缺乏对训练成本和环境影响的说明，是该论文的一个信息缺口。

## 5. 实验数量与充分性

- **主对比实验**：2 个数据集（真实 Droid + 仿真 RLBench）× 4 个基线方法 × 多维度指标（RGB、几何、对应）= 较为充分的横向对比。
- **下游任务实验**：7 个仿真任务 + 3 个真实场景，覆盖长时序操控和多种几何复杂度。
- **消融实验（Table 3）**：3 组——无几何监督基线、显式深度监督（GEM-4D (Dep)）、不同几何基础模型（GEM-4D (VGGT)）。
- **定性分析**：Droid 和 RLBench 上的视觉对比、真实 UF 机械臂部署。
- **公平性考量**：
  - 所有基线均在同一训练集上微调。
  - 由于 TesserAct 的逆动力学不开源，作者使用自己的 AIDS 处理其生成视频进行比较。
  - 由于 CogVideoX 生成视频无法被 AIDS 可靠处理，未报告其任务成功率。
- **总体充分性**：覆盖较为全面，但任务数量（尤其是真实世界）相对有限，且无统计显著性检验（仅说明 20 次生成取平均，std ~1-2%）。

## 6. 主要结论与发现

- **视频质量**：GEM-4D 在 FVD、SSIM、PSNR 上取得最优或次优，视觉真实感优于基线。
- **几何一致性**：在 AbsRel、δ1、δ2、Chamfer 上显著优于所有基线，表明生成帧保留了准确的 3D 结构。
- **对应质量**：δvis_avg 在真实域从 ~67 提升到 71.23，仿真域从 ~61 提升到 68.18。
- **下游操控**：真实 Droid 任务成功率从 ~58-65% 提升到 75-87%，RLBench 仿真任务成功率 63%-82%，远高于 TesserAct（多数任务 < 50%）。
- **核心结论**：将几何基础模型的表征蒸馏到视频世界模型内部，是提升物理一致性和下游动作可靠性的"简单而有效"的方法。

## 7. 优点与亮点

- **方法创新性**：
  - 首次将 4D 几何基础模型作为视频生成模型的"对应关系教师"，而非直接几何量预测器。
  - 形式化论证了为什么几何表征蒸馏等价于隐式对应关系约束（Eq.1 的论证）。
- **架构高效性**：训练时双流，推理时**零额外开销**的单流架构，工程上极具吸引力。
- **系统性闭环**：从指令 → 视频生成 → 逆动力学 → 真实机器人执行，形成完整的视觉到动作链路。
- **AIDS 设计精巧**：双准则置信门控 + 几何-运动学位姿回退，针对生成视频的渐变漂移和突然崩溃分别处理。
- **实验跨越真实与仿真**：在 Droid 真实数据、RLBench 仿真、UF 实物机械臂三层面验证。
- **相对提升显著**：真实世界成功率从 61% 提升到 81%（+20 点）。

## 8. 不足与局限

- **资源不透明**：未披露 GPU 数量/型号、训练时长、数据规模等关键工程细节，难以复现。
- **任务覆盖有限**：
  - 真实世界仅 3 个 Droid 子场景，未涵盖更多样化的物体、背景、机器人体型。
  - 仿真任务仅 7 个，且集中在 RLBench，缺少 CALVIN、Meta-World 等其他基准。
- **依赖多模型堆叠**：AIDS 依赖 Qwen3.5-VL、SAM 2、CoTracker3、FoundationPose、GraspGen 等多个基础模型，系统复杂，任一环节失效可能影响整体成功率。
- **几何教师选择敏感**：消融显示 VGGT 反而会轻微降低性能（因 VGGT 主要面向静态/准静态场景），说明几何教师的选择对动态操控场景有较强依赖性，缺乏通用指导。
- **单视角 RGB 输入**：限制了在遮挡场景或多视角一致性需求高的任务中的应用。
- **缺乏消融的广度**：
  - 未对损失权重 α、几何教师层选择、跟踪阈值 τ、δ 等关键超参数进行敏感性分析。
  - 未对 AIDS 各组件（如双准则门控 vs. 仅用 VLM 重接地）做单独消融。
- **偏差风险**：人类评估主观性强（虽平均 15 人，但仍受视频长度、任务难度等影响）；CogVideoX 因 AIDS 处理失败被排除比较，存在一定的对比公平性争议。
- **应用限制**：当前仅在桌面级操控（Franka、UF Arm）上验证，对移动机器人、双手机器人、柔性物体操控等未涉及。

---

（完）
