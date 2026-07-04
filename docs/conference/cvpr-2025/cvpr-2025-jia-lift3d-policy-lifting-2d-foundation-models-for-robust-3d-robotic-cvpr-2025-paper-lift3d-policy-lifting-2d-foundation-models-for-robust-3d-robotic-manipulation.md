---
title: "Lift3D Policy: Lifting 2D Foundation Models for Robust 3D Robotic Manipulation"
title_zh: Lift3D策略：将2D基础模型提升至鲁棒3D机器人操纵
authors: "Jia, Yueru, Liu, Jiaming, Chen, Sixiang, Gu, Chenyang, Wang, Zhilve, Luo, Longzan, Li, Xiaoqi, Wang, Pengwei, Wang, Zhongyuan, Zhang, Renrui, Zhang, Shanghang"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Jia_Lift3D_Policy_Lifting_2D_Foundation_Models_for_Robust_3D_Robotic_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 将2D基础模型提升为3D视觉-动作机器人操纵策略
tldr: 3D几何信息对机器人操纵至关重要，但3D机器人数据稀缺制约了3D特征提取。本文提出Lift3D框架，通过隐式与显式3D表征渐进增强2D基础模型，构建鲁棒的3D操纵策略。具体设计任务感知掩码自编码器，遮蔽任务相关的可供性区域并重建深度信息。在多个3D机器人操纵基准上的实验表明，该方法在空间推理和复杂场景下优于纯2D策略，为3D视觉-动作策略提供了新范式。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1798, \"height\": 762, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1814, \"height\": 800, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 728, \"height\": 283, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1788, \"height\": 483, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 829, \"height\": 464, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1785, \"height\": 427, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 808, \"height\": 373, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 842, \"height\": 344, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-jia-lift3d-policy-lifting-2d-foundation-models-for-robust-3d-robotic-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 200, \"label\": \"Table\"}]"
motivation: 3D机器人数据稀缺导致显式3D特征提取困难，影响操纵策略空间感知能力。
method: 提出Lift3D框架，通过任务感知掩码自编码器渐进融合2D基础模型与3D表征。
result: 在3D机器人操纵基准上提升空间几何感知与策略鲁棒性，显著优于纯2D方法。
conclusion: 渐进式2D到3D提升可有效缓解数据稀缺，构建鲁棒3D操纵策略。
---

## Abstract
3D geometric information is essential for manipulation tasks, as robots need to perceive the 3D environment, reason about spatial relationships, and interact with intricate spatial configurations. Recent research has increasingly focused on the explicit extraction of 3D features, while still facing challenges such as the lack of large-scale robotic 3D data and the potential loss of spatial geometry. To address these limitations, we propose the Lift3D framework, which progressively enhances 2D foundation models with implicit and explicit 3D robotic representations to construct a robust 3D manipulation policy. Specifically, we first design a task-aware masked autoencoder that masks task-relevant affordance patches and reconstructs depth information, enhancing the 2D foundation model's implicit 3D robotic representation. After self-supervised fine-tuning, we introduce a 2D model-lifting strategy that establishes a positional mapping between the input 3D points and the positional embeddings of the 2D model. Based on the mapping, Lift3D utilizes the 2D foundation model to directly encode point cloud data, leveraging large-scale pretrained knowledge to construct explicit 3D robotic representations while minimizing spatial information loss. In experiments, Lift3D consistently outperforms previous state-of-the-art methods across several simulation benchmarks and real-world scenarios.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Lift3D Policy: Lifting 2D Foundation Models for Robust 3D Robotic Manipulation" following a specific structure. Let me carefully analyze the paper and organize the content.

The paper is from CVPR 2025, about using 2D foundation models (like DINOv2 and CLIP) for 3D robotic manipulation. Let me extract the key information:

1. **Core problem**: 3D geometric information is crucial for robotic manipulation, but there's a lack of large-scale robotic 3D data. Existing methods either train 3D models from scratch (limited by data) or do modality transformations (losing spatial info).

