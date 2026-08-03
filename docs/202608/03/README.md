# 日报 · 2026-08-03

- 最近生成时间：2026-08-03 18:55:05 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：28
- 精读区：17
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and output a concise Chinese summary based on the given recommendation data. Let me analyze the data:

- Date: 2026-08-03
- Status: Success
- Total: 28 papers
- Deep reading: 17 papers
- Quick reading: 11 papers

Top deep reading:
- N₀-VTLA: Scaling Vision-Tactile-Language-Action Model with Latent Tactile Tokens (9.0/10)
- WorldDiT: A Unified Diffusion Architecture for World and Action Modeling (9.0/10)

Top quick reading:
- N₀-TWAM: Scaling Tactile-Native World-Action Model for Contact-Rich Manipulation (8.0/10)
- LeapBot-WA: World-Anchor Action Models via Predictive Latent Alignments (8.0/10)
- PAC-DP: PAC-Bayesian Diffusion Policy Learning (8.0/10)

Themes I see:
1. Tactile-native world models and VLA scaling (N₀-VTLA, N₀-TWAM)
2. World-action models with diffusion (WorldDiT, LeapBot-WA)
3. Diffusion policy learning with theoretical guarantees (PAC-DP)

Let me write 3 concise lines in Chinese:

1) Headline-grabbing summary of today's focus
2) 1-2 most noteworthy directions/conclusions
3) Next-step suggestion for general readers

Let me draft:

1) 今天从28篇论文中精选17篇精读，聚焦"世界模型+动作"的统一架构与可扩展触觉表征。

2) 重点关注两条主线：N₀-VTLA/WorldDiT 把视觉-触觉-语言-动作塞进同一个扩散式世界模型；PAC-DP 则给扩散策略加上了 PAC-Bayes 理论保证，让"学得对"变得可证明。

3) 对做机器人或具身智能的读者，建议先读 N₀-VTLA 与 PAC-DP：一个拓展多模态上限，一个夯实训练可靠性。

Let me refine to be more concise and catchy:

1) 今天从 28 篇中精读 17 篇，主线是"世界模型 × 动作策略"的统一架构与可扩展触觉表征。
2) 最值得关注：N₀-VTLA 用潜在触觉 token 把视-触-语言-动作扩展为同一套世界模型；WorldDiT 与 PAC-DP 分别从扩散架构和 PAC-Bayes 理论两端压实"世界-动作"学习。
3) 建议读者先读 N₀-VTLA 与 PAC-DP——前者拓多模态上限，后者给扩散策略补上可证明的训练保证。

That's good. Let me tighten it more.</think>

今天从 28 篇中精读 17 篇，主线是"世界模型 × 动作策略"的统一架构与可扩展触觉表征。
最值得关注：N₀-VTLA 用潜在触觉 token 把视-触-语言-动作扩展进同一套世界模型，WorldDiT 与 PAC-DP 分别从扩散架构和 PAC-Bayes 理论两端夯实"世界-动作"学习。
建议先读 N₀-VTLA 与 PAC-DP——前者拓展多模态上限，后者给扩散策略补上可证明的训练保证。

