# 量化基础与经典理论

[返回总览](../README.md) · 18 份资料

包含经典量化、PTQ 重构基础，以及信号处理和分布量化的选读资料。

主线：Lloyd-Max 讲义 → AdaRound → BRECQ → Optimal Brain Compression。经典信号处理与分布量化可作为数学拓展。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| [Max-Minimum-Distortion](#p-93) | 1960 | 经典标量量化:理解最小失真目标与最优量化区间。 |
| [Lloyd-Least-Squares-Quantization](#p-94) | 1982 | 经典最小二乘量化:理解决策边界与重构值的交替优化。 |
| [Lloyd-Max-Tutorial](#p-92) | 2006 | 课程讲义:用简明步骤学习 Lloyd-Max 算法;非研究论文。 |
| [Lloyd-Max-Complexity](#p-97) | 1982 | 理论拓展:广义 Lloyd-Max 问题的计算复杂性。 |
| [Grayscale-Requantization](#p-79) | 2006 | 信号处理拓展:数字图像再量化与连续信号量化的区别。 |
| [Lloyd-Max-Dither](#p-80) | 2023 | 信号处理拓展:通过抖动改善量化误差的统计性质。 |
| [Lloyd-Max-Video-Coding](#p-81) | 2007 | 信号处理拓展:将非均匀量化用于分布式视频编码。 |
| [Lloyd-Max-Subband-Coders](#p-95) | 1998 | 信号处理拓展:量化器与子带编码器的联合设计。 |
| [Crawford-Sobel-Lloyd-Max](#p-96) | 2014 | 理论拓展:智能电网信号传递与量化问题的联系。 |
| [Conditional-Distribution-Quantization](#p-103) | 未确认 | 分布量化拓展:用有限代表点近似多模态条件分布。 |
| [MMD-Weighted-Quantization](#p-105) | 未确认 | 分布量化拓展:用 MMD 和梯度流优化带权离散近似。 |
| [Learning-under-Quantization](#p-1009) | 2026 | 理论拓展:量化如何影响高维线性回归的学习动力学。 |
| [GPTQ-Lattice-Geometry](#p-1063) | 2026 | 进阶推导:把 GPTQ 与格上的 Babai 最近平面算法联系起来。 |
| ⭐ [AdaRound](#p-39) | 2020 | 基础必读:舍入到最近值未必最优,用局部重构学习舍入方向。 |
| ⭐ [BRECQ](#p-812) | 2021 | 基础必读:理解块重构如何平衡跨层依赖和泛化。 |
| ⭐ [Optimal-Brain-Compression](#p-30) | 2022 | 基础必读:用二阶信息统一理解训练后量化与剪枝。 |
| [Outlier-Channel-Splitting](#p-34) | 2019 | 理解异常值问题的早期思路:拆分通道并缩小数值范围。 |
| [ACIQ-Post-Training-4bit](#p-235) | 2019 | 基础阅读:CNN 的低比特 PTQ,关注裁剪和误差补偿。 |

<a id="p-93"></a>

## Max-Minimum-Distortion

**Quantizing for minimum distortion**

经典标量量化：理解最小失真目标与最优量化区间。

- 作者：J. Max
- 年份：1960；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/1057548/?arnumber=1057548)
- PDF：[1960-Max-Minimum-Distortion.pdf](1960-Max-Minimum-Distortion.pdf)（6 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-94"></a>

## Lloyd-Least-Squares-Quantization

**Least squares quantization in PCM**

经典最小二乘量化：理解决策边界与重构值的交替优化。

- 作者：Stuart Lloyd
- 年份：1982；依据：Zotero 日期字段
- 原文入口：[论文](https://hal.science/hal-04614938)
- PDF：[1982-Lloyd-Least-Squares-Quantization.pdf](1982-Lloyd-Least-Squares-Quantization.pdf)（10 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-92"></a>

## Lloyd-Max-Tutorial

**Lloyd-Max Quantization (CSG142 Digital Image Processing course notes)**

课程讲义：用简明步骤学习 Lloyd-Max 算法；非研究论文。

- 作者：未整理(见 PDF 首页)
- 年份：2006；依据：本地 PDF 首页
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Lloyd-Max%20Quantization%20%28CSG142%20Digital%20Image%20Processing%20course%20notes%29)（检索入口，非已核实原文链接）
- PDF：[2006-Lloyd-Max-Tutorial.pdf](2006-Lloyd-Max-Tutorial.pdf)（2 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：课程讲义，非研究论文。

<a id="p-97"></a>

## Lloyd-Max-Complexity

**The complexity of the generalized Lloyd - Max problem (Corresp.)**

理论拓展：广义 Lloyd-Max 问题的计算复杂性。

- 作者：M. Garey; D. Johnson; H. Witsenhausen
- 年份：1982；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/1056488/?arnumber=1056488)
- PDF：[1982-Lloyd-Max-Complexity.pdf](1982-Lloyd-Max-Complexity.pdf)（2 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-79"></a>

## Grayscale-Requantization

**Optimal requantization of deep grayscale images and Lloyd-Max quantization**

信号处理拓展：数字图像再量化与连续信号量化的区别。

- 作者：S.M. Borodkin; A.M. Borodkin; I.B. Muchnik
- 年份：2006；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/1576817)
- PDF：[2006-Grayscale-Requantization.pdf](2006-Grayscale-Requantization.pdf)（4 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-80"></a>

## Lloyd-Max-Dither

**Non-Subtractive Dither for Squared Error Linearization of Lloyd-Max Quantizers**

信号处理拓展：通过抖动改善量化误差的统计性质。

- 作者：Morriel Kasher; Michael Tinston; Predrag Spasojevic
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/10476841/)
- 本地 PDF：无附件；请使用上方公开论文入口。
- 导读依据：Zotero 题录与摘要。
- 版本说明：本地 Zotero 只有题录与摘要，无 PDF 附件；保留公开论文入口。

<a id="p-81"></a>

## Lloyd-Max-Video-Coding

**A Lloyd-Max-based Non-Uniform Quantization Scheme for Distributed Video Coding**

信号处理拓展：将非均匀量化用于分布式视频编码。

- 作者：Fang Sheng; Li Xu-Jian; Zhang Li-Wei
- 年份：2007；依据：Zotero 日期字段
- 原文入口：[论文](http://ieeexplore.ieee.org/document/4287621/)
- PDF：[2007-Lloyd-Max-Video-Coding.pdf](2007-Lloyd-Max-Video-Coding.pdf)（6 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-95"></a>

## Lloyd-Max-Subband-Coders

**Optimal construction of subband coders using Lloyd-Max quantizers**

信号处理拓展：量化器与子带编码器的联合设计。

- 作者：M.G. Strintzis; D. Tzovaras
- 年份：1998；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/668023/?arnumber=668023)
- PDF：[1998-Lloyd-Max-Subband-Coders.pdf](1998-Lloyd-Max-Subband-Coders.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-96"></a>

## Crawford-Sobel-Lloyd-Max

**Crawford-sobel meet Lloyd-Max on the grid**

理论拓展：智能电网信号传递与量化问题的联系。

- 作者：B. Larrousse; O. Beaude; S. Lasaulce
- 年份：2014；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/6854781/?arnumber=6854781)
- PDF：[2014-Crawford-Sobel-Lloyd-Max.pdf](2014-Crawford-Sobel-Lloyd-Max.pdf)（5 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-103"></a>

## Conditional-Distribution-Quantization

**Conditional Distribution Quantization in Machine Learning**

分布量化拓展：用有限代表点近似多模态条件分布。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Conditional%20Distribution%20Quantization%20in%20Machine%20Learning)（检索入口，非已核实原文链接）
- PDF：[undated-Conditional-Distribution-Quantization.pdf](undated-Conditional-Distribution-Quantization.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-105"></a>

## MMD-Weighted-Quantization

**Weighted Quantization Using MMD: From Mean Field to Mean Shift via Gradient Flows**

分布量化拓展：用 MMD 和梯度流优化带权离散近似。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Weighted%20Quantization%20Using%20MMD%3A%20From%20Mean%20Field%20to%20Mean%20Shift%20via%20Gradient%20Flows)（检索入口，非已核实原文链接）
- PDF：[undated-MMD-Weighted-Quantization.pdf](undated-MMD-Weighted-Quantization.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-1009"></a>

## Learning-under-Quantization

**Learning under Quantization for High-Dimensional Linear Regression**

理论拓展：量化如何影响高维线性回归的学习动力学。

- 作者：Dechen Zhang; Junwei Su; Difan Zou
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2510.18259)
- PDF：[2026-Learning-under-Quantization.pdf](2026-Learning-under-Quantization.pdf)（75 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1063"></a>

## GPTQ-Lattice-Geometry

**The Lattice Geometry of Neural Network Quantization -- A Short Equivalence Proof of GPTQ and Babai's Algorithm**

进阶推导：把 GPTQ 与格上的 Babai 最近平面算法联系起来。

- 作者：Johann Birnick
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2508.01077)
- PDF：[2026-GPTQ-Lattice-Geometry.pdf](2026-GPTQ-Lattice-Geometry.pdf)（9 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-39"></a>

## AdaRound

**Up or Down? Adaptive Rounding for Post-Training Quantization**

基础必读：舍入到最近值未必最优，用局部重构学习舍入方向。

- 作者：Markus Nagel; Rana Ali Amjad
- 年份：2020；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.mlr.press/v119/nagel20a/nagel20a.pdf)
- PDF：[2020-AdaRound.pdf](2020-AdaRound.pdf)（10 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-812"></a>

## BRECQ

**BRECQ: Pushing the Limit of Post-Training Quantization by Block Reconstruction**

基础必读：理解块重构如何平衡跨层依赖和泛化。

- 作者：Yuhang Li; Ruihao Gong; Xu Tan; Yang Yang; Peng Hu; Qi Zhang; Fengwei Yu; Wei Wang; Shi Gu
- 年份：2021；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2102.05426) · [作者代码（本地摘要提供）](https://github.com/yhhhli/BRECQ)
- PDF：[2021-BRECQ.pdf](2021-BRECQ.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-30"></a>

## Optimal-Brain-Compression

**Optimal Brain Compression: A Framework for Accurate Post-Training Quantization and Pruning**

基础必读：用二阶信息统一理解训练后量化与剪枝。

- 作者：Elias Frantar; Sidak Pal Singh; Dan Alistarh
- 年份：2022；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://arxiv.org/abs/2208.11580)
- PDF：[2022-Optimal-Brain-Compression.pdf](2022-Optimal-Brain-Compression.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-34"></a>

## Outlier-Channel-Splitting

**Improving Neural Network Quantization without Retraining using Outlier Channel Splitting**

理解异常值问题的早期思路：拆分通道并缩小数值范围。

- 作者：Ritchie Zhao; Yuwei Hu; Jordan Dotzel; Christopher De Sa; Zhiru Zhang
- 年份：2019；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.mlr.press/v97/zhao19c.html)
- PDF：[2019-Outlier-Channel-Splitting.pdf](2019-Outlier-Channel-Splitting.pdf)（10 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-235"></a>

## ACIQ-Post-Training-4bit

**Post training 4-bit quantization of convolutional networks for rapid-deployment**

基础阅读：CNN 的低比特 PTQ，关注裁剪和误差补偿。

- 作者：Ron Banner; Yury Nahshan; Daniel Soudry
- 年份：2019；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.neurips.cc/paper_files/paper/2019/hash/c0a62e133894cdce435bcb4a5df1db2d-Abstract.html) · [作者代码（本地摘要提供）](https://github.com/submission2019/cnn-quantization)
- PDF：[2019-ACIQ-Post-Training-4bit.pdf](2019-ACIQ-Post-Training-4bit.pdf)（9 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。
