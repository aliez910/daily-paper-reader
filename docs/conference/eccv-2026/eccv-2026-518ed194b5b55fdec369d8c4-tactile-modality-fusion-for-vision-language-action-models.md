---
title: Tactile Modality Fusion for Vision-Language-Action Models
title_zh: TacFiLM：面向视觉-语言-动作模型的触觉模态融合
authors: "Charlotte Morissette, Amin Abyaneh, Wei-Di Chang, Anas Houssaini, David Meger, Hsiu-Chin Lin, Jonathan Tremblay, Gregory Dudek"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/14918.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 面向通用VLA操纵模型的轻量触觉融合
tldr: 现有视觉-语言-动作模型主要依赖视觉感知，难以捕捉接触丰富操纵中的接触力、摩擦与顺应性。本文提出轻量模态融合方法TacFiLM，将视觉-触觉信号融入VLA策略，避免了大规模重训或token拼接带来的计算负担。该方法使通用VLA模型能够利用触觉线索，在接触密集型复杂操纵任务中表现更可靠。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1352, \"height\": 1184}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 605, \"height\": 605}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 605, \"height\": 605}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 605, \"height\": 605}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 605, \"height\": 605}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 400, \"height\": 400}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-007.webp\", \"caption\": \"\", \"page\": 6, \"index\": 7, \"width\": 605, \"height\": 758}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-008.webp\", \"caption\": \"\", \"page\": 8, \"index\": 8, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-009.webp\", \"caption\": \"\", \"page\": 8, \"index\": 9, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-010.webp\", \"caption\": \"\", \"page\": 8, \"index\": 10, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-011.webp\", \"caption\": \"\", \"page\": 8, \"index\": 11, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-012.webp\", \"caption\": \"\", \"page\": 8, \"index\": 12, \"width\": 548, \"height\": 731}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-013.webp\", \"caption\": \"\", \"page\": 8, \"index\": 13, \"width\": 548, \"height\": 731}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-014.webp\", \"caption\": \"\", \"page\": 8, \"index\": 14, \"width\": 548, \"height\": 731}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-015.webp\", \"caption\": \"\", \"page\": 8, \"index\": 15, \"width\": 548, \"height\": 731}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-016.webp\", \"caption\": \"\", \"page\": 8, \"index\": 16, \"width\": 548, \"height\": 731}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-017.webp\", \"caption\": \"\", \"page\": 8, \"index\": 17, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-018.webp\", \"caption\": \"\", \"page\": 8, \"index\": 18, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-019.webp\", \"caption\": \"\", \"page\": 10, \"index\": 19, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-020.webp\", \"caption\": \"\", \"page\": 10, \"index\": 20, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-021.webp\", \"caption\": \"\", \"page\": 10, \"index\": 21, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-022.webp\", \"caption\": \"\", \"page\": 10, \"index\": 22, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-023.webp\", \"caption\": \"\", \"page\": 10, \"index\": 23, \"width\": 908, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-024.webp\", \"caption\": \"\", \"page\": 10, \"index\": 24, \"width\": 681, \"height\": 908}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-025.webp\", \"caption\": \"\", \"page\": 10, \"index\": 25, \"width\": 908, \"height\": 1210}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-026.webp\", \"caption\": \"\", \"page\": 11, \"index\": 26, \"width\": 735, \"height\": 585}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-027.webp\", \"caption\": \"\", \"page\": 11, \"index\": 27, \"width\": 735, \"height\": 585}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-028.webp\", \"caption\": \"\", \"page\": 11, \"index\": 28, \"width\": 735, \"height\": 585}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-029.webp\", \"caption\": \"\", \"page\": 11, \"index\": 29, \"width\": 773, \"height\": 756}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-030.webp\", \"caption\": \"\", \"page\": 11, \"index\": 30, \"width\": 773, \"height\": 756}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-518ed194b5b55fdec369d8c4/fig-031.webp\", \"caption\": \"\", \"page\": 11, \"index\": 31, \"width\": 773, \"height\": 756}]"
motivation: VLA模型仅依赖视觉，无法捕捉接触丰富操纵中的力与摩擦等交互动力学。
method: 提出轻量级后置触觉融合策略TacFiLM，无需大规模重训即可集成触觉信号。
result: 在接触密集型操纵任务上以低计算开销提升了VLA策略的可靠性。
conclusion: 为通用VLA模型在复杂接触任务中的感知增强提供了实用方案。
---

