# 日报 · 2026-08-13

- 最近生成时间：2026-08-13 17:59:08 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：27
- 精读区：16
- 速读区：11

## 今日简报（AI）
<think>用户需要我根据日报数据生成3句以内的中文总结。让我分析一下数据：

- 日期：2026-08-13
- 总数：27篇论文
- 精读16篇，速读11篇
- 精读最高分9.0：CofactVLA（反事实干预去混淆VLA模型）和Explicit Language Memory（显式语言记忆用于长期规划）
- 速读最高分8.0：Faster-WAM（高效推理的未来条件）、MobileWAM（移动操作的世界动作模型）、VLAff（视觉-语言-可供性模型）

主题都围绕VLA（Vision-Language-Action）模型，这是机器人/具身智能领域。

要求：
1) 标题感官的概括
2) 最值得看的1-2个方向
3) 下步建议

我需要简洁但具体，不编造内容。</think>

今天围绕视觉-语言-动作（VLA）模型共筛读27篇，精读16篇，热点集中在去混淆、长期记忆与高效推理三条主线。最值得关注的是 CofactVLA 通过反事实干预削弱视觉-语言-动作链路中的混杂偏置，以及 Explicit Language Memory 用显式语言记忆解锁长时序规划能力，二者均拿下 9.0 分。对普通读者而言，下一步可优先关注"结构化记忆+去偏训练"的组合落地——这类方法既不需要海量新数据，也更容易迁移到家用机器人、辅助驾驶等真实场景，建议从开源的 WAM 系列与可供性模型入手跟踪后续工作。

## 精读区
1. [CofactVLA: Deconfounding Vision-Language-Action Models via Counterfactual Intervention](/202608/13/2608.04396v1-cofactvla-deconfounding-vision-language-action-models-via-counterfactual-intervention) （9.0/10）
2. [Explicit Language Memory for Long-Horizon Planning in Vision-Language-Action Models](/202608/13/2608.04765v1-explicit-language-memory-for-long-horizon-planning-in-vision-language-action-models) （9.0/10）
3. [BridgeVLA++: A Data-Efficient, Generalizable, and Memory-Augmented Vision-Language-Action Framework for 3D Manipulation](/202608/13/2608.05042v1-bridgevla-a-data-efficient-generalizable-and-memory-augmented-vision-language-action-framework-for-3d-manipulation) （9.0/10）
4. [JoyAI-RA 0.5: Scaling Robot Manipulation Learning via Dual Action Alignment](/202608/13/2608.05674v1-joyai-ra-05-scaling-robot-manipulation-learning-via-dual-action-alignment) （9.0/10）
5. [SpaceVLA: Spatially Grounded VLA for Robotic Manipulation with User-Authored Grasp and Place Anchors](/202608/13/2608.05730v1-spacevla-spatially-grounded-vla-for-robotic-manipulation-with-user-authored-grasp-and-place-anchors) （9.0/10）
6. [In-Context VLA: Endowing Vision-Language-Action Models with Language via In-Context Post-Training and Agentic Tool Use](/202608/13/2608.05738v1-in-context-vla-endowing-vision-language-action-models-with-language-via-in-context-post-training-and-agentic-tool-use) （9.0/10）
7. [VIDP: Variable Impedance Diffusion Policy for Compliant Robot Manipulation from Diverse Demonstrations](/202608/13/2608.06210v1-vidp-variable-impedance-diffusion-policy-for-compliant-robot-manipulation-from-diverse-demonstrations) （9.0/10）
8. [DyPES-VLA: Learning Shared Dynamics Priors and Embodiment-Specific Control for Cross-Embodiment Manipulation](/202608/13/2608.06374v1-dypes-vla-learning-shared-dynamics-priors-and-embodiment-specific-control-for-cross-embodiment-manipulation) （9.0/10）
9. [Fast and Accurate: An Adaptive VLA Inference Framework through Environment-aware Model Selection](/202608/13/2608.06434v1-fast-and-accurate-an-adaptive-vla-inference-framework-through-environment-aware-model-selection) （9.0/10）
10. [Cross-View Action Consistency for Camera-Robust Vision-Language-Action Policies](/202608/13/2608.06965v1-cross-view-action-consistency-for-camera-robust-vision-language-action-policies) （9.0/10）
11. [AutoIntervene: Calibrated Intervention for Action-Chunking Imitation Learning Policies](/202608/13/2608.07065v1-autointervene-calibrated-intervention-for-action-chunking-imitation-learning-policies) （9.0/10）
12. [LIRA: Local Cross-Layer Information Routing for Vision-Language-Action Decoding](/202608/13/2608.07596v1-lira-local-cross-layer-information-routing-for-vision-language-action-decoding) （9.0/10）
13. [Vid2WAM: Distilling Video Diffusion Priors into World Action Models](/202608/13/2608.08558v1-vid2wam-distilling-video-diffusion-priors-into-world-action-models) （9.0/10）
14. [JEPA-WAM: Learning Vision-Language-Action Policies with Joint-Embedding World Modeling](/202608/13/2608.09381v1-jepa-wam-learning-vision-language-action-policies-with-joint-embedding-world-modeling) （9.0/10）
15. [JEPA-WAM: Stage-Level Joint-Embedding Prediction for World-Action Models in Robot Manipulation](/202608/13/2608.10780v1-jepa-wam-stage-level-joint-embedding-prediction-for-world-action-models-in-robot-manipulation) （9.0/10）
16. [StellaVLA: In-Context Structured Demonstration for Generalizable Vision-Language-Action Models](/202608/13/2608.11671v1-stellavla-in-context-structured-demonstration-for-generalizable-vision-language-action-models) （9.0/10）

