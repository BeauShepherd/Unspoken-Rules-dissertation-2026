# Manual Validation Protocol

## Aim

This protocol evaluates whether the LLM pipeline produces source-supported, generalisable implicit normative propositions and whether decontextualisation preserves their meaning.

## Sampling plan

A stratified random sample of 200 final rule records will be created:

- 100 CMV records;
- 100 HH-RLHF records;
- sampling stratified across broad topics within each corpus where feasible; and
- records randomly ordered and dataset labels hidden during manual rating.

The validation sheet will retain a separate identifier that permits records to be linked back to their source after ratings are complete.

## Materials reviewed for each record

Each rating record will contain:

- the relevant source text;
- the original LLM-extracted rule;
- the decontextualised rule; and
- a blinded record identifier.

For CMV, source text includes the relevant post context and comment. For HH-RLHF, source text includes the conversation context, preferred response, and non-preferred response.

## Rating dimensions

Each item is rated on three ordinal dimensions:

| Dimension | 0 | 1 | 2 |
|---|---|---|---|
| Source support | Unsupported or invented | Partly supported or over-inferred | Clearly supported by the source material |
| Normativity | Not a generalisable norm | Borderline or weakly normative | Clearly a generalisable behavioural, epistemic, or moral principle |
| Decontextualisation fidelity | Core meaning changed | Core meaning partly preserved | Core meaning preserved without inappropriate additions |

## Error coding

Where an item receives 0 or 1 on any dimension, one primary reason will be recorded:

- factual claim rather than norm;
- overly topic-specific proposition;
- unsupported inference;
- response-formatting or style proposition;
- over-generalisation during decontextualisation;
- ambiguous or contradictory source evidence; or
- other, with a short explanation.

## Intra-rater consistency

A randomly selected 50-record subset will be re-rated after a delay of 10–14 days. Dataset identity and first-pass ratings will remain hidden during the second pass. Agreement and weighted Cohen's kappa will be reported for the three ordinal dimensions.

## Interpretation

This protocol assesses single-researcher rating stability and construct validity. It does not substitute for independent inter-rater reliability, which will be acknowledged as a limitation.