## 精读区
1. [$N_0$-VTLA: Scaling Vision-Tactile-Language-Action Model with Latent Tactile Tokens](/202608/03/2607.23782v1-n0-vtla-scaling-vision-tactile-language-action-model-with-latent-tactile-tokens) （9.0/10）
2. [WorldDiT: A Unified Diffusion Architecture for World and Action Modeling](/202608/03/2607.23909v1-worlddit-a-unified-diffusion-architecture-for-world-and-action-modeling) （9.0/10）
3. [FutureRTC: Real-Time Robot Execution with Anticipatory-Conditioned Action Chunking](/202608/03/2607.24008v1-futurertc-real-time-robot-execution-with-anticipatory-conditioned-action-chunking) （9.0/10）
4. [DeVA: Decoupled Video-Action Model with physical guidance for robot policy learning](/202608/03/2607.24159v1-deva-decoupled-video-action-model-with-physical-guidance-for-robot-policy-learning) （9.0/10）
5. [ArmnetBench v0.1: Parallel Real-World Evaluation of Manipulation Policies on a Low-Cost Arm Farm](/202608/03/2607.24481v1-armnetbench-v01-parallel-real-world-evaluation-of-manipulation-policies-on-a-low-cost-arm-farm) （9.0/10）
6. [Decompose and Reorganize: Planning with Primitives and Visuomotor Policies Learned from Demonstrations](/202608/03/2607.25397v1-decompose-and-reorganize-planning-with-primitives-and-visuomotor-policies-learned-from-demonstrations) （9.0/10）
7. [Tri-Manual Visuomotor Imitation Learning of Robot Policies](/202608/03/2607.25731v2-tri-manual-visuomotor-imitation-learning-of-robot-policies) （9.0/10）
8. [MoMo: Dial Motion Mode in Robot Manipulation with Spatiotemporal Action Tokenization](/202608/03/2607.26315v1-momo-dial-motion-mode-in-robot-manipulation-with-spatiotemporal-action-tokenization) （9.0/10）
9. [RL$^2$-VLA: Adaptive RL Latent Compositional Steering with Test-Time Scaling for Vision-Language-Action Models](/202608/03/2607.26991v2-rl2-vla-adaptive-rl-latent-compositional-steering-with-test-time-scaling-for-vision-language-action-models) （9.0/10）
10. [TurboVLA: Real-Time Vision-Language-Action Model at 32 Hz on an RTX 4090 with <1 GB VRAM](/202608/03/2607.27205v1-turbovla-real-time-vision-language-action-model-at-32-hz-on-an-rtx-4090-with-1-gb-vram) （9.0/10）
11. [It's Not Just More Demos: Counterfactual Action Sensitivity Coverage for Data-Efficient Robust Robot Imitation](/202608/03/2607.27261v1-its-not-just-more-demos-counterfactual-action-sensitivity-coverage-for-data-efficient-robust-robot-imitation) （9.0/10）
12. [Cross-Embodiment Transfer via Behavior-Aligned Representations](/202608/03/2607.27549v1-cross-embodiment-transfer-via-behavior-aligned-representations) （9.0/10）
13. [RedFlow: Redirect Failure into Action-Level Corrections for Flow-matching VLA Policy](/202608/03/2607.27782v1-redflow-redirect-failure-into-action-level-corrections-for-flow-matching-vla-policy) （9.0/10）
14. [RoboBRIDGE: A Modular Framework for Bridging Policies to Robust Real-World Robotic Agents](/202608/03/2607.27881v1-robobridge-a-modular-framework-for-bridging-policies-to-robust-real-world-robotic-agents) （9.0/10）
15. [ST-WAM: Semantic-Temporal World Action Model for Robust Manipulation under Visual Distribution Shifts](/202608/03/2607.28993v1-st-wam-semantic-temporal-world-action-model-for-robust-manipulation-under-visual-distribution-shifts) （9.0/10）
16. [TRACT: Temporally Routed Action Chunks with Chronological Phase Authority for Contact-Rich Manipulation](/202608/03/2607.29285v1-tract-temporally-routed-action-chunks-with-chronological-phase-authority-for-contact-rich-manipulation) （9.0/10）
17. [WCM: A World Critic Model for Vision-Language-Action Reinforcement Learning](/202608/03/2607.29613v1-wcm-a-world-critic-model-for-vision-language-action-reinforcement-learning) （9.0/10）

## 速读区
1. [$N_0$-TWAM: Scaling Tactile-Native World-Action Model for Contact-Rich Manipulation](/202608/03/2607.23783v1-n0-twam-scaling-tactile-native-world-action-model-for-contact-rich-manipulation) （8.0/10）
2. [LeapBot-WA: World-Anchor Action Models via Predictive Latent Alignments](/202608/03/2607.23969v2-leapbot-wa-world-anchor-action-models-via-predictive-latent-alignments) （8.0/10）
3. [PAC-DP: PAC-Bayesian Diffusion Policy Learning](/202608/03/2607.24296v1-pac-dp-pac-bayesian-diffusion-policy-learning) （8.0/10）
4. [τ: Learning Touch-Augmented Vision-Language-Action Models from Future Visual Supervision](/202608/03/2607.24485v2--learning-touch-augmented-vision-language-action-models-from-future-visual-supervision) （8.0/10）
5. [A Motion-Aware Vector Quantization Framework with Centroid Reuse for Efficient VLA Inference](/202608/03/2607.24148v1-a-motion-aware-vector-quantization-framework-with-centroid-reuse-for-efficient-vla-inference) （7.0/10）
6. [Data Pyramid for Embodied Manipulation](/202608/03/2607.24744v1-data-pyramid-for-embodied-manipulation) （7.0/10）
7. [Vision-TL-Action: Neuro-Symbolic Trajectory Generation from Visual Observations and Temporal Logic](/202608/03/2607.26770v1-vision-tl-action-neuro-symbolic-trajectory-generation-from-visual-observations-and-temporal-logic) （7.0/10）
8. [From Passive Video to Editable Experience: Physically Grounded Experience Synthesis for Embodied Intelligence](/202608/03/2607.26903v1-from-passive-video-to-editable-experience-physically-grounded-experience-synthesis-for-embodied-intelligence) （7.0/10）
9. [KAI: A Kinematic-Aware Interface for Data-Efficient Articulated Object Manipulation](/202608/03/2607.24493v1-kai-a-kinematic-aware-interface-for-data-efficient-articulated-object-manipulation) （6.0/10）
10. [NEO: NeRF It Once, Edit It Many Times for Continuous Object Manipulation](/202608/03/2607.24538v1-neo-nerf-it-once-edit-it-many-times-for-continuous-object-manipulation) （6.0/10）
11. [EgoGenesis: Egocentric World-Action Modeling with Online Anchored Projective Memory and Action-3D RoPE](/202608/03/2607.28243v1-egogenesis-egocentric-world-action-modeling-with-online-anchored-projective-memory-and-action-3d-rope) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