## 速读区
1. [Faster-WAM: Efficient Inference-Time Future Conditioning for Robust World Action Models](/202608/13/2608.04404v1-faster-wam-efficient-inference-time-future-conditioning-for-robust-world-action-models) （8.0/10）
2. [MobileWAM: Bridging World Action Models to Mobile Manipulation with Chain-of-Foresight](/202608/13/2608.04657v2-mobilewam-bridging-world-action-models-to-mobile-manipulation-with-chain-of-foresight) （8.0/10）
3. [VLAff: Vision-Language-Affordance Model for Unified Actionable Affordances](/202608/13/2608.05215v1-vlaff-vision-language-affordance-model-for-unified-actionable-affordances) （8.0/10）
4. [World-to-Wrist: Task-Conditioned Future Wrist Modeling for Fine-Grained Robot Manipulation](/202608/13/2608.05369v1-world-to-wrist-task-conditioned-future-wrist-modeling-for-fine-grained-robot-manipulation) （8.0/10）
5. [SiMDex: Mining Similar Egocentric Videos for Cross-Embodiment Dexterous Manipulation](/202608/13/2608.04196v1-simdex-mining-similar-egocentric-videos-for-cross-embodiment-dexterous-manipulation) （7.0/10）
6. [ARGUS: Aligning Robot Scene Geometry Under Shifting Views with Large 3D Vision Models](/202608/13/2608.05579v1-argus-aligning-robot-scene-geometry-under-shifting-views-with-large-3d-vision-models) （7.0/10）
7. [Decoupling Intention from Trajectory: A Representational Deduction Framework for World Action Models](/202608/13/2608.06994v1-decoupling-intention-from-trajectory-a-representational-deduction-framework-for-world-action-models) （7.0/10）
8. [C2Dex: Contact-Consistent Reconstruction and Retargeting for Dexterous Manipulation from Monocular Video](/202608/13/2608.07045v1-c2dex-contact-consistent-reconstruction-and-retargeting-for-dexterous-manipulation-from-monocular-video) （7.0/10）
9. [SSC: A Verifiable Structured Representation for Bimanual Manipulation Labelling](/202608/13/2608.04425v1-ssc-a-verifiable-structured-representation-for-bimanual-manipulation-labelling) （6.0/10）
10. [GeniWorld: A Generalizable Interactive World Model for Robotic Manipulation via Visual Actions](/202608/13/2608.06332v1-geniworld-a-generalizable-interactive-world-model-for-robotic-manipulation-via-visual-actions) （6.0/10）
11. [Capek 0.5: An Execution-Centric Vision-Language Model for Embodied Intelligence](/202608/13/2608.06756v1-capek-05-an-execution-centric-vision-language-model-for-embodied-intelligence) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
