# OpenClaw Shared Foundations Minimum Conformance Profile v0.1

## 1. Purpose

This document defines the minimum requirements a steward, downstream
repository, public fork, or future OpenClaw-compatible system must satisfy or
respect when describing its relationship to OpenClaw Shared Foundations.

It establishes conformance levels, required domains, mandatory protections,
optional components, inheritance traceability, exception handling, precedence
requirements, public-facing obligations, and a review checklist.

This profile is an architecture and documentation standard. It does not
certify a system, authorize use of a name or mark, finalize licensing policy,
or prove runtime behavior.

## 2. Why Conformance Exists

Shared terminology without measurable requirements permits incompatible
systems to make the same compatibility claim. A system could adopt the
OpenClaw vocabulary while omitting namespace isolation, provenance, recovery,
capability governance, or steward ownership.

Conformance exists to:

- make compatibility claims specific and reviewable
- preserve steward identity and private-memory independence
- distinguish required protections from optional technology
- support multiple runtimes, storage systems, and deployment modes
- expose exceptions and deviations rather than hiding them
- prevent documentation-only similarity from implying operational compliance
- give downstream projects a stable minimum inheritance contract

Conformance is always scoped to a named system, version, environment, and
profile. It is not inherited merely through branding, repository ancestry,
copied documentation, or use of an OpenClaw-related component.

## 3. Conformance Levels

Every claim must name exactly one current level, the Shared Foundations
version assessed, the assessed scope, the assessment date, and whether the
claim is self-assessed or independently reviewed.

### 3.1 Foundation-Aligned

A system is **Foundation-Aligned** when it intentionally follows some
OpenClaw Shared Foundations concepts but has not demonstrated all minimum
compatibility requirements.

An aligned system:

- may cite the foundation concepts it adopts
- must identify missing, changed, or unassessed domains
- must not call itself Foundation-Compatible or Foundation-Compliant
- may be documentation-only, incomplete, or in early design

Alignment is descriptive, not a compatibility guarantee.

### 3.2 Foundation-Compatible

A system is **Foundation-Compatible** when it satisfies every mandatory
requirement in this profile for its declared scope, respects the canonical
precedence and exception models, preserves steward independence, and has
reviewable evidence for the validation checklist.

A compatible system:

- implements or maps all applicable minimum domain contracts
- may omit optional technologies such as Obsidian or MCP
- must govern those domains correctly when they are present
- may use documented, valid exceptions that do not invalidate mandatory
  protections
- must disclose material limitations and unassessed runtime behavior

Compatibility means the system can participate in the architecture without
breaking its minimum contracts. It does not imply official certification.

### 3.3 Foundation-Compliant

A system is **Foundation-Compliant** when it meets Foundation-Compatible
requirements and demonstrates complete, current, reviewable evidence for all
applicable required components, exceptions, recovery expectations, and
conformance claims.

A compliant system must:

- pass every applicable validation item without an unresolved critical gap
- maintain a requirement-to-evidence mapping
- document all exclusions as not applicable with justification
- have no expired, invalid, or undisclosed exception affecting the claim
- verify recovery, rollback, namespace isolation, and governed capability
  behavior at the level appropriate to its implementation
- identify the accountable owner of the conformance statement

Compliance is the strongest level defined in v0.1. Unless an official
certification process is established later, it remains a documented
self-assessment or independent review, not an OpenClaw certification.

### 3.4 Foundation-Experimental

A system is **Foundation-Experimental** when it tests proposed components,
future domains, alternative precedence, or incomplete contracts under bounded
conditions.

An experimental system:

- must identify the experiment, scope, expiry or review date, and rollback
- must not use production compatibility or compliance claims for the
  experimental scope
- must follow the Canonical Override and Exception Manifest when deviating
  from a mandatory rule
- must preserve consent, steward isolation, identity ownership, provenance,
  and audit boundaries
- may describe a non-experimental portion separately if that portion is
  independently assessed

Experimental status is not a shortcut around mandatory protections.

### 3.5 Non-Conformant

A system is **Non-Conformant** when it fails a mandatory requirement, uses an
invalid or expired exception, makes a prohibited claim, cannot produce
required evidence, or knowingly weakens a protected boundary.

Non-conformant systems may still use ideas from Shared Foundations where
permitted, but they must not claim compatibility or compliance. They may
return to another level after correcting the failure and completing a new
assessment.