## Abstract
We propose TacFiLM, a lightweight modality-fusion ap-proach that integrates visual-tactile signals into vision-language-action(VLA) models. While advances in VLAs have introduced robot policiesthat are both generalizable and semantically grounded, these modelsmainly rely on vision-based perception. Vision alone, however, cannotcapture the complex interaction dynamics that occur during contact-richmanipulation, including contact forces, surface friction, compliance, andshear. While recent attempts to integrate tactile signals into VLA modelsoften increase complexity through token concatenation or large-scale pre-training, the heavy computational demands of behaviour models necessi-tate lightweight fusion strategies. To address these challenges, TacFiLMoutlines a post-training finetuning approach that conditions intermedi-ate visual features on pretrained tactile representations using feature-wise linear modulation (FiLM). Experimental results on insertion anddrawer opening tasks demonstrate consistent improvements in successrate, direct task performance, completion time, and force stability acrossboth in-distribution and out-of-distribution tasks. Together, these resultssupport our method as an effective approach to integrating tactile sig-nals into VLA models, improving contact-rich manipulation behaviours.Project page: https://charliem7.github.io/projects/TacFilm/

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "TacFiLM: Tactile Modality Fusion for Vision-Language-Action Models" structured according to 8 specific points. Let me analyze the paper carefully and produce a comprehensive summary.

The paper proposes TacFiLM, a lightweight modality fusion approach that integrates visual-tactile signals into VLA models using FiLM (Feature-wise Linear Modulation).

Let me organize the content according to the 8 required points:

1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Number of experiments and adequacy
6. Main conclusions
7. Strengths
8. Limitations

Let me write this out in Chinese with Markdown formatting.</think>

# TacFiLM 论文总结

## 1. 核心问题与研究动机

- **核心问题**：现有的视觉-语言-动作（VLA）模型（如 OpenVLA、π₀、RT-2 等）主要依赖视觉感知，无法捕捉接触丰富（contact-rich）操作中的接触力、表面摩擦、顺应性、剪切等交互动力学信息，导致在精密插孔、缆线插拔等任务上鲁棒性不足。
- **背景与挑战**：
  - 人类操作依赖视觉、触觉与本体感觉的多模态融合；视觉在遮挡和毫米级调整时反馈有限。
  - 已有触觉融合方法（如 token 拼接、跨模态预训练）通常需要大量数据和算力，且拼接会增加 token 长度、带来上下文退化风险；跨注意力需额外训练大量参数。
  - 通用行为模型对算力需求巨大，亟需轻量化的后训练（post-training）触觉融合策略。
- **目标**：提出一种轻量、即插即用、不增加 token 序列长度的触觉融合方式，让现有 VLA 通用策略能够直接利用触觉信息提升接触密集型任务表现。

## 2. 方法论

### 2.1 核心思想
- **TacFiLM** 通过 **特征线性调制（FiLM, Feature-wise Linear Modulation）** 将预训练触觉表示以"图像条件化"方式注入到 VLA 视觉编码器（DINOv2 + SigLIP）的中间特征中。
- 与 token 拼接不同，FiLM 不增加 LLM 输入 token 长度；与跨注意力不同，不引入大量可训练注意力参数。

### 2.2 关键技术细节

- **策略框架**：基于 OpenVLA-OFT 框架，包含融合 SigLIP + DINOv2 的视觉编码器、轻量 MLP 投影器、Llama-2-7B 解码器语言模型与 MLP 动作头（输出连续动作块）。
- **FiLM 融合流程**：
  1. 触觉图像（来自 DIGIT 视触传感器）由预训练触觉编码器（Sparsh-DINO / T3 等）编码为 patch 级特征，再池化为全局触觉嵌入 `z_t`。
  2. 对每个选定的 ViT block `n`，用一个 MLP 将 `z_t` 映射为 FiLM 参数 `γ_n, β_n`。
  3. FiLM 在每个 ViT block 的 Norm 之后、多头自注意力之前施加：
     ```
     FiLM(F_n | γ_n, β_n) = F_n ⊙ (1 + γ_n) + β_n
     ```
  4. 初始化 `γ, β = 0`，使条件化过程初始近似恒等变换。
- **训练策略**：对 VLA 与触觉编码器的线性层使用 **LoRA 微调**，FiLM 层从零训练，冻结大部分参数，从而保留预训练的视觉-语言先验。
- **预训练触觉编码器对比**：评估 T3、Sparsh-MAE、Sparsh-IJEPA、Sparsh-DINO 四种方案，**最终选用 Sparsh-DINO**（其在旋转/接触分类与 TacBench 力估计任务中表现最佳）。

## 3. 实验设计

- **硬件平台**：Franka Emika Panda 7 自由度机械臂 + 平行二指夹爪（搭载 DIGIT 视触传感器）+ Intel RealSense 相机。
- **控制栈**：基于 Polymetis + libfranka，1 kHz 控制频率，10 Hz 观测采样；使用 3Dconnexion SpaceMouse 进行遥操作示教。
- **任务设置**：插孔与拉抽屉两大类接触密集任务：
  - **分布内（ID）任务**：圆孔插孔（2mm/3mm 间隙）、USB 插头插入、抽屉打开。
  - **分布外（OOD）任务**：方孔/五角孔插孔（2mm/3mm）、HDMI 缆线插入。
  - 每个任务采集 **80 条示教**，每条约 70 步。
