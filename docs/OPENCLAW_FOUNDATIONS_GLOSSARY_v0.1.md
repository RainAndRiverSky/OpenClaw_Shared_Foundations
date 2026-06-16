# OpenClaw Foundations Glossary v0.1

## Purpose

This glossary defines the canonical terminology for OpenClaw Shared
Foundations. Future architecture documents, steward packages, integrations,
validation materials, and public documentation should use these definitions
unless a later version explicitly supersedes them.

Terminology consistency matters because identity, memory, governance, tools,
and recovery overlap without being interchangeable. Stable language prevents
permission ambiguity, accidental data sharing, incompatible inheritance, and
recovery procedures that restore the wrong system or state.

## Canonical Terms

### OpenClaw Shared Foundations

- **Definition:** The versioned, implementation-neutral architecture contracts
  shared by OpenClaw stewards for identity, memory, governance, Obsidian
  knowledge, MCP capabilities, and recovery.
- **Why it matters:** It prevents each steward from rebuilding the same
  structural concepts while preserving independent identity, memory, and
  permissions.
- **Related domains:** All domains.
- **Notes or cautions:** It is not a steward, runtime, shared personality,
  memory database, or integration layer.

### Steward

- **Definition:** An independently identified OpenClaw agent system with its
  own mission, identity, namespace, memory boundaries, permissions, and
  recovery profile.
- **Why it matters:** Steward independence is the primary boundary preventing
  identity homogenization and cross-agent contamination.
- **Related domains:** Identity, memory, governance, MCP, recovery.
- **Notes or cautions:** A steward is not merely a model, prompt, process, bot
  account, or repository. Those may be parts of a steward implementation.

### Steward Repository

- **Definition:** A repository owned by or dedicated to one steward that may
  contain its steward-specific architecture, configuration, documentation, or
  implementation.
- **Why it matters:** Repository boundaries help distinguish shared foundation
  contracts from steward-owned work and private state.
- **Related domains:** Governance, identity, inheritance, recovery.
- **Notes or cautions:** A steward repository must not be assumed to contain
  all live steward state. Private memory and credentials may live elsewhere.

### Foundation Layer

- **Definition:** A shared architecture domain or contract that defines minimum
  structures, rules, and boundaries without supplying steward-specific content.
- **Why it matters:** It establishes stable requirements that multiple stewards
  can adopt across different runtimes and storage systems.
- **Related domains:** All domains.
- **Notes or cautions:** A foundation layer describes what must be represented
  or protected, not necessarily how it is implemented.

### Inheritance Layer

- **Definition:** The boundary where a steward adopts foundation contracts,
  defaults, schemas, or validation requirements and adds steward-owned content
  and stricter policies.
- **Why it matters:** It separates shared requirements from steward-specific
  extensions and protects steward content during foundation upgrades.
- **Related domains:** Identity, governance, memory, MCP, recovery.
- **Notes or cautions:** Inheritance is contract-based, not content copying.

### Standalone Mode

- **Definition:** An operating profile in which one steward uses foundation
  contracts independently without relying on shared OpenClaw ecosystem
  services or cross-steward coordination.
- **Why it matters:** It ensures a steward can remain durable and governable
  without a central ecosystem dependency.
- **Related domains:** Inheritance, governance, memory, MCP, recovery.
- **Notes or cautions:** Standalone does not mean ungoverned, stateless, or
  disconnected from all external tools.

### OpenClaw Ecosystem Mode

- **Definition:** An operating profile in which multiple independent stewards
  participate in governed OpenClaw services, protocols, or shared knowledge
  while retaining separate identities, namespaces, permissions, and private
  memory.
- **Why it matters:** It enables interoperability without making the ecosystem
  a single agent or shared private-memory pool.
- **Related domains:** Governance, inheritance, MCP, memory, recovery.
- **Notes or cautions:** Ecosystem membership never grants automatic access to
  another steward's repository, tools, identity, or memory.

### Harbor Mode

- **Definition:** A protected OpenClaw ecosystem operating profile in which a
  steward connects to approved shared services through a governed boundary
  with explicit admission, namespace isolation, capability allowlists, audit,
  and recovery controls.
- **Why it matters:** It provides a safer coordination posture between fully
  standalone operation and broader ecosystem participation.
- **Related domains:** Governance, MCP, inheritance, memory, recovery.
- **Notes or cautions:** Harbor mode is an architecture profile, not a runtime,
  steward, universal control plane, or permission to pool private memory.

### Identity Spine

- **Definition:** The compact, canonical set of identity records defining a
  steward's name, mission, role, values, voice, boundaries, and stable
  commitments.
