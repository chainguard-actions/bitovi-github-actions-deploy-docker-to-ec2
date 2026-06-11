<!-- markdownlint-disable -->

# Hardening Report: bitovi--github-actions-deploy-docker-to-ec2/v1.0.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **bitovi--github-actions-deploy-docker-to-ec2/v1.0.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yaml contains two `uses:` references pinned to mutable tags rather than full 40-character SHA commit hashes, making the action vulnerable to supply-chain attacks if the referenced tags are moved or overwritten:
- `uses: actions/checkout@v4` (tag ref, not a SHA)
- `uses: bitovi/github-actions-commons@v2.0.8` (version tag ref, not a SHA)
These should be pinned to their full commit SHAs, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v4`.

Locations:

- `action.yaml`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned both mutable tag references in action.yaml to full commit SHAs:
- `actions/checkout@v4` → `actions/checkout@34e114876b0b11c390a56381ad16ebd13914f8d5 # v4`
- `bitovi/github-actions-commons@v2.0.8` → `bitovi/github-actions-commons@734bf31e47290ed9dd3f84bf01d473bfaaf4eebd # v2.0.8`
SHAs were resolved using lookup_action_sha and the original tags are preserved as comments for readability.

