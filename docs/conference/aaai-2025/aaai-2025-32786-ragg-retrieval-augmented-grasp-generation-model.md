---
title: "RAGG: Retrieval-Augmented Grasp Generation Model"
title_zh: RAGG：检索增强的抓取生成模型
authors: "Zhenhua Tang, Bin Zhu, Yanbin Hao, Chong-Wah Ngo, Richang Hong"
date: 2025-04-11
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/32786/34941"
tags: ["query:rob-il"]
score: 5.0
evidence: 模仿人类交互模式生成抓取，机器人操作相关
tldr: 该论文针对意图驱动的抓取生成中存在的操作模糊性与模态鸿沟问题，借鉴人类面对新物体时先模仿相似物体交互模式再细调的机制，提出两阶段RAGG模型。第一阶段通过检索增强扩散模型从知识库中检索最相关交互实例以显式引导抓取生成，第二阶段进一步进行结构稳定的抓取细化。实验表明该方法在抓取质量与语义对齐上均取得提升。该工作为基于视觉的机器人操作提供了一种结合检索先验与生成式抓取的新范式。
source: AAAI-2025-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32786/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 851, \"height\": 472, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32786/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1835, \"height\": 984, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32786/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 845, \"height\": 532, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32786/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 879, \"height\": 274, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2025-accepted/aaai-2025-32786/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 884, \"height\": 262, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32786/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1825, \"height\": 780, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32786/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 854, \"height\": 669, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2025-accepted/aaai-2025-32786/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 878, \"height\": 631, \"label\": \"Table\"}]"
motivation: 意图驱动抓取生成存在操作模糊性与模态鸿沟，难以生成稳定且语义一致的抓取。
method: 提出两阶段RAGG模型，结合检索增强扩散模型与结构稳定抓取细化模块。
result: 在抓取质量与语义对齐方面均取得提升，验证了检索引导机制的有效性。
conclusion: 为结合先验知识的机器人抓取生成提供了新颖而有效的解决方案。
---

## Abstract
Intent-based grasp generation inherently involves challenges such as manipulation ambiguity and modality gaps. To address these, we propose a novel Retrieval-Augmented Grasp Generation model (RAGG). Our key insight is that when humans manipulate new objects, they initially mimic the interaction patterns observed in similar objects, then progressively adjust hand-object contact. Consequently, we develop RAGG as a two-stage approach, encompassing retrieval-guided generation and structurally stable grasp refinement. In the first stage, we propose a Retrieval-Augmented Diffusion Model (ReDim), which identifies the most relevant interaction instance from a knowledge base to explicitly guide grasp generation, thereby mitigating ambiguity and bridging modality gaps to ensure semantically correct manipulation. In the second stage, we introduce a Progressive Refinement Network (PRN) with Kolmogorov-Arnold Network (KAN) layers to refine the generated coarse grasp, employing a Structural Similarity Index loss to constrain the spatial relationship between the hand and the object, thus ensuring the stability of the grasp. Extensive experiments on the OakInk and GRAB benchmarks demonstrate that RAGG achieves superior results compared to state-of-the-art approach, indicating not only better physical feasibility and controllability but also strong generalization and interpretability for unseen objects.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the RAGG paper following a specific 8-point structure. Let me analyze the paper carefully and produce a well-structured Markdown response.

The paper is about Retrieval-Augmented Grasp Generation (RAGG), addressing intent-based grasp generation challenges. Let me organize the key information:

1. Core problem: Manipulation ambiguity and modality gaps in intent-based grasp generation
2. Method: Two-stage approach - Retrieval-Augmented Diffusion Model (ReDim) + Progressive Refinement Network (PRN) with KAN layers and SSIM loss
3. Experiments: OakInk and GRAB datasets, compared with GrabNet baseline
4. Resources: Not explicitly mentioned in the paper
5. Experiment quantity: Multiple comparisons, ablation studies, qualitative analysis
6. Conclusions: Superior physical feasibility, controllability, generalization to unseen objects
7. Strengths: Novel RAG mechanism, interpretability, modular design
8. Limitations: Limited detail on computational resources, only comparison with GrabNet

