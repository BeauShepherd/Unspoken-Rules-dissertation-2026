# Topic Exclusion Log

## Purpose

Exploratory topic modelling was used before rule extraction to identify source-text clusters unlikely to yield generalisable implicit norms. Topics were excluded using the following criteria:

1. **No generalisable implicit rule was plausibly available.** This includes highly idiosyncratic topics tied to a specific fictional scenario, object, or one-off event.
2. **The topic was empirical or definitional rather than normative.** This includes discussions focused on factual claims, classifications, or word meanings without a meaningful behavioural or evaluative principle.

## CMV exclusions

The CMV exploratory solution contained 49 topics. Seven were excluded, leaving 42 topics in the final CMV analytic file.

| Topic ID | Topic label | Criterion | Rationale |
|---:|---|---:|---|
| 01 | Definition and usage of “overrated” term | 2 | Definitional discussion rather than normative reasoning. |
| 30 | Touchscreen technology reliability and performance | 2 | Empirical or technical discussion rather than normative reasoning. |
| 36 | Sandy Hook conspiracy theory legitimacy | 1 | Topic was judged too event-specific to provide a generalisable rule. |
| 38 | Batman versus Superman fighting capabilities | 1 | Fictional and scenario-specific; no generalisable implicit rule was expected. |
| 40 | Pizza, Calzone, and Sandwich Classification | 1 | Classification dispute without a generalisable normative principle. |
| 43 | Coffee preparation and consumption preferences | 1 | Topic-specific preferences without a generalisable implicit rule. |
| 45 | Impact of personal names on life outcomes | 2 | Primarily empirical discussion rather than normative reasoning. |

The retained-topic count, 42, matches the final CMV analytic file.

## HH-RLHF exclusion

The HH-RLHF exploratory solution contained 49 topics. One topic was excluded, leaving 48 topics in the final HH-RLHF analytic file.

| Topic ID | Raw topic label | Rows | Criterion | Rationale |
|---:|---|---:|---:|---|
| 42 | `42_translate_de_article_la` | 227 | 1 | Translation requests lacked independent normative or behavioural content from which a generalisable implicit rule could be recovered. |

## Scope note

These exclusions concern the source-text screening stage. They do not remove individual rules because of their eventual topic membership or because they favour a particular cross-corpus result.

