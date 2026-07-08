# 日报 · 2026-07-08

- 生成时间：2026-07-08 18:38:19 UTC
- 当次推荐总数：28
- 精读区：17
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and produce 3 concise, attractive Chinese summaries based on the given recommendation data.

Let me analyze the data:
- Date: 2026-07-08
- Status: Success
- Total: 28 papers
- Deep read: 17 papers
- Speed read: 11 papers
- Deep read list (with scores): Two papers on Vision-Language-Action (VLA) agents - MIRTH (mutual-info reasoning with temporal hubs) and 3D HAMSTER (3D trajectory guidance in hierarchical VLA models), both 9.0/10
- Speed read list (with scores): Three papers on sim-to-real transfer, test-time scaling, and visuomotor policy learning, all 8.0/10

Let me write three sentences:
1) A catchy headline-style summary
2) The most noteworthy 1-2 directions/conclusions
3) A next-step suggestion for general readers

Topic focus: Robot learning / VLA (Vision-Language-Action) models, policy learning, sim-to-real.

Let me draft:

1) 今天共筛选 28 篇论文，精读 17 篇、速读 11 篇，整体聚焦视觉-语言-动作（VLA）智能体与机器人策略学习方向。

2) 最值得看的是 VLA 高层规划与底层控制融合的趋势——MIRTH 用互信息+时间枢纽做长程推理，3D HAMSTER 用 3D 轨迹引导桥接分层规划；结合 sim-to-real、测试时自适应推理等实操方案，机器人从"理解指令"走向"长时段可靠执行"。

3) 建议读者优先精读 MIRTH 与 3D HAMSTER 两篇，对想动手做 VLA 的同学可重点参考 ChronoFlow 的时序建模与 ELASTIC 的测试时推理扩展思路。

Let me make it more punchy and fit within 3 sentences. The constraint says "3 句以内" so I should keep it tight. Let me refine.

1) 一句概括：今天共读 28 篇、精读 17 篇，主题几乎全在视觉-语言-动作（VLA）智能体与机器人策略学习上。

2) 最值得看：MIRTH 用互信息+时间锚点强化长程推理，3D HAMSTER 用 3D 轨迹把高层规划与底层控制缝起来，分层 VLA 的"思考–执行"闭环正在成形。

3) 下一步：建议先精读这两篇 9.0 的，再拿 ChronoFlow、ELASTIC 速读篇做对照，看自己的项目能在长时记忆或测试时自适应上接哪一块。

This is good. Let me finalize.</think>

1) 今天共筛选 28 篇论文，精读 17 篇、速读 11 篇，主题几乎全集中在视觉-语言-动作（VLA）智能体与机器人策略学习上。

2) 最值得关注的两条主线：MIRTH 用互信息与时间锚点做强长程推理、3D HAMSTER 用 3D 轨迹把分层 VLA 的"规划—控制"缝起来，说明 VLA 正从"听懂指令"迈向"长时段可靠执行"。

3) 下一步建议：先精读这两篇 9.0 分的，再拿 ChronoFlow-Policy 看时序流建模、ELASTIC 看测试时自适应算力扩展，对照自己项目决定是补长时记忆还是补推理弹性。

