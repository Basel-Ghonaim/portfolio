# Product Requirements Document (PRD)
## Developer Portfolio Platform

| | |
|---|---|
| **Version** | 1.0 |
| **Status** | Approved by the product owner |
| **Date** | 2026-10-24 |
| **Approved on** | 2026-10-24 |
| **Language** | English |
| **Decision record** | [`decisions/`](decisions/README.md) — product decisions, one file per discussion axis, with the rationale for every decision |
| **Scope** | Product requirements only. No technology selection, architecture, or implementation plan. |

Every requirement references its source decision in brackets, e.g. **[D4-01]**. When this document and a decision file differ, the decision file is authoritative and this document must be corrected.

---

## 1. Product Overview

### 1.1 Vision
A personal, bilingual developer portfolio that presents the owner as a **Frontend-focused Full-Stack Developer** and evolves with the owner's work. It is managed entirely from a private dashboard, so routine changes never require code changes.

### 1.2 Goals [D1-01]
A balanced, simple mix of three goals:
1. Help the owner get employment (full-time or remote).
2. Attract freelance clients.
3. Build a public professional presence.

### 1.3 Audience [D1-03]
One clear experience serves all visitors: technical and non-technical recruiters, engineers, and project owners. There are no separate paths per audience. Most current visitors are expected to be Arabic speakers, but English is the primary language of the product [D1-04].

### 1.4 Positioning [D1-06]
"Frontend-focused Full-Stack Developer". Backend work is highlighted in project case studies as evidence. The positioning text is editable from the dashboard and evolves with the owner's experience.

### 1.5 Visitor journey
Visitors mainly arrive through links the owner shares (social platforms, applications, messages) [D1-02, D1-05]. Within a minute they should see a clear, attractive portfolio, be able to contact the owner easily, download the CV, and browse projects similar to what they need. The primary call to action is **"Contact me"**; CV download is visible but secondary [D1-07].

### 1.6 Independence [D2-02]
The portfolio is an independent project. It has no technical or schedule dependency on any project it showcases (e.g. Masaha, QuickTweet). Showcased projects are content managed manually and may be shown while still in development.

---

## 2. Release Scope

### 2.1 First release
A medium-sized release focused on quality, without unjustified complexity, growing incrementally afterwards. There is no launch deadline [D2-01].

**Included:**
- Public site: Home, Projects, Project detail, About, Privacy, Not Found [D3-01, D9-07]
- Administration dashboard [D2-03]
- Arabic (RTL) and English (LTR) [D1-04]
- Light and dark themes [D2-07]
- Projects with case studies, simple categorization and filtering [D2-06]
- Direct contact channels [D2-04, D2-11]
- Images, YouTube video links, and CV [axis 08]
- Simple, privacy-respecting analytics [D2-05]
- Tested backup and restore [D2-09]

### 2.2 Excluded from the first release [D2-10]
Blog, testimonials, services section, project search, direct video upload, and contact form. Any of these may be reopened by explicit decision.

### 2.3 Future evolution [D1-08]
The first release is a portfolio, not a platform. Decisions that would block future evolution into a platform are avoided.

---

## 3. Core Principles

| Principle | Requirement |
|---|---|
| No hard-coded content | A fixed section is fixed in existence and position only. All variable data is managed from the dashboard [D3-05]. |
| Single source | Data shown in several places is managed once and displayed everywhere it is needed (e.g. contact channels, name, positioning, CV link) [D3-06]. |
| Nothing empty | Sections, actions, and elements without content are hidden automatically [D3-08, D3-12]. A failed image is not shown at all [D8-09]. |
| Truthfulness | No fabricated data, no false claims, private repositories never presented as public [D4-07, D9-06]. |
| Zero mandatory cost | The first release runs without mandatory spending; services must permit the intended use [D10-09, D10-10]. |
| Proportionate | Simple, maintainable solutions suited to a personal project. |

---

## 4. Public Site

