# Data Availability

## Purpose of this repository

This repository is a reproducibility companion for the dissertation **Unspoken Rules: Do AI Alignment Datasets Contain the Same Implicit Normative Structures That Govern Natural Human Reasoning?** It contains the code, prompts, documentation, small result tables, and validation outputs needed to understand and inspect the analytical workflow.

## Files included here

The public repository includes:

- analysis notebooks and supporting code;
- LLM extraction, decontextualisation, and topic-labelling prompts;
- package and environment requirements;
- exclusion criteria and topic-exclusion records;
- final topic summaries, comparison tables, and validation outputs;
- figure and table-generation code; and
- documentation describing the primary analysis and alternative exploratory runs.

## Files intentionally not included

Some source, intermediate, and rule-level files are too large for practical storage in a standard GitHub repository. These include raw downloaded text tables, API checkpoint files, full extracted-rule tables, per-rule topic-assignment tables, and embedding arrays.

These files are retained in the project archive in Google Drive and local project storage. They are not required to read, inspect, or reproduce the reported summary results from this repository.

## Reproducing the workflow

The notebooks document the pipeline from the original CMV and HH-RLHF source datasets through rule extraction, decontextualisation, joint BERTopic modelling, topic validation, and comparative analysis. A re-run may not reproduce API-generated wording character-for-character because the pipeline uses a hosted LLM. For this reason, the archived final analytic files are retained alongside the public code and result tables.

## Access to large files

The full analytical files underlying the reported results are retained by the author and can be made available on reasonable request, subject to the terms governing the original source datasets and any platform restrictions.

## Security

No API keys, passwords, personal credentials, or private configuration files are included in this repository.

