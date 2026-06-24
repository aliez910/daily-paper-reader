---
title: Continuous Vision-Language-Action Co-Learning with Semantic-Physical Alignment for Behavioral Cloning
title_zh: 面向行为克隆的连续视觉-语言-动作协同学习与语义-物理对齐
authors: "Xiuxiu Qi, Yu Yang, Jiannong Cao, Luyao Bai, Chongshan Fan, Chengtai Cao, Hongpeng Wang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39677/43638"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向行为克隆的VLA协同学习与语义-物理对齐
tldr: 行为克隆在语言条件操作中面临复合误差问题。本文提出CCoL框架，通过连续视觉-语言-动作协同学习与语义-物理对齐，减少动作克隆的不连续性和语义偏差。实验表明该方法有效提升了克隆精度和任务成功率，为行为克隆在复杂操纵中的应用提供了新方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1724, \"height\": 739, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 860, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 864, \"height\": 383, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 592, \"height\": 312, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 591, \"height\": 173, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 844, \"height\": 365, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39677/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 862, \"height\": 444, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39677/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 486, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39677/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 862, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39677/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 880, \"height\": 409, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39677/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1779, \"height\": 499, \"label\": \"Table\"}]"
motivation: 解决行为克隆中的复合误差和语义-物理不对齐问题。
method: 提出连续VLA协同学习框架，实现语义-物理对齐。
result: 提升了行为克隆精度和任务成功率。
conclusion: 提出了一种VLA协同学习方法提升行为克隆性能。
---

## Abstract
Language-Conditioned Manipulation (LCM) facilitates human-robot interaction via Behavioral Cloning (BC), which learns control policies from human demonstrations and serves as a cornerstone of embodied AI. Overcoming compounding errors in sequential action decisions remains a central challenge to improving BC performance. Existing approaches mitigate compounding errors through data augmentation, expressive representation, or temporal abstraction. However, they suffer from physical discontinuities and semantic-physical misalignment, leading to inaccurate action cloning and intermittent execution. In this paper, we present Continuous vision-language-action Co-Learning with Semantic-Physical Alignment (CCoL), a novel BC framework that ensures temporally consistent execution and fine-grained semantic grounding. It generates robust and smooth action execution trajectories through continuous co-learning across vision, language, and proprioceptive inputs (i.e., robot internal states). Meanwhile, we anchor language semantics to visuomotor representations by a bidirectional cross-attention to learn contextual information for action generation, successfully overcoming the problem of semantic-physical misalignment. Extensive experiments show that CCoL achieves an average 8.0% relative improvement across three simulation suites, with up to 19.2% relative gain in human-demonstrated bimanual insertion tasks. Real-world tests on a 7-DoF robot further confirm CCoL’s generalization under unseen and noisy object states.

---

## 论文详细总结（自动生成）

# 论文中文详细总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **研究领域**：语言条件操纵（Language-Conditioned Manipulation, LCM）与行为克隆（Behavioral Cloning, BC）。
- **核心问题**：行为克隆在**长时序决策**中容易产生**复合误差**，并且现有方法（如数据增强、时间抽象等）存在**物理不连续性**（动作跳跃、抖动）和**语义-物理未对齐**（语言指令与视觉-动作表征静态融合，无法随任务阶段动态调整），导致动作克隆不准确、执行不连贯。
- **研究动机**：提出一种能够同时保证**时序一致执行**和**细粒度语义对齐**的BC框架，从而缓解复合误差，提升复杂操作任务的成功率与鲁棒性。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式与算法流程

- **整体框架**：CCoL（Continuous Vision-Language-Action Co-Learning with Semantic-Physical Alignment），包含两大核心模块：
  - **多模态连续协同学习（MCC）**：利用**神经常微分方程（Neural ODE）**对本体感觉嵌入进行连续时间建模，生成平滑的潜在轨迹，替代传统离散分步预测，消除动作不连续。
  - **跨模态语义-物理对齐（CSA）**：通过**双向交叉注意力机制**，在每一步动态地将语言语义锚定到视觉和运动表征上，实现语义到物理的对应。
