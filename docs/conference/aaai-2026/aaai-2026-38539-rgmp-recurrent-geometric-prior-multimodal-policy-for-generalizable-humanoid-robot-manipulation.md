---
title: "RGMP: Recurrent Geometric-prior Multimodal Policy for Generalizable Humanoid Robot Manipulation"
title_zh: RGMP：面向可泛化人形机器人操纵的循环几何先验多模态策略
authors: "Xuetao Li, Wenke Huang, Nengyuan Pan, Kaiyan Zhao, Songhua Yang, Yiming Wang, Mengde Li, Mang Ye, Jifeng Xuan, Miao Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38539/42501"
tags: ["query:rob-il"]
score: 9.0
evidence: 端到端几何语义技能推理的人形机器人操纵
tldr: 现有人形机器人操纵方法依赖大量训练数据且忽略几何推理，导致泛化性差。本文提出RGMP，一个端到端框架，融合几何语义技能推理与数据高效的视觉运动控制。通过循环几何先验多模态策略，该方法显式建模机器人-目标关系，在未见场景中具备更强的泛化能力。实验表明，RGMP在多项操纵任务上以更少训练数据取得了更优性能。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 872, \"height\": 641, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1830, \"height\": 929, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 861, \"height\": 682, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1837, \"height\": 359, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 873, \"height\": 395, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38539/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1832, \"height\": 419, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38539/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1741, \"height\": 545, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38539/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 856, \"height\": 329, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38539/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 855, \"height\": 258, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38539/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 763, \"height\": 224, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38539/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 678, \"height\": 155, \"label\": \"Table\"}]"
motivation: 现有方法忽略几何推理且建模效率低，需要大量训练数据才能实现鲁棒的多模态决策。
method: 提出循环几何先验多模态策略（RGMP），端到端统一几何语义推理与视觉运动控制，高效建模机器人-目标关系。
result: 在多个操纵任务上，RGMP以更少数据实现更高成功率和更好的泛化性。
conclusion: 融入几何先验能够提升数据效率与泛化能力，为通用人形机器人操纵提供有效框架。
---

## Abstract
Humanoid robots exhibit significant potential in executing diverse human-level skills. However, current research predominantly relies on data-driven approaches that necessitate extensive training datasets to achieve robust multimodal decision-making capabilities and generalizable visuomotor control. These methods raise concerns due to the neglect of geometric reasoning in unseen scenarios and the inefficient modeling of robot-target relationships within the training data, resulting in a significant waste of training resources. To address these limitations, we present the Recurrent Geometric-prior Multimodal Policy (RGMP), an end-to-end framework that unifies geometric-semantic skill reasoning with data-efficient visuomotor control. For perception capabilities, we propose the Geometric-prior Skill Selector, which infuses geometric inductive biases into a vision language model, producing adaptive skill sequences for unseen scenes with minimal spatial common sense tuning. To achieve data-efficient robotic motion synthesis, we introduce the Adaptive Recursive Gaussian Network, which parameterizes robot-object interactions as a compact hierarchy of Gaussian processes that recursively encode multi-scale spatial relationships, yielding dexterous, data-efficient motion synthesis even from sparse demonstrations. Evaluated on both our humanoid robot and desktop robot, the RGMP framework achieves 87% task success in generalization tests and exhibits 5× greater data efficiency than the state-of-the-art model. This performance underscores its superior cross-domain generalization, paving the way for more versatile and data-efficient robotic systems.

---

## 论文详细总结（自动生成）

# 论文详细总结：RGMP: Recurrent Geometric-prior Multimodal Policy for Generalizable Humanoid Robot Manipulation

## 1. 核心问题与整体含义（研究动机和背景）

- **研究问题**：现有人形机器人操纵方法高度依赖大规模数据驱动的策略（如扩散模型、Transformer），在面对未见过的场景和物体时，由于缺乏对几何关系的显式推理以及对机器人‑目标空间交互的低效建模，导致泛化能力不足、数据利用率低。
- **核心挑战**：
  - 如何使机器人具备空间‑几何推理能力，从而在语义理解与技能选择之间建立可靠关联（技能选择问题）；
  - 如何从极少量演示中学习到可泛化的运动控制策略，避免过拟合（数据效率问题）。
