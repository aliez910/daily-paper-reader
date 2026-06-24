---
title: "D²PPO: Diffusion Policy Policy Optimization with Dispersive Loss"
title_zh: D²PPO：带有分散性损失的扩散策略优化
authors: "Guowei Zou, Weibing Li, Hejun Wu, Yukun Qian, Yuhang Wang, Haitao Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38959/42921"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操纵模仿学习的扩散策略优化
tldr: 扩散策略在模拟多模态动作分布方面表现优异，但存在表征坍缩问题，即相似观测映射到不可区分特征，影响复杂操纵任务的性能。本文提出D²PPO，通过分散性损失正则化将批内所有隐藏表示作为负样本对，强制网络学习具有区分度的表示。实验证明该方法有效缓解了表征坍缩，显著提升了扩散策略在精细操纵任务上的表现。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 890, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1819, \"height\": 752, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1826, \"height\": 891, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 378, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1831, \"height\": 450, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38959/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1792, \"height\": 847, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38959/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 689, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38959/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1705, \"height\": 496, \"label\": \"Table\"}]"
motivation: 扩散策略的表示坍缩导致相似观测的特征不可区分，限制了对微妙但关键操作差异的处理能力。
method: 提出D²PPO，引入分散性损失，将批次内所有隐藏表示作为负样本对进行正则化，促使网络学习判别性特征。
result: 显著缓解了表示坍缩，在复杂机器人操纵任务上提升了动作预测的准确性和鲁棒性。
conclusion: 分散性正则化为扩散策略提供了一种简单有效的改进方式，适用于需要对细微观测差异做出区分的高精度操纵场景。
---

## Abstract
Diffusion policies excel at robotic manipulation by naturally modeling multimodal action distributions in high-dimensional spaces. Nevertheless, diffusion policies suffer from diffusion representation collapse: semantically similar observations are mapped to indistinguishable features, ultimately impairing their ability to handle subtle but critical variations required for complex robotic manipulation. To address this problem, we propose D²PPO (Diffusion Policy Policy Optimization with Dispersive Loss). D²PPO introduces dispersive loss regularization that combats representation collapse by treating all hidden representations within each batch as negative pairs. D²PPO compels the network to learn discriminative representations of similar observations, thereby enabling the policy to identify subtle yet crucial differences necessary for precise manipulation. In evaluation, we find that early-layer regularization benefits simple tasks, while late-layer regularization sharply enhances performance on complex manipulation tasks. On RoboMimic benchmarks, D²PPO achieves an average improvement of 22.7% in pre-training and 26.1% after fine-tuning, setting new SOTA results. In comparison with SOTA, the results of real-world experiments on a Franka Emika Panda robot show the excitingly high success rate of our method. The superiority of our method is especially evident in complex tasks.

---

## 论文详细总结（自动生成）

# D²PPO 论文详细总结

## 1. 核心问题与整体含义（研究动机与背景）

- **问题**：扩散策略（Diffusion Policy）在机器人操纵中能够自然建模高维连续动作的多模态分布，但作者发现其在复杂操纵任务中成功率低。根本原因是**扩散表示坍缩（diffusion representation collapse）**：语义上相似的观测被编码到几乎不可区分的特征表示中，导致策略无法区分细微但关键的差异，进而生成错误动作。
- **背景**：传统扩散策略只依赖重建损失（如去噪损失）优化，忽视了中间隐藏表示的质量与多样性，使得不同观测的隐藏表示聚拢成相似簇，丧失判别力。这一现象在精细操纵（如抓取姿态选择、零件插入）中尤其致命。
- **意义**：解决表示坍缩是提升扩散策略在复杂操纵任务上性能的关键。论文提出的方法无需额外预训练、模型参数或外部数据，即可增强表示判别性，具有很强实用价值。

## 2. 方法论：核心思想、关键技术细节与流程

- **核心思想**：通过在预训练阶段引入**分散性损失（dispersive loss）** 正则化，将批次内所有隐藏表示视为负样本对，强制它们彼此远离，从而鼓励网络学习具有区分度的特征。后续使用 PPO 微调时，这些增强的表示能提升策略优化效率。
- **关键技术细节**：
  - **分散性损失**：源自对比学习 InfoNCE，但**去除正样本对齐项**，仅保留分散项。设计了三种变体：
    1. **InfoNCE-L2**：基于欧氏距离的平方，`L_disp = log E_{i,j}[exp(-||h_i - h_j||^2/τ)]`。
    2. **InfoNCE-Cosine**：基于余弦差异，`L_disp = log E_{i,j}[exp(- (1 - cos(h_i, h_j))/τ)]`。
    3. **Hinge**：基于铰链损失，`L_disp = E_{i,j}[max(0, ε - D(h_i, h_j))^2]`，强制最小间隔 ε。
  - **两阶段训练框架**：
    - **Stage 1 – 增强预训练**：优化 `L_pre-train = L_diff + λ L_disp`，`L_disp` 在去噪步数 k 上平均，并对 MLP 去噪网络的中间隐藏层施加正则。λ 控制正则强度（实验中 λ = 0.5 最优）。
    - **Stage 2 – 策略梯度微调**：使用 PPO，在扩散 MDP 框架下计算梯度（对去噪链进行重要性采样），保留预训练学到的表示结构，最大化任务回报。
  - **层选择策略**：实验发现，简单任务（Lift）从早期层正则受益，复杂任务（Transport）从晚期层正则受益。中等难度任务（Square）则中间层最优。
