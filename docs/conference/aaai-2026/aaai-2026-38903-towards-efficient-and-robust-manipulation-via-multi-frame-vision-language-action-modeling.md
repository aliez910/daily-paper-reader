---
title: Towards Efficient and Robust Manipulation via Multi-Frame Vision-Language-Action Modeling
title_zh: 面向高效鲁棒操作的多帧视觉-语言-动作建模
authors: "Hao Li, Shuai Yang, Yilun Chen, Xinyi Chen, Xiaoda Yang, Yang Tian, Hanqing Wang, Tai Wang, Dahua Lin, Feng Zhao, Jiangmiao Pang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38903/42865"
tags: ["query:rob-il"]
score: 8.0
evidence: 多帧视觉-语言-动作模型实现高效鲁棒的机器人操作
tldr: 针对单帧VLA模型无法充分利用时序信息的问题，CronusVLA通过单帧预训练和多帧微调两阶段范式，在保持计算效率的同时有效融合多帧历史，显著提升了机器人操作的鲁棒性和效率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38903/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 879, \"height\": 591, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38903/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1803, \"height\": 598, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38903/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 836, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38903/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1836, \"height\": 927, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38903/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 841, \"height\": 513, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38903/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 704, \"height\": 431, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38903/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1636, \"height\": 706, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38903/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 876, \"height\": 687, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38903/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 869, \"height\": 242, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38903/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 780, \"height\": 300, \"label\": \"Table\"}]"
motivation: 单帧VLA模型无法充分利用多帧时序信息，直接输入多帧会导致计算开销和延迟。
method: 提出CronusVLA两阶段框架：先在大型具身数据集上单帧预训练，再在多帧数据上微调。
result: 在多个操作基准上，CronusVLA在效率和鲁棒性上优于单帧基线。
conclusion: 多帧VLA建模是提升机器人操作性能的有效途径。
---

## Abstract
Recent vision-language-action (VLA) models built on pretrained vision-language models (VLMs) have demonstrated strong performance in robotic manipulation. However, these models remain constrained by the single-frame image paradigm and fail to fully leverage the temporal information offered by multi-frame histories, as directly feeding multiple frames into VLM backbones incurs substantial computational overhead and inference latency. We propose CronusVLA, a unified framework that extends single-frame VLA models to the multi-frame paradigm. CronusVLA follows a two-stage process: (1) Single-frame pretraining on large-scale embodied datasets with autoregressive prediction of action tokens, establishing an effective embodied vision-language foundation; (2) Multi-frame post-training, which adapts the prediction of the vision-language backbone from discrete tokens to learnable features, and aggregates historical information via feature chunking. CronusVLA effectively addresses the existing challenges of multi-frame modeling while enhancing performance. To evaluate the robustness under temporal and spatial disturbances, we introduce SimplerEnv-OR, a novel benchmark featuring 24 types of observational disturbances and 120 severity levels. Experiments across three embodiments in simulated and real-world environments demonstrate that CronusVLA achieves leading performance and superior robustness, with a 70.9% success rate on SimplerEnv, a 26.8% improvement over OpenVLA on LIBERO, and the highest robustness score on SimplerEnv-OR, showing the promise of efficient multi-frame adaptation for real-world VLA deployment.

---

## 论文详细总结（自动生成）

### 1. 论文的核心问题与整体含义

- **研究背景**：现有的视觉-语言-动作（VLA）模型大多建立在预训练的视觉-语言模型（VLM）之上，在机器人操作任务中取得了良好性能。但这些模型受限于**单帧图像范式**，只使用当前观测，未能充分利用多帧历史观测中的时序信息。
- **问题提出**：直接将多帧图像送入VLM骨干会导致自注意力计算量随帧数平方级增长，带来巨大的计算开销和推理延迟，难以高效扩展到多帧场景。
- **整体目标**：提出一个统一框架 **CronusVLA**，将单帧VLA模型高效扩展到多帧范式，在保持推理速度的同时提升操作性能和鲁棒性。

### 2. 论文提出的方法论

- **核心思想**：两阶段训练策略——先进行单帧预训练，再进行多帧后训练；通过引入可学习特征和特征分块（feature chunking）实现高效的多帧信息聚合，避免冗余计算。
- **关键技术细节**：
  - **单帧预训练**：基于现有VLM（如Llama 2或Qwen2.5），在大规模异构操作数据集（OXE）上，以自回归方式预测离散动作token（256 bins），建立具身视觉-语言基础。
  - **多帧后训练**：
    - 将离散动作token替换为**可学习特征** \(f_t\)，由视觉-语言骨干提取当前帧和语言指令的连续表示。
    - 引入**特征分块** \(F^M_t = \{f_{t-M+1}, ..., f_t\}\)，通过队列机制缓存历史特征，推理时无需重复计算。
    - 设计**跨帧解码器**（DiT-based），包含特征调制器（feature modulator）和交叉注意力网络，对特征分块解码，输出动作块（action chunking），使用扩散损失训练。
    - 采用**多帧正则化**：对历史帧特征使用stop-gradient，使其仅作为辅助输入（不更新骨干），保持单帧感知能力并加速收敛。
