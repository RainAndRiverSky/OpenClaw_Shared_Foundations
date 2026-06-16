# OpenClaw Requirement Identifier Framework v0.1

## 1. Purpose

This document defines the canonical identifier framework for requirements in
OpenClaw Shared Foundations and for requirements inherited or extended by
future steward repositories.

Requirement identifiers provide stable, compact references to normative
statements across versions, domains, reviews, packages, and implementation
contexts. They allow a requirement to remain traceable even when document
headings, section numbers, filenames, or surrounding explanatory text change.

OpenClaw uses requirement identifiers to support:

- **governance validation:** policies, decisions, exceptions, and approvals can
  identify the exact requirement they govern
- **conformance reviews:** assessors can map each applicable requirement to its
  status, evidence, finding, and accountable owner
- **inheritance tracking:** steward repositories can declare which foundation
  requirements they inherit without copying or redefining them
- **steward packaging:** future packages can identify the requirements their
  contracts, defaults, schemas, and checklists address
- **future audits:** historical records can preserve which requirement and
  lifecycle state applied at the time of an action or assessment
- **cross-document references:** architecture, governance, recovery, and
  validation documents can refer to the same requirement unambiguously

This framework assigns identifier structure and governance rules. It does not
create runtime enforcement, a requirement registry, packaging assets,
integrations, automations, or steward-specific requirements.

## 2. Core Principles

### 2.1 One identifier, one requirement

Each identifier represents one discrete normative requirement. Multiple
independently testable obligations should receive separate identifiers.

### 2.2 Identifiers are persistent

Once published as Active, an identifier must not be renamed, reassigned, or
reused for a different requirement. Editorial movement does not change the
identifier.

### 2.3 Meaning changes require governance

Clarifications that do not change the obligation may retain the identifier.
Material changes to scope, obligation, applicability, or validation criteria
require a new identifier and an explicit supersession relationship.

### 2.4 Domain ownership is explicit

An identifier's domain prefix identifies the foundation domain that owns the
requirement. The prefix does not grant runtime authority or override the
OpenClaw Domain Precedence Model.

### 2.5 References do not prove conformance

Citing, inheriting, or implementing a requirement does not by itself establish
conformance. Applicability, evidence, exceptions, validation, and the assessed
foundation version remain necessary.

### 2.6 Steward content remains separate

Foundation identifiers identify shared contracts. They do not absorb
steward-owned identity, memory, permissions, recovery state, or local policy
into the foundation layer.

## 3. Canonical ID Structure

### 3.1 Canonical Pattern

A foundation requirement identifier uses this form:

```text
OC-<DOMAIN>-<NUMBER>
```

Where:

- `OC` identifies the OpenClaw requirement namespace
- `<DOMAIN>` is an approved uppercase domain prefix
- `<NUMBER>` is a zero-padded three-digit allocation from `001` through `999`

The canonical pattern is:

```text
^OC-[A-Z][A-Z0-9]{1,7}-[0-9]{3}$
```

Canonical identifiers use uppercase ASCII characters, ASCII hyphens, and no
spaces. Leading zeroes are required. The identifier is treated as an opaque
string, not as a decimal value or document section number.

Examples:

```text
OC-ID-001
OC-ID-002

OC-MEM-001
OC-MEM-002

OC-GOV-001
OC-GOV-002

OC-MCP-001
OC-MCP-002

OC-REC-001
OC-REC-002

OC-OBS-001
OC-OBS-002
```

### 3.2 Requirement Record

Every assigned requirement identifier should have a canonical record
containing at least:

- requirement ID
- normative requirement text
- owning domain
- lifecycle state
- foundation or steward source and version
- applicability
- effective date
- validation or evidence expectation
- supersedes or superseded-by relationship, when applicable

Optional metadata may include rationale, risk classification, exception
policy, related identifiers, change history, and accountable governance owner.
Metadata supports the requirement but does not replace its canonical text.

### 3.3 Normative Language

Canonical requirement text should use explicit normative terms such as
`must`, `must not`, `required`, `should`, `should not`, or `may`. The source
document should define any distinction between mandatory, recommended, and
optional requirements.

An identifier should not be assigned to a heading, rationale, example, note,
or broad topic unless that item contains a discrete normative obligation.

## 4. Domain Allocation Rules

The following prefixes are canonical for the initial OpenClaw foundation
domains:

| Prefix | Domain | Allocation scope |
|---|---|---|
| `OC-ID` | Identity | Identity structure, ownership, provenance, namespace association, boundaries, and identity recovery anchors |
| `OC-MEM` | Memory | Durable memory, provenance, retrieval, retention, deletion, classification, and memory isolation |
| `OC-GOV` | Governance | Authority, consent, policy, conformance, exceptions, audit, precedence, change control, and cross-domain governance |
| `OC-MCP` | MCP | MCP capability declaration, gating, permissions, execution boundaries, evidence, and revocation |
| `OC-REC` | Recovery | Recovery triggers, restoration order, integrity checks, rollback, degraded operation, and recovery evidence |
| `OC-OBS` | Obsidian | Obsidian vault projections, note provenance, links, indexes, isolation, and synchronization boundaries |

