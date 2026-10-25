# 05 — Content Management and Publishing

**Status:** Approved
**Approved on:** 2026-10-22

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D5-01 | Projects: edits to a published project are saved privately and are not visible to visitors until the owner explicitly publishes them. The published version remains unchanged until then. | Projects, especially case studies, are long content written in stages; visitors must never see a half-finished edit. |
| D5-02 | All other content (biography, skills, experience, education, certificates, professional links, contact channels, homepage sections) is visible immediately on save. Each item has a show/hide option. *(Save rule added by D5-10; categories added by D5-14.)* | This content is short and usually edited in one session. A draft-and-approve workflow for every type would multiply dashboard complexity without real benefit. |
| D5-03 | The owner can preview a project as visitors will see it, in light and dark themes, before publishing. The preview is visible only to the owner. Preview stays simple. | Allows checking content before it becomes public, without adding a complex review workflow. |
| D5-04 | Project publication states: Draft (visible only to the owner), Published (visible to visitors), Archived (removed from the public site entirely, not reachable even through its direct URL, and kept in the dashboard). | Three states cover the full project lifecycle. |
| D5-05 | Archiving a project removes its featured status automatically. | An archived project cannot appear anywhere on the public site. |
| D5-06 | Restoring an archived project returns it to Draft. Publishing it again is a deliberate action. | Prevents old content from reappearing publicly without review. |
| D5-07 | Project deletion: archiving serves as the recoverable state. Permanent deletion is available only for archived projects and requires explicit confirmation. | Safe deletion without building a separate trash system. |
| D5-08 | Other items (e.g. a skill, link, or certificate) are deleted directly after a confirmation prompt, without a trash system. Backups remain the safety net. | These are small, easily recreated items; a trash system for every type is not justified for a personal project. |
| D5-09 | Principle (provisional): content cannot be published or shown publicly while its required bilingual fields are incomplete. Applied loosely in this axis; the formal rule and the list of required fields are decided in axis 06 and take precedence. | Prevents incomplete public content without pre-empting the language classification. |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D5-10 | For immediately visible content (D5-02), saving is blocked until all bilingual fields of the item are complete in both languages. A message lists the missing fields. *(Review C-01.)* | Reconciles D5-02 with D6-04. Some of this content sits in fixed sections and cannot be hidden, so blocking the save is simpler than a "saved but hidden" state. |
| D5-11 | Archiving a project keeps its unpublished changes. They return with the project as a draft when it is restored. *(Review C-06.)* | No work is lost through archiving. |
| D5-12 | Project preview (D5-03) is available in both languages as well as both themes. *(Review C-10.)* | The owner must be able to check bilingual parts before publishing. |
| D5-13 | A "Discard changes" action reverts a project's unpublished changes to the published version, after a confirmation prompt. *(Review C-11.)* | Gives the owner a way out of an unwanted draft. |
| D5-14 | Categories are immediately visible content (D5-02). Deleting a category that is in use removes it from its projects after a confirmation prompt showing how many projects are affected. *(Review C-12.)* | Categories were missing from D5-02; deletion impact must be visible before it happens. |

## Deferred to other axes

- Formal bilingual completeness rule and required fields → axis 06. D5-09 is superseded by D6-04.
- Backup scope and procedure → axis 10 (see D2-09).
