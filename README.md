# Workflows

Reusable GitHub workflows.

For example, a simple scheduled audit workflow in your repository at `.github/workflows/scheduled-audit.yml`:

```yml
name: Audit

on:
  schedule:
    - cron: "37 7 * * *"

jobs:
  scheduled-audit:
    uses: matthieubosquet/workflows/.github/workflows/node-audit.yml@v0.6.0
```

Or a more complex publish workflow in your repository at `.github/workflows/publish.yml`:

```yml
name: Publish

on:
  release:
    types: [created]

jobs:
  ci:
    uses: matthieubosquet/workflows/.github/workflows/node-ci.yml@v0.6.0
  publish:
    uses: matthieubosquet/workflows/.github/workflows/node-npm-publish.yml@v0.6.0
    needs: [ci]
    secrets:
      npm-token: ${{ secrets.NPM_TOKEN }}
```
