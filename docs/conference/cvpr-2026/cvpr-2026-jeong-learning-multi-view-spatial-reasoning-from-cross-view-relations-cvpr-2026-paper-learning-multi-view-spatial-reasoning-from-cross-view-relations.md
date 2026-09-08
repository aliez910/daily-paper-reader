---
title: Learning Multi-View Spatial Reasoning from Cross-View Relations
title_zh: 基于跨视角关系学习多视角空间推理
authors: "Jeong, Suchae, Song, Jaehwi, Lee, Haeone, Kim, Hanna, Kim, Jian, Lee, Dongjun, Shin, Dong Kyu, Kim, Changyeon, Hahm, Dongyoon, Jin, Woogyeol, Choi, Juheon, Lee, Kimin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Jeong_Learning_Multi-View_Spatial_Reasoning_from_Cross-View_Relations_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 4.0
evidence: 源自机器人操作轨迹的大规模空间推理数据集
tldr: 现有视觉语言模型在单视角任务上表现优异，但缺乏多视角空间推理能力，难以支持跨视角的物体操作。为此，本文构建了 Cross-View Relations（XVR）大规模数据集，包含源自 1.8 万个三维场景与 7 万条机器人操作轨迹的 10 万个视觉问答样本，覆盖对应、验证与定位三类基本空间推理任务。在 XVR 上微调的视觉语言模型在多视角空间推理任务上取得显著提升，为具身智能研究提供了重要数据资源。
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1695, \"height\": 634, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 565, \"height\": 264, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 563, \"height\": 495, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 565, \"height\": 333, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 1801, \"height\": 504, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 867, \"height\": 1026, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 829, \"height\": 568, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1459, \"height\": 432, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-jeong-learning-multi-view-spatial-reasoning-from-cross-view-relations-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1576, \"height\": 766, \"label\": \"Table\"}]"
motivation: 现有视觉语言模型缺乏多视角空间推理能力，难以支持跨视角物体操作。
method: 构建 XVR 大规模数据集并微调视觉语言模型学习多视角空间推理。
result: 微调后的视觉语言模型在多视角空间推理任务上取得显著性能提升。
conclusion: 为多视角空间推理与具身智能研究提供了大规模数据资源与基线模型。
---

## Abstract
Vision-language models (VLMs) have achieved impressive results on single-view vision tasks, but lack the multi-view spatial reasoning capabilities essential for embodied AI systems to understand 3D environments and manipulate objects across different viewpoints. In this work, we introduce Cross-View Relations (XVR), a large-scale dataset designed to teach VLMs spatial reasoning across multiple views. XVR comprises 100K vision-question-answer samples derived from 18K diverse 3D scenes and 70K robotic manipulation trajectories, spanning three fundamental spatial reasoning tasks: Correspondence (matching objects across views), Verification (validating spatial relationships), and Localization (identifying object positions). VLMs fine-tuned on XVR achieve substantial improvements on established multi-view and robotic spatial reasoning benchmarks (MindCube and RoboSpatial). When integrated as backbones in Vision-Language-Action models, XVR-trained representations improve success rates on RoboCasa. Our results demonstrate that explicit training on cross-view spatial relations significantly enhances multi-view reasoning and transfers effectively to real-world robotic manipulation.

---

## 论文详细总结（自动生成）

<think>
The user wants a detailed Chinese summary of the paper "Learning Multi-View Spatial Reasoning from Cross-View Relations" following a specific structure. Let me analyze the paper carefully and provide a comprehensive summary.

The paper introduces XVR (Cross-View Relations), a large-scale dataset for multi-view spatial reasoning. Let me organize my response according to the 8 required points.

Key points to cover:
1. Core problem and motivation
2. Methodology
3. Experimental design
4. Resources and compute
5. Experimental volume and adequacy
6. Main conclusions
7. Strengths
8. Limitations

Let me write this in Chinese, with Markdown formatting.
</think>
# 论文总结：基于跨视角关系学习多视角空间推理（XVR）

## 1. 核心问题与研究动机

- **核心问题**：现有视觉语言模型（VLMs）虽然在单视角视觉任务（如 OCR、图像描述、视频理解）上表现优异，但**缺乏多视角空间推理能力**。在机器人、自动驾驶、AR/VR 等典型多相机应用场景中，模型需要理解不同视角之间的几何关系，以支持物体操作、导航和场景重建等任务。
- **现有研究不足**：
  - 主流空间推理数据集（如 SpatialVLM、RoboSpatial、3DSRBench、All-Angles-Bench 等）大多**仅提供单一视角**或侧重"单视角内的物体属性"，无法刻画跨视角几何关系。
  - 少数多视角数据集（如 MultiSPA、MMSI-Bench、MindCube）要么缺少显式跨视角几何监督，要么**未同时覆盖通用场景与机器人域**。
  - 模型在单视角上虽然视觉合理，但**跨视角会出现空间不一致**。
