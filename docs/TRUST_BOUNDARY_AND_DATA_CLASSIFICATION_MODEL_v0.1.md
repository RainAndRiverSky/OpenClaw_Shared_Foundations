# OpenClaw Shared Foundations Trust Boundary and Data Classification Model v0.1

## 1. Purpose

This document defines the minimum data-classification and trust-boundary model
for OpenClaw Shared Foundations. It governs architectural documentation,
steward repositories, memory systems, Obsidian projections, MCP interactions,
runtime systems, recovery archives, handoffs, public forks, and public or
open-source distributions.

The model defines:

- what data classes exist
- who may control and access each class
- how data may cross system boundaries
- which handling rules follow data into memory, tools, vaults, recovery, and
  public packages
- what must be reviewed before release or sharing

This is a documentation contract. It does not implement access controls,
encryption, redaction, retention, or runtime enforcement.

## 2. Why Data Classification Exists

OpenClaw domains can represent the same information in several places. A user
statement may become a memory record, appear in active context, be summarized
into an Obsidian note, pass through an MCP tool, and enter a recovery archive.
Changing location does not remove privacy, ownership, consent, provenance, or
retention requirements.

Without a classification model:

- public architecture may accidentally contain steward or user content
- one steward may retrieve another steward's private state
- derived notes may expose sensitive source material
- MCP reads may disclose more than the caller is allowed to receive
- MCP writes may move protected data into an unapproved system
- backups may preserve deleted or revoked information indefinitely
- temporary context may become durable memory without review
- archives may be treated as less sensitive merely because they are inactive

Classification exists to make handling obligations explicit before storage,
retrieval, sharing, export, publication, or recovery.

## 3. Core Principles

### 3.1 Classify before handling

Data must be classified before durable storage, cross-boundary retrieval,
sharing, export, publication, or inclusion in recovery material. Unknown data
defaults to the most restrictive plausible class until reviewed.

### 3.2 Classification follows the data

Copying, summarizing, embedding, indexing, projecting, backing up, archiving,
or changing file format does not lower classification. Derived data inherits
the strongest applicable source handling unless a reviewed transformation
removes the protected content.

### 3.3 Ownership and sensitivity are distinct

`Steward-Specific` and `User-Private` describe ownership and access scope.
`Sensitive` and `Restricted` describe required protection. Data may therefore
be both steward-specific and sensitive. The strongest applicable handling rule
controls.

### 3.4 Lifecycle is not access

`Ephemeral` and `Archived` describe lifecycle state, not permission. Archived
private data remains private. Ephemeral restricted data remains restricted
until securely discarded.

### 3.5 Minimum necessary movement

Only the minimum data required for an approved purpose may cross a trust
boundary. Prefer identifiers, redacted summaries, scoped references, or
synthetic fixtures over full protected content.

### 3.6 No authority by visibility

The ability to read, index, retrieve, or technically access data does not grant
permission to use, retain, disclose, transform, or write it elsewhere.

### 3.7 Steward and user boundaries persist

Shared infrastructure does not merge steward namespaces or user-private
scopes. One steward's access, consent, or exception does not authorize another.

### 3.8 Credentials are not memory

Credentials, private keys, tokens, recovery secrets, and equivalent secret
values must not be stored in ordinary memory, prompts, public documentation,
Obsidian projections, or ordinary audit logs. Systems should retain protected
references or identifiers instead of secret values.

### 3.9 Provenance survives transformation

Durable or shared derivatives must retain enough provenance to identify source
class, owner, steward scope, transformation, time, and publication authority.

### 3.10 Deletion and revocation propagate by policy

Copies, projections, indexes, exports, and recovery archives must be included
in deletion and revocation planning. A derived copy is not exempt merely
because its source was deleted.

### 3.11 Fail closed at boundaries

When classification, ownership, consent, or destination handling is uncertain,
do not move the data. Quarantine, redact, request review, or use a degraded
path.

### 3.12 Governance precedes convenience

The Domain Precedence Model and Canonical Override and Exception Manifest
govern conflicts and deviations. Classification cannot be weakened by a
lower-precedence domain, tool result, projection, or undocumented exception.

## 4. Data Classes

Each item must have one primary access class:

