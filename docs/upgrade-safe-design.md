# Upgrade-Safe D365 F&O Design

## Principles

- Prefer standard D365 posting frameworks instead of direct transaction table updates.
- Keep custom logic in service classes, extensions, handlers, and contracts.
- Avoid overlayering.
- Keep business validations explicit and documented.
- Keep external API contracts stable even when internal implementation changes.
- Keep response models consistent across operations.

## Example

For sales packing slip posting, use the D365 form letter/posting framework pattern instead of directly creating posted packing slip journal records.

## Benefits

- Better compatibility with Microsoft platform updates
- Better audit trail
- Reduced regression risk
- Easier support and troubleshooting
- Cleaner handoff between integration and ERP teams
