---
title: Self-Correcting Robot Manipulation via Gaussian-Splatted Foresight
title_zh: 基于高斯泼溅预见的自校正机器人操作
authors: "Shaohui Pan, Yong Xu, Ruotao Xu, Zihan Zhou, Si Wu, Zhuliang Yu"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/34866/37021"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于视觉预测的自校正机器人操作，闭环视觉反馈
tldr: 该论文针对语言条件机器人操作在非结构化环境中因部分观测与动作预测不精确而不可避免产生失败的问题，指出操作失误可能使机械臂进入未训练状态并造成破坏性后果。为此，论文提出一种基于预见驱动的失败检测与自校正模块，利用三维高斯泼溅表示当前场景，并训练预测网络对后续状态进行展望，从而触发主动纠错。实验表明该方法在多种操作任务上显著提升了策略鲁棒性。该工作为实际部署中具备闭环视觉反馈的可靠机器人操作系统提供了关键技术支撑。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34866/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 880, \"height\": 540, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34866/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1642, \"height\": 485, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34866/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 871, \"height\": 339, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34866/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 851, \"height\": 436, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-34866/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 869, \"height\": 219, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34866/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1714, \"height\": 528, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34866/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1777, \"height\": 245, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34866/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1373, \"height\": 167, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34866/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 907, \"height\": 368, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-34866/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 857, \"height\": 142, \"label\": \"Table\"}]"
motivation: 语言条件机器人在部分观测与不精确预测下不可避免会失败，可能导致破坏性后果。
method: 利用三维高斯泼溅建模当前场景并训练预测网络进行状态预见，实现失败检测与自校正。
result: 在多种操作任务上提升策略鲁棒性，证明闭环自校正机制的有效性。
conclusion: 为复杂环境下可靠、可恢复的机器人操作系统提供了新的闭环反馈方案。
---

## Abstract
Language-conditioned robotic manipulation in unstructured environments presents significant challenges for intelligent robotic systems. However, due to partial observation or imprecise action prediction, failure may be unavoidable for learned policies. Moreover, operational failures can lead to the robotic arm entering an untrained state, potentially causing destructive results. Consequently, the ability to detect and self-correct failures is crucial for the development of practical robotic systems. To address this challenge, we propose a foresight-driven failure detection and self-correction module for robot manipulation. By leveraging 3D Gaussian Splatting, we represent the current scene with multiple Gaussians. Subsequently, we train a prediction network to forecast the Gaussian representation of future scenes conditioned on planned actions. Failure is detected when the predicted future significantly deviates from the real observation after action execution. In such cases, the end-effector rolls back to the previous action to avoid an untrained state.  Integrating this approach with the PerACT framework, we develop a self-correcting robot manipulation policy. Evaluations on ten RLBench tasks with 166 variations demonstrate the superior performance of the proposed method, which outperforms state-of-the-art methods by 12.0%  success rate on average.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Self-Correcting Robot Manipulation via Gaussian-Splatted Foresight" following a specific structure with 8 sections. Let me carefully analyze the paper and produce a well-organized Markdown summary.

Let me go through each section:

1. **Core problem and motivation**: The paper addresses failure detection and self-correction in language-conditioned robot manipulation. Due to partial observation and imprecise action prediction, failures are inevitable, and they can lead to "untrained states" with potentially destructive consequences.

2. **Methodology**: 
- 3D Gaussian Splatting (3DGS) to represent current scene
- Prediction network to forecast future Gaussian representation conditioned on planned actions
- Failure detection: when predicted future deviates significantly from real post-execution observation
- Self-correction: roll back to previous action with small Gaussian perturbation
- Built on PerAct framework
- Current scene estimation: regressor f_reg maps latent features to Gaussian primitives Ω = {μ_i, Σ_i, c_i, α_i, h_i}
- Training losses: color loss + semantic loss for current scene; re-rendered image loss + Chamfer distance for future scene
- Failure detection uses Chamfer distance between predicted Gaussian positions and observed point cloud
- Threshold τ to determine failure
- Rollback: a_- + ε (previous action with small perturbation)

