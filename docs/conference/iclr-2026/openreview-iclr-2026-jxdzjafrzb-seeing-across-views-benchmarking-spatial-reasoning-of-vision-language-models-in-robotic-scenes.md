---
title: "Seeing Across Views: Benchmarking Spatial Reasoning of Vision-Language Models in Robotic Scenes"
title_zh: 跨视角观察：机器人场景中视觉语言模型空间推理的基准评测
authors: "ZhiYuan Feng, Zhaolu Kang, Qijie Wang, Zhiying Du, Jiongrui Yan, Shi Shubin, Chengbo Yuan, Huizhi Liang, Yu Deng, Qixiu Li, Rushuai Yang, Ruichuan An, Leqi Zheng, Weijie Wang, Shawn Chen, Sicheng Xu, Yaobo Liang, Jiaolong Yang, Baining Guo"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=jXDZJAfRZB"
tags: ["query:rob-il"]
score: 6.0
evidence: 评估机器人场景中VLM空间推理能力的基准，服务于VLA模型基础
tldr: VLM是具身AI的核心，也是VLA模型的基础，但现有评估多集中于单视图设置。本文提出MV-RoboBench，专门评估VLM在多视图机器人场景中的空间推理能力，旨在衡量模型整合多摄像头信息以应对遮挡与深度歧义的能力。该基准为面向机器人的VLM及VLA模型提供了重要的多视角评测工具，有助于推动其在真实机器人系统中的实际部署。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 现有VLM评测多基于单视图，未能考察其在多摄像头机器人平台中整合多视角信息的能力。
method: 提出MV-RoboBench基准，专门评估VLM在多视图机器人场景中的空间推理能力。
result: 该基准揭示了VLM在多视图机器人推理中的能力与不足，为VLA模型提供评测工具。
conclusion: MV-RoboBench为面向真实机器人的VLM与VLA模型提供了关键的多视角评估手段。
---

## Abstract
Vision-language models (VLMs) are essential to Embodied AI, enabling robots to perceive, reason, and act in complex environments. They also serve as the foundation for the recent Vision-Language-Action (VLA) models. Yet most evaluations of VLMs focus on single-view settings, leaving their ability to integrate multi-view information underexplored. At the same time, multi-camera setups are increasingly standard in robotic platforms, as they provide complementary perspectives to mitigate occlusion and depth ambiguity. Whether VLMs can effectively leverage such multi-view inputs for robotic reasoning therefore remains an open question. To bridge this gap, we introduce \textbf{MV-RoboBench}, a benchmark specifically designed to evaluate the multi-view spatial reasoning capabilities of VLMs in robotic manipulation. MV-RoboBench consists of 1.7k manually curated QA items across eight subtasks, divided into two primary categories: spatial understanding and robotic execution. We evaluate a diverse set of existing VLMs, including both open-source and closed-source models, along with enhanced versions incorporating Chain-of-Thought (CoT)-inspired techniques. The results show that state-of-the-art models remain far below human performance, underscoring the substantial challenges VLMs face in multi-view robotic perception. Additionally, our analysis uncovers two key findings: (i) spatial intelligence and robotic task execution are positively correlated in multi-view robotic scenarios; and (ii) strong performance on existing general-purpose single-view spatial understanding benchmarks does not reliably translate to success in the robotic spatial tasks assessed by our benchmark. We release MV-RoboBench as an open resource to foster progress in spatially grounded VLMs and VLAs, providing not only data but also a standardized evaluation protocol for multi-view embodied reasoning.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided metadata and abstract. Let me organize the content according to the 8 required points.
</think>
# 论文详细总结：MV-RoboBench — 跨视角观察：机器人场景中视觉语言模型空间推理的基准评测

## 1. 核心问题与整体含义（研究动机和背景）

- **核心问题**：现有对视觉语言模型（VLM）的评估多集中于**单视图（single-view）**设置，忽视了 VLM 在**多摄像头（multi-view）**机器人平台上整合多视角信息的能力。
- **背景**：
  - VLM 是具身 AI（Embodied AI）的核心，使机器人能在复杂环境中感知、推理与行动。
  - VLM 同样是近期 **VLA（Vision-Language-Action）** 模型的基础。
  - 现代机器人平台日益普遍地采用多摄像头配置，以**缓解遮挡和深度歧义**。
  - 关键开放问题：VLM 能否有效利用多视角输入进行机器人推理？
- **论文目标**：填补上述空白，提出专门评估 VLM 多视角空间推理能力的基准。

## 2. 方法论

- **核心思想**：构建一个名为 **MV-RoboBench** 的基准数据集，专门评估 VLM 在**机器人操控场景**中的**多视角空间推理能力**。
- **基准组成**：
  - 包含 **1.7k 人工策划（manually curated）的 QA 条目**。
  - 涵盖 **8 个子任务（subtasks）**。
  - 分为 **两大主类**：
    1. **空间理解（Spatial Understanding）**
    2. **机器人执行（Robotic Execution）**