- **本文动机**：构建一个**显式监督跨视角几何关系**的大规模多视角 VQA 数据集，使 VLMs 真正学会"如何在不同视角间建立联系"。

## 2. 方法论

### 2.1 总体思路
提出 **Cross-View Relations (XVR)** 数据集，从 **SfM（Structure-from-Motion）** 的三阶段（对应点匹配 → 一致性验证 → 相机姿态估计）汲取灵感，将多视角空间推理抽象为 **三大类共 8 个子任务**。

### 2.2 任务分类（受 SfM 启发）
- **Correspondence（对应）**：跨视角匹配同一物理实体
  - Point Correspondence：在多视图中定位同一 3D 点
  - Directional Correspondence：跨视角匹配一致的 3D 方向（向量/箭头）
- **Verification（验证）**：检测跨视角的几何/时间一致性
  - Spatial Verification：识别违反 3D 一致性的对应
  - Temporal Verification：在序列中找出时间不一致的帧
- **Localization（定位）**：推断相机之间的相对空间关系
  - Viewpoint Localization：从多参考图确定目标相机位置
  - Directional View Localization：识别"在某方向上"的相机视图
  - Cross-Scenario Localization：跨结构相似场景匹配相同视角
  - Language-Conditioned Localization：根据自然语言描述（如"手腕相机"）选择对应视角

### 2.3 数据生成框架
- **统一生成函数**：G : (I, P, X, T, M) → (Q, A)
  - 输入：图像 I、相机参数 P、3D 几何 X、时间索引 T、元数据 M
  - 输出：问答对 (Q, A)
- **两种数据源对应两套管线**：
  - **通用域管线（General Domain）**：基于 WildRGB-D 等标定多视角数据，对 3D 原始几何（点/相机位姿）做 3D→2D 投影，构造"参考图—目标图—多选项"QA，并生成空间分离的干扰项以避免浅层视觉线索作弊。
  - **机器人域管线（Robotic Domain）**：基于 OXE（Open X-Embodiment）与 AgiBot-World 等机器人轨迹数据，从时空元数据 M 与时间索引 T 采样生成 QA；针对 Temporal Verification，采用 **SSIM 过滤 + 动作启发式**确保时间差异在视觉上可区分。

### 2.4 数据源与严格筛选
- **通用域**：WildRGB-D（保留点云密度 ≥ 1M 点的样本以保证 3D 投影可靠性）
- **机器人域**：从 OXE 套件中仅保留**至少 3 个相机视角**的子集（DROID、Mobile ALOHA、RoboSet、FMB），并满足相机标识一致、轨迹时长 ≥ 20 秒、末端执行器运动显著等条件
- **数据规模**：源自 **18K 3D 场景 + 70K 机器人轨迹** → 447K 图像 → **103K VQA 样本**（平均 4.32 图/样本）

## 3. 实验设计

### 3.1 自建评测基准：XVR-Eval
- **规模**：1,866 条 held-out 样本
- **数据来源**：训练未见的 Mobile ALOHA 轨迹 + WildRGB-D "boat" 场景
- **人类基线**：9 名具有至少 4 年高等教育的标注者，跨任务共收集 795 条标注

### 3.2 评估的 VLM
- **闭源模型**：Claude-4.5-Sonnet、GPT-5、Gemini-2.5-Flash、Gemini-2.5-Pro、Gemini-Robotics-ER-1.5
- **开源模型**：Eagle2-2B、Paligemma2-3B、InternVL-3.5-4B、Qwen3-VL-2B/4B-Instruct
- **本文训练模型**：Qwen3-VL-2B-XVR（在 Qwen3-VL-2B-Instruct 上用 XVR 微调）

### 3.3 外部基准
- **MindCube-Tiny**：分 Around / Rotation / Among 三个子任务
- **RoboSpatial-Home**：评估 Compatibility（空间适配）与 Configuration（物体-物体空间关系），排除 Context 子任务（所有模型为 0）

### 3.4 VLA 下游迁移实验
- **架构**：在 VLM 上加 GR00T-N1.5 风格的扩散动作头
- **训练数据**：NVIDIA GR00T-X-Embodiment-Sim（RoboCasa 仿真器）
- **任务**：Franka 机械臂执行三类操作
  - CoffeePressButton：按钮仅在腕部相机可见
  - TurnOffMicrowave：微波炉面板在左右相机可见、腕部不可见
  - PnPCabToCounter：从 64 个物体类别中抓取并放置
- **评估**：每任务 1,000 次 rollout 的成功率

### 3.5 对比方法与基线
- Random 基线、Human 基线、闭源与开源零样本 VLM、+XVR 微调模型
- VLA 实验中以原 Qwen3-VL-2B VLA 作为基线

## 4. 算力与训练资源

