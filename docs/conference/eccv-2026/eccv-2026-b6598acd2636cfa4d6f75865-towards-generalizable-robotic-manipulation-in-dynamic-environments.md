---
title: Towards Generalizable Robotic Manipulation in Dynamic Environments
title_zh: 面向动态环境的可泛化机器人操控：DOMINO基准
authors: "Heng Fang, Shangru Li, Shuhan Wang, Xuanyang Xi, Dingkang Liang, Xiang Bai"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/934.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 提出DOMINO基准并在动态操控任务上系统评测主流VLA模型
tldr: 针对VLA模型在静态操控表现优异但在动态环境中表现欠佳的问题，本文指出主要原因在于动态操控数据集稀缺以及主流VLA依赖单帧观测、时空推理能力不足。为此，作者提出了DOMINO大规模基准，包含35个具有层次复杂度的动态操控任务、超过11万条专家轨迹以及多维评测套件。系统实验对现有VLA进行了全面评测，并探索了提升动态感知能力的训练策略。该工作为通用视觉-动作模型在复杂动态操控任务上的评测提供了重要基础设施。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-b6598acd2636cfa4d6f75865/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 515, \"height\": 357}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-b6598acd2636cfa4d6f75865/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 516, \"height\": 356}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-b6598acd2636cfa4d6f75865/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 499, \"height\": 340}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-b6598acd2636cfa4d6f75865/fig-004.webp\", \"caption\": \"\", \"page\": 13, \"index\": 4, \"width\": 1448, \"height\": 1086}]"
motivation: 现有VLA模型在动态操控任务中泛化能力差，缺少大规模动态数据集与系统评测基准。
method: 构建DOMINO大规模数据集与基准，提出多维评测套件，并探索动态感知的训练策略。
result: 在35个动态任务上系统评测了现有VLA模型，验证了所提策略对动态泛化能力的提升。
conclusion: DOMINO为动态环境下的通用机器人操控提供了数据集、评测协议与训练洞察。
---

## Abstract
Vision-Language-Action (VLA) models excel in static manipulation but struggle in dynamic environments with moving targets. This performance gap primarily stems from a scarcity of dynamic manipulation datasets and the reliance of mainstream VLAs on single-frame observations, restricting their spatiotemporal reasoning capabilities. To address this, we introduce DOMINO, a large-scale dataset and benchmark for generalizable dynamic manipulation, featuring 35 tasks with hierarchical complexities, over 110K expert trajectories, and a multidimensional evaluation suite. Through comprehensive experiments, we systematically evaluate existing VLAs on dynamic tasks, explore effective training strategies for dynamic awareness, and validate the generalizability of dynamic data. Furthermore, we propose PUMA, a dynamicsaware VLA architecture. By integrating scene-centric historical optical flow and specialized world queries to implicitly forecast object-centric future states, PUMA couples history-aware perception with short-horizon prediction. Results demonstrate that PUMA achieves state-of-the-art performance, yielding a 6.3% absolute improvement in success rate over baselines. Moreover, we show that training on dynamic data fosters robust spatiotemporal representations that transfer to static tasks.

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize a paper in Chinese, using Markdown format, following a specific structure. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is "Towards Generalizable Robotic Manipulation in Dynamic Environments" which introduces DOMINO benchmark and PUMA architecture.

Let me organize the summary according to the 8 requested points.</think>

# 论文总结：面向动态环境的可泛化机器人操控（DOMINO & PUMA）

## 1. 核心问题与研究动机

- **背景**：当前 Vision-Language-Action (VLA) 模型（如 OpenVLA、π0、RDT 等）在**静态操控**任务上已取得显著进展，但在**动态环境**（运动目标、突发扰动）下性能急剧下降。
- **两大瓶颈**：
  - **动态操控数据集稀缺**：动态环境对时空同步性要求极高，专家示教难以实时反应，导致现有具身数据集几乎全部局限于静止任务。
  - **主流 VLA 架构缺乏时空推理能力**：依赖**单帧观测**，无历史上下文、无未来预测，难以捕捉物体运动趋势。
- **研究目标**：构建一个支持**可泛化动态操控**的大规模基准与训练协议，并提出具备动态感知能力的 VLA 架构。

