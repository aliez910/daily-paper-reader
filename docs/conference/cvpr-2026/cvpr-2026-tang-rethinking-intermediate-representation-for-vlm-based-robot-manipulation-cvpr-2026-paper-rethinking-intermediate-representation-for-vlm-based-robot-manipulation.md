---
title: Rethinking Intermediate Representation for VLM-based Robot Manipulation
title_zh: 重新思考面向机器人操作的 VLM 中间表征
authors: "Tang, Weiliang, Gao, Jialin, Pan, Jia-Hui, Wang, Gang, Li, Li Erran, Liu, Yun-Hui, Ding, Mingyu, Heng, Pheng-Ann, Fu, Chi-Wing"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Tang_Rethinking_Intermediate_Representation_for_VLM-based_Robot_Manipulation_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 利用 VLM 设计中间表征以将指令翻译为可执行的操作动作
tldr: 在使用视觉语言模型将人类指令翻译为可操作中间表征时，常面临可理解性与泛化性的权衡。本文受上下文无关文法启发，提出语义装配表征 SEAM，将中间表征分解为语义丰富的词汇表与 VLM 友好的语法规则，并结合开放词汇分割实现精细部件定位。实验表明该方法在多种未见操作任务上提升了鲁棒性与泛化能力，为下游视觉运动策略提供了一种可复用的表征方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1751, \"height\": 854, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1791, \"height\": 1017, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1773, \"height\": 687, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 861, \"height\": 607, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 868, \"height\": 417, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 826, \"height\": 658, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 859, \"height\": 511, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 859, \"height\": 407, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1804, \"height\": 615, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 860, \"height\": 142, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-tang-rethinking-intermediate-representation-for-vlm-based-robot-manipulation-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 876, \"height\": 438, \"label\": \"Table\"}]"
motivation: VLM 用于机器人操作时，中间表征在可理解性与泛化性之间存在权衡。
method: 提出语义装配表征 SEAM，将中间空间分解为词汇表与语法，并结合开放词汇分割。
result: 在多种未见操作任务上提升了指令到动作的翻译鲁棒性与泛化性。
conclusion: 该工作为 VLM 驱动的机器人操作提供了一种通用中间表征设计方法。
---

## Abstract
Vision-Language Model (VLM) is now an important component to enable robust robot manipulation. Yet, using it to translate human instructions into an action-resolvable intermediate representation often needs a tradeoff between VLM-comprehensibility and generalizability. Inspired by context-free grammar structure, we design the Semantic Assembly representation named SEAM, by decomposing the intermediate representation into vocabulary and grammar. Doing so leads us to a concise vocabulary of semantically-rich operations and a VLM-friendly grammar for handling diverse unseen tasks. Also, we design a novel open-vocabulary segmentation paradigm with an in-context learning strategy to precisely localize fine-grained object parts for manipulation (e.g., cup handle, teapot opening) effectively with the shortest inference time over all state-of-the-art parallel works. We then formulate new metrics for action-generalizability and VLM-comprehensibility to evaluate mainstream representations, demonstrating the strong performance of SEAM on both aspects. Extensive real-world experiments further manifest the SOTA performance of SEAM under varying settings and tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Rethinking Intermediate Representation for VLM-based Robot Manipulation" following a specific structure with 8 points. Let me analyze the paper content carefully and organize the summary.

Key information from the paper:
- Problem: VLM-based robot manipulation has a tradeoff between VLM-comprehensibility and action-generalizability in intermediate representations
- Method: SEAM (Semantic Assembly representation) inspired by context-free grammar, decomposing into vocabulary and grammar; also includes RAG-based few-shot open-vocabulary segmentation
- Experiments: 8 tasks (6 rigid objects + 6 articulated), compared with VoxPoser, CoPa, ReKep, OmniManip
- Hardware: UR5 robot, dual Intel RealSense D435 cameras, Qwen3-VL-30B-22A on A100 GPU, Swin-B for segmentation
- Results: 15% improvement over prior SOTA in real-world tasks
- New metrics: action-generalizability (AG) and VLM-comprehensibility (VC)

Let me write a comprehensive Chinese summary.</think>

# 重新思考面向机器人操作的 VLM 中间表征（SEAM）——论文总结

## 1. 核心问题与研究动机

- **背景**：视觉-语言模型（VLM）已成为机器人操作的关键组件，其典型范式是将人类指令翻译为「中间表征」（intermediate representation），再由求解器转换为机器人动作，从而避免端到端 VLA 模型对大量标注数据的依赖。
- **核心矛盾（Trade-off）**：现有中间表征方案存在两种极端：
  - **高层表征**（如 Code-as-Policies、Instruct2Act）：使用预定义的语义技能词（`grasp_center`、`cut`、`move_perpendicular` 等），VLM 易理解但**缺乏跨任务泛化能力**，每遇到新任务都需手工新增词汇。
  - **底层表征**（如 ReKep、OmniManip、GeoManip）：使用关键点、轴、几何约束等基础原语，泛化力强但**表征复杂、生成门槛高**，VLM 难以可靠生成（如 ReKep 需生成显式的代价/约束代码）。
