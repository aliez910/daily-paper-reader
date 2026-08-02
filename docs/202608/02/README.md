# 日报 · 2026-08-02

- 最近生成时间：2026-08-02 17:54:56 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：27
- 精读区：16
- 速读区：11

## 今日简报（AI）
<think>The user wants a daily report summary in Chinese, 3 sentences, based on the given data. Let me analyze:

- Date: 2026-08-02
- Total: 27 papers
- Deep read: 16
- Quick read: 11
- Top deep reads: "The Curse of Precision: A Data Scaling Law for High-Precision Robotic Manipulation" (10/10), "N0-VTLA: Scaling Vision-Tactile-Language-Action Model with Latent Tactile Tokens" (9/10)
- Top quick reads: Several robotics/vision-tactile manipulation papers

The theme is clearly robotic manipulation with vision-tactile-language-action models. Let me write 3 concise sentences.</think>

今天从 27 篇论文中精选精读 16 篇、速读 11 篇，整体围绕"机器人精细操控"与"视觉-触觉-语言-动作多模态模型"两条主线展开。最值得关注的方向：一是高精度操控存在"精度诅咒"的数据扩展规律，二是视觉-触觉-语言-动作模型通过潜在触觉 token 实现了规模化迁移，两者共同指向多模态感知是突破精细操作瓶颈的关键。建议读者先精读那篇满分论文建立数据规模直觉，再对比速读中的 world model 与 Real2Sim2Real 路线，判断自己更看好端到端 VLA 还是"先仿真后落地"的技术路径。

