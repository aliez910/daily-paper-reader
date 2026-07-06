---
title: "From Tokens to Actions: Discrete Flow Matching for Visuomotor Policy Learning"
title_zh: 从token到动作：面向视觉运动策略学习的离散流匹配
authors: "Kexin Shi, Shikhar Bahl, Deepak Pathak"
date: 2025-09-20
pdf: "https://openreview.net/pdf?id=Vg3K3ZEi8B"
tags: ["query:rob-il"]
score: 7.0
evidence: 将离散表征映射到连续动作的视觉运动策略学习
tldr: 物理世界中的连续动作在离散空间中表示可带来更稳定的优化与多模态行为建模能力。为此，本文提出离散流匹配策略DFMP，将连续机器人动作的学习置于离散动作token空间，使用基于评分的生成式建模与流匹配目标进行训练。DFMP在统一框架下同时实现了稳定优化、多模态行为建模与快速推理，系统性地弥合了连续控制与离散表征之间的鸿沟。该方法对复杂视觉运动策略具有重要应用价值。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 连续动作在策略学习中优化困难且难以表达多模态行为，需要新的表征与生成方法。
method: 提出DFMP，将动作建模为离散token间的连续时间马尔可夫链转移，结合流匹配目标进行生成。
result: 该方法在稳定性、多模态性与推理速度上同时取得优势，适用于连续控制。
conclusion: 离散流匹配为视觉运动策略学习提供了统一且高效的解决框架。
---

## Abstract
Although actions in the physical world are inherently continuous, representing them in a discrete space can unlock stability, efficiency, and multimodality in policy learning. We present Discrete Flow Matching Policy (DFMP), a novel method that learns continuous robot actions in a discrete space using score-based generative modeling. DFMP formulates action generation as a Continuous-Time Markov Chain, learning transition probabilities over action tokens. Through this, DFMP unifies three desirable properties: (i) stable optimization through flow-matching objectives, (ii) multimodal behavior modeling via probabilistic branching between tokens, and (iii) fast inference. To bridge continuous control with discrete representations, we systematically study tokenization schemes and analyze their trade-offs, proposing the optimal approach for real world robot policies. We thoroughly evaluate DFMP across many challenging simulated manipulation benchmarks and two real-world robot deployments, showing that our approach provides not only strong task performance, but also better scalability and robustness compared to existing continuous-space methods. These results position DFMP as a new, principled approach to efficient, robust, and multimodal visuomotor policy learning, advancing the integration of discrete generative modeling into real-world robotics. Videos and code are provided on the project page https://dfm-policy.github.io.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "From Tokens to Actions: Discrete Flow Matching for Visuomotor Policy Learning" (DFMP). I need to organize it according to 8 specific points in Markdown format. Let me analyze the provided content carefully.

The paper presents:
- DFMP: Discrete Flow Matching Policy
- Core idea: Learning continuous robot actions in discrete space using score-based generative modeling
- Formulates action generation as Continuous-Time Markov Chain (CTMC)
- Three properties: stable optimization via flow-matching, multimodal behavior modeling, fast inference
- Studies tokenization schemes for continuous control
- Evaluated on simulated manipulation benchmarks and two real-world robot deployments
- Compared against continuous-space methods
- Project page: https://dfm-policy.github.io

The PDF content I have is just the OpenReview CAPTCHA page, so I need to rely on the abstract and metadata provided. I should note that the PDF couldn't be fully extracted. Let me write the summary based on the available information (abstract + metadata) and clearly note the limitation regarding detailed experimental numbers, GPU specs, etc.

Let me structure the response:

1. 核心问题与整体含义
2. 方法论
3. 实验设计
4. 资源与算力
5. 实验数量与充分性
6. 主要结论与发现
7. 优点
8. 不足与局限

I should be honest that I only have the abstract and metadata, not the full paper. Let me write this carefully.
</think>
# 论文总结：DFMP（离散流匹配策略）

> **说明**：所提供的 PDF 链接实际仅返回了 OpenReview 的验证/CAPTCHA 页面，正文未成功提取。以下总结基于论文标题、官方元数据（标题、作者、日期、tag、tldr 等）以及所附的英文摘要进行整合。涉及具体实验数值、算力配置、详细消融等内容在原文未提供的情况下，将明确标注"未在摘要/元数据中给出"。

---

## 1. 核心问题与整体含义（研究动机与背景）

- **问题核心**：物理世界中的机器人动作是连续信号，但当前主流的视觉运动策略学习方法在连续空间中常面临**优化困难、训练不稳定以及难以表达多模态行为**等问题。
- **观察与动机**：尽管动作本身是连续的，但若在**离散 token 空间**中对其建模，可以借鉴离散生成模型（如离散扩散、离散流匹配）所具备的训练稳定性、采样效率与多模态分布表达能力。
- **目标**：在统一框架下，使策略学习同时获得（i）稳定的优化、（ii）多模态行为建模、（iii）快速推理，并弥合"连续控制"与"离散表征"之间的鸿沟，推动离散生成建模在真实机器人中的应用。

---

## 2. 方法论：核心思想、关键技术与算法流程

