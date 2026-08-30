# 日报 · 2026-08-30

- 最近生成时间：2026-08-30 19:36:42 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：28
- 精读区：17
- 速读区：11

## 今日简报（AI）
<think>The user wants a daily digest in Chinese, 3 lines max, based on the provided data about robotics/imitation learning papers from 2026-08-30. Let me summarize concisely.

Key points:
- 28 papers total, 17 deep-read, 11 speed-read
- Top papers (9.0/10): "The Imitator Game" (robot imitation benchmarking) and "WorldToken" (time-first sequence modeling for robotic imitation)
- Other notable 8.0/10 papers relate to counterfactual supervision, action inference, world-model vs imitated world-action models

I need to output 3 lines:
1) Overview for title - engaging
2) Most valuable 1-2 directions/conclusions
3) Next step suggestion for general readers

No markdown headers, no JSON, just plain text 1-3 lines.</think>

今天精选 28 篇机器人模仿与策略学习论文，其中 17 篇深入研读，整体聚焦"机器人模仿能力如何突破纯动作预测"这一核心问题。最值得关注的两条线索：一是《The Imitator Game》提出超越动作预测的机器人模仿能力基准，为衡量真"理解式模仿"提供了量化工具；二是《WorldToken》以时间优先的序列建模重塑机器人模仿学习路径，叠加 CounterAlign 的反事实监督与"世界模型 vs 模仿世界-动作模型"的能力分离研究，共同指向"可评估、可解释、可泛化"的新一代模仿学习框架。建议普通读者先读《The Imitator Game》的基准设计与《WorldToken》的时序思路，再用一两个 demo 任务跟踪后续工作，判断这些方法能否真正迁移到自家机器人或仿真环境。

## 精读区
1. [The Imitator Game: Benchmarking Robot Imitative Ability Beyond Action Prediction](/202608/30/2608.22301v1-the-imitator-game-benchmarking-robot-imitative-ability-beyond-action-prediction) （9.0/10）
2. [WorldToken: Time-First Sequence Modeling for Robotic Imitation Learning](/202608/30/2608.22591v1-worldtoken-time-first-sequence-modeling-for-robotic-imitation-learning) （9.0/10）
3. [Triplet2Track: A Hierarchical System with Object-Centric Representations for Reliable Long-Horizon Manipulation](/202608/30/2608.22800v1-triplet2track-a-hierarchical-system-with-object-centric-representations-for-reliable-long-horizon-manipulation) （9.0/10）
4. [InstructMove: A Text-Indispensable Benchmark for Instruction-Following Manipulation](/202608/30/2608.22990v1-instructmove-a-text-indispensable-benchmark-for-instruction-following-manipulation) （9.0/10）
5. [Act with Intent: Distilling Behavior Intent for Vision-Language-Action Models](/202608/30/2608.23478v1-act-with-intent-distilling-behavior-intent-for-vision-language-action-models) （9.0/10）
6. [Hierarchical Skill Retrieval for Data-Efficient Adaptation of Vision-Language-Action Models](/202608/30/2608.24042v1-hierarchical-skill-retrieval-for-data-efficient-adaptation-of-vision-language-action-models) （9.0/10）
7. [V-Link: Recovering Lost Visual Representations in Action DiT for Vision-Language-Action Models](/202608/30/2608.25308v1-v-link-recovering-lost-visual-representations-in-action-dit-for-vision-language-action-models) （9.0/10）
8. [RA-VLA: Retrieval-Augmented VLA for Test-Time Adaptation](/202608/30/2608.25585v1-ra-vla-retrieval-augmented-vla-for-test-time-adaptation) （9.0/10）
9. [LM-X: Explainable Action Modeling with Progress, Event, and Uncertainty Prediction for Generalist Robot Manipulation](/202608/30/2608.25757v2-lm-x-explainable-action-modeling-with-progress-event-and-uncertainty-prediction-for-generalist-robot-manipulation) （9.0/10）
10. [MA-VLA: Multi-Arm Vision-Language-Action Model for Collaboration and Compositional Generalization](/202608/30/2608.25864v1-ma-vla-multi-arm-vision-language-action-model-for-collaboration-and-compositional-generalization) （9.0/10）
11. [VISTA: Visually Inferred Spatial ConTact Attention for Contact-Rich Manipulation](/202608/30/2608.25872v1-vista-visually-inferred-spatial-contact-attention-for-contact-rich-manipulation) （9.0/10）
12. [StreamPI: Streaming Multimodal Temporal Modeling for Vision-Language-Action Models](/202608/30/2608.26067v1-streampi-streaming-multimodal-temporal-modeling-for-vision-language-action-models) （9.0/10）
13. [Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](/202608/30/2608.26103v2-zero-wam-in-context-world-action-modeling-from-human-videos-for-open-ended-task-generalization) （9.0/10）
14. [FLARE: A Failure-Aware Framework for Autonomous Correction and Recovery in Visual-Language Robotic Manipulation](/202608/30/2608.26645v1-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-visual-language-robotic-manipulation) （9.0/10）
15. [PredVLA: A Sub-Million-Parameter Predictive-Coding Policy for Robot Manipulation](/202608/30/2608.26673v1-predvla-a-sub-million-parameter-predictive-coding-policy-for-robot-manipulation) （9.0/10）
16. [TemporalFlow-VLA: Learning Physically Grounded Execution History for Long-Horizon Robot Manipulation](/202608/30/2608.26821v1-temporalflow-vla-learning-physically-grounded-execution-history-for-long-horizon-robot-manipulation) （9.0/10）
17. [Riemann-1.0: An Embodied World Action Model for Physical AI](/202608/30/2608.27033v1-riemann-10-an-embodied-world-action-model-for-physical-ai) （9.0/10）

