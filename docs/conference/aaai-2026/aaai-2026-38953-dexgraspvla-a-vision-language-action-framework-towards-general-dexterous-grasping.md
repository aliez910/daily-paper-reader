---
title: "DexGraspVLA: A Vision-Language-Action Framework Towards General Dexterous Grasping"
title_zh: DexGraspVLA：面向通用灵巧抓取的视觉-语言-动作框架
authors: "Yifan Zhong, Xuchuan Huang, Ruochong Li, Ceyao Zhang, Zhang Chen, Tianrui Guan, Fanlian Zeng, Ka Nam Lui, Yuyao Ye, Yitao Liang, Yaodong Yang, Yuanpei Chen"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38953/42915"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向通用灵巧抓取的VLA框架
tldr: 现有灵巧抓取研究局限于单目标等受限假设。本文提出DexGraspVLA层次化框架，以预训练视觉语言模型为高层规划器，扩散模型为底层动作控制器，通过迭代变换输入为域不变表示实现泛化。实验证明在多样化场景下抓取成功率显著优于现有方法，为通用灵巧抓取提供了新范式。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38953/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 784, \"height\": 779, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38953/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1364, \"height\": 1028, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38953/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 700, \"height\": 533, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38953/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 849, \"height\": 598, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38953/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 843, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38953/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 481, \"height\": 256, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38953/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 569, \"height\": 255, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38953/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 915, \"height\": 369, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38953/table-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 605, \"height\": 258, \"label\": \"Table\"}]"
motivation: 解决现有灵巧抓取方法泛化能力受限的问题。
method: 提出层次化VLA框架，结合视觉语言模型和扩散动作控制器。
result: 在多样化场景中实现高成功率抓取。
conclusion: 提出了一种面向通用灵巧抓取的VLA框架，具强泛化性。
---

## Abstract
Dexterous grasping remains a fundamental yet challenging problem in robotics. A general-purpose robot must be capable of grasping diverse objects in arbitrary scenarios. However, existing research typically relies on restrictive assumptions, such as single-object settings or limited environments, showing constrained generalization. We present DexGraspVLA, a hierarchical framework for robust generalization in language-guided general dexterous grasping and beyond. It utilizes a pre-trained Vision-Language model as the high-level planner and learns a diffusion-based low-level Action controller. The key insight to achieve generalization lies in iteratively transforming diverse language and visual inputs into domain-invariant representations via foundation models, where imitation learning can be effectively applied due to the alleviation of domain shift. Notably, our method achieves a 90+% dexterous grasping success rate under thousands of challenging unseen cluttered scenes. Empirical analysis confirms the consistency of internal model behavior across environmental variations, validating our design. DexGraspVLA also, for the first time, simultaneously demonstrates free-form long-horizon prompt execution, robustness to adversarial objects and human disturbance, and failure recovery. Extended application to nonprehensile grasping further proves its generality.

---

## 论文详细总结（自动生成）

# DexGraspVLA：面向通用灵巧抓取的视觉-语言-动作框架 — 详细总结

## 1. 核心问题与整体含义（研究动机和背景）

- **现有局限**：灵巧抓取是机器人操作的基础，但已有研究通常依赖强假设（如单目标场景、受控环境），导致泛化能力严重受限。真实应用要求机器人能够在多样化对象、任意背景、光照变化乃至干扰下可靠工作。
- **核心挑战**：如何利用有限的人类演示数据，让灵巧抓取策略泛化到大量未见场景，同时保持闭环控制的鲁棒性。
- **论文目标**：提出 DexGraspVLA，一种层次化 VLA 框架，通过结合基础模型的世界知识与模仿学习的动作建模能力，实现语言引导下的通用灵巧抓取，并在大范围零样本场景中验证其泛化。

## 2. 方法论：核心思想与关键技术细节

- **核心思想**：利用预训练的基础模型（视觉-语言模型、视觉编码器、分割模型）将多样的语言和视觉输入**迭代转化为域不变表示**，从而消除域偏移对模仿学习的影响。在此类稳定的表示上应用模仿学习，即可在训练域之外保持高效动作生成。
- **整体架构**（层次化框架）：
  1. **高层规划器**（VLM, Qwen-VL-Chat / Qwen2.5-VL-72B-Instruct）：将用户指令（如“清理桌子”）分解为子步骤（如“抓住饼干”），并为每个步骤生成目标对象的**边界框**。规划器持续监控任务进度，直至所有指令完成。
  2. **低层控制器**（扩散策略 + 视觉基础模型）：
     - 使用 SAM 根据边界框生成初始对象掩膜，并用 Cutie 进行连续跟踪，得到每帧掩膜 \( m_t \)。
     - 采用 **DINOv2** 作为冻结特征提取器，从头部相机和腕部相机图像中提取视觉特征 \( z_h, z_w \)，这些特征在不同环境（背景、光照）下保持高度一致（域不变）。
     - 融合掩膜特征、视觉特征和机器人本体感知（关节角度），得到观测特征序列 \( \tilde{z}_{\text{obs}} \)。
     - 以**扩散 Transformer（DiT）** 为动作头，预测长度为 \( H \) 的动作块。训练时添加噪声并最小化噪声预测误差；推理时迭代去噪得到动作序列，并采用滚动时域控制（仅执行前 \( H_a \) 步）以提高实时性。
