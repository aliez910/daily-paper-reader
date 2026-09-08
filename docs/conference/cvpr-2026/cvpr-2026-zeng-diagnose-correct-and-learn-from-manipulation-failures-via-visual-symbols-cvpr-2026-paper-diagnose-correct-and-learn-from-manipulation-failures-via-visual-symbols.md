---
title: "Diagnose, Correct, and Learn from Manipulation Failures via Visual Symbols"
title_zh: 通过视觉符号诊断、纠正并学习机器人操作中的失败
authors: "Zeng, Xianchao, Zhou, Xinyu, Li, Youcheng, Shi, Jiayou, Li, Tianle, Chen, Liangming, Ren, Lei, Li, Yong-Lu"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zeng_Diagnose_Correct_and_Learn_from_Manipulation_Failures_via_Visual_Symbols_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 提出诊断VLA操作失败并从中学习的框架，针对真实复杂机器人任务
tldr: 本文针对现有视觉-语言-动作模型在机器人操作中难以诊断失败并从中学习的局限，指出当前失败数据集多为仿真生成、难以泛化到真实场景。为此，作者提出了ViFailback框架，通过显式视觉符号同时提供文本与视觉修正指导，并发布了包含58128个VQA对与5202条真实操作轨迹的大规模数据集。该工作推动了面向复杂操作任务的、具备失败感知能力的视觉模仿学习研究。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 782, \"height\": 665, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1641, \"height\": 875, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1627, \"height\": 945, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 790, \"height\": 433, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1548, \"height\": 482, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 811, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1817, \"height\": 808, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1818, \"height\": 811, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zeng-diagnose-correct-and-learn-from-manipulation-failures-via-visual-symbols-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 864, \"height\": 248, \"label\": \"Table\"}]"
motivation: VLA模型在真实操作中失败诊断与失败学习能力不足，且真实失败数据稀缺。
method: 提出ViFailback框架，结合显式视觉符号提供文本与视觉双重修正指导。
result: 构建大规模真实失败数据集，显著增强了模型对操作失败的诊断与学习能力。
conclusion: 视觉符号化的失败学习机制推动了复杂操作任务中SOTA视觉模仿学习的进步。
---

## Abstract
Vision-Language-Action (VLA) models have recently achieved remarkable progress in robotic manipulation, yet they remain limited in failure diagnosis and learning from failures. Additionally, existing failure datasets are mostly generated programmatically in simulation, which limits their generalization to the real world. In light of these, we introduce ViFailback, a framework designed to diagnose robotic manipulation failures and provide both textual and visual correction guidance. Our framework utilizes explicit visual symbols to enhance annotation efficiency. We further release the ViFailback dataset, a large-scale collection of 58,128 Visual Question Answering (VQA) pairs along with their corresponding 5,202 real-world manipulation trajectories. Based on the dataset, we establish ViFailback-Bench, a benchmark of 11 fine-grained VQA tasks designed to assess the failure diagnosis and correction abilities of Vision-Language Models (VLMs), featuring ViFailback-Bench Lite for closed-ended and ViFailback-Bench Hard for open-ended evaluation. To demonstrate the effectiveness of our framework, we built the ViFailback-8B VLM, which not only achieves significant overall performance improvement on ViFailback-Bench but also generates visual symbols for corrective action guidance. Finally, by integrating ViFailback-8B with a VLA model, we conduct real-world robotic experiments demonstrating its ability to assist the VLA model in recovering from failures. Project page: https://x1nyuzhou.github.io/vifailback.github.io/

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Diagnose, Correct, and Learn from Manipulation Failures via Visual Symbols" following a specific structure. Let me organize the content based on the paper's information.

The paper is about ViFailback framework for diagnosing and correcting robotic manipulation failures using visual symbols. Let me go through each required section:

1. Core problem and motivation: VLA models struggle with failure diagnosis and learning from failures; existing failure datasets are simulation-based with sim-to-real gap.

2. Methodology: ViFailback framework with 7 visual symbols (motion, spatial relation, state), annotation pipeline, ViFailback-8B VLM finetuned from Qwen3-VL-8B with LoRA.