- **研究问题**：能否设计一种同时具备「VLM 可理解性（VLM-comprehensibility）」与「动作泛化性（action-generalizability）」的中间表征？

## 2. 方法论

### 2.1 核心思想：Semantic Assembly Representation (SEAM)

- **灵感来源**：借鉴「上下文无关文法（Context-Free Grammar, CFG）」的范式，将中间表征解耦为：
  - **词汇表 V（Vocabulary）**：一组语义丰富、贴近自然语言的原子操作。
  - **语法 G（Grammar）**：一组规定类型与组合规则的产生式规则，确保组合的合法性与可靠性。
- **设计原则**（六大原则）：
  1. **VLM-Readability**：词汇语义贴近人类语言。
  2. **Proper Abstraction**：隐藏底层实现细节（如用 PCA 算轴），只暴露必要参数。
  3. **Conciseness**：词汇正交化，最小化语义重叠。
  4. **Reliability**：语法内置类型系统，约束 VLM 输出合法。
  5. **Proper Minimalism**：核心词汇最小，降低学习负担。
  6. **Composability**：模块化，可无缝扩展新原语。

### 2.2 SEAM 词汇表与语法示例

- **词汇 V 示例**（约 11 个核心词）：`get_axis`, `get_centroid`, `get_height`, `move_cost`, `parallel_cost`, `perpendicular_cost`, `rotate_cost`, `orbit_cost`, `gripper_close/open`, `get_gripper_pos`。
- **语法 G 示例**：
  - `cost → cost + cost`
  - `get_axis, object → vec`
  - `move_cost, pt, pt → cost`
  - `parallel_cost, vec, vec → cost`
- **翻译示例（切胡萝卜）**：
  ```python
  perpendicular_cost(get_axis("carrot"), get_axis("knife_blade"))
  + move_cost(get_centroid("knife"), get_centroid("knife_blade"), offset=[0,0,0.1])
  ```

### 2.3 基于 RAG 的少样本开放词汇分割

- **问题**：现有 SOTA 分割模型（OV-Seg、Grounded-SAM2、LISA、AffordanceNet）在细粒度部件（如茶壶开口、杯把）上表现不佳，常把整个物体或错误部件分割出来。
- **方案**：
  - 构建图像-掩码配对数据库 D = {(Ki, Pi)}，其中 Ki 为关键短语集合（如 `cup opening, cup rim, cup edge`），Pi 为 (支持图像, 支持掩码) 对。
  - 检索阶段：用 **Levenshtein 距离**匹配查询描述与关键短语，召回对应支持对。
  - 分割阶段：采用 Mapper 少样本分割网络（Swin-B 主干），基于支持特征与查询特征的注意力相似度，将支持掩码映射到查询掩码。
- **优势**：在所有对比并行工作中**推理时间最短（0.6s）**。

### 2.4 轨迹生成

- 中间表征为 Python 可执行代码，执行后得到点云的数值代价。
- 求解抓手目标位姿（R, t），优化公式：

  $$\min_{R,t} \ \text{cost}(P_s \cup R R_0^{-1}(P_m - t_0) + t) + \alpha \|t - t_0\|^2 + \beta \|\text{euler}(R R_0^{-1})\|_1$$

  - Pm：随抓手运动的点云；Ps：静止点云；后两项为位姿正则化。

### 2.5 整体流程

输入（任务指令 + 双目图像） → Qwen-VL 生成 SEAM 中间表征 → 解析为 Python 表达式 → RAG 数据库检索支持图像对 → Mapper 分割 → 点云求解 → UR5 机器人执行。

## 3. 实验设计

### 3.1 Benchmark 与任务设置

- **真实场景基准**：8 项任务，每项每方法执行 10 次（随机化物体位姿）：
  - 刚性物体任务：插笔入筒、回收电池、放杯/碗到碟、盖茶壶盖、按红色按钮。
  - 铰接物体任务：开抽屉、关抽屉、开罐子。
- **合成基准**：随机生成 **33 个单臂、无触觉/力反馈**操作任务，用于评估中间表征的可理解性与泛化性（由 DeepSeek 评判可执行性）。

### 3.2 对比方法

| 方法 | 类别 |
|------|------|
| VoxPoser | 低层（3D 价值图） |
| CoPa | 低层（部件级空间约束） |
| ReKep | 低层（关系关键点约束） |
| OmniManip | 低层（以物体为中心的交互原语） |
| **SEAM (本文)** | 中层（语义装配） |

