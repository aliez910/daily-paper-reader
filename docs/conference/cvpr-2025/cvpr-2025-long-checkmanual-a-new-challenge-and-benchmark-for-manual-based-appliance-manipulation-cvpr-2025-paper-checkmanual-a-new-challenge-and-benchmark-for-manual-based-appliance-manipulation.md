---
title: "CheckManual: A New Challenge and Benchmark for Manual-based Appliance Manipulation"
title_zh: CheckManual：基于说明书的家电操作新挑战与基准
authors: "Long, Yuxing, Zhang, Jiyao, Pan, Mingjie, Wu, Tianshu, Kim, Taewhan, Dong, Hao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Long_CheckManual_A_New_Challenge_and_Benchmark_for_Manual-based_Appliance_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向复杂家电操作任务的基准
tldr: 现有手册相关研究多停留在问答层面，而操作研究又忽视了多页说明书的指导价值。本文提出首个基于说明书的家电操作基准CheckManual，要求机器人先阅读多页说明书以理解部件功能、交互方式与任务步骤，再完成加热等复杂操作任务。该工作将自然语言理解与长程操作决策结合，为评估机器人在真实复杂环境中的操作能力提供了新的挑战性平台，具有推动说明书驱动操作研究的重要意义。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 343, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1800, \"height\": 817, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1810, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1795, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1799, \"height\": 378, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 874, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-long-checkmanual-a-new-challenge-and-benchmark-for-manual-based-appliance-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1796, \"height\": 390, \"label\": \"Table\"}]"
motivation: 现有研究在说明书理解与机器人操作之间存在明显割裂，前者停留在问答层面，后者忽视说明书的指导作用。
method: 构建首个基于多页说明书的家电操作基准，让机器人先阅读说明书再执行操作任务。
result: 提供了一个用于评估复杂操作任务的新挑战性基准数据集。
conclusion: CheckManual推动了说明书驱动的机器人操作研究，连接了语言理解与实际操作。
---

## Abstract
Correct use of electrical appliances has significantly improved human life quality. Unlike simple tools that can be manipulated with common sense, different parts of electrical appliances have specific functions defined by manufacturers. If we want the robot to heat bread by microwave, we should enable them to review the microwave's manual first. From the manual, it can learn about component functions, interaction methods, and representative task steps about appliances. However, previous manual-related works remain limited to question-answering tasks while existing manipulation researchers ignore the manual's important role and fail to comprehend multi-page manuals. In this paper, we propose the first manual-based appliance manipulation benchmark CheckManual. Specifically, we design a large model-assisted human-revised data generation pipeline to create manuals based on CAD appliance models. With these manuals, we establish novel manual-based manipulation challenges, metrics, and simulator environments for model performance evaluation. Furthermore, we propose the first manual-based manipulation planning model ManualPlan to set up a group of baselines for the CheckManual benchmark.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "CheckManual: A New Challenge and Benchmark for Manual-based Appliance Manipulation" organized into 8 specific sections. Let me analyze the paper content carefully and structure the response accordingly.

Let me go through each section:

1. **Core problem and overall meaning**: The paper addresses the gap between manual understanding (NLP, QA tasks) and robotic manipulation. Existing manipulation models can't read multi-page manuals to learn component functions, and existing manual datasets don't support manipulation evaluation.

2. **Methodology**: 
   - LLM-assisted human-revised manual generation pipeline based on CAD models
   - Analysis of real manuals (110 PDFs, 11 categories)
   - Appliance CAD models from PartNet-Mobility (11 categories, 182 models)
   - Part function name annotation using MLLM (GPT-4o)
   - Part function state annotation
   - Human verification
   - Manipulation task creation (LLM proposes, human verifies)
   - Manual figure design (covers, control panels, manipulation guidance)
   - LaTeX-based manual generation
   - ManualPlan model with 3 modules: Manual Resolution, Manipulation Planning, Part Alignment
   - CAD-assisted manipulation policy with primitive actions
   - CAD-free manipulation policy with VoxPoser

3. **Experimental design**:
   - Dataset: 1107 manuals for 369 appliances, 11 categories, 2211 parts, 1464 tasks
   - Three challenge tracks: Track 1 (CAD-Appliance Aligned Planning), Track 2 (Manual & CAD based Manipulation), Track 3 (Pure Manual-based Manipulation)
   - Metrics: alignment success rate, planning success rate, task execution success rate, task completion rate
   - Simulation: SAPIEN
   - Real robot: Franka Panda + RealSense D415
   - Compared with manual ablation (w/o manual)
   - Baseline: ManualPlan + Primitive Actions, ManualPlan + VoxPoser

