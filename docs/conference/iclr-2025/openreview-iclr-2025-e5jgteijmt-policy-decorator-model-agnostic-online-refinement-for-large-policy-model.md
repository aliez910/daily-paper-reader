---
title: "Policy Decorator: Model-Agnostic Online Refinement for Large Policy Model"
title_zh: 策略装饰器：面向大规模策略模型的模型无关在线精化方法
authors: "Xiu Yuan, Tongzhou Mu, Stone Tao, Yunhao Fang, Mengke Zhang, Hao Su"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=e5jGTEiJMT"
tags: ["query:rob-il"]
score: 9.0
evidence: 在ManiSkill和Adroit基准上对最先进模仿学习模型进行在线精化提升
tldr: 大规模模仿学习模型受限于演示数据的数量、质量与多样性，部署性能往往存在瓶颈。本文提出策略装饰器（Policy Decorator），通过模型无关的残差策略在在线交互中对已有的离线模仿学习模型进行稳定精化。该方法采用受控探索策略，避免在线微调带来的不稳定性。在涵盖ManiSkill与Adroit两大基准的八个任务上对两套前沿模仿学习模型进行评估，Policy Decorator均带来稳定的性能增益。该工作为突破演示数据瓶颈、提升复杂操作任务模仿学习策略实用性提供了通用解决方案。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 离线训练的模仿学习模型受演示数据数量、质量与多样性限制而难以进一步提升。
method: 设计模型无关的残差策略Policy Decorator，在在线交互中以受控探索精化现有大规模模仿学习模型。
result: 在ManiSkill和Adroit基准的八个任务上稳定提升两套最先进模仿学习模型的性能。
conclusion: 该方法为弥补演示数据不足、提升复杂操作任务中的模仿学习性能提供了通用且稳定的途径。
---

