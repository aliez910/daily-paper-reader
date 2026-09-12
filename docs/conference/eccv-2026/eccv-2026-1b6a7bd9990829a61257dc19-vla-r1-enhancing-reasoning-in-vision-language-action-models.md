---
title: "VLA-R1: Enhancing Reasoning in Vision-Language-Action Models"
title_zh: VLA-R1：增强视觉-语言-动作模型中的推理能力
authors: "Angen Ye, Zeyu Zhang, Boyuan Wang, Xiaofeng Wang, Dapeng Zhang, Zheng Zhu"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/7763.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 具备显式推理能力的视觉-语言-动作端到端动作生成模型
tldr: VLA模型旨在统一感知、语言与动作生成，具有强大的跨任务跨场景泛化能力，但当前模型缺少显式逐步推理，常直接输出动作而忽略可供性约束与几何关系，且后训练阶段多依赖弱奖励的监督微调。本文提出VLA-R1，将可验证奖励的强化学习与GRPO相结合，系统优化推理与执行两端：先以推理质量作为可验证奖励引导，再联合优化执行能力，从而让VLA在推理过程中显式考虑物理与几何约束，提升复杂机器人控制任务中的端到端表现与泛化能力。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 1570, \"height\": 883}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 1189, \"height\": 1068}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 1290, \"height\": 1156}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 1423, \"height\": 1275}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-005.webp\", \"caption\": \"\", \"page\": 6, \"index\": 5, \"width\": 405, \"height\": 360}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-006.webp\", \"caption\": \"\", \"page\": 6, \"index\": 6, \"width\": 1126, \"height\": 960}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-007.webp\", \"caption\": \"\", \"page\": 6, \"index\": 7, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-008.webp\", \"caption\": \"\", \"page\": 6, \"index\": 8, \"width\": 1024, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-009.webp\", \"caption\": \"\", \"page\": 6, \"index\": 9, \"width\": 1222, \"height\": 522}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-010.webp\", \"caption\": \"\", \"page\": 7, \"index\": 10, \"width\": 1200, \"height\": 809}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-011.webp\", \"caption\": \"\", \"page\": 7, \"index\": 11, \"width\": 642, \"height\": 432}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-012.webp\", \"caption\": \"\", \"page\": 7, \"index\": 12, \"width\": 642, \"height\": 443}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-013.webp\", \"caption\": \"\", \"page\": 7, \"index\": 13, \"width\": 708, \"height\": 656}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-014.webp\", \"caption\": \"\", \"page\": 7, \"index\": 14, \"width\": 592, \"height\": 646}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-015.webp\", \"caption\": \"\", \"page\": 7, \"index\": 15, \"width\": 1200, \"height\": 807}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-016.webp\", \"caption\": \"\", \"page\": 7, \"index\": 16, \"width\": 641, \"height\": 439}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-017.webp\", \"caption\": \"\", \"page\": 12, \"index\": 17, \"width\": 603, \"height\": 455}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-018.webp\", \"caption\": \"\", \"page\": 12, \"index\": 18, \"width\": 600, \"height\": 450}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-019.webp\", \"caption\": \"\", \"page\": 12, \"index\": 19, \"width\": 648, \"height\": 487}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-020.webp\", \"caption\": \"\", \"page\": 12, \"index\": 20, \"width\": 647, \"height\": 487}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-021.webp\", \"caption\": \"\", \"page\": 12, \"index\": 21, \"width\": 644, \"height\": 485}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-022.webp\", \"caption\": \"\", \"page\": 12, \"index\": 22, \"width\": 647, \"height\": 486}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-023.webp\", \"caption\": \"\", \"page\": 12, \"index\": 23, \"width\": 647, \"height\": 486}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-024.webp\", \"caption\": \"\", \"page\": 12, \"index\": 24, \"width\": 647, \"height\": 486}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-025.webp\", \"caption\": \"\", \"page\": 12, \"index\": 25, \"width\": 647, \"height\": 486}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-026.webp\", \"caption\": \"\", \"page\": 12, \"index\": 26, \"width\": 650, \"height\": 488}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-027.webp\", \"caption\": \"\", \"page\": 14, \"index\": 27, \"width\": 641, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-1b6a7bd9990829a61257dc19/fig-028.webp\", \"caption\": \"\", \"page\": 14, \"index\": 28, \"width\": 641, \"height\": 480}]"
motivation: 现有VLA缺乏显式推理且后训练奖励弱，难以兼顾推理质量与动作执行。
method: 结合可验证奖励的强化学习与GRPO，系统优化VLA的推理过程与执行能力。
result: 在多个VLA基准上提升推理质量与端到端动作生成精度。
conclusion: 为通用VLA模型引入显式推理与强化学习奖励，提升复杂机器人控制能力。
---

