---
title: "GraphCoT-VLA: A 3D Spatial-Aware Reasoning Vision-Language-Action Model for Robotic Manipulation with Ambiguous Instructions"
title_zh: GraphCoT-VLA：面向模糊指令的3D空间感知推理视觉-语言-动作模型
authors: "Helong Huang, Min Cen, Kai Tan, Xingyue Quan, Guowei Huang, Hong Zhang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38896/42858"
tags: ["query:rob-il"]
score: 8.0
evidence: 处理模糊指令的3D空间感知推理VLA模型
tldr: 现有VLA模型在处理模糊指令和未知环境时表现不佳。GraphCoT-VLA通过结构化思维链推理模块整合高层任务理解与低层控制，并结合3D空间感知，在模拟和真实环境中实现了对模糊指令的准确执行和任务成功率的显著提升。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 866, \"height\": 630, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1837, \"height\": 1020, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 397, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1723, \"height\": 1579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 876, \"height\": 311, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38896/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1789, \"height\": 1202, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38896/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 835, \"height\": 534, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38896/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1777, \"height\": 374, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38896/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1730, \"height\": 340, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38896/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 541, \"height\": 185, \"label\": \"Table\"}]"
motivation: 现有VLA模型处理模糊指令能力弱，且缺乏3D交互建模。
method: 设计结构化思维链推理模块，结合3D空间特征进行端到端学习。
result: 在多个模糊指令操作任务上，GraphCoT-VLA优于现有方法。
conclusion: 结合推理和3D感知是提升VLA模型鲁棒性的关键。
---

## Abstract
Vision-language-action models have emerged as a crucial paradigm in robotic manipulation. However, existing VLA models exhibit notable limitations in handling ambiguous language instructions and unknown environmental states. Furthermore, their perception is largely constrained to static two-dimensional observations, lacking the capability to model three-dimensional interactions between the robot and its environment. To address these challenges, this paper proposes GraphCoT-VLA, an efficient end-to-end model. To enhance the model's ability to interpret ambiguous instructions and improve task planning, we design a structured Chain-of-Thought reasoning module that integrates high-level task understanding and planning, failed task feedback, and low-level imaginative reasoning about future object positions and robot actions. Additionally, we construct a real-time updatable 3D Pose-Object graph, which captures the spatial configuration of robot joints and the topological relationships between objects in 3D space, enabling the model to better understand and manipulate their interactions. We further integrates a dropout hybrid reasoning strategy to achieve efficient control outputs. Experimental results across multiple real-world robotic tasks demonstrate that GraphCoT-VLA significantly outperforms existing methods in terms of task success rate and response speed, exhibiting strong generalization and robustness in open environments and under uncertain instructions.

---

## 论文详细总结（自动生成）

# GraphCoT-VLA 论文详细中文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 现有 Vision-Language-Action (VLA) 模型在处理**模糊语言指令**（如“我想吃辛辣的河鲜”）和**未知环境状态**时表现不佳，经常产生幻觉或失败。
- 大多数 VLA 的感知局限于**静态 2D 观察**，缺乏对机器人与环境之间**三维交互**的建模能力。
- 本文旨在通过引入**结构化 Chain-of-Thought (CoT) 推理**和**3D 空间感知图**，增强 VLA 对模糊指令的理解、任务规划与鲁棒执行能力，实现端到端的操作模型 GraphCoT-VLA。

## 2. 方法论

### 2.1 核心思想

- 将**高层推理（场景理解、指令可行性判断、反馈生成）**与**低层想象（未来物体位置、机器人状态预测）**通过结构化 CoT 结合，再引入实时更新的 **3D Pose-Object 图**来显式建模机器人与物体间的空间拓扑关系，从而指导动作生成。

### 2.2 关键技术细节