- **关键优势**：整个过程中，原始的语言指令和观测图像被连续转化为边界框、掩膜、DINOv2 特征等域不变信号，极大地缓解了模仿学习对新场景的过拟合问题。

## 3. 实验设计

- **数据集**：
  - 人工收集 **2,094 条成功演示**，使用 **36 个日常物体**（不同大小、重量、几何、纹理、材料），在杂乱桌面场景下随机放置，每次抓取约 3.5 秒。
  - 单独收集 **1,029 条非抓持式抓取演示**（推动 + 抓取）用于扩展实验。
- **测试场景**（全部为“零样本”环境，与训练环境不同）：
  - **大规模泛化**：360 个未见物体 × 单场景；103 个物体 × 6 个未见背景；103 个物体 × 3 种未见光照 → 总共 **1,287 个未见场景**。
  - **基准比较**：24 个未见物体 + 2 种背景 + 2 种光照 + 12 个已见物体（小规模）。
  - **单目标消融**：13 个已见 + 8 个未见物体，每个 5 个位置 × 2 次 → 210 测试。
  - **长时任务**：4 种提示（“清理桌子”“抓住所有瓶子”“所有绿色物体”“所有食物”），每种 24 个随机杂乱场景。
  - **非抓持式抓取**：18 个未见物体，含背景与光照变化共 144 测试。
- **对比方法**：OpenVLA (LoRA/Full FT)、π0 (LoRA/Full FT)、RDT (Full FT)、OpenVLA-OFT (LoRA)，以及两个消融变体（DINOv2-train：可训练 DINOv2；ViT-small：可训练小 ViT，相当于增强版扩散策略）。
- **评价指标**：抓取成功率（物体被提起 10 cm 并保持 20 s）。长时任务还报告子步骤成功率。

## 4. 资源与算力

- **文中未明确说明训练使用的 GPU 型号、数量及训练时长**。仅提及在消融实验中对比了可训练编码器的情况，但未给出具体计算资源开销。因此无法评估实际算力需求。

## 5. 实验数量与充分性

- **实验数量丰富**：覆盖大规模泛化（>1200 测试）、基准对比（4 种 VLA 模型 + 2 种消融）、单目标细节消融、长时任务（4 类提示，每类 24 场景）、非抓持式扩展（144 测试）以及内部行为可视化分析，总计数千次实际机器人测试。
- **充分性评估**：
  - **优点**：测试环境完全真实，零样本设置严格；干扰、恢复、对抗性物体等鲁棒性实验增强了说服力；消融层层递进（编码器可训练性、模型大小），验证了域不变表示的关键作用。
  - **潜在不足**：基准比较仅在较小数据集上进行（24 未见物体 + 2 背景/光照），而非全量 1287 场景，可能略微偏向提出的方法；未与已有的基于强化学习的灵巧抓取方法（如 UniDexGrasp++）进行对比，限制了对端到端强化学习泛化能力的评估；所有实验均在相同硬件平台完成，未跨平台验证。

## 6. 主要结论与发现

- DexGraspVLA 在 **1287 个未见杂乱场景中达到 90.8% 的抓取成功率**（单次尝试，Ours@1），允许最多 3 次尝试时提升至 96.9%，显著优于所有对比 VLA 基线（最高 31.1%）和消融变体（最高 50.5% 在单目标）。
- **内部行为一致性验证**：通过可视化 DINOv2 特征、掩膜和 DiT 注意力，证明即便在视觉变化极大的环境下，模型仍聚焦于同一目标物体，证实了域不变表示的鲁棒性。
- 首次同时实现了**自由形式长时提示执行**（89.6% 任务成功率）、**对抗干扰恢复**和**扩展至非抓持式操作**（84.7%），展现了架构的通用性。

## 7. 优点

- **方法创新**：巧妙利用“域不变表示”桥梁，将基础模型与模仿学习互补结合，而非简单端到端微调；层次化设计使规划与执行解耦，便于扩展。
- **实验设计全面**：大规模真实世界零样本验证，含光照、背景、物体多样性；内部行为可视化有力支撑设计直觉。
- **鲁棒性强**：闭环控制+跟踪+扩散多峰策略，使系统能处理动态干扰、再抓持和失败恢复，远超现有开放环方法。
- **通用性好**：仅改变训练数据即可无缝迁移到非抓持任务，表明框架可适应不同灵巧操作技能。

## 8. 不足与局限

- **任务范围受限**：只涉及抓取，未覆盖功能性操作（如工具使用）或长链操作；未集成触觉感知，依赖纯视觉。
- **消融对比范围**：虽然消融了编码器可训练性，但未系统地测试不同基础模型（如更轻量的 DINOv1、CLIP）的影响；基准对比规模较小。
- **资源透明度低**：未报告训练算力，难以评估方法可复现性。
- **无跨平台验证**：所有实验仅在单一机械臂+手部组合上完成，在不同硬件配置下的泛化性未验证。
- **演示需求**：虽然演示数相对少（2k+），但人工采集仍耗时；对于全新技能（如非抓持）还需额外演示集，限制了极端快速部署。

（完）
