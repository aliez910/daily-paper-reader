---
title: "MoManipVLA: Transferring Vision-language-action Models for General Mobile Manipulation"
title_zh: MoManipVLA：面向通用移动操作的视觉-语言-动作模型迁移
authors: "Wu, Zhenyu, Zhou, Yuheng, Xu, Xiuwei, Wang, Ziwei, Yan, Haibin"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wu_MoManipVLA_Transferring_Vision-language-action_Models_for_General_Mobile_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 迁移视觉-语言-动作模型以实现通用机器人操作
tldr: 传统移动操作方法因缺乏大规模训练数据而难以跨任务与跨环境泛化，而现有VLA基础模型主要针对固定基座操作。本文提出MoManipVLA，一个高效的策略适配框架，将预训练的固定基座VLA模型迁移到移动操作场景。该方法充分利用VLA基础模型的强泛化能力，实现了跨任务与跨环境的高性能移动操作。该工作直接推动了通用视觉-动作模型在机器人领域的发展，对构建通用机器人系统具有重要价值。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1778, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1799, \"height\": 709, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1795, \"height\": 770, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1733, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1771, \"height\": 448, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-momanipvla-transferring-vision-language-action-models-for-general-mobile-manipulation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 238, \"label\": \"Table\"}]"
motivation: 现有VLA基础模型面向固定基座，难以直接应用于移动操作任务。
method: 提出高效的策略适配框架，将预训练固定基座VLA模型迁移至移动操作。
result: 在移动操作场景中实现了跨任务与跨环境的高泛化能力。
conclusion: MoManipVLA将VLA模型的通用能力扩展到移动操作领域。
---

## Abstract
Mobile manipulation is the fundamental challenge for robotics to assist humans with diverse tasks and environments in everyday life. However, conventional mobile manipulation approaches often struggle to generalize across different tasks and environments because of the lack of large-scale training.In contrast, recent advances in vision-language-action (VLA) models have shown impressive generalization capabilities, but these foundation models are developed for fixed-base manipulation tasks.Therefore, we propose an efficient policy adaptation framework to transfer pre-trained VLA models of fix-base manipulation to mobile manipulation, so that high generalization ability across tasks and environments can be achieved in mobile manipulation policy.Specifically, we utilize pre-trained VLA models to generate waypoints of the end-effector with high generalization ability. We design motion planning objectives for the mobile base and the robot arm, which aim at maximizing the physical feasibility of the trajectory. Finally, we present an efficient bi-level objective optimization framework for trajectory generation, where the upper-level optimization predicts waypoints for base movement to enhance the manipulator policy space, and the lower-level optimization selects the optimal end-effector trajectory to complete the manipulation task. Extensive experimental results on OVMM and the real world demonstrate that our method achieves a 4.2% higher success rate than the state-of-the-art mobile manipulation, and only requires 50 training cost for real world deployment due to the strong generalization ability in the pre-trained VLA models.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "MoManipVLA: Transferring Vision-language-action Models for General Mobile Manipulation" following a specific structure with 8 points. Let me analyze the paper carefully and provide a comprehensive summary.

Let me organize my thoughts based on the paper content:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I'll write this in Chinese with Markdown formatting.
</think>
# MoManipVLA 论文总结

## 1. 核心问题与整体含义

**研究背景：** 移动操作（Mobile Manipulation）是机器人服务人类的关键能力，需要移动底盘与机械臂的协同控制以完成跨空间任务。

**核心矛盾：**
- 传统移动操作方法（端到端模仿学习 / 模块化方法）因专家数据采集成本高昂，训练规模受限，泛化能力差；
- 近期 VLA（Vision-Language-Action）基础模型虽具备强大跨任务/跨环境泛化能力，但主要面向**固定基座**操作，无法直接输出底盘与机械臂的协同动作。

**研究目标：** 提出一个高效策略适配框架，将预训练固定基座 VLA 模型的强泛化能力迁移到移动操作任务中，仅需极少量真实数据即可部署。

