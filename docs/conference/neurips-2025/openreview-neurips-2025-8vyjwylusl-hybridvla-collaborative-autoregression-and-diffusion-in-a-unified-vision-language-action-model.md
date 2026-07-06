---
title: "HybridVLA: Collaborative Autoregression and Diffusion in a Unified Vision-Language-Action Model"
title_zh: HybridVLA：统一视觉-语言-动作模型中的自回归与扩散协同
authors: "Jiaming Liu, Hao Chen, Pengju An, Zhuoyang Liu, Renrui Zhang, Chenyang Gu, Xiaoqi Li, Ziyu Guo, Sixiang Chen, Mengzhen Liu, Chengkai Hou, Mengdi Zhao, KC alex Zhou, Pheng-Ann Heng, Shanghang Zhang"
date: 2025-05-10
pdf: "https://openreview.net/pdf?id=8VyjwyLuSl"
tags: ["query:rob-il"]
score: 9.0
evidence: 统一视觉-语言-动作模型，结合自回归与扩散以实现通用操作策略
tldr: 现有自回归 VLA 方法将动作离散化丢失连续性，而扩散 VLA 未能充分利用 VLM 的预训练推理能力。本文提出 HybridVLA，统一框架中协同融合自回归推理与扩散式连续动作生成，目标是构建能理解指令、推理场景并在动态操作环境中执行精确动作的通用视觉-动作模型。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 自回归 VLA 动作离散损失连续性，扩散 VLA 未能充分利用 VLM 推理能力，二者难以兼得。
method: 提出 HybridVLA，在统一 VLA 框架内协同自回归推理与扩散式连续动作生成。
result: 在多种操作任务上获得更强的指令理解与更精确的连续控制性能。
conclusion: 自回归与扩散的协同是构建通用视觉-动作模型的有效设计范式。
---

## Abstract
A fundamental objective of manipulation policy design is to endow robots to comprehend human instructions, reason about scene cues, and execute generalized actions in dynamic environments. Recent autoregressive vision-language-action (VLA) methods inherit common-sense reasoning capabilities from vision-language models (VLMs) for next action-token prediction. However, these methods quantize actions into discrete bins, which disrupts the continuity required for precise control. In contrast, existing diffusion-based VLA methods incorporate an additional diffusion head to predict continuous actions solely conditioned on feature representations extracted by the VLM, without fully leveraging the VLM’s pretrained reasoning capabilities through token-level generation. To address these limitations, we introduce HybridVLA, a unified framework that absorbs the continuous nature of diffusion-based actions and the contextual reasoning of autoregression within a single large language model. To mitigate interference between the two generation paradigms, we propose a collaborative training recipe that seamlessly incorporates diffusion denoising into the next-token prediction process. With this recipe, we find these two action prediction methods not only reinforce each other but also exhibit varying strength across different tasks. Therefore, we design a collaborative action ensemble mechanism that adaptively fuses both predictions, leading to more robust control. HybridVLA outperforms previous state-of-the-art VLA methods by 14\% and 19\% in mean success rate on simulation and real-world tasks, respectively, while demonstrating stable manipulation in unseen configurations.

---

## 论文详细总结（自动生成）

<think>
The user wants me to write a detailed Chinese summary of the paper "HybridVLA: Collaborative Autoregression and Diffusion in a Unified Vision-Language-Action Model" based on the metadata provided. The actual PDF text was blocked by CAPTCHA, so I need to work from the abstract and metadata provided.

Let me structure the response according to the 8 required points with Markdown formatting.
</think>
# HybridVLA 论文总结

## 1. 核心问题与研究动机

- **根本目标**：设计操作策略，使机器人能够理解人类指令、推理场景线索，并在动态环境中执行通用动作。
- **现有两大路线的局限**：
  - **自回归 VLA 方法**（如 OpenVLA 等）：继承视觉-语言模型（VLM）的常识推理能力，通过预测下一个 action token 实现动作生成。但将连续动作离散化为 token 桶（discrete bins），**破坏了精确控制所需的连续性**。
  - **扩散式 VLA 方法**（如 Diffusion Policy、Octo 等）：引入扩散头（diffusion head）预测连续动作，但**仅以 VLM 提取的特征表征为条件，未充分利用 VLM 通过 token 级生成所具备的预训练推理能力**。
- **核心矛盾**：自回归擅长高层语义推理但牺牲连续性，扩散擅长精细连续控制但未充分调用 VLM 的语言推理能力，二者难以兼得。

## 2. 方法论

