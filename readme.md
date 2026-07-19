# The Academic Foundation Model Index (AFMI) [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> An index of foundation models trained natively, from scratch, on their own data and tokenizer, by academic and research institutions. Universities come first; research institutes, national labs, and public consortia are tracked alongside.

Foundation model development is dominated by well-funded commercial labs, and data opacity, licensing constraints, and architectural gatekeeping come with it. In response, universities and other public institutions have pretrained large language models from a *tabula rasa* state: random weights, own corpus, own tokenizer, auditable end to end.

**Academic means a university.** This list puts universities first, because that is the question worth asking: *which universities have actually built a foundation model end to end?* Non-profit research institutes, national laboratories, government institutes, and think tanks (Ai2, EleutherAI, BAAI, TII, NII, and the like) do serious from-scratch work and are tracked here, but in a **separate section below**, because they are not universities.

The from-scratch rule is strict: continued pretraining on a commercial base does not qualify, however substantial the training that follows. Reusing an architecture is fine; inheriting weights is not. A verified entry also has **openly downloadable weights** and roughly **1B+ parameters**. A commercial co-developer does not move a university off the first list; the partner is noted inline. See the [inclusion criteria](reference/criteria.md), the [architectures](reference/architectures.md) and [corpora](reference/corpora.md) specifications, and the [unverified candidates](unverified.md) that miss a bar.

Entries marked **⚠** carry a caveat worth reading before you rely on them, usually a restrictive license or a documented access constraint.

## Contents

