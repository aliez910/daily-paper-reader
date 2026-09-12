---
title: "ComplexMimic: Human–Scene Interaction Imitation in Complex 3D Environments"
title_zh: ComplexMimic：复杂三维环境中的人-场景交互模仿
authors: "Lu Pan, Hongwei Zhao"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/1523.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 面向复杂环境中人-场景交互的物理模仿学习
tldr: 基于物理的人-场景交互模仿学习对具身智能至关重要，能弥合运动学三维运动与真实世界动力学之间的差距，但现有方法主要聚焦简化场景设置，复杂环境很大程度上未被探索，限制了其在实际场景中的适用性。本文聚焦复杂环境下的人-场景交互模仿，提出ComplexMimic框架，通过双流策略解释不完美的动作捕捉数据以重建多样化交互。该工作的核心关注点是人体而非机器人的模仿学习，与本主题中机器人操纵的直接相关性较弱，但其在复杂环境中模仿学习的方法思路仍具有方法论参考价值。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 5929, \"height\": 2821}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-002.webp\", \"caption\": \"\", \"page\": 6, \"index\": 2, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-003.webp\", \"caption\": \"\", \"page\": 6, \"index\": 3, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-004.webp\", \"caption\": \"\", \"page\": 6, \"index\": 4, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-005.webp\", \"caption\": \"\", \"page\": 6, \"index\": 5, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-006.webp\", \"caption\": \"\", \"page\": 6, \"index\": 6, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-007.webp\", \"caption\": \"\", \"page\": 6, \"index\": 7, \"width\": 331, \"height\": 415}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-008.webp\", \"caption\": \"\", \"page\": 9, \"index\": 8, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-009.webp\", \"caption\": \"\", \"page\": 9, \"index\": 9, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-010.webp\", \"caption\": \"\", \"page\": 9, \"index\": 10, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-011.webp\", \"caption\": \"\", \"page\": 9, \"index\": 11, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-012.webp\", \"caption\": \"\", \"page\": 9, \"index\": 12, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-013.webp\", \"caption\": \"\", \"page\": 9, \"index\": 13, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-014.webp\", \"caption\": \"\", \"page\": 9, \"index\": 14, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-015.webp\", \"caption\": \"\", \"page\": 9, \"index\": 15, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-016.webp\", \"caption\": \"\", \"page\": 9, \"index\": 16, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-017.webp\", \"caption\": \"\", \"page\": 9, \"index\": 17, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-018.webp\", \"caption\": \"\", \"page\": 9, \"index\": 18, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-019.webp\", \"caption\": \"\", \"page\": 9, \"index\": 19, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-020.webp\", \"caption\": \"\", \"page\": 9, \"index\": 20, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-021.webp\", \"caption\": \"\", \"page\": 9, \"index\": 21, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-022.webp\", \"caption\": \"\", \"page\": 9, \"index\": 22, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-023.webp\", \"caption\": \"\", \"page\": 9, \"index\": 23, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-024.webp\", \"caption\": \"\", \"page\": 9, \"index\": 24, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-025.webp\", \"caption\": \"\", \"page\": 9, \"index\": 25, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-026.webp\", \"caption\": \"\", \"page\": 9, \"index\": 26, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-027.webp\", \"caption\": \"\", \"page\": 9, \"index\": 27, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-028.webp\", \"caption\": \"\", \"page\": 9, \"index\": 28, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-029.webp\", \"caption\": \"\", \"page\": 9, \"index\": 29, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-030.webp\", \"caption\": \"\", \"page\": 9, \"index\": 30, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-031.webp\", \"caption\": \"\", \"page\": 9, \"index\": 31, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-032.webp\", \"caption\": \"\", \"page\": 9, \"index\": 32, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-033.webp\", \"caption\": \"\", \"page\": 9, \"index\": 33, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-034.webp\", \"caption\": \"\", \"page\": 9, \"index\": 34, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-035.webp\", \"caption\": \"\", \"page\": 9, \"index\": 35, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-036.webp\", \"caption\": \"\", \"page\": 9, \"index\": 36, \"width\": 472, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-037.webp\", \"caption\": \"\", \"page\": 9, \"index\": 37, \"width\": 473, \"height\": 650}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-038.webp\", \"caption\": \"\", \"page\": 14, \"index\": 38, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-039.webp\", \"caption\": \"\", \"page\": 14, \"index\": 39, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-040.webp\", \"caption\": \"\", \"page\": 14, \"index\": 40, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-041.webp\", \"caption\": \"\", \"page\": 14, \"index\": 41, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-042.webp\", \"caption\": \"\", \"page\": 14, \"index\": 42, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-043.webp\", \"caption\": \"\", \"page\": 14, \"index\": 43, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-044.webp\", \"caption\": \"\", \"page\": 14, \"index\": 44, \"width\": 709, \"height\": 1035}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-01371bdf1ffb1d95bd2f7b93/fig-045.webp\", \"caption\": \"\", \"page\": 14, \"index\": 45, \"width\": 709, \"height\": 1035}]"
motivation: 现有方法主要聚焦简化场景设置，复杂环境下人-场景交互模仿研究不足，限制了其实际适用性。
method: 提出ComplexMimic框架，通过双流策略从不完美动作捕捉数据中重建多样化人-场景交互。
result: 在复杂环境中实现了兼顾交互成功与物理自然性的多样化HSI重建。
conclusion: 为复杂环境下基于物理的具身智能模仿学习提供了新方法。
---

