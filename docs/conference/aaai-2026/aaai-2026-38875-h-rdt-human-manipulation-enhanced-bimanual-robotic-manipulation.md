---
title: "H-RDT: Human Manipulation Enhanced Bimanual Robotic Manipulation"
title_zh: H-RDT：人类操作增强的双手机器人操作
authors: "Hongzhe Bi, Lingxuan Wu, Tianwei Lin, Hengkai Tan, Zhizhong Su, Hang Su, Jun Zhu"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38875/42837"
tags: ["query:rob-il"]
score: 9.0
evidence: 利用人类操作数据增强双手机器人操作的模仿学习
tldr: 机器人模仿学习面临高质量演示数据稀缺的问题。该论文利用大规模第一人称人类操作视频（含3D手部姿态标注）提供行为先验，提出H-RDT（人体到机器人扩散变换器）增强双臂操作能力。实验证明跨实体知识迁移有效提升了操作策略的泛化性和数据效率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38875/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1832, \"height\": 1135, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38875/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1402, \"height\": 919, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38875/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 893, \"height\": 684, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38875/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 834, \"height\": 288, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38875/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 870, \"height\": 215, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38875/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1268, \"height\": 282, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38875/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 874, \"height\": 247, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38875/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 830, \"height\": 461, \"label\": \"Table\"}]"
motivation: 机器人演示数据稀缺且跨实体数据难以统一训练。
method: 利用人类操作视频中的行为先验，通过扩散变换器迁移到机器人操作策略。
result: 在双手操作任务上取得了更高的数据效率和泛化性能。
conclusion: 人类操作数据是机器人模仿学习的重要资源，可缓解数据稀缺问题。
---

## Abstract
Imitation learning for robotic manipulation faces a fundamental challenge: the scarcity of large-scale, high-quality robot demonstration data. Recent robotic foundation models often pre-train on cross-embodiment robot datasets to increase data scale, while they face significant limitations as the diverse morphologies and action spaces across different robot embodiments make unified training challenging. In this paper, we present  H-RDT (Human to Robotics Diffusion Transformer), a novel approach that leverages human manipulation data to enhance robot manipulation capabilities. Our key insight is that large-scale egocentric human manipulation videos with paired 3D hand pose annotations provide rich behavioral priors that capture natural manipulation strategies and can benefit robotic policy learning. We introduce a two-stage training paradigm: (1) pre-training on large-scale egocentric human manipulation data, and (2) cross-embodiment fine-tuning on robot-specific data with modular action encoders and decoders. Built on a diffusion transformer architecture with 2B parameters, H-RDT uses flow matching to model complex action distributions. The modular design of action encoder and decoder components enables effective knowledge transfer from the unified human embodiment to diverse robot platforms through efficient fine-tuning. Extensive evaluations encompassing both simulation and real-world experiments, single-task and multitask scenarios, as well as few-shot learning and robustness assessments, demonstrate that H-RDT outperforms training from scratch and existing state-of-the-art methods, including π0 and RDT, achieving significant improvements of 13.9% and 40.5% over training from scratch in simulation and real-world experiments, respectively. The results validate our core hypothesis that human manipulation data can serve as a powerful foundation for learning bimanual robotic manipulation policies.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义（研究动机和背景）

- **核心问题**：机器人模仿学习依赖大规模、高质量的演示数据，但通过遥操作采集数据成本高、效率低；现有跨实体预训练方法（如使用 Open X-Embodiment）虽能扩大数据量，但不同机器人形态和动作空间的差异使得统一训练困难，且机器人数据集总体规模仍然有限。
- **研究动机**：人类操作数据是天然丰富的资源，大规模的第一人称操作视频（例如 EgoDex 包含 829 小时、338k 条轨迹）并配准了 3D 手部姿态，蕴含了物体可供性、操作策略、任务分解等丰富的行为先验，这些知识有望迁移到机器人上，缓解数据稀缺问题。
- **整体含义**：论文提出 H-RDT（Human to Robotics Diffusion Transformer），通过“人类数据预训练 + 跨实体微调”的两阶段范式，系统性地将大规模人类操作知识转移至多种双臂机器人平台，显著提升了操作策略的泛化能力和样本效率。

## 2. 论文提出的方法论：核心思想、关键技术细节、公式或算法流程

- **核心思想**：利用人类操作数据作为强先验，通过统一的动作表示空间弥合人与机器人之间的实体差异，采用扩散 Transformer 与流匹配（Flow Matching）生成动作序列，并用模块化的动作编码/解码器实现跨实体高效微调。
- **关键技术细节**：
  - **动作表示**：设计 48 维向量作为跨实体共享空间，包含双侧手腕 6D 位姿（18 维）和指尖位置（30 维），该表示可覆盖大多数末端执行器位姿控制的机器人动作空间。
  - **两阶段训练**：
    - 阶段 1：在 EgoDex 数据集（338K+ 轨迹，194 个任务）上预训练，使用流匹配损失。
    - 阶段 2：跨实体微调时，冻结预训练的视觉编码器、语言编码器和 Transformer 主干，重新初始化状态适配器、动作适配器和动作解码器，以适配目标机器人的动作维度（如 14 维双臂加夹爪）。
  - **流匹配**：通过直线路径将高斯噪声逐步变换为目标动作分布。损失函数为  
    \( \mathcal{L}_{\text{FM}} = \mathbb{E}\left[ \| v_\theta(a_\tau, \tau, c) - (z - a^*) \|^2 \right] \)，  
    其中 \( a_\tau = \tau a^* + (1-\tau)z \)。推理时使用 ODE 求解器进行确定性多步生成。
  - **网络架构**：约 2B 参数的扩散 Transformer，基于 LLaMA-3 风格（RMSNorm、SwiGLU、AdaLN），包含视觉编码器（DinoV2 + SigLIP）、语言编码器（T5-XXL）以及模块化的动作编码和解码 MLP。
