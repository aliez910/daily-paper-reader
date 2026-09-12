---
title: "HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning"
title_zh: HiPolicy：面向策略学习的分层多频动作分块框架
authors: "Jiyao Zhang, Zimu Han, Junhan Wang, Xionghao Wu, Shihong Lin, Jinzhou Li, Hongwei Fan, Ruihai Wu, Dongjiang Li, Hao Dong"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/10308.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 通过分层多频动作分块实现模仿学习中的细粒度闭环控制
tldr: 针对机器人模仿学习中长时序依赖建模与细粒度闭环控制难以兼得的根本矛盾，本文提出了 HiPolicy 框架。该方法采用分层多频动作分块策略，在不同频率上联合预测动作序列以同时刻画高层粗粒度规划与底层精确反应式动作。它从与各频率对齐的历史观测中提取并融合分层特征，并引入基于熵的执行机制根据动作不确定性自适应平衡规划与控制。实验表明 HiPolicy 在需要长时序推理与反应式闭环行为的复杂操控任务上取得显著性能提升。该工作为长时域模仿学习中的分层闭环控制提供了新思路。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 3795, \"height\": 2257}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 1545, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 1305, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 1249, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 880, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 1167, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 3758, \"height\": 2221}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 1902, \"height\": 1066}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-009.webp\", \"caption\": \"\", \"page\": 1, \"index\": 9, \"width\": 1061, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-010.webp\", \"caption\": \"\", \"page\": 1, \"index\": 10, \"width\": 938, \"height\": 324}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-011.webp\", \"caption\": \"\", \"page\": 1, \"index\": 11, \"width\": 497, \"height\": 323}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-012.webp\", \"caption\": \"\", \"page\": 5, \"index\": 12, \"width\": 797, \"height\": 549}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-013.webp\", \"caption\": \"\", \"page\": 5, \"index\": 13, \"width\": 964, \"height\": 543}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-014.webp\", \"caption\": \"\", \"page\": 5, \"index\": 14, \"width\": 798, \"height\": 549}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-015.webp\", \"caption\": \"\", \"page\": 5, \"index\": 15, \"width\": 452, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-016.webp\", \"caption\": \"\", \"page\": 5, \"index\": 16, \"width\": 478, \"height\": 649}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-017.webp\", \"caption\": \"\", \"page\": 5, \"index\": 17, \"width\": 451, \"height\": 599}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-018.webp\", \"caption\": \"\", \"page\": 5, \"index\": 18, \"width\": 654, \"height\": 672}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-019.webp\", \"caption\": \"\", \"page\": 8, \"index\": 19, \"width\": 1085, \"height\": 349}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-020.webp\", \"caption\": \"\", \"page\": 8, \"index\": 20, \"width\": 902, \"height\": 277}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-021.webp\", \"caption\": \"\", \"page\": 8, \"index\": 21, \"width\": 1764, \"height\": 965}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-022.webp\", \"caption\": \"\", \"page\": 13, \"index\": 22, \"width\": 1097, \"height\": 842}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-023.webp\", \"caption\": \"\", \"page\": 13, \"index\": 23, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-024.webp\", \"caption\": \"\", \"page\": 13, \"index\": 24, \"width\": 1041, \"height\": 788}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-025.webp\", \"caption\": \"\", \"page\": 13, \"index\": 25, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-026.webp\", \"caption\": \"\", \"page\": 13, \"index\": 26, \"width\": 1132, \"height\": 881}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-027.webp\", \"caption\": \"\", \"page\": 13, \"index\": 27, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-028.webp\", \"caption\": \"\", \"page\": 13, \"index\": 28, \"width\": 1050, \"height\": 798}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-029.webp\", \"caption\": \"\", \"page\": 13, \"index\": 29, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-030.webp\", \"caption\": \"\", \"page\": 13, \"index\": 30, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-031.webp\", \"caption\": \"\", \"page\": 13, \"index\": 31, \"width\": 1059, \"height\": 807}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-032.webp\", \"caption\": \"\", \"page\": 13, \"index\": 32, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-033.webp\", \"caption\": \"\", \"page\": 13, \"index\": 33, \"width\": 1096, \"height\": 844}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-034.webp\", \"caption\": \"\", \"page\": 13, \"index\": 34, \"width\": 1013, \"height\": 761}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-035.webp\", \"caption\": \"\", \"page\": 13, \"index\": 35, \"width\": 1077, \"height\": 825}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-036.webp\", \"caption\": \"\", \"page\": 13, \"index\": 36, \"width\": 1013, \"height\": 761}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-037.webp\", \"caption\": \"\", \"page\": 13, \"index\": 37, \"width\": 1096, \"height\": 843}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-038.webp\", \"caption\": \"\", \"page\": 13, \"index\": 38, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-039.webp\", \"caption\": \"\", \"page\": 13, \"index\": 39, \"width\": 1051, \"height\": 797}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-040.webp\", \"caption\": \"\", \"page\": 13, \"index\": 40, \"width\": 1059, \"height\": 807}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-041.webp\", \"caption\": \"\", \"page\": 13, \"index\": 41, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-042.webp\", \"caption\": \"\", \"page\": 13, \"index\": 42, \"width\": 1022, \"height\": 770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-043.webp\", \"caption\": \"\", \"page\": 13, \"index\": 43, \"width\": 1013, \"height\": 761}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-044.webp\", \"caption\": \"\", \"page\": 13, \"index\": 44, \"width\": 553, \"height\": 232}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-045.webp\", \"caption\": \"\", \"page\": 13, \"index\": 45, \"width\": 1106, \"height\": 852}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-046.webp\", \"caption\": \"\", \"page\": 13, \"index\": 46, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-047.webp\", \"caption\": \"\", \"page\": 13, \"index\": 47, \"width\": 1023, \"height\": 769}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-048.webp\", \"caption\": \"\", \"page\": 13, \"index\": 48, \"width\": 1014, \"height\": 760}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-049.webp\", \"caption\": \"\", \"page\": 13, \"index\": 49, \"width\": 1069, \"height\": 815}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-050.webp\", \"caption\": \"\", \"page\": 13, \"index\": 50, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-051.webp\", \"caption\": \"\", \"page\": 13, \"index\": 51, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-052.webp\", \"caption\": \"\", \"page\": 13, \"index\": 52, \"width\": 1078, \"height\": 824}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-053.webp\", \"caption\": \"\", \"page\": 13, \"index\": 53, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-054.webp\", \"caption\": \"\", \"page\": 13, \"index\": 54, \"width\": 1023, \"height\": 769}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-055.webp\", \"caption\": \"\", \"page\": 13, \"index\": 55, \"width\": 1014, \"height\": 760}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-056.webp\", \"caption\": \"\", \"page\": 13, \"index\": 56, \"width\": 1041, \"height\": 787}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-057.webp\", \"caption\": \"\", \"page\": 13, \"index\": 57, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-058.webp\", \"caption\": \"\", \"page\": 13, \"index\": 58, \"width\": 1077, \"height\": 825}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-059.webp\", \"caption\": \"\", \"page\": 13, \"index\": 59, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-060.webp\", \"caption\": \"\", \"page\": 13, \"index\": 60, \"width\": 1022, \"height\": 770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-061.webp\", \"caption\": \"\", \"page\": 13, \"index\": 61, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-062.webp\", \"caption\": \"\", \"page\": 13, \"index\": 62, \"width\": 1022, \"height\": 770}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-063.webp\", \"caption\": \"\", \"page\": 13, \"index\": 63, \"width\": 1013, \"height\": 761}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-064.webp\", \"caption\": \"\", \"page\": 13, \"index\": 64, \"width\": 1040, \"height\": 788}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-065.webp\", \"caption\": \"\", \"page\": 13, \"index\": 65, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-066.webp\", \"caption\": \"\", \"page\": 13, \"index\": 66, \"width\": 1060, \"height\": 806}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-067.webp\", \"caption\": \"\", \"page\": 13, \"index\": 67, \"width\": 1059, \"height\": 806}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-068.webp\", \"caption\": \"\", \"page\": 13, \"index\": 68, \"width\": 1651, \"height\": 1238}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-069.webp\", \"caption\": \"\", \"page\": 13, \"index\": 69, \"width\": 1022, \"height\": 769}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-070.webp\", \"caption\": \"\", \"page\": 13, \"index\": 70, \"width\": 1013, \"height\": 760}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-071.webp\", \"caption\": \"\", \"page\": 13, \"index\": 71, \"width\": 512, \"height\": 398}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-072.webp\", \"caption\": \"\", \"page\": 13, \"index\": 72, \"width\": 671, \"height\": 510}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-073.webp\", \"caption\": \"\", \"page\": 13, \"index\": 73, \"width\": 1014, \"height\": 760}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-074.webp\", \"caption\": \"\", \"page\": 13, \"index\": 74, \"width\": 1078, \"height\": 825}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-075.webp\", \"caption\": \"\", \"page\": 15, \"index\": 75, \"width\": 3148, \"height\": 657}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-076.webp\", \"caption\": \"\", \"page\": 15, \"index\": 76, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-077.webp\", \"caption\": \"\", \"page\": 15, \"index\": 77, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-078.webp\", \"caption\": \"\", \"page\": 15, \"index\": 78, \"width\": 457, \"height\": 365}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-079.webp\", \"caption\": \"\", \"page\": 15, \"index\": 79, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-080.webp\", \"caption\": \"\", \"page\": 15, \"index\": 80, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-081.webp\", \"caption\": \"\", \"page\": 15, \"index\": 81, \"width\": 457, \"height\": 364}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-082.webp\", \"caption\": \"\", \"page\": 15, \"index\": 82, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-083.webp\", \"caption\": \"\", \"page\": 15, \"index\": 83, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-084.webp\", \"caption\": \"\", \"page\": 15, \"index\": 84, \"width\": 738, \"height\": 578}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-3ec0ca5d1e66dae33bac6029/fig-085.webp\", \"caption\": \"\", \"page\": 15, \"index\": 85, \"width\": 456, \"height\": 365}]"
motivation: 固定频率动作分块难以同时兼顾长时序依赖建模与细粒度闭环控制。
method: 提出分层多频动作分块框架，联合预测不同频率动作序列并融合历史特征，引入熵引导执行机制。
result: 在需要长时序与反应式控制的复杂操控任务上显著优于现有动作分块方法。
conclusion: HiPolicy 有效统一了模仿学习中的长时序规划与细粒度闭环控制。
---