- **整体意义**：论文旨在构建一个端到端框架，统一几何‑语义推理与数据高效的视觉运动控制，在提升泛化能力的同时大幅减少所需训练数据量，为人形机器人在真实场景中的灵活部署提供新思路。

## 2. 方法论：核心思想、关键技术细节与算法流程

- **整体架构**：RGMP 是一个端到端框架，包含两大核心模块——**几何先验技能选择器（GSS）** 和**自适应递归高斯网络（ARGN）**。
  - GSS 负责将人类指令与视觉观察转化为具体可执行技能（如抓取、捏取、提起），ARGN 负责根据视觉输入预测精确的关节动作。

- **几何先验技能选择器（GSS）**：
  - 借助预训练的 VLM（Qwen-VL）理解用户指令并定位目标物体（输出边界框）。
  - 结合边界框信息与 YOLOv8n-seg 提供的物体形状信息（几何先验），再注入一组轻量的几何常识规则（约 20 条），指导 VLM 从预定义的技能库中选择最合适的技能。
  - 核心公式：\(P = \text{plan}(I, O \mid C)\)，其中 \(I\) 为指令，\(O\) 为观测，\(C\) 为包含几何先验的上下文。
  - 实现方式为 in‑context learning，无需额外微调 VLM，仅需低秩几何适配器。

- **自适应递归高斯网络（ARGN）**：
  - **动机**：以往方法难以从有限数据中建模全局空间关系；递归计算虽能建立长距离依赖，但易出现梯度消失。
  - **关键技术**：
    1. **自适应衰减机制（ADM）**：根据输入特征生成内容感知的衰减因子 \(W\)，控制历史记忆的遗忘速度，避免关键空间信息丢失。
    2. **旋转位置编码（RoPE）**：为图像块注入相对位置信息，增强空间方向敏感性。
    3. **递归空间混合块**：将序列化为 \(16\times16\) 的图像块的 \(K_s\) 与 \(V_s\) 递归处理，累积全局空间记忆：
       \[
       W_{KV_i} = \frac{n_i + e^u \odot k_i \odot v_i}{d_i + e^u \odot k_i},
       \quad n_i = n_{i-1} \odot e^{-W} + k_i \odot v_i,
       \quad d_i = d_{i-1} \odot e^{-W} + k_i
       \]
       其中 \(u\) 为可学习的局部位置补偿，\(W\) 由 ADM 生成。
    4. **通道混合块**：在通道维度上重分配特征响应。
    5. **多尺度融合**：三个阶段的输出通过可学习权重 \(\alpha_i\) 融合。
    6. **高斯混合模型（GMM）**：将初始预测动作 \(a_{\text{in}}\) 与 6 个高斯分量（对应六自由度关节）进行匹配，选择最近的聚类中心作为最终动作 \(a^*\)，从而避免回归到均值，保留多模态动作分布。

- **算法流程**：
  - 训练阶段：采集演示数据 \((J, O)\) → 通过 Stem 层提取初始特征 \(F_0\) → 三个阶段的 ARGN 块提取多尺度特征 → 多尺度融合 → 线性层输出初始动作 \(a_{\text{in}}\) → MSE 损失；同时利用 EM 算法估计 GMM 参数。
  - 推理阶段：VLM 定位目标并选择技能 → ARGN 根据当前视觉观测输出动作 → 通过 GMM 选择最优动作执行。

## 3. 实验设计

- **数据集/场景**：
  - 真实世界：两种平台——人形机器人（上肢）和桌面双臂机器人（6‑DoF 关节）。技能库包含 120 条真实演示轨迹，对应抓取、捏取、提起等技能。
  - 模拟器：ManiSkill2 环境，包含 5 个任务：推椅子、搬桶、插充电器、开柜门、开抽屉。
- **Benchmark 与方法**：对比了以下方法：
  - 视觉编码器：ResNet50；序列模型：Transformer；竞赛方案：ManiSkill2‑1st；通用策略：Octo、OpenVLA、RDT‑1b、Dex‑VLA；当前 SOTA：Diffusion Policy。
- **评估指标**：
  - \(Acc_s\)：技能选择正确率；\(Acc_t\)：动作执行精度；综合成功率 \(Acc = Acc_s \times Acc_t\)。
