---
title: "Real Garment Benchmark (RGBench): A Comprehensive Benchmark for Robotic Garment Manipulation Featuring a High-Fidelity Scalable Simulator"
title_zh: "RGBench: 面向机器人服装操控的全面基准与高保真可扩展模拟器"
authors: "Wenkang Hu, Xincheng Tang, Yanzhi E, Yitong Li, Zhengjie Shu, Wei Li, Huamin Wang, Ruigang Yang"
date: 2026-03-17
pdf: "https://ojs.aaai.org/index.php/AAAI/article/download/38894/42856"
tags: ["query:rob-il"]
score: 9.0
evidence: 针对机器人服装操控的全面基准，包含高保真模拟器和评估协议
tldr: 针对机器人服装操控缺乏标准基准和逼真模拟器的问题，提出了RGBench，包含6000多种布料网格模型、高性能模拟器和全面评估协议。实验表明该模拟器在真实感上显著优于现有布料仿真器。该基准为复杂可变形物体操控的模仿学习研究提供了标准化测试平台，有助于推动该领域的发展。
source: AAAI-2026-Accepted
selection_source: conference_retrieval
figures_json: "[{\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 790, \"height\": 579, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 872, \"height\": 511, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-003.webp\", \"caption\": \"\", \"page\": 0, \"index\": 3, \"width\": 862, \"height\": 474, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-004.webp\", \"caption\": \"\", \"page\": 0, \"index\": 4, \"width\": 854, \"height\": 496, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-005.webp\", \"caption\": \"\", \"page\": 0, \"index\": 5, \"width\": 860, \"height\": 647, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-006.webp\", \"caption\": \"\", \"page\": 0, \"index\": 6, \"width\": 1755, \"height\": 602, \"label\": \"Figure\"}, {\"url\": \"assets/figures/aaai-2026-accepted/aaai-2026-38894/fig-007.webp\", \"caption\": \"\", \"page\": 0, \"index\": 7, \"width\": 868, \"height\": 443, \"label\": \"Figure\"}]"
tables_json: "[{\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38894/table-001.webp\", \"caption\": \"\", \"page\": 0, \"index\": 1, \"width\": 871, \"height\": 197, \"label\": \"Table\"}, {\"url\": \"assets/tables/aaai-2026-accepted/aaai-2026-38894/table-002.webp\", \"caption\": \"\", \"page\": 0, \"index\": 2, \"width\": 874, \"height\": 835, \"label\": \"Table\"}]"
motivation: 机器人服装操控缺乏真实数据集和逼真模拟器，限制了研究进展。
method: 构建包含大量布料模型、高性能模拟器和评估协议的全面基准RGBench。
result: RGBench的模拟器在真实感上超越现有方案，验证了基准的有效性。
conclusion: RGBench为服装操控研究提供了标准化平台，有望加速该领域发展。
---

## Abstract
While there has been significant progress to use simulated data to learn robotic manipulation of rigid objects, applying its success to deformable objects has been hindered by the lack of both deformable object models and realistic non-rigid body simulators. In this paper, we present Real Garment Benchmark (RGBench), a comprehensive benchmark for robotic manipulation of garments. It features a diverse set of over 6000 garment mesh models, a new high-performance simulator, and a comprehensive protocol to evaluate garment simulation quality with carefully measured real garment dynamics. Our experiments demonstrate that our simulator outperforms currently available cloth simulators by a large margin, reducing simulation error by 20% while maintaining a speed of 3 times faster. We will publicly release RGBench to accelerate future research in robotic garment manipulation.

---

## 论文详细总结（自动生成）

# Real Garment Benchmark (RGBench) 论文总结

## 1. 核心问题与整体含义（研究动机和背景）

- 机器人操控可变形物体（尤其是服装）是机器人研究的前沿挑战，难点在于：服装状态空间高维、行为高度非线性且欠驱动、接触与自碰撞复杂。
- 现有物理模拟器在保真度与性能上存在严重不足：简化模型（如 PBD）导致仿真结果不真实（拉伸、穿透），形成显著的 **sim-to-real 差距**；同时模拟速度慢，难以支持大规模并行训练。
- 缺乏系统性评估仿真保真度的基准与数据集——已有的工作仅限于简单物体（如一维绳、矩形布），缺乏针对复杂服装的标准评估平台。
- **本文目标**：提出 RGBench，包含多样化服装模型、高精度高性能模拟器（GarmentDynamics）及标准化评估协议，以推动机器人服装操控研究。

