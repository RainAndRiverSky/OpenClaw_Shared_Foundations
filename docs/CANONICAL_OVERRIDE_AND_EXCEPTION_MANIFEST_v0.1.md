# OpenClaw Shared Foundations Canonical Override and Exception Manifest v0.1

## 1. Purpose

This document defines the canonical governance framework for proposing,
approving, applying, inheriting, auditing, reviewing, and retiring overrides
and exceptions across OpenClaw Shared Foundations, individual stewards, public
deployments, and future steward ecosystems.

An **override** is an authorized instruction that changes which otherwise valid
rule or configuration controls a specific decision. An **exception** is the
documented governance record permitting a bounded deviation from a normal
requirement. An override must be supported by an approved exception unless an
existing canonical rule already authorizes the override directly.

This manifest is architecture documentation only. It does not grant authority,
change runtime policy, or implement enforcement.

## 2. Why Exceptions Exist

Canonical rules cannot predict every deployment, incident, recovery event,
compatibility constraint, or steward-specific need. A controlled exception
process allows legitimate deviations without turning informal workarounds into
hidden policy.

Exceptions exist to:

- preserve safe operation during emergencies and recovery
- accommodate stricter steward-specific requirements
- support bounded compatibility transitions
- permit reversible experiments
- document public deployment constraints
- make unavoidable deviations visible and reviewable
- preserve accountability when the normal path cannot be followed

Exceptions do not exist to make inconvenient protections optional. They must
not be used to conceal non-conformance, avoid review, acquire unrelated
authority, or convert temporary access into a permanent entitlement.

## 3. Core Governance Principles

### 3.1 Deny by default

No deviation exists until its exception record is approved by the required
authority. Silence, prior behavior, technical capability, urgency, or
availability does not constitute approval.

### 3.2 Narrowest effective scope

Every exception must identify the smallest affected steward, namespace,
domain, capability, data class, environment, and time window capable of
meeting its stated need.

### 3.3 Least authority

An exception grants only the authority explicitly listed. It does not imply
adjacent permissions, cross-steward access, credential access, or permission
to alter unrelated policy.

### 3.4 Separation of duties

The requester, approver, implementer, reviewer, and retiree are distinct roles
when risk is material. No person, steward, tool, or automated process may
unilaterally create, approve, and close its own high-risk exception.

### 3.5 Time bounds and review

Temporary, emergency, recovery, and experimental exceptions require an expiry
or exit condition. Permanent exceptions require a recurring review date and
justification for why the canonical rule should not be changed instead.

### 3.6 Reversibility

An exception must define rollback, cleanup, and verification. Irreversible
deviations require stronger approval and may be invalid when they affect
protected identity, private memory, consent, isolation, or source history.

### 3.7 No hidden inheritance

Exceptions do not propagate to other stewards, environments, descendants,
forks, or future versions unless inheritance is explicit, justified, and
approved at the receiving scope.

### 3.8 Precedence remains controlling

The Domain Precedence Model determines which domain may authorize a
deviation. An exception cannot grant a lower-precedence domain authority over
a subject it does not own.

### 3.9 Stronger protection remains valid

A steward may apply stricter controls without seeking an exception when the
foundation contract allows tightening. An exception is needed only when the
change deviates from a mandatory requirement or a declared compatibility
profile.

### 3.10 Evidence before closure

An exception is not retired merely because its intended action ended. Closure
requires evidence that access, data, configuration, temporary artifacts, and
affected state were restored or reconciled.

### 3.11 Discoverability without disclosure

Exception existence, owner, scope, status, and decision history must remain
discoverable. Sensitive details must be minimized, classified, redacted, or
referenced through protected records rather than exposed in public logs.

### 3.12 Exceptions are not precedents by default

Approval of one exception does not establish policy for another case. Repeated
similar exceptions trigger governance review of the underlying rule.

## 4. Override Categories

An override category describes why a controlling rule is being displaced.
Each approved exception must name one primary override category and may name
secondary categories when necessary.

### 4.1 Emergency Override

