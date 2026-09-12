---
title: "One-Step Flow Policy: Self-Distillation for Fast Visuomotor Policies"
title_zh: 一步流策略：面向快速视运动策略的自蒸馏方法
authors: "Shaolong Li, Lichao Sun, Yongchao Chen"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/15012.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 通过自蒸馏实现快速视运动策略，端到端动作生成
tldr: 生成式流模型和扩散模型为高精度机器人策略提供了所需的连续多模态动作分布，但其依赖迭代采样导致严重的推理延迟，降低了控制频率并损害了时间敏感操纵任务的性能。本文提出一步流策略OFP，一种从零开始的自蒸馏框架，可在不使用预训练教师的情况下实现高保真单步动作生成。该方法统一了自一致性损失以强制跨时间间隔的一致传输，并结合自引导正则化以锐化向高密度专家模式的预测。该工作直接服务于端到端视运动学习对机器人操纵的支撑，通过消除迭代采样延迟提升实时部署效率。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-001.webp\", \"caption\": \"\", \"page\": 6, \"index\": 1, \"width\": 312, \"height\": 1047}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 576, \"height\": 576}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 454, \"height\": 454}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-004.webp\", \"caption\": \"\", \"page\": 6, \"index\": 4, \"width\": 312, \"height\": 1053}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-005.webp\", \"caption\": \"\", \"page\": 9, \"index\": 5, \"width\": 1032, \"height\": 524}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-006.webp\", \"caption\": \"\", \"page\": 13, \"index\": 6, \"width\": 680, \"height\": 508}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-007.webp\", \"caption\": \"\", \"page\": 13, \"index\": 7, \"width\": 684, \"height\": 508}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-008.webp\", \"caption\": \"\", \"page\": 13, \"index\": 8, \"width\": 684, \"height\": 508}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-f3e246d19efd7205317e31cc/fig-009.webp\", \"caption\": \"\", \"page\": 13, \"index\": 9, \"width\": 684, \"height\": 508}]"
motivation: 生成式流和扩散模型依赖迭代采样导致推理延迟，损害了时间敏感操纵任务的控制频率与性能。
method: 提出一步流策略OFP，从零开始的自蒸馏框架，结合自一致性损失与自引导正则化实现单步动作生成。
result: 实现了高保真单步动作生成，显著降低了推理延迟。
conclusion: 为高精度机器人策略在实时操纵中的部署提供了高效的端到端视运动方案。
---

## Abstract
Generative flow and diffusion models provide the continu-ous, multimodal action distributions needed for high-precision roboticpolicies. However, their reliance on iterative sampling introduces severeinference latency, degrading control frequency and harming performancein time-sensitive manipulation. To address this problem, we proposethe One-Step Flow Policy (OFP), a from-scratch self-distillation frame-work for high-fidelity, single-step action generation without a pre-trainedteacher. OFP unifies a self-consistency loss to enforce coherent transportacross time intervals, and a self-guided regularization to sharpen predic-tions toward high-density expert modes. In addition, a warm-start mech-anism leverages temporal action correlations to minimize the generativetransport distance. Evaluations across 56 diverse simulated manipulationtasks demonstrate that a one-step OFP achieves state-of-the-art results,outperforming 100-step diffusion and flow policies while accelerating ac-tion generation by over 100×. We further integrate OFP into the π0.5model on RoboTwin 2.0, where one-step OFP surpasses the original 10-step policy. These results establish OFP as a practical, scalable solutionfor highly accurate and low-latency robot control.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "One-Step Flow Policy: Self-Distillation for Fast Visuomotor Policies" organized into 8 specific sections. Let me carefully analyze the paper content and structure my response.

The paper is about:
- Problem: Flow/diffusion models for robot policies need iterative sampling → high inference latency → bad for time-sensitive manipulation
- Method: One-Step Flow Policy (OFP) - from-scratch self-distillation framework
  - Self-consistency loss: enforces coherent transport across time intervals
  - Self-guided regularization: sharpens predictions toward high-density expert modes
  - Warm-start mechanism: leverages temporal action correlations
- Experiments: 56 simulated tasks (Adroit, DexArt, MetaWorld, RoboTwin 2.0)
- Integration with π0.5 model

Let me organize this into the 8 required sections. I'll write in Chinese with Markdown formatting.

