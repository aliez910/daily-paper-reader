---
title: Restoring Linguistic Grounding in VLA Models via Train-Free Attention Recalibration
title_zh: 通过免训练注意力重校准恢复VLA模型的语言基础
authors: "Ninghao Zhang, Bin Zhu, Shijie Zhou, Jingjing Chen"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/9554.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于LIBERO构建ICBench诊断基准评估VLA操作策略
tldr: 现有VLA模型在分布外指令下可靠性不足，常优先视觉先验而非指令语义，被称为语言盲视。本文从LIBERO构建ICBench诊断基准，系统分析VLA的指令遵循失败模式，并提出无需训练的注意力重校准方法恢复语言基础。该工作对通用机器人VLA策略的鲁棒性研究具有重要价值，揭示了模仿学习在复杂操作任务中的关键短板。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0119ec858a232fa60f59ce70/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1476, \"height\": 813}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0119ec858a232fa60f59ce70/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 1348, \"height\": 618}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0119ec858a232fa60f59ce70/fig-003.webp\", \"caption\": \"\", \"page\": 11, \"index\": 3, \"width\": 901, \"height\": 675}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0119ec858a232fa60f59ce70/fig-004.webp\", \"caption\": \"\", \"page\": 13, \"index\": 4, \"width\": 4448, \"height\": 1084}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0119ec858a232fa60f59ce70/fig-005.webp\", \"caption\": \"\", \"page\": 14, \"index\": 5, \"width\": 1447, \"height\": 707}]"
motivation: 现有VLA策略在分布外指令下出现语言盲视，优先视觉先验而非指令语义。
method: 提出无需训练的注意力重校准方法恢复语言基础，并构建ICBench诊断基准。
result: 系统揭示VLA模型的失败模式并提供即插即用的鲁棒性提升方案。
conclusion: 推动了通用机器人VLA策略的语言基础与鲁棒性研究。
---

## Abstract
Vision-Language-Action (VLA) models enable robots to per-form manipulation tasks directly from natural language instructions andare increasingly viewed as a foundation for generalist robotic policies.However, their reliability under Out-Of-Distribution (OOD) instructionsremains underexplored. In this paper, we reveal a critical failure modein which VLA policies continue executing visually plausible actions evenwhen the language instruction contradicts the scene. We refer to this phe-nomenon as linguistic blindness, where VLA policies prioritize visualpriors over instruction semantics during action generation. To systemati-cally analyze this issue, we introduce ICBench, a diagnostic benchmarkconstructed from the LIBERO dataset that probes language–action cou-pling by injecting controlled OOD instruction contradictions while keep-ing the visual environment unchanged. Evaluations on three represen-tative VLA architectures, including π0 , π0.5 , and OpenVLA-OFT, showthat these models frequently succeed at tasks despite logically impossi-ble instructions, revealing a strong visual bias in action generation. Tomitigate this issue, we propose Instruction-Guided Attention Re-calibration (IGAR), a train-free inference-time mechanism that rebal-ances attention distributions to restore the influence of language instruc-tions. IGAR operates without retraining or architectural modificationand can be directly applied to existing VLA models. Experiments across30 LIBERO tasks demonstrate that IGAR substantially reduces erro-neous execution under OOD contradictory instructions while preservingbaseline task performance. We additionally validate the approach on areal Franka robotic arm, where IGAR effectively prevents manipulationtriggered by inconsistent instructions.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper following a specific structure with 8 points. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is "Restoring Linguistic Grounding in VLA Models via Train-Free Attention Recalibration" - published at ECCV 2026.

Key points to cover:
1. Core problem: Linguistic blindness in VLA models - they prioritize visual priors over instruction semantics
2. Method: ICBench benchmark + IGAR (Instruction-Guided Attention Recalibration) - train-free inference-time intervention
3. Experiments: LIBERO benchmark (30 tasks across Spatial, Object, Goal suites), compared π0, π0.5, OpenVLA-OFT
4. Resources: NVIDIA RTX 5090, latency overhead mentioned
5. Experiment count and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me write a comprehensive summary in Chinese following the structure requested.</think>

# 论文总结：通过免训练注意力重校准恢复 VLA 模型的语言基础

## 1. 核心问题与研究动机

