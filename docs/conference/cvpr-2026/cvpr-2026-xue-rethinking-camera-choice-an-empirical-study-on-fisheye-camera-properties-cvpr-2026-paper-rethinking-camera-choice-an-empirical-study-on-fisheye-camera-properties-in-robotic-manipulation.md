---
title: "Rethinking Camera Choice: An Empirical Study on Fisheye Camera Properties in Robotic Manipulation"
title_zh: 重思相机选型：机器人操纵中鱼眼相机特性的实证研究
authors: "Xue, Han, Min, Nan, Liu, Xiaotong, Chen, Wendi, Fang, Yuan, Lv, Jun, Lu, Cewu, Wen, Chuan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Xue_Rethinking_Camera_Choice_An_Empirical_Study_on_Fisheye_Camera_Properties_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 针对机器人操纵模仿学习中鱼眼相机特性的系统实证研究
tldr: 本文针对机器人模仿学习中广泛采用的腕戴鱼眼相机，开展了首个系统性实证研究。研究围绕空间定位、场景泛化与硬件泛化三个关键问题，在仿真与真实环境中展开大量实验，揭示了宽广视场在空间定位上的优势及其对视觉复杂度的依赖。该工作为视觉反馈驱动的机器人操纵策略学习提供了相机选型与设计依据。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1604, \"height\": 526, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 676, \"height\": 566, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 698, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 685, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 356, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1814, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 857, \"height\": 539, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 607, \"height\": 561, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 829, \"height\": 457, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1528, \"height\": 460, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xue-rethinking-camera-choice-an-empirical-study-on-fisheye-camera-properties-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 905, \"height\": 543, \"label\": \"Table\"}]"
motivation: 鱼眼相机在机器人模仿学习中被广泛使用，但其对策略学习的下游影响缺乏系统性理解。
method: 在仿真与真实环境中围绕空间定位、场景泛化、硬件泛化开展大规模对照实验。
result: 发现广视场显著提升空间定位，但优势依赖于视觉复杂度等条件。
conclusion: 为面向模仿学习的相机选型与视觉输入设计提供了实证指导。
---

## Abstract
The adoption of fisheye cameras in robotic manipulation, driven by their exceptionally wide Field of View (FoV), is rapidly outpacing a systematic understanding of their downstream effects on policy learning. This paper presents the first comprehensive empirical study to bridge this gap, rigorously analyzing the properties of wrist-mounted fisheye cameras for imitation learning. Through extensive experiments in both simulation and the real world, we investigate three critical research questions: spatial localization, scene generalization, and hardware generalization. Our investigation reveals that: (1) The wide FoV significantly enhances spatial localization, but this benefit is critically contingent on the visual complexity of the environment. (2) Fisheye-trained policies, while prone to overfitting in simple scenes, unlock superior scene generalization when trained with sufficient environmental diversity. (3) While naive cross-camera transfer leads to failures, we identify the root cause as scale overfitting and demonstrate that hardware generalization performance can be improved with a simple Random Scale Augmentation (RSA) strategy. Collectively, our findings provide concrete, actionable guidance for the large-scale collection and effective use of fisheye datasets in robotic learning.

---

## 论文详细总结（自动生成）

<think>The user wants a structured, detailed summary in Chinese of the academic paper. Let me carefully analyze the paper content and organize it according to the 8 requested points.

The paper is about fisheye cameras in robotic manipulation, specifically:
1. The first comprehensive empirical study of wrist-mounted fisheye cameras for imitation learning
2. Three research questions: spatial localization, scene generalization, hardware generalization
3. Uses MuJoCo simulation with Robomimic and MimicGen benchmarks, plus real-world experiments
4. Proposes Random Scale Augmentation (RSA) to address cross-camera transfer issues
5. Key findings about FoV benefits, scene complexity dependence, and hardware generalization

Let me write a detailed structured summary in Chinese, organized by the 8 requested sections.