- **实验设置**：
  - 主要泛化实验：仅用 40 条 Fanta 罐抓取演示训练，测试 Fanta（已见）、Coke、喷雾瓶、人手（均为未见物体）在随机位置下的抓取成功率。
  - 消融实验：GSS vs 直接使用 Qwen‑VL；ARGN vs 不加 GMM；组件消融（RoPE、SMB、CMB）；数据效率对比（40～200 条训练样本）。
  - 模拟器任务：评估在非抓取任务上的迁移能力。

## 4. 资源与算力

- 论文未明确说明所使用的 GPU 型号、数量或训练时长，仅在致谢中提及武汉大学超算中心提供计算支持。
- 因此，无法量化具体的算力消耗，但文中强调 RGMP 在数据效率上显著优于扩散策略（仅需 40 条演示即可达到 0.98 成功率），可推测其训练开销相对较低。

## 5. 实验数量与充分性

- **实验数量**：主要进行了五类实验：
  1. 真实机器人泛化实验（5 种物体 × 20 次随机放置）。
  2. 模拟器任务（5 种 ManiSkill2 任务）。
  3. GSS 消融（两种视觉编码器 + 三种动作网络 + Diffusion Policy 组合）。
  4. ARGN 与 GMM 消融。
  5. 组件消融（RoPE、SMB、CMB）及数据效率对比。
- **充分性与客观性**：
  - 实验覆盖了从真实场景到模拟器的多种设置，对比了 8 种以上代表性方法，且所有方法均在相同数据集上训练/测试。
  - 消融实验系统，验证了每个提出的组件（GSS、ARGN、GMM）的贡献。
  - 跨物体/场景的泛化测试有力证明了模型的泛化能力。
  - 但真实实验仅涉及有限的物体类别和技能，且人形机器人的实验仅集中于上肢，平台多样性仍有提升空间。

## 6. 主要结论与发现

1. **性能领先**：RGMP 在真实机器人泛化测试中达到 87% 的综合成功率，远高于 Diffusion Policy 的 70% 以及同期 SOTA 方法（Dex‑VLA 77%）。
2. **数据效率极大提升**：仅需 40 条演示即可达到 0.98 成功率，是 Diffusion Policy 所需 200 条演示的 **5 倍效率提升**。
3. **几何先验有效**：GSS 相比原始 VLM 在技能选择上提升 15‑25 个百分点，证明了融入轻量几何常识的有效性。
4. **递归高斯网络稳健**：ARGN + GMM 的组合优于单一高斯输出，能够从稀疏演示中捕捉多模态动作分布，避免过拟合。

## 7. 优点

- **创新性融合**：首次将几何先验显式注入 VLM 进行技能选择，并提出递归高斯网络实现数据高效运动合成，思路新颖。
- **即插即用**：GSS 的几何规则仅 20 条，且无需大规模微调 VLM，易于迁移到其他机器人。
- **全面真实验证**：在两种物理平台（人形机器人 + 桌面双臂机器人）上验证，增强了结论的可靠性。
- **系统消融**：对每个模块进行了精细的消融，清晰展示了各组件贡献。
- **显著提升效率与泛化**：以极少数据量超越现有方法的泛化能力，对实际部署具有重要价值。

## 8. 不足与局限

- **计算资源未透明**：未报告 GPU 型号、训练时间、参数规模等，不利于重复性与公平对比。
- **几何先验的局限性**：20 条规则由人工定义，可能无法覆盖所有场景的几何约束，且依赖 YOLO 的形装检测精度。
- **技能库规模有限**：仅包含抓取、捏取、提起三种原子技能，复杂任务（如开柜门）需要动态组合，但论文并未展示完整的多技能组合学习（仅在模拟器中显示部分结果）。
- **平台与任务覆盖**：真实实验中的物体种类较少（罐装饮料、纸巾、人手等）且仅在两种设定下测试，人形机器人未进行全身运动（如移动、蹲下等），泛化范围仍有限。
- **仅依赖 RGB**：未显示使用深度或多视角信息对环境进行显式重建，部分极端光照或遮挡场景效果可能下降。
- **潜在偏差风险**：训练数据仅包含 120 条轨迹，可能不足以完全消除场景偏置。

（完）
