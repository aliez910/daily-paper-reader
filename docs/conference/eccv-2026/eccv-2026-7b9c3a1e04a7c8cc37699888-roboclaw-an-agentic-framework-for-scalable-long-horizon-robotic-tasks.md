---
title: "RoboClaw: An Agentic Framework for Scalable Long-Horizon Robotic Tasks"
title_zh: RoboClaw：面向可扩展长视野机器人任务的代理式框架
authors: "Ruiying Li, Yunlang Zhou, Yuyao Zhu, Kylin Chen, Sukai Wang, Kongtao Hu, Minhui Yu, Bowen Jiang, Jiayao Ma, Zhan Su, Yongjian Shen, Yang Yang, Guanghui Ren, Maoqing Yao, Wenhao Wang, Yao Mu"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/9598.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向语言驱动机器人操纵的VLA系统，扩展长视野任务
tldr: 视觉-语言-动作系统在语言驱动机器人操纵方面潜力显著，但将其扩展到长视野任务仍然困难，因为现有流程将数据采集、策略学习和部署分离，依赖人工环境复位且多策略执行脆弱。本文提出RoboClaw代理式机器人框架，在单一VLM驱动控制器下统一数据采集、策略学习与任务执行。在策略层面引入纠缠动作对，将前向操纵行为与反向恢复动作耦合，形成自复位循环以实现自主数据采集。该工作直接服务于通过模仿学习实现复杂机器人操纵任务的核心目标，对基于VLA的长视野操纵策略具有重要贡献。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7b9c3a1e04a7c8cc37699888/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 2238, \"height\": 1142}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7b9c3a1e04a7c8cc37699888/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 1391, \"height\": 799}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7b9c3a1e04a7c8cc37699888/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 3154, \"height\": 1231}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-7b9c3a1e04a7c8cc37699888/fig-004.webp\", \"caption\": \"\", \"page\": 14, \"index\": 4, \"width\": 8267, \"height\": 8210}]"
motivation: VLA系统扩展到长视野操纵任务时面临数据采集、策略学习和部署分离以及多策略执行脆弱的问题。
method: 在单一VLM驱动控制器下统一数据采集、策略学习与任务执行，并引入纠缠动作对形成自复位循环。
result: 实现了长视野机器人任务的自主数据采集与可扩展执行。
conclusion: 为语言驱动机器人操纵的VLA系统提供了统一的代理式解决方案。
---

## Abstract
Vision-Language-Action (VLA) systems have shown strong potential for language-driven robotic manipulation. However, scaling them to long-horizon tasks remains challenging. Existing pipelines typically separate data collection, policy learning, and deployment, resulting in heavy reliance on manual environment resets and brittle multi-policy execution. We present RoboClaw, an agentic robotics framework that unifies data collection, policy learning, and task execution under a single VLM-driven controller. At the policy level, RoboClaw introduces Entangled Action Pairs (EAP), which couple forward manipulation behaviors with inverse recovery actions to form self-resetting loops for autonomous data collection. This mechanism enables continuous on-policy data acquisition and iterative policy refinement with minimal human intervention. During deployment, the same agent performs high-level reasoning and dynamically orchestrates learned policy primitives to accomplish long-horizon tasks. By maintaining consistent contextual semantics across collection and execution, RoboClaw reduces mismatch between the two phases and improves multi-policy robustness. Experiments in real-world manipulation tasks demonstrate improved stability and scalability compared to conventional open-loop pipelines, while significantly reducing human effort throughout the robot lifecycle, achieving a 25% improvement in success rate over baseline methods on long-horizon tasks and reducing human time investment by 53.7%. Code is available at: https://github.com/RoboClaw-Robotics/RoboClaw.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "RoboClaw: An Agentic Framework for Scalable Long-Horizon Robotic Tasks" following a specific structure with 8 sections. Let me analyze the paper carefully and produce a comprehensive summary.

Let me organize my thoughts:

1. Core problem: Scaling VLA systems to long-horizon tasks is challenging because data collection, policy learning, and deployment are separated, leading to manual resets and brittle multi-policy execution.

