---
title: "RC-NF: Robot-Conditioned Normalizing Flow for Real-Time Anomaly Detection in Robotic Manipulation"
title_zh: RC-NF：机器人条件归一化流用于机器人操作实时异常检测
authors: "Zhou, Shijie, Zhu, Bin, Yang, Jiarui, Zhao, Xiangyu, Chen, Jingjing, Jiang, Yu-Gang"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhou_RC-NF_Robot-Conditioned_Normalizing_Flow_for_Real-Time_Anomaly_Detection_in_Robotic_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 针对模仿学习训练的VLA模型在分布外条件下运行可靠性问题
tldr: 模仿学习训练的VLA模型在动态环境中常因分布外条件而失效。本文提出机器人条件归一化流RC-NF，实时监测机器人状态与物体轨迹是否与任务一致。该方法仅需正样本进行无监督训练，并对任务感知的机器人与物体状态解耦处理，可输出精确异常分数并支持干预。论文为提升模仿学习操作策略的部署可靠性提供了实用监控方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1772, \"height\": 767, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1768, \"height\": 576, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 762, \"height\": 781, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 872, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 843, \"height\": 541, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1813, \"height\": 639, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 813, \"height\": 419, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1538, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhou-rc-nf-robot-conditioned-normalizing-flow-for-real-time-anomaly-detection-in-robotic-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1777, \"height\": 444, \"label\": \"Table\"}]"
motivation: 模仿学习训练的VLA模型在动态、分布外场景下难以稳定执行复杂操作任务。
method: 提出机器人条件归一化流，对机器人与物体状态进行解耦并实时计算异常分数。
result: 仅用正样本即可实现精确异常检测，从而支持及时干预恢复。
conclusion: 该方法为VLA模仿学习策略的实际部署提供了有效的安全监控机制。
---

## Abstract
Recent advances in Vision-Language-Action (VLA) models have enabled robots to execute increasingly complex tasks. However, VLA models trained through imitation learning struggle to operate reliably in dynamic environments and often fail under Out-of-Distribution (OOD) conditions. To address this issue, we propose Robot-Conditioned Normalizing Flow(RC-NF), a real-time monitoring model for robotic anomaly detection and intervention that ensures the robot's state and the object's motion trajectory align with the task. RC-NF decouples the processing of task-aware robot and object states within the normalizing flow. It requires only positive samples for unsupervised training and calculates accurate robotic anomaly scores during inference through the probability density function. We further present LIBERO-Anomaly-10, a benchmark comprising three categories of robotic anomalies for simulation evaluation. RC-NF achieves state-of-the-art performance across all anomaly types compared to previous methods in monitoring robotic tasks. Real-world experiments demonstrate that RC-NF operates as a plug-and-play module for VLA models (e.g., Pi0) , providing a real-time OOD signal that enables state-level rollback or task-level replanning when necessary, with a response latency under 100 ms. These results have demonstrated that our RC-NF noticeably enhances the robustness and adaptability of VLA-based robotic systems in dynamic environments.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "RC-NF: Robot-Conditioned Normalizing Flow for Real-Time Anomaly Detection in Robotic Manipulation" organized in a structured Markdown format. Let me carefully analyze the paper and produce a comprehensive summary covering all the requested points.

Let me go through the paper carefully:

1. Core problem: VLA models trained via imitation learning fail in OOD conditions during real-world deployment
2. Method: RC-NF - a normalizing flow model conditioned on robot state and task, with RCPQNet as the affine coupling layer
3. Experiments: LIBERO-Anomaly-10 benchmark, comparison with GPT-5, Gemini 2.5 Pro, Claude 4.5, FailDetect
4. Resources: RTX 3090 mentioned for real-world, but training details not fully specified
5. Experimental quantity: Main results table, ablation study, real-world evaluation
6. Conclusions: SOTA performance, sub-100ms latency, plug-and-play with π0
7. Strengths: Novel architecture, decoupled processing, real-time performance
8. Limitations: Limited to specific anomaly types, depends on SAM2, etc.

Let me write a comprehensive summary in Chinese.</think>

# RC-NF 论文结构化总结

## 1. 核心问题与研究动机

