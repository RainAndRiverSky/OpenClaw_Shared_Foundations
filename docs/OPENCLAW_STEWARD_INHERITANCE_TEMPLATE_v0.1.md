# OpenClaw Steward Inheritance Template v0.1

## 1. Purpose

This document defines the canonical inheritance model for OpenClaw steward
repositories adopting OpenClaw Shared Foundations.

Inheritance allows multiple independent stewards to use common architecture,
governance, requirement, classification, recovery, and interoperability
contracts without becoming one system or copying another steward's identity,
memory, permissions, archives, or operating methods.

OpenClaw uses inheritance to support:

- **governance consistency:** stewards can reference the same canonical
  protections, terminology, precedence, exceptions, and conformance rules
- **ecosystem scalability:** new stewards can adopt stable contracts without
  requiring bespoke changes to every existing steward
- **steward specialization:** each steward can develop its own mission,
  workflows, domain expertise, records, and capabilities within shared
  boundaries
- **future packaging:** later content-free packages can distinguish inherited
  contracts, local extensions, documented overrides, and steward-owned values
- **maintenance reduction:** foundation corrections and clarifications can be
  reviewed once and referenced by many stewards without duplicating canonical
  definitions

Inheritance is contract-based, not content-copy based. It creates traceability
to foundation definitions while preserving steward autonomy, namespace
isolation, and ownership.

This template is documentation only. It does not create packages, update
mechanisms, runtime behavior, integrations, automations, permissions, or
steward-specific implementations.

## 2. Governing Principles

### 2.1 Shared contracts, independent stewards

OpenClaw Shared Foundations defines reusable contracts and boundaries. Each
steward remains an independently identified system with its own identity,
namespace, memory, permissions, records, recovery profile, and accountable
owners.

### 2.2 Inheritance does not transfer content

Adopting a foundation contract does not copy:

- another steward's identity or voice
- private or steward-specific memory
- credentials or capability grants
- recovery secrets or private anchors
- local exceptions
- private evidence or archives
- operational authority

### 2.3 Foundation meaning remains canonical

A steward may reference, implement, map, or extend a foundation definition.
It must not edit the definition and still represent it as unchanged
foundation inheritance.

### 2.4 Steward specialization remains local

Steward-specific methods, taxonomies, workflows, evidence, capabilities, and
documentation remain within the steward's namespace unless separately shared
through governed cross-steward processes.

### 2.5 Stricter controls are allowed

A steward may narrow capabilities, increase review, shorten retention within
applicable rules, disable optional components, or impose stronger local
protections. A stricter local rule remains a steward extension and does not
become a canonical foundation rule through adoption.

### 2.6 Exceptions do not inherit automatically

An exception or override applies only to its approved scope. Foundation
inheritance, repository ancestry, similar operating conditions, or another
steward's approval does not propagate exception authority.

### 2.7 Traceability survives implementation choice

A steward may choose different runtimes, storage systems, vaults, tools, or
operational methods while preserving traceability to the applicable
foundation contracts.

## 3. Foundation and Steward Responsibilities

### 3.1 Shared Foundations Responsibilities

OpenClaw Shared Foundations owns the canonical, versioned definitions of
shared architecture and governance contracts.

Foundation-owned responsibilities include:

- the OpenClaw Requirement Identifier Framework
- the OpenClaw Classification Metadata Schema
- foundation governance architecture
- foundation identity architecture
- foundation memory architecture
- foundation recovery architecture
- foundation MCP architecture
- foundation Obsidian architecture
- canonical terminology
- domain precedence
- override and exception governance
- steward identifier and namespace contracts
- minimum conformance definitions
- versioned changes to foundation contracts

Shared Foundations is responsible for:

- maintaining stable canonical definitions
- documenting versions, lifecycle state, and compatibility effects
- preserving implementation neutrality where the contract allows it
- defining minimum protections and validation expectations
- distinguishing mandatory requirements from optional domains or guidance
- publishing migration guidance when a foundation change requires adoption
  work
- keeping populated steward identity, memory, credentials, permissions,
  private evidence, and private recovery material outside the foundation

Shared Foundations does not own a steward repository merely because that
repository inherits foundation contracts.