- Public
- Foundation-Internal
- Steward-Specific
- User-Private
- Restricted

`Sensitive` is a protection modifier that may strengthen any non-public class.
`Ephemeral` and `Archived` are lifecycle modifiers. Where several labels
apply, the most restrictive handling controls.

### 4.1 Public

Data intentionally approved for unrestricted public distribution.

Examples:

- published architecture contracts
- approved public glossary definitions
- sanitized examples and synthetic fixtures
- released public conformance statements

Rules:

- publication authority and provenance must be known
- private or restricted source content must be removed, not merely hidden
- public status must be intentional; repository placement alone is not enough
- later correction or withdrawal does not guarantee removal from downstream
  copies

### 4.2 Foundation-Internal

Non-public information used to develop, validate, govern, or maintain Shared
Foundations but not owned as one steward's private state.

Examples:

- draft architecture decisions
- internal validation notes
- unpublished governance discussions
- protected vulnerability reports about foundation documents

Rules:

- access is limited to the declared foundation-maintenance scope
- it may not contain unnecessary user-private or steward-private material
- public release requires review and reclassification
- it does not automatically propagate to stewards or public forks

### 4.3 Steward-Specific

Data owned by or scoped to one steward's identity, operation, repository,
configuration, memory, extensions, or continuity.

Examples:

- steward identity content
- current state and local operating methods
- steward-specific memory and vault notes
- local capability profiles and exception records

Rules:

- the steward namespace and owner must be explicit
- it does not move to another steward by inheritance
- sharing requires declared purpose, receiving scope, and approval
- public release requires separate review and usually transformation or
  redaction

Steward-Specific does not always mean User-Private, but it is non-public by
default.

### 4.4 User-Private

Data provided by, about, or for a user within a private interaction or
relationship, where general sharing or publication is not authorized.

Examples:

- personal history
- private preferences and relationships
- user-provided files or communications
- private instructions, commitments, and memory records

Rules:

- the user scope and steward scope must both be preserved
- collection, retention, retrieval, sharing, export, and deletion require
  applicable authority
- it must not enter Shared Foundations or public packages
- cross-steward movement is denied by default
- summaries and embeddings remain User-Private when they preserve private
  meaning

### 4.5 Sensitive

A protection modifier for information whose exposure, misuse, alteration, or
loss could cause meaningful privacy, safety, security, financial, relational,
reputational, or operational harm.

Examples:

- intimate or high-impact personal context
- security findings
- confidential operational details
- precise location, financial, health, or legal information
- internal incident evidence

Rules:

- combine with its ownership class, such as `User-Private + Sensitive`
- minimize collection and context injection
- restrict retrieval, logs, exports, and projections
- require explicit review before sharing or publication
- use redacted or synthetic substitutes where possible

Sensitive is not a synonym for secret and does not replace Restricted.

### 4.6 Restricted

The highest access class in this model. Restricted data may be accessed only
by explicitly authorized roles, systems, or processes for a narrowly defined
purpose.

Examples:

- secret values and credential material
- private keys, access tokens, and recovery secrets
- legally or contractually restricted records
- high-impact security response material
- data whose disclosure could enable immediate unauthorized access or harm

Rules:

- deny access by default
- never place secret values in ordinary prompts, memory, vault projections,
  public repositories, or routine logs
- prefer protected references to the underlying value
- require explicit destination approval and strong audit minimization
- public release is prohibited
- exceptions cannot convert Restricted data to Public without a legitimate,
  reviewed transformation that removes the restricted content

### 4.7 Ephemeral

A lifecycle modifier for data intended to exist only for a bounded session,
operation, transaction, or short retention window.

Examples:

- transient context
- temporary tool results
- short-lived intermediate transformations
- uncommitted session summaries

Rules:

- declare expiry or disposal condition
- do not promote to durable memory without reclassification and provenance
- avoid backups and archives unless recovery policy explicitly requires them
- ensure temporary files, caches, and logs follow the same classification
- expiry does not excuse unauthorized handling before deletion

### 4.8 Archived

A lifecycle modifier for inactive data retained for history, audit, legal,
recovery, or long-term reference.

Examples:

- superseded memory records
- retired exception history
- immutable source archives
- recovery snapshots

