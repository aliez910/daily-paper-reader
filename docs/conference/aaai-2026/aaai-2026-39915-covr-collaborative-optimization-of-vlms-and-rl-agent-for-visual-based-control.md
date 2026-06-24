---
title: "COVR: Collaborative Optimization of VLMs and RL Agent for Visual-Based Control"
title_zh: COVR：视觉-语言模型与强化学习智能体的协同优化用于视觉控制
authors: "Canming Xia, Peixi Peng, Guang Tan, Zhan Su, Haoran Xu, Zhenxian Liu, Luntong Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/39915/43876"
tags: ["query:rob-il"]
score: 6.0
evidence: 视觉-语言模型与强化学习的协同优化用于视觉控制
tldr: 视觉强化学习样本效率低，现有方法仅单方向从VLM蒸馏到RL。COVR提出协作优化框架，利用RL生成数据微调VLM以增强语义推理，再通过动作先验辅助RL策略，在多个视觉控制任务上提升了样本效率和最终性能。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39915/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 239, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39915/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 874, \"height\": 237, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39915/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 873, \"height\": 232, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39915/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1829, \"height\": 733, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-39915/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 874, \"height\": 466, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 862, \"height\": 1053, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 852, \"height\": 727, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 854, \"height\": 728, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1572, \"height\": 338, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1814, \"height\": 581, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-39915/table-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1837, \"height\": 705, \"label\": \"Table\"}]"
motivation: 视觉RL样本效率低，现有VLM辅助RL方法忽略RL数据对VLM的反哺。
method: 提出COVR框架，交替使用RL数据微调VLM和利用增强VLM指导RL策略。
result: 在多个复杂视觉控制任务中，COVR显著提升了RL的样本效率和成功率。
conclusion: 双向协作能更充分发挥VLM在视觉控制中的潜力。
---

## Abstract
Visual reinforcement learning (RL) suffers from poor sample efficiency due to high-dimensional observations in complex tasks. While existing works have shown that vision-language models (VLMs) can assist RL, they often focus on knowledge distillation from the VLM to RL, overlooking the potential of RL-generated interaction data to enhance the VLM. To address this, we propose COVR, a collaborative optimization framework that enables the mutual enhancement of the VLM and RL policies. Specifically, COVR fine-tunes the VLM with RL-generated data to enhance the semantic reasoning ability consistent with the target task, and uses the enhanced VLM to further guide policy learning via action priors. To improve fine-tuning efficiency, we introduce two key modules: (1) an Exploration-Driven Dynamic Filter module that preserves valuable exploration samples using adaptive thresholds based on the degree of exploration, and (2) a Return-Aware Adaptive Loss Weight module that improves the stability of training by quantifying the inconsistency of sampling actions via return signals of RL. We further design a progressive fine-tuning strategy to reduce resource consumption. Extensive experiments show that COVR achieves strong performance across various challenging visual control tasks.

---

## 论文详细总结（自动生成）

以下是根据提供的论文内容生成的中文总结。所有信息均源自原文，未添加额外推测。

---

## 中文总结

### 1. 核心问题与整体含义（研究动机和背景）

视觉强化学习（RL）在处理高维视觉观察时面临样本效率低下的问题。现有利用视觉-语言模型（VLM）辅助RL的工作通常只关注知识从VLM向RL的单向蒸馏（如固定VLM作为特征提取器或通过蒸馏提供先验），却忽略了RL交互生成的数据同样能够反哺和增强VLM的领域知识。作者提出，VLM与RL具有很强的互补性：VLM可提供语义先验加速策略学习，RL能够探索出高质量的状态-动作轨迹用于微调VLM。因此，设计一个双向协作的优化框架是自然且有益的。核心动机即利用RL数据增强VLM的任务推理能力，再将增强后的VLM用于指导RL策略，从而提升整体性能。

### 2. 方法论

**核心思想**：提出COVR框架，包含两个交替进行的阶段：**VLM‑Guided RL** 和 **RL‑tuned VLM**，实现VLM与RL策略的相互增强。

**关键技术细节**：
- **基础算法**：以SAC（Soft Actor‑Critic）作为底层RL算法。
- **VLM‑Guided RL（策略指导）**：在每个时间步，VLM根据当前观测和任务提示推理出一个动作先验 \( a_{v,t} \)，通过解析函数转为连续动作；RL策略网络输出动作 \( a_{r,t} \) 与环境交互。策略损失中加入正则项 \( \lambda \|a_{v,t} - a_{r,t}\|_2^2 \)，使策略网络向VLM的动作先验靠拢。
- **RL‑tuned VLM（用RL数据微调VLM）**：使用RL生成的轨迹数据（观测、动作、累积回报）对VLM进行监督微调。为提高微调效率和质量，提出两个核心模块：
  1. **Exploration‑Driven Dynamic Filter (EDDF)**：维护一个存放轨迹数据的缓冲区，对累积回报进行Z‑score标准化；根据RL策略的当前探索程度（以策略熵 \( \varepsilon_t \) 衡量）动态调整筛选阈值 \( \tau = \text{Median}(G_z) + \text{Sigmoid}(\varepsilon_t) \cdot \text{IQR}(G_z) \)。训练初期熵高时阈值较低，保留更多潜在有价值样本；后期熵降低后阈值变严，优先使用高回报样本。
  2. **Return‑Aware Adaptive Loss Weight (RALW)**：从EDDF筛选出的样本中，将累积回报归一化到[-1,1]；定义自动回归损失时，对每个样本赋予权重 \( w = \max(\bar{g}, 0) \)，使高回报样本对梯度贡献更大，抑制低回报（负回报）样本，缓解类似观测下动作不一致的问题。
