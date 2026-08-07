---
title: Data Scaling Laws in Imitation Learning for Robotic Manipulation
title_zh: 机器人操纵模仿学习中的数据缩放规律
authors: "Fanqi Lin, Yingdong Hu, Pingyue Sheng, Chuan Wen, Jiacheng You, Yang Gao"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=pISLZG7ktL"
tags: ["query:rob-il"]
score: 9.0
evidence: 对机器人操纵模仿学习中数据缩放规律的全面实证研究
tldr: 数据缩放规律已推动NLP与视觉的飞跃，但在机器人操纵模仿学习中尚缺乏系统研究。为此，论文开展大规模实证研究，分析训练环境数量、物体类别和演示数据量对模仿策略泛化能力的影响，并收集超过22000条演示数据。实验揭示了显著的缩放规律，使得单任务策略可在同类任意物体和环境零样本部署，为机器人模仿学习的规模化研究奠定了重要基准和方法论指导。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 模仿学习在机器人操纵中的扩展能力尚未得到系统化研究，是否存在类似NLP与视觉的数据缩放规律尚不清楚。
method: 开展跨大量环境、物体和演示规模的系统化实证研究，收集超过22000条演示数据。
result: 发现显著的数据缩放规律，使单任务策略可在同类任意物体和环境实现零样本部署。
conclusion: 该工作为机器人操纵模仿学习的规模化提供了重要基准与指导原则。
---

## Abstract
Data scaling has revolutionized fields like natural language processing and computer vision, providing models with remarkable generalization capabilities. In this paper, we investigate whether similar data scaling laws exist in robotics, particularly in robotic manipulation, and whether appropriate data scaling can yield single-task robot policies that can be deployed zero-shot for any object within the same category in any environment. To this end, we conduct a comprehensive empirical study on data scaling in imitation learning. By collecting data across numerous environments and objects, we study how a policy’s generalization performance changes with the number of training environments, objects, and demonstrations. Throughout our research, we collect over 40,000 demonstrations and execute more than 15,000 real-world robot rollouts under a rigorous evaluation protocol. Our findings reveal several intriguing results: the generalization performance of the policy follows a roughly power-law relationship with the number of environments and objects. The diversity of environments and objects is far more important than the absolute number of demonstrations; once the number of demonstrations per environment or object reaches a certain threshold, additional demonstrations have minimal effect. Based on these insights, we propose an efficient data collection strategy. With four data collectors working for one afternoon, we collect sufficient data to enable the policies for two tasks to achieve approximately 90\% success rates in novel environments with unseen objects.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of a paper based on the provided metadata and abstract. The paper is about data scaling laws in imitation learning for robotic manipulation. Let me analyze the information provided:

From the metadata:
- Title: "Data Scaling Laws in Imitation Learning for Robotic Manipulation"
- Authors: Fanqi Lin, Yingdong Hu, Pingyue Sheng, Chuan Wen, Jiacheng You, Yang Gao
- Date: 2025-01-22
- ICLR 2025 Accepted
- Score: 9.0
- Key findings: Power-law relationships with environments and objects; diversity more important than absolute number of demos; efficient data collection strategy proposed

From the abstract:
- Investigates whether data scaling laws exist in robotic manipulation
- Studies generalization with number of training environments, objects, and demonstrations
- Collected over 40,000 demonstrations and executed more than 15,000 real-world robot rollouts
- Findings: power-law relationship, diversity matters more, threshold effect for demonstrations
- Proposes efficient data collection strategy
- Four data collectors in one afternoon can collect sufficient data for two tasks achieving ~90% success rates

Important note: The metadata says "超过22000条演示数据" but the abstract says "over 40,000 demonstrations and more than 15,000 real-world robot rollouts". I should note this discrepancy and rely on the abstract.

Let me write the summary now in Chinese, structured according to the requirements.

For computing resources: The paper doesn't explicitly mention GPU specs in the provided text. I should note this.

For experiments: They collected 40,000+ demonstrations and ran 15,000+ real-world rollouts. This is a fairly comprehensive empirical study.

Let me structure the response:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

I'll write this in Chinese with Markdown formatting.</think>

# 《机器人操纵模仿学习中的数据缩放规律》论文总结

## 一、论文核心问题与研究动机

- **核心问题**：在自然语言处理（NLP）和计算机视觉（CV）领域，数据缩放规律（scaling laws）已被证实能显著提升模型的泛化能力。然而在机器人操纵（robotic manipulation）领域的模仿学习（imitation learning）中，**是否存在类似的数据缩放规律尚不明确**。
- **研究目标**：探究模仿学习策略的泛化性能如何随训练环境数量、物体类别数量、演示数据量的变化而变化，并验证通过恰当的数据缩放，**能否训练出可在同类任意物体与任意环境中零样本（zero-shot）部署的单任务策略**。
- **研究意义**：填补机器人模仿学习缩放规律研究的空白，为机器人数据采集策略与策略泛化能力研究提供系统性基准与方法论指导。

---

## 二、方法论：核心思想与技术细节

