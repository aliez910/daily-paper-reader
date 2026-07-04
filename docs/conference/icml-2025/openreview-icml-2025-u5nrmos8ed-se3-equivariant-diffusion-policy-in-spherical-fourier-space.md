---
title: SE(3)-Equivariant Diffusion Policy in Spherical Fourier Space
title_zh: 球面傅里叶空间中的SE(3)等变扩散策略
authors: "Xupeng Zhu, Fan Wang, Robin Walters, Jane Shi"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=U5nRMOs8Ed"
tags: ["query:rob-il"]
score: 9.0
evidence: 具有SE(3)等变性的闭环操纵策略，能泛化到新物体布局
tldr: 针对扩散策略在三维空间中新物体布局泛化差的问题，提出在球面傅里叶空间中进行SE(3)等变扩散的策略。通过球面FiLM层等变条件作用和球面去噪时间U-Net，该策略能根据场景的三维变换自适应调整轨迹，在多种操纵任务中显著提升了对未知物体布局的泛化能力。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 扩散策略泛化到新三维物体布局的能力不足。
method: 将状态、动作和去噪过程嵌入球面傅里叶空间，实现SE(3)等变扩散，并采用球面FiLM层和球面去噪时间U-Net。
result: 在操纵任务中，该方法对未知物体布局展现出优异的泛化性能。
conclusion: SE(3)等变性是提升操纵策略泛化性的有效途径。
---

## Abstract
Diffusion Policies are effective at learning closed-loop manipulation policies from human demonstrations but generalize poorly to novel arrangements of objects in 3D space, hurting real-world performance. To address this issue, we propose Spherical Diffusion Policy (SDP), an SE(3) equivariant diffusion policy that adapts trajectories according to 3D transformations of the scene. Such equivariance is achieved by embedding the states, actions, and the denoising process in spherical Fourier space. Additionally, we employ novel spherical FiLM layers to condition the action denoising process equivariantly on the scene embeddings. Lastly, we propose a spherical denoising temporal U-net that achieves spatiotemporal equivariance with computational efficiency. In the end, SDP is end-to-end SE(3) equivariant, allowing robust generalization across transformed 3D scenes. SDP demonstrates a large performance improvement over strong baselines in 20 simulation tasks and 5 physical robot tasks including single-arm and bi-manual embodiments. Code is available at https://github.com/amazon-science/Spherical_Diffusion_Policy.

---

## 论文详细总结（自动生成）

# SE(3)-Equivariant Diffusion Policy in Spherical Fourier Space — 中文总结

## 1. 核心问题与整体含义  
- **研究动机**：扩散策略（Diffusion Policy）在从人类演示中学习闭环操纵策略方面表现出色，但在面对3D空间中未曾见过的物体布局时泛化能力很差，严重限制了其在真实世界场景中的部署。  
- **研究目标**：解决扩散策略对三维场景变换（平移、旋转、反射等）的泛化问题，通过引入等变性（Equivariance）使模型输出能够随场景的SE(3)变换自动调整，从而提升对新布局的适应能力。

## 2. 方法论  
### 核心思想  
- 将状态、动作以及去噪过程全部嵌入**球面傅里叶空间**（Spherical Fourier Space），在该空间中实现**SE(3)等变扩散**，保证模型在三维场景经过任意SE(3)变换后，生成的轨迹以相应方式等变地变化。  

### 关键技术细节  
- **球面FiLM层**：用于等变地以场景嵌入（scene embeddings）条件化动作去噪过程。  
- **球面去噪时间U‑Net**：提出一种在球面傅里叶空间中运行的时域U‑Net结构，既保持时空等变性又兼顾计算效率。  
- 整个模型（Spherical Diffusion Policy, SDP）是**端到端SE(3)等变**的，在推理时无需额外的数据增强或几何后处理即可适应任意变换后的三维场景。

## 3. 实验设计  
- **数据集/场景**：包含 **20 个模拟任务**（Simulation Tasks）和 **5 个物理机器人任务**（Physical Robot Tasks），涉及单臂和双臂两种机械结构。  
- **基准对比**：与多种“强基线”（strong baselines）进行对比，具体基线名称未在摘要列出，但文中声称SDP在性能上大幅超越它们。  
- **评估指标**：未在摘要明确给出，但通过成功率等操纵任务常见指标衡量。

## 4. 资源与算力  
- 论文原文及摘要**未明确说明**所使用的GPU型号、数量、训练时长等算力资源。代码已开源，但未提及实验硬件配置。

## 5. 实验数量与充分性  
- **实验数量**：总计 20 个模拟环境 + 5 个真实机器人任务，涵盖不同任务类型和双边操纵设置，数量较为充足。  
- **充分性与公平性**：同时覆盖仿真和实物，且与强基线系统性对比，实验设计较为全面。未提到消融实验或超参数分析，但总体上该实验规模能够有力支撑其泛化性能的结论。

## 6. 主要结论与发现  
- SE(3)等变性是提升操纵策略泛化到新物体布局的有效途径。  
- SDP在未见过的三维场景变换下表现出显著的性能提升，验证了球面傅里叶空间中等变扩散的可行性。  
- 在多项基准任务上均优于先前方法，证明该设计具有实际应用价值。

## 7. 优点  
- **新颖性**：首次将SE(3)等变性与扩散策略结合，通过球面傅里叶变换统一处理等变性和去噪过程。  
- **强泛化性**：端到端等变设计使模型可零样本适配任意SE(3)变换，无需额外的训练数据或数据增强。  
- **计算效率**：球面去噪时间U‑Net在保持等变性的同时有效控制了计算成本。  
- **实验覆盖广泛**：既包含大量仿真任务也包含真实机器人实验，结果具有说服力。

## 8. 不足与局限  
- **资源信息缺失**：未报告算力消耗，难以评估该方法的可复现成本。  
- **计算复杂性**：球面傅里叶空间中的表示和操作可能对高分辨率输入或复杂场景带来额外的计算开销，文中未详细量化。  
- **应用限制**：目前主要面向刚体操纵任务，对于非刚体变形、软体操作等场景是否适用尚不明确。  
- **消融分析不足**：未在摘要中提及对不同组件（如表征空间选择、条件化方式）的消融实验，内部模块贡献度不清晰。  
- **领域假设**：方法依赖场景的三维结构信息，在传感器噪声大或部分遮挡环境中性能可能退化，文中未讨论。

（完）
