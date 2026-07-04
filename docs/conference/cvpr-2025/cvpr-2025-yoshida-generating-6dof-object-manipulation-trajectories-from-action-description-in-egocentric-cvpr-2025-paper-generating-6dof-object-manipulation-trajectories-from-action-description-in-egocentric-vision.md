---
title: Generating 6DoF Object Manipulation Trajectories from Action Description in Egocentric Vision
title_zh: 基于自我中心视觉与动作描述生成6DoF物体操作轨迹
authors: "Yoshida, Tomoya, Kurita, Shuhei, Nishimura, Taichi, Mori, Shinsuke"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yoshida_Generating_6DoF_Object_Manipulation_Trajectories_from_Action_Description_in_Egocentric_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 从大规模视频数据中生成机器人操作轨迹
tldr: 为机器人操作训练收集多样化的详细演示数据代价高昂，几乎不可大规模实现。本文提出从大规模自我中心与外部中心视频数据集中提取多样化操作轨迹的框架，并结合文本动作描述构建基于视觉与点云的轨迹生成模型。该方法利用互联网规模视频数据为复杂操作任务的模仿学习提供了可扩展的数据来源。该工作对解决模仿学习数据瓶颈问题具有重要价值。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1781, \"height\": 552, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 562, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 642, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1790, \"height\": 256, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1793, \"height\": 255, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1803, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 820, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 845, \"height\": 648, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 793, \"height\": 228, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 419, \"height\": 739, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 842, \"height\": 254, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1564, \"height\": 640, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 846, \"height\": 222, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 736, \"height\": 250, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yoshida-generating-6dof-object-manipulation-trajectories-from-action-description-in-egocentric-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 828, \"height\": 254, \"label\": \"Table\"}]"
motivation: 收集大规模多样化操作演示数据用于机器人轨迹生成代价过高。
method: 利用大规模Exo-Ego4D视频数据集提取操作轨迹并训练轨迹生成模型。
result: 为操作轨迹生成提供了可扩展的视频数据来源。
conclusion: 该工作为模仿学习的数据扩展提供了新途径。
---

## Abstract
Learning to use tools or objects in common scenes, particularly handling them in various ways as instructed, is a key challenge for developing interactive robots. Training models to generate such manipulation trajectories requires a large and diverse collection of detailed manipulation demonstrations for various objects, which is nearly unfeasible to gather at scale. In this paper, we propose a framework that leverages large-scale ego- and exo-centric video datasets --- constructed globally with substantial effort --- of Exo-Ego4D to extract diverse manipulation trajectories at scale. From these extracted trajectories with the associated textual action description, we develop trajectory generation models based on visual and point cloud-based language models. In the recently proposed egocentric vision-based in-a-quality trajectory dataset of HOT3D, we confirmed that our models successfully generate valid object trajectories, establishing a training dataset and baseline models for the novel task of generating 6DoF manipulation trajectories from action descriptions in egocentric vision.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper following a specific structure. Let me analyze the paper carefully and organize the content.

The paper is about generating 6DoF object manipulation trajectories from action descriptions in egocentric vision. Let me extract key information:

1. Core problem: Generating 6DoF object manipulation trajectories from textual action descriptions, addressing the data scarcity problem in robot manipulation learning.

2. Method: 
- Framework to extract 6DoF object manipulation trajectories from egocentric videos (Ego-Exo4D)
- Four steps: temporal action localization, position sequence extraction, trajectory projection, rotation sequence extraction
- Built EgoTraj dataset with 28,497 trajectories
- Used VLMs (BLIP-2, VILA, PointLLM, MiniGPT-3D) with trajectory tokenization

3. Experiments: HOT3D dataset for evaluation, comparison with Seq2Seq and USST baselines

4. Resources: Not explicitly mentioned in the paper text

5. Experiments: Multiple comparisons across different VLMs, modalities, sampling strategies, dataset scales

6. Conclusions: VLMs can generate valid object trajectories, point cloud/depth info helps, dataset scale improves performance

7. Advantages: First large-scale framework, scalable, multiple VLM backbones tested

8. Limitations: Cannot handle deformable objects, segmentation/registration failures

Let me write this in Chinese with the requested structure.
</think>
# 论文总结：从自我中心视觉与动作描述生成 6DoF 物体操作轨迹

## 1. 核心问题与研究背景

