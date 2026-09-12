---
title: Scaling Verification Can Be More Effective than Scaling Policy Learning for Vision-Language-Action Alignment
title_zh: 扩展验证比扩展策略学习对视觉-语言-动作对齐更有效
authors: "Jacky Kwok, Xilun Zhang, Mengdi Xu, Yuejiang Liu, Azalia Mirhoseini, Chelsea Finn, Marco Pavone"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/11946.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用机器人的VLA模型，研究具身指令跟随的测试时扩展
tldr: 通用机器人需要理解和执行自然语言指令，但现有视觉-语言-动作模型生成的指令与动作仍存在意图-动作差距。本文研究测试时验证作为缩小差距的手段，首先刻画具身指令跟随的测试时扩展规律，证明联合扩展复述指令与生成动作的样本数量可以显著增加测试时多样性，往往比单独扩展某一项更高效地恢复正确动作。该工作直接服务于通用VLA模型在机器人指令跟随任务中的对齐与可靠性提升，为基于视觉-动作映射的通用机器人策略提供了重要的可扩展方法支撑。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1714, \"height\": 953}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 1897, \"height\": 1058}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 804, \"height\": 581}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 930, \"height\": 507}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 1860, \"height\": 1078}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 1669, \"height\": 1020}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 768, \"height\": 768}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-012.webp\", \"caption\": \"\", \"page\": 1, \"index\": 12, \"width\": 1263, \"height\": 1177}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-013.webp\", \"caption\": \"\", \"page\": 3, \"index\": 13, \"width\": 800, \"height\": 1280}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-014.webp\", \"caption\": \"\", \"page\": 3, \"index\": 14, \"width\": 1415, \"height\": 1161}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-015.webp\", \"caption\": \"\", \"page\": 3, \"index\": 15, \"width\": 669, \"height\": 360}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-016.webp\", \"caption\": \"\", \"page\": 3, \"index\": 16, \"width\": 1200, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-017.webp\", \"caption\": \"\", \"page\": 3, \"index\": 17, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-018.webp\", \"caption\": \"\", \"page\": 8, \"index\": 18, \"width\": 431, \"height\": 365}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-019.webp\", \"caption\": \"\", \"page\": 8, \"index\": 19, \"width\": 496, \"height\": 485}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-020.webp\", \"caption\": \"\", \"page\": 11, \"index\": 20, \"width\": 2048, \"height\": 1414}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-021.webp\", \"caption\": \"\", \"page\": 11, \"index\": 21, \"width\": 2048, \"height\": 1281}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-022.webp\", \"caption\": \"\", \"page\": 11, \"index\": 22, \"width\": 2048, \"height\": 1538}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-023.webp\", \"caption\": \"\", \"page\": 11, \"index\": 23, \"width\": 2048, \"height\": 1361}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-024.webp\", \"caption\": \"\", \"page\": 11, \"index\": 24, \"width\": 2048, \"height\": 1286}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-025.webp\", \"caption\": \"\", \"page\": 11, \"index\": 25, \"width\": 2048, \"height\": 1289}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-026.webp\", \"caption\": \"\", \"page\": 11, \"index\": 26, \"width\": 2048, \"height\": 1327}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-027.webp\", \"caption\": \"\", \"page\": 11, \"index\": 27, \"width\": 2048, \"height\": 1395}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-028.webp\", \"caption\": \"\", \"page\": 11, \"index\": 28, \"width\": 2048, \"height\": 1368}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-d23502df44aa3c2f04df06c6/fig-029.webp\", \"caption\": \"\", \"page\": 11, \"index\": 29, \"width\": 2048, \"height\": 1368}]"
motivation: VLA模型生成的指令与动作存在意图-动作差距，需要缩小差距以提升通用机器人的指令跟随能力。
method: 研究测试时验证与扩展规律，通过联合扩展复述指令和生成动作来增加样本多样性。
result: 联合扩展比单独扩展策略学习或验证更高效地恢复正确动作。
conclusion: 测试时验证是缩小VLA模型意图-动作差距并提升通用机器人性能的有效手段。
---

