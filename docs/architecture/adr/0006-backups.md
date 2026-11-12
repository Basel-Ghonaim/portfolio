# ADR 0006 — Backups

**Status:** Accepted
**Date:** 2026-11-12

## Context

D10-05 and D10-06 require:
- a weekly backup of the database and files, stored outside the main hosting providers;
- at least the last 4 backups kept;
- a restore tested before launch and every 6 months;
- a visible alert when backups fail.

Data lives in Neon (database) and Cloudinary (media) (ADR 0003). Every service must be free with no payment card. The application repository is public, so backups must never be stored in it: they contain drafts and archived projects, which must not be public (D5-04).

## Decision

1. **Runner and storage:** a separate **private** GitHub repository, `portfolio-backups`, running a weekly scheduled GitHub Actions workflow. It is free, needs no payment card, and is outside Vercel and Neon.
2. **Contents:**
   - **Database:** a full export, **excluding** the sessions and sign-in attempts tables, which are sensitive and not needed for a restore.
   - **Media:** a copy of every original image and the CV from Cloudinary.
3. **Retention:**
   - **Database:** exports are stored as workflow artifacts and expire automatically after about 5 weeks, which keeps at least the last 4 weekly backups.
   - **Media:** files are mirrored into the private repository, with only new or changed files added each week, so storage does not multiply.
4. **Failure alert:**
   - after each successful backup, its date is recorded in the application database;
   - the dashboard shows an alert when more than 8 days pass without a successful backup, which covers every kind of failure;
   - GitHub also emails the owner automatically when a workflow fails.
5. **Manual backup:** the workflow can be started at any time with GitHub's "Run workflow" button. The dashboard links to it.
6. **Restore:** a documented procedure.
   - The database is first restored into a **separate Neon branch**, a free feature, so tests never touch live data.
   - Media is re-uploaded to Cloudinary with the same identifiers.
   - The restore is tested before launch and every 6 months.
7. **Secrets:** the database URL and the Cloudinary key are stored only as secrets of the private repository. The database user used for backups should have read-only access.

## Alternatives rejected

- **Workflow artifacts or files in the public repository:** would expose drafts and archived content.
- **Relying on Neon's built-in restore history only:** same provider and a short window; does not satisfy "outside the main provider".
- **Paid backup services:** violate the cost rule.

## Consequences

- One additional private repository, owned by the owner, with no extra provider.
- The application database gains a small backup-status record used by the dashboard alert.
- GitHub's free limits for private repositories (Actions minutes and artifact storage) must be checked at setup; database exports are small.
