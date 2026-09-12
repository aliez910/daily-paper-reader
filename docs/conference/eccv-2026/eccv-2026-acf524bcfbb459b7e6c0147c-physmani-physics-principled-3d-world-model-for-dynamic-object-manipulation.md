---
title: "PhysMani: Physics-principled 3D World Model for Dynamic Object Manipulation"
title_zh: PhysMani：面向动态物体操纵的物理约束3D世界模型
authors: "Peng Yun, Shouwang Huang, Hao Li, Jinxi Li, Jianan Wang, Bo Yang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/6204.pdf"
tags: ["query:rob-il"]
score: 7.0
evidence: 面向动态操纵的视觉-语言-动作模型与3D未来预测
tldr: 在非结构化3D环境中操纵快速运动目标仍是具身AI的难题：现有视觉-语言-动作与世界模型缺乏精确的3D几何和物理上有意义的预测能力。本文提出PhysMani框架，将基于物理的3D高斯世界模型与具有未来感知的动作策略模型耦合：通过在线优化学习无散度高斯速度场以实现快速且物理一致的动态预测，并借助可学习的跨注意力模块将未来3D动态融入动作决策；同时发布包含16个任务的PhysMani-Bench基准，验证了模型在动态操纵上的优越性能。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 390, \"height\": 521}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-002.webp\", \"caption\": \"\", \"page\": 4, \"index\": 2, \"width\": 1182, \"height\": 887}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-003.webp\", \"caption\": \"\", \"page\": 4, \"index\": 3, \"width\": 627, \"height\": 417}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-004.webp\", \"caption\": \"\", \"page\": 4, \"index\": 4, \"width\": 627, \"height\": 392}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-005.webp\", \"caption\": \"\", \"page\": 4, \"index\": 5, \"width\": 877, \"height\": 685}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-006.webp\", \"caption\": \"\", \"page\": 7, \"index\": 6, \"width\": 362, \"height\": 334}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-007.webp\", \"caption\": \"\", \"page\": 11, \"index\": 7, \"width\": 2040, \"height\": 717}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-008.webp\", \"caption\": \"\", \"page\": 12, \"index\": 8, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-009.webp\", \"caption\": \"\", \"page\": 12, \"index\": 9, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-010.webp\", \"caption\": \"\", \"page\": 12, \"index\": 10, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-011.webp\", \"caption\": \"\", \"page\": 12, \"index\": 11, \"width\": 1280, \"height\": 720}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-012.webp\", \"caption\": \"\", \"page\": 12, \"index\": 12, \"width\": 2016, \"height\": 1512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-013.webp\", \"caption\": \"\", \"page\": 12, \"index\": 13, \"width\": 2016, \"height\": 1512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-014.webp\", \"caption\": \"\", \"page\": 12, \"index\": 14, \"width\": 2016, \"height\": 1512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-015.webp\", \"caption\": \"\", \"page\": 12, \"index\": 15, \"width\": 2016, \"height\": 1512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-016.webp\", \"caption\": \"\", \"page\": 12, \"index\": 16, \"width\": 2016, \"height\": 1512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-acf524bcfbb459b7e6c0147c/fig-017.webp\", \"caption\": \"\", \"page\": 14, \"index\": 17, \"width\": 932, \"height\": 563}]"
motivation: 现有VLA与世界模型在快速运动目标操纵中缺乏精确3D几何与物理预测。
method: 耦合物理约束的3D高斯世界模型与未来感知策略，通过无散度速度场与跨注意力融合。
result: 在PhysMani-Bench上16个动态操纵任务取得优越表现。
conclusion: 物理一致的世界模型为VLA在动态操纵中的精确控制提供有效支撑。
---

## Abstract
Manipulating fast and dynamically moving targets in un-structured 3D environments remains challenging for embodied AI. Ex-isting visual-language-action models and world models struggle with ac-curate 3D geometry and physically meaningful forecasting. We proposePhysMani, a framework that couples a physics-principled 3D Gaussianworld model with a future-aware action policy model. The world modellearns a divergence-free Gaussian velocity field via online optimizationfor fast and physically grounded future dynamics prediction. The pol-icy model integrates the predicted 3D scene future dynamics through alearnable token based cross-attention module. We introduce PhysMani-Bench, a dynamic manipulation benchmark with 16 tasks, and demon-strate a superior success rate over strong baselines in both simulationand real-world robot experiments. Our code and data are available athttps://github.com/vLAR-group/PhysMani

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze a paper about PhysMani, a physics-principled 3D world model for dynamic object manipulation. I need to provide a structured Chinese summary covering specific points. Let me carefully analyze the paper content and provide a comprehensive summary.

