---
title: "EchoVLA: Robotic Vision-Language-Action Model with Synergistic Declarative Memory for Mobile Manipulation"
title_zh: "EchoVLA:融合协同声明式记忆的机器人视觉-语言-动作移动操作模型"
authors: "Min Lin, Xiwen Liang, Bingqian Lin, Jingzhi Liu, Zijian Jiao, Kehan Li, Ziang Yan, Yu Sun, Weijia Liufu, Yuhan Ma, Jiarui Hu, Yuecheng Liu, Shen Zhao, Yuzheng Zhuang, Xiaodan Liang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/13820.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向移动操作的记忆增强型VLA模型
tldr: "现有视觉-语言-动作模型多局限于短视野桌面操作,缺乏移动操作所需的记忆与推理能力,无法协调导航与操作。本文提出EchoVLA,一种受人类大脑启发的记忆增强型VLA模型。该模型融合场景记忆(空间-语义地图)与情节记忆(任务级多模态经验)两类协同声明式记忆。该工作将通用视觉-动作模型拓展到更长视野的移动操作场景,推动通用机器人在复杂环境中的应用。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-001.webp\", \"caption\": \"\", \"page\": 5, \"index\": 1, \"width\": 348, \"height\": 712}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-002.webp\", \"caption\": \"\", \"page\": 5, \"index\": 2, \"width\": 591, \"height\": 210}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 686, \"height\": 493}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-004.webp\", \"caption\": \"\", \"page\": 10, \"index\": 4, \"width\": 2532, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-005.webp\", \"caption\": \"\", \"page\": 10, \"index\": 5, \"width\": 2532, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-006.webp\", \"caption\": \"\", \"page\": 10, \"index\": 6, \"width\": 2532, \"height\": 347}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-c7ad4a247921cdb6fcf85709/fig-007.webp\", \"caption\": \"\", \"page\": 10, \"index\": 7, \"width\": 2532, \"height\": 346}]"
motivation: "现有VLA模型局限于短视野桌面操作,缺乏支持移动操作中导航与操作协调所需的记忆推理能力。"
method: "提出EchoVLA记忆增强型VLA模型,融合场景记忆与情节记忆的协同声明式记忆机制。"
result: "在移动操作任务中展现出更强的长视野任务执行与空间推理能力,优于基线VLA模型。"
conclusion: "将通用VLA模型拓展至移动操作场景,为复杂环境下的通用机器人策略提供新方向。"
---

## Abstract
Recent progress in Vision–Language–Action (VLA) modelshas enabled embodied agents to interpret multimodal instructions andperform complex tasks. However, existing VLAs are mostly confined toshort-horizon, table-top manipulation, lacking the memory and reasoningcapability required for mobile manipulation, where agents must coordi-nate navigation and manipulation under changing spatial contexts. Inthis work, we present EchoVLA, a memory-aware VLA model for mobilemanipulation. EchoVLA incorporates a synergistic declarative memoryinspired by the human brain, consisting of a scene memory that main-tains a collection of spatial–semantic maps and an episodic memory thatstores task-level experiences with multimodal contextual features. Thetwo memories are individually stored, updated, and retrieved based oncurrent observations, task history, and instructions, and their retrievedrepresentations are fused via coarse- and fine-grained attention to guidebase–arm diffusion policies. To support large-scale training, we furtherintroduce MoMani, an automated benchmark that generates expert-leveltrajectories through multimodal large language model (MLLM)–guidedplanning and feedback-driven refinement, supplemented with real-robotdemonstrations. Comprehensive simulated and real-world results demon-strate that EchoVLA substantially improves overall performance, e.g., itachieves the highest success rates of 0.52 on manipulation/navigationtasks and 0.31 on mobile manipulation tasks in simulation, exceedingthe strong baseline π0.5 by +0.20 and +0.11, respectively.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "EchoVLA: Robotic Vision-Language-Action Model with Synergistic Declarative Memory for Mobile Manipulation" structured into 8 specific sections. Let me carefully analyze the paper content and organize it according to the requested format.

Let me go through the paper carefully:

1. **Core problem and motivation**: Existing VLA models are limited to short-horizon tabletop manipulation, lacking memory and reasoning for mobile manipulation where navigation and manipulation need to be coordinated under changing spatial contexts.

