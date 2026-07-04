---
title: "Magma: A Foundation Model for Multimodal AI Agents"
title_zh: Magma：面向多模态AI智能体的基础模型
authors: "Yang, Jianwei, Tan, Reuben, Wu, Qianhui, Zheng, Ruijie, Peng, Baolin, Liang, Yongyuan, Gu, Yu, Cai, Mu, Ye, Seonghyeon, Jang, Joel, Deng, Yuquan, Gao, Jianfeng"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Yang_Magma_A_Foundation_Model_for_Multimodal_AI_Agents_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向机器人操纵的通用视觉-语言-动作基础模型
tldr: Magma是一个面向多模态AI智能体的基础模型，扩展了视觉-语言模型，新增空间-时间智能以在物理世界中执行动作。该模型在大规模图像、视频和机器人数据上训练，通过Set-of-Mark标注实现动作落地，覆盖UI导航到机器人操纵等多种任务。Magma具备视觉空间理解与行动能力，是通用视觉-动作模型的代表。该工作为构建跨数字与物理世界的一般智能体提供了统一基础，与通用视觉-动作模型主题高度契合。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1774, \"height\": 768, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 877, \"height\": 240, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 584, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 865, \"height\": 404, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1801, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 799, \"height\": 383, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 881, \"height\": 666, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1803, \"height\": 507, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 869, \"height\": 181, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1815, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 868, \"height\": 335, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-yang-magma-a-foundation-model-for-multimodal-ai-agents-cvpr-2025-paper/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1812, \"height\": 496, \"label\": \"Table\"}]"
motivation: 现有视觉语言模型缺少空间-时间智能，难以在物理世界中执行动作。
method: 在图像、视频、机器人异构数据上训练，通过Set-of-Mark实现动作落地。
result: 在UI导航和机器人操纵等多种智能体任务上展现出通用视觉-动作能力。
conclusion: Magma统一了数字与物理世界的智能体能力，推动通用视觉-动作模型发展。
---

## Abstract
We present Magma, a foundation model that serves multimodal AI agentic tasks in both the digital and physical worlds. Magma is a significant extension of vision-language (VL) models in that it not only retains the VL understanding ability (verbal intelligence) of the latter, but is also equipped with the ability to ground and act in the visual-spatial world (spatial-temporal intelligence). To endow agentic capabilities for tasks ranging from UI navigation to robot manipulation, Magma is trained on large amounts of heterogeneous datasets that span from images, videos to robotics data, where actionable visual objects (e.g. clickable buttons in GUI) in images are labeled by Set-of-Mark (SoM) for action grounding, and object movements (e.g. trace of human hands or robotic arms) in videos are labeled by Trace-of-Mark (ToM) for action planning. Extensive experiments show that SoM and ToM help bridge the gap between verbal and action abilities and significantly enhance spatio-temporal intelligence which is fundamental to agentic tasks, as shown in Fig.1. In particular, Magma creates new state-of-the-art results on UI navigation and robotic manipulation tasks, outperforming previous models that are specifically tailored to these tasks. Moreover, Magma preserves strong multimodal understanding ability and compares favorably to popular large multimodal models that are trained on much larger datasets. We have made our model and code public for reproducibility at https://microsoft.github.io/Magma.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the Magma paper, organized in a specific Markdown structure with 8 sections. Let me carefully analyze the paper content and produce a comprehensive summary.

Let me go through each required section:

1. Core problem and overall meaning (motivation/background)
2. Methodology: core ideas, key technical details, formulas/algorithms
3. Experimental design: datasets, benchmarks, comparisons
4. Resources and compute: GPU types, training time, etc.
5. Number and sufficiency of experiments
6. Main conclusions and findings
7. Strengths
8. Limitations

I need to extract specific details from the paper:
- Model: Magma-8B, uses LLaMA-3-8B as LLM backbone, ConvNeXt-XXLarge as vision encoder
- Key innovations: Set-of-Mark (SoM) for action grounding, Trace-of-Mark (ToM) for action planning
- Training data: 39M samples total including images, videos, UI navigation data, robotics data
- Datasets: ShareGPT4V, LLaVA-1.5 SFT, Open X-Embodiment, SeeClick, Vision2UI, Ego4D, Epic-Kitchen, Somethingv2
- Evaluation: ScreenSpot, VisualWebBench, SimplerEnv, Mind2Web, AITW, WidowX Robot, VSR, BLINK, SpatialEval, VideoQA benchmarks
- Results: New SOTA on UI navigation and robotics, outperforms OpenVLA by 20.8% on SimplerEnv
- Training: 3 epochs, learning rate 1e-5

