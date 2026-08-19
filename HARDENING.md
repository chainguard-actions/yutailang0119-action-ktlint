<!-- markdownlint-disable -->

# Hardening Report: yutailang0119--action-ktlint/v3.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **yutailang0119--action-ktlint/v3.1.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses `actions/checkout@v3.0.2` (a version tag) in two steps instead of a full 40-character commit SHA. Mutable tags can be moved to point to different (potentially malicious) commits, enabling supply-chain attacks.

Locations:

- `.github/workflows/test.yml:13`
- `.github/workflows/test.yml:20`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/test.yml` has no top-level `permissions:` key, and neither the `build` job nor the `test` job defines its own `permissions:` block. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (e.g., write access to contents). A minimal explicit `permissions:` block should be added.

Locations:

- `.github/workflows/test.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both findings in .github/workflows/test.yml: (1) Pinned both `actions/checkout@v3.0.2` references to the full SHA `2541b1294d2704b0964813337f33b291d3f8596b` with the tag preserved as a comment. (2) Added `permissions: {}` at the top level to enforce least-privilege token access.

