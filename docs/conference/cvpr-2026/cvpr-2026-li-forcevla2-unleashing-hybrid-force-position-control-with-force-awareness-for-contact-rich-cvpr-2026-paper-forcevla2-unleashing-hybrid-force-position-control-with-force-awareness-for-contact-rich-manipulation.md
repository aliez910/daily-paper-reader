---
title: "ForceVLA2: Unleashing Hybrid Force-Position Control with Force Awareness for Contact-Rich Manipulation"
title_zh: ForceVLA2：面向接触丰富操纵的力感知混合力位控制
authors: "Li, Yang, Zhaxizhuoma, Zhaxizhuoma, Jiang, Hongru, Xia, Junjie, Zhang, Hongquan, Du, Jinda, Zhou, Yunsong, Zeng, Jia, Hao, Ce, Ren, Jieji, Yu, Qiaojun, Lu, Cewu, Qiao, Yu, Pang, Jiangmiao"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Li_ForceVLA2_Unleashing_Hybrid_Force-Position_Control_with_Force_Awareness_for_Contact-Rich_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向接触丰富操纵的端到端力感知VLA与闭环力位混合控制
tldr: 本文针对接触丰富机器人操纵中显式力感知与调节不足导致稳定性差的问题，提出ForceVLA2端到端VLA框架。方法将基于力的提示注入VLM专家以构建阶段化力感知任务概念，并采用跨尺度混合专家动作专家自适应融合实时交互力，实现闭环力位混合控制。该工作推动了端到端视觉运动学习在复杂接触操纵中的实际应用。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1698, \"height\": 599, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1535, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1792, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 754, \"height\": 527, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1788, \"height\": 1092, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1789, \"height\": 628, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 920, \"height\": 348, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 853, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-li-forcevla2-unleashing-hybrid-force-position-control-with-force-awareness-for-contact-rich-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 851, \"height\": 258, \"label\": \"Table\"}]"
motivation: 现有VLA模型缺乏显式力感知与调节，在接触丰富任务中稳定性与精度受限。
method: 在VLM专家中引入力提示，并设计跨尺度MoE动作专家实现闭环力位融合控制。
result: ForceVLA2在多种接触丰富操纵任务中显著提升稳定性、精度与鲁棒性。
conclusion: 为端到端视觉运动模仿学习在力控操纵任务中的落地提供了有力方案。
---

## Abstract
Embodied intelligence for contact-rich manipulation has predominantly relied on position control, while explicit awareness and regulation of interaction forces remain under-explored, limiting stability, precision, and robustness in real-world tasks. We propose ForceVLA2, an end-to-end vision-language-action framework that equips robots with hybrid force-position control and explicit force awareness. ForceVLA2 introduces force-based prompts into the VLM expert to construct force-aware task concepts across stages, and employs a Cross-Scale Mixture-of-Experts (MoE) in the action expert to adaptively fuse these concepts with real-time interaction forces for closed-loop hybrid force-position regulation. To support learning and evaluation, we construct ForceVLA2-Dataset, containing 1,000 trajectories over 5 contact-rich tasks, including wiping, pressing, and assembling, with multi-view images, task prompts, proprioceptive state, and force signals. Extensive experiments show that ForceVLA2 substantially improves success rates and reliability in contact-rich manipulation, outperforming pi0 and pi0.5 by 48.0% and 35.0%, respectively, across the 5 tasks, and mitigating common failure modes such as arm overload and unstable contact, thereby actively advancing force-aware interactive physical intelligence in VLAs.

---

## 论文详细总结（自动生成）

<think>The user wants a structured, in-depth summary of the ForceVLA2 paper in Chinese, using Markdown format. Let me analyze the paper carefully and produce a detailed, comprehensive summary covering all 8 requested aspects.

Let me go through each section:

1. **Core problem and motivation**: Current VLA models lack explicit force awareness and regulation, limiting performance in contact-rich manipulation tasks.

2. **Methodology**: ForceVLA2 framework with:
   - Force prompts in VLM expert
   - Cross-Scale Mixture-of-Experts (MoE) in action expert
   - Hybrid force-position control
   - Multimodal encoder
   - Flow matching policy head

