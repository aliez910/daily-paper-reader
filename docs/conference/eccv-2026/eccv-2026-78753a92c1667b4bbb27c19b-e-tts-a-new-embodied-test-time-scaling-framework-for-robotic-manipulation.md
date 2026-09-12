---
title: "E-TTS: A New Embodied Test-Time Scaling Framework for Robotic Manipulation"
title_zh: "E-TTS:面向机器人操作的新型具身测试时计算扩展框架"
authors: "Wen Ye, Peiyan Li, Tingyu Yuan, Yuan Xu, Xiangnan Wu, Chaoyang Zhao, Jing Liu, Nianfeng Liu, Yan Huang, Liang Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/7793.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向机器人操作的测试时计算扩展框架
tldr: "测试时计算扩展在具身任务中展现潜力,但面临两大挑战:推理-动作扩展机制研究不足,长视野任务依赖历史信息而仅靠当前观测不足。本文提出E-TTS模块化即插即用框架,通过视觉-语言验证器实现历史感知的迭代精炼,统一推理与动作扩展。该方法支持机器人操作的联合推理-动作扩展,为序列决策下的操作策略部署拓展了工具箱,具有实际应用价值。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1204, \"height\": 902}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 812, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 704, \"height\": 524}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 706, \"height\": 522}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 708, \"height\": 532}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 672, \"height\": 376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 672, \"height\": 376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 672, \"height\": 376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 672, \"height\": 376}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-010.webp\", \"caption\": \"\", \"page\": 5, \"index\": 10, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 2520, \"height\": 1888}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-013.webp\", \"caption\": \"\", \"page\": 5, \"index\": 13, \"width\": 2518, \"height\": 1892}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-014.webp\", \"caption\": \"\", \"page\": 14, \"index\": 14, \"width\": 2388, \"height\": 1013}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-78753a92c1667b4bbb27c19b/fig-015.webp\", \"caption\": \"\", \"page\": 15, \"index\": 15, \"width\": 4000, \"height\": 2250}]"
motivation: "现有测试时扩展方法在推理-动作联合扩展与历史信息利用方面研究不足,难以处理长视野操作任务。"
method: "提出E-TTS模块化框架,通过视觉-语言验证器实现历史感知的推理与动作联合迭代精炼。"
result: "在多种长视野机器人操作任务中提升策略性能,验证了联合扩展机制的有效性。"
conclusion: "为操作策略的测试时计算扩展提供统一框架,推动具身智能体在复杂序列任务中的实用部署。"
---

## Abstract
Recently, a few works have made early attempts to study test-time scaling for embodied tasks. However, two major challenges remain unsolved: (1) reasoning can effectively improve the performance of the policy, but its scaling mechanism has seldom been studied; (2) historical information is essential, as embodied tasks are inherently longhorizon and sequential, making sole reliance on current observations for action scaling inadequate due to the lack of historical context utilization. To address these challenges, we introduce E-TTS, a modular and plugand-play Embodied Test-Time Scaling framework that unifies reasoning and action scaling for robotic manipulation via history-aware iterative refinement with vision-language verifiers. To support joint reasoning-action scaling, E-TTS performs reasoning-action joint sampling and scoring in a pairwise manner. To better utilize historical information, E-TTS uses a history buffer to store historical context, which is then used by reasoning and action verifiers to evaluate the sampled candidates. Unlike conventional open-loop TTS methods, E-TTS introduces feedback generation into the sampling process to form a closed-loop iterative refinement mechanism, enhancing both inference efficiency and environmental adaptability. Each component functions as an independent and composable module, allowing flexible and adaptive configuration depending on task requirements. To evaluate the advantages of our framework, we conduct experiments across 4 different benchmarks, 6 environments, 3 embodiments, and 4 base vision-language-action models. The experimental results demonstrate that, without requiring additional expert data collection or retraining, E-TTS consistently improves performance, achieving up to a 33.14% increase in simulation and 26.62% in real-world scenarios. Our project page is https://27yw.github.io/E-TTS-Web/. *Equal contribution.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "E-TTS: A New Embodied Test-Time Scaling Framework for Robotic Manipulation" following a specific structure with 8 points. Let me analyze the paper carefully and produce a comprehensive summary.

Key information from the paper:
1. Problem: Test-time scaling for embodied tasks has two unresolved challenges - reasoning scaling mechanism not studied, and historical information not utilized for long-horizon sequential tasks.
2. Method: E-TTS framework - modular, plug-and-play, history-aware iterative refinement with vision-language verifiers, joint reasoning-action sampling and scoring, feedback-guided refinement.
3. Experiments: 4 benchmarks (SimplerEnv WidowX, SimplerEnv Google Robot, LIBERO, LIBERO-Plus, VLAbench, real-world), 6 environments, 3 embodiments, 4 VLA models (E-CoT, MolmoAct, π0.5, Embodied-R1).
4. Resources: No explicit GPU info mentioned in the paper.
5. Experimental comprehensiveness: Many ablations, comparisons with RoboMonkey, naive TTS baseline, multiple benchmarks.
6. Results: 33.14% max improvement in simulation, 26.62% in real-world.
7. Pros: plug-and-play, modular, history-aware, feedback loop, jointly scales reasoning and action.
8. Limitations: Not explicitly discussed in paper.

