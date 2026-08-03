# Notebooks

This folder will contain the cleaned, numbered notebooks that implement the dissertation pipeline. Notebooks will be uploaded only after API keys, private paths, and unnecessary exploratory cells have been removed.

## Planned order

| Notebook | Purpose |
|---|---|
| `01_data_screening_and_exclusions.ipynb` | Source loading, cleaning, exploratory topic screening, exclusions, and stratified splits. |
| `02_cmv_rule_extraction.ipynb` | Extract implicit rules from CMV comments. |
| `03_cmv_decontextualisation.ipynb` | Decontextualise CMV rules. |
| `04_hh_rlhf_rule_extraction.ipynb` | Extract implicit rules from HH-RLHF preference pairs. |
| `05_hh_rlhf_decontextualisation.ipynb` | Decontextualise HH-RLHF rules. |
| `06_joint_topic_modelling.ipynb` | Build the primary 235,919-rule joint BERTopic models. |
| `07_topic_validation.ipynb` | Compute topic tightness and permutation-validation outputs. |
| `08_manual_validation.ipynb` | Generate, blind, and analyse the manual validation sample. |
| `09_results_and_figures.ipynb` | Produce final tables and figures from the frozen primary analysis. |

## Notebook standards

Each published notebook will:

- begin with a brief plain-English purpose statement;
- identify expected inputs and produced outputs;
- use relative paths rather than personal Google Drive paths;
- read API keys from environment variables, never from the notebook text;
- explain substantive methodological decisions in comments;
- distinguish main analysis from exploratory or alternative runs; and
- end by saving clearly named outputs.