4. **Resources and compute**: Not explicitly mentioned. The paper uses GPT-4o, Grounding-DINO, SAM, FoundationPose, VoxPoser, PaddleOCR, SDXL-Lightning. No specific GPU counts or training durations mentioned.

5. **Experiment count and sufficiency**: 
   - Three tracks with 11 appliance categories
   - Total results table showing per-category performance
   - Manual ablation study
   - Real robot deployment
   - The experiments are systematic but could be more comprehensive

6. **Main conclusions**:
   - ManualPlan can generate some correct task plans
   - MLLMs still struggle with aligning manual annotations to CAD models
   - Long-horizon manual-based manipulation is challenging
   - Manuals are crucial for task performance
   - Error accumulation is the main failure cause

7. **Strengths**:
   - First benchmark for manual-based appliance manipulation
   - Comprehensive data generation pipeline with human verification
   - Three difficulty levels
   - Aligned CAD models and manuals
   - Both simulation and real robot validation

8. **Limitations**:
   - Performance is still low (Track 2 and 3 success rates around 1-7%)
   - Part alignment with CAD models is challenging
   - Limited to tabletop manipulation
   - No training, just baseline framework
   - Limited appliance categories (11)
   - Error accumulation in long-horizon tasks

Let me write this out in a well-structured Chinese Markdown format.
</think>
# CheckManual 论文总结

## 1. 核心问题与整体含义

- **研究背景**：随着家用电器（如微波炉、烤箱、洗衣机等）的广泛使用，人们希望机器人能够代替人类完成家电操作任务（如用烤箱烤面包、用微波炉加热食物）。然而与锤子、茶壶等可凭常识使用的简单工具不同，电器各部件的功能由厂商明确定义（如一个旋钮控制温度、另一个控制时间），难以仅凭外观或常识推断。
- **现有研究的两大割裂**：
  - NLP 领域的说明书相关研究（如 TechQA、S10 QA、Smart TV QA、PM209 等）仅停留在文档检索与问答层面，无法支撑机器人操作评估，且不提供对应的 CAD 模型。
  - 机器人操作领域（如 RT-1/2、OpenVLA、VoxPoser、ReKep 等）仅依赖常识进行规划，缺乏阅读多页说明书的能力，难以处理说明书定义的长程复杂任务。
- **核心问题**：如何让机器人"先读说明书，再操作电器"，实现说明书驱动的家电操作。
- **本文意义**：提出首个基于说明书的家电操作基准 CheckManual，填补说明书理解与机器人操作之间的空白，连接语言理解与长程操作决策。

## 2. 方法论

### 2.1 整体思路

构建一个"大模型辅助 + 人工校验"的数据生成流水线，基于电器 CAD 模型自动生成多页说明书 PDF，并配套仿真环境、评测指标与基线模型。

### 2.2 数据生成流水线（5 个阶段）

1. **准备阶段**：
   - 收集 110 份真实电器说明书 PDF（来自中国、欧盟、日本、印度等），分析其格式（点线注释、部件功能说明、任务表达方式）。
   - 采用 PartNet-Mobility 数据集中的 11 类、共 182 个 CAD 模型（微波炉、洗碗机、冰箱、烤箱等）。
2. **电器创建**：
   - 使用 MLLM（GPT-4o）标注每个可动部件的功能名称（如"温度旋钮"），通过正则表达式解析并形成 part ID ↔ 功能名称字典。
   - 根据部件类型采样可用状态（按钮：按压次数；旋钮/杠杆：每 60° 旋转；门/盖/容器：开/关），并由 LLM 为每个状态赋予具体功能含义。
   - 人工校验超过 2200 个部件功能标注。
3. **操作任务创建**：
   - LLM 基于部件功能与状态，依次提出短程与长程操作任务，每个任务步骤以"部件名 + 操作状态"的可解析格式给出。
   - 人工校验超过 1400 个操作任务。
4. **说明书图像设计**：
   - 封面：选择可动部件可见面积最大的视角渲染 RGB 图，再通过 SDXL-Lightning 添加与电器类别匹配的室内背景。
   - 总览图与控制面板：使用 DBSCAN 聚类按钮/旋钮，对总览图做点线注释，并提供 RGB 风格与线稿风格（通过法线图边缘检测）。
   - 部件操作指导：根据部件类型采用四种真实说明书常见表达（纯文字、部件特写、运动分解图、接触点轨迹），需要人工标注每个部件的 3D 接触点。
   - 人工校验超过 1800 张图像。
