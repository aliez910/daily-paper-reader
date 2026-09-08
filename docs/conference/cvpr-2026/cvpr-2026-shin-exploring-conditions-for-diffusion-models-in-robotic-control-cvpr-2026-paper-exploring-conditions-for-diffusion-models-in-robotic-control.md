---
title: Exploring Conditions for Diffusion Models in Robotic Control
title_zh: 探索扩散模型在机器人控制中的条件机制
authors: "Shin, Heeseong, Heo, Byeongho, Han, Dongyoon, Kim, Seungryong, Kim, Taekyung"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Shin_Exploring_Conditions_for_Diffusion_Models_in_Robotic_Control_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 利用扩散模型为模仿学习控制提供任务自适应视觉表征
tldr: 本文针对模仿学习中冻结的预训练视觉表征缺乏任务自适应性的问题，探索利用文本到图像扩散模型为机器人控制提供表征。方法分析了扩散模型训练数据与机器人环境间的领域差距，提出ORCA框架以任务相关动态视觉条件驱动表征生成。该工作提升了模仿学习在复杂机器人控制中的视觉编码质量。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1786, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1779, \"height\": 513, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1772, \"height\": 983, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1415, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 866, \"height\": 355, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 848, \"height\": 838, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 873, \"height\": 429, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1812, \"height\": 356, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 884, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 871, \"height\": 239, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-shin-exploring-conditions-for-diffusion-models-in-robotic-control-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 869, \"height\": 347, \"label\": \"Table\"}]"
motivation: 预训练视觉表征在策略学习中保持冻结，难以提供任务自适应信息。
method: 提出ORCA框架，利用扩散模型以动态视觉条件生成任务自适应表征。
result: ORCA在多种机器人控制任务中显著优于朴素的文本条件策略。
conclusion: 为扩散模型在模仿学习视觉表征中的应用提供了有效的条件化方法。
---

## Abstract
While pre-trained visual representations have significantly advanced imitation learning, they are often task-agnostic as they remain frozen during policy learning. In this work, we explore leveraging pre-trained text-to-image diffusion models to obtain task-adaptive visual representations for robotic control, without fine-tuning the model itself. However, we find that naively applying textual conditions--a successful strategy in other vision domains--yields minimal or even negative gains in control tasks. We attribute this to the domain gap between the diffusion model's training data and robotic control environments, leading us to argue for conditions that consider the specific, dynamic visual information required for control. To this end, we propose ORCA, which introduces learnable task prompts that adapt to the control environment and visual prompts that capture fine-grained, frame-specific details. Through facilitating task-adaptive representations with our newly devised conditions, our approach achieves state-of-the-art performance on various robotic control benchmarks, significantly surpassing prior methods.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper "Exploring Conditions for Diffusion Models in Robotic Control" (ORCA) following a specific structure. Let me carefully analyze the paper content and organize my response.

The paper is about using text-to-image diffusion models for robotic control, specifically addressing the limitation that pre-trained visual representations are typically frozen and task-agnostic. They propose ORCA which uses learnable task and visual prompts to provide frame-specific conditioning.

Let me organize my response according to the 8 required points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental quantity and sufficiency
6. Main conclusions
7. Strengths
8. Limitations

Let me write this in detailed Chinese with proper Markdown formatting.</think>

# 论文总结：探索扩散模型在机器人控制中的条件机制（ORCA）

## 1. 核心问题与研究动机

- **核心问题**：在基于模仿学习的机器人控制中，预训练视觉表征通常在策略学习阶段保持**冻结**，导致其具有**任务无关（task-agnostic）**特性，难以针对不同控制任务自适应调整。
- **研究背景**：
  - 文本到图像扩散模型（如 Stable Diffusion）在视觉感知任务（语义分割、深度估计等）中已被证明可通过**文本条件（text conditions）**显著提升性能。
  - 然而，将扩散模型应用于机器人控制时，**直接迁移文本条件策略效果不佳**，甚至出现负增益。
- **关键发现**：扩散模型的训练数据（网络图像）与机器人仿真环境之间存在显著**领域差距（domain gap）**，文本词元难以正确对应到控制图像中的关键区域（如机械臂末端、目标物体等）。
- **论文目标**：在不微调扩散模型的前提下，探索如何为机器人控制任务设计**有效的条件机制**，实现**任务自适应视觉表征**。

## 2. 方法论：ORCA 框架