I need to use Markdown formatting, with hierarchical headers and bullet points. The final line should be "（完）".

Let me think about each section:

1. **Core problem & motivation**: Fisheye cameras are increasingly used in robotic manipulation (UMI, RDT2, GEN-0, π0.5) but their downstream impact on policy learning isn't systematically understood. The paper aims to bridge this gap.

2. **Methodology**:
   - Fisheye camera simulation in MuJoCo (two-stage pipeline: cube map → equirectangular → fisheye)
   - Random Scale Augmentation (RSA): samples scale factor from U(0.7, 1.3), center-crop and resize
   - Diffusion Policy with U-Net (DDIM scheduler)
   - State-free policy (no proprioception), ResNet-18 in simulation, CLIP ViT in real-world
   - Relative action space (delta actions)

3. **Experimental design**:
   - Benchmarks: Robomimic, MimicGen (MuJoCo-based)
   - 6 simulation tasks: Square, Tool Hang, Coffee, Threading, Assembly, Mug Cleanup
   - 3 real-world tasks: Pick Cup, Fold Towel, Hang Chinese Knot
   - Hardware: Flexiv Rizon 4 + DH AG-160-95 gripper + Meta Quest 3 teleoperation
   - Camera configs: Pinhole (90° sim / 60° real) vs Fisheye (235° sim / 180° real)
   - Compared: Single vs Double camera, feature-poor vs feature-rich backgrounds, N scenes (1, 8, 16, 32 sim / 1, 2, 4, 6, 8 real), different camera intrinsics

4. **Resources**: Not explicitly mentioned. The paper doesn't specify GPU model, count, or training duration. I should note this.

5. **Experimental volume & adequacy**: 
   - 6 sim tasks × multiple conditions (camera types, scene complexity, scene diversity, camera params)
   - 3 real-world tasks × multiple conditions
   - 50 rollouts per sim evaluation, 20 trials per real evaluation
   - Scene diversity: N = {1, 8, 16, 32} in sim, N = {1, 2, 4, 6, 8} in real
   - Hardware generalization: 5 unseen camera configurations
   - Seems fairly comprehensive but lacks some details

6. **Main findings**:
   - Wide FoV enhances spatial localization, but contingent on visual complexity
   - Fisheye-trained policies need scene diversity to prevent overfitting; with sufficient diversity, they generalize better than pinhole
   - Cross-camera transfer fails due to absolute scale overfitting; RSA effectively addresses this
   - Guidance: collect in feature-rich environments, maximize scene diversity, use scale augmentation

7. **Strengths**:
   - First systematic empirical study on fisheye cameras in robotic manipulation
   - Both simulation and real-world validation
   - Addresses three distinct RQs
   - Provides actionable guidance
   - RSA is simple but effective
   - Implements fisheye simulation in MuJoCo (filling a technical gap)
   - Well-designed evaluation protocol (Normalized Score for real-world)

8. **Limitations**:
   - Only wrist-mounted cameras (no third-view), may not generalize to other configurations
   - RSA evaluated extensively in simulation but only verified in real-world (limited details)
   - Only tested on diffusion policy - results may not generalize to other policy types
   - No explicit mention of computational resources
   - Limited diversity of tasks (6 sim, 3 real)
   - State-free policies may not reflect practical deployment scenarios
   - Single robot arm platform
   - Cross-embodiment transfer not deeply explored
   - No comparison with specific recent fisheye datasets
   - Doesn't deeply analyze computational overhead of RSA

Let me now write this out in a clear, structured Chinese summary.</think>

# 论文总结：重思相机选型——机器人操纵中鱼眼相机特性的实证研究

## 1. 核心问题与研究动机

