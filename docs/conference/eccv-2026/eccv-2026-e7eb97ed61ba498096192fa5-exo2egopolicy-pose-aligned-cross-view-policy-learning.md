---
title: "Exo2EgoPolicy: Pose-Aligned Cross-View Policy Learning"
title_zh: Exo2EgoPolicy：基于位姿对齐的跨视角策略学习
authors: "Hritam Basak, Hadi Tabatabaee, Xin Yang, Shreekant Gayaka, Nan Qiao, Yuyin Sun, Cheng-Hao Kuo, Zhaozheng Yin, Min Sun"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/3272.pdf"
tags: ["query:rob-il"]
score: 6.0
evidence: 从人类演示视频学习自我中心操纵策略
tldr: 从大规模人类视频学习机器人操纵策略面临第三视角与自我中心视角间的几何鸿沟。本文提出Exo2EgoPolicy框架，通过基于SE(3)流形的视角对齐位姿翻译将外视角演示映射到自我中心策略空间。该方法显式建模几何模糊性，避免了基于扩散像素合成的时序不一致问题，为模仿学习操纵策略提供了更可靠的跨视角迁移路径。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-e7eb97ed61ba498096192fa5/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1213, \"height\": 545}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-e7eb97ed61ba498096192fa5/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 5564, \"height\": 2800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-e7eb97ed61ba498096192fa5/fig-003.webp\", \"caption\": \"\", \"page\": 11, \"index\": 3, \"width\": 10248, \"height\": 3532}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-e7eb97ed61ba498096192fa5/fig-004.webp\", \"caption\": \"\", \"page\": 12, \"index\": 4, \"width\": 845, \"height\": 272}]"
motivation: 人类第三视角视频与机器人自我中心控制之间存在巨大视点差异，难以直接迁移。
method: 在SE(3)位姿流形上学习视角条件潜变量模型，实现外-内视角对齐的策略翻译。
result: 在操纵策略迁移任务上避免了扩散方法的时序不一致问题，提升了稳定性。
conclusion: 为大规模人类视频模仿学习提供了基于几何结构的跨视角解决方案。
---

## Abstract
Learning robot manipulation policies from large-scale human videos is challenging due to the viewpoint mismatch between thirdperson observations and egocentric robot control. To this end, we introduce Exo2EgoPolicy, a geometry-aware framework that learns egocentric manipulation policies from monocular exocentric video via viewpointaligned pose translation. Unlike prior Exo→Ego approaches that rely on diffusion-based pixel synthesis and often produce temporally inconsistent predictions, our method operates directly on a structured pose manifold and explicitly models the geometric ambiguity inherent in monocular observation. We formulate exocentric-to-egocentric translation as a viewpoint-conditioned latent variable model on the SE(3) manifold that disentangles pose from camera transformation and captures the ambiguity induced by unknown camera extrinsics. Under bounded viewpoint motion, the formulation yields pose trajectories that are identifiable up to a global rigid transformation and supports stable sequential inference through temporal regularization. Beyond representation alignment, we show that for quasi-static manipulation tasks whose rewards depend primarily on relative hand–object geometry, pose captures the key task-relevant information required for policy learning. This enables policy co-training on pose-translated human demonstrations alongside limited robot teleoperation data within a unified human–robot state space. Empirically, Exo2EgoPolicy improves temporal consistency, cross-view alignment, and out-of-distribution policy transfer compared to pixelbased translation and other cross-view co-training baselines, achieving 20–30% higher task success on manipulation benchmarks. These results suggest that geometry-aligned pose representations provide a scalable foundation for cross-view policy learning from human video. Website

---

## 论文详细总结（自动生成）

<think>Let me analyze this paper carefully and produce a comprehensive structured summary in Chinese following the requested format.

The paper is "Exo2EgoPolicy: Geometry-Aware Policy Transfer from Exocentric Human Demonstrations" - it addresses the challenge of learning robot manipulation policies from human videos recorded in third-person (exocentric) view that need to be transferred to egocentric robot control.

Let me organize my summary according to the 8 requested points.</think>

# Exo2EgoPolicy 论文总结

