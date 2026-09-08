---
title: "AffordGen: Generating Diverse Demonstrations for Generalizable Object Manipulation with Affordance Correspondence"
title_zh: AffordGen：基于可供性对应生成多样化演示以实现可泛化物体操作
authors: "Zhang, Jiawei, Hu, Kaizhe, Huang, Yingqian, Ju, Yuanchen, Xue, Zhengrong, Xu, Huazhe"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhang_AffordGen_Generating_Diverse_Demonstrations_for_Generalizable_Object_Manipulation_with_Affordance_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 生成多样化演示数据并训练闭环视觉运动策略用于模仿学习
tldr: 当前机器人模仿学习策略受限于演示数据在几何变化下的多样性不足，难以泛化。为此，本文提出 AffordGen 框架，利用 3D 生成模型与视觉基础模型在大规模网格之间基于可供性关键点语义对应关系，合成多样化的机器人操作轨迹。基于该可供性感知数据集训练的闭环端到端视觉运动策略融合了语义泛化性与反应式鲁棒性。仿真与真实世界实验均表明该方法在几何变化下取得了显著的性能提升。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1735, \"height\": 727, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1419, \"height\": 786, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 841, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 839, \"height\": 262, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 214, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1785, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 832, \"height\": 335, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 828, \"height\": 279, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 780, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 829, \"height\": 222, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1800, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-affordgen-generating-diverse-demonstrations-for-generalizable-object-manipulation-with-affordance-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1600, \"height\": 622, \"label\": \"Table\"}]"
motivation: 现有模仿学习方法受限于演示数据多样性不足，难以应对几何变化带来的泛化挑战。
method: 利用 3D 生成模型与视觉基础模型，基于可供性关键点对应关系合成多样化操作轨迹，训练闭环视觉运动策略。
result: 仿真与真实世界实验均验证了所提方法在多种几何变化下均取得显著性能提升。
conclusion: 该工作将语义可供性与端到端反应式学习相结合，为提升机器人操作泛化能力提供新思路。
---

## Abstract
Despite the recent success of modern imitation learning methods in robot manipulation, their performance is often constrained by geometric variations due to limited data diversity. Leveraging powerful 3D generative models and vision foundation models (VFMs), the proposed AffordGen framework overcomes this limitation by utilizing the semantic correspondence of meaningful keypoints across large-scale 3D meshes to generate new robot manipulation trajectories. This large-scale, affordance-aware dataset is then used to train a robust, closed-loop visuomotor policy, combining the semantic generalizability of affordances with the reactive robustness of end-to-end learning. Experiments in simulation and the real world show that policies traine with AffordGen achieve high success rates and enable zero-shot generalization to truly unseen objects, significantly improving data efficiency in robot learning.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper "AffordGen" following a specific structure with 8 points. Let me analyze the paper carefully and produce a well-structured Markdown summary.

Let me go through the paper systematically:

1. Core problem: Imitation learning policies are limited by data diversity, especially geometric variations. Limited demonstrations constrain generalization.

2. Method: AffordGen framework - uses 3D generative models + VFMs (DINOv2) to establish semantic keypoint correspondences across large-scale 3D meshes, generates diverse trajectories, trains closed-loop visuomotor policy.

Key technical components:
- Source demo preprocessing (extracting grasp time, skill segment, affording point, function point, SAM2 segmentation)
- 3D mesh semantic correspondence via DINOv2 with multi-view rendering, normalized canonical space
- Trajectory generation: keypoint-constrained replay, motion planning for transition, point cloud generation
- Three stages: ΩG (grasp), ΩS (skill), ΩT (transition)
- Weighted average for keypoint correspondence

3. Experiments:
- Simulation: ManiSkill3, 4 tasks (teapot pouring, mug hanging, knife cutting, shoe organizing)
- Real world: same 4 tasks
- Baselines: DemoGen, CPGen, FUNCTO
- Cross-category: mug pouring, handbag hanging, saw cutting

