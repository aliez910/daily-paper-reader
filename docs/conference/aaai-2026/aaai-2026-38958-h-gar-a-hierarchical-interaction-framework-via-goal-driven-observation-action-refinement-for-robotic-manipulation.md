---
title: "H-GAR: A Hierarchical Interaction Framework via Goal-Driven Observation-Action Refinement for Robotic Manipulation"
title_zh: H-GAR：通过目标驱动的观察-动作精化的层次化交互框架用于机器人操作
authors: "Yijie Zhu, Rui Shao, Ziyang Liu, Jie He, Jizhihui Liu, Jiuru Wang, Zitong Yu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38958/42920"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向机器人操作的层次化目标驱动观察-动作精化
tldr: 现有视频与动作预测模型在处理观察和动作生成时缺乏目标引导，导致语义不匹配。本文提出H-GAR层次化交互框架，首先生成目标观察与粗略动作草图作为高层规划，再通过精化模块实现观察与动作的显式交互。实验表明该方法能够提升预测的语义一致性和操作行为连贯性，为机器人操作中的视觉预测提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 878, \"height\": 664, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1819, \"height\": 721, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 830, \"height\": 300, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 866, \"height\": 586, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1652, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38958/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1646, \"height\": 549, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 838, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1816, \"height\": 509, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1824, \"height\": 350, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 274, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 210, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38958/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 854, \"height\": 476, \"label\": \"Table\"}]"
motivation: 解决视频与动作预测中缺乏目标引导导致的语义不匹配问题。
method: 提出层次化框架，先生成目标观察和动作草图，再进行精化。
result: 提升了预测的语义一致性和行为连贯性。
conclusion: 提出了一种目标驱动的层次化交互框架用于机器人操作。
---

## Abstract
Unified video and action prediction models hold great potential for robotic manipulation, as future observations offer contextual cues for planning, while actions reveal how interactions shape the environment. However, most existing approaches treat observation and action generation in a monolithic and goal-agnostic manner, often leading to semantically misaligned predictions and incoherent behaviors.
To this end, we propose H-GAR, a Hierarchical interaction framework via Goal-driven observation-Action Refinement. To anchor prediction to the task objective, H-GAR first produces a goal observation and a coarse action sketch that outline a high-level route toward the goal. To enable explicit interaction between observation and action under the guidance of the goal observation for more coherent decision-making, we devise two synergistic modules. (1) Goal-Conditioned Observation Synthesizer (GOS) synthesizes intermediate observations based on the coarse-grained actions and the predicted goal observation. (2) Interaction-Aware Action Refiner (IAAR) refines coarse actions into fine-grained, goal-consistent actions by leveraging feedback from the intermediate observations and a Historical Action Memory Bank that encodes prior actions to ensure temporal consistency. By integrating goal grounding with explicit action-observation interaction in a coarse-to-fine manner, H-GAR enables more accurate manipulation. Extensive experiments on both simulation and real-world robotic manipulation tasks demonstrate that H-GAR achieves state-of-the-art performance.

---

## 论文详细总结（自动生成）

# H-GAR 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 现有统一的视频与动作预测模型将观察和动作生成视为**整体式（monolithic）且与目标无关（goal‑agnostic）** 的并行过程，缺乏对“动作如何影响观察”以及“任务目标如何引导轨迹”的显式建模。
- 这导致两个根本缺陷：
  - **目标无关的观察生成**：模型容易产生视觉上合理但与任务目标语义不一致的观察序列，降低可解释性与下游规划准确性。
  - **隐式的观察‑动作耦合**：观察和动作预测路径松散，缺少因果交互，削弱时间一致性并限制自适应能力。
- 本文提出 **H‑GAR（Hierarchical interaction framework via Goal‑driven observation‑Action Refinement）**，通过引入显式的**目标锚定**与**结构化双向交互**，使预测既语义对齐任务目标，又能利用观察和动作之间的相互促进作用，从而提升机器人操作的准确性与连贯性。

## 2. 论文提出的方法论

