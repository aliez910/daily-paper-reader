# 日报 · 2026-07-31

- 最近生成时间：2026-07-31 18:37:39 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：27
- 精读区：16
- 速读区：11

## 今日简报（AI）
<think>The user wants a concise Chinese daily report summary in 3 lines, based on the provided data about robotics/AI papers. Let me craft this carefully.

The data shows:
- 27 papers total, 16 deep-read, 11 skim-read
- Top rated papers focus on Vision-Language-Action models with Mixture-of-Experts, visual attention for robot manipulation, and various world models for robotics
- Themes: VLA models, robot manipulation, world models, tactile models, data scaling laws

Let me write 3 concise lines:
1) Catchy title-line about today's focus
2) Most worth-noting direction/conclusion (1-2 papers)
3) Next-step suggestion for general readers

Line 1: 今日聚焦机器人操作与VLA模型,共筛27篇(精读16),MoE架构与可解释视觉注意力成主线。
Line 2: 最值得关注:MoE VLA展现涌现组合技能,GuidedAttention通过可纠错注意力提升分布外鲁棒性,二者指向"更可解释、更可干预"的机器人策略方向。
Line 3: 建议关注世界-动作统一模型(WorldDiT等)与触觉原生架构,后续可观察它们在长程任务与接触密集场景的实测表现。</think>

今日聚焦机器人操作与 VLA 模型,共筛 27 篇(精读 16、速读 11),Mixture-of-Experts 架构与可纠错视觉注意力成为主线。
最值得关注两个方向:MoE 结构的 VLA 模型涌现出组合式技能;GuidedAttention 通过可解释、可修正的注意力提升模仿学习在分布外场景的鲁棒性。
下一步建议普通读者持续跟踪世界-动作统一扩散架构(如 WorldDiT)与触觉原生世界模型在长程、接触密集任务中的实测进展。

## 精读区
1. [Emergent Compositional Skills in Mixture-of-Experts VLAs](/202607/31/2607.20771v2-emergent-compositional-skills-in-mixture-of-experts-vlas) （9.0/10）
2. [GuidedAttention: Interpretable and Correctable Visual Attention for OOD-Robust Robot Manipulation via Imitation Learning](/202607/31/2607.21049v2-guidedattention-interpretable-and-correctable-visual-attention-for-ood-robust-robot-manipulation-via-imitation-learning) （9.0/10）
3. [$N_0$-VTLA: Scaling Vision-Tactile-Language-Action Model with Latent Tactile Tokens](/202607/31/2607.23782v1-n0-vtla-scaling-vision-tactile-language-action-model-with-latent-tactile-tokens) （9.0/10）
4. [FutureRTC: Real-Time Robot Execution with Anticipatory-Conditioned Action Chunking](/202607/31/2607.24008v1-futurertc-real-time-robot-execution-with-anticipatory-conditioned-action-chunking) （9.0/10）
5. [DeVA: Decoupled Video-Action Model with physical guidance for robot policy learning](/202607/31/2607.24159v1-deva-decoupled-video-action-model-with-physical-guidance-for-robot-policy-learning) （9.0/10）
6. [Decompose and Reorganize: Planning with Primitives and Visuomotor Policies Learned from Demonstrations](/202607/31/2607.25397v1-decompose-and-reorganize-planning-with-primitives-and-visuomotor-policies-learned-from-demonstrations) （9.0/10）
7. [A Causality-aware Infer-diagnose-refine Framework for Test-time Modality Adaptation in VLA Models](/202607/31/2607.25516v1-a-causality-aware-infer-diagnose-refine-framework-for-test-time-modality-adaptation-in-vla-models) （9.0/10）
8. [Tri-Manual Visuomotor Imitation Learning of Robot Policies](/202607/31/2607.25731v2-tri-manual-visuomotor-imitation-learning-of-robot-policies) （9.0/10）
9. [SAM3D-Guided Object-Centric Representation Alignment for Vision-Language-Action Models](/202607/31/2607.25912v1-sam3d-guided-object-centric-representation-alignment-for-vision-language-action-models) （9.0/10）
10. [MoMo: Dial Motion Mode in Robot Manipulation with Spatiotemporal Action Tokenization](/202607/31/2607.26315v1-momo-dial-motion-mode-in-robot-manipulation-with-spatiotemporal-action-tokenization) （9.0/10）
11. [Explicit Kinematic Guidance from Analytic Concepts for Vision-Language-Action Models](/202607/31/2607.26513v1-explicit-kinematic-guidance-from-analytic-concepts-for-vision-language-action-models) （9.0/10）
12. [CheckVLA: Execution-Time Verification with Action-Conditioned World Model for Long-Horizon Mobile Manipulation](/202607/31/2607.26789v1-checkvla-execution-time-verification-with-action-conditioned-world-model-for-long-horizon-mobile-manipulation) （9.0/10）
13. [RL$^2$-VLA: Adaptive RL Latent Compositional Steering with Test-Time Scaling for Vision-Language-Action Models](/202607/31/2607.26991v2-rl2-vla-adaptive-rl-latent-compositional-steering-with-test-time-scaling-for-vision-language-action-models) （9.0/10）
14. [Cross-Embodiment Transfer via Behavior-Aligned Representations](/202607/31/2607.27549v1-cross-embodiment-transfer-via-behavior-aligned-representations) （9.0/10）
15. [World Action Planner: Generalizable Decision-Making with Action-Conditioned World Models](/202607/31/2607.27599v1-world-action-planner-generalizable-decision-making-with-action-conditioned-world-models) （9.0/10）
16. [RedFlow: Redirect Failure into Action-Level Corrections for Flow-matching VLA Policy](/202607/31/2607.27782v1-redflow-redirect-failure-into-action-level-corrections-for-flow-matching-vla-policy) （9.0/10）