## Abstract
The long-standing vision of general-purpose robots hinges on theirability to understand and act upon natural language instructions. Vision-Language-Action (VLA) models have made remarkable progress toward thisgoal, yet their generated actions can still misalign with the given instructions.In this paper, we investigate test-time verification as a means to shrinkthe “intention-action gap.” We first characterize the test-time scaling lawsfor embodied instruction following and demonstrate that jointly scaling thenumber of rephrased instructions and generated actions greatly increasestest-time sample diversity, often recovering correct actions more efficientlythan scaling each dimension independently. To capitalize on these scalinglaws, we present CoVer, a contrastive verifier for vision–language–actionalignment, and show that our architecture scales gracefully with additionalcomputational resources and data. We then introduce CoVer-VLA, a hierar-chical test-time verification pipeline using the trained verifier. At deployment,our framework precomputes a diverse set of rephrased instructions from aVision-Language-Model (VLM), repeatedly generates action candidates foreach instruction, and then uses the verifier to select the optimal high-levelprompt and low-level action chunks. Compared to scaling policy pre-training⋆ †Equal contribution. § Equal advising.on the same data, our verification approach yields 22% gains in-distributionand 13% out-of-distribution on the SIMPLER benchmark, with a further45% improvement in real-world experiments. On the PolaRiS benchmark,CoVer-VLA achieves 14% gains in task progress and 9% in success rate.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze this paper in detail and produce a structured Chinese summary. Let me carefully read through the paper content and organize my response according to the 8 requested points.

The paper is about "Scaling Verification Can Be More Effective than Scaling Policy Learning for Vision-Language-Action Alignment" - it's about CoVer-VLA, a contrastive verifier for VLA models.

Let me organize my analysis:

1. Core problem: The "intention-action gap" in VLA models where generated actions misalign with natural language instructions. Existing work focuses on scaling policy pre-training which has issues like catastrophic forgetting.

2. Method: 
- Characterizes test-time scaling laws for embodied instruction following
- Presents CoVer (Contrastive Verifier) using SigLIP2 encoders + action transformer
- Uses bidirectional InfoNCE loss
- Two-stage training: rephrase augmentation + contrastive learning
- CoVer-VLA hierarchical test-time verification pipeline
- Boot-time reasoning (VLM precomputes rephrases)
- Batched action proposals for efficient search

3. Experiments:
- Datasets: SIMPLER benchmark (4 ID tasks, 3 OOD tasks), PolaRiS benchmark, real-world WidowX robot
- Baselines: π0, π0(rephrase), RoboMonkey, π0+CoVer, π0+Rand.Reph., π0(rephrase)+CoVer
- Evaluation under ERT red-teaming instructions

4. Resources:
- 1B parameter CoVer verifier
- Trained with batch size 32,768 on augmented Bridge V2 (16× synthetic instructions)
- 2k steps using 8 NVIDIA H200 GPUs
- 20 million offline samples
- Inference on RTX-5090 GPU

5. Experimental quantity:
- Verifier scaling studies (5 dimensions)
- SIMPLER evaluation (ID + OOD)
- PolaRiS evaluation
- Real-world experiments (2 tasks)
- Iso-compute comparison
- Latency analysis

6. Main conclusions:
- Verification > policy scaling at matched compute
- Hybrid rephrasing + sampling is most effective
- 22% ID, 13% OOD gains on SIMPLER
- 14% task progress, 9% success rate on PolaRiS
- 45% absolute improvement in real-world

7. Strengths:
- Novel hierarchical framework
- Boot-time reasoning for latency reduction
- Graceful scaling across multiple dimensions
- Comprehensive evaluation including real-world
- Open-source friendly (no need to access VLA internals)

8. Limitations:
- High latency (only 2.2 Hz vs competing 1.5 Hz)
- Base policy proposal quality is the bottleneck
- Positive-only demonstrations - no failure data
- Long-horizon tasks still have low absolute success rates

Let me write this out in Chinese Markdown format.</think>

# 论文总结：CoVer-VLA —— 扩展验证比扩展策略学习对视觉-语言-动作对齐更有效

## 1. 核心问题与研究背景

- **核心问题**：通用机器人要理解和执行自然语言指令，依赖视觉-语言-动作（VLA）模型。然而，VLA 模型生成的"动作"与给定的"指令意图"之间存在显著的 **"意图-动作差距"（intention-action gap）**，即语义等价的复述可能导致完全不同的动作输出，从而在真实部署中造成灾难性错误（如把塑料容器放进烤箱）。
- **现有方法的不足**：
  - 主流方法侧重**扩展策略预训练**（如训练时加入指令复述数据、使用更大的 VLM 主干），但收益有限，且对小的语义扰动仍非常脆弱。
  - 扩展策略预训练还会引发**灾难性遗忘**，削弱 VLM 本身的多模态理解与推理能力。
