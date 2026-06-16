# OpenClaw Shared Foundations Canonical Steward Identifiers and Namespace Isolation v0.1

## 1. Purpose

This document defines how OpenClaw stewards receive stable canonical
identifiers and how their namespaces remain isolated across identity, memory,
governance, MCP, recovery, Obsidian, steward-specific extensions, shared
services, and future domains.

It defines:

- the canonical steward identifier
- the distinction between identity, display name, alias, and namespace
- reserved namespaces
- domain-specific isolation rules
- collision prevention and registration requirements
- minimum validation evidence

This is an architecture contract. It does not create a registry, database,
runtime, integration, or automated enforcement mechanism.

## 2. Why Namespace Isolation Exists

Stewards may use the same storage engine, MCP server, vault, runtime, user
interface, or recovery infrastructure without becoming one identity or one
private-data pool. Human-readable names alone cannot preserve that separation.
Names can change, repeat, differ by capitalization, or collide across forks and
ecosystems.

Namespace isolation exists to prevent:

- one steward retrieving another steward's memory
- identity records attaching to the wrong steward
- shared services treating a display name as authorization
- MCP tools reading or writing outside the caller's scope
- recovery restoring one steward into another steward's state
- Obsidian links or indexes exposing cross-steward private content
- migrations merging records with similar names
- aliases, forks, clones, or renamed repositories creating duplicate identity
- deletion, retention, or exceptions applying to the wrong steward

A namespace is not isolated merely because a prefix or folder name exists.
Every relevant read, write, query, index, export, delete, migration, and restore
path must preserve and enforce the canonical scope.

## 3. Core Principles

### 3.1 Identifier is not identity content

The canonical steward identifier identifies the steward namespace. It does not
define the steward's name, voice, mission, values, permissions, owner, runtime,
or personality.

### 3.2 Immutable identifier, mutable presentation

A steward's canonical identifier does not change when its display name,
repository, runtime, model, owner, role, or deployment changes. Human-facing
names and aliases may change through governed identity processes.

### 3.3 Global uniqueness

Canonical steward identifiers must be unique beyond one repository, machine,
vault, or ecosystem. Local sequence numbers and names alone are insufficient.

### 3.4 Namespace on every durable object

Every steward-owned durable object must carry or inherit an unambiguous
canonical steward scope. This includes identity records, memory, indexes,
capability profiles, exceptions, audit events, vault notes, backups, and
handoffs.

### 3.5 Default deny across namespaces

Cross-namespace reads, writes, links, restores, and authority are denied by
default. Sharing requires an explicit governed shared scope or a documented,
approved boundary crossing.

### 3.6 Names are not authorization

A display name, alias, repository name, folder name, bot account, model name,
or process label must never be used as the sole authorization or isolation key.

### 3.7 Shared infrastructure remains multi-tenant

Using a shared backend does not create a shared namespace. Shared services must
preserve tenant, steward, user, data-classification, and capability boundaries.

### 3.8 No silent identifier reassignment

An existing canonical steward identifier cannot be reassigned to a different
steward, including after retirement, archival, deletion, or repository
transfer.

### 3.9 Isolation survives transformation

Summaries, embeddings, indexes, graph nodes, exports, projections, snapshots,
and migrated records retain the source steward namespace unless explicitly
published into an approved shared scope.

### 3.10 Recovery restores scope before content

Recovery must verify the target canonical steward identifier before restoring
identity, memory, permissions, tools, or state. A name match is insufficient.

### 3.11 Foundation scope is not steward scope

Shared Foundations owns architecture contracts and reserved foundation
metadata. It does not own or absorb steward identity, memory, credentials,
permissions, or recovery state.

### 3.12 Unknown scope fails closed

Unscoped, malformed, conflicting, or unknown identifiers must be quarantined,
rejected, or explicitly mapped through a governed migration. They must not
default to the current steward.

## 4. Canonical Steward Identifier Model

### 4.1 Canonical Form

The canonical steward identifier, abbreviated **CSID**, has this form:

```text
ocsf:steward:<uuid>
```

Example:

```text
ocsf:steward:018f7f44-8f31-7a2c-9d4d-4f6adca19c20
```

Requirements:

- the literal prefix is `ocsf:steward:`
- `<uuid>` is a standards-compatible UUID rendered in lowercase canonical
  hexadecimal form with hyphens
