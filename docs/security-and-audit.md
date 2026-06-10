# Security and Audit Considerations

## Authentication and authorization

For real implementations, use approved D365 authentication patterns and restrict access to only the required service operations.

## Data protection

Never expose the following in public repositories:

- Production URLs
- Client IDs or secrets
- Bearer tokens
- Customer names
- Vendor names
- Item numbers
- Sales order numbers
- Purchase order numbers
- Tracking numbers
- Company-specific labels or prefixes

## Audit

Recommended production audit fields:

| Field | Purpose |
|---|---|
| External transaction ID | Trace caller request |
| Legal entity | Company context |
| Operation name | API operation |
| Document reference | Sales order, PO, transfer order, journal |
| Status | Success, failed, duplicate, validation failed |
| Created date/time | Support timeline |
| Error summary | Support diagnosis |
