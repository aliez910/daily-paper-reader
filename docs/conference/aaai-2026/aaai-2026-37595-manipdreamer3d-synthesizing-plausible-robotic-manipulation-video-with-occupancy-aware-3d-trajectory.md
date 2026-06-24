---
title: "ManipDreamer3D: Synthesizing Plausible Robotic Manipulation Video with Occupancy-aware 3D Trajectory"
title_zh: "ManipDreamer3D: 基于占用感知3D轨迹合成合理机器人操控视频"
authors: "Ying Li, Xiaobao Wei, Xiaowei Chi, Yuming Li, Zhongyu Zhao, Hao Wang, Ningning Ma, Ming Lu, Sirui Han"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37595/41557"
tags: ["query:rob-il"]
score: 7.0
evidence: 通过3D轨迹规划和扩散模型生成机器人操控视频数据
tldr: 为解决机器人操控领域数据稀缺的问题，提出了ManipDreamer3D框架，通过结合3D轨迹规划与占用感知重建，从单张图片和文本指令生成合理的3D操控视频。该方法利用扩散模型合成视频，克服了传统2D轨迹的空间歧义性。实验证明生成的视频能有效扩充训练数据，提升下游操控模型的性能，为机器人操控数据增强提供了新途径。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1611, \"height\": 755, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1249, \"height\": 821, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 808, \"height\": 603, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1645, \"height\": 806, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 804, \"height\": 1505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 847, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37595/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 687, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37595/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 869, \"height\": 232, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37595/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1613, \"height\": 362, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37595/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1827, \"height\": 332, \"label\": \"Table\"}]"
motivation: 机器人操控数据稀缺，现有合成方法因2D轨迹空间歧义而效果欠佳。
method: 结合3D轨迹规划与占用感知重建，通过扩散模型生成3D感知的操控视频。
result: 生成的视频在真实感和多样性上优于现有方法，且能提升下游模型性能。
conclusion: ManipDreamer3D有效缓解了数据瓶颈，对机器人操控研究有重要价值。
---

## Abstract
Data scarcity continues to be a critical bottleneck in the field of robotic manipulation, limiting the ability to train robust and generalizable models. While diffusion models provide a promising approach to synthesizing realistic robotic manipulation videos, their effectiveness hinges on the availability of precise and reasonable control instructions. Current methods primarily rely on 2D trajectories as instruction prompts, which inherently face issues with 3D spatial ambiguity. 
    In this work, we present a novel framework named ManipDreamer3Dfor generating plausible 3D-aware robotic manipulation videos from the input image and the text instruction. Our method combines 3D trajectory planning with a reconstructed 3D occupancy map created from a third-person perspective, along with a novel trajectory-to-video diffusion model. 
    Specifically, ManipDreamer3D first reconstructs the 3D occupancy representation from the input image and then computes an optimized 3D end-effector trajectory, minimizing path length, avoiding collisions and retiming. Next, we employ a latent editing technique to create video sequences from the initial image latent, text instruction and the optimized 3D trajectory. This process conditions our specially trained trajectory-to-video diffusion model to produce robotic pick-and-place videos. Our method significantly reduces human intervention requirements by autonomously planing plausible 3D trajectories. Experimental results demonstrate its superior visual quality and precision.

---

## 论文详细总结（自动生成）

### 1. 核心问题与整体含义（研究动机与背景）
- **研究动机**：机器人操控领域面临严重的数据稀缺问题，收集真实世界演示耗时、劳动密集、受硬件限制，阻碍了策略模型的可扩展性与泛化能力。
- **背景问题**：现有基于扩散模型的视频合成方法使用2D轨迹作为控制指令，存在固有的3D空间歧义性；生成的视频常常违反物理约束、缺乏碰撞规避，且需要大量手动标注对象。

