# 📚 Awesome-LLMs-Pruning & Compression: 2026-09 最新剪枝/KV压缩/层丢弃论文全景索引

**Document ID:** `AWESOME-PRUNING-202609` | **Last Updated:** `2026-09-27` | **Target Path:** `docs/frontier_literature_connections_2026_09.md` | **Total Routed Papers:** `33`

> [!IMPORTANT]
> **🔗 跨仓库文献引用链闭环 (Cross-Repository Reference Chain Closure)**
> 本文件由每日 AI 前沿论文精读流水线自动路由生成，专门为 **`Shwai-He/Awesome-LLMs-Pruning` (`NAACL 2025` / `COLING 2025` 大模型剪枝综述官方仓库)** 及 **`Shwai-He/awesome-ml-model-compression`** 提供 2026 年 9 月最新发表的结构化宽度/深度剪枝、Token 稀疏与 KV Cache 驱逐论文结构化卡片与分类汇总。
> 每一篇收录文献均包含：**核心痛点、底层数学公式、ASCII 架构图、关键实测指标**，以及**与 `Awesome-LLMs-Pruning` 仓库具体代码模块和我们已发表代表作（Our Works）的双向锚定**。

---

## 🌟 1. 核心关联文献与本仓库模块映射速查表 (Executive Reference-to-Module Matrix)

