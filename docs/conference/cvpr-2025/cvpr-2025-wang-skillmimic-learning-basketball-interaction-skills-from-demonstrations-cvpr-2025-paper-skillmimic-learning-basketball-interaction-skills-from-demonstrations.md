---
title: "SkillMimic: Learning Basketball Interaction Skills from Demonstrations"
title_zh: SkillMimic：从演示中学习篮球交互技能
authors: "Wang, Yinhuai, Zhao, Qihan, Yu, Runyi, Tsui, Hok Wai, Zeng, Ailing, Lin, Jing, Luo, Zhengyi, Yu, Jiwen, Li, Xiu, Chen, Qifeng, Zhang, Jian, Zhang, Lei, Tan, Ping"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_SkillMimic_Learning_Basketball_Interaction_Skills_from_Demonstrations_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 基于演示的人-物交互模仿学习
tldr: 传统人-物交互强化学习依赖手工设计的技能奖励，难以在多样化交互间泛化。本文提出 SkillMimic 框架，从 HOI 数据集中提取统一的模仿奖励，从而摆脱对技能专属奖励设计的依赖。该统一奖励能捕捉多样交互模式的本质，使单一策略可掌握多种技能并支持技能间的平滑切换。在篮球等交互任务上的实验表明，多样性与泛化能力随数据集规模增长而提升。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1802, \"height\": 377, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 858, \"height\": 294, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1605, \"height\": 765, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 866, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 861, \"height\": 430, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1769, \"height\": 500, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 861, \"height\": 269, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 1801, \"height\": 276, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1790, \"height\": 310, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1813, \"height\": 208, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-skillmimic-learning-basketball-interaction-skills-from-demonstrations-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 842, \"height\": 285, \"label\": \"Table\"}]"
motivation: 传统 RL 的人-物交互方法依赖手工设计的技能奖励，跨交互泛化能力差且劳动密集。
method: 提出统一的 HOI 模仿奖励，从大规模交互数据集中自动捕获多样交互模式以训练单一策略。
result: 单一策略可掌握多种篮球交互技能并实现技能过渡，性能随数据集增大而提升。
conclusion: 数据驱动的统一模仿奖励可替代手工奖励，实现可扩展的人-物交互技能学习。
---

## Abstract
Traditional reinforcement learning methods for human-object interaction (HOI) rely on labor-intensive, manually designed skill rewards that do not generalize well across different interactions. We introduce SkillMimic, a unified data-driven framework that fundamentally changes how agents learn interaction skills by eliminating the need for skill-specific rewards. Our key insight is that a unified HOI imitation reward can effectively capture the essence of diverse interaction patterns from HOI datasets. This enables SkillMimic to learn a single policy that not only masters multiple interaction skills but also facilitates skill transitions, with both diversity and generalization improving as the HOI dataset grows. For evaluation, we collect and introduce two basketball datasets containing approximately 35 minutes of diverse basketball skills. Extensive experiments show that SkillMimic successfully masters a wide range of basketball skills including stylistic variations in dribbling, layup, and shooting. Moreover, these learned skills can be effectively composed by a high-level controller to accomplish complex and long-horizon tasks such as consecutive scoring, opening new possibilities for scalable and generalizable interaction skill learning. Project page: https://ingrid789.github.io/SkillMimic/

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "SkillMimic: Learning Basketball Interaction Skills from Demonstrations" following a specific structure. Let me analyze the paper carefully and provide a comprehensive summary.

The paper is about:
- Learning basketball interaction skills from demonstrations
- A unified data-driven framework that doesn't require skill-specific rewards
- Uses Contact Graph reward for precise interaction imitation
- Two datasets: BallPlay-V and BallPlay-M
- A high-level controller for skill composition
- Hierarchical approach for complex tasks

Let me organize the summary according to the requested structure.
</think>
# SkillMimic 论文详细总结

## 1. 核心问题与研究动机

- **核心问题**：传统基于强化学习（RL）的人-物交互（HOI）方法严重依赖**手工设计的技能专属奖励函数**，不仅劳动密集，而且难以在多样化的交互技能间泛化。
- **具体挑战**：在篮球等高度复杂的运动场景中，需要掌握投篮、上篮、运球、捡球等多种动态精确的交互技能；现有方法（如 DeepMimic、AMP、ASE）只能学习孤立的运动技能或简单交互（如打柱子、搬箱子），无法用一个统一策略学习多种交互技能，更难以完成连续得分等多阶段长时任务。
- **研究动机**：受人类业余篮球爱好者通过**观看并模仿比赛录像**自学技能的启发，提出一种纯数据驱动的方法，让仿人智能体从 HOI 演示中自动学习多样化交互技能，**消除对技能专属奖励设计的依赖**。

## 2. 方法论

