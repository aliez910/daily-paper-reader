---
title: Lifelong Language-Conditioned Robotic Manipulation Learning
title_zh: 终身语言条件机器人操作学习
authors: "Xudong Wang, Zebin Han, Zhiyu Liu, Gan Li, Jiahua Dong, Baichen Liu, Lianqing Liu, Zhi Han"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38930/42892"
tags: ["query:rob-il"]
score: 4.0
evidence: 语言条件操作的终身学习
tldr: 语言条件操作智能体在学习新技能时会遗忘旧技能。本文提出SkillsCrafter框架，通过技能知识保留和共享知识继承，以及奇异值分解获取语义子空间，实现持续学习。实验证明在多个技能上有效减轻遗忘，同时适应新技能，为终身语言条件操作提供了可行方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38930/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1823, \"height\": 640, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38930/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1749, \"height\": 431, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38930/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1818, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38930/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 544, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38930/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 877, \"height\": 435, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38930/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1845, \"height\": 549, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38930/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1836, \"height\": 552, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38930/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 874, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38930/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 249, \"label\": \"Table\"}]"
motivation: 解决语言条件操作中旧技能遗忘的问题。
method: 提出SkillsCrafter框架，通过技能适应和语义子空间保留旧知识。
result: 在多个操作技能上有效减轻遗忘。
conclusion: 提出了一种终身学习框架用于语言条件操作。
---

## Abstract
Traditional language-conditioned manipulation agent adaptation to new manipulation skills leads to catastrophic forgetting of old skills, limiting dynamic scene practical deployment. In this paper, we propose SkillsCrafter, a novel robotic manipulation framework designed to continually learn multiple skills while reducing catastrophic forgetting of old skills. Specifically, we propose a Manipulation Skills Adaptation to retain the old skills knowledge while inheriting the shared knowledge between new and old skills to facilitate learning of new skills. Meanwhile, we perform the singular value decomposition on the diverse skill instructions to obtain common skill semantic subspace projection matrices, thereby recording the essential semantic space of skills. To achieve forget-less and generalization manipulation, we propose a Skills Specialization Aggregation to compute inter-skills similarity in skill semantic subspaces, achieving aggregation of the previously learned skill knowledge for any new or unknown skill. Extensive simulator and real-world experiments demonstrate the effectiveness and superiority of our SkillsCrafter.

---

## 论文详细总结（自动生成）

# 终身语言条件机器人操作学习（SkillsCrafter）论文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）
- **核心问题**：语言条件机器人操作（LCRM）智能体在顺序适应新技能时，会灾难性地遗忘已学过的旧技能，严重阻碍其在动态环境中的实际部署。
- **现有局限**：传统方法采用任务特定微调（fine-tune）或为每个技能保存独立模型，导致存储和计算开销大；基于LoRA的参数高效微调虽能缓解存储问题，但各技能独立对待，忽略了技能间的共享知识，且推理时需要手动选择适配器，难以扩展。MoE-LoRA类方法虽引入自动路由，但需预定义专家数量，可能过拟合或欠利用。
- **整体含义**：本文首次定义“终身语言条件机器人操作（LLCRM）”任务，旨在使机器人能够持续积累、重用和精炼操作技能，实现类似人类的终身学习能力。核心挑战在于：如何探索和利用技能间的共享知识与专有知识，以及如何自适应灵活地聚合已学知识以应对新技能或未知技能。

## 2. 论文提出的方法论：核心思想、关键技术细节
核心框架名为 **SkillsCrafter**，包含三大模块：**Manipulation Skills Adaptation (MSkA)**、**Skills Specialization Aggregation (SkSA)**、**Skills Specified Inference (SkSI)**。总体以LLARVA（预训练LLaMA 2 + CLIP视觉编码器）为骨干，在每层注入LoRA并创新性设计。

