---
title: "VLA-Cache: Efficient Vision-Language-Action Manipulation via Adaptive Token Caching"
title_zh: VLA-Cache：基于自适应token缓存的高效视觉-语言-动作机器人操作
authors: "Siyu Xu, Yunke Wang, Chenghao Xia, Dihao Zhu, Tao Huang, Chang Xu"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=QZYZ0Xm58q"
tags: ["query:rob-il"]
score: 8.0
evidence: 加速VLA模型以实现实时的端到端视觉-动作机器人控制
tldr: 针对视觉-语言-动作模型计算开销大、难以满足实时机器人控制需求的问题，本文提出了VLA-Cache免训练推理加速方法。该方法通过自适应缓存与复用相邻帧中变化最小的视觉token的键值表征，利用机器人操作的时序连续性减少冗余计算。实验表明VLA-Cache显著提升推理速度且不损失端到端动作生成质量。该工作为VLA模型的实时部署提供了实用加速方案。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: VLA模型计算开销大，难以满足实时机器人控制需求。
method: 提出VLA-Cache，通过跨帧缓存与复用静态视觉token降低推理成本。
result: 在保持动作生成质量前提下显著提升VLA推理速度。
conclusion: 为VLA模型在实时机器人控制中的实际部署提供了高效加速方法。
---

## Abstract
Vision-Language-Action (VLA) models have demonstrated strong multi-modal reasoning capabilities, enabling direct action generation from visual perception and language instructions in an end-to-end manner. However, their substantial computational cost poses a challenge for real-time robotic control, where rapid decision-making is essential. This paper introduces VLA-Cache, a training-free inference acceleration method that reduces computational overhead by adaptively caching and reusing static visual tokens across frames. Exploiting the temporal continuity in robotic manipulation, VLA-Cache identifies minimally changed tokens between adjacent frames and reuses their cached key-value representations, thereby circumventing redundant computations. Additionally, to maintain action precision, VLA-Cache selectively re-computes task-relevant tokens that are environmentally sensitive, ensuring the fidelity of critical visual information. To further optimize efficiency, we introduce a layer adaptive token reusing strategy that dynamically adjusts the reuse ratio based on attention concentration across decoder layers, prioritizing critical tokens for recomputation. Extensive experiments on two simulation platforms (LIBERO and SIMPLER) and a real-world robotic system demonstrate that VLA-Cache achieves up to 1.7× speedup in CUDA latency and a 15\% increase in control frequency, with negligible loss on task success rate. The code and videos can be found at our project page: https://vla-cache.github.io.

---

## 论文详细总结（自动生成）

<think>
The user wants me to analyze a paper about VLA-Cache and provide a structured Chinese summary. Let me organize the information from the abstract and metadata provided.

Key information from the paper:
- Title: VLA-Cache: Efficient Vision-Language-Action Manipulation via Adaptive Token Caching
- Focus: Training-free inference acceleration for VLA models
- Key method: Caching and reusing static visual tokens across frames
- Three main components:
  1. Identifying minimally changed tokens between adjacent frames and reusing cached KV representations
  2. Selectively re-computing task-relevant tokens (environmentally sensitive)
  3. Layer adaptive token reusing strategy based on attention concentration
- Experiments: LIBERO, SIMPLER (simulation), and real-world robotic system
- Results: Up to 1.7× speedup in CUDA latency, 15% increase in control frequency
- Negligible loss on task success rate
- NeurIPS 2025 Accepted

The PDF content I got is just a CAPTCHA page, so I need to rely on the metadata and abstract provided. I should note this limitation.

Let me write a comprehensive structured summary in Chinese.
</think>
# VLA-Cache 论文总结

> **说明**：原始 PDF 链接返回的是 OpenReview 的人机验证页面，未能直接获取正文内容。以下总结主要基于提供的元数据与摘要信息，部分章节（如算力细节、完整实验配置）受限于可见信息，已明确标注。

---

## 1. 核心问题与研究动机

- **背景**：视觉-语言-动作（Vision-Language-Action, VLA）模型能够以端到端的方式从视觉感知和语言指令直接生成机器人动作，展现出强大的多模态推理能力。
- **核心矛盾**：VLA 模型通常基于大规模 Transformer，**计算开销大、推理延迟高**，难以满足实时机器人控制系统对**毫秒级决策**的严格要求。
- **研究意义**：在保证动作生成质量（任务成功率）的前提下压缩推理时延，是 VLA 模型从实验室走向真实机器人部署的关键瓶颈。
- **关键观察（motivation）**：机器人操作任务具有**时序连续性**——相邻帧之间存在大量静态或近似静态的视觉 token，对其重复计算属于显著冗余。

---

## 2. 方法论：VLA-Cache

VLA-Cache 是一种**免训练（training-free）的推理加速框架**，核心思想是**自适应地缓存并跨帧复用视觉 token 的键值（KV）表征**。主要包含三层机制：

### 2.1 静态视觉 Token 的跨帧 KV 缓存与复用
- 对相邻两帧的视觉 token 进行**变化量度量**，识别出"**变化最小**"的 token 子集；
- 直接复用其**上一帧已缓存的 Key/Value 表征**，跳过当前帧的注意力计算；
- 充分利用机器人操作场景中**背景、机器人本体、桌面等静态区域**带来的计算冗余。

### 2.2 任务相关 Token 的选择性重计算
- 为避免因缓存造成对**环境敏感（environmentally sensitive）**信息（如被抓取物体、障碍物）的遗漏；
- **选择性地对任务关键 token 进行重新计算**，保障关键视觉信息的保真度，从而维持动作精度。

