<!-- markdownlint-disable -->

# Hardening Report: yutailang0119--action-ktlint/v5.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **yutailang0119--action-ktlint/v5.0.0** was hardened automatically. 5 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/check-dist.yml use mutable tag-based refs instead of pinned SHA commits, making the workflow vulnerable to supply-chain attacks if the referenced action tags are moved or compromised. Failing references: `actions/checkout@v4` (line 29), `actions/setup-node@v4` (line 33), `actions/upload-artifact@v4` (line 63).

Locations:

- `.github/workflows/check-dist.yml:29`
- `.github/workflows/check-dist.yml:33`
- `.github/workflows/check-dist.yml:63`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/ci.yml use mutable tag-based refs instead of pinned SHA commits. Failing references: `actions/checkout@v4` (line 17), `actions/setup-node@v4` (line 22), `actions/checkout@v4` (line 40).

Locations:

- `.github/workflows/ci.yml:17`
- `.github/workflows/ci.yml:22`
- `.github/workflows/ci.yml:40`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/codeql-analysis.yml use mutable tag-based refs instead of pinned SHA commits. Failing references: `actions/checkout@v4` (line 30), `github/codeql-action/init@v3` (line 34), `github/codeql-action/autobuild@v3` (line 39), `github/codeql-action/analyze@v3` (line 43).

Locations:

- `.github/workflows/codeql-analysis.yml:30`
- `.github/workflows/codeql-analysis.yml:34`
- `.github/workflows/codeql-analysis.yml:39`
- `.github/workflows/codeql-analysis.yml:43`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/licensed.yml use mutable tag-based refs instead of pinned SHA commits. Failing references: `actions/checkout@v4` (line 28), `actions/setup-node@v4` (line 33), `ruby/setup-ruby@v1` (line 40), `licensee/setup-licensed@v1.3.2` (line 43).

Locations:

- `.github/workflows/licensed.yml:28`
- `.github/workflows/licensed.yml:33`
- `.github/workflows/licensed.yml:40`
- `.github/workflows/licensed.yml:43`

### unpinned-uses (severity: high)

All `uses:` references in .github/workflows/linter.yml use mutable tag-based refs instead of pinned SHA commits. Failing references: `actions/checkout@v4` (line 20), `actions/setup-node@v4` (line 26), `super-linter/super-linter/slim@v7` (line 34).

Locations:

- `.github/workflows/linter.yml:20`
- `.github/workflows/linter.yml:26`
- `.github/workflows/linter.yml:34`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable tag-based `uses:` references to full commit SHAs across 5 workflow files:

- check-dist.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02
- ci.yml: actions/checkout@v4 (×2) → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020
- codeql-analysis.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, github/codeql-action/init@v3, autobuild@v3, analyze@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26
- licensed.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, ruby/setup-ruby@v1 → @003a5c4d8d6321bd302e38f6f0ec593f77f06600, licensee/setup-licensed@v1.3.2 → @0d52e575b3258417672be0dff2f115d7db8771d8
- linter.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, super-linter/super-linter/slim@v7 → @12150456a73e248bdc94d0794898f94e23127c88

All original tags preserved as inline comments (e.g., `# v4`) for readability.