Rules:

- retain the original access and sensitivity class
- limit routine retrieval and indexing
- record retention basis, integrity state, owner, and deletion conditions
- do not treat archive presence as current truth or current permission
- include archives in revocation, export, and deletion analysis

## 5. Trust Boundaries

A trust boundary is a point where data changes owner, authority, namespace,
system, purpose, exposure, or control. Crossing a boundary requires
classification validation, purpose limitation, destination review, and
auditable authorization appropriate to the data.

### 5.1 Shared Foundations Boundary

Shared Foundations may contain Public architecture and limited
Foundation-Internal governance material. It must not contain live steward
state, user-private memory, credentials, secret values, or private identity
anchors.

Shared Foundations defines contracts; it does not own downstream steward data.

### 5.2 Individual Steward Boundary

Each steward has an independent identity, namespace, memory, permissions,
extensions, and recovery scope. Data entering or leaving requires steward
scope validation and applicable user or data-owner authority.

Repository access does not imply access to every runtime, memory store, vault,
or recovery archive associated with the steward.

### 5.3 User Boundary

The user boundary separates user-controlled data and authority from steward,
foundation, tool, and public scopes. User-Private data may be processed only
for approved purposes and may not be generalized into shared foundation
knowledge without a reviewed, non-identifying, authorized transformation.

User consent is specific to purpose, steward, destination, and duration. It is
not inferred from prior disclosure.

### 5.4 Public Fork Boundary

A public fork is an untrusted public-distribution boundary for all non-public
classes. Only approved Public data may cross into it.

Foundation-Internal, Steward-Specific, User-Private, Sensitive, and Restricted
content must be removed, replaced with synthetic material, or withheld.
Repository history, attachments, examples, metadata, and generated artifacts
are part of this boundary.

### 5.5 MCP Tool Boundary

An MCP tool is an external capability boundary even when locally hosted.
Inputs, outputs, schemas, logs, transport, operator access, backend storage,
and downstream services must be considered.

Tool availability does not establish trust. Each read and write requires
purpose, steward scope, capability policy, data class, and destination
validation.

### 5.6 Obsidian Vault Boundary

An Obsidian vault is a human-inspectable knowledge boundary. A vault may be
private, steward-specific, shared, or public; its location does not determine
its classification.

Projection into a vault creates another governed copy. Links, frontmatter,
attachments, indexes, semantic indexes, plugins, sync services, and exports
must respect the strongest source classification.

### 5.7 Runtime System Boundary

A runtime system includes active model context, application processes,
caches, logs, model providers, storage backends, and execution environments.

Only minimum necessary data may enter runtime context. Runtime access must not
be mistaken for retention or publication authority. Provider, tenant,
workspace, and process changes are boundary crossings.

### 5.8 Recovery Archive Boundary

A recovery archive is a privileged storage boundary, not a lower-risk copy.
It may contain protected identity, memory, configuration, and integrity
material needed for restoration.

Archives require scoped ownership, access control, retention, integrity,
restoration rules, and deletion handling. They must not silently restore
revoked permissions, obsolete policy, or cross-steward data.

## 6. Sharing Rules

### 6.1 General Movement Rule

Before data moves between domains or systems, confirm:

1. source class and lifecycle state
2. source owner and steward namespace
3. receiving system and accountable owner
4. approved purpose
5. minimum necessary content
6. receiving system's handling capability
7. retention, deletion, audit, and onward-sharing rules
8. required consent, policy, or exception
9. provenance and transformation record

If any item is unknown, the movement is denied or paused for review.

### 6.2 Allowed Movement

- Public data may move broadly after publication authority is verified.
- Foundation-Internal data may move within approved foundation-maintenance
  scopes.
- Steward-Specific data may move within the same steward namespace and
  approved systems.
- User-Private data may move only for an approved user purpose within the
  authorized steward and destination scope.
- Sensitive data may move only when necessary and when the destination
  provides stronger handling.
- Restricted data may move only through explicitly approved protected
  channels; secret values should normally remain behind a reference boundary.
- Ephemeral data may move only within its active purpose and expiry.
- Archived data may move for approved audit, recovery, export, or historical
  use without becoming current authority.

