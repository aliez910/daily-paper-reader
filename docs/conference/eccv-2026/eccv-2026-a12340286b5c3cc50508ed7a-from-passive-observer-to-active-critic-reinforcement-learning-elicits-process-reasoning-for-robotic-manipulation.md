---
title: "From Passive Observer to Active Critic: Reinforcement Learning Elicits Process Reasoning for Robotic Manipulation"
title_zh: 从被动观察者到积极评价者：强化学习激发机器人操纵的过程推理
authors: "Yibin Liu, Yaxing Lyu, Daqi Gao, Zhixuan Liang, Weiliang Tang, Shilong Mu, Xiaokang Yang, Mingyu Ding, Yao Mu"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/6202.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向长视距机器人操纵的过程推理与监控
tldr: 长视距机器人操纵中过程监督的准确性是关键瓶颈：现有视频多模态大模型仅被动识别事件而无法判断当前状态相对目标的进展。本文提出PRIMO R1，利用基于结果的强化学习激励显式思维链推理生成进度估计，并将视频序列锚定到任务阶段构建结构化时间输入，从而将MLLM转变为积极评估进程的评价者，显著提升长视距任务的进程监控可靠性。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 384, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 384, \"height\": 386}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 386, \"height\": 386}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 420, \"height\": 420}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 582, \"height\": 582}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 420, \"height\": 420}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 412, \"height\": 337}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 1000, \"height\": 250}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 1000, \"height\": 250}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-010.webp\", \"caption\": \"\", \"page\": 2, \"index\": 10, \"width\": 1000, \"height\": 250}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 389, \"height\": 384}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 384, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-013.webp\", \"caption\": \"\", \"page\": 5, \"index\": 13, \"width\": 384, \"height\": 384}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-014.webp\", \"caption\": \"\", \"page\": 5, \"index\": 14, \"width\": 384, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-015.webp\", \"caption\": \"\", \"page\": 5, \"index\": 15, \"width\": 582, \"height\": 582}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-016.webp\", \"caption\": \"\", \"page\": 5, \"index\": 16, \"width\": 582, \"height\": 582}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-017.webp\", \"caption\": \"\", \"page\": 5, \"index\": 17, \"width\": 870, \"height\": 548}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-018.webp\", \"caption\": \"\", \"page\": 5, \"index\": 18, \"width\": 877, \"height\": 420}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-019.webp\", \"caption\": \"\", \"page\": 5, \"index\": 19, \"width\": 894, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-020.webp\", \"caption\": \"\", \"page\": 5, \"index\": 20, \"width\": 837, \"height\": 470}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-021.webp\", \"caption\": \"\", \"page\": 13, \"index\": 21, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-022.webp\", \"caption\": \"\", \"page\": 13, \"index\": 22, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-023.webp\", \"caption\": \"\", \"page\": 13, \"index\": 23, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-024.webp\", \"caption\": \"\", \"page\": 13, \"index\": 24, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-025.webp\", \"caption\": \"\", \"page\": 13, \"index\": 25, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-026.webp\", \"caption\": \"\", \"page\": 13, \"index\": 26, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-027.webp\", \"caption\": \"\", \"page\": 13, \"index\": 27, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-028.webp\", \"caption\": \"\", \"page\": 13, \"index\": 28, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-029.webp\", \"caption\": \"\", \"page\": 13, \"index\": 29, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-030.webp\", \"caption\": \"\", \"page\": 13, \"index\": 30, \"width\": 1400, \"height\": 458}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-031.webp\", \"caption\": \"\", \"page\": 13, \"index\": 31, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-032.webp\", \"caption\": \"\", \"page\": 14, \"index\": 32, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-033.webp\", \"caption\": \"\", \"page\": 14, \"index\": 33, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-034.webp\", \"caption\": \"\", \"page\": 14, \"index\": 34, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-035.webp\", \"caption\": \"\", \"page\": 14, \"index\": 35, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-036.webp\", \"caption\": \"\", \"page\": 14, \"index\": 36, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-037.webp\", \"caption\": \"\", \"page\": 14, \"index\": 37, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-a12340286b5c3cc50508ed7a/fig-038.webp\", \"caption\": \"\", \"page\": 14, \"index\": 38, \"width\": 640, \"height\": 480}]"
motivation: 长视距机器人操纵中现有视频MLLM只能被动观察，难以监督当前状态相对目标的进展。
method: 利用基于结果的强化学习激励思维链推理，并构建任务阶段锚定的结构化时序输入。
result: PRIMO R1将MLLM转化为积极评价者，提升了长视距操纵的进程判断能力。
conclusion: 用显式推理奖励将被动观察转为主动批评，增强机器人操纵的过程监督。
---

