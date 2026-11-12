# Glossary

**Status:** Active
**Last updated:** 2026-11-12

This is the canonical vocabulary of the portfolio: code, documentation, and interface text use these terms. Product decisions are recorded in [`decisions/`](decisions/README.md) and technical decisions in the [architecture decision records](../architecture/adr/README.md).

In the Arabic column, `—` marks a term that does not appear by name on public Arabic pages: it is used only in the English-only dashboard [D6-02] or case studies [D6-01], or visitors never see it named.

| Term | Arabic | Meaning |
|---|---|---|
| **Owner** | — | The person the portfolio presents and the dashboard's only user, who signs in with their GitHub account only [D6-02, D10-01]. |
| **Dashboard** | — | The private, English-only administration dashboard from which all variable content is managed without code changes [D2-03, D3-05, D6-02]. The analytics tool's own dashboard is called *the analytics tool's dashboard* [D9-03]. |
| **Positioning** | المسمّى المهني | The owner's professional title, bilingual and editable from the dashboard [D1-06, D6-03]. |
| **"Contact me"** | تواصل معي | The primary call to action, which takes the visitor to the homepage Contact section and does not open email directly [D1-07, D7-02]. |
| **Homepage section** | قسم الصفحة الرئيسية | Either fixed in existence and position (Hero, Contact, Footer) or manageable in order and visibility from the dashboard (Featured Projects, Skills Summary, Experience Highlights) [D3-04, D3-05]. |
| **Projects listing** | صفحة المشاريع | The public page of published projects, in an order set manually from the dashboard [D3-01, D4-09]. |
| **Project page** | صفحة المشروع | The public page of one project, with its title, summary, progress status, case study, media, and links [D3-01]. |
| **Profile photo** | الصورة الشخصية | The owner's photo, shown in the Hero and managed from the dashboard, with bilingual alternative text [D3-10, D8-10]. |
| **Project** | مشروع | A piece of the owner's work shown on the site, managed manually as content and possibly shown while still in development [D2-02]. |
| **Progress status** | حالة التقدّم | **In Development** (قيد التطوير) or **Completed** (مكتمل), shown to visitors as a badge with the "Last updated" date and never as a percentage [D4-01]. |
| **Last updated** | آخر تحديث | The date shown with the progress status, never typed manually: it is set when a change saved with "Mark as progress update" is published [D4-10, D4-13]. |
| **Featured** | مميّز | A project the owner selects and orders by hand for the homepage Featured Projects section, as a display setting applied immediately; Learning and archived projects are never featured [D4-03, D4-04, D4-11, D5-05]. |
| **Learning** | تعلّم | The type category of learning projects, which are shown only when the owner publishes them and are never featured [D4-04, D4-05]. |
| **Category** | تصنيف | A bilingual label that groups projects by type (e.g. Full-Stack, Frontend, Backend, Learning) or by domain; a project may belong to several [D4-05, D6-03]. |
| **Filter** | تصفية | The single list of categories on the Projects listing, one selected at a time plus "All" (الكل), shown only when at least two categories contain published projects [D4-06]. |
| **Private repository** | مستودع خاص | The badge, without a link, shown for a project whose repository is private [D4-07]. |
| **Case study** | دراسة حالة | The English-only account of a project, built from case study sections; on Arabic project pages a short note that it is in English comes first [D6-01, D6-05]. |
| **Case study section** | — | One of a fixed catalog of optional, reorderable sections: Context/Problem, Goals, Role, Approach, Technical Decisions, Challenges, Outcomes, Technologies, Media, Links; empty ones are not shown [D4-08]. On Arabic pages its headings stay in English, as part of the English-only case study [D6-01]. |
| **Staged publishing** | — | The publishing model of projects: edits to a published project are saved privately and reach visitors only when the owner publishes them [D4-11, D5-01]. |
| **Immediately visible content** | — | All content other than projects (e.g. biography, skills, contact channels, categories), visible on save, shown or hidden item by item, and saved only when its bilingual fields are complete [D5-02, D5-10, D5-14]. |
| **Draft** | — | The project state visible only to the owner, to which a restored project returns [D5-04, D5-06]. The pending edits to a published project are *Unpublished changes*, never a draft. |
| **Published** | — | The project state visible to visitors; a project is published only when its bilingual fields are complete [D5-04, D6-04]. |
| **Archived** | — | The project state removed from the public site entirely, unreachable even through direct or old URLs, and kept in the dashboard without featured status [D5-04, D5-05, D6-14]. |
| **Unpublished changes** | — | Privately saved edits to a published project, which visitors do not see until the owner publishes them or reverts them with "Discard changes" [D5-01, D5-13]. |
| **Preview** | — | The owner-only view of a project as visitors will see it, in both languages and both themes [D5-03, D5-12]. |
| **Restore** | — | Returns an archived project to Draft, together with the unpublished changes kept when it was archived [D5-06, D5-11]. Restoring a backup is called *backup restore* [D10-05]. |
| **Permanent deletion** | — | Deleting a project for good, available only for archived projects after explicit confirmation, which releases its slugs and redirects [D5-07, D6-16]. |
| **Bilingual content** | — | Content that cannot be published or shown publicly until it is complete in both Arabic and English [D6-03, D6-04]. |
| **English-only content** | — | Content kept in English only, such as case studies and the CV, which never requires translation and never blocks publication [D6-03, D6-04]. |
| **Slug** | — | The single Latin name in a project's URLs, shared by both languages (e.g. `/en/projects/masaha` and `/ar/projects/masaha`) and changed only by hand, with the old URL redirecting to the new one [D6-07, D6-12]. |
| **Contact channel** | وسيلة تواصل | A direct way to reach the owner (short form *channel*), of a predefined type such as email, WhatsApp, LinkedIn, or GitHub; the owner sets its value, order, and visibility [D2-11, D7-06]. |
| **Cover image** | صورة الغلاف | The one image of a project used in the Projects listing, Featured Projects, and the project's share preview [D8-04]. |
| **Gallery** | — | A project's manually ordered images, uploaded in batches up to a maximum set in Settings and shown in the case study's Media section [D8-05, D8-06, D8-07]. |
| **Share preview** | — | The title, description, and image shown in the page's language when a link to a public page is shared [D1-02, D8-14]. |
| **CV** | السيرة الذاتية | A single English PDF behind a stable link that never changes when the file is replaced; on Arabic pages its action states that it is in English («السيرة الذاتية (بالإنجليزية)») [D6-17, D8-13]. |
