# 日报 · 2026-07-12

- 生成时间：2026-07-12 17:54:09 UTC
- 当次推荐总数：32
- 精读区：21
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and output a concise summary in Chinese, within 3 sentences, based on the provided recommendation data. Let me analyze:

- Date: 2026-07-12
- Total: 32 papers
- Deep reading: 21 papers
- Quick reading: 11 papers
- Top deep reading papers (9.0/10): 
  - CoRE-VLA: Conditional Routing of Experts for scalable and robust VLA modeling
  - WSA: 3D-Centric World-Spatial-Action Model for generalizable robot control
- Top quick reading papers (8.0/10):
  - High-Fidelity One-Step Generative Visuomotor Policy
  - XS-VLA: Coarse-grained Spatial Distillation with Latent Flow Matching for lightweight robotic control
  - RoboDojo: Unified sim-and-real benchmark for generalist robot manipulation

The themes are: Vision-Language-Action models, robot control, visuomotor policies, benchmarks.

Let me craft:
1. A headline-style summary of what was done today
2. The most noteworthy direction/conclusion (1-2 items)
3. Next-step suggestion for general readers</think>

今日精选 32 篇机器人与具身智能论文，覆盖 VLA 模型、视觉运动策略及通用操作基准三大方向，其中 CoRE-VLA 与 WSA 以专家条件路由与 3D 空间-动作建模为代表，展现出高扩展性与强泛化能力。轻量化与高效推理方面，XS-VLA 与一步生成式策略值得关注，前者通过空间蒸馏+潜流匹配压缩模型，后者用递归校正实现高频一致的一步生成。普通读者可优先关注 RoboDojo 这一"仿真-真实"统一评测平台，它是判断各通用策略落地能力的关键标尺。

## 精读区
1. [CoRE-VLA: Towards Scalable and Robust Vision-Language-Action Modeling via Conditional Routing of Experts](/202607/12/2607.03693v1-core-vla-towards-scalable-and-robust-vision-language-action-modeling-via-conditional-routing-of-experts) （9.0/10）
2. [WSA$_1$: a 3D-Centric World-Spatial-Action Model for Generalizable Robot Control](/202607/12/2607.03941v1-wsa1-a-3d-centric-world-spatial-action-model-for-generalizable-robot-control) （9.0/10）
3. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v2-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies) （9.0/10）
4. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v3-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies) （9.0/10）
5. [Simple-to-Complex Structured Demonstrations for Vision-Language-Action Learning](/202607/12/2607.04591v1-simple-to-complex-structured-demonstrations-for-vision-language-action-learning) （9.0/10）
6. [CAC-VLA: Context-Gated Action Conditioning for Vision-Language-Action Models](/202607/12/2607.04816v1-cac-vla-context-gated-action-conditioning-for-vision-language-action-models) （9.0/10）
7. [DSWAM: A Dual-System World Action Foundation Model for Fine-Grained Robot Manipulation](/202607/12/2607.04927v1-dswam-a-dual-system-world-action-foundation-model-for-fine-grained-robot-manipulation) （9.0/10）
8. [InternVLA-A1.5: Unifying Understanding, Latent Foresight, and Action for Compositional Generalization](/202607/12/2607.04988v1-internvla-a15-unifying-understanding-latent-foresight-and-action-for-compositional-generalization) （9.0/10）
9. [Cortex: A Bidirectionally Aligned Embodied Agent Framework for Long-horizon Manipulation](/202607/12/2607.05377v1-cortex-a-bidirectionally-aligned-embodied-agent-framework-for-long-horizon-manipulation) （9.0/10）
10. [From Fixed to Free Cameras: Calibration-Free View-Robust Vision-Language-Action Model](/202607/12/2607.05396v1-from-fixed-to-free-cameras-calibration-free-view-robust-vision-language-action-model) （9.0/10）
11. [SIEVE: Structure-Aware Data Selection for Imitation Learning with VLA Models](/202607/12/2607.06442v1-sieve-structure-aware-data-selection-for-imitation-learning-with-vla-models) （9.0/10）
12. [Pelican-VLA 0.5: Attending Before Acting Benefits Generalization](/202607/12/2607.06655v1-pelican-vla-05-attending-before-acting-benefits-generalization) （9.0/10）
13. [Pelican-VLA 0.5: Attending Before Acting Benefits Generalization](/202607/12/2607.06655v2-pelican-vla-05-attending-before-acting-benefits-generalization) （9.0/10）
14. [NativeMEM: Native Memory Compression for Long-Horizon Robotic Manipulation](/202607/12/2607.06678v1-nativemem-native-memory-compression-for-long-horizon-robotic-manipulation) （9.0/10）
15. [PriGo: Test-Time Primitive Guidance to Diffusion and Flow Policies for Adaptive Robotic Manipulation](/202607/12/2607.07076v1-prigo-test-time-primitive-guidance-to-diffusion-and-flow-policies-for-adaptive-robotic-manipulation) （9.0/10）
16. [LEEVLA: Seeing What Matters in Latent Environment Evolution for Vision-Language-Action](/202607/12/2607.08182v1-leevla-seeing-what-matters-in-latent-environment-evolution-for-vision-language-action) （9.0/10）
17. [TFP: Temporally Conditioned Memory-Fusion Policies for Visuomotor Learning](/202607/12/2607.08283v1-tfp-temporally-conditioned-memory-fusion-policies-for-visuomotor-learning) （9.0/10）
18. [SkillPlug: Unsupervised Skill Mining for Few-Shot Adaptation in Robotic Manipulation](/202607/12/2607.08354v1-skillplug-unsupervised-skill-mining-for-few-shot-adaptation-in-robotic-manipulation) （9.0/10）
19. [Harness VLA: Steering Frozen VLAs into Reliable Manipulation Primitives via Memory-Guided Agents](/202607/12/2607.08448v1-harness-vla-steering-frozen-vlas-into-reliable-manipulation-primitives-via-memory-guided-agents) （9.0/10）
20. [FabriVLA: A Lightweight Vision-Language-Action Model for Precise Multi-Task Manipulation](/202607/12/2607.08575v1-fabrivla-a-lightweight-vision-language-action-model-for-precise-multi-task-manipulation) （9.0/10）
21. [Native Video-Action Pretraining for Generalizable Robot Control](/202607/12/2607.08639v1-native-video-action-pretraining-for-generalizable-robot-control) （9.0/10）

