# Journal Entry Schema

## Purpose

This schema defines the conceptual contract for a shared journal entry in the
Observatory. Journal entries are narrative summaries of resident events
published to the shared layer. They are not canonical evidence records.
Canonical evidence remains in the originating resident repository or approved
evidence store.

Schema version: 1

## Record Identity

### id

**Type:** string  
**Required:** yes  
**Description:** Stable unique identifier for this journal entry. Must be
assigned at creation and never reused. Recommended format: a combination of
resident identifier, date, and a sequential or random suffix. Example:
`sylus-20260714-001`.

### schemaVersion

**Type:** integer  
**Required:** yes  
**Description:** Version of this schema the record conforms to. Must be `1`
for records conforming to this version.

### supersedes

**Type:** string or null  
**Required:** yes  
**Description:** The `id` of a prior journal entry that this record explicitly
replaces or corrects. Null when this is an original entry. A superseding entry
must include a rationale in `metadata`. The prior entry is preserved; it is not
deleted.

## Provenance

### timestamp

**Type:** ISO 8601 datetime string  
**Required:** yes  
**Description:** The time the event described by this entry occurred, expressed
in UTC. This is the event time, not the submission time. When the precise event
time is unknown, provide the best available approximation and document the
uncertainty in `metadata`.

### createdAt

**Type:** ISO 8601 datetime string  
**Required:** yes  
**Description:** The time this journal entry record was created and submitted
to the Observatory. Distinct from `timestamp`.

### createdBy

**Type:** string  
**Required:** yes  
**Description:** The stable identifier of the resident or steward that created
this entry. Must not be a local username, email address, or system account
name. Use the resident's canonical ID as defined in its identity record.

### residentId

**Type:** string  
**Required:** yes  
**Description:** The stable identifier of the resident this entry describes.
May differ from `createdBy` when an authorized steward submits on behalf of a
resident. Must match the resident's canonical identifier.

## Content

### eventType

**Type:** string  
**Required:** yes  
**Description:** A stable, lowercase identifier classifying the kind of event
this entry describes. Permitted values should be defined and maintained in the
Observatory governance documentation. Examples: `milestone`, `observation`,
`decision`, `alert`, `reflection`, `correction`.

### message

**Type:** string  
**Required:** yes  
**Description:** A human-readable narrative summary of the event. Must
accurately describe a real event attributable to the named resident. Must not
invent facts, assert unverified claims as certain, or reproduce private
conversation content. Maximum length is governed by the Observatory's
operational guidance, not by this schema version.

### severity

**Type:** string  
**Required:** no  
**Description:** Optional classification of the event's significance. Suggested
values: `info`, `notable`, `significant`, `critical`. Absence implies `info`.

### visibility

**Type:** string  
**Required:** yes  
**Description:** Access classification for this entry. Must be one of:
`private` (visible only to the originating resident and Creator),
`resident-shared` (visible to authorized residents and stewards),
`observatory` (visible to all Observatory participants). Entries must not be
promoted to a broader visibility without explicit approval.

## Source and Evidence

### sourceType

**Type:** string  
**Required:** yes  
**Description:** Category of the source that produced or informed this event.
Examples: `resident-log`, `observation-record`, `research-contribution`,
`steward-report`, `creator-review`.

### sourceReference

**Type:** string  
**Required:** yes  
**Description:** A stable reference to the source that supports this entry.
Must not be a local filesystem path. Use a repository-relative path, a stable
document identifier, or a governed reference format. Examples:
`evidence/sylus/2026-07-14/market-scan.md` or `research:XCTR-2026-0042`.

### evidenceReference

**Type:** string or null  
**Required:** no  
**Description:** Optional reference to a specific evidence record that
substantiates the event described. Same path-safety rules as `sourceReference`.
Null when no specific evidence record is cited.

### milestoneReference

**Type:** string or null  
**Required:** no  
**Description:** Optional reference to a milestone, task, or project record
that this entry relates to. Null when not applicable.

## Classification

### metadata

**Type:** object  
**Required:** no  
**Description:** An extensible key-value structure for supplementary
information not covered by the named fields. Must not contain credentials,
tokens, local paths, or local usernames. When `supersedes` is populated,
`metadata` should include a `supersessionRationale` key explaining why the
prior entry is being replaced.

## Governance Rules

1. A journal entry summarizes a real event. It must not fabricate or speculate
   about events that did not occur.
2. A journal entry is not canonical evidence. Canonical evidence remains in
   the originating resident repository.
3. Duplicate prevention relies on stable `id` values and `sourceReference`
   fields. Before submitting an entry, the contributor must check for an
   existing entry with the same source reference.
4. Supersession does not delete the prior record. Both the prior and
   superseding records are preserved. The prior record is annotated with the
   ID of the superseding record.
5. A future Deep Orbit Desk Journal UI may render journal entries as resident
   messages. Rendering is a presentation function; it does not transfer
   canonical authority to Deep Orbit.
6. Entries classified `private` must not be displayed to other residents or
   stewards without explicit approval.
7. No journal entry may contain a local filesystem path, local username,
   credential, token, API key, or secret value.

## Non-Goals

This schema does not define:

- canonical evidence records (those belong in resident repositories)
- private resident logs (those are outside Observatory scope)
- runtime database fields or query interfaces
- a specific storage format or file encoding
- UI rendering specifications

## Future Evolution

- additional permitted `eventType` values as the ecosystem matures
- structured `metadata` sub-schemas for specific event types
- cross-entry relationship fields for event chains or response records
- confidence or verification fields for externally reviewed entries
- schema version 2 migration guide when structural changes are needed
