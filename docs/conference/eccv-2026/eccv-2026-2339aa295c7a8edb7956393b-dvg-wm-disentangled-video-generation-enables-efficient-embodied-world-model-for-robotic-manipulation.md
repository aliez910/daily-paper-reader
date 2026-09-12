---
title: "DVG-WM: Disentangled Video Generation Enables Efficient Embodied World Model for Robotic Manipulation"
title_zh: "DVG-WM:解耦视频生成实现高效的机器人操作具身世界模型"
authors: "Ziyu Shan, Zhenyu Wu, Xiaofeng Wang, Zheng Zhu, Ziwei Wang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/7120.pdf"
tags: ["query:rob-il"]
score: 5.0
evidence: 面向机器人操作的具身世界模型
tldr: "基于视频的具身世界模型通过预测未来状态支持机器人操作,但面临动态推理与视觉合成纠缠的根本难题。导致迭代规划推理缓慢或预测过于粗糙而丢失接触细节。本文提出DVG-WM解耦视频生成框架,显式分离动态学习与视觉合成。在初始观测条件下,该方法实现高效世界建模,在保持接触细节的同时提升推理速度。该工作推动基于模型的机器人操作规划研究。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 565, \"height\": 1319}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 1584, \"height\": 721}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-010.webp\", \"caption\": \"\", \"page\": 5, \"index\": 10, \"width\": 1919, \"height\": 865}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-011.webp\", \"caption\": \"\", \"page\": 5, \"index\": 11, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 741, \"height\": 383}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-013.webp\", \"caption\": \"\", \"page\": 8, \"index\": 13, \"width\": 484, \"height\": 464}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-014.webp\", \"caption\": \"\", \"page\": 10, \"index\": 14, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-015.webp\", \"caption\": \"\", \"page\": 10, \"index\": 15, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-016.webp\", \"caption\": \"\", \"page\": 10, \"index\": 16, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-017.webp\", \"caption\": \"\", \"page\": 10, \"index\": 17, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-018.webp\", \"caption\": \"\", \"page\": 10, \"index\": 18, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-019.webp\", \"caption\": \"\", \"page\": 10, \"index\": 19, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-020.webp\", \"caption\": \"\", \"page\": 11, \"index\": 20, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-021.webp\", \"caption\": \"\", \"page\": 11, \"index\": 21, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-022.webp\", \"caption\": \"\", \"page\": 11, \"index\": 22, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-023.webp\", \"caption\": \"\", \"page\": 11, \"index\": 23, \"width\": 720, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-024.webp\", \"caption\": \"\", \"page\": 12, \"index\": 24, \"width\": 1536, \"height\": 1024}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-025.webp\", \"caption\": \"\", \"page\": 14, \"index\": 25, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-026.webp\", \"caption\": \"\", \"page\": 14, \"index\": 26, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-027.webp\", \"caption\": \"\", \"page\": 14, \"index\": 27, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-2339aa295c7a8edb7956393b/fig-028.webp\", \"caption\": \"\", \"page\": 14, \"index\": 28, \"width\": 640, \"height\": 480}]"
motivation: "现有视频世界模型在动态推理与高分辨率视觉合成之间存在纠缠,影响机器人操作规划效率。"
method: "提出解耦视频生成世界模型,将动态学习与视觉合成显式分离以兼顾速度与细节。"
result: "在保持接触丰富细节的同时显著提升迭代规划推理速度,优于现有视频世界模型。"
conclusion: "为基于模型的机器人操作规划提供高效世界建模方案,推动视觉预测与控制结合的研究。"
---

## Abstract
Video-based embodied world models provide an appealingsubstrate for robotic manipulation by predicting future states, yet cur-rent approaches remain limited by a fundamental entanglement: accu-rately modeling dynamics typically requires low-level temporal reason-ing, while producing high-resolution frames demands expansive visualsynthesis according to high-level semantics. This entanglement results inslow inference speed for iterative planning or too coarse predictions toretain contact-rich details. To solve this dilemma, we present Disentan-gled Video Generation World Model (DVG-WM), an efficient frameworkthat explicitly decomposes world modeling into dynamics learn-ing and visual synthesis. Conditioned on an initial observation anda language instruction, our model first generates a plausible sequence ofintermediate visual states to preview the physical interaction and refinesthem to obtain high-fidelity videos. Furthermore, an efficient cascadingmechanism is proposed, where DVG-WM leverages flow matching to di-rectly map the dynamics to video latents, and introduces a latent degra-dation mechanism to enable the capability of regenerating contact-richdetails. Experiments on LIBERO and real-world platforms demonstrateimproved video quality with up to 3.97 × acceleration, validating thatdisentangled video generation can be an efficient embodied world modelfor robotic manipulation.

---

## 论文详细总结（自动生成）

<think>The user wants me to write a detailed Chinese summary of the paper following a specific structure with 8 points. Let me analyze the paper carefully and produce a comprehensive summary.