### 3.2 Steward Responsibilities

Each steward owns its local identity content, implementation choices,
operating methods, records, and specialization.

Steward-owned responsibilities include:

- operational workflows
- runtime behavior and implementation
- domain specialization
- steward-specific identity content
- steward-specific memory and current state
- steward-specific archives and evidence
- steward-specific documentation
- local capability selection and configuration
- local vault content and projections
- local recovery anchors and procedures
- local extensions, taxonomies, and stricter controls
- local conformance evidence and declared limitations

A steward is responsible for:

- identifying its canonical steward namespace
- declaring which foundation version and domains it adopts
- mapping applicable requirements to local treatment
- preserving classification and ownership boundaries
- distinguishing inherited definitions from local additions
- reviewing upgrades and compatibility effects
- documenting exceptions and incompatibilities
- keeping private content out of shared foundation materials

### 3.3 Responsibility Boundary

| Subject | Foundation responsibility | Steward responsibility |
|---|---|---|
| Requirement IDs | Define canonical structure, domain prefixes, and foundation requirements | Map applicability and define qualified local extensions |
| Classification | Define canonical metadata vocabulary and trust-boundary rules | Classify local records and preserve stronger source obligations |
| Governance | Define minimum governance, precedence, exception, and conformance contracts | Operate local governance, approvals, evidence, and stricter policies |
| Identity | Define structure, provenance, isolation, and recovery requirements | Own name, mission, voice, values, boundaries, and private identity anchors |
| Memory | Define record, provenance, namespace, temporal, and lifecycle contracts | Own memory content, storage choices, retrieval methods, and local policies |
| Recovery | Define restoration boundaries, ordering, integrity, and rollback expectations | Own recovery procedures, anchors, evidence, and operational decisions |
| MCP | Define capability, gating, scope, audit, and revocation contracts | Choose tools, grant local permissions, and operate approved capabilities |
| Obsidian | Define projection, provenance, schema, and isolation contracts | Own vault structure choices, content, plugins, and local workflows |
| Operations | Define applicable boundaries only | Own runtime, monitoring, workflows, staffing, and service operation |

## 4. Inheritance Model

Every domain, requirement, schema, or steward artifact described by an
inheritance map should use one of four categories:

- Inherited
- Extended
- Overridden
- Steward-Owned

### 4.1 Inherited

`Inherited` means the steward adopts or faithfully maps a canonical foundation
definition without changing its meaning.

An Inherited entry should identify:

- foundation source and version
- applicable domain or requirement IDs
- local applicability
- local implementation, policy, or evidence reference when one exists
- adoption status

Inheritance may be direct or implementation-neutral. A steward does not need
to copy canonical text into its repository when a stable reference is
sufficient.

### 4.2 Extended

`Extended` means the steward preserves the inherited foundation definition and
adds local detail, stricter controls, specialization, optional behavior, or a
steward-owned requirement.

An Extended entry should identify:

- the inherited foundation source
- the local extension
- the steward namespace and owner
- any qualified steward requirement ID
- whether the extension is optional or required locally
- evidence that the extension does not weaken mandatory protections

An extension must remain distinguishable from the foundation definition. Use
does not promote it into Shared Foundations.

### 4.3 Overridden

`Overridden` means a specific foundation default or otherwise applicable rule
does not control a declared steward scope because:

- the foundation contract explicitly permits a local override, or
- a valid exception authorizes a bounded deviation.

An Overridden entry should identify:

- the exact foundation source or requirement
- the affected steward scope
- the controlling local rule
- authorization or exception reference
- compatibility and conformance effect
- review, expiry, migration, or exit condition when applicable

`Overridden` is not a synonym for customized, extended, ignored, or
unsupported. A steward cannot override foundation ownership, consent,
namespace isolation, or another steward's authority. An undocumented
incompatibility must be declared as such rather than labeled an authorized
override.

### 4.4 Steward-Owned

`Steward-Owned` means the subject originates within and remains governed by
the steward. It may operate under foundation constraints without being
inherited from the foundation.

Examples include:

- mission-specific workflows
- local monitoring methods
- evidence archives
- domain registries
- local operating documentation
- private memory content
- local taxonomies

