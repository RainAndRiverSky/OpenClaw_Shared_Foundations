# OpenClaw Packaging and Distribution Guide v0.1

## 1. Purpose

This document defines the canonical governance and architectural guidance for
how OpenClaw steward repositories may receive, reference, inherit, maintain,
or extend OpenClaw Shared Foundations.

Packaging and distribution guidance exists because a shared architecture can
be adopted in several ways without using one technical delivery mechanism.
The relationship between the canonical Foundation, a steward repository,
local extensions, and future Foundation revisions must remain clear whether a
steward references documents, records an inheritance map, embeds a controlled
copy, or maintains a declared fork.

Consistent guidance supports:

- **ecosystem consistency:** stewards use the same definitions for Foundation
  scope, inheritance, extensions, overrides, and ownership
- **steward onboarding:** a new steward can evaluate and adopt Shared
  Foundations without receiving another steward's private content
- **governance scalability:** canonical protections and change expectations
  can be maintained centrally while local decisions remain steward-owned
- **future ecosystem growth:** new stewards and domains can join without
  requiring changes to existing steward repositories
- **maintenance reduction:** common contracts can be reviewed once and
  referenced across many steward contexts without unnecessary duplication

This guide treats packaging as the governed organization of content-free
Foundation contracts and distribution as the conceptual relationship by which
a steward receives or references those contracts. It does not create an
archive, installer, package registry, synchronization process, release
channel, or runtime integration.

## 2. Relationship to Foundation Contracts

This guide complements:

- the OpenClaw Foundation Package Manifest
- the OpenClaw Steward Inheritance Template
- the OpenClaw Requirement Identifier Framework
- the OpenClaw Classification Metadata Schema
- the Minimum Conformance Profile
- the Domain Precedence Model
- the Canonical Override and Exception Manifest
- the Trust Boundary and Data Classification Model
- the Canonical Steward Identifiers and Namespace Isolation model

The Foundation Package Manifest controls what belongs inside and outside the
logical Foundation Package. The Steward Inheritance Template controls how a
steward records Inherited, Extended, Overridden, and Steward-Owned
relationships.

This guide does not replace those contracts. If packaging convenience
conflicts with classification, namespace isolation, governance, or steward
ownership, the governing Foundation contract controls.

## 3. Packaging Philosophy

### 3.1 Foundation First

Canonical Foundation definitions should be established, versioned, and
reviewed before steward-specific packaging or runtime implementation.

Foundation First means:

- shared terms and contracts are defined at Foundation scope
- steward packages or profiles reference an identified Foundation version
- local specializations remain distinguishable from canonical definitions
- implementation choices do not silently redefine architecture

Foundation First does not mean Foundation ownership of steward identity,
memory, operations, or repositories.

### 3.2 Steward Autonomy

Each steward remains independently identified and governs its own:

- identity content
- memory and current state
- permissions and credentials
- operational workflows
- evidence and archives
- runtime and storage choices
- specialization and local documentation

Adopting Shared Foundations does not make a steward a subordinate runtime
instance, copy another steward's profile, or authorize cross-steward access.

### 3.3 Documentation Before Runtime

Adoption relationships, scope, requirements, optional domains, extensions,
exceptions, and compatibility limitations should be documented before runtime
integration.

Documentation Before Runtime reduces ambiguity about:

- which version is being adopted
- which domains apply
- what remains steward-owned
- what requires an exception
- what evidence will later be needed
- which private content must remain external

Documentation is necessary for traceability but does not prove runtime
behavior.

### 3.4 Non-Intrusive Adoption

Foundation adoption must not overwrite, relocate, merge, or reclassify
steward-owned content.

Non-Intrusive Adoption requires:

- contract-based inheritance
- preservation of the steward namespace
- explicit treatment of local extensions
- no automatic capability enablement
- no transfer of credentials or private records
- no silent changes to runtime behavior

A steward may adopt documentation while deferring implementation or optional
domains.

### 3.5 Governance Consistency

Every distribution model must preserve canonical governance meaning,
including:

- domain precedence
- requirement identifiers
- classification and trust boundaries
- namespace isolation
- override and exception rules
- conformance terminology

Changing delivery form does not weaken these obligations.

### 3.6 Content-Free Distribution

Foundation distribution should contain contracts, definitions, schemas,
templates, and approved synthetic examples only. It must exclude populated
steward identity, memory, credentials, operational evidence, user data,
private archives, and capability grants.

### 3.7 Versioned Traceability

Every steward adoption should identify the Foundation version and the local
adoption or inheritance record. A copied document without source and version
traceability is not a reliable Foundation dependency.

### 3.8 Distribution Does Not Grant Authority

Receiving Foundation documents does not:

- grant permissions
- approve an exception
- establish conformance
- authorize a public claim
- enable MCP tools
- approve publication
- transfer Foundation governance authority

## 4. Distribution Models

The approved conceptual distribution approaches in v0.1 are:

- Reference Model
- Inheritance Model
- Embedded Copy Model
- Fork-and-Extend Model

These models describe documentation relationships. They do not prescribe Git,
package managers, archives, registries, installation commands, or update
mechanisms.

### 4.1 Reference Model

#### Purpose

The Reference Model allows a steward repository to cite canonical Foundation
documents at their authoritative source without copying them into the steward
repository.

#### Advantages

- minimizes duplicated Foundation content
- keeps canonical ownership clear
- reduces risk of local edits being mistaken for Foundation changes
- makes Foundation corrections available at the canonical source
- keeps the steward repository focused on local content

#### Limitations

- the steward must preserve an exact version reference
- availability of a newer canonical source must not silently change the
  steward's adopted version
- offline or archival review may require separately preserved evidence of the
  assessed version
- local readers may need to consult more than one repository

#### Recommended Use Cases

Use the Reference Model when:

- the steward needs a lightweight documentation dependency
- canonical Foundation documents are accessible to intended reviewers
- the steward can maintain a clear versioned inheritance map
- duplication would create unnecessary maintenance risk

The Reference Model is generally preferred for direct use of unchanged
Foundation documents.

### 4.2 Inheritance Model

#### Purpose

The Inheritance Model records how a steward adopts Foundation contracts and
adds steward-owned mappings, extensions, optionality, evidence references, or
approved overrides.

#### Advantages

- provides explicit domain-by-domain traceability
- preserves separation between Foundation definitions and local content
- supports steward specialization
- makes applicability and optional adoption visible
- supports future conformance and upgrade review

#### Limitations

- requires maintenance of an inheritance record
- does not by itself preserve a full local copy of Foundation documents
- can become ambiguous if local extensions are not clearly qualified
- does not prove runtime implementation or conformance

#### Recommended Use Cases

Use the Inheritance Model when:

- a steward intends structured adoption
- local extensions or optional domains need documentation
- future packaging or conformance review is expected
- the steward needs a durable account of Foundation and local responsibilities

The Inheritance Model is the recommended default for steward repositories
formally adopting Shared Foundations.

### 4.3 Embedded Copy Model

#### Purpose

The Embedded Copy Model places a controlled, identified copy of selected
Foundation documentation within a steward repository for local availability,
review, or archival stability.

#### Advantages

- provides local access to the exact adopted text
- supports offline review and historical reconstruction
- can preserve the assessed Foundation version with the steward record
- may simplify review where cross-repository access is impractical

#### Limitations

- creates duplication and drift risk
- local edits may be mistaken for canonical Foundation changes
- copied documents require source, version, and modification status
- upgrades require deliberate comparison and review
- inclusion in a steward repository does not transfer Foundation ownership

#### Recommended Use Cases

Use the Embedded Copy Model only when:

- local preservation of exact Foundation text is materially useful
- the copy is clearly labeled with source and version
- local modifications are prohibited or separately identified
- the steward maintains an inheritance map that points to the canonical source
- review processes can detect stale or divergent copies

An embedded copy should be classified as one of:

- `Unmodified Foundation Copy`
- `Locally Annotated Reference`
- `Derived Steward Document`

