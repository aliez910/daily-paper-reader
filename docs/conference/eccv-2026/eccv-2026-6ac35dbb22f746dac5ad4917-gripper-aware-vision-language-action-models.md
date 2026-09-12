---
title: Gripper-aware Vision Language Action Models
title_zh: 夹爪感知的视觉语言动作模型
authors: "Hanyi Zhang, Zihong Luo, Tianyu Li, Khang Nguyen, Basu Hela, Shreyas Kumar, Ngoc Tran, Feng Dai, Charith Munasinghe, Jorge Queralta, Giovanni Toffetti, Khoa Vo, Ngan Le, Ravi Prakash, Quan Vuong, Tung Ta, Long Hu, Anh Nguyen, Baoru Huang"
date: 2026-09-08
pdf: "https://media.eventhosts.cc/Conferences/ECCV2026/pdfs/5218.pdf"
tags: ["query:rob-il"]
score: 9.0
evidence: 面向通用机器人抓取与操作的视觉语言动作模型
tldr: 现有视觉语言动作模型通常隐式假设夹爪无关性，但抓取策略本质依赖于具体形态。本文揭示了这一局限，并提出MiGA多夹爪感知数据集，涵盖五种不同夹爪类型与十万三千次演示。该工作使VLA模型能够针对不同形态学习适配的抓取策略，推动通用机器人操作的形态感知学习。
source: ECCV-2026-Accepted-Program
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-001.webp\", \"caption\": \"\", \"page\": 1, \"index\": 1, \"width\": 1440, \"height\": 900}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-002.webp\", \"caption\": \"\", \"page\": 1, \"index\": 2, \"width\": 1200, \"height\": 900}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-003.webp\", \"caption\": \"\", \"page\": 1, \"index\": 3, \"width\": 2000, \"height\": 1500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-004.webp\", \"caption\": \"\", \"page\": 1, \"index\": 4, \"width\": 2000, \"height\": 1500}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-005.webp\", \"caption\": \"\", \"page\": 1, \"index\": 5, \"width\": 960, \"height\": 615}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-006.webp\", \"caption\": \"\", \"page\": 1, \"index\": 6, \"width\": 2000, \"height\": 1333}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-007.webp\", \"caption\": \"\", \"page\": 1, \"index\": 7, \"width\": 1200, \"height\": 457}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-008.webp\", \"caption\": \"\", \"page\": 1, \"index\": 8, \"width\": 483, \"height\": 439}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-009.webp\", \"caption\": \"\", \"page\": 3, \"index\": 9, \"width\": 355, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-010.webp\", \"caption\": \"\", \"page\": 3, \"index\": 10, \"width\": 355, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-011.webp\", \"caption\": \"\", \"page\": 3, \"index\": 11, \"width\": 355, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-012.webp\", \"caption\": \"\", \"page\": 3, \"index\": 12, \"width\": 355, \"height\": 355}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-013.webp\", \"caption\": \"\", \"page\": 6, \"index\": 13, \"width\": 641, \"height\": 410}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-014.webp\", \"caption\": \"\", \"page\": 6, \"index\": 14, \"width\": 641, \"height\": 410}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-015.webp\", \"caption\": \"\", \"page\": 6, \"index\": 15, \"width\": 641, \"height\": 410}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-016.webp\", \"caption\": \"\", \"page\": 6, \"index\": 16, \"width\": 456, \"height\": 326}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-017.webp\", \"caption\": \"\", \"page\": 6, \"index\": 17, \"width\": 360, \"height\": 360}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-018.webp\", \"caption\": \"\", \"page\": 6, \"index\": 18, \"width\": 372, \"height\": 372}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-019.webp\", \"caption\": \"\", \"page\": 6, \"index\": 19, \"width\": 438, \"height\": 438}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-020.webp\", \"caption\": \"\", \"page\": 6, \"index\": 20, \"width\": 570, \"height\": 567}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-021.webp\", \"caption\": \"\", \"page\": 6, \"index\": 21, \"width\": 423, \"height\": 346}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-022.webp\", \"caption\": \"\", \"page\": 6, \"index\": 22, \"width\": 423, \"height\": 346}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-023.webp\", \"caption\": \"\", \"page\": 6, \"index\": 23, \"width\": 451, \"height\": 361}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-024.webp\", \"caption\": \"\", \"page\": 6, \"index\": 24, \"width\": 695, \"height\": 551}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-025.webp\", \"caption\": \"\", \"page\": 6, \"index\": 25, \"width\": 695, \"height\": 551}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-026.webp\", \"caption\": \"\", \"page\": 6, \"index\": 26, \"width\": 695, \"height\": 551}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-027.webp\", \"caption\": \"\", \"page\": 6, \"index\": 27, \"width\": 695, \"height\": 551}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-028.webp\", \"caption\": \"\", \"page\": 6, \"index\": 28, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-029.webp\", \"caption\": \"\", \"page\": 6, \"index\": 29, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-030.webp\", \"caption\": \"\", \"page\": 6, \"index\": 30, \"width\": 876, \"height\": 631}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-031.webp\", \"caption\": \"\", \"page\": 6, \"index\": 31, \"width\": 1011, \"height\": 643}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-032.webp\", \"caption\": \"\", \"page\": 6, \"index\": 32, \"width\": 555, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-033.webp\", \"caption\": \"\", \"page\": 6, \"index\": 33, \"width\": 619, \"height\": 570}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-034.webp\", \"caption\": \"\", \"page\": 6, \"index\": 34, \"width\": 616, \"height\": 571}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-035.webp\", \"caption\": \"\", \"page\": 6, \"index\": 35, \"width\": 621, \"height\": 553}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-036.webp\", \"caption\": \"\", \"page\": 7, \"index\": 36, \"width\": 1175, \"height\": 531}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-037.webp\", \"caption\": \"\", \"page\": 7, \"index\": 37, \"width\": 595, \"height\": 595}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-038.webp\", \"caption\": \"\", \"page\": 8, \"index\": 38, \"width\": 512, \"height\": 512}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-039.webp\", \"caption\": \"\", \"page\": 8, \"index\": 39, \"width\": 932, \"height\": 647}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-040.webp\", \"caption\": \"\", \"page\": 8, \"index\": 40, \"width\": 932, \"height\": 647}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-041.webp\", \"caption\": \"\", \"page\": 8, \"index\": 41, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-042.webp\", \"caption\": \"\", \"page\": 8, \"index\": 42, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-043.webp\", \"caption\": \"\", \"page\": 8, \"index\": 43, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-044.webp\", \"caption\": \"\", \"page\": 8, \"index\": 44, \"width\": 476, \"height\": 432}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-045.webp\", \"caption\": \"\", \"page\": 8, \"index\": 45, \"width\": 476, \"height\": 432}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-046.webp\", \"caption\": \"\", \"page\": 8, \"index\": 46, \"width\": 476, \"height\": 432}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-047.webp\", \"caption\": \"\", \"page\": 12, \"index\": 47, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-048.webp\", \"caption\": \"\", \"page\": 12, \"index\": 48, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-049.webp\", \"caption\": \"\", \"page\": 12, \"index\": 49, \"width\": 573, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-050.webp\", \"caption\": \"\", \"page\": 12, \"index\": 50, \"width\": 573, \"height\": 382}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-051.webp\", \"caption\": \"\", \"page\": 12, \"index\": 51, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-052.webp\", \"caption\": \"\", \"page\": 12, \"index\": 52, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-053.webp\", \"caption\": \"\", \"page\": 12, \"index\": 53, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-054.webp\", \"caption\": \"\", \"page\": 12, \"index\": 54, \"width\": 588, \"height\": 421}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-055.webp\", \"caption\": \"\", \"page\": 12, \"index\": 55, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-056.webp\", \"caption\": \"\", \"page\": 12, \"index\": 56, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-057.webp\", \"caption\": \"\", \"page\": 12, \"index\": 57, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-058.webp\", \"caption\": \"\", \"page\": 12, \"index\": 58, \"width\": 563, \"height\": 353}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-059.webp\", \"caption\": \"\", \"page\": 12, \"index\": 59, \"width\": 703, \"height\": 489}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-060.webp\", \"caption\": \"\", \"page\": 12, \"index\": 60, \"width\": 1587, \"height\": 897}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-061.webp\", \"caption\": \"\", \"page\": 12, \"index\": 61, \"width\": 382, \"height\": 379}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-062.webp\", \"caption\": \"\", \"page\": 12, \"index\": 62, \"width\": 1583, \"height\": 907}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-063.webp\", \"caption\": \"\", \"page\": 12, \"index\": 63, \"width\": 561, \"height\": 462}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-064.webp\", \"caption\": \"\", \"page\": 12, \"index\": 64, \"width\": 1583, \"height\": 895}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-065.webp\", \"caption\": \"\", \"page\": 14, \"index\": 65, \"width\": 600, \"height\": 800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-066.webp\", \"caption\": \"\", \"page\": 14, \"index\": 66, \"width\": 600, \"height\": 800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-067.webp\", \"caption\": \"\", \"page\": 14, \"index\": 67, \"width\": 600, \"height\": 800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-068.webp\", \"caption\": \"\", \"page\": 14, \"index\": 68, \"width\": 900, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-069.webp\", \"caption\": \"\", \"page\": 14, \"index\": 69, \"width\": 600, \"height\": 800}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-070.webp\", \"caption\": \"\", \"page\": 14, \"index\": 70, \"width\": 900, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-071.webp\", \"caption\": \"\", \"page\": 14, \"index\": 71, \"width\": 900, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-072.webp\", \"caption\": \"\", \"page\": 14, \"index\": 72, \"width\": 900, \"height\": 1200}, {\"url\": \"assets/figures/eccv-2026-accepted-program/eccv-2026-6ac35dbb22f746dac5ad4917/fig-073.webp\", \"caption\": \"\", \"page\": 14, \"index\": 73, \"width\": 639, \"height\": 663}]"
motivation: 现有VLA模型隐式假设夹爪无关性，忽略了不同夹爪类型需要差异化抓取策略的形态依赖性。
method: 构建MiGA多夹爪感知数据集，涵盖五种夹爪类型与十万三千次跨机器人演示，支持形态感知学习。
result: 为VLA模型提供大规模多形态抓取数据基础，使其能够区分并适配不同夹爪类型的操作策略。
conclusion: 推动了通用机器人抓取与操作任务的形态感知VLA研究。
---

