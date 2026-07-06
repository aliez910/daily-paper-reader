---
title: "BadVLA: Towards Backdoor Attacks on Vision-Language-Action Models via Objective-Decoupled Optimization"
title_zh: BadVLA：通过目标解耦优化对视觉-语言-动作模型实施后门攻击
authors: "Xueyang Zhou, Guiyao Tie, Guowen Zhang, Hecheng Wang, Pan Zhou, Lichao Sun"
date: 2025-09-18
pdf: "https://openreview.net/pdf?id=rEhVHla9zp"
tags: ["query:rob-il"]
score: 4.0
evidence: 分析VLA模型在端到端机器人控制中的安全漏洞
tldr: VLA模型通过多模态输入实现端到端机器人决策，但其紧耦合架构带来新的安全风险。BadVLA首次系统揭示VLA模型面临的后门攻击威胁，提出基于目标解耦优化的两阶段后门注入方法。该工作揭示了在训练即服务范式下VLA模型面临的潜在安全挑战，为后续构建安全可靠的VLA控制系统提供了重要警示。
source: NeurIPS-2025-Accepted
selection_source: conference_retrieval
motivation: VLA模型紧耦合架构存在后门攻击隐患，且在训练即服务场景下威胁尤为严重。
method: 提出目标解耦优化的两阶段后门攻击方法BadVLA。
result: 首次成功在VLA模型中嵌入隐蔽持久的后门，揭示了安全风险。
conclusion: 呼吁研究者在VLA模型设计中重视安全性与防御机制。
---

## Abstract
Vision-Language-Action (VLA) models have advanced robotic control by enabling end-to-end decision-making directly from multimodal inputs. However, their tightly coupled architectures expose novel security vulnerabilities. Unlike traditional adversarial perturbations, backdoor attacks represent a stealthier, persistent, and practically significant threat—particularly under the emerging Training-as-a-Service paradigm—but remain largely unexplored in the context of VLA models. To address this gap, we propose **BadVLA**, a backdoor attack method based on Objective-Decoupled Optimization, which for the first time exposes the backdoor vulnerabilities of VLA models. Specifically, it consists of a two-stage process: (1) explicit feature-space separation to isolate trigger representations from benign inputs, and (2) conditional control deviations that activate only in the presence of the trigger, while preserving clean-task performance. Empirical results on multiple VLA benchmarks demonstrate that BadVLA consistently achieves near-100\% attack success rates with minimal impact on clean task accuracy. Further analyses confirm its robustness against common input perturbations, task transfers, and model fine-tuning, underscoring critical security vulnerabilities in current VLA deployments. Our work offers the first systematic investigation of backdoor vulnerabilities in VLA models, highlighting an urgent need for secure and trustworthy embodied model design practices.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "BadVLA: Towards Backdoor Attacks on Vision-Language-Action Models via Objective-Decoupled Optimization" based on the provided content. I need to organize it according to the 8 specified points with Markdown formatting. Let me analyze the available information:

1. The PDF extraction failed (just shows CAPTCHA page)
2. The metadata provides a good overview
3. The abstract provides detailed methodology information

I'll work with the abstract and metadata to create a comprehensive summary, being careful to note when information is not directly available from the text (especially for the PDF content).
</think>
# BadVLA 论文总结

> 注：本次获取的 PDF 文本因 OpenReview 验证页面限制而未成功提取完整内容（仅有 CAPTCHA 页面），以下总结主要基于论文元数据与摘要（Abstract）进行整理，部分细节（尤其是实验配置与算力）可能存在不完整之处。

---

## 1. 核心问题与整体含义（研究动机与背景）

- **研究对象**：Vision-Language-Action（VLA）模型——一类能够直接从多模态输入（视觉 + 语言）实现端到端机器人决策的模型。
- **研究动机**：
  - VLA 模型具有"紧耦合架构"，将感知、语言理解与动作生成集成在统一框架中，这虽然提升了性能，但也带来了新的安全风险。
  - 在**"Training-as-a-Service"（训练即服务）**这一新兴范式下，模型可能由不可信的第三方训练或微调，后门攻击的威胁被显著放大。
  - 现有研究对 VLA 模型的对抗扰动已有所涉及，但对其**后门攻击（backdoor attack）**这一更隐蔽、更持久、实战意义更大的威胁缺乏系统性研究。
- **研究目标**：首次系统揭示 VLA 模型面临的后门攻击威胁，并提出一种有效的后门注入方法 BadVLA，以警示安全风险。

---

## 2. 方法论：核心思想与关键技术

### 总体思路
BadVLA 采用**目标解耦优化（Objective-Decoupled Optimization）**的两阶段方法，将后门注入过程中"对干净任务性能的影响"与"对触发器的攻击响应"分离优化，避免两者目标冲突。

### 关键技术细节
- **阶段一：特征空间显式分离（Explicit Feature-Space Separation）**
  - 在特征空间中显式地将"触发器表征"与"正常输入表征"分离；
  - 使模型能够在内部形成对触发器的独立、可区分的表示，从而为后续条件性偏差建立基础。