- **研究背景**：Vision-Language-Action（VLA）模型（如 π0、π0.5、OpenVLA-OFT）被视为通用机器人策略的基础，能够根据自然语言指令直接执行操作任务。然而其在**分布外（OOD）指令**下的可靠性尚未被充分研究。
- **关键问题**：作者发现 VLA 模型存在一种严重失效模式——即使指令与场景语义矛盾，策略仍会执行视觉上合理的动作，而忽略语言指令。
- **现象定义**：作者将这一现象命名为 **"语言盲视"（Linguistic Blindness）**，即 VLA 策略在动作生成过程中过度依赖视觉先验，而忽视指令语义。
- **研究意义**：与对话式 AI 不同，机器人控制的失误会直接转化为物理动作，可能损坏物体、违反安全约束或引发危险行为。因此确保机器人对语言指令保持敏感性，是可信具身智能的核心需求。

## 2. 方法论

### 2.1 ICBench 诊断基准

- 基于 LIBERO 数据集构建，**保持视觉场景不变**，仅对指令进行受控的 OOD 语义扰动。
- **四种矛盾类型**：
  - **V1**：操作对象属性替换（如"黑碗"→"白碗"）
  - **V2**：目标位置属性增广（如"盘子"→"黑盘子"）
  - **V3**：双重属性扰动（操作对象与目标同时矛盾）
  - **V4**：空间关系替换（如"在桌上"→"在桌下"）
- **核心指标——语言基础评分（LGS）**：定义为正常指令成功率与矛盾指令成功率之差。LGS 越高表示语言指令对动作的影响越大。
- **设计原则**：最小表层扰动、确定性不可满足、语义复杂度多样化。

### 2.2 IGAR 方法（Instruction-Guided Attention Recalibration）

一种**免训练、推理时即插即用**的干预机制，通过三阶段恢复语言基础：

**阶段一：注意力汇（Sink）Token 检测**
- 计算隐藏状态的 RMS 范数，识别具有**局部极端激活**的特征维度（spike ratio φ(d) > γ=3.0）。
- 选取 top-k=5 个 spike 维度，当某 token 在这些维度上的最大值超过阈值 τ=20 时被判定为 sink token。
- 将 sink token 分为视觉 sink（SV）和文本 sink（ST）。

**阶段二：基础性头选择（Grounding Head Selection）**
- 对每个注意力头 h 和非图像区域的查询位置 q，筛选满足两个条件的头：
  - 条件 c1：头未被视觉 sink 主导（结构注意力而非语义注意力），ρ=0.4
  - 条件 c2：头对视觉 token 分配了显著注意力，α=0.01
- 两者同时满足的头才被选为干预对象。

**阶段三：注意力重分配**
- 对被选中的头-query 对，将 sink token 的注意力按比例 p=0.6 进行衰减。
- 释放的注意力预算 Ω 按原始注意力比例重新分配到非 sink 的文本 token。
- 干预范围为前 16 层 transformer，对不同 VLA 采用统一约束（π0.5 和 OpenVLA-OFT）或对比式离散化处理（π0 的流匹配扩散）。

**关键特性**：无需梯度更新、无需额外训练数据、无需修改模型架构，可直接嵌入部署的 VLA 策略。

## 3. 实验设计

- **基准数据集**：LIBERO（涵盖 **Spatial、Object、Goal** 三个套件共 30 个任务）。
- **评估模型**：三个代表性 VLA 架构——π0、π0.5、OpenVLA-OFT。
- **每变体实验次数**：50 次独立 rollout。
- **评估指标**：任务成功率（SR）与语言基础评分（LGS）。
- **对比方法**：仅与各 VLA 自身基线对比，未与其他鲁棒性方法（如 CAST、CounterfactualVLA）直接比较；注意力可视化作为定性分析。
- **消融实验**：三阶段（sink 检测、头选择、注意力重分配）逐步剥离。
- **超参敏感性实验**：衰减因子 p、边界 ρ、干预层数 L。
- **真实世界验证**：在 **Franka Research 3** 机械臂（配备两个 Intel RealSense D435 摄像头）上验证 π0 策略。

## 4. 资源与算力