Let me think through each section:

1. Core problem: Dynamic object manipulation in unstructured 3D environments - existing VLAs and world models lack accurate 3D geometry awareness and physically meaningful forecasting
2. Method: Physics-principled 3D Gaussian world model with divergence-free velocity field + future-aware action policy with cross-attention
3. Experiments: PhysMani-Bench with 16 tasks (8 groups × 2 speeds), comparisons with Act3D, pi0.5, ManiGaussian, 3DDA, 3DFA, 3DFA-OF, plus real-world tasks
4. Compute: RTX 4090, inference 272.8ms/frame, world model optimization ~200ms, training 53 hours
5. Experimental quantity: Multiple ablations, real-world tests, generalization studies
6. Conclusions: PhysMani outperforms baselines by 8.1 points on average
7. Strengths: Physics-grounded approach, online optimization for speed, benchmark contribution
8. Limitations: Moderate-sized benchmark (16 tasks), not scaled to hundreds of tasks, specific scenarios

Let me organize this into a well-structured Chinese summary.</think>

# PhysMani 论文详细总结

## 一、核心问题与研究动机

### 1.1 核心问题
在非结构化的 3D 环境中对**快速、复杂运动的动态目标**进行精准操作，是具身智能领域长期未解决的核心难题。典型场景包括：
- 接住被抛出的球
- 将物品装载到移动的容器中
- 将盘子放到旋转的转盘上
- 在传送带或桌面上抓取运动物体

### 1.2 现有方法的三大不足
- **几何感知缺失**：现有 VLA（视觉-语言-动作）模型与世界模型对 3D 场景几何缺乏显式建模；
- **物理一致性不足**：基于视频生成的世界模型虽画面逼真，但预测的动态常违反基本物理规律（如散度自由条件），无法可靠地指导 3D 空间中的精确动作；
- **推理延迟过高**：大型视觉-语言-扩散模型链式推理速度慢，难以满足动态操作对实时性的要求。

### 1.3 研究意义
动态目标操作要求机器人同时具备**3D 几何理解、物理一致性预测、低延迟响应**三种能力。本文正是填补这一关键空白的工作。

---

## 二、方法论

### 2.1 整体框架
PhysMani 由两个并行模块组成：
1. **物理约束的 3D 高斯世界模型**：连续学习场景的几何、外观与物理动态；
2. **未来感知的动作策略模型**：将当前视觉观测与预测的未来动态共同作为输入，输出机器人动作。

### 2.2 物理约束的 3D 高斯世界模型

#### 核心思想
基于 3D Gaussian Splatting（3DGS），为每个高斯核学习一个**无散度（divergence-free）的速度场**，确保预测的未来动态满足不可压缩流体的物理约束。

#### 三个核心子模块
- **规范化 3D 高斯模块**：在 $t=0$ 时，由 $C$ 个相机的 RGB/D 观测初始化高斯集合 $\mathcal{G}_0 = \{g_0, r_0, s_0, \sigma, c\}$（位置、四元数、缩放、不透明度、颜色），通过反向投影稀疏点云并使用 $\ell_1 + \ell_{SSIM}$ 损失优化。
- **物理约束的高斯速度模块**：对每个高斯学习 6 个基本速度分量 $V_t = [v_x^t, v_y^t, v_z^t, w_z^t, w_y^t, w_x^t]$（三个线速度+三个角速度）。速度场表示为：
  
  $$v(g_t, t) = V_t \cdot B(g_t)$$
  
  其中 $B(g_t) \in \mathbb{R}^{6 \times 3}$ 是基础向量矩阵，理论上保证散度为零。
- **在线优化未来动态**：摒弃原 FreeGave 中复杂的形变网络与离线优化策略，改为**流式在线优化**（见算法1），每次新帧到达后：
  1. 获取当前速度场 $v(g_t, t)$；
  2. 用 FreeGave 的交错中点法将高斯从 $t'$ 推到 $t$；
  3. 通过 $\ell_1 + \ell_{SSIM}$ 损失梯度优化高斯的位置、方向、速度网络 $f_{vel}$ 共 $T=50$ 次迭代；
  4. 冻结 $f_{vel}$ 后再细化 $T'=7$ 次迭代以补偿外观变化；
  5. 单轮约 200 ms，单卡 RTX 4090 即可运行。

### 2.3 未来感知的动作策略模型

