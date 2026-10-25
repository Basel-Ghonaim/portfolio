# 03 — Public Site Structure

**Status:** Approved
**Approved on:** 2026-10-22

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D3-01 | Public pages: Home, Projects (listing), Project detail, About, Privacy *(added by D9-07)*, and a Not Found (404) page in the visitor's language. There is no separate Contact page. | Compact structure that covers all visitor needs. A Contact page has no purpose while the contact form is deferred (D2-04). |
| D3-02 | Content gets its own page if at least one applies: it is too long to show fully on the homepage, it is shared through its own link, or it contains details needed only by some visitors. Otherwise it is a homepage section. | A single, explicit rule keeps the structure easy to navigate and applies to future content. |
| D3-03 | Content placement follows the distribution table below. | Applies D3-02 to current content. |
| D3-04 | Homepage sections: Hero, Contact, and Footer are fixed. Featured Projects, Skills Summary, and Experience Highlights are manageable (order and visibility). | Protects the essential structure while allowing useful control. Implements D2-08. |
| D3-05 | A fixed section is fixed in existence and position only. All variable data inside any section is managed from the dashboard and is never hard-coded. | Routine content changes must not require code changes. |
| D3-06 | Data that appears in more than one place has a single source in the dashboard and is displayed automatically wherever needed (e.g. contact channels, name, positioning, CV link, professional links). | One change updates every occurrence; prevents inconsistent content. |
| D3-07 | Header: Home, Projects, About, a "Contact me" action, language switcher, and light/dark theme switcher. | Covers all primary destinations and controls. |
| D3-08 | An enabled section with no content is hidden automatically. No empty section is ever shown. | Keeps the public experience compact and credible. |
| D3-09 | About page sections have a fixed order. Empty sections are hidden automatically. Their order is not manageable from the dashboard in the first release. | Sufficient for the first release and simpler than full section management. |
| D3-10 | The owner's photo appears in the Hero section and is managed from the dashboard. Its presence on the About page is left to design decisions. | Personal presence on the first screen; About page layout is a design concern. |

## Content distribution (D3-03)

| Content | Homepage | Own page |
|---|---|---|
| Introduction and positioning | Hero section | — |
| Projects | Featured projects only | Projects listing, and one page per project |
| Skills and technologies | Summary | Full list on About |
| Experience | Highlights | Full list on About |
| Education and certificates | — | About |
| Full biography | — | About |
| CV | Action in Hero | Action on About |
| Contact | Fixed section; also in the footer of every page | — |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D3-11 | The theme follows the visitor's device setting by default. A theme chosen with the theme switcher is remembered locally. *(Review C-05.)* | D2-07 confirmed theme support but not default or persistence; mirrors language-preference behavior. |
| D3-12 | Any action or element without content is hidden automatically, not only sections (e.g. the CV action when no CV is uploaded, the profile photo when none is uploaded). Extends D3-08. *(Review C-09.)* | Nothing empty or broken is ever shown. |

## Deferred to other axes

- Featured-project rules and project listing/filtering behavior → axis 04.
- Language switcher behavior and URLs → axis 06.