## Abstract
Physics-based Human-Scene Interaction (HSI) imitation learn-ing is crucial for embodied intelligence as it bridges the gap betweenkinematic 3D motions and real-world dynamics. However, most exist-ing methods focus on simplified scene settings, leaving complex envi-ronments largely unexplored, which limits their applicability in real-world scenarios. In this paper, we focus on HSI mimicry in complexenvironments. Under this complex setting, we observe an inherent trade-off between successfully performing interaction and maintaining natu-ral, physically plausible motions. To address this challenge, we proposeComplexMimic, a framework that reconstructs diverse HSI by inter-preting imperfect MoCap data. First, we introduce a Dual Flow Strat-egy, which learns two complementary experts: an imitation expert foraccurate motion tracking and an interaction expert for collision-awareadaptation in complex scenes. Second, naive multi-expert distillation,which treats all experts equally, often under-samples challenging be-haviors, limiting effective learning. To mitigate this issue, we proposea difficulty-aware distillation strategy that adaptively weights super-vision and prioritizes hard-yet-learnable trajectories guided by failurestatistics and learning progress signals. Extensive experiments on threebenchmark datasets demonstrate that our approach outperforms cur-rent state-of-the-art methods. Our implementation is available at https://github.com/LuPan23/ComplexMimic.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze and summarize the academic paper "ComplexMimic: Human–Scene Interaction Imitation in Complex 3D Environments" in Chinese, following a structured Markdown format with 8 specific points.

Let me carefully read through the paper and extract the key information for each section:

1. **Core problem and motivation**: Physics-based HSI imitation learning in complex environments, addressing the trade-off between motion fidelity and task feasibility.

2. **Methodology**: Two-stage framework:
   - Stage I: Dual Flow Strategy - imitation expert (strict τ≤0.25, scene-free) + interaction expert (relaxed τ≥0.5, with height map)
   - Stage II: Difficulty-Aware Distillation (DAD) - includes regime-specialized teacher routing, multi-teacher distillation via KL divergence, and difficulty-aware sampling (inter-group + intra-group prioritization with learnability filtering)

3. **Experimental setup**:
   - Datasets: TRUMANS, LINGO, GIMO
   - Metrics: Succ, Eg-mpjpe, Empjpe, Eacc, Evel
   - Baselines: DeepMimic, AMP, PHC, MaskedMimic

4. **Resources**: Single NVIDIA 4090 GPU, Isaac Gym simulator

5. **Experiments**: 
   - 3 datasets evaluated
   - Ablation study with 8 components
   - Qualitative comparisons

6. **Conclusions**: 

7. **Strengths**: 

8. **Limitations**: 

Let me organize this into a comprehensive Chinese summary.</think>

# ComplexMimic 论文总结

## 1. 核心问题与整体含义

**研究背景**：基于物理仿真的人-场景交互（Human-Scene Interaction, HSI）模仿学习是具身智能与角色动画的关键方向，旨在弥合运动学三维运动与真实世界物理动力学之间的差距。

**核心问题**：现有 HSI 模仿学习方法（如 MimicBench、PHC、MaskedMimic 等）多聚焦于简化场景（单物体、预定义任务如"坐在椅子上"），无法应对含复杂家具、不规则几何与狭窄通道的真实 3D 环境。

**关键观察——可行性-忠实性权衡（Feasibility–Faithfulness Trade-off）**：
- 训练中的早终止阈值 τ（允许偏离参考运动的最大值）控制策略严格程度。
- **较大 τ**：提高交互成功率（Succ），但降低运动保真度（MPJPE 增大），因策略"放水"以规避碰撞。
- **较小 τ**：提高运动保真，但策略无法探索可行解，导致复杂场景中频繁早期终止失败。

