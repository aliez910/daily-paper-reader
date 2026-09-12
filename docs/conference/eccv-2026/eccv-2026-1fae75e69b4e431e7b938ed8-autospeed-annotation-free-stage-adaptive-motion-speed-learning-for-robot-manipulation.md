---
title: "AutoSpeed: Annotation-Free Stage-Adaptive Motion Speed Learning for Robot Manipulation"
title_zh: AutoSpeed：面向机器人操控的无标注阶段自适应运动速度学习
authors: "Qingda Hu, Ziheng Qiu, Jieru Zhao, Zhongxue Gan, Wenchao Ding"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/2045.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 针对机器人操控的模仿学习型视觉运动策略框架
tldr: 针对现有模仿学习视觉运动策略固定模仿专家速度与预测时域的问题，本文提出模型无关的AutoSpeed框架。该方法将不同速度的未来轨迹作为候选优化目标，结合复合代价评估，无需阶段或速度标注即可实现阶段自适应的操控策略。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1fae75e69b4e431e7b938ed8/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 2268, \"height\": 649}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1fae75e69b4e431e7b938ed8/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 2189, \"height\": 737}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1fae75e69b4e431e7b938ed8/fig-003.webp\", \"caption\": \"\", \"page\": 9, \"index\": 3, \"width\": 1558, \"height\": 728}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1fae75e69b4e431e7b938ed8/fig-004.webp\", \"caption\": \"\", \"page\": 11, \"index\": 4, \"width\": 2598, \"height\": 1394}]"
motivation: 现有IL视觉运动策略固定模仿速度与时域，限制了操控灵活性与吞吐量。
method: 将不同速度的候选轨迹作为优化目标，通过复合代价评估选择阶段自适应速度。
result: 在不需额外标注的前提下提升了操控策略的灵活性与任务吞吐。
conclusion: 阶段自适应速度学习为视觉运动操控策略提供了通用增强方法。
---

## Abstract
Different stages of manipulation tasks exhibit varying lev-els of difficulty, suggesting stage-dependent motion speeds and temporalprediction horizons. However, existing IL-based visuomotor policies typ-ically imitate the execution speed of expert demonstrations and operatewith a fixed temporal prediction horizon, limiting flexibility and over-all task throughput. In this paper, we introduce AutoSpeed, a model-agnostic learning framework that enables existing visuomotor policies topredict trajectories with stage-adaptive motion speeds, without requir-ing speed or stage annotations. We treat future trajectories at differentspeeds as candidate optimization targets, evaluate each candidate us-ing a composite cost that trades off prediction error against predictionhorizon, and optimize the policy toward the minimum-cost candidate.With a fixed-length action sequence, speed modulation adjusts the ef-fective temporal prediction horizon: simple stages are executed fasterwith a longer prediction horizon, whereas complex stages are executedmore slowly with a shorter prediction horizon. Specifically, we implementspeed modulation in the frequency domain via the discrete cosine trans-form (DCT), which enables smooth, non-integer speed scaling and thuspreserves motion continuity. Extensive evaluations show that AutoSpeedsubstantially reduces task execution time while also improving successrates. Under the AutoSpeed framework, the inferred motion speeds ex-hibit a strong correspondence with task stages.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "AutoSpeed: Annotation-Free Stage-Adaptive Motion Speed Learning for Robot Manipulation" organized into 8 specific sections. Let me analyze the paper carefully and provide a comprehensive summary.

Let me go through the paper systematically:

1. **Core problem and motivation**: Existing IL-based visuomotor policies mimic expert demonstration speeds and use fixed prediction horizons, which limits flexibility and throughput. Different task stages have different difficulties, requiring stage-dependent speeds.

2. **Methodology**: AutoSpeed framework:
   - Treat future trajectories at different speeds as candidate optimization targets
   - Composite cost balancing prediction error vs prediction horizon
   - DCT-based frequency domain speed modulation
   - Ratio Head to predict speed ratio
   - Nonlinear Temporal Aggregation (NTA)
   - Three-stage training strategy for generative models

3. **Experiments**: 
   - Simulation: ALOHA (Transfer Cube, Insertion), LIBERO-10, Meta-World (50 tasks)
   - Real-world: Agilex Piper bimanual robot, 4 tasks
   - Baselines: ACT, BAKU-DiT, BAKU-Flow
   - Metrics: Success rate, episode length, execution time

4. **Compute resources**: Not explicitly mentioned

5. **Number of experiments and sufficiency**: Multiple benchmarks, real-world tasks, ablation studies on speed range and w coefficient

6. **Main conclusions**: Reduces execution time while improving success rates

7. **Strengths**: Model-agnostic, no annotations needed, DCT preserves high-frequency details, NTA enables smooth deployment

8. **Limitations**: Real-world experiments only on 4 tasks, relies on speed ratio sampling range, etc.

Let me write this up in Chinese with Markdown formatting.</think>

# AutoSpeed 论文总结

