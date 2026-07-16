---
title: Architectures
nav_order: 3
---

# Architectures
{: .no_toc }

Structural specifications of natively pretrained academic models.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## How to read this table

**"Base architecture" means the design, not the weights.** Nearly every model here reuses a published architecture — LLaMA, GPT-2, BLOOM — while training its parameters from random initialization. That is normal science and does not disqualify a model. It is also the single most common source of confusion about this list: "based on the Llama architecture" and "based on Llama" are different claims, and only the second one is disqualifying.

`Not disclosed` means the authors did not publish the value. It is not a gap for someone to fill with a plausible guess.

## Decoder-only architectures

| Model | Lead | Params | Base architecture | Attention & position | Activation |
|:--|:--|:--|:--|:--|:--|
| LLM360 Amber | Petuum, MBZUAI | 6.7B | LLaMA | Multi-head, RoPE | SwiGLU |
| LLM360 Crystal | Petuum, MBZUAI, Cerebras | 6.7B | LLaMA + LayerNorm | Multi-head, 25% RoPE | SwiGLU |
| LLM360 K2 | MBZUAI, Petuum | 65B | LLaMA | Multi-head, RoPE | SwiGLU |
| LLM360 K2-V2 | MBZUAI IFM | 70B | Optimized LLaMA (80 layers, 8192 hidden) | Grouped-query, long-context RoPE | SwiGLU |
| OLMo 3 | Ai2 | 7B, 32B | Causal transformer | Grouped-query, YaRN | SwiGLU |
| OLMo Hybrid | Ai2 | 7B | Hybrid attention + Gated DeltaNet (3:1) | Gated DeltaNet linear RNN + attention | SwiGLU |
| Marin | Stanford CRFM | 8B, 32B | Llama-style | Grouped-query, RoPE | SwiGLU |
| Pythia | EleutherAI | 70M–12B | GPT-NeoX | Multi-head, RoPE | GELU |
| GPT-NeoX-20B | EleutherAI | 20B | GPT-NeoX | Multi-head, RoPE (25%) | GELU |
| GPT-J-6B | EleutherAI | 6B | GPT-J (parallel attn/FF) | Multi-head, RoPE | GELU |
| BLOOM | BigScience | 560M–176B | BLOOM | Multi-head, ALiBi | GELU |
| Apertus | EPFL, ETH Zürich, CSCS | 8B, 70B | Transformer decoder | 8B multi-head / 70B grouped-query, QK-Norm | xIELU |
| EuroLLM | IST, Unbabel, Edinburgh | 1.7B, 9B, 22B | Dense transformer | Grouped-query, RoPE | SwiGLU |
| Salamandra | Barcelona Supercomputing Center | 2B, 7B | Transformer decoder-only | Grouped-query, RoPE | SwiGLU |
| Poro 34B | TurkuNLP, Silo AI, HPLT | 34.2B | BLOOM | Multi-head, ALiBi | GELU |
| Viking | TurkuNLP, Silo AI, HPLT | 7B, 13B, 33B | LLaMA-like | Multi-head, RoPE | SwiGLU |
| FinGPT | TurkuNLP | 186M–13B | BLOOM | Multi-head, ALiBi | GELU |
| NorGPT | NTNU / NorwAI | 369M, 3B, 23B | GPT-2 | Multi-head, learned absolute | GELU |
| PULI GPT-3SX | HUN-REN NYTK | 6.7B | GPT-NeoX | Multi-head, RoPE | GELU |
| HPLT models | HPLT consortium | 2.15B | Llama-style | Multi-head, RoPE | SwiGLU |
| Minerva | Sapienza University of Rome | 350M–7B | Mistral-style | Grouped-query, RoPE | SwiGLU |
| CroissantLLM | Illuin, CentraleSupélec | 1.3B | LLaMA-style | Multi-head, RoPE | SwiGLU |
| GPT-SW3 | AI Sweden, RISE | 126M–40B | GPT-NeoX / NeMo Megatron | Multi-head, RoPE | GELU |
| Tucano | University of Bonn | 160M–2.4B | Llama | Grouped-query, RoPE | SwiGLU |
| TeenyTinyLlama | PUCRS, University of Bonn | 160M, 460M | Llama-2 | Multi-head, RoPE | SwiGLU |
| Fugaku-LLM | Tokyo Tech, Tohoku, RIKEN, Fujitsu | 13B | GPT-2 / Megatron-DeepSpeed | Global dense, absolute | GELU |
| LLM-jp-3 | NII | 1.8B–13B | LLaMA-2 | Multi-head, RoPE | SwiGLU |
| LLM-jp-4 8B | NII | 8.6B | Llama 2 | Multi-head, RoPE | SwiGLU |
| LLM-jp-4 32B-A3B | NII | 32B MoE (3.8B active) | Qwen3 MoE, 128 experts, 8 active | Grouped-query, RoPE | SwiGLU |
| InternLM2 | Shanghai AI Lab, SenseTime | 1.8B, 7B, 20B | LLaMA structural principles | Grouped-query, RoPE (200K ctx) | SwiGLU |
| InternLM3 | Shanghai AI Lab | 8B | InternLM | Grouped-query, RoPE | SwiGLU |
| Aquila2 | BAAI | 7B, 34B, 70B | GPT-3 / LLaMA design | Multi-head, RoPE | SwiGLU |
| CPM-1 | Tsinghua, BAAI | 2.6B | GPT-3 / decoder | Dense, absolute | GELU |
| YuLan-Base | Renmin University of China | 12B | Decoder-only | Multi-head, RoPE | SwiGLU |
| YuLan-Mini | Renmin University of China | 2.4B | Decoder-only | Grouped-query, RoPE | SwiGLU |
| Jais-13B | Inception, MBZUAI, Cerebras | 13B | GPT-3 | Multi-head, ALiBi | SwiGLU |
| Jais 2 | Inception, MBZUAI | 8B, 70B | Optimized decoder | Multi-head, ALiBi | SwiGLU |
| ALLaM-7B | SDAIA / NCAI | 7B | Llama-style (Megatron-LM) | Multi-head, RoPE | SwiGLU |
| Fanar Star | QCRI, HBKU | 7B | Transformer decoder | Not disclosed | Not disclosed |
| AraGPT2 | AUB MIND Lab | 135M–1.46B | GPT-2 | Multi-head, learned absolute | GELU |
| Falcon | TII | 7B, 40B, 180B | Falcon (parallel attn, multi-query) | Multi-query, RoPE | GELU |
| SEA-LION v1 | AI Singapore | 3B, 7B | MPT | Multi-head, ALiBi | GELU |
| TinyLlama | SUTD | 1.1B | Llama-2 | Grouped-query, RoPE | SwiGLU |
| SmallThinker | SJTU IPADS, Zenergize AI | 4B-A0.6B, 21B-A3B | Sparse MoE | Grouped-query, NoPE-RoPE hybrid | ReGLU |
| DCLM-7B | ML Foundations, UW | 6.9B | Llama-style (OpenLM) | Multi-head, RoPE | SwiGLU |
| MAP-Neo | M-A-P, University of Waterloo | 7B | Llama-style | Grouped-query, RoPE | SwiGLU |
| BioMedLM | Stanford CRFM | 2.7B | GPT-2 | Multi-head, learned absolute | GELU |
| GatorTronGPT | University of Florida | 5B, 20B | GPT-3 (Megatron-LM) | Multi-head, learned absolute | GELU |

