# Outputs

This folder will contain outputs generated from the cleaned primary-analysis notebooks.

## Planned structure

```text
outputs/
├── figures/          # Publication-style figures used in the dissertation
├── tables/           # Final tables used in the dissertation
└── supplementary/    # Additional robustness, validation, and audit outputs
```

Only regenerated outputs should be placed here. This avoids confusion between early exploratory charts and the final figures/tables reported in the dissertation.

Every final output should be traceable to a numbered notebook and should use a descriptive filename, for example:

- `figure_01_pipeline_and_validation.png`
- `figure_02_normative_topic_landscape.png`
- `figure_03_topic_enrichment_by_corpus.png`
- `table_01_dataset_and_extraction_summary.csv`
- `table_02_primary_topic_comparison.csv`

