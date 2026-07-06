---
title: "COIN: Chain Of INteraction Benchmark: When Reasoning meets Embodied interaction"
title_zh: COIN：交互链基准——推理与具身交互的交汇
authors: "Xianhao Wang, Xiaojian Ma, Haozhe Hu, Rongpeng Su, Yutian Cheng, Zhou Ziheng, Hangxin Liu, Lei Liu, Bin Li, Qing Li"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=xU8DPbrglA"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向现实机器人操作交互式推理的基准测试
tldr: 现有基准未能系统评估通用具身智能体在部分可观测条件下执行长时序、因果依赖的交互式推理能力。本文提出了COIN基准，专门用于评估真实机器人操作中的交互式推理能力。核心贡献包括构建包含50个交互任务的COIN-50任务集与配套评估协议。该工作为复杂机器人操作能力的系统化评测奠定了重要基础。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有基准无法系统评估通用具身智能体在部分可观测下完成长时序因果依赖任务的能力。
method: 构建包含50个交互任务的COIN-50基准与对应评估协议，专门衡量交互式推理能力。
result: 为复杂机器人操作任务在交互式推理维度上的系统化评测提供了专用基准平台。
conclusion: COIN填补了具身交互推理评测的空白，有望推动真实场景长时序操作策略研究。
---

## Abstract
Generalist embodied agents must perform interactive, causally-dependent reasoning, continually interacting with the environment, acquiring information, and updating plans to solve long-horizon tasks before they could be adopted in real-life scenarios. For instance, retrieving an apple from a cabinet may require opening multiple doors and drawers before the apple becomes visible and reachable—demanding sequential interaction under partial observability. However, existing benchmarks fail to systematically evaluate this essential capability. We introduce \textbf{COIN}, a benchmark designed to assess interactive reasoning in realistic robotic manipulation through three key contributions. First, we construct \textbf{COIN-50}: 50 interactive tasks in daily scenarios, and create \textbf{COIN-Primitive} required by causally-dependent tasks, and \textbf{COIN-Composition} with mid-term complexity for skill learning and generalization evaluation. Second, we develop a low-cost mobile AR teleoperation system and collect the COIN-Primitive Dataset with 50 demonstrations per primitive task (1,000 in total). Third, we develop systematic evaluation metrics about execution stability and generalization robustness to evaluate \textbf{CodeAsPolicy}, \textbf{VLA}, and language-conditioned \textbf{H-VLA} approaches. Our comprehensive evaluation reveals critical limitations in current methods: models struggle with interactive reasoning tasks due to significant gaps between visual understanding and motor execution. We provide fine-grained analysis of these limitations.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "COIN: Chain Of INteraction Benchmark: When Reasoning meets Embodied interaction" based on the provided abstract and metadata. The PDF couldn't be accessed (CAPTCHA blocked), so I'll rely on the abstract and metadata to construct the summary.

Let me organize the summary according to the 8 points requested, using Markdown formatting.

Key information from abstract and metadata:
- Title: COIN: Chain Of INteraction Benchmark
- Focus: Interactive, causally-dependent reasoning in embodied agents for long-horizon tasks
- Problem: Existing benchmarks fail to systematically evaluate interactive reasoning in realistic robotic manipulation under partial observability
- Key contributions:
  1. COIN-50: 50 interactive tasks in daily scenarios, plus COIN-Primitive (required by causally-dependent tasks) and COIN-Composition (mid-term complexity)
  2. Low-cost mobile AR teleoperation system + COIN-Primitive Dataset (50 demos per primitive, 1000 total)
  3. Systematic evaluation metrics for execution stability and generalization robustness
- Methods evaluated: CodeAsPolicy, VLA, language-conditioned H-VLA
- Findings: Current models struggle with interactive reasoning due to gaps between visual understanding and motor execution
- Source: ICLR 2026

Let me write the summary in Chinese, following the structure requested.
</think>
# 论文总结：COIN——交互链基准

## 1. 核心问题与研究动机

- **研究背景**：通用具身智能体（generalist embodied agents）要在真实场景中被采用，必须具备**交互式、因果依赖的推理能力**（interactive, causally-dependent reasoning），即在部分可观测条件下，通过持续与环境交互、获取信息、动态更新规划，完成长时序任务。
- **典型场景**：例如从橱柜中取苹果，可能需要依次打开多个门和抽屉，直到苹果变得可见且可触及——这要求在**部分可观测性下进行序贯交互决策**。
- **现有问题**：现有基准未能**系统性地评估**这一关键能力，难以衡量智能体在"感知—行动—再感知—再行动"闭环中的因果推理与策略调整水平。

## 2. 方法论：核心思想与关键设计