## 速读区
1. [CounterAlign: Counterfactual Supervision for Vision-Language-Action Models](/202608/30/2608.21740v1-counteralign-counterfactual-supervision-for-vision-language-action-models) （8.0/10）
2. [DELE-w0.5: Inferring Action from Future Latent State for Robotic Manipulation](/202608/30/2608.22067v3-dele-w05-inferring-action-from-future-latent-state-for-robotic-manipulation) （8.0/10）
3. [On the Capability Separation Between World-Model Policy Learning and Imitated World-Action Models](/202608/30/2608.22197v1-on-the-capability-separation-between-world-model-policy-learning-and-imitated-world-action-models) （8.0/10）
4. [DreamMimic: Learning Visuomotor Whole-Body Loco-Manipulation via World Model](/202608/30/2608.22278v1-dreammimic-learning-visuomotor-whole-body-loco-manipulation-via-world-model) （8.0/10）
5. [WAM-OPD: On-Policy Distillation for World Action Models](/202608/30/2608.22364v1-wam-opd-on-policy-distillation-for-world-action-models) （8.0/10）
6. [Pointing-VLA: Typed Spatial Grounding Interfaces for Vision-Language-Action Manipulation](/202608/30/2608.23138v1-pointing-vla-typed-spatial-grounding-interfaces-for-vision-language-action-manipulation) （8.0/10）
7. [TONAV: Task-Oriented Navigation and Action-Velocity Chunk Learning for Articulated Object Quadrupedal Mobile Manipulation](/202608/30/2608.22296v1-tonav-task-oriented-navigation-and-action-velocity-chunk-learning-for-articulated-object-quadrupedal-mobile-manipulation) （7.0/10）
8. [LD4WAM: Learning Latent Dynamics from Human Videos for World Action Models](/202608/30/2608.22403v1-ld4wam-learning-latent-dynamics-from-human-videos-for-world-action-models) （7.0/10）
9. [Robust Bimanual Vision-Language-Action Models via Embarrassingly Simple Modality Masking](/202608/30/2608.22419v1-robust-bimanual-vision-language-action-models-via-embarrassingly-simple-modality-masking) （7.0/10）
10. [TrAct: Bridging Robot Control and Visual Prediction with Visual Tracks](/202608/30/2608.24101v1-tract-bridging-robot-control-and-visual-prediction-with-visual-tracks) （7.0/10）
11. [Beyond Instance Slots: Semantically Rich World Models for Physical Interaction Planning](/202608/30/2608.22294v2-beyond-instance-slots-semantically-rich-world-models-for-physical-interaction-planning) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
