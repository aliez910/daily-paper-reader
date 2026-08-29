# 日报 · 2026-08-29

- 最近生成时间：2026-08-29 19:46:22 UTC
- 今日累计更新：2 次
- 今日累计推荐总数：39
- 精读区：24
- 速读区：15

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and produce a concise summary in Chinese, within 3 sentences, based on the given data. I need to follow the specified format:

1) A headline-suitable one-sentence summary
2) A sentence highlighting 1-2 most worthwhile directions/conclusions
3) A sentence giving next-step advice for general readers

Let me analyze the data:
- Date: 2026-08-29
- Total: 39 papers
- Deep read: 24
- Quick read: 15
- Top deep read: WorldToken (10.0) and ForeTime-VLA (9.0) - both about robotic imitation learning with time/future token approaches
- Quick reads include topics like demonstration unlearning, visual-tactile grasping, counterfactual supervision for VLA models

Key themes: Robotics imitation learning, VLA models, time/future token prediction, physical property awareness, counterfactual supervision.

Let me craft the summary:</think>

今日精选 39 篇机器人与具身智能论文，聚焦模仿学习与视觉-语言-动作模型的最新进展，重点围绕时间序列建模与未来 token 预测展开。最值得关注的两个方向：WorldToken 和 ForeTime-VLA 提出了以"时间优先"和"因果未来 token"为核心的新框架，在机器人模仿与传送带操控任务上效果突出；同时，ViTacPhys 与 CounterAlign 分别从视觉-触觉物理属性感知和反事实监督角度增强了 VLA 模型的鲁棒性。感兴趣的同学可优先精读 WorldToken，再结合 CounterAlign 思考如何把时间因果建模与反事实监督融合到自己的项目中。

## 精读区
1. [WorldToken: Time-First Sequence Modeling for Robotic Imitation Learning](/202608/29/2608.22591v1-worldtoken-time-first-sequence-modeling-for-robotic-imitation-learning) （10.0/10）
2. [ForeTime-VLA: Causal Future-Token Distillation from a World Action Model for Conveyor-Belt Manipulation](/202608/29/2608.20735v1-foretime-vla-causal-future-token-distillation-from-a-world-action-model-for-conveyor-belt-manipulation) （9.0/10）
3. [Beyond Imitation: Self-Improving Robot Policies via Off-Policy Q-Planning](/202608/29/2608.21204v1-beyond-imitation-self-improving-robot-policies-via-off-policy-q-planning) （9.0/10）
4. [Inferring Action from Future Latent State for Robotic Manipulation](/202608/29/2608.22067v2-inferring-action-from-future-latent-state-for-robotic-manipulation) （9.0/10）
5. [The Imitator Game: Benchmarking Robot Imitative Ability Beyond Action Prediction](/202608/29/2608.22301v1-the-imitator-game-benchmarking-robot-imitative-ability-beyond-action-prediction) （9.0/10）
6. [Robust Bimanual Vision-Language-Action Models via Embarrassingly Simple Modality Masking](/202608/29/2608.22419v1-robust-bimanual-vision-language-action-models-via-embarrassingly-simple-modality-masking) （9.0/10）
7. [Triplet2Track: A Hierarchical System with Object-Centric Representations for Reliable Long-Horizon Manipulation](/202608/29/2608.22800v1-triplet2track-a-hierarchical-system-with-object-centric-representations-for-reliable-long-horizon-manipulation) （9.0/10）
8. [Pointing-VLA: Typed Spatial Grounding Interfaces for Vision-Language-Action Manipulation](/202608/29/2608.23138v1-pointing-vla-typed-spatial-grounding-interfaces-for-vision-language-action-manipulation) （9.0/10）
9. [GaussVLA: Geometry-Aware Spatial Reasoning for Vision-Language-Action Model](/202608/29/2608.24959v1-gaussvla-geometry-aware-spatial-reasoning-for-vision-language-action-model) （9.0/10）
10. [RA-VLA: Retrieval-Augmented VLA for Test-Time Adaptation](/202608/29/2608.25585v1-ra-vla-retrieval-augmented-vla-for-test-time-adaptation) （9.0/10）
11. [LM-X: Explainable Action Modeling with Progress, Event, and Uncertainty Prediction for Generalist Robot Manipulation](/202608/29/2608.25757v2-lm-x-explainable-action-modeling-with-progress-event-and-uncertainty-prediction-for-generalist-robot-manipulation) （9.0/10）
12. [VISTA: Visually Inferred Spatial ConTact Attention for Contact-Rich Manipulation](/202608/29/2608.25872v1-vista-visually-inferred-spatial-contact-attention-for-contact-rich-manipulation) （9.0/10）
13. [One Policy, Many Embodiments: Unified Camera-Centric Action Geometry Pre-training for Heterogeneous Embodied Manipulation](/202608/29/2608.26058v1-one-policy-many-embodiments-unified-camera-centric-action-geometry-pre-training-for-heterogeneous-embodied-manipulation) （9.0/10）
14. [StreamPI: Streaming Multimodal Temporal Modeling for Vision-Language-Action Models](/202608/29/2608.26067v1-streampi-streaming-multimodal-temporal-modeling-for-vision-language-action-models) （9.0/10）
15. [Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](/202608/29/2608.26103v2-zero-wam-in-context-world-action-modeling-from-human-videos-for-open-ended-task-generalization) （9.0/10）
16. [FLARE: A Failure-Aware Framework for Autonomous Correction and Recovery in Visual-Language Robotic Manipulation](/202608/29/2608.26645v1-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-visual-language-robotic-manipulation) （9.0/10）
17. [TemporalFlow-VLA: Learning Physically Grounded Execution History for Long-Horizon Robot Manipulation](/202608/29/2608.26821v1-temporalflow-vla-learning-physically-grounded-execution-history-for-long-horizon-robot-manipulation) （9.0/10）
18. [EXIMO: VLM Guided Exploration of VLA Policies](/202608/29/2608.19891v1-eximo-vlm-guided-exploration-of-vla-policies) （9.0/10）
19. [ForeTime-VLA: Causal Future-Token Distillation from a World Action Model for Conveyor-Belt Manipulation](/202608/29/2608.20735v2-foretime-vla-causal-future-token-distillation-from-a-world-action-model-for-conveyor-belt-manipulation) （9.0/10）
20. [Inferring Action from Future Latent State for Robotic Manipulation](/202608/29/2608.22067v1-inferring-action-from-future-latent-state-for-robotic-manipulation) （9.0/10）
21. [Act with Intent: Distilling Behavior Intent for Vision-Language-Action Models](/202608/29/2608.23478v1-act-with-intent-distilling-behavior-intent-for-vision-language-action-models) （9.0/10）
22. [Hierarchical Skill Retrieval for Data-Efficient Adaptation of Vision-Language-Action Models](/202608/29/2608.24042v1-hierarchical-skill-retrieval-for-data-efficient-adaptation-of-vision-language-action-models) （9.0/10）
23. [Gripper-aware Vision Language Action Models](/202608/29/2608.24603v1-gripper-aware-vision-language-action-models) （9.0/10）
24. [V-Link: Recovering Lost Visual Representations in Action DiT for Vision-Language-Action Models](/202608/29/2608.25308v1-v-link-recovering-lost-visual-representations-in-action-dit-for-vision-language-action-models) （9.0/10）

