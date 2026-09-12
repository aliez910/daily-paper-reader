---
title: "E-VLA: Event-Augmented Vision-Language-Action Model for Dark and Blurred Scenes"
title_zh: E-VLA：面向暗光与模糊场景的事件增强视觉-语言-动作模型
authors: "Jiajun Zhai, Hao Shi, Shangwei Guo, Kailun Yang, Kaiwei Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/7675.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向退化视觉下机器人操纵稳健性的事件增强VLA模型
tldr: 机器人VLA模型在开放场景下泛化能力强，但感知模块在极端低光、运动模糊和黑帧等退化条件下非常脆弱，重建图像又会带来误差。本文提出E-VLA框架，直接利用事件流中的运动与结构线索，避免从事件重建图像造成的误差，保持语义感知与感知-动作一致性；同时搭建基于DAVIS346事件相机的开源遥操作平台，采集覆盖多种任务与光照的真实RGB-事件-动作同步数据集，验证了模型在退化视觉下完成复杂操纵任务的稳健性。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 553, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 447, \"height\": 370}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-004.webp\", \"caption\": \"\", \"page\": 9, \"index\": 4, \"width\": 593, \"height\": 518}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-005.webp\", \"caption\": \"\", \"page\": 9, \"index\": 5, \"width\": 593, \"height\": 449}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6220b06e956470d3da5fb7e5/fig-006.webp\", \"caption\": \"\", \"page\": 9, \"index\": 6, \"width\": 524, \"height\": 431}]"
motivation: 机器人VLA的视觉感知在低光、模糊等退化条件下脆弱，影响操纵鲁棒性。
method: 直接融合事件流中的运动与结构线索，避免图像重建，构建RGB-事件-动作多模态VLA。
result: 在多种退化视觉条件下完成真实机器人操纵任务并保持稳健性能。
conclusion: 事件增强为VLA在退化视觉下的复杂操纵提供了新的感知范式。
---

## Abstract
Robotic Vision-Language-Action (VLA) models generalizewell for open-ended manipulation, but their perception is fragile undersensing-stage degradations such as extreme low light, motion blur, andblack clipping. We present E-VLA, an event-augmented VLA frameworkthat improves manipulation robustness when conventional frame-basedvision becomes unreliable. Instead of reconstructing images from events,E-VLA directly leverages motion and structural cues in event streamsto preserve semantic perception and perception-action consistency un-der adverse conditions. We build an open-source teleoperation platformwith a DAVIS346 event camera and collect a real-world synchronizedRGB-event-action manipulation dataset across diverse tasks and illumi-nations. We also propose lightweight, pretrained-compatible event in-tegration strategies and study event windowing for stable deployment.Experiments show that even a simple parameter-free fusion, i.e., over-laying accumulated event maps onto RGB images, could substantiallyimprove robustness in dark and heavy-blur scenes: on Pick-Place at 20lux, success increases from 0% (image-only) to 60% with overlay fusionand to 90% with our event adapter; under severe motion blur (1000 ms-exposure proxy), Pick-Place improves from 0% to 20-25%, and Sortingfrom 5% to 32.5%. Overall, E-VLA provides systematic evidence thatevent-driven perception can be effectively integrated into VLA mod-els, pointing toward robust embodied intelligence beyond conventionalframe-based imaging. Code and dataset will be available at E-VLA.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "E-VLA: Event-augmented Vision-Language-Action Model for Dark and Blurred Scenes". Let me analyze the paper content carefully and structure the summary according to the 8 requested points.

Let me go through each section carefully:

1. **Core problem and motivation**: VLA models are fragile in low-light, motion blur, and black-clipping conditions. Event cameras offer high dynamic range and microsecond latency, but integrating them into pretrained VLAs is non-trivial because event streams are sparse and statistically different from dense RGB.

2. **Methodology**:
   - Two fusion strategies: (a) Overlay-based fusion (parameter-free, pre-encoding), (b) Hierarchical Event Adapter (lightweight, multi-layer fusion inside ViT)
   - Event windowing: recent-count (N most recent events) vs. fixed-duration
   - Representation: polarity-agnostic accumulation, then demosaicing for 3-channel input
   - Built on SmolVLA backbone with SigLIP vision encoder
   - Hierarchical event adapter: weight-sharing patch embedding, 4 transformer blocks, fused into SigLIP layers 3, 6, 9, 12
   - Formulas: Eq. 1 (event tuple), Eq. 2 (recent-count window), Eq. 3 (event accumulation + demosaicing), Eq. 5 (overlay), Eq. 6 (hierarchical fusion)

