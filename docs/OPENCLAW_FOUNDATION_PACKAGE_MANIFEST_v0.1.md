# OpenClaw Foundation Package Manifest v0.1

## 1. Purpose

This document defines the canonical contents, scope, and boundaries of the
OpenClaw Shared Foundations package.

The Foundation Package is the logical collection of versioned,
implementation-neutral architecture, governance, schema, requirement,
classification, conformance, and inheritance documents that stewards may
reference or adopt. It defines shared contracts and structural defaults
without supplying populated steward content or runtime behavior.

OpenClaw Shared Foundations exists separately from steward repositories
because the foundation and each steward own different subjects:

- the foundation owns canonical contracts, terminology, minimum protections,
  and cross-domain rules
- each steward owns its identity content, memory, permissions, operations,
  evidence, specialization, and local documentation

Keeping these layers separate supports:

- **portability:** foundation contracts can be used across different
  repositories, runtimes, storage systems, model providers, and knowledge
  tools
- **consistency:** stewards can reference the same architecture, requirement,
  classification, precedence, and inheritance definitions
- **governance:** shared protections and change boundaries remain reviewable
  without acquiring control of steward-owned state
- **packaging:** future content-free packages can be described consistently
  before any archive, installer, registry, or distribution mechanism exists
- **ecosystem growth:** new stewards and future domains can adopt shared
  contracts without merging existing steward identities or repositories

This manifest defines a conceptual package composition. It does not generate a
package, prescribe a file archive, define a distribution channel, implement a
runtime, create release assets, or modify steward repositories.

## 2. Package Principles

### 2.1 Contracts, not populated state

The Foundation Package contains reusable definitions and structural guidance.
It does not contain live or populated steward records.

### 2.2 Implementation neutrality

Foundation contracts describe what must be represented, governed, protected,
or validated. They do not require a particular runtime, database, vault,
provider, MCP server, deployment platform, or automation system unless a
future version explicitly and justifiably defines such a dependency.

### 2.3 Steward independence

Receiving, referencing, or inheriting the Foundation Package does not transfer
identity, memory, credentials, permissions, exceptions, recovery authority, or
ownership between stewards.

### 2.4 Content classification

Foundation Package content must be appropriate for its declared
classification and package scope. Public distribution, if later authorized,
requires separate publication governance. Inclusion in this logical manifest
does not itself classify a document as Public.

### 2.5 Versioned traceability

Every canonical package component must be identifiable by source, title, and
version or version context. Steward inheritance must identify the Foundation
version adopted or assessed.

### 2.6 Optional systems remain optional

Inclusion of an architecture domain in the Foundation Package does not make
its technology mandatory for every steward. MCP and Obsidian remain
conditional where the applicable foundation profile permits their omission.

### 2.7 No authority through package presence

The presence of a schema, example, capability description, or governance
document in the package does not grant permission, establish consent, enable a
tool, prove conformance, or create runtime enforcement.

## 3. Foundation Package Scope

The Foundation Package may include the following categories of canonical
material.

### 3.1 Domain Architectures

The six initial domain architectures belong within Foundation scope:

- Identity Architecture
- Memory Architecture
- Governance Architecture
- Recovery Architecture
- MCP Architecture
- Obsidian Architecture

These documents define implementation-neutral responsibilities, structures,
boundaries, risks, and future packaging considerations for their domains.

### 3.2 Cross-Domain Governance Contracts

Canonical cross-domain contracts belong within Foundation scope, including:

- OpenClaw Foundations Glossary
- Domain Precedence Model
- Canonical Override and Exception Manifest
- Trust Boundary and Data Classification Model
- Canonical Steward Identifiers and Namespace Isolation
- Minimum Conformance Profile

These documents establish terminology, authority relationships, exceptions,
classification, namespace isolation, and conformance expectations shared
across domains.

### 3.3 Phase 8C Packaging Foundations

The following Phase 8C documentation belongs within Foundation scope:

- OpenClaw Requirement Identifier Framework
- OpenClaw Classification Metadata Schema
- OpenClaw Steward Inheritance Template
- OpenClaw Foundation Package Manifest

Future approved Phase 8C schemas, templates, checklists, and package-boundary
documents may also become Foundation components when they meet the composition
rules in this manifest.

### 3.4 Foundation Planning and Validation Records