5. **LaTeX 说明书生成**：
   - 预定义常用 LaTeX 宏包与图标库，随机采样封面、图表、文本风格。
   - LLM 以"前一段正确代码 + 文本功能标注 + 任务列表 + 图像路径"为提示，逐段生成 LaTeX 源码。
   - 采取"段级粒度编译"机制，编译失败则重新生成。

### 2.3 基准与评测任务

- **数据集规模**：1107 份说明书 / 369 个电器 / 11 个类别 / 12 种部件类型 / 2211 个可动部件 / 1464 个操作任务（最长 18 步）。
- **三条挑战赛道**：
  - Track 1：Manual-CAD-Appliance Aligned Planning（CAD 模型可用且部件 ID 与观测对齐，仅做规划）。
  - Track 2：Manual & CAD based Manipulation（CAD 模型可用但需自行做 6-DoF 位姿估计与部件对齐）。
  - Track 3：Pure Manual-based Manipulation（仅说明书，无 CAD 辅助）。
- **评测指标**：
  - 步骤级：部件对齐成功率、规划成功率、任务执行成功率、任务完成率（成功步数 / 总步数）。
  - 任务级：所有步骤按正确顺序完成则视为任务成功。
  - 关节状态误差阈值：旋转关节 ±30°；平移关节需移动 ≥25% 行程，且末端与本体的同向位移比 > 50%。

### 2.4 基线模型 ManualPlan

包含三个模块：

1. **说明书解析模块**：将说明书 PDF 拆分为页面图像，用 PaddleOCR 提取文本，用 MLLM 检测图像/表格，得到每页的图文信息。
2. **操作规划模块**：调用 LLM 按字典格式生成步骤级操作计划（部件名 + 状态），仅允许使用说明书中出现的部件。
3. **部件对齐模块**：使用 Grounding-DINO 检测 + SAM 分割生成可动部件掩膜，并叠加彩色透明掩膜与数字 ID（Set-of-Mark 提示），再由 MLLM 将掩膜 ID 映射到说明书部件名。

### 2.5 低层操作策略

- **CAD 辅助操作（Track 2）**：通过 FoundationPose 估计 6-DoF 位姿，将观测与 CAD 模型对齐后获得关节轴信息；为不同部件类型设计 CAD 辅助的原子动作（门/滑盖/屏幕用 AnyGrasp 预测抓取位姿，按钮沿法向推压，旋钮沿法向抓取并绕接触点旋转）。
- **无 CAD 操作（Track 3）**：将 ManualPlan 与 VoxPoser 结合，ManualPlan 负责"大脑"层面的规划与部件对齐，VoxPoser 负责"小脑"层面的开放词汇操作执行。

## 3. 实验设计

- **数据集与场景**：
  - 自建 CheckManual 数据集（含 1107 份 LaTeX 生成的多页 PDF 说明书 + 369 个 CAD 电器 + 1464 个操作任务）。
  - 仿真环境使用 SAPIEN；末端执行器为 Franka Panda flying gripper。
  - 真实机器人采用 Franka Panda + RealSense D415（眼在手上），按 Track 3 定义进行部署。
- **基准对比方法**：
  - Track 1：ManualPlan（与"w/o manual"消融对比）。
  - Track 2：ManualPlan + Primitive Actions（与"w/o manual"消融对比）。
  - Track 3：ManualPlan + VoxPoser（与"w/o manual"消融对比）。
- **关键模块**：使用 GPT-4o 作为大语言/多模态大模型，Grounding-DINO、Segment Anything、FoundationPose、PaddleOCR、SDXL-Lightning 等作为工具链。
- **评测粒度**：对 11 个电器类别分别报告指标，统计平均结果（表 2）。

## 4. 资源与算力

- 论文**未明确说明**训练所用的 GPU 型号、数量、训练时长等算力细节。
- 推理过程主要依赖 GPT-4o 商用 API，以及 Grounding-DINO、SAM、FoundationPose、VoxPoser、SDXL-Lightning、PaddleOCR 等开源模型的预训练权重，未报告额外训练。
- 真机实验仅使用单台 Franka Panda + RealSense D415，未说明机器人数量与控制计算资源。

## 5. 实验数量与充分性

