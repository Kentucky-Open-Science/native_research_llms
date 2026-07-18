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

IFEval strict-avg and MMLU (5-shot), university-led instruction models. Eleven now carry a comparable number; **eight we measured ourselves** on a pristine lm-eval-harness (2026-07-18).

| IFEval | MMLU | Model (instruction-tuned) | University | Source |
|--:|--:|:--|:--|:--|
| **74.9** | - | Jais-2-70B-Chat | MBZUAI | card |
| **70.8** | 61.1 | marin-8b-instruct | Stanford | measured |
| **61.6** | 27.8 | KOS-V4-Instruct (3B) | University of Kentucky | card (we measured 60.6) |
| **61.5** | 52.8 | YuLan-Mini-Instruct | Renmin | measured |
| *55.9* | - | *GPT-3.5-turbo-1106 (the line)* | *OpenAI* | *InternLM2 report* |
| 54.1 | 52.5 | LLäMmlein-7B-chat | Würzburg | measured |
| 51.5 | - | LLM360 K2-Chat | MBZUAI | Open LLM Leaderboard |
| 34.6 | pending | Poro-34B-chat | U Turku | measured |
| 21.5 | 40.7 | Minerva-7B-instruct | Sapienza | measured |
| 19.9 | 24.0 | CroissantLLMChat | CentraleSupélec | measured |
| 15.0 | 25.9 | Tucano-2b4-Instruct | U Bonn | measured |
| 6.0 | - | TinyLlama-1.1B-Chat | SUTD | Open LLM Leaderboard |

**Four university models clear the original-ChatGPT line: Jais-2-70B-Chat (74.9), marin-8b-instruct (70.8), KOS-V4-Instruct (61.6), and YuLan-Mini-Instruct (61.5).** KOS-V4 and YuLan-Mini are a statistical tie (a 0.9-point gap against a 2.14-point stderr). The two benchmarks rank the set almost independently: KOS-V4 is 3rd on instruction-following but near the MMLU chance floor, an instruction model by design and not a knowledge model, while Poro-34B is the largest model here (34B) yet places mid-pack, below models a third its size. Multilingual models (Poro, Minerva, Croissant, Tucano, LLäMmlein) are measured on English and understate their designed capability.

Reported, but **not** in strict-avg format, so not placed on the line:

| IFEval | Model | University | Format |
|--:|:--|:--|:--|
| 85.8 | SmallThinker-21BA3B-Instruct | SJTU | unlabeled |
| 75.2 | Apertus-70B-Instruct | EPFL / ETH Zürich | prompt-loose |

## What is left

The eight measurements above closed most of the gap. What remains is less "unmeasured" than "not yet runnable":

- **Deferred, gated (2):** Jais-13b-chat (MBZUAI) and Fugaku-LLM-13B-instruct (Tokyo Tech / Tohoku) return HTTP 403 until a license is accepted.
- **Excluded, not runnable as-is (7):** AmberChat, CrystalChat (MBZUAI), weblab-10b-instruction-sft (U Tokyo), and YuLan-Chat-3-12b (Renmin) publish no chat template; LLaDA-8B-Instruct (Renmin) is a masked-diffusion LM with no autoregressive loglikelihood for `lm-eval`; Tanuki-8x8B (U Tokyo) ships remote code incompatible with current `transformers`; apple/DCLM-7B-IT (U Washington) no longer resolves.
- **Base-only:** OpenLLaMA, FinGPT, Viking, AraGPT2, the biomedical models, and the base research models (Sumi, Mamba, H3, Based, Plaid, GLA) have no instruct variant to evaluate.

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

## Reference models

Not universities. A comparable-scale, GPT-3.5-generation reference set (the KOS-V4 card's "IFEval in context"), so the university numbers above sit against peers rather than the current frontier. A `~` marks a strict-avg estimated from a published loose or AVG4 figure, or an unofficial parameter count.

| IFEval | Model | Company | Params |
|--:|:--|:--|:--|
| 73.9 | Llama-3.2-3B-Instruct | Meta | 3.2B |
| 64.7 | Qwen2.5-3B-Instruct | Alibaba | 3.0B |
| 64.2 | Phi-3-medium-4k-instruct | Microsoft | 14B |
| 60.5 | Yi-1.5-9B-Chat | 01.AI | 8.8B |
| 57.7 | Phi-3.5-mini-instruct | Microsoft | 3.8B |
| ~57 | GPT-3.5-turbo-0613 | OpenAI | ~20B |
| 56.1 | Phi-3-mini-4k-instruct | Microsoft | 3.8B |
| **55.9** | **GPT-3.5-turbo-1106 (the line)** | OpenAI | ~20B |
| 55.0 | Mistral-7B-Instruct-v0.2 | Mistral AI | 7.2B |
| 54.7 | Mistral-7B-Instruct-v0.3 | Mistral AI | 7.2B |
| 50.4 | gemma-1.1-7b-it | Google | 8.5B |
| 49.5 | zephyr-7b-beta | Hugging Face | 7.2B |
| ~49 | GPT-3.5-turbo-0125 | OpenAI | ~20B |
| 44.3 | Llama-3.1-8B-Instruct | Meta | 8.0B |
| 43.7 | Qwen1.5-7B-Chat | Alibaba | 7.7B |
| 39.8 | Llama-2-13b-chat | Meta | 13B |
| 31.6 | Qwen1.5-4B-Chat | Alibaba | 4.0B |

For scale only: current frontier instruction models sit far above this range (GPT-4o around 81, Llama-3.1-70B around 87). They are a different size and generation, and are not the comparison here.

## Method and caveats

- **Measured rows** (Source = "measured") are from a pristine EleutherAI lm-evaluation-harness 0.4.12 run (univ-baseline, 2026-07-18): stock `ifeval` (google/IFEval, 541 prompts, 0-shot, greedy, chat template applied) and stock `mmlu` (cais/mmlu, 57 subjects, 5-shot, `acc`). Two controls passed: Qwen3-4B reproduced within 1.5 points, and KOS-V4's MMLU reproduced to four decimals across two harness builds.
- **Measurement error.** IFEval prompt-strict stderr is ±2.14 points on 541 prompts, so differences under about 2 points are not distinguishable (KOS-V4 and YuLan-Mini are a tie by this measure).
- **Multilingual models are scored on English.** Poro (Finnish), Minerva (Italian), Croissant (French), Tucano (Portuguese), and LLäMmlein (German) are measured on English IFEval and MMLU; the scores understate designed capability and are not a general quality ranking.
- **Other open-model rows** come from the Open LLM Leaderboard v2 "IFEval" column (strict-avg); card-derived rows (Jais 2, KOS-V4) compute strict-avg from the two strict sub-metrics. **KOS-V4-Instruct** is listed at its card value 61.6; our own pristine-harness run measured 60.63.
- **GPT-3.5-turbo-1106** strict sub-metrics (50.5 / 61.2) are from the InternLM2 report (arXiv:2403.17297); GPT-3.5 snapshots differ (0613 around 57, 1106 = 55.9, 0125 around 49), so the snapshot is named. **GPT-4o's 81** is OpenAI's single figure with no strict/loose breakdown, so it is not verified strict-avg.
