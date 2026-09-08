---
title: "SaPaVe: Towards Active Perception and Manipulation in Vision-Language Action Models for Robotics"
title_zh: SaPaVe：面向机器人的视觉语言动作模型中主动感知与操作
authors: "Liu, Mengzhen, Zhou, Enshen, Chi, Cheng, Han, Yi, Rong, Shanyu, Chen, Liming, Wang, Pengwei, Wang, Zhongyuan, Zhang, Shanghang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_SaPaVe_Towards_Active_Perception_and_Manipulation_in_Vision-Language_Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 端到端视觉语言动作框架，统一主动感知与操作并解耦动作空间
tldr: 现有方法难以将语义驱动的主动感知与稳健的视点不变操作统一在同一模型中。本文提出端到端框架SaPaVe，将相机动作与操作动作解耦，先在大规模数据上学习语义相机控制，再通过混合数据联合优化两类动作。论文发布了包含20万对图文相机动作数据的ActiveViewPose-200K数据集，并推动了通用型视觉语言动作模型在复杂场景中的发展。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1792, \"height\": 679, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1797, \"height\": 1107, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1795, \"height\": 1066, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1794, \"height\": 510, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1800, \"height\": 293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 280, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1781, \"height\": 213, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 226, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-sapave-towards-active-perception-and-manipulation-in-vision-language-action-models-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 852, \"height\": 248, \"label\": \"Table\"}]"
motivation: 现有VLA模型难以同时具备语义级主动感知和视点不变的操作执行能力。
method: 将相机动作与操作动作解耦，并采用自底向上分层训练与混合数据联合优化策略。
result: 构建200K图像-语言-相机动作数据集并实现端到端主动感知与操作。
conclusion: 该工作推动了通用型VLA模型在复杂场景中的语义与几何协同。
---

## Abstract
Active perception and manipulation are crucial for robots to interact with complex scenes. Existing methods struggle to unify semantic-driven perception actively with robust, viewpoint-invariant execution accordingly. To this end, we propose SaPaVe, an end-to-end framework that jointly learns these capabilities in a data-efficient manner. Central to our approach is a decoupling of camera and manipulation actions, contrary to shared-action-space, and learning in a bottom-up strategy: we first train semantic camera control on our proposed large-scale dataset, then jointly optimizes both action types via hybrid data. To support this, we introduce ActiveViewPose-200K, comprising 200k image-language-camera movement pairs for semantic camera movement learning, and a 3D geometry-aware module that improves execution robustness under dynamic viewpoints. We further present ActiveManip-Bench, the first benchmark filling the gap to evaluate active manipulation. Extensive experiments in both simulation and real-world settings show that SaPaVe outperforms recent VLA models such as GR00T N1 and pi0, achieving up to 31.25% higher success rates in real-world tasks. Our results show that tightly coupled perception and execution, when trained with decoupled yet coordinated strategies, enable efficient and generalizable active manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "SaPaVe: Towards Active Perception and Manipulation in Vision-Language Action Models for Robotics" following a specific structured format. Let me carefully analyze the paper content and provide a comprehensive summary covering all 8 required points.

Let me organize my thoughts:

1. **Core Problem & Motivation**: Active perception + manipulation for robots is hard. Existing VLA models are trained on fixed near-optimal views, lacking semantic active perception and robustness to viewpoint changes. Methods either discretize camera control (VQA-based) or try to extend VLA action space but suffer from data scarcity and lack of 3D geometric awareness.

2. **Methodology**: 
   - Decoupled action space (camera vs manipulation)
   - Bottom-up two-stage training:
     - Stage 1: Train camera adapter (LoRA on VLM) + camera action decoder on ActiveViewPose-200K using MSE loss
     - Stage 2: Freeze camera adapter, train decoupled action heads on mixed data
   - Camera Adapter: LoRA on VLM
   - Decoupled Action Heads: separate camera action decoder and other action decoder
   - Universal Spatial Knowledge Injection: Universal Spatial Encoder from MapAnything, element-wise add with VLM tokens, injected into DiT blocks for denoising
   - ActiveViewPose-200K dataset construction
   - Action chunking with horizon k

3. **Experiments**:
   - Datasets: ActiveViewPose-200K (200K), ActiveManip-Bench (sim), real-world teleop data
   - Benchmarks: ActiveManip-Bench (12 tasks, 100 objects, 20 scenes, G1 humanoid in Isaac Sim)
   - Baselines: Qwen2.5-VL-72B, Gemini-2.5-Pro, Multi-SpatialMLLM, GR00T-N1, π0
   - Tasks: Unoccluded/Occluded/Out-of-View Pick-and-Place, Articulated Manipulation

4. **Resources**: The paper doesn't mention specific GPU types, count, or training duration. I should note this.

5. **Experiment count & sufficiency**:
   - 6 tables of results
   - Semantic active perception evaluation
   - Fixed vs dynamic camera evaluation
   - Comparison with VLA baselines
   - Generalization evaluation (varied objects, lighting, scenes)
   - Ablation study (Stage 1, Stage 2, D.A.H., C.A., U.S.K.I.)
   - Quite comprehensive but limited to specific setups