## Abstract
Robotic imitation learning faces a fundamental trade-off be-tween modeling long-horizon dependencies and enabling fine-grained closed-loop control. Existing fixed-frequency action chunking approaches strug-gle to achieve both. Building on this insight, we propose HiPolicy, ahierarchical multi-frequency action chunking framework that jointly pre-dicts action sequences at different frequencies to capture both coarsehigh-level plans and precise reactive motions. We extract and fuse hi-erarchical features from history observations aligned to each frequencyfor multi-frequency chunk generation, and introduce an entropy-guidedexecution mechanism that adaptively balances long-horizon planningwith fine-grained control based on action uncertainty. Experiments ondiverse simulated benchmarks and real-world manipulation tasks showthat HiPolicy can be seamlessly integrated into existing 2D and 3D gen-erative policies, delivering consistent improvements in performance whilesignificantly enhancing execution efficiency.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "HiPolicy: Hierarchical Multi-Frequency Action Chunking for Policy Learning" organized in a specific structure with 8 main points. Let me carefully analyze the paper and produce a structured Markdown summary.

Let me go through the paper systematically:

1. Core problem: The fundamental trade-off between long-horizon dependency modeling and fine-grained closed-loop control in robotic imitation learning. Fixed-frequency action chunking cannot achieve both.