## 4. Minimum Required Domains

The minimum profile distinguishes domains that must exist in every compatible
system from conditional domains that may be absent but become governed when
used.

### 4.1 Governance

**Status:** Mandatory for Foundation-Compatible and Foundation-Compliant.

Minimum requirements:

- a governance charter with purpose, authority, scope, and accountable owners
- explicit consent, boundary, data-classification, retention, deletion,
  change, and cross-steward rules
- capability policy and gating for any operational capabilities
- provenance and audit requirements
- adoption of the canonical precedence and exception models
- an escalation path and discoverable exception register

Governance must apply before memory mutation, capability execution, recovery
override, or cross-steward sharing.

### 4.2 Identity

**Status:** Mandatory for stewards; conditionally mandatory for non-steward
repositories that publish or package steward contracts.

Minimum steward requirements:

- canonical identity record with name, role, mission, scope, values, and
  boundaries
- separation of stable identity, current state, and critical facts
- identity provenance and controlled change
- a stable steward namespace
- ordered identity recovery anchors
- explicit steward ownership of identity content

A library or documentation repository need not instantiate a steward
personality, but it must preserve the identity contract and must not supply a
universal or copied identity as a compatibility requirement.

### 4.3 Memory

**Status:** Mandatory when a system stores or retrieves durable steward
knowledge. A system with no durable memory must declare memory disabled and
must not claim memory conformance.

Minimum requirements when applicable:

- a canonical memory record model
- provenance, timestamps, sensitivity, scope, owner, and stable identifiers
- namespace isolation
- exact retrieval or an equivalent deterministic lookup path
- bounded context assembly
- temporal preservation of superseded facts
- deletion, reset, retention, export, backup, and graceful-failure contracts
- no fabricated recall when records are unavailable

Semantic retrieval, graphs, consolidation, and shared memory are not required.

### 4.4 Recovery

**Status:** Mandatory for every Foundation-Compatible or
Foundation-Compliant system that preserves identity, state, memory,
configuration, or capabilities.

Minimum requirements:

- declared recovery triggers and states
- ordered governance, identity, state, and memory anchors as applicable
- backup or reconstruction contract
- rollback and migration-recovery expectations
- integrity and restoration verification
- recovery logging and escalation
- proof that recovery cannot silently cross steward boundaries
- a safe degraded mode when full integrity cannot be established

A stateless documentation artifact may mark operational recovery controls not
applicable, but it must preserve version history, change traceability, and a
documented restoration source.

### 4.5 MCP

**Status:** Optional. Conditionally mandatory when MCP is present or claimed.

Minimum requirements when applicable:

- server and tool inventory
- typed capability descriptions and risk classes
- steward, workspace, data, and tenant scope controls
- credential boundaries
- health and failure behavior
- capability policy, audit, and write safeguards
- read-only adoption before higher-risk writes where practical
- independent authorization for every steward

MCP availability, protocol compatibility, or server discovery never grants
permission.

### 4.6 Obsidian

**Status:** Optional. Conditionally mandatory when an Obsidian vault or
Obsidian projection is present or claimed.

Minimum requirements when applicable:

- a vault manifest and operating guide
- explicit raw-source and derived-knowledge separation
- provenance and steward scope
- a navigable index and change history
- schema or metadata conventions
- health expectations for stale, broken, orphaned, or contradictory content
- a declaration of whether any vault artifact is a scoped source of truth
- continued usability without optional semantic tooling

Obsidian is a knowledge surface, not a mandatory runtime memory engine.

### 4.7 Public Governance

**Status:** Mandatory for public repositories, public forks, distributed
packages, or public OpenClaw compatibility claims.

Minimum requirements:

- a clear project identity and conformance statement
- version and change history
- contribution and review expectations, even if contributions are not
  currently accepted
- a security-reporting contact or documented private reporting path
- public/private content boundaries
- exception and limitation disclosure appropriate to the audience
- no implied official status, certification, license grant, or endorsement

This profile does not choose or finalize a license, code of conduct, trademark
policy, or certification program. Their absence must be disclosed before
public distribution where relevant.

### 4.8 Steward-Specific Extensions

**Status:** Optional, but governed whenever present.

Minimum requirements:

