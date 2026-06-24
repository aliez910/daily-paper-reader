---
title: Object-Centric Latent Action Learning
title_zh: 以物体为中心的潜在动作学习
authors: "Albina Klepach, Alexander Nikulin, Ilya Zisman, Denis Tarasov, Alexander Derevyagin, Andrei Polubarov, Nikita Lyubaykin, Igor Kiselev, Vladislav Kurenkov"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39423/43384"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向操纵任务模仿学习的物体中心潜在动作学习
tldr: 本文针对从无标注视频中进行模仿学习时存在的动作标签缺失和视觉干扰问题，提出了一种以物体为中心的潜在动作学习框架。该方法通过自监督物体中心预训练，解耦智能体运动与背景干扰，从而提取更鲁棒的代理动作标签，提升模仿学习在复杂操纵任务中的性能。实验表明该方法在存在干扰的情况下显著优于基线，为利用海量互联网视频训练具身智能体提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39423/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 865, \"height\": 401, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39423/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1469, \"height\": 628, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39423/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 709, \"height\": 707, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39423/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1451, \"height\": 724, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39423/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1876, \"height\": 1056, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39423/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1839, \"height\": 819, \"label\": \"Table\"}]"
motivation: 现有方法在无标注视频中学习动作时易受背景干扰，导致模仿学习效果不佳。
method: 提出物体中心潜在动作学习框架，通过自监督物体中心预训练解耦智能体运动与背景动态，提升代理动作标签质量。
result: 在存在视觉干扰的场景下，该方法显著提高了模仿学习的鲁棒性和任务成功率。
conclusion: 物体中心视角能有效利用无标签视频进行模仿学习，为扩展机器人学习的数据来源提供可行方案。
---

## Abstract
Leveraging vast amounts of unlabeled internet video data for embodied AI is currently bottlenecked by the lack of action labels and the presence of action-correlated visual distractors. Although recent latent action policy optimization (LAPO) has shown promise in inferring proxy action labels from visual observations, its performance degrades significantly when distractors are present. To address this limitation, we propose a novel object-centric latent action learning framework that centers on objects rather than pixels. We leverage self-supervised object-centric pretraining to disentangle the movement of the agent and distracting background dynamics. This allows LAPO to focus on task-relevant interactions, resulting in more robust proxy-action labels, enabling better imitation learning and efficient adaptation of the agent with just a few action-labeled trajectories. We evaluated our method in eight visually complex tasks across the Distracting Control Suite (DCS) and Distracting MetaWorld (DMW). Our results show that object-centric pretraining mitigates the negative effects of distractors by 50%, as measured by downstream task performance: average return (DCS) and success rate (DMW).

---

## 论文详细总结（自动生成）

# 论文总结：《Object-Centric Latent Action Learning》（以物体为中心的潜在动作学习）

## 1. 核心问题与整体含义（研究动机和背景）

- **问题根源**：互联网视频数据虽然丰富，但缺乏动作标签，且存在与动作相关的视觉干扰（如动态背景、相机抖动、颜色变化），导致现有的从观测中学习潜在动作的方法（如 LAPO）在干扰下性能严重退化。
- **核心目标**：提出一种以物体为中心的潜在动作学习框架，利用自监督物体中心预训练解耦智能体运动与干扰背景动态，从而提取更鲁棒的代理动作标签，使得仅需极少有标注轨迹即可高效模仿学习。
- **整体含义**：为利用海量无标签互联网视频训练具身智能体提供了可行且鲁棒的解决方案，降低了具身 AI 对精确动作标注的依赖。

## 2. 方法论

### 核心思想
- 以物体为中心的表示（object-centric representations）能天然隔离任务相关实体与背景干扰，通过将原始像素空间分解为离散、可解释的物体槽（slots），使潜在动作模型聚焦于因果动态而非伪相关。

### 关键技术细节
- **物体中心预训练**：采用 VideoSAUR 模型（Zadaianchuk et al., 2023）将视频帧分解为 K 个时空物体槽。每个槽对应一个实体，并可投影回像素空间得到注意力掩码（masks）。通过固定槽初始化提高跨 episode 的一致性。
- **自动槽选择（Linear Action Probe）**：基于少量有标签轨迹，对各槽表示做 PCA 降维后训练线性回归器预测真实动作，以 5 折交叉验证的 MSE 作为打分，选出预测性最强的槽集合 S⋆。该方法可自动识别控制相关实体，无需手动标注。
- **潜在动作学习**：基于 LAPO（Schmidt & Jiang, 2024）训练潜在动作模型。两种具体实现：
  - **LAPO-slots**：直接在选出的槽嵌入空间上训练逆动态模型（IDM）和前向动态模型（FDM），优化目标为最小化下一时刻嵌入的 MSE。
  - **LAPO-masks**：利用选出的槽掩码过滤原图（得到仅含相关物体的图像），在像素级重建任务中训练 IDM 和 FDM。
- **行为克隆与微调**：利用推断出的潜在动作训练 BC 策略，再基于极少量（≤2.5%）有真实动作标签的轨迹微调，实现对下游任务的快速适应。

## 3. 实验设计