3. Experiments: ViFailback-Bench (Lite closed-ended, Hard open-ended) with 500 trajectories, 22 tasks, 11 VQA types; compared with 16 models including GPT-4o, Gemini-2.5-Pro, Qwen2.5-VL series, Qwen3-VL series, InternVL3 series, RoboBrain2.0 series, Cosmos-Reason1-7B.

4. Resources: Not explicitly mentioned in the paper - need to note this.

5. Number of experiments: Multiple tables, finetuning data scaling experiments, real-world experiments on 3 tasks with 21 trials each.

6. Conclusions: ViFailback-8B significantly outperforms baselines, with 22.2% improvement when integrated with VLA model.

7. Strengths: Visual symbols for efficient annotation, large-scale real-world dataset, comprehensive benchmark, real-world validation.

8. Limitations: Mentioned in the discussion about action distribution in failure trajectories not being utilized; also performance has not saturated indicating need for more data.

Let me write this in Chinese with proper Markdown structure.
</think>
# 论文总结：Diagnose, Correct, and Learn from Manipulation Failures via Visual Symbols

## 1. 核心问题与研究动机

- **VLA 模型的失败盲点**：Vision-Language-Action (VLA) 模型（如 π0.5、OpenVLA、RT-2 等）在大规模模仿学习下表现优异，但在真实部署中遇到 OOD（分布外）场景时仍会产生大量失败，且**缺乏诊断、纠正与从失败中学习的能力**。
- **现有失败数据集的局限**：当前主流失败数据集（如 RACER、AHA、RoboFAC 等）大多通过**仿真扰动程序化生成**，受 sim-to-real gap 限制，难以泛化到真实世界。
- **真实失败数据未被充分利用**：在遥操作与策略 rollout 过程中，会自然产生大量失败轨迹，但**缺乏高效、低成本的标注方法**来利用这些数据。
- **文本指导的脆弱性**：现有方法多为 VLM 提供文本反馈，但当前 VLA 模型对**自然语言指令遵循能力脆弱**，导致纠正效果有限。
- **核心研究问题**：如何高效标注真实世界的失败数据？如何让 VLM 既能诊断失败又能提供**可被 VLA 直接执行的纠正信号**？

## 2. 方法论

### 2.1 核心思想
提出 **ViFailback 框架**，使用**显式视觉符号**（visual symbols）作为：
- 标注阶段的高效标注工具（鼠标拖拽即可完成）；
- 模型输出的可解释纠正信号（VLA 可直接"看懂"）。

### 2.2 七种视觉符号设计
分为三类：
- **运动符号（Motion Symbols）**：
  - 彩色直线箭头：用颜色编码 3D 方向（红=前后、绿=左右、蓝=上下）；
  - 半圆弧箭头：表示末端执行器的旋转方向（顺时针/逆时针）。
- **空间关系符号（Spatial Relation Symbols）**：
  - 双十字准星 + 虚线：表示两个目标需要对齐；
  - 十字准星：高亮理想目标对象或区域。
- **状态符号（State Symbols）**：
  - ON/OFF 标签：指示夹爪开/关；
  - 禁止图标：指示末端应停止；
  - 倒带图标：指示末端或物体需回退到之前状态。

每个符号记录关键元素（类别、起点、终点、方向等），使 VLM 能**像人类标注者一样绘制视觉纠正指导**。

### 2.3 细粒度任务定义
- **失败诊断（Failure Diagnosis）** 5 个子任务：失败检测、关键帧定位、失败子任务定位、失败类型识别、失败原因分析。
- **纠正指导（Corrective Action Guidance）** 3 个子任务：低层文本指导、高层文本指导、视觉指导。
- **4 类失败类型**：任务规划错误、夹爪 6D 位姿错误、夹爪状态错误、人为干预。

### 2.4 三阶段数据标注流水线
- **阶段 1**：通过 UI 控件（滑块、按钮）完成基础失败诊断标注；任务描述由 Qwen2.5-Max 分解为子任务。
- **阶段 2**：标注者选择合适的纠正选项，并**用鼠标拖拽绘制视觉符号**。
- **阶段 3**：用 Qwen3-VL-235B 结合已标注信息生成高层描述（失败推理与高层指导），再经人工校验精修。

