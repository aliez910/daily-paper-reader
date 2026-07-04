---
title: "OmniManip: Towards General Robotic Manipulation via Object-Centric Interaction Primitives as Spatial Constraints"
title_zh: OmniManip：通过以物体为中心的交互基元实现通用机器人操作
authors: "Pan, Mingjie, Zhang, Jiyao, Wu, Tianshu, Zhao, Yinghao, Gao, Wenlong, Dong, Hao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Pan_OmniManip_Towards_General_Robotic_Manipulation_via_Object-Centric_Interaction_Primitives_as_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用机器人操作的视觉-语言-动作原语
tldr: 通用机器人在非结构化环境中操作仍是难题，现有 VLM 缺乏精细三维空间理解，而对 VLM 进行机器人数据微调构建 VLA 又受数据成本与泛化能力限制。本文提出 OmniManip，以物体为中心的交互基元作为空间约束，在物体规范空间中定义可复用的操作约束，从而将 VLM 的高层推理结果精确转换为底层动作。该方法以低成本方式构建 VLA 模型，在多种通用操作任务上展现了良好的泛化能力。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 718, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1795, \"height\": 1217, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 861, \"height\": 587, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 853, \"height\": 452, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 537, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 847, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 854, \"height\": 492, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 817, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1737, \"height\": 819, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 804, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-pan-omnimanip-towards-general-robotic-manipulation-via-object-centric-interaction-primitives-as-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 835, \"height\": 246, \"label\": \"Table\"}]"
motivation: VLM 缺乏精细三维空间理解，难以直接用于精确操作；VLA 微调成本高且泛化差。
method: 提出以物体为中心的交互基元作为空间约束，将高层推理结果精确映射为底层操作动作。
result: 在多种非结构化通用操作任务上提升了泛化性能，并降低了对大规模机器人数据的依赖。
conclusion: 以物体为中心的基元表征可有效弥合高层语义推理与底层精确操作之间的鸿沟。
---

## Abstract
The development of general robotic systems capable of manipulating in unstructured environments is a significant challenge. While Vision-Language Models(VLM) excel in high-level commonsense reasoning, they lack the fine-grained 3D spatial understanding required for precise manipulation tasks. Fine-tuning VLM on robotic datasets to create Vision-Language-Action Models(VLA) is a potential solution, but it is hindered by high data collection costs and generalization issues. To address these challenges, we propose a novel object-centric representation that bridges the gap between VLM's high-level reasoning and the low-level precision required for manipulation. Our key insight is that an object's canonical space, defined by its functional affordances, provides a structured and semantically meaningful way to describe interaction primitives, such as points and directions. These primitives act as a bridge, translating VLM's commonsense reasoning into actionable 3D spatial constraints. In this context, we introduce a dual closed-loop, open-vocabulary robotic manipulation system: one loop for high-level planning through primitive resampling, interaction rendering and VLM checking, and another for low-level execution via 6D pose tracking. This design ensures robust, real-time control without requiring VLM fine-tuning. Extensive experiments demonstrate strong zero-shot generalization across diverse robotic manipulation tasks, highlighting the potential of this approach for automating large-scale data generation.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the OmniManip paper following a specific 8-point structure. Let me analyze the paper carefully and organize the information.

The paper is about OmniManip, a CVPR 2025 paper proposing object-centric interaction primitives as spatial constraints for general robotic manipulation. Let me structure the summary based on the 8 requested points.

Key information from the paper:
1. Core problem: VLM lacks 3D spatial understanding for precise manipulation; VLA fine-tuning is costly and has generalization issues
2. Method: Object-centric canonical interaction primitives (points + directions) in canonical space, dual closed-loop (planning with RRC + execution with 6D pose tracking)
3. Experiments: 12 real-world tasks on Franka Panda arm, compared with VoxPoser, CoPa, ReKep
4. Resources: Not explicitly mentioned GPU types
5. Experimental thoroughness: Multiple ablations, viewpoint tests, stability tests
6. Conclusions: Strong zero-shot generalization, dual closed-loop provides robustness
7. Strengths: Novel object-centric representation, dual closed-loop, no VLM fine-tuning needed
8. Limitations: Cannot handle deformable objects, depends on 3D AIGC mesh quality, multiple VLM calls computational challenges

Let me write this up in a structured Markdown format.
</think>
# OmniManip 论文总结

## 1. 核心问题与研究动机