Used to contain an active, material threat to safety, privacy, integrity,
availability, or steward isolation when waiting for the standard approval
cycle would increase harm.

Requirements:

- a declared incident or equivalent documented trigger
- the shortest practical duration
- immediate containment scope
- no expansion beyond incident response
- prompt retrospective approval and review
- automatic expiry unless affirmatively renewed

Emergency authority may pause capabilities, isolate systems, revoke access, or
move a steward into degraded mode. It may not fabricate consent, disclose
private memory for convenience, or permanently alter steward identity.

### 4.2 Recovery Override

Used during a declared recovery state to temporarily change normal operating
order, disable suspect components, select approved recovery anchors, restore a
verified snapshot, or enter degraded mode.

Requirements:

- an identified recovery trigger
- the affected steward and namespace
- approved recovery authority
- snapshot or evidence preservation where possible
- rollback and verification criteria
- termination when recovery is verified or abandoned

A recovery override cannot restore revoked permissions, cross steward
boundaries, or treat an unverified backup as authoritative.

### 4.3 Steward-Specific Override

Used for a bounded deviation required by one steward's operating scope,
environment, risk posture, or domain method.

This override remains local to that steward unless separately adopted
elsewhere. Stricter controls that already conform to the foundation do not
require an override.

### 4.4 Foundation Override

Used when Shared Foundations governance supersedes a weaker or conflicting
local behavior for systems claiming conformance.

A foundation override may enforce mandatory protections, reject an invalid
compatibility claim, or require migration from a deprecated contract. It may
not edit steward-owned identity or private memory, grant capabilities, or
claim ownership of a steward repository.

### 4.5 Public Deployment Override

Used when a public or open-source distribution must deviate from a default
because of public hosting, disclosure, contribution, licensing, security, or
multi-tenant conditions.

Public deployment overrides may narrow exposed features or remove private
integration assumptions. They may not publish private steward content,
weaken required isolation, or imply official compatibility without approval.

### 4.6 Compatibility Override

Used for a bounded transition when a steward, adapter, vault, schema, or
downstream implementation cannot yet satisfy a newer contract.

Requirements:

- current and target versions
- exact incompatible requirements
- impact on conformance claims
- compensating controls
- migration plan and deadline
- rollback or continued-operation plan

Compatibility overrides must not become indefinite substitutes for migration.

## 5. Exception Categories

An exception category describes its lifecycle and policy status. Every
exception must use exactly one category.

### 5.1 Temporary

A time-bound deviation for a known operational need.

Required controls:

- start and expiry timestamps or explicit exit condition
- named owner
- rollback plan
- no automatic renewal
- review before extension

Expiration returns the affected scope to the canonical rule. An expired
exception cannot continue through implied consent.

### 5.2 Permanent

A continuing deviation with no planned operational end date.

Permanent does not mean unreviewed or irrevocable. It requires:

- a durable rationale
- a recurring review schedule
- a named accountable owner
- compatibility and inheritance statements
- retirement criteria
- analysis of whether the canonical rule should instead be amended

Permanent exceptions should be rare. Repeated permanent exceptions indicate
that the foundation contract or compatibility profile may need revision.

### 5.3 Experimental

A reversible, isolated deviation used to test an architectural assumption,
optional component, or proposed governance change.

It requires:

- a hypothesis and success criteria
- a limited test population and environment
- prohibited-data and prohibited-capability boundaries
- observation and rollback plans
- an expiry date
- a rule that successful experimentation does not automatically authorize
  production adoption

### 5.4 Deprecated

An exception retained for historical traceability but no longer valid for new
use. It may identify a replacement, migration path, retirement deadline, and
affected legacy scopes.

Deprecated exceptions:

- cannot authorize new deployments
- cannot be copied into new steward packages
- remain discoverable for audit and recovery history
- must distinguish remaining legacy use from retired use

## 6. Approval Requirements

### 6.1 Governance Roles

Every adopting scope must assign named people or accountable groups to these
roles before exceptions can be approved:

- **Requester:** proposes the exception and supplies evidence.
- **Scope Owner:** owns the affected steward, domain, repository, or
  deployment.
- **Policy Owner:** owns the canonical requirement being changed.
- **Data Owner:** approves effects on private, shared, restricted, or
  user-controlled data.
- **Capability Owner:** approves effects on MCP or other operational
  capabilities.
- **Recovery Authority:** approves actions performed during recovery.
- **Security or Privacy Reviewer:** reviews material confidentiality,
  integrity, isolation, or public exposure risk.
- **Foundation Governance Maintainer:** approves foundation-wide,
  cross-steward, conformance, and official public-project exceptions.
- **Auditor or Independent Reviewer:** verifies evidence and lifecycle
  compliance without exercising the exception.

One accountable party may hold multiple low-risk roles, but material or
high-risk exceptions require separation between requester and approver.

### 6.2 Who May Create an Exception

An exception proposal may be created by:

- a steward owner or authorized steward maintainer
- a domain, data, capability, recovery, security, or privacy owner
- a foundation governance maintainer
- an authorized public deployment maintainer
- an incident responder acting within an established emergency process
- an automated system only as an unapproved draft or emergency alert

A steward, model, tool, or automated process cannot approve its own proposal.

### 6.3 Who May Approve an Exception

Approval must include the Policy Owner and Scope Owner. Additional approval is
required when the exception affects:

| Impact | Additional required approval |
|---|---|
| Private, restricted, or user-controlled data | Data Owner and privacy review |
| MCP writes, destructive actions, or infrastructure mutation | Capability Owner and governance review |
| Recovery anchors, restore, deletion, or rollback | Recovery Authority |
| Identity spine or identity-change process | Identity owner and foundation governance review |
| Cross-steward scope or shared services | Every affected Scope Owner and foundation governance review |
| Public release, conformance, or official compatibility claims | Foundation Governance Maintainer |
| Security boundaries or active incidents | Security reviewer or authorized incident authority |
| Permanent weakening of a mandatory protection | Not approvable as an exception; amend the canonical rule or declare non-conformance |

Emergency overrides may begin with the authorized incident role when delay
would increase harm. They require retrospective approval by the normal owners
within the documented review window. Failure to obtain it ends the override.

### 6.4 Who May Retire an Exception

An exception may be retired by:

- the Scope Owner after verifying restoration and cleanup
- the Policy Owner when the exception is no longer required
- the Recovery Authority after verified recovery completion
- the Foundation Governance Maintainer for foundation-wide or official public
  exceptions
- an auditor or security authority through escalation when the exception is
  expired, invalid, compromised, or being misused

Retirement must not destroy the exception record. It changes status, revokes
authority, and preserves the audit history.

### 6.5 Renewal and Modification

Renewal is a new approval decision. Material changes to scope, duration,
capabilities, data classes, inheritance, or risk require a new version or a
replacement exception. Approval cannot be inferred from the earlier record.

## 7. Inheritance Rules

### 7.1 General Rule

Exceptions are non-inheritable by default. Contract inheritance does not copy
temporary authority, private context, approvals, credentials, or local
deviations.

### 7.2 From Shared Foundations

A foundation exception may propagate only when its record:

- explicitly identifies the affected conformance profile or foundation
  version
- states whether adoption is mandatory, optional, or informational
- identifies affected domains and migration requirements
- contains no steward-private content
- defines downstream acceptance, rejection, and reporting behavior

Foundation overrides that enforce mandatory protections apply to conforming
systems. Permission-expanding exceptions require separate steward acceptance
and local approval.

### 7.3 From Individual Stewards

A steward exception remains within that steward's namespace, environment, and
declared deployment. It does not propagate:

- to another steward
- to a shared service used by other stewards
- from test to production
- from standalone mode to ecosystem or Harbor mode
- to a future steward package
- through copied configuration or memory

Another steward may adopt the same pattern only through its own exception
record and approval.

### 7.4 From Future Steward Ecosystems

An ecosystem may define a shared exception profile for common infrastructure,
but each exception must distinguish:

- ecosystem governance authority
- participating stewards
- local opt-in or mandatory status
- shared-service scope
- data and namespace boundaries
- withdrawal and retirement behavior
- effect on compatibility claims

An ecosystem exception cannot authorize access to a steward's private memory,
identity, credentials, or write capabilities without that steward's explicit
scoped approval.

### 7.5 Forks and Downstream Projects

Public forks may retain exception records for history or define their own.
They must not present downstream exceptions as canonical OpenClaw approvals.
Official status and compatibility claims remain governed by the applicable
public governance process.

## 8. Documentation Requirements

Every exception record must contain:

1. **Exception ID:** stable, unique, namespace-qualified identifier.
2. **Title:** concise description of the deviation.
3. **Status:** proposed, approved, active, suspended, expired, retired,
   rejected, or deprecated.
4. **Exception category:** temporary, permanent, experimental, or deprecated.
5. **Override category:** emergency, recovery, steward-specific, foundation,
   public deployment, or compatibility.
6. **Canonical rule affected:** exact document, version, section, requirement,
   or policy identifier.
7. **Reason and evidence:** the need, constraints, and alternatives considered.
8. **Scope:** stewards, namespaces, domains, repositories, environments,
   capabilities, data classes, and users affected.
9. **Explicit exclusions:** what the exception does not authorize.
10. **Precedence basis:** authority under the Domain Precedence Model.
11. **Risk assessment:** safety, privacy, security, identity, memory,
    recovery, compatibility, and public-governance effects.
12. **Compensating controls:** protections replacing or narrowing the affected
    requirement.
13. **Start, expiry, and review dates:** including timezone or unambiguous
    date format.
14. **Trigger and exit criteria:** conditions that activate and terminate the
    exception.
15. **Rollback and cleanup plan:** restoration steps and responsible owner.
16. **Verification evidence:** proof required before activation and closure.
17. **Inheritance statement:** non-inheritable or exact propagation rules.
18. **Compatibility statement:** conformance impact and required disclosures.
19. **Owners and approvers:** accountable roles and approval timestamps.
20. **Audit location:** protected reference to decision and activity records.
21. **Revision history:** changes, renewals, suspensions, and retirement.
22. **Sensitive-data handling:** classification, redaction, access, and
    retention requirements for the record itself.

The exception record must not contain credentials, unnecessary private
memory, secret values, or unrestricted copies of sensitive evidence.

## 9. Audit Requirements

### 9.1 Canonical Register

Every governance scope must maintain a discoverable exception register. The
register may be public, internal, or split by classification, but it must allow
authorized reviewers to identify:

- active, expiring, expired, suspended, and retired exceptions
- owner and affected scope
- canonical rule affected
- approval and review status
- inheritance and compatibility impact
- protected location of supporting evidence

### 9.2 Lifecycle Events

The audit history must record:

- proposal
- review requests and decisions
- approval or rejection
- activation and use
- material scope changes
- suspension
- renewal
- expiry
- rollback and cleanup
- verification
- retirement or deprecation

### 9.3 Usage Audit

When an exception authorizes an action, material uses should record the actor,
time, target, exception ID, action class, result, and relevant scope. Logs
should summarize sensitive arguments and results rather than reproduce private
content.

### 9.4 Review Cadence

- Emergency exceptions: reviewed immediately after containment and before any
  extension.
- Recovery exceptions: reviewed at recovery-state transitions and closure.
- Temporary exceptions: reviewed before expiry or renewal.
- Experimental exceptions: reviewed at defined checkpoints and before
  production consideration.
- Permanent exceptions: reviewed on a recurring schedule.
- Deprecated exceptions: reviewed until all remaining legacy use is retired.

### 9.5 Tamper Evidence and Retention

Exception decisions and audit history should be append-preserving,
version-controlled, or otherwise tamper-evident. Retention follows applicable
governance and data classification. Retirement does not authorize deletion of
required evidence.

### 9.6 Audit Failure

If required audit evidence is unavailable, untrustworthy, or incomplete, the
exception must be suspended or restricted to a safe degraded state until
review. Audit failure cannot be cured by undocumented reconstruction.