- **GPU**：单卡 **NVIDIA RTX 5090**。
- **推理延迟**：OpenVLA-OFT 从 98.7±2.0 ms 增至 105.6±0.5 ms，开销约 +7.0 ms。
- **训练时长**：未明确报告（因 IGAR 免训练）。
- **数据规模**：50 trials × 30 任务 × 4 矛盾类型 × 3 VLA 模型为仿真实验规模；真实世界仅进行定性验证。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 三个 VLA 架构 × 三个 LIBERO 套件 × 四种矛盾类型 = **36 个核心评估单元**
  - 三阶段组件消融实验
  - 三个超参维度的敏感性分析
  - 真实世界定性验证
- **充分性评价**：
  - 实验设计较为系统，涵盖了诊断（Q1）、缓解（Q2）和保持（Q3）三个研究问题。
  - 不足之处在于：
    - 未与其他鲁棒性方法（如 CAST、CounterfactualVLA、SayCan）进行直接横向比较；
    - 真实世界实验仅做定性展示，缺少统计性指标；
    - 矛盾指令仅依赖人工模板生成，未考察更复杂的 OOD 形式（如长指令、否定句）；
    - 每个任务 50 次 rollout 属于中等规模。

## 6. 主要结论与发现

- **诊断结论**：现代 VLA 模型普遍存在**严重的语言盲视**。在 LIBERO 上，面对矛盾指令时 π0.5 和 OpenVLA-OFT 的成功率仍经常超过 90%，LGS 接近 0；π0 略好但仍存在显著视觉偏差。
- **IGAR 有效性**：在 OOD 矛盾指令下，IGAR 大幅降低错误执行率，LGS 显著提升（如 π0 在 Goal 套件 V4 下 LGS 从 19.4 提升至 59.4）。
- **基线保持性**：在正常指令下，IGAR 对性能影响极小（π0 平均 −0.4%，OpenVLA-OFT 平均 +0.5%）。
- **真实世界泛化**：在 Franka 机械臂上，π0+IGAR 能在矛盾指令下产生"应得的失败"（如悬停、空抓），而非基线的"虚假成功"。
- **架构差异**：π0 受益最大，π0.5 改进最有限（说明其视觉线索依赖更强）。

## 7. 优点与亮点

- **问题新颖性**：首次系统性地揭示并命名 VLA 中的"语言盲视"现象，填补了 OOD 指令鲁棒性研究的空白。
- **方法实用性**：IGAR 是首个针对 VLA 策略的推理时注意力干预方法，**无需训练、即插即用**，便于实际部署。
- **基准设计严谨**：ICBench 通过"视觉不变+语言矛盾"控制变量，精准隔离了语言-动作耦合度。
- **LGS 指标**：提出了直观的语言基础量化指标，比单纯的 SR 更能反映指令遵循能力。
- **跨架构验证**：覆盖了离散生成（OpenVLA-OFT）与流匹配扩散（π0/π0.5）两类范式。
- **真实世界验证**：在 Franka 平台上完成物理实验，超越纯仿真研究。

## 8. 不足与局限

- **外部对比缺失**：未与已有的鲁棒性 VLA 方法（CAST、CounterfactualVLA、SafeVLA 等）进行定量比较，难以判断 IGAR 的相对优势。
- **矛盾类型局限**：仅考察属性替换与空间关系替换四种类型，未覆盖否定句、复合指令、长指令、隐含意图等更复杂的 OOD 语言形式。
- **真实世界评估不充分**：仅展示定性案例，缺少统计性成功率与失败模式分析，泛化性证据有限。
- **超参依赖**：IGAR 的关键阈值（τ=20、γ=3.0、ρ=0.4、p=0.6、L=16）需预先标定，跨模型迁移性未充分验证。
- **机制解释不足**：仅给出注意力可视化，缺乏对"为何视觉汇形成"以及"为何文本 sink 检测能解决问题"的理论分析。
- **任务范围有限**：仅使用 LIBERO 仿真，未在 DROID、Open X-Embodiment 等大规模数据集衍生的策略上验证。
- **潜在副作用风险**：IGAR 在异常情况下可能产生"应得失败"，但如何在复杂环境中区分"安全拒绝"与"性能退化"未深入讨论。

（完）
