---
title: "RoboTwin: Dual-Arm Robot Benchmark with Generative Digital Twins"
title_zh: RoboTwin：基于生成式数字孪生的双臂机器人基准
authors: "Mu, Yao, Chen, Tianxing, Chen, Zanxin, Peng, Shijia, Lan, Zhiqian, Gao, Zeyu, Liang, Zhixuan, Yu, Qiaojun, Zou, Yude, Xu, Mingkun, Lin, Lunkai, Xie, Zhiqiang, Ding, Mingyu, Luo, Ping"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Mu_RoboTwin_Dual-Arm_Robot_Benchmark_with_Generative_Digital_Twins_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 双臂机器人操纵基准与生成式数字孪生专家数据集
tldr: 多样化演示数据稀缺以及与真实环境对齐的评估基准不足，严重制约了双臂协调和复杂物体操纵研究。本文提出RoboTwin生成式数字孪生框架，利用3D生成基础模型和大语言模型，从单张2D图像生成多样化物体数字孪生，构建多样化专家数据集与真实对齐的评估平台。同时引入空间关系感知的代码生成方法，在多种双臂操纵任务上验证了平台有效性，为复杂操纵基准研究提供重要基础设施。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 813, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1609, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1711, \"height\": 508, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1010, \"height\": 373, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 582, \"height\": 385, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1550, \"height\": 484, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 790, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 903, \"height\": 293, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1630, \"height\": 971, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 785, \"height\": 377, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-mu-robotwin-dual-arm-robot-benchmark-with-generative-digital-twins-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 788, \"height\": 382, \"label\": \"Table\"}]"
motivation: 多样化演示数据稀缺且缺乏与真实对齐的评估基准，制约双臂操纵研究。
method: 利用3D生成模型和大语言模型构建数字孪生框架，自动生成多样化专家数据与评估场景。
result: 在多种双臂操纵任务上构建了真实对齐的基准与多样化演示数据集。
conclusion: 生成式数字孪生可有效解决双臂操纵数据稀缺和基准不足的问题。
---

## Abstract
In the rapidly advancing field of robotics, dual-arm coordination and complex object manipulation are essential capabilities for developing advanced autonomous systems. However, the scarcity of diverse, high-quality demonstration data and real-world-aligned evaluation benchmarks severely limits such development. To address this, we introduce RoboTwin, a generative digital twin framework that uses 3D generative foundation models and large language models to produce diverse expert datasets and provide a real-world-aligned evaluation platform for dual-arm robotic tasks. Specifically, RoboTwin creates varied digital twins of objects from single 2D images, generating realistic and interactive scenarios. It also introduces a spatial relation-aware code generation framework that combines object annotations with large language models to break down tasks, determine spatial constraints, and generate precise robotic movement code. Our framework offers a comprehensive benchmark with both simulated and real-world data, enabling standardized evaluation and better alignment between simulated training and real-world performance. We validated our approach using the open-source COBOT Magic Robot platform. Policies pre-trained on RoboTwin-generated data and fine-tuned with limited real-world samples demonstrate significant potential for enhancing dual-arm robotic manipulation systems by improving success rates by over 70% for single-arm tasks and over 40% for dual-arm tasks compared to models trained solely on real-world data.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "RoboTwin: Dual-Arm Robot Benchmark with Generative Digital Twins" (CVPR 2025). I need to organize it according to 8 specific points with hierarchical headings and bullet points in Markdown format, ending with "(完)".

Let me analyze the paper carefully:

1. **Core problem**: Lack of diverse demonstration data and real-world-aligned evaluation benchmarks for dual-arm robotic manipulation tasks.

2. **Methodology**: 
   - Generative digital twin framework using 3D generative foundation models (Deemos Rodin) and LLMs
   - From single 2D RGB image → GPT-4V description → variations via LLM → SDXL-Turbo generates 2D variations → 3D generation → textured 3D models
   - Spatial annotation framework: key points (function point, contact point) and axes (function axis, approach axis, lateral axis)
   - Feature point matching using Stable Diffusion encoder for transferring annotations across instances
   - Spatial relation-aware code generation: 6-step process (Scene Initialization, Task Decomposition, Constraint Inference, Robot Behavior Generation, Success Evaluation, Iterative Refinement)
   - Optimization formulation with screw motion planner

3. **Experiments**:
   - 15 tasks in benchmark (14 used for benchmarking, full list shown in Fig 5)
   - ManiSkill3 simulation environment
   - Cobot Magic Robot platform (4 arms, 4 Intel RealSense D-435 cameras)
   - Compared methods: DP3 (XYZ, XYZ+RGB), DP (2D Diffusion Policy)
   - Tested with 20, 50, 100 demonstrations

4. **Resources**: The paper mentions D-robotics for cloud computing and Deemos for 3D model support, but doesn't specify exact GPU types/numbers/training time.

5. **Experiment count and sufficiency**:
   - Real-world: 50 trials per task, multiple tasks
   - Tables 1, 2, 3 cover comprehensive comparisons
   - Real-to-sim experiments
   - 3 seeds for benchmarking

