---
title: "TCoT: Trajectory Chain-of-Thoughts for Robotic Manipulation with Failure Recovery in Vision-Language-Action Model"
title_zh: "TCoT: 基于轨迹思维链的具身操控失败恢复视觉-语言-动作模型"
authors: "Xiang Li, Ya-Li Li, Yuan Wang, Huaqiang Wang, Shengjin Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/37577/41539"
tags: ["query:rob-il"]
score: 9.0
evidence: 结合轨迹思维链的视觉-语言-动作模型，用于机器人操控的失败恢复
tldr: 针对视觉-语言-动作(VLA)模型缺乏中间规划与失败恢复能力、难以完成长时域任务的问题，提出了TCoT框架。该框架将轨迹思维链引入VLA模型，使模型能够逐步规划动作、检测失败并纠正错误。实验表明，TCoT显著提升了在复杂长序列任务上的成功率和泛化能力，增强了VLA模型的实用性和可靠性。该工作为VLA模型向更自主的机器人操控演进提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37577/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 868, \"height\": 774, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37577/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1839, \"height\": 673, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37577/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 853, \"height\": 610, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37577/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1786, \"height\": 609, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-37577/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 831, \"height\": 496, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37577/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 886, \"height\": 707, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37577/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1739, \"height\": 388, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37577/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 264, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37577/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 863, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-37577/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 769, \"height\": 276, \"label\": \"Table\"}]"
motivation: VLA模型缺乏任务规划和失败恢复能力，导致长时域任务失败率高。
method: 提出TCoT框架，在VLA模型中集成轨迹思维链用于规划、检测和恢复。
result: 在复杂操控任务上，TCoT显著提升成功率和泛化性，尤其长时域任务。
conclusion: TCoT有效增强了VLA模型的规划与容错能力，扩展了其应用范围。
---

## Abstract
Recent advances in vision-language-action (VLA) models
have demonstrated impressive generalization for robotic manipulation.
However, these models often operate by directly mapping visual and linguistic inputs to subsequent actions, lacking intermediate task planning, along with failure detection and recovery ability.
These limitations prevent them from effectively decomposing complex tasks, recognizing problems, and correcting erroneous actions, ultimately resulting in complete task failure. This significantly hinders their ability to perform long-horizon tasks and generalization ability.
To this end, we introduce TCoT: Trajectory Chain-of-Thought, a unified VLA framework that enhances this direct mapping with trajectory planning as well as failure detection and recovery.
TCoT leverages hierarchy trajectories as a precise and compact representation of CoT reasoning for manipulation: global planning provides a high-level, goal-oriented trajectory to guide the robot toward its task objective, while local planning focuses on real-time adjustments to address dynamic changes.
Moreover, we designed the Global-Local Switching Recovery algorithm that detects and effectively recovers from failures. 
Experimental results reveal that TCoT surpasses the state-of-the-art methods across both real and simulated scenarios and exhibits superior generalization capabilities.

---

## 论文详细总结（自动生成）

以下是对论文《TCoT: Trajectory Chain-of-Thoughts for Robotic Manipulation with Failure Recovery in Vision-Language-Action Model》的详细中文总结，按照指定要点依次展开。

### 1. 核心问题与整体含义（研究动机和背景）

- **当前瓶颈**：现有的视觉-语言-动作（VLA）模型虽然在机器人操控上展现了不错的泛化能力，但普遍直接将高层的视觉和语言输入映射为低层动作，**缺乏中间任务规划**（无法将复杂任务分解为子步骤）以及**失败检测与恢复能力**。这导致机器人在长时域（long-horizon）任务中容易反复执行已完成的动作或陷入死循环，且一旦出错无法主动纠正，最终造成任务整体失败。
- **研究目标**：为了解决上述问题，论文提出 **TCoT（Trajectory Chain-of-Thought）** 框架，旨在增强VLA模型的结构化推理能力，使其能够像人类一样先规划路径、实时调整，并在失败时切换策略，从而提升复杂操控任务的成功率与鲁棒性。

### 2. 论文提出的方法论

- **核心思想**：利用分层轨迹（Hierarchical Trajectory）作为中间推理表示（CoT），在VLA模型中引入显式的规划层和失败恢复机制。轨迹是二维图像坐标系下的末端执行器路径点序列，兼具紧凑性与可解释性。
- **关键技术细节**：
  - **全局轨迹规划（Global Planning）**：通过对称窗口采样，生成覆盖较长时段（含过去和未来）的稀疏路径点，提供任务级导向，帮助模型评估进度并保持目标一致性。
  - **局部轨迹规划（Local Planning）**：以更高频率和更密间隔采样较短时段内的路径点，用于实时调整和精细操控，适应动态变化。
  - **失败检测与恢复（GLSR算法）**：
    - 在在线 rollout 中收集成功/失败样本，用二值标签训练模型预测任务是否完成（`Isuccess`）。
    - 推理时，当检测到失败（`Isuccess=False`），主动从全局规划切换到局部规划，重新生成可替换的轨迹段进行恢复，避免简单重复错误行为。
  - **训练流程**：采用 LoRA 微调预训练 VLA 主干（以 OpenVLA 为例），联合优化三个损失：动作预测损失 $L_a$、轨迹预测损失 $L_p$、失败检测损失 $L_f$。通过不同的提示模板（`lg/l` 和 `lf`）统一调用轨迹规划、动作生成与失败检测功能。
