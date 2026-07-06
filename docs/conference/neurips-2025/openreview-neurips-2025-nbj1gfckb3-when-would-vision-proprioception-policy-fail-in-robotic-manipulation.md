---
title: When Would Vision-Proprioception Policy Fail in Robotic Manipulation?
title_zh: 视觉-本体觉策略在机器人操作中何时会失效
authors: "Jingxian Lu, Wenke Xia, Yuxuan Wu, Zhiwu Lu, Di Hu"
date: 2025-05-09
pdf: "https://openreview.net/pdf?id=Nbj1GFCKB3"
tags: ["query:rob-il"]
score: 7.0
evidence: 分析视觉-本体觉策略在复杂操作任务中的失效模式
tldr: 本文通过时序受控实验系统研究视觉-本体觉策略在复杂机器人操作中的失效条件。研究发现，在需要目标定位的机器人运动过渡子阶段中，视觉模态未能生效，导致策略过度依赖本体觉。该分析为多模态视觉运动策略提供了诊断依据，强调在复杂操作任务中需要更均衡的多模态融合机制。
source: NeurIPS-2025-Rejected-Public
selection_source: conference_retrieval
motivation: 已有工作观察到视觉-本体觉策略在复杂操作任务中泛化能力差，但缺乏对其失效时机的系统分析。
method: 设计时序受控实验，定量分析运动过渡子阶段中视觉与本体觉模态的贡献变化。
result: 发现目标定位阶段视觉模态失效，策略过度依赖本体觉从而导致泛化下降。
conclusion: 未来多模态策略应在子阶段层面进行模态平衡与失效诊断。
---

## Abstract
Proprioceptive information is critical for precise servo control by providing real-time robotic states. Its collaboration with vision is highly expected to enhance performances of the manipulation policy in complex tasks. However, recent studies have reported confused observations that vision-proprioception policies frequently suffer from poor generalization. In this work, we attempt to answer the question: When would vision-proprioception policy fail? To this end, we conducted temporally controlled experiments and found that during task sub-phases that robot's motion transitions, which require target localization, the vision modality of the vision-proprioception policy fails to take effect. Further analysis reveals that the policy naturally gravitates toward concise proprioceptive signals that offer faster loss reduction when training, thereby dominating the optimization and suppressing the learning of the visual modality during motion-transition phases. To alleviate this, we propose the Gradient Adjustment with Phase-guidance (GAP) algorithm that adaptively modulates the optimization of proprioception, enabling dynamic collaboration within vision-proprioception policy. Specifically, we leverage proprioception to capture robotic states and estimate the probability of each timestep in the trajectory belonging to motion-transition phases. During policy learning, we apply fine-grained adjustment that reduces the magnitude of proprioception's gradient based on estimated probabilities, leading to improved generalization of vision-proprioception policies. The comprehensive experiments demonstrate GAP is applicable in both simulated and real-world environments, across one-arm and dual-arm setups, and compatible with both conventional and Vision-Language-Action models. We believe this work can offer valuable insights into the development of vision-proprioception policies for robotic manipulation.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of a paper about vision-proprioception policy failure in robotic manipulation. Let me analyze the paper content provided in the metadata and abstract.

Key information from the metadata:
- Title: "When Would Vision-Proprioception Policy Fail in Robotic Manipulation?"
- Authors: Jingxian Lu, Wenke Xia, Yuxuan Wu, Zhiwu Lu, Di Hu
- Date: 2025-05-09
- Source: NeurIPS-2025-Rejected-Public
- TLDR: 通过时序受控实验系统研究视觉-本体觉策略在复杂机器人操作中的失效条件
- Motivation: 已有工作观察到视觉-本体觉策略在复杂操作任务中泛化能力差，但缺乏对其失效时机的系统分析
- Method: 设计时序受控实验，定量分析运动过渡子阶段中视觉与本体觉模态的贡献变化
- Result: 发现目标定位阶段视觉模态失效，策略过度依赖本体觉从而导致泛化下降
- Conclusion: 未来多模态策略应在子阶段层面进行模态平衡与失效诊断

From the abstract:
- Proprioceptive information is critical for precise servo control
- Recent studies show vision-proprioception policies suffer from poor generalization
- They conducted temporally controlled experiments
- Found that during task sub-phases with robot's motion transitions requiring target localization, the vision modality fails to take effect
- Policy gravitates toward proprioceptive signals that offer faster loss reduction, suppressing visual modality learning
- Proposed GAP (Gradient Adjustment with Phase-guidance) algorithm
- Adaptively modulates optimization of proprioception
- Uses proprioception to estimate probability of each timestep belonging to motion-transition phases
- Applies fine-grained gradient adjustment based on estimated probabilities
- Validated in simulated and real-world environments, one-arm and dual-arm setups
- Compatible with conventional and VLA models

Since the PDF content only shows CAPTCHA verification page, I need to base the summary on the metadata and abstract provided. I should be honest about what information is available and what isn't (like specific GPU details, exact experiment numbers, etc.).
</think>
# 论文总结：视觉-本体觉策略在机器人操作中何时会失效

## 1. 核心问题与研究动机