3. **Experiments**:
   - Dataset: self-collected RGB-Event-Action dataset (724 episodes, 339310 frames), 3 tasks (Pick-Place, Sorting, Stacking), 4 illumination levels (200, 100, 75, 40 lux)
   - Benchmarks: comparisons against image-only, RetinexNet, Retinexformer, EvLight, E2VID
   - Tasks evaluated across multiple lux levels and exposure times (motion blur proxy)
   - OOD generalization test
   - Ablations: event windowing, training recipe, weight-sharing

4. **Resources**: Single NVIDIA A800 GPU for training, NVIDIA AGX Orin for on-robot inference. Training: 20k iterations. Specific training time not mentioned.

5. **Number of experiments**: Multiple tables (Tab. 1 low-light Pick-Place, Tab. 2 OOD, Tab. 3 motion blur, Tab. 4 windowing, Tab. 5 training recipe), plus qualitative comparisons. 6+ configurations, plus ablations.

6. **Conclusions**: Event augmentation dramatically improves VLA robustness under degraded vision; both simple overlay and hierarchical adapter help; recent-count windowing is more stable; improves OOD generalization.

7. **Strengths**: 
   - First to integrate events into VLA framework
   - Open-source platform and dataset
   - Lightweight adapter (only ~13M params, <3% of model)
   - Comprehensive ablations on design choices
   - Real-world experiments on physical robot

8. **Limitations**:
   - Color discrimination in Sorting is challenging (events encode intensity changes, not absolute color)
   - Stacking task fails due to viewpoint occlusion from wrist camera
   - Performance drops at very low illumination (~2 lux) where event noise dominates
   - Small dataset (724 episodes) compared to large-scale VLA training data
   - Monocular wrist-view limits generalizability

Let me write this in Chinese, structured with Markdown.</think>

# E-VLA：面向暗光与模糊场景的事件增强视觉-语言-动作模型 —— 论文总结

## 1. 核心问题与研究背景

- **研究对象**：面向机器人操纵的视觉-语言-动作（Vision-Language-Action, VLA）模型，如 RT-1/RT-2、π 系列、OpenVLA、RDT-1B、Gemini Robotics、SmolVLA 等。
- **核心问题**：现有 VLA 模型几乎完全依赖基于帧的 RGB 相机作为感知接口，在**低光照、运动模糊和黑帧裁剪（black clipping）**等感知阶段退化条件下表现脆弱，导致动作成功率急剧下降甚至归零。
- **根本原因**：图像增强和数据增强只能作用于已经退化的成像信号，无法恢复采集时丢失的信息；单纯增大曝光时间又会引入运动模糊与时延。
- **解决思路**：引入事件相机（event camera），其异步、高时间分辨率、宽动态范围的特性天然适合弱光与高速运动场景；但事件流稀疏、统计分布与 RGB 图像差异大，难以直接嫁接到以图像预训练为基础的 VLA 架构。
- **本文定位**：首次系统性地研究如何将事件视觉感知集成到大规模预训练 VLA 框架中，在保持原有预训练视觉-语言先验的同时，提升在低光和模糊场景下的操纵稳健性。

---

## 2. 方法论

### 2.1 整体框架（E-VLA）
- 以 **SmolVLA**（基于 SmolVLM + SigLIP 视觉编码器，约 0.5B 参数）作为基线，融合事件流后再经 VLM 与 Action Expert 生成动作块（action chunk）。
- 关键设计：不重建图像，而是将事件流转化为类图像表征并直接与 RGB 融合，保持与 SigLIP 输入分布一致。

### 2.2 事件表征与窗口化
- **事件定义**：每个事件 $e_i = (x_i, y_i, t_i, p_i)$，$p_i \in \{+1, -1\}$ 为亮度变化极性。
- **窗口化策略**：采用 **recent-count（最近 N 个事件）** 方案，而非固定时长窗口：
  $$E_{t_e} = \{e_i \mid t_i \le t_e\},\quad W_I = \{e_k\}_{k=|E_{t_e}|-N+1}^{|E_{t_e}|}$$
  原因：固定时长窗口在机械臂速度剧烈变化时不稳定，低速会丢事件，高速会模糊。
