---
title: "Twin-DAgger: Synergizing Digital Twins and Human Corrections for Efficient Robot Manipulation"
title_zh: Twin-DAgger：融合数字孪生与人类纠错的高效机器人操纵学习
authors: "Jiahang Li, Zhirui Zhang, Kairan Ding, Fan Fei, Yunkai Tang, Jiaming Liu, Xiao He, Ziyu Chen, Gaohao Zhou, Jieji Ren, Yandong Guo, Shanghang Zhang, Boxin Shi"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/12105.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 基于模仿学习的机器人操纵及DAgger数据聚合
tldr: 离线模仿学习策略在分布外会因误差累积而严重退化，而传统DAgger依赖一对一真实环境专家纠错，成本极高。本文提出Twin-DAgger，将数字孪生数据生成与人类纠错结合，并通过建模DAgger轨迹揭示的时空失效模式提升覆盖效率。实验表明该方法以更少专家投入实现了更广分布外覆盖，推动模仿学习在复杂操纵任务中的实用化。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-001.webp\", \"caption\": \"\", \"page\": 2, \"index\": 1, \"width\": 765, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-002.webp\", \"caption\": \"\", \"page\": 2, \"index\": 2, \"width\": 1150, \"height\": 408}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-003.webp\", \"caption\": \"\", \"page\": 2, \"index\": 3, \"width\": 573, \"height\": 468}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-004.webp\", \"caption\": \"\", \"page\": 2, \"index\": 4, \"width\": 715, \"height\": 631}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-005.webp\", \"caption\": \"\", \"page\": 2, \"index\": 5, \"width\": 589, \"height\": 519}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-006.webp\", \"caption\": \"\", \"page\": 2, \"index\": 6, \"width\": 718, \"height\": 634}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-007.webp\", \"caption\": \"\", \"page\": 2, \"index\": 7, \"width\": 581, \"height\": 513}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-008.webp\", \"caption\": \"\", \"page\": 2, \"index\": 8, \"width\": 652, \"height\": 575}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-009.webp\", \"caption\": \"\", \"page\": 2, \"index\": 9, \"width\": 715, \"height\": 631}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-010.webp\", \"caption\": \"\", \"page\": 2, \"index\": 10, \"width\": 646, \"height\": 569}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-011.webp\", \"caption\": \"\", \"page\": 2, \"index\": 11, \"width\": 1073, \"height\": 1715}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-012.webp\", \"caption\": \"\", \"page\": 2, \"index\": 12, \"width\": 1371, \"height\": 1500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-013.webp\", \"caption\": \"\", \"page\": 2, \"index\": 13, \"width\": 489, \"height\": 481}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-014.webp\", \"caption\": \"\", \"page\": 2, \"index\": 14, \"width\": 573, \"height\": 468}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-015.webp\", \"caption\": \"\", \"page\": 2, \"index\": 15, \"width\": 573, \"height\": 468}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-016.webp\", \"caption\": \"\", \"page\": 2, \"index\": 16, \"width\": 573, \"height\": 468}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-017.webp\", \"caption\": \"\", \"page\": 6, \"index\": 17, \"width\": 1204, \"height\": 1536}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-018.webp\", \"caption\": \"\", \"page\": 6, \"index\": 18, \"width\": 1943, \"height\": 1934}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-019.webp\", \"caption\": \"\", \"page\": 20, \"index\": 19, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-020.webp\", \"caption\": \"\", \"page\": 20, \"index\": 20, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-021.webp\", \"caption\": \"\", \"page\": 20, \"index\": 21, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-022.webp\", \"caption\": \"\", \"page\": 20, \"index\": 22, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-023.webp\", \"caption\": \"\", \"page\": 20, \"index\": 23, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-024.webp\", \"caption\": \"\", \"page\": 20, \"index\": 24, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-025.webp\", \"caption\": \"\", \"page\": 20, \"index\": 25, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-026.webp\", \"caption\": \"\", \"page\": 20, \"index\": 26, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-027.webp\", \"caption\": \"\", \"page\": 20, \"index\": 27, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-028.webp\", \"caption\": \"\", \"page\": 20, \"index\": 28, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-029.webp\", \"caption\": \"\", \"page\": 20, \"index\": 29, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-030.webp\", \"caption\": \"\", \"page\": 20, \"index\": 30, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-031.webp\", \"caption\": \"\", \"page\": 20, \"index\": 31, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-032.webp\", \"caption\": \"\", \"page\": 20, \"index\": 32, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-033.webp\", \"caption\": \"\", \"page\": 20, \"index\": 33, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-034.webp\", \"caption\": \"\", \"page\": 20, \"index\": 34, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-035.webp\", \"caption\": \"\", \"page\": 20, \"index\": 35, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-036.webp\", \"caption\": \"\", \"page\": 20, \"index\": 36, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-037.webp\", \"caption\": \"\", \"page\": 20, \"index\": 37, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-038.webp\", \"caption\": \"\", \"page\": 20, \"index\": 38, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-039.webp\", \"caption\": \"\", \"page\": 20, \"index\": 39, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-040.webp\", \"caption\": \"\", \"page\": 20, \"index\": 40, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-041.webp\", \"caption\": \"\", \"page\": 20, \"index\": 41, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-042.webp\", \"caption\": \"\", \"page\": 20, \"index\": 42, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-043.webp\", \"caption\": \"\", \"page\": 20, \"index\": 43, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-044.webp\", \"caption\": \"\", \"page\": 20, \"index\": 44, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-045.webp\", \"caption\": \"\", \"page\": 20, \"index\": 45, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-046.webp\", \"caption\": \"\", \"page\": 20, \"index\": 46, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-047.webp\", \"caption\": \"\", \"page\": 20, \"index\": 47, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-048.webp\", \"caption\": \"\", \"page\": 20, \"index\": 48, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-049.webp\", \"caption\": \"\", \"page\": 21, \"index\": 49, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-050.webp\", \"caption\": \"\", \"page\": 21, \"index\": 50, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-051.webp\", \"caption\": \"\", \"page\": 21, \"index\": 51, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-052.webp\", \"caption\": \"\", \"page\": 21, \"index\": 52, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-053.webp\", \"caption\": \"\", \"page\": 21, \"index\": 53, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-054.webp\", \"caption\": \"\", \"page\": 21, \"index\": 54, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-055.webp\", \"caption\": \"\", \"page\": 21, \"index\": 55, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-056.webp\", \"caption\": \"\", \"page\": 21, \"index\": 56, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-057.webp\", \"caption\": \"\", \"page\": 21, \"index\": 57, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-058.webp\", \"caption\": \"\", \"page\": 21, \"index\": 58, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-059.webp\", \"caption\": \"\", \"page\": 21, \"index\": 59, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-060.webp\", \"caption\": \"\", \"page\": 21, \"index\": 60, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-061.webp\", \"caption\": \"\", \"page\": 21, \"index\": 61, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-062.webp\", \"caption\": \"\", \"page\": 21, \"index\": 62, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-063.webp\", \"caption\": \"\", \"page\": 21, \"index\": 63, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-064.webp\", \"caption\": \"\", \"page\": 21, \"index\": 64, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-065.webp\", \"caption\": \"\", \"page\": 21, \"index\": 65, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-066.webp\", \"caption\": \"\", \"page\": 21, \"index\": 66, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-067.webp\", \"caption\": \"\", \"page\": 21, \"index\": 67, \"width\": 472, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-068.webp\", \"caption\": \"\", \"page\": 21, \"index\": 68, \"width\": 472, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-069.webp\", \"caption\": \"\", \"page\": 21, \"index\": 69, \"width\": 472, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-070.webp\", \"caption\": \"\", \"page\": 21, \"index\": 70, \"width\": 472, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-071.webp\", \"caption\": \"\", \"page\": 21, \"index\": 71, \"width\": 472, \"height\": 354}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-072.webp\", \"caption\": \"\", \"page\": 21, \"index\": 72, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-073.webp\", \"caption\": \"\", \"page\": 21, \"index\": 73, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-074.webp\", \"caption\": \"\", \"page\": 21, \"index\": 74, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-075.webp\", \"caption\": \"\", \"page\": 21, \"index\": 75, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-076.webp\", \"caption\": \"\", \"page\": 21, \"index\": 76, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-077.webp\", \"caption\": \"\", \"page\": 21, \"index\": 77, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-078.webp\", \"caption\": \"\", \"page\": 21, \"index\": 78, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-079.webp\", \"caption\": \"\", \"page\": 22, \"index\": 79, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-080.webp\", \"caption\": \"\", \"page\": 22, \"index\": 80, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-081.webp\", \"caption\": \"\", \"page\": 22, \"index\": 81, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-082.webp\", \"caption\": \"\", \"page\": 22, \"index\": 82, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-083.webp\", \"caption\": \"\", \"page\": 22, \"index\": 83, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-084.webp\", \"caption\": \"\", \"page\": 22, \"index\": 84, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-085.webp\", \"caption\": \"\", \"page\": 22, \"index\": 85, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-086.webp\", \"caption\": \"\", \"page\": 22, \"index\": 86, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-087.webp\", \"caption\": \"\", \"page\": 22, \"index\": 87, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-088.webp\", \"caption\": \"\", \"page\": 22, \"index\": 88, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-089.webp\", \"caption\": \"\", \"page\": 22, \"index\": 89, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-090.webp\", \"caption\": \"\", \"page\": 22, \"index\": 90, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-091.webp\", \"caption\": \"\", \"page\": 22, \"index\": 91, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-092.webp\", \"caption\": \"\", \"page\": 22, \"index\": 92, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-093.webp\", \"caption\": \"\", \"page\": 22, \"index\": 93, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-094.webp\", \"caption\": \"\", \"page\": 22, \"index\": 94, \"width\": 631, \"height\": 474}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-095.webp\", \"caption\": \"\", \"page\": 23, \"index\": 95, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-096.webp\", \"caption\": \"\", \"page\": 23, \"index\": 96, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-097.webp\", \"caption\": \"\", \"page\": 23, \"index\": 97, \"width\": 719, \"height\": 538}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-098.webp\", \"caption\": \"\", \"page\": 24, \"index\": 98, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-099.webp\", \"caption\": \"\", \"page\": 24, \"index\": 99, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-100.webp\", \"caption\": \"\", \"page\": 24, \"index\": 100, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-101.webp\", \"caption\": \"\", \"page\": 24, \"index\": 101, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-102.webp\", \"caption\": \"\", \"page\": 24, \"index\": 102, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-103.webp\", \"caption\": \"\", \"page\": 24, \"index\": 103, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-104.webp\", \"caption\": \"\", \"page\": 24, \"index\": 104, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-105.webp\", \"caption\": \"\", \"page\": 24, \"index\": 105, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-106.webp\", \"caption\": \"\", \"page\": 24, \"index\": 106, \"width\": 640, \"height\": 480}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-0b5abcf501defc511408d07c/fig-107.webp\", \"caption\": \"\", \"page\": 24, \"index\": 107, \"width\": 640, \"height\": 480}]"
motivation: 离线模仿学习易因误差累积而失效，传统DAgger对真实世界专家纠错依赖过大。
method: 融合数字孪生数据生成与DAgger轨迹时空失效模式建模，降低专家标注负担。
result: 在复杂操纵任务上以更少真实纠错实现更广分布外覆盖与更高成功率。
conclusion: 为模仿学习在实际机器人操纵部署中提供了一条高效可扩展的路径。
---

