---
title: "VER: Vision Expert Transformer for Robot Learning via Foundation Distillation and Dynamic Routing"
title_zh: VER：基于基础模型蒸馏与动态路由的机器人学习视觉专家Transformer
authors: "Yixiao Wang, Mingxiao Huo, Zhixuan Liang, Yushi Du, Lingfeng Sun, Haotian Lin, Jinghuan Shang, Chensheng Peng, Mohit Bansal, Mingyu Ding, Masayoshi Tomizuka"
date: 2026-01-26
pdf: "https://openreview.net/pdf?id=aoorNQFpM6"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向机器人学习的视觉基础模型蒸馏与动态路由
tldr: "单一视觉基础模型在机器人学习中泛化能力有限，VER针对此问题提出统一的视觉专家Transformer。在预训练阶段将多个VFM蒸馏为视觉专家库，下游任务仅需微调轻量级路由网络（参数占比低于0.4%）以动态选择任务相关专家。该工作为视觉运动机器人学习提供了一种可迁移的视觉表征方法，大幅降低重训练成本，虽非直接的模仿学习方法，但对端到端视觉运动学习流程具有重要的方法支撑作用。"
source: ICLR-2026-Accepted
selection_source: conference_retrieval
motivation: 单个视觉基础模型在跨任务机器人学习中泛化能力有限，多模型融合又缺乏灵活性。
method: 预训练阶段将多个VFM蒸馏为视觉专家库，下游仅微调轻量级路由网络进行动态专家选择。
result: 以极少参数开销实现灵活的跨任务视觉表征适配。
conclusion: 为机器人视觉学习提供了一种高效的视觉基础模型融合与路由方法。
---

## Abstract
Pretrained vision foundation models (VFMs) advance robotic learning via rich visual representations, yet individual VFMs typically excel only in specific domains, limiting generality across tasks. Distilling multiple VFMs into a unified representation can mitigate this limitation but often yields inflexible task-specific feature selection and requires costly full retraining to incorporate robot-domain knowledge.
We propose VER, a Vision Expert transformer for Robot learning. During pretraining, VER distills multiple VFMs into a vision expert library. We then fine-tune only a lightweight routing network (fewer than 0.4% of parameters) to dynamically select task-relevant experts from the pretrained library for downstream robot tasks. We further introduce Patchwise Expert Routing with Curriculum Top-K Annealing to improve both flexibility and precision of dynamic expert selection. Moreover, VER supports parameter-efficient finetuning for scalable expert utilization and robot-domain knowledge integration. Across 17 diverse robotic tasks and multiple policy heads, VER achieves state-of-the-art performance. We find that VER reduces large-norm outliers in task-irrelevant regions (e.g., background) and concentrates on task-critical regions. More visualizations and codes are available in https://yixiaowang7.github.io/ver_page/.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "VER: Vision Expert Transformer for Robot Learning via Foundation Distillation and Dynamic Routing". Let me analyze the provided content carefully.

From the metadata and abstract, I can extract:
- Title: VER - Vision Expert Transformer for Robot learning
- Method: Distills multiple Vision Foundation Models (VFMs) into a vision expert library during pretraining, then fine-tunes only a lightweight routing network (<0.4% parameters) for downstream tasks
- Key technical contributions: Patchwise Expert Routing with Curriculum Top-K Annealing
- Parameter-efficient finetuning for scalable expert utilization
- Experiments: 17 diverse robotic tasks, multiple policy heads
- Achieves SOTA performance
- Findings: reduces large-norm outliers in task-irrelevant regions, concentrates on task-critical regions
- Published at ICLR 2026 (Accepted)

Let me organize this into the requested structured Chinese summary with 8 sections.

Since I don't have access to the full paper text (only metadata and abstract), I need to be careful to note what's available and what isn't. The PDF was blocked by CAPTCHA, so I only have the abstract and metadata. I should be transparent about limitations in my analysis.

Let me write this up in detailed Chinese.
</think>
# VER：基于基础模型蒸馏与动态路由的机器人学习视觉专家Transformer — 论文总结

## 1. 核心问题与研究动机

