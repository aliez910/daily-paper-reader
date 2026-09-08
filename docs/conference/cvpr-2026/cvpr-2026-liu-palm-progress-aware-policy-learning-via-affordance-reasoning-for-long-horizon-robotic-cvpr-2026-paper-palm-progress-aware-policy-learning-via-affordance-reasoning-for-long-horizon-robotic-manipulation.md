---
title: "PALM: Progress-Aware Policy Learning via Affordance Reasoning for Long-Horizon Robotic Manipulation"
title_zh: PALM：基于可供性推理的长时程机器人操作进度感知策略学习
authors: "Liu, Yuanzhe, Zhu, Jingyuan, Mo, Yuchen, Li, Gen, Cao, Xu, Jin, Jin, Shen, Yifan, Li, Zhengyuan, Yu, Tianjiao, Yuan, Wenzhen, Ding, Fangqiang, Lourentzou, Ismini"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Liu_PALM_Progress-Aware_Policy_Learning_via_Affordance_Reasoning_for_Long-Horizon_Robotic_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于可供性推理的长时程机器人操作 VLA 框架
tldr: 现有视觉-语言-动作模型在长时程、多步骤机器人操作任务中容易出现重复动作、漏步与提前终止等问题，根源在于缺乏对任务相关交互线索与子任务进度的内部推理。为此，本文提出 PALM，一种以交互中心可供性推理与子任务进度线索为核心结构的 VLA 框架，通过蒸馏物体相关性、接触几何、空间布局与运动动态等可供性表征。该方法显著提升了长时程复杂操作任务中的执行成功率与鲁棒性，为通用 VLA 策略的可解释推理提供了新方案。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1750, \"height\": 863, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1738, \"height\": 791, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1630, \"height\": 719, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1803, \"height\": 599, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 876, \"height\": 317, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1801, \"height\": 396, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 868, \"height\": 310, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-liu-palm-progress-aware-policy-learning-via-affordance-reasoning-for-long-horizon-robotic-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1680, \"height\": 478, \"label\": \"Table\"}]"
motivation: 现有 VLA 模型缺乏内部推理机制，难以处理长时程多步骤操作任务。
method: 构建以可供性推理与子任务进度感知为核心的 VLA 框架，蒸馏交互相关表征。
result: 显著减少了重复动作、漏步与提前终止等执行错误。
conclusion: 为可解释的长时程通用机器人操作策略提供了新方法。
---

## Abstract
Recent advancements in vision-language-action (VLA) models have shown promise in robotic manipulation, yet they continue to struggle with long-horizon, multi-step tasks. Existing methods lack internal reasoning mechanisms that can identify task-relevant interaction cues or track progress within a subtask, leading to critical execution errors such as repeated actions, missed steps, and premature termination. To address these challenges, we introduce PALM, a VLA framework that structures policy learning around interaction-centric affordance reasoning and subtask progress cues. PALM distills complementary affordance representations that capture object relevance, contact geometry, spatial placements, and motion dynamics, and serve as task-relevant anchors for visuomotor control. To further stabilize long-horizon execution, PALM predicts continuous within-subtask progress, enabling seamless subtask transitions. Across extensive simulation and real-world experiments, PALM consistently outperforms baselines, achieving a 91.8% success rate on LIBERO-LONG, a 12.5% improvement in average length on CALVIN ABC->D, and a 2ximprovement over real-world baselines across three long-horizon generalization settings.

---

## 论文详细总结（自动生成）

<think>The user wants a structured Chinese summary of the PALM paper. Let me analyze the paper content carefully and organize it according to the 8 requested sections.

Let me go through each section:

1. Core problem and motivation: VLA models struggle with long-horizon, multi-step tasks due to lack of internal reasoning mechanisms for affordance cues and progress tracking.

2. Methodology: 
- Two main components: fine-grained affordance prediction module and progress-aware inverse dynamics policy
- Four affordance types: Global (object relevance via Grounding DINO + SAM), Local (contact geometry via Gaussian heatmaps like GLOVER++), Spatial (placement points via SpatialVLM + RoboPoint), Dynamic (motion via CoTracker)
- Two learnable query sets: affordance queries (Global, Local, Spatial, Dynamic) and action-progress queries
- GPT-2 backbone with diffusion transformer for action and progress prediction
- Pre-training on DROID, BridgeData V2, EPIC-KITCHENS, RoboCerebra; fine-tuning on 942 annotated trajectories

3. Experiments:
- CALVIN ABC→D benchmark
- LIBERO (Spatial, Object, Goal, Long)
- Real-world: xArm6, 6 subtasks, 3 generalization settings
- Baselines: RT-1, Robo-Flamingo, OpenVLA, Diffusion Policy, π0, 3D-VLA, 3D Diffuser Actor, RoboUniview, Susie, GR-1, Seer, Octo, SpatialVLA, CoT-VLA, TraceVLA, CoA-VLA

