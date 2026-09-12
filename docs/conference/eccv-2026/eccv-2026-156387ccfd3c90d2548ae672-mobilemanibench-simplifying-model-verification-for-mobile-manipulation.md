---
title: "MobileManiBench: Simplifying Model Verification for Mobile Manipulation"
title_zh: "MobileManiBench:简化移动操作模型验证的基准平台"
authors: "Wenbo Wang, Fangyun Wei, Qixiu Li, Xi Chen, Yaobo Liang, Chang Xu, Jiaolong Yang, Baining Guo"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4170.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向移动操作VLA架构的仿真基准
tldr: "视觉-语言-动作模型推动机器人操作进步,但仍依赖以静态桌面场景为主的远程操作数据集。本文提出基于NVIDIA Isaac Sim的仿真优先框架,用于在实际部署前验证VLA架构。MobileManiBench自主生成多样化的移动操作轨迹,提供语言指令、多视角RGB-深度-分割图像、状态动作同步等丰富标注。该基准支持两种移动平台与多种机器人构型,为VLA模型评估提供可复现平台,填补了移动操作基准的关键空白。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-156387ccfd3c90d2548ae672/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 4224, \"height\": 2304}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-156387ccfd3c90d2548ae672/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 1775, \"height\": 1124}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-156387ccfd3c90d2548ae672/fig-003.webp\", \"caption\": \"\", \"page\": 8, \"index\": 3, \"width\": 1413, \"height\": 1120}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-156387ccfd3c90d2548ae672/fig-004.webp\", \"caption\": \"\", \"page\": 9, \"index\": 4, \"width\": 2932, \"height\": 1710}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-156387ccfd3c90d2548ae672/fig-005.webp\", \"caption\": \"\", \"page\": 10, \"index\": 5, \"width\": 1452, \"height\": 539}]"
motivation: "现有VLA模型验证依赖静态桌面远程操作数据,缺乏面向移动操作的标准化基准。"
method: "基于Isaac Sim构建仿真优先框架,自动生成多样化移动操作轨迹并提供多模态标注。"
result: "建立支持双移动平台的大规模移动操作基准,实现VLA架构部署前的可复现评估。"
conclusion: "填补移动操作基准空白,为通用VLA策略的标准化验证提供重要基础设施支撑。"
---

## Abstract
Vision-language-action models have advanced robotic ma-nipulation but remain constrained by reliance on the large, teleoperation-collected datasets dominated by the static, tabletop scenes. We propose asimulation-first framework to verify VLA architectures before real-worlddeployment and introduce MobileManiBench, a large-scale benchmarkfor mobile-based robotic manipulation. Built on NVIDIA Isaac Sim andpowered by reinforcement learning, our pipeline autonomously gener-ates diverse manipulation trajectories with rich annotations (languageinstructions, multi-view RGB–depth–segmentation images, synchronizedobject/robot states and actions). MobileManiBench features 2 mobileplatforms (parallel-gripper and dexterous-hand robots), 2 synchronizedcameras (head and right wrist), 630 objects in 20 categories, 5 skills(open, close, pull, push, pick) with over 100 tasks performed in 100 re-alistic scenes, yielding 300K trajectories. This design enables controlled,scalable studies of robot embodiments, sensing modalities, and policy ar-chitectures, accelerating research on data efficiency and generalization.We benchmark representative VLA models and report insights into per-ception, reasoning, and control in complex simulated environments, withall code, datasets, and models publicly released at our project website:https://dexhand.github.io/MobileManiBench/.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "MobileManiBench: Simplifying Model Verification for Mobile Manipulation" organized into 8 specific sections. Let me carefully analyze the paper content and structure my response accordingly.