Key details to include:
1. Core problem/motivation: iterative sampling latency
2. Method: OFP with self-consistency, self-guided regularization, warm-start
3. Experiments: 56 tasks across 4 benchmarks, comparison with DP, FM Policy, CP, OneDP, MP1
4. Resources: Only mentions FASRC cluster at Harvard, no specific GPU details
5. Number of experiments: 2D + 3D + VLA integration + ablations
6. Conclusions: state-of-the-art on 56 tasks, 100x speedup, integration with π0.5
7. Strengths
8. Limitations</think>

# 一步流策略（OFP）：面向快速视运动策略的自蒸馏方法 —— 论文总结

## 1. 论文核心问题与整体含义

- **研究背景**：生成式流（Flow Matching）和扩散（Diffusion）模型凭借对连续多模态动作分布的天然建模能力，已成为高精度机器人视运动策略的主导范式，已被应用于 VLA 模型（如 π0、π0.5、RDT-1B、GR00T 等）中。
- **核心矛盾**：这类生成式策略依赖迭代求解 ODE/SDE，单次动作生成需要数十至上百次网络前向传播，引入严重的**推理延迟瓶颈**。
  - 在高速抓取、动态交互等时间敏感场景中，延迟直接降低控制频率、放大复合误差，导致任务失败。
- **核心问题**：**如何在不损失控制精度的前提下，将生成式策略加速到极少步数（甚至单步）？**
- **现有方案的不足**：
  - 高阶数值求解器：极少步下离散误差不可控。
  - 一致性蒸馏（如 CP）：轨迹匹配目标具"模式覆盖"性质，单步预测精度不足。
  - 分数蒸馏（如 OneDP）：具"模式寻求"性质，牺牲多样性且只能单步推理，无法以算力换精度。
  - MeanFlow 系列（如 MP1）：依赖 JVP 计算，显存大、优化不稳。

## 2. 方法论：OFP 的核心思想与关键技术

### 2.1 总体框架
- 提出 **One-Step Flow Policy (OFP)**：一个**从零训练、不依赖预训练教师模型**的自蒸馏框架。
- 三大核心组件：
  1. **自一致性训练（Self-Consistency Training）** —— 沿轨迹保证跨时间区间一致性。
  2. **自引导正则化（Self-Guided Regularization）** —— 利用模型自身分数进行 CFG 增强，引导单步预测收敛到专家模式。
  3. **热启动机制（Warm-Start）** —— 利用连续动作块的时间相关性，提供强先验降低单步传输距离。

### 2.2 自一致性训练
- 不直接拟合瞬时速度场，而是学习**区间平均速度场** $u_\theta(z_t, t, r \mid o)$（$0 \le t \le r \le 1$）。
- 区间更新规则：$z_r = z_t + (r-t) u_\theta(z_t, t, r \mid o)$。
- 使用 **EMA 教师模型** $u_{\theta^-}$ 预测子区间终点：
  - $\hat{z}_r = z_m + (r-m) u_{\theta^-}(z_m, m, r)$
  - 训练目标：$u_{\text{target}} = (\hat{z}_r - z_t)/(r-t)$
  - 损失：$\mathcal{L}_{\text{self-consistency}} = \mathbb{E}\| u_\theta - u_{\text{target}}\|^2$
- **时间收缩调度（Time-Contracting Schedule）**：$m \sim \mathcal{U}[t, t+(r-t)\rho(s)]$，$\rho(s)$ 随训练步单调递减。早期 $\rho \approx 1$ 时利用插值 $z_m$ 降低教师不可靠带来的自举误差；后期 $\rho \to 0$ 强制局部一致性以精修轨迹。
- **边界锚定损失** $\mathcal{L}_{\text{flow}}$：对瞬时速度做标准 Flow Matching 监督，保证多步推理能力与数据分布贴合。
- **命题 1 理论保证**：在 Lipschitz 连续 + 教师准确条件下，$\rho(s) \to 0$ 时 $u_{\text{target}}$ 收敛到真实平均速度场。
- **与 MeanFlow 区别**：避免昂贵的 Jacobian-Vector Product（JVP），仅用前向计算；附录给出当 $(m-t) \to 0$ 时其目标等价于 MeanFlow 的有限差分近似。