- **Pose-Object 图实时构建**  
  - 输入：多模态数据流（RGB‑D 图像、机器人关节角度）。  
  - 步骤：  
    1. 用 YOLO-World 检测物体边界框，提取 2D 中心点。  
    2. 结合深度图像、相机内参和外参，将 2D 点投影到机器人基坐标系下的 3D 点。  
    3. 通过正向运动学计算机器人末端位置。  
    4. 所有物体节点与末端节点全连接形成图。  
  - 图编码：两层 GNN（层归一化 + 图卷积 + ReLU），输出节点特征供后续使用。

- **结构化 Chain-of-Thought 推理**  
  - 使用 Qwen2.5‑VL‑7B 分阶段执行：  
    1. **场景理解**：描述当前观测中的物体。  
    2. **可行性分析与反馈**：判断模糊指令是否可执行，若不可行则生成建议。  
    3. **未来想象**：预测 ∆t=30 帧后的物体位置和机器人状态（转换为文本）。  
  - CoT 输出与语言指令、视觉、图特征共同输入 VLM（基于 PaLiGemma）。

- **整体架构与动作生成**  
  - 输入：头部+左右腕部 RGB 图像、机器人状态、语言指令、Pose-Object 图。  
  - VLM 输出令牌分为两部分：一部分自回归生成 CoT 解释，另一部分送入**动作专家（基于 flow matching）**预测未来 ∆t 步的动作序列。  
  - 动作专家以机器人状态和噪声为输入，学习时间相关的去噪向量场。

- **Dropout 联合训练策略**  
  - 随机丢弃 CoT 监督（概率 p），使模型同时学习“推理引导”与“直接动作预测”两种模式。  
  - 损失函数：  
    - CoT 部分：标准交叉熵损失 \(L_{CoT}\)。  
    - 动作部分：条件流匹配损失 \(L_{action}\)。  
    - 总损失：\((1-d) \cdot (\lambda_{CoT} L_{CoT} + \lambda_{action} L_{action}) + d \cdot L_{action}\)，其中 \(d \sim Bernoulli(p)\)。  
  - 推理时：首帧生成 CoT 提供反馈与指引，后续帧跳过 CoT 直接预测动作，保证实时性（~10 Hz）。

## 3. 实验设计

### 3.1 场景与数据集

- **机器人平台**：双臂机器人（每臂 7 自由度），搭载头、颈、手部 RGB‑D 相机。  
- **数据采集**：以头部相机时间戳对齐模态（相机 30 Hz，PD 控制 150 Hz），动作定义为关节角度。  
- **任务**：设计两个场景共 6 个子任务，每个场景按可用物体变化分为 3 个子任务（见表 1）：  
  - **Food Preparation**：食材选择（鱼、鸡蛋、番茄、辣椒，子任务中不同组合）。  
  - **Outfit Selection**：衣物选择（T恤、毛衣、短裤，子任务中不同组合）。  
- **样本量**：每个子任务采集 100 个演示，共 600 个训练样本。物体位置随机平移（10 cm）、旋转（≤30°），衣物排列按预定排列或均匀采样。

### 3.2 对比方法

- **ACT**（Transformer 从零训练，图像→动作）  
- **Diffusion Policy**（扩散模型生成动作）  
- **Octo**（预训练 Transformer，在 Open X‑Embodiment 上训练后微调）  
- **π0**（通用 VLA，同时使用图像和语言输入，微调）  
- **Ours (GraphCoT-VLA)**

### 3.3 评估指标

- 每个任务测试 **20 次**，成功率（全程完成正确才算成功）。  
- 额外关注“任务混淆”（task confusion）——机器人是否能在模糊指令下正确辨别真实意图。

## 4. 资源与算力

- 论文中 **未明确说明** 使用的 GPU 型号、数量、训练时长等硬件信息。  
- 仅提及推理频率测量（π0 和本文方法均约 10 Hz），首帧 CoT 耗时 < 30 s。

## 5. 实验数量与充分性

### 5.1 实验组数

