# 权重 PTQ 与误差补偿

[返回总览](../README.md) · 17 份资料

以权重量化、二阶近似、重构目标和跨层误差控制为主；部分方法也支持激活量化。

主线：GPTQ → AWQ → SpQR/OWQ；进阶比较 GPTAQ、CBQ、BoA 与 Qronos 的误差目标。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| ⭐ [GPTQ](#p-33) | 2023 | 核心必读:利用近似二阶信息逐列量化,并补偿未量化权重。 |
| ⭐ [AWQ](#p-37) | 2023 | 核心必读:依据激活识别重要权重,用通道缩放改善权重量化。 |
| [OWQ](#p-237) | 2024 | 通过异常激活识别敏感权重,并用混合精度保护关键部分。 |
| [SpQR](#p-238) | 2023 | 将少量敏感权重单独存储,结合稀疏表示和低比特量化。 |
| [SEPTQ](#p-48) | 2025 | 先静态确定重要位置,再逐列量化与更新权重,简化 PTQ 流程。 |
| [GPTAQ](#p-60) | 2025 | 采用非对称校准,使量化层对齐原始全精度输出。 |
| [GuidedQuant](#p-51) | 2025 | 将最终任务损失的梯度信息引入量化目标。 |
| [CBQ](#p-66) | 2025 | 跨 Transformer 块重构,缓解低比特量化的误差累积。 |
| [FBQuant](#p-71) | 2025 | 借鉴负反馈机制,通过补偿分支改善权重量化重构。 |
| [Quantization-without-Tears](#p-52) | 未确认 | 用具有闭式解的轻量线性结构补偿量化信息损失。 |
| [Joint-Sparsification-Quantization](#p-58) | 未确认 | 研究剪枝与量化的联合设计及两者对异常值的不同需求。 |
| [D2Quant](#p-948) | 2026 | 结合下投影权重的双尺度量化和激活偏移校正。 |
| [SliderQuant](#p-1034) | 2026 | 根据层敏感度设计滑动窗口,改善跨层及层内量化。 |
| [Qronos](#p-1067) | 2026 | 同时处理权重、激活及前层误差,理解误差校正与扩散。 |
| [BoA](#p-1076) | 2025 | 考虑注意力模块中的层间依赖,构造 attention-aware Hessian。 |
| [TurboBoA](#p-1073) | 2026 | 改进 BoA 的联合通道量化和误差补偿,提高量化效率。 |
| [Compensation-Aware-Residual-Error](#p-1080) | 2026 | 重新定义补偿过程中的残差,使重构对齐原始全精度输出。 |

<a id="p-33"></a>

## GPTQ

**GPTQ: Accurate Post-Training Quantization for Generative Pre-trained Transformers**

核心必读：利用近似二阶信息逐列量化，并补偿未量化权重。

- 作者：Elias Frantar; Saleh Ashkboos; Torsten Hoefler; Dan Alistarh
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2210.17323) · [作者代码（本地摘要提供）](https://github.com/IST-DASLab/gptq)
- PDF：[2023-GPTQ.pdf](2023-GPTQ.pdf)（16 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-37"></a>

## AWQ

**AWQ: Activation-aware Weight Quantization for LLM Compression and Acceleration**

核心必读：依据激活识别重要权重，用通道缩放改善权重量化。

- 作者：Ji Lin; Jiaming Tang; Haotian Tang; Shang Yang; Xingyu Dang; Chuang Gan; Song Han
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2306.00978)
- PDF：[2023-AWQ.pdf](2023-AWQ.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-237"></a>

## OWQ

**OWQ: Outlier-Aware Weight Quantization for Efficient Fine-Tuning and Inference of Large Language Models**

通过异常激活识别敏感权重，并用混合精度保护关键部分。

- 作者：Changhun Lee; Jungyu Jin; Taesu Kim; Hyungjun Kim; Eunhyeok Park
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2306.02272)
- PDF：[2024-OWQ.pdf](2024-OWQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：本地 PDF 标题为 OWQ: Lessons learned from activation outliers for weight quantization in large language models，与题录标题存在版本差异。

<a id="p-238"></a>

## SpQR

**SpQR: A Sparse-Quantized Representation for Near-Lossless LLM Weight Compression**

将少量敏感权重单独存储，结合稀疏表示和低比特量化。

- 作者：Tim Dettmers; Ruslan Svirschevski; Vage Egiazarian; Denis Kuznedelev; Elias Frantar; Saleh Ashkboos; Alexander Borzunov; Torsten Hoefler; Dan Alistarh
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2306.03078)
- PDF：[2023-SpQR.pdf](2023-SpQR.pdf)（26 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-48"></a>

## SEPTQ

**SEPTQ: A Simple and Effective Post-Training Quantization Paradigm for Large Language Models**

先静态确定重要位置，再逐列量化与更新权重，简化 PTQ 流程。

- 作者：Han Liu; Haotian Gao; Xiaotong Zhang; Changya Li; Feng Zhang; Wei Wang; Fenglong Ma; Hong Yu
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3690624.3709287)
- PDF：[2025-SEPTQ.pdf](2025-SEPTQ.pdf)（12 页）
- 导读依据：本地 PDF 前两页。

<a id="p-60"></a>

## GPTAQ

**GPTAQ: Efficient Finetuning-Free Quantization for Asymmetric Calibration**

采用非对称校准，使量化层对齐原始全精度输出。

- 作者：Yuhang Li; Ruokai Yin; Donghyun Lee; Shiting Xiao; Priyadarshini Panda
- 年份：2025；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.mlr.press/v267/li25dn.html)
- PDF：[2025-GPTAQ.pdf](2025-GPTAQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-51"></a>

## GuidedQuant

**GuidedQuant: Large Language Model Quantization via Exploiting End Loss Guidance**

将最终任务损失的梯度信息引入量化目标。

- 作者：Jinuk Kim; Marwa El Halabi; Wonpyo Park; Clemens JS Schaefer; Deokjae Lee; Yeonhong Park; Jae W. Lee; Hyun Oh Song
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2505.07004)
- PDF：[2025-GuidedQuant.pdf](2025-GuidedQuant.pdf)（27 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-66"></a>

## CBQ

**CBQ: Cross-Block Quantization for Large Language Models**

跨 Transformer 块重构，缓解低比特量化的误差累积。

- 作者：Xin Ding; Xiaoyu Liu; Zhijun Tu; Yun Zhang; Wei Li; Jie Hu; Hanting Chen; Yehui Tang; Zhiwei Xiong; Baoqun Yin; Yunhe Wang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2312.07950)
- PDF：[2025-CBQ.pdf](2025-CBQ.pdf)（20 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-71"></a>

## FBQuant

**FBQuant: FeedBack Quantization for Large Language Models**

借鉴负反馈机制，通过补偿分支改善权重量化重构。

- 作者：Yijiang Liu; Hengyu Fang; Liulu He; Rongyu Zhang; Yichuan Bai; Yuan Du; Li Du
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2501.16385)
- PDF：[2025-FBQuant.pdf](2025-FBQuant.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-52"></a>

## Quantization-without-Tears

**Quantization without Tears**

用具有闭式解的轻量线性结构补偿量化信息损失。

- 作者：Minghao Fu; Hao Yu; Jie Shao; Junjie Zhou; Ke Zhu; Jianxin Wu
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Quantization%20without%20Tears)（检索入口，非已核实原文链接）
- PDF：[undated-Quantization-without-Tears.pdf](undated-Quantization-without-Tears.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-58"></a>

## Joint-Sparsification-Quantization

**Compressing Large Language Models by Joint Sparsification and Quantization**

研究剪枝与量化的联合设计及两者对异常值的不同需求。

- 作者：Jinyang Guo; Jianyu Wu; Zining Wang; Jiaheng Liu; Ge Yang; Yifu Ding; Ruihao Gong; Haotong Qin; Xianglong Liu
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Compressing%20Large%20Language%20Models%20by%20Joint%20Sparsification%20and%20Quantization)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/uanu2002/JSQ)
- PDF：[undated-Joint-Sparsification-Quantization.pdf](undated-Joint-Sparsification-Quantization.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-948"></a>

## D2Quant

**D2Quant: Accurate Low-bit Post-Training Weight Quantization for LLMs**

结合下投影权重的双尺度量化和激活偏移校正。

- 作者：Xianglong Yan; ChengZhu Bao; Zhiteng Li; Tianao Zhang; Shaoqiu Zhang; Ruobing Xie; Samm Sun; Yulun Zhang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.02546)
- PDF：[2026-D2Quant.pdf](2026-D2Quant.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1034"></a>

## SliderQuant

**SliderQuant: Accurate Post-Training Quantization for LLMs**

根据层敏感度设计滑动窗口，改善跨层及层内量化。

- 作者：Shigeng Wang; Chao Li; Yangyuxuan Kang; Jiawei Fan; Zhonghong Ou; Anbang Yao
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=SliderQuant%3A%20Accurate%20Post-Training%20Quantization%20for%20LLMs)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/deep-optimization/SliderQuant)
- PDF：[2026-SliderQuant.pdf](2026-SliderQuant.pdf)（30 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1067"></a>

## Qronos

**Qronos: Correcting the Past by Shaping the Future... in Post-Training Quantization**

同时处理权重、激活及前层误差，理解误差校正与扩散。

- 作者：Shihao Zhang; Haoyu Zhang; Ian Colbert; Rayan Saab
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2505.11695)
- PDF：[2026-Qronos.pdf](2026-Qronos.pdf)（24 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1076"></a>

## BoA

**BoA: Attention-aware Post-training Quantization without Backpropagation**

考虑注意力模块中的层间依赖，构造 attention-aware Hessian。

- 作者：Junhan Kim; Ho-young Kim; Eulrang Cho; Chungman Lee; Joonyoung Kim; Yongkweon Jeon
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2406.13474)
- PDF：[2025-BoA.pdf](2025-BoA.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1073"></a>

## TurboBoA

**TurboBoA: Faster and Exact Attention-aware Quantization without Backpropagation**

改进 BoA 的联合通道量化和误差补偿，提高量化效率。

- 作者：Junhan Kim; Yeo Jeong Park; Seungwoo Son; Chungman Lee; Ho-young Kim; Joonyoung Kim; Yongkweon Jeon
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.04929) · [作者代码（本地摘要提供）](https://github.com/SamsungLabs/TurboBoA)
- PDF：[2026-TurboBoA.pdf](2026-TurboBoA.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1080"></a>

## Compensation-Aware-Residual-Error

**Rethinking Residual Errors in Compensation-Based LLM Quantization**

重新定义补偿过程中的残差，使重构对齐原始全精度输出。

- 作者：Shuaiting Li; Juncan Deng; Kedong Xu; Rongtao Deng; Hong Gu; Minghan Jiang; Haibin Shen; Kejie Huang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Rethinking%20Residual%20Errors%20in%20Compensation-Based%20LLM%20Quantization)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/list0830/ResComp)
- PDF：[2026-Compensation-Aware-Residual-Error.pdf](2026-Compensation-Aware-Residual-Error.pdf)（18 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
