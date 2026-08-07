---
title: "GEVRM: Goal-Expressive Video Generation Model For Robust Visual Manipulation"
title_zh: GEVRM：面向鲁棒视觉操纵的目标表达视频生成模型
authors: "Hongyin Zhang, Pengxiang Ding, Shangke Lyu, Ying Peng, Donglin Wang"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=hPWWXpCaJ7"
tags: ["query:rob-il"]
score: 9.0
evidence: 抗外部扰动的闭环视觉-语言-动作视觉操纵模型
tldr: 现有视觉-语言-动作模型在部署时易受外部扰动影响，导致动作不准和泛化性能下降。为此，论文提出GEVRM，一种引入目标表达视频生成模块作为内部模型的闭环VLA方法，将经典内模控制原理与生成式视频预测相结合，使策略能主动抵消扰动。在多种视觉操纵任务上的实验表明，该方法显著提升了外部扰动下的鲁棒性，为闭环视觉反馈的通用机器人策略提供了新的设计范式。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型在部署中无法应对不可避免的外部扰动，导致动作预测不准和泛化能力下降。
method: 基于内模控制原理，提出引入目标表达视频生成作为内部模型的闭环VLA框架GEVRM。
result: 在多种扰动条件下的视觉操纵任务中显著提升了鲁棒性与泛化能力。
conclusion: GEVRM将生成式预测引入闭环控制，为鲁棒的通用视觉-动作操纵策略提供了有效方案。
---

## Abstract
With the rapid development of embodied artificial intelligence, significant progress has been made in vision-language-action (VLA) models for general robot decision-making. However, the majority of existing VLAs fail to account for the inevitable external perturbations encountered during deployment. These perturbations introduce unforeseen state information to the VLA, resulting in inaccurate actions and consequently, a significant decline in generalization performance. The classic internal model control (IMC) principle demonstrates that a closed-loop system with an internal model that includes external input signals can accurately track the reference input and effectively offset the disturbance. We propose a novel closed-loop VLA method GEVRM that integrates the IMC principle to enhance the robustness of robot visual manipulation. The text-guided video generation model in GEVRM can generate highly expressive future visual planning goals. Simultaneously, we evaluate perturbations by simulating responses, which are called internal embeddings and optimized through prototype contrastive learning. This allows the model to implicitly infer and distinguish perturbations from the external environment. The proposed GEVRM achieves state-of-the-art performance on both standard and perturbed CALVIN benchmarks and shows significant improvements in realistic robot tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of a paper titled "GEVRM: Goal-Expressive Video Generation Model For Robust Visual Manipulation". The PDF content extraction failed (only CAPTCHA page shown), but the markdown metadata provides substantial information including the abstract. Let me structure a comprehensive summary based on the available information.

Key information from metadata:
- Title: GEVRM: Goal-Expressive Video Generation Model For Robust Visual Manipulation
- Authors: Hongyin Zhang, Pengxiang Ding, Shangke Lyu, Ying Peng, Donglin Wang
- Date: 2025-01-22
- Source: ICLR-2025-Accepted
- Score: 9.0
- Motivation: Existing VLA models fail to handle external perturbations during deployment
- Method: IMC principle + goal-expressive video generation as internal model
- Result: SOTA on CALVIN benchmarks (standard and perturbed), significant improvement in real robot tasks
- Tags: query:rob-il (robot imitation learning)

Let me write a structured summary following the user's requested outline. I should note that since the full PDF text wasn't accessible, some details (like specific equations, exact GPU numbers, etc.) cannot be verified and should be acknowledged.</think>

# GEVRM 论文总结

## 1. 核心问题与研究动机

- **研究背景**：随着具身人工智能（Embodied AI）的快速发展，视觉-语言-动作（Vision-Language-Action, VLA）模型在通用机器人决策中取得了显著进展，但绝大多数现有 VLA 模型在**部署时无法应对不可避免的外部扰动**（如光照变化、物体位移、视角偏差等）。
- **核心问题**：外部扰动会向 VLA 输入未预料的状态信息，导致动作预测不准，进而使**泛化性能大幅下降**，限制了模型在实际场景中的可靠应用。
- **理论启发**：论文引用经典控制理论中的**内模控制（Internal Model Control, IMC）原理**——若闭环系统中包含一个能反映外部输入信号的内部模型，则系统可准确跟踪参考输入并有效抵消扰动。

## 2. 方法论

### 2.1 核心思想
- 提出 **GEVRM（Goal-Expressive Video Generation Model）**：一种将**内模控制原理**与**生成式视频预测**相结合的**闭环 VLA 框架**。
- 关键设计：将**目标表达视频生成模块**作为系统的"内部模型"，使策略能够主动生成目标视觉规划，并据此抵消扰动影响。

