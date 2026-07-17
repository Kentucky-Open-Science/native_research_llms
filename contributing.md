# Contribution Guidelines

Thanks for helping build this registry. This list has a narrow, deliberate scope, so please read the criteria before opening a pull request.

## What belongs on this list

An entry must satisfy **all four** criteria.

### 1. Pretrained from scratch

The model's weights must be initialized randomly and trained from a *tabula rasa* state. This is the defining rule of the list, and it is applied strictly.

A model is **not** eligible if it was warm-started from someone else's pretrained checkpoint. That includes:

- Continued (or "continual") pretraining on a commercial base, training Llama 3.1 8B on a new language does not make a new from-scratch model.
- Vocabulary expansion plus continued pretraining.
- Fine-tuning, instruction tuning, RLHF, or LoRA adaptation of an existing base.
- Distillation from a teacher model's outputs, where the student inherits the teacher's weights.

Instruction-tuned or aligned *variants* of an eligible base model are fine to mention within that model's entry, the base is what qualifies.

If a model's provenance is ambiguous, it does not go on the list until it is resolved. "Probably from scratch" is not from scratch.

### 2. Academic or non-commercial research lead

The pretraining run must be led by a university, a non-profit research institute, a national laboratory, or a public research consortium. Examples of qualifying leads: ETH Zürich, Ai2, EleutherAI, Barcelona Supercomputing Center, Japan's National Institute of Informatics, AI Sweden.

Industry *collaboration* is expected and fine, academic pretraining runs routinely depend on hardware partners and cloud credits. What matters is that the research lead and the scientific direction are academic. A model developed by a company's research division and merely published at a conference does not qualify.

### 3. Publicly documented

Every entry needs at least one canonical, resolving public link: a Hugging Face model repository, a GitHub repository, an arXiv paper, or an official project page.

Citations to private documents, unlisted Drive files, internal reports, or personal correspondence are not acceptable evidence. If the public cannot check the claim, it does not go on the list.

Gated weights are acceptable *if* the gate is documented and the model is otherwise publicly described, some clinical models cannot release weights trained on protected health information. Mark these clearly.

### 4. It's actually a language model

Causal decoder-only, encoder-decoder, encoder-only, and diffusion language models are all in scope. Models over non-linguistic sequence data (genomics, medical imaging, protein structure) are out of scope, however interesting their architecture.

## How to add a model

1. Open the [add-a-model issue](https://github.com/Kentucky-Open-Science/native_research_llms/issues/new?template=add-model.yml) first if you want to check fit before doing the work.
2. Fork, then add your entry to the appropriate section of `readme.md`, in alphabetical order within that section.
3. Match the existing format exactly:

   ```markdown
   - [Model Name](https://huggingface.co/org/model), One sentence, ending with a period. `Institution` `params` `year`
   ```

4. Keep the description to one sentence, factual and neutral. No marketing language, no "state-of-the-art", no "revolutionary". Say what it is and what makes it distinct.
5. In your pull request description, include **evidence for the from-scratch claim**, a link to the paper section, model card statement, or training config that shows random initialization. This is the one thing every PR is checked on, so please don't skip it.
6. If your model belongs in the reference tables, update `reference/architectures.md` and `reference/corpora.md` too. Leave a cell as `Not disclosed` rather than guessing.

## Corrections

Corrections are as welcome as additions, and are reviewed with the same rigor. If a model on this list was **not** actually trained from scratch, please open a [correction issue](https://github.com/Kentucky-Open-Science/native_research_llms/issues/new?template=correction.yml) with evidence. Entries that fail verification are removed, not quietly footnoted.

## Quality bar

- Every claim traces to a public source.
- Parameter counts, token volumes, and hardware refer to the *pretraining* run, not later stages.
- Prefer the model card and the paper over blog posts, press releases, and secondary coverage.
- `Not disclosed` is a perfectly good value. An honest gap is more useful than a confident guess.

## Pull request checks

CI runs [awesome-lint](https://github.com/sindresorhus/awesome-lint) and a link checker on every PR. Please make sure both pass. You can run them locally:

```sh
npx awesome-lint
npx markdown-link-check readme.md
```