- **关键技术细节**：
  - **上下文感知表示学习**：
    - 视觉编码器：ViT → 空间特征 \(x_t\)
    - 文本编码器：RoBERTa → 上下文嵌入 \(\hat{l}_t\)
    - 本体感觉编码器：CVAE + Transformer/TCN → 嵌入 \(e_t\)
  - **MCC**：
    - CVAE 预测初始潜在状态 \(z_0\) 的均值和方差；
    - Neural ODE 求解初始值问题：\(z(t_\delta) = z_0 + \int_0^{t_\delta} f(z(t),t;\psi) dt\)，输出连续潜在轨迹 \(Z_t\)；
    - 将视觉、语言、本体感觉特征投影到共享嵌入空间 \(\tilde{x}_t, \tilde{l}_t, \tilde{Z}_t\)。
  - **CSA**：
    - 设计多头双向交叉注意力：计算语言与视觉-运动上下文之间的注意力分数 \(F_t^{(i)}(\tilde{l}_t, X_t)\) 和 \(F_t^{(i)}(X_t, \tilde{l}_t)\)；
    - 融合得到特征 \(\tilde{F}_t\)，并结合位置编码得到最终多模态表示 \(\xi_t\)。
  - **上下文动作生成**：利用目标条件解码器（带残差连接、层归一化、Dropout）预测未来 \(k\) 步动作 \(a'_{t:t+k}\)。
  - **损失函数**：
    - 行为克隆损失 \(\mathcal{L}_{BC} = \mathcal{L}_{recon} + \mathcal{L}_{KL}\)（CVAE变分下界）
    - 不连续惩罚 \(\mathcal{E}_{disc}\)（强制潜在状态的导数与Neural ODE预测一致）
    - 总损失 \(\mathcal{L} = \frac{1}{N}\sum (\mathcal{L}_{BC} + \mathcal{E}_{disc})\)

## 3. 实验设计：数据集/场景、基准与对比方法

- **模拟环境**：
  - **Aloha MuJoCo**：双人协作任务（方块传递、双人插入），包含脚本和人类演示数据。
  - **RLBench**：多场景任务（LampOn, GrillMeat, Phone, OpenBottle等）。
  - **Franka Kitchen**：多阶段长时域任务（拧旋钮、开门、开微波炉等）。
- **对比方法**（baselines）：
  - 时序建模：BCCNN, RT-1, BeT, VINN
  - 时序抽象/动作分块：ACT, AWE
  - 扩散策略：DP, DIC, HDP, 3DDiff
  - 表征增强：R3M, Voltron, MPI
- **评价指标**：成功率（%），定义明确并保持与以往工作一致的设置。

## 4. 资源与算力

- 论文明确提到：**单块RTX 4090 GPU**，训练时长约**5.3小时**。
- 推理每动作序列平均**0.015秒**（±0.003秒），约**67 Hz**策略频率，满足实时性要求。
- 模型参数量根据骨干网络不同（ViT-S 22M, ViT-B 86M），训练时未提及分布式并行，总体算力需求适中。

## 5. 实验数量与充分性

- **模拟实验**：包含3个不同模拟套件、多个子任务（表1-3），与9个以上baseline对比。
- **消融实验**：表4详细消融了MCC、CSA、不连续惩罚、注意力替换、TCN替换等关键组件，验证各模块贡献。
- **轨迹平滑度分析**：计算速度和加速度的标准差，显示CCoL比无MCC版本分别降低30.8%和32.7%。
- **超参数分析**：考察Neural ODE求解器时间步长的影响（图5），结论合理。
- **定性分析**：展示CSA驱动的注意力转移（图4），证明语义锚定的阶段性。
- **真实世界实验**：在Franka Emika Panda 7-DoF机器人上执行3种操作任务（抬笔、滑方块、放置方块），每种15次试验，报告成功率和4类失败率（图6）。
- **充分性评价**：实验覆盖多任务、多环境、多基线，消融完整，结合模拟和实物，设计较为充分和客观。但每个真实任务仅有15次试次，统计效力略有限；模拟中未专门针对未见物体类别或极端干扰进行系统测试。

## 6. 论文的主要结论与发现

- CCoL在三个模拟套件上平均相对改进**8.0%**，在人演示双人插入任务上相对提升**19.2%**。
- MCC和CSA均对性能提升有显著贡献（消融实验中分别下降15%和9%），不连续惩罚进一步改善时序平滑性。
- 轨迹平滑度分析证实Neural ODE有效降低高频抖动和异常加减速。
- 真实世界中CCoL表现出较强的泛化能力（成功率最高达86.7%），但失败主要源于定位、接触、运动学适应和尺寸感知误差。
- 模型训练效率高（5.3h/RTX4090），推理速度快（约67Hz），具有实际部署潜力。

## 7. 优点

- **方法创新性**：首次将Neural ODE与双向交叉注意力系统性结合用于行为克隆，同时解决物理不连续和语义-物理未对齐。
- **实验全面**：覆盖多个模拟环境、多种baselines、详细的消融、实物验证，支持结论的可靠性。
- **效果显著**：特别是在复杂双人协同和长时域任务上提升幅度大，且训练/推理资源需求合理。
- **可解释性**：提供注意力热图（图4），直观展示语言语义到视觉区域的动态映射。

## 8. 不足与局限

- **任务范围**：仅在特定设定（桌面操作、有限物体类型）上验证，未见与LLM或基础模型集成，开集泛化能力未评估。
- **实验统计**：真实世界每个条件仅15次试验，未提供置信区间，可能受随机波动影响。
- **失败分析**：论文虽报告了四类失败率（定位、接触、运动学、尺寸），但未深入分析失败占比的方差和根本原因。
- **环境依赖**：MCC依赖Neural ODE求解，对于非常快或高度不连续的动作可能仍有限制；求解器步长选择（2.0）在文中表现最佳，但未讨论其通用性。
- **计算鲁棒性**：虽然在RTX4090上训练可行，但若扩展到更大规模（如10M+演示）仍可能需要更多算力，文中未分析扩展性。

（完）
