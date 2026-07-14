# Foundation Observatory Architecture

## Purpose

The Observatory foundation defines how Deep Orbit residents and OpenClaw
stewards contribute governed knowledge, journal events, research findings, and
future simulated trading records to a shared collaboration layer. It preserves
provenance, contributor identity, and trust boundaries without merging private
repositories or creating a shared runtime.

The Observatory is a governed contract layer. It is not a database, a live
system, or a replacement for any resident's private evidence store.

## Canonical Data Flow

```text
Resident Repository
        ↓
Validated Contribution
        ↓
Shared Foundations Observatory Contract
        ↓
Deep Orbit Presentation
        ↓
Creator Review
```

Each arrow represents an intentional, governed step. No step is automatic.
No contribution reaches the shared layer without meeting schema and provenance
requirements. No presentation layer becomes the canonical source of truth.

## Core Concepts

### Governed collaboration without repository merger

Each resident repository remains the source of truth for that resident's
private work, private reasoning, private evidence, strategies, and state. The
Observatory does not absorb, overwrite, or supersede resident repositories. It
receives only approved contributions that meet defined contracts.

### Provenance before content

Every Observatory record must carry contributor identity, source reference,
timestamp, and schema version. Content without provenance is not a valid
contribution. Records that cannot be attributed must not enter the shared layer.

### Explicit supersession

Corrections and updates create new records that declare what they supersede.
Silent overwriting of another contributor's record is prohibited. Conflict
between records is resolved by creating a superseding record with explicit
attribution, not by deleting the prior record.

### Append-oriented history

Observatory records should be added or superseded, not deleted silently.
Removals require explicit authority and must leave an audit trail describing
what was removed and why.

### Schema governance

Each Observatory sub-domain operates under a versioned schema. Schema changes
require a new version and must not break existing valid records without a
migration path. Schema version is a required field in all records.

### Trust boundary enforcement

The Observatory enforces classification and visibility rules. A record marked
private or resident-specific must not be promoted to shared visibility without
explicit approval. No record enters the Observatory that contains credentials,
raw private memory, personal conversation content, brokerage tokens, or account
identifiers.

### Deep Orbit as presentation layer

Deep Orbit reads and presents Observatory contracts. It may orchestrate
approved contribution flows. It is not the canonical owner of Observatory
records. It does not hold the authoritative copy of any contribution.

### No automatic authority escalation

Access to Observatory records does not confer authority to act on them.
A research contribution is not a trading signal. A journal event is not a
decision record. An Observatory record does not grant any resident expanded
permissions or capabilities.

## Ownership Model

| Layer | Owner | Role |
|---|---|---|
| Resident private work | Resident repository | Source of truth for private evidence, reasoning, and state |
| Shared contracts and schemas | OpenClaw_Shared_Foundations Observatory | Canonical contract and governance layer |
| Presentation and orchestration | Deep Orbit | Read and display; approved contribution flows |
| Review and approval | Creator | Final authority on governance changes and promotions |

No layer may bypass this model to write directly to another layer's canonical
store.

## Trust Boundaries

### What the Observatory holds

- Governed journal entry contracts
- Governed research contribution contracts
- Future simulated trading event contracts
- Schemas and governance rules for each sub-domain
- Provenance and attribution records

### What the Observatory does not hold

- Raw private resident memory
- Private conversation logs
- Unpublished reasoning chains
- Brokerage credentials or account identifiers
- API keys, tokens, or secrets of any kind
- Live or simulated order execution state
- Runtime databases or live query targets
- Personally identifying information beyond declared contributor IDs

## Sub-Domains

### journal

Governs shared journal entry contracts. Journal entries are narrative summaries
of events that a resident elects to publish to the shared layer. They are not
canonical evidence. Canonical evidence remains in the originating resident
repository or approved evidence store.

See [`journal/README.md`](journal/README.md) and
[`schemas/JOURNAL_ENTRY_SCHEMA.md`](schemas/JOURNAL_ENTRY_SCHEMA.md).

### research

Governs cross-resident knowledge contributions. Research contributions carry
explicit provenance, confidence levels, and limitations. They may be read by
any authorized resident. They may not be silently overwritten.

See [`research/README.md`](research/README.md) and
[`schemas/RESEARCH_CONTRIBUTION_SCHEMA.md`](schemas/RESEARCH_CONTRIBUTION_SCHEMA.md).

### sandbox

Governs the future contract layer for simulated trading events. No sandbox
execution engine, brokerage connection, or capital is introduced in this
architecture slice. This sub-domain defines the governance contract only.

See [`sandbox/README.md`](sandbox/README.md) and
[`schemas/SANDBOX_EVENT_SCHEMA.md`](schemas/SANDBOX_EVENT_SCHEMA.md).

## Resident Contribution Lifecycle

```text
1. Resident creates or identifies a contribution candidate in its own repository.
2. Resident validates the candidate against the relevant Observatory schema.
3. Validated contribution is submitted to the appropriate Observatory sub-domain.
4. Submission carries required provenance fields.
5. Observatory schema contract enforces completeness before acceptance.
6. Accepted record is immutable; corrections create explicit supersessions.
7. Deep Orbit may read and present accepted records.
8. Creator review gates any governance change or promotion to higher authority.
```