Roadmaps, validation checklists, architecture decisions, and foundation
handoffs may be retained within the Shared Foundations repository when they
provide traceability for the canonical architecture.

Such records must be clearly distinguished from current normative contracts.
Historical presence does not make every planning note, finding, or handoff a
required inheritance component.

### 3.5 Content-Free Structural Examples

The Foundation Package may include documentation-only examples, templates, or
synthetic fixtures when they:

- contain no real steward or user-private content
- use synthetic, redacted, or clearly marked placeholder identifiers
- illustrate a canonical contract
- remain implementation-neutral
- do not imply permission, conformance, or operational readiness

This manifest does not authorize creating executable fixtures or package
assets.

## 4. Explicit Exclusions

The following must remain outside the Foundation Package.

### 4.1 Runtime Implementations

Excluded runtime material includes:

- application or service code
- executable scripts
- agents, daemons, workers, or schedulers
- runtime adapters
- database implementations
- model-provider implementations
- live MCP servers or clients
- deployment configuration
- containers, images, or infrastructure definitions

Architecture may describe interfaces and expectations without including their
implementation.

### 4.2 Credentials and Secrets

The package must never contain:

- credentials
- API keys
- access tokens
- private keys
- passwords
- recovery secrets
- protected endpoints with embedded authorization
- secret environment values

Documentation should use protected references or synthetic placeholders, not
secret values.

### 4.3 Steward and User Content

The package must never contain:

- steward memories
- user data
- personal histories
- private communications
- populated identity profiles
- private identity anchors
- relationship context
- current steward state
- steward-specific knowledge bases
- private Obsidian notes or attachments

Foundation schemas may define where such values belong without supplying the
values.

### 4.4 Operational Material

Excluded operational material includes:

- operational reports
- live monitoring output
- incident evidence
- service logs
- production audit records
- steward-specific evidence archives
- backups and recovery archives
- live conformance evidence
- runtime health records

Sanitized structural examples may be documented only when they satisfy
classification and composition rules.

### 4.5 Integrations and Automations

The package must not contain:

- steward integrations
- external-service integrations
- automation workflows
- lifecycle hooks
- scheduled jobs
- synchronization processes
- migration executors
- installation or update automations

Conceptual integration boundaries may be documented without creating an
integration.

### 4.6 Steward-Specific Operations

The package must not contain:

- steward-specific workflows
- local capability grants
- local operating procedures presented as universal
- steward-specific taxonomies
- local recovery procedures or anchors
- local approval records
- local exception authority
- local archive inventories
- populated steward inheritance profiles

Reusable local patterns remain steward-owned until accepted through versioned
foundation governance.

### 4.7 Distribution and Public Release Assets

This manifest does not include or authorize:

- package archives
- installers
- registries
- checksums or signatures
- release bundles
- public download pages
- public announcement materials
- badges or certification marks
- repository publishing configuration

Logical inclusion in the Foundation Package is separate from approval for
public release or distribution.

## 5. Package Boundaries

The OpenClaw architecture distinguishes four conceptual layers:

1. Foundation
2. Steward
3. Runtime
4. External Services

### 5.1 Foundation Boundary

The Foundation layer contains canonical, versioned, content-free contracts.

It owns:

- architecture definitions
- governance and conformance contracts
- canonical terminology
- requirement and classification frameworks
- inheritance and package-boundary guidance
- implementation-neutral schemas and templates

It does not own:

- populated steward identity or memory
- operational authority
- credentials or permissions
- runtime state
- external services

### 5.2 Steward Boundary

The Steward layer contains one steward's independently owned content and
specialization.

It owns:

- identity content and namespace
- memory and current state
- local governance operation
- local extensions and documentation
- capability selection and grants
- evidence, archives, and recovery material
- domain-specific workflows

A steward depends on Foundation contracts without becoming part of the
Foundation Package.

### 5.3 Runtime Boundary

The Runtime layer implements behavior using technologies selected by the
steward or operator.

It may include:

- applications and agent processes
- storage and retrieval systems
- context assembly
- policy enforcement
- capability execution
- logging, monitoring, and recovery operations

Runtime implementations must map to applicable Foundation and Steward
contracts, but they remain outside the Foundation Package. Runtime behavior
cannot silently redefine canonical Foundation meaning.

### 5.4 External Services Boundary

External Services are systems not owned as Foundation contracts or steward
content, including:

- model providers
- databases and hosted storage
- MCP services
- communications platforms
- financial, sales, research, or other domain services
- synchronization and hosting providers

External services are capability and trust boundaries. Their availability
does not grant authority, and their schemas or policies do not become
Foundation definitions merely because a steward uses them.

### 5.5 Boundary Summary

| Layer | Primary responsibility | Included in Foundation Package |
|---|---|---|
| Foundation | Canonical contracts, schemas, governance, and shared definitions | Yes |
| Steward | Identity, memory, specialization, evidence, and local policy | No |
| Runtime | Technical implementation and operational behavior | No |
| External Services | Third-party or separately governed capabilities and infrastructure | No |

Movement or reference across these boundaries remains governed by
classification, namespace, provenance, capability, and exception rules.

## 6. Foundation Dependency Model

Steward repositories conceptually depend on Shared Foundations through
versioned contract references.

A steward dependency declaration should identify:

- adopted Foundation version
- inherited domains
- applicable requirements
- optional or deferred domains
- local extensions
- approved overrides or exceptions
- compatibility limitations
- local evidence or implementation mappings

The dependency is:

- **versioned:** a steward records the Foundation version it adopts
- **selectively applicable:** mandatory domains and requirements apply as
  defined; conditional or optional domains are declared separately
- **contract-based:** the dependency is on definitions and obligations, not
  copied private content
- **implementation-neutral:** equivalent implementations may satisfy the same
  contract when permitted
- **non-transitive for steward content:** adopting the Foundation does not
  cause one steward to depend on another steward's repository or state

Conceptually:

```text
OpenClaw Shared Foundations
    |
    +-- canonical contracts and version
    |
    +-- Steward A inheritance map
    |      +-- Steward A content and implementation
    |
    +-- Steward B inheritance map
           +-- Steward B content and implementation
```

Steward A and Steward B may depend on the same Foundation version without
depending on each other.

This model does not define Git relationships, package managers, submodules,
registries, synchronization, installation, or update mechanisms.

## 7. Versioning Guidance

Foundation versions describe the compatibility significance of changes to the
logical Foundation Package.

The recommended conceptual form is:

```text
MAJOR.MINOR.PATCH
```

Pre-1.0 documents may continue to use explicit document versions such as
`v0.1`. This section defines change meaning only and does not create a release
procedure.

### 7.1 Major Version

A Major version indicates a change that may require steward migration,
reassessment, or an updated inheritance map.

Examples include:

- incompatible changes to mandatory architecture contracts
- removal or redefinition of canonical fields or classifications
- changed domain precedence
- changed steward ownership or namespace rules
- incompatible requirement semantics
- a newly mandatory domain that affects existing scopes

A Major change must identify compatibility and migration effects. It must not
overwrite steward-owned content.

### 7.2 Minor Version

A Minor version indicates backward-compatible Foundation expansion.

Examples include:

- a new optional domain
- new optional metadata fields
- additional foundation requirements that do not invalidate existing adopted
  contracts
- new documentation templates
- expanded guidance or validation coverage

A Minor change may require an applicability review but should not require
existing compliant steward content to be rewritten solely because the new
feature exists.

### 7.3 Patch Version

A Patch version indicates a backward-compatible correction or clarification
that does not change normative meaning.

Examples include:

- typo and formatting corrections
- corrected links or document references
- clearer non-normative examples
- wording clarification that preserves existing obligations

A material normative change must not be disguised as a Patch.

### 7.4 Document and Package Versions

Individual Foundation documents may have their own versions. The Foundation
Package version identifies an approved composition of document versions.

A package inventory should make both levels traceable:

- Foundation Package version
- component document title and version

Changing one component does not automatically determine the package version
category; governance must evaluate the compatibility effect on the package as
a whole.

### 7.5 Version Adoption

A steward should continue to identify its adopted Foundation version until it
reviews and adopts another version. Newer availability does not silently
change the steward's contract.

Optional additions may be deferred when no adopted requirement makes them
applicable. Incompatible changes require the treatment described by the
Steward Inheritance Template and applicable exception governance.

This manifest does not define release cadence, branches, tags, changelogs,
signing, publishing, support windows, or distribution procedures.

## 8. Package Composition Rules

A future document is eligible for inclusion in the Foundation Package only
when it defines a reusable, foundation-owned contract or supporting record
that applies across stewards or foundation governance.

