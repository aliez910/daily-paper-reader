---
title: Unified Vision-Language-Action Model
title_zh: 统一视觉-语言-动作模型
authors: "Yuqi Wang, Xinghang Li, Wenxuan Wang, Junbo Zhang, Yingyan Li, Yuntao Chen, Xinlong Wang, Zhaoxiang Zhang"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=PklMD8PwUy"
tags: ["query:rob-il"]
score: 9.0
evidence: 统一视觉-语言-动作模型，以离散token化实现通用操控
tldr: 现有VLA模型多依赖VLM的通用理解能力直接生成动作，忽略了视觉观测中蕴含的丰富时序与因果结构。本文提出UniVLA，将视觉、语言与动作统一为离散token序列进行自回归建模。其token化设计天然支持从大规模视频数据中灵活学习多模态任务，并证明生成式视觉监督可显著提升视觉理解能力。该工作为基于视频的通用机器人操控提供了新的VLA建模思路。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有VLA模型主要利用VLM理解能力生成动作，忽略了视觉观测中蕴含的丰富时序与因果结构。
method: 提出UniVLA，将视觉、语言与动作统一为离散token序列进行自回归生成式建模。
result: 证明生成式视觉监督可显著提升视觉理解能力，并支持从大规模视频中学习多模态操控任务。
conclusion: UniVLA为通用机器人操控提供了一种新的统一多模态VLA建模框架。
---

## Abstract
Vision-language-action models (VLAs) have garnered significant attention for their potential in advancing robotic manipulation.
However, previous approaches predominantly rely on the general comprehension capabilities of vision-language models (VLMs) to generate action signals, often overlooking the rich temporal and causal structure embedded in visual observations. In this paper, we present UniVLA, a unified and native multimodal VLA model that autoregressively models vision, language, and action signals as discrete token sequences. This tokenized formulation naturally supports flexible multimodal task learning, particularly from large-scale video data, and further demonstrates that generative vision supervision can significantly enhance visual understanding. By incorporating world modeling during post-training, UniVLA captures causal dynamics from videos, facilitating effective transfer to downstream policy learning—especially for long-horizon tasks. Our approach sets new state-of-the-art results across several widely used simulation benchmarks, including CALVIN, LIBERO, and Simplenv-Bridge, substantially outperforming prior methods. For example, UniVLA achieves 95.5% average success rate on LIBERO benchmark, surpassing π₀-FAST's 85.5%. We further demonstrate its broad applicability through experiments on real-world ALOHA manipulation tasks and autonomous driving scenarios.

---

## 论文详细总结（自动生成）

<think>
The user wants me to analyze a paper about "Unified Vision-Language-Action Model" (UniVLA) and provide a structured Chinese summary. Let me organize my response according to the 8 points requested.

The paper is from ICLR-2026-Accepted, and based on the metadata and abstract provided, I can extract the following information:

1. Core problem: Existing VLA models rely on VLM's general understanding to generate actions, ignoring rich temporal and causal structure in visual observations.

2. Method: UniVLA - unified multimodal VLA model that autoregressively models vision, language, and action as discrete token sequences. Uses tokenized formulation, post-training with world modeling for causal dynamics from videos.

3. Experiments: CALVIN, LIBERO, Simplenv-Bridge benchmarks. Compared to prior methods including π₀-FAST. Also tested on real-world ALOHA manipulation and autonomous driving.

4. Resources: Not explicitly mentioned in the provided text.

5. Experiment count: Multiple benchmarks, real-world tasks, autonomous driving scenarios.

6. Results: 95.5% average success rate on LIBERO, surpassing π₀-FAST's 85.5%. New SOTA on CALVIN, LIBERO, Simplenv-Bridge.

7. Strengths: Tokenized unified formulation, world modeling for causal dynamics, generative vision supervision enhances understanding.

8. Limitations: Not explicitly stated in the provided content, but I can infer some potential limitations.

Let me write a comprehensive summary in Chinese following the required structure.
</think>
# UniVLA：统一视觉-语言-动作模型 论文总结

## 1. 核心问题与研究动机

- **研究背景**：视觉-语言-动作模型（VLA）近年来在机器人操控领域受到广泛关注，旨在将视觉感知、语言指令与动作生成统一建模。
- **现有问题**：已有 VLA 方法主要依赖视觉-语言模型（VLM）的通用理解能力来生成动作信号，**忽略了视觉观测中蕴含的丰富时序结构与因果信息**。
- **核心动机**：如何更充分地利用视频数据中的时序因果结构，提升 VLA 模型在通用操控任务（尤其是长时序任务）上的迁移能力。

---

## 2. 方法论

### 核心思想
- 提出 **UniVLA**（Unified VLA），将**视觉、语言与动作统一表示为离散 token 序列**，通过自回归方式统一建模。

