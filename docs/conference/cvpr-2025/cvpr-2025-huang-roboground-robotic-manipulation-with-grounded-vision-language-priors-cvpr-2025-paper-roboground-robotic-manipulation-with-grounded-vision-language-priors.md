---
title: "RoboGround: Robotic Manipulation with Grounded Vision-Language Priors"
title_zh: RoboGround：基于接地视觉语言先验的机器人操纵
authors: "Huang, Haifeng, Chen, Xinyi, Chen, Yilun, Li, Hao, Han, Xiaoshen, Wang, Zehan, Wang, Tai, Pang, Jiangmiao, Zhao, Zhou"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Huang_RoboGround_Robotic_Manipulation_with_Grounded_Vision-Language_Priors_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于视觉语言接地先验的操纵策略实现感知到动作的映射
tldr: 现有机器人操纵策略依赖隐式中间表征，泛化能力受限。本文提出 RoboGround，将大规模视觉语言模型生成的接地掩码作为显式空间指引，告知策略目标物体与放置位置。该方法在多种操纵任务中提升了策略泛化能力，是视觉到动作映射的有效桥接方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 817, \"height\": 986, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1710, \"height\": 957, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1709, \"height\": 684, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 867, \"height\": 211, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1807, \"height\": 326, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 324, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 872, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 870, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-huang-roboground-robotic-manipulation-with-grounded-vision-language-priors-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 699, \"height\": 222, \"label\": \"Table\"}]"
motivation: 操纵策略需要更显式、可泛化的空间中间表征。
method: 利用视觉语言模型生成接地掩码作为策略中间表征。
result: 在多个操纵任务上提升了策略的泛化表现。
conclusion: 验证了接地视觉语言先验对操纵策略的促进作用。
---

## Abstract
Recent advancements in robotic manipulation have highlighted the potential of intermediate representations for improving policy generalization. In this work, we explore grounding masks as an effective intermediate representation, balancing two key advantages: (1) effective spatial guidance that specifies target objects and placement areas while also conveying information about object shape and size, and (2) broad generalization potential driven by large-scale vision-language models pretrained on diverse grounding datasets. We introduce \method, a grounding-aware robotic manipulation policy that leverages grounding masks as an intermediate representation to guide policy networks in object manipulation tasks. To further explore and enhance generalization, we propose an automated pipeline for generating large-scale, simulated data with a diverse set of objects and instructions. Extensive experiments show the value of our dataset and the effectiveness of grounding masks as intermediate guidance, significantly enhancing the generalization abilities of robot policies.

---

## 论文详细总结（自动生成）

<think>
The user wants me to write a detailed Chinese summary of the paper "RoboGround: Robotic Manipulation with Grounded Vision-Language Priors" based on the provided content. I need to follow a specific structure with 8 points and use Markdown formatting. Let me analyze the paper carefully and produce a comprehensive summary.

Let me organize my thoughts on each section:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experiment quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me write this out in detail.
</think>
# RoboGround 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：机器人操纵策略的泛化能力受限。现有方法存在两大困境：
  - **粗粒度表征**（如语言指令）：易获取但缺乏精确空间信息，难以支撑细粒度操作。
  - **细粒度表征**（如目标图、点流）：空间信息丰富，但需要大量数据与算力训练，难以扩展。
- **关键观察**：现有模拟数据集（如 MimicGen、RoboCasa、CALVIN）存在场景复杂度低、指令多样性不足的问题，导致策略容易过拟合到简单指令-场景映射上。
- **本文主张**：**接地掩码（grounding mask）** 是一种理想的中间表征，兼具（1）显式空间指引（形状、尺寸、位置）与（2）大规模视觉语言模型（VLM）预训练赋予的强泛化能力。
- **目标**：将掩码作为桥梁，把高层语言指令与底层动作策略连接起来，提升策略在新对象、新场景和新指令上的泛化性能。

---

## 2. 方法论

### 2.1 核心思想
采用"**接地 VLM + 掩码引导策略**"的两段式架构：先用大规模接地 VLM（GLaMM）将语言指令解析为目标对象与放置区域掩码；再将这些掩码以多种形式注入到低层策略网络。

