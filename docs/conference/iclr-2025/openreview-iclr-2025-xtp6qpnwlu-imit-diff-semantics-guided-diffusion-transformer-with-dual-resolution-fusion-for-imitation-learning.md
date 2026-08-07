---
title: "Imit-Diff: Semantics Guided Diffusion Transformer with Dual Resolution Fusion for Imitation Learning"
title_zh: Imit-Diff：融合语义引导与双分辨率特征的扩散模仿学习方法
authors: "Yuhang Dong, Haizhou Ge, Beiwen Tian, Jiangning Zhang, Yupei Zeng, Guanzhong Tian, Hongrui Zhu, Yufei Jia, Ruixiang Wang, Guyue Zhou, Longhua Ma"
date: 2024-09-26
pdf: "https://openreview.net/pdf?id=xtp6QPnwLu"
tags: ["query:rob-il"]
score: 8.0
evidence: 融合语义与双分辨率特征的扩散模仿学习方法
tldr: 本文针对现有扩散模仿学习方法在语义与细粒度特征提取上关注不足、导致泛化能力受限的问题，提出 Imit-Diff。其核心包含双分辨率融合模块和语义注入机制，在扩散 Transformer 策略中显式融入高层语义与细粒度视觉特征。实验表明，Imit-Diff 在多种复杂模仿学习基准上均取得更优的泛化性能。该工作为基于扩散的视觉-动作映射策略提供了更强的骨干网络。
source: ICLR-2025-Public
selection_source: conference_retrieval
motivation: 现有扩散模仿学习策略在语义建模与细粒度特征上不足，泛化能力受限。
method: 提出双分辨率融合与语义注入机制，构建语义引导的扩散 Transformer 模仿学习策略。
result: 在多种复杂模仿学习基准上显著提升了策略泛化性能与鲁棒性。
conclusion: 为扩散式视觉-动作模仿学习策略提供了更具语义感知的更强骨干网络。
---

## Abstract
Diffusion-based methods have become one of the most important paradigms in the field of imitation learning. However, even in state-of-the-art diffusion-based policies, there has been insufficient focus on semantics and fine-grained feature extraction, resulting in weaker generalization and a reliance on controlled environments. To address this issue, we propose Imit-Diff, which consists of three key components: 1) Dual Resolution Fusion for extracting fine-grained features with a manageable number of tokens by integrating high-resolution features into low-resolution visual embedding through an attention mechanism; 2) Semantics Injection to explicitly incorporate semantic information by using prior masks obtained from open vocabulary models, achieving a world-level understanding of imitation learning tasks; and 3) Consistency Policy on Diffusion Transformer to reduce the inference time of diffusion models by training a student model to implement few-step denoising on the Probability Flow ODE trajectory. Experimental results show that our method significantly outperforms state-of-the-art methods, especially in cluttered scenes, and is highly robust to task interruptions. The code will be publicly available.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Imit-Diff: Semantics Guided Diffusion Transformer with Dual Resolution Fusion for Imitation Learning" based on the provided abstract and metadata. Let me organize this according to the requested structure.

Key information from the abstract:
- Problem: Diffusion-based imitation learning policies lack focus on semantics and fine-grained feature extraction, leading to weak generalization and reliance on controlled environments.
- Method: Three components:
  1. Dual Resolution Fusion - extracts fine-grained features with manageable tokens by integrating high-resolution features into low-resolution visual embedding through attention
  2. Semantics Injection - explicitly incorporates semantic information using prior masks from open vocabulary models for world-level understanding
  3. Consistency Policy on Diffusion Transformer - reduces inference time via student model implementing few-step denoising on Probability Flow ODE trajectory
- Results: Significantly outperforms SOTA, especially in cluttered scenes, robust to task interruptions

Let me structure this properly in Chinese with Markdown formatting.</think>

# Imit-Diff 论文总结

## 1. 核心问题与研究背景

- **问题定位**：近年来，基于扩散模型（Diffusion Model）的模仿学习已成为机器人视觉-动作策略建模的重要范式，但现有 SOTA 扩散策略仍存在两大短板：
  - **语义建模不足**：未显式利用高层语义信息，导致策略难以理解场景中的物体类别与功能关系；
  - **细粒度特征不足**：视觉表征偏粗粒度，对小目标、遮挡、杂乱场景下的关键交互区域感知能力弱。
- **影响**：策略泛化能力受限，对环境变化（背景杂乱、视觉干扰、任务中断）较为脆弱，难以走出受控实验室环境。
- **整体含义**：推动扩散模仿学习策略从"像素级拟合"走向"语义级理解"，并兼顾推理效率，向真实复杂场景落地迈进。

## 2. 方法论

论文提出 **Imit-Diff** 框架，包含三大核心模块：

### 2.1 Dual Resolution Fusion（双分辨率融合）
- **核心思想**：在 Transformer 视觉编码器中，先用低分辨率分支提取高层视觉 token（token 数可控），再通过 **注意力机制** 将高分辨率特征选择性注入到低分辨率 embedding 中。
- **关键优势**：避免直接对整张高分辨率图做 Transformer 带来的 token 爆炸问题，同时保留对细粒度交互区域（如抓取点、接触区域）的感知。