- **研究背景**：通用机器人在非结构化环境中的操作是长期难题。VLM（如 GPT-4o）在高层语义推理上表现优异，但缺乏精确 3D 空间感知能力，难以直接驱动低层精细操作。
- **现有方案局限**：
  - **VLA（Vision-Language-Action）路线**：在机器人数据上微调 VLM 输出轨迹，但数据采集成本高，且易产生机器人特定的表征，泛化能力受限。
  - **交互基元路线**（如 VoxPoser、CoPa、ReKep）：将动作抽象为关键点/向量，但生成原语的提议过程是 task-agnostic 的，缺乏任务适配性，且 2D 图像或 1D 文本对 3D 原语的压缩存在信息损失，叠加 VLM 幻觉问题，稳定性不足。
- **核心问题**：如何构建一种既能被 VLM 高层推理调用、又能保留精细 3D 几何信息的中间表征，桥接高层语义与低层精确操作？

## 2. 方法论

### 2.1 核心思想
- 关键洞察：以**物体功能可供性（functional affordance）**定义的**规范空间（canonical space）**作为操作表征的承载空间，天然具有结构化、语义一致的特性。
- 提出**以物体为中心的交互基元（Object-Centric Interaction Primitives）**：每个基元由交互点 $p \in \mathbb{R}^3$ 与交互方向 $v \in \mathbb{R}^3$ 构成，记为 $O = \{p, v\}$。
- 在 active / passive 物体之间构建**空间约束（spatial constraints）**，包含：
  - 距离约束：$D(O_a, O_p) = \|p_a - p_p\|_2 = d_i$
  - 角度约束：$\Theta(O_a, O_p) = \arccos\left(\frac{v_a \cdot v_p}{\|v_a\|_2 \|v_p\|_2}\right) = \theta_i$，$\theta_i \in \{0, \pi\}$

### 2.2 关键技术细节
- **任务分解**：用 SAM + GroundingDINO 标记前景物体，VLM 过滤任务相关对象并将任务分解为多个 stage $S_i = \{A_i, O_i^{active}, O_i^{passive}\}$，定义 6 种原子动作。
- **3D 资产准备**：单视图 3D 生成网络（如 One-2-3-45++ / TripoSR）得到物体 mesh，Omni6DPose 进行 6D 姿态估计以实现规范空间对齐。
- **交互点定位**：使用 SCAFFOLD 的网格视觉提示，分 "Visible/Tangible" 和 "Invisible/Intangible" 两类；不可见点通过多视图推理与规范空间推断，任务级抓取点用多原语热力图提升稳定性。
- **交互方向采样**：在规范空间以**主轴方向**作为初始候选，用 VLM 给出语义描述，LLM 评分排序，得到任务相关的有序候选方向。
- **约束提取与优化**：将约束转化为末端执行器位姿的优化问题：
  $$P_{ee}^* = \arg\min_{P_{ee}} \sum_{j=1}^{N} L_j(P_{ee}), \quad L = \{L_C, L_{collision}, L_{path}\}$$
  - $L_C$：约束保持损失；$L_{collision}$：碰撞避免损失；$L_{path}$：平滑轨迹损失（平移 + 旋转）。

### 2.3 双闭环系统
- **闭环规划（Self-correction via RRC）**：
  - 算法 1：Resampling–Rendering–Checking，依次渲染交互图像让 VLM 判断 success / failure / refine。
  - 失败则进入 refine 阶段，沿预测方向 $v_i$ 周围均匀采样 6 个细化方向重新评估。
- **闭环执行**：使用现成的 6D 姿态跟踪器（基于 Omni6DPose）实时更新 active / passive 物体位姿，重新优化末端执行器目标位姿，应对抓取偏差、目标位移等动态扰动。

## 3. 实验设计

- **硬件平台**：Franka Emika Panda 机械臂 + UMI 替换指；两台 Intel RealSense D415（腕部第一人称 + 第三方全局视角）。
- **任务 benchmark**：12 个真实世界操作任务（10 次/任务，每次重置布局）：
  - **刚体操作（6 个）**：pour tea、insert flower into vase、insert pen into holder、recycle battery、pick up cup on dish、fit lid onto teapot。
  - **关节物操作（6 个）**：open/close drawer、hammer button、press red button、close laptop lid、open jar。
- **基线方法**：
  - **VoxPoser**：LLM+VLM 合成 3D value maps，零样本 + 闭环控制。
  - **CoPa**：以部件级空间约束+VLM 的开放词汇操作。
  - **ReKep**：关系关键点约束 + 层级优化的实时方法。
- **实现细节**：GPT-4o 作为 VLM；AnyGrasp / GraspNet 用于 6-DOF 抓取；GenPose++ 用于通用 6D 姿态估计；约束优化使用基于采样的近似求解（如 cuRobo）。

## 4. 资源与算力

