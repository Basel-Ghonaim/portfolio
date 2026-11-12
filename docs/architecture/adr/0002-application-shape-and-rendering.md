# ADR 0002 — Application Shape and Rendering

**Status:** Accepted
**Date:** 2026-11-12

## Context

The portfolio is a small personal site, not a high-traffic platform. It must stay simple, light, and close to the owner's existing expertise (React with `react-router-dom`, as in Masaha). At the same time, the PRD requires:

- a share preview (title, description, image) for every public page, in its language (D1-02, D8-14);
- basic search readiness (D1-05);
- performance targets that are a launch gate, measured in the lab on a mid-range mobile profile: LCP ≤ 2.5 s, INP ≤ 200 ms, CLS ≤ 0.1 (D11-01).

Link-preview crawlers do not run JavaScript, so every public page must deliver initial HTML containing its language, direction, and metadata (reuse constraint R4-C1).

## Decision

1. **Rendering:** the frontend is a single-page application built with `react-router-dom` (library mode) and Vite, as in Masaha. There is no server-side rendering framework.
2. **Server-injected HTML:** for every public URL, Express serves the application HTML with the following injected before sending:
   - `lang` and `dir` on `<html>`, derived from the URL language prefix (D6-06);
   - page title, description, and share-preview tags (D1-02, D8-14);
   - a preload hint for the project cover image on project pages (LCP image);
   - the page's initial public data embedded in the HTML, so the page renders without an extra request after the JavaScript loads.
3. **Pre-paint script:** limited to the light/dark theme only (stored choice, otherwise device setting — D3-11), since language and direction come from the server.
4. **One frontend application:** the public site and the dashboard live in one app, `apps/web`. The dashboard is served under `/admin`, rendered in the browser with TanStack Query, excluded from search (D1-05), and loaded as a separate code chunk only when `/admin` is opened, so visitors never download dashboard code.
5. **Repository shape:** `apps/web` (frontend), `apps/api` (Express API modules), `packages/shared` (Zod schemas and request/response types — ADR 0001).
6. **One server, one origin:** a single Express server serves the API under `/api/v1` and the application HTML for all routes. Same-origin cookies support the GitHub sign-in session (D10-01, D10-03) without CORS configuration.
7. **Design layer location:** `apps/web/src/shared/design-system/`, as in Masaha (resolves reuse decision R1-05). Its independence (exports only, never imports from the rest of the app) is enforced by an ESLint boundary rule (R9-03).
8. **Performance budget:** the initial JavaScript of the public site must not exceed **150 KB compressed (gzip)**, checked automatically in CI.

## Alternatives rejected

- **Next.js:** a new mental model (server/client components, caching rules) and overlap with Express; excluded by the owner.
- **React Router framework mode (server rendering):** better initial content and search indexing, but adds new conventions (route modules, loaders, server entry, server/client code awareness). Not justified for a small, low-traffic portfolio when the owner prefers known tools.
- **Two frontend applications (site and dashboard):** two build setups and duplicated configuration with no benefit for a single administrator.
- **Separate API and frontend origins:** requires CORS and cross-site cookie handling for no benefit.

## Consequences

- The owner works entirely with known tools; Masaha's frontend structure transfers with minimal change.
- Share previews, language, and direction are correct for every public page (R4-C1 satisfied for metadata).
- Page content is rendered in the browser. This is accepted for the basic search readiness required by D1-05.
- Performance on mobile is the main risk; it is mitigated by embedded initial data, the LCP image preload, the separate dashboard chunk, and the enforced JavaScript budget. If the lab performance gate (D11-01) cannot be met, this decision is revisited in a new ADR (e.g. pre-rendering public pages or server rendering).
