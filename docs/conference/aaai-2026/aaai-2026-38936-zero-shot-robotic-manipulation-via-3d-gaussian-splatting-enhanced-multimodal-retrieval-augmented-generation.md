---
title: Zero-Shot Robotic Manipulation via 3D Gaussian Splatting-Enhanced Multimodal Retrieval-Augmented Generation
title_zh: 基于3D高斯泼溅增强多模态检索生成的零样本机器人操作
authors: "Zilong Xie, Jingyu Gong, Xin Tan, Zhizhong Zhang, Yuan Xie"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38936/42898"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过3D高斯泼溅增强多模态检索生成实现零样本机器人操作
tldr: 本文提出RobMRAG框架，利用3D高斯泼溅增强的多模态检索生成实现零样本机器人操作。构建多源操作知识库，通过层次多模态检索与MLLM推理结合，弥合了几何理解不足。实验表明该方法在零样本场景下取得良好操作成功率，有效泛化到未见物体和任务，为端到端机器人操作提供了一种可解释的新范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38936/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1845, \"height\": 653, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38936/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1830, \"height\": 1233, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38936/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 884, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38936/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 881, \"height\": 350, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38936/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 883, \"height\": 738, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38936/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1847, \"height\": 916, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38936/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 894, \"height\": 557, \"label\": \"Table\"}]"
motivation: 端到端方法因数据有限和可解释性差难以泛化到新物体。
method: 构建多源操作知识库，采用层次多模态检索和生成。
result: 在零样本场景下取得较好操作成功率，展示泛化能力。
conclusion: 结合外部知识与3D表示提升机器人操作的泛化性。
---

## Abstract
Existing end-to-end approaches of robotic manipulation often lack generalization to unseen objects or tasks due to limited data and poor interpretability. While recent Multimodal Large Language Models (MLLMs) demonstrate strong commonsense reasoning, they struggle with geometric and spatial understanding required for pose prediction. In this paper, we propose RobMRAG, a 3D Gaussian Splatting-Enhanced Multimodal Retrieval-Augmented Generation (MRAG) framework for zero-shot robotic manipulation. Specifically, We construct a multi-source manipulation knowledge base containing object contact frames, task completion frames, and pose parameters. During inference, a Hierarchical Multimodal Retrieval module first employs hybrid semantic search to find task-relevant object prototypes, then selects the geometrically closest reference example based on pixel-level similarity and Instance Matching Distance (IMD). We further introduce a 3D-Aware Pose Refinement module based on 3D Gaussian Splatting into the MRAG framework, which aligns the pose of the reference object to the target object in 3D space. The aligned results are reprojected onto the image plane and used as input to the MLLM to enhance the generation of the final pose parameters. Extensive experiments show that on a test set containing 30 categories of household objects, our method improves the success rate by 7.76% compared to the best-performing zero-shot baseline under the same setting, and by 6.54% compared to the state-of-the-art supervised baseline. Our results validate that RobMRAG effectively bridges the gap between high-level semantic reasoning and low-level geometric execution, enabling robotic systems that generalize to unseen objects while remaining inherently interpretable.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与整体含义（研究动机与背景）
现有端到端机器人操作方法因数据有限且可解释性差，难以泛化到未见物体或任务。多模态大语言模型（MLLM）具备强常识推理，但对几何与空间理解不足，导致抓取位姿预测不准确。本文提出 **RobMRAG**——一种基于 3D 高斯泼溅（3DGS）增强的多模态检索生成（MRAG）框架，旨在弥合高层语义推理与低层几何执行之间的鸿沟，实现零样本下的通用机器人操作。

