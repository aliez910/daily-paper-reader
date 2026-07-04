---
title: "GENMANIP: LLM-driven Simulation for Generalizable Instruction-Following Manipulation"
title_zh: GenManip：基于大语言模型的指令跟随操作泛化仿真平台
authors: "Gao, Ning, Chen, Yilun, Yang, Shuai, Chen, Xinyi, Tian, Yang, Li, Hao, Huang, Haifeng, Wang, Hanqing, Wang, Tai, Pang, Jiangmiao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Gao_GENMANIP_LLM-driven_Simulation_for_Generalizable_Instruction-Following_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向指令跟随操作泛化的基准仿真平台
tldr: 真实环境中的机器人操作面临严重的泛化挑战，现有仿真平台难以支持指令跟随策略在多样化任务与场景下的公平对比。本文构建 GenManip 桌面仿真平台，通过 LLM 驱动的任务导向场景图自动合成大规模多样化任务，并依托一万余个标注三维资产系统评估泛化能力。该平台填补了指令跟随基础模型在操作领域评测的空白，有助于推动可泛化操作策略的研究。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1767, \"height\": 1116, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1783, \"height\": 813, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 491, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1791, \"height\": 703, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 448, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 850, \"height\": 402, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1810, \"height\": 512, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1591, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 810, \"height\": 207, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-gao-genmanip-llm-driven-simulation-for-generalizable-instruction-following-manipulation-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 826, \"height\": 334, \"label\": \"Table\"}]"
motivation: 现有仿真平台不支持对指令跟随操作策略在多样化任务中的泛化进行公平评估。
method: 利用 LLM 驱动的任务导向场景图与大规模标注三维资产自动合成多样化操作任务与场景。
result: 提供了一个可系统评估操作泛化能力的大规模仿真基准平台。
conclusion: GenManip 为指令跟随操作策略的泛化研究提供了公平、可扩展的仿真基础设施。
---

## Abstract
Robotic manipulation in real-world settings remains challenging, especially regarding robust generalization. Existing simulation platforms lack sufficient support for exploring how policies adapt to varied instructions and scenarios. Thus, they lag behind the growing interest in instruction-following foundation models like LLMs, whose adaptability is crucial yet remains underexplored in fair comparisons. To bridge this gap, we introduce GenManip, a realistic tabletop simulation platform tailored for policy generalization studies. It features an automatic pipeline via LLM-driven task-oriented scene graph to synthesize large-scale, diverse tasks using 10K annotated 3D object assets. To systematically assess generalization, we present GenManip-Bench, a benchmark of 200 scenarios refined via human-in-the-loop corrections. We evaluate two policy types: (1) modular manipulation systems integrating foundation models for perception, reasoning, and planning, and (2) end-to-end policies trained through scalable data collection. Results show that while data scaling benefits end-to-end methods, modular systems enhanced with foundation models generalize more effectively across diverse scenarios. We anticipate this platform to facilitate critical insights for advancing policy generalization in realistic conditions. All code will be made publicly available.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "GENMANIP: LLM-driven Simulation for Generalizable Instruction-Following Manipulation" following a specific structure. Let me carefully analyze the paper content and organize it according to the 8 required sections.

Let me extract the key information:

1. **Core problem**: Real-world robotic manipulation generalization is challenging. Existing simulation platforms don't support fair evaluation of instruction-following policies across diverse tasks and scenarios.

2. **Method**: 
- GenManip platform built on Isaac Sim
- Task-oriented Scene Graph (ToSG) for scenario synthesis
- LLM-driven (GPT-4) automatic task generation
- 10K annotated 3D object assets from Objaverse, GRUtopia, PartNet-Mobility
- 100 articulated objects
- Primitive skills: pick, place for rigid objects; open, close, press, push, pull, twist for articulated
- LLM-driven ToSG generation: nodes (object, status), edges (object, relation, anchor), goal conditions
- ToSG-based layout construction with topological sorting

3. **Experiments**:
- GenManip-Bench: 200 human-curated scenarios
- Compared modular methods: CoPA, MOKA with various MLLMs (GPT-4o, GPT-4.5, Claude-3.7-Sonnet, Gemini-2.0-Flash, Qwen2.5-VL-72B)
- Compared end-to-end methods: GR-1, ACT
- Data scaling: 100, 200, 300, 500, 1000 episodes
- Generalization scenarios: limited region, full table, 5 scenes, unseen instructions, unseen objects
- Metrics: SR (success rate) and SPL (success rate weighted by path length)

4. **Resources**: The paper doesn't explicitly mention GPU models, count, or training duration. Computational constraints are mentioned but no specifics.

5. **Experiment sufficiency**: Multiple ablations - distractors, task horizon, modular ablations, learning-based ablations. User study on realism. But full evaluation on all 200 scenarios left for future work due to computational constraints.

6. **Conclusions**: 
- Modular methods generalize better but struggle with spatial perception
- End-to-end methods benefit from scaling but sensitive to scene/instruction changes
- Dual-system framework suggested as scalable alternative

