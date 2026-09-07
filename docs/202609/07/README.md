# 日报 · 2026-09-07

- 最近生成时间：2026-09-07 20:46:32 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：28
- 精读区：17
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and output a concise summary in Chinese based on the given recommendation data. Let me analyze the data:

- Date: 2026-09-07
- Status: Success
- Total: 28 papers
- Deep reading (精读): 17 papers
- Quick reading (速读): 11 papers
- Top deep reading papers: DriftingVLA (9.0/10) and CometVLA (9.0/10)
- Top quick reading papers: AGM (8.0/10), SymVD (8.0/10), AcrossWAM1.0 (8.0/10)

All papers are about VLA (Vision-Language-Action) models for robotics/embodied AI. The theme is clearly about robot manipulation policies using VLA models.

Let me write 3 lines:
1) A catchy headline-like summary
2) The most noteworthy directions/findings
3) Next-step suggestion for general readers

Let me make it concise, specific, and based only on the given data.</think>

今日聚焦机器人 VLA 模型：精读 17 篇中，DriftingVLA 与 CometVLA 并列 9.0 分，前者主打"逐维度时间漂移"实现原生一步生成，后者通过具身数据金字塔协同训练强化物理理解；速读 8 分档集中在记忆闭环、对称蒸馏与世界-动作栈三条互补路线。
方向上值得优先关注的是"原生一步 VLA 生成"与"多源数据协同训练提升物理理解"，这两条路径都在试图降低延迟并拉近仿真与真实部署的差距。
建议先精读 DriftingVLA 的方法图与 CometVLA 的数据分层结构，再结合 SymVD 看蒸馏如何压缩大模型，留意这套组合是否适合你自己的机器人或自动驾驶任务。

## 精读区
1. [DriftingVLA: Native One-Step Vision-Language-Action Generation via Per-Dimension Temporal Drifting](/202609/07/2608.29749v1-driftingvla-native-one-step-vision-language-action-generation-via-per-dimension-temporal-drifting) （9.0/10）
2. [CometVLA: Co-Training on an Embodied Data Pyramid towards Physical Understanding](/202609/07/2608.30289v1-cometvla-co-training-on-an-embodied-data-pyramid-towards-physical-understanding) （9.0/10）
3. [Behavior-Skill: A Fine-Grained Benchmark for Evaluating Vision-Language-Action Policies in Long-Horizon Tasks](/202609/07/2608.30536v1-behavior-skill-a-fine-grained-benchmark-for-evaluating-vision-language-action-policies-in-long-horizon-tasks) （9.0/10）
4. [Temporal Forcing: 4D Representation Alignment for Vision-Language-Action Models](/202609/07/2608.30643v1-temporal-forcing-4d-representation-alignment-for-vision-language-action-models) （9.0/10）
5. [ZimaBlue: Evolving Generalizable World Action Models through Scalable Video Pre-training](/202609/07/2609.00188v1-zimablue-evolving-generalizable-world-action-models-through-scalable-video-pre-training) （9.0/10）
6. [REFACTOR-VLA: Unsupervised Library Learning of Typed Motor Programs](/202609/07/2609.01215v1-refactor-vla-unsupervised-library-learning-of-typed-motor-programs) （9.0/10）
7. [EmbodiedSkills: A Unified Framework for Orchestrating, Training, and Deploying VLA Agents](/202609/07/2609.01281v1-embodiedskills-a-unified-framework-for-orchestrating-training-and-deploying-vla-agents) （9.0/10）
8. [Does Imitation Learning Preserve Temporal Robustness in Dexterous Manipulation? An Expert-Learner Comparison Across Task Execution Speeds](/202609/07/2609.01453v1-does-imitation-learning-preserve-temporal-robustness-in-dexterous-manipulation-an-expert-learner-comparison-across-task-execution-speeds) （9.0/10）
9. [RoboTok: An Internet-Scale Data Engine for Human Demonstration Retrieval and Dexterous Manipulation Learning](/202609/07/2609.03199v1-robotok-an-internet-scale-data-engine-for-human-demonstration-retrieval-and-dexterous-manipulation-learning) （9.0/10）
10. [Scaling Bimanual Household Manipulation from 1,500 hours of Demonstrations to On-Policy Corrections](/202609/07/2609.03591v1-scaling-bimanual-household-manipulation-from-1500-hours-of-demonstrations-to-on-policy-corrections) （9.0/10）
11. [WISE: World-model-guided Imagination Scheduling for Efficient Post-training of Vision-Language-Action Models](/202609/07/2609.03681v1-wise-world-model-guided-imagination-scheduling-for-efficient-post-training-of-vision-language-action-models) （9.0/10）
12. [MINERVA: How Small Can a Manipulation Policy Be and Still Solve LIBERO?](/202609/07/2609.03715v1-minerva-how-small-can-a-manipulation-policy-be-and-still-solve-libero) （9.0/10）
13. [Reasoning Without Inference Cost: Latent Semantic Scaffolding for Robot VLA Policies](/202609/07/2609.04893v1-reasoning-without-inference-cost-latent-semantic-scaffolding-for-robot-vla-policies) （9.0/10）
14. [LIBERO-RECOVER: Beyond Task Success Towards Failure Recovery in Robotic Manipulation Models](/202609/07/2609.05178v1-libero-recover-beyond-task-success-towards-failure-recovery-in-robotic-manipulation-models) （9.0/10）
15. [RoboSPA: Can VLA Models Go Beyond Simple Scenes and Short-Horizon Tasks?](/202609/07/2609.05324v1-robospa-can-vla-models-go-beyond-simple-scenes-and-short-horizon-tasks) （9.0/10）
16. [Towards Neuro-Symbolic Procedural Reasoning for Long-Horizon Vision-Language-Action Manipulation](/202609/07/2609.05369v1-towards-neuro-symbolic-procedural-reasoning-for-long-horizon-vision-language-action-manipulation) （9.0/10）
17. [What Matters, When? Diagnosing and Improving Conditional Visual Grounding in Visuomotor Imitation Policies](/202609/07/2609.05376v1-what-matters-when-diagnosing-and-improving-conditional-visual-grounding-in-visuomotor-imitation-policies) （9.0/10）

