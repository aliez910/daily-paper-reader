---
title: "FlowRAM: Grounding Flow Matching Policy with Region-Aware Mamba Framework for Robotic Manipulation"
title_zh: FlowRAM：基于区域感知 Mamba 的流匹配机器人操纵策略
authors: "Wang, Sen, Wang, Le, Zhou, Sanping, Tian, Jingyi, Li, Jiayi, Sun, Haowen, Tang, Wei"
date: 2025-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2025/papers/Wang_FlowRAM_Grounding_Flow_Matching_Policy_with_Region-Aware_Mamba_Framework_for_CVPR_2025_paper.pdf"
tags: ["query:rob-il"]
score: 8.0
evidence: 用流匹配生成式策略将视觉观测映射为操纵动作
tldr: 现有基于扩散的机器人操纵策略推理迭代去噪，计算效率低。本文提出 FlowRAM 框架，采用流匹配策略结合区域感知 Mamba 结构进行三维场景理解，兼顾精度与效率。该方法在多模态信息处理和动作生成上实现加速，为高精度机器人操纵提供了高效的视觉到动作映射方案。
source: CVPR-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 855, \"height\": 534, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 911, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1804, \"height\": 629, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1788, \"height\": 451, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 869, \"height\": 482, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 861, \"height\": 542, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1801, \"height\": 405, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 859, \"height\": 386, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 857, \"height\": 262, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2025-accepted/cvpr-2025-wang-flowram-grounding-flow-matching-policy-with-region-aware-mamba-framework-for-cvpr-2025-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 854, \"height\": 350, \"label\": \"Table\"}]"
motivation: 扩散策略推理慢，难以满足高精度操纵任务的效率需求。
method: 提出流匹配策略与区域感知 Mamba 框架，实现高效三维感知与动作生成。
result: 在高精度操纵任务中兼顾精度与推理效率。
conclusion: 为视觉驱动的生成式操纵策略提供了更高效的替代方案。
---

## Abstract
Robotic manipulation in high-precision tasks is essential for numerous industrial and real-world applications where accuracy and speed are required. Yet current diffusion-based policy learning methods generally suffer from low computational efficiency due to the iterative denoising process during inference. Moreover, these methods do not fully explore the potential of generative models for enhancing information exploration in 3D environments. In response, we propose FlowRAM, a novel framework that leverages generative models to achieve region-aware perception, enabling efficient multimodal information processing. Specifically, we devise a Dynamic Radius Schedule, which enables adaptive perception, facilitating transitions from global scene comprehension to fine-grained geometric details. Furthermore, we integrate state space models to integrate multimodal information, while preserving linear computational complexity. In addition, we employ conditional flow matching to learn action poses by regressing deterministic vector fields, which simplifies the learning process while maintaining performance. We verify the effectiveness of the FlowRAM in the RLBench, an established manipulation benchmark, and achieve state-of-the-art performance. The results demonstrate that FlowRAM achieves a remarkable improvement, particularly in high-precision tasks, where it outperforms previous methods by 12.0% in average success rate. Additionally, FlowRAM is able to generate physically plausible actions for a variety of real-world tasks in less than 4 time steps, significantly increasing inference speed.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "FlowRAM: Grounding Flow Matching Policy with Region-Aware Mamba Framework for Robotic Manipulation" based on the provided content. I need to organize it according to 8 specific points and use Markdown formatting.

Let me analyze the paper content carefully:

1. **Core problem and motivation**: Diffusion-based robotic manipulation policies are slow due to iterative denoising, and they don't fully exploit generative models for 3D scene understanding, especially in high-precision tasks.

2. **Methodology**: 
   - Dynamic Radius Schedule (DRS) that adapts perception region over time steps
   - State Space Models (Mamba) for multimodal fusion with linear complexity
   - Conditional Flow Matching (CFM) for fast action generation
   - Key formulas: CFM loss, ODE, DRS radius scheduling

3. **Experimental design**:
   - RLBench benchmark
   - 10 multi-task settings, 7 high-precision tasks
   - 6 real-world tasks
   - Baselines: PerAct, GNFactor, ManiGaussian, Act3D, RVT-2, 3D Diffuser Actor

