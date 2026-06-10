# Idempotency and Duplicate Prevention

## Why it matters

3PL systems may retry API calls after network timeouts. Without duplicate prevention, the same warehouse update may be posted more than once.

## Recommended approaches

| Pattern | Description |
|---|---|
| External correlation ID | Require the 3PL to send a unique transaction ID |
| Document status validation | Check whether the D365 document is already posted |
| Line quantity validation | Prevent posting more than the remaining deliverable/receivable quantity |
| Optional integration log | Store request hash, external ID, result, and timestamp |
| Safe retry response | If already posted, return a clear duplicate/already-processed response |

## Example correlation fields

```json
{
  "externalTransactionId": "3PL-2026-000001",
  "legalEntity": "usmf",
  "salesId": "SO-000001"
}
```

## Note

This public sample does not include a full integration log table implementation, but production implementations should consider one for audit, support, and duplicate prevention.
