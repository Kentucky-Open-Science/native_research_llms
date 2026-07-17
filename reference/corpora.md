---
title: Corpora & compute
nav_order: 4
---

# Corpora and compute
{: .no_toc }

Pretraining data, tokenizers, and the machines these runs actually happened on.
{: .fs-6 .fw-300 }

<details open markdown="block">
  <summary>Contents</summary>
  {: .text-delta }
- TOC
{:toc}
</details>

## How to read this table

Token volumes refer to the **pretraining** run only, not mid-training, not annealing, not instruction tuning. Where a project reports several figures, this table takes the one the technical report defines as pretraining and notes conflicts below.

`Not disclosed` means the value was never published.

## Pretraining data and infrastructure

| Model | Cluster | Tokens | Dominant languages | Tokenizer vocab |
|:--|:--|:--|:--|:--|
| LLM360 Amber | 32× DGX A100 | 1.3T | English (SlimPajama, C4, RefinedWeb) | 32,000 |
| LLM360 Crystal | Condor Galaxy 1 (Cerebras) | 1.4T | English, code (SlimPajama, StarCoder) | 32,032 |
| LLM360 K2 | 480× A100 | 1.4T | English (TxT360) | 32,000 |
| LLM360 K2-V2 | AMD / NVIDIA custom | 12.25T | English, math, code | 32,000 |
| OLMo 3 | Ai2 | 5.9T mix (Dolma 3, ~9.3T corpus) | English, math, code | 100,277 |
| OLMo Hybrid | Ai2 | 6.0T | English, math, code | 100,277 |
| Marin | Stanford CRFM | 12.0T | English, math, code | Not disclosed |
| Pythia | EleutherAI | 300B (the Pile, ×2 dedup) | English | 50,254 |
| GPT-NeoX-20B | EleutherAI | 400B (the Pile) | English | 50,254 |
| GPT-J-6B | EleutherAI | 400B (the Pile) | English | 50,400 |
| BLOOM | **Jean Zay** (IDRIS/CNRS, 384× A100) | 366B (ROOTS) | 46 natural + 13 programming languages | 250,680 |
| Apertus | **ALPS** (CSCS, 4,096× GH200) | 15.0T | 1,811 languages | Not disclosed |
| EuroLLM | **MareNostrum 5** (400× H100) | 4.0T | 24 EU official + 11 other | Custom multilingual |
| Salamandra | **MareNostrum 5** | 12.875T | 35 European languages + code | 256,000 |
| Poro 34B | **LUMI** (512× MI250X) | 1.0T | Finnish, English, code | 128,000 |
| Viking | **LUMI** (1024× MI250X) | 2.0T | Finnish, Swedish, Danish, Norwegian, Icelandic, English, code | 128,000 |
| FinGPT | **Mahti** / LUMI (CSC) | 300B each | Finnish (monolingual) | 131,072 |
| NorGPT | NTNU Idun | ~25B | Norwegian Bokmål & Nynorsk, English | 64,000 |
| PULI GPT-3SX | HUN-REN | 36.3B words | Hungarian (monolingual) | Not disclosed |
| HPLT models | **LUMI** | 100B | 38 languages (one model each) | Not disclosed |
| Minerva | **Leonardo** (CINECA) | 2.5T | Italian 1.14T / English 1.14T / code 200B | 51,200 |
| CroissantLLM | **Jean Zay**, Adastra, Ruche | 3.0T | French–English 1:1, code | 32,000 |
| GPT-SW3 | 160× A100 (NeMo Megatron) | 320B | Swedish, Norwegian, Danish, Icelandic, English, code | 64,000 |
| Tucano | University of Bonn | 200B (GigaVerbo) | Portuguese (monolingual) | 32,000 |
| TeenyTinyLlama | PUCRS | 6.2B | Brazilian Portuguese | 32,000 |
| Fugaku-LLM | **Fugaku** (13,824 CPU nodes) | 380B | Japanese, English (Dolma), code | 60,000 |
| LLM-jp-3 | **ABCI** (H100) | 2.1T | Japanese, English, code | 96,867 |
| LLM-jp-4 | **ABCI 3.0** (AIST) | 10.5T (of ~19.5T corpus) | Japanese, English, code, multilingual | Not disclosed |
| InternLM2 | Shanghai AI Lab | 2.0–2.6T | Chinese, English, code | 92,401 |
| InternLM3 | Shanghai AI Lab | 4.0T | Chinese, English | 128,512 |
| Aquila2 | BAAI (FlagScale) | ~1.8T | Chinese ~40%, English, code | 100,008 |
| CPM-1 | 64× V100 | 100GB | Chinese (encyclopedia, news, dialogue) | 30,000 |
| YuLan-Base | Renmin University of China | ~1.7T | Chinese, English | 51,200 |
| YuLan-Mini | Renmin University of China | 1.08T | Chinese, English, math, code | 99,000 |
| Jais-13B | **Condor Galaxy 1** | 395B (116B AR / 279B EN) | Arabic, English, code | 150,272 |
| Jais 2 | **Condor Galaxy 1 & 2** (64× CS-2 each) | 2.6T | Arabic (MSA + dialect), English, code | 150,272 |
| ALLaM-7B | Megatron-LM cluster | 5.2T (4T EN → 1.2T AR/EN) | Arabic, English | Not disclosed |
| Fanar Star | QCRI | ~1.0T | Arabic, English, code | Not disclosed |
| AraGPT2 | TPUv3-128 | 77GB | Arabic (monolingual) | 64,000 |
| Falcon | AWS (up to 4,096× A100) | 1.5T (7B) / 1T (40B) / 3.5T (180B) | English, multilingual web (RefinedWeb) | 65,024 |
| SEA-LION v1 | AI Singapore | 980B | 11 Southeast Asian languages, English | 256,000 |
| TinyLlama | 16× A100-40G | 3.0T | English (SlimPajama, StarCoder) | 32,000 |
| SmallThinker | SJTU / Zenergize | 2.5T (4B) / 7.2T (21B) | English, Chinese, STEM, math | 151,936 |
| DCLM-7B | ML Foundations | 2.6T (DCLM-Baseline) | English | 50,432 |
| MAP-Neo | M-A-P | 4.5T (Matrix) | English, Chinese | 64,000 |
| BioMedLM | MosaicML cloud (128× A100) | 300B | PubMed abstracts + PubMed Central | 28,896 |
| GatorTronGPT | 560× A100 | 277B words (82B clinical) | UF Health clinical notes, English | 50,176 |
| Sumi | Tohoku University | 1.5T | English, math, code, reasoning | 151,936 |

