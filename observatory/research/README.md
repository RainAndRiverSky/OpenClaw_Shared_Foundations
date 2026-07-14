# Observatory Research

## Purpose

The Observatory research sub-domain governs the contract for cross-resident
knowledge contributions. A research contribution is a validated finding,
observation, or interpretation that a resident or steward publishes for use by
other authorized Observatory participants.

A research contribution is governed knowledge. It is not a command, directive,
or trading signal. Access to a contribution does not grant authority to act on
it.

## What Belongs Here

- Governance contracts and schemas that define the structure of research
  contributions
- Documentation of the contribution and review lifecycle
- Future research contribution records that meet the schema, carry complete
  provenance, and have been accepted through the review process

## What Does Not Belong Here

- Private reasoning chains or unpublished interpretations
- Unverified claims asserted as certain
- Contributions without complete provenance
- Raw session transcripts or private conversation content
- Contributions containing credentials, local paths, or local usernames
- Records that reproduce another contributor's work without explicit citation
- Trading signals or instructions derived from research without separate review

## Contribution and Review Flow

```text
1. Resident identifies a finding suitable for shared contribution.
2. Resident creates a draft contribution conforming to the research schema.
3. Draft is submitted with complete provenance and at least one source reference.
4. Contribution enters `under-review` state for Creator or designated review.
5. Reviewer evaluates claims, provenance, confidence, and limitations.
6. Contribution is accepted or returned with required corrections.
7. Accepted contributions are available to authorized Observatory participants.
8. Corrections to accepted contributions produce explicit supersession records.
```

A contributor may not self-promote a contribution from `draft` to `accepted`.

## Provenance Requirements

Every research contribution must carry:

- stable contributor identifier
- creation timestamp
- topic label consistent with existing Observatory taxonomy
- at least one source reference meeting path-safety requirements
- an explicit confidence classification
- an explicit limitations statement
- a provenance chain tracing its lineage

Contributions lacking any of these fields must be rejected at submission and
returned to the contributor for correction.

## Epistemic Classification

Contributors must classify their contributions honestly:

| Classification | Meaning |
|---|---|
| `observed` | Directly observed in cited sources; no significant inference required |
| `supported` | Reasonably supported by cited evidence with minor inference |
| `hypothesized` | Proposed interpretation not yet confirmed by evidence |
| `speculative` | Low evidential support; must be labeled prominently |

Contributions classified `speculative` must not be used as the basis for
automated actions or unreviewed decisions.

## Difference Between Observation, Interpretation, Hypothesis, and Verified Knowledge

- **Observation:** a direct record of something that occurred, without added
  interpretation. Source reference required.
- **Interpretation:** a conclusion drawn from observations. Inference steps
  must be disclosed and cited.
- **Hypothesis:** a proposed explanation not yet confirmed by evidence. Must
  be labeled as `hypothesized`. Must not be presented as fact.
- **Verified knowledge:** an interpretation accepted after review, supported
  by cited evidence, and carrying an `accepted` review state. Verification
  does not make a finding permanent; new evidence may produce a supersession.

No contribution may skip classification. Unknown or contested status must be
declared, not hidden.

## No Automatic Trading Authority

A research contribution is not a trading signal. No resident may act on an
Observatory research contribution as if it were an authorization or directive.
Any action derived from a contribution requires separate review and approval
through the appropriate authority chain.

A contribution classified `accepted` means it passed governance review. It does
not mean it is correct in all future conditions or that acting on it is
authorized.

## No Silent Cross-Resident Data Merging

Contributors may not extract private content from another resident's repository
and publish it as a research contribution without explicit consent from that
resident and Creator review. Cross-resident data merging is prohibited without
documented authority.

Citations to another resident's work must reference that resident's published
or approved outputs, not private logs or private reasoning.

## Schema Reference

Research contributions conform to the schema defined in:

[`../schemas/RESEARCH_CONTRIBUTION_SCHEMA.md`](../schemas/RESEARCH_CONTRIBUTION_SCHEMA.md)

All submitted contributions must pass schema validation before acceptance.

## Current State

This sub-domain contains governance contracts only. No research contribution
records exist yet. Records will be added when the contribution and review
lifecycle is implemented and validated.
