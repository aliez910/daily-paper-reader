---
title: "TTF-VLA: Temporal Token Fusion via Pixel-Attention Integration for Vision-Language-Action Models"
title_zh: "TTF-VLA: 通过像素-注意力整合的时间令牌融合用于视觉-语言-动作模型"
authors: "Chenghao Liu, Jiachen Zhang, Chengxuan Li, Zhimu Zhou, Shixin Wu, Songfang Huang, Huiling Duan"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38910/42872"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向视觉-语言-动作模型的时间融合方法，提升机器人操控推理质量
tldr: 针对视觉-语言-动作(VLA)模型逐帧处理视觉输入、忽视帧间时间一致性的问题，提出了TTF方法。该方法无需训练，通过结合灰度像素差异分析和注意力语义相关性评估的双维度检测，智能融合历史与当前视觉令牌。实验证明TTF有效降低了视觉噪声影响，提升了VLA模型在操控任务中的稳定性和准确性。该技术可作为即插即用模块，广泛增强现有VLA模型。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38910/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1619, \"height\": 913, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38910/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 845, \"height\": 820, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38910/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1797, \"height\": 558, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38910/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 878, \"height\": 252, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38910/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 873, \"height\": 871, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38910/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1430, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38910/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 809, \"height\": 246, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38910/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1748, \"height\": 320, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38910/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 248, \"label\": \"Table\"}]"
motivation: VLA模型逐帧处理视觉输入，忽略帧间时间一致性，易受视觉噪声干扰。
method: 提出TTF，通过双维度检测无训练地融合历史与当前视觉令牌。
result: TTF显著提升VLA模型在噪声环境下的操控性能，计算开销极小。
conclusion: TTF轻量高效，为VLA模型提供了实用的时间增强方案。
---

## Abstract
Vision-Language-Action (VLA) models process visual inputs independently at each timestep, discarding valuable temporal information inherent in robotic manipulation tasks. This frame-by-frame processing makes models vulnerable to visual noise while ignoring the substantial coherence between consecutive frames in manipulation sequences. We propose Temporal Token Fusion (TTF), a training-free approach that intelligently integrates historical and current visual representations to enhance VLA inference quality. Our method employs dual-dimension detection combining efficient grayscale pixel difference analysis with attention-based semantic relevance assessment, enabling selective temporal token fusion through hard fusion strategies and keyframe anchoring to prevent error accumulation. Comprehensive experiments across LIBERO, SimplerEnv, and real robot tasks demonstrate consistent improvements: 4.0 percentage points average on LIBERO (72.4% vs 68.4% baseline), cross-environment validation on SimplerEnv (4.8% relative improvement), and 8.7% relative improvement on real robot tasks. Our approach proves model-agnostic, working across OpenVLA and VLA-Cache architectures. Notably, TTF reveals that selective Query matrix reuse in attention mechanisms enhances rather than compromises performance, suggesting promising directions for direct KQV matrix reuse strategies that achieve computational acceleration while improving task success rates.

---

## 论文详细总结（自动生成）

## 1. 论文的核心问题与整体含义

- **研究动机与背景**：当前视觉-语言-动作（VLA）模型在机器人操控任务中逐帧独立处理视觉输入，丢弃了相邻帧间的强时间相关性（如物体移动的连续性）。这种“时间短视”导致模型对视觉噪声（光照波动、运动模糊、传感器伪影）敏感，并忽略操控序列中固有的结构模式。论文旨在解决这一矛盾：如何在不忽略任务关键变化的前提下，有效利用历史帧中的稳定信息。
- **整体含义**：提出一种无需额外训练的时间令牌融合方法（TTF），自动识别哪些视觉区域可以安全复用历史令牌，哪些必须更新，从而提升VLA模型在噪声环境下的推理质量和任务成功率，且可作为一种即插即用模块增强现有VLA架构。

## 2. 论文提出的方法论

- **核心思想**：通过双维度检测（低层像素差异 + 高层语义相关性）为每个视觉补丁（patch）生成二值融合掩码，决定使用当前帧令牌还是复用前一帧令牌；并引入关键帧机制防止误差累积。
- **关键技术细节**：
  - **灰度像素差异检测**：将RGB转换为灰度图，计算相邻帧每个14×14 patch的平均灰度绝对差，与阈值（τ_pixel）比较得到像素掩码 m_pixel。
  - **基于注意力的语义相关性检测**：利用前一层的文本→视觉注意力或动作→视觉注意力，计算每个patch的语义重要性，通过top-k选择得到语义掩码 m_attention。
  - **融合决策**：`m_fusion = m_pixel OR m_attention`，即任一维度认为重要则从当前帧获取该patch，否则重用历史令牌。
  - **硬融合策略**：对于每个patch，融合掩码为1时保留当前令牌，为0时替换为前一帧对应位置的令牌。
  - **关键帧机制**：每K帧（默认K=3）强制对所有patch重新计算，避免误差长期累积。
- **算法流程**（文字说明）：
  1. 若当前帧是关键帧，则直接通过视觉编码器提取所有令牌。
  2. 否则，提取当前帧令牌，并利用前一帧的灰度图和注意力权重计算每个patch的融合掩码。
  3. 根据掩码将当前帧令牌与前一帧令牌融合，得到最终输入给语言模型的时间融合令牌。
