# 非均匀、向量与超低比特表示

[返回总览](../README.md) · 23 份资料

关注量化网格、码本、二值表示和有效位数；部分方法同时使用旋转或训练。

主线：SqueezeLLM → QuIP → QuIP# → AQLM → GPTVQ/VPTQ；二值分支从 PB-LLM、BiLLM 进入。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| [SqueezeLLM](#p-49) | 2024 | 结合敏感度驱动的非均匀量化与稠密/稀疏分解。 |
| [Piecewise-Linear-Quantization](#p-64) | 2020 | 以分段线性网格改善低比特数值近似。 |
| [LeanQuant](#p-73) | 2025 | 根据损失误差和逆 Hessian 信息学习量化网格。 |
| [Kashin-Quantization](#p-75) | 2024 | 利用冗余基与 Kashin 表示改善量化前的数值分布。 |
| [QuIP](#p-208) | 2023 | 学习非相干预处理与带理论保证的超低比特权重量化。 |
| ⭐ [QuIP-sharp](#p-192) | 2024 | 结合 Hadamard 非相干变换和格码本,阅读标量到向量量化的过渡。 |
| ⭐ [AQLM](#p-210) | 2024 | 核心进阶:用多个可学习码本相加表示权重,并跨块优化。 |
| [GPTVQ](#p-69) | 2025 | 将二阶重构扩展到向量量化,研究码本维度与精度的关系。 |
| [VPTQ](#p-70) | 2024 | 结合二阶优化与向量码本,面向极低比特权重表示。 |
| [PCDVQ](#p-901) | 2025 | 把向量方向与模长解耦,分别构造匹配分布的码本。 |
| [BiLLM](#p-167) | 2024 | 区分显著权重与普通权重,并用二值残差逼近压缩权重。 |
| [PB-LLM](#p-168) | 2023 | 部分权重二值化、少量显著权重保留高精度;同时讨论 PTQ/QAT。 |
| [PTQ1-61](#p-782) | 未确认 | 用结构化显著通道掩码降低额外位开销,探索低于 2 bit 的 PTQ。 |
| [NanoQuant](#p-936) | 2026 | 将权重量化建模为低秩二值分解,探索低于 1 bit 的表示。 |
| [SEMQ](#p-830) | 2026 | 结合敏感度误差最小化和异常值分离设计非均匀量化。 |
| [Logarithmic-Quantization](#p-863) | 2018 | 分析对数量化的适用分布及小型网络中的精度损失。 |
| [LogART](#p-1030) | 2026 | 在对数域学习舍入,并自适应选择量化基数。 |
| [BPDQ](#p-953) | 2026 | 用比特平面与系数构造可变网格,再进行二阶误差补偿。 |
| [BOF4](#p-1007) | 2025 | 分析块内归一化后的分布,设计 4-bit 最优浮点表示。 |
| [WPQ](#p-98) | 未确认 | 独立匿名稿:结合乘积量化、平滑与共享码本压缩 LLM。 |
| [Trainable-Vector-Quantization](#p-99) | 未确认 | 独立匿名稿:用 STE 和隐变量让向量量化权重参与梯度优化。 |
| [UniQuanF](#p-100) | 未确认 | 独立匿名稿:结合均匀量化的可优化性与二进制编码的表示能力。 |
| [LCQ](#p-193) | 未确认 | 独立匿名稿:使用低秩码本提升权重量化的表示能力。 |

<a id="p-49"></a>

## SqueezeLLM

**SqueezeLLM: Dense-and-Sparse Quantization**

结合敏感度驱动的非均匀量化与稠密/稀疏分解。

- 作者：Sehoon Kim; Coleman Hooper; Amir Gholami; Zhen Dong; Xiuyu Li; Sheng Shen; Michael W. Mahoney; Kurt Keutzer
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2306.07629) · [作者代码（本地摘要提供）](https://github.com/SqueezeAILab/SqueezeLLM)
- PDF：[2024-SqueezeLLM.pdf](2024-SqueezeLLM.pdf)（23 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-64"></a>

## Piecewise-Linear-Quantization

**Post-Training Piecewise Linear Quantization for Deep Neural Networks**

以分段线性网格改善低比特数值近似。

- 作者：Jun Fang; Ali Shafiee; Hamzah Abdel-Aziz; David Thorsley; Georgios Georgiadis; Joseph Hassoun
- 年份：2020；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2002.00104)
- PDF：[2020-Piecewise-Linear-Quantization.pdf](2020-Piecewise-Linear-Quantization.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-73"></a>

## LeanQuant

**LeanQuant: Accurate and Scalable Large Language Model Quantization with Loss-Error-Aware Grid**

根据损失误差和逆 Hessian 信息学习量化网格。

- 作者：Tianyi Zhang; Anshumali Shrivastava
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=LeanQuant%3A%20Accurate%20and%20Scalable%20Large%20Language%20Model%20Quantization%20with%20Loss-Error-Aware%20Grid)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/LeanModels/LeanQuant)
- PDF：[2025-LeanQuant.pdf](2025-LeanQuant.pdf)（24 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-75"></a>

## Kashin-Quantization

**Quantization of Large Language Models with an Overdetermined Basis**

利用冗余基与 Kashin 表示改善量化前的数值分布。

- 作者：Daniil Merkulov; Daria Cherniuk; Alexander Rudikov; Ivan Oseledets; Ekaterina Muravleva; Aleksandr Mikhalev; Boris Kashin
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2404.09737)
- PDF：[2024-Kashin-Quantization.pdf](2024-Kashin-Quantization.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-208"></a>

## QuIP

**QuIP: 2-Bit Quantization of Large Language Models With Guarantees**

学习非相干预处理与带理论保证的超低比特权重量化。

- 作者：Jerry Chee; Volodymyr Kuleshov; Yaohui Cai
- 年份：2023；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.neurips.cc/paper_files/paper/2023/hash/0df38cd13520747e1e64e5b123a78ef8-Abstract-Conference.html) · [作者代码（本地摘要提供）](https://github.com/Cornell-RelaxML/QuIP)
- PDF：[2023-QuIP.pdf](2023-QuIP.pdf)（34 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-192"></a>

## QuIP-sharp

**QuIP#: Even Better LLM Quantization with Hadamard Incoherence and Lattice Codebooks**

结合 Hadamard 非相干变换和格码本，阅读标量到向量量化的过渡。

- 作者：Albert Tseng; Jerry Chee; Qingyao Sun; Volodymyr Kuleshov; Christopher De Sa
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.04396)
- PDF：[2024-QuIP-sharp.pdf](2024-QuIP-sharp.pdf)（23 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-210"></a>

## AQLM

**Extreme Compression of Large Language Models via Additive Quantization**

核心进阶：用多个可学习码本相加表示权重，并跨块优化。

- 作者：Anonymous Authors
- 年份：2024；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.mlr.press/v235/egiazarian24a.html)
- PDF：[2024-AQLM.pdf](2024-AQLM.pdf)（18 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份；公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-69"></a>

## GPTVQ

**GPTVQ: The Blessing of Dimensionality for LLM Quantization**

将二阶重构扩展到向量量化，研究码本维度与精度的关系。

- 作者：Mart van Baalen; Andrey Kuzmin; Ivan Koryakovskiy; Markus Nagel; Peter Couperus; Cedric Bastoul; Eric Mahurin; Tijmen Blankevoort; Paul Whatmough
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.15319)
- PDF：[2025-GPTVQ.pdf](2025-GPTVQ.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-70"></a>

## VPTQ

**VPTQ: Extreme Low-bit Vector Post-Training Quantization for Large Language Models**

结合二阶优化与向量码本，面向极低比特权重表示。

- 作者：Yifei Liu; Jicheng Wen; Yang Wang; Shengyu Ye; Li Lyna Zhang; Ting Cao; Cheng Li; Mao Yang
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2409.17066)
- PDF：[2024-VPTQ.pdf](2024-VPTQ.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-901"></a>

## PCDVQ

**PCDVQ: Enhancing Vector Quantization for Large Language Models via Polar Coordinate Decoupling**

把向量方向与模长解耦，分别构造匹配分布的码本。

- 作者：Yuxuan Yue; Zukang Xu; Zhihang Yuan; Dawei Yang; Jianlong Wu; Liqiang Nie
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2506.05432)
- PDF：[2025-PCDVQ.pdf](2025-PCDVQ.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-167"></a>

## BiLLM

**BiLLM: Pushing the Limit of Post-Training Quantization for LLMs**

区分显著权重与普通权重，并用二值残差逼近压缩权重。

- 作者：Wei Huang; Yangdong Liu; Haotong Qin; Ying Li; Shiming Zhang; Xianglong Liu; Michele Magno; Xiaojuan Qi
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.04291) · [作者代码（本地摘要提供）](https://github.com/Aaronhuang-778/BiLLM)
- PDF：[2024-BiLLM.pdf](2024-BiLLM.pdf)（20 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-168"></a>

## PB-LLM

**PB-LLM: Partially Binarized Large Language Models**

部分权重二值化、少量显著权重保留高精度；同时讨论 PTQ/QAT。

- 作者：Yuzhang Shang; Zhihang Yuan; Qiang Wu; Zhen Dong
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2310.00034)
- PDF：[2023-PB-LLM.pdf](2023-PB-LLM.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-782"></a>

## PTQ1-61

**PTQ1.61: Push the Real Limit of Extremely Low-Bit Post-Training Quantization Methods for Large Language Models**

用结构化显著通道掩码降低额外位开销，探索低于 2 bit 的 PTQ。

- 作者：Jiaqi Zhao; Miao Zhang; Ming Wang; Yuzhang Shang; Kaihao Zhang; Weili Guan; Yaowei Wang; Min Zhang
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=PTQ1.61%3A%20Push%20the%20Real%20Limit%20of%20Extremely%20Low-Bit%20Post-Training%20Quantization%20Methods%20for%20Large%20Language%20Models)（检索入口，非已核实原文链接）
- PDF：[undated-PTQ1-61.pdf](undated-PTQ1-61.pdf)（20 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-936"></a>

## NanoQuant

**NanoQuant: Efficient Sub-1-Bit Quantization of Large Language Models**

将权重量化建模为低秩二值分解，探索低于 1 bit 的表示。

- 作者：Hyochan Chong; Dongkyu Kim; Changdong Kim; Minseop Choi
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.06694)
- PDF：[2026-NanoQuant.pdf](2026-NanoQuant.pdf)（26 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-830"></a>

## SEMQ

**SEMQ: Efficient non-uniform quantization with sensitivity-based error minimization for large language models**

结合敏感度误差最小化和异常值分离设计非均匀量化。

- 作者：Dongmin Li; Xiurui Xie; Dongyang Zhang; Athanasios V. Vasilakos; Man-Fai Leung
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://linkinghub.elsevier.com/retrieve/pii/S0167739X25004145) · [作者代码（本地摘要提供）](https://github.com/ldm2060/semq)
- PDF：[2026-SEMQ.pdf](2026-SEMQ.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-863"></a>

## Logarithmic-Quantization

**A Deep Look into Logarithmic Quantization of Model Parameters in Neural Networks**

分析对数量化的适用分布及小型网络中的精度损失。

- 作者：Jingyong Cai; Masashi Takemoto; Hironori Nakajo
- 年份：2018；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3291280.3291800)
- PDF：[2018-Logarithmic-Quantization.pdf](2018-Logarithmic-Quantization.pdf)（9 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1030"></a>

## LogART

**LogART: Pushing the Limit of Efficient Logarithmic Post-Training Quantization**

在对数域学习舍入，并自适应选择量化基数。

- 作者：Jiawei Xu; Yi Zheng; Chenghe Sun; Taiyu Zhou; Zuqi Zhang; Jie Li; Lirong Zheng; Zhuo Zou
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=LogART%3A%20Pushing%20the%20Limit%20of%20Efficient%20Logarithmic%20Post-Training%20Quantization)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/logart-lab/logart)
- PDF：[2026-LogART.pdf](2026-LogART.pdf)（30 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-953"></a>

## BPDQ

**BPDQ: Bit-Plane Decomposition Quantization on a Variable Grid for Large Language Models**

用比特平面与系数构造可变网格，再进行二阶误差补偿。

- 作者：Junyu Chen; Jungang Li; Jing Xiong; Wenjie Wang; Qingyao Yang; He Xiao; Zhen Li; Taiqiang Wu; Mengzhao Chen; Zhen Peng; Chaofan Tao; Long Shi; Hongxia Yang; Ngai Wong
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.04163)
- PDF：[2026-BPDQ.pdf](2026-BPDQ.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1007"></a>

## BOF4

**Improving Block-Wise LLM Quantization by 4-bit Block-Wise Optimal Float (BOF4): Analysis and Variations**

分析块内归一化后的分布，设计 4-bit 最优浮点表示。

- 作者：Patrick Blumenberg; Thomas Graave; Tim Fingscheidt
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2505.06653)
- PDF：[2025-BOF4.pdf](2025-BOF4.pdf)（29 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-98"></a>

## WPQ

**WPQ: Product Quantization-Augmented Compression for Efficient Low-bit Representation in LLMs**

独立匿名稿：结合乘积量化、平滑与共享码本压缩 LLM。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=WPQ%3A%20Product%20Quantization-Augmented%20Compression%20for%20Efficient%20Low-bit%20Representation%20in%20LLMs)（检索入口，非已核实原文链接）
- PDF：[undated-WPQ.pdf](undated-WPQ.pdf)（10 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-99"></a>

## Trainable-Vector-Quantization

**Trainable Vector Quantization for Large Language Models**

独立匿名稿：用 STE 和隐变量让向量量化权重参与梯度优化。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Trainable%20Vector%20Quantization%20for%20Large%20Language%20Models)（检索入口，非已核实原文链接）
- PDF：[undated-Trainable-Vector-Quantization.pdf](undated-Trainable-Vector-Quantization.pdf)（12 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-100"></a>

## UniQuanF

**Unifying Uniform and Binary-coding Quantization for Accurate Compression of Large Language Models**

独立匿名稿：结合均匀量化的可优化性与二进制编码的表示能力。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Unifying%20Uniform%20and%20Binary-coding%20Quantization%20for%20Accurate%20Compression%20of%20Large%20Language%20Models)（检索入口，非已核实原文链接）
- PDF：[undated-UniQuanF.pdf](undated-UniQuanF.pdf)（19 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-193"></a>

## LCQ

**LCQ: Low-Rank Codebook based Quantization for Large Language Models**

独立匿名稿：使用低秩码本提升权重量化的表示能力。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=LCQ%3A%20Low-Rank%20Codebook%20based%20Quantization%20for%20Large%20Language%20Models)（检索入口，非已核实原文链接）
- PDF：[undated-LCQ.pdf](undated-LCQ.pdf)（11 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。