### 8.1 Eligibility

An eligible component should:

- address a shared architecture, governance, schema, classification,
  requirement, conformance, inheritance, or recovery need
- be implementation-neutral unless a justified contract requires otherwise
- be reusable by more than one steward or future steward type
- preserve steward identity, memory, namespace, and permission independence
- contain no populated private steward or user data
- identify its title, scope, owner, and version
- define relationships to existing Foundation documents

Steward-specific usefulness alone does not establish Foundation eligibility.

### 8.2 Scope Requirements

A proposed component must state:

- purpose
- normative and non-normative scope
- owning domain or cross-domain owner
- intended consumers
- applicability
- dependencies
- exclusions
- inheritance behavior
- compatibility impact
- classification
- version

It should distinguish required contracts from optional guidance and examples.

### 8.3 Governance Expectations

Foundation composition changes require versioned Foundation governance.
Review should confirm:

- the component does not duplicate or contradict an existing contract
- domain ownership and precedence are clear
- requirement IDs are assigned when normative obligations need stable
  references
- classification metadata is appropriate
- private or restricted content is absent
- conformance and inheritance effects are documented
- future migration or deprecation can be expressed

### 8.4 Prohibited Composition Patterns

A document must not enter the Foundation Package merely because:

- it exists in the Shared Foundations repository
- one steward uses it
- it is operationally convenient
- it describes a popular tool or vendor
- it contains historical foundation discussion
- several stewards independently created similar local content

Repository location is evidence of location, not automatic evidence of
canonical package status.

### 8.5 Removal or Replacement

A canonical component should be removed, deprecated, superseded, or replaced
only through versioned governance that identifies:

- affected package and document versions
- requirement and inheritance effects
- replacement source, when applicable
- compatibility significance
- historical reference treatment

Historical records may remain in the repository without remaining active
Foundation Package components.

## 9. Example Package Inventory

The following inventory illustrates a Foundation Package composition based on
the current documentation. It is not a generated archive, lockfile, release
bundle, or public distribution.

### 9.1 Core Domain Architectures

| Component | Repository source | Package role |
|---|---|---|
| Identity Architecture | `identity/FOUNDATION_IDENTITY_ARCHITECTURE.md` | Canonical identity structure and boundary contract |
| Memory Architecture | `memory/FOUNDATION_MEMORY_ARCHITECTURE.md` | Canonical durable-memory and provenance contract |
| Governance Architecture | `governance/FOUNDATION_GOVERNANCE_ARCHITECTURE.md` | Canonical authority and governance contract |
| Recovery Architecture | `recovery/FOUNDATION_RECOVERY_ARCHITECTURE.md` | Canonical recovery and restoration contract |
| MCP Architecture | `mcp/FOUNDATION_MCP_ARCHITECTURE.md` | Canonical external-capability contract |
| Obsidian Architecture | `obsidian/FOUNDATION_OBSIDIAN_ARCHITECTURE.md` | Canonical optional knowledge-projection contract |

### 9.2 Cross-Domain Contracts

| Component | Repository source | Package role |
|---|---|---|
| Foundations Glossary | `docs/OPENCLAW_FOUNDATIONS_GLOSSARY_v0.1.md` | Canonical terminology |
| Domain Precedence Model | `docs/DOMAIN_PRECEDENCE_MODEL_v0.1.md` | Cross-domain authority and conflict rules |
| Override and Exception Manifest | `docs/CANONICAL_OVERRIDE_AND_EXCEPTION_MANIFEST_v0.1.md` | Controlled deviation governance |
| Trust Boundary and Data Classification Model | `docs/TRUST_BOUNDARY_AND_DATA_CLASSIFICATION_MODEL_v0.1.md` | Data-handling and boundary contract |
| Steward Identifiers and Namespace Isolation | `docs/CANONICAL_STEWARD_IDENTIFIERS_AND_NAMESPACE_ISOLATION_v0.1.md` | Canonical steward identity and isolation contract |
| Minimum Conformance Profile | `docs/MINIMUM_CONFORMANCE_PROFILE_v0.1.md` | Minimum compatibility and evidence expectations |

### 9.3 Phase 8C Packaging Foundations