- **研究动机**：让机器人学会使用日常工具并按指令执行多样化操作是发展交互式机器人的关键能力。然而，训练能够生成操作轨迹的模型需要**大规模、多样化**的精细操作演示数据，这类数据在真实场景中几乎无法大规模采集。
- **现有数据局限**：
  - 精确的 3D 手-物交互数据（如 H2O、EgoPAT3D、HOT3D）需借助多相机、深度相机或光学标记，采集成本高、规模有限。
  - 大规模自我中心视频（Ego4D、Ego-Exo4D）虽可大规模获取，但缺乏精确的 6DoF 操作轨迹与相机外参标注。
- **核心问题**：能否从**普通单目自我中心视频**（无需预标定的相机外参）中自动提取 6DoF 物体操作轨迹，并基于动作描述生成对应的操作轨迹？

## 2. 方法论

### 2.1 整体框架
作者提出从自我中心视频中自动提取 6DoF 物体操作轨迹的四步流水线，并构建训练数据集 **EgoTraj**；然后基于视觉-语言模型（VLM）将轨迹生成形式化为 **Next-Token Prediction** 任务。

### 2.2 轨迹提取流水线（4 个阶段）
1. **时间动作定位**：以 Ego-Exo4D 原始标注时刻为中心切出 4 秒片段，使用 GPT-4o 联合动作描述判断动作起止帧 $t_{\text{start}}$、$t_{\text{end}}$，同时识别操作物体名称并判断是否为刚体。
2. **位置序列提取**：用 Grounded-SAM 对起始帧进行开放词汇分割得到 2D 掩码；用 Depth Anything 估计深度；用 SpaTracker 在 3D 空间跟踪掩码点，得到物体中心 3D 轨迹点。
3. **轨迹投影（去除相机运动）**：将每帧 RGB-D 转为点云 $P_i$，通过公式 $\begin{bmatrix}x\\y\\z\end{bmatrix}=d_{ij}K^{-1}\begin{bmatrix}i\\j\\1\end{bmatrix}$ 计算相机坐标。计算 FPFH 特征后用 RANSAC + Colored ICP 进行点云配准，得到各帧相对 $f_{\text{start}}$ 的外参矩阵；再将跟踪结果乘以该矩阵，投影到 $f_{\text{start}}$ 的相机坐标系。
4. **旋转序列提取**：设初始物体位姿为单位变换，对每时刻的物体点云与初始点云计算协方差矩阵 $H=U\Sigma V^T$，得到旋转矩阵 $R=VU^T$，再转为旋转向量 $r\in\mathbb{R}^3$；将位置和旋转拼接得到 6DoF 轨迹。

### 2.3 轨迹生成模型
- **任务定义**：给定动作描述 + 视觉输入（图像/点云/深度）+ 物体初始位姿，生成 6DoF 位姿序列。
- **位姿离散化**：对 6 个连续维度（$x,y,z,\text{roll,pitch,yaw}$）各量化为 256 个 bin，加入 256 个特殊 token 作为轨迹词表。
- **骨干 VLM**：
  - 2D 视觉：BLIP-2 (2.7B/6.7B)、VILA (3B/8B)，并扩展加入深度编码器
  - 3D 点云：PointLLM (7B)、MiniGPT-3D (2.7B)
- **训练目标**：标准的交叉熵语言建模损失（next-token prediction）。

## 3. 实验设计

- **训练数据**：从 Ego-Exo4D 提取 28,497 条轨迹（27,788 训练 / 709 验证）。
- **评估数据**：HOT3D（986 条带精确 6DoF 标注的样本），平均轨迹长度 33.17 帧，截断到 20 帧（平均 15.39 帧）。
- **评价指标**：
  - ADE：预测与真值轨迹各时间步的 L2 距离
  - FDE：最终时间步的 L2 距离
  - GD（Geodesic Distance）：旋转矩阵之间的角度差 $d(R^*,R)=\arccos\frac{\text{tr}(R^{*T}R)-1}{2}$
- **对比方法**：
  - 传统 Seq2Seq Transformer + MLP 头（递归预测下一位姿）
  - USST（基于 3D 手轨迹预测的不确定性感知状态空间 Transformer）
  - BLIP-2 / VILA / MiniGPT-3D / PointLLM 多种 VLM 变体（含/不含深度）
- **基准任务**：
  - 3DoF（仅位置）与 6DoF（位置+旋转）轨迹生成
  - 反向任务：基于图像/点云生成动作描述

## 4. 资源与算力

- **论文正文未明确说明**训练所用的 GPU 型号、数量、训练时长、参数规模细节（仅标注了模型参数量，如 BLIP-2 2.7B/6.7B、PointLLM 7B、VILA 3B/8B 等）。
- 仅提到 4 秒片段的图像帧以 20 fps 采样；推理阶段采样最多 10 个候选轨迹。
- 算力消耗属于**未报告**状态。