2. Method: HiPolicy - hierarchical multi-frequency action chunking framework
- Jointly predicts action sequences at multiple frequencies
- Extracts and fuses hierarchical features from history observations
- Entropy-guided execution mechanism
- Key components:
  - Hierarchical feature extraction
  - Hierarchical FiLM fusion
  - Global feature fusion (with cross-attention and CLS token)
  - Entropy estimation via parallel sampling
  - Adaptive frequency selection

3. Experiments: 
- RoboTwin 1.0 (12 tasks)
- RoboTwin 2.0 (9 tasks)
- 8 real-world tasks on Franka Panda with Robotiq 2F-85 gripper, Zed 2i cameras, Zed Mini camera
- Baselines: DP (Diffusion Policy), DP3 (3D Diffusion Policy)

4. Resources: 
- RTX 4090 GPU mentioned for runtime evaluation
- No explicit training time mentioned

5. Experimental volume:
- 21 simulation tasks total
- 8 real-world tasks
- Ablation studies (4 components)
- Sample times ablation
- Runtime/memory comparison
- Acceleration experiment
- 100 episodes per simulation task
- 10 trials per real-world task

6. Main conclusions:
- 62% improvement over DP, 44% over DP3
- 42% improvement on real-world with 14% faster execution
- 25% reduction in executed steps with 24% reduction in wall-clock time