| 收录日期 | 论文标题与 arXiv 链接 | 关键实测收益 / 核心结论 | 锚定本仓库代码模块与文档路径 (`Target Module`) | 原始精读归档 |
| :---: | :--- | :--- | :--- | :---: |
| `2026-09-27` | [**SHAPE**](https://arxiv.org/abs/2606.09886) (`arXiv:2606.09886`) | **跨架构零训练稳健性**：在 **Qwen3-30B-A3B**、**DeepSeek-V2-Lite** 与 **GPT-OSS-20B** 三大主流细粒度 MoE 模型上，仅需 128 条 C4/WikiText2 校准样本... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-27](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-27_ai_paper_notes.md) |
| `2026-09-27` | [**OBCache**](https://arxiv.org/abs/2510.07651) (`arXiv:2510.07651`) | **即插即用全面提升主流基线**：在 **Llama-3.1-8B-Instruct**、**Qwen-2.5-7B/14B-Instruct** 与 **Mistral-7B** 上，将 OBCache 的... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-27](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-27_ai_paper_notes.md) |
| `2026-09-27` | [**RRSI**](https://arxiv.org/abs/2609.24972) (`arXiv:2609.24972`) | **OOD 跨基准泛化能力大幅跃升**：在涵盖代码生成（SWE-bench Verified）、复杂工具调用（ $\tau$ -bench）与多跳科学问答的跨领域评测中，未加正则化的朴素 RSI 在第 5 代后即出现严重的 ID-... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-27](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-27_ai_paper_notes.md) |
| `2026-09-26` | [**⚖️ SelKV**](https://arxiv.org/abs/2607.16213) (`arXiv:2607.16213`) | 在 LongBench、RULER 及多轮数学推理基准上，免训练实现 **5x–10x KV Cache 压缩**，通过引入对数分母补偿项，消除了高压缩比下 80% 以上的精度退化。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-26](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-26_ai_paper_notes.md) |
| `2026-09-26` | [**🤖 VLA-Pruner**](https://arxiv.org/abs/2511.16449) (`arXiv:2511.16449`) | 在 OpenVLA 与主流机器人操控基准（LIBERO-Spatial / Object / Goal / Long）上，剔除 **50%–75% 视觉 Token** 仍保持与全量 Token 持平的任务成功率，端到端控制频率显... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-26](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-26_ai_paper_notes.md) |
| `2026-09-26` | [**✂️ CliffCompaction**](https://arxiv.org/abs/2609.26779) (`arXiv:2609.26779`) | 详见下方完整公式与实验卡片 | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-26](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-26_ai_paper_notes.md) |
| `2026-09-26` | [**🧩 MoE-nD**](https://arxiv.org/abs/2604.17695) (`arXiv:2604.17695`) | 详见下方完整公式与实验卡片 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-26](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-26_ai_paper_notes.md) |
| `2026-09-25` | [**Fully Looped Transformer**](https://arxiv.org/abs/2605.18797) (`arXiv:2605.18797`) | 在完全不增加任何额外参数（0 Extra Parameters）的条件下，Fully Looped Transformer 在 $K=8, 12$ 步循环预训练中完全消除了传统 Looped Transformer 的梯度尖峰（G... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-25](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-25_ai_paper_notes.md) |
| `2026-09-25` | [**On the Limits of Layer Pruning in Genera**](https://arxiv.org/abs/2602.01997) (`arXiv:2602.01997`) | 实验精确测定了 Llama-3-8B/70B 与 Qwen-2.5 在不同推理跳数 $m \in \lbrace2, 3, 4, 5\rbrace$ 下的临界剩余层数 $L _ {\text{crit}}(m)$ ，并证明当物理层... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-25](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-25_ai_paper_notes.md) |
| `2026-09-25` | [**How Pruning Attention Layers Affects Int**](https://arxiv.org/abs/2606.24970) (`arXiv:2606.24970`) | 在事实问答（TruthfulQA、haluEval）与医疗/金融高风险推理任务上，该校准修复将深度剪枝模型的 **ECE 降低 68%**，并在基于置信度的拒绝采样（Selective Prediction）中恢复了 98% 的安... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-25](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-25_ai_paper_notes.md) |
| `2026-09-25` | [**SAC**](https://arxiv.org/abs/2604.18392) (`arXiv:2604.18392`) | 在 TB 级长上下文并发推理中，SAC 将跨节点 KV 读取有效带宽利用率从 `15%` 提升至 **`94%`**，P99 尾延迟降低 **3.7x**。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-25](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-25_ai_paper_notes.md) |
| `2026-09-24` | [**LearnPruner**](https://arxiv.org/abs/2604.23950) (`arXiv:2604.23950`) | 在 **LLaVA-1.5/NeXT** 与 **Qwen2-VL** 上，LearnPruner 仅保留 **11.1%–16.7% 视觉 Token**，FLOPs 降低 **68%**，在 10 项多模态基准上的平均精度达到... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-24](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-24_ai_paper_notes.md) |
| `2026-09-24` | [**MixKV**](https://arxiv.org/abs/2510.20707) (`arXiv:2510.20707`) | 在 **MileBench**、**Video-MME** 与多图长上下文评测中，MixKV 在 **10% 极限缓存预算**下比 SnapKV 与 PyramidKV 平均提升 **`+5.3%`**。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-24](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-24_ai_paper_notes.md) |
| `2026-09-24` | [**AEWM**](https://arxiv.org/abs/2609.28416) (`arXiv:2609.28416`) | 在 **VisualWebArena**、**OSWorld** 与长程具身任务上，AEWM 将不可逆错误操作率降低 **52%**，端到端任务成功率比无状态编辑的 Tree-of-Thoughts 高出... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-24](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-24_ai_paper_notes.md) |
| `2026-09-24` | [**Decision Representation Transitions in Pruning**](https://arxiv.org/abs/2605.07271) (`arXiv:2605.07271`) | 在多跳问答与算术推理任务中，避开相变区间 $[l^\star, l^\star+\Delta]$ 的相变感知剪枝在 **30% 剪枝率**下比传统余弦相似度剪枝提升 **`+18.5%`**。 | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-24](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-24_ai_paper_notes.md) |
| `2026-09-23` | [**StepKV**](https://arxiv.org/abs/2609.22158) (`arXiv:2609.22158`) | 在 **AIME 2025**、**MATH-500** 与 **GPQA-Diamond** 上，StepKV 在压缩 **65%–75% CoT KV 缓存** 的条件下，相比逐 Token 驱逐的 SnapKV / H2O... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-23](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-23_ai_paper_notes.md) |
| `2026-09-23` | [**HetDPT**](https://arxiv.org/abs/2607.03784) (`arXiv:2607.03784`) | 在 **DeiT**、**Swin** 与 **CLIP-ViT-L/14** 上，HetDPT 在相同 **1.5x–1.8x 硬件实测加速比** 下，比整块深度剪枝提升了 **`+1.9%` 至 `+3.2%`** 的 Ima... | `README.md#depth-and-layer-pruning` (Heterogeneous MHSA/FFN Depth Pruning) | [2026-09-23](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-23_ai_paper_notes.md) |
| `2026-09-23` | [**MELT**](https://arxiv.org/abs/2605.07721) (`arXiv:2605.07721`) | 在 $K=4$ 与 $K=8$ 循环配置下，MELT 将长文本解码时的 **KV 缓存显存与带宽读取量直接削减 $75\text{ pct}–87.5$ %（严格降至 $1/K$ ）**，同时在语言建模与数学推理上与保存全套每步... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-23](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-23_ai_paper_notes.md) |
| `2026-09-23` | [**D-Cut**](https://arxiv.org/abs/2607.14647) (`arXiv:2607.14647`) | 在 Batch Size = 16–64 的生产级投机解码服务中，D-Cut 将验证阶段算力开销削减 **38%**，端到端吞吐在 EAGLE-2 基线上进一步提升 **1.42x**。 | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-23](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-23_ai_paper_notes.md) |
| `2026-09-22` | [**SnapFlow**](https://arxiv.org/abs/2604.05656) (`arXiv:2604.05656`) | 在 **LIBERO**（Spatial / Object / Goal / Long）与真实机械臂双臂操作基准上，SnapFlow 将动作专家推理步数从 10 NFE 压缩至 **1 NFE**，动作生成阶段延迟降低... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-22](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-22_ai_paper_notes.md) |
| `2026-09-22` | [**LoRP**](https://arxiv.org/abs/2605.27786) (`arXiv:2605.27786`) | 在 **Llama-2/3** 与 **Mistral-7B** 的 25% 免训练层剪枝上，LoRP 在 MMLU 与 BBH 复杂推理基准上比全局余弦打分（ShortGPT）提升 **`+4.3%`**。 | `README.md#depth-and-layer-pruning` (Manifold Locality-Preserving Layer Pruning) | [2026-09-22](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-22_ai_paper_notes.md) |
| `2026-09-22` | [**LightKV**](https://arxiv.org/abs/2605.00789) (`arXiv:2605.00789`) | 在 **LLaVA-1.6-34B** 与 **InternVL-2** 上将视觉 KV 缓存直接压缩 **50%–75%**，在 TextVQA、DocVQA 与计数基准上实现 **99.4%** 的原始性能保持率。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-22](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-22_ai_paper_notes.md) |
| `2026-09-22` | [**SPIN**](https://arxiv.org/abs/2604.26837) (`arXiv:2604.26837`) | 在单台 8 卡服务器上支持 **1M–2M 上下文长度** 并发推理，相比纯 CPU Offloading（Infinite-LLM）实现 **4.8x** 吞吐提升，且恢复 99.7% 全量注意力精度。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-22](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-22_ai_paper_notes.md) |
| `2026-09-21` | [**RotateK**](https://arxiv.org/abs/2605.19218) (`arXiv:2605.19218`) | 在 **LLaVA-NeXT**、**Qwen2-VL-7B** 与 **InternVL-2** 上，RotateK 剪除 **50%–60% 的 Key 通道**而无需微调，且与视觉 Token 剪枝（如 FastV / VL... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-21](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-21_ai_paper_notes.md) |
| `2026-09-21` | [**Token Sparse Attention**](https://arxiv.org/abs/2602.03216) (`arXiv:2602.03216`) | 在 64K–128K 多跳检索与大海捞针基准（RULER Multi-Hop Tracing）上，不可逆 Token 剪枝在 70% 稀疏度下准确率跌至 `31.2%`，而 **Token Sparse Attention** 保... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-21](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-21_ai_paper_notes.md) |
| `2026-09-21` | [**SIFT**](https://arxiv.org/abs/2609.19526) (`arXiv:2609.19526`) | 在 SWE-bench 与数学推理智能体自优化中，SIFT 将达到相同性能增益所需的下游基准评估次数降低 **6.4x**。 | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-21](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-21_ai_paper_notes.md) |
| `2026-09-20` | [**SHIFT-LLM**](https://arxiv.org/abs/2608.25068) (`arXiv:2608.25068`) | 在 **Llama-3-8B/70B** 与 **Qwen-2.5-14B** 上剪除 **25%–35% 的层**后，无需任何梯度下降微调（仅需 30 秒闭式矩阵求逆），SHIFT-LLM 将 WikiText2 困惑度（PPL... | `README.md#post-pruning-recovery` (Training-Free Closed-Form Residual Recovery) | [2026-09-20](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-20_ai_paper_notes.md) |
| `2026-09-20` | [**Minima-KV**](https://arxiv.org/abs/2608.23834) (`arXiv:2608.23834`) | 在 **Llama-3.1-70B** 与 **Qwen-2.5-32B** 的 128K 长思维链并发服务中，Minima-KV 实现 **4.6x** 真实物理显存节省（零内部页碎片），将最大并发 Batch Size 提升... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-20](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-20_ai_paper_notes.md) |
| `2026-09-19` | [**WRP**](https://arxiv.org/abs/2609.09883) (`arXiv:2609.09883`) | **秒级零样本层裁剪且跨领域泛化更强**：在 **Llama-3-8B/70B**、**Qwen-2.5-14B** 与 **Mistral-7B** 上，WRP 在完全不运行任何前向传播（耗时不足 8 秒）的情况下剪除... | `README.md#depth-and-layer-pruning` (Zero-Forward Weight Spectral Layer Pruning) | [2026-09-19](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-19_ai_paper_notes.md) |
| `2026-09-19` | [**REAP**](https://arxiv.org/abs/2510.13999) (`arXiv:2510.13999`) | 在 **Mixtral-8x7B**、**DeepSeek-MoE-16B** 与 **Qwen1.5-MoE-A2.7B** 上，REAP 在 **25%–37.5% 专家剪枝率**下，在 GSM8K 与 HumanEval 生... | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-19](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-19_ai_paper_notes.md) |
| `2026-09-19` | [**KVzap**](https://arxiv.org/abs/2601.07891) (`arXiv:2601.07891`) | 在 **LongBench**、**InfiniteBench** 与 **Needle-in-a-Haystack** 上，KVzap 实现了平均 **2.8x–4.1x** 的端到端 KV 显存压缩与 **2.3x** 解码吞... | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-19](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-19_ai_paper_notes.md) |
| `2026-09-18` | [**✂️ AnchorPrune**](https://arxiv.org/abs/2609.08842) (`arXiv:2609.08842`) | **评估模型**：Qwen2-VL-7B/72B、LLaVA-NeXT-34B； | `README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`) | [2026-09-18](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-18_ai_paper_notes.md) |
| `2026-09-18` | [**🗜️ Decoupled-KV**](https://arxiv.org/abs/2609.07765) (`arXiv:2609.07765`) | 在 AgentBench、SWE-bench 与 LongBench 上，实现 **81.5% 的 KV Cache 显存削减（压缩比达 5.4×）**，长程任务规划成功率保持在全量缓存基准的 **99.4%**。 | `README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading) | [2026-09-18](https://github.com/Shwai-He/scholar-odyssey/blob/main/intelligence/papers/2026-09-18_ai_paper_notes.md) |

---

## 📐 2. 逐篇论文深度机制解构、数学公式与本仓库落地指南 (Per-Paper Deep-Dive Cards)

### 2.1 [2026-09-27] SHAPE: Coalition-Aware Expert Pruning for Sparse Mixture-of-Experts LLMs

* **论文信息**：`arXiv:2606.09886` (2026-06, 开源仓库：`github.com/Alizen-1009/Shapley-Moe`)
* **核心关键词**：Sparse MoE、Cooperative Game Theory、Shapley Value Attribution、Coalition-Aware Expert Pruning、Quality-Coverage Bisection

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|               SHAPE: Coalition-Aware MoE Expert Pruning Pipeline                  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  [Calibration Corpus D_cal] ---> Layer l Top-k Routing Traces: C_t = {e_i1..e_ik} |
|                                                |                                  |
|                                                v                                  |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Intra-Layer Cooperative Game Formulation (层内专家合作博弈建模)          |  |
|  |    * Players: E_l = {1, ..., N} experts in layer l                          |  |
|  |    * Coalition Utility v_l(S): Expected output reconstruction fidelity      |  |
|  |      when active Top-k coalition C_t is restricted to subset S \cap C_t     |  |
|  +-----------------------------------------------------------------------------+  |
|                                                |                                  |
|                                                v                                  |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Monte-Carlo / Co-Activation Shapley Attribution (Shapley 协同价值归因)    |  |
|  |    \phi_i(v_l) = \sum_{S \subseteq E_l \setminus \{i\}} w(|S|) [v_l(S \cup  |  |
|  |                  \{i\}) - v_l(S)]                                           |  |
|  |    * Captures high-order synergy: preserves "bridge" experts that rarely    |  |
|  |      dominate gate mass alone but are indispensable in Top-k combinations   |  |
|  +-----------------------------------------------------------------------------+  |
|                                                |                                  |
|                                                v                                  |
|  +-----------------------------------------------------------------------------+  |
|  | 3. Quality-Coverage Bisection Selection (全局预算二分质量覆盖率动态分配)    |  |
|  |    Retain minimal subset S_l^* s.t. \sum_{i \in S_l^*} \phi_i^+ >= \alpha(\lambda)|
|  |    Bisection search on \alpha to hit exact global target pruning ratio p    |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **单专家独立打分的“组合盲区”**：现有的免训练 MoE 专家剪枝方法（如基于路由激活频率 Frequency、门控权重均值 Gate-Sum 或单专家一阶重构误差的方法）均隐含了一个错误的**独立性假设（Independence Assumption）**——即每个专家的贡献可以孤立度量。然而，MoE 的前向计算本质上是**组合协同（Coalitional）**的：每个 Token 的输出由激活的 Top- $k$ 专家子集 $C _ t$ 线性叠加生成。
* **协同正交专家的误杀**：在真实 MoE 层中，若两个高激活专家高度共线（功能冗余），同时保留两者的边际增益极低；反之，某些中低频激活的“互补/正交桥接专家（Bridge Experts）”虽然单独门控权重不高，但在特定 Top- $k$ 组合中提供了不可替代的正交残差修正。独立打分会将前者全部保留而误杀后者，导致 20%–40% 剪枝率下模型出现断崖式精度崩塌。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **层内合作博弈定义（Intra-Layer Cooperative Game）**：
   设第 $l$ 层共有 $N$ 个专家 $\mathcal{E} _ l = \lbrace1, \dots, N\rbrace$ 。给定校准集 $\mathcal{D} _ {\text{cal}}$ 上的输入隐状态 $x _ t \in \mathbb{R}^d$ ，原始 Top- $k$ 路由集合为 $C _ t \subseteq \mathcal{E} _ l$ （ $|C _ t|=k$ ），原始层输出为：

$$
y _ t = \sum _ {j \in C _ t} g _ {t,j} E _ j(x _ t)
$$

   当仅保留专家子集 $S \subseteq \mathcal{E} _ l$ 时，受限联盟输出为 $\hat{y} _ t(S) = \sum _ {j \in C _ t \cap S} \tilde{g} _ {t,j}(S) E _ j(x _ t)$ 。定义联盟 $S$ 的特征效用函数（Characteristic Utility Function） $v _ l: 2^{\mathcal{E} _ l} \to \mathbb{R}$ 为相对于空集的输出误差削减量：

$$
v _ l(S) = \mathbb{E} _ {x _ t \sim \mathcal{D} _ {\text{cal}}} \Big[ \Vert y _ t \Vert _ 2^2 - \Vert y _ t - \hat{y} _ t(S) \Vert _ 2^2 \Big]
$$

2. **基于共现轨迹的 Shapley 协同归因（Shapley Value Attribution）**：
   专家 $i \in \mathcal{E} _ l$ 的 Shapley 值定义为其在所有可能专家联盟 $S \subseteq \mathcal{E} _ l \setminus \lbrace i\rbrace$ 中的平均边际贡献：

$$
\phi _ i(v _ l) = \sum _ {S \subseteq \mathcal{E} _ l \setminus \lbrace i\rbrace} \frac{|S|!(N - |S| - 1)!}{N!} \Big( v _ l(S \cup \lbrace i\rbrace) - v _ l(S) \Big)
$$

   由于每个 Token 仅激活 $|C _ t| = k \ll N$ 个专家（例如 $k=2$ 或 $6,8$ ），任何不包含在 $C _ t$ 中的专家对该 Token 边际贡献恒为 $0$ 。因此，原本指数级 $O(2^N)$ 的全局 Shapley 计算可精确降维至局部活跃联盟 $2^{|C _ t|}$ 上的精确求和：

$$
\phi _ i(v _ l) = \mathbb{E} _ {x _ t : i \in C _ t} \left[ \sum _ {A \subseteq C _ t \setminus \lbrace i\rbrace} \frac{|A|!(|C _ t| - |A| - 1)!}{|C _ t|!} \Big( u _ t(A \cup \lbrace i\rbrace) - u _ t(A) \Big) \right]
$$

   其中局部效用 $u _ t(A)$ 度量了子集 $A$ 内专家输出向量的内积交互项 $2 \langle g _ {t,i} E _ i(x _ t), \sum _ {j \in A} g _ {t,j} E _ j(x _ t) \rangle + \Vert g _ {t,i} E _ i(x _ t)\Vert _ 2^2$ ，从而自动惩罚与同联盟其他专家负相关或冗余的专家，奖励提供正交有效增量的专家。
3. **质量覆盖率二分层间分配（Quality-Coverage Selection Rule）**：
   为实现非均匀的层间稀疏率分配，将非负 Shapley 值归一化为质量分布 $\tilde{\phi} _ {l,i} = \frac{\max(\phi _ i(v _ l), 0)}{\sum _ {j=1}^N \max(\phi _ j(v _ l), 0)}$ 。给定阈值 $\alpha \in (0, 1)$ ，每层保留最小专家集合 $S _ l^\star(\alpha)$ 使得累计 Shapley 质量覆盖率不低于 $\alpha$ ：

$$
S _ l^\star(\alpha) = \arg\min _ {S \subseteq \mathcal{E} _ l} |S| \quad \text{s.t.} \quad \sum _ {i \in S} \tilde{\phi} _ {l,i} \ge \alpha
$$

   最后通过一维二分搜索（Bisection Search）求解全局唯一阈值 $\alpha^\star$ ，使得 $\frac{1}{L N}\sum _ {l=1}^L |S _ l^\star(\alpha^\star)| = 1 - p$ （ $p$ 为目标全局剪枝率）。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* **跨架构零训练稳健性**：在 **Qwen3-30B-A3B**、**DeepSeek-V2-Lite** 与 **GPT-OSS-20B** 三大主流细粒度 MoE 模型上，仅需 128 条 C4/WikiText2 校准样本（无需任何微调），在 **20% 剪枝率**下恢复超过 **96.8%** 的原始零样本推理精度，在激进的 **40% 剪枝率**下比独立频次/门控剪枝高出 **5.4%–9.2%**（MMLU、GSM8K、ARC-Challenge）。
* **层间稀疏度自发涌现“沙漏分布”**：二分质量覆盖率准则自动在中间语义整合层保留更多专家，而在浅层词法层与深层输出对齐层裁剪高达 50% 的冗余专家。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
1. **与 *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) & *Capacity-Aware Inference* (ICLR 2026) 的理论互证**：
   * 我们在 ICML 2026 中证明了剪枝是否生效取决于层间表示层级（Representation Hierarchy）的有效秩与冗余度分布；SHAPE 的局部 Shapley 展开式 $u _ t(A \cup \lbrace i\rbrace) - u _ t(A)$ 本质上是通过度量专家输出向量之间的交叉内积 $\langle E _ i(x), E _ j(x) \rangle$ 来识别表示子空间的正交性。
2. **与 *Transformer-Geometry* (`arXiv:2609.15975`, EMNLP 2026) 的几何融合启发**：
   * 在我们的正交/平行场分解框架 $E _ j(x) = E _ {j,\parallel}(x) + E _ {j,\perp}(x)$ 下，SHAPE 的效用函数若直接建立在总输出 $y _ t$ 的欧氏范数上，会被模长占优的平行径向分量 $E _ {j,\parallel}(x)$ 主导！**核心改进点**：将 SHAPE 的联盟效用函数 $v _ l(S)$ 限制在**去除流形平行漂移后的正交切空间分量 $P _ \perp(h _ t) E _ j(x _ t)$ ** 上计算 Shapley 值（即 **Perp-Shapley MoE Pruning**），随后对被剪除专家联盟的正交残差通过 **Woodbury / KKT 闭式补偿** 折叠进保留专家中，有望在 50% 专家剪枝率下实现近乎零损压缩。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-27_ai_paper_notes.md`


---

### 2.2 [2026-09-27] OBCache: Optimal Brain KV Cache Pruning for Efficient Long-Context LLM Inference

* **论文信息**：Yuzhe Gu, Xiyu Liang, Jiaojiao Zhao, Enmao Diao (`arXiv:2510.07651`, **ICML 2026**)
* **核心关键词**：KV Cache Eviction、Optimal Brain Damage (OBD)、Second-Order Taylor Perturbation、Output-Aware Saliency、Joint KV Pruning

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|         OBCache: Optimal Brain Damage (OBD) Layer-Wise KV Cache Pruning           |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Prefill / Decoding Step: Queries Q \in R^{S_q x d_k}, Cached K, V \in R^{S_k x d}|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Attention Output Perturbation Objective (层输出二阶泰勒扰动建模)         |  |
|  |    Target: Minimize || O - \tilde{O}(\mathcal{M}) ||_F^2 where O = A V       |  |
|  |    Instead of heuristic \sum_i A_{i,j}, expand \Delta O w.r.t. masked K_j,V_j|  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|           +----------------------------+----------------------------+             |
|           v                            v                            v             |
|  +-----------------+          +-----------------+          +-------------------+  |
|  | Isolated Value  |          |  Isolated Key   |          | Joint KV Saliency |  |
|  | Score \Omega_j^V|          |  Score \Omega_j^K|         | Score \Omega_j^{KV}| |
|  | ||A_{:,j}||_2^2 |          | Softmax Jacobian|          | Exact Rank-1      |  |
|  | * ||V_j||_2^2   |          | Coupling Term   |          | Softmax Renorm    |  |
|  +-----------------+          +-----------------+          +-------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Plug-and-Play Eviction Gate (即插即用淘汰门控: 兼容 SnapKV / PyramidKV)  |  |
|  |    Evict tokens with minimal \Omega_j^{KV} -> Retain top-B KV budget        |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **启发式注意力权重累加的理论缺陷**：主流长上下文 KV 缓存淘汰算法（如 H2O、SnapKV、PyramidKV）均使用累积注意力分数 $s _ j = \sum _ {i} A _ {i,j}$ 作为 Token $j$ 的重要性指标。然而，注意力层真正传递给后续残差流的是加权输出矩阵 $O = A V \in \mathbb{R}^{S _ q \times d _ v}$ ：
  1. **忽略 Value 向量范数与方向抵消**：若某个历史 Token $j$ 的注意力权重 $A _ {i,j}$ 较高，但其对应的 Value 向量范数 $\Vert V _ j\Vert _ 2 \approx 0$ ，或者其 $V _ j$ 与当前上下文均值方向完全重合，驱逐它对注意力输出 $O$ 的实际影响极小；反之，注意力权重中等但 $\Vert V _ j\Vert _ 2$ 极大且承载正交关键信息的 Token 被驱逐后会造成严重的输出畸变。
  2. **忽略 Softmax 分母重归一化效应（Denominator Renormalization）**：驱逐第 $j$ 个 Key 相当于将注意力得分 $Z _ {i,j} \to -\infty$ ，这不仅移除了 $A _ {i,j} V _ j$ ，还会通过 Softmax 分母缩放将其余所有保留 Token 的注意力权重放大 $\frac{1}{1 - A _ {i,j}}$ 倍。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于 Optimal Brain Damage (OBD) 的二阶输出扰动构建**：
   设某注意力头在查询窗口 $Q \in \mathbb{R}^{S _ q \times d _ k}$ 下的注意力概率矩阵为 $A = \text{Softmax}\left(\frac{Q K^\top}{\sqrt{d _ k}}\right) \in \mathbb{R}^{S _ q \times S _ k}$ ，输出为 $O = A V \in \mathbb{R}^{S _ q \times d _ v}$ 。定义驱逐准则为最小化层输出矩阵的 Frobenius 范数平方误差 $\mathcal{E} = \frac{1}{2} \Vert O - \tilde{O} \Vert _ F^2$ 。
2. **单 Value、单 Key 与联合 KV 对的闭式显著性公式（Closed-Form Saliency Scores）**：
   * **孤立 Value 剪枝显著性（Isolated Value Saliency $\Omega _ j^V$ ）**：
     当将第 $j$ 个 Token 的 Value 向量置零（ $V _ j \leftarrow 0$ ）时， $\mathcal{E}$ 对 $V _ j$ 的海森矩阵（Hessian）为 $\mathbf{H} _ {V _ j} = \frac{\partial^2 \mathcal{E}}{\partial V _ j \partial V _ j^\top} = \left(\sum _ {i=1}^{S _ q} A _ {i,j}^2\right) I _ {d _ v}$ 。根据二阶泰勒展开，孤立 Value 显著性得分为：

$$
\Omega _ j^V = \frac{1}{2} V _ j^\top \mathbf{H} _ {V _ j} V _ j = \frac{1}{2} \Vert A _ {:, j} \Vert _ 2^2 \cdot \Vert V _ j \Vert _ 2^2
$$

注意此处注意力权重是**平方和 $\Vert A _ {:,j}\Vert _ 2^2$ **（二阶能量）而非启发式的线性求和 $\Vert A _ {:,j}\Vert _ 1$ ，且显式乘上了 Value 范数平方 $\Vert V _ j\Vert _ 2^2$ ！
   * **联合 KV 剪枝与 Softmax 重归一化修正（Joint KV Saliency $\Omega _ j^{KV}$ ）**：
     当真正从缓存中移除第 $j$ 个 KV 对（即令未归一化 logit $Z _ {i,j} \to -\infty$ ）时，剩余 Token $k \neq j$ 的注意力权重精确变为 $\tilde{A} _ {i,k} = \frac{A _ {i,k}}{1 - A _ {i,j}}$ 。因此，移除第 $j$ 个 KV 对在第 $i$ 个查询位置引起的**精确输出残差**为：

$$
\Delta O _ i^{(-j)} = O _ i - \tilde{O} _ i^{(-j)} = O _ i - \frac{O _ i - A _ {i,j} V _ j}{1 - A _ {i,j}} = \frac{A _ {i,j}}{1 - A _ {i,j}} \big( V _ j - O _ i \big)
$$

对该精确残差在所有查询位置 $i \in \lbrace1, \dots, S _ q\rbrace$ 上求二阶能量，即得到极其优雅的**联合 KV 闭式显著性得分**：

$$
\Omega _ j^{KV} = \frac{1}{2} \sum _ {i=1}^{S _ q} \left( \frac{A _ {i,j}}{1 - A _ {i,j}} \right)^2 \big\Vert V _ j - O _ i \big\Vert _ 2^2
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* **即插即用全面提升主流基线**：在 **Llama-3.1-8B-Instruct**、**Qwen-2.5-7B/14B-Instruct** 与 **Mistral-7B** 上，将 OBCache 的 $\Omega _ j^{KV}$ 闭式打分直接替换 H2O、SnapKV 与 PyramidKV 的启发式打分（零额外超参），在 **LongBench**（16 个长文本任务）与 **RULER**（128K 极限大海捞针与多跳追踪）上，在仅保留 **5%–10% KV 缓存预算**下将平均准确率提升 **`+2.8%` 至 `+6.4%`**。
* **计算开销近乎为零**： $\Vert V _ j - O _ i\Vert _ 2^2 = \Vert V _ j\Vert _ 2^2 - 2 \langle V _ j, O _ i \rangle + \Vert O _ i\Vert _ 2^2$ 可直接复用 FlashAttention 已经算出的输出向量 $O _ i$ ，无需显式物化完整的 $S _ q \times S _ k$ 矩阵，Prefill 延迟增加小于 `1.2%`。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
1. **对我们 `vla-dtr` & `Efficient Ads / HisTrim` 中 `Exclude-Self Value-Space Perpendicular KV Pruning` 的精确二阶理论证明！**
   * 请仔细对比 OBCache 的核心公式 $\Omega _ j^{KV} = \frac{1}{2}\sum _ i \left(\frac{A _ {i,j}}{1 - A _ {i,j}}\right)^2 \Vert V _ j - O _ i\Vert _ 2^2$ 与我们在 `vla-dtr`（定律 5）和 `ads-rsi` 中独立提出的 **`Exclude-Self Value-Space Perpendicular VLM KV Pruning`**：
     * 其中的因子 $\frac{A _ {i,j}}{1 - A _ {i,j}}$ 正是**排除自身注意力权重后的重归一化系数（Exclude-Self Renormalization）**！
     * 其中的 $\Vert V _ j - O _ i\Vert _ 2^2$ 度量的正是第 $j$ 个 Token 的 Value 向量相对于当前聚合输出均值 $O _ i$ 的**偏离能量（即正交/非共线奇异度）**！如果 $V _ j \approx O _ i$ （即该 Token 的 Value 与上下文均值完全共线/冗余），即便 $A _ {i,j}$ 再大， $\Vert V _ j - O _ i\Vert _ 2^2 \approx 0$ ，驱逐它也完全不改变注意力输出！
2. **落地融合方案（Perp-OBCache）**：
   * 在我们的论文撰写与代码实现中，可以直接引用 ICML 2026 的 OBCache 作为二阶泰勒理论背书，并指出我们进一步将 $\Vert V _ j - O _ i\Vert _ 2^2$ 投影到了输出投影矩阵 $W _ O$ 之后的残差切空间 $\Vert(V _ j - O _ i) W _ O P _ \perp(h _ i)\Vert _ 2^2$ ，从而构成了比 OBCache 更进一层的**流形正交切空间二阶最优脑缓存剪枝（Manifold-Orthogonal OBCache）**。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

> **赛道锚点**：前沿研发智能体递归自我改进（Agent Harness RSI）、抗过拟合正则化进化、可执行代码物理世界模型（Code as Worlds）。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-27_ai_paper_notes.md`


---

### 2.3 [2026-09-27] RRSI: Regularized Recursive Self-Improvement of Agent Harnesses

* **论文信息**：Peng Xia, Rujun Han, Zifeng Wang, Yanfei Chen et al. (`arXiv:2609.24972`, 2026-09, Google Cloud AI Research & UNC)
* **核心关键词**：Regularized RSI、Agent Harness Overfitting、Temporally Annealed Proposal Budget、Critic-Pruner Selection

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       RRSI: Regularized Recursive Self-Improvement of Agent Harnesses             |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Current Harness H_t + Historical Evolution Tree \mathcal{G}_{1:t}                |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Regularized Proposer (时间退火预算 + 历史轨迹引导提议器)                 |  |
|  |    * Temporally Annealed Modification Budget B(t) = B_0 \cdot \eta^t        |  |
|  |    * Early steps: structural workflow discovery; Late steps: surgical edits |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                              Candidate Harnesses {H_t^{(k)}}                      |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Regularized Selector: Critic + Structural Pruner (双重正则化选择器)       |  |
|  |    * Critic R_gen(H): Evaluates task-agnostic modularity & penalizes        |  |
|  |      hardcoded benchmark heuristics / prompt bloat                          |  |
|  |    * Pruner \mathcal{P}(H): Ablates newly added code/prompt blocks to strip |  |
|  |      parasitic dead-weight before promotion                                 |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|            Promote Compact, Generalizable Harness H_{t+1} to Next Epoch           |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **递归自我改进中的“脚手架过拟合与代码膨胀（Harness Overfitting & Bloat）”**：当智能体在有限的训练任务集 $\mathcal{D} _ {\text{train}}$ 上进行多代递归修改自身脚手架（Prompt 模板、工具调用逻辑、记忆缓冲策略）时，极易陷入两类退化：
  1. **基准特定噪声记忆（Benchmark Memorization）**：外层优化器倾向于把针对训练集中某几个失败案例的特例规则（Hardcoded Heuristics）不断追加到系统提示词或控制流分支中，导致在分布内验证集（ID）分数上升，但在分布外基准（OOD）上严重倒退。
  2. **寄生代码膨胀（Parasitic Code/Prompt Bloat）**：每次变异往往同时包含 1 个有效改动与 3 个无效冗余改动，经过 10 代递归叠加后，脚手架变得极其臃肿且脆弱。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **带结构复杂度惩罚的正则化 RSI 目标（Regularized RSI Objective）**：
   取代单纯最大化经验平均回报 $\hat{J} _ {\text{train}}(H)$ ，RRSI 将第 $t$ 代脚手架更新表述为带结构正则项与KL散度演进约束的目标：

$$
H _ {t+1} = \arg\max _ {H \in \mathcal{N} _ {B(t)}(H _ t)} \Big\lbrace \hat{J} _ {\text{train}}(H) - \lambda _ 1 \Omega _ {\text{complex}}(H) - \lambda _ 2 \mathcal{D} _ {\text{spec}}(H \Vert H _ 0) \Big\rbrace
$$

   其中 $\Omega _ {\text{complex}}(H)$ 度量脚手架控制流分支圈复杂度（Cyclomatic Complexity）与 Prompt 长度， $\mathcal{D} _ {\text{spec}}(H \Vert H _ 0)$ 为评论家模型（Critic）评估的任务特异度惩罚（惩罚硬编码领域词汇或特定格式技巧）。
2. **时间退火变异邻域预算（Temporally Annealed Modification Budget）**：
   定义第 $t$ 代允许修改的最大 AST 节点数/代码行数上界 $B(t)$ 随迭代轮次指数衰减：

$$
B(t) = \max\Big( B _ {\min}, \lfloor B _ 0 \cdot \gamma^t \rfloor \Big), \qquad \gamma \in (0, 1)
$$

   早期迭代（ $t$ 较小）允许大尺度重构智能体工作流拓扑（如引入反思循环或分层规划器），后期迭代则强制收敛为局部精细调优（Surgical Edits），防止后期破坏已收敛的核心架构。
3. **消融式结构修剪算子（Ablative Structural Pruner $\mathcal{P}$ ）**：
   对于候选补丁 $\Delta H = \bigcup _ {m=1}^M \delta h _ m$ （包含 $M$ 个模块化改动块），修剪器 $\mathcal{P}$ 执行留一消融检验（Leave-One-Out Ablation）或静态依赖裁剪，剔除所有边际增益 $\Delta \hat{J}(\delta h _ m) < \epsilon _ {\text{prune}}$ 的寄生代码段，仅合并最小必要改动核（Minimal Sufficient Core）。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* **OOD 跨基准泛化能力大幅跃升**：在涵盖代码生成（SWE-bench Verified）、复杂工具调用（ $\tau$ -bench）与多跳科学问答的跨领域评测中，未加正则化的朴素 RSI 在第 5 代后即出现严重的 ID-OOD 剪刀差（OOD 性能下降 `4.2%`），而 **RRSI** 持续稳定进化至第 12 代，在完全未见的 OOD 基准上取得 **`+7.8%` 至 `+12.5%`** 的净提升，同时将最终脚手架代码/提示词体积压缩了 **58%**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接指导我们 `ads-rsi`、`vla-loop` 与 `rsi-pareto-ledger` 的算子演化防膨胀纪律**：
  * 在我们的 RSI 自动化实验循环中，候选算子（Candidate Operator）在经历多轮突变后有时也会累加不必要的辅助超参或冗余分支。借鉴 RRSI 的 **Temporally Annealed Budget** 与 **Ablative Pruner $\mathcal{P}$ **，我们在每轮候选算子晋级（Promotion）前应强制执行一次“最小自由度消融检查（Minimal-DoF Ablation Gate）”：任何未能贡献 $>0.1\sigma$ 净增益的附加项一律回滚剥离，确保最终回迁至 Google3 生产库（`rsi-google3-backporter`）的算子保持极简闭式形态。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-27_ai_paper_notes.md`


---

### 2.4 [2026-09-26] ⚖️ *SelKV: Selective KV Cache Merging with Per-Token Merge-or-Drop and Attention Compensation*
> **聚焦领域**：KV Cache Compression · Softmax Denominator Compensation · Token Merging vs. Dropping  
> **arXiv**：[`arXiv:2607.16213`](https://arxiv.org/abs/2607.16213)

```
  待压缩历史 Token 序列 ──► [ 软余弦门控 (Soft Cosine Gate) 评估 Value 流形相似度 ]
                                       │
                        ┌──────────────┴──────────────┐
                        ▼                             ▼
             [ 高相似度: 加权合并 KV ]        [ 低相似度低重要度: 直接丢弃 ]
                        └──────────────┬──────────────┘
                                       ▼
               [ 注意力比率补偿 (Attention-Ratio Logit Compensation) ]
               消除 Softmax 分母塌陷 (Attention Sag) ──► 免训练高压缩保真
```

#### 🎯 背景与痛点剖析 (Problem Statement)
* **为什么免训练剪枝/合并会导致“注意力塌陷（Attention Sag）”**：当我们在推理期丢弃或合并大量历史 Token 后，参与 Softmax 计算的 Key 数量从 $N$ 锐减至 $M$ （ $M \ll N$ ）。若直接对剩余 $M$ 个 Token 的内积得分做标准 Softmax 归一化，原本被大量被删 Token 分担的分母配分函数质量消失，导致剩余 Token（或合并簇）的注意力权重被人为膨胀或失衡，深层表征模长发生剧烈偏移。

#### 💡 核心方法与数学推导 (Mathematical Formulations)
1. **软余弦门控决定“合并还是丢弃” (Soft Cosine Gate for Merge-or-Drop)**：
   - 给定被淘汰候选 Token $i$ 及其在保留集合中的最近邻锚点 $j^\star$ ，计算其 Value 向量的余弦相似度 $s _ i = \cos(v _ i, v _ {j^\star})$ ；
   - 通过平滑门控函数 $g(s _ i) = \sigma(\alpha (s _ i - \tau))$ 动态决定将其特征并入锚点 $j^\star$ （当 $s _ i > \tau$ ）还是直接丢弃（当 $s _ i \le \tau$ ）。
2. **注意力比率对数补偿 (Attention-Ratio Compensation)**：
   - 若锚点 $j^\star$ 吸收了等效计数为 $c _ {j^\star}$ 的历史 Token 质量，则在计算注意力 Logits 时显式加上对数质量补偿项：

$$
\tilde{a} _ {q, j^\star} = \frac{q^\top k _ {j^\star}}{\sqrt{d _ k}} + \ln(c _ {j^\star})
$$

   - 从而保证合并/剪枝前后的 Softmax 分母配分函数 $Z = \sum _ j \exp(\tilde{a} _ {q,j})$ 严格守恒！

#### 📊 关键实验与结论 (Experiments & Findings)
* 在 LongBench、RULER 及多轮数学推理基准上，免训练实现 **5x–10x KV Cache 压缩**，通过引入对数分母补偿项，消除了高压缩比下 80% 以上的精度退化。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发 (Relevance & Synergy with Our Works)
* **🎯 锚定代表作与在研主线**：
  * [Active Line: *Efficient Ads & VLA `HisTrim` (Hierarchical Progressive Token Drop + Softmax Denominator Mass Compensation)*]
  * [Paper #15: *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026)]
  * [Paper #16: *Transformer-Geometry* (EMNLP 2026, `arXiv:2609.15975`)]
* **🔬 机理对比与技术演进**：
  * **这篇工作独立验证了我们本周在 `Efficient Ads` 与 `axon` FlashAttention 推导中发现的核心机制！** 我们在 W39 周记（9/21）中明确指出：**当丢弃 Token 后，若直接把剩余保留 Token 的注意力权重重新归一化到 100%，会引发 $>1\times$ 的权重膨胀（分母偏差 / Denominator Bias）**，并推导出了 FlashAttention LSE（ $L _ i = m _ i + \ln \ell _ i$ ）下的 `$+\ln(M)$` 对数配分函数补偿与特殊 Token（Attention Sink）保留机制；
  * `SelKV` 在免训练 KV 合并场景下观测到了完全相同的现象（其命名为 *Attention Sag*），并用 $+\ln(c _ {j^\star})$ 予以修正。
* **💡 下一阶段研究（Next Research Directions）落地启发**：
  * 在正在撰写的 `Efficient Ads`（冲刺 NAACL）正文中，可将 `SelKV` 与我们的分母偏差修正共同作为**“Token 稀疏化中的 Softmax 配分函数守恒定律”**的双向佐证，进一步强化我们把“分母偏差 ↔ 位置编码与 Attention Sink”作为核心机制贡献（而非工程补丁）的理论厚度！

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-26_ai_paper_notes.md`


---

### 2.5 [2026-09-26] 🤖 *VLA-Pruner: Temporal-Aware Dual-Level Visual Token Pruning for Efficient Vision-Language-Action Inference*
> **聚焦领域**：Vision-Language-Action (VLA) · Embodied AI · Visual Token Pruning · Temporal Consistency  
> **arXiv**：[`arXiv:2511.16449`](https://arxiv.org/abs/2511.16449)

```
  连续控制帧视觉流 ──► [ 层级一 (Prefill): 跨模态指令-视觉语义重要度评估 ]
                                           │
                                           ▼
                       [ 层级二 (Decode): 时域指数平滑动作相关性追踪 S_t = λS_{t-1} + (1-λ)A_t ]
                                           │
                                           ▼
                       [ Combine-then-Filter 联合剪枝: 避免浅层误删关键操控锚点 ]
```

#### 🎯 背景与痛点剖析 (Problem Statement)
* **“语义显著性”与“动作控制必要性”的错位（Semantic-Action Gap）**：在机械臂精细操控任务（如 LIBERO）中，单帧静态视觉编码器认为显著的背景物体，未必是当前动作步（Action Chunk）夹爪需要接触的目标；反之，若在浅层仅凭静态视觉注意力盲目丢弃大量 Patch Token，会导致深层 Action Expert 丢失空间几何锚点，引发轨迹剧烈抖动。

#### 💡 核心方法与数学实现 (Mathematical Formulations)
1. **双层重要度融合准则 (Combine-then-Filter Dual-Level Criterion)**：
   - 同时提取语言指令在 Prefill 阶段对第 $i$ 个视觉 Token 的语义关注度 $I _ {\text{sem}}^{(i)}$ ，以及解码器生成动作 Token 时的交叉注意力得分 $I _ {\text{act}, t}^{(i)}$ ；
2. **跨时间步动作相关性平滑 (Temporal Action Smoothing)**：
   - 利用连续控制帧之间的时间连续性，引入历史动作注意力动量缓存：

$$
\tilde{I} _ {\text{act}, t}^{(i)} = \lambda \tilde{I} _ {\text{act}, t-1}^{(i)} + (1 - \lambda) I _ {\text{act}, t}^{(i)}
$$

   - 仅保留综合得分 $S _ t^{(i)} = I _ {\text{sem}}^{(i)} \cdot \tilde{I} _ {\text{act}, t}^{(i)}$ 最高的视觉 Token 子集。

#### 📊 关键实验与结论 (Experiments & Findings)
* 在 OpenVLA 与主流机器人操控基准（LIBERO-Spatial / Object / Goal / Long）上，剔除 **50%–75% 视觉 Token** 仍保持与全量 Token 持平的任务成功率，端到端控制频率显著提升。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发 (Relevance & Synergy with Our Works)
* **🎯 锚定代表作与在研主线**：
  * [Active Line: *Physical AI (`VLADrop` / `DTR` / `HiSTrim` Exclude-Self Value-Space Perp KV256)*]
  * [Paper #8: *Understanding and Harnessing Sparsity for Unified Multimodal Models* (TMLR 2026)]
  * [Paper #9: *Uncovering the Redundancy in Transformers via Layer Dropping* (TMLR 2025)]
* **🔬 机理对比与技术演进**：
  * 我们在 W38 周记（9/15–9/17）中深刻总结了两条核心定律：（1）**Layer 0（纯 ID Embedding、尚未经过上下文交互）绝不能直接做激进 Token Drop**，必须在表征充分上下文化之后再按浅层保守、深层激进的曲线压缩；（2）**VLA 的鲁棒性来源于三个时间尺度的“伤口愈合（Wound Healing）”纠错通道**（步内注意力、步间去噪、episode 内周期性视觉重锚）；
  * `VLA-Pruner` 的时域平滑动量 $\tilde{I} _ {\text{act}, t}$ 恰恰显式利用了我们指出的第三层“episode 内时域连续重锚”特性！
* **💡 下一阶段研究（Next Research Directions）落地启发**：
  * 在 `Physical AI` (MLSys) 论文中，可将 `VLA-Pruner` 纳入 Related Work 与对比讨论，突出我们 **全栈四维协同压缩（数据 DTR + Token `HiSTrim` + 层 `VLADrop/Loop` + 步数 `SnapFlow` 单步蒸馏）** 相比单一视觉 Token 剪枝在真实硬件延迟（Batch=1 访存带宽瓶颈）上的系统级代差优势。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-26_ai_paper_notes.md`


---

### 2.6 [2026-09-26] ✂️ *CliffCompaction: Cost-Efficient Compaction for Long-Horizon Coding Agents*
> **聚焦领域**：AI Coding Agents · Context Compaction · Test-Time Compute Scaling  
> **arXiv**：[`arXiv:2609.26779`](https://arxiv.org/abs/2609.26779)

* **核心痛点**：长程自主编程智能体（Coding Agents）在执行数十轮终端命令与编译调试后，上下文迅速触顶；传统的“LLM 摘要压缩（Rephrasing/Summarization）”不仅消耗大量额外 Token，还会抹除精确报错行号与变量名（引入幻觉与信息失真）。
* **具体做法**：提出 **CliffCompaction（断崖式无改写压实）**——严格禁止用模型改写历史轨迹，而是基于语法块与工具调用轮次边界，对过期中间输出执行确定性截断与丢弃，完整保留最近活跃窗口与关键锚点原文。
* **结论**：在 *KernelBench* 与 *Terminal-Bench* 上将测试期推理成本降低 **50%**，同时使轻量级模型（如 Kimi K2.6）在同等预算下的任务解决率反超未压缩的超大模型——这也与我们在 Stock 语料清洗中得出的**“能用确定性规则截断清洗，就绝不用 LLM 改写（防止隐蔽信息扭曲与泄漏）”**原则完全一致！

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-26_ai_paper_notes.md`


---

### 2.7 [2026-09-26] 🧩 *MoE-nD: Per-Layer Mixture-of-Experts Routing for Multi-Axis KV Cache Compression*
> **聚焦领域**：Multi-Axis KV Cache Compression · Per-Layer Routing · Heterogeneous Quantization  
> **arXiv**：[`arXiv:2604.17695`](https://arxiv.org/abs/2604.17695)

* **核心痛点**：Transformer 不同层对 Token 驱逐（Eviction）、低比特量化（Quantization）和低秩分解（Low-Rank Projection）的敏感度截然不同，全局采用单一压缩轴或统一压缩率必然在敏感层造成性能崩塌。
* **具体做法**：将多维 KV 压缩配置（如 $\left(k\text{-bits}, v\text{-bits}, \text{keep-ratio}\right)$ ）构建为离散专家池，利用轻量级逐层 MoE 路由器根据输入分布动态为每一层分配最优混合压缩算子，在满足全局显存上界约束的同时最大化输出保真度。
* **结论**：在长文本理解与代码生成任务上实现 ** $3\times\sim 20\times$ ** 极限显存压缩且几乎无损精度，验证了我们关于**“各层表征冗余度非均匀分布，压缩率应沿层自适应分配”**的核心判断。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-26_ai_paper_notes.md`


---

### 2.8 [2026-09-25] Fully Looped Transformer: Stabilizing Looped Models via Attention Injection and Residual Scaling

* **论文信息**：`arXiv:2605.18797` (2026-05)
* **核心关键词**：Fully Looped Transformer、Attention Injection、Anchor KV Grounding、Gradient Oscillation Prevention

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       Fully Looped Transformer with Parameter-Free Initial Attention Injection    |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Initial Pass (k=0): Input Embedding H^{(0)} ---> Compute Anchor (K^{(0)}, V^{(0)})|
|                                        |                                          |
|                                        v                                          |
|  Loop Iteration k = 1 .. K:                                                       |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Anchor-Injected Multi-Head Attention (零参数初始锚点键值注入)            |  |
|  |    \tilde{K}^{(k)} = (1 - \lambda_k) K^{(k)} + \lambda_k K^{(0)}            |  |
|  |    \tilde{V}^{(k)} = (1 - \lambda_k) V^{(k)} + \lambda_k V^{(0)}            |  |
|  |    Prevents representation drift & provides direct gradient highway to k=0  |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Unit-Sphere / Variance-Preserving Residual Update                        |  |
|  |    H^{(k+1)} = \text{Norm}\big( H^{(k)} + \frac{1}{\sqrt{K}} f_\theta(H^{(k)}, \tilde{K}^{(k)}, \tilde{V}^{(k)}) \big)|
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **深层循环中的“初始锚点遗忘”与反向传播雅可比谱半径失控**：当一个循环 Transformer 连续迭代 $K \ge 8$ 步时，第 $k$ 步的隐状态 $H^{(k)}$ 经过反复的非线性自注意力和 FFN 变换后，逐渐丢失了原始输入 Token 的精细词法锚点信息；同时在反向传播（BPTT）中，共享权重连乘 $\prod _ {k=1}^K \big(I + \frac{\partial f _ \theta}{\partial H^{(k)}}\big)$ 极易引发梯度震荡或消失。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **零参数初始注意力注入（Parameter-Free Attention Injection）**：
   缓存首轮（ $k=0$ ）计算得到的初始键值张量 $\left(K^{(0)}, V^{(0)}\right)$ 。在后续任意第 $k \in \lbrace1, \dots, K\rbrace$ 次循环中，通过凸组合或拼接将初始锚点注入当前步的注意力键值中：

$$
O^{(k)} = \text{Softmax}\left( \frac{Q^{(k)} \big( (1-\lambda) K^{(k)} + \lambda K^{(0)} \big)^\top}{\sqrt{d _ k}} \right) \Big( (1-\lambda) V^{(k)} + \lambda V^{(0)} \Big)
$$

   这一设计在计算图上为每一个循环步 $k$ 建立了一条直通初始表征 $\left(K^{(0)}, V^{(0)}\right)$ 的**一阶梯度短路高速通道（Direct Gradient Highway）**：

$$
\frac{\partial \mathcal{L}}{\partial H^{(0)}} = \frac{\partial \mathcal{L}}{\partial H^{(K)}} \prod _ {k=1}^K J _ k + \lambda \sum _ {k=1}^K \frac{\partial \mathcal{L}}{\partial O^{(k)}} \frac{\partial O^{(k)}}{\partial (K^{(0)}, V^{(0)})} \frac{\partial (K^{(0)}, V^{(0)})}{\partial H^{(0)}}
$$

   从而彻底消除了高循环步数下的梯度消失与震荡！

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在完全不增加任何额外参数（0 Extra Parameters）的条件下，Fully Looped Transformer 在 $K=8, 12$ 步循环预训练中完全消除了传统 Looped Transformer 的梯度尖峰（Gradient Spikes），验证集困惑度（PPL）降低 **`1.45`**，下游推理基准提升 **`+4.9%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接印证我们 `vla-loop` 定律（Lightweight Dropped-Span VLM Cross-KV Grounding）！**
  * 我们在 `vla-loop` 中发现，当动作专家循环迭代 $K=3,4$ 步时，若每一步都强绑回初始锚点 VLM Prefix KV（即此处的 $\left(K^{(0)}, V^{(0)}\right)$ ），即可完美阻止循环轨迹漂移！该论文的梯度短路公式为我们 `vla-loop` 的 Cross-KV Grounding 提供了极其漂亮的反向传播雅可比谱稳定性证明。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-25_ai_paper_notes.md`


---

### 2.9 [2026-09-25] On the Limits of Layer Pruning in Generative Reasoning LLMs

* **论文信息**：`arXiv:2602.01997` (2026-02)
* **核心关键词**：Limits of Layer Pruning、Sequential Circuit Depth、Multi-Step Arithmetic & Logic Degradation

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       Limits of Layer Pruning: Shallow Knowledge Lookup vs. Compositional Depth   |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Task Type A: Fact Retrieval / Single-Hop QA (MMLU, ARC-Easy, HellaSwag)          |
|    Parallel Associative Memory Circuits ---> Tolerates 30%-40% Layer Pruning!     |
|                                                                                   |
|  Task Type B: Multi-Step Compositional Reasoning (GSM8K, MATH, Symbolic Carry)    |
|    Requires Sequential Circuit Depth D_{\min} >= m \cdot d_{\text{hop}}           |
|    When remaining layers L_{\text{keep}} < D_{\min}:                              |
|    ===> Sharp Cliff Collapse (Even with LoRA recovery!)                           |
|                                        |                                          |
|                                        v                                          |
|  Solution: Convert Pruned Physical Layers into Shared Looped Iterations!          |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **层剪枝评估中的“多项选择幸存者偏差”**：大量层剪枝论文声称剪掉 30% 的层后在 HellaSwag、PIQA、Winogrande 甚至 MMLU 选择题上保留了 95% 性能。然而作者通过系统性压力测试发现，同一批被剪枝模型在自由生成的多步算术、代码执行追踪与符号逻辑推理任务上性能暴跌超过 **40%–65%**。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于计算复杂性理论的串行电路深度下界（TC $^0$ Sequential Depth Lower Bound）**：
   单个自注意力+FFN 层属于常数深度阈值电路类 $\text{TC}^0$ 。对于包含 $m$ 步嵌套函数复合 $g _ m \circ g _ {m-1} \circ \dots \circ g _ 1(x)$ （如多位数连加进位链或 $m$ 跳变量代换）的单个前向步推理，若没有外部 CoT Token 展开，模型内部必须至少具备 $L _ {\text{eff}} \ge m \cdot c _ {\text{hop}}$ 个串行非线性消息传递层。
   一旦物理层剪枝使剩余层数 $L _ {\text{keep}} = (1 - p) L < m \cdot c _ {\text{hop}}$ ，任何静态线性适配器或宽度扩容都无法弥补串行电路深度的缺失：

$$
\inf _ {\theta \in \Theta _ {L _ {\text{keep}}}} \mathbb{P}\big( f _ \theta(x) \neq g _ m \circ \dots \circ g _ 1(x) \big) \ge \frac{1}{2} - \exp\big(-\Omega(N^{\epsilon})\big) \quad \text{whenever } L _ {\text{keep}} < m \cdot c _ {\text{hop}}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 实验精确测定了 Llama-3-8B/70B 与 Qwen-2.5 在不同推理跳数 $m \in \lbrace2, 3, 4, 5\rbrace$ 下的临界剩余层数 $L _ {\text{crit}}(m)$ ，并证明当物理层被剪除后，**唯有通过测试期层循环（Layer Looping）恢复有效串行深度 $L _ {\text{eff}}$ **，才能跨过生成式推理的电路深度下界！

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **为我们为何从单纯的静态层剪枝（`vla-dtr` / *Layer Dropping* TMLR 2025）走向“层剪枝 + 循环精化协同（`vla-loop`）”提供了最坚实的复杂度理论支撑！**
  * 在撰写我们的论文导论（Introduction）与理论动机（Motivation）时，该定理可直接引用：静态深度剪枝省下了显存但突破了串行复合电路深度下界 $L _ {\text{crit}}$ ，而通过 1-Pass 主干 + LoRA 循环级联恰好以零额外主干显存恢复了所需的有效复合深度 $L _ {\text{eff}}$ ！

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-25_ai_paper_notes.md`


---

### 2.10 [2026-09-25] How Pruning Attention Layers Affects Interpretability, Faithfulness, and Confidence Calibration

* **论文信息**：`arXiv:2606.24970` (2026-06)
* **核心关键词**：Attention Layer Pruning、Confidence Calibration (ECE)、Faithfulness、Overconfident Hallucination

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|     Impact of Attention Layer Pruning on Faithfulness & Confidence Calibration    |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Pruned Mid-Deep Attention Layers ---> Loss of "Inhibitory / Suppression Heads"   |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Pathology Diagnosis: Logit Norm Inflation & Entropy Collapse                |  |
|  |    || h^{(L)}_{\text{pruned}} ||_2 > || h^{(L)}_{\text{orig}} ||_2          |  |
|  |    Expected Calibration Error (ECE) spikes by 2.5x - 4.0x!                  |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Fix: Inhibitory Subspace Projection + Variance-Matched Logit Rescaling      |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **剪枝后模型的“过度自信幻觉（Overconfident Hallucination）”**：作者发现，许多在中深层被视作“低贡献”而被剪除的注意力层，实际上包含了关键的**抑制头（Suppression / Negative Heads）**——它们的作用是在上下文证据不足或存在冲突时压低错误候选词的 Logit。剪除这些层后，虽然 Top-1 准确率仅轻微下降，但模型的预测分布熵急剧坍缩，期望校准误差（ECE）暴增 3 倍以上！

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **抑制头缺失导致的 Logit 方差膨胀模型**：
   在完整模型中，深层抑制注意力层的输出增量满足 $\langle \Delta h _ {\text{inhib}}^{(l)}, h^{(l-1)} \rangle < 0$ （即对残差流起负反馈阻尼作用）。剪除该层后，终端隐状态平行范数失控放大，导致输出词表概率 $p _ {\text{pruned}}(y \mid x)$ 的期望校准误差（ECE）激增：

$$
\text{ECE} = \sum _ {b=1}^B \frac{|I _ b|}{N} \Big| \text{acc}(I _ b) - \text{conf}(I _ b) \Big|
$$

2. **负反馈阻尼恢复与流形方差对齐**：
   在剪枝切口处引入沿残差主方向的阻尼收缩算子 $\tilde{h} = h - \beta \frac{\langle h, u _ {\text{inhib}} \rangle}{\Vert u _ {\text{inhib}}\Vert _ 2^2} u _ {\text{inhib}}$ 并校准输出层温度 $\tau^\star = \frac{\sigma(\text{logits} _ {\text{pruned}})}{\sigma(\text{logits} _ {\text{orig}})}$ 。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在事实问答（TruthfulQA、haluEval）与医疗/金融高风险推理任务上，该校准修复将深度剪枝模型的 **ECE 降低 68%**，并在基于置信度的拒绝采样（Selective Prediction）中恢复了 98% 的安全边界。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Transformer-Geometry* (`arXiv:2609.15975`, EMNLP 2026) 的“负平行分量（Negative Parallel Component）”发现完全吻合！**
  * 我们在 *Transformer-Geometry* 中明确观测到中深层部分模块具有 $\Delta h _ \parallel < 0$ 的径向阻尼效应；剪除它们而不做平行范数阻尼补偿，必然导致终端模长膨胀与置信度失真。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-25_ai_paper_notes.md`


---

### 2.11 [2026-09-25] SAC: Disaggregated KV Cache Architecture for Sparse Attention Serving over CXL

* **论文信息**：`arXiv:2604.18392` (2026-04)
* **核心关键词**：CXL 3.0 Memory Pooling、Disaggregated KV Cache、Sparse Attention Sub-Page Gather

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       SAC: CXL-Disaggregated KV Cache Architecture for Sparse Attention           |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  GPU Compute Nodes <--- CXL 3.0 Fabric ---> Shared CXL Memory Pool (TB-Scale KV)  |
|                                                       |                           |
|                                                       v                           |
|  +-----------------------------------------------------------------------------+  |
|  | Near-Memory Sparse Gather Engine on CXL Type-2/3 Controller                 |  |
|  |    Receives Top-k sparse token indices from GPU -> Packs only selected      |  |
|  |    cachelines into dense CXL flits -> 6.5x effective bandwidth amplification|  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **稀疏注意力在 PCIe/CXL 远端内存读取时的粒度放大（Granularity Amplification）**：当稀疏注意力仅需读取分散在不同物理页中的少量关键 Token 时，传统 DMA 以 4KB 页为单位搬运会导致高达 85% 的无效带宽浪费。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **CXL 控制器端近存稀疏聚集与头维度转置存储**：
   在 CXL 内存池侧按缓存行（64B Cacheline）对齐存储单头量化 KV 向量，由 CXL 控制器根据 GPU 下发的稀疏索引列表 $\mathcal{I} _ {\text{top-}k}$ 在远端完成紧密打包（Dense Packing）后再经 CXL.mem 链路回传：

$$
\text{BW} _ {\text{eff}} = \text{BW} _ {\text{CXL}} \cdot \frac{d _ {\text{head}} \cdot b _ {\text{quant}}}{\lceil d _ {\text{head}} \cdot b _ {\text{quant}} / 64\text{B} \rceil \cdot 64\text{B}} \approx 0.94 \cdot \text{BW} _ {\text{CXL}}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 TB 级长上下文并发推理中，SAC 将跨节点 KV 读取有效带宽利用率从 `15%` 提升至 **`94%`**，P99 尾延迟降低 **3.7x**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **为我们的 SelKV / OBCache 稀疏缓存算法在大规模分布式机架上的部署提供了硬件近存聚集蓝图**。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-25_ai_paper_notes.md`


---

### 2.12 [2026-09-24] LearnPruner: Two-Stage Differentiable Visual Token Pruning for Large Vision-Language Models

* **论文信息**：`arXiv:2604.23950` (2026-04)
* **核心关键词**：Two-Stage Visual Token Pruning、Differentiable Gumbel/Sigmoid Masking、Shallow Deduplication & Deep Grounding

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       LearnPruner: Two-Stage Differentiable Visual Token Pruning for LVLMs        |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Visual Patch Tokens V^{(0)} (N_v = 576)                                          |
|          |                                                                        |
|          v                                                                        |
|  +-----------------------------------------------------------------------------+  |
|  | Stage 1 (Shallow Layer l_1): Vision-Intrinsic Redundancy Pruning            |  |
|  |    Removes background & spatially homogeneous patches BEFORE cross-modal    |  |
|  |    stabilizes -> Retains N_1 tokens                                         |  |
|  +-----------------------------------------------------------------------------+  |
|          |                                                                        |
|          v                                                                        |
|  +-----------------------------------------------------------------------------+  |
|  | Stage 2 (Mid Layer l_2): Instruction-Grounded Cross-Modal Pruning           |  |
|  |    Prunes task-irrelevant objects using stabilized text-to-vision attention |  |
|  |    Differentiable Soft-to-Hard Attention Bias: A_{i,j} + \log m_j(\tau)     |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **单阶段过早剪枝的“跨模态盲视”与过晚剪枝的“算力浪费”**：若在极浅层（如第 2 层）就仅凭文本指令去剪除大量视觉 Token，此时文本与视觉表征尚未完成跨模态对齐，极易误删目标物体；而若等到第 16 层才剪枝，前 16 层已经消耗了超过 50% 的全量视觉 FLOPs。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **浅层视觉内生去重 + 中层指令对齐聚焦的两阶段架构**：
   在浅层 $l _ 1$ ，仅基于视觉自注意力与空间局部方差剔除纯背景冗余块（保留率 $\rho _ 1 \approx 50$ %）；在中层 $l _ 2$ ，利用已对齐的跨模态交互特征进一步筛选与指令强相关的核心块（保留率 $\rho _ 2 \approx 15$ %）。
2. **注意力对数掩码软硬退火（Differentiable Log-Mask Annealing）**：
   训练期将连续重要性得分 $s _ j \in (0, 1)$ 通过温度 $\tau$ 转化为软掩码 $m _ j(\tau) = \sigma\big((s _ j - \theta _ {\text{thr}})/\tau\big)$ ，并以对数偏置注入注意力矩阵：

$$
\tilde{A} _ {i, j} = \frac{m _ j(\tau) \exp(q _ i^\top k _ j / \sqrt{d _ k})}{\sum _ {r} m _ r(\tau) \exp(q _ i^\top k _ r / \sqrt{d _ k})}
$$

   随着 $\tau \to 0^+$ ， $m _ j(\tau) \to \lbrace0, 1\rbrace$ ，训练期软注意力平滑收敛至推理期的物理硬剔除，实现零训练-推理鸿沟。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **LLaVA-1.5/NeXT** 与 **Qwen2-VL** 上，LearnPruner 仅保留 **11.1%–16.7% 视觉 Token**，FLOPs 降低 **68%**，在 10 项多模态基准上的平均精度达到全 Token 模型的 **99.6%**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Sparsity for Unified Multimodal Models* (TMLR 2026) & *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) 的完美契合**：验证了根据表征层级演化阶段（浅层模态内去重 vs. 中层跨模态语义聚焦）分阶段设置不同剪枝准则的必要性。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-24_ai_paper_notes.md`


---

### 2.13 [2026-09-24] MixKV: Balancing Importance and Diversity for Modality-Specific KV Cache Compression

* **论文信息**：`arXiv:2510.20707` (2025/2026)
* **核心关键词**：Importance-Diversity Trade-off、Modality-Specific KV Compression、Cosine Repulsion Selection

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       MixKV: Balancing Importance and Diversity in Multimodal KV Compression      |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Visual KV Cache (High Spatial Redundancy) vs. Text KV Cache (High Info Density)  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Modality-Adaptive Submodular Selection Objective                            |  |
|  |    \max_{S: |S|=B} \sum_{i \in S} \text{Imp}(i) - \lambda_{\text{mod}} \sum_{i,j \in S} \cos(K_i, K_j)|
|  |    * Vision modality: High \lambda_{\text{vis}} avoids picking 50 tokens    |  |
|  |      from the same salient foreground patch                                 |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **纯重要性排序在视觉模态上的“局部高光扎堆陷阱”**：在多模态长上下文中，视觉特征具有极强的空间局部相关性。若仅按注意力得分 Top- $B$ 挑选视觉 KV，预算内的 $B$ 个槽位会被画面中心最显著物体的几十个高度相似的相邻图像块占满，而画面边缘的关键次要物体则被完全清空。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **模态自适应重要性-多样性边际增益准则（Modality-Adaptive Marginal Gain）**：
   在贪心或分块并行选择保留集 $S$ 时，第 $j$ 个候选 Token 的综合得分为其注意力重要性减去其与已选集合在 Key/Value 空间的最大余弦冗余度：

$$
\Phi(j \mid S) = s _ {\text{imp}}(j) - \lambda _ m \cdot \max _ {i \in S} \left( \frac{\langle K _ j, K _ i \rangle}{\Vert K _ j\Vert _ 2 \Vert K _ i\Vert _ 2} \right)
$$

   其中视觉模态的排斥权重 $\lambda _ {\text{vis}} > \lambda _ {\text{text}}$ ，根据各层模态内平均余弦相似度自动校准。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **MileBench**、**Video-MME** 与多图长上下文评测中，MixKV 在 **10% 极限缓存预算**下比 SnapKV 与 PyramidKV 平均提升 **`+5.3%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 `vla-dtr` 和 `Efficient Ads / HisTrim` 的正交子空间选择完全一致**：在多视角机器人相机或长用户历史序列中，通过 Gram-Schmidt 正交投影排斥共线项，正是最大化子空间体积（Determinantal Point Process）的快速实现。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-24_ai_paper_notes.md`


---

### 2.14 [2026-09-24] AEWM: Agent-Editing World Model with Inference-Time Action Judge and State Revision

* **论文信息**：`arXiv:2609.28416` (2026-09)
* **核心关键词**：Agent-Editing World Model、Inference-Time State Revision、Action Judge、Latent Trajectory Correction

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       AEWM: Agent-Editing World Model (Action Judge & Inference State Revision)   |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Agent State z_t ---> Propose Candidate Action a_t ---> World Model Predicts \hat{z}_{t+1}|
|                                                                |                  |
|                                                                v                  |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Action Judge J_\phi(z_t, a_t, \hat{z}_{t+1})                             |  |
|  |    Detects dead-ends, safety violations, or sub-goal regression BEFORE exec |  |
|  +-----------------------------------------------------------------------------+  |
|                                                                |                  |
|                                             If Judge Score < \tau_{\text{pass}}   |
|                                                                v                  |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Active State Revision Operator \mathcal{E}_\psi(z_t, \hat{z}_{t+1})      |  |
|  |    Edits internal memory/belief state z_t -> z_t^{\text{revised}} to prune  |  |
|  |    corrupted assumptions and resample clean action a_t^*                    |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **仅重采样动作无法清除已污染的内部记忆状态**：在长程 Web 操作或代码修复任务中，当智能体的内部信念/上下文记忆 $z _ t$ 已经混入了错误的假设时，单纯利用世界模型拒绝当前动作并从同一状态 $z _ t$ 重新采样，依然会反复生成同类的错误动作。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于反事实进度判别的内部状态编辑算子（Counterfactual State Revision）**：
   当世界模型预测下一状态 $\hat{z} _ {t+1} = f _ {\text{WM}}(z _ t, a _ t)$ 未能通过动作评判器 $J _ \phi(z _ t, a _ t, \hat{z} _ {t+1}) < \tau$ 时，触发状态编辑器 $\mathcal{E} _ \psi$ 直接在信念状态/工作记忆上施加反事实修正增量：

$$
z _ t^{\text{rev}} = z _ t + \mathcal{E} _ \psi\big( z _ t, a _ t, \hat{z} _ {t+1}, \nabla _ {z _ t} J _ \phi(z _ t, a _ t, \hat{z} _ {t+1}) \big)
$$

   随后基于修正后的干净状态 $z _ t^{\text{rev}}$ 重新生成可执行动作 $a _ t^\star \sim \pi _ \theta(\cdot \mid z _ t^{\text{rev}})$ 。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **VisualWebArena**、**OSWorld** 与长程具身任务上，AEWM 将不可逆错误操作率降低 **52%**，端到端任务成功率比无状态编辑的 Tree-of-Thoughts 高出 **`+10.8%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **对我们 `vla-loop` 动态循环早停与修正（Bridge-Readout Dynamic Halting）的启发**：在循环迭代中若检测到预测轨迹能量异常，可通过低秩正交校正算子直接修正潜状态而非盲目增加循环次数。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-24_ai_paper_notes.md`


---

### 2.15 [2026-09-24] Decision Representation Transitions in Pruning: Silent vs. Decisive Phases

* **论文信息**：`arXiv:2605.07271` (2026-05)
* **核心关键词**：Decision Representation Phase Transition、Silent vs. Decisive Layers、Linear Probe Separability、Pruning Collapse Boundary

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       Decision Representation Transitions: Silent vs. Decisive Layer Phases       |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Layer Index l:  1 --------> l^* - 1  |  l^* --------> l^* + \Delta  |  ... ---> L|
|                  [   Silent Phase   ] | [ Decisive Phase Transition ] | [Refinement]|
|                  Distributed Evidence | Abrupt jump in Logit Lens &   |           |
|                  Accumulation         | Linear Probe Separability     |           |
|                                                                                   |
|  Pruning Law: Pruning inside Silent/Refinement = Linear graceful degradation;     |
|               Pruning across Phase Transition [l^*, l^*+\Delta] = Total Collapse! |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **为何剪除同样数量的层，有时精度仅降 1%，有时却瞬间跌至随机猜测（0%）？** 传统层重要性指标缺乏对决策信息在深度方向如何涌现的相变刻画。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **决策表征相变点（Decisive Phase Transition Point $l^\star$ ）的形式化检测**：
   定义第 $l$ 层隐状态对最终输出决策类别 $Y$ 的互信息增益率（通过 Logit Lens 分布与最终层分布的对称 KL 二阶差分度量）：

$$
\Delta I _ {\text{dec}}(l) = D _ {\text{KL}}\big( P^{(L)}(Y \mid X) \Vert P^{(l-1)}(Y \mid X) \big) - D _ {\text{KL}}\big( P^{(L)}(Y \mid X) \Vert P^{(l)}(Y \mid X) \big)
$$

   实验揭示 $\Delta I _ {\text{dec}}(l)$ 并非随层深均匀分布，而是在窄区间 $[l^\star, l^\star + \Delta]$ 内呈现尖锐的脉冲式跃迁（将分散在多跳上下文中的隐式证据突然坍缩绑定为显式答案表征）。任何触碰该相变核区间的层剪枝都会切断证据绑定链条。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在多跳问答与算术推理任务中，避开相变区间 $[l^\star, l^\star+\Delta]$ 的相变感知剪枝在 **30% 剪枝率**下比传统余弦相似度剪枝提升 **`+18.5%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) 及 `vla-dtr` 的核心相变定律完全一致！**
  * 这篇论文从决策互信息跃迁角度再次印证了我们在 ICML 2026 和 `vla-dtr`（Phase-Transition Laws）中提出的黄金准则：**绝不能剪除负责跨模态特征绑定与相变跃迁的桥梁层（Bridge/Decisive Layers）**，而应将剪枝预算集中在静默累积层与末端微调层。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-24_ai_paper_notes.md`


---

### 2.16 [2026-09-23] StepKV: Step-Aware KV Cache Compression for Preserving Reasoning Continuity

* **论文信息**：`arXiv:2609.22158` (2026-09)
* **核心关键词**：Step-Aware KV Compression、Long-CoT Reasoning Continuity、Semantic Span Eviction、Discourse Boundary Detection

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       StepKV: Step-Aware KV Cache Compression for Long-CoT Reasoning Models       |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Generated CoT Stream ---> Boundary Detector (\n\n, "Wait,", equation delimiters) |
|                            Partitions tokens into Reasoning Steps {S_1, S_2..S_M} |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Step-Level Cohesive Saliency Scoring (推理步级内聚显著性打分)            |  |
|  |    U(S_m) = \frac{1}{|S_m|^\alpha} \sum_{j \in S_m} A_{\text{future} \to j} |  |
|  |             \cdot (1 + \gamma \cdot \mathbb{I}[\text{is\_milestone}(S_m)])  |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Whole-Step Retention or Summary Compression (整步保留或边界锚点折叠)     |  |
|  |    Never punch holes inside an active mathematical equation or logic step!  |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **逐 Token 驱逐在长思维链（Long-CoT）中的“公式穿孔效应（Formula Swiss-Cheese Effect）”**：在 DeepSeek-R1 或 Qwen-QwQ 等推理模型生成数万 Token 的推导过程中，H2O/SnapKV 等按单 Token 注意力打分驱逐的方法往往会保留某一步方程的等号和首尾变量，却把括号内的中间符号剪掉。这种“半句话残骸”留在 KV 缓存中会严重误导后续注意力回溯，导致模型陷入重复验算死循环。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **推理步边界切分与步内完整性约束**：
   将长思维链序列划分为语义内聚的推理步集合 $\mathcal{S} = \lbrace S _ 1, S _ 2, \dots, S _ M\rbrace$ （以换行符、逻辑连接词或公式块定界）。引入步级二值保留决策变量 $z _ m \in \lbrace0, 1\rbrace$ （而非 Token 级独立变量），将预算为 $B$ 的 KV 缓存淘汰问题形式化为带步长权重的 0-1 背包优化：

$$
\max _ {z \in \lbrace0, 1\rbrace^M} \sum _ {m=1}^M z _ m \cdot \mathcal{U} _ {\text{step}}(S _ m) \qquad \text{s.t.} \quad \sum _ {m=1}^M z _ m |S _ m| + \sum _ {m=1}^M (1 - z _ m) c _ {\text{anchor}} \le B
$$

   其中被淘汰的冗余探索步（如已推翻的“Wait, let me recalculate”死胡同分支， $z _ m=0$ ）仅保留其末尾 $c _ {\text{anchor}}=2$ 个结论边界 Token 作为消极记忆锚点，而保留的关键推导步（ $z _ m=1$ ）则完整保留其内部全部 Token。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **AIME 2025**、**MATH-500** 与 **GPQA-Diamond** 上，StepKV 在压缩 **65%–75% CoT KV 缓存** 的条件下，相比逐 Token 驱逐的 SnapKV / H2O 将推理准确率大幅提升 **`+9.4%` 至 `+15.2%`**，并缩短了 18% 的无效重复反思长度。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *EffiR* (ACL 2026) 及 `Efficient Ads / HisTrim` 的块级结构化剪枝高度一致**：
  * 在我们的用户行为序列压缩（HisTrim）与长程推理压缩（EffiR）中，同样发现按完整事件/完整推理子句（Event/Step-Level）进行内聚度打分与整块保留，远比破坏局部语法结构的零散 Token 剔除稳健得多。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-23_ai_paper_notes.md`


---

### 2.17 [2026-09-23] HetDPT: Rethinking Depth Pruning for Vision Transformers — A Heterogeneity-Aware Perspective

* **论文信息**：`arXiv:2607.03784` (2026-07)
* **核心关键词**：Heterogeneity-Aware Depth Pruning、Decoupled MHSA/FFN Pruning、Vision Transformers

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|      HetDPT: Heterogeneity-Aware Decoupled Sub-Layer Depth Pruning for ViTs       |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Standard Block l:  X ---> [MHSA^{(l)} (Spatial Mixing)] ---> [FFN^{(l)} (Channel)]|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Sub-Layer Functional Heterogeneity Profiling (子层异构功能解耦剖析)      |  |
|  |    Deep MHSA layers exhibit high spatial attention map redundancy;          |  |
|  |    Shallow/Mid FFN layers exhibit higher channel transformation redundancy  |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Independent Sub-Layer Pruning under Latency Constraint                   |  |
|  |    Can prune MHSA^{(l)} while keeping FFN^{(l)} (or vice versa) with zero   |  |
|  |    dimension mismatch via residual identity bypass                          |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **整块绑定剪枝（Coupled Block Pruning）忽略了注意力与 FFN 的深度角色错位**：传统深度剪枝总是将第 $l$ 层的 $\left( \text{MHSA}^{(l)}, \text{FFN}^{(l)} \right)$ 捆绑在一起同时保留或同时删除。然而在视觉与多模态编码器中，深层的空间跨 Token 交互（MHSA）早已收敛（注意力图趋于恒等或全局平均），但深层的逐 Token 特征非线性映射（FFN）仍在执行关键的语义分类投影。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **MHSA 与 FFN 异构解耦敏感度建模**：
   分别为每个子层引入独立的二值门控 $\left(m _ {\text{attn}}^{(l)}, m _ {\text{ffn}}^{(l)}\right) \in \lbrace0, 1\rbrace^2$ ：

$$
h _ {\text{mid}}^{(l)} = h^{(l-1)} + m _ {\text{attn}}^{(l)} \cdot \text{MHSA}^{(l)}\big(\text{LN} _ 1(h^{(l-1)})\big)
$$

$$
h^{(l)} = h _ {\text{mid}}^{(l)} + m _ {\text{ffn}}^{(l)} \cdot \text{FFN}^{(l)}\big(\text{LN} _ 2(h _ {\text{mid}}^{(l)})\big)
$$

   利用泰勒二阶敏感度联合硬件实测延迟表 $\tau _ {\text{attn}}, \tau _ {\text{ffn}}$ 求解整数线性规划（ILP）：

$$
\min _ {\lbrace m _ {\text{attn}}^{(l)}, m _ {\text{ffn}}^{(l)}\rbrace} \sum _ {l=1}^L \Big( (1 - m _ {\text{attn}}^{(l)}) \Omega _ {\text{attn}}^{(l)} + (1 - m _ {\text{ffn}}^{(l)}) \Omega _ {\text{ffn}}^{(l)} \Big) \quad \text{s.t.} \quad \sum _ {l=1}^L \big( m _ {\text{attn}}^{(l)} \tau _ {\text{attn}} + m _ {\text{ffn}}^{(l)} \tau _ {\text{ffn}} \big) \le T _ {\text{budget}}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **DeiT**、**Swin** 与 **CLIP-ViT-L/14** 上，HetDPT 在相同 **1.5x–1.8x 硬件实测加速比** 下，比整块深度剪枝提升了 **`+1.9%` 至 `+3.2%`** 的 ImageNet 与多模态下游准确率。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Layer Dropping* (TMLR 2025) & `vla-dtr` 的子层解耦路由完美呼应**：在 VLA 视觉主干与动作专家的深度剪枝中，深层 Cross-Attention 往往比 FFN 更早饱和，采用解耦子层跳过可进一步压榨 15% 延迟。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#depth-and-layer-pruning` (Heterogeneous MHSA/FFN Depth Pruning)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-23_ai_paper_notes.md`


---

### 2.18 [2026-09-23] MELT: Memory-Efficient Looped Transformer — Decoupling Compute from Memory

* **论文信息**：`arXiv:2605.07721` (2026-05)
* **核心关键词**：Memory-Efficient Looped Transformer、Shared Cross-Loop KV Cache、Compute-Memory Decoupling

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|         MELT: Memory-Efficient Looped Transformer (Shared KV Cache Pool)          |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Standard Looped Transformer (K Loops):                                           |
|    Stores separate KV^{(1)}, KV^{(2)}, ..., KV^{(K)} -> K x Memory Footprint!     |
|                                                                                   |
|  MELT Architecture:                                                               |
|    Single Physical KV Cache Buffer \mathcal{C}_{KV} in HBM                        |
|    Loop k=1..K reads & refines \mathcal{C}_{KV} via gated EMA update:             |
|    \mathcal{C}_{KV}^{(k)} = (1 - \alpha_k) \mathcal{C}_{KV}^{(k-1)} + \alpha_k \text{Proj}_{KV}(h^{(k)})|
|    ===> O(K) Compute Depth with strictly O(1) KV Cache Memory!                    |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **循环 Transformer 的“隐性 KV 缓存倍增陷阱”**：虽然 Looped Transformer 通过复用层权重将模型参数显存压缩为 $1/K$ ，但在自回归生成时，如果第 $t$ 个 Token 在第 $k$ 次循环时需要 Attend 到前序 Token $1 \dots t-1$ 在第 $k$ 次循环时的键值状态，就必须为全部 $K$ 次循环分别缓存独立的 $K^{(k)}, V^{(k)}$ ，导致 KV 缓存显存依然随循环步数 $K$ 线性增长！

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **跨循环指数移动平均共享 KV 缓存（Cross-Loop EMA Shared KV Cache）**：
   对于历史已生成的上下文位置 $1 \dots t-1$ ，仅在显存中维护唯一一份最终收敛态的键值缓存 $\left(K _ {\text{shared}}, V _ {\text{shared}}\right)$ （即每个历史 Token 完成第 $K$ 次循环后的稳态 KV）。在当前位置 $t$ 执行第 $k \in \lbrace1, \dots, K\rbrace$ 次内部循环时，当前查询 $q _ t^{(k)}$ 统一读取历史稳态缓存 $K _ {\text{shared}, 1:t-1}$ 并结合当前步自键值 $\left(k _ t^{(k)}, v _ t^{(k)}\right)$ ：

$$
\text{Attn} _ t^{(k)} = \text{Softmax}\left( \frac{q _ t^{(k)} \big[ K _ {\text{shared}, 1:t-1}; k _ t^{(k)} \big]^\top}{\sqrt{d _ k}} \right) \begin{bmatrix} V _ {\text{shared}, 1:t-1} \cr v _ t^{(k)} \end{bmatrix}
$$

   当第 $t$ 个 Token 完成全部 $K$ 步循环后，仅将其终端稳态 $\left(k _ t^{(K)}, v _ t^{(K)}\right)$ 写入共享缓存池！

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 $K=4$ 与 $K=8$ 循环配置下，MELT 将长文本解码时的 **KV 缓存显存与带宽读取量直接削减 $75\text{ pct}–87.5$ %（严格降至 $1/K$ ）**，同时在语言建模与数学推理上与保存全套每步 KV 的基线性能完全持平（差异 `<0.2%`）。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接印证我们 `vla-loop` 定律 v19/v20（1-Pass Backbone + Multi-Step LoRA-Only Cascade & Shared KV Grounding）**：在 Looped VLA 中，历史观测与前缀只需保存唯一一份稳态 KV 缓存，多步循环仅更新当前动作查询状态，从而将循环推理的内存带宽开销降到最低。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-23_ai_paper_notes.md`


---

### 2.19 [2026-09-23] D-Cut: Adaptive Verification Depth Pruning for Batched Speculative Decoding

* **论文信息**：`arXiv:2607.14647` (2026-07)
* **核心关键词**：Speculative Decoding、Verification Depth Pruning、Cross-Request Budget Allocation

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       D-Cut: Adaptive Verification Depth Pruning for Batched Speculative Decoding |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Batched Draft Trees {T_1, ..., T_B} with Draft Confidence Scores {c_1, ..., c_B} |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Early-Layer Margin Verification (浅层置信度提前决断)                        |  |
|  |    At Intermediate Layer L_{\text{cut}} < L:                                |  |
|  |    If early logit margin \Delta z^{(L_{\text{cut}})} >> \tau_accept or << -\tau_reject:|
|  |    Drop verified/rejected draft tokens from remaining layers L_{\text{cut}}+1..L|
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **批量投机解码验证阶段的深层算力浪费**：在大 Batch 投机解码中，目标大模型需要同时并行验证每个请求的 $K$ 个草稿 Token。实际上，超过 70% 的简单正确草稿或明显错误的草稿在目标模型的前 60% 层就已经毫无悬念地分出胜负，继续让它们跑完后 40% 层纯属浪费。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于中间层 Logit 间隔的动态截断准则**：
   在中间探测层 $l _ {\text{probe}}$ ，通过轻量早期退出投影计算草稿 Token $y _ i$ 的对数概率边际 $\Delta _ {i}^{(l)} = \hat{\ell}^{(l)}(y _ i) - \max _ {v \neq y _ i} \hat{\ell}^{(l)}(v)$ 。当 $|\Delta _ {i}^{(l)}| > \gamma _ l$ 时，立即锁定接受/拒绝决策，并将该草稿及其后续依赖子树从第 $l+1 \dots L$ 层的批次张量中动态压缩移除。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 Batch Size = 16–64 的生产级投机解码服务中，D-Cut 将验证阶段算力开销削减 **38%**，端到端吞吐在 EAGLE-2 基线上进一步提升 **1.42x**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Capacity-Aware Inference* (ICLR 2026) & *Layer Dropping* (TMLR 2025) 直接协同**：在多步推理或投机验证中引入中间层间隔早退门控，可显著提升高并发批次下的有效吞吐。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-23_ai_paper_notes.md`


---

### 2.20 [2026-09-22] SnapFlow: One-Step Action Generation for Flow-Matching VLAs via Progressive Self-Distillation

* **论文信息**：`arXiv:2604.05656` (2026-04)
* **核心关键词**：Flow-Matching VLA、1-NFE Action Generation、Progressive Self-Distillation、Chord Velocity Matching

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|      SnapFlow: 1-NFE Action Generation for Flow-Matching VLAs via Self-Distill    |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  VLM Prefix KV Cache (Visual + Language) + Action Noise A_0 ~ N(0, I)             |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Two-Step Euler Teacher Chord Construction (两步欧拉教师割线目标构造)     |  |
|  |    a_{t + \Delta t} = a_t + \Delta t \cdot v_{\theta^-}(a_t, t, \Delta t)   |  |
|  |    a_{t + 2\Delta t} = a_{t+\Delta t} + \Delta t \cdot v_{\theta^-}(a_{t+\Delta t}, t+\Delta t, \Delta t)|
|  |    Target Chord Velocity: \bar{u}_{\text{chord}} = \frac{a_{t+2\Delta t} - a_t}{2\Delta t}|
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Progressive Halving Schedule: N = 16 -> 8 -> 4 -> 2 -> 1 NFE             |  |
|  |    Student predicts single-step jump: \hat{A}_1 = A_0 + v_\theta(A_0, 0, 1) |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **多步 ODE 动作去噪拖慢具身实时控制频率**：以 $\pi _ 0$ 、 $\pi _ {0.5}$ 与 GR00T 为代表的现代视觉语言动作模型（VLAs）普遍采用条件流匹配（Conditional Flow Matching）动作专家，在推理时需对动作块（Action Chunk $A \in \mathbb{R}^{H \times d _ a}$ ）执行 $N=10$ 步欧拉积分。尽管动作专家本身参数量较小（如 300M），但 10 次串行交叉注意力与 FFN 前向传播占用了超过 65% 的端到端推理延迟。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **步长条件化割线速度场自蒸馏（Step-Conditioned Chord Velocity Self-Distillation）**：
   扩展动作专家网络输入为 $\left(a _ t, t, \delta\right)$ ，其中 $t \in [0, 1)$ 为当前流时刻， $\delta \in \lbrace2^{-k}\rbrace$ 为目标积分跨度（Step Size）。当跨度从 $\delta$ 倍增至 $2\delta$ 时，利用指数移动平均（EMA）目标网络 $\theta^-$ 执行两次半步积分生成割线目标速度（Chord Velocity）：

$$
\tilde{a} _ {t+\delta} = a _ t + \delta \cdot v _ {\theta^-}(a _ t, t, \delta \mid C _ {\text{VLM}})
$$

$$
u _ {\text{chord}}(a _ t, t, 2\delta) = \frac{1}{2} v _ {\theta^-}(a _ t, t, \delta \mid C _ {\text{VLM}}) + \frac{1}{2} v _ {\theta^-}(\tilde{a} _ {t+\delta}, t+\delta, \delta \mid C _ {\text{VLM}})
$$

   最小化单步跨度预测与双步合成割线之间的 Huber/L2 损失：

$$
\mathcal{L} _ {\text{SnapFlow}}(\theta) = \mathbb{E} _ {t, \delta, a _ 0} \Big[ \big\Vert v _ \theta(a _ t, t, 2\delta \mid C _ {\text{VLM}}) - \text{sg}\big(u _ {\text{chord}}(a _ t, t, 2\delta)\big) \big\Vert _ 2^2 \Big]
$$

2. **推理期零迭代一步生成（1-NFE Inference）**：
   当 $\delta = 1, t = 0$ 时，只需单次前向传播即可直接输出完整动作序列 $\hat{a} _ 1 = a _ 0 + v _ \theta(a _ 0, 0, 1 \mid C _ {\text{VLM}})$ 。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **LIBERO**（Spatial / Object / Goal / Long）与真实机械臂双臂操作基准上，SnapFlow 将动作专家推理步数从 10 NFE 压缩至 **1 NFE**，动作生成阶段延迟降低 **8.4x**，端到端控制频率提升 **2.6x**，同时保持了原始 10 步模型 **98.5%** 以上的成功率。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **正是我们 `vla-distillation` 技能库的核心基石之一（定律 G16–G21 & G27 v3）！**
  * 我们在 `vla-distillation` 中已经系统证明：单纯的 SnapFlow 1-NFE 在高曲率接触任务（如 LIBERO-10 长程插拔）中若不配合 **Perp-Directional Decomposition（G20 正交-平行速度场解耦）**、**MeanFlow + IMM + SFP 联合目标（G21）** 以及 **Stage-2 Cumulative Rank-128 Weight Folding（G27 v3）**，会出现约 1.5%–2.5% 的末端精度折损；将 SnapFlow 的渐进弦长目标与我们的四支柱 Data-RSI 协同设计结合，即可在零推理分支开销下实现超越 10-NFE 教师的无损 1-NFE/3-NFE 闭环控制。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-22_ai_paper_notes.md`


---

### 2.21 [2026-09-22] LoRP: Locality-Aware Redundancy Pruning for LLM Depth Compression

* **论文信息**：`arXiv:2605.27786` (2026-05)
* **核心关键词**：Locality-Aware Depth Pruning、Manifold Neighborhood Preservation、k-NN Graph Overlap、One-Shot Layer Pruning

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|          LoRP: Locality-Aware Redundancy Pruning for LLM Depth Compression        |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Token Representations before & after Layer l: H^{(l-1)}, H^{(l)} \in R^{N x d}   |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Local k-NN Manifold Graph Construction (局部流形邻域图构建)              |  |
|  |    For each token i, find k-nearest neighbors \mathcal{N}_k^{(l)}(i)        |  |
|  |    under cosine/geodesic distance                                           |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Locality Preservation Score (局部邻域拓扑保持率打分)                     |  |
|  |    \mathcal{S}_{\text{loc}}(l) = \frac{1}{N} \sum_{i=1}^N \frac{|\mathcal{N}_k^{(l-1)}(i) \cap \mathcal{N}_k^{(l)}(i)|}{k}|
|  |    High \mathcal{S}_{\text{loc}}(l) => Layer l does not reorganize semantics|  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **全局余弦相似度（Global Cosine Similarity）受制于各向异性均值偏移**：ShortGPT 等传统方法通过单点输入输出的余弦相似度 $\cos(h _ i^{(l-1)}, h _ i^{(l)})$ 判断层冗余度。然而在深层 Transformer 中，所有 Token 都共享一个巨大的共同方向（Common Mean Direction），导致即便某层对 Token 之间的相对局部语义拓扑进行了剧烈重排，其单点全局余弦相似度依然高达 `0.95` 以上，引发误判。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于核对齐与 $k$ -近邻重叠的局部几何冗余度（Neighborhood Locality Redundancy）**：
   记第 $l$ 层在小批量样本 $N$ 个 Token 上的局部亲和矩阵为 $K _ {i,j}^{(l)} = \exp\left(-\frac{\Vert h _ i^{(l)} - h _ j^{(l)}\Vert _ 2^2}{2\sigma _ l^2}\right)$ 。定义第 $l$ 层的局部流形冗余度为相邻两层局部邻域分布的对称 KL 散度倒数（或 $k$ -NN 交并比）：

$$
\mathcal{R} _ {\text{LoRP}}(l) = \frac{1}{N} \sum _ {i=1}^N \left( \frac{|\mathcal{N} _ k(h _ i^{(l-1)}) \cap \mathcal{N} _ k(h _ i^{(l)})|}{k} \right) \cdot \exp\Big( - D _ {\text{JS}}\big( P _ i^{(l-1)} \Vert P _ i^{(l)} \big) \Big)
$$

   若 $\mathcal{R} _ {\text{LoRP}}(l) \to 1$ ，说明第 $l$ 层既未改变样本间的局部聚类关系，也未分离混淆语义簇，可安全移除。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **Llama-2/3** 与 **Mistral-7B** 的 25% 免训练层剪枝上，LoRP 在 MMLU 与 BBH 复杂推理基准上比全局余弦打分（ShortGPT）提升 **`+4.3%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接验证了我们 *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) 的核心论断**：层剪枝的关键不在于单点向量的绝对位移，而在于该层是否触发了表示层级（Representation Hierarchy）的局部邻域拓扑相变！

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#depth-and-layer-pruning` (Manifold Locality-Preserving Layer Pruning)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-22_ai_paper_notes.md`


---

### 2.22 [2026-09-22] LightKV: Make Your LVLM KV Cache More Lightweight

* **论文信息**：`arXiv:2605.00789` (2026-05)
* **核心关键词**：LVLM KV Cache Compression、Cross-Modality Message Passing、Prompt-Guided Visual Aggregation

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|            LightKV: Prompt-Guided Cross-Modality Visual KV Aggregation            |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Visual Tokens V_{1:N_v} + Text Instruction Tokens T_{1:N_t}                      |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Cross-Modality Message Passing Score (文本指令引导的视觉重要性传递)      |  |
|  |    s_i = \frac{1}{N_t} \sum_{j \in \text{Text}} A_{j \to i}^{\text{cross}}  |  |
|  |    Partition V into Anchor Set \mathcal{A} (Top-K) & Redundant Set \mathcal{R}|
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Soft Bipartite KV Aggregation (二分图软聚合而非硬丢弃)                   |  |
|  |    \tilde{K}_a = K_a + \sum_{r \in \mathcal{R}} W_{a,r} K_r,                |  |
|  |    \tilde{V}_a = V_a + \sum_{r \in \mathcal{R}} W_{a,r} V_r                 |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **硬丢弃（Hard Eviction）导致的背景空间上下文丢失**：高分辨率多模态模型（LVLM）单张图产生 576–2,304 个视觉 Token。直接硬丢弃低注意力视觉 Token 会抹除背景空间相对位置与全局计数信息（例如数物体个数任务）。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **指令引导的二分图 KV 软合并（Prompt-Guided Bipartite KV Merging）**：
   利用文本指令 Token 对视觉 Token 的跨模态注意力选出锚点集合 $\mathcal{A}$ 与待合并集合 $\mathcal{R}$ 。对于每个被淘汰的视觉 Token $r \in \mathcal{R}$ ，计算其与锚点 $a \in \mathcal{A}$ 在 Key 空间的余弦相似度分布 $W _ {a,r} = \text{Softmax} _ a(\beta \cos(K _ a, K _ r))$ ，并执行注意力守恒的加权合并：

$$
\tilde{K} _ a = \frac{\alpha _ a K _ a + \sum _ {r \in \mathcal{R}} \alpha _ r W _ {a,r} K _ r}{\alpha _ a + \sum _ {r \in \mathcal{R}} \alpha _ r W _ {a,r}}, \qquad \tilde{V} _ a = \frac{\alpha _ a V _ a + \sum _ {r \in \mathcal{R}} \alpha _ r W _ {a,r} V _ r}{\alpha _ a + \sum _ {r \in \mathcal{R}} \alpha _ r W _ {a,r}}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **LLaVA-1.6-34B** 与 **InternVL-2** 上将视觉 KV 缓存直接压缩 **50%–75%**，在 TextVQA、DocVQA 与计数基准上实现 **99.4%** 的原始性能保持率。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 `vla-dtr` 及 *Sparsity for Unified Multimodal Models* (TMLR 2026) 的结合**：在合并非核心视觉 Token 时，仅合并与锚点平行的背景分量，而将正交运动边缘特征显式保留为独立锚点。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-22_ai_paper_notes.md`


---

### 2.23 [2026-09-22] SPIN: Unifying Sparse Attention with Hierarchical Memory for Scalable Long-Context LLM Serving

* **论文信息**：`arXiv:2604.26837` (2026-04)
* **核心关键词**：Sparse Attention Serving、Hierarchical GPU-CPU Memory、Asynchronous Layer-Ahead Prefetching

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       SPIN: Unifying Sparse Attention with Hierarchical Memory Serving            |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  GPU HBM: [Compact Page Indices + Hot Anchor KV Cache (10%)]                      |
|  CPU DRAM: [Full Cold KV Cache Pool (100%)]                                       |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Layer l-1 Hidden State Speculative Index Prediction                         |  |
|  |    Predict Top-K sparse pages needed by Layer l BEFORE Layer l starts       |  |
|  |    Overlap PCIe/NVLink DMA prefetch of missing cold pages with Layer l-1 FFN|  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **动态稀疏注意力的 PCIe 按需拉取延迟陷阱**：若将全量 KV 缓存卸载至 CPU 内存并在每层动态选出 Top- $k$ 页面后才通过 PCIe 搬运回 GPU，PCIe 传输延迟将远超稀疏注意力节省的计算时间。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **跨层隐状态余弦惯性预取（Cross-Layer Speculative Page Prefetching）**：
   利用相邻层查询向量高度相似的几何惯性（ $\cos(Q^{(l-1)}, Q^{(l)}) > 0.9$ ），在第 $l-1$ 层计算注意力的同时，使用轻量级页中心内积 $\hat{s} _ p^{(l)} = Q^{(l-1)} \bar{K} _ p^{(l)\top}$ 提前预测第 $l$ 层所需的冷页集合 $\mathcal{P} _ {\text{miss}}^{(l)}$ ，实现计算与 PCIe DMA 搬运的完美流水线掩盖：

$$
T _ {\text{step}}^{(l)} = \max\Big( T _ {\text{FFN}}^{(l-1)} + T _ {\text{QKV}}^{(l)}, \frac{|\mathcal{P} _ {\text{miss}}^{(l)}| \cdot B _ {\text{page}}}{\text{BW} _ {\text{PCIe}}} \Big)
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在单台 8 卡服务器上支持 **1M–2M 上下文长度** 并发推理，相比纯 CPU Offloading（Infinite-LLM）实现 **4.8x** 吞吐提升，且恢复 99.7% 全量注意力精度。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Transformer-Geometry* (EMNLP 2026) 的层间方向平稳性定理天然契合**：正是因为深层残差流中平行分量占主导、层间角度旋转平缓，才保证了跨层提前 1–2 层预取稀疏 KV 页的高命中率！

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-22_ai_paper_notes.md`


---

### 2.24 [2026-09-21] RotateK: Rotation-Aligned Key Channel Pruning for Vision-Language Models

* **论文信息**：`arXiv:2605.19218` (2026-05)
* **核心关键词**：Key Channel Pruning、Orthogonal Rotation Alignment、Vision-Language Models (VLMs)、Head-Dimension Compression

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|       RotateK: Rotation-Aligned Key Channel Pruning for Vision-Language Models    |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Attention Score Invariance under Orthogonal Rotation R \in O(d_k):               |
|    Q K^\top = (Q R)(K R)^\top   where R^\top R = I_{d_k}                          |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Cross-Modal Key-Query Co-Energy SVD (跨模态查询-键联合能量奇异值对齐)    |  |
|  |    Compute covariance C_K = \mathbb{E}[K_{\text{vis}}^\top K_{\text{vis}}]  |  |
|  |    Eigendecompose C_K = R \Lambda R^\top ---> Fold R into W_Q, W_K offline  |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Tail Channel Truncation (尾部低能量通道截断: 兼容 RoPE 2x2 块旋转)       |  |
|  |    Retain top-r channels (r = 0.4 d_k) -> 60% Key Cache & GEMM Reduction    |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **原始坐标轴下的通道能量弥散**：在多模态大模型（VLM）中，除序列长度方向（Token 维度）冗余外，注意力头内部的特征维度 $d _ k$ （如 $d _ k=128$ ）在视觉特征空间中实际上具有极低的本征秩。然而，在原始训练得到的正交基下，信号能量均匀弥散在全部 128 个通道上，直接按坐标轴剪除任何通道都会造成较大的内积误差 $\Vert Q K^\top - \tilde{Q} \tilde{K}^\top\Vert _ F$ 。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **RoPE 兼容的分块正交旋转能量集中（RoPE-Compatible Block-Orthogonal Rotation）**：
   由于旋转位置编码（RoPE）以二维子平面 $\left(2i, 2i+1\right)$ 为单位作用： $R _ \Theta(m) = \text{diag}(R _ {\theta _ 1}^{(m)}, \dots, R _ {\theta _ {d _ k/2}}^{(m)})$ ，为保持与 RoPE 的可交换性，RotateK 将 $d _ k/2$ 个二维频率对按预期内积能量贡献 $\mathcal{E} _ i = \mathbb{E}\big[ \Vert q _ {[2i:2i+1]} \Vert _ 2^2 \cdot \Vert k _ {[2i:2i+1]} \Vert _ 2^2 \big]$ 进行重排，并在每个同频子空间内执行正交主轴对齐 $U _ i \in O(2)$ ：

$$
\tilde{W} _ Q = W _ Q U _ {\text{rot}}, \qquad \tilde{W} _ K = W _ K U _ {\text{rot}}
$$

2. **误差上界最小化通道截断**：
   保留能量最高的前 $r$ 个通道子块，此时注意力 logit 截断误差满足紧上界：

$$
\mathbb{E}\big[ | q^\top k - \tilde{q} _ {1:r}^\top \tilde{k} _ {1:r} |^2 \big] \le \sum _ {i = r/2 + 1}^{d _ k/2} \lambda _ i(C _ Q) \lambda _ i(C _ K)
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **LLaVA-NeXT**、**Qwen2-VL-7B** 与 **InternVL-2** 上，RotateK 剪除 **50%–60% 的 Key 通道**而无需微调，且与视觉 Token 剪枝（如 FastV / VLA-Pruner）**100% 正交兼容**，联合实现 **4.2x** 注意力加速且 VQA 精度损失 `<0.5%`。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 `MerA` SVD 初始化及 *Sparsity for Unified Multimodal Models* (TMLR 2026) 的正交协同**：
  * RotateK 在特征通道维度 $d _ k$ 上的正交旋转浓缩与我们在 Token 维度 $N _ {\text{vis}}$ 上的剪枝构成了完整的二维矩阵联合低秩逼近（Row + Column Dual Sparsity），可直接嵌入 `vla-distillation` 的视觉前缀压缩器中。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-21_ai_paper_notes.md`


---

### 2.25 [2026-09-21] Token Sparse Attention: Efficient Long-Context Inference with Interleaved Token Selection

* **论文信息**：`arXiv:2602.03216` (2026-02)
* **核心关键词**：Token Sparse Attention、Interleaved Compress-Decompress、Reversible Token Selection、Dense Kernel Compatibility

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|     Token Sparse Attention (TSA): Interleaved Reversible Token Sparsification     |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Layer l Input Hidden States H^{(l)} \in R^{L x d}                                |
|          |                                                                        |
|          +---> [Select Top-M Active Tokens I_l] ---> Gather Q_sub, K_sub, V_sub   |
|          |                                                   |                    |
|          |                                                   v                    |
|          |                                      Dense FlashAttention (M x M)      |
|          |                                                   |                    |
|          +---> [Scatter-Add Back to Full Length L] <---------+                    |
|          |                                                                        |
|          v                                                                        |
|  Layer l+1 Input H^{(l+1)} \in R^{L x d} (Previously skipped tokens can re-awake!)|
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **永久性 Token 丢弃（Permanent Token Dropping）的不可逆信息损失**：传统早退或逐层漏斗式 Token 剪枝（如 FastV、PyramidDrop）一旦在第 $l$ 层将某个 Token 丢弃，该 Token 在后续第 $l+1 \dots L$ 层中便永远消失。然而，在多跳推理或长文档问答中，浅层看似不相关的背景段落往往需要在深层推理出中间结论后才被重新检索激活。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **层内 Gather-Attention-Scatter 可逆稀疏算子**：
   在第 $l$ 层，轻量路由器根据当前隐状态打分选出活跃下标集 $\mathcal{I} _ l \subset \lbrace1, \dots, L\rbrace$ （ $|\mathcal{I} _ l| = M = \rho L \ll L$ ）。通过行抽取算子 $P _ {\mathcal{I} _ l} \in \lbrace0, 1\rbrace^{M \times L}$ 构造紧凑子矩阵：

$$
\tilde{Q} = P _ {\mathcal{I} _ l} Q, \quad \tilde{K} = P _ {\mathcal{I} _ l} K, \quad \tilde{V} = P _ {\mathcal{I} _ l} V \in \mathbb{R}^{M \times d}
$$

   在紧凑稠密张量上直接调用标准 FlashAttention-3 内核计算 $\tilde{O} = \text{FlashAttn}(\tilde{Q}, \tilde{K}, \tilde{V})$ ，随后通过转置散射算子 $P _ {\mathcal{I} _ l}^\top$ 还原回全序列残差流：

$$
H^{(l+1)} = H^{(l)} + P _ {\mathcal{I} _ l}^\top \big( \tilde{O} W _ O \big)
$$

   由于非活跃 Token $j \notin \mathcal{I} _ l$ 通过恒等残差分支完整保留了其隐状态 $H _ j^{(l)}$ ，它在第 $l+1$ 层可根据更新后的全局语义被重新选入 $\mathcal{I} _ {l+1}$ ！

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 64K–128K 多跳检索与大海捞针基准（RULER Multi-Hop Tracing）上，不可逆 Token 剪枝在 70% 稀疏度下准确率跌至 `31.2%`，而 **Token Sparse Attention** 保持了 **`88.4%`** 的高准确率，同时因完全复用稠密 FlashAttention 内核实现了 **2.6x** 真实注意力加速。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) & *Layer Dropping* (TMLR 2025) 的本质联系**：
  * TSA 的 `Gather -> Attention -> Scatter-Add` 本质上是对非活跃 Token 执行了**“Token 级条件层跳过（Token-Wise Conditional Layer Dropping）”**！这为我们把整层跳过（Layer Dropping）细粒度化为每个循环步/每层的动态子集更新提供了极佳的硬件友好范式。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-21_ai_paper_notes.md`


---

### 2.26 [2026-09-21] SIFT: Recursive Self-Improvement via Fast Tree-Search

* **论文信息**：`arXiv:2609.19526` (2026-09)
* **核心关键词**：Sample-Efficient RSI、Fast Tree-Search、LLM-as-a-Judge Surrogate、Multi-Fidelity Evaluation

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|            SIFT: Recursive Self-Improvement via Fast Tree-Search                  |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Root Agent Code H_0 ---> Expand K Candidate Code Patches {\Delta H_1..\Delta H_K}|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Tier-1 Surrogate Gate: Fast Pairwise LLM-as-a-Judge + Syntax/Unit Smoke Test|  |
|  |    Scores semantic plausibility & structural novelty in <3 seconds          |  |
|  |    Prunes 85% of low-utility patches BEFORE benchmark execution             |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Tier-2 Full Benchmark Gate: Execute Top-m Survivors on Held-Out Task Suite  |  |
|  |    Backpropagate true reward R(H) to update UCT Tree Search value estimates |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **RSI 树搜索中的“评估瓶颈（Evaluation Bottleneck）”**：在搜索智能体改进补丁时，超过 95% 的算力消耗在将每个候选补丁运行在数百道下游评测题上，而其中绝大部分候选修改仅包含语法微调或退化逻辑。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **双保真度 UCT 树搜索准则（Bi-Fidelity UCT Selection）**：
   结合快速评判器先验得分 $\hat{Q} _ {\text{judge}}(H)$ 与真实基准评估均值 $\bar{R} _ {\text{eval}}(H)$ 构建混合树搜索上置信界：

$$
\text{UCT} _ {\text{SIFT}}(H) = \frac{n(H) \bar{R} _ {\text{eval}}(H) + \kappa \hat{Q} _ {\text{judge}}(H)}{n(H) + \kappa} + c \sqrt{\frac{\ln N(\text{parent}(H))}{n(H) + 1}}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 SWE-bench 与数学推理智能体自优化中，SIFT 将达到相同性能增益所需的下游基准评估次数降低 **6.4x**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接对应我们 `rsi-diagnosis-mutator` 的 `SMOKE-TEST (<5s) -> REMOTE GPU EVAL` 两级门控协议**：再次验证了在提交昂贵远程评测前通过轻量级诊断与冒烟测试过滤无效变异的高杠杆价值。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-21_ai_paper_notes.md`


---

### 2.27 [2026-09-20] SHIFT-LLM: Distribution Shift Correction in Depth-Pruned LLMs

* **论文信息**：`arXiv:2608.25068` (2026-08)
* **核心关键词**：Depth Pruning、Distribution Shift Correction、Linear Residual Adapters (LRA)、Closed-Form Ridge Regression、Weight Folding

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|          SHIFT-LLM: Closed-Form Distribution Shift Correction at Cut Sites        |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Original Stack:  h^{(l-1)} ---> [Pruned Block l..l+m] ---> h_{\text{orig}}^{(l+m)}|
|  Pruned Stack:    \tilde{h}^{(l-1)} -----(Identity Skip)---> \tilde{h}^{(l-1)}    |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Covariate Shift Diagnosis at Pruning Cut Site (剪枝切口协变量偏移诊断)   |  |
|  |    \Delta \mu = \mathbb{E}[h_{\text{orig}}^{(l+m)} - \tilde{h}^{(l-1)}],    |  |
|  |    Angular & norm mismatch causes downstream RMSNorm / Attention saturation |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Closed-Form Linear Residual Adapter (LRA) via Woodbury/Ridge             |  |
|  |    \hat{h}^{(l+m)} = \tilde{h}^{(l-1)} + U_r V_r^\top \tilde{h}^{(l-1)} + b |  |
|  |    Solved in closed form on 128 calibration sequences (Training-Free)       |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **层剪枝切口处的“流形断裂（Manifold Fracture）”**：当直接移除 Transformer 中的第 $l$ 至 $l+m$ 层时，第 $l-1$ 层的输出隐状态 $\tilde{h}^{(l-1)}$ 被直接送入原本期望接收 $h _ {\text{orig}}^{(l+m)}$ 的第 $l+m+1$ 层。由于缺失了中间层的残差漂移与旋转，输入分布的一阶均值 $\mu$ 与二阶协方差矩阵 $\Sigma$ 发生剧烈跳变，导致紧随其后的注意力层 Q/K 点积失真并沿着深层指数级放大。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **剪枝切口处的最小二乘残差重构**：
   设剪枝段输入隐状态矩阵为 $X = \tilde{H}^{(l-1)} \in \mathbb{R}^{N \times d}$ ，原始未剪枝模型在该切口输出的目标残差增量为 $\Delta Y = H _ {\text{orig}}^{(l+m)} - \tilde{H}^{(l-1)} \in \mathbb{R}^{N \times d}$ 。SHIFT-LLM 在切口处插入一个低秩线性残差适配器（LRA） $W _ {\text{LRA}} = U _ r V _ r^\top + \mathbf{1} b^\top$ ，通过带 Tikhonov 正则化的岭回归闭式求解全秩最优映射 $W^\star$ ：

$$
W^\star = \arg\min _ {W \in \mathbb{R}^{d \times d}} \big\Vert \Delta Y - (X - \bar{X}) W \big\Vert _ F^2 + \lambda \Vert W \Vert _ F^2 = \Big( \tilde{X}^\top \tilde{X} + \lambda I _ d \Big)^{-1} \tilde{X}^\top \Delta \tilde{Y}
$$

2. **激活协方差加权奇异值截断（Covariance-Weighted Truncated SVD）**：
   为保证适配器自身的计算开销可忽略（或直接折叠进下一层权重），对预测输出空間执行白化 SVD 分解：

$$
\tilde{X} W^\star = \hat{U} \hat{\Sigma} \hat{V}^\top \implies U _ r = (\tilde{X}^\top \tilde{X} + \lambda I _ d)^{-1/2} \hat{U} _ {:, 1:r} \hat{\Sigma} _ {1:r}^{1/2}, \quad V _ r = \hat{V} _ {:, 1:r} \hat{\Sigma} _ {1:r}^{1/2}
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **Llama-3-8B/70B** 与 **Qwen-2.5-14B** 上剪除 **25%–35% 的层**后，无需任何梯度下降微调（仅需 30 秒闭式矩阵求逆），SHIFT-LLM 将 WikiText2 困惑度（PPL）从 `28.4` 恢复至 **`9.1`**，零样本常识与数学推理平均精度恢复 **`+7.9%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与我们 `modellesion-compression-scaffold`、`vla-dtr` (Ortho-MerA) 及 *Layer Dropping* (TMLR 2025) 的直接印证**：
  * SHIFT-LLM 的闭式岭回归校正算子 $W^\star = (\tilde{X}^\top \tilde{X} + \lambda I)^{-1} \tilde{X}^\top \Delta \tilde{Y}$ 与我们在 `modellesion-compression-scaffold` 中使用的 **Depth SVD-LoRA / Woodbury KKT 闭式残差补偿** 数学形式完全一致！更进一步，结合我们的 `vla-dtr`（Ortho-MerA），我们只需对正交切空间残差 $\Delta Y _ \perp = \Delta Y \cdot P _ \perp(X)$ 进行低秩 SVD 拟合，而将平行分量 $\Delta Y _ \parallel$ 简化为标量增益 $\alpha \in \mathbb{R}$ ，即可用一半的秩恢复更高的几何保真度。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#post-pruning-recovery` (Training-Free Closed-Form Residual Recovery)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-20_ai_paper_notes.md`


---

### 2.28 [2026-09-20] Minima-KV: Mixed-Format Paged Attention for Extreme KV Cache Compression

* **论文信息**：`arXiv:2608.23834` (2026-08)
* **核心关键词**：Mixed-Precision KV Cache、PagedAttention、Sub-Page Bit-Packing、Reasoning Continuity

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|        Minima-KV: Mixed-Format Paged Attention for Extreme KV Compression         |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Incoming KV Tokens ---> Saliency Tiering: [Tier-0: FP16] [Tier-1: INT4] [Tier-2: INT2]|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Unified Iso-Byte Physical Page Pool (等字节物理页统一内存池)             |  |
|  |    Each Physical Page = 64 KB fixed size:                                   |  |
|  |    * Can store N_0 FP16 tokens OR 4*N_0 INT4 tokens OR 8*N_0 INT2 tokens    |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Warp-Specialized Mixed-Format PagedAttention Kernel                      |  |
|  |    Single CUDA kernel dispatches dequantization per page descriptor header  |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **混合精度 KV 缓存的“页表碎片化与多核启动开销”**：虽然算法层已证明将关键 Token 存为 FP16、次要 Token 存为 INT4/INT2 可逼近无损压缩，但在 vLLM 等生产级 PagedAttention 系统中，传统的物理页（Page Block）按固定 Token 槽位数划分。若不同位宽的 Token 混存，会导致高达 40% 的页内字节对齐浪费（Internal Fragmentation），或被迫拆分为 3 次独立 CUDA Kernel 启动。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **等字节容量物理页抽象（Iso-Byte Physical Page Abstraction）**：
   固定每个物理页的字节容量为 $B _ {\text{page}}$ （如 64 KB）。对于位宽为 $b \in \lbrace16, 4, 2\rbrace$ 的页类型，其容纳的逻辑 Token 槽位数动态缩放为：

$$
C _ {\text{slots}}(b) = \frac{8 \cdot B _ {\text{page}}}{2 \cdot H _ {kv} \cdot d _ h \cdot b + M _ {\text{meta}}(b)}
$$

   其中 $M _ {\text{meta}}(b)$ 为分组量化缩放因子与零点（Scale & Zero-Point）的紧凑页头字节数。
2. **页描述符驱动的单核融合反量化注意力（Single-Kernel Fused Dequant-Attention）**：
   在逻辑页表中增加 2-bit 格式标签 $\text{fmt}(p) \in \lbrace0, 1, 2\rbrace$ ，CUDA Warp 在读取物理页 $p$ 时根据 $\text{fmt}(p)$ 在寄存器内执行即时位解包（Register-Level Bit Unpacking）：

$$
\hat{K} _ p = \text{Unpack} _ {\text{fmt}(p)}(Q _ p^K) \odot s _ p^K + z _ p^K, \qquad S _ p = Q \hat{K} _ p^\top
$$

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **Llama-3.1-70B** 与 **Qwen-2.5-32B** 的 128K 长思维链并发服务中，Minima-KV 实现 **4.6x** 真实物理显存节省（零内部页碎片），将最大并发 Batch Size 提升 **3.9x**，端到端解码吞吐提升 **2.7x**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接解决我们昨日精读的 SelKV 与 `Efficient Ads / HisTrim` 混合位宽生产落地瓶颈**：可将我们的正交价值空间显著性打分（Perp-OBCache）作为 Minima-KV 的三档分层准则（FP16 / INT4 / INT2），直接集成进统一等字节页表内核中。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-20_ai_paper_notes.md`


---

### 2.29 [2026-09-19] WRP: Forward-Free LLM Depth Pruning via Weight Redundancy

* **论文信息**：`arXiv:2609.09883` (2026-09)
* **核心关键词**：Forward-Free Depth Pruning、Weight Redundancy、Spectral Subspace Alignment、Calibration-Free Layer Dropping

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|            WRP: Forward-Free LLM Depth Pruning via Weight Redundancy              |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Frozen Pretrained Weights {W_Q^{(l)}, W_K^{(l)}, W_V^{(l)}, W_O^{(l)}, W_FFN^{(l)}}|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Effective Layer Operator Construction (无需前向激活的等效层算子构建)     |  |
|  |    \mathcal{T}_{\text{attn}}^{(l)} = W_O^{(l)} W_V^{(l)},                   |  |
|  |    \mathcal{T}_{\text{ffn}}^{(l)}  = W_{\text{down}}^{(l)} W_{\text{up}}^{(l)}| |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Spectral Concentration & Inter-Layer Subspace Redundancy (谱冗余度量)    |  |
|  |    R_{\text{intra}}(l) = 1 - \frac{\exp(H(\sigma^{(l)}))}{d}                |  |
|  |    R_{\text{inter}}(l) = \| U_{1:r}^{(l)\top} U_{\text{prev}}^{(1:l-1)} \|_F^2|
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 3. Zero-Pass One-Shot Block Pruning (<10 Seconds on CPU/Single GPU)         |  |
|  |    Prune top-K redundant blocks with highest w_1 R_{\text{intra}} + w_2 R_{\text{inter}}|
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **校准集偏差（Calibration Set Bias）与前向显存开销**：现有的大模型深度/层剪枝方法（如 ShortGPT 的 Block Influence、LaCo、SliceGPT）均依赖在特定校准集（如 WikiText2 或 C4）上运行前向传播以统计输入输出余弦相似度。这不仅在 70B+ 模型上消耗高昂显存与时间，更严重的是层重要性打分高度受制于校准集分布——在通用语料上表现为“弱贡献”的层，往往承载着数学推理或代码生成的关键长尾子空间，剪除后导致严重的领域退化。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **无激活等效残差映射提取**：
   对于第 $l$ 层 Transformer 块，将其对残差流 $h^{(l-1)}$ 的线性主轴作用表征为注意力值-输出合成矩阵 $M _ {\text{attn}}^{(l)} = W _ O^{(l)} W _ V^{(l)} \in \mathbb{R}^{d \times d}$ 与前馈网络合成算子 $M _ {\text{ffn}}^{(l)} = W _ {\text{down}}^{(l)} (W _ {\text{up}}^{(l)} \odot \bar{\sigma} _ {\text{gate}}) \in \mathbb{R}^{d \times d}$ 。
2. **层内有效秩赤字与层间子空间投影重叠度**：
   对合成算子执行奇异值分解 $M^{(l)} = U^{(l)} \Sigma^{(l)} V^{(l)\top}$ ，定义归一化奇异值分布 $p _ i^{(l)} = \frac{\sigma _ i^{(l)}}{\sum _ j \sigma _ j^{(l)}}$ 。层的权重综合冗余度得分 $\mathcal{S} _ {\text{WRP}}(l)$ 由**层内谱坍缩度**与**相对于前序累积子空间的投影冗余度**共同决定：

$$
\mathcal{S} _ {\text{WRP}}(l) = \underbrace{\left( 1 - \frac{\exp\big(-\sum _ {i=1}^d p _ i^{(l)} \log p _ i^{(l)}\big)}{d} \right)} _ {\text{Intra-Layer Spectral Redundancy}} + \lambda \underbrace{\frac{\big\Vert P _ {\text{span}(1:l-1)} U _ {:, 1:r}^{(l)} \big\Vert _ F^2}{r}} _ {\text{Inter-Layer Subspace Overlap}}
$$

   其中 $P _ {\text{span}(1:l-1)}$ 为前 $l-1$ 层输出主奇异子空间的正交投影算子。若第 $l$ 层的输出主奇异方向几乎完全落在前序层已经张成的子空间内（即缺乏新的正交特征扩展），则该层被判定为高度冗余。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* **秒级零样本层裁剪且跨领域泛化更强**：在 **Llama-3-8B/70B**、**Qwen-2.5-14B** 与 **Mistral-7B** 上，WRP 在完全不运行任何前向传播（耗时不足 8 秒）的情况下剪除 **20%–25% 的层**，在 GSM8K 与 HumanEval 等对校准集敏感的生成任务上比 ShortGPT 和 SLEB 高出 **`+3.4%` 至 `+6.1%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与 *Layer Dropping* (TMLR 2025)、*Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026) 及 *Transformer-Geometry* (`arXiv:2609.15975`, EMNLP 2026) 的深度呼应**：
  * WRP 的第二项 $\big\Vert P _ {\text{span}(1:l-1)} U _ {:, 1:r}^{(l)} \big\Vert _ F^2$ 在权重空间精确刻画了我们在 *Transformer-Geometry* 中定义的**平行分量与正交分量之比**——当层权重输出子空间与前序累积子空间高度重合时，该层仅产生平行特征放大而缺乏正交旋转增量！我们可以将 WRP 的纯权重谱重叠指标与单批次激活几何探针结合，作为 `vla-dtr`（VLADrop）的快速层筛选先验。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#depth-and-layer-pruning` (Zero-Forward Weight Spectral Layer Pruning)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-19_ai_paper_notes.md`


---

### 2.30 [2026-09-19] REAP: Router-Weighted Expert Activation Pruning for Sparse MoE Models

* **论文信息**：`arXiv:2510.13999` (2025/2026)
* **核心关键词**：MoE Expert Pruning、Router Gate Weighting、Expert Activation Norm、Generative Reasoning Preservation

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|            REAP: Router-Weighted Expert Activation Pruning Pipeline               |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Token x_t ---> Router Gate g_{t,e} = Softmax(W_r x_t)_e                          |
|            ---> Active Expert Output E_e(x_t) = W_down (SiLU(W_gate x_t) * W_up x_t)|
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | Joint Multiplicative Saliency Metric (门控权重 x 激活输出范数联合度量)       |  |
|  |    I_{\text{REAP}}(e) = \mathbb{E}_{x_t \in \mathcal{A}_e} [ g_{t,e} \cdot  |  |
|  |                         \| E_e(x_t) \|_2 ] \cdot \hat{P}(e \in \text{Top-}k)|  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|       Prune Lowest-I_{\text{REAP}} Experts ---> Gate Renormalization (Zero-Train) |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **仅凭路由频率或专家合并（Expert Merging）在生成任务上的失效**：传统 MoE 压缩常根据专家被选中的频次 $\hat{P}(e \in \text{Top-}k)$ 剪枝，或将相似专家权重线性平均（Merging）。作者发现：（1）在代码生成与数学推理等生成任务中，线性合并两个非线性 SwiGLU 专家的权重会破坏内部特征门控对齐，引起特征坍缩；（2）许多高频被选中的专家其输出向量范数 $\Vert E _ e(x _ t)\Vert _ 2$ 极小（充当空操作/恒等缓冲），而真正决定推理跃迁的专家则具有高门控权重乘以高输出激活范数。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **路由器加权激活范数重要性（Router-Weighted Activation Norm）**：
   由于 MoE 层的精确输出增量为 $\Delta h _ t = \sum _ {e \in \text{Top-}k(x _ t)} g _ {t,e} E _ e(x _ t)$ ，单个专家 $e$ 从激活集合中移除时引起的期望一阶残差上界正比于 $g _ {t,e} \Vert E _ e(x _ t)\Vert _ 2$ 。因此 REAP 定义专家 $e$ 的全局重要性为：

$$
\mathcal{I} _ {\text{REAP}}(e) = \frac{1}{|\mathcal{D} _ {\text{cal}}|} \sum _ {t=1}^{|\mathcal{D} _ {\text{cal}}|} \mathbb{I}\big(e \in \text{Top-}k(x _ t)\big) \cdot g _ {t,e} \cdot \big\Vert E _ e(x _ t) \big\Vert _ 2
$$

2. **保留集门控重归一化（Post-Pruning Gate Renormalization）**：
   裁剪掉得分最低的专家集合 $\mathcal{E} _ {\text{prune}}$ 后，对剩余专家集合 $\mathcal{E} _ {\text{keep}}$ 的门控权重执行保和重归一化 $\tilde{g} _ {t,e} = \frac{g _ {t,e}}{\sum _ {j \in \text{Top-}k(x _ t) \cap \mathcal{E} _ {\text{keep}}} g _ {t,j}}$ ，以补偿被移除专家的幅度损失。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **Mixtral-8x7B**、**DeepSeek-MoE-16B** 与 **Qwen1.5-MoE-A2.7B** 上，REAP 在 **25%–37.5% 专家剪枝率**下，在 GSM8K 与 HumanEval 生成基准上大幅超越各类专家合并算法（HC-SMoE、M-SMoE）达 **`+8.5%` 至 `+14.2%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **与 *Capacity-Aware Inference* (ICLR 2026) & *Transformer-Geometry* (EMNLP 2026) 的结合**：
  * REAP 揭示了 $\Vert g _ {t,e} E _ e(x _ t)\Vert _ 2$ 相比单纯门控概率 $g _ {t,e}$ 的优越性。结合我们的 *Transformer-Geometry*，我们可以进一步将 $\Vert E _ e(x _ t)\Vert _ 2$ 替换为正交切向范数 $\Vert P _ \perp(h _ t) E _ e(x _ t)\Vert _ 2$ ，避免那些仅沿当前残差方向做无效径向放大的专家占据高分。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-19_ai_paper_notes.md`


---

### 2.31 [2026-09-19] KVzap: Fast Input-Adaptive KV Cache Compression

* **论文信息**：`arXiv:2601.07891` (2026-01)
* **核心关键词**：Input-Adaptive KV Compression、Dynamic Budget Allocation、Long-Context Inference、Zero-Overhead Gating

#### 📐 架构与核心算法流程图 (ASCII Blueprint)

```text
+-----------------------------------------------------------------------------------+
|               KVzap: Fast Input-Adaptive KV Cache Compression                     |
+-----------------------------------------------------------------------------------+
|                                                                                   |
|  Input Sequence X_{1:L} ---> Layer l Attention Entropy & Dispersion Probe         |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 1. Input-Adaptive Retention Ratio Predictor (输入感知动态保留率估计)        |  |
|  |    \rho_{l,h}(X) = \text{Clamp}\big( \frac{\exp(H(A_{l,h}))}{L}, \rho_{\min}, \rho_{\max} \big)|
|  |    Spiky attention -> Aggressive zap; Uniform retrieval -> High retention   |  |
|  +-----------------------------------------------------------------------------+  |
|                                        |                                          |
|                                        v                                          |
|  +-----------------------------------------------------------------------------+  |
|  | 2. Local + Heavy-Hitter Zap Kernel (硬件友好块级快速裁剪)                   |  |
|  |    Keep top-\lceil \rho_{l,h}(X) L \rceil keys/values + sliding sink window |  |
|  +-----------------------------------------------------------------------------+  |
+-----------------------------------------------------------------------------------+
```

#### 🎯 背景与痛点 (Background & Pain Points)
* **静态固定压缩率（Fixed Compression Ratio）对输入复杂度差异的盲目性**：现有 KV 压缩方法往往对所有输入样本、所有层与注意力头强制设定固定的预算比例（例如固定保留 20%）。然而，简单摘要任务的注意力高度集中在少数锚点 Token 上（可安全压缩 85%），而密集多跳检索或代码调试任务的注意力分布高度弥散，固定高压缩率会导致关键上下文丢失。

#### 💡 核心方法与数学公式 (Core Methodology & Math)
1. **基于归一化注意力谱熵的输入自适应预算（Spectral-Entropy Adaptive Budget）**：
   对于第 $l$ 层第 $h$ 个注意力头在观察窗口 $W$ 上的平均注意力分布 $\bar{a} _ {l,h} \in \Delta^{L-1}$ ，计算其香农熵 $H(\bar{a} _ {l,h}) = -\sum _ {j=1}^L \bar{a} _ {l,h,j} \log \bar{a} _ {l,h,j}$ 。定义该头的有效支撑集比例（Effective Support Ratio）作为动态保留率 $\rho _ {l,h}(X)$ ：

$$
\rho _ {l,h}(X) = \text{clip}\left( \gamma \cdot \frac{\exp\big( H(\bar{a} _ {l,h}) \big)}{L}, \rho _ {\min}, \rho _ {\max} \right)
$$

   当注意力高度尖锐时， $\exp(H(\bar{a} _ {l,h})) \ll L$ ，KVzap 自动触发激进裁剪；当输入需要广泛上下文聚合时， $\exp(H(\bar{a} _ {l,h}))$ 增大，自动扩容该头的保留槽位。

#### 📊 关键实验与结论 (Key Experiments & Takeaways)
* 在 **LongBench**、**InfiniteBench** 与 **Needle-in-a-Haystack** 上，KVzap 实现了平均 **2.8x–4.1x** 的端到端 KV 显存压缩与 **2.3x** 解码吞吐提升，同时在密集检索任务上比固定预算 SnapKV 高出 **`+4.7%`**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发
* **直接赋能我们 `Efficient Ads / HisTrim` 与 `rsi-diagnosis-mutator` 的序列有效样本量（ESS）自适应门控**：
  * 注意 $\exp(H(\bar{a}))$ 与我们在 `rsi-diagnosis-mutator` 中用于诊断长序列注意力坍缩的 **Sequence Effective Sample Size ( $\text{ESS} = 1 / \sum _ j a _ j^2$ )** 在数学上同属 Rényi 熵族（ $\alpha=1$ vs. $\alpha=2$ ）！我们可以在 `HisTrim` 和 `vla-dtr` 中直接用计算更快的二阶 Rényi 有效样本量 $\text{ESS} _ {l,h} / L$ 动态调节每层视觉/用户历史 Token 的保留比例。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-19_ai_paper_notes.md`


---

### 2.32 [2026-09-18] ✂️ *AnchorPrune: Geometry-Preserving Representation Hierarchy Compression for Multimodal Large Language Models*
> **聚焦领域**：Multimodal Sparsity · Representation Hierarchies · Layer Dropping · Geometric Manifolds  
> **arXiv**：[`arXiv:2609.08842`](https://arxiv.org/abs/2609.08842)

```
  多模态隐状态流形 ──► [ 1. 局部几何锚点提取 (Anchor SVD) ] ──► 计算流形重构失真率 D_l
                                     │                                      │
                                     ▼                                      ▼
                      [ 2. 层级表征阶梯贡献判定 ]             [ 3. 联合压缩: 40% 层丢弃 + 50% Token 稀疏 ]
                      判为冗余饱和层 ──► 予以跳过               零微调保留 99.2% MMBench 精度
```

#### 🎯 背景与痛点 (Problem Statement)
多模态大模型在深层网络中存在极高比例的视觉表征冗余。现有的 Token 剪枝与 Layer Dropping 往往割裂进行：若先剪 Token 再丢层，会导致跨模态语义对齐发生断崖式崩塌；若仅做静态层丢弃，浅层大量的背景无用 Token 依然占据巨大的显存与 Attention 算力。

#### 💡 核心方法与原文底层数学实现 (Mathematical Formulations)
1. **多模态局部几何锚点矩阵 (Multimodal Geometric Anchors)**：
   - 在第 $l$ 层提取多模态激活流形 $\mathcal{M} _ l$ 上的代表性锚点子集 $\mathcal{A} _ l = \lbrace a _ 1, a _ 2, \dots, a _ K\rbrace \subset \mathbb{R}^{d}$ ；
   - 求解局部切空间的主成分基底，定义层级几何表征流形失真度指标 $\mathcal{D} _ l$ ：

$$
\mathcal{D} _ l \triangleq \frac{1}{K} \sum _ {k=1}^K \left\lVert a _ k - \Pi _ {\mathcal{A} _ {l-1}}(a _ k) \right\rVert _ 2^2
$$

   - 当 $\mathcal{D} _ l < \tau _ {\text{layer}}$ 时，判定该层为表征阶梯中的平坦饱和层，可安全丢弃。
2. **锚点引导的动态 Token 稀疏过滤 (Anchor-Guided Token Sparsification)**：
   - 仅保留与核心几何锚点内积相似度大于动态阈值的 Token，在浅层过滤掉 50% 以上的无用背景 Patch，同时维持深层关键语义边界。

#### 📊 关键实验与结论 (Experiments & Findings)
* **评估模型**：Qwen2-VL-7B/72B、LLaVA-NeXT-34B；
* **压缩指标**：联合跳过 **40% Transformer 层** 并剔除 **50% 视觉 Token**，无需微调，在 MME、MMBench、ChartQA 上平均精度损失仅 **0.8%**，端到端推理提速 **2.7 倍**，显存峰值降低 **62%**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发 (Relevance & Synergy with Our Works)
* **🎯 锚定代表作**：
  * [Paper #15: *Demystifying When Pruning Works via Representation Hierarchies* (ICML 2026)]
  * [Paper #8: *Understanding and Harnessing Sparsity for Unified Multimodal Models* (TMLR 2026)]
  * [Paper #9: *Uncovering the Redundancy in Transformers via Layer Dropping* (TMLR 2025)]
* **🔬 机理对比与技术演进**：
  * 我们在 *ICML 26* 与 *TMLR 25* 中奠定了从“表征层级阶梯（Representation Hierarchies）”解释剪枝机理的理论基石；
  * *AnchorPrune* 将我们的层级冗余理论推进到了“层丢弃（Layer Dropping）与 Token 动态稀疏（Token Sparsity）的二维联合优化”，提供了具体的几何锚点判据；
* **💡 下一阶段研究（Next Research Directions）落地启发**：
  * 可直接将锚点流形失真度 $\mathcal{D} _ l$ 集成至我们的多模态轻量化评估脚本中，作为我们后续多模态稀疏化大模型训练的正则化损失函数。

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#structured-pruning-and-sparsity` (`Shwai-He/Awesome-LLMs-Pruning`)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-18_ai_paper_notes.md`


---

### 2.33 [2026-09-18] 🗜️ *Decoupled-KV: Low-Rank Residual Decomposition for Multi-Turn Agentic KV Cache Compression*
> **聚焦领域**：KV Cache Compression · Agent Long-Context · Low-Rank Decomposition · Memory Bandwidth  
> **arXiv**：[`arXiv:2609.07765`](https://arxiv.org/abs/2609.07765)

```
  多轮对话/Agent 历史 KV ──► [ 低秩主基底空间 U_base (共享常驻) ] ──► 显存占用极小 (占 10%)
                                              │
                                              ▼
                             [ 动态稀疏时域残差 ΔK, ΔV ] ──► 8-Bit 符号压缩 (占 8.5%)
                                              │
                                              ▼
                              [ 总 KV Cache 显存削减 81.5% (保持 99.4% 精度) ]
```

#### 🎯 背景与痛点 (Problem Statement)
在自主智能体（AI Agents）与多轮长对话场景中，随着工具调用轨迹和历史环境反馈不断延长（达到 64K~256K tokens），KV 缓存占据超过 80% 的 GPU 显存。传统的基于 Token 丢弃的方法会丢失历史工具调用的精确参数信息，导致 Agent 多步规划频繁崩溃。

#### 💡 核心方法与数学公式 (Mathematical Formulations)
1. **低秩基础基底与时域稀疏残差解耦 (Decoupled Representation)**：
   - 将跨轮次的 Key 张量 $K \in \mathbb{R}^{T \times d}$ 解耦为静态系统提示/工具定义的共享低秩基底 $U _ {\text{base}} \in \mathbb{R}^{d \times r}$ （ $r \ll d$ ）与动态增量残差：

$$
K = Z U _ {\text{base}}^T + \Delta K, \quad \text{其中 } \Vert\Delta K\Vert _ 0 \le s \cdot (T \times d)
$$

2. **正交残差追踪与高效重构**：
   - 对 $U _ {\text{base}}$ 保持全精度常驻显存，对稀疏残差 $\Delta K, \Delta V$ 执行 1.5-bit 量化编码与行稀疏存储，在注意力计算时通过轻量 Fused Kernel 瞬时还原。

#### 📊 关键实验与结论 (Experiments & Findings)
* 在 AgentBench、SWE-bench 与 LongBench 上，实现 **81.5% 的 KV Cache 显存削减（压缩比达 5.4×）**，长程任务规划成功率保持在全量缓存基准的 **99.4%**。

#### 🔗 与我们工作（Our Works）的直接关联与落地启发 (Relevance & Synergy with Our Works)
* **🎯 锚定代表作**：
  * [Paper #13: *EffiR: Making Large Language Models Efficient Dense Retrievers* (ACL 2026)]
  * [Paper #3: *SparseAdapter: Parameter-Efficient Fine-Tuning* (EMNLP 2022)]
* **🔬 机理对比与技术演进**：
  * 我们在 *EffiR (ACL 26)* 中探索了低维稠密向量对齐与检索压缩；
  * 本文证明了多轮 Agent 交互中 Key/Value 张量内部存在极强的低秩共享子空间与稀疏残差分离特性；
* **💡 下一阶段研究（Next Research Directions）落地启发**：
  * 可将该低秩残差分解架构应用于我们 Dense Retriever 的长文档向量索引中，将向量库内存开销直接削减 80%。

---

## 🔥 板块二：全球前沿热点精选 (Trending Frontier)

---

> [!TIP]
> **🎯 `Awesome-LLMs-Pruning` 仓库代码级落地点 (`Target Module`)**：`README.md#kv-cache-compression` (KV Cache Eviction, Quantization & Offloading)  
> **📚 上游精读归档 (`Upstream Source`)**：`scholar-odyssey/intelligence/papers/2026-09-18_ai_paper_notes.md`


---
