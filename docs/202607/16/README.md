# 日报 · 2026-07-16

- 生成时间：2026-07-16 18:09:17 UTC
- 当次推荐总数：33
- 精读区：22
- 速读区：11

## 今日简报（AI）
<think>The user wants a Chinese daily report summary based on the given data. Let me analyze:

- Date: 2026-07-16
- Total: 33 papers
- Deep read: 22 papers
- Quick read: 11 papers
- Top deep reads: Two papers rated 9.0/10 about VLA models for 3D geometry/dynamics manipulation and a review on VLA for aerial robotics and bimanual manipulation
- Top quick reads: Three papers rated 8.0/10 about world models for teleoperation, 4D embodied world models, and memory compression for manipulation

The theme is clearly VLA (Vision-Language-Action) models, world models, and robotic manipulation.

Let me write 3 lines:
1. Title-suitable summary
2. Best 1-2 directions/conclusions
3. Next step suggestion for general readers</think>

今日聚焦具身智能前沿，共筛读 33 篇论文（精读 22 篇、速读 11 篇），核心围绕 VLA 模型三维感知与机器人操作两大主线展开。值得重点关注的方向：一是 VLA 模型正从 2D 视觉向 3D 几何与动力学建模升级（以 Lift3D-VLA 为代表，9.0 分），同时 VLA 在无人机遥操作与双臂操作等复杂场景的综述（9.0 分）标志着该范式走向系统化梳理；二是世界模型与长程记忆压缩（如 RynnWorld 系列与 NativeMEM，均 8.0 分）正在成为突破长时序操作任务的关键路径。建议读者若对机器人或大模型应用感兴趣，可优先从 VLA 综述入手建立全景认知，再选择三维感知或世界模型任一方向深入追踪。

## 精读区
1. [Lift3D-VLA: Lifting VLA Models to 3D Geometry and Dynamics-Aware Manipulation](/202607/16/2607.06564v1-lift3d-vla-lifting-vla-models-to-3d-geometry-and-dynamics-aware-manipulation) （9.0/10）
2. [Vision Language Action (VLA) Models for Unmanned Aerial Robotics and Bimanual Manipulation: A Review](/202607/16/2607.06706v1-vision-language-action-vla-models-for-unmanned-aerial-robotics-and-bimanual-manipulation-a-review) （9.0/10）
3. [WAM-TTT: Steering World-Action Models by Watching Human Play at Test Time](/202607/16/2607.06988v1-wam-ttt-steering-world-action-models-by-watching-human-play-at-test-time) （9.0/10）
4. [PriGo: Test-Time Primitive Guidance to Diffusion and Flow Policies for Adaptive Robotic Manipulation](/202607/16/2607.07076v1-prigo-test-time-primitive-guidance-to-diffusion-and-flow-policies-for-adaptive-robotic-manipulation) （9.0/10）
5. [Dual Latent Memory in Vision-Language-Action Models for Robotic Manipulation](/202607/16/2607.07608v1-dual-latent-memory-in-vision-language-action-models-for-robotic-manipulation) （9.0/10）
6. [LEEVLA: Seeing What Matters in Latent Environment Evolution for Vision-Language-Action](/202607/16/2607.08182v1-leevla-seeing-what-matters-in-latent-environment-evolution-for-vision-language-action) （9.0/10）
7. [TFP: Temporally Conditioned Memory-Fusion Policies for Visuomotor Learning](/202607/16/2607.08283v2-tfp-temporally-conditioned-memory-fusion-policies-for-visuomotor-learning) （9.0/10）
8. [SkillPlug: Unsupervised Skill Mining for Few-Shot Adaptation in Robotic Manipulation](/202607/16/2607.08354v1-skillplug-unsupervised-skill-mining-for-few-shot-adaptation-in-robotic-manipulation) （9.0/10）
9. [Harness VLA: Steering Frozen VLAs into Reliable Manipulation Primitives via Memory-Guided Agents](/202607/16/2607.08448v3-harness-vla-steering-frozen-vlas-into-reliable-manipulation-primitives-via-memory-guided-agents) （9.0/10）
10. [FabriVLA: A Lightweight Vision-Language-Action Model for Precise Multi-Task Manipulation](/202607/16/2607.08575v2-fabrivla-a-lightweight-vision-language-action-model-for-precise-multi-task-manipulation) （9.0/10）
11. [Native Video-Action Pretraining for Generalizable Robot Control](/202607/16/2607.08639v1-native-video-action-pretraining-for-generalizable-robot-control) （9.0/10）
12. [CLAP: Direct VLM-to-VLA Adaptation via Language-Action Grounding](/202607/16/2607.08974v1-clap-direct-vlm-to-vla-adaptation-via-language-action-grounding) （9.0/10）
13. [TS-Mask VLA: 2D Temporal-Spatial Masking for Vision-Language-Action Model with Effective Bridging](/202607/16/2607.09818v1-ts-mask-vla-2d-temporal-spatial-masking-for-vision-language-action-model-with-effective-bridging) （9.0/10）
14. [More Structure, Not More Capacity: Object-Centric Representations for Visuomotor Imitation Learning](/202607/16/2607.09825v1-more-structure-not-more-capacity-object-centric-representations-for-visuomotor-imitation-learning) （9.0/10）
15. [SUREFlow: State-space Uncertainty-aware REsidual Flow Matching for Robust Robot Manipulation](/202607/16/2607.10504v1-sureflow-state-space-uncertainty-aware-residual-flow-matching-for-robust-robot-manipulation) （9.0/10）
16. [Action Map Policy: Learning 3D Closed-loop Manipulation via Pixel Classification](/202607/16/2607.10706v1-action-map-policy-learning-3d-closed-loop-manipulation-via-pixel-classification) （9.0/10）
17. [SegDiff: Segmented Trajectory Diffusion for Consistent and Adaptive Robot Manipulation](/202607/16/2607.11027v1-segdiff-segmented-trajectory-diffusion-for-consistent-and-adaptive-robot-manipulation) （9.0/10）
18. [Pix2Act: Image-Space Manipulation Policies with Equivariant Augmentation](/202607/16/2607.11167v1-pix2act-image-space-manipulation-policies-with-equivariant-augmentation) （9.0/10）
19. [VistaVLA: Geometry- and Semantic-Aware 3D Gaussian-Grounded VLA for Robotic Manipulation](/202607/16/2607.12356v1-vistavla-geometry--and-semantic-aware-3d-gaussian-grounded-vla-for-robotic-manipulation) （9.0/10）
20. [Generalizable VLA Finetuning via Representation Anchoring and Language-Action Alignment](/202607/16/2607.13429v1-generalizable-vla-finetuning-via-representation-anchoring-and-language-action-alignment) （9.0/10）
21. [GigaWorld-Policy-0.5: A Faster and Stronger WAM Empowered by AutoResearch](/202607/16/2607.13960v1-gigaworld-policy-05-a-faster-and-stronger-wam-empowered-by-autoresearch) （9.0/10）
22. [Industrial Dexterity Benchmark: A Hardware-Software Benchmarking Platform for Industrial Dexterous Manipulation](/202607/16/2607.14021v1-industrial-dexterity-benchmark-a-hardware-software-benchmarking-platform-for-industrial-dexterous-manipulation) （9.0/10）

