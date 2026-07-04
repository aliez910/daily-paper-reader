---
title: "Think Small, Act Big: Primitive Prompt Learning for Lifelong Robot Manipulation"
title_zh: 小步思考大步行动：面向终身机器人操作的原语提示学习
authors: "Yao, Yuanqi, Liu, Siao, Song, Haoming, Qu, Delin, Chen, Qizhi, Ding, Yan, Zhao, Bin, Wang, Zhigang, Li, Xuelong, Wang, Dong"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yao_Think_Small_Act_Big_Primitive_Prompt_Learning_for_Lifelong_Robot_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 终身机器人操作与可复用动作原语
tldr: 通用机器人需要在持续学习新操作技能的同时保留已有能力，但现有经验回放与参数高效方法难以充分利用跨任务共享原语。本文提出原语提示学习（PPL），通过两阶段方案，先在多技能预训练阶段学习运动感知的原语提示以建模跨任务的语义与运动共享原语，再将其扩展到新任务，实现可复用、可扩展的终身机器人操作。实验表明该方法在终身操作基准上显著提升了知识保持与前向迁移能力。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 777, \"height\": 827, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1674, \"height\": 621, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1709, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1703, \"height\": 572, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1767, \"height\": 593, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1761, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 845, \"height\": 369, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 870, \"height\": 203, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 863, \"height\": 494, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1443, \"height\": 394, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 441, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yao-think-small-act-big-primitive-prompt-learning-for-lifelong-robot-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 874, \"height\": 176, \"label\": \"Table\"}]"
motivation: 通用机器人需在连续获取新技能的同时有效利用先验知识，但朴素经验回放难以利用技能间的共享原语。
method: 提出原语提示学习两阶段框架，通过多技能预训练学习运动感知原语提示以捕获跨任务共享语义与运动基元。
result: 在终身机器人操作基准上实现了更好的知识保留与新任务迁移效果。
conclusion: 原语级提示为终身机器人操作提供了可复用且可扩展的知识组织方式。
---

## Abstract
Learning a generalist robot that can effectively leverage prior knowledge for continuous skill acquisition remains significantly challenging. Despite the success of experience replay and parameter-efficient methods in maintaining knowledge across skills, naively applying these methods causes a failure to leverage the shared primitives between skills. To tackle these issues, we propose Primitive Prompt Learning (PPL), to achieve lifelong robot manipulation via reusable and extensible primitives. Within our two stage learning scheme, we first learn a set of primitive prompts to model primitives through multi-skills pre-training stage, where motion-aware prompts are learned to capture semantic and motion shared primitives across different skills. Secondly, when acquiring new skills in lifelong span, new prompts are concatenated and optimized with frozen pretrained prompts, boosting the learning via knowledge transfer from old skills to new ones. For evaluation, we construct a large-scale skill dataset and conduct extensive experiments in both simulation and real-world tasks, demonstrating PPL's superior performance over state-of-the-art methods.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Think Small, Act Big: Primitive Prompt Learning for Lifelong Robot Manipulation" organized in a specific structure. Let me analyze the paper content and create a comprehensive summary.

The paper proposes Primitive Prompt Learning (PPL) for lifelong robot manipulation. Let me break down what I need to cover:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me write a thorough, well-structured summary in Chinese.
</think>
# 论文总结：Think Small, Act Big — Primitive Prompt Learning for Lifelong Robot Manipulation

## 1. 核心问题与研究动机

- **长期目标**：构建一个"通用机器人（generalist robot）"，使其能够像人类一样，将已学技能的先验知识迁移并复用到新技能的学习中，从而在生命周期中持续获取新操作能力。
- **现有方法的两类瓶颈**：
  - **经验回放（Experience Replay）**：依赖存储历史数据，但在大规模实际部署中受限于存储与隐私约束。
  - **正则化 / 参数高效方法（如 LoRA、TAIL）**：为每个任务单独保留参数或施加约束，可缓解灾难性遗忘，但往往无法在不同任务间显式建模可共享的"动作原语"，因此知识迁移效率低下，尤其对"语义不同但底层运动模式相似"的任务（如抓取杯子与放置香蕉）难以有效复用。