- **核心思想**：开展大规模、系统化的实证研究，通过控制变量分析**环境数量、物体类别数量、每环境/物体的演示次数**三者对模仿学习策略泛化性能的影响，识别其中的缩放模式。
- **关键技术路线**：
  1. **数据维度划分**：将训练数据规模分解为三个独立维度——环境数（environments）、物体数（objects）、每环境/物体的演示数（demonstrations per environment/object）。
  2. **泛化性能建模**：通过改变每个维度的数据量来训练策略，测量在未见过的环境与未见过的同类物体上的成功率。
  3. **缩放关系识别**：将泛化性能与各数据维度进行曲线拟合，识别潜在的幂律（power-law）关系。
  4. **高效采集策略**：基于发现的规律，提出优化的数据采集策略——**优先增加环境与物体的多样性，而非盲目增加单一环境/物体的演示数量**。
- **算法/公式层面**：核心结论以**幂律关系**描述：策略泛化性能（如成功率）随环境数和物体数的增长呈近似幂律关系（power-law），而当每环境/物体的演示数达到一定阈值后，进一步增加演示对性能的边际增益极小。

---

## 三、实验设计

- **数据规模**：收集 **超过 40,000 条演示数据**（注意：元数据中提到的"超过 22,000 条"与摘要存在出入，应以摘要为准），并执行 **超过 15,000 次真实机器人回合（real-world rollouts）**。
- **任务设置**：针对机器人操纵任务（具体为元数据提到的"两个任务"），在多种真实环境与多种同类物体下采集演示与评估。
- **评估协议**：
  - 采用**严格的评估协议**（rigorous evaluation protocol），区分**已见 vs. 未见环境**、**已见 vs. 未见物体**。
  - 重点评估**零样本泛化能力**（即在未见过的环境与同类未见物体上测试）。
- **对比基线**：未在摘要中明确列出具体基线方法；研究侧重于**控制变量式的自我对比**（不同数据规模组合下的策略性能对比）。
- **基准（benchmark）**：本研究本身即为机器人模仿学习缩放规律提供了新的**实证基准**。

---

## 四、资源与算力

- **算力信息**：摘要与元数据中**未明确说明**所使用的 GPU 型号、数量、训练时长等算力细节。
- **数据采集资源**：摘要提到**由 4 名数据采集人员（four data collectors）花一个下午即可采集足够数据**，使两个任务的策略在未见环境中达到约 **90% 的成功率**——这表明该方法的采集成本相对可控。
- **真实机器人执行**：执行超过 15,000 次真实机器人回合，反映了较大的硬件投入与实验周期。

---

## 五、实验数量与充分性

- **实验数量**：
  - 数据维度涵盖环境数、物体数、演示次数三个维度的系统性变化。
  - 超过 40,000 条演示 + 超过 15,000 次真实机器人评估。
- **充分性评估**：
  - 实验规模**极为庞大**，是机器人模仿学习领域罕见的系统性实证研究。
  - 采用控制变量方法，维度划分清晰。
- **客观性与公平性**：
  - 使用严格的评估协议，结果具有较高可信度。
  - 由于未在摘要中详细列出对比算法与具体的统计检验方法，**外部对比的公平性有待正文进一步验证**。

---

## 六、主要结论与发现

1. **幂律缩放关系**：策略的泛化性能与环境数量、物体类别数量之间呈**近似幂律关系（power-law）**——这与 NLP/CV 中的观察一致。
2. **多样性优先**：**环境与物体的多样性远比演示的绝对数量更重要**。
3. **演示饱和效应**：当每环境或每物体的演示数达到**某一阈值后**，继续增加演示对性能的提升**微乎其微**。
4. **高效采集策略**：基于上述规律提出的数据采集策略极为高效——**4 名采集员 1 个下午的采集量**即可让两个任务策略在未见环境与未见物体上达到约 **90% 的成功率**。

---

## 七、优点与亮点

- **填补研究空白**：是**首个**在机器人模仿学习领域系统验证数据缩放规律的大规模实证研究。
- **大规模数据支撑**：40,000+ 演示与 15,000+ 真实机器人回合使结论具有较强统计效力。
- **反直觉的实用洞察**："多样性优于数量"的结论对机器人数据采集实践具有直接指导意义，能大幅降低数据采集成本。
- **高效采集策略的可操作性**：所提出的策略可在**极短时间内（一个下午）由少量人员**完成，对工业界与学术界均有参考价值。
- **为零样本部署提供路径**：证明通过恰当的数据缩放，单任务策略可在同类任意物体与任意环境中实现零样本部署。

---

## 八、不足与局限

- **算力信息缺失**：未在摘要中披露 GPU 型号、数量、训练时长等关键算力细节，难以复现与对比成本。
- **任务与物体类别覆盖有限**：摘要重点提到"两个任务"，是否能在更广泛的任务类型（如长时序任务、双臂操作、柔性物体等）上验证缩放规律仍未知。
- **仿真与真实差距**：仅基于真实机器人实验，**未涉及仿真到真实（sim-to-real）迁移**场景；不同机器人平台（夹爪、灵巧手、移动底盘等）的泛化性未讨论。
- **基线对比缺失**：摘要未明确列出与现有模仿学习方法（如 Diffusion Policy、ACT、RT-1/2 等）的对比，难以判断其相对于 SOTA 的优势。
- **物体类别语义范围未细化**："同类任意物体"的具体类别边界（如刚性 vs. 软体、对称 vs. 非对称、形态多样性）未在摘要中说明。
- **元数据与摘要数据不一致**：元数据标注"超过 22,000 条演示数据"，摘要却写"超过 40,000 条"，需以正文为准，可能反映不同实验阶段的统计。
- **应用限制**：聚焦于"单任务"策略，**多任务/多技能的联合缩放规律**尚未涉及。

（完）
