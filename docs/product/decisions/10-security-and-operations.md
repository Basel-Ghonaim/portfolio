# 10 — Security and Operations

**Status:** Approved
**Approved on:** 2026-10-24

This axis defines required behavior only. No technology or service provider is selected.

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D10-01 | Dashboard sign-in uses the owner's GitHub account only; any other account is rejected. No passwords are used or stored in the first release. | Simplest secure option: no password storage, and GitHub's two-factor authentication protects the account. |
| D10-02 | Access recovery relies first on recovering the GitHub account itself. For emergencies (e.g. loss of the account), a recovery path exists that requires access to the hosting environment owned by the owner and cannot be performed from the site itself. | Recovery must not depend on the same factor that was lost. |
| D10-03 | A dashboard session stays active for 7 days unless the owner signs out. A "Sign out of all devices" action is available. Repeated failed sign-in attempts are slowed down. | Convenient for a single owner while limiting the impact of a compromised session. |
| D10-04 | The owner is warned before leaving a page with unsaved changes. If the session expires while editing, the unsaved work is not lost: the owner signs in again and completes the save. There is no autosave in the first release. | Protects work without the added complexity of autosave. |
| D10-05 | Backups run weekly: automatically if the free service allows it, otherwise through a "Back up now" action with a reminder in the dashboard. The last 4 backups are kept, stored outside the main hosting provider. Restore is tested before launch and then every 6 months. | Proportionate protection for content that may exist only in the dashboard (D2-09); storing backups elsewhere prevents losing them with the provider. |
| D10-06 | A failed backup shows a clear alert in the dashboard. | Failures must not go unnoticed for months. |
| D10-07 | If a secondary external service fails (e.g. analytics or YouTube), the site keeps working normally; only the affected part is unavailable. | External failures must not disrupt unrelated functionality. |
| D10-08 | Error pages show a simple message in the visitor's language without technical details. Secrets (keys, credentials) never appear in code, the repository, logs, frontend output, or error messages. | Prevents leaking internals and secrets. |
| D10-09 | Provider selection criterion: any service selected later must not suspend the project or delete its data because of low activity. | A real risk for free tiers with a low-traffic site. |
| D10-10 | The first release runs on a free subdomain provided by the hosting provider. When moving to a custom domain later, old links redirect to the new domain where the host allows it. | Zero mandatory cost (PRD). Earlier migration means fewer old links in circulation. |
| D10-11 | Every protected operation is authorized on the server side, and all inputs and uploaded files are validated. *(Approved with PRD v1.0.)* | Interface-only protection can be bypassed; validation protects data integrity and security. |