- **应用趋势**：腕戴鱼眼相机因具备超大视场（FoV，常 >180°），正被越来越多的机器人模仿学习系统采用，例如 UMI、RDT2、GEN-0、π0.5 等大规数据采集项目，以及 VLA 基础模型。
- **核心矛盾**：鱼眼相机的应用速度远远超过对其下游学习影响的研究。业界对其在模仿学习中的具体收益、潜在风险、适用条件缺乏系统性认识。
- **关键空白**：
  - 现有鱼眼数据集（如 WoodScape、SynWoodScape）缺乏机器人操纵任务；
  - 主流机器人 benchmark（RLBench、ManiSkill、Robomimic 等）均未提供鱼眼渲染；
  - 尚未有工作系统隔离鱼眼镜头的光学特性对策略性能的影响。
- **研究目标**：针对腕戴鱼眼相机，围绕其两大固有特性（**宽视场**与**径向畸变**），提出三个研究问题，并给出可落地的数据采集与使用指导。

---

## 2. 方法论

### 2.1 问题形式化与三个研究问题（RQ）

- **RQ1 空间定位**：宽视场是否能提升策略的空间定位能力？
- **RQ2 场景泛化**：宽视场是否有助于跨背景的泛化？
- **RQ3 硬件泛化**：在一个鱼眼镜头上训练的策略能否迁移到不同内参的新镜头？

控制变量为：**相机模型**（鱼眼 vs 针孔）、**场景复杂度**（特征贫乏 vs 特征丰富）、**场景多样性 N**（1 → N 个背景）、**相机内参**（不同 FoV 与畸变）。

### 2.2 鱼眼相机仿真（MuJoCo 内实现）

- **两阶段渲染管线**（图 2）：
  1. 在仿真环境内放置 6 张朝向六个基本方向（前/后/左/右/上/下）的虚拟相机，拼成立方贴图（cubemap）；
  2. 将立方贴图投影为全景（equirectangular）中间表示；
  3. 应用鱼眼投影模型（参考 OmniCV-Lib）将其重投影到鱼眼图像平面。
- **意义**：填补了现有 MuJoCo benchmark 不支持鱼眼渲染的空白。

### 2.3 随机尺度增强（RSA）

- **核心思想**：跨相机失败源于策略对物体**绝对像素尺度**的过拟合，而非相对关系。
- **实现**（图 3）：
  - 对每张训练图像，从均匀分布 U(0.7, 1.3) 采样尺度因子 s；
  - 按 s 中心裁剪并 resize 到网络输入尺寸；
  - 当 s > 1.0 时为"zoom-out"：图像缩小后用黑边 padding 填充。
- **作用机理**：迫使网络关注物体相对夹爪/末端执行器的尺度，提升跨相机鲁棒性。
- **对比**：相比固定尺度（如 0.95）的 Random Crop Augmentation，RSA 显式覆盖了放大与缩小两侧。

### 2.4 模仿学习框架

- **核心算法**：Diffusion Policy（U-Net 作为噪声预测网络，DDIM 采样器）。
- **视觉编码器**：
  - 仿真：未经预训练的 ResNet-18；
  - 真实：CLIP ViT（预训练），提升对真实环境纹理与光照的鲁棒性。
- **关键设计**：**状态无关（state-free）策略**——不使用本体感知（末端位姿、关节状态），迫使策略完全依赖视觉，从而能直接评估鱼眼视场对空间定位的贡献。
- **动作空间**：
  - 仿真：delta 动作（Robomimic 默认）；
  - 真实：相对动作（相对动作块首帧，UMI 默认）。

---

## 3. 实验设计

### 3.1 仿真实验

- **基准**：Robomimic、MimicGen（基于 MuJoCo，均已扩展支持鱼眼渲染）。
- **相机配置**：
  - 针孔：FoV=90°；
  - 鱼眼：FoV=235°；
  - 均不含第三方视角相机（与 UMI / RDT2 / GEN-0 保持一致，避免混淆变量）。
- **任务（6 个，图 4）**：Square、Tool Hang、Coffee、Threading、Assembly、Mug Cleanup；覆盖高精度、空间泛化、长时序任务。

### 3.2 真实世界实验

