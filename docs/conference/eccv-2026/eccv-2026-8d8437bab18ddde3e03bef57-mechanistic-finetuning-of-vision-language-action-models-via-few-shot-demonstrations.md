---
title: Mechanistic Finetuning of Vision-Language-Action Models via Few-Shot Demonstrations
title_zh: 通过少样本演示对视觉-语言-动作模型进行机理化微调
authors: "Chancharik Mitra, Yusen Luo, Raj Saravanan, Dantong Niu, Anirudh Pai, Jesse Thomason, Trevor Darrell, Abrar Anwar, Deva Ramanan, Roei Herzig"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/13378.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过少样本演示微调视觉-语言-动作模型以适配机器人任务
tldr: 针对视觉-语言-动作模型在机器人上需要微调以适配不同具身和任务的问题，本文提出基于功能特异性启发的少样本微调方法Robotic Steering。该方法只更新任务相关的稀疏表征，有效缓解过拟合并保留预训练通用性。实验显示在多个机器人任务上取得更好效果。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8d8437bab18ddde3e03bef57/fig-001.webp\", \"caption\": \"\", \"page\": 3, \"index\": 1, \"width\": 1559, \"height\": 735}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8d8437bab18ddde3e03bef57/fig-002.webp\", \"caption\": \"\", \"page\": 4, \"index\": 2, \"width\": 1559, \"height\": 1043}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-8d8437bab18ddde3e03bef57/fig-003.webp\", \"caption\": \"\", \"page\": 14, \"index\": 3, \"width\": 800, \"height\": 439}]"
motivation: VLA模型在机器人上需要微调以适应不同具身和任务，但现有方法存在过拟合问题。
method: 提出Robotic Steering，仅微调任务特定的稀疏表征以保留预训练通用性。
result: 在少样本机器人任务微调中表现优于全参数微调，缓解了过拟合。
conclusion: 机理化的稀疏微调为通用VLA模型适配机器人任务提供了有效路径。
---

## Abstract
Vision-Language Action (VLAs) models promise to extendthe remarkable success of vision-language models (VLMs) to robotics. Yet,unlike VLMs in the vision-language domain, VLAs for robotics requirefinetuning to contend with varying physical factors like robot embodiment,environment characteristics, and spatial relationships of each task. Wepropose leveraging few-shot demonstrations of tasks to better capture thisphysical variability. Overfitting to the trained task is yet another problemof existing methods. Inspired by functional specificity, we hypothesizethat finetuning only task-specific sparse model representations is bothmore effective and better retains pretrained model generality. In thiswork, we introduce Robotic Steering, a finetuning approach groundedin mechanistic interpretability that leverages few-shot demonstrations toidentify and selectively finetune task-specific attention heads aligned withthe physical, visual, and linguistic requirements of robotic tasks. Throughcomprehensive on-robot evaluations with a Franka Emika robot arm, wedemonstrate that Robotic Steering outperforms LoRA while achievingsuperior robustness under task variation, reduced computational cost,and enhanced interpretability for adapting VLAs to diverse robotic tasks.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper, organized according to the specified outline. Let me carefully analyze the paper content and structure my response accordingly.

The paper is about "Robotic Steering" - a mechanistic interpretability-based finetuning approach for Vision-Language-Action (VLA) models. Let me extract the key information:

1. Core problem: VLAs require finetuning for each deployment, and existing methods like LoRA overfit to narrow training distribution.

2. Method: 
- Three-step approach
- Step 1: Use k-NN regression on few-shot demonstrations to identify task-relevant attention heads
- Step 2: Selective LoRA finetuning on query and output projections of selected heads
- Step 3: Standard inference

3. Experiments:
- 5 real-robot tasks with Franka Emika Panda arm
- π0 and π0.5 VLAs
- Compared with full-head LoRA, zero-shot baselines
- LIBERO-Plus simulation benchmark
- Ablation studies on head selection methods, training components, scaling

4. Resources:
- 2 NVIDIA RTX A6000 GPUs
- 5000 training steps
- JAX implementation
- Training time: 189 min (π0 RS) vs 239 min (π0 LoRA), 185 min (π0.5 RS) vs 214 min (π0.5 LoRA)

5. Experiment count:
- 5 primary real-robot tasks
- 40 trials per task evaluation
- Multiple ablations: head selection methods (CMA, REINFORCE, KNN), training components
- Scaling experiments (demonstrations, training iterations)
- Generalization tests (unseen tasks, multi-task)
- Robustness tests (lighting, form, distractor)
- LIBERO-Plus simulation (Long suite, 10 tasks)

6. Conclusions:
- Robotic Steering matches or outperforms LoRA
- 96% fewer trainable parameters
- 21% less training time
- Better robustness to environmental variations
- Better generalization to unseen tasks

7. Highlights:
- First mechanistic interpretability approach for VLA finetuning
- Novel use of few-shot demonstrations to specify physical tasks
- Computational efficiency
- Standard checkpoint deployment (no inference overhead)
- Interpretability through attention head visualization