## 速读区
1. [Rethinking Demonstration Unlearning in Imitation Learning for Robotics](/202608/29/2608.20784v1-rethinking-demonstration-unlearning-in-imitation-learning-for-robotics) （8.0/10）
2. [ViTacPhys: Physical Property-Aware Grasping from Human Visual-Tactile Demonstrations](/202608/29/2608.21355v1-vitacphys-physical-property-aware-grasping-from-human-visual-tactile-demonstrations) （8.0/10）
3. [CounterAlign: Counterfactual Supervision for Vision-Language-Action Models](/202608/29/2608.21740v1-counteralign-counterfactual-supervision-for-vision-language-action-models) （8.0/10）
4. [DreamMimic: Learning Visuomotor Whole-Body Loco-Manipulation via World Model](/202608/29/2608.22278v1-dreammimic-learning-visuomotor-whole-body-loco-manipulation-via-world-model) （8.0/10）
5. [LD4WAM: Learning Latent Dynamics from Human Videos for World Action Models](/202608/29/2608.22403v1-ld4wam-learning-latent-dynamics-from-human-videos-for-world-action-models) （8.0/10）
6. [InstructMove: A Text-Indispensable Benchmark for Instruction-Following Manipulation](/202608/29/2608.22990v1-instructmove-a-text-indispensable-benchmark-for-instruction-following-manipulation) （8.0/10）
7. [What Matters for Latent Actions in Robot Learning](/202608/29/2608.19613v1-what-matters-for-latent-actions-in-robot-learning) （8.0/10）
8. [Just Noticeable Difference Modeling for Token Compression in Vision-Language-Action Models](/202608/29/2608.21247v1-just-noticeable-difference-modeling-for-token-compression-in-vision-language-action-models) （8.0/10）
9. [PhysCaP: Grounding Code-as-Policy Agent with Physics-Informed Exploration](/202608/29/2608.21031v1-physcap-grounding-code-as-policy-agent-with-physics-informed-exploration) （7.0/10）
10. [WAM-OPD: On-Policy Distillation for World Action Models](/202608/29/2608.22364v1-wam-opd-on-policy-distillation-for-world-action-models) （7.0/10）
11. [TrAct: Bridging Robot Control and Visual Prediction with Visual Tracks](/202608/29/2608.24101v1-tract-bridging-robot-control-and-visual-prediction-with-visual-tracks) （7.0/10）
12. [OrthoSkillVLA: Continual Skill Learning via Gradient-Informed Skill Subspace Adaptation](/202608/29/2608.19589v1-orthoskillvla-continual-skill-learning-via-gradient-informed-skill-subspace-adaptation) （7.0/10）
13. [DECOWAM: Decoupled Whole-Body World-Action Model for Legged Mobile Manipulation](/202608/29/2608.20114v2-decowam-decoupled-whole-body-world-action-model-for-legged-mobile-manipulation) （7.0/10）
14. [VT-MUSE: Multimodal Unified Sequential Visuotactile Representation Learning for Manipulation](/202608/29/2608.21290v1-vt-muse-multimodal-unified-sequential-visuotactile-representation-learning-for-manipulation) （6.0/10）
15. [Contact-Rich Robotic Manipulation in Construction via Zero-Shot Learning: A Diffusion Policy-Guided Adaptive Control](/202608/29/2608.22100v1-contact-rich-robotic-manipulation-in-construction-via-zero-shot-learning-a-diffusion-policy-guided-adaptive-control) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
