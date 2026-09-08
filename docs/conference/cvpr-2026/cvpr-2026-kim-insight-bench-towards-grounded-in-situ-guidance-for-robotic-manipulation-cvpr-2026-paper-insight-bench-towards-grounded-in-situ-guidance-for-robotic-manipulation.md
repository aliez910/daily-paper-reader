---
title: "INSIGHT Bench: Towards Grounded IN-SItu Guidance for Robotic ManipulaTion"
title_zh: INSIGHT Bench：面向机器人操纵的原位引导基准
authors: "Kim, Seonho, Hong, Junhyeong, Lee, Kyungjae, Oh, Yoonseon"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Kim_INSIGHT_Bench_Towards_Grounded_IN-SItu_Guidance_for_Robotic_ManipulaTion_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操纵VLA模型的原位引导基准
tldr: 本文针对VLA模型无法利用物体上书写或刻画的原位操作引导信息这一问题，提出INSIGHT Bench基准。该基准建立了原位引导理解的任务形式化与分类体系，并提供可扩展仿真评估框架。该工作填补了机器人操纵中VLA模型利用物体原位信息能力评估的空白，推动了复杂操纵基准的发展。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 994, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 824, \"height\": 204, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 852, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1728, \"height\": 925, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 647, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1804, \"height\": 370, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 827, \"height\": 208, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-kim-insight-bench-towards-grounded-in-situ-guidance-for-robotic-manipulation-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 856, \"height\": 361, \"label\": \"Table\"}]"
motivation: VLA模型无法理解物体上的原位引导信息，且缺乏标准化评测基准。
method: 构建INSIGHT Bench基准，含动作方向线索与过程性指令的分类体系及仿真框架。
result: 为评估VLA模型原位引导理解能力提供了系统化、可扩展的评测平台。
conclusion: 推动复杂机器人操纵任务中模仿学习的标准化基准研究。
---

## Abstract
Humans intuitively rely on text and symbols inscribed on objects (e.g. "PULL", "Squeeze and Turn") to perform tasks safely and correctly. In contrast, vision-language-action models excel at following external language commands, but remain largely unaware of this object-centric information. This capability is essential for reliable robotic operation, yet progress remains unmeasured due to the absence of standardized benchmarks. To address this gap, we introduce INSIGHT Bench, a benchmark that formalizes the task of "in-situ guide grounding". INSIGHT Bench provides a comprehensive taxonomy that evaluates how agents utilize diverse guide information, including action-direction cues and procedural instructions. It also includes a scalable simulation framework that procedurally generates tasks and programmatically links each visual guide to its corresponding physical constraint. We release both the benchmark and the resulting trajectory dataset to support future research. Our evaluation of recent VLA models reveals a critical limitation: their ability to ground in-situ guides is inconsistent and strongly dependent on the type of information. While models succeed on some guide categories, they frequently fail on others. However, performance improves substantially when the same information is provided as language instructions, indicating that in-situ guides could contribute to manipulation performance if VLAs were capable of interpreting them. These findings underscore the need for further research on understanding and grounding in-situ guides.

---

## 论文详细总结（自动生成）

<think>The user is requesting a structured Chinese summary of the INSIGHT Bench paper. Let me analyze the paper content carefully and organize my response according to the 8 required points.

The paper introduces INSIGHT Bench, a benchmark for evaluating VLA (Vision-Language-Action) models' ability to ground "in-situ guides" - text and symbols physically embedded on objects that indicate how they should be manipulated.

Let me structure my response:

1. Core problem: VLA models can't understand in-situ visual guides on objects, lack of benchmarks
2. Methodology: Taxonomy of 5 guide categories, simulation framework, data generation pipeline
3. Experiments: Three tasks (Cabinet, Door, Bottle), comparison with NG-VLA, G-VLA, LI-VLA settings
4. Resources: Not explicitly mentioned in detail
5. Experiment count: 3 tasks × 3 models × 3 settings + real-world validation
6. Findings: VLAs struggle with complex guide types but benefit from language instructions
7. Strengths: Novel taxonomy, scalable generation, comprehensive analysis
8. Limitations: Limited tasks, real-world gap, small-scale real validation

Let me write a detailed Chinese summary.</think>

# INSIGHT Bench 论文总结

## 1. 核心问题与研究动机

