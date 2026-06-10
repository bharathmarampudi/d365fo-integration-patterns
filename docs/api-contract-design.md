# API Contract Design

## Standard response envelope

All service operations should return the same top-level shape:

```json
{
  "success": true,
  "data": {},
  "errors": []
}
```

For failures:

```json
{
  "success": false,
  "data": null,
  "errors": [
    {
      "message": "Sales order is required.",
      "details": "salesId was not provided.",
      "trace": "Validation failed before posting."
    }
  ]
}
```

## Request contract principles

- Use clear field names that external systems can understand.
- Include legal entity in each request when the service supports multiple companies.
- Use stable D365 references such as `inventTransId`, line number, journal number, or document number.
- Validate external quantities against D365 status before posting.
- Use a consistent date format and validate date parsing before posting.
- Return validation errors in a consistent structure.

## Response design principles

- Return `success = true` only after D365 posting is completed.
- Return posted document references in `data`.
- Return validation and posting errors in `errors`.
- Do not expose internal server names, tokens, URLs, credentials, or sensitive production data.
