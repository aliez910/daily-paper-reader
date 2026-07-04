---
title: Object-Centric Prompt-Driven Vision-Language-Action Model for Robotic Manipulation
title_zh: 面向机器人操控的以目标对象为核心、提示驱动的视觉-语言-动作模型
authors: "Li, Xiaoqi, Xu, Jingyun, Zhang, Mingxu, Liu, Jiaming, Shen, Yan, Ponomarenko, Iaroslav, Xu, Jiahui, Heng, Liang, Huang, Siyuan, Zhang, Shanghang, Dong, Hao"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Li_Object-Centric_Prompt-Driven_Vision-Language-Action_Model_for_Robotic_Manipulation_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向机器人操控的视觉-语言-动作模型
tldr: "在机器人操控任务中,自然语言指令往往存在歧义,而目标图像或视频又可能过于具体,难以同时兼顾高层规划与底层动作表达。为此,本文提出了一种以目标对象为核心、由多模态提示驱动的视觉-语言-动作模型。该方法在 RGB 图像上叠加简洁的 2D 视觉提示,用于显式表达末端执行器位姿和接触后的运动方向等任务目标。实验表明,所提方法能在多种操控任务中实现更精确、可解释的视觉-动作映射。该工作为复杂操控任务提供了一种兼顾灵活性与精确性的通用解决方案。"
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1705, \"height\": 643, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1629, \"height\": 740, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1627, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1417, \"height\": 747, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1552, \"height\": 592, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 660, \"height\": 390, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1417, \"height\": 747, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 804, \"height\": 272, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-li-object-centric-prompt-driven-vision-language-action-model-for-robotic-manipulation-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 863, \"height\": 263, \"label\": \"Table\"}]"
motivation: "自然语言指令存在歧义,而图像或视频目标又过于具体,需要一种兼顾高层规划与底层动作的提示方式。"
method: "提出一种在 RGB 图像上叠加 2D 视觉提示的 VLA 模型,结合关键帧规划与多模态输入,生成末端执行器位姿和动作方向。"
result: 方法在多种机器人操控任务中实现了更精准、可解释的任务规范与执行效果。
conclusion: 为通用视觉-语言-动作模型在复杂操控场景中的落地提供了一种简洁而有效的提示驱动范式。
---

## Abstract
In robotic manipulation, task goals can be conveyed through various modalities, such as language, goal images, and goal videos. However, natural language can be ambiguous, while images or videos may offer overly detailed specifications. To address these challenges, we propose a novel approach using comprehensive multi-modal prompts that explicitly convey both low-level actions and high-level planning in a simple manner. Specifically, for each key-frame in the task sequence, our method allows for manual or automatic generation of simple and expressive 2D visual prompts overlaid on RGB images. These prompts represent the required task goals, such as the end-effector pose and the desired movement direction after contact. We develop a training strategy that enables the model to interpret these visual-language prompts and predict the corresponding contact poses and movement directions in SE(3) space. Furthermore, by sequentially executing all key-frame steps, the model can complete long-horizon tasks. This approach not only helps the model explicitly understand the task objectives but also enhances its robustness on unseen tasks by providing easily interpretable prompts. We evaluate our method in both simulated and real-world environments, demonstrating its robust manipulation capabilities.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Object-Centric Prompt-Driven Vision-Language-Action Model for Robotic Manipulation" (CrayonRobo). Let me organize my analysis according to the 8 required points.

Let me carefully read through the paper content and extract relevant information:

1. Core problem and motivation: Task goals conveyed through various modalities - language, goal images, goal videos. Language is ambiguous, images/videos too detailed. Need a way that conveys both low-level actions and high-level planning.

2. Methodology: CrayonRobo - uses 2D visual prompts overlaid on RGB images (crayon-style). Four colors:
- Blue: contact point
- Red: end-effector z-axis direction
- Green: end-effector y-axis direction
- Yellow: next moving direction after contact
Training strategy uses progressive input pairs (a)-(d) in Figure 2
Three losses: Text Supervision Loss (L_T), Orthogonal Loss (L_O), Projection Loss (L_P)
Model architecture based on ManipLLM VLA with CLIP visual encoder, LLaMA tokenizer, multi-modal projection, with only adapters and projection module fine-tuned
Inference: automatic (Grounded-DINO + GPT-4) or manual drawing

