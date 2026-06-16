# OpenClaw Classification Metadata Schema v0.1

## 1. Purpose

This document defines the canonical descriptive metadata schema for
classifying OpenClaw foundation documents, steward-owned records, evidence
archives, memory records, operational records, references, and future
packaging materials.

The schema provides a consistent way to describe:

- the handling classification of an item
- its intended retention category
- who owns and maintains it
- its intended visibility
- its steward scope
- the requirements it supports or is governed by
- its version and lifecycle status

Metadata classification supports:

- **governance consistency:** documents and records use the same labels when
  describing handling, ownership, retention, and visibility
- **stewardship boundaries:** foundation, steward, shared-steward, and external
  material remain distinguishable
- **auditability:** evidence and historical records can retain their declared
  classification, owner, requirement references, version, and status
- **inheritance:** steward repositories can adopt the schema while preserving
  local ownership and namespace boundaries
- **packaging preparation:** future package manifests and templates can
  reference stable metadata fields without inventing incompatible labels
- **future ecosystem expansion:** new stewards, domains, record types, and
  shared services can use a common descriptive vocabulary

This schema is a documentation contract. It does not implement permissions,
access control, retention schedules, deletion policies, runtime enforcement,
packaging, integrations, automations, or public release processes.

## 2. Relationship to Existing Foundation Models

This schema complements, and does not replace:

- the OpenClaw Shared Foundations Trust Boundary and Data Classification Model
- the Canonical Steward Identifiers and Namespace Isolation model
- the OpenClaw Requirement Identifier Framework
- the Domain Precedence Model
- the Canonical Override and Exception Manifest

The Trust Boundary and Data Classification Model remains authoritative for
handling obligations, trust-boundary movement, sensitive material,
user-private data, and restricted material. This schema supplies compact,
reusable metadata labels for describing records and artifacts.

Where a source has a more specific classification, such as
`Foundation-Internal`, `Steward-Specific`, `User-Private`, or a `Sensitive`
modifier, that source classification must be preserved in an appropriate
record or extension field. A broader metadata label must never lower,
replace, or conceal the stronger source obligation.

The four metadata dimensions in this schema are independent:

- classification describes handling context
- retention describes intended persistence
- ownership describes responsibility and authority
- visibility describes the intended audience or use posture

No value in one dimension automatically determines a value in another.
Permanent data is not automatically Public. Steward-owned data is not
automatically Steward Private. Visibility does not grant permission.

## 3. Core Principles

### 3.1 Classify deliberately

Classification must reflect the item's content, source obligations, owner,
purpose, and intended use. Repository location or technical accessibility does
not establish classification.

### 3.2 Preserve the strongest obligation

Copies, summaries, exports, indexes, evidence extracts, and other derivatives
preserve the strongest applicable source classification unless a governed
review authorizes reclassification.

### 3.3 Keep dimensions separate

Classification, retention, ownership, visibility, version, and status answer
different questions. They must not be treated as interchangeable shortcuts.

### 3.4 Unknown does not mean unrestricted

An item with missing, conflicting, or uncertain metadata must not be assumed
Public, permanent, shareable, or foundation-owned. It should be reviewed under
the governing classification model.

### 3.5 Metadata does not create authority

A metadata block describes an item's declared treatment. It does not create
consent, ownership, access rights, conformance, publication approval, or
permission to cross a trust boundary.

### 3.6 Inheritance preserves ownership

Stewards may inherit the schema and foundation definitions. They do not
inherit another steward's records, identity, memory, evidence, or authority.

## 4. Classification Levels

The canonical metadata classification values are:

- Public
- Internal
- Restricted
- Steward Private

These labels are not a complete permissions model and are not necessarily a
single linear sensitivity scale. When several obligations apply, the most
protective governing rule controls.

### 4.1 Public

**Intended usage:** Material intentionally approved for unrestricted
distribution, such as published foundation architecture, approved public
documentation, synthetic examples, or released public statements.

**Sharing expectations:** May be distributed broadly after publication
authority, provenance, and content review are established. Public repository
placement alone does not establish Public classification.

**Inheritance considerations:** Public foundation definitions may be
referenced or inherited by stewards. Inheritance does not transfer foundation
ownership or make steward additions Public.

