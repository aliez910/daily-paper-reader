---
title: Data Augmentation for Instruction Following Policies via Trajectory Segmentation
title_zh: 通过轨迹分割增强指令跟随策略的训练数据
authors: "Niklas Hoepner, Ilaria Tiddi, Herke van Hoof"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/33892/36047"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向指令跟随策略的数据增强，结合模仿学习训练
tldr: 该论文针对机器人或游戏中指令跟随智能体因指令-轨迹配对数据稀缺而难以规模化训练的问题，提出在半监督设定下从大量未标注游玩轨迹中提取标注片段以增强数据。论文放宽了对片段长度的强假设，扩展了视频分割方法在可变长度场景下的适用性，从而扩充小型标注数据集，提升下游通过模仿学习训练的指令跟随策略表现。实验验证了该方法在多个场景下能有效提高策略质量。该工作为基于模仿学习的指令跟随智能体训练提供了重要的数据增强工具，对机器人操作任务具有方法支撑价值。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1571, \"height\": 368, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 844, \"height\": 574, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 826, \"height\": 427, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 840, \"height\": 1006, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 635, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 838, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-33892/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 776, \"height\": 586, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33892/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 760, \"height\": 110, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33892/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 191, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33892/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 713, \"height\": 425, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-33892/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 755, \"height\": 426, \"label\": \"Table\"}]"
motivation: 指令-轨迹配对数据稀缺限制可指令智能体的规模化训练。
method: 提出半监督方法，从未标注游玩轨迹中提取可变长度标注片段以扩充数据。
result: 下游通过模仿学习训练的指令跟随策略性能得到提升。
conclusion: 为基于模仿学习的可指令智能体训练提供了一种有效的数据增强方法。
---

## Abstract
The scalability of instructable agents in robotics or gaming is often hindered by limited data that pairs instructions with agent trajectories. However, large datasets of unannotated trajectories containing sequences of various agent behaviour (play trajectories) are often available. In a semi-supervised setup, we explore methods to extract labelled segments from play trajectories. The goal is to augment a small annotated dataset of instruction-trajectory pairs to improve the performance of an instruction-following policy trained downstream via imitation learning. Assuming little variation in segment length, recent video segmentation methods can effectively extract labelled segments. To address the constraint of segment length, we propose Play Segmentation (PS), a probabilistic model that finds maximum likely segmentations of extended subsegments, while only being trained on individual instruction segments. Our results in a game environment and a simulated robotic gripper setting underscore the importance of segmentation; randomly sampled segments diminish performance, while incorporating labelled segments from PS improves policy performance to the level of a policy trained on twice the amount of labelled data.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Data Augmentation for Instruction Following Policies via Trajectory Segmentation" organized according to specific points. Let me analyze the paper carefully and structure the response accordingly.

The paper is about data augmentation for instruction following policies through trajectory segmentation. Let me extract the key information:

1. Core problem: Limited data pairing instructions with trajectories for instructable agents
2. Method: Semi-supervised approach using Play Segmentation (PS) - a probabilistic model
3. Experiments: BabyAI environment and CALVIN robotic manipulation benchmark
4. Resources: Not explicitly mentioned in detail
5. Experiment count: Multiple comparisons across two environments
6. Conclusions: PS outperforms video segmentation methods, achieves performance equivalent to 2x labeled data
7. Strengths: Novel PS approach, thorough comparison
8. Limitations: Computational complexity, no groundtruth annotations in CALVIN

Let me write a comprehensive Chinese summary following the requested structure.</think>

# 论文总结：通过轨迹分割增强指令跟随策略的训练数据

## 一、核心问题与研究动机

- **核心问题**：在机器人或游戏场景中，训练可指令智能体（instructable agent）需要大量「自然语言指令—轨迹」的配对标注数据，但此类数据稀缺且标注成本高昂，成为规模化训练的主要瓶颈。
- **数据利用思路**：现实中却存在大量「未标注的游玩轨迹（play trajectories）」，即人类或代理自由操作产生、包含多种行为序列的长轨迹（如 YouTube 游戏视频、机器人 play data）。如何从这些未标注数据中挖掘有价值的监督信号？
- **研究目标**：在**半监督**设定下，仅使用少量带标签的指令片段，从大量未标注游玩轨迹中自动分割并标注出有效的指令片段，以扩充小型标注数据集，从而提升下游通过**模仿学习**训练的指令跟随策略性能。
- **关键挑战**：游玩轨迹包含多个连续或重叠的指令行为，简单随机采样容易切到不完整的指令或多指令片段，导致分布外（OOD）问题，影响策略训练。