- **Why it matters:** It provides the minimum source material needed to keep a
  steward recognizable and recoverable.
- **Related domains:** Identity, governance, recovery.
- **Notes or cautions:** It should remain small and stable. Current tasks and
  long histories do not belong in the identity spine.

### Current State

- **Definition:** A time-sensitive record of a steward's active priorities,
  open commitments, recent changes, operating condition, and continuity
  warnings.
- **Why it matters:** It lets a steward resume present work without treating
  transient context as permanent identity.
- **Related domains:** Identity, memory, recovery.
- **Notes or cautions:** Current state requires timestamps, refresh rules, and
  stale-state handling.

### Critical Facts

- **Definition:** The minimal set of current, high-relevance facts needed in
  nearly every steward interaction.
- **Why it matters:** It provides essential orientation at low context cost.
- **Related domains:** Identity, memory, context management.
- **Notes or cautions:** Critical facts are not a general memory archive and
  should remain bounded, current, and attributable.

### Memory Record

- **Definition:** A durable unit of remembered information with content, type,
  stable identifier, source, timestamps, steward scope, confidence,
  sensitivity, and lifecycle metadata.
- **Why it matters:** A canonical record contract enables storage-neutral
  retrieval, deletion, export, and migration.
- **Related domains:** Memory, governance, recovery.
- **Notes or cautions:** Raw, extracted, inferred, curated, and summarized
  records must be distinguishable.

### Provenance

- **Definition:** Evidence describing where information came from, who or what
  created it, when it was observed and learned, and how it was transformed.
- **Why it matters:** Provenance supports trust, correction, temporal truth,
  auditability, and recovery.
- **Related domains:** Memory, governance, Obsidian, recovery.
- **Notes or cautions:** Provenance does not prove that a source is correct; it
  proves the origin and transformation history are known.

### Retrieval

- **Definition:** The governed process of locating and returning relevant
  memory or knowledge for a specific need.
- **Why it matters:** Durable storage has limited value if a steward cannot
  recover the correct information at the correct time.
- **Related domains:** Memory, Obsidian, MCP, context management.
- **Notes or cautions:** Retrieval must be scoped, ranked, attributable, and
  bounded before context injection.

### Semantic Retrieval

- **Definition:** Retrieval based on similarity of meaning, usually through
  embeddings or another semantic representation.
- **Why it matters:** It can find relevant material when the query and source
  use different words.
- **Related domains:** Memory, Obsidian.
- **Notes or cautions:** Semantic similarity is not factual verification and
  may return plausible but irrelevant records.

### Exact Retrieval

- **Definition:** Retrieval based on literal tokens, identifiers, keywords, or
  full-text matches.
- **Why it matters:** It protects precision for names, dates, paths, IDs,
  quotations, and explicit decisions.
- **Related domains:** Memory, Obsidian.
- **Notes or cautions:** Exact retrieval may miss conceptually related content
  expressed with different language.

### Temporal Retrieval

- **Definition:** Retrieval that considers when a fact or relationship was
  true, when it was learned, and whether it remains current.
- **Why it matters:** It prevents obsolete facts from being presented as the
  current state and supports historical questions.
- **Related domains:** Memory, governance, recovery.
- **Notes or cautions:** Event time and learned time should remain distinct.

### Knowledge Graph

- **Definition:** A structured representation of entities, relationships, and
  optionally their provenance and validity periods.
- **Why it matters:** It supports relationship-heavy recall and navigation that
  flat text search cannot express efficiently.
- **Related domains:** Memory, Obsidian.
- **Notes or cautions:** Graph edges are records or claims, not automatically
  verified truth.

### Context Engine

- **Definition:** The architecture component that selects, orders, limits, and
  assembles identity, current state, memory, tool, and session information for
  a steward interaction.
- **Why it matters:** It controls context quality and cost without dumping the
  full archive into every prompt.
- **Related domains:** Identity, memory, governance, recovery.
- **Notes or cautions:** A context engine is not a memory store. It consumes
  source material under precedence and token-budget rules.

### Consolidation

- **Definition:** A governed process that reviews existing records to extract,
  connect, summarize, deduplicate, or promote durable knowledge.
- **Why it matters:** It reduces fragmentation and helps useful patterns emerge
  over time.
- **Related domains:** Memory, Obsidian.
- **Notes or cautions:** Consolidation must preserve provenance and must not
  silently replace verbatim sources.

### Retention

- **Definition:** The policy governing how long data remains active, archived,
  recoverable, or eligible for deletion.
