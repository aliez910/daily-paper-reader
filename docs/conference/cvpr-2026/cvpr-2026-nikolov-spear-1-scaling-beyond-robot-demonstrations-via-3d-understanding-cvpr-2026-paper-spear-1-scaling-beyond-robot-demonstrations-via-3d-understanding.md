---
title: "SPEAR-1: Scaling Beyond Robot Demonstrations via 3D Understanding"
title_zh: SPEAR-1：通过三维理解扩展超越机器人演示的规模
authors: "Nikolov, Nikolay, Albanese, Giuliano, Dey, Sombit, Yanev, Aleksandar, Van Gool, Luc, Zaech, Jan-Nico, Paudel, Danda Pani"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Nikolov_SPEAR-1_Scaling_Beyond_Robot_Demonstrations_via_3D_Understanding_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用机器人基础模型，通过3D理解扩展至演示之外的泛化能力
tldr: 现有机器人基础模型多基于二维图像语言预训练的VLM，缺乏三维空间推理能力。本文认为这是其难以跨环境、任务和本体泛化的瓶颈。SPEAR-1通过为非机器人图像补充三维标注，并将三维理解能力注入预训练VLM，避免依赖大规模机器人数据。该工作为通用型机器人基础模型的扩展提供了更具可扩展性的三维接地路径。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1831, \"height\": 542, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 852, \"height\": 594, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1751, \"height\": 605, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1622, \"height\": 550, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1624, \"height\": 537, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1798, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 161, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-nikolov-spear-1-scaling-beyond-robot-demonstrations-via-3d-understanding-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 158, \"label\": \"Table\"}]"
motivation: 通用机器人基础模型因依赖2D VLM而缺乏3D空间推理，泛化能力受限。
method: 为非机器人图像添加3D标注，并将3D理解能力注入预训练VLM以提升泛化。
result: 在跨环境、任务与本体的设置下获得优于现有RFM的泛化表现。
conclusion: 该工作证明3D接地是扩展通用机器人基础模型的关键路径。
---

## Abstract
Robotic Foundation Models (RFMs) hold great promise as generalist, end-to-end systems for robot control.Yet their ability to generalize across new environments, tasks, and embodiments remains limited.We argue that a major bottleneck lies in their foundations: most RFMs are built by fine-tuning internet-pretrained Vision-Language Models (VLMs).However, these VLMs are trained on 2D image-language tasks and lack the 3D spatial reasoning inherently required for embodied control in the 3D world.Bridging this gap directly with large-scale robotic data is costly and difficult to scale.Instead, we propose to enrich easy-to-collect non-robotic image data with 3D annotations and enhance a pretrained VLM with 3D understanding capabilities.Following this strategy, we train SPEAR-VLM, a 3D-aware VLM that infers object coordinates in 3D space from a single 2D image.Building on SPEAR-VLM, we introduce our main contribution, SPEAR-1: a robotic foundation model that integrates grounded 3D perception with language-instructed embodied control.Trained on ~45M frames from 24 Open X-Embodiment datasets, SPEAR-1 outperforms or matches state-of-the-art models such as \pi_0-FAST and \pi_ 0.5 , while it uses 20xfewer robot demonstrations.This carefully-engineered training strategy unlocks new VLM capabilities and as a consequence boosts the reliability of embodied control beyond what is achievable with only robotic data.We make our model weights and 3D-annotated datasets publicly available.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "SPEAR-1: Scaling Beyond Robot Demonstrations via 3D Understanding" following a specific structure. Let me analyze the paper carefully and provide a comprehensive, well-organized response.

Key points from the paper:
1. The paper addresses the limitation of existing Robot Foundation Models (RFMs) that rely on 2D VLMs and lack 3D spatial reasoning.
2. They propose SPEAR-VLM (a 3D-aware VLM) and SPEAR-1 (a robot foundation model).
3. They use MoGe depth encoder, integrate with PaliGemma VLM.
4. Training: ~45M frames from 24 Open X-Embodiment datasets, with 20× fewer robot demonstrations.
5. Experiments on WidowX (Bridge) and Franka (DROID) platforms.
6. Comparison with OpenVLA, π0-FAST, π0.5, SpatialVLA.

Let me organize this into the requested format.</think>

# SPEAR-1 论文总结

## 一、核心问题与研究动机