**核心问题**：当前视觉-语言-动作（VLA）模型虽然能够很好地遵循外部语言指令执行机器人操作任务，但**无法理解物体上物理嵌入的视觉引导信息**（in-situ guides），例如门上的"PUSH"/"PULL"标识、儿童安全瓶上的"Squeeze and Turn"图标等。这类引导信息在日常生活中无处不在，是人类理解"如何操作物体"的关键线索，但目前**缺乏标准化基准**来衡量 VLA 模型在该能力上的进展。

**研究背景与意义**：
- 现有机器人数据集（DROID、Open X-Embodiment、BridgeData V2 等）规模庞大，但主要关注通过外部语言指令或人类演示进行学习，忽略了**物体本身携带的可操作语义信息**。
- 视觉提示（visual prompting）和目标图像条件化（goal-image conditioning）等先前方法依赖外部提供的视觉线索，而非物体自身嵌入的信息。
- 原位引导（in-situ guides）能够提供与特定物理可供性（affordance）紧耦合的简洁视觉信号，对**程序性约束**（如"先按压再旋转"）的处理从"后验纠错"转变为"主动指令遵循"。

---

## 2. 方法论

### 2.1 任务形式化与分类体系

INSIGHT Bench 形式化了 **"原位引导理解（in-situ guide grounding）"** 任务，提出五类引导信息分类：

| 类别 | 描述 |
|------|------|
| (1) Contact Affordance | 标识可交互部件的接触可供性 |
| (2) In-Part Contact Specification | 部件内部的精确接触位置与方式 |
| (3) Action Directional Information | 施加操作方向约束（如旋转方向） |
| (4) Procedural Guidance | 多步操作的顺序约束 |
| (5) Target Disambiguation | 多个候选部件间的目标区分 |

### 2.2 仿真环境

- 基于 **NVIDIA Isaac Lab**，提供 GPU 并行化物理仿真与照片级渲染。
- **硬件配置**：固定 7-DoF Franka Emika Panda 臂 + 平行夹爪。
- **感知系统**：四个相机（左肩、右肩、腕部 + 一个额外引导感知相机），提供 224 × 224 RGB 图像、深度图、内参及引导的语义分割掩码。
- **资产准备**：从 Isaac Sim 库和已有数据集（PartManip、UniDoorManip、AdaManip）获取物体资产；通过凸分解、关节偏移修正、网格简化提升物理稳定性。
- **引导资产生成**：使用 Google Material Symbols Library 的 12 个符号图标 + Blender 4.5.6 制作的 20 个文本资产，导出为 USD 格式。

### 2.3 任务设计（四个子任务×三类信息维度）

- **Cabinet（目标区分）**：使用 102 个对象资产（2-6 个可目标关节），共 267 个场景；评估 Contact Affordance + Target Disambiguation。
- **Door（程序性引导）**：55 个门资产 × 4 配置（顺/逆时针、推/拉），共 220 个场景；铰链关节被锁定，需先旋转手柄解锁，评估 Affordance + Action Direction + Procedural Guidance。
- **Bottle-Standard（动作方向）**：6 个变体（标准开/关 + 挤压关 × CW/CCW），共 296 个场景中的标准变体。
- **Bottle-Squeeze（精细接触）**：2 个变体（儿童瓶开口 CW/CCW），评估 Affordance + In-Part Contact + Procedural Guidance。

### 2.4 演示数据生成框架（核心创新）

**两阶段场景生成**：
- **Stage 1 — Guide-to-Physics Grounding**：每个 episode 采样高层任务（如 Bottle）和子任务（如"squeeze and open clockwise"），渲染对应视觉引导，并程序化激活相关物理约束（如旋转关节在被夹爪按压前锁定）。
- **Stage 2 — Guide Spatial Randomization**：在语义相关区域（如瓶盖顶面、抽屉前面板）程序化采样引导位置与朝向，避免空间记忆化过拟合。

**轨迹生成**：
- 采用**层级化、基于技能的流水线**：高层任务定义为参数化技能序列（如 GRASP → ROTATE → PULL），低层参数 θ_i 从仿真状态自动实例化。
- 使用 **CuRobo** 运动规划器 + 关节级 PID 控制器执行。
- 数据格式：ζ = {(o_t, a_t, r_t)}_{t=0}^{T}，其中 o_t 包含本体感知状态与视觉输入，a_t ∈ R^8（7-DoF 关节 + 夹爪），r_t 为稀疏终局奖励。
- **技能库**：S = {GRASP(p, q), ROTATE(ϕ), PULL(d)} 三个原语。

