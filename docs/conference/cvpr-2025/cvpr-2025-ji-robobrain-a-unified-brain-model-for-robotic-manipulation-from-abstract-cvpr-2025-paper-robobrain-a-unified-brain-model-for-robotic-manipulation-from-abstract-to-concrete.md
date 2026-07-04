---
title: "RoboBrain: A Unified Brain Model for Robotic Manipulation from Abstract to Concrete"
title_zh: RoboBrain：面向从抽象到具体机器人操控的统一大脑模型
authors: "Ji, Yuheng, Tan, Huajie, Shi, Jiayu, Hao, Xiaoshuai, Zhang, Yuan, Zhang, Hengyuan, Wang, Pengwei, Zhao, Mengdi, Mu, Yao, An, Pengju, Xue, Xinda, Su, Qinghang, Lyu, Huaihai, Zheng, Xiaolong, Liu, Jiaming, Wang, Zhongyuan, Zhang, Shanghang"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ji_RoboBrain_A_Unified_Brain_Model_for_Robotic_Manipulation_from_Abstract_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向长时序机器人操控的统一视觉语言大脑模型，涵盖规划、可供性感知与轨迹预测
tldr: 现有面向机器人的多模态大语言模型在长时序操控任务中仍缺乏规划能力、可供性感知与轨迹预测能力，导致难以将抽象指令落地为具体动作。本文提出统一大脑模型 RoboBrain，通过联合视觉与语言推理，将复杂操控指令分解为可执行的子任务，并预测完整的操作轨迹。在多种操控基准上的实验表明，该模型在任务拆解与轨迹预演方面优于通用多模态大模型，验证了以视觉为锚点的通用模型可作为复杂机器人操控的大脑模块。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1555, \"height\": 1061, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1700, \"height\": 989, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1806, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1757, \"height\": 950, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1608, \"height\": 299, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1653, \"height\": 414, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 1671, \"height\": 876, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 511, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 662, \"height\": 202, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ji-robobrain-a-unified-brain-model-for-robotic-manipulation-from-abstract-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 740, \"height\": 231, \"label\": \"Table\"}]"
motivation: 通用多模态大模型在长时序机器人操控中缺乏规划、可供性感知与轨迹预测等关键能力。
method: 构建面向机器人的统一多模态大模型，联合视觉场景与语言指令进行子任务分解与轨迹预测。
result: 在多种操控基准上取得更优的任务分解与轨迹预测效果，超越通用多模态大模型。
conclusion: 验证了视觉驱动的通用模型可作为复杂机器人操控的统一大脑，具备良好的泛化能力。
---

## Abstract
Recent advancements in Multimodal Large Language Models (MLLMs) have shown remarkable capabilities across various multimodal contexts. However, their application in robotic scenarios, particularly for long-horizon manipulation tasks, reveals significant limitations. These limitations arise from the current MLLMs lacking three essential robotic brain capabilities: Planning Capability, which involves decomposing complex manipulation instructions into manageable sub-tasks; Affordance Perception, the ability to recognize and interpret the affordances of interactive objects; and Trajectory Prediction, the foresight to anticipate the complete manipulation trajectory necessary for successful execution. To enhance the robotic brain's core capabilities from abstract to concrete, we introduce ShareRobot, a high-quality heterogeneous dataset that labels multi-dimensional information such as task planning, object affordance, and end-effector trajectory. ShareRobot's diversity and accuracy have been meticulously refined by three human annotators. Building on this dataset, we developed RoboBrain, an MLLM-based model that combines robotic and general multi-modal data, utilizes a multi-stage training strategy, and incorporates long videos and high-resolution images to improve its robotic manipulation capabilities.Extensive experiments demonstrate that RoboBrain achieves state-of-the-art performance across various obotic tasks, highlighting its potential to advance robotic brain capabilities.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper "RoboBrain: A Unified Brain Model for Robotic Manipulation from Abstract to Concrete" following a specific 8-point structure. Let me carefully analyze the paper content and organize it accordingly.

Let me go through each point:

1. **Core problem and overall meaning**: The paper addresses limitations of MLLMs in robotic long-horizon manipulation tasks - lack of three key capabilities: planning, affordance perception, and trajectory prediction.

2. **Methodology**: 
   - ShareRobot dataset construction
   - RoboBrain model based on LLaVA architecture
   - Multi-stage training strategy (Phase 1: General OV Training with stages 1-2, Phase 2: Robotic Training with stages 3-4)
   - A-LoRA for affordance, T-LoRA for trajectory
   - SigLIP + 2-layer MLP + Qwen2.5-7B-Instruct