- **Why it matters:** It limits unbounded growth, privacy exposure, and stale
  context.
- **Related domains:** Memory, governance, recovery, audit.
- **Notes or cautions:** Retention is not deletion; archived or backed-up data
  may still exist.

### Recovery Anchor

- **Definition:** An approved source of truth used in a defined order to
  restore governance, identity, current state, memory integrity, or operating
  capability.
- **Why it matters:** It makes recovery evidence-based instead of dependent on
  style, guesswork, or whichever record is easiest to access.
- **Related domains:** Recovery, identity, governance, memory.
- **Notes or cautions:** Recovery anchors require ownership, version, integrity,
  and precedence information.

### Identity Reload

- **Definition:** The recovery action that reintroduces and validates a
  steward's canonical identity spine and applicable governance boundaries.
- **Why it matters:** It restores recognizability and behavioral integrity
  after drift, compaction, or a new session.
- **Related domains:** Identity, recovery.
- **Notes or cautions:** Reload is not identity replacement and must not import
  another steward's identity.

### Context Compaction

- **Definition:** The controlled reduction of active conversation context by
  summarizing, moving, or dropping older material while preserving required
  continuity.
- **Why it matters:** It allows long-running sessions to continue within
  context limits.
- **Related domains:** Memory, recovery, identity.
- **Notes or cautions:** Compaction must preserve critical identifiers,
  decisions, unresolved work, provenance, and recovery cues.

### Drift

- **Definition:** A meaningful divergence between current steward behavior or
  state and its validated identity, governance, memory, or operating contract.
- **Why it matters:** Unchecked drift can make a steward inconsistent,
  untrustworthy, or unsafe.
- **Related domains:** Identity, governance, recovery, memory.
- **Notes or cautions:** Change is not automatically drift. Drift is assessed
  against approved sources and intended evolution.

### Corruption

- **Definition:** Damage or inconsistency that makes stored data, metadata,
  indexes, relationships, or configuration unreliable or unreadable.
- **Why it matters:** Corruption can silently degrade retrieval, recovery, and
  identity continuity.
- **Related domains:** Memory, Obsidian, recovery.
- **Notes or cautions:** A broken derived index does not necessarily mean the
  source records are corrupted.

### Rollback

- **Definition:** The controlled restoration of a previously verified
  architecture, configuration, schema, or data state after a failed change.
- **Why it matters:** It limits damage from migration, integration, or recovery
  failure.
- **Related domains:** Recovery, governance, memory, inheritance.
- **Notes or cautions:** Rollback requires a verified prior state and must
  account for changes made after the rollback point.

### Capability Policy

- **Definition:** The rules describing which capability classes are allowed,
  denied, gated, or conditionally available to a steward.
- **Why it matters:** It separates technical availability from granted
  authority.
- **Related domains:** Governance, MCP, inheritance.
- **Notes or cautions:** A capability policy should identify owner, scope,
  risk, default state, approval requirements, and revocation behavior.

### Capability Gate

- **Definition:** A control that enforces a capability policy before a tool or
  operation can be used.
- **Why it matters:** It prevents high-risk actions from becoming available
  merely because code, credentials, or a server exists.
- **Related domains:** Governance, MCP, recovery.
- **Notes or cautions:** Documentation alone is not an enforcement gate.

### MCP

- **Definition:** Model Context Protocol, a typed protocol for exposing tools,
  resources, and contextual capabilities to compatible agent systems.
- **Why it matters:** MCP provides a common boundary between stewards and
  external systems while allowing capability-specific governance.
- **Related domains:** MCP, governance, memory, Obsidian.
- **Notes or cautions:** MCP compatibility does not establish trust,
  authorization, data safety, or steward scope by itself.

### MCP Read Tool

- **Definition:** An MCP tool whose approved purpose is to retrieve, inspect, or
  list information without intentionally changing the target system.
- **Why it matters:** Read tools are the preferred first integration surface
  for discovery and compatibility validation.
- **Related domains:** MCP, governance, memory, Obsidian.
- **Notes or cautions:** Reads can still expose sensitive data, incur costs, or
  trigger side effects in poorly designed systems.

### MCP Write Tool

- **Definition:** An MCP tool that creates, updates, deletes, executes, sends,
  or otherwise changes state in a target system.
- **Why it matters:** Write tools require stronger validation, authorization,
  audit, idempotency, and rollback controls.
- **Related domains:** MCP, governance, recovery.
- **Notes or cautions:** Destructive tools are a high-risk subset of write
  tools and should not be treated as ordinary updates.

