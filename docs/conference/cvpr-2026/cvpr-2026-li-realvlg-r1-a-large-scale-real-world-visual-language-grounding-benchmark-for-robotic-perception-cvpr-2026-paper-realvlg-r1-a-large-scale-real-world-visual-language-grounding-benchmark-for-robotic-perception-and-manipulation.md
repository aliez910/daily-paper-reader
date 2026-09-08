---
title: "RealVLG-R1: A Large-Scale Real-World Visual-Language Grounding Benchmark for Robotic Perception and Manipulation"
title_zh: RealVLG-R1：面向机器人感知与操作的大规模真实场景视觉语言对齐基准
authors: "Li, Linfei, Zhang, Lin, Shen, Ying"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Li_RealVLG-R1_A_Large-Scale_Real-World_Visual-Language_Grounding_Benchmark_for_Robotic_Perception_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 面向真实场景的视觉语言对齐与抓取大规模基准
tldr: 现有视觉语言对齐方法侧重粗粒度目标定位，且传统抓取方法缺乏语言引导，难以应用于语言驱动的操作任务。为此，本文提出 RealVLG 框架，包含 110 亿样本规模的 RealVLG-11B 数据集以及统一对齐与抓取任务的 RealVLG-R1 模型。该基准支持系统评测语言驱动机器人操作方法，并通过语义引导弥补纯几何抓取方法的不足，对推动真实场景下的语言驱动操作研究具有重要参考价值。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1695, \"height\": 632, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1707, \"height\": 726, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1786, \"height\": 474, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1620, \"height\": 712, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 814, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 829, \"height\": 163, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-realvlg-r1-a-large-scale-real-world-visual-language-grounding-benchmark-for-robotic-perception-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1770, \"height\": 346, \"label\": \"Table\"}]"
motivation: 现有视觉语言对齐方法粒度粗且缺乏与抓取的结合，难以支撑语言驱动操作。
method: 构建 RealVLG-11B 数据集并提出统一视觉语言对齐与抓取的 RealVLG-R1 模型。
result: 在真实场景下提升了语言驱动抓取与对齐的精度与鲁棒性。
conclusion: 为真实场景语言驱动机器人操作提供了大规模基准与统一模型。
---

## Abstract
Visual-language grounding aims to establish semantic correspondences between natural language and visual entities, enabling models to accurately identify and localize target objects based on textual instructions. Existing VLG approaches focus on coarse-grained, object-level localization, while traditional robotic grasping methods rely predominantly on geometric cues and lack language guidance, which limits their applicability in language-driven manipulation scenarios. To address these limitations, we propose the RealVLG framework, which integrates the RealVLG-11B dataset and the RealVLG-R1 model to unify real-world visual-language grounding and grasping tasks. RealVLG-11B dataset provides multi-granularity annotations including bounding boxes, segmentation masks, grasp poses, contact points, and human-verified fine-grained language descriptions, covering approximately 165,000 images, over 800 object instances, 1.3 million segmentation, detection, and language annotations, and roughly 11 billion grasping examples. Building on this dataset, RealVLG-R1 employs Reinforcement Fine-tuning on pretrained large-scale vision-language models to predict bounding boxes, segmentation masks, grasp poses, and contact points in a unified manner given natural language instructions. Experimental results demonstrate that RealVLG supports zero-shot perception and manipulation in real-world unseen environments, establishing a unified semantic-visual multimodal benchmark that provides a comprehensive data and evaluation platform for language-driven robotic perception and grasping policy learning. All data and code are publicly available at https://github.com/lif314/RealVLG-R1.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "RealVLG-R1: A Large-Scale Real-World Visual-Language Grounding Benchmark for Robotic Perception and Manipulation" organized in 8 specific sections. Let me analyze the paper carefully and structure the response.

Key points from the paper:
1. Problem: VLG methods are coarse-grained, traditional grasping lacks language guidance
2. Method: RealVLG framework with RealVLG-11B dataset and RealVLG-R1 model
3. Dataset: 165K images, 800+ objects, 1.3M segmentation/detection/language annotations, 11B grasping examples
4. Model: Uses Qwen2.5-VL as backbone, trained with RLVR (GRPO and GSPO)
5. Experiments: Compare against Qwen-VL-Max, Gemini2.5-Flash, Qwen2.5-VL series, with SFT variants
6. No mention of specific GPU/compute resources
7. Experiments: Multiple splits (Seen, Similar, Novel), multiple tasks (Bbox, Seg, Grasp, Contact)
8. Conclusions: Strong zero-shot generalization, unified perception-grasping