- **关键瓶颈**：现有机器人基础模型（RFMs）虽然在通用端到端机器人控制方面展现出潜力，但在**跨环境、跨任务、跨本体（embodiment）泛化**方面的能力仍然有限。
- **深层原因**：现有 RFMs 通常基于互联网预训练的视觉语言模型（VLMs，如 PaliGemma）微调得到，而这些 VLM 仅在**2D 图文任务**上训练，天然缺乏**3D 空间推理能力**，而这种能力是机器人在 3D 物理世界中执行操作所必需的。
- **直接补齐的代价**：通过大规模机器人演示数据让 VLM 隐式学习 3D 结构，**成本极高且难以扩展**。
- **本文思路**：转向"易获取"的非机器人 2D 图像数据，通过自动标注 3D 信息并将其注入 VLM，使 VLM 具备与控制相关的 3D 理解能力，进而减少对机器人数据的依赖。

## 二、方法论

### 2.1 整体框架：分阶段训练流水线

- **Stage 0**：通用 VLM 预训练（如 PaliGemma 在网络规模数据上的训练）。
- **Stage 1**：在 PaliGemma 基础上加入单目深度编码器 MoGe，构建 **SPEAR-VLM**，并在带 3D 标注的非机器人 2D 图像上进行**3D 感知的 VQA 任务训练**。
- **Stage 2**：添加动作专家（action expert），在 Open X-Embodiment（OXE）机器人演示数据上训练 **SPEAR-1**（VLA 模型）。

### 2.2 SPEAR-VLM 架构

- **基础骨干**：PaliGemma，包含 SigLIP 视觉编码器、线性投影器、Gemma 语言模型。
- **3D 增强**：集成 **MoGe 单目深度编码器**（采用其 ViT 编码器最后 4 层中间特征，沿特征维拼接后通过随机初始化的线性投影器映射到 LLM 嵌入空间）。
- **特征融合**：SigLIP 投影器输出与 MoGe 投影器输出取平均后送入 LLM。
- **3D token 扩展**：在 PaliGemma 分词器中新增 N=1024 个**3D token**，用于在文本中编码 3D 坐标信息。

### 2.3 3D VQA 任务设计

- 任务包括：**3D 目标检测**（输出物体的 3D 包围盒顶点）、**物体-物体关系**（物体间 xyz 距离分量）、**相机-物体关系**、**物体关键点**等。
- 这些任务直接对应机器人操作所需的 3D 空间推理能力。

### 2.4 数据标注流水线（仅需 2D 图像输入）

- **步骤 1**：使用 Gemini 检测图像中的 2D 包围盒与语义标签。
- **步骤 2**：用 SAM2 基于 2D 包围盒生成实例级分割掩码。
- **步骤 3**：通过 MoGe 直接预测图像的 3D 点云，用分割掩码过滤得到物体 3D 点云，进而计算有向 3D 包围盒。
- **数据来源**：EgoExo4D 的"烹饪"和"自行车维修"部分（200k 图像）+ Bridge-V2 的 30k 帧（按 10% 比例采样）。

### 2.5 SPEAR-VLM 训练过程

- **第一阶段**：仅训练随机初始化的权重和 SigLIP 投影器，其余参数冻结；2k 步。
- **第二阶段**：保持 SigLIP 与 MoGe 编码器冻结，3D token 的 next-token-prediction 损失权重放大 λ=2；10k 步。

### 2.6 SPEAR-1 架构与动作生成

- **动作专家**：采用 π0 的 Flow Matching 架构，预测动作 chunk（horizon H=5，5Hz）。
- **旋转表示**：在单位四元数构成的 S³ 流形上做 flow matching（而非 R⁴→S³ 的线性流匹配），更加稳定。
- **噪声插值**：平移分量在欧氏空间线性插值 x^τ_t = τ·x_t + (1-τ)·x₀；旋转分量在 S³ 流形上做球面线性插值（slerp）。
- **训练损失**：平移使用 MSE 损失，旋转使用速度向量的余弦损失 + 测地线损失；监督信号为条件流匹配损失 L(θ) = L_R³(θ) + L_S³(θ)。
- **推理**：在 [0,1] 上对学习的向量场积分（平移用 Euler 积分，旋转在 S³ 流形上积分）。

### 2.7 其他工程改进