### Obsidian Projection

- **Definition:** A human-inspectable vault representation of steward
  knowledge, memory references, decisions, or state using Markdown, metadata,
  links, and indexes.
- **Why it matters:** It provides durable and portable visibility without
  requiring Obsidian to be the runtime memory engine.
- **Related domains:** Obsidian, memory, recovery.
- **Notes or cautions:** A projection may be derived from another source of
  truth and must declare whether it is authoritative, editable, or read-only.

### Vault Schema

- **Definition:** The documented structure and metadata contract for an
  Obsidian projection, including content roots, note types, frontmatter,
  indexes, raw-source rules, and infrastructure boundaries.
- **Why it matters:** It keeps vault content consistent, portable, and safe to
  upgrade.
- **Related domains:** Obsidian, inheritance, governance.
- **Notes or cautions:** Folder names alone do not constitute a vault schema.

### Namespace

- **Definition:** A stable logical boundary that scopes identifiers, memory,
  tools, configuration, and state to a steward, tenant, or approved shared
  domain.
- **Why it matters:** Namespaces prevent collisions and unintended data access
  across stewards.
- **Related domains:** Identity, memory, MCP, governance, recovery.
- **Notes or cautions:** A name prefix is not sufficient isolation unless every
  relevant read and write path enforces it.

### Agent Isolation

- **Definition:** The property that one steward's identity, memory,
  credentials, permissions, failures, and recovery actions cannot silently
  affect another steward.
- **Why it matters:** It is the operational expression of steward
  independence.
- **Related domains:** Governance, memory, MCP, recovery.
- **Notes or cautions:** Shared services require explicit tenant and namespace
  enforcement to preserve isolation.

### Public Governance

- **Definition:** The policies and repository materials needed to manage a
  public or open-source foundation, including licensing, contribution rules,
  security reporting, change governance, release policy, and community
  conduct.
- **Why it matters:** Architecture quality alone does not establish safe or
  sustainable public stewardship.
- **Related domains:** Governance, ecosystem adoption.
- **Notes or cautions:** Public governance must not disclose private steward
  operations or weaken security boundaries for transparency.

### Private Memory

- **Definition:** Memory restricted to an authorized user, steward, or defined
  private scope and not eligible for general ecosystem sharing.
- **Why it matters:** It protects sensitive history, relationships, identity
  anchors, and operational information.
- **Related domains:** Memory, governance, recovery.
- **Notes or cautions:** Private memory remains private when backed up,
  embedded, summarized, or projected into another format.

### Steward-Specific Memory

- **Definition:** Memory owned by and scoped to one steward's work, identity,
  decisions, observations, or user relationship.
- **Why it matters:** It preserves continuity without merging independent
  steward histories.
- **Related domains:** Memory, identity, governance.
- **Notes or cautions:** Steward-specific does not always mean user-private,
  but it is never shared automatically.

### Shared Foundation Memory

- **Definition:** Non-private, governed knowledge about foundation contracts,
  terminology, validated patterns, compatibility decisions, and ecosystem
  standards that approved stewards may use.
- **Why it matters:** It lets stewards benefit from common architectural
  learning without sharing private histories.
- **Related domains:** Memory, governance, inheritance.
- **Notes or cautions:** It must not become a disguised pool of
  steward-specific or user-private memory. Inclusion requires provenance,
  publication authority, and revocation rules.

### Source of Truth

- **Definition:** The approved authoritative source for a particular kind of
  information within a defined scope.
- **Why it matters:** It gives conflict resolution, recovery, and updates a
  stable reference.
- **Related domains:** All domains.
- **Notes or cautions:** There may be different sources of truth for identity,
  current state, raw records, permissions, and derived indexes. The term must
  always name its scope.

### Precedence Model

- **Definition:** The ordered rules used to resolve conflicts among safety
  policy, user authority, foundation governance, steward identity, current
  state, memory, tool results, and transient context.
- **Why it matters:** It prevents whichever source was loaded last from
  silently overriding more authoritative information.
- **Related domains:** Governance, identity, memory, recovery.
- **Notes or cautions:** Precedence does not make a higher source infallible;
  provenance, scope, and explicit exceptions still matter.

### Threat Model

- **Definition:** A structured account of protected assets, trusted and
  untrusted boundaries, possible adversaries, failure modes, attack paths, and
  required mitigations.
- **Why it matters:** It turns distributed safety concerns into testable
  security and privacy assumptions.
- **Related domains:** Governance, memory, MCP, Obsidian, recovery.
- **Notes or cautions:** A risk list is not a complete threat model. The model
  must identify actors, assets, boundaries, and consequences.