## 1. 核心问题与研究动机

- **核心问题**：在大规模人类视频（多为第三人称/外视角，即 exocentric）中学习机器人操作策略时，面临严重的视角失配——人类演示通常以第三视角录制，而机器人控制需要第一人称（egocentric）视角信号。
- **根本性挑战**：
  - 外→内视角的极端视角变化导致关键区域（如书本内页、手指-物体接触细节）在第三视角下完全被遮挡，问题本身是欠定的（ill-posed inverse problem）。
  - 现有方法分两类且均有缺陷：
    - **几何方法**（如 NeRF 风格）：本质上是回归性的，需要稠密多视角监督，单目输入难以处理严重遮挡。
    - **生成式扩散方法**（像素空间合成）：能"幻觉"不可见区域，但像素级合成常出现几何漂移、时间不一致、帧间抖动，无法保证下游控制所需的结构一致性。
- **研究主张（核心洞察）**：将 Exo→Ego 翻译从"像素合成"任务重新定义为"结构化几何对齐"任务。对于机器人操作，最终目标是恢复与动作相关的几何结构（手-物体相对位姿），而非背景纹理。

## 2. 方法论

### 2.1 整体框架
Exo2EgoPolicy 完全在**结构化位姿流形（SE(3)）**上操作，包含四个紧密耦合的模块：

1. **几何感知的视角条件位姿翻译**（3.1 节）
2. **时序正则化**（3.2 节）
3. **基于 MDP 的位姿充分性论证**（3.3 节）
4. **统一人-机位姿空间的策略协同训练**（3.4 节）

### 2.2 关键技术细节

- **流形定义**：状态 $p_t = (p_t^{\text{hand}}, p_t^{\text{obj}})$ 定义在 $M_{\text{pose}} = M_{\text{hand}} \times M_{\text{obj}}$ 上，其中 $M_{\text{hand}} = SE(3) \times \mathbb{R}^K$（6-DoF 腕部姿态 + K 维手指关节），$M_{\text{obj}} = SE(3)$（物体 6-DoF 位姿）。

- **几何潜在编码**：使用 DINOv2-ViT-L/14 图像编码器 $E_i$ 和 3 层 MLP 位姿编码器 $E_p$，融合得到几何潜在 $z_t \in \mathbb{R}^{563}$。

- **SE(3) 上的扩散模型**：
  - 前向 SDE 在 $M_{\text{pose}}$ 切空间上添加高斯扰动；
  - 反向 SDE 通过分数网络 $s_\psi(p_t^{(\tau)}, \tau, z_t)$ 生成自我中心位姿；
  - 训练目标为连续时间条件分数匹配损失 $\mathcal{L}_{\text{diff}}(\psi)$。

- **相对物体坐标系（关键设计）**：生成目标是物体相对的手部位姿 $(p_t^{\text{obj}})^{-1} \cdot p_t^{\text{hand}}$，自然边缘化掉动态相机。

- **命题 1（可辨识性）**：在相机帧间运动 $\log_{SE(3)}(\Delta c_{t,t+1}) \leq \epsilon$（小量）的条件下，生成的自我中心轨迹可被辨识至全局刚性变换 $T_{\text{global}} \in SE(3)$。

- **时序正则化**：分数网络以自回归方式条件于前一帧 $p_{t-1}$，并通过运动先验 $\Phi$（2 层 GRU，谱归一化使 $L=0.95$）施加时序一致性损失 $\mathcal{L}_{\text{temp}}$：
  $$\mathcal{L}_{\text{temp}} = \sum_{t=2}^{T} \|\hat{p}_t^{\text{hand}} \boxminus \Phi_{\text{hand}}(p_{t-1}, z_t)\|^2 + \beta \|\hat{p}_t^{\text{obj}} \boxminus \Phi_{\text{obj}}(p_{t-1}, z_t)\|^2$$
  其中 $\boxminus$ 为李群差分运算。

