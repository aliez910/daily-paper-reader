---
title: "Rethinking Progression of Memory State in Robotic Manipulation: An Object-Centric Perspective"
title_zh: 重新思考机器人操作中的记忆状态进展：以物体为中心的视角
authors: "Nhat Chung, Taisei Hanyu, Toan Nguyen, Huy Le, Frederick Bumgarner, Duy Minh Ho Nguyen, Khoa Vo, Kashu Yamazaki, Chase Rainwater, Tung Kieu, Anh Nguyen, Ngan Le"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37337/41299"
tags: ["query:rob-il"]
score: 8.0
evidence: 针对物体级记忆挑战的机器人操作新基准
tldr: 现有机器人操作基准大多假设马尔可夫性，忽略了物体历史对决策的关键作用。本文提出LIBERO-Mem，一个非马尔可夫任务套件，包含短时和长时任务，要求智能体跟踪物体的状态和交互历史，为评估操作策略的长期记忆能力提供了新的挑战和方向。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37337/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1755, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37337/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1817, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37337/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1324, \"height\": 532, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37337/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 883, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37337/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 881, \"height\": 1340, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37337/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 884, \"height\": 595, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37337/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 841, \"height\": 595, \"label\": \"Table\"}]"
motivation: 现有操作基准忽略了物体级别的部分可观测性，策略缺乏持久记忆导致失败。
method: 设计LIBERO-Mem任务套件，包含短时和长时非马尔可夫操作任务。
result: 实验表明现有visuomotor策略在LIBERO-Mem上表现不佳，凸显了记忆挑战。
conclusion: 物体级记忆是复杂操作任务的关键能力，需要新的方法和基准来推动研究。
---

## Abstract
As embodied agents operate in increasingly complex environments, the ability to perceive, track, and reason about individual object instances over time becomes essential, especially in tasks requiring sequenced interactions with visually similar objects. In non-Markovian settings, critical decision cues lie in object histories rather than the current scene. Without persistent memory of prior interactions (what was used, where it was placed, or how it changed), visuomotor policies may fail, repeat past actions, or overlook completed ones. To surface this challenge, we introduce LIBERO-Mem, a non-Markovian task suite for stress-testing robotic manipulation under object-level partial observability. It combines short- and long-horizon object tracking with temporally sequenced subgoals, requiring reasoning beyond the current frame. However, vision-language-action (VLA) models often struggle in such settings, with token scaling quickly becoming intractable even for tasks spanning just a few hundred frames. We propose Embodied-SlotSSM, a slot-centric VLA framework built for temporal scalability. It maintains spatio-temporally consistent slot identities and leverages them through two mechanisms: (1) slot-state-space modeling for reconstructing short-term history, and (2) a relational encoder to align the input tokens with action decoding. Together, these components enable temporally grounded, context-aware action prediction. Experiments show Embodied-SlotSSM's baseline performance on LIBERO-Mem and general tasks, offering a scalable solution for non-Markovian reasoning in object-centric policies.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：现有机器人操作策略（尤其是视觉-语言-动作模型，VLA）通常假设环境是马尔可夫性的（Markovian），即当前动作仅由当前观测决定。但在实际任务中，智能体需要根据与物体的历史交互来做出正确决策，例如：是否已经抓取过某个物体、物体之间的相对顺序如何变化等。这种情况下，相同的视觉输入可能对应不同的语义状态，即存在物体级的部分可观测性（POMDP）。
- **研究背景**：现有的机器人操作基准（如LIBERO、RLBench、RoboCasa等）多建立在马尔可夫假设之上，缺乏对物体历史记忆的测试；而少数的记忆基准（如MemoryBench、MIKASA-Robo）也未系统性地关注物体身份模糊性、长时依赖和物体级交互历史。因此，论文旨在提出一个专门评估非马尔可夫物体级记忆的基准，并探索一种基于物体中心记忆的策略框架。

## 2. 论文提出的方法论：核心思想、关键技术细节

