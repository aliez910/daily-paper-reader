---
title: Human-assisted Robotic Policy Refinement via Action Preference Optimization
title_zh: 通过动作偏好优化实现人机协作的机器人策略精炼
authors: "Wenke Xia, Yichu Yang, Hongtao Wu, Xiao Ma, Tao Kong, Di Hu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=dlQ1iUpQNf"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过人类偏好对齐优化VLA基础模型用于真实部署
tldr: 针对视觉-语言-动作模型依赖离线专家数据而难以在部署后持续改进的问题，本文提出了动作偏好优化（APO）方法。该方法通过人机协作框架收集干预轨迹与失败纠正信号，基于人类偏好对齐对VLA策略进行迭代式精炼。实验表明该方法能够在真实环境中对已部署的机器人策略进行持续优化。该工作为VLA模型的在线精炼与可靠部署提供了新路径。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: VLA基础模型依赖离线专家数据，部署后难以持续改进。
method: 提出动作偏好优化（APO），利用人机协作收集偏好轨迹以对齐VLA策略。
result: 实现了部署后VLA策略的迭代式精炼并提升实际任务可靠性。
conclusion: 为VLA模型在真实世界中的持续优化与可靠部署提供了可行方案。
---

## Abstract
Establishing a reliable and iteratively refined robotic system is essential for deploying real-world applications. 
    While Vision-Language-Action (VLA) models are widely recognized as the foundation model for such robotic deployment, their reliance on offline expert demonstrations critically limits their capacity for post-deployment refinement. 
    To mitigate this limitation, we introduce Action Preference Optimization (APO), a method designed to refine VLA models by human-assisted preference alignment gathered through interaction with environments.
    This method begins with a human-robot collaboration framework for reliable failure correction and interaction trajectory collection through human intervention.  
    However, directly leveraging these interaction trajectories for preference optimization is non-trivial due to the challenges of irreversible robotic actions and token distribution mismatch. To solve this, APO proposes an adaptive reweighting algorithm with binary desirability signals derived from interaction, empowering VLA models effectively suppress failure-prone actions while enhancing corrective action adaptation.
    Ultimately, APO equips VLA models with the crucial capability to learn from failure, paving the way for their iterative refinement and reliable deployment in dynamic environments.
    The experiments conducted in simulation and real-world scenarios prove superior generalization and robustness of our human-assisted framework across a variety of manipulation tasks. We believe this work could bring insights for efficient and stable optimization of VLA models through human-robot collaboration. The code and dataset are released at https://github.com/GeWu-Lab/Action-Preference-Optimization.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper based on the provided content. Let me analyze the paper first.

The paper is titled "Human-assisted Robotic Policy Refinement via Action Preference Optimization" (通过动作偏好优化实现人机协作的机器人策略精炼). It appears to be a NeurIPS 2025 accepted paper.

Key points from the paper:
- Addresses limitations of VLA (Vision-Language-Action) models which rely on offline expert demonstrations and cannot easily be refined after deployment
- Proposes Action Preference Optimization (APO)
- Uses human-robot collaboration framework
- Has an adaptive reweighting algorithm with binary desirability signals
- Experiments in simulation and real-world scenarios
- Code released at https://github.com/GeWu-Lab/Action-Preference-Optimization

The PDF content was not actually extractable (it was a CAPTCHA page), so I have to work with the metadata and abstract provided. I should be honest about this limitation but still provide a comprehensive summary based on the available information.

Let me structure the response according to the requested format. I should note where information is not available from the extracted text and rely on the abstract and metadata.
</think>
# 论文总结：通过动作偏好优化实现人机协作的机器人策略精炼

> **说明**：原 PDF 链接（OpenReview）被 CAPTCHA 拦截，未能解析到正文内容。本总结基于题目、摘要与元数据进行，方法细节、实验数据等无法完全从原文中验证的部分会明确标注。

---

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（Vision-Language-Action, VLA）模型已成为机器人部署的基础模型，在通用操作任务上展现了强大的泛化能力。
- **核心痛点**：现有 VLA 模型的训练高度依赖**离线的专家演示数据**，缺乏部署后持续学习与纠错的能力。
  - 部署后若遇到训练分布之外的失败，难以在线纠正；
  - 真实场景中的失败往往不可逆（irreversible actions），进一步加剧了数据采集与策略更新的难度；
  - 在线交互轨迹与离线专家数据在 token 分布上存在 mismatch，难以直接复用现有对齐方法。
- **研究目标**：提出一种能够在真实部署中**持续优化**VLA 策略的方案，使机器人能够从失败中学习并可靠部署。

---

## 2. 方法论：Action Preference Optimization (APO)

### 2.1 整体框架：人机协作的轨迹收集

- 设计**人机协作（human-robot collaboration）框架**，允许人类在机器人执行过程中进行**干预（intervention）**：
  - 当机器人即将出错或已经出错时，由人类接管控制；
  - 干预轨迹被记录为"**偏好轨迹**"，用于后续对齐训练；
  - 解决"不可逆动作"问题：人类干预作为安全兜底，避免失败造成物理损伤或任务彻底失败。

### 2.2 关键技术：基于二元偏好信号的自适应重加权

- **核心思想**：不再直接套用通用 RLHF 中对完整回复做偏好排序的方式，而是将干预信息抽象为**二元 desirability 信号（binary desirability signals）**：
  - 标记轨迹中哪些动作是**需要抑制的失败动作**（failure-prone actions）；
  - 标记哪些是**应当鼓励的纠正动作**（corrective action adaptation）。