- **算法流程概述**：
  1. 使用 Vision Transformer（ViT）编码视觉观测。
  2. 在扩散去噪过程中，选取特定中间层特征计算分散性损失。
  3. 交替优化扩散损失和分散性损失直到收敛。
  4. 加载预训练权重，在环境中用 PPO 在线微调，更新策略参数。

## 3. 实验设计：数据集、基准与对比方法

- **模拟器与基准**：MuJoCo 物理引擎，**RoboMimic** 基准，包含四个不同复杂度的操纵任务：
  - Lift（简单）、Can（中等）、Square（高）、Transport（最高）。
- **数据集**：使用 RoboMimic 提供的专家演示数据（human demonstrations）进行预训练。
- **对比方法**：
  - **预训练阶段**：主要与 DPPO（基线）对比，并评估五种分散损失变体在跨任务上的提升。
  - **微调阶段**：与 8 种 SOTA 方法比较，包括：
    - LSTM-GMM、IBC、BET、DiffusionPolicy-C、DiffusionPolicy-T、DPPO、MTIL（10-step & Full History）。
- **真实机器人实验**：在 **Franka Emika Panda** 机器人上部署，对四个 RoboMimic 任务各执行 100 次试验，并与 DPPO（无分散损失）进行可视化对比。

## 4. 资源与算力

- **文中未明确说明**具体使用的 GPU 型号、数量或训练时长。
- 仅在算法描述中提及使用标准的扩散模型训练设置，但未提供算力开销的量化信息（例如 GPU 天数、显存需求等）。这是论文在资源报告上的一个缺失。

## 5. 实验数量与充分性

- **实验数量**：
  - 预训练阶段：在 4 个任务上评估了 5 种分散损失变体，共计 20+ 组结果（含不同层选择）。
  - λ 消融：在 Square 任务上对 λ 进行 6 个值（0.0–1.0）的探索，确定最优为 0.5。
  - 微调阶段：在 4 个任务上与 8 种方法对比，每组训练曲线均展示了多轮的平均与标准差。
  - 真实实验：每任务 100 次试验，总计 400 次真实操纵。
- **充分性分析**：
  - 正面：任务难度梯度覆盖完整，模拟与真实实验相互验证；消融实验全面（损失变体、系数、层位置）；统计指标包含成功率、均值、中位数、标准差及排名，结果客观。
  - 潜在不足：未在更多样化的领域（如移动操作、多指灵巧手）验证；对比方法中缺少一些最新的大规模预训练策略（如 RT-2 类），但限于基准条件可理解。

## 6. 主要结论与发现

- **表示坍缩是扩散策略在复杂操纵失败的根本原因**：通过聚类分析与学习曲线对比，确认了表示坍缩导致动作多样性不足。
- **分散性损失有效缓解表示坍缩**：相比基线，预训练平均提升 **22.7%**，微调后平均提升 **26.1%**。
- **层选择与任务难度正相关**：简单任务早期层正则优，复杂任务晚期层正则优，为实际调参提供指导。
- **D²PPO 在 RoboMimic 上达到 SOTA**：平均成功率 94%，排名第一，且在 Transport 等最难任务上从 60%（DPPO）提升至 87%。
- **真实机器人验证成功**：在 Franka Emika Panda 上实现所有任务高成功率，对比 DPPO 在 Square 任务上的失败案例，证明了分散表示对精细操作的关键作用。

## 7. 优点

- **方法简洁高效**：分散性损失去除了对比学习中对正样本对的需求，无额外模型参数或预训练阶段，即插即用。
- **两阶段框架合理**：先提升表示质量再策略优化，避免微调过程中表示退化。
- **分析深入**：通过特征可视化、聚类和层效应规律揭示了表示坍缩和正则化的机制，具有很强的启发性。
- **实验充分公平**：使用同一基准、一致评价指标，并与多种基线对比；真实实验验证了迁移性。
- **通用性强**：λ 值在跨任务上仅需简单调参，层选择也可根据复杂度经验确定。

## 8. 不足与局限

- **算力开销未报告**：无 GPU 型号、训练时间等资源信息，难以复现和比较效率。
- **任务领域局限**：仅在桌面操纵任务（RoboMimic）上验证，未涉及全身运动、移动操作或复杂装配等场景。
- **调参依赖**：λ 与层选择需要根据任务复杂度手动调整，可能在实际应用中需额外调试成本。
- **泛化性隐忧**：论文未讨论分散性损失在不同策略架构（如基于 RNN、Transformer 的策略）或不同观察模态（如纯状态输入）下的表现。
- **可能过度分散**：强制所有样本远离可能损失某些必要相似性，对于需要利用相似观测共享特征的任务可能产生副作用（论文中的 λ 消融也显示过大 λ 会降低性能）。
- **与最新大规模模型的对比缺失**：虽然 RoboMimic 基准限制了方法类别，但与 RT-1/RT-2、Octo 等大规模预训练模型的间接比较未提及。

（完）
