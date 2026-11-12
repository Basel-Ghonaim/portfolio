# ADR 0007 — Supporting Libraries

**Status:** Accepted
**Date:** 2026-11-12

## Context

Masaha uses a wider set of libraries than the portfolio needs. The public site must stay light: initial JavaScript ≤ 150 KB gzip (ADR 0002). Public pages receive their data embedded in the HTML, while the dashboard fetches data in the browser. Case studies need headings, paragraphs, lists, links, and images without a page builder (D4-14, R5-05). Brand icons for contact channels need a licensed source (R6-03).

## Decision

### Taken from Masaha's stack
- **Frontend:** Vite, Tailwind CSS v4, shadcn/ui with Radix, `react-router-dom`.
- **Dashboard data and forms (dashboard only):** TanStack Query, react-hook-form, Zod, TanStack Table.
- **Design-system dependencies:** cva, clsx, tailwind-merge, lucide-react, Sonner (toasts), cmdk (category combobox).
- **Backend:** Express 5, Prisma 7, Zod, pino (logging), helmet (security headers).

### Left out
- **react-day-picker:** Calendar and DatePicker are not copied (R5-04).
- **Axios:** replaced by native `fetch` with a small wrapper.
- **Zustand:** state is simple; React context is used where needed.
- **jose:** sessions are stored in the database (ADR 0004).
- **bcrypt:** there are no passwords.
- **sharp:** image processing is done by Cloudinary (ADR 0003).
- **Leaflet:** there are no maps.

### Added
- **Cloudinary SDK (server):** signs direct browser uploads and supports backups (ADR 0003, ADR 0006).

### Case-study editor
- Case studies are written in **Markdown**, with a side-by-side preview in the dashboard.
- Markdown is converted to HTML **on the server**, sanitized, and embedded in the page, so visitors download no editor or parser code.
- The Markdown parser and HTML sanitizer are chosen at setup time, preferring the lightest well-maintained options, and recorded then.

### Brand icons
- The official SVG logos (GitHub, LinkedIn, WhatsApp, X, Telegram) are taken from each brand's own resources and added as components in `iconSet`, following each brand's usage guidelines. No icon library is installed for five logos.

## Alternatives rejected

- **A visual rich-text editor (e.g. TipTap):** heavier and more setup and sanitization work, unjustified for a single developer user.
- **Keeping Axios and Zustand for consistency with Masaha:** extra bundle size with no benefit at this scale.
- **A full brand-icon library:** a dependency for five icons.

## Consequences

- The public bundle carries only what public pages need; dashboard libraries load only in the dashboard chunk.
- Masaha code copied from its `shared/api` layer must be adapted from Axios to `fetch`.
- Stored case-study content is Markdown, portable and readable outside the application.