- clear separation from canonical foundation requirements
- declared owner, namespace, scope, and version
- no weakening of mandatory protections
- documented precedence relationships
- explicit exception records for non-conforming deviations
- no hidden propagation to other stewards
- compatibility impact and rollback or removal path

Stricter local controls are conforming extensions and do not require
exceptions.

## 5. Mandatory Requirements

Every Foundation-Compatible or Foundation-Compliant steward must:

1. Identify the exact Shared Foundations version and assessment scope.
2. Use canonical glossary terms or clearly map local terms to them.
3. Preserve independent steward identity, namespace, private memory, and
   permissions.
4. Maintain a governance charter and named accountable roles.
5. Apply the Domain Precedence Model within the assessed scope.
6. Use the Canonical Override and Exception Manifest for deviations.
7. Separate canonical requirements, steward-owned content, and optional
   extensions.
8. Maintain provenance for material identity and durable memory records.
9. Classify protected data and govern access, sharing, retention, deletion,
   and audit.
10. Prevent one steward's authority from implicitly authorizing another.
11. Gate capabilities by explicit policy; technical availability is not
    permission.
12. Keep credentials and secret values outside prompts, memory, public
    documentation, and ordinary audit output.
13. Provide deterministic access to canonical records when durable memory is
    enabled.
14. Preserve historical truth rather than silently overwriting superseded
    facts.
15. Define recovery anchors, rollback, degraded behavior, verification, and
    cross-steward isolation.
16. Keep derived summaries, indexes, graph claims, and projections subordinate
    to their verified sources unless explicitly designated otherwise.
17. Maintain a discoverable record of active, expired, retired, and rejected
    exceptions appropriate to its governance scope.
18. Document optional or disabled domains and avoid claiming conformance for
    unassessed features.
19. Disclose material limitations, unresolved risks, and compatibility
    exceptions.
20. Retain reviewable evidence sufficient to complete the validation
    checklist.

Foundation-Compliant systems must additionally maintain a current
requirement-to-evidence mapping and objective verification for every
applicable requirement.

## 6. Optional Requirements

The following may be omitted without breaking compatibility when the omission
is documented and no related capability is claimed:

- Obsidian or any specific vault product
- MCP or any specific MCP server
- semantic or vector retrieval
- knowledge graphs
- temporal graph databases
- consolidation or sleep-time processing
- emotional or relational observations
- cross-steward shared knowledge
- multimodal memory
- dynamic MCP server registration
- remote MCP gateways
- shared server pools
- automated recovery
- dashboards and human approval queues
- one particular runtime, model provider, database, index, or storage engine
- ecosystem or Harbor mode participation
- public distribution
- steward-specific extensions

Omitting an optional component does not remove the obligation to govern
equivalent behavior implemented elsewhere.

## 7. Prohibited Claims

Users, stewards, forks, and downstream projects must not claim:

- Foundation-Compatible when any mandatory requirement is unmet or unassessed
- Foundation-Compliant without current evidence for every applicable
  requirement
- official certification, approval, endorsement, or stewardship unless an
  authorized process grants it
- compatibility with an unspecified Shared Foundations version
- that copied terminology, documentation, or repository ancestry proves
  conformance
- that MCP protocol support grants trusted or authorized capability access
- that use of Obsidian makes a vault a canonical source of truth
- that one steward inherits another steward's identity, private memory,
  credentials, consent, or permissions
- that an exception automatically applies to another steward, environment, or
  version
- that an expired, invalid, or undisclosed exception preserves compatibility
- that Foundation-Experimental is equivalent to compatibility or compliance
- that Foundation-Aligned guarantees interoperability
- that a stricter local rule is an official foundation requirement
- that a downstream precedence change is the canonical OpenClaw model
- that this profile supplies a final license, trademark permission, or public
  certification
- that private-memory disclosure is required to prove conformance

Materially misleading claims make the affected scope Non-Conformant until
corrected and reassessed.

## 8. Inheritance Requirements

Conformance inheritance is contract-based, not content-copy based.

Every compatible or compliant claim must remain traceable to:

- the assessed Shared Foundations version
- the applicable domain architecture documents
- the OpenClaw Foundations Glossary
- the Domain Precedence Model
- the Canonical Override and Exception Manifest
- local mappings, extensions, exclusions, and exceptions
- the assessment date, scope, owner, and evidence location

