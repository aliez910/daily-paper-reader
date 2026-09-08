---
title: "FLARE: A Failure-Aware Framework for Autonomous Correction and Recovery in Visual-Language Robotic Manipulation"
title_zh: "FLARE:面向视觉-语言机器人操纵的失败感知自主修正与恢复框架"
authors: "Zhao, Ganlong, Tang, Zijia, Chen, Xingping, Kuang, Zhanghui, Tian, Ye, Li, Guanbin"
date: 2026-06-01
pdf: "https://openaccess.thecvf.com/content/CVPR2026/papers/Zhao_FLARE_A_Failure-Aware_Framework_for_Autonomous_Correction_and_Recovery_in_CVPR_2026_paper.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向复杂长视野操纵VLA模型的失败恢复
tldr: "视觉-语言-动作模型在复杂长视野机器人操纵中容易因执行失败而崩溃,本文提出FLARE框架。该方法通过在训练中注入扰动与桥接片段,并引入重试与重置机制,使VLA具备自主错误恢复能力。实验表明该方法能有效应对漏抓、掉物、碰撞等常见失败,显著提升了基于视觉的模仿学习在复杂机器人任务中的鲁棒性。"
source: CVPR-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 768, \"height\": 917, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 1806, \"height\": 625, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 858, \"height\": 445, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 860, \"height\": 354, \"label\": \"Figure\"}, {\"url\": \"assets/figures/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 873, \"height\": 279, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 1810, \"height\": 415, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 869, \"height\": 241, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/table-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 866, \"height\": 253, \"label\": \"Table\"}, {\"url\": \"assets/tables/cvpr-2026-accepted/cvpr-2026-zhao-flare-a-failure-aware-framework-for-autonomous-correction-and-recovery-in-cvpr-2026-paper/table-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 862, \"height\": 166, \"label\": \"Table\"}]"
motivation: "VLA模型在轨迹单调、无失败数据上训练,难以应对执行错误,鲁棒性差。"
method: "提出FLARE框架,通过扰动注入与桥接片段以及重试-重置机制赋予模型错误恢复能力。"
result: 在长视野操纵任务中显著提升面对常见执行错误时的成功率与鲁棒性。
conclusion: 推动了面向复杂机器人任务的视觉模仿学习在鲁棒性方面的前沿进展。
---

## Abstract
Vision-Language-Action Models (VLAs) have demonstrated significant promise in generalizing to complex, long-horizon robotic manipulation tasks. However, their performance remains brittle, as they are typically trained on trajectory-monotonic, failure-free demonstrations. This reliance on "perfect" data leaves them unable to recover from common execution errors, such as a missed grasp, a dropped object, or an unexpected collision. In this paper, we propose FLARE, a novel framework that endows VLAs with robust error recovery capabilities through a "Retry" and "Reset" paradigm. First, we introduce a "Retry" mechanism by injecting perturbation and bridging segments that decouple robot pose from environment state into demonstrations, enabling the policy to autonomously handle execution deviations. Second, to address critical, state-breaking (OOD) failures, we introduce a "Reset" pipeline. We leverage an MLLM for offline failure analysis to automatically identify OOD states from execution videos. This analysis enables the efficient, targeted collection of a small library of object-centric "Reset" skills, which are trained to restore the environment to a task-valid state. Our full framework integrates these learned policies. At inference, an online MLLM monitor arbitrates between task execution and "Reset" skills. Experiments on challenging, contact-rich manipulation tasks show our approach significantly improves task success and robustness.

---

## 论文详细总结（自动生成）

<think>
We need answer Chinese structured exactly 8 points, detailed but concise, objective, based only supplied text. Need note inconsistencies perhaps date. Need assess resources: no GPU models/quantity/training time. Need experiments counts. Need interpret "9 tasks", 50 trials each = 450 sim trials, 80 real (40 each x2). Baselines 7 listed. Data: 10 demos/task -> 500 augmented, 20 reset each ->500. Ablations hyperparam number unknown from figure perhaps could infer curves but not exact. Need be careful.

Let's deeply analyze paper and likely issues to state.