- [Rankings](#rankings)
- [Universities](#universities)
- [Research institutes and national labs](#research-institutes-and-national-labs)
- [Public research consortia](#public-research-consortia)
- [Related](#related)

## Rankings

The headline metric is **IFEval strict-avg** (instruction-following accuracy, the Open LLM Leaderboard's "IFEval" column), measured against the original-ChatGPT line, **GPT-3.5-turbo-1106 = 55.9**. It asks one question: *has a from-scratch university model reached what made ChatGPT usable?*

### Academic-only

No commercial partner, no corporate-donated compute. University teams on university or public
compute. **This is the headline ranking.**

| IFEval | MMLU | University instruction model | Institution | Train tokens |
|--:|--:|:--|:--|--:|
| **61.6** | 27.8 | **KOS-V4-Instruct (3B)** | University of Kentucky | **180B** |
| **61.5** | 52.8 | YuLan-Mini-Instruct | Renmin | undisclosed |
| *55.9* | - | *GPT-3.5-turbo-1106 (the line)* | *OpenAI* | *undisclosed* |
| 54.1 | 52.5 | LLäMmlein-7B-chat | Würzburg | undisclosed |
| 21.5 | 40.7 | Minerva-7B-instruct | Sapienza | 210B |
| 19.9 | 24.0 | CroissantLLMChat | CentraleSupélec | undisclosed |
| 15.0 | 25.9 | Tucano-2b4-Instruct | U Bonn | 200B |
| 6.0 | - | TinyLlama-1.1B-Chat | SUTD | 3T |

**Two academic-only models clear the original-ChatGPT line: KOS-V4-Instruct (61.6) and YuLan-Mini
(61.5)** — a 0.1-point separation, well inside the benchmark's ±2.1-point standard error on 541
prompts, so they are statistically tied. KOS-V4-Instruct is the only one of the two that publishes a
training token count (180B, 24 GPUs). Minerva is academic-only but state-resourced (Italy's PNRR/FAIR
programme, CINECA).

### University-led, commercially backed

Same from-scratch rule, but a commercial partner supplied compute or engineering. **Separated because
a donated industrial training budget is not a resource a university lab can match**, and ranking the
two together measures sponsorship as much as method.

| IFEval | MMLU | Model | Institution | Train tokens | Commercial partner |
|--:|--:|:--|:--|--:|:--|
| **74.9** | - | Jais-2-70B-Chat | MBZUAI | 2.6T | Inception |
| **70.8** | 61.1 | Marin 8B Instruct | Stanford | **12.7T** | **Google** (TPU Research Cloud) |
| 51.5 | - | LLM360 K2-Chat | MBZUAI | undisclosed | Petuum |
| 34.6 | \* | Poro-34B-chat | U Turku | 1T | Silo AI |

Marin reaches 70.8 on **12.7T tokens — 71x KOS-V4-Instruct's 180B** — with TPUs provided by Google.
Jais 2 leads on 2.6T with Inception. These are strong results and belong on this site; they are not a
like-for-like comparison with a lab running 24 of its own GPUs.

IFEval strict-avg and MMLU (5-shot accuracy), as percentages; 8 of these we measured on a common pristine harness on 2026-07-18. **Four university models clear the original-ChatGPT line: Jais 2 (74.9), Marin (70.8), KOS-V4-Instruct (61.6), and YuLan-Mini (61.5).** The two benchmarks rank the set almost independently: KOS-V4 follows instructions well (3rd) but sits near the MMLU chance floor by design (it is an instruction model, not a knowledge model), while Poro-34B is the largest model here yet mid-pack on instructions. Multilingual models (Poro, Minerva, Croissant, Tucano, LLäMmlein) are measured on English and understate their designed capability. (Apertus 75.2 and SmallThinker 85.8 report IFEval in loose or unlabeled formats that are not strict-avg, so they are off the line; \* = Poro MMLU pending.)

The full tables (research institutes, a GPT-3.5-generation reference set, MMLU, format caveats, and the complete needs-eval list) are on the [rankings page](rankings.md).

## Universities

The academic list. Led by a university; a commercial co-developer is noted inline but does not disqualify.

### Fully open and reproducible

- [Marin 8B](https://github.com/marin-community/marin) - Stanford CRFM's 8B and 32B models trained on 12.7T tokens, with the entire research process (code, data, experiments, and failures) documented in the open as it happened. Compute was provided by **Google's TPU Research Cloud** (TPU v4/v5e), per the model card's acknowledgements.
- [OpenLLaMA](https://huggingface.co/openlm-research/open_llama_7b) - UC Berkeley's OpenLM Research 3B, 7B, and 13B open reproduction of LLaMA, with tokenizer and weights trained from scratch on RedPajama and RefinedWeb.
- [DCLM-7B](https://github.com/mlfoundations/dclm) - The University of Washington and ML Foundations' 7B, built with Apple, trained on 2.6T tokens as the reference model for the DataComp-LM benchmark. **⚠** Weights ship under Apple's Sample Code License, not an OSI license.
- [FinGPT](https://turkunlp.org/gpt3-finnish) - TurkuNLP (University of Turku)'s seven monolingual Finnish models from 186M to 13B, each trained on 300B tokens. Unrelated to AI4Finance's identically named financial model.
- [Tucano](https://github.com/Nkluge-correa/Tucano) - University of Bonn's Portuguese models from 160M to 2.4B, trained on the 200B-token GigaVerbo corpus.
- [LLM360 Amber](https://huggingface.co/LLM360/Amber) - MBZUAI and Petuum's 6.7B model trained on 1.3T tokens, released with 360 checkpoints from step zero onward.
- [LLM360 Crystal](https://huggingface.co/LLM360/Crystal) - MBZUAI, Petuum, and Cerebras's 6.7B language-and-code model trained on 1.4T tokens of SlimPajama and StarCoder, with 143 checkpoints.
- [LLM360 K2](https://huggingface.co/LLM360/K2) - MBZUAI and Petuum's 65B model matching Llama 2 70B on roughly 35% less training compute, with the full pipeline released.
- [LLM360 K2-V2](https://huggingface.co/LLM360/K2-V2) - MBZUAI's 70B reasoning-oriented model trained on 12.25T tokens with a 512K context window.

### Multilingual and regional

- [Apertus](https://huggingface.co/swiss-ai/Apertus-8B-2509) - EPFL and ETH Zürich's 8B and 70B models trained on 15T tokens spanning over 1,800 languages, on the CSCS Alps supercomputer.
- [Minerva](https://nlp.uniroma1.it/minerva/) - Sapienza University of Rome's 350M to 7B models, the first family trained from scratch on Italian, with the 7B seeing 2.5T tokens.
- [weblab-10b](https://huggingface.co/matsuo-lab/weblab-10b) - The University of Tokyo Matsuo Lab's 10B Japanese-English model trained on roughly 600B tokens. **⚠** Non-commercial CC BY-NC license.
- [Tanuki](https://huggingface.co/weblab-GENIAC/Tanuki-8x8B-dpo-v1.0) - The University of Tokyo Matsuo Lab and a volunteer GENIAC community's 8B dense and 8x8B MoE Japanese models pretrained fully from scratch.
- [LLäMmlein](https://huggingface.co/LSX-UniWue/LLaMmlein_1B) - The University of Würzburg's 1B and 7B German models trained transparently from scratch with a custom German tokenizer. **⚠** Research-only RAIL-M license.
- [YuLan-Base-12B](https://github.com/RUC-GSAI/YuLan-Chat) - Renmin University of China's 12B bilingual model trained on roughly 1.7T tokens. **⚠** The readme restricts use to academic purposes, contradicting the MIT license file.
- [AraGPT2](https://github.com/aub-mind/arabert) - American University of Beirut's 135M to 1.46B Arabic models trained on 77GB of text, predating Llama entirely. **⚠** Custom license of unconfirmed status.
- [CroissantLLM](https://huggingface.co/croissantllm/CroissantLLMBase) - CentraleSupélec and Illuin Technology's 1.3B bilingual model trained on 3T tokens at a strict 1:1 French-English ratio, released with the FrenchBench benchmark.
- [Fugaku-LLM](https://huggingface.co/Fugaku-LLM/Fugaku-LLM-13B) - Tokyo Institute of Technology and Tohoku University's 13B, trained with RIKEN and Fujitsu on the Fugaku supercomputer's CPUs, with Megatron-DeepSpeed ported to run on it.
- [Jais](https://huggingface.co/inceptionai/jais-13b) - MBZUAI's 13B Arabic-English model, built with Inception and Cerebras, trained on 395B tokens with a 150K Arabic-centric vocabulary.
- [Jais 2](https://huggingface.co/inceptionai/Jais-2-70B-Chat) - MBZUAI and Inception's 8B and 70B Arabic models trained from scratch on 2.6T tokens on the Condor Galaxy clusters.
- [Poro 34B](https://huggingface.co/LumiOpen/Poro-34B) - TurkuNLP (University of Turku)'s 34B, built with Silo AI and HPLT, trained on 1T tokens of Finnish, English, and code on LUMI. The Llama-derived Poro 2 does not qualify.
- [Viking](https://huggingface.co/LumiOpen/Viking-33B) - TurkuNLP (University of Turku)'s 7B, 13B, and 33B models, built with Silo AI and HPLT, trained on 2T tokens covering all Nordic languages, English, and code.

### Biomedical and clinical

- [KOS-V4](https://huggingface.co/collections/Kentucky-Open-Science/kos-v4-llm) - The University of Kentucky College of Medicine's 3B decoder trained from scratch on 180B tokens of medical text (base KOS-V4-Base, 24 GPUs). Its GRPO-tuned Instruct variant scores 61.6 IFEval strict-avg, clearing the original GPT-3.5-turbo. **⚠** Non-commercial, research-only (CC BY-NC-SA).
- [BioMedLM](https://huggingface.co/stanford-crfm/BioMedLM) - Stanford CRFM's 2.7B trained solely on PubMed with a purpose-built 28,896-token biomedical vocabulary, small enough to deploy privately. **⚠** The BLOOM RAIL license forbids using it to provide medical advice.
- [GatorTronGPT](https://github.com/uf-hobi-informatics-lab/GatorTronGPT) - University of Florida's 5B and 20B trained on 277B words including 82B words of UF Health clinical notes. **⚠** Weights gated behind UF licensing because of PHI provenance, a documented data-protection exception; the open artifact is the 345M GatorTronS.

### Small and efficient

- [TinyLlama-1.1B](https://github.com/jzhang38/TinyLlama) - Singapore University of Technology and Design's 1.1B trained on up to 3T tokens, reusing Llama 2's architecture and tokenizer for ecosystem compatibility.
- [YuLan-Mini](https://github.com/RUC-GSAI/YuLan-Mini) - Renmin University of China's data-efficient 2.4B trained on 1.08T tokens, released with training code, checkpoints, and optimizer states.
- [SmallThinker](https://github.com/SJTU-IPADS/SmallThinker) - Shanghai Jiao Tong University and Zenergize AI's 4B and 21B MoE models designed natively for local hardware, exceeding 20 tokens/second on consumer CPUs via pre-attention expert prefetching.

### Alternative architectures and objectives

- [Sumi](https://huggingface.co/tohoku-nlp/sumi-7b) - Tohoku University's 7B uniform diffusion language model trained on 1.5T tokens, letting any token be revised at any step rather than fixing text left to right. The first UDLM pretrained at this scale.
- [Mamba](https://github.com/state-spaces/mamba) - Carnegie Mellon and Princeton's 130M to 2.8B selective state-space models (Mamba and Mamba-2), the reference implementation of the SSM alternative to attention, trained on the Pile.
- [H3](https://huggingface.co/danfu09/H3-1.3B) - Stanford Hazy Research's 125M to 2.7B state-space models trained on 400B tokens of the Pile, a direct precursor to Mamba.
- [Based](https://huggingface.co/hazyresearch/based-1b) - Stanford Hazy Research's up-to-1.4B models pairing linear attention with a tiny sliding window, trained from scratch for efficient-architecture research.
- [Plaid](https://github.com/igul222/plaid) - Stanford's roughly 1B continuous-diffusion language model pretrained on OpenWebText2, the first diffusion LM to beat GPT-2 124M in likelihood.
- [LLaDA](https://huggingface.co/GSAI-ML/LLaDA-8B-Base) - Renmin University of China and Ant Group's 8B masked-diffusion language model pretrained from scratch on 2.3T tokens, competitive with LLaMA3 8B and the largest from-scratch academic diffusion LM to date.
- [GLA](https://huggingface.co/fla-hub/gla-2.7B-100B) - MIT and the MIT-IBM Watson AI Lab's 1.3B and 2.7B gated-linear-attention models trained on SlimPajama, a sub-quadratic alternative to softmax attention.

## Research institutes and national labs

Serious from-scratch work by non-profit institutes, national labs, government institutes, and foundations. In the registry, but **not universities**, so not part of the academic list above.

### Fully open and reproducible

- [Pythia](https://github.com/EleutherAI/pythia) - EleutherAI's suite of 16 models from 70M to 12B, trained on identical data in identical order, with 154 public checkpoints each for interpretability research.
- [GPT-NeoX-20B](https://huggingface.co/EleutherAI/gpt-neox-20b) - EleutherAI's 20B model trained on the Pile, the largest dense autoregressive model with publicly available weights at its release.
- [GPT-J-6B](https://huggingface.co/EleutherAI/gpt-j-6b) - EleutherAI's 6B model trained on the Pile with Mesh Transformer JAX, alongside the earlier 1.3B and 2.7B GPT-Neo models.
- [OLMo 3](https://huggingface.co/allenai/Olmo-3-1125-32B) - Ai2's 7B and 32B family released with the complete Dolma 3 training data, code, and every intermediate checkpoint.
- [OLMo 2](https://huggingface.co/allenai/OLMo-2-1124-7B) - Ai2's 7B, 13B, and 32B models trained from scratch on OLMo-Mix-1124, the generation that added the 13B and 32B scales to the family.
- [OLMo](https://huggingface.co/allenai/OLMo-7B) - Ai2's original 1B and 7B models trained on Dolma, the first fully-open OLMo generation, released with data, code, and checkpoints.
- [OLMo Hybrid 7B](https://huggingface.co/allenai/Olmo-Hybrid-7B) - Ai2's 7B interleaving attention with Gated DeltaNet linear-RNN layers, pretrained on 6T tokens at roughly twice the data efficiency of OLMo 3.
- [MAP-Neo 7B](https://github.com/multimodal-art-projection/MAP-NEO) - The M-A-P open collective and University of Waterloo's bilingual 7B trained on 4.5T tokens, releasing the Matrix corpus and data pipeline alongside the weights. **⚠** No license file, despite the readme claiming MIT.
- [FORGE](https://github.com/at-aaims/forge) - Oak Ridge National Laboratory's 1.4B to 22.4B scientific models trained on 257B tokens from over 200M scientific articles on the Frontier supercomputer. **⚠** Weights ship without a license file.

### Multilingual and regional

- [Polyglot-Ko](https://huggingface.co/EleutherAI/polyglot-ko-12.8b) - EleutherAI's 1.3B to 12.8B Korean models trained on 1.2TB of Korean text with a purpose-built 30K-token Korean tokenizer.
- [Aquila2](https://github.com/FlagAI-Open/Aquila2) - BAAI's 7B, 34B, and 70B bilingual models trained on roughly 1.8T tokens, weighted toward native rather than translated Chinese knowledge. **⚠** Weights use a custom BAAI license.
- [CPM-1](https://github.com/TsinghuaAI/CPM-Generate) - Tsinghua University and BAAI's 2.6B Chinese model from 2020, trained on 100GB of text with a purpose-built Chinese sub-word tokenizer.
- [Salamandra](https://huggingface.co/BSC-LT/salamandra-7b) - The Barcelona Supercomputing Center's 2B and 7B models trained on 12.875T tokens across 35 European languages and code, with a 40B sibling released as ALIA-40b.
- [PULI GPT-3SX](https://huggingface.co/NYTK/PULI-GPT-3SX) - The Hungarian Research Centre for Linguistics's 6.7B Hungarian model trained on 36.3B words with GPT-NeoX. **⚠** License signals conflict across the readme, the model card, and the institute's site.
- [LLM-jp-3](https://huggingface.co/llm-jp/llm-jp-3-13b) - Japan's National Institute of Informatics's 13B trained on 2.1T tokens, released as a fully open model including data and training process.
- [LLM-jp-4](https://www.nii.ac.jp/en/news/release/2026/0403.html) - NII's 8.6B dense and 32B MoE models trained on 10.5T tokens on ABCI 3.0, with reasoning variants using the Harmony channel format.
- [ALLaM-7B](https://huggingface.co/humain-ai/ALLaM-7B-Instruct-preview) - Saudi Arabia's National Center for AI at SDAIA's 7B Arabic-English model trained on 5.2T tokens. The 13B and 70B variants are Llama-2-initialized and do not qualify.
- [Falcon](https://huggingface.co/tiiuae/falcon-40b) - TII Abu Dhabi's 7B and 40B models trained on curated web data under Apache 2.0. **⚠** The 180B uses a restrictive custom license; training code was never released.
- [SEA-LION v1](https://huggingface.co/aisingapore/SEA-LION-v1-7B) - AI Singapore's 3B and 7B Southeast Asian models trained on 980B tokens with a custom SEABPETokenizer. Versions 2 and 3 are Llama-derived and do not qualify.
- [InternLM2](https://github.com/InternLM/InternLM) - Shanghai AI Laboratory and SenseTime's 1.8B, 7B, and 20B bilingual models with 200K context, trained on up to 2.6T tokens with a custom tokenizer. The Qwen-derived Intern-S1 line does not qualify.
- [Lucie-7B](https://huggingface.co/OpenLLM-France/Lucie-7B) - CNRS and CEA's 7B French-English model, coordinated by LINAGORA under OpenLLM-France, trained from scratch on Jean Zay with checkpoints from step zero.

### Small and efficient

- [InternLM3-8B](https://huggingface.co/internlm/internlm3-8b-instruct) - Shanghai AI Laboratory's 8B trained on only 4T tokens, cutting training cost by over 75% against comparable models.

### Alternative architectures and objectives

- [RWKV](https://huggingface.co/RWKV) - The RWKV project's attention-free linear-RNN models up to 14B, trained from scratch on up to 3.1T tokens under the Linux Foundation. **⚠** Led by an individual maintainer rather than an institution.

## Public research consortia

Named multi-party public consortia, funded and staffed across several institutions and sometimes industry members.

- [BLOOM](https://huggingface.co/bigscience/bloom) - BigScience's 176B trained on the ROOTS corpus across 59 languages by a thousand-researcher consortium on France's Jean Zay supercomputer. **⚠** Released under the BigScience RAIL license, which carries behavioral use restrictions.
- [EuroLLM](https://eurollm.io/) - The EuroLLM consortium (Instituto Superior Técnico, Unbabel, Edinburgh)'s 1.7B, 9B, and 22B models covering all 24 official EU languages plus 11 more, trained on EuroHPC infrastructure.
- [HPLT models](https://github.com/hplt-project) - A Horizon Europe consortium's 2.15B decoder models covering 38 languages, trained on LUMI from the HPLT and FineWeb corpora.
- [Teuken-7B](https://huggingface.co/openGPT-X/Teuken-7B-instruct-research-v0.4) - The OpenGPT-X consortium's (Fraunhofer, TU Dresden, Jülich, with IONOS and Aleph Alpha) 7B model trained from scratch on 6T tokens across all 24 official EU languages.

## Related

- [Awesome LLM](https://github.com/Hannibal046/Awesome-LLM) - Broad list of large language models, commercial and academic.
- [Awesome Open Source LLMs](https://github.com/eugeneyan/open-llms) - Open LLMs licensed for commercial use.
- [LLM360](https://www.llm360.ai/) - Open-source LLM initiative publishing complete training pipelines.
- [Open LLM Leaderboard](https://huggingface.co/spaces/open-llm-leaderboard/open_llm_leaderboard) - Community benchmarks for open models.

## Contributing

Contributions are welcome. Read the [contribution guidelines](contributing.md) first, additions must include evidence of from-scratch pretraining, and corrections are held to the same standard as additions.
