---
title: Sumi and uniform diffusion
parent: Case studies
nav_order: 1
---

# Sumi and uniform diffusion
{: .no_toc }

Tohoku University's 7B departure from left-to-right generation.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## Why it matters

[Sumi](https://arxiv.org/abs/2606.19005) is a fully open 7B **uniform diffusion language model** pretrained from scratch on 1.5T tokens. Its authors state the gap it fills plainly: unlike autoregressive and masked-diffusion approaches, no UDLM had previously been pretrained at large scale.

That absence is the point. Autoregressive decoders commit to tokens left to right and cannot revisit them. A uniform diffusion model allows any token in a sequence to be revised at any step, which makes generation adaptive rather than strictly sequential. Whether that property survives contact with scale was, before Sumi, an open empirical question with no reference point.

It is also a change **no fine-tune can reach**. The training objective is fixed at pretraining time. You cannot adapt a causal decoder into a diffusion model by feeding it more data, at any budget. If the alternative is going to be evaluated at 7B at all, someone has to spend a full pretraining run finding out — and the institution that did was a university NLP group, not a commercial lab with a product to ship.

## The training run

Pretraining ran in three sequential stages:

| Stage | Tokens | Sequence length | Data emphasis |
|:--|:--|:--|:--|
| Pretraining | 1.3T | 1,184 | General English |
| Mid-training 1 | 130B | 1,184 | Math, code, logical reasoning |
| Mid-training 2 | 120B | 4,864 | Math, code, logical reasoning |

The corpus is the English portion of llm-jp-corpus-v4, notably **excluding FineWeb subsets** in favor of documents rescored with an educational classifier distilled from Qwen3-32B annotations. A single Warmup-Stable-Decay learning rate schedule spans the whole pipeline, with an auxiliary loss term maintaining gradient stability.

The staging is worth reading as a decision rather than a detail. Extending the sequence length only in the final 120B tokens concentrates the expensive long-context work at the end, after the cheap short-context stage has already done the bulk of the learning — the same instinct visible in Dante-2B's phased context extension and in most compute-constrained academic runs. It is what optimization under a fixed, non-renewable allocation looks like.

## What it found

Sumi is competitive with comparable autoregressive models on knowledge, reasoning, and coding, and **underperforms on commonsense benchmarks**.

The honest result is the useful one. A commercial lab publishing a 7B with a known benchmark deficit would face real pressure to bury the comparison or requalify the claim; the paper reports it directly, and the mixed picture is more informative than a win would be. It says the uniform diffusion objective is viable at scale but not uniformly superior, which is exactly the kind of finding that tells the next group where to look.

Because the team released weights, checkpoints, and complete training specifications, that "where to look" is actionable rather than rhetorical. The scaling dynamics can be analyzed against autoregressive baselines by anyone, which is the entire justification for spending a public compute allocation on the question.

## Sources

- Paper: [Sumi: Open Uniform Diffusion Language Model from Scratch](https://arxiv.org/abs/2606.19005) (arXiv 2606.19005)
- Project page: [Tohoku NLP Group](https://www.nlp.ecei.tohoku.ac.jp/projects/sumi/)
- Authors: Mengyu Ye, Keito Kudo, Wataru Ikeda, Ryosuke Matsuda, Keisuke Sakaguchi, Jun Suzuki