- **图像分辨率**：外部相机 280×210，腕部相机 112×112；**保持纵横比**（中心裁剪或填充），避免深度与点云估计被破坏。
- **视觉编码器微调策略**：VLM 训练阶段 SigLIP 与 MoGe 均训练，VLA 训练阶段冻结 MoGe（关键消融结论）。
- **数据归一化**：采用基于全局分位数的归一化，鼓励跨数据集学习运动而非"记忆"每个数据集。

## 三、实验设计

### 3.1 数据集

- **VLM 训练**：EgoExo4D（200k）+ Bridge-V2 子集（30k）——非机器人图像 + 3D 标注。
- **VLA 预训练**：Open X-Embodiment（OXE）24 个数据集，共约 **45M 帧**。
- **VLA 后训练（post-training）**：
  - SPEAR-1 (Bridge)：在 Bridge V2 上微调，用于 WidowX 评估。
  - SPEAR-1 (DROID)：在 DROID 数据集上微调，用于 Franka 评估。

### 3.2 评估基准与对比方法

- **仿真基准**：SIMPLER WidowX 环境（4 个任务）。
- **真实环境**：
  - WidowX（Bridge 设置，匹配 Bridge V2 硬件）：5 个任务，M=4，N=3，共 60 次试验。
  - Franka Research 3（DROID 设置）：5 个任务，M=5，N=3，共 75 次试验，涵盖未见过的环境与视角变化。
- **对比模型**：
  - OpenVLA、SpatialVLA（开源 VLA 基线）；
  - π0-FAST（自回归基线）；
  - **π0.5**（用 **20×** 更多机器人数据训练的 SOTA 模型）。

### 3.3 评估协议

- 每个任务定义 M 个初始条件（物体起始位置变化），每个条件执行 N 次试验；
- 使用**任务进度平均得分**（含部分完成度评分细则），而非简单的成功率；
- 设置固定种子 + 确定性 CUDA 操作 + EMA 检查点以减少训练方差。

### 3.4 关键消融（Table 1）

- 在 Bridge V2 单环境子集上训练并在 SIMPLER 评估，对比：
  - 无 3D（PaliGemma baseline）；
  - SPEAR-VLM 架构但仅训练随机像素的 3D 坐标（无对象级任务）；
  - 仅用对象级 3D 任务但不用 MoGe；
  - 完整 SPEAR-VLM；
  - 各种编码器训练/冻结组合。
- **关键发现**：
  1. 没有对象级 3D 任务时，3D 预训练几乎无收益；
  2. 对象级 3D 任务即使不用 MoGe 也能带来一定提升；
  3. VLA 训练阶段冻结 MoGe 至关重要，否则性能显著下降；
  4. SigLIP 与 MoGe 在 VLM 阶段均参与训练，配合 VLA 阶段冻结 MoGe，是最优配置。

### 3.5 真实环境 DROID 消融（Table 2）

- 同样在 DROID 上从头训练，比较 π0-PaliGemma (DROID) vs π0-SPEAR-VLM (DROID)；
- SPEAR-VLM 在 3 个 Franka 任务上平均高出 **>10%**，且在 DROID 训练集中**未出现**的"Carrot on Plate"任务上展示出更好的泛化能力。

## 四、资源与算力

- **VLM 训练（SPEAR-VLM）**：批大小 512，第一阶段 2k 步 + 第二阶段 10k 步；**16 块 Nvidia H200 GPU，总耗时约 18 小时**。
- **VLA 预训练**：批大小 2048，**300k 步（约 6 天）**，使用 **32 块 Nvidia H200 GPU**。
- **VLA 后训练**：在 Bridge V2 / DROID 上各微调 50k 步（具体算力配置未在主文给出）。
- **总机器人演示数据量**：约 **45M 帧**，约为 π0/π0.5 所用数据的 **1/20**。

## 五、实验数量与充分性

- **实验类型**：
  - 1 组架构与训练策略消融（5 行对比，Table 1）；
  - 1 组 VLM backbone 替换对比（Table 2，2 个模型）；
  - 1 组 SIMPLER 仿真对比（3 个模型，Table 3）；
  - 2 个真实环境平台（WidowX、Franka），共 **10 个任务**，合计 **135 次真实试验/模型**；
  - 多次小规模实验（BridgeData V2）用于动作表示、损失、数据归一化等设计选择消融。