Allocation rules:

1. Assign the requirement to the domain that owns the normative obligation,
   not merely the domain where the requirement is cited.
2. Cross-domain requirements should normally be owned by Governance and link
   to related domain requirements.
3. Do not duplicate one obligation under several prefixes. Use
   cross-references when multiple domains are affected.
4. Domain prefixes are stable once requirements have been published beneath
   them.
5. `ID` means Identity in this framework. It does not mean a generic
   identifier category.

### 4.1 Future Reserved Domains

Future foundation domains may receive a new `OC-<DOMAIN>` prefix only through
versioned foundation governance. A proposal must define:

- the domain name and boundary
- the requested prefix
- why an existing domain cannot own the requirements
- interactions with precedence, conformance, exceptions, and inheritance
- migration or alias treatment for any provisional references

Unregistered prefixes are reserved and must not be presented as canonical
OpenClaw foundation prefixes. Prefixes must be unique, must not be visually
confusable with an existing prefix, and must not redefine an existing domain.

Experimental documents may use an explicitly marked provisional label, but
that label does not become canonical until approved. Provisional labels must
not consume or imply permanent requirement IDs.

## 5. Reserved Numbering Policy

Each approved domain prefix has an independent three-digit number space.
Numbers are allocated within the owning domain as follows:

| Range | Allocation |
|---|---|
| `001-099` | Foundation Core |
| `100-199` | Future Foundation Expansion |
| `200-499` | Steward Extensions |
| `500-999` | Reserved |

### 5.1 Foundation Core: 001-099

This range is for the initial stable requirements necessary to define the
domain's foundation contract. Allocation should leave reasonable gaps when
groups of related requirements are expected.

### 5.2 Future Foundation Expansion: 100-199

This range is for later canonical foundation requirements added through
versioned governance. Addition to this range does not make a requirement
automatically mandatory; applicability and normative strength must be declared
in the requirement record.

### 5.3 Steward Extensions: 200-499

This range is for steward-owned requirements that extend an existing
foundation domain. Because separate stewards may allocate the same local
number, a steward extension must be referenced with its canonical steward
identifier or another approved globally unique steward namespace:

```text
<CSID>::OC-<DOMAIN>-<NUMBER>
```

Example structural form:

```text
<canonical-steward-id>::OC-MEM-200
```

The qualified form is the complete steward-extension reference. A bare
`OC-MEM-200` reference is ambiguous and must not be represented as a canonical
foundation requirement.

Steward extension numbers:

- are allocated and governed by the owning steward
- must not redefine or replace foundation requirements
- may impose stricter local controls
- must remain distinguishable from inherited foundation requirements
- do not become foundation requirements through use, publication, or reuse

### 5.4 Reserved: 500-999

This range is held for future governance decisions, migrations, ecosystem
coordination, or other uses not defined in v0.1. Requirements must not be
allocated from this range without a versioned update to this framework.

### 5.5 General Allocation Rules

- Allocate identifiers deliberately; sequential density is not required.
- Do not renumber requirements to close gaps.
- Do not reuse identifiers from Deprecated, Superseded, or Retired
  requirements.
- A withdrawn Draft number should remain recorded as unassigned or withdrawn
  when it has appeared in review materials.
- Number ranges do not indicate precedence, severity, applicability, or
  lifecycle state.

## 6. Requirement Lifecycle

Every requirement record must declare exactly one current lifecycle state.

### 6.1 Draft

A Draft requirement is proposed and under review. It may be cited for design
or planning only when clearly labeled Draft. It must not be used as the sole
basis for a conformance or compliance claim.

A Draft may be revised materially before activation. If its identifier has
been circulated, withdrawal should be recorded to prevent later accidental
reuse.

### 6.2 Active

An Active requirement is approved, effective, and available for applicability
and conformance assessment. Its canonical text, source version, and effective
date must be identifiable.

### 6.3 Deprecated

A Deprecated requirement remains valid for declared legacy or transition
scopes but is discouraged for new adoption. Its record should state:

- why it is deprecated
- the affected scope
- the preferred replacement, if any
- the transition or review window

Deprecation does not erase prior applicability or evidence obligations.

### 6.4 Superseded

A Superseded requirement has been replaced by one or more newer requirements.
Its record must identify the replacement IDs and effective relationship. The
replacement requirement should identify the requirement it supersedes.

Supersession is not assumed to be one-to-one. A requirement may be split,
combined, or replaced by requirements in another domain. Historical
assessments continue to reference the requirement version that applied at the
time.

### 6.5 Retired

A Retired requirement is no longer applicable to new or current scopes. It is
preserved for history, audit, migration, and interpretation of earlier
records. A retired identifier must never be reassigned.

### 6.6 Lifecycle Transitions

The normal progression is:

```text
Draft -> Active -> Deprecated -> Superseded or Retired
```

Governance may move an Active requirement directly to Superseded or Retired
when justified. Lifecycle changes must be versioned, dated, and attributable.
Changing lifecycle state does not alter the identifier.

