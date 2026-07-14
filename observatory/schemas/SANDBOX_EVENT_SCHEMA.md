# Sandbox Event Schema

## Purpose

This schema defines the conceptual contract for a simulated trading event in
the Observatory sandbox sub-domain. Sandbox events are records of actions,
outcomes, and decisions within a fully isolated paper-trading simulation. No
sandbox event connects to a live brokerage, moves real capital, or constitutes
a real financial transaction.

This schema defines the future contract only. No sandbox execution engine is
introduced in this architecture slice.

Schema version: 1

## Boundary Statement

**Simulated trading only.** Every field in this schema describes a simulated
event. No field carries real monetary value, real order state, or real account
information. Implementation must ensure physical and logical separation from
any live brokerage connection.

No resident may transition a sandbox strategy to live capital without Creator
approval. Performance in simulation does not constitute readiness for live
capital. These prohibitions apply regardless of sandbox performance metrics.

## Record Identity

### eventId

**Type:** string  
**Required:** yes  
**Description:** Stable unique identifier for this sandbox event. Must be
assigned at creation and never reused. Recommended format: sandbox account
prefix, date, and a sequential or random suffix. Example: `sbx-20260714-0017`.

### schemaVersion

**Type:** integer  
**Required:** yes  
**Description:** Version of this schema the record conforms to. Must be `1`
for records conforming to this version.

### sandboxAccountId

**Type:** string  
**Required:** yes  
**Description:** Identifier for the simulated account this event belongs to.
Must be a sandbox-only identifier with no relationship to any real brokerage
account number. Must carry a prefix or naming convention that makes its
simulated nature unambiguous.

## Provenance

### timestamp

**Type:** ISO 8601 datetime string  
**Required:** yes  
**Description:** The time this simulated event occurred within the sandbox,
expressed in UTC.

### createdAt

**Type:** ISO 8601 datetime string  
**Required:** yes  
**Description:** The time this event record was created. May differ from
`timestamp` when events are recorded with a delay.

### contributor

**Type:** string  
**Required:** yes  
**Description:** The stable identifier of the resident or strategy that
originated this event. Use canonical resident IDs. Must not be a local
username, email address, or system account name.

### approvalState

**Type:** string  
**Required:** yes  
**Description:** The governance approval state of this event. Permitted values:

- `proposed` — event submitted for sandbox execution but not yet approved
- `approved` — event approved for simulated execution
- `rejected` — event rejected; rationale in `rationaleReference`
- `executed` — event simulated and recorded
- `voided` — event voided after recording; tombstone preserved

Transitions require the authority defined in Observatory governance. A
contributor may not self-approve their own proposals.

## Event Classification

### eventType

**Type:** string  
**Required:** yes  
**Description:** Classification of the simulated event. Permitted values:

- `proposal` — a resident proposes a simulated action for approval
- `approval` — an authorized party approves a proposed action
- `rejection` — an authorized party rejects a proposed action
- `simulated_order` — a simulated order is submitted
- `simulated_fill` — a simulated order is filled at a simulated price
- `position_update` — a position record is updated following a fill
- `risk_event` — a risk threshold condition is observed
- `limit_breach` — a risk limit is breached in simulation
- `strategy_evaluation` — a formal evaluation of strategy performance
- `sandbox_reset` — the sandbox state is reset to a defined baseline

## Instrument and Action

### symbol

**Type:** string or null  
**Required:** no  
**Description:** The simulated instrument identifier. Required for order and
position event types. Null for non-instrument events such as `sandbox_reset`.
Must not be a live brokerage ticker feed reference unless explicitly labeled as
delayed or historical data.

### action

**Type:** string or null  
**Required:** no  
**Description:** The simulated action taken. Permitted values when applicable:
`buy`, `sell`, `short`, `cover`, `hold`, `cancel`. Null for non-action event
types.

### quantity

**Type:** number or null  
**Required:** no  
**Description:** The simulated quantity of shares or units. Required for order
and fill event types. Must be a non-negative number. Null for non-quantity
event types.

