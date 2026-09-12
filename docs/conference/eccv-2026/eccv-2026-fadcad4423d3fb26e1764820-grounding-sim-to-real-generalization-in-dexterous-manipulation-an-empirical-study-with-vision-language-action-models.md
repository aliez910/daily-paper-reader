---
title: "Grounding Sim-to-Real Generalization in Dexterous Manipulation: An Empirical Study with Vision-Language-Action Models"
title_zh: 扎根于灵巧操纵的仿真到现实泛化：基于视觉-语言-动作模型的实证研究
authors: "Ruixing Jin, ZiCheng Zhu, Ruixiang Ouyang, Sheng Xu, Bo Yue, Zhizheng Wu, Guiliang Liu"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/10355.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向灵巧操纵的通用VLA模型仿真到现实泛化经验研究
tldr: 通用机器人操纵策略通常依赖大规模数据，但真实数据采集成本高昂，仿真合成数据与真实分布存在显著差距：现有Sim-to-Real研究在通用VLA策略上的系统实证仍显不足。本文针对灵巧操纵任务，在通用视觉-语言-动作策略上系统考察Sim-to-Real泛化的关键决定因素，通过仿真数据训练并在真实世界灵巧操纵任务中评测，揭示影响迁移成败的核心因素，对大规模通用策略的仿真数据利用与真实部署具有重要指导意义。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 490, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 475, \"height\": 305}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 528, \"height\": 294}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 721, \"height\": 298}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-005.webp\", \"caption\": \"\", \"page\": 10, \"index\": 5, \"width\": 561, \"height\": 243}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-006.webp\", \"caption\": \"\", \"page\": 10, \"index\": 6, \"width\": 561, \"height\": 334}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-007.webp\", \"caption\": \"\", \"page\": 10, \"index\": 7, \"width\": 561, \"height\": 243}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-008.webp\", \"caption\": \"\", \"page\": 10, \"index\": 8, \"width\": 462, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-009.webp\", \"caption\": \"\", \"page\": 10, \"index\": 9, \"width\": 456, \"height\": 275}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-010.webp\", \"caption\": \"\", \"page\": 10, \"index\": 10, \"width\": 458, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-011.webp\", \"caption\": \"\", \"page\": 10, \"index\": 11, \"width\": 462, \"height\": 268}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-012.webp\", \"caption\": \"\", \"page\": 10, \"index\": 12, \"width\": 1536, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-013.webp\", \"caption\": \"\", \"page\": 14, \"index\": 13, \"width\": 1679, \"height\": 984}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-014.webp\", \"caption\": \"\", \"page\": 14, \"index\": 14, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-015.webp\", \"caption\": \"\", \"page\": 14, \"index\": 15, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-016.webp\", \"caption\": \"\", \"page\": 14, \"index\": 16, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-017.webp\", \"caption\": \"\", \"page\": 14, \"index\": 17, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-018.webp\", \"caption\": \"\", \"page\": 14, \"index\": 18, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-fadcad4423d3fb26e1764820/fig-019.webp\", \"caption\": \"\", \"page\": 14, \"index\": 19, \"width\": 640, \"height\": 480}]"
motivation: 仿真合成数据与真实数据分布差距大，通用VLA策略的Sim-to-Real实证不足。
method: 系统实验考察数据规模、域随机化等因素对灵巧操纵VLA策略Sim-to-Real迁移的影响。
result: 在真实世界灵巧操纵任务上识别出影响VLA泛化的关键决定因素。
conclusion: 为通用VLA策略在灵巧操纵中的仿真数据利用与真实部署提供实证依据。
---

## Abstract
Learning a generalist control policy for robotic manipula-tion typically relies on large-scale datasets. Given the high cost of real-world data collection, a practical alternative is to generate synthetic datathrough simulation. However, the resulting synthetic data often exhibitsa significant gap from real-world distributions. While many prior studieshave proposed algorithms to bridge the Sim-to-Real discrepancy, thereremains a lack of principled research that grounds these methods in real-world manipulation tasks, particularly their performance on generalistpolicies such as Vision-Language-Action (VLA) models. In this study,we empirically examine the primary determinants of Sim-to-Real gen-eralization across four dimensions: multi-level domain randomization,photorealistic rendering, physics-realistic modeling, and reinforcementlearning updates. To support this study, we design a comprehensive eval-uation protocol to quantify the real-world performance of manipulationtasks. The protocol accounts for key variations in background, light-ing, distractors, object types, and spatial features. Through experimentsinvolving over 10k real-world trials, we derive critical insights into Sim-to-Real transfer. To inform and advance future studies, we release boththe robotic platforms and the evaluation protocol for public access tofacilitate independent verification, thereby establishing a realistic andstandardized benchmark for robotic manipulation policies.