### 核心思想
采用**粗到细的分层精化**策略：首先预测一个**目标观察（goal observation）** 和一组**粗粒度动作草图**，勾勒出达到目标的高层路线；随后通过两个协同模块实现观察与动作的显式交互，逐步精化为细粒度、目标一致的动作序列。

### 关键技术细节
1. **整体流程**  
   - 输入：任务指令 \(I\)，历史观察序列 \(\{O_{t-h+1},...,O_t\}\)，以及掩码的未来观察。  
   - 使用预训练 VAE 将图像编码为潜在 tokens，CLIP 编码指令文本。  
   - Transformer 编码器融合历史、未来和指令 token 得到联合潜在特征 \(Z_{t+1:t+h'}\)。  
2. **目标与粗动作生成**  
   - 利用最终潜在 \(Z_{t+h'}\) 通过轻量视频扩散解码器预测目标观察 \(O_{t+h'}\)，损失 \(L_{goal}\)。  
   - 从联合潜在 \(Z_{t+1:t+h'}\) 通过扩散模型生成粗动作序列，损失 \(L_{coarse}\)。  
3. **Goal‑Conditioned Observation Synthesizer (GOS)**  
   - 引入可学习查询 \(Q_{Inter}\)，先与目标观察潜在做自注意力聚合目标语义，再与粗动作潜在做交叉注意力注入动作上下文，生成中间观察潜在 \(Z_{Inter}\)，损失 \(L_{inter}\)。  
4. **Interaction‑Aware Action Refiner (IAAR)**  
   - 建立**历史动作记忆库（Historical Action Memory Bank）**，存储过去精化后的动作潜在，采用相似度驱动的冗余压缩策略维持紧凑性。  
   - 粗动作先与记忆库做**交互层（HisInter）**（以记忆库为 K/V，粗动作为 Q），获取时间先验。  
   - 再与 GOS 输出的中间观察潜在 \(Z_{Inter}\) 做交叉注意力，融入语义视觉反馈，得到精化动作 \(\hat{A}\)，损失 \(L_{fine}\)。  
5. **总损失**  
   \(L_{total} = L_{goal} + L_{coarse} + L_{inter} + L_{fine}\)，所有损失均为扩散去噪误差。

### 算法流程（文字说明）
1. 编码历史与掩码未来观察及指令 → 联合潜在表示。  
2. 从联合潜在解码出目标观察和粗动作序列（扩散）。  
3. GOS 以目标观察潜在和粗动作潜在为条件合成中间观察潜在（自注意力 + 交叉注意力）。  
4. IAAR 利用历史动作记忆库和中间观察潜在，通过两次注意力（历史交互 + 观察交叉注意）精化粗动作。  
5. 记忆库按相似性合并最邻近的动作潜在以控制大小。  
6. 联合训练所有扩散损失。

## 3. 实验设计

- **模拟环境**  
  - 单任务：**PushT**（推T形块任务）。  
  - 多任务：**PushT‑M**（PushT变体）、**Libero‑10**（10种操作任务）。  
- **真实世界**  
  - 平台：Cobot Agilex ALOHA。  
  - 任务：物体放置（Object Placement）、抽屉操作（Drawer Manipulation）、毛巾折叠（Towel Folding）、鼠标排列（Mouse Arrangement）。  
- **对比方法**  
  - 基线包括 Diffusion Policy‑C/T、UniPi、OpenVLA、STAR、CoT‑VLA、SpatialVLA、PD‑VLA、UVA 等（带*为原文报告，†为复现结果）。  
- **评估指标**  
  - 主要：**成功率（SR）** 和排名（RK）；真实世界长时任务报告阶段完成率。  
  - 观察生成质量：**FVD（Fréchet Video Distance）**。  
- **实验覆盖**  
  - 主实验结果（Table 1 模拟，Table 2 真实世界）。  
  - 观察生成对比（Table 3，不同自回归步数）。  
  - 消融研究（Table 4‑6）：组件消融（GOS/IAAR/记忆库）、目标策略消融、记忆库大小与更新策略消融。  
  - 相关性分析（Fig. 4）：FVD 与成功率的关系。  
  - 定性可视化（Fig. 5‑6）：中间观察预测和执行轨迹比较。

## 4. 资源与算力

论文**未明确说明**使用的 GPU 型号、数量及训练时长。仅在致谢中提及计算资源由“松山湖 HPC 中心（Great Bay University）”支持，但未提供具体硬件配置与训练时间等细节。

## 5. 实验数量与充分性

- **实验数量**：涵盖 2 种模拟设置（单/多任务）+ 4 个真实世界任务，超过 10 个基线对比，6 组消融表格 + 若干可视化分析，实验量充足。  
- **充分性与公平性**：  
  - 模拟实验遵循标准协议（PushT/Libero‑10），且复现部分基线（†标记）以控制变量。  
  - 消融实验系统性地验证了每个模块（GOS、IAAR、记忆库大小与更新策略）的贡献，客观揭示了各组件作用。  
  - 真实世界任务多样且具长时程挑战，结果可信。  
- **局限性**：真实世界任务数量有限（4 个），验证范围仍可扩大；未报告计算效率或运行时间，难以全面评估实用性。

## 6. 论文的主要结论与发现

- H‑GAR 在**所有模拟和真实世界任务上均取得最高成功率**，显著优于现有 SOTA 方法（如 UVA、PD‑VLA 等）。  
- 显式目标观察生成作为语义锚点，有效缓解了语义漂移，使中间观察与任务目标保持一致。  
- GOS 和 IAAR 的协同作用显著提升性能：两者搭配使用效果最佳，任一组件的缺失均导致成功率下降。  
- 历史动作记忆库（尤其基于相似度的压缩策略）能进一步精化动作，增强时间一致性与最终表现。  
- 观察生成质量（FVD）与任务成功率呈**强负相关**（Fig.4），说明高质量视觉预测对下游操作至关重要。  
- 定性可视化显示 H‑GAR 能生成语义连贯的中间观察，并在真实长时任务中完整执行所有子阶段，而基线方法在关键步骤失败。

## 7. 优点

- **目标锚定与粗到细层次**：首次将目标观察显式地作为生成过程的一部分，使预测固有地与任务意图对齐，解决了现有方法目标无关的弊端。  
- **结构化双向交互**：GOS 和 IAAR 通过注意力机制实现观察与动作的相互调节，建立了因果明确的生成路径，优于并行或松耦合范式。  
- **历史动作记忆库**：利用压缩的记忆提供时间先验，使动作精化获得行为一致性，且相似度合并策略既控制内存又保留多样性。  
- **广泛的实验验证**：覆盖模拟单/多任务及真实世界的多种操作，包括长时程、多阶段任务，实验设计与消融分析严谨全面。  
- **可视化充分直观**：展示了目标预测、中间帧生成以及真实执行对比，增强了方法可解释性。

## 8. 不足与局限

- **计算资源未报告**：缺少 GPU 型号、数量、训练时间等关键效率指标，难以评估方法的实际部署成本。  
- **观察生成质量可能受限**：方法依赖目标观察的准确预测，若目标预测失败（如复杂场景），后续中间观察和精化动作可能一起恶化；论文未充分分析目标预测失败时的鲁棒性。  
- **记忆库机制开销**：相似度计算与合并操作增加额外推理负担，且阈值（大小和合并频率）需人工设定，论文未深入讨论其对实时性的影响。  
- **真实世界任务种类有限**：仅 4 个任务，且均基于 ALOHA 平台，未涵盖更复杂（如灵巧手、动态环境）或更多样（如多物体杂乱场景）的操作，泛化性仍需更多验证。  
- **基线与复现条件**：部分基线结果来自原文或复现，复现细节（如超参数、种子、硬件）未完整披露，可能引入不可控的对比偏差。  
- **消融实验样本量**：虽然消融表格清晰，但未报告多次重复的统计显著性（如均值、方差、置信区间），结果的稳定性不够透明。  
- **应用限制**：方法目前聚焦于短程到中程任务，对于需要复杂推理或长时间规划的任务，粗‑细结构可能仍面临累积误差问题（论文未深入讨论）。

（完）