### 关键技术细节
- **统一离散化 token 化**：将图像（视觉）、文本指令（语言）和机器人动作（动作）全部 token 化后纳入同一序列，便于自回归生成式训练。
- **生成式视觉监督**：将视觉 token 作为生成目标，证明该监督方式能够显著提升模型的视觉理解能力。
- **后训练阶段的世界建模（World Modeling）**：通过预测未来视频帧等方式，让模型从视频中学习因果动力学，从而更好地迁移到下游策略学习，尤其对**长时序任务**有显著帮助。
- **视频数据预训练 + 操控数据微调**两阶段范式：先在大规模视频上做统一 token 序列的自回归预训练，再在操控数据上做策略微调。

### 算法流程（文字描述）
1. **Token 化**：对视觉帧、语言指令、动作块进行统一编码为离散 token。
2. **预训练**：在大规模视频数据上进行自回归下一个 token 预测，涵盖视觉预测与语言/动作生成。
3. **后训练世界建模**：在视频数据上继续训练以强化因果动态建模能力。
4. **下游微调**：在仿真/真实操控数据集上微调策略 token 的生成。

---

## 3. 实验设计

### 数据集 / 场景
- **仿真基准**：
  - CALVIN
  - LIBERO
  - Simplenv-Bridge
- **真实场景**：
  - ALOHA 真实机器人操控任务
  - 自动驾驶场景

### 对比方法
- 多类已有 VLA 与策略学习方法（隐含对比）。
- 明确点名的强基线：**π₀-FAST**。

### 主要结果指标
- 任务成功率（success rate）。
- 长时序任务表现（LIBERO 多任务集合平均）。

---

## 4. 资源与算力

- **论文 PDF 在抓取时遭遇 OpenReview 的 CAPTCHA 验证**，未能获得正文细节。
- **所提供的元数据与摘要中未明确说明**：
  - GPU 型号与数量
  - 预训练 / 微调时长
  - 数据规模
- 这一点在本次总结中**无法确认**，建议查阅正文或附录。

---

## 5. 实验数量与充分性

- **基准覆盖充分**：覆盖 3 个主流仿真基准 + 真实机器人 + 自动驾驶，体现方法的**跨域泛化能力**。
- **横向比较**：与 π₀-FAST 等强基线对比，差异显著（如 LIBERO 95.5% vs 85.5%）。
- **消融与组件验证**：摘要中提到"生成式视觉监督"和"世界建模后训练"是关键模块，按惯例应有相关消融，但**具体消融维度未在抓取内容中体现**。
- **客观性**：第三方公认 benchmark + 真实场景实验，方法对比公平性较高；但单篇论文中通常仍可能存在 cherry-picking 风险，需结合复现情况判断。

---

## 6. 主要结论与发现

- **统一 token 化是有效的 VLA 建模路径**：把视觉、语言、动作统一为离散 token，可自然融合视频预训练与策略学习。
- **生成式视觉监督优于纯判别式监督**：通过让模型"生成"视觉内容，可显著提升视觉理解。
- **世界建模带来长时序优势**：因果动态建模对长时序操控任务尤其重要。
- **新的 SOTA**：在 CALVIN、LIBERO、Simplenv-Bridge 上取得当时最优。
- **跨域适用性**：在 ALOHA 真实操控和自动驾驶中同样表现良好，说明方法具有通用性。

---

## 7. 论文亮点

- **统一范式**：将"预测像素/视频"与"预测动作"统一在自回归 token 框架下，避免多模块拼接的复杂性。
- **充分利用视频数据**：相比依赖静态图像-语言对的传统 VLA，UniVLA 把视频中的时序因果信息显式建模，提升长时序任务表现。
- **后训练世界建模**：可作为通用插件，与现有 VLA 框架正交。
- **跨域验证**：仿真 + 真实机器人 + 自动驾驶，覆盖范围广。
- **结果显著**：在 LIBERO 上比 π₀-FAST 提升约 10 个百分点。

---

## 8. 不足与局限

- **PDF 抓取受限**：本次未能获取正文细节，关于**算力、数据规模、完整消融、失败案例**等信息缺失。
- **离散 token 化的固有局限**：动作离散化会引入量化误差，对精细操控（亚厘米级 / 高频控制）可能不友好；论文未在抓取内容中深入讨论此点。
- **对 VLM backbone 的依赖未充分披露**：摘要未说明底层 VLM 规模与训练数据量，难以判断性能提升的来源（架构 vs 规模）。
- **真实场景验证有限**：仅在 ALOHA 和自动驾驶上做了演示，**与工业级大规模真实部署尚有距离**。
- **自动驾驶与操控的异构性**：两者任务语义差异大，"统一"是否带来真正增益需更细粒度分析。
- **公平性问题**：对比方法的复现条件、超参数是否一致未在抓取文本中说明，存在对比公平性疑问。
- **可解释性与安全性**：自回归生成式策略在真实机器人上是否安全、可解释，论文未涉及。

（完）
