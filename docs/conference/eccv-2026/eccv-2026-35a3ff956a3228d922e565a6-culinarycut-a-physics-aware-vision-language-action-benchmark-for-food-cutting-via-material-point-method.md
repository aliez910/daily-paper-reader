---
title: "CulinaryCut: A Physics-aware Vision-Language-Action Benchmark for Food Cutting via Material Point Method"
title_zh: CulinaryCut：基于物质点法的物理感知VLA食品切割基准
authors: "Hyunsuh Koh, Changyong Song, Youngjae Choi, Misa Viveiros, David Hyde, Heewon Kim"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/10616.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 提出CulinaryCut基准以评测现有VLA在复杂非刚性切割任务上的表现
tldr: 针对现有机器人操控数据集与VLA基准主要围绕刚性物体、无法同时刻画切割任务所需空间精度、形变、拓扑变化与接触力的问题，本文提出了CulinaryCut基准。该基准将基于物质点法（MPM）的可形变仿真器与机器人环境相结合以生成数据集，并对现有VLA模型进行评测，揭示其在物理感知方面的不足。该工作为评估通用视觉-动作模型在复杂可形变操控任务上的能力提供了物理真实的测试平台。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1920, \"height\": 1080}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 684, \"height\": 312}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 1920, \"height\": 1080}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 612, \"height\": 612}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 642, \"height\": 389}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 1536, \"height\": 2048}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 642, \"height\": 389}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 622, \"height\": 401}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 830, \"height\": 300}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 652, \"height\": 383}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 552, \"height\": 384}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-012.webp\", \"caption\": \"\", \"page\": 1, \"index\": 12, \"width\": 865, \"height\": 673}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-013.webp\", \"caption\": \"\", \"page\": 1, \"index\": 13, \"width\": 824, \"height\": 566}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-014.webp\", \"caption\": \"\", \"page\": 5, \"index\": 14, \"width\": 920, \"height\": 435}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-015.webp\", \"caption\": \"\", \"page\": 5, \"index\": 15, \"width\": 1177, \"height\": 796}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-016.webp\", \"caption\": \"\", \"page\": 5, \"index\": 16, \"width\": 2048, \"height\": 1152}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-017.webp\", \"caption\": \"\", \"page\": 5, \"index\": 17, \"width\": 400, \"height\": 300}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-018.webp\", \"caption\": \"\", \"page\": 5, \"index\": 18, \"width\": 800, \"height\": 800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-019.webp\", \"caption\": \"\", \"page\": 5, \"index\": 19, \"width\": 645, \"height\": 476}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-020.webp\", \"caption\": \"\", \"page\": 5, \"index\": 20, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-021.webp\", \"caption\": \"\", \"page\": 5, \"index\": 21, \"width\": 884, \"height\": 980}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-022.webp\", \"caption\": \"\", \"page\": 5, \"index\": 22, \"width\": 1143, \"height\": 2048}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-023.webp\", \"caption\": \"\", \"page\": 5, \"index\": 23, \"width\": 740, \"height\": 740}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-024.webp\", \"caption\": \"\", \"page\": 5, \"index\": 24, \"width\": 830, \"height\": 300}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-025.webp\", \"caption\": \"\", \"page\": 5, \"index\": 25, \"width\": 632, \"height\": 395}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-026.webp\", \"caption\": \"\", \"page\": 5, \"index\": 26, \"width\": 2000, \"height\": 2000}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-027.webp\", \"caption\": \"\", \"page\": 10, \"index\": 27, \"width\": 720, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-028.webp\", \"caption\": \"\", \"page\": 10, \"index\": 28, \"width\": 720, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-029.webp\", \"caption\": \"\", \"page\": 10, \"index\": 29, \"width\": 720, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-030.webp\", \"caption\": \"\", \"page\": 10, \"index\": 30, \"width\": 2048, \"height\": 567}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-031.webp\", \"caption\": \"\", \"page\": 11, \"index\": 31, \"width\": 6570, \"height\": 2666}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-032.webp\", \"caption\": \"\", \"page\": 12, \"index\": 32, \"width\": 2048, \"height\": 1354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-033.webp\", \"caption\": \"\", \"page\": 12, \"index\": 33, \"width\": 1260, \"height\": 878}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-034.webp\", \"caption\": \"\", \"page\": 12, \"index\": 34, \"width\": 1977, \"height\": 1820}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-035.webp\", \"caption\": \"\", \"page\": 12, \"index\": 35, \"width\": 1920, \"height\": 1080}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-036.webp\", \"caption\": \"\", \"page\": 12, \"index\": 36, \"width\": 485, \"height\": 443}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-037.webp\", \"caption\": \"\", \"page\": 12, \"index\": 37, \"width\": 455, \"height\": 381}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-038.webp\", \"caption\": \"\", \"page\": 12, \"index\": 38, \"width\": 2048, \"height\": 1352}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-039.webp\", \"caption\": \"\", \"page\": 12, \"index\": 39, \"width\": 1034, \"height\": 733}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-040.webp\", \"caption\": \"\", \"page\": 13, \"index\": 40, \"width\": 1221, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-041.webp\", \"caption\": \"\", \"page\": 13, \"index\": 41, \"width\": 802, \"height\": 558}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-042.webp\", \"caption\": \"\", \"page\": 13, \"index\": 42, \"width\": 1000, \"height\": 450}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-043.webp\", \"caption\": \"\", \"page\": 13, \"index\": 43, \"width\": 2048, \"height\": 673}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-044.webp\", \"caption\": \"\", \"page\": 13, \"index\": 44, \"width\": 2048, \"height\": 1710}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-045.webp\", \"caption\": \"\", \"page\": 14, \"index\": 45, \"width\": 1263, \"height\": 878}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-046.webp\", \"caption\": \"\", \"page\": 14, \"index\": 46, \"width\": 500, \"height\": 300}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-047.webp\", \"caption\": \"\", \"page\": 14, \"index\": 47, \"width\": 2048, \"height\": 1350}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-048.webp\", \"caption\": \"\", \"page\": 14, \"index\": 48, \"width\": 1267, \"height\": 877}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-049.webp\", \"caption\": \"\", \"page\": 14, \"index\": 49, \"width\": 1266, \"height\": 879}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-050.webp\", \"caption\": \"\", \"page\": 14, \"index\": 50, \"width\": 787, \"height\": 513}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-051.webp\", \"caption\": \"\", \"page\": 14, \"index\": 51, \"width\": 803, \"height\": 555}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-35a3ff956a3228d922e565a6/fig-052.webp\", \"caption\": \"\", \"page\": 14, \"index\": 52, \"width\": 500, \"height\": 300}]"
motivation: 现有VLA基准主要针对刚体，难以同时刻画切割任务中的形变、拓扑变化与接触力交互。
method: 构建CulinaryCut基准，将MPM可形变仿真器与机器人环境结合以生成数据集并评测VLA模型。
result: 在非刚性切割任务上系统评测现有VLA，揭示其在物理感知方面的关键不足。
conclusion: CulinaryCut 为复杂可形变操控任务中VLA模型的物理感知评测提供了新基准。
---

