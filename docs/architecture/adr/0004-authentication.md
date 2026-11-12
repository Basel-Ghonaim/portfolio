# ADR 0004 — Authentication

**Status:** Accepted
**Date:** 2026-11-12

## Context

The dashboard has exactly one user: the owner. Sign-in uses the owner's GitHub account only, with no passwords (D10-01). Sessions last 7 days, with "Sign out of all devices" and slowed repeated failures (D10-03). Emergency recovery must require access to the hosting environment and must not be possible from the site itself (D10-02). The application runs on Vercel functions (ADR 0003), where in-memory state is not shared between requests.

## Decision

1. **Implementation:** a small, custom GitHub OAuth flow inside Express, with no authentication library. A GitHub OAuth App provides the credentials; one route starts sign-in and one route handles the callback.
2. **Owner check:** the signed-in GitHub account is matched by its **numeric account ID**, not its username (usernames can change). The allowed ID is stored in an environment variable. Any other account is rejected.
3. **Sessions:** a secure cookie (`HttpOnly`, `Secure`, `SameSite=Lax`) valid for 7 days. Sessions are **stored in the database**, so "Sign out of all devices" deletes them.
4. **Protection:**
   - the OAuth `state` parameter prevents forged sign-in requests;
   - state-changing dashboard requests are accepted only from the same origin;
   - sign-in attempts are rate-limited with counters stored in the database (in-memory limits do not work across Vercel function instances).
5. **Emergency recovery:** through the Vercel dashboard only — change the allowed account ID in the environment variable, or invalidate all sessions by rotating the session signing secret.

## Alternatives rejected

- **A full authentication library or hosted auth service:** far larger than one owner needs, and adds a dependency or a provider.
- **Stateless tokens only (e.g. JWT without server storage):** "Sign out of all devices" would require extra revocation logic.
- **Matching by GitHub username:** a username can change or be taken by someone else.

## Consequences

- No passwords are stored, and GitHub's two-factor authentication protects access.
- A sessions table and a sign-in attempts table are added to the database.
- Losing access to the GitHub account is recoverable only through the hosting account, as required by D10-02.
