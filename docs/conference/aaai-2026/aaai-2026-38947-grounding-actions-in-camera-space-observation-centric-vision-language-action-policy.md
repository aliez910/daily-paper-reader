---
title: "Grounding Actions in Camera Space: Observation-Centric Vision-Language-Action Policy"
title_zh: 在相机空间中锚定动作：以观测为中心的视觉-语言-动作策略
authors: "Tianyi Zhang, Haonan Duan, Haoran Hao, Yu Qiao, Jifeng Dai, Zhi Hou"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38947/42909"
tags: ["query:rob-il"]
score: 8.0
evidence: 将动作预测锚定在相机观测空间以解决VLA模型的空间不一致性
tldr: VLA模型常因观察空间与动作空间的不一致导致泛化困难。OC-VLA通过相机外参将末端执行器位姿从基坐标系转换到相机坐标系，统一了预测目标，在多种环境配置下显著提升了泛化性能。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 858, \"height\": 506, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1808, \"height\": 571, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 810, \"height\": 1187, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 855, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 855, \"height\": 588, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38947/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 1062, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38947/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1441, \"height\": 244, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38947/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1778, \"height\": 855, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38947/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1829, \"height\": 265, \"label\": \"Table\"}]"
motivation: VLA模型预测在基坐标系下，但数据来自不同相机视角，导致空间不一致。
method: 引入OC-VLA框架，利用相机外参将动作预测转换到相机观测空间。
result: 在模拟和真实环境实验中，OC-VLA展现了更好的泛化能力和操作成功率。
conclusion: 观测空间锚定是提升VLA模型泛化性的有效设计选择。
---

## Abstract
Vision-Language-Action (VLA) models frequently encounter challenges in generalizing to real-world environments due to inherent discrepancies between observation and action spaces. Although training data are collected from diverse camera perspectives, the models typically predict end-effector poses within the robot base coordinate frame, resulting in spatial inconsistencies. To mitigate this limitation, we introduce the Observation-Centric VLA (OC-VLA) framework, which grounds action predictions directly in the camera observation space. Leveraging the camera’s extrinsic calibration matrix, OC-VLA transforms end-effector poses from the robot base coordinate system into the camera coordinate system, thereby unifying prediction targets across heterogeneous viewpoints. This lightweight, plug-and-play strategy ensures robust alignment between perception and action, substantially improving model resilience to camera viewpoint variations. The proposed approach is readily compatible with existing VLA architectures, requiring no substantial modifications. Comprehensive evaluations on both simulated and real-world robotic manipulation tasks demonstrate that OC-VLA accelerates convergence, enhances task success rates, and improves cross-view generalization.

---

## 论文详细总结（自动生成）

# 论文中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- 当前 Vision-Language-Action (VLA) 模型面临的主要挑战在于**观测空间与动作空间的不一致**：训练数据来自各种相机视角，但模型通常预测**机器人基坐标系下的末端执行器位姿**。
- 这迫使模型隐式学习相机-机器人之间的变换矩阵，尤其在相机视角多变（如 Droid 数据集包含 1417 种视角）时，同一动作在不同视角下的观测差异巨大，导致**学习冲突和泛化困难**。
- 论文提出的 **Observation-Centric VLA (OC-VLA)** 将动作预测直接锚定在**相机观测空间**，通过统一预测目标与视觉观测所在的空间，从根本上缓解空间不匹配问题，提升模型的跨视角泛化能力。

## 2. 方法论
- **核心思想**：利用相机外参矩阵 \(T\)，将训练数据中的末端执行器动作从机器人基坐标系转换到**第三方相机坐标系**，并将该相机空间下的动作作为模型的预测目标；推理时将预测结果再转换回机器人坐标系执行。
- **关键技术细节**：
  - 设两个相邻时刻的末端位姿为 \(P^{\text{world}}_1, P^{\text{world}}_2\)，则机器人基坐标系下的动作为 \(A^{\text{world}} = P^{\text{world}}_2 \cdot (P^{\text{world}}_1)^{-1}\)。
  - 利用相机外参 \(T\)，有 \(P^{\text{cam}} = T \cdot P^{\text{world}}\)，进而得到相机空间动作 \(A^{\text{cam}} = P^{\text{cam}}_2 \cdot (P^{\text{cam}}_1)^{-1} = T \cdot A^{\text{world}} \cdot T^{-1}\)。
  - 将 \(A^{\text{cam}}\) 转换为 7 维形式 \(\langle x, y, z, \text{roll}, \text{pitch}, \text{yaw}, \text{gripper} \rangle\) 作为监督信号。
  - 该方法兼容**离散动作空间**（交叉熵损失）和**连续动作空间**（扩散 MSE 损失），无需修改模型架构。
- **优化视角分析**：从 UV 坐标与相机坐标的映射出发，指出相机空间动作比基坐标动作更易于从视觉特征直接推断，从而减少模型对不同视角下变换矩阵 \(T\) 的隐式学习负担。