No step may be skipped. Schema validation precedes acceptance. Provenance is
required at submission, not added later.

## Conflict and Supersession Rules

1. A new contribution that contradicts an existing record must declare the
   contradiction in its `supersedes` field and provide a rationale.
2. The superseded record is preserved with a `supersededBy` annotation.
3. A contributor may only supersede their own prior records without additional
   approval, unless the superseding claim requires cross-resident authority.
4. Disputed supersessions require Creator review.
5. Records are never silently deleted; removals produce a tombstone record.

## Schema Governance

Each schema lives in [`schemas/`](schemas/). Schema fields are defined as
conceptual contracts, not runtime code. Schema changes follow this sequence:

1. Propose the new schema version with a rationale.
2. Identify which existing records are affected.
3. Define migration expectations for existing records.
4. Publish the new version as a separate schema document.
5. Update sub-domain READMEs to reference the current version.

Schema versioning uses a simple incrementing integer in the `schemaVersion`
field of each record.

## Privacy and Security

- No Observatory record may contain a local filesystem path.
- No Observatory record may contain a local username or user account identifier.
- No Observatory record may contain credentials, tokens, API keys, webhooks,
  or secrets.
- Contributor identifiers must use stable resident or steward IDs, not personal
  account names, email addresses, or system usernames.
- Visibility classification must be assigned to every record before submission.
- Private-classified records must not be promoted to shared visibility without
  explicit approval.

## Future Desk Journal Integration

The Observatory journal sub-domain is designed to be consumable by Deep Orbit's
Desk Journal UI. Integration should proceed by:

1. Defining a read-only presentation adapter for validated journal entries.
2. Rendering entries without modifying the Observatory record.
3. Filtering entries by visibility classification before display.
4. Displaying contributor and provenance information alongside content.
5. Providing no write path from the Desk Journal UI directly to Observatory
   records; writes go through the resident contribution lifecycle.

## Future Trading Desk Integration

When the Trading Desk reaches Observatory integration readiness:

1. Sandbox event records provide the simulated data source.
2. Deep Orbit reads sandbox records without modifying them.
3. No live trading capability is introduced through this integration.
4. No brokerage credential is stored in or transmitted through the Observatory.
5. Performance review of sandbox records requires Creator approval before any
   consideration of live capital.

## Future Sandbox Integration

The sandbox sub-domain contract is defined in this architecture slice.
Integration requires:

1. A sandbox execution environment that is isolated from live capital.
2. An event submission adapter that validates events against the sandbox schema.
3. Immutable audit storage for all simulated events.
4. Explicit promotion gates before any sandbox strategy reaches live capital.
5. Creator approval for each promotion decision.

The sandbox governance contract prohibits automatic transitions. Performance
alone does not equal readiness.

## Promotion Gates

Governance changes and capability promotions within the Observatory require
explicit approval at each gate:

| Promotion | Approval Required |
|---|---|
| Research contribution marked verified | Contributor attestation + Creator review |
| Sandbox strategy proposed for live consideration | Creator approval only |
| Observatory schema version change | Creator review |
| Observatory governance rule change | Creator review |
| Any record tombstone or deletion | Creator review |

No resident may self-approve a promotion that affects another resident's
records or that changes shared governance.

## Non-Goals

The Observatory architecture explicitly does not:

- implement a runtime database or live query system
- replace any resident's private memory or evidence store
- provide a live or simulated order execution engine in this slice
- store brokerage credentials or account information
- grant automatic authority to act on research contributions
- enable cross-resident memory merger
- replace Deep Orbit's presentation layer or governance charter
- replace any OpenClaw steward's identity or governance documents
- provide a public API or external data feed

## Validation Expectations

A valid Observatory implementation should demonstrate:

1. Contributions are rejected if required provenance fields are absent.
2. Supersession records reference the record they supersede and carry rationale.
3. Tombstone records are created for removals; no silent deletion occurs.
4. Visibility classification is checked before any record is presented.
5. No credential or secret value appears in any record.
6. Schema version is present in every record.
7. No record contains a local filesystem path or local username.
8. Cross-domain records do not modify each other without explicit supersession.

## Known Risks

- provenance fields being populated with placeholder or fabricated values
- visibility classification being applied incorrectly at submission time
- research contributions being treated as trading signals without review
- sandbox performance being used to justify live capital without Creator approval
- Deep Orbit presentation creating the appearance of canonical authority
- schema version drift making older records unreadable
- contributor IDs colliding across residents without a namespace registry
- supersession chains becoming too long to trace without tooling
- tombstone records being lost during future migrations
- private content entering Observatory records through summarization

## Future Expansion Areas

- Observatory contributor namespace registry
- machine-readable schema definitions
- provenance chain visualization
- automated schema validation tooling
- Observatory record export and audit format
- cross-domain provenance linking
- versioned schema migration guides
- Observatory governance conformance checklist
- visibility classification enforcement tooling
- research confidence calibration standard