3. **Experimental design**:
   - Datasets: Open X-Embodiment (selected 51,403 instances), RoboVQA, OpenEQA, ShareRobot test set, AGD20K
   - Benchmarks: RoboVQA (BLEU1-4), OpenEQA, ShareRobot (GPT-4o scoring), affordance (AP), trajectory (DFD, HD, RMSE)
   - Baselines: GPT-4V, Claude3, LLaVA-1.5, LLaVA-OneVision-7B, Qwen2-VL-7B, RoboMamba, LLaVA-NeXT-7B

4. **Resources**: 8×A800 GPUs per server, multiple servers, Zero3 distributed training. No specific training time mentioned.

5. **Experimental quantity and sufficiency**: 
   - 3 planning benchmarks
   - 1 affordance benchmark
   - 4 trajectory ablation variants
   - Visualization examples
   - Pretty comprehensive

6. **Main conclusions**: SOTA on multiple robotic benchmarks, validates ShareRobot dataset and RoboBrain framework.

7. **Strengths**:
   - Large-scale fine-grained dataset (1M+ QA pairs)
   - Multi-dimensional labeling
   - Multi-stage training strategy
   - Supports long videos and high-resolution images
   - A-LoRA and T-LoRA for task-specific capabilities
   - Strong performance improvements

8. **Limitations**:
   - No real-world robot experiments mentioned
   - No training time/cost details
   - Reliance on GPT-4o for evaluation could introduce bias
   - Limited diversity in some respects
   - The paper is relatively short (11 pages)

Let me write this up in Chinese with proper Markdown formatting.</think>

# RoboBrain 论文总结

## 1. 核心问题与研究背景

论文聚焦于**多模态大语言模型（MLLM）在长时序机器人操控任务中的能力缺口**。作者指出，尽管 MLLM 在视觉问答、图像描述、情感分析等通用任务上表现优异，但其在机器人场景（尤其是长时序、复杂操控任务）中的应用仍存在显著局限，主要原因在于现有模型缺乏三项关键的"机器人脑"能力：

- **规划能力（Planning Capability）**：将复杂操控指令分解为可管理的子任务；
- **可供性感知（Affordance Perception）**：识别并解释交互对象的可操作区域；
- **轨迹预测（Trajectory Prediction）**：预判完整操控轨迹以支持执行。

以"拿起茶壶将水倒入杯子"为例，现有 MLLM 既无法可靠地将该任务拆解为"靠近茶壶—提起—移至杯口—倾斜倒水"等子任务，也难以识别茶壶的可抓取区域，更无法给出末端执行器的运动轨迹。论文认为根本原因是**缺乏面向机器人操控的大规模、细粒度数据集**。

## 2. 方法论

### 2.1 核心思想

论文提出"**从抽象到具体**"的核心理念：通过构建高质量异构数据集 ShareRobot，并在其上训练统一 MLLM 模型 RoboBrain，使模型既能理解高层语言指令，又能输出可执行的低层动作表达（可供性区域 + 运动轨迹）。

### 2.2 ShareRobot 数据集构建

- **数据筛选**：从 Open X-Embodiment 中筛选 51,403 条高质量样本，遵循高分辨率图像（≥128 像素）、准确描述、成功执行状态、长视频（≥30 帧）、目标不被遮挡、轨迹清晰等原则。
- **规划标注（Planning）**：对每段演示均匀抽取 30 帧，借助 Gemini 将高层描述分解为低层原子任务，由 3 名标注员复核。基于 RoboVQA 的 10 种问题类型各设计 5 种模板，每实例随机选用 2 种模板生成 QA 对，最终得到 **1,027,990 个 QA 对**（训练 100 万 / 测试 2,050）。
- **可供性标注（Affordance）**：筛选 6,522 张图像，按指令标注每张图中的可供性包围盒 {l(x), l(y), r(x), r(y)}（训练 6,000 / 测试 522）。
- **轨迹标注（Trajectory）**：筛选 6,870 张图像，为每张图标注末端执行器至少 3 个 {x, y} 路径点（训练 6,000 / 测试 870）。
- **数据多样性**：覆盖 23 个原始数据集、12 种机器人本体、102 个场景、107 类原子任务（如 pick、move、reach、lift、place 等）。

### 2.3 RoboBrain 模型架构

基于 LLaVA 架构，由三个模块组成：

1. **基础规划模型**：Vision Encoder 采用 **SigLIP**，Projector 为 2 层 MLP，LLM 采用 **Qwen2.5-7B-Instruct**。输入可为图像、多图或视频。
2. **A-LoRA 模块（可供性感知）**：用边界框表达可供性 `{l(x), l(y), r(x), r(y)}`，每个对象可拥有多个可供性区域。
3. **T-LoRA 模块（轨迹预测）**：将轨迹定义为二维视觉迹线，输出归一化到 [0, 1000) 的 2D 路径点序列 $P_{t:N} = \{(x_i, y_i) \mid i = t, t+1, ..., N\}$。

### 2.4 多阶段训练策略

