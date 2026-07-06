---
title: Generalizable Domain Adaptation for Sim-and-Real Policy Co-Training
title_zh: 可泛化的仿真-真实策略协同训练域自适应方法
authors: "Shuo Cheng, Liqian Ma, Zhenyang Chen, Ajay Mandlekar, Caelan Reed Garrett, Danfei Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=ufKaXYJt1F"
tags: ["query:rob-il"]
score: 8.0
evidence: 仿真-真实协同训练行为克隆策略以实现可泛化的机器人操作
tldr: 针对行为克隆中真实演示数据采集成本高的问题，本文提出仿真-真实协同训练框架，通过对齐跨域观测-动作联合分布学习域不变、任务相关的特征空间。该方法使策略主要在仿真中训练，仅需少量真实演示即可获得可泛化的机器人操作能力。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: 行为克隆依赖大量真实演示数据，仿真与真实间的域差距阻碍策略迁移。
method: 提出仿真-真实协同训练框架，通过对齐观测-动作联合分布学习域不变任务相关特征。
result: 在少量真实演示条件下获得优于纯仿真或纯真实训练的跨域操作性能。
conclusion: 联合分布对齐是缩小仿真-真实差距并提升行为克隆泛化性的有效机制。
---

## Abstract
Behavior cloning has shown promise for robot manipulation, but real-world demonstrations are costly to acquire at scale. While simulated data offers a scalable alternative, particularly with advances in automated demonstration generation, transferring policies to the real world is hampered by various simulation and real domain gaps. In this work, we propose a unified sim-and-real co-training framework for learning generalizable manipulation policies that primarily leverages simulation and only requires a few real-world demonstrations. Central to our approach is learning a domain-invariant, task-relevant feature space. Our key insight is that aligning the joint distributions of observations and their corresponding actions across domains provides a richer signal than aligning observations (marginals) alone. We achieve this by embedding an Optimal Transport (OT)-inspired loss within the co-training framework, and extend this to an Unbalanced OT framework to handle the imbalance between abundant simulation data and limited real-world examples. We validate our method on challenging manipulation tasks, showing it can leverage abundant simulation data to achieve up to a 30\% improvement in the real-world success rate and even generalize to scenarios seen only in simulation.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided metadata. Let me organize the content according to the 8 required points.

The paper is about "Generalizable Domain Adaptation for Sim-and-Real Policy Co-Training" - a sim-and-real co-training framework for behavior cloning that uses optimal transport for domain alignment.

Let me structure the summary:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I'll write in Chinese with Markdown formatting.
</think>
# 论文总结：可泛化的仿真-真实策略协同训练域自适应方法

## 1. 核心问题与研究动机

- **研究领域**：基于行为克隆（Behavior Cloning, BC）的机器人操作策略学习。
- **核心矛盾**：行为克隆虽在机器人操作中表现良好，但依赖大量真实世界演示数据，采集成本高昂、难以规模化。
- **已有方案的不足**：
  - 仿真数据虽可大规模生成（尤其是借助自动化演示生成技术），但存在仿真-真实域差距（sim-to-real gap），导致策略迁移效果差。
  - 传统的域对齐方法通常只对齐观测的边际分布（marginal distribution），忽略了"观测-动作"之间的条件关系，信号利用不充分。
- **本文目标**：提出一个统一的仿真-真实协同训练框架，主要利用仿真数据，仅需少量真实演示，即可学到**可泛化**的机器人操作策略，并能处理仿真数据丰富、真实数据稀缺的不平衡问题。

## 2. 方法论

- **核心思想**：学习一个**域不变、任务相关**的特征空间（domain-invariant, task-relevant feature space），从而弥合仿真与真实之间的域差距。
- **关键洞察（Key Insight）**：对齐跨域的**观测-动作联合分布**比单独对齐观测的边际分布能提供更丰富、更有判别力的对齐信号。
- **技术细节**：
  - **最优传输损失（OT-inspired loss）**：在协同训练框架中嵌入 OT 损失，用于对齐两个域的联合分布。
  - **非平衡最优传输（Unbalanced Optimal Transport, UOT）**：扩展为 UOT 框架，专门处理仿真数据量远大于真实数据的不平衡问题，避免传统 OT 对样本数量严格匹配的假设。
  - **整体框架**：属于"协同训练"范式，仿真与真实数据共同参与训练，但真实数据需求极少。
- **算法流程概述**：
  1. 分别从仿真和真实环境采集（观测, 动作）对，构成两个域的数据集。
  2. 通过共享/对齐的编码器学习特征表示。
  3. 在特征空间中施加 OT/UOT 损失，拉齐两域的观测-动作联合分布。
  4. 行为克隆目标（动作预测）作为主任务损失，与分布对齐损失联合优化。

