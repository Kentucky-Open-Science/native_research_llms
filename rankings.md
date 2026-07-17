---
title: Rankings
nav_order: 5
---

# Rankings
{: .no_toc }

University decoder progress, measured against the original-ChatGPT line.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## The metric

One number, chosen so a university model can be compared both to its peers and to the models everyone already knows: **IFEval, strict-avg**.

Strict-avg is the mean of IFEval's prompt-level-strict and instruction-level-strict accuracy — exactly the "IFEval" column of the [Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard) v2. It measures whether a model actually follows explicit instructions, which is the capability that turned base GPT-3 into something people could use.

The reference line is **GPT-3.5-turbo ≈ 59.3** (the original ChatGPT era). Everything here is asked one question: *has a from-scratch university model reached that line?*

**Formats do not mix.** IFEval also gets reported "loose", or as prompt-strict alone; those run higher than strict-avg and are shown separately, never ranked against the line.

## Universities

IFEval strict-avg, university-led models. Only three have a published, comparable number.

| IFEval | Model | University | Source |
|--:|:--|:--|:--|
| **74.9** | **Jais 2** (70B) | MBZUAI | card (EN; AR 70.6) |
| — | *· · · GPT-3.5-turbo ≈ 59.3 · · ·* | | |
| **51.5** | **LLM360 K2** | MBZUAI | Open LLM Leaderboard |
| — | *· · · Llama-2-70b-chat 49.6 · · ·* | | |
| **6.0** | **TinyLlama-1.1B** | SUTD | Open LLM Leaderboard |

**One university model clears the GPT-3.5 line: Jais 2 (MBZUAI).** LLM360 K2 (also MBZUAI) sits just under it, level with Llama-2-70b-chat — GPT-3.5's open contemporary.

Reported, but **not** in strict-avg format, so not placed on the line:

| IFEval | Model | University | Format |
|--:|:--|:--|:--|
| 85.8 | SmallThinker (21B) | SJTU | unlabeled |
| 75.2 | Apertus (70B) | EPFL / ETH Zürich | prompt-loose |

## The gap: needs evaluation

Every other **university** model has **no published IFEval in any format**. This is the finding, not a footnote: the field has barely measured its own instruction-following on a common axis.

Awaiting evaluation — Marin (Stanford), Minerva (Sapienza), Jais-13b (MBZUAI), CroissantLLM (CentraleSupélec), Fugaku-LLM (Tokyo Tech · Tohoku), Poro · Viking (U Turku), weblab-10b · Tanuki (U Tokyo), LLäMmlein (Würzburg), YuLan-Base · YuLan-Mini (Renmin), OpenLLaMA (UC Berkeley), DCLM (U Washington), FinGPT (U Turku), Tucano (U Bonn), LLaDA (Renmin), LLM360 Amber · Crystal (MBZUAI), and the base-only research models (Sumi, Mamba, H3, Based, Plaid, GLA), where instruction-following may not apply.

## Research institutes and national labs

Not universities, shown for context. These have more leaderboard coverage.

| IFEval | Model | Institution | Source |
|--:|:--|:--|:--|
| 72.4 | OLMo 2 (7B-Inst) | Ai2 | Open LLM Leaderboard |
| 70.1 | InternLM2.5 (20B-chat) | Shanghai AI Lab | Open LLM Leaderboard |
| — | *· · · GPT-3.5-turbo ≈ 59.3 · · ·* | | |
| 44.0 | ALLaM-7B | SDAIA | card (38.1 / 50.0) |
| 34.7 | OLMo (v1, 7B-Inst) | Ai2 | Open LLM Leaderboard |
| 30.4 | Lucie-7B | CNRS / CEA | Open LLM Leaderboard |
| 24.5 | Salamandra (7B-Inst) | BSC | Open LLM Leaderboard |
| 24.5 | Falcon (40B-Inst) | TII | Open LLM Leaderboard |

Format-mismatched (not on the line): OLMo 3 89.0 (inst-loose, Ai2), InternLM3-8B 79.3 (prompt-strict, Shanghai AI Lab).

## Commercial reference line

| IFEval | Model | Format |
|--:|:--|:--|
| 86.7 | Llama-3.1-70B-Instruct | strict-avg |
| 86.4 | Qwen2.5-72B-Instruct | strict-avg |
| 81.0 | GPT-4o | unlabeled |
| 80.2 | GPT-4 | strict-avg (derived) |
| 74.4 | gemma-2-9b-it | strict-avg |
| **59.3** | **GPT-3.5-turbo** | **strict-avg (the anchor)** |
| 55.0 | Mistral-7B-Instruct-v0.2 | strict-avg |
| 49.6 | Llama-2-70b-chat | strict-avg |

## Method and caveats

- **Source of truth** for open models is the Open LLM Leaderboard v2 "IFEval" value (strict-avg). Where a model is not on the board, the number comes from its own paper or card, and its format is labeled; where a card gives both strict sub-metrics (ALLaM, Jais 2), strict-avg is computed as their mean.
- **GPT-3.5-turbo** strict sub-metrics (53.8 / 64.7) are from the GLAN paper ([arXiv 2402.13064](https://arxiv.org/abs/2402.13064)); the original IFEval paper evaluated only GPT-4 and PaLM 2.
- **GPT-4o's 81** is OpenAI's single figure with no strict/loose breakdown — not verified strict-avg.
- MMLU and other benchmarks are kept as secondary context in the repository's `_data/evals.yml`; they are not the ranking axis.
- Everything marked *needs evaluation* is a candidate to run on a single common harness so the comparison is finally apples-to-apples rather than self-reported.