## Abstract
Food cutting is a representative non-rigid manipulation taskinvolving deformation, contact forces, and material separation, yet itRobot Simulation remains largely unexplored in VLA research. Existing robot manipula-tion datasets are primarily built around rigid objects and struggle tojointly capture the spatial precision, deformation, topology changes, andCut the banana force interactions required for cutting. To systematically study theseat the center. challenges, we introduce CulinaryCut, a benchmark that integrates anniskill MPM-based deformable simulator with a robot environment to generatedataset rather than provided as policy inputs, enabling evaluation of ex-isting VLAs while exposing where physical grounding is needed. Usingthree representative VLA baselines, we identify two core limitations innon-rigid cutting. First, a geometry gap: VLAs struggle to map ratio-and direction-based instructions onto object geometry, especially whensequential cuts change the object’s topology. Second, a physics gap: be-cause policies output motion without a notion of material stiffness orcontact resistance, a geometrically accurate path may still fail to severthe object. We show that training VLAs on physics-grounded trajecto-ries, without modifying the policy architecture or adding force inputs,improves cutting success and sim-to-real transfer. Together, CulinaryCutprovides a foundation for evaluating spatial reasoning and physical plau-sibility in deformable manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed structured Chinese summary of the paper "CulinaryCut: A Physics-Grounded Cutting Benchmark for Vision-Language-Action Models". I need to analyze the paper carefully and produce a summary following the 8 specified points.