2. **Methodology**: 
   - EchoVLA: memory-aware VLA model with two complementary declarative memories inspired by human brain
   - Scene memory: persistent voxel map (parallels parahippocampal cortex - PHC)
   - Episodic memory: time-indexed token buffer (mirrors hippocampus)
   - Coarse- and fine-grained cross-attention for retrieval
   - Per-part diffusion policy for arm/base
   - MoMani benchmark: automated MLLM-guided planning with feedback-driven refinement

3. **Experimental design**:
   - Datasets: MoMani simulation (7,889 episodes) and real-world (1,200 episodes)
   - Simulator: RoboCasa
   - Real robot: TidyBot++ platform in 7m × 7m arena
   - Baselines: BC-T, Diffusion Policy, DP3, π0.5, WB-VIMA
   - Tasks: PnPC2S, PnPS2C, TOF, TOS, Nav only, OD, CM, PCIS, OR, RK, EnP

4. **Resources**: 8 NVIDIA A100 GPUs mentioned. No specific training time.

5. **Experimental quantity**: Multiple ablations - observation, memory module, hyperparameter sensitivity. Real-world experiments with 20 trials per task.

6. **Main conclusions**: EchoVLA achieves 0.52 SR on manipulation/navigation and 0.31 on mobile manipulation (simulation), 0.44 SR real-world, outperforming π0.5 by +0.20 and +0.11 respectively.

7. **Strengths**: 
   - Neuro-inspired dual memory design
   - Synergistic declarative memory with coarse-to-fine attention
   - Comprehensive benchmark MoMani
   - Strong performance on long-horizon tasks
   - Automated data generation pipeline

8. **Limitations**:
   - Depends on high-quality depth and pose streams
   - Cumulative odometry drift can cause spatial misalignments
   - Sensitive to dynamic occlusion (e.g., fridge door opening)
   - Cold-start problem in novel environments
   - 3D scene memory sensitivity to extreme structural dynamics

Let me write this up in proper Markdown format.</think>

# EchoVLA 论文总结

## 1. 核心问题与整体含义（研究动机与背景）

- **现有 VLA 模型的局限**：尽管 RT-2、OpenVLA、ManipLLM、π0/π0.5 等 VLA 模型在桌面操作上表现优异，但大多局限于**短视野、桌面级**操作，采用 **Markovian 决策**（仅依赖当前观测），缺乏长时序、跨空间的记忆与推理能力。
- **移动操作（Mobile Manipulation）的核心挑战**：机器人需在动态空间环境中**协调导航与操作**，同一观测画面可能对应完全不同的任务阶段（如"柜门已开"vs."即将开柜门"），属于**非 Markov 任务**。
- **本文动机**：受人类大脑**声明式记忆系统**（parahippocampal cortex 处理空间-场景结构 + hippocampus 处理时序经验）启发，提出一种**双记忆协同**的 VLA 模型，使机器人同时具备"在哪儿"（空间记忆）与"如何完成任务"（情节记忆）的推理能力。

## 2. 方法论

### 2.1 整体框架（EchoVLA）
- 三大组件：**多模态状态表征 → 记忆检索与交互 → 扩散动作生成**。
- 输入：多视角 RGB-D、点云、语言指令、本体感知状态。
- 输出：基座动作 $a_t^{\text{base}}$ 与机械臂动作 $a_t^{\text{arm}}$，由 per-part 扩散策略分别生成。

### 2.2 多模态状态表征 $S_t = [L, V_t, P_t, R_t]$
- **语言 token $L$**：冻结 SigLIP 文本塔编码指令。
- **视觉 token $V_t$**：冻结 SigLIP 视觉塔编码三路 RGB，拼接投影。
- **点云 token $P_t$**：可训练 PointAttn 编码几何信息。
- **本体感知 token $R_t$**：MLP 编码关节/末端状态。

### 2.3 协同声明式记忆
- **场景记忆 $M_{\text{scene}}$（对应 PHC）**：维护 Key-Value 形式的体素特征图，Key 为 3D 空间索引 $(x,y,z)$，Value 为聚合的 PointAttn 特征。
  - 更新规则：基于重建误差 $\delta = \|V_t^{3D} - D(M_{\text{scene}}[x,y,z])\|_2$ 的 EMA 更新（$\alpha=0.2$，阈值 $\tau=0.5$）。
  - 检索：在当前相机视锥内 top-k 选择。