2. **Method**: Lift3D framework with two stages:
   - Stage 1 (Implicit 3D representation): Task-aware MAE that masks task-related affordance patches and reconstructs depth information
   - Stage 2 (Explicit 3D representation): 2D model-lifting strategy that maps 3D points to 2D positional embeddings, using pretrained 2D PEs to encode point cloud data

3. **Experiments**: 
   - 3 simulation benchmarks: MetaWorld (15 tasks), Adroit (3 tasks), RLBench
   - 10 real-world tasks
   - Compared with 9 baselines including CLIP, R3M, VC-1, PointNet, PointNet++, PointNeXt, SPA, DP3, RVT-2

4. **Resources**: The paper doesn't explicitly mention specific GPU types, counts, or training time.

5. **Experiment count**: Multiple benchmarks, ablations with 9 configurations, generalization tests with 3 scenarios, scalability tests with 3 model sizes.

6. **Results**: 
   - MetaWorld: 83.9% mean SR (CLIP), 84.5% (DINOv2)
   - Adroit: 88.0% mean SR (CLIP)
   - Real-world: 62.5% mean SR
   - Improvements: 18.2% over SOTA on MetaWorld, 21.3% on Adroit
   - Real-world improvement: 17 points over DP3

7. **Strengths**:
   - Novel approach of using 2D PEs for 3D point cloud encoding
   - Task-aware masking with affordance guidance
   - Strong performance even with simple MLP head
   - Good generalization across objects, backgrounds, lighting
   - Scalability with model size

8. **Limitations**:
   - Cannot comprehend language conditions directly
   - Single-view point cloud only
   - Need to mention limitations explicitly mentioned in paper

Let me write this in a structured Markdown format in Chinese.
</think>
# Lift3D Policy 论文总结

## 1. 核心问题与研究动机

- **核心问题**：3D 几何信息对机器人操纵任务至关重要，机器人需感知 3D 环境、推理空间关系并与复杂空间配置交互。然而构建 3D 操纵策略面临两大挑战：
  - **数据稀缺**：大规模机器人 3D 数据不足，直接训练或微调 3D 模型（如 PointNet++/PointNeXt）泛化能力受限，且 3D/体素特征计算成本高。
  - **空间信息损失**：现有方法常通过模态转换（如 2D 特征升维到 3D、或将 3D 点云投影为多视图图像）注入 2D 预训练知识，但转换过程不可避免地损失空间信息。
- **核心疑问**：能否在保留完整 3D 空间输入的同时，利用大规模 2D 预训练知识构建 3D 操纵策略？
- **研究目标**：将基于 Transformer 的 2D 基础模型（如 DINOv2、CLIP）"提升"为鲁棒的 3D 操纵策略，逐步增强隐式与显式 3D 机器人表征。

## 2. 方法论：核心思想与关键技术

### 2.1 整体框架：两阶段渐进式提升

Lift3D 包含两个递进阶段：
- **阶段 1（隐式 3D 表征增强）**：通过任务感知 MAE 自监督微调，让 2D 基础模型获得 3D 空间感知能力。
- **阶段 2（显式 3D 表征构建）**：通过 2D 模型提升策略，将 2D 模型直接用于编码点云数据，复用其大规模预训练知识。

### 2.2 关键技术细节

**（1）任务感知掩码自编码器（Task-aware MAE）**
- **数据来源**：从 Open X-Embodiment 等机器人数据集中采样约 100 万训练样本，含配对的图像与深度数据。
- **可供性引导掩码**：
  - 用 CLIP 根据任务文本描述（如"机械臂拿起红碗放进灰碗"）生成图像注意力图。
  - 通过阈值（θ=0.5）将注意力图二值化，分离任务相关可供性区域与背景。
  - 任务相关 patch 全部被掩码，背景 patch 随机掩码以达到 75% 掩码率。
- **重建目标**：对任务相关及部分背景 patch 重建**深度信息**（而非 RGB），以增强 3D 空间感知。
- **损失函数**：
  $$\mathcal{L}_{\text{implicit}} = \|2D_e(x_{\text{vis}}) - 2D_e^{\text{pre}}(x_{\text{vis}})\|_1 + \|2D_d(2D_e(x_{\text{vis}}) \| x_{\text{mask}}) - D_{\text{target}}\|_1$$
  - 第一项为**视觉 token 蒸馏损失**（防止灾难性遗忘预训练知识）。
  - 第二项为深度重建 L1 损失。