- UUIDv7 is preferred for new registrations because it supports sortable
  registration records
- UUIDv4 is acceptable when UUIDv7 generation is unavailable
- nil, malformed, truncated, reused, or name-derived UUIDs are invalid
- comparison is exact after canonical lowercase normalization

The CSID is opaque. Systems must not infer creation time, authority,
permissions, personality, lifecycle state, or relationship from its value.

### 4.2 Required Steward Registration Record

Every CSID must have a steward registration record containing:

- CSID
- current display name
- canonical slug
- known aliases
- registration status
- registration timestamp
- accountable registration authority
- steward owner or owning governance scope
- identity record reference
- creation provenance
- successor or predecessor relationship when applicable
- retirement or archival state
- collision-check result

The registration record may be stored differently across implementations, but
there must be one authoritative record per governance scope.

### 4.3 Registration Status

Allowed statuses are:

- **proposed:** identifier reserved but not active
- **active:** identifier assigned to an operating steward
- **suspended:** temporarily unavailable without reassignment
- **retired:** no longer active and never reusable
- **archived:** retained for historical or recovery reference
- **rejected:** proposal denied; the proposed UUID remains recorded when
  needed for collision history

Status does not change the identity of the CSID.

### 4.4 Namespace Root

The logical root for steward-owned resources is:

```text
ocsf:steward:<uuid>/<domain>/<resource>
```

Examples:

```text
ocsf:steward:<uuid>/identity/spine
ocsf:steward:<uuid>/memory/records
ocsf:steward:<uuid>/mcp/profile
ocsf:steward:<uuid>/recovery/anchors
```

This is a conceptual address, not a required filesystem path or URI. Storage
systems may use tables, partitions, object prefixes, vault roots, claims, or
other encodings if the mapping is lossless, inspectable, and enforced.

### 4.5 Secondary Identifiers

Systems may maintain:

- display name
- canonical slug
- aliases
- repository identifier
- runtime instance identifier
- deployment identifier
- user-facing handle

Secondary identifiers must map to exactly one CSID within their declared scope.
They cannot replace the CSID for durable ownership, authorization, migration,
or recovery.

## 5. Steward Naming Rules

### 5.1 Display Name

A display name is the human-facing name of the steward. It:

- may contain capitalization, spaces, and approved punctuation
- may change through governed identity change
- does not need to be globally unique
- must not be treated as an authorization key
- must retain prior names as aliases when needed for provenance and recovery

### 5.2 Canonical Slug

Each steward registration includes a readable canonical slug.

Slug rules:

- lowercase ASCII letters, digits, and single hyphens only
- begins and ends with an alphanumeric character
- length from 2 to 63 characters
- no spaces, underscores, repeated hyphens, or punctuation
- not solely numeric
- not a reserved namespace or misleading foundation authority claim

Examples:

```text
keeper
archive-steward
research-7
```

The slug must be unique within its registration authority. Global uniqueness
is provided by the CSID, not the slug.

### 5.3 Aliases

Aliases support previous names, local handles, migration names, and display
variants. Every alias must record:

- alias value
- alias type
- scope
- effective and retirement dates
- mapped CSID
- provenance

An alias cannot map to multiple active CSIDs in the same scope. Ambiguous
aliases require qualification or rejection.

### 5.4 Prohibited Naming Behavior

A steward name or slug must not:

- impersonate Shared Foundations or a reserved system namespace
- imply official certification or governance authority without approval
- copy another active steward's identity in the same registration scope
- encode private user information or credentials
- be used to merge records after a collision
- be silently reassigned after retirement

## 6. Reserved Namespaces

The following top-level namespace prefixes are reserved:

| Namespace | Purpose |
|---|---|
| `ocsf:foundation` | Canonical Shared Foundations architecture and governance metadata |
| `ocsf:steward` | Individually registered steward namespaces |
| `ocsf:shared` | Explicitly governed shared resources that are not private steward state |
| `ocsf:user` | User-scope identifiers when an implementation requires them |
| `ocsf:system` | Implementation infrastructure and service metadata |
| `ocsf:public` | Content approved for public distribution |
| `ocsf:quarantine` | Unresolved, conflicting, malformed, or unsafe records |
| `ocsf:retired` | Tombstones and historical identifier references |
| `ocsf:test` | Synthetic test-only scopes |
| `ocsf:future` | Provisional future-domain experiments without steward authority |