Let me organize my thoughts on each section:

1. Core problem and motivation: VLA models lack evaluation on non-rigid cutting tasks. Existing benchmarks focus on rigid objects. Need to capture deformation, topology change, contact forces.

2. Methodology: 
- IntSim: coupled MLS-MPM simulator + ManiSkill
- 15 food items with real material properties from food engineering literature
- Contact force computed from momentum exchange via SDFs
- 21,000 trajectories expanded to 1.57M instances via visual (15 scenes) and language (5 variants) augmentation
- LLM-based language synthesis
- AABB-based motion planner for trajectory generation
- Velocity guardrail for safety

3. Experiments:
- Baselines: RDT, Octo, OpenVLA
- Single-object, multi-object, transfer-object, continuous cut, split cut
- Physics gap ablation: ManiSkill-trained vs IntSim-trained
- Real robot validation on Franka Panda

4. Resources: NVIDIA GPUs acknowledged, but specific count/hours not detailed. Franka Emika Panda arm with F/T sensor.

5. Experiment count: Multiple evaluation protocols (I-V), real-world validation, ablation. Reasonably comprehensive.

6. Conclusions: Two core gaps identified (geometry gap, physics gap). Physics-grounded training without architecture changes improves performance.

7. Strengths: Novel benchmark, physics integration at data level, real validation, addresses important gap.

8. Limitations: Only 15 food items, no viscoelastic/moisture modeling, single real-world validation item, visual sim-to-real gap remains, limited real robot deployment (1/10 vs 3/10).

Let me write this up in Chinese, structured with Markdown.</think>

# CulinaryCut 论文总结

## 一、核心问题与研究动机

- **核心问题**：当前 Vision-Language-Action (VLA) 模型在机器人操控领域多以**刚性物体**任务为主，缺乏对**非刚性切割**任务的系统性评测。切割任务涉及三大物理特性——**形变（deformation）、接触力（contact forces）、拓扑变化（topology changes/material separation）**，而这恰恰是几何轨迹对齐类方法所无法覆盖的。
- **研究动机**：
  - 现有大规模机器人数据集（如 Open X-Embodiment、DROID、BridgeData V2、LIBERO、RoboMIND）**缺乏切割任务**或**无法同时提供**接触力信号、语言指令、多视角观测、连续动作等 VLA 训练所需的全部要素。
  - 切割专用仿真（DiSECt、TopoCut、SliceIt!、RoboCook）虽建模材料行为，但**不联合提供**语言指令、多视角观测与连续控制轨迹。
  - 部分工作（ForceVLA）尝试在策略输入中加入力信号，但本文的立场是：在**不修改策略架构、不引入力输入**的前提下，研究**数据层面**的物理一致性是否能改善 VLA 的切割能力。

## 二、方法论

### 2.1 整体框架 IntSim

- **核心思想**：将基于粒子法的可形变物理仿真器（**MLS-MPM**）与机器人仿真器（**ManiSkill**）耦合，使机器人动作既能驱动物理形变与拓扑断裂，又能在视觉上呈现完整的切割过程。
- **关键组件**：
  - **MLS-MPM 求解器**：处理大变形与拓扑变化，结合 corotated elasticity、J2 塑性与连续损伤模型（continuum damage），刻画各食物的刚度与切割阻力。
  - **ManiSkill**：负责机器人运动学执行与视觉渲染。
  - **接触力计算**：刀具与砧板被建模为 SDF（signed distance field），由 MPM 粒子在网格节点上的速度变化累积冲量，反推得到实时接触力曲线。
