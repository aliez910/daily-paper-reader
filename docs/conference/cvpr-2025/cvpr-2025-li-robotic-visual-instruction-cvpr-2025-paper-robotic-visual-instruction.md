---
title: Robotic Visual Instruction
title_zh: 机器人视觉指令：以符号化草图引导三维操作
authors: "Li, Yanbang, Gong, Ziyang, Li, Haoyang, Huang, Xiaoqi, Kang, Haolan, Bai, Guangping, Ma, Xianzheng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_Robotic_Visual_Instruction_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 可视化草图作为机器人操作策略的输入
tldr: 自然语言作为人-机交互媒介存在空间精度不足、表达冗长模糊等问题。本文提出机器人视觉指令 RoVI，以箭头、圆圈、颜色与数字等手绘符号表征空间-时序信息，并构建 VIEW 流程使策略能够基于 RoVI 生成精确的三维操作动作。在多种操作任务上的实验表明，该方法在空间精度与无歧义性方面显著优于纯语言指令。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1788, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1784, \"height\": 328, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1777, \"height\": 671, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 859, \"height\": 677, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 398, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1799, \"height\": 267, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 875, \"height\": 266, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 864, \"height\": 296, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 876, \"height\": 265, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 863, \"height\": 379, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1803, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1806, \"height\": 382, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 266, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-robotic-visual-instruction-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 329, \"label\": \"Table\"}]"
motivation: 自然语言缺乏空间精度，难以高效、精准地指导机器人在三维空间中的操作。
method: 提出 RoVI 视觉指令范式与 VIEW 流程，使策略能基于手绘符号草图生成精确的 3D 操作动作。
result: 在多种操作任务上较纯语言指令实现了更高的空间精度与更低歧义性。
conclusion: 符号化视觉指令可作为语言之外的精准人-机交互媒介，有效提升机器人操作性能。
---

## Abstract
Recently, natural language has been the primary medium for human-robot interaction. However, its inherent lack of spatial precision for robotic control introduces challenges such as ambiguity and verbosity. To address these limitations, we introduce the ***Robotic Visual Instruction (RoVI)***, a novel paradigm to guide robotic tasks through an object-centric, hand-drawn symbolic representation. RoVI effectively encodes spatial-temporal information into human-interpretable visual instructions through 2D sketches, utilizing arrows, circles, colors, and numbers to direct 3D robotic manipulation. To enable robots to understand RoVI better and generate precise actions based on RoVI, we present ***Visual Instruction Embodied Workflow (VIEW)***, a pipeline formulated for RoVI-conditioned policies. This approach leverages Vision-Language Models (VLMs) to interpret RoVI inputs, decode spatial and temporal constraints from 2D pixel space via keypoint extraction, and then transform them into executable 3D action sequences. We additionally curate a specialized dataset of 15K instances to fine-tune small VLMs for edge deployment, enabling them to effectively learn RoVI capabilities. Our approach is rigorously validated across 11 novel tasks in both real and simulated environments, demonstrating significant generalization capability. Notably, VIEW achieves an 87.5% success rate in real-world scenarios involving unseen tasks that feature multi-step actions, with disturbances, and trajectory-following requirements. Code and Datasets in this paper will be released soon.

---

## 论文详细总结（自动生成）

<think>The user wants me to provide a detailed structured summary of the paper "Robotic Visual Instruction" (RoVI) in Chinese, following 8 specific points. Let me analyze the paper carefully and produce a comprehensive summary.

Key information from the paper:
1. Title: Robotic Visual Instruction (RoVI)
2. Authors: Yanbang Li et al.
3. Conference: CVPR 2025
4. Main contribution: A new HRI paradigm using hand-drawn sketches (arrows, circles, colors, numbers) instead of natural language
5. Pipeline: VIEW (Visual Instruction Embodied Workflow) - uses VLMs to interpret RoVI and generate action sequences
6. Dataset: RoVI Book - 15K instances for fine-tuning small VLMs
7. Experiments: 11 novel tasks (8 real-world, 3 simulated)
8. Success rate: 87.5% in real-world with multi-step, disturbances, trajectory-following

Let me organize the response according to the 8 requested points with Chinese Markdown formatting.</think>

# 论文总结：Robotic Visual Instruction (RoVI)

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：自然语言作为人-机交互（HRI）的主流媒介，在机器人控制中存在先天缺陷：
  - 难以精确描述空间细节（位置、方向、距离）；
  - 易产生歧义与冗长表达（尤其是涉及空间对齐时）；
  - 在图书馆、医院等公共场所不宜采用口头交互。
- **现有视觉方案的不足**：
  - **目标图像（Goal Image）**：要求用户预先提供任务完成后的末端状态与场景，违背用户操作直觉；
  - **轨迹图像（Trajectory Image）**：要求用户绘制完整的末端运动路径，可读性与可用性较差。
