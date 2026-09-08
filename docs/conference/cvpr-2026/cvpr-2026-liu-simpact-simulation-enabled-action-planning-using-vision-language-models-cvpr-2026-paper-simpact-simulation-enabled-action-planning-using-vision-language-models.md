---
title: "SIMPACT: Simulation-Enabled Action Planning using Vision-Language Models"
title_zh: SIMPACT：基于视觉语言模型的仿真驱动动作规划
authors: "Liu, Haowen, Yao, Shaoxiong, Chen, Haonan, Gao, Jiawei, Mao, Jiayuan, Huang, Jia-Bin, Du, Yilun"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_SIMPACT_Simulation-Enabled_Action_Planning_using_Vision-Language_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 基于VLM的仿真闭环动作规划框架，用于细粒度机器人操作任务
tldr: 针对视觉语言模型缺乏物理动力学知识、难以直接用于细粒度机器人操作任务的问题，本文提出测试时仿真驱动的动作规划框架SIMPACT。该方法通过在闭环仿真中赋予VLM物理推理能力，无需额外训练即可从单帧RGB-D观测生成可执行动作计划。论文推动了VLM在物理接地动作规划中的应用，为机器人操作提供语义与物理兼具的规划能力。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1787, \"height\": 498, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1678, \"height\": 601, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1796, \"height\": 342, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1745, \"height\": 1079, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1805, \"height\": 910, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 599, \"height\": 399, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1796, \"height\": 333, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1602, \"height\": 261, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-simpact-simulation-enabled-action-planning-using-vision-language-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 225, \"label\": \"Table\"}]"
motivation: 现有VLM缺乏对物理动力学的接地理解，难以完成细粒度机器人操作任务。
method: 在测试时将仿真世界模型嵌入VLM决策回路，实现无需训练的物理推理与动作规划。
result: 在仅给定单帧RGB-D观测下生成物理合理的可执行操作计划。
conclusion: 该框架为VLM在物理接地机器人操作中的部署提供了轻量化新路径。
---

## Abstract
Vision-Language Models (VLMs) exhibit remarkable common-sense and semantic reasoning capabilities. However, they lack a grounded understanding of physical dynamics. This limitation arises from training VLMs on static internet-scale visual-language data that contain no causal interactions or action-conditioned changes. Consequently, it remains challenging to leverage VLMs for fine-grained robotic manipulation tasks that require physical understanding, reasoning, and corresponding action planning. To overcome this, we present SIMPACT, a test-time, SIMulation-enabled ACTion Planning framework that equips VLMs with physical reasoning through simulation-in-the-loop world modeling, without requiring any additional training. From a single RGB-D observation, SIMPACT efficiently constructs physics simulations, enabling the VLM to propose informed actions, observe simulated rollouts, and iteratively refine its reasoning. By integrating language reasoning with physics prediction, our simulation-enabled VLM can understand contact dynamics and action outcomes in a physically grounded way. Our method demonstrates state-of-the-art performance on five challenging, real-world rigid-body and deformable manipulation tasks that require fine-grained physical reasoning, outperforming existing general-purpose robotic manipulation models. Our results demonstrate that embedding physics understanding via efficient simulation into VLM reasoning at test time offers a promising path towards generalizable embodied intelligence.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "SIMPACT: Simulation-Enabled Action Planning using Vision-Language Models" organized in specific sections. Let me analyze the paper content and structure the summary accordingly.

Key information from the paper:
1. Core problem: VLMs lack physical dynamics understanding, making them unsuitable for fine-grained robotic manipulation
2. Method: SIMPACT - test-time simulation-enabled action planning framework
3. Experiments: 7 real-world tasks (rigid body and deformable manipulation)
4. Baselines: π0.5, VoxPoser, MOKA
5. Hardware: Franka Research 3 robot, Intel RealSense D435i
6. VLM: Google Gemini 2.5 Pro
7. No specific GPU/training time mentioned
8. Results: 80%, 60%, 40%, 90%, 80%, 80%, 70% success rates across tasks

Let me organize this into the required format.
</think>
# SIMPACT 论文总结

## 1. 核心问题与研究动机

- **核心问题**：视觉语言模型（VLM）虽然在语义理解与常识推理方面表现突出，但缺乏对**物理动力学**的接地（grounded）理解。由于 VLM 是在静态、互联网规模的图文数据上训练的，缺少因果交互与动作条件变化信息，因此难以胜任需要精细物理推理的机器人操作任务（例如推纸箱不倒、堆碗、压扁黏土成方形等）。
- **关键瓶颈**：
  - 纯语言推理无法准确预测接触动力学、力平衡与时序变化。
  - 现有 VLA（Vision-Language-Action）模型依赖大量动作标注数据，泛化能力有限。
  - 已有 3D 几何表征方法（如 VoxPoser、MOKA）仍缺乏**时间动态信息**。
