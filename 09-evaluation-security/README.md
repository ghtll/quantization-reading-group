# 评测、误差分析与安全

[返回总览](../README.md) · 4 份资料

从基准任务、扰动分析和安全能力评估量化效果；安全用途的向量量化单独标注为扩展。

先读 Evaluating Quantized LLMs，再根据课题选择误差分析或安全评测。

年份沿用本地题录、明确的 PDF 版本信息或标注的公开原始论文页面，不代表首次公开年份；“未确认”不作猜测。⭐ 为主线优先阅读。

PDF 与本文件位于同一目录，可通过下方文件链接直接阅读；“论文”链接指向外部原文入口。

## 目录

| 资料 | 年份 | 阅读提示 |
| --- | --- | --- |
| ⭐ [Evaluating-Quantized-LLMs](#p-180) | 2024 | 核心必读:分别评估权重、激活和 KV 量化在多种任务上的影响。 |
| [Quantization-Perturbation](#p-191) | 2024 | 把量化视为扰动,分析大模型对不同误差的敏感性。 |
| [Q-resafe](#p-50) | 2025 | 评估量化对模型安全能力的影响,并研究量化感知修补。 |
| [Q-MLLM](#p-888) | 2025 | 扩展阅读:用向量量化增强多模态安全,目标不同于单纯低比特压缩。 |

<a id="p-180"></a>

## Evaluating-Quantized-LLMs

**Evaluating Quantized Large Language Models**

核心必读：分别评估权重、激活和 KV 量化在多种任务上的影响。

- 作者：Shiyao Li; Xuefei Ning; Luning Wang; Tengxuan Liu; Xiangsheng Shi; Shengen Yan; Guohao Dai; Huazhong Yang; Yu Wang
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2402.18158)
- PDF：[2024-Evaluating-Quantized-LLMs.pdf](2024-Evaluating-Quantized-LLMs.pdf)（45 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-191"></a>

## Quantization-Perturbation

**What Makes Quantization for Large Language Model Hard? An Empirical Study from the Lens of Perturbation**

把量化视为扰动，分析大模型对不同误差的敏感性。

- 作者：Zhuocheng Gong; Jiahao Liu; Jingang Wang; Xunliang Cai; Dongyan Zhao; Rui Yan
- 年份：2024；依据：Zotero 日期字段
- 原文入口：[论文](https://ojs.aaai.org/index.php/AAAI/article/view/29765)
- PDF：[2024-Quantization-Perturbation.pdf](2024-Quantization-Perturbation.pdf)（8 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-50"></a>

## Q-resafe

**Q-resafe: Assessing Safety Risks and Quantization-aware Safety Patching for Quantized Large Language Models**

评估量化对模型安全能力的影响，并研究量化感知修补。

- 作者：Kejia Chen; Jiawen Zhang; Jiacong Hu; Yu Wang; Jian Lou; Zunlei Feng; Mingli Song
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2506.20251) · [作者代码（本地摘要提供）](https://github.com/Thecommonirin/Qresafe)
- PDF：[2025-Q-resafe.pdf](2025-Q-resafe.pdf)（19 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。

<a id="p-888"></a>

## Q-MLLM

**Q-MLLM: Vector Quantization for Robust Multimodal Large Language Model Security**

扩展阅读：用向量量化增强多模态安全，目标不同于单纯低比特压缩。

- 作者：Wei Zhao; Zhe Li; Yige Li; Jun Sun
- 年份：2025；依据：Zotero 日期字段
- 原文入口：[论文](https://arxiv.org/abs/2511.16229) · [作者代码（本地摘要提供）](https://github.com/Amadeuszhao/QMLLM)
- PDF：[2025-Q-MLLM.pdf](2025-Q-MLLM.pdf)（18 页）
- 导读依据：Zotero 摘要及本地 PDF 前两页。
