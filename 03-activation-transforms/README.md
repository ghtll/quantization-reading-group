# 激活异常值与等价变换

[返回总览](../README.md) · 22 份资料

通过缩放、重排、旋转或仿射变换改善量化分布；也纳入解释异常值来源的分析论文。

主线：LLM.int8() → SmoothQuant → OmniQuant → QuaRot → SpinQuant；再阅读 FlatQuant、DuQuant 等变体。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| ⭐ [LLM-int8](#p-197) | 2022 | 核心必读:认识大模型中的异常特征及混合精度矩阵乘法。 |
| ⭐ [SmoothQuant](#p-202) | 2023 | 核心必读:通过等价缩放把激活量化难度迁移到权重。 |
| [Massive-Activations](#p-124) | 2024 | 现象分析:定位巨大激活值,并理解其与注意力和偏置的关系。 |
| [RPTQ](#p-175) | 2023 | 按通道数值范围重排并分组量化,缓解通道间差异。 |
| ⭐ [OmniQuant](#p-200) | 2024 | 学习裁剪和等价变换参数,改善低比特量化校准。 |
| [AffineQuant](#p-162) | 2024 | 将缩放扩展为可学习仿射变换,扩大量化优化空间。 |
| [LRQuant](#p-141) | 2024 | 学习平滑参数,并关注量化模型对未见数据的稳健性。 |
| ⭐ [QuaRot](#p-132) | 2024 | 核心必读:利用旋转的等价性分散异常值,实现低比特推理。 |
| ⭐ [SpinQuant](#p-62) | 2025 | 学习旋转矩阵,比较随机旋转与任务驱动旋转的差异。 |
| [DuQuant](#p-77) | 2024 | 结合分块旋转和置换,分散普通异常值与巨大异常值。 |
| [OstQuant](#p-78) | 2025 | 联合正交与缩放变换,改善数据分布对量化空间的利用。 |
| [FlatQuant](#p-59) | 2025 | 用可学习仿射变换展平分布,关注精度与在线变换开销。 |
| [PrefixQuant](#p-54) | 2025 | 用前缀 token 隔离 token 级异常值,改善静态量化。 |
| [DFRot](#p-61) | 2025 | 分析旋转后残留的异常激活,并设计更细致的旋转策略。 |
| [BASE-Q](#p-63) | 2025 | 在旋转外加入偏置和非对称缩放,进一步调整分布。 |
| [DartQuant](#p-800) | 未确认 | 面向量化分布进行旋转校准,减少旋转优化开销。 |
| [AdaQTransform](#p-821) | 2025 | 通过量化步长解耦与自适应变换扩大 PTQ 优化空间。 |
| [RoMeo](#p-899) | 2026 | 结合旋转与混合精度,处理两个维度上的异常值。 |
| [OFQ-LLM](#p-950) | 2025 | 围绕异常值处理设计低比特 LLM 量化与加速方法。 |
| [ParoQuant](#p-1023) | 2026 | 结合成对 Givens 旋转、通道缩放与推理内核,面向推理型 LLM。 |
| [STaMP](#p-1082) | 2025 | 沿序列维度变换激活,并以少量高精度 token 保留信息。 |
| [RUQuant](#p-1308) | 2026 | 从 Lloyd-Max 条件出发,用分阶段正交变换改善均匀量化。 |

<a id="p-197"></a>

## LLM-int8

**LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale**

核心必读：认识大模型中的异常特征及混合精度矩阵乘法。

- 作者：Tim Dettmers; Mike Lewis; Younes Belkada; Luke Zettlemoyer
- 年份：2022；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://arxiv.org/abs/2208.07339)
- PDF：[2022-LLM-int8.pdf](2022-LLM-int8.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-202"></a>

## SmoothQuant

**SmoothQuant: Accurate and Efficient Post-Training Quantization for Large Language Models**

核心必读：通过等价缩放把激活量化难度迁移到权重。

- 作者：Guangxuan Xiao; Ji Lin; Mickael Seznec; Hao Wu; Julien Demouth; Song Han
- 年份：2023；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.mlr.press/v202/xiao23c.html)
- PDF：[2023-SmoothQuant.pdf](2023-SmoothQuant.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-124"></a>

## Massive-Activations

**Massive Activations in Large Language Models**

现象分析：定位巨大激活值，并理解其与注意力和偏置的关系。

- 作者：Mingjie Sun; Xinlei Chen; J. Zico Kolter; Zhuang Liu
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.17762) · [作者代码（本地摘要提供）](https://github.com/locuslab/massive-activations)
- PDF：[2024-Massive-Activations.pdf](2024-Massive-Activations.pdf)（32 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-175"></a>

## RPTQ

**RPTQ: Reorder-based Post-training Quantization for Large Language Models**

按通道数值范围重排并分组量化，缓解通道间差异。

- 作者：Zhihang Yuan; Lin Niu; Jiawei Liu; Wenyu Liu; Xinggang Wang; Yuzhang Shang; Guangyu Sun; Qiang Wu; Jiaxiang Wu; Bingzhe Wu
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2304.01089) · [作者代码（本地摘要提供）](https://github.com/hahnyuan/RPTQ4LLM)
- PDF：[2023-RPTQ.pdf](2023-RPTQ.pdf)（18 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-200"></a>

## OmniQuant

**OmniQuant: Omnidirectionally Calibrated Quantization for Large Language Models**

学习裁剪和等价变换参数，改善低比特量化校准。

- 作者：Wenqi Shao; Mengzhao Chen; Zhaoyang Zhang; Peng Xu; Lirui Zhao; Zhiqian Li; Kaipeng Zhang; Peng Gao; Yu Qiao; Ping Luo
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2308.13137) · [作者代码（本地摘要提供）](https://github.com/OpenGVLab/OmniQuant)
- PDF：[2024-OmniQuant.pdf](2024-OmniQuant.pdf)（25 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-162"></a>

## AffineQuant

**AffineQuant: Affine Transformation Quantization for Large Language Models**

将缩放扩展为可学习仿射变换，扩大量化优化空间。

- 作者：Yuexiao Ma; Huixia Li; Xiawu Zheng; Feng Ling; Xuefeng Xiao; Rui Wang; Shilei Wen; Fei Chao; Rongrong Ji
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2403.12544)
- PDF：[2024-AffineQuant.pdf](2024-AffineQuant.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-141"></a>

## LRQuant

**LRQuant: Learnable and Robust Post-Training Quantization for Large Language Models**

学习平滑参数，并关注量化模型对未见数据的稳健性。

- 作者：Jiaqi Zhao; Miao Zhang; Chao Zeng; Ming Wang; Xuebo Liu; Liqiang Nie
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://aclanthology.org/2024.acl-long.122) · [作者代码（本地摘要提供）](https://github.com/zjq0455/RLQ)
- PDF：[2024-LRQuant.pdf](2024-LRQuant.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-132"></a>

## QuaRot

**QuaRot: Outlier-Free 4-Bit Inference in Rotated LLMs**

核心必读：利用旋转的等价性分散异常值，实现低比特推理。

- 作者：Saleh Ashkboos; Amirkeivan Mohtashami; Maximilian L. Croci; Bo Li; Pashmina Cameron; Martin Jaggi; Dan Alistarh; Torsten Hoefler; James Hensman
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2404.00456) · [作者代码（本地摘要提供）](https://github.com/spcl/QuaRot)
- PDF：[2024-QuaRot.pdf](2024-QuaRot.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-62"></a>

## SpinQuant

**SpinQuant: LLM quantization with learned rotations**

学习旋转矩阵，比较随机旋转与任务驱动旋转的差异。

- 作者：Zechun Liu; Changsheng Zhao; Igor Fedorov; Bilge Soran; Dhruv Choudhary; Raghuraman Krishnamoorthi; Vikas Chandra; Yuandong Tian; Tijmen Blankevoort
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2405.16406) · [作者代码（本地摘要提供）](https://github.com/facebookresearch/SpinQuant)
- PDF：[2025-SpinQuant.pdf](2025-SpinQuant.pdf)（24 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-77"></a>

## DuQuant

**DuQuant: Distributing Outliers via Dual Transformation Makes Stronger Quantized LLMs**

结合分块旋转和置换，分散普通异常值与巨大异常值。

- 作者：Haokun Lin; Haobo Xu; Yichen Wu; Jingzhi Cui; Yingtao Zhang; Linzhan Mou; Linqi Song; Zhenan Sun; Ying Wei
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2406.01721) · [作者代码（本地摘要提供）](https://github.com/Hsu1023/DuQuant)
- PDF：[2024-DuQuant.pdf](2024-DuQuant.pdf)（29 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-78"></a>

## OstQuant

**OstQuant: Refining Large Language Model Quantization with Orthogonal and Scaling Transformations for Better Distribution Fitting**

联合正交与缩放变换，改善数据分布对量化空间的利用。

- 作者：Xing Hu; Yuan Cheng; Dawei Yang; Zukang Xu; Zhihang Yuan; Jiangyong Yu; Chen Xu; Zhe Jiang; Sifan Zhou
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2501.13987) · [作者代码（本地摘要提供）](https://github.com/BrotherHappy/OSTQuant)
- PDF：[2025-OstQuant.pdf](2025-OstQuant.pdf)（27 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-59"></a>

## FlatQuant

**FlatQuant: Flatness Matters for LLM Quantization**

用可学习仿射变换展平分布，关注精度与在线变换开销。

- 作者：Yuxuan Sun; Ruikang Liu; Haoli Bai; Han Bao; Kang Zhao; Yuening Li; Jiaxin Hu; Xianzhi Yu; Lu Hou; Chun Yuan; Xin Jiang; Wulong Liu; Jun Yao
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2410.09426) · [作者代码（本地摘要提供）](https://github.com/ruikangliu/FlatQuant)
- PDF：[2025-FlatQuant.pdf](2025-FlatQuant.pdf)（25 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-54"></a>

## PrefixQuant

**PrefixQuant: Eliminating Outliers by Prefixed Tokens for Large Language Models Quantization**

用前缀 token 隔离 token 级异常值，改善静态量化。

- 作者：Mengzhao Chen; Yi Liu; Jiahao Wang; Yi Bin; Wenqi Shao; Ping Luo
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2410.05265) · [作者代码（本地摘要提供）](https://github.com/ChenMnZ/PrefixQuant)
- PDF：[2025-PrefixQuant.pdf](2025-PrefixQuant.pdf)（23 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-61"></a>

## DFRot

**DFRot: Achieving Outlier-Free and Massive Activation-Free for Rotated LLMs with Refined Rotation**

分析旋转后残留的异常激活，并设计更细致的旋转策略。

- 作者：Jingyang Xiang; Sai Qian Zhang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2412.00648)
- PDF：[2025-DFRot.pdf](2025-DFRot.pdf)（34 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-63"></a>

## BASE-Q

**BASE-Q: Bias and Asymmetric Scaling Enhanced Rotational Quantization for Large Language Models**

在旋转外加入偏置和非对称缩放，进一步调整分布。

- 作者：Liulu He; Shenli Zheng; Karwei Sun; Yijiang Liu; Yufei Zhao; Chongkang Tan; Huanrui Yang; Yuan Du; Li Du
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2506.15689) · [作者代码（本地摘要提供）](https://github.com/Heliulu/BASE-Q)
- PDF：[2025-BASE-Q.pdf](2025-BASE-Q.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-800"></a>

## DartQuant

**DartQuant: Efficient Rotational Distribution Calibration for LLM Quantization**

面向量化分布进行旋转校准，减少旋转优化开销。

- 作者：Yuantian Shao; Yuanteng Chen; Peisong Wang; Jianlin Yu; Jing Lin; Yiwu Yao; Zhihui Wei; Jian Cheng
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=DartQuant%3A%20Efficient%20Rotational%20Distribution%20Calibration%20for%20LLM%20Quantization)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/CAS-CLab/DartQuant.git)
- PDF：[undated-DartQuant.pdf](undated-DartQuant.pdf)（35 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已从其他题录下识别并归回匹配的 PDF 附件；未修改 Zotero。

<a id="p-821"></a>

## AdaQTransform

**From Decoupling to Adaptive Transformation: A Wider Optimization Space for PTQ**

通过量化步长解耦与自适应变换扩大 PTQ 优化空间。

- 作者：Zhaojing Wen; Qiulin Zhang; Yuan Zhang; Rudan Chen; Xichao Yang; Di Xie; Jiang Zhu
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=From%20Decoupling%20to%20Adaptive%20Transformation%3A%20A%20Wider%20Optimization%20Space%20for%20PTQ)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/zjxyz/AdaQTransform)
- PDF：[2025-AdaQTransform.pdf](2025-AdaQTransform.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-899"></a>

## RoMeo

**RoMeo: Mitigating Dual-dimensional Outliers with Rotated Mixed Precision Quantization**

结合旋转与混合精度，处理两个维度上的异常值。

- 作者：Qihao Zhang; MingLiang Tang; Mingshu Zhai; Kinman Lei; Jidong Zhai
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3774934.3786419)
- PDF：[2026-RoMeo.pdf](2026-RoMeo.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-950"></a>

## OFQ-LLM

**OFQ-LLM: Outlier-Flexing Quantization for Efficient Low-Bit Large Language Model Acceleration**

围绕异常值处理设计低比特 LLM 量化与加速方法。

- 作者：Gang Wang; Siqi Cai; Wenjie Li; Dongxu Lyu; Guanghui He
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/10924797/)
- PDF：[2025-OFQ-LLM.pdf](2025-OFQ-LLM.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1023"></a>

## ParoQuant

**ParoQuant: Pairwise Rotation Quantization for Efficient Reasoning LLM Inference**

结合成对 Givens 旋转、通道缩放与推理内核，面向推理型 LLM。

- 作者：Yesheng Liang; Haisheng Chen; Zihan Zhang; Song Han; Zhijian Liu
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2511.10645)
- PDF：[2026-ParoQuant.pdf](2026-ParoQuant.pdf)（18 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-1082"></a>

## STaMP

**STaMP: Sequence Transformation and Mixed Precision for Low-Precision Activation Quantization**

沿序列维度变换激活，并以少量高精度 token 保留信息。

- 作者：Marco Federici; Riccardo Del Chiaro; Boris van Breugel; Paul Whatmough; Markus Nagel
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2510.26771)
- PDF：[2025-STaMP.pdf](2025-STaMP.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1308"></a>

## RUQuant

**RUQuant: Towards Refining Uniform Quantization for Large Language Models**

从 Lloyd-Max 条件出发，用分阶段正交变换改善均匀量化。

- 作者：Han Liu; Haotian Gao; Changya Li; Feng Zhang; Xiaotong Zhang; Wei Wang; Hong Yu
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2604.04013)
- PDF：[2026-RUQuant.pdf](2026-RUQuant.pdf)（12 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