---

## 论文详细总结（自动生成）

<think>Let me carefully analyze this paper and provide a comprehensive Chinese summary following the specified structure.

The paper is titled "Grounding Sim-to-Real Generalization in Dexterous Manipulation: An Empirical Study with Vision-Language-Action Models" - though interestingly, the metadata says "Dexterous" but the actual paper text talks about bimanual manipulation tasks (Click Bell, Place Empty Cup, Beat Block Hammer, Stack Bowls Two, Place Dual Bottles) using a Cobot Magic platform (not really dexterous hand manipulation). I should note this discrepancy.

Let me organize the key points:

1. **Core problem/motivation**: 
- VLA models need large-scale data, but real-world data is expensive
- Synthetic data has Sim2Real gap
- Previous Sim2Real methods (DR, domain adaptation, rendering fidelity, RFT) evaluated independently on general tasks, not specifically grounded for VLA models in manipulation
- Lack of mechanistic understanding of which factors contribute to Sim2Real transferability

2. **Methodology**:
- Factorized empirical study of zero-shot Sim2Real for VLA models
- Four dimensions: multi-level DR, photorealistic rendering, physics-realistic modeling, RL updates
- Based on OpenVLA-OFT with Llama2 7B backbone
- SFT with L1 regression loss, RL with GRPO (DAPO-style, no KL penalty)
- Domain Randomization factors: BG, TD, CP, LT, TH (5 components)
- Randomization granularity: episode-wise vs frame-wise
- Rendering fidelity: Low/Medium/High photorealism + distorted physics

3. **Experimental design**:
- Simulator: RobotWin 2.0
- 5 tasks: Click Bell, Place Empty Cup, Beat Block Hammer, Stack Bowls Two, Place Dual Bottles
- 100 demonstrations per task
- Real robot: Piper platform with RealSense D435
- Evaluation factors: background, lighting, distractors (2/4/8), objects (seen/unseen), spatial (3x3 grid)

4. **Resources/compute**: Not explicitly mentioned in the paper - I should note this.

5. **Experiment count**: 
- Over 10,000 real-world trials
- Multiple tables (Table 1, 2, 3) showing factorized analysis
- Various combinations of DR factors

6. **Main findings**:
- Lesson 1: Spatial randomization (CP, TH) is primary driver
- Lesson 2: Appearance randomization complementary
- Lesson 3: Frame-wise granularity better than episode-wise
- Lesson 4: Higher fidelity helps but diminishing returns
- Lesson 5: RL enhances robustness to distribution shifts

7. **Strengths**:
- Massive real-world evaluation (10k+ trials)
- Factorized experimental design
- Public benchmark release
- Comprehensive protocol

8. **Limitations**:
- Single VLA model (OpenVLA-OFT)
- Single robot platform
- Limited task diversity (5 tasks)
- No compute details
- Tasks are relatively simple tabletop manipulation, not truly "dexterous"
- Metadata title says "Dexterous" but paper is about bimanual manipulation

Let me now write the summary in Chinese, well-structured.</think>

# 论文总结：基于 VLA 模型的灵巧 / 双臂操纵 Sim-to-Real 泛化实证研究

> 注：原文 PDF 实际标题为 "Grounding Sim-to-Real Generalization in Robotic Manipulation…"，元数据中的 "Dexterous Manipulation" 与正文（Click Bell、Place Empty Cup 等桌面级双手机器人任务，使用 Piper / Cobot Magic 平台）描述并不完全一致，下文按正文内容总结。

---

## 1. 核心问题与研究背景

- **数据稀缺与仿真替代的必要性**：训练通用的机器人操纵策略（尤其是 Vision-Language-Action, VLA 模型）通常需要大规模真实机器人轨迹数据，但真实数据采集成本高昂、硬件相关、难以扩展，仿真合成数据成为现实可行的替代方案。
- **Sim-to-Real 差距**：仿真与真实在动力学、运动学、传感器特性等方面存在显著差异，导致仿真训练的 VLA 在真实环境中性能明显下降。
- **现有方法的不足**：
  - 主流 Sim-to-Real 方法——域随机化 (DR)、域适应、视觉/物理保真渲染、强化学习微调 (RFT)——多在通用控制策略上评估，**缺乏针对 VLA 模型在真实操纵任务中的系统实证**；
  - DR 通常以"单块化"方式使用，难以解耦各因素的贡献；
  - 缺乏机制性的理解，使得 Sim-to-Real 策略无法被原则化地优化。