- **未明确披露**：论文未给出具体的 GPU 型号/数量、训练时长、batch size、optimizer 等训练超参
- **间接信息**：
  - 微调 VLM：基于 Qwen3-VL-2B-Instruct，约 10 万样本规模
  - VLA 训练：使用 GR00T-X-Embodiment-Sim + RoboCasa 仿真，1,000 次 rollout/任务
  - 数据生成涉及 3D 投影、SSIM 过滤、大规模 QA 合成，但具体并行/算力未说明
- **可视为局限性**：算力与训练成本信息缺失，难以复现其计算开销

## 5. 实验数量与充分性

- **实验类别较丰富**：
  1. XVR-Eval 8 个子任务 × 多模型对比（10 个 VLM + 随机 + 人类基线）
  2. 跨域外部基准迁移（MindCube-Tiny 3 子任务 + RoboSpatial-Home 2 子任务）
  3. 下游 VLA 三类操作任务 × 1,000 rollout 的仿真评估
  4. 任务级、人/模型/闭源/开源多维对比分析
- **优势**：
  - 涵盖训练集评测 + 跨域迁移 + 真实下游任务，证据链完整
  - 人类基线 + 随机基线提供上下界参考
  - 包含 Distribution Shift 分析（如 MindCube 由内向外 vs XVR 由外向内的相机朝向差异）
- **不足**：
  - 缺乏消融实验：未消融"3 类任务/8 子任务"的相对贡献
  - 缺乏数据规模/配比消融
  - VLA 仅在仿真中评估，未在真实机器人上验证
  - 训练超参与算力缺失 → 难以复现

## 6. 主要结论与发现

- **整体提升**：Qwen3-VL-2B-XVR 在 XVR-Eval 整体准确率上较基线提升 **+1.8 倍相对增益（68.06% vs 36.82%）**，并超过所有闭源模型
- **任务级发现**：
  - **几何类任务大幅提升**：Point Correspondence 由 46.59% → 94.32%，Spatial Verification 由 23.11% → 84.85%（甚至超过 GPT-5）
  - **定位任务一致提升**：Viewpoint Localization 接近人类水平
  - **Temporal Verification 出现下降**（45.29% → 41.18%）：XVR 偏同步几何，牺牲了时间敏感性
- **闭源模型观察**：
  - Gemini-Robotics-ER-1.5 在 Viewpoint Localization 上仅 6.22%，低于随机（22.22%），说明**机器人专用训练未带来跨视角关系理解**
  - 模型规模与空间推理能力并不正相关（Gemini-2.5-Flash > Pro）
- **跨域迁移**：在 MindCube 和 RoboSpatial 上稳定提升，最大增益在 Compatibility (+7.6%) 和 Among (+7.0%)；但涉及连续相机运动的 Around/Rotation 提升有限
- **VLA 迁移**：三任务均提升，平均 **+13% 绝对成功率**；TurnOffMicrowave 提升最大（45.7% → 72.7%）
- **超人类表现**：在 Point Correspondence 与 Spatial Verification 上超过人类基线

## 7. 优点

- **任务设计有理论根基**：借鉴 SfM 三大阶段（对应、验证、定位），逻辑清晰且具备几何可解释性
- **数据源异构且互补**：通用域提供精确几何，机器人域提供动态视角切换，覆盖面广
- **显式跨视角监督**：平均 4.32 图/样本，是少数同时覆盖通用+机器人域的显式跨视角数据集
- **证据链完整**：数据集 → XVR-Eval → 外部基准 → VLA 仿真迁移，从训练到下游应用逐级验证
- **细致的人类基线 + 闭源对比**：包含 9 人 795 标注以及 5 个闭源模型对比，提供了清晰的能力定位
- **生成管线严谨**：SSIM 过滤、3D 投影、空间分离干扰项等设计避免"视觉作弊"
- **任务设计可操作性强**：8 个子任务显式覆盖 Correspondence/Verification/Localization 三类核心能力

## 8. 不足与局限

- **时间推理能力下降**：Temporal Verification 训练后性能下降，且对动态相机运动（MindCube Around/Rotation）迁移有限，揭示几何—时间权衡
- **VLA 仅仿真评估**：未在真实机器人上验证，物理执行的复杂性未被覆盖
- **训练细节缺失**：未披露 GPU 型号/数量、训练时长、batch size、优化器等超参，可复现性受限
- **缺少消融实验**：
  - 未消融三大类/八子任务各自贡献
  - 未消融数据规模、域配比（50% 静态 + 50% 机器人轨迹）的合理性
  - 未消融不同 VLM 骨干的差异
- **分布差异未完全弥合**：MindCube 相机朝向（外向内）与 XVR（内向外）相反，限制了部分任务迁移
- **闭源模型评测的不确定性**：通过 API 调用闭源模型，结果可能受版本、提示词、温度等影响，未报告具体复现设置
- **应用场景仍以机器人为中心**：对 AR/VR、自动驾驶等其它多视角场景的实际收益未经验证
- **数据偏差风险**：WildRGB-D 场景偏室内，OXE 偏固定工位，可能无法覆盖真实世界的全部多样性

（完）
