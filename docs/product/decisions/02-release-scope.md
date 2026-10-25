# 02 — Release Scope

**Status:** Approved
**Approved on:** 2026-10-22

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D2-01 | The first release is a medium-sized version focused on quality, without unjustified complexity. The product grows incrementally afterwards. There is no launch deadline. | The owner works on the project part-time and prioritizes quality over speed, while avoiding both a minimal release and over-engineering. |
| D2-02 | The portfolio is an independent project. It has no technical or schedule dependency on any project it showcases (e.g. Masaha, QuickTweet). Showcased projects are content managed manually and may be displayed while still in development. | The portfolio serves the owner's evolving professional profile; it must not be blocked by, or coupled to, the progress of other work. |
| D2-03 | The administration dashboard is part of the first release. It must be capable but not complex, and extensible. | Routine content changes must not require code changes. The dashboard also serves as practical evidence of backend capability (see D1-06). |
| D2-04 | The contact form is deferred. In the first release, visitors contact the owner through direct channels managed from the dashboard, including a "copy email" action next to the email link. | Removes visitor personal-data storage, spam protection, rate limiting, and email-service dependency, with no meaningful loss for visitors. The "Contact me" call to action (D1-07) remains. |
| D2-05 | Analytics are included in a simple, logical form. | Provides useful insight without unnecessary complexity. Details are decided in axis 09. |
| D2-06 | Project categorization and filtering are included in a simple form. | The number of projects is small; filtering must stay proportionate. Details are decided in axis 04. |
| D2-07 | Light and dark themes are supported. | Confirmed requirement. |
| D2-08 | Homepage sections are of two kinds: fixed sections that cannot be changed, and manageable sections whose order and visibility are controlled from the dashboard. | Gives control where useful while protecting the essential structure. Details are decided in axis 03. |
| D2-09 | Backup and restore cover both the database and uploaded files, follow a documented procedure, and are tested by at least one actual restore before launch. Heavy automation is not required. | Dashboard-managed content may be the only copy of the owner's content, and free-tier services may change or remove data. Scope stays proportionate because no visitor data is stored. Details are decided in axis 10. |
| D2-10 | Excluded from the first release: blog, testimonials, services section, project search, direct video upload, and contact form. Any of these may be reopened by explicit decision. | Keeps the first release focused. |
| D2-11 | Direct contact channels in the first release: email, WhatsApp, LinkedIn, and GitHub. The owner can add, edit, and manage channels from the dashboard. *(Refined by D7-06: channels are chosen from predefined types.)* | Covers the channels visitors expect while remaining manageable without code changes. |

## Notes

- WhatsApp currently uses the owner's personal number; it will be replaced with a business number when one is available. This is the owner's accepted privacy choice.

## Carried forward to other axes

- Featured-project eligibility must account for the fact that the owner's strongest projects are currently in development (see D2-02) → axis 04.
- Contact axis (07) is reduced to direct contact channels and their presentation.
