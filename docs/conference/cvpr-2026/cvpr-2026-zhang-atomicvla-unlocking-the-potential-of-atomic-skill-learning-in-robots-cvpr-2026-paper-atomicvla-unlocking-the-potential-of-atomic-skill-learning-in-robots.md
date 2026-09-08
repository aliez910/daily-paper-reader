---
title: "AtomicVLA: Unlocking the Potential of Atomic Skill Learning in Robots"
title_zh: AtomicVLA：释放机器人原子技能学习的潜力
authors: "Zhang, Likui, Tang, Tao, Zhan, Zhihao, Chen, Xiuwei, Chen, Zisheng, Han, Jianhua, Zhu, Jiangtong, Xu, Pei, Xu, Hang, Wu, Hefeng, Lin, Liang, Liang, Xiaodan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhang_AtomicVLA_Unlocking_the_Potential_of_Atomic_Skill_Learning_in_Robots_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向长视距复杂机器人操作的VLA框架，采用原子技能分解以实现任务规划与执行
tldr: 现有VLA模型在长视距、多步骤的机器人操作任务上表现欠佳，原因在于其单一的动作解码器难以随数据规模扩展。本文提出AtomicVLA，一个统一的规划-执行框架，能够联合生成任务级规划、原子技能抽象以及细粒度动作，并通过技能引导的混合专家机制构建可扩展的原子技能库。该工作直接回应了面向复杂机器人任务的先进视觉模仿学习需求，支持持续技能获取与泛化能力提升，对于通用机器人操作系统的构建具有重要价值。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 568, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1787, \"height\": 849, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1777, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1777, \"height\": 330, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1792, \"height\": 297, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 839, \"height\": 700, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1524, \"height\": 440, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1526, \"height\": 336, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 279, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1675, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhang-atomicvla-unlocking-the-potential-of-atomic-skill-learning-in-robots-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 791, \"height\": 263, \"label\": \"Table\"}]"
motivation: 现有VLA模型使用单一动作解码器，难以应对长视距多步骤任务且可扩展性差，限制了复杂操作的持续技能获取。
method: 提出统一的规划-执行框架，联合生成任务规划、原子技能抽象和细粒度动作，并构建技能引导的混合专家原子技能库。
result: 在长视距多步骤机器人操作任务上提升了泛化能力和可扩展性，支持持续技能习得与复杂任务执行。
conclusion: AtomicVLA通过原子技能分解显著增强了VLA模型在复杂机器人任务中的表现与扩展能力。
---

## Abstract
Recent advances in Visual-Language-Action (VLA) models have shown promising potential for robotic manipulation tasks.However, real-world robotic tasks often involve long-horizon, multi-step problem-solving and require generalization for continual skill acquisition, extending beyond single actions or skills. These challenges present significant barriers for existing VLA models, which use monolithic action decoders trained on aggregated data, resulting in poor scalability.To address these challenges, we propose AtomicVLA, a unified planning-and-execution framework that jointly generates task-level plans, atomic skill abstractions, and fine-grained actions. AtomicVLA constructs a scalable atomic skill library through a Skill-Guided Mixture-of-Experts (SG-MoE), where each expert specializes in mastering generic yet precise atomic skills. Furthermore, we introduce a flexible routing encoder that automatically assigns dedicated atomic experts to new skills, enabling continual learning.We validate our approach through extensive experiments. In simulation, AtomicVLA outperforms \pi_ 0 by 2.4% on LIBERO, 10% on LIBERO-LONG, and outperforms \pi_ 0 and \pi_ 0.5 by 0.22 and 0.25 in average task length on CALVIN. Additionally, our AtomicVLA consistently surpasses baselines by 18.3% and 21% in real-world long-horizon tasks and continual learning. These results highlight the effectiveness of atomic skill abstraction and dynamic expert composition for long-horizon and lifelong robotic tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "AtomicVLA: Unlocking the Potential of Atomic Skill Learning in Robots" following a specific structure. Let me analyze the paper carefully and provide a comprehensive summary.

The paper is about a VLA (Vision-Language-Action) model for robotic manipulation that addresses long-horizon and continual learning challenges through atomic skill decomposition.

Let me organize my response according to the 8 requested points.</think>

# AtomicVLA 论文总结

## 1. 核心问题与研究动机

- **现实需求与现有方法的差距**：现实机器人任务通常包含**长视距、多步骤**的问题求解，并需要**持续技能获取**能力，而现有 VLA 模型仍以单一动作为单位输出，难以胜任复杂任务。
- **现有 VLA 的两大瓶颈**：
  - **可扩展性差**：多数 VLA 使用单一动作解码器（在聚合数据上训练），新增技能需对全模型微调，计算与数据开销巨大，且易受机器人数据稀缺限制。
  - **严重技能干扰**：当不同技能混合训练时，单一解码器难以保持技能专精，导致**灾难性遗忘**，阻碍终身学习。
  - **规划-执行解耦问题**：两阶段（VLM 规划 + VLA 控制）架构存在模块间信息不一致、易产生过时指令等问题。