- **模型名称**：**Discrete Flow Matching Policy (DFMP)**，一种基于评分离散生成建模（score-based generative modeling）的视觉运动策略。
- **核心思想**：将连续机器人动作的学习**置于离散动作 token 空间**中，但通过**连续时间马尔可夫链（Continuous-Time Markov Chain, CTMC）** 来描述 token 之间的转移概率，从而把"离散表征"与"连续控制"统一起来。
- **关键技术**：
  - **离散流匹配目标（Flow-Matching Objective）**：替代传统连续扩散或回归损失，提供稳定、可扩展的训练信号。
  - **基于评分的生成建模（Score-based Generative Modeling）**：在 token 空间学习转移概率 / 评分函数，使策略具备采样式生成能力。
  - **token 间的概率分支（Probabilistic Branching）**：在 token 转移图上自然引入概率性分支，从而显式表达**多模态行为分布**（同一观测下可对应多种合理动作）。
  - **离散-连续桥接的 token 化方案**：系统研究动作 tokenization 方式（如何将连续动作编码为 token、解码回连续动作），并分析不同方案的权衡，提出面向真实机器人的最优 token 化方案。
- **算法流程（文字版）**：
  1. 将连续动作经 token 化（编码器）映射到离散动作 token 序列。
  2. 在 token 空间上定义 CTMC 转移过程，并用**流匹配损失**训练评分/转移模型。
  3. 推理时，从随机/先验 token 出发，按学习到的 CTMC 转移进行快速迭代采样，生成离散动作序列。
  4. 将生成的 token 经 detokenizer（解码器）映射回连续动作，送入机器人执行。

---

## 3. 实验设计：数据集、benchmark 与对比方法

- **仿真环境**："许多具有挑战性的仿真操控基准"（具体名称在摘要中未列出，未在摘要/元数据中给出）。
- **真实机器人实验**：在 **2 个真实机器人部署场景**上进行了评估（具体任务未在摘要/元数据中给出）。
- **对比方法**：摘要表述为"现有连续空间方法"（existing continuous-space methods），未在摘要/元数据中明确列出具体 baseline。
- **评价维度**：任务成功率、可扩展性（scalability）、鲁棒性（robustness），以及隐含的推理速度、多模态性。
- **附加资源**：项目页 https://dfm-policy.github.io 提供视频与代码。

---

## 4. 资源与算力

- **GPU 型号 / 数量 / 训练时长**：**未在摘要/元数据中给出**（PDF 正文未成功提取）。
- **代码与模型**：作者承诺开源代码与视频（项目页托管），但具体的训练算力成本、单次实验时间等数据**未在摘要/元数据中给出**。

---

## 5. 实验数量与充分性

- **实验规模**：
  - 仿真：覆盖"多个（many）具有挑战性的操控基准"。
  - 真实：2 个真实机器人部署。
  - 消融：摘要明确提到**对 token 化方案进行了系统性研究（systematically study tokenization schemes and analyze their trade-offs）**，可视为对离散-连续桥接的消融分析。
- **是否充分、客观、公平**：
  - 优点：同时覆盖仿真与真实机器人，且强调对 token 化方案的独立消融，兼顾方法有效性与设计选择的合理性。
  - 不足：摘要未具体说明基准数量、每个基准的随机种子数、统计显著性检验等，**充分性需以正文为准**；对比方法未明示，存在"挑选性比较"的潜在风险（无法从摘要判断）。

---

## 6. 主要结论与发现

- **总体结论**：DFMP 在统一框架下同时实现了稳定优化、多模态行为建模和快速推理，是一种面向视觉运动策略的**原则性新方法**。
- **关键发现**：
  - 在多个仿真操控基准上，DFMP 取得**强任务性能**。
  - 相较现有连续空间方法，DFMP 在**可扩展性（scalability）与鲁棒性（robustness）** 上更优。
  - token 化方案对最终策略性能有显著影响，恰当的 token 化设计是连接连续控制与离散表征的关键。
- **意义**：将离散生成建模进一步推向**真实机器人控制**领域，为高效、鲁棒、多模态的视觉运动策略学习提供了新范式。

---

## 7. 优点

- **统一性**：单一框架兼顾稳定优化 + 多模态 + 快速推理，避免了"补丁式"叠加。
- **离散-连续桥接**：通过 CTMC 形式化 token 间转移，理论路径清晰，既保留离散建模优势又服务于连续控制。
- **系统性 token 化研究**：对动作 token 化方案做专门分析，并给出面向真实机器人的最优选择，实践指导价值高。
- **仿真 + 真实双验证**：在 2 个真实机器人上做了部署验证，落地性强。
- **可复现性**：提供项目页、视频与开源代码。
- **应用价值**：对复杂视觉运动策略（如多模态行为、长时序操控）具有较高实用意义。

---

## 8. 不足与局限

- **PDF 提取失败**：本次仅能基于摘要与元数据进行总结，**实验细节、算力配置、完整消融表格、失败案例等关键信息缺失**。
- **真实部署规模有限**：仅 2 个真实机器人任务，对**长尾场景、扰动类型、硬件差异**的覆盖仍可能不足。
- **对比方法透明度不足**：摘要未列出具体 baseline，存在选择性比较的风险；也未提及与**其他离散策略方法**（如 BeT、DDT 等）的横向对比信息。
- **多模态评估不充分**：摘要仅称"多模态行为建模"为优势，但未给出**多模态量化指标**（如覆盖率、模式坍缩度量等）。
- **推理速度量化缺失**：宣称"快速推理"，但未给出**采样步数、延迟**等具体数据。
- **token 化方案的依赖性**：性能依赖于所选 token 化方式，迁移到**新动作空间或新形态机器人**时可能需要重新设计，存在**泛化与调参成本**。
- **评分模型在长 token 序列上的可扩展性**：CTMC 转移学习的复杂度与 token 序列长度相关，**未在摘要/元数据中给出**对长 horizon 任务的可扩展性证据。
- **数据效率 / 样本复杂度**：未在摘要/元数据中给出对训练样本量、demo 数量的对比，可能限制其在数据稀缺场景下的适用性。

（完）