3. **Experimental design**: 
   - ForceVLA2-Dataset with 1000 trajectories across 5 tasks
   - 20 trials per task
   - Baselines: ACP, π0, π0.5, ForceVLA, π0 w/ F

4. **Resources**: The paper doesn't mention specific GPU models or training time.

5. **Experiment quantity**: Main results table + 2 ablation tables + qualitative tests.

6. **Main conclusions**: 66% average success rate, outperforms baselines significantly.

7. **Advantages**: First end-to-end force-aware VLA with hybrid control, force prompts, Cross-Scale MoE, etc.

8. **Limitations**: Limited task variety, no mention of computational resources, etc.

Let me write a comprehensive Chinese summary now.</think>

# ForceVLA2 论文结构化总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

### 核心问题
- 现有视觉-语言-动作模型（VLA）在**接触丰富操作**（contact-rich manipulation）任务中，主要依赖**位置控制**，对**交互力的显式感知与调节**能力严重不足。
- 这导致在擦拭、按压、装配等需要稳定接触的现实中任务里，机器人容易出现**机械臂过载、接触不稳定、任务失败**等问题。
- 现有力相关工作（如 ForceVLA、ACP、TLA 等）往往只将力/触觉视为**辅助感知输入**，而非用于**主动闭环的力-位混合调节**。

### 研究背景与动机
- 借鉴人体感觉运动控制机制：人类通过高层视觉/语言推理定位子任务目标，同时通过实时力反馈进行精细的力-位调节。
- 现有 VLA 缺乏对**子任务阶段性时空关系**的推理能力，也缺少将力感知与主动力-位交互融合的机制。
- 推动 VLA 从"力感知"走向"力交互"，实现真正的物理智能。

---

## 2. 论文提出的方法论

### 整体框架
ForceVLA2 是一个**端到端 VLA 框架**，将力感知与混合力-位控制统一建模，分两层设计：
- **长期力感知推理**（VLM 专家内）：通过**力提示**（force prompt）构建阶段化力感知任务概念。
- **短期反应式操作技能**（动作专家内）：通过**跨尺度混合专家（Cross-Scale MoE）**融合多模态信息，输出混合力-位动作。

### 关键技术细节

#### 2.1 长期力感知（VLM 专家中通过 Prompting 实现）
- **力提示（Force Prompt）**：以文本形式指示当前子任务状态（如"按下瓶子，进度 0.9"），类似离散状态机，决定是否进入下一阶段。
- 编码流程：
  - 多视角图像 → SigLIP 视觉编码器 → 视觉 token $Z_v$
  - 任务文本 $T_t$ 与力提示 $T_f$ 拼接 → 文本编码器 → 语言 token $Z_l$
  - 拼接得到 $E_{in} = [Z_v; Z_l]$，输入 VLM（PaliGemma）得到融合多模态表征 $E$。

#### 2.2 短期力-控制回路（动作专家）
- **本体-力编码**：
  - 末端 6D 位姿 $p \in \mathbb{R}^7$ 经线性层 $\phi_P$ 编码为 $E_P$。
  - 6D 力/力矩 $f_{raw} \in \mathbb{R}^6$ 经 $\phi_F$ 编码为 $E_F$。
  - 多模态状态表示 $E_{state} = [E_P; E_F]$。
