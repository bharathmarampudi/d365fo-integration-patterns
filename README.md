# D365 F&O Integration Patterns

Public showcase repository for Microsoft Dynamics 365 Finance & Operations integration architecture patterns.

This repo demonstrates how enterprise warehouse and 3PL integrations can be designed using upgrade-safe D365 F&O patterns, service contracts, posting frameworks, validation layers, and clear response structures.

> This repository contains sanitized sample architecture and sample code only. It does not include proprietary customer code, company-specific endpoints, credentials, item numbers, order numbers, tracking numbers, or production data.

## Showcase scenario

A third-party logistics provider sends warehouse execution updates into D365 F&O for:

- Sales packing slip posting
- Transfer order shipment and receipt
- Counting journal posting
- Purchase order receipt
- Return packing slip / return receipt scenarios

## Architecture summary

```mermaid
flowchart LR
    A[3PL / External Warehouse System] --> B[HTTPS API Call]
    B --> C[D365 F&O Custom Service]
    C --> D[Request Contract Validation]
    D --> E[Standard D365 Posting Framework]
    E --> F[D365 Transaction / Journal / Document]
    F --> G[Response Contract]
    G --> H[3PL Success or Error Response]
```

## What this demonstrates

- Custom service class design
- Request and response contract pattern
- Request validation before posting
- Use of D365 posting frameworks instead of direct table updates
- Clear success/error responses
- Upgrade-safe architecture thinking
- Support-friendly exception handling
- Idempotency and duplicate prevention design considerations

## Repository structure

```text
docs/
  3pl-api-architecture.md
  api-contract-design.md
  error-handling-pattern.md
  idempotency-and-duplicate-prevention.md
  upgrade-safe-design.md
  security-and-audit.md

diagrams/
  3pl-integration-architecture.mmd

samples/
  payloads/
  responses/
  xpp/
    contracts/
    services/
    shared/

checklists/
  api-review-checklist.md
  production-readiness-checklist.md
```

## Design principle

For D365 F&O integrations, avoid direct table updates when a standard business process/posting framework exists. The custom API should validate input, prepare the right posting parameters, call the standard framework, and return a clear response to the calling system.