### 2.2 自动数据生成流水线
- 在 RoboCasa 基础上构建自动化生成流程，产出 **24K 演示 + 112K 多样化指令**，覆盖 176 类、3526 个物体。
- **对象集扩展**：从 Objaverse 中筛选 1017 个高质量桌面操作物体，GPT-4 协助分类与筛选。
- **指令多样性**（三类）：
  - **外观型（Appearance）**：用 GPT-4 提取物体颜色/形状/材质等属性作为唯一特征，按 CLIP 相似度采样干扰物。
  - **空间型（Spatial）**：基于规则生成（"在胡萝卜右边的物体"），并要求角度偏差不超过 30°。
  - **常识型（Commonsense）**：GPT-4 根据多视角图像与目标描述生成日常场景化指令（"我们在做果沙拉，请拿起相关物品"）。

### 2.3 接地视觉语言模型（Grounded VLM）
- 基于 **GLaMM**，使用 CLIP 视觉编码器 + LLM + SAM 编码器/解码器。
- 输入图像与指令，输出 `<SEG>` token 解析出的二值掩码（目标对象掩码 $M_o$ + 放置区域掩码 $M_p$）。
- 关键公式：
  - 文本生成：$y_t = L(f_v(\text{CLIP}(x_v)), x_t)$
  - 像素级掩码：$M = D(f_s(F_{seg}), E(x_v))$
- 使用仿真数据 + 原始 VLM 数据进行指令微调，mIoU 从零样本 13.2 提升至 48.2。

### 2.4 接地策略网络（Grounded Policy Network）
- 基于 **GR-1** 的语言条件 Transformer 架构。
- **通道级融合**：将掩码 $M_o, M_p$ 与图像做通道拼接，线性层投影回 3 通道后送入预训练 ViTMAE。
  $$Z_v = \text{ViTMAE}(\text{Linear}(\text{Concat}(x_v, M_o, M_p)))$$
- **Patch 级融合（Grounded Perceiver）**：在 14×14 patch 特征上引入三组可学习 query：
  - 全局 query $Q_g$：捕获整图信息。
  - 目标对象 query $Q_o$：通过掩码 $M_o$ 引导注意力。
  - 放置区域 query $Q_p$：通过掩码 $M_p$ 引导注意力。
- Token 序列为 $\{Z^v_{CLS}, P(Z^v_P), Z_t, Z_s, Z_{ACT}\}$，Transformer 解码器预测下一步动作。
- **训练损失**：$L_{total} = L_{arm} + L_{gripper}$（Smooth-L1 + BCE）。
- **推理**：每个回合开头对 VLM 调用一次，多视角并行处理，单回合前向只预测下一步动作。

---

## 3. 实验设计

### 3.1 仿真环境
- 基于 **RoboCasa** 构建仿真场景。
- 训练集：RoboCasa 原始 66K 演示 + 本文新生成 24K 演示 / 112K 指令。
- 测试集：每个指令类型生成 400 个测试样本，涵盖拾取放置（Pick-and-Place）的外观/空间/常识三类指令，以及开门/关抽屉/按按钮/转杠杆/旋钮等基础操作技能。

### 3.2 对比基线
- **ACT**（Zhao et al., 2023）：CVAE 风格的动作分块 Transformer，无语言输入。
- **BC-Transformer**：RoboMimic 的标准行为克隆 + CLIP 语言 + FiLM 融合。
- **GR-1**：GPT 风格语言条件视频生成模型（无大规模预训练与图像预测的复现版本）。

### 3.3 评估指标
- 拾取放置任务：报告"**接触率 / 成功率**"（%）双指标。
- 基础技能任务：报告成功率。
- 零样本评估：分 **Unseen Instance**（同类新对象）与 **Unseen Class**（全新类别）两个层级。

---

## 4. 资源与算力

- 文中**未明确给出完整的算力配置**。
- 仅在消融实验中提到"完整训练与评估在 8 张 NVIDIA 4090 GPU 上需要数天时间"，且为加速消融使用了 3K + 3K 的子集。
- 数据生成依赖 GPT-4 API，VLM 微调与策略训练未披露具体 GPU 时长。

---

## 5. 实验数量与充分性

