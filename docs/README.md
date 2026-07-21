<div class="dpr-home-notice-card">
  <h3 class="dpr-home-notice-title">🚀 Start Here</h3>
  <ul class="dpr-home-notice-list">
    <li><a href="#/tutorial/README">使用教程</a></li>
  </ul>
</div>

## 每次日报
- 最新运行日期：2026-07-21
- 运行时间：2026-07-21 18:12:08 UTC
- 运行状态：成功
- 本次总论文数：23
- 精读区：12
- 速读区：11

### 今日简报（AI）
<think>The user wants me to act as a daily report editor and output 3 lines of Chinese summary based on the given data. Let me analyze:

- Date: 2026-07-21
- Status: Success
- Total: 23 papers
- Deep read (精读): 12
- Quick read (速读): 11
- Top deep reads: SegDiff (9.0) and Pix2Act (9.0) - both about robot manipulation with diffusion/image-space policies
- Quick reads: VIA (Visual Interface Agent for Robot Control), predictive/aligned/scalable robot learning, WALA (latent actions)

Theme: Robot manipulation and learning, particularly diffusion-based trajectory models and image-space policies.

Let me write 3 concise, specific Chinese lines:
1) A headline-style summary
2) Most notable directions/conclusions
3) Next-step suggestion for general readers</think>

今日精选 23 篇机器人操控与学习前沿，精读 12 篇，速读 11 篇，整体质量稳定且方向集中。
本日最值得关注的两个亮点：分段轨迹扩散模型 SegDiff（9.0）在长程、组合式操控任务上展现出色的一致性与自适应能力；Pix2Act（9.0）通过等变增强在图像空间直接生成动作策略，简化了从像素到行为的映射路径。
建议关注"扩散+轨迹分段"与"图像空间等变策略"两条主线，若从事机器人基础模型研发，可优先复现 Pix2Act 的数据增强策略并评估其在自身任务上的迁移效果。
- 详情：[/202607/21/README](/202607/21/README)