- **算法设计**：提出**自适应重加权（adaptive reweighting）算法**：
  - 通过对不同动作 token 的偏好权重进行动态调整，缓解"在线干预轨迹"与"离线专家数据"之间的**token 分布不一致（token distribution mismatch）**问题；
  - 目标：让 VLA 模型在保留原有专家能力的同时，**抑制**失败模式、强化纠错模式。
- **训练范式**：可以理解为一种针对机器人动作空间的"类 DPO"式偏好优化，但针对动作的不可逆性以及轨迹分布差异做了针对性改进。

### 2.3 方法流程（文字版）

1. 部署 VLA 基础模型到真实机器人；
2. 在任务执行中由人类按需干预，收集"干预轨迹 + 失败纠正信号"；
3. 将干预信息编码为二元偏好标签；
4. 用自适应重加权算法对偏好损失进行计算；
5. 迭代微调 VLA 模型，使其更倾向于选择纠正性动作、规避失败性动作；
6. 回到真实环境再次部署，循环迭代。

> 注：具体的损失函数形式、推导细节、伪代码等无法从摘要中直接获得，需查阅正文与附录。

---

## 3. 实验设计

> 由于 PDF 未能解析，以下信息部分基于摘要描述，**未能确认**的部分会明确标出。

- **场景**：
  - 仿真环境中的多种 manipulation 任务；
  - 真实机器人场景中的多种操作任务。
- **Benchmark**：摘要未明确给出所使用 benchmark 名称。**待正文确认**。
- **对比方法**：
  - 摘要层面强调"与多种 baseline 相比在泛化性与鲁棒性上更优"；
  - **未明确列出**对比方法清单（推测可能包括：原始 VLA、SFT、行为克隆、RLAIF/DPO 类方法、传统 RL 微调等），需以正文为准。
- **评估维度**：
  - 任务成功率；
  - 泛化能力（是否对未见过的指令/物体/场景有效）；
  - 鲁棒性（面对干扰、失败恢复等的能力）。

---

## 4. 资源与算力

- **未在摘要中提及**使用的 GPU 型号、数量、训练时长等。
- 元数据中也未提供相关字段。
- 实际训练 VLA 模型通常需要较大算力（如多卡 A100 / H100 级别），但**本论文具体算力消耗待正文确认**。

---

## 5. 实验数量与充分性

- **已可确认的部分**：
  - 同时覆盖**仿真 + 真实机器人**两类环境；
  - 包含**多种 manipulation 任务**；
  - 摘要声称验证了"superior generalization and robustness"，说明做了较为系统的横向比较。
- **尚不明确的部分（需查正文）**：
  - 具体任务数量、每个任务的 trial 次数；
  - 是否有充分的消融实验（如：去掉 human intervention、去掉 adaptive reweighting、不同的重加权策略等）；
  - 真实世界实验中的人类评估者数量与统计显著性检验；
  - 是否在多个 VLA 基础模型上做了验证，还是只基于单一 backbone。
- **客观性评估**：
  - 由于偏好信号依赖人类干预，**人类主观判断的一致性**可能影响结果；
  - 真实环境实验的复现成本较高，需关注作者是否公开了数据集与代码（**已声明开源**：https://github.com/GeWu-Lab/Action-Preference-Optimization），这对社区复现与公平比较是积极信号。

---

## 6. 主要结论与发现

- APO 方法能够使 VLA 模型**从失败中学习**，实现部署后的迭代式策略精炼；
- 基于人类干预的偏好信号 + 自适应重加权，可以有效缓解"token 分布不一致"与"动作不可逆"两大难题；
- 仿真与真实实验均表明该框架在**泛化性**和**鲁棒性**上优于对比方法；
- 为 VLA 模型的**在线、持续、稳定**优化提供了一条可行路径，推动其在动态真实环境中的可靠部署。

---

## 7. 优点与亮点

- **问题定位精准**：抓住 VLA 模型"部署后难更新"这一关键瓶颈，与产业落地需求高度契合。
- **方法设计贴合场景**：
  - 引入人类干预作为安全机制，契合"动作不可逆"的实际约束；
  - 用二元偏好信号 + 自适应重加权，绕开完整轨迹偏好排序的难点，针对性强。
- **从仿真到真实**：覆盖 simulation 与 real-world 双重验证，结论更具说服力。
- **开源贡献**：公开代码与数据集（GitHub 仓库已给出），便于社区复现与后续研究。
- **定位 NeurIPS 2025**：经过同行评审的会议接收论文，具备一定学术认可度。

---

## 8. 不足与局限

- **PDF 未能完整解析**：本总结的细节程度受限于仅可获得摘要与元数据；具体的损失函数、算法伪代码、实验表格与消融结果未在本次总结中体现。
- **依赖人类干预的代价**：
  - 需要持续的人类监督，人力成本较高；
  - 不同操作员之间的干预策略差异可能引入**主观偏差**。
- **安全性与失败模式的分析不足（从摘要看）**：
  - 摘要未明确讨论在哪些类型任务上方法失效、对抗性扰动下的表现等。
- **Benchmark 与对比基线未在摘要中明确**：实际公平性需通过正文表格验证。
- **算力与训练成本不透明**：未说明训练资源需求，限制了对工程落地成本的评估。
- **泛化边界不清晰**：是否能在长时间、多任务、长尾场景中持续精炼而不出现"灾难性遗忘"，摘要中未给出答案。
- **应用限制**：从方法描述看，主要适用于可由人类实时接管的操作任务；对于高速、强实时性的任务（如运动控制、无人机等）适用性可能有限。

---

（完）