---

## 2. 方法论

**核心思想：** 不直接让 VLA 模型输出底盘-臂联合动作，而是将其"降级"为**末端执行器（end-effector）航点预测器**，再通过基于物理可行性的轨迹优化生成底盘与机械臂的协同运动。

**关键技术细节：**

**(1) VLA 航点生成**
- 使用预训练 **OpenVLA-7B** 作为固定基座策略网络；
- 输入：当前 RGB 图像、机器人本体感知状态（基座位姿、末端位姿、夹爪开合度）、语言指令；
- 输出：末端执行器在基座坐标系下的航点 $Q_i$；
- 通过坐标变换 $\Gamma$ 将其映射到世界坐标系 $\hat{Q}_i$。

**(2) 运动规划目标函数（公式 6）**
整体目标由三项加权构成：
$$O = \lambda_1 F_r + \lambda_2 F_s + \lambda_3 F_c$$

- **可达性代价 $F_r$（公式 3）：** 使用 Pinocchio IK 求解器迭代次数衡量——$N_{IK} \leq N_{max}$ 时返回归一化迭代数；超过则赋予大常数 $C_0$，代表不可达；
- **平滑性代价 $F_s$（公式 4）：** 惩罚相邻时刻机械臂关节角与基座本体状态的二范数差；
- **碰撞代价 $F_c$（公式 5）：** 利用 **nvblox** 构建场景 ESDF（欧氏距离场），在机器人表面随机采样 $N_q$ 个查询点，统计距障碍物表面小于安全阈值 $\epsilon_0$ 的违反量。

**(3) 双层轨迹优化（Algorithm 1）**
- **上层（基座更新）：** 用 Dual Annealing 全局搜索 + SLSQP 局部优化，仅更新基座位姿，目标是扩张机械臂可达操作空间；评价标准为搜索空间的期望代价与 Top-k 代价的加权和（公式 7）；
- **下层（末端更新）：** 固定上层得到的基座航点，搜索最佳末端执行器轨迹以贴合 VLA 预测航点；
- **停止条件：** 末端位姿与 VLA 预测航点距离小于公差 $\mu_s$；
- **类比依据：** 借鉴人形机器人将高维动作分解为上下身的思路（文中类比 39-DoF 分解为 27+12）。

**整体流程：** 输入图像与语言 → VLA 预测末端航点 → 航点经坐标变换到世界系 → 双层优化生成底盘-臂协同轨迹 → 真实执行。

---

## 3. 实验设计

**数据集与基准：**
- **OVMM（Open Vocabulary Mobile Manipulation）基准**：包含 60 个类家庭场景、18k+ 日常 3D 物体；任务定义为"将目标物体从容器 A 移至容器 B"，需顺序执行 Nav→Gaze→Pick→Nav→Place 五个阶段；使用 Hello Robot Stretch；
- **真实环境：** 采用 hexman echo plus 底盘 + RM65 机械臂，Intel RealSense T265 跟踪相机；ESDF 用 nvblox 重建；语义分割用 Grounding SAM。

**对比方法：**
- **OVMM 仿真：** UniTeam、OVMM(RL)、OVMM(Heuristic)、RoboAI、KUZHUM；
- **真实环境：** 无显式对比基线，但测试了三类任务（堆叠方块、打开抽屉、放入碗）。

**评价指标：** 部分成功率（FindObj/Pick/FindRecep）、总体成功率、平均步数、推理时延（Latency）。

---

## 4. 资源与算力

- **微调硬件：** 4 张 **RTX 3090 GPU**；
- **微调数据：** 收集 200 条 pick-and-place 演示，使用 LoRA 在 **OpenVLA-7B** 上微调 **10K epochs**；
- **真实部署成本：** 仅需 **50 条专家样本**完成微调即可部署；
- **中间步数设置：** 根据相邻航点位姿变化与步长 0.05 计算；
- **超参数：** $\lambda_1=10.0, \lambda_2=1.0, \lambda_3=0.6$，安全阈值 $\epsilon_0=0.1$；
- **论文中未明确说明：** 训练总时长（小时数）、双层优化的具体耗时分解、4 卡并行策略的细节。