Let me organize this into a comprehensive Chinese summary.</think>

# RealVLG-R1 论文详细总结

## 1. 核心问题与整体含义

**研究背景**：视觉-语言对齐（Visual-Language Grounding, VLG）旨在建立自然语言与视觉实体之间的语义对应关系，使模型能够根据文本指令准确识别并定位目标物体。该任务是跨模态理解的核心，在语言驱动的感知、交互与智能控制中扮演基础角色。

**现有不足**：
- **VLG 方面**：现有研究主要聚焦于粗粒度、目标级别的定位（边界框、分割掩码），尚未扩展到"可操作的抓取理解"（即推理如何与物体交互）。
- **抓取方面**：传统机器人抓取研究主要依赖视觉或几何线索，缺乏语言和语义引导，难以应用于多任务、人机交互的操作场景。
- **数据集方面**：如 Grasp-Anything、Grasp-Anything++ 等数据集基于扩散模型生成的合成场景，存在语义失真与视觉不一致问题；抓取标注由 RAGT-3/3 生成，精度有限；语言描述多为粗粒度，缺乏细粒度的、与物体对齐的描述及空间关系信息。

**研究意义**：当前 VLG 与抓取研究之间存在明显的语义理解与操作推理鸿沟，不足以支持需要细粒度、多模态感知的真实机器人场景。RealVLG 框架旨在统一这两个任务，为语言驱动的机器人感知与操作提供数据基础和评测平台。

---

## 2. 方法论

### 2.1 整体框架
RealVLG 框架包含两个核心组件：
1. **RealVLG-11B 数据集**：大规模真实场景、多模态、多粒度的视觉-语言对齐与抓取数据集。
2. **RealVLG-R1 模型**：基于预训练大视觉语言模型（Qwen2.5-VL）并采用强化学习微调策略的统一模型。

### 2.2 RealVLG-11B 数据集构建

**数据来源**：整合了多个真实场景抓取数据集：
- 单物体场景：Cornell
- 多物体关系场景：VMRD
- 渐进式物体场景：OCID-Grasp
- 杂乱场景：GraspNet、GraspClutter6D

共约 **165,000 张图像**，**800+ 个物体实例**。

**统一标注流水线**（5 步）：
1. **元描述生成**：提取每个物体的 3D 模型，从 8 个不同视角渲染，输入 GPT-4o 生成物体的元描述（捕捉内在属性）。
2. **语言指令生成**：将图像与元描述输入 GPT-4o，生成详细语言指令，描述物体的类别、颜色、形状、属性以及与其他物体的空间关系。
3. **定位验证**：使用 Qwen-VL-Max 进行目标检测，输出边界框。
4. **分割生成**：使用 SAM2 获取高精度分割掩码。
5. **抓取姿态标准化**：统一转换为矩形抓取姿态，并计算接触点（保证接触点位于物体表面）。

**人机协作验证**：人工标注员对元描述、语言指令、边界框、分割掩码进行交叉验证，若发现不一致则修正语言描述并重新执行检测和分割流程。

**数据集规模**：约 165K 图像、800+ 物体、1.3M 分割/检测/语言标注、约 110 亿个抓取样本。

**数据划分**：Seen（48 个训练物体）、Similar（50 个相似未见物体）、Novel（37 个新颖物体），每个子集约 15K 图像、150K 实例、300M 抓取标注。

### 2.3 RealVLG-R1 模型设计

**核心动机**：传统监督微调（SFT）方法在抓取姿态预测这种多解场景中存在两个问题：（1）迫使模型拟合单一标签会产生"平均化"的、物理上不可行的预测；（2）固定监督信号不足以捕捉抓取稳定性、空间一致性、物理可行性等多维目标。

**关键技术**：采用 **带可验证奖励的强化学习（RLVR）** 范式，受 DeepSeek-R1 启发：

1. **可验证奖励函数**：
$$R(q, o) = \begin{cases} 1, & \text{if } o = \text{ground truth} \\ 0, & \text{otherwise} \end{cases}$$

2. **策略优化目标**（含 KL 散度正则化）：
$$\max_{\pi_\theta} \mathbb{E}_{q,o}\left[R(q, o) - \beta D_{KL}[\pi_\theta(o|q) \| \pi_{ref}(o|q)]\right]$$

