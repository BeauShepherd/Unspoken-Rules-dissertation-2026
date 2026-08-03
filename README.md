# Unspoken Rules in Human Debate and AI Alignment Data

## Overview

This repository accompanies a dissertation examining whether **AI-alignment preference data contain the same implicit normative structures that appear in natural human reasoning**.

The study uses a large-language-model pipeline to extract generalisable, implicit norms from two corpora, decontextualise those rules, and organise them with BERTopic for descriptive and comparative analysis.

## Research questions

1. **Extraction validity** — To what extent can an LLM-based pipeline extract valid, generalisable implicit norms from dialogue text?
2. **Normative structure** — What thematic structure characterises the extracted norms?
3. **Cross-corpus comparison** — How do the distributions of normative themes differ between naturalistic human debate and AI-alignment preference data?

## Data sources

- **CMV** — Reddit's r/ChangeMyView corpus, used here as a naturalistic human-debate corpus.
- **HH-RLHF** — Anthropic's Helpful and Harmless preference dataset, restricted to helpful preference data, used here as an AI-alignment preference corpus.

## Pipeline at a glance

1. Obtain and screen source data using documented exclusion criteria.
2. Use Claude Haiku to extract generalisable implicit normative propositions.
3. Decontextualise extracted propositions so that they can be compared across domains.
4. Fit joint BERTopic models to the pooled rule corpus.
5. Validate topic quality using embedding-based tightness and size-matched permutation tests.
6. Compare the thematic distributions of CMV and HH-RLHF rules.
7. Conduct a blinded manual audit of extraction and decontextualisation validity.

## Primary analysis

All dissertation results will be based on the **full joint corpus of 235,919 decontextualised rules**:

- 91,681 CMV rules
- 144,238 HH-RLHF rules

The broad model targeted 15 topics with a minimum topic size of 30 and yielded 14 observed topics. The fine-grained model was uncapped, used a minimum topic size of 15, and yielded 865 topics.

This primary full-corpus analysis is distinct from the balanced pooled subsample and other exploratory clustering runs retained in the wider parent project. Those alternative analyses will be explicitly labelled and will not be used as the source of the dissertation's main inferential claims.

## Repository guide

| Location | Contents |
|---|---|
| [`docs/`](docs/) | Plain-English study documentation, decisions, exclusions, availability, and validation protocol. |
| [`prompts/`](prompts/) | Versioned LLM prompts used for extraction, decontextualisation, and topic labelling. |
| [`notebooks/`](notebooks/) | Numbered notebooks that implement the pipeline. |
| [`data/`](data/) | Small, meaningful result tables and data documentation. |
| [`outputs/`](outputs/) | Reproducible figures, tables, and supplementary outputs. |

## Start here

1. Read [`docs/data-availability.md`](docs/data-availability.md) to understand which materials are public and why some large files are archived separately.
2. Read the documentation index in [`docs/README.md`](docs/README.md).
3. Follow the numbered notebooks once they are added.

## Reproducibility and security

The public repository will contain code, prompts, documentation, small final result tables, and validation outputs. Large raw and intermediate files are archived separately because of size constraints. No API keys, credentials, or private configuration files should be committed to this repository.