## 3. 实验设计
- **模拟环境**：基于 **ManiSkill2** 的 5 个任务（PickCube-v0、StackCube-v0、PickSingleYCB-v0、PickClutterYCB-v0、PickSingleEGAD-v0）。生成 300,000 个随机相机视角，构建超过 40,000 条轨迹，按 19:1 划分为训练集与验证集；最终从验证集每任务采样 100 条轨迹共 500 条用于闭环评估。
- **真实机器人平台**：Franka Emika Panda + Robotiq 2F-85 夹爪 + 3 个 RealSense D435i 相机。设置三种评估条件：
  - **固定相机**：使用 Camera1 收集 15 个任务（各 10 条演示）微调与评估；
  - **轻微扰动**：使用 Camera2（带小幅度位置扰动）收集 8 个任务，并保持类似配置评估；
  - **新颖相机视角**：使用未见过的新相机进行零样本评估。
- **对比方法**：
  - OpenVLA-OFT（离散动作）、π0（连续动作）使用官方微调协议；
  - 自身基线（基于 Dita 架构）分别在**机器人基坐标系**和**相机基坐标系**下训练。
- **评价指标**：任务成功率（每任务 10 次试验的平均成功率）。

## 4. 资源与算力
- 文中明确给出优化细节：
  - **GPU**：8 块 NVIDIA A100（每 GPU 处理 256 样本）。
  - **Batch Size**：2048。
  - **训练步数**：模拟实验（从零训练）30,000 步；真实实验（微调）20,000 步。
  - **学习率**：Causal Transformer 和 Q-Former 为 1e-4，DINOv2 为 1e-5。
  - **优化器**：AdamW。
- （文中未提及预训练阶段的额外算力消耗，但给出了微调阶段的明确配置。）

## 5. 实验数量与充分性
- **模拟实验**：共 2（动作空间：离散/连续）× 2（坐标选择：基坐标系/相机坐标系）= **4 组核心对比**（表 1），每个任务（5 个）报告成功率，总计 4×5=20 个数据点。此外提供定性对比（图 3）。
- **真实实验**：
  - 表 2：固定相机下 8 种方法（含 (var) 零样本）在 15 个任务上的成功率；表 3：轻微扰动下 4 种方法在 8 个任务上的成功率。
  - 零样本新颖视角评估（表 2 中标注 (var) 的行）。
  - 定性对比（图 6）展示抓取鲁棒性。
- **充分性与公平性**：
  - 覆盖模拟与真实场景，任务种类多样（拾取、堆叠、倒水、旋转、推拉等），视角变化类型丰富（固定、扰动、新颖）。
  - 对比方法使用官方微调协议，自身基线仅改变坐标空间而保持架构一致。
  - 不足：缺乏对外参标定误差的消融分析；未对比其他坐标空间（如图像平面坐标）；未包含腕部相机视角。

## 6. 主要结论与发现
- OC-VLA 在模拟和真实环境下**始终优于基坐标系基线**，特别是离散动作空间下模拟平均提升约 **14%**（53.2% vs 45.2%）；真实固定相机下提升约 **10%**（68% vs 58%）。
- 在**新颖相机视角**下，OC-VLA 仅下降 14%（从 68% 到 54%），而最强基线 OpenVLA-OFT 下降超过 20%（从 63.3% 到 42%），展示了更强的视角鲁棒性。
- 在**轻微相机扰动**条件下，相机基坐标模型的相对优势更加明显（73.8% vs 61.3%），印证了其对视角变化的包容性。
- 结论：**将动作预测锚定在观测空间是提升 VLA 模型泛化能力的有效设计选择**，且可作为即插即用模块无缝集成到现有架构中。

## 7. 优点
- **方法简洁实用**：仅需利用相机外参进行坐标变换，不引入额外网络模块或推理开销，易于复现和部署。
- **通用性**：兼容离散和连续两种主流动作空间，适用于扩散策略和 token 分类策略。
- **广泛的实验验证**：同时包含模拟和真实环境，覆盖多任务、多视角（固定、扰动、零样本新颖视角），并与多个 SOTA 基线公平对比。
- **开源代码**：提供完整代码仓库，增强可重复性。

## 8. 不足与局限
- **依赖相机外参**：需要精准的相机-机器人标定信息，限制了在未标定或动态环境中的直接应用。
- **仅考虑第三人称视角**：未探索第一人称（如腕部相机）或多相机融合场景下的有效性。
- **缺乏对标定误差的鲁棒性分析**：未实验外参噪声对性能的影响，实际部署中可能存在风险。
- **消融实验不够深入**：例如未比较其他坐标空间（如图像 UV 坐标）或不同变换公式；未分析不同动作空间（离散 vs 连续）对跨视角增益的差异原因。
- **计算资源需求较高**：使用了 8 块 A100 GPU 进行训练，对资源有限的团队不够友好（尽管方法本身轻量，但训练规模较大）。
- **未见零样本直接部署测试**：真实实验中所有模型均经过微调（10-shot），未评估完全不微调的零样本泛化能力。

（完）
