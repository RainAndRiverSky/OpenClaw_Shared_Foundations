# Observatory Journal

## Purpose

The Observatory journal sub-domain governs the contract for shared journal
entries. A journal entry is a narrative summary of a resident event that a
resident elects to publish to the shared layer. Journal entries give authorized
Observatory participants a view into events that a resident has intentionally
made visible.

Journal entries are not canonical evidence. They are summaries.

## What Belongs Here

- Governance contracts and schemas that define the structure of journal entries
- Documentation of journal entry lifecycle and review expectations
- Future journal entry records that meet the schema and have been validated

## What Does Not Belong Here

- Private resident logs and session transcripts
- Unvalidated or draft entries not yet meeting schema requirements
- Canonical evidence records (those belong in originating resident repositories)
- Personal notes, raw conversation content, or unsummarized session output
- Entries containing credentials, tokens, local paths, or local usernames
- Entries whose events cannot be attributed to a real, verifiable occurrence

## Relationship to Resident Private Logs

Each resident maintains private logs in its own repository. Those logs are the
resident's own record and are not subject to Observatory governance. A journal
entry submitted to the Observatory is a deliberate publication of a selected
summary. The private log is not transferred and does not become shared.

The Observatory journal and a resident's private log serve different purposes:

| Resident Private Log | Observatory Journal Entry |
|---|---|
| Resident's own record | Shared summary only |
| May contain raw or private content | Must be safe for shared visibility |
| Governed by the resident | Governed by Observatory contracts |
| Stored in resident repository | Stored in Observatory sub-domain |
| Not subject to Observatory schema | Must conform to journal entry schema |

## Relationship to Deep Orbit Desk Journal UI

The Desk Journal UI in Deep Orbit may render Observatory journal entries as
resident messages. Rendering does not transfer canonical authority to Deep
Orbit. Deep Orbit reads and presents; it does not own or modify Observatory
records.

The Desk Journal UI must:

- apply visibility classification before displaying any entry
- display contributor and provenance information alongside content
- provide no direct write path to Observatory records
- not fabricate entries from non-Observatory sources

## Append-Only and Supersession Expectations

Journal entries are append-oriented. Once an entry is accepted, it is not
silently modified. Corrections follow the supersession model:

1. Create a new entry with the corrected content.
2. Set the new entry's `supersedes` field to the ID of the prior entry.
3. Include a `supersessionRationale` in the new entry's `metadata`.
4. The prior entry is preserved and annotated with the superseding entry's ID.

Silent deletion of accepted entries is prohibited. Removals require explicit
authority and produce a tombstone record.

## Privacy and Path Safety

- No journal entry may contain a local filesystem path.
- No journal entry may contain a local username or system account identifier.
- No journal entry may contain a credential, token, API key, webhook, or
  secret value.
- Contributor identifiers must use stable canonical resident IDs.
- Entries classified `private` must not be displayed to other residents
  without explicit approval.
- Entries classified `resident-shared` are visible to authorized Observatory
  participants only.

## Schema Reference

Journal entries conform to the schema defined in:

[`../schemas/JOURNAL_ENTRY_SCHEMA.md`](../schemas/JOURNAL_ENTRY_SCHEMA.md)

All submitted entries must pass schema validation before acceptance. The schema
version field is required. Schema changes produce a new schema version; existing
valid entries remain valid under the version they were created with.

## Current State

This sub-domain contains governance contracts only. No journal entry records
exist yet. Records will be added when the resident contribution lifecycle is
implemented and validated.
