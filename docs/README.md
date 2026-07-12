<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-12
- 运行时间：2026-07-12 17:54:09 UTC
- 运行状态：成功
- 本次总论文数：32
- 精读区：21
- 速读区：11

### 今日简报（AI）
<think>The user wants me to act as a daily report editor and output 3 sentences in Chinese summarizing today's recommended papers. Let me analyze:

- Date: 2026-07-12
- Total: 32 papers
- Deep read: 21 papers
- Quick read: 11 papers
- Top deep reads: CoRE-VLA (9.0) and WSA (9.0) - both about VLA models and robot control
- Quick reads: generative visuomotor policies, lightweight robotic control, simulation benchmarks

Let me craft 3 concise Chinese sentences:
1) A title-worthy summary of today's content
2) The most noteworthy directions/conclusions (1-2)
3) Next-step suggestion for general readers</think>

今日精选 32 篇论文（精读 21 + 速读 11），焦点集中在视觉-语言-动作模型与机器人通用控制方向，多篇提出新架构与训练策略推动可扩展性与泛化能力。最值得关注的是 CoRE-VLA 与 WSA$_1$ 两篇高分工作，分别通过条件路由专家机制和 3D 中心的世界-空间-动作建模，为大规模 VLA 训练与跨场景机器人控制提供了新范式。建议普通读者优先阅读这两篇精读以把握 VLA 演进主线，再结合速读中关于生成式策略压缩与仿真基准的内容，理解从模型到落地的完整链路。
- 详情：[/202607/12/README](/202607/12/README)

