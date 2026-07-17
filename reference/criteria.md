---
title: Inclusion criteria
nav_order: 2
---

# Inclusion criteria
{: .no_toc }

Why this list is small, and why that is the point.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## The from-scratch rule

A model qualifies only if its weights were **initialized randomly** and trained from a *tabula rasa* state.

This is the entire reason the list exists. Without the rule, "academic LLM" collapses into "someone at a university ran a fine-tune", which describes thousands of artifacts and tells you nothing about institutional capability. With the rule, the list answers a specific and much harder question: *which non-commercial institutions have actually built a foundation model end to end?*

That question matters because the interesting properties of a model — data provenance, tokenizer design, licensing freedom, auditability of the full training pipeline — are determined at pretraining time. A model warm-started from a commercial checkpoint inherits that checkpoint's data opacity and its license, no matter how much subsequent training it receives. You cannot audit what you did not train.

### What disqualifies a model

- **Continued pretraining** on someone else's base. Training Llama 3.1 8B on 100B tokens of a new language produces a genuinely useful model and a legitimate research contribution. It does not produce a from-scratch model, and it remains subject to Meta's license.
- **Vocabulary expansion plus continued pretraining.** Common in non-English adaptation. Still warm-started.
- **Fine-tuning, instruction tuning, RLHF, LoRA.** These are post-training stages.
- **Ambiguous provenance.** If the paper and model card do not establish random initialization, the model waits outside until someone establishes it.

### What does not disqualify a model

- **Industry collaboration.** Academic pretraining runs depend on hardware partners, cloud credits, and engineering support from vendors. Jais was trained with Cerebras; BioMedLM with MosaicML; Fugaku-LLM with Fujitsu. What matters is that the research lead and scientific direction are academic.
- **Reusing an architecture.** Building on the Llama *architecture* while training the *weights* from random init is from-scratch. Architecture is a published design; weights are the artifact. Nearly every model here reuses an architecture, and that is normal science.
- **Instruction-tuned variants.** If the base qualifies, its aligned descendants are mentioned within the same entry.

## The institutional rule

**Academic means a university.** The first list is universities only — the question the registry exists to answer is *which universities have built a foundation model end to end*.

Everything else non-commercial is tracked too, but in separate sections and not labeled "academic":

- **Universities** — the academic list. Degree-granting universities. MBZUAI, Instituto Superior Técnico, CentraleSupélec, SUTD, SJTU, EPFL, ETH Zürich, Sapienza, and the rest all count. A commercial co-developer does **not** move a university off this list — the partner is recorded inline as a tag, not a demotion.
- **Research institutes and national labs** — a separate section. Non-profit research institutes, national laboratories, government research institutes, and foundations: Ai2, EleutherAI, BAAI, TII, NII, SDAIA, AI Singapore, Shanghai AI Lab, Oak Ridge, the Barcelona Supercomputing Center, and the like. These do serious from-scratch work — Ai2's OLMo and EleutherAI's Pythia are among the most reproducible models in existence — but they are **not universities**, so they are not on the academic list.
- **Public research consortia** — a third section. Named multi-party public efforts: BigScience, OpenGPT-X, the EuroHPC projects.
- **Corporate research divisions** are excluded entirely, even when they publish excellent papers and release open weights. FAIR, Microsoft Research, and NVIDIA Research are not in scope.

Using commercial cloud or vendor hardware does not change who led a run; leadership does, not the invoice.

## The public-evidence rule

Every entry needs at least one canonical, resolving public link.

Private documents, internal reports, unlisted Drive files, and personal correspondence cannot establish an entry. This is not bureaucratic caution. A registry whose claims cannot be checked is not a registry, it is an assertion — and the failure mode is specific: unverifiable entries tend to carry the *most* impressive-sounding detail, because nothing constrains them.

## The verified-weights and scale rules

A verified entry has **openly downloadable weights** and roughly **1B or more parameters**.

Weights that are gated behind approval, region-locked, or never released do not meet the bar. Nor does a sub-1B research prototype, however influential — the reference implementations of alternative architectures often land here. Neither is *disqualifying*: a model that clears the from-scratch rule but misses one of these lands on the [unverified candidates]({% link unverified.md %}) list, held until the blocking condition changes. That is a different fate from a from-scratch failure, which is removed outright.

The one exception to open weights is a documented **data-protection** constraint. GatorTronGPT cannot release raw weights trained on protected health information without risking re-identification of patients; that PHI gate is a legitimate constraint, not evasion, and the model is thoroughly documented in the literature, so it stays on the verified list, marked as such. The exception is narrow — it covers legally protected training data, not ordinary access controls.

## The language-model rule

Causal decoder-only, encoder-decoder, encoder-only, and diffusion language models are all in scope.

Foundation models over non-linguistic sequence data are not, however architecturally interesting. Single-cell transcriptomics models, medical imaging diffusion models, and protein language models solve different problems against different data and belong on different lists. The shared use of a transformer block is not enough to make them comparable.

## On removal

Entries that fail verification are **removed, not footnoted**.

A list that keeps a disproven entry with an asterisk has decided its own completeness matters more than its accuracy. This one has decided the opposite. If you can show that a listed model was not trained from scratch, that its institution is misattributed, or that it does not exist, please [open a correction](https://github.com/Kentucky-Open-Science/native_research_llms/issues/new?template=correction.yml) — that is a contribution of exactly the same value as an addition.