## Abstract
Vision language action models (VLAs) have advanced general purpose robotic grasping and manipulation by enabling robots to interpret visual observations and natural language instructions to generate executable action sequences. However, existing VLAs often implicitly assume gripper invariance, despite grasping strategies being inherently embodiment-dependent. Different gripper types, such as parallel-jaw and suction, usually require distinct interaction strategies to achieve the same grasping objective. Moreover, current datasets for VLAs predominantly rely on parallel-jaw grippers, limiting gripper-aware learning. To address this gap, we introduce MiGA, a multi-gripper-aware dataset spanning five distinct gripper types across multiple robots with 103,000 demonstrations, explicitly capturing strategy divergence under shared task objectives. We further propose GVLA, which combines a new multi-gripper tokenizer with adapter-based policy routing. Our new gripper encoding induces structured embedding information that balances parameter sharing and strategy differentiation, while layer-wise probing confirms meaningful gripper-conditioned representations for VLAs. Intensive experiments in both simulation and real-world robots show that our GVLA outperforms the current baselines across evaluated settings. Our method also improves zero-shot generalization or few-shot adaptation to new objects or unseen tasks, and enable more efficient gripper adaptation.

---

## 论文详细总结（自动生成）

<think>The user wants me to analyze a research paper about "Gripper-aware Vision Language Action Models" (GVLA) and provide a detailed Chinese summary following a specific structure. Let me organize the content based on the paper.

