# Error Handling Pattern

## Goal

External systems should receive clear, support-friendly error messages without needing direct access to D365 infolog screens.

## Pattern

1. Validate request fields before posting.
2. Collect validation errors into an error list.
3. During posting, catch exceptions.
4. Convert D365 infolog messages into response errors.
5. Return a consistent response contract.

## Recommended response fields

| Field | Purpose |
|---|---|
| `message` | Short error message for the calling system |
| `details` | More detailed explanation |
| `trace` | Technical trace or infolog message sanitized for external consumption |

## Notes

For public samples, do not expose internal class names, stack traces, server names, credentials, endpoints, or environment details.