### 2.3 自引导正则化
- 仅用自身 EMA 模型 $u_{\theta^-}$ 估计分数，无需外部教师。
- 利用 OT 路径关系 $s(\tilde z_t \mid o) = \frac{t\, u(\tilde z_t, t, t \mid o) - \tilde z_t}{1-t}$。
- 基于 **Classifier-Free Guidance（CFG）** 的 CA（CFG-Augmentation）项构造自引导目标：
  - $s_{\text{target}} = \text{sg}\big[u_\theta(z_t,t,1 \mid o) - \big(u_{\theta^-}(\tilde z_{t'}, t', t' \mid \phi) - u_{\theta^-}(\tilde z_{t'}, t', t' \mid o)\big)\big]$
  - 损失：$\mathcal{L}_{\text{self-guidance}} = \mathbb{E}\|u_\theta - s_{\text{target}}\|^2$
- 通过**条件丢弃**（以概率 $p_{\text{drop}}$ 将 $o$ 替换为 $\phi$）让单网络同时承载条件/无条件动力学。
- 梯度语义：最小化该损失等价于最小化反向 KL 散度的 CFG 增强项，使生成结果被"推开"无条件模式、向专家高密度模式收敛。

### 2.4 统一训练目标
$$\mathcal{L}_{\text{self-distill}} = \mathcal{L}_{\text{flow}} + \lambda_c \mathcal{L}_{\text{self-consistency}} + \lambda_g \mathcal{L}_{\text{self-guidance}}$$

### 2.5 热启动机制（Warm-Start）
- 在 receding-horizon 控制下，将上一未执行片段 $[a_{h+1}, \dots, a_H]$ 移位并以末端动作填充，形成完整长度先验 $a_{\text{warm}}$。
- 推理时不再从高斯噪声出发，而是：
  - $z_{t_w} = (1-t_w)\epsilon + t_w a_{\text{warm}}$
  - 单步生成：$\hat a = z_{t_w} + (1-t_w) u_\theta(z_{t_w}, t_w, 1 \mid o)$
- 该初始化与训练时的自引导构造结构一致，**训练零成本**即可显著降低传输距离。

### 2.6 灵活推理策略
- **单步**：$\hat a = \epsilon + u_\theta(\epsilon, 0, 1 \mid o)$。
- **少步**：按离散时间表 $\{0=\tau_0<\dots<\tau_K=1\}$ 递归调用区间速度场，以算力换精度。

## 3. 实验设计

### 3.1 数据集与基准
- **2D 图像条件**：
  - Adroit（3 个任务）：Door / Hammer / Pen / Bucket / Faucet / Laptop / Toilet 等。
  - DexArt（4 个任务）。
- **3D 点云条件**：
  - 同上 7 个任务 + **MetaWorld（49 个任务）**，按难度分为 Easy / Medium / Hard / Very Hard。
  - 单任务学习（Adroit、DexArt）+ 大规模多任务学习（MetaWorld）。
- **VLA 集成**：**RoboTwin 2.0**（双臂操作，4 个任务），含域随机化（杂乱干扰物、背景纹理、光照、桌面高度）。

### 3.2 对比方法
- 多步基线：**Diffusion Policy (DP/DP3)**、**Flow Matching Policy (FM Policy)**，NFE = 100/10。
- 蒸馏/加速基线：
  - **Consistency Policy (CP)** —— 一致性蒸馏，从预训练 DP3 教师蒸馏。
  - **OneDP** —— 分数蒸馏，单步专用。
  - **MP1** —— MeanFlow 改造，从零训练。
- VLA 集成对比：**CFM**、**Shortcut Models**、**Improved MeanFlow (iMF)**，对比 π0.5 10 步基线。

### 3.3 评估指标
- 成功率（Success Rate），3 个随机种子，报告均值±标准差。
- 壁钟时间（Wall-clock latency, ms）。

## 4. 资源与算力

- 文中**仅**在致谢部分提到：实验在 **Harvard FASRC 集群**（FAS Division of Science Research Computing Group）上运行。
- **未明确披露**：所用 GPU 型号/数量、单次训练时长、推理硬件等具体算力细节。
- 报告的推理延迟：OFP 单步约 **17.58 ms / action chunk**；DP3 100 步约 3225.67 ms；3D FM Policy 100 步约 1865.72 ms（即相对加速约 **183×** 与 **106×**）。

## 5. 实验数量与充分性

- **主结果实验**：
  - 2D 任务 7 个（NFE=1 vs 100/10 步基线）。
  - 3D 任务 56 个（含 MetaWorld 4 个难度分级），覆盖单任务与多任务。