## Abstract
Imitation learning enables robots to acquire complex manipulation skills from expert demonstrations, but offline-trained policies struggle to generalize beyond their training distribution, where small errors compound into severe distribution shift. Dataset Aggregation (DAgger) mitigates this by collecting human corrections during deployment, yet conventional DAgger operates entirely in the real world with a oneto-one ratio between expert effort and training trajectories makes comprehensive out-of-distribution (OOD) coverage impractical. Digital Twin (DT) techniques can scale data generation, but when applied to DAgger data without modification, they ignore the spatial and temporal failure patterns that DAgger rollouts reveal, leaving policies vulnerable precisely where and when they fail most. We propose Twin-DAgger, which treats each real-world intervention as simultaneously a spatial probe identifying failure-prone workspace regions and a temporal prior marking critical deviation moments. Twin-DAgger exploits these signals through two targeted augmentation mechanisms: difficulty-based stratified sampling concentrates synthetic data generation on high-failure-rate regions, and intervention-focused trajectory warping perturbs trajectories at each intervention onset to simulate a distribution of near-failure states while preserving the expert’s corrective recovery. On real-world manipulation tasks, Twin-DAgger matches conventional DAgger performance using only 15% human interventions and outperforms failure-agnostic DT baselines by 20% success rate under equal data budgets, demonstrating that generating data where and when the policy fails, rather than generating more data uniformly, is the critical driver of sample-efficient robustness.

