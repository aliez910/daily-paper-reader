---
title: "LIBERO-Plus: A Progressive Robustness Benchmark for Visual-Language-Action Models"
title_zh: LIBERO-Plus：面向视觉-语言-动作模型的渐进式鲁棒性评测基准
authors: "Fei, Senyu, Wang, Siyin, Shi, Junhao, Dai, Zihao, Cai, Jikun, Qian, Pengfang, Ji, Li, He, Xinzhe, Zhang, Shiduo, Fei, Zhaoye, Fu, Jinlan, Gong, Jingjing, Qiu, Xipeng"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Fei_LIBERO-Plus_A_Progressive_Robustness_Benchmark_for_Visual-Language-Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 10.0
evidence: 对机器人操作基准上VLA模型进行多维扰动的鲁棒性评测
tldr: 本文针对当前VLA模型在机器人操作基准上报告的成功率虚高、鲁棒性不足的问题，提出了渐进式鲁棒性评测框架LIBERO-Plus。该框架在七个维度（物体布局、相机视角、机器人初始状态、语言指令、光照、背景纹理与传感器噪声）上施加受控扰动。论文系统分析了十个最先进的VLA模型，发现它们在多维扰动下普遍存在一致的鲁棒性短板，为复杂操作任务上的模仿学习评测提供了更细粒度的工具。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1763, \"height\": 741, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 671, \"height\": 668, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 789, \"height\": 728, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 867, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 429, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1676, \"height\": 560, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 694, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 857, \"height\": 564, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1807, \"height\": 478, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-fei-libero-plus-a-progressive-robustness-benchmark-for-visual-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1567, \"height\": 1022, \"label\": \"Table\"}]"
motivation: 现有VLA评测基准对鲁棒性覆盖窄，难以揭示模型在扰动下的真实失败模式。
method: 构建LIBERO-Plus基准，在七个维度上对VLA模型施加自动且细粒度的受控扰动评测。
result: 对十个SOTA模型进行系统分析，揭示出一致性的鲁棒性短板。
conclusion: 为复杂操作任务中的模仿学习提供了更全面可靠的鲁棒性评测工具。
---

## Abstract
Visual-Language-Action (VLA) models report impressive success rates exceeding 95% on robotic manipulation benchmarks, yet these results may mask fundamental weaknesses in robustness. Current simulation-based robustness evaluations suffer from narrow perturbation coverage, manual design constraints, and coarse-grained analysis that fails to reveal when and how models fail. To address this gap, we propose LIBERO-Plus, a comprehensive, automatic, and fine-grained evaluation framework with controlled perturbations across seven dimensions: object layouts, camera viewpoints, robot initial states, language instructions, lighting conditions, background textures, and sensor noise. Our systematic analysis of ten state-of-the-art models reveals consistent brittleness beneath apparent competence, with performance dropping from 95% to below 30% under modest perturbations. Our findings challenge the assumption that high benchmark scores equate to true competency and highlight the need for evaluation practices that assess reliability under realistic variation.

---

## 论文详细总结（自动生成）

<think>The user wants me to provide a detailed Chinese summary of the LIBERO-Plus paper following a specific structure with 8 points. Let me carefully analyze the paper content and organize a comprehensive response.

The paper is about:
- A robustness benchmark for VLA models
- 7 perturbation dimensions
- 10 SOTA models evaluated
- 10,030 tasks
- Progressive difficulty L1-L5
- Findings about fragility, language neglect, positional bias, compositional generalization gap

Let me structure the response according to the 8 required points.</think>

# LIBERO-Plus 论文结构化分析

## 1. 核心问题与研究动机

