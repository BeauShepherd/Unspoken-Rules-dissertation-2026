# Project Overview

## Research aim

This dissertation investigates whether the implicit norms extracted from naturalistic human debate differ from those recovered from AI-alignment preference data. The motivating concern is that preference datasets used in alignment may foreground some forms of human normative reasoning while underrepresenting others.

## Corpus roles

### CMV: naturalistic human debate

The CMV corpus consists of Reddit r/ChangeMyView discussions in which users publicly challenge one another's views. It is used as a corpus of naturally occurring argumentative and normative reasoning.

### HH-RLHF: AI-alignment preference data

The HH-RLHF corpus contains human preferences between alternative assistant responses. This study uses helpful preference data and excludes the harmless-base split because its annotation task selected the more harmful response, making it unsuitable for a study of preferred normative expectations.

## Pipeline

1. **Screening and exclusions** — exploratory topics without generalisable normative content were excluded according to documented criteria.
2. **Rule extraction** — Claude Haiku was prompted to identify generalisable rules, norms, principles, or heuristics supported by each source item.
3. **Decontextualisation** — extracted rules were rewritten into domain-general prescriptive propositions while preserving their core behavioural or epistemic content.
4. **Joint topic modelling** — pooled CMV and HH-RLHF rules were embedded with `all-MiniLM-L6-v2` and clustered using BERTopic.
5. **Topic validation** — embedding-based topic tightness and size-matched random baselines assessed whether the final clusters were more coherent than random rule collections.
6. **Comparative analysis** — topic distributions were compared between datasets at broad and fine-grained resolutions.
7. **Manual audit** — a blinded human validation protocol will assess source support, normativity, and decontextualisation fidelity for a stratified rule sample.

## Unit of analysis

A source comment or preference pair can yield several extracted rules. Rule-level data are appropriate for describing the thematic space, but comments and preference pairs are the relevant independent source units for any resampling or uncertainty analysis.

## Why the comparison uses topics rather than master rules

Within-corpus master rules can provide a concise descriptive summary. However, manual inspection of joint clusters indicated that a single topic can contain several related, non-equivalent prescriptive propositions. The primary cross-corpus comparison therefore treats a topic as a shared **normative agenda** and uses thematic labels plus representative rules, rather than forcing each topic into one master-rule statement.

