---
title: Home
nav_order: 1
description: A registry of large language models pretrained from scratch by universities, non-profit research institutes, and national laboratories.
permalink: /
---

# Academic & Research LLMs
{: .fs-9 }

Which non-commercial institutions have actually built a foundation model end to end — and what did it take?
{: .fs-6 .fw-300 }

[The list]({{ site.aux_links['View on GitHub'][0] }}#readme){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Inclusion criteria](reference/criteria.html){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## What this is

Foundation model development is dominated by well-funded commercial labs, which brings data opacity, licensing constraints, and architectural gatekeeping along with it. In response, a number of universities, national labs, and non-profit research consortia have pretrained large language models **from scratch** — random weights, own data, own tokenizer, full pipeline auditability.

This registry tracks those models, and only those models.

The defining rule is strict: a model qualifies only if it was trained from a *tabula rasa* state. Continued pretraining on a commercial base — however substantial, however good the resulting model — does not qualify. That rule is what makes the list answer something worth knowing. [Read the reasoning](reference/criteria.html).

## Where to start

| If you want | Go to |
|:---|:---|
| The list itself, one line per model | [readme]({{ site.aux_links['View on GitHub'][0] }}#readme) |
| Architecture, attention, positional embeddings, activations | [Architectures](reference/architectures.html) |
| Corpora, token volumes, tokenizers, compute clusters | [Corpora & compute](reference/corpora.html) |
| Why a model you expected isn't here | [Inclusion criteria](reference/criteria.html) |
| Deep dives on notable training runs | [Case studies](case-studies/) |

## What the data shows

A few patterns are visible once the models are lined up side by side.

**Compute sovereignty is regional.** European academic pretraining concentrates on a handful of public supercomputers — LUMI, MareNostrum 5, ALPS, Jean Zay — and the models that come out of them are shaped by those allocations. Japan's runs go through ABCI and Fugaku. This is national research infrastructure being exercised, and the model list doubles as a map of who has it.

**Tokenizers are where the linguistics lives.** The most consistent finding across non-English academic models is that they build their own tokenizer, and say why. Vocabulary sizes range from 30K to 256K, and the large ones are almost always multilingual or morphologically-rich-language projects buying back sequence length that an English-centric BPE would waste.

**Architecture converges; data doesn't.** Nearly every recent entry is a decoder-only transformer with grouped-query attention, rotary embeddings, and SwiGLU. The differentiation is almost entirely in the corpus, the tokenizer, and the training discipline — which is precisely what a from-scratch run gets you control over and a fine-tune does not.

## Contributing

Additions and corrections are both welcome, and are held to the same standard: **public, checkable evidence**. Entries that fail verification are removed rather than footnoted.

See [contributing.md]({{ site.aux_links['View on GitHub'][0] }}/blob/main/contributing.md).

---

Released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Model names and trademarks belong to their respective institutions.