1 core problem: VLA trained successful monotonic demos, coupling robot pose and env state, success bias, no recovery. ID vs OOD. FLARE resilient autonomy.

2 methodology details:
- Policy πθ(a_t | o_t,I), Markovian, action chunk.
- state s=(s^e, s^r), env states valid trajectory S_task.
- ID env valid, robot pose low-prob. Retry.
- OOD env state unrecoverable, reset.
- Perturbation bridging:
  compose task from subtask segments transformed in scenes, Ttask.
  d_i = perturbation dA random pose and bridging dB interpolation to next action's starting pose.
  Taug = dinit, a0,d0...
  train dB + subsequent a; omit dA target. Linear pos + SLERP rotation.
- Reset:
  execute retry model hundreds episodes; Gemini 2.5 Pro offline analyzes failure videos JSON: error type, target, error group, timestamp. Mine state + reset instruction. Reset demos 10-20 or 20 per skill from logged state, preserve group relative arrangement in varied scenes, augment to 500.
  LoRA adapters for task/reset. π0.5 shared backbone; LM/action expert LoRA, Adam lr 2.5e-4 constant. In deployment online MLLM monitor, ID no prompt/intervention, OOD swap adapter, confirm reset switch back.
Potential formula and algorithm. Explain online monitor? Abstract says online MLLM arbitrates. In methodology says if ID no intervention. OOD swap.