---

## 5. 实验数量与充分性

**实验规模：**
- 1 项 OVMM 主对比（表 1）+ 1 项消融（表 2）+ 1 项失败案例统计（表 3）+ 1 项真实环境测试（表 4）；
- 消融研究较系统：分别去除可达性、平滑性、碰撞项；对比 Bi-level 与 Direct 搜索；对比 GT mask 与 Detic 分割；
- 真实环境每任务 10 次试验（样本量较小）。

**充分性评价：**
- **优点：** 在公开基准上覆盖多类基线，含五阶段细粒度分解，并附带失败模式分析，方法层面消融完整；
- **不足：**
  - 真实实验每任务仅 10 次，统计显著性不足；
  - 消融虽多但缺少对 VLA 选型（OpenVLA-7B vs 其他 VLA）的对比；
  - 没有跨场景（如不同房间布局、不同光照）的鲁棒性测试；
  - 真实环境缺少与其他移动操作基线（如 SPIN、OK-Robot）的直接对比。

---

## 6. 主要结论与发现

1. **性能领先：** 在 OVMM 上比 SOTA 高 **4.2% 总体成功率、11.2% 部分成功率**（49.4% vs KUZHUM 38.2%）；
2. **低部署成本：** 真实环境仅需 50 条专家样本微调即可达 40% 成功率（堆叠任务 30%、放入碗 40%、开抽屉 10%）；
3. **效率均衡：** 平均步数接近启发式方法，推理时延接近 RL 方法（≈693ms）；
4. **组件贡献排序：** 可达性项影响最大（移除后 SR 暴跌至 11.3%），平滑性次之，碰撞项最弱（影响约 0.5%）；
5. **双层优化有效：** 在保持接近的成功率下将延迟从 742.9ms 降至 693.1ms；
6. **失败主因：** "Orient to place"占 72.09%，说明基座导航对齐仍是核心瓶颈。

---

## 7. 优点

- **方法论创新性强：** 首次系统性地将"固定基座 VLA → 移动操作"的迁移问题转化为"航点引导 + 物理可行优化"，思路清晰；
- **物理可行性建模完整：** 显式建模可达性、平滑性、碰撞三个维度，引入 ESDF 与 IK 迭代次数作为软约束；
- **搜索效率优化：** 双层分解缓解了 10-DoF 搜索空间的维度灾难，引入 Dual Annealing + SLSQP 混合策略；
- **数据效率突出：** 50 条样本即可真实部署，凸显对预训练 VLA 泛化能力的成功利用；
- **失败分析透明：** 明确报告了失败模式分布（Table 3），便于后续研究定位改进点；
- **代码/项目页开放：** 提供项目页便于复现。

---

## 8. 不足与局限

- **依赖 VLA 上限：** 性能天花板受 VLA 模型本身限制，且 VLA 仅在高度受限的运动空间内有效（论文自承）；
- **泛化平台受限：** 当前方法仅针对特定移动平台（基座+机械臂结构），其他移动平台需要重新设计运动规划约束（论文自承）；
- **缺少任务规划：** 无长视野（long-horizon）任务规划模块，对需要多阶段推理的复杂任务处理能力不足（论文自承）；
- **真实实验统计薄弱：** 每任务仅 10 次试验，抽屉任务仅 10% 成功率，证据力有限；
- **视觉感知瓶颈：** 替换为 Detic 后 SR 暴跌至 11.3%，暴露对分割质量的强依赖；
- **公平性风险：** VLA 微调使用了 200 条 OVMM 启发式策略的演示，但对比基线（如 KUZHUM）的数据规模未严格对齐；
- **应用场景限制：** 当前主要在仿真与简化家庭任务验证，未涉及工业、物流等高动态场景。

（完）
