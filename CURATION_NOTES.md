# 整理与去重说明

整理日期：2026-10-07。来源：本地 Zotero 快照。仅生成导出目录，没有修改 Zotero 数据库、收藏夹、笔记或附件。

检查了 290 条非附件有效题录，以及 29 个独立 PDF。最终收录 152 篇论文和 1 份课程讲义，其中 152 份有本地 PDF，去重后每份保留一份附件；1 篇仅保留题录与公开链接。

分类是用于组内阅读的人工主分类，同一论文可以跨主题；并非互斥的正式方法学分类。导读依据题名、摘要及 PDF 前两页，未声称逐篇完成全文精读或复现实验。

## 重复记录与版本合并

按规范化题名、方法名以及本地摘要/PDF 身份核对。以下编号仅用于对应本地快照，不代表发表顺序。

| 保留入口 | 合并的本地条目编号 |
| --- | --- |
| [Low-bit-DNN-Survey](00-surveys/README.md#p-1312) | 1312, 893 |
| [CBQ](02-weight-ptq/README.md#p-66) | 66, 179 |
| [QuaRot](03-activation-transforms/README.md#p-132) | 132, 135 |
| [SpinQuant](03-activation-transforms/README.md#p-62) | 62, 91, 101 |
| [DuQuant](03-activation-transforms/README.md#p-77) | 77, 136 |
| [OstQuant](03-activation-transforms/README.md#p-78) | 78, 86 |
| [FlatQuant](03-activation-transforms/README.md#p-59) | 59, 90 |
| [ParoQuant](03-activation-transforms/README.md#p-1023) | 1023, 1022 |
| [LeanQuant](04-nonuniform-vector-extreme/README.md#p-73) | 73, 72, 174 |
| [Kashin-Quantization](04-nonuniform-vector-extreme/README.md#p-75) | 75, 163 |
| [OneBit](05-qat-adaptation/README.md#p-209) | 209, 216 |
| [Atom](06-kv-cache-systems/README.md#p-133) | 133, 134 |
| [MQuant](07-vision-multimodal/README.md#p-87) | 87, 88, 89, 909 |
| [QSLAW](07-vision-multimodal/README.md#p-925) | 925, 931, 878 |
| [SPEED-Q](07-vision-multimodal/README.md#p-890) | 890, 934 |
| [AKVQ-VL](07-vision-multimodal/README.md#p-885) | 885, 927, 879 |
| [CASP](07-vision-multimodal/README.md#p-886) | 886, 929 |

## 附件归属修正

- Quamba 条目下有一份首页为 DartQuant 的附件，导出时按 DartQuant 归类。
- LeanQuant 条目下有一份首页为 RepQ-ViT 的附件，导出时按 RepQ-ViT 归类。
- 以上修正仅作用于导出；原始 Zotero 保持不变。

## 独立 PDF 与不确定字段

- WPQ、Trainable Vector Quantization、UniQuanF、QQQ、LCQ、DB-LLM、DeltaDQ 等独立 PDF 已按首页题名收录。
- I&S-ViT 的年份来自 PDF 首页正式期刊信息；RepQ-ViT 的 2023 来自所保存 ICCV 2023 PDF 版本。
- 匿名稿缺少可靠年份或作者时保留“未确认”或“Anonymous authors”，不把投稿年份标成已发表年份。
- VLMQ-Hessian-Augmentation 与 VLMQ-Token-Redundancy 的题名和摘要不同，暂保留两个入口；未仅凭相同方法简称合并。
- OWQ 的本地题录与 PDF 使用不同标题，已在对应条目标注。
- 年份通常来自 Zotero 日期字段，可能是预印本修订年份；不构成严格的首发时间线。
- 原文与代码链接优先沿用本地题录/摘要及 PDF arXiv 标记，其中 13 篇核心/相关论文的缺失公开入口已补充并核对；其他链接未逐条联网验证。

## 未纳入主清单的边界条目

以下虽在量化收藏夹内或检索中命中，但摘要主线是其他压缩/适配问题：

| 本地条目 | 题名 | 原因 |
| --- | --- | --- |
| 10 | Revisiting Offline Compression: Going Beyond Factorization-based Methods for Transformer Language Models | 自编码器/离线压缩，非量化主线 |
| 139 | LaCo: Large Language Model Pruning via Layer Collapse | 层剪枝，非量化主线 |
| 159 | SVD-LLM: Truncation-aware Singular Value Decomposition for Large Language Model Compression | 低秩 SVD 压缩，非量化主线 |
| 183 | Implicit Regularization in Deep Matrix Factorization | 矩阵分解的隐式正则化，非量化主线 |
| 186 | Efficient Low-Dimensional Compression of Overparameterized Models | 低维压缩，非量化主线 |
| 189 | Compressible Dynamics in Deep Overparameterized Low-Rank Learning & Adaptation | 低秩学习动力学，非量化主线 |
| 832 | GraLoRA: Granular Low-Rank Adaptation for Parameter-Efficient Fine-Tuning | 参数高效低秩适配，非量化主线 |

SparseGPT、MiniCPM4 等综合压缩或模型报告仅在摘要中涉及量化，本次未扩展为全部相邻领域文献。CASP 的方法包含明确的比特分配与量化步骤，因此收录。

编号 83 原题名只有一个 URL，核对 [NeurIPS 原文](https://proceedings.neurips.cc/paper_files/paper/2024/file/ba92705991cfbbcedc26e27e833ebbae-Paper-Conference.pdf) 后确认为 HaloScope 幻觉检测论文，因此不纳入量化清单。另有 13 篇论文的公开入口通过原始论文页面核对补充。

## 文件完整性

每个收录 PDF 均验证可读取。2026-10-08 已将原 CSV/JSON 文献清单改为 `papers.xlsx`，按原有 10 个分类分表，仅保留论文名字、简介和 AI摘要。AI摘要根据本地摘要及已提取的 PDF 前两页编写，原文入口和版本信息保留在各分类 README。Non-Subtractive Dither 条目没有本地附件，未虚构或下载 PDF。重复论文保留一份代表版本；有实质版本差异时导出不等同于完整版本归档。

PDF 文件名统一为 `年份-方法简称.pdf`，未知年份使用 `undated`。未复制 Zotero 私人笔记、阅读状态文件和原始数据库。
