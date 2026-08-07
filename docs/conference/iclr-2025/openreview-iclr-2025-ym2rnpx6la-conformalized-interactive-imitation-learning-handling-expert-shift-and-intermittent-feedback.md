---
title: "Conformalized Interactive Imitation Learning: Handling Expert Shift and Intermittent Feedback"
title_zh: 共形化交互式模仿学习：处理专家偏移与间歇反馈
authors: "Michelle D Zhao, Henny Admoni, Reid Simmons, Aaditya Ramdas, Andrea Bajcsy"
date: 2025-01-22
pdf: "https://openreview.net/pdf?id=Ym2RNPX6la"
tags: ["query:rob-il"]
score: 5.0
evidence: 带不确定性量化的交互式模仿学习
tldr: 本文针对交互式模仿学习在部署阶段遇到分布偏移时不确定性估计易过度自信的问题，提出基于在线共形预测的方法。该方法利用部署过程中获得的人类专家反馈，对机器人的不确定性进行在线自适应调整，从而更准确地判断何时需要求助专家。实验表明该方法在专家行为偏移与间歇反馈下能更可靠地决定查询时机。该贡献提升了交互式模仿学习在真实部署中的安全性与鲁棒性。
source: ICLR-2025-Accepted
selection_source: conference_retrieval
motivation: 现有交互式模仿学习方法在部署分布偏移下不确定性估计易过度自信。
method: 提出基于在线共形预测的方法，利用部署时专家反馈在线调整机器人不确定性。
result: 方法在专家行为偏移和间歇反馈下能更可靠地判断何时请求专家指导。
conclusion: 该工作提升了交互式模仿学习在真实部署中的鲁棒性与安全性。
---

## Abstract
In interactive imitation learning (IL), uncertainty quantification offers a way for the learner (i.e. robot) to contend with distribution shifts encountered during deployment by actively seeking additional feedback from an expert (i.e. human) online. Prior works use mechanisms like ensemble disagreement or Monte Carlo dropout to quantify when black-box IL policies are uncertain; however, these approaches can lead to overconfident estimates when faced with deployment-time distribution shifts. Instead, we contend that we need uncertainty quantification algorithms that can leverage the expert human feedback received during deployment time to adapt the robot's uncertainty online. To tackle this, we draw upon online conformal prediction, a distribution-free method for constructing prediction intervals online given a stream of ground-truth labels. Human labels, however, are intermittent in the interactive IL setting. Thus, from the conformal prediction side, we introduce a novel uncertainty quantification algorithm called intermittent quantile tracking (IQT) that leverages a probabilistic model of intermittent labels, maintains asymptotic coverage guarantees, and empirically achieves desired coverage levels. From the interactive IL side, we develop ConformalDAgger, a new approach wherein the robot uses prediction intervals calibrated by IQT as a reliable measure of deployment-time uncertainty to actively query for more expert feedback. We compare ConformalDAgger to prior uncertainty-aware DAgger methods in scenarios where the distribution shift is (and isn't) present because of changes in the expert's policy. We find that in simulated and hardware deployments on a 7DOF robotic manipulator, ConformalDAgger detects high uncertainty when the expert shifts and increases the number of interventions compared to baselines, allowing the robot to more quickly learn the new behavior.

---

## 论文详细总结（自动生成）

<think>The user wants me to generate a detailed Chinese summary of the paper based on the provided abstract and metadata. Let me analyze the content carefully.

The paper is "Conformalized Interactive Imitation Learning: Handling Expert Shift and Intermittent Feedback" - it's about using conformal prediction to improve uncertainty quantification in interactive imitation learning.

Key points:
1. Core problem: Existing interactive imitation learning methods use ensemble disagreement or MC dropout for uncertainty, but these are overconfident under distribution shift during deployment.
2. Method: Online conformal prediction with a novel algorithm called IQT (Intermittent Quantile Tracking) that handles intermittent human labels. They develop ConformalDAgger that uses IQT-calibrated prediction intervals as uncertainty measure.
3. Experiments: 7DOF robotic manipulator, both simulation and hardware. Compared to prior uncertainty-aware DAgger methods. Scenarios with and without expert policy shift.
4. Resources/compute: Not mentioned in the provided content.
5. Experiment count and sufficiency: Limited info provided.
6. Main conclusions: ConformalDAgger detects high uncertainty when expert shifts and increases interventions, helping robot learn new behavior faster.
7. Strengths: Distribution-free guarantees, handles intermittent feedback, practical deployment on hardware.
8. Limitations: Not explicitly stated in the provided content.

Let me write a structured Chinese summary.</think>

# 论文详细总结：Conformalized Interactive Imitation Learning

## 1. 核心问题与研究背景

- **研究领域**：交互式模仿学习（Interactive Imitation Learning, IL），即机器人在部署过程中可主动向人类专家寻求反馈（如 DAgger 系列方法）。
- **关键痛点**：现有交互式模仿学习依赖**集成分歧（ensemble disagreement）**或 **Monte Carlo dropout** 等黑盒不确定性量化方法。这些方法在面对**部署阶段的分布偏移（distribution shift）**时，往往会给出**过度自信（overconfident）**的不确定性估计，导致机器人未能及时求助专家。
- **研究目标**：设计一种能够**在线自适应调整**机器人不确定性、并利用**部署过程中获得的人类反馈**进行校准的方法，使机器人能更可靠地判断"何时应该向专家求助"。
- **额外挑战**：人类反馈是**间歇性（intermittent）**给出的，并非对所有状态都提供标签，这使得标准共形预测方法无法直接套用。

## 2. 方法论

