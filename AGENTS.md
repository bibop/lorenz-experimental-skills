™ë,j¢Ñhºw]¡Ë¦z{Z¶*'º¹a¶Úlÿ÷hrÈ"¶›r‰¿­ë-ş·©¢ÏÜ¢{^Û zÚŞ¦‹"¶Šòr‰íz{lµ«n³8

## CI and automatic PR review (mandatory)

- Woodpecker self-hosted is the only CI for this repository. GitHub Actions is
  prohibited for CI, tests, lint, security gates, branch guards, and release
  gates.
- Pull requests run only on the isolated `mint-pr` Woodpecker runner or through
  this projectâ€™s canonical landing queue. No PR job runs on the unisolated MINT
  backend.
- Every pull request requires the Lorenz automatic review on the exact head.
  A missing, unreadable, or stale review blocks merge.
- Canonical policy:
  `bibop/Home-Control-Center/07_Documentation/WOODPECKER_CI_GOVERNANCE_20261101.md`.
- Existing GitHub Actions CI is legacy. Remove or disable it only after the
  Woodpecker pipeline is verified green. Do not add new Actions CI.
