---
title: Reducing Symmetry Mismatch Caused by Freely Placed Cameras in Robotic Learning
title_zh: 减少机器人学习中自由放置相机造成的对称性失配
authors: "David Klee, Dian Wang, Robert Platt, Robin Walters"
date: 2024-09-27
pdf: "https://openreview.net/pdf?id=2LHzKdb8Ao"
tags: ["query:rob-il"]
score: 6.0
evidence: 处理视觉机器人操作中相机视角的对称性失配
tldr: 当相机不在俯视位置时，等变策略学习在机器人操作中存在对称性失配问题，导致模型性能下降。本文表明，将相机图像预处理为俯视视角后，等变方法在不同视角和不同学习算法下都能稳定地获得更好的效果。该方法实现简单，同时兼容 RGB 与 RGBD 输入。该工作为任意相机放置下的视觉闭环机器人操作提供了一项实用且通用的增强手段。
source: ICLR-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 等变策略在非俯视相机下存在对称性失配，导致机器人操作性能下降。
method: 将侧视相机图像转换为类俯视视角，使变换与输入对齐，从而提升等变方法表现。
result: 在 RGB 与 RGBD 输入下、不同视角与不同学习算法上均稳定提升性能。
conclusion: 为自由相机放置下的视觉机器人操作提供了一种简单有效的等变性增强方法。
---

## Abstract
Equivariant policy learning has been shown to solve robotic manipulation tasks with minimal training or demonstration data.  However, the effectiveness of equivariance depends on whether transformations of the scene align with simple transformations of the input data. This is true when the camera is in a top-down view, but in the common case where a camera views the robot workspace from the side, there is a symmetry mismatch, reducing model performance. We show that equivariant methods perform better when camera images are transformed to appear as top-down images.  Our approach is simple to implement, works for RGB and RGBD images, and reliably improves performance across different view angles and learning algorithms.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Reducing Symmetry Mismatch Caused by Freely Placed Cameras in Robotic Learning" based on the provided abstract and metadata. I need to organize it into 8 sections as specified, using Markdown format with hierarchical headings and bullet points. I should be honest about limitations (e.g., the full PDF wasn't accessible due to CAPTCHA, so I'm working primarily from the abstract and metadata). Let me structure this carefully.</think>

# 论文总结：减少机器人学习中自由放置相机造成的对称性失配

> **说明**：本次可获取的内容仅为论文摘要（Abstract）与元数据信息，PDF 全文因 OpenReview 的 CAPTCHA 验证未能完整加载，因此以下总结主要基于摘要内容推断和归纳，部分细节（特别是实验数量、资源算力等）若摘要未明确提及，将如实标注。

---

## 1. 核心问题与整体含义（研究动机与背景）

- **核心问题**：等变策略学习（Equivariant Policy Learning）在机器人视觉操控中被证明能以极少的训练或演示数据完成任务，但其有效性建立在一个前提上——场景的几何/对称变换能够与输入数据的简单变换（如像素平移、旋转）对齐。
- **背景与痛点**：
  - 当相机处于**俯视（top-down view）**角度时，场景中的平移/旋转等对称变换近似对应于图像像素的平移/旋转，等变性假设成立。
  - 然而在真实部署中，相机往往**自由放置**，尤其是**侧视（side view）**视角，此时 3D 空间中的对称操作不再与简单的 2D 像素变换对应，产生**对称性失配（symmetry mismatch）**。
  - 这种失配会导致等变模型性能下降，限制了等变方法在自由相机放置场景中的实际应用。
- **研究意义**：解决这一失配问题可以显著拓展等变策略学习在真实机器人部署中的可用性，让"任意相机视角 + 极少数据"成为可行方案。

---

## 2. 方法论：核心思想与关键技术

- **核心思想**：通过图像预处理，将**侧视相机图像变换为"类俯视"（top-down-like）视角**，使得后续等变网络所假设的输入对称性得以恢复，从而避免对称性失配。
- **关键技术细节**：
  - **视角变换预处理**：在将图像送入策略网络之前，使用几何投影或单目/深度逆透视变换（Inverse Perspective Mapping, IPM）将侧视 RGB 或 RGBD 图像扭曲（warp）为近似俯视的鸟瞰表示。
  - **即插即用**：该预处理是一个轻量的前处理模块，与下游具体使用的等变网络结构、训练算法解耦。
  - **多模态兼容**：同时支持 **RGB** 与 **RGBD** 输入，覆盖常见的机器人视觉输入模式。
  - **算法流程（文字描述）**：
    1. 相机采集侧视 RGB / RGBD 图像。
    2. 利用相机内外参或深度信息，将像素重新投影到鸟瞰（俯视）平面。
    3. 将重投影后的图像送入等变策略网络进行推理或训练。
    4. 输出动作（末端位姿 / 关节指令）。
- **公式层面**：摘要未给出具体公式；从方法描述看，涉及经典的相机逆透视投影几何（针孔模型 + 单应性 / 深度反投影）。等变性部分应仍沿用现有 E(2)/SO(2) 等变卷积或群等变网络框架。

---

## 3. 实验设计：数据集 / 场景 / 对比方法