### 2.3 层自适应（Layer-Adaptive）Token 复用策略
- 不同 Transformer 解码层对不同 token 的关注程度（attention concentration）不同；
- 引入**层级自适应的复用率（reuse ratio）**：
  - 注意力更分散（更"全局"）的层 → 倾向于更高复用比；
  - 注意力更集中（更"局部/任务相关"）的层 → 优先对关键 token 进行重计算。
- 动态地在"复用"与"重算"之间做权衡，**最大化效率同时最小化对动作质量的扰动**。

### 2.4 整体流程（文字描述）
1. 输入当前帧视觉 token；
2. 与上一帧比较，划分"低变化 / 高变化"两组；
3. 低变化 token → 加载缓存 KV；高变化（任务相关）token → 重计算；
4. 依据当前层的注意力分布动态调整复用比例；
5. 拼接后进入后续层 / 输出动作头。

---

## 3. 实验设计

### 3.1 数据集 / 场景
- **仿真平台**：
  - **LIBERO**：常用的机器人操作仿真基准；
  - **SIMPLER**：另一仿真评测环境。
- **真实机器人系统**：在真实机器人平台上进行了实操验证。

### 3.2 Benchmark 与评测指标
- 评测维度包括：
  - **CUDA 推理延迟**（latency）；
  - **控制频率**（control frequency）；
  - **任务成功率**（task success rate）。
- 重点考察**加速比**与**任务性能损失**的权衡曲线。

### 3.3 对比方法
- 摘要中未明确列出所有 baseline（受限于 PDF 未获取完整正文）；
- 通常此类工作的对比基线包括：**原始 VLA 模型（无缓存）**、**均匀/固定比例 token 剪枝或缓存方法**等；
- 建议在阅读正文后补充完整对比表。

---

## 4. 资源与算力

- **未在可见摘要 / 元数据中明确说明**所用 GPU 型号、数量、训练/推理时长。
- 摘要仅给出加速结果层面的指标：
  - 最高 **1.7× CUDA 延迟加速**；
  - 控制频率提升 **约 15%**。
- 由于 VLA-Cache 是**免训练方法**，主要消耗在推理阶段，无需专门训练资源。
- 实际部署所用的硬件平台（GPU 型号、嵌入式设备等）需要查阅正文或附录确认。

---

## 5. 实验数量与充分性

- **可见实验范围**：
  - 2 个仿真平台（LIBERO + SIMPLER）；
  - 1 个真实机器人系统；
  - 涵盖延迟、控制频率、任务成功率三类指标。
- **充分性评价**：
  - **优点**：仿真 + 真实机器人双重验证，提高了结论的可靠性；延迟与任务性能并重，体现了"实用性"导向。
  - **可能的不足**（仅基于摘要推断）：
    - 是否做了**完整的消融实验**（仅缓存静态 token / 仅层自适应 / 完整三件套）尚不明确；
    - 是否在**多种 VLA backbone**（如 OpenVLA、RT-2、π0 等）上泛化测试未在摘要中提及；
    - 真实机器人实验中任务的多样性、扰动设置等细节需阅读正文确认。

---

## 6. 主要结论与发现

- VLA-Cache 在**不损失（或几乎不损失）任务成功率**的前提下，可实现：
  - 最高 **1.7× CUDA 延迟加速**；
  - 控制频率提升 **约 15%**。
- 验证了**机器人操作时序连续性**可被有效利用来减少 VLA 推理中的冗余计算。
- "**静态 token 缓存 + 任务相关 token 重算 + 层自适应复用率**"三件套是协同有效的。
- 为 VLA 模型在**实时机器人闭环控制**中的实际部署提供了**免训练、即插即用**的加速方案。

---

## 7. 优点与亮点

- **方法层面**：
  - **免训练**（training-free）：无需重新训练 VLA，对已有部署友好；
  - **自适应性**：既跨帧自适应选 token，也跨层自适应调复用率；
  - **保留关键信息**：通过"任务相关 token 重算"避免单纯缓存带来的精度损失；
- **实验层面**：
  - 同时覆盖**仿真 + 真实机器人**，具有较强的实践说服力；
  - 报告了**CUDA 延迟、控制频率、成功率**三维度指标，权衡分析较完整；
- **应用层面**：
  - 直接面向 VLA 实时部署痛点，**工程价值高**；
  - 提供了项目页与代码/视频，工程可复现性较好。

---

## 8. 不足与局限

- **可获取信息有限**：由于未能成功抓取 PDF 正文，**完整方法细节、全部消融实验、所有 baseline 列表、所使用的 GPU 资源**等关键信息缺失，需要参照正式论文。
- **Backbone 泛化性未知**：摘要未明确说明 VLA-Cache 在不同 VLA 主干网络（如 OpenVLA、RT-2、π0 等）上的表现是否一致。
- **任务多样性与扰动鲁棒性**：真实机器人实验中任务集规模、光照/遮挡/物体位置扰动等设置，需通过正文评估。
- **缓存策略的额外开销**：跨帧比较 token 变化、计算层注意力分布等步骤本身也会引入 CPU/IO 开销，在**极低算力嵌入式平台**上的端到端收益仍需验证。
- **对动态场景的假设依赖**：方法有效性的前提是"相邻帧存在大量静态区域"；在**高度动态、非结构化、视角剧烈变化**的场景下，复用率可能下降，加速效果可能打折。
- **可解释性与稳定性**：缓存与重算的边界由启发式规则决定，缺少对"何时缓存失败"的系统性分析。

---

（完）
