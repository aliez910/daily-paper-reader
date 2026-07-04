---
title: "PDFactor: Learning Tri-Perspective View Policy Diffusion Field for Multi-Task Robotic Manipulation"
title_zh: PDFactor：面向多任务机器人操纵的三视角策略扩散场学习
authors: "Tian, Jingyi, Wang, Le, Zhou, Sanping, Wang, Sen, Li, Jiayi, Sun, Haowen, Tang, Wei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Tian_PDFactor_Learning_Tri-Perspective_View_Policy_Diffusion_Field_for_Multi-Task_Robotic_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于扩散场的策略将视觉与语言映射为多任务操纵动作
tldr: 多任务机器人操纵中，视觉与语言驱动的动作分布难以兼顾精度与效率。本文提出 PDFactor，将三维点云分解为三正交特征平面，并利用三视角 Transformer 构建与观测对齐的潜在扩散场，表示 6-DoF 动作概率分布。该方法在多任务操纵基准上验证了精度与效率的平衡。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 833, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1764, \"height\": 585, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1809, \"height\": 583, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 784, \"height\": 461, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1777, \"height\": 452, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 774, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 774, \"height\": 251, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1806, \"height\": 938, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1800, \"height\": 249, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-tian-pdfactor-learning-tri-perspective-view-policy-diffusion-field-for-multi-task-robotic-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 863, \"height\": 327, \"label\": \"Table\"}]"
motivation: 多任务操纵需在精度与效率间权衡动作分布建模方式。
method: 提出三视角混合表征与潜在扩散场，用于 6-DoF 动作分布建模。
result: 在多任务操纵基准上兼顾了精度与推理效率。
conclusion: 为多任务视觉语言操纵策略提供了高效的概率建模方法。
---

## Abstract
Robotic manipulation based on visual observations and natural language instructions is a long-standing challenge in robotics. Yet prevailing approaches model action distribution by adopting explicit or implicit representations, which often struggle to achieve a trade-off between accuracy and efficiency. In response, we propose PDFactor, a novel framework that models action distribution with a hybrid triplane representation. In particular, PDFactor decomposes 3D point cloud into three orthogonal feature planes and leverages a tri-perspective view transformer to produce dense cubic features as a latent diffusion field aligned with observation space representing 6-DoF action probability distribution at an arbitrary location. We employ a small denoising network conceptually as both a parameterized loss function measuring the quality of the learned latent features and an action gradient decoder to sample actions from the latent diffusion field during inference. This design enables our PDFactor to benefit from spatial awareness of explicit representation and arbitrary resolution of implicit representation, rendering it with manipulation accuracy, inference efficiency, and model scalability. Experiments demonstrate that PDFactor outperforms state-of-the-art approaches across a diverse range of manipulation tasks in RLBench simulation. Moreover, PDFactor can effectively learn multi-task policies from a limited number of human demonstrations, achieving promising accuracy in a variety of real-world manipulation tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "PDFactor: Learning Tri-Perspective View Policy Diffusion Field for Multi-Task Robotic Manipulation" in Markdown format. I need to cover 8 specific points and end with "（完）".

Let me organize this carefully based on the paper content:

1. Core problem and meaning - the paper addresses multi-task robotic manipulation with visual observations and language instructions, the trade-off between accuracy and efficiency in action distribution modeling
2. Methodology - hybrid triplane representation + latent diffusion field, tri-perspective view transformer, small denoising MLP, score matching loss
3. Experiments - RLBench 18 tasks, real world 6 tasks, compared with C2F-ARM, PerAct, Act3D, 3D Diffuser Actor, RVT, RVT-2
4. Resources - 8 NVIDIA RTX 3090 GPUs, ~30k iterations, batch size 256
5. Experimental scale and adequacy - many experiments, ablations, scalability tests
6. Main conclusions - outperforms SOTA by 5.9%, 10x faster than diffusion baselines
7. Strengths - hybrid representation, efficiency, scalability
8. Limitations - still needs many diffusion steps for high precision, real-world only 6 tasks

Let me write this in a structured, concise but comprehensive Markdown format.</think>

# PDFactor 论文总结

## 1. 核心问题与整体含义

