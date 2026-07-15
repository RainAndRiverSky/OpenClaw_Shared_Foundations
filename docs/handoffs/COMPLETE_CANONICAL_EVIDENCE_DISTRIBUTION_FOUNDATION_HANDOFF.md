# Complete - Canonical Evidence Distribution Foundation Handoff

## Status

Documentation-only handoff.

No runtime code, automation, scheduler logic, ingestion logic, sandbox, paper
trading, broker connectivity, or Deep Orbit UI implementation is included in
this record.

## Purpose

Record the completion of the Sylus Scheduled Observation Foundation and define
the next Shared Foundations milestone candidate:

**Canonical Evidence Distribution**

This milestone is positioned in Shared Foundations because it defines the
long-term contract between resident-owned canonical repositories and
presentation systems such as Deep Orbit. It is not a Sylus-specific feature.

## Completed Foundation

The Sylus Scheduled Observation Foundation has verified the following
operational shape:

```text
LaunchAgent
-> Local runtime
-> Pending outbox
-> Creator-authorized validation
-> Canonical evidence
```

The completed foundation established:

- LaunchAgent scheduling
- local runtime deployment
- runtime provenance
- local logging
- observer validation
- atomic artifact publication
- pending outbox
- manual canonical ingestion
- duplicate protection
- canonical evidence preservation
- public documentation
- focused test coverage
- security and public-readiness review

The observer, outbox, and manual ingestion boundary are operational. The
remaining problem is not scheduled observation; it is service-context access
between canonical resident repositories and presentation services.

## Evidence State Vocabulary

The following state terms are preserved for future contract work:

- `pending`: locally produced, non-canonical, not visible to presentation
  systems.
- `ingested`: validated and admitted to the resident-owned canonical
  repository.
- `rejected`: invalid, malformed, conflicting, or unsafe; never canonical.
- `canonical`: present in the resident-owned source of truth.
- `observed`: describes runtime activity only; it does not imply canonical
  admission.

Pending and rejected artifacts must not be displayed as canonical evidence.

## Ownership Model

### Resident Repository

The resident repository owns:

- observer implementation
- evidence schemas and formats
- canonical evidence artifacts
- ingestion logic
- operational documentation
- resident-specific validation rules

### Deep Orbit

Deep Orbit owns:

- presentation
- orchestration
- resident workspace behavior
- Observatory surfaces
- read-only consumption of approved resident outputs

Deep Orbit must not become the canonical evidence owner and must not treat a
local mirror, cache, or presentation index as source of truth.

### Shared Foundations

Shared Foundations owns:

- reusable contracts
- governance vocabulary
- lifecycle rules
- cross-resident interoperability boundaries
- publication and distribution architecture

## Key Discovery

Repeated validation isolated macOS service-context restrictions around
LaunchAgents and external-volume repository access. Broadening operating-system
permissions is not the preferred architectural answer.

The reusable answer is a governed distribution boundary:

```text
Resident repository
-> Canonical evidence
-> Distribution publisher
-> Presentation index
-> Deep Orbit
```

This separates resident truth from presentation state.

## Canonical Evidence Distribution Milestone

### Purpose

Define a governed publication layer between resident-owned canonical evidence
and Deep Orbit presentation surfaces.

### Design Goals

1. Resident repositories remain canonical.
2. Deep Orbit never owns resident evidence.
3. Presentation indexes are derived artifacts.
4. Derived artifacts are reproducible.
5. Derived artifacts are disposable.
6. Canonical evidence always wins.
7. Pending evidence is never displayed.
8. Rejected evidence is never displayed.
9. Presentation indexes never become canonical.

### Presentation Index Scope

A resident presentation index may include approved metadata such as:

- latest observation
- health
- freshness
- artifact count
- summary
- governance status
- timestamps
- provenance references
- source resident identifier
- distribution version

The index does not replace canonical evidence.

## Contract Work To Define

The next milestone should inspect existing Shared Foundations contracts first
and determine whether a resident publication contract already exists. If not,
the smallest reusable contract should define:

- Canonical Evidence Contract
- Presentation Index Contract
- Resident Publication Contract
- Deep Orbit Read Contract
- Freshness Contract
- Provenance Contract
- Distribution Versioning
- Artifact Identity
- Lifecycle Rules

## Deferred Work

The following remain out of scope for this handoff and should not be started
from this record alone:

- automatic ingestion
- automatic publication
- sandbox implementation
- paper trading
- Evidence Record Identity
- cross-resident aggregation
- Trading Desk implementation
- broker connectivity
- live trading

## Next Implementation Milestone

Implement **Canonical Evidence Distribution** using the completed Scheduled
Observation Foundation as the first concrete source case.

Expected deliverables for the future milestone:

- publication contract
- presentation index schema
- publisher design or implementation plan
- adapter consumption contract
- freshness metadata
- provenance metadata
- resident compatibility rules

Scheduled Observation should not be redesigned. The distribution milestone
builds on it.

## Success Criteria For Future Milestone

Deep Orbit should eventually consume published presentation indexes rather than
raw repository evidence.

Canonical repositories remain source of truth. Shared Foundations owns the
contracts. Deep Orbit owns presentation. Residents own evidence.

## Restart Point

Next work should begin with:

```text
Shared Foundations
Milestone: Canonical Evidence Distribution
```

Recommended first steps:

1. Inspect existing Shared Foundations contracts.
2. Determine whether a resident publication contract already exists.
3. Prefer extension over replacement.
4. Design the smallest resident-agnostic contract capable of supporting Sylus
   now and future residents later.
5. Do not begin sandbox, paper trading, broker, or automatic-ingestion work.

## Confidence

Very high.

The Scheduled Observation architecture is mature enough to justify extracting
the publication boundary into Shared Foundations. This milestone generalizes
the architecture rather than solving a Sylus-only problem.