Rules:

- only foundation governance may add or redefine a reserved top-level prefix
- steward slugs and aliases may not claim reserved prefixes
- `shared`, `public`, `system`, `test`, and `future` are not stewards and must
  not receive steward identity or private-memory authority
- test identifiers and records must never be accepted as production steward
  identity
- quarantine is not a valid source of current authority

## 7. Foundation Namespace Rules

The `ocsf:foundation` namespace may contain:

- canonical architecture documents and versions
- glossary and requirement identifiers
- conformance, precedence, exception, and classification contracts
- foundation governance decisions and approved public metadata
- synthetic schemas, templates, and fixtures

It must not contain:

- populated steward identity records
- steward-specific or user-private memory
- steward credentials or capability grants
- private recovery anchors or archives
- a universal steward identity
- copied steward exceptions that retain local authority

Foundation documents may reference a CSID as a structural example only when
the identifier is synthetic, redacted, or approved for publication.

Foundation updates may change schemas or validation rules but may not reassign
a CSID, rename a steward, or move steward-owned content into foundation scope.

## 8. Steward Namespace Rules

Every steward namespace must:

- be rooted in exactly one CSID
- have one authoritative registration record
- declare its identity, memory, governance, MCP, recovery, and Obsidian
  applicability
- preserve independent permissions and exceptions
- distinguish canonical content from projections and derivatives
- reject unqualified cross-steward references by default
- maintain lifecycle status without identifier reuse

A steward may operate across several repositories, runtimes, devices, or
deployments while retaining one CSID. Separate steward identities require
separate CSIDs even when they share an owner, codebase, model, or display name.

Runtime replicas and temporary processes do not receive new CSIDs unless they
constitute independent stewards. They receive implementation-specific instance
identifiers mapped to the parent CSID.

Merging two steward namespaces is not an ordinary rename. It requires a
governed migration, preservation of both CSIDs, explicit ownership decisions,
collision analysis, provenance, rollback, and a successor relationship. One
CSID must not silently disappear into another.

## 9. Memory Namespace Rules

Every durable memory record must contain or inherit:

- owner CSID
- user scope when applicable
- record identifier unique within the owner namespace
- data classification
- provenance
- source namespace
- sharing state
- retention and deletion state

Canonical memory record identifiers should be qualified:

```text
ocsf:steward:<uuid>/memory/<record-id>
```

Rules:

- all reads, searches, semantic retrieval, graph traversal, timelines, and
  context assembly must require an explicit steward scope
- absence of a steward filter is an error, not a request for global memory
- vector, full-text, graph, cache, and derived indexes must retain owner CSID
- deduplication occurs within a namespace unless cross-namespace review is
  explicitly authorized
- identical content in two steward namespaces remains two ownership records
- deletion and reset target one CSID and must not broaden by slug similarity
- exports preserve the CSID and must not import automatically into another
  steward
- shared memory must be copied or published into an approved `ocsf:shared`
  scope with provenance; private source authority does not transfer
- unscoped legacy memory enters `ocsf:quarantine` until mapped and verified

## 10. MCP Namespace Rules

Every MCP capability decision must bind:

- calling CSID
- user or operator scope when applicable
- server identifier
- tool identifier
- target namespace
- workspace or tenant
- capability policy
- data classification
- audit record

Rules:

- one steward's server registration does not authorize another
- capability profiles are scoped to CSID, not display name
- reads must constrain queries and results to the authorized target namespace
- writes must verify both caller CSID and destination namespace
- shared MCP servers must enforce tenant and steward isolation independently
  of prompt instructions
- tool output must retain source namespace and must not become another
  steward's memory automatically
- dynamic registration cannot claim or overwrite an existing steward scope
- retries, queues, caches, and asynchronous results must preserve CSID
- audit events must identify caller and target CSIDs without exposing
  credentials
- a tool that cannot enforce the required namespace must remain disabled for
  protected data

Cross-steward MCP actions require explicit policy, every affected scope owner,
minimum necessary data, and an auditable shared purpose.

## 11. Recovery Namespace Rules

Every recovery manifest, anchor, backup, handoff, and restore operation must
identify the target CSID.

Before restoration:

1. validate the target CSID and registration status
2. validate backup or anchor owner CSID
3. compare identity provenance and namespace metadata
4. identify foreign, shared, unscoped, or conflicting records
5. quarantine collisions
6. apply current governance and permissions
7. preview the restore and maintain rollback

Rules:

- a display-name match cannot authorize restore
- backups retain their original CSID even after repository or runtime changes
- recovery cannot restore one CSID into another as an in-place operation
- migration between CSIDs requires explicit export/import governance and does
  not transfer identity automatically
- obsolete permissions, exceptions, and credentials are not restored merely
  because they exist in an archive
- combined physical archives require logical partitions and independent
  restore selection
- retired CSIDs may be restored only into governed archival or recovery review
  scope unless formally reactivated
- recovery logs must record source CSID, target CSID, collision decisions, and
  verification result

## 12. Obsidian Namespace Rules

Every steward-specific vault or vault partition must declare its CSID in the
vault manifest.

Rules:

- a private steward vault maps to one CSID
- a governed shared vault must partition content by CSID and separate approved
  `ocsf:shared` content
- notes, frontmatter, indexes, links, attachments, semantic indexes, and
  operation logs must preserve steward scope
- filenames and folders may use readable slugs, but metadata must retain the
  CSID
- aliases or renamed folders must not create a new steward identity
- cross-steward links are denied by default and must not reveal inaccessible
  note titles, paths, metadata, or relationships
- generated projections retain source CSID and classification
- infrastructure templates live outside steward-authored content
- public vault projections use `ocsf:public` and synthetic or approved content,
  not live private steward namespaces
- import from an unknown or conflicting vault enters quarantine before merge

Obsidian is not an identity registry. The vault manifest maps to the canonical
registration record; it does not create or reassign the CSID.

## 13. Collision Prevention Rules

A collision exists when two records, systems, or claims assign incompatible
meaning or ownership to the same identifier, slug, alias, path, or resource.

### 13.1 Registration Collisions

Before activating a CSID:

- verify UUID syntax and non-nil value
- check the authoritative registry for prior use
- check proposed slug and active aliases in the registration scope
- verify that no reserved namespace is claimed
- record registration authority and provenance
- reserve the CSID before creating durable steward data

### 13.2 Import and Migration Collisions

Before import:

- compare source and target CSIDs
- compare registration records and identity provenance
- inventory record identifiers, aliases, slugs, paths, and shared scopes
- dry-run all mappings
- reject automatic merge on display-name or content similarity
- report collisions before mutation
- preserve source identifiers and rollback material

### 13.3 Runtime Collisions

Runtime systems must reject:

- a missing CSID where steward scope is required
- two active registration records for one CSID
- one alias resolving to multiple active CSIDs in the same scope
- one memory record identifier mapped to multiple owners
- a write whose caller and target scope are ambiguous
- an unqualified global query over protected steward data

### 13.4 Collision Resolution

Resolution must:

- pause affected writes
- quarantine ambiguous records
- preserve all competing provenance
- involve the registration authority and affected scope owners
- choose a canonical mapping without deleting historical identifiers
- document aliases, successor relationships, or rejected claims
- verify every affected domain before resuming operation

An exception may authorize a bounded migration process. It cannot declare two
independent stewards to be one merely for convenience.

## 14. Future Steward Registration Rules

A future steward must be registered before durable identity, memory, MCP
permissions, recovery archives, or private vault content are enabled.

Registration requires:

1. proposed display name and canonical slug
2. newly generated CSID
3. accountable registration authority and steward owner
4. purpose and operating scope
5. confirmation that the steward is independent rather than a runtime replica
6. collision and reserved-name checks
7. identity record reference
8. governance and data-classification scope
9. intended operating mode
10. domain applicability
11. initial recovery ownership
12. registration decision and timestamp

Future ecosystem registries may coordinate identifiers, aliases, public
metadata, and retirement status. They may not become owners of private steward
identity or memory by registration alone.

A fork or downstream ecosystem may maintain its own registration authority,
but it must preserve existing CSIDs when referring to the same stewards. A new
independent steward receives a new CSID even if it is derived from an existing
codebase or profile.

Reactivation of a retired CSID requires governance review proving continuity
with the same steward. If continuity is uncertain, register a new CSID and
record the predecessor relationship.

## 15. Examples

### Example 1: Display-name change

