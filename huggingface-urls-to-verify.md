# Hugging Face URL verification

**Status: verified.** Every Hugging Face repo ID referenced by this registry has now been checked directly against the Hugging Face API (existence, gated status, and the license tag on the model card), not merely inferred from search results. The earlier TLS block on `huggingface.co` that produced this file has been cleared, and the checklist below is closed out with the results.

Everything else in the repository — arXiv, GitHub, Nature/npj, project pages — was verified directly in the original pass and returned HTTP 200.

## How this was checked

Each ID was resolved through `https://huggingface.co/api/models/<id>`, which returns existence, `gated` (`false` / `auto` click-through / `manual` approval), `disabled`, and the card's `license` tag. A `307` is a repo that was renamed or merged (the old ID still redirects). A `401` on the models API is indistinguishable between "gated and needs auth" and "does not exist" — but genuinely gated repos that *do* exist (e.g. `AI-Sweden-Models/gpt-sw3-126m`, `manual` gate) still return `200` with metadata, so a bare `401` is treated as "not publicly resolvable."

The `lint` workflow's lychee job continues to check link liveness on every push and weekly; this document covers the judgment calls lychee cannot make.

## Corrections and resolutions from this pass

Nothing on the list had to be removed. The verification **confirmed** the existing entries; the items below are refinements, redirects, and answers to the previously open questions.

**Renames (old ID still redirects, so links are not broken):**

- `PowerInfer/SmallThinker-21BA3B-Instruct` → `Tiiny/SmallThinker-21BA3B-Instruct` (org renamed PowerInfer → **Tiiny**). Same for the `4BA0.6B` variant. The readme links the GitHub repo, so no readme change is required.
- `ALLaM-AI/ALLaM-7B-Instruct-preview` → `humain-ai/ALLaM-7B-Instruct-preview` (org rebranded to **HUMAIN**). The readme link 307-redirects and still resolves; the canonical host is now `humain-ai`.
- `BSC-LT/salamandra-40b` → `BSC-LT/ALIA-40b` (the 40B ships only under the ALIA name — confirmed, as the entry already states).
- `apple/DCLM-Baseline-7B` → `apple/DCLM-7B`; `stanford-crfm/pubmedgpt` → `stanford-crfm/BioMedLM`.

**Previously open questions, now answered:**

- **LLM-jp-4 base repos exist.** `llm-jp/llm-jp-4-8b-base` and `llm-jp/llm-jp-4-32b-a3b-base` both resolve (Apache 2.0); `llm-jp/llm-jp-4-8b` redirects to the base. Only the `-thinking` variants had surfaced before.
- **Jais 2 base is not openly released.** `inceptionai/Jais-2-70B` and `-8B` return `401` (as do invented `-Base` names), while the `-Chat` variants return `200` (Apache 2.0). Only the chat weights are public; the entry correctly links `Jais-2-70B-Chat`.
- **Sumi weights located.** `tohoku-nlp/sumi-7b` (Apache 2.0), collected under `tohoku-nlp/sumi`, code at `github.com/tohoku-nlp/sumi`. The case study now links these directly instead of only the project page.
- **Minerva Tier-3 IDs confirmed.** `sapienzanlp/Minerva-350M-base-v1.0` and `-3B-base-v1.0` both exist (the naming-pattern inferences were correct).
- **Olmo 3 date stamps confirmed.** 7B is `1025`, 32B is `1125`; `allenai/Olmo-3-1125-7B` 404s, as warned.

**License tags read off the model cards:**

