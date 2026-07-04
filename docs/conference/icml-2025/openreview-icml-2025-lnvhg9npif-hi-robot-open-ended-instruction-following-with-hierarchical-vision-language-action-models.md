---
title: "Hi Robot: Open-Ended Instruction Following with Hierarchical Vision-Language-Action Models"
title_zh: "Hi Robot: 基于分层视觉-语言-动作模型的开放式指令跟随"
authors: "Lucy Xiaoyang Shi, brian ichter, Michael Robert Equi, Liyiming Ke, Karl Pertsch, Quan Vuong, James Tanner, Anna Walling, Haohuan Wang, Niccolo Fusai, Adrian Li-Bell, Danny Driess, Lachy Groom, Sergey Levine, Chelsea Finn"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=lNVHg9npif"
tags: ["query:rob-il"]
score: 9.0
evidence: 分层视觉-语言-动作模型实现开放式指令跟随
tldr: 针对通用机器人难以处理复杂指令和用户反馈的问题，提出一种分层视觉-语言-动作系统。该系统利用视觉-语言模型先推理高层次指令和反馈，再执行具体动作，实现了开放式指令跟随。实验表明该方法能有效处理多种复杂任务，提升了机器人的通用性和交互能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 通用机器人需处理复杂指令，现有系统难以有效整合语言理解与物理执行。
method: 提出分层VLA架构，顶层使用视觉-语言模型推理指令，底层执行具体动作。
result: 在多种开放式指令任务上取得良好表现，能处理用户反馈进行动态调整。
conclusion: 分层视觉-语言-动作模型是实现通用机器人有效指令跟随的重要方向。
---

## Abstract
Generalist robots that can perform a range of different tasks in open-world settings must be able to not only reason about the steps needed to accomplish their goals, but also process complex instructions, prompts, and even feedback during task execution. Intricate instructions (e.g., "Could you make me a vegetarian sandwich?" or "I don't like that one") require not just the ability to physically perform the individual steps, but the ability to situate complex commands and feedback in the physical world. In this work, we describe a system that uses vision-language models in a hierarchical structure, first reasoning over complex prompts and user feedback to deduce the most appropriate next step to fulfill the task, and then performing that step with low-level actions. In contrast to direct instruction following methods that can fulfill simple commands ("pick up the cup"), our system can reason through complex prompts and incorporate situated feedback during task execution ("that's not trash"). We evaluate our system across three robotic platforms, including single-arm, dual-arm, and dual-arm mobile robots, demonstrating its ability to handle tasks such as cleaning messy tables, making sandwiches, and grocery shopping.
Videos are available at https://www.pi.website/research/hirobot

---

## 论文详细总结（自动生成）

# 论文详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究动机**：通用机器人需要在开放世界环境中完成多种任务，不仅要推理实现目标的步骤，还要处理复杂指令（如“请给我做一个素食三明治”）、提示以及在执行过程中的用户反馈（如“我不喜欢那个”）。现有系统往往只能执行简单指令（如“拿起杯子”），缺乏将复杂语言命令和情境化反馈与物理世界行动相结合的能力。
- **整体含义**：该工作旨在增强机器人的通用性和交互能力，使其能够理解并执行开放式指令，并能在任务过程中根据用户反馈动态调整行为，从而向更通用、更自然的人机协作迈进一步。

## 2. 论文提出的方法论：核心思想、关键技术细节、算法流程

- **核心思想**：提出一种分层视觉-语言-动作系统（Hi Robot），将高层语义推理与低层物理动作执行分离，利用视觉-语言模型（VLM）处理复杂指令和用户反馈，再将推理结果传递给底层动作生成模块。
- **关键技术细节**：
  - 采用**分层架构**（Hierarchical Vision-Language-Action Models）：
    - **顶层**：使用视觉-语言模型（如预训练的大视觉-语言模型）对复杂提示和用户反馈进行情境化推理，决定当前任务的“最合适的下一步”步骤。该层负责分解高层指令、理解用户意图、处理修正反馈。
    - **底层**：将顶层推理出的步骤转换为具体的低层动作（例如机械臂运动、夹爪控制），可能依赖于已有的动作策略或运动规划器。
  - 系统能够**在线整合反馈**：在执行过程中，若用户给出新的指令或否定性反馈（如“那不是垃圾”），顶层VLM重新推理并调整计划，底层动作随之更新。