- 论文**未明确披露**训练所用 GPU 型号、数量、训练时长等算力细节。
- 推理阶段依赖多次 GPT-4o API 调用、6D 姿态估计、姿态跟踪等实时模块，强调"实时性"（real-time）但未给出具体延迟数字。
- VLM 微调：本方法**刻意避免** VLM 微调，因此无大规模 GPU 训练开销。

## 5. 实验数量与充分性

- **主表（Table 1）**：12 个任务 × 4 个方法（VoxPoser / CoPa / ReKep / OmniManip），含关闭闭环规划的 OmniManip (Open-loop) 消融。刚体 / 关节物分组统计。
- **稳定性分析（Figure 5 + 文字）**：以"pour tea"为案例可视化 ReKep/CoPa/OmniManip 的关键点提议与执行对比。
- **视角一致性（Table 2 + Figure 6）**：在 0°/25°/45°/75°/90° 五个视角下对比"recycle battery"的成功率。
- **采样效率（Table 3）**：对比 OmniManip 主轴采样 vs. SO(3) 均匀采样的迭代次数与成功率（recycle battery、pour tea）。
- **闭环规划消融**：Table 1 中 Open-loop 列直接给出量化结果（约 15% 性能下降）。
- **闭环执行消融**：Figure 8 定性展示无闭环执行时的两类典型失败（抓取偏移、目标动态位移），并以文字说明 ReKep 的关键点跟踪在遮挡下 47% 失败率。
- **充分性评价**：
  - 优点：覆盖刚体/关节物/视角变化/采样策略/消融/失败模式，维度较全。
  - 局限：仅在 12 个任务上评估，每个任务仅 10 次试验，统计显著性有限；缺少与近期 VLA（如 OpenVLA、RT-2）的对比。

## 6. 主要结论与发现

- OmniManip 在 12 个真实任务上**零样本**整体显著优于 VoxPoser、CoPa、ReKep：刚体 68.3%（vs. 15.0% / 30.0% / 45.0%），关节物 61.7%（vs. 16.7% / 26.7% / –）。
- **规范空间交互基元**带来两个关键收益：
  1. **稳定性**：主轴驱动采样替代 SO(3) 均匀采样，迭代更少且成功率更高（recycle battery 80% vs. 50%）。
  2. **视角不变性**：0°–90° 视角变化下成功率几乎不变（7–8/10），而 ReKep 从 0° 的 0/10 退化到 90° 的 7/10。
- **双闭环是关键**：闭环规划带来 >15% 的成功率提升；闭环执行显著缓解遮挡与目标位移带来的失败。
- 应用潜力：可作为**自动化专家示范生成**的工具，辅助模仿学习扩展（详见补充材料 A.6）。

## 7. 方法与实验的亮点

- **创新的中间表征**：首次将交互基元定义在以功能可供性构建的规范空间内，融合了关键点的细粒度与 6D 姿态的稳定性。
- **避免 VLM 微调**：纯提示工程 + 闭环机制实现开放词汇操作，规避 VLA 路线的昂贵数据与泛化问题。
- **RRC 自纠错机制**：渲染 + 重采样 + VLM 校验，引入规划阶段的反馈回路，针对性缓解幻觉。
- **基于 6D 姿态跟踪的执行闭环**：相比关键点跟踪对遮挡更鲁棒，可在交互点不可见时继续跟踪。
- **统一的 6 原子动作集** + 任务级多原语热力图：降低 VLM 决策空间，提升抓取鲁棒性。

## 8. 不足与局限

- **形变物体不可处理**：姿态表征无法建模可形变物体，限制了方法适用范围。
- **依赖 3D AIGC 网格质量**：单视图生成网格的精度直接影响规范空间与原语估计，整体质量仍受制于当前 3D 生成模型。
- **多次 VLM 调用带来计算压力**：尽管支持并行，GPT-4o 等模型的 API 延迟与费用仍是系统瓶颈，未给出定量分析。
- **实验规模有限**：仅 12 任务 × 10 次实验，未与最新 VLA 模型（如 OpenVLA、RT-2 等）做对比；缺少公开 benchmark（如 RLBench、SAPIEN）的标准化评估。
- **无明确的失败模式量化**：Figure 8 给予定性失败案例，但闭环执行消融未提供系统性数字。
- **物体假设较理想**：依赖 Omni6DPose 等通用 6D 姿态估计器，对未见过类别或严重遮挡、堆叠场景的鲁棒性未深入讨论。
- **安全与误差累积**：闭环规划 + 执行虽能自纠，但多次 VLM 调用与重采样的累积误差在长任务流中未做分析。

（完）
