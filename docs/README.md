<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-11
- 运行时间：2026-07-11 18:16:12 UTC
- 运行状态：成功
- 本次总论文数：33
- 精读区：22
- 速读区：11

### 今日简报（AI）
<think>The user wants a Chinese daily report summary in 3 lines based on the given data. Let me analyze:

- Date: 2026-07-11
- Total: 33 papers
- Deep read: 22
- Quick read: 11
- Top deep reads: TACO (9.0/10) - Tactile World Model as Self-Corrector for VLA Post-Training; HiMe (9.0/10) - Hierarchical Embodied Memory for Long-Horizon VLA Control
- Top quick reads: WorldBagel (8.0), High-Fidelity One-Step Generative Visuomotor Policy (8.0), XS-VLA (8.0)

The theme is clearly about VLA (Vision-Language-Action) models for robotics, with emphasis on tactile/world models, memory, and efficient policies.

I need to write 3 lines:
1) Headline-style summary
2) Most noteworthy directions
3) Next-step suggestion for general readers

Keep it concise, specific, no markdown headers or JSON.</think>

今日共筛选 33 篇论文并完成 22 篇精读、11 篇速读，焦点集中在机器人视觉-语言-动作（VLA）模型的后训练与效率优化方向。最值得关注的两条主线：一是 TACO 用触觉世界模型为 VLA 做"自纠错"后训练、HiMe 用分层具身记忆支撑长时序控制，二者都直指 VLA 落地中的鲁棒性与长程规划痛点；二是 XS-VLA、WorldBagel、单步生成式视觉运动策略共同推动模型轻量化与一体化世界建模。普通读者可持续关注"触觉+记忆"加持的 VLA 后训练范式，以及轻量级/单步生成策略两条赛道，下一步建议先精读 TACO 与 HiMe 两篇，再结合 WorldBagel 评估其在自家机器人或仿真平台上的迁移成本。
- 详情：[/202607/11/README](/202607/11/README)

