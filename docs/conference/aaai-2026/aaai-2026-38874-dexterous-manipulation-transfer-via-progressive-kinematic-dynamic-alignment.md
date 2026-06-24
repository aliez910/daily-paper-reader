---
title: Dexterous Manipulation Transfer via Progressive Kinematic-Dynamic Alignment
title_zh: 通过渐进运动学-动力学对齐的灵巧操作转移
authors: "Wenbin Bai, Qiyu Chen, Xiangbo Lin, Jw L, Quancheng Li, Hejiang Pan, Yi Sun"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38874/42836"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过渐进对齐将人手操作从视频转移到灵巧机器人轨迹
tldr: 本文针对灵巧操作数据稀缺的问题，提出一种手部无关的操作转移系统，通过渐进式运动学-动力学对齐，将人类手部操作序列从演示视频转换为高质量的灵巧机器人轨迹。该方法无需大量训练数据，有效解决了人机手部差异和高维协调控制的挑战。实验在多种灵巧操作任务上验证了转移效果，展示了一种可扩展的数据生成途径，为灵巧操作策略学习提供了新思路。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 875, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1826, \"height\": 782, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 856, \"height\": 392, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 858, \"height\": 435, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 823, \"height\": 459, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 873, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38874/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 877, \"height\": 275, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38874/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 238, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38874/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 866, \"height\": 145, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38874/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 782, \"height\": 187, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38874/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 598, \"height\": 115, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38874/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 856, \"height\": 188, \"label\": \"Table\"}]"
motivation: 灵巧机器人手数据稀缺，限制了数据驱动策略学习。
method: 设计渐进转移框架，先建立运动学对齐，再进行动力学适配。
result: 在多种灵巧操作任务上验证了转移效果，无需大量训练数据。
conclusion: 提供了一种可扩展的灵巧操作数据生成方法，促进策略学习。
---

## Abstract
The inherent difficulty and limited scalability of collecting manipulation data using multi-fingered robot hand hardware platforms have resulted in severe data scarcity, impeding research on data-driven dexterous manipulation policy learning. To address this challenge, we present a hand-agnostic manipulation transfer system. It efficiently converts human hand manipulation sequences from demonstration videos into high-quality dexterous manipulation trajectories without requirements of massive training data. To tackle the multi-dimensional disparities between human hands and dexterous hands, as well as the challenges posed by high-degree-of-freedom coordinated control of dexterous hands, we design a progressive transfer framework: first, we establish primary control signals for dexterous hands based on kinematic matching; subsequently, we train residual policies with action space rescaling and thumb-guided initialization to dynamically optimize contact interactions under unified rewards; finally, we compute wrist control trajectories with the objective of preserving operational semantics. Using only human hand manipulation videos, our system automatically configures system parameters for different tasks, balancing kinematic matching and dynamic optimization across dexterous hands, object categories, and tasks. Extensive experimental results demonstrate that our framework can automatically generate smooth and semantically correct dexterous hand manipulation that faithfully reproduces human intentions, achieving high efficiency and strong generalizability with an average transfer success rate of 73%, providing an easily implementable and scalable method for collecting robot dexterous manipulation data. Refer to the arXiv version for the appendix.

---

## 论文详细总结（自动生成）

# 详细中文总结

## 1. 论文的核心问题与整体含义（研究动机和背景）

灵巧多指机器人手的硬件平台数据采集难度大、扩展性差，导致**数据严重稀缺**，限制了数据驱动的灵巧操作策略学习。现有方法要么仅依靠运动学映射（缺乏物理交互稳定性），要么依赖强化学习（奖励设计任务特定、探索效率低），难以高效、泛化地将人手操作技能转移至不同灵巧手。  

本文提出**PKDA（Progressive Kinematic-Dynamic Alignment）系统**，目标是从人手演示 RGB 视频出发，自动生成高质量、语义一致的灵巧机器人操作轨迹，**无需大量训练数据**，并**适配多种灵巧手、物体类别和操作任务**，为数据驱动系统提供可扩展的数据生成途径。

## 2. 论文提出的方法论

### 核心思想
融合**运动学匹配**与**动力学优化**的渐进对齐：先通过指尖位置约束建立初步运动学映射，再以强化学习训练残差策略优化接触动力学，最后利用物体轨迹反推手腕运动保持操作语义。

### 关键技术细节（四大模块）

- **Interaction Perceptor（交互感知器）**  
  从原始 RGB 视频中提取人手轨迹 \( H \)（指尖位置+手掌朝向）、物体轨迹 \( O \)（位姿）及指尖接触点 \( C \)。对于已知物体模型的数据集（如 DexYCB、TACO），用 HFL-Net 估计；对于无模型的视频，使用 Hold 联合重建，并对物体网格做凸分解优化。

