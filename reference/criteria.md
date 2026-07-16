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

The pretraining run must be led by a university, a non-profit research institute, a national laboratory, or a public research consortium.

The boundary here is genuinely fuzzy, and this list resolves ambiguity case by case rather than pretending a bright line exists:

- **MBZUAI** is a degree-granting university whose models ship with commercial partners (Inception, Cerebras, Petuum). Listed.
- **Ai2** and **EleutherAI** are non-profits, not universities. Listed — excluding them would cut the most reproducible open models in existence while admitting far less rigorous university one-offs, which would make the list worse at the thing it is for.
- **Barcelona Supercomputing Center** and **NII** are national research institutes. Listed.
- **Corporate research divisions** are excluded, even when they publish excellent papers and release open weights. FAIR, Microsoft Research, and NVIDIA Research are not in scope.

## The public-evidence rule

Every entry needs at least one canonical, resolving public link.

Private documents, internal reports, unlisted Drive files, and personal correspondence cannot establish an entry. This is not bureaucratic caution. A registry whose claims cannot be checked is not a registry, it is an assertion — and the failure mode is specific: unverifiable entries tend to carry the *most* impressive-sounding detail, because nothing constrains them.

**Gated weights are acceptable** when the gate is documented and the model is otherwise publicly described. GatorTronGPT cannot release raw weights trained on protected health information without risking re-identification of patients; that is a legitimate constraint, not evasion, and the model is thoroughly documented in the literature. Gated entries are marked as such.

## The language-model rule

Causal decoder-only, encoder-decoder, encoder-only, and diffusion language models are all in scope.

Foundation models over non-linguistic sequence data are not, however architecturally interesting. Single-cell transcriptomics models, medical imaging diffusion models, and protein language models solve different problems against different data and belong on different lists. The shared use of a transformer block is not enough to make them comparable.

## On removal

Entries that fail verification are **removed, not footnoted**.

A list that keeps a disproven entry with an asterisk has decided its own completeness matters more than its accuracy. This one has decided the opposite. If you can show that a listed model was not trained from scratch, that its institution is misattributed, or that it does not exist, please [open a correction](https://github.com/Kentucky-Open-Science/native_research_llms/issues/new?template=correction.yml) — that is a contribution of exactly the same value as an addition.