## Abstract
Vision-Language-Action (VLA) models aim to unify per-ception, language understanding, and action generation, offering strongcross-task and cross-scene generalization with broad impact on embodiedAI. However, current VLA models often lack explicit step-by-step rea-soning, instead emitting final actions without considering affordance con-straints or geometric relations. Their post-training pipelines also rarelyreinforce reasoning quality, relying primarily on supervised fine-tuningwith weak reward design. To address these challenges, we present VLA-R1, a reasoning-enhanced VLA that integrates Reinforcement Learningfrom Verifiable Rewards (RLVR) with Group Relative Policy Optimiza-tion (GRPO) to systematically optimize both reasoning and execution.Specifically, we design an RLVR-based post-training strategy with ver-ifiable rewards for region alignment, trajectory consistency, and outputformatting, thereby strengthening reasoning robustness and executionaccuracy. Moreover, we develop VLA-CoT-13K, a high-quality datasetthat provides chain-of-thought supervision explicitly aligned with affor-dance and trajectory annotations. Furthermore, extensive evaluations onin-domain, out-of-domain, simulation, and real-robot platforms demon-strate that VLA-R1 achieves superior generalization and real-world per-formance compared to prior VLA methods. We plan to release the model,code, and dataset following the publication of this work.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "VLA-R1: Enhancing Reasoning in Vision-Language-Action Models" following a structured Markdown template. I need to cover 8 specific points and end with "（完）".

Let me carefully analyze the paper content and structure my response:

1. Core problem and motivation: VLA models lack explicit reasoning, post-training relies on weak rewards
2. Methodology: VLA-R1 with RLVR + GRPO, VLA-CoT-13K dataset, three verifiable rewards (GIoU, ALAF Fréchet, Format)
3. Experiments: In-domain (ShareRobot), OOD (UMD, VAIT), real-world (4 scenarios + S5), simulation (Piper, UR5)
4. Resources/compute: Not explicitly mentioned in the paper
5. Experimental sufficiency: Multiple baselines, ablation studies, real-world and simulation tests
6. Main conclusions
7. Strengths
8. Limitations

Let me write this in Chinese with Markdown formatting.</think>

# VLA-R1 论文总结

## 1. 核心问题与研究动机

- **研究背景**：Vision-Language-Action（VLA）模型旨在统一感知、语言理解与动作生成，具备较强的跨任务、跨场景泛化能力，是具身智能的重要研究方向。
- **现有 VLA 的两大缺陷**：
  - **缺乏显式逐步推理**：模型往往直接输出最终动作，没有对可供性 affordance 约束、几何关系、容器选择等进行显式推理，导致在颜色相似、物体重复、多个候选容器等场景下出现指令消歧失败。
  - **后训练阶段奖励设计薄弱**：主流方法仅依赖监督微调（SFT），缺乏对推理质量的强化；即便引入 RL，也多采用单一目标奖励，难以同时优化区域对齐与轨迹一致性，泛化性和真实场景表现受限。
- **本文目标**：同时在"数据层"与"优化层"注入显式推理能力，弥合推理质量与动作执行之间的鸿沟。

## 2. 方法论

### 2.1 整体框架
VLA-R1 采用 **两阶段训练**：
1. **Stage 1（SFT）**：在 VLA-CoT-13K 上进行监督微冷启，使模型学会"先思考再执行"；
2. **Stage 2（RL）**：基于 GRPO 与三类可验证奖励做强化学习后训练。

### 2.2 关键模块
- **基础模型**：以 Qwen2.5-VL-3B 为骨架，ViT + 2D RoPE 视觉编码，MLP merger 投影视觉 token，再由 Qwen2.5 解码器融合多模态信息，附加 action decoder 模块映射到控制输出。
- **控制栈**：推理时将几何预测（2D 可供性框 + 2D 轨迹）通过相机内外参做深度反投影，再经机器人 URDF 与运动学求解得到关节级命令。
- **VLA-CoT Data Engine**：使用 Qwen2.5-VL-72B 作为教师模型，针对 affordance 与 trajectory 两类任务分别生成结构化 CoT：
  - Affordance 任务：任务解析 → 场景语义理解 → 可供性区域定位 → 可行性检查；
  - Trajectory 任务：指令-运动解析 → 目标/夹爪定位 → 轨迹-场景交互分析 → 轨迹逻辑与平滑性分析。