Let me write this up in Chinese with proper Markdown formatting.</think>

# RAGG：检索增强的抓取生成模型 — 论文总结

## 1. 核心问题与研究背景

- **任务定义**：给定一个 3D 物体（点云 / 网格）和一个文本操作意图（如 "use" 或 "hold"），生成与之匹配的 3D 手部抓取姿态，使其满足物理可行、语义正确且对未见物体具有泛化能力。
- **两大核心挑战**：
  - **操作模糊性**：同一意图可能对应多种合理姿态，导致生成模型难以收敛。
  - **跨模态鸿沟**：文本意图、物体点云与手部姿态之间存在显著的语义差距。
- **现有方法局限**：
  - GrabNet 等方法将三种模态压缩到统一潜空间重建，性能远不及人类交互水平。
  - Text2Grasp、DiffH2O、SemGrasp 等依赖 GPT 生成的高质量文本描述，缺乏对罕见物体的灵活性。
- **作者的关键洞察**：人类操纵新物体时，会先"模仿"相似物体的交互模式，再逐步调整接触细节 → 引入检索增强生成（RAG）机制作为类比。

## 2. 方法论

### 2.1 整体框架（RAGG 两阶段）
- **第一阶段：检索引导生成** — Retrieval-Augmented Diffusion Model（**ReDim**）
- **第二阶段：结构稳定抓取细化** — Progressive Refinement Network（**PRN**）

### 2.2 联合检索机制（Joint Retrieval）
- **知识库构建**：
  - 用 **BPS（基点集）** 提取物体点云特征 $f^{obj}_i \in \mathbb{R}^{4096}$，并将意图转为 one-hot 编码 $f^{int}_i$；
  - 拼接得到物体-意图联合特征 $F_i = [f^{obj}_i, f^{int}_i] \in \mathbb{R}^{4097}$；
  - 使用 **K-Means** 聚类（按余弦距离）成 $K$ 类，每类保留 $L$ 个最近样本，共得到 $K \times L$ 条检索条目。
- **检索过程**：
  - 计算查询条件与知识库条目的余弦相似度 $s_i = \langle [f^{obj}, f^{int}], F^{KB}_i \rangle$；
  - 取出 Top-$v$（论文取 $v=1$）个最相关抓取构成参考集合 $\mathcal{M}$。

### 2.3 检索增强扩散模型（ReDim）
- **扩散过程**（DDPM 风格）：
  $$q(y_t | y_0) := \sqrt{\bar{\alpha}_t} y_0 + \varepsilon \sqrt{1 - \bar{\alpha}_t}$$
  其中 $\bar{\alpha}_t = \prod_{s=0}^{t} \alpha_s$，$\alpha_t = 1 - \beta_t$，采用余弦噪声调度。
- **去噪器结构**：由 **Grasp Embedding** → 多个 **Semantics Calibration Transformer (SCT)** 块 → 生成头（Generation Head）组成。
  - 输入去噪结果 $\tilde{y}_0 = D(y_t, i, o, t, m)$；
  - **SCT 块**：用查询为 $Q = \text{Linear}(f_y)$，键值由 $[f_i, f_o, f_m, f_t]$ 经线性变换得到；通过 cross-attention + 自适应 AdaLN（回归 $\alpha, \beta, \gamma$ 参数）实现多模态融合；
  - **生成头**：经 MANO 层输出手部 mesh $\tilde{y}_0 \in \mathbb{R}^{778 \times 3}$，**直接预测干净信号**（类似 MDM）而非噪声。
