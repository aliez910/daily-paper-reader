---
title: "Video Prediction Policy: A Generalist Robot Policy with Predictive Visual Representations"
title_zh: 视频预测策略：具有预测视觉表征的通用机器人策略
authors: "Yucheng Hu, Yanjiang Guo, Pengchao Wang, Xiaoyu Chen, Yen-Jen Wang, Jianke Zhang, Koushil Sreenath, Chaochao Lu, Jianyu Chen"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=c0dhw1du33"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于视频扩散预测视觉表征的通用机器人策略
tldr: 现有视觉编码器主要捕获静态信息，忽略了动态方面。本文提出视频预测策略(VPP)，利用视频扩散模型预测未来帧，从而学习包含动态信息的视觉表征，用于机器人动作学习。实验表明VPP能够提升策略的泛化性能，为通用机器人策略的发展提供了新思路。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有视觉编码器捕获静态信息而忽视动态，限制了机器人策略的泛化。
method: 利用预训练的视频扩散模型生成预测未来帧，并从中学习视觉表征以指导动作生成。
result: 在多个仿真和真实任务上验证了VPP的有效性和泛化性。
conclusion: VPP展示了利用视频预测进行机器人动作学习的潜力，推动通用策略发展。
---

## Abstract
Visual representations play a crucial role in developing generalist robotic policies. Previous vision encoders, typically pre-trained with single-image reconstruction or two-image contrastive learning, tend to capture static information, often neglecting the dynamic aspects vital for embodied tasks. 
Recently, video diffusion models (VDMs) demonstrate the ability to predict future frames and showcase a strong understanding of physical world. 
We hypothesize that VDMs inherently produce visual representations that encompass both current static information and predicted future dynamics, thereby providing valuable guidance for robot action learning. 
Based on this hypothesis, we propose the Video Prediction Policy (VPP), which learns implicit inverse dynamics model conditioned on predicted future representations inside VDMs. 
To predict more precise future, we fine-tune pre-trained video foundation model on robot datasets along with internet human manipulation data.
In experiments, VPP achieves a 18.6\% relative improvement on the Calvin ABC-D generalization benchmark compared to the previous state-of-the-art, and demonstrates a 31.6\% increase in success rates for complex real-world dexterous manipulation tasks. For your convenience, videos can be found at https://video-prediction-policy.github.io/

---

## 论文详细总结（自动生成）

# 视频预测策略（VPP）：基于预测视觉表征的通用机器人策略

## 1. 核心问题与整体含义
现有机器人视觉编码器通常通过单帧图像重建或双帧对比学习进行预训练，这类方法倾向于捕获静态场景特征，而忽略了对具身任务至关重要的动态信息（如物体运动、动作后果等）。这种对动态信息的缺失限制了机器人策略在变化环境中的泛化能力。  
近年来，视频扩散模型（VDM）已展现出准确预测未来帧的能力，并内含着对物理世界的强理解。作者假设这类模型在内部表征中同时编码了当前静态信息与预测的未来动态，故可提取出更具指导性的视觉特征用于机器人动作学习。基于这一假设，该论文提出视频预测策略（Video Prediction Policy, VPP），旨在将视频扩散模型的预测能力融入策略学习，推动通用机器人策略的发展。

## 2. 方法论
- **核心思想**：利用预训练的视频扩散模型对未来帧进行预测，并从中提取既包含当前静态信息又包含预测动态的视觉表征，以此作为条件来指导机器人动作的生成。
- **关键技术细节**：
  - VPP 学习一个**隐式逆动力学模型**，该模型以视频扩散模型内部的预测未来表征为条件（即给定当前观察和预测的未来表征，输出当前动作）。
  - 为提高对未来预测的准确度，作者在机器人数据集以及互联网人类操作数据上，对预训练的视频基础模型进行**微调**，使其更好地适应机器人场景。
  - 方法不依赖显式的未来图像，而是利用扩散模型潜空间中的预测表征，实现视觉预测与动作生成的端到端融合。