## 1. 核心问题与研究动机

- **背景**：基于模仿学习（IL）的视觉运动策略（visuomotor policy）已成为机器人操控的主流范式，并广泛延伸至视觉-语言-动作（VLA）大模型。然而现有策略普遍存在两个核心局限：
  - **固定模仿专家速度**：策略原样复制示教中的执行速度，而专家示范速度通常并非最优。
  - **固定预测时域（action chunking horizon）**：策略对所有任务阶段采用统一长度的动作序列输出，忽略不同阶段的难度差异。
- **关键观察**：操控任务天然具备**阶段化结构**——简单阶段（如自由空间接近、回位）需要快速执行与长时域预测；精细阶段（如插轴、持续接触）需要慢速执行与短时域、紧反馈。这与人类运动控制中的速度-精度权衡（speed-accuracy trade-off）相一致。
- **现有方案不足**：已有方法（DemoSpeedUp、ESPADA、SpeedAug、SAIL、VFIL 等）多依赖前置的代理策略或 VLM/LLM 标注，需要外部工具或额外模型；或在推理阶段调节速度，难以端到端联合优化。
- **本文主张**：在端到端训练中**隐式地**推断阶段相关的速度比（speed ratio），无需任何阶段或速度标注。

## 2. 方法论

### 2.1 核心思想
将"不同速度下的未来轨迹"作为一组**候选优化目标**，通过复合代价函数挑选当前阶段最合适的目标来监督策略，从而隐式学习阶段自适应速度。

### 2.2 关键技术细节

- **优化目标集合**：在时间步 *t*，构造 *M* 个候选动作序列 $\{\tilde{A}^{(m)}\}$，对应从 0.8 到 2.2 等离散速度比 $\{r_m\}$。
- **复合代价函数**：
  $$J(\tilde{A}^{(m)}) = E_t^{(m)} + w \cdot \log(h_t)$$
  其中 $E_t^{(m)}$ 为预测误差（MSE），$h_t = H \cdot r_t$ 为有效预测时域，$w$ 为长度惩罚系数。候选速度越快、时域越长，对应代价越低，从而鼓励"能预测就加速"；代价取最小者 $m^\star = \arg\min_m J(\tilde{A}^{(m)})$ 作为监督目标。
- **频域速度变换（DCT）**：通过离散余弦变换将动作序列映射到频域，在频域做时间轴缩放后再逆变换回时域，实现**非整数速度倍率**的平滑加减速，并保留高频细节（对精细操控至关重要）。
  $$\tilde{A} = B(r) \cdot C,\quad C = \text{DCT}(A)$$
- **Ratio Head**：从潜在观测特征中预测速度比 $r_t$，与策略联合训练；用于生成模型第三阶段训练和推理阶段的 NTA。
- **生成模型的三阶段训练**：
  1. **早期阶段**：对所有候选目标取平均损失，让模型先学习平滑、低复杂度的结构。
  2. **多目标选择阶段**：按复合代价选最小代价目标进行监督。
  3. **模式收敛阶段**：冻结 Ratio Head，直接用其预测的速度训练，使生成过程快速收敛到所选模式。
- **非线性时序聚合（NTA）**：针对可变速度预测设计，在固定时间窗口内收集多个 chunk 的重叠预测，按指数衰减加权平均，并对齐时间偏移，实现推理时的平滑执行。
- **模型无关性**：公式 7、8 分别给出了扩散策略（对注入噪声的 MSE）和流匹配策略（对速度场的 MSE）下的误差计算方式；同时支持非生成式（MLP 类）策略。

## 3. 实验设计

### 3.1 数据集与场景
- **仿真**：
  - **ALOHA 仿真**：Transfer Cube、Insertion 两项双臂任务，各 50 条专家示教。
  - **LIBERO-10**：10 个任务的多任务学习场景。
  - **Meta-World**：50 个任务的多任务学习场景。
  - **总计 62 个仿真任务**。
- **真实世界**：Agilex Piper 双臂机器人平台，桌面操控环境，含两路腕部相机 + 一路顶部固定相机；4 个任务（Transfer the Banana、Place the Toy、Stacking Two Cubes、Store Block in Drawer），各约 50 条示教。

### 3.2 对比方法
- **ACT**（Action Chunking Transformer）：非生成式基线。
- **BAKU**：多任务 Transformer 策略，分别测试 **BAKU-DiT**（扩散式动作头）和 **BAKU-Flow**（流匹配式动作头）两种动作头。
- 真实世界实验中还对比了带时序聚合（TA）的 BAKU-Flow。

### 3.3 评估指标
- 任务成功率（SR）
- 平均回合长度 / 执行时间（Len / Time）
- ALOHA 每任务 50 次 rollouts，LIBERO / Meta-World 每任务 10 次，真实世界每任务 20 次。

## 4. 资源与算力