3. **组对比优势估计**：从旧策略 $\pi_{\theta_{old}}$ 采样 G 个响应，计算组相对优势：
$$\hat{A}_i = \frac{r(x, y_i) - \text{mean}(\{r(x, y_j)\})}{\text{std}(\{r(x, y_j)\})}$$

4. **两种算法实现**：
   - **GRPO**：使用 token 级重要性权重 $w_{i,t}(\theta)$ 进行 off-policy 修正。
   - **GSPO**：使用序列级裁剪重要性权重 $s_i(\theta)$（长度归一化），提升长序列场景的稳定性。

5. **任务特定奖励设计**：
   - **格式奖励** $R_{Format}$：强制结构化输出。
   - **任务奖励** $R_{Task}$：
     - 边界框：IoU 二值奖励 $R_{Bbox} = \mathbb{1}(\text{IoU}(B_p, B_{gt}) \geq \tau_{iou})$。
     - 分割：结合粗定位和 S-measure $R_{Seg} = \mathbb{1}(\text{IoU} \geq \tau_{iou}) + S_\alpha(M_p, M_{gt})$。
     - 抓取姿态：用 sin/cos 表示角度 $\theta$，对所有姿态分量应用 Huber 损失之和的负值。
     - 接触点：先转为抓取矩形，计算 IoU 和点距离。

6. **输出格式**：所有任务采用 `<think>...</think><answer>...</answer>` 格式，便于格式奖励计算。

---

## 3. 实验设计

### 3.1 数据质量评估
对比 Grasp-Anything 和 Grasp-Anything++，每数据集随机抽取 10,000 个样本，使用以下指标：
- **MTLD**：语言多样性
- **CLIP Score (S_CLIP)**：视觉-语言对齐度
- **R_s**：边界框内分割覆盖率
- **R_g**：分割掩码内抓取点比例
- **R_c**：分割掩码内接触点比例

### 3.2 RealVLG Benchmark 评测指标
- **定位**：gIoU、cIoU
- **分割**：S-measure ($S_\alpha$)、F-measure ($F_\beta$)
- **抓取**：mIoU、Grasp Accuracy（gAcc，IoU > 0.25 且角度偏差 < 30°）
- **有效性**：Validity Rate（VR / $R_v$），即非空且可解析输出的比例

### 3.3 对比方法
- **闭源模型**：Qwen-VL-Max、Gemini 2.5-Flash
- **开源模型**：Qwen2.5-VL-3B/7B 及其 SFT 变体（在 LLaMA-Factory 框架下实现）
- **本文方法**：RealVLG-R1-3B/7B，分别采用 GRPO 和 GSPO 算法（在 VERL 框架下实现）

---

## 4. 资源与算力

**论文中未明确说明**具体的 GPU 型号、数量或训练时长。仅提到：
- 训练数据量：仅使用 10% 的训练集，训练 10 个 epoch
- 训练框架：VERL（用于 RL 微调）、LLaMA-Factory（用于 SFT 基线）
- 模型规模：3B 和 7B 两个版本

**这一点是该论文的明显不足**，缺乏计算资源的详细报告，难以评估实验的可复现性和成本。

---

## 5. 实验数量与充分性

### 5.1 实验规模
- **数据集质量对比实验**：1 组（对比 Grasp-Anything、Grasp-Anything++）
- **基准评测实验**：在 3 个子集（Seen、Similar、Novel）上评估 4 个任务（Bbox、Seg、Grasp、Contact），共 **3 × 4 = 12 组实验配置**
- **对比方法**：8 种（Qwen-VL-Max、Gemini2.5-Flash、Qwen2.5-VL-3B、Qwen2.5-VL-3B+SFT、RealVLG-R1-3B-GRPO/GSPO、Qwen2.5-VL-7B、Qwen2.5-VL-7B+SFT、RealVLG-R1-7B-GRPO/GSPO）

### 5.2 充分性评价
**较为充分**：
- 覆盖了多个粒度任务和多个数据集划分
- 对比了闭源和开源模型，包含了 SFT 基线
- 评估了零样本泛化能力（Novel 子集）

**不足之处**：
- **缺少消融实验**：未对各奖励组件（格式奖励 vs 任务奖励）进行单独消融
- **缺少真实机器人抓取执行实验**：论文声称"支持真实场景零样本感知与操作"，但仅有离线评测数据，缺乏实际机器人物理执行的验证
- **缺少与 Grasp-Anything++ 等语言驱动抓取方法的直接对比**
- **未在杂乱场景中的端到端操作任务上评估**（如堆叠、放置等）