## 7. Cross-Reference Rules

Future documents may reference requirement IDs in prose, tables, manifests,
checklists, evidence maps, findings, decisions, and package documentation.

### 7.1 First and Subsequent References

The first material reference in a document should include the identifier and a
short human-readable label or summary:

```text
OC-MEM-014 (memory provenance preservation)
```

Later references may use the identifier alone when the context remains clear.
The canonical requirement text must not be reconstructed from the short label.

### 7.2 Version and Source

When applicability could differ by release, a reference must identify the
governing foundation version or canonical source version:

```text
OC-GOV-021, OpenClaw Shared Foundations v0.2
```

Historical evidence and audit records should preserve the version assessed,
not silently resolve to the newest wording.

### 7.3 Multiple Requirements

List discrete identifiers rather than inventing undocumented ranges.
`OC-MEM-001 through OC-MEM-009` is valid only when every identifier in that
range is intentionally included. Otherwise, enumerate the applicable IDs.

### 7.4 Relationship Labels

Documents should state the relationship when it is not obvious. Recommended
labels include:

- `implements`
- `validates`
- `provides evidence for`
- `constrained by`
- `inherits`
- `extends`
- `excepts from`
- `supersedes`
- `related to`

A cross-reference must not imply implementation, evidence, approval, or
conformance unless that relationship is explicitly declared and supported.

### 7.5 Findings and Exceptions

Conformance findings, exceptions, waivers, and remediation records must cite
the exact affected requirement IDs. Broad domain-only references are
insufficient when canonical IDs exist.

An exception changes the approved treatment of a requirement within a defined
scope; it does not modify the canonical requirement or identifier.

### 7.6 Steward Extension References

Foundation requirements use their bare canonical IDs. Steward extensions in
the `200-499` range use the qualified steward form:

```text
<CSID>::OC-GOV-200
```

Documents must not remove the steward qualifier when doing so could make a
local extension appear to be a foundation requirement.

## 8. Steward Inheritance Guidance

A steward repository inherits a foundation requirement by referencing the
canonical requirement ID, governing foundation version, applicability, and
local treatment. It does not need to copy or rewrite the canonical requirement
text.

An inheritance record should identify:

- the canonical foundation requirement ID
- the foundation version
- applicability to the steward
- local status, such as adopted, not applicable, excepted, or pending
- implementation or policy reference, when one exists
- evidence reference, when assessment is claimed
- any stricter steward extension

Steward repositories must:

- preserve the original foundation identifier and meaning
- keep inherited requirements distinct from steward-owned extensions
- reference approved exceptions without editing the foundation requirement
- use a qualified `200-499` identifier for local normative additions
- record the foundation version used for assessment or packaging
- reassess applicability when a foundation requirement is superseded or the
  adopted foundation version changes

Steward repositories must not:

- renumber a foundation requirement
- redefine foundation text under the same identifier
- mark a foundation requirement globally Deprecated, Superseded, or Retired
- use a local extension to weaken a mandatory foundation protection while
  claiming unchanged conformance
- present a steward extension as canonical merely because several stewards
  adopt it

A stricter local rule may coexist with an inherited foundation requirement.
The inheritance record should cite both:

```text
inherits: OC-GOV-018
extended-by: <canonical-steward-id>::OC-GOV-200
```

If a steward cannot satisfy a foundation requirement, it must record the
applicable conformance effect and use the canonical exception process when an
exception is permitted. Editing the inherited wording is not an exception
mechanism.

## 9. Governance and Maintenance

Canonical foundation requirement IDs may be assigned, activated, deprecated,
superseded, or retired only through versioned OpenClaw foundation governance.
The governing change record should identify:

- identifiers affected
- previous and new lifecycle states
- effective date
- rationale
- compatibility and migration effects
- replacement identifiers, when applicable

Future registries, schemas, or packaging documents may operationalize this
framework, but they must preserve its identifier structure, lifecycle history,
domain ownership, range allocation, and steward qualification rules.

Conflicts between a requirement and another foundation contract are resolved
through the canonical Domain Precedence Model and Override and Exception
Manifest. The numeric value of an identifier never resolves precedence.

## 10. Reference Summary

| Element | Canonical rule |
|---|---|
| Foundation form | `OC-<DOMAIN>-<NUMBER>` |
| Identity prefix | `OC-ID` |
| Memory prefix | `OC-MEM` |
| Governance prefix | `OC-GOV` |
| MCP prefix | `OC-MCP` |
| Recovery prefix | `OC-REC` |
| Obsidian prefix | `OC-OBS` |
| Foundation core | `001-099` |
| Foundation expansion | `100-199` |
| Steward extensions | `200-499`, steward-qualified |
| Reserved | `500-999` |
| Lifecycle states | Draft, Active, Deprecated, Superseded, Retired |
| Reuse rule | Published identifiers are never reassigned |

This v0.1 framework establishes the identifier foundation for later Phase 8C
steward packaging documents. It defines references and governance only; it
does not generate packages or modify steward implementations.
