# API Review Checklist

Use this checklist before publishing a D365 F&O custom service for external integration.

- [ ] Request contract uses clear, stable field names.
- [ ] Legal entity handling is explicit.
- [ ] Required fields are validated before posting.
- [ ] Quantity and status validations prevent over-posting.
- [ ] Service uses standard posting frameworks where possible.
- [ ] Response contract is consistent across operations.
- [ ] Errors are returned in a caller-friendly format.
- [ ] No secrets, internal URLs, or production values are logged or returned.
- [ ] Duplicate prevention has been considered.
- [ ] API behavior is documented for support teams.