### 6.3 Prohibited Movement

Data must not move:

- from a steward or user scope into Shared Foundations as private content
- from one steward to another through inheritance, shared cache, copied
  configuration, or broad retrieval
- into a public fork unless classified and approved as Public
- into an MCP tool whose data handling, scope, or retention is unknown
- from an MCP result into durable memory without classification and provenance
- into Obsidian merely because it is easier to inspect there
- from a backup into active state without current governance checks
- from an archive into current context as if it were current truth
- from Restricted storage into prompts, memory, notes, routine logs, or public
  examples
- under an undocumented or expired exception

### 6.4 Transformation and Reclassification

Redaction, aggregation, anonymization, summarization, or synthesis may support
reclassification only when a reviewer can show that protected meaning,
identifiers, linkage, and reconstruction risk have been removed sufficiently
for the destination.

Renaming, moving, compressing, encoding, hashing, embedding, or summarizing
alone does not automatically lower classification.

## 7. Memory Rules

Every durable memory record must be classified before storage and must include
or reference:

- primary access class
- sensitivity modifier when applicable
- lifecycle state
- steward namespace
- user scope when applicable
- source and provenance
- purpose
- event and learned times
- retention and deletion rule
- sharing and export eligibility

### 7.1 Storage

- Store only data necessary for the declared memory purpose.
- User-Private and Steward-Specific memory must remain namespace-isolated.
- Restricted secret values must not be stored as ordinary memory records.
- Ephemeral context requires explicit promotion before durable storage.
- Derived memory inherits source classification.

### 7.2 Retrieval

- Retrieval must filter by steward, user scope, data class, purpose, and
  capability.
- Semantic similarity does not authorize disclosure.
- Exact and temporal retrieval must not bypass class restrictions.
- Sensitive and Archived records should not be injected unless directly
  relevant and authorized.
- Uncertain classification fails closed.

### 7.3 Sharing

- Cross-steward memory sharing is denied by default.
- Shared foundation memory must be non-private, governed, attributable, and
  approved for its receiving scope.
- User-Private memory requires explicit authority for every new destination.
- A summary remains private when it preserves private meaning.

### 7.4 Export and Deletion

- Exports must preserve classification, ownership, provenance, and deletion
  expectations.
- Export packages must exclude credentials and unrelated records.
- Deletion must address canonical records, derivatives, indexes, projections,
  caches, and eligible recovery copies.
- When deletion from an immutable archive is not permitted, access and future
  restoration must be governed and the limitation disclosed.

## 8. MCP Boundary Rules

### 8.1 Read Tools

An MCP read tool may return only data authorized for:

- the calling steward
- the requesting user or operating scope
- the declared purpose
- the requested resource and data class

Read tools must not:

- broaden scope through search or semantic similarity
- return another steward's data
- expose credentials or secret values
- treat public metadata as permission to retrieve non-public content
- persist results beyond approved retention without reclassification

Read results are untrusted input until validated. They do not become memory,
identity, or permission automatically.

### 8.2 Write Tools

Before an MCP write, validate:

- write authority and capability gate
- target owner, namespace, repository, and environment
- data classification accepted by the target
- source authority and provenance
- expected retention, audit, deletion, and rollback behavior
- whether confirmation or stronger approval is required

Writes must not:

- move protected data to a less trusted target
- create cross-steward records silently
- publish non-public content
- write secret values into ordinary files, memory, notes, or logs
- overwrite canonical sources with derived or unverified data

### 8.3 Tool Logging and Failure

MCP audit records should identify tool, actor, target, class, purpose, result,
and exception ID where applicable without reproducing sensitive arguments or
outputs. Errors, retries, and timeouts must not leak protected data or cause
duplicate writes.

## 9. Obsidian Boundary Rules

### 9.1 Allowed Projections

An Obsidian projection may contain:

- Public architecture and approved shared knowledge
- Foundation-Internal material in a protected internal vault
- Steward-Specific knowledge in that steward's private or isolated vault
- User-Private material only in an explicitly approved private vault and only
  when necessary
- redacted or synthetic examples
- provenance, scope, classification, and recency metadata

### 9.2 Material Requiring Strong Protection