---

## 论文详细总结（自动生成）

<think>The user wants a detailed Chinese summary of the paper "Twin-DAgger" organized into 8 specific sections. Let me analyze the paper content carefully and structure a comprehensive response.

Let me go through each section:

1. Core problem and overall meaning (motivation and background)
2. Methodology: core ideas, key technical details, formulas/algorithm flow
3. Experimental design: datasets/scenarios, benchmarks, comparison methods
4. Resources and compute: GPU models, training time, etc.
5. Number and sufficiency of experiments: ablation studies, fairness
6. Main conclusions and findings
7. Strengths: highlights of method or experimental design
8. Limitations and shortcomings

Let me write this out in Markdown with hierarchical headings and bullet points.</think>

# Twin-DAgger 论文总结

## 一、核心问题与研究背景

- **离线模仿学习的固有缺陷**：通过行为克隆（Behavior Cloning）训练的策略在分布外（OOD）场景下容易因小误差累积而产生严重的分布偏移（distribution shift），最终导致任务失败。
- **传统 DAgger 的成本瓶颈**：Dataset Aggregation（DAgger）通过部署阶段的人工纠错来缓解分布偏移，但每条专家干预只能生成 1 条轨迹，**专家投入与训练数据之间是 1:1 的低效关系**，难以覆盖多样化的 OOD 场景。
- **直接套用数字孪生（DT）增广方法的局限**：现有 DT 数据生成方法（如 MimicGen、Real2Render2Real）是为全遥操作数据设计的，对所有时间步和空间区域一视同仁，**忽视了 DAgger 过程本身揭示的两类关键失效信号**——时间模式（何时开始偏移）和空间模式（哪里频繁失败）。
- **研究目标**：利用少量真实世界专家干预，通过数字孪生进行有针对性的失效模式感知增广，实现成本高效的策略鲁棒性提升。