Key information from the paper:
1. Core problem: VLA models rely on teleoperation datasets with static tabletop scenes, lacking benchmarks for mobile manipulation
2. Method: Simulation-first framework using NVIDIA Isaac Sim + RL to generate diverse manipulation trajectories
3. Benchmark features: 2 mobile robots (G1 with gripper, XHand with dexterous hand), 630 objects, 20 categories, 5 skills, 100+ tasks, 100 scenes, 300K trajectories
4. Resources: 32 V100 GPUs (RL training), 8 A6000 GPUs (data generation), 8 B200 GPUs (VLA training)
5. Experiments: Multiple ablations on image inputs, state inputs, seen/unseen objects/scenes, comparisons with OpenVLA, CogACT, π0, π0.5
6. Main findings: 8 takeaways covering structure-complexity, generalization challenges, dexterous hand trade-offs, multi-view importance, etc.
7. Limitations: Not extensively discussed in the paper, but I can identify some

Let me write a comprehensive Chinese summary following the requested format.</think>

# MobileManiBench 论文总结

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（VLA）模型近年来在机器人操作领域取得显著进展，但其训练高度依赖大规模远程操作数据集（如 Open X-Embodiment），且这些数据大多采集自固定基座、第三视角的静态桌面场景。
- **核心痛点**：
  - 硬件改动（如增加腕部相机、深度相机、夹爪换成灵巧手、加入移动底盘）需要重新采集数据，成本高昂且迭代效率低。
  - 远程操作难以扩展到灵巧手或移动平台，限制了 VLA 模型的快速验证与迭代。
- **研究目标**：在真实数据采集之前，先在仿真环境中完成数据生成与模型验证，提供一种可扩展、可控的方案，支持多样化机器人构型、传感模态和任务场景。

## 2. 方法论

### 2.1 整体框架：仿真优先的两阶段流水线

1. **MobileManiRL 训练阶段**：为每一个「机器人-物体-技能」三元组合训练一个统一的基于状态（state-based）的强化学习策略。
2. **MobileManiDataset 生成阶段**：将训练好的 RL 策略部署到多个真实场景中，自动生成成功操作的轨迹数据。
3. **MobileManiVLA 训练阶段**：基于生成的数据集，训练通用 VLA 模型。

### 2.2 移动机器人构型

- **G1 机器人**（AGIBOT）：并联夹爪，7 维动作（6 维腕部位移 + 1 维夹爪）。
- **XHand 机器人**（RobotEra）：12 自由度灵巧手，18 维动作（6 维腕部位移 + 12 维手指关节）。
- 两个机器人均配备 2 自由度移动底盘（绕 z 轴旋转 + 沿 y 轴平移），双臂中只激活右臂。

### 2.3 MobileManiRL 关键技术细节

- **输入**：时间嵌入、物体状态（抓取点+目标点）、机器人本体感知、机器人-物体距离、上一时刻动作。G1 总维度 ~146，XHand 总维度 ~223。
- **网络**：4 层 MLP（隐藏维度 1024/1024/512/512）+ 动作头 + 同构的价值网络。
- **奖励函数**：

$$R = R_d + (1 - f_g) R_a + f_g (R_g + R_m + R_s)$$

其中 $R_d$ 为全局距离奖励，$R_a$ 为接近动作奖励，$f_g$ 为抓取标志（距离低于阈值置 1），$R_g$、$R_m$、$R_s$ 分别为抓取、移动、成功奖励。任务成功条件：抓取点在 300 步内到达目标点。
- **关键点参数化**：用「机器人手部关键点-物体抓取点-目标点」之间的相对位移统一参数化所有任务。
- **简化场景训练**：把所有物体归类到「地面场景」和「桌面场景」两类，1,182 个机器人-物体-技能组合训练，G1 平均成功率 89.6%，XHand 平均成功率 92.9%。

### 2.4 MobileManiVLA 模型架构

- **视觉模块**：SigLIP 编码器处理头部与腕部 RGB-D 图像（224×224）。
- **语言模块**：指令形式为「<技能> <物体>」（如 "open faucet"），由 Gemma-2 处理。
- **动作模块**：基于 DiT（扩散 Transformer）的动作模块，输入为噪声动作序列、认知特征 $f_c$、腕部状态特征 $f_s$，采用 MSE 损失训练：