- **事件表征**：极性无关地累加每个像素的事件数得到 $\tilde{E} \in \mathbb{R}^{H\times W}$，再做 min-max 归一化和去马赛克（Demosaicing）得到三通道 $E \in \mathbb{R}^{H\times W \times 3}$，使其与 SigLIP 输入分布匹配。

### 2.3 两种事件融合策略
1. **Overlay 融合（无参数，编码前融合）**
   - 在 ViT 编码前，将最近窗口内的累积事件图按极性着色直接叠加到 RGB 图像上：
   $$I_o(x,y) = \begin{cases} I(x,y), & |E(x,y)|=0 \\ c(p_j), & j = \arg\max_i t_i, e_i \in E(x,y) \end{cases}$$
   - 即插即用，不引入额外参数。
2. **层次化 Event Adapter（编码中间融合）**
   - 采用共享权重的 $16\times 16$ patch embedding 与 4 个 Transformer 块构成轻量级 event adapter，与 SigLIP 在第 3/6/9/12 层进行分层融合。
   - 融合公式：
   $$E^{(l+1)} = G_{l+1}(E^{(l)}),\quad F^{(l+1)} = F_{l+1}\big(\mathrm{Fuse}(F^{(l)}, E^{(l)})\big)$$
   - $\mathrm{Fuse}(\cdot)$ 通过 MLP 实现，仅增加约 **13M 参数（小于模型总量的 3%）**。

### 2.4 训练策略
- 冻结 VLM 主干，仅微调 Action Expert、投影 MLP，以及 Event Adapter。
- 两阶段训练：先训练新引入的 adapter，再联合微调 adapter + action expert + 投影层。
- 对图像分支施加随机 dropout，避免模型走捷径，强制利用事件线索。

---

## 3. 实验设计

### 3.1 数据集与平台
- **自建 RGB-Event-Action 数据集**：基于 SO100 6-DoF 机械臂 + DAVIS346 事件相机（346×260 分辨率，微秒级时间戳对齐），腕部单目视角，配 100°+ 广角镜头。
- **任务**：Pick-Place、Sorting（按颜色分拣）、Stacking（堆叠）。
- **光照**：200 / 100 / 75 / 40 lux 四档；共 724 集（episodes），339310 帧，其中正常光照 305 集、弱光 419 集。
- **数据格式**：LeRobot 格式，RGB 帧、事件流、机械臂状态与动作按相机时间戳对齐。

### 3.2 对比方法
- **Image-only（10 ms 曝光）**基线
- **图像增强类**：RetinexNet、Retinexformer、EvLight
- **事件重建类**：E2VID（事件→图像重建）
- **本文方法**：Overlay、Event Adapter

### 3.3 评估协议
- 在 SO100 + DAVIS346 真实机器人 + NVIDIA AGX Orin 上进行在线评测。
- Pick-Place 10 个测试位姿；Sorting/Stacking 各 10 对配位置（物体随机交换）。
- 部分得分制（pick / place）；Pick-Place / Stacking 限时 1 分钟，Sorting 限时 1.5 分钟。
- 同步推理，动作块大小 40 @ 30 Hz（每次前向预测约 1.33 s 动作）。

### 3.4 实验内容
- **低光照性能**（Tab. 1，Pick-Place）：20–75 lux 逐档评测。
- **OOD 泛化**（Tab. 2）：仅在 200 lux 数据上训练，测试更低 lux 的泛化能力。
- **运动模糊性能**（Tab. 3）：100–1000 ms 曝光时间下 Pick-Place 与 Sorting 任务。
- **消融研究**（Tab. 4-5）：
  - 事件窗口大小与类型（5/20/40 ms vs. 500/2000/4000 events）
  - 训练配方（Action-only / Event-only / Action →Event →Joint / 权重共享）
- **失败案例分析**：Sorting 的颜色判别失败、Stacking 的视角遮挡。

---

## 4. 资源与算力

- **训练**：单张 **NVIDIA A800 GPU**，训练 20k 迭代。
- **在线推理与数据采集**：**NVIDIA AGX Orin**（边缘部署平台，符合真实部署约束）。
- **未明确给出**：训练总时长、显存占用、参数总量（除 Event Adapter 的 13M 增量外）；事件相机相关参数与镜头规格（DAVIS346、2.2 mm / F1.8 广角镜头）。
- 论文未提供分布式训练或大规模算力使用信息，整体算力开销属于轻量级。

---

## 5. 实验数量与充分性

