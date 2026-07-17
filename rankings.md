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

Strict-avg is the mean of IFEval's prompt-level-strict and instruction-level-strict accuracy, exactly the "IFEval" column of the [Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard) v2. It measures whether a model actually follows explicit instructions, which is the capability that turned base GPT-3 into something people could use.

The reference line is **GPT-3.5-turbo-1106 = 55.9** (the original ChatGPT). Everything here is asked one question: *has a from-scratch university model reached that line?*

Two ground rules. **IFEval is an instruction-following metric**, so every ranked row is a model's **instruction-tuned** variant; base checkpoints are tracked in a separate base-model list. And **formats do not mix**: IFEval also gets reported "loose", or as prompt-strict alone, and those run higher than strict-avg, so they are shown separately and never ranked against the line.

## Universities

IFEval strict-avg, university-led instruction models. Four have a published, comparable number.

| IFEval | Model (instruction-tuned) | University | Source |
|--:|:--|:--|:--|
| **74.9** | Jais-2-70B-Chat | MBZUAI | card (EN; AR 70.6) |
| **61.6** | KOS-V4-Instruct (3B) | University of Kentucky | card (own harness, OLL-calibrated) |
| *55.9* | *GPT-3.5-turbo-1106 (the line)* | *OpenAI* | *InternLM2 report* |
| **51.5** | LLM360 K2-Chat | MBZUAI | Open LLM Leaderboard |
| **6.0** | TinyLlama-1.1B-Chat | SUTD | Open LLM Leaderboard |

**Two university models clear the original-ChatGPT line: Jais-2-70B-Chat (MBZUAI, 74.9) and KOS-V4-Instruct (University of Kentucky, 61.6)**, the latter a from-scratch 3B trained on 180B tokens and 24 GPUs, which is a notable result for that budget rather than a claim on the field. LLM360 K2-Chat (51.5) sits just under the line, level with Llama-2-70b-chat, GPT-3.5's open contemporary.

Reported, but **not** in strict-avg format, so not placed on the line:

| IFEval | Model | University | Format |
|--:|:--|:--|:--|
| 85.8 | SmallThinker-21BA3B-Instruct | SJTU | unlabeled |
| 75.2 | Apertus-70B-Instruct | EPFL / ETH Zürich | prompt-loose |

## The gap: needs evaluation

Every other **university** model has **no published IFEval in any format**. This is the finding, not a footnote: the field has barely measured its own instruction-following on a common axis.

Awaiting evaluation: Marin (Stanford), Minerva (Sapienza), Jais-13b (MBZUAI), CroissantLLM (CentraleSupélec), Fugaku-LLM (Tokyo Tech, Tohoku), Poro and Viking (U Turku), weblab-10b and Tanuki (U Tokyo), LLäMmlein (Würzburg), YuLan-Base and YuLan-Mini (Renmin), OpenLLaMA (UC Berkeley), DCLM (U Washington), FinGPT (U Turku), Tucano (U Bonn), LLaDA (Renmin), LLM360 Amber and Crystal (MBZUAI), and the base-only research models (Sumi, Mamba, H3, Based, Plaid, GLA), where instruction-following may not apply.

## Research institutes and national labs

Not universities, shown for context. Instruction-tuned variants; these have more leaderboard coverage.

| IFEval | Model (instruction-tuned) | Institution | Source |
|--:|:--|:--|:--|
| 72.4 | OLMo-2-7B-Instruct | Ai2 | Open LLM Leaderboard |
| 70.1 | InternLM2.5-20B-chat | Shanghai AI Lab | Open LLM Leaderboard |
| *55.9* | *GPT-3.5-turbo-1106 (the line)* | *OpenAI* | *InternLM2 report* |
| 44.0 | ALLaM-7B-Instruct | SDAIA | card (38.1 / 50.0) |
| 34.7 | OLMo-7B-Instruct (v1) | Ai2 | Open LLM Leaderboard |
| 30.4 | Lucie-7B-Instruct | CNRS / CEA | Open LLM Leaderboard |
| 24.5 | Salamandra-7B-instruct | BSC | Open LLM Leaderboard |
| 24.5 | Falcon-40B-instruct | TII | Open LLM Leaderboard |

Format-mismatched (not on the line): OLMo-3-32B-Think 89.0 (inst-loose, Ai2), InternLM3-8B-instruct 79.3 (prompt-strict, Shanghai AI Lab).

## Commercial reference line

Instruction / chat models, strict-avg unless noted.

| IFEval | Model | Format |
|--:|:--|:--|
| 86.7 | Llama-3.1-70B-Instruct | strict-avg |
| 86.4 | Qwen2.5-72B-Instruct | strict-avg |
| 81.0 | GPT-4o | unlabeled |
| 80.2 | GPT-4 | strict-avg (derived) |
| 74.4 | gemma-2-9b-it | strict-avg |
| 64.7 | Qwen2.5-3B-Instruct | strict-avg |
| **55.9** | **GPT-3.5-turbo-1106** | **strict-avg (the anchor)** |
| 55.0 | Mistral-7B-Instruct-v0.2 | strict-avg |
| 49.6 | Llama-2-70b-chat | strict-avg |

## Method and caveats

- **Source of truth** for open models is the Open LLM Leaderboard v2 "IFEval" value (strict-avg). Where a model is not on the board, the number comes from its own paper or card, and its format is labeled; where a card gives both strict sub-metrics (ALLaM, Jais 2, KOS-V4), strict-avg is computed as their mean.
- **GPT-3.5-turbo-1106** strict sub-metrics (50.5 / 61.2) are from the InternLM2 report (arXiv:2403.17297); GPT-3.5 snapshots differ (0613 around 57, 1106 = 55.9, 0125 around 49), so the snapshot is named.
- **KOS-V4-Instruct's 61.6** is measured on the authors' own copy of the harness, calibrated to the leaderboard (they measure Qwen2.5-3B at 64.0 against the board's 64.7).
- **GPT-4o's 81** is OpenAI's single figure with no strict/loose breakdown, so it is not verified strict-avg.
- MMLU and other benchmarks are kept as secondary context in the repository's `_data/evals.yml`; they are not the ranking axis.
- Everything marked *needs evaluation* is a candidate to run on a single common harness so the comparison is finally apples-to-apples rather than self-reported.