7. Highlights:
- Novel hierarchical multi-frequency framework
- Entropy-guided adaptive execution
- Can be integrated into existing 2D and 3D policies
- Modest computational overhead

8. Limitations:
- Limited to relatively small models and datasets
- No integration with large VLA models
- Authors suggest extending to large-scale multimodal settings

Let me write this in Chinese with Markdown formatting.</think>

# HiPolicy 论文结构化总结

## 一、核心问题与研究动机

- **根本矛盾**：机器人模仿学习（Imitation Learning, IL）在**长时序依赖建模**与**细粒度闭环控制**之间存在难以调和的权衡。
- **现有方法的瓶颈**：基于扩散模型的生成式策略（如 Diffusion Policy、DP3、ACT）采用**固定频率动作分块（action chunking）**，存在两大痛点：
  - **误差累积**：单步预测误差在长序列中不断放大，导致任务失败。
  - **频率-粒度二选一**：低频分块利于建模长时序依赖但缺乏闭环控制精度；高频分块控制精细但视野受限。
- **关键灵感来源**：人类运动控制研究表明，复杂动作天然包含**多频率成分**——低频慢动作编码高层意图，高频快动作实现精确反应与调整。
- **核心研究问题**：能否借鉴这一分层多频结构，统一模仿学习中的长时序规划与细粒度闭环控制？

---

## 二、提出方法：HiPolicy 框架

### 2.1 整体思路

- 将传统固定频率动作分块扩展为**分层多频动作分块**：在同一 chunk 内**联合预测多个频率**（M 个频率成分 f₁, …, f_M）的动作序列，并融合各频率对应的历史观测特征。
- 推理时通过**熵引导的自适应执行**机制，按不确定性动态选择执行频率。

### 2.2 关键模块

1. **分层特征提取（Hierarchical Feature Extraction）**
   - 从同一观测历史中按不同频率采样帧序列
   - 视觉输入支持 2D 图像或 3D 点云；本体感知（关节位置、速度、夹爪状态）通过 MLP 编码
   - 得到多个频率的观测特征 𝒻_O^{f_m}

2. **分层 FiLM 融合（Hierarchical FiLM Fusion）**
   - 对每个频率成分，使用对应频率的观测特征作为条件，对相应频率的动作特征做 FiLM 调制
   - 公式：𝓕_A^h ← ⊕_{m=1}^M FiLM(𝓕_O^{f_m}, 𝓕_A^{f_m})
   - 实现不同时间分辨率下的观测-动作对齐

