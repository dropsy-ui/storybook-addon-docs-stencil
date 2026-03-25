# Contributing

Thanks for contributing to `@dropsy-ui/storybook-addon-docs-stencil`.

## Development

### Branching

- Create feature branches from `main`.
- Use focused PRs with clear summaries.

### Local setup

```bash
npm ci
npm run build
```

## Versioning Model

This package tracks Storybook major versions.

- Addon `9.x` supports Storybook `9.x`.
- Addon `10.x` supports Storybook `10.x`.

A Storybook major compatibility change should be released as an addon major.

## Release Process

Releases are automated with Changesets and GitHub Actions.

### Day-to-day flow

1. Make code changes in a feature branch.
2. Add a changeset in the same branch:

```bash
npm run changeset
```

3. Select the correct bump type (`patch`, `minor`, or `major`).
4. Write clear release notes in the changeset prompt.
5. Open and merge your PR to `main`.

After merge, `.github/workflows/release.yml` runs and Changesets will:

- open or update a release PR (`chore: release`) with version/changelog changes, or
- publish immediately if the release PR has already been merged.

### Publishing behavior

When the release PR is merged:

- package versions are updated,
- npm publish runs via `changeset publish`,
- GitHub Release and tag are created automatically.

## Major Release Example (`10.0.0`)

For Storybook 10 support:

1. Implement and validate Storybook 10 compatibility.
2. Add a changeset with a `major` bump.
3. Mention Storybook 10 support and key breaking changes in the changeset text.
4. Merge feature PR(s) into `main`.
5. Merge the generated `chore: release` PR.
6. Confirm npm package and GitHub Release were published.

## Pre-merge Checklist

- `npm run lint` passes.
- `npm run build` passes.
- A changeset is included for user-facing changes.
- README and docs are updated when behavior changes.

## Manual Recovery

If release automation fails:

1. Fix the workflow or token issue.
2. Re-run the failed GitHub Actions job.
3. If needed, run locally:

```bash
npm run version-packages
npm run release
```

Only use manual local release commands when automation is blocked.