- **渐进式微调策略**：微调间隔 \( \psi_c \) 随微调次数 \( c \) 线性增长（\( \psi_{c+1} = \psi_c + \psi_c \cdot c \)），初始间隔 \( \psi_0 = 5000\)；每次微调后清空轨迹缓冲区，并采用LoRA低秩微调减少显存消耗。

**算法流程（文字简述）**：初始化SAC、VLM及缓冲区；每步获得VLM动作先验，采样RL动作执行并存储轨迹；每隔 \( \psi_c \) 步触发一次VLM微调：利用EDDF从缓冲区中筛选高质量样本，使用RALW损失进行LoRA微调，清空缓冲区，并更新微调间隔。

### 3. 实验设计

- **环境与场景**：
  - **CARLA** 自动驾驶模拟器：两个挑战性场景——Highway（#HW，前方最多10辆随机车辆）和 Ghost Pedestrian（#GP，行人从静止车辆后突然穿行）。指标为 episode reward (ER) 和 driving distance (DD)。
  - **DMControl** 机器人控制套件：六个常用任务（Cartpole Swingup、Reacher Easy、Cheetah Run、Walker Walk、Finger Spin、Ball in Cup Catch）。
- **Benchmark 与对比方法**：
  - **纯视觉RL方法**：SAC、DeepMDP、CURL、DrQ、SPR、MLR、PER、ERE、ResAct 等。
  - **仅VLM方法**：VBE。
  - **VLM辅助RL方法**：DPL、APL、VPF、DGC（均为已有工作）。
  - 在DMControl中还对比了Dreamer、PlaNet、SVEA、PlayVirtual、TACO、MADI、PSRL 等当前SOTA。
- **实现细节**：VLM采用Qwen2.5-VL-3B；每个实验使用3个不同随机种子，训练100K步，测试10个episode；报告均值和标准差。

### 4. 资源与算力

论文中**未明确说明**所使用的GPU型号、数量以及具体训练时长。仅提及采用LoRA微调以降低资源消耗，以及“Computing support was provided by Pengcheng Cloudbrain”。因此无法给出具体算力统计。

### 5. 实验数量与充分性

- **主要实验**：在CARLA的2个场景和DMControl的6个任务上进行了性能比较，共8组实验（表1-4）；其中表4对比了16种方法，覆盖多种类别。
- **消融实验**：在CARLA的#HW场景上进行了11组消融（表5），逐一验证EDDF、RALW、Z‑score、累积回报 vs 即时奖励、Q值替换、随机权重等设计的作用。并额外验证了COVR在三种基础算法（SAC、DeepMDP、RAD）上的增益（表3）。
- **充分性与公平性**：实验覆盖多种类型的环境和基线方法，消融设计细粒度，并且都基于相同随机种子和评估协议。标准差的报告增强了结果的可信度。说明实验设计较为充分、客观。

### 6. 主要结论与发现

- COVR在所有测试任务中均取得了最优或接近最优的性能，在CARLA场景下ER和DD显著优于第二好的方法（如ResAct、DGC），在DMControl的六个任务上也全面超越之前的VLM辅助方法。
- 相比单向知识蒸馏（如DPL、APL），双向协作能带来更稳定的性能提升和更小的方差。
- 消融实验表明EDDF和RALW对最终性能贡献显著：动态筛选优于固定比例或随机筛选；累积回报作为筛选指标优于即时奖励或Q值；RALW基于回报加权的损失有效缓解了动作不一致问题。
- 渐进式微调策略提高了训练效率，LoRA适配器保持了较低的资源开销。

### 7. 优点

- **方法创新性**：首次明确提出并实现了VLM与视觉RL之间的双向协作优化，突破了单向蒸馏的局限。
- **模块设计巧妙**：EDDF利用策略熵动态调整样本筛选阈值，兼顾探索初期多样性与后期质量；RALW通过回报权重平稳处理不一致动作，自动回归损失与标签平滑相结合。
- **实验全面扎实**：涵盖自动驾驶和机器人控制两大领域，对比方法丰富（16种以上），消融实验细致，且报告了标准差，结果可靠。
- **实践友好**：采用渐进式微调与LoRA，降低了VLM微调的计算成本；测试时仅需RL策略网络，无需VLM在线推理，满足实时性要求。

### 8. 不足与局限

- **未讨论自身局限**：论文未专门分析COVR的潜在缺点或适用范围，例如对VLM基础能力的依赖（实验中固定使用Qwen2.5-VL-3B，更大或更小模型的影响未探究）。
- **计算成本未量化**：虽然提及渐进式微调和LoRA减少资源消耗，但没有报告与单纯RL训练相比的具体额外开销（GPU hours、显存占用等）。
- **实验环境有限**：仅在CARLA和DMControl上验证，缺少其他常见视觉RL平台（如Atari、MetaWorld）的测试；CARLA场景相对简单（直道、固定行人点），泛化性有待进一步验证。
- **限定动作空间**：方法基于连续动作空间设计（SAC），离散动作或混合动作场景下需调整扩展。
- **潜在的偏差风险**：RL生成的轨迹数据本身存在探索偏差，EDDF的筛选可能进一步强化这种偏差；RALW对高回报样本的过度强调可能使VLM忽视其他有价值的探索行为。

（完）
