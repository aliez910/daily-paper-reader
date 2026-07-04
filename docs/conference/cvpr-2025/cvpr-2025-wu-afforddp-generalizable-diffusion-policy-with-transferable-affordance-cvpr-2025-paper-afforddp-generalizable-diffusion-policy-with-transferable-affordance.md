---
title: "AffordDP: Generalizable Diffusion Policy with Transferable Affordance"
title_zh: AffordDP：基于可迁移可供性的可泛化扩散策略
authors: "Wu, Shijie, Zhu, Yihang, Huang, Yunao, Zhu, Kaizhen, Gu, Jiayuan, Yu, Jingyi, Shi, Ye, Wang, Jingya"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wu_AffordDP_Generalizable_Diffusion_Policy_with_Transferable_Affordance_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向可泛化机器人操纵的扩散策略
tldr: 基于扩散的策略在机器人操纵任务上表现优异，但难以处理分布外场景。AffordDP通过引入可迁移的3D接触可供性建模，使扩散策略能够泛化到完全未见过的物体类别。在多个仿真和真实机器人操纵基准上的实验表明，相较于仅依赖视觉特征的方法，新方法在跨类别泛化能力上取得显著提升。该工作为基于可供性先验的视觉运动策略提供了一种通用范式，对推动可扩展模仿学习具有重要意义。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1794, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1763, \"height\": 886, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1768, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1615, \"height\": 743, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 882, \"height\": 525, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 292, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 200, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wu-afforddp-generalizable-diffusion-policy-with-transferable-affordance-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1538, \"height\": 355, \"label\": \"Table\"}]"
motivation: 现有扩散策略对域外物体泛化能力有限，难以迁移到全新类别。
method: 提出AffordDP，通过3D接触建模将可供性先验融入扩散策略实现跨类别泛化。
result: 在多个仿真和真实机器人操纵基准上显著优于仅依赖视觉特征增强的方法。
conclusion: 可供性先验可有效提升扩散策略对未见过物体类别的操纵泛化能力。
---

## Abstract
Diffusion-based policies have shown impressive performance in robotic manipulation tasks while struggling with out-of-domain distributions. Recent efforts attempted to enhance generalization by improving the visual feature encoding for diffusion policy. However, their generalization is typically limited to the same category with similar appearances. Our key insight is that leveraging affordances--manipulation priors that define "where" and "how" an agent interacts with an object--can substantially enhance generalization to entirely unseen object instances and categories. We introduce the Diffusion Policy with transferable Affordance (AffordDP), designed for generalizable manipulation across novel categories. AffordDP models affordances through 3D contact points and post-contact trajectories, capturing the essential static and dynamic information for complex tasks. The transferable affordance from in-domain data to unseen objects is achieved by estimating a 6D transformation matrix using foundational vision models and point cloud registration techniques. More importantly, we incorporate affordance guidance during diffusion sampling that can refine action sequence generation. This guidance directs the generated action to gradually move towards the desired manipulation for unseen objects while keeping the generated action within the manifold of action space. Experimental results from both simulated and real-world environments demonstrate that AffordDP consistently outperforms previous diffusion-based methods, successfully generalizing to unseen instances and categories where others fail.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "AffordDP: Generalizable Diffusion Policy with Transferable Affordance" following 8 specific points. Let me analyze the paper content carefully and structure my response.

Let me organize the content:

1. Core problem: Diffusion-based policies struggle with out-of-domain generalization, especially to unseen object categories. Previous work focused on visual feature encoding but limited to same category.

2. Method:
- Affordance modeling: 3D contact point (static) + post-contact trajectory (dynamic)
- Affordance memory: Built using Grounded-SAM, CLIP encoder
- Static affordance transfer: SD-DINOv2 features for 2D correspondence, then back-project to 3D
- Dynamic affordance transfer: 6D transformation matrix with separate R and t estimation
  - Translation: difference between source and target 3D contact points
  - Rotation: ICP on part point clouds (using Point-SAM to segment manipulable parts)
- Affordance-guided diffusion policy: conditions C = {Ot, St, Φ}
- Adaptive affordance guidance during sampling: loss based on distance between end-effector and static affordance
- Uses DDIM, with analytical guidance solution

3. Experiments:
- Simulation: IsaacGym, GAPartnet objects, Franka arm
- Tasks: PullDrawer, OpenDoor (simulation); OpenDoor, PullDrawer, Pick&Place (real-world)
- Baselines: DP (Diffusion Policy), DP3 (3D Diffusion Policy)
- Training settings: object-specific vs unified policy training
- Variance levels: Easy, Medium, Hard

4. Resources: No specific GPU info mentioned. Training data: 30 demos (object-specific), 20 per object × 5 objects (unified simulation), 25 demos per object × 4 objects (real-world).

