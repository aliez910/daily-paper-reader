---
title: "RoboSpatial: Teaching Spatial Understanding to 2D and 3D Vision-Language Models for Robotics"
title_zh: RoboSpatial：面向 2D 与 3D 视觉-语言模型的机器人空间理解数据集
authors: "Song, Chan Hee, Blukis, Valts, Tremblay, Jonathan, Tyree, Stephen, Su, Yu, Birchfield, Stan"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Song_RoboSpatial_Teaching_Spatial_Understanding_to_2D_and_3D_Vision-Language_Models_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向机器人视觉-语言模型的空间理解数据集
tldr: 空间理解是机器人感知环境并与之交互的关键能力，但当前视觉-语言模型训练数据多源自通用图像集，缺乏参考帧等高级空间理解。本文构建 RoboSpatial 大规模空间理解数据集，专门面向 2D 与 3D 视觉-语言模型，涵盖自我、世界与物体等多种参考系下的推理能力。该数据集有助于提升下游机器人任务中的空间推理表现。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 849, \"height\": 481, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 865, \"height\": 546, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1622, \"height\": 1035, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 873, \"height\": 294, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1799, \"height\": 325, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 263, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 663, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1622, \"height\": 867, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 368, \"height\": 291, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-song-robospatial-teaching-spatial-understanding-to-2d-and-3d-vision-language-models-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 457, \"height\": 227, \"label\": \"Table\"}]"
motivation: 现有视觉-语言模型训练数据缺乏参考帧等高级空间理解，难以支持机器人空间推理任务。
method: 构建大规模空间理解数据集 RoboSpatial，覆盖多种参考系下的 2D 与 3D 空间推理样本。
result: 在 RoboSpatial 上训练的视觉-语言模型在机器人空间推理任务中表现显著提升。
conclusion: 专用空间理解数据集可有效增强视觉-语言模型在机器人领域的空间推理能力。
---

## Abstract
Spatial understanding is a crucial capability that enables robots to perceive their surroundings, reason about their environment, and interact with it meaningfully. In modern robotics, these capabilities are increasingly provided by vision-language models. However, these models face significant challenges in spatial reasoning tasks, as their training data are based on general-purpose image datasets that often lack sophisticated spatial understanding. For example, datasets frequently do not capture reference frame comprehension, yet effective spatial reasoning requires understanding whether to reason from ego-, world-, or object-centric perspectives. To address this issue, we introduce RoboSpatial, a large-scale dataset for spatial understanding in robotics. It consists of real indoor and tabletop scenes, captured as 3D scans and egocentric images, and annotated with rich spatial information relevant to robotics. The dataset includes 1M images, 5k 3D scans, and 3M annotated spatial relationships, and the pairing of 2D egocentric images with 3D scans makes it both 2D- and 3D- ready. Our experiments show that models trained with RoboSpatial outperform baselines on downstream tasks such as spatial affordance prediction, spatial relationship prediction, and robotics manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "RoboSpatial: Teaching Spatial Understanding to 2D and 3D Vision-Language Models for Robotics" following a specific structure with 8 points. Let me analyze the paper content carefully.

Based on the abstract and metadata provided:

1. Core problem: VLMs lack spatial understanding for robotics because training data is based on general-purpose images without sophisticated spatial understanding (like reference frame comprehension).

2. Method: Introduce RoboSpatial - a large-scale dataset with 1M images, 5k 3D scans, 3M annotated spatial relationships, covering ego-, world-, and object-centric perspectives.

3. Experiments: Downstream tasks - spatial affordance prediction, spatial relationship prediction, robotics manipulation. The paper mentions baseline comparisons.

4. Resources: Not explicitly mentioned in the provided content.

5. Experiment quantity: Need to discuss this based on available info.

6. Conclusions: Models trained with RoboSpatial outperform baselines.

7. Strengths: 2D-3D paired data, large scale, rich annotations.

8. Limitations: Need to discuss.

Let me write a comprehensive Chinese summary based on the provided abstract and metadata.</think>

# RoboSpatial 论文总结

## 一、核心问题与研究动机

- **关键能力**：空间理解是机器人感知环境、推理环境并与之有意义交互的核心能力。
- **现状瓶颈**：当前机器人领域日益依赖视觉-语言模型（VLM）来提供这些能力，但 VLM 在空间推理任务上表现欠佳。
- **根本原因**：VLM 的训练数据多源自通用图像数据集（如网络图片），缺乏对"参考系"（reference frame）概念的系统性覆盖——例如"自我中心（ego-centric）"、"世界中心（world-centric）"和"物体中心（object-centric）"等视角。
- **研究目标**：构建一个面向机器人空间理解的大规模专用数据集，以弥补通用数据集在空间语义上的缺失，从而提升 VLM 在机器人下游任务中的空间推理能力。