- **实验组数**：约 5–6 个主表（Tab. 1–5），覆盖低光照（6 档 lux）、运动模糊（6 档曝光）、OOD 泛化、窗口化消融（7 种配置）、训练配方消融（4 种配置）、失败模式分析。
- **公平性**：
  - 所有方法在相同的多任务多光照数据集上微调 20k 迭代；
  - VLM 主干统一冻结；
  - 测试配置（位置、物体、初始姿态）固定，保证可比性；
  - 部分得分制减少主观偏差。
- **充分性**：
  - 优点：覆盖了多种光照、曝光、任务、消融维度，并做了 OOD 测试；
  - 局限：仅在单台 SO100 机械臂 + 单相机（腕部单目）下完成，缺少跨平台泛化验证；Sorting/Stacking 评测样本量较小（10 组配对）；数据集总规模（724 episodes）与主流 VLA 训练数据相比仍偏小。

---

## 6. 主要结论与发现

- **事件增强显著提升 VLA 在退化视觉下的稳健性**：
  - Pick-Place @ 20 lux：图像-only 0% → Overlay 60% → Event Adapter 90%；
  - Pick-Place @ 30 lux：图像-only 35% → Adapter 90%；
  - Pick-Place @ 25/20 lux 黑帧裁剪：图像-only 0%，事件方案仍可保持 60–90%。
- **运动模糊场景**：1000 ms 严重模糊下，Pick-Place 从 0% 提升至 20–25%，Sorting 从 5% 提升至 32.5%。
- **OOD 泛化**：仅在 200 lux 数据训练，Event Adapter 在 75/40/30/20 lux OOD 下分别保持 85/75/70/45%，显著优于图像-only（65/30/0/0%）。
- **事件窗口化**：recent-count 窗口比固定时长窗口更稳定，2000 events 表现最佳。
- **训练配方**：两阶段训练（先 adapter 再联合微调）+ patch embedding 权重共享显著提升性能（50% → 90%）。
- **事件优势的本质**：来自事件相机的高时间分辨率和宽动态范围，而非任务特定的模糊适配训练（所有模型均未在模糊数据上训练）。
- **失败模式**：颜色判别（事件仅编码强度变化，无法恢复静态颜色）和腕部视角遮挡仍是开放问题。

---

## 7. 优点与亮点

- **首创性**：首次系统性地将事件视觉集成到大规模预训练 VLA 框架中，填补了事件感知与 VLA 学习之间的空白。
- **即插即用的双策略**：从无参数 Overlay 到轻量 Event Adapter，覆盖不同算力预算与精度需求。
- **极小参数量开销**：Event Adapter 仅 13M 参数（<3%），不破坏预训练分布，可与现有 VLA 解耦部署。
- **完整开源生态**：开源遥操作平台 + 真实同步 RGB-Event-Action 数据集，便于复现与后续研究。
- **系统性消融**：覆盖事件表征、窗口大小、训练策略、模块融合位置等多个设计维度，为后续工作提供工程指引。
- **真实部署视角**：从数据采集到推理均使用 AGX Orin 边缘平台，验证了实用性而非纯实验室结果。
- **OOD 泛化提升**：证明事件感知可以减少对低光标注数据的依赖，具有数据效率优势。

---

## 8. 不足与局限

- **数据集规模有限**：仅 724 episodes，远小于主流 VLA 训练集（如 Open X-Embodiment），可能限制策略的泛化能力。
- **单平台单视角**：仅在 SO100 + 腕部单目 DAVIS346 上验证，缺少跨机械臂、跨相机、跨实验室的迁移实验。
- **颜色感知受限**：Sorting 任务中事件无法编码绝对颜色，导致颜色判别性能下降，限制了需精细颜色识别的应用场景。
- **视角遮挡瓶颈**：Stacking 任务失败主要由腕部相机被夹持物体遮挡造成，事件信号无法缓解该几何级限制。
- **极低照度极限**：在约 2 lux 以下，事件噪声开始主导，性能下降，文中以补充材料 Tab. S1 提及但未深入分析。
- **闭源基线对比的不对称性**：与 SmolVLA 等开源基线可直接对比，但 RT-2、π0、Gemini Robotics 等更大规模闭源 VLA 未能纳入对比，可能高估相对增益。
- **理论分析不足**：缺乏对事件贡献机理的理论分析（如信息瓶颈、可识别性等），主要依赖经验性消融。
- **应用范围受限**：目前聚焦桌面级 Pick-Place 类任务，对移动操作、双臂协作、长时序任务等场景未验证。

（完）