3. Experiments: SAPIEN simulator with PartNet-Mobility dataset, ~1500 object shapes, 10,000 training samples
Baselines: Flowbot3D, ManipLLM, Implicit3D, RT-Trajectory, AVDC
Real-world: Franka Emika robotic arm with RealSense 415 camera
Tasks: open trashcan, open microwave, lift lid, wipe table, heat toaster

4. Resources: 6-8 hours to collect 10,000 training samples. No specific GPU info mentioned.

5. Experiments: Multiple categories seen and unseen, ablation study on different prompt types, noise tolerance analysis, real-world experiments with 5 trials per task.

6. Conclusions: Comprehensive multi-modal prompts that explicitly convey both low-level actions and high-level planning. Model-interpretable prompts show promising performance on seen and unseen tasks.

7. Highlights: 
- Combines visual and language prompts (multi-modal)
- Progressive training strategy
- Handles both seen and unseen tasks
- Real-world deployment without fine-tuning
- Tolerance to noisy inputs
- Can work without prompts after fine-tuning

8. Limitations:
- Cannot directly avoid obstacles (need motion planner)
- Limited real-world task diversity
- 2D direction may be challenging if perpendicular to camera
- Manual drawing may have user variability
- No specific information on GPU compute

Let me write this up in Chinese with proper Markdown formatting.
</think>
# 论文总结：面向机器人操控的以目标对象为核心、提示驱动的 VLA 模型（CrayonRobo）

## 1. 核心问题与研究动机

- **问题背景**：在机器人操控任务中，目标指令可以通过多种模态传达：自然语言、目标图像、目标视频等。然而这些模态各有缺陷：
  - **自然语言**：存在歧义，要么过于简短难以理解任务，要么过于冗长导致模型难以遵循。
  - **目标图像**：包含大量与任务无关的冗余信息（背景、非交互物体）。
  - **目标视频**：人类示视频编码成本高；生成视频质量受限。
  - **现有视觉提示方法**（如 RT-Sketch、RT-Trajectory）：要么仅描绘终态、忽略关键中间帧；要么只给出位置轨迹、缺失方向信息，且长轨迹会因关键帧重叠造成混乱。
- **核心研究问题**：能否找到一种**精确、无冗余**地传达目标与末端执行器动作的方式？
- **研究动机**：关键帧（key-frame）代表了任务执行过程中末端执行器的重要或瓶颈步骤，利用关键帧序列可以同时承载**高层规划**与**底层动作**信息，因此提出"以目标对象为核心、由多模态提示驱动"的 VLA 模型。

## 2. 方法论

### 2.1 核心思想

- 提出 **CrayonRobo** 方法：在 RGB 图像上叠加 4 种颜色的"蜡笔风格"2D 视觉提示，分别表示：
  - **蓝色**：接触点（contact point）
  - **红色**：末端执行器 z 轴方向
  - **绿色**：末端执行器 y 轴方向
  - **黄色**：接触后下一时刻运动方向
- 同时使用语言提示消除视觉提示可能造成的歧义（提供 2D 接触点坐标与各方向单位向量）。
- 模型输入：图像 $I \in \mathbb{R}^{H\times W\times 3}$ + 语言提示 $P$，输出 3D 接触位姿 $a_P^0$ 和运动方向 $a_M^0$（SE(3) 空间）。
- 长时任务通过**关键帧序列**串联完成：每个关键帧对应一个子目标，连续执行所有关键帧步骤即可完成整体任务。

### 2.2 数据采集（仿真）

- 基于 SAPIEN 仿真器 + PartNet-Mobility 数据集，使用基于规则的方法在仿真中获取接触位姿、3D 方向真值。
- 3D 接触点反投影到 2D 图像得到 $a_p^0=(x,y)$，z/y 轴方向同样通过 3D→2D 投影后用线段连接得到红绿线，移动方向同理得到黄线。
- 共采集约 **10,000** 个训练样本，耗时 **6–8 小时**。

### 2.3 模型架构

- 沿用开源 VLA 模型（ManipLLM）骨干：CLIP 视觉编码器 + LLaMA 分词器 + 多模态投影模块。
- **参数高效微调**：冻结主参数，仅微调 LLaMA 注入的 **LoRA 适配器** 与多模态投影模块。
- 将位姿预测建模为**语言建模任务**，以文本形式直接输出 3D 方向。

### 2.4 训练策略（渐进式输入对）

设计 (a)→(b)→(c)→(d) 四种逐渐丰富的输入对：

