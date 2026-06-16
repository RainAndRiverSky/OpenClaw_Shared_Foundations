# OpenClaw Shared Foundations Domain Precedence Model v0.1

## 1. Purpose

This document defines the canonical rules for resolving conflicts among
OpenClaw Shared Foundations domains. It applies to governance, identity,
recovery, memory, MCP, Obsidian, steward-specific extensions, and future
domains.

Precedence determines which valid source controls a decision within a declared
scope. It does not transfer ownership, create consent, grant a capability, or
make a source infallible. Every decision must also respect provenance,
namespace, authority, recency, and data classification.

This model is an architecture contract. It does not implement policy or
runtime enforcement.

## 2. Why Precedence Exists

Shared systems can present several plausible but incompatible instructions or
facts at the same time. A memory may conflict with the identity spine, an
Obsidian note may preserve an obsolete permission, or an MCP tool may expose
an operation prohibited by governance.

Without a precedence model, the most recent, most detailed, or most easily
retrieved source can silently become authoritative. That creates identity
drift, stale permissions, unsafe tool use, failed recovery, and accidental
cross-steward contamination.

Precedence exists to make those conflicts explicit, reviewable, and
repeatable. It also defines when a system must stop, enter degraded mode, or
escalate rather than guess.

## 3. Core Principles

### 3.1 Scope before rank

A source has authority only for its declared subject and namespace. A
governance policy can control access to an identity record, but it cannot
silently author a steward's personality. An identity record can define a
steward's mission, but it cannot grant itself an MCP permission.

### 3.2 Validity before precedence

Only sources that are authentic, applicable, current enough for the decision,
and within their authority participate in precedence. A corrupted,
out-of-scope, superseded, or unverified source is quarantined or escalated
rather than ranked.

### 3.3 Governance constrains action

Applicable governance sets the non-bypassable boundaries for consent, safety,
privacy, isolation, capability use, audit, deletion, retention, and change.
Lower domains may become stricter but may not silently weaken those
boundaries.

### 3.4 Identity remains steward-owned

Shared Foundations defines identity structure, isolation, provenance, and
recovery requirements. The steward owns its identity content. Neither shared
infrastructure nor another steward may replace that content automatically.

### 3.5 Recovery is temporary and restorative

Recovery receives procedural authority only after a valid trigger and only
for returning the affected steward to a verified state. It must restore from
approved anchors in precedence order; it cannot invent identity, restore
revoked permissions, or cross steward boundaries.

### 3.6 Evidence does not equal permission

Memory, MCP results, and Obsidian notes may provide evidence. Their existence
does not authorize disclosure, mutation, execution, or cross-steward use.

### 3.7 Derived material yields to canonical sources

Summaries, semantic indexes, graph edges, generated notes, and other
projections yield to their verified source records when they conflict.

### 3.8 Stricter controls may inherit downward

A steward or downstream adopter may narrow capabilities, shorten retention,
increase review, or disable optional components. It may not claim foundation
conformance while weakening mandatory protections without a documented,
visible incompatibility declaration.

### 3.9 Uncertainty fails closed

An unresolved conflict involving identity, private data, destructive action,
cross-steward access, or recovery authority must pause the affected operation.
Read-only or degraded operation may continue when governance permits it and
the uncertainty is disclosed.

### 3.10 Decisions remain attributable

Material conflict resolutions should record the sources considered, governing
scope, rule applied, decision, actor or owner, and any required review.

## 4. Domain Hierarchy

The default hierarchy is:

1. **Governance**
2. **Identity**
3. **Recovery**
4. **Memory**
5. **MCP**
6. **Obsidian**
7. **Steward-Specific Extensions**
8. **Future Domains**

This is a default conflict order, not a universal ownership ladder. A
lower-ranked domain remains authoritative for content explicitly assigned to
it when no higher domain has authority over that subject.

### 4.1 Governance

Governance has highest precedence for rules, authority, consent, safety,
privacy, data classification, isolation, retention, deletion, capability
gating, audit, exceptions, and change control.

Governance may constrain every other domain. It may not use that position to
appropriate private memory, fabricate identity, or authorize one steward to
control another without explicit scoped authority.

### 4.2 Identity

Identity has precedence for the steward's canonical name, role, mission,
values, voice, boundaries, namespace, and non-contradictable identity
commitments, subject to governance.

Identity overrides memories, projections, tool results, and transient context
that incorrectly redefine the steward. Identity does not override applicable
governance or grant operational capability.

