---
title: "Exploratory, Communicative, and Deployable: Vision-Driven Embodied Agents for Open-World Mobile Manipulation"
title_zh: 探索、沟通与可部署：面向开放世界移动操作的视觉驱动具身智能体
authors: "Boyu Mi, Mengchen Ma, Yifei Yao, Xing Gao, Hanqing Wang, Junting Chen, Yangzi Li, Zihou Zhu, Guohao Li, Zhenfei Yin, Tai Wang, Yao Mu, Jiangmiao Pang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/13173.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 视觉驱动的移动操作智能体
tldr: 现有机器人框架常依赖特权仿真器状态或完整指令，绕过真实部署挑战。本文提出REAL，一个面向开放世界移动操作的智能体框架，构建了无需神谕感知的仿真到真实一致环境接口，并集成模拟用户实现人在回路交互。框架设计多样化任务驱动数据收集、监督微调与在线强化学习，系统优化智能体在真实环境中的部署性能。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 880, \"height\": 544}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 1024, \"height\": 775}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-007.webp\", \"caption\": \"\", \"page\": 6, \"index\": 7, \"width\": 1440, \"height\": 1440}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-008.webp\", \"caption\": \"\", \"page\": 6, \"index\": 8, \"width\": 530, \"height\": 298}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-009.webp\", \"caption\": \"\", \"page\": 6, \"index\": 9, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-010.webp\", \"caption\": \"\", \"page\": 6, \"index\": 10, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-011.webp\", \"caption\": \"\", \"page\": 6, \"index\": 11, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-012.webp\", \"caption\": \"\", \"page\": 6, \"index\": 12, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-013.webp\", \"caption\": \"\", \"page\": 14, \"index\": 13, \"width\": 1343, \"height\": 224}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-014.webp\", \"caption\": \"\", \"page\": 14, \"index\": 14, \"width\": 2022, \"height\": 336}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-015.webp\", \"caption\": \"\", \"page\": 14, \"index\": 15, \"width\": 1274, \"height\": 205}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-016.webp\", \"caption\": \"\", \"page\": 14, \"index\": 16, \"width\": 1177, \"height\": 188}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f6360d1b5e5b065a94b56e6d/fig-017.webp\", \"caption\": \"\", \"page\": 14, \"index\": 17, \"width\": 2048, \"height\": 1144}]"
motivation: 现有具身智能体框架依赖特权仿真器状态或完整指令，难以应对真实部署中的探索与意图消歧挑战。
method: 提出REAL框架，建立无需神谕感知的仿真到真实一致环境API，并集成模拟用户以支持人在回路交互。
result: 通过多样化任务组合驱动数据收集、监督微调与在线强化学习，系统提升开放世界移动操作性能。
conclusion: 为视觉驱动的真实世界移动操作智能体部署提供了完整的端到端解决方案。
---

## Abstract
Real-world deployment of embodied agents requires activeexploration, visual grounding, and interactive intent disambiguation. How-ever, existing frameworks often rely on privileged simulator states or as-sume complete instructions, bypassing realistic deployment challenges.To bridge this gap, we present REAL, an agentic framework for open-world mobile manipulation. REAL establishes sim-to-real-consistent en-vironment APIs without oracle perception and integrates a simulateduser to enable human-in-the-loop interaction. Within this environment,we design diverse task compositions to drive data collection, supervisedfine-tuning, and online reinforcement learning, systematically optimizingagent performance. To comprehensively evaluate this approach, we in-troduce REAL-Bench, a benchmark spanning 241 tasks across activeexploration, visual distraction, articulated manipulation, and interactivedisambiguation. Experimental results demonstrate that our trained agentoutperforms leading commercial closed-source VLMs on interactive taskswith a 56.9% success rate. Further empirical analysis reveals that ourhierarchical training pipeline successfully aligns the model’s tool-use ca-pabilities while maintaining robust open-vocabulary reasoning under ex-tended exploration horizons. Finally, we deploy and evaluate our frame-work on a physical dual-arm mobile robot, where it achieves a 78.3%end-to-end success rate over 60 real-world episodes. These physical trialsdemonstrate robust zero-shot transferability to unseen household scenar-ios, validating that our sim-to-real-consistent design successfully bridgesthe reality gap for long-horizon mobile manipulation. Code is availableat https://github.com/InternRobotics/REAL.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Exploratory, Communicative, and Deployable: Vision-Driven Embodied Agents for Open-World Mobile Manipulation" following a specific structure with 8 sections. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is about REAL framework for embodied agents in mobile manipulation. Let me go through each required section:

1. Core problem and motivation: Real-world deployment challenges - active exploration, visual grounding, interactive intent disambiguation. Existing frameworks rely on privileged simulator states or complete instructions.