| 级别 | 输入内容 |
|------|----------|
| (a) | 仅接触点（2D 位置） |
| (b) | 接触点 + z 轴方向 |
| (c) | 接触点 + z/y 轴方向 |
| (d) | 接触点 + z/y 轴方向 + 运动方向 |

使模型逐步学习各提示分量的物理含义。

### 2.5 损失函数

总目标：$L = \lambda_1 L_T + \lambda_2 L_O + \lambda_3 L_P$

- **$L_T$（文本监督损失）**：将归一化 3D 方向向量离散化为 100 个 bin（[-50, 50]，间隔 0.02），使用交叉熵损失监督输出文本。
- **$L_O$（正交损失）**：从模型输出中提取 $a_Z^0$ 与 $a_Y^0$，用 Gram-Schmidt 正交损失保证二者几何正交关系。
- **$L_P$（投影损失）**：将预测的 3D 方向反投影回 2D，与输入的 2D 方向提示做余弦相似度监督：
  
  $$L_P = \left(1 - \frac{a_z^* \cdot a_z^0}{\|a_z^*\|\|a_z^0\|}\right) + \left(1 - \frac{a_y^* \cdot a_y^0}{\|a_y^*\|\|a_y^0\|}\right) + \left(1 - \frac{a_m^* \cdot a_m^0}{\|a_m^*\|\|a_m^0\|}\right)$$

> 注意 $L_P$ 的具体项根据输入提示动态调整（缺失的提示不参与该项监督）。

### 2.6 推理与交互

- **自动生成提示**：使用 Grounded-DINO 获得物体边界框中心作为蓝色接触点 → 均匀采样 32 条候选方向 → GPT-4 从候选中挑选 z/y/运动方向。
- **手动绘制提示**：用户直接用画笔在图像上绘制四种颜色的提示。
- **动作执行**：2D 接触点利用深度图和相机参数反投影为 3D 点；$a_Z^0$ 与 $a_Y^0$ 共同决定旋转矩阵（初始接触姿态）；若提供 $a_M^0$ 则按其方向继续运动。
- **关键帧序列串联**：依次执行各关键帧子目标，完成长时任务。
- **特殊原语处理**：pick/push/pull 需要运动方向；place/move 不需要；rotate 通过两个时间帧体现（位置不变、末端旋转）。

## 3. 实验设计

### 3.1 数据集与场景

- **仿真环境**：SAPIEN 仿真器 + PartNet-Mobility 数据集，约 **1,500** 个物体形状，多视角随机化，使用飞行式 Franka Panda 夹爪。
- **训练样本**：约 10,000 个（耗时 6–8 小时）。
- **真实环境**：Franka Emika 机械臂（默认平行夹爪）+ Intel RealSense 415 相机（提供 RGB 与深度图）。
- **真实任务**：开垃圾桶、开微波炉、抬起盖子、擦桌子、加热烤面包机（部分含多步）。

### 3.2 评估指标

- 操控成功率 = 成功样本数 / 总测试样本数（通过物体部件移动距离阈值判定）。

### 3.3 对比方法

| 类型 | 方法 | 说明 |
|------|------|------|
| 纯视觉 | Flowbot3D | 点云上预测 flow，取最大 flow 点作为交互点 |
| 语言条件 | ManipLLM | 文本+初始图像，预测末端位姿 |
| 3D 视觉目标 | Implicit3D | transporter 检测关键点（吸盘） |
| 视觉提示 | RT-Trajectory | 复现方法，画末端轨迹 |
| 视频目标 | AVDC | 视频生成策略（用 Gemini-1.5 评估任务成功率约 10.2%） |
| **本文** | Ours(s) / Ours(f) | 蜡笔提示 VLA（s：吸盘；f：平行夹爪） |

### 3.4 消融研究

- 提示类型的渐进消融（Ex1–Ex3 + Full）：仅位置 → +z → +y → +运动方向。
- 视觉 vs 语言提示的对比（Ours w/o v.）。
- 各损失函数的消融（在附录 5）。
- 提示噪声鲁棒性分析（10%–40% 方向噪声）。

## 4. 资源与算力

- **训练数据采集**：6–8 小时（在仿真器中），共约 10,000 样本。
- **真实实验**：在工作站上使用内置图像编辑器绘制提示，单任务 5 次试验，每次更换相机视角与物体初始位姿。
- **GPU 型号与数量、训练总时长**：**论文未明确说明**。仅在附录中可能有间接信息，正文未见具体算力配置。