- **损失函数**：
  - 重建损失 $L_{rec} = \lambda_1 \|\tilde{y}_0 - y_0\|^2 + \lambda_2 \|\tilde{e}_0 - e_0\|^2$
  - 双向接触损失 $L_{h2o} + L_{o2h}$（手到物体、物体到手的 signed distance）
  - 权重 $\lambda_1=\lambda_3=34.825$，$\lambda_2=\lambda_4=29.85$

### 2.4 渐进式细化网络（PRN）
- **结构**：3 个残差块，每个残差块由两层 **KAN（Kolmogorov-Arnold Network）** 组成（即 **ResKAN**），提供强非线性表示能力。
- **核心创新 — SSIM 损失**：
  - 不同于传统的逐顶点损失（容易导致手指整体离开物体），改为对手掌 17 个局部区域计算 **结构相似性指数 (SSIM)**；
  - 对每个区域的"距离集合" $\hat{d}$ 与真实距离 $d_0$ 计算均值、方差、协方差，得到 SSIM score；
  - $\text{SSIM}(\hat{d}, d_0) = \frac{(2\mu_1\mu_2+C_1)(2\sigma_{12}+C_2)}{(\mu_1^2+\mu_2^2+C_1)(\sigma_1^2+\sigma_2^2+C_2)}$
  - $C_1=0.0001, C_2=0.0009$，跨区域求和作为损失项，约束手-物体空间关系。
- **优化策略**：三轮迭代，分别施加 contact / contact+reconstruction / contact+reconstruction+SSIM 损失。

## 3. 实验设计

### 3.1 数据集
- **OakInk**：1,800 个物体模型 / 32 类。采用 **Yang et al. (2022)** 的协议，选取 9 类（瓶子、相机、圆柱瓶、眼镜、游戏手柄、洗液泵、马克杯、笔、喷雾器）× 2 种意图（use / hold）训练与测试，并额外选 **3 个未见类别**（碗、耳机、刀）评估泛化能力。
- **GRAB**：真实人类抓取，51 个物体 / 10 位受试者。选 S1 受试者 pass 操作下的物体进行域外测试，包括 2 个 OakInk 同类（相机、马克杯）与 2 个未见类（红酒杯、牙膏）。

### 3.2 评估指标
1. **穿透深度 (Penetration Depth)** ↓ — 物理可行性
2. **实体相交体积 (Intersection Volume)** ↓ — 物理可行性
3. **仿真位移 (Simulation Displacement)** ↓ — 物理稳定性
4. **聚类中心距离 (Center Distance via t-SNE)** ↑ — 可控性
5. **人类感知成功率**（5 名志愿者盲评）↑

### 3.3 对比方法
- 主要对比 **GrabNet**（由 Yang et al. 扩展用于意图驱动任务）— 实质上是 SOTA baseline；
- 实验内容涉及与最新 SOTA（DiffH2O、Text2Grasp、SemGrasp 等）相关的讨论，但定量表上仅与 GrabNet 对比。

## 4. 资源与算力

- 论文中 **未明确披露** 任何 GPU 型号、数量、训练时长或计算开销信息；
- 仅在附录与正文提示方法使用 PyTorch 框架并依赖 MANO 模型，但未给出具体训练硬件与环境配置。

## 5. 实验数量与充分性

- **定量对比**：在 OakInk 上对 9 类物体 × 2 意图 × 4 项物理指标 + 1 项可控性 + 1 项感知率（共约 108 个数据点），并在 OakInk 未见 3 类与 GRAB 域外 4 类上报告 4 项指标。
- **分布分析**：图 3 给出穿透深度的样本分布直方图，附录用类似方式展示仿真位移分布。
- **消融研究**：表 3 列出 9 种组件配置（Base / OriR / JR / PRN 组合），系统验证了 ReDim、JR 与 PRN 各自贡献，并验证 PRN 可即插即用地提升 GrabNet。
- **定性分析**：图 4（已见类）与图 5（参考样本与生成抓取的对应关系）展示视觉质量与可解释性。
- **充分性评价**：
  - **优势**：消融维度划分细致，覆盖 seen / unseen / out-of-domain 三类场景，加入感知评测。
  - **局限**：定量对比基线仅 1 个（GrabNet），未与 DiffH2O、Text2Grasp、SemGrasp 等同期 SOTA 直接比较；未见类别样本量、per-category 样本数及统计显著性检验未给出；t-SNE 距离作为"可控性"的代理指标存在主观性。

