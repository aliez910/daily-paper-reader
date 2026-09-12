---
title: "ContextFlow: In-Context Flow Matching for Robot Manipulation"
title_zh: ContextFlow：面向机器人操控的上下文流匹配模仿学习
authors: "Jian Ding, Xianjie DAI, Roei Herzig, Nussair Hroub, Jinjie Mai, Dengxin Dai, Bernard Ghanem, Mohamed Elhoseiny"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/8149.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于条件流匹配的上下文模仿学习，直接针对机器人操控的模仿学习问题
tldr: 针对现有自回归上下文模仿学习方法将连续动作离散化、导致误差累积并限制对未见任务配置泛化能力的问题，本文提出了ContextFlow。该方法是一个条件流匹配模型，学习用于上下文模仿学习的连续动作分布，将基于流的策略以示范上下文为条件，从而在保留上下文学习优势的同时支持连续控制。在机器人操控任务上的实验表明，ContextFlow 在泛化能力和误差控制方面均优于自回归基线。该工作为面向复杂操控任务的连续动作模仿学习提供了一种新范式。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 870, \"height\": 819}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 870, \"height\": 833}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-003.webp\", \"caption\": \"\", \"page\": 7, \"index\": 3, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-004.webp\", \"caption\": \"\", \"page\": 7, \"index\": 4, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-005.webp\", \"caption\": \"\", \"page\": 7, \"index\": 5, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-006.webp\", \"caption\": \"\", \"page\": 7, \"index\": 6, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-007.webp\", \"caption\": \"\", \"page\": 7, \"index\": 7, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-008.webp\", \"caption\": \"\", \"page\": 7, \"index\": 8, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-009.webp\", \"caption\": \"\", \"page\": 7, \"index\": 9, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-010.webp\", \"caption\": \"\", \"page\": 7, \"index\": 10, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-011.webp\", \"caption\": \"\", \"page\": 7, \"index\": 11, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-012.webp\", \"caption\": \"\", \"page\": 7, \"index\": 12, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-013.webp\", \"caption\": \"\", \"page\": 7, \"index\": 13, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-014.webp\", \"caption\": \"\", \"page\": 7, \"index\": 14, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-015.webp\", \"caption\": \"\", \"page\": 7, \"index\": 15, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-016.webp\", \"caption\": \"\", \"page\": 7, \"index\": 16, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-017.webp\", \"caption\": \"\", \"page\": 7, \"index\": 17, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-018.webp\", \"caption\": \"\", \"page\": 7, \"index\": 18, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-019.webp\", \"caption\": \"\", \"page\": 7, \"index\": 19, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-020.webp\", \"caption\": \"\", \"page\": 7, \"index\": 20, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-021.webp\", \"caption\": \"\", \"page\": 7, \"index\": 21, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-022.webp\", \"caption\": \"\", \"page\": 7, \"index\": 22, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-023.webp\", \"caption\": \"\", \"page\": 7, \"index\": 23, \"width\": 1024, \"height\": 1536}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-024.webp\", \"caption\": \"\", \"page\": 7, \"index\": 24, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-025.webp\", \"caption\": \"\", \"page\": 7, \"index\": 25, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-026.webp\", \"caption\": \"\", \"page\": 7, \"index\": 26, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-027.webp\", \"caption\": \"\", \"page\": 7, \"index\": 27, \"width\": 1280, \"height\": 1707}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-028.webp\", \"caption\": \"\", \"page\": 7, \"index\": 28, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-029.webp\", \"caption\": \"\", \"page\": 7, \"index\": 29, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-030.webp\", \"caption\": \"\", \"page\": 7, \"index\": 30, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-031.webp\", \"caption\": \"\", \"page\": 7, \"index\": 31, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-032.webp\", \"caption\": \"\", \"page\": 7, \"index\": 32, \"width\": 848, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-033.webp\", \"caption\": \"\", \"page\": 10, \"index\": 33, \"width\": 512, \"height\": 350}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-034.webp\", \"caption\": \"\", \"page\": 10, \"index\": 34, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-035.webp\", \"caption\": \"\", \"page\": 10, \"index\": 35, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-036.webp\", \"caption\": \"\", \"page\": 10, \"index\": 36, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-037.webp\", \"caption\": \"\", \"page\": 10, \"index\": 37, \"width\": 512, \"height\": 311}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-038.webp\", \"caption\": \"\", \"page\": 10, \"index\": 38, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-039.webp\", \"caption\": \"\", \"page\": 14, \"index\": 39, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-040.webp\", \"caption\": \"\", \"page\": 14, \"index\": 40, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-041.webp\", \"caption\": \"\", \"page\": 14, \"index\": 41, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-042.webp\", \"caption\": \"\", \"page\": 14, \"index\": 42, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-043.webp\", \"caption\": \"\", \"page\": 14, \"index\": 43, \"width\": 2048, \"height\": 2048}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-044.webp\", \"caption\": \"\", \"page\": 14, \"index\": 44, \"width\": 1056, \"height\": 1008}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-045.webp\", \"caption\": \"\", \"page\": 14, \"index\": 45, \"width\": 1280, \"height\": 1280}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-046.webp\", \"caption\": \"\", \"page\": 14, \"index\": 46, \"width\": 1770, \"height\": 1770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-efe8ec291bee74949f3a0417/fig-047.webp\", \"caption\": \"\", \"page\": 14, \"index\": 47, \"width\": 3477, \"height\": 959}]"
motivation: 自回归上下文模仿方法离散化连续动作，导致误差累积和泛化能力受限。
method: 提出条件流匹配模型ContextFlow，学习上下文条件下的连续动作分布用于模仿学习。
result: 在机器人操控任务上相比自回归基线取得更好的泛化能力与更低的误差累积。
conclusion: ContextFlow 将流匹配与上下文模仿学习结合，提升了连续动作操控的鲁棒性。
---