- **跨模态交互**：以视觉-语言 token $E$ 为 KV，以状态 token 为 Query 进行 Cross-Attention，得到 $E'_{state}$。
- **力信号旁路**：原始 $E_F$ 绕过跨模态融合，直接送入 MoE，保留快速力反馈梯度。
- **输入拼接**：$E_{cond} = [E; E'_{state}; E_F]$。

#### 2.3 跨尺度混合专家（Cross-Scale MoE）
- 三个专家：视觉（V）、状态（S）、力（F），均为轻量 MLP。
- 动态门控网络计算 token 级别路由权重 $w = [w_V, w_S, w_F]$：
  $$E_{MoE} = \sum_{m \in \{V,S,F\}} w_m \cdot \text{Expert}_m(E_{cond})$$
- 模型在不同阶段自动强调不同模态：自由运动时侧重视觉，接触/顺应时侧重力。

#### 2.4 流匹配策略（Flow Matching Policy）
- 基于条件流匹配的动作生成头，从噪声逐步去噪得到动作：
  $$a_t^{(1)} = [\Delta p_t; f_t], \quad s_t \in [0, 1]$$
- 其中 $\Delta p_t \in \mathbb{R}^7$ 为末端位姿增量，$f_t \in \mathbb{R}^6$ 为预测接触力，$s_t$ 为子任务完成概率。

#### 2.5 子任务转移概率建模
- 基于方向对齐度 $\Theta$（Beta 分布 $\alpha=2$）、剩余距离 $L$（指数分布 $\lambda=2$）、力 $F$（均匀分布）联合建模：
  $$\hat{s}_t = P(\Theta \leq \theta, L \geq l, F \leq f) = \Gamma(\alpha+1) \cdot \theta^\alpha \cdot e^{-\lambda l} \cdot \frac{f-n}{m-n}$$
- 当 $\hat{s}_t$ 超过阈值时切换子任务并重置为 0。

---

## 3. 实验设计

### 数据集
- **ForceVLA2-Dataset**：1,000 条轨迹，约 500K 同步时间步。
- **5 个接触丰富任务**：
  - Press bottle（按压瓶子）
  - Clean vase（清洁花瓶）
  - Clean board（擦黑板）
  - Retrieve plate（搜寻取盘）
  - Assemble gears（齿轮装配）
- **硬件**：Flexiv Rizon 4s 7-DOF 机械臂 + DH AG-95 自适应夹爪。
- **传感器**：3 个 RGB 相机（2 个 D455 第三人称 + 1 个 D435 腕部）+ 末端 6D 力/力矩传感器（300 Hz）。
- **采集方式**：基于力反馈的 GELLO 遥操作框架。
- **标注**：每个任务分为 3-5 个子任务，根据力信号过渡离线标注。

### 评估指标
- **成功率（%）**，每个任务 20 次独立试验。

### 对比方法（Baselines）
- **π0**：流匹配 VLA 基线
- **π0.5**：多任务协同训练版本
- **ACP**（Adaptive Compliance Policy）：基于导纳控制的扩散策略
- **ForceVLA**：引入力模态的 VLA
- **π0 w/ F**：π0 简单拼接力输入

---

## 4. 资源与算力

- **论文中未明确说明**训练所用的 GPU 型号、数量、训练时长等算力细节。
- 仅提及模型基于 PaliGemma（3B VLM）和 SigLIP 视觉编码器，基于 π0 框架扩展。
- 数据采集硬件明确：Flexiv Rizon 4s + DH AG-95 + Intel RealSense D455/D435 + 6D 力/力矩传感器。
- **缺失信息**：训练算力、推理延迟、模型参数量、训练 epoch 数等关键资源指标未披露。

---

## 5. 实验数量与充分性

### 主要实验
1. **主实验（Table 1）**：5 个任务 × 6 个方法 × 20 次试验 = 600 次真实机器人试验。
2. **组件消融（Table 2）**：在 π0 基础上逐步加入 FP、ME、CM 三个模块，共 4 组配置。
3. **模态融合消融（Table 3）**：Cross-Scale MoE 中视觉模态（VM）与力模态（FM）的组合，共 3 组。
4. **定性测试（Fig. 5-6）**：包含高速跟随、方向跟随、目标重定位、抓取失败重试等动态扰动场景。

### 充分性评估
- **优点**：实验涵盖多个典型接触任务，包含真实扰动测试；消融逻辑清晰，能验证各模块贡献。
- **不足**：
  - 任务种类有限（仅 5 个），缺乏对更长视野、更复杂装配链路的验证。
  - 试验次数（每任务 20 次）统计置信度有限。
  - 缺乏跨机器人/跨硬件迁移测试。
  - 未与更多近期 SOTA 方法（如 GR00T-N1、HybridVLA 等）做对比。
  - 未在仿真环境做大规模统计实验。

---

## 6. 论文的主要结论与发现

### 定量结论
- ForceVLA2 在 5 个任务上平均成功率 **66%**，显著优于所有基线。
- 相对 **π0 提升 48.0%**，相对 **π0.5 提升 35.0%**。
- 在最具挑战的 **Assemble gears** 任务上，相对次优方法提升高达 **50 个百分点**（10% → 70%）。
- 力相关基线（ACP、π0 w/ F）相比无力基线提升有限，说明**简单拼接力输入反而可能干扰预训练 VLA 表征**。

### 定性发现
- 力敏感任务（如 Clean board、Press bottle）中，ForceVLA2 能主动调节接触力，**避免机械臂过载**。
- 在瓶底突然下降的扰动下，能快速响应新接触配置，保持稳定按压。
- 花瓶旋转后表面法向变化时，能沿表面滑动完成擦拭。
- 在 Retrieve plate 任务中，初次抓取失败后可自主重新尝试，表现出强鲁棒性。

### 消融结论
- 三模块（FP、ME、CM）逐步叠加带来单调性能提升。
- **Cross-Scale MoE 贡献最大**。
- VM 与 FM 在 MoE 中贡献大致相当，二者缺一不可。
- 简单任务（如 Press bottle、Clean board）中额外力 token 可能引入多余自由度，反而略微降低成功率。

---

## 7. 优点与亮点

### 方法层面
- **首个将显式混合力-位控制融入 VLA 端到端框架**的工作，从"力感知"走向"力交互"。
- **力提示（Force Prompt）** 设计简洁优雅：将子任务状态以文本形式注入 VLM，无需复杂架构改动即可获得阶段化任务概念。
- **Cross-Scale MoE + 力信号旁路**：短期反应式力反馈绕过跨模态交互，保留梯度保真度，实现快速闭环。
- **概率化子任务转移建模**：基于方向对齐、距离、力的联合概率分布定义子任务进度，数学上严谨。
- **数据采集设计**：基于力反馈的 GELLO 遥操作，自然捕获力-运动耦合的演示数据。

### 实验层面
- 多任务、多模态对比充分，覆盖感知、推理、控制全链路。
- 真实扰动测试（高速、方向、重定位）展示出实际部署价值。
- 消融逻辑清晰，验证各模块必要性与贡献。

### 数据集层面
- ForceVLA2-Dataset 是**首个同时提供力提示与力控制监督**的数据集，填补了从力感知到力交互研究的空白。

---

## 8. 不足与局限

### 方法层面
- **力控制输出解释性有限**：模型直接预测 $f_t \in \mathbb{R}^6$ 力向量，但未明确如何在真实硬件上执行力跟踪（仅靠末端位置增量隐式调节）。
- **子任务进度阈值需人工设定**，且子任务边界依赖离线力信号标注，泛化到新任务时标注成本高。
- **任务规划仍是预定义**：Force Prompt 由预设子任务列表驱动，未实现完全自主的子任务发现与扩展。
- **Beta/Exponential/Uniform 分布假设可能与真实场景不完全匹配**，子任务进度建模依赖较强先验。

### 实验层面
- **任务覆盖偏窄**：仅 5 个接触任务，缺少对精细插孔、柔性物体操作、多手指接触等更广泛场景的验证。
- **试验统计量较小**：每任务仅 20 次，置信区间较宽。
- **对比方法有限**：未与 GR00T-N1、HybridVLA、TLA、3D Diffuser Actor 等近期方法直接比较。
- **未提供仿真 benchmark**：难以做大规模重复实验与统计分析。
- **缺乏失败案例深度分析**：定性结果偏向成功展示，未系统归纳失败模式与边界条件。

### 资源与可复现性
- **算力、训练时长、超参数完全未披露**，可复现性受限。
- 模型规模、数据集细节仅部分给出（如 1000 条轨迹总数），具体每个任务的轨迹数、训练/验证划分未明确。
- 力/力矩传感器的标定流程、噪声水平、采样率同步细节描述较为简略。

### 应用层面
- 依赖**高精度末端力/力矩传感器**，对于低成本或无传感器的平台难以直接迁移。
- 假设操作环境已知且任务结构化，对开放世界、长视野任务的适用性未验证。
- 仅在单一机器人平台（Flexiv Rizon 4s）上验证，跨平台迁移能力未知。

---

（完）