- **情节记忆 $M_{\text{epi}}$（对应海马体）**：FIFO 缓冲存储最近 $k$ 步的多模态 token 序列 $\{(S_{t-k}, t-k), \ldots, (S_{t-1}, t-1)\}$，保留原始编码 token 以捕获细粒度时序信息（如"柜门已开"）。
- **分层检索与融合**：
  - 粗粒度交叉注意力（场景级）：$Z_{\text{scene}}^t = \text{CrossAttn}(q=V_t^{3D},\, k/v=M_{\text{scene}}^{\text{sel}})$
  - 细粒度交叉注意力（情节级）：$Z_{\text{epi}}^t = \text{CrossAttn}(q=S_t,\, k/v=M_{\text{epi}}^{\text{sel}})$
  - 融合表征 $H_t = [Z_{\text{scene}}^t, Z_{\text{epi}}^t]$，作为扩散策略条件。

### 2.4 Per-Part 扩散策略
- 基座与机械臂各自独立去噪过程 $\epsilon_\theta^{(p)}(z_t, H_t, t)$，$p \in \{\text{base, arm}\}$。
- 训练目标：$\mathcal{L} = \sum_{p} \mathbb{E}_{t,z_t}\|\epsilon - \epsilon_\theta^{(p)}(z_t, H_t, t)\|^2$。
- 这种解耦设计便于异构运动的学习与跨任务迁移。

### 2.5 MoMani 数据引擎
- **在线候选生成**：MLLM prompter → 目标对齐采样(L1) → 安全导航(L2) → 导航-操作缝合(L3)；通过硬质量门控（无碰撞、$\Delta_{\text{pos}}<0.05$m、$\Delta_{\text{ori}}<5°$、100% 任务成功）。
- **离线筛选与审计**：字典序排序(L4) + 场景-相机审计，最终生成 5000+ 多模态轨迹。

## 3. 实验设计

### 3.1 数据集 / 场景
- **模拟**：RoboCasa 仿真器，MoMani 仿真数据集 **7,889 episodes**：
  - 纯导航 57.0%，PnPC2S 10.8%，PnPS2C 10.7%，TOS 10.7%，TOF 10.7%。
- **真实机器人**：TidyBot++ 平台（Kinova Gen3 7-DoF + 全向移动底盘 + 前 RGB-D + 顶视立体相机，30 Hz ROS 同步），**1,200 episodes** 涵盖 OD/CM/PCIS/OR/RK/EnP 六类任务。
- **Benchmark**：作者同时提出 **MoMani**（统一自动化 Co-Gen 流程），是唯一同时覆盖 R（实机）+ S（仿真）+ Navigation/Manipulation/Co-Gen 三类生成模式的基准。

### 3.2 对比方法
- 模拟：BC-T、Diffusion Policy、DP3、π0.5、WB-VIMA。
- 实机：π0.5、Diffusion Policy。

### 3.3 评估任务
- 模拟：PnPC2S、PnPS2C、TOF、TOS、Nav only，以及在 Mobile 设定下的协调控制任务。
- 实机：OD（开抽屉）、CM（关微波炉）、PCIS（杯置水槽）、OR（开冰箱）、RK（旋钮）、EnP（跨房间取物放置，362.9 帧）。

## 4. 资源与算力

- 训练使用 **8 块 NVIDIA A100 GPU**。
- 观测：多视角 RGB-D + 机器人状态；动作空间分解为基座 + 机械臂。
- **未明确披露**：训练时长、单 epoch 时间、总训练 token/step 数、超参数搜索成本等关键算力细节。

## 5. 实验数量与充分性

- **主对比实验**：5 个任务 × 2 类设定（Manipulation/Navigation vs. Mobile Manipulation）× 3 random seeds × 50 episodes/任务 = 约 1500 次模拟 rollout。
- **消融实验**（PnPC2S 任务）：
  - 观测消融（去掉 RGB 或 Point Cloud）。
  - 记忆消融（去掉 EM / SM）。