- **论文中未明确说明**所使用的 GPU 型号、数量、训练时长或总算力消耗。
- 仅提到：生成模型由于需要对每个候选目标去噪会带来少量额外开销，但由于动作头参数量占比小且候选去噪可并行，训练不会显著变慢。
- 对 DCT 频域变换的额外计算开销也未给出量化数据。

## 5. 实验数量与充分性

- **主实验**：仿真单任务（ALOHA 2 任务）+ 仿真多任务（LIBERO-10 + Meta-World）+ 真实世界 4 任务，涵盖生成式与非生成式策略。
- **消融实验**：
  - **速度范围消融**：在 ALOHA Transfer Cube 上测试 [1×, 2×]、[1×, 4×]、[2×, 4×] 三种范围，证明不同上下界下策略均能学出"复杂阶段减速"的一致模式。
  - **长度惩罚系数 *w* 消融**：测试 0.3、0.7、1.3、1.7 四个值，分析其对速度偏好与性能的影响。
- **真实世界对比**：AutoSpeed + NTA 与 BAKU-Flow + TA 在 4 个任务上对比。
- **速度比与阶段的对应关系可视化**（图 4）：定性展示推断速度与任务阶段的对齐。
- **充分性评估**：
  - 实验覆盖了仿真 + 真实、生成 + 非生成、单任务 + 多任务三种维度。
  - 但真实世界仅 4 个任务且全部为桌面简单操控，泛化性证据较弱。
  - 速度范围与 *w* 的消融仅在 ALOHA Transfer Cube 一个任务上完成，跨任务一致性证据不足。
  - 与 DemoSpeedUp 之外的多种最新方法（SAIL、SRIL、SpeedAug 等）的直接对比有限。

## 6. 主要结论与发现

- **效率与成功率兼得**：AutoSpeed 在所有基准上同时**降低执行时间**并**提升成功率**——ALOHA Transfer Cube 上加速至 1.7×；LIBERO-10 最高加速约 40%；Meta-World 上 BAKU-DiT 成功率提升 19%、BAKU-Flow 提升 7.8%；真实世界平均加速约 1.78×。
- **速度与阶段强对齐**：训练中隐式推断的速度曲线与任务阶段高度吻合，复杂交互阶段自动减速，简单阶段自动加速，且这一模式在不同的速度范围与 *w* 设置下均稳定出现。
- **相对熵方法的优越性**：相比 DemoSpeedUp 基于动作熵识别可加速阶段的方式，AutoSpeed 对"启动 / 回位"等快速运动阶段识别更准确，且能区分多模态不确定性与真实预测不确定性。
- **耦合时域调整**：通过固定输出 chunk 长度 + 速度缩放，等效实现了阶段自适应的预测时域，无需枚举多个候选时域。
- **控制性**：通过调整速度范围和 *w*，可控制运动风格（保守 / 激进）。

## 7. 优点

- **真正无需标注**：完全端到端隐式推断阶段信号，规避了外部标注或代理策略的成本与不一致问题。
- **模型无关**：兼容非生成式（MLP / Transformer）与生成式（扩散 / 流匹配）策略，公式清晰且适用范围广。
- **频域 DCT 调速**：支持非整数倍速缩放，保留高频动作细节，对精细操控更友好。
- **生成式模型训练稳定性**：三阶段训练策略有效缓解了多目标优化的不稳定性。
- **推理阶段的 NTA**：解决可变速度预测下的时序聚合问题，实现平滑部署。
- **实验设计覆盖面较广**：仿真 + 真实 + 多种动作头 + 消融实验。

## 8. 不足与局限

- **真实世界实验规模偏小**：仅 4 个桌面任务、约 50 条示教 / 任务，20 次评估 / 任务，对真实世界的泛化与鲁棒性证据较弱。
- **算力信息缺失**：未报告 GPU 型号 / 数量 / 训练时长，难以评估方法的实际部署成本与可复现性。
- **超参数依赖**：速度范围、*w* 系数需手动设定，虽具控制性但缺乏自适应机制；消融仅在一个任务上进行，跨任务迁移性未验证。
- **动作过采样的依赖**：真实世界实验中示教被过采样 2× 才能充分体现 DCT 减速下的精细动作保真度，普通数据上的极限性能可能受限。
- **高速度与高增益耦合**：ALOHA Transfer Cube 在标准控制器下加速反而导致成功率下降（72% → 64%），需结合高增益控制器才能超越基线（78%），意味着该方法对底层控制器有额外要求。
- **缺乏与更多最新基线的直接对比**：与 SAIL、SRIL、SpeedAug 等方法仅有概念对比，未在统一基准上做 head-to-head 评估。
- **误差信号 $E_t^{(m)}$ 在生成模型下依赖代理目标**（如对噪声的 MSE），不同生成范式下可能产生不一致的速度选择偏好，理论分析不足。
- **任务阶段边界的"隐式性"**：虽然推断速度与阶段对齐，但模型并未显式输出阶段标签，缺乏可解释性与可控性。

（完）