Inheritance must preserve:

- foundation-owned schemas, minimum protections, and validation expectations
- steward ownership of identity and private memory
- namespace and permission separation
- required provenance, deletion, recovery, and audit semantics
- explicit distinction between canonical requirements and local additions

Inheritance must not copy:

- another steward's identity content
- private or steward-specific memory
- credentials or capability grants
- local exception authority
- recovery secrets or private anchors
- public compatibility approval

A downstream system may replace implementations while retaining conceptual
and behavioral traceability. If it changes a mandatory contract, it must use a
valid exception, lower its conformance claim, or declare non-conformance.

## 9. Exception Handling

All deviations must follow
`docs/CANONICAL_OVERRIDE_AND_EXCEPTION_MANIFEST_v0.1.md`.

For conformance purposes:

- valid exceptions must identify their effect on compatibility or compliance
- exceptions are non-inheritable by default
- stricter conforming controls do not require an exception
- expired, suspended, invalid, or unapproved exceptions provide no authority
- permanent exceptions require recurring review
- experimental exceptions do not authorize production conformance claims
- invalid exceptions cannot preserve Foundation-Compatible or
  Foundation-Compliant status

A valid exception may preserve Foundation-Compatible status only when
compensating controls maintain all non-waivable protections and the limitation
is disclosed. Foundation-Compliant status requires complete exception
evidence and no unresolved critical impact.

## 10. Precedence Requirements

Every Foundation-Compatible or Foundation-Compliant system must adopt or
faithfully map
`docs/DOMAIN_PRECEDENCE_MODEL_v0.1.md`.

At minimum, the system must preserve:

1. governance authority over consent, safety, privacy, isolation, policy, and
   capability permission
2. steward identity authority over canonical identity content, subject to
   governance
3. temporary and restorative recovery authority
4. memory as evidence rather than permission
5. MCP result authority without MCP permission authority
6. Obsidian as a projection unless explicitly designated as a scoped source of
   truth
7. steward extensions below mandatory foundation protections
8. future domains below established domains until formally classified

Local terminology or implementation may differ, but conflict outcomes must be
equivalent. A different hierarchy requires a documented incompatibility or
approved exception and may prevent compatibility or compliance.

## 11. Public/Open Source Requirements

A public repository, fork, package, or compatibility statement must provide:

- a visible conformance level, version, scope, assessment date, and assessor
  type
- a concise list of implemented, disabled, not-applicable, experimental, and
  non-conformant domains
- material exceptions and limitations without exposing protected evidence
- clear separation between canonical OpenClaw documents and local changes
- versioned release or change information
- contribution status and review expectations
- a private security-reporting path or clear statement that one is pending
- a statement that private memory, identity anchors, and credentials are not
  required for review
- accurate attribution and notices under whatever licensing policy is later
  adopted
- no implication of official certification, endorsement, trademark
  permission, or finalized licensing where none exists

Before a final public-governance package exists, a project may state that
licensing, contribution, security, conduct, release, or naming policies are
pending. It must not represent their absence as approval or permission.

Public evidence should use synthetic, redacted, or structure-only fixtures.
Conformance review must not require publication of private steward state.

## 12. Validation Checklist

### Claim and Scope

- [ ] The claimed conformance level is one of the five canonical levels.
- [ ] The Shared Foundations version is explicit.
- [ ] The assessed steward, repository, deployment, environment, and domains
  are explicit.
- [ ] The assessment date, owner, and assessor type are recorded.
- [ ] Limitations and unassessed behavior are disclosed.

### Governance

- [ ] A governance charter and accountable roles exist.
- [ ] Consent, boundaries, data classification, retention, deletion, change,
  audit, and cross-steward rules are documented.
- [ ] Capability policy applies before tool execution.
- [ ] An escalation path and exception register exist.
- [ ] No mandatory protection is bypassed by an optional component.

### Identity and Independence

- [ ] The steward has a canonical identity spine and stable namespace.
- [ ] Stable identity is separated from current state and critical facts.
- [ ] Identity changes have provenance and approval.
- [ ] Steward-owned identity and private memory remain outside shared
  foundation packages.
- [ ] One steward cannot authorize or contaminate another.

### Memory