- **Trajectory Proposer（轨迹提出器）**  
  通过**非线性优化**将人手轨迹重定向至灵巧手关节角序列 \( Q \)。优化目标包含三项：
  - 指尖位置误差 \( E_f \)（世界坐标系下人手与灵巧手对应指尖的距离）
  - 手掌朝向误差 \( E_o \)（测地线距离）
  - 时间平滑项 \( E_s \)（惩罚相邻帧过大变化）  
  不依赖手指‑手腕向量，改用**指尖绝对位置**，降低对手形态差异的敏感性。  
  优化后的关节角序列通过逆动力学转换为初步控制信号 \( A_{\text{primary}} \)。

- **ContactAdapt Optimizer（接触自适应优化器）**  
  利用强化学习（RL）训练残差策略，修正 \( A_{\text{primary}} \) 以优化手‑物交互动力学。关键设计：
  1. **RL-Configurator**：跨任务统一奖励配置。从 \( A_{\text{primary}} \) 中选取**拇指尖端最接近对应接触点且无碰撞**的状态作为预抓取初始状态；将所有任务抽象为“拾起”阶段，以物体首次偏离初始位置 0.1m 的位姿为目标。
  2. **动作空间缩放**：将手腕运动范围压缩到预抓取状态的邻域 \( \mathcal{N}(\hat{q}_{\text{pre}}, \rho) \) 内，手指关节保持全范围运动，减少无效探索、防止手腕过度驱动。
  3. **统一奖励函数**：分层设计——接近奖励（引导指尖靠近目标接触点）、抓取奖励（接触奖励+模仿奖励，接触容忍阈值 0.06m）、提升奖励（拇指与另一指接触后引导物体至目标位姿）。无需任务特定调参。

- **Wrist Trajectory Planner（手腕轨迹规划器）**  
  假设稳定抓取后手‑物无相对滑动，利用 RL 结束时物体位姿 \( o_{\text{grasp}} \) 与稳定抓取时手腕位姿 \( T_{\text{grasp}} \)，反算全局手腕轨迹 \( T_t = o_t \cdot (T_{\text{grasp}}^{-1} \cdot o_{\text{grasp}})^{-1} \)，并通过 PD 控制器驱动，保留完整操作语义（如“升起‑倾斜‑放下”）。

整个流程无需任务特定参数调整，系统自动配置。

## 3. 实验设计

### 使用的数据集 / 场景

| 场景 | 数据源 | 数量 | 说明 |
|------|--------|------|------|
| **全信息场景** | GRAB 数据集 | ~600 条人手单侧交互轨迹 | 精确手位姿、物体位姿、接触标注 |
| **模型已知视觉场景** | DexYCB、TACO | 各 10 条 | 单目 RGB 视频，物体 3D 模型已知 |
| **模型未知视觉场景** | 自拍视频（日常物体） | 5 种操作任务 | 仅 RGB 视频，无物体模型 |
| 跨手测试 | 同一数据集（40 条 TCDM 任务） | Adroit / Allegro / Leap Hand | — |
| 真实世界 | UR10 + Leap Hand | 3 类任务（Shake、Pour、Stamp） | 仿真轨迹直接开环执行 |

### Benchmark 与对比方法

对比方法：
- **Anyteleop**（Qin et al. 2023）：纯运动学重定向（Retarget‑only）。
- **PGDM**（Dasari, Gupta, Kumar 2023）：使用预抓取姿态初始化 RL，以物体轨迹作为强约束（需精确轨迹跟踪）。
- **D-Grasp**（Christen et al. 2021）：以单帧抓取姿态为参考，专门设计奖励函数。
- *PKDA-P*：在 TCDM 任务子集（40 条）上的结果。
- *PKDA-F*：在全量 GRAB（600 条）上的结果。

### 评估指标

- **SR Grasp (%)**：抓取成功率（物体能保持在目标位置 0.05m 内）。
- **SR Follow (%)**：跟随成功率（整个操作过程中不掉落）。
- **Ep (m)**：物体平移偏差（平均欧氏距离）。
- **Er (°)**：物体旋转偏差（平均测地线距离）。
- **TSR (%)**：转移成功率（意图层面的一致性，见附录 B.1）。

## 4. 资源与算力

文中**未明确说明**使用的 GPU 型号、数量及训练时长。摘要末尾提及附录（arXiv 版）可能包含更多细节，但本文本未提供。因此无法总结具体算力开销。