Key points from the paper:
1. Problem: Existing VLAs assume gripper invariance, but grasping strategies depend on gripper morphology
2. Method: MiGA dataset (103K demos, 5 gripper types) + GVLA model with multi-gripper tokenizer and dual Mixture-of-Adapters
3. Experiments: Simulation and real-world, comparisons with baselines
4. Resources: Not explicitly mentioned in the text
5. Experimental thoroughness: Multiple ablations, cross-gripper transfer, few-shot adaptation
6. Conclusions: GVLA outperforms baselines
7. Strengths: New dataset, novel architecture
8. Limitations: Simulation limitations, no explicit kinematic modeling, entanglement issues

Let me write a comprehensive Chinese summary.</think>

# 论文总结：夹爪感知的视觉语言动作模型（GVLA）

## 1. 核心问题与研究动机

- **核心问题**：现有视觉语言动作模型（VLA）隐式假设**夹爪无关性（gripper invariance）**，即认为同一任务可以用同一套抓取策略完成。但实际上，不同形态的夹爪（如平行二指、吸盘、灵巧手等）由于接触力学、可控自由度、几何结构差异巨大，**完成同一任务需要本质不同的策略**。
- **举例说明**：抓取一个扁平的 DVD 盒时，平行二指夹爪需要先把物体推到桌沿再从侧面抓取，而吸盘可以直接从上方吸起。这一现象揭示了"任务目标一致 ≠ 策略空间一致"的关键洞察。
- **数据集瓶颈**：现有大型机器人数据集（Open X-Embodiment、DROID、Bridge V2 等）几乎全部基于平行二指夹爪，缺乏夹爪多样性与策略多样性。
- **研究目标**：探索 VLA 模型能否学习**形态依赖性与策略级分化（embodiment-dependence and strategy-level divergence）**，以应对多样化的真实抓取任务。