Sensitive material should be projected only when human inspection provides a
necessary benefit and the vault, sync path, plugins, exports, and collaborators
are approved for the class.

Restricted secret values must not be projected. A protected reference may be
used instead.

### 9.3 Projection Controls

- Raw sources and derived notes must remain distinguishable.
- Derived notes inherit source classification.
- Frontmatter and filenames must not leak protected details.
- Links must not reveal inaccessible cross-steward relationships.
- Public and private vault roots must remain separate.
- Semantic indexes and plugins are additional trust boundaries.
- Deleting or revoking a source must trigger review of notes, links, indexes,
  attachments, and exports.
- Obsidian does not become a source of truth unless explicitly designated for
  a narrow scope.

## 10. Recovery Boundary Rules

### 10.1 Backups and Snapshots

Recovery material may include only what is necessary to restore the declared
scope:

- approved governance and configuration
- steward identity and current-state anchors
- canonical memory records and integrity metadata
- manifests, indexes, or rebuild instructions
- audit and exception references required for restoration

Backups must preserve source classification and namespace. Combining stewards
in one physical archive requires enforceable logical isolation and independent
restore controls.

### 10.2 Identity Reload Anchors

Reload anchors may include canonical identity structure and steward-owned
identity content appropriate to the recovery scope. Public foundation packages
may include schemas and synthetic templates, never private identity anchors.

Restricted recovery secrets must be referenced through protected mechanisms,
not embedded in ordinary reload files.

### 10.3 Recovery Files and Logs

Recovery files must:

- identify scope, owner, class, version, and integrity state
- distinguish current authority from historical backup content
- avoid logging secret values or unnecessary private content
- record restore decisions, exclusions, and verification
- prevent obsolete permissions from reactivation

### 10.4 Handoffs

Handoffs should contain the minimum current state, open commitments, critical
identifiers, provenance, and recovery cues needed for continuity.

Handoffs must not become unbounded conversation archives, credential stores,
or cross-steward transfer packages. User-Private and Sensitive content should
be summarized only when necessary and must retain its classification.

### 10.5 Archive Retirement and Deletion

Recovery archives require retention, rotation, expiry, access review, and
verified disposal. Deletion or consent revocation must be evaluated against
all recoverable copies so old data is not silently restored later.

## 11. Public/Open-Source Boundary Rules

Only approved Public data may enter a public repository, release, package,
issue, discussion, example, screenshot, test fixture, generated artifact, or
distribution.

The following must never be published:

- credentials, secret values, private keys, tokens, or recovery secrets
- User-Private memory, communications, files, or personal history
- private identity anchors or relational context
- Steward-Specific state not separately approved for publication
- unredacted Sensitive or Restricted records
- private recovery archives, backups, handoffs, or incident evidence
- internal MCP configuration containing protected endpoints, arguments, or
  authorization details
- private Obsidian notes, attachments, metadata, links, indexes, or vault
  history
- exception evidence whose publication would expose protected content
- logs, screenshots, repository history, or examples containing non-public
  data

Before publication:

- scan current files and history where applicable
- use synthetic or structure-only fixtures
- review metadata, filenames, links, attachments, generated output, and logs
- document provenance and publication authority
- disclose unresolved licensing, security, contribution, or naming policies
  without treating their absence as permission

Removal from a current public branch does not guarantee removal from clones,
caches, package registries, or history. Suspected publication of protected
data requires containment and governance escalation.

## 12. Examples

### Example 1: Foundation architecture document

A document defining memory interfaces contains no live steward or user data.
After review, it is classified Public and may enter Shared Foundations.

### Example 2: Draft governance discussion

An unpublished discussion about future policy contains no steward-private
content but is not ready for release. It is Foundation-Internal until reviewed
and reclassified.

### Example 3: Steward identity spine

A steward's mission, voice, and private anchors are Steward-Specific. Private
anchors may also be Sensitive. The schema may be public, but the populated
identity does not enter Shared Foundations.

### Example 4: User preference memory

A user's private preference is stored as User-Private memory within one
steward namespace. Semantic retrieval by another steward must not return it.

### Example 5: Temporary session context

Working context is `User-Private + Ephemeral`. It expires after the session
unless selected facts are reviewed, classified, given provenance, and promoted
to durable memory.