- **硬件**：Flexiv Rizon 4（7 轴力控机械臂）+ DH AG-160-95 自适应夹爪；Meta Quest 3 遥操作。
- **相机配置**：针孔 FoV=60° vs 鱼眼 FoV=180°；无第三方视角相机。
- **任务（3 个，图 5）**：Pick Cup（空间泛化）、Fold Towel（可形变物体操纵）、Hang Chinese Knot（高精度旋转操作）。
- **背景**：可更换，区分 feature-poor / feature-rich。

### 3.3 评估协议

- **仿真**：成功率（SR），每次配置跑 50 次 rollout，取训练期间最佳 checkpoint。
- **真实**：多阶段归一化分数（Normalized Score = 完成阶段数 / 总阶段数），每配置 20 次试验；每次试验前严格重置机器人与物体位姿，确保公平对比。

### 3.4 主要对比维度

- 单/双腕戴相机 × 针孔/鱼眼 × 特征贫乏/丰富背景 × 训练场景数 N = {1, 8, 16, 32}（仿真）/ {1, 2, 4, 6, 8}（真实）；
- 跨相机迁移：在 1 个 seen param 上训练，迁移到 5 个 unseen param。

---

## 4. 资源与算力

- **论文中未明确说明**所使用 GPU 型号、数量、显存大小、训练时长或推理时间等算力信息。
- 仅可推断：仿真采用 MuJoCo，模型规模为 ResNet-18 / CLIP ViT-B/16 + U-Net，应可在常规工作站级别 GPU（如单卡 RTX 4090/A100 级别）上完成。
- 真实世界实验受限于 3 台实体相机与单一机械臂平台，主要瓶颈在数据采集而非训练。

---

## 5. 实验数量与充分性

### 5.1 实验规模

- **仿真**：6 个任务 × 多种相机/背景/场景数组合；跨硬件泛化涉及 1 seen + 5 unseen 参数配置；每配置 50 次 rollout。
- **真实世界**：3 个任务 × 多组配置（特征贫乏/丰富、N 种训练场景等）；每配置 20 次试验；共涉及 3 种以上不同物理相机型号。
- **辅助消融**：单相机 vs 双相机 × 针孔 vs 鱼眼 × 特征贫乏 vs 丰富，构成 4×2 表。
- **空间感知探针**：通过 finetune MLP 头预测本体感知状态来间接衡量视觉编码器的空间表征质量（表 2）。

### 5.2 充分性与客观性评价

- **优点**：
  - 仿真与真实世界交叉验证；
  - 控制变量清晰，针孔组作为对照；
  - 真实世界试验次数（20/配置）高于部分同类工作的 10 次；
  - 真实世界试验前严格重置，降低随机性。
- **可能的不足**：
  - 真实世界任务数仅 3 个、相机型号有限，硬件泛化的真实实验证据相对薄弱（论文亦承认详细真实实验放入了补充材料）；
  - 仅在 Diffusion Policy 上验证，未涵盖其他策略范式（ACT、3D Diffusion Policy、Octo 等 VLA）；
  - 单机械臂平台，跨 embodiment 迁移未涉及；
  - 仿真与真实世界的视觉编码器不同（ResNet-18 vs CLIP ViT），可能导致仿真/真实间结论差异难以完全归因于鱼眼本身。

---

## 6. 主要结论与发现

### 6.1 RQ1——空间定位

- **结论**：鱼眼的宽视场**确实**提升空间定位，但**前提是环境必须具有丰富的视觉特征**。
- **证据**：
  - 真实世界：富特征下鱼眼 vs 针孔的平均归一化分数增益为 +0.39（针孔仅 +0.18）；
  - 表 2 的本体感知预测探针显示，鱼眼 + 富特征组合的平移误差最低（如 Pick Cup 仅 2.362 cm，针孔+贫特征则高达 12.309 cm）。
- **指导**：数据采集应优先选择视觉复杂、特征丰富的环境。