$$L_{MSE} = \mathbb{E}_{\epsilon \sim \mathcal{N}(0,1), i} \|\hat{\epsilon}_i - \epsilon\|^2$$

- **推理策略**：每次预测 N=16 步动作块，使用 K=4 的自适应集成（CogACT 风格）。

## 3. 实验设计

### 3.1 数据集与场景

- **物体**：630 个独特物体，跨 20 类（来自 PartNet-Mobility、UniDoorManip、YCB）。
- **技能**：open / close / pull / push / pick，共 5 项。
- **任务**：100+ 任务。
- **场景**：100 个真实感场景（厨房、卧室、医院、办公室、仓库、停车场等），80 个用于训练，20 个用于测试。
- **轨迹**：300K 条轨迹（每条平均 160 帧，30 FPS），每条包含语言指令、头/腕 RGB-深度-分割图像、物体/机器人状态、动作。
- **训练/测试划分**：训练用 506 物体 + 80 场景，测试用 124 未见物体 + 20 未见场景，共 15,232 vs 920 个机器人-物体-技能-场景组合。

### 3.2 对比方法

- **RL 基线**：MobileManiRL（自身）
- **VLA 模型对比**：OpenVLA (7B)、CogACT (7B)、π₀ (3B)、π₀.₅ (3B)、MobileManiVLA (3B)

### 3.3 消融维度

- 图像输入：head RGB / head depth / wrist RGB / wrist depth 的不同组合
- 状态输入：腕部位姿、抓取点、目标点
- 物体/场景泛化：见过 vs 未见过
- 基座：固定 vs 移动

## 4. 资源与算力

| 阶段 | GPU 配置 | 训练时长 |
|---|---|---|
| MobileManiRL 训练 | 32 × NVIDIA V100（1,024 并行仿真环境，lr=1e-3，4K iterations） | 每机器人约 4 天 |
| MobileManiDataset 生成 | 8 × NVIDIA RTX A6000 | 每机器人约 6 天 |
| MobileManiVLA 训练 | 8 × NVIDIA B200（batch=480，lr=2e-5，320K iterations） | 每机器人约 12 天 |

- 仿真平台：NVIDIA Isaac Sim。
- 数字资产来源：Isaac Sim 自带 + Genie Sim。
- 论文未明确说明总成本，但训练单个机器人的完整流水线需 V100 + A6000 + B200 合计约 22 天。

## 5. 实验数量与充分性

- **主实验**：图 5 展示 20 类物体 × 5 个技能的成功率，表 3 汇总 G1 与 XHand 在 5 项技能上的均值。
- **消融实验**：表 4（图像输入与状态输入各 4 组）、表 5（4 组可见性矩阵）、表 7（固定 vs 移动基座）。
- **模型对比实验**：表 6（5 个 VLA 模型）。
- **RL 评估**：每个组合 1,024 episodes；VLA 评估：每个未见组合 10 episodes。
- **总体充分性**：
  - 实验维度较丰富，覆盖了输入模态、状态信息、泛化性、机器人构型等多个维度。
  - VLA 评估样本量（每组合 10 episodes）相对偏少，统计置信度有限。
  - 消融实验仅在 G1 子集（272 训练 / 66 测试物体）上进行，结论推广到 XHand 上需谨慎。
  - 缺少与其他专用移动操作数据集（如 Humanoid Everyday、Mobile ALOHA）的直接对比，且只做了仿真内评估，真实世界泛化证据有限。

## 6. 主要结论与发现（论文 8 条 Takeaway）

