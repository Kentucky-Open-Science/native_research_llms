---
title: Unverified candidates
nav_order: 7
---

# Unverified candidates
{: .no_toc }

Models that pass the from-scratch rule but fall short of a verified-list requirement.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## What this list is

Everything here was **pretrained from scratch by a non-commercial institution**, it clears the hardest bar. It is not on the [main list](https://github.com/Kentucky-Open-Science/native_research_llms#readme) because it misses one of the verified requirements: **openly downloadable weights**, roughly **1B+ parameters**, and a **generative** (non-encoder) objective.

Nothing here is disqualified. These are held for the day the blocking condition changes, weights get released, a larger variant ships, at which point they move to the verified list. Models that fail the from-scratch rule itself are not tracked here; they are removed, per the [inclusion criteria]({% link reference/criteria.md %}).

Full evidence for every entry, institution, from-scratch quote, source URL, license, lives in the repository's `_data/candidates.yml`.

## Weights not openly available

From-scratch and institutional, but the weights are gated behind approval, region-locked, or unreleased.

| Model | Institution | Size | Why it waits |
|:--|:--|:--|:--|
| [GPT-SW3](https://arxiv.org/abs/2305.12987) | AI Sweden, RISE | 126M–40B | No open download; access by application from a European research institution only. |
| [NorGPT](https://huggingface.co/NorGLM/NorGPT-3B) | NTNU | 369M, 3B, 23B | Available only to Nordic organizations and students. |
| [Fanar Star](https://arxiv.org/abs/2501.13944) | QCRI, HBKU | 7B | Weights never released; the open Fanar-1-9B is Gemma-2-derived and does not qualify. |
| [GLM-130B](https://github.com/THUDM/GLM-130B) | Tsinghua KEG | 130B | From scratch, but weights are application-gated under a custom license. |
| AuroraGPT | Argonne National Laboratory | 7B, 70B | DOE from-scratch base, but the model repo is private; no open weights yet. |

## Below the ~1B scale floor

From-scratch and openly available, but smaller than the verified list's parameter floor. Several are the reference implementations of alternative architectures, where the contribution is the objective rather than the scale.

| Model | Institution | Size | Note |
|:--|:--|:--|:--|
| [TeenyTinyLlama](https://github.com/Nkluge-correa/TeenyTinyLlama) | PUCRS, University of Bonn | 160M, 460M | Brazilian Portuguese, custom tokenizer. |
| [SEDD](https://github.com/louaaron/Score-Entropy-Discrete-Diffusion) | Stanford | 90M, 320M | Score-entropy discrete diffusion (ICML 2024 best paper). |
| [MDLM](https://huggingface.co/kuleshov-group/mdlm-owt) | Cornell | ~170M | Masked diffusion, trained on OpenWebText. |
| [UDLM](https://huggingface.co/kuleshov-group/udlm-lm1b) | Cornell | ~139M | Uniform diffusion; the small-scale sibling of the listed Sumi. |
| [Hyena](https://huggingface.co/Zymrael/hyena-small-150b-tok) | Stanford, Mila | 153M released | Long-convolution; larger paper variants are not open-weight. |
| [Diffusion-LM](https://github.com/XiangLi1999/Diffusion-LM) | Stanford | ~80M | Continuous diffusion; a toy-scale proof of concept. |

## Encoder-only

In scope by the criteria, but excluded from the verified generative lists. Grouped here until they get their own home.

| Model | Institution | Size | Note |
|:--|:--|:--|:--|
| [EuroBERT](https://huggingface.co/EuroBERT/EuroBERT-210m) | CentraleSupélec, IST | 210M–2.1B | Multilingual masked-LM encoder over a 5T-token corpus. |
| [SciBERT](https://huggingface.co/allenai/scibert_scivocab_uncased) | Allen Institute for AI | ~110M | Scientific-text BERT; the `scivocab` variants are from scratch. |
| [WangchanBERTa](https://huggingface.co/airesearch/wangchanberta-base-att-spm-uncased) | VISTEC | ~105M | Thai RoBERTa-base trained on 78.5 GB of Thai text. |

## Promotion

If you can show that one of these has crossed the line, open weights released, a 1B+ variant shipped, please [open a correction](https://github.com/Kentucky-Open-Science/native_research_llms/issues/new?template=correction.yml). The bar to move onto the verified list is the same public, checkable evidence the main list requires.