Let me write this in Chinese with Markdown formatting.</think>

# 论文总结：E-TTS —— 面向机器人操作的新型具身测试时计算扩展框架

## 1. 核心问题与研究动机

- **研究背景**：测试时计算扩展（Test-Time Scaling, TTS）通过增加推理阶段的算力换取更高输出质量，已在 CV/NLP 中取得显著成效。由于真实机器人数据采集成本极高，TTS 在具身领域同样具有吸引力（许多任务如物体重排等延迟不敏感，优先追求任务成功率）。
- **现有 TTS 在具身领域的不足**：以 Hume、RoboMonkey、RoVer、TACO 为代表的工作仅在**动作空间**进行扩展，且未利用历史信息，忽略了具身任务的两大本质特征——
  1. **推理与动作紧密耦合**：现有 VLA 模型（如 E-CoT、MolmoAct、π0.5、Embodied-R1）普遍先输出中间推理再生成动作，仅扩展动作会造成高层规划与低层执行的失配；
  2. **长视野、序列决策特性**：单纯依靠当前观测评估候选动作，缺乏历史轨迹上下文，限制了在复杂具身场景中的效果。
- **整体目标**：提出一个**即插即用、模块化**的具身 TTS 框架 E-TTS，统一推理与动作的联合扩展，并结合历史信息与闭环反馈机制。

## 2. 方法论：核心思想与关键技术

### 2.1 整体框架
- 给定任务指令 $I$ 与当前观测 $O_t$，按以下流程在每个时间步运行：
  1. **推理-动作联合采样**（Sec. 3.2）
  2. **历史感知验证与选择**（Sec. 3.3）
  3. **反馈引导的迭代精炼**（Sec. 3.4）
- 各模块均可独立启停、可组合，无需重训或额外专家数据。

### 2.2 推理-动作联合采样
- 给定通用策略 $\pi_\theta(c_t, a_t \mid O_t, I)$，每步采样 $M$ 条推理 $c_t^i$，每条推理下采样 $N$ 个动作，形成**联合样本**：
  $$J_{t}^{i,j} = (c_t^i, a_t^{i,j}), \quad B_t^i = \{J_t^{i,j}\}_{j=1}^{N}$$
- 维护一个**滑动窗口历史缓冲** $H_t = \{J_{t-K}, O_{t-K}, \dots, J_{t-1}, O_{t-1}\}$，为后续验证器提供时序依赖信息。

### 2.3 历史感知验证与选择
- **推理验证器 $V_c$（零样本）**：基于 Qwen2.5-VL-7B，针对三类推理设计专门处理策略：
  - **文本推理**（如 Embodied-R1 的子任务）：评估逻辑一致性、因果合理性；
  - **多模态推理**（如 E-CoT 的框/夹爪位姿 + 子任务）：将视觉感知渲染到图像上作为视觉提示；
  - **空间推理**（如 MolmoAct 的轨迹关键点）：转化为视觉提示并叠加到原观测，配合代表性示例提升 VLM 对空间上下文的理解。
- **动作验证器 $V_a$（训练）**：基于 LLaVA-7B，使用 SimplerEnv 与 LIBERO 收集的 90k 配对（成功/失败）轨迹，按 MSE 准则打标，采用改进的 Bradley–Terry 损失训练；动作按 RT-2 方式离散为 256 bins。
- **联合评分 + ε-greedy 自适应选择**：
  $$S_t^{i,j} = S_c^{i,j} \times \hat{S}_a^{i,j}$$
  以概率 $\epsilon$ 随机探索，否则选择联合分数最高者，且分数须超过阈值 $\eta$，否则进入下一轮重采样。

### 2.4 反馈引导的闭环迭代精炼
- 当整批候选被拒绝时，推理验证器对失败样本生成**结构化文本反馈** $F_t^i$（针对错误归因与改进建议），将反馈拼接回指令形成新提示：
  $$I_t^{i+1} = \text{Concat}(I, F_t^i)$$
- 驱动 VLA 在下一轮重新采样，直到找到高分候选或达到最大批次上限 $M$。
- **效率优化**：使用 vLLM 引擎 + PagedAttention + 静态指令前缀共享，最小化额外延迟。

## 3. 实验设计

