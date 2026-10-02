<!-- markdownlint-disable -->

# Hardening Report: bitovi--github-actions-deploy-docker-to-ec2/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **bitovi--github-actions-deploy-docker-to-ec2/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Two `uses:` references in action.yaml are pinned to mutable version tags rather than immutable 40-character commit SHAs. This exposes the action to supply-chain attacks if the referenced tags are moved or the upstream repositories are compromised.

1. `uses: actions/checkout@v4` — should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`
2. `uses: bitovi/github-actions-commons@v2.0.8` — should be pinned to a full SHA, e.g. `bitovi/github-actions-commons@<40-char-sha> # v2.0.8`

Locations:

- `action.yaml:29886`
- `action.yaml:29967`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both unpinned action references in hardened/action/action.yaml:
1. `actions/checkout@v4` → `actions/checkout@11d5960a326750d5838078e36cf38b85af677262 # v4`
2. `bitovi/github-actions-commons@v2.0.8` → `bitovi/github-actions-commons@734bf31e47290ed9dd3f84bf01d473bfaaf4eebd # v2.0.8`
Both SHAs were resolved via lookup_action_sha. No other unpinned references were found.