- **背景**：近年来视觉-语言-动作（VLA）模型在 LIBERO 等仿真基准上报告的成功率普遍超过 95%，给人一种"机器人操控问题已基本解决"的错觉；但真实部署中，模型在光照变化、相机视角偏移、语言表述差异等情境下表现急剧下降。
- **核心问题**：现有仿真鲁棒性评测存在三大缺陷——
  1. 扰动类型覆盖窄，仅针对单一或少数轴线；
  2. 多依赖人工设计，扩展性差、不可复现；
  3. 仅报告聚合成功率，难以揭示"何时"与"何种条件下"失败。
- **研究目标**：构建一个全面、自动、细粒度的鲁棒性评测框架，揭示当前 VLA 模型在扰动下的真实能力边界。

## 2. 方法论

- **总体框架**：在 LIBERO 基础上扩展，提出 **LIBERO-Plus**，包含 **7 个扰动维度、21 个子维度、10,030 个任务实例**，并划分 **L1–L5 五级难度**（基于 4 个代表性 VLA 模型的实证表现自动分层）。
- **七大扰动维度**：
  1. **物体布局（Layout）**：引入干扰物体 + 目标物体空间位姿变换；
  2. **相机视角（Camera）**：相机位姿、朝向与视场调整；
  3. **机器人初始状态（RobotInit）**：机械臂起始位姿变化；
  4. **语言指令（Language）**：语义改写、复杂度提升；
  5. **光照条件（Light）**：强度、方向、颜色变化；
  6. **背景纹理（Background）**：表面材质与纹理替换；
  7. **传感器噪声（Noise）**：抖动、高斯模糊等光度畸变。
- **关键技术**：
  - 自动化任务构建：参数化扰动生成，无需人工逐条设计；
  - 渐进式难度分层：依据实证表现将扰动按强度排序；
  - 统计化的"组合泛化差距"（Compositionality Gap）：
    - 定义成功指示变量 $Y$，扰动指示变量 $D_i$；
    - 计算条件概率 $p(D_i=1 \mid Y=1)$ 与联合条件概率 $p(D_i=1, D_j=1 \mid Y=1)$；
    - 组合泛化差距定义为协方差：
      $$\Delta_{ij} = p(D_i=1, D_j=1 \mid Y=1) - p(D_i=1 \mid Y=1)\,p(D_j=1 \mid Y=1)$$
    - $\Delta_{ij}<0$ 表示扰动之间存在负向交互，组合后性能下降超过独立效应之和。
- **验证实验**：包括"空指令实验"、"目标替换实验"、"全黑/第三视角黑帧消融"等。

## 3. 实验设计

- **基准平台**：LIBERO 仿真器（多视角观测 + 语言指令）。
- **数据集规模**：
  - 测试集：**10,030 个任务实例**；
  - 训练集（增强版）：**20,000+ 成功轨迹**，覆盖六类扰动；
  - 组合扰动统计实验：**30,000 次独立重复试验**，6 维度成对组合，每对 2,000 次试验。
- **对比方法（共 10 个 SOTA VLA 模型）**：
  - 自回归类：OpenVLA、OpenVLA-OFT、OpenVLA-OFT_w（仅第三视角）、OpenVLA-OFT_m（混合 SFT 版）、π0、π0-Fast、Nora、WorldVLA、UniVLA、RIPT-VLA。
  - 涵盖扩散模型、RL 后训练、世界模型等多种训练范式。
- **评测指标**：任务成功率（%）、性能下降幅度（↓），并按维度与 L1–L5 难度分层报告。

## 4. 资源与算力

- 论文**未明确给出 GPU 型号、数量、训练时长等具体算力信息**；
- 仅在补充材料中描述数据集构建细节和模型实现细节（附录 B/D），未提供完整训练算力账单；
- 增强训练实验中提到对 OpenVLA-OFT 权重进行"混合微调"（mixed fine-tuning），但未公开训练时长与硬件配置。

## 5. 实验数量与充分性

- **实验规模**：
  - 10 个模型 × 7 扰动维度 × 5 个难度等级 = 350 组以上细分评测；
  - 10,030 个任务实例 + 30,000 次组合扰动统计试验；
  - 额外消融：空指令、目标替换、视角遮挡（3rd-Black/All-Black）。
