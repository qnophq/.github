# Security Policy

## Supported Versions

qnop is in early active development (Phase 0 — project skeleton). Security
fixes are issued for:

- The `main` branch of every active repository in this organization.
- The most recent tagged release of each repository (where releases exist).

Older releases do **not** receive backported fixes. If you are running an
older version, the recommended path is to upgrade.

## Reporting a Vulnerability

**Do not file a public GitHub issue for a suspected vulnerability.**

Use one of the following private channels:

1. **Preferred — GitHub Private Security Advisories.** On the affected
   repository, go to `Security` → `Advisories` → `New draft security
   advisory`. This keeps the discussion private until a fix is published and
   gives us the right tooling for coordinated disclosure.
   - Direct link template: `https://github.com/qnophq/<repo>/security/advisories/new`
2. **Fallback — email** to <info@devtank42.de>. Include:
   - The affected repository and version (commit SHA if possible).
   - A clear description of the issue and its impact.
   - Steps to reproduce, including any proof-of-concept code.

Please do not include exploit details in any public channel (issues,
discussions, PR descriptions, social media) until a fix is released.

## What to Expect

qnop is maintained by a small team. We commit to best-effort response on the
following timeline:

- **Acknowledgment** of your report within **5 business days**.
- **Initial triage** (confirm / dispute / request more info) within
  **14 business days**.
- A **fix or mitigation plan** communicated transparently once triage is
  complete. Timelines depend on severity and complexity; we will keep you
  updated.
- **Coordinated disclosure** once a fix is available. We are happy to credit
  reporters in the advisory if requested.

These are commitments to communicate, not guarantees of resolution time. We
cannot offer 24/7 incident response.

## Out of Scope

The following are out of scope for this security policy:

- Denial-of-service via traffic volume against public endpoints.
- Social-engineering attacks against maintainers or contributors.
- Vulnerabilities in dependencies that are already publicly disclosed and
  tracked by Renovate / the Dependency Dashboard.
- Issues that require physical access to a server running qnop.

## License Note

qnop is licensed under AGPL-3.0. The reporting channels above apply equally to
all users of the codebase, including downstream forks and commercial
licensees. Please report privately first, regardless of how you are running
the software.
