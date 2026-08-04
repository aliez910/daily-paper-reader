# 日报 · 2026-08-04

- 最近生成时间：2026-08-04 18:39:24 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：30
- 精读区：19
- 速读区：11

## 今日简报（AI）
<think>The user wants me to create a daily report summary in Chinese based on the given paper recommendations. I need to output 3 lines of text without Markdown headers or JSON. Let me analyze the data:

- Date: 2026-08-04
- Status: Success
- Total: 30 papers
- Deep reads: 19
- Quick reads: 11
- Top deep reads: WorldDiT (9.0/10) and FutureRTC (9.0/10) - both about world models and real-time robot execution
- Top quick reads: LeapBot-WA (world-anchor action models), PAC-DP (PAC-Bayesian diffusion policy), CoTinyVLA (chain-of-thought distillation for VLA models)

Theme: World models + robot action generation, diffusion policies, VLA models

Let me craft 3 concise Chinese sentences:
1. A headline-style summary
2. Key directions/conclusions worth noting
3. Next-step suggestion for general readers</think>

今日筛选 30 篇论文并完成 19 篇精读，主线聚焦"世界模型+机器人动作生成"在实时推理与策略学习方向的最新进展。
最值得关注的两条线：一是 WorldDiT 等统一扩散架构把世界建模与动作生成打通，FutureRTC 则用预测式条件分块把延迟压到实时级；二是 PAC-DP、CoTinyVLA 表明贝叶斯扩散策略与小模型思维链蒸馏正在让策略学习更稳、更轻。
建议读者先读 WorldDiT 与 FutureRTC 的方法图，再对照 LeRobot 等开源实现跑通一个最小 demo，亲身感受"世界模型驱动的具身决策"从论文到落地的差距。

## 精读区
1. [WorldDiT: A Unified Diffusion Architecture for World and Action Modeling](/202608/04/2607.23909v2-worlddit-a-unified-diffusion-architecture-for-world-and-action-modeling) （9.0/10）
2. [FutureRTC: Real-Time Robot Execution with Anticipatory-Conditioned Action Chunking](/202608/04/2607.24008v1-futurertc-real-time-robot-execution-with-anticipatory-conditioned-action-chunking) （9.0/10）
3. [DeVA: Decoupled Video-Action Model with physical guidance for robot policy learning](/202608/04/2607.24159v1-deva-decoupled-video-action-model-with-physical-guidance-for-robot-policy-learning) （9.0/10）
4. [ArmnetBench v0.1: Parallel Real-World Evaluation of Manipulation Policies on a Low-Cost Arm Farm](/202608/04/2607.24481v1-armnetbench-v01-parallel-real-world-evaluation-of-manipulation-policies-on-a-low-cost-arm-farm) （9.0/10）
5. [Decompose and Reorganize: Planning with Primitives and Visuomotor Policies Learned from Demonstrations](/202608/04/2607.25397v1-decompose-and-reorganize-planning-with-primitives-and-visuomotor-policies-learned-from-demonstrations) （9.0/10）
6. [Tri-Manual Visuomotor Imitation Learning of Robot Policies](/202608/04/2607.25731v3-tri-manual-visuomotor-imitation-learning-of-robot-policies) （9.0/10）
7. [SAM3D-Guided Object-Centric Representation Alignment for Vision-Language-Action Models](/202608/04/2607.25912v1-sam3d-guided-object-centric-representation-alignment-for-vision-language-action-models) （9.0/10）
8. [Explicit Kinematic Guidance from Analytic Concepts for Vision-Language-Action Models](/202608/04/2607.26513v1-explicit-kinematic-guidance-from-analytic-concepts-for-vision-language-action-models) （9.0/10）
9. [TurboVLA: Real-Time Vision-Language-Action Model at 32 Hz on an RTX 4090 with <1 GB VRAM](/202608/04/2607.27205v1-turbovla-real-time-vision-language-action-model-at-32-hz-on-an-rtx-4090-with-1-gb-vram) （9.0/10）
10. [Cross-Embodiment Transfer via Behavior-Aligned Representations](/202608/04/2607.27549v1-cross-embodiment-transfer-via-behavior-aligned-representations) （9.0/10）
11. [RedFlow: Redirect Failure into Action-Level Corrections for Flow-matching VLA Policy](/202608/04/2607.27782v1-redflow-redirect-failure-into-action-level-corrections-for-flow-matching-vla-policy) （9.0/10）
12. [RayViT: Ray-Conditioned Visual Representations for Viewpoint-Robust Imitation Learning](/202608/04/2607.29622v1-rayvit-ray-conditioned-visual-representations-for-viewpoint-robust-imitation-learning) （9.0/10）
13. [SelfWAM: A Self-Grounded Unified World Action Model for Fast Robot Control](/202608/04/2608.00725v1-selfwam-a-self-grounded-unified-world-action-model-for-fast-robot-control) （9.0/10）
14. [DreamTrajectory: Trajectory-Guided Action Generation with World Model Alignment for Mobile Manipulation](/202608/04/2608.01381v1-dreamtrajectory-trajectory-guided-action-generation-with-world-model-alignment-for-mobile-manipulation) （9.0/10）
15. [DynamicManip: Enabling Dynamic Manipulation from a Single Static Demonstration](/202608/04/2608.01452v1-dynamicmanip-enabling-dynamic-manipulation-from-a-single-static-demonstration) （9.0/10）
16. [AffordTrajDP: Dynamic Affordance-Guided Visuomotor Policy Learning for Robotic Manipulation](/202608/04/2608.01603v1-affordtrajdp-dynamic-affordance-guided-visuomotor-policy-learning-for-robotic-manipulation) （9.0/10）
17. [Multi-View Unified Camera Fields: Geometry-Shaped Action-Facing Representations for RGB-Only Multi-Camera VLA Policies](/202608/04/2608.01826v1-multi-view-unified-camera-fields-geometry-shaped-action-facing-representations-for-rgb-only-multi-camera-vla-policies) （9.0/10）
18. [Look Where It Matters: Adaptive Visual Refinement for Vision-Language-Action Models](/202608/04/2608.02197v1-look-where-it-matters-adaptive-visual-refinement-for-vision-language-action-models) （9.0/10）
19. [ChainVLA: Chaining Vision-Language-Action Queries through a Unified Execution State for Long-Horizon Manipulation](/202608/04/2608.02326v1-chainvla-chaining-vision-language-action-queries-through-a-unified-execution-state-for-long-horizon-manipulation) （9.0/10）

