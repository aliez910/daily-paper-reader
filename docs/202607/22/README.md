# 日报 · 2026-07-22

- 最近生成时间：2026-07-22 18:08:49 UTC
- 今日累计更新：1 次
- 今日累计推荐总数：23
- 精读区：12
- 速读区：11

## 今日简报（AI）
<think>The user wants me to act as a daily report editor and output a concise summary in 3 sentences based on the provided data. Let me analyze:

- 23 papers total, 12 deep reads, 11 quick reads
- Top paper: Xiaomi-Robotics-1 (10/10) - VLA model with 100K+ hours of real-world data
- Second: Mixture of Frames Policy (9/10) - bimanual mobile manipulation
- Other notable: Worlds in One Demo (8/10) - synthetic data for mobile manipulation
- Generalizable VLA Finetuning (8/10) - representation anchoring
- Semantic Anchoring for Robotic Action (8/10) - action representations

The theme is clearly about VLA (Vision-Language-Action) models and robotics manipulation, with emphasis on data scaling, multi-frame action denoising, and synthetic data for open-world tasks.

Let me write 3 concise Chinese sentences:
1) Title-sensory overview
2) Key directions/conclusions worth focusing on
3) Next-step suggestion for general readers</think>

今天从 23 篇候选中精选 12 篇深读，焦点集中在具身智能的大模型与数据驱动范式，尤其是 VLA 视觉-语言-动作模型在真实数据规模化与多帧去噪策略上的突破。最值得看的是小米开源的 10 万小时级真实轨迹 VLA 模型，以及面向双臂移动操作的 Mixture of Frames 去噪策略，前者证明数据规模仍是具身大模型的天花板，后者则展示了多帧融合在提升动作稳定性上的实用价值。普通读者可关注"高质量真实数据 + 多帧动作建模"这一主线，等待跨平台开源权重与可复现的评测基准出现后再做深入跟进。

## 精读区
1. [Xiaomi-Robotics-1: Scaling Vision-Language-Action Models with over 100K Hours of Real-World Trajectories](/202607/22/2607.15330v1-xiaomi-robotics-1-scaling-vision-language-action-models-with-over-100k-hours-of-real-world-trajectories) （10.0/10）
2. [Mixture of Frames Policy: Multi-Frame Action Denoising for Bimanual Mobile Manipulation](/202607/22/2607.11884v1-mixture-of-frames-policy-multi-frame-action-denoising-for-bimanual-mobile-manipulation) （9.0/10）
3. [VistaVLA: Geometry- and Semantic-Aware 3D Gaussian-Grounded VLA for Robotic Manipulation](/202607/22/2607.12356v2-vistavla-geometry--and-semantic-aware-3d-gaussian-grounded-vla-for-robotic-manipulation) （9.0/10）
4. [GigaWorld-Policy-0.5: A Faster and Stronger WAM Empowered by AutoResearch](/202607/22/2607.13960v1-gigaworld-policy-05-a-faster-and-stronger-wam-empowered-by-autoresearch) （9.0/10）
5. [Industrial Dexterity Benchmark: A Hardware-Software Benchmarking Platform for Industrial Dexterous Manipulation](/202607/22/2607.14021v1-industrial-dexterity-benchmark-a-hardware-software-benchmarking-platform-for-industrial-dexterous-manipulation) （9.0/10）
6. [Reflex: Real-Time VLA Control through Streaming Inference](/202607/22/2607.14695v1-reflex-real-time-vla-control-through-streaming-inference) （9.0/10）
7. [FoMoVLA: Bridging Visual Foresight and Motion Guidance for Vision-Language-Action Models](/202607/22/2607.14739v1-fomovla-bridging-visual-foresight-and-motion-guidance-for-vision-language-action-models) （9.0/10）
8. [Towards Human-like Physical Intelligence: LifelongVision-Language-Action Learning for Robotic Manipulation](/202607/22/2607.14852v1-towards-human-like-physical-intelligence-lifelongvision-language-action-learning-for-robotic-manipulation) （9.0/10）
9. [RoboTTT: Context Scaling for Robot Policies](/202607/22/2607.15275v1-robottt-context-scaling-for-robot-policies) （9.0/10）
10. [Dynamics-Aware Meta-Imitation for Generalization to Unseen Robotic Manipulation](/202607/22/2607.15880v1-dynamics-aware-meta-imitation-for-generalization-to-unseen-robotic-manipulation) （9.0/10）
11. [Closing the Loop in Humanoid VLA: Persistent 3D Object Tokens for Verifiable Loco-Manipulation](/202607/22/2607.18016v1-closing-the-loop-in-humanoid-vla-persistent-3d-object-tokens-for-verifiable-loco-manipulation) （9.0/10）
12. [FM-VLA: Force-based Memory for Vision-Language-Action Models in Contact-Rich Manipulation](/202607/22/2607.18231v1-fm-vla-force-based-memory-for-vision-language-action-models-in-contact-rich-manipulation) （9.0/10）

## 速读区
1. [Worlds in One Demo: A Synthetic Data Engine for Learning Open-World Mobile Manipulation](/202607/22/2607.13154v2-worlds-in-one-demo-a-synthetic-data-engine-for-learning-open-world-mobile-manipulation) （8.0/10）
2. [Generalizable VLA Finetuning via Representation Anchoring and Language-Action Alignment](/202607/22/2607.13429v1-generalizable-vla-finetuning-via-representation-anchoring-and-language-action-alignment) （8.0/10）
3. [Semantic Anchoring for Robotic Action Representations](/202607/22/2607.13597v2-semantic-anchoring-for-robotic-action-representations) （8.0/10）
4. [Learning Forward & Reverse Skills from a Single Unfinished Demonstration for Constrained Manipulation Tasks](/202607/22/2607.13882v1-learning-forward--reverse-skills-from-a-single-unfinished-demonstration-for-constrained-manipulation-tasks) （8.0/10）
5. [Reducing Temporal Redundancy for Efficient Vision-Language-Action Inference](/202607/22/2607.12287v1-reducing-temporal-redundancy-for-efficient-vision-language-action-inference) （7.0/10）
6. [Jetson-PI: Towards Onboard Real-Time Robot Control via Foresight-Aligned Asynchronous Inference](/202607/22/2607.12659v3-jetson-pi-towards-onboard-real-time-robot-control-via-foresight-aligned-asynchronous-inference) （7.0/10）
7. [ExToken: Structured Exploration for Efficient Vision-Language-Action Reinforcement Fine-tuning](/202607/22/2607.12931v1-extoken-structured-exploration-for-efficient-vision-language-action-reinforcement-fine-tuning) （7.0/10）
8. [Distributionally Robust and Safe Imitation Learning](/202607/22/2607.13436v1-distributionally-robust-and-safe-imitation-learning) （7.0/10）
9. [UR-VC: Unsupervised Robotic Value Correction for Time-Derived Progress Proxies](/202607/22/2607.12892v1-ur-vc-unsupervised-robotic-value-correction-for-time-derived-progress-proxies) （6.0/10）
10. [Exploratory, Communicative, and Deployable: Vision-Driven Embodied Agents for Open-World Mobile Manipulation](/202607/22/2607.13653v1-exploratory-communicative-and-deployable-vision-driven-embodied-agents-for-open-world-mobile-manipulation) （6.0/10）
11. [Zero2Skill: Bootstrapping Robot Skills through Autonomous Data Collection, Training, and Deployment](/202607/22/2607.14047v2-zero2skill-bootstrapping-robot-skills-through-autonomous-data-collection-training-and-deployment) （6.0/10）

---
使用键盘方向键可在日报/论文之间快速切换。
