---
title: "Localizing, Structuring, and Rendering: Bridging 3D and 2D Vision-Language-Action Models for Robotic Manipulation"
title_zh: 定位、结构化与渲染：桥接3D与2D视觉语言动作模型的机器人操作
authors: "Zhao, Yunlong, Deng, Xiaoheng, Cao, Yichao, Chen, Yi, He, Xiangjian, You, Shan, Yang, Shuo, Fan, Lei, Wang, Fei, Su, Xiu"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhao_Localizing_Structuring_and_Rendering_Bridging_3D_and_2D_Vision-Language-Action_Models_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过可微分渲染桥接3D与2D视觉语言动作模型，实现端到端机器人操作
tldr: 三维机器人操作既需要空间几何推理，也需要直观语义感知，但现有3D与2D VLA范式各有所长。本文提出DiffRender-VLA，通过可微分渲染在两种范式间建立梯度一致的视觉中介，定位末端执行器位姿并生成可微分图像。该框架以端到端方式统一了几何推理与图像级语义连续性，为复杂三维机器人操作提供了新的VLA建模思路。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1766, \"height\": 783, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1812, \"height\": 936, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1798, \"height\": 1002, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1805, \"height\": 815, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 845, \"height\": 672, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 868, \"height\": 1014, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 880, \"height\": 737, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 858, \"height\": 386, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1787, \"height\": 679, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 543, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-localizing-structuring-and-rendering-bridging-3d-and-2d-vision-language-action-models-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 283, \"label\": \"Table\"}]"
motivation: 3D VLA缺乏直观语义理解，2D VLA缺乏显式空间接地，难以兼顾。
method: 提出可微分渲染框架DiffRender-VLA，通过视觉中介统一3D与2D VLA。
result: 在复杂三维操作场景下实现几何与语义的协同决策。
conclusion: 该工作为端到端VLA模型融合空间推理与视觉语义提供了新范式。
---

## Abstract
Robotic manipulation in complex 3D environments requires unifying spatial reasoning with intuitive visual perception, which is a capability that current Vision-Language-Action paradigms address separately. While 3D VLAs excel in geometric and physical reasoning, they lack intuitive, image-level understanding and dense visual semantics; conversely, 2D VLAs (even with depth image) provide rich visual intuition and semantic continuity but miss explicit spatial global grounding. We introduce DiffRender-VLA, a differentiable rendering-based framework that bridges 3D and 2D Vision-Language-Action models through gradient-consistent visual mediation. It generates differentiable images by localizing the next end-effector target with a world-aligned cube marker, differentiably structuring surrounding geometry whose color encodes spatial relations to the marker, and rendering adaptive viewpoints optimized to reveal the target-environment spatial relationships. These differentiable images serve as visual bridges, embedding spatial semantics while allowing gradients from 2D VLAs to backpropagate into 3D representations, thereby coupling geometric reasoning with visual perception. This closed differentiable loop unifies reasoning and perception, substantially improving performance under occlusion, clutter, and complex spatial manipulation tasks, achieving average improvements of +12.1% over state-of-the-art methods. Codes are available at https://github.com/zyl123456aB/DIFFVLA.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a CVPR 2026 paper titled "Localizing, Structuring, and Rendering: Bridging 3D and 2D Vision-Language-Action Models for Robotic Manipulation" (DiffRender-VLA). Let me analyze the provided content carefully.

From the metadata and abstract, I can extract:

1. **Core problem**: Robotic manipulation in 3D environments requires both spatial reasoning and visual perception. Current VLA models split into two paradigms:
   - 3D VLAs: good at geometric/physical reasoning but lack intuitive image-level understanding
   - 2D VLAs: rich visual intuition and semantic continuity but miss explicit spatial grounding

2. **Method**: DiffRender-VLA - a differentiable rendering-based framework that bridges 3D and 2D VLAs through gradient-consistent visual mediation. It:
   - Localizes next end-effector target with a world-aligned cube marker
   - Differentiably structures surrounding geometry with color encoding spatial relations to the marker
   - Renders adaptive viewpoints optimized to reveal target-environment spatial relationships
   - Creates differentiable images that serve as visual bridges
   - Allows gradients from 2D VLAs to backpropagate into 3D representations
   - Creates a closed differentiable loop

3. **Results**: +12.1% average improvement over SOTA, performs well under occlusion, clutter, and complex spatial manipulation tasks.

4. **Code**: Available at https://github.com/zyl123456aB/DIFFVLA

However, I notice the PDF text was not actually extracted - only the metadata and abstract are provided. So I need to be careful about what I can claim with certainty:
- The abstract provides good detail on motivation and method
- I have table and figure references but no actual content
- I cannot determine specific datasets, benchmarks, baselines, compute resources, or detailed experimental results from the provided content

I should note these limitations in my summary where appropriate, being honest about what I can and cannot determine from the given materials.

Let me structure the summary according to the user's requested 8 points, being careful to:
- Use clear hierarchical Markdown formatting
- Be honest about what is known from the abstract vs. what I cannot determine
- Keep the language concise but informative
- End with "（完）"

Let me draft this now.
</think>
# 论文总结：DiffRender-VLA — 桥接 3D 与 2D 视觉-语言-动作模型的机器人操作

## 1. 核心问题与研究动机

