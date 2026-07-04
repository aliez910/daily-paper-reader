---
title: Spatial-Temporal Graph Diffusion Policy with Kinematic Modeling for Bimanual Robotic Manipulation
title_zh: 融合运动学建模的时空图扩散策略用于双手机器人操控
authors: "Lv, Qi, Li, Hao, Deng, Xiang, Shao, Rui, Li, Yinchuan, Hao, Jianye, Gao, Longxiang, Wang, Michael Yu, Nie, Liqiang"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Lv_Spatial-Temporal_Graph_Diffusion_Policy_with_Kinematic_Modeling_for_Bimanual_Robotic_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: "面向双手操控的模仿学习扩散策略,结合运动学建模"
tldr: "模仿学习在双手操控任务中取得了显著进展,但现有方法在预测末端执行器位姿时往往忽略机器人物理结构与运动学约束,容易产生自碰撞与不可行的关节姿态。本文提出 KStar Diffuser,一种融合运动学信息的时空图扩散策略。该方法在扩散过程中显式建模机器人的物理结构与关节限制,从而生成更合理、可执行的操控动作。在多项双手操控基准上的实验表明,所提方法在可行性与任务性能方面均优于已有扩散策略。该工作推动了复杂双手操控任务下可执行模仿学习策略的发展。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 733, \"height\": 468, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1804, \"height\": 844, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 819, \"height\": 425, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1767, \"height\": 912, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1626, \"height\": 901, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 823, \"height\": 283, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-lv-spatial-temporal-graph-diffusion-policy-with-kinematic-modeling-for-bimanual-robotic-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 801, \"height\": 214, \"label\": \"Table\"}]"
motivation: "现有模仿学习方法在双手操控中常忽略机器人物理结构与运动学约束,导致自碰撞与不可行动作。"
method: "提出 KStar Diffuser,在时空图扩散过程中显式融入机器人结构与关节运动学约束。"
result: "在双手操控基准上,该方法在可行性与任务性能方面均优于已有扩散策略。"
conclusion: 为复杂双手操控任务下兼顾物理可行性的模仿学习策略提供了新的设计思路。
---

## Abstract
Despite the significant success of imitation learning in robotic manipulation, its application to bimanual tasks remains highly challenging. Existing approaches mainly learn a policy to predict a distant next-best end-effector pose (NBP) and then compute the corresponding joint rotation angles for motion using inverse kinematics. However, they suffer from two important issues: (1) rarely considering the physical robotic structure , which may cause self-collisions or interferences, and (2) overlooking the kinematics constraint , which may result in the predicted poses not conforming to the actual limitations of the robot joints. In this paper, we propose Kinematics enhanced Spatial-TemporAl gRaph Diffuser (KStar Diffuser). Specifically, (1)to incorporate the physical robot structure information into action prediction, KStar Diffuser maintains a dynamic spatial-temporal graph according to the physical bimanual joint motions at continuous timesteps. This dynamic graph serves as the robot-structure condition for denoising the actions; (2) to make the NBP learning objective consistent with kinematics, we introduce the differentiable kinematics to provide the reference for optimizing KStar Diffuser. This module regularizes the policy to predict more reliable and kinematics-aware next end-effector poses. Experimental results show that our method effectively leverages the physical structural information and generates kinematics-aware actions in both simulation and real-world.

---

## 论文详细总结（自动生成）

<think>The user wants me to provide a detailed Chinese summary of the paper following a specific structure. Let me analyze the paper carefully and organize the content according to the 8 required points.

The paper is "Spatial-Temporal Graph Diffusion Policy with Kinematic Modeling for Bimanual Robotic Manipulation" (KStar Diffuser), published at CVPR 2025.

Let me go through each required section:

1. Core problem and meaning - bimanual manipulation with imitation learning, two issues: physical robot structure ignored (self-collisions) and kinematics constraints ignored

2. Methodology - KStar Diffuser with two key components: spatial-temporal graph and kinematics regularizer with differentiable forward kinematics

3. Experiments - RLBench2 simulation benchmark, real-world Cobot Agilex ALOHA, compared with ACT, RVT-LF, PerAct-LF, PerAct2, DP-J, DP-EE, DP3

4. Resources/compute - not explicitly mentioned in the paper

5. Number of experiments - 5 simulation tasks with 20 and 100 demos, 2 real-world tasks with 100 demos, ablation study

6. Main conclusions - outperforms baselines by over 10% in real-world, over 20% in simulation

7. Strengths - explicit structure modeling, kinematics regularizer, comprehensive experiments

8. Limitations - mentioned briefly

Let me write this in a structured Markdown format in Chinese.</think>

# 论文总结：KStar Diffuser —— 融合运动学建模的时空图扩散策略用于双手机器人操控

## 1. 核心问题与研究动机