3 experimental design:
RoboMimic 9 contact rich tasks, 9 columns. D0/D1 randomization. Coffee D0/D1, Stack D0/D1, StackThree D0/D1, Threading D0, ThreePiece Assembly D0/D1. 9 task settings. D suffix. Simulation likely MuJoCo (mentions MuJoCo state). 50 trials/task.
Baselines:
OpenVLA; task-conditioned diffusion; subgoal-conditioned LLaVA 1.5 5Hz; motion-conditioned LLaVA reflection; Phoenix; Phoenix-Human upper bound; pi0.5.
Results perhaps useful in section 6. The user asks experiment design, but main conclusions include. We can include benchmark and results.
Real world 2 tasks Piper + RealSense D435i top/wrist, 40 each. Any6D approximate pose estimation, 10 human demos to 50 per task/reset skill. Stack blocks and U insert. Compare π0.5.
Ablations Table 3 four settings? Text says covering four settings but lists Ours, w/o Reset, Reset-Only, Oracle (four). Table omitted Reset-Only row weird. Mention.
Ablation P&B rotation fixed T=.5 and translation fixed R=45 on Coffee D1; best r 30 and t .7, from implementation max 45°, .5 m. Exact sampled values not extracted, don't overclaim. Also figure generation success.
Reset skills 4: lid, pod, T, U; Table 4.
Failure identification 50 videos "for Coffee and ThreePieceAssembly" ambiguous total 50 per? The text: "manually label 50 execution videos for the Coffee and ThreePieceAssembly" could mean 50 videos for each or total. Need flag ambiguity rather than assert. Table reports three tasks? Caption says "on three tasks: Reset/Retry classification, Reset object identification and Timestamp identification" likely three components, not tasks. We can say 50 videos across these two tasks, extraction not clear whether each or total. Metrics.
4 resources:
No hardware/training compute in supplied main text. 500 aug from 10; 20 reset from 500; hyperparameters. No GPU, number, training epochs/duration, inference latency. Gemini proprietary 2.5 Pro external. Robot hardware but not compute. 10 human demos each, real data 10->50.
Potential "loRA train LM and action expert". Fine tuning.
5 number and sufficiency:
Count experiments carefully:
- Primary sim 9 task settings, 50 = 450.
- Hyperparam ablation: two one-dimensional sweeps on Coffee D1, exact number settings unavailable from text; so count not exact.
- reset ablation: four variants? Ours, w/o reset, Reset-only, Oracle. But table has 3 rows. Mention discrepancy. Four tasks/settings (Coffee D0,D1, TPA D0,D1) each variant.
- reset evaluation: 4 skills, likely one aggregate success each and generation efficiency; no trial count stated in main text.
- failure recognition: 50 execution videos across two tasks; three metrics.
- real world 2 tasks x40 =80, each base/ours perhaps 40 each method = 80 trial outcomes per task, 160 method-level arm-level if treating all; report 80 total per task? Usually table 40 trials and both methods evaluated, likely 80 runs per task. We can state two task settings, 40 trials per condition as caption, resulting 80 evaluations per task and 160 method-task evaluations. But perhaps table's 40 trials means each method 40, likely yes. In main text "Table 2 success rates... (40 trials)" and columns baseline/ours means each. So 80 each task. No confidence intervals. This supports sufficiency nuance.
- maybe initial failure mining over hundreds episodes, exact omitted.
- 9 tasks only simulation, 2 real tasks, not broad open world. Hyperparameters over one task, real limited.
- π0.5 vs Phoenix confounded by backbone. Improvement 11.8 over π0.5 partly backbone. We should highlight fair baseline? All methods not same backbone except ours and π0.5. Phoenix uses diffusion/LLaVA, OpenVLA etc. Comparisons don't establish contribution of each component. They do ablation. Phoenix-Human uses human corrections and 100 etc, but comparison maybe not fully fair because privileged human feedback. π0.5 strong baseline but not all. Real only π0.5, no Phoenix/Oracle. Statistical uncertainty absent: one mean percentage over 50 with no variance/CI/significance. D0/D1 unclear exact randomization ranges. Simulation uses privileged state for data mining? They say logged MuJoCo; real uses Any6D. Concern: offline reset reconstruction has simulation privileged states; real approximate. Main text says no privileged coordinates real.
- MLLM labels likely no inter-rater beyond manual 50. Failure identification accuracy and performance downstream; false negative cases can matter.
- selected tasks not severe pose recovery. Some reset skill low 20-24. Online monitor errors (timestamp etc). 
- reset skill library manual seed 20 demonstrations and augmentation; scalability concern.
- MLLM is proprietary, reproducibility issue, prompt only supplement not here. Offline+online perhaps closed loop.
- architecture: adapters selected through language prompt; paper says online MLLM identifies skill and directs swap, not necessarily VLA language prompt. Abstract distinct language prompts. Potential mismatch. We can mention online MLLM monitor likely control overhead. No latency/latency.
- P&B random perturbations generated synthetically using planning/interpolation, and training excludes perturbation action. Validity/generation noise tradeoff, but no detailed ablations of data size or perturbation target omission.
- no task horizon / compute metrics.
- simulation benchmark (RoboMimic) maybe old; 9 tasks. "MimicGen 10 demos to 500". Use LoRA.
- perhaps result numbers: 84.0 vs pi0.5 72.2, +11.8 percentage points; Phoenix 57.8 +26.2 pp. Ours beats Phoenix-Human 78.9 by 5.1 pp. 8/9 SOTA; exception Threading D0: Ours 72 vs Phoenix-Human 100, π0.5 42, Phoenix 68. Table says Ours 72. It is 4th? Phoenix-Human 100, Phoenix 68, subgoal 24 etc. State not best. Need present perhaps conclusion. D1 improvements vs π0.5:
Coffee +22, Stack +8, StackThree +6, TPA +12, Threading D1 +30. D1 pronounced. Coffee D0 +14, Stack D0 0, StackThree D0 +10, TPA D0 +4. Could mention.
Real results 75 vs62.5 +12.5; 55 vs45 +10. Table.
Ablation:
Ours avg across four: (96+78+62+58)/4=73.5. w/o reset (92+74+60+54)=70; difference 3.5 as paper. Oracle (100+90+68+64)=80.5, +7 over ours. Reset-only (88+64+60+50)=65.5 perhaps not in table but described. Interesting Ours-Oracle 80.5.
P&amp;B sensitivity best 30°, 0.7; implementation max 45° and 0.5m? Figure says best t=.7, while implementation says max translation .5m. Inconsistency! Important. Text implementation: "max 45° rotation, 0.5m translation"; sensitivity says best t=0.7. Could be figure "translation value" unit maybe m? If max 0.5 but 0.7 impossible. Need flag as internal inconsistency/ambiguous units. Very useful in objective summary. Maybe Figure labels extraction could indicate t=.7 no units. Should explicitly say 0.7 according to paper but implementation caps 0.5m, unit or range inconsistent. Could avoid overemphasizing if OCR issue? It says max 45°, 0.5m translation, best t =0.7. That's direct. Mention.
- Hyperparam larger variance improves until excessive, tradeoff. Data generation efficiency.
- Reset success:
Coffee lid 84, pod 24; TPA T 88, U 20. Efficiency 83.7, 11.6, 48.6,5.9. This reveals limitations.
- MLLM failure case:
Coffee reset/retry 88, reset object 88, timestamp78. TPA 96,78,66. Oracle human instructions improvement 7.
- Human demos 20 for each reset; "e.g. 10-20" methods; implementation 20. Real 10 and to50.
- number reset skills? Coffee 2, TPA2. Task library likely K; no exact total. failure mining over hundreds. Don't overstate.

