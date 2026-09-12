---
title: "StructPolicy: Structure-Guided Imitation Learning Robust to Visual Domain Shifts"
title_zh: "StructPolicy:面向视觉域偏移鲁棒的结构引导模仿学习方法"
authors: "Zehao Du, Jiude Wei, Cewu Lu, Jianhua Sun"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/4858.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 模仿学习从视觉输入到动作的映射
tldr: "模仿学习通过从视觉输入到动作的映射实现机器人操作,但在光照、视角等视觉域偏移下鲁棒性差。本文提出StructPolicy,构建编码细粒度物体结构的Structure Map,该结构在视觉域变化下保持不变且对操作至关重要。该方法通过StructCon自动构建模块与StructEncoder编码器将结构信息融入模仿学习策略。该工作显著提升了视觉模仿学习在复杂机器人操作任务中的鲁棒性,具有重要实用价值。"
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 678, \"height\": 702}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 576, \"height\": 576}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 679, \"height\": 248}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 748, \"height\": 507}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 1045, \"height\": 701}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 576, \"height\": 575}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 352, \"height\": 352}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 679, \"height\": 702}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 575, \"height\": 575}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-010.webp\", \"caption\": \"\", \"page\": 2, \"index\": 10, \"width\": 576, \"height\": 575}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-011.webp\", \"caption\": \"\", \"page\": 2, \"index\": 11, \"width\": 679, \"height\": 701}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-012.webp\", \"caption\": \"\", \"page\": 2, \"index\": 12, \"width\": 575, \"height\": 575}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-013.webp\", \"caption\": \"\", \"page\": 2, \"index\": 13, \"width\": 679, \"height\": 701}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-014.webp\", \"caption\": \"\", \"page\": 2, \"index\": 14, \"width\": 575, \"height\": 576}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-015.webp\", \"caption\": \"\", \"page\": 5, \"index\": 15, \"width\": 564, \"height\": 491}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-016.webp\", \"caption\": \"\", \"page\": 5, \"index\": 16, \"width\": 650, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-017.webp\", \"caption\": \"\", \"page\": 5, \"index\": 17, \"width\": 426, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-018.webp\", \"caption\": \"\", \"page\": 5, \"index\": 18, \"width\": 553, \"height\": 455}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-019.webp\", \"caption\": \"\", \"page\": 5, \"index\": 19, \"width\": 428, \"height\": 590}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-020.webp\", \"caption\": \"\", \"page\": 5, \"index\": 20, \"width\": 604, \"height\": 262}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-021.webp\", \"caption\": \"\", \"page\": 6, \"index\": 21, \"width\": 846, \"height\": 893}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-022.webp\", \"caption\": \"\", \"page\": 6, \"index\": 22, \"width\": 634, \"height\": 530}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-023.webp\", \"caption\": \"\", \"page\": 6, \"index\": 23, \"width\": 659, \"height\": 203}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-024.webp\", \"caption\": \"\", \"page\": 6, \"index\": 24, \"width\": 500, \"height\": 305}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-025.webp\", \"caption\": \"\", \"page\": 6, \"index\": 25, \"width\": 536, \"height\": 236}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-026.webp\", \"caption\": \"\", \"page\": 6, \"index\": 26, \"width\": 535, \"height\": 267}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-027.webp\", \"caption\": \"\", \"page\": 6, \"index\": 27, \"width\": 829, \"height\": 872}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-028.webp\", \"caption\": \"\", \"page\": 10, \"index\": 28, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-029.webp\", \"caption\": \"\", \"page\": 10, \"index\": 29, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-030.webp\", \"caption\": \"\", \"page\": 10, \"index\": 30, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-031.webp\", \"caption\": \"\", \"page\": 10, \"index\": 31, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-032.webp\", \"caption\": \"\", \"page\": 10, \"index\": 32, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-033.webp\", \"caption\": \"\", \"page\": 10, \"index\": 33, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-034.webp\", \"caption\": \"\", \"page\": 10, \"index\": 34, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-035.webp\", \"caption\": \"\", \"page\": 10, \"index\": 35, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-036.webp\", \"caption\": \"\", \"page\": 10, \"index\": 36, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-037.webp\", \"caption\": \"\", \"page\": 10, \"index\": 37, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-038.webp\", \"caption\": \"\", \"page\": 10, \"index\": 38, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-039.webp\", \"caption\": \"\", \"page\": 10, \"index\": 39, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-040.webp\", \"caption\": \"\", \"page\": 10, \"index\": 40, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-041.webp\", \"caption\": \"\", \"page\": 10, \"index\": 41, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-042.webp\", \"caption\": \"\", \"page\": 10, \"index\": 42, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-043.webp\", \"caption\": \"\", \"page\": 10, \"index\": 43, \"width\": 540, \"height\": 540}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-044.webp\", \"caption\": \"\", \"page\": 11, \"index\": 44, \"width\": 800, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-045.webp\", \"caption\": \"\", \"page\": 11, \"index\": 45, \"width\": 800, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-046.webp\", \"caption\": \"\", \"page\": 11, \"index\": 46, \"width\": 800, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-047.webp\", \"caption\": \"\", \"page\": 11, \"index\": 47, \"width\": 800, \"height\": 600}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-048.webp\", \"caption\": \"\", \"page\": 11, \"index\": 48, \"width\": 866, \"height\": 866}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-049.webp\", \"caption\": \"\", \"page\": 11, \"index\": 49, \"width\": 866, \"height\": 866}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-050.webp\", \"caption\": \"\", \"page\": 11, \"index\": 50, \"width\": 866, \"height\": 866}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-051.webp\", \"caption\": \"\", \"page\": 11, \"index\": 51, \"width\": 595, \"height\": 458}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-052.webp\", \"caption\": \"\", \"page\": 11, \"index\": 52, \"width\": 590, \"height\": 465}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-053.webp\", \"caption\": \"\", \"page\": 11, \"index\": 53, \"width\": 866, \"height\": 866}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-054.webp\", \"caption\": \"\", \"page\": 14, \"index\": 54, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-055.webp\", \"caption\": \"\", \"page\": 14, \"index\": 55, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-056.webp\", \"caption\": \"\", \"page\": 14, \"index\": 56, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-057.webp\", \"caption\": \"\", \"page\": 14, \"index\": 57, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-058.webp\", \"caption\": \"\", \"page\": 14, \"index\": 58, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-059.webp\", \"caption\": \"\", \"page\": 14, \"index\": 59, \"width\": 726, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-060.webp\", \"caption\": \"\", \"page\": 14, \"index\": 60, \"width\": 726, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-061.webp\", \"caption\": \"\", \"page\": 14, \"index\": 61, \"width\": 726, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-062.webp\", \"caption\": \"\", \"page\": 14, \"index\": 62, \"width\": 726, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-063.webp\", \"caption\": \"\", \"page\": 14, \"index\": 63, \"width\": 726, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-064.webp\", \"caption\": \"\", \"page\": 14, \"index\": 64, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-065.webp\", \"caption\": \"\", \"page\": 14, \"index\": 65, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-066.webp\", \"caption\": \"\", \"page\": 14, \"index\": 66, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-067.webp\", \"caption\": \"\", \"page\": 14, \"index\": 67, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-068.webp\", \"caption\": \"\", \"page\": 14, \"index\": 68, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-069.webp\", \"caption\": \"\", \"page\": 14, \"index\": 69, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-070.webp\", \"caption\": \"\", \"page\": 14, \"index\": 70, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-071.webp\", \"caption\": \"\", \"page\": 14, \"index\": 71, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-072.webp\", \"caption\": \"\", \"page\": 14, \"index\": 72, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-073.webp\", \"caption\": \"\", \"page\": 14, \"index\": 73, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-074.webp\", \"caption\": \"\", \"page\": 14, \"index\": 74, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-075.webp\", \"caption\": \"\", \"page\": 14, \"index\": 75, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-076.webp\", \"caption\": \"\", \"page\": 14, \"index\": 76, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-077.webp\", \"caption\": \"\", \"page\": 14, \"index\": 77, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-078.webp\", \"caption\": \"\", \"page\": 14, \"index\": 78, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-079.webp\", \"caption\": \"\", \"page\": 14, \"index\": 79, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-080.webp\", \"caption\": \"\", \"page\": 14, \"index\": 80, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-081.webp\", \"caption\": \"\", \"page\": 14, \"index\": 81, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-082.webp\", \"caption\": \"\", \"page\": 14, \"index\": 82, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-083.webp\", \"caption\": \"\", \"page\": 14, \"index\": 83, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-084.webp\", \"caption\": \"\", \"page\": 14, \"index\": 84, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-085.webp\", \"caption\": \"\", \"page\": 14, \"index\": 85, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-086.webp\", \"caption\": \"\", \"page\": 14, \"index\": 86, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-087.webp\", \"caption\": \"\", \"page\": 14, \"index\": 87, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-088.webp\", \"caption\": \"\", \"page\": 14, \"index\": 88, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-089.webp\", \"caption\": \"\", \"page\": 14, \"index\": 89, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-090.webp\", \"caption\": \"\", \"page\": 14, \"index\": 90, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-091.webp\", \"caption\": \"\", \"page\": 14, \"index\": 91, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-092.webp\", \"caption\": \"\", \"page\": 14, \"index\": 92, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-093.webp\", \"caption\": \"\", \"page\": 14, \"index\": 93, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-094.webp\", \"caption\": \"\", \"page\": 14, \"index\": 94, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-095.webp\", \"caption\": \"\", \"page\": 14, \"index\": 95, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-096.webp\", \"caption\": \"\", \"page\": 14, \"index\": 96, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-097.webp\", \"caption\": \"\", \"page\": 14, \"index\": 97, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-098.webp\", \"caption\": \"\", \"page\": 14, \"index\": 98, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-099.webp\", \"caption\": \"\", \"page\": 14, \"index\": 99, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-100.webp\", \"caption\": \"\", \"page\": 14, \"index\": 100, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-101.webp\", \"caption\": \"\", \"page\": 14, \"index\": 101, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-102.webp\", \"caption\": \"\", \"page\": 14, \"index\": 102, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-103.webp\", \"caption\": \"\", \"page\": 14, \"index\": 103, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-104.webp\", \"caption\": \"\", \"page\": 14, \"index\": 104, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-105.webp\", \"caption\": \"\", \"page\": 14, \"index\": 105, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-106.webp\", \"caption\": \"\", \"page\": 14, \"index\": 106, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-107.webp\", \"caption\": \"\", \"page\": 14, \"index\": 107, \"width\": 728, \"height\": 409}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-18ac194074ea6d99c59c4954/fig-108.webp\", \"caption\": \"\", \"page\": 14, \"index\": 108, \"width\": 728, \"height\": 409}]"
motivation: "模仿学习策略在视觉域偏移下鲁棒性不足,严重限制其在真实机器人操作中的部署。"
method: "构建域不变的Structure Map,通过StructCon自动构造模块与StructEncoder将其融入模仿学习策略。"
result: "在多种视觉域偏移条件下显著提升操作成功率,验证了结构引导对IL鲁棒性的关键作用。"
conclusion: "为视觉模仿学习的跨域鲁棒性问题提供通用解决方案,推动复杂操作任务的实际部署。"
---