- **研究意义**：提出在**测试时**（test-time）将物理仿真嵌入 VLM 推理回路，为通用机器人操作提供"语义 + 物理"兼具的轻量路径。

---

## 2. 方法论

### 2.1 整体框架
- **输入**：单帧 RGB-D 图像 $I_0$ + 自然语言任务描述 $\ell_{task}$
- **输出**：机器人末端执行器动作序列 $a = \{a_t\}_{1 \le t \le T}$，其中 $a_t \in SE(3) \times \mathbb{R}$（6DoF 末端位姿 + 夹爪开度）

### 2.2 仿真构建（Sec 3.1）
- **状态转移方程**：$s_t = \mathrm{SIM}(s_{t-1}, a_t; \theta)$
  - 状态空间 $s_t$ 包含所有任务相关信息：刚体为 6DoF 位姿，可形变物体为 $N$ 个粒子位置 $\mathbb{R}^{3 \times N}$。
  - 仿真参数 $\theta = (\theta_{geom}, \theta_{phys})$：几何参数（形状/位姿）与物理参数（质量、摩擦、质心、弹性等）。
- **几何与物理参数自动化**：
  - 用 VLM 根据用户指令生成物体标签；
  - **GroundedSAM2** 分割目标物体；
  - 刚体：用 **Hunyuan3D 2.1**（image-to-3D 模型）重建三角网格，并通过 RGB-D 点云估计尺度与位姿（**FoundationPose**）；
  - 可形变物体：将分割后的深度图反投影得到 3D 表面点，并在物体表面与桌面之间体积内**均匀采样粒子**；
  - 物理引擎自动选择：刚体用 **MuJoCo**；硬可形变用 **Projective Dynamics** 变体（PyTorch 实现）；软可形变用 **MPM（Material Point Method，Warp 实现）**。
  - 物理参数（质量、摩擦、弹性等）由 VLM 借助常识推理推断。

### 2.3 基于 VLM 的动作规划（Sec 3.2）
- **算法 1 流程**：
  1. **初始化采样**：VLM 生成 $K$ 条候选高层动作序列 $\{a_i\}$，并各自在仿真中 rollout 得到 $\{s_i\}$；
  2. **迭代优化**：VLM optimizer 基于所有失败/成功的（动作，状态）上下文推理新动作 $a_k$；
  3. **成功评估**：VLM 根据仿真最终状态判断任务是否完成；否则继续优化，直至达到 $K_{max}=13$（3 次优化迭代）。
- **关键模块**：
  - **VLM Sampler（SAMPLE）**：采用**分层动作生成**——高层用符号动作（`MOVE`, `GRASP`, `RELEASE` 等），低层用 `ACTION2POSE` 映射到连续 6DoF 轨迹，便于 VLM 在预训练先验上推理。
  - **VLM Optimizer（OPTIMIZE）**：通过**上下文学习**（in-context learning）从所有采样失败/成功案例中推理，输出非局部动作更新。
  - **VLM Evaluator（TASKSUCCESS）**：根据最终仿真图像与状态判断成功。
- **VLM 选择**：Google Gemini 2.5 Pro。
- **核心创新点**：
  1. 零样本、无需任务训练；
  2. 仿真作为 VLM 推理的"上下文反馈"机制；
  3. VLM 同时承担**采样器、优化器、评估器**三重角色。

---

## 3. 实验设计

### 3.1 任务设置（共 7 个真实世界细粒度操作任务）
| 任务 | 物体类型 | 核心物理挑战 |
|---|---|---|
| Non-toppling push | 刚体（纸箱、瓶子） | 推力位置与距离，避免倾倒 |
| Bowl stacking | 刚体（碗） | 抓取边缘、稳定堆叠 |
| Pivoting | 刚体（Pocky 盒） | 维持侧面接触使物体竖立 |
| Shape rope | 可形变（绳） | 形变结果满足开合比 |
| Shape dough | 可形变（黏土） | 双向垂直按压成方形 |
| Avoid obstacle | 刚体 | 路径规划绕障 |
| Sweeping | 刚体（咖啡豆） | 多次扫动集合 |

每个任务做 **10 次试验**，以成功率作为评价指标。

### 3.2 硬件
- **机器人**：Franka Research 3 + 平行爪夹爪（黏土任务用 3D 打印大接触面积末端执行器）
- **传感器**：单个标定的 Intel RealSense D435i RGB-D 相机