4. Resources/compute: Not explicitly mentioned in the extracted text.

5. Experimental quantity and adequacy:
- Multiple ablation studies (affordance components, training modules, data composition)
- Comparison against many baselines
- Multiple benchmarks and generalization tests

6. Main conclusions:
- SOTA on CALVIN ABC→D with 12.5% improvement in average length (4.48)
- 91.8% success on LIBERO-LONG
- 2x improvement over real-world baselines

7. Strengths:
- Novel integration of structured affordance prediction with progress-aware control
- Four complementary affordance types capturing different scales/aspects
- Continuous progress prediction for temporal consistency
- Comprehensive evaluation across simulation and real-world

8. Limitations:
- Limited real-world scenarios (only 6 subtasks in one setup)
- Reliance on annotated data (942 trajectories)
- Computational cost not analyzed
- Generalization to other embodiments not shown
- Closed-loop correction not addressed

Let me write the summary now.</think>

# PALM 论文总结

## 1. 核心问题与研究动机

- **问题背景**：视觉-语言-动作（VLA）模型在通用机器人操作上取得显著进展，但在**长时程、多步骤**任务中表现仍然不佳。
- **核心缺陷**：
  - 缺乏识别**任务相关交互线索**（affordance cues）的内部推理机制；
  - 缺乏对**子任务进度**的连续跟踪能力。
- **典型失败模式**：重复动作、漏掉必要步骤、提前终止、错误状态下报告成功。
- **根源分析**：传统行为克隆将异质子任务混合训练，压缩了不同阶段的判别信息，导致视觉相似但语义不同的状态难以区分，跨子任务过渡不稳定。

## 2. 方法论

### 2.1 整体框架
PALM 是一个端到端 VLA 框架，包含两大核心模块：
1. **细粒度可供性预测模块** `f_aff(l, o_t, s_t) → F̂_{t+n}`：预测未来偏移 `t+n` 处的可供性潜变量；
2. **进度感知逆动力学策略** `f_inv(l, o_t, s_t, F̂_{t+n}) → (â_{t:t+n-1}, p̂_{t:t+n-1})`：联合解码动作与连续进度标量 `p_t ∈ [0, 1]`。

### 2.2 架构组成
- **多模态编码器**：CLIP 文本编码 + MAE 视觉编码 + Perceiver Resampler + 状态 MLP；GPT-2 主干融合。
- **两组可学习查询**：
  - **可供性查询**：分为四个子查询 `<Global>`、`<Local>`、`<Spatial>`、`<Dynamic>`；
  - **动作-进度查询**：聚合上下文与可供性潜变量，条件化 DiT。
- **块式结构化注意力机制**：各子查询仅关注共享上下文，并使用因果注意力保持时间一致性。
- **解码器**：扩散 Transformer（DiT）联合输出 `n` 步动作序列与 `n` 步进度序列。

### 2.3 四类可供性预测
| 类型 | 含义 | 监督信号 | 损失函数 |
|---|---|---|---|
| **Global** | 指令相关的物体先验（mask + 特征） | Grounding DINO + SAM 生成的 mask | Focal Loss + Dice Loss |
| **Local** | 接触似然（高频局部几何） | GLOVER++ 风格的 Gaussian 热图 | Focal Loss + KL 散度 |
| **Spatial** | 可执行放置点候选 | SpatialVLM + RoboPoint 采样点 | 集合匹配（Set-matching）L2 损失 |
| **Dynamic** | 运动区域预测（夹爪/可动物体） | CoTracker 轨迹累计位移栅格化 | 掩码 VAE 重建 + KL 散度 |

### 2.4 进度感知逆动力学
- 将经典逆动力学扩展为 `n` 步形式；
- 进度值 `p_t` 与动作共同由 DiT 预测，附加到动作输出空间 `Ã = A × P`；
- 训练目标：标准扩散去噪 MSE 损失，对动作-进度联合向量加噪预测。

### 2.5 训练策略
- **预训练**：BridgeData V2、DROID（机器人数据）+ EPIC-KITCHENS、RoboCerebra（长时程视频）；
- **微调**：942 条人工标注轨迹（半自动方法），含可供性与连续进度标签。

## 3. 实验设计

### 3.1 仿真基准
- **CALVIN ABC→D**：在 A、B、C 环境预训练，在未见过的 D 环境测试，34 个任务；
- **LIBERO**：四个子套件（Spatial、Object、Goal、Long），各 10 个任务。

