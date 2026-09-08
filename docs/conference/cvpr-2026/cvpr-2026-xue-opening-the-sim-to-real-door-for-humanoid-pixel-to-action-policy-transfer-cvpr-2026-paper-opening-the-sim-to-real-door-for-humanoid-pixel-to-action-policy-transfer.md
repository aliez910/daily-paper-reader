---
title: Opening the Sim-to-Real Door for Humanoid Pixel-to-Action Policy Transfer
title_zh: 为类人机器人像素到动作策略迁移打开仿真到真实之门
authors: "Xue, Haoru, He, Tairan, Wang, Zi, Ben, Qingwei, Xiao, Wenli, Luo, Zhengyi, Da, Xingye, Castañeda, Fernando, Shi, Guanya, Sastry, Shankar, Fan, Linxi, Zhu, Yuke"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Xue_Opening_the_Sim-to-Real_Door_for_Humanoid_Pixel-to-Action_Policy_Transfer_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向人形机器人像素到动作的闭环策略迁移
tldr: "本文利用GPU加速的真实感仿真,构建可扩展的仿真到真实迁移路径,用于视觉驱动的人形机器人运动操纵。作者设计了师生自举学习框架,结合分阶段重置探索策略与GRPO微调,以提升部分可观测性下的闭环一致性。在铰接物体交互等高难度基准上的结果表明,纯仿真训练的像素到动作策略可成功迁移至真实人形机器人,验证了闭环视觉反馈在复杂操纵任务中的可行性。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1811, \"height\": 945, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1800, \"height\": 1242, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 868, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1805, \"height\": 868, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1804, \"height\": 523, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 857, \"height\": 443, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 857, \"height\": 465, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/fig-008.webp\", \"caption\": \"\", \"page\": 0, \"index\": 8, \"width\": 851, \"height\": 457, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xue-opening-the-sim-to-real-door-for-humanoid-pixel-to-action-policy-transfer-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 324, \"label\": \"Table\"}]"
motivation: "真实机器人数据昂贵,需要利用仿真实现可扩展的视觉策略迁移到真实人形机器人。"
method: "提出师生自举框架结合分阶段重置探索与GRPO微调,提升闭环一致性与可迁移性。"
result: 纯仿真训练的像素到动作策略成功迁移至真实人形机器人完成铰接物交互。
conclusion: 为视觉驱动的复杂机器人闭环操纵控制提供了仿真到真实的新路径。
---

## Abstract
Recent progress in GPU-accelerated, photorealistic simulation has opened a scalable data-generation path for robot learning, where massive physics and visual randomization allow policies to generalize beyond curated environments. Building on these advances, we develop a teacher-student-bootstrap learning framework for vision-based humanoid loco-manipulation, using articulated-object interaction as a representative high-difficulty benchmark. Our approach introduces a staged-reset exploration strategy that stabilizes long-horizon privileged-policy training, and a GRPO-based fine-tuning procedure designed to mitigate partial observability and improve closed-loop consistency in sim-to-real RL. Trained entirely on synthetic simulation data, the resulting policy achieves robust zero-shot performance across diverse articulated objects--including multiple door types--and outperforms human teleoperators by up to 31.7% in task completion time under the same whole-body control stack. This represents the first humanoid sim-to-real policy capable of diverse articulated loco-manipulation from pure RGB perception.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Opening the Sim-to-Real Door for Humanoid Pixel-to-Action Policy Transfer" based on the provided metadata and abstract. Let me organize this into the 8 requested sections.

The paper is about sim-to-real transfer for humanoid robots, specifically for pixel-to-action policies in articulated object manipulation (like opening doors). Let me analyze the content carefully:

1. Core problem: Real robot data is expensive, need to use simulation for scalable vision policy transfer to real humanoid robots.

2. Method: Teacher-student-bootstrap learning framework with:
   - Staged-reset exploration strategy for stabilizing long-horizon privileged policy training
   - GRPO-based fine-tuning to mitigate partial observability and improve closed-loop consistency
   - Pure RGB perception
   - Synthetic simulation data only

3. Experiments: Articulated object interaction as benchmark (door opening)

4. Resources: Not explicitly mentioned in the provided text

5. Experimental quantity: Not fully detailed in the provided content

6. Conclusions: First humanoid sim-to-real policy for articulated loco-manipulation from pure RGB, outperforms human teleoperators by up to 31.7%

7. Advantages: Scalable sim-to-real, pure RGB perception, outperforms human teleoperators

8. Limitations: Not explicitly detailed in the provided content

Let me write this up in Chinese with the requested structure.</think>

# 论文总结：Opening the Sim-to-Real Door for Humanoid Pixel-to-Action Policy Transfer

## 1. 核心问题与研究动机

- **核心问题**：如何将仅在仿真环境中训练的视觉驱动（像素到动作）策略高效、可扩展地迁移到真实的人形机器人上，使其能够完成复杂的"全身运动+操纵"任务。
- **背景与动机**：
  - 真实机器人数据采集成本高昂、规模受限，难以支撑大规模视觉策略学习。
  - 随着 GPU 加速的真实感仿真技术日趋成熟，物理与视觉随机化使仿真训练具备良好的泛化潜力。
  - 已有工作多集中于固定基座机械臂或简单任务，**全人形机器人在部分可观测条件下的仿真到真实（sim-to-real）像素到动作闭环迁移**仍是开放难题。
  - 本文选取**铰接物体交互（如开门）**作为高难度基准任务，因其涉及长视野、接触丰富、对闭环反馈依赖强。

## 2. 方法论