- `HPLT/hplt-2.0-*` → **apache-2.0** (the paper only said "permissive"; the SPDX id is now confirmed).
- `NYTK/PULI-GPT-3SX` / `PULI-GPTrio` → **cc-by-nc-4.0** on Hugging Face. The three-way conflict (readme GPL / third-party quants cc-by-nc / institute "research purposes") is real; the card itself carries `cc-by-nc-4.0`, so the ⚠ stands.
- `croissantllm/CroissantLLMBase` → **mit**. `NorGLM/NorGPT-3B` → **cc-by-nc-sa-4.0** (consistent with the Nordic-only research restriction).
- `AI-Sweden-Models/gpt-sw3-*` → `manual` gate, license `other` — confirms the "expect friction" note; access is by approval.
- `m-a-p/neo_7b` → the Hugging Face card tags **apache-2.0**, even though the GitHub repo still has no LICENSE file. The ⚠ (readme claims MIT, GitHub has no license) is about the GitHub artifact and still holds; the HF mirror being apache-2.0 is a third, separate signal.
- `aubmindlab/aragpt2-base` → **no license tag at all**; `aragpt2-mega` → `other`. OSI status remains unconfirmed; ⚠ stands.
- `BAAI/Aquila2-*` → `other` (custom BAAI license, as stated). `yulan-team/YuLan-Base-12b` → HF tag **mit**, while the readme restricts to academic use — the contradiction the entry flags is confirmed.
- `tiiuae/falcon-180B` → `auto` gate, restrictive custom license (as stated); `falcon-7b`/`40b` → apache-2.0.
- `bigscience/bloom` and `stanford-crfm/BioMedLM` → **bigscience-bloom-rail-1.0**, confirming both RAIL caveats.

**Off-list, re-confirmed:**

- **PersianLLaMA stays off** — but the earlier reasoning was imprecise. `ViraIntelligentDataMining/PersianLLaMA-13B` exists as a **full-weight** 13B (six safetensors shards, `base_model: null`, no adapter config), not a LoRA. It is disqualified because it is built on Meta's LLaMA rather than trained from scratch, not because it is an adapter. The `-7B` returns `401` (not publicly resolvable).

## Confidence tiers (retained for reference)

- **Tier 1 — quoted in the paper.** The SmallThinker IDs (`SmallThinker-21BA3B-Instruct`, `-4BA0.6B-Instruct`) — verified, now under the `Tiiny` org.
- **Tier 3 — pattern-inferred.** All resolved above: Minerva 350M/3B confirmed; ALLaM confirmed under `humain-ai`; PersianLLaMA-7B confirmed non-existent.

## Checklist (closed)

### Fully open and reproducible

- [x] `EleutherAI/pythia-*` (70m–12b, `-deduped`), `gpt-neox-20b`, `gpt-j-6b`, `gpt-neo-1.3B`/`2.7B` — apache-2.0 / mit
- [x] `allenai/Olmo-3-1025-7B`, `Olmo-3-1125-32B`, `-Instruct`/`-Think` variants, `Olmo-Hybrid-7B` — apache-2.0 (`Olmo-3-1125-7B` 404s, as warned)
- [x] `marin-community/marin-8b-base`/`-instruct` — apache-2.0
- [x] `LLM360/Amber`, `Crystal`(+`CrystalChat`), `K2`(+`K2-Chat`), `K2-V2`(+`-Instruct`) — apache-2.0
- [x] `m-a-p/neo_7b` (+ instruct/sft, `neo_2b_general`) — apache-2.0 on HF; `m-a-p/Matrix` is a **dataset**, not a model
- [x] `TurkuNLP/gpt3-finnish-*`, `TucanoBR/Tucano-*` — apache-2.0
- [x] `apple/DCLM-7B` (`DCLM-Baseline-7B` redirects here) — apple-ascl

### Multilingual and regional