## 速读区
1. [LeapBot-WA: World-Anchor Action Models via Predictive Latent Alignments](/202608/04/2607.23969v2-leapbot-wa-world-anchor-action-models-via-predictive-latent-alignments) （8.0/10）
2. [PAC-DP: PAC-Bayesian Diffusion Policy Learning](/202608/04/2607.24296v1-pac-dp-pac-bayesian-diffusion-policy-learning) （8.0/10）
3. [CoTinyVLA: Chain-of-Thought Distillation for a Sub-Billion-Parameter Vision-Language-Action Model](/202608/04/2607.25487v1-cotinyvla-chain-of-thought-distillation-for-a-sub-billion-parameter-vision-language-action-model) （8.0/10）
4. [A Causality-aware Infer-diagnose-refine Framework for Test-time Modality Adaptation in VLA Models](/202608/04/2607.25516v1-a-causality-aware-infer-diagnose-refine-framework-for-test-time-modality-adaptation-in-vla-models) （8.0/10）
5. [A Motion-Aware Vector Quantization Framework with Centroid Reuse for Efficient VLA Inference](/202608/04/2607.24148v1-a-motion-aware-vector-quantization-framework-with-centroid-reuse-for-efficient-vla-inference) （7.0/10）
6. [KAI: A Kinematic-Aware Interface for Data-Efficient Articulated Object Manipulation](/202608/04/2607.24493v1-kai-a-kinematic-aware-interface-for-data-efficient-articulated-object-manipulation) （7.0/10）
7. [RLMM-Flow: A Flow-based Mobile Manipulation Framework with Latent-Space Reinforcement Learning](/202608/04/2607.26460v1-rlmm-flow-a-flow-based-mobile-manipulation-framework-with-latent-space-reinforcement-learning) （7.0/10）
8. [Practice Makes Policies: Bootstrapping and Consolidating Robotic Capabilities from Zero Human Demonstrations](/202608/04/2607.26809v1-practice-makes-policies-bootstrapping-and-consolidating-robotic-capabilities-from-zero-human-demonstrations) （7.0/10）
9. [Data Pyramid for Embodied Manipulation](/202608/04/2607.24744v1-data-pyramid-for-embodied-manipulation) （6.0/10）
10. [DexDirect: Direct Kinesthetic Arm Guidance for Efficient Dexterous Demonstration Collection](/202608/04/2607.27784v1-dexdirect-direct-kinesthetic-arm-guidance-for-efficient-dexterous-demonstration-collection) （6.0/10）
11. [EgoGenesis: Egocentric World-Action Modeling with Online Anchored Projective Memory and Action-3D RoPE](/202608/04/2607.28243v1-egogenesis-egocentric-world-action-modeling-with-online-anchored-projective-memory-and-action-3d-rope) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