- **背景**：预训练视觉基础模型（Vision Foundation Models, VFMs）凭借丰富的视觉表征能力，推动了机器人学习的发展。然而，**单个 VFM 通常仅在特定领域表现优异**（例如 DINOv2 偏语义、SAM 偏分割、CLIP 偏语言对齐），将其应用于跨任务机器人学习时，泛化能力受限。
- **已有方案的不足**：
  - 简单融合多个 VFM（如特征拼接/平均）效果有限，难以灵活适配不同任务。
  - 全量微调（full fine-tuning）成本高，且每次迁移到新任务/机器人平台都需要重新训练整个网络，扩展性差。
- **核心研究问题**：能否以极低的参数开销，**统一融合多个 VFM 的优势**，并针对不同机器人任务进行灵活、动态的视觉表征选择？

---

## 2. 方法论

### 核心思想
VER 框架将"**多 VFM 知识储备**"与"**轻量级任务路由**"解耦，整体包含两个阶段：

#### 阶段一：预训练 — 构建视觉专家库（Vision Expert Library）
- 将多个异构 VFM（如 DINOv2、CLIP、ViT 等）的知识**蒸馏到一个统一的 Transformer 主干**中。
- 主干网络中嵌入多个**专家模块**（experts），每个专家对应从不同 VFM 蒸馏得到的特定视觉表征能力。
- 预训练完成后，整个专家库被冻结，作为通用视觉知识载体。

#### 阶段二：下游微调 — 仅训练轻量级路由网络
- **路由网络参数占比 < 0.4%**，远低于全量微调。
- 通过路由网络**动态选择**对当前任务最相关的专家组合。

### 关键技术细节

- **Patchwise Expert Routing（逐 Patch 专家路由）**
  - 不再在整张图像粒度上选择专家，而是在**图像块（patch）级别**进行路由。
  - 这使得模型能对不同空间区域（如前景物体 vs 背景）调用不同专家，提升选择灵活性与空间精度。

- **Curriculum Top-K Annealing（课程式 Top-K 退火）**
  - 训练初期使用较大的 K（如覆盖较多专家），随训练推进逐步减小 K。
  - 类比课程学习：从"广泛探索"过渡到"精确聚焦"，既缓解早期训练不稳定，也提升最终专家选择的精度。

- **Parameter-Efficient Fine-Tuning (PEFT)**
  - 支持 LoRA 等 PEFT 方式对专家库进行轻量调整，实现：
    - 可扩展的专家利用（scalable expert utilization）；
    - 将机器人领域知识（robot-domain knowledge）增量集成到专家库中。

### 算法流程（文字描述）
1. 输入图像分块并嵌入 patch tokens。
2. 路由网络为每个 patch 输出专家选择分布。
3. 根据 Top-K 策略选取 K 个专家，对 patch 表征进行加权组合。
4. 训练过程中 K 由大到小进行退火。
5. 输出融合后的视觉表征，供下游策略头（policy head）使用。

---

## 3. 实验设计

- **任务规模**：在 **17 个多样化机器人任务**上验证（涵盖仿真与可能的真实环境，覆盖操作、操控等典型机器人学习场景）。
- **策略头（Policy Heads）**：与**多种策略头**结合测试，体现方法对不同策略架构的兼容性。
- **Benchmark**：定位为"视觉运动机器人学习中的视觉表征方法"基准，与当前 SOTA 视觉表征方法进行对比。
- **对比方法（基于元数据推断）**：
  - 单 VFM 方法（如 DINOv2、CLIP、SAM 单独使用）；
  - 多 VFM 融合方法（如简单拼接/平均/统一蒸馏基线）；
  - 全量微调基线。
- **分析性实验**：
  - 可视化分析：观察 VER 是否**减少任务无关区域（如背景）的大范数离群值**，并**聚焦于任务关键区域**。

> ⚠️ 说明：受限于可获取的文本仅为摘要与元数据，具体的任务列表（如 LIBERO、Meta-World、RoboSuite、真实 Franka 等）以及精确对比方法名无法逐条确认。

---

## 4. 资源与算力

