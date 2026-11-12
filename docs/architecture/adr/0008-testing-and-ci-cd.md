# ADR 0008 — Testing and CI/CD

**Status:** Accepted
**Date:** 2026-11-12

## Context

D11-05 requires testing focused on critical flows, D11-01 to D11-04 set measurable quality targets, and the light process (Q15) requires a branch and Pull Request per task with automated checks. Reuse decisions R8-01 to R8-08 define the tooling taken from Masaha. Masaha's CI runs ten separate jobs on every Pull Request; the portfolio keeps that structure and strengthens it. The repository is public, so GitHub's security features and Actions are free, and no service may require a payment card (ADR 0003).

## Decision

### Test tools
- **Unit and component tests:** Vitest with Testing Library.
- **API tests:** Supertest.
- **Browser end-to-end tests:** Playwright.
- **Accessibility:** vitest-axe with WCAG 2.2 AA rules and `target-size` enabled (R8-05), and axe in Playwright in a real browser (R8-06).
- **Test database:** a real PostgreSQL instance — Docker Compose locally and a temporary service container in GitHub Actions. Neon is never used by tests.
- **External services:** Cloudinary, GitHub, and Umami are replaced by fakes in all tests. Tests need no internet access or real accounts.
- **Sign-in in browser tests:** tests create a session directly in the test database and set the cookie. There is no test-only sign-in route in the code.
- **Coverage:** no numeric target; critical flows first (D11-05).

### Pull Request workflow (`CI`)
Each job runs separately (in parallel where possible). Jobs 1–14 are required status checks:

| # | Job | Purpose |
|---|---|---|
| 1 | `lint` | ESLint, including design-system boundary rules (R9-03) |
| 2 | `format:check` | Prettier formatting |
| 3 | `typecheck` | TypeScript across all workspaces |
| 4 | `test:unit` | Unit tests |
| 5 | `test:component` | Component tests with accessibility checks |
| 6 | `check:classes` | Logical-properties rule (R8-02) |
| 7 | `check:links` | Documentation links (R8-03) |
| 8 | `check:conflicts` | Leftover merge-conflict markers across the whole repository (R8-01) |
| 9 | `build` | Production build of all workspaces |
| 10 | `test:api` | API tests against PostgreSQL |
| 11 | `db:migrate` | Applies all Prisma migrations from scratch and fails if `schema.prisma` and the migrations differ (drift) |
| 12 | `budget` | Public-site initial JavaScript ≤ 150 KB gzip (ADR 0002) |
| 13 | `test:e2e` | Playwright on Chromium, with accessibility checks |
| 14 | `audit` | `npm audit`; fails on high or critical vulnerabilities |
| 15 | `lighthouse` | Lab performance report on Home, Projects, one case study, and About (D11-01). Reported on every Pull Request; **not** a required check, because lab measurements in Actions are noisy. It becomes blocking only in the release check. |

### Security
- **Secret scanning with push protection:** blocks pushing keys or credentials (D10-08).
- **CodeQL:** code security analysis on every Pull Request (required check).
- **Dependabot:** vulnerability alerts and automatic update Pull Requests. Security updates are immediate; regular updates are weekly and grouped.

### Branch protection on `main`
- Direct pushes are blocked; every change arrives through a Pull Request whose required checks passed.
- Only status checks are required, not human review: the owner is the only developer and GitHub does not allow approving one's own Pull Request.
- Superseded runs on the same Pull Request are cancelled, and dependencies are cached, to keep CI fast.

### Deployment (CD)
- Vercel deploys `main` automatically. Since `main` only receives Pull Requests with passing checks, production only receives passing code.
- Prisma migrations are applied automatically during production deployment. If they fail, the deployment stops and the previous version keeps running.
- Pull Request preview deployments use a separate Neon branch without real data and are excluded from search. Dashboard sign-in may not work on previews (a GitHub OAuth App has one callback URL); this is accepted.
- **Post-deploy smoke test:** after every production deployment, a workflow checks `/health`, the Arabic and English home pages, and that `lang`, `dir`, and share-preview tags are present in the HTML (ADR 0002). A failure emails the owner.

### Weekly scheduled workflow
- Playwright on Firefox and WebKit (D11-03).
- Lighthouse report.
- Full `npm audit`.
- Full CodeQL scan.

These run before launch as well.

## Alternatives rejected

- **Required human review:** blocks a single developer.
- **All browsers on every Pull Request:** slows every change; covered weekly and before launch.
- **Blocking Pull Requests on Lighthouse scores:** noisy results would cause false failures.
- **Commit-message linting, licence scanning, multi-stage deployments:** slow or complex without benefit for a personal project.

## Consequences

- The public repository demonstrates a strong, visible quality process.
- Production receives only code that passed every required check, and broken deployments are detected immediately.
- Branch protection, secret scanning, CodeQL, and Dependabot are configured in the GitHub repository settings at setup time.