6. **Main conclusions**:
   - 70%+ improvement for single-arm, 40%+ for dual-arm
   - Sim-to-real gap can be bridged
   - DP3 better few-shot, DP better with more data
   - RGB integration is inconsistent

7. **Strengths**:
   - End-to-end pipeline from single image to deployment
   - Real-to-sim alignment
   - Comprehensive benchmark
   - Validates sim-to-real transfer

8. **Limitations**:
   - Poor performance on complex dual-arm coordination tasks
   - RGB+point cloud fusion not consistent
   - Limited to certain object types
   - 300 simulation data needed as hyperparameter

Let me structure this properly in Chinese.
</think>
# RoboTwin 论文总结

## 1. 核心问题与研究背景

- **研究领域**：双臂机器人的协调操作与复杂物体操控，这是医疗、制造、物流、家用辅助等场景实现高级自主系统的关键能力。
- **核心痛点**：
  - 多样化、高质量的演示数据极度稀缺；
  - 缺乏与真实世界对齐的评估基准。
- **现有方法的局限**：
  - 人工遥操数据成本高、耗时长、难以覆盖多样化场景；
  - 仿真中算法轨迹生成器需要任务专属设计，可扩展性差；
  - MimicGen、RoboCaca 等基于固定场景预设，难以应对任务变体；
  - 现有基准多关注单臂或分离双臂任务（如 Peract2、HumanoidBench、BiGym），缺乏集成双臂系统的统一标准。

## 2. 方法论

### 2.1 整体框架
提出 **RoboTwin 生成式数字孪生框架**，核心由三部分组成：
1. 多样化数字资产生成（Real→Sim）；
2. 空间感知标注框架；
3. 基于 LLM 的专家数据自动生成。

### 2.2 多样化数字资产生成（Real-to-Sim）
- 工具：**Deemos Rodin** 3D 生成基础模型；
- 流程：
  1. 拍摄真实物体 2D RGB 图像；
  2. 使用 **GPT-4V** 分析图像生成描述；
  3. 利用语言模型衍生出"形似而不同"的描述变体；
  4. 结合 **SDXL-Turbo** 生成多样化的 2D 图像集；
  5. 输入图像条件 3D 生成模型，输出包含几何、表面法线、线框和纹理的 3D 资产；
- 质量验证：通过 **UCLIP-I** 相似度 + GPT-4V 视觉双验证；
- 物理保真：GPT-4V 分类物体材质，并附以 ±5% 随机扰动的物理参数。

### 2.3 空间标注框架
- **关键点**：
  - 功能点（Point for Function）：工具的主要功能位置（如锤头击打面）；
  - 接触点（Point for Contact）：人与工具或其他物体的交互区域。
- **三类轴**：
  - 功能轴（Function Axis）：功能执行方向；
  - 接近轴（Approach Axis）：接近目标的方向；
  - 侧向轴（Lateral Axis）：与上述两轴垂直的第三维方向。
- **跨实例标注迁移**：使用 Stable Diffusion 编码器在俯视图下做特征点匹配，将同一类物体的标注迁移到不同 3D 实例，避免重复标注。

### 2.4 空间感知专家数据生成（基于 LLM）
- **双臂系统能力**：
  - 螺旋运动插值 + 协同夹爪 → 同步双臂；
  - 独立双臂动作；
  - 连续安全中间位姿调整 → 动态避碰。
- **三阶段流程**：
  1. 空间约束推理（从物体标注建立几何关系）；
  2. LLM 生成可执行代码（使用 MPlib 轨迹优化库）；
  3. 执行验证（含自纠错反馈机制）。
- **六步生成管线**：
  1. 场景初始化；
  2. 任务分解（LLM 拆解为子任务）；
  3. 约束推理（每个子任务推导功能点-轴关系、接触姿态、目标对齐等）；
  4. 机器人行为生成（调用 API 生成代码）；
  5. 成功评估；
  6. 迭代优化（错误信息反馈给 LLM 重生成）。
- **核心优化问题**：
  - 目标：最小化代价函数 $J(\theta(t))$；
  - 约束：
    - 运动学：$T_{ee} = f_{FK}(\theta(t))$；
    - 位姿对齐：$P_{ee} = P_o - d \cdot \vec{a}_o$，$\vec{n}_{ee} = \vec{a}_o$；
    - 碰撞规避：$\theta(t) \in C, \forall t \in [t_0, t_f]$。

## 3. 实验设计

### 3.1 基准与平台
- **仿真环境**：ManiSkill3（基于 SAPIEN 的 GPU 加速平台）；
- **真实平台**：COBOT Magic 开源机器人（4 条机械臂 + 4 个 Intel RealSense D-435 RGBD 相机），搭载于 Tracer 底盘；
- **基准任务数**：15 个（表 1 测试了 14 个），涵盖单臂/双臂任务，例如：block_hammer_beat、block_handover、blocks_stack、mug_hanging、pick_apple_messy、shoes_place、dual_bottles_pick 等；
- **数据规模**：每个任务提供 100 组仿真数据 + 20 组真实遥操数据；
- **数据形式**：每帧包含前/左/右 3 个相机视角的 RGB 与深度图、点云、机械臂关节与末端位姿。

