<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-18
- 运行时间：2026-07-18 18:01:58 UTC
- 运行状态：成功
- 本次总论文数：29
- 精读区：18
- 速读区：11

### 今日简报（AI）
<think>The user wants a daily report summary in Chinese, based on the given recommendation data. Let me analyze:

- Date: 2026-07-18
- Total: 29 papers
- Deep read: 18 papers
- Quick read: 11 papers
- Top deep reads: Two papers scored 9.0/10, both about VLA (Vision-Language-Action) models and visuomotor imitation learning
- Quick reads scored 8.0/10: VLM-to-VLA adaptation, tactile-guided dexterous manipulation, sub-task demonstrations for rearrangement

I need to write 3 sentences:
1) A headline-style summary of what was done today
2) Most worthwhile 1-2 directions/conclusions
3) Next step suggestion for general readers

Let me craft this concisely and attractively in Chinese.</think>

今天从 29 篇论文中精读 18 篇、速读 11 篇，主线集中在机器人视觉-语言-动作（VLA）模型与操控学习两大方向，整体节奏紧凑、产能稳定。
最值得关注的是"用更合理的结构而非更大容量提升模仿学习"这一思路（9.0 分），以及通过时序-空间掩码与语言-动作接地实现高效 VLA 适配的方案（9.0/8.0 分），共同指向"结构先于规模"的训练范式。
建议普通读者优先跟踪 VLA 高效适配与灵巧操作基准两条线，留意它们在真实硬件上的复现结果，再决定是否投入工程实践。
- 详情：[/202607/18/README](/202607/18/README)

### 精读区论文标签
1. [TS-Mask VLA: 2D Temporal-Spatial Masking for Vision-Language-Action Model with Effective Bridging](/202607/18/2607.09818v1-ts-mask-vla-2d-temporal-spatial-masking-for-vision-language-action-model-with-effective-bridging)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操作的视觉-语言-动作框架，采用时空掩码
2. [More Structure, Not More Capacity: Object-Centric Representations for Visuomotor Imitation Learning](/202607/18/2607.09825v1-more-structure-not-more-capacity-object-centric-representations-for-visuomotor-imitation-learning)  
   标签：评分：9.0/10、query:rob-il
   evidence：研究面向视觉运动模仿学习的物体中心表征