The paper is about DVG-WM (Disentangled Video Generation World Model), which addresses the problem of entanglement between dynamics modeling and high-resolution visual synthesis in video-based embodied world models for robotic manipulation.

Let me organize my summary according to the 8 required sections.</think>

# DVG-WM 论文总结

## 1. 核心问题与研究动机

- **研究背景**：基于视频的具身世界模型（embodied world model）通过预测未来状态为机器人操作提供基础，可用于迭代规划、目标条件策略学习等任务。
- **核心矛盾**：当前方法存在**动力学建模与高分辨率视觉合成的根本性纠缠**：
  - 精确的动力学建模需要低层级时间推理（关注接触、滑动、遮挡等物理交互模式），这些并不一定需要高分辨率或丰富纹理；
  - 高分辨率帧的生成需要高层级语义和丰富纹理信息，计算开销巨大。
- **导致问题**：单一整体式视频生成器在高分辨率下推理速度慢，难以满足实际机器人迭代规划中需要反复调用的需求；而低分辨率预测又会丢失接触细节。
- **研究目标**：解耦动态学习与视觉合成，在各自最优分辨率下学习，从而兼顾推理效率与接触细节保真度。

## 2. 方法论

### 2.1 整体框架
- **两阶段管线（Preview-Refine）**：
  - **Preview 阶段**：在低分辨率（256×384）下生成动力学潜变量 $z^{lr}$，快速预览物理交互过程；
  - **Refinement 阶段**：将低分辨率动力学映射到高分辨率（480×720）视频潜变量 $z^{hr}$，恢复细节。
- **形式化**：给定初始观测 $x_0$ 和语言指令 $c$，学习 $p(x_{1:N} | x_0, c)$，分解为：
  - $g_p(z^{lr} | x_0^d, c)$（preview）
  - $g_r(z^{hr} | z^{lr}, x_0, c)$（refine）

### 2.2 低分辨率 Preview 阶段
- 以 **CogVideoX-5B** 为视频生成骨干；
- 丢弃可学习位置编码，使用 **3D RoPE** 支持可变输出分辨率；
- 采用 **LoRA（rank=128）** 应用于注意力层、FFN 和层归一化，低成本适配到低分辨率具身数据。

### 2.3 高分辨率 Refinement 阶段
- 采用更小的 **CogVideoX-2B**（观察到操作场景结构化、状态转换平缓）。
- **关键创新 1：Flow Matching 级联机制**
  - 直接在潜空间建立从 $\tilde{z}^{lr}$（上采样后的低分辨率潜变量）到 $z^{hr}$ 的直线 ODE 路径：
    $$z_\tau = (1-\tau)\tilde{z}^{lr} + \tau z^{hr}, \quad \tau \sim U(0,1)$$
  - 速度场目标：$u^\star(z_\tau, \tau) = z^{hr} - \tilde{z}^{lr}$
  - 训练损失：
    $$\mathcal{L}_{FM} = \mathbb{E}\left[\| v_\theta(z_\tau, \tau | z^{lr}, x_0, c) - u^\star(z_\tau, \tau) \|^2 \right]$$
  - 推理时仅需 **K=4 步**确定性流过程即可获得高分辨率潜变量。
- **关键创新 2：Latent Degradation 机制**
  - 与传统像素级退化不同，对潜变量加扰动再解码形成训练对；
  - 避免 shortcut upscaling，使模型必须重建接触相关结构（夹爪-物体交互区域），而不是简单像素放大。

### 2.4 动作生成模块（Action Expert）
- 在无可用机器人状态时，使用**视觉条件 Diffusion Policy (DP)** 作为动作专家；
- 将预测帧编码为条件 $h_t$，通过 DDPM 反向过程生成动作序列；
- 训练策略：先单独训练世界模型，再联合微调 action expert 与世界模型（仅用 $\mathcal{L}_{DP}$）。

## 3. 实验设计

### 3.1 数据集
- **LIBERO 仿真数据集**：约 5K 条轨迹，按 8:2 划分训练/测试；
- **真实世界自采数据集**：7K 条轨迹，覆盖 Galaxea A1 与 UR7e 机械臂平台，配备 RealSense L515 RGBD 相机。

### 3.2 评估指标
- **视频质量**：PSNR、SSIM、LPIPS、FVD；
- **目标级准确率（Object Accuracy）**：10% 轨迹人工核查操作目标正确率；
- **Embodiment 区域 Mask-IoU**（用 Grounded SAM 提取）；
- **真实世界任务成功率**。

### 3.3 对比基线
- **视频质量对比**：CogVideoX-5B、Wan2.1-14B、LongScape、LVP-14B；
- **真实世界动作规划对比**：CogVideoX-5B 世界模型 + Diffusion Policy；
- **9 个真实任务**：move banana、pick&place bread、sweep rubbish、stack cube、adapter insertion、push cube、open drawer、assemble gears、make a toast。