**Governance considerations:** Public classification must be intentional.
Protected source content must be removed through a reviewed transformation,
not merely hidden, renamed, or moved.

**Trust-model relationship:** Corresponds to the `Public` class in the Trust
Boundary and Data Classification Model.

### 4.2 Internal

**Intended usage:** Non-public material used within a declared organizational
or collaborative scope for development, governance, validation, planning,
operations, or review.

**Sharing expectations:** Shared only within the declared internal scope and
for the stated purpose. It is not eligible for unrestricted publication
without review and reclassification.

**Inheritance considerations:** Internal foundation material does not
automatically propagate to steward repositories. Internal steward material
does not propagate to the foundation or another steward through inheritance.

**Governance considerations:** The owner and scope must be explicit because
`Internal` alone does not identify whose internal boundary applies. More
specific source classifications must remain recorded.

**Trust-model relationship:** Commonly summarizes `Foundation-Internal` for
foundation-owned records. For steward-owned records, the more specific
`Steward-Specific` or `User-Private` source class must remain preserved rather
than being obscured by this broader label.

### 4.3 Restricted

**Intended usage:** Material requiring the narrowest handling because
disclosure, alteration, or misuse could cause immediate or substantial harm,
violate an obligation, or expose protected operational capability.

**Sharing expectations:** Not shared broadly. Any movement or reference must
follow the applicable trust-boundary, purpose, and protected-handling rules.
Protected references should be used instead of underlying secret values.

**Inheritance considerations:** Restricted content is never inherited merely
because a schema, package, repository, or requirement is inherited. A
foundation definition may describe a restricted field without containing its
value.

**Governance considerations:** Restricted classification cannot be weakened
by convenience, visibility, packaging, copying, or an undocumented local
override. Secret values remain outside ordinary documentation and metadata
examples.

**Trust-model relationship:** Corresponds to the `Restricted` class in the
Trust Boundary and Data Classification Model.

### 4.4 Steward Private

**Intended usage:** Non-public material owned by or scoped to one steward,
including steward identity content, private operating context, local evidence,
memory, configuration, and continuity records.

**Sharing expectations:** Remains within the declared steward namespace unless
a separate governed purpose and boundary crossing are approved. It is not
shared with another steward, the foundation, or the public by default.

**Inheritance considerations:** Schema definitions may be inherited, but
Steward Private values and records do not travel with foundation packages or
between stewards. Each steward supplies and governs its own content.

**Governance considerations:** The canonical steward identifier should be
declared. User-private, sensitive, or restricted obligations must remain
visible when they also apply; `Steward Private` must not be used to generalize
or weaken them.

**Trust-model relationship:** Commonly summarizes the `Steward-Specific`
class. When user-private material is involved, the `User-Private` source class
and user scope must also be preserved under the Trust Boundary and Data
Classification Model.

## 5. Retention Levels

The canonical retention values are:

- Permanent
- Operational
- Temporary
- Ephemeral

These categories describe intended persistence. They do not establish a
duration, retention schedule, disposal date, deletion method, legal hold, or
deletion policy.

### 5.1 Permanent

**Purpose:** Identify records intended to remain durable as canonical,
historical, evidentiary, or long-term reference material.

**Expected lifespan:** Indefinite or enduring relative to the owning system,
subject to applicable governance and later versioned decisions.

**Stewardship expectations:** Maintain ownership, provenance, integrity,
version history, classification, and discoverability. Permanent does not mean
immutable, current, public, or exempt from governing obligations.

### 5.2 Operational

**Purpose:** Identify records retained while they support an active operating,
governance, conformance, recovery, or stewardship need.

**Expected lifespan:** For the relevant operational lifecycle or continuing
business purpose. No fixed duration is created by this category.

**Stewardship expectations:** Maintain current ownership, status, scope, and
version. Review continued relevance when the associated operation, system,
requirement, or stewardship purpose changes.

### 5.3 Temporary

**Purpose:** Identify bounded working material created for a review,
migration, investigation, transformation, handoff, or other limited task.

**Expected lifespan:** Until the declared task, transition, or review purpose
is complete, subject to applicable governance.

**Stewardship expectations:** Name the owner and purpose, avoid treating the
record as canonical, preserve source classification, and prevent unreviewed
promotion into durable foundation or steward records.

