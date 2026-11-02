# `useBaseBranchConfig=merge` with a missing base branch config

Minimal reproduction of Renovate's behaviour when `useBaseBranchConfig=merge` is set, but one of the `baseBranchPatterns` has no Renovate config file.

| Branch        | `renovate.json`                                              |
| ------------- | ------------------------------------------------------------ |
| `main`        | present, sets `baseBranchPatterns` and `useBaseBranchConfig` |
| `release/1.x` | present (adds a `packageRules` label)                        |
| `release/2.x` | **missing**                                                  |

All branches have a `package.json` with an outdated `lodash`, so Renovate has something to do on each.

To reproduce, run Renovate against this repo (i.e. with `LOG_LEVEL=debug`) and compare the logs and branches/PRs for `release/1.x` vs `release/2.x`.
