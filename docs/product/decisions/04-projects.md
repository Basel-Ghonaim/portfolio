# 04 — Projects

**Status:** Approved
**Approved on:** 2026-10-22

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D4-01 | Project progress is either "In Development" or "Completed". Visitors see a status badge and a "Last updated" date. Completion percentages are not shown. | Status and date stay truthful without ongoing maintenance. Percentages go stale, cannot be verified by visitors, and may be read negatively. |
| D4-02 | Projects in development may be featured. | The owner's strongest work (e.g. Masaha, QuickTweet) is currently in development (see D2-02). |
| D4-03 | Featured projects and their order are selected manually. There is no separate maximum-count setting: the homepage shows exactly the projects the owner selects, in the owner's chosen order. | Full manual control in a single step, without an extra setting. |
| D4-04 | Learning projects are shown under the "Learning" category and are never featured on the homepage. Only the learning projects the owner chooses to publish are shown. | Shows the learning journey without weakening the impression of the strongest work. |
| D4-05 | Categories are of two kinds: by type (e.g. Full-Stack, Frontend, Backend, Learning) and by domain. "Learning" is a type category. A project may belong to more than one category. | Supports describing projects accurately without a rigid single classification. |
| D4-06 | Project filtering is shown only when at least two categories contain published projects. It is a single list of all categories with one category selected at a time, plus an "All" option. | Avoids a useless filter with few projects; a single list is sufficient for a small number of projects. |
| D4-07 | A project with a private repository shows a "Private repository" badge with no link. The case study and media serve as evidence. | Private repositories must not be presented as publicly accessible. |
| D4-08 | Case studies use a fixed catalog of sections, all optional and reorderable: Context/Problem, Goals, Role, Approach, Technical Decisions, Challenges, Outcomes, Technologies, Media, Links. Empty sections are not shown. | Flexible enough for different projects without becoming a page builder. |
| D4-09 | The order of projects on the Projects listing page is set manually from the dashboard. | The owner controls how work is presented. |
| D4-10 | The "Last updated" date is never typed manually. When saving a project, the owner can choose an explicit action (e.g. a "Mark as progress update" option) that sets the date to the time of saving. Saving without choosing it leaves the date unchanged. *(Timing refined by D4-13.)* | The date reflects real project progress, not minor portfolio edits such as typo fixes, without requiring manual date entry. |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D4-11 | Featured selection, featured order, and Projects listing order are display settings applied immediately. They are not subject to the staged publishing of project content (D5-01). *(Review C-04.)* | Staged publishing protects project content; display settings are simple choices that need no review step. |
| D4-12 | When a published change makes a project "Learning", its featured status is removed automatically. *(Review C-04.)* | Keeps D4-04 true at all times. |
| D4-13 | The "Last updated" date chosen with "Mark as progress update" (D4-10) is applied when that change is published, not when it is saved privately. Refines the timing in D4-10. *(Review C-08.)* | Under staged publishing (D5-01), the save time can be days before visitors see the change. |
| D4-14 | Case-study formatting supports headings, paragraphs, lists, links, and images, without becoming a page builder. *(Approved with PRD v1.0.)* | Enough structure for clear case studies while staying within D4-08. |

## Deferred to other axes

- Bilingual vs. English-only classification of project fields (titles, summaries, category names) → axis 06. Case studies are English-only (D1-09).
- Publication states, drafts, archiving, and restoration of projects → axis 05.
- Project URLs and slugs → axis 06.
- Project media types and limits → axis 08.
