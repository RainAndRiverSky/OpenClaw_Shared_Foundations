# Canonical Evidence Contract

## Purpose

This contract defines the governance rules and field requirements for a unit of
canonical evidence produced by a resident-owned repository. Canonical evidence
is the authoritative, resident-governed record of a fact, observation, or
finding. It remains in the resident's own repository and is never transferred to
a shared layer. Only canonical evidence may be referenced by a resident
publication for distribution to a presentation surface.

This contract is resident-agnostic. Any resident repository may adopt it.

Schema version: 1

---

## Artifact Identity

Every canonical evidence artifact must carry a stable, resident-namespaced
identity using the following format:

```
residentId:artifactId
```

- `residentId` is the resident's canonical identifier as declared in their
  identity record. It must not be a local username, email address, or system
  account name.
- `artifactId` is a stable identifier assigned by the resident at the time the
  artifact is created. It must be unique within the resident's namespace and
  must never be reused, even after rejection or deletion.

**Examples:**

```
sylus:obs-evidence-20260714-001
sylus:obs-evidence-20260714-002
```

No centralized artifact registry is required. Namespace collision is prevented
by the `residentId` prefix. If a centralized registry becomes necessary,
that requirement must be established by concrete implementation evidence before
one is mandated.

---

## Required Fields

### artifactId

**Type:** string
**Required:** yes
**Description:** The resident-local stable identifier for this artifact. Together
with `residentId`, forms the full namespaced identity `residentId:artifactId`.
Must not be reused.

### schemaVersion

**Type:** integer
**Required:** yes
**Description:** Version of this contract schema the artifact conforms to. Must
be `1` for artifacts conforming to this version.

### residentId

**Type:** string
**Required:** yes
**Description:** The canonical identifier of the resident that owns and produced
this artifact. Must not be a local username, email address, or system account
name.

### evidenceState

**Type:** string
**Required:** yes
**Description:** The current admission state of this artifact. Permitted values
are defined below. This field must be kept current by the resident's own
processes.

### stateChangedAt

**Type:** ISO 8601 datetime string
**Required:** yes
**Description:** The UTC timestamp of the most recent `evidenceState` change.
Must be updated whenever `evidenceState` changes.

### sourceReference

**Type:** string
**Required:** yes
**Description:** A stable reference to the source within the resident's own
repository or governed evidence store from which this artifact originates.
Must not be a local filesystem path. Use repository-relative paths or stable
document identifiers.

### provenanceChain

**Type:** array of strings
**Required:** yes
**Description:** An ordered list of namespaced artifact identifiers
(`residentId:artifactId`) tracing the lineage of this artifact, oldest first,
with the current artifact's namespaced ID appended last. For a new artifact with
no predecessors, this contains only the current artifact's namespaced ID. Must
never be truncated.

---

## Evidence States

### `pending`

The artifact has been created or submitted for admission review but has not yet
been evaluated. Pending artifacts are not eligible for presentation. A pending
artifact must never appear in a presentation index.

### `ingested`

The artifact has been received and is actively under review or processing by the
resident's own evidence pipeline. Ingested artifacts are not yet admitted as
canonical. An ingested artifact must never appear in a presentation index.

### `rejected`

The artifact failed admission review. Rejected artifacts are preserved for audit
purposes but are never eligible for presentation. A rejected artifact must never
appear in a presentation index. Rejection must produce a `rejectionReason`
annotation (see Rejection Behavior below).

### `canonical`

The artifact has passed all admission checks and is confirmed as resident
canonical evidence. Only canonical artifacts may be referenced by a resident
publication. Only canonical artifacts are eligible to appear in a presentation
index.

**`observed` is runtime activity vocabulary only.** It must not be used as an
evidence admission state.

---

## State Transition Rules

### Allowed Transitions

| From | To | Meaning |
|---|---|---|
| `pending` | `ingested` | Artifact received, review in progress |
| `pending` | `rejected` | Artifact failed admission immediately |
| `ingested` | `canonical` | Artifact passed all admission checks |
| `ingested` | `rejected` | Artifact failed admission after review |
| `canonical` | `rejected` | Previously admitted artifact retroactively failed |

### Invalid Transitions