- **算法流程（文字说明）**：输入多视角 RGB 图像、机器人本体状态和语言指令，经编码器提取特征后，与带噪动作序列拼接；在 Transformer 主干中进行自注意力和交叉注意力处理，最终由动作解码器输出预测的动作序列。

## 3. 实验设计：使用了哪些数据集 / 场景，它的 benchmark 是什么，对比了哪些方法

- **数据集与场景**：
  - **人类预训练**：EgoDex（338K 条轨迹，194 个任务，829 小时第一人称视频配 3D 手部姿态）。
  - **仿真评测**：RoboTwin 2.0 双臂操作基准，含 Easy（整洁桌面）和 Hard（域随机化：灯光、背景、桌面高度变化）两种模式。
  - **现实实验**：
    - Aloha-Agilex-2.0（Piper 双臂）：毛巾折叠、杯子放杯垫。
    - 双 UR5 + UMI：外卖袋放置任务（分解为左右手拾取/放置 4 个子任务）。
    - 双 ARX5：113 种拾取放置任务，每任务仅 1-5 条演示（少量样本设置）。
- **Benchmark**：RoboTwin 2.0 单任务（13 个任务）和多任务（45 个任务训练，主要报告 10 个任务）。
- **对比方法**：RDT、π0、以及自身消融版本 H-RDT w/o human（无人类预训练）。

## 4. 资源与算力：如果文中有提到，请总结使用了多少算力（GPU 型号、数量、训练时长等）。若未明确说明，也请指出这一点

- **论文未明确提及** GPU 型号、数量、训练时长等具体算力信息。仅指出模型参数量为

约2B参数（即20亿参数）。此外，预训练数据EgoDex包含338K条轨迹、829小时视频；微调使用少量机器人演示数据（每个任务1-50条轨迹）。但未说明具体训练硬件配置。

## 5. 结果与发现

- **仿真结果（RoboTwin 2.0）**：
  - 单任务（Single-task）平均成功率：H-RDT 达 96.1%，显著优于 RDT（64.9%）和 π0（58.8%），且方差更小。
  - 多任务（Multi-task, 45 任务训练, 10 任务评估）：H-RDT 成功率 78.7%，对比 RDT 为 47.9%、π0 为 40.0%。
  - 抗干扰能力（Hard 模式）：H-RDT 在光照、背景、桌面高度变化下成功率降幅最小（≤5%），而 RDT 和 π0 分别下降 10-30%。
- **真实机器人结果**：
  - **Piper 双臂**（毛巾折叠、杯子放杯垫）：H-RDT 在 50 条演示下成功率 90% 以上，0-shot 直接部署仍可完成部分任务（如杯垫任务 60%）。
  - **双 UR5 + UMI**（外卖袋放置，45 条演示）：H-RDT 多流程评审成功率 50%，优于 RDT（10%）和 π0（0%），且展现出左手取、右手放的分工协作。
  - **双 ARX5**（113 种拾取放置，每任务仅 1-5 条演示）：H-RDT 在 1 条演示时成功率约 30%，5 条演示时提升至 70%+，显著高于无人类预训练的基线（<10%），证明了极强的样本效率。
- **消融实验**：
  - 去掉人类预训练（H-RDT w/o human）后，多任务仿真成功率从 78.7% 跌至 52.4%，接近 π0 水平，表明人类数据带来的大幅提升。
  - 冻结编码器 vs 全部微调：冻结编码器（两阶段方案）在 50 条演示下远超全微调，但在 500 条演示时差距缩小，说明少量机器人数据时预训练特征重要性更高。

## 6. 潜在局限性

- **动作表示空间差异**：48 维人手到机器人末端位姿的映射假设手腕和手指尖可类比，但无法涵盖软体抓手、灵巧手等多自由度末端；且部分机器人动作空间可能不在该表示内（如全身移动或轮式平台）。
- **人类数据规模与质量依赖**：EgoDex 虽大但任务是固定集合（194 个），且为第三视角视频（第一人称标注细节有限），预训练任务分布可能不覆盖某些机器人操作场景（如大物体搬运）。
- **多阶段微调开销**：与端到端训练相比，两阶段流程需要分别维护人类数据与机器人数据，且冻结大量参数仍需要训练新的适配器和解码器，并非完全零成本。
- **硬件与环境通用性**：目前仅在固定双臂平台上验证，尚未测试单臂、移动底座或非结构化环境；RoboTwin 2.0 Hard 模式虽有域随机但仍是仿真。

## 7. 个人评价与展望

- **贡献**：提出的 H-RDT 是首个系统利用大规模人类操作视频预训练通用机器人策略的工作，通过流匹配与模块化迁移策略在多个双臂平台取得 SOTA 结果，且样本效率优势突出。论文把动作表示、预训练目标和微调流程设计得干净、可复现，是对跨实体模仿学习思路的有力推进。
- **不足之处**：虽然使用了 2B 参数模型和大量人类数据，但并未公开训练能耗或推理时间，难直接评估实际部署成本；此外，48 维动作空间的普适性有待验证，对于类人双手并非完美匹配。
- **未来方向**：可扩展至更丰富的动作空间（如灵巧手、全身运动）；引入更多人类数据集（如 Ego4D、Something-Something）；探索无需微调的零样本迁移；或在真实部署时与低层反馈控制器结合以提高鲁棒性。

综上所述，H-RDT 展示了人类操作数据对机器人策略预训练的巨大潜力，为社区提供了一个有效的跨实体迁移范式和强劲的基线方法。

（完）
