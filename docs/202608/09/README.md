# 日报 · 2026-08-09

- 最近生成时间：2026-08-09 17:30:52 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：33
- 精读区：22
- 速读区：11

## 今日简报（AI）
<think>The user wants a daily report summary in Chinese, 3 lines max, based on the given data. Let me analyze:

- Date: 2026-08-09
- Total: 33 papers
- Deep read: 22, Speed read: 11
- Top deep reads (9.0/10): SelfWAM and DynamicWAM - both about World Action Models for robot control/manipulation
- Top speed reads (8.0/10): Cloud-Edge VLA models, RL Bootstrapping OpenVLA-OFT, OC-VLA++ with cross-view consistency

Theme: Robot control/manipulation with World Action Models (WAM) and VLA models

Let me write 3 concise lines:
1. Headline-style overview
2. Key directions worth attention
3. Next step suggestion for general readers</think>

今日共筛选 33 篇论文并完成 22 篇精读，重点聚焦机器人世界-动作模型（WAM）与视觉-语言-动作（VLA）控制的最新进展，主题高度集中在具身智能操作方向。
最值得关注的两条主线：一是 SelfWAM 与 DynamicWAM 证明统一世界-动作模型可同时实现快慢速机器人控制与动态操作；二是云边协同 VLA（Latency-Tolerant）与单目几何引导的跨视角一致性（OC-VLA++）正在突破延迟与视角鲁棒性两大落地瓶颈。
建议普通读者优先读 SelfWAM 了解"世界模型+动作"统一范式，再看 OC-VLA++ 感受工程化技巧，即可快速建立当前具身 AI 前沿的全貌认知。

## 精读区
1. [SelfWAM: A Self-Grounded Unified World Action Model for Fast Robot Control](/202608/09/2608.00725v1-selfwam-a-self-grounded-unified-world-action-model-for-fast-robot-control) （9.0/10）
2. [DynamicWAM: Dual-Path Motion Conditioning for World-Action Models in Dynamic Manipulation](/202608/09/2608.00793v1-dynamicwam-dual-path-motion-conditioning-for-world-action-models-in-dynamic-manipulation) （9.0/10）
3. [DreamTrajectory: Trajectory-Guided Action Generation with World Model Alignment for Mobile Manipulation](/202608/09/2608.01381v1-dreamtrajectory-trajectory-guided-action-generation-with-world-model-alignment-for-mobile-manipulation) （9.0/10）
4. [AffordTrajDP: Dynamic Affordance-Guided Visuomotor Policy Learning for Robotic Manipulation](/202608/09/2608.01603v1-affordtrajdp-dynamic-affordance-guided-visuomotor-policy-learning-for-robotic-manipulation) （9.0/10）
5. [Look Where It Matters: Adaptive Visual Refinement for Vision-Language-Action Models](/202608/09/2608.02197v1-look-where-it-matters-adaptive-visual-refinement-for-vision-language-action-models) （9.0/10）
6. [ChainVLA: Chaining Vision-Language-Action Queries through a Unified Execution State for Long-Horizon Manipulation](/202608/09/2608.02326v2-chainvla-chaining-vision-language-action-queries-through-a-unified-execution-state-for-long-horizon-manipulation) （9.0/10）
7. [Grounded Semantic Re-Binding for Robust Instruction Generalization in Vision-Language-Action Models](/202608/09/2608.02497v1-grounded-semantic-re-binding-for-robust-instruction-generalization-in-vision-language-action-models) （9.0/10）
8. [Ego2Robot: Scalable Robot Data Synthesis from Egocentric Human Data](/202608/09/2608.02580v1-ego2robot-scalable-robot-data-synthesis-from-egocentric-human-data) （9.0/10）
9. [How Should Vision-Language-Action Models Use Proprioceptive State?](/202608/09/2608.03052v1-how-should-vision-language-action-models-use-proprioceptive-state) （9.0/10）
10. [A Hierarchical Approach to Imitation Learning for Manipulation Tasks Requiring Time Varying Forces](/202608/09/2608.03103v1-a-hierarchical-approach-to-imitation-learning-for-manipulation-tasks-requiring-time-varying-forces) （9.0/10）
11. [Unified Visuomotor Targets: Supervising VLAs Beyond Physical Actions](/202608/09/2608.03563v1-unified-visuomotor-targets-supervising-vlas-beyond-physical-actions) （9.0/10）
12. [Track4Action: Distilling World-Centric 3D Tracker into Vision-Language-Action Policies](/202608/09/2608.03727v1-track4action-distilling-world-centric-3d-tracker-into-vision-language-action-policies) （9.0/10）
13. [CofactVLA: Deconfounding Vision-Language-Action Models via Counterfactual Intervention](/202608/09/2608.04396v1-cofactvla-deconfounding-vision-language-action-models-via-counterfactual-intervention) （9.0/10）
14. [Faster-WAM: Efficient Inference-Time Future Conditioning for Robust World Action Models](/202608/09/2608.04404v1-faster-wam-efficient-inference-time-future-conditioning-for-robust-world-action-models) （9.0/10）
15. [MobileWAM: Bridging World Action Models to Mobile Manipulation with Chain-of-Foresight](/202608/09/2608.04657v2-mobilewam-bridging-world-action-models-to-mobile-manipulation-with-chain-of-foresight) （9.0/10）
16. [BridgeVLA++: A Data-Efficient, Generalizable, and Memory-Augmented Vision-Language-Action Framework for 3D Manipulation](/202608/09/2608.05042v1-bridgevla-a-data-efficient-generalizable-and-memory-augmented-vision-language-action-framework-for-3d-manipulation) （9.0/10）
17. [World-to-Wrist: Task-Conditioned Future Wrist Modeling for Fine-Grained Robot Manipulation](/202608/09/2608.05369v1-world-to-wrist-task-conditioned-future-wrist-modeling-for-fine-grained-robot-manipulation) （9.0/10）
18. [JoyAI-RA 0.5: Scaling Robot Manipulation Learning via Dual Action Alignment](/202608/09/2608.05674v1-joyai-ra-05-scaling-robot-manipulation-learning-via-dual-action-alignment) （9.0/10）
19. [SpaceVLA: Spatially Grounded VLA for Robotic Manipulation with User-Authored Grasp and Place Anchors](/202608/09/2608.05730v1-spacevla-spatially-grounded-vla-for-robotic-manipulation-with-user-authored-grasp-and-place-anchors) （9.0/10）
20. [In-Context VLA: Endowing Vision-Language-Action Models with Language via In-Context Post-Training and Agentic Tool Use](/202608/09/2608.05738v1-in-context-vla-endowing-vision-language-action-models-with-language-via-in-context-post-training-and-agentic-tool-use) （9.0/10）
21. [Robust-WAM: Bridging Generative Pretraining and Semantic Foresight in World-Action Models](/202608/09/2608.05903v1-robust-wam-bridging-generative-pretraining-and-semantic-foresight-in-world-action-models) （9.0/10）
22. [DyPES-VLA: Learning Shared Dynamics Priors and Embodiment-Specific Control for Cross-Embodiment Manipulation](/202608/09/2608.06374v1-dypes-vla-learning-shared-dynamics-priors-and-embodiment-specific-control-for-cross-embodiment-manipulation) （9.0/10）