- **背景**：Vision-Language-Action（VLA）模型（如 π0、OpenVLA、RT-2 等）通过模仿学习在专家演示数据上训练，能够从自然语言指令映射到低层控制动作，可执行日益复杂的操作任务。
- **核心痛点**：VLA 模型在真实动态环境中部署时，常因 **Out-of-Distribution（OOD）条件** 失效，表现为：
  - **任务级 OOD**：当前指令与环境不再匹配（如要求把球放入"打开的抽屉"但抽屉已关闭）。
  - **状态级 OOD**：机器人相对物体的运动轨迹偏离训练分布（如抓取后物体滑落）。
- **现有方案的不足**：
  - 行为分类式监控（行为树、状态机）需穷举异常条件，难以应对组合式多变场景。
  - 基于 VLM 的双系统监控（Sentinel 等）需要多步推理，延迟达多秒级，无法及时干预。
  - 现有流匹配方法（如 FailDetect）仅简单拼接图像与机器人状态特征，缺乏任务感知与结构化解耦。
- **本文目标**：构建一个 **实时（sub-100ms）、即插即用、无监督训练（无需负样本/异常数据）的运行时异常检测模块**，可为 VLA 提供统一的 OOD 信号，并支持任务级重规划与状态级回滚。

---

## 2. 方法论

### 2.1 整体框架

- **核心思路**：将机器人异常检测建模为 **机器人状态 s 与任务相关物体轨迹 x_target 的联合分布 p_T(x_target, s) 估计问题**，并通过概率密度的负对数作为异常分数。
- **基础**：Normalizing Flow（NF）通过 K 步可逆变换 f 在复杂分布 X 与简单分布 Z（高斯）之间建立双向映射，可精确计算似然：
  $$\log p_{X|C}(x|c) = \log p_{Z|C}(f_c(x)|c) + \sum_{i=1}^K \log\left|\det \frac{\partial f_{i,c}(y_{i-1})}{\partial y_{i-1}}\right|$$
- **条件 c = (s, τ)**：s 为机器人状态（关节、夹爪、笛卡尔位姿），τ 为任务嵌入。
  - **任务嵌入 τ**：将任务 prompt 映射到 T 维超球面（半径 R）上的表面向量，使其在潜在空间均匀分布、最大程度分离，作为高斯先验均值 μ_task。
  - **物体点集**：SAM2 对视频流分割掩码 → 网格采样得到点集 X，作为 NF 的输入。

### 2.2 核心创新：Robot-Conditioned Point Query Network（RCPQNet）

作为 RC-NF 的仿射耦合层，融合机器人状态、任务嵌入与物体点集。

- **输入处理**：点集 x ∈ R^{B×T×N×2} 沿时间维度切分为两半（x_b 与 x_t），仅 x_b 进入 RCPQNet 生成 γ（缩放）和 β（平移），对 x_t 做仿射变换，保证可逆。
- **Task-aware Robot-Conditioned Query**：
  - 机器人状态经线性层映射至隐空间；
  - 通过 **FiLM**（Feature-wise Linear Modulation）用任务嵌入 τ 对其进行调制；
  - 得到的 query token 编码了"机器人当前状态 + 高层任务目标"。
- **Dual-Branch Point Feature Encoding**：
  - **Dynamic Shape 分支**：对每帧点集做中心化与归一化以消除平移与尺度影响，再用 MLP + GRU + Transformer 编码形状的时序变化。
  - **Positional Residual 分支**：保留原始点集中的绝对位置残差信息，补偿形状归一化损失。
  - 两个分支输出融合后作为 memory token，与 query token 通过 cross-attention 交互，最终生成条件相关的仿射参数。
- **关键设计哲学**：**机器人特征作为 query、物体点特征作为 memory**，实现多模态信息的结构化解耦与高效交互，避免特征干扰。

### 2.3 异常检测与处理机制

- **异常分数**：负对数似然（−log p）越大表示越偏离正常任务分布。
- **静态阈值校准**（不随时间变化）：
  $$Upper_T = \mu_T + Q_{1-\alpha}(D_T)$$
  其中 μ_T 为 S1 上的平均异常分数，D_T 为 S2 上的偏差集合，α = 0.05（沿用 FailDetect 设计）；训练时施加 debiasing 以保证分数时序平滑。
