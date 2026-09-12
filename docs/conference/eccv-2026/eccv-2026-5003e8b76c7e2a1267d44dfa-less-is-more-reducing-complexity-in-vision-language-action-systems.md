---
title: "Less is More: Reducing Complexity in Vision-Language-Action Systems"
title_zh: 少即是多：简化视觉-语言-动作系统的复杂度
authors: "Jinhui Ye, Ning Gao, Senqiao Yang, Jinliang Zheng, Zixuan Wang, Yuxin Chen, Pengguang Chen, Yilun Chen, Shu Liu, Jiaya Jia"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/1087.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 通用视觉-语言-动作模型在多基准机器人任务上的系统评估
tldr: 针对视觉-语言-动作模型领域架构与流程日益复杂的问题，本文提出简洁而强大的基线StarVLA-α。该方法在统一的多基准上系统评估动作建模、机器人预训练与接口工程等关键设计选择，为通用机器人智能体研究提供了清晰的参照。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-001.webp\", \"caption\": \"\", \"page\": 5, \"index\": 1, \"width\": 560, \"height\": 327}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 560, \"height\": 297}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-003.webp\", \"caption\": \"\", \"page\": 5, \"index\": 3, \"width\": 560, \"height\": 274}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-004.webp\", \"caption\": \"\", \"page\": 5, \"index\": 4, \"width\": 700, \"height\": 1050}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-005.webp\", \"caption\": \"\", \"page\": 5, \"index\": 5, \"width\": 506, \"height\": 624}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-006.webp\", \"caption\": \"\", \"page\": 5, \"index\": 6, \"width\": 527, \"height\": 718}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-5003e8b76c7e2a1267d44dfa/fig-007.webp\", \"caption\": \"\", \"page\": 5, \"index\": 7, \"width\": 667, \"height\": 667}]"
motivation: 现有VLA模型架构与流程高度碎片化，难以系统分析各设计选择的影响。
method: 提出StarVLA-α基线，最小化架构复杂度以隔离变量并系统分析关键设计轴。
result: 在统一的多基准测试中展示了简洁设计的强劲性能。
conclusion: 简化设计有助于推动通用VLA模型的系统性研究与基准比较。
---

## Abstract
Vision-Language-Action (VLA) models have emerged as apromising paradigm for building general-purpose robotic agents. How-ever, the VLA landscape remains highly fragmented and complex: asexisting approaches vary substantially in architectures, training data,embodiment configurations, and benchmark-specific engineering. In thiswork, we introduce StarVLA-α, a simple yet strong baseline designedto study VLA design choices under controlled conditions. StarVLA-αdeliberately minimizes architectural and pipeline complexity to reduceexperimental confounders and enable systematic analysis. Specifically,we re-evaluate several key design axes, including action modeling strate-gies, robot-specific pretraining, and interface engineering. Across uni-fied multi-benchmark training on LIBERO, SimplerEnv, RoboTwin, andRoboCasa, the same simple baseline remains highly competitive, indi-cating that a strong VLM backbone combined with minimal design isalready sufficient to achieve strong performance without relying on ad-ditional architectural complexity or engineering tricks. Notably, our sin-gle generalist model outperforms π0.5 by 20% on the public real-worldRoboChallenge benchmark. We expect StarVLA-α to serve as a solidstarting point for future research in the VLA regime. Code will be re-leased at https://github.com/starVLA/starVLA.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "StarVLA-α: Reducing Complexity in Vision-Language-Action Systems" following a specific structure with 8 points. Let me analyze the paper carefully and produce a structured summary.

Let me go through each point:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and adequacy
6. Main conclusions
7. Strengths
8. Limitations

The paper is about VLA (Vision-Language-Action) models for robotics. It proposes StarVLA-α as a simple baseline to systematically study VLA design choices. Let me extract key information:

- Backbone: Qwen3-VL (specifically Qwen3-VL-4B mentioned)
- Action head: simple MLP for continuous action prediction
- Four action head designs compared: FAST (discrete), MLP (default), GR00T (dual-system), π (diffusion-style)
- Benchmarks: LIBERO, SimplerEnv, RoboTwin 2.0, RoboCasa-GR1
- Real-world: RoboChallenge benchmark on ARX5 robot
- Action padding: pad all action vectors to 32 dimensions
- Comparison with: OpenVLA-OFT, π0, π0+FAST, π0.5, GR00T-N1.6, FAST
- Robot pretraining comparison: OXE, InternData-A1, RoboTwin-Rand
- Data engineering ablations: Proprioception, History frames, Delta action, Relative action
- Model size study: 2B, 4B, 8B
- Batch size study: 64, 128, 256, 512, 1024
- Results: StarVLA-α achieves 98.8% on LIBERO avg, 76.0% on SimplerEnv Google VM, 53.8% on RoboCasa-GR1
- On RoboChallenge: 33.6% SR vs π0.5's 12.7% (outperforms by 20%)

Note about resources/compute: The paper doesn't explicitly mention GPU model, count, or training time. I should note this.

