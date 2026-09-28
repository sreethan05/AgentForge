# Release Process

1. Make sure all intended changes are merged into `main`.
2. Update the version in `package.json` (semver: MAJOR.MINOR.PATCH).
3. Update `CHANGELOG.md` if one exists, summarising the changes.
4. Tag the release: `git tag vX.Y.Z && git push origin vX.Y.Z`.
5. Create a GitHub Release from the tag with release notes.

## Versioning

- **PATCH** — bug fixes, no new features.
- **MINOR** — new features, backwards compatible.
- **MAJOR** — breaking changes.