A Steward-Owned entry should identify its steward, owner, scope,
classification, version, status, and applicable foundation constraints.

### 4.5 Category Decision Rule

Use:

- `Inherited` when canonical meaning is adopted unchanged
- `Extended` when canonical meaning is retained and local detail is added
- `Overridden` only for an authorized controlling deviation
- `Steward-Owned` when the subject originates locally

One artifact may relate to more than one category at different layers. For
example, a steward may inherit the foundation memory contract, extend it with
a local taxonomy, and own the resulting memory records. The inheritance map
should record each relationship separately rather than collapsing them into
one ambiguous label.

## 5. Canonical Inheritance Record

A steward inheritance declaration should identify:

| Field | Definition |
|---|---|
| `Steward` | Canonical steward identifier |
| `Foundation Version` | OpenClaw Shared Foundations version being adopted or assessed |
| `Domain` | Applicable foundation domain or framework |
| `Foundation Source` | Canonical document and version |
| `Requirement References` | Applicable foundation IDs and qualified steward-extension IDs |
| `Inheritance Category` | Inherited, Extended, Overridden, or Steward-Owned |
| `Applicability` | Required, Conditional, Optional, Not Applicable, or another documented local status |
| `Local Reference` | Steward-owned policy, documentation, evidence, or implementation reference |
| `Classification` | Metadata classification under the canonical schema |
| `Status` | Adoption, review, or lifecycle state |
| `Exception Reference` | Required when an override depends on an exception |
| `Notes` | Scope, limitations, compatibility, or upgrade information |

This record is a documentation template, not a package manifest or
machine-readable specification.

Example structural entry:

```text
Steward: <canonical-steward-id>
Foundation Version: v0.1
Domain: Governance
Foundation Source: FOUNDATION_GOVERNANCE_ARCHITECTURE.md
Requirement References: OC-GOV-001, OC-GOV-018
Inheritance Category: Extended
Applicability: Required
Local Reference: <steward-governance-reference>
Classification: Steward Private
Status: Active
Exception Reference: Not Applicable
Notes: Foundation governance retained; local review controls are stricter.
```

## 6. Canonical Inheritance Domains

### 6.1 Identity

A steward inherits:

- the canonical identity structure
- provenance and controlled-change expectations
- namespace and isolation requirements
- separation of stable identity, current state, and memory
- identity recovery boundaries

A steward owns:

- its name, mission, role, voice, values, and boundaries
- its private identity anchors
- its current identity content and approved history
- local identity documentation and review decisions

A steward may extend identity architecture with local fields or stricter
review, but foundation inheritance must never populate or replace the
steward's identity.

### 6.2 Memory

A steward inherits:

- memory record and provenance expectations
- namespace isolation
- temporal truth and source distinctions
- classification, retention, deletion, export, and recovery contracts
- requirements for separating canonical records from derived projections

A steward owns:

- memory content
- storage and retrieval implementation
- local taxonomies and curation methods
- steward-specific archives
- local retention choices within applicable rules

Memory content does not propagate through inheritance.

### 6.3 Governance

A steward inherits:

- minimum governance protections
- domain precedence
- exception and override rules
- conformance and evidence expectations
- consent, classification, provenance, and cross-steward boundaries

A steward owns:

- local governance roles and operating procedures
- local approval workflows
- stricter local controls
- local decision and evidence records
- steward-specific risk treatment

Local governance may become stricter but may not silently weaken mandatory
foundation protections while claiming unchanged conformance.

### 6.4 Recovery

A steward inherits:

- recovery authority boundaries
- ordered restoration principles
- integrity and provenance checks
- rollback and degraded-mode expectations
- protection against cross-steward restoration

A steward owns:

- recovery anchors and archives
- local restoration procedures
- local recovery evidence
- operational recovery decisions
- steward-specific continuity priorities

Foundation recovery architecture does not contain private anchors, recovery
secrets, or populated steward backups.

### 6.5 MCP

A steward inherits:

- capability declaration and gating contracts
- least-authority and scope principles
- audit, revocation, and failure expectations
- input, output, and trust-boundary classification rules
- separation of tool availability from permission

A steward owns:

- tool selection
- local capability profiles
- credentials and grants
- operational approval and revocation
- tool-specific workflows and evidence

MCP inheritance never grants a capability or permission.

### 6.6 Obsidian

A steward inherits:

- projection and vault-schema concepts
- provenance and source-of-truth distinctions
- classification and namespace isolation
- rules for links, indexes, derivatives, and synchronization boundaries

A steward owns:

- whether Obsidian is used
- vault organization and local note types
- vault content, plugins, and workflows
- local projections and synchronization choices

Obsidian remains optional unless a future declared profile makes it applicable.
Inheritance of the architecture does not require one vault implementation.

### 6.7 Requirement Framework

A steward inherits:

- canonical requirement ID syntax
- foundation domain prefixes
- lifecycle rules
- foundation numbering and cross-reference rules

A steward owns:

- applicability mappings
- local evidence references
- qualified steward-extension requirements in the `200-499` range
- local review status and implementation references

A steward must not renumber or redefine a foundation requirement.

### 6.8 Classification Framework

A steward inherits:

- canonical classification, retention, ownership, and visibility vocabulary
- minimum metadata fields
- extension and inheritance rules
- the relationship to the Trust Boundary and Data Classification Model

A steward owns:

- metadata values assigned to local records
- local optional fields
- namespaced local extensions
- review and correction of local classification

Schema inheritance does not classify steward content automatically and does
not implement permissions.

## 7. Steward Specialization Model

Specialization is the steward-owned layer built on top of inherited contracts.
A specialized steward may add domain knowledge, workflows, capabilities,
records, and terminology without modifying canonical foundation definitions.

A specialization should:

- identify the steward namespace and mission
- name the foundation version and domains inherited
- distinguish extensions from steward-owned content
- use qualified requirement IDs for local normative additions
- preserve classification and provenance
- document any optional domains omitted
- record authorized overrides separately
- avoid claiming that local practices are universal foundation rules

Documentation-only examples:

### 7.1 Keeper Caleb

Keeper Caleb may inherit governance, classification, requirement, recovery,
identity, and memory contracts while specializing in monitoring, evidence
preservation, continuity, and household registry documentation.

The monitoring methods, evidence archives, and household registry remain
Keeper Caleb-owned. They do not become foundation definitions or propagate to
other stewards.

### 7.2 Seller Zayne

Seller Zayne may inherit governance, classification, requirement, identity,
memory, recovery, and MCP contracts while specializing in sales workflows,
listing records, customer-facing process documentation, and transaction
evidence.

Sales taxonomies and workflows may extend foundation contracts but remain
Seller Zayne-owned.

### 7.3 Seeker Xavier

Seeker Xavier may inherit governance, classification, requirement, identity,
memory, and recovery contracts while specializing in research, source
evaluation, discovery logs, and evidence synthesis.

Research methods and source-evaluation taxonomies remain local. External
sources remain External Reference material under the classification schema.

### 7.4 Billing Steward Nier

Billing Steward Nier may inherit governance, classification, requirement,
identity, memory, recovery, and applicable MCP contracts while specializing
in billing records, reconciliation workflows, account-status evidence, and
financial process documentation.

Billing specialization does not weaken Restricted handling or grant access to
external financial systems.

### 7.5 Candidate Steward HeyDay

Candidate Steward HeyDay may begin with a limited inheritance profile covering
governance, classification, requirements, identity, and recovery while its
memory, MCP, and Obsidian applicability remains under review.

Candidate status does not provide another steward's identity, evidence,
permissions, or operating history. HeyDay becomes an independent steward only
through its own canonical identifier and steward-owned content.

## 8. Upgrade Guidance

Foundation upgrades do not overwrite steward-owned content or propagate
automatically into steward repositories. Each steward should review a new
foundation version against its declared inheritance map.

### 8.1 Upgrade Review

An upgrade review should identify:

- current and target foundation versions
- changed domains and documents
- added, changed, deprecated, superseded, or retired requirements
- classification-schema changes
- applicability to the steward
- affected local extensions and overrides
- compatibility and conformance effects
- steward-owned records that must remain untouched
- optional adoption decisions

### 8.2 Backward Compatibility