## Abstract
Imitation Learning (IL) offers an effective approach for robotmanipulation by learning a mapping from visual inputs to actions. How-ever, this paradigm suffers from poor robustness under visual domainshifts (e.g., lighting conditions, camera viewpoints, etc.), often failingto perform manipulation. Our key insight in tackling this problem is toconstruct a Structure Map encoding the fine-grained object structuresthat remain invariant across visual domains and vital for manipulation.Based on this insight, we propose StructPolicy, a method elaboratelydesigned to incorporate the domain-invariant Structure Map into the ILpolicy through two modules: StructCon and StructEncoder. StructCon isan automated Structure Map construction module that leverages struc-ture primitives to enable flexible transformation and composition to forma wide range of objects. StructEncoder is a hierarchical network thatefficiently captures structural relationships and affordance from Struc-ture Map. This provides the IL policy with both domain-invariant andstructurally-aware features, guiding it toward robust manipulation un-der visual domain shifts. We extensively evaluate StructPolicy across 49manipulation tasks in multiple benchmarks and diverse real-world tasksunder various visual changes. The results demonstrate consistent andsignificant performance improvements across all tasks, validating thatStructPolicy enhances the effectiveness and robustness against visual do-main shifts of the IL policy, improving manipulation accuracy.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "StructPolicy: Structure-Guided Imitation Learning Robust to Visual Domain Shifts". I need to organize it according to the 8 specified points in Markdown format. Let me carefully analyze the paper content.

