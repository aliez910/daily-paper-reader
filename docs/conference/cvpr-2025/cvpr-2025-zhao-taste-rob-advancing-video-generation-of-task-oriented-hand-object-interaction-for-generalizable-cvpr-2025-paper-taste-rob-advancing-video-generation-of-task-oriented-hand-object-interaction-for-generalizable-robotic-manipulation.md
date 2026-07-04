---
title: "TASTE-Rob: Advancing Video Generation of Task-Oriented Hand-Object Interaction for Generalizable Robotic Manipulation"
title_zh: TASTE-Rob：面向可泛化机器人操纵的任务导向手-物交互视频生成
authors: "Zhao, Hongxiang, Liu, Xingchen, Xu, Mutian, Hao, Yiming, Chen, Weikai, Han, Xiaoguang"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Zhao_TASTE-Rob_Advancing_Video_Generation_of_Task-Oriented_Hand-Object_Interaction_for_Generalizable_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 生成用于机器人模仿学习的任务导向手-物交互视频演示
tldr: 现有手-物交互视频数据集如Ego4D普遍存在视角不一致和交互错位问题，限制了其在精确模仿学习中的应用。本文提出TASTE-Rob大规模数据集，包含十万余段以自我中心视角拍摄、与语言指令严格对齐的手-物交互视频。基于该数据微调的视频生成模型可生成高质量任务演示，为可泛化机器人模仿学习提供重要数据支撑，有助于推动通用操纵策略的发展。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 857, \"height\": 438, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 779, \"height\": 263, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 689, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 697, \"height\": 467, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 775, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 693, \"height\": 441, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 791, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 794, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-009.webp\", \"caption\": \"\", \"page\": 0, \"index\": 9, \"width\": 1761, \"height\": 644, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/fig-010.webp\", \"caption\": \"\", \"page\": 0, \"index\": 10, \"width\": 791, \"height\": 546, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 852, \"height\": 146, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1705, \"height\": 574, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 645, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 727, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-zhao-taste-rob-advancing-video-generation-of-task-oriented-hand-object-interaction-for-generalizable-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 783, \"height\": 448, \"label\": \"Table\"}]"
motivation: 现有手-物交互数据集存在视角不一致和交互错位，制约精确模仿学习。
method: 构建十万段自我中心、与指令对齐的TASTE-Rob视频数据集并微调视频生成模型。
result: 生成高质量任务演示视频，为可泛化机器人模仿学习提供可靠数据基础。
conclusion: 高质量大规模交互视频数据集是推动通用机器人模仿学习的关键基础设施。
---

## Abstract
We address key limitations in existing datasets and models for task-oriented hand-object interaction video generation, a critical approach of generating video demonstrations for robotic imitation learning. Current datasets, such as Ego4D, often suffer from inconsistent view perspectives and misaligned interactions, leading to reduced video quality and limiting their applicability for precise imitation learning tasks. Towards this end, we introduce TASTE-Rob -- a pioneering large-scale dataset of 100,856 ego-centric hand-object interaction videos. Each video is meticulously aligned with language instructions and recorded from a consistent camera viewpoint to ensure interaction clarity. By fine-tuning a Video Diffusion Model (VDM) on TASTE-Rob, we achieve realistic object interactions, though we observed occasional inconsistencies in hand grasping postures. To enhance realism, we introduce a three-stage pose-refinement pipeline that improves hand posture accuracy in generated videos. Our curated dataset, coupled with the specialized pose-refinement framework, provides notable performance gains in generating high-quality, task-oriented hand-object interaction videos, resulting in achieving superior generalizable robotic manipulation. To foster further advancements in the field, TASTE-Rob dataset and source code will be made publicly available on our website https://taste-rob.github.io.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "TASTE-Rob: Advancing Video Generation of Task-Oriented Hand-Object Interaction for Generalizable Robotic Manipulation" based on the provided PDF content and metadata. I need to organize the summary according to 8 specific points, using Markdown format with hierarchical headers and bullet points. The summary should be concise but comprehensive, ending with "（完）".

Let me carefully analyze the paper content and prepare a structured summary covering all 8 required points.

Key points from the paper:
1. Problem: Existing ego-centric HOI datasets like Ego4D have inconsistent camera viewpoints and misaligned interactions
2. Method: TASTE-Rob dataset (100,856 videos) + three-stage pose-refinement pipeline
3. Experiments: Comparison with baselines, ablation studies
4. Resources: Limited info on GPU/hardware
5. Conclusion and findings
6. Pros and cons

Let me write this out systematically.</think>

# TASTE-Rob 论文总结

## 1. 核心问题与研究动机

- **研究背景**：机器人模仿学习（IL）依赖视频演示，但要求演示视频与执行环境近乎一致，难以泛化到未见场景。视频扩散模型（VDM）生成的演示可缓解此问题。
- **两条技术路线**：
  - 机器人-物体交互视频生成：受限于机器人数据规模小。
  - 人-手-物交互（HOI）视频生成：可利用大规模人类操作数据，是更可扩展的方案。