### 4.1 Pages [D3-01]
| Page | Content |
|---|---|
| Home | Hero, Featured Projects, Skills Summary, Experience Highlights, Contact, Footer |
| Projects | Listing of published projects with filtering |
| Project detail | Title, summary, status, case study, media, links |
| About | Full biography, experience, education, certificates, full skills, CV action |
| Privacy | What is measured, no personal data collected, YouTube loads on click [D9-07] |
| Not Found | Simple message in the visitor's language [D10-08] |

There is no separate Contact page.

### 4.2 Page vs. section rule [D3-02]
Content gets its own page if it is too long for the homepage, is shared through its own link, or contains details only some visitors need. Otherwise it is a homepage section.

### 4.3 Content placement [D3-03]
| Content | Homepage | Own page |
|---|---|---|
| Introduction and positioning | Hero | — |
| Projects | Featured only | Listing and per-project pages |
| Skills and technologies | Summary | Full list on About |
| Experience | Highlights | Full list on About |
| Education and certificates | — | About |
| Full biography | — | About |
| CV | Action in Hero | Action on About |
| Contact | Fixed section, plus footer on every page | — |

### 4.4 Homepage sections [D3-04]
- **Fixed:** Hero, Contact, Footer.
- **Manageable (order and visibility):** Featured Projects, Skills Summary, Experience Highlights.

### 4.5 About page [D3-09]
Sections have a fixed order; empty sections are hidden automatically.

### 4.6 Hero [D3-04, D3-10, D1-07]
Owner photo (managed from the dashboard), name, positioning, "Contact me" action, and CV action. No contact channels appear in the Hero [D7-03].

### 4.7 Header [D3-07]
Home, Projects, About, "Contact me", language switcher, theme switcher. The footer additionally links to the Privacy page [D9-07].

### 4.8 Themes [D2-07, D3-11]
Light and dark themes across all screens. The default follows the visitor's device setting; a theme chosen with the switcher is remembered locally.

---

## 5. Projects

### 5.1 Progress [D4-01, D4-10, D4-13]
- Progress status: **In Development** or **Completed**, shown as a badge with a "Last updated" date. Completion percentages are not shown.
- The date is never typed manually. When saving, the owner can choose "Mark as progress update"; the date is set when that change is **published**. Otherwise the date stays unchanged.

### 5.2 Featured projects [D4-02, D4-03, D4-04, D4-11, D4-12, D5-05]
- Projects in development may be featured.
- The owner selects featured projects and their order manually; the homepage shows exactly the selection. No maximum-count setting.
- Learning projects are never featured. A published change that makes a project "Learning" removes its featured status automatically.
- Archiving removes featured status automatically.
- Featured selection, featured order, and listing order are display settings applied immediately.

### 5.3 Learning projects [D4-04]
Shown under the "Learning" category. Only those the owner publishes are shown.

### 5.4 Categories and filtering [D4-05, D4-06, D5-14]
- Two kinds of categories: by **type** (e.g. Full-Stack, Frontend, Backend, Learning) and by **domain**. A project may belong to several.
- Category names are bilingual [D6-03].
- Filtering appears only when at least two categories contain published projects: a single list of all categories, one selected at a time, plus "All".
- Deleting a category in use removes it from its projects after a confirmation showing how many projects are affected.

### 5.5 Listing order [D4-09]
Set manually from the dashboard.

### 5.6 Links and private repositories [D4-07]
Optional links (e.g. live demo, repository). A private repository shows a "Private repository" badge with no link; the case study and media serve as evidence.

### 5.7 Case studies [D4-08, D6-01]
- English-only.
- A fixed catalog of optional, reorderable sections: Context/Problem, Goals, Role, Approach, Technical Decisions, Challenges, Outcomes, Technologies, Media, Links. Empty sections are not shown.
- Formatting supports headings, paragraphs, lists, links, and images, without becoming a page builder [D4-14].

---

## 6. Content Management and Publishing