- **本文主张**：与其继续扩展策略预训练，不如转向**测试时扩展**（test-time scaling），让 VLA 在推理时利用额外算力对齐指令与动作。

---

## 2. 方法论

### 2.1 核心思想
将测试时推理转化为一个**层次化验证问题**：
- **高层（语言层）**：在多个由 VLM 生成的语义等价复述中，挑选能产生最可靠动作分布的指令；
- **低层（动作层）**：在选定指令下，对多个候选动作块打分，选出与意图最对齐的动作。

### 2.2 关键技术

**(1) 测试时扩展规律刻画**（Section 3）
- 在 Bridge V2 上采样 1000 个 (s, a, I) 元组，比较四种采样策略：重复采样、高斯扰动、指令复采样、混合采样。
- 关键发现：
  - **指令复述**比单纯重复采样和高斯扰动产生更低动作误差；
  - **混合采样**（多个复述 × 每个复述多个动作）效果最佳，动作误差与候选数 k 服从幂律：log(e) ≈ log(a) + b·log(k)。

**(2) CoVer 对比验证器**（Section 4.2）
- **架构**：
  - 文本感知视觉编码器：基于冻结的 SigLIP2，通过 text-aware 注意力抽取任务相关特征；
  - 动作编码器：Transformer 编码短期历史 + 未来动作块，捕获长程时间依赖；
  - 三者投影到统一嵌入空间。
- **训练两阶段**：
  - **阶段一**：用 Open-X-Embodiment 的同义复述集 I(l) 对原始指令做**语言扩展**，不改变动作（避免伪造失败轨迹）；
  - **阶段二**：双向 InfoNCE 损失，把同 batch 内其它样本视为隐式负例，无需显式失败标注。
- **训练规模**：1B 参数、batch size 32768、20M 离线样本、训练 2k 步、8 张 H200 GPU。

**(3) CoVer-VLA 层次化推理流水线**（Section 4.3）
- **Boot-time 推理**：部署前由 VLM（如 GPT-4o，约 11s 生成 8 条复述）对初始场景做结构化推理，预计算并缓存复述嵌入，避免在线生成。
- **Batched 候选生成**：对 K 条复述 × M 个动作，组成 K×M 个候选。
- **打分与选择**：
  - 先对每个复述下 M 个动作分数取均值，挑出最优复述 l′*；
  - 再在该复述下挑得分最高的动作块 a′* 作为执行；
  - 每个 chunk 边界重新执行，形成闭环。

---

## 3. 实验设计

### 3.1 数据集与场景
- **模拟环境**：
  - **SIMPLER** 基准：4 个分布内（ID）任务（Carrot on Plate、Eggplant in Basket、Spoon on Towel、Block Stacking）；
  - **3 个 OOD 任务**（来自 Interleave-VLA）：Redbull on Plate、Zucchini on Towel、Tennis in Basket，包含同类干扰物（如红牛 vs 可口可乐、西葫芦 vs 胡萝卜、网球 vs 乒乓球）。
- **PolaRiS 基准**：PanClean、BlockStack、FoodBussing 3 个长视野任务。
- **真实环境**：WidowX 机器人上 2 个任务（pepto bismol on plate、redbull on plate）。
- **训练数据**：Bridge V2 + 16× 合成指令扩展；测试在 DROID 与 Bridge 风格场景上。
- **指令扰动**：统一使用 ERT（Embodied Red Teaming）生成的对抗性指令。

### 3.2 对比方法
以 π0（或 π0.5）为基座模型，比较 6 种变体：
1. π0：基线；
2. π0(rephrase)：在指令增强数据上微调；
3. **RoboMonkey**：7B 验证器 + 动作重采样；
4. π0+CoVer：仅加入本文测试时验证；
5. π0+Rand.Reph.：仅随机挑一条复述，不验证；
6. π0(rephrase)+CoVer：策略扩展 + 测试时验证的组合。

---

## 4. 资源与算力

| 项目 | 配置 |
|------|------|
| CoVer 参数量 | 1B |
| 训练 batch size | 32,768 |
| 训练数据 | 2000 万离线样本（Bridge V2 + 16× 合成指令） |
| 训练步数 | 2k 步 |
| 训练 GPU | 8 × NVIDIA **H200** |
| 推理 GPU | 单卡 **RTX-5090** |
| Boot-time 推理 | GPT-4o，约 11s/episode 生成 8 条复述 |
| 推理速度 | 16 候选约 453 ms（≈2.2 Hz），加上 boot-time 摊销约 **1.85 Hz**（优于 RoboMonkey 的 1.5 Hz） |