- **现有数据集的关键缺陷**（以 Ego4D 为代表）：
  - **相机视角不一致**：片段来自头戴相机长视频，视角持续变化；而 IL 演示通常需要固定视角。
  - **动作-指令错位**：长视频被切分为短片段，部分片段仅包含与任务部分对齐的交互，造成与语言指令不匹配。
- **现有生成模型的缺陷**：即便强大的通用 VDM 也难以生成准确的任务导向 HOI 视频；且微调后存在手部抓握姿态在时间维度上的不一致问题。

## 2. 方法论

### 2.1 TASTE-Rob 数据集构建

- **规模与组成**：100,856 段自我中心（ego-centric）HOI 视频，每段配语言指令；其中 75,389 段为单手任务，25,467 段为双手任务。
- **采集规范**：
  - 使用广角镜头相机，固定 1080p 视角录制，相机保持静止。
  - 单段视频时长 < 8 秒，仅包含一个完整动作；采集者按"开始-执行-结束"流程记录。
  - 视角与 Ego4D 头戴相机设置对齐，保持自我中心一致性。
- **多样性**：
  - 环境：厨房、餐厅、办公桌、卧室、洗手间、梳妆台等。
  - 动作：抓取、放置、推动、倾倒、保持、开/关，以及旋转、折叠、堆叠、扭转、擦拭、按压、切割等。
  - 手部姿态：基于 HaMeR 提取手部参数，分析掌心朝向（表 1）、指间角度（图 3）与指节曲率（图 4），验证姿态多样性。

### 2.2 三阶段姿态精炼管线（Pose-Refinement Pipeline）

**Stage I：粗粒度动作规划（Coarse Action Planner）**
- 基于 DynamiCrafter（I2V 潜空间扩散模型）微调，仅更新 image context projector 与 spatial layers。
- 输入：任务语言 $T$、环境图像 $i$；输出：粗粒度 HOI 视频 $\hat{v}_c$。
- 优化目标：
$$\min_{\theta_V} \mathbb{E}_{t,z,\epsilon\sim\mathcal{N}(0,I)} \| \epsilon - \epsilon_\theta(z_t, T, i, t, fps) \|_2^2$$
- 训练：30K 步，batch size 16，学习率 $5\times10^{-5}$。
- **问题**：抓握姿态在时间维度上不稳定（pinch 与 grasp 混用等）。

**Stage II：手部姿态序列修订**
- 用 MediaPipe 从粗视频中提取手部关键点序列 $p_c \in \mathbb{R}^{L_p \times N_h \times 2}$。
- 扩展 MDM（Motion Diffusion Model）：增加 CLIP 图像分支融合环境信息 $i$。
- 优化目标：
$$\min_{\theta_M} \mathbb{E}_{t,p,\epsilon\sim\mathcal{N}(0,I)} \| p_0 - \mathcal{M}(p_t, T, i, t) \|_2^2$$
- 关键设计：不在纯噪声上生成，而是以 $p_c$ 为起点进行 $N_{rv}=10$ 步去噪，平衡"空间准确性"与"运动可行性"。
- 训练：100K 步，batch size 64，学习率 $1\times10^{-4}$。

**Stage III：基于精炼姿态的再生**
- 训练一个 frame-independent pose encoder $\mathcal{S}$，将精炼姿态的可视化图像 $s_i$ 注入到 Stage I 模型 V 的中间特征（仿 ControlNet）。
- 公式：$F_i^{inject} = \mathcal{S}(s_i, z_i, t)$。
- 训练时冻结 V，仅更新 $\mathcal{S}$ 的参数 $\eta$：
$$\min_\eta \mathbb{E}_{t,s,\mathcal{E}(v),\epsilon\sim\mathcal{N}(0,I)} \| \epsilon - \epsilon_\theta^S(z_t; T, i, s, t, fps) \|_2^2$$
- 训练：30K 步，batch size 32，学习率 $5\times10^{-5}$。
- 推理：50 步去噪，$N_{rv}=10$。

## 3. 实验设计

### 3.1 数据集与场景
- **TASTE-Rob-Test**：从 TASTE-Rob 中按动作类别抽取 2% 作为测试集。
- **Mujoco 仿真数据集**：基于 Im2Flow2Act 平台随机选取 50 个任务用于机器人操纵评估。

### 3.2 对比方法
- 视频生成基线：**consistI2V**、**DynamiCrafter**、**Open-Sora Plan**、**CogVideoX**。
- 数据集消融基线：**Ego4D-Gen**（用 Ego4D 中 83,647 段 HOI 视频微调 DynamiCrafter）。
- 模型变体：**Coarse-TASTE-Rob**（仅 Stage I，无姿态精炼）。

