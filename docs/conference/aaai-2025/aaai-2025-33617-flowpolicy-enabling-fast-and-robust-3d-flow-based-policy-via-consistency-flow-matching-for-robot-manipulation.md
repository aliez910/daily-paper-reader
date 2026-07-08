---
title: "FlowPolicy: Enabling Fast and Robust 3D Flow-Based Policy via Consistency Flow Matching for Robot Manipulation"
title_zh: FlowPolicy：通过一致性流匹配实现快速鲁棒的基于3D流的机器人操控策略
authors: "Qinglun Zhang, Zhen Liu, Haoqiang Fan, Guanghui Liu, Bing Zeng, Shuaicheng Liu"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33617/35772"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于视觉的模仿学习通过流匹配实现复杂机器人操控
tldr: 基于扩散和流匹配的策略在视觉模仿学习中被证明有效，但递归式的去噪过程导致推理效率低下，难以同时满足效率与质量。本文提出FlowPolicy框架，将一致性流匹配与3D视觉相结合，通过归一化速度场的自一致性来改进流动态，实现快速且鲁棒的动作策略生成。3D流策略在复杂操控任务上显著降低推理延迟，同时保持或提升任务成功率。该工作为基于视觉的模仿学习在实时机器人控制中的部署提供了一条高效路径，推动模仿学习向复杂、长时序操控任务落地。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 750, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1811, \"height\": 1024, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 932, \"height\": 446, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 885, \"height\": 444, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 802, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33617/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 875, \"height\": 798, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33617/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1830, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33617/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1834, \"height\": 330, \"label\": \"Table\"}]"
motivation: 现有基于扩散/流匹配的模仿学习策略推理效率低，难以满足机器人实时操控需求。
method: 提出FlowPolicy框架，结合一致性流匹配与3D视觉，通过归一化速度场自一致性来生成快速鲁棒的操控策略。
result: 在机器人操控基准上实现了更优的效率与质量权衡，降低推理延迟并保持任务成功率。
conclusion: 一致性流匹配是提升视觉模仿学习策略推理效率的有效途径，适用于复杂机器人操控任务。
---

## Abstract
Robots can acquire complex manipulation skills by learning policies from expert demonstrations, which is often known as vision-based imitation learning. Generating policies based on diffusion and flow matching models has been shown to be effective, particularly in robotic manipulation tasks. However, recursion-based approaches are inference inefficient in working from noise distributions to policy distributions, posing a challenging trade-off between efficiency and quality. This motivates us to propose FlowPolicy, a novel framework for fast policy generation based on consistency flow matching and 3D vision. Our approach refines the flow dynamics by normalizing the self-consistency of the velocity field, enabling the model to derive task execution policies in a single inference step. Specifically, FlowPolicy conditions on the observed 3D point cloud, where consistency flow matching directly defines straight-line flows from different time states to the same action space, while simultaneously constraining their velocity values, that is, we approximate the trajectories from noise to robot actions by normalizing the self-consistency of the velocity field within the action space, thus improving the inference efficiency. We validate the effectiveness of FlowPolicy in Adroit and Metaworld, demonstrating a 7× increase in inference speed while maintaining competitive average success rates compared to state-of-the-art methods.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "FlowPolicy: Enabling Fast and Robust 3D Flow-Based Policy via Consistency Flow Matching for Robot Manipulation" organized into 8 specific sections. Let me carefully analyze the paper and produce a comprehensive summary.

Let me go through the paper systematically:

1. Core problem: The paper addresses the inefficiency of diffusion/flow-matching-based imitation learning policies. While diffusion-based and flow-matching-based methods (like DP, DP3) are effective for robotic manipulation, they require many iterative sampling steps at inference time, making them unsuitable for real-time robotic control. The trade-off between inference efficiency and policy quality is the main challenge.

2. Method: FlowPolicy - uses Consistency Flow Matching (Consistency-FM) with 3D point cloud conditioning. Key technical details:
   - 3D visual representation: single-view depth images → point clouds via camera intrinsics/extrinsics → FPS downsampling → lightweight MLP encoder for compact 3D representation
   - The flow model is conditioned on state s and visual representation v
   - Two-segment Consistency-FM is used for training
   - One-step inference enabled
   - The key equation: LFlowPolicy with consistency loss and velocity consistency loss
   - Multi-segment training to balance quality and efficiency

3. Experiments:
   - Benchmarks: Adroit (3 dexterous manipulation tasks: Hammer, Door, Pen) and Metaworld (34 tasks across Easy/Medium/Hard/Very Hard)
   - Total: 37 tasks
   - Baselines: DP (2D), DP3 (3D), Simple DP3, Adaflow, Consistency Policy (CP)
   - Metrics: Success rate, inference time, NFE
   - Evaluated 20 episodes per 200 training epochs, 3 random seeds