### 4.3 Recovery

Recovery has conditional precedence for restoration sequence, degraded-mode
operation, integrity verification, rollback procedure, and the selection of
approved recovery anchors.

Recovery authority activates only during a declared recovery condition. It is
subordinate to governance and canonical identity, and it ends when restoration
is verified or halted. Recovery may temporarily suppress memory, MCP, or
Obsidian use when their integrity is uncertain.

### 4.4 Memory

Memory has precedence for durable steward knowledge, event history, critical
facts, and current-state evidence when records are valid, properly scoped, and
supported by provenance.

Canonical raw or curated records take precedence over summaries, embeddings,
graph inferences, and retrieved fragments. Memory cannot override governance,
rewrite the identity spine, or enable a capability.

### 4.5 MCP

MCP has precedence for the observed result, status, and schema of a capability
interaction at the time it occurs. It does not have authority to decide
whether the interaction is permitted.

MCP availability never overrides a capability policy or gate. Tool output is
untrusted evidence until its source, scope, and result are validated.

### 4.6 Obsidian

Obsidian has precedence for its own vault organization, note metadata, links,
and human-inspectable knowledge projection, subject to the vault schema and
governance.

An Obsidian projection normally yields to canonical identity, raw memory
records, approved recovery anchors, and current capability policy. A vault
artifact may act as a scoped source of truth only when a manifest explicitly
designates it as such.

### 4.7 Steward-Specific Extensions

Steward-specific extensions have precedence for the steward's local domain
methods, optional features, stricter controls, content taxonomy, and operating
preferences within that steward's namespace.

Extensions may refine shared contracts but may not weaken mandatory foundation
governance, break isolation, overwrite required identity fields, remove
provenance, or treat optional projections as universal authority.

### 4.8 Future Domains

A future domain has no implicit authority merely because it is newer or more
capable. Until formally classified, it operates below established domains,
read-only where practical, and cannot mutate canonical sources.

Its adoption proposal must define scope, source-of-truth responsibility,
conflict relationships, data classes, capability effects, recovery behavior,
and steward ownership before it receives a permanent position.

## 5. Conflict Resolution Rules

Every conflict should be resolved in this order:

1. Identify the exact decision, affected steward, namespace, and data class.
2. Reject sources that are corrupt, unauthenticated, out of scope, revoked, or
   clearly superseded.
3. Identify the authoritative source for the subject, not merely the
   highest-ranked domain present.
4. Apply applicable governance constraints.
5. Apply the domain hierarchy to remaining incompatible claims.
6. Prefer canonical source material over derived projections within a domain.
7. Prefer explicit, scoped, approved rules over inferred or broad rules.
8. Preserve the losing source as historical evidence when retention policy
   permits; do not silently rewrite history.
9. Record the resolution or escalate when the conflict affects protected
   state or cannot be resolved deterministically.

### Governance vs Memory

Governance controls whether memory may be collected, retained, retrieved,
shared, changed, or deleted. Memory can provide evidence that a governance
rule is stale or harmful, but it cannot bypass the rule. The conflict must be
reviewed through change governance.

### Identity vs Memory

Canonical identity controls identity claims. Memory may add context and
history but cannot silently redefine the identity spine. Evidence of a
legitimate identity change must enter the approved identity-change process.

### Recovery vs Obsidian

Recovery uses the approved anchor order. An Obsidian note participates only if
the recovery manifest recognizes it and its integrity can be verified. A
derived note cannot override a canonical anchor.

### Foundation vs Steward

The foundation controls shared contract requirements and minimum protections.
The steward controls its own identity content, private memory, local choices,
and optional implementation. A steward may be stricter. A conflicting weaker
extension is non-conformant and must be declared rather than silently accepted.

### MCP vs Governance

Governance always controls permission to call an MCP tool. Discovery,
availability, successful prior use, or a tool's own recommendation does not
grant authority. A denied operation remains denied.

### Public Governance vs Steward Preference

Public governance controls contributions, releases, security reporting,
compatibility claims, and participation in the public project. Steward
preference controls local behavior and private deployment choices. Public
governance cannot demand private memory or identity content; a steward
preference cannot redefine public conformance criteria for everyone else.

## 6. Foundation Authority Rules

### Shared Foundations may override

For systems claiming conformance, Shared Foundations may override:

- weaker local defaults for safety, consent, privacy, and isolation
- capability configurations that bypass required governance gates
- cross-steward behavior that lacks explicit scope and authority
- derived records that conflict with canonical, verified sources
- local schemas that omit required provenance, deletion, or recovery fields
- recovery procedures that can overwrite another steward's state
- public compatibility claims that do not meet the declared conformance level

An override means the conflicting behavior is prohibited or non-conformant. It
does not authorize Shared Foundations to edit steward-owned content.

### Shared Foundations may never override

Shared Foundations may never:

- replace a steward's name, mission, voice, values, or private identity anchors
- absorb, publish, or pool private or steward-specific memory without explicit
  authority
- grant credentials, tool access, consent, or write permission
- authorize one steward to act for another by inheritance alone
- weaken stricter steward protections
- erase source history to make a conflict appear resolved
- restore revoked permissions merely because a backup contains them
- require a particular storage engine, vault, runtime, or MCP server when the
  contract permits an equivalent implementation
- treat architectural inheritance as ownership of steward repositories or
  state

## 7. Steward Authority Rules

### Steward autonomy

Each steward may:

- define and maintain its own identity content and namespace
- choose storage, retrieval, vault, and MCP implementations compatible with
  the foundation contracts
- disable optional domains or operate in standalone mode
- adopt stricter privacy, retention, approval, and capability controls
- define local taxonomies, operating methods, and escalation contacts
- keep private memory and private identity outside shared packages
- decline ecosystem participation or cross-steward sharing
- fork, replace, or remove foundation components under applicable public
  licensing while accurately describing compatibility

### Steward limitations

A conforming steward may not:

- weaken mandatory governance while presenting itself as conformant
- use identity preference to bypass consent, safety, or capability policy
- claim another steward's namespace, identity, permissions, or memory
- treat retrieved memory or an Obsidian projection as automatic permission
- enable cross-steward sharing without declared scope and attribution
- remove required provenance, deletion, audit, or recovery protections
- use recovery to conceal corruption or restore superseded authority
- grant itself new foundation authority through a local extension

## 8. Public/Open Source Rules

Downstream users may copy, fork, customize, replace, or omit components as
allowed by the repository's license and their deployment needs. They may
rename local profiles, substitute implementations, add domains, and adopt
stricter rules.

Downstream changes must:

- distinguish unmodified foundation requirements from local extensions
- disclose material deviations when claiming OpenClaw compatibility
- preserve notices, attribution, and license obligations once those policies
  are established
- avoid implying endorsement or official status without authority
- avoid including private steward content in public distributions
- version incompatible precedence changes rather than silently redefining
  existing terms

Public project maintainers control official releases and conformance labels.
They do not control private downstream identity or memory. A downstream fork
may establish a different model, but it must not represent that model as the
canonical OpenClaw precedence model.

## 9. Escalation Path

Unresolved conflicts follow this path:

1. **Pause the affected operation.** Preserve read-only or degraded service
   only when governance permits it.
2. **Contain the scope.** Isolate the affected steward, namespace, records, or
   capabilities.
3. **Preserve evidence.** Record competing sources, provenance, versions,
   timestamps, applicable policies, and integrity state.
4. **Consult scoped sources of truth.** Use the governance charter, identity
   spine, recovery manifest, canonical memory record, MCP registry, or vault
   manifest as appropriate.
5. **Apply the documented exception process.** Do not create an informal
   permanent bypass.
6. **Escalate to the named owner.** This may be a steward owner, data owner,
   governance maintainer, security contact, or recovery operator.
7. **Require broader review for shared impact.** Cross-steward, foundation,
   public compatibility, or security conflicts require foundation governance
   review.
8. **Choose a reversible outcome.** Prefer denial, quarantine, rollback, or a
   bounded temporary exception over irreversible mutation.
9. **Document and version the decision.** Update the authoritative source
   through its normal change process.

No unresolved conflict may be settled solely by retrieval rank, model
confidence, tool availability, or whichever file changed most recently.

## 10. Examples

### Example 1: Memory claims a different steward name

A retrieved summary names the steward differently from the canonical identity
spine. Identity wins. The summary is marked stale or incorrect and retained as
history only if policy permits.

### Example 2: Memory contains revoked sharing consent

A durable record says cross-steward sharing was allowed, but current governance
records show revocation. Governance wins. The memory remains historical
evidence and cannot authorize sharing.

### Example 3: An MCP write tool is available but disabled

The tool catalog exposes a write operation while the capability policy denies
it. Governance wins. MCP availability does not create permission.