- **阶段二：条件性控制偏差（Conditional Control Deviations）**
  - 仅在触发器出现时激活攻击行为（控制偏差）；
  - 在不出现触发器时，模型行为与正常模型几乎一致，从而保持对**干净任务（clean-task）性能**的影响最小化。
- **攻击效果**：在多个 VLA benchmark 上实现接近 100% 的攻击成功率（ASR），且对干净任务准确率的影响极小。

> 原文未给出具体的损失函数形式或伪代码（因 PDF 未完整提取），以上为基于摘要的概括性描述。

---

## 3. 实验设计

### 数据集 / 场景
- 论文摘要中提到"在多个 VLA benchmarks 上"进行实验，但**未在摘要中明确列出具体 benchmark 名称**（如 LIBERO、OpenVLA 评估套件、RT-X 等是否被使用无法从摘要确认）。

### 对比方法
- 摘要中**未明确列出基线对比方法**。一般而言此类工作会与朴素后门攻击（如 BadNets 风格触发器）、投毒攻击等对比，但具体细节需查阅论文正文。

### 评估维度（基于摘要推断）
- **攻击成功率（ASR）**：在触发器存在时诱导恶意动作的成功率；
- **干净任务准确率（Clean Accuracy）**：在无触发器情况下执行正常任务的性能；
- **鲁棒性分析**：
  - 对常见输入扰动（Input Perturbations）的鲁棒性；
  - 任务迁移（Task Transfer）下的持久性；
  - 模型微调（Fine-tuning）下的持久性。

---

## 4. 资源与算力

- **未在提供的摘要与元数据中提及**具体的 GPU 型号、数量或训练时长。
- 由于 PDF 全文未能成功提取，相关算力信息**无法从当前可访问的材料中确认**。
- 推测：VLA 模型规模较大（如 OpenVLA-7B 级别），攻击实验通常需要多卡 A100/H100 级别的 GPU，但**未经原文证实**。

---

## 5. 实验数量与充分性

- **基于摘要的判断**：
  - 实验覆盖了**多个 VLA benchmark**、**多种鲁棒性场景**（扰动、迁移、微调），从攻击方法学角度较为全面。
  - 实现了**接近 100% 的 ASR** 与**极小的干净任务性能损失**，显示出方法的强有效性。
- **局限性**：
  - 摘要信息无法判断是否包含**消融实验（ablation study）**、**不同触发器类型/大小的对比**、**不同 VLA backbone 的对比**。
  - 摘要未说明对比基线的数量与种类，**实验公平性无法仅从摘要评估**。
  - 由于 PDF 未能完整获取，**实验充分性的全面判断受限**。

---

## 6. 主要结论与发现

- 首次系统性地证明了 VLA 模型**存在严重的后门漏洞**。
- BadVLA 能在多种 VLA benchmark 上实现**接近 100% 的攻击成功率**，且对干净任务性能的影响极小。
- BadVLA 注入的后门具有**鲁棒性**：
  - 能抵御常见输入扰动；
  - 在任务迁移场景下仍能保持；
  - 在模型微调后仍能存活。
- 强调在"训练即服务"范式下，VLA 模型的供应链安全面临**切实且紧迫**的威胁。
- 呼吁在 VLA 模型设计中纳入**安全性与防御机制**。

---

## 7. 优点与亮点

- **问题新颖性**：首次系统研究 VLA 模型的后门攻击问题，填补了研究空白。
- **方法创新**：将攻击目标解耦为"特征空间分离"与"条件性控制偏差"两个阶段，避免了攻击性能与干净性能之间的权衡冲突。
- **攻击隐蔽性与有效性兼顾**：ASR 接近 100% 的同时，对干净任务几乎无影响。
- **鲁棒性强**：在扰动、迁移、微调等现实威胁模型下均能保持攻击效果。
- **现实意义突出**：契合"训练即服务"等实际部署场景的安全需求，具有较强的工程警示价值。
- **对防御研究的启发性**：为后续 VLA 模型的安全训练、可信微调、防御性蒸馏等方向提供了明确的研究动机。

---

## 8. 不足与局限

- **PDF 全文未能获取**：本次无法从原文中获取实验细节、公式、伪代码与算力配置等关键信息，**总结的全面性受限**。
- **伦理与披露问题**：作为攻击性研究，若同时未配套提出针对性防御方法或安全建议，其纯粹的"暴露漏洞"价值可能受限（摘要中提到呼吁安全设计，但具体防御方案未明确给出）。
- **评估覆盖度未知**：摘要未说明是否评估了**不同规模 VLA**、**不同触发器形态**（patch、风格化、语义型）、**物理世界部署**等场景。
- **应用限制**：
  - 实验主要在仿真 benchmark 上进行，与真实机器人部署之间可能存在**sim-to-real gap**；
  - 触发器的物理可实现性、隐蔽性在现实环境中仍需进一步验证。
- **潜在偏差风险**：若实验仅在有限类型的 VLA 模型上验证，结论的**泛化性**可能不足。
- **复现性未知**：未在摘要中提及代码是否开源、是否提供预训练触发器等。

（完）