## Abstract
Although highly effective in vision and language domains, applying in-context learning to robotics remains challenging. Existing autoregressive in-context imitation methods discretize continuous actions and exacerbate the accumulation of early prediction errors through next-token prediction, limiting their generalization on unseen task configurations. Meanwhile, flow-matching policies have been explored for continuous robot control and can help mitigate compounding errors; however, in-context imitation learning within a flow-matching framework remains underexplored. To address these limitations, we introduce ContextFlow, a conditional flow-matching model that learns continuous action distributions for in-context imitation learning. ContextFlow conditions flow-based action prediction on demonstrations and observations, enabling robust generation from noisy action distributions. To better encode multimodal in-context demonstrations, we adapt perceiver-style multimodal context compressors that distill visual, proprioceptive, and action sequences into compact, task-relevant latent representations. On LIBERO, ContextFlow outperforms ICRT by 35 percentage points in average success rate on unseen task configurations, while matching the performance of the task-specific fine-tuned VLA model π with- 0 out any fine-tuning on unseen tasks. On real robots, it generalizes to unseen configurations of both single-arm and bimanual tasks, achieving 40% success on a new pen-uncapping configuration. Project Page: https://dingjiansw101.github.io/contextflow-page/.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "ContextFlow: In-Context Flow Matching for Robot Manipulation" organized in 8 specific sections. Let me analyze the paper carefully and structure the response according to the requirements.

The paper proposes ContextFlow, which combines conditional flow matching with in-context imitation learning for robot manipulation. Let me go through each section:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me write a comprehensive Chinese summary in Markdown format.</think>

# ContextFlow 论文总结

## 1. 核心问题与研究动机

- **背景**：上下文模仿学习（In-Context Imitation Learning, ICIL）旨在让机器人通过观察少量示范，在测试时无需梯度更新即可适应新任务，是将 LLM 领域成熟的 ICL 能力迁移到机器人操控的重要方向。
- **现有方法局限**：当前主流 ICIL 方法（如 ICRT、RICL、Prompt-DT 等）大多采用自回归架构（Autoregressive Model, ARM），存在两个根本问题：
  - **离散化误差**：连续动作需经 action tokenizer 量化为离散 token，存在不可避免的重建误差；
  - **误差累积（Compounding Error）**：自回归逐步预测使早期错误在 rollout 中不断放大，在分布外（训练/测试任务配置不同）的场景下尤为严重。
- **研究动机**：近年来 Flow Matching（FM）在连续机器人控制（如 π0）中展现出比自回归更优的稳定性，但**尚未有工作将 in-context learning 系统地融入到 flow-matching 框架中**。本文正是要填补这一空白。

---

## 2. 方法论

### 2.1 整体思路

提出 **ContextFlow**，一个以示范（demonstration）为条件的条件流匹配模型，将流匹配的"连续动作块并行预测"优势与 ICL 的"少样本无更新适应"能力相结合。

### 2.2 关键技术细节

- **问题形式化**：对任务 τ，给定示范 d = [T, X, Q, A]（文本指令 + 图像序列 + 关节/夹爪状态 + 动作），目标是建模条件分布 π(aₜ | oₜ, d)，其中 aₜ 表示未来 H 个动作块。
- **流匹配目标**：
  - 构造插值分布 pₛ(aᵗ | aₜ) = 𝒩(s·aₜ, (1−s)²I)，s∈[0,1]；
  - 中间动作为 aᵗ = (1−s)ε + s·aₜ；
  - 真实速度场为 u = aₜ − ε；
  - 学习一个参数化速度场 u_θ(aᵗ, oₜ, d, s)；
  - 损失函数 L_CFM = 𝔼‖u_θ − u‖²，s ~ Beta(1.5, 1)；
  - 推理使用 K=10 步前向 Euler 求解器。