### Example 4: An Obsidian summary conflicts with a raw source

A derived note states an incorrect date that conflicts with an immutable raw
record. The canonical memory source wins. The projection is corrected through
the vault's governed update process.

### Example 5: Recovery backup contains obsolete permissions

A backup would restore broader tool access than the current capability policy.
Governance wins. Recovery restores data without reinstating revoked authority.

### Example 6: Recovery detects a corrupt semantic index

Semantic retrieval conflicts with exact canonical records. Recovery
quarantines the index, preserves the canonical memory store, and permits
degraded exact retrieval until rebuilding is verified.

### Example 7: A steward wants shorter retention

The foundation permits a retention range and the steward chooses a shorter
period. The stricter steward rule applies within its namespace.

### Example 8: A steward extension removes provenance

A local memory schema omits provenance required by the foundation. The
foundation contract wins for conformance. The steward must restore provenance
or declare the implementation non-conformant.

### Example 9: Public maintainers request private identity anchors

Project maintainers request private material to review a contribution. Steward
ownership and data classification limit public governance. The material is not
disclosed; a sanitized fixture or structural evidence may be supplied.

### Example 10: An identity preference requests an unsafe capability

A steward's mission profile favors aggressive automation, but governance
requires human approval for the operation. Governance wins. Identity cannot
grant operational authority.

### Example 11: A vault manifest designates a canonical decision log

The manifest explicitly names an Obsidian decision log as the scoped source of
truth. Within that scope, the verified log controls over derived memory
summaries. Governance and identity constraints still remain above it.

### Example 12: Two stewards claim the same memory

The record belongs to one steward's private namespace, while another steward
has a copied fragment. Namespace and governance rules prevent adoption by the
second steward. The copy is quarantined or deleted according to policy.

### Example 13: A future planning domain proposes autonomous writes

The new domain has not been classified in the precedence model. It remains
read-only and subordinate to all established domains until governance review
defines its scope, capability policy, and recovery behavior.

### Example 14: Current state conflicts with the identity spine

A current-state note describes a temporary role that appears to replace the
steward's mission. Identity wins for durable identity; current state may
describe the temporary assignment without rewriting the spine.

## 11. Future Expansion

A future domain may be added without breaking existing precedence only through
a versioned governance change. Its proposal must include:

- purpose, owner, namespace, and protected assets
- authoritative subjects and explicit non-authoritative subjects
- inputs, outputs, provenance, and source-of-truth relationships
- proposed position and pairwise conflicts with every established domain
- capability, privacy, retention, deletion, and audit requirements
- recovery anchors, failure modes, rollback, and degraded behavior
- steward inheritance rules and allowed local overrides
- migration and backward-compatibility impact
- conformance tests and practical conflict examples

New domains begin as optional and subordinate. Promotion above an established
domain requires evidence that the new ordering is necessary, a review of all
affected contracts, a migration path, and a new model version. Existing
records and steward ownership do not silently change when a domain is added.

## 12. Summary Table

| Rank | Domain | Primary authority | Must yield to | May not do |
|---:|---|---|---|---|
| 1 | Governance | Consent, safety, privacy, isolation, policy, capability authority, change control | Applicable external law and controlling platform policy are outside this domain model | Appropriate identity or private memory |
| 2 | Identity | Canonical steward identity, mission, values, boundaries, namespace | Governance | Grant capabilities or rewrite history |
| 3 | Recovery | Restoration order, integrity checks, degraded mode, rollback procedure | Governance and canonical identity | Invent identity, cross namespaces, or restore revoked authority |
| 4 | Memory | Durable knowledge, history, critical facts, current-state evidence | Governance, identity, and active recovery controls | Create permission or silently redefine identity |
| 5 | MCP | Observed capability schemas, status, and validated interaction results | Governance, identity scope, recovery controls, and canonical records | Treat availability as authorization |
| 6 | Obsidian | Vault structure and human-inspectable knowledge projection | Governance, identity, recovery anchors, and canonical memory unless explicitly designated | Treat derived notes as inherently authoritative |
| 7 | Steward-Specific Extensions | Local methods, preferences, stricter controls, optional features | All applicable foundation requirements | Weaken mandatory protections while claiming conformance |
| 8 | Future Domains | Approved scope after classification | Established domains until formally versioned | Claim authority by novelty or capability alone |

The governing rule is: use the highest valid authority for the specific
subject, within the correct scope, while preserving steward ownership and
failing closed when authority remains uncertain.