## 2. 方法论：核心思想与关键技术细节

- **整体框架**：RGBench 集成了服装数据集、双臂机器人设置（AGILEX Piper 或 JAKA K1）与 GarmentDynamics 模拟系统，围绕抓取（Grasp）、甩动（Fling）、折叠（Fold）三项基本任务进行仿真与真实对比。
- **数据集构建**：
  - 包含 **6000+ 服装网格模型**（4000+ 工业级生产资产 + 2000+ 来自 ClothesNet）。
  - 涵盖多种尺寸、风格（合身、宽松、结构化、飘逸）与材料（棉、亚麻、羊毛、涤纶、尼龙、丝绸等）。
  - 几何精度通过导入生产级 DXF 图样实现；物理参数（拉伸刚度、弯曲刚度、密度）使用 **SST1000 拉伸测试仪**与 **SBE1000 弯曲测试仪** 依照 ASTM 标准测量。
- **真实操控数据（Ground Truth）**：
  - 双臂机器人按预设轨迹执行操作，Intel RealSense L515 相机采集 RGB 点云，用 Grounded-SAM 分割出服装区域，获得 real point cloud \( \mathcal{P}_{\text{real}} \)。
- **评估指标**：
  - **Chamfer Distance (CD)**：Sim-to-real（\( CD_{s2r} \)）与 Real-to-sim（\( CD_{r2s} \)）两个方向。
  - **Hausdorff Distance (HD)**：同样双向计算。
  - 重点采用 real-to-sim 方向，因其更反映仿真对真实观测的拟合程度，且不受粒子模拟膨胀/爆炸的干扰。
- **模拟器 GarmentDynamics 核心设计**：
  - **连续介质有限元模型 (FEM)**：布料视为连续弹性表面，离散为三角形网格；各向异性应变模型（Baraff & Witkin），弯曲阻力为曲率的二次函数，以更好捕捉褶皱。
  - **物理参数直接输入**：使用实测属性（密度、厚度、弹性模量、表面粗糙度等）。
  - **碰撞处理**：结合 **基于势能的接触力** 与 **碰撞解缠机制 (Volino method)**，实现高鲁棒性。
  - **GPU 加速隐式时间积分**：
    - 采用 **隐式欧拉**，将每步求解转化为能量最小化问题。
    - 通过少数 **非精确 Newton 迭代** 求解，内部使用固定次数的 **预条件共轭梯度法 (PCG)**。
    - 预条件器采用 **多级 Additive Schwarz (MAS) 框架**，各子域块通过 Gauss-Jordan 求逆并固化于 GPU，运行时无冲突的稀疏矩阵-向量乘并行。
  - **碰撞检测加速**：构建 GPU 级包围盒层次，利用 **NVIDIA RTX 射线求交特性** 并行执行。
  - **操控模式**：机器人模式（完整 URDF + 关节模拟）与伪模式（直接控制布料顶点简化交互）两种。

## 3. 实验设计

- **使用的数据集 / 场景**：
  - **BCM 公开基准**：矩形格子布数据集，用于验证基础精度。
  - **RGBench 自身数据集**：7 种服装类型（Cakeskirt、Coat、Dress、Hoodie、Pleat Skirt、L-Sleeves、T-Shirt），每个服装执行 Grasp、Fling、Fold 三种操作。
- **对比方法**：MuJoCo、PyBullet、NVIDIA Isaac Sim（主流机器人模拟器）。
- **评估内容**：
  1. **BCM 验证**：动态与准静态两种模式，对比 CD、HD。
  2. **模拟效率与可扩展性**：测试顶点数 5k/10k/20k/40k 时的初始化时间与平均步长时间。
  3. **Sim-to-real 差距定量对比**：在 RGBench 各服装-任务组合上，分别计算两个方向的 CD 与 HD；包括伪模式（表 2）与机器人模式（图 7）。
  4. **定性可视化**：展示折叠任务中各模拟器与真实点云的对比（图 5）。
