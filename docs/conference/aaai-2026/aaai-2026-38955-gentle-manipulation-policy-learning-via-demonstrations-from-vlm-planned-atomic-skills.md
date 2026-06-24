---
title: Gentle Manipulation Policy Learning via Demonstrations from VLM Planned Atomic Skills
title_zh: 通过来自VLM规划原语技能的演示学习轻柔操作策略
authors: "Jiayu Zhou, Qiwei Wu, Jian Li, Zhe Chen, Xiaogang Xiong, Renjing Xu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38955/42917"
tags: ["query:rob-il"]
score: 8.0
evidence: 从视觉语言模型规划的原语技能中学习轻柔操作演示
tldr: 长时域接触式操作需要大量真实数据和专家知识。该论文提出结合VLM层次化分解、带力约束的RL原语技能以及知识蒸馏的框架，在仿真中训练每个原子技能的RL策略，并利用VLM规划生成演示，最终蒸馏成可部署的策略。实验表明在轻柔操作任务上实现了高成功率且无物体损伤。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1472, \"height\": 883, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 432, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 878, \"height\": 618, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1749, \"height\": 866, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 752, \"height\": 499, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38955/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 870, \"height\": 525, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38955/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 883, \"height\": 118, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38955/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 762, \"height\": 298, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38955/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 816, \"height\": 577, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38955/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1448, \"height\": 225, \"label\": \"Table\"}]"
motivation: 长时域接触式操作需要大量数据且易导致物体损伤。
method: 将任务分解为原子技能，在仿真中训练带力约束的RL策略，并用VLM规划生成演示进行蒸馏。
result: 在轻柔操作任务上实现了高成功率和零损伤。
conclusion: 结合层次化分解和仿真训练可降低真实数据需求并保证安全性。
---

## Abstract
Autonomous execution of long-horizon, contact-rich manipulation tasks traditionally requires extensive real-world data and expert engineering, posing significant cost and scalability challenges. This paper proposes a novel framework integrating hierarchical semantic decomposition, reinforcement learning (RL), visual language models (VLMs), and knowledge distillation to overcome these limitations. Complex tasks are decomposed into atomic skills, with RL-trained policies for each primitive exclusively in simulation. Crucially, our RL formulation incorporates explicit force constraints to prevent object damage during delicate interactions. VLMs perform high-level task decomposition and skill planning, generating diverse expert demonstrations. These are distilled into a unified policy via Visual-Tactile Diffusion Policy for end-to-end execution. We conduct comprehensive ablation studies exploring different VLM-based task planners to identify optimal demonstration generation pipelines, and systematically compare imitation learning algorithms for skill distillation. Extensive simulation experiments and physical deployment validate that our approach achieves policy learning for long-horizon manipulation without costly human demonstrations, while the VLM-guided atomic skill framework enables scalable generalization to diverse tasks.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）
- **核心问题**：长时域、接触丰富的机器人操作任务（如开门、放置物品）传统上依赖大量真实世界数据和专家工程，成本高、扩展性差；且现有方法缺少对接触力的显式考虑，容易造成物体损伤。
- **背景**：模仿学习需要昂贵的人类演示数据；强化学习在长时域任务中奖励函数设计困难；视觉‑语言模型（VLM）可用于任务规划，但普遍未融合触觉和力信息。
- **整体目标**：提出一个自动化框架，在仿真中训练带力约束的原子技能，利用VLM将复杂任务层次分解为技能序列，生成多样化的专家演示，并通过知识蒸馏得到端到端的轻柔操作策略，从而大幅降低对真实人类演示的依赖，实现可扩展、安全的长时域操作。

## 2. 方法论
- **核心思想**：将长时域任务分解为一系列原子技能（atomic skills），每个技能在仿真中用强化学习（RL）训练并显式施加力约束；VLM作为高层规划器根据任务描述和场景图像输出原子技能序列，机器人依次执行技能并采集演示数据；最后通过视觉‑触觉扩散策略（VT‑DP）将多模态数据蒸馏为统一策略。
- **关键技术细节**：
  - **原子技能**：设计五种技能（grasp, rotate, move, horizontal pull, lateral move），每种技能关注特定的力分量（法向力、剪切力、扭矩）。使用Soft Actor‑Critic（SAC）算法在Isaac Gym中训练，奖励函数包含时间惩罚、距离奖励、力惩罚项等，并采用域随机化（物体位姿、质量、摩擦）增强鲁棒性。
  - **数据生成（VASK）**：VLM（如Doubao‑vision‑pro）接收系统提示、任务描述、背景图像，从原子技能库中选择匹配的技能序列；机器人按序执行技能，期间记录视觉点云、触觉点云、接触力等信息；只保留任务成功且接触力较低的轨迹。
  - **策略蒸馏（VT‑DP）**：以DP3为基础，融合视觉点云（256点）和触觉点云（128点），分别编码后输入Transformer扩散模型预测动作序列。使用2步观测预测5步未来动作，操作horizon为8步；训练时100步噪声，推理时10步去噪；模型参数约13.27M，训练约800 epochs。
