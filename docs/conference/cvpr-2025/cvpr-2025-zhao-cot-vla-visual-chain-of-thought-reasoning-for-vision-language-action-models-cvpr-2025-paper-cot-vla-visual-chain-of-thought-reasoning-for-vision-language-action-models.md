---
title: "CoT-VLA: Visual Chain-of-Thought Reasoning for Vision-Language-Action Models"
title_zh: CoT-VLA：面向视觉-语言-动作模型的视觉思维链推理
authors: "Zhao, Qingqing, Lu, Yao, Kim, Moo Jin, Fu, Zipeng, Zhang, Zhuoyang, Wu, Yecheng, Li, Zhaoshuo, Ma, Qianli, Han, Song, Finn, Chelsea, Handa, Ankur, Lin, Tsung-Yi, Wetzstein, Gordon, Liu, Ming-Yu, Xiang, Donglai"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhao_CoT-VLA_Visual_Chain-of-Thought_Reasoning_for_Vision-Language-Action_Models_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 引入视觉思维链推理的最先进VLA模型处理复杂操作
tldr: 现有VLA模型主要采用直接输入输出映射，缺少复杂操作所需的关键中间推理步骤。本文提出CoT-VLA，通过自回归预测未来图像帧作为视觉目标，再生成动作序列，将显式视觉思维链推理引入VLA模型。该端到端视觉运动方法为VLA增添了时间规划与推理能力。该工作是面向复杂机器人任务的视觉模仿学习的前沿进展，对提升VLA在长程操作中的决策能力具有重要意义。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 999, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1798, \"height\": 556, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 655, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1811, \"height\": 424, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1746, \"height\": 1196, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 866, \"height\": 632, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1565, \"height\": 281, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 875, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 852, \"height\": 278, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-cot-vla-visual-chain-of-thought-reasoning-for-vision-language-action-models-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 845, \"height\": 195, \"label\": \"Table\"}]"
motivation: 现有VLA模型缺乏复杂操作所需的时间规划与中间推理能力。
method: 在VLA中引入视觉思维链，自回归预测未来图像作为目标再生成动作。
result: 为VLA模型增加了显式推理步骤，提升复杂操作任务表现。
conclusion: CoT-VLA是面向复杂操作任务的视觉模仿学习的重要前沿进展。
---

## Abstract
Vision-language-action models (VLAs) have shown potential in leveraging pretrained vision-language models and diverse robot demonstrations for learning generalizable sensorimotor control. While this paradigm effectively utilizes large-scale data from both robotic and non-robotic sources, current VLAs primarily focus on direct input--output mappings, lacking the intermediate reasoning steps crucial for complex manipulation tasks. As a result, existing VLAs lack temporal planning or reasoning capabilities. In this paper, we introduce a method that incorporates explicit visual chain-of-thought (CoT) reasoning into vision-language-action models (VLAs) by predicting future image frames autoregressively as visual goals before generating a short action sequence to achieve these goals. We introduce CoT-VLA, a state-of-the-art 7B VLA that can understand and generate visual and action tokens. Our experimental results demonstrate that CoT-VLA achieves strong performance, outperforming the state-of-the-art VLA model by 17% in real-world manipulation tasks and 6% in simulation benchmarks. Videos are available at: https://cot-vla.github.io/.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "CoT-VLA: Visual Chain-of-Thought Reasoning for Vision-Language-Action Models" organized into specific sections. Let me analyze the paper content carefully and structure the response according to the 8 requested points.

Let me go through the paper systematically:

1. **Core problem and motivation**: Existing VLAs focus on direct input-output mapping without intermediate reasoning steps, lacking temporal planning and reasoning capabilities needed for complex manipulation tasks.

