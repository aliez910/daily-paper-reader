---
title: Learning Diffusion Policy from Primitive Skills for Robot Manipulation
title_zh: 从原语技能中学习扩散策略用于机器人操作
authors: "Zhihao Gu, Ming Yang, Difan Zou, Dong Xu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38889/42851"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于技能条件的扩散策略的机器人操纵模仿学习
tldr: 现有扩散策略依赖全局指令导致动作生成错位。该论文提出SDP，用八种可复用原语技能作为条件，结合视觉语言模型提取离散表示，指导扩散策略生成短时控制信号。实验表明该方法提高了动作对齐性和任务成功率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38889/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 845, \"height\": 321, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38889/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 806, \"height\": 371, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38889/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1444, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38889/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1566, \"height\": 462, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38889/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1668, \"height\": 340, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38889/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1358, \"height\": 717, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38889/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38889/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 773, \"height\": 546, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38889/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 844, \"height\": 210, \"label\": \"Table\"}]"
motivation: 现有扩散策略基于全局指令生成短时控制，易导致动作与指令不匹配。
method: 提出技能条件扩散策略SDP，从视觉语言模型中提取离散技能表示并规划动作。
result: 在多种操作任务上实现了更高的成功率和指令遵循度。
conclusion: 原语技能作为条件能有效提升扩散策略在机器人操作中的表现。
---

## Abstract
Diffusion policies have recently shown great promise for generating actions in robotic manipulation. However, existing approaches often rely on global instructions to produce short-term control signals, which can result in misalignment in action generation. We conjecture that the primitive skills, referred to as fine-grained, short-horizon manipulations, such as "move up" and "open the gripper", provide a more intuitive and effective interface for robot learning. To bridge this gap, we propose SDP, a skill-conditioned diffusion policy that integrates interpretable skill learning with conditional action planning. SDP abstracts eight reusable primitive skills across tasks and employs a vision-language model to extract discrete representations from visual observations and language instructions. Based on the representations, a lightweight router network is designed to assign a desired primitive skill for each state, which helps construct a single-skill policy to generate skill-aligned actions. By decomposing complex tasks into a sequence of primitive skills and selecting a single-skill policy, the proposed SDP ensures skill-consistent behavior across diverse tasks.
Extensive experiments on two challenging simulation benchmarks and real-world robot deployments demonstrate that SDP consistently outperforms state-of-the-art methods, providing a new paradigm for skill-based robot learning with diffusion policies.

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

现有扩散策略（Diffusion Policy）通常直接以高层语言指令（如“拿起柠檬放进黄色平底锅”）作为条件来生成短期低层动作序列。这种方式存在明显的粒度不匹配：高层指令过于抽象，无法提供对当前瞬时操作（如“闭合夹爪”）的具体指导，导致动作生成与目标意图之间的错位。  
作者提出将复杂任务分解为一系列可复用的 **原语技能**（primitive skills），例如“上移”、“下移”、“旋转”、“闭合夹爪”等细粒度的短时操作。这些技能更直观、更易执行，且可以在不同任务间共享。由此引出的核心思想是：以 **技能条件** 代替语言条件来指导扩散策略，从而提升动作的准确性和一致性。

## 2. 方法论

### 核心思想
提出 SDP（Skill-conditioned Diffusion Policy），将技能学习与条件扩散规划融合，整体框架包括三个主要模块：

- **原语技能抽象**：人工定义 8 种可跨任务复用的原语技能（roll，yaw，open gripper，move up，translate，close gripper，move down，rotate）。每个技能对应一个结构化的文本描述模板（如“the robot arm is going to close the gripper”）。
- **技能分配模块**：使用视觉‑语言模型（VLM）从静态相机与腕部相机图像以及高层语言指令中提取联合表征；一个轻量级路由网络（MLP + Softmax + top-1）据此在每一步选择最合适的单技能。
- **单技能扩散策略**：在 Diffusion Transformer 中，通过 LoRA 方式引入技能相关的 FFN 层，该层的参数由选中技能的嵌入动态生成，从而实现技能对动作生成的显式控制。

