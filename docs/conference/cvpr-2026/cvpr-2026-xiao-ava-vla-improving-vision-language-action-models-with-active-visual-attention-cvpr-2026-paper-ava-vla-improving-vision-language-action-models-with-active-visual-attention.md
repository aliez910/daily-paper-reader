---
title: "AVA-VLA: Improving Vision-Language-Action models with Active Visual Attention"
title_zh: AVA-VLA：通过主动视觉注意力改进视觉-语言-动作模型
authors: "Xiao, Lei, Li, Jifeng, Gao, Juntao, Ye, Feiyang, Jin, Yan, Qian, Jingjing, Zhang, Jing, Wu, Yong, Yu, Xiaoyuan"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Xiao_AVA-VLA_Improving_Vision-Language-Action_models_with_Active_Visual_Attention_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 将VLA重铸为部分可观测马尔可夫过程，引入循环信念状态以实现闭环视觉反馈
tldr: 本文指出当前视觉-语言-动作模型逐时刻独立处理视觉观测，忽略了机器人控制天然的部分可观测性。为此，作者将VLA策略学习重新建模为部分可观测马尔可夫决策过程，并提出AVA-VLA，通过循环状态近似智能体对任务历史的信念，并引入主动视觉注意力机制。实验表明该框架在具身任务中显著提升了闭环视觉反馈效果与操作性能。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 860, \"height\": 736, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1711, \"height\": 892, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1691, \"height\": 493, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1758, \"height\": 528, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1446, \"height\": 870, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 423, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 849, \"height\": 230, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 837, \"height\": 363, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-xiao-ava-vla-improving-vision-language-action-models-with-active-visual-attention-cvpr-2026-paper/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1763, \"height\": 235, \"label\": \"Table\"}]"
motivation: 现有VLA历史无关的设计无法建模部分可观测环境中的任务历史信息。
method: 提出AVA-VLA，以循环信念状态结合主动视觉注意力实现动作生成。
result: 在具身操作任务中显著提升了闭环反馈质量与策略表现。
conclusion: POMDP视角与循环信念为VLA闭环视觉反馈控制提供了有效途径。
---

## Abstract
Vision-Language-Action (VLA) models have shown remarkable progress in embodied tasks recently, but most methods process visual observations independently at each timestep. This history-agnostic design treats robot manipulation as a Markov Decision Process, even though real-world robotic control is inherently partially observable and requires reasoning over past interactions. To address this mismatch, we reformulate VLA policy learning from a Partially Observable Markov Decision Process perspective and propose AVA-VLA, a framework that conditions action generation on a recurrent state that serves as a neural approximation to the agent's belief over task history. Built on this recurrent state, we introduce Active Visual Attention (AVA), which dynamically reweights visual tokens in the current observation to focus on regions most relevant given both the instruction and execution history. Extensive experiments show that AVA-VLA achieves state-of-the-art performance on standard robotic benchmarks, including LIBERO and CALVIN, and transfers effectively to real-world dual-arm manipulation tasks. These results demonstrate the effectiveness of temporally grounded active visual processing for improving VLA performance in robotic sequential decision-making.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "AVA-VLA: Improving Vision-Language-Action models with Active Visual Attention" following a specific structure. Let me carefully analyze the paper content and organize the summary according to the 8 requested points.

Let me extract the key information:

1. Core problem: Existing VLA models process visual observations independently at each timestep, treating robot manipulation as MDP when it's actually POMDP. This history-agnostic design loses temporal context.

2. Method: 
- Reformulate VLA as POMDP
- Recurrent state r_{t-1} as neural approximation of belief state b_{t-1}
- Active Visual Attention (AVA) module that uses recurrent state to dynamically reweight visual tokens
- AVA uses FiLM to condition visual features on language, then cross-attention between visual queries and recurrent state as key/value
- Soft weights ω_t applied to all LLM layers via attention matrix modulation
- State-based initialization: recurrent state used as action placeholder
- Truncated BPTT with horizon T=4
- L2 regularization on soft weights

3. Experiments:
- LIBERO (Spatial, Object, Goal, Long) - both single-task and multi-task
- CALVIN ABC→D
- Mobile ALOHA real-world (4 tasks)
- Baselines: TraceVLA, WorldVLA, π0, π0-FAST, UnifiedVLA, OpenVLA-OFT, OpenVLA, SpatialVLA, CoT-VLA, NORA, PD-VLA, UniVLA, FLOWER, RIPT-VLA, VLA-Adapter, Seer

4. Resources: Nvidia A800 GPUs mentioned, but no specific count or training time mentioned.

5. Experimental scope:
- LIBERO comparison (Table 1)
- CALVIN comparison (Table 2)
- Real-world comparison (Figure 3)
- Backbone ablation (Table 3)
- Component ablation (Table 4)
- Visual token pruning analysis (Table 5)
- Qualitative visualization (Figure 4)