### 2.5 模型训练
- 基于 **Qwen3-VL-8B** 基模，使用 **LoRA** 微调 1 个 epoch，得到 **ViFailback-8B**。
- 训练集：52,418 VQA 对，来自 4,702 条轨迹，覆盖 95 个任务。

### 2.6 VLA 集成方法
- **VSF（Visual Symbols-Following）方法**：收集低层运动轨迹并标注视觉符号，类似 PEEK 掩膜无关区域，对 π0.5 进行端到端 SFT。
- **PMC（Point-based Motion Control）方法**：用低级运动控制器驱动末端执行器跟随视觉符号，必要时调用 GraspNet 估计抓取姿态。

## 3. 实验设计

### 3.1 数据集与基准
- **ViFailback 数据集**：
  - 5,202 条真实操作轨迹，覆盖 100 个任务；
  - 58,128 个 VQA 对，11 种细粒度 VQA 任务；
  - 使用 ALOHA 双臂机器人平台采集；
  - 657 条成功轨迹 + 4,545 条失败轨迹；
  - 4,995 条来自人工遥操作，其余来自 π0.5 rollout。
- **ViFailback-Bench**（500 条轨迹，22 个任务）：
  - **ViFailback-Bench Lite（闭卷）**：2,622 个 VQA 对，6 类任务（失败检测、关键帧定位、子任务定位、失败类型识别、低层规避、低层纠正）；
  - **ViFailback-Bench Hard（开卷）**：2,192 个 VQA 对，5 类任务（低层 CoT 规避、低层 CoT 纠正、失败原因、高层规避、高层纠正）。

### 3.2 对比方法（共 16 个模型）
- **通用开源 VLM**：Qwen2.5-VL-3B/7B/32B/72B、Qwen3-VL-2B/4B/8B/32B、InternVL3-8B/78B；
- **具身 VLM**：RoboBrain2.0-3B/7B/32B、Cosmos-Reason1-7B；
- **闭源商用 VLM**：GPT-4o、Gemini-2.5-Pro。

### 3.3 评估指标
- 多选题：使用准确率（%）；
- 开放题：使用 GPT-4o 作为评判器，从**语义相似性、内容完整性、功能等价性**三维度打分取均值。

### 3.4 真实世界验证
- 平台：ALOHA 双臂机器人；
- VLA 模型：π0.5；
- 3 个未见任务：**PlaceOne、PlaceTwo、Pull&Place**；
- 每个方法每个任务做 21 次试验，对比 4 种配置：
  - π0.5(base & symbol) 不带 ViFailback 纠正；
  - π0.5(base) 不带 ViFailback 纠正；
  - π0.5(base & symbol) + VSF 带 ViFailback 纠正；
  - π0.5(base) + PMC 带 ViFailback 纠正。

## 4. 资源与算力

- **论文中未明确说明** GPU 型号、数量、训练时长等具体算力信息。
- 可推断信息：
  - 训练使用 LoRA 微调 Qwen3-VL-8B，训练 1 个 epoch；
  - 评估涉及 16 个 VLM，闭源模型通过 API 调用；
  - 真实实验使用 ALOHA 双臂机器人平台（2 个腕部相机 + 1 个头部相机）。

## 5. 实验数量与充分性

### 5.1 实验规模
- **主结果表（Table 1）**：16 个模型在 ViFailback-Bench 上的整体性能对比；
- **Lite 详细分析（Table 2）**：6 个子任务的细粒度对比；
- **Hard 详细分析（Table 3）**：5 个子任务的细粒度对比；
- **数据规模消融（Figure 4）**：使用 1,200 / 2,400 / 3,600 / 4,702 条轨迹 4 个数据量级训练，分析 12 类 VQA 任务性能；
- **真实世界实验（Table 4）**：3 个任务 × 4 种方法 × 21 次试验 = 252 次真实试验；
- **定性可视化（Figure 5）**：3 个任务的关键帧与视觉提示可视化。

### 5.2 公平性与客观性评估
- **基准公平**：所有模型在统一 ViFailback-Bench 上评估；
- **真实实验公平**：每个方法使用相同初始布局与设置，每任务 21 次试验；
- **对比方法广泛**：涵盖开源/闭源、通用/具身共 16 个模型；
- **潜在偏差风险**：
  - 闭卷与开卷任务使用 GPT-4o 评判，可能引入评判器偏差；
  - 真实实验任务数量（仅 3 个）相对有限；
  - 视觉符号标注依赖人工，质量受标注者主观影响。

