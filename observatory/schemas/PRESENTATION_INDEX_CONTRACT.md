# Presentation Index Contract

## Purpose

This contract defines the governance rules and field requirements for a
presentation index. A presentation index is a derived, reproducible,
disposable artifact that Deep Orbit or another authorized presentation surface
generates from a valid resident publication. It is purpose-built for rendering
and must never become a canonical source of truth.

A presentation index is always secondary to the resident publication that
produced it. If the resident publication changes, the presentation index must
be discarded and regenerated. A presentation index does not hold or replace
canonical evidence.

This contract is resident-agnostic. Presentation indexes may be generated for
any resident whose publication conforms to the Resident Publication Contract.

See also:
- [`CANONICAL_EVIDENCE_CONTRACT.md`](CANONICAL_EVIDENCE_CONTRACT.md)
- [`RESIDENT_PUBLICATION_CONTRACT.md`](RESIDENT_PUBLICATION_CONTRACT.md)
- [`DEEP_ORBIT_READ_CONTRACT.md`](DEEP_ORBIT_READ_CONTRACT.md)

Schema version: 1

---

## Derived-Artifact Declaration

A presentation index is a **derived artifact**. This means:

1. It is reproducible: given the same resident publication and the same
   presentation rules, regenerating the index must produce an equivalent
   result.
2. It is disposable: a presentation index may be discarded and regenerated at
   any time without loss of canonical evidence, because canonical evidence lives
   in the resident's repository.
3. It is not canonical: a presentation index must never be treated as the
   source of truth for any field it contains. The resident publication and the
   resident's evidence store are the sources of truth.
4. It must not be promoted: a presentation index must never be elevated to
   canonical or archive status, even if it persists in storage beyond the
   generation that produced it.

---

## Freshness

Freshness is a contractual concept defined in this document. No separate
Freshness Contract is needed unless implementation evidence proves separation is
necessary.

**Definition:** A presentation index is **fresh** when it was generated from
the most recent valid resident publication and no superseding publication has
been received since generation.

**Definition:** A presentation index is **stale** when a newer valid resident
publication exists that the current index does not reflect, or when the
publication that produced it has been superseded by a higher `distributionVersion`
from the same resident.

**Staleness is not an error.** A stale index is a valid prior-state index. It
must be displayed with an explicit stale indicator. It must never be presented
as current.

`freshAt` records the UTC timestamp at which the index was confirmed fresh.
`freshnessSource` records the identity of the publication that produced the
fresh state (`publicationId` from the resident publication).

---

## Required Fields

### indexId

**Type:** string
**Required:** yes
**Description:** Stable unique identifier for this presentation index record.
Assigned at generation time. Recommended format:
`residentId-idx-YYYYMMDD-NNN`. Must never be reused.

### schemaVersion

**Type:** integer
**Required:** yes
**Description:** Version of this contract schema the index conforms to. Must
be `1` for records conforming to this version.

### residentId

**Type:** string
**Required:** yes
**Description:** The canonical identifier of the resident whose canonical
evidence produced the resident publication that this index was derived from.

### distributionVersion

**Type:** integer
**Required:** yes
**Description:** The `distributionVersion` of the resident publication this
index was derived from. Used to detect stale indexes: if a newer publication
arrives with a higher `distributionVersion`, this index is stale.

### generatedAt

**Type:** ISO 8601 datetime string
**Required:** yes
**Description:** The UTC timestamp at which this index was generated.

### freshAt

**Type:** ISO 8601 datetime string
**Required:** yes
**Description:** The UTC timestamp at which this index was confirmed fresh, i.e.,
confirmed to reflect the then-current valid resident publication. May be the
same as `generatedAt` when generated immediately after a new valid publication
is received.

### freshnessSource

**Type:** string
**Required:** yes
**Description:** The `publicationId` of the resident publication from which this
index was derived. Used to trace freshness back to a specific publication event.

### visibility

**Type:** string
**Required:** yes
**Description:** Access classification for this index. Must be one of:
`private`, `resident-shared`, or `observatory`. Must not exceed the visibility
of the resident publication it was derived from. Promotions to broader
visibility require explicit approval.

### entries

**Type:** array of objects
**Required:** yes
**Description:** The ordered list of presentation entries derived from the
resident publication's `artifactRefs`. Each entry represents one canonical
artifact. An empty array is valid when the resident publication contains no
artifact references.

Each entry object must include at minimum:
- `artifactRef` (string): the namespaced artifact identifier
  (`residentId:artifactId`)
- `residentId` (string): the resident that owns the artifact
- `evidenceState` (string): must be `canonical`; entries with any other state
  must be excluded

Each entry may additionally include approved presentation metadata (see
Approved Presentation Metadata below).

### provenanceRef

**Type:** string
**Required:** yes
**Description:** The `publicationId` of the resident publication this index was
derived from. Equivalent to `freshnessSource`. Preserved for cross-document
traceability.

