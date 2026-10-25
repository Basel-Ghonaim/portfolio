# 06 — Languages and URLs

**Status:** Approved
**Approved on:** 2026-10-22

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D6-01 | Case studies are English-only. *(Transferred from D1-09.)* | Longest content in the site; English is the primary language of the technical field (D1-04). |
| D6-02 | The administration dashboard is English-only. *(Transferred from D1-10.)* | The owner is the only user; removes significant work with no visitor impact. |
| D6-03 | Content is classified as bilingual or English-only according to the classification table below. | Each content type is classified once, so no individual item needs a language decision. |
| D6-04 | Bilingual completeness rule: an item in the bilingual column cannot be published or shown publicly unless it is complete in both languages. English-only content never requires translation and never blocks publication. *(Supersedes the provisional principle D5-09.)* | Prevents incomplete public content while keeping English-only content simple. |
| D6-05 | English content shown inside Arabic pages is displayed correctly left-to-right, while surrounding headings and labels remain in Arabic. On an Arabic project page, the title and summary appear in Arabic, followed by a short note (e.g. "Case study available in English"), then the case study. | Makes the language switch explicit and keeps mixed-direction content readable. |
| D6-06 | Each language has its own URL path, e.g. `/en/projects` and `/ar/projects`. | Every page has a clear, shareable link per language, and share previews appear in the correct language (D1-02). |
| D6-07 | A single Latin slug is shared by both languages, e.g. `/en/projects/masaha` and `/ar/projects/masaha`. | Arabic slugs become long, unreadable encoded strings when copied and shared. A shared slug makes switching languages a simple path-prefix change and removes per-language slug rules. |
| D6-08 | Visiting `/` opens the saved language if one exists; otherwise English. | Predictable entry behavior consistent with English as the primary language (D1-04). |
| D6-09 | An explicit language URL (e.g. `/ar/...`) always takes precedence over the saved preference. | Shared links must open in the language they were shared in. |
| D6-10 | The saved language preference changes only when the visitor uses the language switcher. Opening a link in another language does not change it. | Prevents a single shared link from silently changing a visitor's language on later visits. |
| D6-11 | The language switcher opens the same page in the other language and keeps the selected filter. If that is not possible (e.g. a project that was just archived), it opens the nearest parent page (the Projects listing). | Preserves the visitor's context instead of sending them back to the homepage. |
| D6-12 | A slug does not change automatically when a project title changes. The owner can change it manually; the previous URL then redirects automatically to the new one. | Links already sent in applications and messages must keep working. |
| D6-13 | A slug that is still used by a redirect cannot be assigned to another project. | Prevents an old link from silently pointing to a different project. |
| D6-14 | Current and previous URLs of an archived project open nothing (Not Found), consistent with D5-04. | Archived projects must not be reachable through any URL. |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D6-15 | A slug change made within unpublished project changes takes effect only when the change is published. The new slug is reserved while it waits, so no other project can take it. *(Review C-07.)* | Applies D5-01 to URLs and prevents conflicts. |
| D6-16 | When an archived project is permanently deleted (D5-07), its slugs and old redirect URLs are released and may be reused. *(Review C-13.)* | Reservation (D6-13) only protects existing content. |
| D6-17 | On Arabic pages, the CV action states that the CV is in English (e.g. "السيرة الذاتية (بالإنجليزية)"). *(Review C-14.)* | The CV is English-only (D6-03); visitors should know before downloading. |

## Content classification (D6-03)

| Bilingual | English-only |
|---|---|
| Entire public site interface (navigation, buttons, messages, 404 page) | Administration dashboard |
| Name, professional positioning, short biography | Case studies |
| Full biography on the About page | CV (PDF) |
| Project title and short summary | Skill and technology names |
| Category names | Experience, education, and certificates |
| Title and description of every page for sharing and search | Names of professional links |
| Contact channel type labels, as interface text *(corrected by D7-06)* | |
| Alternative text (alt) for the project cover image and the profile photo *(refined by D8-10)* | Alternative text (alt) for project gallery images *(D8-10)* |
| WhatsApp prefilled message *(added by D7-04)* | |
| Privacy page content *(added by D9-07)* | |

## Notes

- D1-09 and D1-10 are transferred to this axis as D6-01 and D6-02.
- D5-09 is superseded by D6-04.