- **本文主张**：提出一种新型交互范式 **RoVI（Robotic Visual Instruction）**，以**手绘二维符号（箭头、圆圈、颜色、数字）**为载体，将"时序 3D 坐标序列"压缩为"人类可理解的二维视觉语言"，在**用户友好性、可解释性、时空对齐性**三方面取得更优平衡。

---

## 2. 方法论：核心思想、关键技术细节与流程

### 2.1 RoVI 符号设计
- **基本元素**：
  - **箭头（Arrow）**：表示"从 A 到 B 的移动"，由尾点 $p_0$、路径点 $\{p_1,\dots,p_{n-1}\}$、端点 $p_n$ 组成；
  - **圆圈（Circle）**：表示**功能中心（affordance center）**，用于抓取点、旋转支点、按压点等；
  - **颜色/数字**：区分多步骤任务的时序顺序（绿、蓝、粉等）。
- **三种对象级动作**：
  1. 移动（移动 A→B，由箭头表示）；
  2. 旋转（圆圈+箭头表示旋转方向与角度）；
  3. 拾取/选择（仅圆圈）。
- **绘制风格**：支持"松散手绘"与"几何规整"两种风格，后者对 VLM 解析更友好（见消融）。

### 2.2 VIEW 流水线（Visual Instruction Embodied Workflow）
整体包含三大组件：

- **VLM $f_\theta$**：接收手绘 RoVI 草图 $v\in\mathbb{R}^{H\times W\times 3}$、初始观测图像 $X$ 与默认提示，输出：
  - 自然语言响应 $y_{\text{language}}$：包含任务预测与子目标序列；
  - 可执行代码函数 $y_{\text{code}}$（如 `move()`、`grasp()`）。
- **关键点模块 $f_\delta$（基于 YOLOv8 训练）**：直接检测 RoVI 符号部件（箭头、圆圈），输出 2D 像素空间的关键点序列 $\{p_0, p_i, p_n\}$。
- **关键点驱动的低层策略 $\pi$**：
  - 将 2D 像素关键点通过 RGB-D 相机映射为 3D 坐标 $p'_i\in\mathbb{R}^3$；
  - 结合 AnyGrasp 抓取模块得到初始位姿 $e_0$，构造 SE(3) 位姿序列 $\{e_1,\dots,e_N\}$；
  - 每个时间步 $t$ 最小化代价函数：

$$
L_i(t)=\alpha_i\,\delta_{\text{trans}}(t)+(1-\alpha_i)\,\delta_{\text{rot}}(t)
$$

  - 平动代价 $\delta_{\text{trans}}(t)=\|e_t-e_i\|$；
  - 旋转代价 $\delta_{\text{rot}}(t)=|\theta_t-\theta_i|$，其中 $\theta_i$ 由相邻向量 $v_i=p'_i-c$ 与 $v_{i+1}=p'_{i+1}-c$ 反余弦计算得到；
  - $\alpha_i=1$ 表示平动，$\alpha_i=0$ 表示旋转。

### 2.3 RoVI Book 数据集
- **规模**：15K 图像-文本问答对；
- **来源**：基于 Open X-Embodiment 数据集；
- **任务构成**：64% 单步 + 36% 多步任务；涵盖 5 类基础操作（移动、旋转、拾取、开抽屉/柜、关抽屉/柜）；
- **数据增强**：每任务生成 3–8 种视觉变体（路径、风格、线宽）；
- **标注**：先由 GPT-4o 生成答案，再经人工语义过滤；
- **训练方式**：使用 LoRA 对 LLaVA-7B/13B 进行参数高效微调（PEFT）。

---

## 3. 实验设计：数据集、场景、对比方法

### 3.1 真实环境实验
- **机械臂**：UFACTORY X-Arm 6 与 UR5（双指夹爪）；
- **相机**：两台 RealSense D435（俯视 + 第三方视角）；
- **控制频率**：20 Hz，delta 末端控制模式；
- **任务数**：8 个真实未见任务（含轨迹跟随、杂乱干扰、多步操作）；
- **基线方法**：
  - VoxPoser（基于 GPT-4o 的语言条件策略）；
  - CoPa（语言 + Set-of-Mark 视觉提示，基于 GPT-4o）；
  - RT-1-X、Octo-language、Octo-goal-image（端到端 VLA 模型）。
- **评估指标**：
  - 动作成功率（10 次试验）；
  - 时空对齐度（6 分 Likert 量表）。

### 3.2 仿真环境实验
- **仿真器**：SAPIEN + SIMPLER；
- **任务数**：3 个新任务（杂乱场景）；
- **对比**：RT-1-X、Octo（语言 & 目标图像两种条件）。