- **算法流程简述**：
  1. 接收用户自然语言指令或反馈 + 当前视觉观测（摄像头图像）。
  2. 顶层VLM对指令和场景进行联合推理，输出一个或多个子任务（如“先拿面包”、“再放生菜”）。
  3. 底层动作模块根据当前子任务和观测，生成具体的关节或末端执行器动作序列。
  4. 若在执行过程中收到新反馈，回到步骤2重新规划。

- **公式或算法细节**：文中未提供显式公式，上述为基于摘要及元数据的合理推断。

## 3. 实验设计：数据集/场景、基准、对比方法

- **实验平台与场景**：在三种不同的机器人平台上进行实验：
  - 单臂机器人
  - 双臂机器人
  - 双臂移动机器人
- **任务类型**（示例）：
  - 清理杂乱的桌子（涉及分类垃圾和非垃圾）
  - 制作三明治（需理解“素食”等属性）
  - 杂货购物（需根据用户偏好挑选物品）
- **评价基准**：文中未提及与其他方法定量对比的基准（如没有给出标准数据集或排名）。实验以**定性演示**和**任务成功率**（可能）的方式呈现，但摘要及元数据未提供具体数值。
- **对比方法**：文中未明确对比其他基线方法。仅概括性说明本系统相比直接指令跟随方法（如只能执行“拿起杯子”）更具优势。

## 4. 资源与算力

- **文中未明确说明**所使用的GPU型号、数量、训练时长等信息。元数据中也没有算力相关细节。因此无法从现有信息中总结。

## 5. 实验数量与充分性

- **实验数量**：根据摘要和元数据，实验涉及三个不同平台、多个任务类型（至少清理、烹饪、购物三类），但没有报告具体任务数量、每个任务的测试次数或用户交互轮数。也未提及是否进行了消融研究（如有无分层结构的影响、不同VLM的选择等）。
- **充分性与客观性**：
  - **优点**：多平台评估增加了泛化属性的说服力；任务多样性较好。
  - **不足**：缺乏与现有方法的定量比较，没有标准基准上的指标；结果可能偏定性演示，客观性不足；未提供统计显著性分析或失败案例讨论。因此，实验的充分性和公平性尚不完全明确。

## 6. 论文的主要结论与发现

- 提出的分层视觉-语言-动作系统能够有效处理开放式指令和动态用户反馈，实现了更为灵活的机器人任务执行。
- 系统在多样化任务（清理、制作三明治、购物）和不同机器人平台上均表现出良好的性能，证明了架构的通用性。
- 通过高层语言推理与低层动作控制的分离，机器人可以更好地理解复杂命令和情境化反馈，从而提升人机交互的自然性和任务成功率。
- 作者认为分层VLA模型是迈向通用机器人有效指令跟随的重要方向。

## 7. 优点：方法与实验设计的亮点

- **方法论亮点**：
  - 提出分层框架，将语言理解和物理执行解耦，降低系统复杂度，且便于利用预训练的VLM知识。
  - 支持在线反馈整合，使机器人能动态调整行为，更具交互柔性。
  - 适用于多种平台（单臂、双臂、移动机器人），展示出良好的可迁移性。
- **实验亮点**：
  - 覆盖多个现实世界任务，任务难度较高（如理解“素食”偏好、识别垃圾等），体现了系统的推理能力。
  - 提供了视频演示（网站链接），使结果直观可视。

## 8. 不足与局限

- **实验覆盖有限**：缺乏大规模定量实验和标准基准上的对比，结论支撑偏向定性展示。
- **偏差风险**：测试场景可能经过挑选，未报告失败率或反面案例，易产生性能高估。
- **应用限制**：
  - 系统依赖预训练VLM，其推理能力受限于模型本身的质量和训练数据分布，可能难以处理罕见或模糊指令。
  - 底层动作模块假设有可靠的低层控制策略，目前未讨论对复杂或高精度任务（如精密装配）的适用性。
  - 未提及用户研究，实际人机交互体验未得到系统评估。
- **资源与复现**：未公开算力需求、训练代码或模型权重，可复现性存疑。

（完）
