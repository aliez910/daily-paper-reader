---
title: "Metric-Bench: Exploring In-context Spatial Metric Reasoning in VLMs for Indoor Scenes"
title_zh: Metric-Bench：探索视觉语言模型在室内场景中的上下文空间度量推理
authors: "Yuling Xi, Haokai Zhang, Muzhi Zhu, Hao Zhong, Zongze Du, Hengyu Zhao, Chenchen Jing, Yufei Yin, Bin Qin, Yongjie Yang, Zhenbo Luo, Hao Chen, Chunhua Shen"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/5753.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向机器人操控的空间度量推理基准测试
tldr: 针对现有视觉语言模型在空间度量推理上的瓶颈，本文提出聚焦的基准Metric-Bench。该方法通过图像内已知尺寸的参考物体，引导模型进行上下文度量推理，学习2D到3D映射，服务于机器人操控等具身AI任务。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 515, \"height\": 406}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 654, \"height\": 529}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 365, \"height\": 479}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 308, \"height\": 495}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 996, \"height\": 746}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 1288, \"height\": 688}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 417, \"height\": 417}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 500, \"height\": 500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-009.webp\", \"caption\": \"\", \"page\": 5, \"index\": 9, \"width\": 530, \"height\": 228}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-010.webp\", \"caption\": \"\", \"page\": 5, \"index\": 10, \"width\": 544, \"height\": 232}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 546, \"height\": 233}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 719, \"height\": 349}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-013.webp\", \"caption\": \"\", \"page\": 5, \"index\": 13, \"width\": 508, \"height\": 535}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-014.webp\", \"caption\": \"\", \"page\": 5, \"index\": 14, \"width\": 330, \"height\": 404}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-015.webp\", \"caption\": \"\", \"page\": 10, \"index\": 15, \"width\": 3564, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-016.webp\", \"caption\": \"\", \"page\": 23, \"index\": 16, \"width\": 609, \"height\": 454}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-017.webp\", \"caption\": \"\", \"page\": 23, \"index\": 17, \"width\": 624, \"height\": 312}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-45a67b67d7c2fca865584944/fig-018.webp\", \"caption\": \"\", \"page\": 23, \"index\": 18, \"width\": 605, \"height\": 341}]"
motivation: 现有空间推理受限于像素级监督，易导致多模态能力的灾难性遗忘。
method: 利用图像内已知尺寸参考物体构建上下文度量推理基准。
result: 为VLM在操控与导航中的空间推理能力提供了系统化评测工具。
conclusion: 该基准有助于推动VLM在具身任务中的度量推理研究。
---

## Abstract
Metric reasoning is a critical and challenging task for VisionLanguage Models (VLMs), playing a pivotal role in embodied AI taskssuch as robotic manipulation and autonomous navigation. However, cur-rent spatial reasoning remains bottlenecked by rigid pixel-level supervi-sion; such localized optimization often compromises general multimodalintelligence, triggering performance degradation or catastrophic forget-ting of broad reasoning capabilities. To address these limitations, weintroduce Metric-Bench, a focused benchmark designed to guide metric-spatial reasoning using contextual information. By incorporating in-imagereference objects with known physical dimensions, Metric-Bench guidesmodels to implicitly learn the 2D-to-3D mapping without camera in-trinsics. We further present MetricReasoner, a task-adapted reinforce-ment fine-tuning recipe for reference-grounded metric reasoning, usingstructured prompts and verifiable numerical rewards. Extensive experi-ments on Metric-Bench demonstrate that our approach significantly en-hances spatial metric understanding, outperforming existing and evenlarger proprietary models by 43.1%, while improving downstream em-bodied performance over a spatial-specialized counterpart by 30.4% onRoboSpatial overall accuracy and 9.3% on ERQA, and additionally deliv-ering consistent gains on general benchmarks (15.9% on V⋆Bench, 88.9%on BLINK), indicating that the proposed adaptation does not necessarilycompromise general VLM capabilities.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Metric-Bench: Exploring In-context Spatial Metric Reasoning in VLMs for Indoor Scenes". I need to follow the structured outline provided and use Markdown formatting. Let me carefully analyze the paper content to extract all relevant information.

Key information from the paper:
- Core problem: VLMs struggle with metric reasoning (inferring real-world sizes/distances from images), while excelling at semantic reasoning. Current spatial reasoning approaches use rigid pixel-level supervision which can cause catastrophic forgetting.
- Method: 
  1. Metric-Bench: A benchmark built on ScanNetV2 with 1340 QA pairs across 5 spatial categories (size, position, depth, distance, 3D bounding box)
  2. Uses in-image reference objects with known physical dimensions
  3. MetricReasoner: Reinforcement fine-tuning with structured prompts and verifiable rewards
  4. Three reward components: Format reward, Exponential Precision (EP) reward, Binned Proximity (BP) reward
  5. Uses GRPO (Group Relative Policy Optimization)