### 5.4 Ephemeral

**Purpose:** Identify transient material intended only for a session,
operation, transaction, or similarly short-lived context.

**Expected lifespan:** Only for the bounded active context for which it was
created. This schema does not assign a numerical lifespan.

**Stewardship expectations:** Avoid unnecessary durable copies, archives, or
projections. Promotion to a more durable category requires deliberate review,
provenance, ownership, and classification.

Ephemeral retention never lowers an item's classification while the item
exists.

## 6. Ownership Types

The canonical ownership values are:

- Foundation
- Steward
- Shared Steward
- External Reference

Ownership identifies responsibility for the record and its canonical meaning.
It does not, by itself, grant access or establish intellectual-property rights.

### 6.1 Foundation

Used for canonical OpenClaw Shared Foundations contracts, definitions,
governance records, and approved foundation metadata.

Foundation ownership responsibilities include:

- maintaining the canonical definition and version
- governing changes, extensions, and deprecations
- preserving provenance and cross-document consistency
- keeping steward-private and user-private values outside foundation records

### 6.2 Steward

Used for records owned by one identified steward.

Steward ownership responsibilities include:

- declaring the canonical steward identifier
- preserving namespace and content boundaries
- maintaining local classification, version, status, and provenance
- governing local extensions and evidence
- preventing local content from being represented as canonical foundation
  content

### 6.3 Shared Steward

Used for records intentionally co-owned or jointly maintained by two or more
identified stewards under a declared shared scope.

Shared Steward ownership responsibilities include:

- identifying every participating steward
- declaring the shared purpose and accountable maintenance process
- distinguishing shared content from each steward's private content
- preserving provenance and contribution boundaries
- avoiding any implication that shared ownership transfers foundation
  authority or grants access to unrelated steward records

Shared Steward is not a default ownership type for ecosystem services,
co-location, common tooling, or similar content.

### 6.4 External Reference

Used for material whose canonical source and ownership remain outside
OpenClaw Shared Foundations and its steward repositories.

External Reference ownership responsibilities include:

- identifying the external source and, when known, its version or retrieval
  date
- distinguishing a reference from an adopted foundation requirement
- preserving attribution and applicable source obligations
- avoiding unsupported claims that OpenClaw controls, guarantees, or
  republishes the external material

An OpenClaw-maintained citation record may be internally maintained while the
referenced content remains externally owned.

## 7. Visibility Rules

Visibility values provide audience and use guidance only. They do not
implement permissions, access-control lists, capabilities, authentication, or
authorization.

The canonical visibility values are:

| Visibility | Guidance |
|---|---|
| Foundation Visible | Intended for the applicable foundation-maintenance or foundation-publication scope |
| Steward Visible | Intended for the identified steward's authorized scope |
| Cross-Steward Visible | Intended for explicitly named stewards within a declared shared purpose |
| Restricted Access | Intended only for a narrowly approved protected scope |
| Reference Only | Intended to be cited or inspected as a source, not treated as locally owned or directly editable canonical content |

Visibility guidance:

- `Foundation Visible` does not make an item Public.
- `Steward Visible` must identify the applicable steward.
- `Cross-Steward Visible` must identify participating stewards and does not
  authorize ecosystem-wide sharing.
- `Restricted Access` does not define the technical control needed to protect
  the item.
- `Reference Only` does not authorize copying, modification, redistribution,
  or execution.
- When visibility conflicts with classification or source obligations, the
  more protective governing rule controls.

## 8. Canonical Metadata Fields

The following fields form the canonical minimum metadata model.

| Field | Required | Definition |
|---|---|---|
| `Classification` | Yes | One canonical classification value: `Public`, `Internal`, `Restricted`, or `Steward Private` |
| `Retention` | Yes | One canonical retention value: `Permanent`, `Operational`, `Temporary`, or `Ephemeral` |
| `Owner` | Yes | One ownership type: `Foundation`, `Steward`, `Shared Steward`, or `External Reference` |
| `Steward` | Conditional | Canonical steward identifier or identified steward set when ownership, scope, or visibility is steward-bound; otherwise `Not Applicable` |
| `Visibility` | Yes | One visibility guidance value from Section 7 |
| `Requirement Reference` | Conditional | Canonical OpenClaw requirement ID, qualified steward-extension ID, or list of IDs governing or supported by the item |
| `Version` | Yes | Version of the classified item or metadata-bearing record, not merely the current repository version |
| `Status` | Yes | Declared lifecycle or review state appropriate to the item type |