- **异常处理分层**：
  - **任务级 OOD**：触发高层控制器（人工或 LLM 规划器）进行任务重规划，更新子任务序列。
  - **状态级 OOD**：触发 **homing procedure**（归位程序），使机械臂返回初始姿态，局部调整轨迹/控制参数直至异常分数低于阈值，再无缝交还 VLA 控制权。

---

## 3. 实验设计

### 3.1 数据集与 Benchmark

- **训练数据**：原始 **LIBERO-10**（每任务 50 条专家演示）。
- **新提出的 Benchmark：LIBERO-Anomaly-10**，包含三种操作任务专属异常：
  1. **Gripper Open**：在应抓取时刻夹爪保持张开，物体位置正常但状态与任务不符。
  2. **Gripper Slippage**：抓取后摩擦力归零，物体滑动产生异常轨迹。
  3. **Spatial Misalignment**：机器人移向错误舱位（前/左/右）而非任务规定的后舱，测试语义-空间对齐。
- 标注规则：t_anomaly 之前为正常，之后为异常。前两类对 LIBERO-10 全部 10 个任务生成，第三类只涉及放置类任务。

### 3.2 对比方法

- **VLM 类（以 Sentinel 形式调用，1 Hz 并行采样）**：
  - GPT-5、Gemini 2.5 Pro、Claude 4.5。
- **流模型类**：FailDetect（基于一致性流匹配，拼接图像与机器人状态特征）。
- **评估指标**：**AUC**（整体判别能力）与 **AP**（精确率-召回率，适用于类别不平衡）。

### 3.3 真实世界设置

- **机械臂**：Franka Research 3，配备腕部 + 第三人称两台 Intel RealSense D435 相机。
- **VLA 基线**：π0，训练数据与 RC-NF 一致；RC-NF 仅使用第三人称相机用于监控。
- **任务场景**："把蓝色球放进打开的抽屉" 等派生任务，模拟抽屉中途关闭（任务级 OOD）与球被抓后掉落/滚到夹爪后方（状态级 OOD）。

---

## 4. 资源与算力

- **真实世界推理**：在消费级 GPU **Nvidia GeForce RTX 3090** 上实现，响应延迟 < 100 ms。
- **训练细节**：
  - 流步数 **K = 12**，训练 **100 epochs**，施加 debiasing 做数据平衡。
  - 第一帧的 box prompt 在仿真中通过计算机图形保证可复现；在真实世界中由 Gemini 2.5 Pro 提供。
- **未明确说明**：未给出训练所用 GPU 数量/型号、训练总时长、内存占用等具体信息；这是论文中较显著的披露空白。

---

## 5. 实验数量与充分性

- **主表（Table 1）**：1 组对比实验，在 LIBERO-Anomaly-10 三类异常上对比 5 个方法（GPT-5、Gemini 2.5 Pro、Claude 4.5、FailDetect、RC-NF），分别报告 AUC 与 AP。
- **消融实验（Table 2）**：5 行——完整模型、去任务嵌入、去机器人状态、去 Positional Residual 分支、去 Dynamic Shape 分支，验证 RCPQNet 各组件贡献。
- **可视化分析（Figure 4）**：异常分数随时间变化曲线，展示 t_anomaly 前后分数突变与平滑性。
- **真实世界评估（Figure 5/6/7）**：两类 OOD 场景下的 π0 与 π0+RC-NF 对比，包含任务级与状态级两段连续事件。
- **充分性评价**：
  - **优点**：覆盖了仿真 + 真实世界、定量 + 定性；消融实验系统化；视觉化分析直观。
  - **局限**：异常类别仅 3 种且都是相对受控的合成异常；对真实世界中更复杂、非预设的扰动（如光照变化、遮挡、新物体等）覆盖不足；基线 VLM 仅以 1 Hz 采样评估，对延迟的对比条件设置存在一定不公平性（真实部署中 VLM 推理本身就慢）。

---

## 6. 主要结论与发现