---

## 2. 方法论

### 2.1 DOMINO 数据集与基准

- **任务设计**：
  - 35 个动态操控任务，覆盖 5 种机器人本体（Aloha-AgileX、ARX-X5、Franka、Piper、UR5-Wsg）。
  - 双臂操作为主，任务分为 **Dynamic Interception（拦截）** 与 **Dynamic Tracking（跟踪）** 两大类。
- **难度分级**（由动力学系数 α 参数化最大速度）：
  - **Level 1**：恒速（低阶可预测）。
  - **Level 2**：多项式轨迹（高阶可预测，曲率可变）。
  - **Level 3**：分段随机运动（速度/加速度不连续，突发扰动）。
- **数据规模**：>11 万条专家轨迹，含规范与域随机化设置。
- **三阶段时空同步数据生成**：时序预演 → 运动学反推 → 同步动态执行。
- **评测指标**：除 Success Rate (SR) 外，引入 **Manipulation Score (MS)**——基于 Route Completion × 安全惩罚因子，对执行质量进行连续量化。

### 2.2 PUMA 架构（Predictive Unified Manipulation Architecture）

- **基础**：基于 Qwen3-VL 视觉-语言模型。
- **两大核心模块**：
  1. **场景中心时空动力学编码**：
     - 以固定步长采样 h 帧历史第三人称视角图像，**空间压缩后计算光流图**（而非堆叠原始帧），送入视觉编码器。显式提供稠密运动线索。
  2. **物体中心动态表示**：
     - 训练时采样 N 帧未来帧，用 **GroundingDINO + SAM2** 分割目标物体。
     - 提取 DINO patch-token 特征，经掩码平均池化得到物体级未来特征 $f_{t+i}$。
     - 引入 N 个可学习的 **World Queries**，在潜空间中预测未来表示 $\hat{z}_{t+i}$，通过余弦相似度损失对齐 ground-truth 特征。
- **推理时**：未来预测分支不参与，**无额外开销**。
- **损失函数**：
  - 动作损失：$\mathcal{L}_{action} = \frac{1}{K}\sum_i \|\hat{a}_{t+i} - a^*_{t+i}\|_1$
  - 世界损失：$\mathcal{L}_{world} = \frac{1}{N}\sum_i\left(1 - \frac{\hat{z}_{t+i}^\top f_{t+i}}{\|\hat{z}_{t+i}\|\|f_{t+i}\|}\right)$
  - 总目标：$\mathcal{L}_{total} = \mathcal{L}_{action} + \lambda \mathcal{L}_{world}$
- **动作输出**：单次前向预测长度为 K 的 action chunk。

---

## 3. 实验设计

- **基准**：
  - 主要在 DOMINO@0.1（Level 1，α=0.1 m/s，clean setting，Aloha-AgileX）评估。
  - 静态对比实验使用 RoboTwin 2.0。
- **对比方法**：ACT、OpenVLA、OpenVLA-OFT、RDT-1B、π0、π0.5、π0-FAST、VLA-Adapter、InternVLA-M1、Qwen3-VL-based VLA（含公平复现）。
- **实验维度**：
  - 静态 vs. 动态性能对比（Tab. 1）。
  - 难度等级 Level 1-3 退化曲线（Fig. 4）。
  - 任务类型（DI/DT）细分（Tab. 4）。
  - 跨等级泛化（Level 1→2/3，Tab. 5）。
  - 静态-动态混合训练效果（Tab. 6）。
  - 真实机器人迁移（5 个任务，AgileX Piper 双臂，Tab. Fig. 6）。
  - 推理延迟（Tab. 7，RTX 4090）。
  - 消融实验（光流 vs. 原始帧、预测步长 N，Tab. 8）。
  - Oracle 实验（注入真实未来轨迹，Tab. 2）。

---

## 4. 资源与算力

- **训练**：NVIDIA A100 GPU。
- **数据生成与评测**：NVIDIA RTX 系列 GPU。
- **延迟基准**：单卡 RTX 4090，batch size=1，bf16，50 次预热后平均 500 次查询。
- **真实机器人**：AgileX Piper 6-DoF 双臂，配备 D435 RGB-D 相机，每任务 50 条遥操作示教。
- **未明确说明**：训练时长、模型参数量、数据集构建总工时、A100 的具体卡数。

