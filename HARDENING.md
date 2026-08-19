<!-- markdownlint-disable -->

# Hardening Report: yutailang0119--action-ktlint/v4.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **yutailang0119--action-ktlint/v4.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file uses `actions/checkout@v4.1.2` in two steps. The ref `v4.1.2` is a mutable version tag, not a pinned 40-character commit SHA. If the tag is moved or the repository is compromised, the action could execute arbitrary code. Each reference should be replaced with the full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4.1.2`.

Locations:

- `.github/workflows/test.yml:13`
- `.github/workflows/test.yml:21`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/test.yml` has no top-level `permissions:` key, and neither the `build` job nor the `test` job defines its own `permissions:` block. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g. write access to contents). A minimal `permissions:` block (e.g. `contents: read`) should be added at the top level or per job.

Locations:

- `.github/workflows/test.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed hardened/action/.github/workflows/test.yml: (1) Pinned both `actions/checkout@v4.1.2` references to the full commit SHA `9bb56186c3b09b4f86b1c65136769dd318469633` with the tag preserved as a comment. (2) Added a top-level `permissions: contents: read` block to enforce least-privilege token access.