## 5. 实验数量与充分性

- **全信息场景**：约 600+40 条轨迹，覆盖 GRAB 及 TCDM 任务子集。
- **视觉感知场景**：共 20 条（DexYCB ×10 + TACO ×10）+ 5 条自拍视频，样本量较小但用于验证鲁棒性。
- **跨手实验**：在 40 条 TCDM 任务上测试三种灵巧手，结果合理。
- **消融实验**：
  - 重定向方法（指尖‑手腕向量 vs. 指尖绝对位置）。
  - 预抓取选择策略（拇指/食指/中指引导 + 触发时机 Nearest / 0.05m / 0.1m）。
  - 动作空间缩放（有无对比）。
- **真实世界**：3 类任务，定性验证可行性。

**实验充分性评价**：  
多场景、多手、多基线的对比较为全面；消融实验覆盖了框架的核心设计组件，结论明确。但视觉场景（尤其是模型未知）的样本量较少（5 个任务），可能限制泛化性的统计显著性。对比实验仅在 TCDM 任务上同时比较了 PGDM 与 PKDA-P，而 D-Grasp/Anyteleop 也在全信息场景下做了更广泛的比较，整体公平性良好。

## 6. 论文的主要结论与发现

1. **PKDA 在多种场景下均取得高转移成功率**：全信息场景 PKDA‑F TSR 达 73.3%，TCDM 子集 PKDA‑P 达 77.5%，优于 PGDM（72.5%）、D-Grasp（57.5%）、Anyteleop（7.5%）。
2. **学习效率更高**：相比 PGDM，PKDA 在更少 RL 步数内达到更高成功率（图 4）。
3. **鲁棒性良好**：在视觉感知不准确（位姿估计误差、物体重建缺陷）时，TSR 仍不低于 70%，表明策略对输入噪声具有抵抗能力。
4. **跨手适应能力强**：Adroit（77.5%）、Allegro（72.5%）、Leap（67.5%）成功转移，运动学差异大但位置/旋转偏差稳定，说明功能对齐优先于硬件特定调参。
5. **核心组件不可或缺**：消融实验证实**指尖绝对位置映射**优于指尖‑手腕向量；**拇指引导 + Nearest 触发 + 动作空间缩放**为最佳组合，移除动作缩放后 TSR 从 77.5% 骤降至 37.5%。
6. **真实世界可行性**：仿真生成轨迹在真实机器人上开环执行可复现操作意图（Shake、Pour、Stamp）。

## 7. 优点

- **渐进式对齐框架**：巧妙结合运动学匹配的高效初始化与强化学习的动力学优化，形成互补。
- **手部无关性**：指尖重定向基于空间几何而非拓扑结构，且手腕轨迹由相对关系驱动，只需指定手指对应关系即可适配不同灵巧手，无需调整整体参数。
- **统一奖励与自动配置**：RL-Configurator 提取跨任务共性（“拾起”目标），统一奖励无需任务特定设计，降低使用门槛。
- **动作空间缩放**：针对手腕和手指的不同探索特性设计了压缩策略，显著提升探索效率，防止手腕过度驱动。
- **端到端视频输入**：仅需单目 RGB 视频，无需在线人手参与或复杂穿戴设备，系统自动完成感知、规划、优化全流程。
- **实验验证充分**：覆盖多种信息条件、多手、多任务、真实场景，消融清晰，对比公平。

## 8. 不足与局限

- **操作类型限制**：论文明确指出主要处理**相对稳定的手‑物接触模式**，对于频繁改变多个接触点的动态操作（如旋转、灵巧重抓取等）尚未探索，未来工作需进一步扩展。
- **依赖视觉感知质量**：虽然实验表明对感知误差有一定鲁棒性，但视觉估计（尤其无物体模型时）误差仍然可能导致预抓取不理想。自拍视频场景仅 5 个任务，样本量有限。
- **物体尺寸敏感**：大型灵巧手（Allegro、Leap）对小型/细长物体（如锤子）转移成功率较低，硬件机构差异带来自然局限。
- **真实实验控制有限**：真实世界实验仅 3 个任务，且采用开环执行，未进行闭环调整或 Sim2Real 域适应讨论。
- **计算资源信息缺失**：未报告训练 RL 所需的 GPU 型号、数量及时间，可复现性信息不足。
- **对比方法覆盖**：PGDM 仅能在 TCDM 子集上比较（40 个任务），且重定向部分 Anyteleop 纯运动学方法成功率极低，基线优势明显。

（完）