Let me now structure this comprehensively in Chinese.
</think>
# Magma：面向多模态AI智能体的基础模型 — 论文总结

## 1. 核心问题与整体含义

- **研究动机**：当前视觉-语言-动作（VLA）模型虽然在各自领域取得进展，但普遍存在"领域割裂"问题：UI导航（如Pix2ACT、SeeClick）与机器人操纵（如RT-2、OpenVLA）模型各自独立训练，导致模型在一种任务上表现出色，却在另一类任务上能力退化，且都牺牲了通用多模态理解能力。
- **整体目标**：构建一个**统一的跨数字/物理世界多模态智能体基础模型**，同时具备两类核心能力：
  - **多模态理解（verbal intelligence）**：图像/视频的语义、空间、时序理解
  - **多模态动作预测（spatial-temporal intelligence）**：在2D数字界面和3D物理环境中执行精确动作
- **核心挑战**：
  - **任务异构**：UI任务预测2D坐标，机器人任务预测7-DoF动作，二者输出空间差距大
  - **数据稀缺**：最大的机器人数据集 Open X-Embodiment 仅约1M轨迹，覆盖22个环境
  - **数据未利用**：大量未标注的instructive videos未被有效利用
  - **统一接口缺失**：需要寻找"surrogate tasks"（代理任务）弥合理解与动作之间的鸿沟

## 2. 方法论

### 2.1 核心思想

提出**两种代理训练目标**（surrogate tasks）来弥合verbal与spatial智能之间的鸿沟，将异构数据（图像、视频、UI、机器人）统一到同一接口下训练：

- **Set-of-Mark (SoM)**：用于**动作定位（Action Grounding）**——在图像中给可操作对象打上数字标签mark
- **Trace-of-Mark (ToM)**：用于**动作规划（Action Planning）**——沿时间轴追踪mark的未来轨迹

### 2.2 关键公式

**统一的多模态智能体形式化**：
$$O^l = \pi(I, \text{task})$$
其中 $l \in \{\text{verbal}, \text{spatial}\}$，$I$ 为历史视觉观测，task 为文本任务描述。

**SoM动作定位**（式2）：
$$o_{\text{mark}}^t = \{\text{action}^t : \text{mark}^t\} = \pi(I_M^t, \text{task})$$
模型从带mark的图像中预测动作类型和正确的mark编号。

**ToM动作规划**（式3）：
$$o_{\text{mark}}^t = \{\text{action}^t : \text{mark}^t : \text{trace}^{t+1:l}\} = \pi(\{I^1,...,I^{t-1}, I_M^t\}, \text{task})$$
模型需要预测未来 $l-t$ 帧的mark轨迹。

### 2.3 算法流程

- **SoM生成（Algorithm 1）**：
  - 输入：图像 $I$、候选bounding boxes $B$、图像尺寸
  - 为每个box分配文本标签（数字编号），绘制矩形框
  - 通过 `FindOptimalCorner` 寻找离已绘制box最远的角落放置标签，避免重叠
  - 输出：带mark标注的图像

- **ToM生成（Algorithm 2）**：
  - 在初始帧放置 $s \times s$ 网格点（$s=15$）
  - 使用 **CoTracker** 提取像素级未来轨迹
  - 若存在全局相机运动（阈值 $\eta=2$），应用**单应性变换（Homography Transformation）**消除相机移动：
    $$h_i = H(M_t, M_{t+i}) \in \mathbb{R}^{3\times 3}$$
  - 根据相邻帧平均运动幅值（阈值 $\epsilon=2$）将轨迹分类为前景/背景
  - K-Means聚类前后景轨迹，随机选1至多个聚类中心作为最终ToM
  - 在第一帧应用SoM可视化

### 2.4 训练细节