Key points from the paper:
1. Core problem: Imitation learning fails under visual domain shifts (lighting, background, viewpoint, noise)
2. Method: Structure Map + StructCon + StructEncoder
3. Experiments: MetaWorld, CALVIN, real-world tasks (49 total)
4. Resources: Not explicitly mentioned in the paper text I have
5. Experiment count: Multiple benchmarks, ablations
6. Conclusions: Improves robustness across various conditions
7. Advantages: Domain-invariant structure, hierarchical encoding
8. Limitations: Need to consider what the paper doesn't address

Let me write this in Chinese with proper structure.</think>

# StructPolicy 论文总结

## 1. 核心问题与研究动机

- **核心问题**：模仿学习（Imitation Learning, IL）在机器人操作中虽然训练高效，但策略严重依赖训练时的视觉条件，一旦遭遇**视觉域偏移**（如光照强度变化、背景颜色变化、相机视角偏移、渲染噪声等），任务成功率会急剧下降，难以在实际环境中可靠部署。
- **现有方案的不足**：
  - **基于物体中心的表示（OCR）**：通过分割图像去掉背景干扰，但分割结果对光照与视角仍敏感，未实现真正的域不变。
  - **通用视觉骨干网络**：对场景级视觉变化没有结构性约束，泛化能力有限。