4. **Resources**:
   - NVIDIA RTX 3090, 8 GPUs
   - 300K training steps, batch size 320
   - AdamW optimizer, learning rate 1e-4

5. **Experimental quantity and sufficiency**:
   - Multi-task (10 tasks), high-precision (7 tasks), real-world (6 tasks)
   - Ablation studies on architecture, modules, time steps
   - 3 random seeds for variance

6. **Main conclusions**: SOTA performance, especially 12% improvement on high-precision tasks, less than 4 inference steps

7. **Strengths**: Region-aware perception, efficient multimodal fusion, fast inference

8. **Limitations**: Limited real-world evaluation, no detailed analysis of failure cases, etc.

Let me write this up in proper Markdown format.
</think>
# FlowRAM 论文总结

## 1. 核心问题与研究动机

- **任务背景**：在高精度机器人操纵任务（如插入 USB、拧螺丝、插充电头等）中，机器人既需要全局语义理解，又需要任务相关区域的细粒度几何感知，定位或执行上的微小偏差就会导致任务失败。
- **现有方法的不足**：
  - 确定性策略难以建模高维、连续且多模态的动作分布，泛化能力有限。
  - 基于扩散模型的策略（如 3D Diffuser Actor、Diffusion Policy）虽擅长多模态动作建模，但推理时需多步迭代去噪，速度慢，难以满足实时控制。
  - 现有 3D 感知方法（RVT、PerAct、Act3D 等）要么依赖高分辨率体素、要么对任务相关区域的局部几何细节关注不足，在高精度任务上性能受限。
- **本文目标**：同时提升精度与效率，提出一种兼顾区域感知 3D 表征与快速动作生成的统一框架。

## 2. 方法论

### 2.1 整体思路
- 用 **条件流匹配（CFM）** 替代扩散过程，直接回归一个确定性的速度场，将噪声沿 ODE 快速搬运到目标动作分布，省去多步去噪。
- 利用 **流匹配生成过程本身** 作为调度信号，驱动 3D 感知半径从全局逐步收缩到任务相关区域，实现"全局语义 → 局部几何"的渐进聚焦。
- 用 **Mamba（选择性状态空间模型）** 融合多模态 token（点云、RGB、文本指令、噪声化位姿、本体感知），保持线性计算复杂度。

### 2.2 关键技术细节
- **Dynamic Radius Schedule (DRS)**：
  - 在离散时间步 $i = 0, 1, \dots, N$ 上，生成一系列区域感知 mask $M_i = \{(p_i, r_i)\}$，其中 $p_i$ 为第 $i$ 步的噪声化末端位置，$r_i$ 为感知半径。
  - $r_i$ 随时间步单调递减：$r_{\min} \le r_i < r_{i-1} < \dots < r_0$，文中采用线性策略 $r_i = (1 - i)(r_0 - r_{\min}) + r_{\min}$，也可替换为余弦退火等形式。
  - 在每个区域内用 Farthest Point Sampling (FPS) 进行高分辨率点采样，既保留全局信息又突出任务相关几何细节。
- **多模态 Token 序列化**：
  - 点云分支：经 DRS 采样后用 PointMamba 编码得到几何特征 $F_{\text{geo}} \in \mathbb{R}^{N_1 \times C}$。
  - 图像分支：用 CLIP + FPN 处理多视角 RGB 得到语义特征 $F_{\text{rgb}} \in \mathbb{R}^{N_2 \times C}$。
  - 文本与本体感知：CLIP 文本编码得到 $F_{\text{text}}$，噪声化位姿投影得到 $F_{\text{open}}$。
  - 拼接为 $F_{\text{in}} = \mathrm{concat}(F_{\text{geo}}, F_{\text{rgb}}, F_{\text{text}}, F_{\text{open}})$，再送入 Mamba 块（含 LN、线性层、Conv1d、SiLU 激活、SSM、Gated MLP 等）。