#### 骨干网络
采用 **3D FlowMatch Actor（3DFA）** 作为骨干，使用 Rectified Flow 进行高效去噪预测末端执行器的关键位姿。

#### 未来动态融合（核心创新）
对 3D 场景点云 $P_t \in \mathbb{R}^{4096 \times 3}$ 中的每个点 $p_t$，按如下 6 步融入动态信息：
1. **KNN 检索**：找到与 $p_t$ 最近的 $K$ 个高斯 $\{g_t^1, \dots, g_t^K\}$；
2. **计算偏移**：$\Delta p = p_t - g_t^k$；
3. **聚合**：得到 $\Delta P \in \mathbb{R}^{4096 \times K \times 3}$ 及对应速度 $\hat{D}_t \in \mathbb{R}^{4096 \times K \times 6}$；
4. **MLP 编码**：分别将 $\Delta P$ 与 $\hat{D}_t$ 编码为 $\Delta\bar{P} \in \mathbb{R}^{4096 \times K \times 120}$ 与 $\bar{D}_t \in \mathbb{R}^{4096 \times K \times 120}$；
5. **可学习查询的跨注意力**：引入可学习向量 $L \in \mathbb{R}^{1 \times 120}$ 作为 query，$\Delta\bar{P}$ 作 key，$\bar{D}_t$ 作 value，经 3 个注意力层后得到动态 token $\tilde{D}_t \in \mathbb{R}^{4096 \times 120}$；
6. **融合**：将 $\tilde{D}_t$ 与视觉 token $\tilde{F}_{vis}^t$ 相加，得到未来感知 token $A_t$，送入策略网络。

#### 训练损失
联合监督流匹配速度场（$\ell_2$）与夹爪开闭状态（BCE）。

### 2.4 计算加速
由于高斯数量固定，作者**复用静态计算图**，避免动态构建，显著降低 kernel 启动开销。

---

## 三、实验设计

### 3.1 PhysMani-Bench（仿真基准）
基于 RLBench 扩展构建，含 **8 组任务 × 2 速度档（normal / high）= 16 个任务**：
| 任务类别 | 内容 |
|---|---|
| Beat Buzz | 沿旋转钢丝引导环形工具 |
| Insert Peg | 将环套入旋转立柱 |
| Drop to Hoop | 将球投入移动篮筐 |
| Pick Cube | 抓取桌面运动立方体 |
| Push Button | 按压桌面运动按钮 |
| Deposit Rubbish | 投垃圾到移动箱 |
| Place Cup | 将杯子挂到旋转架 |
| Remove Cup | 从旋转架上取下杯子 |

- 每个任务 160 条专家轨迹，按 100/20/40 划分训练/验证/测试集；
- 4 个固定外置相机；
- 目标速度最高达 2 m/s（与 Franka Panda 末端最大速度相当）。

### 3.2 对比方法
| 方法 | 类型 |
|---|---|
| Act3D | 体素化 3D 动作预测 |
| pi0.5 | 通用 VLA 模型（LoRA 微调） |
| ManiGaussian | 动态高斯+动作策略 |
| 3DDA | 3D 扩散策略 |
| 3DFA | 3D Rectified Flow 策略 |
| 3DFA-OF | 3DFA + 2D 光流（5通道） |

### 3.3 评估指标
- **主指标**：成功率（SR）
- **次指标**：PSNR、SSIM、LPIPS、logRMSE（深度）、目标轨迹欧氏距离

### 3.4 真实世界任务
使用 Astribot S1 双指机械臂 + 4 个 RealSense D435i 相机（240×320 分辨率，5 Hz 控制），4 个任务（传送带抓取、传送带放置、旋转架放置、旋转架取杯），共 180 训练 + 60 验证 episode，每模型 64 次在线试验。

---

## 四、算力资源

| 项目 | 配置 |
|---|---|
| GPU | NVIDIA RTX 4090（单卡） |
| CPU | Intel Core i7-13700F |
| 世界模型单帧优化 | ≈ 200 ms |
| 策略推理 | 272.8 ms/frame |
| 训练时长 | 53 小时 |
| 显存占用 | 22 GB（训练）/ 1 GB（推理） |

> 单卡 RTX 4090 即可完成所有训练与推理，是该方法实用性的一大亮点。

---

## 五、实验数量与充分性

