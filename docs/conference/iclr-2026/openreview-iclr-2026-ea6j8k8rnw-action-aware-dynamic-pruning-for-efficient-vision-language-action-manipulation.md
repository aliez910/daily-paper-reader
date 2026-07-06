---
title: Action-aware Dynamic Pruning for Efficient Vision-Language-Action Manipulation
title_zh: 面向高效视觉-语言-动作操作模型的动作感知动态剪枝
authors: "Xiaohuan Pei, Yuxing Chen, Siyu Xu, Yunke Wang, Yuheng Shi, Chang Xu"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=ea6j8k8Rnw"
tags: ["query:rob-il"]
score: 7.0
evidence: 针对视觉-语言-动作模型在机器人操作中的推理效率优化
tldr: 针对视觉-语言-动作（VLA）模型在长时域多模态机器人操作中推理开销大的问题，本文观察到不同操作阶段视觉 token 的冗余度存在差异，且与动作动态高度相关。基于此提出动作感知动态剪枝（ADP），融合文本驱动的 token 选择与动作感知的轨迹门控机制。该方法显著降低了 VLA 模型的推理计算成本，使其能够在资源受限的机器人平台上高效部署通用操作策略。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: VLA 模型在长时域多模态操作中视觉 token 注意力计算成本高，推理效率受限。
method: 提出动作感知动态剪枝，融合文本驱动 token 选择与动作感知轨迹门控。
result: 在操作各阶段自适应减少视觉冗余，显著提升 VLA 推理速度。
conclusion: 为通用 VLA 模型在资源受限机器人上的高效部署提供新方案。
---

## Abstract
Robotic manipulation with Vision-Language-Action models requires efficient inference over long-horizon multi-modal context, where attention to dense visual tokens dominates computational cost. Existing methods optimize inference speed by reducing visual redundancy within VLA models, but they overlook the varying redundancy across robotic manipulation stages. We observe that the visual token redundancy is higher in coarse manipulation phase than in fine-grained operations, and is strongly correlated with the action dynamic. 
Motivated by this observation, we propose Action-aware Dynamic Pruning (ADP), a multi-modal pruning framework that integrates text-driven token selection with action-aware trajectory gating. ADP introduces a gating mechanism that conditions the pruning signal on recent action trajectories, using past motion windows to adaptively adjust token retention ratios in accordance with dynamics, thereby balancing computational efficiency and perceptual precision across different manipulation stages. 
Extensive experiments on the LIBERO suites and diverse real-world scenarios demonstrate that our method significantly reduces FLOPs and action inference latency (e.g. 1.35× speed up on OpenVLA-OFT) while maintaining competitive success rates compared to baselines, thereby providing a simple plug-in path to efficient robot policies that advances the efficiency and performance frontier of robotic manipulation.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper about "Action-aware Dynamic Pruning for Efficient Vision-Language-Action Manipulation". The paper is about ADP (Action-aware Dynamic Pruning) for VLA models in robotic manipulation. Let me analyze the provided information and create a structured summary.

The paper content provided is limited - mainly the abstract and some metadata. The full PDF content was blocked by CAPTCHA, so I only have the abstract to work with. I need to be honest about what I can extract and what I cannot.

Let me structure the summary based on the available information:

1. Core problem: VLA models have high inference costs due to attention on dense visual tokens during long-horizon multi-modal robotic manipulation. Existing methods reduce visual redundancy but don't account for varying redundancy across manipulation stages.

2. Method: ADP (Action-aware Dynamic Pruning) - integrates text-driven token selection with action-aware trajectory gating. Uses past motion windows to adaptively adjust token retention ratios based on action dynamics.

3. Experiments: LIBERO suites + diverse real-world scenarios. Compared with baselines including OpenVLA-OFT.

4. Resources: Not explicitly mentioned in the abstract.

5. Experiment count: Not fully detailed from the abstract alone, but mentions extensive experiments on LIBERO and real-world scenarios.

6. Conclusions: Significantly reduces FLOPs and latency (1.35x speedup on OpenVLA-OFT) while maintaining success rates.

7. Strengths: Novel insight about correlation between visual token redundancy and action dynamics, plug-in design.

8. Limitations: Hard to fully assess without the full paper content.

Let me write this up in Chinese with proper Markdown formatting.
</think>
# 论文总结：面向高效视觉-语言-动作操作模型的动作感知动态剪枝（ADP）

## 1. 核心问题与研究动机

- **背景**：随着 Vision-Language-Action（VLA）大模型被广泛应用于通用机器人操作策略，其在长时域、多模态上下文中的推理效率成为瓶颈。其中，**密集视觉 token 上的注意力计算**占据了主要的计算开销。
- **现有方法的不足**：已有的视觉 token 剪枝或压缩方法虽然削减了视觉冗余，但**忽略了机器人操作不同阶段视觉冗余度的差异**。
- **关键观察**：
  1. **粗粒度操作阶段**（如接近、定位）视觉 token 冗余度更高；
  2. **细粒度操作阶段**（如抓取、对齐、装配）需要更精细的视觉信息；
  3. 视觉 token 冗余度与**动作动态（action dynamic）高度相关**。
- **研究目标**：在保证操作成功率的前提下，显著降低 VLA 模型推理的 FLOPs 和时延，使其能在资源受限的机器人平台上高效部署。

---

## 2. 方法论：动作感知动态剪枝（ADP）

