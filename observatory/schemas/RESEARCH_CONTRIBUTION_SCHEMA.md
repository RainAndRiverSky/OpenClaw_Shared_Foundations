# Research Contribution Schema

## Purpose

This schema defines the conceptual contract for a governed cross-resident
knowledge contribution in the Observatory. Research contributions allow a
resident or steward to share a validated finding, observation, or interpretation
with other authorized participants without merging private repositories or
transferring evidence ownership.

A research contribution is a governed claim, not a command or signal. Access to
a contribution does not grant authority to act on it.

Schema version: 1

## Record Identity

### contributionId

**Type:** string  
**Required:** yes  
**Description:** Stable unique identifier for this contribution. Must be
assigned at creation and never reused. Recommended format: a topic prefix, a
date, and a sequential or random suffix. Example: `mkt-20260714-003`.

### schemaVersion

**Type:** integer  
**Required:** yes  
**Description:** Version of this schema the record conforms to. Must be `1`
for records conforming to this version.

### supersedes

**Type:** string or null  
**Required:** yes  
**Description:** The `contributionId` of a prior contribution that this record
explicitly replaces or corrects. Null when this is an original contribution.
A superseding record must include rationale in `metadata`. The prior record is
preserved and annotated.

## Provenance

### contributor

**Type:** string  
**Required:** yes  
**Description:** The stable identifier of the resident or steward that produced
this contribution. Must not be a local username, email address, or system
account name. Use the contributor's canonical ID as defined in their identity
record.

### timestamp

**Type:** ISO 8601 datetime string  
**Required:** yes  
**Description:** The time this contribution was created, expressed in UTC.

### provenanceChain

**Type:** array of strings  
**Required:** yes  
**Description:** An ordered list of identifiers tracing the lineage of this
contribution. For an original contribution, this contains only the
`contributionId`. For a superseding contribution, it includes the chain of
prior `contributionId` values in chronological order, oldest first, with the
current ID appended. This field must never be truncated.

## Content

### topic

**Type:** string  
**Required:** yes  
**Description:** A short, stable label identifying the subject domain of this
contribution. Topic values should be consistent across contributions about the
same subject to support future retrieval. Examples: `equity-volume-pattern`,
`volatility-surface-behavior`, `resident-risk-tolerance`.

### summary

**Type:** string  
**Required:** yes  
**Description:** A human-readable statement of the finding, observation, or
interpretation. Must accurately reflect the evidence cited. Must not assert
unverified claims as certain. Must not reproduce private conversation content.
Claims must be scoped to what the cited evidence actually supports.

### reviewState

**Type:** string  
**Required:** yes  
**Description:** The current governance state of this contribution. Permitted
values:

- `draft` — submitted but not yet reviewed
- `under-review` — active Creator or designated review in progress
- `accepted` — reviewed and accepted for shared use
- `superseded` — replaced by a newer contribution identified in `supersededBy`
- `withdrawn` — removed from active use; tombstone record preserved

Transitions between states require the authority defined in Observatory
governance. A contributor may not self-promote from `draft` to `accepted`.

### supersededBy

**Type:** string or null  
**Required:** yes  
**Description:** The `contributionId` of the record that supersedes this one.
Null when this record is current. Populated only when `reviewState` is
`superseded`.

## Scope and Applicability

### applicableResidents

**Type:** array of strings or the literal string `all`  
**Required:** yes  
**Description:** The residents or stewards for whom this contribution is
relevant. Use canonical resident IDs. The value `all` indicates relevance to
all current and future Observatory participants. This field defines relevance,
not permission; visibility is governed separately.

### visibility

**Type:** string  
**Required:** yes  
**Description:** Access classification for this contribution. Must be one of:
`private`, `resident-shared`, or `observatory`. Same semantics as the journal
entry schema. Promotions to broader visibility require explicit approval.

## Evidence and Sources

### sourceReferences

**Type:** array of strings  
**Required:** yes  
**Description:** One or more stable references to the sources that support this
contribution. Must not be local filesystem paths. Use repository-relative
paths, stable document identifiers, or governed reference formats. At least one
source reference is required.

### evidenceReferences

**Type:** array of strings  
**Required:** no  
**Description:** Optional references to specific evidence records that
substantiate this contribution. Same path-safety rules as `sourceReferences`.
Empty array when no specific evidence records are cited.

### canonicalEvidenceRef

**Type:** string or null
**Required:** no
**Description:** Optional namespaced reference to a single resident-owned
canonical evidence artifact that this contribution is directly linked to.
Format: `residentId:artifactId` as defined in the Canonical Evidence Contract
(see [`CANONICAL_EVIDENCE_CONTRACT.md`](CANONICAL_EVIDENCE_CONTRACT.md)).

This field links the contribution to canonical evidence without transferring
ownership of that evidence. The evidence remains in the originating resident
repository. Populating this field does not promote the evidence into the
Observatory or make the contribution an authoritative copy of the evidence.

Null when this contribution does not correspond to a specific canonical evidence
artifact. When populated, the referenced artifact must exist in the originating
resident's evidence store and must have `evidenceState` of `canonical` at
the time the contribution is submitted.

## Epistemic Classification

### confidence

**Type:** string or null  
**Required:** no  
**Description:** The contributor's explicit assessment of evidential support.
Required when `reviewState` is `accepted`. Permitted values:

- `observed` — directly observed in cited sources with no inference required
- `supported` — reasonably supported by cited evidence with minor inference
- `hypothesized` — proposed interpretation not yet confirmed by evidence
- `speculative` — low evidential support; requires prominent labeling

Null is acceptable for `draft` state. Contributions with `speculative`
confidence must not be used as the basis for automated actions.

### limitations

**Type:** string  
**Required:** yes  
**Description:** An explicit statement of what this contribution does not cover,
where the evidence may be incomplete or time-bound, and what would be required
to increase confidence. Must not be left empty. If no limitations are known,
state that explicitly with a brief rationale.

## Governance

### metadata

**Type:** object  
**Required:** no  
**Description:** Extensible key-value structure for supplementary information.
Must not contain credentials, tokens, local paths, or local usernames. When
`supersedes` is populated, `metadata` should include a
`supersessionRationale` key.

## Governance Rules

1. A research contribution is governed knowledge. It is not a trading signal,
   an instruction, or a directive. Access to a contribution does not authorize
   any resident to act on it without separate review and approval.
2. A contributor may not overwrite another contributor's record. Corrections
   create a new superseding record. The prior record is preserved.
3. Unsupported claims must not be promoted as shared knowledge. The
   `confidence` field is required before a contribution reaches `accepted`
   state.
4. Private reasoning chains, raw session transcripts, and unverified
   interpretations must not enter the Observatory as research contributions.
5. A contribution does not transfer evidence ownership. Cited evidence remains
   in its originating repository.
6. No contribution may contain a local filesystem path, local username,
   credential, token, API key, or secret value.
7. `reviewState` transitions must follow the authority model in Observatory
   governance. Self-approval from `draft` to `accepted` is prohibited.

## Non-Goals

This schema does not define:

- a trading signal format or distribution channel
- a decision record or instruction format
- private resident reasoning chains
- runtime database fields or query interfaces
- a specific storage format or file encoding
- a public data feed or external API

## Future Evolution

- structured topic taxonomy for consistent labeling
- cross-contribution relationship fields for citation chains
- reviewer identity fields for accepted contributions
- expiration or review-cycle fields for time-sensitive findings
- schema version 2 migration guide when structural changes are needed