- **作者的核心洞察**：在视觉域变化中，物体的**拓扑结构与空间布局（即"物体结构"）保持不变**，且这些结构信息恰好决定了可操作区域（affordance）。这一观点源于 Gibson 的生态知觉理论。
- **研究目标**：将这种"域不变的结构信息"显式注入到 IL 策略中，使其在视觉扰动下仍能稳定完成结构化操作任务。

## 2. 方法论

### 2.1 核心思想
提出 **Structure Map（结构图）**：一种仅编码物体**拓扑结构与空间布局**的描述子，对光照、背景、视角等视觉域变化保持不变；并设计 **StructPolicy** 框架，将其自动构造并融合进任意 IL 策略。

### 2.2 Structure Map 的三层定义
- **结构基元（Structure Primitives）**：如 Cuboid（长方体）、Arch Box（拱形盒）、Cylinder（圆柱）等，通过对几何模板的**结构化采样**（多面体均匀三角化、曲面按弧段采样）得到带标签的 3D 点集。
- **物体结构（Object Structure, $S_o$）**：由若干基元组成，建模空间布局：$S_o = \bigcup_{m=1}^{N_o} \{(p_i, \ell_i)\}_{i=1}^{N_m}$，其中 $p_i\in\mathbb{R}^3$ 为采样点、$\ell_i$ 为基元类型标签。**拓扑关系**通过物理约束（大小、位姿）施加。
- **可供性（Affordance, $A_o$）**：物体表面上对应可操作行为的三角面片集合 $A_o = \bigcup_{i=1}^{K_o} F_i$。
- **Structure Map**：$\mathcal{M} = \{(S_o^k, A_o^k, k)\}_{k=1}^{K}$，对 K 个任务相关物体统一编码结构与可供性。

### 2.3 StructCon（自动构造模块）
- 输入：任务描述、RGB 图像、IL 策略原始输入。
- 流程：
  1. **检索增强生成（RAG）**：用 VLM 根据任务描述与图像生成文本摘要，再通过 **BGE-M3** 编码为稠密向量，在 **ConceptFactory 数据库**（包含 39 类、4380 个物体）中检索最相关的物体类别。
  2. **结构模板检索**：从 ConceptFactory 取回对应的**结构基元**与**物理约束规则**，形成初始结构模板。
  3. **参数估计**：用 IL 视觉编码器 + MLP 头估计模板参数，实例化出 Structure Map。