## Naming Conventions

1. Use **OpenClaw Shared Foundations** for the complete architecture program.
2. Use **foundation layer** for one shared architecture domain or contract.
3. Use **steward** for an independent OpenClaw agent system.
4. Use **steward repository** only for a repository dedicated to one steward.
5. Capitalize product and protocol names: **OpenClaw**, **Obsidian**, and
   **MCP**.
6. Use lowercase for general architecture terms such as identity spine,
   namespace, provenance, and recovery anchor.
7. Use **steward-specific** with a hyphen when it modifies a noun.
8. Use **cross-steward** with a hyphen for governed interactions spanning
   multiple stewards.
9. Use **read-only** for an intentionally non-mutating access profile.
10. Version normative documents with an explicit suffix such as `v0.1`.
11. Name modes as operating profiles: **standalone mode**, **OpenClaw ecosystem
    mode**, and **Harbor mode**.
12. When using **source of truth**, always state the scope, such as identity
    source of truth or permission source of truth.

## Terms to Avoid

- **Shared brain:** Implies merged identity or private memory. Use shared
  foundation memory or shared knowledge when that is what is meant.
- **Master agent:** Implies undefined authority over independent stewards. Use
  coordinator, operator, or explicitly named governance role.
- **Clone:** Implies copied identity or memory. Use steward instance, profile,
  or inheritance package.
- **Global memory:** Too broad and unsafe. State the namespace and sharing
  policy.
- **Universal identity:** Conflicts with steward independence.
- **Open access:** Ambiguous. Name the actual public, shared, private, or
  restricted data class.
- **Safe by default:** Avoid unless the exact defaults and threat assumptions
  are documented.
- **Permanent memory:** Retention, deletion, and recovery policies may change.
  Use durable memory when appropriate.
- **Automatic consent:** Consent and authority cannot be inferred from system
  availability.
- **Unredacted audit:** Audit records should minimize and protect sensitive
  content.
- **Single source of truth:** Avoid without scope; different domains may have
  different authoritative sources.

## Terms That Must Not Be Used Interchangeably

| Term A | Term B | Required distinction |
|---|---|---|
| OpenClaw Shared Foundations | steward | Shared contracts versus an independent agent system |
| foundation layer | inheritance layer | Shared requirements versus the adoption and extension boundary |
| steward | steward repository | Operating identity and state versus a code/document container |
| standalone mode | Harbor mode | Independent operation versus governed shared-service participation |
| Harbor mode | OpenClaw ecosystem mode | Protected ecosystem profile versus the broader ecosystem profile |
| identity spine | current state | Stable identity versus time-sensitive operating context |
| current state | critical facts | Broad active condition versus minimal always-relevant facts |
| memory record | context | Durable stored unit versus material assembled for one interaction |
| private memory | steward-specific memory | Access classification versus ownership and scope |
| steward-specific memory | shared foundation memory | One steward's continuity versus publishable common architecture knowledge |
| provenance | confidence | Origin and transformation evidence versus assessed reliability |
| semantic retrieval | exact retrieval | Meaning similarity versus literal matching |
| temporal retrieval | retention | Time-aware recall versus data lifecycle duration |
| knowledge graph | source of truth | Relationship representation versus scoped authority |
| context engine | memory store | Context assembly versus durable storage |
| consolidation | compaction | Durable knowledge refinement versus active context reduction |
| recovery anchor | backup | Approved restoration authority versus a copy of data |
| identity reload | rollback | Re-establishing identity context versus restoring a prior system state |
| drift | corruption | Behavioral or contract divergence versus damaged or inconsistent data |
| capability policy | capability gate | Rule describing access versus control enforcing the rule |
| MCP | MCP server | Protocol versus one service implementing the protocol |
| MCP read tool | MCP write tool | Retrieval intent versus state-changing intent |
| Obsidian projection | source of truth | A knowledge representation versus authority, unless explicitly designated |
| namespace | agent isolation | Logical scope versus the enforced property preventing cross-agent effects |
| public governance | foundation governance | Public project stewardship versus architecture rules applied to stewards |
| precedence model | threat model | Conflict resolution order versus security and privacy analysis |

## Terminology Consistency Summary

Consistent terminology makes the Shared Foundations reviewable and portable.
It keeps shared contracts separate from steward-owned identity, distinguishes
stored memory from active context, separates policy from enforcement, and makes
deployment modes explicit. These distinctions are required before conformance,
precedence, threat modeling, steward packaging, or runtime integration can be
validated safely.