---

## 6. 主要结论与发现

### 6.1 数据集质量
RealVLG-11B 在所有可比指标上均优于现有数据集：
- MTLD 从 27.45/15.14 提升至 36.49（语言多样性更高）
- CLIP Score 从 0.54/0.52 提升至 0.65（语义对齐更强）
- R_s = 0.99（边界框与分割掩码几何高度一致）
- R_g 和 R_c 显著优于 Grasp-Anything

### 6.2 视觉定位任务
- RealVLG-R1-3B：gIoU 超过 87%（比 SFT 提升 30 个百分点）
- RealVLG-R1-7B：gIoU 进一步提升至 89%
- Novel 场景中仍保持强泛化能力（gIoU ~88%）
- 所有配置 VR = 100%，输出高度结构化

### 6.3 视觉抓取任务
- SFT 在抓取任务上表现很差（mIoU <5%，gAcc <3%），说明 token 级监督不足以保证物理可行性
- RL 微调显著提升：3B 模型 mIoU/gAcc 达 34.7%/40.3%
- 即使在 Novel 场景中仍保持合理准确率（mIoU/gAcc = 26.9%/20.2%）

### 6.4 GRPO vs GSPO
- **GRPO**：在小模型上奖励更敏感，抓取精度略高
- **GSPO**：在大模型上训练更稳定，接触点精度更高

---

## 7. 优点

1. **数据集规模与质量**：
   - 110 亿抓取样本，800+ 物体，是目前最大同时融合语义与视觉信息的真实场景数据集
   - 采用"GPT-4o 生成 → Qwen-VL-Max 验证 → 人工复核"的多级流水线，标注可靠性高
   - 多粒度标注（边界框、分割、抓取姿态、接触点、语言描述）一体化

2. **方法创新性**：
   - 首次将基于可验证奖励的强化学习微调应用于统一的多任务视觉-语言对齐与抓取
   - 解决抓取多解场景下 SFT 的固有缺陷，无需依赖确定性标签
   - 任务特定的复合奖励设计巧妙（角度用 sin/cos 编码、接触点先转矩形再评估）

3. **统一框架**：
   - 单一模型支持边界框、分割、抓取、接触点四种任务的端到端预测
   - 减少多阶段误差累积，提升语义一致性

4. **零样本泛化能力**：
   - 在 Novel 场景中仍保持较高准确率，证明良好的泛化性能

5. **完整的开源承诺**：代码与数据全部公开。

---

## 8. 不足与局限

1. **缺乏真实机器人执行验证**：论文核心声称"支持真实场景零样本感知与操作"，但仅展示了离线评测结果（gIoU、mIoU 等），未在实际机器人平台上进行物理抓取成功率的验证。这与论文标题中"Robotic Perception and Manipulation"形成落差。

2. **算力资源未披露**：未说明 GPU 型号、数量、训练时长，无法评估计算成本与可复现性。

3. **消融实验不充分**：
   - 缺少对各奖励组件（格式奖励 vs IoU 奖励 vs Huber 损失）的单独消融
   - 缺少对 RL 算法中关键超参数（如 β、采样数 G）的敏感性分析
   - 未对比不同 backbone 架构（如 LLaVA、InternVL 等）

4. **任务范围有限**：
   - 仅评估矩形抓取（4-DoF），未覆盖 6-DoF 抓取
   - 抓取对象局限于"桌面抓取"场景，未涉及更复杂的操作任务（如堆叠、放置、工具使用）
   - 接触点预测仅作为抓取的副产品，未独立深入分析

5. **数据偏差风险**：
   - 数据集由多个真实数据集整合而成，可能存在物体类别、场景复杂度、视角的分布偏差
   - 训练集仅 10% 数据量，模型性能可能受限于数据效率

6. **效率问题**：当前为 7B 模型，论文在未来工作中提到将探索 SmolVLM 等轻量模型，说明当前部署效率仍是瓶颈。

7. **评测局限性**：
   - gAcc 阈值（IoU > 0.25，角度 < 30°）可能过于宽松
   - 缺少对推理延迟、计算开销的评测

8. **泛化范围**：未在跨域（如工业、家庭、户外）场景下进行评估，应用边界尚不清晰。

（完）