- Datasets: Metric-Bench (1340 test samples), RoboSpatial, ERQA, CountBench, V*Bench, BLINK, Q-Spatial++
- Comparison: 15 VLMs including GPT-5-mini, Gemini-2.5-Flash, InternVL3.5 series, Qwen2.5-VL, Qwen3-VL, LLaVA-OneVision, VST, SpaceR
- Resources: 4 H100 GPUs, batch size 128, group size 32, learning rate 2e-6, 3 epochs, ~12 hours training
- Main results: MetricReasoner achieves 48.59 MRA, outperforming baselines by 43.1%
- Improvements on downstream: 30.4% on RoboSpatial, 9.3% on ERQA, 15.9% on V*Bench, 88.9% on BLINK

Let me organize this into the required structure.</think>

# Metric-Bench 论文总结

## 1. 核心问题与研究背景

- **关键能力缺失**：当前视觉语言模型（VLM）在语义理解和指令跟随上表现出色，但在**度量尺度推理**（metric reasoning）方面存在显著短板——难以从单目图像中推断物体的真实尺寸、距离、深度等物理量。
- **应用需求**：度量推理是具身 AI 的核心能力，直接影响机器人操控、自主导航等下游任务的可靠性。
- **现有方法的瓶颈**：
  - 传统空间推理依赖**刚性像素级监督**或显式数值回归，导致优化偏向局部特征，损害多模态通用能力；
  - 容易引发**灾难性遗忘**，降低模型在通用视觉-语言任务上的表现；
  - 需要依赖**相机内参**才能恢复度量尺度，限制了跨场景泛化能力。
- **人类启发**：人类可通过已知尺寸的参考物体，结合相对位置与遮挡线索进行度量推断，而非死记硬背。本研究旨在让 VLM 具备类似的**上下文度量推理**能力。

---

## 2. 方法论

### 2.1 核心思想

模仿人类"通过参考物体进行相对度量推断"的认知方式，构建一个**参考物体驱动的度量推理基准**，并设计专门的强化微调策略，使 VLM 在不依赖相机内参的情况下学会**隐式的 2D 到 3D 映射**。

### 2.2 关键技术细节

#### （1）Metric-Bench 基准构建

- **数据来源**：基于 ScanNetV2 室内 RGB-D 数据集（含相机内外参与 3D 实例标注）。
- **坐标转换**：将原始世界坐标系下的 3D 标注转换为**相机坐标系**下的度量（中心坐标 (x, y, z)、长/宽/高），使度量推理与人类视觉观察过程一致。
- **三类查询模板**：
  1. **尺寸推断**（size-to-size）：由已知尺寸推断目标尺寸；
  2. **位置/距离推断**（position/distance）：由空间线索推断目标位置或距离；
  3. **混合推理**（hybrid）：综合尺寸与位置/距离线索。
- **数据筛选**：使用 Laplacian 方差去除运动模糊帧；通过相机内参投影保留视场内可见物体。
- **质量控制**：采用 VLM 自动检查 + 人工验证双重协议剔除不可见目标、重复问题或歧义样本。
- **数据划分**：1340 张图像构成 5K 训练样本，134 张图像构成 1340 测试样本；训练/测试场景**完全不重叠**，避免数据泄漏。

#### （2）MetricReasoner 微调策略

- **基础模型**：以 Qwen3-VL-8B 为基座。
- **结构化 Prompt**：包含三部分——3D 基础知识（针孔成像、相机坐标系定义）、推理指导（七步推理链）、输出规范（`<think>...</think><Final answer>...` 格式）。
- **奖励函数设计**（三种奖励相加）：
  - **格式奖励（Format Reward）**：检查输出是否符合指定标签格式；
  - **指数精度奖励（EP, Exponential Precision）**：$R_{EP} = e^{-|\hat{y} - y|}$，误差越大奖励衰减越快；
  - **分箱邻近奖励（BP, Binned Proximity）**：按误差区间离散化打分（误差 < 0.25 得 1 分；< 0.5 得 0.05 分；< 1 得 0.01 分；否则 0 分）。
- **优化算法**：基于 **GRPO**（Group Relative Policy Optimization）进行强化微调，组内归一化优势函数。

---

## 3. 实验设计

### 3.1 数据集与基准

- **自建基准**：Metric-Bench（1340 测试样本，5 类：size、position、depth、distance、3D bounding box）。
- **下游任务基准**：
  - 空间相关：RoboSpatial、ERQA；
  - 通用视觉：CountBench、V\*Bench、BLINK；
  - 零样本评测：Q-Spatial++。
- **人类表现**：在 400 题子集上报告了人类评测分数作为上限参考。

### 3.2 对比方法（共 15 个 VLM）

- **闭源专有模型**：GPT-5-mini、Gemini-2.5-Flash；
- **开源通用模型**：InternVL3.5（1B/4B/8B/14B）、Qwen2.5-VL（7B/32B）、Qwen3-VL（8B/32B）、LLaVA-OneVision（0.5B/7B）；
- **空间专用模型**：VST-7B（RL/SFT 两版本）、SpaceR-7B。