## 精读区
1. [MIRTH: Mutual-Information Reasoning with Temporal Hubs for Vision-Language-Action Agents](/202607/08/2606.31167v1-mirth-mutual-information-reasoning-with-temporal-hubs-for-vision-language-action-agents) （9.0/10）
2. [3D HAMSTER: Bridging Planning and Control in Hierarchical Vision Language Action Models through 3D Trajectory Guidance](/202607/08/2606.31329v1-3d-hamster-bridging-planning-and-control-in-hierarchical-vision-language-action-models-through-3d-trajectory-guidance) （9.0/10）
3. [3D HAMSTER: Bridging Planning and Control in Hierarchical Vision Language Action Models through 3D Trajectory Guidance](/202607/08/2606.31329v2-3d-hamster-bridging-planning-and-control-in-hierarchical-vision-language-action-models-through-3d-trajectory-guidance) （9.0/10）
4. [Unleashing More Actions via Action Compositional Training for VLA Models](/202607/08/2607.00351v1-unleashing-more-actions-via-action-compositional-training-for-vla-models) （9.0/10）
5. [AutoSpeed: Annotation-Free Stage-Adaptive Motion Speed Learning for Robot Manipulation](/202607/08/2607.01051v2-autospeed-annotation-free-stage-adaptive-motion-speed-learning-for-robot-manipulation) （9.0/10）
6. [FurnitureVLA: Learning Long-Horizon Bimanual Furniture Assembly with Vision-Language-Action Model](/202607/08/2607.01212v1-furniturevla-learning-long-horizon-bimanual-furniture-assembly-with-vision-language-action-model) （9.0/10）
7. [VLAFlow: A Unified Training Framework for Vision-Language-Action Models via Co-training and Future Latent Alignment](/202607/08/2607.01586v1-vlaflow-a-unified-training-framework-for-vision-language-action-models-via-co-training-and-future-latent-alignment) （9.0/10）
8. [Bridge-WA: Predicting Where and How the World Changes for Robotic Action](/202607/08/2607.02195v1-bridge-wa-predicting-where-and-how-the-world-changes-for-robotic-action) （9.0/10）
9. [CoRE-VLA: Towards Scalable and Robust Vision-Language-Action Modeling via Conditional Routing of Experts](/202607/08/2607.03693v1-core-vla-towards-scalable-and-robust-vision-language-action-modeling-via-conditional-routing-of-experts) （9.0/10）
10. [High-Fidelity One-Step Generative Visuomotor Policy via Recursive Correction, Frequency Consistency, and Contrastive Flow Matching](/202607/08/2607.03865v1-high-fidelity-one-step-generative-visuomotor-policy-via-recursive-correction-frequency-consistency-and-contrastive-flow-matching) （9.0/10）
11. [WSA$_1$: a 3D-Centric World-Spatial-Action Model for Generalizable Robot Control](/202607/08/2607.03941v1-wsa1-a-3d-centric-world-spatial-action-model-for-generalizable-robot-control) （9.0/10）
12. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/08/2607.04434v2-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies) （9.0/10）
13. [Simple-to-Complex Structured Demonstrations for Vision-Language-Action Learning](/202607/08/2607.04591v1-simple-to-complex-structured-demonstrations-for-vision-language-action-learning) （9.0/10）
14. [CAC-VLA: Context-Gated Action Conditioning for Vision-Language-Action Models](/202607/08/2607.04816v1-cac-vla-context-gated-action-conditioning-for-vision-language-action-models) （9.0/10）
15. [InternVLA-A1.5: Unifying Understanding, Latent Foresight, and Action for Compositional Generalization](/202607/08/2607.04988v1-internvla-a15-unifying-understanding-latent-foresight-and-action-for-compositional-generalization) （9.0/10）
16. [Cortex: A Bidirectionally Aligned Embodied Agent Framework for Long-horizon Manipulation](/202607/08/2607.05377v1-cortex-a-bidirectionally-aligned-embodied-agent-framework-for-long-horizon-manipulation) （9.0/10）
17. [Lift3D-VLA: Lifting VLA Models to 3D Geometry and Dynamics-Aware Manipulation](/202607/08/2607.06564v1-lift3d-vla-lifting-vla-models-to-3d-geometry-and-dynamics-aware-manipulation) （9.0/10）

## 速读区
1. [Efficient Sim-to-Real Transfer of World-Action Models from Synthetic Priors](/202607/08/2606.31101v1-efficient-sim-to-real-transfer-of-world-action-models-from-synthetic-priors) （8.0/10）
2. [ELASTIC: Efficiently Learning to Adaptively Scale Test-Time Compute for Generative Control Policies](/202607/08/2606.31132v1-elastic-efficiently-learning-to-adaptively-scale-test-time-compute-for-generative-control-policies) （8.0/10）
3. [ChronoFlow-Policy: Unifying Past-Current-Future Interaction Flow in Visuomotor Policy Learning](/202607/08/2606.31493v1-chronoflow-policy-unifying-past-current-future-interaction-flow-in-visuomotor-policy-learning) （8.0/10）
4. [ChronoFlow-Policy: Unifying Past-Current-Future Interaction Flow in Visuomotor Policy Learning](/202607/08/2606.31493v2-chronoflow-policy-unifying-past-current-future-interaction-flow-in-visuomotor-policy-learning) （8.0/10）
5. [Multisensory Continual Learning: Adapting Pretrained Visuomotor Policies to Force](/202607/08/2606.30988v2-multisensory-continual-learning-adapting-pretrained-visuomotor-policies-to-force) （7.0/10）
6. [RoboTacDex: A Dexterous Visual-Tactile-Action Dataset for Humanoid Manipulation](/202607/08/2606.31836v1-robotacdex-a-dexterous-visual-tactile-action-dataset-for-humanoid-manipulation) （7.0/10）
7. [DVG-WM: Disentangled Video Generation Enables Efficient Embodied World Model for Robotic Manipulation](/202607/08/2606.32028v2-dvg-wm-disentangled-video-generation-enables-efficient-embodied-world-model-for-robotic-manipulation) （7.0/10）
8. [From World Models to World Action Models: A Concise Tutorial for Robotics](/202607/08/2607.00836v1-from-world-models-to-world-action-models-a-concise-tutorial-for-robotics) （7.0/10）
9. [Multisensory Continual Learning: Adapting Pretrained Visuomotor Policies to Force](/202607/08/2606.30988v1-multisensory-continual-learning-adapting-pretrained-visuomotor-policies-to-force) （6.0/10）
10. [Multisensory Continual Learning: Adapting Pretrained Visuomotor Policies to Force](/202607/08/2606.30988v3-multisensory-continual-learning-adapting-pretrained-visuomotor-policies-to-force) （6.0/10）
11. [Stage-Transition Dense Reward Modeling for Reinforcement Learning](/202607/08/2606.31377v1-stage-transition-dense-reward-modeling-for-reinforcement-learning) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