| Component | Repository source | Package role |
|---|---|---|
| Requirement Identifier Framework | `docs/OPENCLAW_REQUIREMENT_IDENTIFIER_FRAMEWORK_v0.1.md` | Stable requirement references |
| Classification Metadata Schema | `docs/OPENCLAW_CLASSIFICATION_METADATA_SCHEMA_v0.1.md` | Canonical descriptive metadata |
| Steward Inheritance Template | `docs/OPENCLAW_STEWARD_INHERITANCE_TEMPLATE_v0.1.md` | Contract adoption and specialization model |
| Foundation Package Manifest | `docs/OPENCLAW_FOUNDATION_PACKAGE_MANIFEST_v0.1.md` | Package scope and boundary definition |

### 9.4 Supporting Repository Documents

The following may support traceability without necessarily being mandatory
inheritance components:

| Component | Repository source | Role |
|---|---|---|
| Repository overview | `README.md` | Orientation and current repository scope |
| Shared Foundations Roadmap | `docs/SHARED_FOUNDATIONS_ROADMAP_v0.1.md` | Phase planning and sequencing |
| Phase 8B Validation Checklist | `docs/PHASE_8B_VALIDATION_CHECKLIST_v0.1.md` | Historical validation record |
| Foundation handoffs | `docs/handoffs/` | Historical phase-transition records |

An approved future package inventory should identify whether each component is
normative, supporting, optional, historical, or deprecated.

## 10. Future Expansion Guidance

Additional Foundation domains may be added when an existing domain cannot
express a materially distinct, reusable contract.

A future-domain proposal should define:

- domain purpose and boundary
- foundation ownership
- relationship to Governance, Identity, Recovery, Memory, MCP, and Obsidian
- precedence and conflict behavior
- requirement prefix, when approved
- classification and trust-boundary effects
- conformance applicability
- inheritance and optionality
- recovery and migration expectations
- compatibility impact on existing Foundation versions

### 10.1 Non-Breaking Expansion

A new domain may be added without breaking existing steward inheritance when:

- it is optional or conditionally applicable
- existing requirement meanings remain unchanged
- existing namespace and ownership rules remain valid
- existing stewards do not need to modify private content
- omission remains valid for previously declared scopes
- the new domain has no implicit authority over established domains

Such an addition would normally be considered Minor-version expansion, subject
to governance review.

### 10.2 Breaking Expansion

A new domain is potentially breaking when it:

- changes mandatory protections
- changes domain precedence
- redefines existing requirement or classification meaning
- requires existing stewards to restructure owned content
- makes a previously optional behavior mandatory
- changes conformance claims for existing scopes

Breaking expansion requires explicit compatibility and migration guidance and
would normally require a Major version.

### 10.3 Existing Steward Protection

Future package expansion must not:

- modify existing steward repositories automatically
- populate new steward-owned fields without steward action
- merge steward namespaces
- inherit local exceptions
- enable integrations or capabilities
- require use of another steward's specialization
- invalidate a prior version without documented governance

Existing stewards may remain on their recorded Foundation version or adopt a
new version according to applicable support, conformance, and compatibility
guidance.

### 10.4 Promotion of Steward Patterns

A steward-owned or shared-steward pattern may be proposed for Foundation
adoption. Promotion requires:

- removal of steward-private content
- generalization into an implementation-neutral contract
- clear foundation ownership
- compatibility and inheritance review
- versioned governance approval

Until approved, the pattern remains outside the Foundation Package.

## 11. Reference Summary

### Included

- canonical domain architectures
- cross-domain governance and conformance contracts
- requirement and classification frameworks
- steward inheritance guidance
- package scope and composition definitions
- approved content-free schemas, templates, and synthetic examples

### Excluded

- runtime implementations
- credentials, API keys, tokens, and secrets
- steward identity, memory, current state, and user data
- operational reports, evidence, logs, backups, and archives
- integrations and automations
- steward-specific workflows and permissions
- package archives and distribution mechanisms
- public release assets

### Boundary Rule

| Layer | Foundation Package treatment |
|---|---|
| Foundation | Included when canonical and approved |
| Steward | Referenced structurally; populated content excluded |
| Runtime | Contract consumer; implementation excluded |
| External Services | Boundary dependency; service and integration excluded |

The governing rule is: package canonical, content-free Foundation contracts;
keep steward state, runtime behavior, external services, operational material,
and distribution mechanisms outside.
