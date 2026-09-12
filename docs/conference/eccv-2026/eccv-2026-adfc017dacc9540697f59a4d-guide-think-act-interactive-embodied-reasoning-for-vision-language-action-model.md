---
title: "Guide, Think, Act: Interactive Embodied Reasoning for Vision-Language-Action Model"
title_zh: 引导、思考、动作：面向视觉-语言-动作模型的交互式具身推理
authors: "Yiran Ling, Qing Lian, Jinghang Li, Qing Jiang, TianMing Zhang, Xiaoke Jiang, Chuanxiu Liu, Jie Liu, Lei Zhang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/5953.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 交互式VLA框架用于机器人策略引导
tldr: 现有视觉-语言-动作（VLA）模型学习从多模态感知到动作的直接映射，但在分布外场景下表现脆弱且难以纠错，而现有具身思维链方法又缺乏人类空间引导机制。为此本文提出GTA-VLA交互式框架，允许用户通过显式视觉线索引导机器人策略并进行空间推理。该方法在视觉歧义和动作失误恢复方面增强了策略鲁棒性，对复杂操纵任务中的通用VLA模型具有重要意义。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 511, \"height\": 310}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 4000, \"height\": 2250}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-003.webp\", \"caption\": \"\", \"page\": 10, \"index\": 3, \"width\": 3223, \"height\": 1995}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-004.webp\", \"caption\": \"\", \"page\": 15, \"index\": 4, \"width\": 1279, \"height\": 1706}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-005.webp\", \"caption\": \"\", \"page\": 15, \"index\": 5, \"width\": 482, \"height\": 313}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-006.webp\", \"caption\": \"\", \"page\": 15, \"index\": 6, \"width\": 482, \"height\": 313}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-007.webp\", \"caption\": \"\", \"page\": 15, \"index\": 7, \"width\": 482, \"height\": 313}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-adfc017dacc9540697f59a4d/fig-008.webp\", \"caption\": \"\", \"page\": 15, \"index\": 8, \"width\": 482, \"height\": 313}]"
motivation: 现有VLA模型的紧耦合感知-动作映射在分布外易失效，且缺乏人类空间引导纠错机制。
method: 提出GTA-VLA交互式框架，融合显式视觉引导与具身思维链，实现空间可操控的机器人策略推理。
result: 在多种机器人操纵基准上显著提升VLA策略的分布外鲁棒性与可纠错能力。
conclusion: 该工作推动了可交互、可纠错的通用VLA模型在复杂任务中的实际部署。
---

## Abstract
In this paper, we propose GTA-VLA (Guide, Think,Act), an interactive Vision-Language-Action (VLA) framework thatenables spatially steerable embodied reasoning by allowing users to guiderobot policies with explicit visual cues. Existing VLA models learn adirect "Sense-to-Act" mapping from multimodal observations to robotactions. While effective within the training distribution, such tightly cou-pled policies are brittle under out-of-domain (OOD) shifts and difficultto correct when failures occur. Although recent embodied Chain-of-Thought (CoT) approaches expose intermediate reasoning, they stilllack a mechanism for incorporating human spatial guidance, limitingtheir ability to resolve visual ambiguities or recover from mistakes. Toaddress this gap, our framework allows users to optionally guide thepolicy with spatial priors, such as affordance points, boxes, and traces,which the subsequent reasoning process can directly condition on. Basedon these inputs, the model generates a unified spatial-visual Chain-of-Thought that integrates external guidance with internal task planning,aligning human visual intent with autonomous decision-making. Forpractical deployment, we further couple the reasoning module with alightweight reactive action head for efficient action execution. Extensiveexperiments demonstrate the effectiveness of our approach. On thein-domain SimplerEnv WidowX benchmark, our framework achievesa state-of-the-art 81.2% success rate. Under OOD visual shifts andspatial ambiguities, a single visual interaction substantially improvestask success over existing methods, highlighting the value of interactivereasoning for failure recovery in embodied control.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze an academic paper and provide a detailed Chinese summary following specific structural requirements. I need to organize the content into 8 sections covering: core problem, methodology, experimental design, computational resources, experiment quantity/sufficiency, conclusions, strengths, and limitations. Let me carefully analyze the paper content.

The paper is about GTA-VLA, an interactive Vision-Language-Action framework for embodied reasoning. Let me extract key information:

1. **Core Problem**: Existing VLA models use direct "Sense-to-Act" mapping which is brittle under OOD shifts. Embodied CoT methods lack human spatial guidance mechanisms.

2. **Method**: Guide-Think-Act paradigm with:
   - Guide: Optional spatial priors (points, boxes, traces)
   - Think: Structured spatial-visual CoT (Ctask, Cvision, Crobot)
   - Act: Flow-matching action head with async slow-fast execution
   - Uses Qwen3-VL-2B as backbone
   - Interact-306K dataset constructed automatically