### 5.1 主要实验
1. **PhysMani-Bench 仿真评估**：16 任务 × 6 基线（含消融版本），覆盖 8 大类动态操作；
2. **未来帧预测评估**：4 个相机 × 16 任务 × 多个时间步（1st/5th/10th）；
3. **真实世界 4 任务评估**：每任务 64 次试验；
4. **泛化能力实验**：变化物体形状、颜色、速度、初始位置；
5. **消融实验**：
   - 移除速度分量 $D_t$；
   - 移除可学习 token $L$（改用 self-attention）；
   - 优化迭代次数 $T \in \{10, 20, 30, 40, 50\}$；
6. **速度场可视化分析**：展示 6 个基本速度分量在动态物体上的聚焦；
7. **计算效率分析**：与 FreeGave、ManiGaussian 等对比训练/推理时间。

### 5.2 充分性评价
- **优点**：评估覆盖了仿真+真实、多个基线、多个消融维度；每个方法取最后 5 个 checkpoint 中最优 3 个模型以减小方差；
- **可能的不足**：仅在 RLBench 风格场景下评测，缺乏对其他机器人平台（移动臂、人形机器人）的迁移验证；真实实验任务数仅 4 个。

---

## 六、主要结论与发现

1. **PhysMani 平均 SR 达 45.9%**，较次优的 3DFA（37.8%）**提升 8.1 个百分点**；
2. **未来帧预测质量显著优于 ManiGaussian 与 FreeGave**：在 1st、5th、10th 帧上 PSNR、轨迹误差均更优；
3. **推理速度提升 3.0×**：PhysMani 单帧 205 ms，FreeGave 607 ms；
4. **2D 光流信息不足**：3DFA-OF 与 3DFA 性能几乎持平，说明仅靠 2D 运动线索无法捕获 3D 动态；
5. **强 VLA 模型 pi0.5 在高速任务中表现差**，反映其对 3D 几何与物理动态的捕获能力不足；
6. **物理一致性可视化**：速度分量自然聚焦于机器人臂与运动目标，忽略静态背景，验证了物理先验的有效性；
7. **真实世界中平均 SR 62.5%**，较 3DFA（45.3%）提升 17.2 个百分点；
9. **方法对优化迭代次数 $T$ 不敏感**：$T=10$ 时仍达 45.8% SR，表明模型具有较好的鲁棒性。

---

## 七、优点与亮点

1. **首个面向通用动态操纵的物理一致 3D 世界模型 + 策略框架**，填补了 VLA 在动态任务上的能力空白；
2. **无散度速度场**为预测结果提供严格的物理约束，避免了视频生成模型的"画面逼真但物理不合理"问题；
3. **在线优化 + 静态计算图复用**实现 200 ms 级在线更新，远快于原版 FreeGave（607 ms）；
4. **模块化设计**：3DFA 骨干可替换，便于复用；
5. **PhysMani-Bench 基准**：弥补动态操纵评测基准的空白；
6. **充分的多维度实验**：包括未来帧质量、轨迹误差、消融、真实实验、计算效率、泛化能力；
7. **轻量级部署**：单卡 RTX 4090 + 22 GB 显存即可完成训练，实用性强；
8. **贡献开源**：代码、数据、基准全部公开。

---

## 八、不足与局限

1. **基准规模有限**：仅 16 个任务（8 类 × 2 速度），相比 PhysInOne 等大规模基准差距明显，作者也指出"扩展至数百任务是非平凡的"；
2. **依赖外置固定相机**：4 个固定相机是必要前提，限制了相机视角受限场景的适用性；
3. **专家轨迹依赖**：所有方法均使用脚本化专家策略收集的 100 条轨迹/任务，**模仿学习的性能上界被专家演示质量限制**；
4. **任务同质化**：8 类任务本质上均基于 RLBench 物体扩展，物体种类、外观多样性有限，可能影响跨场景迁移；
5. **真实世界任务偏少**：仅 4 个任务 × 64 次试验，对真实环境的噪声、光照、物体多样性覆盖不足；
6. **高速任务性能仍不理想**：尽管 PhysMani 领先，但高速档最高 SR 仅 46.7%（Drop to Hoop High），仍有提升空间；
7. **未见对未见物体/未见任务的零样本评测**：泛化能力仅在变化外观与速度下验证，缺少对新任务结构的零样本测试；
8. **方法局限**：将机械臂本身也视作动态环境的一部分进行建模，没有显式区分自运动（self-motion）与外部目标运动，可能影响策略的可解释性与控制精度；
9. **未对失败案例进行系统性分析**：例如哪些任务类型失败率最高、失败原因是预测不准还是策略欠拟合，缺乏深入讨论。

（完）
