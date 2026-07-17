---
title: Home
nav_order: 1
description: A registry of large language models pretrained from scratch by universities, non-profit research institutes, and national laboratories.
permalink: /
---

# The Academic Foundation Model Index (AFMI)
{: .fs-9 }

Which universities have actually built a foundation model end to end, and how do they measure up to GPT-3.5?
{: .fs-6 .fw-300 }

[The list](https://github.com/Kentucky-Open-Science/native_research_llms#readme){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Rankings]({% link rankings.md %}){: .btn .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Inclusion criteria]({% link reference/criteria.md %}){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What this is

Foundation model development is dominated by well-funded commercial labs, which brings data opacity, licensing constraints, and architectural gatekeeping along with it. In response, a number of universities, national labs, and non-profit research consortia have pretrained large language models **from scratch**: random weights, own data, own tokenizer, full pipeline auditability.

This registry tracks those models, and only those models. **Academic means a university.** Universities come first, with research institutes, national labs, and public consortia tracked in separate sections below the academic list.

The defining rule is strict: a model qualifies only if it was trained from a *tabula rasa* state. Continued pretraining on a commercial base, however substantial, however good the resulting model, does not qualify. That rule is what makes the list answer something worth knowing. [Read the reasoning]({% link reference/criteria.md %}).

## Where to start

| If you want | Go to |
|:---|:---|
| The list itself, one line per model | [readme](https://github.com/Kentucky-Open-Science/native_research_llms#readme) |
| How universities rank on IFEval vs GPT-3.5 | [Rankings]({% link rankings.md %}) |
| Architecture, attention, positional embeddings, activations | [Architectures]({% link reference/architectures.md %}) |
| Corpora, token volumes, tokenizers, compute clusters | [Corpora & compute]({% link reference/corpora.md %}) |
| Why a model you expected isn't here | [Inclusion criteria]({% link reference/criteria.md %}) |
| From-scratch models that miss a verified bar | [Unverified candidates]({% link unverified.md %}) |
| Deep dives on notable training runs | [Case studies]({% link case-studies/index.md %}) |

## What the data shows

A few patterns are visible once the models are lined up side by side.

**Compute sovereignty is regional.** European academic pretraining concentrates on a handful of public supercomputers (LUMI, MareNostrum 5, ALPS, Jean Zay), and the models that come out of them are shaped by those allocations. Japan's runs go through ABCI and Fugaku. This is national research infrastructure being exercised, and the model list doubles as a map of who has it.

**Tokenizers are where the linguistics lives.** The most consistent finding across non-English academic models is that they build their own tokenizer, and say why. Vocabulary sizes range from 30K to 256K, and the large ones are almost always multilingual or morphologically-rich-language projects buying back sequence length that an English-centric BPE would waste.

**Architecture converges; data doesn't.** Nearly every recent entry is a decoder-only transformer with grouped-query attention, rotary embeddings, and SwiGLU. The differentiation is almost entirely in the corpus, the tokenizer, and the training discipline, which is precisely what a from-scratch run gets you control over and a fine-tune does not.

## Contributing

Additions and corrections are both welcome, and are held to the same standard: **public, checkable evidence**. Entries that fail verification are removed rather than footnoted.

See [contributing.md](https://github.com/Kentucky-Open-Science/native_research_llms/blob/main/contributing.md).

---

Released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Model names and trademarks belong to their respective institutions.