**研究目标**：在复杂 3D 场景下同时实现高交互可行性与高运动保真度。

---

## 2. 方法论

论文提出 **ComplexMimic**，一种两阶段框架。

### 阶段 I：双流策略（Dual Flow Strategy）

训练两个互补的教师专家：

- **模仿专家（Imitation Expert）**：
  - 仿真环境：不加载场景网格
  - 终止阈值：严格（τ ≤ 0.25）
  - 目标：高保真度跟踪参考运动
  - 优化器：PPO（GAE 优势估计）

- **交互专家（Interaction Expert）**：
  - 仿真环境：加载完整场景网格
  - 终止阈值：宽松（τ ≥ 0.5）
  - 输入：除本体状态外，附加 20×20 高度图（采样间隔 8 cm，对齐角色朝向）
  - 目标：碰撞感知的稳健交互

两者均基于 MLP（隐藏层 {2048,1024,1024,512}）的 PPO 策略。

### 阶段 II：难度感知蒸馏（Difficulty-Aware Distillation, DAD）

将两专家能力蒸馏到统一的 Transformer 学生策略（4 层、4 头、隐藏维度 512）。包含三部分：

1. **任务专属教师路由（Regime-Specialized Teacher Routing）**：
   - 用模仿专家在含场景仿真器中评估所有训练动作；
   - 跟踪成功的进入 G_Imitate，其余进入 G_Interact；
   - 蒸馏时按组别选择对应教师（π_Imitate 不依赖场景输入，π_Interact 使用高度图）。

2. **多教师蒸馏目标**（基于 KL 散度的高斯动作分布蒸馏）：
   $$L_{KD}(\theta) = \mathbb{I}[m \in G_{Inter}] \cdot D_{KL}\big(\pi_\theta(\cdot|s_t,hm_t) \| \pi^{(T)}_{Interact}\big) + (1-\mathbb{I}) \cdot D_{KL}\big(\pi_\theta(\cdot|s_t,hm_t) \| \pi^{(T)}_{Imitate}\big)$$
   
   联合优化：$L(\theta) = \lambda_{PPO} L_{PPO} + \lambda_{KD} L_{KD}$，学生仍通过 PPO 在含场景仿真器中在线优化。

3. **难度感知采样（Difficulty-Aware Sampling, DAS）**：
   - **运动级难度分数**：每 K 步评估学生策略，以二值失败指示 f_k(m) 的 EMA 作为 D_k(m) ∈ [0,1]。
   - **组间采样**：按组级难度 softmax 采样：$p_k(c) \propto \exp(\tau_{inter} D_k^{cls}(c))$。
   - **组内优先级**：按 $p_k(m|c) \propto \exp(\tau_{intra} s_k(m))$ 采样，$s_k(m)=D_k(m)$。
   - **可学习性过滤**：用回报改善量 $\Delta R_k(m)$ 的 EMA $I_k(m)$，对长期无改善者施加 $u_k(m)=\exp(-\lambda_u \max(0,\epsilon_u - I_k(m)))$ 的惩罚；最终分数 $s_k(m)=D_k(m)+\log u_k(m)$。
   - 最终采样概率混合少量均匀先验（ε=0.05）以保证覆盖。

---

## 3. 实验设计

### 数据集
| 数据集 | 用途 | 特点 |
|---|---|---|
| **TRUMANS** | 域内训练与测试 | 最大规模、多样化高质 HSI 数据；按 SceneMI 切分为 121 帧序列，10% 测试集 |
| **LINGO** | 跨域泛化 | 未见过的场景配置（文本驱动生成） |
| **GIMO** | 真实场景评估 | 真实扫描网格，含重建噪声和伪影 |

### 评估指标
- **Succ**：成功率（平均关节偏离 >0.5 m 视为失败）
- **Eg-mpjpe**：全局平均关节位置误差（mm）
- **Empjpe**：根部相对平均关节位置误差（mm）
- **Eacc / Evel**：加速度 / 速度误差（mm/frame² 与 mm/frame）

### 对比方法（基线）
- DeepMimic、AMP、PHC、MaskedMimic（均补充同等规模的高度图以公平比较）
- 论文自身消融：Ours w/o DAS

### 主要结果
- **TRUMANS**：Succ 从 0.872 → **0.906**；Eg-mpjpe 从 85.793 → **77.840**（较 PHC 提升 3.90% Succ，9.36% Eg-mpjpe 下降）。
- **LINGO**：Succ 从 0.719 → **0.746**，跨域泛化最强。
- **GIMO**：Succ 从 0.515 → **0.579**，在含噪声的真实扫描场景中亦稳健。