Need obey final line exact （完）. No text after.

We should organize:
# 总结 maybe.
## 1...
Use bullets.
Need language concise info complete. Maybe "说明：仅基于提供文本". Not requested but could mention publication date weird? No need. Could note source says 2026.

Let's craft detailed.

Section 1:
- VLA generalization, failure.
- data issue: success-only, trajectory-monotonic, correlation P(sr|se,Ddemo), ID and OOD.
- objective.
Maybe define "整体含义" dual mechanisms and resilience.

Section 2:
- taxonomy
- policy formula
- Retry data generation pipeline
- Reset pipeline
- Training and inference
- Important implementation.
Could put exact formula:
πθ(at | ot,I), at∈ A^K (action sequence). State decomposition. Definitions.
- Perturbation and bridging d_i=(dA_i,dB_i). T_aug. Targets.
- MLLM JSON fields.
- LoRA and hyperparams.
- Note Gemini 2.5 Pro.
Potential "offline failure analysis using privileged logs": In sim state logs, error group. Real approximate. Mention.
- At inference ID left to policy; OOD online monitor swaps.

Section 3:
- Benchmark. List tasks and variants.
- data generation and trials.
- baselines.
- ablations and real world.
Could include outcomes perhaps in point 6. But experiment design should mention metrics. Success rate.

Section 4:
- no GPU count, model size, epochs, training duration/inference. Mention exact known compute/optimization.
- Hardware: Piper, D435i, Any6D. Data volume.
- Gemini.
- training on 500 augmented, reset.
- resource enough? no.

Section 5:
"实验数量与充分性" with table-like bullet counts:
1 sim main
2 hyperparam
3 reset ablation
4 reset skills
5 failure classification
6 real
7 failure collection hundreds.
Potential trial-level estimate:
Primary = 9×50=450.
Real = if 40 each method on each task: 2×2×40=160; paper table labels 40 trials perhaps ambiguity. Better phrase: "每个任务列出基线与 FLARE 各40次（按表格通常含义），共160次；若‘40 trials’指总计，则需正文澄清." But in summary, don't be too confusing? Objective. We can say 2 tasks, each method 40 based on table. It is likely.
Reset success trial count not given. Hyperparam exact grid missing. Failure video count ambiguous.
- "实验数量中等偏广; coverage but not enough for open-world; no CI, etc."
- fairness: same benchmark, 50 trials; but backbone differences, Phoenix-Human human, data amounts differ, LoRA config, sim vs real. Ablations helps. π0.5 is common backbone for ours; comparisons to π0.5 fair. But Phoenix based different policy. Phoenix-Human is upper bound not directly fair.
- Internal inconsistency max translation. Also Table 3 text says four settings but table shows only three? It does show Ours w/o Reset, Ours, Ours-Oracle, while text lists Reset-Only. We can say text discusses Reset-Only but rendered Table 3 doesn't list it, so reproducibility/audit issue. Good.
- "No confidence intervals" important.
- "MimicGen from 10 demos, 500" baseline generated perhaps all.

Section 6:
- 84.0, 8/9, + etc.
- exception.
- real.
- D1 robustness.
- ablation.
- MLLM.
- P&B.
- oracle gap.
- main conclusion.