4. Resources: 
   - Single NVIDIA RTX 2080Ti GPU
   - PyTorch framework
   - 3000 training epochs
   - Batch size 128
   - AdamW optimizer, lr=1e-4
   - EMA decay 0.95
   - 10 expert demonstrations per task

5. Experimental thoroughness:
   - Runtime comparison (Table 1)
   - Success rate comparison (Table 2)
   - Qualitative comparison (Figure 3)
   - Learning curves (Figure 4)
   - Ablation on number of expert demonstrations (Figure 5)
   - Fair comparison with 3 random seeds, multiple baselines

6. Conclusions: FlowPolicy achieves 7x faster inference (19.9ms vs 145.7ms for DP3) while maintaining competitive success rates (70.0% average vs 68.7% for DP3). 1.3% higher than DP3, 2.6% higher than Simple DP3.

7. Advantages:
   - First 3D flow-based policy with one-step inference
   - Real-time inference (19.9ms)
   - Better learning stability
   - Breaks through performance bottlenecks
   - No need for distillation (unlike consistency models)

8. Limitations:
   - Only tested in simulation
   - No real-world robot experiments
   - Limited to single-view point clouds
   - Comparison may not include latest 3D methods
   - Computational resources are modest (single 2080Ti)
   - The 7x speedup is somewhat expected given one-step vs 10-step, but quality comparison is more meaningful

Let me now write this in Chinese with proper Markdown formatting.
</think>
# FlowPolicy 论文详细总结

## 1. 核心问题与研究动机

**核心问题**：如何在视觉模仿学习中兼顾**推理效率**与**策略质量**的平衡。

- 基于扩散（Diffusion Policy, DP）与流匹配（Flow Matching）的策略在机器人操控中已被证明有效，但这类方法在推理时需要**多次递归采样**（如 DP3 需要 10 步 NFE），导致推理延迟较高，无法满足实时机器人控制需求。
- 现有加速方案（如 DDIM、Consistency Model）通常需借助**蒸馏**或牺牲生成质量，实用性受限。
- **流匹配（FM）**虽比扩散更稳定高效，但直接应用于复杂 3D 视觉条件下的机器人动作生成的研究仍处于空白。
- 论文首次将 **Consistency Flow Matching（Consistency-FM）** 与 **3D 点云表征**结合，提出可在**单步推理**下生成高质量动作的策略框架。

---

## 2. 方法论

### 2.1 整体框架
- **骨干网络**：基于 3D Diffusion Policy（DP3）架构，将其中的扩散过程替换为一致性流匹配。
- **3D 视觉条件表征**：
  - 通过单视角深度图与相机内外参生成点云
  - 使用最远点采样（FPS）下采样（Adroit: 512 点，Metaworld: 1024 点）
  - 轻量级 MLP 编码为 64 维紧凑 3D 表征
  - 与机器人状态嵌入共同作为条件输入
- **观测时序**：使用最近 2 帧点云作为条件。

### 2.2 关键技术：一致性流匹配（Consistency-FM）
- **核心思想**：直接定义从任意时刻 t 到同一终点（动作空间）的**直线流**，并约束速度值的一致性，从而实现单步生成。
- **速度一致性**：要求沿同一直线流的任意点上的速度向量保持一致：
  $$L(\theta) = E_{t \sim \mu} E_{x_t, x_{t+\Delta t}} \| f_\theta(t, x_t) - f_{\theta^-}(t+\Delta t, x_{t+\Delta t}) \|_2^2 + \alpha \| \nu_\theta(t, x_t) - \nu_{\theta^-}(t+\Delta t, x_{t+\Delta t}) \|_2^2$$
- **多段训练（Multi-segment Training）**：将时间区间划分为 K 段（如 K=2），每段内分别归一化一致速度场，构造分段线性轨迹，放宽速度一致性约束，提高分布表达灵活性。
- **目标函数（条件化后）**：在 (s, v) 条件下学习两段一致性流场，将噪声轨迹一步变换为目标动作轨迹。

### 2.3 训练与推理流程
- **训练**：最小化 Consistency-FM 损失（含数据一致性项 + 速度一致性项），更新参数 θ，目标参数 θ⁻ 使用 EMA 更新。
- **推理**：直接从高斯噪声 a₀ 通过流模型一步预测目标动作 a₁，无需迭代采样。

---

## 3. 实验设计

### 3.1 数据集与基准
| 基准 | 任务数 | 类型 |
|------|--------|------|
| **Adroit** | 3（Hammer, Door, Pen） | 高自由度灵巧手操控 |
| **Metaworld** | 34（Easy:21, Medium:4, Hard:4, Very Hard:5） | 双指机器人臂操控 |
| **合计** | **37 个任务** | 仿真环境 |