## 5. 实验数量与充分性

- **仿真对比实验**：覆盖 16 类任务（seen）+ 16 类任务（unseen），分 5 种基线方法对比，指标充分。
- **消融实验**：4 组（提示组合）+ 噪声鲁棒性曲线（4 档噪声）+ 视觉/语言提示对比 + 损失消融（在附录）。
- **真实实验**：5 个任务（含 2 个多步），每任务 5 次试验，分手动（dra.）与自动（auto.）两套；同时探索"无提示"微调（w/o P.）。
- **公平性**：
  - 所有方法采用相同 train/test 划分。
  - 但 RT-Trajectory 论文提交时未开源，作者自行复现，可能存在实现差异。
  - AVDC 基于生成视频评估，且其生成成功率仅 10.2%，对比并不完全公平。
  - Flowbot3D/ManipLLM/Implicit3D 使用吸盘，与本文的"夹爪版"分开比较，避免了直接冲突。
- **总体评价**：实验较充分，但真实世界任务多样性有限（仅 5 类），缺乏大规模用户研究。

## 6. 主要结论与发现

- **CrayonRobo 在仿真中大幅优于现有基线**：Ours(s) 在 seen/unseen 任务上均超过 Flowbot3D、ManipLLM、Implicit3D、RT-Trajectory、AVDC。
- **提示越丰富，预测越准**：从 Ex1（仅位置）→ Full（全 4 类提示）性能单调提升（0.42/0.37 → 0.74/0.72）。
- **多模态提示优于单一模态**：去掉视觉提示（Ours w/o v.）性能从 0.74/0.72 下降至 0.69/0.68。
- **鲁棒性强**：在 10%–20% 方向噪声下性能几乎不下降；30%–40% 噪声下虽有下降但仍可执行。
- **零样本真实世界能力**：无需 sim-to-real 微调即可在真实 Franka 上完成未见任务；长时任务成功率与单步任务接近。
- **可"无提示"复用**：用首次成功执行的关键帧和预测位姿做 20 epoch 微调后，模型可独立执行（开微波 5/10、擦桌子 6/10）。

## 7. 优点

- **多模态提示设计新颖**：4 色蜡笔提示同时承载位置、姿态、运动方向三类底层动作信息；结合关键帧序列承载高层规划。
- **训练策略渐进式**：通过 (a)→(d) 递进输入对，使模型深入理解每个提示分量的物理含义，避免一次性输入所有提示带来的学习难度。
- **几何一致性显式建模**：正交损失 + 投影损失双重约束，确保 3D 预测与 2D 提示几何一致。
- **容错性强**：对位置噪声（GroundingDINO 中心 ≠ 真实接触点）、方向噪声（10%–20%）均能稳定工作。
- **用户友好**：同时支持手动绘制和自动生成两种方式，使用门槛低。
- **架构高效**：仅微调 LoRA 适配器和投影模块，保留预训练知识，训练效率高。
- **可解释性高**：提示本身即为"模型可理解"的语言，便于调试和纠错。
- **长时任务可分解**：将复杂任务拆解为关键帧序列并优化每步成功率，整体成功率有保障。

## 8. 不足与局限

- **避障能力缺失**：作者明确指出方法本身**无法直接避障**，需借助 curobo 等外部运动规划库。
- **2D 投影歧义**：当方向向量垂直于相机时，2D 表示困难，需添加轻微噪声以提升可见性。
- **真实任务种类少**：仅 5 类真实任务，每类 5 次试验，覆盖有限，统计显著性偏弱。
- **手工绘制易引入用户差异**：不同用户绘制的提示在位置、长度、方向上可能存在主观差异，缺乏用户研究。
- **RT-Trajectory 比较可能不公平**：作者自行复现，未使用官方实现细节。
- **AVDC 评估不严谨**：仅基于生成视频质量评估下游策略，并非端到端执行成功率对比。
- **未见硬件算力细节**：训练时长、GPU 型号/数量、显存占用等关键信息缺失，难以评估计算成本与可复现性。
- **手动 vs 自动对比未深入**：自动方式使用 GroundingDINO + GPT-4，依赖大模型 API，部署成本与延迟未讨论。
- **缺少失败案例的系统分析**（仅在附录 6 简略提及）：未定量统计失败原因分布。

（完）