- **命题 2（非发散界）**：若单步误差 $\leq \epsilon$ 且 $\Phi$ 是 $L$-Lipschitz（$L<1$，压缩映射），则累积轨迹误差均匀有界：
  $$\sup_{t\in[1,T]} \mathbb{E}[d_{\mathcal{M}}(\hat{p}_t, p_t^*)] \leq \frac{\epsilon}{1-L}$$

- **MDP 充分性论证**：对"准静态"任务（奖励仅依赖相对手-物体几何），相对变换 $\delta_t = (\hat{p}_t^{\text{obj}})^{-1} \cdot \hat{p}_t^{\text{hand}}$ 是充分统计量，与像素外观无关，因此策略能跨域泛化。

- **协同训练**：将翻译后的人类演示 $\mathcal{D}_{\text{human}}^{\text{trans}}$ 与有限遥操作数据 $\mathcal{D}_{\text{robot}}$ 投射到统一状态-动作空间，通过 Action Transformer 策略 $\pi_\theta$ 进行联合行为克隆：
  $$\mathcal{L}_{\text{policy}}(\theta) = \mathbb{E}_{(p,a)\sim\mathcal{D}_{\text{robot}}}[\ell(\pi_\theta(p), a)] + \mu \cdot \mathbb{E}_{(\hat{p},\hat{a})\sim\mathcal{D}_{\text{human}}^{\text{trans}}}[\ell(\pi_\theta(\hat{p}), \hat{a})]$$
  其中 $\mu = 0.3$，通过梯度范数匹配选取。

## 3. 实验设计

### 3.1 数据集
- **位姿翻译训练**：OakInk V2、H2O、AssemblyHands、Assembly101
- **协同训练的人类数据**：TACO、MimicPlay
- **基准测试**：H2O 数据集上的四个泛化划分（未见物体/动作/场景/受试者）；Assembly101；Ego Humanoid Manipulation Benchmark（基于 NVIDIA Isaac Lab，Unitree H1 仿人机器人 + Inspire 灵巧手）

### 3.2 任务
- **短时域原子任务**（7 个）：Stack-Can、Push-Box、Open-Drawer、Close-Drawer、Flip-Mug、Pour-Balls、Open-Laptop
- **长时域多阶段任务**（5 个）：Sort-Cans、Insert-Cans、Unload-Cans、Insert-And-Unload-Cans、Stack-Can-Into-Drawer
- **视觉设置**：Seen（背景匹配训练）、Unseen（22 种未见的背景组合）

### 3.3 对比方法
分四大类：
1. **无人类数据基线**：ACT、EgoVLA-NoPretrain
2. **无视角翻译的协同训练**：Exo-only（直接使用外视角位姿）
3. **像素空间视角翻译**：EgoWorld、4Diff、EgoX（先用扩散生成视频，再用 HAMER + FoundationPose 提取位姿）
4. **自我中心预训练**：EgoVLA（当前最强先验方法）

### 3.4 评估指标
- **位姿翻译**：PA-MPJPE、AUC_J（关节精度）、PA-MPVPE、AUC_V、F@5mm、F@15mm（网格精度）
- **策略评估**：Success Rate（SR）、Progress Rate（PSR）

## 4. 资源与算力

- **训练硬件**：8 张 A100 GPU
- **训练时长**：位姿翻译模块训练 200 个 epoch，batch size 128，AdamW 优化器（lr=3×10⁻⁴，余弦退火，5K warmup，权重衰减 10⁻⁴）
- **分数网络**：12 层 Transformer，8 头注意力，隐藏维度 512
- **运动先验**：2 层 GRU（隐藏层 256），预训练 20 个 epoch，使用谱归一化强制 $L=0.95$
- **扩散设置**：VP-SDE + 余弦噪声调度，训练 1000 步，推理 50 步 DDIM，加权函数 $\lambda(\tau) = 1-\cos(\pi\tau/2)$
- **报告局限**：未明确报告总训练时长（小时/天数），仅给出 epoch 数与硬件配置

## 5. 实验数量与充分性

- **位姿翻译评估**：H2O 四个泛化划分 × 6 个指标 + Assembly101 完整数据集，覆盖了较全面的泛化场景
- **策略协同训练评估**：
  - 短时域 7 任务 × 2 视觉配置（Seen/Unseen）× 7 类方法 = 共 ~100 个数据点
  - 长时域 5 任务 × 2 视觉配置 × 7 类方法