- **公式示例**：
  - 融合函数：$\tilde{T}_t = F(T_t, T_{t-1}, I_t, I_{t-1}, L_t)$
  - 硬融合规则：$\tilde{t}_t^{(i)} = t_t^{(i)}$ if $m_{fusion}^{(i)}=1$, else $t_{t-1}^{(i)}$

## 3. 实验设计

- **数据集与场景**：
  - **LIBERO仿真**：4个任务套件（Object, Spatial, Goal, Long），每套含10个任务×20 episodes=200 episodes/套，共800 episodes。
  - **SimplerEnv仿真**：3个跨环境任务（Move Near、Pick Coke Can、Drawer），总episode数为240+300+216=756。
  - **真实机器人任务**：Franka Research 3，3类任务（单物体抓放、多物体顺序操、接触式关门），每任务20 episodes，共60 episodes。
- **对比方法**：
  - 基线：OpenVLA（任务微调版）和VLA-Cache。
  - TTF分别应用于OpenVLA和VLA-Cache，比较成功率。
  - 消融实验：仅像素检测、仅注意力检测、联合检测；关键帧间隔分析（14种K值）。
- **评价指标**：任务成功率（%）和令牌复用率（fusing rate）。

## 4. 资源与算力

- 论文未明确说明所使用的GPU型号、数量、训练时长等具体算力信息。仅在真实机器人实验中提到基于OpenVLA-7B在特定数据上微调了20,000步，但未给出硬件细节。TTF方法本身是无需训练的，因此推理阶段额外计算量很小（<2%）。

## 5. 实验数量与充分性

- **实验数量**：较全面。
  - LIBERO：2种基模型×4套任务×200 episodes，总计1,600次评估（含VLA-Cache则为3,200次）。
  - SimplerEnv：仅有OpenVLA base模型，3任务×～
  - 真实机器人：1种模型，3任务×20 episodes。
  - 消融实验：维度消融（3种变体，每套任务×200 episodes）、关键帧间隔消融（14个K值，涵盖Object和Long两个任务套）。
- **充分性与公平性**：
  - 覆盖模拟与真实环境，任务多样性较好（单物体、多物体、长序列、接触式）。
  - 与VLA-Cache等现有方法对比，并在同一框架下测试了模型无关性。
  - 消融实验验证了每个组件的必要性，关键帧分析展示了性能与复用率的权衡。
  - 但存在局限：未与其他token压缩/复用方法（如ToMe、FastV、SparseVLM）进行直接比较；仅在两个VLA架构上验证；真实任务样本量较小（20 episodes），可能存在统计波动。

## 6. 论文的主要结论与发现

- TTF在LIBERO上平均提高4.0个百分点（绝对提升），从68.4%到72.4%；SimplerEnv相对提升4.8%；真实机器人相对提升8.7%。
- 方法具有模型无关性，对OpenVLA和VLA-Cache均有效。
- 双维度检测（像素+注意力）优于单独使用任一维度，且逻辑或（OR）融合策略能在较高复用率下保持性能。
- 关键帧机制有效防止误差累积，最佳K值约为3–15区间。
- **意外发现**：在VLA-Cache+TTF中，由于融合导致静态patch的Query矩阵被隐式复用（接近KQV全复用），不仅没有损害性能，反而有所提升，尤其对长序列任务。这提示未来可直接设计KQV矩阵复用策略，同时实现加速和性能改进。

## 7. 优点

- **训练免费**（training-free），即插即用，无需修改模型权重。
- **轻量高效**：额外计算开销<2%，适合实时控制。
- **双维度检测设计合理**：灰度像素差异捕捉低层运动，注意力语义相关性捕捉任务重要区域，两者互补。
- **关键帧机制**简洁有效，在性能与历史利用之间取得平衡。
- **实验全面**：覆盖仿真多个benchmark和真实机器人，验证了跨环境泛化能力。
- **模型无关性**：成功应用于OpenVLA和VLA-Cache两种架构，证明通用性。
- **揭示有益结论**：Query矩阵的复用反而提升性能，为后续加速研究提供方向。

## 8. 不足与局限

- **实验对比不足**：未与主流的视觉令牌压缩/复用方法（如ToMe、FastV、SparseVLM）直接比较，这些方法也可用于VLA时间维度。
- **基线模型范围有限**：仅测试OpenVLA和VLA-Cache，未在更多VLA模型（如RT-2、Octo、π0）上验证。
- **真实机器人实验规模较小**：每个任务仅20 episodes，可能不足以展示统计显著性；且任务种类偏少。
- **超参数依赖**：像素阈值和注意力top-k等参数需手动设定，虽然论文称对LIBERO和SimplerEnv使用相同参数表现稳健，但跨更广域环境可能需要调整。
- **单历史帧依赖**：仅融合前一帧，未探索多帧历史或自适应时间窗口。
- **注意力来源限制**：采用前一帧的注意力权重，若前一帧注意力不可靠（如初始帧）可能导致误判。
- **计算资源信息缺失**：未提供训练/推理所用的GPU型号、数量及时长，不利于复现和效率对比。
- **潜在公平性问题**：VLA-Cache+TTF中隐式Query复用未经显式隔离实验，其收益可能部分来自融合策略而非复用本身。

（完）