- **研究目标**：对**零样本 Sim-to-Real（仅仿真训练，直接部署至真实环境）**场景下 VLA 模型的迁移性进行**因子化（factorized）实证研究**，揭示决定迁移成败的关键因素。

---

## 2. 方法论

### 2.1 整体框架
- 基于 **RoboTwin 2.0** 仿真平台与 **OpenVLA-OFT**（Llama2 7B + 融合视觉编码器 + 并行动作分块解码 + L1 连续动作回归）作为统一基线策略。
- 在仿真中训练，零样本迁移至 Piper 真实机器人平台（Intel RealSense D435 RGB，640×480）。

### 2.2 训练目标

- **监督微调（SFT）**：L1 回归损失最小化预测动作块与示范动作的差
$$
\mathcal{L}_{\text{SFT}}(\theta)=\mathbb{E}_{(o_t,a_{t:t+M},l)\sim\mathcal{D}}\big[\|\pi_\theta(o_t,l)-a_{t:t+M}\|_1\big]
$$

- **强化学习微调（RL Fine-Tuning）**：采用 GRPO（类 SimpleVLA-RL），并使用 DAPO 式改进（**移除 KL 惩罚**），按组内相对优势优化
$$
\hat{A}_i=\frac{R_i-\text{mean}(\{R_j\})}{\text{std}(\{R_j\})},\quad r_{i,t}(\theta)=\frac{\pi_\theta(a_{i,t}|o_{i,t})}{\pi_{\theta_{\text{old}}}(a_{i,t}|o_{i,t})}
$$
仅使用"组内同时含成功与失败回合"的小组进行更新。

### 2.3 因子化分析维度

| 维度 | 因子 | 关键设置 |
|---|---|---|
| **域随机化 (DR)** | 背景 ξ_BG、桌面干扰物 ξ_TD、相机位姿 ξ_CP、光照 ξ_LT、桌面高度 ξ_TH | Episode-wise vs Frame-wise |
| **随机化粒度** | Episode-wise（每回合采样一次）/ Frame-wise（每步重采样） | TH、TD 维持 episode-wise 以保证任务可行 |
| **渲染保真度** | Low / Medium / High（光线追踪、采样率、路径深度、降噪） | 物理失真设置：极端重力、摩擦、恢复系数 |
| **RL 后训练** | SFT / SFT+RL / SFT+RL+DR | 三种配置对比 |

- **空间因子**（TH、CP）vs **外观因子**（BG、LT、TD）的对比是核心分析线索。

---

## 3. 实验设计

### 3.1 仿真与任务
- **仿真器**：RoboTwin 2.0，每个任务 100 条示范轨迹。
- **任务（5 项）**：Click Bell、Place Empty Cup、Beat Block Hammer、Stack Bowls Two、Place Dual Bottles。
- **仿真 OOD 评估**：在未见过的背景、桌面纹理、干扰物、桌面高度、相机位姿、光照下分别独立扰动。

### 3.2 真实环境评估协议
- **平台**：Piper 机械臂 + RealSense D435。
- **评测变量**：
  - 背景：木桌/蓝布/黄格 3 种桌面纹理
  - 光照：3 个光源位置 + 不同色温
  - 物体：见过/未见过的同类物体实例
  - 干扰物：2 / 4 / 8 个（来自独立物集）
  - 空间泛化：3×3 网格的未见位置
- **流程**：基准配置 → 单因子逐一扰动 → 多次小随机位移取平均成功率。

### 3.3 对比方法
- **基线**：Clean（无 DR）SFT
- **DR 配置**：BG / LT / TD / CP / TH 单因子、组合（TH+CP+BG/LT/TD）、All Factors
- **粒度对比**：Episode-wise vs Frame-wise（分别对 CP、BG、LT）
- **渲染对比**：Low / Medium / High 保真度 + 物理失真设置
- **训练范式对比**：SFT / SFT+RL / SFT+RL+DR

---

## 4. 资源与算力

- **论文未明确披露**：GPU 型号与数量、训练时长、显存占用等算力信息均**未在正文中给出**。
- 可推断：基线策略为 Llama2 7B 级别的 VLA，且涉及超过 1 万次真实世界 trial（机器人时间成本高），但缺乏官方算力声明是一处信息空白。

---

## 5. 实验数量与充分性