### 8.1 Classification

`Classification` states the schema-level handling label. When the Trust
Boundary and Data Classification Model requires a more specific source class
or modifier, it must be preserved through optional metadata rather than
discarded.

### 8.2 Retention

`Retention` states the intended persistence category. It does not encode a
date, schedule, deletion trigger, or disposal instruction.

### 8.3 Owner

`Owner` states which ownership model governs the item. The field should use
the canonical ownership type, while optional metadata may name the accountable
maintainer or external source.

### 8.4 Steward

`Steward` identifies the canonical steward scope using the Canonical Steward
Identifier model. It is required for Steward ownership, Shared Steward
ownership, Steward Visible records, Cross-Steward Visible records, and
Steward Private classification.

For Shared Steward records, every participating steward must be identified.
Display names, repository names, or aliases must not replace canonical steward
identifiers.

### 8.5 Visibility

`Visibility` states the intended audience posture. It remains descriptive and
must not be interpreted as proof that technical permissions exist.

### 8.6 Requirement Reference

`Requirement Reference` links the item to one or more requirements defined
under the OpenClaw Requirement Identifier Framework.

The relationship should be stated when useful, such as:

- governed by
- implements
- validates
- provides evidence for
- inherits
- extends

A bare reference does not prove conformance or implementation.

### 8.7 Version

`Version` identifies the classified item's own declared version. Version
formats may vary by artifact type, but the value must remain unambiguous
within its owning scope.

### 8.8 Status

`Status` identifies the item's current lifecycle or review state. The allowed
status vocabulary may depend on the item type. For example, requirement
records use the lifecycle states defined by the OpenClaw Requirement
Identifier Framework.

The status vocabulary used by a record type must be documented, and status
must not be inferred from classification, retention, or repository location.

### 8.9 Optional Extension Fields

Implementations and future documentation may add optional fields such as:

- `Title`
- `Record Type`
- `Source Classification`
- `Sensitivity Modifier`
- `User Scope`
- `Purpose`
- `Provenance`
- `Accountable Maintainer`
- `Effective Date`
- `Review Date`
- `External Source`
- `Related Records`
- `Supersedes`

Optional fields must not redefine canonical fields or conceal stronger
handling obligations.

## 9. Example Metadata Blocks

The following blocks are documentation-only illustrations. They are not
machine-readable specifications, package manifests, runtime configuration, or
permission definitions. Placeholder steward identifiers do not represent real
stewards.

### 9.1 Public Foundation Document

```text
Classification: Public
Retention: Permanent
Owner: Foundation
Steward: Not Applicable
Visibility: Foundation Visible
Requirement Reference: OC-GOV-001
Version: v0.1
Status: Active
```

This example describes an approved public foundation document. The requirement
reference identifies a relationship but does not establish conformance.

### 9.2 Internal Foundation Evidence Record

```text
Classification: Internal
Retention: Operational
Owner: Foundation
Steward: Not Applicable
Visibility: Foundation Visible
Requirement Reference: OC-GOV-014
Version: review-2026-01
Status: Under Review
Source Classification: Foundation-Internal
```

This example preserves the more specific trust-model classification while
using the canonical metadata fields.

### 9.3 Steward-Private Governance Record

```text
Classification: Steward Private
Retention: Operational
Owner: Steward
Steward: <canonical-steward-id>
Visibility: Steward Visible
Requirement Reference: OC-GOV-018
Version: v1.2
Status: Active
Source Classification: Steward-Specific
```

This example identifies a local record without moving its contents into the
foundation or another steward repository.

### 9.4 Shared-Steward Review Record

```text
Classification: Internal
Retention: Temporary
Owner: Shared Steward
Steward: <canonical-steward-id-a>, <canonical-steward-id-b>
Visibility: Cross-Steward Visible
Requirement Reference: OC-MCP-022
Version: review-01
Status: Open
Purpose: Bounded joint conformance review
```

This example describes a declared shared scope. It does not grant either
steward access to unrelated private records.