- **主结果表（Table 1）**：1 个数据集，1 组主对比（4 种方法 × 4 类指令 + 4 类基础技能 ≈ 32 个数据点）。
- **零样本表（Table 2）**：2 个未见层级 × 4 类指令 × 有/无掩码 = 16 个数据点。
- **消融实验（Tables 3–6）**：
  - 训练数据与掩码消融（6 种配置）。
  - 掩码融合模块消融（4 种配置）。
  - 接地表示形式消融（6 种表示）。
  - VLM 微调数据消融（3 种配置）。
- **总实验量**：约 **6 张表、50+ 数据点**，覆盖主对比、零样本、数据、模块、表示、VLM 等多个维度。
- **充分性评价**：
  - 优点：消融全面，涵盖数据、模块、表征三个层次；零样本评估分两级；对比了 3 个不同基线。
  - 不足：仅在仿真环境评估，缺乏真实机器人实验；测试样本量（400 / 类型）适中但未做多随机种子统计显著性分析。

---

## 6. 主要结论与发现

- **掩码作为中间表征显著有效**：在外观、空间、常识三类语义复杂指令上，RoboGround 相对最强基线 GR-1 提升约 **25–40 个百分点**（成功率），在零样本 Unseen Class 上提升近 **100%（相对值）**。
- **数据多样性 + 掩码引导缺一不可**：仅用原始简单数据时，掩码作用不明显；引入高复杂度新数据后掩码价值凸显，二者结合效果最佳。
- **掩码优于点 / 包围盒**：二维低维表示（点、包围盒）效果均不如掩码，验证了形状尺寸信息的重要性。
- **通道级 + Patch 级融合互补**：Grounded Perceiver 比单纯通道拼接更有效，二者叠加效果最佳。
- **GT 掩码 vs 预测掩码**：用预测掩码已能取得接近 GT 掩码的效果，证明 VLM 输出的可靠性。
- **接地 VLM 微调是必要环节**：零样本 mIoU 仅 13.2，需用仿真 + 原始 VLM 数据联合微调（达 48.2）才能在实际指令下稳定生成正确掩码。
- **接触率与成功率存在差距**：模型定位目标能力强，但抓取姿态仍有改进空间。

---

## 7. 优点

- **方法层面**：
  - 首次系统性地将"像素级接地掩码"作为机器人操纵的中间表征，兼顾空间精确性与泛化性。
  - Grounded Perceiver 设计巧妙：通过 mask-guided 注意力实现 patch 级的区域聚焦，避免标准 Perceiver 的信息丢失。
  - 模块化设计：VLM 与策略网络解耦，便于替换和升级。
- **数据层面**：
  - 自动化数据生成流水线可扩展，融合 GPT-4 与 CLIP 相似度筛选生成高复杂度场景。
  - 24K 演示 + 112K 指令 + 3526 物体的规模在仿真数据中颇具竞争力。
- **实验层面**：
  - 消融充分，覆盖数据、模块、表征、VLM 四维度。
  - 零样本评估分两级，体现真实泛化能力。
  - 公开代码与数据（robo-ground.github.io），可复现性强。

---

## 8. 不足与局限

- **仅仿真评估**：未在真实机器人上验证，仿真到真实的迁移性能未经验证。
- **算力与训练细节披露不足**：未明确报告完整训练时长、显存占用、批量大小等。
- **VLM 推理开销**：每回合开头调用一次 VLM（多视角并行），对实时性要求高的部署可能存在挑战；Grounded Perceiver 额外引入了 3×k query token，增加了计算量。
- **抓取姿态能力有限**：成功率显著低于接触率，说明对抓取位姿的学习仍不充分，作者也承认这一点。
- **单回合任务假设**：掩码在任务开始时生成一次，假设目标位置不变；对于目标移动或多阶段任务不适用。
- **数据偏差风险**：所有训练均在 RoboCasa 厨房场景下进行，可能对其他场景（如工业、家庭其他区域）的迁移性有限。
- **GPT-4 依赖**：数据生成与指令构造高度依赖 GPT-4 API，存在 API 稳定性、成本与潜在数据偏差问题。
- **缺乏用户研究或失败分析**：未对失败案例进行系统性归因（如混淆对象、抓取失败、放置错误等）。

（完）