## 精读区
1. [The Curse of Precision: A Data Scaling Law for High-Precision Robotic Manipulation](/202608/02/2607.23108v1-the-curse-of-precision-a-data-scaling-law-for-high-precision-robotic-manipulation) （10.0/10）
2. [$N_0$-VTLA: Scaling Vision-Tactile-Language-Action Model with Latent Tactile Tokens](/202608/02/2607.23782v1-n0-vtla-scaling-vision-tactile-language-action-model-with-latent-tactile-tokens) （9.0/10）
3. [$N_0$-TWAM: Scaling Tactile-Native World-Action Model for Contact-Rich Manipulation](/202608/02/2607.23783v1-n0-twam-scaling-tactile-native-world-action-model-for-contact-rich-manipulation) （9.0/10）
4. [WorldDiT: A Unified Diffusion Architecture for World and Action Modeling](/202608/02/2607.23909v1-worlddit-a-unified-diffusion-architecture-for-world-and-action-modeling) （9.0/10）
5. [τ: Learning Touch-Augmented Vision-Language-Action Models from Future Visual Supervision](/202608/02/2607.24485v2--learning-touch-augmented-vision-language-action-models-from-future-visual-supervision) （9.0/10）
6. [Decompose and Reorganize: Planning with Primitives and Visuomotor Policies Learned from Demonstrations](/202608/02/2607.25397v1-decompose-and-reorganize-planning-with-primitives-and-visuomotor-policies-learned-from-demonstrations) （9.0/10）
7. [CoTinyVLA: Chain-of-Thought Distillation for a Sub-Billion-Parameter Vision-Language-Action Model](/202608/02/2607.25487v1-cotinyvla-chain-of-thought-distillation-for-a-sub-billion-parameter-vision-language-action-model) （9.0/10）
8. [Tri-Manual Visuomotor Imitation Learning of Robot Policies](/202608/02/2607.25731v1-tri-manual-visuomotor-imitation-learning-of-robot-policies) （9.0/10）
9. [S2A2: Audio-Visual Imitation Learning for Manipulation Tasks Using Acoustic Spatial Information](/202608/02/2607.26047v1-s2a2-audio-visual-imitation-learning-for-manipulation-tasks-using-acoustic-spatial-information) （9.0/10）
10. [MoMo: Dial Motion Mode in Robot Manipulation with Spatiotemporal Action Tokenization](/202608/02/2607.26315v1-momo-dial-motion-mode-in-robot-manipulation-with-spatiotemporal-action-tokenization) （9.0/10）
11. [Explicit Kinematic Guidance from Analytic Concepts for Vision-Language-Action Models](/202608/02/2607.26513v1-explicit-kinematic-guidance-from-analytic-concepts-for-vision-language-action-models) （9.0/10）
12. [Route by Kinematics, Act by Observation: Kinematics-Supervised Expert Routing in MoE-Augmented VLA](/202608/02/2607.26807v1-route-by-kinematics-act-by-observation-kinematics-supervised-expert-routing-in-moe-augmented-vla) （9.0/10）
13. [TurboVLA: Real-Time Vision-Language-Action Model at 32 Hz on an RTX 4090 with <1 GB VRAM](/202608/02/2607.27205v1-turbovla-real-time-vision-language-action-model-at-32-hz-on-an-rtx-4090-with-1-gb-vram) （9.0/10）
14. [It's Not Just More Demos: Counterfactual Action Sensitivity Coverage for Data-Efficient Robust Robot Imitation](/202608/02/2607.27261v1-its-not-just-more-demos-counterfactual-action-sensitivity-coverage-for-data-efficient-robust-robot-imitation) （9.0/10）
15. [Cross-Embodiment Transfer via Behavior-Aligned Representations](/202608/02/2607.27549v1-cross-embodiment-transfer-via-behavior-aligned-representations) （9.0/10）
16. [RoboBRIDGE: A Modular Framework for Bridging Policies to Robust Real-World Robotic Agents](/202608/02/2607.27881v1-robobridge-a-modular-framework-for-bridging-policies-to-robust-real-world-robotic-agents) （9.0/10）

## 速读区
1. [ViTacWorld: Scaling Visuo-Tactile World Models for Contact-Rich Robot Manipulation](/202608/02/2607.22530v1-vitacworld-scaling-visuo-tactile-world-models-for-contact-rich-robot-manipulation) （8.0/10）
2. [Real2Sim2Real for Vision-Language-Action Manipulation: An AMD ROCm-Based Pipeline](/202608/02/2607.22997v1-real2sim2real-for-vision-language-action-manipulation-an-amd-rocm-based-pipeline) （8.0/10）
3. [LeapBot-WA: World-Anchor Action Models via Predictive Latent Alignments](/202608/02/2607.23969v2-leapbot-wa-world-anchor-action-models-via-predictive-latent-alignments) （8.0/10）
4. [FutureRTC: Real-Time Robot Execution with Anticipatory-Conditioned Action Chunking](/202608/02/2607.24008v1-futurertc-real-time-robot-execution-with-anticipatory-conditioned-action-chunking) （8.0/10）
5. [DeVA: Decoupled Video-Action Model with physical guidance for robot policy learning](/202608/02/2607.24159v1-deva-decoupled-video-action-model-with-physical-guidance-for-robot-policy-learning) （8.0/10）
6. [ArmnetBench v0.1: Parallel Real-World Evaluation of Manipulation Policies on a Low-Cost Arm Farm](/202608/02/2607.24481v1-armnetbench-v01-parallel-real-world-evaluation-of-manipulation-policies-on-a-low-cost-arm-farm) （8.0/10）
7. [A Motion-Aware Vector Quantization Framework with Centroid Reuse for Efficient VLA Inference](/202608/02/2607.24148v1-a-motion-aware-vector-quantization-framework-with-centroid-reuse-for-efficient-vla-inference) （7.0/10）
8. [PAC-DP: PAC-Bayesian Diffusion Policy Learning](/202608/02/2607.24296v1-pac-dp-pac-bayesian-diffusion-policy-learning) （7.0/10）
9. [KAI: A Kinematic-Aware Interface for Data-Efficient Articulated Object Manipulation](/202608/02/2607.24493v1-kai-a-kinematic-aware-interface-for-data-efficient-articulated-object-manipulation) （7.0/10）
10. [Data Pyramid for Embodied Manipulation](/202608/02/2607.24744v1-data-pyramid-for-embodied-manipulation) （7.0/10）
11. [Failure Detection for Surgical Robot Imitation Policies via Flow-Matching World Modeling](/202608/02/2607.27511v1-failure-detection-for-surgical-robot-imitation-policies-via-flow-matching-world-modeling) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
