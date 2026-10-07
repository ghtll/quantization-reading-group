# 视觉与多模态量化

[返回总览](../README.md) · 19 份资料

涵盖 ViT、VLM、扩散 Transformer、视觉自回归与视觉语言动作模型。

ViT 分支：PTQ4ViT → RepQ-ViT → FIMA-Q。VLM 分支：MBQ → MQuant → Q-VLM；KV 分支补读 AKVQ-VL。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| [FIMA-Q](#p-43) | 2025 | 用 Fisher 信息矩阵近似指导 ViT 的量化重构。 |
| [ERQ](#p-47) | 未确认 | 分步处理激活与权重量化误差,并用回归更新进行修正。 |
| ⭐ [PTQ4ViT](#p-871) | 2024 | ViT 入门:针对 Softmax/GELU 分布设计双均匀量化和 Hessian 指标。 |
| [I-and-S-ViT](#p-850) | 2026 | 针对 ViT 的 Softmax 与 LayerNorm 激活设计量化器和稳定优化。 |
| [RepQ-ViT](#p-866) | 2023 | 通过尺度重参数化连接精细校准与硬件友好的推理量化。 |
| [MQuant](#p-87) | 2025 | 多模态静态量化,重点关注模态差异与推理效率。 |
| ⭐ [MBQ](#p-911) | 2025 | 多模态入门:在校准中平衡文本与视觉的量化敏感度。 |
| [Q-VLM](#p-913) | 2024 | 根据跨层依赖与激活熵划分重构块,降低多模态量化误差。 |
| [Bi-VLM](#p-915) | 2025 | 研究视觉语言模型的极低精度权重表示及视觉 token 冗余。 |
| [LUQ](#p-919) | 2025 | 面向多模态模型的逐层超低比特量化。 |
| [VLMQ-Hessian-Augmentation](#p-921) | 2025 | 通过 Hessian 增强改善视觉语言模型的 PTQ。 |
| [VLMQ-Token-Redundancy](#p-923) | 未确认 | 独立匿名稿:抑制冗余视觉 token,并用重要性感知目标指导量化。 |
| [QSLAW](#p-925) | 2024 | 通过量化感知尺度学习和多模态预热改善视觉语言适配。 |
| [SPEED-Q](#p-890) | 2025 | 分阶段处理与增强蒸馏,面向端侧 VLM 的低比特量化。 |
| [AKVQ-VL](#p-885) | 2025 | 多模态 KV 分支:依据文本和关键 token 的注意力分配比特。 |
| [CASP](#p-886) | 2025 | 结合注意力稀疏性、低秩分解和最优比特分配压缩多模态模型。 |
| [VQ4DiT](#p-74) | 未确认 | 将向量量化用于扩散 Transformer,联合考虑码本与分配。 |
| [Shift-and-Sum](#p-982) | 2026 | 视觉自回归模型:用平移求和量化与校准重采样降低误差。 |
| [QVLA](#p-977) | 2026 | 视觉语言动作模型:基于通道重要性统一量化与剪枝。 |

<a id="p-43"></a>

## FIMA-Q

**FIMA-Q: Post-Training Quantization for Vision Transformers by Fisher Information Matrix Approximation**

用 Fisher 信息矩阵近似指导 ViT 的量化重构。

- 作者：Zhuguanyu Wu; Shihe Wang; Jiayi Zhang; Jiaxin Chen; Yunhong Wang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2506.11543) · [作者代码（本地摘要提供）](https://github.com/ShiheWang/FIMA-Q)
- PDF：[2025-FIMA-Q.pdf](2025-FIMA-Q.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-47"></a>

## ERQ

**ERQ: Error Reduction for Post-Training Quantization of Vision Transformers**

分步处理激活与权重量化误差，并用回归更新进行修正。

- 作者：Yunshan Zhong; Jiawei Hu; You Huang; Yuxin Zhang; Rongrong Ji
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=ERQ%3A%20Error%20Reduction%20for%20Post-Training%20Quantization%20of%20Vision%20Transformers)（检索入口，非已核实原文链接）
- PDF：[undated-ERQ.pdf](undated-ERQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-871"></a>

## PTQ4ViT

**PTQ4ViT: Post-training quantization for vision transformers with twin uniform quantization**

ViT 入门：针对 Softmax/GELU 分布设计双均匀量化和 Hessian 指标。

- 作者：Zhihang Yuan; Chenhao Xue; Yiqi Chen; Qiang Wu; Guangyu Sun
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2111.12293)
- PDF：[2024-PTQ4ViT.pdf](2024-PTQ4ViT.pdf)（20 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-850"></a>

## I-and-S-ViT

**I&S-ViT: An Inclusive & Stable Method for Post-Training ViTs Quantization**

针对 ViT 的 Softmax 与 LayerNorm 激活设计量化器和稳定优化。

- 作者：未整理(见 PDF 首页)
- 年份：2026；依据：本地 PDF 首页
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=I%26S-ViT%3A%20An%20Inclusive%20%26%20Stable%20Method%20for%20Post-Training%20ViTs%20Quantization)（检索入口，非已核实原文链接）
- PDF：[2026-I-and-S-ViT.pdf](2026-I-and-S-ViT.pdf)（18 页）
- 导读依据：本地 PDF 前两页。

<a id="p-866"></a>

## RepQ-ViT

**RepQ-ViT: Scale Reparameterization for Post-Training Quantization of Vision Transformers**

通过尺度重参数化连接精细校准与硬件友好的推理量化。

- 作者：未整理(见 PDF 首页)
- 年份：2023；依据：本地 PDF 首页
- 原文入口：[论文](https://openaccess.thecvf.com/content/ICCV2023/html/Li_RepQ-ViT_Scale_Reparameterization_for_Post-Training_Quantization_of_Vision_Transformers_ICCV_2023_paper.html)
- PDF：[2023-RepQ-ViT.pdf](2023-RepQ-ViT.pdf)（10 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本；已从其他题录下识别并归回匹配的 PDF 附件；未修改 Zotero。

<a id="p-87"></a>

## MQuant

**MQuant: Unleashing the Inference Potential of Multimodal Large Language Models via Static Quantization**

多模态静态量化，重点关注模态差异与推理效率。

- 作者：Jiangyong Yu; Sifan Zhou; Dawei Yang; Shuoyu Li; Shuo Wang; Xing Hu; Chen Xu; Zukang Xu; Changyong Shu; Zhihang Yuan
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3746027.3755433)
- PDF：[2025-MQuant.pdf](2025-MQuant.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-911"></a>

## MBQ

**MBQ: Modality-Balanced Quantization for Large Vision-Language Models**

多模态入门：在校准中平衡文本与视觉的量化敏感度。

- 作者：Shiyao Li; Yingchun Hu; Xuefei Ning; Xihui Liu; Ke Hong; Xiaotao Jia; Xiuhong Li; Yaqi Yan; Pei Ran; Guohao Dai; Shengen Yan; Huazhong Yang; Yu Wang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2412.19509) · [作者代码（本地摘要提供）](https://github.com/thu-nics/MBQ)
- PDF：[2025-MBQ.pdf](2025-MBQ.pdf)（21 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-913"></a>

## Q-VLM

**Q-VLM: Post-training Quantization for Large Vision-Language Models**

根据跨层依赖与激活熵划分重构块，降低多模态量化误差。

- 作者：Changyuan Wang; Ziwei Wang; Xiuwei Xu; Yansong Tang; Jie Zhou; Jiwen Lu
- 年份：2024；依据：公开原始论文页面（见论文链接）
- 原文入口：[论文](https://proceedings.neurips.cc/paper_files/paper/2024/hash/cffbaf4f47546ece96bb42c0edda40ee-Abstract-Conference.html)
- PDF：[2024-Q-VLM.pdf](2024-Q-VLM.pdf)（21 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：公开论文入口已联网核对；本地 PDF 可能为较早版本。

<a id="p-915"></a>

## Bi-VLM

**Bi-VLM: Pushing Ultra-Low Precision Post-Training Quantization Boundaries in Vision-Language Models**

研究视觉语言模型的极低精度权重表示及视觉 token 冗余。

- 作者：Xijun Wang; Junyun Huang; Rayyan Abdalla; Chengyuan Zhang; Ruiqi Xian; Dinesh Manocha
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2509.18763)
- PDF：[2025-Bi-VLM.pdf](2025-Bi-VLM.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-919"></a>

## LUQ

**LUQ: Layerwise Ultra-Low Bit Quantization for Multimodal Large Language Models**

面向多模态模型的逐层超低比特量化。

- 作者：Shubhang Bhatnagar; Andy Xu; Kar-Han Tan; Narendra Ahuja
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2509.23729)
- PDF：[2025-LUQ.pdf](2025-LUQ.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-921"></a>

## VLMQ-Hessian-Augmentation

**VLMQ: Efficient Post-Training Quantization for Large Vision-Language Models via Hessian Augmentation**

通过 Hessian 增强改善视觉语言模型的 PTQ。

- 作者：Yufei Xue; Yushi Huang; Jiawei Shao; Jun Zhang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2508.03351)
- PDF：[2025-VLMQ-Hessian-Augmentation.pdf](2025-VLMQ-Hessian-Augmentation.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：库中有另一篇也使用 VLMQ 名称、但题名和摘要不同的资料，暂分开保留。

<a id="p-923"></a>

## VLMQ-Token-Redundancy

**Towards Efficient Post-Training Quantization for Large Vision-Language Models via Token-wise Redundancy Elimination**

独立匿名稿：抑制冗余视觉 token，并用重要性感知目标指导量化。

- 作者：Anonymous authors(本地匿名稿)
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Towards%20Efficient%20Post-Training%20Quantization%20for%20Large%20Vision-Language%20Models%20via%20Token-wise%20Redundancy%20Elimination)（检索入口，非已核实原文链接）
- PDF：[undated-VLMQ-Token-Redundancy.pdf](undated-VLMQ-Token-Redundancy.pdf)（21 页）
- 导读依据：本地 PDF 前两页。
- 版本说明：所选 PDF 为匿名稿；不据投稿年份推断发表年份；库中有另一篇也使用 VLMQ 名称、但题名和摘要不同的资料，暂分开保留。

<a id="p-925"></a>

## QSLAW

**Advancing Multimodal Large Language Models with Quantization-Aware Scale Learning for Efficient Adaptation**

通过量化感知尺度学习和多模态预热改善视觉语言适配。

- 作者：JingJing Xie; Yuxin Zhang; Mingbao Lin; Liujuan Cao; Rongrong Ji
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://dl.acm.org/doi/10.1145/3664647.3680838)
- PDF：[2024-QSLAW.pdf](2024-QSLAW.pdf)（11 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-890"></a>

## SPEED-Q

**SPEED-Q: Staged Processing with Enhanced Distillation towards Efficient Low-bit On-device VLM Quantization**

分阶段处理与增强蒸馏，面向端侧 VLM 的低比特量化。

- 作者：Tianyu Guo; Shanwei Zhao; Shiai Zhu; Chenguang Ma
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2511.08914) · [作者代码（本地摘要提供）](https://github.com/antgroup/SPEED-Q)
- PDF：[2025-SPEED-Q.pdf](2025-SPEED-Q.pdf)（13 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-885"></a>

## AKVQ-VL

**AKVQ-VL: Attention-Aware KV Cache Adaptive 2-Bit Quantization for Vision-Language Models**

多模态 KV 分支：依据文本和关键 token 的注意力分配比特。

- 作者：Zunhai Su; Wang Shen; Linge Li; Zhe Chen; Hanyu Wei; Huangqi Yu; Kehong Yuan
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2501.15021)
- PDF：[2025-AKVQ-VL.pdf](2025-AKVQ-VL.pdf)（7 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-886"></a>

## CASP

**CASP: Compression of Large Multimodal Models Based on Attention Sparsity**

结合注意力稀疏性、低秩分解和最优比特分配压缩多模态模型。

- 作者：Mohsen Gholami; Mohammad Akbari; Kevin Cannons; Yong Zhang
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2503.05936)
- PDF：[2025-CASP.pdf](2025-CASP.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
- 版本说明：已合并重复题录/不同本地版本，保留一份代表 PDF。

<a id="p-74"></a>

## VQ4DiT

**VQ4DiT: Efficient Post-Training Vector Quantization for Diffusion Transformers**

将向量量化用于扩散 Transformer，联合考虑码本与分配。

- 作者：Juncan Deng; Shuaiting Li; Zeyu Wang; Hong Gu; Kedong Xu; Kejie Huang
- 年份：未确认；依据：未确认
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=VQ4DiT%3A%20Efficient%20Post-Training%20Vector%20Quantization%20for%20Diffusion%20Transformers)（检索入口，非已核实原文链接）
- PDF：[undated-VQ4DiT.pdf](undated-VQ4DiT.pdf)（9 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-982"></a>

## Shift-and-Sum

**Shift-and-Sum Quantization for Visual Autoregressive Models**

视觉自回归模型：用平移求和量化与校准重采样降低误差。

- 作者：Jaehyeon Moon; Bumsub Ham
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[按完整题名检索](https://scholar.google.com/scholar?q=Shift-and-Sum%20Quantization%20for%20Visual%20Autoregressive%20Models)（检索入口，非已核实原文链接）
- PDF：[2026-Shift-and-Sum.pdf](2026-Shift-and-Sum.pdf)（22 页）
- 导读依据：本地 PDF 前两页。

<a id="p-977"></a>

## QVLA

**QVLA: Not All Channels Are Equal in Vision-Language-Action Model's Quantization**

视觉语言动作模型：基于通道重要性统一量化与剪枝。

- 作者：Yuhao Xu; Yantai Yang; Zhenyang Fan; Yufan Liu; Yuming Li; Bing Li; Zhipeng Zhang
- 年份：2026；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2602.03782)
- PDF：[2026-QVLA.pdf](2026-QVLA.pdf)（17 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