3. [SUREFlow: State-space Uncertainty-aware REsidual Flow Matching for Robust Robot Manipulation](/202607/18/2607.10504v1-sureflow-state-space-uncertainty-aware-residual-flow-matching-for-robust-robot-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向操作的不确定性感知流匹配视觉-语言-动作策略
4. [Dual-Process Atomic Skill Learning: Decoupling Semantic Reasoning and Real-Time Control](/202607/18/2607.10625v1-dual-process-atomic-skill-learning-decoupling-semantic-reasoning-and-real-time-control)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向复杂多步组合任务的语言条件模仿学习
5. [Action Map Policy: Learning 3D Closed-loop Manipulation via Pixel Classification](/202607/18/2607.10706v1-action-map-policy-learning-3d-closed-loop-manipulation-via-pixel-classification)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过像素级动作分类实现三维闭环操作
6. [SegDiff: Segmented Trajectory Diffusion for Consistent and Adaptive Robot Manipulation](/202607/18/2607.11027v1-segdiff-segmented-trajectory-diffusion-for-consistent-and-adaptive-robot-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：基于模仿学习的闭环视觉运动策略用于机器人操作
7. [Pix2Act: Image-Space Manipulation Policies with Equivariant Augmentation](/202607/18/2607.11167v1-pix2act-image-space-manipulation-policies-with-equivariant-augmentation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向图像空间操作策略的模仿学习方法，使用等变数据增强
8. [See like a Robot: Robot-Centric Pointmaps for Vision-Language-Action Models](/202607/18/2607.11498v1-see-like-a-robot-robot-centric-pointmaps-for-vision-language-action-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向跨视角泛化的视觉-语言-动作模型
9. [Mixture of Frames Policy: Multi-Frame Action Denoising for Bimanual Mobile Manipulation](/202607/18/2607.11884v1-mixture-of-frames-policy-multi-frame-action-denoising-for-bimanual-mobile-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向双臂移动操作的扩散式视觉运动策略
10. [VistaVLA: Geometry- and Semantic-Aware 3D Gaussian-Grounded VLA for Robotic Manipulation](/202607/18/2607.12356v2-vistavla-geometry--and-semantic-aware-3d-gaussian-grounded-vla-for-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操控的三维高斯接地 VLA 端到端视觉-语言-动作模型
11. [Generalizable VLA Finetuning via Representation Anchoring and Language-Action Alignment](/202607/18/2607.13429v1-generalizable-vla-finetuning-via-representation-anchoring-and-language-action-alignment)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过行为克隆在机器人示教上微调的视觉-语言-动作策略
12. [GigaWorld-Policy-0.5: A Faster and Stronger WAM Empowered by AutoResearch](/202607/18/2607.13960v2-gigaworld-policy-05-a-faster-and-stronger-wam-empowered-by-autoresearch)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向闭环实时部署的以动作为中心的World Action模型
13. [Industrial Dexterity Benchmark: A Hardware-Software Benchmarking Platform for Industrial Dexterous Manipulation](/202607/18/2607.14021v1-industrial-dexterity-benchmark-a-hardware-software-benchmarking-platform-for-industrial-dexterous-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：为工业灵巧操作提供基准板与模仿学习框架
14. [Action QFormer: Structured Representation Shaping under Action Supervision in Vision-Language-Action Models](/202607/18/2607.14635v1-action-qformer-structured-representation-shaping-under-action-supervision-in-vision-language-action-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：研究视觉-语言-动作模型中动作监督对表征的影响
15. [Reflex: Real-Time VLA Control through Streaming Inference](/202607/18/2607.14695v1-reflex-real-time-vla-control-through-streaming-inference)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向实时机器人控制的视觉-语言-动作流式推理
16. [FoMoVLA: Bridging Visual Foresight and Motion Guidance for Vision-Language-Action Models](/202607/18/2607.14739v1-fomovla-bridging-visual-foresight-and-motion-guidance-for-vision-language-action-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：结合视觉预测与运动引导的视觉-语言-动作模型用于视觉运动策略学习
17. [Towards Human-like Physical Intelligence: LifelongVision-Language-Action Learning for Robotic Manipulation](/202607/18/2607.14852v1-towards-human-like-physical-intelligence-lifelongvision-language-action-learning-for-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操作的终身视觉-语言-动作学习框架
18. [RoboTTT: Context Scaling for Robot Policies](/202607/18/2607.15275v1-robottt-context-scaling-for-robot-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：扩展视觉运动上下文，实现一次性上下文内模仿并提升闭环长时操作性能

### 速读区论文标签
1. [CLAP: Direct VLM-to-VLA Adaptation via Language-Action Grounding](/202607/18/2607.08974v1-clap-direct-vlm-to-vla-adaptation-via-language-action-grounding)  
   标签：评分：8.0/10、query:rob-il
   evidence：直接将视觉语言模型转化为VLA，构建通用机器人视觉-动作模型
2. [TactiDex: A Real-World Tactile-Guided Benchmark for Human-Like Dexterous Manipulation](/202607/18/2607.09190v1-tactidex-a-real-world-tactile-guided-benchmark-for-human-like-dexterous-manipulation)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向灵巧操作的真实触觉引导基准与标准化评测
3. [Implicit-Behavior Coordination from Unlabeled Sub-Task Demonstrations for Rearrangement Tasks](/202607/18/2607.09234v1-implicit-behavior-coordination-from-unlabeled-sub-task-demonstrations-for-rearrangement-tasks)  
   标签：评分：8.0/10、query:rob-il
   evidence：面向长时序重排任务的隐式行为协调模仿学习
4. [PhysV2A: Reachability-Gated and Semantic-Mask-Constrained Feasibility Completion for Video-to-Robot Manipulation](/202607/18/2607.09365v1-physv2a-reachability-gated-and-semantic-mask-constrained-feasibility-completion-for-video-to-robot-manipulation)  
   标签：评分：8.0/10、query:rob-il
   evidence：将视频中物体运动转化为机器人可执行的操作轨迹
5. [AgenticFocus: Object-Preserving Mixed Reality Synthesis from Human FPV Video for Dexterous Humanoid Learning](/202607/18/2607.08857v2-agenticfocus-object-preserving-mixed-reality-synthesis-from-human-fpv-video-for-dexterous-humanoid-learning)  
   标签：评分：7.0/10、query:rob-il
   evidence：从人类视频生成机器人可训练示教用于模仿学习
6. [Learning More from Less: Reinforcement Learning from Hindsight](/202607/18/2607.09042v1-learning-more-from-less-reinforcement-learning-from-hindsight)  
   标签：评分：7.0/10、query:rob-il
   evidence：通过事后重标记对VLA模型进行强化学习后训练以提升样本效率
7. [GenVid2Robot: From Video Generation to Robot Manipulation via Rigid-Geometric Consistency](/202607/18/2607.09191v1-genvid2robot-from-video-generation-to-robot-manipulation-via-rigid-geometric-consistency)  
   标签：评分：7.0/10、query:rob-il
   evidence：将生成视频运动转换为可执行的机器人操作轨迹，实现视觉到动作的映射
8. [One-Shot Multimodal Learning from Demonstration with Force-Constrained Elastic Maps](/202607/18/2607.09515v1-one-shot-multimodal-learning-from-demonstration-with-force-constrained-elastic-maps)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向操作任务的一次性多模态示教学习
9. [Causally Debiased Latent Action Model for Embodied Action Conditioned World Models](/202607/18/2607.09185v1-causally-debiased-latent-action-model-for-embodied-action-conditioned-world-models)  
   标签：评分：6.0/10、query:rob-il
   evidence：通过潜在动作建模为无标签视频学习动作表征
10. [Tactile and Vision Conditioned Contact-Centric Control for Whole-Arm Manipulation](/202607/18/2607.09218v1-tactile-and-vision-conditioned-contact-centric-control-for-whole-arm-manipulation)  
   标签：评分：6.0/10、query:rob-il
   evidence：基于视觉与触觉条件的滚动时域控制器用于整臂操作
11. [B-spline Policy: Accelerating Manipulation Policies via B-spline Action Representations](/202607/18/2607.09648v1-b-spline-policy-accelerating-manipulation-policies-via-b-spline-action-representations)  
   标签：评分：6.0/10、query:rob-il
   evidence：面向机器人操作策略的连续动作表示


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
