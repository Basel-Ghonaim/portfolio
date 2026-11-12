# ADR 0001 — Core Stack and Monorepo

**Status:** Accepted
**Date:** 2026-10-25

## Context

The portfolio is a personal project (PRD v1.0) built by an owner whose main expertise is React and TypeScript, expanding into backend work. The owner's existing project, Masaha, uses the same core technologies, and some of its assets will be reused through copy-and-own (local reuse decisions R1-01–R1-05). The project must stay simple, run at zero mandatory cost, and behave identically on every machine and in CI.

## Decision

1. **Core technologies:** React, TypeScript in strict mode, PostgreSQL, Prisma, Express, and Node.js.
2. **Versions:** start from Masaha's versions — React 19, Express 5, Prisma 7, Node 24.
   - Node uses LTS releases only; whether to stay on Node 24 or move to a newer LTS is verified at setup time.
   - The PostgreSQL version is set by the hosting provider chosen in the hosting ADR; local development uses the same version.
3. **Monorepo tool:** npm workspaces. A build orchestrator (e.g. Turborepo) is added only if builds become slow.
4. **Shared package:** `packages/shared` holds Zod schemas and request/response types used by both backend and frontend. The rest of the repository layout (`apps/*`) is decided in the application-shape ADR.
5. **TypeScript configuration:** a shared `tsconfig.base.json` inherited by every package.
6. **Module system:** ESM throughout; no CommonJS.
7. **Local database:** PostgreSQL through Docker Compose.
8. **Reproducible environment:** `package-lock.json` is committed, and the Node version is pinned in the project.

## Alternatives rejected

- **Shared package published to a registry, or Git submodules, for Masaha assets:** rejected in favor of copy-and-own; the projects stay independent.
- **pnpm workspaces or Turborepo from the start:** extra tooling and learning without benefit at this size.
- **CommonJS or mixed module systems:** adds configuration friction with no benefit.

## Consequences

- The owner works with familiar tools, and Masaha assets transfer with minimal friction.
- Frontend and backend share one definition of data shapes, preventing drift.
- The application shape and rendering approach (per-page initial HTML with language, direction, and metadata — constraint R4-C1) remain open and are decided next; they may add a framework on top of React without changing this core.