**数据规模与格式**：
- 数据以 **10Hz 频率**采集，存储为 **LeRobot** 格式（降低使用门槛）。
- **Guided Dataset**：14,076 条带引导的演示轨迹。
- **Guideless Dataset**：相同任务但无引导资产，作为对照基线。

---

## 3. 实验设计

### 3.1 基准对比方法

评估了三个近期 SOTA VLA 模型：
- **π0**（VLM 骨干：PaliGemma 3B，动作专家：Flow Matching）
- **SmolVLA**（VLM 骨干：SmolVLM-2 0.5B）
- **GR00T N1.5**（VLM 骨干：Eagle-2.5 2.1B）

### 3.2 三种训练/评估条件

| 条件 | 训练数据集 | 评估输入 | 含义 |
|------|---------|---------|------|
| **NG-VLA**（No-Guide） | Guideless Dataset | 无引导 | 基线性能 |
| **G-VLA**（Guided-Visual） | Guided Dataset | 视觉引导 | 评估模型能否从视觉引导中学习 |
| **LI-VLA**（Language-Instructed） | Guided Dataset | 视觉引导 + 语言指令 | 提供外部 VLM（GPT-5）解析的引导语义 |

### 3.3 评估协议

- 每个 (对象, 任务变体) 对评估 8 次 rollout。
- 10 秒时间限制，关节越过校准阈值即视为成功。
- 训练时使用仿真器状态生成的真值指令，评估时使用 GPT-5 从观察生成指令，模拟真实部署场景。

### 3.4 真实世界验证

使用 GR00T 在仿真预训练权重基础上用 LoRA 微调，每变体收集 15 条真实演示，评估 Bottle-Std（CW/CCW）和 Cabinet（左/右），每设置 10 次试验。

---

## 4. 资源与算力

**论文未明确披露**具体的 GPU 型号、数量或训练时长。考虑到：
- 实验涉及三个 VLA 模型的多任务微调、Isaac Lab 的大规模并行仿真数据生成（14,076 条轨迹 + 对照组）以及真实世界验证；
- VLM 骨干从 0.5B（SmolVLM-2）到 3B（PaliGemma）不等；
- 数据生成需大量 GPU 并行物理仿真。

可推断训练/生成涉及多块 GPU 资源，但具体配置（如 A100/H100 数量、训练 epoch 数、wall-clock time）在主论文与可获取的元数据中**均未提供**，属于该论文的一个信息披露缺失。

---

## 5. 实验数量与充分性

**实验数量概览**：
- **3 个模型 × 3 种训练条件（NG/G/LI）× 4 个任务（Cabinet/Door/Bottle-Std/Bottle-Squeeze）= 36 组核心实验配置**。
- 每个配置在所有 (对象, 变体) 对上进行 8 次 rollout。
- **真实世界验证**：2 个任务 × 2 个变体 × 10 次试验。
- 此外还有"无位置随机化的消融数据集"用于隔离接触点检测误差的影响。

**充分性评估**：
- **优点**：覆盖了五个信息维度的不同组合，分类体系清晰，三种训练条件提供了受控对比，能够明确分离感知瓶颈与动作执行瓶颈。
- **不足**：
  - 真实世界验证规模较小（每个设置仅 10 次试验、15 条演示），统计显著性有限。
  - 缺乏对其他 SOTA VLA 模型（如 OpenVLA、Octo）的评估。
  - LI-VLA 借助外部 GPT-5 提供语言指令，可能引入外部模型的偏差，模糊了"模型自身理解力"的评估。
  - 主要在仿真中进行，未充分覆盖 sim-to-real gap 的多样性场景（不同物体材质、光照等）。

整体而言，**实验设计较为系统且公平**（统一训练流程、多任务设置、控制变量），但真实世界规模和模型广度仍有提升空间。

---

## 6. 主要结论与发现

1. **整体性能瓶颈在感知与理解，而非动作执行**：G-VLA 与 NG-VLA 的整体成功率差异极小（π0: 12.1% → 14.1%；GR00T N1.5: 17.2% → 18.5%；SmolVLA 反而下降 10.1% → 7.4%），表明模型未能有效利用视觉引导语义，引导甚至可能成为视觉干扰项。