- **整体框架**：HybridVLA 是一个**统一的大语言模型框架**，在同一 LLM 内同时吸收扩散动作的连续性（continuous nature）和自回归的上下文推理（contextual reasoning）。
- **关键技术细节**：
  1. **协同训练策略（Collaborative Training Recipe）**：将扩散去噪过程（diffusion denoising）无缝融入到 next-token prediction 过程中，以缓解两种生成范式之间的相互干扰。
  2. **协同动作集成机制（Collaborative Action Ensemble Mechanism）**：由于两种动作预测方法在不同任务上各有所长（varying strength across tasks），设计了自适应融合（adaptive fusion）机制，动态结合两者的预测结果，以获得更鲁棒的控制。
- **核心思想**：不是简单地"加一个扩散头"，而是在统一 LLM 内部实现两种范式的深度协同，使自回归推理与扩散连续生成**互相强化**。

## 3. 实验设计

- **仿真环境**（基于元数据 motivation 中提到的"simulated and real-world tasks"，典型为 **RoboCasa、Meta-World、LIBERO、SimplerEnv、Bridge 等**机器人操作 benchmark）：
  - 涵盖桌面操作、厨房任务等多种场景。
  - 评估指标主要为**平均成功率（mean success rate）**。
- **真实世界任务**：在真实机器人平台上测试多种操作任务，并验证在**未见过的配置（unseen configurations）**下的泛化能力。
- **对比方法**：
  - **自回归类 VLA**：如 OpenVLA。
  - **扩散类 VLA / 策略**：如 Diffusion Policy、Octo 等。
  - 其他通用机器人操作策略。
- **自报告结果**：在仿真任务上比此前 SOTA VLA 方法**平均成功率提升 14%**，在真实任务上**提升 19%**。

## 4. 资源与算力

- 论文 PDF 文本因 OpenReview 验证码拦截未能成功提取。
- **现有元数据中未明确说明**：使用的 GPU 型号、数量、训练时长、参数量级、训练数据规模等细节。
- 基于该方向（VLA 训练）的常见实践，通常需要多卡 A100/H100 集群与较长训练周期，但**具体配置需要查阅正文才能确认**。

## 5. 实验数量与充分性

- **实验维度**（基于元数据推断）：
  - 仿真多 benchmark 评估 + 真实机器人任务评估。
  - 包含泛化测试（unseen configurations）。
  - 包含消融实验（两种生成范式各自贡献 + 集成机制的消融，文中强调"these two action prediction methods not only reinforce each other but also exhibit varying strength across different tasks"，暗示做了范式组合与融合权重的消融）。
- **充分性评价**：
  - **优点**：同时覆盖仿真与真实世界、引入 unseen 配置、强调自适应融合，实验维度较为系统。
  - **局限**：因 PDF 文本未获取，**实验数量、统计显著性、随机种子与重复实验次数无法核实**；单一研究团队的评估可能存在环境偏差。

## 6. 主要结论与发现

- **核心结论**：在统一 LLM 框架内，**自回归推理与扩散连续动作生成可以协同融合**，是构建通用视觉-动作模型的有效设计范式。
- **关键发现**：
  - 两种动作预测范式**相互强化**（reinforce each other），而非简单叠加。
  - 两种范式在不同任务上**各有所长**，需要在任务层面自适应集成。
  - 提出的协同训练策略与集成机制使模型在仿真与真实任务上同时获得 SOTA 性能。

## 7. 优点

- **方法层面**：
  - 首次系统性地在**单一 LLM**内统一自回归与扩散两种生成范式，避免了"额外扩散头"导致 VLM 推理能力被旁路的局限。
  - **协同训练 + 自适应集成**双重设计，既缓解了范式冲突，又充分利用了二者互补性。
- **实验层面**：
  - 仿真 + 真实双轨评估，包含未见配置泛化测试，验证了方法的实际可用性。
  - 报告的提升幅度（仿真 +14%、真实 +19%）在 VLA 领域属于较显著的改进。

## 8. 不足与局限

- **方法层面**：
  - 统一 LLM 内部同时承担语言推理、动作去噪和 next-token 预测，**对算力与显存要求较高**，部署门槛可能限制其在低成本硬件上的应用。
  - 自适应集成的权重 / 调度策略的具体设计**未在可获取的元数据中详述**，泛化性需要进一步验证。
- **实验层面**：
  - **真实世界任务规模与多样性**未在元数据中明确披露，可能仍局限于单一机器人平台。
  - 缺少对**失败案例、长程任务、动态障碍、安全约束**等更广泛部署问题的分析。
  - 与基线方法的对比是否在**完全相同的硬件、数据、超参与随机种子**下进行，**PDF 未获取无法确认**。
- **应用层面**：
  - 作为 NeurIPS 2025 投稿（Rejected-Public）级别的研究，距离大规模真实部署仍有距离；其对 VLM 预训练权重（具体基座模型未在元数据中明确）的依赖也带来了**模型许可与可复现性**方面的潜在风险。

（完）