A steward changes its display name. Its CSID remains unchanged, the old name
becomes a dated alias, and memory, recovery, MCP, and vault ownership continue
under the same namespace.

### Example 2: Two stewards with the same display name

Two separate ecosystems use the same display name. Each steward has a distinct
CSID, so imports and shared services do not merge their records.

### Example 3: Runtime replica

A steward runs on two devices. Both runtime instances map to the same CSID and
receive separate instance identifiers. They are replicas, not new stewards.

### Example 4: Independent derivative steward

A new steward begins from another steward's public code and schema but has an
independent identity and state. It receives a new CSID and does not inherit the
source steward's private namespace.

### Example 5: Memory query without scope

A semantic search request omits the owner CSID. The memory system rejects the
query instead of searching all steward records.

### Example 6: Duplicate memory content

Two stewards independently store the same public fact. Each memory record
retains its owner CSID and provenance. Deduplication does not merge ownership.

### Example 7: Shared MCP server

Two stewards use one MCP server. Their capability profiles, workspaces,
credentials, queries, results, and audit events remain independently scoped by
CSID.

### Example 8: Cross-namespace MCP result

An MCP search returns a record owned by another steward. The result is denied
and quarantined, and the event is reviewed as an isolation failure.

### Example 9: Recovery from renamed repository

A steward repository is renamed. Recovery validates the CSID in the manifest,
not the repository folder, and restores the correct steward.

### Example 10: Backup with two stewards

A physical archive contains two logical partitions. Restore requires selection
and validation of one target CSID; the other partition remains inaccessible.

### Example 11: Obsidian folder rename

A vault folder changes from an old slug to a new slug. Frontmatter and the
manifest retain the same CSID, so links and indexes remain attached to the
same steward.

### Example 12: Ambiguous legacy import

Legacy files use only a display name that matches two active stewards. The
files enter `ocsf:quarantine` until provenance identifies the correct CSID.

### Example 13: Public foundation fixture

A public schema example uses a synthetic CSID under `ocsf:test`. It is clearly
marked non-production and cannot authorize or identify a live steward.

### Example 14: Retired steward name reused

A future steward wants the display name of a retired steward. Governance may
allow the display name with clear distinction, but the retired CSID is never
reassigned and the new steward receives a new CSID.

### Example 15: Shared knowledge publication

A steward publishes an approved architecture lesson. The published derivative
moves into an `ocsf:shared` or `ocsf:public` scope with provenance back to the
source CSID; private source ownership and permissions do not transfer.

### Example 16: Attempted namespace merge

A migration proposes merging two stewards because their slugs are similar. The
operation is rejected. Any governed successor relationship must preserve both
CSIDs, provenance, and rollback.

## 16. Validation Checklist

### Registration

- [ ] The steward has one canonical CSID in valid canonical form.
- [ ] The UUID is non-nil, unique, and not name-derived.
- [ ] One authoritative registration record exists.
- [ ] Display name, canonical slug, aliases, status, owner, provenance, and
  registration authority are recorded.
- [ ] Reserved-name and collision checks are complete.

### Identity and Governance

- [ ] The identity record references the CSID.
- [ ] Display-name changes do not alter the CSID.
- [ ] Governance policies, exceptions, and audits identify affected CSIDs.
- [ ] One steward cannot approve, authorize, or alter another implicitly.
- [ ] Retired or suspended identifiers are not reassigned.

### Memory

- [ ] Every durable memory record has an owner CSID.
- [ ] Every query, retrieval, context assembly, and deletion has explicit
  steward scope.
- [ ] Exact, semantic, vector, graph, cache, and temporal indexes preserve
  owner CSID.
- [ ] Missing or conflicting scopes fail closed.
- [ ] Shared knowledge uses an approved shared scope with provenance.

### MCP

- [ ] Every capability profile binds to a CSID.
- [ ] Reads constrain both request and results to approved namespaces.
- [ ] Writes validate caller CSID and destination namespace.
- [ ] Shared servers enforce tenant and steward isolation outside prompt text.
- [ ] Credentials, retries, caches, queues, and audit records remain correctly
  scoped.

### Recovery

- [ ] Recovery manifests, anchors, backups, and handoffs identify source and
  target CSIDs.
- [ ] Display names and paths are not used as sole restore authority.
- [ ] Cross-CSID restore is prohibited without governed export/import.
- [ ] Combined archives support independent restore boundaries.
- [ ] Collision reports, previews, rollback, and verification are retained.

