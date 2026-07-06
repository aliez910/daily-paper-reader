---
title: Video Generators are Robot Policies
title_zh: 视频生成器即机器人策略
authors: "Junbang Liang, Pavel Tokmakov, Ruoshi Liu, Sruthi Sudhakar, Paarth Shah, Rares Andrei Ambrus, Carl Vondrick"
date: 2025-09-17
pdf: "https://openreview.net/pdf?id=cWczH8ontO"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过视频生成实现端到端视觉运动策略的灵巧操作
tldr: 现有视觉运动策略在感知与行为分布偏移下泛化能力差，且严重依赖大规模人类示教数据。为此，本文提出Video Policy，将视频生成与动作生成融合在一个端到端可训练框架中，以视频生成作为机器人策略学习的代理。该方法仅需少量示教即可从生成视频中提取鲁棒策略，在未见过物体和背景下表现出强泛化能力，并显著提升灵巧操作的样本效率。
source: ICLR-2026-Public
selection_source: conference_retrieval
motivation: 现有视觉运动策略在分布偏移下泛化能力差，且依赖大量人类示教数据。
method: 提出Video Policy模块化框架，结合视频生成与动作生成进行端到端策略学习。
result: 该方法以极少示教数据获得强泛化策略，在未见过物体和背景下表现优异。
conclusion: 工作展示了视频生成作为机器人策略学习代理的潜力与样本效率优势。
---

## Abstract
Despite tremendous progress in dexterous manipulation, current visuomotor policies remain fundamentally limited by two challenges: they struggle to generalize under perceptual or behavioral distribution shifts, and their performance is constrained by the size of human demonstration data. In this paper, we use video generation as a proxy for robot policy learning to address both limitations simultaneously.
We propose Video Policy, a modular framework that combines video and action generation that can be trained end-to-end. Our results demonstrate that learning to generate videos of robot behavior allows for the extraction of policies with minimal demonstration data, significantly improving robustness and sample efficiency. Our method shows strong generalization to unseen objects, backgrounds, and tasks, both in simulation and the real world. We further highlight that task success is closely tied to the generated video, with action-free video data providing critical benefits for generalizing to novel tasks. By leveraging large-scale video generative models, we achieve superior performance compared to recent VLAs and video-action models, paving the way for more scalable and data-efficient robot policy learning.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Video Generators are Robot Policies" (Video Policy). Let me analyze the provided content carefully.

From the abstract and metadata, I can extract the following key information:

1. **Core Problem**: 
   - Visuomotor policies struggle with generalization under perceptual/behavioral distribution shifts
   - Performance is constrained by size of human demonstration data
   - Need for data-efficient robot policy learning

2. **Method**:
   - Video Policy - a modular framework combining video and action generation
   - Trained end-to-end
   - Uses video generation as proxy for robot policy learning
   - Leverages large-scale video generative models
   - Can extract policies from generated videos with minimal demonstration data

3. **Experiments**:
   - Tested in simulation and real world
   - Generalization to unseen objects, backgrounds, and tasks
   - Compared with recent VLAs (Vision-Language-Action models) and video-action models

4. **Resources**: Not explicitly mentioned in the provided text

5. **Conclusions**:
   - Task success is closely tied to generated video quality
   - Action-free video data provides critical benefits for novel tasks
   - Superior performance compared to VLAs and video-action models
   - Paves way for scalable, data-efficient policy learning

Let me structure a detailed Chinese summary based on the available information, being honest about what is and isn't provided in the text.

I should be careful to:
- Only use information provided in the text
- Note when information is missing (e.g., specific datasets, GPU info, experiment counts)
- Not fabricate details
- Provide a clear, structured Chinese summary

Let me write the summary now.
</think>
# 论文总结：Video Generators are Robot Policies（视频生成器即机器人策略）

## 1. 核心问题与研究动机

- **领域背景**：灵巧操作（dexterous manipulation）研究近年来取得显著进展，但视觉运动策略（visuomotor policies）仍面临两大根本性瓶颈。
- **问题一：泛化能力差**：现有策略在感知层面（如光照、纹理、背景等外观变化）或行为层面（任务变体）发生分布偏移时，性能急剧下降。
- **问题二：数据依赖高**：策略性能严重依赖大规模人类示教数据，获取成本高且难以扩展。
- **核心假设**：利用大规模视频生成模型的世界知识与视觉先验，将"视频生成"作为机器人策略学习的代理任务，可以同时缓解上述两个问题。