A locally annotated or derived document must not be presented as canonical
Foundation text.

### 4.4 Fork-and-Extend Model

#### Purpose

The Fork-and-Extend Model allows a downstream project to maintain a declared
derivative of Foundation documents while adding or changing architecture for
its own scope.

#### Advantages

- supports substantial experimentation or divergent requirements
- allows coordinated changes across many Foundation-derived documents
- preserves an ancestry record when maintained carefully
- may support proposals that later return to Foundation governance

#### Limitations

- has the highest divergence and maintenance risk
- downstream changes are not automatically canonical OpenClaw definitions
- compatibility and conformance claims require exact disclosure
- Foundation updates may not merge cleanly with local changes
- local governance cannot acquire Foundation authority through ancestry

#### Recommended Use Cases

Use the Fork-and-Extend Model when:

- a project intentionally needs material architectural divergence
- experimental or downstream governance is clearly separated
- maintainers can track changed and unchanged contracts
- compatibility limitations are disclosed
- the derivative does not claim canonical status without approval

A conforming steward normally should prefer Reference plus Inheritance over a
fork. A fork that changes mandatory contracts must use valid exceptions where
permitted, change its conformance claim, or declare incompatibility.

### 4.5 Model Selection Summary

| Model | Primary relationship | Best fit | Main risk |
|---|---|---|---|
| Reference | Cite canonical source | Lightweight unchanged use | Version ambiguity |
| Inheritance | Map canonical contracts to steward scope | Formal steward adoption | Incomplete local mapping |
| Embedded Copy | Preserve identified local copy | Offline or archival review | Drift and mistaken ownership |
| Fork-and-Extend | Maintain declared derivative | Material experimentation or divergence | Compatibility loss |

Models may be combined when their roles remain explicit. For example, a
steward may use the Reference Model for canonical documents, the Inheritance
Model for applicability, and an Embedded Copy for an assessed historical
version.

## 5. Steward Adoption Process

The conceptual steward adoption lifecycle is:

1. Evaluate
2. Adopt
3. Inherit
4. Extend
5. Maintain

### 5.1 Evaluate

The steward reviews Shared Foundations before making an adoption claim.

Evaluation should identify:

- steward mission and canonical identifier
- proposed Foundation version
- mandatory and conditional domains
- local architecture and terminology mappings
- known incompatibilities
- private content and runtime boundaries
- expected distribution model
- governance and review owners

Evaluation may conclude that the steward is not ready to adopt, will adopt a
limited scope, or will remain Foundation-Aligned rather than claiming
compatibility.

### 5.2 Adopt

The steward records an intentional decision to use a named Foundation version
for a declared scope.

An adoption record should identify:

- steward
- Foundation version
- distribution model
- adopted domains and frameworks
- optional or deferred items
- adoption owner and date
- current status
- known limitations

Adoption does not automatically enable runtime behavior or establish
Foundation-Compatible status.

### 5.3 Inherit

The steward creates or maintains an inheritance map using the Steward
Inheritance Template.

The map should distinguish:

- Inherited Foundation contracts
- Extended local rules
- Overridden rules with valid authorization
- Steward-Owned subjects
- not-applicable, optional, or deferred items

Applicable Foundation requirements should use canonical requirement IDs.
Steward extensions should use qualified steward identifiers where required.

### 5.4 Extend

The steward adds its own identity content, specialization, workflows,
documentation, classifications, and implementation mappings.

Extensions must:

- remain within the steward namespace
- preserve canonical Foundation meaning
- identify their local owner and version
- remain distinguishable from inherited requirements
- avoid weakening mandatory protections
- use exception governance for authorized deviations

A steward may complete adoption without defining optional extensions.

### 5.5 Maintain

The steward keeps its adoption relationship current.

Maintenance includes:

- preserving the adopted Foundation version
- reviewing relevant Foundation revisions
- updating local applicability and extension records
- reviewing exceptions and compatibility limitations
- maintaining classification and namespace boundaries
- preserving historical adoption decisions
- keeping claims aligned with current evidence