6. Main conclusions:
- SOTA on LIBERO and CALVIN
- Effective real-world transfer
- POMDP perspective improves VLA

7. Strengths:
- Novel POMDP reformulation
- Effective recurrent state design
- AVA module demonstrates clear visual focus improvements
- Token pruning capability
- Multiple backbone compatibility

8. Limitations:
- No detailed computational cost analysis
- T=4 horizon may miss long-term dependencies
- Limited real-world tasks
- Foundation on OpenVLA-OFT only (though tested on other backbones)
- Only LIBERO+ in appendix
- No detailed training time/cost mentioned

Let me now write this in Chinese with clear markdown structure.</think>

# AVA-VLA 论文总结

## 1. 核心问题与研究动机

- **核心问题**：现有 Vision-Language-Action (VLA) 模型在每个时间步**独立处理视觉观测**，将机器人操作建模为马尔可夫决策过程 (MDP)。但真实机器人控制本质上是**部分可观测**的，需要对过去交互进行推理。
- **关键缺陷**：
  - 视觉帧独立处理，无法捕捉跨时间步的不可观测动态（如遮挡信息、内部状态）。
  - 每个时刻的视觉注意力都由静态语言指令引导，**被迫从零开始重新评估**视觉信息，无法抑制时序冗余或聚焦于历史动作使之重要的区域。
  - 视觉系统呈"被动"而非"主动"，制约了 VLA 在动态序贯决策中的表现。
- **研究意义**：将 VLA 重新置于 POMDP 框架下进行建模，为闭环视觉反馈控制提供理论基础。

## 2. 方法论

### 2.1 POMDP 视角下的重新建模
- 将策略由 $\bar{A}_t \sim P_\theta(A_t|x_t)$（MDP 形式）重构为：
$$\bar{A}_t \sim P_\theta(A_t | x_t, b_{t-1})$$
  其中 $b_{t-1}$ 为理论信念状态。
- 由于真实信念状态不可计算，提出用**循环状态 (Recurrent State) $r_{t-1}$** 作为其神经网络近似。

### 2.2 循环状态的构建
- 取上一时刻最后一层 LLM 解码器输出 $h_{t-1}^M$，通过 MLP $B$ 变换得到：
$$r_{t-1} = B(h_{t-1}^M) \in \mathbb{R}^{L_A \times d}$$
- 同时将 $r_{t-1}$ 作为**动作占位符 (action placeholder) 的初始化** $p_t = r_{t-1}$，以在并行解码中保留时序上下文。

### 2.3 主动视觉注意力 (AVA) 模块
- **步骤 1**：通过模态专属 MLP 将视觉/语言特征映射到低维空间 $d'$，并用 **FiLM** 层以语言指令调制视觉特征 $\hat{z}_t^I = F_\gamma(\bar{z}_t^S) \odot \bar{z}_t^I + F_\beta(\bar{z}_t^S)$。
- **步骤 2**：以视觉 token 为 Query $Q_t = W_Q \hat{z}_t^I$，以循环状态为 Key/Value $K_t, V_t = W_K \hat{r}_{t-1}, W_V \hat{r}_{t-1}$，做 Cross-Attention + Self-Attention。
- **步骤 3**：经过 FFN 与线性层 $W: d' \to 2$ + Softmax 得到每个视觉 token 的增强/抑制权重 $\rho_t \in \mathbb{R}^{L_I \times 2}$，并以可学习标量 $\gamma = (\gamma_0, \gamma_1)$ 组合得到**软权重 $\omega_t$**。
- **步骤 4**：将 $\omega_t$ 嵌入到每一层 LLM 的注意力矩阵中：
$$A_{i,j}^{t,m} = \frac{\exp(C_{i,j}^{t,m}) U_{i,j}^t}{\sum_l \exp(C_{i,l}^{t,m}) U_{i,l}^t}$$
  其中 $U_{i,j}^t$ 对非视觉或对角位置为 1，对视觉 token 为 $\omega_j^t$。

### 2.4 训练与推理
- 采用**截断沿时间反向传播 (Truncated BPTT)**，展开长度 $T=4$，平衡显存与时序建模。
- 损失函数为预测 MAE + 软权重 L2 正则（鼓励权重聚焦于任务相关区域）：
$$L_{total} = \sum_{n=1}^N \sum_{t=0}^{T-1} (L_{t,n} + \lambda L^\omega_{t,n})$$
- 推理时采用完全递归方式，初始 $r_{-1} = \bar{0}$。

## 3. 实验设计

### 3.1 数据集 / 场景
- **LIBERO**：终身机器人学习基准，含 Spatial / Object / Goal / Long 四个子套件，100 个任务、5000 episode。
- **LIBERO+**：LIBERO 的鲁棒性扩展基准，含 7 个扰动维度（附录）。
- **CALVIN (ABC→D)**：长视野语言条件操作基准，34 个任务，跨环境零样本泛化评估。
- **Mobile ALOHA 真实机器人**：4 个桌面双手机器人任务——Pick and Place、Sequenced Instruction (Tower of Hanoi)、Flexible Object Folding (折毛巾)、Dexterous Action (铲小物)，每个任务 30~450 条示教。