- **少步 vs 单步对比**（Tab. 3）：NFE=1 与 NFE=4 同时验证。
- **数据效率分析**（Fig. 4）：在 DexArt Faucet 上扫描 20/50/100/150 演示数据量，对比 OFP 与 MP1。
- **消融实验**：分别移除自一致性、自引导正则化、热启动；附录给出详细结果。
- **VLA 集成**：π0.5 上 4 个 RoboTwin 2.0 任务，与 3 种从零加速方法及 10 步基线对比。
- **充分性评估**：
  - **优点**：覆盖 2D/3D/VLA、任务级数与难度分级兼具，单步与少步并重，3 个种子统计。
  - **不足**：
    - 全部为**仿真**实验，未在真实机器人上验证。
    - 消融仅给摘要描述，细节放附录，主文中可读性受限。
    - DP3/FM Policy 在 3D 上不同任务的最优 NFE 设置未充分扫描。

## 6. 主要结论与发现

- **2D 图像条件**（Tab. 1）：1 步 OFP 平均 68.3%，**超过** DP 100 步（64.2%）与 FM Policy 100 步（67.2%）。
- **3D 点云条件**（Tab. 2）：1 步 OFP 平均 71.6%，相对 DP3 100 步提升约 8%、相对 3D FM Policy 100 步提升 19.7%，在 MetaWorld 几乎所有难度档位均最佳。
- **延迟 vs 精度**（Fig. 1）：单步 OFP 同时占据"高成功 + 低延迟"左上角，相对 DP3/FM Policy 加速 **100× 以上**。
- **少步 vs 单步**（Tab. 3）：OFP 在 NFE=1 即可击败 CP/OneDP，且随 NFE 增大持续提升（4 步时达 66.2%）。
- **数据扩展性**（Fig. 4）：20 demos 时 OFP 明显优于 MP1；150 demos 时仍稳定上升，而 MP1 出现下降。
- **VLA 集成**（Fig. 5）：π0.5 + OFP（NFE=1）在 4 个 RoboTwin 2.0 任务上平均 **94.7%**，**超越**原始 π0.5（NFE=10）。
- **优化稳定性**：MP1 因 JVP 出现高方差与损失尖峰；OFP 仅用前向计算，训练更稳。

## 7. 优点与方法/实验亮点

- **从零自蒸馏、无需教师**：摆脱对预训练 DP3/扩散教师的依赖，简化部署。
- **统一两派蒸馏范式**：在同一模型上同时具备轨迹一致性（few-step 强）和 CFG 引导的分布级锐化（one-step 强）。
- **避免 JVP**：相对 MeanFlow 类方法显存与训练时间显著降低，优化更稳。
- **训练免费的 Warm-Start**：在推理时即插即用，同时提升时序平滑与精度。
- **理论与实践结合**：命题 1 与附录对收敛性的形式化证明，对 MeanFlow 目标给出有限差分等价性论证。
- **广泛验证**：覆盖 56 个仿真任务 + VLA 大模型集成，单/少步均强，延迟优势数量级。

## 8. 不足与局限

- **仅仿真验证**：所有结果在 Adroit/DexArt/MetaWorld/RoboTwin 2.0 上完成，**未在物理机器人系统上评估**，作者明确将此列为下一步工作。
- **算力披露缺失**：未给出 GPU 型号/数量、训练时长等具体算力信息，难以横向比较训练成本。
- **热启动的依赖性**：单步加速部分得益于 Warm-Start，但文中未系统讨论 Warm-Start 在不同执行 horizon、不同任务上的鲁棒性边界。
- **CFG 引导的代价**：自引导正则化需要条件丢弃以联合学习无条件分支，超参数（$p_{\text{drop}}$、$\lambda_g$、$\lambda_c$、$\alpha$、$t_w$ 等）的敏感性与最优取值未充分披露。
- **方法局限性**：作者也指出 OFP 与"系统级加速"（量化、结构化剪枝）是正交的，但本文未实际结合这些技术。
- **可能偏差**：
  - 与 MP1 在 MetaWorld Very Hard 上差距不大（49.2% vs 47.7%/32.3%），但与 CP、OneDP 对比时 OFP 提升幅度在不同任务上并不均匀。
  - 仿真环境的接触动力学与视觉域随机化水平与真实硬件仍存在差距，迁移风险未知。

（完）