---

## 二、方法论

### 2.1 核心思想
- 将每条 DAgger 干预轨迹同时视为 **空间探针**（标记失败高发区域）和 **时间先验**（标记关键偏移时刻），基于此进行有针对性的 DT 数据增广，而非均匀地生成更多数据。

### 2.2 系统框架（"train–explore–augment–train" 闭环）
1. **策略预训练**：基于 100 条初始遥操作演示训练基础策略 π_θ。
2. **真实世界部署与专家干预**：使用 Meta Quest 3 VR 头显进行遥操作干预，每条 DAgger 轨迹包含二元干预指示符 c_t ∈ {0, 1}、机器人本体感知状态 s_t 和物体初始位姿 p_obj^0。
3. **DT 增广（核心步骤）**：在 ManiSkill 3 仿真器中重建真实环境，通过两种机制生成大量针对性增广数据 D_aug。
4. **策略后训练**：D_post = D_init ∪ D_aug。

### 2.3 关键技术细节

- **干预聚焦轨迹形变（Intervention-Focused Trajectory Warping）—— 时间维度**
  - 根据 c_t 的转折点将轨迹分段，定位干预起始点 t_onset 和结束点 t_end。
  - 在每个干预起始点对末端执行器（EE）位姿施加局部高斯扰动：
    $$\mathbf{e}'_{\text{onset},i} = \mathbf{e}_{\text{onset},i} + \boldsymbol{\varepsilon}_i, \quad \boldsymbol{\varepsilon}_i \sim \mathcal{N}(\mathbf{0}, \boldsymbol{\Sigma}_i)$$
  - 采用两阶段权重调度实现平滑过渡：前干预阶段从 0 渐升至 1，专家纠错阶段从 1 衰减至 0（分别对应 Slerp 旋转插值和线性平移插值）。
  - 通过基于 Pinocchio 的逐帧逆运动学（IK）求解，确保关节空间的连续性和物理可行性。

