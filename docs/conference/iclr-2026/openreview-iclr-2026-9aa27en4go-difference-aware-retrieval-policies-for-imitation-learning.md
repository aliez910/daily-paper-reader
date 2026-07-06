---
title: Difference-Aware Retrieval Policies for Imitation Learning
title_zh: 差异感知的检索式模仿学习策略
authors: "Quinn Pfeifer, Ethan Pronovost, Paarth Shah, Khimya Khetarpal, Siddhartha Srinivasa, Abhishek Gupta"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=9AA27en4go"
tags: ["query:rob-il"]
score: 7.0
evidence: 基于检索的半参数化模仿学习以提升分布外泛化能力
tldr: 针对参数化行为克隆方法在分布外状态泛化差、部署时误差累积的问题，本文提出差异感知检索策略DARP。该方法不再学习全局状态到动作的映射，而是基于k近邻对训练数据进行局部结构推理来预测动作，从而缓解部署中的误差累积现象。该半参数化方法为提升模仿学习策略的鲁棒性提供了一种有效机制。
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 参数化行为克隆在分布外状态泛化能力差，部署时易出现误差累积问题。
method: 提出DARP，基于训练样本的k近邻局部结构预测动作，采用半参数化检索方式。
result: 有效缓解了误差累积问题，提升了模仿学习策略在分布外场景下的鲁棒性。
conclusion: 基于局部结构的检索式策略为提升模仿学习泛化能力提供了一种有效机制。
---

## Abstract
Parametric imitation learning via behavior cloning can suffer from poor generalization to out-of-distribution states due to compounding errors during deployment. We show that reusing the training data during inference via a semi-parametric retrieval-based imitation learning approach can alleviate this challenge. We present Difference-Aware Retrieval Policies for Imitation Learning (DARP), a semi-parametric retrieval-based imitation learning approach that addresses this limitation by reparameterizing the imitation learning problem in terms of local neighborhood structure rather than direct state-to-action mappings. Instead of learning a global policy, DARP trains a model to predict actions based on k-nearest neighbors from expert demonstrations, their corresponding actions, and the relative distance vectors between neighbor states and query states. DARP requires no additional assumptions beyond those made for standard behavior cloning -- it does not require additional data collection, online expert feedback, or task-specific knowledge. We demonstrate consistent performance improvements of 15-46% over standard behavior cloning across diverse domains, including continuous control and robotic manipulation, and across different representations, including high-dimensional visual features.

---

## 论文详细总结（自动生成）

<think>
The user wants me to generate a detailed Chinese summary of the paper based on the provided metadata and abstract. Let me carefully analyze the content and structure my response according to the 8 points requested.

From the metadata and abstract, I can extract:

1. **Core problem**: Parametric behavior cloning suffers from poor OOD generalization and compounding errors
2. **Method**: DARP - semi-parametric retrieval-based imitation learning using k-nearest neighbors, distance vectors
3. **Experiments**: Continuous control, robotic manipulation, high-dimensional visual features; compared to standard behavior cloning
4. **Resources**: Not mentioned in the provided text
5. **Experimental count**: "consistent performance improvements of 15-46%" across diverse domains - but specific number of experiments not detailed
6. **Conclusions**: Alleviates compounding errors, improves OOD robustness
7. **Strengths**: No additional assumptions, no extra data, no online feedback, no task-specific knowledge needed
8. **Limitations**: Not explicitly stated in the provided content

I should note that the PDF content was just a CAPTCHA page, so I only have access to the metadata. I'll need to be honest about what can be inferred and what cannot.

Let me write a comprehensive Chinese summary following the requested structure.
</think>
# 论文总结：差异感知的检索式模仿学习策略（DARP）

## 1. 核心问题与研究动机

- **核心问题**：参数化行为克隆（Behavior Cloning, BC）在面对分布外（OOD）状态时泛化能力较差，且在部署过程中容易出现**误差累积（compounding errors）**问题。
- **问题根源**：传统参数化策略学习的是从状态到动作的**全局映射**，缺乏对训练数据局部结构信息的利用。当测试状态偏离训练分布时，全局模型无法依靠相似局部信息进行有效推理，导致错误逐步放大。
- **研究动机**：探索一种**半参数化（semi-parametric）**方法，在推理时直接复用训练数据，通过检索机制提升对未见状态的鲁棒性。

---

## 2. 方法论：Difference-Aware Retrieval Policies (DARP)