## 10. Invalid Exceptions

The following exceptions must never be permitted:

- an exception that fabricates or assumes user consent
- an exception that grants access to another steward's private memory,
  identity, namespace, credentials, or permissions without explicit authority
- an exception that allows one steward to approve itself for another
- an exception that removes provenance from durable memory
- an exception that makes privileged or destructive operations unauditable
- an exception that disables deletion, retention, or recovery obligations
  without a controlling legal or governance process and documented handling
- an exception that rewrites source history to hide a conflict or incident
- an exception that restores revoked permissions from a backup
- an exception that permanently replaces steward-owned identity through
  foundation inheritance
- an exception that publishes private content as a public compatibility
  fixture
- an exception that treats MCP availability as authorization
- an exception that silently merges steward namespaces
- an exception that has unlimited scope, duration, or unspecified authority
- an exception approved only by the requester when material risk is present
- an exception whose compensating control is merely a promise to be careful
- an exception that suppresses known corruption while claiming verified
  recovery
- an exception that claims canonical or official status without public
  governance approval
- an exception created to evade an applicable higher authority or controlling
  external obligation

When a requested deviation requires one of these outcomes, the request must be
rejected, the system must declare non-conformance, or the canonical rule must
be reconsidered through formal change governance.

## 11. Examples

### Example 1: Emergency capability shutdown

An MCP server begins returning cross-namespace results. An authorized incident
responder activates a temporary emergency override that disables the server
for all affected stewards. The override narrows capability rather than
expanding access, records the incident, and expires after isolation is
verified.

### Example 2: Recovery with exact retrieval only

A steward's semantic index is corrupt. A recovery authority approves a
temporary recovery override disabling semantic retrieval while exact canonical
records remain available. Closure requires index rebuild verification and
confirmation that no source records changed.

### Example 3: Stricter steward retention

A steward shortens its private-memory retention below the foundation maximum.
Because the foundation permits stricter controls, no exception is required.
The steward documents the local policy as a conforming extension.

### Example 4: Longer retention for a regulated record

A deployment must retain a narrowly defined audit class longer than its normal
policy. A permanent steward-specific exception names the controlling
obligation, data class, access controls, recurring review, and deletion trigger.
It does not extend retention for unrelated private memory.

### Example 5: Legacy schema transition

A steward cannot immediately supply one newly required provenance field. A
temporary compatibility override identifies affected legacy records,
compensating source links, migration milestones, conformance disclosure, and a
deadline. New records must use the current schema.

### Example 6: Experimental Obsidian projection

A steward tests a generated read-only Obsidian projection. An experimental
exception limits the test to synthetic or approved data, prohibits canonical
writes, defines success criteria, and expires before any production adoption.

### Example 7: Public demonstration deployment

A public demo omits write tools, private-memory adapters, and recovery actions.
This is a public deployment override that narrows functionality and clearly
states that the demo is not a full conformance deployment.

### Example 8: Foundation rejection of a weak local gate

A steward configuration enables destructive MCP writes by default. A
foundation override marks the behavior non-conformant and requires the
mandatory capability gate. It does not grant Shared Foundations permission to
edit the steward repository.

### Example 9: Cross-steward shared service

Three stewards use one read-only index service. An ecosystem exception
documents namespace filters, participating scope owners, audit behavior,
withdrawal, and failure isolation. It does not authorize shared private memory
or propagate to a fourth steward.

### Example 10: Expired emergency access

Temporary incident access reaches its expiry without renewal. The exception
automatically stops authorizing access. Continued use is a governance
violation even if the technical credential still functions.

### Example 11: Recovery backup with revoked permissions

A backup contains obsolete capability permissions. A recovery exception
authorizes restoration of canonical data only. Current governance remains
authoritative, and the obsolete permissions are not restored.

### Example 12: Identity change request

A steward owner proposes changing a stable mission field. A steward-specific
exception cannot bypass the identity-change process. Identity ownership and
foundation governance review are required; the request is handled as a
versioned identity change, not an informal memory update.