3. **Experimental design**:
- CoppeliaSim simulation + Bullet physics engine
- Datasets: PerAct dataset (10 tasks, 166 variations) and HiveFormer dataset (6 tasks)
- 20 episodes of demonstrations per task
- Single front camera, 128×128 resolution
- M=20 additional camera views for Gaussian Splatting training
- Compared methods: PerAct, GNFactor, ManiGaussian, ACT3D
- Robustness: Colosseum benchmark (light color, object color, object texture, table color perturbations)
- Evaluation: 25 episodes per task, 3 random seeds

4. **Resources**:
- PyTorch platform
- 2× A800 GPUs
- Training: 300,000 iterations on PerAct, 100,000 iterations on HiveFormer
- Batch size 2
- LAMB optimizer, lr 5e-4 with cosine scheduler
- 3000 iterations in first phase (action loss only)
- Physical workspace 1m³, voxel resolution 100
- 16,384 points in pointcloud
- N=16,384 Gaussian primitives
- Noise scale 0.001, threshold τ=0.40

5. **Experiment quantity and sufficiency**:
- Multiple tables: Table 1 (PerAct dataset, 10 tasks), Table 2 (HiveFormer dataset, 6 tasks), Table 3 (ablation), Table 4 (robustness), Table 5 (threshold sensitivity)
- Ablation: w/o vs w/ self-correction
- Threshold sensitivity: 6 values tested
- 4 perturbation types in robustness
- Multiple metrics: Planning, Long, Tools, Motion, Screw, Occlusion categories
- 3 random seeds for statistical significance
- Relatively comprehensive

6. **Main conclusions**:
- Outperforms SOTA by 12.0% on PerAct dataset average (56.4% vs 44.4%)
- 13.3% improvement on HiveFormer dataset
- Best in 7/10 tasks on PerAct, 5/6 on HiveFormer
- Self-correction provides ~18% improvement
- Better robustness on Colosseum
- Low sensitivity to threshold (50%+ across 0.3-0.5)

7. **Strengths**:
- Novel integration of 3DGS for foresight prediction
- Point cloud distance (Chamfer) is more stable than RGB comparison
- Modular design that can integrate with other methods
- Comprehensive evaluation
- Good robustness
- Two-phase training scheme

8. **Limitations**:
- Only tested in simulation (CoppeliaSim)
- Performance depends on threshold τ
- Limited tasks (10+6)
- Comparison with point cloud rather than rendered RGB might miss some visual details
- Gaussian noise perturbation may not always lead to recovery
- Single front camera
- No real-world experiments
- Reliance on additional M=20 camera views for training supervision

Let me organize this into a clean Markdown summary.
</think>
# 论文总结：基于高斯泼溅预见的自校正机器人操作

## 1. 核心问题与研究动机

- **任务背景**：语言条件（language-conditioned）的机器人操作在非结构化环境中面临巨大挑战，机器人需要执行多步骤、涉及工具使用与几何推理的复杂任务。
- **失败不可避免**：由于部分观测（遮挡）、环境扰动以及动作预测的不精确性，策略执行失败是常态而非例外。
- **关键痛点——"未训练状态"**：现有策略多基于专家成功轨迹训练，一旦失败发生，机器人可能进入训练数据未覆盖的"未训练状态"，若继续按原计划执行，可能造成破坏性后果（如推倒物体、碰撞等）。
- **核心目标**：在执行层面（execution level）实现"失败检测 + 自动回滚 + 重新规划"的闭环自校正能力，填补现有方法在容错恢复方面的空白。

## 2. 方法论

### 2.1 核心思想
- 定义失败 = 动作执行后的实际观测与预期视觉结果之间的不一致。
- 用 **3D 高斯泼溅（3DGS）** 表示当前场景，并训练预测网络根据规划动作预测未来场景的高斯表示。
- 通过对比预测与实际观测的几何差异检测失败，触发回滚与重新规划。

### 2.2 关键技术细节