## 3. 实验设计

- **任务场景**：在具有挑战性的机器人操作任务（manipulation tasks）上验证。
- **Benchmark**：论文未在元数据中明确说明使用的具体 benchmark 名称（可能为论文中自定义的若干操作任务场景），但强调任务具备一定难度且能体现跨域泛化能力。
- **对比基线（隐含）**：根据元数据描述，可推断至少比较了以下设定：
  - 纯仿真训练（仅仿真数据）。
  - 纯真实训练（仅真实数据）。
  - 朴素仿真-真实混合训练（无显式分布对齐）。
  - 其它常见的域自适应/对齐基线方法。
- **评估指标**：真实世界任务成功率（real-world success rate）。
- **亮点验证**：不仅评估常规场景，还测试了"仅在仿真中见过"场景的泛化能力（unseen-in-real scenarios）。

## 4. 资源与算力

- **论文元数据中未明确披露**：
  - 未提及具体 GPU 型号与数量。
  - 未给出训练时长、参数量、推理耗时等数据。
- 由于正文未能获取（PDF 被 CAPTCHA 拦截），无法判断正文是否包含实验环境细节。建议参考正文补充。

## 5. 实验数量与充分性

- **实验规模**：摘要中提到"challenging manipulation tasks"（多个任务）以及"30% 的真实成功率提升"，说明至少包含：
  - 多个任务上的主结果对比。
  - 跨域泛化（在仿真中独有场景）的额外测试。
- **可能包含的消融分析**（基于方法设计推断）：
  - OT 损失 vs. UOT 损失的对比（验证不平衡处理的必要性）。
  - 联合分布对齐 vs. 仅边际分布对齐的对比（验证核心洞察）。
  - 真实演示数据量的消融（验证"少量真实数据"假设）。
- **充分性评价**：从摘要角度看，实验覆盖了主结果、跨域泛化和关键消融维度；但因无法访问正文，无法判断统计显著性、随机种子数量、任务多样性等是否充分。
- **客观性**：方法直接以真实世界成功率为主要指标，较为客观；但缺乏正文细节，无法评估是否存在 cherry-picking 风险。

## 6. 主要结论与发现

- **有效性**：所提出的仿真-真实协同训练框架在少量真实演示条件下，相较纯仿真或纯真实训练，可获得**最高 30% 的真实世界成功率提升**。
- **泛化性**：策略能够泛化到**仅在仿真中见过的场景**（seen only in simulation），证明所学特征空间具备良好的域不变性。
- **机制有效性**：对齐**观测-动作联合分布**比仅对齐观测边际分布在域自适应上信号更丰富，是提升行为克隆跨域泛化的有效机制。
- **不平衡处理**：UOT 框架能有效处理仿真-真实样本量严重不平衡的问题。

## 7. 优点

- **核心洞察新颖**：将"对齐联合分布"作为域自适应的关键设计，区别于传统的边际分布对齐，提供了更丰富的监督信号。
- **不平衡建模细致**：引入 Unbalanced OT 处理数据量不匹配，比标准 OT 更贴合实际场景。
- **数据效率高**：显著降低对真实演示数据的依赖，降低采集成本。
- **双重贡献**：既提升常规场景性能，又能泛化到"仿真独有"场景，实用价值高。
- **框架统一性**：将 OT/UOT 损失嵌入协同训练流程，设计较为简洁自然。

## 8. 不足与局限

- **数据/任务覆盖未知**：由于无法访问正文，不清楚是否在多个机器人平台、多个任务类别、不同外观/动力学差异下做了全面测试。
- **真实演示数量依赖性未充分说明**：未明确"少量真实演示"具体是几条到几十条量级，以及在不同真实数据量下的性能曲线。
- **OT 损失的计算开销**：OT/UOT 在大规模数据上可能带来较高的计算成本，论文是否讨论了可扩展性存疑。
- **理论与经验结合不足**：未提及是否给出理论保证（如泛化误差上界、对齐效果的形式化分析）。
- **潜在偏差风险**：
  - 仿真环境的真实性（sim-to-real gap 的具体类型，如视觉、物理、动力学）若与真实平台差异过大，可能高估方法效果。
  - 任务选择和指标定义若由作者自行设计，存在评估偏差风险。
- **应用范围限制**：行为克隆范式本身受限于专家演示质量，且仅在"操作任务"上验证，未推广到导航、移动操作等更广泛的机器人任务。

（完）