- **Mixture-of-Experts 架构**：
  - **Context Expert（300M 参数）**：处理当前观察 + 文本 + 示范上下文；
  - **Action Expert**：处理当前本体感知状态 + 噪声动作，通过 cross-attention 与 Context Expert 交互；
  - 两者均基于类似 Gemma 的结构，权重初始化自 π0（视觉编码器 SigLIP），Action Expert 用 LoRA (rank=32) 微调。
- **多模态上下文压缩器（核心创新之一）**：
  - 借鉴 Perceiver/Perceiver IO 思路，为图像、本体感知状态、动作三种模态各设计一个可学习压缩器；
  - 通过交叉注意力 + 自注意力交替层，将长示范压缩为固定大小（每模态 32 个 latent query）的紧凑表示；
  - 缓解了长多模态序列对标准 Transformer 注意力的二次复杂度瓶颈。
- **块状因果注意力（Block-wise Causal Attention）**：action tokens 可 attention 到 context tokens，但反之不行；这样可在 K 步流匹配迭代中**缓存 context tokens**，显著降低推理开销。

### 2.3 ContextFlow-Plain 与 ContextFlow

- **ContextFlow-Plain**：不启用压缩器，直接用 attention 处理示范；为 baseline 验证流匹配本身的增益。
- **ContextFlow**：完整模型，启用三种模态压缩器。

---

## 3. 实验设计

### 3.1 数据集与场景

- **仿真**：LIBERO 基准（Franka Panda 机械臂），重点评估 **LIBERO-Spatial**（空间推理）与 **LIBERO-Object**（物体操控），训练时还引入 LIBERO-Goal 和 LIBERO-10 的数据；附加实验进一步加入 LIBERO-90。
  - 每个任务套件 10 个任务 → 8 个 seen + 2 个 unseen；
  - 每个任务 50 次推理评估成功率。
- **真实机器人**：自建 ALOHA 平台数据集，包含 **25 个任务配置 / 1318 条多模态轨迹 / 1064 训练示范**（另有 254 条仅训练用）：
  - 单臂 Pick-and-Place（234 步）；
  - 精细双手 Uncap Pen（534 步）；
  - 双手 Put Egg in Box（736 步）；
  - 另含 handover、cup stack、stir、water wipe 四个额外双手任务。
- **3 个机位相机**：1 个高空 + 2 个腕部相机。

### 3.2 对比方法

- **ICRT**：代表性自回归 ICL baseline（LLaMA2-Base 主干）。
- **ContextAR**：作者自实现的更强自回归 baseline，使用与 ContextFlow 相同的 SigLIP+π0 初始化，确保公平对比"自回归 vs 流匹配"。
- **OpenVLA-OFT**：大规模 VLA 模型，纯文本指令驱动。
- **π0**：VLA flow model，纯文本指令驱动。
- **π0 (FT)**：用 1 条未见任务示范对 π0 进行任务级微调，作为"参数化适应"参考。

### 3.3 评估指标

- 主指标：成功率（Success Rate）；
- 辅助：累积 MSE（compounding error）、推理吞吐量、注意力图、轨迹可视化。

---

## 4. 资源与算力

- **模型规模**：Context Expert 约 300M 参数；Action Expert 与 SigLIP 来自 π0 初始化。
- **训练配置**：20K 步迭代，batch size 32；cosine 学习率，peak 2.5e-5，min 2.5e-6，前 1000 步 warm-up。
- **硬件信息**：**论文未明确说明 GPU 型号、数量、单卡训练时长或总算力消耗**（仅在 Acknowledgements 中提及得到 KAUST 资助）。这是一个明显的报告缺失点。

---

## 5. 实验数量与充分性

实验数量较为充分，主要包括：

- **主对比实验**（Tab. 1）：6 个模型 × 4 个任务配置 × LIBERO-Spatial/Object。
- **消融实验**（5 组）：
  - Tab. 2：压缩器有效性（图像 / 状态+动作组合）；
  - Tab. 3：上下文各模态贡献（图像、文本、状态+动作三选一/全选）；
  - Tab. 4：图像帧数（4 vs 8）与状态/动作数（64/128/256）超参；
  - Tab. 5：动作头对比（MLP L1 / Diffusion / Flow Matching）；
  - Tab. 6：累积 MSE 对比；
  - Tab. 7：扩展训练数据（加入 LIBERO-90）对 Goal/10 任务的影响。
