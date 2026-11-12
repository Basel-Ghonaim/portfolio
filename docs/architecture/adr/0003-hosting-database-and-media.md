# ADR 0003 — Hosting, Database, and Media Storage

**Status:** Accepted
**Date:** 2026-11-12

## Context

The first release must run at zero cost (PRD; D10-09, D10-10). The owner already runs Masaha on Vercel and Neon on free plans, in the Frankfurt region, and the experience is fully satisfactory. The owner will never add a payment card to any service and will not use any service that could cost money, not even one cent. If the portfolio succeeds, it may later move to paid official hosting.

## Decision

1. **Application hosting:** Vercel, free Hobby plan, for the current stage. One Express server and one origin, as defined in ADR 0002.
2. **Database:** Neon, free plan (PostgreSQL).
3. **Region:** Frankfurt for both the application and the database, as in Masaha, so requests between them stay fast.
4. **Media storage:** Cloudinary, free plan, for images and the CV.
   - Files are uploaded directly from the browser to Cloudinary with a signed upload issued by the server, so files never pass through the Vercel function. This avoids the function request-size limit, which is believed to be about 4.5 MB, below the 5 MB limit set in D8-02.
   - Image optimization required by D8-03 (resizing, a lighter format, removal of location metadata) uses Cloudinary transformations.
5. **Stable CV link:** the public CV link is the portfolio's own route, which serves the current file stored in Cloudinary. The link never changes when the file is replaced, whatever the storage provider (D8-13).
6. **Cost rule:** no service may require a payment card or be able to charge money. Every service must stop at its free limits rather than bill.
7. **Fewest providers:** Vercel, Neon, and Cloudinary only for hosting, data, and media.
8. **Portability:** because hosting may later move to paid official hosting, the code stays provider-neutral:
   - a standard Express application;
   - a standard PostgreSQL connection through Prisma;
   - file storage behind a small internal interface, so Cloudinary can be replaced without touching features;
   - all provider settings in environment variables.

## Verifications at setup time

These are believed true but must be confirmed against current official terms before the foundations are built:

- the Vercel function request-size limit and maximum execution duration;
- Neon free-plan behavior on inactivity: no project deletion or suspension that violates D10-09, and a fast wake-up;
- Cloudinary free-plan delivery of PDF files (free accounts may restrict PDF delivery by default) and the free-plan limits;
- Vercel Hobby fair-use terms for a personal portfolio.

## Alternatives rejected

- **Hosts whose free plans sleep the server for long periods:** the first visitor would wait 30–60 seconds; recruiters open a link once.
- **Any service requiring a payment card, or able to charge:** violates the owner's cost rule.
- **Uploading files through the Express function:** blocked by the function request-size limit.

## Consequences

- The owner reuses a deployment setup proven in Masaha.
- Image optimization comes from Cloudinary, with no image-processing code on the server.
- Moving to paid hosting later requires configuration changes, not a rewrite.
