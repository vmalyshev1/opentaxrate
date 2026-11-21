# About this fork

`vmalyshev1/opentaxrate` is a fork of
[equated-org/opentaxrate](https://github.com/equated-org/opentaxrate)
(OpenTaxRate, MIT License, Copyright (c) 2026 Interlay, Inc. (DBA Equated)).
It serves as the primary rates provider for the private US-Sales-Tax-Calc app.
The upstream `LICENSE` is kept unchanged.

## Changes in this fork

- Dependency versions raised to clear known advisories: `drizzle-orm`
  ^0.45.2 (SQL identifier escaping), `hono` ^4.13.16 and
  `@hono/node-server` ^2.1.11 (path-handling and middleware bypasses).
  `pnpm typecheck` passes. The test suite showed no new failures against
  the unmodified code in the same environment.
- Remaining advisory: an old `esbuild` pulled in by `drizzle-kit` (a
  development and migration tool). It concerns esbuild's development server,
  which this project does not run in production.

## Staying in sync with upstream

`.github/workflows/upstream-sync.yml` runs every Monday (and on demand from
the Actions tab). It merges new upstream commits into the `upstream-sync`
branch, runs the type check, the tests and a production dependency audit,
and opens a pull request into `main` with the results. A conflict confined
to `pnpm-lock.yaml` is resolved automatically by regenerating the lockfile;
any other conflict opens an issue. Nothing reaches `main` until the PR is
merged by hand.

The app pins a specific version of this fork and moves to a newer one only
deliberately, after review and an accuracy check against official state
answers.