- **SimplerEnv-OR 鲁棒性基准**：引入24种观测扰动（空间：全局、局部、离散；时间：恒定、循环、稀疏）及120个严重级别，使用鲁棒性分数（R-Score = 100 * SR_i / SR）定量评估。

### 3. 实验设计

- **使用的数据集与场景**：
  - 预训练：OXE（Open X-Embodiment）数据集。
  - 后训练：Bridge-v2 和 Fractal 数据集（约148k episodes, 5M多帧片段）。
  - 评估基准：
    - **SimplerEnv**：WidowX机器人（WR）和Google机器人（GR）设置，共12个任务。
    - **LIBERO**：4个任务套件（Spatial, Object, Goal, Long）。
    - **SimplerEnv-OR**：新增观测扰动基准，含24种扰动类型，2300次试验。
    - **真实世界**：Franka Research 3平台，三类任务（简单操作、长序列、泛化与鲁棒性），每任务25次试验。
- **对比方法**（18种以上）：RT-1-X, RT-2-X, Octo-Base, OpenVLA, CogACT, TraceVLA, SpatialVLA, π0, π0-FAST, GR00T-N1.5, RoboVLMs, Magma, Dita, OpenVLA-OFT, π0.5 + KI等，涵盖不同规模（0.5B–8B）和单/多帧方法。
- **消融实验**：
  - 后训练策略消融（基线→+多帧→+解码器→+骨干训练→+正则化）。
  - 跨帧解码器设计消融（有无交叉注意力、有无调制器、MLP vs SiT vs DiT）。
  - 帧数影响分析（1–10帧对性能和速度的影响）。

### 4. 资源与算力

- **文中未明确说明**具体的GPU型号、数量、训练时长等信息。仅在致谢中提到使用了GPU集群（由MCC Lab and 中国科学院机器人AI科学家平台支持），未量化算力消耗。

### 5. 实验数量与充分性

- **实验数量**：总实验涵盖**三大模拟基准**（SimplerEnv 12任务 × 2设置、LIBERO 4套件、SimplerEnv-OR 24扰动类型×多频率）、**真实世界**（3类任务共多个子任务），以及**多组消融实验**（后训练策略、解码器结构、帧数）。各实验均报告了多次试验的平均成功率（如200–400次试验）。
- **充分性与客观性**：
  - 对比方法全面，包括代表性单帧和多帧VLA。
  - 采用统一的检查点进行公平对比（部分方法使用相同训练数据集）。
  - 消融实验系统，验证每个组件贡献。
  - 此外，**SimplerEnv-OR** 专门用于评估鲁棒性，弥补了现有基准的空白。
- **结论**：实验充分且设计合理，结果清晰证明了CronusVLA的优势。

### 6. 论文的主要结论与发现

- CronusVLA在**SimplerEnv**上达到平均70.9%成功率（7B模型），大幅领先现有方法（如CogACT 63.8%, TraceVLA 41.1%）。
- 在**LIBERO**上平均97.0%成功率，尤其在长序列任务达到94.0%（比OpenVLA提升40.3%）。
- 在**SimplerEnv-OR**上，多帧建模带来强鲁棒性：在时间扰动（稀疏）下R-Score为96.2，空间扰动下86.9，优于所有对比方法。
- **推理速度**：通过特征缓存避免自回归解码，速度达8.73 Hz，而直接输入多帧的方案仅3.09 Hz。
- **帧数影响**：存在最优帧数（7B模型7帧，0.5B模型4帧），过多帧反而导致性能下降。
- **多帧正则化**有效保持单帧感知并加速收敛。

### 7. 优点

- **方法设计**：
  - 两阶段训练平衡了预训练效率与多帧建模能力，无需从头训练多帧模型。
  - 特征分块 + 队列机制实现高效推理，避免重复计算。
  - 跨帧解码器（调制器+交叉注意力）有效聚合时序信息。
- **实验评估**：
  - 覆盖模拟和真实世界多种机器人平台（WidowX, Google Robot, Franka），任务多样。
  - 提出新的鲁棒性基准SimplerEnv-OR，补全现有评估不足。
  - 对比方法多且新，消融实验全面。
- **性能**：在多个主流基准上取得当时最佳或领先结果，且在小模型（0.5B）上也表现优异。

### 8. 不足与局限

- **计算开销不透明**：未报告训练所需算力（GPU型号、数量、时间），难以复现或比较成本。
- **帧数敏感**：最佳帧数因模型规模而异（4–7帧），缺乏自适应机制，需要手动调优。
- **后训练数据局限**：仅使用Bridge-v2和Fractal两个高质量数据集，泛化性可能受数据分布限制。
- **真实世界评估规模**：仅在一个平台（Franka）上进行有限任务（25次试次/任务），统计显著性可能不足；未见跨机器人迁移或长期部署测试。
- **鲁棒性基准局限**：SimplerEnv-OR仅针对单视角扰动，未考虑视角变化、光照剧烈变化等更复杂场景。
- **局限性讨论缺失**：论文未明确讨论失败案例或方法潜在不足，如对历史帧质量的依赖、长时延场景下的适应性等。
- **与其他多帧方法对比**：虽然对比了RoboVLMs、TraceVLA等，但缺少与更多近期多帧方法的横向对比（可能因论文发表时间较早）。

（完）