Maintenance is a governance responsibility, not an automatic update process.

## 6. Foundation Upgrade Guidance

Foundation revisions should be evaluated against the steward's recorded
adoption scope and inheritance map before adoption.

### 6.1 Review Inputs

An upgrade review should consider:

- current and proposed Foundation versions
- changed package inventory
- changed domain contracts
- added, changed, deprecated, superseded, or retired requirements
- classification-schema changes
- precedence, exception, namespace, or conformance changes
- local extensions that depend on changed definitions
- optional additions
- steward-owned content that must remain untouched

### 6.2 Compatibility Considerations

The steward should determine whether the revision is:

- backward-compatible for its declared scope
- compatible only after local documentation changes
- compatible only with an approved bounded exception
- incompatible with its current implementation or governance
- irrelevant to its current scope

A Foundation-level Minor or Patch classification does not remove the need for
local review. A local extension may depend on assumptions affected by an
otherwise non-breaking change.

### 6.3 Optional Adoption

New optional domains, requirements, fields, or guidance may be:

- adopted immediately
- scheduled for later review
- deferred with a documented reason
- marked not applicable to the steward's scope

Deferring an optional item is not an override unless another applicable
contract makes it mandatory.

### 6.4 Documentation Review Expectations

Before recording an upgraded version, the steward should update or confirm:

- adoption record
- inheritance map
- requirement mappings
- classification mappings
- local extensions
- exception references
- compatibility notes
- conformance scope and claims

Historical records should preserve the Foundation version that applied at the
time of each assessment or decision.

### 6.5 Upgrade Outcomes

After review, a steward may:

- adopt the revision
- adopt selected optional additions while retaining its current base version
  where governance permits
- remain on the prior version
- use an approved compatibility exception
- revise its conformance claim
- declare incompatibility

Foundation availability does not silently update steward contracts.

### 6.6 Upgrade Preservation

An upgrade review must not authorize:

- overwriting steward identity or memory
- merging namespaces
- importing another steward's defaults
- enabling capabilities
- restoring revoked permissions
- reclassifying private content as Public
- propagating unrelated exceptions

This section does not define download, installation, merge, synchronization,
migration, or update mechanisms.

## 7. Package Boundary Protection

### 7.1 Separation of Concerns

The four package boundaries remain distinct:

| Layer | Owns |
|---|---|
| Foundation | Canonical contracts, schemas, requirements, governance, and shared definitions |
| Steward | Identity, memory, specialization, evidence, local policy, and local documentation |
| Runtime | Technical implementation and operational behavior |
| External Services | Separately governed systems and capabilities |

Distribution may create references between these layers but must not collapse
their ownership.

### 7.2 Steward Autonomy

During adoption, a steward retains authority over:

- whether to adopt a supported Foundation version
- optional domains and local specialization
- implementation and storage choices
- local stricter controls
- private content
- runtime timing and operational readiness

Steward autonomy does not permit a conforming claim that silently weakens
mandatory Foundation protections.

### 7.3 Foundation Integrity

Foundation integrity requires:

- canonical documents remain attributable to Foundation governance
- embedded copies retain source and version labels
- local annotations remain visibly local
- forks disclose divergence
- requirement IDs retain canonical meaning
- Foundation classifications and governance terms are not redefined locally
- local extensions do not masquerade as Foundation requirements

### 7.4 Content and Data Protection

Foundation adoption must not move into a Foundation package or shared
distribution:

- steward memory
- user data
- private identity anchors
- credentials or secret values
- local evidence archives
- operational logs
- private recovery material
- protected Obsidian content

Examples must be synthetic, redacted, or structural.

### 7.5 Capability Protection

Packaging and distribution do not enable tools, external services,
integrations, or automations. Capability availability remains separate from
permission and must follow applicable MCP and governance contracts.

### 7.6 Boundary Failure

If adoption material mixes canonical Foundation content with unmarked local
changes, private content, or operational configuration, the steward should
pause the affected adoption claim and restore clear ownership, classification,
and version boundaries.