Let me write the summary in Chinese with markdown formatting.</think>

# StarVLA-α 论文总结

## 1. 核心问题与研究动机

- **领域背景**：Vision-Language-Action（VLA）模型是当前实现通用机器人智能体的热门范式，自 RT-1/RT-2 以来快速发展。
- **核心问题**：VLA 领域存在严重的"碎片化"困境：
  - 架构差异大（视觉塔、语言主干、动作专家各异）；
  - 训练数据与机器人本体（embodiment）配置不统一（单臂、双臂、人形机器人等）；
  - 动作空间与归一化方式互不兼容；
  - 评测实践不一致（benchmark 特定的超参调优、动作块策略、训练划分）。
- **研究意义**：这种异质性导致不同方法的性能增益难以归因——难以判断改进来自建模创新还是实验变差。与 VLM 领域已逐步形成标准化训练范式不同，VLA 领域急需建立方法论共识。
- **核心假设（minimal-sufficiency hypothesis）**：一个强 VLM 主干 + 轻量动作头，已足以获得主流 VLA 系统的性能，无需复杂架构与数据工程。

## 2. 方法论

### 2.1 整体框架：StarVLA-α 基线

- **极简数据处理**：
  - 仅使用原始 RGB 图像与语言指令作为输入，无 benchmark 特定工程；
  - 动作归一化基于训练集（zero mean, unit variance）；
  - 评测严格遵循各 benchmark 官方协议。
- **简洁架构**：
  - 主干采用 **Qwen3-VL**（开源、广泛使用、原生支持多模态，避免单独选择视觉编码器）；
  - 动作头为 **轻量 MLP**：读取指定 action token 的隐藏状态，回归一段连续动作块（action chunk）。
- **统一 Benchmark 集成**：
  - 通过 thin adapter 标准化观测格式、动作接口与评测入口；
  - 支持跨多种机器人本体（单臂、双臂、人形机器人）的统一训练与评测；
  - 通过简单 padding 将所有机器人的动作维度统一到 32 维，无需 per-task 工程。

### 2.2 四种动作头设计的对比（消融维度）

- **StarVLA-α-FAST**：离散动作预测（自回归 FAST tokenizer，类似 π0-FAST）；
- **StarVLA-α（默认）**：连续动作回归 + 轻量 MLP（类似 OpenVLA-OFT）；
- **StarVLA-α-GR00T**：双系统架构，VLM 作为 System 2，flow-matching 模块作为 System 1；
- **StarVLA-α-π**：基于 flow matching 的扩散式连续动作预测（类似 π0）。

### 2.3 三条再评估设计轴

1. **动作头架构是否必要**？—— 比较 FAST、MLP、GR00T、π 四种头部；
2. **动作相关预训练是否必要**？—— 比较 OXE、InternData-A1、RoboTwin-Rand 等大规模预训练数据的影响；
3. **数据工程是否必要**？—— 消融 Proprioception、History frames、Delta action、Relative action 等常见工程技巧。

### 2.4 算法流程（文字描述）

1. 输入：RGB 图像 + 自然语言指令；
2. 通过 Qwen3-VL 编码得到多模态隐藏状态；
3. 取出 action token 的隐藏向量；
4. 经 MLP 头回归连续动作块（连续控制信号）；
5. 训练目标：标准 MSE / flow-matching 损失（取决于动作头类型）。

## 3. 实验设计

### 3.1 数据集 / Benchmark

| Benchmark | 类型 | 评测内容 |
|---|---|---|
| **LIBERO** | 仿真 | Spatial / Object / Goal / Long 四类任务 |
| **SimplerEnv** | 仿真→真实迁移 | WidowX、Google Robot VA / VM（含 clean / random 设定） |
| **RoboTwin 2.0** | 仿真（双臂） | 24 子任务，clean/random 不同数据量 |
| **RoboCasa-GR1** | 仿真（人形机器人） | 24 子任务，演示数据规模 10/100/1000 |
| **RoboChallenge** | 真实机器人 (ARX5) | 11 个桌面操作任务（SR + 进度分数） |

### 3.2 对比方法

- **Specialist 设置下**：OpenVLA-OFT、π0、π0+FAST、π0.5、GR00T-N1.6、FAST；
- **Generalist 设置下**：π0.5、GR00T-N1.6、StarVLA-α-π、StarVLA-α-GR00T、StarVLA-α（默认）。

### 3.3 训练协议

- **Specialist**：每个 benchmark 数据集单独训练一个模型；
- **Generalist**：合并所有数据集联合训练一个模型，跨 benchmark 评估无需额外微调；
- 学习率 1e-4，batch size 256（默认，含 64/128/512/1024 消融）。

## 4. 资源与算力

- **论文未明确披露**：
  - 未给出 GPU 型号与数量；
  - 未给出训练总时长（epoch 数、wall-clock time）；
  - 仅说明使用了 2B / 4B / 8B 三档 Qwen3-VL 模型，batch size 256 为默认。
