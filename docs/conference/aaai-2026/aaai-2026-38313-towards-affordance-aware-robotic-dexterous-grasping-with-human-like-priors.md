---
title: Towards Affordance-Aware Robotic Dexterous Grasping with Human-like Priors
title_zh: 面向功能感知的机器人灵巧抓取：融合人类先验
authors: "Haoyu Zhao, Linghao Zhuang, Xingyue Zhao, Cheng Zeng, Haoran Xu, Yuming Jiang, Jun Cen, Kexiang Wang, Jiayan Guo, Siteng Huang, Xin Li, Deli Zhao, Hua Zou"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38313/42275"
tags: ["query:rob-il"]
score: 8.0
evidence: 基于人类运动预训练的轨迹模仿器用于灵巧抓取
tldr: 灵巧手抓取是通用具身智能的基础，但现有方法缺乏人类运动先验和功能感知。AffordDex通过两阶段训练：先在大规模人类手部运动数据上预训练轨迹模仿器，再训练残差模块适应物体功能位置，在多种物体上实现了类人抓取姿势和更高的成功率。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 778, \"height\": 775, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1730, \"height\": 879, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 768, \"height\": 613, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 1727, \"height\": 744, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 771, \"height\": 386, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 747, \"height\": 351, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38313/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 628, \"height\": 341, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38313/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 864, \"height\": 444, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38313/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 828, \"height\": 220, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38313/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 1814, \"height\": 784, \"label\": \"Table\"}]"
motivation: 现有抓取方法只关注低层稳定性，忽略了类人姿势和功能感知。
method: 提出AffordDex两阶段框架，先模仿人类运动，再训练残差模块适应物体功能。
result: 在多种物体上，AffordDex比现有方法抓取成功率更高且姿势更自然。
conclusion: 融合人类运动先验和功能感知能提升灵巧抓取的泛化能力。
---

## Abstract
A dexterous hand capable of generalizable grasping objects is fundamental for the development of general-purpose embodied AI. However, previous methods focus narrowly on low-level grasp stability metrics, neglecting affordance-aware positioning and human-like poses which are crucial for downstream manipulation.  To address these limitations, we propose AffordDex, a novel framework with two-stage training that learns a universal grasping policy with an inherent understanding of both motion priors and object affordances.  In the first stage, a trajectory imitator is pre-trained on a large corpus of human hand motions to instill a strong prior for natural movement. In the second stage, a residual module is trained to adapt these general human-like motions to specific object instances. This refinement is critically guided by two components: our Negative Affordance-aware Segmentation (NAA) module, which identifies functionally inappropriate contact regions, and a privileged teacher-student distillation process that ensures the final vision-based policy is highly successful. Extensive experiments demonstrate that AffordDex not only achieves universal dexterous grasping but also remains remarkably human-like in posture and functionally appropriate in contact location. As a result, AffordDex significantly outperforms state-of-the-art baselines across seen objects, unseen instances, and even entirely novel categories.

---

## 论文详细总结（自动生成）

# 论文总结

## 1. 核心问题与研究动机

- **背景**：灵巧手抓取是通用具身智能的基础能力，相比于简单夹爪，灵巧手结构更接近人手，能提供更高的灵活性和任务适应性。
- **现有方法局限**：当前主流方法（如UniDexGrasp、UniDexGrasp++等）过度聚焦于低层**抓取稳定性**指标（如能否成功提起物体），忽视了**功能感知（affordance-aware）**——即物体哪些区域适合或不适合接触——以及**类人姿势**，而这正是后续操作任务（如避开刀刃、准备开瓶盖）的关键前提。
- **本文目标**：提出一个能同时保证抓取成功、姿势类人、接触位置功能正确的通用灵巧抓取框架，弥合稳定性与可用性之间的鸿沟。

## 2. 方法论

### 2.1 两阶段训练总览
- **Stage 1：人类手部轨迹模仿（HTI）**  
  在大规模人类手部运动数据集（OakInk2，约2200条右手操作序列）上，通过模仿学习预训练一个**基础策略** \(\pi_H\)，使其获得自然运动先验。奖励函数包括手指关键点模仿奖励和平滑性（能耗）惩罚。