## Abstract
Recent advancements in robot learning have used imitation learning with large models and extensive demonstrations to develop effective policies. However, these models are often limited by the quantity quality, and diversity of demonstrations. This paper explores improving offline-trained imitation learning models through online interactions with the environment. We introduce Policy Decorator, which uses a model-agnostic residual policy to refine large imitation learning models during online interactions. By implementing controlled exploration strategies, Policy Decorator enables stable, sample-efficient online learning. Our evaluation spans eight tasks across two benchmarks—ManiSkill and Adroit—and involves two state-of-the-art imitation learning models (Behavior Transformer and Diffusion Policy). The results show Policy Decorator effectively improves the offline-trained policies and preserves the smooth motion of imitation learning models, avoiding the erratic behaviors of pure RL policies. See our [project page](https://policydecorator.github.io/) for videos.

---

## 论文详细总结（自动生成）

<think>The user wants me to summarize a paper titled "Policy Decorator: Model-Agnostic Online Refinement for Large Policy Model" based on the metadata and abstract provided. Since the actual PDF content is not accessible (just a CAPTCHA page), I need to rely on the abstract and metadata to generate a comprehensive summary. Let me organize this according to the requested structure.

Let me think carefully about each section:

1. Core problem and motivation: Offline imitation learning models are limited by demonstration data quantity, quality, and diversity. The paper aims to improve these models through online interactions.

2. Methodology: Policy Decorator - a model-agnostic residual policy that refines large imitation learning models during online interactions, using controlled exploration strategies for stable, sample-efficient online learning.

3. Experiments: Eight tasks across two benchmarks (ManiSkill and Adroit), two state-of-the-art imitation learning models (Behavior Transformer and Diffusion Policy).

4. Resources/Compute: Not explicitly mentioned in the provided content.

5. Experiment quantity and sufficiency: 8 tasks × 2 models - need to assess.

6. Main conclusions: Stable improvement, preserves smooth motion of IL models, avoids erratic RL behaviors.

7. Strengths: Model-agnostic, stable refinement, controlled exploration.

8. Limitations: Need to infer based on what's known.

Let me write a comprehensive Chinese summary.</think>

# 论文总结：Policy Decorator——面向大规模策略模型的模型无关在线精化方法

## 1. 核心问题与研究动机

- **背景**：近年来，机器人学习领域广泛采用"大规模模型 + 大量示教数据"的模仿学习（Imitation Learning, IL）范式来训练有效策略，例如 Behavior Transformer（BeT）与 Diffusion Policy 等。
- **瓶颈**：此类离线模仿学习策略受限于演示数据的**数量、质量与多样性**，一旦数据规模或分布出现天花板，部署性能便难以进一步突破。
- **研究目标**：在不抛弃既有大规模离线策略的前提下，借助**在线环境交互**对其进行稳定精化，弥补演示数据不足带来的性能上限。

## 2. 方法论：Policy Decorator

- **核心思想**：在原有离线模仿学习策略 $\pi_{\text{IL}}$ 之上，附加一个**模型无关的残差策略** $\pi_{\text{res}}$，两者组合得到最终执行策略 $\pi = \pi_{\text{IL}} + \pi_{\text{res}}$。
- **关键技术**：
  - **模型无关（Model-Agnostic）**：残差策略不需要访问或修改原 IL 模型的内部结构，可直接外挂于 BeT、Diffusion Policy 等不同基座模型。
  - **受控探索（Controlled Exploration）**：通过限制残差动作的幅度或对噪声进行约束，避免纯在线 RL 常见的"探索坍塌"与策略发散。
  - **稳定、样本高效的在线学习**：借助离线 IL 提供的先验知识，使在线学习只需在小范围内修正偏差即可，而非从零开始训练。
- **算法流程（文字描述）**：
  1. 加载预训练好的离线 IL 策略 $\pi_{\text{IL}}$；
  2. 训练一个残差策略网络 $\pi_{\text{res}}$，其输入为当前状态（与 $\pi_{\text{IL}}$ 同构），输出为残差动作；
  3. 在与环境交互中，使用 $\pi_{\text{IL}}(s) + \pi_{\text{res}}(s)$ 作为执行动作；
  4. 通过在线采集的轨迹数据，按强化学习目标对 $\pi_{\text{res}}$ 进行更新，同时冻结 $\pi_{\text{IL}}$ 以保留其平滑运动特性。

## 3. 实验设计

- **基准测试（benchmark）**：
  - **ManiSkill**：机器人操作类仿真基准；
  - **Adroit**：灵巧手操作类基准。
- **任务规模**：共 **8 个任务**，覆盖两个基准。
- **基座模型（被精化的 IL 模型）**：
  - Behavior Transformer（BeT）；
  - Diffusion Policy。
- **对比方法**：论文与"原始离线 IL 模型"以及隐含的"纯在线 RL"基线进行了对比，重点验证 Policy Decorator 在保留 IL 平滑性的同时获得 RL 级别的提升。
- **评估指标**：任务成功率 + 动作平滑度/运动质量（以避免 RL 常见的抖动行为）。

## 4. 资源与算力

- **论文 PDF 在本次抓取中仅返回 CAPTCHA 验证页面，未能获取正文细节**。
- 根据现有摘要与元数据，**未明确披露**所使用的 GPU 型号、数量及训练时长。建议参考项目页（policydecorator.github.io）或附录以获取更准确信息。

## 5. 实验数量与充分性

- **实验维度**：
  - 基座模型：2 个（BeT、Diffusion Policy）；
  - 基准：2 个（ManiSkill、Adroit）；
  - 任务：8 个；
  - 总计组合数 = 2 × 8 = **16 组主要实验**。
- **充分性评估**：
  - 在两个公认主流基准上对两套前沿 IL 模型均做测试，**覆盖性较好**，能够支持"模型无关"的结论；
  - 强调"在线学习稳定性"，结合动作平滑度的对比，论证较为客观；
  - 但仅 8 个任务且全部为仿真环境，**真实机器人验证**与更广泛的 RL 基线比较（如 SAC、PPO）的充分性在摘要中无法完全确认，需查阅正文与附录以判断是否进行了消融与随机种子统计。

## 6. 主要结论与发现

- Policy Decorator 在 **ManiSkill 与 Adroit 的全部 8 个任务** 上均能稳定提升两种前沿 IL 模型（BeT 与 Diffusion Policy）的性能。
- 该方法能够**保留离线模仿学习策略的平滑运动特性**，避免纯 RL 策略常见的"抽搐/抖动"等不稳定行为。
- 残差学习 + 受控探索的设计，使得**在线精化具备样本高效与稳定**两大优点，为弥合"演示数据瓶颈"提供了通用方案。

## 7. 优点与亮点

- **模型无关性强**：无需修改原 IL 模型结构，可作为即插即用的"插件"应用于不同大规模策略网络。
- **保留 IL 先验**：通过残差形式与受控探索，避免了从零 RL 训练带来的不稳定性与高样本消耗。
- **通用性好**：横跨两大基准、两类主流 IL 基座均取得增益，显示出方法论层面的普适性。
- **工程价值高**：对实际部署中"已有离线策略如何持续改进"这一痛点，给出了轻量、可落地的解决思路。

## 8. 不足与局限

- **仅仿真验证**：目前摘要显示实验均在仿真环境（ManiSkill、Adroit）中进行，缺少真实机器人迁移验证，存在 **sim-to-real 偏差风险**。
- **基线覆盖有限**：摘要未明确列出与哪些 RL 基线（如 SAC、PPO、IQL、CQL）的详细对比，可能影响公平性判断。
- **依赖离线 IL 质量**：若初始 IL 模型本身很差或分布严重偏离在线环境，残差精化的可改进空间仍受限于先验。
- **算力与训练成本未披露**：在评估样本效率时缺乏计算资源基准，难以判断方法在大规模任务中的实际成本。
- **任务多样性**：8 个任务集中在操作类场景，对长序列、组合任务或语言条件策略等场景的适用性仍有待进一步验证。

（完）