---

## 2. 方法论

### 2.1 MiGA 数据集（Multi-Gripper-Aware Dataset）

- **规模与覆盖**：103,000 次演示、5 种夹爪类型、5 种机器人平台、36 个任务、仿真 + 真实双环境。
- **五种夹爪类型**：
  - 平行二指（Franka Panda、Robotiq 2F-85）
  - 三指（Robotiq 3-Finger）
  - 自研软体二指
  - 吸盘（Cobot Pump、UR10 Suction Cup）
  - 五指灵巧手（Inspire Hand RH56DFTP）
- **任务四大类**：Singulated（分散物体）、Stacked（堆叠场景）、Constrained（受限空间）、Semantic（语义抓取），每类任务至少 3 种夹爪执行。
- **额外监督**：自然语言策略描述、子步骤分解、约 5% 失败演示。

### 2.2 GVLA 模型架构

- **整体思路**：在已有 VLA backbone（π0 / π0.5）上引入两个新组件——多粒度夹爪 tokenizer 和双混合适配器（Dual MoA）。
- **多粒度夹爪 Tokenizer（三级软提示）**：
  - 平台级 token $P^{(r)}$：编码机器人运动学结构
  - 类别级 token $P^{(g)}$：编码夹爪类型共享的操作先验
  - 实例级 token $P^{(u)}$：编码具体夹爪的细粒度特征
  - 三者串联后前置拼接到观测嵌入：
    $$\tilde{X}^{(r,g,u)} = [P^{(h)}; X] \in \mathbb{R}^{(p_r+p_g+p_u+n_{\text{obs}})\times d}$$
- **双混合适配器（Dual MoA）**：
  - 平台路由器 $G^{(p)}$ 与夹爪路由器 $G^{(g)}$ 各自基于 top-k 选择专家；
  - 每个专家为瓶颈变换 $\mathcal{A}=W^{\text{up}}(\text{GeLU}(W^{\text{down}}(x)))$；
  - 输出叠加：$x \leftarrow x + \sum G^{(p)}_i \mathcal{A}^{(p)}_i + \sum G^{(g)}_j \mathcal{A}^{(g)}_j$。
- **插入位置选择**：通过**层级探针分析（layer-wise probing）**，测量各层动作隐藏表示对夹爪类型的敏感度 $S_{\text{type}}$，发现最后一层敏感度显著升高，故 MoA 插入 backbone 最后一层。
- **训练损失**（多目标联合）：
  - 动作流匹配损失 $\mathcal{L}_{\text{action}}$（基于 π0 的条件流匹配）
  - 夹爪分类辅助损失 $\mathcal{L}_{\text{gripper}}$
  - 路由器负载均衡损失 $\mathcal{L}_{\text{LB}}$，防止专家坍缩

---

## 3. 实验设计

### 3.1 数据与场景

- **仿真**：基于 NVIDIA Isaac Lab，使用 Franka Panda 与 UR10；
- **真实机器人**：UFACTORY xArm7、Franka Panda、UR5，配腕部与第三方多视角 RGB-D 相机；
- **任务划分**：四类任务（Flat、Stacked、Constrained、Semantic）。

### 3.2 评估指标（5 项）

1. **Success Rate (SR)**：任务成功率
2. **Prediction Error (PE)**：预测动作与真值的平均偏差
3. **CAPD（Counterfactual Action Prediction Divergence）**：仅修改夹爪身份时预测动作变化幅度，反映夹爪特异性行为
4. **LPA（Linear Probe Accuracy）**：逐层训练线性分类器评估夹爪可分性
5. **GCS（Gripper Contribution Score）**：衡量软提示相对视觉特征的贡献

### 3.3 对比基线

- 传统两阶段抓取检测器：**AnyGrasp**、**GraspMAS**
- VLA 基线：**GraspVLA**、**OpenVLA-OFT**、**π0**、**π0.5**
- 自身消融：GVLA（π0 backbone）与 GVLA（π0.5 backbone）

---

## 4. 资源与算力

- **论文正文未明确说明** GPU 型号、数量、训练时长等算力信息；
- 仅提及 fine-tuning 步数：少样本适应使用 **20K 步**微调；
- 真实机器人实验仅使用 **10 条演示 + 20K 步**完成少样本迁移；
- 推测使用了多 GPU 训练 π0.5 backbone（因 π0.5 原始训练需大量算力），但具体配置未给出。

---

## 5. 实验数量与充分性