- **基于 CFM 的策略学习**：
  - 状态 $x_t = t x_1 + (1-t) x_0$，目标速度场 $u(x_t) = \frac{dx_t}{dt} = x_1 - x_0$。
  - 参数化速度场网络 $v_\theta(x_t, t, C)$ 由 SSM + MLP 构成，并使用 AdaLN 注入条件 $C$（融合特征、指令、本体感知）。
  - 损失函数：$L_{\text{CFM}} = \mathbb{E}_{t, x_0, x_1} \|x_1 - x_0 - v_\theta(x_t, t, C)\|^2$，辅以二分类交叉熵损失 $L_{\text{open}}$ 预测夹爪开合状态。
  - 推理：$x_{t+\Delta t} = x_t + v_\theta(x_t, t, C) \Delta t$，从 $t=0$ 积分到 $t=1$；实验中通常只需 2–4 步即可得到关键帧位姿。
- **动作表示**：6-DoF 末端位姿（位置 + 6D 连续旋转 + 夹爪开合），避免四元数不连续问题；采用关键帧（keyframe）范式。

## 3. 实验设计

- **数据集与场景**：
  - **RLBench**（基于 CoppeliaSim）仿真基准，使用 7-DoF Franka Panda 机械臂 + 平行夹爪。
  - **多任务设置**：10 个任务、20 次示范/任务、≥2 个变体、共计 166 个变体；4 个 RGB-D 相机（前、左肩、右肩、手腕），图像分辨率 $128 \times 128$，使用 BiRRT 运动规划器执行。
  - **高精度任务设置**：选自 RLBench 的 7 个高精度任务（Screw Nail、Insert onto Square Peg、Plug Charger、Setup Checkers、Insert USB、Unplug Charger、Put umbrella in Stand），每个任务 100 次示范。
  - **真实机器人实验**：6-DoF UR5 + Robotiq 2F-140 夹爪 + 单目 Azure Kinect 相机，6 个语言条件任务、14 个变体、56 条示范轨迹，图像先 $2048 \times 1536$ 后下采样至 $256 \times 192$，用 MoveIt!+BiRRT 规划。
- **对比方法**：
  - 仿真：PerAct、GNFactor、ManiGaussian、Act3D、RVT-2、3D Diffuser Actor。
  - 高精度子集：Act3D、RVT-2、3D Diffuser Actor。
  - 部分基线（Act3D、3D Diffuser Actor）使用 $256 \times 256$ 图像；FlowRAM 与 RVT-2 等使用 $128 \times 128$ 图像进行公平比较。
- **评估指标**：任务成功率（%），多任务取 10 任务均值，高精度取 7 任务均值；每任务 25 个 episode，3 个随机种子报告均值与标准差。

## 4. 资源与算力

- **GPU**：NVIDIA RTX 3090。
- **GPU 数量**：8 块。
- **训练配置**：AdamW 优化器，学习率 $1 \times 10^{-4}$，batch size 320，训练 300K 步，使用 EMA 平滑权重。
- **推理速度评估**：在单卡 NVIDIA RTX 3090 上以相同输入对比扩散方法与 FlowRAM 的推理时间。
- 论文未明确披露总训练时长（小时数），仅给出训练步数与 batch size；真实机器人训练的具体算力也未单独说明。

## 5. 实验数量与充分性

- **实验覆盖**：
  - 多任务 10 任务对比（Tab. 1）。
  - 高精度 7 任务对比（Tab. 2）。
  - 架构与模块消融（Mamba vs. Transformer，DRS、点云编码器 P.E.、CFM vs. DDIM 等组合，Tab. 3）。
  - 推理步数影响（2/4/8/16/32 步，DDIM vs. CFM，Tab. 4）。
  - 高精度任务下 DDPM(100)、DDIM(4)、CFM(2/4) 性能对比（Fig. 4）。
  - 真实机器人 6 任务、14 变体、共 60 次测试（Tab. 5）。
