# 09 — Analytics and Privacy

**Status:** Approved
**Approved on:** 2026-10-24

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D9-01 | Core metrics: visits, views per project (Arabic and English views are counted together as one project, per the shared slug D6-07), traffic sources (e.g. LinkedIn, GitHub, direct), CV downloads, and clicks per contact channel. | Covers the questions the owner needs answered. Channel clicks are the only signal of visitor interest while the contact form is deferred (D2-04). |
| D9-02 | Additional metrics: page language (Arabic/English) and device type (mobile, desktop, tablet). | Useful for future design decisions without adding complexity. |
| D9-03 | Analytics are viewed in the analytics tool's own dashboard, linked from the administration dashboard. No analytics page is built inside the administration dashboard in the first release. | Much simpler and free; a custom analytics page is significant work not justified for the first release. |
| D9-04 | Analytics must not use cookies or collect personal data, so no consent banner is needed. This is a product requirement that any tool selected later must satisfy. | Respects visitor privacy and avoids an intrusive banner. Legal requirements per jurisdiction are not assessed here. |
| D9-05 | The owner's own visits are excluded from analytics. | Otherwise they would heavily inflate numbers on a low-traffic site. |
| D9-06 | Data is reported truthfully: an unavailable source is shown as "Unknown", never invented; true zero activity is distinguished from unavailable data; bot traffic is excluded where possible. | No fabricated data (PRD). |
| D9-07 | A short bilingual Privacy page is added, linked from the footer. It explains what is measured, that no personal data is collected, and that the YouTube player loads only on click (D8-12). | Builds visitor trust at minimal cost. Amends the page list in D3-01. |

## Notes

- D9-07 adds a Privacy page to the public pages defined in D3-01, and its content is bilingual under D6-04.