- **消融实验**（表 5）：包含 4 个消融维度——（a）物体相对坐标系；（b）几何潜在编码；（c）自回归条件；（d）时序一致性损失
- **充分性评价**：
  - 优点：方法分类清晰、对比维度全面，提供了定量（指标）+ 定性（可视化）+ 消融的多角度证据
  - 局限：仅在仿真环境（Isaac Lab）测试，缺少真实机器人实验；未见报告多次随机种子下的统计置信区间；EgoX 等最新基线可能时间相近

## 6. 主要结论与发现

- 在 H2O 全部四个泛化划分上，Exo2EgoPolicy 全面超越所有基线，PA-MPJPE 较最强基线 EgoX 降低 27%，F@5mm 在 Unseen Actions 上提升 30% 以上。
- 在 Assembly101 上，PA-MPJPE 从 17.1（EgoX）降至 12.6，F@15mm 提升 6.6 点。
- 策略协同训练上，短时域 Seen 平均 SR 达 81.9%，Unseen 73.7%，均超越 EgoVLA（77.8% / 69.1%）。
- 长时域任务提升更显著：Seen 平均 SR 53.3%（+7.4%），Unseen 36.1%（+7.3%），表明时序一致的位姿序列能直接减少子任务边界的累积误差。
- 关键发现：未经视角翻译直接使用外视角位姿（Exo-only）几乎无收益（+1.1% SR），证明视角翻译是必要的；像素空间翻译受制于位姿提取误差，泛化能力受限。
- 结论：几何对齐的位姿表征是跨视角策略学习可扩展的基础。

## 7. 优点与亮点

- **范式转变**：从"像素合成"转向"结构化几何推理"，任务对齐（视觉→控制）而非追求感知指标。
- **理论保证**：
  - 命题 1 提供 SE(3) 上的可辨识性论证（直至全局刚体变换）
  - 命题 2 提供轨迹误差的紧致上界（压缩映射条件）
  - MDP 框架证明位姿对特定任务类是充分统计量
- **相对物体坐标系**：巧妙地通过 $(p^{\text{obj}})^{-1} \cdot p^{\text{hand}}$ 边缘化未标定相机参数，无需已知相机外参。
- **自回归时序正则化**：直接缓解像素级扩散的"帧间抖动"问题，提供控制可用的连续运动学信号。
- **统一协同训练空间**：无需硬件改装或显式重定向，将人手作为"不同 embodiment"在同一运动学空间内训练。
- **实证充分**：相比像素基线，任务成功率绝对提升 20–30%。

## 8. 不足与局限

- **缺乏真实机器人验证**：所有策略评估均在 NVIDIA Isaac Lab 仿真环境中进行，Sim2Real gap 未讨论。
- **任务范围有限**：仅限"准静态"操作任务，对快速运动或接触丰富的动态任务（如工具敲击、双手协调中的接触力）未验证充分性假设是否成立。
- **位姿提取依赖外部模型**：当前流程需依赖 HAMER（手部）和 FoundationPose（物体）作为外部观测；这些模型本身的失败模式会传递到下游策略。
- **单目输入的固有局限**：在严重遮挡或退化场景下，单目位姿估计可能失效。
- **未明确说明计算开销与延迟**：扩散模型在推理时可能带来实时性挑战，论文未给出端到端推理耗时。
- **训练时长报告不完整**：仅提到 epoch 数和 GPU 型号，未给出 wall-clock 训练时间。
- **统计显著性未充分验证**：未报告多次随机种子下的置信区间或显著性检验，单次实验可能存在波动。
- **数据集偏差**：外→内视角训练数据集中物体类目有限，对训练集之外的新颖物体泛化能力虽优于基线，但提升是否可持续仍存疑。
- **依赖人类视频的存在性**：方法仍需大量"合适"的人类演示，对录制条件（背景、运动范围）有要求，并非完全"任意互联网视频可用"。

（完）