- **背景**：模仿学习在单臂操控任务中已取得显著成功，但其向双手机器人操控（Bimanual Manipulation）任务扩展时面临独特挑战——双臂需要协调运动，同时必须严格服从物理约束。
- **主流方案的局限**：现有方法多采用"两阶段管线"——先预测"下一最优末端位姿"（Next-Best end-effector Pose, NBP），再通过逆运动学（IK）求解关节角度。然而，这种范式存在两大根本缺陷：
  - **忽视机器人物理结构**：仅使用低维本体感知向量（如夹爪旋转角或末端位姿），未建模双臂间的空间拓扑关系、运动链结构与关节配置，易导致**自碰撞（self-collision）与双臂干涉**。
  - **忽视运动学约束**：IK 常作为后处理步骤，与位姿学习目标脱钩，导致预测位姿在笛卡尔空间看似平滑，却在接近**运动学奇异点或关节极限**时映射出不可行的关节轨迹。
- **研究意义**：将结构与运动学约束融入策略学习框架，使预测的双臂动作既满足任务目标又满足物理可行性，是推动双手机器人操控走向真实部署的关键。

## 2. 方法论

### 2.1 整体框架：KStar Diffuser
核心思想是：**机器人物理结构与运动学特性应作为条件驱动位姿预测，而非作为独立的后处理约束**。框架包含两大创新模块——时空机器人图（Spatial-Temporal Robot Graph）与运动学正则化器（Kinematics Regularizer）。

### 2.2 关键技术细节

#### (a) 多模态融合主干网络
- 输入：语言指令 $\ell$、多视角 RGB-D 观测 $o$、历史 $n$ 帧观测（文中 $n=2$）。
- 使用 Transformer 编码器提取图像特征 $E_I$ 与文本特征 $E_T$，并通过 $l_{FiLM}$ 个 FiLM 层进行跨模态融合，输出隐状态 $H_B$。
- 采用关键帧发现（Keyframe Discovery）筛选 Kξ 个关键点，对 6D 末端位姿 $\mathbf{a}_{EE}$ 进行预测。

#### (b) 时空机器人图（Spatial-Temporal Robot Graph）
- **空间结构图构建**：基于 URDF 描述文件，将双臂系统建模为无向图 $G_s = \langle V, E \rangle$，节点代表关节、边代表连杆关系。每个节点特征 $f_i \in \mathbb{R}^D$ 由三部分拼接而成：
  1. **关节坐标** $f_i^{JC} = [x_i, y_i, z_i]$：关节在笛卡尔坐标系下的绝对坐标，按工作空间归一化；
  2. **关节距离** $f_i^{JD}$：节点 $v_i$ 与其他所有节点的欧氏距离（$m$ 维向量）；
  3. **机体标签** $f_i^{BL} = [0,1]$：区分左/右臂的一热向量，捕捉对称运动模式。
- **时空图扩展**：将历史 $T$ 个时间步的空间图 $\{G_s^i\}_{i=0}^{T-1}$ 联合，并新增**跨时间边** $E'$，连接同一关节在不同时间步的节点，从而建模关节的连续运动相关性。
- **图特征学习**：使用图卷积网络（GCN）在时空图上传播与聚合节点特征，最终隐状态 $H_G$ 作为机器人结构表征，去条件化扩散去噪过程。

#### (c) 运动学正则化器（Kinematics Regularizer）
- **可微正向运动学（DFK）**：给定关节配置 $\Theta = [\theta_1, ..., \theta_n]$，正向运动学 $f_{FK}: \mathbb{R}^n \to SE(3)$ 是可微映射，能够将梯度从位姿损失回传至关节空间。
- **关节空间辅助监督**：将主干隐状态 $H_B$ 与图特征 $H_G$ 拼接后投影至关节空间，预测 $\hat{\mathbf{a}}_{joint}$，通过 DFK 得到参考末端位姿 $H_R$。
- **条件扩散过程**：以 $H_R$ 为附加条件驱动扩散去噪，使生成的末端位姿序列始终落在 IK 求解器的可行域内。
- **总损失**：
$$
L = \lambda L_{EE} + (1 - \lambda) L_{joint}
$$
其中 $L_{EE}$ 为末端位姿的 MSE 扩散损失，$L_{joint}$ 为关节角度的 MSE 监督损失，$\lambda$ 为权衡系数。

#### (d) 训练与推断
- 训练：从高斯噪声出发，按 DDPM 公式迭代去噪；通过前向过程 $a^k = \sqrt{\alpha_k}a^0 + \sqrt{1-\alpha_k}\epsilon$ 添加噪声。
- 推断：从 $a^K \sim \mathcal{N}(0, I)$ 出发，经 $K$ 步去噪得到 $a^0_{EE}$ 用于执行；IK 求解器将末端位姿转换为关节角以实际控制机器人。

## 3. 实验设计

### 3.1 数据集与场景
- **仿真基准**：使用 **RLBench2**（RLBench 扩展版，专为双手操控设计），包含 5 项任务——Push Box、Lift Ball、Handover Item (easy)、Pick Laptop、Sweep Dustpan。
- **真实世界**：基于 **Cobot Agilex ALOHA** 双臂机器人平台，部署 2 项任务——Lift Plate 与 Handover（物体交接）。
- **演示数量**：在仿真中分别使用 **20 与 100** 两个规模的演示数据训练，在真实世界中使用 100 个演示训练，**每任务测试 15 次**。

