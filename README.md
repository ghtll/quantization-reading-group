# 量化论文阅读小组

面向新入组同学的量化阅读资料库，以大模型量化为主，兼顾经典理论、视觉与多模态、推理系统和评测。

**本地 Zotero 整理 · 2026-10-07 · 152 篇论文 + 1 份讲义 · 10 个主题 · 152 份 PDF（约 619.7 MiB）**

每个分类目录包含一份导读 README 和已有的论文 PDF。Non-Subtractive Dither 一篇在本地库中没有附件，已保留题录与公开链接。导读为中文一句话概括，附完整题名、作者、库中年份、原文入口及版本说明。

## Excel 论文清单

[打开 papers.xlsx](papers.xlsx)。工作簿按上述 10 个文件夹分类建立工作表，每篇只保留“论文名字、简介、AI摘要”三列，支持筛选并冻结表头。

简介是一句话概括；AI摘要依据本地文献摘要及此前提取的 PDF 前两页，概述问题与方法，未视为全文精读。原文入口和版本说明仍见各分类 README。原 153 条资料全部保留，其中包括 1 份明确标注的 Lloyd-Max 讲义。更新日期：2026-10-08。

## 从哪里开始

第一次接触量化，可以先沿下面这条路线读完 10 篇，不必一开始遍历整个资料库：

1. [量化综述](00-surveys/README.md#p-84)：弄清 PTQ、QAT、量化粒度、标度与舍入。
2. [AdaRound](01-foundations/README.md#p-39)：为什么直接四舍五入不够好？
3. [GPTQ](02-weight-ptq/README.md#p-33)：如何用二阶信息补偿逐步量化产生的误差？
4. [AWQ](02-weight-ptq/README.md#p-37)：为什么观察激活可以帮助量化权重？
5. [LLM.int8()](03-activation-transforms/README.md#p-197)：大模型中的异常特征是什么？
6. [SmoothQuant](03-activation-transforms/README.md#p-202)：如何在权重和激活之间迁移量化难度？
7. [QuaRot](03-activation-transforms/README.md#p-132)：等价旋转为什么能改善量化？
8. [LLM-QAT](05-qat-adaptation/README.md#p-201)：训练参与后，能恢复哪些低比特损失？
9. [QServe](06-kv-cache-systems/README.md#p-172)：低比特表示如何转化为实际服务加速？
10. [Evaluating Quantized LLMs](09-evaluation-security/README.md#p-180)：应该怎样完整评估量化模型？

数学背景较弱时，先补 [Lloyd-Max 讲义](01-foundations/README.md#p-92)；想理解 GPTQ 的推导，可在 GPTQ 前读 [Optimal Brain Compression](01-foundations/README.md#p-30)。以上是教学阅读顺序，不是发表时间顺序。

## 分类导航

| 目录 | 数量 | 主要问题 |
| --- | ---: | --- |
| [综述与全景](00-surveys/README.md) | 6 | 先认识术语与研究地图，再进入具体方法。离散 token 综述属于延伸方向。 |
| [量化基础与经典理论](01-foundations/README.md) | 18 | 包含经典量化、PTQ 重构基础，以及信号处理和分布量化的选读资料。 |
| [权重 PTQ 与误差补偿](02-weight-ptq/README.md) | 17 | 以权重量化、二阶近似、重构目标和跨层误差控制为主；部分方法也支持激活量化。 |
| [激活异常值与等价变换](03-activation-transforms/README.md) | 22 | 通过缩放、重排、旋转或仿射变换改善量化分布；也纳入解释异常值来源的分析论文。 |
| [非均匀、向量与超低比特表示](04-nonuniform-vector-extreme/README.md) | 23 | 关注量化网格、码本、二值表示和有效位数；部分方法同时使用旋转或训练。 |
| [QAT、低比特训练与适配](05-qat-adaptation/README.md) | 20 | 包含量化感知训练、蒸馏、低秩补偿、低精度微调，以及量化友好的预训练。 |
| [KV Cache 与推理系统](06-kv-cache-systems/README.md) | 17 | 关注长上下文缓存、存储与计算精度、GPU 内核和端到端服务效率。 |
| [视觉与多模态量化](07-vision-multimodal/README.md) | 19 | 涵盖 ViT、VLM、扩散 Transformer、视觉自回归与视觉语言动作模型。 |
| [MoE、SSM 与其他模型](08-moe-ssm-other/README.md) | 7 | 按特殊模型结构组织，包括混合专家、状态空间模型、图网络和联邦应用。 |
| [评测、误差分析与安全](09-evaluation-security/README.md) | 4 | 从基准任务、扰动分析和安全能力评估量化效果；安全用途的向量量化单独标注为扩展。 |

每篇只放在一个主要主题下，避免重复 PDF。例如 AWQ 同时涉及激活缩放，但主归类为权重 PTQ；AKVQ-VL 属于 KV 量化，同时因多模态特性放在视觉与多模态目录。


## 文件结构

```text
quantization-reading-group/
├── README.md                     # 总览、阅读路线与组会建议
├── 00-surveys/ … 09-evaluation-security/
│   ├── README.md                 # 分类导读与完整题录
│   └── 年份-方法简称.pdf           # 本地论文副本
├── papers.xlsx                   # 按 10 个分类分表：论文名字、简介、AI摘要
├── CURATION_NOTES.md              # 去重、附件归属与字段说明
├── READING_NOTE_TEMPLATE.md       # 学生阅读记录模板
└── .gitignore
```


