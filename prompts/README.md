# Prompts

This folder will contain the exact prompt text used in the dissertation pipeline. Keeping prompts in separate plain-text files makes the LLM-assisted stages auditable without forcing readers to search through notebooks.

## Planned prompt files - can we do hyperlink to skip down this file?

- `cmv_rule_extraction.md`
- `hh_rlhf_rule_extraction.md`
- `cmv_decontextualisation.md`
- `hh_rlhf_decontextualisation.md`
- `topic_labelling.md`

  02- HH-decontextuliases prompt:

  DECONTEXT_PROMPT = """You will be given a rule or norm extracted from a piece of text. The rule may be expressed in domain-specific language tied to a particular topic (e.g. child support, medical evidence, gun control).

Your task is to rewrite the rule as a general prescriptive principle that:

- Preserves the core behavioural or epistemic norm
- Removes references to specific domains, topics, or named situations
- Remains concrete enough to be actionable (do not reduce it to a platitude)
- Is expressed as a clear prescriptive statement (what one should do or how one should reason)
- Do not add information, implications or instructions that are not present in the original rule

Examples:

Input: "When evaluating gun control policies, consider both the immediate safety benefits and the long-term effects on civil liberties."
Output: "When evaluating any policy, weigh both its immediate benefits and its long-term effects on other values."

Input: "In medical debates, do not dismiss anecdotal evidence entirely — it can point to patterns worth investigating."
Output: "Do not dismiss anecdotal evidence entirely, as it can point to patterns worth investigating systematically."

Input: "When someone claims superiority in a domain, ask them to specify measurable evidence rather than accepting the claim at face value."
Output: "Require measurable evidence before accepting claims of superiority or expertise."

Return only the rewritten rule. No explanation, no preamble."""


def decontextualise(rule: str, max_retries: int = 4) -> str:
    """
    Send one rule to Claude Haiku and return the decontextualised version.

    Includes exponential backoff retry logic for transient server errors
    (InternalServerError, RateLimitError etc.) -- these are common during
    long runs and are not bugs, just the server hiccuping.

    Wait times between retries: 5s, 10s, 20s, 40s (doubles each time).
    After 4 failed attempts, returns None so the calling loop can log it
    and move on -- the null will be caught and retried on the next resume.
    """

## Documentation standard

Each prompt file will state:

- the pipeline stage it supports;
- the input fields inserted into the prompt;
- the exact prompt text used in the final run;
- the model identifier and token limit used for that stage; and
- any material differences between the CMV and HH-RLHF versions.

Prompts will never contain API keys, credentials, or private paths.

