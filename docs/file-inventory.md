# File Inventory and Naming Rules

## Purpose

The parent project contains multiple exploratory and comparative runs. This inventory makes clear which files define the dissertation's primary analysis and which files should be treated as alternative or archived analyses.

## Primary full-corpus analysis

These files correspond to the dissertation's main joint corpus of **235,919 rules**:

| File | Role | Publish in `data/`? |
|---|---|---|
| `pooled_bertopic_broad.csv` | Per-rule broad-topic assignment table; large intermediate output | No — archive separately |
| `pooled_bertopic_finegrained.csv` | Per-rule fine-topic assignment table; large intermediate output | No — archive separately |
| `pooled_bertopic_broad_summary.csv` | 14-topic broad summary | Yes |
| `pooled_bertopic_finegrained_summary.csv` | 865-topic fine-grained summary | Yes |
| `topic_domain_analysis.csv` | Fine-topic comparative statistics | Yes |
| `broad_topic_tightness.csv` | Broad-topic embedding tightness | Yes |
| `fine_topic_tightness.csv` | Fine-topic embedding tightness | Yes |
| `broad_topic_permutation_test.csv` | Broad-topic random-baseline validation | Yes |

## Primary source-specific analytic files

| File | Role | Public-repository treatment |
|---|---|---|
| `cmv_all_subsets_decontextualised.xlsx` | Final CMV rule-level authority | Archive separately or provide on reasonable request |
| `hh_subset0_decontextualised.csv` | Final HH-RLHF rule-level authority | Archive separately; too large for standard GitHub storage |
| `hh_subset_0.csv` | HH-RLHF pre-extraction subset | Archive separately |

## Alternative runs

The following should never be presented as the dissertation's primary analysis without explicit labelling:

| Current filename | What it represents | Recommended future name |
|---|---|---|
| `cmv_bertopic_broad (4).csv` | Balanced pooled subsample, not CMV-only data | `pooled_balanced_broad_assignments.csv` |
| `cmv_bertopic_finegrained (4).csv` | Balanced pooled subsample, not CMV-only data | `pooled_balanced_fine_assignments.csv` |
| `hh_subset0_bertopic_*` | HH-RLHF-only clustering outputs | Prefix with `hh_individual_` when copied into a clean release folder |

## Naming convention for new files

Use names that answer three questions: **what corpus, what analysis level, and what role?**

Examples:

- `pooled_full_fine_summary.csv`
- `pooled_balanced_broad_summary.csv`
- `cmv_individual_master_rules.csv`
- `hh_individual_topic_summary.csv`
- `table_01_dataset_extraction_summary.csv`

Avoid duplicate-number filenames, spaces, and ambiguous prefixes such as `cmv_` for pooled files.