- **公式或流程**：无复杂公式，突出层次分解→VLM规划→原子技能执行→数据过滤→VT‑DP蒸馏的流水线。

## 3. 实验设计
- **任务与场景**：在Isaac Gym仿真环境中设计4个长时域操作任务：
  - Object Stack (OS)：抓取方块堆叠到平台
  - Open and Place (OP)：打开盒子并将物体放进去
  - Cabinet and Place (CP)：拉开抽屉并将物体放进去
  - Pour Ball (PB)：抓取装有球的杯子，将球倒入碗中
- **机器人系统**：UR5臂 + 两个GelSight Mini触觉传感器 + 平行夹爪 + Intel RealSense D415 RGB-D相机。仿真使用TacSL触觉模型。
- **对比方法**：
  - 演示数据来源比较：VASK+VT‑DP vs. 人类演示+VT‑DP vs. 直接VLM规划（无原子技能）
  - 输入模态比较：视觉点云+触觉点云（VT‑DP） vs. 视觉点云 alone vs. RGB+触觉 vs. RGB alone
  - VLM规划器消融：6种VLM（Doubao‑pro, Doubao‑lite, Qwen系列等）
  - 力感知消融：有无力惩罚项（每个任务10次试验）
- **评价指标**：成功率（SR）、平均成功路径长度（SPL）、平均接触力（ACF）。

## 4. 资源与算力
- 文中仅提及VT‑DP模型训练使用RTX 3060 GPU（推理频率28 Hz），但未说明RL原子技能训练的具体GPU型号、数量或耗时，也未给出VLM推理的资源消耗。**算力信息不充分**。

## 5. 实验数量与充分性
- **消融实验**：
  - VLM规划器消融：6个VLM × 4任务，报告成功率（Tab 2）。
  - 技能消融：4任务对比VASK vs. 直接VLM规划（Tab 3）。
  - 力感知消融：2个策略 × 4任务 × 10次试验，用箱线图展示接触力分布（Fig 5）。
- **方法比较**：
  - 演示数据比较：3种数据源 × 4任务，报告SR、SPL、ACF（Tab 3）。
  - 输入模态比较：4种配置 × 4任务 × 30次试验，报告成功率（Tab 4）。
- **真实世界实验**：定性展示4个任务执行过程（Fig 6），无定量指标。
- **充分性评价**：实验覆盖了框架各关键组件和主要竞争方法，每个条件均有多次独立试验，但缺乏随机种子说明，真实世界部分缺少定量评估。整体较充分。

## 6. 主要结论与发现
- VASK+VT‑DP在成功率和轻柔接触上显著优于所有基线，特别是在复杂任务（CP、OP）上优势明显。
- 使用原子技能比直接VLMR规划路径更稳定、成功率高、接触力更低。
- 力感知奖励有效降低了接触力，促进轻柔操作。
- 视觉+触觉点云融合优于单一模态，且点云比RGB表现更好。
- 合成数据（VASK）质量优于人类演示（人类演示有停顿、不一致），且收集成本低。
- 在真实机器人上成功部署，验证了框架的可行性。

## 7. 优点
- **自动数据生成**：无需昂贵人类演示，通过VLM+原子技能自动产生高质量、带力约束的长时域操作数据。
- **显式力控制**：在RL训练阶段加入力惩罚，确保轻柔操作，避免物体损伤。
- **多模态融合**：VT‑DP融合视觉和触觉点云，兼顾空间感知与接触细节，性能优于单模态方法。
- **层次可扩展**：同一套原子技能可组合成多种任务，易于扩展到新场景。
- **全面消融**：系统评估了VLM选择、技能、力感知、输入模态等组件，验证了设计合理性。

## 8. 不足与局限
- **VLM开销**：VLM推理引入额外计算延迟，可能影响实时性。
- **仿真到真实差距**：虽成功部署，但点云对齐依赖精心设计（数字孪生+后处理），泛化性仍有限。
- **算力信息缺失**：未明确RL训练和VLM推理的详细资源需求，不利于可复现性评估。
- **真实世界评估较弱**：仅定性展示，缺少成功率、力等定量指标。
- **任务多样性有限**：仅4个仿真任务，场景和物体种类不够丰富，泛化能力有待更多验证。
- **VLM依赖**：性能受所选VLM模型影响较大，弱模型（如Qwen2.5‑7b）几乎完全失败。

（完）