- **训练策略**：冻结 2D 基础模型主体，仅微调注入的 LoRA 适配器与 MAE 解码器。

**（2）2D 模型提升策略（2D Model-Lifting）**
- **核心思想**：不重新学习 3D 位置编码，而是通过**虚拟平面投影**建立 3D 点到 2D 预训练位置编码（PE）的映射。
- **步骤**：
  1. 用轻量级 3D tokenizer（FPS 降采样 + k-NN + 线性层）将点云转为 128 个 3D token（B×128×768）。
  2. 将每个 3D 坐标投影到 **6 个虚拟平面**（立方体投影），得到 n 个 2D 坐标 $\{C_{ij}^{2D}\}_{j=1}^n$。
  3. 用这些 2D 坐标查询预训练 2D 位置编码表，得到 $\{PE_{2D}(C_{ij}^{2D})\}_{j=1}^n$。
  4. 取平均得到统一的 3D 位置编码：
     $$PE_{3D} = \frac{1}{n}\sum_{j=1}^n PE_{2D}(C_{ij}^{2D})$$
  5. 将 $PE_{3D}$ 与 3D token 相加，输入 2D 基础模型。
- **关键优势**：避免模态转换造成空间信息损失；保留 2D 模型的大规模预训练知识；不引入额外的可学习 3D PE。
- **动作预测**：7-DoF 末端执行器位姿（3 平移 + 3 旋转 + 1 夹爪），通过简单 3 层 MLP 策略头输出，损失为平移 MSE + 旋转余弦距离 + 夹爪 BCE。
- **训练策略**：冻结 2D 基础模型，仅更新 3D tokenizer、LoRA 适配器与策略头。

## 3. 实验设计

### 3.1 数据集与基准
- **仿真基准**（共 30+ 任务）：
  - **MetaWorld**（MuJoCo + Sawyer 机械臂 + 双指夹爪）：15 个任务，按难度分 4 档（简单 7 / 中等 5 / 困难 2 / 极难 1），每任务 25 条演示，每条 200 步。
  - **Adroit**（MuJoCo + 灵巧手）：3 个任务（hammer、door、pen），DoF 分别为 26/28/24，每任务 100 条演示，每条 100 步。
  - **RLBench**（CoppeliaSim + Franka Panda + 夹爪）：基于 OMPL 关键帧采样，每任务 100 条演示。
- **真实世界任务**（10 个）：Franka Research 3 + Intel RealSense L515 RGBD 静态前视，包括放瓶子、倒水、拔充电器、堆叠、滑动、浇花、擦桌、开/关抽屉等；每任务 40 次演示，选取 30 个关键帧训练，20 次评估。

### 3.2 对比方法（9 类）
- **2D 机器人表征方法**：CLIP（ViT-base）、R3M、VC-1。
- **3D 表征方法**：PointNet、PointNet++、PointNeXt、SPA（3D MAE 预训练 SOTA）。
- **3D 模仿学习策略**：DP3（3D Diffusion Policy）、RVT-2。
- 所有方法使用相同的 3 层 MLP 策略头与训练损失（保证公平对比）。

### 3.3 训练与评估细节
- 输入：224×224 RGB 图像或单视角 1024 点点云。
- 优化器：Adam（β₁=0.9, β₂=0.999），学习率 1e-3，MetaWorld 恒定学习率，Adroit 余弦退火 + 0.1 warmup。
- 训练 100 epoch，每 10 epoch 评估 25 次，报告最佳策略平均成功率。

## 4. 资源与算力

- 论文**未明确说明**具体 GPU 型号、数量及训练时长。
- 从方法复杂度推断：单卡（如 A100/V100）即可完成实验；3D tokenizer 与 MLP 策略头为轻量组件，2D 基础模型采用 ViT-base（86M）至 ViT-giant（1B）。

## 5. 实验数量与充分性

