---
title: Affordance-Guided Coarse-to-Fine Exploration for Base Placement in Open-Vocabulary Mobile Manipulation
title_zh: 可供性引导的从粗到细探索用于开放词汇移动操纵中的基座放置
authors: "Tzu-Jung Lin, Jia-Fong Yeh, Hung-Ting Su, Chung-Yi Lin, Yi-Ting Chen, Winston H. Hsu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38909/42871"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于可供性的基座放置用于开放词汇移动操纵
tldr: 开放词汇移动操纵中，基座选择对任务成功至关重要。现有方法仅导航到物体附近而不考虑可供性，导致操纵失败。本文提出可供性引导的从粗到细探索框架，结合视觉语言模型的语义理解与几何可行性，通过迭代优化选择最优基座位置。在基准上，该方法显著提高了操纵成功率，特别是在需要精细操作的任务中。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38909/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1805, \"height\": 509, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38909/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1665, \"height\": 845, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38909/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 841, \"height\": 784, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38909/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 881, \"height\": 388, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38909/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1802, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38909/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1741, \"height\": 302, \"label\": \"Table\"}]"
motivation: 现有移动操纵方法在基座选择时不考虑可供性，导致操纵成功率低。
method: 提出零样本可供性引导的从粗到细探索框架，通过构建可供性RGB和障碍物地图融合语义与空间信息，迭代优化基座位置。
result: 在多项移动操纵任务上显著提升成功率，尤其需要精确基座定位的场景。
conclusion: 融入可供性推理能够提升开放词汇移动操纵的鲁棒性，是实际应用中的关键因素。
---

## Abstract
In open-vocabulary mobile manipulation (OVMM), task success often hinges on the selection of an appropriate base placement for the robot. Existing approaches typically navigate to proximity-based regions without considering affordances, resulting in frequent manipulation failures. We propose Affordance-Guided Coarse-to-Fine Exploration, a zero-shot framework for base placement that integrates semantic understanding from vision-language models (VLMs) with geometric feasibility through an iterative optimization process. Our method constructs cross-modal representations, namely Affordance RGB and Obstacle Map+, to align semantics with spatial context. This enables reasoning that extends beyond the egocentric limitations of RGB perception. To ensure interaction is guided by task-relevant affordances, we leverage coarse semantic priors from VLMs to guide the search toward task-relevant regions and refine placements with geometric constraints, thereby reducing the risk of convergence to local optima. Evaluated on five diverse open-vocabulary mobile manipulation tasks, our system achieves an 85% success rate, significantly outperforming classical geometric planners and VLM-based methods. This demonstrates the promise of affordance-aware and multimodal reasoning for generalizable, instruction-conditioned planning in OVMM.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **开放词汇移动操纵（OVMM）** 中，机器人基座放置的位置对任务成功至关重要。现有方法通常仅将机器人导航到目标物体附近，依赖几何路径规划（如 A*、RRT*），**缺乏对任务相关可供性（affordance）的语义理解**，导致频繁的操作失败（例如：未面向抽屉导致无法打开柜子、未对齐锅把手导致无法抓取）。
- 核心挑战包括：**(1)** 基座放置需同时满足几何可行性（无碰撞、适当距离）与语义意图（朝向操作面）；**(2)** 机器人视野有限，单张 RGB 图像可能遗漏合适放置区域（如柜子前方区域被遮挡）。
- 论文旨在解决**在有限感知下联合推理语义与几何约束**的基座选择问题。

## 2. 论文提出的方法论
### 核心思想
- 提出**零样本框架——可供性引导的从粗到细探索（Affordance-Guided Coarse-to-Fine Exploration）**，融合视觉语言模型（VLM）的语义理解与几何可行性，通过迭代优化选择最优基座位置。
- 关键创新：**(1)** 跨模态表示（Affordance RGB 和 Obstacle Map+）将语义线索与空间地图对齐，克服单视图 RGB 的视野局限；**(2)** 从粗到细优化策略，先使用 VLM 的粗语义先验引导搜索到任务相关区域，再逐步强调几何约束确保物理可行性。

### 技术细节
- **阶段一：可供性引导投影（Affordance Guidance Projection）**
  - 从 RGB 图像中用 Grounded SAM 分割目标物体，用 GPT-4o 选择粗可供性方向。
  - 构建两种表示：
    - **Affordance RGB（Iaff）**：RGB 图像上叠加 12 个等间距（30°）方向箭头，并标注 VLM 选择的粗方向“A”。
    - **Obstacle Map+（M⁺_local）**：障碍物地图上叠加目标物体轮廓、机器人当前位置、以方向“A”为中心的 ±60° 扇形区域，以及颜色与 Iaff 一致的 12 个箭头。

- **阶段二：可供性驱动的从粗到细优化（Affordance-Driven Coarse-to-Fine Optimization）**
  1. **可供性关键点选择**：利用 DINOv2 提取特征，Grounded SAM 分割目标，k-means 聚类产生候选点，GPT-4o 选择最符合任务语义的关键点 g。
  2. **迭代优化（T 步）**：
     - **采样**：从以 g 为中心的截断高斯分布采样 N 个候选基座位置 {xi}，限制在碰撞自由区域。
     - **评分**：每个候选得分 w(x) = w_geo(x)^αt · w_sem(x)^(1-αt)  
       - w_geo：基于到 g 的距离符合高斯分布的累积概率（偏好距离 r*）。  
       - w_sem：基于到动态语义中心 μt 的距离（σs 逐渐减小）。  
       - αt 随时间从语义偏向几何（sigmoid 调度：αt = α_max / (1 + e^{-γ(t-T/2)})）。
     - **重采样与 VLM 排名**：根据归一化权重采样 N_sample 个候选，投影到 M⁺_local，与 Iaff 和指令一起送入 VLM，返回前 k 个语义相关点，更新 μt 为 k 个点的平均。
     - **最终输出**：最后一轮取 VLM 排名前 5，剔除离群最远 2 个后取剩余 3 个的平均作为最终基座位置。

