---
title: "Learning What to Do and What Not To Do: Offline Imitation from Expert and Undesirable Demonstrations"
title_zh: 知所当行与知所不当行：基于专家与不良演示的离线模仿学习
authors: "Huy Hoang, Tien Anh Mai, Pradeep Varakantham, Tanvi Verma"
date: 2025-09-19
pdf: "https://openreview.net/pdf?id=IqlKCjLyYd"
tags: ["query:rob-il"]
score: 5.0
evidence: 结合专家与不良演示的离线模仿学习
tldr: 本文研究利用专家演示与不良演示的对比行为进行离线模仿学习，提出一种新的优化KL散度差的公式，并证明在专家数据占优时目标函数具有凸性。该方法避免了对抗训练，训练稳定且实用，但主要聚焦于离线模仿学习的理论框架，并未专门针对视觉机器人操纵任务。其贡献为离线模仿学习提供了一种通用、稳定的方法论，对机器人操纵中的模仿学习也具备一定的方法迁移价值。
source: ICLR-2026-Rejected-Public
selection_source: conference_retrieval
motivation: 离线模仿学习常忽略不良行为中的有价值信号。
method: 提出KL散度差优化公式，在专家数据占优条件下具有凸性，实现稳定非对抗训练。
result: 为包含正负演示的离线模仿学习提供理论与算法支持。
conclusion: 扩展了离线模仿学习可利用的数据信号范围。
---

## Abstract
Offline imitation learning typically learns from expert and unlabeled demonstrations, yet often overlooks the valuable signal in explicitly undesirable behaviors. In this work, we study offline imitation learning from contrasting behaviors, where the dataset contains both expert and undesirable demonstrations. We propose a novel formulation that optimizes a difference of KL divergences over the state-action visitation distributions of expert and undesirable (or bad) data. Although the resulting objective is a DC (Difference-of-Convex) program, we prove that it becomes *convex* when expert demonstrations outweigh undesirable demonstrations, enabling a practical and stable non-adversarial training objective. Our method avoids adversarial training and handles both positive and negative demonstrations in a unified framework. Extensive experiments on standard offline imitation learning benchmarks demonstrate that our approach consistently outperforms state-of-the-art baselines.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper based on the provided metadata and abstract. Since the actual PDF content is not accessible (CAPTCHA blocked), I need to rely on the metadata, abstract, and the structured information provided. Let me organize the summary according to the 8 required points.

Key information from the materials:
- Title: "Learning What to Do and What Not To Do: Offline Imitation from Expert and Undesirable Demonstrations"
- Topic: Offline imitation learning using both expert and undesirable (bad) demonstrations
- Method: Optimizes difference of KL divergences over state-action visitation distributions; DC program that becomes convex when expert data outweighs bad data; non-adversarial training
- Experiments: Standard offline imitation learning benchmarks; outperforms SOTA baselines
- Source: ICLR 2026 rejected (public)
- Score: 5.0
- Motivation: Undesirable behaviors contain valuable signal that is often overlooked

Since the full paper text is not available, I should be transparent about this and base the summary on available information while clearly noting where details are limited.
</think>
# 论文总结：知所当行与知所不当行——基于专家与不良演示的离线模仿学习

> 注：原文 PDF 因 OpenReview 验证码限制未能获取完整正文，以下总结主要依据论文摘要与元数据进行，细节有限之处已明确标注。

---

## 1. 核心问题与研究动机

- **背景**：离线模仿学习（Offline Imitation Learning, Offline IL）通常利用专家演示及大量未标注数据进行策略学习，但**常常忽略明确标注的不良（undesirable / bad）行为**中所蕴含的有价值信号。
- **核心问题**：如何同时从**正例（专家演示）和负例（不良演示）**的对比行为中进行离线模仿学习，使策略既知道"该做什么"，也清楚"不该做什么"。
- **研究意义**：将不良演示从"被丢弃的噪声"转化为"显式监督信号"，扩展离线模仿学习可利用的数据形态。