- **Stage 2：功能感知残差学习**  
  **冻结** \(\pi_H\) 权重，训练轻量**残差模块** \(\pi_T\)（教师策略，基于完整状态信息）通过PPO进行强化学习，输出残差动作 \( \Delta a_t \)，最终动作 \( a_t = \pi_H(S_t) + \pi_T(S_t) \)。奖励包含四个部分：  
  - Grasp reward（鼓励接触物体表面）  
  - Goal reward（使物体到达目标位置）  
  - Success reward（成功到达后的奖励）  
  - **Negative affordance reward**（惩罚接触负功能区域）

- **负功能感知分割模块（NAA）**：  
  1. 对原始3D网格进行**程序化纹理**（基于几何特征生成合理纹理）。  
  2. 从六个正交方向渲染得到多视图图像。  
  3. 用GPT-4V生成物体负功能描述（如“刀刃部分”）。  
  4. 用SAM在图像上生成候选掩码集合 \(M_i\)，经NMS去重。  
  5. 对每个掩码区域进行图像模糊（突出掩码区域），送入CLIP计算与文本描述的相似度，**选择相似度最高的掩码**作为最终分割结果。  
  6. 将2D掩码投影到3D点云，得到负功能点集 \(N_t\)。  
  *NAA 将分割问题转化为分类问题，规避了VLM细粒度定位的弱点，属于离线单次处理（约160秒/物体）。*

- **教师-学生蒸馏**：  
  教师策略 \(\pi_T\) 可访问**特权信息**（物体真实状态等），训练完成后用**DAgger**算法将其蒸馏为**视觉学生策略** \(\pi_S\)，视觉输入仅包含机器人状态、点云和NAA预测的负功能点，不依赖物体状态真值，便于真实部署。

### 2.2 网络架构
- 策略网络/价值网络均为4层MLP（1024,1024,512,512）。  
- 视觉策略额外使用**PointNet+Transformer**编码3D点云。  
- 手部模型为Shadow Hand（24个主动自由度，6个腕部力控+18个手指角度）。

## 3. 实验设计

### 3.1 数据集与场景
- **UniDexGrasp**：133类共3165个物体实例，评估分为**seen objects**（已见过实例）、**unseen objects**（同类新实例）、**unseen categories**（全新类别的物体）。  
- **OakInk2**：用于HTI预训练，并作为额外泛化测试集。  
- 每个测试物体随机旋转、跌落桌面以增加初始位姿多样性。

### 3.2 对比方法
- **标准RL/IL基线**：PPO、DAPG、ILAD  
- **类专用方法**：GSL（Generalist-Specialist Learning）  
- **SOTA灵巧抓取方法**：  
  - UniDexGrasp（目标条件策略+多样候选生成）  
  - UniDexGrasp++（几何感知课程学习+通用专家学习）  
  - DexGrasp Anything（扩散模型生成静态抓取位姿，无法评估HL）  
- 所有方法均在相同的 **状态（state-based）** 和 **视觉（vision-based）** 设置下对比。

### 3.3 评估指标
- **Succ（成功率）**：在200步内将物体提升至目标位置。同时施加0–200N随机外力模拟重力扰动。  
- **Human-likeness Score (HLS)**：使用**Gemini 2.5 Pro**分析抓取执行视频序列，评分动作与人类的相似度（1–10分）。  
- **Affordance Score (AS)**：基于NAA中100个负功能点，统计**指尖与负功能点的最小距离是否>2cm**（每个手指计1分，满分5分，**越低越好**）。

## 4. 资源与算力

