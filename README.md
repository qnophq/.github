# qnophq/.github

Org-wide defaults for the [qnophq](https://github.com/qnophq) GitHub
organization. GitHub loads files from this repository automatically for every
repository under `qnophq/*` that does not provide its own override.

## Layout

| Path | Purpose |
| --- | --- |
| `default.json` | Renovate config consumed via `extends: ["github>qnophq/.github"]`. |
| `.github/workflows/renovate.yml` | Reusable Renovate trigger; consumer repos call it via `uses:` with their own schedule + permissions. |
| `.github/workflows/renovate-config-validator.yml` | Validates `default.json` on every push and PR. |

This repository is **public** so that Renovate can resolve the
`github>qnophq/.github` preset using each consumer repo's own
repository-scoped `GITHUB_TOKEN` — no PAT or GitHub App is required. The file
contains no secrets, only dependency-grouping and pinning policy.

## Override behavior

A file in a specific repo's `.github/` directory always overrides the
corresponding file here. For Renovate, per-repo `renovate.json` files extend
`github>qnophq/.github` and add their own `packageRules` for project-specific
stacks (e.g. the Java/Gradle and frontend groupings live in
`qnophq/qnop/.github/renovate.json`, not here).

## Self-hosted Renovate

qnophq runs its own Renovate via GitHub Actions (`renovatebot/github-action`),
not the Mend-hosted GitHub App. The `renovatebot/github-action` SHA pin and run
conventions live once in this repo's reusable workflow; consumer repos add a
short stub. Minimal stub for a consumer repo's `.github/workflows/renovate.yml`:

```yaml
name: Renovate

on:
  schedule:
    - cron: "0 4 * * 1-5"
  workflow_dispatch:
    inputs:
      logLevel:
        description: "Log level"
        type: choice
        default: info
        options: [info, debug]

jobs:
  renovate:
    uses: qnophq/.github/.github/workflows/renovate.yml@main
    permissions:
      contents: write
      pull-requests: write
      issues: write
    with:
      logLevel: ${{ inputs.logLevel || 'info' }}
```

Each caller's `GITHUB_TOKEN` is scoped to its own repo, so the call is
single-repo by design — the reusable workflow adds no cross-repo write access.

## Maintenance

Changes to `default.json` affect every repo in the org. Treat them as
cross-cutting and let the `renovate-config-validator` workflow validate the
config before merging.