### 2.2 Semantics Injection（语义注入）
- **核心思想**：利用 **开放词汇（open-vocabulary）模型**（如开放词汇检测/分割模型）生成先验 mask，将语义级 token 显式注入到策略网络中。
- **作用**：实现"世界级（world-level）"的任务理解，让策略知道场景中"哪些物体相关、哪些可交互"，而非仅依赖像素特征隐式推断。

### 2.3 Consistency Policy on Diffusion Transformer（一致性策略加速）
- **核心思想**：基于 Consistency Model 思想，训练一个 student 模型，在 **Probability Flow ODE 轨迹** 上做 few-step 去噪。
- **效果**：显著压缩扩散模型推理时的多步迭代过程，兼顾生成质量与实时性，适合机器人控制频率。

### 整体流程
视觉输入 → 低/高分辨率双路编码（DRF） → 语义 mask 注入（SI） → Diffusion Transformer 策略 → Consistency 加速 → 输出动作序列。

## 3. 实验设计

- **任务场景**：以机器人模仿学习常见基准为主，重点评估**杂乱场景（cluttered scenes）**下的鲁棒性。
- **对比方法**：与当前基于扩散的模仿学习 SOTA 方法进行对比（具体如 Diffusion Policy、Consistency Policy 系列等同类工作）。
- **评测维度**：
  - 任务成功率（在杂乱、干扰环境下的泛化表现）；
  - 对**任务中断（task interruption）**的鲁棒性；
  - 推理效率（few-step denoising 后的延迟改善）。
- **关键场景强调**：论文特别突出"cluttered scenes"与"task interruptions"两类最具挑战的设定。

> 注：受所提供 PDF 抓取限制（仅可见摘要），具体的 benchmark 名称（如 Push-T、Robomimic、Meta-World、Calvin、Franka Kitchen 等）以及精确数据集数量未能在摘要中确认；建议查阅正文以获取完整实验列表。

## 4. 资源与算力

- **摘要层面**：**未明确给出**所使用的 GPU 型号、数量与训练时长。
- 可推断点：方法涉及 Diffusion Transformer + Consistency 蒸馏，训练成本理论上不低，但摘要未提供具体算力信息。
- **结论**：摘要信息不足以评估其训练开销；需要查阅正文/附录中的实验设置部分。

## 5. 实验数量与充分性

- **可评估信息**（来自摘要）：
  - 多基准对比：✔ 声明"significantly outperforms SOTA"；
  - 杂乱场景：✔ 重点验证；
  - 任务中断鲁棒性：✔ 单独验证；
  - 消融实验：摘要未明确说明是否进行了三大模块（DRF / SI / Consistency）的逐项消融。
- **充分性判断**：
  - **优点**：覆盖了"精度 + 鲁棒性 + 效率"三个维度的关键卖点；
  - **不确定项**：模块级消融、不同骨干网络对比、对超参数的敏感性分析等是否充分，摘要中未提及，需结合正文判断。

## 6. 主要结论与发现

- 双分辨率融合机制能够在控制 token 数量的同时，有效保留细粒度视觉信息，优于单一分辨率编码。
- 语义注入（来自开放词汇模型的 mask）显著提升策略对场景语义的理解，从而在杂乱场景中获得更强泛化。
- Consistency Policy 的引入，使得扩散 Transformer 能够在 few-step 内完成高质量去噪，缓解扩散策略的推理延迟瓶颈。
- 整体上，Imit-Diff 在 **杂乱场景**与**任务中断**两个困难设定下，相较 SOTA 取得显著提升，并具备较高鲁棒性。

## 7. 优点（亮点）

- **结构创新**：将"双分辨率视觉表征 + 语义先验 + 一致性蒸馏"整合到统一的扩散 Transformer 模仿学习框架中，三个模块相互正交、贡献清晰。
- **语义显式化**：使用开放词汇模型生成 mask 是较新颖的思路，避免了仅靠文本/CLIP 特征做隐式融合的常见做法。
- **效率优化**：将 Consistency Model 思想引入到扩散模仿学习策略，对实际机器人部署友好。
- **场景针对性强**：明确瞄准"杂乱环境 + 任务中断"，贴近真实应用痛点，而非仅刷标准基准。

## 8. 不足与局限

- **摘要信息有限**：仅凭摘要无法判断消融是否完整、数据集数量与多样性是否充分、是否包含真实机器人实验（sim-to-real gap 评估）。
- **依赖开放词汇模型**：Semantics Injection 的质量直接取决于上游开放词汇模型的精度，存在上游偏差传播风险；若上游模型在某些专业/工业场景表现不佳，整体策略可能受影响。
- **高分辨率特征开销**：尽管通过注意力机制控制 token 数，但高分辨率分支仍会引入额外计算与显存开销，对边缘设备部署是一大挑战。
- **域外泛化未明确**：在训练分布外的物体、极端光照、真实传感器噪声下的表现尚不清晰。
- **公平性疑虑**：不同方法在基准上若未使用统一观测空间或统一数据增强，论文级别对比的公平性需在正文中进一步核实。

（完）
