# Git Workflow

## Branching

- `main` — always buildable; protected.
- `feature/<short-name>` — new features.
- `fix/<short-name>` — bug fixes.
- `docs/<short-name>` — documentation changes.

## Commit messages

Use short, imperative subjects (`Add login form`, not `added login form`) with a body explaining the why when it isn't obvious.

## Pull requests

1. Rebase onto `main` before opening a PR.
2. Keep PRs small and focused.
3. Squash-merge is preferred to keep history clean.