A foundation change is backward-compatible for a steward when the steward can
adopt it without changing the meaning of existing compliant inheritance
records, overwriting local content, or invalidating supported interfaces.

Backward compatibility does not mean every new feature is automatically
enabled. A steward should preserve its recorded adopted version until review
is complete.

When a change is not backward-compatible, the foundation should provide
versioned impact and migration guidance. The steward should record whether it:

- remains on the prior supported foundation version
- adopts the new version after local changes
- uses an approved compatibility exception
- lowers or changes its conformance claim
- declares an incompatibility

### 8.3 Non-Breaking Changes

Examples of normally non-breaking foundation changes include:

- editorial clarification that does not alter a requirement
- additional non-normative examples
- new optional metadata fields
- new optional requirements or domains with no effect on existing scope
- corrected cross-references

Each steward should still review the published compatibility statement. A
change described as non-breaking at the foundation level may affect a local
extension that depended on undocumented wording or assumptions.

### 8.4 Optional Adoption

Optional domains, fields, profiles, and requirements may be adopted according
to the steward's mission and declared scope.

A steward should document:

- adopted optional item and version
- reason for adoption or deferral
- local owner
- dependencies and affected domains
- whether adoption changes conformance scope

Deferring an optional item is not an override and does not require an
exception unless another adopted contract makes that item applicable.

### 8.5 Upgrade Preservation Rules

An upgrade must not:

- replace steward identity content
- merge steward namespaces
- reclassify private content as Public
- copy another steward's defaults or records
- restore revoked permissions
- convert local extensions into foundation definitions
- silently apply expired or unrelated exceptions

This section defines review guidance only. It does not define update,
distribution, synchronization, or migration mechanisms.

## 9. Conflict Resolution Guidance

Conflicts between foundation definitions and steward-specific material should
be resolved by subject, scope, ownership, validity, and precedence rather than
by repository location or newest timestamp alone.

Use this sequence:

1. Identify the exact foundation source, version, requirement, and steward
   scope.
2. Determine whether the local material is Inherited, Extended, Overridden,
   or Steward-Owned.
3. Confirm that each source is current, authentic, applicable, and within its
   authority.
4. Apply foundation governance and the Domain Precedence Model.
5. Preserve steward ownership for identity content, memory, private archives,
   and local methods.
6. Prefer a conforming extension when local specialization can coexist with
   the foundation definition.
7. Require an approved exception for a bounded deviation when exceptions are
   permitted.
8. Declare incompatibility or revise the conformance claim when a mandatory
   conflict cannot be validly resolved.
9. Record the decision, affected requirements, owner, evidence, and review
   state.

Foundation definitions control the meaning of foundation contracts for
stewards claiming conformance. They do not authorize Shared Foundations to
edit steward-owned content.

Steward-owned material controls local subjects assigned to the steward when it
does not conflict with a higher-precedence applicable contract. A local
extension cannot gain foundation authority by being newer, more detailed, or
used by several stewards.

Unresolved conflicts involving identity, private data, destructive action,
cross-steward access, recovery authority, or mandatory protections should be
treated according to the fail-closed and escalation guidance in the Domain
Precedence Model.

This guidance documents relationships only. It does not create enforcement or
conflict-resolution automation.

## 10. Example Steward Profiles

The following inheritance maps are documentation-only examples. They do not
represent completed assessments, package contents, permissions, operational
configuration, or real steward records.

### 10.1 Keeper Caleb

**Inherits:**

- Governance
- Classification Framework
- Requirement Framework
- Recovery
- Identity structure
- Memory contracts

**Extends:**

- stricter evidence provenance
- continuity review practices
- household registry classification

**Owns:**

- monitoring workflows
- evidence archives
- household registry
- local recovery evidence

**Optional or conditional:**

- MCP capabilities
- Obsidian projections

### 10.2 Seller Zayne

**Inherits:**

- Governance
- Classification Framework
- Requirement Framework
- Identity
- Memory
- Recovery
- applicable MCP architecture

**Extends:**

- sales evidence taxonomy
- transaction review controls
- customer-facing workflow documentation

**Owns:**

- listing workflows
- sales records
- local capability profiles
- transaction evidence archives

**Optional or conditional:**