3. **全局特征融合（Global Feature Fusion）**
   - 通过**跨注意力（Cross-Attention）**+ **CLS Token** 促进跨频率信息交流
   - 先进行 frequency fusion 得到全局特征，再与局部特征拼接
   - 最后再次用 FiLM 注入观测条件

4. **熵引导自适应执行（Entropy-Guided Adaptive Execution）**
   - 对每个 chunk 独立并行采样 N=100 次，估计动作分布
   - 将每个动作建模为高斯分布，用样本均值/方差估计 Shannon 熵：Ĥ^j = log(√(2πe)·σ̂^j)
   - 取所有频率与时间步的平均熵作为整体熵指标
   - 通过预设阈值表自适应选择执行频率：低熵（稳定）→ 高频精细控制；高熵（不确定）→ 低频加速规划

### 2.3 架构与训练

- 基于 1D-CNN U-Net 的扩散模型，整体框架可无缝嵌入 DP 和 DP3
- 训练过程遵循 Diffusion Policy 范式（详见论文附录 C）

---

## 三、实验设计

### 3.1 仿真基准

| 基准 | 任务数 | 特点 |
|------|--------|------|
| **RoboTwin 1.0** | 12 个任务 | 数字孪生框架，涵盖从精细到长时序操控 |
| **RoboTwin 2.0** | 9 个任务 | 自动化真实合成数据生成，强域随机化 |

- 任务分类：
  - **精确任务**（如堆叠方块、扫码盖章）：末端执行器位姿容差小
  - **非精确任务**（如瓶子放置）：容差较宽松
- 任务按 demo steps 排序，最长 665 步（Blocks stack hard）

### 3.2 真实场景

- **机器人**：Franka Emika Panda + Robotiq 2F-85 夹爪
- **相机**：2 个 Zed 2i（第三人称）+ 1 个 Zed Mini（腕部第一人称），沿用 DROID 设置
- **任务数**：8 个（放碗、关微波炉、收纳蔬菜、包装、扫板、堆方块、按下烤面包机按钮、开微波炉）

### 3.3 对比基线

- **DP（Diffusion Policy, Chi et al. 2023）**：2D RGB 输入
- **DP3（3D Diffusion Policy, Ze et al. 2024）**：3D 点云输入
- HiPolicy 分别与 DP 和 DP3 集成对比

---

## 四、资源与算力

- **GPU**：实验运行在 **NVIDIA RTX 4090**（用于推理耗时、显存、墙钟时间测量）
- **训练时长**：论文**未明确给出**训练时长、epoch 数或数据规模等细节（仅提及"固定 epoch 训练，使用相同数据划分"）
- **推理开销**（RTX 4090 测得）：
  - DP：6560 MB VRAM，100 ms/inference
  - DP + HiPolicy：7457 MB VRAM（+897 MB），108 ms/inference（+8 ms）
- 熵估计采样 N 从 1 增至 100 仅引入 2.0 ms 延迟与 63 MB 显存开销

---

## 五、实验数量与充分性

### 5.1 实验规模

- **仿真**：21 个任务 × 100 episodes/任务 = **2100 次评估**
- **真实场景**：8 个任务 × 10 trials/任务 = **80 次真实实验**
- **消融实验**：
  - 分层条件消融（High / Low / Hier.）
  - 融合模块消融（w/o Fusion）
  - 分层频率结构消融（w/o Hier.）
  - 熵引导执行消融（DP / DP+HiPolicy w/o EG / DP+HiPolicy）
  - 采样次数 N 消融（1, 5, 10, 100, 500）
  - 运行时间与显存对比
  - 加速实验

### 5.2 公平性与充分性