- [ ] Memory is declared enabled, disabled, or not applicable.
- [ ] Enabled durable memory has scope, owner, provenance, timestamps,
  sensitivity, and stable identifiers.
- [ ] Namespace isolation and deterministic canonical lookup are validated.
- [ ] Temporal truth, bounded context, deletion, reset, retention, export, and
  graceful failure are addressed.
- [ ] Semantic, graph, or derived records do not silently override sources.

### Recovery

- [ ] Recovery triggers, states, anchors, escalation, and degraded behavior
  are defined.
- [ ] Backup or reconstruction, rollback, and verification are documented.
- [ ] Recovery does not restore revoked permissions.
- [ ] Recovery cannot silently modify another steward.
- [ ] Applicable recovery scenarios have reviewable evidence.

### MCP and Obsidian

- [ ] MCP is absent or has registry, scope, credential, policy, audit, write,
  health, and failure controls.
- [ ] MCP authorization is independent for each steward.
- [ ] Obsidian is absent or has a manifest, operating guide, provenance,
  raw/derived separation, indexing, and health expectations.
- [ ] Obsidian source-of-truth status is explicit.
- [ ] Optional tooling can fail without fabricating results or destroying
  canonical records.

### Extensions, Exceptions, and Precedence

- [ ] Canonical requirements and steward-specific extensions are distinct.
- [ ] The Domain Precedence Model is adopted or faithfully mapped.
- [ ] Every deviation has a valid exception or is declared non-conformant.
- [ ] Exceptions are scoped, current, approved, auditable, and non-inheriting
  by default.
- [ ] No invalid exception affects the claim.

### Public Governance

- [ ] Public-facing claims identify level, version, scope, date, and evidence
  status.
- [ ] Official certification or endorsement is not implied.
- [ ] Canonical content and downstream changes are distinguishable.
- [ ] Contribution, security reporting, versioning, and pending policy status
  are visible where applicable.
- [ ] Public evidence contains no credentials or unnecessary private content.

### Decision

- [ ] Foundation-Compatible: every mandatory applicable item passes or has a
  valid disclosed exception preserving non-waivable protections.
- [ ] Foundation-Compliant: every applicable item passes with current,
  complete, mapped evidence and no unresolved critical exception.
- [ ] Foundation-Experimental: experimental scope, expiry, rollback, and claim
  limitations are explicit.
- [ ] Any failed mandatory item lowers the claim to Foundation-Aligned,
  Foundation-Experimental, or Non-Conformant as appropriate.

## 13. Examples

### Example 1: Documentation project using the concepts

A repository cites the identity and memory architectures but has no governance
mapping or validation evidence. It may claim Foundation-Aligned, not
Foundation-Compatible.

### Example 2: Steward without Obsidian

A steward meets mandatory governance, identity, memory, and recovery
requirements but uses no Obsidian vault. It may be Foundation-Compatible if it
declares Obsidian disabled and makes no Obsidian conformance claim.

### Example 3: Steward without MCP

A steward has no external tool protocol. MCP is documented as absent. Its
compatibility claim remains valid because MCP is optional.

### Example 4: MCP-enabled steward with broad shared credentials

A steward meets memory requirements but shares unrestricted credentials with
another steward. It is Non-Conformant because capability authorization and
isolation are mandatory when MCP is present.

### Example 5: Memory-free steward

A steward intentionally operates without durable memory. It declares memory
disabled, preserves identity and recovery for its remaining state, and avoids
memory-conformance claims. It may still be Foundation-Compatible within that
declared scope.

### Example 6: Complete self-assessment

A steward passes all applicable checklist items and maintains current evidence
for namespace isolation, recovery, exceptions, and capability governance. It
may self-describe as Foundation-Compliant v0.1, explicitly stating that the
claim is self-assessed and not officially certified.

### Example 7: Experimental graph retrieval

A compatible steward tests a temporal knowledge graph under an approved
experimental exception. The base system may retain its compatible claim, but
the graph feature is Foundation-Experimental until separately validated.

### Example 8: Expired compatibility exception

A legacy adapter depends on an expired schema exception. The affected scope
can no longer claim Foundation-Compatible until the adapter migrates or a new
exception is approved.

### Example 9: Public fork with clear deviations

A fork changes the precedence model and labels the change prominently. It may
claim Foundation-Aligned or Foundation-Experimental, but not compatibility
with the canonical v0.1 profile unless an approved exception preserves
equivalent outcomes.