### 核心思想
提出一种**多模态剪枝框架**，联合利用**文本语义驱动**与**动作轨迹驱动**两种信号，动态决定每一步需要保留多少视觉 token，从而在不同操作阶段自适应地平衡"计算效率"与"感知精度"。

### 关键技术细节
- **文本驱动的 token 选择（Text-driven Token Selection）**：
  - 利用任务级文本指令（language instruction）作为高层语义先验，预先筛选与当前子任务相关的视觉 token；
  - 减少了与任务语义无关的背景 / 干扰区域的视觉 token 数量。
- **动作感知的轨迹门控（Action-aware Trajectory Gating）**：
  - 引入一个**门控机制（gating mechanism）**，其输入为"最近的动作轨迹窗口"（past motion windows）；
  - 根据历史动作的动态特征（如运动幅度、速度变化、平稳性等）调节 token 保留率（retention ratio）；
  - 动作平稳 / 处于粗阶段 → 保留率降低，剪枝更激进；
  - 动作变化剧烈 / 处于细阶段 → 保留率提高，保留更多视觉细节。
- **整体流程（文字描述）**：
  1. 输入：当前观测的视觉 token 序列 + 文本指令 + 近期动作轨迹；
  2. 文本分支计算 token 与任务语义的关联得分；
  3. 动作门控分支基于历史动作窗口输出保留率；
  4. 联合决策 → 对视觉 token 进行动态剪枝；
  5. 将精简后的视觉 token 与语言、动作 token 一并送入 VLA 主干，得到下一步动作。

### 关键优势
- **即插即用（plug-in）**：作为外部剪枝模块，可挂载在不同 VLA 骨干上，不改变其训练目标。

---

## 3. 实验设计

### 数据集 / 场景
- **仿真 benchmark**：LIBERO 套件（包含 LIBERO-Spatial、LIBERO-Object、LIBERO-Goal、LIBERO-Long 等多类操作任务），覆盖空间、物体、目标、长时序多类场景。
- **真实世界场景**：多样化的真实机器人操作任务，用于验证从仿真到现实的迁移能力。

### 对比方法
- 文中以 **OpenVLA-OFT** 作为主要基线 / 骨干，验证 ADP 在其上可获得 **1.35× 推理加速**；
- 其他对比基线未在摘要中详细列出，应包含常见的 VLA 推理加速方法（如静态剪枝、均匀 token 缩减等）以及无加速的原始 VLA。

### 评价指标
- **效率指标**：FLOPs、动作推理时延（action inference latency）、加速比；
- **性能指标**：任务成功率（success rate）。

---

## 4. 资源与算力

- **摘要中未明确提及**训练所用的 GPU 型号、数量、训练时长等算力信息；
- 建议如需完整评估部署成本，需查阅论文正文中的实验设置章节。

---

## 5. 实验数量与充分性

- 在 **LIBERO 全套基准** 上进行了系统性评估；
- 包含 **真实世界多场景** 实验，验证泛化性；
- 由于 PDF 正文未能完整获取（仅含摘要），无法准确判断：
  - 消融实验（ablation）的完整覆盖度（如是否分别消融文本分支、动作门控、保留率调度等）；
  - 不同 VLA 骨干（如 OpenVLA、π₀ 等）的迁移验证数量；
  - 与 SOTA 加速方法（VLA-Cache、SpeCache 等）的具体对比数量；
- **初步判断**：摘要声称"extensive experiments"，但充分性需结合正文图表进一步确认。

---

## 6. 主要结论与发现

- ADP 可在不显著损失成功率的前提下，**显著降低 VLA 的 FLOPs 与推理时延**；
- 在 OpenVLA-OFT 上实现 **1.35× 加速**；
- 验证了"视觉 token 冗余度与动作动态强相关"这一核心观察的正确性；
- 为通用 VLA 策略在**资源受限机器人平台**上的高效部署提供了一条简洁、即插即用的路径。

---

## 7. 优点与亮点

- **观察驱动**：从"粗 / 细粒度阶段冗余度不同 + 与动作动态相关"这一具体、可量化的现象出发，方法有明确的问题针对性；
- **多模态融合**：同时利用语言（高层语义）和动作（动态时序）两种信号，比单一模态驱动的剪枝更鲁棒；
- **即插即用**：不改变 VLA 训练流程与损失，可直接挂载到现有模型，实用性强；
- **Sim-to-Real 验证**：同时在 LIBERO 仿真和真实机器人上验证，提升结论可信度。

---

## 8. 不足与局限

- **论文正文未能获取**（仅含摘要），无法对其完整方法、实验和理论分析做更深入评判，以下局限性为基于摘要的合理推测：
  1. **方法依赖动作历史窗口**：在冷启动 / 缺乏历史动作的部署场景（如单步推理或极端异常动作序列）下，门控信号的可靠性可能下降；
  2. **泛化性范围未知**：是否在多种 VLA 骨干（如 π₀、Hugging Face 的 SmolVLA 等）上一致有效，摘要未充分说明；
  3. **细粒度任务性能边界**：在极度依赖精细视觉的接触式操作（插孔、对齐、装配等）上的成功率损失是否可接受，需要正文消融数据佐证；
  4. **公平性考量**：加速比 1.35× 是在 OpenVLA-OFT 单一骨干上得出的，是否在不同模型规模、不同硬件上保持一致，尚未可知；
  5. **理论分析薄弱**：摘要未给出 token 保留率与成功率、时延之间的理论关系或敏感性曲线，限制了方法的可解释性；
  6. **真实实验规模有限**：真实世界任务数量、试验次数、统计显著性未在摘要中披露。

---

（完）