- **公平性考量**：
  - 对比 π0-FAST 与 π0.5 时使用开源权重，且这些模型均使用双相机输入；
  - 训练阶段使用固定种子与确定性 CUDA 减少方差；
  - 使用 EMA 检查点稳定最终性能。
- **客观性**：实验设计基本公平，但存在一些潜在偏差（见第八节）。

## 六、主要结论与发现

- **核心结论**：在 VLM 中嵌入**显式 3D 空间推理能力**（通过 3D 标注的非机器人数据 + MoGe 深度编码器）可以**显著减少对昂贵机器人演示数据的依赖**，同时提升跨环境、跨任务的零样本泛化能力。
- **关键量化结果**：
  - 在 Franka (DROID) 上，**SPEAR-1 显著优于 π0-FAST，并与 π0.5 持平**，但仅使用其 **1/20** 的机器人演示数据；
  - 在 WidowX (Bridge) 上，SPEAR-1 比 OpenVLA 平均任务进度高 **10%**；
  - 在 SIMPLER 仿真上，SPEAR-1 平均成功率 **57.3%**，超过 SpatialVLA（42.7%）和 OpenVLA（1.0%）超 10 个百分点；
  - 仅用 **200k 非机器人图像**即可超越使用 **900M+ 额外机器人帧**训练的基线。
- **方法论结论**：3D 接地是扩展通用机器人基础模型更具可扩展性的路径。

## 七、优点与亮点

- **数据效率极高**：用 20× 较少的机器人演示数据达到 SOTA 性能，验证了"用易获取的非机器人数据补 3D 知识"这一思路的有效性。
- **端到端策略**：与 SpatialVLA、MolmoAct 等需推理时多步处理的方法不同，SPEAR-1 在**基础模型层面**实现 3D 增强，可端到端实时控制。
- **标注流水线优雅**：仅需 2D 图像 + 现成基础模型（Gemini + SAM2 + MoGe）即可生成 3D 包围盒、距离等标注，**无需深度传感器或人工 3D 标注**。
- **开放共享**：模型权重与 3D 标注数据集均公开发布（spear.insait.ai）。
- **细致的工程改进**：包括旋转在 S³ 流形上的 flow matching、保持图像纵横比、全局分位数归一化、EMA 检查点等，对实际性能有显著影响。
- **多平台验证**：同时在 WidowX 与 Franka 两种本体上展示零样本性能，且测试任务包含未见环境与视角变化。

## 八、不足与局限

- **非度量深度**：MoGe 输出的是**仿射不变**的点云，3D 标注不在度量空间内；论文承认该设计选择的下游影响尚未充分分析，需要未来引入度量深度估计器。
- **几何复杂度有限**：现有 3D 预训练策略**不适用于可变形物体**；复杂几何（旋转估计、碰撞检测）未被建模。
- **依赖后训练**：SPEAR-1 仍需在目标本体上**微调**才能达到满意结果；真正的"零样本跨本体"仍是开放问题。
- **扩展性未知**：3D 预训练数据量/质量与下游机器人控制性能之间的**scaling law 尚未研究**；当前受限于算力与时间未能展开。
- **任务多样性有限**：仅在 10 个真实任务上验证，相较于 π0.5 等用海量多样化机器人数据训练的方法，**泛化范围**仍存在不确定性。
- **评估偏差风险**：
  - 与 π0-FAST、π0.5 的比较是在未见目标环境的"零样本"设置下进行的，但 SPEAR-1 (DROID) 经过了 DROID 后训练，而 π0-FAST 与 π0.5 的 DROID 版本均为社区开源版本，可能存在训练细节差异未充分披露；
  - 评测由作者团队自行执行，可能引入主观偏差；
  - SIMPLER 仿真结果被作者承认"仅指示相对性能，不代表绝对性能"，削弱了仿真结论的参考价值。
- **闭源 SOTA 比较的不对等**：与 Gemini Robotics 1.0 等闭源系统相比，本文方法在规模与多样性上存在天然差距，论文中提到但未充分量化这一差距。
- **VLM 阶段规模有限**：VLM 训练仅 18 小时、16 卡 H200，相对当前大模型训练规模较小，可能限制 3D 理解的深度。

（完）
