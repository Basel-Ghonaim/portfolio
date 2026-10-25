# 11 — Quality and Acceptance Criteria

**Status:** Approved
**Approved on:** 2026-10-24

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D11-01 | Performance targets: LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1. The release gate is a lab measurement on defined pages (Home, Projects listing, one case study, About), in both languages and both themes, using a mid-range mobile simulation. Real-user field data is monitored after launch when available. | A low-traffic site will rarely have sufficient field data, so a field-only criterion could never be evaluated. |
| D11-02 | Accessibility target: WCAG 2.2 AA for the public site and the administration dashboard. Verified by automated checks plus a manual keyboard and screen-reader pass, in both right-to-left and left-to-right directions. | Automated checks alone do not cover keyboard and screen-reader use. |
| D11-03 | Supported browsers: the latest two major versions of Chrome, Edge, Firefox, and Safari, including Safari on iPhone and iPad. | Makes "modern browsers" testable. |
| D11-04 | Supported screens: mobile, tablet, and desktop. Minimum supported width is 320 px, with no horizontal scrolling on any page. | Makes responsive support testable. |
| D11-05 | Testing prioritizes critical flows rather than a numeric coverage target. Priority tests: rejection of any account other than the owner's; drafts and archived projects never visible to visitors by any means, including direct URLs; unpublished edits not visible before publishing; blocking publication of content incomplete in either language; redirect of old URLs after a slug change; language switching; image upload, limits, and partial upload failure; stable CV link after replacement; backup and restore. | Effort goes where failures would harm the owner or visitors. |
| D11-06 | The first release is ready for launch when: all approved decisions in axes 01–10 are met; all priority tests pass; performance and accessibility criteria are met; one actual restore has succeeded; and no known critical security, accessibility, or data-loss defect remains open. | A single, verifiable definition of release readiness. |
| D11-07 | Non-critical defects (e.g. a minor visual detail in one browser) do not block launch, provided they are documented and scheduled for fixing. | Avoids blocking launch on cosmetic issues while keeping them tracked. |
| D11-08 | The public site and the dashboard provide clear loading, empty, success, and error states. *(Approved with PRD v1.0.)* | Users always understand what is happening and whether an action succeeded. |