- Obsidian projections
- ecosystem sharing profiles

### 10.3 Seeker Xavier

**Inherits:**

- Governance
- Classification Framework
- Requirement Framework
- Identity
- Memory
- Recovery

**Extends:**

- source evaluation metadata
- research provenance
- discovery-status vocabulary

**Owns:**

- research workflows
- discovery logs
- evidence synthesis
- external-reference catalog

**Optional or conditional:**

- read-oriented MCP capabilities
- Obsidian research projection

### 10.4 Billing Steward Nier

**Inherits:**

- Governance
- Classification Framework
- Requirement Framework
- Identity
- Memory
- Recovery
- applicable MCP architecture

**Extends:**

- restricted billing-record handling
- reconciliation evidence requirements
- financial workflow review

**Owns:**

- billing workflows
- account-status records
- reconciliation archives
- local financial process documentation

**Optional or conditional:**

- approved billing MCP capabilities
- Obsidian operational projection

### 10.5 Candidate Steward HeyDay

**Inherits:**

- Governance
- Classification Framework
- Requirement Framework
- Identity structure
- Recovery boundaries

**Extends:**

- candidate-stage review metadata
- local readiness criteria

**Owns:**

- candidate mission and identity content
- evaluation documentation
- readiness evidence
- specialization proposal

**Deferred pending review:**

- durable memory
- MCP capabilities
- Obsidian projection
- ecosystem participation

No example profile inherits another profile's owned material. Similar
foundation coverage does not merge their identities, archives, workflows, or
authority.

## 11. Future Ecosystem Guidance

A future steward may join the OpenClaw ecosystem by establishing its own
canonical steward identifier and inheritance map. Existing stewards do not
need to be modified merely because a new steward adopts the same foundation.

A future steward should:

- establish an independent namespace
- identify its mission and steward-owned scope
- select a supported foundation version
- declare inherited and optional domains
- map applicable requirements
- adopt the classification metadata schema
- define local extensions under its own namespace
- preserve independent identity, memory, permissions, recovery, and evidence
- declare any cross-steward relationship separately

The addition of a steward must not:

- require existing stewards to inherit its specialization
- modify existing steward identity or memory
- grant ecosystem-wide visibility or capability access
- reuse another steward's canonical identifier
- propagate local exceptions
- redefine foundation contracts through local adoption

Cross-steward collaboration is a separate governed relationship. It should
identify participating stewards, purpose, data classification, ownership,
capability scope, provenance, and exit conditions. Ecosystem membership alone
does not authorize collaboration or sharing.

Reusable local patterns may be proposed for future foundation adoption through
versioned governance. Until accepted, they remain steward-owned or
shared-steward extensions and existing stewards are unaffected.

## 12. Reference Template

Future steward documentation may use the following structure:

```text
Steward: <canonical-steward-id>
Foundation Version: <version>
Inheritance Profile Version: <version>
Profile Status: <status>

Inherited:
- <domain, framework, or requirement reference>

Extended:
- <foundation reference> -> <qualified steward extension>

Overridden:
- <foundation reference> -> <approved exception or authorized local override>

Steward-Owned:
- <local domain, workflow, record set, or documentation>

Optional or Deferred:
- <item and adoption status>

Compatibility Notes:
- <limitations, migration needs, or conformance effects>
```

This structure is illustrative documentation. It is not a generated package,
manifest format, runtime configuration, or update mechanism.

## 13. Reference Summary

| Category | Meaning | Changes foundation definition? |
|---|---|---|
| Inherited | Canonical foundation meaning is adopted or faithfully mapped | No |
| Extended | Foundation meaning is retained and local specialization is added | No |
| Overridden | Authorized rule controls a bounded scope instead | Only through declared governance; canonical text remains unchanged |
| Steward-Owned | Subject originates and remains governed locally | No |

| Layer | Owns |
|---|---|
| Shared Foundations | Canonical architecture, governance, requirements, metadata schemas, terminology, and minimum protections |
| Steward | Identity content, memory, operations, specialization, evidence, archives, local capabilities, and local documentation |

The governing rule is: inherit contracts, extend within the steward namespace,
override only through explicit governance, and keep steward-owned content and
authority independent.