### simulatedPrice

**Type:** number or null  
**Required:** no  
**Description:** The simulated execution price per unit. Required for
`simulated_fill` event type. This is a hypothetical price used for simulation
only. It carries no financial obligation. Null for non-price event types.

### orderType

**Type:** string or null  
**Required:** no  
**Description:** The type of simulated order. Examples: `market`, `limit`,
`stop`, `stop_limit`. Null for non-order event types.

## Risk and Limits

### riskLimits

**Type:** object or null  
**Required:** no  
**Description:** A record of the risk limits in effect at the time of this
event. Limits are defined and modified only through the Observatory governance
process. No resident may change risk limits silently. This field records the
limits that were active; it does not set them. Null when risk limits are not
relevant to the event type.

### limitBreachDetail

**Type:** string or null  
**Required:** no  
**Description:** A description of the limit condition when `eventType` is
`limit_breach`. Must reference the specific limit and the observed value. Null
for all other event types.

## Performance

### simulatedPnl

**Type:** number or null  
**Required:** no  
**Description:** The simulated unrealized or realized profit and loss
associated with this event, in the sandbox account's simulated currency unit.
This value is hypothetical and carries no real financial meaning. Null when not
applicable to the event type.

### cumulativeSimulatedPnl

**Type:** number or null  
**Required:** no  
**Description:** The cumulative simulated profit and loss for the sandbox
account as of this event. Hypothetical only. Null when not applicable.

## Rationale and Evidence

### rationaleReference

**Type:** string or null  
**Required:** no  
**Description:** A stable reference to the document, research contribution,
or observation that informed this event. Must not be a local filesystem path.
Use repository-relative paths or governed reference formats. Required when
`eventType` is `rejection` or `strategy_evaluation`.

### evidenceReferences

**Type:** array of strings  
**Required:** no  
**Description:** Optional references to specific evidence records that support
the strategy or decision behind this event. Same path-safety rules as
`rationaleReference`. Empty array when no specific evidence is cited.

## Audit

### auditMetadata

**Type:** object  
**Required:** yes  
**Description:** Immutable fields recorded at creation time for audit
integrity. Minimum required keys:

- `recordedBy` — stable identifier of the agent or system that recorded
  this event (not necessarily the `contributor`)
- `recordedAt` — ISO 8601 datetime of record creation
- `immutable` — boolean, must be `true` for executed and voided events

This object must not be modified after an event reaches `executed` or
`voided` state.

### metadata

**Type:** object  
**Required:** no  
**Description:** Extensible key-value structure for supplementary information.
Must not contain credentials, tokens, local paths, or local usernames.

## Governance Rules

1. Sandbox events describe simulation only. No sandbox event constitutes a
   real financial transaction or real order.
2. No sandbox event may reference a real brokerage account number, real
   credential, real API key, or real authentication token.
3. No resident may self-approve their own proposals. Approval requires a
   separate authorized party as defined in Observatory governance.
4. Risk limits are set through Observatory governance. No resident may change
   risk limits silently or unilaterally.
5. Transition from sandbox to live capital requires explicit Creator approval
   and is outside the scope of this schema. Performance metrics alone do not
   authorize transition.
6. All sandbox events are immutable once they reach `executed` or `voided`
   state. Corrections produce a `voided` tombstone and a new record.
7. No sandbox event may contain a local filesystem path, local username,
   credential, token, API key, or secret value.
8. A `sandbox_reset` event must record the baseline state being restored and
   the authority that approved the reset.

## Non-Goals

This schema does not define:

- a live trading event format
- brokerage API integration specifications
- real account or position management
- a financial reporting format
- a production order management system
- runtime database fields, query interfaces, or execution logic
- a specific storage format or file encoding

## Future Evolution

- structured `riskLimits` sub-schema with field-level definitions
- strategy versioning fields for multi-version performance comparison
- cross-event relationship fields for order-fill chains
- batch event submission contracts for high-frequency simulation
- schema version 2 migration guide when structural changes are needed
- promotion-readiness checklist linked to governance gates