3. **Experiments**:
   - Datasets/Benchmarks: LIBERO, SimplerEnv (Bridge/WidowX), SimplerEnv-Plus (new)
   - Comparisons: OpenVLA, OpenVLA-OFT, π0, π0.5, GR00T-N1, X-VLA, ThinkAct, CoT-VLA, Uni-VLA, MolmoAct
   - Real-world deployment with Agile Piper robot

4. **Resources**: Not explicitly mentioned in the text provided

6. **Main Results**:
   - LIBERO: 98.6% average success
   - SimplerEnv: 81.2% SOTA
   - OOD on SimplerEnv-Plus: significant improvements
   - Real-world: substantial improvements with guidance

Let me write a comprehensive Chinese summary following the required structure.</think>

# 论文总结：GTA-VLA（引导、思考、动作）

## 一、核心问题与研究动机

- **现有 VLA 模型的局限**：主流视觉-语言-动作（VLA）模型采用隐式的"感知-动作"（Sense-to-Act）端到端映射，仅在训练分布内有效。面对分布外（OOD）的视觉与语义偏移时表现脆弱，且当感知失败时缺乏显式纠错接口。
- **具身思维链方法的不足**：近期提出的"感知-思考-动作"范式（如 ECoT、MolmoAct 等）虽暴露了中间推理，但仍由模型内部信念驱动，无法被人类直接干预；在 OOD 场景下，错误的早期目标定位会传导为连贯但错误的规划。
- **核心研究问题**：如何在保持自主执行能力的同时，允许人类通过空间线索（如点、框、轨迹）直接对具身推理过程进行条件化引导，从而在空间歧义或失败发生时实现可纠错的机器人策略。
- **应用场景**：杂乱场景中的抓取、多候选相似物体消歧、跨分布泛化以及失败恢复等真实机器人操控任务。

## 二、方法论：Guide-Think-Act 框架

### 整体范式

将策略推理分解为三个阶段：
- **Guide（引导）**：在图像空间中接受可选的空间先验 $P_{\text{spatial}}$（点、框、轨迹），与语言指令和视觉观测融合。
- **Think（思考）**：VLM 主干生成结构化的空间-视觉思维链序列 $C$，并输出对应的隐状态 $H_{\text{reasoning}}$。
- **Act（动作）**：下游 Flow-Matching 动作头消费最新隐状态与高频控制观测，输出连续动作块 $A_t$。

### 关键技术组件

- **主干模型**：采用 Qwen3-VL-2B 作为视觉-语言主干，因其原生支持点/框坐标定位。
- **空间先验形式化**：
  - 仿生点引导 $P_{\text{point}} = (x, y)$：交互锚点；
  - 框引导 $P_{\text{bbox}} = (x_{\min}, y_{\min}, x_{\max}, y_{\max})$：目标区域；
  - 轨迹引导 $P_{\text{trace}} = \{(x_1, y_1), ..., (x_m, y_m)\}$：粗粒度运动偏好。
- **空间先验序列化**：将空间先验编码为与主干一致的相对坐标 token 串接在语言指令后；缺席时模型仍可自主推理。
- **结构化思维链 $C = [C_{\text{task}}, C_{\text{vision}}, C_{\text{robot}}]$**：
  - $C_{\text{task}}$：任务语义分解；
  - $C_{\text{vision}}$：视觉定位与功能点预测；
  - $C_{\text{robot}}$：机器人运动草图（2D 末端轨迹）。
- **条件化推理**：$P(C \mid I_t, L, P_{\text{spatial}})$，使同一主干在有无引导下共享推理路径。
- **异步快慢架构**：VLM 以低频生成推理与隐状态缓存；Flow-Matching 动作头以高频通过交叉注意力访问最新缓存，避免每步自回归解码。
- **训练数据**：自动构建 Interact-306K（来自 Open X-Embodiment、DROID、RoboMind、BridgeData V2 等共约 30.6 万条轨迹），含关键帧提取、任务分解、开放词汇定位（DINO-X）、跟踪过滤、末端轨迹投影等步骤；对生成的空间标注添加随机扰动以模拟真实交互。
- **两阶段训练**：阶段一在 Interact-306K 上训练主干与动作头；阶段二在目标本体（如 BridgeData V2）上联合微调。

## 三、实验设计

### 基准与场景

- **LIBERO**（sim-to-sim）：Spatial / Object / Goal / Long 四个子集，用于多任务泛化评估。
- **SimplerEnv（Bridge / WidowX）**（real-to-sim）：真实机器人高保真数字孪生，测试零样本视觉运动迁移。
- **SimplerEnv-Plus**（本文新提出的 OOD 基准）：四类扰动——视觉偏移（光照、视点）、机器人状态偏移（初始位姿与执行噪声）、语言偏移（动词/名词/属性词替换）、物体偏移（未见物体与同类别干扰物）。
- **真实机器人**：Agile Piper 6-DoF + 主相机 + 腕部相机（Realsense D435），执行四类抓取任务（已见/未见 × 单目标/多候选）。

### 对比方法