Section 7:
- reframes failure as data / taxonomy.
- data-efficient dual recovery.
- decouples robot pose.
- MLLM dual role and mined error groups.
- modular LoRA scaling.
- sim+real.
Need not overpraise.

Section 8:
- compute/repro
- coverage
- privileged sim mining / timestamp errors
- reset complexity
- MLLM dependency
- backbone and fairness
- metric/statistics
- no latency/horizon/calibration
- hyperparam inconsistency
- applicability.
Could be detailed but concise.

Need ensure final line exactly `（完）`. No citation required.

Let's formulate in Chinese polished.

Potential date says CVPR 2026 paper. No need.

Let's inspect all details for exact title. Chinese translation "操纵" perhaps manipulation is 操作. We can call 机器人操作.

Could mention MLLM means multimodal large language model. Use VLA.

No external claims.

Let's ensure "number experiments" not claim 8/9 from main but okay.
Table 1 means 9 columns (task variants). They say 9 manipulation tasks but with D0/D1 variants; technically 9 task settings. Paper says 9 tasks. We can distinguish "9个任务/任务设置（含D0/D1）". There are Coffee, Stack, StackThree, Threading, ThreePiece Assembly; variants. Count:
Coffee2 + Stack2 + StackThree2 + Threading1 + TPA2 =9.
Main text says 9 tasks, but actually 5 task families/9 settings. We can phrase.

"RoboMimic Simulation". 500 per task from 10 using MimicGen; retry augmentation also. They "generated 500 augmented demonstrations per task from 10 initial human demos using Mimicgen". The P&B maybe integrated; wording could mean 500 final. No need parse.

"fine-tuned language model and action expert of π0.5 with LoRA". Mention no exact rank. LR.

Real: "10 human demos and augmented to 50 for each task/reset skill." likely per task. Any6D.
No "Piper arm model" perhaps Piper robot arm, not model.

Formula in paper: at ∼ πθ(·|ot,I), with action chunk. State decomposition. Use math Markdown.
Definitions.

Perturbations: random joint velocities/end effector. bridging planner-free interpolation. "not used as training targets" important.
Potential synthetic trajectories can be invalid. The paper says benefit outweighs rare invalid. Include as method but also limitation.

Reset:
- all execution videos including success/fail over hundreds.
- JSON exact.
- error group semantic asset preserving internal relative poses.
- mined exact sim state at timestamp, 20 demos.
- reset only after confirmation.
- online monitor and active adapter.

Potential weirdness: "MLLM monitor observes VLA's execution" and ID "No intervention needed". It may not explicitly detect ID because if it detects OOD. Fine.

Section 4 compute: Do not say no compute if paper supplementary not provided; phrase supplied text. They request based on content; "提供的正文未明确". Good.
- no number GPUs, model size, epochs, wall-clock, energy. No FLOPs. No inference frequency? Subgoal baseline 5 Hz but not FLARE. Could mention.
- "数百 episodes" and 50 eval. Data collection human labor: 10 per task, 20 per reset. Useful resource.
- Gemini external resource.
- real robot sensor.

Fairness: They compare all at 50 trials? likely yes. No variance.
- Hyperparameter optimized? They may choose P&B r and t using Coffee D1, then same across tasks. Good.
- Same random seeds? not stated. Mention.
- "D1 improvement more pronounced" supports.

Let's make answer not excessively huge but detailed. Desired 5. Maybe 2500-3500 Chinese chars. User wants detailed. We can do ~3000-4500 Chinese chars. Use subbullets.

Let's draft.

Need perhaps calculate percentage points correctly:
84.0 - 57.8=26.2 pp.
84.0 -72.2=11.8 pp.
84.0 -78.9=5.1 pp.
Real +12.5 and +10 pp.
Ablation avg difference 3.5 pp.
Oracle +7.
Best r30 and t0.7.
Failure object reset lower.
Threading D0 72 vs Phoenix 68 but below Phoenix-Human100 and π0.5? Wait π0.5 is42, so ours above. "not best" only human. yes.
Main claims "outperforms Phoenix previous leading" 72 vs68. Good.

Fairness issue: OpenVLA baseline and others may use architectures not π0.5; 500 demonstrations perhaps all? Main
</think>