5. Experiment count: Multiple tables, ablation study, instance/category generalization tests.

6. Main conclusions: AffordDP outperforms baselines in cross-category generalization.

7. Strengths: Novel affordance representation, end-to-end framework combining semantics and geometry.

8. Limitations: Foundation models' spatial understanding limitations, challenges in modeling/extracting affordances for some scenarios.

Let me write the structured summary in Chinese.
</think>
# AffordDP 论文总结

## 1. 核心问题与研究动机

- **领域背景**：基于扩散模型的模仿学习（如 Diffusion Policy）在机器人视觉运动策略中表现优异，但其分布外泛化能力差，限制实际部署。
- **现有方法的局限**：
  - 已有工作（如 3D Diffusion Policy / DP3、Equibot、GenDP 等）通过改进视觉特征编码（点云、SIM(3)-等变网络、3D 语义场）来增强泛化，但仅能在**同一类别、相似外观**的物体间迁移。
  - 难以实现对**全新实例甚至全新类别**的零样本泛化。
- **关键洞察**：人类可以轻松将"开门"技能从柜子迁移到微波炉、冰箱，这源于任务级"可供性（affordance）"先验——即"在哪里"和"如何"与物体交互的知识。
- **本文目标**：将可供性引入扩散策略，实现对未见实例和未见类别的可泛化操作。

## 2. 方法论

### 2.1 可供性的统一表示

- 将可供性定义为 **Φ = (c, τ)**：
  - **静态可供性 c ∈ ℝ³**：3D 接触点（"在哪里"）。
  - **动态可供性 τ ∈ ℝ³ˣᴺ**：接触后末端执行器的有序 3D 轨迹点（"如何"交互）。

### 2.2 可供性记忆库构建

- 使用 Grounded-SAM 裁剪目标物体，CLIP 图像编码器提取外观特征 z。
- 记忆库 M = {(T, Φ, z, P)}，包含任务名、可供性、外观特征、点云 P。
- 检索时使用同一任务 T 下的余弦相似度寻找最相似源物体。

### 2.3 静态可供性迁移

- 利用 SD-DINOv2 生成像素级图像特征 Fˢ 和 Fᵀ。
- 通过特征匹配（argmax）找到源接触点 cˢ_2D 在目标图像中的对应点 cᵀ_2D。
- 将 cᵀ_2D 反投影到 3D 世界坐标得 cᵀ_3D。

### 2.4 动态可供性迁移（6D 变换矩阵）

- 平移向量 **t** = 目标接触点 − 源接触点。
- 旋转矩阵 **R**：使用 Point-SAM 以 3D 接触点为提示分割可操作部件点云，然后对部件点云（而非整体）做 ICP 配准，最小化
  - E(T) = Σ_{(p,q)∈K} [(p − Tq) · n_p]²
  - 部件级配准避免整体形状/尺度差异带来的偏差。
- 最终变换：**τᵀ = Rτˢ + t**。

### 2.5 可供性引导的扩散策略

- **条件集合**：C = {Oₜ, Sₜ, Φ}
  - Oₜ：场景点云（裁剪+下采样后用 MLP 编码）。
  - Sₜ：机器人本体感知（MLP 编码）。
  - Φ：可供性（接触点用 MLP，轨迹用 Transformer + [CLS] token 编码）。
- **基础框架**：DDIM 条件扩散，训练损失 L = ‖εᵏ − ε_θ(aₜᵏ, k, fₜ)‖²。
- **自适应可供性引导采样**：
  - 定义损失 L_g = ‖p_ee − c³ᴰ‖²（当末端执行器接近接触点时启用，否则为 0，由阈值 θ 控制）。
  - 采用 DSG 的解析式引导：
    - a_{t}^{k−1*} = μ_θ(aₜᵏ) − √n · δ_k · ∇_{aₜᵏ} L_g / ‖∇_{aₜᵏ} L_g‖₂
  - 引导使生成动作在动作流形内**逐步靠近目标接触点**，兼顾分布合理性与任务精度。

## 3. 实验设计

- **仿真平台**：IsaacGym；物体来自 **GAPartNet**；机械臂为 **Franka** + 侧装相机。
- **任务**：
  - 仿真：PullDrawer、OpenDoor。
  - 真实世界：OpenDoor、PullDrawer、Pick&Place。
- **基线方法**：
  - **DP**（Diffusion Policy，图像输入）。
  - **DP3**（3D Diffusion Policy，点云输入）。
- **训练设置**：
  - **单物体训练**（object-specific）：每个任务 30 条专家示范，按数据方差分 Easy/Medium/Hard 三档。
  - **统一策略训练**（unified）：每任务选 5 个不同物体，每物体 20 条示范。