- **公式与算法**（文字说明）：
  - 行动定义为7维增量：$[\Delta p, \Delta \theta, gripper]$。
  - 全局轨迹采样：$P_t^g = \{ p_{t-n_g\lfloor L_g/2\rfloor}, ..., p_t, ..., p_{t+n_g\lfloor L_g/2\rfloor} \}$。
  - 局部轨迹采样：$P_t^l = \{ p_t, p_{t+n_l}, ..., p_{t+n_l L_l} \}$（$n_l < n_g$）。
  - 失败检测通过训练模型预测 $I_{t}^{\text{success}}$ 实现。
  - GLSR 算法：初始生成全局轨迹；在时间步 $t_f$ 后，每隔 $t_l$ 步检测一次 `Isuccess`，若为假则切换到局部规划重新生成轨迹与动作。

### 3. 实验设计

- **仿真环境**：使用 **LIBERO benchmark**，包含四个任务套件：
  - LIBERO-Spatial（空间关系，10任务）
  - LIBERO-Object（物体操控，10任务）
  - LIBERO-Goal（目标导向，10任务）
  - LIBERO-Long（长时域，10任务）
  - 每个任务提供50个人类遥操作演示。
- **真实环境**：使用 **AIRBOT 机械臂**，设计7个实际任务，涵盖堆叠、移除、放置、工具使用等（如堆方块、取碗、放瓶子、用勺子等）。
- **对比方法**（离散动作模型）：
  - OpenVLA, OpenVLA-Multi, ECoT, GRAPE, CoT-VLA
- **连续动作模型对比**：π0, UniVLA, OpenVLA-OFT
- **评估指标**：成功率（Success Rate, SR）。

### 4. 资源与算力

- **文中未明确说明**使用的 GPU 型号、数量或总训练时长。仅提及使用 LoRA 进行高效微调，但未提供具体硬件配置或计算开销。因此无法给出确切算力信息。

### 5. 实验数量与充分性

- **实验组数**：
  - LIBERO 上进行了单任务（每个套件分别训练/评估）和多任务（所有40个任务联合训练）两组对比。
  - 实时场景下同样进行了单任务和多任务对比。
  - 消融实验分别验证了全局轨迹、局部轨迹、GLSR 三个组件的贡献（4种设置）。
  - 另外在连续动作模型上也进行了对比（表2）。
- **充分性**：整体实验设计较为全面，覆盖了仿真和真实环境，对比了多种 SOTA 方法，并通过消融明确了各组件的必要性。每组结果均提供了多次重复的平均值和标准误差，统计上相对可靠。
- **公平性**：所有方法基于相同主干或公开实现，评估协议一致，对比公平。但真实场景只有7个任务，且未报告跨场景的零样本迁移，泛化性验证有限。

### 6. 论文的主要结论与发现

- **性能提升**：TCoT 在 LIBERO 所有套件上的平均成功率均超过现有方法，尤其在长时域任务（LIBERO-Long）上提升显著（+12.8% vs. OpenVLA）。
- **多任务泛化**：在多任务设置下，TCoT 相比单任务进一步提升（83.3% vs. 82.9%），而基线 OpenVLA 反而下降，说明轨迹表示能有效促进任务间的知识共享。
- **失败恢复有效性**：GLSR 机制是性能改善的关键（消融实验显示开启后平均成功率提高6.4%），显式策略切换比 VLA 的隐式重试更可靠。
- **工具使用与复杂操作**：在真实实验中，TCoT 在工具使用和多步长任务上的优势更明显，平均成功率相对OpenVLA提升28%（单任务）和75%（多任务）。

### 7. 优点

- **创新性**：首次将分层轨迹规划与失败检测恢复整合进统一的VLA框架，形成“规划-执行-检测-恢复”的闭环，思路新颖。
- **实用性强**：自动数据生成流水线（利用跟踪、分割模型）降低了人工标注成本；LoRA 微调使方法易于扩展。
- **消融设计清晰**：通过逐步添加组件验证了全局、局部、GLSR 各自的贡献，实验归因明确。
- **泛化能力**：多任务实验中表现优于单任务，证明轨迹中间层有助于抽象共享知识。
- **多场景验证**：同时提供仿真与真实机器人实验，增强了结果的可信度。

### 8. 不足与局限

- **实验覆盖**：真实世界任务数量较少（7个），且未包含密集抓取、物体堆叠中的物理干扰、环境变化等更复杂的动态场景，泛化性验证不够全面。
- **偏差风险**：轨迹生成依赖预训练的跟踪与分割模型（CoTracker、SAM2），这些模型在遮挡或快速运动时可能出现不准确，从而影响训练数据质量，但文中未深入分析该影响。
- **资源与可重复性**：未提供代码或模型权重，也未报告训练所需算力，不利于他人复现与比较。
- **未讨论灾难性遗忘**：在多任务或持续学习场景下，LoRA 微调后模型是否会遗忘原有能力未探讨。
- **应用限制**：当前方法基于2D图像轨迹，对于需要精密3D操作或力反馈的任务可能不够；GLSR 的切换阈值（如 `tf` 和 `tl`）需根据任务手工设定，缺乏自适应机制。
- **统计细节**：虽然报告了标准误差，但未做显著性检验（如 t 检验），提升是否统计显著不够明确。

（完）
