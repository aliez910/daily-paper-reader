---
title: "FM-Steer: Enhance Generalist Policies with Value-Guided Cascaded Denoising"
title_zh: FM-Steer：基于价值引导级联去噪增强通用机器人策略
authors: "Song, Haoming, Qu, Delin, Yao, Yuanqi, Chen, Qizhi, Li, Jiarui, Lv, Qi, Tang, Yiwen, Kang, Li, Zhou, Heng, Gao, Xianqiang, Tang, Yuhang, Li, Xiaofan, Shi, Modi, Ren, Guanghui, Yao, Maoqing, Zhao, Bin, Wang, Dong, Li, Xuelong"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Song_FM-Steer_Enhance_Generalist_Policies_with_Value-Guided_Cascaded_Denoising_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于价值引导采样增强流式 VLA 通用策略以支持灵巧操作
tldr: 测试时计算扩展在数字领域大语言模型上效果显著，但在面向物理世界的机器人基础模型中尚未得到充分探索。为此，本文提出 FM-Steer 框架，针对基于流的视觉-语言-动作通用策略，引入价值引导采样与级联动作去噪机制，并通过中间流验证器估计状态-动作价值。该方法显著提升了灵巧机器人操作中的控制性能与实时动作生成速率，为通用 VLA 策略的测试时增强提供了实用方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1777, \"height\": 797, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1754, \"height\": 850, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1806, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1796, \"height\": 573, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 766, \"height\": 624, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 870, \"height\": 243, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1810, \"height\": 378, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1804, \"height\": 716, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-song-fm-steer-enhance-generalist-policies-with-value-guided-cascaded-denoising-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 277, \"label\": \"Table\"}]"
motivation: 测试时计算扩展尚未充分应用于面向物理世界的机器人基础模型。
method: 引入价值引导采样与级联去噪机制，通过流验证器提升 VLA 通用策略性能。
result: 在灵巧机器人操作任务中提升了控制性能与实时动作生成速率。
conclusion: 为通用机器人策略的测试时计算增强提供了有效框架。
---

## Abstract
Humans naturally allocate more time before acting when handling complex tasks in the physical world. This paradigm has recently led to remarkable advances in boosting Large Language Models (LLMs) on complex tasks in digital domains. However, the potential of test-time computing remains largely unexplored for robotic foundation models that interact with the physical world. In this work, we propose FM-Steer, a test-time computing framework that augments flow-based Vision-Language-Action (VLA) generalist policies with value-guided sampling and cascaded action denoising, enabling stronger control performance and real-time action rates for dexterous robot manipulation. FM-Steer first introduces an intermediate flow verifier to estimate state-action values for candidate actions. At test time, the policy iteratively samples multiple noisy action proposals and retains the one with the highest predicted value, yielding value-aligned, high-quality actions without retraining. To satisfy the stringent frequency demands of robot control, FM-Steer further introduces cascaded action denoising, decoupling expensive value-guided sampling from fast action refinement. A lightweight Lite-Flow denoiser asynchronously takes the selected high-value noisy action and rapidly denoises it to produce the final control signal, enabling fluid, high-rate execution. During deployment, the intermediate verifier operates at a low frequency to provide value-guided sampling, while the Lite-Flow denoiser continually processes selected candidates to maintain real-time control. Extensive experiments demonstrate that FM-Steer scales flow-based VLA models effectively at test time and achieves state-of-the-art performance across diverse simulation benchmarks and real-world dexterous robotic tasks. The source code is available on the project page: https://hume-vla.github.io.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "FM-Steer: Enhance Generalist Policies with Value-Guided Cascaded Denoising" based on the provided PDF content and metadata. Let me organize this carefully following the 8 requested sections.

Let me analyze the paper:

1. Core problem & motivation: Test-time computing has been successful in LLMs but not explored for robotic foundation models (especially flow-based VLAs). Robot control has strict real-time requirements.

2. Methodology:
- Value-guided test-time sampling: instead of sampling fully denoised actions, sample intermediate flow points with varying noise levels
- Intermediate flow verifier φ: trained with offline RL (calibrated Q-learning), estimates state-action value Q(qt, Aτnt) for candidate flow points, uses Best-of-N selection
- Noise forcing + stochastic Euler forward process to overcome determinism of flow matching
- Special query token qt attached to VLA input sequence
- Cascaded action denoising: original VLA does denoising from 0 to τ*, Lite-Flow denoiser ϕ does τ* to 1
- Lite-Flow denoiser: lightweight transformer, takes sub-action chunks and continues denoising
- Asynchronous operation: VLA at 4Hz, Lite-Flow at 90Hz
- Equation (2): noise forcing for candidate generation
- Equation (4): argmax selection
- Equation (5): Lite-Flow denoising