## Abstract
Accurate process supervision remains a critical challenge forlong-horizon robotic manipulation. A primary bottleneck is that currentvideo MLLMs, trained primarily under a Supervised Fine-Tuning (SFT)paradigm, function as passive “Observers” that recognize ongoing eventsrather than evaluating the current state relative to the final task goal.In this paper, we introduce PRIMO R1 (Process Reasoning InducedMOnitoring), a 7B framework that transforms video MLLMs into ac-tive “Critics”. We leverage outcome-based Reinforcement Learning to in-centivize explicit Chain-of-Thought generation for progress estimation.Furthermore, our architecture constructs a structured temporal inputby explicitly anchoring the video sequence between initial and currentstate images. Supported by the proposed PRIMO Dataset and Bench-mark, extensive experiments across diverse in-domain environments andout-of-domain real-world humanoid scenarios demonstrate that PRIMOR1 achieves state-of-the-art performance. Quantitatively, our 7B modelachieves a 50% reduction in the mean absolute error of specialized rea-soning baselines, demonstrating significant relative accuracy improve-ments over 72B-scale general MLLMs. Furthermore, PRIMO R1 exhibitsstrong zero-shot generalization on difficult failure detection tasks. Weestablish state-of-the-art performance on the RoboFail benchmark with67.0% accuracy, surpassing closed-source models like OpenAI o1 6.0%.The project website is: 10-oasis-01.github.io/primo-r1-website.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of an academic paper about PRIMO R1, which is a framework for robotic manipulation process reasoning. Let me analyze the paper carefully and structure the summary according to the 8 requested points.

Let me go through the paper systematically:

1. **Core Problem & Motivation**: The paper addresses the challenge of accurate process supervision for long-horizon robotic manipulation. Current video MLLMs under SFT paradigm are passive "Observers" - they recognize events but don't evaluate progress toward goals.

2. **Methodology**: 
   - PRIMO R1 (Process Reasoning Induced MOnitoring), a 7B framework
   - Transforms video MLLMs into active "Critics"
   - Uses outcome-based Reinforcement Learning (specifically GRPO - Group Relative Policy Optimization)
   - Incentivizes explicit Chain-of-Thought generation
   - Structured temporal input: video sequence anchored between initial state image and current state image
   - Input: I_init (initial state), V_seq (process video), I_curr (current state), L (language instruction)
   - Output: progress score y in [0, 100]
   - Reward design: format reward (rfmt) + accuracy reward (racc)
   - racc = max(0, 1 - | - y_gt|/R_max)
   - GRPO objective with KL divergence penalty

3. **Experiments**:
   - Datasets: PRIMO Dataset (SFT: 116k, RL: 182k)
     - Sources: AgiBot (real-world), BEHAVIOR-1k, RoboTwin (simulations)
     - Additional: EgoPlan, RoboVQA, ShareRobot, STAR, NExT-QA, Perception Test for diversity
   - Benchmark: PRIMO Bench
     - In-Domain (Same Task): BEHAVIOR, AgiBot, RoboTwin (3,000 each)
     - Out-of-Domain (Cross-Task, Cross-Environment): BEHAVIOR, AgiBot, RoboTwin, Real Humanoid (Leju KUAVO-MY)
   - Metrics: MRA (Mean Relative Accuracy), MAE (Mean Absolute Error)
   - Baselines: GPT-5 mini, GPT-4o, Gemini 2.5 Flash, Claude-Haiku-4.5, Qwen2.5-VL-7B/72B, InternVL 3.5 8B, ProgressLM-3B-RL, Video R1 7B, Robobrain 7B, Cosmos-Reasoning 7B, VLAC, GVL, Robo-Dopamine-3B/4B, ProgressLM
   - Also tested on RoboFail benchmark

4. **Resources**: The paper mentions "Detailed experimental setups, including hardware specifications, training parameters, and inference configurations like sampled frame count and frame resolution, are provided in Appendix H." So most details are in the appendix, not the main paper.