2. **Methodology**: 
   - Visual Chain-of-Thought (Visual CoT) reasoning - predicting subgoal images as intermediate reasoning steps
   - Two-phase approach: predict subgoal image, then generate action sequence
   - Built on VILA-U base model (unified multimodal foundation model)
   - Hybrid attention mechanism: causal attention for text/image generation, full attention for action prediction
   - Action chunking
   - Formulas: Eq (1) vanilla VLA, Eq (2) subgoal image prediction, Eq (3) action generation
   - Loss functions: L_visual and L_action

3. **Experimental design**:
   - LIBERO benchmark (4 suites: Spatial, Object, Goal, Long)
   - Bridge-V2 real-robot platform (WidowX 6-DoF, 45k trajectories)
   - Franka-Tabletop (Franka Emika Panda 7-DoF, 10-150 demos per task)
   - Baselines: Diffusion Policy, Octo, OpenVLA, SUSIE

4. **Resources/compute**: The paper doesn't explicitly mention GPU specs, training duration, etc. I should note this absence.

5. **Number of experiments**: 
   - LIBERO: 4 suites, 500 episodes each, 3 seeds
   - Bridge-V2: 4 categories, 10 trials each
   - Franka-Tabletop: 6 tasks, multiple trials
   - Ablation studies on action chunking, hybrid attention, CoT
   - Pretraining ablation
   - Better visual reasoning study with ground-truth vs generated goals

6. **Conclusions**: CoT-VLA achieves SOTA, outperforming prior SOTA by 17% in real-world and 6% in simulation; visual reasoning improvements directly translate to better action execution.

7. **Strengths**: Novel visual CoT approach, hybrid attention, leverages action-less video data, comprehensive evaluation.

8. **Limitations**: 
   - Computational overhead (7x slowdown from image generation)
   - Lower visual quality than diffusion-based models
   - Action chunking can introduce discontinuous actions
   - Limited visual reasoning generalization for new tasks

Let me write this in Chinese with Markdown formatting.</think>

# CoT-VLA 论文总结

## 1. 核心问题与研究动机

- **问题背景**：现有视觉-语言-动作模型（VLA）虽然在通用机器人操控中取得进展，但其主流范式是直接将"视觉观测 + 语言指令"映射到"机器人动作"，**缺乏显式中间推理步骤**，难以胜任需要时间规划与因果推理的复杂操控任务。
- **关键不足**：
  - 现有 VLA（如 OpenVLA、Octo 等）以"输入→输出"直接映射为主，缺少类似 LLM 中 Chain-of-Thought (CoT) 的逐步推理机制；
  - 已有的具身 CoT 工作多依赖语言描述、关键点或边界框等抽象表征，需要额外标注或预处理流水线；
  - 大量无动作标注的视频数据未被有效利用来增强视觉推理能力。
- **研究目标**：将**视觉思维链（Visual CoT）**显式引入 VLA，使模型先在像素空间"思考"未来状态，再据此生成动作，并充分利用无动作视频数据。

## 2. 方法论

### 2.1 核心思想

- 将"未来子目标图像（subgoal image）"作为视觉推理的中间步骤，使 VLA 在生成动作前显式进行"视觉思考"。
- 推理分两阶段：
  - **阶段 1（视觉推理）**：基于当前观测 $s_t$ 与语言指令 $l$，自回归预测 $n$ 帧之后的子目标图像 $\hat{s}_{t+n}$；
  - **阶段 2（动作生成）**：基于 $l$、$s_t$ 与子目标 $\hat{s}_{t+n}$，并行生成 $m$ 个连续动作 $\{\hat{a}_t,...,\hat{a}_{t+m}\}$。

### 2.2 形式化表述

- 训练数据：机器人演示 $\mathcal{D}_r=\{(l, a_{1:T}, s_{1:T})\}$；无动作视频 $\mathcal{D}_v=\{(l, s_{1:T})\}$。
- Vanilla VLA：$\hat{a}_t \sim P_\theta(a_t \mid s_t, l)$
- CoT-VLA：
  $$\hat{s}_{t+n} \sim P_\theta(s_{t+n} \mid s_t, l) \quad (2)$$
  $$\{\hat{a}_t,...,\hat{a}_{t+m}\} \sim P_\theta(\{a_t,...,a_{t+m}\} \mid s_t, l, \hat{s}_{t+n}) \quad (3)$$