## 6. 主要结论与发现

- 在 OakInk 上 RAGG 各项物理指标全面优于 GrabNet：平均穿透 0.506 vs 0.513 cm（hold），0.410 vs 0.541 cm（use）；相交体积 3.667 vs 5.165 cm³；仿真位移 1.274 vs 1.964 cm。
- **可控性大幅提升**：聚类中心距离从 33.094 提升至 61.395；人类感知成功率从 82.46% 提升至 93.44%。
- **泛化性**：在 OakInk 未见 3 类与 GRAB 域外 4 类上，RAGG 在所有相交体积指标上均优于 GrabNet，验证了检索先验在迁移场景下的价值。
- **消融结论**：扩散模型本身（#4 vs #1）即可降低穿透；JR（#6 vs #4）显著增强可控性；PRN（#9 vs #7）使穿透下降 0.010 cm、相交体积下降 0.473 cm³、位移下降 0.351 cm；PRN 单独应用于 GrabNet（#3 vs #2）也能持续提升物理可行性。
- **可解释性**：生成结果与检索样本在姿态上高度对齐（如未见耳机模仿"使用游戏手柄"的姿态），验证了 RAG 机制的有效性。

## 7. 优点与亮点

- **RAG 与扩散模型结合的新范式**：首次将检索增强机制系统性地引入 3D 抓取生成任务，为扩散模型提供显式先验，缓解了文本提示的依赖。
- **Semantics Calibration Transformer (SCT)**：通过自适应 AdaLN + cross-attention 实现文本、点云、参考抓取、时间步四种条件信号的有效对齐融合。
- **KAN-based Refinement (ResKAN)**：用 Kolmogorov-Arnold Network 替代传统 MLP，提供更优的非线性表达能力，且模块可即插即用地嵌入其他生成模型。
- **SSIM 结构损失**：用局部空间结构相似度替代单纯顶点损失，缓解了"所有手指同时远离物体"的失败模式，提升抓取稳定性。
- **可解释性**：检索到的参考样本使生成过程具备人类可理解的"模仿-调整"逻辑，对未见物体的迁移尤为友好。
- **消融设计细致**：9 组组件组合逐项验证，论证了 JR 与 PRN 各自的必要性以及 PRN 的可迁移性。

## 8. 不足与局限

- **对比基线单一**：定量实验只与 GrabNet 一家对比，未与同期 SOTA（如 DiffH2O、Text2Grasp、SemGrasp）直接同表评测，难以全面判断相对优势。
- **资源与算力披露缺失**：未给出 GPU 型号、数量、训练耗时、推理时间等关键信息，难以评估方法的实际部署成本。
- **未见类别测试样本有限**：仅 3 类（OakInk）与 4 类（GRAB），且未报告每类样本数及统计检验，可能存在结果波动。
- **可控性指标客观性不足**：t-SNE 中心距离受随机种子与超参影响较大；5 名志愿者的主观评判也难以标准化，存在偏差风险。
- **Top-$v=1$ 的简化**：检索仅返回单一最相关样本，未探索多参考融合或不确定性量化。
- **依赖 MANO 与高质量知识库**：方法对 MANO 参数化模型和预构建交互知识库存在依赖，对极端未见物体（如完全无相似样本）的退化情况未作讨论。
- **应用边界**：论文聚焦静态抓取合成，未涉及动态轨迹、双手操作、对不同人手型的适配等扩展场景。

（完）