5. **Experiment Volume**:
   - Main results table (Table 1) across 4 environments
   - Ablation study on generalization (Table 2): Base, SFT-only, RL-only, SFT+RL
   - Failure detection on RoboFail (Table 3)
   - Ablation on input modalities (Table 4)
   - Fine-grained error analysis (Figure 4)
   - Continuous progress estimation case study (Figure 5)
   - Qualitative comparison of reasoning (Figure 6)

6. **Main Conclusions**:
   - Achieves SOTA: MRA 82.90, MAE 15.52
   - 7B model outperforms 72B-scale general MLLMs by +9.10 MRA
   - 50% MAE reduction vs specialized reasoning baselines
   - 67.0% accuracy on RoboFail, surpassing GPT-4o (63.0%), OpenAI o1 (61.0%), Cosmos-Reason1-56B (66.2%)
   - SFT memorizes, RL generalizes
   - Progress reasoning intrinsically enables failure detection

7. **Strengths**:
   - Clear conceptual framework (Observer → Critic)
   - Innovative combination of GRPO + structured temporal anchoring
   - Comprehensive benchmark with both ID and OOD evaluation
   - Strong empirical results across multiple environments
   - Demonstrates emergent capabilities for failure detection

8. **Limitations**:
   - Relies on simulated data mostly (only one real-world humanoid)
   - Computationally expensive due to GRPO with multiple samples
   - Performance on Real Humanoid OOD is significantly lower than ID (72.32 vs 87+)
   - SFT phase still requires CoT annotations
   - Limited discussion of inference latency for real-time applications
   - The "Real Humanoid" is only one robot platform (Leju KUAVO-MY)
   - Note: paper text references Mingyu Ding as author but metadata doesn't include them, while actual author list in PDF doesn't include Mingyu Ding but metadata does - some inconsistency

Let me write this up in Markdown format in Chinese.</think>

# 论文总结：PRIMO R1 —— 从被动观察者到积极评价者

## 一、核心问题与研究动机

- **关键瓶颈**：长视距机器人操纵中的过程监督（process supervision）精度不足。当前主流视频多模态大模型（MLLM）大多基于监督微调（SFT）范式训练，本质上是"被动观察者（Observer）"——能够识别和描述正在发生的事件，但**无法定量评估当前状态距离最终任务目标还差多远**。
- **深层缺陷**：
  - 缺乏显式的时间边界锚定（temporal boundary anchoring）；
  - 缺乏连续的推理通路（continuous reasoning pathway）；
  - 因此容易对失败轨迹给出高分（视觉上"像"成功的运动），对未见物体泛化能力差，且无法解释预测依据。
- **核心主张**：可靠的奖励模型必须从"观察者"演化为**"评价者（Critic）"**，即具备显式过程推理能力、能定量对齐"当前状态—目标状态"差距的判别模型。

## 二、方法论

### 1. 任务形式化
- 输入四元组：初始状态图像 `I_init`、过程视频序列 `V_seq = {v1,...,v_T}`、当前状态图像 `I_curr`、语言指令 `L`。
- 输出：标量进度估计 `y ∈ [0, 100]`（0=初始，100=完成）。
- 核心映射函数 `F(I_init, V_seq, I_curr, L) → y`。

### 2. 关键设计：结构化时间输入
- 将视频序列显式锚定在 `I_init` 与 `I_curr` 两张状态图像之间；
- 提供清晰的视觉边界条件，把"通用时序感知"转化为"结构化状态对齐验证"。

### 3. 训练范式：SFT + GRPO 两阶段
- **SFT 阶段**：在 116k 含思维链（CoT）标注的样本（PRIMO-R1-CoT-116k）上学习结构化输出格式；
- **RL 阶段**：在 182k 样本（PRIMO-R1-182k）上使用 **Group Relative Policy Optimization (GRPO)** 进行基于结果的强化学习。

### 4. GRPO 优化核心
- **组采样与优势估计**：对同一任务采样 G 个输出 `{o_1, ..., o_G}`，通过组内奖励统计量估计基线：
  $$A_i = \frac{r_i - \text{mean}(r_1,\ldots,r_G)}{\text{std}(r_1,\ldots,r_G) + \epsilon}$$