- ✅ 统一超参数（论文附录 D），保证基线与改进方法可比
- ✅ 任务按 demo steps 排序并按精确/非精确分类，覆盖了不同 horizon 与控制粒度
- ✅ 同时验证 2D（DP）与 3D（DP3）模态，泛化性较好
- ✅ 仿真与真实场景双重验证
- ⚠️ 真实场景每个任务仅 10 次评估，统计意义有限
- ⚠️ 仅对比 DP/DP3 两个基线，未与 ACT、H3DP、Reactive Diffusion Policy 等近期分层方法做直接对比

---

## 六、主要结论与发现

### 6.1 仿真结果（RoboTwin 1.0 + 2.0）

| 基线 | 平均成功率 | HiPolicy 提升 |
|------|-----------|--------------|
| DP   | 37%       | **60% (+62%)** |
| DP3  | 41%       | **59% (+44%)** |

- 精确任务平均：DP 22% → 45%（+105%）；DP3 28% → 53%（+89%）
- 非精确任务平均：DP 59% → 79%（+34%）；DP3 59% → 70%（+19%）
- 提升最显著：Block hammer beat（DP 0→67）、Stamp seal（DP3 15→74）、Block handover（DP 61→100）

### 6.2 真实场景结果

- 平均成功率：DP 60% → **HiPolicy 85%（+42%）**
- 平均执行步数：129 → 111（**减少 14%**）
- 关微波炉任务：DP 成功率 0%（未锁紧卡扣），HiPolicy 100%

### 6.3 效率结论

- 执行步数减少 25%，墙钟时间减少 24%，但每步推理仅多 8 ms
- 熵曲线分析（图 6）证实：低熵对应精确动作（如夹取），高熵对应粗略动作（如接近），与执行策略一致

---

## 七、方法与实验的亮点

- **🎯 问题切入精准**：直接抓住模仿学习中"长时序 vs 闭环精度"的根本矛盾，从人类运动控制中汲取灵感
- **🔧 即插即用**：HiPolicy 可无缝集成到现有 2D/3D 生成式策略（DP、DP3），无需重新设计架构
- **🧠 熵引导自适应执行**：将策略不确定性作为频率选择的"门控信号"，兼具稳健性与效率
- **📊 实验覆盖全面**：同时覆盖精确/非精确、短/长/超长 horizon、2D/3D 模态、仿真/真实场景
- **💡 消融充分**：分层条件、融合模块、频率结构、熵引导、采样次数等关键设计均有独立验证
- **⚖️ 效率权衡合理**：额外计算开销极小（+8 ms, +897 MB），换来显著性能与速度提升
- **📈 熵曲线可解释性**：图 6 可视化展示熵与任务阶段的对应关系，增强结果可信度

---

## 八、不足与局限

### 8.1 方法层面

- **未应用于大规模模型**：未集成到 VLA（如 π0、OpenVLA）等大型视觉-语言-动作框架，作者在 Limitation 中明确承认
- **频率数量与选择依赖预设**：M 个频率与熵阈值需手动设定，缺乏自适应机制
- **熵估计开销**：需要 N=100 次并行采样才能获得稳定估计，增加了部署复杂度
- **未处理多模态动作分布**：当底层动作分布非高斯时，熵估计可能不准确

### 8.2 实验层面

- **真实实验评估次数偏少**：每任务仅 10 trials，难以排除随机性影响
- **基线范围有限**：仅对比 DP/DP3，未与 ACT、H3DP、Reactive Diffusion Policy、CARP、Dense Policy 等同期分层/分块方法直接比较
- **训练细节缺失**：未报告训练时长、数据规模、epoch 数等关键信息，复现性受限
- **任务分布偏差**：真实任务集中在 Franka 桌面场景，未涵盖移动机器人、户外环境等
- **效率评估口径**：性能提升部分来自执行步数减少，需进一步澄清这是真正"加速"还是"任务更早完成"

### 8.3 适用性限制

- 对硬件平台、控制频率假设较强（默认 f_ctrl=15 Hz）
- 真实场景中强依赖精确的本体感知与外参标定
- 多频率特征融合引入额外参数，对小数据集可能存在过拟合风险

---

（完）