8. Limitations:
- Requires open-source model weights
- Single robot embodiment tested
- Only LLM attention heads analyzed, not other components

Let me write the structured Chinese summary.</think>

# 论文总结：Mechanistic Finetuning of Vision-Language-Action Models via Few-Shot Demonstrations

## 1. 核心问题与研究动机

- **研究背景**：视觉-语言-动作（VLA）模型将视觉-语言模型的成功扩展到机器人控制领域，但与 VLM 不同，VLA 在实际部署时必须针对每个具体环境（具身差异、光照、相机角度、目标位置等）进行任务级微调。
- **关键问题**：
  - 现有微调方法（如 LoRA）对所有参数做"一刀切"式适配，容易在窄训练分布上过拟合，破坏预训练获得的通用能力。
  - 机器人任务的"边界"是连续的物理变化空间（几厘米偏差、光照差异即可改变所需行为），仅靠语言描述无法完整刻画任务。
- **核心假设**：受神经科学"功能特异性"与 Transformer 机理可解释性研究的启发，作者认为 VLA 中存在与任务相关的"特定注意力头"，只微调这些稀疏组件既能提高效率，又能保留预训练的通用能力。

## 2. 方法论：Robotic Steering

整体流程分为三步：

### 步骤 1：识别任务相关注意力头（k-NN 回归打分）
- 输入：少量（20 条）专家演示轨迹 $\mathcal{D}=\{(\tau_i, a_i)\}$，每条轨迹包含 $T$ 个时间步的视觉、语言、状态 token。
- 对每个注意力头 $(l,h)$，提取最后 token 位置的激活向量 $h_{l,h}(\tau_i^t)$。
- 对每个查询观测 $q$，在该 head 的表示空间中按余弦相似度检索 k 个最近邻时间步，并用距离加权平均预测对应动作 $\hat{a}_{l,h}^t$。
- 评分函数：对所有 head 计算预测动作与真值动作的 MSE，$\text{score}_k(l,h)$ 越低表示该 head 编码任务相关信息越充分。
- 在 $k\in\{10,20,30,40\}$ 的小网格上选最优 $k$，取 MSE 最小的 top-m 个 head（文中 $m=20$）作为任务头集合 $\mathcal{H}_{\text{task}}$。

### 步骤 2：选择性 LoRA 微调
- 仅在 $\mathcal{H}_{\text{task}}$ 内对 Query 投影和 Output 投影应用 LoRA（rank = 8）：
  $$W'^{l,h}_Q = W^{l,h}_Q + B^{l,h}_Q A^{l,h}_Q,\quad W'^{l,h}_O = W^{l,h}_O + B^{l,h}_O A^{l,h}_O,\quad (l,h)\in\mathcal{H}_{\text{task}}$$
- 由于 $\pi_{0.5}$ 的 Gemma 主干使用多查询注意力（Multi-Query Attention），Key/Value 在一层内被所有 head 共享，因此不针对 head 做 KV 适配。
- 视觉编码器、动作专家（action expert）、LLM 主干的其他参数全部冻结；FFN 上的 LoRA 与流匹配（flow matching）动作头保持与 LoRA 基线一致的训练设置，使对比"仅差在 head 选择上"。
- 训练目标沿用基模型本身的损失（如 $\pi_{0.5}$ 的 flow matching loss）。

### 步骤 3：标准推理部署
- 微调后得到的是普通 checkpoint，无需在推理时进行激活干预或额外计算，可直接用于标准 VLA 推理流水线。

## 3. 实验设计

### 真实机器人实验（核心）
- **机器人平台**：7-DoF Franka Emika Panda + Robotiq 夹爪 + Polymetis 低层控制器；启用左臂相机和腕部相机，6 Hz 记录；与 DROID 数据集设置一致。
- **5 个任务**（每任务 20 条遥操演示，每评估项 40 次试验）：
  1. place marker in mug
  2. press red button hard
  3. pick up red cube
  4. place green cube in red bowl
  5. push red cup to red bowl
- **基线方法**：
  - 零样本：$\pi_0$-DROID、$\pi_{0.5}$-DROID
  - 微调方法：$\pi_0$/$\pi_{0.5}$ 全头 LoRA（Full-head LoRA，rank=8，5000 步）
- **基座模型**：PaliGemma 主干，18 层 × 8 head；选 top-20 head。

### 仿真实验
- **Benchmark**：LIBERO-Plus（Long suite），相比标准 LIBERO 在测试时引入物体布局与光照扰动。
- **设置**：仅用 Task 0 的 20 条演示对 $\pi_0$ 进行微调；评估 (a) 训练任务在扰动下的鲁棒性 (b) 跨 9 个未见任务的迁移能力。

### 额外实验维度
- **泛化**：单任务训练 → 未见任务 Pick Mug；多任务训练（Place Marker + Place Cube）。
- **鲁棒性**：光照变化、物体形态变化、引入干扰物。
- **可视化**：任务相关 head 的注意力图可视化（说明不同任务激活不同的 head 集合）。