---

## 2. 方法论：Video Policy 框架

- **核心思想**：将视频生成与动作生成融合到同一个**端到端可训练**的模块化框架中，通过学习生成机器人行为的视频来间接学习策略。
- **关键技术要点**：
  - **双任务联合训练**：同时建模视频（观测预测）与动作（控制输出），二者共享表征。
  - **视频作为代理任务**：先在大规模视频数据上学到丰富的物理与场景先验，再迁移到机器人控制。
  - **少样本策略提取**：仅需少量示教即可从生成的视频中抽取可执行策略。
  - **动作无关视频数据的作用**：强调 action-free 的视频数据对迁移到新任务有"关键益处"。
- **训练范式**：端到端（end-to-end）训练，而非传统两阶段"先预训练视频模型、再做动作预测"的解耦方案。

---

## 3. 实验设计

- **场景覆盖**：
  - **仿真环境**：在仿真中进行系统性评估。
  - **真实世界**：在真实机器人上验证迁移效果。
- **泛化维度**：
  - 未见过的物体（unseen objects）
  - 未见过的背景（unseen backgrounds）
  - 未见过的任务（unseen tasks）
- **基线对比**：
  - 近期 VLA（Vision-Language-Action）模型
  - 近期 video-action 模型
- **Benchmark 细节**：原文未提供具体的 benchmark 名称、任务数量和评价指标（所给摘要中未提及），无法进一步细化。

---

## 4. 资源与算力

- 所提供的论文文本（摘要 + 元数据）**未明确说明**：
  - 使用的 GPU 型号与数量
  - 训练时长
  - 算力开销
- 因此本节信息缺失，建议查阅正文或附录获取细节。

---

## 5. 实验数量与充分性

- **实验规模**：从摘要可知涵盖**仿真 + 真实世界**、**多种未见过的物体/背景/任务**维度，并对比了 VLA 与 video-action 两类基线。
- **充分性评价**：
  - 优点：覆盖了仿真-真实迁移、外观与任务层面的双重分布偏移测试。
  - 不足：所给材料未提供消融实验数量、各任务的样本量、统计显著性检验等细节，难以判断实验是否充分与公平；具体基准、指标和误差条等信息需要查阅正文确认。

---

## 6. 主要结论与发现

- **视频生成质量与任务成功高度相关**：任务成功率与生成视频的质量呈强相关，说明视频生成可作为策略学习的高质量代理。
- **动作无关视频数据价值显著**：即不含动作标注的视频数据对泛化到新任务有"关键益处"，表明大规模无动作视频可被有效利用。
- **样本效率大幅提升**：仅需极少量示教数据即可获得强泛化策略。
- **性能超越现有基线**：在对比近期 VLA 与 video-action 模型时取得更优表现，验证了方法的先进性。
- **可扩展性**：证明利用大规模视频生成模型为机器人策略学习提供了**更可扩展、数据更高效**的路径。

---

## 7. 优点与亮点

- **范式创新**：首次系统性地将"视频生成"作为机器人策略学习的代理任务，思路新颖。
- **端到端联合建模**：避免了两阶段方案中表征不对齐的问题。
- **数据效率突出**：在少示教设定下仍能获得强泛化能力，降低对人类示教的依赖。
- **双重泛化**：同时在感知（物体、背景）与行为（任务）层面验证泛化性，覆盖面广。
- **充分利用无动作视频**：大幅扩展了可用的训练数据池。
- **仿真-真实迁移**：包含 real-world 实验，验证了方法的实用性。

---

## 8. 不足与局限

- **实验细节披露不足**：摘要层级未公开具体的 benchmark、数据集、任务数量、评价指标与消融设置，读者难以独立评估结果稳健性。
- **算力信息缺失**：未提及训练资源消耗，难以判断方法的可复现成本。
- **视频生成模型的依赖性**：方法性能高度依赖底层视频生成模型的质量，可能继承其偏差与失败模式。
- **因果与安全性风险**：仅以"任务成功率"作为主要评价，未充分讨论失败案例与安全边界。
- **偏差与公平性**：未明确是否针对不同物体类别、光照、遮挡等条件进行了平衡采样，存在评估偏差风险。
- **应用范围**：当前在摘要层面主要聚焦灵巧操作，是否适用于移动操作、长视野任务等更广泛场景尚不明确。

（完）