- **规则化复合奖励**：
  - 格式奖励 `r_fmt`：仅当严格遵循 `<think>...</think><answer>...</answer>` 结构时给正分；
  - 精度奖励 `r_acc`：连续线性衰减，`r_acc = max(0, 1 - |ŷ - y_gt| / R_max)`，`R_max = 100`。
- **GRPO 目标函数**：
  $$\mathcal{L}_{\text{GRPO}}(\theta) = -\frac{1}{G}\sum_{i=1}^{G}\left[\min(\rho_i A_i, \text{clip}(\rho_i, 1-\epsilon, 1+\epsilon)A_i) - \beta \cdot D_{\text{KL}}(\pi_\theta \| \pi_{\text{ref}})\right]$$
- 优势：相比 PPO 不需要单独训练价值网络，节省显存，适合视频 MLLM 训练。

### 5. 推理时生成的 CoT 结构
- **Planning**：将高层语义目标分解为线性执行步骤；
- **Observation**：从连续视频中抽取动态变量、部件级状态变化；
- **Reasoning**：将视觉原语对照执行拓扑做状态对齐，输出量化进度。

## 三、实验设计

### 1. 数据集（PRIMO Dataset）
- **SFT 数据（116k）**：AgiBot（18.3k）、BEHAVIOR-1k（20k）、RoboTwin（22.4k），并补充 EgoPlan、RoboVQA、ShareRobot、STAR、NExT-QA、Perception Test 等通用视频推理数据以增强多样性。
- **RL 数据（182k）**：BEHAVIOR（60k）、AgiBot（38.5k）、RoboTwin（45.4k）、RoboVQA、ShareRobot。
- 数据标注含细粒度进度标签与 CoT 推理路径。

### 2. Benchmark（PRIMO Bench）
- **In-Domain (ID) - Same Task**：BEHAVIOR / AgiBot / RoboTwin 各 3000 条；
- **Out-of-Domain (OOD) - Cross-Task & Cross-Environment**：
  - Cross-Task：BEHAVIOR / AgiBot / RoboTwin 各 3000 条；
  - Cross-Environment：真实人形机器人 Leju KUAVO-MY 遥操作采集的 4791 条真实轨迹（工厂、服务场景等非结构化环境）。
- **第三方评测**：RoboFail 基准（failure detection 零样本泛化测试）。

### 3. 评估指标
- **MRA（Mean Relative Accuracy）**：在多个阈值下"相对误差 < 1-τ"的比例均值；
- **MAE（Mean Absolute Error）**：绝对预测误差均值；
- 此外还在 RoboFail 上使用准确率（%）。

### 4. 对比方法（覆盖全面）
- **闭源通用大模型**：GPT-5 mini、GPT-4o、Gemini 2.5 Flash、Claude-Haiku-4.5；
- **开源通用 MLLM**：Qwen2.5-VL-7B / 72B、InternVL 3.5-8B；
- **推理与视频 MLLM**：ProgressLM-3B-RL、Video R1-7B、RoboBrain-7B、Cosmos-Reasoning-7B；
- **专用进度/奖励模型**：VLAC、GVL、Robo-Dopamine-3B/4B、ProgressLM。

## 四、资源与算力

- 论文主文未给出具体 GPU 型号、数量、训练时长等算力信息；
- 仅在第 4 节末尾说明"详细实验设置（硬件规格、训练参数、采样帧数、分辨率等）请见 **Appendix H**"；
- 基础模型为 **Qwen2.5-VL-7B-Instruct**，所有训练阶段均基于该 7B backbone；
- 因此**算力细节不可从主文评估**，需结合附录确认。

## 五、实验数量与充分性

- **实验规模**：
  - Table 1：主结果对比，覆盖 4 个环境、3 类模型族（闭源 / 开源通用 / 专用）；
  - Table 2：消融 Base / SFT / RL / SFT+RL 在 ID vs OOD 的表现；
  - Table 3：RoboFail 零样本 failure detection 对比；
  - Table 4：输入模态消融（6 种组合）；
  - Figure 4：分区间 MAE 细粒度分析（5 个进度区间 × 4 个环境）；
  - Figure 5：长视距任务"Clear the countertop waste"连续轨迹进度曲线；
  - Figure 6："Fold shorts" 推理链定性对比。
