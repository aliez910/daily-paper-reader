---
title: "CABTO: Context-Aware Behavior Tree Grounding for Robot Manipulation"
title_zh: CABTO：上下文感知行为树接地用于机器人操作
authors: "Yishuai Cai, Xinglin Chen, Yunxin Mao, Kun Hu, Minglong Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/40936/44897"
tags: ["query:rob-il"]
score: 4.0
evidence: 通过行为树处理机器人操作控制
tldr: 行为树规划中手动构建动作模型和控制策略耗时巨大。CABTO形式化行为树接地问题，并提出第一个高效框架，利用预训练大模型启发式搜索完整一致的行为树系统，在多种操作任务上验证了有效性。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40936/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1808, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40936/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1837, \"height\": 876, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40936/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1843, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-40936/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1830, \"height\": 382, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40936/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1820, \"height\": 496, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40936/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1744, \"height\": 390, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-40936/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1827, \"height\": 372, \"label\": \"Table\"}]"
motivation: 行为树系统构建依赖专家知识，过程繁琐。
method: 形式化行为树接地问题，提出CABTO框架结合大模型启发式搜索。
result: 在多种机器人操作场景中成功自动生成完整的行为树系统。
conclusion: 自动行为树接地能显著降低机器人控制系统的设计成本。
---

## Abstract
Behavior Trees (BTs) offer a powerful paradigm for designing modular and reactive robot controllers. BT planning, an emerging field, provides theoretical guarantees for the automated generation of reliable BTs. However, BT planning typically assumes that a well-designed BT system is already grounded—comprising high-level action models and low-level control policies—which often requires extensive expert knowledge and manual effort. In this paper, we formalize the BT Grounding problem: the automated construction of a complete and consistent BT system. We analyze its complexity and introduce CABTO (Context-Aware Behavior Tree grOunding), the first framework to efficiently solve this challenge. CABTO leverages pre-trained Large Models (LMs) to heuristically search the space of action models and control policies, guided by contextual feedback from BT planners and environmental observations. Experiments spanning seven task sets across three distinct robotic manipulation scenarios demonstrate CABTO’s effectiveness and efficiency in generating complete and consistent behavior tree systems.

---

## 论文详细总结（自动生成）

# CABTO: Context-Aware Behavior Tree Grounding for Robot Manipulation 总结

## 1. 核心问题与整体含义

- **研究背景**：行为树（BT）因其模块化、可解释性和反应性，被广泛用于机器人控制。BT 规划能够自动生成具有理论保证的 BT，但这类方法通常假设一个已经“接地”（grounded）的系统——包含手工设计的高层动作模型与低层控制策略——这需要大量专家知识和手动调试。
- **研究动机**：构建完整且一致的 BT 系统（即动作模型能覆盖所有任务，且控制策略的执行效果与模型声明一致）是部署的前置条件，但手动构建过程繁琐且易出错。
- **整体含义**：论文将 BT 接地问题形式化，并提出首个自动化框架 CABTO，利用预训练大模型（LM）结合规划器与环境反馈，高效搜索动作模型和控制策略空间，自动生成完整且一致的 BT 系统，从而大幅降低机器人控制系统的设计成本。

## 2. 方法论

- **核心思想**：将 BT 接地分解为三个互补阶段，利用大语言模型（LLM）和视觉-语言模型（VLM）分别进行启发式搜索，并通过规划器与仿真环境的反馈引导搜索方向，避免穷举搜索。
- **关键技术细节**：
  - **阶段一：高层模型提案（High-level Model Proposal）**  
    使用 LLM 根据任务描述（目标状态、初始条件等）生成候选动作模型（STRIPS 风格，包含前提、添加/删除效果）。通过 BT 规划器检验当前模型集对任务集的完整性（能否为每个任务规划出执行树），若存在未解任务，则收集规划失败上下文（如未完成的 BT 结构、已扩展条件数等），引导 LLM 补充更合适的动作模型。
  - **阶段二：低层策略采样（Low-level Policy Sampling）**  
    对每个候选动作模型，使用 VLM（Molmo + 编程接口）根据模型语义和仿真执行上下文，从预定义的策略库（端到端、分层、基于规则等）中采样具体控制策略及其超参数。验证策略时，在满足前提的初始状态下执行，检查终止状态是否与模型定义一致（即达到添加/删除效果）。对于每个模型，最多尝试 N_max 次。
  - **阶段三：跨层精炼（Cross-level Refinement）**  
    若某动作模型在多次策略采样后仍无法获得一致策略，VLM 综合规划上下文（该模型在规划树中的角色）和执行上下文（仿真图像、执行反馈等），生成修正后的动作模型（如补充遗漏的空间前提、修正效果谓词），重新进入模型候选池。
- **算法流程（文字说明）**：  
  初始化空动作集 A，候选模型池 HE 由 LLM 初始提案获得。主循环中：  
  1. 使用 BT 规划器检查 HE 对任务集 P 的完整性，将失败任务的诊断信息传入 LLM，生成新模型并加入 HE，直至所有任务可解或无法进一步补充。  
  2. 对 HE 中每个未验证的模型 h，重复：VLM 根据上下文采样策略 π，在仿真中执行并验证一致性。若一致，将 ⟨h, π⟩ 加入 A，否则尝试下一个策略。若 N_max 次后仍不成功，调用跨层精炼生成修正模型 h' 加入 HE。  
  3. 完成所有模型验证后，将 HE 修剪为仅含已验证模型，循环继续，直到 P 全部可解。最后从 A 中提取所有条件谓词构成条件集 C，返回 BT 系统 Φ = ⟨C, A⟩。

## 3. 实验设计