- **关键观察**：作者通过光流（optical flow）分析发现，许多在高层语义上不同的技能（如"抓取香蕉"与"放茶壶"）在底层运动学层面共享相似的运动原语（motion primitives）。这些原语是跨任务知识迁移的天然桥梁，但现有方法均未充分利用。
- **本文定位**：提出 **原语提示学习（Primitive Prompt Learning, PPL）**，以可复用、可扩展的"原语提示"为载体，在两阶段学习框架中实现终身机器人操作。

---

## 2. 方法论

### 2.1 整体框架：两阶段学习
- **多技能预训练阶段**：在 J 个任务的演示数据上，学习一组"原语提示"，用以建模跨任务共享的原语。
- **终身学习阶段**：冻结预训练提示，仅追加并优化新任务的提示，实现从旧技能到新技能的知识迁移，且无需访问历史数据。

### 2.2 关键技术 1：原语提示（Primitive Prompt）
- 骨干网络采用 **Diffusion Transformer Policy**（Diffusion Policy + Transformer）。
- 提示形式为可学习参数 $p \in \mathbb{R}^{L_p \times D}$，被切分为 $p^K, p^V \in \mathbb{R}^{(L_p/2) \times D}$，并以 **prefix-tuning** 的方式拼接到 Transformer 每一层多头自注意力（MSA）的 Key 与 Value 之前：
  $$f_{P-T}(p, h) = \text{MSA}\big(h^Q,\ [p^K; h^K],\ [p^V; h^V]\big)$$
- 与简单 prompt learning 不同，PPL 将提示组织为 **M 个组件** $\{P_m\}$，并配备对应的 Attention Vector $A$ 与 Key $K$。最终提示通过文本-光流查询与各组件的相似度做加权求和：
  $$\alpha_m = \cos\_sim(\text{AttenQuery},\ K_m),\quad p = \sum_m \alpha_m P_m$$
  其中 $\text{AttenQuery} = \text{MAP}(T, F) \odot A$。

### 2.3 关键技术 2：运动感知提示（Motion-Aware Prompting, MAP）
- **动机**：纯语言指令作为查询只能匹配语义相似的任务，无法发现"语义不同但运动相关"任务间的共享原语。
- **做法**：
  - 用 **RAFT** 计算稠密光流，捕捉场景中像素级运动矢量 $(u, v)$，其对纹理/颜色外观变化具有不变性。
  - 用 **CLIP** 编码任务语言指令 $T$，提供语义特异性。
  - 通过学习函数 $f_{\text{prompt}}$ 融合两种信息：
    $$\text{MAP}(T, F) = f_{\text{prompt}}\big(E_{\text{CLIP}}(T),\ \Phi(F)\big)$$
- **效果**：相同光流模式（如"抓-提-放"轨迹）即便在语义不同任务下也能被检索到，从而实现跨任务原语迁移。