### 2.1 核心思想
- 将**交互技能定义为参考 HOI 状态转移的集合**：当智能体能操控物体产生与参考状态转移一致的 HOI 序列时，即认为掌握了该技能。
- 关键洞察是：**统一的 HOI 模仿奖励**可以从数据集中有效捕捉多样交互模式的本质。

### 2.2 BallPlay 数据集
- **BallPlay-V**：基于单目 RGB 视频估计，包含 8 个不同篮球技能片段。
- **BallPlay-M**：基于多视角光学动捕系统，**约 35 分钟**的综合篮球交互数据。
- 数据采用带技能标签的片段组织，作为参考 HOI 状态转移。

### 2.3 训练流程（IS 策略）
- 输入：HOI 状态 $s_t = \{o_t^{prop}, o_t^{f}, o_t^{obj}\}$，包括人形本体感知、指尖接触力、物体观测，加上 one-hot 技能标签 $c_j$。
- 输出：高斯策略网络（1024-512-512 三层 MLP，ReLU 激活）输出关节目标旋转，由 PD 控制器执行。
- 训练时随机选取一个片段帧初始化状态，PD 控制仿真推演下一状态，重复直至跌倒或达到最大长度。

### 2.4 统一 HOI 模仿奖励
- **总奖励公式**：$r_t = r_t^{bt} \cdot r_t^{ot} \cdot r_t^{rel} \cdot r_t^{reg} \cdot r_t^{cg}$，**采用乘法组合**而非加法（避免子奖励不平衡陷入局部最优）。
- 子奖励组成：
  - $r_t^{bt}$：身体运动学模仿（关节位置、旋转及其速度）。
  - $r_t^{ot}$：物体运动学模仿。
  - $r_t^{rel}$：相对运动奖励（强调 HOI 相对关系）。
  - $r_t^{reg}$：自适应速度正则（抑制高频抖动）。
  - $r_t^{cg}$：**接触图（Contact Graph）奖励**——核心创新。

### 2.5 接触图（Contact Graph, CG）
- 定义为完全图 $G = \{V, E\}$：节点存储是否与其他节点接触的二元值，**边**存储两节点间是否接触。
- 节点定义灵活：篮球场景下聚合为 3 个节点——双手、其余身体、球。
- **CG 奖励**：$r_t^{cg} = \exp(-\sum_{j=1}^{J} \lambda_{cg}[j] \cdot e_{cg,t}[j])$，其中 $e_{cg,t} = |s_{cg,t} - \hat{s}_{cg,t}|$ 为仿真与参考 CG 边集的绝对差。
- **关键作用**：避免"运动学局部最优"——如用头扶球、用腕部夹球、用双手撑桌保持平衡等错误接触模式（见 Fig. 5）。

### 2.6 高级控制器（HLC）与技能复用
- HLC 输入：当前 HOI 状态 $s_t$ + 任务观测 $h_t$（如篮筐位置）。
- 输出：离散技能嵌入 $c_t$ 驱动预训练 IS 策略。
- 实现的任务：投掷（Throwing）、朝目标运球（Heading）、绕圈运球（Circling）、连续得分（Scoring）。

## 3. 实验设计

### 3.1 数据集与场景
- **BallPlay-V**（8 个技能视频片段）+ **BallPlay-M**（35 分钟动捕数据）。
- **GRAB**（外部数据集，用于消融验证）。
- 仿真仿人智能体学习约 **10 种篮球技能**：投篮、跳投、篮板、传球、上篮、转身挑篮、各种运球（左/右/前/转）、捡球、交叉步等。

### 3.2 评估指标
- **Acc.**：每帧物体位置误差 < 0.2 m 且身体 MPJPE < 0.1 m 且接触正确时的整体 HOI 模仿准确率。
- **Eb-mpjpe / Eo-mpjpe**：身体与物体的平均每关节位置误差（mm）。
- **Ecg**：接触图误差（0~1）。
- **Success Rate**：技能执行成功率。

### 3.3 对比方法
- **DeepMimic\***：将 DeepMimic 风格的奖励适配到含物体场景。
- **AMP\***：将 AMP 对抗模仿奖励适配到含物体场景。
- **PPO**：从零学习。
- **ASE**：基于身体运动先验的低层策略。
- **ASE\***：基于身体+物体运动先验。
- 自己的 **SkillMimic**（含/不含 CGR、含/不含乘法组合）。

## 4. 资源与算力
- 论文中**明确提及**的算力信息较少，仅在部分场景提到：
  - **Scoring 任务 HLC 训练**：在 **NVIDIA RTX 4090 GPU** 上**约 3 小时**完成。
  - IS 策略训练规模：在 BallPlay-M 上约 **4.5 × 10⁹ 样本**（约 45 亿），覆盖 7 项技能。
  - 高级任务训练：投掷/朝目标/绕圈各约 0.4 × 10⁹ 样本；Scoring 约 1.2 × 10⁹ 样本。
  - 捡球数据规模消融训练：每个数据集规模约 **3.2 × 10⁹ 样本**。