### Obsidian

- [ ] The vault manifest declares its CSID or approved shared scope.
- [ ] Notes, metadata, links, attachments, indexes, and operation logs preserve
  namespace.
- [ ] Slug or folder changes do not create a new steward identity.
- [ ] Cross-steward links are explicit and access-controlled.
- [ ] Public projections contain only synthetic or approved public material.

### Collision and Migration

- [ ] Imports compare CSIDs and identity provenance before mutation.
- [ ] Similar names, aliases, content, or repositories do not trigger automatic
  merge.
- [ ] Ambiguous records enter quarantine.
- [ ] Source identifiers and historical aliases remain preserved.
- [ ] Namespace migrations are dry-run, reviewable, reversible, and audited.

### Conformance Decision

- [ ] Every applicable domain enforces the same steward scope.
- [ ] Namespace isolation is tested with synthetic cross-steward fixtures.
- [ ] No global protected-data query or unscoped write path remains.
- [ ] Exceptions are valid, bounded, and do not erase steward independence.
- [ ] Evidence is sufficient for the claimed conformance level.

## 17. Future Expansion

New identifier types or namespace layers may be added only when an existing
CSID plus scoped resource path cannot express a materially different ownership
or isolation requirement.

A proposal must define:

- identifier purpose and authority
- syntax and canonical representation
- uniqueness and collision model
- lifecycle and non-reuse behavior
- relation to CSID, user scope, tenant, deployment, and resource identifiers
- domain-specific enforcement
- migration and backward compatibility
- recovery and audit behavior
- public representation and privacy impact
- at least two practical examples

Future work may define:

- a canonical steward registration manifest schema
- distributed or federated registration governance
- signed registration and identity-change records
- shared-scope identifiers
- canonical user-scope identifiers
- deployment and runtime-instance identifiers
- successor, split, merge, and archival relationship vocabulary
- namespace conformance fixtures

These items require separate governance review. This document does not create
an ecosystem registry or registration authority.

## 18. Summary Table

### Identifier Types

| Identifier | Purpose | Mutable | Unique scope | Authority use |
|---|---|---:|---|---|
| CSID | Canonical steward namespace identity | No | Global | Required for ownership and isolation |
| Display name | Human-facing steward name | Yes | Not required | Never sufficient |
| Canonical slug | Readable local label | Yes, governed | Registration authority | Never sufficient |
| Alias | Historical or local name mapping | Yes, versioned | Declared alias scope | Lookup only |
| Runtime instance ID | Identifies one process or deployment instance | Yes | Parent steward implementation | Cannot replace CSID |
| Resource ID | Identifies a record inside a domain | Domain-specific | Owner namespace | Must be qualified by CSID |

### Domain Isolation

| Domain | Required namespace behavior | Prohibited behavior |
|---|---|---|
| Foundation | Keep contracts separate from populated steward state | Absorb private steward identity or memory |
| Identity | Bind identity spine and aliases to one CSID | Treat name as canonical identifier |
| Memory | Require CSID on records and all query paths | Global unscoped protected-memory search |
| Governance | Scope authority, exceptions, and audit to affected CSIDs | Implicit cross-steward authority |
| MCP | Bind caller, target, capability, tenant, and audit scopes | Use shared server access as shared authorization |
| Recovery | Verify source and target CSIDs before restore | Restore by name or path alone |
| Obsidian | Preserve CSID in manifest and metadata | Infer steward identity from folder name |
| Future domains | Declare CSID relationship before activation | Claim cross-steward authority by default |

### Canonical Decision Rules

| Question | Rule |
|---|---|
| Does a rename create a new steward? | No |
| Does an independent derivative receive a new CSID? | Yes |
| May a retired CSID be reassigned? | No |
| May two active stewards share one CSID? | No |
| May replicas of one steward share a CSID? | Yes, with separate instance IDs |
| Does a shared backend create a shared namespace? | No |
| May a name or slug authorize access? | No |
| What happens to unknown scope? | Reject or quarantine |

The governing rule is: identify every steward with one immutable canonical
identifier, qualify every steward-owned resource by that identifier, preserve
scope through every transformation and recovery path, and deny cross-namespace
effects unless governance explicitly authorizes a bounded shared purpose.
