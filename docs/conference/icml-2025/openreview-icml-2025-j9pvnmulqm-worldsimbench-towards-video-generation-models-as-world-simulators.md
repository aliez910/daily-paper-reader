---
title: "WorldSimBench: Towards Video Generation Models as World Simulators"
title_zh: WorldSimBench：面向视频生成模型的世界模拟器基准
authors: "Yiran Qin, Zhelun Shi, Jiwen Yu, Xijun Wang, Enshen Zhou, Lijun Li, Zhenfei Yin, Xihui Liu, Lu Sheng, Jing Shao, LEI BAI, Ruimao Zhang"
date: 2025-05-01
pdf: "https://openreview.net/pdf?id=j9pVnmulQm"
tags: ["query:rob-il"]
score: 4.0
evidence: 世界模拟器基准包含操作评估，与操作基准间接相关
tldr: 本文针对现有预测模型缺乏层次分类和评估标准的问题，提出WorldSimBench，将预测模型功能层次化，并从感知和操作两个层面评估世界模拟器，融入人类偏好。该基准填补了从具身视角评估视频生成模型的空白，为未来世界模型研究提供参考。
source: ICML-2025-Accepted
selection_source: conference_retrieval
motivation: 现有预测模型缺乏分类和评估标准，尤其缺少从具身视角评估世界模拟器的基准。
method: 提出WorldSimBench，包括显式感知评估和隐式操作评估的双重评估框架。
result: 该基准能有效评估视频生成模型作为世界模拟器的能力，涵盖人类偏好。
conclusion: WorldSimBench为高能力具身预测模型的评估提供了新平台。
---

## Abstract
Recent advancements in predictive models have demonstrated exceptional capabilities in predicting the future state of objects and scenes. However, the lack of categorization based on inherent characteristics continues to hinder the progress of predictive model development. Additionally, existing benchmarks are unable to effectively evaluate higher-capability, highly embodied predictive models from an embodied perspective. In this work, we classify the functionalities of predictive models into a hierarchy and take the first step in evaluating World Simulators by proposing a dual evaluation framework called WorldSimBench. WorldSimBench includes Explicit Perceptual Evaluation and Implicit Manipulative Evaluation, encompassing human preference assessments from the visual perspective and action-level evaluations in embodied tasks, covering three representative embodied scenarios: Open-Ended Embodied Environment, Autonomous, Driving, and Robot Manipulation. In the Explicit Perceptual Evaluation, we introduce the HF-Embodied Dataset, a video assessment dataset based on fine-grained human feedback, which we use to train a Human Preference Evaluator that aligns with human perception and explicitly assesses the visual fidelity of World Simulater. In the Implicit Manipulative Evaluation, we assess the video-action consistency of World Simulators by evaluating whether the generated situation-aware video can be accurately translated into the correct control signals in dynamic environments. Our comprehensive evaluation offers key insights that can drive further innovation in video generation models, positioning World Simulators as a pivotal advancement toward embodied artificial intelligence.

---

## 论文详细总结（自动生成）

# WorldSimBench：面向视频生成模型的世界模拟器基准 —— 中文总结

## 1. 核心问题与整体含义（研究动机与背景）
- **核心缺陷**：现有预测模型（如视频生成模型）虽已能预测未来场景，但缺乏**基于自身能力等级的分类体系**，且**缺少从具身智能（Embodied AI）视角评估模型作为“世界模拟器”的标准化基准**。  
- **研究目标**：提出一个层级化的功能分类，并构建首个双维度评估框架 **WorldSimBench**，用于衡量视频生成模型作为世界模拟器的综合能力，从而填补该领域在评测方法上的空白。

## 2. 方法论：核心思想与关键技术细节
### 2.1 整体框架
- 将世界模拟器的功能分为**层级化**类别，并引入**双重评估**机制：
  - **显式感知评估（Explicit Perceptual Evaluation）**  
    - 从视觉感知角度评估生成视频的**保真度**与**人类偏好**。  
    - 构建 **HF-Embodied 数据集**（基于细粒度人类反馈的视频评估数据集），训练 **人类偏好评估器（Human Preference Evaluator）**，使其与人类主观判断对齐。
  - **隐式操作评估（Implicit Manipulative Evaluation）**  
    - 从**动作控制**角度评估视频与动作的**一致性**。  
    - 检测生成的情境感知视频能否在动态环境中被准确转换为正确的控制信号。

### 2.2 覆盖场景
- 三个代表性具身场景：  
  - **开放式具身环境（Open-Ended Embodied Environment）**  
  - **自动驾驶（Autonomous Driving）**  
  - **机器人操作（Robot Manipulation）**

### 2.3 关键技术细节（文献中未提供具体公式或算法流程，仅作概念描述）
- 人类偏好评估器使用 HF-Embodied 数据集进行监督训练，模拟人对视频质量的偏好。  
- 隐式操作评估通过将生成视频输入到预定义的动作映射模型中，对比预测动作与真实动作的一致性。

## 3. 实验设计
### 3.1 所用数据集 / 场景
- **HF-Embodied 数据集**：用于显式评估中训练人类偏好评估器。  
- **三大评估场景**：开放式具身环境、自动驾驶、机器人操作（具体数据集名称未在摘要中列出）。

### 3.2 Benchmark 设置
- WorldSimBench 本身即为新提出的基准，包含上述双重评估协议。

### 3.3 对比方法
- **论文内容中未提及对比了哪些视频生成模型**；仅说明该基准可用于评估各类世界模拟器。

## 4. 资源与算力
- **论文内容未明确说明**训练或评估所消耗的 GPU 型号、数量、时长等算力信息。  
- 因此无法提供具体资源使用数据。

## 5. 实验数量与充分性
- **实验组数**：仅从摘要可知进行了显式感知评估和隐式操作评估，并在三个场景下分别实施；未提及消融实验或具体实验次数。  
- **充分性分析**：  
  - 优点：覆盖了感知与动作两个关键维度和多个具身场景，设计较全面。  
  - 不足：缺少与现有基准的定量比较、模型间性能对比等详细实验细节，且未提及多轮交叉验证或鲁棒性测试，因此**实验充分性存疑**，需参考完整论文判断。

## 6. 主要结论与发现
- WorldSimBench 能**有效区分**不同视频生成模型作为世界模拟器的能力。  
- 显式评估可反映人类对视觉质量的偏好，隐式评估可反映视频内容对动作控制的支撑程度。  
- 该基准为**高能力具身预测模型**的评估提供了新平台，并为视频生成模型向具身智能发展提供了方向性启示。

## 7. 优点（方法或实验设计亮点）
- **首创性**：首次从具身视角建立世界模拟器的层次化评估标准。  
- **双维度设计**：同时考虑视觉感知（人类偏好）和动作一致性（隐式控制），弥补了传统仅关注视觉指标的缺陷。  
- **场景覆盖**：包含开放式环境、自动驾驶、机器人操作三类典型具身任务，具有一定代表性。  
- **数据集构建**：通过细粒度人类反馈（HF-Embodied）训练偏好评估器，使机器评估接近人类判断。

## 8. 不足与局限
- **实验公开性弱**：摘要中未提供具体实验结果、对比模型、消融分析等，导致无法独立验证方法有效性。  
- **信息缺失**：算力资源、训练细节、模型架构、人类标注规模等均未说明，限制了可复现性。  
- **偏差风险**：人类偏好评估器可能引入标注者主观偏差，且仅三个场景是否足以泛化到所有具身任务尚存疑虑。  
- **应用限制**：隐式评估依赖于“生成视频→动作信号”的映射准确性，若映射模型本身有偏，则评估结果可能失真。

---
（完）