### 2. 方法论
- **核心思想**：从单张第三视角图像和文本指令出发，先重建3D占用表示，在占用空间中规划优化的3D末端执行器轨迹（兼顾短路径、平滑、无碰撞），再将轨迹参数化为2D掩码序列，通过潜在编辑技术将轨迹条件注入扩散模型，生成连贯的操控视频。
- **关键技术细节**：
  - **3D占用重建**：使用VGGT从单视图点云 → 神经表面重建 → 稠密化 → 离散化为 64×64×64 占用网格。
  - **轨迹规划**：
    - 三阶段（接近、操作、回退）分别用A*初始化。
    - 基于CHOMP的多目标优化：碰撞损失（SDF）、路径长度、加速度平滑、曲率平滑，损失加权后使用Adam优化。
    - 路径感知时间重分配：根据子轨迹长度重新分配点，并按照正弦速度曲线插值，使速度分布更符合物理规律。
  - **轨迹数据整理**（用于训练）：
    - 用VGGT重建全视频序列的3D场景。
    - 用YOLO检测夹爪手指→映射到3D坐标。
    - 用LLM解析指令→Qwen-VL视觉定位→SAM分割对象掩码。
  - **轨迹引导视频合成**：
    - 3D轨迹投影为2D圆形掩码（球体模型+透视投影）。
    - 潜在编辑：保留第一帧潜在，后续帧在掩码区域覆盖对象/夹爪的池化潜在，构造动态潜在视频。
    - 条件生成：将构造的潜在直接沿通道维拼接噪声潜在（UNet），或先进行2倍时间平均池化（DiT），无需额外控制模块。

### 3. 实验设计
- **数据集**：bridge V1 + bridge V2，经数据整理得到8700个有效episode，按9:1划分训练/测试。
- **Benchmark与指标**：视频质量（FVD, PSNR, SSIM）、VBench六项指标、轨迹误差（机器人/物体分别计算）。
- **对比方法**：
  - SVD架构下：DragAnything、This&That。
  - DiT架构下：RoboMaster。
  同时报告本方法两个版本：ManipDreamer3D(SVD) 和 ManipDreamer3D(DiT)。

### 4. 资源与算力
- 文中未明确说明使用的GPU型号、数量或训练时长，因此无法总结具体算力投入。

### 5. 实验数量与充分性
- **实验组数**：
  - 表2：视频质量与轨迹误差对比（5种方法+5项指标）。
  - 表3：VBench指标对比（5种方法+6项指标）。
  - 图5：定性比较（与This&That）。
  - 图6：轨迹优化消融（优化vs未优化）。
  - 图7：精确操控控制演示（不同接触点）。
- **充分性评价**：实验覆盖了主流视频生成和机器人操控基线、两种骨干架构、多个指标维度，并包含关键设计消融。数据集较为单一（仅bridge），但场景内多样性足够；缺乏跨数据集/跨机器人泛化测试。整体实验设计客观公平，但在消融深度（如各损失分量贡献）和更广泛场景验证上可进一步补充。

### 6. 主要结论与发现
1. 在SVD和DiT两种骨干下，ManipDreamer3D在所有视频质量指标上均优于此前最优方法，同时显著降低轨迹误差。
2. 占用感知的3D轨迹规划能自动生成安全、平滑、物理合理的路径，相比直接使用未优化轨迹，可避免碰撞等不可行行为。
3. 提出的潜在编辑融合方法可无缝适配不同扩散架构，无需额外参数模块即实现精确的轨迹控制。
4. 方法支持关键点、完整轨迹、affordance三级控制，且减少人工标注需求。

### 7. 优点
- **方法创新**：首次在机器人视频生成中结合占用重建与3D轨迹规划，解决2D控制的空间歧义。
- **控制粒度**：同时控制末端执行器和物体轨迹，并支持affordance级别条件。
- **实现轻量**：潜在编辑方案无额外参数，兼容UNet和DiT，易于集成。
- **自动化程度高**：从图像到视频全流程无需手工标注对象位置或轨迹点。

### 8. 不足与局限
- **规划假设**：当前仅针对刚体、准静态抓取，未考虑非刚体变形、接触力等。
- **场景与任务覆盖**：仅在bridge数据集（桌面操控）上评估，未验证在工厂、医疗等不同环境或长序列任务上的泛化能力。
- **数据依赖**：训练数据依赖大量预处理（点云重建、检测分割），可能引入噪声与误差。
- **对比公平性**：部分基线如DragAnything、This&That未提供最优配置下的重现结果，可能低估其性能。
- **资源信息缺失**：未报告训练算力，不利于复现和横向效率比较。
- **消融分析**：缺少对各损失权重、网格分辨率、时间重分配策略等参数的全面分析。

（完）