- **数据集**：基于 ShareRobot 子集生成 **VLA-CoT-13K**（13K CoT 标注），同时具有 affordance、轨迹、CoT 标注，覆盖 12 种机器人、102 个任务。

### 2.3 三类可验证奖励
1. **Affordance 奖励（GIoU）**：$R_{aff}=GIoU(\hat b, b^*)$，在非重叠情况下也能提供有效梯度信号；
2. **轨迹奖励（Angle-Length Augmented Fréchet, ALAF）**：
   - $D_{ALAF}$ 同时考虑位置、夹角（$\lambda_\theta$）和相邻段长度比（$\lambda_r$）：
   $$D_{ALAF}(\hat T,T^*) = \min_\Phi \max_{(i,j)\in\Phi}\Big\{\|\hat p_i-p_j^*\|^2 + \lambda_\theta \arccos\!\big(\frac{\hat t_i t_j^*}{\|\hat t_i\|\|t_j^*\|}\big) + \lambda_r \log(\hat \ell_i/\ell_j^*)\Big\}$$
   - 归一化后 $R_{traj} = 1-\tilde D_{ALAF}$；
3. **格式奖励**：模型输出须符合 `<think>...<output>...</output>` 结构，二值奖励。

### 2.4 GRPO 目标
$$L_{GRPO}(\theta) = -\sum_{g=1}^{n}\frac{1}{|o_g|}\sum_{k=1}^{|o_g|}\Big[\min\big(r_{g,k}(\theta)\hat A_{g,k},\ \mathrm{clip}(r_{g,k}(\theta),1-\epsilon,1+\epsilon)\hat A_{g,k}\big) - \beta D_{KL}(\pi_\theta\|\pi_{ref})\Big]$$
组内优势 $\hat A_{g} = (r_g-\bar r)/\sigma_r$，并通过 KL 惩罚防止策略漂移。

## 3. 实验设计

### 3.1 数据集与场景
- **域内 In-Domain**：ShareRobot 子集（12 机器人、102 任务），6,522 张 affordance 标注、6,870 张 trajectory 标注；
- **域外 Out-of-Domain**：UMD Part Affordance（1,200 样本，grasp/cut/pound/scoop）+ VAIT（500 轨迹样本，人工校正）；
- **真实机器人**：4 个桌面场景（S1 颜色碗抓取、S2 同类水果消歧、S3 厨房微波炉遮挡、S4 混合干扰），以及为消歧专门设计的 S5；每个场景 10～30 次独立试验；
- **仿真**：RoboTwin 平台，桌面随机化生成器，Piper 与 UR5 两种机械臂，各 10 次试验。

### 3.2 评测指标
- **可供性**：IoU (%)；
- **轨迹**：离散 Fréchet 距离（DFD）、Hausdorff 距离（HD）、RMSE，统一归一化到 [0,1000)；
- **任务级**：成功率 SR（affordance 需正确抓握/无对象时输出空；trajectory 需到达目标区域并完成放置）。

### 3.3 对比基线
- 开源多模态模型：Phi-4-MM、Gemma-3-12B/27B-it、Qwen2.5-VL-3B/32B-Instruct；
- SFT 模型：InternVL2-2B、LLaVA-1.6-7B、RoboBrain-7B、NORA-3B；
- RL 后训练模型：ManipLVM-R1-3B、Embodied-R1-3B；
- 真实机器人基线：OpenVLA、RT-2-X、Pi0、Pi0.5（部分基线经 160 条真实 + 80 条仿真轨迹微调后部署）。

### 3.4 消融实验
四组配置：无 CoT 无 RL / 仅 CoT / 仅 RL / CoT+RL，全部在相同超参数下训练。

## 4. 资源与算力

- **论文未明确披露** 使用的 GPU 型号、数量或训练时长；也未给出参数量、推理延迟、显存占用等工程指标。仅说明基础模型采用 Qwen2.5-VL-3B，教师模型为 Qwen2.5-VL-72B。
- 训练曲线、收敛步数、计算开销等均未在文中报告，存在 **算力信息不透明** 的问题。