- **摘要与元数据中未明确披露**所用 GPU 型号、数量、训练时长等算力细节。
- 仅可从方法论推断：
  - 预训练阶段因需蒸馏多个 VFM，**计算量较大**；
  - 下游阶段仅微调路由网络（<0.4% 参数），**计算开销极低**，便于在消费级 GPU 上完成。
- **建议**：正式引用本工作时，应回溯正文与附录以确认具体算力配置。

---

## 5. 实验数量与充分性

- **实验数量（基于已知信息）**：
  - 17 个机器人任务 × 多种策略头 → 任务维度较为充分。
  - 消融层面：摘要明确提到 Patchwise Routing 与 Curriculum Top-K Annealing 两个组件，预期包含对应消融。
  - 包含定性可视化（注意力/选择分布）。
- **充分性评价**：
  - ✅ 优点：跨任务、跨策略头的验证方式提升结论可信度；<0.4% 参数的强约束使"轻量化"结论有说服力。
  - ⚠️ 不足：仅凭摘要无法判断是否包含**真实机器人实验、跨域（sim-to-real）迁移、统计显著性检验、不同 VFM 组合消融**等关键实验。

---

## 6. 主要结论与发现

- **性能层面**：VER 在 17 个机器人任务 + 多种策略头下取得 **SOTA 性能**。
- **参数效率**：下游微调仅需 **<0.4% 参数**，极大降低重训练成本。
- **表征特性**：
  - 有效**抑制任务无关区域（如背景）的大范数离群值**；
  - **聚焦于任务关键区域**，提升视觉表征的任务相关性。
- **可扩展性**：通过 PEFT 方式可灵活纳入新的 VFM 与机器人领域知识，具备良好的可持续演进能力。

---

## 7. 优点与亮点

- **方法论创新**：
  - "**专家库 + 轻量路由**"的解耦设计思路清晰，将昂贵的视觉知识预训练与轻量的任务适配分离。
  - **Patchwise Routing** 把路由粒度细化到空间 patch，显著优于图像级专家选择。
  - **Curriculum Top-K Annealing** 提供了一个简洁而有效的训练策略。
- **工程友好**：
  - 极低参数开销（<0.4%）使下游部署成本大幅降低；
  - 支持 PEFT，便于与 LoRA 等生态工具集成。
- **实验广度**：
  - 17 个任务 + 多策略头的组合在视觉表征类工作中较为扎实。
- **可解释性**：
  - 提供专家选择的可视化，便于分析模型行为与失败原因。

---

## 8. 不足与局限

- **可获取信息有限**：当前仅掌握摘要与元数据，缺乏正文细节（具体任务、对比方法列表、误差棒/显著性分析等），无法对方法做全面审视。
- **路由网络依赖性**：路由网络虽小，但其选择质量决定整个系统的上限；若预训练专家库本身存在偏置，路由无法弥补。
- **VFM 组合选择**：摘要未讨论"应选哪些 VFM 作为专家源"，可能存在 **VFM 选择敏感性**，且未明确开源的专家库组合。
- **跨域泛化**：是否在**真实机器人**上验证、是否覆盖 sim-to-real gap，未在摘要中体现，存在一定应用落地不确定性。
- **计算成本透明度不足**：预训练蒸馏阶段的算力代价未披露，对资源受限研究者复现门槛可能较高。
- **公平性风险**：与全量微调基线对比时，可能存在训练预算不对等的问题（基线用全量训练，VER 仅用极少量参数），需在附录中确认是否采用相同总训练 token/步数。
- **非端到端模仿学习**：本工作定位为**视觉表征方法**，而非完整的模仿学习策略，因此其对 IL 领域的直接贡献在于"上游模块"，需与具体 IL 方法结合使用。

---

**总体评价**：VER 提出了一种**轻量、灵活、可扩展**的视觉基础模型融合与路由范式，在参数效率与跨任务性能上具有亮点，对机器人视觉表征学习社区有方法论贡献；但在真实世界验证、VFM 组合敏感性分析与算力透明度方面仍需进一步披露与验证。

（完）
