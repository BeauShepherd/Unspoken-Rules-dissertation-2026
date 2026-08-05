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
file 02 CMV extrcations:
# This is the exact prompt used for subsets 0 and 1, do not modify
EXTRACTION_PROMPT = """\
You are analysing a comment from Reddit's r/ChangeMyView, a community where \
users post opinions and invite others to challenge them through debate.

Context — the original post being debated:

Title: {post_title}

Post: {post_selftext}

Comment to analyse:

{comment_body}

Your task: extract every rule, norm, principle, or heuristic that is stated or \
clearly implied in the comment — generalizable statements about HOW people should \
reason, argue, or make decisions in situations like this one.

Here are some examples of rules:

1. Domain-specific rules of thumb — practical guidelines for a type of situation \
(e.g. "always consider unintended consequences of a policy")

2. Pragmatic interaction norms — how one should behave toward others \
(e.g. "offer evidence when challenging a claim")

3. Moral heuristics — ethical principles invoked to justify or critique a choice \
(e.g. "you should not hold people responsible for outcomes they could not foresee")

4. Reasoning patterns — general decision strategies or appeals to fairness, \
precedent, or consequences (e.g. "if you accept X you must also accept Y for consistency")

Rules to extract:

- Generalizable principles, not facts specific only to this comment

- Stated explicitly OR clearly implied by the commenter's reasoning or framing

- Often signalled by words like: should, always, never, it's important to, \
you have to, the right thing is, it's fair to, in situations like this

- Rewrite in general form if the comment states it only about their specific \
case (e.g. "I always back my claims with sources" -> "Always support claims with evidence")

- Each rule must be understandable to an intelligent adult who has not read \
the source comment

Do NOT extract:

- Pure factual statements about the specific debate topic

- Questions without an implied norm

- Rules that only make sense within this specific topic

Return ONLY a raw JSON array of strings with no markdown, no code fences, no \
explanation. Each string should be one concise rule in general form. Example:

["Always weigh long-term consequences over short-term comfort.", "You should \
not let sunk costs drive future decisions."]

If no rules can be extracted, return an empty list."""


def parse_json_response(text: str) -> list:
    """
    Clean and parse the model's raw text output into a Python list.
    The model sometimes wraps its response in markdown code fences (```json ... ```)
    even when instructed not to -- the regex strips those before parsing.
    """
    text = text.strip()
    text = re.sub(r"^```(?:json)?\s*", "", text)  # remove opening fence
    text = re.sub(r"\s*```$", "", text)            # remove closing fence
    return json.loads(text.strip())


def extract_rules(post_title: str, post_selftext: str,
                  comment_body: str, debug: bool = False) -> list:
    """
    Send one comment to Claude Haiku and return a list of extracted rule strings.
    Returns an empty list if the model finds nothing extractable or if parsing fails.

    Retry logic handles transient server errors (500) which can occur on long runs.
    Uses exponential backoff: waits 5s, then 10s, then 20s before giving up.
    If all retries fail, returns an empty list so the run continues rather than crashes.
    """

File: 03 cmv deconetxctualisation:

DECONTEXT_PROMPT = """You will be given a rule or norm extracted from an online debate. The rule may be expressed in domain-specific language tied to a particular topic (e.g. child support, medical evidence, gun control).

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


FILE: 04 BERTopic_clustering: labels

def generate_topic_label(rules_sample: list) -> str:
    """
    Send a sample of rules from one cluster to Claude Haiku
    and get back a short 4-7 word label describing the shared principle.
    """
    rules_text = "\n".join([f"{i+1}. {r}" for i, r in enumerate(rules_sample)])

    message = client.messages.create(
        model="claude-haiku-4-5-20251001",
        max_tokens=50,
        messages=[
            {
                "role": "user",
                "content": f"""You are labelling a cluster of related rules extracted from human debates.

Here are up to 10 rules from this cluster:

{rules_text}

Generate a short label (4-7 words) that describes the shared principle across these rules.
The label should read as a theme or norm category, not as a full sentence.

Return only the label, nothing else."""

File: 05_Master_rules: Master rule prompt:
SYNTHESIS_PROMPT = """You are synthesising a cluster of related rules extracted from human debates into a single master rule.

Cluster label: {topic_label}

Rules in this cluster:

{rules_text}

Your task: write a single master rule that captures the shared principle across all these rules.

Requirements:

- The master rule should be prescriptive (what one should do or how one should reason)
- It should be general enough to cover all rules in the cluster
- It should be specific enough to be actionable -- do not reduce it to a platitude
- Maximum 2 sentences
- Aim for under 60 words
- Write in clear, simple English that any intelligent adult can understand
- Do not add information that is not present in the rules above
- Do not reference specific domains or topics

Return only the master rule. No explanation, no preamble."""


# ── SHORT VERSION PROMPT ──────────────────────────────────────────────────────
# Takes the already-synthesised master rule and compresses it further
# into a single plain-language sentence under 15 words
# Purpose: stimulus material for the human rater study (Stage 2)
# where shorter, simpler phrasings are easier for participants to evaluate

SHORT_VERSION_PROMPT = """You will be given a rule. Rewrite it as a single short sentence of no more than 15 words.

Use plain everyday language. Keep the core meaning intact.

Rule: {master_rule}

Return only the short version. No explanation, no preamble."""


def synthesise_master_rule(rules_list: list, topic_label: str,
                           max_retries: int = 4) -> str:
    """
    Send all rules in a cluster to Claude Haiku and get back
    a single master rule capturing the shared principle.

    Uses all rules in the cluster (not just a sample) so the
    master rule covers the full range of the cluster.

    Includes exponential backoff retry for transient server errors.
    Returns None if all retries fail -- the calling loop will log it.
    """

  SAME FILE:  CLAUDE CONFIRMATION ON DUPLICATES.

  ef check_if_same_rule(rule_a: str, rule_b: str,
                       max_retries: int = 4) -> dict:
    """
    Ask Claude Haiku whether two master rules express the same principle.
    Returns a dict with 'verdict' (SAME or DIFFERENT) and 'reason' (one sentence).
    """
    prompt = f"""You are reviewing two rules to determine whether they express the same underlying principle.

Rule A: {rule_a}

Rule B: {rule_b}

Are these the same rule expressed differently, or are they genuinely different rules?

Answer with:
SAME - if they express the same core principle and could be merged into one rule
DIFFERENT - if they express distinct principles that should remain separate

Then in one sentence explain your reasoning.

Format your response exactly as:
VERDICT: [SAME or DIFFERENT]
REASON: [one sentence]"""

  
## Documentation standard

Each prompt file will state:

- the pipeline stage it supports;
- the input fields inserted into the prompt;
- the exact prompt text used in the final run;
- the model identifier and token limit used for that stage; and
- any material differences between the CMV and HH-RLHF versions.

Prompts will never contain API keys, credentials, or private paths.