- **实验规模充分**：
  - 仿真：30+ 任务、3 基准、9 个对比方法。
  - 真实世界：10 个任务、20 次/任务评估。
  - 消融实验：9 组配置（系统性地拆解 AMS、Depth、RGB、VD、2ML-PEs、L-PEs 等模块）。
  - 泛化实验：3 类场景（不同物体 / 背景 / 光照） × 2 任务。
  - 可扩展性实验：3 种模型规模（ViT-base 86M、ViT-large 304M、ViT-giant 1B）。
- **公平性**：
  - 所有表征方法统一使用相同的 3 层 MLP 策略头与训练损失。
  - 输入配置（点云分辨率 1024、图像 224×224）统一。
  - 与 3D 策略方法（DP3/RVT-2）按各自原始设置对比，文中明确说明。
- **不足**：每个 MetaWorld 任务仅 25 条演示，样本量较少；且未与最新的 VLA 模型（如 OpenVLA、RT-2）直接对比。

## 6. 主要结论与发现

- **仿真结果（表 1）**：
  - MetaWorld 平均成功率：Lift3D(CLIP) **83.9%**、Lift3D(DINOV2) **84.5%**，比最佳 2D 方法（R3M 75.1%）高约 8.8%，比最佳 3D 表征方法（SPA 69.5%）高 14.4%，比 SOTA 3D 策略 DP3（65.3%）高 18.6%。
  - Adroit 灵巧手任务：Lift3D(CLIP) 平均 **88.0%**，比 DP3（66.7%）高 21.3%。
- **真实世界结果（表 2）**：Lift3D 平均成功率 **62.5%**，比 DP3（45.5%）高 17 个百分点。
- **泛化能力（表 4）**：在不同物体/背景/光照下，Lift3D 性能下降幅度最小（-11% ~ -41%），明显优于 DP3 与 VC-1。
- **可扩展性（图 4）**：在极难任务 shelf-place 上，将 DINOV2 从 ViT-base 升级到 ViT-large/ViT-giant，成功率从 28% 提升至 58%/68%，收敛更快。
- **关键洞察**：
  - 深度重建目标比 RGB 重建更有效。
  - 可供性引导掩码优于随机掩码。
  - 蒸馏损失对防止灾难性遗忘至关重要。
  - 复用预训练 2D PE 比新学 3D PE 更能保留预训练知识。

## 7. 优点

- **方法新颖**：首次提出将 2D 预训练位置编码直接用于 3D 点云编码的"提升"策略，巧妙回避了模态转换的信息损失。
- **设计精巧**：任务感知 MAE 引入 CLIP 注意力图引导掩码，使重建任务更聚焦于可供性区域，提升学习效率。
- **实现简洁**：仅需简单 3 层 MLP 策略头即可超越复杂 3D 策略（如 DP3），证明表征质量才是关键。
- **通用性强**：兼容多种 2D 基础模型（CLIP/DINOV2），不限定特定架构。
- **泛化鲁棒**：在物体/背景/光照变化下均表现稳健，得益于大规模预训练知识与深度几何重建。
- **可扩展性好**：随模型规模增大性能持续提升，展示了基础模型范式在机器人领域的潜力。

## 8. 不足与局限

- **语言条件缺失**：作者明确指出 Lift3D 无法直接理解语言条件；虽然可集成 CLIP，但需要额外接入语言模型才能构建 3D VLA 模型。
- **单视角点云**：实验均使用单视角点云（1024 点），未验证多视角融合或更密集点云的性能。
- **演示数据量小**：MetaWorld 仅 25 条/任务演示，真实世界 30 关键帧/任务，样本效率声明（"30 episodes"）需更系统的少样本分析。
- **任务类型有限**：真实世界任务以桌面级 pick-and-place 为主，未涉及移动操作、长序列任务或工具使用。
- **无算力报告**：缺少 GPU 型号、数量、训练时长、推理延迟等部署相关信息。
- **公平性边界**：与 DP3 等 3D 策略对比时遵循各自原始设置，但未控制所有超参一致；未与最新 VLA 大模型（如 OpenVLA、π₀）比较。
- **2D PE 容量限制**：立方体投影仅 6 个虚拟平面，PE 表达能力受限于 2D 网格分辨率，极复杂 3D 结构可能仍存信息瓶颈。

（完）