## 5. 实验数量与充分性

- **基准实验**：在域内、域外两组数据上对比 11 个基线；
- **真实机器人**：4 场景共 40 次试验，后期扩展为 5 场景 × 30 次试验 = 150 次真实试验；
- **仿真**：2 机械臂 × 10 次 = 20 次试验；
- **消融**：4 配置 × 全指标对比 + 案例可视化（图 5 展示 CoT 对 affordance/trajectory 的修正效果）；
- **公平性**：所有基线均采用 few-shot prompting 或经相同真实轨迹微调，OpenVLA/RT-2-X 等因不能直接部署到任意本体，作者专门采集数据进行微调以保证公平；
- **充分性评价**：覆盖域内/域外、仿真/真实，较为全面；但每个真实场景试验次数偏少（10 次/场景在统计上波动较大），后期扩到 30 次是必要的改进；缺少双臂、四足等其他本体验证。

## 6. 主要结论与发现

- 在域内基准上，VLA-R1-3B 取得 **IoU=36.51**、平均轨迹误差 **91.74**，相对最强基线 ManipLVM-R1 分别提升 **17.78%** 和下降 **17.25%**；
- 在 OOD 基准上，IoU 提升至 **33.96**，轨迹三项误差全面下降，验证跨域泛化能力；
- 在真实机器人上，affordance 平均 SR **62.5%**、trajectory SR **75%**，优于 Pi0.5（62.5%/70%）、Pi0（45%/50%）等；
- 仿真中 Piper 与 UR5 分别取得 60%/50% affordance SR 与 80%/60% trajectory SR；
- 消融表明 **CoT 与 RL 互补**：CoT 单独可提升 IoU（23.74→28.37），RL 单独可显著降低轨迹误差（128.38→108.66），两者结合效果最佳；
- CoT 能帮助模型在多勺、多目标等场景下进行颜色/位置消歧，并避免轨迹碰撞。

## 7. 优点与亮点

- **数据 + 优化双轮驱动**：同时提出 VLA-CoT 数据引擎与 RLVR 后训练策略，是首个把 CoT 显式监督与可验证奖励联合用于 VLA 的工作；
- **奖励设计细致且可验证**：ALAF 同时度量位置、切向角度和段长比，比传统 Fréchet 更适合评估轨迹形状与平滑性；GIoU 在非重叠区域仍能提供梯度；
- **结构化输出**：强制 `<think>/<output>` 格式，提升可解释性，便于工程落地与失败分析；
- **评测覆盖多维度**：同时覆盖域内/域外基准、仿真、真实机器人，并扩展消歧专用场景；
- **相对小模型（3B）取得 SOTA**：相比更大参数模型（Qwen2.5-VL-32B、Gemma-3-27B）有显著优势，具身任务的"推理质量"比"参数规模"更关键。

## 8. 不足与局限

- **算法与奖励假设**：所有奖励都依赖 2D 标注（bbox + 像素轨迹），未利用深度、3D 点云或本体感知信号，限制了在强遮挡、非平面场景中的适用性；
- **GRPO 与可验证奖励的依赖**：需要任务级 ground truth（affordance 框 + 轨迹），推广到没有标注的开放任务（如长程家务）仍困难；
- **真实试验样本量**：早期真实机器人仅 10 次/场景，统计噪声较大；后续扩到 30 次虽更可靠但仍未覆盖随机扰动、光照变化等；
- **本体单一**：仅在 Piper、UR5 等单臂桌面机器人上验证，论文 Limitations 明确指出 **未在双臂、四足等本体上验证**，泛化到更复杂本体的能力未知；
- **算力信息缺失**：训练硬件、时长、显存、推理延迟均未披露，难以复现和成本评估；
- **CoT 生成依赖闭源/大教师**：使用 Qwen2.5-VL-72B 生成 CoT，存在教师模型偏差传播风险，且成本较高；
- **奖励设计可能引发 reward hacking**：GIoU 与 ALAF 仅约束几何对齐，无法保证物理可行性（如奇异点、关节限位），需要控制栈兜底；
- **基线对比范围**：缺少对近期 reasoning-VLA（如 HiRT、3D-VLA、SuSIE 等）的对比，且部分基线（OpenVLA、RT-2-X）经过额外微调，公平性仍存一定争议。

（完）