2. **语言指令显著提升性能**：LI-VLA 整体成功率大幅提升（GR00T: 18.5% → 24.3%；π0: 14.1% → 18.5%），说明当引导信息被翻译为语言后，模型能够执行所需物理动作，**核心瓶颈是视觉语义解码能力**。

3. **任务特异性结论**：
   - **Cabinet（目标区分）**：G-VLA 显著优于 NG-VLA（如 GR00T 性能提升超 3 倍），说明模型能学习简单的空间区分信号。
   - **Bottle-Standard（动作方向）**：G-VLA 与 LI-VLA 均无显著提升，所有模型均难以前后方向旋转。
   - **Door（程序性引导）**：除 GR00T 外，视觉引导反而降低性能；语言指令带来显著提升，主要源于模型对程序性信息的语言理解。
   - **Bottle-Squeeze（精细接触）**：结果因模型而异——π0 的 G-VLA 表现最佳（约 2 倍提升），GR00T 的 LI-VLA 最佳（4 倍提升），SmolVLA 在所有设置下均失败。表明精细物理指令的成功依赖 VLM 骨干的强弱。

5. **真实世界一致性**：Bottle-Std 上 LI-VLA (65%) > G-VLA (45%)；Cabinet 上 G-VLA (50%) ≈ LI-VLA (45%)，验证仿真发现的结论在真实场景中成立。

**核心结论**：当前 VLA 模型在原位引导理解上**能力高度不一致且依赖信息类型**，简单的目标区分可学习，复杂的程序性、方向性、精细接触引导则普遍失败；这一空白亟需专门为原位引导设计的新方法。

---

## 7. 方法与实验设计的亮点

- **首创性**：首个形式化"原位引导理解"任务的基准，填补了 VLA 评估的空白维度。
- **系统化分类体系**：五类引导信息维度清晰且可组合，提供了评估 VLA 推理能力的细粒度切片。
- **Guide-to-Physics 程序化绑定**：将视觉引导与物理约束在仿真中程序化关联，避免了人工数据标注的不可扩展性。
- **空间随机化设计**：解耦语义内容与空间位置，防止模型依赖位置记忆化，提高了评估的稳健性。
- **自动化大规模演示生成**：相比 MimicGen、SkillGen 等方法，无需手动关键点指定或人工验证，且能整合引导语义；Guided + Guideless 双数据集设计提供天然对照实验。
- **LeRobot 格式开放**：降低使用门槛，并附带技能级标签，支持层级化学习研究。
- **三重对照实验设计（NG/G/LI）**：巧妙分离"是否有引导"、"是否能解读引导"、"是否能执行动作"三个独立因素，使结论定位精确。

---

## 8. 不足与局限

- **真实世界验证规模较小**：每个真实场景仅 10 次试验、15 条 LoRA 微调演示，统计可信度有限，未覆盖光照变化、视角变化、物体差异等真实场景因素。
- **引导资产有限**：仅 12 个符号图标 + 20 个文本资产，引导多样性受限，可能无法充分测试模型的鲁棒性。
- **任务范围有限**：仅包含 Cabinet、Door、Bottle 三类日常物体，未覆盖工具使用（如剪刀、扳手）、电器面板、医疗器械等更复杂的引导类型。
- **LI-VLA 依赖外部 VLM**：使用 GPT-5 作为语言指令生成器，可能引入外部模型偏差，且无法评估模型自身对引导的独立理解能力。
- **算力信息披露缺失**：未提供训练时长、GPU 数量、数据生成耗时等关键信息，限制可复现性评估。
- **VLM 骨干规模有限**：实验中最大的 VLM 仅为 3B（PaliGemma），未测试更大规模（如 7B+）VLA 模型的潜在差异。
- **位置随机化消融范围有限**：仅用"无位置随机化"数据集隔离接触点检测误差，未对其他因素（如引导遮挡、视角变化）做更系统的消融。
- **评估仅在仿真与简化真实环境**：仿真器渲染与真实世界存在 sim-to-real gap，论文未深入探讨这一差距对原位引导（其细节可能因渲染差异而丢失）的影响。

（完）
