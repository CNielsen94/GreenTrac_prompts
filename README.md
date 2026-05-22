# GreenTrac — Prompts & Codebooks

The prompts and codebook definitions used for LLM-based policy-mix coding, extracted
from the [GreenTrac_AutoCoder](https://github.com/CNielsen94/GreenTrac_AutoCoder)
replication package.

> Madsen, S.H.J., Nielsen, C., Olsen, T., Dreyer, E., Hansen, T. & Jurowetzki, R. (2025).
> *Using large language models in policy mix analysis.*

This repository contains **only** the prompt templates and codebook definitions — none
of the coded results, ground-truth data, or analysis scripts.

## Contents

| Path | Description |
|------|-------------|
| `prompts/` | The 48 modular prompt files used for the final upscaled coding run |
| `codebook.json` | The master codebook definition used in the study |
| `iterations/iteration_1..5/codebook.json` | Per-iteration codebook definitions, tracking prompt/scheme calibration |
| `iterations/iteration_6_upscaled/prompts/` | The prompt set as used in the final (iteration 6) upscaled run — 47 files (the `03_measures/01_targets.txt` prompt is omitted in this run) |

## Prompt structure

Each prompt is a single-code, single-task template for a qualitative coding assistant.
Prompts are organized hierarchically by analytic dimension:

```
prompts/
├── 01_submission_metadata.txt
├── 02_objectives/            (7 objective codes)
├── 03_measures/
│   ├── 01_targets.txt
│   ├── 02_economic_instruments/    (7 codes)
│   ├── 03_regulatory_instruments/  (11 codes)
│   └── 04_soft_instruments/        (9 codes)
└── 04_value_chain/
    ├── 01_upstream/          (2 codes)
    ├── 02_midstream/         (4 codes)
    ├── 03_downstream/        (4 codes)
    └── 04_cross_value_chain/ (2 codes)
```

Every prompt follows the same template:

1. An expert-role preamble and task instructions.
2. A **Code Definitions** block describing each field to populate
   (`mentioned`, `timeframe_specified`, `citation`, `reasoning`, etc.).
3. An **Expected JSON Output Structure** specification.
4. A `{{DOCUMENT_TEXT}}` placeholder where the document under analysis is injected.

## Codebooks

`codebook.json` is the master codebook; the per-iteration `codebook.json` files under
`iterations/` capture how the coding scheme evolved across the six calibration
iterations of the study. They define the hierarchical code categories
(submission metadata, objectives, measures, value chain) and the fields the prompts
extract for each.

---

*Extracted from the GreenTrac_AutoCoder replication package. For coded results,
ground-truth data, and analysis scripts, see the original repository.*