- **研究背景**：基于视觉观测与自然语言指令的多任务机器人操纵是具身智能与机器人学的长期挑战。现有端到端模仿学习方法通常依赖大量人类演示数据，且泛化能力较差。
- **核心问题**：当前动作分布建模方式存在两难——**显式策略**（如体素/点云 action value map）易于空间对齐但难以处理连续高维动作；**隐式策略**（基于能量模型或扩散模型）能建模连续多模态分布，但依赖大型去噪网络与迭代推理，效率与精度难以兼顾。
- **研究目标**：设计一种能在空间感知、推理效率与模型可扩展性之间取得平衡的混合动作表征方法，以支持语言条件下的多任务 6-DoF 操纵。

---

## 2. 方法论

### 核心思想
- 提出 **Policy Diffusion Field（策略扩散场）**：一种混合显式–隐式动作表征，将动作分布显式锚定到三维观测空间，并以小型网络解码动作分数梯度，从而兼具显式方法的空间感知与隐式方法的任意分辨率与多模态建模能力。

### 关键技术细节
- **三视角特征投影（Tri-Perspective View Projection）**：将多视角 RGB-D 图像构造成点云后，投影并通过可学习的卷积 + Max-Pool 生成三个正交 2D 特征平面（俯视、前后、左右），避免重渲染带来的遮挡问题。
- **三视角 Transformer**：将三平面特征与语言（CLIP）token、机器人本体感知 token 拼接；通过 **3D 旋转位置编码（RoPE）** 显式编码三维相对位置；以 **Adaptive Layer Norm（AdaLN）** 注入本体感知，输出稠密的三平面潜在特征。
- **特征聚合与查询**：对任意 3D 位置 (x, y, z)，通过其在三平面上的投影做双线性插值并求和，得到潜在向量 z，作为该位置的 6-DoF 动作分布隐式表征。
- **Score Matching Loss（评分匹配损失）**：将扩散模型原理引入到位置级 z 上——
  - 训练目标：以小型残差 MLP 作为去噪网络 ε_θ(a_t, z)，预测噪声 ε；等价于在评分函数 s_θ(a_t, t, z) 上的 score matching。
  - 推理：通过 DDPM 反向过程从高斯噪声迭代采样 6-DoF 末端位姿，z 由当前噪声动作所在位置聚合并随去噪步骤更新。
  - 设计哲学：小型 MLP 同时充当“衡量潜在特征质量的参数化损失函数”和“动作梯度解码器”。
- **辅助预测**：夹爪开合与碰撞状态通过 z 的 MLP 头以二元交叉熵预测。
- **模型规模**：提供 T/S/B 三个变体（16M / 34M / 83M 参数），另设计两阶段“缩放后再预测”的 PDFactor-2。

### 公式要点
- 评分匹配目标：L_pose = E[‖ε − ε_θ(a_t|t, z)‖²]，其中 z = AggregatedTriplane(x,y,z)。
- DDPM 反向公式：a_{t−1} = (1/√α_t)[a_t − (1−α_t)/√(1−ᾱ_t) ε_θ] + σ_t δ。

---

## 3. 实验设计

### 数据集 / 场景
- **仿真**：RLBench 基准（CoppelaSim + Franka Panda + 4 个 128×128 RGB-D 相机），18 个任务，每个任务 100 条演示训练 / 25 条测试，按 PerAct 设置复现。
- **真实世界**：6 个桌面任务（put fruit、push buttons、stack cups、stack blocks、sort cylinder、put mustard），UR5 + Azure Kinect，每任务 15 条人工演示，每个任务 10 次评估回合。

### 对比方法
- **显式/类别式**：C2F-ARM-BC、PerAct、Act3D、RVT、RVT-2
- **隐式/扩散式**：3D Diffuser Actor
- 评测指标为任务成功率（%），取 5 个随机种子的均值±标准差，并给出平均排名。

### 评估维度（消融）
- 8 类任务挑战分类：planning、tools、long-horizon、rotation、motion、multimodal、precision、occlusion
- 多种设计选择：是否使用 3D RoPE、是否使用 feature projection（vs. RVT 的 point rendering）、去噪 MLP 深度、模型规模、数据规模（10/25/50/100）、扩散采样步数。

---

## 4. 资源与算力

