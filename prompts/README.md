# Prompts

This folder will contain the exact prompt text used in the dissertation pipeline. Keeping prompts in separate plain-text files makes the LLM-assisted stages auditable without forcing readers to search through notebooks.

## Planned prompt files

- `cmv_rule_extraction.md`
- `hh_rlhf_rule_extraction.md`
- `cmv_decontextualisation.md`
- `hh_rlhf_decontextualisation.md`
- `topic_labelling.md`

## Documentation standard

Each prompt file will state:

- the pipeline stage it supports;
- the input fields inserted into the prompt;
- the exact prompt text used in the final run;
- the model identifier and token limit used for that stage; and
- any material differences between the CMV and HH-RLHF versions.

Prompts will never contain API keys, credentials, or private paths.

