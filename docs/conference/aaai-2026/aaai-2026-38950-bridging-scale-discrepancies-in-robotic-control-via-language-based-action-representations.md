---
title: Bridging Scale Discrepancies in Robotic Control via Language-Based Action Representations
title_zh: 通过基于语言的动作表示弥合机器人控制中的尺度差异
authors: "Yuchi Zhang, Churui Sun, Shiqi Liang, Diyuan Liu, Chao Ji, Weinan Zhang, Ting Liu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38950/42912"
tags: ["query:rob-il"]
score: 7.0
evidence: 基于语言的动作表示解决机器人控制中的尺度差异
tldr: 本文针对机器人动作数据分布偏移阻碍预训练的问题，提出基于语义的语言动作表示，忽略数值尺度差异，强调方向性。该方法将机器人动作归一化为统一表示，使预训练更有效。实验证明该表示提升了跨平台和任务的动作学习效果，促进了机器人控制的鲁棒性和泛化能力。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38950/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1844, \"height\": 476, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38950/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1391, \"height\": 725, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38950/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 732, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 817, \"height\": 383, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 380, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 787, \"height\": 384, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 768, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 765, \"height\": 434, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38950/table-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 856, \"height\": 472, \"label\": \"Table\"}]"
motivation: 机器人动作数据存在严重分布偏移，阻碍预训练知识迁移。
method: 提出语义化的语言动作表示，忽略数值尺度，强调方向性。
result: 实验显示该方法提升了跨平台和任务的动作学习效果。
conclusion: 语言表示有效促进了机器人控制的预训练和迁移。
---

## Abstract
Recent end-to-end robotic manipulation research increasingly adopts architectures inspired by large language models to enable robust manipulation. However, a critical challenge arises from severe distribution shifts between robotic action data, primarily due to substantial numerical variations in action commands across diverse robotic platforms and tasks, hindering the effective transfer of pretrained knowledge. To address this limitation, we propose a semantically grounded linguistic representation to normalize actions for efficient pretraining. Unlike conventional discretized action representations that are sensitive to numerical scales, the motion representation specifically disregards numeric scale effects, emphasizing directionality instead. This abstraction mitigates distribution shifts, yielding a more generalizable pretraining representation. Moreover, using the motion representation narrows the feature distance between action tokens and standard vocabulary tokens, mitigating modality gaps. Multi-task experiments on two benchmarks demonstrate that the proposed method significantly improves generalization performance and transferability in robotic manipulation tasks.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机与背景）

* **核心问题**：不同机器人平台和任务产生的动作指令存在显著的数值尺度差异（如位置增量、旋转角度、抓取状态等），导致多源数据集之间存在严重分布偏移。这种偏移阻碍了预训练知识在新任务上的有效迁移，使得现有端到端模型通常需要大量微调才能在新场景中表现良好。
* **整体意义**：现有方法如 RT-2、OpenVLA、Octo 虽然借鉴了大规模语言模型架构，但动作数据的数值分布不一致仍是泛化瓶颈。论文提出一种基于语义的语言动作表示（motion representation），通过忽略具体数值尺度、强调方向性，将动作统一为粗粒度的自然语言描述，从而弥合不同来源数据之间的分布差异，提升预训练的效率与可迁移性。

## 2. 方法论：核心思想、关键技术细节与算法流程

### 核心思想
* 将连续机器人动作（7维：ΔX, ΔY, ΔZ, Δroll, Δpitch, Δyaw, GripperState）映射为固定的自然语言结构，如 `move forward/backward left/right up/down, tilt up/down, rotate clockwise/counterclockwise, open/close gripper`，以及表示无动作的 `stop`。
* 利用这一中间表示作为两阶段训练的语义目标：先学习从观测和指令生成运动语言，再结合运动语言生成具体的离散动作token。

### 关键技术细节

#### 动作分词器（Action Tokenizer）
* 连续动作归一化（排除1%和99%之外的离群点），每个维度离散化为256个bin，每个bin对应一个特殊token（<extra_0>~<extra_255>），使动作预测转化为token序列预测。

#### 运动生成（Motion Generation）
* **阈值自适应**：考虑高速运动引起的抖动，引入速度校正项，公式：  
  \( T_i(t) = T_i^{base} + \beta \cdot \frac{1}{\tau} \sum_{s=t-\tau}^{t} |\hat{\Delta}_i(s)| \)  
  即基本阈值加上窗口内的平均位移绝对值乘以敏感系数。
* **分层窗口检测**：使用三个时间分辨率的窗口（fast, mid, slow），分别对应快速、中等、缓慢运动：
  - \( M_f \): 单位步位移 > 2T（快速运动）
  - \( M_m \): 窗口内累积位移 > T 且每一步位移 > 0（中等运动）
  - \( M_s \): 大窗口内累积位移 > T 且方向稳定，同时每步位移 > T/(2Δt_s)（慢速运动）
  - 最终判定：\( \text{Motion}(t) = M_f(t) \lor M_m(t) \lor M_s(t) \)
* 该自适应分层方法相比固定阈值（如ECoT）显著提升动作标注准确率（86.37% vs 57.62%），有效抑制抖动误判。

#### 两阶段训练
* **第一阶段（预训练）**：仅预测运动token。输入格式为：`<START>system...<STOP> <START>user What action should the robot take to {instruction}?<STOP> <START>motion {motion}<STOP>`，只计算绿色部分损失（motion token）。
* **第二阶段（微调）**：预测运动token和动作token。输入格式扩展为：`... <START>motion {motion}<STOP> <START>assistant {action}<STOP>`，同时计算两部分损失。
* 模型架构基于OpenVLA，使用SigLIP和DINOv2编码图像，LLM采用Qwen2.5（0.5B/1.5B/3B），增加256个特殊动作token。