### 精读区论文标签
1. [TACO: TActile World Model as a Self-COrrector forScalable VLA Post-Training](/202607/11/2607.02840v1-taco-tactile-world-model-as-a-self-corrector-forscalable-vla-post-training)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向接触丰富操作任务的视觉-语言-动作模型后训练
2. [HiMe: Hierarchical Embodied Memory for Long-Horizon Vision-Language-Action Control](/202607/11/2607.03449v1-hime-hierarchical-embodied-memory-for-long-horizon-vision-language-action-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操作的 VLA 框架，采用分层具身记忆控制
3. [CoRE-VLA: Towards Scalable and Robust Vision-Language-Action Modeling via Conditional Routing of Experts](/202607/11/2607.03693v1-core-vla-towards-scalable-and-robust-vision-language-action-modeling-via-conditional-routing-of-experts)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向可扩展鲁棒操作的通用VLA条件专家路由模型
4. [WSA$_1$: a 3D-Centric World-Spatial-Action Model for Generalizable Robot Control](/202607/11/2607.03941v1-wsa1-a-3d-centric-world-spatial-action-model-for-generalizable-robot-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：基于3D中心的机器人基础模型,采用模仿学习实现可泛化的视觉到动作控制
5. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/11/2607.04434v1-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：统一仿真与真实基准，用于系统评估通用机器人操作策略
6. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/11/2607.04434v2-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：通用机器人操作策略的统一仿真与真实基准
7. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/11/2607.04434v3-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向通用机器人操纵策略的仿真-现实统一基准
8. [Simple-to-Complex Structured Demonstrations for Vision-Language-Action Learning](/202607/11/2607.04591v1-simple-to-complex-structured-demonstrations-for-vision-language-action-learning)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向VLA模仿学习的由简到繁演示组织策略,用于操作任务
9. [DSWAM: A Dual-System World Action Foundation Model for Fine-Grained Robot Manipulation](/202607/11/2607.04927v1-dswam-a-dual-system-world-action-foundation-model-for-fine-grained-robot-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：双系统世界-动作模型，结合VLA规划与WAM执行用于细粒度操作
10. [Cortex: A Bidirectionally Aligned Embodied Agent Framework for Long-horizon Manipulation](/202607/11/2607.05377v1-cortex-a-bidirectionally-aligned-embodied-agent-framework-for-long-horizon-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向长视野操作的通用 VLA 框架,通过层次化对齐实现
11. [From Fixed to Free Cameras: Calibration-Free View-Robust Vision-Language-Action Model](/202607/11/2607.05396v1-from-fixed-to-free-cameras-calibration-free-view-robust-vision-language-action-model)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向操作任务的视角鲁棒视觉-语言-动作模型
12. [From Foundation to Application: Improving VLA Models in Practice](/202607/11/2607.06403v1-from-foundation-to-application-improving-vla-models-in-practice)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向通用机器人操作的视觉-语言-动作基础模型,覆盖多任务与多形态
13. [SIEVE: Structure-Aware Data Selection for Imitation Learning with VLA Models](/202607/11/2607.06442v1-sieve-structure-aware-data-selection-for-imitation-learning-with-vla-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向VLA模型模仿学习的数据结构感知选择方法
14. [PriGo: Test-Time Primitive Guidance to Diffusion and Flow Policies for Adaptive Robotic Manipulation](/202607/11/2607.07076v1-prigo-test-time-primitive-guidance-to-diffusion-and-flow-policies-for-adaptive-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：模仿学习下扩散/流策略的鲁棒操纵
15. [Dual Latent Memory in Vision-Language-Action Models for Robotic Manipulation](/202607/11/2607.07608v1-dual-latent-memory-in-vision-language-action-models-for-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向长视野操作的具有潜记忆的通用VLA模型
16. [TFP: Temporally Conditioned Memory-Fusion Policies for Visuomotor Learning](/202607/11/2607.08283v1-tfp-temporally-conditioned-memory-fusion-policies-for-visuomotor-learning)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向阶段依赖型操作的带记忆融合视觉运动学习
17. [SkillPlug: Unsupervised Skill Mining for Few-Shot Adaptation in Robotic Manipulation](/202607/11/2607.08354v1-skillplug-unsupervised-skill-mining-for-few-shot-adaptation-in-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过无监督技能挖掘增强视觉运动模仿策略以实现少样本适应
18. [EgoWAM: World Action Models Beyond Pixels with In-the-Wild Egocentric Human Data](/202607/11/2607.08436v1-egowam-world-action-models-beyond-pixels-with-in-the-wild-egocentric-human-data)  
   标签：评分：9.0/10、query:rob-il
   evidence：基于野外第一人称人类数据训练世界动作模型用于可扩展模仿学习
19. [Harness VLA: Steering Frozen VLAs into Reliable Manipulation Primitives via Memory-Guided Agents](/202607/11/2607.08448v1-harness-vla-steering-frozen-vlas-into-reliable-manipulation-primitives-via-memory-guided-agents)  
   标签：评分：9.0/10、query:rob-il
   evidence：将冻结 VLA 暴露为可重试操纵原语，由记忆引导智能体调度
20. [FabriVLA: A Lightweight Vision-Language-Action Model for Precise Multi-Task Manipulation](/202607/11/2607.08575v1-fabrivla-a-lightweight-vision-language-action-model-for-precise-multi-task-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：轻量VLA模型在Meta-World MT50多任务操纵基准上评估
21. [Native Video-Action Pretraining for Generalizable Robot Control](/202607/11/2607.08639v1-native-video-action-pretraining-for-generalizable-robot-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：从头构建的视频动作基础模型，面向通用端到端机器人控制
22. [DexVerse: A Modular Benchmark for Multi-Task, Multi-Embodiment Dexterous Manipulation](/202607/11/2607.08751v1-dexverse-a-modular-benchmark-for-multi-task-multi-embodiment-dexterous-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向多任务灵巧操作的多模块化基准

### 速读区论文标签
1. [WorldBagel: Uncovering the Power of Unified Multimodal Models for Vision-Language-Action-World Modeling](/202607/11/2607.03461v1-worldbagel-uncovering-the-power-of-unified-multimodal-models-for-vision-language-action-world-modeling)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向多任务机器人操作与世界建模的统一VLAW框架
2. [High-Fidelity One-Step Generative Visuomotor Policy via Recursive Correction, Frequency Consistency, and Contrastive Flow Matching](/202607/11/2607.03865v1-high-fidelity-one-step-generative-visuomotor-policy-via-recursive-correction-frequency-consistency-and-contrastive-flow-matching)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向端到端视觉运动学习的生成式视觉运动策略
3. [XS-VLA: Coupling Coarse-grained Spatial Distillation with Latent Flow Matching for Lightweight Robotic Control](/202607/11/2607.04171v1-xs-vla-coupling-coarse-grained-spatial-distillation-with-latent-flow-matching-for-lightweight-robotic-control)  
   标签：评分：8.0/10、query:rob-il
   evidence：通过空间蒸馏构建轻量 VLA 框架用于机器人控制
4. [HALO-WA: Hybrid-Attention Latent-Guided Online Reinforcement Learning for World-Action Models](/202607/11/2607.04265v1-halo-wa-hybrid-attention-latent-guided-online-reinforcement-learning-for-world-action-models)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向端到端机器人控制的世界动作模型在线强化学习自适应
5. [Differential Amplifier-Inspired AmpAttention for Multi-View Robotic Manipulation](/202607/11/2607.02845v1-differential-amplifier-inspired-ampattention-for-multi-view-robotic-manipulation)  
   标签：评分：7.0/10、query:rob-il
   evidence：用于端到端视觉运动操纵的多视图注意力模型
6. [DREAMSTEER: Latent World Models Can Steer VLA Policies During Deployment Without Any Finetuning](/202607/11/2607.02865v1-dreamsteer-latent-world-models-can-steer-vla-policies-during-deployment-without-any-finetuning)  
   标签：评分：7.0/10、query:rob-il
   evidence：部署时通过潜世界模型引导VLA策略
7. [ObjRetarget: An Object-Aware Motion Retargeting Framework with Anthropomorphic Arm Constraints and Polyhedral Hand Modeling](/202607/11/2607.03828v1-objretarget-an-object-aware-motion-retargeting-framework-with-anthropomorphic-arm-constraints-and-polyhedral-hand-modeling)  
   标签：评分：7.0/10、query:rob-il
   evidence：通过人体动作重定向从人类操作视频学习机器人灵巧操作
8. [SoftVTBench: A Safety-Aware Visuo-Tactile Benchmark for Physically Constrained Robotic Manipulation of Deformable Objects](/202607/11/2607.04234v1-softvtbench-a-safety-aware-visuo-tactile-benchmark-for-physically-constrained-robotic-manipulation-of-deformable-objects)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向可形变物体复杂操作的视触觉基准
9. [Exp2VLA: Enabling Vision-Language-Action for Drone Navigation from Expert Demonstrations](/202607/11/2607.03146v1-exp2vla-enabling-vision-language-action-for-drone-navigation-from-expert-demonstrations)  
   标签：评分：6.0/10、query:rob-il
   evidence：从专家示范蒸馏的视觉-语言-动作模型用于端到端控制
10. [Beyond Point-Attached Semantics: Object-Centric Semantic Fields for Generalizable Manipulation](/202607/11/2607.03163v1-beyond-point-attached-semantics-object-centric-semantic-fields-for-generalizable-manipulation)  
   标签：评分：6.0/10、query:rob-il
   evidence：面向可泛化操纵的物体中心 3D 语义场
11. [OmniTacTune: Policy-Agnostic Real-World RL for Tactile Residual Adaptation of Visual Policies](/202607/11/2607.03723v1-omnitactune-policy-agnostic-real-world-rl-for-tactile-residual-adaptation-of-visual-policies)  
   标签：评分：6.0/10、query:rob-il
   evidence：在接触丰富操纵中用触觉反馈闭合视觉策略回路


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
