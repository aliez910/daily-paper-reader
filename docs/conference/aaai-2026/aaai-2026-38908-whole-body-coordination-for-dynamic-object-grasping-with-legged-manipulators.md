---
title: Whole-Body Coordination for Dynamic Object Grasping with Legged Manipulators
title_zh: 带腿机械臂动态物体抓取的全身协调
authors: "Qiwei Liang, Boyang Cai, Rongyi He, Hui Li, Tao Teng, Haihan Duan, Changxin Huang, Runhao Zeng"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38908/42870"
tags: ["query:rob-il"]
score: 6.0
evidence: 针对动态抓取任务的全身控制
tldr: 该论文针对四足机械臂在动态环境中的抓取问题，提出了DQ-Bench基准和DQ-Net师生框架，实现了全身协调的动态物体抓取。实验表明该方法在多种动态条件下有效，填补了动态抓取 benchmark 的空白。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38908/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1834, \"height\": 808, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38908/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1846, \"height\": 926, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38908/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 889, \"height\": 551, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38908/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1836, \"height\": 502, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38908/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1836, \"height\": 472, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38908/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 876, \"height\": 176, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38908/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1828, \"height\": 339, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38908/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 879, \"height\": 297, \"label\": \"Table\"}]"
motivation: 现有研究多聚焦静态物体抓取，忽略了动态目标，限制了在物流分拣等人机协作场景中的应用。
method: 提出DQ-Bench基准和DQ-Net师生框架，通过全身协调控制实现动态抓取。
result: 在多种动态条件下评估了抓取性能，证明了框架的有效性。
conclusion: 该工作为四足机械臂动态抓取提供了基准和方法，拓展了应用场景。
---

## Abstract
Quadrupedal robots with manipulators offer strong mobility and adaptability for grasping in unstructured, dynamic environments through coordinated whole-body control. However, existing research has predominantly focused on static-object grasping, neglecting the challenges posed by dynamic targets and thus limiting applicability in dynamic scenarios such as logistics sorting and human–robot collaboration. To address this, we introduce DQ-Bench, a new benchmark that systematically evaluates dynamic grasping across varying object motions, velocities, heights, object types, and terrain complexities, along with comprehensive evaluation metrics. Building upon this benchmark, we propose DQ-Net, a compact teacher–student framework designed to infer grasp configurations from limited perceptual cues. During training, the teacher network leverages privileged information to holistically model both the static geometric properties and dynamic motion characteristics of the target, and integrates a grasp fusion module to deliver robust guidance for motion planning. Concurrently, we design a lightweight student network that performs dual-viewpoint temporal modeling using only the target mask, depth map, and proprioceptive state, enabling closed-loop action outputs without reliance on privileged data. Extensive experiments on DQ-Bench demonstrate that DQ-Net achieves robust dynamic objects grasping across multiple task settings, substantially outperforming baseline methods in both success rate and responsiveness. We will release our codebase and benchmark publicly.

---

## 论文详细总结（自动生成）

# 1. 核心问题与整体含义

- **研究动机**：四足机器人加装机械臂后具备优秀的移动性和地形适应能力，但现有研究大多聚焦于静态物体抓取，忽略了物流分拣、人机协作等实际场景中目标持续运动的挑战。动态抓取要求机器人快速感知目标运动并调整自身姿态，同时保持全身稳定。
- **整体含义**：为了填补该领域缺乏标准化评估平台的空白，本文首次提出了专门用于四足机器人动态抓取的基准 DQ-Bench，并基于该基准设计了端到端的全身协调控制框架 DQ-Net，以实现在多种动态难度下稳定高效的抓取。

# 2. 方法论

- **核心思想**：采用**教师-学生蒸馏框架**。教师网络在仿真中利用特权信息（物体真值位姿、速度、点云等）训练出高质量的高层策略；学生网络仅依靠机载传感器（基座与腕部摄像头的深度图和分割掩膜、本体感受）模仿教师输出动作，实现无需特权信息的闭环控制。
- **关键技术细节**  
  - **Grasp Fusion Module (GFM)**：在教师网络前添加。先离线用固定视角下的抓取预测网络生成N个候选抓取姿态，保留top-K作为相对变换存入记忆库。在线时，用当前物体位姿和点云特征构造query，通过注意力机制从记忆库中融合出最适合当前时刻的抓取表示。  
  - **学生网络（DSM）**：采用双流Transformer架构。两个视角（腕部相机、基座相机）各自输入连续三帧的掩膜和深度图，经共享CNN编码得到特征序列，与本体感受嵌入拼接后输入Transformer进行时序建模，最后融合输出高层动作。
  - **动作映射**：高层策略输出末端执行器位置/姿态增量、机身线速度和偏航角速率，通过逆运动学（机械臂）和低层策略网络（四足）转换为关节角度，经PD控制执行。