- **主对比实验（表 2）**：两个任务，每个任务 3 个子任务（共 6 个条件），对比 4 个基线。  
- **消融实验（表 3）**：  
  - 去掉 CoT 和图（即 π0 基线）  
  - 去掉 Pose-Object 图  
  - 去掉 CoT  
  - 完整模型  
  - 在每个子任务上报告成功率。  
- **效率实验（表 4）**：π0 与本文 co-training 版本频率对比。  
- **可视化**：CoT 推理内容展示（图 5）、图结构可视化（图 6）以及失败案例对比（图 4）。

### 5.2 充分性与公平性

- **优点**：  
  - 对比了多种主流方法（ACT、扩散策略、离线预训练模型、VLA 微调），覆盖较全。  
  - 消融实验设计了逐步去除关键组件的组合，验证了每一项贡献。  
  - 每个条件测试 20 次，对成功率评估有一定统计意义。  
- **潜在不足**：  
  - 样本量相对较小（每个子任务 100 演示，测试 20 次），可能受随机影响。  
  - 未报告多次运行的平均值和方差，无法评估稳定性。  
  - 未在公开数据集（如 Bridge、RoboSet）上验证，仅在自建场景中评估，泛化性结论有限。  
  - 基线模型的微调细节（训练轮数、超参数）未完全描述，可能影响可比性。

## 6. 主要结论与发现

- GraphCoT-VLA 在 **Food Preparation** 和 **Outfit Selection** 任务上的平均成功率分别达到 **76.67% 和 70.00%**，显著优于所有基线（最优基线 Octo 50.00%、π0 51.67%）。  
- 基线模型在模糊指令下容易产生 **任务混淆**（如应拿 T‑shirt 却拿毛衣），而本文模型正确理解意图，没有混淆。  
- **Pose-Object 图** 带来最多 18.33% 的成功率提升，尤其在需要高末端精度的任务中（如挂衣架），提升了动作流畅度与稳定性。  
- **CoT 推理** 使模型具备场景理解、反馈生成和未来预测能力，避免“抖动”行为，使动作更加连贯有规划。  
- 推理速度与 π0 相当（~10 Hz），首帧引入 CoT 后无额外计算开销。

## 7. 优点

- **创新性**：  
  - 提出 **结构化 CoT** 结合高层理解反馈与低层未来想象，是首个在 VLA 中同时实现任务分解、失败反馈和状态预测的工作。  
  - 引入 **实时 Pose-Object 图** 显式建模 3D 空间关系，弥补了 2D 静态感知的缺陷。  
  - **Dropout 混合推理策略** 在保持实时性的同时保留了深度推理能力。  
- **实验验证**：在真实机器人上完成了多个模糊指令场景，展示了实际可用性，并提供了丰富的可视化分析。  
- **效果突出**：在所有子任务上明显超过基线，无任务混淆，且消融实验清晰证明了各模块的贡献。

## 8. 不足与局限

- **缺乏历史时序记忆**：当前模型仅依赖当前观测和未来想象，无法利用过去帧的长程上下文（作者在结论中也指出）。  
- **依赖外部工具**：CoT 生成使用 Qwen2.5‑VL‑7B，物体检测使用 YOLO-World，这些预训练模型的性能和质量直接影响整体效果，且可能带来延迟或错误传播。  
- **场景局限**：仅在桌面食材挑选和挂衣架选择两类任务上测试，环境视觉多样性有限；未在更复杂、杂乱或动态环境中验证。  
- **评估样本量较小**：每个条件测试 20 次，无置信区间或多次重复，结论的统计显著性有待加强。  
- **算力与训练细节缺失**：未报告 GPU 型号、训练时长等关键资源信息，影响了可复现性和对成本的理解。  
- **数据集不公开**：自建数据集未开放，无法供社区复现或对比；基线模型微调细节未完全披露，公平性有一定折扣。

（完）
