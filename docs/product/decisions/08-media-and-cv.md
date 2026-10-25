# 08 — Media and CV

**Status:** Approved
**Approved on:** 2026-10-24

## Decisions

| ID | Decision | Rationale |
|---|---|---|
| D8-01 | Allowed upload types: JPG, PNG, and WebP for images; PDF for the CV only. SVG uploads are not allowed. Icons (technologies, channels) are part of the design. | SVG can contain executable code and securing it adds work without first-release value. |
| D8-02 | Size limits: 5 MB per image and 5 MB for the CV file. These limits are fixed and not configurable from the dashboard. | Practical limits for normal images and CVs. Size and type limits are security limits and stay fixed. |
| D8-03 | Uploaded images are optimized automatically: oversized dimensions are reduced, the format is converted to a lighter one, and location (GPS) metadata is removed. | The owner uploads images as they are; performance targets are supported and location privacy is protected. |
| D8-04 | Each project has exactly one cover image. It appears in the Projects listing and in Featured Projects, and is used as the share-preview image for the project link. | Consistent project presentation and correct share previews (D1-02). |
| D8-05 | Each project has an image gallery. Multiple images can be selected and uploaded in one batch, then ordered manually. If some uploads fail, successful images are kept and the owner sees which images failed and why. | Projects may have many images; uploading one by one is not acceptable. Partial failure must not lose successful work. |
| D8-06 | The maximum number of gallery images per project defaults to 20 and can be changed from the dashboard Settings page within a range of 1–50. Batch uploads are limited by the remaining capacity under this maximum (e.g. 15 existing images with a maximum of 20 allows 5 more). Lowering the maximum never deletes existing images; it only blocks new additions until the count is below the new maximum. | Avoids code changes for a routine adjustment. A single setting avoids conflicting limits; the safe range protects free-tier storage and page performance. |
| D8-07 | Gallery images appear in the case study's Media section. An image can also be placed inside other case-study sections when needed (e.g. a diagram in Technical Decisions). | One clear gallery, with flexibility where an image supports a specific section. |
| D8-08 | Clicking an image enlarges it within the site, with navigation between gallery images. It does not open a separate page. | Visitors stay on the project page. |
| D8-09 | An image that fails to load is not shown at all: no broken-image icon and no visible text in its place. | A failed image must not degrade the page's appearance. |
| D8-10 | Alternative text is required for every meaningful image; one short sentence is sufficient. It is bilingual for the cover image and the profile photo, and English-only for project gallery images. Decorative images are marked as decorative and need no text. | Alt text serves screen-reader users and search engines for images that load normally (WCAG 2.2 AA). It is independent of D8-09. |
| D8-11 | There is no central media library. Images are uploaded within the item they belong to. An image used by a published version is never deleted, even if it is replaced in a draft. | Simpler dashboard; protects published content during staged edits (D5-01). |
| D8-12 | External video in the first release supports YouTube only. Videos play inside the site, never redirecting to YouTube. A thumbnail with a play button is shown, and the player loads only when the visitor clicks. The number of video links is not limited. | Faster pages and no third-party tracking before the visitor chooses to watch. Direct video upload remains excluded (D2-10). |
| D8-13 | The CV is a single file with a stable link that does not change when the file is replaced; every previously shared link always serves the latest CV. The downloaded file has a clear name (e.g. `YourName-CV.pdf`). There is no history of previous versions; backups preserve them. | Links sent in applications must never break or serve an outdated CV. |

## Decisions from the consistency review (2026-10-24)

| ID | Decision | Rationale |
|---|---|---|
| D8-14 | Share previews for pages other than project pages use one default share image managed from the dashboard, plus a title and description per page in both languages managed from the dashboard. Project pages use their cover image, title, and summary automatically. *(Review C-03.)* | D1-02 requires a share preview for every page, but D8-04 covered project pages only. |

## Notes

- D8-06 introduces the dashboard Settings page. Only settings the owner genuinely needs to change are added there; security limits stay fixed.
- D8-10 refines the alt-text rows of the content classification in axis 06.
