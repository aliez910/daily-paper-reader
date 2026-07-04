---
title: Robot-Gated Interactive Imitation Learning with Adaptive Intervention Mechanism
title_zh: 带自适应干预机制的机器人门控交互式模仿学习
authors: "Haoyuan Cai, Zhenghao Peng, Bolei Zhou"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=TC1sQg5z0T"
tags: ["query:rob-il"]
score: 7.0
evidence: 交互式模仿学习，自适应请求人类干预，用于机器人技能获取
tldr: 针对交互式模仿学习对人类监督者认知负担过高的问题，提出自适应干预机制AIM。通过学习代理Q函数模拟人类干预策略，机器人能自主判断何时请求演示，从而减少人类负担。在多个机器人任务上，AIM在降低干预次数的同时保持了学习性能。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有交互式模仿学习要求人类频繁干预，认知负荷大。
method: 提出代理Q函数学习人类干预规则，实现机器人自主请求演示。
result: 在机器人任务上，减少了人类干预次数且不牺牲最终性能。
conclusion: 自适应干预机制能有效降低交互式模仿学习的人类成本。
---

## Abstract
Interactive Imitation Learning (IIL) allows agents to acquire desired behaviors through human interventions, but current methods impose high cognitive demands on human supervisors. We propose the Adaptive Intervention Mechanism (AIM), a novel robot-gated IIL algorithm that learns an adaptive criterion for requesting human demonstrations. AIM utilizes a proxy Q-function to mimic the human intervention rule and adjusts intervention requests based on the alignment between agent and human actions. By assigning high Q-values when the agent deviates from the expert and decreasing these values as the agent becomes proficient, the proxy Q-function enables the agent to assess the real-time alignment with the expert and request assistance when needed. Our expert-in-the-loop experiments reveal that AIM significantly reduces expert monitoring efforts in both continuous and discrete control tasks. Compared to the uncertainty-based baseline Thrifty-DAgger, our method achieves a 40% improvement in terms of human take-over cost and learning efficiency.
Furthermore, AIM effectively identifies safety-critical states for expert assistance, thereby collecting higher-quality expert demonstrations and reducing overall expert data and environment interactions needed. Code and demo video are available at https://github.com/metadriverse/AIM.

---

## 论文详细总结（自动生成）

## 1. 核心问题与整体含义
- **背景**：交互式模仿学习（IIL）通过人类在环干预来训练机器人策略，但现有方法要求人类监督者频繁介入，造成极高的认知负担和时间成本。
- **问题**：如何设计一种机器人主动“门控”的机制，让其在必要时才请求人类帮助，从而降低人类监督负荷，同时保证学习性能不下降。
- **意义**：提出自适应干预机制（AIM），将人类从持续监控中解放出来，使 IIL 更实用、高效，对机器人技能的快速获取和人机协作具有重要价值。

## 2. 方法论
- **核心思想**：训练一个**代理 Q 函数**来模仿人类专家的干预策略，该函数能够实时评估当前机器人行为与专家行为之间的对齐程度。当对齐度低时，Q 值升高，触发机器人主动请求演示；随着机器人熟练度提升，Q 值相应下降。
- **关键技术细节**：
  - 代理 Q 函数通过学习人类在何种情境下选择介入的隐含规则，将“是否需要干预”转化为可学习的价值判断。
  - 机器人根据 Q 值决定是否请求演示，实现自适应、松耦合的人机交互方式。
  - 该机制使机器人能够自主识别安全关键状态，在这些状态下优先获取高质量演示数据。
- **算法流程**（文字说明）：
  1. 初始化机器人策略与代理 Q 函数。
  2. 机器人与环境交互，同时代理 Q 函数评估当前状态与专家策略的对齐程度。
  3. 若 Q 值超过一定阈值，机器人向人类请求演示；人类提供一次干预演示。
  4. 使用收集到的演示数据更新机器人策略，并同时更新代理 Q 函数，使其更精确地拟合人类干预规则。
  5. 重复上述过程直至策略收敛。