### 2.1 核心思想
- 提出 **ORCA**（a framework for conditioning diffusion models in robotic control），通过**可学习的任务提示（task prompts）和视觉提示（visual prompts）**对扩散模型进行条件化。
- 强调两点：(1) 条件应**任务对齐（task-grounded）**；(2) 条件应**帧敏感（frame-sensitive）**，以捕捉动态视频流中每帧的细节。

### 2.2 技术细节

**（1）任务提示（Task Prompts）**
- 用一组**可学习的词元（learnable tokens）**替代传统文本提示，所有观测共享同一组任务提示。
- 通过行为克隆损失在下游任务中端到端学习，隐式学习关注任务关键区域（如机器人末端、目标物体）。

**（2）视觉提示（Visual Prompts）**
- 使用预训练 **DINOv2** 作为视觉编码器 $\mathcal{E}_V$，提取**密集（dense）局部特征**而非全局特征。
- 通过一个小型卷积层投影后，与任务提示**拼接**输入文本编码器 $\tau_\theta$，形成条件 $C^*$。
- 视觉提示捕捉每帧细粒度、动态变化的信息。

**（3）特征选取**
- 从 Stable Diffusion v1.5 的 U-Net 中提取 **down-sampling 块 + bottleneck 块** 的中间特征（具体为 down 1、down 2、down 3 和 mid 块的拼接）。
- 设置 timestep $t=0$，任务提示长度 $l_t=4$，视觉提示长度 $l_v=16$。

**（4）训练目标（行为克隆损失）**

$$
\mathcal{L}_{BC}(\phi, p) = \sum_i \sum_o \| \pi_\phi(\epsilon_\theta(z_t, t; C^*)) - a_i^o \|
$$

其中：
- $z_t = \sqrt{\bar{\alpha}_t} E(I_i^o) + \sqrt{1-\bar{\alpha}_t}\epsilon$
- $C^* = \tau_\theta(p_t; p_v)$
- 同时优化策略网络 $\pi_\phi$、任务提示 $p_t$ 和视觉提示 $p_v$
- **冻结** Stable Diffusion 主体，仅训练提示参数（约 **10.6M**）

### 2.3 算法流程
1. 输入观测图像 $I$，经 VQGAN 编码为 $z_0$，再加噪得 $z_t$。
2. 视觉编码器 $\mathcal{E}_V$ 提取图像特征 → 卷积投影 → 视觉提示 $p_v$。
3. 可学习任务提示 $p_t$ 与 $p_v$ 拼接，经文本编码器 $\tau_\theta$ 生成条件 $C^*$。
4. U-Net 在条件 $C^*$ 下提取中间特征 $f$。
5. 压缩层 + 策略网络 $\pi_\phi$ 输出动作。

## 3. 实验设计

### 3.1 评测基准（12 个任务）
- **DeepMind Control (DMC)**：5 个任务（Walker-stand、Walker-walk、Reacher-easy、Cheetah-run、Finger-spin），评价指标为归一化分数。
- **MetaWorld**：5 个任务（Assembly、Bin-picking、Button-press、Drawer-open、Hammer），评价指标为最佳成功率。
- **Adroit**：2 个任务（Pen、Relocate，28-DoF 灵巧手），评价指标为最佳成功率。

### 3.2 演示数据量
- Adroit：每个任务 **2** 条演示
- DMC：每个任务 **5** 条演示
- MetaWorld：每个任务 **5** 条演示
- 训练 100 epochs，每 10 epochs 在线评估一次。

### 3.3 对比方法
- **任务无关基线**：
  - **CLIP**（ViT-L/16）
  - **VC-1**（ViT-L/16）
  - **SCR**（Stable Diffusion 1.5 + null 条件）
- **任务自适应基线（扩散模型条件化）**：
  - **Text (Simple)**：仅用任务名作为文本提示
  - **Text (Caption)**：用 Gemini 2.5 生成的详细描述作为文本提示
  - **CoOp**：可学习前缀词元 + 任务名
  - **TADP**：在 Caption 基础上加入通过 Textual Inversion 学习的风格词 $S^*$
- **本文方法**：**ORCA**（任务提示 + 视觉提示）

## 4. 资源与算力

- **论文中未明确说明**所使用的 GPU 型号、数量或训练时长。
- 仅可推断：
  - 仅训练提示参数（**约 10.6M**）和压缩层，远少于全模型微调（VC-1 约 302.3M，SCR 约 346.7M）。
  - 实验涉及 12 个任务 × 3 个 seed × 100 epochs，估计训练开销适中（扩散模型推理为主要瓶颈）。
  - 推理时依赖 Stable Diffusion v1.5 U-Net 前向传播。

## 5. 实验数量与充分性