### 3.2 对比方法
- **LIBERO**：TraceVLA、WorldVLA、π0、π0-FAST、UnifiedVLA、OpenVLA-OFT、SpatialVLA、CoT-VLA、NORA、PD-VLA、UniVLA、FLOWER、RIPT-VLA。
- **CALVIN**：OpenVLA、UniVLA、UnifiedVLA、OpenVLA-OFT、FLOWER、VLA-Adapter、Seer。
- **真实机器人**：UniVLA、OpenVLA-OFT。

### 3.3 评价指标
- 成功率 (Success Rate, SR)；
- CALVIN 额外使用 Avg. Len（连续完成任务数 0~5）。

## 4. 资源与算力
- 仅明确提到实验在 **Nvidia A800 GPU** 上进行。
- 基础模型为 **OpenVLA-OFT**（LLaMA2-7B 主干 + DINOv2/SigLIP 双分支视觉编码器）。
- **未披露** GPU 数量、训练时长、显存占用等具体算力信息。

## 5. 实验数量与充分性

| 实验类别 | 内容 |
|---|---|
| 主基准对比 | LIBERO（单策略 + 多策略）、CALVIN ABC→D |
| 真实机器人 | Mobile ALOHA 4 任务对比 |
| 消融 | 不同 backbone（OpenVLA-7B / LLaMA2-7B / Qwen2.5-0.5B） |
| 消融 | 状态初始化 vs AVA 模块 vs 两者组合 |
| 分析 | 视觉 token 剪枝（50%~90% 多种比例） |
| 可视化 | 软权重演化、跨视角视觉聚焦对比 |

- **充分性评价**：
  - 覆盖了仿真+真实、4 个 LIBERO 子套件、长视野 CALVIN 和多任务真实机器人，**较为全面**。
  - 同时报告了单任务和多任务两种设定，对比基线多达 13 个以上。
  - 但真实机器人任务仅 4 类、LIBERO+ 仅在附录体现，**鲁棒性评估略显有限**。

## 6. 主要结论与发现
- **LIBERO**：单策略多套件平均 SR 98.0%，单策略单套件平均 98.2%，均在 LIBERO-Long 等最具挑战性子套件上达到 SOTA。
- **CALVIN**：ABC→D 全部 5 个连续任务 SR 均超 89%，平均完成长度 4.65，超过 UnifiedVLA、FLOWER、VLA-Adapter 等强基线。
- **Mobile ALOHA**：四项真实任务平均成功率均高于 UniVLA 与 OpenVLA-OFT。
- **消融发现**：
  - AVA 模块与状态初始化互补，组合效果最佳（98.0% vs 基线 96.8%）。
  - 在未经过机器人数据预训练的 LLaMA2-7B 与 Qwen2.5-0.5B 主干上仍有 +1.4%~+2.6% 提升，**说明框架与主干解耦**。
- **剪枝发现**：AVA 软权重可直接用于 token 剪枝，剪 70% token 后仍保持 97.3% SR，剪 90% 仍优于多个基线。

## 7. 优点与亮点
- **理论贡献清晰**：首次显式地从 POMDP 视角重构 VLA 策略，将循环信念与视觉处理耦合。
- **方法可解释性强**：可视化显示 AVA 注意力权重能稳定锁定机械臂接触点与目标物体，相较 vanilla VLA 显著改善视觉聚焦。
- **通用性**：不依赖特定 backbone，在机器人预训练和未预训练的主干上均有效。
- **附带收益**：天然支持视觉 token 剪枝，提供效率优化路径。
- **实证充分**：仿真+真实均 SOTA，多个消融维度相互印证。

## 8. 不足与局限
- **算力信息不透明**：未公开训练时长、GPU 数量、显存占用，复现成本难以估计。
- **历史长度受限**：截断 BPTT 仅 $T=4$，对真正长视野依赖可能仍不充分；与 MemoryVLA 等带显式记忆库的方法未直接对比。
- **真实任务规模有限**：仅 4 个 Mobile ALOHA 任务，且各任务演示数差异较大（30~450），可能存在评估偏差。
- **鲁棒性评估不充分**：LIBERO+ 等扰动基准结果仅放附录，未与众多近期鲁棒性 VLA 方法直接比较。
- **依赖 OpenVLA-OFT 范式**：AVA 与并行解码/动作 chunk 紧耦合，向 AR 解码或扩散式 VLA（如 CogACT、π0）迁移成本未讨论。
- **超参数依赖**：$\gamma_0, \gamma_1, \lambda, c$ 等超参数需额外调节，目标均值 $c$ 的选择缺乏敏感性分析（仅附录简要提及）。
- **缺少与序列建模 VLM 的横向比较**：与 VLM-3R、Seer 等持续状态模型的差异未深入讨论。

（完）