**当前场景估计（Current Scene Estimation）**：
- 特征提取：$z = f_{\text{sem}}(o)$，对 RGB-D 观测 $o$ 提取语义特征。
- 高斯回归：$\Omega = f_{\text{reg}}(z; \theta_{\text{reg}})$，输出 $N$ 个高斯基元 $g_i = (\mu_i, \Sigma_i, c_i, \alpha_i, h_i)$，包含位置、方差、颜色、不透明度、语义特征。
- 训练损失：$\ell_{\text{cur}} = \sum_m \|\tilde{I}_m - I_m\|_F^2 + \lambda_{\text{sem}} \sum_m (1 - \cos(\tilde{H}_m, \psi(I_m)))$，包含颜色重建损失与语义一致性损失，其中 $\psi(\cdot)$ 采用 Stable Diffusion 特征提取器。

**未来场景预测（Future Scene Prediction）**：
- 将未来视为当前刚体的物理变换，预测网络为每个高斯输出位置偏移 $\Delta\mu_i$ 与旋转偏移 $\Delta r_i$。
- 训练损失：$\ell_{\text{pre}} = \sum_m \|\tilde{I}_m^+ - I_m^+\|_F^2 + \lambda_p D(\{\mu_i^+\}, P_{\text{gt}})$，包含图像重建损失与基于 Chamfer 距离的点云损失。

**失败检测与自校正**：
- 一致性度量：$d = D(\{\mu_i^+\}, P)$，即预测高斯中心点集与执行后观测点云之间的 Chamfer 距离（选用点云而非 RGB 渲染图，因为几何结构更稳定、不受光照影响）。
- 判定准则：若 $d > \tau$（阈值），判定为失败。
- 回滚操作：执行 $a^- + \epsilon$，即回退到上一步动作并叠加一个小幅高斯扰动 $\epsilon \sim \mathcal{N}(0, 0.001^2)$，避免陷入相同失败状态。

### 2.3 整体框架
- 基于 PerAct 骨干网络，动作定义为 $(a_{\text{pos}}, a_{\text{angle}}, a_{\text{grip}}, a_{\text{coll}})$ 四元组（位置、角度、夹爪开合、碰撞标志）。
- **两阶段训练**：
  1. 第一阶段（约 3000 次迭代）：仅优化动作分类交叉熵损失 $\ell_{\text{action}}$。
  2. 第二阶段：联合优化 $\ell_{\text{total}} = \ell_{\text{action}} + \lambda_{\text{cur}}\ell_{\text{cur}} + \lambda_{\text{pre}}\ell_{\text{pre}}$。
- 自我校正模块可作为通用插件，理论上可与其他语言条件操作方法结合。

## 3. 实验设计

### 3.1 仿真环境与数据集
- **仿真平台**：CoppeliaSim + Bullet 物理引擎。
- **数据集**：
  - PerAct 数据集：10 个任务，共 166 个变体（close jar、open drawer、sweep to dustpan、meat off grill、turn tap、slide block、put in drawer、reach and drag、push buttons、stack blocks）。
  - HiveFormer 数据集：6 个任务（basketball in hoop、change clock、phone on base、put rubbish in bin、stack wine、turn oven on）。
- **演示数据**：每个任务采集 20 条专家演示。
- **观测配置**：单个前置相机，128×128 RGB-D；训练 3DGS 时额外使用 $M=20$ 个相机视角提供监督。

### 3.2 对比方法
- PerAct、Perceiver-Actor 多任务 Transformer 基线
- GNFactor（结合 NeRF 的可泛化神经特征场）
- ManiGaussian（动态 3DGS + 语义特征）
- ACT3D（3D 特征场 Transformer）

### 3.3 评估指标
- 成功率为主要指标，每任务评估 25 个 episode，3 个随机种子。
- 任务分组：Planning（多子目标）、Long（>10 步）、Tools（需工具）、Motion（精确抓取）、Screw（拧动）、Occlusion（几何推理）。
- 鲁棒性评估：Colosseum 基准，覆盖光照颜色、物体颜色、物体纹理、桌面颜色四种扰动。

## 4. 资源与算力

- **GPU**：2 块 NVIDIA A800。
- **训练时长**：
  - PerAct 数据集：300,000 次迭代。
  - HiveFormer 数据集：100,000 次迭代。