### 3.3 VLM 理解能力评估
- **测试模型**：GPT-4o、Gemini-1.5 Pro、Claude 3.5-Sonnet、InternLM-XComposer2-VL-7B、LLaVA-v1.6-Mistral-7B、MiniGPT-4、VIP-LLaVA-7B 以及微调后的 LLaVA-13B (RoVI Book)；
- **评估内容**："Task"（任务理解）与"Planning"（子目标分解）准确率。

### 3.4 消融实验
- **绘制风格**：松散 vs. 几何规整；
- **关键点模块**：YOLOv8 vs. Grounding DINO、OWL-ViT、OWL-V2；
- **指标**：像素欧氏距离误差（MD）与 mAP@50px。

---

## 4. 资源与算力

- **明确说明的算力**：实验全部在 **单块 NVIDIA A40 GPU** 上进行；
- **训练配置**：LoRA 微调 LLaVA-7B/13B，1 个 epoch，学习率 $2\times10^{-4}$；
- **关键点模块**：YOLOv8 在自构 2K 图像数据集上训练；
- **未明确说明的内容**：总训练时长、数据生成耗时、推理延迟、模型参数量细节等。

---

## 5. 实验数量与充分性

- **实验总量**：
  - 8 个真实任务 + 3 个仿真任务（11 个未见任务）；
  - 7 大类 VLM 在 11 任务上的理解能力对比；
  - 4 类目标检测模型在 4 任务上的关键点提取对比；
  - 2 种绘制风格的消融；
  - 多种误差来源的分解分析。
- **充分性评价**：
  - **优点**：实验维度涵盖真实/仿真、不同 VLM、不同绘制风格、不同检测模块，且所有任务均为**未见任务**与**未见环境**，对泛化性验证较为严格；
  - **不足**：每个任务仅 10 次试验，统计显著性较弱；缺少用户研究（user study）评估"易用性"与"可解释性"的主观指标；基线覆盖主要语言条件方法，但缺乏与最新轨迹图像方法（如 RT-Trajectory）的直接对比。

---

## 6. 主要结论与发现

- **核心性能**：VIEW 在真实未见任务上取得 **87.5% 成功率**（含多步、干扰、轨迹跟随），显著优于 VoxPoser（43.8%）与 CoPa（45%）；
- **VLM 理解能力**：GPT-4o 综合最优（任务/规划准确率 81%/97%），但随步骤数增加而下降；经 RoVI Book 微调的 LLaVA-13B 在**长序列任务上反超大模型**；
- **时空对齐**：RoVI 是唯一同时具备路径精确性与末端一致性的指令形式；
- **关键点模块优势**：YOLOv8 相比开放词汇检测器（Grounding DINO/OWL-ViT/OWL-V2）具有更稳定的 mAP（接近 1.0）与更小的距离误差；
- **绘制风格**：结构化的几何风格显著优于松散手绘风格。

---

## 7. 优点（方法与实验设计的亮点）

- **范式创新**：首次系统提出"手绘符号 → 3D 操作"的完整范式，明确区分 RoVI 与目标图像、轨迹图像的差异；
- **流程完整**：包含符号设计、数据集构建、VLM 解析、关键点提取、低层控制全链路；
- **时序解耦**：用颜色/数字编码步骤，将复杂多步任务自然分解为单步子任务，降低 VLM 时序推理负担；
- **误差鲁棒性**：关键点模块仅检测 RoVI 符号部件而非环境对象，避免开放词汇检测受干扰物影响；
- **数据与模型双驱动**：提供 15K 数据集 + 微调方案，使小模型也具备 RoVI 能力，利于边缘部署；
- **定性分析**：通过 50 次试验轨迹采样对比，直观展示 RoVI 在路径收敛性上的优势。

---

## 8. 不足与局限

- **任务覆盖有限**：仅 11 个任务，且集中在桌面级 pick-and-place 类操作，缺少长距离导航、移动操作（mobile manipulation）、柔性物体操作等场景；
- **绘制方式受限**：依赖平板/PC 绘图软件，未验证真实纸质草图或非受控手绘的鲁棒性；
- **颜色依赖性强**：多步任务时序完全依赖颜色/数字区分，对色盲用户或灰度图像不友好；
- **缺乏用户研究**：未评估普通用户的可绘制性、学习成本与主观偏好；
- **算力与时长未披露**：训练时长、推理延迟、显存占用等关键工程指标缺失；
- **泛化边界未明**：关键点模块仅在 2K 图像上训练，复杂背景、密集符号场景下的泛化性未充分验证；
- **与最新方法对比有限**：未与 RT-Trajectory、3D-VLA、Socratic Models 等轨迹或多模态方法直接对比；
- **潜在偏差**：所有 RoVI 数据均来自 GPT-4o 生成 + 人工过滤，可能引入模型偏好偏差；试验次数较少（每任务 10 次），统计显著性有限。

（完）