- **研究场景**：复杂三维环境下的机器人操控（robotic manipulation）。
- **关键矛盾**：空间推理与视觉感知难以在单一 VLA（Vision-Language-Action）范式中同时兼顾。
  - **3D VLA**：擅长几何与物理推理，但缺乏直观的图像级语义理解与稠密视觉语义。
  - **2D VLA**（即便引入深度图）：具备丰富的视觉直觉与语义连续性，但缺少显式的空间全局接地（spatial grounding）。
- **目标**：建立一种端到端可微的统一框架，使 3D 几何推理与 2D 图像级语义能够协同工作。

## 2. 方法论：DiffRender-VLA 核心思想与关键技术

- **核心范式**：以**可微分渲染（Differentiable Rendering）**作为视觉中介，桥接 3D 与 2D VLA，建立梯度一致的闭环。
- **三大关键步骤**（即论文标题的"定位—结构化—渲染"）：
  1. **定位（Localizing）**：在世界坐标系下放置一个与下一末端执行器（end-effector）目标对齐的**立方体标记（cube marker）**。
  2. **结构化（Structuring）**：以**可微方式**对周围几何进行结构化处理，并使用**颜色编码各部分与标记之间的空间关系**。
  3. **渲染（Rendering）**：渲染出**自适应视角**的图像，以最大化揭示目标—环境之间的空间关系。
- **可微桥梁作用**：
  - 渲染得到的可微图像（differentiable images）作为视觉桥，将空间语义嵌入 2D 视觉流。
  - 允许 2D VLA 的梯度**反向传播**进入 3D 表示，实现几何推理与视觉感知的耦合。
- **整体架构**：形成"**推理 ⇄ 感知**"的闭环可微回路（closed differentiable loop）。

## 3. 实验设计

> **说明**：所提供的 PDF 文本中**未直接给出实验章节的正文**，以下信息来自摘要与元数据推断：

- **任务类型**：复杂三维操控任务，涵盖遮挡（occlusion）、杂乱（clutter）、复杂空间操作等场景。
- **对比基线**：摘要声明在 SOTA 方法上取得**平均 +12.1% 的提升**，但具体基线名称（可能包括 3D Diff Policy 类方法、2D VLA 类方法、DP3 等）未在所提供文本中明确列出。
- **评估指标**：未在摘要中详细说明，常见的此类工作通常报告成功率（success rate）。

## 4. 资源与算力

- **所提供的文本中未明确给出**：
  - GPU 型号与数量
  - 训练时长
  - 数据规模
- **可获取信息**：作者已开源代码（https://github.com/zyl123456aB/DIFFVLA），具体算力细节需查阅仓库或正文实验章节。

## 5. 实验数量与充分性

- 由于缺乏正文内容，**具体实验组数（消融实验数量、跨数据集测试、跨任务泛化等）无法从所提供材料中确认**。
- 从摘要可推断其声明的关键实验维度：
  - 遮挡环境
  - 杂乱环境
  - 复杂空间操作
- **客观性评价**：摘要给出"平均 +12.1% over SOTA" 的整体比较结论，但**公平性、统计显著性、消融完整性等需进一步从正文与附录确认**。

## 6. 主要结论与发现

- 提出 **DiffRender-VLA**，以**可微渲染作为视觉中介**，首次实现 3D VLA 与 2D VLA 在端到端梯度层面上的统一。
- 在遮挡、杂乱、复杂空间操作任务上均显著优于现有 SOTA 方法，**平均提升 +12.1%**。
- 验证了"**几何推理 + 视觉语义连续性**"互补融合的有效性，为三维机器人操控提供新的 VLA 建模范式。

## 7. 优点与亮点

- **方法论新颖性**：将**可微分渲染**从纯视觉/图形学领域引入 VLA 框架，思路具有跨领域创新性。
- **梯度一致的统一框架**：3D 与 2D 范式不再"拼接"或"后处理融合"，而是通过梯度反向传播实现**真正的端到端联合优化**。
- **空间语义编码方式巧妙**：用**颜色编码几何与标记的空间关系**，将抽象空间结构转化为 2D VLA 易于理解的图像线索。
- **自适应视角渲染**：根据目标—环境关系动态选择观察视角，理论上具备更好的任务适应性。
- **开源代码**：提供 GitHub 仓库，便于复现与后续研究。

## 8. 不足与局限

- **实验透明度受限**：所提供的 PDF 文本未包含实验章节细节，**数据集、基线、算力、消融、超参数分析等关键信息暂无法在本总结中确认**，需结合正文审阅。
- **可微渲染的计算成本**：可微分渲染通常需要逐像素反向传播，**可能带来额外显存与时间开销**，对实时控制是否构成瓶颈未在摘要中讨论。
- **对 3D 重建质量的依赖**：框架依赖底层 3D 表示（如点云或几何重建）的精度，**在传感器噪声大或重建稀疏的场景下性能可能下降**。
- **颜色编码的语义耦合假设**：将空间关系通过颜色映射到 2D 图像，**对预训练 2D VLM 的先验知识存在一定假设**，跨域迁移性需要进一步验证。
- **任务覆盖广度未知**：摘要强调遮挡/杂乱/空间操作，但对**长时序任务、多阶段任务、跨具身迁移**等场景的适用性未明确。
- **SOTA 比较公平性**：未明确是否对所有基线使用相同训练数据、相同演示次数（demonstrations）以及相同硬件，**对比公平性需正文验证**。

---

（完）
