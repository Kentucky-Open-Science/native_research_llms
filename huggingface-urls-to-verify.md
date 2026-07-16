# Hugging Face URLs pending verification

`huggingface.co` is blocked at the TLS layer from the network this list was built on (DNS resolves; the handshake fails). Every URL below was therefore established from search-engine result titles, the models' papers, or verified GitHub readmes — **not** by fetching the page.

Everything else in this repository was verified directly: arXiv, GitHub, Nature/npj, and project pages all returned HTTP 200.

## You probably don't need to do this by hand

The `lint` workflow runs [lychee](https://github.com/lycheeverse/lychee-action) against every markdown file on GitHub's runners, which are not behind this block. It will check every URL below automatically on the first push and fail the build on any that 404. Re-run it any time from the Actions tab.

This file exists for the cases CI can't settle: a URL that resolves but points at the *wrong* model, a repo that has been renamed with a redirect still in place, or gated repos that return 200 to an anonymous checker but require an access request in practice.

## Confidence tiers

Not all of these are equally uncertain.

**Tier 1 — quoted in the paper itself.** The repo ID appears verbatim in the model's own arXiv text. Effectively primary-source; a 404 here would mean the authors mis-stated their own repo.

- `PowerInfer/SmallThinker-21BA3B-Instruct` — note the id drops hyphens (`21BA3B`, not `21B-A3B`), and the org is **PowerInfer**, not SJTU
- `PowerInfer/SmallThinker-4BA0.6B-Instruct`

**Tier 2 — search-result titles of the form `org/model · Hugging Face`.** The page exists and is indexed under that exact path. Low risk.

**Tier 3 — pattern-inferred from a sibling repo.** Highest risk; these are the ones worth your attention.

- `sapienzanlp/Minerva-350M-base-v1.0` — inferred from the 1B/7B naming pattern; not seen in results
- `sapienzanlp/Minerva-3B-base-v1.0` — same
- `ALLaM-AI/ALLaM-7B-Instruct-preview` — mirror `humain-ai/ALLaM-7B-Instruct-preview` also reported
- `ViraIntelligentDataMining/PersianLLaMA-7B` — **could not be confirmed to exist at all**; only the 13B surfaced, and the 13B is the LoRA variant that does *not* qualify. This model is currently **off the list** for that reason.

## Checklist

Tick these off as you confirm. A ✗ means: open a correction, don't quietly patch the URL — if a repo is missing, the entry's evidence may be weaker than it looks.

### Fully open and reproducible

- [ ] `EleutherAI/pythia-6.9b` (+ the 70m–12b ladder, and `-deduped` variants)
- [ ] `EleutherAI/gpt-neox-20b`
- [ ] `EleutherAI/gpt-j-6b`
- [ ] `EleutherAI/gpt-neo-1.3B`, `EleutherAI/gpt-neo-2.7B`
- [ ] `allenai/Olmo-3-1025-7B` — **date stamps are inconsistent**; the 7B is `1025`, the 32B is `1125`. `Olmo-3-1125-7B` will 404.
- [ ] `allenai/Olmo-3-1125-32B`
- [ ] `allenai/Olmo-3-7B-Instruct`, `allenai/Olmo-3-7B-Think`, `allenai/Olmo-3-32B-Think`
- [ ] `allenai/Olmo-3.1-32B-Think`, `allenai/Olmo-3.1-32B-Instruct` — post-training only, folded into the OLMo 3 entry
- [ ] `allenai/Olmo-Hybrid-7B` — note the `-7B` suffix moves to the **end**
- [ ] `marin-community/marin-8b-base`, `marin-community/marin-8b-instruct`
- [ ] `LLM360/Amber`, `LLM360/AmberChat`, `LLM360/AmberSafe`
- [ ] `LLM360/Crystal` — canonical; `CrystalCoder` was **renamed** to this. Chat variant: `LLM360/CrystalChat`
- [ ] `LLM360/K2`, `LLM360/K2-Chat`
- [ ] `LLM360/K2-V2`, `LLM360/K2-V2-Instruct`
- [ ] `m-a-p/neo_7b` (+ `neo_7b_instruct_v0.1`, `neo_7b_sft_v0.1`, `neo_2b_general`, `m-a-p/Matrix`)
- [ ] `TurkuNLP/gpt3-finnish-small` (+ `-medium`, `-large`, `-xl`, `-3B`, `-8B`, `-13B`)
- [ ] `TucanoBR/Tucano-160m` (+ `-630m`, `-1b1`, `-2b4`)
- [ ] `apple/DCLM-7B`, `apple/DCLM-Baseline-7B`

### Multilingual and regional

- [ ] `swiss-ai/Apertus-8B-2509`, `swiss-ai/Apertus-70B-2509` (+ `-Instruct-2509`)
- [ ] `utter-project/EuroLLM-9B`, `utter-project/EuroLLM-22B-2512` (+ `-Instruct` variants)
- [ ] `BSC-LT/salamandra-7b`, `BSC-LT/salamandra-2b` (+ `-instruct`)
- [ ] `BSC-LT/ALIA-40b` — **`BSC-LT/salamandra-40b` does not exist**; the 40B ships under this name
- [ ] `bigscience/bloom` (+ `bloom-560m` … `bloom-7b1`)
- [ ] `LumiOpen/Poro-34B` — org is **LumiOpen**, not TurkuNLP
- [ ] `LumiOpen/Viking-33B`, `LumiOpen/Viking-7B`, `LumiOpen/Viking-13B`
- [ ] `HPLT/hplt-2.0-ukr_Cyrl-llama-2b-30bt` (representative of 38 language models)
- [ ] `sapienzanlp/Minerva-7B-base-v1.0`, `sapienzanlp/Minerva-7B-instruct-v1.0`, `sapienzanlp/Minerva-1B-base-v1.0`
- [ ] `croissantllm/CroissantLLMBase`, `croissantllm/CroissantLLMChat-v0.1`
- [ ] `AI-Sweden-Models/gpt-sw3-126m` … `-40b` — **expect friction**; AI Sweden states these are no longer openly downloadable
- [ ] `NorGLM/NorGPT-3B` — org is **NorGLM**, not NorwAI. The NorwAI org hosts the *adapted* models, which don't qualify.
- [ ] `NYTK/PULI-GPT-3SX`, `NYTK/PULI-GPTrio`
- [ ] `Fugaku-LLM/Fugaku-LLM-13B`, `Fugaku-LLM/Fugaku-LLM-13B-instruct`
- [ ] `llm-jp/llm-jp-3-13b` (+ the `llm-jp-3.1-*` series)
- [ ] `llm-jp/llm-jp-4-8b-thinking`, `llm-jp/llm-jp-4-32b-a3b-thinking` — **base repo IDs for LLM-jp-4 were not confirmed**; only the thinking variants surfaced. Worth finding the base.
- [ ] `internlm/internlm2-7b`, `internlm/internlm2-20b`, `internlm/internlm2-1_8b`
- [ ] `internlm/internlm3-8b-instruct`
- [ ] `BAAI/Aquila2-7B`, `BAAI/Aquila2-34B`, `BAAI/AquilaChat2-34B-16K`
- [ ] `TsinghuaAI/CPM-Generate`
- [ ] `yulan-team/YuLan-Base-12b`
- [ ] `inceptionai/jais-13b`, `inceptionai/jais-13b-chat` — originally `core42/*`; both orgs reported live
- [ ] `inceptionai/Jais-2-70B-Chat`, `inceptionai/Jais-2-8B-Chat` — **only `-Chat` variants surfaced; no base weights found.** Confirm whether Jais 2 base is released at all.
- [ ] `ALLaM-AI/ALLaM-7B-Instruct-preview`
- [ ] `aubmindlab/aragpt2-base` (+ `-medium`, `-large`, `-mega`)
- [ ] `tiiuae/falcon-7b`, `tiiuae/falcon-40b` (+ `falcon-180B`, restrictive license)
- [ ] `aisingapore/SEA-LION-v1-3B`, `aisingapore/SEA-LION-v1-7B`, `aisingapore/SEA-LION-v1-7B-IT`

### Biomedical and clinical

- [ ] `stanford-crfm/BioMedLM` — stale id `stanford-crfm/pubmedgpt` appears in older readmes
- [ ] `UFNLP/gatortronS` — the open 345M proxy. **GatorTronGPT itself has no HF repo**; that's expected and stated in the entry.

### Small and efficient

- [ ] `TinyLlama/TinyLlama-1.1B-intermediate-step-1431k-3T` — the final base; `TinyLlama_v1.1` is a separate 2T run
- [ ] `TinyLlama/TinyLlama-1.1B-Chat-v1.0`
- [ ] `PowerInfer/SmallThinker-21BA3B-Instruct`, `PowerInfer/SmallThinker-4BA0.6B-Instruct` (Tier 1)
- [ ] `yulan-team/YuLan-Mini`, `yulan-team/YuLan-Mini-Instruct`
- [ ] `nicholasKluge/TeenyTinyLlama-160m`, `nicholasKluge/TeenyTinyLlama-460m` — personal namespace, not an org

### Alternative objectives

- [ ] Sumi weights — the paper states weights and checkpoints were released, but **no HF repo ID surfaced**. The entry currently links the Tohoku project page instead. Worth locating.

## Non-HF items also worth a look

Not blocked by the network, but unresolved for other reasons:

- [ ] **MAP-Neo weight license** — the readme claims MIT, but the GitHub API returns `license: null` and there is no LICENSE file. Do not describe as MIT until confirmed.
- [ ] **PULI license** — three contradictory signals: readme says GPL, third-party quants tag `cc-by-nc-4.0`, the institute's site says "research purposes."
- [ ] **AraGPT2 license** — HF tag reads "custom"; OSI status unconfirmed.
- [ ] **HPLT license** — the paper says "permissive"; exact SPDX identifier never stated.
- [ ] **Caduceus parameter count** — conflicting evidence (~7.7M vs ~26M). Not currently on the list (genomics, out of scope), noted in case it comes up.
- [ ] **ESM-3 org move** — `github.com/evolutionaryscale/esm` now redirects to `github.com/Biohub/esm` with an MIT readme, which would be a license change from the original non-commercial Cambrian license. Out of scope here, but flagged.