---

## 5. 实验数量与充分性

- **验证器扩展实验**（Section 5.1）：在 5 个维度上独立扫描——模型规模（250M→1B）、数据规模（8×→64×）、batch size（2k→8k）、训练 epoch、集成大小（1→8）。
- **模拟实验**：SIMPLER 4 ID + 3 OOD 任务（7 项），PolaRiS 3 任务 × 50 episodes × 3 seeds（150 回合/任务）。
- **真实实验**：2 个 WidowX 任务。
- **等算力对比**（Table 2）：在 K=4、8 下对比 temperature sampling、Best-of-N 与 CoVer。
- **延迟分析**（Table 3）：不同 batch size 下的 π0.5、CoVer、端到端延迟。

**客观性评价**：
- 基线覆盖较全面（包括当前最强 RoboMonkey 与训练时增强基线）；
- 多次随机种子、报告 mean ± std；
- OOD 任务中特意放入同类干扰物，避免场景识别捷径。
- 但总体而言，长视野任务绝对成功率仍偏低（BlockStack 仅 0.7%），凸显基座策略的瓶颈。

---

## 6. 主要结论与发现

1. **测试时验证 > 训练时扩展**：在相同数据预算下，π0+CoVer 比 π0(rephrase) 在 ID 上高 15%、OOD 上高 12%，且所需训练算力大幅减少。
2. **混合采样最优**：联合扩展复述数 K 与每复述动作数 M 比单独扩展任一项更高效。
3. **验证器可被多维扩展**：合成指令量、模型参数、负样本数、训练 epoch、集成规模均带来稳定提升。
4. **大规模实验结果**：
   - SIMPLER：**ID +22%、OOD +13%**；
   - PolaRiS：**任务进度 +14%、成功率 +9%**；
   - 真实 WidowX 任务：**绝对成功率 +45%**（如 0% → 50%、10% → 70%）。
5. **等算力下优势显著**：在 K=8、匹配 FLOPs 时，CoVer 比 temperature sampling 高 +43%、比 Best-of-N 高 +27%。
6. **鲁棒性来源**：CoVer 学习到的是细粒度的指令-动作对齐，而非粗粒度的场景识别（在含同类干扰物的 OOD 上仍能 +31%）。

---

## 7. 优点与亮点

- **方法新颖**：首次将测试时验证显式分解为"高层指令优化 + 低层动作验证"，并用对比学习统一表征。
- **零样本验证**：CoVer 无需访问基座 VLA 的内部参数（plug-and-play），可在任意 chunk-based VLA 上使用。
- **Boot-time 缓存**：将 VLM 推理搬到部署前，有效摊销推理延迟（端到端仍 ~1.85 Hz）。
- **扩展性证据充分**：从模型规模、负样本、训练 epoch、集成、数据量五个角度均给出幂律/单调提升。
- **实证丰富**：覆盖 ID、OOD、长视野、真实机器人，且与当前 SOTA RoboMonkey 直接比较。
- **训练策略稳健**：用 in-batch 隐式负例避免伪造失败轨迹，工程上简洁可复现。

---

## 8. 不足与局限

- **基座策略仍是天花板**：若候选动作中无可行解，验证器无法恢复（如 BlockStack 成功率近 0）。
- **绝对成功率仍偏低**：PolaRiS 的 BlockStack、FoodBussing 上 π0.5+CoVer 仅 0.7%/5.3%，长视野任务需进一步结合动力学验证器。
- **训练时正样本 only**：仅靠 in-batch 隐式负例，未引入真实失败/近失败轨迹，可能错过细粒度边界；作者把显式失败注入留作未来工作。
- **依赖外部 VLM 做复述**：需 GPT-4o 等强 VLM，11s/episode 的 boot-time 仍是不可忽略开销，且 VLM 复述本身有噪声（随机复述实验方差大）。
- **离线数据规模有限**：尽管 20M 样本与 16× 扩展，但与真正 web-scale 多模态数据相比仍偏小；通用性可能受 Bridge V2 风格影响。
- **推理频率受限**：~1.85 Hz 对需要高速反应的任务（如接触丰富操作）可能仍不够快。
- **计算预算未充分披露**：基线（如 RoboMonkey）的完整训练-推理 FLOPs 对比只在 Figure 2 中给出概述，缺少精确数字。
- **评估指令分布偏单一**：仅使用 ERT 风格的对抗性复述，未覆盖嘈杂、口语化或多步指令等其他真实分布漂移。

（完）