- **核心思想**：提出 Embodied-SlotSSM，一种以 slot（槽）为中心的 VLA 框架，通过维持时空一致的 slot 表征来追踪物体身份和状态，从而在部分可观测性下支持基于记忆的决策。框架主要由三部分组成：
  1. **瞬态记忆（Transient Memory）**：通过 Slot Attention 实现物体定位和绑定，并使用时序对比损失增强跨帧一致性；采用 SlotSSM（基于状态空间模型）对每个 slot 的短期历史进行建模（预测过去 p 帧和未来 q 帧的物体潜在状态），从而捕捉物体运动和临时依赖。
  2. **持久记忆与动作控制**：通过 Slot Fusion 模块将当前 slot、预测的下一个 slot 以及可选的 oracle 子目标嵌入融合，形成包含时间上下文的物体级表征；再通过 Relation Encoder（交叉注意力）生成关系 token，最终由 VLA 解码器依据关系 token、slot 动态和任务语言嵌入预测动作。
  3. **非马尔可夫动作预测**：动作生成条件为 $P_\theta(a_t | \{r^{(j)}_t\}, \{d^{(j)}_t\}, l)$，其中 $d^{(j)}_t$ 为融合后的 slot 动态，$r^{(j)}_t$ 为关系 token，l 为任务指令，从而实现基于历史的上下文感知决策。
- **关键技术细节**：
  - Slot Attention 初始化策略：t=0 时随机初始化，t>0 时使用上一帧最终的 slot 输出，保持身份一致性。
  - 状态空间模型采用块对角矩阵，由各 slot 独立参数化以提高模块化。
  - 默认 slot 数 K=16。
  - 使用 Past MLP 解码窗口内未来帧的物体潜在表示，提供重建监督。
- **公式/算法流程（文字说明）**：输入图像序列 → 视觉编码器 → Slot Attention 得到 slot 集合 → SlotSSM 对每个 slot 进行自回归建模并预测窗口内的 latent → Slot Fusion 整合当前 slot、预测 slot 和子目标嵌入 → Relation Encoder 生成关系 token → 联合动作解码输出动作。

## 3. 实验设计

- **数据集与场景**：
  - **LIBERO-Goal**：通用机器人操作基准，包含 10 个任务（如放置碗、开抽屉等），用于评估一般任务性能。
  - **LIBERO-Mem**：论文新提出的非马尔可夫基准，包含 10 个任务，涵盖四种记忆维度：物体运动 (OM)、物体顺序 (OS)、物体关系 (OR)、物体遮挡 (OO)。任务要求跟踪物体交互历史（如重复拿放若干次、按序移动物体、遮挡下识别等）。
- **Benchmark 对比方法**：
  - **基线**：π0（密集 token，h=1）、SlotVLA（h=1 和 h=8，即仅用当前帧或 8 帧输入）、OpenVLA（文中记为 SlotVLA？实际 SlotVLA 是物体中心版本，h 表示历史帧数）。
  - **论文方法**：Embodied-SlotSSM（实验中使用了一个接收 oracle 子目标标记的版本，称为 Naive E-SlotSSM）。
- **评估指标**：
  - LIBERO-Goal：成功率（success rate），每个任务重复 N=20 个随机种子。
  - LIBERO-Mem：子目标完成率（subgoal completion percentage），同样 N=20 个 seed。
- **实验规模**：共 10 个一般任务 + 10 个非马尔可夫任务，每个方法在各任务上运行 20 次（seed），报告平均指标。另外有定性可视化 slot 注意力图。

## 4. 资源与算力

- **文中未明确说明使用的具体 GPU 型号、数量、训练时长**。只在实验设置中提到每个任务重复 N 个 seed，但未提及模型训练的计算资源或推理成本。因此，无法总结具体的算力细节。

## 5. 实验数量与充分性

- **实验数量**：
  - LIBERO-Goal：10 个任务，每个任务 20 个 seed，报告成功率。
  - LIBERO-Mem：10 个任务，每个任务 20 个 seed，报告子目标完成率。
  - 定性可视化（slot attention over time）展示在单个任务 T1 上。
  - 没有单独的消融实验（如去除 SlotSSM 或对比不同 slot 设计），仅有方法间的横向比较。