## 二、方法论

- **核心思想**：构建一个配对的 2D/3D 空间理解数据集，覆盖多种参考系下的空间关系标注，使训练出的 VLM 能够同时在二维图像与三维点云上完成空间推理。
- **数据集 RoboSpatial**：
  - **规模**：约 **100 万张图像** + **5000 个三维扫描** + **300 万条标注空间关系**。
  - **场景类型**：真实室内场景与桌面级（tabletop）场景。
  - **数据形式**：
    - 2D 端：以自我中心（egocentric）图像形式呈现；
    - 3D 端：对应三维扫描数据；
    - 二者一一配对，因此同时适用于 2D 与 3D VLM（"2D- and 3D- ready"）。
  - **标注内容**：丰富的、与机器人相关的空间信息，涵盖自我/世界/物体等多参考系下的空间关系。
- **技术流程（概述）**：
  1. 在室内与桌面环境中采集三维扫描 + 同步 RGB-D 自我中心图像；
  2. 对 3D 场景中物体之间的空间关系进行自动化与人工结合的标注；
  3. 将 3D 标注投影或对应到 2D 图像，形成配对训练样本；
  4. 用于 2D 与 3D VLM 的微调或训练，使其学会多参考系空间推理。

## 三、实验设计

- **下游任务（benchmark）**：
  - 空间可供性预测（Spatial Affordance Prediction）；
  - 空间关系预测（Spatial Relationship Prediction）；
  - 机器人操作（Robotics Manipulation）。
- **对比基线**：文中使用 "baselines"（基于通用数据训练的标准 VLM）作为对照，验证 RoboSpatial 训练的增益。
- **数据覆盖**：室内 + 桌面两类典型机器人操作环境；涵盖 2D 与 3D 两种模态的评估。

## 四、资源与算力

- 论文正文（摘要 + 元数据部分）**未明确给出**所使用 GPU 型号、数量、训练时长或具体计算资源。
- 仅可推断数据集规模：1M 图像 + 5K 3D 扫描 + 3M 空间关系标注，属于大规模数据采集与处理工程。

## 五、实验数量与充分性

- **从元数据可见**：论文包含至少 **4 张主要图表** 和 **6 张表格**，涵盖数据示例、统计特性、空间关系类别、模型性能对比等。
- **评估维度**：
  - 多种下游任务（可供性、空间关系、操作）；
  - 2D 与 3D 模型分别验证；
  - 与多个基线对比。
- **充分性评价**：
  - **优点**：覆盖了 2D/3D 双模态与多任务，实验设计较为全面。
  - **局限**：仅凭元数据无法判断消融实验（如不同参考系标注、不同数据规模）的细致程度；摘要未提及人类评估或真实机器人实机测试细节。

## 六、主要结论与发现

- 在 RoboSpatial 上训练的视觉-语言模型**显著优于**基线模型（在空间可供性预测、空间关系预测、机器人操作等任务上）。
- 配对 2D-3D 数据 + 多参考系标注是提升机器人空间推理的关键。
- 通用图像数据集不足以支撑机器人级别的空间理解，需要专门构建空间理解数据集。

## 七、优点与亮点

- **规模庞大**：百万级图像 + 5K 3D 扫描 + 300 万条空间关系，是目前公开数据集中规模较大的机器人空间理解数据集之一。
- **2D 与 3D 配对**：同一场景同时具备 2D 图像与 3D 扫描，使数据集可同时服务 2D 与 3D VLM，扩展性强。
- **多参考系覆盖**：明确区分自我、世界、物体三种参考系，对机器人"以我/以世界/以物体为中心"的视角切换具有针对性。
- **任务驱动**：标注信息直接面向机器人下游任务（可供性、空间关系、操作），实用价值高。
- **真实场景**：基于真实室内与桌面环境的采集，避免了纯合成数据的 sim-to-real 鸿沟问题。

## 八、不足与局限

- **场景多样性有限**：数据集中在室内与桌面环境，对室外、动态环境、杂乱大规模场景的覆盖可能不足。
- **标注成本与偏差**：300 万条空间关系标注中自动化程度未知，人工标注可能引入主观偏差。
- **参考系覆盖深度**：虽然提到了 ego/world/object 三种参考系，但摘要未详细说明各参考系样本是否均衡；某些参考系可能样本不足。
- **基准与泛化**：未明确说明是否在跨场景、跨物体类别上做了泛化测试，存在过拟合特定室内布局的风险。
- **算力与可复现性**：未披露训练资源、训练时长、超参数细节，复现成本可能较高。
- **3D 数据利用**：数据集标注主要服务于 VLM 微调，对 3D 几何结构（如精确深度、占据关系）的充分利用程度有待进一步验证。

（完）