### 2.4 StructEncoder（结构特征编码模块）
两条并行流：
- **可供性编码流**：Pose Generator 从 affordance 出发生成**粗略抓取位姿**（位置 + 接近方向），再经 MLP-based Pose Encoder 编码为 $f_p$。
- **结构编码流**：分层处理 ——
  - **Primitive Encoder**（MLP + Attention Pooling）逐类提取基元内几何特征；
  - **Structure Encoder**（Transformer）聚合得到跨基元的拓扑与空间关系特征 $f_s$。
- **特征融合**：将 $f_p$ 与 $f_s$ 通过 MLP 融合为 $f_m$，与 IL 视觉特征 $f_v$ 拼接后送入策略头预测动作。
- **训练方式**：与 IL 主干**联合训练**，无新增损失项。

## 3. 实验设计

### 3.1 数据集与场景
- **MetaWorld**（15 个任务）：涵盖简单（开抽屉、按键、拉手柄等）、中等（钉钉子、清扫等）、困难/极难（装配、插入、置物于货架等）难度。
- **CALVIN**（34 个任务）：长视野、指令链任务；包含 D→D 与 ABCD→D 两种评测设置。
- **真实机器人**：使用 7-DoF **Flexiv Rizon 4** 机械臂 + Flexiv-GN01 夹爪，30 Hz；RGB-D 相机为 **Intel RealSense L515**；点云 1024 点；测试 8 个任务（开门、关门、开茶壶、装盒、放置、铺毛巾、堆叠玩具块、堆杯），每个任务 20 次试验。
- **视觉变化类型**：①光照强度（LI=0.5–1.5）；②背景颜色（红/绿通道值 0.2/0.6/1.0）；③相机视角（水平 ±10°/±20°/±30°）；④渲染噪声（光线追踪 SPP=2/16/32/64）。

### 3.2 对比基线
- **CALVIN**：TaKSIE、HULC++、MDT、MDT-V、FLOWER；DeeR、GR-1、MoDE。
- **MetaWorld**：DP（Diffusion Policy）、DP3、Lift3D。
- **真实环境**：DP、DP3、MDT-V、Lift3D。
- **辅助表示对比**：Mask、Keypoints、Pose、BBox 等简单 OCR 表征。

## 4. 资源与算力
- **论文中未明确给出**训练所用 GPU 型号、数量及总训练时长。
- 仅可推断：实验基于标准 IL 骨干（DP/DP3/MDT-V/Lift3D/FLOWER 等）联合训练；真实机器人在 30 Hz 控制频率下运行。论文未报告算力消耗或推理显存占用，仅给出 StructPolicy 与 Lift3D(CLIP) 的推理时延对比。

## 5. 实验数量与充分性

### 5.1 实验数量
- **总任务数**：49 个（仿真 34 + MetaWorld 15），加 8 个真实任务。
- **有效性实验**：MetaWorld 15 任务 + CALVIN D→D + ABCD→D，涵盖 9+ 个基线方法。
- **鲁棒性实验**：在 CALVIN 上对 MDT-V 进行 4 类视觉变化（光照、背景、视角、噪声）逐档评测。
- **构造精度实验**：用 SAM 提取真值点云，对 Structure Map 在 4 类域偏移下用 Chamfer Distance / EMD / F-Score 三项指标量化。
- **系统误差分解**：分阶段引入结构模板与参数的真值，分析各组件误差贡献。
- **消融实验**：
  - 表 4：Map 编码器（StructEncoder / PointNet / PointTransformer / DenseFusion）× 表征采样（结构化 / 均匀）；
  - 表 5：StructEncoder 内部设计（结构/可供性编码 + MLP/Concat/Attention 融合）；
  - 表 6：Structure Map vs. 简单 OCR（Mask/Keypoints/Pose/BBox）。
