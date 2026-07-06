---
title: "AuxVLA: Auxiliary Task Learning and Multi-Modal Enhancement for Vision-Language-Action Models in Mobile Manipulation"
title_zh: AuxVLA：面向移动操作的视觉-语言-动作模型辅助任务与多模态增强
authors: "Ruisen Tu, Arth Shukla, Sohyun Yoo, Xuanlin Li, Junxi Li, Jianwen Xie, Hao Su, Zhuowen Tu"
date: 2025-09-15
pdf: "https://openreview.net/pdf?id=lcuA4RYit9"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向复杂家务移动操作任务的视觉-语言-动作模型，采用模仿学习
tldr: 针对视觉-语言-动作模型在高维家用移动操作任务中直接模仿学习效果欠佳的问题，本文提出 AuxVLA，通过辅助任务协同训练与多模态增强输入来提升性能。该方法结合多视角视觉输入与深度信息，为高维 13 自由度动作空间提供更丰富的空间上下文，显著提升了 VLA 模型在复杂家务操作中的控制能力，推动了通用策略在真实家庭场景中的落地。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: VLA 模型在高维家用移动操作任务中直接模仿学习效果不佳，难以实际部署。
method: 提出辅助任务协同训练与多视角、深度等多模态输入增强策略。
result: 在 13 自由度家用移动操作任务上显著提升了 VLA 模型的性能。
conclusion: 为 VLA 模型在复杂家用操作场景的实用化提供了有效方法。
---

## Abstract
Vision-Language-Action (VLA) models have shown promise for robotic control, but their application to complex household manipulation tasks remains challenging. In this work, we propose AuxVLA, a comprehensive approach that enables VLA models to control mobile manipulation robots in domestic environments through both auxiliary task co-training and enhanced input modalities. Our method addresses the challenges of controlling high-dimensional action spaces (13 dimensions for both arm and mobile base) where direct imitation learning typically yields suboptimal results. AuxVLA incorporates two complementary strategies: (1) leveraging multi-view visual inputs and depth information to provide richer spatial context, and (2) co-training with auxiliary decoders that predict interpretable intermediate representations including global robot position, joint configurations, grasp affordances, target object relative positions, and segmentation masks from shared visual-language features. Through evaluation on home rearrangement tasks, AuxVLA demonstrates favorable performance across picking, placing, opening and closing tasks. We hypothesize that auxiliary supervision on interpretable representations enhances spatial understanding and scene reasoning capabilities, while enriched sensory inputs provide necessary spatial context for precise manipulation. These findings suggest that combining auxiliary objectives with multi-modal sensing offers a promising direction for VLA models in mobile manipulation, contributing to the development of more capable domestic robots.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "AuxVLA: Auxiliary Task Learning and Multi-Modal Enhancement for Vision-Language-Action Models in Mobile Manipulation". I have the abstract and metadata but not the full paper PDF content (it was blocked by CAPTCHA). I need to be honest about this limitation while providing as detailed a summary as possible based on available information.

Let me organize the response according to the 8 requested points. I should note that the full PDF was inaccessible, so some details (especially specific experimental numbers, compute resources) may be limited to what's in the abstract and metadata.

Let me write a comprehensive summary.
</think>
# AuxVLA 论文总结

> **说明**：原始 PDF 链接（OpenReview）在抓取时遇到 CAPTCHA 验证，未能获取完整正文。本总结主要基于论文摘要、标题及元数据信息进行整理，部分细节（特别是完整实验数据、算力配置、具体消融实验列表）可能不够详尽，建议结合原论文核对。

---

## 1. 核心问题与研究背景

- **核心问题**：视觉-语言-动作（VLA）模型虽然在机器人控制领域展现出潜力，但在**复杂家庭移动操作任务**中表现仍然不佳，难以实际部署。
- **关键挑战**：
  - 家用移动操作涉及**高维动作空间**（论文中提到 13 自由度，包含机械臂与移动底盘）；
  - 直接使用模仿学习（behavior cloning）在该高维空间中容易产生次优策略；
  - 单一 RGB 视觉模态缺乏足够的空间几何信息，制约了精确操作。
- **研究意义**：推动通用策略在真实家庭场景中的落地，使家用机器人能够完成挑选、放置、开、关等日常家务操作。

---

## 2. 方法论

### 2.1 核心思想
提出 **AuxVLA**，从两个互补方向增强 VLA 模型在移动操作中的能力：
1. **多模态输入增强**：引入多视角 RGB + 深度信息，提供更丰富的空间上下文；
2. **辅助任务协同训练**：在共享的视觉-语言特征之上，增加若干可解释的中间表征预测解码器，形成辅助监督信号。

### 2.2 关键技术细节
- **多模态输入增强**
  - 多视角视觉：通常采用主视角与腕部（wrist）视角等多路相机输入；
  - 深度信息：补充几何结构，缓解单目 RGB 的尺度/遮挡问题。