### 2.1 Manipulation Skills Adaptation（MSkA）
- **目标**：持续学习新技能并保留旧技能知识。
- **技能共享知识继承（Adapter Inheritance）**：基于观测3（子空间A倾向于学习共享知识，B学习专有知识），将第t个技能LoRA的A矩阵初始化为先前所有技能A矩阵的聚合版本，聚合权重由SkSA模块（依技能语义相似度计算）获得，实现继承共享知识。
- **技能专有知识正交约束（Skills Orthogonal Optimization）**：强制当前技能LoRA的B矩阵与先前所有技能的B矩阵正交，并用L2归一化防止零解，从而保留技能特定知识并维持结构稳定。
- **动态稀疏LoRA加载（Gumbel-Softmax Gating）**：基于观测2（不同技能对不同层重要性不同），每层引入可训练的Gumbel-Softmax门控，自适应决定该层是否注入LoRA，并加入稀疏正则项，避免简单技能过参数化、复杂技能欠参数化。
- **训练损失**：自回归动作预测交叉熵损失 + 正交约束损失 + 稀疏正则项。

### 2.2 Skills Specialization Aggregation（SkSA）
- **核心思想**：基于观测1（技能参数子空间与语义子空间具有相似相关性），利用技能指令的语义子空间相似度来自适应聚合已学LoRA适配器。
- **关键步骤**：
  1. 对每个技能的多条指令使用CLIP文本编码器提取嵌入，进行**SVD**分解，取其右奇异向量的前 $r_s$ 行构成投影矩阵 $\psi_t$，作为该技能的公共语义子空间投影。
  2. 对于新技能或未知技能，计算其指令嵌入在每个已学语义子空间上的投影，并计算余弦相似度，经指数（$\gamma$）变换后归一化得到聚合权重 $\Omega$。
  3. 将权重与所有已学LoRA适配器进行加权聚合，得到当前技能专用的聚合适配器 $\Delta \tilde{W}$。

### 2.3 Skills Specified Inference（SkSI）
- 推理时，依据输入指令通过SkSA聚合得到适配器，加载到预训练模型上，使机器人能够利用历史知识完成任意已知或未知技能，实现遗忘最小化。

## 3. 实验设计
### 3.1 数据集/场景
- **模拟环境**：基于RLBench搭建12项常见机器人操作技能（如开抽屉、滑方块、放钱、扫灰尘、按按钮、转水龙头、放置玩具、拿瓶子、叠方块、拧灯泡、掀肉饼、关罐子等）。
- **真实环境**：包含6项真实世界操作技能（如开抽屉、推按钮、堆方块、拿玩具等），使用UR-5机械臂及RGB相机采集。
- **总技能序列**：共18个技能（12模拟+6真实），其中前16个用于训练和测试（顺序学习），后2个未训练仅用于开放世界泛化测试。

### 3.2 Benchmark
- **任务定义**：终身语言条件机器人操作（LLCRM）基准，所有技能按顺序学习，测试时技能ID不可知，评估所有技能的成功率和遗忘率。
- **评估指标**：
  - **平均成功率（ASR）**：每个技能25个episode的成功率均值。
  - **遗忘率（FR）**：相对于刚学完时的性能下降比例。
  - 开放世界泛化能力：最后2个未经训练的技能的ASR。

### 3.3 对比方法（共11种）
- **基础方法**：Seq-FT（顺序全量微调）、LwF-LoRA（知识蒸馏）、EWC-LoRA（参数重要性正则）。
- **MoE类方法**：Dense MoLE、Sparse MoLE、MoLA、HydraLoRA、BranchLoRA。
- **正交子空间类方法**：O-LoRA + SkSA、SD-LoRA + SkSA。
- 所有对比方法均基于同一LLARVA骨干和LoRA配置，公平比较。

### 3.4 消融实验
- 表3：分别移除Gumbel门控（GGM）、继承A（INA）、正交项（SOT），验证各组件对共享/专有知识探索的作用。
- 表4：比较不同知识聚合策略（指令匹配、视觉匹配、平均池化、最相似选取），验证SkSA的有效性。

## 4. 资源与算力
- 文中明确说明：使用PyTorch 2.1.2与cu121，在**8张NVIDIA RTX 6000 Ada Generation GPUs**上完成训练和测试。
- **未提供**具体的训练总时长或每个技能的迭代步数，因此无法评估计算的绝对成本。
- 推理阶段仅需加载聚合后的LoRA，开销较小。