## 2. 方法论
- **核心思想**：通过多源知识库存储操作案例，采用分层多模态检索获取与当前任务最匹配的参考示例，再借助 3DGS 对参考位姿进行空间精对齐，最后将精化后的二维重投影结果送入 MLLM 生成最终抓取位姿。
- **关键技术细节**：
  - **多源知识库构建**：整合仿真、真实机器人数据集（如 HOI4D）及互联网数据，每个案例包含接触帧、成功帧、指令文本、2D 接触点及末端执行器方向。
  - **分层多模态检索**：
    1. **文本语义检索**：三优先级混合策略（稀疏检索 BM25 → 稠密嵌入检索 → 跨源扩展），公式为文本余弦相似度 \(S_{\text{text}}\)。  
    2. **视觉相似性过滤**：用 CLIP 计算观测图像与候选接触帧的余弦相似度 \(S_{\text{CLIP}}\)，选出 top-n。  
    3. **几何匹配**：计算实例匹配距离（IMD），衡量局部特征一致性，选距离最小的候选。
  - **3D-Aware 位姿精化模块**：用预训练生成模型 TRELLIS 从参考 RGB-D 构建 3DGS 表示；对参考抓取位姿施加预设小角度旋转 \(R_k\)，将 3D 接触点与方向变换后重新投影到图像平面（公式 \(p'_k = \pi(M[R_k|t]p'_e)\)），并再次计算 IMD 选出最佳对齐位姿。
  - **LoRA 微调与推理**：联合掩码语言建模（MLM）损失和位姿回归损失（包括接触点 MSE 与方向余弦相似度），对 MLLM 进行低秩适应微调。推理时，检索精化后的参考作为额外输入，输出结构化抓取参数（2D 点 + 两个 3D 方向）。

## 3. 实验设计
- **数据集与场景**：基于 SAPIEN 仿真器和 PartNetMobility 数据集，使用 Franka Panda 吸盘机械臂。训练集包含 20 类物体共约 2 万成功操作样本；测试集分 **Test Seen**（已知类别不同实例）和 **Test Unseen**（全新类别），共覆盖 30 类家居物体。
- **评价指标**：平均操作成功率（ASR），包括位移阈值 \(\delta=0.01\)（初始位姿）和 \(\delta=0.1\)（持续运动），但主表统一报告 ASR%。
- **对比方法**：包括零样本基线 RAM、CrayonRobo，监督基线 Where2Act、UMPNet、Flowbot3D、Implicit3D、ManipLLM（全量 / 局部设置）。实验在相同训练/测试划分与末端执行器配置下进行。

## 4. 资源与算力
论文未明确提及所用 GPU 型号、数量或训练时长。仅指出使用 LoRA 微调，未提供详细硬件开销信息。

## 5. 实验数量与充分性
主要实验包括：
- **表1**：全量对比（零样本、All、Local 三种设置），覆盖 30 类物体，含复现结果。
- **表2**：消融实验（去除检索、仅文本检索+不同距离、加入3D对齐；不同MLLM骨干 Qwen2-VL、LLaMA3.2-VL、Qwen2.5-VL）。
- **图3**：检索候选数 top-n 与旋转采样数 K 的影响。
- **定性结果**：检索策略可视化、位姿精化对齐示例。
实验设计相对充分，控制变量清晰，基准方法均在相同设置下复现，公平性较好。

## 6. 主要结论与发现
- 零样本设置下，RobMRAG 在 Unseen 上 ASR 达 43.53%，比最强零样本基线 RAM 高 7.76 个百分点。
- 微调 All 设置下，Unseen 上 ASR 达 57.54%，比监督 SOTA（ManipLLM）高 6.54 个百分点；在 Local 设置（已知接触点）下优势更大。
- 消融表明：层级检索和 3D 位姿精化均贡献显著；使用更强 MLLM 骨干（如 Qwen2.5-VL）可进一步提升性能。
- 框架有效结合外部知识库与 3D 几何对齐，实现了类级别泛化与可解释性。

## 7. 优点
- **创新性**：首次将 MM-RAG 与 3DGS 结合用于机器人操作，解决了 MLLM 几何不足的问题。
- **检索增强泛化**：多源知识库 + 分层检索 + 3D 精化，使零样本操作成为可能。
- **可解释性**：检索到的可操作案例为 MLLM 提供了具体几何上下文，输出结构清晰。
- **可扩展性**：支持不同 MLLM 骨干，性能随模型增强而提升。

## 8. 不足与局限
- **细粒度精度不足**：对交互区域极小的物体（如剪刀 17.84%、钳子 32%）成功率低，难以处理毫米级操作。
- **数据集固有缺陷**：部分场景图像退化严重（如 Door 图像像素丢失 80%），部分指令模糊（如 Faucet 未区分操作类型），影响模型表现。
- **计算开销未讨论**：3DGS 生成与多视角渲染可能带来额外延迟，文中未分析实时性。
- **依赖知识库覆盖**：虽有三优先级回退，但对完全无参考的极端新颖任务泛化能力仍有限。

（完）