## 8. Example Distribution Scenarios

The following examples are documentation-only. They do not modify the named
stewards, establish real adoption, enable capabilities, or prove conformance.

### 8.1 Keeper Caleb

Keeper Caleb uses the Reference Model for canonical Foundation documents and
the Inheritance Model for Governance, Classification, Requirements, Recovery,
Identity structure, and Memory contracts.

Caleb records monitoring, evidence archives, and household registry work as
Steward-Owned. A local archival copy of the assessed Foundation version may
use the Embedded Copy Model if it is clearly labeled and kept unmodified.

### 8.2 Seller Zayne

Seller Zayne uses the Inheritance Model for Governance, Identity, Memory,
Recovery, Classification, Requirements, and applicable MCP architecture.

Sales workflows, listing records, transaction evidence, and local capability
profiles remain Zayne-owned extensions or records. MCP architecture adoption
does not enable sales tools or grant access to external services.

### 8.3 Seeker Xavier

Seeker Xavier uses the Reference and Inheritance Models for Foundation
contracts while extending source-evaluation metadata and research provenance.

Research logs, evidence synthesis, and external-reference catalogs remain
Xavier-owned. External sources do not become Foundation content through
reference or citation.

### 8.4 Billing Steward Nier

Billing Steward Nier uses the Inheritance Model with explicit Restricted
classification mappings for billing and reconciliation subjects.

Billing workflows, account records, financial evidence, credentials, and
external-service configurations remain outside the Foundation Package. The
distribution relationship grants no access to financial systems.

### 8.5 Candidate Steward HeyDay

Candidate Steward HeyDay begins with the Reference Model and a limited
Inheritance Model covering Governance, Classification, Requirements, Identity
structure, and Recovery boundaries.

Memory, MCP, Obsidian, and ecosystem participation remain deferred during
evaluation. HeyDay does not receive another steward's profile, history,
evidence, or exceptions.

### 8.6 Future OpenClaw Steward

A future steward establishes a new canonical steward identifier, evaluates a
supported Foundation version, selects a distribution model, and records an
independent inheritance map.

The new steward may reuse canonical contracts and develop its own
specialization without modifying Keeper Caleb, Seller Zayne, Seeker Xavier,
Billing Steward Nier, Candidate Steward HeyDay, or any other steward.

## 9. Ecosystem Expansion Guidance

Future stewards join through independent adoption, not through modification of
existing steward repositories.

A future steward should:

- establish an independent canonical identifier and namespace
- identify its mission and accountable owner
- select a Foundation version
- choose a distribution model
- evaluate mandatory, conditional, and optional domains
- create an inheritance map
- classify local records
- define local extensions separately
- preserve private identity, memory, permissions, evidence, and recovery
- document cross-steward relationships independently

Existing stewards are not required to:

- adopt the new steward's specialization
- change their Foundation version
- expose private records
- grant capabilities
- share a runtime or memory store
- accept the new steward into a cross-steward relationship
- inherit its exceptions

### 9.1 Cross-Steward Relationships

Any collaboration between stewards is separate from Foundation distribution.
It should define:

- participating steward identifiers
- purpose
- data classification
- ownership
- capability scope
- provenance
- duration or exit conditions

Ecosystem membership and shared Foundation adoption do not create automatic
cross-steward authority.

### 9.2 Shared Patterns

Several stewards may independently use a similar extension. That pattern
remains local or Shared Steward material until approved through versioned
Foundation governance.

Foundation promotion should generalize the pattern, remove private content,
define compatibility, and preserve existing steward inheritance.

### 9.3 New Foundation Domains

New domains should normally enter as optional or conditional when they can do
so without changing existing contracts. They must define ownership,
precedence, requirement identifiers, classification, inheritance, and
compatibility effects.

Existing stewards should not be required to adopt a new optional domain merely
because the ecosystem expands.

## 10. Future Packaging Evolution

The following areas are intentionally deferred beyond this v0.1 documentation
foundation:

### 10.1 Runtime Packaging