## Known conflicts in the published record

These are places where sources disagree. The table above takes the technical report's figure; the conflict is recorded here rather than silently resolved.

- **Salamandra 7B**, some secondary sources report 7.8T tokens. The model card states 12.875T "pre-trained from scratch." The card wins.
- **TinyLlama**, the abstract says roughly 1T unique tokens over about 3 epochs; the project and body report 3T total. `TinyLlama_v1.1` is a separate 2T run, not a revision of the same model.
- **YuLan-Base-12B**, the readme says "over 1.6TB tokens," conflating bytes with tokens. The paper's ~1.7T is the citable figure.
- **LLM-jp-4**, the press release reports ~10.5T tokens used from a ~19.5T corpus, plus ~1.2T mid-training; the thinking-variant card reports 11.7T across pretraining and mid-training combined. Both are consistent once you separate the stages.
- **Jais 2**, 1.6T circulates widely but appears to be the web/math/code subset, or carried over from jais-family-30b-16k's 1.666T. The tech report's total is 2.6T.
- **SmallThinker-21B**, 2.0T circulates; the paper reports 7.2T for the 21B and 2.5T for the 4B.

## What the table shows

**This is a map of public compute.** Read the cluster column and a geography appears: LUMI for the Nordics, MareNostrum 5 for Spain and the EU consortium, ALPS for Switzerland, Jean Zay for France, Leonardo for Italy, ABCI and Fugaku for Japan, Condor Galaxy for the Gulf. Academic pretraining happens where a state built a machine and allocated it to research. The model list doubles as an inventory of which countries can do this at all.

Fugaku is the outlier worth pausing on: 13,824 **CPU** nodes, with Megatron-DeepSpeed ported to A64FX specifically to make it possible. It is the clearest demonstration on this list that the constraint is institutional access rather than any particular hardware.

**Tokenizers are where the linguistics lives.** Vocabulary sizes span 28,896 to 256,000, and the spread is not arbitrary. The large vocabularies belong to multilingual projects and morphologically rich languages buying back sequence length that an English-centric BPE would waste, Salamandra and SEA-LION at 256K, BLOOM at 250K, Jais at 150K for Arabic. The small ones belong to focused monolingual or domain runs: BioMedLM's 28,896-token PubMed vocabulary is the smallest here.

BioMedLM's vocabulary also settles its own provenance. At 28,896 tokens against GPT-2's 50,257, the embedding matrices are shape-incompatible, so a fine-tune of GPT-2 is not merely undocumented but arithmetically impossible. Several entries can be verified this way: a bespoke tokenizer is a fingerprint of a from-scratch run, because you cannot inherit weights whose vocabulary you have replaced. CroissantLLM's bilingual tokenizer, CPM's Chinese sub-word vocabulary, and TeenyTinyLlama's Portuguese SentencePiece all carry the same signature.

**From-scratch and openly available pull in opposite directions in clinical NLP.** The most rigorous clinical pretraining runs are the hardest to obtain, and the mechanism is visible in the corpus column. GatorTronGPT's 82B words of UF Health notes are what make it worth building and what make its weights ungatable, its own paper's data-availability statement lists only its encoders. BioMedLM avoided the problem by staying on published literature and still ships a license forbidding medical advice. There is no clinical model on this list that is simultaneously from scratch, open-weight, and trained on real patient records, and the corpus column explains why there cannot be.