- **超参敏感度**：窗口大小 $L \in \{2,4,8,16\}$，更新阈值 $\tau \in \{0.1,0.3,0.5,0.7\}$。
- **实机实验**：6 任务 × 20 trials = 120 次真实 rollout。
- **充分性评价**：
  - 优点：兼顾仿真+实机、多任务、多基线，含消融与敏感度分析。
  - 局限：消融仅在单一任务（PnPC2S）上完成，结论的泛化性受限；随机种子数仅 3 个；每任务评估回合 50 个，置信区间可能较宽；实机仅与两个基线比较，未与 MemoryVLA、AnywhereVLA 等同期记忆类方法直接对比。

## 6. 主要结论与发现

- **仿真结果**（RoboCasa）：
  - Manipulation/Navigation 平均 SR：**EchoVLA 0.52 vs. π0.5 0.32**（+0.20）。
  - Mobile Manipulation 平均 SR：**EchoVLA 0.31 vs. π0.5 0.20**（+0.11）。
  - 多数基线在 Mobile 设定下显著退化（如 BC-T 从 0.28→0.05），验证了协调控制的难度。
- **实机结果**（TidyBot++，7m×7m 场地）：
  - 平均 SR：**EchoVLA 0.44 vs. π0.5 0.33 vs. Diffusion Policy 0.32**。
  - 长视野任务 EnP 上 EchoVLA 取得 0.10 SR（基线几乎为 0），验证协同记忆的稳定作用。
- **核心发现**：
  - 场景 + 情节双记忆显著优于单一记忆或无记忆。
  - 几何点云对空间定位至关重要（去掉 PC 后性能下降明显）。
  - $L=8$、$\tau=0.5$ 为最佳超参平衡点。
  - EM 在长视野任务中起到"校正锚"作用，弥补 SM 体素地图的"鬼影"误差。
  - 显式 3D 场景记忆在剧烈结构变化（如冰箱门打开）下会失效。

## 7. 优点

- **神经科学启发的双记忆架构**：PHC + 海马体的类比清晰，场景记忆与情节记忆各司其职又通过粗-细粒度注意力互补，机制可解释性强。
- **分层检索设计**：粗粒度（空间结构）+ 细粒度（时序经验）层次分明，提升长视野一致性。
- **Per-Part 扩散策略**：解耦基座与机械臂动力学，有利于异构动作学习与跨任务迁移。
- **MoMani 数据引擎**：首次统一 Sim + Real + Nav + Manip + Co-Gen 全模式自动化生成，质量门控 + 字典序排序 + 场景审计三层把关。
- **Sim2Real 落地**：在 TidyBot++ 真实平台多任务上验证，且提供完整失败分析。
- **任务多样性**：模拟 4 类 + 实机 6 类任务，覆盖纯导航、操作、移动操作三大类。

## 8. 不足与局限

- **算力披露不完整**：仅给出 GPU 型号与数量，未报告训练时长、显存占用、收敛 epoch、推理时延等关键指标。
- **消融范围有限**：仅在 PnPC2S 单任务上做消融，未在其他任务或实机上交叉验证记忆模块的贡献。
- **基线对比不全面**：未与同期 MemoryVLA、AnywhereVLA、AC-DiT 等强调记忆/导航的工作直接对比，难以判断相对优势。
- **对感知质量高度依赖**：性能依赖高精度深度和里程计；累积漂移会导致 SM"鬼影"；新环境的冷启动问题未解决。
- **动态遮挡失效**：OR 任务中显式 3D SM 在门打开后几何剧变时性能下降，揭示显式表征的固有脆弱性。
- **场景记忆的更新机制较粗糙**：基于固定阈值 $\tau=0.5$ 和 EMA $\alpha=0.2$，缺乏自适应/概率化更新，难以应对非平稳环境。
- **评估规模有限**：模拟每任务 50 episode × 3 seed，统计置信区间可能较宽；实机每任务仅 20 trials，且未报告方差。
- **语言指令单一**：未展示对复杂/含糊指令的鲁棒性。
- **应用限制**：当前假设固定相机布局与已知本体感知配置，迁移到不同形态机器人（人形、腿足等）需重新适配。

（完）