- **评测指标**：成功率（%）、直接成功率（首次尝试即成功）、平均最大接触力（N）、平均完成时间（s）。
- **基线方法**：
  1. **OpenVLA-OFT**：纯视觉基线。
  2. **TactileConcat**：使用 T3/Sparsh 编码后将触觉 token 拼接到 VLM 输入（代表 token 拼接方法）。
  3. **Cross-Attn**：参考 PolyTouch 架构，6 层交叉注意力块，视觉作为 Q、触觉作为 K/V（代表跨注意力方法）。

## 4. 资源与算力

- 论文未明确披露训练所用的 GPU 型号、数量、训练时长等算力细节。
- 仅提到所有方法均训练至 **80k 步**，并使用 LoRA 进行参数高效微调；机器人控制以 1 kHz 运行、采样 10 Hz。
- 这是该论文的一个明显信息缺失。

## 5. 实验数量与充分性

- **总实验规模**：超过 **1000 次真实机器人 rollout**。
  - 分布内评估：480 次（每个方法×任务 30 次）。
  - 分布外评估：300 次（每个方法×任务 15 次）。
  - 消融实验：240 次。
- **消融实验**：
  - FiLM 集成位置消融（AllFiLM / Early / Middle / Late FiLM）。
  - 相机鲁棒性消融（80% 亮度衰减、50% 帧冻结）。
  - 触觉编码器选型消融（T3 与三种 Sparsh 变体）。
- **客观性**：
  - 所有方法均在 OpenVLA-OFT 同一骨干上进行公平比较，差异可归因于融合策略。
  - 在 ID、OOD、视觉降级三个维度都做了系统评测，并通过分类任务与 TacBench 力回归任务选型触觉编码器。
- **局限性**：
  - 每个任务每次方法仅 15~30 次 rollout，统计样本量较小；
  - 任务集集中在插孔与抽屉开启，未覆盖更广泛的接触密集操作（如装配、打磨等）；
  - 仅在单一机器人硬件上验证。

## 6. 主要结论与发现

- **ID 任务**：TacFiLM 在 3mm 圆孔插孔上达到 **100% 成功率**，相比最佳基线在多个任务上最高提升 **50%**；直接成功率、力稳定性、效率均更优。
- **OOD 任务**：在 3mm 间隙插孔上仍保持 **100% 成功率**，HDMI 缆线插入成功率较基线提升约 **30%**；接触力约为基线的 **1/3**。
- **视觉降级鲁棒性**：80% 亮度衰减与 50% 帧冻结条件下 TacFiLM 仍保持 100% 成功率，体现触觉对视觉退化的补偿作用。
- **融合策略比较**：FiLM > 拼接 > 视觉 > 跨注意力；其中跨注意力因额外可训练参数多，在小数据下明显欠拟合。
- **触觉编码器选择**：Sparsh-DINO 在所有评测维度最优，成为默认配置。
- **FiLM 集成位置**：仅在 ViT 早期或部分 block 上施加即可获得相近效果，证明 TacFiLM 对融合位置不敏感、计算开销可控。

## 7. 优点与亮点

- **方法创新**：首次将 FiLM 用于 VLA 模型的触觉融合，既不增加 token 长度，也不引入大规模跨模态预训练，工程简洁。
- **保留预训练先验**：LoRA + 零初始化 FiLM 的训练策略，最大限度保留 VLA 视觉-语言先验，仅以低维全局触觉偏置（γ, β）注入新信息。
- **兼容性广**：融合方式对触觉编码器（T3 / Sparsh）以及 ViT 集成位置均不敏感。
- **多维度评估**：成功率、直接成功率、接触力、完成时间四指标联合反映可靠性、效率与安全性。
- **OOD 与鲁棒性双重验证**：分别在物体几何变化（OOD）与视觉退化（鲁棒性）下验证了方法的可推广性。
- **大量真实机器人实验**：超过 1000 次 rollout，远超多数同类研究的实验规模。

## 8. 不足与局限

- **算力信息缺失**：未披露 GPU 类型、数量、训练时长等关键算力细节。
- **任务覆盖有限**：实验仅围绕插孔、缆线插入、抽屉开启三类接触密集任务，缺乏更广泛的操作场景（如装配、揉捏、双手机器人等）。
- **真实环境偏差**：每个任务/方法 15~30 次 rollout 样本量较小，存在较大随机性，置信区间未完整报告。
- **依赖精确触觉仿真缺失**：作者明确指出由于缺乏精确视触仿真器，无法扩展到更复杂的虚拟环境，限制了大范围实验与对比。
- **架构耦合**：目前仅在 OpenVLA-OFT 上验证，未在 π₀.5、RT-2 等其他 VLA 骨干上验证，泛化到不同 VLA 架构仍是开放问题。
- **微调数据量**：80 条示教/任务属于小规模，可能限制更复杂融合机制的发挥（如跨注意力明显欠拟合）。

（完）
