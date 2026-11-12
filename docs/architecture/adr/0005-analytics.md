# ADR 0005 — Analytics

**Status:** Accepted
**Date:** 2026-11-12

## Context

The PRD requires simple, privacy-respecting analytics (D9-01 – D9-07):
- visits, views per project (both languages counted together), traffic sources, CV downloads, clicks per contact channel, page language, and device type;
- no cookies and no personal data;
- the owner's visits excluded;
- viewed in the tool's own dashboard.

Every service must be free with no payment card (ADR 0003).

Vercel Web Analytics on the Hobby plan does not support custom events and keeps one month of data, so CV downloads and channel clicks could not be measured (checked 2026-11-12, Vercel docs: "Pricing for Web Analytics").

## Decision

1. **Tool:** Umami Cloud, free Hobby plan. It is cookieless, collects no personal data, supports custom events, and keeps 6 months of data. The owner created the account on 2026-11-12 in the EU data region, without a payment card.
2. **Events:**
   - Visits, sources, and device types are recorded automatically. Page language is visible from the URL prefix (`/ar`, `/en`).
   - Three custom events:
     - `project-view`, with the project's shared slug, so Arabic and English views of a project are combined (D6-07);
     - `cv-download`;
     - `channel-click`, with the channel type.
3. **Owner exclusion:** when the owner signs in to the dashboard, that browser is marked so Umami stops tracking it. Every device the owner signs in from is excluded automatically.
4. **Dashboard:** `/admin` is never tracked.
5. **Loading:** the small tracking script loads after the page, does not count toward the initial JavaScript budget (ADR 0002), and the site keeps working if the service is unavailable (D10-07).
6. **Viewing:** in Umami's own dashboard, linked from the administration dashboard (D9-03).
7. **Privacy page:** states that Umami is used, without cookies or personal data (D9-07).

## Alternatives rejected

- **Vercel Web Analytics (Hobby):** no custom events and only one month of data.
- **Building our own event counting:** would require an analytics page in the dashboard, which D9-03 excludes.

## Consequences

- One more provider (Umami), justified because no current provider meets D9-01 for free.
- If Umami's free terms change, the tracking calls are isolated in one small module so the tool can be replaced.
