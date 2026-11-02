# Conduit Gateway

> Users should access outcomes, not systems.

Conduit Gateway is a prototype architecture for modernizing legacy systems through policy-driven outcome access.

Instead of exposing systems directly, Conduit Gateway retrieves information from one or more legacy systems, applies policy validation, trust evaluation, auditing, and recovery checks, then returns only the requested outcome.

---

## The Problem

Many organizations depend on legacy systems that are expensive, risky, or impractical to replace.

Traditional modernization approaches often expose underlying systems through APIs, databases, portals, and direct integrations, increasing complexity and attack surface.

Conduit Gateway explores a different approach:

- Users request outcomes rather than systems.
- Legacy systems remain isolated.
- Access flows through policy-controlled conduits.
- Only approved information is returned.
- Recovery and auditing occur automatically.

---

## Core Principle

### Traditional Access

```text
User
  ↓
System
  ↓
Data
```

### Conduit Gateway

```text
User
  ↓
Outcome Request
  ↓
Conduit
  ↓
Result
```

The user should not need to know:

- Which systems are involved
- Where information is stored
- How retrieval occurs
- What infrastructure exists behind the request

The user receives an outcome.

---

## Architecture

```text
                 User
                   │
                   ▼
           Request Broker
                   │
                   ▼
          Ephemeral Conduit
                   │
                   ▼
             Route Builder
                   │

      Policy   Trust   Audit   Recovery
       Node     Node    Node      Node

                   │
                   ▼
            Outcome Engine
                   │

        Payroll   Benefits   HR

                   │
                   ▼

      Compensation Summary
```

---

## Features

### Outcome-Based Access

Users request outcomes rather than direct access to systems.

Example:

**Request**

```text
salary
```

**Response**

```json
{
  "salary": 85000
}
```

---

### Composite Outcomes

Conduit Gateway can assemble information from multiple systems and return a single outcome.

Example:

**Request**

```text
compensation_summary
```

**Response**

```json
{
  "salary": 85000,
  "benefits": "Premium Plan",
  "department": "Engineering"
}
```

The user receives only the approved result.

---

### Dynamic Routing

Each request travels through a dynamically generated route of validation nodes.

Example:

```text
PolicyNode
TrustNode
AuditNode
RecoveryNode
```

No fixed route is required.

---

### Ephemeral Conduits

Routes exist only for the lifetime of a request.

```text
Request Created
      ↓
Route Generated
      ↓
Outcome Returned
      ↓
Route Destroyed
```

---

### Legacy System Isolation

Underlying systems remain isolated behind the Conduit Gateway.

Examples:

- Payroll
- Benefits
- Human Resources

Users never interact directly with these systems.

---

### Policy Enforcement

Channels control:

- Allowed actions
- Allowed systems
- Request limits
- Access policies

Requests that violate policy are blocked before data retrieval.

---

### Audit Logging

Every request and policy decision can be recorded for future review.

Example:

```text
Timestamp
User
Action
Result
```

---

### Trust Engine

Channels maintain trust scores that can be used to evaluate behavior.

Future versions may use trust scoring to:

- Restrict access
- Require additional validation
- Lock risky channels

---

### Rate Limiting

Channels can enforce request thresholds.

Example:

```text
Max Requests: 5
```

Requests beyond policy limits are denied.

---

### Snapshot Recovery

Conduit Gateway maintains known-good snapshots.

```text
Snapshot
   ↓
Corruption
   ↓
Detection
   ↓
Restore
```

---

### Self-Healing Restoration

The gateway validates system integrity and automatically restores corrupted records.

Example:

```text
Salary = -9999999
```

Detected as invalid:

```text
Anomaly Detected
Snapshot Restored
```

---

## Current Prototype

The current proof of concept includes:

- Legacy Payroll System
- Legacy Benefits System
- Legacy HR System
- Request Broker
- Dynamic Route Builder
- Policy Engine
- Trust Engine
- Audit Engine
- Recovery Engine
- Outcome Assembly
- Snapshot Recovery
- Self-Healing Restoration
- Channel Policies
- Rate Limiting
- Composite Outcomes

---

## Example Workflow

```text
User Requests:
"compensation_summary"

        ↓

Request Broker

        ↓

Ephemeral Conduit

        ↓

Policy Validation

        ↓

Trust Evaluation

        ↓

Audit Logging

        ↓

Recovery Check

        ↓

Payroll System
Benefits System
HR System

        ↓

Outcome Assembly

        ↓

Return Result
```

Result:

```json
{
  "salary": 85000,
  "benefits": "Premium Plan",
  "department": "Engineering"
}
```

---

## Future Roadmap

### Version 2

- JSON-based policy files
- Database-backed legacy adapters
- REST API endpoint layer
- Route analytics
- Expanded trust scoring
- Configurable outcome templates
- Enterprise policy management

### Version 3

- Web dashboard
- Administrative monitoring tools
- Multiple legacy-system connectors
- Advanced channel orchestration
- Policy simulation tools

---

## Future Research

Areas of future exploration include:

- Dynamic policy generation
- Route optimization
- Conduit analytics
- Enterprise legacy adapters
- Outcome marketplaces
- Agent-assisted outcome requests

---

## Project Status

**Prototype / Research Project**

Conduit Gateway is an experimental architecture exploring outcome-based access patterns for legacy system modernization, information isolation, and policy-driven orchestration.

---

## Project Philosophy

> Users should access outcomes, not systems.