> 注：以下信息为根据摘要推断；具体任务名与基准在全文不可获取的条件下无法一一列出。

- **数据集 / 仿真场景**：
  - 摘要提到"在不同视角（different view angles）下"验证，推测使用了**多个相机角度**设置的仿真操控场景。
  - 可能采用机器人操作仿真平台（如 robosuite、robomimic、RLBench 等，**未明确披露**）。
- **Benchmark**：
  - 摘要未点明具体 benchmark；但提到对比"different learning algorithms"，可能涵盖 **等变模仿学习 / 等变强化学习**等多种基线算法。
- **对比方法**：
  - **基线 1**：未做视角变换、直接用侧视图像训练的等变方法（保留原始对称性失配）。
  - **基线 2**：使用非等变（vanilla）策略网络 + 侧视输入。
  - **所提方法**：等变方法 + 视角变换预处理。
- **输入模态**：分别测试了 **RGB** 与 **RGBD** 两种输入。

---

## 4. 资源与算力

- 摘要中**未提及**所使用的 GPU 型号、数量、训练时长、显存占用等算力细节。
- 由于全文未能加载，具体训练成本（如模拟器小时数、真实机器人演示次数、收敛所需 epoch 数等）均**无法确认**。
- 仅能合理推测：所提方法为预处理模块，计算开销主要来自单张图像的逆透视变换，开销极小；网络规模应与原等变基线一致，未带来额外显著算力需求。

---

## 5. 实验数量与充分性

- **已知的实验维度**（根据摘要）：
  - 多种相机视角角度（至少 ≥2：侧视 vs. 变换后俯视，可能还有正俯视）。
  - 多种输入模态：RGB、RGBD。
  - 多种学习算法（"different learning algorithms"）。
- **充分性评估**：
  - 摘要中"reliably improves performance across different view angles and learning algorithms" 表明作者做了**跨视角 × 跨算法**的消融/对比，思路较为系统。
  - 但仅凭摘要**无法判断**：
    - 是否包含**真实机器人**实验（而非仅仿真）。
    - 是否对多种任务类别（pick-and-place、插孔、装配、铰链操作等）做了覆盖。
    - 是否做了**对相机标定误差**、**深度噪声**等鲁棒性测试。
    - 统计显著性（多次随机种子）是否充分。
  - 因此从可获取信息来看，实验**方向正确但充分性难以独立验证**。

---

## 6. 主要结论与发现

- **主要结论**：
  - 在自由放置的侧视相机设置下，等变策略学习存在对称性失配问题，会显著降低性能。
  - 将相机图像预处理为类俯视视角后，等变方法能够恢复与输入对齐的对称性，**稳定优于**未做变换的等变基线。
  - 该方法简单、易实现，对 RGB 与 RGBD 输入均有效，且在不同视角与不同学习算法下一致性较好。
- **关键发现**：
  - 等变方法的性能**强依赖于视角与输入对齐**这一隐含假设。
  - 一个简单的几何预处理（视角变换）即可作为**通用增强手段**，几乎不增加算法复杂度。
  - 该工作为**任意相机放置**下的视觉闭环机器人操控提供了一种实用、通用的等变性增强方案。

---

## 7. 优点（方法与实验设计的亮点）

- **问题切入精准**：精准指出了等变策略学习的一个真实但常被忽视的失败模式——相机视角引发的对称性失配，而非继续"堆叠"更复杂的等变结构。
- **方法简洁实用**：仅需一次图像几何变换即可修复对称性，工程上几乎零成本，便于落地。
- **模态与算法无关**：同时兼容 RGB / RGBD，并适用于多种等变学习算法，泛化性强。
- **与现实部署契合**：直接回应"相机不能保证俯视"的现实约束，提升了等变方法的实用价值。
- **思想可推广**：类似的"先对齐再等变"思路有望被推广到非平面对称（旋转、缩放、SE(2)/SO(3)）等其他对称失配情形。

---

## 8. 不足与局限

- **论文可获取性受限**：由于 CAPTCHA 限制，本次无法获取全文，摘要以外的方法细节、实验规模、统计方法均无法核实，存在一定评估盲区。
- **依赖相机内外参 / 深度信息**：
  - IPM 变换需要相机标定（内参、外参）；
  - 对 RGB 输入而言，纯单目逆透视会在高度维度引入误差；
  - 对 RGBD 输入则依赖深度图的精度与完整性。
- **真实世界验证**：摘要未明确说明是否在**真实机器人**上验证，若仅仿真，则存在 sim-to-real gap 风险。
- **视角极端性**：当相机高度极低、几乎水平时，逆透视变换会出现大面积盲区与拉伸，方法的有效边界**未在摘要中讨论**。
- **任务多样性**：摘要未给出任务列表，难以判断是否覆盖了接触丰富、遮挡严重或工具使用等更复杂的操控场景。
- **未触及更广义的对称失配**：本文聚焦平移/旋转类失配，对**光照变化、物体类别对称性、背景干扰**等其他可能影响等变有效性的因素未做讨论。
- **公平性考量**：若对比时未对所有方法统一数据增强与训练预算，则"reliably improves"的结论需要更严格的统计支撑（如多 seed、置信区间）。

---

（完）