- **充分性与公平性**：
  - 优点：实验覆盖 ID 与 OOD、仿真与真实、连续估计与离散判别、模型规模横跨 7B~72B、闭源/开源/专用三档对比；
  - 局限：作者承认 ProgressLM 在 Real Humanoid 上因使用"专用输入配置"而结果更优，PRIMO R1 采用统一协议，这一对照"不完全 cell-by-cell 公平"，作者通过平均性能与跨环境结果进行补救；
  - 整体实验设计较为系统，但**没有公开算力、训练时长、推理延迟细节**（仅指向附录），影响可复现性评估。

## 六、主要结论与发现

1. **综合性能 SOTA**：在 PRIMO Bench 四个环境上 PRIMO R1（7B）取得平均 MRA=82.90、MAE=15.52，超过所有评估基线；
2. **小模型超越大模型**：7B 模型比 Qwen2.5-VL-72B 高 9.10 MRA；
3. **专用基线大幅缩短**：相对专用推理基线，MAE 降低约 50%（15.52 vs 27~29）；
4. **OOD 鲁棒性显著**：在 Real Humanoid OOD 上取得 72.32 MRA，远超 Qwen2.5-VL-7B 的 56.46；
5. **SFT 与 RL 的协同机制**：
   - SFT 单独使用在 ID 表现良好，但易对训练分布过拟合，OOD 掉到 67.30；
   - RL 单独使用缺乏格式先验，平均 MRA 仅 76.72；
   - SFT + RL 联合达到最佳，平均 MRA=85.28，ID 与 OOD 同时提升；
6. **涌现能力**：优化连续进度推理隐式构造了离散 failure detection 所需的时间上下文表示，RoboFail 上达到 67.0%，超过 GPT-4o（63.0%）、OpenAI o1（61.0%）、Cosmos-Reason1-56B（66.2%），与 Gemini 2.0 Flash 持平；
7. **模态必要性**：三模态联合（I_init + V_seq + I_curr）效果最佳；仅静态帧或仅边界图像均不足。

## 七、优点与亮点

- **概念创新**："Observer → Critic" 的范式跃迁清晰且具说服力，把"过程监督"从被动打分升级为显式因果推理；
- **方法组合精炼**：GRPO + 结构化时间锚定 + 语言条件化，思路简洁但有效；
- **奖励设计实用**：纯规则化（格式 + 连续线性衰减精度），无需 dense 标注即可激发 CoT；
- **Benchmark 设计严谨**：明确划分 ID-SameTask、OOD-CrossTask、OOD-CrossEnvironment，能区分"看到过任务 / 看到过环境"两种泛化；
- **涌现证据扎实**：progress estimation 与 failure detection 的"耦合性"由跨任务、跨环境的定量结果支撑；
- **定性分析深入**：Figure 6 展示的 CoT 三段式（Planning/Observation/Reasoning）使模型决策具备可解释性。

## 八、不足与局限

- **算力与训练细节不透明**：主文未披露 GPU 型号/数量、训练时长、显存占用、GRPO 组大小 G 等关键复现信息；
- **真实数据覆盖偏窄**：Cross-Environment 仅使用 Leju KUAVO-MY 一款人形机器人，且未覆盖光照、遮挡、动态干扰等更复杂的真实场景；
- **OOD 仍存在显著性能落差**：PRIMO R1 在 Real Humanoid 上 MRA=72.32，相比 ID 上的 87+ 仍下降 15+ 点，说明 Sim-to-Real 迁移尚未完全解决；
- **公平比较的折衷**：专用模型使用各自"推荐输入配置"、PRIMO 使用"统一协议"，可能导致专用模型在某些环境下被低估/高估；
- **推理延迟未充分讨论**：CoT 输出会增加推理长度，作者仅在主文末尾提示"详见 Appendix C.2"，对实时机器人控制场景的实用性影响仍不清晰；
- **数据规模与多样性**：尽管 SFT 数据达 116k、RL 数据 182k，但绝大多数来自仿真（AgiBot、BEHAVIOR、RoboTwin），真实世界轨迹仅 4791 条，可能引入 Sim-to-Real 偏差；
- **可解释性 CoT 的可靠性**：CoT 是 RL 间接激励的产物，并非由人工逐步标注强制约束，可能出现"事后合理化"现象，文中未对此做针对性分析；
- **作者列表一致性**：PDF 主文未将 Mingyu Ding 列入作者，但元数据补全为作者之一，存在署名差异。

（完）