### 5.1 实验规模
- **主实验**：3 个基准 × 12 个任务 × 3 个随机种子 = 约 36 组数值结果。
- **消融实验**：
  - 组件消融（任务提示 / 视觉提示）：Table 4，4 种组合。
  - 层选择消融：Table 5，8 种层配置。
  - 微调对比：Table 3，对比 VC-1 和 SCR 的微调结果。
- **可视化分析**：
  - 跨任务（Button-press、Cheetah-run）的交叉注意力图：Figure 3。
  - 不同帧（Frame 1/15/30/45）的任务提示 vs 视觉提示对比：Figure 6。
  - 案例研究：定性分析条件效果。

### 5.2 充分性评价
- **优点**：
  - 覆盖了视觉模仿学习的三大主流基准，任务多样（连续控制、操作、灵巧操作）。
  - 与多种代表性基线对比，包含任务无关与任务自适应两大类。
  - 通过交叉注意力可视化提供了**直观的可解释性证据**。
- **不足**：
  - 每个任务仅 2–5 条演示，规模较小，可能限制泛化性讨论。
  - 缺乏真实世界机器人实验，所有结果来自仿真。
  - 仅做了与扩散模型相关的对照，未与最新基于视频预训练（如 R3M、VIP、MVP 等）的扩展方法做深入对比。

## 6. 主要结论与发现

- **文本条件在机器人控制中效果有限**：基于 Gemini 2.5 生成的详细描述作为条件，在某些任务（如 Button-press）上有提升，但在 Cheetah-run 等任务上反而下降，因为扩散模型无法正确将文本词与图像区域对应。
- **冻结预训练表征存在任务无关性问题**：没有任何单一任务无关表征能在所有任务中表现最优。
- **任务提示 + 视觉提示的组合是关键**：两者互补——任务提示关注稳定的任务目标区域，视觉提示捕捉动态帧级细节。
- **ORCA 在所有 12 个任务上达到 SOTA**：
  - DMC 平均得分 74.3（vs SCR 68.3、VC-1 53.1、CLIP 59.5）
  - MetaWorld 平均成功率 95.2%（vs SCR 90.4%）
  - Adroit 平均成功率 65.3%（vs SCR 58.0%）
- **微调扩散模型不可行**：在有限演示数据上对 VC-1、SCR 进行微调会导致严重过拟合（成功率下降 80%+）。
- **U-Net 早期层特征更适合控制任务**：down-sampling + bottleneck 特征组合优于 up-sampling 特征。

## 7. 论文亮点

- **问题视角新颖**：首次系统研究扩散模型在机器人控制中的**条件设计**，揭示了"文本条件 → 视觉任务"成功经验无法直接迁移的根本原因。
- **方法简洁有效**：仅引入可学习提示（约 10.6M 参数），无需微调扩散模型，避免了对每个任务存储独立模型副本。
- **可视化证据充分**：通过交叉注意力图直接展示了文本条件失败的具体机制（错误的词-区域对应），以及 ORCA 的任务/视觉提示如何正确关注关键区域。
- **实验全面**：覆盖三大基准 12 个任务，消融实验涵盖组件、层选择，并与多种基线公平比较。
- **明确的失败模式分析**：指出完整微调（full fine-tuning）的灾难性后果，论证了"冻结 + 条件化"路线的合理性。

## 8. 不足与局限

- **演示数据量极少**：每个任务仅 2–5 条演示，难以评估方法在**数据更充足场景**下的扩展性。
- **缺乏真实世界实验**：所有实验均在仿真环境（MuJoCo）中完成，迁移到真实机器人平台的有效性未经验证。
- **视觉编码器选择单一**：视觉提示部分固定使用 DINOv2，未对其他视觉编码器（如 DINOv1、CLIP-Vision、EVA-CLIP 等）做对比研究。
- **任务提示初始化敏感性未讨论**：可学习提示的随机初始化策略可能影响收敛速度和最终性能，论文缺乏相关消融。
- **跨任务泛化能力未探索**：不同任务需要训练独立的提示集，缺乏对**跨任务共享提示**或**零样本迁移**的讨论。
- **依赖 U-Net 推理开销**：尽管仅训练小参数，但推理时仍需运行完整扩散 U-Net 前向传播，实时性受限（论文未报告推理延迟）。
- **样本效率未与传统表征学习方法对比**：未明确报告 ORCA 相比 R3M、VIP 等方法的样本效率差异。
- **领域差距结论的可推广性**：仅基于 Gemini 2.5 一种 VLM 生成描述，未考虑使用更强 VLM 或人工设计提示词的情况。

（完）