### 3.2 对比方法（共 7 个）
- **基于 Transformer**：
  - ACT（Action Chunking Transformer，CVAE 编解码）
  - RVT-LF（多视角 Transformer + leader-following）
  - PerAct-LF（Perceiver Transformer + leader-following，体素动作预测）
  - PerAct2（双统一特征空间 + 协同自注意力）
- **基于扩散模型**：
  - DP-J（扩散策略，预测关节角）
  - DP-EE（重新实现的扩散策略，预测末端位姿）
  - DP3（融合点云的 3D 扩散策略）

## 4. 资源与算力
- 论文**未明确披露**所使用的 GPU 型号、数量、训练时长或总计算资源消耗，这一点在文中没有具体说明，属于值得关注的透明度缺口。

## 5. 实验数量与充分性

- **仿真实验**：5 个任务 × 2 个演示规模 × 3 个随机种子，结果以均值 ± 标准差报告。
- **真实世界实验**：2 个任务 × 1 个演示规模 × 15 次测试。
- **消融实验**：在 Handover Item 任务（仿真 + 真实）上逐步去除 KR（运动学正则化器）与 ST Graph（时空图），形成三组对比（完整 / 仅去 KR / 双移除）。
- **定性分析**：在仿真与真实任务上对比 KStar Diffuser 与 DP3、PerAct2 的执行轨迹。
- **充分性评估**：
  - 实验涵盖多任务、多演示规模、多基线，**公平性较好**（同一基准、统一评估指标成功率为最终目标达成率）。
  - 但**真实世界任务仅 2 个、每任务 15 次测试**，样本量较小，统计显著性可能受限。
  - **基线差异较大**：部分基线（如 ACT、DP3）是为单臂设计的直接迁移方案，对比可凸显方法针对性改进，但也可能拉大差距，使数字对比偏乐观。

## 6. 主要结论与发现

- **仿真性能显著领先**：KStar Diffuser 在 20 demos 下整体成功率 **58.0%（领先次优 24.9% 约 33 个百分点）**；100 demos 下达到 **68.2%（领先次优 40.5% 约 27.7 个百分点）**；在 Lift Ball 与 Pick Laptop 上表现尤为突出（Pick Laptop 89.0% vs 次优 69.7%）。
- **真实世界结果**：整体成功率 **43.1%（领先 PerAct2 29.9% 约 13.2 个百分点）**，尤其在 Handover 任务上实现 19.7%（对比 PerAct2 仅 8.8%）。
- **消融结论**：
  - **KR 模块**对真实环境尤为重要——去除后真实成功率从 19.7% 降至 15.3%，原因在于真实场景存在传感器噪声与光照反射等扰动，缺乏运动学正则化时策略更易违反关节约束；
  - **ST Graph** 对双臂协同至关重要——同时移除两个组件后仿真与真实性能均显著下降（23.4% → 14.8% 整体），证明了时空图对建模双臂空间-时间依赖性的有效性。
- **定性发现**：KStar Diffuser 能在笔记本电脑紧贴桌面的 Pick Laptop 任务中生成"一臂推开、一臂抓取抬起"的协同轨迹，验证了对双臂协调模式的捕获能力。

## 7. 论文优点与方法亮点

- **物理结构显式建模**：首次在双手操控扩散策略中引入 URDF 驱动的时空图，将运动链、关节类型与双臂拓扑关系显式编码，而非简单拼接低维本体感知向量。
- **可微运动学正则化**：通过 DFK 将关节空间监督与末端位姿学习目标联合优化，缓解了 IK 不可行的位姿预测问题。
- **结构化特征设计**：节点特征融合坐标、距离与机体标签，使 GCN 能同时感知局部几何与双臂对称性。
- **实验覆盖较全面**：仿真 5 任务、真实 2 任务、含消融与定性可视化，并提供多演示规模的对比。
- **可扩展性强**：模块化设计（图 + 运动学正则化器）可与多种扩散骨干或视觉编码器组合。

## 8. 不足与局限

- **算力透明度不足**：未报告训练资源（GPU 类型/数量/时长），难以复现与对比计算成本。
- **真实世界样本偏少**：仅 2 个真实任务、每任务 15 次测试，统计置信度受限。
- **基线对照不完全公平**：部分 Transformer 基线（如 ACT、DP-J）基于关节角预测，与 KStar Diffuser 基于末端位姿的预测范式不同；统一的 IK 后处理也可能放大 KStar 在运动学可行性上的优势。
- **任务范围有限**：仿真任务集中于桌面级协同操作，未涵盖形变物体、长序列任务或移动操控等更复杂场景。
- **依赖 URDF 与既定机械臂**：方法的强结构性依赖给迁移到异构机械臂（如非固定拓扑或柔性臂）带来挑战。
- **超参数与细节部分缺失**：$\lambda$ 权衡系数、关键帧发现算法、IK 求解器具体实现等细节依赖附录，全文未给出系统超参数分析。
- **可解释性依赖可视化**：双臂协同优势主要通过轨迹定性展示，缺乏更精细的可解释性分析（如对各模块注意力的可视化）。

（完）