---

## 2. 方法论

- **核心思想**：提出一种新的优化目标——在**专家与不良数据的状态-动作访问分布（state-action visitation distribution）**上，最小化**两个 KL 散度之差**（Difference of KL Divergences），即：
  - 拉近策略分布与专家分布的距离；
  - 推远策略分布与不良分布的距离。
- **理论性质**：
  - 该目标本身是一个 **DC（Difference-of-Convex）规划问题**，通常为非凸、难优化；
  - 论文**证明了在专家演示数据量占优**（expert demonstrations outweigh undesirable demonstrations）的条件下，目标函数退化为**凸优化问题**，从而获得稳定、可解的训练目标。
- **算法特点**：
  - **非对抗训练**（non-adversarial），区别于 GAIL 系对抗方法；
  - 统一框架同时处理正、负演示；
  - 训练稳定，避免了对抗学习中的模式崩溃与不稳定性问题。

---

## 3. 实验设计

- **数据集 / Benchmark**：使用**标准的离线模仿学习基准**（根据元数据，未给出具体名称，推测包含 D4RL 系列或类似 MuJoCo 运动控制任务）。
- **对比方法**：与多种**当前最优（SOTA）基线**进行对比，但具体方法名未在可获取的文本中列出。
- **评估指标**：以策略性能（累积回报）为主，比较所提方法与基线在标准 Offline IL 任务上的表现。

---

## 4. 资源与算力

- 可获取的文本**未明确提及**所用 GPU 型号、数量、训练时长等计算资源信息。
- 此处无法评估其训练成本与可复现性对算力的依赖。

---

## 5. 实验数量与充分性

- 元数据显示论文包含**大量实验（"Extensive experiments"）**，但具体实验组数、消融研究的设置细节因 PDF 受限**无法精确统计**。
- **客观性**：作者声称在多个标准 Offline IL 基准上一致优于 SOTA 基线，初步可视为对方法有效性的较充分验证，但仍需阅读正文确认：
  - 是否在**不同比例的正负样本**下验证了"专家数据占优"假设；
  - 是否做了**超参数敏感性分析**与**消融实验**。

---

## 6. 主要结论与发现

- 提出了一种基于**KL 散度差**的 Offline IL 优化框架，统一利用正负演示；
- 证明了在专家数据占优的条件下，目标函数具有**凸性**，使训练可解且稳定；
- 该方法**避免了对抗训练**，简化了优化过程；
- 在标准 Offline IL 基准上**一致优于 SOTA 基线**。

---

## 7. 优点

- **理论贡献突出**：将负例引入模仿学习框架，并给出 DC 程序的凸性条件，理论分析清晰。
- **方法简洁实用**：非对抗训练，避免了 GAIL 类方法调参困难、训练不稳定的问题。
- **统一框架**：将正、负演示纳入同一目标函数，扩展了离线模仿学习的数据利用范围。
- **方法论迁移价值**：对机器人操纵等需要显式避免不良行为的模仿学习任务有潜在迁移意义。

---

## 8. 不足与局限

- **理论假设较强**：凸性结论依赖"专家数据量占优"假设，**在专家数据稀缺、负例占优的实际场景中难以保证**，限制了方法的适用边界。
- **应用场景有限**：摘要与元数据表明，该工作**主要聚焦于离线模仿学习的理论框架**，未针对视觉机器人操纵任务进行专门验证，**与机器人实际部署之间存在距离**。
- **实验细节不透明**：受 CAPTCHA 限制无法获取完整实验细节，可能存在的数据集覆盖度、对照基线选择公平性、消融完整性等问题需进一步核实。
- **偏差风险**：声称"一致优于 SOTA"但缺乏对失败案例与边界条件的分析，可能存在选择性报告（selective reporting）的风险。
- **可复现性未知**：未提供算力、代码、超参数等关键信息，难以评估复现成本。

---

（完）