- **关键技术**：
  - 评估覆盖多种 VLM，包括开源与闭源模型。
  - 在评估中引入 **Chain-of-Thought (CoT) 启发的增强方法**，以提升模型推理表现。
  - 提供了**标准化的评估协议**，确保评估一致性。
- **算法流程（文字描述）**：
  1. 构建多视角机器人操控场景数据集。
  2. 人工设计涵盖空间理解与执行能力的 QA 条目。
  3. 在多种 VLM 上进行零样本或 CoT 增强推理测试。
  4. 统计并分析各子任务表现，与人类水平对比。

## 3. 实验设计

- **基准数据集**：MV-RoboBench（1.7k QA 条目，8 个子任务）。
- **任务类别**：
  - 空间理解（Spatial Understanding）
  - 机器人执行（Robotic Execution）
- **对比方法**：
  - 多种**开源 VLM**。
  - 多种**闭源 VLM**。
  - **CoT 增强版本**的 VLM。
  - 以**人类表现**作为性能上界参考。
- **评估维度**：
  - 各子任务准确率。
  - 与人类水平差距。
  - 空间智能与机器人任务执行之间的相关性分析。
  - 单视图空间理解基准表现与多视图机器人任务表现之间的迁移性分析。

## 4. 资源与算力

- **论文中未明确提及**具体的算力使用情况（如 GPU 型号、数量、训练时长等）。
- 这可能是因为本文工作以**基准评测**为主，侧重于评估而非训练大规模模型，因此算力消耗未被作为重点报告。

## 5. 实验数量与充分性

- **实验规模**：
  - 1.7k 人工策划的 QA 条目，8 个子任务。
  - 评估涵盖多种 VLM（含开源、闭源、CoT 增强版本）。
- **实验类型**：
  - 主实验：多 VLM 在 MV-RoboBench 上的表现对比。
  - 分析性发现：
    1. 空间智能与机器人任务执行在多视图机器人场景中呈**正相关**。
    2. 在通用单视图空间理解基准上的强表现**不能可靠地**迁移到本文基准上的机器人空间任务。
- **充分性评价**：
  - 评测覆盖了主流开源与闭源模型，并加入人类基线，**对比较为公平**。
  - 提供了 CoT 增强版本的对比，有助于理解推理增强策略的实际效果。
  - 但 1.7k QA 条目规模有限，可能对评测复杂长尾空间推理能力造成覆盖不足。
  - 未见明显消融实验（例如不同多视角融合策略的对比），分析层面主要集中在相关性观察。

## 6. 主要结论与发现

- **核心结论**：当前 SOTA VLM 在多视图机器人空间推理任务上的表现**远低于人类水平**，说明 VLM 在多视角机器人感知方面仍面临**巨大挑战**。
- **关键发现**：
  1. **空间智能与机器人任务执行**在多视图机器人场景中呈正相关。
  2. 通用单视图空间理解基准上的强表现**不能可靠地**转化为本文基准中机器人空间任务的成功。
- **资源贡献**：MV-RoboBench 以开源资源形式发布，包含数据与标准化评估协议。

## 7. 优点

- **填补研究空白**：首个专门评估 VLM 多视图空间推理能力的基准，弥补了现有评测集中于单视图的不足。
- **任务设计系统**：8 个子任务覆盖空间理解与机器人执行两大类，层次清晰。
- **评估全面**：覆盖开源、闭源、CoT 增强等多种 VLM，并设人类基线。
- **双重分析视角**：既评估绝对性能，又揭示了空间智能与执行能力的相关性、单视图到多视图的迁移性不足等深层洞察。
- **开源贡献**：公开数据与评估协议，便于后续研究复现与扩展。
- **面向真实部署**：紧密对接多摄像头机器人平台实际需求，具有较强应用价值。

## 8. 不足与局限

- **数据规模有限**：1.7k QA 条目可能不足以覆盖真实机器人场景中的长尾与复杂情况。
- **场景覆盖范围**：聚焦于机器人操控（manipulation）场景，未涉及导航、交互等更广泛的具身任务。
- **算力信息缺失**：未报告评估所用算力，复现成本难以估计。
- **缺乏消融实验**：未深入探讨不同多视角融合策略、视觉编码器选择等因素对性能的影响。
- **闭源模型不透明**：闭源 VLM 的内部机制未知，CoT 增强的提升来源难以精确归因。
- **偏差风险**：人工策划 QA 条目可能引入标注者主观偏差，影响评测的客观性。
- **迁移性结论有限**：关于单视图到多视图迁移性不足的发现，可能受具体任务设计影响，普适性有待进一步验证。

（完）