## 速读区
1. [High-Fidelity One-Step Generative Visuomotor Policy via Recursive Correction, Frequency Consistency, and Contrastive Flow Matching](/202607/12/2607.03865v1-high-fidelity-one-step-generative-visuomotor-policy-via-recursive-correction-frequency-consistency-and-contrastive-flow-matching) （8.0/10）
2. [XS-VLA: Coupling Coarse-grained Spatial Distillation with Latent Flow Matching for Lightweight Robotic Control](/202607/12/2607.04171v1-xs-vla-coupling-coarse-grained-spatial-distillation-with-latent-flow-matching-for-lightweight-robotic-control) （8.0/10）
3. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v1-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies) （8.0/10）
4. [VLA Grounder: Language-Conditioning Space Optimization for Black-Box VLA Models](/202607/12/2607.04517v1-vla-grounder-language-conditioning-space-optimization-for-black-box-vla-models) （8.0/10）
5. [ObjRetarget: An Object-Aware Motion Retargeting Framework with Anthropomorphic Arm Constraints and Polyhedral Hand Modeling](/202607/12/2607.03828v1-objretarget-an-object-aware-motion-retargeting-framework-with-anthropomorphic-arm-constraints-and-polyhedral-hand-modeling) （7.0/10）
6. [SoftVTBench: A Safety-Aware Visuo-Tactile Benchmark for Physically Constrained Robotic Manipulation of Deformable Objects](/202607/12/2607.04234v1-softvtbench-a-safety-aware-visuo-tactile-benchmark-for-physically-constrained-robotic-manipulation-of-deformable-objects) （7.0/10）
7. [HALO-WA: Hybrid-Attention Latent-Guided Online Reinforcement Learning for World-Action Models](/202607/12/2607.04265v1-halo-wa-hybrid-attention-latent-guided-online-reinforcement-learning-for-world-action-models) （7.0/10）
8. [ACE-Brain-0.5: A Unified Embodied Foundational Model for Physical Agentic AI](/202607/12/2607.04426v1-ace-brain-05-a-unified-embodied-foundational-model-for-physical-agentic-ai) （7.0/10）
9. [OmniTacTune: Policy-Agnostic Real-World RL for Tactile Residual Adaptation of Visual Policies](/202607/12/2607.03723v1-omnitactune-policy-agnostic-real-world-rl-for-tactile-residual-adaptation-of-visual-policies) （6.0/10）
10. [ACE: Agentic Control for Embodied Manipulation via Zero-shot Workflow Reasoning](/202607/12/2607.04162v1-ace-agentic-control-for-embodied-manipulation-via-zero-shot-workflow-reasoning) （6.0/10）
11. [TouchWorld: A Predictive and Reactive Tactile Foundation Model for Dexterous Manipulation](/202607/12/2607.07287v1-touchworld-a-predictive-and-reactive-tactile-foundation-model-for-dexterous-manipulation) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