- **硬件**：8 块 NVIDIA RTX 3090 GPU
- **优化**：AdamW，初始学习率 2.5×10⁻⁴，余弦退火 + 前 2k 步 warmup，batch size 256
- **训练时长**：仿真模型约 30k 次迭代；真实世界模型 10k 次迭代
- **SE(3) 数据增强** 应用于点云
- 论文正文中未单独报告 GPU 时长与模型 FLOPs，仅给出参数量与 FPS 形式的推理速度对比。

---

## 5. 实验数量与充分性

- **主表结果**：RLBench 18 任务 × 5 seeds ≈ 180+ 仿真回合/任务，附标准差，统计性较强。
- **可扩展性实验**：模型规模（T/S/B/2）与数据规模（10/25/50/100 demos）独立测试，含学习曲线。
- **消融实验**：4 项架构消融（diffusion transformer 基线、无 3D RoPE、无 feature projection、不同 MLP 深度），系统性较强。
- **推理效率分析**：扫描 10–100 扩散步数，对比 3D Diffuser Actor 的成功率与 FPS。
- **真实世界**：6 任务 60 episode 总评估，与 3DA、RVT-2 直接对比。
- **总体评价**：实验覆盖较全面，含仿真+真实、消融+扩展性+效率维度，对比基线较新且公平；不过真实世界任务数较少且使用单一物体放置/堆叠类，泛化结论仍受限。

---

## 6. 主要结论与发现

- 在 RLBench 18 任务上平均成功率达 **87.3%**，比此前 SOTA RVT-2 绝对提升 **5.9%**，并取得最低平均排名 1.6。
- 即使最小的 PDFactor-T（16M）仍具竞争力；PDFactor-2 借助两阶段预测提升精细任务表现（如 place cups 从 39.2 → 64.0）。
- 推理速度相比现有扩散策略（如 3D Diffuser Actor）**提升约 10×**，与显式方法 RVT 相当甚至更快。
- 架构设计均带来显著增益：3D RoPE +6.9%、feature projection +9%、小型 denoising MLP（3 层）即可获得 84.0% 成功率，模型越大对多模态任务越友好。
- 真实世界 6 任务平均成功率 **47/60**，显著优于 3D Diffuser Actor（31/60）和 RVT-2（38/60）。
- 仿真与真实均验证了“显式空间感知 + 隐式扩散解码”的混合表征在精度与效率间的有效性。

---

## 7. 优点

- **混合表征创新**：首次将 triplane + diffusion field 结合用于 6-DoF 动作分布建模，避免了大体素 grid 与大型去噪网络的负担。
- **空间对齐设计**：动作空间直接锚定到三平面特征，做到“所见即所动作”，简化了状态–动作映射。
- **效率优势**：小型 denoising MLP + 可查询特征，使扩散推理只需前向数百次查询而非大数据网络迭代。
- **可扩展性良好**：模型与数据规模提升均带来稳定收益，便于未来扩展到更大模型/数据。
- **实证充分**：仿真 SOTA + 真实世界泛化 + 多维度消融同时进行。
- **2D 投影避免遮挡**：相比 RVT 的 image re-rendering，直接对点特征做投影缓解了机械臂自遮挡问题。

---

## 8. 不足与局限

- **采样步数依赖**：作者承认取得更高精度仍需较多扩散步数，未与最新的少步/一致性蒸馏技术结合。
- **真实世界评估有限**：仅 6 个任务、单一工位、UR5 + MoveIt! BiRRT，任务结构相对简单且偏向桌面 pick-and-place 变体，未涉及更复杂接触式或杂乱场景。
- **演示数据量小**：真实任务仅 15 条/任务，缺少不同光照/物体/演示者等扰动下的鲁棒性测试。
- **训练开销披露不充分**：未明确报告总 GPU 时长、单次训练能耗或部署到不同机械臂的迁移成本。
- **失败分析与安全约束**：对失败模式、碰撞状态预测有效性、对抗性扰动等未做深入分析，存在一定偏差与安全风险讨论空白。
- **与新兴 3D 表征的对比缺失**：未与 3D Gaussian Splatting（如 ManiGaussian、 GNFactor）等近期 3D 神经场基线直接比较。
- **公式可解释性有限**：score matching loss 作为“特征质量的参数化损失”这一说法较新颖，但对 z 的可解释性与失败情形缺乏可视化分析。

（完）