## 速读区
1. [Latency-Tolerant Cloud-Edge Collaborative Vision-Language-Action Models via Emergent Representational Specialization](/202608/09/2608.00569v1-latency-tolerant-cloud-edge-collaborative-vision-language-action-models-via-emergent-representational-specialization) （8.0/10）
2. [RL Bootstrapping of OpenVLA-OFT for a Novel Robot Embodiment](/202608/09/2608.01013v1-rl-bootstrapping-of-openvla-oft-for-a-novel-robot-embodiment) （8.0/10）
3. [OC-VLA++: Monocular Geometry-Guided Cross-View Consistency for Viewpoint-Robust Robotic Manipulation](/202608/09/2608.01066v1-oc-vla-monocular-geometry-guided-cross-view-consistency-for-viewpoint-robust-robotic-manipulation) （8.0/10）
4. [Hermite Curves as Trajectory Priors for Vision-Language-Action Models](/202608/09/2608.01265v1-hermite-curves-as-trajectory-priors-for-vision-language-action-models) （8.0/10）
5. [Diagnosing Compositional Generalization in Sequential Robot Tasks](/202608/09/2607.29687v1-diagnosing-compositional-generalization-in-sequential-robot-tasks) （7.0/10）
6. [Disentangling Visuo-Tactile Foresight: Oracle-Guided Interface Discovery for World Action Models](/202608/09/2608.00547v1-disentangling-visuo-tactile-foresight-oracle-guided-interface-discovery-for-world-action-models) （7.0/10）
7. [Weights or Skills? A Survey of Robot-Learning Techniques: from Action-Predicting Weights to Robots that Write their Own Skills](/202608/09/2608.01851v1-weights-or-skills-a-survey-of-robot-learning-techniques-from-action-predicting-weights-to-robots-that-write-their-own-skills) （7.0/10）
8. [RoboReact: Agentic Skill Distillation from Generated Egocentric Videos for Generalizable Whole-Body Manipulation](/202608/09/2608.03387v1-roboreact-agentic-skill-distillation-from-generated-egocentric-videos-for-generalizable-whole-body-manipulation) （7.0/10）
9. [Probabilistic Reachable-Action Verification of Visuomotor Policies via Set-Based Training](/202608/09/2608.02545v1-probabilistic-reachable-action-verification-of-visuomotor-policies-via-set-based-training) （6.0/10）
10. [EmbodiedVAE: Disentangled Video VAE for Efficient and Controllable Embodied Manipulation](/202608/09/2608.02990v1-embodiedvae-disentangled-video-vae-for-efficient-and-controllable-embodied-manipulation) （6.0/10）
11. [Structure-Aware Robust Fine-Tuning: Defending Vision-Language-Action Robots Against Physical Attention Hijacking](/202608/09/2608.03231v1-structure-aware-robust-fine-tuning-defending-vision-language-action-robots-against-physical-attention-hijacking) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