### 3.2 真实世界
- **平台**：UFACTORY xArm6 + Gripper G2 + 两台 RealSense D455（eye-on-hand + eye-on-base）；
- **任务**：6 个连续子任务的 pick-and-place，由单一高层指令驱动；
- **泛化设置**：
  - 随机位置（Random Localization）；
  - 视觉干扰物（Visual Distraction）；
  - 未见光照（Unseen Lighting）；
- **基线**：OpenVLA、Octo；每方法最多 3 次执行，20 次 rollout。

### 3.3 对比方法（共四类）
- **自回归类**：RT-1、Robo-Flamingo、OpenVLA；
- **扩散类**：Diffusion Policy、π0；
- **3D 感知类**：3D-VLA、3D Diffuser Actor、RoboUniview；
- **预测类**：Susie、GR-1、Seer、Octo、SpatialVLA、CoT-VLA、TraceVLA、CoA-VLA。

## 4. 资源与算力

- **论文中未明确提及**所用 GPU 型号、数量、训练时长、显存占用等算力细节。
- 仅有训练数据规模描述：942 条微调轨迹、200 条 xArm 真实世界微调数据。

## 5. 实验数量与充分性

- **消融实验**：
  - 四种可供性组件的累积消融（G → G+L → G+L+S → G+L+S+D）；
  - 三大核心模块（可供性、进度、逆动力学）的预训练与微调消融；
  - 训练数据组合消融（去除四类数据中任一种）；
- **基准覆盖**：CALVIN、LIBERO 四个子套件、真实世界三种泛化设置；
- **统计报告**：CALVIN 报告 1000 次 rollout 每任务前三 checkpoint 平均；LIBERO 报告 3 个种子 × 500 episodes 的均值±标准差。
- **充分性评估**：整体实验设计较系统，但真实世界任务仅 1 种语义结构（pick-and-place 序列）和单一机器人平台。

## 6. 主要结论与发现

- **CALVIN ABC→D**：PALM 平均长度 **4.48**，5 子任务成功率 **82.0%**，较先前 SOTA（Seer 64.3%）提升 **17.7 个百分点**；消融显示去掉进度预测性能下降（4.02）。
- **LIBERO-LONG**：成功率 **91.8%**，较最强基线（CoT-VLA 69.0%）提升 **22.8 个百分点**；四子套件平均 94.5%。
- **真实世界**：在三种长时程泛化设置下，平均长度均显著优于基线（3.05 / 3.80 / 3.55 vs OpenVLA 0.95 / 1.60 / 1.25、Octo 0.65 / 0.95 / 1.05），约 **2× 提升**。
- **关键消融发现**：
  - 去掉可供性预测 → 微调阶段下降最大（4.48 → 3.58）；
  - 去掉进度预测 → 预训练阶段下降最大（4.48 → 3.73）；
  - 去掉逆动力学预测 → 预训练与微调均下降；
  - 四类数据（in-the-wild、长时程视频、人工标注、仿真预训练）缺一不可。

## 7. 优点

- **结构化可供性表示**：将 affordance 拆解为 Global/Local/Spatial/Dynamic 四种互补潜变量，分别捕获物体相关性、接触几何、空间布局与运动动态，提供细粒度任务锚点；
- **进度感知控制**：连续标量 `p_t` 与动作联合去噪预测，提供显式时序正则，缓解跨子任务过渡模糊；
- **闭环感知-动作-进度框架**：将预测可供性作为策略条件变量，避免显式规划器或分层控制器；
- **预训练 + 微调范式结合多源数据**：融合机器人数据与长时程视频，提升语义进度先验；
- **全面评估**：覆盖仿真基准（CALVIN、LIBERO 全四套件）、多种方法类别、多种消融、真实世界三种泛化设置。

## 8. 不足与局限

- **算力与效率不透明**：未报告 GPU 型号、数量、训练时长等关键复现信息；
- **真实世界覆盖有限**：仅 xArm6 + 单一种类任务（6 步 pick-and-place），未验证其他机械臂、夹爪或操作语义；
- **标注成本依赖**：依赖 942 条人工半自动标注轨迹与 200 条真实世界演示，扩展到更大任务集合时成本较高；
- **可供性标注管线依赖外部模型**：Global 依赖 Grounding DINO+SAM、Spatial 依赖 SpatialVLM+RoboPoint、Dynamic 依赖 CoTracker，可能继承这些模型的偏差与失败模式；
- **未来预测偏移 `n` 固定**：未分析 `n` 取值对性能的影响；
- **缺乏失败分析与安全机制**：未讨论错误恢复、纠错闭环或安全检测模块；
- **跨具身泛化未验证**：仅在单一机器人本体训练与测试，未验证对其他形态机器人的迁移能力。

（完）
