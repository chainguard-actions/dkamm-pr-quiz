<!-- markdownlint-disable -->

# Hardening Report: dkamm--pr-quiz/v0.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dkamm--pr-quiz/v0.1.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The composite action uses `actions/setup-node@v4`, which is a mutable tag reference rather than a pinned 40-character commit SHA. If the tag is moved (e.g., by a supply-chain compromise), the action will silently execute different code. Pin to a full SHA, e.g. `actions/setup-node@1d0ff469b12462b0d180f2d9f1b6d7f5e5e5e5e5 # v4`.

Locations:

- `action.yml:57`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned `actions/setup-node@v4` to its full commit SHA `actions/setup-node@49933ea5288caeca8642d1e84afbd3f7d6820020 # v4` in hardened/action/action.yml line 57. The original tag is preserved as a comment for readability.

