# QAT、低比特训练与适配

[返回总览](../README.md) · 20 份资料

包含量化感知训练、蒸馏、低秩补偿、低精度微调，以及量化友好的预训练。

主线：LLM-QAT → BitDistiller；训练架构分支读 BitNet → BitNet b1.58；适配分支读 QA-LoRA → RILQ。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| ⭐ [LLM-QAT](#p-201) | 2023 | 核心必读:用模型生成数据进行量化感知训练与蒸馏。 |
| ⭐ [BitNet](#p-198) | 2023 | 从训练阶段设计二值权重 Transformer,关注训练与部署的区别。 |
| ⭐ [BitNet-b1-58](#p-203) | 2024 | 通过三值权重训练探索 1.58-bit LLM,与训练后量化对照阅读。 |
| [BitDistiller](#p-143) | 2024 | 结合量化感知训练和自蒸馏恢复低于 4-bit 的模型能力。 |
| [OneBit](#p-209) | 2024 | 使用一位权重表示、初始化和 QAT 探索极低比特 LLM。 |
| [QA-LoRA](#p-784) | 2024 | 联合量化与低秩适配,并关注适配器合并后的量化表示。 |
| [RILQ](#p-44) | 未确认 | 用跨层协同的 LoRA 误差补偿改善 2-bit 模型。 |
| [ZeroQuant-V2](#p-138) | 2023 | 系统分析 PTQ 敏感度,并引入低秩误差补偿。 |
| [Quantized-Side-Tuning](#p-178) | 2024 | 通过量化与旁路调优降低权重、优化器及激活的训练内存。 |
| [Soft-Prompt-Recovery](#p-212) | 未确认 | 用软提示恢复压缩模型能力,比较量化与剪枝后的迁移效果。 |
| [R2-Loss](#p-213) | 未确认 | 在训练中约束权重范围,为后续量化构造更友好的分布。 |
| [N2UQ](#p-190) | 2022 | 通过广义 STE 连接非均匀表示能力与均匀量化部署。 |
| [PARQ](#p-104) | 未确认 | 用分段仿射正则化研究 QAT,并解释 STE 的联系。 |
| [Tequila](#p-797) | 2025 | 围绕三值训练中的优化陷阱改进低比特学习。 |
| [Low-Precision-Finetuning-Outliers](#p-991) | 2024 | 研究低精度微调时异常激活的整数表示与算子实现。 |
| [QeRL](#p-962) | 2025 | 结合低精度量化与参数高效适配,研究强化学习训练效率。 |
| [Bell-Box-Quantization](#p-1004) | 2026 | 将信息表示与计算域映射结合,改善量化感知预训练。 |
| [DB-LLM](#p-199) | 未确认 | 独立匿名稿:结合双二值表示与偏差感知蒸馏。 |
| [DeltaDQ](#p-215) | 未确认 | 独立匿名稿:对微调产生的增量权重联合稀疏化与量化。 |
| [Bit-by-Bit](#p-989) | 未确认 | 独立匿名稿:逐步降低训练精度,并结合异常通道拆分。 |

<a id="p-201"></a>

## LLM-QAT

**LLM-QAT: Data-Free Quantization Aware Training for Large Language Models**

核心必读：用模型生成数据进行量化感知训练与蒸馏。

- 作者：Zechun Liu; Barlas Oguz; Changsheng Zhao; Ernie Chang; Pierre Stock; Yashar Mehdad; Yangyang Shi; Raghuraman Krishnamoorthi; Vikas Chandra
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2305.17888)
- PDF：[2023-LLM-QAT.pdf](2023-LLM-QAT.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-198"></a>

## BitNet

**BitNet: Scaling 1-bit Transformers for Large Language Models**

从训练阶段设计二值权重 Transformer，关注训练与部署的区别。

- 作者：Hongyu Wang; Shuming Ma; Li Dong; Shaohan Huang; Huaijie Wang; Lingxiao Ma; Fan Yang; Ruiping Wang; Yi Wu; Furu Wei
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2310.11453)
- PDF：[2023-BitNet.pdf](2023-BitNet.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-203"></a>

## BitNet-b1-58

**The Era of 1-bit LLMs: All Large Language Models are in 1.58 Bits**

通过三值权重训练探索 1.58-bit LLM，与训练后量化对照阅读。

- 作者：Shuming Ma; Hongyu Wang; Lingxiao Ma; Lei Wang; Wenhui Wang; Shaohan Huang; Li Dong; Ruiping Wang; Jilong Xue; Furu Wei
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.17764)
- PDF：[2024-BitNet-b1-58.pdf](2024-BitNet-b1-58.pdf)（8 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-143"></a>

## BitDistiller

**BitDistiller: Unleashing the Potential of Sub-4-Bit LLMs via Self-Distillation**

结合量化感知训练和自蒸馏恢复低于 4-bit 的模型能力。

- 作者：Dayou Du; Yijia Zhang; Shijie Cao; Jiaqi Guo; Ting Cao; Xiaowen Chu; Ningyi Xu
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.10631)
- PDF：[2024-BitDistiller.pdf](2024-BitDistiller.pdf)（14 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-209"></a>

## OneBit

**OneBit: Towards Extremely Low-bit Large Language Models**

使用一位权重表示、初始化和 QAT 探索极低比特 LLM。

- 作者：Yuzhuang Xu; Xu Han; Zonghan Yang; Shuo Wang; Qingfu Zhu; Zhiyuan Liu; Weidong Liu; Wanxiang Che
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.11295)
- PDF：[2024-OneBit.pdf](2024-OneBit.pdf)（15 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-784"></a>

## QA-LoRA

**QA-LoRA: Quantization-Aware Low-Rank Adaptation of Large Language Models**

联合量化与低秩适配，并关注适配器合并后的量化表示。

- 作者：Yuhui Xu; Lingxi Xie; Xiaotao Gu; Xin Chen; Heng Chang
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2309.14717) · [作者代码（本地摘要提供）](https://github.com/yuhuixu1993/qa-lora)
- PDF：[2024-QA-LoRA.pdf](2024-QA-LoRA.pdf)（18 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-44"></a>

## RILQ

**RILQ: Rank-Insensitive LoRA-Based Quantization Error Compensation for Boosting 2-Bit Large Language Model Accuracy**

用跨层协同的 LoRA 误差补偿改善 2-bit 模型。

- 作者：Geonho Lee; Janghwan Lee; Sukjin Hong; Minsoo Kim; Euijai Ahn; Du-Seong Chang; Jungwook Choi
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=RILQ%3A%20Rank-Insensitive%20LoRA-Based%20Quantization%20Error%20Compensation%20for%20Boosting%202-Bit%20Large%20Language%20Model%20Accuracy)（检索入口，非已核实原文链接）
- PDF：[undated-RILQ.pdf](undated-RILQ.pdf)（10 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-138"></a>

## ZeroQuant-V2

**ZeroQuant-V2: Exploring Post-training Quantization in LLMs from Comprehensive Study to Low Rank Compensation**

系统分析 PTQ 敏感度，并引入低秩误差补偿。

- 作者：Zhewei Yao; Xiaoxia Wu; Cheng Li; Stephen Youn; Yuxiong He
- 年份：2023；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2303.08302)
- PDF：[2023-ZeroQuant-V2.pdf](2023-ZeroQuant-V2.pdf)（24 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-178"></a>

## Quantized-Side-Tuning

**Quantized Side Tuning: Fast and Memory-Efficient Tuning of Quantized Large Language Models**

通过量化与旁路调优降低权重、优化器及激活的训练内存。

- 作者：Zhengxin Zhang; Dan Zhao; Xupeng Miao; Gabriele Oliaro; Qing Li; Yong Jiang; Zhihao Jia
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2401.07159)
- PDF：[2024-Quantized-Side-Tuning.pdf](2024-Quantized-Side-Tuning.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-212"></a>

## Soft-Prompt-Recovery

**Soft Prompt Recovers Compressed LLMs, Transferably**

用软提示恢复压缩模型能力，比较量化与剪枝后的迁移效果。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Soft%20Prompt%20Recovers%20Compressed%20LLMs%2C%20Transferably)（检索入口，非已核实原文链接）
- PDF：[undated-Soft-Prompt-Recovery.pdf](undated-Soft-Prompt-Recovery.pdf)（18 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-213"></a>

## R2-Loss

**R2 Loss: Range Restriction Loss for Model Compression and Quantization**

在训练中约束权重范围，为后续量化构造更友好的分布。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=R2%20Loss%3A%20Range%20Restriction%20Loss%20for%20Model%20Compression%20and%20Quantization)（检索入口，非已核实原文链接）
- PDF：[undated-R2-Loss.pdf](undated-R2-Loss.pdf)（10 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-190"></a>

## N2UQ

**Nonuniform-to-Uniform Quantization: Towards Accurate Quantization via Generalized Straight-Through Estimation**

通过广义 STE 连接非均匀表示能力与均匀量化部署。

- 作者：Zechun Liu; Kwang-Ting Cheng; Dong Huang; Eric Xing; Zhiqiang Shen
- 年份：2022；依据：Zotero 日期字段
- 原文入口：[论文](https://ieeexplore.ieee.org/document/9879262/)
- PDF：[2022-N2UQ.pdf](2022-N2UQ.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-104"></a>

## PARQ

**PARQ: Piecewise-Affine Regularized Quantization**

用分段仿射正则化研究 QAT，并解释 STE 的联系。

- 作者：Anonymous Authors
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=PARQ%3A%20Piecewise-Affine%20Regularized%20Quantization)（检索入口，非已核实原文链接）
- PDF：[undated-PARQ.pdf](undated-PARQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-797"></a>

## Tequila

**Tequila: Trapping-free Ternary Quantization for Large Language Models**

围绕三值训练中的优化陷阱改进低比特学习。

- 作者：Hong Huang; Decheng Wu; Rui Cen; Guanghua Yu; Zonghang Li; Kai Liu; Jianchen Zhu; Peng Chen; Xue Liu; Dapeng Wu
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2509.23809) · [作者代码（本地摘要提供）](https://github.com/Tencent/AngelSlim)
- PDF：[2025-Tequila.pdf](2025-Tequila.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-991"></a>

## Low-Precision-Finetuning-Outliers

**Mitigating Outlier Activations in Low-Precision Fine-Tuning of Language Models**

研究低精度微调时异常激活的整数表示与算子实现。

- 作者：Alireza Ghaffari; Justin Yu; Mahsa Ghazvini Nejad; Masoud Asgharian; Boxing Chen; Vahid Partovi Nia
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2312.09211)
- PDF：[2024-Low-Precision-Finetuning-Outliers.pdf](2024-Low-Precision-Finetuning-Outliers.pdf)（7 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-962"></a>

## QeRL

**QeRL: Beyond Efficiency -- Quantization-enhanced Reinforcement Learning for LLMs**

结合低精度量化与参数高效适配，研究强化学习训练效率。

- 作者：Wei Huang; Yi Ge; Shuai Yang; Yicheng Xiao; Huizi Mao; Yujun Lin; Hanrong Ye; Sifei Liu; Ka Chun Cheung; Hongxu Yin; Yao Lu; Xiaojuan Qi; Song Han; Yukang Chen
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2510.11696)
- PDF：[2025-QeRL.pdf](2025-QeRL.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-1004"></a>

## Bell-Box-Quantization

**Boosting Entropy with Bell Box Quantization**

将信息表示与计算域映射结合，改善量化感知预训练。

- 作者：Ningfeng Yang; Tor M Aamodt
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Boosting%20Entropy%20with%20Bell%20Box%20Quantization)（检索入口，非已核实原文链接） · [作者代码（本地摘要提供）](https://github.com/1733116199/bbq)
- PDF：[2026-Bell-Box-Quantization.pdf](2026-Bell-Box-Quantization.pdf)（30 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-199"></a>

## DB-LLM

**DB-LLM: Accurate Dual-Binarization for Efficient LLMs**

独立匿名稿：结合双二值表示与偏差感知蒸馏。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=DB-LLM%3A%20Accurate%20Dual-Binarization%20for%20Efficient%20LLMs)（检索入口，非已核实原文链接）
- PDF：[undated-DB-LLM.pdf](undated-DB-LLM.pdf)（11 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-215"></a>

## DeltaDQ

**DeltaDQ: Distribution-Driven Delta Compression for Fine-tuned LLMs**

独立匿名稿：对微调产生的增量权重联合稀疏化与量化。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=DeltaDQ%3A%20Distribution-Driven%20Delta%20Compression%20for%20Fine-tuned%20LLMs)（检索入口，非已核实原文链接）
- PDF：[undated-DeltaDQ.pdf](undated-DeltaDQ.pdf)（10 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。

<a id="p-989"></a>

## Bit-by-Bit

**Bit-by-Bit: Progressive QAT with Outlier Channel Splitting for Stable Low-Bit LLMs**

独立匿名稿：逐步降低训练精度，并结合异常通道拆分。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Bit-by-Bit%3A%20Progressive%20QAT%20with%20Outlier%20Channel%20Splitting%20for%20Stable%20Low-Bit%20LLMs)（检索入口，非已核实原文链接）
- PDF：[undated-Bit-by-Bit.pdf](undated-Bit-by-Bit.pdf)（17 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份。