- **主对比实验**（Table 2）：7 种方法 × 4 类任务 = 28 个数据点；
- **Tokenizer 对比**（Table 3）：MLP、VQ-VAE、Language Prompt 与本文方法在 PE、CAPD、GCS 上的对比；
- **消融实验**（Table 4）：分别移除 $P^{(g)}$、$P^{(p)}$、$P^{(u)}$、MoA、MoA(g)、MoA(p)，共 7 组配置；
- **跨物体零样本泛化**（Fig. 8）：4 个新任务上的零样本表现；
- **少样本适应**（Fig. 9）：三种场景——同夹爪新任务、新夹爪新任务、混合夹爪数据适应；
- **层级探针分析**（Fig. 6、Fig. 7）：LPA 与 Noise/Padding baseline 的逐层比较；
- **真实机器人实验**（Fig. 10）：UR5 + Robotiq 2F-85 在四类任务上的成功率对比；
- **失败案例分析**（Fig. 11）：三类失败原因归纳。
- **充分性评价**：实验覆盖了仿真/真实、零样本/少样本、组件消融、跨夹爪迁移、失败分析等多个维度，**总体较为充分**，但每类任务的样本数量与统计显著性检验在正文中未详细披露。

---

## 6. 主要结论与发现

- **数据集层面**：MiGA 是首个明确编码"相同任务目标、不同夹爪策略"的多夹爪数据集，包含 132 种夹爪-策略对；
- **方法层面**：
  - 提出的多粒度夹爪 tokenizer 在嵌入空间中产生按夹爪类型良好聚类的表示（Fig. 2d）；
  - 优于 MLP、VQ-VAE、Language Prompt 三种基线 token 化方式（Table 3）；
  - 层级探针显示夹爪感知信号贯穿整个网络，并在深层（L12-L18）保持高可分性；
- **性能层面**：
  - GVLA（π0.5）平均成功率 **66.00%**，较最强基线 π0.5（58.38%）提升 **+7.62%**；
  - 真实机器人实验中 GVLA 在四类任务上均优于 π0.5，少样本迁移表现尤其突出；
- **泛化层面**：在跨物体零样本、跨夹爪少样本场景下均显著优于 π0.5 baseline；
- **可解释性层面**：CAPD 显著高于基线，表明模型确实学到了夹爪特异的行为而非通用策略。

---

## 7. 优点与亮点

- **数据集贡献突出**：MiGA 首次系统覆盖了五种主流夹爪形态，并显式标注策略级差异，对社区有较高复用价值；
- **方法设计精巧**：
  - 三级软提示设计兼顾参数共享与策略特化；
  - 通过层级探针指导 MoA 插入位置，避免了拍脑袋式设计；
  - 负载均衡损失防止路由器坍缩，提升训练稳定性；
- **实验维度丰富**：包含零样本、少样本、跨域迁移、真实机器人等多角度验证；
- **指标体系全面**：不仅评估成功率，还引入 CAPD、GCS 等专门衡量"夹爪特异性"的指标；
- **可视化充分**：Fig. 2 通过特征热力图直观展示 token 化方法的优劣；
- **失败分析坦诚**：明确指出三类失败原因（intra-type misalignment、物理极限、运动学不可行），避免过度乐观。

---

## 8. 不足与局限

- **算力信息缺失**：未披露训练所用的 GPU 型号、数量、时长等关键信息，**复现门槛不透明**；
- **仿真局限**：依赖 NVIDIA Isaac Lab，对软体夹爪与多自由度灵巧手的物理仿真精度有限（作者已在 Limitations 中承认）；
- **缺少显式几何建模**：夹爪信息仅以软提示形式编码，没有显式的运动学或接触建模，**实例级细粒度适应仍有限**（如 Robotiq 2F-85 迁移时 PE 仍偏高）；
- **视觉-夹爪表征纠缠**：作者自承夹爪与视觉特征部分纠缠，在域偏移下策略仍可能过度依赖图像信息；
- **任务规模有限**：仅 36 个任务、4 类场景，相比 Bridge V2（60K）等大规模数据集，规模与多样性仍小；
- **统计显著性未明确**：每类任务的成功率缺少多次重复实验的均值与方差报告，难以判断结果稳健性；
- **真实机器人实验样本极少**：仅 10 条演示完成少样本迁移，未充分验证在更复杂真实环境中的可扩展性；
- **跨形态失败模式**：当面对物理上无法完成的任务时（如夹爪尺寸不足），模型仍会生成"看似合理但物理不可行"的轨迹，缺乏运动学可行性的硬约束；
- **仅基于 π0 / π0.5 验证**：未在其他主流 VLA backbone（如 OpenVLA、RT-2）上验证方法的通用性。

---

（完）