### Example 10: Obsidian vault as an undeclared authority

A system lets generated vault summaries overwrite canonical memory without a
manifest designation. It is Non-Conformant because derived projection is
silently controlling source truth.

### Example 11: Stricter privacy controls

A steward disables shared memory and shortens retention. These are stricter
conforming extensions, so no exception is required and compatibility is
preserved.

### Example 12: Public repository with pending license

A public architecture fork states its conformance scope and clearly discloses
that licensing policy is unresolved. This profile does not grant permission;
the project may make only claims supported by its actual legal and governance
status.

### Example 13: Copied steward identity

A downstream package includes another steward's identity spine as its default
identity. It is Non-Conformant because inheritance is contract-based and may
not copy steward-owned identity.

### Example 14: Recovery works but lacks evidence

A maintainer believes rollback works, but no current verification evidence
exists. The affected scope cannot claim Foundation-Compatible or
Foundation-Compliant until recovery is verified. It may claim
Foundation-Aligned while disclosing the evidence gap.

### Example 15: Library preserving the identity contract

A reusable library does not instantiate a steward. It preserves namespace,
identity ownership, precedence, and recovery interfaces and clearly scopes its
claim to the library contract. It may be Foundation-Compatible without having
a personality of its own.

### Example 16: Misleading official claim

A downstream project calls itself “OpenClaw Certified” without an authorized
certification process. The prohibited claim makes the affected public scope
Non-Conformant until corrected and reassessed.

## 14. Future Expansion

New conformance levels or requirements may be added only through versioned
foundation governance.

A proposal must define:

- the need not addressed by existing levels
- exact mandatory and optional requirements
- affected domains and precedence relationships
- evidence and validation criteria
- exception and inheritance behavior
- migration and backward-compatibility effects
- public claim language
- deprecation and retirement rules
- at least two practical examples

New requirements should begin as optional, experimental, or announced future
requirements unless an urgent non-waivable protection is necessary. Promotion
to mandatory status requires a version change, impact review, migration
guidance, and a reasonable transition policy.

Future versions may add:

- official conformance statement templates
- canonical requirement identifiers
- evidence and traceability schemas
- compatibility subprofiles for standalone, ecosystem, and Harbor modes
- domain-specific validation suites
- risk tiers and critical-failure definitions
- independent-review and certification governance
- deprecation windows
- public naming and mark-usage policy

## 15. Summary Table

### Conformance Levels

| Level | Meaning | Minimum evidence | Permitted claim |
|---|---|---|---|
| Foundation-Aligned | Uses some foundation concepts but has gaps or incomplete assessment | Adopted concepts and disclosed gaps | Alignment only |
| Foundation-Compatible | Meets every mandatory applicable requirement for a declared scope | Completed checklist and reviewable supporting evidence | Compatibility, not certification |
| Foundation-Compliant | Compatible with complete current evidence for every applicable requirement | Requirement-to-evidence mapping and objective verification | Compliance, with assessor type disclosed |
| Foundation-Experimental | Tests incomplete or proposed behavior in bounded scope | Experiment record, safeguards, expiry, and rollback | Experimental status only for affected scope |
| Non-Conformant | Fails mandatory rules, evidence, exception validity, or claim integrity | Failure or unresolved gap record | No compatibility or compliance claim |

### Domain Applicability

| Domain | Compatible/Compliant applicability | Omission rule |
|---|---|---|
| Governance | Mandatory | Cannot be omitted |
| Identity | Mandatory for stewards; contract-preserving for non-steward artifacts | Non-steward scope must be explicit |
| Memory | Mandatory when durable memory exists or is claimed | May be disabled and declared |
| Recovery | Mandatory for preserved identity, state, memory, configuration, or capabilities | Stateless artifacts require restoration traceability |
| MCP | Conditional | May be absent; requirements activate when present |
| Obsidian | Conditional | May be absent; requirements activate when present |
| Public Governance | Conditional | Activates for public distribution or claims |
| Steward-Specific Extensions | Conditional | May be absent; governed when present |

### Claim Rule

The conformance level is determined by the weakest material result within the
declared scope. Optional technology may be absent, but mandatory protections,
honest claims, precedence, valid exception handling, steward independence, and
reviewable evidence may not be omitted.