- **真实机器人实验**（Tab. 8）：6 个未见任务配置 × 2 个模型 × 每任务 10 次试验。
- **可视化分析**：失败模式分类、压缩器注意力图、3D 轨迹对齐。
- **公平性**：通过 ContextAR vs ContextFlow-Plain 的控制变量对比，隔离了"自回归 vs 流匹配"的纯粹影响；统一了视觉主干和初始化。
- **不足**：真实机器人试验仅 10 次/任务，统计显著性较弱；未见任务仅在"同类原语内的物体/空间配置变化"，未触及"全新任务类型"的真正 OOD。

---

## 6. 主要结论与发现

- **流匹配 > 自回归**：在 ICL 设定下，ContextFlow-Plain（FM）比 ContextAR（AR）平均成功率高 10.5 个百分点（控制变量），验证了"连续动作并行预测"对减少 compounding error 的关键作用。
- **压缩器增益明显**：ContextFlow 比 Plain 再提升 9.5 分，平均成功率 73.5%，比 ICRT 高 35 分。
- **匹配任务级微调**：ContextFlow 在未见任务上取得 73.5%，与 π0 (FT) 的 72.5% 持平，但**完全无需任务级微调**，具备更快的部署速度和避免灾难性遗忘的优势。
- **文本不够，示范更优**：ContextAR 比 OpenVLA-OFT 高 13.5 分，说明仅靠文本指令难以泛化到未见任务配置。
- **多模态缺一不可**：本体感知 + 动作模态对未见任务贡献最大（移除后掉 44.5 分）；文本贡献其次（移除后掉 9.0 分）；图像也必不可少。
- **误差累积现象**：前 30 步 ContextAR 与 ContextFlow 相当，但 30 步后自回归的 MSE 显著增长，分布偏移下尤为明显。
- **图像压缩器学到任务感知**：attention 随任务阶段动态切换——抓取前关注夹爪，抓取后关注物体，放置阶段关注目标位置。
- **真实机器人可推广**：在 ALOHA 上对未见单臂与双手任务均取得非平凡成功率（最高 6/10 抓鸡蛋入盒），ICRT 则几乎全部失败。

---

## 7. 优点

- **范式创新**：首次将 in-context learning 与 flow matching 框架深度融合，弥补了 ICIL 领域长期以来仅依赖自回归 + 离散 token 的不足。
- **架构设计周到**：
  - 双专家 + 块状因果注意力使 context token 可跨 K 步流匹配迭代复用；
  - 三模态分别压缩，针对图像、状态、动作的冗余特性差异化设计；
  - 初始化策略（π0 + SigLIP + LoRA）充分利用已有大规模 VLA 预训练。
- **实验控制严谨**：ContextAR vs ContextFlow-Plain 的控制变量对比是论文亮点之一，让读者能纯粹比较"建模方式"而非"架构差异"。
- **覆盖仿真 + 真实机器人**：且真实机器人包含精细双手操控，验证了高频闭环控制场景下的可用性。
- **公开项目页与新数据集**：贡献了 1318 条 ALOHA in-context 示范数据集，对社区有直接价值。

---

## 8. 不足与局限

- **算力与训练细节缺失**：未报告 GPU 型号/数量、单卡或总训练时长、推理延迟等关键信息，难以复现与横向比较。
- **泛化范围有限**：作者明确承认 generalization 仅限"同类原语内未见的物体或空间布局"，并未真正处理"全新任务类别"的 OOD，是 in-context imitation 领域的开放问题。
- **真实机器人统计偏弱**：每任务仅 10 次试验，且未做显著性检验；失败模式分析样本量有限。
- **数据量与多样性瓶颈**：当扩展到 LIBERO-90 后，Goal/10 上的平均从 36.8 仅升至 43.0，Goal 仅到 29%，说明现有模型容量/数据仍不足以驾驭更复杂任务分布。
- **扩散对比不公**：Tab. 5 中 Diffusion 20K 步仅 16.5%（vs FM 73.5%），100K 才到 33.5%，但未在同迭代、同超参下充分调优，结论"FM 优于 Diffusion"需谨慎对待。
- **效率未充分量化**：虽称"ContextFlow 吞吐量高于 AR 基线"，但缺乏具体数字（FPS、延迟、显存占用）的对照表。
- **依赖强预训练骨干**：核心增益高度依赖 π0 初始化；冷启动条件下 ContextFlow-Plain 的表现如何仍待验证。
- **误差分析局限**：compounding error 分析仅针对一个 S2 任务，缺少多任务、多步骤的统计。

（完）