3. Experiments:
- 3 simulation benchmarks: LIBERO, SimplerEnv (WidowX + Google Robot matching & aggregation)
- 3 real-world platforms: WidowX 250s, AgiBot G-1, Franka
- 15 robot learning scenarios, 21 real-world manipulation tasks
- Compared with OpenVLA-OFT, OpenHelix, π0, π0.5, GR00T N1, OpenVLA, V-GPS, RoboMonkey

4. Resources:
- Trained on 8 A100 GPUs, batch size 8-32
- Inference on single RTX 4090
- No training time mentioned

5. Experiments count and adequacy:
- LIBERO: 4 sub-benchmarks (Spatial, Object, Goal, Long)
- SimplerEnv: 4 WidowX tasks + 4 Google Robot tasks (matching & aggregation = 8 more)
- Real-world: 3 platforms, 21 tasks total
- Ablations: 4 settings × multiple benchmarks/robots
- Visualization with PCA

6. Main conclusions:
- FM-Steer achieves SOTA
- π0 + FM-Steer: +4.4% LIBERO, +25.9% Simpler, +12.9% real-world
- 91% success rate on WidowX (vs 79% for π0, 58% for OpenVLA)
- 87% on Franka (vs 73% π0, ~67% OpenVLA)
- 82% on AgiBot G-1
- Maintains high control frequency

7. Strengths:
- Novel test-time scaling for flow-based VLAs
- Cascaded denoising solves efficiency problem
- Asynchronous architecture (4Hz VLA + 90Hz Lite-Flow)
- Failure recovery capability
- Strong generalization across platforms

8. Limitations:
- Real-world tasks limited (21 tasks)
- Only tested with 2 flow-based VLA bases (π0, GR00T N1)
- Hyperparameter sensitivity (T in 0.7-0.9, N=5)
- Comparison with limited test-time baselines
- Real-world ablation limited to 4 settings

Let me write this in Chinese, structured with Markdown.</think>

# FM-Steer 论文总结

## 1. 核心问题与研究背景

- **关键问题**：测试时计算（test-time computing）已在数字域大语言模型（LLM）中取得显著效果（如数学、编程、对话等任务），但在面向物理世界的机器人基础模型（尤其是基于 Flow Matching 的视觉-语言-动作 VLA 模型）中仍未被充分探索。
- **核心矛盾**：机器人控制对实时性（控制频率）要求极高，简单的"重复采样+验证"（如 V-GPS、RoboMonkey）虽能提升性能，却会大幅降低控制频率，难以胜任灵巧动态任务；而 Flow Matching 推理本身因多次 Euler 前向迭代开销大，进一步加剧了该矛盾。
- **两个关键问题**：
  - 如何对 Flow-based VLA 模型进行有效的测试时计算？
  - 如何在提升性能的同时保持甚至提高实时控制频率？

## 2. 方法论

FM-Steer 是一个测试时计算框架，针对 Flow-based VLA 设计了两个核心模块：**中间流验证器（Intermediate Flow Verifier）** 与 **Lite-Flow 去噪器**，并采用**异步工作**方式。

### 2.1 价值引导的测试时采样（Value-Guided Test-Time Sampling）

- **核心理念**：不对最终去噪完成的动作进行重复采样（开销过大），而是在 Flow Matching 的 ODE 轨迹上对**中间带噪动作（flow points）**进行采样与筛选。
- **候选生成（噪声强制 + 随机 Euler 过程）**：
  - 对第 n 个候选点 $A^n_{\tau_t}$ 设置不同噪声水平 $\tau_n = T - (n-1)\xi$，$T \in (0,1)$ 控制原始 VLA 的去噪计算量，$\xi$ 控制相邻候选点之间的噪声间隔；
  - 每个候选点的 Euler 前向过程被建模为各向同性高斯分布 $p(A^{\tau+\delta}_t | A^\tau_t) \sim \mathcal{N}(\mu_\tau, \Sigma_\tau)$，通过注入方差 $\Sigma_\tau$ 打破 Flow Matching 的确定性，从而获得多样化的中间候选。