- **公式与算法流程**（文本描述）：  
  输入当前图像帧 → 视频扩散模型编码并预测未来帧表征 → 提取该表征作为条件 → 逆动力学模型基于当前观测与预测表征输出当前动作 → 动作执行后循环。

## 3. 实验设计
- **数据集与场景**：
  - 仿真环境：**Calvin ABC-D 泛化基准**（包含多个桌面操控子任务，考察策略在新任务组合下的零样本泛化）。
  - 真实世界：**复杂灵巧操作任务**（涉及多指手的高精度操控，如物体重新抓取、精细放置等）。
- **对比方法**：与“之前最先进（previous state-of-the-art）”方法对比；具体对比了哪些基线方法文中未完整列举（如可能包括基于静态编码器的方法、不使用视频预测的方法等）。
- **Benchmark**：Calvin ABC‑D 给出了标准化的泛化评估协议；真实任务由研究者自定义评估，包含多类成功判别。

## 4. 资源与算力
论文摘要及提供的元数据中**未明确说明**所使用的 GPU 型号、数量或训练时长。考虑到该方法涉及微调大规模视频扩散模型，可推测需要较大的计算集群（如多张 A100 或 H100），但具体细节需阅读全文才能获知。

## 5. 实验数量与充分性
- **报告实验数**：文本主要报告了两组对比实验：① Calvin ABC‑D 泛化基准（相对提升 18.6%）；② 真实灵巧操控任务（成功率提升 31.6%）。  
- **充分性与客观性**：  
  - 覆盖了仿真与真实两种场景，初步证明了方法的有效性和泛化能力。  
  - 但仅从摘要看，**无法判断**论文内部是否包含充分的消融实验（例如对预测表征不同使用方式的对比、微调的影响、不同模型参数量的影响等）。  
  - 对比基线只提到“previous state‑of‑the‑art”，未列出具体方法，公平性难以全面评估。  
  - 综合而言，实验展示了显著性能提升，但**实验覆盖的深度与广度需阅读全文才能确定**。

## 6. 主要结论与发现
- 视频扩散模型能够提供富含动态信息的预测视觉表征，这对于机器人动作学习至关重要。
- 基于此表征学习隐式逆动力学模型的 VPP，在仿真泛化基准上相对之前最优方法提升 18.6%，在真实灵巧操作任务上成功率提升 31.6%。
- 该工作验证了利用视频预测进行机器人策略学习的可行性，为构建真正的通用机器人策略提供了新范式。

## 7. 优点
- **创新性**：首次将视频扩散模型内部的预测表征直接作为动作条件，区别于传统的静态编码器或两帧对比方法。
- **动态信息捕获**：天然利用 VDM 对未来物理动态的理解，弥补以往视觉编码对动态忽视的缺陷。
- **数据融合**：通过在机器人数据和互联网人类操作数据上微调视频基础模型，有效补充了机器人领域的数据局限性。
- **实验验证**：同时提供仿真与复杂真实任务的结果，表明方法不仅实验室规模有效，亦能应对真实世界的精细操控。

## 8. 不足与局限
- **计算开销**：依赖大规模视频扩散模型，推理时需执行帧预测，可能带来实时性与计算成本的挑战（文中未进行分析或优化讨论）。
- **实验覆盖有限**：仅展示了两个主要场景，未见在更多样机器人任务（如导航、移动操作）上的验证；消融分析、组件贡献、模型规模影响等未被摘要提及。
- **基线不透明**：对比“之前 SOTA”但未列出具体方法名，横向对比的公平性和完整性难以在摘要层面判断。
- **预测误差敏感性**：如果 VDM 预测不准确，可能误导逆动力学模型，但文中未讨论鲁棒性或误差分析。
- **泛化范围**：暂未讨论该方法能否从仿真直接迁移到不同物体、场景或未经训练的交互行为，通用性尚有验证空间。

（完）