## 5. 实验数量与充分性

- **实验组数**：
  1. 多种 VLM 骨干（BLIP-2、VILA、PointLLM、MiniGPT-3D）共 8 种配置 × 3DoF/6DoF × 多种输入模态（约 32 个数据点）
  2. 与 USST 3 种训练设置的对比（从零训练、预训练、微调）
  3. 概率采样（1, 3, 10 个候选）的消融
  4. 数据规模消融（1.0, 0.5, 0.1, 0.05, 0.01 比例）
  5. 反向任务：动作描述生成（BLIP-2、PointLLM 各 2 个条件 × 3 个指标）
  6. 定性分析：不同动词（pick/stir）生成轨迹的差异
- **充分性与公平性评估**：
  - 优点：覆盖了多种视觉模态、多个 VLM 变体；既有位置误差也有旋转误差；含数据规模消融，论证了自动提取框架的扩展性。
  - 局限：评估仅在 HOT3D 单一测试集上，缺乏多基准验证；评价指标为 L2/角度距离，未引入任务级（如机器人执行成功率）评估；轨迹长度被截断到 20 帧，限制了长时序任务的衡量；缺少与最先进机器人操作模型（如 RT-2、OpenVLA）的直接对比。

## 6. 主要结论与发现

- VLM 在文本引导的 6DoF 物体轨迹生成任务上**显著优于**传统 Seq2Seq 基线（PointLLM 比 Seq2Seq 的 3D ADE 低 0.103 m）。
- **空间信息（点云/深度）有助于性能提升**：3D 模态 VLM（PointLLM、MiniGPT-3D）以及加入深度图的 2D VLM 普遍优于纯图像输入。
- **模型规模并非唯一决定因素**：BLIP-2 (2.7B) 反而优于 VILA (8B)，说明任务特性比单纯放大模型更关键。
- **轨迹可用于反向任务**：将轨迹作为额外输入，使动作描述生成中的**动词相似度（Sim_v）提升近 10%**。
- **数据规模与性能正相关**：从 1% 到 100% 训练数据，性能单调提升，验证了自动提取框架的扩展性。
- **概率采样能力**：因采用语言模型框架，可通过 nucleus sampling 生成多条合理轨迹，候选数越多最优 ADE 越好；但 GD 改善有限，旋转生成仍是难点。

## 7. 优点与亮点

- **首创性**：首次在**不需要预标定相机外参**的条件下，从普通单目自我中心视频中自动构建大规模 6DoF 物体操作轨迹数据集（28,497 条，远超 H2O、HOT3D 等）。
- **数据规模与多样性优势**：涵盖 228 种动作动词、4,158 种物体，比现有 H2O（12 动词）、HOT3D（30 动词）多出 1–2 个数量级。
- **方法兼容性广**：流水线可应用于大多数自我中心视频数据集；模型框架兼容任意 VLM 骨干。
- **任务形式新颖**：将 6DoF 轨迹生成形式化为 next-token prediction，统一了视觉-语言-动作的接口。
- **双向验证**：不仅能从文本生成轨迹，还能用轨迹反哺动作描述生成，验证了提取轨迹的语义正确性。

## 8. 不足与局限

- **应用范围限制**：
  - 6DoF 边界框表示无法处理**非刚体**（如衣物、食材）。
  - 仅筛选"刚体"操作，过滤了相当部分自然操作。
- **技术失败模式**：
  - 当场景中出现**相似物体**时，Grounded-SAM 分割易失败。
  - 当**相机运动剧烈**时，点云配准（FPFH+RANSAC+Colored ICP）易失败。
  - DUSt3R 等联合方法在自我中心视角下会"挤压"细节 3D 运动，限制其直接应用。
- **数据噪声**：EgoTraj 由 ML 方法自动提取，存在位姿估计误差；与 H2O、HOT3D 的精确实验室标注相比，质量有差距。
- **评估不充分**：
  - 单一测试集（HOT3D）且样本数仅 986。
  - 缺乏机器人**实际执行**或仿真执行的闭环评估。
  - 轨迹被截断到 20 帧，对长时序任务适用性受限。
- **未报告算力**：训练资源、时长、超参未公开，难以复现与对比。
- **与机器人落地脱节**：生成的轨迹为物体级 6DoF 位姿，未直接给出机器人动作指令（关节空间、夹爪状态等），从"物体轨迹"到"机器人可执行动作"仍存在鸿沟。

（完）
