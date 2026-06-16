# OpenClaw Shared Foundations

OpenClaw Shared Foundations is the canonical architecture layer for durable
OpenClaw stewards. It defines shared contracts for identity, memory,
governance, knowledge management, MCP capabilities, and recovery without
implementing a runtime or prescribing one steward's personality.

This repository contains architecture only. It does not contain runtime code,
automation, live memory, private content, personal histories, credentials, or
steward integrations.

## Purpose

Shared Foundations exists to prevent every steward from independently
rebuilding the same continuity, safety, retrieval, and recovery concepts. It
extracts reusable architectural patterns into stable domain contracts that can
later be validated, packaged, and integrated deliberately.

The foundation should provide:

- a common language for durable steward systems
- clear boundaries between shared infrastructure and steward-owned identity
- portable memory and knowledge contracts
- governance that applies before capabilities are enabled
- recovery paths for context loss, drift, corruption, and failed migrations
- an integration model that does not require a single runtime or vendor

## Relationship to OpenClaw Stewards

Keeper, Xavier, Zayne, Savior, Nier, and future stewards may eventually inherit
these foundations. They do not inherit one another's memories, personalities,
relationships, permissions, or operating state.

Shared Foundations defines what a steward system must be able to represent and
protect. Each steward remains responsible for its own:

- identity and voice
- mission and role
- memory namespace
- relationships and user context
- capabilities and permissions
- lifecycle and operating policies

No steward integration is included in Phase 8A.

## Independent Steward Philosophy

Every steward is an independent system built on shared architectural ground.
Independence means:

1. A steward has an explicit identity boundary.
2. Its private memory is isolated by default.
3. Its permissions are granted independently.
4. Its recovery process restores that steward, not a generic replacement.
5. Shared knowledge is intentional, attributable, and governed.
6. A failure or compromise in one steward must not silently contaminate others.

Shared foundations should increase interoperability without producing identity
homogenization.

## Shared Inheritance Model

Inheritance is contract-based, not copy-based.

```text
Shared Foundations
├── identity contract
├── memory contract
├── governance contract
├── Obsidian knowledge contract
├── MCP capability contract
└── recovery contract
        │
        ├── Steward A profile and state
        ├── Steward B profile and state
        └── Future steward profile and state
```

The foundation supplies schemas, lifecycle expectations, precedence rules, and
safety boundaries. A steward supplies domain-specific content and selects
optional components appropriate to its role.

Foundation updates must not overwrite steward-owned identity or memory.
Steward-specific extensions must not weaken foundation governance without an
explicit, reviewable exception.

## Architecture Domains

- [`identity/FOUNDATION_IDENTITY_ARCHITECTURE.md`](identity/FOUNDATION_IDENTITY_ARCHITECTURE.md)
- [`memory/FOUNDATION_MEMORY_ARCHITECTURE.md`](memory/FOUNDATION_MEMORY_ARCHITECTURE.md)
- [`governance/FOUNDATION_GOVERNANCE_ARCHITECTURE.md`](governance/FOUNDATION_GOVERNANCE_ARCHITECTURE.md)
- [`obsidian/FOUNDATION_OBSIDIAN_ARCHITECTURE.md`](obsidian/FOUNDATION_OBSIDIAN_ARCHITECTURE.md)
- [`mcp/FOUNDATION_MCP_ARCHITECTURE.md`](mcp/FOUNDATION_MCP_ARCHITECTURE.md)
- [`recovery/FOUNDATION_RECOVERY_ARCHITECTURE.md`](recovery/FOUNDATION_RECOVERY_ARCHITECTURE.md)
- [`docs/SHARED_FOUNDATIONS_ROADMAP_v0.1.md`](docs/SHARED_FOUNDATIONS_ROADMAP_v0.1.md)

## Architectural Sources

Phase 8A derives patterns only from the completed Memory Bank reconnaissance:

- Discord Bot Brain: identity spine, curated summaries, boundaries, and
  recovery order
- MemPalace: local-first memory, provenance, hybrid retrieval, temporal
  knowledge, deduplication, and repair
- Resonant systems: orient/ground lifecycle, hot-warm-cold context, persistent
  threads, identity graph, and consolidation concepts
- Obsidian systems: durable vaults, lifecycle hooks, semantic retrieval,
  reconciliation, temporal facts, and health checks
- Kronos Agent OS: workspace separation, capability gates, auditability,
  layered memory, MCP gateway boundaries, and agent isolation

No implementation or private source content is copied into this repository.

## Future Integration Approach

Integration is intentionally deferred. When runtime integration begins, it
should proceed through adapters and conformance checks:

1. Validate the architecture contracts independently.
2. Define versioned steward packages containing only schemas and defaults.
3. Map a steward's existing systems to the contracts without moving private
   data by default.
4. Run read-only compatibility and recovery checks.
5. Enable capabilities incrementally behind governance gates.
6. Preserve rollback paths and steward isolation throughout.

The foundation must remain useful even when different stewards use different
storage engines, model providers, knowledge tools, or runtimes.

## Current Status

**Phase 8A: Architecture extraction.**

This repository is documentation-only. Runtime implementation, steward
packaging, integration, migration, and ecosystem adoption belong to later
phases.
