# Foundation Memory Architecture

## Purpose

The memory foundation defines how stewards capture, store, retrieve, update,
isolate, retain, and recover durable knowledge without placing entire histories
into every context window. It prioritizes relevance, provenance, local control,
and graceful degradation.

## Core Concepts

### Layered memory

Memory is divided by access cost and relevance:

- **L0 identity:** minimal always-loaded identity
- **L1 essential continuity:** current state, critical facts, and key anchors
- **L2 contextual recall:** topic-filtered retrieval
- **L3 deep archive:** explicit semantic, exact, graph, or timeline search

### Multiple memory forms

No single store solves every retrieval need. The architecture distinguishes:

- session history
- curated durable facts
- episodic records and summaries
- verbatim source records
- semantic vectors
- exact-text indexes
- temporal entity relationships
- active threads and unresolved commitments

### Provenance before confidence

Every durable record should identify where it came from, when it was learned,
which steward owns it, and whether it is raw, extracted, inferred, or curated.

### Hybrid retrieval

Exact search protects names, dates, identifiers, and quoted decisions.
Semantic search finds meaning. Graph and temporal retrieval reconstruct
relationships and change. Results should be ranked and deduplicated before
context injection.

### Capture before context loss

Lifecycle capture should protect meaningful information before compaction or
session termination. Capture must be bounded, reviewable, and idempotent.

### Storage neutrality

The foundation defines contracts, not a required database. Local files, SQLite,
vector stores, knowledge graphs, or external services may implement the same
interfaces.

## Required Components

- **Memory record model:** content, type, source, timestamps, steward, scope,
  confidence, sensitivity, and stable identifier
- **Namespace isolation:** separate private stores or mandatory steward filters
- **Session continuity store:** recent thread history with bounded retention
- **Durable fact store:** curated or extracted facts with source links
- **Exact retrieval:** keyword or full-text search
- **Context assembler:** injects only relevant, bounded memory
- **Deduplication:** deterministic identity and similarity checking
- **Temporal behavior:** preserve superseded facts rather than silently
  overwriting history
- **Deletion and reset contracts:** record, scope, steward, and complete reset
- **Retention policy:** caps, archival rules, and stale-data treatment
- **Export and backup contract:** portable, inspectable recovery material
- **Graceful degradation:** memory failure must not crash the primary steward
  path or trigger fabricated recall

## Optional Components

- vector retrieval and reranking
- temporal knowledge graph
- associative or novelty-based surfacing
- emotional or relational observations
- offline consolidation or sleep-time processing
- cross-steward shared knowledge
- multimodal memory
- memory importance and decay scoring
- contradiction detection
- agent diaries or first-person journals
- pluggable storage backends

Cross-steward memory and emotional memory require additional governance and
must remain opt-in.

## Inheritance Strategy

All stewards inherit the record contract, retrieval behavior, provenance
requirements, and deletion expectations. They do not inherit shared private
content.

Each steward selects:

- enabled memory types
- storage backend
- retention duration
- retrieval thresholds
- optional graph or vector features
- allowed shared-memory scopes

The foundation should expose stable conceptual operations such as store,
search, retrieve by ID, invalidate, timeline, export, and delete. Runtime names
and storage technology may vary.

## Future Steward Integration

Future integration should begin in read-only mode:

1. map existing steward data to the canonical record model
2. verify namespace separation
3. test exact retrieval before semantic retrieval
4. validate provenance and temporal handling
5. add bounded context assembly
6. enable capture hooks only after duplication and retention tests
7. enable graph, consolidation, or shared memory separately

No steward should be required to migrate its full archive to adopt the
foundation.

## Known Risks

- retrieval returning plausible but irrelevant records
- summary drift away from verbatim source material
- duplicate capture during repeated hooks
- cross-steward contamination
- stale facts presented as current
- sensitive content entering vectors or external backends
- unbounded memory growth
- compaction destroying identifiers, decisions, or open tasks
- graph relationships being treated as verified facts
- backend corruption or index/schema mismatch

## Future Expansion Areas

- memory conformance fixtures and retrieval benchmarks
- sensitivity-aware retrieval
- configurable promotion and demotion between layers
- confidence-aware context assembly
- shared-knowledge publication workflows
- multimodal provenance contracts
- contradiction review queues
- storage backend capability negotiation
- portable steward memory manifests