### 6.1 Two publishing models [D5-01, D5-02]
| Content | Behavior |
|---|---|
| **Projects** | Edits to a published project are saved privately. Visitors keep seeing the published version until the owner explicitly publishes. |
| **All other content** (biography, positioning, skills, experience, education, certificates, professional links, contact channels, categories, homepage sections, share metadata) | Visible immediately on save. Each item can be shown or hidden. |

### 6.2 Bilingual completeness on save [D5-10, D6-04]
For immediately visible content, saving is blocked until all bilingual fields of the item are complete; a message lists the missing fields. Projects cannot be published until their bilingual fields are complete.

### 6.3 Project states [D5-04]
| State | Visibility |
|---|---|
| Draft | Owner only |
| Published | Visitors |
| Archived | Removed from the public site entirely, unreachable even through direct URLs, kept in the dashboard |

### 6.4 Project lifecycle rules
- **Preview** as visitors will see it, in both languages and both themes, visible only to the owner [D5-03, D5-12].
- **Discard changes** reverts unpublished changes to the published version, after confirmation [D5-13].
- **Archive** removes featured status [D5-05] and keeps unpublished changes [D5-11].
- **Restore** returns the project to Draft, with its kept changes [D5-06, D5-11].
- **Permanent deletion** is available only for archived projects and requires explicit confirmation [D5-07]. It releases the project's slugs [D6-16].

### 6.5 Deleting other items [D5-08]
Direct deletion after a confirmation prompt, without a trash system. Backups are the safety net.

### 6.6 Dashboard
- English-only [D6-02].
- Includes a Settings page for values the owner genuinely needs to change (first setting: gallery image maximum) [D8-06]. Security limits stay fixed.
- Links to the analytics tool's dashboard [D9-03].

---

## 7. Languages and URLs

### 7.1 Content classification [D6-03, D7-04, D7-06, D8-10, D9-07]
| Bilingual | English-only |
|---|---|
| Entire public interface (navigation, buttons, messages, 404) | Administration dashboard |
| Name, positioning, short biography | Case studies |
| Full biography (About) | CV (PDF) |
| Project title and short summary | Skill and technology names |
| Category names | Experience, education, certificates |
| Page titles and descriptions for sharing and search | Names of professional links |
| Alt text for cover images and the profile photo | Alt text for project gallery images |
| WhatsApp prefilled message | |
| Privacy page content | |
| Contact channel type labels (interface text) | |

English-only content never requires translation and never blocks publication [D6-04].

### 7.2 Mixed-language display [D6-05, D6-17]
- English content inside Arabic pages displays correctly left-to-right; surrounding headings and labels remain Arabic.
- Arabic project pages show the title and summary in Arabic, a short note that the case study is in English, then the case study.
- On Arabic pages the CV action states that the CV is in English.

### 7.3 URLs [D6-06, D6-07]
- Each language has its own path: `/en/...` and `/ar/...`.
- One Latin slug is shared by both languages: `/en/projects/masaha` ↔ `/ar/projects/masaha`.

### 7.4 Language selection [D6-08 – D6-11]
- `/` opens the saved language, otherwise English.
- An explicit language URL always takes precedence over the saved preference.
- The saved preference changes only through the language switcher.
- The switcher opens the same page in the other language, keeping the selected filter. If impossible, it opens the nearest parent page (the Projects listing).

### 7.5 Slug stability [D6-12 – D6-16]
- A slug does not change when a title changes. The owner can change it manually; the old URL redirects to the new one.
- A slug change within unpublished changes takes effect on publish; the new slug is reserved meanwhile.
- A slug used by a redirect cannot be assigned to another project.
- Current and old URLs of an archived project return Not Found.
- Permanent deletion releases the project's slugs and redirects.

---

## 8. Contact Channels