### 3.3 评测指标

- **MRA**（Mean Relative Accuracy，10 个阈值 {0.5, 0.55, ..., 0.95} 下相对误差 < 1−θ 的比例均值）；
- **RMSE**（Root Mean Squared Error）；
- **δ₁**（预测值与真值比值最大者 < 1.25 的比例）。

---

## 4. 资源与算力

- **GPU**：4 块 H100；
- **训练配置**：batch size = 128，group size = 32，学习率 = 2×10⁻⁶；
- **训练时长**：3 个 epoch，约 **12 小时**；
- **实现框架**：基于 GRPO 的强化微调（未提及具体代码库如 Verl、TRL 等）。

---

## 5. 实验数量与充分性

### 5.1 实验规模

- **主结果**：Metric-Bench 全面对比（15 个模型 × 3 个指标 × 5 个类别 = 225+ 数据点）；
- **消融实验**：
  - 参考物体数量消融（0/2/4/5 个参考）；
  - 奖励函数消融（EP / BP 各自及组合，共 4 组）；
  - BP 分箱粒度消融（4/5/6/8 区间）；
- **微调策略对比**：SFT、RL w/ CoT&SFT、纯 RFT 三种策略对比；
- **下游任务验证**：在 ERQA、RoboSpatial、CountBench、V\*Bench、BLINK、Q-Spatial++ 上评测；
- **定性分析**：给出 3 个推理案例（size、box、position）以及在 RoboTwin 2.0 上的零样本可视化。

### 5.2 充分性评价

- **优点**：覆盖了基准、消融、策略对比、跨域迁移、定性可视化等多个维度，实验较为系统。
- **不足**：
  - 训练集仅 5K 样本，测试仅 1340，规模相对较小；
  - 缺乏多基座模型对比（仅在 Qwen3-VL-8B 上做 RFT），不能完全排除基座选择的偶然性；
  - 闭源模型评测样本量（400 题）远小于完整测试集（1340 题），对比公平性受限；
  - 未做多次随机种子实验以报告误差棒，结果稳定性存疑。

---

## 6. 主要结论与发现

- **整体性能**：MetricReasoner 在 Metric-Bench 上 MRA 达到 **48.59**，显著超过所有对比模型（含 GPT-5-mini 的 37.84、Gemini-2.5-Flash 的 33.95）；
- **下游具身任务**：相比空间专用模型 VST-7B-RL，在 RoboSpatial 上提升 **30.4%** 整体准确率，在 ERQA 上提升 **9.3%**；
- **通用能力保持**：在 V\*Bench 上提升 **15.9%**，BLINK 上提升 **88.9%**，CountBench 达到 0.920，证明强化微调**未损害通用推理**；
- **类别差异**：大多数模型在**深度估计**上表现较好，但在**距离估计**上表现最差；
- **参考物体数量**：4 个参考物体达到最优平衡，过多（5 个）反而导致性能下降（信息过载）；
- **奖励贡献**：BP 是主导贡献项，EP 提供细粒度补充；两者结合效果最佳；
- **策略对比**：纯 RFT 优于 SFT 与 CoT-SFT→RFT 两阶段策略，说明 CoT 监督可能与下游奖励目标不一致。

---

## 7. 优点

- **任务设计新颖**：首次提出"参考物体驱动的度量推理"评测范式，无需相机内参，贴近人类认知；
- **基准构建严谨**：采用坐标转换、模糊帧过滤、双重质量控制、场景级划分等多重质量保证；
- **奖励设计精细**：EP + BP 兼顾连续精度与离散邻近度，互补性强；
- **全面性突出**：不仅在专门基准上评估，还验证了在具身任务与通用任务上的迁移能力，证明了方法的"无损"特性；
- **定性分析深入**：提供了完整的 Chain-of-Thought 推理过程展示，可解释性好。

---

## 8. 不足与局限

- **数据集规模偏小**：仅 1340 个测试样本，统计显著性可能受限；
- **基座单一**：仅在 Qwen3-VL-8B 上验证 RFT 策略，缺乏对其他基座（如 InternVL、Qwen2.5-VL）的迁移性验证；
- **闭源模型评测子集偏小**：仅用 400 题与人类对比，可能不能完全反映真实差距；
- **缺乏统计稳健性报告**：未报告多次实验的均值/标准差或显著性检验；
- **场景局限于室内**：数据源为 ScanNetV2，未覆盖室外场景；室外空间几何与光照条件差异较大；
- **奖励设计依赖阈值**：BP 奖励的分箱阈值（如 0.25、0.5、1）属于人为设定，可能不适用于所有度量尺度（如极大或极小目标）；
- **应用限制**：目前仅适用于室内静态场景下的单图推理；视频、动态场景的扩展尚未验证；
- **未讨论失败模式细节**：除定性示例外，缺少对错误案例的系统性分析（如遮挡、相似物体干扰等）。

（完）