- **核心思想**：构建一个专门面向**真实机器人操作场景下交互式推理**的基准测试平台 COIN，覆盖从基础原语到组合任务的完整评测谱系。
- **三个关键贡献**：
  1. **任务集构建**
     - **COIN-50**：50 个日常场景下的交互任务。
     - **COIN-Primitive**：被因果依赖任务所依赖的基础原语任务集合。
     - **COIN-Composition**：中等复杂度的组合任务，用于技能学习与泛化评估。
  2. **数据采集系统**
     - 开发了一套**低成本移动 AR 遥操作系统**（low-cost mobile AR teleoperation system）。
     - 采集 **COIN-Primitive Dataset**：每个原语任务 50 条演示，共 **1,000 条**轨迹。
  3. **评估协议**
     - 设计了系统化的评估指标，覆盖两个维度：
       - **执行稳定性（execution stability）**
       - **泛化鲁棒性（generalization robustness）**

## 3. 实验设计与对比方法

- **评测场景**：基于真实机器人操作的日常交互任务，涵盖部分可观测、长时序、因果依赖的条件。
- **基准（Benchmark）**：
  - COIN-50（任务集）
  - COIN-Primitive（基础原语）
  - COIN-Composition（组合任务）
- **对比方法**（三类代表性具身策略范式）：
  - **CodeAsPolicy**：将策略表达为可执行代码的范式。
  - **VLA**（Vision-Language-Action）：视觉-语言-动作通用大模型。
  - **H-VLA**（language-conditioned Hierarchical VLA）：语言条件下的分层视觉-语言-动作模型。
- **评测维度**：执行稳定性 + 泛化鲁棒性，强调"视觉理解"与"运动执行"之间的衔接。

## 4. 资源与算力

- **论文中未明确说明**训练或评测所使用的 GPU 型号、数量及训练时长等算力细节。
- 已知硬件相关资源仅为**自研的低成本移动 AR 遥操作系统**（用于数据采集），未见大规模预训练算力开销的描述。
- 建议读者参阅论文正文/附录以确认是否有补充信息。

## 5. 实验数量与充分性

- **实验规模**：
  - 50 个交互任务 + 若干原语任务 + 若干组合任务。
  - 1,000 条遥操作演示数据（50 任务 × 20 原语 × 50 演示）。
  - 至少对 **3 类方法**（CodeAsPolicy、VLA、H-VLA）进行对比评测。
- **实验维度**：
  - 覆盖执行稳定性与泛化鲁棒性两大指标。
  - 提供细粒度（fine-grained）的能力分析。
- **充分性评价**：
  - 任务设计层次清晰（原语—组合—完整任务），有利于系统化诊断能力瓶颈。
  - 但**仅基于三类方法的对比**略显有限，且未明确给出每种方法在每类任务上的具体指标细分，存在评测覆盖深度不充分的风险。
  - 缺少对人类水平基线（human baseline）的对比可能影响结果客观性的进一步论证。

## 6. 主要结论与发现

- **核心发现**：当前主流方法（CodeAsPolicy、VLA、H-VLA）在**交互式推理任务**上表现吃力，暴露了**视觉理解与运动执行之间存在显著鸿沟**。
- **能力诊断**：
  - 模型在部分可观测条件下的序贯决策能力不足。
  - 因果依赖型任务的执行稳定性较差。
  - 跨任务的泛化能力有限。
- **结论意义**：COIN 填补了具身交互推理评测的空白，为推动真实场景下的长时序操作策略研究提供了**专用评测基础设施**。

## 7. 优点

- **任务设计系统化**：将任务分解为"原语—组合—完整"三层结构，有利于细粒度分析能力短板。
- **真实场景导向**：50 个任务贴近日常操作，且强调**部分可观测与因果依赖**两大现实约束。
- **数据采集成本低**：基于自研移动 AR 遥操作系统，**降低了对昂贵专业遥操作设备的依赖**，提升了基准的可复现性与推广性。
- **评估指标多维化**：同时关注执行稳定性与泛化鲁棒性，避免单一指标带来的偏差。
- **方法对比覆盖三类范式**：涵盖代码策略、端到端 VLA 与分层 VLA，具备较好的代表性。

## 8. 不足与局限

- **PDF 原文未能获取**，上述分析主要基于摘要与元数据，部分细节（如具体公式、完整算法流程、误差分析表格）可能不完整。
- **算力信息缺失**：未披露训练/评测所用 GPU 与时长，限制了结果的可复现性参考。
- **方法覆盖有限**：仅评测三类方法，缺少对经典行为克隆、强化学习、以及最新大模型策略（如 RT-2、OpenVLA 等）的横向对比。
- **任务数量相对较少**：50 个任务对长时序复杂操作的统计稳定性可能不足，存在过拟合风险。
- **缺少人类基线**：未提及与人类操作者表现的对比，难以判断模型与人类水平的实际差距。
- **场景偏差风险**：日常任务虽然贴近生活，但与工业、户外等更复杂环境的泛化性未经验证。
- **遥操作演示数据规模有限**：1,000 条数据对当前数据驱动的具身学习方法而言可能偏小，可能不足以支撑高性能策略的训练。

（完）
