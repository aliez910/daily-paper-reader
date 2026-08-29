# 日报 · 2026-08-29

- 最近生成时间：2026-08-29 01:14:01 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：29
- 精读区：18
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and output a concise 3-line Chinese summary based on the given recommendation data.

Let me analyze the data:
- Date: 2026-08-29
- Status: Success
- Total: 29 papers
- Deep read: 18
- Quick read: 11
- Top deep reads: WorldToken (10.0), EXIMO (9.0) - both about robotic imitation learning and VLA (Vision-Language-Action)
- Quick reads focus on: latent actions in robot learning, demonstration unlearning, token compression in VLA models

Theme: All papers are about robotics + VLA (Vision-Language-Action) models and imitation learning.

Top picks:
1. WorldToken: Time-First Sequence Modeling for Robotic Imitation Learning (10.0)
2. EXIMO: VLM Guided Exploration of VLA Policies (9.0)
3. What Matters for Latent Actions in Robot Learning (8.0)
4. Rethinking Demonstration Unlearning (8.0)
5. Just Noticeable Difference Modeling for Token Compression in VLA (8.0)

I need to write:
1) A title-suitable one-line summary of what was done today
2) A line pointing to 1-2 most worthwhile directions/conclusions
3) A line giving next-step suggestion for general readers

Let me draft:

1) 今日筛选29篇机器人与具身智能论文，精读18篇速读11篇，焦点集中在VLA策略与模仿学习。
2) 最值得关注：WorldToken以时间优先序列建模刷新模仿学习表现（10分），EXIMO利用VLM引导VLA策略探索（9分），提示"时间结构+多模态引导"成为具身智能新主线。
3) 对关注落地的读者，建议先看WorldToken的时间序列范式和JND token压缩思路，两者结合有助于兼顾性能与部署效率。

Let me refine to be more concise and specific:

1) 今日共筛选29篇论文（精读18/速读11），主题集中在VLA策略与机器人模仿学习。
2) 最值得看：WorldToken以时间优先序列建模拿下满分（10分），EXIMO用VLM引导VLA策略探索（9分），"时间结构+多模态探索"成为新趋势。
3) 建议普通读者优先读WorldToken了解时间序列新范式，再速览JND token压缩，关注性能与效率的平衡。

Let me check the constraint: 3 lines max, each line is one sentence (one 句). Let me adjust.

Actually it says "1-3 行文本", so 1-3 lines. Let me output exactly 3 lines, each one sentence.

Line 1: Today we screened 29 papers on VLA/robotics imitation learning, 18 deep + 11 quick.
Line 2: Most noteworthy: WorldToken (10/10) time-first sequence modeling for imitation, EXIMO (9/10) VLM-guided exploration of VLA policies.
Line 3: For general readers, start with WorldToken's paradigm and the JND token compression idea.

Final version:</think>

今日共筛选29篇论文（精读18、速读11），全部围绕VLA策略与机器人模仿学习展开。
最值得看：WorldToken以时间优先序列建模拿下10分满分，EXIMO用VLM引导VLA策略探索斩获9分，"时间结构+多模态引导"成为具身智能新主线。
普通读者建议先精读WorldToken把握时间序列新范式，再速览JND token压缩论文，兼顾性能与部署效率。