- **性能领先**：在 LIBERO-Anomaly-10 上 RC-NF 平均 AUC = 0.9309、AP = 0.9494，比此前最优方法（GPT-5）提升约 **8% AUC 和 10% AP**。
- **VLM 的盲区**：GPT-5、Gemini 2.5 Pro、Claude 4.5 在 Gripper Open/Slippage 上表现中等，但在 Spatial Misalignment 上退化至 AUC ≈ 0.5、AP ≈ 0.4（接近随机），说明 VLM 在"视觉语义对齐空间方向"上力不从心。
- **FailDetect 的局限**：简单拼接图像与机器人状态特征，导致特征纠缠与不平衡，性能显著落后于 RC-NF。
- **关键组件贡献**：
  - 任务嵌入对 Spatial Misalignment 至关重要（去掉后 AUC 由 0.9676 降至 0.8139）。
  - 机器人状态对 Gripper Open 至关重要（去掉后 AUC 暴跌至 0.6327）。
  - Dynamic Shape 分支是 Dual-Branch 中最关键的（去掉后平均 AUC 由 0.93 降至 0.68，Spatial Misalignment 上几乎完全失效）。
- **真实部署**：RC-NF < 100 ms 的延迟可与 π0 等 VLA 模型实时协作，有效处理任务级与状态级 OOD。
- **泛化能力**：从仿真到真实世界的 sim-to-real 迁移有效，结构化特征解耦带来分数的平滑性、稳定性和准确性。

---

## 7. 优点与亮点

- **方法创新**：
  - 首次将 Normalizing Flow 引入机器人操作实时异常检测，输出具备概率意义的连续异常分数（不同于 VLM 的离散分级或分类器的二元输出）。
  - **RCPQNet** 仿射耦合层设计新颖：以任务感知的机器人特征为 query、点集特征为 memory，cross-attention 替代传统 MLP，结构化地融合多模态信息。
  - **Dual-Branch Point Feature Encoding** 同时建模"形状变化"与"位置残差"，对抓取滑落和空间错位等差异化的运动异常都具判别力。
- **训练范式**：仅需正样本（成功演示），无监督训练，避免了异常数据采集/标注难题。
- **架构兼容性**：plug-and-play 设计，无需修改 VLA 架构，可作为通用 OOD 信号同时支持任务级重规划与状态级回滚。
- **Benchmark 贡献**：LIBERO-Anomaly-10 弥补了"通用任务失败"数据集无法评估操作任务专属异常的空白。
- **全面验证**：仿真量化、消融、可视化、真实世界实验四管齐下。
- **延迟突破**：< 100 ms 推理满足闭环控制实时性约束，远快于 VLM 的多秒级推理。

---

## 8. 不足与局限

- **依赖外部组件**：RC-NF 严重依赖 SAM2 提供物体分割掩码；SAM2 在遮挡、相似物体、动态背景、小目标等场景下可能失败，进而污染点集。
- **异常类型覆盖有限**：
  - LIBERO-Anomaly-10 仅 3 类预定义异常，均为受控合成扰动；
  - 未涵盖光照变化、视角偏移、新物体出现、传感器噪声等更真实、更多样的 OOD 来源。
  - Spatial Misalignment 仅在放置类任务中存在，泛化到其他任务类型未充分验证。
- **VLM 基线对比的公平性**：
  - VLM 仅以 1 Hz 采样评估，未充分体现其多模态推理的丰富信息；
  - VLM 提示词来自 Sentinel（任务进度评估），并非为异常检测专门优化。
- **算力与训练信息不完整**：未披露训练 GPU 型号/数量、训练总时长、模型参数量、内存占用等关键信息，复现门槛较高。
- **阈值需校准**：使用静态阈值需要 S1、S2 两组标定数据，跨任务/跨环境的迁移性未讨论。
- **任务嵌入依赖 spherical uniform encoding**，对未见过的任务 prompt 分布外情况未做压力测试。
- **方法局限**：基于 Normalizing Flow 的方法在非常高维空间上扩展性有限，目前仅适用于 LIBERO 规模的操作任务；尚不清楚能否扩展到更长时序、更多物体的复杂场景。
- **真实实验规模小**：仅在 Franka Research 3 上、围绕单一任务（蓝色球进抽屉）演示，缺少跨机器人平台、跨任务族、跨环境的广泛验证。

（完）
