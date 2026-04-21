---
name: extract-customer-insights
description: Internal workflow for extracting high-quality customer discovery insights from transcripts and interview notes. Used by ingest when processing customer evidence.
user-invocable: false
allowed-tools:
  - Read
  - Write
  - Edit
  - Glob
  - Grep
---

# Customer Insight Extraction Workflow

Use this workflow when processing source material in `Research/Customer/Evidence/`, especially discovery calls, interview transcripts, and detailed customer notes.

This is an internal helper workflow for `/ingest`. The default user behavior should remain: call `/ingest <source>` and let ingest apply this extraction pattern automatically for customer evidence.

## Goal

Turn a customer call transcript or interview note into a structured, evidence-linked insight note in `Knowledge/Insights/Customer/`.

The purpose is not to summarize everything that was said. The purpose is to extract the most decision-useful customer learning while keeping a clear boundary between:

- what the customer explicitly said
- what the agent can reasonably infer
- what still needs validation from additional calls

## Best-Practice Principles

- Stay close to the evidence before generalizing.
- Prefer 3-4 core problems over long lists of minor complaints.
- Preserve customer language that reveals how they frame the problem.
- Separate pain points from feature requests.
- Capture business impact, not just stated inconvenience.
- Treat a single call as a signal, not as market truth.
- Record uncertainty and open questions instead of over-claiming.

## Workflow

1. Confirm the source is customer evidence.
   - Use this workflow for transcripts, interview notes, discovery calls, and other customer-facing source material under `Research/Customer/Evidence/`.

2. Read the source and identify the discovery structure.
   - Look for the triggering event or why-now moment.
   - Identify the current process, current tools, and where breakdowns occur.
   - Identify the buyer's desired future state, constraints, stakeholders, and timeline when available.

3. Extract the core customer learning.
   - Capture only the top 3-4 pain points or themes.
   - For each pain point, identify:
     - what the customer said or strongly implied
     - why it matters to the business or team
     - any current workaround
     - any indication of severity, urgency, or frequency

4. Preserve exact language.
   - Pull short, memorable phrases that reveal the customer's framing.
   - Prefer quotes that are useful later for positioning, messaging, or internal alignment.

5. Separate observations from interpretations.
   - Distinguish:
     - direct evidence
     - reasonable inference
     - open question or weak signal
   - Do not rewrite a vague statement as a strong conclusion.

6. Capture decision-relevant context.
   - Include:
     - customer role and company context
     - current state
     - desired outcomes
     - buying context and timeline
     - decision criteria or constraints

7. Create or update the customer insight note.
   - Place it in `Knowledge/Insights/Customer/`.
   - Keep the note concise, structured, and queryable.
   - Link it back to the source transcript in `## Sources`.

8. Suggest linked knowledge updates only when warranted.
   - If the transcript meaningfully informs strategy, active context, playbooks, metrics, or a decision record, update those notes.
   - Prefer linking those knowledge notes back to the customer insight note instead of treating a single call as enough to rewrite canonical knowledge on its own.

## Suggested Output Structure

Use this structure unless a nearby established note suggests a better local pattern:

```yaml
---
title: <Insight title>
type: insight
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources: [Research/Customer/Evidence/<file>]
source_authors: []
tags: [customer-insight, discovery-call]
---
```

```md
## Key Takeaways
- ...
- ...
- ...

## Customer Context
- ...

## Current State
- ...

## Core Problems
### <Problem>
- Evidence:
- Impact:
- Workaround:
- Confidence:

## Desired Outcomes
- ...

## Buying Context
- Stakeholders:
- Timeline:
- Constraints:

## Language To Preserve
- "..."

## Open Questions
- ...

## Related
- [[...]]

## Sources
- [[...]]
```

## Rules

- Do not collapse the whole call into a generic summary.
- Do not turn every request into a roadmap recommendation.
- Do not treat one transcript as enough to redefine market truth.
- Prefer precision over comprehensiveness.
- Keep the chain visible: evidence -> insight -> linked knowledge.