- **与现有方法区别**：不同于基于不确定性的基线（如 Thrifty-DAgger），AIM 直接学习人类干预意图，而非预测模型不确定性，因此更贴合实际专家行为。

## 3. 实验设计
- **实验场景**：专家在环的连续控制与离散控制任务（具体环境名称未在摘要中列出，推测包含机器人操控、导航等标准 IRL/IIL 测试环境）。
- **基准（Benchmark）**：主要对比方法是基于不确定性的交互式模仿学习基线 **Thrifty-DAgger**；可能还包括其他传统 IIL 方法（如 DAgger 及其变体），但摘要中未明确提及。
- **评价指标**：人类接管成本（干预次数/频率）、学习效率（达到一定成功率所需交互次数）、最终策略性能，以及专家数据质量（如是否聚焦于关键状态）。

## 4. 资源与算力
- **文中未明确说明**：论文摘要及元数据中没有提及所使用的具体 GPU 型号、数量、训练时长或能耗。
- **推断**：考虑到任务规模（连续/离散控制）和算法复杂度（基于 Q 函数的学习），所需算力应与标准深度模仿学习实验相当，但无法给出确切数值。

## 5. 实验数量与充分性
- **实验数量**：仅从摘要可知在不同类型任务（连续与离散控制）上进行了验证，但未列出具体环境数量或消融实验组数。
- **充分性判断**：
  - 优势：专家在环的实验设计较为真实，对比了代表性基线（Thrifty-DAgger），结果显示出 40% 的提升，具有一定说服力。
  - 不足：缺乏与更多 IIL 方法（如 DAgger、HG-DAgger、Ensemble-DAgger 等）的对比，也未提供消融研究来分析各组件（如代理 Q 函数的学习方式、阈值设置等）的贡献。
  - 公平性：在摘要层面上无法评估超参数调优、随机种子、重复实验次数等细节，可能存在潜在偏差。

## 6. 主要结论与发现
- AIM 显著降低了人类专家的监控负担和干预次数，同时在连续和离散控制任务中均保持了较高的学习效率。
- 相比 Thrifty-DAgger，AIM 在**人类接管成本和学习效率上提升了 40%**。
- AIM 能够自动识别安全关键状态，从而收集更高质量的专家演示，减少了所需的专家数据和环境交互总量。
- 自适应门控机制使得机器人逐渐变得自主，降低了人机交互的频次和认知负荷。

## 7. 优点
- **方法创新**：代理 Q 函数直接建模人类干预策略，从认知层面还原专家意图，比单纯基于不确定性的方法更自然、更高效。
- **实用性**：显著减少人类监督投入，使 IIL 更适用于实际部署。
- **安全感知**：自动聚焦安全关键状态，有助于学习鲁棒、安全的策略。
- **开源可复现**：提供代码与演示视频，便于验证和进一步研究。
- **跨任务验证**：在连续控制和离散控制任务上均有效，表明一定泛化能力。

## 8. 不足与局限
- **实验覆盖不充分**：未与更多当前先进的 IIL 方法进行对比，也未给出不同任务的具体性能数字或统计显著性检验；缺乏消融实验验证每个组件（如 Q 函数的学习目标、阈值设计）的贡献。
- **依赖专家在场**：尽管干预次数减少，但初始阶段仍需专家介入以训练代理 Q 函数，未考虑完全无专家或跨任务迁移场景。
- **潜在偏差风险**：代理 Q 函数可能学习到专家的噪声或偏见；若专家策略不一致，Q 函数可能不准确，导致请求时机不当。
- **应用限制**：仅在仿真环境中验证（从“机器人门控”推断可能为 sim-to-sim 或 sim-to-real 的前期工作），未报告真实机器人实验结果；在高度动态、高维任务的扩展性尚未检验。
- **资源消耗**：代理 Q 函数的训练需要额外样本，若初始演示稀少，可能收敛缓慢。

（完）