- **模型架构**：LLaMA-3-8B 语言骨干 + ConvNeXt-XXLarge 视觉编码器（支持任意分辨率）
- **动作表示**：
  - 2D坐标 → 文本字典表示
  - 7-DoF机器人动作 → LLM最后256个离散token（与OpenVLA一致）
  - 坐标归一化到图像尺寸后量化为256 bin
- **训练方式**：端到端联合训练，视觉编码器与LLM全部微调
- **优化器**：学习率恒为 $1e-5$，最多3个epoch

## 3. 实验设计

### 3.1 训练数据（39M样本总计）

| 数据类型 | 数据集 | 样本量 |
|---|---|---|
| 多模态理解 | ShareGPT4V、LLaVA-1.5、OCR相关数据集 (Magma-SFT) | ~2M |
| UI导航 | SeeClick、Vision2UI | ~2.75M |
| 机器人操纵 | Open X-Embodiment | 9.4M |
| 教学视频 | Ego4D、Epic-Kitchen、Something-v2、其他 | ~25.1M |

### 3.2 模型变体

- **Magma-8B (UI)**：仅UI数据
- **Magma-8B (OXE)**：仅机器人数据
- **Magma-8B (ACT)**：UI + 机器人
- **Magma-8B (Full)**：全部数据 + SoM/ToM（默认模型）

### 3.3 Benchmark与对比方法

**多模态理解（Zero-shot）**：
- VQAv2、TextVQA、POPE
- 对比：GPT-4V、LLaVA-1.5/Next、Qwen-VL、Fuyu

**UI动作定位与导航**：
- ScreenSpot（Mobile/Desktop/Web）——对比 SeeClick、Qwen-VL-Chat、Fuyu
- VisualWebBench（VWB）——对比 GPT-4V+OmniParser

**机器人操纵（Zero-shot）**：
- SimplerEnv（Google Robot 8任务172场景、Bridge）——对比 Octo、RT-1-X、OpenVLA

**下游微调**：
- Mind2Web（Web UI）——对比 GPT-4-MindAct、SeeClick、CogAgent、Qwen2-UIX 等
- AITW（移动UI）
- 真实 WidowX 250 机械臂（4个新任务）

**空间与时序推理**：
- VSR、BLINK、SpatialEval
- VideoQA: IntentQA、NextQA、VideoMME、MVBench
- 对比：Gemini-1.5、GPT-4V、LLaVA-OV、Video-Chat2 等

## 4. 资源与算力

- **论文未明确披露**：
  - 未提供具体GPU型号与数量
  - 未给出训练时长（epoch数与wall-clock time）
  - 未给出参数量对应的总算力消耗（FLOPs）
- **可推断信息**：
  - 训练最多3个epoch，恒定学习率 $1e-5$
  - 8B参数规模模型联合微调LLM与视觉编码器
  - 整个预训练数据集39M样本，单epoch遍历成本较高
- 这一点是论文的一个明显信息缺失。

## 5. 实验数量与充分性

- **实验规模较大且较为系统**：
  - 涵盖3大类任务（理解、UI、机器人）+ 空间/时序推理细分
  - 超过20个benchmark
  - 多个模型变体消融（UI-only / OXE-only / ACT / Full / Full-w/o SoM+ToM）
  - 真实机器人验证（10 trials × 4 tasks）
- **消融研究**：
  - 表3对比了不同数据组合与SoM/ToM开关效果
  - 验证了SoM+ToM是"关键且必要"的代理任务——无SoM+ToM时仅简单合并数据反而伤害性能
- **公平性考量**：
  - 论文坦诚指出 Magma 缺乏post-training（指令微调）阶段，在需要打印完整答案选项的benchmark上可能吃亏
  - 对部分benchmark补充说明了使用full answer matching与standard option matching的差异
  - 机器人实验中两个模型使用相同的初始状态进行公平对比
- **不足之处**：
  - 真实机器人仅4个任务、每任务10次试验，统计意义有限
  - 未在更大规模真实环境（多家具/多房间）验证泛化性
  - 空间推理部分被脚注说明受指令遵循能力不足影响，部分结果可能受评估pipeline偏差影响

## 6. 主要结论与发现