- 每个任务使用 **10 条专家演示**（由训练好的启发式策略生成）。

### 3.2 对比方法
- **3D 基线**：DP3、Simple DP3（轻量版 DP3）
- **2D 基线**：DP（Diffusion Policy）、Adaflow、Consistency Policy（CP）

### 3.3 评估指标
- **成功率（Success Rate）**：20 个回合每 200 训练周期评估一次，取 5 个最高成功率均值
- **推理时间（Inference time, ms）**
- **NFE（Number of Function Evaluations）**
- **3 个随机种子**，报告均值与标准差

---

## 4. 资源与算力

- **硬件**：单块 **NVIDIA RTX 2080Ti GPU**
- **框架**：PyTorch
- **训练配置**：
  - 优化器：AdamW，学习率 1e-4
  - Batch size：128
  - 训练周期：3000 epochs（多数任务 500–1000 epochs 收敛）
  - EMA 衰减率：0.95
  - 动作/状态归一化到 [-1, 1]
- **论文未明确报告训练总时长**，仅以 epoch 数表示。

---

## 5. 实验数量与充分性

### 5.1 实验维度
1. **推理时间对比**（Table 1）：在 37 个任务上测量 NFE 与推理时间
2. **成功率对比**（Table 2）：在 37 个任务上对比多种基线
3. **定性可视化**（Figure 3）：Adroit Pen 与 Metaworld Pick-Place 两组任务
4. **学习曲线**（Figure 4）：4 个代表性任务
5. **专家演示数量消融**（Figure 5）：4 个任务，演示数 1/10/20/50

### 5.2 充分性评价
- **优点**：
  - 实验覆盖 37 个仿真任务，涵盖难度梯度，较为全面
  - 多基线（2D + 3D）对比，公平性较好
  - 3 个随机种子，统计严谨
  - 包含定性、定量、消融三个层次
- **局限**：
  - **仅限仿真**，未涉及真实机器人实验
  - **未做关键消融**：如 Consistency-FM 段数 K、点云数量、3D 表征的消融
  - 训练与基线方法的超参数选择细节披露不充分
  - 仅在单块 2080Ti 上评估，未讨论硬件可扩展性

---

## 6. 主要结论与发现

- **推理速度**：FlowPolicy 平均推理时间 **19.9 ms**，比 DP3（145.7 ms）**快 7×**，比 Simple DP3（63.0 ms）**快 3×**。
- **成功率**：在 37 个任务上平均成功率 **70.0%**，比 DP3（68.7%）高 1.3%，比 Simple DP3（67.4%）高 2.6%。
- **学习稳定性**：FlowPolicy 学习曲线更平滑，训练过程稳定，避免了 DP3 的成功率波动。
- **数据效率**：在演示数据量有限时（1 条）也能达到较高成功率；演示数增加时能突破 DP3 的性能瓶颈。
- **首次验证**：在 3D 视觉条件下的 Consistency-FM 条件生成可行性。

---

## 7. 优点与亮点

- **首创性**：首次将 Consistency-FM 与 3D 点云条件结合用于机器人操控策略生成。
- **效率-质量平衡**：通过速度一致性约束与多段训练，实现真正的**单步推理**。
- **无需蒸馏**：区别于 Consistency Model 需依赖教师模型蒸馏，FlowPolicy 可直接训练。
- **确定性采样**：因 ODE 路径固定，推理时间方差更小，实时性更稳定。
- **架构简洁**：直接复用 DP3 编码器，仅替换生成模块，工程改造成本低。
- **跨任务泛化**：在 37 个不同难度任务上均能保持竞争力，表明条件流匹配学习到的动作分布质量高。

---

## 8. 不足与局限

- **无真实机器人验证**：所有实验均在仿真环境（Adroit、Metaworld）中完成，对 sim-to-real 的迁移性未作评估。
- **算力受限**：仅在单块 2080Ti 上评估，未测试在更高算力或分布式环境下的可扩展性。
- **观测模态单一**：仅使用单视角点云，未探索多视角融合或与 2D 图像的混合表征。
- **消融实验不充分**：缺少对 Consistency-FM 段数 K、点云分辨率、损失权重 α、编码器架构等关键组件的消融研究。
- **演示数据来源单一**：依赖启发式策略生成的演示，未考虑人类演示的噪声、异质性等情况。
- **对比范围有限**：未与最新 3D 操控方法（如 RISE、DP3 的改进版本）以及其他 Flow Matching 操控方法做充分对比。
- **评估指标局限**：未评估轨迹平滑度、动作多样性、鲁棒性等维度，仅以成功率与推理时间为主。
- **代码与可复现性**：未明确说明是否提供全部训练超参数与数据预处理细节，限制了复现便利性。

（完）