- **材料参数**：15 种食材的密度、Young's modulus、Poisson's ratio 取自食品工程文献（Apple、Cucumber、Melon、Banana、Orange、Peach、Strawberry 等）。

### 2.2 数据生成流水线（Fig. 2）

1. **遥操作示范**：对每种切割样式（Slice / Multi / Bias / Dice / Saw）由人工示教生成初始演示。
2. **物理仿真**：刀具首次接触食材后，MPM 仿真器实时更新形变与拓扑。
3. **语言增强**：基于模板+同义词池+LLM（GPT-4）改写，每条轨迹至少生成 5 种语言变体；指令类型涵盖定量比例（"Cut 1/4 off"）、均分（"Slice into four equal pieces"）、方向（"from the right"）等。
4. **轨迹增强**：通过 AABB-based 运动规划器，对**物体位置、缩放、姿态**以及**切割高度、速度**做随机化。
5. **视觉增强**：在 15 个室内背景（Replica-CAD、AI2-THOR、ProcTHOR）下重新渲染。

### 2.3 数据规模

- **21,000 条**基础轨迹 × **15 个背景** × **5 条语言变体** ≈ **1.57M 总实例**。
- 每条样本包含：语言指令、多视角观测、连续控制动作、接触力曲线。

### 2.4 安全与公平设置

- **Velocity Guardrail**：在执行阶段对所有基线策略统一施加速度限幅，但不向策略提供额外观测或重规划，以隔离"物理数据"与"安全模块"的影响。

## 三、实验设计

### 3.1 评测对象
- **基线 VLA 模型**：RDT（diffusion-based transformer）、Octo（开源通用策略）、OpenVLA（VLM+动作头）。
- 三个模型均在 CulinaryCut 训练集上 **fine-tune**，且**不接收**力、接触或损伤状态作为输入。

### 3.2 Benchmark 任务协议（5 项）
| 编号 | 任务 | 评估目标 |
|------|------|----------|
| I | 单物体切割 | 物体尺度与定位精度 |
| II | 多物体场景 | 视觉干扰下的目标定位 |
| III | 跨类别泛化（leave-one-out） | 几何/外观/材料迁移能力 |
| IV | 连续比例切割（0.1–0.9） | 比例-几何映射能力 |
| V | 顺序分割切（1/3、1/4、1/5） | 拓扑变化下的长程规划 |

### 3.3 物理剥离评估（Physics Gap Ablation）
- 训练数据：ManiSkill 几何轨迹 vs IntSim 物理接地轨迹
- 评测环境：ManiSkill（仅几何）vs IntSim（含 MPM 物理）
- 任务：橙子切割

### 3.4 真实机器人验证
- **平台**：Franka Emika Panda + 厨房刀 + 腕部 F/T 传感器（60 Hz）
- **任务**：对香蕉进行恒速下切
- **对比指标**：去除基线后真实峰值力 vs IntSim 估算峰值力，以及归一化时序曲线形态

## 四、资源与算力

- 论文仅致谢中提及 **NVIDIA Corporation 提供 GPU**，但**未明确说明**具体 GPU 型号、数量、训练时长。
- 物理仿真侧给出 MLS-MPM 框架参数：网格分辨率 **120³**、Δt=**2×10⁻⁵ s**、**6 子步**。
- 真实机器人侧仅部署一次代表性实验（橙子切割），规模较小。
- ➡️ **资源信息严重不足**是该论文在可复现性方面的一个明显短板。

## 五、实验数量与充分性