- **Takeaway 1**：物体结构与技能复杂度共同决定性能方差。简单铰接物体（马桶盖、笔记本、洗碗机）较易处理，需精确把手定位的（车门、桌腿）难度更大；open/pull/pick 因需要稳定抓取比 close/push 更难。
- **Takeaway 2**：从显式状态观测转向隐式感知输入后，VLA 模型的泛化性能出现明显下降，但带来了向未见物体/场景的真实泛化能力。
- **Takeaway 3**：灵巧手提升 RL 策略的精度（92.9% vs 89.6%），但在 VLA 阶段与并联夹爪持平（57.3% vs 56.7%）；手指与物体表面的碰撞会降低 open/pull 表现，但能改善 pick 物体的力封闭抓取。
- **Takeaway 4**：多视角多模态视觉输入对泛化至关重要。仅头部 RGB 仅 7.9%，加深度/腕部 RGB 提升至 14.1%/14.9%，组合 RGB-D + 头/腕双视角达 28.2%。
- **Takeaway 5**：腕部状态与粗略物体空间先验（首帧抓取点/目标点）进一步提升性能，从 22.4% 提升至 36.6%。
- **Takeaway 6**：未见物体比未见场景更难泛化：双未见 28.2%、未见物体-见场景 39.2%、见物体-未见场景 51.3%、双可见 59.6%。
- **Takeaway 7**：MobileManiBench 提供统一平台下不同 VLA 模型的可比基线，OpenVLA、CogACT、π₀、π₀.₅、MobileManiVLA 分别为 4.5%、6.8%、11.2%、18.8%、28.2%。
- **Takeaway 8**：底盘移动能力对超越桌面的操作至关重要。固定基座时 MobileManiRL 成功率从 82.8% 跌至 25.4%。

## 7. 论文亮点

- **首创性**：针对移动操作（含移动底盘 + 灵巧手 + 腕部视角）提供大规模、统一的仿真基准，填补了当前 VLA 研究的空白。
- **自动数据生成流水线**：用统一 RL 策略 + 关键点参数化 + 通用奖励，避免了为每个任务手动设计策略，使 300K 轨迹可扩展生成。
- **多维度可控变量**：同一基准同时支持机器人构型（并联夹爪 vs 灵巧手）、传感模态（RGB/Depth）、输入组合、可见性划分的对照实验。
- **多模态标注丰富**：每条轨迹同时包含语言指令、RGB-D-分割图像、状态、动作，便于多种模态融合研究。
- **完全开源**：代码、数据集、模型全部公开，且兼容 Open X-Embodiment 类已有 VLA 训练范式。
- **统一评估协议**：在仿真内可直接对比 OpenVLA、CogACT、π₀、π₀.₅ 等多个模型，提供了基线参考。

## 8. 不足与局限

- **仅仿真评估**：缺少真实机器人的对比实验（仅在附录中展示了 MobileManiVLA 的真实世界推理片段，无系统性真实部署报告），sim-to-real 差距未充分论证。
- **任务偏重铰接物体**：open/close 类任务占主导，而 pick 类（YCB 整体物体）多样性不足；缺少长时序、多步骤组合任务。
- **左臂始终闲置**：两个机器人都固定左臂只用右臂，限制了双臂协调操作的研究。
- **评估样本量偏小**：每个未见组合仅 10 episodes，统计波动可能较大，且 RL 与 VLA 的评估协议不一致（1,024 vs 10）。
- **消融范围有限**：表 4-7 的消融只在 G1 机器人和子集任务（open/pull/pick）上进行，对 XHand 灵巧手的结论外推需要额外验证。
- **数据分布偏差**：物体来自 PartNet-Mobility、UniDoorManip、YCB，偏向家庭/厨房场景，对户外、工业等场景覆盖有限。
- **计算成本高**：训练单个机器人需 V100/A6000/B200 组合约 22 天，对中小研究团队复现门槛较高。
- **未见场景定义模糊**：仅在场景布局层面划分「未见」，物体类别本身仍属训练分布，难以完全验证长尾开放世界泛化能力。
- **缺少失败分析**：论文主要报告成功率，对失败模式（如指尖碰撞、底盘导航误差、指令歧义）的诊断较少。

（完）
