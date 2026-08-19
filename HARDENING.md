<!-- markdownlint-disable -->

# Hardening Report: yutailang0119--action-ktlint/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **yutailang0119--action-ktlint/v3.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow file references actions/checkout@v3.0.0 (a version tag) in two steps. Tags are mutable and can be moved to point to different — potentially malicious — commits. Each uses: reference should be pinned to a full 40-character commit SHA (e.g., actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v3.0.0).

Locations:

- `.github/workflows/test.yml:13`
- `.github/workflows/test.yml:20`

### missing-permissions (severity: medium)

The workflow file has no top-level permissions: key and neither the 'build' job nor the 'test' job defines its own permissions: block. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be broader than necessary. A minimal permissions block (e.g., contents: read) should be added at the top level or to each job.

Locations:

- `.github/workflows/test.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed hardened/action/.github/workflows/test.yml: (1) Pinned both actions/checkout@v3.0.0 references to the full SHA a12a3943b4bdde767164f792f33f40b04645d846 with the original tag preserved as a comment. (2) Added a top-level `permissions: contents: read` block to restrict the workflow token to the minimum necessary permissions.