### 关键技术细节

- **表征提取**：利用冻结的 CLIP 文本编码器将技能模板编码为 prompt embedding，再用 VLM（基于 Florence‑2 的 Transformer）融合视觉与语言 token，获得全局表征 \( z_{vl} \)。
- **路由器**：将 \( z_{vl} \) 在 token 维度平均后通过 MLP 产生 8 维 logits，经 softmax 后执行 top-1 选取技能，最终拿到对应 skill embedding \( z \)。
- **条件注入**：时间步与本体感受（proprioception）经 MLP 编码后通过 AdaLN 注入；视觉与语言 token 通过 Cross‑Attention。技能嵌入则用于参数化额外的 FFN（SwishGLU + 两个低秩矩阵），与原始 FFN 输出相加形成最终特征。
- **训练损失**：去噪分数匹配损失 \( L_{SM} \) 加上一个正交正则化项 \( L_{Orth} \) 以降低 prompt embeddings 间的余弦相似度。
- **推理步数**：仅用 4 步 DDIM 采样即可生成动作序列，显著低于同类方法（如 MDT 与 MoDE 使用的 10 步）。

## 3. 实验设计

### 模拟基准

- **CALVIN**：34 个任务，24000 条含语言标注的演示。评价设置包括 **ABC→D**（在场景 A、B、C 训练，零样本测试 D）和 **ABCD→D**（全场景训练）。测试集为 1000 条 5 步指令链，度量成功率与平均完成长度。
- **LIBERO**：包含四个套件：Spatial（空间关系）、Object（多种物体）、Goal（不同目标）、Long（长时任务）。每套 10 个任务，每任务有人工遥操作演示 50 条。采用微调（fine-tuning）范式评估。

### 真实世界实验

- 自建 9 个任务，通过 6‑DoF Lebai 机器人臂数据收集，每任务 30 条演示。
- **多任务学习**：包含空间觉察（拿起柠檬/开微波炉放薯片）、工具使用（扫积木、用勺搅拌）、语义理解（倒水、叠方块）。
- **视觉泛化**：在未见过的物体（苹果、香蕉）以及复杂背景干扰下测试拾取放置任务。

### 对比方法

- **模拟场景**：DiffPolicy（CNN 扩散策略）、Octo、MDT、MoDE、OpenVLA、UniVLA 等。对齐 LIBERO 还包括 MaIL、UniActions。
- **真实场景**：对比 MoDE 与 OpenVLA（均使用作者提供的官方代码与参数微调）。

所有实验结果均报告多随机种子的平均值与标准差（3 个种子或 20 次试验），保证统计可靠性。

## 4. 资源与算力

论文明确报告：

- 模型在 **4 块 NVIDIA A100 GPU** 上微调，训练 **40 个 epoch**。
- 优化器：AdamW，学习率 \( 10^{-4} \)，批次大小 64，图像分辨率 224 × 224。
- 模型参数量：**1017M**，FLOPs **74.5G**。与基线相比（MoDE 780M / 57.4G / 30.5ms），SDP 推理时间 **45.1ms**（稍长但性能显著提升）。
- 预训练部分：基于 Open X‑Embodiment 数据集，在 Diffusion Transformer（12 块）上进行预训练（文中提及，但未给出预训练所需的具体算力细节）。

## 5. 实验数量与充分性

### 实验数量

- **CALVIN** 两大设置（ABC→D、ABCD→D），报告 step‑wise 成功率和平均长度（表 1）。
- **LIBERO** 四个套件，每个套件报告平均成功率及标准差（表 2）。
- **真实世界** 9 个任务，分别列出多任务与泛化成功率（图 4）。
- **消融实验** 分组件消融（表 3a）与技能注入策略消融（表 3b），覆盖 CALVIN 与 LIBERO‑Long。
- **复杂度分析**（表 4）：参数量、FLOPs、推理时间 & 性能。
- **技能可视化**（图 5）：展示了 2 条任务链每一步的分配技能。