## 3. 实验设计
- **仿真环境**：NVIDIA Isaac Sim，使用 TIAGo++ 移动操纵平台（左臂 7-DOF，差分驱动基座），头戴 RGB-D 相机（1280×720）。
- **任务与场景**：5 个开放词汇移动操纵任务（代表家庭常见场景）：
  1. 扔罐子到垃圾桶（Throw the Can into Trash）
  2. 移动锅靠近红杯子（Move Pot Near Red Mug）
  3. 把杯子放到架子上（Put Mug on Shelf）
  4. 打开柜子（Open Cabinet）
  5. 打开洗碗机（Open Dishwasher）
- **评估方式**：每个任务执行 20 次（随机物体位置、朝向、机器人起始位姿），记录任务成功率（IK 可解、无碰撞、成功执行操作原语并验证物理效果）。
- **对比方法（Baselines）**：
  - Object Center + A*/RRT*：经典几何规划器，导航至目标中心固定距离处。
  - Affordance Point + A*/RRT*：VLM 选择可供性关键点 g，然后几何规划器导航至 g 固定距离。
  - Pivot(I)：基于 VLM 迭代更新动作，仅使用 RGB 图像（参考 PIVOT 方法）。
  - Pivot(M⁺_local, Iaff)：使用与本文相同的多模态输入（Obstacle Map+ 和 Affordance RGB）的 PIVOT 变种。
- **额外实验**：
  - **α 系数消融**：固定 α=0（仅语义）、0.5（平衡）、1（仅几何）与本文递增 αt 的比较。
  - **投影模块消融**：完整方法、去掉 12 箭头、去掉粗方向箭头“A”、去掉整个投影机制。

## 4. 资源与算力
- **论文未明确说明所使用的 GPU 型号、数量、训练时长等算力信息。** 文中提到系统是零样本的，VLM 推理可能基于 GPT-4o 等商业 API，但具体算力消耗未报告。

## 5. 实验数量与充分性
- **实验数量**：共 5 个任务 × 20 次 = 100 次随机试验，加上 α 消融（4 种配置 × 5 任务 × 20 次 = 400 次）和投影模块消融（4 种配置 × 5 任务 × 20 次 = 400 次），总计约 900 次仿真试验，数量较充分。
- **充分性**：
  - 任务类型多样：包括简单目标（垃圾桶）、需对齐目标（锅、架子）、铰接物体（柜子、洗碗机），覆盖不同空间与方向约束。
  - 所有对比方法在相同条件下公平比较，使用固定随机种子确保可复现。
  - 消融实验系统验证了各组件贡献（α 调度、投影箭头、方向信号）。
  - **局限性**：仅限仿真环境，缺乏真实机器人实验；每个任务场景内物体布局随机但环境复杂度有限。

## 6. 论文的主要结论与发现
- 所提方法在 5 个任务上平均成功率达 **85%**，显著优于：
  - 经典方法（Object Center + A*/RRT*：47%~50%，Affordance Point + A*/RRT*：58%~61%）
  - VLM 方法（Pivot(I)：26%，Pivot(M⁺_local, Iaff)：23%）
- **关键发现**：
  - 几何规划器缺乏任务语义，方向敏感任务（开柜子、开洗碗机）失败率高。
  - VLM 方法直接做决策时缺乏几何可行性考虑，导致距离过远或碰撞。
  - 从粗到细的 α 调度（逐渐从语义转向几何）优于固定权重，避免过早陷入局部最优。
  - 投影模块对性能至关重要：移除后成功率从 85% 降至 48%，说明语义线索必须显式映射到空间地图才能被 VLM 有效利用。

## 7. 优点
- **零样本且无监督**：无需任务特定训练数据，直接利用预训练 VLM（GPT-4o）和视觉基础模型（Grounded SAM、DINOv2），泛化能力强。
- **跨模态融合巧妙**：Affordance RGB 和 Obstacle Map+ 将语义意图与几何布局对齐，克服了单视图 RGB 的视野限制，使 VLM 可进行全局推理。
- **从粗到细优化**：合理利用 VLM 的粗语义先导（初始阶段）和几何约束（后期精度），实现鲁棒且准确的基座选择，避免局部最优。
- **实验设计全面**：涵盖多种任务类型与约束，消融实验验证各组件贡献，对比基线代表当前主流方法，结果区分度清晰。

## 8. 不足与局限
- **几何精度有限**：相较于纯几何方法，VLM 在精细距离估计上可能较弱，导致某些任务（如精确放置）的几何精度不足。
- **仍存在推理错误**：尽管有投影对齐，VLM 在复杂场景中仍可能产生语义误解或不当选择（论文提及“在有些情况下可能产生不正确推理”）。
- **未考虑机械臂轨迹碰撞**：当前优化仅考虑基座本身的无碰撞，未纳入机械臂运动时的碰撞风险评估，在拥挤环境中可能导致执行失败。
- **仅限仿真验证**：未在真实机器人平台上进行实验，真实世界的感知噪声、执行误差等因素未被考虑。
- **计算资源未报告**：未提供 VLM 推理的算力消耗，可能影响在资源受限平台上的可部署性评价。
- **场景局限性**：测试环境为桌面级或简单室内场景，未验证在更复杂动态环境（如移动障碍物、人机交互）中的性能。

（完）