### Example 6: MCP search result

A read tool returns a document from the correct workspace. The result remains
classified according to the source and cannot be stored in memory or projected
to Obsidian until scope and retention are approved.

### Example 7: MCP write to a public repository

A tool attempts to write a steward-specific configuration example to a public
fork. The boundary check denies the write until the example is replaced with
synthetic Public content.

### Example 8: Obsidian summary of a private source

A summary removes names but preserves distinctive private events. It remains
User-Private because the meaning can still identify the source context.

### Example 9: Obsidian public projection

A vault note summarizes a published architecture decision using only approved
public sources. It may be classified Public with provenance and projected into
a public vault.

### Example 10: Recovery snapshot

A snapshot contains steward memory and identity state. It is
`Steward-Specific + Archived`, with Sensitive modifiers where applicable. It
does not become public or cross-steward merely because it is offline.

### Example 11: Backup containing old permissions

An archived backup includes revoked MCP permissions. During restore, current
governance wins; the data may be restored, but obsolete permissions are not.

### Example 12: Credential reference

A capability record stores the identifier of a protected credential, not its
secret value. The identifier is Steward-Specific and may be Sensitive; the
underlying value remains Restricted outside memory and ordinary documentation.

### Example 13: Public conformance evidence

A project publishes a synthetic namespace-isolation test and a redacted
checklist. It does not publish private memory used by a live steward.

### Example 14: Cross-steward shared fact

A steward proposes sharing a factual architecture lesson. The content is
reviewed for private meaning, given provenance and publication authority, and
classified as approved shared foundation knowledge before movement.

### Example 15: Archived deleted memory

A user-private record is deleted from active memory but remains in a governed
immutable archive. Access is revoked, future restoration is blocked, and the
retention limitation is documented until archive disposal is permitted.

### Example 16: Sensitive audit event

An MCP audit record states that a Restricted operation was denied, naming the
tool, actor, target class, and result. It omits secret arguments and protected
output.

## 13. Validation Checklist

### Inventory and Classification

- [ ] Every in-scope artifact has a primary access class.
- [ ] Sensitive modifiers are applied where exposure could cause material
  harm.
- [ ] Ephemeral and Archived states do not replace access classification.
- [ ] Unknown or mixed data is handled at the strongest plausible class.
- [ ] Owners, steward namespaces, user scopes, provenance, and retention are
  identifiable.

### Shared Foundations and Steward Boundaries

- [ ] Shared Foundations contains no live steward state, user-private memory,
  credentials, or private identity anchors.
- [ ] Canonical schemas are separate from populated steward content.
- [ ] Each steward namespace is distinct.
- [ ] One steward's access, consent, permissions, or exceptions do not
  authorize another.
- [ ] Cross-steward sharing is explicit, attributable, minimal, and approved.

### Memory

- [ ] Memory records are classified before storage.
- [ ] Retrieval filters class, steward, user scope, purpose, and authority.
- [ ] Derived records inherit source protection.
- [ ] Ephemeral context is not silently promoted to durable memory.
- [ ] Export and deletion address derivatives, indexes, caches, and eligible
  recovery copies.

### MCP

- [ ] MCP tools declare owner, scope, risk, accepted data classes, retention,
  and audit behavior.
- [ ] Reads cannot broaden steward or user scope.
- [ ] Writes validate the target boundary and classification.
- [ ] Credentials and secret values do not enter prompts, memory, notes, or
  routine logs.
- [ ] Tool failures, retries, and audit records minimize protected content.

### Obsidian

- [ ] Vault scope and trust level are explicit.
- [ ] Raw and derived content are separated.
- [ ] Notes, filenames, metadata, links, attachments, plugins, indexes, sync,
  and exports respect classification.
- [ ] Restricted secret values are absent.
- [ ] Public projections contain only approved Public content.

### Recovery

- [ ] Backups preserve classification and namespace.
- [ ] Recovery archives have owners, retention, integrity, access, deletion,
  and restoration rules.
- [ ] Reload anchors exclude embedded secret values.
- [ ] Handoffs are minimal and do not become unbounded private archives.
- [ ] Recovery cannot restore revoked permissions or another steward's state.