- **基于难度的分层采样（Difficulty-Based Stratified Sampling）—— 空间维度**
  - 将工作空间划分为 K 个子区域（如 50×32 cm 矩形划分为 3×2 = 6 个区域），记录各区域经验成功率 S_i。
  - 按难度分配增广预算：
    $$N_i = N_{\text{total}} \cdot \frac{(1 - S_i)^\gamma}{\sum_{j=1}^{K} (1 - S_j)^\gamma}$$
    其中聚焦因子 γ=5，用以进一步加权失败高发区域。
  - 在每个区域内对物体位姿进行扰动，并叠加干预聚焦轨迹形变生成多样化的纠错轨迹。

### 2.4 工程实现细节
- **异步策略推理系统**：双线程架构（推理线程 + 执行线程），通过线程安全的环形缓冲区解耦策略推理与动作执行；对过时动作进行剪裁，缓冲占用率低于 2%。
- **DT 视觉多样化**：随机化环境光照、桌面背景、干扰物体，并对第三人称相机视角进行局部邻域采样。

---

## 三、实验设计

### 3.1 任务与场景
- **主任务**：机器人前方的 Pick-and-Place 抓放任务，工作空间均匀划分为 6 个区域。
- **额外任务**（附录 C）：
  - **Peg-in-Hole（PIH）**：高精度插入任务，3 mm 容差。
  - **Categorical-Sorting（CS）**：长时序分类分拣任务。

### 3.2 数据规模
- **基础演示**：每个任务 100 条 VR 遥操作演示。
- **DAgger 干预数据**：6 条真实世界纠错轨迹（每区域 1 条失败轨迹作为种子）。
- **增广数据**：DT 内生成 100 条增广轨迹。

### 3.3 评估的策略
- **ACT**（Action Chunking Transformer）
- **π0**（视觉-语言-动作流模型，基于 OpenPI 实现）

### 3.4 对比基线
- **无后训练的基础策略**：直接在初始 100 条演示上训练。
- **Real2Render2Real (R2R2R)**：当前先进的 DT 增广方法（在 ManiSkill 3 中复现以共享同一 DT 环境）。
- **Conventional DAgger**：纯真实世界干预，无 DT 增广。
- **Teleoperation**：补充遥操作演示。

### 3.5 评估指标
- 主指标：成功率（Success Rate, SR），单次任务限定在 2000 步内完成且无需专家干预。
- 辅助分析：每区域成功率分布、零样本视觉鲁棒性测试（红色光照环境）。

---

## 四、资源与算力

- **GPU**：单卡 **NVIDIA H200**（142 GB 显存）。
- **训练时长**：
  - ACT：batch size 64，训练 100K 步，AdamW 优化器，学习率 1×10⁻⁴。
  - π0：batch size 32，训练 50K 步，峰值学习率 5×10⁻⁵，使用 EMA（衰减率 0.999）。
- **机器人平台**：RealMan RM-75-6FB（7-DoF，最大伸展约 640 mm）+ Inspire EG2-4C2 1-DoF 并行夹爪。
- **视觉系统**：第三人称 RealSense D435 + 腕戴 RealSense D405，分辨率 640×480，采集频率 30 Hz。
- **仿真器**：ManiSkill 3，使用 Pinocchio 作为 IK 求解器。
- 论文未明确报告训练墙钟时间与 GPU 小时数。

---

## 五、实验数量与充分性

- **主任务对比实验**：表 1 报告基础策略、R2R2R（100 和 500 样本）、消融变体（去除时间/空间组件）的完整对比；图 3 报告与常规 DAgger 沿训练数据量的对比曲线。
- **消融实验**：
  - 组件消融：去除空间采样（w/o Spatial）、去除时间形变（w/o Temporal）以及完整版本。
  - 超参数敏感度：空间聚焦因子 γ ∈ {1, 2, 5, 10}，时间扰动尺度 Σ ∈ {0.5, 1, 2, 5}（图 5）。
