# Foundation MCP Architecture

## Purpose

The MCP foundation defines how stewards discover and use external
capabilities through bounded, typed, auditable interfaces. It separates
knowledge of how to perform work from permission to execute tools.

## Core Concepts

### Tools are capabilities

An MCP tool represents access to a system, not merely a convenient function.
Every server and tool requires an owner, scope, risk classification, and
governance posture.

### Static before dynamic

Preconfigured, reviewed servers are the default. Runtime addition, removal, or
mutation of MCP servers is a high-risk optional capability.

### Progressive disclosure

Stewards should receive a concise capability catalog first and detailed tool
schemas only when needed. This limits context overhead and avoids exposing
irrelevant capabilities.

### Typed contracts

The agent-facing interface should use stable, structured inputs and outputs.
Adapters absorb transport or backend differences.

### Read before write

Read-only discovery and retrieval tools are lower-risk integration points.
Writes, deletion, execution, and infrastructure mutation require stronger
controls.

### Graceful absence

An unavailable MCP server must produce a clear error or fallback path, not
fabricated results.

## Required Components

- **Server registry:** identifier, purpose, transport, owner, status, and
  configuration source
- **Tool catalog:** name, description, schema, capability class, and risk
- **Capability policy:** default state and approval requirements
- **Scope controls:** steward, workspace, data, and tenant boundaries
- **Credential boundary:** secrets remain outside prompts, memory, and logs
- **Transport abstraction:** stdio, HTTP, or future transport behind one
  conceptual contract
- **Health contract:** availability, version, and failure reporting
- **Audit contract:** tool, arguments summary, result summary, status, actor,
  and duration
- **Write safeguards:** validation, idempotency where possible, and explicit
  confirmation for destructive operations
- **Failure behavior:** timeout, unavailable, malformed result, and denied
  capability states

## Optional Components

- dynamic server registration
- remote MCP gateways
- server discovery
- tool caching
- sandboxed execution
- per-tool cost budgets
- human approval queues
- tool composition
- shared server pools across stewards
- dashboard management

Dynamic management and shared pools must be disabled by default.

## Inheritance Strategy

The foundation defines the registry, tool metadata, audit, and capability
contracts. Each steward receives an allowlisted capability profile.

Stewards may inherit:

- common read-only knowledge tools
- shared protocol adapters
- standard health and audit behavior

Stewards must independently receive:

- credentials
- write permissions
- destructive capabilities
- workspace access
- dynamic management rights

One steward's server authorization does not authorize another.

## Future Steward Integration

Integration should proceed by capability class:

1. register servers without enabling them
2. verify health and schemas
3. enable read-only tools for a single steward
4. validate audit and scope boundaries
5. enable bounded writes
6. add destructive or dynamic capabilities only after governance review
7. evaluate shared-server operation separately

Adapters should let stewards use the same conceptual capability even when the
underlying server differs.

## Known Risks

- excessive tool definitions consuming context
- credentials leaking into logs or memory
- server supply-chain compromise
- overly broad filesystem or workspace access
- dynamic server mutation bypassing review
- tool results containing prompt injection
- retries causing duplicate writes
- shared servers leaking data across stewards
- transport timeout interpreted as successful completion
- skills hiding dangerous tool behavior

## Future Expansion Areas

- MCP conformance profiles
- capability negotiation
- signed server manifests
- standardized approval metadata
- sensitivity labels on tool outputs
- deterministic replay for audited calls
- cross-steward broker policies
- portable server bundles with safe defaults