- **几何能力评估**：5 类协议（I–V），覆盖单物体、多物体、跨类别、连续比例、顺序分割，**结构较完整**。
- **物理能力评估**：通过 (训练集 × 评测集) 的 2×2 矩阵（ManiSkill/IntSim × 几何/物理）系统性地分离"几何 gap"与"物理 gap"，**实验设计巧妙**。
- **方向与比例泛化**：对 RDT 进行了左/右翻转、0.25↔0.75、0.5↔0.25 的多项迁移测试。
- **统计充分性**：每个配置 20 次随机种子试验，结果可重复性较好；但真实机器人实验样本极少（10 次）且仅限单一物品。
- **公平性**：所有基线采用相同 fine-tune 协议与相同的 Velocity Guardrail，未给任何模型额外力输入，**横向比较公平**。
- **不足**：未与 ForceVLA 等显式力条件策略对比；未在 RDT/Octo/OpenVLA 之外引入更多样化架构（如 π0、GR00T）；视觉域差距的量化讨论有限。

## 六、主要结论与发现

1. **Geometry Gap（几何鸿沟）**：
   - 多物体场景下，RDT 由 69% 降至 31%，Octo 由 42% 降至 17%，OpenVLA 由 51% 降至 28%。
   - 跨类别 leave-one-out 评测中，三者均有 8–25 个百分点的下降。
   - 连续比例切割（0.1–0.9）显示各模型对相邻比例鲁棒性差，Octo/OpenVLA 在中段比例上接近崩塌。
   - 顺序分割切（RDT）首刀成功率最高仅 30%（1/3 黄瓜），后续步骤几乎全部失败——表明拓扑变化下的长程几何推理能力缺失。
2. **Physics Gap（物理鸿沟）**：
   - 几何训练（ManiSkill）+ 几何评测（ManiSkill）：62%
   - 几何训练 + 物理评测（IntSim）：**23%**（严重塌陷）
   - 物理训练（IntSim）+ 物理评测：**59%**
   - 真实机器人：1/10 → 3/10
   - ➡️ **几何正确的轨迹未必能切断物体**，仅靠数据层面的物理接地即可显著缩小物理 gap。
3. **方向与比例对称性缺失**：左右翻转（如 0.25 ↔ 0.75）使 RDT 成功率从 55% 降至 20%；0.75→0.25 甚至降至 0%。
4. **接触力曲线验证**：去除基线后真实峰值力 ≈ 12.5 N，IntSim ≈ 12.0 N，**相对误差 < 5%**，时序归一化曲线吻合良好。

## 七、优点

- **问题新颖且重要**：首次将 VLA 评测下沉到非刚性切割这一接触丰富任务，弥补了数据集缺口。
- **仿真-真实闭环**：用真实 Franka F/T 测量验证 MPM 力曲线，是该类工作少有的**定量物理验证**。
- **数据层面而非架构层面的解决思路**：证明仅靠"物理接地的演示数据"即可显著提升切割成功率，避免了对 VLA 架构的侵入式改造，**工程友好**。
- **评测协议系统化**：将几何 gap 与物理 gap 通过 2×2 矩阵解耦，方法学上清晰。
- **数据规模与多样性**：15 类食材、15 个背景、5 种语言变体，1.57M 实例，覆盖面较广。
- **语言指令设计**：同时支持比例、方向、连续比例、顺序分割，对几何语言理解的覆盖较为细致。

## 八、不足与局限

- **算力资源披露不足**：未给出 GPU 型号、数量与训练时长，**可复现性受限**。
- **真实机器人实验规模过小**：仅 10 次试验、单一食材（香蕉/橙子），结论的统计强度有限。
- **材料模型简化**：MLS-MPM 未建模**粘弹性松弛（viscoelastic relaxation）**、**湿度依赖**、**粘附/纤维撕裂**等效应，与真实食品切割仍存在差距。
- **食物种类有限**：仅 15 种蔬果，未覆盖面包、肉类、奶酪等常见食材。
- **视觉 sim-to-real gap 未解决**：作者明确承认该 gap 仍存在，并提出与 Cosmos 等世界模型结合作为未来方向。
- **未与 ForceVLA 等显式力条件方法对比**：使得"数据层解决 vs 架构层解决"的相对优劣无法直接量化。
- **顺序分割测试**：仅在 RDT 上展开，未覆盖 Octo/OpenVLA，**比较不完整**。
- **缺少失败模式分析**：未深入讨论误切、多切、轨迹抖动等具体失败模式。

---

（完）