### 2.4 关键技术 3：终身技能获取
- 预训练完成后冻结全部原语提示组件 $\{P_m, K_m, A_m\}$。
- 遇到新任务 $k$ 时，**追加**新的提示组件 $(P', K', A')$，将提示库扩展为 $\mathbb{R}^{Z \times D}$。
- 训练新任务时只优化新增的提示，但加权计算 $\alpha$ 时仍会与所有已学提示（冻结）做相似度匹配——这样新任务能自动调用最相关的旧原语。
- 训练目标采用标准的扩散策略去噪损失（行为克隆的扩散形式）。

### 2.5 算法流程概览
- 算法 1 给出了完整伪代码：循环遍历每个任务 → 计算 RAFT 光流 → MAP 查询 → Prefix 提示前向 → 扩散损失 → 反向更新；进入终身阶段后，初始化新提示组件 → 计算新 MAP 查询 → 注意力加权 → 冻结旧提示，仅优化新提示。

---

## 3. 实验设计

### 3.1 数据集 / 场景
- **仿真技能数据集**（自建大规模数据集）：
  - 基于 **MimicGen** 构建 12 个基础技能（如抓方块、放咖啡杯、关机器盖、拉开抽屉等），每个技能提供 1K 条人类演示，初始状态分布广泛。
  - 基于 **LIBERO** 终身操作基准，包含多场景、多物体的操作任务（如 LIBERO-GOAL 等）。
  - 图 5 给出了 12 个技能的展示图，覆盖抓取、放置、关节操作等动作空间。
- **真实世界数据集**：
  - 平台为 **Franka Panda** 机械臂；
  - 预训练阶段 4 个技能（抓香蕉、抓方块、放香蕉到篮子、方块放到毯子），每个 200 条演示；
  - 终身阶段 5 个新技能（放饮料到砧板、放羊角面包、抓红/绿方块与放置、推下茶壶把手等）；
  - 每个任务在 15 次独立运行上评估成功率。

### 3.2 评测指标
- **FWT (Forward Transfer Weight)**：当前模型在第 k 个新任务上的最佳成功率，反映对新任务的迁移能力。
- **BWT (Backward Transfer Weight)**：训练完第 k 个任务后，在前 k−1 个任务上的成功率相对各自最佳值的平均变化，反映对旧任务的保持能力。
- 两者越高越好。

### 3.3 对比方法
- **多技能预训练对比**：Diffusion-Transformer (Diff-T) 基线、MoE-based Policy（Sparse Diffusion Policy）。
- **终身学习对比**：
  - **Sequential**（朴素顺序微调）
  - **ER**（Experience Replay，经验回放）
  - **LoRA / TAIL**（任务级低秩适配）
  - **PPL (Ours)**

### 3.4 主要结果摘要
- **MimicGen 终身学习（Table 1）**：7 个任务平均 FWT = 0.78±0.09 / 0.83±0.03（PPL 两种设置），显著高于 Sequential (0.65)、ER (0.61)、LoRA/TAIL (0.78)。BWT 方面 PPL 同样占优，且 ER/LoRA 的 BWT 为明显负值（-0.46 ~ -0.56），说明存在灾难性遗忘。
- **LIBERO（Figure 7）**：在同场景多任务中，PPL 平均成功率 0.73 ± 0.03，优于 Sequential (0.72) 和 ER (0.65)。
- **真实世界（Table 2）**：4 个预训练任务平均 0.84 ± 0.05，3 个终身任务平均 0.68 ± 0.05，均超过 Diff-T / MoE / Sequential / ER 基线。

---

## 4. 资源与算力

- **论文未明确给出**：GPU 型号、数量、训练时长、参数量等具体算力信息均未在正文中披露。
- **可推断信息**：
  - 真实世界实验在单台 **Franka Panda** 上完成。
  - 模型骨干为 Diffusion Transformer Policy，提示参数规模为 $L_p \times D$（论文未给出具体数值）。
  - 仿真实验规模较大（12 任务 × 1K 演示 + LIBERO 7 任务终身序列），隐含需要多卡 GPU 训练，但具体配置缺失。
- **建议**：复现时需自行根据 Diff-T 原始实现规模估算算力。

---

## 5. 实验数量与充分性

- **实验类别覆盖**：
  - 多技能预训练（MimicGen / LIBERO / 真实世界）
  - 终身学习（7 任务 MimicGen 序列 + 3 任务真实世界序列）
  - 消融：MAP（仅文本 vs 文本+光流）、原语提示数量、消去原语提示的两种退化情形
  - 鲁棒性：复杂光照（暖光 → 冷光 → 暗光）下推茶壶把手
  - PPL vs LoRA / MoE 训练速度与性能对比
- **充分性评价**：
  - **优点**：覆盖仿真 + 真实世界 + 终身序列 + 消融 + 鲁棒性，结构完整；并通过权重可视化（图 6）直观展示 MAP 的语义-运动双重检索能力。
  - **不足**：
    - 真实世界任务仅 4 预训练 + 3 终身，规模偏小，统计显著性较弱。
    - 终身学习任务数（MimicGen 7 个）虽多，但未给出每个任务单独的方差分析或显著性检验。
    - BWT 指标下 PPL 与 LoRA/ER 的差距在论文叙述中被强调，但表格中部分任务的方差区间重叠（如 Task 2: 0.79±0.01 vs 0.75±0.12），公平性论证稍显不足。
    - 缺乏对不同 robot embodiment、不同动作空间（双手机、灵巧手）的泛化测试。

---

## 6. 主要结论与发现

- **跨任务共享原语确实存在**：通过光流可视化与权重分析证实，许多高层语义不同但底层运动模式相似的任务在提示空间中有相似的响应。
- **MAP 是关键**：纯文本查询只能检索语义相似任务；引入光流后，提示权重能在语义不同但运动相关任务间共享，从而实现真正的"原语级"知识迁移。
- **两阶段可扩展性**：冻结预训练提示 + 追加新提示的机制，使得终身学习阶段无需历史数据即可实现正向前向迁移（FWT），同时较好保持旧任务能力（BWT 退化最小）。
- **PPL 在性能与效率上兼具优势**：在 MimicGen、LIBERO、真实世界实验中均取得 SOTA；与 MoE 相比训练速度相近（MoE 实际约为 PPL 2 倍训练时长）但性能更优；与 LoRA 相比训练速度相当但迁移效果明显更好。
- **PPL 同时具备"原语级"可解释性**：通过可视化提示权重，可观察到每个任务调用了哪些共享原语。

---

## 7. 优点与亮点

- **问题定位新颖**：首次将"原语（primitive）"概念系统性地引入终身机器人操作的提示学习框架，填补了"任务间共享运动结构"这一未被充分利用的研究空白。
- **运动感知提示（MAP）设计巧妙**：结合 CLIP（语义）与 RAFT 光流（运动），用统一查询同时检索两类共享原语，方法简洁、效果好。
- **两阶段解耦清晰**：预训练学习通用原语，终身阶段冻结 + 追加，避免灾难性遗忘且无需历史数据，实用性强。
- **实验维度较全面**：仿真 + 真实世界 + 消融 + 鲁棒性 + 训练速度对比，且有清晰的权重可视化（图 6）佐证 MAP 的有效性。
- **即插即用**：以 prefix-tuning 形式挂接到 Diff-T 上，未修改骨干结构，易于迁移到其它扩散策略。

---

## 8. 不足与局限

- **真实世界实验规模有限**：仅 4 预训练 + 3 终身任务、每任务 200 演示、15 次运行，远小于仿真规模，结论的泛化性仍需更多真实世界数据验证。
- **对光流质量的依赖**：在动态光照（暖→冷→暗）实验中，作者发现 PPL (text+flow) 性能退化至 0.61，弱于纯文本 (0.80) 和 Diff-T (0.75)，说明光流在视觉退化场景下会成为噪声来源，方法对 RAFT 质量较敏感。
- **光照鲁棒性未解决**：作者承认这是局限性，并计划引入深度 / 3D scene flow 改进，但当前版本未给出解决方案。
- **提示数量需手工调参**：消融（图 8）显示提示数过多或过少都会损害性能，但未给出自动化选择策略或对超参的敏感性曲线。
- **缺乏任务间干扰的系统分析**：仅给出 BWT 平均值，未分析哪些任务对之间存在"干扰"或"互促进"现象，原语提示的可解释性优势未被充分利用。
- **与最新 VLA 模型对比缺失**：未与近年视觉-语言-动作基础模型（如 RT-2、OpenVLA、π0 等）在终身场景下直接比较，难以判断其在通用机器人基础模型时代下的相对位置。
- **隐私/算力信息缺失**：未报告训练成本，限制复现性评估。
- **单机器人 embodiment**：仅在 Franka Panda 上验证，未覆盖双手机、灵巧手、移动操作等更复杂形态，方法的跨 embodiment 迁移性未知。

（完）