## 速读区
1. [AGM: Achievement-Grounded Memory for Closed-Loop Agents with Frozen VLA Policies](/202609/07/2608.29537v1-agm-achievement-grounded-memory-for-closed-loop-agents-with-frozen-vla-policies) （8.0/10）
2. [SymVD: Symmetric Vision Language Action Distillation for Robot Manipulation](/202609/07/2608.29828v1-symvd-symmetric-vision-language-action-distillation-for-robot-manipulation) （8.0/10）
3. [AcrossWAM1.0:A Modular Latent World-Action Stack for Compact Robot Policies](/202609/07/2608.29937v1-acrosswam10a-modular-latent-world-action-stack-for-compact-robot-policies) （8.0/10）
4. [PAVE: Predictive Alignment and Value-Guided Evolution for World-Action Policies](/202609/07/2608.30378v2-pave-predictive-alignment-and-value-guided-evolution-for-world-action-policies) （8.0/10）
5. [Training-Free Action Correction for VLA Model Failures via Language Feedback](/202609/07/2608.29967v1-training-free-action-correction-for-vla-model-failures-via-language-feedback) （7.0/10）
6. [Motus2: A Self-Evolving General World Model for Dexterous Manipulation](/202609/07/2608.30237v1-motus2-a-self-evolving-general-world-model-for-dexterous-manipulation) （7.0/10）
7. [Zeva: In-Context Causal Learning for Generalizable Embodied Manipulation](/202609/07/2608.30880v1-zeva-in-context-causal-learning-for-generalizable-embodied-manipulation) （7.0/10）
8. [Facet-0: A Robotic Foundation Model for Contact-Rich Precise Manipulation](/202609/07/2609.01596v1-facet-0-a-robotic-foundation-model-for-contact-rich-precise-manipulation) （7.0/10）
9. [$\mathcal{N}_0$-Foundation: Towards the Age of Tactile Intelligence](/202609/07/2608.29601v1-mathcaln0-foundation-towards-the-age-of-tactile-intelligence) （6.0/10）
10. [Towards Generalizable Visually Grounded Exploration of Household Devices](/202609/07/2609.00845v1-towards-generalizable-visually-grounded-exploration-of-household-devices) （6.0/10）
11. [Latent Cluster Analysis for Vision-Language-Action Models](/202609/07/2609.02634v1-latent-cluster-analysis-for-vision-language-action-models) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