- **核心目标**：构建一个**统一的规划-执行框架**，既能进行高层任务规划，又能生成细粒度动作，并具备**可扩展、可终身学习**的原子技能库。

---

## 2. 方法论

### 2.1 整体框架：Think-Act 统一架构

- 通过引入两个特殊输出 token **`[think]`** 和 **`[act]`** 让模型自适应选择输出模式：
  - **Thinking 模式**：输出任务链 $C_{0:k}$、当前执行进度 $C_t$、**原子技能抽象** $\sigma$（仅在任务初始化或子技能切换时触发）。
  - **Acting 模式**：根据最新的 $\sigma$ 与本体感知 $s_t$ 生成低层动作块 $A_t$。
- 算法 1 给出了推理流程：模型先预测模式 token，再选择 Thinking 或 Acting；Acting 时先调用 Router 选专家，再调用动作专家。

### 2.2 技能引导的混合专家（SG-MoE）

- **基础**：基于 $\pi_0$ 构建，扩展为 MoE 结构。
- **三要素**：
  1. **技能路由器（Skill Router）**；
  2. **共享专家**（保留 $\pi_0$ 的通用动作生成能力）；
  3. **多个原子技能专家**（每个专家专注于一种原子技能）。
- **原子技能嵌入**：借鉴扩散模型噪声调度的思路，将每个技能抽象映射到标量噪声水平 $\sigma \in [0, 100]$，再经归一化映射为高维向量：
  $$Z_\sigma = E(\text{norm}(\log(\sigma)))$$
  连续、结构化的嵌入空间有利于语义分离与稳定路由。
- **稀疏路由**：Top-1 选择专家 $k$，最终输出为加权组合：
  $$F_{\text{out}} = (1 - w_k) \cdot F_{\text{share}}(x_t) + w_k \cdot F_k(x_t)$$
  其中 $x_t$ 表示多模态输入 $[O_{1:n}^t, \ell, s_t]$。

### 2.3 持续学习与技能扩展

- **模块化设计**：新增原子技能只需添加一个专家 + 扩展路由器，无需重训已有专家。
- **路由器初始化**：扩展路由器通过复制原路由器权重初始化，新分支使用小随机值，可微调成本低、避免灾难性遗忘。

### 2.4 任务规划数据生成管线

- 基于**主轴分析（Principal-Axis Analysis）**对末端执行器轨迹进行原子动作切分：分析 $\Delta x, \Delta y, \Delta z, \Delta \text{roll/pitch/yaw}$ 与夹爪状态变化。
- 通过 **InternVideo2.5** 对视频片段进行语义校验与标签修正，生成结构化推理链（任务链 + 原子动作标签）。
- 例：$z$ 持续下降 + 夹爪闭合 ⇒ "pick"；平移小、旋转大、夹爪闭合 ⇒ "turn"。

---

## 3. 实验设计

### 3.1 数据集 / Benchmark

- **模拟环境**：
  - **LIBERO**（4 个子套件：Spatial / Object / Goal / **Long**）
  - **CALVIN**（ABC→D 切分）
- **真实环境**：Franka 机械臂
  - **3 个长视距任务**：Objects in plate、Object into drawer、Object into microwave
  - **5 个短任务**（用于持续学习）：Grasp block、Stack blocks、Close microwave、Press button、Open drawer（新技能）
  - 数据规模：短任务每类 50 条轨迹，长任务每类 100 条，共 550 条真实演示轨迹。

### 3.2 对比方法

- **LIBERO 基线**：Octo、OpenVLA、SpatialVLA、CoT-VLA、$\pi_0$、$\pi_0.5$。
- **CALVIN 基线**：$\pi_0$、$\pi_0.5$。
- **真实机器人基线**：$\pi_0$、$\pi_0.5$（含持续学习场景）。
- **消融基线**（LIBERO-LONG）：
  1. 非 MoE 的 $\pi_0$ 基线；
  2. 标准的 token 级 MoE；
  3. MoDE（基于去噪步 $t$ 路由）。

### 3.3 训练设置

- 基于 $\pi_0$ 与 $\pi_0.5$ 预训练权重，轨迹格式遵循 **LeRobot** 标准。
- LIBERO 与真实机器人使用 **5 个技能专家**；CALVIN 因任务词表更大使用 **8 个技能专家**。

---

## 4. 资源与算力