- First-release channels: email, WhatsApp, LinkedIn, GitHub [D2-11].
- Channels are chosen from a predefined list of supported types, each with a design icon and a bilingual interface label. The owner adds the value and manages order and visibility. A new type requires a small code addition [D7-06].
- **"Contact me"** takes the visitor to the homepage Contact section (from other pages, the homepage at that section). It does not open email directly [D7-02].
- **Placement** [D7-03]: the Contact section shows all visible channels with name and value plus "copy email"; the footer shows them as icons on every page; the Hero shows no channels.
- **WhatsApp** opens with a prefilled message in the page language, managed in both languages and editable by the visitor [D7-04].
- **Copy email** shows a short "Copied" confirmation in the page language, announced to screen readers [D7-05].
- WhatsApp currently uses the owner's personal number, to be replaced by a business number later (owner's accepted choice) [axis 02 notes].

---

## 9. Media, Sharing, and CV

### 9.1 Uploads [D8-01 – D8-03]
- Types: JPG, PNG, WebP for images; PDF for the CV only. SVG uploads are not allowed.
- Size: 5 MB per image, 5 MB for the CV. Fixed limits.
- Images are optimized automatically: dimensions reduced, converted to a lighter format, location metadata removed.

### 9.2 Project images [D8-04 – D8-08, D8-11]
- One cover image per project, used in the listing, Featured Projects, and the share preview.
- A gallery with multi-image batch upload and manual ordering. On partial failure, successful images are kept and failures are reported with reasons.
- Gallery maximum: 20 by default, configurable in Settings within 1–50. Batch uploads are limited by remaining capacity. Lowering the maximum never deletes existing images.
- Gallery images appear in the case study's Media section and may also be placed inside other sections.
- Clicking an image enlarges it within the site, with navigation between gallery images.
- No central media library; images belong to their item. An image used by a published version is never deleted, even if replaced in a draft.

### 9.3 Alternative text [D8-10]
Required for every meaningful image (one short sentence): bilingual for cover images and the profile photo, English for gallery images. Decorative images are marked as decorative.

### 9.4 Video [D8-12]
YouTube links only. Videos play inside the site; a thumbnail with a play button is shown and the player loads only on click. No limit on the number of links.

### 9.5 Sharing and search [D1-02, D1-05, D8-14]
- Every public page has a share preview (title, description, image) in its language.
- Project pages use their cover image, title, and summary. Other pages use a default share image plus per-page bilingual titles and descriptions, all managed from the dashboard.
- Basic search readiness: stable URLs, per-page titles and descriptions, sitemap, exclusion of drafts, archived content, previews, and the dashboard, and semantic structure. No search content strategy.

### 9.6 CV [D8-13]
A single English PDF with a stable link that never changes when the file is replaced, downloaded with a clear name (e.g. `YourName-CV.pdf`). No version history; backups preserve previous files.

---

## 10. Analytics and Privacy

- **Metrics** [D9-01, D9-02]: visits; views per project (both languages counted together); traffic sources; CV downloads; clicks per contact channel; page language; device type.
- **Viewing** [D9-03]: in the analytics tool's own dashboard, linked from the administration dashboard.
- **Privacy** [D9-04]: no cookies and no personal data, so no consent banner. Any tool selected later must satisfy this. Legal requirements per jurisdiction are not assessed in this document.
- **Exclusions** [D9-05, D9-06]: the owner's own visits and, where possible, bot traffic.
- **Truthfulness** [D9-06]: unavailable sources are shown as "Unknown"; true zero is distinguished from unavailable data.
- **Privacy page** [D9-07]: short, bilingual, linked from the footer.

---

## 11. Security and Operations