2. Methodology: REAL framework with:
- Sim-to-real-consistent environment APIs without oracle perception
- Simulated user for human-in-the-loop interaction
- Multi-level active exploration toolchain (nav_to, walk_around, show_object_by_category, gaze_at)
- POMDP formulation with aggregated state
- SFT + GSPO (Group Sequence Policy Optimization)
- World Graph representation for state tracking

3. Experiments: REAL-Bench with 241 tasks across 4 families (FDP, FODP, FDO, SUL). Compared with Gemini 3 Pro, Gemini 2.5 Pro, GPT-5, GPT-4o, Claude Haiku 4.5, Qwen3-VL-235B, Qwen3-VL-8B.

4. Resources: Not explicitly mentioned in the extracted text.

5. Experimental completeness: Main table comparison, failure mode taxonomy (100 episodes manual analysis), ablation-like studies on SFT epochs and RL addition, real-world deployment with 60 episodes.

6. Main conclusions: Outperforms commercial VLMs on interactive tasks (56.9% success), 78.3% real-world success rate, validates sim-to-real transfer.

7. Strengths: 
- No oracle perception
- Simulated user for dynamic intent alignment
- Two-stage SFT+RL training
- Real-world validation on physical robot
- Tool-use alignment + adaptive replanning

8. Limitations:
- Task space limited to cross-receptacle rearrangement
- Simulated user has bounded behavioral envelope
- Receptacles modeled as monolithic without part-level distinction
- Vision encoder frozen limits articulated manipulation

Let me write this in Chinese with Markdown format.</think>

# 论文总结：REAL——面向开放世界移动操作的视觉驱动具身智能体

## 1. 核心问题与研究动机

**研究背景**：随着大语言模型（LLM）与视觉语言模型（VLM）的发展，具身智能体（Embodied Agent）在长程任务规划中展现了强大能力。然而现有框架在从仿真走向真实部署时仍存在两类根本性局限：

- **主动探索的"特权依赖"**：多数环境为智能体提供全局对象列表（如 Embodied Agent Interface、ManiTaskGen）、理想化的"find"工具（如 VisualAgentBench、EmbodiedBench、VoTa-Bench，可瞬移定位目标），或仅在文本层面进行探索（PARTNR、EMMOE）。这些特权接口难以在真实机器人上复现，导致 sim-to-real 性能落差。
- **指令的"完全明确假设"**：现有基准默认用户已掌握场景全局信息，给出无歧义指令并执行开环流程。真实场景中，用户的初始指令往往带有歧义（多个候选目标、未知偏好），需要智能体主动对话澄清（如 ADAPT、FARMER 仅关注偏好查询或习惯记忆，缺乏与移动操作的闭环协同）。

**研究目标**：REAL（**Explo**Ratory、communicativ**E**、**A**nd deploy**L**able）旨在构建一个**消除神谕感知（oracle-free）**、**集成模拟用户（simulated user）**、**可零样本迁移到真实机器人**的端到端框架。

---

## 2. 方法论

### 2.1 整体架构

REAL 基于 GRUtopia 仿真平台，包含三大组件：
- **无神谕环境接口**：智能体只能获得"物理可获取"的环境先验（如长期 3D 占据图、容器语义类别），不能访问全局对象列表、目标 3D 位姿、仿真器状态、目标坐标。
- **多层级主动探索工具链**：
  - `nav_to`：容器间导航（基于结构先验）
  - `walk_around`：绕容器扫描，绕过遮挡、多视角检测
  - `show_object_by_category`：开词汇 2D 感知，定位指定类别目标
  - `gaze_at`：逼近目标并居中（考虑物理距离约束）
- **视觉交互接地**：将 2D 分割结果反向投影到 3D 空间，构建临时探索地图；通过 Set-of-Mark（SoM）提示将视觉 ID 注入观测，使 pick/open 等操作完全通过视觉 ID 参数化。
- **模拟用户**：基于 Gemini 3 Flash 驱动，监控智能体执行历史，提供动态多轮反馈；用户只能看到智能体的探索结果，无法访问仿真器后端状态。

### 2.2 问题形式化（POMDP）

由于长程任务上下文会爆炸，REAL 不拼接全历史，而是采用聚合状态：

$$o_t = \langle o_t^{env}, o_t^{hist} \rangle, \quad o_t^{hist} = \langle o_{t-1}^{env}, a_{t-1}, h_{t-1} \rangle$$

历史状态 $h_t = (\Sigma_t, task_t)$ 通过 VLM 自总结（self-summarization）压缩：

$$h_t \leftarrow VLM(o_t^{env}, a_t, h_{t-1})$$