- **空间分析**：图 4 提供 6 个区域在四种策略下的成功率热图。
- **跨任务泛化**：附录 C 中在 PIH 与 CS 任务上重复相同对比（表 S2、S3）。
- **鲁棒性测试**：附录 B.2 在未见过的红色光照环境下做零样本评估（表 S1）；并报告摩擦系数随机化对动力学鲁棒性的提升。
- **充分性评估**：
  - 实验覆盖了主任务 + 2 个跨任务 + 鲁棒性测试，较为全面。
  - 公平性：所有对比方法使用相同的 DT 环境和基础演示数据；R2R2R 在 ManiSkill 3 中重新实现以保证环境一致。
  - 但每个实验的统计重复次数未详细说明（例如每个区域是否做了多次 rollout 平均）。

---

## 六、主要结论与发现

- **样本效率显著提升**：Twin-DAgger 仅用 **6 条真实专家干预**（约为常规 DAgger 所需 50 条干预的 15%）即可达到与常规 DAgger 相当的性能。
- **击败 DT 基线**：在相同 100 条增广数据预算下，比无失效感知的 R2R2R 高 **20% 成功率**（在 π0 上由 55% 提升到 85%）。
- **朴素 DT 增广的负面效应**：R2R2R 在 π0 上扩展到 500 条样本时，成功率反而从 55% 下降到 43.3%，表明不加区分的增广可能导致**灾难性遗忘**。
- **时空机制互补**：单独使用时间或空间机制都能超过 R2R2R 基线，二者组合增益更大，说明两者针对的是**互补的失效模式**。
- **关键洞察**：策略鲁棒性的关键驱动因素**不是生成更多数据，而是在正确的时间和地点生成数据**。
- **跨任务泛化**：在 PIH 和 CS 任务上，Twin-DAgger 一致优于 R2R2R 并匹配常规 DAgger，验证了方法的通用性。
- **零样本鲁棒性**：在红色光照干扰下，π0 成功率仍能保持 70%（基线仅 36.7%），表明 DT 中的视觉多样化有效提升了泛化能力。

---

## 七、优点与亮点

- **问题定位精准**：明确指出传统 DAgger 与 DT 增广各自的不足，提出"时空失效模式"这一统一视角，思路清晰。
- **方法设计对称且优雅**：空间维度对应"哪里失败"，时间维度对应"何时失败"，两个机制彼此正交且互补。
- **工程实现完整**：包含异步推理系统、IK 求解、碰撞检测、视觉随机化等工程细节，具有较强的可复现性。
- **样本效率极高**：以传统方法 15% 的真实干预成本达到同等性能，对于实际部署意义重大。
- **验证充分**：组件消融 + 超参数敏感度 + 跨任务泛化 + 零样本鲁棒性 + 物理参数随机化测试。
- **坦诚讨论消融的负面现象**：朴素 DT 增广导致 π0 性能下降，揭示了"更多数据并不总是更好"的关键洞察。

---

## 八、不足与局限

- **场景限制**：
  - 当前方法依赖 DT 轨迹重放，**主要支持刚体操作**，对柔性/可形变物体（如布料、绳子）难以重建和增广。
  - VR 遥操作 + IK 求解的关节配置在工作空间边界可能不自然，作者建议未来采用机器人同构外骨骼。
- **DAgger 范式固有限制**：
  - 无法处理专家反应前来不及挽回的不可逆失败（如易碎物品破碎），需要预测式干预（如触觉反馈引导）。
- **实验统计充分性**：
  - 论文未明确说明每个成功率数值背后的试验次数与置信区间，难以评估结果的统计显著性。
  - 跨任务实验规模较小（仅 PIH 与 CS），未覆盖更多样化的任务类型（如铰接物体、双手协调等）。
- **DT 保真度依赖**：
  - 增广质量受限于 DT 的视觉与动力学重建精度；若重建误差较大，sim-to-real 迁移可能引入新的偏差。
- **超参数敏感度**：
  - γ=10 时性能急剧下降至 38.3%，表明空间集中因子对性能影响较大，实际应用时需针对具体任务和机器人调优。
- **可扩展性**：
  - 工作空间划分和区域数 K 是手工设定的，对不同机械臂构型或更复杂的工作空间需要重新设计。

（完）