6. **Main conclusions**:
   - Decoupling camera and manipulation actions is effective
   - Bottom-up training strategy works
   - Camera adapter preserves VLM knowledge
   - Universal spatial knowledge injection is crucial
   - Outperforms GR00T-N1 and π0 by significant margins

7. **Strengths**:
   - Novel decoupled action space design
   - Data-efficient bottom-up training
   - Comprehensive benchmark
   - Significant performance gains
   - 3D geometry awareness
   - Good generalization

8. **Limitations**:
   - Only tested on Unitree G1 humanoid
   - Limited real-world tasks
   - Computational resources not specified
   - 200K dataset is synthetic (semi-automatically generated)
   - No comparison with more recent active manipulation methods like EgoMI or ActiveUMI in main results
   - Tolerance threshold for success metric not clearly defined

Let me write this up in a structured Markdown format in Chinese.</think>

# SaPaVe 论文总结

## 1. 核心问题与研究动机

**研究背景**：让机器人在复杂场景中实现类人级别的"主动感知 + 操作"（active manipulation）是一项长期目标。该任务需要同时具备两种互补能力：
- **语义主动感知（Semantic Active Perception）**：策略性地调整视角以获取被遮挡或视场外的关键信息（例如旋转头视角以观察柜子里的碗）。
- **主动视角执行（Active-View Execution）**：将从新视角观察到的信息稳健地转化为可执行动作，即使在次优视角下也能完成任务。

**现有方法的不足**：
- 基于 VLM 的 VQA 离散视角选择方法粒度粗，无法在连续相机姿态空间中精细控制。
- 现有端到端 VLA 模型（如 GR00T-N1、π0）通常在固定、近最优的头部相机视角下训练和评测，对视角扰动敏感。
- 直接在统一动作空间中扩展相机动作会带来"数据稀缺"和"缺乏 3D 几何感知"两大问题，导致动作空间冲突与次优性能。

**核心动机**：现有方法难以将语义驱动的主动感知与稳健的、视点不变的操作统一到同一端到端模型中。

---

## 2. 方法论

### 2.1 核心思想
**关键洞察**——相机运动本质上与具体本体解耦（embodiment-agnostic），更容易学习。据此提出"自底向上"的两阶段训练策略，并将相机动作与机械臂/手部动作**解耦**到独立动作空间中，避免相互干扰。

### 2.2 问题形式化
- 策略 $\pi_\theta : O \times L \to A$，输入为 RGB 图像、可选的 3D 几何信息（深度图、相机内外参）与语言指令 $L$。
- 输出动作轨迹 $A_t = (A_{head,t}, A_{other,t})$：
  - $a_{head} \in \mathbb{R}^2$：头部相机相对 pitch / yaw 调整；
  - $a_{other} \in \mathbb{R}^{26}$：Unitree G1 仿人平台双臂（双 7-DoF）+ 双手（双 6-DoF Inspire Hand）的 26 自由度关节增量。
- 采用 action chunking 策略，预测长度为 $k$ 的动作序列。

### 2.3 架构设计
基于 VLM + 视觉编码器构建，主要包含三个新组件：

1. **Camera Adapter（相机适配器）**：在 VLM 上以 LoRA 形式注入，仅学习语义相机运动，不破坏 VLM 原始语义能力。
2. **Decoupled Action Heads（解耦动作头）**：两个独立解码器——Camera Action Decoder 与 Other Action Decoder，分别输出 $a_{head}$ 与 $a_{other}$。
3. **Universal Spatial Knowledge Injection（通用空间知识注入）**：
   - 采用来自 MapAnything 的预训练 Universal Spatial Encoder，可接受任意形式的 3D 几何输入（深度、相机内外参等），无需重新训练；
   - 编码后的空间 token 与 VLM 输出 token 逐元素相加；
   - 混合 token 注入 DiT 块，在动作去噪过程中引导解码。

### 2.4 两阶段训练流程
- **Stage 1（语义主动感知对齐）**：使用 ActiveViewPose-200K 训练 Camera Adapter 与 Camera Action Decoder，损失为 $L_{stage1} = L_{MSE}(A_{head,t}, A^*_{head,t})$。
- **Stage 2（主动操作微调）**：冻结 Camera Adapter，使用 ActiveViewPose-200K + 主动操作机器人数据的混合数据训练解耦动作头，损失为 $L_{stage2} = \lambda_{head} L_{head} + \lambda_{other} L_{other}$。

### 2.5 数据集与基准
- **ActiveViewPose-200K**：基于 Objaverse 中精选的 4k 资产 + 500 个场景 + 3k 任务模板，通过启发式算法计算最优视角并由 GPT-4o 生成/人工校对指令，构造 200k 图文-相机运动对。
- **ActiveManip-Bench**：基于 NVIDIA Isaac Sim 构建，搭载 G1 仿人机器人 + 主动头部相机，包含 12 个任务、100 个物体、20 个场景，涵盖未遮挡/遮挡/视场外三种取放与关节操作任务。

---

## 3. 实验设计

