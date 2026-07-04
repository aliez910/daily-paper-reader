---
title: "Prior Does Matter: Visual Navigation via Denoising Diffusion Bridge Models"
title_zh: Prior Does Matter：基于去噪扩散桥模型的视觉导航
authors: "Ren, Hao, Zeng, Yiming, Bi, Zetong, Wan, Zhaoliang, Huang, Junlong, Cheng, Hui"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Ren_Prior_Does_Matter_Visual_Navigation_via_Denoising_Diffusion_Bridge_Models_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 基于扩散的视觉机器人控制模仿学习但聚焦导航
tldr: 扩散模仿学习在机器人任务中取得进展，但视觉导航中从高斯噪声初始化导致冗余去噪。本文提出基于去噪扩散桥模型的视觉导航框架，使用更贴近目标动作分布的先验指导生成。该方法虽涉及模仿学习与视觉控制，但聚焦导航而非操纵任务。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 788, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1805, \"height\": 729, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 466, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1799, \"height\": 440, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 837, \"height\": 503, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1791, \"height\": 550, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 871, \"height\": 439, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-ren-prior-does-matter-visual-navigation-via-denoising-diffusion-bridge-models-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 865, \"height\": 368, \"label\": \"Table\"}]"
motivation: 扩散策略从高斯噪声出发，难以高效生成导航动作。
method: 采用去噪扩散桥模型，用更接近目标的先验生成动作序列。
result: 提升了视觉导航中扩散策略的精度与效率。
conclusion: 为先验选择对扩散模仿策略的重要性提供了新视角。
---

## Abstract
Recent advancements in diffusion-based imitation learning, which shows impressive performance in modeling multimodal distributions and training stability, have led to substantial progress in various robot learning tasks. In visual navigation, previous diffusion-based policies typically generate action sequences by initiating from denoising Gaussian noise. However, the target action distribution often diverges significantly from Gaussian noise, leading to redundant denoising steps and increased learning complexity. Additionally, the sparsity of effective action distributions makes it challenging for the policy to generate accurate actions without guidance. To address these issues, we propose a novel, unified visual navigation framework leveraging the denoising diffusion bridge models named NaviBridger. This approach enables action generation by initiating from any informative prior actions, enhancing guidance and efficiency in the denoising process. We explore how diffusion bridges can enhance imitation learning in visual navigation tasks and further examine three source policies for generating prior actions. Extensive experiments in both simulated and real-world indoor and outdoor scenarios demonstrate that NaviBridger accelerates policy inference and outperforms the baselines in generating target action sequences. Code is available at https://github.com/hren20/NaiviBridger.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Prior Does Matter: Visual Navigation via Denoising Diffusion Bridge Models" following a specific structure with 8 points. Let me analyze the paper carefully and provide a comprehensive summary.

The paper proposes NaviBridger, a framework using Denoising Diffusion Bridge Models (DDBM) for visual navigation. Let me organize my response according to the requested structure.

Key points from the paper:
1. Problem: Standard diffusion policies start from Gaussian noise, which is far from the target action distribution, leading to redundant denoising steps and difficulties in generating accurate actions.
2. Method: Uses diffusion bridges that start from informative prior actions rather than Gaussian noise. Three prior policies: Gaussian, Rule-based, Learning-based (CVAE).
3. Experiments: Indoor (Stanford 2D-3D-S) and Outdoor (Gazebo citysim) simulations, real-world tests. Baselines: NoMaD, ViNT.
4. Resources: Single NVIDIA RTX TITAN GPU, ~30 hours training.
5. Multiple experiments with different priors, denoising steps, ablation studies.
6. Learning-based prior achieves best performance, ~90% success rate.
7. Strengths: Novel application of DDBM to navigation, theoretical error bound analysis, multiple prior strategies.
8. Limitations: Performance with high-speed moving objects, rule-based priors lack generalization.

Let me write this out in a well-organized Markdown format.</think>

# 论文总结：Prior Does Matter：基于去噪扩散桥模型的视觉导航（NaviBridger）

## 1. 核心问题与研究动机

- **任务背景**：视觉导航是移动机器人的核心能力之一，主流方法由「全局规划器」与「局部规划器」组成。基于扩散模型的模仿学习局部规划器因能建模多模态分布且训练稳定，近来取得显著进展（如 NoMaD、ViNT 等）。
- **关键问题**：
  - 现有扩散策略以 **高斯噪声** 作为去噪起点，但目标动作分布与高斯噪声差异显著，造成 **去噪步骤冗余、学习复杂度升高**。
  - 有效动作在分布中极为 **稀疏**，从混沌噪声出发难以生成精确动作。