## 速读区
1. [The Curse of Precision: A Data Scaling Law for High-Precision Robotic Manipulation](/202607/31/2607.23108v1-the-curse-of-precision-a-data-scaling-law-for-high-precision-robotic-manipulation) （8.0/10）
2. [$N_0$-TWAM: Scaling Tactile-Native World-Action Model for Contact-Rich Manipulation](/202607/31/2607.23783v1-n0-twam-scaling-tactile-native-world-action-model-for-contact-rich-manipulation) （8.0/10）
3. [WorldDiT: A Unified Diffusion Architecture for World and Action Modeling](/202607/31/2607.23909v1-worlddit-a-unified-diffusion-architecture-for-world-and-action-modeling) （8.0/10）
4. [LeapBot-WA: World-Anchor Action Models via Predictive Latent Alignments](/202607/31/2607.23969v2-leapbot-wa-world-anchor-action-models-via-predictive-latent-alignments) （8.0/10）
5. [Scale Up Strategically: Learning Compositional Generalization via Bias-Aware Evaluation and Data Collection for Robotic Manipulation](/202607/31/2607.21582v1-scale-up-strategically-learning-compositional-generalization-via-bias-aware-evaluation-and-data-collection-for-robotic-manipulation) （7.0/10）
6. [AXIS: A Growable Community-Driven Data Engine for Scalable Robot Manipulation](/202607/31/2607.21588v1-axis-a-growable-community-driven-data-engine-for-scalable-robot-manipulation) （7.0/10）
7. [Ordered Action Tokens for Visuomotor Policy Learning](/202607/31/2607.21670v1-ordered-action-tokens-for-visuomotor-policy-learning) （7.0/10）
8. [Addressing the Orchestration Gap in Generalist Robots via Physical Agency](/202607/31/2607.21725v1-addressing-the-orchestration-gap-in-generalist-robots-via-physical-agency) （7.0/10）
9. [URF: A Unified Robot Control-Policy Framework for Stable Contact Aware Manipulation](/202607/31/2607.20912v1-urf-a-unified-robot-control-policy-framework-for-stable-contact-aware-manipulation) （6.0/10）
10. [TableVerse: A Large-scale Tabletop Dataset with Real-world Grounded Layouts for Generalizable Manipulation](/202607/31/2607.21017v1-tableverse-a-large-scale-tabletop-dataset-with-real-world-grounded-layouts-for-generalizable-manipulation) （6.0/10）
11. [One Hand Watches The Other: Dynamic Multi-Agent Cooperation for Sample-Efficient Bimanual Manipulation in Dynamic Environments](/202607/31/2607.22119v1-one-hand-watches-the-other-dynamic-multi-agent-cooperation-for-sample-efficient-bimanual-manipulation-in-dynamic-environments) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