- **批大小**：2。
- **优化器**：LAMB，初始学习率 $5 \times 10^{-4}$，余弦退火调度。
- **超参数**：物理工作空间 $1\,\text{m}^3$，体素分辨率 100；点云点数 16,384；高斯基元数 $N=16{,}384$；扰动 $\epsilon$ 缩放因子 0.001；失败阈值 $\tau=0.40$。
- **数据增强**：SE(3) 增强。
- 注：论文未明确报告 wall-clock 训练时间。

## 5. 实验数量与充分性

- **主结果表**（Table 1）：PerAct 数据集 10 个任务 + 分组平均。
- **跨数据集验证**（Table 2）：HiveFormer 数据集 6 个任务。
- **消融实验**（Table 3）：对比有/无自校正模块在 6 类任务分组上的表现。
- **鲁棒性分析**（Table 4）：Colosseum 基准上 4 种扰动 × 2 个任务。
- **阈值敏感性**（Table 5）：6 个 $\tau$ 值（0.25–0.50）。
- **定性可视化**（Figure 4、5）：新视角合成、预测点云对比。
- **客观性评估**：
  - 使用 3 个随机种子报告均值与标准差，体现统计严谨性。
  - 任务覆盖多类别（规划、长时序、工具使用等），具备一定全面性。
  - 不过评估仍局限于仿真环境，缺乏真实机器人实验。

## 6. 主要结论与发现

- **性能领先**：在 PerAct 数据集 10 任务上以 56.4% 平均成功率超过 SOTA 12.0%（前最佳 ManiGaussian 44.4%）；在 HiveFormer 数据集上以 59.3% 超过 SOTA 13.3%。
- **任务覆盖优势**：在 7/10 PerAct 任务和 5/6 HiveFormer 任务上取得最佳，9/10 任务排名前二。
- **自校正贡献显著**：有/无自校正模块对比，平均成功率从 38.0% 提升至 56.4%，提升约 18 个百分点。
- **鲁棒性优势**：在 Colosseum 全部四种扰动下均优于 PerAct 和 GNFactor。
- **阈值鲁棒**：$\tau$ 在 0.3–0.5 区间内成功率均 >50%，对阈值选择不敏感。
- **类别提升**：Planning 类任务提升 14.0%，Tools 类提升 12.0%，对需要多步协调与工具使用的任务改进尤为明显。

## 7. 优点

- **新颖的问题视角**：首次将 3DGS 与"预见式失败检测"结合用于机器人自校正，思路独特。
- **表示选择有据可循**：
  - 3D 高斯显式表示便于直接施加变换。
  - 点云 Chamfer 距离比 RGB 渲染对比更稳定、不受光照干扰。
- **模块化设计**：自校正模块可与现有语言条件策略（如 PerAct）解耦集成，具备较好可扩展性。
- **评测全面**：跨数据集、跨任务类别、跨扰动维度、消融与超参分析相结合，证据链较完整。
- **可视化验证充分**：提供新视角合成与未来点云预测的可视化，直观展示方法有效性。
- **工程细节完整**：算法伪代码、损失函数、两阶段训练流程、超参数均给出。

## 8. 不足与局限

- **仅仿真验证**：所有实验在 CoppeliaSim 中进行，缺乏真实机器人部署与 sim-to-real 分析，限制实际应用说服力。
- **观测视角限制**：仅使用单前置相机 + 训练时 20 个额外视角，依赖较为理想化的多视角监督，在遮挡严重或单目部署场景的可行性存疑。
- **失败检测粒度粗**：仅依赖单一 Chamfer 距离阈值 $\tau$，未讨论对不同任务/不同扰动自适应阈值的可能性，存在误报与漏报风险。
- **回滚策略简单**：仅回退到上一步 + 固定尺度高斯扰动，未考虑更智能的重规划（如结合 LLM 推理），对多次连续失败情况缺乏处理。
- **高斯基元规模大**：$N=16{,}384$ 个高斯带来较大计算与显存开销，对实时性要求严格的真实场景部署构成挑战。
- **对比基线时效性**：ManiGaussian 等 3DGS 方法仍在快速迭代，缺少与最新通用机器人基础模型（如 OpenVLA、π₀ 等）的对比。
- **作者指出的未来工作**：承认当前仅聚焦执行级错误，未来希望结合 LLM 推理能力扩展到长期规划层面的失败检测与修正。

（完）