- **UI导航新SOTA**：
  - 在SimplerEnv上Magma较OpenVLA平均成功率提升**20.8%**（近翻倍）
  - 在VWB上零样本性能**84.1 vs GPT-4V+OmniParser的71.6**
- **机器人操纵新SOTA**：
  - 真实WidowX上4个任务中3个明显优于OpenVLA
  - "Pick Place Hotdog Sausage"、"Put Mushroom in Pot"等需精确操作的任务上OpenVLA几乎无法完成，Magma成功率显著
  - 域外任务"Push Cloth Left to Right"显示Magma具有更强的空间泛化
- **下游任务上SOTA**：
  - Mind2Web 三个子集Step SR均显著领先：Cross-Website 45.4、Cross-Task 43.4、Cross-Domain 47.3（次优为Qwen2-UIX的31.0/38.2/34.9）
- **空间/时序能力显著增强**：
  - VSR 65.1（无SoM/ToM仅58.1）、SpatialEval 41.6
  - IntentQA 80.9、NextQA 72.9、MVBench 59.4，超越多数10B以下视频LMM
- **关键洞察**：
  - 简单拼接异构数据集无法带来增益，反而伤害性能
  - **SoM+ToM是统一数字与物理世界的关键**：通过把动作预测统一为"在带mark的图像上选mark"问题，可从大量未标注视频中挖掘动作监督

## 7. 优点

- **方法论创新性高**：
  - SoM+ToM的代理任务设计巧妙，将"动作定位"和"动作规划"统一为可视化预测问题
  - 首次用统一模型覆盖UI导航+机器人操纵+多模态理解三类任务，打破领域壁垒
- **数据规模与多样性突出**：
  - 39M异构样本，包含大规模未标注教学视频的自动标注利用
  - ToM生成pipeline（CoTracker + Homography + KMeans聚类）解决了相机运动干扰
- **实验覆盖全面**：
  - 横跨数字/物理世界，多个benchmark SOTA
  - 同时验证zero-shot、efficient finetune、真实机器人三种设定
  - 消融实验清晰揭示了SoM/ToM的必要性
- **开源且可复现**：模型、代码、数据均已公开
- **与OpenVLA相比的明显优势**：
  - 不仅性能更强，还保持通用VL能力（OpenVLA牺牲了通用理解）
  - 通过homography处理相机运动，使其对ego-centric video和机器人轨迹均适用

## 8. 不足与局限

- **算力与训练信息不透明**：未披露GPU型号/数量、训练时长、数据准备耗时，使复现成本难以预估
- **真实机器人验证有限**：
  - 仅4个任务、每任务10次试验，样本量小
  - 只在单一机械臂平台（WidowX 250）验证，未涉及多机械臂/多平台泛化
- **Post-training缺失**：
  - 模型缺乏指令微调阶段，在需要"输出完整答案选项"的benchmark上需依赖评估pipeline workaround
  - 可能影响在真实人机交互场景中的指令遵循能力
- **评估偏差风险**：
  - ScreenSpot的SoM生成依赖OmniParser（GPT-4V+OmniParser的强基线亦使用相同工具，可能高估Magma相对于其他UI模型的差距）
  - VSR等benchmark使用*号标注作者自行评估的模型权重，与原文献报告可能存在测量差异
- **ToM的局限**：
  - K-Means聚类随机选点可能引入噪声
  - Homography变换仅能消除刚体相机运动，对非刚体或复杂场景运动可能失效
  - 网格采样s=15较粗，可能漏掉小目标的关键轨迹
- **2D/3D动作统一性不彻底**：
  - 2D UI动作（坐标点）和7-DoF机器人动作（256个离散token）实际使用不同表示，仅在概念上"统一"
  - 量化到256 bin可能对精细机器人控制造成精度损失
- **应用范围限制**：
  - 论文聚焦于navigation/简单manipulation，未涉及长horizon任务、复杂多步规划
  - 教学视频ToM的语义信息未充分利用，mark只编码运动轨迹而无语义标签
- **可解释性与安全**：
  - 论文未深入讨论智能体在物理世界中的安全部署、风险评估
  - 缺乏对失败模式的系统分析

（完）