Deferred work includes executable applications, adapters, containers,
deployment definitions, runtime configuration, and implementation bundles.

### 10.2 Automated Distribution

Deferred work includes synchronization, installation, update automation,
dependency resolution, and automated migration.

### 10.3 Package Registries

Deferred work includes registry selection, package naming, publishing,
discovery, integrity metadata, and dependency-lock formats.

### 10.4 Public Releases

Deferred work includes public release approval, licensing, contribution
processes, security reporting, signatures, checksums, download channels,
announcements, and public release assets.

### 10.5 Certification Programs

Deferred work includes official certification authorities, marks, badges,
assessment accreditation, renewal programs, and public certification
registries.

### 10.6 Installation Instructions

Deferred work includes command-line procedures, repository linking,
submodules, package-manager instructions, environment setup, and deployment
steps.

### 10.7 Integration Catalogs

Deferred work includes supported runtime matrices, MCP server catalogs,
external-service adapters, tested provider combinations, and operational
compatibility suites.

### 10.8 Automated Conformance

Deferred work includes validators, policy engines, evidence collectors,
automated requirement checks, and enforcement mechanisms.

Future work in these areas must preserve Foundation scope, steward autonomy,
classification, namespace isolation, version traceability, and exception
governance.

## 11. Completion Criteria

Shared Foundations adoption is successfully documented for a steward
repository when all applicable criteria below are met.

### 11.1 Identity and Scope

- the steward has an independent canonical identifier or a documented pending
  identifier state appropriate to evaluation
- the adoption scope is explicit
- the adopted Foundation version is explicit
- the selected distribution model is explicit

### 11.2 Inheritance

- adopted domains and frameworks are listed
- mandatory, conditional, optional, deferred, and not-applicable items are
  distinguishable
- Inherited, Extended, Overridden, and Steward-Owned relationships are clear
- applicable Foundation requirements retain canonical identifiers
- steward extensions remain qualified and local

### 11.3 Boundary Protection

- Foundation content is separate from steward-owned content
- identity, memory, credentials, permissions, user data, and private archives
  remain outside Foundation scope
- runtime and external-service implementations remain separate
- classifications and steward namespaces are preserved
- embedded copies or forks disclose source, version, and modifications

### 11.4 Governance

- local governance ownership is identified
- deviations use approved exception governance where required
- compatibility limitations are documented
- optional adoption does not masquerade as mandatory Foundation scope
- public or certification claims are not made without applicable authority

### 11.5 Maintenance Readiness

- an adoption or inheritance record has an owner and status
- future Foundation revisions can be compared against the recorded version
- local extensions and exceptions are discoverable
- historical version relationships can be reconstructed
- steward-owned content is protected from Foundation upgrades

### 11.6 Completion Meaning

Meeting these criteria means the steward has a clear, governed, and
maintainable documentation relationship with Shared Foundations.

It does not by itself mean:

- runtime implementation is complete
- integrations are installed
- automation is enabled
- conformance evidence has been validated
- Foundation-Compatible or Foundation-Compliant status has been achieved
- public distribution is approved
- official certification or endorsement exists

Those claims require their own applicable governance, evidence, and future
processes.

## 12. Reference Summary

### Core Philosophy

- Foundation First
- Steward Autonomy
- Documentation Before Runtime
- Non-Intrusive Adoption
- Governance Consistency
- Content-Free Distribution
- Versioned Traceability

### Distribution Models

| Model | Recommended role |
|---|---|
| Reference | Cite unchanged canonical Foundation sources |
| Inheritance | Record formal steward adoption and specialization |
| Embedded Copy | Preserve an identified local copy when justified |
| Fork-and-Extend | Maintain a declared derivative for material divergence |

### Adoption Lifecycle

```text
Evaluate -> Adopt -> Inherit -> Extend -> Maintain
```

### Governing Rule

Distribute content-free, versioned Foundation contracts; adopt them through
explicit steward-owned records; preserve canonical meaning, steward autonomy,
and package boundaries; and defer runtime, installation, automation, public
release, and certification mechanisms to future governed phases.