---

## 5. 实验数量与充分性

- **实验规模**：
  - 主实验覆盖 35 个任务 × 3 种动态等级 × 5 种机器人本体 × 多模型对比。
  - 静态-动态零样本迁移、混合训练、跨等级 LoRA 适配、真实机器人验证、消融与延迟分析，**实验维度较为全面**。
- **公平性**：
  - 所有 VLA 模型均在 DOMINO 上微调（除 ACT 按任务微调）。
  - 部分基线（如 OpenVLA-OFT、π0.5、Qwen3-VL-based）使用相同 Qwen3-VL backbone 重实现以保证可比性。
- **局限性**：
  - 主实验仅在 Level 1 + Aloha-AgileX 平台进行（受算力限制），跨等级实验仅用 10 任务子集。
  - 真实机器人实验仅 5 个任务、每任务 20 次试验，统计可信度有限。
  - Level 3（最复杂）整体性能仍很低（SR < 5%），暴露当前方法在高度随机场景下的能力天花板。

---

## 6. 主要结论与发现

- **Finding 1**：动态操控是 VLA 的新前沿。从静态到动态，性能断崖式下降（如 π0.5 从 44.8%→7.5% SR），不可仅靠扩展静态方法解决。
- **Finding 2**：单纯注入未来轨迹不够。缺乏历史上下文时模型过拟合于轨迹跟踪，导致控制抖动；必须**历史 + 未来联合建模**。
- **Finding 3**：动态数据促进可泛化表示。在动态数据上训练的策略可零样本迁移到静态场景；与静态数据共训练可同时提升两种设置下的表现（静态结构先验 + 动态反应灵活性）。
- **SOTA 结果**：PUMA 在 DOMINO@0.1 上取得 17.20% SR / 34.97 MS，较最强基线（OpenVLA-OFT Qwen3-VL 版 10.86% SR）**绝对提升 6.3% SR**；真实机器人上平均 42% SR，远超 π0.5 (24%)。
- **消融结论**：光流 > 原始历史帧；预测步长 N=4 优于 N=2；光流与未来预测模块均带来稳定增益。

---

## 7. 优点与亮点

- **基准贡献突出**：首次系统定义动态操控的难度分级与多维评测指标（SR + MS），填补领域空白。
- **数据生成 pipeline 设计精巧**：三阶段时空同步方法解决了动态场景下专家示教的同步难题，具备可扩展性。
- **架构设计简洁高效**：用光流替代原始帧堆叠降低计算负担；未来预测仅在训练时启用，**推理零额外开销**。
- **实验维度丰富**：涵盖静态/动态迁移、跨等级、真实机器人、消融、延迟，论证较完整。
- **公平性考虑**：对部分基线统一 backbone 重实现，控制变量。
- **真实世界验证**：证实仿真训练的动态感知能力可通过 LoRA 轻量化迁移到真实平台。

---

## 8. 不足与局限

- **数据集-评测覆盖偏窄**：主实验仅 Level 1 + 单机器人本体；Level 2/3 评估局限于 10 任务子集与单一模型。
- **Level 3 性能仍极低**：最复杂的随机扰动场景下 PUMA 仅 4.6% SR，远未达到实用水平。
- **真实机器人实验样本量不足**：每任务 20 次试验，统计显著性较弱；任务数量仅 5 个。
- **算力与训练细节缺失**：未给出训练时长、A100 卡数、参数规模等关键信息，复现难度较大。
- **PUMA 依赖 Qwen3-VL**：98 ms 延迟中 backbone 占 94.7%，控制频率仅 ~10 Hz，对高速动态操控可能不足。
- **Orcale 实验仅提升 MS 而非 SR**：暗示当前架构在"轨迹跟踪"与"实际操控"之间存在表征冲突，问题未被彻底解决。
- **未涉及长时序任务**：光流仅覆盖 h 帧短期历史，对长时域动态场景的可扩展性未验证。
- **潜在偏差**：主实验在 clean setting（无域随机化）下进行，泛化至真实噪声环境的鲁棒性证据有限。

（完）