## Non-autoregressive objectives

Only one model on this list departs from left-to-right next-token prediction. That is itself a finding: the from-scratch academic space has converged hard on the causal decoder, and alternatives to the objective are the rarest thing here.

| Model | Lead | Params | Objective | Attention & position | Activation |
|:--|:--|:--|:--|:--|:--|
| Sumi | Tohoku University | 7B | Uniform discrete diffusion (UDLM) | Grouped-query, YaRN | SwiGLU |

Sumi builds on generalized interpolating discrete diffusion, letting any token in a sequence be revised at any step rather than committing left to right. It is the first uniform diffusion language model pretrained at this scale, which makes it a reference point for measuring diffusion scaling dynamics against autoregressive baselines. See the [case study](../case-studies/sumi.html).

## What the table shows

**Architecture has converged; the differentiation moved elsewhere.** Nearly every model released since 2024 is a decoder-only transformer with grouped-query attention, rotary embeddings, and SwiGLU. If you sort this table by year, the right-hand columns stop varying.

That convergence is the argument for the list's existence rather than against it. When architecture is a solved commodity, the remaining degrees of freedom are the corpus, the tokenizer, the data ordering, and the training discipline — every one of which is fixed at pretraining time and inherited, unexamined, by anything built on someone else's checkpoint. The [corpora table](corpora.html) is where these models actually differ.

**The exceptions are informative.** The models that break the pattern break it deliberately and for stated reasons: Sumi's diffusion objective, OLMo Hybrid's Gated DeltaNet layers, SmallThinker's pre-attention routing for on-device prefetch, ALiBi in the older Nordic and Arabic models that needed length extrapolation before RoPE scaling matured. None of those changes is reachable by fine-tuning.
