# Observatory Sandbox

## Purpose

The Observatory sandbox sub-domain governs the future contract for simulated
trading events. The sandbox is a paper-trading environment where residents may
propose, evaluate, and record simulated market actions under governed conditions
without connecting to a live brokerage, moving real capital, or creating real
financial obligations.

This sub-domain contains the governance contract only. No sandbox execution
engine, brokerage integration, or simulated capital is introduced in this
architecture slice.

## Simulated Trading Only

The sandbox operates on simulated data and simulated accounts exclusively.
Every field in the sandbox schema describes a hypothetical event. No sandbox
event constitutes a real financial transaction.

The following are prohibited in this architecture and any implementation derived
from it:

- real brokerage connections of any kind
- real account numbers, credentials, or authentication tokens
- real capital allocation or movement
- automatic transition from sandbox performance to live trading
- any resident or steward approving their own promotion to live capital
- silent modification of risk limits

## Future Scope

When the sandbox sub-domain is implemented, it will:

- accept simulated trading event records conforming to the sandbox event schema
- maintain an immutable audit log of all simulated events
- enforce risk limits defined through Observatory governance
- provide performance records for strategy evaluation
- support Creator review of strategy evaluation results

It will not:

- connect to any brokerage API
- store real credentials or account information
- execute real orders
- automatically promote strategies to live capital

## Governance Gates

All sandbox activity is subject to Observatory governance. Key gates:

| Activity | Gate |
|---|---|
| Proposing a simulated action | Schema validation + contributor identity |
| Approving a simulated action | Separate authorized party (not the proposer) |
| Changing risk limits | Observatory governance process + Creator review |
| Strategy evaluation review | Creator review |
| Promotion consideration | Creator approval only; performance metrics alone are insufficient |
| Resetting sandbox state | Observatory governance process + Creator review |

No gate may be bypassed. No resident may self-approve proposals or promotion
decisions.

## Shared Knowledge Input Model

Sandbox strategies may be informed by Observatory research contributions. A
strategy proposal may cite accepted research contributions through the
`rationaleReference` or `evidenceReferences` fields. Citing a research
contribution does not constitute its authorization as a trading signal. A
separate strategy proposal and approval is required for each simulated action.

## Separation Between Strategy Proposal and Simulated Execution

A strategy proposal is a request for permission to execute a simulated action.
It is not itself an execution. Execution requires an approval event from an
authorized party. These are separate records with separate accountability.

The contribution lifecycle for a sandbox action:

```text
Resident strategy proposal (contributor)
        ↓
Approval review (authorized party, not the proposer)
        ↓
Simulated order (sandbox execution contract)
        ↓
Simulated fill (sandbox execution contract)
        ↓
Position update (sandbox record)
        ↓
Strategy evaluation (Creator review)
```

No step implies the next step is automatically authorized.

## Creator Approval Boundaries

Creator is the final authority on:

- all governance rule changes in the sandbox sub-domain
- all risk limit changes
- all strategy evaluation outcomes
- any consideration of promotion from simulation to live capital

Creator approval must be explicit for each decision. Prior approvals do not
carry forward to new decisions.

## No Real Brokerage Access

This architecture explicitly prohibits:

- storing brokerage credentials in the Observatory or any layer that reads it
- transmitting credentials through Observatory records or contracts
- referencing real brokerage account numbers in any Observatory field
- building adapters that connect sandbox event records to live order routing
- using sandbox performance as the sole basis for live capital allocation

These prohibitions apply regardless of sandbox performance metrics, strategy
age, or contributor experience.

## Schema Reference

Sandbox events conform to the schema defined in:

[`../schemas/SANDBOX_EVENT_SCHEMA.md`](../schemas/SANDBOX_EVENT_SCHEMA.md)

All submitted events must pass schema validation before acceptance. Schema
version is required in every record.

## Current State

This sub-domain contains governance contracts only. No sandbox execution
environment exists. No simulated events have been recorded. Implementation
requires a separate architecture and implementation slice approved by Creator.