## 3. 实验设计：数据集、Benchmark与对比方法

### 数据集
* **预训练**：Open X-Embodiment（OXE）的7个子集，包括furniture-bench、jaco等，总计约12,000条轨迹。刻意排除LIBERO和Bridge V2，以测试零样本迁移。
* **微调/评估**：
  - **LIBERO**：130+语言条件操作任务，四个套件：Spatial, Goal, Object, Long。
  - **SimplerEnv**（基于Bridge V2的仿真环境）：四个任务：Place a spoon on a towel, Place a carrot on a plate, Stack a green block on a yellow block, Place an eggplant in a yellow basket。

### 对比方法
* **Baselines**：Diffusion Policy, ScaleDP, Octo, OpenVLA, RT-1-x, ECoT。涵盖了扩散策略、视觉-语言-动作模型、基于Transformer的策略等类别。

### 评估指标
* 成功率（Success Rate），多次运行报告均值和标准差。

## 4. 资源与算力
* **GPU型号**：所有实验在A100-80G GPU上运行。
* **数量与时长**：文中未明确说明具体使用的GPU数量和每阶段训练时长。提到预训练batch size=2048，微调batch size=512，学习率2e-5。详细的计算效率、推理时间等信息在Appendix C，但提取文本中未包含附录内容，因此无法提供更精确的算力消耗。
* **模型规模**：Qwen2.5（0.5B/1.5B/3B）以及OpenVLA（7B）的对比实验，说明不同规模下的表现。

## 5. 实验数量与充分性
* **总体实验数量**：超过6组对比实验（表3-9），包括：
  - 从零训练 vs. 预训练后微调（Table 3 vs 5, 4 vs 6）
  - 带运动token vs. 不带运动token（w/ motion vs w/o motion）
  - 原始运动生成方法 vs. 优化运动生成方法（Table 7）
  - 不同模型大小（0.5B, 1.5B, 3B）
  - 与多个SOTA对比（Table 8, 9）
* **消融实验**：明确验证了阈值自适应和分层窗口的贡献（Table 7: Ours vs raw motion vs w/o motion）。
* **充分性评价**：
  - 公平：均在同一基准和评估流程下进行，报告置信区间。
  - 客观：两次以上独立运行并报告标准差。
  - 覆盖全面：涵盖多个任务类型（空间、目标、物体、长时序）、多种模型尺寸、有无预训练等关键变量。
  - 但注意到简化任务“Stack Blocks”在所有方法上成功率为0，可能因环境差异或任务本身难度过高，导致该子集区分度不足。

## 6. 主要结论与发现
1. **运动token显著提升性能**：无论从零训练还是基于预训练，加入运动token的模型在LIBERO和SimplerEnv上平均成功率均更高（例：3B模型在LIBERO提升+6.9%，在SimplerEnv提升+14.1%）。
2. **预训练带来的增益更明显**：经过运动预训练后再微调的模型，比直接从头训练的模型表现更优，说明运动表示有助于捕获通用的方向性知识。
3. **自适应阈值与分层窗口有效**：相比ECoT的固定阈值方法，提出的运动生成方法将标注准确率从57.62%提升至86.37%，并消除了抖动引起的误分割。
4. **表示对齐可视化**：PCA分析显示，加入运动token后，动作token的嵌入与原始词汇token的特征距离变小，模态差异缩小，有助于更高效的训练。
5. **规模效应**：3B模型性能最佳，1.5B在SimplerEnv上增益有限，可能受限于仿真环境与现实数据间的差距（Sim-to-Real gap）。

## 7. 优点：方法与实验设计的亮点
* **方法创新性**：
  - 提出用自然语言作为中间动作表示，忽略数值尺度、聚焦方向性，从根本上缓解分布偏移。
  - 自适应多尺度运动检测算法（阈值+分层窗口）增强了跨数据集鲁棒性，无需人工标注外部模块。
  - 两阶段训练（先粗后细）符合课程学习思想，提高预训练效率。
* **实验设计亮点**：
  - 在预训练中刻意排除目标评估集，保证零样本迁移评估的公平性。
  - 多维度消融（有无运动、原始vs优化、不同大小），清晰证明各组件贡献。
  - 可视化PCA嵌入证明动作-语言模态差距缩小，提供直观解释。

## 8. 不足与局限
* **实验覆盖方面**：
  - 预训练仅使用了OXE的7个子集（约12K轨迹），相对于全部OXE数据规模较小，更多数据可能带来更强泛化。
  - 所有测试均在仿真环境（LIBERO、SimplerEnv）中进行，未在真实机器人上验证，Sim-to-Real泛化能力未知。
  - “Stack Blocks”任务成功率均为0，说明精细操作仍是挑战，运动表示的粗粒度可能不足以支撑高精度任务。
  - 1.5B模型在SimplerEnv上增益微弱甚至下降，提示模型大小与环境域间存在非线性关系，需进一步调优。
* **方法本身局限**：
  - 运动语言描述基于固定模板（如move/tilt/rotate），可能无法表达所有细粒度或非常规动作，存在表达能力上限。
  - 规则生成运动依赖准确的分层窗口参数，虽自适应但仍需手动设定基本阈值和窗口尺寸，可能对极端新域敏感。
  - 两阶段训练增加了训练流程复杂度，且需额外运动标签生成步骤。
* **计算资源**：未明确给出GPU数量和训练耗时，难以复现成本；对于更大规模模型（如7B+）实验尚缺。
* **偏差风险**：数据分布仍可能偏向OXE和Bridge V2等特定数据集风格，其他领域（如双机械臂、移动操作）未验证。

（完）