其中 $\Sigma_t = [\sigma_0, \sigma_1, ..., \sigma_t]$ 仅记录被环境反馈 $e_t$ 确认成功的动作，保证 $o_t^{hist}$ 对 $t-1$ 时刻自然滤波 $\mathcal{F}_{t-1}$ 可测，保持 POMDP 因果结构。

### 2.3 训练流程

**阶段一：监督微调（SFT）—— 工具调用对齐**
- 以 Qwen3-VL-8B-Instruct 为基座（冻结视觉编码器以保留预训练视觉表征）。
- 由规则规划器在仿真器中执行轨迹，并通过 LLM 进行"社交注释"（Social Annotation），将指令改写为含歧义版本、注入 `ask` 动作与模拟用户回复。
- 损失函数为标准行为克隆负对数似然：

$$\mathcal{L}_{SFT} = -\sum_{(T,\tau)\in \mathcal{D}} \sum_{t=1}^{L} \log \pi_\theta(a_t, h_t \mid T, o_t)$$

**阶段二：在线强化学习（RL）—— GSPO**
- 采用 **Group Sequence Policy Optimization (GSPO)** 而非 GRPO。原因：GRPO 用步级重要性比率，累积 log-ratio 方差随长度增长，易触发剪裁；GSPO 改用长度归一化的序列比率，将方差压缩 $1/L^2$，适合长程 rollout。
- **奖励设计（基于 World Graph）**：
  - 定义世界图 $WG = \{(r_j, E_j)\}$，$\Delta_{task} = WG^{goal} - WG^{init}$ 列出所需状态变更（如 pick n 个对象产生 $2n$ 项）；
  - 每步即时差异 $\delta_t = WG_t - WG_{t-1}$ 与 $\Delta_{task}$ 匹配即得正奖，命中条目移除以防止 reward hacking；
  - 物理引擎天然约束时序因果（pick-before-place）；
  - 加入关节操作与导航子目标奖励；
  - 含时间惩罚 $-\lambda_{time}$ 与失败动作的严重度分级惩罚；
  - 对含干扰物的任务，对 `ask` 工具按难度条件查询预算 $B_{ask}$ 给予奖励。

### 2.4 数据资产

- 7 个高保真场景（来自 GRScenes，11 种房间类型、100 个可交互容器）；
- 2,500+ 物体实例、639 个类别（来自 MesaTask）；
- 同时在物体级与容器级引入干扰物，要求细粒度视觉消歧。

---

## 3. 实验设计

### 3.1 基准：REAL-Bench

共 **241 个任务实例**，分四类：
| 类别 | 数量 | 说明 |
|------|------|------|
| FDP（Furniture-Distractor Pick-and-Place） | 72 | 容器级干扰的移动操作 |
| FODP（Furniture & Object-Distractor Pick-and-Place） | 56 | 容器+物体双层干扰，开词汇全类别 |
| FDO（Furniture-Distractor Open/Close） | 48 | 关节操作（开/关柜门抽屉），高动态状态转换 |
| SUL（Simulator-User-Loop） | 65 | 指令含歧义，需主动 `ask` 用户澄清 |

### 3.2 对比基线

零样本提示：Gemini 3 Pro Preview、Gemini 2.5 Pro、GPT-5、GPT-4o、Claude Haiku 4.5、Qwen3-VL-235B-A22B-Instruct、Qwen3-VL-8B-Instruct。

### 3.3 训练变体
- Ours-8B-SFT-only（1 epoch）
- Ours-8B-SFT-only（2 epoch）
- Ours-8B-SFT+RL（GSPO）

### 3.4 真实部署

硬件：Ark LIFT2 双臂移动机器人；底层操作由微调的 $\pi_{0.5}$ VLA 模型执行；高层策略通过 Model Context Protocol（MCP）零样本迁移；评估 60 个真实回合。

---

## 4. 资源与算力

论文未明确披露训练所用的 GPU 型号、数量或训练时长，仅提到：
- 训练在仿真环境（GRUtopia）中进行；
- 选 8B 参数的 Qwen3-VL-8B 以适配算力受限的机器人平台；
- 数据合成、轨迹生成、模拟用户调用 Gemini 3 Pro/Flash。

**算力信息缺失**：这是一个明显的报告空白，读者无法评估训练成本或复现门槛。

---

## 5. 实验数量与充分性

实验规模相对充分：

