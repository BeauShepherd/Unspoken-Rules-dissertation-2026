# Notebooks

This folder will contain the cleaned, numbered notebooks that implement the dissertation pipeline. Notebooks will be uploaded only after API keys, private paths, and unnecessary exploratory cells have been removed.

## HH-RLHF Pipline

| Notebook | Purpose |
|---|---|
| [01_HH_Download_Data.ipynb](hh-rlhf-pipeline/01_HH_Download_Data.ipynb) | Source loading, cleaning, exploratory topic screening, exclusions, and stratified splits. |
| | Extract implicit rules from CMV comments. |
| | Decontextualise CMV rules. |
| | Extract implicit rules from HH-RLHF preference pairs. |
| | Decontextualise HH-RLHF rules. |
| | Build the primary 235,919-rule joint BERTopic models. |
| | Compute topic tightness and permutation-validation outputs. |
| | Generate, blind, and analyse the manual validation sample. |
| | Produce final tables and figures from the frozen primary analysis. |

## CMV Pipline

| Notebook | Purpose |
|---|---|
|  |  |

## Cross-Comparison Pipeline

| Notebook | Purpose |
|---|---|
|  |  |

## Notebook standards

Each published notebook will:

- begin with a brief plain-English purpose statement;
- identify expected inputs and produced outputs;
- use relative paths rather than personal Google Drive paths;
- read API keys from environment variables, never from the notebook text;
- explain substantive methodological decisions in comments;
- distinguish main analysis from exploratory or alternative runs; and
- end by saving clearly named outputs.