- 仿真环境未明确说明（推测为 Isaac Gym/PhysX 类物理仿真器，但未在正文明示）。
- **未明确说明** GPU 数量、CPU 资源、IS 策略总体训练时长、基线方法的算力消耗。

## 5. 实验数量与充分性

- **交互技能学习**：
  - Tab. 2：在 4 个典型技能上与 DeepMimic\*、AMP\* 对比成功率。
  - Tab. 1：在 GRAB 与 BallPlay-V 上做奖励设计消融（乘法 vs 加法、CGR 是否引入），给出 Acc./MPJPE/Eo-mpjpe/Ecg 多维度量化结果。
  - Fig. 5：4 组定性消融展示 CGR 关键作用。
  - Fig. 7 + Fig. 8：捡球技能的 1/10/40/131 个片段数据规模消融，并测试 1~5 m 距离的泛化能力（1000 次随机摆放测试）。
- **高级任务**：
  - Tab. 3：在 4 个高级任务（Heading/Circling/Throwing/Scoring）上对比 PPO/ASE/ASE\*/SkillMimic 的成功率。
  - Fig. 9：定性展示技能手动切换与高级任务执行轨迹。
- **充分性评价**：
  - 优点：消融较为系统（奖励组成、数据规模、关键模块 CGR），覆盖定量与定性，提供失败模式可视化。
  - 不足：缺乏与近期专门 HOI 模仿方法（如 PhysHOI、PNP 等）的直接对比；与 PPO/ASE\* 的高级任务对比仅在 4 个任务上，**未做统计显著性检验**；技能数虽多但每技能展示的指标有限（如仅 Tab. 2 给 4 个技能的成功率）。

## 6. 主要结论与发现
- **统一模仿奖励可替代手工设计**：单一 IS 策略在**完全相同的超参数配置**下能学会投篮、上篮、运球、捡球等多种篮球技能。
- **CGR 是关键**：去除 CGR 时，智能体陷入运动学局部最优（如用头/腕部代偿），加上 CGR 后接触精度大幅提升（Ecg 在 BallPlay-V 上从 0.412 降至 0.087）。
- **乘法组合优于加法**：避免子奖励不平衡，提升整体精度。
- **数据可扩展性显著**：捡球技能在 1/10/40/131 个片段训练后泛化成功率从 0.5% 跃升至 85.6%，验证了"数据越大、泛化越强"的标度律。
- **基于交互先验的 HLC 显著加速复杂任务学习**：Scoring HLC 仅需 3 小时即可达到 80.25% 成功率，而 PPO/ASE/ASE\* 在 4 个高级任务上**全部接近 0%**。
- **首次实现连续篮球得分**：通过 HLC 组合多种交互技能，智能体能完成"运球→上篮→捡篮板→再上篮"的连续得分长时任务。

## 7. 方法与实验的亮点
- **统一数据驱动范式**：彻底摆脱"一技能一奖励"的设计瓶颈，具有强可扩展性。
- **接触图（CG）的提出**：以图结构显式建模交互接触，是简洁且通用的方案。
- **乘法奖励设计**：在多子奖励系统中防止某一子奖励被压制，引导均衡学习。
- **层次化结构（IS + HLC）**：以交互技能为高层先验，比传统运动先验更贴近任务需求。
- **数据标度律验证**：明确展示技能多样性/泛化能力随 HOI 数据增长而提升。
- **公开新数据集**：BallPlay-V 与 BallPlay-M 填补篮球 HOI 模仿数据空白。
- **首次实现仿真仿人连续篮球得分**这一极具展示力的长时任务。

## 8. 不足与局限
- **数据集规模与多样性有限**：BallPlay-M 虽号称 35 分钟，但相比动捕数据库的规模仍较小；BallPlay-V 仅 8 个片段。
- **缺乏与最新专用 HOI 方法的对比**：未与 PhysHOI、PNP、SAGA 等同期方法直接对照，难以判断在 HOI 模仿精度上的相对优势。
- **仿真到真实的迁移未涉及**：论文明确表示尚未迁移到真实机器人，而 Sim-to-Real 是该方向最终落地的关键瓶颈。
- **物体几何泛化未验证**：CG 节点定义依赖具体场景，物体类别/几何改变时需要重新设计节点。
- **多物体感知受限**：当前方法直接获取特权物体状态，无法处理多物体同时感知的真实环境。
- **评估的统计严谨性不足**：成功率指标多来自单次或少数种子训练，**未见多次种子的均值与标准差**，未做显著性检验。
- **基线在高级任务上全部失败**（0%），可能存在基线实现或奖励调优不充分的风险，**基线公平性存疑**。
- **算力与训练细节披露不充分**：GPU 数量、IS 训练总时长、仿真环境版本等关键信息缺失，再现性受限。
- **数据集采集成本**：动捕 35 分钟的精细篮球交互数据采集成本极高，可能限制该方法在更广泛 HOI 场景的推广。

（完）
