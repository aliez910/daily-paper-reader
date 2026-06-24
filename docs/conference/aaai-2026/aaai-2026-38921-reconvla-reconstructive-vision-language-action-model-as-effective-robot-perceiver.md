---
title: "ReconVLA: Reconstructive Vision-Language-Action Model as Effective Robot Perceiver"
title_zh: "ReconVLA: 重构式视觉-语言-动作模型作为有效的机器人感知器"
authors: "Wenxuan Song, Ziyang Zhou, Han Zhao, Jiayi Chen, Pengxiang Ding, Haodong Yan, Yuxin Huang, Feilong Tang, Donglin Wang, Haoang Li"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38921/42883"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过重构式感知增强的视觉-语言-动作模型用于机器人控制
tldr: 针对当前视觉-语言-动作(VLA)模型视觉注意力分散、难以聚焦目标区域的问题，提出了ReconVLA模型。该模型引入隐含的注意力引导范式，通过扩散变换器重建图像中的注视区域，迫使模型学习细粒度表示并准确分配注意力。实验证明ReconVLA在多种机器人操控任务中显著提升了任务成功率和泛化能力，为VLA模型的感知增强提供了有效方案。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 870, \"height\": 569, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 286, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1569, \"height\": 812, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1832, \"height\": 503, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 812, \"height\": 505, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38921/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1741, \"height\": 377, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38921/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 850, \"height\": 293, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38921/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1240, \"height\": 277, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38921/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1760, \"height\": 554, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38921/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1778, \"height\": 342, \"label\": \"Table\"}]"
motivation: 现有VLA模型视觉注意力分散，无法聚焦目标区域，导致操控性能受限。
method: 提出ReconVLA，利用扩散变换器重建注视区域以隐式引导视觉注意力。
result: 在多个操控基准上，ReconVLA在成功率和泛化性上均超越现有VLA模型。
conclusion: 重构式注意力引导有效增强了VLA模型的感知能力，提升了操控表现。
---

## Abstract
Recent advances in Vision-Language-Action (VLA) models have enabled robotic agents to integrate multimodal understanding with action execution. However, our empirical analysis reveals that current VLAs struggle to allocate visual attention to target regions.
Instead, visual attention is always dispersed. To guide the visual attention grounding on the correct target, we propose ReconVLA, a reconstructive VLA model with an implicit grounding paradigm.  Conditioned on the model's visual outputs, a diffusion transformer aims to reconstruct the gaze region of the image, which corresponds to the target manipulated objects. This process prompts the VLA model to learn fine-grained representations and accurately allocate visual attention, thus effectively leveraging task-specific visual information and conducting precise manipulation. Moreover, we curate a large-scale pretraining dataset comprising over 100k trajectories and 2 million data samples from open-source robotic datasets, further boosting the model’s generalization in visual reconstruction. Extensive experiments in simulation and the real world demonstrate the superiority of our implicit grounding method, showcasing its capabilities of precise manipulation and generalization.

---

## 论文详细总结（自动生成）

## 1. 核心问题与研究背景

- **问题**：当前 Vision-Language-Action (VLA) 模型虽然融合了多模态理解与动作执行，但经验分析发现其视觉注意力严重分散，无法精准聚焦于任务目标区域，导致在复杂场景和长程任务中常操控错误物体。
- **动机**：受人类视觉“注视”（gaze）行为启发——中央凹区域清晰聚焦、周围模糊——作者旨在通过辅助视觉重建任务，隐式引导模型将注意力分配到正确目标，从而提升操控精度。

## 2. 方法论：ReconVLA

- **核心思想**：引入**隐式接地（Implicit Grounding）**范式，不依赖外部检测器或显式坐标输出，而是让 VLA 模型在其视觉输出上学习重建“注视区域”（即待操控目标的局部图像块），以此迫使模型学习细粒度表示并校正注意力分布。
- **关键技术细节**：
  - **模型架构**（图3）：基于 LLaVA-7b（视觉编码器 SIGLIP + 语言模型 Qwen2-7b）。输入为多视角图像与语言指令，输出含两类 token：**动作 token**（自回归预测）和**重建 token**（由 LLM 视觉输出部分产生）。
  - **重建目标**：将注视区域图像通过冻结的视觉分词器（连续 VAE）编码为场景 token $$z_0$$，并对其添加噪声。扩散去噪器（轻量级 Diffusion Transformer）以重建 token $$h_R$$ 为条件，从噪声中恢复 $$z_0$$。损失函数为：
    $$ \mathcal{L}_{\text{visual}} = \mathbb{E}_{t, \epsilon} \left\| \mathcal{D}(z_t; h_R, t) - \epsilon \right\|^2 $$
    总损失为动作交叉熵损失与视觉重建损失之和。
  - **注视区域获取**：预训练阶段使用 Grounding DINO 自动检测并裁剪当前帧中与指令相关的目标区域，形成“原图-注视区域”配对数据。