- **训练流程**：分层训练。先使用PPO训练低层策略并冻结；然后训练高层教师策略；最后用DAgger训练学生策略（最小化动作MSE损失）。

# 3. 实验设计

- **数据集与场景**：基于Isaac Gym仿真环境构建的 **DQ-Bench**，包含四个难度等级：  
  - Level 1：低速（0‑15 cm/s）固定轨迹（线性或弧线）  
  - Level 2：高速（15‑30 cm/s）固定轨迹  
  - Level 3：高速（0‑30 cm/s）随机二维轨迹  
  - Level 4：高速随机三维轨迹（含z轴自由运动）  
  地面为随机不平坦地形，物体初始高度随机采样。物体来自YCB数据集，分为seen（训练/测试）和unseen（仅测试）两组。
- **对比方法**：  
  - VBC（静态抓取基线）  
  - VBC‑D（VBC的动态版本，适应了奖励和角度约束以处理动态抓取）  
  - DQ‑Net w/o GFM（去掉抓取融合模块）  
  - DQ‑Net w/o vel（去掉物体速度输入）  
  所有方法共享同一低层控制策略。
- **评估指标**：抓取成功率（GSR）、一次抓取成功率（OSSR）、完成步数（TSC）。

# 4. 资源与算力

- **说明**：文中明确写道“All training and evaluation are performed on a single NVIDIA RTX 4090 GPU”。  
- **训练配置**：  
  - 教师策略使用6000个并行环境，rollout长度24，总时间步80,000。  
  - 学生策略使用200个并行环境，相同时间步数。  
- **未详细说明**：具体训练时长（如小时数）未给出，但可推断在单卡上可较快完成。

# 5. 实验数量与充分性

- **主要实验**：  
  - 表1：四个难度等级下所有方法的GSR和OSSR，涵盖教师和学生策略。  
  - 表2：学生策略与CNN‑based策略的GSR及参数量对比。  
  - 表3：平均完成步数TSC。  
  - 图3：未见过物体（6种YCB物体）在Level 4下的泛化能力。  
  - 图4、5：定性示例对比。
- **消融实验**：通过移除GFM和速度输入进行消融，证明了这两个组件的重要性。
- **充分性与公平性**：所有方法在相同环境、同一低层策略下评估，视觉输入均加入4帧延迟以模拟真实感知延迟。实验覆盖了不同难度、不同物体类别，并考虑了泛化场景。整体实验设计比较全面、客观。

# 6. 主要结论与发现

- DQ‑Net在四个难度级别上均显著优于VBC‑D等基线，Level 4下学生GSR比VBC‑D高约25%。  
- 抓取融合模块（GFM）和速度信息对于动态场景下的实时位姿预测至关重要，缺少它们会导致GSR下降。  
- 学生网络采用双视角时序Transformer，相比CNN‑based策略，在更少参数（5.37M vs 8.43M）下取得了更高的成功率，证明其对动态信息的建模更有效。  
- 一次抓取成功率（OSSR）表明DQ‑Net决策更果断、适应快速运动的能力更强。  
- 在未见过物体上仍能保持较好性能，显示了良好的泛化能力。

# 7. 优点

- **首创性**：提出了首个针对四足机器人动态抓取的标准化基准（DQ-Bench），为后续研究提供了可复现的比较平台。  
- **方法设计合理**：师生框架结合抓取记忆融合，教师端利用丰富信息学习优质策略，学生端实现轻量化闭环控制，兼顾性能与实用。  
- **双视角时序建模**：融合腕部（细节）与基座（全局）相机信息，并使用时序Transformer增强对运动的理解，设计巧妙。  
- **实验充分**：在多个难度级别和未见过物体上进行了系统评估，消融实验合理，并提供了定性分析，说服力强。

# 8. 不足与局限

- **仅在仿真中验证**：所有实验在Isaac Gym中完成，未在真实机器人上部署，存在仿真到现实（sim‑to‑real）的差距，尤其是视觉感知和物理交互的真实性尚未验证。  
- **任务场景简化**：实验中仅处理单个移动物体，未涉及多物体、密集场景或物体遮挡、变形等更复杂情况。  
- **计算假设**：教师网络依赖真值位姿和点云，在实际中获取这些信息成本高、噪声大；学生网络虽不依赖特权信息，但依赖预训练的分割模型（Track‑SAM）和深度传感器，这些在真实场景下可能不稳定。  
- **机械臂仅使用逆运动学**：未考虑动力学约束和柔顺控制，可能影响与高速运动物体接触时的稳定性。  
- **未见明显偏差分析**：未讨论失败案例的类型分布或对特定物体的系统性偏差。

（完）