## 二、方法论：核心技术细节

### 1. 数据形式化

- **标注集** $\mathcal{D}_{ann}$：包含 $N$ 个（轨迹 $\tau$，指令 $d$）配对，其中轨迹长度 $T_k$ 较短；
- **未标注集** $\mathcal{D}_{unann}$：包含 $M$ 个仅轨迹数据，长度 $T'_k \gg T_k$；
- **目标**：从 $\mathcal{D}_{unann}$ 提取带标签的片段，加入 $\mathcal{D}_{ann}$ 用于下游模仿学习训练。

### 2. 三种分割方法的对比

**(a) 随机采样片段（Random Segments）**：从游玩轨迹中随机采样窗口，用基于标注集训练的标签模型（I3D 架构）打标签。基线方法，存在严重 OOD 问题。

**(b) 视频分割方法的改造**：
- **UnLoc**（Action Segmentation 方法）：基于 CLIP 框架，对每帧预测动作标签，将背景类裁剪掉。计算复杂度 $O(|\zeta|)$，随指令数线性增长。
- **TriDet**（Temporal Action Localization 方法）：通过边界预测头直接输出动作起点、终点和类别。计算复杂度 $O(1)$。
- **共同缺点**：二者均假设指令长度变化小，需要「先采样大窗口再裁剪」的策略；当指令长度差异大时表现差。

**(c) Play Segmentation（PS，本文核心方法）**：
- **概率分解**：
$$p(\tau_{1:K}, \alpha_{0:T-1}|o_{0:T}) = \prod_{k=1}^{K} p_{\theta_{LM}}(\tau_k|o_{\alpha(k):\alpha(k+1)}) \cdot \prod_{t=0}^{T-1} p_{\theta_{Seg}}(\alpha_t|o_{\gamma(\alpha_{0:t}):t+1})$$
- **两个预测头**：
  - 标签模型 $p_{\theta_{LM}}$：预测片段对应指令；
  - 分割模型 $p_{\theta_{Seg}}$：预测每个时间步是否为片段边界。
- **负样本构造**（关键创新）：将标注片段在时间轴上左右平移、缩短或拉长，构建分割标签为 0 的负样本，使模型学到「完整指令片段」的概念。
- **推理时**：通过动态规划（类似 Hidden Semi-Markov Model 的 Viterbi 算法）求解最优分割 $\alpha^*_{0:T-1}$，复杂度 $O(T^3)$；通过滑窗方式处理超长轨迹。
- **共享骨干网络**：两个预测头共用参数，仅有独立输出层。

## 三、实验设计

### 实验场景

1. **BabyAI**（网格世界，Chevalier-Boisvert 等，2019）：
   - 任务：GoTo + 7 distractors，导航至指定颜色物体；
   - 观测：64×64 RGB 图像；动作：4 维离散；
   - play 轨迹由自动 bot 生成，每个轨迹串联 10 个任务，时长 11–71 步；
   - 评估指标：25 步内任务成功率（512 episodes）。

2. **CALVIN**（Mees 等，2022）：
   - 模拟 Franka Panda 7 自由度机械臂桌面操作；
   - 34 种任务类型（推块、开抽屉、开关灯等）；
   - play 轨迹长度 1674–30838 步，指令片段长度 32–64 步；
   - 观测：静态相机 + 腕部相机图像；
   - 评估指标：连续 5 条指令中完成的平均指令数（1000 序列）；
   - 训练采用多上下文模仿学习（MCIL）。

### 对比方法

- **基线**：随机片段标注（Random Relabel）；
- **上界**：GT-Relabel（用真实边界 + 标签模型重打标签）；
- **其他基线**：不同标注数据量（100%、50%、25%、10%）；
- **视频分割对比**：UnLoc、TriDet；
- **本文方法**：Play Segmentation（PS）。

## 四、资源与算力

- **论文未明确说明**所用 GPU 型号、数量及具体训练时长。
- 可推断信息：
  - BabyAI 训练相对轻量，使用模仿学习标准配置；
  - CALVIN 实验基于 MCIL 框架，训练开销较大；
  - 标注过程依赖于 Hybrid Intelligence Center 与 SURF 协作的荷兰国家 e-infrastructure（grant no. EINF-6630），暗示使用了大规模计算资源但未披露细节。