### 精读区论文标签
1. [SegDiff: Segmented Trajectory Diffusion for Consistent and Adaptive Robot Manipulation](/202607/21/2607.11027v1-segdiff-segmented-trajectory-diffusion-for-consistent-and-adaptive-robot-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：模仿学习闭环视觉运动策略，观测到动作映射
2. [Pix2Act: Image-Space Manipulation Policies with Equivariant Augmentation](/202607/21/2607.11167v1-pix2act-image-space-manipulation-policies-with-equivariant-augmentation)  
   标签：评分：9.0/10、query:rob-il
   evidence：针对操纵策略的模仿学习方法，以图像空间动作预测为核心
3. [VistaVLA: Geometry- and Semantic-Aware 3D Gaussian-Grounded VLA for Robotic Manipulation](/202607/21/2607.12356v2-vistavla-geometry--and-semantic-aware-3d-gaussian-grounded-vla-for-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：视觉-语言-动作模型直接将语言指令和二维视觉输入映射为机器人动作
4. [Generalizable VLA Finetuning via Representation Anchoring and Language-Action Alignment](/202607/21/2607.13429v1-generalizable-vla-finetuning-via-representation-anchoring-and-language-action-alignment)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过行为克隆在机器人演示上微调视觉-语言-动作模型以完成操纵任务
5. [Industrial Dexterity Benchmark: A Hardware-Software Benchmarking Platform for Industrial Dexterous Manipulation](/202607/21/2607.14021v1-industrial-dexterity-benchmark-a-hardware-software-benchmarking-platform-for-industrial-dexterous-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向工业灵巧操作端到端多模态模仿学习的软硬件基准平台
6. [DiMaS: Distribution Matching for Steering Vision-Language-Action Models](/202607/21/2607.14280v1-dimas-distribution-matching-for-steering-vision-language-action-models)  
   标签：评分：9.0/10、query:rob-il
   evidence：为用作机器人操作策略的VLA模型设计的表示引导方法
7. [Towards Human-like Physical Intelligence: LifelongVision-Language-Action Learning for Robotic Manipulation](/202607/21/2607.14852v1-towards-human-like-physical-intelligence-lifelongvision-language-action-learning-for-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向机器人操纵的终身视觉-语言-动作学习框架
8. [RoboTTT: Context Scaling for Robot Policies](/202607/21/2607.15275v1-robottt-context-scaling-for-robot-policies)  
   标签：评分：9.0/10、query:rob-il
   evidence：从人类视频进行一次性上下文模仿学习，扩展视觉运动上下文并实现闭环增益
9. [Xiaomi-Robotics-1: Scaling Vision-Language-Action Models with over 100K Hours of Real-World Trajectories](/202607/21/2607.15330v1-xiaomi-robotics-1-scaling-vision-language-action-models-with-over-100k-hours-of-real-world-trajectories)  
   标签：评分：9.0/10、query:rob-il
   evidence：以十万小时级真实移动操纵轨迹训练通用 VLA 模型
10. [Dynamics-Aware Meta-Imitation for Generalization to Unseen Robotic Manipulation](/202607/21/2607.15880v1-dynamics-aware-meta-imitation-for-generalization-to-unseen-robotic-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：面向未见操纵任务泛化的元模仿学习框架
11. [RynnBrain 1.1: Towards More Capable and Generalizable Embodied Foundation Model](/202607/21/2607.17977v1-rynnbrain-11-towards-more-capable-and-generalizable-embodied-foundation-model)  
   标签：评分：9.0/10、query:rob-il
   evidence：提出RynnBrain-VLA跨具身动作空间模型并部署到多款机器人
12. [Closing the Loop in Humanoid VLA: Persistent 3D Object Tokens for Verifiable Loco-Manipulation](/202607/21/2607.18016v1-closing-the-loop-in-humanoid-vla-persistent-3d-object-tokens-for-verifiable-loco-manipulation)  
   标签：评分：9.0/10、query:rob-il
   evidence：通过持久化3D物体令牌在视觉-语言-动作策略中实现闭环反馈的移动操纵

### 速读区论文标签
1. [VIA: Visual Interface Agent for Robot Control](/202607/21/2607.11119v1-via-visual-interface-agent-for-robot-control)  
   标签：评分：8.0/10、query:rob-il
   evidence：通过视觉界面控制基础模型实现通用机器人策略
2. [Towards Predictive, Aligned, and Scalable Robot Learning](/202607/21/2607.11270v1-towards-predictive-aligned-and-scalable-robot-learning)  
   标签：评分：8.0/10、query:rob-il
   evidence：基于潜变量世界动作模型的视觉动力学推理与动作生成
3. [WALA Learning Executable Latent Actions from Action-Labeled Demonstrations and Action-Free Videos](/202607/21/2607.11397v1-wala-learning-executable-latent-actions-from-action-labeled-demonstrations-and-action-free-videos)  
   标签：评分：8.0/10、query:rob-il
   evidence：从有动作演示与无动作视频中联合学习可执行潜动作的模仿框架
4. [See like a Robot: Robot-Centric Pointmaps for Vision-Language-Action Models](/202607/21/2607.11498v1-see-like-a-robot-robot-centric-pointmaps-for-vision-language-action-models)  
   标签：评分：8.0/10、query:rob-il
   evidence：解决 VLA 模型中相机坐标系与机器人坐标系不匹配的问题
5. [A Single Diffusion-Policy Controller for Multi-Task Block Pushing with Zero-Shot Sim-to-Real Transfer](/202607/21/2607.10892v1-a-single-diffusion-policy-controller-for-multi-task-block-pushing-with-zero-shot-sim-to-real-transfer)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向多任务操作的模仿学习扩散策略
6. [EDAR: Learning Environment-Dependent Action Representations for Robotic Manipulation](/202607/21/2607.11427v1-edar-learning-environment-dependent-action-representations-for-robotic-manipulation)  
   标签：评分：7.0/10、query:rob-il
   evidence：基于环境视觉后果的视觉到动作映射
7. [Mixture of Frames Policy: Multi-Frame Action Denoising for Bimanual Mobile Manipulation](/202607/21/2607.11884v1-mixture-of-frames-policy-multi-frame-action-denoising-for-bimanual-mobile-manipulation)  
   标签：评分：7.0/10、query:rob-il
   evidence：面向双臂移动操作的扩散式视觉运动策略
8. [Worlds in One Demo: A Synthetic Data Engine for Learning Open-World Mobile Manipulation](/202607/21/2607.13154v2-worlds-in-one-demo-a-synthetic-data-engine-for-learning-open-world-mobile-manipulation)  
   标签：评分：7.0/10、query:rob-il
   evidence：通过合成数据引擎从少量演示扩展面向开放世界移动操纵的模仿学习
9. [DenseReward: Dense Reward Learning via Failure Synthesis for Robotic Manipulation](/202607/21/2607.13033v1-densereward-dense-reward-learning-via-failure-synthesis-for-robotic-manipulation)  
   标签：评分：6.0/10、query:rob-il
   evidence：面向机器人操纵的密集奖励学习，超越模仿学习并使用视觉-语言奖励模型
10. [Distributionally Robust and Safe Imitation Learning](/202607/21/2607.13436v1-distributionally-robust-and-safe-imitation-learning)  
   标签：评分：6.0/10、query:rob-il
   evidence：面向复杂决策任务的分布鲁棒且安全的模仿学习框架
11. [ConceptTree: Bringing Semantic Transparency to Black-Box Decision Making for Robotic Manipulation](/202607/21/2607.17861v1-concepttree-bringing-semantic-transparency-to-black-box-decision-making-for-robotic-manipulation)  
   标签：评分：6.0/10、query:rob-il
   evidence：将操作技能选择重构为基于视觉概念的推理,实现观测到动作的映射


<div class="dpr-home-promo-card">
  <h3 class="dpr-home-promo-title">💬 社区与支持</h3>
  <ul class="dpr-home-promo-list">
    <li>欢迎 Star / Fork / Issue / PR</li>
    <li>QQ群：583867967（欢迎交流，已有：1151人）</li>
  </ul>
</div>