### 充分性与公平性

- 模拟基准使用了标准官方协议（CALVIN 1000 链评估、LIBERO fine‑tune 设置）。
- 对比方法均采用其官方实现与推荐超参数，并在相同环境下微调。
- 结果均为多次试验的平均 ± 标准差，消融也做了 3 个种子。
- 总体来看，实验设计覆盖了多任务、长周期、零样本泛化、真实迁移，并涉及模型组件分析，充分且客观。唯一略显不足的是真实世界实验的随机种子数未明确说明（仅提到 20 次试验），但总体可信。

## 6. 主要结论与发现

1. **大幅领先现有方法**：  
   - CALVIN ABC→D 场景下，SDP 完成 5 个连续任务的到达率 **76.9%**，比最强基线 MoDE（62.4%）高 14.5%，比 UniVLA（56.5%）高 20.4%。  
   - LIBERO 平均成功率达 **96.9%**，比 UniVLA（92.5%）高 4.4%，比 MDT（76.1%）高 20.8%。  

2. **技能抽象有效且可解释**：可视化（图 5）表明，模型在无显式监督下自然学到分步骤的技能分配，且每步分配与观察高度一致，说明技能条件化提供了结构化的控制空间。

3. **对未见物体与视觉干扰具有合理泛化能力**：真实世界中，SDP 对苹果表现良好（形状相似），对香蕉形状变化较大时成功率有所降低但仍优于基线；引入干扰物后成功率下降仅 10%（65% vs 75%），说明鲁棒性较强。

4. **关键组件与注入策略均被验证有效**：消融表明 VLM 跨注意力、AdaLN 先验注入、技能抽象、CPE 均带来逐步提升；LoRA‑style FFN 参数化优于加性/拼接/FiLM 等注入方式。

## 7. 优点

- **创新性**：首次将原语技能显式引入扩散策略的条件流程，融合神经网络技能分配与低层动作生成。
- **模块化与可复用性**：8 种技能可组合表述大多数操作任务，不同任务共享同一技能集，提高了数据效率。
- **可解释性**：路由器分配结果可以直接可视化为时序技能链，便于理解机器人行为决策。
- **性能优势**：在多个基准上跨任务、跨场景取得一致领先，特别在长时序任务（CALVIN 5‑step）上提升显著。
- **推理效率高**：仅需 4 步去噪即可生成动作，远少于同类扩散政策（通常 10‑20 步），在稍增计算量前提下换取性能大幅提升。
- **实验全面**：覆盖模拟（CALVIN, LIBERO）和真实场景，消融、复杂度、可视化完备，对比方法包含 SOTA 扩散策略和 VLA 策略，公平性佳。

## 8. 不足与局限

- **模型规模与效率**：SDP 参数 1017M，FLOPs 74.5G，高于大部分基线（MoDE 780M, 57.4G），推理时间 45.1ms（MoDE 30.5ms）。虽然性能提升显著，但在资源受限的部署场景下可能存在障碍。
- **技能集固定**：目前仅定义 8 种原语技能，可能无法覆盖所有新颖任务中所需的动作（如一些独特姿态）。作者未讨论技能扩展或自动发现技能的方法。
- **泛化边界未深入探讨**：对形状差异大的新物体（香蕉）成功率大幅下降，说明对几何变化的泛化有限。此外，干扰物实验仅在单一设置下进行，鲁棒性验证尚不够全面。
- **依赖大规模预训练**：模型在 Open X‑Embodiment 上预训练后微调，未分析缺乏预训练时的性能，也无法脱离开源数据集复现。
- **未对失败模式做系统分析**：论文只汇报了成功率，没有讨论哪些类型的任务/步骤容易失败以及原因，不利于后续改进。

---

（完）