- **特殊查询 token $q_t$**：作为可学习 token 附加在原始 VLA 输入序列末尾，与 VLM 输出的图像/文本/状态/动作 token 充分交互后聚合当前观测信息。
- **中间流验证器 $\varphi$**：
  - 输入：$q_t$ 与候选 flow point $A^n_{\tau_t}$；
  - 输出：状态-动作价值 $Q_\varphi(q_t, A^n_{\tau_t})$；
  - **训练**：使用离线强化学习（Calibrated Q-learning），从同一机器人示范数据集构建；将 ground-truth 动作按 $A^T_t = T \cdot A_t + (1-T)\cdot \epsilon$ 构造为对应噪声水平的带噪动作；奖励采用稀疏二值奖励（每个 episode 最后 3 步成功为 +1，其余为 0）。
- **Best-of-N 选择**：选择价值最高的候选 $A^{\tau^*}_t = \arg\max_{A^n_{\tau_t}} Q_\varphi(q_t, A^n_{\tau_t})$。

### 2.2 级联动作去噪（Cascaded Action Denoising）

- **核心思想**：将去噪过程在原始 VLA 与 Lite-Flow 去噪器之间**解耦**。
- **原始 VLA**：仅完成从 $0$ 到 $\tau^*$ 的部分去噪（低频，4 Hz）；
- **Lite-Flow 去噪器 $\phi$**：一个轻量 Transformer，从 $\tau^*$ 到 $1$ 完成剩余去噪过程（高频，90 Hz）。
- **子动作分块**：将 $A^{\tau^*}_t$（horizon $H=30$）均匀切成 $K$ 个子块（$h=15$），第 $k$ 个子块 $A^{\tau^*}_{t,k}$ 对应观测 $o_{t,k}$，Lite-Flow 通过 $\int_{\tau^*}^1 v_\phi(A^\tau_{t,k}, o_{t,k}) d\tau + A^{\tau^*}_{t,k}$ 输出精细动作。
- **训练**：Lite-Flow 使用相同的 Flow Matching 损失，但输入是噪声水平为 $\tau^*$ 的带噪子动作而非纯噪声。

### 2.3 异步部署

- **共享队列**：原始 VLA + 验证器 4 Hz 运行，将最优候选存入队列；Lite-Flow 从队列中持续取出进行去噪，以 90 Hz 输出执行动作；
- **优势**：将昂贵的"重复采样+验证"与高频动作精修解耦，既保证推理深度又保证实时性。

## 3. 实验设计

### 3.1 仿真基准
- **LIBERO**：4 个子基准（LIBERO-Spatial / Object / Goal / Long），评估终身知识迁移与长期任务能力。
- **SimplerEnv**：包含 WidowX 250 平台 4 个任务，以及 Google Robot 平台的 4 个任务，分别在 **Visual Matching** 与 **Visual Aggregation** 设置下评估，测试视觉泛化。

### 3.2 真实机器人平台（共 3 个、21 个任务）
- **WidowX 250s**：6-DoF 伺服控制，10 个任务，零样本；
- **Franka Emika Panda**：7-DoF 协作臂控制，4 个任务（运行于 20 Hz 高频）；
- **AgiBot G-1 人形机器人**：全身上肢控制，4 个任务（运行于 30 Hz 高频）。

### 3.3 对比方法
- **通用策略基线**：OpenVLA、OpenVLA-OFT、OpenHelix、π0、π0.5、GR00T N1；
- **测试时计算基线**：V-GPS、RoboMonkey。

### 3.4 评估指标
- 任务成功率（SR）及其标准误差；
- 控制频率（Hz）；
- 任务平均排名（Rank）；
- 可视化价值图与 PCA 投影。

## 4. 资源与算力

- **训练**：8 张 **NVIDIA A100** GPU，batch size 在 8–32 之间（依数据集不同而异）；
- **推理部署**：单张 **RTX 4090** GPU；
- **超参数**：噪声上界 $T \in [0.7, 0.9]$，候选数 $N = 5$，动作块长度 $H = 30$，子块长度 $h = 15$，原始 VLA 工作频率 4 Hz，Lite-Flow 90 Hz；
- **未提及**：训练总时长、每个数据集的训练 epoch 数、Lite-Flow 验证器的模型规模、推理延迟数值等细节。

## 5. 实验数量与充分性

- **主实验**：
  - LIBERO：4 子基准 × 多模型对比，覆盖 SOTA 与自对比；
  - SimplerEnv：2 个平台（WidowX、Google Robot）× 4 任务 × 2 设置（Matching、Aggregation）；
  - 真实机器人：3 平台 × 共 21 任务，对比 4 类基线。
