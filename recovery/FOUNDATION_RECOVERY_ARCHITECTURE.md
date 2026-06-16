# Foundation Recovery Architecture

## Purpose

The recovery foundation defines how a steward returns to trustworthy operation
after identity drift, context compaction, memory corruption, failed migration,
tool failure, or partial data loss. Recovery restores the validated spine before
resuming deeper expression or automation.

## Core Concepts

### Recovery is ordered restoration

Restore in this order:

1. safety and governance
2. identity honesty
3. identity spine
4. current state
5. memory integrity
6. tool capability
7. optional automation and deeper behavior

### Stop performance first

When identity or memory is uncertain, the steward should reduce unsupported
claims and stylistic overperformance. It should state uncertainty and consult
sources of truth.

### Recovery anchors

Every steward needs an explicit ordered list of identity, state, governance,
and memory sources used during recovery.

### Snapshot before repair

Repair and migration begin with an inspectable backup or snapshot. Destructive
cleanup occurs only after verification.

### Dry-run and idempotency

Recovery operations should preview changes where possible and be safe to
repeat.

### Graceful degraded mode

A steward may operate with reduced memory or tools when integrity cannot be
verified, but must disclose the degraded state.

## Required Components

- **Recovery triggers:** identity drift, false recall, compaction, index
  failure, schema mismatch, corruption, missing tool, or failed migration
- **Recovery state model:** healthy, degraded, recovering, verification, and
  restored
- **Ordered recovery anchors:** governance, identity, current state, and memory
  sources
- **Backup contract:** what is captured, where, when, and how it is verified
- **Context recovery:** handoff, session summary, recent messages, and open work
- **Identity recovery:** reload and validate the steward's canonical spine
- **Memory recovery:** exact-store verification before rebuilding derived
  indexes
- **Migration recovery:** dry-run, collision reporting, rollback, and
  idempotency
- **Verification criteria:** tests proving restored retrieval, identity, scope,
  and permissions
- **Recovery log:** cause, actions, artifacts, verification, and remaining risk
- **Isolation:** failed recovery in one steward cannot modify another

## Optional Components

- automated integrity gates
- quarantining corrupt indexes
- periodic disaster-recovery exercises
- transcript indexing and session-chain reconstruction
- recovery dashboards
- checksummed manifests
- replica or secondary storage
- safe-mode steward profile
- operator alerts
- cross-backend rebuild tools

Automation may detect or assist recovery but should not silently rewrite
identity or private source material.

## Inheritance Strategy

Every steward inherits the recovery states, required artifacts, and
verification expectations. Each steward supplies:

- its recovery anchor order
- storage-specific backup procedures
- acceptable degraded capabilities
- operator and escalation contacts
- steward-specific recognition checks

Foundation recovery logic must remain storage-neutral and must not assume all
stewards share a runtime.

## Future Steward Integration

Before integration is considered complete, each steward should demonstrate:

1. identity restoration from canonical anchors
2. context restoration after compaction
3. memory operation with semantic retrieval disabled
4. recovery from stale or corrupt derived indexes
5. scoped deletion and restore
6. failed migration rollback
7. tool outage behavior
8. proof that recovery does not cross steward boundaries

Recovery validation should precede production automation.

## Known Risks

- backups containing unprotected private data
- corrupted backups being treated as authoritative
- summaries omitting critical identifiers or pending work
- repair tools rewriting verbatim sources
- recovery restoring obsolete permissions
- automatic recovery hiding unresolved corruption
- identity recovery becoming theatrical rather than evidence-based
- destructive cleanup occurring before verification
- migration merging separate steward namespaces
- recovery procedures depending on unavailable external services

## Future Expansion Areas

- canonical recovery manifest
- recovery conformance scenarios
- cryptographic integrity checks
- tiered backup and restore objectives
- steward safe-mode profiles
- cross-backend index reconstruction
- incident postmortem template
- ecosystem disaster-recovery standards
