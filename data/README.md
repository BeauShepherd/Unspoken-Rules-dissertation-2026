# Data Folder

This folder contains the **small, meaningful outputs** needed to inspect and reproduce the dissertation's reported analyses.

## What belongs here

- topic-summary tables;
- cross-corpus comparison tables;
- topic-tightness and permutation-validation tables;
- manually coded validation data after identifiers and source text have been handled appropriately; and
- small metadata files describing each included table.

## What does not belong here

- raw downloaded CMV or HH-RLHF data;
- API checkpoint files;
- full extracted-rule tables;
- per-rule topic-assignment files; or
- embedding arrays.

Those large materials are retained separately as described in [`../docs/data-availability.md`](../docs/data-availability.md).

## Primary result tables to add

The following existing small outputs are candidates for inclusion after the file-by-file cleaning stage:

- `pooled_bertopic_broad_summary.csv`
- `pooled_bertopic_finegrained_summary.csv`
- `topic_domain_analysis.csv`
- `broad_topic_tightness.csv`
- `fine_topic_tightness.csv`
- `broad_topic_permutation_test.csv`

Each file will be reviewed, renamed if needed, and documented before upload.