- **充分性与公平性**：
  - 每个任务 3 个随机种子报告均值与标准差，统计意义上较为严谨。
  - 主要对比方法（RVT-2、3D Diffuser Actor 等）使用相同 GPU 类型与数量并按相同示范重训；Act3D、3D Diffuser Actor 虽使用更高图像分辨率，文中也做了说明。
  - 消融从架构（Transformer vs. Mamba）、感知（有无 DRS、点云编码器）、训练目标（CFM vs. DDIM）三个维度系统展开。
- **可能的不足**：
  - 真实机器人实验任务数与示范数仍较少（6 任务、56 条轨迹），场景泛化能力有待更广泛验证。
  - 缺少对失败案例的深入分析（什么类型的任务/变体上仍会失败、失败原因分布等）。
  - 与部分基线图像分辨率不完全一致（虽文中做了说明，仍可能带来轻微的对比偏差）。

## 6. 主要结论与发现

- **多任务 SOTA**：在 RLBench 10 任务上平均成功率 82.3%，超越 3D Diffuser Actor（78.4%）与 RVT-2（76.2%），在 Open Drawer、Put Buttons、Stack Blocks 等任务上提升尤为显著（如 Stack Blocks 提升 19.3%）。
- **高精度任务大幅领先**：在 7 个高精度任务上平均成功率 52.0%，比此前最佳方法提升 12.0%；在 Insert USB、Setup Checkers、Insert onto Square Peg 等任务上明显优于 RVT-2 和 3D Diffuser Actor。
- **推理速度优势**：CFM 仅需 2 步即可生成合理动作（4 步内即可完成真实任务），相比 DDIM 在低步数下完全失败的情况，CFM 显著更适合少步数推理。
- **模块有效性**：
  - DRS 对任务相关区域感知至关重要，去掉 DRS 后性能与速度均下降。
  - Mamba 在融合点云 + RGB + 文本等长序列时，比 Transformer 推理更快且性能相当。
  - AdaLN + CFM 联合使用带来最佳性能。
- **真实机器人验证**：在 UR5 上 6 个任务共 49/60 成功率，证明方法可迁移到现实世界，且动态半径可视化效果直观。

## 7. 优点与亮点

- **将流匹配过程与感知调度耦合**：DRA/DRS 是本文最具创意的设计，利用 ODE 时间步自然地驱动"全局→局部"的渐进感知，无需额外的显式定位网络。
- **生成式策略的高效化**：用 CFM 替代 DDPM/DDIM，显著减少推理步数，对实时机器人控制具有实际价值。
- **统一的 Mamba 多模态融合框架**：将视觉编码与策略网络都基于 SSM 搭建，保持线性复杂度，适合长序列多模态输入。
- **实验较为系统**：覆盖多任务、高精度子集、消融、推理步数、真实机器人，3 个随机种子报告误差，公平性较好。
- **真实部署验证**：不仅停留在仿真，还在 UR5 上完成 6 个真实任务，展示了方法的实用性。

## 8. 不足与局限

- **真实世界实验规模有限**：仅 6 任务、56 条示范、60 次评估，对真实场景中的光照、遮挡、物体多样性等鲁棒性尚需更大规模验证。
- **未见任务失败分析**：未提供失败案例的可视化或分类讨论，难以判断方法在哪些类型的边界条件下仍不稳定。
- **对比基线图像分辨率不一致**：Act3D、3D Diffuser Actor 使用 $256 \times 256$ 图像，FlowRAM 用 $128 \times 128$，尽管文中做了说明，仍可能略微高估相对优势。
- **依赖关键帧范式**：使用 BiRRT 等运动规划器到达关键帧，对底层控制器存在依赖，未讨论连续动作生成或闭环控制下的表现。
- **训练算力细节不完整**：未给出总训练时长、单卡显存占用、能源消耗等指标，复现成本难以精确估计。
- **DRS 对初始位置噪声敏感**：半径调度依赖于噪声化位置 $p_i$，若早期流场估计偏差较大，可能影响最终感知区域的质量，相关风险文中未深入讨论。
- **Mamba 在机器人领域的成熟度**：Mamba 模块在多模态融合中的可解释性、长序列外推能力仍处于早期，方法的鲁棒性边界有待进一步研究。

（完）