- **效率实验**：推理时延对比。

### 5.2 充分性评价
- 实验覆盖**仿真 + 真实**、**多基线 + 多种辅助表示**、**4 类视觉扰动**，并配以消融和误差分析，整体比较充分。
- 真实实验每个任务 20 次试验，**样本量较小**，统计稳定性可能受限。
- 域偏移评测**主要在 CALVIN + MDT-V 上**，对其他基线/其他 benchmark 的鲁棒性未系统展开，覆盖略有不均。

## 6. 主要结论与发现

- **整体有效性**：在 CALVIN（ABC→D 与 D→D）和 MetaWorld 上对所有基线均带来稳定提升；首次在 MetaWorld 上将策略成功率推至 **>90%**。
- **域偏移鲁棒性**：在光照、背景、视角、噪声四类变化下，StructPolicy 始终优于 MDT-V；真实环境下面对 Lift3D 背景颜色变化成功率从 28.3% 提升至 69.1%（+40.8%）。
- **Structure Map 的稳定性**：即便在域偏移下，CD 仅从 8.66 升至 12.89（×10⁻³），F-Score 仍保持约 51.8%，说明跨域结构一致性高。
- **瓶颈分析**：参数估计器是 StructCon 的主要误差源（占系统性能差距的 ~7.4%），RAG 分类几乎无误差。
- **设计必要性**：分层结构编码（Primitive + Structure）、可供性编码与 MLP 融合缺一不可；相比 Mask/Keypoint/Pose/BBox，Structure Map 提供更显著增益（DP +12.3%，DP3 +12.5%）。
- **推理开销**：仅增加约 **2.99 ms**（vs Lift3D-CLIP）。

## 7. 优点 / 亮点

- **视角新颖**：从 Gibson 生态知觉出发，把"物体结构"作为域不变锚点，而非依赖 OCR 分割或纯视觉骨干，与既有方法形成差异化。
- **结构图设计的层次化**：基元→物体结构→可供性，三层粒度清晰，且通过结构化采样保证了几何精度。
- **与 VLM/ConceptFactory 结合**：利用 RAG 把语义先验与结构化几何模板统一，减少幻觉并保证物体类别一致。
- **即插即用**：作为插件模块，对 DP/DP3/MDT-V/Lift3D/FLOWER 等多种 IL 主干均带来正向收益，泛用性强。
- **真实部署验证**：不仅在仿真，还在 Flexiv 真实机械臂上验证四种骨干与四种视觉扰动，工程可信度高。
- **系统分析全面**：构造精度、系统误差分解、组件消融、效率测试一应俱全。

## 8. 不足与局限

- **算力与训练细节缺失**：未报告所用 GPU 型号/数量、训练时长、显存开销，难以复现与横向对比。
- **依赖外部知识库**：依赖 **ConceptFactory（4380 物体，39 类）** 构建 Structure Map，对库外/长尾物体或非标准物体（如柔性物体、流体、奇异工具）泛化能力存疑。
- **依赖 VLM 调用**：推理链路中含 VLM + RAG，**实时性受限**（虽然论文报告了 70.20 ms 增量，但 VLM 调用可能成为部署瓶颈），文中未给出 VLM 的具体型号/规模/延迟。
- **真实实验样本量偏小**：每任务 20 次试验，统计置信度有限；且真实任务数（8 个）相对仿真较少。
- **鲁棒性评测覆盖不均**：域偏移细粒度评测集中在 CALVIN+MDT-V，其他基线/benchmark 的鲁棒性未充分展开。
- **参数估计器是瓶颈**：误差分解显示参数估计贡献了大部分性能损失，但论文未提出针对该模块的进一步改进方案。
- **对动态/可形变物体建模有限**：Structure Map 用刚性基元与物理约束描述，**难以刻画柔性物体或非刚性结构**，限制了在更广泛操作任务中的应用。
- **未与最新 3D 表示方法充分对比**：例如未与最近基于 3D 语义场、神经辐射场、Gaussian Splatting 等域不变 3D 表示对比，对"结构化 + 域不变"这一路线缺乏更广谱的基准。

（完）