- OpenVLA、OpenVLA-OFT、π0、π0.5、GR00T-N1、X-VLA、ThinkAct、CoT-VLA、Uni-VLA、MolmoAct 等十余种主流 VLA 与具身 CoT 方法。

## 四、资源与算力

- **未在正文或附录摘要中明确披露**具体的 GPU 型号、卡数与训练时长。文中仅说明训练在 Interact-306K 与目标本体数据上进行两阶段训练，未给出算力开销或推理延迟的详细数字。

## 五、实验数量与充分性

- **基准对比**：LIBERO 与 SimplerEnv（Bridge）主结果表 1，覆盖 10+ 基线。
- **OOD 泛化**：SimplerEnv-Plus 4 类扰动 × 4 种方法（表 2）。
- **引导有效性**：表 3 系统评估稠密语言指令、点引导、框引导在未见物体与干扰物歧义场景下的表现；另单独分析轨迹引导。
- **消融实验**：表 4 分别去除 $C_{\text{robot}}$、$C_{\text{task}}$、$C_{\text{vision}}$，并对比自由形式 CoT。
- **真实机器人**：图 4 展示 4 类任务的定性结果与定量成功率（基线 / w/ CoT / w/ 点引导）。
- **充分性评价**：实验覆盖了标准基准、专门设计的 OOD 基准、消融与真实部署，多维度验证了自主性能与交互纠错能力，较为系统；但缺乏与同类具身 CoT 方法在 OOD 场景下的细粒度对照，且引导触发方式依赖人工或脚本，自动触发（不确定性/失败检测）被列为未来工作。

## 六、主要结论与发现

- **自主性能**：在 LIBERO 平均成功率 98.6%，与最强基线相当；在 SimplerEnv（Bridge）平均成功率 **81.2%**，达到 SOTA。
- **OOD 鲁棒性**：在 SimplerEnv-Plus 的视觉、机器人状态、语言、物体四类偏移下均显著优于 OpenVLA、π0.5、X-VLA，物体偏移场景提升最显著（平均 61.4% vs X-VLA 52.3%）。
- **交互纠错有效性**：在未见物体歧义场景下，稠密语言指令平均 27.8%，加入点引导提升至 40.9%，加入框引导进一步提升至 56.9%；干扰物歧义下点引导平均提升至 54.2%。轨迹引导在避障/约束路径任务上将成功率从 27.8% 提升至 30.5%。
- **结构化 CoT 的价值**：消融表明 $C_{\text{vision}}$ 影响最大（-14.5%），其次是 $C_{\text{task}}$（-12.4%），$C_{\text{robot}}$ 影响最小（-3.1%）；自由形式 CoT 性能下降 15.6%，说明显式结构化字段更有利于与用户先验对齐。
- **真实机器人**：在已见/未见 × 单目标/多候选四类抓取任务上，引入 CoT 与点引导均带来持续提升，在未见与指代消歧场景下提升最大。

## 七、优点与亮点

- **可条件化引导接口设计**：将空间先验作为可选 token 直接拼入指令，保持单一推理路径同时支持自主与交互模式，工程上简洁优雅。
- **显式结构化空间-视觉 CoT**：相比自由形式 CoT 更稳定、更可控，便于对接外部几何约束。
- **异步慢-快架构**：在保留丰富推理能力的同时解决自回归 VLM 在实时控制中的延迟瓶颈。
- **可扩展数据管线**：Interact-306K 由现有轨迹自动合成空间-CoT 监督，无需人工采集干预轨迹，训练成本可控。
- **专门构建的交互式 OOD 基准**：SimplerEnv-Plus 显式覆盖视觉/状态/语言/物体四类扰动，为交互式 VLA 评测提供基础设施。
- **真实机器人验证**：在 Agile Piper 上完成四类任务的端到端验证，体现工程落地价值。

## 八、不足与局限

- **2D 图像空间限制**：引导接口与推理均以 2D 图像坐标为基础，缺乏 3D 几何先验；作者明确将此列为未来工作。
- **算力与效率未披露**：训练算力、推理延迟与实时性数据缺失，难以评估部署成本。
- **引导触发依赖人工/脚本**：未实现基于置信度、不确定性或失败检测的自动触发，限制了完全自主系统的实用性。
- **本体单一**：实验集中在单臂 WidowX / Agile Piper，论文指出可扩展至双臂但未实际验证；SimplerEnv 主要报告 WidowX，Google Robot 结果被推迟到附录。
- **真实实验规模较小**：真实机器人仅 4 类任务、每类仅展示 1 个对比柱状数据，未给出统计显著的多次重复实验细节，存在过拟合到特定任务设置的风险。
- **基线公平性**：部分基线（如 X-VLA）使用最大推理步长 120 步的复现结果，且不同方法可能在本体对齐、动作参数化上存在差异，对比并非绝对公平。
- **OOD 实验覆盖**：虽然 SimplerEnv-Plus 设计较为系统，但与同类具身 CoT（如 MolmoAct、CoT-VLA）的直接 OOD 对照较少，未能充分隔离"结构化 CoT"与"空间引导"各自的贡献。

（完）