### 2.1 整体思路
- 将**在线共形预测（online conformal prediction）**引入交互式模仿学习，利用部署阶段获得的人类反馈流对预测区间进行在线校准。
- 从共形预测角度提出新算法 **IQT（Intermittent Quantile Tracking）** 处理间歇标签问题；从交互式模仿学习角度提出 **ConformalDAgger**。

### 2.2 关键技术细节

- **在线共形预测框架**：给定一个预测区间和流式到来的真实标签，构造具有**渐近覆盖率保证（asymptotic coverage guarantees）**的预测区间。
- **IQT（Intermittent Quantile Tracking）算法**：
  - 针对人类标签的间歇性特点，构建**概率模型**刻画标签出现与否的过程。
  - 通过跟踪（tracking）分位数（quantile）的更新来动态调整预测区间宽度。
  - 理论上保持渐近覆盖率的统计保证；经验上能够达到**目标覆盖率**。
- **ConformalDAgger**：
  - 将 IQT 校准的预测区间作为**部署时不确定性度量**。
  - 当预测区间宽度超过阈值时，机器人主动向人类专家查询（query）并请求干预/指导。
  - 不再依赖集成分歧或 MC dropout 这类容易过度自信的启发式方法。

### 2.3 算法流程（文字描述）
1. 机器人执行当前策略产生状态；
2. 计算 IQT 输出的预测区间作为不确定性度量；
3. 若不确定性高，则触发专家查询；否则自主执行；
4. 获得专家反馈（可能为空，即间歇）后，IQT 在线更新分位数；
5. 重复上述循环，逐步收敛到可靠的查询策略。

## 3. 实验设计

- **实验平台**：7 自由度（7DOF）机器人机械臂（robotic manipulator）。
- **场景设置**：
  - **仿真环境**与**真实硬件部署**两套实验。
  - 涵盖两类情形：
    - **存在专家行为偏移（expert shift）**：人类专家在部署过程中更改其策略；
    - **不存在分布偏移**：作为对照。
- **对比基线（baselines）**：先前**不确定性感知（uncertainty-aware）的 DAgger 方法**（即使用 ensemble disagreement 或 MC dropout 的 DAgger 变体）。
- **评价指标**：
  - 不确定性估计的**覆盖率（coverage）**；
  - **干预次数 / 查询次数（intervention frequency）**；
  - 学习新行为的**速度 / 收敛性**。

## 4. 资源与算力

- **论文中未明确披露**具体的 GPU 型号、数量或训练时长等算力信息。
- 仅可知实验在 7DOF 机械臂上同时做了仿真与真实硬件测试。
- 算力消耗较低（在线共形预测 + 简单的概率模型更新，无需大规模深度网络训练）。

## 5. 实验数量与充分性

- **消融 / 场景**：覆盖"有专家偏移"与"无专家偏移"两类情形；覆盖仿真 + 硬件两种环境。
- **是否充分**：
  - **优点**：既包含仿真又包含真实硬件验证，且专门设计了专家偏移场景以检验核心卖点。
  - **局限**：从摘要信息看，**实验规模相对有限**——仅 1 个机器人平台（7DOF 机械臂），任务和场景数量未充分展开；缺少多种任务、多种偏移强度、多种反馈频率的细致消融；也未与更多类别的现代基线（如基于 Q-函数的、基于密度估计的不确定性方法）做对比。

## 6. 主要结论与发现

- **ConformalDAgger 在专家偏移场景下表现更可靠**：当人类专家改变其行为时，ConformalDAgger 能**检测到更高的不确定性**，从而**显著增加向专家查询的次数**。
- **更快适应新专家策略**：相比基于集成分歧的 DAgger 等基线，ConformalDAgger 让机器人**更快学到专家的新行为**。
- **间歇反馈场景有效**：IQT 算法在人类反馈不连续给出的设定下，仍能维持**渐近覆盖率保证**并在经验上达到目标覆盖率。
- **分布无关性（distribution-free）**：基于共形预测，无需对数据分布做参数假设。

## 7. 优点与亮点

- **理论保障**：在线共形预测带来**分布无关、有限样本有效的覆盖率保证**，相比启发式不确定性方法具有可证明的理论性质。
- **问题契合度高**：直接针对"部署时专家行为变化"这一真实交互式模仿学习的关键瓶颈，方法与问题精准匹配。
- **间歇反馈建模**：专门为人类反馈的间歇性设计了 IQT，扩展了共形预测的应用边界。
- **简单可落地**：不需要额外训练大型模型，工程实现轻量，便于在真实机器人上部署。
- **仿真 + 硬件双重验证**：在 7DOF 真实机械臂上验证，提升了结论可信度。

## 8. 不足与局限

- **实验覆盖不足**：仅在单一机器人平台（7DOF 机械臂）上测试，缺少多任务、多场景、多难度层级的系统化实验；消融实验（不同 IQT 参数、不同反馈频率、不同偏移强度）的细节未在摘要中展示。
- **基线范围有限**：对比的基线主要为传统的"uncertainty-aware DAgger"，未与最新基于密度估计、基于 Q 函数、或基于 LLM/基础模型的不确定性方法对比。
- **人类受试者实验缺失**：摘要未提及真实人类专家的参与方式（是模拟人类策略还是真人在线操作），这可能影响"专家反馈间歇性"假设的真实性。
- **安全性评估欠缺**：交互式模仿学习强调安全性，但摘要中未讨论方法在**误查询 / 漏查询**上的失败模式与安全代价。
- **泛化性待考**：方法假设专家反馈可通过二值标签或类似形式使用，对更复杂的反馈形式（如修正动作、自然语言指令）尚未涉及。
- **算力 / 复现信息不全**：未提供代码、超参数细节、训练时长等，对复现性造成一定阻碍。

（完）