### 3.3 评估指标
- **视频生成质量**：KVD、FVD、PIC（与 DynamiCrafter 一致）。
- **抓握姿态一致性**：GPV（姿态方差）、GTCE（抓握类型分类误差）、HMDA（手部运动方向准确性）。
- **机器人操纵**：在 Mujoco 仿真中用生成的视频作为演示，调用 Im2Flow2Act 策略模型，统计成功率。

### 3.4 主要结果
- 视频生成（表 3）：TASTE-Rob 的 KVD=0.03、FVD=9.43、PIC=0.90，显著优于 CogVideoX（KVD=0.16、FVD=48.72）。
- 数据集消融（表 4）：Coarse-TASTE-Rob 远优于 Ego4D-Gen（KVD 0.04 vs 0.18；FVD 10.85 vs 52.17）。
- 姿态精炼消融（表 5）：完整管线相比粗模型，GTCE 由 67.8% 降至 9.7%，HMDA 由 26.4° 降至 11.3°，成功率由 84% 提升至 96%。
- 去噪步数消融（表 6）：$N_{rv}=10$ 在姿态一致性与空间感知间取得最佳折中。

## 4. 资源与算力

- **GPU 型号与数量**：论文未明确给出。
- **训练时长**：仅给出迭代步数（30K / 100K / 30K）与 batch size（16 / 64 / 32），未报告 wall-clock 训练时间。
- **算力缺口**：这是一项明显的说明缺失，读者难以复现成本与可行性。

## 5. 实验数量与充分性

- **数据集比较**（表 2）：与 Disney、ADL、Charades-Ego、HOI4D、UT Ego、EGTEA Gaze+、EPIC-KITCHENS、Ego4D 等 8 个数据集在分辨率、规模、视角、动作对齐等维度做了系统对比。
- **消融实验**：
  - 数据集消融（TASTE-Rob vs Ego4D）。
  - 管线消融（粗模型 vs 三阶段完整管线）。
  - 超参消融（$N_{rv}$ 的取值）。
- **多样性分析**：手部朝向、指间角、曲率分布均做了统计。
- **充分性评估**：
  - 优点：覆盖了数据集级、方法级与超参级多个维度，且在 TASTE-Rob-Test 与 Mujoco 两个场景上验证。
  - 不足：物理机器人实验缺失，仅有仿真；与基线方法的对比侧重视频生成质量，抓握姿态指标与机器人指标只对比自家变体；TASTE-Rob-Test 来自同一分布，可能高估泛化能力。

## 6. 主要结论与发现

- 高质量、严格对齐的自我中心 HOI 数据集显著优于现有大规模但松散对齐的数据集（Ego4D）。
- 通用 VDM 即使参数量大也难以直接生成准确的任务导向 HOI 视频，需要专门微调。
- 视频级扩散模型擅长"任务理解"（识别目标物体与动作），但在"抓握姿态时间一致性"上存在系统性缺陷。
- 通过 MDM 引入姿态先验，可显著改善手-物交互的物理可行性与机器人下游任务成功率（+12%）。
- 姿态精炼步数 $N_{rv}$ 决定了"姿态一致性"与"空间感知"的权衡，存在最优中间值。

## 7. 优点与亮点

- **数据规范创新**：固定相机视角、单动作、单段录制、明确起止时机的采集流程，为 IL 演示量身定制，是工程上细致且有效的贡献。
- **三阶段管线分工清晰**：任务级规划与姿态级修订解耦，便于独立训练与诊断。
- **以 $p_c$ 而非纯噪声为起点的 MDM 修订**：巧妙融合了空间准确性与运动可行性，兼顾两阶段模型的优势。
- **frame-independent pose encoder + ControlNet 式注入**：轻量、可即插即用，无需重新训练主干。
- **端到端可下游**：明确将生成视频接入 Im2Flow2Act 策略，证明数据-生成-模仿闭环可行。

## 8. 不足与局限

- **场景验证局限**：机器人实验仅在 Mujoco 仿真中评估，未涉及真实机器人迁移。
- **数据偏差风险**：采集者均为右利手，文中已承认这导致掌心朝向分布略偏左；并且任务/场景均以日常家居为主，对工业场景的覆盖不足。
- **数据集规模虽大但与 Ego4D 同一数量级**：9M 帧 vs 19.2M 帧，规模优势并非压倒性。
- **指标设计细节欠奉**：GPV/GTCE/HMDA 的具体算法细节被放入附录，正文中缺少清晰量化定义。
- **方法局限**：作者承认当目标物体发生显著形变（旋转、打开等）时，生成质量下降。
- **算力与可复现性信息缺失**：未报告 GPU 型号、训练时长、推理时延等，限制了对工业落地成本的判断。
- **潜在负向社会影响**：大规模真人操作视频涉及隐私，未在正文讨论采集授权与脱敏问题。

（完）