- [x] `swiss-ai/Apertus-8B-2509`/`70B`/`-Instruct` — apache-2.0
- [x] `utter-project/EuroLLM-9B` (auto gate)/`1.7B`/`22B-2512` — apache-2.0
- [x] `BSC-LT/salamandra-7b`/`2b`, `BSC-LT/ALIA-40b` (40B name) — apache-2.0
- [x] `bigscience/bloom` (+ 560m…7b1) — bigscience-bloom-rail-1.0
- [x] `LumiOpen/Poro-34B`, `Viking-7B`/`13B`/`33B` — apache-2.0
- [x] `HPLT/hplt-2.0-*` — apache-2.0
- [x] `sapienzanlp/Minerva-7B`/`3B`/`1B`/`350M-base-v1.0` — apache-2.0
- [x] `croissantllm/CroissantLLMBase` — mit
- [x] `AI-Sweden-Models/gpt-sw3-126m…40b` — manual gate, other
- [x] `NorGLM/NorGPT-3B` — cc-by-nc-sa-4.0
- [x] `NYTK/PULI-GPT-3SX`, `PULI-GPTrio` — cc-by-nc-4.0
- [x] `Fugaku-LLM/Fugaku-LLM-13B` (+ instruct) — auto gate, other
- [x] `llm-jp/llm-jp-3-13b`, `llm-jp-4-8b-base`, `llm-jp-4-32b-a3b-base` (+ thinking) — apache-2.0
- [x] `internlm/internlm2-7b`/`20b`/`1_8b` (other), `internlm3-8b-instruct` (apache-2.0)
- [x] `BAAI/Aquila2-7B`/`34B`, `AquilaChat2-34B-16K` — other
- [x] `TsinghuaAI/CPM-Generate` — mit
- [x] `yulan-team/YuLan-Base-12b` — mit (readme restricts to academic — conflict noted)
- [x] `inceptionai/jais-13b`(+chat), `Jais-2-70B-Chat`/`8B-Chat` — apache-2.0; **Jais 2 base not public**
- [x] `humain-ai/ALLaM-7B-Instruct-preview` (was `ALLaM-AI/*`) — apache-2.0
- [x] `aubmindlab/aragpt2-base` (no tag) / `-mega` (other) — OSI status unconfirmed
- [x] `tiiuae/falcon-7b`/`40b` (apache-2.0), `falcon-180B` (auto gate, restrictive)
- [x] `aisingapore/SEA-LION-v1-3B`/`7B`/`7B-IT` — mit

### Biomedical and clinical

- [x] `stanford-crfm/BioMedLM` (`pubmedgpt` redirects here) — bigscience-bloom-rail-1.0
- [x] `UFNLP/gatortronS` (the open 345M proxy) — apache-2.0; GatorTronGPT itself has no HF repo, as stated

### Small and efficient

- [x] `TinyLlama/TinyLlama-1.1B-intermediate-step-1431k-3T` (+ `-Chat-v1.0`) — apache-2.0
- [x] `Tiiny/SmallThinker-21BA3B-Instruct`, `-4BA0.6B-Instruct` (was `PowerInfer/*`) — apache-2.0
- [x] `yulan-team/YuLan-Mini`(+`-Instruct`) — mit
- [x] `nicholasKluge/TeenyTinyLlama-160m`/`-460m` — apache-2.0

### Alternative objectives

- [x] `tohoku-nlp/sumi-7b` — apache-2.0 (weights + checkpoints + recipe released)

## Non-HF items — status

- [x] **MAP-Neo weight license** — GitHub still `license: null` / no LICENSE file; HF card tags apache-2.0. Readme ⚠ (GitHub artifact) stands.
- [x] **PULI license** — cc-by-nc-4.0 on the model card; three-way conflict is genuine.
- [x] **AraGPT2 license** — base has no HF license tag, mega tagged `other`; OSI status still unconfirmed.
- [x] **HPLT license** — apache-2.0 (SPDX now confirmed).
- [ ] **Caduceus parameter count** — still conflicting (~7.7M vs ~26M). Genomics, out of scope; noted only.
- [ ] **ESM-3 org move** — `evolutionaryscale/esm` → `Biohub/esm` with an MIT readme (license change from the original non-commercial Cambrian license). Out of scope; flagged.