---

## 4. 资源与算力

- **GPU**：单卡 **NVIDIA RTX 4090**。
- **物理仿真**：NVIDIA Isaac Gym（GPU 并行）。
- **控制频率**：策略 30 Hz，仿真 60 Hz。
- **训练时长**：论文未明确给出总训练小时数或样本量级。
- **代码**：开源（github.com/LuPan23/ComplexMimic），但补充材料中可能未提供完整配置。

---

## 5. 实验数量与充分性

论文实验较为充分，可分为：

- **3 个数据集** 评估（域内 + 跨域 + 真实扫描）。
- **8 组消融实验**（TRUMANS）：
  - w/o 模仿专家、w/o 交互专家
  - w/o 组间采样、w/o 组内优先级、w/o 可学习性过滤
  - w/o PPO（纯蒸馏）
  - 随机路由、动作平均（替代路由策略）
- **定量对比**（4 个基线 × 3 个数据集 × 5 个指标）。
- **定性可视化**：典型失败模式（碰撞、抖动、偏离）对比。
- **报告引用 Figure 3** 解释回报改善信号对困难但可学样本的聚焦效果。

**充分性评价**：实验覆盖了核心贡献的各个组件（双流、DAD 子模块、路由策略、PPO 必要性），并在三种典型分布下验证泛化能力。但 LINGO 与 GIMO 的消融结果仅承诺于补充材料，正文中未呈现，对每个数据集上各模块贡献的细粒度比较有限。

---

## 6. 主要结论与发现

1. **复杂场景下 HSI 模仿存在固有的可行性-忠实性权衡**，无法通过单一专家或单一阈值解决。
2. **解耦训练 + 自适应蒸馏** 是有效路径：模仿专家负责运动保真，交互专家负责碰撞规避，二者通过 DAD 融合。
3. **任务专属路由** 显著优于随机路由或动作平均路由，避免了梯度干扰。
4. **难度感知采样** 能高效分配训练预算于"困难但可学"样本，结合可学习性过滤避免长期停滞样本浪费算力。
5. 联合 **PPO + KL 蒸馏** 的目标比纯模仿蒸馏更优（Succ 从 0.830 → 0.906）。
6. 方法在真实扫描场景（GIMO）中亦保持优势，展示了较强的鲁棒性与迁移性。

---

## 7. 优点

- **问题定位新颖**：首次系统处理复杂（密集家具、不规则几何）3D 环境下的物理 HSI 模仿，超越已有简化场景设定。
- **方法论创新**：
  - 双流专家将运动跟踪与场景交互解耦，避免单一策略的多目标冲突。
  - 基于在线失败统计 + 回报改善的难度评分，兼顾静态难度与可学习性。
  - 任务专属路由与组间/组内两级优先级采样，结构清晰、可解释性强。
- **实证充分**：覆盖 3 个数据集、4 个强基线、8 组消融，定量与定性并重。
- **实用性**：方法无需依赖语言指令或场景标注输入，扩展到真实扫描数据时仍稳健。
- **开源可复现**：代码公开。

---

## 8. 不足与局限

- **未涉及机器人操控**：本文聚焦虚拟人形角色（SMPL 平均体型）的物理模仿，并未迁移到真实机器人硬件；与"机器人模仿学习"主题的工程化关联较弱。
- **单 GPU 训练效率受限**：单卡 RTX 4090 训练可能限制可扩展到大数据集或长周期训练，论文未提供训练时长/样本量。
- **依赖 MoCap 数据质量**：方法建立在"解释不完美 MoCap"假设上，但未深入分析 MoCap 噪声/缺失对最终策略鲁棒性的影响。
- **超参数敏感度未充分报告**：τ_inter、τ_intra、λ_u、ε_u 等关键采样温度与阈值均固定为单一取值，未给出敏感性分析。
- **场景表示有限**：高度图采样分辨率固定（20×20, 8 cm），对远距离或垂直复杂几何的感知可能不足。
- **消融覆盖不平衡**：TRUMANS 上消融详尽，但 LINGO 与 GIMO 的消融被推迟到补充材料，主文中跨域结论的归因不够透明。
- **安全与失败处理**：未讨论当策略仍无法完成某些交互时的兜底机制或安全约束。
- **风格/语义控制缺失**：相较 HUMANISE、LINGO 等语言驱动方法，本工作仍需完整参考运动输入，未探索语言/语义条件下的 HSI 模仿。

（完）