### 3.3 评估指标

- **Action-Generalizability (AG)**：AG = 1 − |V|/T，词汇越少、任务越多 → AG 越高。
- **VLM-Comprehensibility (VC)**：VC = Nsucc/T，VLM 成功生成可执行表征的比例。
- **真实任务成功率**：每任务 10 次试验的成功率，区分闭/开环。

## 4. 资源与算力

- **机器人平台**：UR5 工业机械臂 + 夹爪作为末端执行器。
- **视觉模块**：两台 Intel RealSense D435 深度相机（工作区两侧），拼接双视图后输入 VLM。
- **VLM**：Qwen3-VL-30B-22A，部署在 **1 张 NVIDIA A100 GPU**。
- **分割网络**：Swin-B Transformer 主干 + Mapper 匹配器（论文未明确实时部署 GPU）；推理时间对比实验统一在 **A6000 GPU** 上进行。
- **训练时长**：未明确披露（多为使用现成预训练模型，少样本匹配器与 RAG 数据库构建未给出训练细节）。

## 5. 实验数量与充分性

- **真实任务实验**：8 项任务 × 4 种对比方法 × 闭/开环 × 10 次 = 约 640 次试验，结果详实。
- **指标评测实验**：33 个合成任务 × 4 种方法，覆盖词汇量、任务量与可理解性。
- **消融实验**：明确展示了 SEAM 与 RAG 分割两个组件的独立贡献（如图 5「插笔入筒」、图 6「盖茶壶盖」两个 case study）。
- **效率对比**：4 种分割方法的推理时间对比（Tab. 3）。
- **定性对比**：与 LISA、OV-Seg、Grounded-SAM2、AffordanceCup/Spout 等多种 SOTA 分割方法在 8 类部件上的可视化对比（图 3）。
- **充分性评估**：实验同时覆盖任务成功率、两个新指标、分割质量与推理速度，多维度较充分；但每个任务仅 10 次试验，统计显著性偏弱，且基准任务数量与场景多样性有限。

## 6. 主要结论与发现

- **核心结论**：VLM 中间表征的设计在可理解性与动作泛化性之间存在明确权衡，SEAM 是首个同时在两者上表现优异的设计。
- **性能提升**：SEAM 在真实世界任务上比 OmniManip（先前 SOTA）总体成功率提升 **15%**（闭环 83.8% vs 68.8%）。
- **分割效果**：RAG-based 分割在细粒度部件定位上明显优于现有开放词汇方法，且推理时间最短。
- **指标验证**：AG 与 VC 两个新指标能够清晰区分高层 vs 低层方法的优劣，验证了 trade-off 的客观存在。

## 7. 优点与亮点

- **理论视角新颖**：首次将 CFG 形式化思想引入 VLM 中间表征设计，提出词汇-语法解耦的通用框架。
- **可解释性强**：SEAM 表征为人类可读的 Python 代码，便于调试与扩展。
- **工程完备**：从表征设计、分割到轨迹优化形成闭环，并在 UR5 + 双 RealSense 真实平台上验证。
- **指标贡献**：提出 AG 与 VC 两个可量化、可对比的指标，填补了该领域缺乏系统化评测的空白。
- **分割效率**：RAG + Mapper 管线在 0.6 秒内完成部件级分割，兼顾精度与速度。
- **可视化充分**：通过 Figure 1 的高层 vs 低层 vs SEAM 三方对比，生动展示了设计动机与优势。

## 8. 不足与局限

- **真实任务规模有限**：仅 8 个任务、每个 10 次试验，统计置信度偏低；缺乏跨场景、多物体类别的大规模评测。
- **失败模式分析不足**：论文在结论中仅笼统提及两类失败原因（VLM 空间理解缺陷、遮挡/感知噪声），未给出定量的失败案例统计。
- **基准偏见风险**：合成 33 任务的「可执行性」由 DeepSeek 评判，引入了 LLM-as-a-judge 的潜在偏差，可能高估可理解性。
- **VLM 与算力依赖**：完全依赖闭源级 Qwen3-VL-30B + A100，复现门槛较高；未讨论小模型下的退化情况。
- **感知能力局限**：仅依赖两台固定 RGB-D 相机，对遮挡与小部件的鲁棒性有限；文中承认是关键失败源之一。
- **缺乏长期、力反馈任务**：场景局限于单臂、无触觉、无力反馈的桌面操作，未涉及长时序、技能组合或多机器人协作。
- **数据库构建成本**：RAG 数据库需要为每个部件预标注 (图像, 掩码) 对，扩展新部件时仍需人工介入，自动化程度有限。

（完）