---

## Approved Presentation Metadata

Index entries may include the following presentation-oriented fields. These
fields are derived from resident publication data and canonical artifact
metadata. They must not embed or replace canonical evidence content.

| Field | Description |
|---|---|
| `latestObservation` | Timestamp or summary of the most recent canonical observation the artifact represents |
| `health` | A presentation-ready status label derived from canonical evidence (e.g., `healthy`, `degraded`, `unavailable`) |
| `freshness` | A freshness label for this specific entry (`fresh`, `stale`) |
| `artifactCount` | Count of canonical artifacts included in the publication for this resident |
| `summary` | A short human-readable summary derived from canonical evidence; must not reproduce private details |
| `governanceStatus` | A label describing the governance standing of the evidence (e.g., `canonical`, `review-pending`) |
| `timestamps` | Relevant timestamps (e.g., `publishedAt`, `stateChangedAt`) carried from canonical evidence metadata |
| `provenanceReferences` | One or more provenance references tracing to the originating resident publication |
| `sourceResidentId` | The `residentId` of the resident whose canonical evidence is represented |
| `distributionVersion` | The `distributionVersion` of the publication that produced this entry |

No field in this list may be used to embed the full content of canonical
evidence or to replace canonical evidence with a summarized copy that becomes
the authoritative version.

---

## Reproducibility Expectations

1. Regenerating an index from the same resident publication must produce an
   index with equivalent `entries` content, even if `indexId` and `generatedAt`
   differ.
2. A presentation surface must not treat index regeneration as a canonical
   event. The canonical event is the resident's evidence admission, not the
   index derivation.
3. Index generation order for `entries` may vary by implementation, but must
   be deterministic given the same input publication.

---

## Disposal and Regeneration Behavior

1. When a new valid resident publication is received with a higher
   `distributionVersion`, the current index must be regenerated.
2. The prior index may be retained for a transition period with an explicit
   stale indicator but must not be presented as current.
3. A stale index must be clearly labeled. The consumer must not present stale
   data as current under any circumstances.
4. Regeneration does not require Creator approval. Disposal of the prior index
   is automatic and safe because canonical evidence is preserved in the
   resident's repository.

---

## Stale-Index Behavior

1. When the current index is known to be stale (a newer publication exists),
   the presentation surface must display a stale indicator alongside any data
   from the index.
2. The stale indicator must be visible and unambiguous to the consumer.
3. A stale index must never be silently promoted to current status.
4. If regeneration fails, the presentation surface must retain the last known
   valid index with a stale indicator and must not fall back to presenting
   stale data without the indicator.

---

## Unavailable-Publisher Behavior

When the resident's publication source is unavailable:

1. The presentation surface must retain the last known valid index.
2. The retained index must be displayed with an explicit unavailability
   indicator, distinct from a normal stale indicator.
3. The presentation surface must not fabricate or infer updated entries from
   the unavailable publisher.
4. When the publisher becomes available again, the presentation surface must
   re-evaluate currency and either confirm freshness or regenerate.

---

## Governance Rules

1. A presentation index must never be treated as canonical evidence.
2. A presentation index must never be promoted to archive or canonical status.
3. Pending and rejected evidence must never appear in a presentation index,
   directly or indirectly.
4. A presentation index entry must only exist for artifacts with
   `evidenceState` of `canonical`.
5. Deep Orbit must not write to or alter canonical evidence in the resident's
   repository based on the contents of a presentation index.
6. Indexes are regenerated, not corrected in place. If an index contains an
   error, it is discarded and regenerated from the current valid publication.

---

## Compatibility Reference: Sylus Scheduled Observation

The following describes how this contract maps to the Sylus Scheduled
Observation Foundation. This is a compatibility example, not a runtime
implementation.

After Sylus produces a valid resident publication, Deep Orbit generates a
presentation index from it. The index contains one entry per canonical Sylus
observation artifact. When Sylus produces a new publication (higher
`distributionVersion`), Deep Orbit discards the prior index and regenerates.
If Sylus is unavailable, Deep Orbit retains the last index with an
unavailability indicator.

```text
Canonical Sylus evidence
        ↓
Resident publication (Sylus)
        ↓
Presentation index     ← this contract governs this artifact
        ↓
Deep Orbit read
```

---

## Non-Goals

This contract does not define:

- canonical evidence fields or admission rules (see
  `CANONICAL_EVIDENCE_CONTRACT.md`)
- resident publication fields or validation (see
  `RESIDENT_PUBLICATION_CONTRACT.md`)
- Deep Orbit consumer obligations (see `DEEP_ORBIT_READ_CONTRACT.md`)
- runtime ingestion automation or schedulers
- broker connectivity or live data feeds
- paper or live trading behavior
- a storage format or file encoding