## 速读区
1. [RynnWorld-Teleop: An Action-Conditioned World Model for Digital Teleoperation](/202607/16/2607.06558v1-rynnworld-teleop-an-action-conditioned-world-model-for-digital-teleoperation) （8.0/10）
2. [RynnWorld-4D: 4D Embodied World Models for Robotic Manipulation](/202607/16/2607.06559v1-rynnworld-4d-4d-embodied-world-models-for-robotic-manipulation) （8.0/10）
3. [NativeMEM: Native Memory Compression for Long-Horizon Robotic Manipulation](/202607/16/2607.06678v1-nativemem-native-memory-compression-for-long-horizon-robotic-manipulation) （8.0/10）
4. [SPECTRA: Context-Conditioned Spectral Movement Primitives for Robot Skill Generalization](/202607/16/2607.06978v1-spectra-context-conditioned-spectral-movement-primitives-for-robot-skill-generalization) （8.0/10）
5. [GeoProp: Grounding Robot State in Vision for Generalist Manipulation](/202607/16/2607.07101v1-geoprop-grounding-robot-state-in-vision-for-generalist-manipulation) （7.0/10）
6. [Compositional Motion Generation from Demonstration with Object-Centric Neural Fields](/202607/16/2607.07129v1-compositional-motion-generation-from-demonstration-with-object-centric-neural-fields) （7.0/10）
7. [Feedback Manipulation Regularization: Enabling Offline Agent Alignment for Imitation Learning](/202607/16/2607.07859v1-feedback-manipulation-regularization-enabling-offline-agent-alignment-for-imitation-learning) （7.0/10）
8. [ContactMimic: Humanoid Object Interaction via Contact Control](/202607/16/2607.08742v1-contactmimic-humanoid-object-interaction-via-contact-control) （7.0/10）
9. [TouchWorld: A Predictive and Reactive Tactile Foundation Model for Dexterous Manipulation](/202607/16/2607.07287v1-touchworld-a-predictive-and-reactive-tactile-foundation-model-for-dexterous-manipulation) （6.0/10）
10. [Multi-Agent Robotic Control with Onboard Vision-Language Models](/202607/16/2607.07403v1-multi-agent-robotic-control-with-onboard-vision-language-models) （6.0/10）
11. [Smooth Operator: A Real-Time Sampling-Based Algorithm for Kinematic Hand Retargeting](/202607/16/2607.07491v2-smooth-operator-a-real-time-sampling-based-algorithm-for-kinematic-hand-retargeting) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