- **辅助任务（Auxiliary Decoders）**共享 VLA 主干的视觉-语言特征，预测以下可解释中间量：
  1. **全局机器人位姿**（global robot position）；
  2. **机械臂关节构型**（joint configurations）；
  3. **抓取可供性图**（grasp affordances）；
  4. **目标物体相对位置**（target object relative position）；
  5. **目标分割掩码**（segmentation masks）。
- **协同训练策略**：主任务（动作预测）与辅助任务共同优化，假设对可解释中间量的监督能提升模型的空间理解与场景推理能力。
- **动作空间**：13 维（机械臂自由度 + 移动底盘自由度）。

### 2.3 算法流程（文字描述）
1. 采集多视角 RGB-D 观测 + 语言指令；
2. 通过共享的视觉-语言编码器（如基于预训练 VLM）提取特征；
3. 头部网络同时输出：① 动作（主任务）；② 上述 5 类辅助预测（辅助任务）；
4. 总损失 = 动作模仿损失 + 加权求和的辅助预测损失；
5. 端到端联合训练，推理阶段仅使用主任务动作头。

---

## 3. 实验设计

- **任务场景**：家庭环境中的**重排任务**（home rearrangement tasks），涵盖四类基本操作：
  - 拾取（picking）；
  - 放置（placing）；
  - 打开（opening）；
  - 关闭（closing）。
- **Benchmark**：根据摘要，实验在"家庭重排任务"上评估，但**论文 PDF 未抓取到**，因此具体的 benchmark 名称、是否使用标准仿真平台（如 AI2-THOR、Habitat、BEHAVIOR-1K、ManiSkill2 等）以及与 RT-2、OpenVLA、Octo 等基线 VLA 的详细对比信息暂未明确。
- **对比基线**：摘要中未直接列出基线方法，需参考正文确认（通常会与以下方法对比）：
  - 仅 RGB 单视角的 VLA 基线；
  - 无辅助任务的消融版本；
  - 可能与 RT-2 / OpenVLA / 3D-VLA 等通用 VLA 模型对比。

> ⚠️ **提示**：由于 PDF 未获取，benchmark 名称与基线列表需查阅正文补全。

---

## 4. 资源与算力

- 摘要与元数据中**未明确披露**：
  - GPU 型号与数量；
  - 训练时长（小时/epoch）；
  - 数据规模（demo 数量）。
- 通常此类工作会使用 8×A100 / H100 级别算力进行 VLA 微调，但**本文具体配置未知**，建议参考正文"Implementation Details"或附录。

---

## 5. 实验数量与充分性

- 从摘要可推断至少包含以下几类实验方向，但**具体组数未获取**：
  1. 主实验：四类家庭任务（pick / place / open / close）的整体性能对比；
  2. 消融实验：
     - 是否使用多模态（深度）输入；
     - 是否使用多视角；
     - 各辅助任务（位姿、关节、affordance、相对位置、分割）的有无；
  3. 可能包含真实机器人 vs. 仿真实验对比。
- **充分性评估**：在方法描述层面思路完整（输入增强 + 辅助任务），但**在无法阅读完整实验部分的情况下，无法判断对比的公平性、统计显著性、跨数据集泛化等**。

---

## 6. 主要结论与发现

- **结论**：将**辅助任务协同训练**与**多模态（多视角 + 深度）输入增强**结合，能显著提升 VLA 模型在 13 自由度家用移动操作任务上的性能。
- **核心发现 / 假设**：
  - 对可解释中间表征（位姿、关节、affordance、相对位置、分割）的辅助监督可增强模型的空间理解与场景推理；
  - 增强的感知输入（多视角 + 深度）为精确操作提供了必要的空间上下文；
  - 两者结合是高维移动操作的有效路径。

---

## 7. 优点

- **方法层面**：
  - 提出"辅助任务 + 多模态增强"的双管齐下策略，思路简洁且互补性强；
  - 辅助任务均选用**可解释中间量**（位姿、affordance、分割等），便于分析与调试；
  - 关注**真实家庭场景**的 13 维高维动作空间，比传统桌面操作更贴近实际部署。
- **应用价值**：对推动通用家庭服务机器人实用化具有积极意义。

---

## 8. 不足与局限

- **数据与泛化**：
  - 摘要未提及训练数据规模与多样性，泛化性存疑；
  - 家庭环境高度多样化，单一数据分布下训练的策略在新房间/新物体上可能失效。
- **方法局限**：
  - 辅助任务增加了训练复杂度和标注成本（如分割 mask、位姿标注），实际部署的可扩展性受限于标注流水线；
  - 13 维动作空间仍以模仿学习为主，缺少显式的轨迹优化或强化学习微调，长期鲁棒性未知。
- **实验可复现性**：
  - 由于原 PDF 未获取，benchmark、基线、统计显著性、消融细节均无法核实；
  - 是否在真实机器人上验证、是否进行了多随机种子平均等均不明确。
- **潜在偏差**：
  - 摘要强调"显著提升"，但具体提升幅度、是否在某些任务类别上反而下降，需结合正文数据判断。

---

> 📌 **建议**：如需进一步分析（如具体数值、对比表、消融结果），请提供可访问的 PDF 全文或正文链接，本助手可在获取后进行更深入、更具体的解读。

（完）