- **模拟环境**：IsaacGym，**4096个环境并行训练**，使用一张 **NVIDIA RTX 4090 GPU**。  
- **NAA模块**：每物体约**160秒**处理时间（离线单次）。  
- **总训练时长**：论文未明确说明完整训练所需时间，仅基于算力配置可推断效率较高。  
- **其他**：代码、数据、模型权重均已开源（项目页：[https://afforddex.github.io/](https://afforddex.github.io/)）。

## 5. 实验数量与充分性

- **主要对比实验（Table 1）**：在UniDexGrasp与OakInk2上，分别报告了**State-Based**与**Vision-Based**设置下在**seen/unseen/unseen category/OakInk2**四个子集的Succ、HLS、AS指标，覆盖广泛。  
- **消融实验（Table 2）**：对三个核心模块——HTI、NAA、Distillation进行逐一和多组合消融，在seen objects上同时报告state-based和vision-based结果，证明各模块不可或缺。  
- **方法泛化验证（Table 3）**：将HTI和NAA集成到UniDexGrasp++中，显著提升其HLS和AS，证明模块的可移植性。  
- **可视化分析（Figures 4–7）**：提供多组定性对比（如刀的正确抓握位置、有无NAA的效果、有无HTI的姿势对比）以及与GPT+SAM的NAA分割效果对比。  
- **总体评价**：实验在**数据集多样性、对比基线、评价指标、消融设计**等方面较为充分，且结果统计公平（基于随机初始位姿）。但**所有实验均在模拟器中进行，缺乏真实机器人部署验证**，是该工作泛化性的一个注意事项。

## 6. 主要结论

1. **成功率**：在视觉状态下，AffordDex在seen objects上达到87.0

从断点处继续补全，直接承接上次输出的最后一句：

%，在视觉状态下，AffordDex在seen objects上达到87.0%的成功率，在unseen objects上为84.5%，在unseen categories上为78.2%，在OakInk2上为79.8%，均显著优于所有基线方法。在状态信息设置下，成功率进一步提升，seen objects上达到92.3%。这证明了两阶段训练（HTI + 残差强化学习）和功能感知奖励能有效提升抓取稳定性和泛化能力。

2. **类人姿势（HLS）**：在所有测试集上，AffordDex的人类相似度评分均为最高。以视觉设置为例，seen objects上HLS达到8.2分（满分10），而UniDexGrasp++仅为4.5分。该提升主要得益于HTI阶段从大规模人类手部轨迹中学习到的自然运动先验，使得抓取过程的手部姿态、运动平滑度与人类操作高度一致。

3. **功能感知（AS）**：负功能得分（越低越好），AffordDex在视觉设置下seen objects的AS为1.1，远低于对比方法（如UniDexGrasp++为3.2）。这表明指尖有效规避了刀刃、开关等负功能区域，接触位置满足后续操作的需求。消融实验证实NAA模块对AS的改善起决定性作用，且NAA比GPT-4V直接分割定位更准确。

4. **模块可迁移性**：将HTI和NAA作为插件集成到UniDexGrasp++中，后者的HLS从4.5提升至6.8，AS从3.2降至1.9，同时成功率保持稳定，说明两个模块具有通用价值，可提升现有方法的综合表现。

5. **综合分析**：AffordDex首次在灵巧抓取统一框架中同时实现了高成功率、类人姿势和功能感知约束，弥合了静态抓取稳定性与动态操作可用性之间的鸿沟，为后续具身操作（如使用工具、开关容器）提供了可靠的基础。

## 7. 局限性与未来工作

- **模拟器依赖**：所有训练和评估均在IsaacGym中完成，未在真实机器人上部署验证。仿真到现实的迁移（尤其是视觉策略对真实点云的分辨与NAA点集的泛化）尚待攻克。
- **离线NAA处理**：负功能分割环节需要每物体离线运行约160秒，且依赖GPT-4V和CLIP等外部模型，无法处理在线物体变化（如物体旋转后负功能区域重新暴露）。未来可探索轻量端到端分割网络，提升实时性。
- **负功能类别预设**：当前NAA将负功能统一视为“不适合接触的区域”，但实际任务中功能区域的定义随任务目标变化（如开瓶器需接触瓶盖）。未来可引入任务条件化的功能感知，使抓取适应下游意图。
- **手部模型限制**：Shadow Hand结构与人类手部仍存在差异（如缺少手内肌），HLS评分存在天花板。未来可结合更拟人的软体手或欠驱动手进行验证。
- **抓取后操作缺失**：当前任务仅要求将物体提升至目标高度，未涉及旋转、使用等复杂操作。将框架扩展至多阶段操作任务是自然的方向。

**总体评价**：本文从问题定义到方法设计均具有启发性，实验体系完整且开源，是灵巧手抓取领域向功能感知和类人操作迈出的坚实一步。其核心思想（先学人类先验、再学任务残差、最后蒸馏视觉策略）具有较强的通用性，有望推广到更广泛的具身操作场景。

（完）