### 数据集与环境
- **Distracting Control Suite (DCS)**：包含四种运动任务（cheetah-run, walker-run, hopper-hop, humanoid-walk），干扰包括动态背景（DAVIS 2017 视频）、颜色变化、相机扰动；其中 DCS-Hard 使用全部三种干扰。
- **Distracting MetaWorld (DMW)**：新引入的基准，在 MetaWorld 四个操作任务（hammer, bin-picking, basketball, soccer）上叠加 DCS 风格动态背景，涉及多物体交互与组合推理。

### Benchmark 与对比方法
- **基线方法**：
  - LAPO（原始方法，在含干扰数据上训练）
  - LAPO-clean（上界，在干净无干扰数据上训练）
- **提出方法**：
  - LAPO-slots（利用物体槽嵌入）
  - LAPO-masks（利用物体掩码过滤图像）
- **评估指标**：
  - DCS：标准化回报（normalized return，以完整真实动作 BC 为 1）
  - DMW：标准化成功率（normalized success rate）

### 实验设置
- 每个任务三种随机种子，微调使用的有标签轨迹数量从 0.1% 到 2.5% 不等（DCS: 4-128 条, DMW: 32-512 条）。
- 额外进行槽选择有效性分析（K=4 与 K=15 下的槽排序与下游性能）、不同槽数 K 的鲁棒性（K=2~15）以及干扰难度递增下的表现（DCS vs. DCS-Hard）。

## 4. 资源与算力

- **明确说明**：论文正文及附录中未明确报告 GPU 型号、数量或具体训练时长。
- **推断与说明**：方法基于 VideoSAUR 和 LAPO 训练，两者均需要一定的算力支持，但具体的计算资源消耗信息缺失。因此需要指出：论文**未提及具体算力资源**，读者无法据此评估复现成本。

## 5. 实验数量与充分性

- **实验规模**：覆盖 8 个任务（DCS 4 个 + DMW 4 个），每个任务 3 个随机种子，微调轨迹数量多档。主要结果表（Table 1）汇总了平均性能。
- **充分性分析**：
  - 消融/分析实验丰富：包括槽选择自动相关性验证（图 5a-d）、不同槽数 K 的鲁棒性测试（图 5e）、干扰难度增加下的表现对比（图 1 及 Section “Increasing distractions difficulty”）。
  - 均报告方差或置信区间，且对上界（clean）和下界（distracted baseline）进行了对比，公平性良好。
  - 但仍存在局限：所有实验均在模拟器中完成，未涉及真实机器人数据或真实互联网视频；环境干扰模式相对结构化（背景视频、颜色偏移、相机抖动），可能不能完全代表真实世界复杂干扰。

## 6. 主要结论与发现

- **物体中心预训练可显著缓解干扰影响**：在 DCS 和 DMW 上，LAPO-slots 和 LAPO-masks 将 LAPO 与 LAPO-clean 之间的性能差距缩小约 50%（Table 1），复杂任务如 humanoid-walk 的提升高达 +174%。
- **自动槽选择有效且与下游性能强相关**：线性动作探针的打分能够准确识别控制相关槽；槽选择的结果与 BC 后的成功率高度相关（图 5d），可作为无需手动标注的槽选取准则。
- **对槽数 K 的选择鲁棒**：在 DMW 上 K 从 2 到 15 均能稳定超越 LAPO 基线（图 5e），表明方法对预训练超参数不敏感。
- **LAPO-slots 比 LAPO-masks 在更复杂干扰下更鲁棒**：DCS-Hard 中 LAPO-slots 仍保持 52% 的差距缩小率，而 LAPO-masks 降至 26%，归因于 VideoSAUR 内置 DINOv2 编码器对视觉外观变化更具鲁棒性。

## 7. 优点

- **方法创新性**：首次将物体中心表征与潜在动作学习系统结合，利用了 OCL 的因果解耦能力解决视觉干扰问题，思路新颖。
- **自动槽选择机制**：基于线性探针的方法简单有效，无需人工标注或密集调参，增强了可复用性。
- **实验设计全面**：覆盖多种干扰类型、多个任务、多档微调预算，且进行了槽选择、槽数鲁棒性、干扰难度等多维度分析，结果可信度高。
- **性能提升显著且稳定**：在 8 个任务上一致超越 LAPO 基线，部分任务接近上界，且优势随干扰增强而保持，证明方法的通用性。
- **开源性**：提供代码链接（GitHub），便于复现和后续研究。

## 8. 不足与局限

- **依赖物体中心模型的性能**：方法有效性受限于底层 OCL 模型（VideoSAUR）的能力。当前 OCL 仍存在槽数固定、缺乏记忆机制、无法处理频繁出入场等问题，限制在复杂真实场景的迁移。
- **实验限于模拟器**：未在真实机器人或真实互联网视频上验证，对真实世界干扰（如光照突变、部分遮挡、多视角）的鲁棒性未知。
- **数据多样性不足导致槽坍塌**：如在 DMW 中，因轨迹多样性有限，VideoSAUR 将机械臂与目标物体合并为一个槽，虽然仍能分离干扰，但丢失了细粒度物体分离能力。在数据更复杂的真实场景中，该问题可能加剧。
- **计算资源未报告**：缺乏训练效率与复现成本的透明度，难以评估方法的经济可行性。
- **弱监督或无监督约束有限**：自动槽选择仍需少量有标签轨迹（用于线性探针），虽然量极少，但仍不属于完全无监督场景。对于完全无任何标签的互联网视频，该方法需进一步调整。

---

（完）