- 整体算力透明度较低，是本论文的不足之一。

## 五、实验数量与充分性

- **实验规模**：
  - BabyAI：策略评估在 512 episodes 上、跨 8 个随机种子；
  - CALVIN：评估 1000 个序列、跨 4 个种子；
  - 标注数据量消融：100%、50%、25%、10% 四档；
  - 分割质量评估：精度、召回率、F1、标签准确率四指标；
  - 标签分布与任务改进相关性分析。
- **充分性评价**：
  - **较为充分**：覆盖了两个差异显著的 benchmark（合成游戏 vs 真实机器人模拟），多随机种子、多指标对比；
  - **仍可改进**：缺少对 PS 模型自身关键超参数（如窗口大小 $\omega$、平移范围）的消融；对 DP 算法效率的实测时间未报告；视频分割方法在 CALVIN 上的标签质量无法评估（无标注）。
- **公平性**：所有方法均在相同的起始分割（starting split）上公平比较。

## 六、主要结论与发现

1. **分割质量至关重要**：随机采样片段会显著降低策略性能（BabyAI 中从 0.84 降至 0.05），说明有效分割是数据增强的前提。
2. **GT-Relabel 上界有效**：在两个环境中，加入 GT-Relabel 片段均能恢复 100% 标注数据的性能，验证了标签模型的可靠性。
3. **视频分割方法不可靠**：UnLoc 和 TriDet 因训练与测试时长分布不一致，难以泛化到长游玩轨迹；在 BabyAI 中 TriDet 甚至严重损害策略性能（0.26）。
4. **PS 显著优于视频分割**：PS 实现了更高的分割精度（0.826）和标签准确率（0.516）。
5. **PS 提升下游策略至 2× 数据水平**：
   - BabyAI：PS 取得 0.702，介于 GT-50% (0.805) 与 GT-25% (0.645) 之间，相当于 2 倍标注数据的水平；
   - CALVIN：PS 取得 1.477，介于 GT-50% (1.411) 与 GT-100% (1.698) 之间。
6. **标签分布不均是性能瓶颈**：PS 抽取的片段在某些任务上过采样，与策略改进呈正相关，表明任务覆盖均衡性影响最终效果。

## 七、优点与亮点

- **问题定位精准**：直击指令跟随领域数据稀缺的核心痛点，提出从「play data」挖掘价值的半监督新视角。
- **方法设计新颖**：PS 通过正负样本对比学习分割边界，并以动态规划求解最优分割，巧妙绕开了对完整标注游玩轨迹的依赖。
- **跨场景验证**：同时在合成游戏（BabyAI）与高维机器人模拟（CALVIN）上验证，方法通用性较强。
- **对比基线全面**：既与视频分割前沿方法（UnLoc、TriDet）比较，也与多种数据规模及随机基线对比，论证严密。
- **开放源代码**：GitHub 开源实现（PlaySegmentation-AAAI2025），便于复现与扩展。

## 八、不足与局限

- **计算复杂度高**：PS 的动态规划算法复杂度为 $O(T^3)$，对长轨迹（CALVIN 中达 30838 步）需滑窗处理，效率受限；论文未给出实际推理时间数据。
- **CALVIN 无真值评估**：CALVIN 的 play 轨迹未标注，无法直接评估分割质量，只能依赖下游策略表现作为间接证据。
- **视频分割方法的失败原因未深入剖析**：仅给出精度和准确率数据，缺乏对其失败机理的细致分析（如为何训练分布与测试分布不匹配）。
- **标签分布偏差**：抽取的片段在任务类型上不均衡，会导致少数任务欠训练，但论文未提出缓解策略（如重加权或平衡采样）。
- **对负样本构造超参数敏感**：平移步数 $\{t_{min}, ..., t_{max}\}$ 的选择对 PS 影响较大，但论文未进行消融实验。
- **风险讨论较浅**：仅指出错误指令执行与滥用两类风险，未讨论分割错误导致的安全隐患或标注数据偏差带来的伦理问题。
- **应用限制**：当前方法假设指令来自有限集合 $\zeta$，难以直接扩展到开放词汇或长自然语言描述场景。

（完）