- **任务集与场景**：共 7 个任务集，覆盖 3 种机器人平台：
  - 单臂 Franka：Cover（覆盖）、Blocks（堆叠）
  - 双臂 Franka：Pour（倒水）、Handover（交接）、Storage（存储）
  - 移动 Fetch：Tidy Home（整理房间）、Cook Meal（烹饪）
  每个任务集包含 3 个具体目标，共 21 个任务。
- **仿真环境**：Franka 任务使用 Isaac Sim，Fetch 任务使用 OmniGibson。
- **基准与对比**：本文是首个 BT 接地框架，没有直接对比其他完整 grounding 方法。消融实验自身对比了：
  - 规划上下文的有/无（表 1）
  - LLM 类型（GPT-3.5-Turbo vs GPT-4o，表 1）
  - 低层策略类型（End-to-end、Hierarchical、Rule-based、Molmo+cuRobo+APIs、OpenVLA、VoxPoser、ReKep 等，表 2）
  - 执行上下文的有/无（表 2）
  - 跨层精炼中环境反馈的有/无（表 3，含文本基线）
- **评价指标**：
  - 高层模型提案：平均规划成功率（ASR）、完全规划成功率（CSR）、反馈次数（FC）
  - 低层策略采样：成功率（SR）
  - 跨层精炼：成功率（SR）、平均反馈次数（Avg. FC）

## 4. 资源与算力

- 论文明确提到：“All experiments are conducted on a single NVIDIA RTX 4090 GPU”。未说明具体训练/推理时长，但基于 10 次重复实验，算力消耗在单 GPU 上可行。

## 5. 实验数量与充分性

- **数量**：
  - 高层模型提案：每个 LLM 配置 10 次重复，覆盖 7 个任务集，报告平均值。
  - 低层策略采样：对 5 种典型动作模型，测试多种策略类型，每种 10 次。
  - 跨层精炼：对 5 种有缺陷的动作模型，在有/无反馈下各 10 次。
  - 总实验组数：包含消融与主结果，超过 20 组不同条件，每组 10 次重复。
- **充分性与客观性**：
  - 任务集覆盖单/双臂、移动操作、长期任务等多样性，验证了泛化性。
  - 所有消融实验均采取“有/无”控制变量，公平比较。
  - 多次重复取均值降低随机性，结果可靠。
  - 局限：缺乏与其他自动 BT 生成方法（如进化计算、RL）的端到端对比——但论文定位于 grounding 问题，此类方法通常假定已有底层策略，不直接可比。整体实验设计合理，结论有说服力。

## 6. 主要结论与发现

- CABTO 能成功自动生成完整且一致的 BT 系统，在 7 个任务集上 CSR 最高达 100%（如 GPT-4o + 规划上下文场景）。
- **规划上下文至关重要**：引入规划失败诊断信息后，GPT-4o 的 CSR 从 50% 提升至 90% 以上，GPT-3.5 也从约 43% 提升至 64%（表 1）。
- **GPT-4o 优于 GPT-3.5**：在带规划上下文的场景下，GPT-4o 综合 CSR 达 90%，显著优于 GPT-3.5 的约 64%。
- **低层策略采样有效**：VLM 能够根据执行上下文改进策略采样，带上下文的成功率（62%）明显高于无上下文（28%~44%）（表 2）。
- **跨层精炼弥补模型缺陷**：环境反馈使动作模型修正成功率从 12%（纯文本）提升至 74%（带多模态反馈）（表 3）。
- **不同策略类型各有优势**：Molmo+cuRobo 在关门/开门等需语义关键点的动作上表现更好，ReKep 和规则基方法在抓取上更强。

## 7. 优点

- **问题形式化清晰**：首次严格定义 BT 系统的完整性与一致性，将接地问题转化为可求解的规划-执行联合优化问题。
- **框架设计巧妙**：利用 LLM 处理抽象符号推理，VLM 处理视觉与物理执行，两者通过规划器/仿真反馈连接，形成闭环启发式搜索，无需穷举。
- **消融实验全面**：分别验证了高层上下文、低层上下文、跨层反馈、LM 能力、策略类型等多个因素，深度剖析了每个组件的贡献。
- **多场景验证**：覆盖单臂/双臂/移动操作，包含基础操作和复杂协同，体现良好泛化性。
- **代码开源**（https://github.com/DIDS-EI/CABTO），便于复现和后续研究。

## 8. 不足与局限

- **仅仿真验证**：所有实验在 Isaac Sim 和 OmniGibson 中完成，未部署到真实机器人，存在 sim-to-real 差距。动作模型与策略的仿真一致性不能保证在真机上同样可靠。
- **抽象概念纠正能力有限**：跨层精炼中，对“Put(obj, loc)”的“At”谓词冗余等缺乏直接视觉线索的缺陷，修正成功率仅 40%，表明 VLM 在处理纯符号冗余时仍有局限。
- **策略采样成功率仍有提升空间**：当前最好条件下策略平均成功率 62%，部分动作（如 Close）仅 50%，且完全自动化的跨层精炼最多需 3 个反馈循环，仍可能失败。
- **依赖 LM 能力**：高层提案依赖 LLM 对规划上下文的敏感度，低层采样依赖 VLM 的视觉-代码生成能力，若 LM 性能不足，框架效果会受限。论文仅测试了 GPT-3.5/4o，未探索开源模型。
- **计算开销未量化**：未报告每次推理或每次反馈循环的平均时间或 token 消耗，难以评估在多任务或大规模场景下的可扩展性。
- **任务集规模较小**：每个场景仅 3 个目标，且任务属性较为结构化，对更开放、更复杂的日常操作任务的适应性有待验证。

（完）