- 仅可推断：使用了 Qwen3-VL 系列（2B/4B/8B 参数规模）作为主干，训练规模较大（Generalist 设置下联合 5 个数据集、batch size 最大 1024），但具体硬件配置需参考代码仓库（https://github.com/starVLA/starVLA）。

## 5. 实验数量与充分性

- **动作头消融**：4 种头部 × 4 个 benchmark ≈ 16 组主对比；
- **预训练数据消融**：4 种预训练设置 × 2 个 benchmark × 多个数据规模 ≈ 多组对照；
- **数据工程消融**：4 种技巧（Proprioception、History、Delta、Relative）× 3 个 benchmark × 多种数据规模 ≈ 数十组细分实验；
- **Generalist vs Specialist**：1 种 generalist × 多 specialist × 多 benchmark；
- **扩展研究**：模型规模（2B/4B/8B）、batch size（5 档）、动作参数化（3 种策略）各一组扫描；
- **真实机器人实验**：RoboChallenge 11 个任务，与 π0.5、π0 对比。

**评价**：
- 实验覆盖较广，包含仿真、跨本体、跨任务以及真实机器人；
- 在统一设置下做变量隔离（控制 backbone、数据规模、训练协议）较为规范；
- 但部分 benchmark（如 SimplerEnv WidowX、RoboTwin random）不同方法之间差距较小，单次实验可能存在方差，论文未给出多次 seed 的均值/方差，仅给单点结果，存在一定统计偏差风险；
- 真实机器人部分仅展示 ARX5 一种本体，缺乏跨硬件的泛化证据。

## 6. 主要结论与发现

1. **强 VLM 主干 + 简单 MLP 动作头已足够强**：在 4 个 benchmark 上均达到 SOTA 或极具竞争力的性能（LIBERO 98.8%、SimplerEnv Google VM 76.0%、RoboCasa-GR1 53.8%）。
2. **连续动作预测显著优于离散（FAST）**，但不同连续动作头（MLP / GR00T / π）之间差异有限。
3. **大规模动作预训练并非总是有益**：跨域数据（如 OXE）反而会损害下游表现；领域匹配的数据（InternData-A1、RoboTwin-Rand）仅在低数据场景下带来提升。
4. **常见数据工程技巧收益有限**：在数据充足时，Proprioception、History frames、Delta/Relative action 等几乎无收益；仅在低数据场景下有小幅改善。
5. **Generalist 模型可跨任务跨本体泛化**：单个联合训练模型在大多数 benchmark 上仍能匹配或超过 specialist 模型，RoboCasa-GR1 上甚至提升 3.5%。
6. **模型规模与 batch size 至关重要**：2B → 4B 提升明显（WidowX +18.1%，RoboCasa +6.6%），但 4B → 8B 增益有限（<1%）；batch size 越大性能越好，512 已能取得强结果。
7. **真实机器人上显著超越基线**：在 RoboChallenge（ARX5）上，StarVLA-α 取得 33.6% SR / 54.5 进度分数，比 π0.5（12.7% / 27.6）高出约 20%。

## 7. 优点

- **方法论贡献突出**：将 VLA 领域设计选择置于受控实验下做"重新审视"，提供清晰的参照基线；
- **简洁实用**：单一主干 + MLP 头 + 简单 padding 即可在多 benchmark 上达到 SOTA，工程门槛低；
- **跨 benchmark 统一评测**：避免 benchmark 特定调优带来的虚假增益；
- **Generalist 实验设计有意义**：直接评估跨任务、跨本体泛化能力，符合通用智能体研究的目标；
- **真实机器人验证**：在公开真实 benchmark 上大幅超越现有强基线（π0.5），具有实际应用价值；
- **代码开源承诺**：提供完整代码仓库，便于复现与扩展。

## 8. 不足与局限

- **算力与训练成本未披露**：缺乏 GPU 型号、数量、训练时长、能耗等关键信息，难以评估实际部署代价；
- **真实机器人本体单一**：仅在 ARX5 上验证，泛化到其他真实硬件（如人形机器人）的可行性有待证明；
- **统计显著性不足**：大多数实验仅给出单点结果，未提供多次随机种子的均值与方差，部分小差距结论（如动作头之间）说服力受限；
- **预训练数据规模有限**：OXE 使用 232.6k 条轨迹、InternData-A1 使用 630k 条，与更大规模机器人预训练数据集相比规模较小，可能影响结论普适性；
- **未见失败案例分析**：对困难任务（如 RoboTwin random 数据下、Libero Long 任务）失败的根因缺乏深入讨论；
- **安全与伦理未涉及**：真实机器人实验未涉及安全性评估、应急停止机制等实际部署关键问题；
- **动作空间 padding 的局限性**：简单 padding 到 32 维可能引入冗余信息，对极高维动作空间的机器人本体（如多指灵巧手）可扩展性存疑；
- **评测基准偏差**：所选 benchmark 仍以仿真为主，SimplerEnv 虽含真实场景但任务相对简单，难以完全代表真实世界复杂性。

（完）