## 6. 主要结论与发现

- **基准整体表现不佳**：当前最佳闭源模型 Gemini-2.5-Pro 在 Lite 上仅 54.64%，GPT-4o 在 Hard 上仅 40.00%，说明 VLM 在**机器人失败诊断与纠正方面仍存在显著差距**。
- **ViFailback-8B 大幅领先**：
  - Lite 上达到 **93.70%**，较最佳基线（Gemini-2.5-Pro 54.64%）提升 **39.14%**；
  - Hard 上达到 **72.64%**，较最佳基线（GPT-4o 40.00%）提升 **32.64%**；
  - 较其 zero-shot 同基模型（Qwen3-VL-8B）提升 **39.6%**。
- **数据规模效应显著**：性能随训练数据量持续提升（尚未饱和），每增加 1 人时标注平均带来 0.64% 准确率提升；视觉符号代码生成任务从 0 提升到 38.73%。
- **真实世界应用价值**：将 ViFailback-8B 集成到 π0.5 后，**任务成功率平均提升 22.2%**（VSF +20.6%，PMC +23.8%）。
- **方法对比**：PMC 在多数任务上优于 VSF，表明**低级运动控制器跟随视觉符号**比端到端 SFT 更有效。
- **视觉符号 vs 文本**：视觉符号化的纠正比纯语言指令更直接有效，是连接 VLM 反馈与 VLA 行动的关键桥梁。

## 7. 优点与亮点

- **真实世界数据规模**：5,202 条真实轨迹 + 58,128 VQA 对，是目前规模最大的**真实机器人失败诊断数据集**之一，填补了 sim-to-real gap 的关键空白。
- **标注机制创新**：7 类视觉符号 + 鼠标拖拽 + VLM 辅助，**显著降低标注成本**，每条标注约 30 秒。
- **双重输出设计**：ViFailback-8B 同时输出**结构化 JSON + 视觉符号绘制代码**，既可解释又可执行。
- **任务定义细粒度**：11 类 VQA 任务覆盖从检测、定位到推理、指导的完整链条，任务定义清晰。
- **CoT 推理设计**：Hard 基准强制模型**先检测定位再输出指导**，更贴近实际纠错流程。
- **真实世界闭环验证**：不仅在 VQA 上评估，还在 ALOHA 平台上做了完整的 VLM-VLA 协作系统验证。
- **基准全面**：Lite（闭卷）+ Hard（开卷）+ 11 类任务细粒度分解，**评估维度立体**。

## 8. 不足与局限

- **算力信息缺失**：未公开训练所需的 GPU 型号、数量、训练时长等关键信息，复现门槛不透明。
- **真实实验任务覆盖有限**：仅 3 个真实任务（PlaceOne、PlaceTwo、Pull&Place），且都相对简单，对复杂多步任务的泛化能力尚待验证。
- **数据规模仍未饱和**：作者明确表示性能未饱和，但**未给出训练数据的天花板**或预期饱和点。
- **动作分布信息未利用**：作者在 Discussion 中明确指出，**失败轨迹中的动作分布信息**（而非仅视觉符号）这一"价值丰富的信息"尚未被利用。
- **视觉符号依赖人工绘制**：标注质量受人工主观影响，且视觉符号体系可能**不适用于所有任务类型**（如高度动态或长程任务）。
- **失败类型不均衡**：4 类失败中"任务规划"和"6D 位姿"占主导，其他类型样本可能不足。
- **VLA 集成需额外训练**：π0.5 本身不能直接遵循视觉符号，需要 VSF 额外 SFT 数据或 PMC 控制器，**增加系统复杂度**。
- **基模型偏依赖 Qwen3-VL**：未探索在其他 VLM 基模型（如 InternVL、LLaVA）上的迁移效果，泛化性未充分验证。
- **评判器偏差**：开卷任务使用 GPT-4o 作为评判器，可能**偏好同类模型输出**，引入评估偏差。
- **静态视觉符号局限**：当前视觉符号为静态绘制，**未探索视频级时序符号**对动态纠正的潜在价值。

（完）