- **客观性**：
  - 全部扰动均参数化自动生成，避免人工偏差；
  - 统计显著性通过卡方检验验证（附录 F）；
  - 五级难度基于多个代表模型的平均表现自动划分，减少主观性。
- **公平性**：
  - 所有模型在相同扰动设置下评测；
  - 但部分模型（如 OpenVLA-OFT_m、π0-fast）的原始训练已包含多样化数据，可能使其在扰动评测中具备先天优势，这一点作者在结论中有提及但未深入控制。
- **总体判断**：实验规模大、覆盖维度广，**充分性与客观性较好**；但缺少跨基准（如真实机器人、ManiSkill 等）的外部验证。

## 6. 主要结论与发现

- **Finding 1**：VLA 模型在多种扰动下均表现出显著的脆弱性，性能从 95%+ 下降至 30% 以下；
- **Finding 2**：对相机视角和机器人初始状态最敏感，对光照与背景相对鲁棒；
- **Finding 3**：语言扰动对性能影响最小（平均仅 -25.3），暗示模型未充分利用语言；
- **Finding 4**：架构（是否含腕部相机）与训练范式（数据多样性）显著影响鲁棒性；
- **Finding 5**：模型能忽略干扰物体，但目标物体位移时性能骤降，呈现**位置偏置**而非语义理解；
- **Finding 6**：腕部相机对光照鲁棒性贡献巨大，是光照稳定的关键；
- **Finding 7–8**：替换任务目标后成功率接近 0，证明 VLA 模型**几乎不遵循语言指令**，更多依赖固定视觉-动作映射；
- **Finding 9**：多维组合扰动下泛化能力**不可分解**（compositionality gap 普遍为负），扰动之间互相加剧难度；
- **额外结果**：在 LIBERO-Plus 增强数据上微调 OpenVLA-OFT 后，总体成功率提升至 79.6%，相机视角鲁棒性提升 37.2 个百分点，证明**训练数据多样性**可有效改善鲁棒性。

## 7. 优点

- **全面性**：7 维度、21 子维度、10,030 任务的扰动规模显著超越以往基准（AGNOSTOS、INT-ACT、COLOSSEUM 等）；
- **自动化**：参数化扰动生成保证可复现与可扩展；
- **细粒度**：L1–L5 难度分层 + 组合泛化差距分析，揭示失败模式而非仅聚合指标；
- **方法论严谨**：引入协方差形式的组合泛化差距指标，并配合卡方检验做显著性验证；
- **诊断价值高**：通过空指令、目标替换、视角遮挡等消融实验，明确揭示"VLA 退化为 VA"的本质问题；
- **闭环贡献**：不仅评测，还提供数据增强 + 微调方案，证明基准本身可指导改进。

## 8. 不足与局限

- **算力与训练细节不透明**：未公开训练所用 GPU、时长与超参，第三方复现难度较高；
- **仿真单一性**：仅基于 LIBERO 仿真器，缺少真实机器人或跨仿真器（如 RLBench、ManiSkill）的外部验证；
- **语言扰动设计局限**：扰动以改写为主，未涵盖多轮对话、模糊指令、指代消解等真实场景复杂语言；
- **组合扰动仅两两**：最高只分析成对交互，三维及以上的耦合效应未涉及；
- **公平性瑕疵**：被评测模型中部分（如 π0-fast、OpenVLA-OFT_m）已在大规模多样化数据上预训练，存在"评测即偏向多模态预训练模型"的潜在偏差；
- **行为机制解释有限**：虽提出位置偏置、忽略语言等结论，但缺少对注意力可视化、特征表示的深入机理分析；
- **应用限制**：主要面向桌面机械臂的桌面操作任务，未涉及移动机器人、长序列任务、跨形态迁移等场景。

（完）