2. Method: 
- RoboClaw framework with single VLM-driven controller
- Three-level abstraction: Skills, Tools, Policies
- EAP (Entangled Action Pairs) for self-resetting data collection
- Structured memory: role identity, task-level memory, working memory
- CoT reasoning
- MCP interface
- π0.5 VLA model as low-level policy

3. Experiments: 
- AgiBot G01 dual-arm mobile platform
- Four scenarios: vanity table, kitchen shelf, study desk, convenience store shelf
- Four tasks: Body Lotion, Primer, Lipstick, Tissue Wipe
- Compared with manual baseline and two baselines for long-horizon

4. Resources: Not explicitly mentioned GPU details. Only mentioned π0.5 fine-tuning with LoRA settings (rank 16, alpha 16, etc.) and 10k training steps.

5. Experiment count: 4 main research questions, success rate tables, human effort comparisons, 20 trials for main results.

6. Conclusions: 25% improvement in success rate, 53.7% reduction in human effort.

7. Strengths: Unified framework, EAP mechanism, closed-loop learning from failures.

8. Limitations: Cloud-based VLM latency, assumption of practical inverse reset behaviors.

Let me write this in Chinese with proper Markdown formatting.</think>

# RoboClaw 论文总结

## 一、核心问题与研究动机

- **核心问题**：视觉-语言-动作（VLA）系统在语言驱动的机器人操控方面具有显著潜力，但将其扩展到复杂的**长视野（long-horizon）任务**时面临系统性挑战：
  - 现有流程将**数据采集、策略学习、任务部署**三个阶段彼此分离，由不同人员或流程处理，导致任务状态语义、子任务边界、成功标准等在阶段间产生**信息断层**。
  - 真实机器人数据采集严重依赖**人工环境复位、轨迹筛选与监督**，随着任务复杂度提升，人力成本急剧上升。
  - 训练数据的状态分布与部署阶段的状态分布不一致，导致**训练-执行失配**，微小错误在长视野任务中容易被级联放大。
- **关键矛盾**：缺乏一个能跨数据采集、策略学习与任务执行全生命周期的**统一语义表征与决策机制**，从而限制了语言驱动机器人系统的可扩展性。

## 二、方法论

### 2.1 整体框架：RoboClaw 代理式架构
- 采用一个**现成的视觉-语言模型（VLM）作为元控制器（meta-controller）**，通过**上下文学习（ICL）**结合结构化记忆进行高层推理。
- 三个层级抽象：
  - **Policies**：底层 VLA 模型（本工作采用 π0.5），输出低层电机动作；
  - **Tools**：可调用系统接口（启动/终止策略、环境摘要、查询机器人状态、呼叫人类等），通过 **MCP（Model Context Protocol）** 暴露；
  - **Skills**：可复用的高层流程，编排 Tools 完成子任务。
- **结构化记忆**包含三部分：
  - `r_t`：角色身份（决定当前操作模式与可用工具集）；
  - `g_t`：任务级记忆（全局任务、子任务分解与执行状态）；
  - `w_t`：工作记忆（当前激活的技能、近期工具调用历史）。
- **决策循环**：每步 `t`，VLM 基于观察 `o_t` 和记忆 `m_t` 进行**链式思考（CoT）**推理 → 调用工具 → 执行底层策略 → 更新记忆，形成"感知-推理-动作"闭环。

### 2.2 自主数据采集：纠缠动作对（EAP）
- **核心思想**：对每个操控策略 `k`，同时学习一对**前向执行策略** `π→_{θ_k}` 和**反向复位策略** `π←_{φ_k}`，二者首尾相连形成**自复位循环**。
- 前向轨迹 `τ→_k` 完成操控后，触发反向轨迹 `τ←_k`，机器人自主恢复至**可复用的前置条件区域**，无需人工介入。
- 一对纠缠动作定义为：`τ_k = (τ→_k, τ←_k)`，并存储到数据集 `D` 中用于后续策略训练。
- 反向任务被刻意设计为**比前向任务更简单**，以保证复位成功率，从而维持自复位循环的稳定。