### 6.2 RQ2——场景泛化

- **结论**：鱼眼策略在简单场景下**更易过拟合**，但只要训练场景足够多样（N 足够大），其跨场景泛化能力**显著优于**针孔。
- **证据**：
  - 真实世界 Pick Cup：训练场景 N=8 时，鱼眼在未见场景的归一化分数迅速超过 95%，针孔增长平缓；
  - 仿真中趋势一致但增幅较小，归因于视觉编码器（未预训练 ResNet-18）和仿真背景复杂度较低。
- **指导**：最大化场景多样性（背景纹理、光照、干扰物）是解锁鱼眼泛化潜力的关键。

### 6.3 RQ3——硬件泛化

- **结论**：跨相机直接迁移会出现严重性能下降，根因是**对绝对像素尺度的过拟合**；RSA 能有效缓解。
- **证据**（图 10）：在 6 个仿真任务上平均，使用 RSA 后跨 5 种 unseen 参数的成功率均高于标准增强基线，特别是 Param 3、Param 4 等极端参数下提升最显著。
- **指导**：训练时引入强尺度的数据增强（如 RSA），提升跨镜头迁移能力，便于利用多源异构鱼眼数据集。

---

## 7. 论文亮点

- **首创性**：第一篇针对机器人模仿学习中鱼眼相机特性的系统实证研究，填补了"鱼眼用得多、研究少"的空白。
- **双管齐下**：同时在仿真（大规模、可控变量）和真实世界（小规模、可信验证）展开研究，互为补充。
- **工具贡献**：在 MuJoCo 中实现了完整的鱼眼渲染管线，参考 OmniCV-Lib 的两阶段方法可被社区直接复用。
- **RQs 设计清晰**：将鱼眼两大光学特性（宽视场 / 畸变）自然映射到三类泛化问题（定位 / 场景 / 硬件），逻辑自洽。
- **方法简洁**：RSA 仅通过随机尺度裁剪即可显著提升跨相机泛化，无需修改网络结构或额外监督，工程友好。
- **可落地指导**：三项"Guidance"明确、可操作，直接面向大规模数据采集与模型训练实践。
- **评估精细**：真实世界采用多阶段归一化分数，比二元成功/失败更能反映策略行为差异。

---

## 8. 不足与局限

- **算力与训练细节缺失**：未报告 GPU 型号、数量、训练时长、超参搜索过程，复现成本难以估算。
- **策略范式单一**：仅在 Diffusion Policy + U-Net 上验证，未涵盖 ACT、3D Diffuser Actor、Octo 等主流 VLA/模仿学习方法，结论的泛化性有待验证。
- **真实世界规模有限**：硬件泛化在真实世界中仅做"验证性"展示，详细数据放入补充材料，可能存在选择性报告风险。
- **相机配置受限**：仅考虑腕戴相机，且不含第三方视角相机；多视角腕戴配置、其他镜头型号的覆盖不足。
- **仿真与真实视觉编码器不一致**：仿真用未经预训练的 ResNet-18，真实用 CLIP ViT，可能导致两套实验的结论差异并非完全源自鱼眼本身。
- **任务复杂度有限**：仿真 6 任务、真实 3 任务，均偏向桌面级 pick-and-place 或简单插装；缺乏长时序、接触丰富、刚体动力学复杂的任务。
- **状态无关策略的代价**：移除本体感知后，方法能否与含状态输入的策略在实际部署中比拼仍未知。
- **未分析计算开销**：RSA 引入的额外训练耗时与对最终推理速度的影响未讨论。
- **缺乏下游 VLA 评估**：未将结论扩展到基于鱼眼数据预训练的 VLA 模型（如 GEN-0、RDT2 等）的实际微调与部署场景。
- **背景差异未量化**：特征贫乏/丰富的"视觉复杂度"靠人工定义，缺乏图像复杂度（如信息熵、特征点数量）的客观度量。

（完）