- **Sign-in** [D10-01]: the owner's GitHub account only; any other account is rejected. No passwords in the first release. No public registration.
- **Recovery** [D10-02]: through GitHub account recovery first; an emergency path requires access to the owner's hosting environment and cannot be performed from the site.
- **Sessions** [D10-03]: 7 days unless signed out; "Sign out of all devices"; repeated failed sign-ins are slowed down.
- **Unsaved work** [D10-04]: warning before leaving a page with unsaved changes; an expired session does not lose unsaved work. No autosave.
- **Backups** [D2-09, D10-05, D10-06]: database and files; weekly (automatic where the free service allows, otherwise "Back up now" with a dashboard reminder); last 4 kept, stored outside the main hosting provider; restore tested before launch and every 6 months; failures shown as a dashboard alert.
- **Resilience** [D10-07]: if a secondary external service fails, the site keeps working and only the affected part is unavailable.
- **Errors and secrets** [D10-08]: simple error messages in the visitor's language without technical details; secrets never appear in code, the repository, logs, frontend output, or error messages.
- **Server-side authorization** [D10-11]: every protected operation is authorized on the server side; all inputs and uploaded files are validated.
- **Provider criterion** [D10-09]: services must not suspend the project or delete data because of low activity.
- **Domain** [D10-10]: a free provider subdomain for the first release; when moving to a custom domain later, old links redirect where the host allows.

---

## 12. Quality Requirements

| Area | Requirement |
|---|---|
| Performance [D11-01] | LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1. Release gate: lab measurement on Home, Projects listing, one case study, and About, in both languages and themes, with a mid-range mobile simulation. Field data monitored after launch when available. |
| Accessibility [D11-02] | WCAG 2.2 AA for the public site and the dashboard. Automated checks plus a manual keyboard and screen-reader pass, in RTL and LTR. |
| Browsers [D11-03] | Latest two major versions of Chrome, Edge, Firefox, and Safari, including Safari on iPhone and iPad. |
| Screens [D11-04] | Mobile, tablet, desktop. Minimum width 320 px, no horizontal scrolling. |
| States [D11-08] | Clear loading, empty, success, and error states on the public site and the dashboard. |

---

## 13. Acceptance Criteria

### 13.1 Priority tests [D11-05]
1. Any account other than the owner's GitHub account is rejected at sign-in.
2. Drafts and archived projects are never visible to visitors by any means, including direct and old URLs.
3. Unpublished project changes are not visible before publishing; the published version stays intact.
4. Publishing or saving content with incomplete bilingual fields is blocked, and the missing fields are listed.
5. After a slug change, the old URL redirects in one step to the current URL.
6. The language switcher opens the equivalent page in the other language, keeping the filter.
7. Image uploads respect type, size, and gallery limits; on partial failure, successful images are kept and failures are reported.
8. The CV link remains the same after the file is replaced and serves the new file.
9. A backup can be restored into a clean environment, reproducing content and media without broken references.

### 13.2 Release readiness [D11-06, D11-07]
The first release is ready when:
- All approved decisions in axes 01–10 are met.
- All priority tests pass.
- Performance and accessibility criteria are met.
- One actual restore has succeeded.
- No known critical security, accessibility, or data-loss defect remains open.

Non-critical defects do not block launch if they are documented and scheduled for fixing.

---

## 14. Risks

| Risk | Mitigation |
|---|---|
| Free-tier terms, quotas, or inactivity policies change | Provider criterion [D10-09], backups outside the main provider [D10-05], portability |
| Content exists only in the dashboard | Weekly backups, tested restore, failure alerts [D10-05, D10-06] |
| Bilingual content drifts | Save and publish blocked until complete [D5-10, D6-04] |
| Shared links break | Stable slugs, redirects, stable CV link [D6-12, D8-13], domain redirects [D10-10] |
| Personal WhatsApp number is public | Owner's accepted choice; replaced by a business number later |
| Unsupported claims undermine trust | Honest positioning, status badges, private-repository badge [D1-06, D4-01, D4-07] |
| GitHub account loss locks out the dashboard | Emergency recovery through the hosting environment [D10-02] |

---

## 15. Out of Scope for This Document

The following are decided in later phases, each requiring explicit authorization:
- Assessment of reusable assets from Masaha.
- Technology and service-provider selection (must satisfy D9-04, D9-05, D10-09, and zero mandatory cost).
- System architecture.
- Implementation plan.

Design-level details (e.g. visual layout, numeral style in Arabic dates, photo placement on About) are left to the design phase.
