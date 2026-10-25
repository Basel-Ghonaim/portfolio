# Product Decisions

This folder records the **product decisions** reached during discovery, one file per discussion axis.

Product decisions define what the product does and why. They are distinct from technical and architectural decisions (ADRs), which are recorded separately and must not be added here.

**Phase status:** Product discovery completed. PRD v1.0 approved on 2026-10-24.

## Rules

- The consolidated PRD is [`../PRD.md`](../PRD.md) (v1.0, approved, built from these decisions).
- Decisions recorded here are authoritative. If the PRD differs from a decision file, the PRD must be corrected.
- Decisions added by the cross-axis consistency review (2026-10-24) are marked *(Review C-xx)* in their axis files.
- Only decisions explicitly approved by the product owner are recorded as approved.
- Each decision has a stable ID (`D<axis>-<number>`, e.g. `D1-04`) so it can be referenced from other axes.
- Decisions made early that belong to a later axis are recorded where they were made and marked for transfer to their owning axis.
- An axis file is created only when discussion of that axis begins.

## Axes

| # | Axis | File | Status |
|---|---|---|---|
| 01 | Goals and audience | [01-goals-and-audience.md](01-goals-and-audience.md) | Approved |
| 02 | Release scope | [02-release-scope.md](02-release-scope.md) | Approved |
| 03 | Public site structure | [03-public-structure.md](03-public-structure.md) | Approved |
| 04 | Projects | [04-projects.md](04-projects.md) | Approved |
| 05 | Content management and publishing | [05-content-and-publishing.md](05-content-and-publishing.md) | Approved |
| 06 | Languages and URLs | [06-languages-and-urls.md](06-languages-and-urls.md) | Approved |
| 07 | Contact channels | [07-contact-channels.md](07-contact-channels.md) | Approved |
| 08 | Media and CV | [08-media-and-cv.md](08-media-and-cv.md) | Approved |
| 09 | Analytics and privacy | [09-analytics-and-privacy.md](09-analytics-and-privacy.md) | Approved |
| 10 | Security and operations | [10-security-and-operations.md](10-security-and-operations.md) | Approved |
| 11 | Quality and acceptance criteria | [11-quality-and-acceptance.md](11-quality-and-acceptance.md) | Approved |

Axes may be adjusted as the discussion progresses.