### 2.1 核心思想
- 不再学习一个全局的"状态→动作"映射，而是将模仿学习问题**重新参数化**为基于**训练样本局部邻域结构**的推理问题。
- 本质思想：与其"内插/外推"一个连续函数，不如在测试时检索与查询状态最相似的训练样本，并基于其局部结构预测动作。

### 2.2 关键技术细节
- **基于 k 近邻（k-NN）的检索机制**：给定查询状态，在训练数据集中检索其 k 个最近邻样本。
- **输入特征构造**：使用三类信息作为策略输入——
  1. 邻居状态；
  2. 邻居对应的动作；
  3. **邻居状态与查询状态之间的相对距离向量**（"差异感知"的来源）。
- **输出动作预测**：由一个学习模型（神经网络）综合上述局部信息输出最终动作，而非简单的均值/加权平均。
- **关键性质**：
  - 仅需标准 BC 的前提假设，无需额外数据采集；
  - 无需在线专家反馈；
  - 无需任务专属先验知识。

### 2.3 算法流程（文字描述）
1. 准备专家演示数据集；
2. 训练阶段：学习一个以（k 个邻居状态、邻居动作、相对距离向量）为输入、以真实动作为监督信号的策略网络；
3. 推理阶段：对每个查询状态，在训练集中检索 k-NN，输入策略网络，得到动作。

---

## 3. 实验设计

- **实验领域**：
  - 连续控制任务（continuous control）；
  - 机器人操控任务（robotic manipulation）。
- **输入表示**：
  - 状态向量（低维）；
  - 高维视觉特征（high-dimensional visual features）。
- **对比方法（Baseline）**：标准参数化行为克隆（standard behavior cloning）。
- **核心指标**：相对标准 BC 的性能提升幅度。

---

## 4. 资源与算力

- **论文提供的 PDF 文本仅包含 OpenReview 验证码页面**，未提取到正文内容。
- 因此**无法从所提供材料中确认**：
  - GPU 型号与数量；
  - 训练时长；
  - 算力消耗情况。
- 这一点需在获取完整 PDF 后进一步补充。

---

## 5. 实验数量与充分性

- **可确认信息**：
  - 论文报告在"多个不同领域"上获得了 **15%–46% 的稳定性能提升**；
  - 覆盖了不同输入模态（低维状态与高维视觉）。
- **不足**：
  - 由于正文未提取，**具体实验任务数量、消融实验设置、不同 k 值的影响、与更多基线（如 DAC、IBC、扩散策略等）的对比**等细节均无法从当前材料确认。
  - 现有信息难以客观判断实验是否充分覆盖了所有声称的场景。

---

## 6. 主要结论与发现

- **核心结论**：基于局部邻域结构的检索式半参数化策略能有效缓解 BC 的误差累积问题。
- **定量发现**：在多种连续控制、机器人操控任务以及不同表示（状态/视觉特征）下，DARP 一致性地比标准 BC 提升 **15%–46%**。
- **方法论启示**：将模仿学习从"全局函数拟合"视角转换为"局部结构推理"视角，可在不增加数据与监督的前提下显著提升鲁棒性。

---

## 7. 优点与亮点

- **方法层面**：
  - **结构新颖**：将检索机制引入模仿学习策略，强调"差异感知"以利用局部几何信息；
  - **半参数化设计**：兼顾神经网络的拟合能力与训练数据的显式记忆能力；
  - **假设最小化**：不引入额外数据、在线监督或任务先验，易于落地。
- **实验层面**（基于摘要可推断）：
  - 跨领域（控制+操控）、跨模态（状态+视觉）的双重验证；
  - 相对提升幅度较大且稳定（15%–46%），说明方法在多种场景下均有效。

---

## 8. 不足与局限

- **可从摘要推断的局限**：
  - **检索开销**：k-NN 在大规模数据集上推理时存在存储与最近邻搜索的开销问题，摘要未讨论其可扩展性；
  - **特征依赖**：检索质量依赖表示空间，视觉特征下的检索性能与表征学习方法紧密耦合；
  - **基线较少**：摘要仅与"标准 BC"对比，未说明是否与近期强基线（如扩散策略、Transformer BC、DAC 等）进行公平比较。
- **未明确说明的部分**（受限于无法获取正文）：
  - 是否进行消融实验（如不同 k 值、是否使用距离向量、不同骨干网络等）；
  - 是否在真实机器人上部署；
  - 计算资源、训练时长、超参数选择等细节；
  - 对失败案例或方法失效场景的分析。

---

（完）