### 2.3 底层策略学习（π0.5 微调）
- 底层 VLA 策略 π0.5 联合处理视觉观察、指令（由 RoboClaw 代理动态生成）和机器人本体感受状态，预测长度为 `H` 的**动作块（action chunk）** `A_t`：
  - `A_t = π0.5(o_t, l_t, q_t)`，`A_t = [a_t, …, a_{t+H-1}]`
- 训练目标为**条件流匹配（conditional flow matching）**：
  - `L_τ(θ) = E_{p(A_t|o_t,l_t,q_t), q(A_t^τ|A_t)} [ ‖v_θ(A_t^τ, o_t, l_t, q_t) − u(A_t^τ | A_t) ‖² ]`
  - 其中 `A_t^τ = (1−τ)ε + τA_t`，从高斯噪声线性插值到真实动作分布。

### 2.4 部署时的过程监督与技能调度
- 部署阶段使用相同的代理闭环：基于观察与结构化记忆选择子任务 → 调用前向策略 → 通过 `Fetch Robot Stats` 和 `Env Summary` 周期性监控进度。
- 失败处理分级：
  - **可重试**：简单重试同一策略；
  - **可恢复**：通过 `Change Policy` 切换到其他前向策略或重规划；
  - **需人工**：通过 `Call Human` 工具升级到人工干预；
- **闭环生命周期学习**：部署阶段产生的轨迹会回灌到数据集 `D`，与采集阶段共享相同的决策循环与语义上下文，实现技能库的持续扩充与策略迭代优化。

## 三、实验设计

### 3.1 平台与环境
- **硬件平台**：AgiBot G01 双臂移动操控机器人，底盘移动 + 双臂 20 自由度，每臂配备 AGIBOT OmniPicker 自适应夹爪。
- **场景**：四个真实环境
  - 卧室梳妆台（vanity table）
  - 厨房储物架
  - 书房书桌
  - 便利店货架
- **子任务**：四类代表性操控
  - Body Lotion（身体乳）：大范围搬运；
  - Primer（隔离霜）：放置后需关闭抽屉，存在遮挡与间隙问题；
  - Lipstick（口红插入）：紧容差插孔，对齐要求高；
  - Tissue Wipe（纸巾擦拭）：依赖持续表面接触的连续运动。

### 3.2 对比方法
- **数据采集对比**：纯人工采集（人工示范 + 人工复位）作为基线。
- **长视野任务对比**：
  - **Baseline 1**：在相同数据集上训练的纯 π0.5 模型，不使用 RoboClaw 框架；
  - **Baseline 2**：以四个独立子任务成功率之积作为期望成功率的估计。

### 3.3 评测指标
- 子任务成功率（每 50 次试验）；
- 归一化人类时间投入（人工 vs. EAP）；
- 人工干预次数；
- 长视野任务整体成功率。

## 四、资源与算力

- 论文**未明确披露**具体的 GPU 型号、数量、训练时长等硬件资源信息。
- 仅在表 1 中提供了 **π0.5 微调的超参数**：
  - 精度 bfloat16、batch size 16、训练步数 10k、warmup 100 步、学习率 2.5×10⁻⁵、推理步数 3、启用梯度检查点；
  - LoRA 设置：rank=16，alpha=16，dropout=0.1，目标模块为 all-linear。
- 主要资源承诺集中在 AgiBot G01 机器人平台及多场景真实环境部署上。

## 五、实验数量与充分性