- **大规模预训练**：收集 BridgeData V2、LIBERO、CALVIN 等开源数据，构建包含 >100k 条轨迹、>2M 样本的数据集。预训练时同时优化动作损失与重建损失，以装备 VLA 模型的视觉重建泛化能力；随后在具体任务上微调对齐。

## 3. 实验设计

- **仿真基准**：
  - **CALVIN**（34 个任务，4 种环境 A/B/C/D），长程评估为连续 5 个子任务（ABC→D 为跨背景泛化，ABCD→D 为同背景）。
  - **指标**：每步成功率与平均完成长度（Avg. Len）。
- **真实世界设置**：
  - 机器人平台：AgileX PiPer 6-DoF 臂 + 1-DoF 平行夹爪；相机：RealSense D515（Eye-on-Base）、ORBBEC Dabai（Eye-on-Hand）。
  - 任务：四种代表性任务（Stack bowls, Put fruit into bowl, Flip cups, Bus table），每任务 150 条训练轨迹；另有 2 个未见物体泛化测试。
- **对比方法**：
  - **接地范式对比**：显式接地（EG，YOLOv11 裁剪并联合输入）、链式思考接地（CG，输出边界框再输出动作）、隐式接地（IG，本文方法）。
  - **与 SOTA 比较**：生成方法（UniPi, SuSIE, CLOVER, 3D-VLA, GR-1, Vidman, GEVRM）与大 VLA 模型（RoboFlamingo, VLAS, OpenVLA, UniVLA）。
- **消融实验**：重建监督、注视区域 vs. 整图、预训练与否。

## 4. 资源与算力

- 文中**未明确提及**所使用的 GPU 型号、数量、训练时长等具体算力信息。仅提到模型基于 LLaVA-7b（7B 参数），且预训练数据规模较大（2M 样本），但未报告实际训练开销。

## 5. 实验数量与充分性

- **实验数量**：涵盖仿真（CALVIN 两个设置）与真实世界（4 个任务 + 2 个泛化），包含范式对比、注意力可视化、消融、与大量 SOTA 对比、真人演示数据泛化测试，共计超过 10 组定量比较。
- **充分性**：实验较为全面，验证了方法在不同维度（接地方式、训练策略、任务类型、泛化性）上的有效性；且遵循统基准（CALVIN）进行公平对比，消融控制了变量。但真实环境任务数偏少（4 个），且仅在一个机械臂平台上测试，泛化范围有限。

## 6. 主要结论与发现

- 隐式接地显著优于显式接地（EG）和链式思维接地（CG），且在 CALVIN ABC→D 中达到 64.1% 的第五步成功率，领先第二名 UniVLA（56.5%）7.6 个百分点。
- 注意力可视化证实 ReconVLA 能够将注意力聚焦于目标物体，而基线则分散。
- 预训练对于泛化至关重要，注视区域重建（而非整图重建）效果最佳。
- 在真实世界任务中，ReconVLA 在所有四项任务上均优于 OpenVLA 和 PD-VLA，尤其在需精细操控的 Flip cups、Bus table 任务上优势明显；对于未见物体，ReconVLA 仍能成功操控，显示良好的视觉泛化能力。

## 7. 优点

- **方法创新**：首次将隐式重建作为视觉接地手段用于 VLA，避免了外部分割器或额外输入输出，训练与推理简单高效。
- **数据贡献**：构建了大规模多源机器人预训练数据集，并公开自动标注流程。
- **实验严谨**：不仅对比多种接地范式，还与多种 SOTA 方法（包括生成式与大 VLA）在同一个基准下比较，消融实验充分。
- **真实世界验证**：展示了实际部署可行性，并专门测试了未见物体泛化，增强了结果说服力。

## 8. 不足与局限

- **算力与效率未报告**：文中未给出训练时间、GPU 数量等资源消耗，难以评估方法的实际训练成本。
- **数据集偏差风险**：预训练数据仅来自 BridgeData V2、LIBERO、CALVIN，场景和物体多样性有限，可能不能充分覆盖真实世界分布；且注视区域依赖 Grounding DINO 自动生成，标注噪声可能影响预训练质量。
- **平台与任务广度**：真实实验仅使用一个机器人臂和四个任务，且均属于桌面操控；未测试移动操作、多臂协同等更复杂场景，泛化结论需谨慎。
- **计算开销**：虽然附加快扩散去噪器为轻量级，但整体仍保持 7B 规模，在边缘设备上部署可能受限。
- **缺乏与更基础策略（如行为克隆、扩散策略）的对比**：对比主要集中于 VLA 类方法，未与纯动作策略（如 Diffusion Policy）比较，以突出 VLA+重建的边际贡献。

（完）