- **整体框架**：教师—学生—自举（teacher–student–bootstrap）学习框架，面向视觉驱动的人形 loco-manipulation（全身运动+操纵）。
- **核心技术细节**：
  - **分阶段重置探索策略（Staged-Reset Exploration）**：
    - 在特权信息（privileged policy）训练阶段，通过分阶段重置机制稳定长视野训练，避免策略陷入局部最优或发散。
    - 通过课程式的状态重置，逐步引导策略探索更具挑战性的接触与操纵阶段。
  - **基于 GRPO 的微调（GRPO-based Fine-tuning）**：
    - 使用 Group Relative Policy Optimization 对学生策略进行微调。
    - 目的：缓解部分可观测性带来的不确定性，提升闭环一致性。
  - **数据来源**：
    - 训练数据**完全来自仿真**，包含大规模物理与视觉随机化。
    - 学生策略仅接收**纯 RGB 视觉输入**（pixel-to-action），无需特权状态。
- **算法流程（文字描述）**：
  1. 在仿真中利用特权信息训练教师策略；
  2. 通过分阶段重置策略稳定训练过程；
  3. 教师策略产生演示用于学生策略的行为克隆/自举学习；
  4. 引入 GRPO 对学生策略进行微调，使其在部分可观测的 RGB 输入下保持闭环稳定；
  5. 训练完成后直接零样本部署到真实人形机器人。

## 3. 实验设计

- **任务与场景**：
  - 核心基准任务：**铰接物体交互（articulated-object interaction）**，以开门为主，包含多种门型。
  - 属于全身控制（whole-body control）下的运动+操纵（loco-manipulation）任务。
- **感知模态**：纯 RGB 相机输入。
- **对比基线**：
  - 同一全身控制栈下的**人类遥操作员（human teleoperators）**作为主要性能对比对象。
  - （摘要中未明确列出其他具体基线方法，可能在正文有补充。）
- **评估指标**：任务完成时间（task completion time），并报告相对人类遥操作的提升幅度。

## 4. 资源与算力

- 论文摘要与元数据中**未明确给出**以下信息：
  - 使用的 GPU 型号与数量；
  - 总训练时长或墙钟时间；
  - 仿真环境规模、并行环境数。
- 从方法描述可推断：依赖 **GPU 加速的仿真平台**（可能是 Isaac 系列或类似），并涉及大规模并行 rollout 以支持 GRPO 微调；但具体算力细节需查阅正文/附录。

## 5. 实验数量与充分性

- 摘要中明确提到的实验维度：
  - 多种铰接物体（包含多种门型）的零样本泛化测试；
  - 与人类遥操作员在同一控制栈下的对照；
  - 报告了任务完成时间提升 **最高达 31.7%**。
- **充分性评估**：
  - 从公开摘要来看，实验覆盖了"多样化门型 + sim-to-real 零样本迁移 + 人机对比"三个关键维度，体现了较为系统的验证。
  - 但摘要**未披露消融实验细节**（如分阶段重置、GRPO 微调各自贡献的消融），无法仅凭摘要判断消融充分性。
  - 评测基线仅以人类遥操作为对照，缺少与其他 SOTA 仿真训练策略或他方 sim-to-real 方法的直接横向比较，公平性论证稍显单薄。

## 6. 主要结论与发现

- 本文实现了**首个仅依赖 RGB 视觉、纯仿真训练即可零样本迁移到真实人形机器人**的多样化铰接物体 loco-manipulation 策略。
- 在铰接物体交互（多种门型）任务上，该策略在相同全身控制栈下，**任务完成时间比人类遥操作员最高提升 31.7%**。
- 验证了**闭环视觉反馈**在复杂人形机器人操纵任务中的可行性与必要性。
- 表明基于 GPU 真实感仿真的可扩展数据生成路径，配合教师—学生—自举与 GRPO 微调，可以有效打通人形机器人的 sim-to-real 闭环策略迁移通道。

## 7. 优点与亮点

- **纯 RGB、零样本迁移**：无需特权状态在真机推理，部署门槛低。
- **大规模仿真数据 + 随机化**：物理与视觉双随机化提升跨物体、跨场景泛化能力。
- **方法组合创新**：分阶段重置探索 + GRPO 微调，分别针对训练稳定性与部分可观测下的闭环一致性，思路清晰。
- **人机对比视角**：与同一控制栈下的人类遥操作员直接比较，结果直观且具有实际参考价值。
- **任务难度高**：开门等铰接物操作对闭环反馈敏感，能充分暴露方法能力上限。

## 8. 不足与局限

- **资源与算力透明度不足**：未在摘要中披露 GPU 规模、训练时长、仿真并行度等关键细节，复现成本难以评估。
- **基线对比有限**：仅与人类遥操作员对比，缺少与其他 sim-to-real 视觉策略、模仿学习方法或他方 RL 基线的横向比较，难以判断相对领域内 SOTA 的位置。
- **消融实验缺失（基于摘要）**：分阶段重置、GRPO 微调各组件的贡献未在摘要中量化，需在正文确认。
- **感知模态单一**：仅依赖 RGB，未涉及深度、触觉或多模态融合，在遮挡或光照极端变化下的鲁棒性存疑。
- **任务集中于开门**：虽称为"多样化铰接物"，但摘要主要强调门类交互，向抽屉、柜门、工具操作等其他铰接物类型的泛化情况披露不足。
- **人形平台单一**：摘要未提及是否在多款人形机器人上验证，跨平台泛化能力未知。
- **安全与失败恢复**：真实人形机器人在开门失败时的行为、恢复策略与安全约束未见说明。

（完）