- **四组核心实验**分别回答四个研究问题（数据采集效率、子任务成功率、长视野任务表现、从失败中学习）。
- **逆向复位策略成功率**：四任务各 50 次试验，结果 36/50 – 43/50（表 2）。
- **前向策略迭代训练**：1–5 次迭代，每次追加 50 条 EAP 数据，共 250 次试验/任务（表 3）。
- **长视野任务**：20 次试验的成功率曲线（图 4c），比较 RoboClaw 与两个基线。
- **人类工作量**：分别在采集阶段与 rollout 阶段进行归一化对比（图 4a、4b）。
- **充分性评价**：
  - 优点：覆盖了采集效率、单策略鲁棒性、长视野组合、失败恢复四个维度，逻辑链条清晰；包含迭代训练曲线，能够体现 EAP 的渐进收益。
  - 不足：单一机器人平台（AgiBot G01）、单一底层 VLA 模型（π0.5）、真实环境试验次数（每任务最多 250 次）相对有限，缺少跨平台、跨模型、跨场景的泛化验证；缺少与近期其他代理式机器人框架（如 Agentic Robot、HAMSTER、HiRobot）的直接对比。

## 六、主要结论与发现

- **EAP 自复位机制有效**：将人类采集工作量降低约 **53.7%**（人工时间相对值约 2.16×，人工干预相对值约 8.04×）。
- **迭代 rollout 持续提升策略性能**：随着训练数据从 50 增加到 250 条样本，所有前向策略的成功率单调上升，例如 Lipstick 从 2/50 提升到 23/50，Tissue Wipe 从 11/50 提升到 26/50。
- **长视野任务显著优于基线**：在梳妆台整理任务上，RoboClaw 比 Baseline 1 高 **25%**，并显著超过"子任务成功率之积"的期望值，说明代理的**过程监控与恢复策略调用**对组合任务至关重要。
- **失败学习**：系统将失败分为"非退化"（可重试）与"退化"（需恢复动作）两类；随着执行经验积累，恢复行为被沉淀为专门的**恢复策略**，自主恢复能力逐渐提升。
- **统一生命周期**：部署轨迹回灌训练集，使执行本身成为持续学习的来源。

## 七、优点与亮点

- **统一的代理式框架**：用同一个 VLM 控制闭环贯穿数据采集、策略学习、部署全过程，解决阶段间语义断层问题。
- **EAP 设计简洁而有效**：将"复位动作"显式建模为对偶策略，比手工设计"失败检测+人工复位"更自动化，且训练分布与执行分布更一致。
- **过程监督与分级恢复**：在部署时引入显式的状态监控、子任务评估与"重试-恢复-求助"三级策略，显著降低长视野任务中的错误级联。
- **闭环生命周期学习**：执行产生的轨迹自动回灌训练集，使系统具备持续进化的能力，符合"agentic"理念。
- **真实场景、真实硬件**：在多种真实家居/零售场景中进行端到端验证，而非仅依赖仿真。

## 八、不足与局限

- **云端 VLM 延迟**：依赖大模型进行高层推理，部署时可能引入不可忽视的延迟，影响实时性，论文已自承该问题。
- **逆向策略的实用性假设**：EAP 假设每个前向任务都能找到一个**简单的逆操作**实现自复位，这在复杂或不可逆的任务（例如破坏性操作、烹饪化学反应等）中可能不成立，限制方法的可推广范围。
- **数据/算力披露不充分**：缺少 GPU 型号/数量、训练总时长、数据总规模等关键信息，复现成本难以评估。
- **实验规模与多样性有限**：仅在 AgiBot G01 单一平台上验证，任务集局限于四个相对简单的桌面操作；缺少更复杂的多阶段、移动操控、长序列任务。
- **基线选择不全面**：未与 RoboCopilot、Genie Centurion、FieldGen、Agentic Robot、HAMSTER 等近期代理式或闭环数据采集方法做直接对比，难以判断相对优势。
- **统计显著性未充分讨论**：每任务 50 次试验、20 次长视野试验的置信区间与显著性检验未在文中呈现，结论的稳健性需进一步验证。
- **依赖人工兜底**：尽管减少了 53.7% 人工投入，但仍需 `Call Human` 兜底；在完全无人值守场景下的可靠性尚未充分论证。
- **数据偏置与场景泛化**：四项任务均在受控的家居/零售环境中进行，物体外观、布局变化有限，模型在高度多样化场景下的鲁棒性未知。

（完）