7. **Highlights**: 
- ToSG as scalable, LLM-compatible representation
- 10K annotated assets
- Human-in-the-loop curated benchmark
- Comprehensive comparison of modular vs end-to-end approaches
- User study showing realism comparable to/better than other benchmarks

8. **Limitations**:
- Full-scale evaluation across 200 scenarios not done
- Limited skill types
- Only pick-and-place demonstrated primarily
- Single task in scaling experiments (pick banana)
- Long-horizon tasks remain challenging for both approaches

Let me write this up in Chinese with proper Markdown formatting.</think>

# GENMANIP 论文总结

## 1. 核心问题与研究动机

- **核心问题**：真实环境下的机器人操作策略缺乏足够的泛化能力，而现有仿真平台难以支持对**指令跟随（instruction-following）策略**在多样化任务与场景下的公平、系统化评估。
- **背景矛盾**：以 LLM/MLLM 为代表的"基础模型驱动的模块化方法"与以 VLA 为代表的"端到端模仿学习方法"是目前提升操作泛化能力的两大主流路线，但二者在统一基准下的对比仍然缺失。
- **现有平台的不足**：RLBench、LIBERO、CALVIN 等平台要么场景过于简化、要么采用纯随机化布局，无法测试 MLLM 对空间/常识/外观/长程推理能力；RoboCasa 虽强调真实感和多样性，但缺乏标准化的指令与场景评测基准。
- **本文目标**：填补"指令跟随 + 多样化场景 + 公平评测"的空白，提供一个面向泛化研究的大规模、可控、真实感桌面操作仿真平台与基准。

---

## 2. 方法论

### 2.1 平台基础
- 基于 **NVIDIA Isaac Sim** 构建，利用其照片级渲染与并行数据采集能力。
- **资产规模**：从 Objaverse 的 660K 模型经 GPT-4V 筛选标注得到 **10K 刚体资产** + **100 关节体资产**（如笔记本、垃圾桶、微波炉、抽屉等），并加入 **100 个 HDRI 室内背景**。
- **VL 标注**：每个资产包含物体描述、物理属性（尺寸、质量）与语义属性（类别、颜色、形状、材质），通过 GPT-4V 自动生成并经人工校正。
- **原子技能**：刚体支持 pick/place 等关键姿态（pre-grasp、post-grasp、move、pre-place、post-place）；关节体支持 open/close/press/push/pull/twist（参考 MimicGen/SkillMimicGen）。

### 2.2 任务导向场景图（ToSG）
针对 PDDL 对 LLM 不够友好的问题，提出更轻量的中间表示：
- **节点**：`(object, status)` 表示物体及其状态（如 open/closed）。
- **边**：`(object, relation, anchor_object)` 表示物体间空间关系（left/right/front/behind/near/on/in）。
- **目标条件**：由若干 pair/triplet 组成，用于任务完成评估。
- **LLM 友好性**：使用自然语言描述，便于 GPT-4 生成与回放校验。

### 2.3 LLM 驱动的任务合成流水线
1. **种子采样**：随机采样种子物体 + 任务类型（空间/外观/常识/长程）。
2. **ToSG 生成**：GPT-4 根据种子物体标注与提示词生成 ToSG。
3. **布局构建**：按 `on/in` 关系拓扑排序放置物体，并满足空间关系约束（如 "near" 在 5cm 阈值内）。
4. **可执行性校验**：通过至少一条运动规划演示验证任务可执行。
5. **自动数据采集**：基于特权信息与原子技能，利用 MPlib 运动规划为每个目标条件生成一条演示。

### 2.4 评测机制
- 将最终场景反向转换为 ToSG，与目标条件做**逻辑比对**，得到任务成功率。
- 物理仿真上限 **9000 步**（约 150s @ 60 FPS）。
- 指标：**SR（Success Rate）** 与 **SPL（Success weighted by Path Length）**。

---

## 3. 实验设计

### 3.1 数据集与基准
- **GenManip-Bench**：**200 个人工校正的场景**，覆盖四类任务：
  - 长程规划（long horizon）
  - 空间推理（spatial）
  - 外观推理（appearance）
  - 常识推理（common sense）
- 同时提供大规模训练用合成场景用于端到端方法的扩展训练。

### 3.2 对比方法

| 类别 | 方法 | 说明 |
|------|------|------|
| 模块化（零样本） | **CoPA†** | 空间约束 + 部件级视觉提示（GPT-4V/4o/4.5、Claude-3.7、Gemini-2.0、Qwen2.5-VL-72B） |
| 模块化（零样本） | **MOKA†** | 基于 Mark 的视觉提示规划（同上五种 MLLM） |
| 端到端 | **GR-1** | GPT 风格跨模态视频生成式策略 |
| 端到端 | **ACT** | Transformer + 时间集成策略 |