- **测试对象类型**：已见实例、同类未见实例、**未见类别实例**。
- **真实世界数据**：遥操作采集，每物体 25 条，每任务 4 个物体，共 100 条/任务。
- **评估指标**：成功率；真实实验中每个测试对象进行 3 次试验，至少 1 次成功即记为成功。

## 4. 资源与算力

- 论文**未明确披露**所用 GPU 型号、数量或训练时长。
- 仅在致谢中提到使用了上海科技大学的 **HPC 平台**，未给出具体硬件配置与训练开销。
- 实验数据量：仿真 100–150 条/任务；真实世界 100 条/任务，相比 DP/DP3 通常需要 200+ 示范，**数据效率更高**。

## 5. 实验数量与充分性

- **仿真定量实验**（3 张主表）：
  - 表 2：单物体训练，三档方差难度，两个任务。
  - 表 3：统一策略训练，三种对象类型（已见/同类未见/未见类别），两个任务。
- **真实世界实验**（表 4）：3 个任务 × 3 种对象类型 = 9 个评估维度。
- **实例与类别泛化表格**（表 1）：PullDrawer 任务对 4 个未见物体（Cabi­net 1/2、Dressing Table、Oven）的成功率。
- **消融实验**（表 5）：在 OpenDoor 仿真任务上，分别去掉轨迹、去掉 affordance guidance 三组对比。
- **可视化与失败分析**（图 4）：对比 DP、DP3 与本文方法在真实任务中的执行过程（位置错误、旋转错误、抓取过早闭合等）。
- **充分性评价**：
  - 实验涵盖**仿真+真实**、**单物体+统一策略**、**已见/同类未见/跨类别**三个维度，并配以消融，整体较充分。
  - 基线仅对比了 DP 和 DP3，**未与 Equibot、GenDP、G3Flow 等同期方法直接比较**，公平性略有不足。
  - 真实试验每个对象仅 3 次试验，统计置信度有限。

## 6. 主要结论与发现

- **跨类别泛化显著提升**：在仿真 OpenDoor 未见类别上，AffordDP 成功率 26.7%，而 DP/DP3 仅 3.3%/5.6%。
- **真实世界零样本能力**：跨类别场景中，DP 完全失败，DP3 有限，AffordDP 取得 40%–50% 成功率。
- **数据效率更高**：仅需 100 条真实示范即可工作，远少于 DP/DP3 的 200+ 条。
- **关键组件贡献**：消融显示动态轨迹 + 自适应引导均带来明显提升，特别是后者对**未见类别**改善最显著。
- **失败模式**：DP 缺乏空间感知、DP3 易对特定位置过拟合且动作序列重叠，AffordDP 缓解了这些问题。

## 7. 方法与实验设计的亮点

- **统一的静态+动态可供性表示**：从 2D 接触点升级为 3D 接触点 + 后接触轨迹，能表达复杂操作过程。
- **2D 语义对应 + 3D 几何配准的混合迁移策略**：将 SD-DINOv2 的语义匹配与 Point-SAM + ICP 的几何配准结合，分别估计平移与旋转，提升了跨结构/跨类别迁移的鲁棒性。
- **部件级而非整体配准**：减弱形状/尺度差异的影响，避免传统实例级配准的不可靠问题。
- **解析式的扩散引导公式**：在 DDIM 框架内引入自适应 L_g 引导，理论上保留动作流形结构，实现"既贴任务又保分布"。
- **数据效率优势明显**：仅 100 条真实示范即可获得跨类别泛化能力。

## 8. 不足与局限

- **基线对比有限**：仅与 DP、DP3 对比，未与 Equibot、GenDP、G3Flow、RAM、Robo-ABC 等同期方法直接较量，难以判断相对最优性。
- **真实实验统计量小**：每个对象仅 3 次试验，结论可能受随机性影响。
- **真实世界任务种类有限**：仅 3 个任务（开柜门、拉抽屉、抓取放置），且均依赖相对结构化的可操作部件，对更复杂、长时序、非铰接物体的适用性未验证。
- **依赖基础模型的语义理解**：作者自承基础模型空间理解有限，难以指定"特定部件"的可供性迁移；这在细粒度零件级操作中可能成为瓶颈。
- **可供性提取与建模受限**：在难以建模/提取可供性的场景（如柔性物体、流体、复杂工具使用）下方法不适用。
- **未见类别泛化仍有较大提升空间**：真实世界跨类别成功率仅 40%–50%，距实用化部署尚有距离。
- **未报告训练算力与消融以外的稳健性分析**：缺乏对超参数（θ 阈值、引导权重 γ、训练样本数）的敏感性研究。
- **场景多样性不足**：仿真仅使用 GAPartNet 中的刚性铰接物体，未涵盖杂乱堆叠、遮挡严重等更现实的场景。

（完）