| 阶段 | 内容 | 训练模块 | 数据规模 |
|------|------|---------|---------|
| Stage 1 | 对齐与通用知识学习 | Projector | LCS-558K |
| Stage 1.5 | 通用多模态学习 | 全模型 | 4M 高质量图文 |
| Stage 2 | 视觉指令微调 | 全模型 | 3.2M 单图 + 1.6M 图视频 |
| Stage 3 | 机器人多任务学习（含规划） | 全模型 | 1.3M 机器人数据 + 1.7M 通用数据（防遗忘）|
| Stage 4 | 可供性 + 轨迹 LoRA 微调 | A-LoRA + T-LoRA | 10K + 400K |

视觉分辨率从 384 → 384×{2×2} → 384×{6×6} 逐级提升，Token 数量从 729 增长至最多 729×37，以支持**历史帧记忆**和**高分辨率图像输入**。

## 3. 实验设计

### 3.1 数据集与 Benchmark

- **规划任务**：RoboVQA（BLEU1-4）、OpenEQA（GPT-4o 评分）、ShareRobot 测试集（GPT-4o 评分）。
- **可供性预测**：AGD20K 测试集，使用 **Average Precision (AP)** 指标（多 IoU 阈值）。
- **轨迹预测**：ShareRobot 轨迹测试集，使用 **DFD（离散 Fréchet 距离）、HD（Hausdorff 距离）、RMSE** 三个指标。

### 3.2 对比方法

- **规划任务**：GPT-4V、Claude3、LLaVA-1.5、LLaVA-OneVision-7B、Qwen2-VL-7B、RoboMamba；
- **可供性预测**：Qwen2-VL-7B、LLaVA-NeXT-7B；
- **轨迹预测**：模型自身的 4 个变体（Baseline、+Start Points、+Max Points、+Spec Token & End Points）。

## 4. 资源与算力

论文仅提到使用 **DeepSpeed Zero3** 分布式训练策略，在**每台配备 8×A800 GPU 的服务器集群**上进行训练，但**未明确披露**：
- 服务器总数量；
- 训练总时长；
- 端到端训练成本。

## 5. 实验数量与充分性

- **规划实验**：3 个 Benchmark × 6 个基线模型；
- **可供性实验**：1 个 Benchmark × 2 个基线；
- **轨迹实验**：4 个消融变体；
- **可视化分析**：多轮规划示例展示。

整体实验覆盖了三项核心能力且包含基线对比与消融分析，**规划能力实验较为充分**，但可供性与轨迹预测的对比基线数量偏少（仅 2 个基线），消融也仅在轨迹任务上展开。

## 6. 主要结论与发现

- RoboBrain 在 **OpenEQA、ShareRobot、RoboVQA** 三大规划基准上均超越所有基线模型；
- 在 RoboVQA 上 BLEU-4 比第二名高出 **18.75**；
- 可供性预测 AP 达 **27.1%**，较 Qwen2-VL-7B（12.5%）提升 14.6，较 LLaVA-NeXT-7B（9.8%）提升 17.3；
- 轨迹预测最终变体相对 Baseline，DFD 下降 42.9%、HD 下降 94.2%、RMSE 下降 31.6%；
- 验证了**视觉驱动通用模型可作为复杂机器人操控的统一大脑模块**这一假设。

## 7. 优点

- **数据集贡献突出**：ShareRobot 是当时规模最大的开源规划/可供性/轨迹统一数据集（100 万 + QA 对），具有细粒度、多维度、高质量、易扩展等特点；
- **多阶段训练设计合理**：在通用多模态能力基础上注入机器人知识，并通过混合通用数据缓解灾难性遗忘；
- **支持长视频与高分辨率图像**：通过分辨率逐步提升策略，Token 数最高达 729×37，赋予模型历史帧记忆能力；
- **模块化设计**：A-LoRA 与 T-LoRA 解耦可供性/轨迹能力，可独立微调；
- **可视化结果直观**：展示了多轮交互式规划过程。

## 8. 不足与局限

- **缺乏真实机器人实验**：所有评估均在离线 Benchmark 上完成，未见真实机器人部署验证；
- **算力与训练成本披露不足**：未给出 GPU 数量、训练时长、数据规模下的具体耗时；
- **评估依赖 GPT-4o**：OpenEQA 与 ShareRobot 测试均使用 GPT-4o 评分，存在主观性与潜在偏见，且 BLEU 类指标对长文本生成的语义评估能力有限；
- **基线数量偏少**：可供性预测仅 2 个对比模型，轨迹预测仅做自身消融，缺乏与其他专用模型的横向对比；
- **可供性与轨迹数据规模有限**：分别仅 6,000 训练样本，相对规划任务（百万级）规模悬殊；
- **泛化性验证不足**：未明确报告跨场景、跨本体的零样本/少样本泛化实验；
- **论文篇幅较短**（11 页），附录信息有限，限制了方法细节的完整呈现。

（完）