## 精读区
1. [WorldToken: Time-First Sequence Modeling for Robotic Imitation Learning](/202608/29/2608.22591v1-worldtoken-time-first-sequence-modeling-for-robotic-imitation-learning) （10.0/10）
2. [EXIMO: VLM Guided Exploration of VLA Policies](/202608/29/2608.19891v1-eximo-vlm-guided-exploration-of-vla-policies) （9.0/10）
3. [ForeTime-VLA: Causal Future-Token Distillation from a World Action Model for Conveyor-Belt Manipulation](/202608/29/2608.20735v2-foretime-vla-causal-future-token-distillation-from-a-world-action-model-for-conveyor-belt-manipulation) （9.0/10）
4. [Beyond Imitation: Self-Improving Robot Policies via Off-Policy Q-Planning](/202608/29/2608.21204v1-beyond-imitation-self-improving-robot-policies-via-off-policy-q-planning) （9.0/10）
5. [Inferring Action from Future Latent State for Robotic Manipulation](/202608/29/2608.22067v1-inferring-action-from-future-latent-state-for-robotic-manipulation) （9.0/10）
6. [The Imitator Game: Benchmarking Robot Imitative Ability Beyond Action Prediction](/202608/29/2608.22301v1-the-imitator-game-benchmarking-robot-imitative-ability-beyond-action-prediction) （9.0/10）
7. [Robust Bimanual Vision-Language-Action Models via Embarrassingly Simple Modality Masking](/202608/29/2608.22419v1-robust-bimanual-vision-language-action-models-via-embarrassingly-simple-modality-masking) （9.0/10）
8. [Triplet2Track: A Hierarchical System with Object-Centric Representations for Reliable Long-Horizon Manipulation](/202608/29/2608.22800v1-triplet2track-a-hierarchical-system-with-object-centric-representations-for-reliable-long-horizon-manipulation) （9.0/10）
9. [Pointing-VLA: Typed Spatial Grounding Interfaces for Vision-Language-Action Manipulation](/202608/29/2608.23138v1-pointing-vla-typed-spatial-grounding-interfaces-for-vision-language-action-manipulation) （9.0/10）
10. [Act with Intent: Distilling Behavior Intent for Vision-Language-Action Models](/202608/29/2608.23478v1-act-with-intent-distilling-behavior-intent-for-vision-language-action-models) （9.0/10）
11. [Hierarchical Skill Retrieval for Data-Efficient Adaptation of Vision-Language-Action Models](/202608/29/2608.24042v1-hierarchical-skill-retrieval-for-data-efficient-adaptation-of-vision-language-action-models) （9.0/10）
12. [Gripper-aware Vision Language Action Models](/202608/29/2608.24603v1-gripper-aware-vision-language-action-models) （9.0/10）
13. [V-Link: Recovering Lost Visual Representations in Action DiT for Vision-Language-Action Models](/202608/29/2608.25308v1-v-link-recovering-lost-visual-representations-in-action-dit-for-vision-language-action-models) （9.0/10）
14. [RA-VLA: Retrieval-Augmented VLA for Test-Time Adaptation](/202608/29/2608.25585v1-ra-vla-retrieval-augmented-vla-for-test-time-adaptation) （9.0/10）
15. [LM-X: Explainable Action Modeling with Progress, Event, and Uncertainty Prediction for Generalist Robot Manipulation](/202608/29/2608.25757v2-lm-x-explainable-action-modeling-with-progress-event-and-uncertainty-prediction-for-generalist-robot-manipulation) （9.0/10）
16. [StreamPI: Streaming Multimodal Temporal Modeling for Vision-Language-Action Models](/202608/29/2608.26067v1-streampi-streaming-multimodal-temporal-modeling-for-vision-language-action-models) （9.0/10）
17. [Zero-WAM: In-Context World-Action Modeling from Human Videos for Open-Ended Task Generalization](/202608/29/2608.26103v2-zero-wam-in-context-world-action-modeling-from-human-videos-for-open-ended-task-generalization) （9.0/10）
18. [FLARE: A Failure-Aware Framework for Autonomous Correction and Recovery in Visual-Language Robotic Manipulation](/202608/29/2608.26645v1-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-visual-language-robotic-manipulation) （9.0/10）

## 速读区
1. [What Matters for Latent Actions in Robot Learning](/202608/29/2608.19613v1-what-matters-for-latent-actions-in-robot-learning) （8.0/10）
2. [Rethinking Demonstration Unlearning in Imitation Learning for Robotics](/202608/29/2608.20784v1-rethinking-demonstration-unlearning-in-imitation-learning-for-robotics) （8.0/10）
3. [Just Noticeable Difference Modeling for Token Compression in Vision-Language-Action Models](/202608/29/2608.21247v1-just-noticeable-difference-modeling-for-token-compression-in-vision-language-action-models) （8.0/10）
4. [ViTacPhys: Physical Property-Aware Grasping from Human Visual-Tactile Demonstrations](/202608/29/2608.21355v1-vitacphys-physical-property-aware-grasping-from-human-visual-tactile-demonstrations) （8.0/10）
5. [CounterAlign: Counterfactual Supervision for Vision-Language-Action Models](/202608/29/2608.21740v1-counteralign-counterfactual-supervision-for-vision-language-action-models) （8.0/10）
6. [DreamMimic: Learning Visuomotor Whole-Body Loco-Manipulation via World Model](/202608/29/2608.22278v1-dreammimic-learning-visuomotor-whole-body-loco-manipulation-via-world-model) （8.0/10）
7. [OrthoSkillVLA: Continual Skill Learning via Gradient-Informed Skill Subspace Adaptation](/202608/29/2608.19589v1-orthoskillvla-continual-skill-learning-via-gradient-informed-skill-subspace-adaptation) （7.0/10）
8. [DECOWAM: Decoupled Whole-Body World-Action Model for Legged Mobile Manipulation](/202608/29/2608.20114v2-decowam-decoupled-whole-body-world-action-model-for-legged-mobile-manipulation) （7.0/10）
9. [PhysCaP: Grounding Code-as-Policy Agent with Physics-Informed Exploration](/202608/29/2608.21031v1-physcap-grounding-code-as-policy-agent-with-physics-informed-exploration) （7.0/10）
10. [WAM-OPD: On-Policy Distillation for World Action Models](/202608/29/2608.22364v1-wam-opd-on-policy-distillation-for-world-action-models) （7.0/10）
11. [VT-MUSE: Multimodal Unified Sequential Visuotactile Representation Learning for Manipulation](/202608/29/2608.21290v1-vt-muse-multimodal-unified-sequential-visuotactile-representation-learning-for-manipulation) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