- **公平性措施**：所有模拟器均使用相同初始状态（模板对齐）、相同手眼标定与延迟补偿。

## 4. 资源与算力

- **文中未明确说明具体 GPU 型号、数量或训练时长**。
- 仅提到利用 **NVIDIA RTX 射线求交特性** 加速碰撞检测，暗示使用支持 RT 核心的 GPU（如 RTX 系列）。
- 所有仿真运算均在单个或单卡 GPU 上完成，但未给出显存或详细硬件配置。

## 5. 实验数量与充分性

- **实验组数多维覆盖**：
  - BCM 基准：2 种模式（动态/准静态） × 3 种模拟器 = 6 组结果。
  - 效率对比：4 种顶点复杂度 × 4 种模拟器 = 16 组数据。
  - 主实验（伪模式）：7 种服装 × 3 种动作 × 4 种模拟器 = 84 组量化结果（表 2 展示 21 项 × 各 4 指标）。
  - 机器人模式精选抓取任务 × 6 种服装 × 3 模拟器（图 7）。
  - 定性对比与可视化（图 5、6）。
  - 每个数据点带有误差条（反映多次独立试验）。
- **充分性评价**：
  - 覆盖不同材料、结构复杂度、接触动态。
  - 比较当前最主流的三种机器人模拟器，且包含自身模拟器，对比完整。
  - 采用双向指标避免单一偏向性。
  - 总体实验设计充分、可比性强，但缺少真实场景中不同机器人类型/抓取点变化的泛化验证。

## 6. 主要结论与发现

- **BCM 基准精度**：GarmentDynamics 在准静态模式下 **CD 比 SOTA (FLEX) 低 46%**（0.0389 vs 0.072），**HD 低 45%**；动态模式下也最优（CD=0.062）。
- **模拟效率**：
  - 40k 顶点时，步时间仅 **7.4 ms**（Isaac Sim 为 26.6 ms，快 3.6 倍；比 MuJoCo 快 65 倍；比 PyBullet 快 16 倍）。
  - 初始化时间降低 **超过 90%**。
- **Sim-to-real 差距**：
  - 在所有服装与任务上，GarmentDynamics 均显著低于基线，**平均 CD<sub>r2s</sub> 降低超过 37%**（伪模式）。
  - 对拓扑复杂服装（如 Cakeskirt），误差降低 **44%（伪模式）** 与 **77%（机器人模式）**。
  - 动态任务（Fling）差距最大，但 GarmentDynamics 仍保持优势（CD/HD 改善 >20%）。
- 伪模式与机器人模式对比中，机器人模式下误差整体更大，但 GarmentDynamics 仍大幅领先，说明其在完整物理交互中的稳定性。

## 7. 优点

- **全面的基准设计**：包含大量真实服装模型（6000+）与实测物理参数，覆盖多种材料与结构，填补了复杂服装评估空白。
- **高保真模拟器**：使用 FEM 与隐式积分，兼顾精度与稳定性；多级预条件器与 RTX 加速实现高计算性能（3× - 65× 加速）。
- **精细的评估方法**：采用双向 Chamfer / Hausdorff 距离，更公平衡量 sim-to-real 一致性；严格的初始对齐与同步处理提升可比性。
- **开源承诺**：数据集与模拟器计划公开发布，有利于社区后续引用与改进。

## 8. 不足与局限

- **计算资源未开放**：未明确 GPU 型号、并行卡数、训练时间，影响复现性。
- **真实实验范围受限**：仅涉及抓取、甩动、折叠三种基本动作，未涵盖更复杂的操作（如穿脱、折叠收纳、折叠后放置等

等），也未评估不同机器人构型与抓取策略下的泛化能力。
- **材料模型简化**：尽管实测了弹性模量、密度等参数，但模拟中采用线性弹性本构，未考虑布料的非线性、粘弹性及塑性行为，可能影响高动态与剧烈变形场景下的保真度。
- **环境与感知依赖**：评估依赖高精度分割（Grounded-SAM）与深度相机，未测试分割错误、传感器噪声对结果的影响，实际部署时的鲁棒性有待验证。
- **缺乏动态与长期反馈**：仅关注单步操作后的瞬时姿态，未评估长时间序列下仿真与真实轨迹的累积误差，以及重复操作对材料属性退化的模拟。

（完）
