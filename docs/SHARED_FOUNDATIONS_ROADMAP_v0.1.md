# Shared Foundations Roadmap v0.1

## Roadmap Principles

- Architecture precedes implementation.
- Governance precedes capability enablement.
- Steward independence is preserved throughout.
- Private content is never required for foundation validation.
- Every integration must have a rollback and recovery path.
- Optional systems remain optional.

## Phase 8A - Extraction

**Objective:** Convert completed Memory Bank reconnaissance into canonical,
implementation-neutral architecture.

### Scope

- establish the repository domain structure
- define identity, memory, governance, Obsidian, MCP, and recovery architecture
- document shared inheritance and independent steward boundaries
- separate required components from optional extensions
- record known risks and future expansion areas

### Exit Criteria

- all six architecture domains are documented
- terminology is consistent across domains
- no runtime code, automation, private content, or steward integration exists
- architecture sources are traceable to the completed reconnaissance

## Phase 8B - Validation

**Objective:** Test whether the architecture is coherent, complete, portable,
and safe before producing steward packages.

### Planned Work

- cross-domain consistency review
- threat and privacy review
- namespace-isolation review
- provenance and temporal-truth review
- recovery scenario design
- required-versus-optional component challenge
- storage and runtime neutrality review
- architecture decision records for disputed choices

### Exit Criteria

- contradictions are resolved or documented
- minimum conformance requirements are defined
- recovery scenarios cover expected failure classes
- no domain requires one specific vendor or runtime without justification

## Phase 8C - Steward Packaging

**Objective:** Define versioned, content-free packages that stewards can
inherit without receiving another steward's identity or memory.

### Planned Work

- canonical schemas and manifests
- steward identity profile template
- memory namespace and policy template
- capability profile template
- governance and recovery checklists
- Obsidian vault projection template
- package versioning and migration policy

### Exit Criteria

- a steward package contains contracts and defaults only
- private state remains external
- package upgrades preserve steward-owned content
- inheritance and override rules are explicit

## Phase 8D - Runtime Integration

**Objective:** Implement and validate adapters in controlled steward-specific
projects.

### Planned Work

- select pilot runtime separately from this architecture repository
- build read-only adapters first
- run conformance and recovery checks
- enable memory capture and MCP capabilities incrementally
- add observability, audit, deletion, and rollback
- document steward-specific deviations

### Exit Criteria

- pilot steward passes conformance and recovery tests
- permissions remain least-privilege
- private data remains isolated
- disabling the integration restores the prior steward state

## Phase 8E - Ecosystem Adoption

**Objective:** Make Shared Foundations a stable, versioned contract available
to current and future OpenClaw stewards.

### Planned Work

- publish compatibility levels
- define steward onboarding and certification guidance
- establish change governance
- maintain migration and deprecation policy
- support multiple runtimes and storage backends
- create ecosystem-wide recovery and incident standards

### Exit Criteria

- multiple independent stewards can inherit the same foundation contracts
- no steward is forced into a shared identity or private memory store
- foundation evolution is versioned and reviewable
- ecosystem adoption does not weaken governance or recovery guarantees

## Explicitly Deferred From Phase 8A

- runtime code
- automation and lifecycle hooks
- database or vector-store selection
- live MCP servers
- steward migrations
- integration into Keeper, Xavier, Zayne, Savior, Nier, HeyDay, or any future
  steward
- copying or importing personal memory