### 2.2 关键技术细节
1. **文本引导的未来视觉目标生成**：GEVRM 中的文本引导视频生成模型能根据语言指令生成**高表达力的未来视觉规划目标（goal frames）**。
2. **扰动评估机制——内部嵌入（Internal Embeddings）**：
   - 通过模拟扰动响应得到内部嵌入向量；
   - 使用**原型对比学习（prototype contrastive learning）**进行优化；
   - 使模型能够**隐式推断并区分来自外部环境的扰动**，从而在闭环中补偿。
3. **闭环架构**：VLA 策略以生成的"目标视频/未来帧"为参考，结合当前观测中的内部嵌入，在动作预测过程中动态校正扰动。

> 注：由于原始 PDF 文本提取失败（仅获得 CAPTCHA 页面），具体的损失函数形式、网络结构细节、算法伪代码等无法在此处完整复述，以上内容基于摘要与元数据归纳。

## 3. 实验设计

- **基准测试**：
  - **CALVIN 基准**（包括标准设置与受扰动设置），这是机器人视觉操纵领域的常用 benchmark。
  - **真实机器人任务**（realistic robot tasks），用于验证 sim-to-real 表现。
- **对比方法**：摘要声明在 CALVIN 基准的**标准与扰动设置**上均取得 **state-of-the-art (SOTA)**，但具体对比的基线方法列表需参考正文表格。
- **评估维度**：
  - 标准任务下的性能；
  - 多种扰动条件下的鲁棒性；
  - 真实机器人任务中的部署效果。

> 注：具体的扰动类型（光照、遮挡、视角扰动等）、任务类别、成功率指标（success rate / task completion）等细节因 PDF 未能解析而无法给出。

## 4. 资源与算力

- 原文 PDF 未成功提取，**关于 GPU 型号、数量、训练时长、显存占用等算力信息无法确认**。
- 通常此类工作会涉及多卡 A100/V100 集群训练（尤其是视频生成模块），但本论文**未在摘要层披露具体算力**，需进一步查阅正文/附录。

## 5. 实验数量与充分性

- 摘要明确报告了在**两个维度**的实验：(1) CALVIN 标准与扰动基准；(2) 真实机器人任务。
- 鲁棒性实验涉及"多种扰动条件"，体现了一定的充分性。
- 是否包含完整的**消融实验**（如移除视频生成模块、移除内部嵌入、移除对比学习损失等）以及**多场景泛化测试**，需查阅正文与附录。
- 总体而言，从摘要层面看实验覆盖了仿真基准+真实机器人两类场景，对 VLA 类工作是较合理的；但**客观性评价需以完整论文实验为准**。

## 6. 主要结论与发现

- GEVRM 在 CALVIN 基准（标准与扰动设置）上达到 **SOTA** 性能。
- 在真实机器人任务中表现出**显著的性能提升**，验证了闭环 IMC 架构在真实部署中的有效性。
- 将**生成式视频预测引入闭环控制**为通用鲁棒视觉-动作操纵策略提供了新的设计范式。

## 7. 优点

- **理论结合扎实**：将经典控制理论 IMC 原理与现代生成式模型结合，赋予工作清晰的理论动机与可解释性。
- **双重创新点**：(1) 文本引导视频生成作为内部模型；(2) 原型对比学习用于扰动识别，二者协同提升鲁棒性。
- **任务级贡献显著**：同时在标准基准、扰动基准与真实机器人上验证，覆盖面较广。
- **发表层级高**：被 **ICLR 2025 接收**，表明其方法与实验质量获得同行评审认可。
- **范式意义**：为"将生成式预测融入闭环控制"这一方向提供了示范，可启发后续研究。

## 8. 不足与局限

- **PDF 文本未能成功解析**，上述总结主要基于摘要与元数据，可能遗漏：网络细节、训练曲线、消融细节、失败案例等关键信息。
- **扰动类型的覆盖广度未知**：摘要仅笼统提及"外部扰动"，具体的扰动设置（视觉扰动 vs 物理扰动 vs 对抗扰动）及其难度等级需要正文确认。
- **真实机器人任务规模有限**：通常论文中的 real-world 实验任务数较少，**统计显著性**可能弱于仿真结果。
- **视频生成模块的算力开销**：未来帧生成通常计算昂贵，部署时的**推理时延与算力需求**是潜在应用瓶颈，论文未在摘要层讨论。
- **依赖大规模视频预训练**：生成式视频模型的性能通常依赖大规模预训练数据，可能引入**数据偏差与泛化风险**。
- **与主流 VLA（如 RT-2、OpenVLA 等）的对比深度**：需在正文中确认是否在统一协议下进行公平对比。
- **应用限制**：目前验证聚焦于桌面级视觉操纵任务，能否迁移到**移动操作、长时序任务、双臂协作**等更复杂场景尚待探索。

（完）