### 3.1 数据集与场景
- **ActiveViewPose-200K**：Train/Val/Test1/Test2，其中 Test2 指令省略详细相机运动描述，要求模型从图文共同推理。
- **ActiveManip-Bench**（仿真）：12 任务 × 100 物体 × 20 场景。
- **真实世界数据集**：通过机器人遥操作采集，包含 4 类任务（遮挡/视场外 Pick-and-Place、遮挡/视场外 Articulated Manipulation）。

### 3.2 对比方法
- **语义感知阶段**：Qwen2.5-VL-72B、Gemini-2.5-Pro、Multi-SpatialMLLM（专用空间 VLM）。
- **仿真相机配置**：Fixed Camera、Fixed + Wrist Camera、Active + Wrist Camera。
- **真实世界 VLA 基线**：π0、GR00T-N1（均将动作空间扩展为含相机运动的统一空间后微调）。

### 3.3 评测指标
统一采用成功率（%）。语义感知阶段判断预测的 pitch/yaw 是否在容差范围内接近真值（容差具体定义见附录 A）。

---

## 4. 资源与算力

**论文中未明确给出**所使用的 GPU 型号、数量、训练时长或参数量级（仅提及模型约 2B 参数）。这一定程度上限制了实验可复现性的评估。建议在后续工作中补充算力开销信息。

---

## 5. 实验数量与充分性

论文共给出 **5 张主表** 与多项可视化定性结果，主要实验包括：
1. **语义主动感知评测**（Table 1）：在 Test1/Test2 上与 3 个 VLM 对比。
2. **固定/动态相机对比**（Table 2）：在 ActiveManip-Bench 上对比 4 种相机配置 × 6 类任务。
3. **真实世界 VLA 对比**（Table 3）：与 π0、GR00T-N1 在 4 类任务上的对比。
5. **泛化能力评测**（Table 4）：在未见物体、不同光照、不同场景下测试。
6. **消融实验**（Table 5）：5 组消融（Stage 1、Stage 2、D.A.H.、C.A.、U.S.K.I.）。

**充分性评估**：
- 优点：实验设计系统化，覆盖仿真 + 真实世界、消融、泛化等多维度；
- 局限：真实世界仅测试 4 类任务、单一 G1 平台；与近期主动操作方法（如 ActiveUMI、EgoMI）缺乏直接对比；评测次数/置信区间未明确披露。

整体而言实验较为充分且覆盖了核心论据，但真实世界部分规模相对有限。

---

## 6. 主要结论与发现

- **解耦动作空间有效**：相机动作与操作动作分离设计显著优于统一动作空间，避免训练阶段相互干扰。
- **自底向上训练至关重要**：Stage 1 建立语义主动感知先验后，Stage 2 才能高效完成主动操作。
- **Camera Adapter 优于全量微调**：LoRA 形式既学到相机控制，又保留 VLM 高层语义。
- **空间知识注入显著提升鲁棒性**：省略 U.S.K.I. 后简单遮挡取放任务成功率下降约 15%。
- **量化结果**：
  - 在 ActiveViewPose-200K 上以仅 2B 参数比 Gemini-2.5-Pro 高 11.6%；
  - 在 ActiveManip-Bench 上超越固定视角 GR00T-N1 58%；
  - 在真实世界任务上比 π0 高 40%、比 GR00T-N1 高 31.25%；
  - 对未见物体、不同光照与场景均保持稳健性能。

---

## 7. 优点与亮点

- **创新的解耦范式**：首次明确提出相机运动与本体操作动作分离，避免统一动作空间冲突。
- **数据高效**：通过 Stage 1 在大规模合成数据上学习感知先验，Stage 2 仅需少量真实数据即可实现主动操作。
- **首个主动操作基准**：ActiveManip-Bench 填补了现有基准仅评测固定视角的空白。
- **3D 几何感知**：Universal Spatial Knowledge Injection 灵活支持多种 3D 输入配置，显著提升视角变化下的鲁棒性。
- **消融全面**：5 组消融覆盖训练策略、关键模块，论证充分。
- **跨平台落地**：仿真 + 真实世界双重验证，部署在 Unitree G1 仿人机器人上，工程性强。

---

## 8. 不足与局限

- **算力信息缺失**：未报告 GPU 型号、数量、训练时长，可复现性受限。
- **真实世界规模有限**：仅 4 类任务、单一 G1 平台，未覆盖不同光照、机器人构型的广泛验证。
- **数据集合成属性强**：ActiveViewPose-200K 通过启发式 + GPT-4o 半自动生成，存在与真实物理交互分布的差距，可能导致 sim-to-real 偏差。
- **缺乏与同类最新方法的直接对比**：未在主实验中纳入 ActiveUMI、EgoMI 等同期主动操作工作。
- **评测统计严谨性**：未提供多次试验的标准差或置信区间，单次成功率可能存在波动。
- **应用限制**：当前仅验证于 26-DoF 双臂仿人平台，推广至不同自由度构型（如单臂、移动机械臂）仍需进一步实验。
- **容差与失败模式分析不足**：语义感知评测中容差阈值的具体设定、失败案例的定性分析较为有限。

（完）