### Example 13: Repeated compatibility exceptions

Several stewards request the same permanent compatibility deviation. The
exceptions do not automatically become precedent. Foundation governance opens
a contract review to decide whether the canonical requirement, compatibility
profile, or migration guidance needs revision.

### Example 14: Private evidence in a public register

An exception depends on a sensitive incident report. The public register
contains the exception ID, owner, scope, status, and redacted rationale while
the evidence remains in a protected audit location. Discoverability is
preserved without disclosure.

### Example 15: Automated exception proposal

A health monitor detects recovery drift and drafts an exception proposal. The
proposal has no authority until the Recovery Authority and required owners
approve it. Automation cannot approve or activate its own expanded access.

### Example 16: Downstream fork changes precedence

A public fork adopts a different domain order. It may do so under the
applicable license, but it must version the change, disclose incompatibility,
and avoid calling its local exception canonical OpenClaw approval.

## 12. Future Expansion

New override or exception categories may be added only through versioned
foundation governance. A proposal must define:

- the unmet need and why existing categories are insufficient
- category definition and lifecycle
- allowed and prohibited scopes
- required approvers and separation of duties
- inheritance behavior
- audit events and review cadence
- invalid uses
- compatibility and migration effects
- recovery and rollback requirements
- at least two practical examples

New categories begin as experimental unless foundation governance explicitly
approves another status. They cannot weaken the invalid-exception rules,
retroactively authorize past activity, or silently change existing exception
semantics.

Future work may add:

- canonical exception identifier and record schemas
- risk tiers and approval matrices
- conformance-level mappings
- public and protected register formats
- standard review windows and expiry limits
- exception metrics and repeated-exception thresholds
- cryptographic approval and tamper-evidence guidance
- incident-to-exception linkage
- machine-readable policy representations
- cross-ecosystem recognition rules

## 13. Summary Table

### Override Categories

| Override category | Intended use | Typical duration | Minimum authority | Inheritance |
|---|---|---|---|---|
| Emergency | Immediate containment of material harm | Shortest practical period | Authorized incident role plus retrospective normal approval | Never automatic |
| Recovery | Ordered restoration or degraded operation | Declared recovery state | Recovery Authority, Scope Owner, and affected owners | Affected steward only unless explicitly broadened |
| Steward-specific | Local operating need or bounded deviation | Temporary or reviewed permanent | Scope Owner and Policy Owner | Local only |
| Foundation | Enforce canonical protection or compatibility rule | Versioned requirement or transition | Foundation Governance Maintainer and Policy Owner | Only as explicitly declared |
| Public deployment | Public hosting, disclosure, or distribution constraint | Deployment lifetime with review | Public deployment owner and foundation governance when official claims are affected | Deployment-specific |
| Compatibility | Bounded migration or legacy accommodation | Until migration deadline | Scope Owner, Policy Owner, and compatibility governance | Never automatic |

### Exception Categories

| Exception category | Required endpoint | Renewal | New adoption |
|---|---|---|---|
| Temporary | Expiry or exit condition | New approval required | Allowed within approved scope |
| Permanent | Recurring review and retirement criteria | Continued approval at review | Allowed only within stated scope |
| Experimental | Expiry, evaluation, and rollback | New approval required | Limited to approved test scope |
| Deprecated | Migration or retirement completion | Not renewable for new use | Prohibited |

### Decision Rule

| Question | Canonical answer |
|---|---|
| Is an undocumented deviation valid? | No |
| Does an exception grant adjacent authority? | No |
| Does an exception propagate automatically? | No |
| May stricter conforming controls be adopted without exception? | Yes |
| May the requester self-approve a material exception? | No |
| May an expired exception continue through prior practice? | No |
| May an exception override steward ownership, consent, or isolation? | No |
| Must retired exceptions remain auditable? | Yes |

The governing rule is: every deviation must be explicit, narrow, approved,
time-aware, reversible where possible, non-inheriting by default, and
discoverable throughout its lifecycle.
