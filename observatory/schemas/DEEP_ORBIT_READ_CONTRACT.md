# Deep Orbit Read Contract

## Purpose

This contract defines the obligations that Deep Orbit (or any authorized
presentation surface) must fulfill when consuming a presentation index derived
from a resident publication. These obligations protect the integrity of
canonical evidence, preserve resident ownership, and ensure consumers never
misrepresent stale or ineligible data as current canonical truth.

This contract governs read-only consumption. Deep Orbit has no write path into
resident evidence through this contract.

See also:
- [`CANONICAL_EVIDENCE_CONTRACT.md`](CANONICAL_EVIDENCE_CONTRACT.md) — defines
  evidence eligibility
- [`RESIDENT_PUBLICATION_CONTRACT.md`](RESIDENT_PUBLICATION_CONTRACT.md) —
  defines the publication Deep Orbit receives
- [`PRESENTATION_INDEX_CONTRACT.md`](PRESENTATION_INDEX_CONTRACT.md) — defines
  the index Deep Orbit generates and reads

Schema version: 1

---

## Consumer Obligations

### 1. Verify presentation index schema compatibility

Before rendering any data from a presentation index, Deep Orbit must confirm
that the index's `schemaVersion` is a version it is capable of interpreting.
If the `schemaVersion` is unrecognized or incompatible, Deep Orbit must not
render the index and must fail closed (see obligation 9).

### 2. Verify visibility before rendering

Deep Orbit must check the `visibility` field of the presentation index before
rendering any content from it. Content classified as `private` must not be
rendered in a shared context. Content classified as `resident-shared` must only
be rendered in authorized resident-specific views. Promotions to broader
visibility must not be performed by Deep Orbit unilaterally.

### 3. Verify artifact eligibility

For each entry in the presentation index, Deep Orbit must confirm that the
entry's `evidenceState` is `canonical`. Entries with any other `evidenceState`
must be excluded from rendering. Deep Orbit must not render evidence in
`pending`, `ingested`, or `rejected` state under any circumstances.

If `evidenceState` cannot be determined for an entry, Deep Orbit must exclude
that entry and must not assume eligibility.

### 4. Display freshness or staleness accurately

Deep Orbit must display the freshness status of the index accurately:

- If the index is fresh (confirmed to reflect the most recent valid publication),
  freshness must be displayed or accessible to the consumer.
- If the index is stale (a newer publication exists or the publisher is
  unavailable), a stale or unavailable indicator must be displayed. The
  indicator must be visible and unambiguous.
- Stale data must never be presented as current.
- Deep Orbit must not suppress or hide the stale indicator to improve visual
  presentation.

### 5. Preserve provenance references

Deep Orbit must carry and display provenance references from the presentation
index without modification. Provenance references must not be stripped, altered,
or omitted from any rendered view that includes index content. If a view cannot
display provenance references, it must link to a view that can.

### 6. Never present stale data as current

This obligation is stated explicitly because it is the most safety-critical.
No rendering path, caching layer, fallback, or error-handling logic may result
in stale data being presented without a stale or unavailable indicator.

If the freshness status of an index cannot be established, Deep Orbit must
treat the index as stale and display accordingly. Deep Orbit must fail toward
explicit staleness, never toward silent currency.

### 7. Never treat the presentation index as canonical

Deep Orbit must not:

- use a presentation index entry as the authoritative record of canonical
  evidence
- cache a presentation index entry as a replacement for the resident's canonical
  evidence
- promote a presentation index to archive, canonical, or persistent authority
  status
- allow a presentation index to become the source of truth for any downstream
  system

If a downstream consumer requests canonical evidence, Deep Orbit must direct
that consumer to the resident's own repository or governed evidence store, not
to the presentation index.

### 8. Provide no direct mutation path into resident evidence

Deep Orbit must not expose any path by which a user action, API call, or
automated process can write to, modify, or delete canonical evidence in a
resident's repository through a presentation index or Deep Orbit's presentation
layer.

Read-only means read-only. If Deep Orbit facilitates a contribution flow (as
permitted by the Observatory Architecture), that flow must follow the governed
resident contribution lifecycle and must not bypass canonical evidence admission.

### 9. Fail closed when eligibility or visibility cannot be established

When Deep Orbit cannot establish that:
- the presentation index `schemaVersion` is compatible, or
- the `visibility` of the index permits rendering in the current context, or
- the `evidenceState` of an entry is `canonical`

then Deep Orbit must exclude the affected entry or index from rendering entirely.
It must not guess, default to permissive, or display partial data without
indicating that some content was excluded.

Failing closed means: render nothing rather than render something uncertain as
certain.

### 10. Preserve the last known valid index only with an explicit stale or unavailable indicator

If a newer publication has been received but index regeneration has not
completed, or if the publication source is unavailable, Deep Orbit may display
the last known valid index as a temporary fallback. This fallback display must
be accompanied by an explicit stale or unavailable indicator. The indicator must
not be dismissible or hidden by default.

Deep Orbit must attempt to refresh the index and must not indefinitely serve
a stale fallback without surfacing the staleness to the consumer.

---

## Prohibited Behaviors

The following behaviors are prohibited regardless of implementation context:

| Prohibited Behavior | Reason |
|---|---|
| Rendering a `pending` or `rejected` artifact entry | Violates evidence eligibility rules |
| Presenting stale index data as current without an indicator | Misrepresents evidence state to the consumer |
| Writing to or modifying canonical evidence in a resident repository | Violates resident ownership |
| Promoting a presentation index to canonical status | Violates derived-artifact declaration |
| Stripping provenance references from a rendered view | Breaks traceability |
| Rendering content from an incompatible `schemaVersion` | Risks silent misinterpretation |
| Assuming `canonical` state when `evidenceState` is absent | Violates fail-closed requirement |
| Silently suppressing the stale or unavailable indicator | Misrepresents currency to the consumer |

---

## Compatibility Reference: Sylus Scheduled Observation

The following describes how this contract applies to the Sylus Scheduled
Observation Foundation. This is a compatibility example, not a runtime
implementation.

When Deep Orbit receives a Sylus resident publication, it generates a
presentation index. When rendering the Observatory panel for Sylus:

1. Deep Orbit verifies the index `schemaVersion` is compatible.
2. Deep Orbit checks visibility before rendering any entry.
3. Deep Orbit excludes any entry whose `evidenceState` is not `canonical`.
4. Deep Orbit displays freshness based on `freshAt` and `distributionVersion`.
5. Deep Orbit preserves and displays provenance references for each entry.
6. If Sylus is unavailable, Deep Orbit shows the last known valid index with an
   explicit unavailability indicator.
7. Deep Orbit provides no path for a user to modify Sylus canonical evidence
   from the presentation panel.

```text
Canonical Sylus evidence
        ↓
Resident publication (Sylus)
        ↓
Presentation index
        ↓
Deep Orbit read     ← this contract governs this step
```

---

## Non-Goals

This contract does not define:

- how Deep Orbit renders or styles content (UI design is outside this contract)
- the internal architecture of Deep Orbit's rendering layer
- runtime adapter implementation details
- broker connectivity or live data feeds
- paper or live trading behavior
- canonical evidence admission logic (see `CANONICAL_EVIDENCE_CONTRACT.md`)
- resident publication generation logic (see `RESIDENT_PUBLICATION_CONTRACT.md`)
- presentation index generation logic (see
  `PRESENTATION_INDEX_CONTRACT.md`)
