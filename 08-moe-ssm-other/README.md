# MoE、SSM 与其他模型

[返回总览](../README.md) · 7 份资料

按特殊模型结构组织，包括混合专家、状态空间模型、图网络和联邦应用。

先选一个模型方向：MoE 从 QMoE 开始；SSM 从 Quamba 开始。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| [Quamba](#p-46) | 2024 | SSM 分支:针对选择性状态空间模型中的敏感特征和异常值量化。 |
| [QMoE](#p-184) | 2023 | MoE 入门:压缩海量专家参数,并配合执行框架降低存储需求。 |
| [CodeQuant](#p-974) | 2026 | MoE 分支:联合聚类、旋转平滑和码本表示处理异常值。 |
| [MoE-Generalization-Guarantees](#p-997) | 2026 | MoE 分支:依据专家敏感度分配精度,并分析泛化保证。 |
| [KBVQ-MoE](#p-1019) | 2026 | MoE 分支:结合跨专家低秩结构、向量量化和偏差补偿。 |
| [TopGQ](#p-102) | 未确认 | GNN 分支:利用节点拓扑相似性设计无需重训练的量化。 |
| [Federated-QAT-IoRT](#p-895) | 2026 | 应用拓展:将聚类 QAT 与联邦学习结合用于物联网入侵检测。 |

<a id="p-46"></a>

## Quamba

**Quamba: A Post-Training Quantization Recipe for Selective State Space Models**

SSM 分支：针对选择性状态空间模型中的敏感特征和异常值量化。

- 作者：Hung-Yueh Chiang; Chi-Chih Chang; Natalia Frumkin; Kai-Chiang Wu; Diana Marculescu
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2410.13229) · [作者代码（本地摘要提供）](https://github.com/enyac-group/Quamba)
- PDF：[2024-Quamba.pdf](2024-Quamba.pdf)（27 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-184"></a>

## QMoE

**QMoE: Sub-1-Bit Compression of Trillion-Parameter Models**

MoE 入门：压缩海量专家参数，并配合执行框架降低存储需求。

- 作者：Elias Frantar; Dan Alistarh
- 年份：2023；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://arxiv.org/abs/2310.16795)
- PDF：[2023-QMoE.pdf](2023-QMoE.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-974"></a>

## CodeQuant

**CodeQuant: Unified Clustering and Quantization for Enhanced Outlier Smoothing in Low-Precision Mixture-of-Experts**

MoE 分支：联合聚类、旋转平滑和码本表示处理异常值。

- 作者：Xiangyang Yin; Xingyu Liu; Tianhua Xia; Vithursan Thangarasa; Valavan Manohararajah; Eric Sather; Sai Qian Zhang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=CodeQuant%3A%20Unified%20Clustering%20and%20Quantization%20for%20Enhanced%20Outlier%20Smoothing%20in%20Low-Precision%20Mixture-of-Experts)（检索入口，非已核实原文链接）
- PDF：[2026-CodeQuant.pdf](2026-CodeQuant.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-997"></a>

## MoE-Generalization-Guarantees

**Efficient Quantization of Mixture-of-Experts with Theoretical Generalization Guarantees**

MoE 分支：依据专家敏感度分配精度，并分析泛化保证。

- 作者：Mohammed Nowaz Rabbani Chowdhury; Kaoutar El Maghraoui; Hsinyu Tsai; Naigang Wang; Geoffrey W Burr; Liu Liu; Meng Wang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Efficient%20Quantization%20of%20Mixture-of-Experts%20with%20Theoretical%20Generalization%20Guarantees)（检索入口，非已核实原文链接）
- PDF：[2026-MoE-Generalization-Guarantees.pdf](2026-MoE-Generalization-Guarantees.pdf)（36 页）
- 导读依据：本地 PDF 前两页。

<a id="p-1019"></a>

## KBVQ-MoE

**KBVQ-MoE: KLT-guided SVD with Bias-Corrected Vector Quantization for MoE Large Language Models**

MoE 分支：结合跨专家低秩结构、向量量化和偏差补偿。

- 作者：Zukang Xu; Zhixiong Zhao; Xing Hu; Zhixuan Chen; Dawei Yang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.11184)
- PDF：[2026-KBVQ-MoE.pdf](2026-KBVQ-MoE.pdf)（23 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-102"></a>

## TopGQ

**TopGQ: Post-Training Quantization for GNNs Leveraging Topological Similarity within Nodes**

GNN 分支：利用节点拓扑相似性设计无需重训练的量化。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=TopGQ%3A%20Post-Training%20Quantization%20for%20GNNs%20Leveraging%20Topological%20Similarity%20within%20Nodes)（检索入口，非已核实原文链接）
- PDF：[undated-TopGQ.pdf](undated-TopGQ.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-895"></a>

## Federated-QAT-IoRT

**Federated DDoS Detection with Clustered Quantization-Aware Training Models for IoRT**

应用拓展：将聚类 QAT 与联邦学习结合用于物联网入侵检测。

- 作者：Matilda Nkoom; Daniel Commey; Yousef Alsenani; Sena G. Hounsinou; Garth V. Crosby
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/11366492/)
- PDF：[2026-Federated-QAT-IoRT.pdf](2026-Federated-QAT-IoRT.pdf)（6 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