### 精读区论文标签
1. [CoRE-VLA: Towards Scalable and Robust Vision-Language-Action Modeling via Conditional Routing of Experts](/202607/12/2607.03693v1-core-vla-towards-scalable-and-robust-vision-language-action-modeling-via-conditional-routing-of-experts)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向异构传感器的通用视觉-语言-动作模型
2. [WSA$_1$: a 3D-Centric World-Spatial-Action Model for Generalizable Robot Control](/202607/12/2607.03941v1-wsa1-a-3d-centric-world-spatial-action-model-for-generalizable-robot-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：基于模仿学习的机器人基础模型，将视觉与语言映射为连续动作并引入三维推理
3. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v2-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向通用机器人操作策略的仿真-真实统一基准
4. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v3-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向通用机器人操控策略的统一仿真与真实基准
5. [Simple-to-Complex Structured Demonstrations for Vision-Language-Action Learning](/202607/12/2607.04591v1-simple-to-complex-structured-demonstrations-for-vision-language-action-learning)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向视觉模仿学习 VLA 的结构化示教数据组织
6. [CAC-VLA: Context-Gated Action Conditioning for Vision-Language-Action Models](/202607/12/2607.04816v1-cac-vla-context-gated-action-conditioning-for-vision-language-action-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向通用机器人操作的视觉-语言-动作模型动作条件化
7. [DSWAM: A Dual-System World Action Foundation Model for Fine-Grained Robot Manipulation](/202607/12/2607.04927v1-dswam-a-dual-system-world-action-foundation-model-for-fine-grained-robot-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：在世界动作模型与 VLA 之间开展公平真实机器人对比，面向细粒度操控评测
8. [InternVLA-A1.5: Unifying Understanding, Latent Foresight, and Action for Compositional Generalization](/202607/12/2607.04988v1-internvla-a15-unifying-understanding-latent-foresight-and-action-for-compositional-generalization)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向复杂操作组合泛化的统一视觉-语言-动作模型
9. [Cortex: A Bidirectionally Aligned Embodied Agent Framework for Long-horizon Manipulation](/202607/12/2607.05377v1-cortex-a-bidirectionally-aligned-embodied-agent-framework-for-long-horizon-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：基于VLA的分层框架，面向长时序机器人操作并利用视觉反馈闭环
10. [From Fixed to Free Cameras: Calibration-Free View-Robust Vision-Language-Action Model](/202607/12/2607.05396v1-from-fixed-to-free-cameras-calibration-free-view-robust-vision-language-action-model)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向操作的视觉-语言-动作模型，具有视角鲁棒性的视觉运动策略
11. [SIEVE: Structure-Aware Data Selection for Imitation Learning with VLA Models](/202607/12/2607.06442v1-sieve-structure-aware-data-selection-for-imitation-learning-with-vla-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向VLA模仿学习的结构感知数据选择方法
12. [Pelican-VLA 0.5: Attending Before Acting Benefits Generalization](/202607/12/2607.06655v1-pelican-vla-05-attending-before-acting-benefits-generalization)  
   标签：评分：9.0/10、query:rob-il
   evidence：统一视觉-语言-动作模型，融合感知、未来帧生成与动作预测并引入推理槽
13. [Pelican-VLA 0.5: Attending Before Acting Benefits Generalization](/202607/12/2607.06655v2-pelican-vla-05-attending-before-acting-benefits-generalization)  
   标签：评分：9.0/10、query:rob-il
   evidence：具有注意力级泛化的统一 VLA 模型用于操作
14. [NativeMEM: Native Memory Compression for Long-Horizon Robotic Manipulation](/202607/12/2607.06678v1-nativemem-native-memory-compression-for-long-horizon-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向长视程机器人操控的带视觉记忆VLA端到端控制模型
15. [PriGo: Test-Time Primitive Guidance to Diffusion and Flow Policies for Adaptive Robotic Manipulation](/202607/12/2607.07076v1-prigo-test-time-primitive-guidance-to-diffusion-and-flow-policies-for-adaptive-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操作的扩散与流策略模仿学习
16. [LEEVLA: Seeing What Matters in Latent Environment Evolution for Vision-Language-Action](/202607/12/2607.08182v1-leevla-seeing-what-matters-in-latent-environment-evolution-for-vision-language-action)  
   标签：评分：9.0/10、query:rob-il
   evidence：将多模态输入映射为机器人动作的VLA模型，聚焦复杂动态场景
17. [TFP: Temporally Conditioned Memory-Fusion Policies for Visuomotor Learning](/202607/12/2607.08283v1-tfp-temporally-conditioned-memory-fusion-policies-for-visuomotor-learning)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向阶段依赖操作的记忆增强视觉运动学习
18. [SkillPlug: Unsupervised Skill Mining for Few-Shot Adaptation in Robotic Manipulation](/202607/12/2607.08354v1-skillplug-unsupervised-skill-mining-for-few-shot-adaptation-in-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过技能挖掘实现少样本视觉运动模仿策略迁移
19. [Harness VLA: Steering Frozen VLAs into Reliable Manipulation Primitives via Memory-Guided Agents](/202607/12/2607.08448v1-harness-vla-steering-frozen-vlas-into-reliable-manipulation-primitives-via-memory-guided-agents)  
   标签：评分：9.0/10、query:rob-il
   evidence：以记忆增强的代理式框架将冻结的视觉-语言-动作模型引导为可靠的接触密集型操控原语
20. [FabriVLA: A Lightweight Vision-Language-Action Model for Precise Multi-Task Manipulation](/202607/12/2607.08575v1-fabrivla-a-lightweight-vision-language-action-model-for-precise-multi-task-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向多任务操控的轻量级VLA模型，在Meta-World MT50上取得高成功率
21. [Native Video-Action Pretraining for Generalizable Robot Control](/202607/12/2607.08639v1-native-video-action-pretraining-for-generalizable-robot-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：为机器人控制从零构建的原生视频-动作基础模型，支撑端到端操控

### 速读区论文标签
1. [High-Fidelity One-Step Generative Visuomotor Policy via Recursive Correction, Frequency Consistency, and Contrastive Flow Matching](/202607/12/2607.03865v1-high-fidelity-one-step-generative-visuomotor-policy-via-recursive-correction-frequency-consistency-and-contrastive-flow-matching)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向机器人操作的快速单步生成式视觉运动策略
2. [XS-VLA: Coupling Coarse-grained Spatial Distillation with Latent Flow Matching for Lightweight Robotic Control](/202607/12/2607.04171v1-xs-vla-coupling-coarse-grained-spatial-distillation-with-latent-flow-matching-for-lightweight-robotic-control)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向端到端机器人控制的轻量视觉-语言-动作模型
3. [RoboDojo: A Unified Sim-and-Real Benchmark for Comprehensive Evaluation of Generalist Robot Manipulation Policies](/202607/12/2607.04434v1-robodojo-a-unified-sim-and-real-benchmark-for-comprehensive-evaluation-of-generalist-robot-manipulation-policies)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向通用机器人操控策略的统一仿真与真实基准
4. [VLA Grounder: Language-Conditioning Space Optimization for Black-Box VLA Models](/202607/12/2607.04517v1-vla-grounder-language-conditioning-space-optimization-for-black-box-vla-models)  
   标签：评分：8.0/10、query:rob-il
   evidence：VLA模型作为机器人端到端动作策略
5. [ObjRetarget: An Object-Aware Motion Retargeting Framework with Anthropomorphic Arm Constraints and Polyhedral Hand Modeling](/202607/12/2607.03828v1-objretarget-an-object-aware-motion-retargeting-framework-with-anthropomorphic-arm-constraints-and-polyhedral-hand-modeling)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向从人类视频进行灵巧操作模仿学习的人-机器人运动重定向框架
6. [SoftVTBench: A Safety-Aware Visuo-Tactile Benchmark for Physically Constrained Robotic Manipulation of Deformable Objects](/202607/12/2607.04234v1-softvtbench-a-safety-aware-visuo-tactile-benchmark-for-physically-constrained-robotic-manipulation-of-deformable-objects)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向物理受限可形变物体操作的视觉-触觉安全基准
7. [HALO-WA: Hybrid-Attention Latent-Guided Online Reinforcement Learning for World-Action Models](/202607/12/2607.04265v1-halo-wa-hybrid-attention-latent-guided-online-reinforcement-learning-for-world-action-models)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向真实操作精度的世界-动作模型在线强化学习
8. [ACE-Brain-0.5: A Unified Embodied Foundational Model for Physical Agentic AI](/202607/12/2607.04426v1-ace-brain-05-a-unified-embodied-foundational-model-for-physical-agentic-ai)  
   标签：评分：7.0/10、query:rob-il
   evidence：统一具身基础模型整合感知、决策、交互与自监控，支撑通用机器人操控
9. [OmniTacTune: Policy-Agnostic Real-World RL for Tactile Residual Adaptation of Visual Policies](/202607/12/2607.03723v1-omnitactune-policy-agnostic-real-world-rl-for-tactile-residual-adaptation-of-visual-policies)  
   标签：评分：6.0/10、query:rob-il
   evidence：面向接触丰富操作的视觉策略触觉残差在线强化学习适配
10. [ACE: Agentic Control for Embodied Manipulation via Zero-shot Workflow Reasoning](/202607/12/2607.04162v1-ace-agentic-control-for-embodied-manipulation-via-zero-shot-workflow-reasoning)  
   标签：评分：6.0/10、query:rob-il
   evidence：基于掩码的视觉-动作闭环接口用于桌面操作
11. [TouchWorld: A Predictive and Reactive Tactile Foundation Model for Dexterous Manipulation](/202607/12/2607.07287v1-touchworld-a-predictive-and-reactive-tactile-foundation-model-for-dexterous-manipulation)  
   标签：评分：6.0/10、query:rob-il
   evidence：在灵巧操控中将触觉快速反馈与慢速动作推理解耦，构建反应式基础模型


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