- **核心洞察**：能否用一个 **结构化、任务相关的源分布**（而非随机高斯）作为去噪起点？这与最优传输理论（Doob's h-transform）相契合，并已在图像翻译、修复等配对任务中验证有效。
- **主要挑战**：视觉导航中**不存在天然的源分布**，需要构造适合的初始分布并将扩散桥技术适配到导航任务。

---

## 2. 方法论：NaviBridger 框架

### 2.1 整体架构
框架包含三大模块：
- **特征提取模块**：Transformer 编码器对当前与历史观测 $O=\{I_t\}_{t=T-p}^{T}$ 及目标图像 $I_g$ 提取上下文向量 $c_t$。
- **先验动作生成模块**：由 $c_t$ 经不同策略生成源动作 $a_s \in \pi_s$。
- **去噪扩散桥模块**：通过 DDBM 将 $a_s$ 平滑变换为目标动作 $a \in \pi$。去噪网络采用 **1-D temporal CNN + FiLM 条件调制**，迭代去噪 $k$ 次。

### 2.2 关键技术：扩散桥在模仿学习中的应用
- 使用 **Doob's h-transform** 在两端点 $(a_s, a_0)$ 之间构造扩散桥：
  $$da_t = [f(a_t, t) - g^2(t)(s(a_t, t, a_T, T) - h(a_t, t, a_T, T))]dt + g(t)d\hat{w}_t$$
- 采用 **DDBM 的近似采样分布** $q(a_t|a_0, a_T) = \mathcal{N}(\hat{\mu}_t, \hat{\sigma}_t^2 I)$ 进行重参数化与去噪。
- 训练时使用 **加权 MSE 去噪桥损失** $L_b$。

### 2.3 理论分析：误差上界
- 通过 KL 散度度量源分布 $\pi_s(a_T)$ 与目标分布 $\pi(a_0)$ 之间的偏差：
  $$\mathbb{E}[\|a_t - a_0\|^2] \leq C \cdot D_{KL}(\pi_s(a_T)\|\pi(a_0))$$
- 结论：**源分布越接近目标分布，误差上界越小，DDBM 性能越好**。

### 2.4 三种先验动作生成策略
| 策略 | 实现方式 | 特点 |
|---|---|---|
| **Gaussian Prior** | 标准高斯噪声 | 无信息先验；可作为与 DDPM 的公平对照 |
| **Rule-based Prior** | 全连接层 + 抛物线路径（依据预测距离 $d$ 与行为分类：直行、左转、右转、左/右 U 弯） | 可解释；但跨场景泛化弱 |
| **Learning-based Prior** | 轻量级 CVAE，基于专家数据学习观测-动作映射 | 接近目标分布，效果最佳 |

### 2.5 总损失函数
$$\mathcal{L} = \lambda_b \mathcal{L}_b + \lambda_p \mathcal{L}_p + \lambda_d \mathcal{L}_d$$
包含扩散桥损失 $L_b$、先验损失 $L_p$（规则式含 MSE+CE，学习式含 MSE+KL）、时间距离损失 $L_d$。

---

## 3. 实验设计

### 3.1 数据集
训练数据来自四个公开数据集的合并：
- **RECON**、**SCAND**、**GoStanford**、**SACSoN**
- 提供连续图像帧序列与对应位姿信息。

### 3.2 仿真场景
- **室内**：Stanford 2D-3D-S
- **室外**：Gazebo CitySim
- 每个场景设置两种任务：
  - **Basic Task**：测试环境与拓扑地图配置一致（长距离导航）。
  - **Adaptation Task**：测试环境加入未在地图中的障碍物（适应性）。

### 3.3 真实世界测试
- 部署平台：**Nvidia Jetson Orin AGX** 板载机器人。
- 仅使用 RGB 输入。

### 3.4 对比基线
- **NoMaD**（基于 DDPM 的扩散策略，视觉导航 SOTA）
- **ViNT**（基于回归的视觉导航基础模型，含 CNN 与自注意力）

### 3.5 评价指标
- **Length**：完成任务时的路径长度（均值±方差）
- **Collision**：每次试验的平均碰撞次数
- **Success Rate**：成功率（包含是否到达、是否卡住、超时）

---

## 4. 资源与算力