- 子目标图像预测损失 $\mathcal{L}_{\text{visual}}$ 使用 RQ-VAE 风格的残差量化逐层预测视觉 token；动作预测损失 $\mathcal{L}_{\text{action}}$ 采用离散化（256 bin）后的交叉熵；总损失 $\mathcal{L} = \mathcal{L}_{\text{action}} + \mathcal{L}_{\text{visual}}$。

### 2.3 关键技术细节

- **基础模型**：VILA-U（7B），统一多模态理解/生成模型，图像被编码为 $16 \times 16 \times 4$ 离散视觉 token，分辨率 $256 \times 256$。
- **混合注意力机制（Hybrid Attention）**：
  - 文本与图像生成采用 **causal attention**（next-token prediction）；
  - 动作序列采用 **full attention**，使所有动作维度可并行交互，并通过特殊 token `[x] [θ] [g]` 实现并行解码。
- **Action Chunking**：每次预测长度为 10 的动作序列以提升稳定性与吞吐。
- **训练流程**：
  - **预训练**：在 Open X-Embodiment 数据子集 + EPIC-KITCHEN-100 + Something-Something V2 上联合训练视觉推理（同时利用 $\mathcal{D}_r$ 与 $\mathcal{D}_v$）与动作生成；
  - **下游适应**：在目标机器人平台（Bridge-V2、Franka-Tabletop）的任务演示上微调 LLM 主干、投影器与 depth transformer，冻结视觉塔。
- **测试时闭环控制**（Algorithm 1）：每执行 $m$ 个动作后重新观测，更新 $s_t$ 后再生成新的子目标与动作 chunk。

## 3. 实验设计

### 3.1 仿真基准

- **LIBERO**（4 个任务套件）：
  - LIBERO-Spatial、LIBERO-Object、LIBERO-Goal、LIBERO-Long；
  - 每个任务 50 条人类遥操作演示；
  - 统一采用 OpenVLA 的预处理流程（去暂停、$256\times256$、180° 旋转）。

### 3.2 真实机器人平台

- **Bridge-V2**：6-DoF WidowX 机械臂，使用 45k 语言标注轨迹，覆盖视觉鲁棒性、运动泛化、语义泛化与语言接地四类评估；
- **Franka-Tabletop**：台架式 7-DoF Franka Emika Panda，预训练中未见；每任务仅 10–150 条演示，包含 3 个单指令 + 3 个多指令任务。

### 3.3 对比基线

- **Diffusion Policy**：从零训练的 SOTA 模仿学习算法（带 action chunking + DistilBERT 条件）；
- **Octo**：在 OpenX 上预训练但不带 VLM 初始化的通用策略；
- **OpenVLA**：开源 VLA 基线；
- **SUSIE**：两阶段（图像编辑 + 目标条件策略）方法，使用其发布检查点在 Bridge-V2 上评估。

## 4. 资源与算力

- **论文未明确披露** GPU 型号、数量、单卡训练时长或总训练成本，仅说明：
  - 模型规模为 7B 参数；
  - 推理时由于需要生成 256 个图像 token 才能产生动作 chunk（chunk size=10），**平均存在约 7× 的推理减速**；
  - 视觉塔在训练中保持冻结，可训练部分为 LLM 主干、投影器与 depth transformer。
- 建议视为 NVIDIA 内部大算力训练（参考论文机构），但**具体算力规格缺失**。

## 5. 实验数量与充分性

### 5.1 实验规模