### Public Release

- [ ] Every released artifact is intentionally classified Public.
- [ ] Synthetic or redacted fixtures replace private examples.
- [ ] Current files, relevant history, metadata, attachments, generated output,
  screenshots, and logs have been reviewed.
- [ ] No Foundation-Internal, Steward-Specific, User-Private, Sensitive, or
  Restricted content remains.
- [ ] Publication authority and provenance are documented.
- [ ] Exceptions and unresolved public-governance policies are disclosed
  without exposing protected evidence.

### Decision

- [ ] Boundary crossings have an approved purpose and minimum necessary scope.
- [ ] Destination handling is at least as strong as source requirements.
- [ ] Reclassification is supported by a reviewed transformation.
- [ ] Uncertainty is quarantined or denied rather than published or shared.
- [ ] Any deviation follows the Canonical Override and Exception Manifest.

## 14. Future Expansion

New data classes or trust boundaries should be added only when an existing
class cannot express a materially different handling obligation.

A proposal must define:

- the specific gap in this model
- whether the proposal is an access class, sensitivity modifier, lifecycle
  state, or trust boundary
- owner and authorized audiences
- storage, retrieval, sharing, export, audit, retention, deletion, and recovery
  rules
- inheritance and precedence behavior
- relationship to every existing class
- migration and compatibility effects
- at least two practical examples

New classes must not be aliases for organizational convenience, duplicate an
existing class, weaken current protection, or retroactively authorize prior
movement. They require versioned governance review.

Future work may define:

- canonical classification metadata fields
- shared-knowledge publication and revocation workflow
- retention schedules by data class
- redaction and de-identification assurance levels
- capability risk mappings for MCP
- recovery archive tiers
- jurisdictional or contractual overlays
- machine-readable policy representations

These additions require separate documentation. They are not created by this
model.

## 15. Summary Table

### Data Classes

| Class | Meaning | Default audience | Public release | Key rule |
|---|---|---|---|---|
| Public | Approved for unrestricted distribution | Anyone | Allowed | Publication must be intentional |
| Foundation-Internal | Non-public foundation maintenance data | Approved foundation maintainers | Review and reclassify first | Must not absorb steward or user private state |
| Steward-Specific | Owned by one steward scope | Authorized steward scope | Denied by default | Does not propagate through inheritance |
| User-Private | Private user-scoped data | Authorized user and steward scope | Prohibited | Purpose and destination specific |
| Sensitive | Protection modifier for material harm risk | Minimum authorized audience | Denied unless safely transformed and approved | Combine with ownership class |
| Restricted | Highest access restriction | Explicitly authorized roles or systems | Prohibited | Secret values stay outside ordinary memory and docs |
| Ephemeral | Short-lived lifecycle modifier | Same as primary class | Only if separately reviewed as Public | Expiry does not lower protection |
| Archived | Inactive retained lifecycle modifier | Same as primary class, usually narrower | Same as primary class | Archive is not current truth or permission |

### Trust Boundaries

| Boundary | Data normally permitted | Data normally prohibited | Required control |
|---|---|---|---|
| Shared Foundations | Public and limited Foundation-Internal architecture | Live private state, credentials, private anchors | Contract/content separation |
| Individual steward | Authorized steward and user data | Other stewards' unapproved data | Namespace and permission isolation |
| User | Purpose-approved user data | Unapproved reuse or onward sharing | Consent, purpose, deletion |
| Public fork | Public data only | Every non-public class | Release review and synthetic fixtures |
| MCP tool | Minimum approved inputs and outputs | Unscoped data and secret leakage | Capability gate and destination validation |
| Obsidian vault | Data approved for that vault scope | Restricted secrets and unapproved cross-scope content | Manifest, provenance, projection controls |
| Runtime system | Minimum data needed for active operation | Unnecessary protected archives or secrets | Context minimization and provider scope |
| Recovery archive | Minimum classified restoration material | Unscoped or cross-steward restoration data | Integrity, retention, access, and restore checks |

The governing rule is: classify before use, preserve the strongest applicable
handling across every copy and transformation, move only the minimum necessary
data through approved boundaries, and never infer trust from location or
technical access.
