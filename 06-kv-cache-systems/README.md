# KV Cache 与推理系统

[返回总览](../README.md) · 17 份资料

关注长上下文缓存、存储与计算精度、GPU 内核和端到端服务效率。

KV 分支：IntactKV → CommVQ/TurboQuant → JanusQuant。服务分支：Atom → QServe → FP4/MicroMix。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| [IntactKV](#p-125) | 2024 | 保留关键起始 token 的高精度 KV,以改善量化模型精度。 |
| [JanusQuant](#p-897) | 2026 | 面向长上下文的 2-bit KV 量化,结合变换与注意力内核。 |
| [ChanMix](#p-958) | 2026 | 按 KV 通道的量化敏感度分配比特预算。 |
| [CommVQ](#p-1297) | 2025 | 设计可与 RoPE 交换的加性码本,降低 KV 解码开销。 |
| [TurboQuant](#p-1300) | 2025 | 研究在线向量量化的失真界,并应用于 KV 缓存压缩。 |
| [Atom](#p-133) | 2024 | 核心系统阅读:将混合精度低比特量化用于高吞吐 LLM 服务。 |
| ⭐ [QServe](#p-172) | 2024 | 核心系统阅读:联合 W4A8KV4 量化与系统设计,减少反量化开销。 |
| [BitMoD](#p-68) | 2025 | 细粒度混合数据类型与位串行硬件协同设计。 |
| [Compressibility-of-Quantized-LLMs](#p-181) | 2024 | 研究量化之后继续采用数据压缩的空间与代价。 |
| [Dual-Precision-Quantization](#p-917) | 未确认 | 区分存储精度和计算精度,设计兼顾吞吐与精度的表示。 |
| [FlexQ](#p-946) | 2025 | 面向 INT6 LLM 服务进行算法与系统协同设计。 |
| [Microscaling-FP4-MR-GPTQ](#p-1013) | 2026 | 分析微缩放 FP4 的误差并结合量化算法与 GPU 内核改进。 |
| [MicroMix](#p-1071) | 2026 | 结合微缩放浮点格式的混合精度分配与矩阵乘法内核。 |
| [AnyBCQ](#p-1040) | 2026 | 利用二进制编码支持可变精度,并设计相应推理内核。 |
| [QTALE](#p-941) | 2026 | 联合 token 自适应跳层与量化,研究两种压缩方式的相互影响。 |
| [UniQL](#p-1060) | 2026 | 联合量化与低秩压缩,支持边缘端调整模型压缩率。 |
| [QQQ](#p-173) | 未确认 | 独立匿名稿:结合平滑、二阶补偿与 W4A8 内核加速推理。 |

<a id="p-125"></a>

## IntactKV

**IntactKV: Improving Large Language Model Quantization by Keeping Pivot Tokens Intact**

保留关键起始 token 的高精度 KV，以改善量化模型精度。

- 作者：Ruikang Liu; Haoli Bai; Haokun Lin; Yuening Li; Han Gao; Zhengzhuo Xu; Lu Hou; Jun Yao; Chun Yuan
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2403.01241) · [作者代码（本地摘要提供）](https://github.com/ruikangliu/IntactKV)
- PDF：[2024-IntactKV.pdf](2024-IntactKV.pdf)（26 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-897"></a>

## JanusQuant

**JanusQuant: Accurate and Efficient 2-bit KV Cache Quantization for Long-Context Inference**

面向长上下文的 2-bit KV 量化，结合变换与注意力内核。

- 作者：Chengyu Sun; Yaqi Xia; Hulin Wang; Donglin Yang; Xiaobo Zhou; Dazhao Cheng
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3774934.3786428)
- PDF：[2026-JanusQuant.pdf](2026-JanusQuant.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-958"></a>

## ChanMix

**Channel-Aware Mixed-Precision Quantization for Efficient Long-Context Inference**

按 KV 通道的量化敏感度分配比特预算。

- 作者：Chengxi Liao; Zeyi Wen
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Channel-Aware%20Mixed-Precision%20Quantization%20for%20Efficient%20Long-Context%20Inference)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/cxiliao/ChanMix)
- PDF：[2026-ChanMix.pdf](2026-ChanMix.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1297"></a>

## CommVQ

**CommVQ: Commutative Vector Quantization for KV Cache Compression**

设计可与 RoPE 交换的加性码本，降低 KV 解码开销。

- 作者：Junyan Li; Yang Zhang; Muhammad Yusuf Hassan; Talha Chafekar; Tianle Cai; Zhile Ren; Pengsheng Guo; Foroozan Karimzadeh; Colorado Reed; Chong Wang; Chuang Gan
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2506.18879)
- PDF：[2025-CommVQ.pdf](2025-CommVQ.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1300"></a>

## TurboQuant

**TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate**

研究在线向量量化的失真界，并应用于 KV 缓存压缩。

- 作者：Amir Zandieh; Majid Daliri; Majid Hadian; Vahab Mirrokni
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2504.19874)
- PDF：[2025-TurboQuant.pdf](2025-TurboQuant.pdf)（25 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-133"></a>

## Atom

**Atom: Low-bit Quantization for Efficient and Accurate LLM Serving**

核心系统阅读：将混合精度低比特量化用于高吞吐 LLM 服务。

- 作者：Yilong Zhao; Chien-Yu Lin; Kan Zhu; Zihao Ye; Lequn Chen; Size Zheng; Luis Ceze; Arvind Krishnamurthy; Tianqi Chen; Baris Kasikci
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2310.19102)
- PDF：[2024-Atom.pdf](2024-Atom.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-172"></a>

## QServe

**QServe: W4A8KV4 Quantization and System Co-design for Efficient LLM Serving**

核心系统阅读：联合 W4A8KV4 量化与系统设计，减少反量化开销。

- 作者：Yujun Lin; Haotian Tang; Shang Yang; Zhekai Zhang; Guangxuan Xiao; Chuang Gan; Song Han
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2405.04532) · [作者代码（本地摘要提供）](https://github.com/mit-han-lab/qserve)
- PDF：[2024-QServe.pdf](2024-QServe.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-68"></a>

## BitMoD

**BitMoD: Bit-serial Mixture-of-Datatype LLM Acceleration**

细粒度混合数据类型与位串行硬件协同设计。

- 作者：Yuzong Chen; Ahmed F. AbouElhamayed; Xilai Dai; Yang Wang; Marta Andronic; George A. Constantinides; Mohamed S. Abdelfattah
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/10946739/)
- PDF：[2025-BitMoD.pdf](2025-BitMoD.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-181"></a>

## Compressibility-of-Quantized-LLMs

**On the Compressibility of Quantized Large Language Models**

研究量化之后继续采用数据压缩的空间与代价。

- 作者：Yu Mao; Weilan Wang; Hongchao Du; Nan Guan; Chun Jason Xue
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2403.01384)
- PDF：[2024-Compressibility-of-Quantized-LLMs.pdf](2024-Compressibility-of-Quantized-LLMs.pdf)（5 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-917"></a>

## Dual-Precision-Quantization

**Dual Precision Quantization for Efficient and Accurate Deep Neural Networks Inference**

区分存储精度和计算精度，设计兼顾吞吐与精度的表示。

- 作者：Tomer Gafni; Asaf Karnieli; Yair Hanani
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Dual%20Precision%20Quantization%20for%20Efficient%20and%20Accurate%20Deep%20Neural%20Networks%20Inference)（检索入口，非已核实原文链接）
- PDF：[undated-Dual-Precision-Quantization.pdf](undated-Dual-Precision-Quantization.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-946"></a>

## FlexQ

**FlexQ: Efficient Post-training INT6 Quantization for LLM Serving via Algorithm-System Co-Design**

面向 INT6 LLM 服务进行算法与系统协同设计。

- 作者：Hao Zhang; Aining Jia; Weifeng Bu; Yushu Cai; Kai Sheng; Hao Chen; Xin He
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2508.04405)
- PDF：[2025-FlexQ.pdf](2025-FlexQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1013"></a>

## Microscaling-FP4-MR-GPTQ

**Bridging the Gap Between Promise and Performance for Microscaling FP4 Quantization**

分析微缩放 FP4 的误差并结合量化算法与 GPU 内核改进。

- 作者：Vage Egiazarian; Roberto L. Castro; Denis Kuznedelev; Andrei Panferov; Eldar Kurtic; Shubhra Pandit; Alexandre Marques; Mark Kurtz; Saleh Ashkboos; Torsten Hoefler; Dan Alistarh
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2509.23202)
- PDF：[2026-Microscaling-FP4-MR-GPTQ.pdf](2026-Microscaling-FP4-MR-GPTQ.pdf)（35 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1071"></a>

## MicroMix

**MicroMix: Efficient Mixed-Precision Quantization with Microscaling Formats for Large Language Models**

结合微缩放浮点格式的混合精度分配与矩阵乘法内核。

- 作者：Wenyuan Liu; Haoqian Meng; Yilun Luo; Yafei Zhao; Peng Zhang; Xindian Ma
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2508.02343) · [作者代码（本地摘要提供）](https://github.com/lwy2020/MicroMix)
- PDF：[2026-MicroMix.pdf](2026-MicroMix.pdf)（20 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1040"></a>

## AnyBCQ

**AnyBCQ: Hardware Efficient Flexible Binary-Coded Quantization for Multi-Precision LLMs**

利用二进制编码支持可变精度，并设计相应推理内核。

- 作者：Gunho Park; Jeongin Bae; Beomseok Kwon; Byeongwook Kim; Se Jung Kwon; Dongsoo Lee
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2510.10467)
- PDF：[2026-AnyBCQ.pdf](2026-AnyBCQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-941"></a>

## QTALE

**QTALE: Quantization-Robust Token-Adaptive Layer Execution for LLMs**

联合 token 自适应跳层与量化，研究两种压缩方式的相互影响。

- 作者：Kanghyun Noh; Jinheon Choi; Yulhwa Kim
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.10431)
- PDF：[2026-QTALE.pdf](2026-QTALE.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1060"></a>

## UniQL

**UniQL: Unified Quantization and Low-rank Compression for Adaptive Edge LLMs**

联合量化与低秩压缩，支持边缘端调整模型压缩率。

- 作者：Hung-Yueh Chiang; Chi-Chih Chang; Yu-Chen Lu; Chien-Yu Lin; Kai-Chiang Wu; Mohamed S. Abdelfattah; Diana Marculescu
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2512.03383) · [作者代码（本地摘要提供）](https://github.com/enyac-group/UniQL)
- PDF：[2026-UniQL.pdf](2026-UniQL.pdf)（24 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-173"></a>

## QQQ

**QQQ: Quality Quattuor-Bit Quantization for Large Language Models**

独立匿名稿：结合平滑、二阶补偿与 W4A8 内核加速推理。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=QQQ%3A%20Quality%20Quattuor-Bit%20Quantization%20for%20Large%20Language%20Models)（检索入口，非已核实原文链接）
- PDF：[undated-QQQ.pdf](undated-QQQ.pdf)（10 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。