5. Experiments:
- Multiple configurations of (#meshes × #demos per mesh): 20×50, 50×20, 100×10, 1000×1
- In-category + zero-shot cross-category
- Simulation + real world
- 4 tasks each

4. Resources: Not explicitly mentioned in the text I have access to

6. Conclusions: AffordGen boosts performance by 24.1% (sim) and 24.3% (real) over best baselines

7. Strengths: Novel use of affordance as generative prior, closes loop between affordance methods and end-to-end learning, zero-shot generalization

8. Limitations: 
- 3D meshes required
- Keypoint annotation still needed
- Limited to certain functional classes
- Performance vs number of unseen objects first increases then decreases
- Specific to manipulation with grasp+skill structure

Let me write the response.</think>

# AffordGen 论文总结

## 1. 核心问题与研究动机

- **数据多样性的瓶颈**：当前模仿学习（Visuomotor Imitation Learning）在机器人操作中虽然效果显著，但其推广部署受到两个根本性挑战阻碍：
  - 收集大规模、高质量人类演示的成本极高；
  - 学到的策略对训练中未遇到的新物体和场景泛化能力差。
- **现有合成数据方法的不足**：
  - 轨迹适配类方法（MimicGen、DemoGen、CPGen）虽然能从少量演示扩展出大量轨迹，但本质仍在源物体上做空间增强，语义范围受限，无法迁移到未见物体，且对姿态变化的处理能力有限；
  - 可供性（Affordance）方法（Robo-ABC、DenseMatcher、FUNCTO）依赖关键点对应将技能迁移到新物体，但多为开环规划（Planning-centric），依赖对应精度与规划算法，缺乏闭环反应能力。
- **研究目标**：将可供性知识作为数据生成的"生成式先验（Generative Prior）"，而非在线规划信号，以打通"语义泛化"与"端到端反应式学习"之间的壁垒。

---

## 2. 方法论

### 2.1 任务分解
- 将操作任务分解为三个阶段：$\Omega = \{\Omega_G, \Omega_S, \Omega_T\}$
  - $\Omega_G$（抓取阶段）：夹爪闭合抓取物体；
  - $\Omega_S$（技能阶段）：执行任务关键动作（如倾倒、对准）；
  - $\Omega_T$（过渡阶段）：连接前两阶段的无碰撞自由空间运动。
- 输入为点云观测（3D 点云更易操作生成新数据）。

### 2.2 源演示预处理（Source Demonstration Pre-processing）
- 提取信息：
  - 抓取时刻 $t_{\text{grasp}}$：通过末端执行器状态判定；
  - 技能段 $\tau_s$：由 VLM 推理或人工标注；
  - 关键点：可供性点 $x_{\text{aff}}$（夹爪与物体的接触点）与功能点 $x_{\text{fun}}$（工具与目标物体的接触点）。
- 点云处理：
  - 用 SAM2 对 RGB 图像进行语义分割（机器人、物体、目标、其他），再映射到点云；
  - 使用 Farthest Point Sampling（FPS）下采样得到工作空间点云 $O_e \subset \mathbb{R}^3$。

### 2.3 基于 3D 网格的语义对应（核心创新点）
- **关键问题**：现有 2D 语义对应难以直接用于需要精确 3D 标注的机器人操作。
- **解决方案**：
  1. 使用 6D 位姿估计器（Omni6DPose）将所有 3D 网格归一化到统一规范空间（Canonical Space）；
  2. 从 $n$ 个视角并行渲染 RGB-D 图像 $I_i$，位姿为 $P_i$；
  3. 用 DINOv2 提取每张图像的语义特征 $S_i$；
  4. 对源网格关键点 $x$ 邻域的 $m$ 个最近顶点 $v_j$，将其投影到图像坐标 $u_{ij}^{src}$，通过余弦相似度在目标图像中找到对应像素：
  
$$u_{ij}^{tg} = \arg\max_u \text{CosSim}(S_i^{src}[u_{ij}], S_i^{tg}[u])$$
$$w_{ij} = \text{CosSim}(S_i^{src}[u_{ij}], S_i^{tg}[u_{ij}^{tg}])$$

  5. 将所有匹配像素反投影到 3D 空间得到候选对应点，加权平均得到目标关键点：

$$x' = \frac{\sum_{i,j} w_{ij} v_{ij}^{tg}}{\sum_{i,j} w_{ij}}$$

### 2.4 多样化演示生成
- **关键点约束的轨迹重放**：
  - 假设：同一功能类（Function Class）的物体，其末端执行器相对于可供性点的轨迹相似，且功能点相对于目标物体的轨迹相似；
  - 抓取段 $\tau_g$：通过减去 $x_{\text{aff}}$ 加上 $x'_{\text{aff}}$ 进行局部坐标系平移迁移；
  - 技能段 $\tau_s$：通过功能点相对于末端执行器的变换 $T_{\text{fun}}^{ee}$ 推导功能点轨迹，再以同样方式迁移；
  - 最后通过 $T'$ 变换到世界系，并通过 IK 解算关节角。
- **过渡段运动规划**：用运动规划或球面线性插值（SLERP）连接 $\tau_g'$ 和 $\tau_s'$。
- **点云数字表亲生成（Point Cloud Digital Cousin）**：
  - 不同于 DemoGen 的全局平移旋转，AffordGen 直接渲染机器人和操作物体的点云，并替换源演示中的对应点云，得到混合"真-仿真"数据，缓解 sim-to-real 差距。

---

## 3. 实验设计

### 3.1 数据集与场景
- **仿真平台**：ManiSkill3（GPU 并行化机器人仿真）。
- **任务（共 4 个仿真 + 4 个真机任务，均含抓取与技能阶段）**：
  - 茶壶倒水（Teapot Pouring）
  - 杯子挂置（Mug Hanging）
  - 刀具切割（Knife Cutting）
  - 鞋子整理（Shoe Organizing，长视距、多物体任务）
- **网格数据集**：PAM 数据集或 Hunyuan3D 2.0 生成的 3D 资产；随机划分为 seen（用于生成训练数据）与 unseen（用于评估）。
- **跨类别任务**：杯子倒水（源自茶壶倒水）、手提包挂置（源自杯子挂置）、锯切割（源自刀具切割）。

### 3.2 对比基线
- **DemoGen**：基于 3D 点云的合成演示生成，1 个源演示生成 1000 条轨迹；
- **CPGen**：通过形变和拉伸源网格提升形状泛化能力；
- **FUNCTO**：基于关键点对应的规划式方法（仅真机实验引入）。

### 3.3 评估配置
- **仿真**：每个网格 50 次评估，初始位置和姿态随机；
- **真机**：固定姿态集评估——大多数任务 27 种姿态（9 位 × 3 朝向），鞋子整理任务 10 种姿态（2 位 × 5 朝向）。

---

## 4. 资源与算力

- 论文正文中**未明确披露**所用 GPU 型号、数量及具体训练时长；
- 仅在实验设定中提到 ManiSkill3 作为"GPU 并行化"的仿真平台，并指出采用了"并行渲染"以提高点云生成吞吐量；
- 训练阶段的算力细节（如 DP3 等策略训练的 GPU 时长）未在所提供文本中给出。

---

## 5. 实验数量与充分性

- **同类别泛化网格 × 演示配置**：测试了 5 种 (#Mesh, #Demo per Mesh) 组合：
  - DemoGen: 1×1000
  - CPGen: 1000×1
  - AffordGen: 20×50、50×20、100×10、1000×1
- **跨类别零样本泛化**：3 个仿真 + 3 个真机任务（mug→teapot、handbag→mug、saw→knife）；
- **同类别跨网格性能分布分析**（Figure 7）：选取 5 个评估网格按与源物体的相似度排列，分析性能衰减趋势；
- **评估对象维度**：源物体（Source）+ 5–20 个未见物体（Unseen）；
- **可观察到的消融趋势**：随着生成数据覆盖更多未见物体，"物体级生成能力"先升后降，论文亦将此作为对未来工作的指引；
- **充分性评价**：
  - 优点：覆盖了同类别、跨类别、仿真、真机四种场景，对比了三种主流基线（含规划式与生成式），且做了 (Mesh × Demo) 网格搜索；
  - 局限：未见网格数量有限（5–20 个），未见物体泛化能力的统计置信度可能受限；未见提及方法在不同噪声、动态扰动下的鲁棒性测试。

---

## 6. 主要结论与发现

- **性能提升**：在仿真和真机任务上，AffordGen 相比最强基线分别平均提升 **24.1%** 和 **24.3%**；
- **数据效率**：仅需少量人类演示（仿真中 1 条，真机中 10 条），即可扩展到上千条多样化轨迹，覆盖上百个不同网格；
- **跨类别零样本泛化**：AffordGen 是唯一在跨类别任务中取得有意义非零成功率的方法（CPGen 与 DemoGen 几乎全部失败）；
- **隐性学习关键点关系**：基于 3D 空间对应与大规模生成数据训练后，策略隐式学会了可供性点、功能点与物体形状之间的关系，从而缓解了基于规划方法中的关键点遮挡问题；
- **数据规模权衡**：随着生成时使用的未见物体数量增加，物体级泛化能力呈"先升后降"曲线，提示过度扩展可能引入噪声关键点对应。

---

## 7. 方法与实验设计的亮点

- **范式创新**：将可供性从"在线规划信号"重新定位为"离线数据生成先验"，巧妙避开了规划式方法的精度瓶颈，同时保留了语义泛化能力；
- **3D 规范化空间 + 多视角 DINOv2 对应**：在统一规范空间中进行多视角渲染与特征匹配，比直接做 3D 网格语义对应更稳健，且复用了大规模预训练视觉基础模型；
- **轨迹三段式生成**：将任务分解为抓取、技能、过渡三段，分别用关键点约束迁移和运动规划处理，降低了生成难度；
- **混合真-仿真点云（数字表亲）**：避免完全重建仿真环境，同时缓解 sim-to-real 差距；
- **同时覆盖同类别与跨类别**：在仿真与真机上均验证了零样本跨类别泛化，跨类别实验设计精巧（壶→杯、包→杯挂、锯→刀切）；
- **充分的多基线、多配置对比**：与 DemoGen、CPGen、FUNCTO 三个具有代表性的方法进行多维度比较。

---

## 8. 不足与局限

- **算力与训练细节缺失**：论文未披露 GPU 型号、数量、训练时长等关键复现信息，影响复现性与可对比性；
- **关键点仍需标注**：可供性点与功能点的标注目前依赖 VLM 或人工，自动化程度有待提高，限制了在更大规模任务上的扩展；
- **依赖 3D 网格资产**：方法依赖目标物体的 3D 网格，对网格质量、姿态估计精度较为敏感；真实场景中获取高质量网格成本不低；
- **任务结构假设**：方法基于"抓取 + 技能 + 过渡"的三段式分解，不适用于无明确可供性点（如柔性物体、流体）或长链纯接触任务；
- **泛化性能的非单调性**：未见物体数量增加时，性能先升后降，说明当前关键点对应仍有噪声，对大规模跨实例生成构成挑战；
- **未见物体评估规模有限**：仿真中仅在 5–20 个未见网格上评估，未见物体多样性、统计置信度有提升空间；
- **缺乏对抗性扰动与失败分析**：未见讨论光照变化、动态障碍、传感器噪声等扰动下的鲁棒性，闭环策略的失败模式分析也未深入展开；
- **应用限制**：当前生成策略对操作物体的"功能类"有较强假设，需属于同一功能类（如壶和杯都属于"盛水"），限制了任务多样性的横向扩展。

（完）