### 3.4 真实世界评估协议
- 每个任务 50 条演示，每任务滚动 20×4=80 次（4 种桌面布局/位置/任务长度变体），报告平均成功率与标准差。

## 4. 资源与算力

- **Preview 阶段**：单卡 **A100-80G**，batch size=4，训练 **10,000 次迭代**，AdamW（β₁=0.9, β₂=0.95, weight decay=1e-4, grad clip=0.1）；
- **Refinement 阶段**：**8 张 A100-80G** GPU，batch size=6，训练 **10 个 epoch**，约 24 小时；
- **视频长度**：49 帧，720p；
- 总训练成本较高，但通过 LoRA 和级联设计控制了大部分训练开销。

## 5. 实验数量与充分性

- **仿真实验**：
  - LIBERO 上与 4 个基线的定量对比（PSNR/SSIM/LPIPS/FVD/Object Accuracy）；
  - 效率对比表（推理时长）；
  - 定性可视化对比；
- **消融研究**：
  - LoRA 微调步数对 preview 阶段的影响（step 0/3K/4K/5K）；
  - 组件分析（像素退化 vs 潜变量退化、朴素级联 vs Flow Matching、移除 preview、移除 refine、降低 preview 分辨率）；
  - Refinement 步数 K 的消融（K=1, 2, 4, 8）；
- **真实世界实验**：
  - 9 个任务 ×2 平台，每任务 80 次 rollout；
  - 视频质量对比（PSNR/SSIM/LPIPS/FVD/Mask-IoU）；
  - 任务成功率统计（CogVideoX vs DVG-WM）；
- **充分性评价**：实验覆盖了定量/定性、消融、仿真/真实、效率/质量多个维度，对比方法较新且多样，公平性较好；但 Object Accuracy 是人工核查 10% 样本，存在主观性。

## 6. 主要结论与发现

- **视频质量**：在 LIBERO 上，DVG-WM 在 PSNR（20.019）、LPIPS（0.120）、FVD（152.36）、Object Accuracy（**89%**）上均优于 CogVideoX-5B、Wan2.1-14B、LVP-14B；SSIM 仅略低于 LongScape。
- **推理效率**：DVG-WM 仅需 88.7 秒生成视频，相比 LVP-14B（354.2 秒）实现 **3.97× 加速**，相比 CogVideoX-5B（236.8 秒）约 2.67× 加速。
- **真实世界表现**：
  - 视频质量各项指标均优于 CogVideoX；
  - Mask-IoU 提升（0.54→0.57），表明 embodiment 区域感知更好；
  - **任务平均成功率从 34.0% 提升至 62.2%（+28.2%）**，在 adapter insertion、assemble gears、make a toast 等接触密集、长时间跨度任务上提升尤其明显。
- **核心结论**：解耦的视频生成（动力学 + 视觉合成分离）可作为高效具身世界模型的实用基础。

## 7. 优点与亮点

- **问题洞察深刻**：明确指出动力学建模与高分辨率视觉合成的本质矛盾，并提出自然的解耦解决思路；
- **方法创新突出**：
  - Flow Matching 级联机制显著减少 refine 阶段 NFEs（4 步即可）；
  - Latent Degradation 机制有效避免 shortcut upscaling，强制重建接触细节；
- **架构灵活**：Preview 与 Refine 阶段可分别选用不同大小的骨干模型（CogVideoX-5B + CogVideoX-2B），平衡性能与效率；
- **实验全面**：覆盖仿真与真实世界、定量与定性、消融与对比，且真实世界任务多样（9 个任务 ×2 平台），具备较强说服力；
- **下游适配自然**：通过 vision-only Diffusion Policy 即可将世界模型用于动作规划，无需机器人状态输入。

## 8. 不足与局限

- **依赖强预训练模型**：依赖 CogVideoX 系列，预训练权重偏向通用视频分布，对具身场景的迁移仍需要 LoRA 微调；
- **语言条件粒度有限**：当前仅以单条语言指令作为高层目标，无法表达多阶段子目标或交互式纠正指令；
- **评测数据规模有限**：
  - 真实世界自采数据 7K 条轨迹，9 个任务每任务仅 50 条演示，模型在更复杂或长尾任务上的泛化性未充分验证；
  - Object Accuracy 仅人工核查 10% 样本，存在主观性和统计误差；
- **未与其他先进世界模型直接对比动作规划**：真实世界动作规划实验仅与 CogVideoX 基线对比，未纳入 LongScape、WorldVLA、Genie Envisioner 等近期方法的真实部署结果；
- **推理加速有限定**：Refinement 步数 K=4 仍有可优化的余地，且整体 88.7 秒的推理延迟对毫秒级闭环控制仍较慢；
- **安全性与失败模式未充分讨论**：未分析世界模型预测错误（如幻觉物体/错误目标）时的风险传播；
- **Sim-to-Real 差距**：仿真训练的模型在真实场景中虽有效，但评估的 9 个任务相对结构化，未覆盖更杂乱的家庭/工业环境。

（完）