- **实验规模**：3 条赛道 × 11 个电器类别 ≈ 33 个细分指标，再加"w/o manual"消融，共计约 66 组数据点。
- **消融实验**：对每条赛道均与"w/o manual"做对比，验证说明书的必要性。
- **真机验证**：按 Track 3 的任务定义进行了真实机器人部署，并对长程任务中"成功执行的步骤进行缓存"以缓解误差累积（借鉴 ReKep 思路）。
- **充分性评价**：
  - 优点：覆盖了从规划到执行的完整链条，且同时给出仿真与真机结果，并做了必要的消融。
  - 不足：(1) 每个电器类别的样本量、任务数量、统计置信区间未给出；(2) 缺少与其他说明书理解或操作大模型（如 RT-2、ManipLLM、CoPa、ReKep）的直接对比；(3) 真机实验描述较简短，缺乏定量结果与失败案例分析；(4) Track 1 之后未对各模块（如 OCR、SoM 对齐）做更细粒度消融。

## 6. 主要结论与发现

- **规划能力**：ManualPlan 在 Track 1 上能基于多页说明书生成部分正确的任务计划，但即便是当前最强的 MLLM，也难以将说明书中的部件标注与 CAD 模型对齐，成为规划性能的主要瓶颈。
- **操作能力**：在 Track 2/3 上整体表现仍较低（任务成功率多为 1%~7%），长程操作中部件识别、规划与多步执行错误的累积是失败主因。
- **说明书作用**：所有赛道在去掉说明书输入后性能均显著下降（如 Track 1 总规划成功率从 20.70% 降到 7.99%；Track 3 总成功率从 2.87% 降到 0.55%），验证了说明书在规划与执行中的关键作用。
- **赛道对比**：Track 3（无 CAD）整体略优于 Track 2（需自对齐 CAD 与观测），说明 CAD 模型带来的额外位姿与对齐挑战反而放大了误差传播。
- **真机可行性**：通过步骤级缓存策略，可以在真实 Franka Panda 上完成 Track 3 任务，验证了框架的实际部署潜力。

## 7. 优点

- **首创性**：首个端到端、可量化的"说明书驱动家电操作"基准，跨越了 NLP 说明书理解与机器人操作之间的鸿沟。
- **数据质量保障**：提出"大模型预标注 + 人工校验"的多阶段流水线（覆盖部件名、部件状态、任务步骤、图像四个环节），总计人工校验 2200+ 部件、1400+ 任务、1800+ 图像，有效控制噪声。
- **多粒度挑战设计**：3 条赛道由易到难，依次考察规划、CAD 辅助操作、纯说明书操作，覆盖真实应用的不同信息可用性。
- **模态与图文档处理完备**：说明书以 LaTeX 编译生成的真实 PDF 形式给出，并配以 CAD 模型、RGB-D 观测，贴合真实使用场景。
- **基线模型与策略丰富**：ManualPlan 模块化设计清晰，CAD 辅助原子动作与无 CAD 的 VoxPoser 双策略并重，便于后续工作直接对比与扩展。
- **仿真+真机双重验证**：在 SAPIEN 仿真与 Franka Panda 真机上均完成测试，验证了方法的工程可用性。

## 8. 不足与局限

- **性能整体偏低**：Track 2/3 任务成功率仅在 1%~7% 区间，远未达到实用水平，方法本身仍处于"基线水平"而非"解决方案"。
- **部件对齐瓶颈明显**：Track 1 中部件对齐成功率（22.96%）显著低于规划成功率，且限制了后续任务执行；说明 Set-of-Mark + GPT-4o 的视觉对齐能力在多页说明书、复杂部件场景下仍不稳定。
- **真机实验描述薄弱**：仅给出"按 Track 3 定义部署 + 步骤级缓存"的概要，缺少具体任务数、成功率、失败原因、视频示例等定量分析。
- **缺乏与前沿方法对比**：未与 RT-2、OpenVLA、ManipLLM、ReKep、CoPa 等代表性方法在同一基准上直接比较，难以判断其相对优势。
- **类别与场景受限**：仅覆盖 11 类常见家电，且仅支持桌面级、单臂 Franka Panda 飞行夹爪操作，尚未覆盖双臂、移动操作、嵌入式电器等更复杂场景。
- **数据生成偏置**：所有说明书均由 LaTeX 自动生成，可能与真实厂商说明书在排版、语言风格、图标语义上存在差异；大模型生成的功能命名/任务也可能继承 LLM 本身的偏好与错误（论文已通过人工校验缓解，但风险仍存在）。
- **长程误差累积**：当前 Track 2/3 的低成功率主要来自长程执行中的误差累积，但论文未提出具体的"重规划"或"视觉伺服"等缓解机制，仅在真机上做了步骤级缓存。
- **算力与可复现性不明**：未披露任何训练/推理算力、推理时延或成本，难以评估其在资源受限平台上的实际部署难度。

（完）
