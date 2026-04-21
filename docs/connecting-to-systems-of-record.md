# Connecting the Knowledge Engine to Systems of Record

This repository works best as a knowledge engine that sits beside existing systems of record, not in place of them.

Use it to turn source material into reusable knowledge. Keep operational truth in the tools already responsible for operational truth.

## The split of responsibilities

Use this repository for:

- raw source material and intermediate synthesis in `Research/`
- durable concepts, strategy, decisions, metrics, and playbooks in `Knowledge/`
- polished outputs in `Outputs/`

Use systems of record for:

- CRM data such as contacts, accounts, opportunities, activities, and next steps
- support and ticket state
- project and task state
- finance, legal, and HR records
- any person-level or account-level operational status that changes frequently

## Why this split works

Knowledge compounds when it is durable, reusable, and linked across contexts.

Operational systems optimize for current state, ownership, permissions, workflows, and auditability. They answer questions such as:

- who owns this account?
- what was last discussed with this contact?
- what is the current deal stage?
- what is the next action and when is it due?

This repository answers different questions:

- what patterns are repeating across customer conversations?
- how is our understanding of the ICP changing?
- which objections are common enough to shape positioning or playbooks?
- what decisions have we made and why?

Trying to do both jobs in one place usually creates a poor CRM and a noisy knowledge base.

## Recommended workflow for customer calls

1. Store the authoritative relationship record in your CRM.
2. Capture the transcript, recording summary, or notes in `Research/Customer/Evidence/` if that material belongs in this repository.
3. Extract synthesis into `Research/Customer/Insights/`.
4. Promote repeated and durable insights into `Knowledge/`.
5. Link any important decision, metric change, or playbook update back to the supporting insight.

For example:

- CRM stores: call date, participants, account, summary, next steps, deal implications
- `Research/Customer/Evidence/` stores: transcript or detailed source note
- `Research/Customer/Insights/` stores: extracted pains, triggers, objections, terminology, surprises
- `Knowledge/Foundations/Strategy/` stores: ICP or positioning changes supported by repeated evidence
- `Knowledge/Operating System/Playbooks/` stores: updated interview prompts or sales handling patterns

## Answering "what was last discussed with person X at company Y?"

That question should usually be answered by the CRM.

It depends on relationship-specific memory, current ownership, and latest activity state. Those are system-of-record concerns.

If you want this repository to support that workflow indirectly, store a stable reference in the CRM record to the relevant research note or transcript. The repository can then provide analytical depth while the CRM remains the place to check recency and ownership.

## Integration patterns

### 1. Link out from the CRM

Add a field in the CRM for:

- repository note URL
- transcript file path
- research note ID
- insight note link

Use this when the CRM user sometimes needs the underlying evidence or synthesis.

### 2. Link back from research notes

Include a lightweight reference in a research note such as:

- CRM account ID
- CRM contact ID
- call ID
- opportunity ID

Keep these as references, not as duplicated operational records.

### 3. Periodic ingestion from operational tools

Export or sync selected material from CRM, support, or call-recording tools into `Research/` on a schedule.

This works well for:

- call transcripts
- win-loss summaries
- support themes
- tagged feedback exports

The repository should ingest and distill that material, not become the canonical home of the live records themselves.

### 4. Private extension for sensitive source material

If transcripts or account-specific material are sensitive, keep them in:

- a private fork
- a private companion repository
- a secure storage system referenced from this repository

Then promote only the reusable insight into the main curated knowledge base.

## A simple architecture

```text
Call recorder / CRM / support tool
            |
            v
    Export or sync source material
            |
            v
Research/Customer/Evidence/
            |
            v
Research/Customer/Insights/
            |
            v
Knowledge/
            |
            v
Outputs/

CRM remains the system of record for contact, account, deal, and activity state.
```

## Design rules

- Keep one source of truth for operational state.
- Use this repository for durable learning and linked reasoning.
- Store relationship history where permissions, workflows, and ownership already exist.
- Promote patterns into `Knowledge/`, not account-by-account memory.
- When in doubt, ask whether the note will still be useful after the specific relationship context changes.

If the answer is no, it probably belongs in the external system of record instead.