- **控制频率分析**：在 WidowX 平台上对比 V-GPS、RoboMonkey、FM-Steer 在调整超参数达到最佳性能后的控制频率（图 1）。
- **可视化分析**：
  - 价值图（候选动作在 PCA 空间中的价值分布）；
  - 级联去噪轨迹投影（x-y、x-z 平面）。
- **消融实验**：4 个消融设置（w/o Cascaded Denoising、w/o Repeat Sampling、w/o Lite-Flow Denoiser、w/o Flow Verifier），分别在 LIBERO、SimplerEnv、AgiBot 4 任务、Franka 10 任务、WidowX 10 任务上评估。
- **充分性评价**：实验覆盖仿真 + 真实、3 个机器人形态、多种基线、消融完整，整体较为充分；但真实世界任务样本数有限（21 个），仍属中等规模；多个对比项未在所有平台统一测试。

## 6. 主要结论与发现

- **性能领先**：
  - LIBERO：FM-Steer(π0) 平均成功率 **98.6%**，排名第一，超过 π0.5（96.8%）与 OpenVLA-OFT（97.1%）；
  - SimplerEnv WidowX：**79.5%**，较 V-GPS（37.0%）提升 +42.5%，较 RoboMonkey（47.8%）提升 +31.7%；
  - SimplerEnv Google Robot：Matching 76.6%、Aggregation 60.3%，均 SOTA；
  - 真实机器人：WidowX 平均 **91%**（较 π0 +12%、OpenVLA +33%），Franka **87%**（较 π0 +14.75%），AgiBot G-1 **82%**（较 π0 +20%）。
- **价值引导 + 级联去噪协同**：在 LIBERO 消融中分别去掉任一组件，性能下降 2.7%–8.8%；真实机器人场景下降幅度更大（最高 -78%）。
- **频率优势**：FM-Steer 是唯一同时提升性能与控制频率的方法，原始 VLA 4 Hz + Lite-Flow 90 Hz 异步架构兼顾"深思"与"快动"。
- **失败恢复能力**：当策略进入错误状态时，验证器可选择更优候选进行轨迹修正，提升鲁棒性。
- **可视化结论**：ground-truth 动作位于验证器估计的高价值区域；Lite-Flow 在 x-y、x-z 平面内对所选候选点进行进一步精修。

## 7. 优点

- **新颖性**：首次系统地将测试时计算范式推广至 Flow-based VLA；引入"中间候选 + 价值引导"的非端到端思路，避免重复完整去噪的巨大开销；
- **架构设计精巧**：通过级联去噪与异步部署，巧妙化解"深度推理 vs. 高控制频率"的矛盾，原始 VLA 4 Hz、Lite-Flow 90 Hz 的分工具备工程美感；
- **通用性强**：以插件式方式增强现有 Flow-based VLA（π0、GR00T N1），无需重训原模型；同时适用于多种机器人形态（6-DoF、7-DoF、人形上肢）；
- **鲁棒性显著**：在复杂任务（如绿色杯子放在粉色布上、泡茶等）中展现出失败恢复能力；
- **消融充分**：四大组件均参与消融，且覆盖仿真+真实多个平台；
- **可视化直观**：价值图与轨迹投影增强了结果可解释性。

## 8. 不足与局限

- **真实世界实验规模有限**：仅 3 个平台、21 个任务，样本量与场景多样性相对中等；
- **基线对比覆盖不均**：Flow-based VLA 仅在 π0 与 GR00T N1 上验证，对其他 Flow-based 模型（如近期提出的多种 VLA）的适用性未充分测试；
- **超参数依赖性**：$T \in [0.7, 0.9]$、$N=5$、$h=15$ 等超参数对性能影响显著，但论文未给出系统性的敏感性分析；
- **训练细节不透明**：未公开训练时长、Lite-Flow 与验证器的具体规模、数据集采样比例等细节，影响复现性；
- **离线 RL 验证器的局限**：训练数据来自示范数据，可能在分布外（OOD）状态或长尾任务上价值估计偏差；
- **效率与硬件约束**：测试时需多次采样并调用 Lite-Flow，对算力的需求高于单次推理，对部署硬件有较高门槛；
- **未见对动态性极强任务的深入分析**：虽提到 90 Hz，但对极端动态（如高速避障、瞬时反应）的适用性未深入论证。

（完）
