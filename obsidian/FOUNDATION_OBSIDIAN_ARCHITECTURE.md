# Foundation Obsidian Architecture

## Purpose

The Obsidian foundation defines a durable, human-inspectable knowledge layer
for steward context. It treats plain Markdown, metadata, links, indexes, and raw
sources as a portable projection of knowledge rather than as the runtime
memory engine itself.

## Core Concepts

### Vault-first durability

Durable knowledge belongs in versionable vault content. Tool-specific
auto-memory files should act as indexes or adapters, not the sole source of
truth.

### Folders by purpose, links by meaning

A note has one primary home but may connect to many people, projects,
decisions, sources, and memory records through explicit links.

### Raw and derived separation

Original sources remain immutable. Derived notes, summaries, indexes, and
synthesis can be rebuilt from raw material.

### AI-readable notes

Notes should be self-contained, have consistent metadata, state provenance and
recency, and provide enough summary for a future steward to judge relevance
without loading the entire file.

### Lifecycle-aware knowledge

Session start, writes, compaction, and session end are opportunities to load,
validate, preserve, and index knowledge. Hooks are an architectural concept;
their implementation is outside Phase 8A.

### Truth maintenance

Search before creation, preserve temporal changes, reconcile contradictions,
and identify stale or orphaned content.

## Required Components

- **Vault manifest:** schema version, infrastructure boundaries, content roots,
  and optional index identity
- **Vault operating guide:** conventions and precedence for any steward or tool
  accessing the vault
- **Index:** navigable catalog of important notes
- **Operation log:** append-only record of structural or knowledge changes
- **Raw source area:** immutable source material with provenance
- **Derived knowledge area:** maintained notes, summaries, and synthesis
- **Current-state area:** active projects, decisions, people, and open work
- **Templates:** consistent metadata and note structure
- **Frontmatter contract:** type, dates, description, tags, source, confidence,
  and steward scope where relevant
- **Linking contract:** explicit links for related entities and source context
- **Health contract:** orphan, broken-link, stale-claim, and contradiction checks

## Optional Components

- semantic index such as QMD
- MCP vault adapter
- Obsidian Bases
- JSON Canvas visualizations
- scheduled reconciliation and synthesis
- ingestion adapters for documents or media
- people, project, incident, decision, and performance views
- architecture-note generation
- multilingual notes and aliases

The canonical vault must remain usable as plain files when optional tooling is
unavailable.

## Inheritance Strategy

The foundation provides vault contracts and templates. Each steward may have:

- an independent vault
- an isolated namespace within a governed shared vault
- a read-only projection generated from another durable store

Steward packages define their own content taxonomy while retaining foundation
requirements for provenance, indexes, raw-source immutability, and health.

Foundation infrastructure files must be distinguishable from steward-authored
content so upgrades do not overwrite private notes.

## Future Steward Integration

A steward integration should:

1. inventory the existing vault without rewriting it
2. identify raw sources and derived notes
3. establish a manifest and operating guide
4. map current conventions to canonical metadata
5. create indexes before adding semantic retrieval
6. validate links, provenance, and private boundaries
7. introduce lifecycle adapters only after read/write rules are accepted

Obsidian remains a knowledge surface, not a mandatory runtime dependency.

## Known Risks

- competing vault schemas from multiple frameworks
- automatic rewriting damaging user-authored nuance
- duplicate notes caused by incomplete search
- raw sources being modified as if they were summaries
- frontmatter drift
- semantic indexes becoming stale
- links exposing private cross-steward information
- append-only growth without synthesis
- generated notes asserting fabricated absence or certainty
- infrastructure upgrades overwriting content

## Future Expansion Areas

- canonical vault manifest schema
- steward-specific template packs
- read-only generated projections
- vault health scoring
- temporal fact and contradiction views
- portable semantic-index adapters
- controlled cross-vault references
- migration contracts between vault versions