### 3.3 对比方法
- **π0.5**：大规模机器人动作数据训练的 VLA 模型
- **VoxPoser**：使用体积价值图的 VLM 规划方法
- **MOKA**：基于关键点与可供性标记的 VLM 规划方法（对原文不支持的推/压任务做了扩展）

---

## 4. 资源与算力

- 论文**未明确报告**训练算力（因本方法为零训练、测试时方法）。
- 仿真实现细节：
  - Projective Dynamics 变体：基于 **PyTorch**；
  - MPM 求解器：基于 **NVIDIA Warp**；
  - 图像到 3D：Hunyuan3D 2.1；分割：GroundedSAM2；位姿估计：FoundationPose。
- 试验规模：每个任务 10 次试验，总计约 70 次真实世界试验。
- 文中**未披露**所使用的 GPU 型号与数量，也未给出单次规划的计算耗时。

---

## 5. 实验数量与充分性

- **实验维度**：
  - 7 个任务覆盖刚体 + 可形变、推/抓/扫/按压等多种操作模式；
  - 主结果表（表 2）：与 3 个基线对比；
  - 消融实验（表 3）：移除 VLM 采样器 / 移除仿真 rollout / 移除 VLM 优化器；
  - 采样数量消融（表 4）：$K=3,10,20$ 三档；
  - 失败案例分类（感知/规划/执行）分析；
  - 定性可视化（仿真 vs 真实世界）。
- **充分性评价**：
  - ✅ 任务多样、对比公平、覆盖刚体与可形变；
  - ✅ 包含消融与定性分析；
  - ⚠️ 每个任务仅 10 次试验，统计置信度有限；
  - ⚠️ 缺乏任务之外的场景/物体泛化测试；
  - ⚠️ 无与最新 VLA 模型（如 OpenVLA、RT-2）的直接对比；
  - ⚠️ 仿真与现实的视觉差距（sim2real gap）未量化。

---

## 6. 主要结论与发现

- **整体性能**：在 7 个任务上全面超越基线，成功率分别为 80% / 60% / 40% / 90% / 80% / 80% / 70%，平均显著高于 VoxPoser、MOKA、π0.5（多数为 0%）。
- **关键发现**：
  - **物理接地显著提升 VLM 操控能力**：移除仿真后性能大幅下降，说明语言推理无法替代物理 rollout。
  - **VLM 采样的初始化至关重要**：随机采样导致几乎全部失败。
  - **VLM 优化器能执行"非局部"推理**：可从失败案例中学习并改进行动（如图 4 的"不倒推动"案例）。
  - **采样数量并非越多越好**：$K=20$ 时部分任务（碗堆叠、绳形）反而下降，可能因过长上下文削弱 VLM 推理效果。
- **主要贡献**：
  1. 零样本、测试时 VLM 物理感知动作规划框架；
  2. 单 RGB-D 自动构建多物理引擎仿真的 pipeline；
  3. 以仿真为上下文的 in-context learning 机器人动作生成新范式。

---

## 7. 优点与亮点

- **范式创新**：将"仿真即上下文"引入 VLM 推理，无需任何任务专属训练；
- **系统完整度高**：覆盖感知 → 仿真 → 规划 → 优化 → 执行的端到端 pipeline；
- **任务多样性**：同时支持刚体（MuJoCo）与可形变（MPM、Projective Dynamics）仿真；
- **高层动作抽象**：用符号化（`MOVE/GRASP/RELEASE`）动作调用 VLM 语义先验，再映射到连续轨迹，巧妙利用了 VLM 在预训练数据中常见的符号模式；
- **失败分析细致**：将失败原因分为感知/规划/执行三类，便于后续改进；
- **公开项目页面**：https://simpact-bot.github.io（按文末提供）。

---

## 8. 不足与局限

- **感知层面**：
  - 单视图 3D 重建在遮挡下质量不佳；可引入 inpainting / 生成式 3D 补全模型改进；
  - 物理参数由 VLM 启发式推断，精度有限，sim2real 偏差难以避免。
- **执行层面**：
  - 当前为**开环执行**，对累积误差敏感；
  - 论文提到可选的"重规划"机制（Supp. Sec. B.9）但未充分展开。
- **实验层面**：
  - 每任务仅 10 次试验，统计显著性弱；
  - 缺少对不同 VLM（如 GPT-4V、Claude）的对比；
  - 缺少 sim2real 差距的量化指标。
- **泛化能力**：
  - 未在未见物体、复杂背景、多物体交互场景下验证；
  - 铰接物体（articulating objects）、流体、工具使用等未覆盖。
- **计算开销**：未报告测试时每次规划的实际耗时，难以判断其实用性。
- **失败案例**：pivoting 任务成功率仅 40%，说明对接触细节要求高的任务仍有挑战。

（完）