- **充分性与公平性**：
  - 对比方法包括不同历史帧数的变体，但论文方法（Naive E-SlotSSM）利用了 oracle 子目标信息，其他方法没有，因此对比并非完全公平——实际方法在非马尔可夫任务上的优势部分来自于额外的子目标监督。但论文也指出了这一点（局限性）。
  - 在 LIBERO-Goal 上，Naive E-SlotSSM 不依赖 oracle 子目标？从实验描述看，Naive E-SlotSSM 是在 LIBERO-Mem 中使用 oracle 子目标的版本；一般任务上是否使用 oracle 未明确。但表述中 LIBERO-Goal 上 Naive E-SlotSSM 取得了最好结果，这可能是由于其 slot 记忆机制仍然有效。
  - 总体而言，实验覆盖了关键对比，但缺乏对记忆模块不同组件的消融、不同 slot 数量、长期记忆延展性等方面的深入分析，实验充分性一般。

## 6. 论文的主要结论与发现

- 现有 VLA 模型（π0、SlotVLA）在 LIBERO-Mem 上近乎无法完成子目标（平均成功率为 0%~5%），暴露了它们在非马尔可夫物体级记忆上的根本局限。
- 提出的 Embodied-SlotSSM（Naive E-SlotSSM）在 LIBERO-Mem 上平均子目标完成率达到 14.8%，虽然绝对数值不高（部分任务仍为0%），但显著优于基线，尤其在有重复动作和物体关系调整的任务上（如 T1: 50%, T3: 33.3%, T9: 30%）。
- 在一般任务（LIBERO-Goal）上，Naive E-SlotSSM 平均成功率 83.0%，高于基线 SlotVLA（75.5%）和无记忆的版本，表明物体中心记忆对一般操作也有帮助。
- 定性分析显示，Embodied-SlotSSM 能维持对相同物体实例的稳定注意力跟踪，体现了物体持久性（object permanence）。

## 7. 优点

- **问题定义清晰**：明确指出了现有基准忽视的物体级非马尔可夫问题，并设计了针对性的基准 LIBERO-Mem，包含多种记忆维度（运动、顺序、关系、遮挡），对短期和长期记忆都有测试。
- **方法新颖**：将槽状态空间模型（SlotSSM）首次引入机器人 VLA 策略，实现了模块化、可扩展的物体中心记忆，通过 slot 的初始化传递和时序对比损失实现身份一致性，结合瞬态与持久记忆进行动作解码。
- **可扩展性**：使用少量 slot token（16个）即可编码场景，对比使用密集 token（256个）的 OpenVLA 等方法更加适合长序列任务，避免了 token 数量随帧数线性增长的问题。
- **实验结果支持结论**：在 LIBERO-Goal 和 LIBERO-Mem 上均展示了优于基线的结果，验证了物体中心记忆在非马尔可夫场景下的必要性。

## 8. 不足与局限

- **实验场景局限**：LIBERO-Mem 和 LIBERO-Goal 均为模拟环境，无真实机器人实验，其泛化到物理世界的可靠性未知。
- **依赖 oracle 子目标**：论文中报告的 Naive E-SlotSSM 实际使用了 oracle 文本子目标作为输入（例如“bowl 1 on plate 3”），这在实际任务中通常无法获得，导致方法自主推理能力不足。论文承认这是一个“弱基线”。
- **性能仍然较低**：即使在 LIBERO-Mem 上最好的方法平均子目标完成率也仅 14.8%，多数任务仍然失败，说明非马尔可夫物体级记忆仍是极具挑战性的开放问题。
- **消融实验缺失**：没有对记忆模块（如 SlotSSM、时序对比损失、Slot Fusion 等）进行消融，无法量化各组件贡献。
- **内容与表述**：部分实验对比不够公平（oracle 信息），可能高估方法相对优势。另外，没有讨论模型在不同任务类型（OM/OS/OR/OO）上的性能差异，也未进行长时延展性（如更长的帧数）的压力测试。
- **计算资源未报告**：缺乏训练成本分析，不利于复现和效率比较。

（完）