- **论文未明确披露**所用 GPU 型号、数量及训练时长。
- 仅提到模型基于 $\pi_0 / \pi_0.5$ 预训练，并使用 LeRobot 标准数据格式训练。
- **附录**提及有"进一步实现细节"，但摘要与正文未列出算力细节，建议进一步查阅附录。

---

## 5. 实验数量与充分性

- **模拟实验**：
  - LIBERO 4 个子套件；
  - CALVIN（ABC→D，5 段连续任务）；
  - **1 组消融实验**（LIBERO-LONG 上比较非 MoE、标准 MoE、MoDE、SG-MoE）。
- **真实机器人实验**：
  - 1 组长视距混合训练（3 个任务）；
  - 1 组持续学习实验（4 旧 + 1 新技能）；
  - 定性示例（错误恢复、Interference/Degradation 可视化）。
- **充分性评估**：
  - **优点**：覆盖模拟 + 真实机器人、含消融与可视化（推理示例、错误恢复、干扰前后对比）、分别报告基座为 $\pi_0$ 与 $\pi_0.5$ 的两个版本结果；
  - **不足**：
    - 真实实验任务数量较少（仅 3 长任务 + 5 短任务），每类轨迹仅 50–100 条，统计显著性证据有限；
    - 仅使用 Franka 单平台，跨平台泛化未验证；
    - CALVIN 评估受协议限制（错误恢复不算成功），可能低估模型真实能力；
    - 消融实验只针对 LIBERO-LONG，缺乏其他维度（如不同专家数量、嵌入方式、初始化策略）的系统消融。

---

## 6. 主要结论与发现

- **LIBERO**：AtomicVLA 平均 96.6%，AtomicVLA\* 97.8%；**LIBERO-LONG** 上 AtomicVLA\* 达 96.2%，**比 $\pi_0$ 提升 10%**。
- **CALVIN**：AtomicVLA\* 平均任务长度 4.27，**比 $\pi_0.5$ 提升 0.25**；后三段提升 5.8%–6.6%。
- **真实机器人长视距**：AtomicVLA\* 比基线平均提升 **18.3%**（基座 $\pi_0.5$），能更好处理夹爪状态切换（如关闭微波炉）。
- **真实机器人持续学习**：基座 $\pi_0.5$ 平均下降 15%（Stack 任务下降 20%），AtomicVLA\* 仅下降 1.3%，整体 5 任务平均提升 **21%**。
- **消融结论**：在 LIBERO-LONG 上，SG-MoE 比标准 MoE 高 6.6%，比 MoDE 高 5.7%，证明**基于原子技能语义路由**优于 token 级或去噪步级路由。
- **附加能力**：观察到 AtomicVLA 在执行失败时具备**错误恢复**能力（自动重新评估进度并重做当前技能）。

---

## 7. 优点

- **统一的规划-执行架构**：通过 `[think]/[act]` 切换避免模块解耦导致的信息不一致。
- **原子技能 + SG-MoE**：以语义单元而非 token 为路由粒度，技能专精度高、干扰小，且与扩散/流匹配等动作解码器天然兼容。
- **可扩展、可终身学习**：新增技能只需增加专家与路由器分支，冻结旧专家即可避免灾难性遗忘。
- **数据生成方法可借鉴**：基于运动学主轴 + InternVideo2.5 的弱监督原子动作标注，降低对人工标注的依赖。
- **错误恢复能力**：在模拟与真实实验中均观察到自动重规划的现象。
- **结果提升显著**：在 LIBERO-LONG、CALVIN、真实长视距与持续学习场景上均有一致且较大的提升。

---

## 8. 不足与局限

- **算力与训练成本未披露**：难以评估方法的实际落地成本。
- **真实实验规模偏小**：仅 Franka 单平台、3 长 + 5 短任务、每类 ≤100 条轨迹，统计意义与跨平台泛化性证据有限。
- **评估协议限制**：CALVIN 不允许失败后恢复导致后续任务继续执行，可能低估模型真实能力。
- **原子技能集合依赖预定义**：当前路由需将技能映射到固定 $\sigma$ 范围（[0,100]），新增大量技能时 $\sigma$ 分配策略、专家容量上限未见讨论。
- **消融不够全面**：未对专家数量、嵌入方式、路由器初始化策略、共享专家 vs 纯专家等关键设计做系统消融。
- **数据生成管线依赖 InternVideo2.5**：额外的视频 MLLM 推理开销及对模型质量的依赖未充分讨论。
- **局限场景**：未明确分析在**双手机器人、动态环境、遮挡或光照剧烈变化**等更具挑战性的真实场景下的表现。
- **理论分析薄弱**：缺乏对 SG-MoE 路由稳定性、技能语义可解释性、收敛性等理论层面的论证。

（完）