| Transition | Reason |
|---|---|
| `rejected` → `canonical` | Rejected evidence must not be silently rehabilitated. A new artifact with a new `artifactId` and updated evidence must be submitted. |
| `rejected` → `pending` | Rejection is a terminal determination for that artifact. |
| `canonical` → `pending` | Canonical evidence does not regress to pending. |
| `canonical` → `ingested` | Canonical evidence does not regress to in-review. |
| Any → any (without updating `stateChangedAt`) | A state change without a timestamp update is a contract violation. |

---

## Presentation Eligibility Rules

1. An artifact with `evidenceState` of `pending` must never appear in a
   presentation index.
2. An artifact with `evidenceState` of `ingested` must never appear in a
   presentation index.
3. An artifact with `evidenceState` of `rejected` must never appear in a
   presentation index.
4. Only an artifact with `evidenceState` of `canonical` may be referenced by a
   resident publication and appear in a derived presentation index.
5. Presentation eligibility is re-evaluated at each resident publication
   generation. Evidence that was canonical at prior publication time but has
   since been rejected must not be carried forward into new publications.

---

## Rejection Behavior

When an artifact is rejected:

1. The `evidenceState` field is set to `rejected`.
2. The `stateChangedAt` field is updated to the rejection timestamp.
3. A `rejectionReason` annotation is attached, stating in plain language why the
   artifact failed admission. The reason must not be left blank.
4. The artifact record is preserved in the resident's evidence store for audit
   purposes.
5. The artifact is permanently ineligible for presentation, even if a later
   process determines the underlying evidence was valid. A new artifact with a
   new `artifactId` must be created if re-admission is warranted.

---

## Path and Identity Safety Rules

1. No canonical evidence artifact may contain a local filesystem path.
2. No canonical evidence artifact may contain a local username or system account
   identifier.
3. No canonical evidence artifact may contain credentials, API keys, tokens,
   webhooks, or secrets of any kind.
4. `residentId` must use the resident's stable canonical identifier, not any
   system-level or personal account identifier.
5. `sourceReference` must be expressed as a repository-relative or
   protocol-prefixed stable reference, never as an absolute path on any local
   machine.

---

## Governance Rules

1. Canonical evidence ownership remains with the resident at all times. This
   contract does not transfer ownership.
2. Deep Orbit may not write to, modify, or silently alter any artifact governed
   by this contract.
3. The resident's own admission process determines whether an artifact reaches
   `canonical` state. No external system may promote an artifact to `canonical`
   without the resident's explicit admission logic.
4. This contract is resident-agnostic. All conforming residents must use the same
   field names, state values, and transition rules defined here.
5. Extension fields may be added by a resident in `metadata` without changing
   the contract schema version, provided they do not conflict with contract
   field names.

---

## Optional Fields

### metadata

**Type:** object
**Required:** no
**Description:** Extensible key-value structure for resident-specific
supplementary information. Must not contain credentials, tokens, local paths, or
local usernames. Must not override or shadow any required field.

### rejectionReason

**Type:** string
**Required:** conditionally — required when `evidenceState` is `rejected`
**Description:** A plain-language statement of why this artifact failed
admission. Must not be empty for rejected artifacts.

---

## Compatibility Reference: Sylus Scheduled Observation

The following describes how the Sylus Scheduled Observation Foundation maps
conceptually to this contract. This is a compatibility example, not a runtime
implementation.

Sylus produces scheduled observation records in its own repository. Each
observation that passes Sylus's internal validation enters the evidence pipeline
as a `pending` artifact, advances to `ingested` during processing, and is
admitted as `canonical` upon successful validation. Observations that fail
validation are `rejected` and preserved for audit. Only `canonical` Sylus
observations are eligible to be referenced in a Sylus resident publication and
subsequently rendered in a Deep Orbit presentation index.

The full conceptual flow is:

```text
Canonical Sylus evidence
        ↓
Resident publication (Sylus)
        ↓
Presentation index
        ↓
Deep Orbit read
```

No step in this flow is automatic. Each step requires the prior step to
have produced a valid, schema-conformant output.

---

## Non-Goals

This contract does not define:

- a runtime database schema or query interface
- a specific file format or encoding
- an ingestion automation or scheduler
- a broker connection or live data feed
- a centralized artifact registry
- Deep Orbit UI behavior beyond eligibility rules
- the Resident Publication Contract (see `RESIDENT_PUBLICATION_CONTRACT.md`)
- the Presentation Index Contract (see `PRESENTATION_INDEX_CONTRACT.md`)
- the Deep Orbit Read Contract (see `DEEP_ORBIT_READ_CONTRACT.md`)