### 3.2 对比方法
- **2D Diffusion Policy (DP)**：基于 2D 视觉信息；
- **3D Diffusion Policy (DP3)**：基于点云，测试两种输入模态：
  - DP3 (XYZ)：仅几何；
  - DP3 (XYZ+RGB)：几何 + 颜色。

### 3.3 评估设定
- 演示规模：20 / 50 / 100 个专家样本；
- 每个任务在 3 个随机种子下评估；
- 真实世界每个任务进行 50 次试验，初始位姿随机化。

## 4. 资源与算力

- **致谢中提到**：
  - D-robotics 提供云算力支持；
  - Deemos 提供 3D 生成模型支持。
- **未明确披露**：具体的 GPU 型号与数量、训练时长、3D 资产生成数量级、LLM 调用次数等关键算力细节均**未在论文中明确说明**。
- 仅可推断：3D 生成依赖商业平台 Rodin，LLM 推断使用 GPT-4V，可能为多节点云端并行（无明确证据）。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 仿真中 14 个任务 × 3 种方法 × 3 种数据规模 × 3 个随机种子 ≈ 378 组配置；
  - 真实环境 5 个单臂任务 + 5 个双臂任务，每任务 50 次试验；
  - 数据规模缩放实验（图 7）；
  - 定性代码生成成功率（图 5）。
- **优点**：
  - 任务类型多样，覆盖同步、交接、避碰等双臂模式；
  - 同时进行 sim-to-real 迁移验证；
  - 3 个随机种子提供统计可靠性。
- **不足**：
  - 缺少消融实验（如：去除空间标注、去除 LLM 分解、去除 3D 生成变化等模块的对比）；
  - 缺乏与其他生成式数据框架（MimicGen、RoboCaca）的直接基准对比；
  - 每个任务 100 组仿真数据是否充足、300 组预训练数据作为超参的选取依据仅来自图 7 经验值。

## 6. 主要结论与发现

- **Sim-to-Real 迁移效果显著**：
  - 单臂任务：300 仿真 + 20 真实样本预训练 → 真实任务平均成功率从 1.2% 提升至 72%（提升 70%+）；
  - 双臂任务：平均成功率从 20% 提升至 62%（提升 40%+）。
- **方法对比**：
  - DP3 表现出色的少样本学习能力（20 样本下即可达到较高成功率），但扩展性受限，100 样本时性能不升反降；
  - DP 在数据充足时扩展性更强，如 Dual Bottles Pick (Easy) 从 1.7% → 85.7%；
  - RGB+点云融合效果不一致，部分任务提升明显（如 Pick Apple Messy），部分任务下降。
- **任务复杂度影响**：
  - 简单双臂操作（如 Dual Bottles Pick）成功率高；
  - 复杂协调任务（如 Dual Shoes Place）所有方法均低于 15%。
- **关键瓶颈**：当前模仿学习算法在双臂紧密协调任务上仍存在明显局限。

## 7. 优点与方法亮点

- **端到端 Real-to-Sim 管线**：仅需单张 RGB 图像即可生成多样化 3D 资产，门槛低；
- **空间关系感知 + LLM 代码生成**：将物体功能/接近/侧向轴以及功能/接触点编码为可被 LLM 理解的语义结构，显著超越 Rekep 等仅基于关键点的方法；
- **跨实例标注迁移**：利用 Stable Diffusion 特征做对应匹配，避免同类物体重复标注；
- **双臂系统能力齐备**：同步、独立、动态避碰三种模式覆盖真实协调需求；
- **包含自纠错机制**：执行错误反馈给 LLM 形成闭环；
- **基准开源且覆盖真实-仿真对齐**：硬件配置严格一致，便于公平比较；
- **真实平台验证充分**：在 COBOT Magic 上完成 sim-to-real 验证，提供了可复现的工程范式。

## 8. 不足与局限

- **算力与训练细节不透明**：未报告 GPU 型号/数量、训练耗时、生成数据量级，难以评估生成成本与可复现性；
- **复杂双臂任务表现差**：双鞋放置等需要紧密协调的任务所有方法均 <15%，说明算法在双手机巧协作上仍有显著空白；
- **多模态融合效果不稳定**：DP3 (XYZ+RGB) 在不同任务上表现差异大，缺少对融合策略的深入分析；
- **3D 生成依赖第三方商业平台**：Rodin 闭源，资产多样性与可扩展性受限于外部服务；
- **评估指标单一**：以成功率为主，缺少对效率、鲁棒性、抗干扰能力等多维度的细致评估；
- **样本规模偏小**：每个任务仅 20-100 个演示样本，模型泛化性的结论可能受数据量限制；
- **基准偏差风险**：任务以桌面 pick-and-place 类为主，对更复杂的操作（如柔性物体、工具使用长序列、动态环境）覆盖不足；
- **缺乏消融实验**：各核心模块（3D 生成、空间标注、LLM 分解、避碰规划）对最终贡献的量化分析不充分。

（完）
