# Analytical Decisions

This document records the decisions that define the dissertation's primary analysis. It is intended to prevent confusion between the main analysis and alternative exploratory or parent-project runs.

## Primary joint corpus

The primary comparison pools all available final decontextualised rules:

- CMV: 91,681 rules from 16,426 comments.
- HH-RLHF: 144,238 rules from 28,635 preference pairs.
- Joint corpus: 235,919 rules.

All dissertation comparisons should use files explicitly labelled **`pooled_full`** or the existing `pooled_bertopic_*` files that contain 235,919 rows.

## Primary BERTopic specification

| Component | Broad model | Fine-grained model |
|---|---:|---:|
| Topic target | 15 | Uncapped |
| Minimum topic size | 30 | 15 |
| Observed topics | 14 | 865 |
| UMAP components | 5 | 5 |
| UMAP minimum distance | 0.0 | 0.0 |
| UMAP metric | cosine | cosine |
| UMAP random state | 42 | 42 |
| HDBSCAN selection | EOM | EOM |
| HDBSCAN metric | euclidean | euclidean |
| Embedding model | `all-MiniLM-L6-v2` | `all-MiniLM-L6-v2` |

## Outlier reassignment

HDBSCAN initially classified 58.0% of broad-model rules and 59.1% of fine-grained-model rules as outliers. The primary analysis reassigns these rules using BERTopic's embedding-based `reduce_outliers` procedure.

This choice is reported transparently rather than hidden. Final-topic validity is assessed with embedding tightness and size-matched permutation tests. A sensitivity analysis retaining original outliers as unassigned will be reported separately if conducted.

## Topic as the comparative unit

The cross-corpus comparison uses thematic topics rather than one master rule per cluster. Manual inspection showed that joint clusters can contain multiple related but distinct propositions. A topic is therefore interpreted as a normative agenda, represented by a thematic label and exemplar rules.

## Distinct analyses that must not be confused

### Balanced pooled subsample

A separate balanced pooled run contains approximately 91,681 rules from each dataset, for 183,364 rules overall. It is an alternative robustness or exploratory analysis and is not the primary source of dissertation statistics.

### Other parent-project analyses

The wider project contains other clustering runs, including analyses with different minimum topic sizes. These are not interchangeable with the primary 235,919-rule, 865-topic fine-grained solution. Any such output must be explicitly identified as an alternative analysis.

## LLM settings

Extraction, decontextualisation, and topic labelling use `claude-haiku-4-5-20251001`. The notebooks specify `max_tokens` of 1024 for extraction, 256 for decontextualisation, and 50 for topic labels. Temperature was not explicitly set in the original pipeline and should be reported transparently in the dissertation.