### 3.3 实验维度
- **模块化评测**：在 200 场景全集上对比五种 MLLM 的 CoPA 与 MOKA。
- **消融**：任务长程步数（horizons）、干扰物数量（distractors）、抓取提议（SoM vs CtoF-SoM）、运动规划方式（PointToPoint vs Mark-based Grid）。
- **端到端数据规模消融**：100/200/300/500/1000 episodes，单任务"将香蕉放在盘子上"。
- **端到端泛化消融**：有限区域随机化 / 全桌随机化 / 5 场景跨布局 / 未见指令 / 未见物体。

---

## 4. 资源与算力

- **论文中未明确说明**所使用的 GPU 型号、数量与训练时长。
- 论文仅在 5.3 节末尾提到"由于计算限制，全 200 场景的端到端评估留待未来工作"，间接说明算力受限。
- 推理侧使用 GPT-4o/4.5、Claude-3.7、Gemini-2.0-Flash、Qwen2.5-VL-72B 等闭源/开源 MLLM 作为云服务调用，未提及 API 成本。

---

## 5. 实验数量与充分性

- **实验规模**：
  - 模块化实验覆盖 **2 种方法 × 5 种 MLLM × 4 类任务**，每个方法-MLLM 组合均在 200 场景上评测；
  - **消融实验 4 组**：horizons、distractors、抓取提议、运动规划；
  - 端到端 **6 个泛化设置 × 6 个数据规模**；
  - 真实感 **用户研究**：对 5 个基准各采样 20 场景做 1–5 分排序。
- **充分性与公平性**：
  - 优点：模块化方法采用**统一接口**重写 CoPA / MOKA 并在相同基准下对比，避免了各方法在自设场景下的偏差。
  - 不足：端到端方法仅在 1 个单任务（pick banana→plate）上做数据缩放评测，未在 200 场景上完整评测；GR-1 与 ACT 的泛化测试与模块化方法共享同一基准，但样本数与场景多样性受限。

---

## 6. 主要结论与发现

- **模块化方法在零样本泛化上更优**：CoPA + GPT-4.5 在全部任务上达到 **23.0% SR**，显著优于其他组合。
- **模块化方法在长程任务上表现最差**：所有模型平均仅 **9.07% SR**，瓶颈在于任务分解与子步骤映射。
- **外观与常识类任务相对较好**：MLLM 能借助先验知识理解物体属性。
- **路径效率低**：CoPA 的 SPL 约为 SR 的 1/6，MOKA 甚至为 1/10，说明中间表示驱动的规划难以生成最优路径。
- **端到端方法依赖数据规模**：GR-1 从 100 到 1000 episodes 时 SR 从 33% 提升到 95%，ACT 从 40% 提升到 72.5%。
- **端到端方法泛化能力脆弱**：在 5 场景跨布局下仅 43.5% SR，对**未见指令和未见物体几乎完全失败（0%）**。
- **总体结论**：模块化系统凭借基础模型的语义/常识先验在多样化场景下泛化更稳健；端到端方法虽然能随数据扩展，但在语义与组合层面的泛化仍然有限，**双系统框架（dual-system）** 被认为更具可扩展性。

---

## 7. 优点与亮点

- **ToSG 表示法**：兼具结构化与 LLM 友好的特性，简化了 PDDL 的复杂语法，便于大规模自动合成与可逆回放评估。
- **资产与标注规模化**：10K 标注刚体 + 100 关节体 + HDRI 背景，覆盖度远高于现有桌面操作平台（Tab.1）。
- **基准构建采用 human-in-the-loop**，在 200 场景上保证真实感与多样性。
- **真实感用户研究**显示 GenManip 真实度（1.4±0.3）优于 RLBench（4.0±0.5）、RoboCasa（1.6±0.4）等。
- **统一接口下对比模块化 vs 端到端**，并对模块化系统内部每个模块做细粒度消融，定位误差来源。
- **提出 SR + SPL 双指标**，同时考察任务完成与路径效率，揭示了模块化方法的路径次优问题。
- **可扩展性强**：ToSG 既是任务生成接口，又是评测接口，便于社区扩展任务类型与场景。

---

## 8. 不足与局限

- **端到端方法评测规模不足**：仅在 1 个单任务上做数据规模消融，未在 200 场景上完成大规模训练与评测（作者承认受算力限制）。
- **技能覆盖有限**：刚体仅演示 pick-and-place；关节体虽定义了 6 类技能（open/close/press/push/pull/twist），但未在主实验中充分验证。
- **长程任务仍是难点**：模块化与端到端方法在 horizon≥2 时均显著下降，问题未被充分解决。
- **未涉及双臂、移动操作、柔性物体**等更复杂操作类型。
- **基准局限于桌面场景**，未覆盖 Behavior-1K 所强调的"日常全场景活动"。
- **MLLM 调用受限于 API**，结果可能因模型版本更新而不可复现。
- **真实感仅通过用户主观评分**评估，缺乏与真实世界硬件 sim-to-real 的迁移验证。
- **场景生成仍依赖 GPT-4**，存在幻觉与失败模式（如不合物理的布局），需要人工后期校正。

（完）