## 4. 资源与算力

- **GPU**：2 张 NVIDIA RTX A6000。
- **框架**：JAX（文中特别指出为 JAX 模型开发激活提取功能是一项技术贡献，因为 JAX 缺少便捷的 hook）。
- **训练时长**（5,000 步、20 条演示）：
  - $\pi_0$ + LoRA：239 min
  - $\pi_0$ + Robotic Steering：189 min（**节省约 21%**）
  - $\pi_{0.5}$ + LoRA：214 min
  - $\pi_{0.5}$ + Robotic Steering：185 min
- **可训练参数**：Full-head LoRA ≈ 29M；Robotic Steering ≈ 15.8M（**减少约 45%**）。
- **head 选择时间**：K-NN ≈ 0.2 min；CMA ≈ 58 min；REINFORCE ≈ 93 min。
- **激活缓存**：约 92.83M。

## 5. 实验数量与充分性

- **真实机器人实验**：5 个任务 × 2 个基座模型 × 2 种微调方法 × 40 次评估 = 800 次真实试验，足以获得统计性结论。
- **消融实验**：
  - head 选择方法对比（K-NN / CMA / REINFORCE）
  - 训练组件对比（仅 Query vs. Query+MLP/FFN LoRA）
  - 演示数量缩放（1 / 5 / 10 / 20 / 40）
  - 训练迭代次数缩放（1000–5000）
- **泛化与鲁棒性**：单任务、多任务、非重叠 vs. 联合 head 选择策略；光照、形态、干扰物三种扰动。
- **仿真**：LIBERO-Plus 上 10 个任务。
- **充分性评估**：实验覆盖了性能、效率、可扩展性、泛化、鲁棒性、可解释性多个维度，任务、模型、扰动类型都比较充分。但**所有对比方法仅在单一 Franka 臂上进行**，且只在 5 个任务上做实机测试，跨平台、跨任务的覆盖仍有局限。

## 6. 主要结论与发现

- **性能**：在 5 个真实任务上，Robotic Steering 在两个 VLA（$\pi_0$、$\pi_{0.5}$）上均匹配或优于全头 LoRA（如 Place Cube in Bowl：$\pi_0$ 上 85% vs 60%，$\pi_{0.5}$ 上 80% vs 65%）。
- **效率**：可训练参数约减少 45%（29M → 15.8M）；训练时间缩短约 21%；head 选择几乎无开销（0.2 min vs 58–93 min）。
- **泛化**：在未见任务 Pick Mug 上，Robotic Steering 显著优于 LoRA（65% vs 42.5%）。
- **鲁棒性**：在光照、形态、干扰物三种扰动下，Robotic Steering 的性能下降幅度显著小于 LoRA。
- **仿真**：LIBERO-Plus 上 Robotic Steering 在物体布局和光照两种扰动下都更接近零样本性能，而 LoRA 明显"灾难性遗忘"。
- **可解释性**：可视化证实不同任务确实激活不同的 head 子集，呼应"功能特异性"假设。

## 7. 优点

- **首次将机理可解释性引入 VLA 微调**：基于 head 级别的功能特异性做出有原则的稀疏化设计。
- **设计对照公平**：所有非 head 训练组件（FFN LoRA、动作头、损失、数据）与 LoRA 基线一致，差异仅来源于 head 选择 → 任何性能差异都直接归因于"选什么"而非"怎么训"。
- **效率显著**：参数与训练时间双下降，且 head 选择步骤本身也是最便宜的方案。
- **可解释性强**：可通过 head 选择结果与注意力可视化直接解读模型行为。
- **零推理开销**：产出标准 checkpoint，能即插即用部署到现有 VLA 流水线。
- **少样本友好**：仅 20 条演示即可取得优于 LoRA 的效果，契合真实机器人迭代场景。
- **全面的多维评估**：包含性能、效率、泛化、鲁棒性、可解释性、消融、仿真、缩放实验。

## 8. 不足与局限

- **依赖开源权重**：需要访问模型内部激活，无法直接应用于闭源 VLA。
- **单一硬件验证**：仅在 Franka Emika Panda 上做实机测试；其他具身（移动臂、灵巧手、轮式机器人等）的迁移性未验证。
- **特征提取局限于 LLM 注意力头**：视觉编码器、动作专家、视觉-语言投影层中可能也存在任务相关特征，但本工作未触及。
- **head 集合规模受限**：固定选 top-20，缺乏对 $m$ 大小的更细粒度灵敏度分析（仅在附录简要消融）。
- **多任务 head 选择策略简单**：仅探索了"非重叠"和"联合"两种策略，未考虑层级化或专家混合式机制。
- **伦理风险**：作者自指出，对模型行为进行"外科手术式"修改可能在缺乏充分审计时被滥用，但同时也强调这是机理方法的优势。
- **与零样本能力的权衡未完全量化**：虽然在仿真上展示了"少遗忘"，但在更复杂的真实长时任务中尚未严格验证。

（完）