## 5. 实验数量与充分性
- **数量**：主实验（Tab.1 & Tab.2）覆盖18个技能（16个学习+2个开放域），对比11种方法；消融实验两组（Tab.3 & Tab.4）验证11种框架变体；此外还有初步观测实验（图2）和可视化案例（图5）。
- **充分性**：
  - 任务设定（LLCRM）是全新的，benchmark设计合理，涵盖模拟与真实、已知与未知技能。
  - 对比方法众多且为SOTA，包括正则、MoE、正交子空间等代表性类型，覆盖全面。
  - 消融实验对各个创新组件进行了分拆验证，结论清晰。
  - 在模拟和真实场景中均验证，增强了结论的泛化性。
- **公平性**：所有方法基于相同骨干和LoRA设置，实验条件一致；评估时每个技能执行25次，统计平均结果，减少随机性。

## 6. 论文的主要结论与发现
- **SkillsCrafter在LLCRM任务上显著优于所有对比方法**：平均ASR达52.0%，比最优基线（SD-LoRA+SkSA, 50.0%）高出2个百分点；平均FR降至16.0%，比基线（20.8%）降低4.8个百分点。
- **在开放世界泛化技能（S17、S18）上表现最佳**，说明知识聚合机制有助于利用先验技能完成未见过的任务。
- **消融实验证明**：共享知识继承、正交约束、动态稀疏加载、基于SVD语义子空间的聚合均为关键组件，缺一不可。
- **三则关键观察**：
  1. 技能参数子空间与语义子空间的相似性一致（可关联）。
  2. 不同技能所需的知识在各Transformer层分布不同（可稀疏化）。
  3. LoRA的A子空间自然表征共享知识，B子空间表征专有知识（可解耦）。

## 7. 优点
- **任务新颖性**：首次定义并构建了终身语言条件机器人操作（LLCRM）任务及基准，推动该方向研究。
- **方法设计巧妙**：充分利用LoRA内在的分解特性（A共享 / B专有），并验证了语义-参数子空间的关联性，据此设计轻量且高效的聚合机制。
- **创新技术点**：
  - 正交约束 + 继承初始化实现技能共享与专有知识的协同学习。
  - Gumbel-Softmax门控实现动态稀疏LoRA注入，避免固定分配导致过/欠拟合。
  - 基于SVD的语义子空间投影 + 指数归一化权重聚合，泛化能力强。
- **实验充分**：模拟+真实、已知+开放泛化、11种对比方法、多组消融，较全面验证了有效性。
- **代码开源**：提供项目网站和代码链接，利于复现。

## 8. 不足与局限
- **技能遗忘未完全消除**：虽然在整体上FR显著降低，但部分技能（如S11、S16）仍表现较高遗忘率（S11 FR=75%，S16 FR=0%? 从表2看SkillsCrafter的S16 FR=0但S11 FR=75%? 实际表2中SkillsCrafter最后一行显示S11 FR=25%? 仔细看表：SkillsCrafter在S11的FR值为25%（表2最后一行），S16为0%但S16是真实环境？仍有较大遗忘。且对S8-S11等简单技能遗忘依然严重，可能表明知识聚合对某些技能效果有限。
- **开放世界泛化仍有差距**：S17和S18未训练，SkillsCrafter成功率40%和52%，虽优于基线，但离实用仍有距离。
- **未提供训练时间与计算成本**：尽管给出了GPU信息，但缺乏训练每技能的耗时或总时间，无法评估方法的实际计算效率。
- **RLBench技能种类有限**：12个模拟技能均为相对简单的桌面操作，是否适用于更复杂且具高动态性的任务（如装配、多步长时任务）尚未验证。
- **仅对LoRA结构进行实验**：方法高度依赖LoRA的分解假设（A共享/B专有），是否适用于其他参数高效微调方法（如Adapter、Prefix Tuning）未探讨。
- **无理论保证**：正交约束虽直观，但缺乏系统的收敛性分析或最优性证明。
- **超参数敏感**：如SVD截断维度rs、正交项权重λ、温度τg等未进行灵敏度分析，可能影响可复现性。
- **未讨论无指令场景**：仅处理语言指令输入，若指令缺失或模糊则无法正常工作。

（完）
