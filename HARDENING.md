<!-- markdownlint-disable -->

# Hardening Report: dkamm--pr-quiz/v0.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dkamm--pr-quiz/v0.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action uses `actions/setup-node@v4`, which is pinned to a mutable version tag rather than an immutable 40-character commit SHA. If the tag is moved (e.g. by a supply-chain compromise), the action will silently execute different code. Pin to a full SHA, e.g. `actions/setup-node@1d0ff469b4a3d2f2b2b1b1b1b1b1b1b1b1b1b1b # v4`.

Locations:

- `action.yml:57`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/setup-node@v4` to its full commit SHA `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4` in hardened/action/action.yml at line 57. The mutable tag is preserved as a comment for readability.

### Iteration 2

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action tags to full SHA commit hashes across 5 workflow files:
- check-dist.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, actions/upload-artifact@v4 → @ea165f8d65b6e75b540449e92b4886f43607fa02
- ci.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020
- codeql-analysis.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, github/codeql-action/init@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/autobuild@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26, github/codeql-action/analyze@v3 → @b7351df727350dca84cb9d725d57dcf5bc82ba26
- linter.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5, actions/setup-node@v4 → @49933ea5288caeca8642d1e84afbd3f7d6820020, super-linter/super-linter/slim@v7 → @12150456a73e248bdc94d0794898f94e23127c88
- quiz.yml: actions/checkout@v4 → @34e114876b0b11c390a56381ad16ebd13914f8d5
All original tags preserved as inline comments.