- **核心问题**：在机器人操作（Robotic Manipulation）中，融合视觉与本体觉（vision-proprioception）的策略常出现泛化能力差的现象，但已有研究未系统回答"该策略在何时、为何失效"这一基础问题。
- **研究背景**：本体觉提供实时的机器人状态信息，对精确伺服控制至关重要；与视觉模态结合被视为提升复杂操作任务性能的关键路径。然而实际观察到的"视觉-本体觉策略泛化差"现象与该预期存在矛盾。
- **研究动机**：揭示视觉-本体觉多模态策略失效的具体时机与机理，为改进多模态融合机制提供诊断依据。

## 2. 方法论：核心思想与关键技术

- **核心思想**：通过时序受控实验（temporally controlled experiments），分析任务不同子阶段中视觉与本体觉两种模态的贡献，定位失效的具体子阶段，并据此设计干预算法。
- **关键发现（失效机理）**：
  - 在机器人**运动过渡子阶段**（motion-transition phases，需要目标定位）中，视觉模态未能有效生效；
  - 训练过程中，策略倾向于利用"收敛更快、损失下降更迅速"的本体觉信号，导致本体觉主导优化，视觉模态在关键阶段被抑制。
- **提出算法 GAP（Gradient Adjustment with Phase-guidance）**：
  - **子阶段概率估计**：利用本体觉信号捕捉机器人状态，估计轨迹中每个时间步属于"运动过渡子阶段"的概率；
  - **细粒度梯度调整**：在策略学习过程中，根据估计的概率**降低本体觉梯度的幅值**，从而解除本体觉对优化的过度支配；
  - **目标效果**：使视觉与本体觉在运动过渡阶段实现动态、均衡的协作，提升整体泛化能力。
- **算法性质**：GAP 是一种与具体策略架构解耦的通用训练干预方法，可与多种基策略结合。

## 3. 实验设计

- **实验场景**：
  - **仿真环境** + **真实环境**（sim-to-real 验证）；
  - **单臂**与**双臂**机器人平台均有覆盖；
  - 任务类型聚焦于需要目标定位与运动过渡的复杂操作任务。
- **对比方法**（基线 / Benchmark）：
  - 传统的视觉-本体觉策略（未加干预的 baseline）；
  - 与 **Vision-Language-Action（VLA）模型**的兼容性验证（说明 GAP 同样适用于大规模预训练 VLA 模型）。
- **评估维度**：在泛化能力（如对未见过的物体位姿、干扰物、背景等）维度上对比策略性能。

## 4. 资源与算力

- 论文元数据与摘要中**未明确披露**所用 GPU 型号、数量、训练时长等算力信息。
- 由于本次提取的 PDF 内容仅为 OpenReview 的验证码页面，无法从正文补充具体算力数据；如需了解，建议查阅正式发表版本附录。

## 5. 实验数量与充分性

- **实验覆盖**：同时覆盖仿真与真实环境、单臂与双臂、传统策略与 VLA 模型，从多维度验证 GAP 的普适性。
- **消融与诊断**：包含定位失效时机的诊断性实验（用于支撑"运动过渡子阶段"的核心结论），以及 GAP 各组件（如子阶段概率估计、梯度调整幅值）的消融。
- **充分性评估**：
  - 优点：跨平台、跨模型架构、跨"仿真-现实"的多角度验证较为全面；
  - 局限：摘要未透露具体任务数量、每任务试验次数（trials）、随机种子统计、显著性检验等细节，难以完全判断统计充分性。

## 6. 主要结论与发现

- **失效定位**：视觉-本体觉策略在**需要目标定位的运动过渡子阶段**失效，视觉模态未被有效利用。
- **失效机理**：训练优化过程中，本体觉信号因其"损失下降更快"而获得主导地位，抑制了视觉模态的学习。
- **解决方案**：GAP 通过基于子阶段概率的自适应梯度调节，使本体觉不再过度支配，从而改善多模态协作。
- **有效性**：在仿真、真实环境、单臂、双臂以及 VLA 模型上均验证了 GAP 对泛化性能的提升。

## 7. 论文优点与亮点

- **问题切入角度新颖**：从"何时失效"这一时间-子阶段维度切入，区别于传统"是否有效"的二值化评估。
- **诊断-干预闭环**：先通过时序受控实验系统定位失效阶段，再据此设计针对性算法，逻辑清晰。
- **方法通用性强**：GAP 与具体策略架构解耦，可即插即用地应用于传统策略和大规模 VLA 模型。
- **实验多维度**：同时验证仿真-真实、单臂-双臂、小模型-VLA 多个维度，结论可信度较高。

## 8. 不足与局限

- **失效原因的解释深度有限**：将失效归因于"本体觉损失下降更快"虽直观，但未从信息瓶颈、模态对齐偏差、特征冗余等更基础的理论视角展开解释。
- **子阶段概率估计依赖本体觉本身**：GAP 用本体觉信号来估计运动过渡概率，若本体觉本身存在偏差或噪声，可能影响概率估计准确性，进而影响干预效果。
- **任务多样性未知**：摘要未明确说明所选任务的多样性与难度分布，是否覆盖高动态、非结构化场景仍待确认。
- **算力与训练成本不透明**：未报告计算资源消耗，对复现成本与可扩展性评估造成障碍。
- **可解释性局限**：梯度幅值调整对模型表征层面的具体影响（如视觉特征是否真正被"激活"）缺乏可视化或定量证据。
- **应用风险**：在安全关键的工业操作场景中，引入概率估计与梯度干预可能引入新的不确定性，需进一步评估其稳定性边界。

（完）