### 9.5 Restricted Reference Record

```text
Classification: Restricted
Retention: Operational
Owner: External Reference
Steward: Not Applicable
Visibility: Reference Only
Requirement Reference: OC-REC-011
Version: source-version-identified-by-owner
Status: Current Reference
External Source: Protected source reference only
```

This example records a protected reference without embedding the underlying
restricted value or source content.

### 9.6 Ephemeral Steward Working Record

```text
Classification: Steward Private
Retention: Ephemeral
Owner: Steward
Steward: <canonical-steward-id>
Visibility: Steward Visible
Requirement Reference: Not Applicable
Version: session-local
Status: Transient
Source Classification: Steward-Specific
```

This example does not define a deletion schedule. It only describes the
record's intended transient role.

## 10. Extension Rules

Future classification, retention, ownership, visibility, or metadata-field
values may be added only through versioned foundation governance.

An extension proposal must define:

- the gap that existing values cannot express
- the metadata dimension being extended
- the new value's precise meaning
- its relationship to every existing value in that dimension
- inheritance and steward-scope behavior
- compatibility and migration effects
- interaction with the Trust Boundary and Data Classification Model
- at least two documentation-only examples

Extensions must:

- preserve the meaning of existing values
- avoid aliases that differ only in wording
- avoid weakening an existing classification or trust-boundary obligation
- remain distinguishable from steward-local vocabulary
- define how older consumers should treat an unknown value
- use a version change when canonical meaning or required fields change

Unknown canonical values should be treated as unresolved metadata and reviewed
under the most protective plausible applicable rules. They must not silently
default to Public, unrestricted, foundation-owned, or permanent.

Stewards may define local metadata extensions in their own namespace. Local
extensions:

- must not redefine a canonical field or value
- must remain clearly identified as steward-owned
- must not be represented as foundation requirements
- must not weaken inherited foundation obligations
- should retain the canonical minimum fields for interoperability

## 11. Steward Inheritance Guidance

A steward repository may inherit this schema by referencing its canonical
document name and version and by using the canonical fields and values without
modifying their foundation definitions.

An inheritance declaration should identify:

- schema name and version
- steward's canonical identifier
- adopted canonical fields
- any steward-local optional fields
- local record types using the schema
- any documented compatibility limitations

Steward repositories may:

- apply the schema to local documents, evidence, memory, and operational
  records
- add stricter local classification or review practices
- define namespaced optional fields
- use qualified steward requirement IDs in `Requirement Reference`
- omit a conditional field only when its applicability is genuinely absent

Steward repositories must:

- preserve canonical field and value meanings
- retain steward namespace and ownership on local records
- keep foundation definitions separate from populated steward-private values
- preserve stronger source classifications and modifiers
- distinguish inherited schema from local extensions
- reassess metadata when an item changes owner, purpose, source obligation,
  version, or trust boundary

Steward repositories must not:

- edit the foundation definition and present it as unchanged inheritance
- copy another steward's metadata values or records as defaults
- use inheritance to transfer private content or ownership
- treat visibility guidance as implemented permission
- treat retention categories as deletion schedules
- classify material Public merely because it appears in a package or
  repository

Foundation schema updates may add fields or values through versioned
governance. A steward should record the schema version it has adopted and
review compatibility before adopting a newer version. Steward-owned content
remains under steward governance during schema upgrades.

## 12. Reference Summary

### Canonical Values

| Dimension | Values |
|---|---|
| Classification | Public, Internal, Restricted, Steward Private |
| Retention | Permanent, Operational, Temporary, Ephemeral |
| Ownership | Foundation, Steward, Shared Steward, External Reference |
| Visibility | Foundation Visible, Steward Visible, Cross-Steward Visible, Restricted Access, Reference Only |

### Canonical Minimum Fields

| Field | Requirement |
|---|---|
| `Classification` | Required |
| `Retention` | Required |
| `Owner` | Required |
| `Steward` | Conditional |
| `Visibility` | Required |
| `Requirement Reference` | Conditional |
| `Version` | Required |
| `Status` | Required |

The governing rule is: classify deliberately, preserve the strongest source
obligation, keep classification, retention, ownership, and visibility
distinct, and inherit the schema without inheriting another steward's private
content or authority.