- **真实试验规模**：超过 **10,000 次真实机器人 trial**，是大规模 Sim2Real 实证研究中的较高量级。
- **实验组合**：
  - DR 表（Table 1）：5 任务 × 8 配置（Clean + 5 单因子 + 2 组合 + All）= 80 个数据点 × Sim-OOD/Real 两列；
  - 粒度表（Table 2）：3 因子 × 2 粒度 × 5 任务 = 30 数据点 × Sim-OOD/Real；
  - 渲染保真度（图 3a）：3 级别 + 物理失真 × 5 任务；
  - RL 表（Table 3）：3 训练变体 × 5 任务 × Sim-OOD/Real = 30 数据点。
- **充分性评估**：
  - ✅ 因子化设计解耦了各因素贡献，结论可解释性强；
  - ✅ 同时报告 Sim-OOD 与真实结果，便于区分仿真内/外交迁移；
  - ⚠️ 仅使用单一基线策略（OpenVLA-OFT），未与其他 VLA（如 π0、OpenVLA、CogACT）对比；
  - ⚠️ 仅 5 个相对简单的桌面任务，任务多样性有限；
  - ⚠️ 任务成功率仍偏低（如 All Factors 下多数任务真实成功率仍在 50% 以下），说明即使采用全部技术，仍有较大提升空间。

---

## 6. 主要结论与发现（5 条经验法则）

1. **空间随机化是 Sim-to-Real 泛化的首要驱动**：相机位姿 (CP) 与桌面高度 (TH) 单独使用即可带来最大提升，**显著超过纯外观扰动**（BG、LT）。
2. **外观随机化提供互补增益**：在已有空间扰动基础上叠加 BG/LT/TD 可进一步提升，且 All Factors 组合普遍最佳。
3. **粒度至关重要（Frame-wise > Episode-wise）**：CP、BG 上 Frame-wise 相比 Episode-wise 在真实任务中提升约 **3–13%**；LT 提升较小（0–2%）。
4. **仿真保真度提升有助于迁移，但收益递减**：从 Low→Medium 提升明显，Medium→High 边际收益减小；物理保真度的增益小于视觉保真度。
5. **RL 显著增强分布偏移下的鲁棒性**：在 Clean 仿真中 SFT+RL 即可将真实平均成功率从 ~5.6% 提升至 **33.4%**；叠加 DR 后进一步提升至 **42.8%**（真实）与 70.8%（Sim-OOD）。

---

## 7. 优点

- **大规模真实评测**：10k+ 真实 trial，体量远超多数 Sim2Real 研究。
- **因子化、可解释的实验设计**：将 DR 拆解为 5 个独立因子 + 2 种粒度 + 3 级渲染保真度 + 3 种训练范式，能够定量归因。
- **公开基准与平台**：开放机器人硬件与协议，建立标准化的真实环境基准（受 RoboChallenge 启发），便于独立复现与持续评测。
- **方法论完整性**：覆盖了 DR、渲染、物理、RL 四大维度，是首个针对 VLA 模型的系统化 Sim2-Real 实证。
- **清晰的工程实现**：明确描述了 SFT（L1）、RL（GRPO+无 KL）、粒度策略限制（TD/TH 不做 frame-wise）等实现细节。

---

## 8. 不足与局限

- **任务覆盖有限**：仅 5 个桌面级双手机器人任务（无插孔、折叠、布料等细粒度灵巧操作），与元数据标题中的"Dexterous Manipulation"不完全吻合。
- **单一基线策略**：仅基于 OpenVLA-OFT，未验证结论在不同 VLA（π0、OpenVLA、CogACT、GR00T）上是否一致——结论的普适性受限。
- **任务难度仍偏高、成功率有限**：即使是"All Factors"配置，多数任务真实成功率仍 < 50%，说明单靠现有 Sim2Real 工具难以完全解决差距。
- **缺少算力/训练成本披露**：GPU 型号、数量、训练小时数等关键信息未给出，限制了对方法落地成本的评估。
- **统计显著性未充分讨论**：未见置信区间、误差棒或显著性检验，结果的稳定性/复现性需结合开放平台进一步验证。
- **零样本设定排除了域适应**：作者明确指出域适应方法不在本文范围，但与现实部署中常见的少量真实数据微调存在脱节。
- **物理保真度分析较粗**：仅给出"失真 vs 真实"的二分比较，未像视觉保真度那样做多级细化，难以精细归因。
- **任务设计偏向评估而非极限测试**：所有因子扰动都在合理范围内，未涉及极端环境（强遮挡、严重过曝、传感器噪声）等更具挑战的分布外情形。
- **视觉感知与运动执行的耦合度未深入分析**：尽管结论指出"空间 > 外观"，但缺少注意力可视化或特征层面的诊断证据来解释机制。

（完）