- **GPU**：单卡 **NVIDIA RTX TITAN**
- **训练时长**：约 **30 小时**，30 个 epoch
- **学习率**：$1 \times 10^{-4}$；批量大小 256（学习式方法为 224）
- **DDBM 参数**：VE 模型，$\sigma_0=\sigma_T=0.5$，默认采样步数 $k=10$
- 推理部署在 **Nvidia Jetson Orin AGX**，但论文**未明确报告部署时的功耗、实时频率、内存占用等指标**。

---

## 5. 实验数量与充分性

- **仿真定量实验**（Table 1）：室内外 × 基本/适应任务 × 3 种先验 = **12 组数据点**对比基线。
- **消融实验**：
  - 去噪步数 $k \in \{1,4,7,10\}$ 对 DDPM 与 DDBM 的影响（Table 2，4 个数据集共 5 个评价项）。
  - 源/目标分布作用对比（Table 3）：直接使用先验 vs. 经过桥去噪后的性能。
  - 步数-成功率-推理时间联合分析（Fig. 5）。
- **可视化对比**：去噪过程在仿真与真实环境下的路径展示（Fig. 4），以及二维合成数据上的 EMD 演示（Fig. 3）。
- **充分性评价**：
  - 覆盖了**多种场景、任务难度、先验策略与超参数**，整体较为充分。
  - 与 SOTA 基线（NoMaD、ViNT）的对比使用相同数据集训练，**公平性较好**。
  - 但每个表格仅展示单一随机种子的统计结果，**未报告多次随机种子下的方差**，稳健性证据略弱。

---

## 6. 主要结论与发现

- **先验策略效果排序**：Learning-based > Gaussian > Rule-based > 原始 DDPM 基线。
- **关键定量结果**（室内适应任务）：学习式先验 DDBM 成功率达 **88%**，NoMaD 为 32%，ViNT 仅 28%；室外学习式先验同样以 64% 显著领先 NoMaD 的 52%。
- **去噪效率**：即便使用高斯先验，DDBM 也只需 2-4 步即可收敛到稳定动作，远少于 DDPM；学习式先验在 10 步时达到约 90% 成功率。
- **去噪步数鲁棒性**：DDBM 在 $k$ 从 10 降至 1 时性能波动较小，而 DDPM 在步数减少时误差显著上升。
- **理论验证**：KL 误差上界分析得到实验证实——源分布越接近目标，桥去噪误差越小。
- **统一性**：NaviBridger 在无合适先验时可退化为标准扩散模型，兼容性好。

---

## 7. 优点与亮点

- **首创性**：首次将 **去噪扩散桥模型（DDBM）** 引入视觉导航任务，弥补了机器人学习领域应用扩散桥的空白。
- **理论深度**：给出了**基于 KL 散度的误差上界**，为「为什么需要先验」提供了数学依据。
- **多策略灵活性**：系统对比了三种先验（高斯、规则、学习式），并讨论各自的优劣与适用场景，层次清晰。
- **统一框架**：保留了与标准扩散模型的兼容性，向后兼容性强。
- **工程完整性**：在仿真与真实机器人平台上均完成验证，提供了开源代码。
- **可视化直观**：2D 合成数据、仿真、真实环境三层可视化清晰展示了「先验引导 vs. 高斯噪声」的差异。

---

## 8. 不足与局限

- **随机种子与方差**：主要结果（Table 1、Table 3）仅给出单次训练的标准差，**未报告多次随机种子重训练的方差**，统计显著性证据不足。
- **规则式先验泛化差**：依赖手工设计的抛物线路径与行为分类，在未见过的拓扑结构下表现下降（室外仅 14% 成功率）。
- **推理时间权衡**：DDBM 在相同步数下推理时间**略长于 DDPM**（Fig. 5），尽管所需步数更少，实际部署的实时性收益需进一步评估。
- **动态场景能力有限**：作者明确指出，**高速移动障碍物场景下**性能下降，需要更快响应或自适应策略。
- **缺乏失败案例分析**：未深入分析桥去噪失败时（如先验严重偏离目标）的失效模式。
- **算力细节不足**：未明确报告部署在 Jetson Orin AGX 上的具体帧率、功耗与延迟，仅在实验中提及「可部署」。
- **CVAE 先验的训练开销**：虽然 CVAE 被称作「轻量级」，但引入额外训练负担与超参调节成本，文中未量化对比端到端训练成本。
- **真实世界实验规模**：仅定性展示了真实环境路径，**缺少真实场景下完整的成功率/碰撞次数定量统计**。

（完）