- **LIBERO**：每个套件 500 episodes × 3 random seeds，4 个套件共 6000 次评估；
- **Bridge-V2**：4 个泛化类别 × 10 trials；
- **Franka-Tabletop**：6 个任务 × 多 trial；
- **消融实验**：
  - 在 LIBERO-Spatial 与 LIBERO-Goal 上比较 VLA / +Action Chunking / +Hybrid Attention / +CoT（完整）四档配置；
  - Franka-Tabletop 上的预训练消融（基 VILA-U 直接微调 vs. 完整预训练）；
- **额外分析**：OOD 长程任务中对比"生成子目标 vs. 真实子目标"对成功率的影响。

### 5.2 充分性评价

- **优点**：覆盖仿真 + 两种真实机器人平台、3 类基线、含多维泛化维度（视觉、运动、语义、语言）；并通过消融逐项验证 action chunking、hybrid attention、visual CoT 的贡献。
- **不足**：
  - 真实机器人实验 trial 数（10 / 任务级别）较小，结果的统计显著性有限；
  - 未与更近的 VLA（如 π₀、HiRT 等）或世界模型类方法做直接比较；
  - 没有给出按 token 的计算复杂度、显存占用等量化指标。

## 6. 主要结论与发现

- **整体性能**：
  - LIBERO 平均成功率 **81.1%**，超越 OpenVLA（76.5%）与 Octo（75.1%）；
  - Bridge-V2 四类泛化总体与 OpenVLA 可比，Motion 与 Semantic 类别优于基线；
  - Franka-Tabletop 上平均性能 SOTA，**较 SOTA VLA 真实任务提升 17%、仿真提升 6%**。
- **组件贡献**：Action chunking → Hybrid Attention → Visual CoT 逐档提升；
- **预训练价值**：完整预训练使 Franka-Tabletop 成功率从 53.7% 提升至 78.8%（相对 +46.7%）；
- **视觉推理与动作执行的耦合**：在 OOD 任务中用真实子目标代替生成子目标，绝对成功率提升 40%，证明视觉推理质量直接决定动作性能上限。

## 7. 优点与亮点

- **方法论创新**：首次将"子目标图像作为视觉 CoT 中间步"集成到 VLA 框架，无需额外标注，可直接利用演示视频的中间帧；
- **数据利用**：通过 $\mathcal{D}_v$ 的引入，使 VLA 能够从无动作的大规模视频中学习动态与指令跟随，扩展了训练数据范围；
- **架构设计**：混合注意力（causal for vision/text + full for actions）与 action chunking 配合，使动作预测可并行解码且各维度可交互；
- **可解释性**：模型在动作前显式生成目标图像，便于事后审计"为什么这样做"，相比抽象表征更直观；
- **全面评估**：仿真 + 两套真实机器人平台 + 多种基线 + 多维泛化 + 消融，论证较为完整。

## 8. 不足与局限

- **推理效率瓶颈**：每次决策需生成 256 个视觉 token，动作 chunk size 仅 10，平均存在约 7× 推理减速，限制实时部署；
- **图像质量受限**：自回归离散化图像生成质量低于扩散式图像编辑模型（如 SUSIE），在细粒度视觉理解上仍有差距；
- **动作 chunk 边界不连续**：action chunking 在 chunk 切换处可能产生不连续动作，且缺乏高频反馈；
- **OOD 视觉泛化不足**：在未见任务中，子目标图像生成质量下降，导致下游动作性能受限（"better visual reasoning helps" 实验已侧面证实）；
- **真实实验 trial 数偏少**：Bridge-V2 仅 10 trials/category，Franka-Tabletop trial 数同样有限，统计可信度有限；
- **未报告算力与训练细节**：缺少 GPU 型号、数量、训练时长、超参数完整列表（部分放至 supplementary），影响复现评估；
- **应用限制**：当前仅验证单臂末端执行控制（7-DoF），尚未扩展到双臂、移动操作或更高维动作空间；
- **公平性争议**：基线使用各自发布检查点（OpenVLA / Octo / SUSIE）而 CoT-VLA 经过额外预训练，可能引入预训练数据规模优势带来的偏差。

（完）