- **仿真主表**：在 4 个任务族 × 8 个基线 + 3 个训练变体 = 共 **44 个数据点**，覆盖主动探索、视觉干扰、关节操作、交互消歧四类核心能力。
- **消融式分析**：通过 SFT 不同 epoch 数（1 vs 2）+ RL on/off 三组对比，展示行为克隆过拟合与 RL 恢复泛化的关键现象；相当于消融 SFT 强度、RL 必要性、奖励设计（含 ask 社交奖励）。
- **失败模式分析**：人工标注 SFT+RL 模型 100 个回合，按对象混淆（25%）、关键动作缺失（17%）、记忆丢失（9%）、其他（2%）分类，提供诊断信息。
- **真实部署**：60 个回合（FDO/SUL/FODP 三类），并报告 SR、SPL、平均查询次数、VLM 推理延迟。
- **公平性考量**：所有基线均使用零样本提示；REAL 训练用 Qwen3-VL-8B 是公开小模型，对比了多个闭源商用大模型，体现了"小模型+专门训练优于闭源通用大模型"的核心论点。

但仍有一定局限：未做不同场景规模、不同物体类别的进一步细粒度消融；RL 阶段的超参（$\lambda_{time}$、$B_{ask}$）扫描未公开；模拟用户行为的多样性未做敏感性测试。

---

## 6. 主要结论与发现

1. **智能体优于闭源大模型**：Ours-8B-SFT+RL 在交互型任务 SUL 上达到 **56.9%** 成功率，超过 Gemini 3 Pro Preview（53.8%）、GPT-5（52.3%）等闭源模型。
2. **真实部署有效**：60 个真实回合达到 **78.3%** 端到端成功率，无不可恢复的系统崩溃；底层 VLA 原语执行成功率 85.3%。
3. **SFT 与 RL 互补**：单 epoch SFT 工具对齐后 FDP 达 45.8%；第二个 epoch 在 FDP 升至 65.3% 但 FODP 跌至 28.6%（过拟合）；GSPO 在保持工具调用能力的同时恢复开词汇鲁棒性（FODP 33.9%），并在 SUL 大幅跃升。
4. **社交奖励驱动主动意图对齐**：通过 `ask` 的奖励设计，模型学会在歧义下暂停并查询用户，而非被动执行模板。
5. **冻结视觉编码器带来视觉瓶颈**：FDO（关节操作）成功率仍较低，反映基础模型视觉接地能力的局限。
6. **结构化记忆抑制长程幻觉**：真实部署中，模型能正确执行因果序列（先开微波→再去取面包→放入→关门），证明自总结状态机制有效。

---

## 7. 优点与亮点

- **去除神谕感知**是核心创新：传统基准假设全局物体清单或瞬移定位，REAL 强制使用 RGB 探索，使仿真到真实接口完全一致。
- **集成模拟用户闭环**：不只生成问题或记忆习惯，而是把多轮对话嵌入到主动探索→消歧→操作的正循环，更贴近真实人机协作。
- **聚合历史而非拼接**：自总结的 $(\Sigma_t, task_t)$ 结构缓解上下文爆炸与时间幻觉，对长程任务尤为关键。
- **GSPO 选择理由清晰**：明确指出 GRPO 的步级比率方差问题，给出 $1/L^2$ 压缩的工程化解释。
- **World Graph 驱动的稠密奖励**：基于状态差异而非稀疏完成信号，配合物理引擎的天然时序约束，奖励信号稳定且防 reward hacking。
- **MCP 标准接口**：高层 VLM 策略与底层物理后端解耦，仿真训练的策略可直接 zero-shot 部署到真实机器人。
- **真实部署验证**：少有论文同时给出仿真 benchmark 与 60 回合真实机器人结果，且报告了 SPL、查询次数、VLM 延迟等多元指标。

---

## 8. 不足与局限

- **任务空间局限**：聚焦"跨容器对象重排"，未涵盖时间有序子任务、空间关系目标（如"放在盘子左边"）等更复杂的组合约束。
- **模拟用户行为受限**：用户偏好被约束于场景内物体、回复锚定智能体轨迹；真实用户可能在任务中途提出新目标或通过隐式线索传达意图。
- **容器建模粗糙**：容器被建模为单体（如 cabinet_1），缺乏部件级区分（单个搁板），限制探索与操作的精度。
- **视觉编码器冻结导致关节操作瓶颈**：FDO 成功率相对较低，需进一步扩展多模态能力。
- **算力与训练成本未披露**：GPU 型号、数量、训练时长、模拟用户调用成本等关键信息缺失，限制复现性评估。
- **评估偏差风险**：
  - 模拟用户由 Gemini 3 Flash 驱动，可能存在偏好偏差或风格偏差；
  - 真实部署 60 个回合虽有意义，但样本量仍较小，未给出置信区间；
  - 训练数据来自规则规划器，可能无法覆盖非典型的探索失败模式。
- **未深入分析 RL 训练稳定性**：GSPO 替换 GRPO 的实证收益仅在 SUL 上明显，其他任务上 RL 相对 SFT 提升有限，需更细致的训练曲线与消融。

（完）