### 3.1 数据集 / 场景 / Benchmark
| Benchmark | 平台 | 用途 |
|---|---|---|
| SimplerEnv (Visual Matching & Variant Aggregation) | WidowX / Google Robot | 真实到仿真迁移评估 |
| LIBERO（Spatial / Object / Goal / Long 四类，每类 10 任务） | Franka Panda | 终生学习与知识迁移 |
| LIBERO-Plus（7 类扰动 10030 任务，每类前 200 个评估） | Franka Panda | 鲁棒性泛化测试 |
| VLAbench | 复合任务平台 | 长视野推理、世界知识、语义指令、物理常识 |
| 真实世界 | Franka Research 3 + ZED 2i + RealSense D405 | 实机部署验证 |

### 3.2 对比方法
- **基座 VLA 模型**：E-CoT、MolmoAct、π0.5、Embodied-R1（覆盖文本/多模态/空间三类推理）；
- **TTS 基线**：RoboMonkey（仅扩展动作）、naive TTS（同时扩推理与动作但无历史/反馈）、TACO（附录 B.8 中评估）。

### 3.3 评估规模
- 每个任务 24–50 次 rollout；
- 实机每个任务 40 次 rollout，共 160 次；每任务收集 100 条 SpaceMouse 示教用于 MolmoAct 微调。

## 4. 资源与算力

- 论文**未明确披露**训练/推理所用的 GPU 型号、数量或训练时长；
- 仅说明推理阶段使用了 **vLLM 引擎 + PagedAttention + 前缀共享 KV 缓存**等系统级优化；
- 推断属于使用通用 GPU 集群运行（如 NVIDIA A100/H100 级别，因 vLLM 是其主流部署方案），但具体配置缺失。

## 5. 实验数量与充分性

- **集成验证维度**：4 个 VLA × 6 个环境 × 3 种本体 × 4 个 Benchmark；
- **消融实验**：在 SimplerEnv WidowX + E-CoT 上对反馈、推理扩展、动作扩展、联合评分、历史缓冲、ε-greedy 六组件逐一去除；
- **超参数扫描**：对样本规模 (R/A)、历史长度 K、阈值 η、探索率 ε 进行了较系统的网格扫描；
- **性能-延迟权衡分析**：与 RoboMonkey 对比，仅增加 7.8% 执行时间却提升 51.5% 平均成功率；
- **推理-动作资源配比实验**：在 60 步采样上限下测试 5 种分配比例，确认 1:1 配比最佳；
- **客观性与公平性**：每个方法使用相同的任务指令与评估间隔（10 步）；消融对照清晰，但部分基线（如 RoboMonkey）只在单一环境集成，可能对结果有轻微偏差。

## 6. 主要结论与发现

- **有效性**：E-TTS 在 4 个 Benchmark 上对 4 种 VLA 均能稳定提升，无需重训或额外专家数据，仿真最高提升 **33.14%**，实机平均提升 **26.62%**（22.13% → 48.75%）；
- **关键设计贡献**：联合推理-动作扩展 + 历史缓冲 + 闭环反馈，三者缺一不可；
- **历史长度**：在 K≈10 时收益最大，过长会引入噪声；
- **推理 vs 动作配比**：1:1 配比最优，单边过强均会下降；
- **可扩展性**：模块化设计使其可灵活组合，对不同推理类型的 VLA 通用；
- **涌现行为**：实机中观察到自主重试抓取等自纠错能力，作者认为源自 VLM 的预训练知识。

## 7. 优点与亮点

- **首个统一推理+动作的具身 TTS 框架**，填补现有工作仅扩动作的空白；
- **闭环反馈机制**区别于传统开环 TTS，可显著提升推理-动作对齐与采样效率；
- **历史感知**契合具身任务的序列决策本质；
- **即插即用**：不修改 VLA 权重，模块可独立启停，便于社区复用；
- **效率优化**完善（vLLM + PagedAttention + 前缀共享），使延迟开销可控；
- **实验广度大**：覆盖 4 VLA × 6 环境 × 3 本体，含消融、超参、性能-延迟、资源配比、实机五类分析；
- **实机自纠错**是亮点发现。

## 8. 不足与局限

- **算力与训练细节不透明**：未给出 GPU 型号/数量/训练时长，难以复现；
- **实机任务规模有限**：仅 4 个任务、每任务 40 次 rollout，统计显著性受限于样本量；
- **验证器依赖外部 VLM**：Qwen2.5-VL-7B 与 LLaVA-7B 带来额外推理开销，对延迟敏感场景适用性受限；
- **历史缓冲长度与阈值依赖经验**：K、η、ε 需针对不同任务手工调优，缺乏自适应机制；
- **RoboMonkey 等基线仅在单一环境集成**，对比公平性有限；
- **未涉及多模态大反馈模型的失败模式分析**，对错误反馈的可靠性讨论不足；
- **应用限制**：仍主要适用于延迟不敏感的长视野任务，对实时控制任务（如高速跟踪）尚未验证；
- **计算开销与碳成本**未讨论。

（完）
